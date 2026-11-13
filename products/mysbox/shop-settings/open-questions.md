# Open Questions — shop-settings

## OQ-shop-settings-001 — CONFLICT

```json
{"oq_id":"OQ-shop-settings-001","type":"CONFLICT","feature_id":"general-settings","summary":"Giá trị nhỏ nhất của Buyback limit time mâu thuẫn ngay trong cùng tài liệu: ghi 'tối thiểu 1' nhưng gợi ý trên ô có 0.5. Cần dev xác nhận form chấp nhận 0.5 giờ hay từ chối (tối thiểu 1), và có nhận số thập phân không — trước khi viết boundary test.","side_a":"Tài liệu \"General Settings\" §Bảng setting: Buyback limit time mặc định 24, tối thiểu 1.","side_b":"Tài liệu \"General Settings\" §Bảng setting: ô Buyback limit time gợi ý \"e.g., 0.5, 1, 24\".","conflict_group":"CONF-merchant-app-05","kb_ids":["general-settings#KB-023","general-settings#KB-024"],"check_ids":["general-settings:CHK-011"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-005 / CONF-merchant-app-05: 2026-10-17: Ô Buyback limit time khoá trên gói Free: min=\"1\" và placeholder \"e.g., 0.5, 1, 24\" cùng có trên UI; không nhập/lưu thử được nên validation khi lưu chưa biết.","staging_observation_kb_ids":["general-settings#KB-059"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-merchant-app-005"}
```

## OQ-shop-settings-002 — CONFLICT

```json
{"oq_id":"OQ-shop-settings-002","type":"CONFLICT","feature_id":"general-settings","summary":"Mốc bắt đầu cửa sổ resell mâu thuẫn ngay trong cùng tài liệu: nhãn UI nói tính từ lúc đơn được tạo, phần mô tả nói tính từ lúc đơn paid. Cần xác nhận mốc thực tế (nếu đơn chỉ được tạo trong app khi nhận webhook paid thì hai mốc trùng nhau). Phía mô tả 'tính từ lúc đơn paid' thuộc shard feature thiết lập resell. Các tài liệu resell khác nói cửa sổ tính từ lúc draw (random quà), mà draw xảy ra khi app nhận webhook đơn paid; cần dev xác nhận mốc bắt đầu thực tế (lúc tạo đơn, lúc paid hay lúc draw) và các mốc này có trùng nhau không.","side_a":"Tài liệu \"General Settings\" §Bảng setting: nhãn \"Duration for customers to resell from order is created\" (hours).","side_b":"Tài liệu \"General Settings\" §Bảng setting: Buyback limit time là độ dài cửa sổ resell, tính từ lúc đơn paid.","conflict_group":"CONF-merchant-app-01","kb_ids":["general-settings#KB-021","resell-setup-and-eligibility#KB-008"],"check_ids":["general-settings:CHK-012"],"supersedes":"OQ-merchant-app-006"}
```

## OQ-shop-settings-003 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-003","type":"OPEN_ISSUE","feature_id":"general-settings","summary":"Mặc định phía server (khi chưa lưu) của \"Store credit app\" là Koin hay None? — Shop chưa từng lưu mục Koin: không biết store credit đang Koin hay None, ảnh hưởng nút trả bằng store credit.","kb_ids":["general-settings#KB-032","general-settings#KB-033"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-026: 2026-10-17: Form hiện \"Koin\" trong khi GET users/config trả {data:null} — field vắng, mặc định phía server không lộ qua API. Khách vãng lai không thấy block store credit (không tách được nguyên nhân).","staging_observation_kb_ids":["general-settings#KB-061","general-settings#KB-062"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-026"}
```

## OQ-shop-settings-004 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-004","type":"OPEN_ISSUE","feature_id":"general-settings","summary":"Khoảng hợp lệ và validation của \"Auto-unbox after\" và \"Trigger before\" (min/max, số nguyên, cho phép 0, để trống)? — Không có boundary để viết test validation mục Auto-Unbox.","kb_ids":["general-settings#KB-014","general-settings#KB-019"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-027: 2026-10-17: Chỉ trạng thái ban đầu (checkbox tắt, ô ẩn) — KB-058; validation không quan sát (classifier).","staging_observation_kb_ids":["general-settings#KB-058"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-027"}
```

## OQ-shop-settings-005 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-005","type":"OPEN_ISSUE","feature_id":"general-settings","summary":"Nguyên tắc chỉ áp cho đơn tạo sau thời điểm lưu có áp cho setting không gắn với lịch đơn (Koin, công tắc Flow, khoá metafield) hay chỉ cho lịch auto-unbox/resell? — Quyết định expected result khi đổi setting với đơn đang mở.","kb_ids":["general-settings#KB-009"],"supersedes":"OQ-merchant-app-028"}
```

## OQ-shop-settings-006 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-006","type":"OPEN_ISSUE","feature_id":"general-settings","summary":"Merchant/staff role nào trên Shopify được mở và lưu General Settings? — Phân quyền portal cho màn này không được nêu.","kb_ids":["_object-level#KB-006","general-settings#KB-001"],"supersedes":"OQ-merchant-app-029"}
```

## OQ-shop-settings-007 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-007","type":"OPEN_ISSUE","feature_id":"general-settings","summary":"Ai bật hide_watermark (merchant, nhân viên, theo gói) và ở đâu? — Quyết định test watermark theo role/plan.","kb_ids":["general-settings#KB-052"],"supersedes":"OQ-merchant-app-030"}
```

## OQ-shop-settings-008 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-008","type":"OPEN_ISSUE","feature_id":"general-settings","summary":"Tag đơn sinh theo mẫu khi vượt giới hạn độ dài thì bị cắt, bỏ qua hay báo lỗi? — Không có hành vi khi vượt giới hạn cho mẫu tag đơn.","kb_ids":["general-settings#KB-045","general-settings#KB-046"],"supersedes":"OQ-merchant-app-031"}
```

## OQ-shop-settings-009 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-009","type":"OPEN_ISSUE","feature_id":"general-settings","summary":"Các gói khác ngoài Free/Early-bird có dùng animation Gacha machine mặc định không, và Free/Early-bird khi cờ tắt thấy gì? — Tài liệu chỉ nêu cờ cho phép Free/Early-bird dùng, không nêu hành vi khi tắt.","kb_ids":["general-settings#KB-040","general-settings#KB-041"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-032: 2026-10-17: Shop gói Free: Gacha hiện xám, không chọn được, không badge/tooltip. Gói khác và giá trị cờ enable_gacha_machine chưa quan sát.","staging_observation_kb_ids":["general-settings#KB-065"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-032"}
```

## OQ-shop-settings-010 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-010","type":"OPEN_ISSUE","feature_id":"general-settings","summary":"recent_pulls_visible_from dùng định dạng ngày nào và so sánh theo múi giờ nào? — Boundary test lọc feed Recent pulls.","kb_ids":["general-settings#KB-051"],"supersedes":"OQ-merchant-app-033"}
```

