# Môi trường: thao tác

Host, auth, tool, chạy song song, production. Store dùng cho việc gì và giới hạn test: guide mục 3, 4.

## Host và auth

| Thành phần | Staging | Production |
|---|---|---|
| Portal admin | `staging-portal.teeinblue.com` | `portal.teeinblue.com` |
| API merchant (SDK gọi) | `staging-api.teeinblue.com` | `api.teeinblue.com` |
| API portal (Sanctum + GraphQL `/api/graphql`) | `staging-api.teeinblue.com/api` | `portal-api.teeinblue.com/api` (khác host API merchant) |
| CDN file design order | `cdn.ownego.com/teeinblue-staging/designs/…` | `cdn.teeinblue.com/designs/…` |
| SDK storefront | `staging-sdk.teeinblue.com` | `sdk.teeinblue.com` |
| Customize page | `staging-sdk.teeinblue.com/customize/` | `customize.teeinblue.com` |
| Upload | `upload-staging.teeinblue.com` | `photo-api.teeinblue.com` |

- Nhận biết môi trường của storefront: xem script SDK (`staging-sdk` = staging).
- **Auth staging = Sanctum session:** `GET /sanctum/csrf-cookie` (Origin/Referer = portal) → `POST /api/login` kèm `X-XSRF-TOKEN` → cookie session. Gọi thẳng `staging-graphql.teeinblue.com` lỗi "Invalid response from authorization hook". Thiếu User-Agent → 403. `scripts/make-mcp-storage-state.mjs` làm sẵn bước này.
- **Session portal staging (`playwright/.auth/mcp-isolated.json`) mặc định vào org `TIB_STAGING`**, không phải org `TIB_USER_A` của store <TIB_STORE_URL>. Data của instance `TIB_STORE_INSTANCE_ID` cần acting user `TIB_USER_A` (`portal.open(page, route, { acting: 64 })`, header `x-acting-user-id`). Ngoại lệ: staff của org `TIB_USER_B` không dùng header này (xem catalog).
- **GraphQL Hasura:** id kiểu `bigint` (vd `printareas_by_pk(id: $id)` với `$id: bigint!`), truyền `Int` sẽ lỗi.
- **Máy QA không có ImageMagick (`identify`).** Đọc kích thước/DPI file design bằng `design.meta()` trong `scripts/tib/lib.mjs` (PNG pHYs, JPEG JFIF, PDF MediaBox).
- **2FA portal staging:** tắt từ 2026-10-28. Nếu `/login/two-factor` xuất hiện lại → nhờ người dùng nhập mã trong server Playwright `playwright` (preflight).

## Env

Chép `_env.example` thành `.env` rồi điền giá trị do operator cấp. Tạo token bằng `POST /api/tokens` với `name` và `abilities`, giá trị chỉ hiện lúc tạo. Ability: `orders:read`, `orders:write`, `customizations:read`, `campaigns:read`, `products:read`, `mcp:access`.

## Cache, session, state

- **`app-v1.js` không có version hash, cache 10 năm**: trình duyệt có thể chạy bundle cũ. Preflight phải so bundle.
- **Translations storefront cache immutable 1 năm theo `translation_version`**: vừa Save có thể chưa tăng version → đợi rồi reload, hoặc mở context sạch.
- **Customization data của field trên storefront nằm ở localStorage** (global option ở key `teeinblue-global-options`) → dùng context sạch, localStorage giữ customization cũ.
- **Dialog Confirm password có hiệu lực 15 phút**: case cần thấy dialog phải fresh login hoặc chờ quá 15 phút.
- **Theme <TIB_STORE_URL> đặt `teeinblue.autofixerDelay: 2000` trong inline script**, ưu tiên hơn config public (config không có key này). Đọc `window.teeinblue.autofixerDelay` trên trang thật; cần delay 0 thì ghi đè trong trang, mất khi reload. <TIB_SDK_V2> không đặt, delay 0. (2026-11-05 TIB-5665)
- **`default_layer_value` của user `TIB_USER_A`** do người dùng tự đặt, có thể đổi (lần gần nhất `{required: true, show_in_cart: true}`, 2026-10-21) → đọc lại giá trị thật trước khi test.

## Tool: MCP và Shopify

