# Gỡ block khi vận hành

Gặp trở ngại thì tra theo dấu hiệu, làm theo cách xử lý, rồi xác minh đã phục hồi. Khớp thì không hỏi lại người dùng, ghi "phục hồi theo <mục>" kèm bằng chứng. Tối đa 2 phương án, hết thì mới `blocked`.

Cách xử lý chỉ áp cho bước setup, không áp cho luồng đang kiểm thử, và không bao giờ là tiêu chí Pass.

## 429 kéo dài khi tạo layer-image
- Dấu hiệu: `POST /api/layer-images/from-clipart` hoặc `/by-temporary-file` trả 429 liên tục, UI kẹt `Generating...`, không có toast. GET/publish vẫn 200.
- Nguyên nhân: đã xác minh là quota tạo layer-image theo account, cửa sổ dài (không phải burst). Ngưỡng cụ thể: giả thuyết, ≤ 2 request liên tiếp.
- Cách xử lý: dừng mọi thao tác tạo layer-image, làm các phần khác trước; thử lại 1 lần sau vài giờ. Tính trước số request cần dùng và gom lại.
- Cách xác minh: request tiếp theo trả 201, layer có ảnh trong library.
- Giới hạn: chỉ nhóm POST tạo layer-image. Không áp cho 429 của SDK storefront (rate limit khác, staging cố ý đặt nhỏ). Nếu issue đang test chính là rate limit này thì 429 là kết quả, không phải blocker.

## Storefront 404 dù campaign by Shopify đã publish
- Dấu hiệu: portal publish 200, nhưng `/products/<handle>` 404, không có trong `/collections/all`; nút `View` chỉ mở trang chủ.
- Nguyên nhân: đã xác minh là Shopify product chưa bật sales channel Online Store.
- Cách xử lý: login Shopify admin bằng Playwright → product → bật Online Store.
- Cách xác minh: `/products/<handle>` trả trang sản phẩm có form teeinblue.
- Giới hạn: không áp khi issue đang test chính là luồng publish/sync product sang Shopify (khi đó 404 là kết quả cần ghi nhận).

## Payload có `<script>` bị WAF chặn lúc save/upload
- Dấu hiệu: `net::ERR_FAILED` kèm lỗi CORS (không có `Access-Control-Allow-Origin`), toast `Network Error`; payload sạch cùng endpoint thì 200/201.
- Nguyên nhân: đã xác minh là edge/WAF chặn theo nội dung body chứa `<script` / `onload=`.
- Cách xử lý: dựng data bằng biến thể không có `<script>` (vd `<img src=x onerror=...>`).
- Cách xác minh: save 200 và payload persist nguyên văn sau reload.
- Giới hạn: chỉ khi case không bắt buộc đúng payload `<script>`. Case yêu cầu đúng payload đó thì vế đó `blocked` (cần Dev whitelist), không được thay payload rồi kết luận. Không ghi "WAF chặn" thành kết luận "app an toàn".

## Runner script bị Shopify chặn "Verify you are human" (Cloudflare)
- Dấu hiệu: `node scripts/tib/run.mjs` mở storefront <TIB_STORE_URL> ra trang "Your connection needs to be verified before you can proceed" (Cloudflare checkbox), `sf.open` timeout chờ `.tee-field`; trước đó có loạt 429 Shopify (`cart/add`, `/cart.js` trả HTML) sau nhiều lượt ATC liên tiếp. Thử `--headed` và `--state` lấy từ context MCP vẫn bị chặn.
- Nguyên nhân: giả thuyết — bot protection của Shopify chấm điểm context mới/headless sau burst request; chưa xác minh tiêu chí.
- Cách xử lý: chạy cùng logic bằng `browser_run_code_unsafe` với `filename` trên server MCP đang vào được (vd run cũ, mỗi file là `async (page) => {...}` tự chứa helper, không import được module; ảnh lưu bằng `path` tuyệt đối, kết quả trả JSON). Checkout cũng làm trong cùng browser đó.
- Cách xác minh: trang product có `.tee-field`, ATC trả customization 201 + cart/add 200.
- Giới hạn: chỉ cho bước chạy storefront; không đổi tiêu chí Pass. Môi trường run_code không có `require`/`process`/`import()`; ghép ảnh dùng script node riêng trong project (`@playwright/test` resolve từ project root). Tham số `filename` lỗi ENOENT khi trỏ vào thư mục evidence của project; khi đó trả kết quả dạng JSON rồi ghi file bằng shell.