## OQ-shop-settings-011 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-011","type":"OPEN_ISSUE","feature_id":"general-settings","summary":"skip_order_line_item_sync và Exclude Test Order nằm ở đâu trong back-office và ai bật được? — Cần biết vị trí và người thao tác để dựng data kiểm.","kb_ids":["dashboard-and-analytics#KB-046","general-settings#KB-042"],"supersedes":"OQ-merchant-app-034"}
```

## OQ-shop-settings-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-012","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Các setting ẩn recent_pulls_publish_test_orders, share_unboxing_enabled, share_image_daily_limit chỉ có trên nhánh build-staging, chưa lên production. Cần xác nhận khi nào lên production và giá trị mặc định/hành vi trên production.","kb_ids":["general-settings#KB-053","general-settings#KB-054","general-settings#KB-055"],"supersedes":"OQ-merchant-app-078"}
```

## OQ-shop-settings-013 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-013","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Bấm \"Discard\" trên màn General Settings thì form trở về giá trị đã lưu gần nhất (hay giá trị mặc định nếu mục chưa từng lưu), có hộp xác nhận không, và thanh Save/Discard có ẩn đi không?","check_ids":["general-settings:CHK-003"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-079: 2026-10-17: Mục chưa từng lưu: Discard không hỏi xác nhận, form về giá trị đang hiển thị (Variant SKU), thanh ẩn, không request. Mục đã từng lưu chưa quan sát.","staging_observation_kb_ids":["general-settings#KB-064"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-merchant-app-079"}
```

## OQ-shop-settings-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-014","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Nguyên tắc \"giá trị đã lưu chỉ áp cho đơn tạo sau thời điểm lưu\" có áp cho cả các setting không gắn với lịch đơn (khoá metafield quà, Store credit app, công tắc Shopify Flow) không, hay chỉ cho lịch auto-unbox và cửa sổ resell?","check_ids":["general-settings:CHK-008"],"supersedes":"OQ-merchant-app-080"}
```

## OQ-shop-settings-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-015","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["general-settings:CHK-015","general-settings:CHK-019"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-081: 2026-10-17: Koin: Store credit app \"Koin\" (None/Koin), key trống; 5 mục không có setting ẩn (gacha, watermark, physical_tag, skip_line_item_sync, Exclude Test Order). Phần lưu Koin (CHK-015) không làm.","staging_observation_kb_ids":["general-settings#KB-057","general-settings#KB-061"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-merchant-app-081"}
```

## OQ-shop-settings-016 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-016","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Khi shop chưa từng lưu mục Koin, mặc định phía server của \"Store credit app\" là Koin hay None, và khi đó khách có thấy lựa chọn mua box bằng store credit không?","check_ids":["general-settings:CHK-016"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-082: 2026-10-17: API trả data null (không có field); form hiện Koin; khách vãng lai không thấy gì từ block \"Buy box by store credit\". Mặc định server chưa đọc được.","staging_observation_kb_ids":["general-settings#KB-061","general-settings#KB-062"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-merchant-app-082"}
```

## OQ-shop-settings-017 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-017","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Lưu Koin private API Key không hợp lệ thì có bị từ chối không và thông báo gì; khi chuyển Store credit app sang None thì giảm giá tự động mua bằng store credit đã tạo có bị gỡ không?","check_ids":["general-settings:CHK-017"],"supersedes":"OQ-merchant-app-083"}
```

## OQ-shop-settings-018 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-018","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Tài liệu ghi ba setting ẩn chỉ có trên nhánh build-staging với mặc định recent_pulls_publish_test_orders Tắt, share_unboxing_enabled Bật, share_image_daily_limit 300. Các mặc định này có phải là hành vi mong đợi không, khi nào chúng lên production và mặc định trên production là gì?","check_ids":["general-settings:CHK-022"],"supersedes":"OQ-merchant-app-084"}
```

## OQ-shop-settings-019 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-019","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Khoảng hợp lệ của \"Auto-unbox after\" và \"Trigger before\" là gì (cho phép 0, số thập phân, để trống không, giá trị tối đa, Trigger before có được lớn hơn Auto-unbox after không) và form báo lỗi gì khi nhập sai?","check_ids":["general-settings:CHK-023"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-085: 2026-10-17: Như OQ-merchant-app-027.","staging_observation_kb_ids":["general-settings#KB-058"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-merchant-app-085"}
```

## OQ-shop-settings-020 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-020","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Mọi nhân viên Shopify được phép mở app có được lưu General Settings không, hay việc lưu còn phụ thuộc quyền Shopify cụ thể nào của nhân viên?","check_ids":["general-settings:CHK-024"],"supersedes":"OQ-merchant-app-086"}
```

## OQ-shop-settings-021 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-021","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Trên staging, shop gói Free thấy công tắc Shopify Flow không bị khoá và trang Pricing không nhắc Flow. Shopify Flow có dùng được ở mọi gói (kể cả Free) không, và bật/lưu công tắc trên gói Free có được chấp nhận không?","kb_ids":["general-settings#KB-063","_object-level.automation-growth#KB-006"],"check_ids":["general-settings:CHK-025"],"tags":["staging-observed"],"supersedes":"OQ-merchant-app-112"}
```

## OQ-shop-settings-022 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-022","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Trên staging, Gacha bị khoá với shop gói Free mà không có lời giải thích hay gợi ý nâng gói. Đây có phải thiết kế (Gacha chỉ mở khi nhân viên bật enable_gacha_machine hoặc ở gói trả phí) không, và có cần hiện lý do khoá cho merchant không?","kb_ids":["general-settings#KB-065"],"check_ids":["general-settings:CHK-026"],"tags":["staging-observed"],"supersedes":"OQ-merchant-app-113"}
```

## OQ-shop-settings-023 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-023","type":"OPEN_ISSUE","feature_id":"general-settings","summary":"Mục \"Auto-unbox notification\" nằm ở đâu — staging chỉ có 5 mục (Auto-Unbox, Buyback limit time, Order setting, Koin, Shopify Flow), không có mục riêng; nó hiện trong mục Auto-Unbox khi bật \"Enable auto-unbox\", hay không có trên màn hình? — KB-056 nói General Settings có mục Auto-unbox notification; không định vị được thì không viết được check cho mục này.","kb_ids":["general-settings#KB-056","general-settings#KB-057","general-settings#KB-058"],"tags":["staging-observed"],"supersedes":"OQ-merchant-app-116"}
```

## OQ-shop-settings-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-024","type":"NEEDS_CONFIRMATION","feature_id":"general-settings","summary":"Quan sát staging mới chạm vùng rủi ro cao (quyền truy cập / tiền / billing): Block \"Buy box by store credit\" không render gì với khách vãng lai; Mục Shopify Flow: công tắc tắt, không khoá theo gói; Form box trên shop Free: Gacha hiện xám, không chọn được, không giải thích. Item là OBSERVED_CURRENT; cần PO xác nhận đây là hành vi dự kiến trước khi dùng làm expected result.","kb_ids":["general-settings#KB-062","general-settings#KB-063","general-settings#KB-065"],"tags":["staging-observed","risk-flag"],"supersedes":"OQ-merchant-app-118"}
```