| Tool | Giới hạn | Cách xử lý |
|---|---|---|
| Staging MCP `create-global-option-tool` | Không có `show_in_cart` → giá trị GO không hiện ở cart / order Options. Lỗi đã report riêng | Case cần thấy ở cart → bật Show in cart trên Portal rồi sync campaign |
| Staging MCP `create-global-option-tool` / `update-global-option-tool` type `text` | Lỗi `top/left/width required` dù payload có đủ (2026-11-04 TIB-5608; trước đó 2026-10-21 tạo được) | Tạo bằng Portal hoặc `POST /api/global-options`, xem `_flows/global-options.md` |
| Staging MCP (GO, layer) | **Không áp `default_layer_value`** của user (portal có áp) | Expected khi tạo qua MCP = payload truyền vào. Dựng data cho case phụ thuộc default thì tạo bằng Portal |
| Staging MCP condition (`dependency.dependencies[].value`) | Phải đúng kiểu id: AO nguồn category = số `[3510]`, inline = chuỗi `["L00"]`. Sai kiểu MCP vẫn nhận nhưng storefront không match | Dùng id số lấy từ campaign JSON `clipart_categories[].options[].id` |
| Shopify MCP (`mcp__shopify__*`) | Trỏ <TIB_STORE_URL> (instance `TIB_STORE_INSTANCE_ID`); `get-orders` chỉ trả order cũ nhất; không tạo collection, không publish Online Store; product tạo bằng MCP chưa lên Online Store (storefront 404) | Làm qua Shopify admin bằng Playwright (server `playwright`, có session). Xem L-002 |
| Playwright headless | Timing mạng sai; thiếu throttle mặc định | Dùng server MCP (headed); throttle/route theo công thức trong agent execute |

## Chạy song song

- Server `playwright`: profile cố định, giữ session tương tác (Shopify admin SSO, 2FA). Dùng cho việc cần login tay.
- Server `playwright-2`, `playwright-3`: `--isolated` + `storageState` login sẵn (`playwright/.auth/mcp-isolated.json`, gồm portal + mở khoá 2 storefront + Shopify admin nếu `shopify.json` còn hạn). Mỗi lần server khởi động là một context sạch. Session hết hạn → `node scripts/make-mcp-storage-state.mjs` rồi restart Claude Code.
- Mỗi issue một server. Tài nguyên dùng chung (setting store/account, theme, campaign tái sử dụng) phải giữ quyền qua `scripts/tib_runctl.py`.
- Instance `TIB_STORE_INSTANCE_ID` và `TIB_BOUNDLESS_INSTANCE_ID` dùng chung account → không chạy song song.

## Quan sát chưa xác nhận

- Quota tạo layer-image theo account (429 kéo dài, ≤ 2 request liên tiếp) — ngưỡng cụ thể chưa rõ (L-001).
- Upload bị 422 validation có tính vào daily limit hay không — chưa rõ.

## Production — kiểm tra sau deploy

- **Mặc định production chỉ đọc** (probe khi phân tích, xem `qa-requirement-analysis`). **Ngoại lệ duy nhất:** agent `tib-prod-verify` được tạo/sửa data `[QA-PROD]` và chạy happy case tới hết luồng (ATC, checkout, order) trên **store test production** người dùng cấp (người dùng chốt 2026-11-01).
- Account, store, host: `tests/prod/env.production.json` (chép từ `.example`, không commit) + biến trong `.env` (`TIB_PROD_*`). Store test `<TIB_PROD_STORE_URL>` (instance instance production, plan partner_test), dựng 2026-11-02. **Session portal production** (user account production, người dùng login tay qua Shopify 2026-11-02): `playwright/.auth/prod.json`, profile giữ ở `playwright/.profiles/prod`. Kiểm: `node scripts/tib/prod-login.mjs --check`; hết hạn → chạy `node scripts/tib/prod-login.mjs` (mở Chrome, người dùng login, tự lưu). Data production dựng qua MCP `prod_tib` hoặc `portal.*` (MCP không có mọi field, vd `dpi` của print area).
- Kiểm đã deploy: `scripts/tib/deploy-probe.mjs` (bundle portal), không dựa vào MCP — xem `tests/prod/README.md`.
- Checkout trên production chỉ khi store test dùng thanh toán test/bogus/COD; không chắc → hỏi người dùng. **<TIB_PROD_STORE_URL> dùng Bogus Gateway như staging** (người dùng xác nhận 2026-11-02): thẻ `1` = thành công.
- Fixture production ghi trong `tests/prod/manifest.json` + catalog (môi trường production), không xoá sau verify.

## Dấu hiệu khi thao tác

| Dấu hiệu | Cách xử lý |
|---|---|
| Trang "Verify you are human" trên storefront | Bot protection của Shopify. Nghỉ vài phút, dùng browser đã vào được |