## Cần login portal bằng account khác (vd org `TIB_USER_B`) trên server Playwright isolated
- Dấu hiệu: server `playwright-2`/`-3` đang ở session user `TIB_USER_A` (từ `mcp-isolated.json`), case cần account khác (`TIB_USER_B_*`); `browser_run_code_unsafe` không đọc được `.env` ("A dynamic import callback was not specified").
- Nguyên nhân: đã xác minh 2026-11-03 (TIB-5619) — mọi server isolated và `run.mjs` dùng **chung một session Sanctum** trong `playwright/.auth/mcp-isolated.json`; `POST /api/logout` trên một server huỷ session đó cho tất cả (run.mjs với state mặc định trả `/api/user` 401).
- Cách xử lý: **KHÔNG logout** trên server MCP. Tạo storageState riêng cho account kia bằng node (Sanctum `csrf-cookie` → `POST /api/login` với `env('TIB_USER_B_EMAIL'/'_PASSWORD')` từ `scripts/tib/lib.mjs`, import playwright bằng đường dẫn tuyệt đối `node_modules/playwright/index.mjs` nếu script ở ngoài repo), lưu ở scratchpad, rồi chạy case bằng `run.mjs --state <file>`. Lỡ logout rồi: `node scripts/make-mcp-storage-state.mjs` và báo coordinator restart các server isolated.
- Cách xác minh: case trong `run.mjs --state <file>` gọi `portal.open` trả `me.id` = id account cần (vd 94); state mặc định vẫn `GET /api/user` 200.
- Giới hạn: luồng cần nhìn UI từng bước bằng MCP vẫn không đổi account được trên server isolated (trừ khi coordinator cấp server có session account đó).

## Sửa artwork (đổi addon variant) rồi sync bằng MCP nhưng storefront không đổi
- Dấu hiệu: sau `update-artwork-layer-tool` + `bulk-sync-campaign-tool` (queued, `need_sync=false`), storefront vẫn dùng dữ liệu cũ: `window.teeinblueCampaign.version` không đổi, request `api/merchant/campaigns/<shopifyProductId>.json?v=<version cũ>` trả bản cũ (bản `v=<timestamp mới>` đã có dữ liệu mới), `addonVariants` thiếu variant addon mới.
- Nguyên nhân: giả thuyết — sync qua MCP không cập nhật metafield `teeinblue.campaign_version` / `teeinblue.addon_variants` như nút Update của portal.
- Cách xử lý: mở `/campaigns/<id>/edit?product-id=<pb>` → `Update` → dialog `Multi-store launch` → `Update` ở hàng store đích (`POST /api/campaigns/<id>/sync` 200 với `instance_id`).
- Cách xác minh: reload storefront: `teeinblueCampaign.version` mới, `addonVariants` có variant mới, option hiện giá addon.
- Giới hạn: chỉ là bước setup. Nếu issue đang test chính là sync qua MCP thì đây là kết quả cần báo, không né.

## Expected nằm ở bảng DB nội bộ hoặc job theo lịch, QA không thấy trên UI/GraphQL
- Dấu hiệu: comment Dev verify bằng một bảng DB (GraphQL báo `field '<table>' not found in type: 'query_root'`), hoặc kết quả chỉ có sau cron/job đêm.
- Nguyên nhân: đã xác minh — GraphQL merchant chỉ lộ một phần bảng; job chạy theo lịch server.
- Cách xử lý: **không đưa thành câu blocking.** Bảng: soạn query read-only + expected theo từng case (mẫu run cũ), người dùng chạy và dán kết quả. Job: ghi trong preflight là cần nhờ Dev chạy command sau khi re-render, không chờ lịch. Chưa rõ đã deploy chưa: thao tác đầu tiên sinh đúng dòng DB là bằng chứng đã deploy. Bảng hàng đợi kiểu `trashed_images`: dòng mất sau khi job cleanup chạy, nên phải query trong ngày, trước job đêm và trước khi gọi cleanup. Query rỗng sau job chưa phải là fail: kiểm file cũ trên CDN (QA quan sát file đã xoá trả 403, giống path không tồn tại, không phải 404; Dev chưa xác nhận mã, xem OQ-campaign-098). Staging có endpoint cleanup cho QA (xem `environment_differences`); dry-run không dự báo số file sẽ xoá, `trashed_images_before` là số dòng đã đến hạn, không phải tổng bảng.
- Cách xác minh: kết quả query khớp expected của case; output command của Dev có trong report.
- Giới hạn: DB chỉ đọc, không sửa data. Tên cột không suy đoán, chạy query cấu trúc bảng trước. Không áp cho production. Job do Dev chạy, agent không tự chạy.