## OQ-shop-settings-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-025","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Bộ tài liệu nguồn không chỉ định role mặc định cho object này (bootstrap-request để role null): các KB item mang scope.role theo vai trò tài liệu nêu cho từng hành vi, hoặc \"unspecified\" khi tài liệu không nêu. Cần PO/Dev xác nhận ma trận role → quyền thực tế trên production (merchant owner/staff, khách, admin Mysbox theo từng role) trước khi dùng các check PERMISSION làm oracle.","supersedes":"OQ-storefront-widget-001"}
```

## OQ-shop-settings-026 — CONFLICT

```json
{"oq_id":"OQ-shop-settings-026","type":"CONFLICT","feature_id":"storefront-data-sync","summary":"Ngưỡng trễ được coi là bình thường giữa thay đổi (tồn kho/plan) và dữ liệu trên widget: một phút hay vài phút? Cùng một playbook nêu hai con số khác nhau.","side_a":"Playbook 3 (storefront, widget, theme và trang khách), phần mở đầu: trễ một phút là bình thường","side_b":"Playbook 3 §Box báo hết hàng mà tồn kho còn: trễ vài phút là bình thường","conflict_group":"CONF-storefront-widget-02","kb_ids":["storefront-data-sync#KB-041","storefront-data-sync#KB-044"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-002 / CONF-storefront-widget-02: 2026-10-17: Một đơn Bogus: tồn kho trên widget đổi trong ≤ 23 giây sau paid (mẫu đầu +23s đã đổi), không đổi thêm tới +5 phút. Không trả lời được \"ngưỡng bình thường\" là 1 phút hay vài phút — đó là câu hỏi về expected.","staging_observation_kb_ids":["storefront-data-sync#KB-048"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-storefront-widget-002"}
```

## OQ-shop-settings-027 — CONFLICT

```json
{"oq_id":"OQ-shop-settings-027","type":"CONFLICT","feature_id":"storefront-data-sync","summary":"Độ trễ của khối hiển thị tồn kho trên storefront: vài giây (tài liệu tồn kho) hay một phút / vài phút (playbook storefront)?","side_a":"Tài liệu \"Tồn kho, pool, sold-out và hiển thị tồn kho\" §Hiển thị tồn kho trên storefront: có thể trễ vài giây so với lần bốc","side_b":"Playbook 3 (storefront, widget, theme và trang khách): trễ một phút (phần mở đầu) hoặc vài phút (§Box báo hết hàng mà tồn kho còn) là bình thường","conflict_group":"CONF-storefront-widget-03","kb_ids":["storefront-data-sync#KB-006","storefront-data-sync#KB-041","storefront-data-sync#KB-044"],"check_ids":["storefront-data-sync:CHK-019"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-003 / CONF-storefront-widget-03: 2026-10-17: Độ trễ quan sát ≤ 23 giây (dưới 1 phút); mốc dưới trong 23 giây đầu không đo được; một đơn.","staging_observation_kb_ids":["storefront-data-sync#KB-048"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-storefront-widget-003"}
```

## OQ-shop-settings-028 — CONFLICT

```json
{"oq_id":"OQ-shop-settings-028","type":"CONFLICT","feature_id":"storefront-data-sync","summary":"Tồn kho từng món trên widget lấy từ đâu: gọi Storefront API của Shopify (luôn mới nhất) hay từ dữ liệu đã publish do app ghi lên biến thể (có thể cũ)?","side_a":"Tài liệu \"Dữ liệu storefront: metafield hay app proxy?\" §Widget ở trang sản phẩm đọc gì: tên, ảnh, giá, tồn kho từng món gọi Storefront API bằng token công khai","side_b":"Playbook 3 (storefront, widget, theme và trang khách), phần mở đầu: widget không đọc tồn kho trực tiếp từ Shopify mà đọc dữ liệu đã publish","conflict_group":"CONF-storefront-widget-04","kb_ids":["storefront-data-sync#KB-019","storefront-data-sync#KB-039"],"check_ids":["storefront-data-sync:CHK-020"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-004 / CONF-storefront-widget-04: 2026-10-17: Trên staging số tồn kho widget lấy từ metafield mysbox.box in ra trong Liquid (pools/quantity); Storefront API không có quantityAvailable và getProducts trả metafield null.","staging_observation_kb_ids":["storefront-data-sync#KB-049"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-storefront-widget-004"}
```

## OQ-shop-settings-029 — CONFLICT

```json
{"oq_id":"OQ-shop-settings-029","type":"CONFLICT","feature_id":"widget-translations","summary":"Chuỗi mặc định hiển thị tồn kho còn lại trên widget trang sản phẩm: `{remaining-items}/{total-items} left` (bảng Content & Translation, nhóm Product) hay `{quantity}/{total} left` (mặc định của itemStockText trong window.Mysbox)? Là cùng một chuỗi với hai cú pháp placeholder hay hai chuỗi khác nhau, và khách thực sự thấy chuỗi nào khi không có custom_script?","side_a":"Tài liệu \"Widget storefront, theme block, dịch văn bản, custom CSS/JS\" §Bước 3 — Dịch văn bản: `{remaining-items}/{total-items} left`","side_b":"Cùng tài liệu §Bước 4 — Custom CSS / JS: itemStockText mặc định `{quantity}/{total} left`","conflict_group":"CONF-storefront-widget-01","kb_ids":["widget-custom-code#KB-008","widget-translations#KB-011"],"check_ids":["widget-translations:CHK-018"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-005 / CONF-storefront-widget-01: 2026-10-17: Không có custom script: khách thấy \"3/3 left\"; itemStockText không đặt nên bundle rơi về item_stock_left \"{remaining-items}/{total-items} left\" (cùng chuỗi với bảng Content & Translation); không thấy cú pháp {quantity}/{total}.","staging_observation_kb_ids":["widget-translations#KB-038","widget-custom-code#KB-024","widget-custom-code#KB-025"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-storefront-widget-005"}
```

## OQ-shop-settings-030 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-030","type":"OPEN_ISSUE","feature_id":"storefront-data-sync","summary":"Hạn chế đã biết: metafield storefront bị cũ khi lần đẩy thất bại (widget hiện món/tồn kho cũ, \"sold out\" sai). Có retry/cảnh báo không, mức độ nghiêm trọng và kế hoạch sửa?","kb_ids":["storefront-data-sync#KB-013","storefront-data-sync#KB-034","storefront-data-sync#KB-035"],"check_ids":["storefront-data-sync:CHK-022"],"supersedes":"OQ-storefront-widget-006"}
```

## OQ-shop-settings-031 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-031","type":"OPEN_ISSUE","feature_id":"storefront-data-sync","summary":"Hạn chế đã biết: cờ capacity đã publish có thể cũ sau khi đổi plan, làm widget/khối unbox bị ẩn dù plan đã ổn. Mức độ nghiêm trọng và trạng thái sửa?","kb_ids":["storefront-data-sync#KB-036"],"check_ids":["storefront-data-sync:CHK-023"],"supersedes":"OQ-storefront-widget-007"}
```

## OQ-shop-settings-032 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-032","type":"OPEN_ISSUE","feature_id":"storefront-data-sync","summary":"Danh sách đầy đủ các thời điểm Mysbox ghi metafield ngoài publish box và đổi gói, và các namespace/key cụ thể được ghi vào biến thể khi publish. — Tester cần biết hành động nào phải làm mới widget và side effect nào cần kiểm trên Shopify.","kb_ids":["storefront-data-sync#KB-011","storefront-data-sync#KB-015","storefront-data-sync#KB-022"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-008: 2026-10-17: Variant chỉ có metafield mysbox.box: ghi khi publish, pools cập nhật sau đơn, giữ với published_at null khi Deactivate, không ghi lại khi Save lúc Draft. Danh sách đầy đủ thời điểm ghi vẫn cần Dev.","staging_observation_kb_ids":["storefront-data-sync#KB-047","storefront-data-sync#KB-048","storefront-data-sync#KB-051","storefront-data-sync#KB-052"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-storefront-widget-008"}
```

## OQ-shop-settings-033 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-033","type":"OPEN_ISSUE","feature_id":"storefront-data-sync","summary":"Deactivate (về Draft) box có xoá metafield mysbox.box không, hay chỉ xoá khi xoá box? — Ảnh hưởng dữ liệu storefront và điều kiện ẩn widget khi box Draft.","kb_ids":["storefront-data-sync#KB-003","storefront-data-sync#KB-025","storefront-data-sync#KB-042"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-009: 2026-10-17: Deactivate (POST /unpublish) KHÔNG xoá metafield mysbox.box; ~1 phút sau metafield còn, chỉ published_at = null; widget không render. Trường hợp xoá box không thử (cấm).","staging_observation_kb_ids":["storefront-data-sync#KB-051"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-storefront-widget-009"}
```

## OQ-shop-settings-034 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-034","type":"OPEN_ISSUE","feature_id":"storefront-data-sync","summary":"Ở shop dùng Shopify Markets (đa tiền tệ), widget hiển thị ký hiệu tiền tệ nào và checkout tính theo tiền tệ nào? — Tài liệu chỉ nói \"không quy đổi\"; thiếu expected result cho shop đa tiền tệ.","kb_ids":["storefront-data-sync#KB-021"],"supersedes":"OQ-storefront-widget-010"}
```

## OQ-shop-settings-035 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-035","type":"OPEN_ISSUE","feature_id":"storefront-data-sync","summary":"Token công khai Storefront API được cấp/quản lý thế nào, và widget hành xử ra sao khi lời gọi Storefront API thất bại? — Case lỗi mạng/token cho widget chưa có expected result.","kb_ids":["storefront-data-sync#KB-007","storefront-data-sync#KB-023"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-011: 2026-10-17: Token Storefront API nằm ở window._Mysbox.storefrontToken và được gửi qua header X-Shopify-Storefront-Access-Token; cách cấp/quản lý token và hành vi khi lỗi không quan sát được.","staging_observation_kb_ids":["storefront-data-sync#KB-050"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-storefront-widget-011"}
```

## OQ-shop-settings-036 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-036","type":"OPEN_ISSUE","feature_id":"storefront-data-sync","summary":"Hai plan đặc biệt vĩnh viễn được miễn điều kiện ẩn widget/khối unbox theo trạng thái hết hạn là plan nào? — Cần để kiểm điều kiện ẩn widget theo plan.","kb_ids":["storefront-data-sync#KB-043"],"supersedes":"OQ-storefront-widget-012"}
```

## OQ-shop-settings-037 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-037","type":"OPEN_ISSUE","feature_id":"widget-custom-code","summary":"Hạn chế đã biết: JS tuỳ biến lỗi cú pháp trong Customizations có thể làm hỏng widget, không có cơ chế chặn được nêu. Có kế hoạch validate/chặn không?","kb_ids":["widget-custom-code#KB-016"],"check_ids":["widget-custom-code:CHK-013"],"supersedes":"OQ-storefront-widget-013"}
```

## OQ-shop-settings-038 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-038","type":"OPEN_ISSUE","feature_id":"widget-custom-code","summary":"Ai được sửa ô Customizations: chỉ admin nội bộ có quyền update_customizations, hay support có role riêng; merchant có bao giờ được sửa không? — Feature xoay quanh \"ai được sửa\"; cần ma trận role để viết check permission.","kb_ids":["widget-custom-code#KB-001","widget-custom-code#KB-004","widget-custom-code#KB-018"],"supersedes":"OQ-storefront-widget-014"}
```

## OQ-shop-settings-039 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-039","type":"OPEN_ISSUE","feature_id":"widget-custom-code","summary":"Nơi lưu (bảng/field) của các field Customizations và metafield custom_style/custom_script gắn ở owner nào (shop, sản phẩm hay biến thể)? — Không có data model thì không kiểm dữ liệu custom code được.","kb_ids":["widget-custom-code#KB-017"],"supersedes":"OQ-storefront-widget-015"}
```

## OQ-shop-settings-040 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-040","type":"OPEN_ISSUE","feature_id":"widget-custom-code","summary":"Giá trị mặc định của các tuỳ chọn window.Mysbox / window.MysboxCustomOptions khác (ngoài remainText). — Cần baseline để kiểm hành vi khi không có custom script.","kb_ids":["widget-custom-code#KB-007","widget-custom-code#KB-011"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-016: 2026-10-17: window.Mysbox và window.MysboxCustomOptions đều undefined (không có object mặc định); bundle widget rơi về itemStockText → item_stock_left, remainText → remain_text, currencyPrecision 100. Mặc định của MysboxCustomOptions (bundle trang khách) chưa kiểm.","staging_observation_kb_ids":["widget-custom-code#KB-024","widget-custom-code#KB-025"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-storefront-widget-016"}
```

## OQ-shop-settings-041 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-041","type":"OPEN_ISSUE","feature_id":"widget-theme-embed-setup","summary":"Hạn chế tương thích theme đã biết: widget không nhận ra form add-to-cart của một số theme, và cart drawer đặc thù làm vỡ layout widget. Danh sách theme bị ảnh hưởng và trạng thái sửa?","kb_ids":["widget-theme-embed-setup#KB-039","widget-theme-embed-setup#KB-042"],"check_ids":["widget-theme-embed-setup:CHK-026","widget-theme-embed-setup:CHK-027"],"supersedes":"OQ-storefront-widget-017"}
```

## OQ-shop-settings-042 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-042","type":"OPEN_ISSUE","feature_id":"widget-theme-embed-setup","summary":"Giá trị mặc định và biên của các tuỳ chọn Style Settings ngoài \"Hide item price\" (Image size min/max, Maximum number of groups shown mặc định, Box item is shown as mặc định...). — Không có default/boundary thì không test giá trị biên được.","kb_ids":["widget-theme-embed-setup#KB-026","widget-theme-embed-setup#KB-027"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-018: 2026-10-17: Đã ghi mặc định mọi tuỳ chọn Item list (Image size 200 min 20 không max/step, Maximum groups 2 min 1...) và cách client kẹp giá trị ngoài biên; không có \"Box item is shown as\" (mở CONF-storefront-widget-05). Validate phía server khi Save không thử; mỗi giá trị biên một lần.","staging_observation_kb_ids":["widget-theme-embed-setup#KB-046","widget-theme-embed-setup#KB-047"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-storefront-widget-018"}
```

## OQ-shop-settings-043 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-043","type":"OPEN_ISSUE","feature_id":"widget-theme-embed-setup","summary":"Hành vi trên production và staging chưa được xác minh — toàn bộ profile dựng từ tài liệu. — Mọi rule là expected theo tài liệu dev; chưa có quan sát runtime để đối chiếu.","kb_ids":["widget-theme-embed-setup#KB-003"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-019: 2026-10-17: Staging: embed Active, 5 block Installed, widget mount với watermark trên trang product. Production chưa xác minh.","staging_observation_kb_ids":["widget-theme-embed-setup#KB-044","widget-theme-embed-setup#KB-045","widget-theme-embed-setup#KB-048"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-storefront-widget-019"}
```

## OQ-shop-settings-044 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-044","type":"OPEN_ISSUE","feature_id":"widget-translations","summary":"Hạn chế đã biết của bản dịch: hai bản (dữ liệu app/dữ liệu shop) lệch khi ghi bản thứ hai thất bại; lưu hai ngôn ngữ cùng lúc có thể ghi đè nhau; chuỗi unboxing lấy từ khoá dịch của product. Mức độ nghiêm trọng và trạng thái sửa?","kb_ids":["widget-translations#KB-031","widget-translations#KB-032","widget-translations#KB-033"],"check_ids":["widget-translations:CHK-020","widget-translations:CHK-021","widget-translations:CHK-022"],"supersedes":"OQ-storefront-widget-020"}
```

## OQ-shop-settings-045 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-045","type":"OPEN_ISSUE","feature_id":"widget-translations","summary":"Banner gói Free ở Content & Translation có nội dung gì; gói Free bấm lưu thì UI phản hồi thế nào (nút khoá, thông báo nâng gói hay lỗi) và có sửa được không? — Tài liệu chỉ nói \"chỉ thấy banner\" / \"không lưu được\"; expected result cần thông điệp/trạng thái UI cụ thể.","kb_ids":["widget-translations#KB-001","widget-translations#KB-002"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-021: 2026-10-17: Banner gói Free nguyên văn đã ghi; trang vẫn hiện form, không có nút Save khi chưa sửa nên chưa có phản hồi lưu (mở CONF-storefront-widget-06).","staging_observation_kb_ids":["widget-translations#KB-035"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-storefront-widget-021"}
```

## OQ-shop-settings-046 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-046","type":"OPEN_ISSUE","feature_id":"widget-translations","summary":"Danh sách đầy đủ chuỗi mặc định của từng nhóm dịch. — Bảng chỉ ghi ví dụ; không kiểm hết được chuỗi.","kb_ids":["widget-translations#KB-008","widget-translations#KB-010","widget-translations#KB-013"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-022: 2026-10-17: Có đủ 16 chuỗi mặc định nhóm general-settings và chuỗi mặc định Product page từ bundle; các nhóm unboxing/buyback-widget/order/share-unboxing trả data null qua API nên chuỗi mặc định của chúng chưa thấy. | 2026-10-17: Bổ sung ngoài outcome: \"Auto-open in: {time}\" (ví dụ ở KB-008) không có trong 16 key general-settings; 6 tab dịch còn lại chưa mở.","staging_observation_kb_ids":["widget-translations#KB-036","widget-translations#KB-037","widget-translations#KB-038"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-storefront-widget-022"}
```

## OQ-shop-settings-047 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-047","type":"OPEN_ISSUE","feature_id":"widget-translations","summary":"Khi merchant dịch cả phần trong ngoặc nhọn thì hệ thống xử lý thế nào (validate, chặn lưu, hay hiển thị sai)? — Tài liệu chỉ nêu cảnh báo; hành vi khi vi phạm chưa mô tả.","kb_ids":["widget-translations#KB-006"],"supersedes":"OQ-storefront-widget-023"}
```

## OQ-shop-settings-048 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-048","type":"OPEN_ISSUE","feature_id":"widget-translations","summary":"Danh sách đầy đủ metafield bản dịch của shop (tài liệu liệt kê 3 key rồi \"...\"). — Không kiểm được đủ phạm vi dịch nếu không biết hết key.","kb_ids":["widget-translations#KB-029"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-024: 2026-10-17: Nguồn dịch thấy phía client: _Mysbox.mysboxTranslation / mysboxProductPageTranslation / mysboxUnboxingTranslation và 5 endpoint /apps/mysbox/api/translations/*; tên metafield shop không thấy phía client.","staging_observation_kb_ids":["widget-translations#KB-037"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-storefront-widget-024"}
```

## OQ-shop-settings-049 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-049","type":"OPEN_ISSUE","feature_id":"widget-translations","summary":"Danh sách ngôn ngữ ở \"Select language\" có giới hạn theo các ngôn ngữ shop đã publish trên Shopify không? — Ảnh hưởng check chọn ngôn ngữ và trạng thái \"No locale found\".","kb_ids":["widget-translations#KB-003","widget-translations#KB-004"],"supersedes":"OQ-storefront-widget-025"}
```

## OQ-shop-settings-050 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-050","type":"NEEDS_CONFIRMATION","feature_id":"storefront-data-sync","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["storefront-data-sync:CHK-004","storefront-data-sync:CHK-007","storefront-data-sync:CHK-008","storefront-data-sync:CHK-013","storefront-data-sync:CHK-024"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-026: 2026-10-17: CHK-007: widget ở chế độ tồn kho không hiện giá item; CHK-024: khách vãng lai đọc được config shop + bản dịch trong HTML trang. CHK-004/008/013 không quan sát. Không thay authority.","staging_observation_kb_ids":["storefront-data-sync#KB-053","_object-level.storefront-widget#KB-006"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-storefront-widget-026"}
```

## OQ-shop-settings-051 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-051","type":"NEEDS_CONFIRMATION","feature_id":"storefront-data-sync","summary":"QA quan sát tần suất ghi metafield lên biến thể (giới hạn 5 lần mỗi giây mỗi shop) ở đâu: log ứng dụng, admin panel hay công cụ của Shopify? Các lần ghi vượt giới hạn được xếp hàng hay bị bỏ?","kb_ids":["storefront-data-sync#KB-005","storefront-data-sync#KB-040"],"check_ids":["storefront-data-sync:CHK-018"],"supersedes":"OQ-storefront-widget-027"}
```

## OQ-shop-settings-052 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-052","type":"NEEDS_CONFIRMATION","feature_id":"storefront-data-sync","summary":"Khi merchant sửa chance trong Mysbox mà chưa publish lại, widget có tiếp tục hiện chance cũ cho tới khi metafield được ghi lại không; sửa box có tự kích hoạt ghi lại metafield hay chỉ khi publish?","check_ids":["storefront-data-sync:CHK-021"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-028: 2026-10-17: Save khi Draft tạo version mới, không tự publish, metafield vẫn giữ chance cũ (v3026) sau ~47s; chance trên widget không quan sát được vì widget ẩn khi Draft; publish lại không thử.","staging_observation_kb_ids":["storefront-data-sync#KB-052","storefront-data-sync#KB-053"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-storefront-widget-028"}
```

## OQ-shop-settings-053 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-053","type":"NEEDS_CONFIRMATION","feature_id":"widget-custom-code","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["widget-custom-code:CHK-001","widget-custom-code:CHK-002","widget-custom-code:CHK-003"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-029: 2026-10-17: CHK-001: staging không có ô nhập CSS/JS tự do cho merchant. CHK-002/003 cần admin panel — không quan sát.","staging_observation_kb_ids":["widget-custom-code#KB-026"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-storefront-widget-029"}
```

## OQ-shop-settings-054 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-054","type":"NEEDS_CONFIRMATION","feature_id":"widget-custom-code","summary":"Ai được sửa ô Customizations của shop: chỉ admin nội bộ có quyền update_customizations, hay support có role riêng? Support bật custom CSS/JS cho shop ở đâu, và \"nhân viên\" nhập CSS/JS là nhân viên của bên nào?","check_ids":["widget-custom-code:CHK-004"],"supersedes":"OQ-storefront-widget-030"}
```

## OQ-shop-settings-055 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-055","type":"NEEDS_CONFIRMATION","feature_id":"widget-custom-code","summary":"Chữ của tuỳ chọn remainText (mặc định \"Remain\") hiển thị ở vị trí nào trên widget và trong điều kiện nào; các tuỳ chọn khác của window.Mysbox và window.MysboxCustomOptions có giá trị mặc định là gì?","kb_ids":["widget-custom-code#KB-009"],"check_ids":["widget-custom-code:CHK-009"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-031: 2026-10-17: Dòng box hiện \"Remaining boxes: x/y\" bên phải tiêu đề \"Box items\" (box Single, tracked, show_item_stock true); không thấy chữ \"Remain\" (mở CONF-storefront-widget-07). Mặc định các tuỳ chọn khác chỉ thấy một phần.","staging_observation_kb_ids":["widget-custom-code#KB-025","widget-custom-code#KB-024"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-storefront-widget-031"}
```

## OQ-shop-settings-056 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-056","type":"NEEDS_CONFIRMATION","feature_id":"widget-custom-code","summary":"Cú pháp và phạm vi của customTranslate là gì (ghi đè theo khoá nào, theo từng ngôn ngữ hay mọi ngôn ngữ), và nó ưu tiên hơn bản dịch trong Content & Translation không?","kb_ids":["widget-custom-code#KB-012"],"check_ids":["widget-custom-code:CHK-012"],"supersedes":"OQ-storefront-widget-032"}
```

## OQ-shop-settings-057 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-057","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["widget-theme-embed-setup:CHK-013"],"supersedes":"OQ-storefront-widget-033"}
```

## OQ-shop-settings-058 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-058","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Ai được bật cờ ẩn watermark \"Powered by Mysbox\" (merchant, nhân viên Mysbox hay tự động theo gói), và bật ở màn hình nào?","kb_ids":["widget-theme-embed-setup#KB-019"],"check_ids":["widget-theme-embed-setup:CHK-017"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-034: 2026-10-17: Gói Free hiện \"Powered by Mysbox\"; merchant không có control ẩn. Ai bật hide_watermark vẫn cần PO.","staging_observation_kb_ids":["widget-theme-embed-setup#KB-048","widget-theme-embed-setup#KB-049"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-storefront-widget-034"}
```

## OQ-shop-settings-059 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-059","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Nhãn chính xác của trang hướng dẫn và nút deep-link trong portal là \"Setup instructions\" / \"Add block to theme editor\" hay \"Instructions\" / \"Add block to theme\"?","kb_ids":["widget-theme-embed-setup#KB-004","widget-theme-embed-setup#KB-041"],"check_ids":["widget-theme-embed-setup:CHK-022"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-035: 2026-10-17: Nhãn trên staging: trang \"Setup instructions\" (route /instructions) và nút \"Add block to theme editor\" — khớp KB-004. Không thay authority cho production.","staging_observation_kb_ids":["widget-theme-embed-setup#KB-045"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-storefront-widget-035"}
```

## OQ-shop-settings-060 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-060","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Dashboard phát hiện app embed/block đã cài bằng cách nào và hiển thị những giá trị trạng thái nào (ngoài \"Active\"); tên nguyên văn của hai block checkout trong bảng trạng thái app extension là gì?","kb_ids":["widget-theme-embed-setup#KB-005","widget-theme-embed-setup#KB-034"],"check_ids":["widget-theme-embed-setup:CHK-023"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-036: 2026-10-17: Tên nguyên văn hai block checkout và request lấy trạng thái (Admin GraphQL App Bridge đọc file theme + checkoutProfiles) đã ghi; chỉ thấy \"Active\"/\"Installed\", logic phía server/client suy trạng thái không quan sát.","staging_observation_kb_ids":["widget-theme-embed-setup#KB-044"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-storefront-widget-036"}
```

## OQ-shop-settings-061 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-061","type":"NEEDS_CONFIRMATION","feature_id":"widget-translations","summary":"Nhóm dịch \"Share unboxing\" chỉ có trên nhánh build-staging. Khi nào lên production, và trên production trang Content & Translation có hiện nhóm này không?","kb_ids":["widget-translations#KB-022","widget-translations#KB-023"],"supersedes":"OQ-storefront-widget-037"}
```

## OQ-shop-settings-062 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-062","type":"NEEDS_CONFIRMATION","feature_id":"widget-translations","summary":"Khi merchant dịch hoặc sửa cả phần trong ngoặc nhọn của một chuỗi, hệ thống xử lý thế nào: chặn lưu, cảnh báo, hay lưu và hiển thị sai trên storefront?","check_ids":["widget-translations:CHK-012"],"supersedes":"OQ-storefront-widget-038"}
```

## OQ-shop-settings-063 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-063","type":"NEEDS_CONFIRMATION","feature_id":"widget-translations","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["widget-translations:CHK-013","widget-translations:CHK-014","widget-translations:CHK-017"],"staging_observation":"Ghi chú quan sát staging cho OQ-storefront-widget-039: 2026-10-17: CHK-013: banner Free ghi nguyên văn, chưa thử lưu; CHK-014: widget hiện chuỗi mặc định. CHK-017 cần admin panel.","staging_observation_kb_ids":["widget-translations#KB-035","widget-translations#KB-038"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-storefront-widget-039"}
```

## OQ-shop-settings-064 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-064","type":"NEEDS_CONFIRMATION","feature_id":"widget-translations","summary":"Nhóm dịch \"Share unboxing\" (chữ ở popup chia sẻ) hiện chỉ có trên nhánh build-staging: khi nào lên production, và trên production trang Content & Translation có hiển thị nhóm này không?","check_ids":["widget-translations:CHK-019"],"supersedes":"OQ-storefront-widget-040"}
```

## OQ-shop-settings-065 — CONFLICT

```json
{"oq_id":"OQ-shop-settings-065","type":"CONFLICT","feature_id":"widget-custom-code","summary":"Giá trị mặc định của remainText: tài liệu ghi \"Remain\"; staging (không có window.Mysbox) hiện \"Remaining boxes: 6/6\" do bundle rơi về remain_text \"Remaining boxes: {remaining-items}/{total-items}\". \"Remain\" là giá trị cũ, giá trị ở surface khác, hay tài liệu sai?","side_a":"Base KB-009 (CE, dev_doc): remainText của window.Mysbox mặc định \"Remain\".","side_b":"Quan sát staging KB-025: không đặt remainText thì dòng box hiện \"Remaining boxes: {remaining-items}/{total-items}\".","conflict_group":"CONF-storefront-widget-07","kb_ids":["widget-custom-code#KB-009","widget-custom-code#KB-025"],"related_oq_ids":["OQ-shop-settings-055"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-041"}
```

## OQ-shop-settings-066 — CONFLICT

```json
{"oq_id":"OQ-shop-settings-066","type":"CONFLICT","feature_id":"widget-theme-embed-setup","summary":"Tài liệu nói Style Settings có tuỳ chọn \"Box item is shown as\" (List / Carousel); trên staging, Item list (Single, Bundle, cả Random by items và Random by groups) và các trang Style Settings đã mở đều không có tuỳ chọn này. Tuỳ chọn đã bị bỏ, nằm ở chỗ khác (setting block trong theme editor?) hay chưa lên staging?","side_a":"Base KB-027 (CE, dev_doc): tuỳ chọn \"Box item is shown as\" có hai giá trị List / Carousel.","side_b":"Quan sát staging KB-047: không có tuỳ chọn này ở Item list và các trang Style Settings đã duyệt.","conflict_group":"CONF-storefront-widget-05","kb_ids":["widget-theme-embed-setup#KB-027","widget-theme-embed-setup#KB-047"],"related_oq_ids":["OQ-shop-settings-042"],"tags":["staging-observed"],"check_ids":["widget-theme-embed-setup:CHK-028"],"supersedes":"OQ-storefront-widget-042"}
```

## OQ-shop-settings-067 — CONFLICT

```json
{"oq_id":"OQ-shop-settings-067","type":"CONFLICT","feature_id":"widget-translations","summary":"Merchant gói Free mở Content & Translation: tài liệu nói chỉ thấy banner; staging hiện banner kèm toàn bộ form (8 tab, input không bị khoá). Expected cho gói Free là chỉ banner hay banner + form chỉ đọc/không lưu được?","side_a":"Base KB-002 (CE, dev_doc): merchant gói Free mở trang chỉ thấy banner.","side_b":"Quan sát staging KB-035: banner \"Translations are not available in the Free plan\" + form đầy đủ, 16 textbox tab General không disabled, không có Save khi chưa sửa.","conflict_group":"CONF-storefront-widget-06","kb_ids":["widget-translations#KB-002","widget-translations#KB-035"],"related_oq_ids":["OQ-shop-settings-045","OQ-shop-settings-063"],"tags":["staging-observed"],"check_ids":["widget-translations:CHK-023"],"supersedes":"OQ-storefront-widget-043"}
```

## OQ-shop-settings-068 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-068","type":"NEEDS_CONFIRMATION","feature_id":"storefront-data-sync","summary":"Staging (1 đơn): tồn kho trên widget cập nhật ≤ 23 giây sau khi đơn paid, chỉ pool của item trúng giảm, chance trong metafield không tính lại. Đây có phải hành vi mong đợi (chance hiển thị không tính lại theo tồn kho còn lại), và độ trễ tối đa chấp nhận được là bao nhiêu?","kb_ids":["storefront-data-sync#KB-048","storefront-data-sync#KB-053"],"check_ids":["storefront-data-sync:CHK-025"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-044"}
```

## OQ-shop-settings-069 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-069","type":"NEEDS_CONFIRMATION","feature_id":"storefront-data-sync","summary":"Staging (một box, 4 lần đọc): variant chỉ có metafield mysbox.box với shape như đã ghi. Đây có phải contract ổn định của metafield (key nào bắt buộc), và Mysbox còn ghi metafield ở những thời điểm nào khác?","kb_ids":["storefront-data-sync#KB-047"],"check_ids":["storefront-data-sync:CHK-026"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-045"}
```

## OQ-shop-settings-070 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-070","type":"NEEDS_CONFIRMATION","feature_id":"storefront-data-sync","summary":"Staging: token Storefront API nằm công khai trong trang (window._Mysbox.storefrontToken) và được widget gửi qua header. Token này được cấp/xoay vòng thế nào, phạm vi quyền của nó là gì, và widget xử lý ra sao khi lời gọi Storefront API lỗi?","kb_ids":["storefront-data-sync#KB-050"],"check_ids":["storefront-data-sync:CHK-027"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-046"}
```

## OQ-shop-settings-071 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-071","type":"NEEDS_CONFIRMATION","feature_id":"storefront-data-sync","summary":"Staging (1 lần): sau Deactivate, widget ẩn nhưng nút Add to cart / Buy it now của biến thể box vẫn hiện và metafield vẫn còn với published_at null. Khách có mua được biến thể box đang Draft không, và đó có phải hành vi mong đợi?","kb_ids":["storefront-data-sync#KB-051"],"check_ids":["storefront-data-sync:CHK-028"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-047"}
```

## OQ-shop-settings-072 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-072","type":"NEEDS_CONFIRMATION","feature_id":"storefront-data-sync","summary":"Staging: Save box ở Draft tạo version mới nhưng không ghi lại metafield variant. Khi Activate lại, metafield có được ghi theo version mới nhất không, và với box đang Active thì Save có ghi lại metafield ngay không?","kb_ids":["storefront-data-sync#KB-052"],"check_ids":["storefront-data-sync:CHK-029"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-048"}
```

## OQ-shop-settings-073 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-073","type":"NEEDS_CONFIRMATION","feature_id":"storefront-data-sync","summary":"Staging: ở chế độ \"Show remaining stock\", thẻ item chỉ hiện \"x/y left\" và không có Chance. Hai chế độ hiển thị (tồn kho / chance) có loại trừ nhau theo thiết kế không, và chế độ \"Show original chance\" hiển thị gì trên storefront?","kb_ids":["storefront-data-sync#KB-053"],"check_ids":["storefront-data-sync:CHK-030"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-049"}
```

## OQ-shop-settings-074 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-074","type":"NEEDS_CONFIRMATION","feature_id":"widget-custom-code","summary":"Staging (shop không có custom code): window.Mysbox và window.MysboxCustomOptions không tồn tại và bundle widget không tham chiếu MysboxCustomOptions/custom_style/custom_script. custom_script được chèn vào trang theo cơ chế nào (khối riêng của theme extension?) và trang khách có đọc MysboxCustomOptions không?","kb_ids":["widget-custom-code#KB-024"],"check_ids":["widget-custom-code:CHK-014"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-050"}
```

## OQ-shop-settings-075 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-075","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Staging (1 mẫu, mọi block đã cài): Dashboard chỉ hiện \"Active\" / \"Installed\" và lấy trạng thái bằng Admin GraphQL đọc file theme MAIN + checkoutProfiles. Khi embed tắt hoặc block chưa đặt thì thẻ và bảng hiển thị giá trị gì, và đọc theme MAIN có đúng là cách phát hiện chính thức không?","kb_ids":["widget-theme-embed-setup#KB-044"],"check_ids":["widget-theme-embed-setup:CHK-029"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-051"}
```

## OQ-shop-settings-076 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-076","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Staging (1 mẫu, setup đã hoàn tất): các nút của setup guide disabled khi bước đã xong. Khi bước chưa xong, setup guide hiển thị gì và mỗi nút mở đâu? Nhãn \"Setup instructions\" / \"Add block to theme editor\" thấy trên staging có phải nhãn chính thức không?","kb_ids":["widget-theme-embed-setup#KB-045"],"check_ids":["widget-theme-embed-setup:CHK-030"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-052"}
```

## OQ-shop-settings-077 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-077","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Staging (1 mẫu): mặc định Item list là Square thumbnail, Hide item name/chance OFF, Hide item price ON, Image size 200, Show tier chance ON, Show random items in each group ON, Show item name and price OFF, Maximum number of groups shown 2. Đây có phải bộ mặc định chính thức không (tài liệu chỉ nêu Hide item price mặc định bật và 2 nhóm)?","kb_ids":["widget-theme-embed-setup#KB-046"],"check_ids":["widget-theme-embed-setup:CHK-031"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-053"}
```

## OQ-shop-settings-078 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-078","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Item list nhận Image size 99999 và Maximum groups 2.5 mà không báo lỗi (staging, chưa lưu, mỗi giá trị 1 lần). Giới hạn đúng của hai ô là gì, server có từ chối khi Save giá trị ngoài biên không, và widget storefront hiển thị ra sao nếu lưu được?","kb_ids":["widget-theme-embed-setup#KB-046"],"check_ids":["widget-theme-embed-setup:CHK-032"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-054"}
```

## OQ-shop-settings-079 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-079","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Staging gói Free: link \"Powered by Mysbox\" mở apps.shopify.com/mystery-box-builder ở tab mới. Đích link và việc watermark luôn hiện ở gói Free có phải hành vi chính thức không, và gói nào thì watermark bị ẩn?","kb_ids":["widget-theme-embed-setup#KB-048"],"check_ids":["widget-theme-embed-setup:CHK-033"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-055"}
```

## OQ-shop-settings-080 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-080","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Staging gói Free: merchant không có control ẩn watermark và không thấy cờ watermark trong dữ liệu merchant. Ai bật cờ hide_watermark (nhân viên Mysbox ở admin panel, hay tự động theo gói trả phí)?","kb_ids":["widget-theme-embed-setup#KB-049"],"check_ids":["widget-theme-embed-setup:CHK-034"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-056"}
```

## OQ-shop-settings-081 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-081","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Staging (1 mẫu): nội dung widget render ở light DOM, shadow root của custom element mở và rỗng. Đây có phải cấu trúc ổn định mà automation có thể dựa vào không?","kb_ids":["widget-theme-embed-setup#KB-050"],"check_ids":["widget-theme-embed-setup:CHK-035"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-057"}
```

## OQ-shop-settings-082 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-082","type":"NEEDS_CONFIRMATION","feature_id":"widget-theme-embed-setup","summary":"Staging (1 mẫu): mặc định của Animation (tab Carousel), Recent pulls (Show recent pulls OFF) và Share unboxing (Sharing popup) như đã ghi. Đây có phải mặc định chính thức không, và tab Drawing / Card flip / Gacha, \"Sharing image\" có tuỳ chọn / mặc định gì?","kb_ids":["widget-theme-embed-setup#KB-051","_object-level.storefront-widget#KB-005"],"check_ids":["widget-theme-embed-setup:CHK-036"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-058"}
```

## OQ-shop-settings-083 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-083","type":"NEEDS_CONFIRMATION","feature_id":"widget-translations","summary":"Staging: nhóm general-settings có 16 chuỗi mặc định (box_items có dấu cách cuối \"Box items \") và không có \"Auto-open in: {time}\". Đây có phải bộ chuỗi mặc định chính thức không, dấu cách cuối có chủ ý không, và \"Auto-open in: {time}\" thuộc nhóm nào?","kb_ids":["widget-translations#KB-036"],"check_ids":["widget-translations:CHK-024"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-059"}
```

## OQ-shop-settings-084 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-settings-084","type":"NEEDS_CONFIRMATION","feature_id":"widget-translations","summary":"Staging (shop chưa có bản dịch, shopLocale en): mọi request bản dịch gửi locale=default. Khi shop có ngôn ngữ phụ và bản dịch, client gửi locale nào, và metafield shop nào là nguồn của các API này?","kb_ids":["widget-translations#KB-037"],"check_ids":["widget-translations:CHK-025"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-060"}
```

## OQ-shop-settings-085 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-085","type":"OPEN_ISSUE","feature_id":"storefront-data-sync","summary":"Activate lại box đã sửa khi Draft có ghi metafield mysbox.box version mới (quantity/chance mới) không, và widget hiện chance nào sau đó? — Save khi Draft không ghi lại metafield (KB-052); nếu Activate cũng không ghi thì widget hiện chance/tồn kho cũ.","kb_ids":["storefront-data-sync#KB-052","storefront-data-sync#KB-037"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-061"}
```

## OQ-shop-settings-086 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-086","type":"OPEN_ISSUE","feature_id":"storefront-data-sync","summary":"Khi box Draft (metafield published_at null) khách vẫn bấm Add to cart / Buy it now trên variant box được — đơn đó được xử lý thế nào? — Widget ẩn nhưng nút mua vẫn hiện (KB-051); chưa có expected result cho đơn mua box Draft.","kb_ids":["storefront-data-sync#KB-051"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-062"}
```

## OQ-shop-settings-087 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-087","type":"OPEN_ISSUE","feature_id":"storefront-data-sync","summary":"Vì sao getProducts (Storefront API) trả metafield mysbox.box = null trong khi Liquid in được metafield đó — widget có phụ thuộc vào trường này không? — Có thể là quyền đọc metafield của token Storefront; ảnh hưởng nguồn dữ liệu dự phòng của widget.","kb_ids":["storefront-data-sync#KB-049"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-063"}
```

## OQ-shop-settings-088 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-088","type":"OPEN_ISSUE","feature_id":"widget-custom-code","summary":"Mục \"Advanced Settings\" của form box có chứa ô nhập code/tuỳ chọn nâng cao nào không? — Là màn duy nhất chưa mở khi kiểm 'merchant không có ô CSS/JS'.","kb_ids":["widget-custom-code#KB-026"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-064"}
```

## OQ-shop-settings-089 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-089","type":"OPEN_ISSUE","feature_id":"widget-theme-embed-setup","summary":"Save Style Settings với giá trị ngoài biên (Image size 99999, Maximum groups 2.5) thì server chấp nhận hay từ chối, và widget storefront hiển thị ra sao? — Client không báo lỗi (KB-046); chưa biết có validate phía server.","kb_ids":["widget-theme-embed-setup#KB-046"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-065"}
```

## OQ-shop-settings-090 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-090","type":"OPEN_ISSUE","feature_id":"widget-theme-embed-setup","summary":"Tab Drawing / Card flip / Gacha của Animation và tab \"Sharing image\" của Share unboxing có tuỳ chọn / mặc định gì? — Chưa mở trên staging; thiếu baseline Style Settings.","kb_ids":["widget-theme-embed-setup#KB-051","_object-level.storefront-widget#KB-005"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-066"}
```

## OQ-shop-settings-091 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-settings-091","type":"OPEN_ISSUE","feature_id":"widget-translations","summary":"Widget/trang khách luôn gửi locale=default dù shopLocale là \"en\" — ở shop có ngôn ngữ phụ, locale gửi đi có theo ngôn ngữ storefront của khách không? — Quyết định bản dịch theo ngôn ngữ có tới được khách (KB-024).","kb_ids":["widget-translations#KB-037","widget-translations#KB-024"],"tags":["staging-observed"],"supersedes":"OQ-storefront-widget-067"}
```