## Autofixer chạy trễ hơn config public cho thấy; cửa sổ quan sát ngắn làm case "không có update" pass giả
- Dấu hiệu: config public (`campaigns/<id>.json`, `teeinblueShopConfig`) không có `autofixer_delay`, nhưng `cart/update.js` của autofixer đến sau 3 giây thay vì dưới 1 giây.
- Nguyên nhân: `teeinblue-custom-script` do app embed teeinblue render đặt `teeinblue = { autofixerDelay: …, ... }` (không phải theme); SDK ưu tiên option này trước `settings.autofixer_delay`. Giá trị do Dev đổi theo store, không cố định. Ghi chú thêm: `grep -o '.{N}chuỗi.{N}'` trên HTML storefront không khớp khi dòng ngắn, dùng `grep -c` hoặc đọc `window.teeinblue` trong trang.
- Cách xử lý: đầu lượt đọc `window.teeinblue?.autofixerDelay` trên trang thật. Cửa sổ quan sát phải dài hơn debounce 200ms + delay + 1 lần đọc cart. Case yêu cầu delay 0 thì đặt `window.teeinblue.autofixerDelay = 0` trong trang (mất khi reload, không đổi theme) và ghi rõ.
- Cách xác minh: case đối chứng (orphan + `cart/update.js`) thấy `cart/update.js` đến sau khoảng delay + 1 giây.
- Giới hạn: SDK chỉ đọc lại cart khi `hasCartModified` true; muốn ép đọc thì dispatch `shopify-event-cart-modified` trước khi fetch. Chỉ dùng để dựng điều kiện, không thay thế bước của case.

## `POST /api/merchant/shopify/customization` trả 429 khi nhiều case ATC chạy dồn
- Dấu hiệu: `POST /api/merchant/shopify/customization` trả 429 khi nhiều case ATC chạy dồn (vd 7 case song song trong khoảng 3 phút).
- Nguyên nhân: rate limit của API customization (ngưỡng chưa rõ).
- Cách xử lý: chạy tuần tự (`--parallel 1`) hoặc giãn các case có ATC.
- Cách xác minh: chạy lại tuần tự trả 201.
- Giới hạn: chỉ cản setup; nếu issue đang test là rate limit thì 429 là kết quả.

## Playwright MCP báo `Browser chrome-for-testing not installed`
- Dấu hiệu: Playwright MCP báo `Browser chrome-for-testing not installed` (thiếu bản chromium yêu cầu).
- Cách xử lý: chạy `npx @playwright/mcp install-browser chrome-for-testing` (tải vào cache ms-playwright của máy).
- Cách xác minh: gọi lại tool browser của server đó chạy được.

## Render game text (shape-text/spiral/warp-text) sai vẫn hiện sau khi fix đã deploy
- Dấu hiệu: cùng text cũ vẫn ra ảnh lỗi, response `cf-cache-status: HIT` với `age` lớn.
- Nguyên nhân: đã xác minh — response 200 cache ở CDN `max-age=604800`, ảnh lỗi render trước fix vẫn được trả lại.
- Cách xử lý: retest bằng text mới hoặc slot mới (gọi thẳng staging-api với `?slot=qa-<run>.0`), chỉ kết luận trên response `MISS`; hỏi Dev nếu cần purge cache. Order đặt trước fix: xem open-questions của `sdk` (OQ-sdk-248).
- Cách xác minh: response của lượt retest có `cf-cache-status: MISS`.
- Giới hạn: chỉ áp cho ảnh preview đã cache; không thay bước của case đang test.
