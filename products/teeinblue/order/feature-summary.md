# Object: Order (product: teeinblue) — Feature Profile Summary
**Published context version:** 15

- **Env:** staging. Bootstrap 2026-09-13; cập nhật CBS-006 (TIB-5584) và CBS-011 (TIB-5558, action Hide) 2026-10-30; CBS-074 (Edit Customization sau order, tracking từ provider) 2026-11-06; CBS-096 (import đơn Shopify với customization_id sai định dạng, order design ảnh AI, order design vector) 2026-11-07; CBS-112 (feature mới `fulfillment-provider-request`: request gửi nhà in qua API Myze/PosterFlow) 2026-11-10; CBS-114 (Re-generate design và Edit customization ở portal trên order đã đặt, vào `edit-customization-after-order`) 2026-11-10; CBS-138 (4 rule spec-hub S2: artwork version của order, trạng thái Ready sau khi lưu design, tìm personalization qua cart, gom request theo provider) 2026-11-11; CBS-148 (TIB-5724: preset CustomCat trong payload, CustomCat từ chối preset, vào `fulfillment-provider-request`) 2026-11-12.
- **Nguồn:** phần lớn knowledge là `OBSERVED_CURRENT` từ bootstrap; item `CONFIRMED_EXPECTED` gồm KB-182, KB-238, KB-239, KB-392 từ test case Testlane PASS; KB-772, KB-774 từ test case ghi trên Jira QA-3348/QA-3365 PASS (kết quả AI); đều trên staging; KB-182 chờ PO xác nhận vì đổi đầu ra fulfillment (OQ-order-020)
- **Actor coverage:** storefront = GUEST buyer only (no signed-in buyer tested); portal = owner (explorer (TIB_STAGING_EMAIL), sub=<explorer>) only (no non-owner/restricted role tested)
- **Authoritative store: `store TIB_STORE_URL_2`** — NOT `store TIB_STORE_URL_1`. The latter has a known add-to-cart failure for this campaign that prevents completing a real order there; this KB should not be treated as verified for that store until its add-to-cart issue is investigated separately (see `OQ-order-013`).
- **7 features** (`place-personalized-order-storefront`, `review-and-initiate-fulfillment-portal`, `edit-customization-after-order`, `shopify-order-import`, `order-design-vector-render`, `order-design-print-resolution`, `fulfillment-provider-request`). Hai feature đầu đã có coverage; `edit-customization-after-order` và `shopify-order-import` chưa có coverage xác nhận (item đều PROPOSED, check đều NEEDS_CONFIRMATION); `order-design-vector-render` chỉ có quan sát một lượt (BASELINE). Không feature nào bị chặn hoàn toàn.
- **58 KB items** across the object: 0 HIGH, 12 MEDIUM, 46 LOW. 24 item bootstrap resting on exactly ONE order end-to-end (plus a second order used only to illustrate the sync conflict below).
- **1 unresolved conflict spanning both features:** `OQ-order-001` — an order placed successfully at storefront checkout did not appear in the portal Orders list for 90+ minutes across all statuses/stores/a 30-day range; a second order did sync after an unverified user claim that a webhook configuration issue had been fixed. That claim has never been independently verified.

---

## place-personalized-order-storefront — Place personalized order from storefront
**Goal:** Buyer (GUEST) chọn personalization cho một sản phẩm, add to cart, và hoàn tất checkout để tạo order.
**Entry point:** Trang sản phẩm campaign "QA Explore Campaign PB 01" (campaign 2595) trên `store TIB_STORE_URL_2`

**Capabilities:**
1. Chọn personalize template → hiện 7 trường phụ thuộc bắt buộc (Skin Tone auto-default, Hairstyle 2 cấp, Woman Name text ≤10 ký tự, Cat Breed #1/#2 2 cấp, Cat Name #1/#2 text ≤10 ký tự)
2. Điền trường → counter ký tự cập nhật đúng, mockup preview cập nhật live
3. Add to cart → đúng 1 line item, cart/checkout chỉ hiển thị personalization qua mockup image, không có field=value text
4. Checkout: "Test Payment Gateway" (card 1/2/3 = approved/declined/gateway-failure) tồn tại song song real gateway; Standard shipping $8.00 hoàn tất → Subtotal $55.99 + Shipping $8.00 = Total $63.99, không tax cho địa chỉ US/NY này
5. Order confirmation hiển thị đầy đủ confirmation number, contact/shipping/billing/payment (masked), cost breakdown
6. Order hoàn tất ở storefront **có thể** xuất hiện trong portal Orders — nhưng KHÔNG đảm bảo (xem risk)

**Coverage:** storefront (product page → confirmation, 1 combo) ✅ · api (POST /cart/add) ⚠️ INFERRED-only, chưa có raw payload · portal (order xuất hiện sau sync) ✅ (1/2 order) · signed-in buyer ❌ · Express shipping hoàn tất ❌ · declined/gateway-failure payment ❌ · missing-required-field submission ❌ · exact 10-char boundary ❌ · cart reload persistence ❌ · multi-item order ❌
**Confidence:** LOW (hầu hết KB item), 3 item MEDIUM nhờ corroborate với một quan sát trước đó (store khác)
**Risks/Unknowns:**
- **OQ-order-001**: order sync từ storefront vào portal không đáng tin cậy — 1/2 order test không bao giờ sync; root cause (claim webhook config) chưa verify độc lập
- POST /cart/add request/response mechanics là INFERRED, không có raw payload
- Express shipping price ($15.00) là INFERRED, chưa từng hoàn tất path này
- Không có error path (4xx/5xx, declined card, missing field) nào được quan sát trong lần khám phá này (xem `OQ-order-002`, `OQ-order-003`)
- Mọi finding pricing/field-dependency chỉ dựa 1-2 sample, không được suy rộng thành rule chung

**Cập nhật CBS-011 (TIB-5558, action Hide):**
- Layer action Hide có field Required đang bị ẩn không chặn Add to cart; payload customization và localStorage không có key của layer đó; giá trị đã nhập trước khi layer bị ẩn không vào cart/order/print file (KB-238, CONFIRMED_EXPECTED/MEDIUM, nguồn: test case Testlane PASS trên staging 2026-10-28, chạy trước khi 6 PR của TIB-5558 merge (2026-10-29); production chưa xác nhận).
- Chưa chạy lại trên build sau merge/production (OQ-order-021); layer Required kiểu khác text hoặc nhiều layer Hide cùng ẩn chưa kiểm (OQ-order-022); PO chưa xác nhận đây là ý định cho merchant (OQ-order-025).

**Gate:** publish này giữ điều kiện — `OQ-order-001` phải giữ UNRESOLVED; KB-006/KB-009 giữ INFERRED, không nâng cấp

**Cập nhật CBS-013 (TIB-5203):** chuỗi Add to cart → checkout → order trên portal → file design có giá trị layer + Global Option (KB-369, OBSERVED_CURRENT/LOW, 1 lượt trên staging trước redeploy) — chưa xác nhận, ảnh hưởng order/fulfillment, chờ PO/Dev (OQ-order-027). CHK-022-ORDER01 là NEEDS_CONFIRMATION.

**Cập nhật CBS-096:**
- Order design dùng ảnh AI đã generate và fit vào box layer (T2I GPT Default phủ đúng box; MU GPT 2K phủ hết chiều rộng, contain, không crop); item Ready (KB-766, OBSERVED_CURRENT/LOW, một lượt chạy staging 2026-10-27, không ghi build). Số đo bbox/kích thước master không phải giá trị chuẩn. Cách fit đúng và model khác chưa xác nhận (OQ-order-051).

---

## review-and-initiate-fulfillment-portal — Review and initiate fulfillment for an incoming order
**Cập nhật CBS-163 (TIB-5689), `CONFIRMED_EXPECTED`/MEDIUM theo Dev:** regenerate/cancel design của order item trả 10 field của design, không relation (KB-790); template export CSV store/show có `template_name`, `template_fields`, không `user_id` (KB-792); `/fulfills/unknown` (mở trực tiếp) tải được thay vì lỗi 500 trước đây, list dự kiến rỗng (KB-794, KB-795). Quan sát test case KB-791 (gồm upload ảnh trong Edit customization của order trả `id`, `url`, `original`), KB-793, KB-796. Mapped badge, title link fallback, Regenerate trên `/fulfills/unknown` không hoạt động và không tính là bug (Dev; OQ-order-094). Check CHK-P31..P39.
**Goal:** Merchant (owner) xem lại order đã sync (line item, campaign/variant, customization/design, customer/shipping/billing, status) và khởi tạo bước gửi fulfillment.
**Cập nhật CBS-006 (TIB-5584, staging 2026-10-16):** print file PNG/PDF của order từ artwork có Group ẩn không chứa nội dung Group (KB-182, `CONFIRMED_EXPECTED`/MEDIUM). Layout emboss/shape-cut chưa verify (KB-183, OQ-order-018). Checklist CHK-P17..CHK-P20; OQ-order-018..020.
**Entry point:** portal Orders list → order-details → nút "Confirm & Send to fulfill" (KHÔNG có route `/fulfills` riêng biệt)

**Capabilities:**
1. Orders list: filter mặc định (date range, Store=Any, TIB Status=Any), backed bởi `GET /api/orders?by_teeinblue=1`; search theo internal order name (`#1002`) hoạt động, search theo Shopify confirmation code (`JTEL87JY0`) KHÔNG match dù order đã sync — 2 namespace khác nhau
2. Order-details: header `#1002 (#-4322)`, badge tib_status `ready` = API integer `6` (chỉ 1 cặp giá trị từng quan sát); order-item card có status badge RIÊNG, Shopify SKU khác Fulfilled SKU, Customization block, Designs (mockup + printarea 3600x5400px)
3. Item Activity Logs: 4 sự kiện tự động (created → generating design → design generated → Ready to fulfill) trong ~22 giây, KHÔNG cần thao tác merchant
4. "Confirm & Send to fulfill" **trên instance CHƯA connect POD (Printify)**: mở dialog review (không submit ngay), hiện prompt "Connect", chỉ 2 GraphQL query READ-ONLY chạy quanh click — KHÔNG có mutation/network call ra POD nào. **Phát hiện này CHỈ áp dụng cho trạng thái POD chưa connect** — nhánh đã connect hoàn toàn chưa quan sát (xem `OQ-order-012`)
5. "Change status" dropdown hiện đúng 5 option (Ready/Sent/Fulfilled/Paused/Canceled) — chỉ quan sát danh sách, chưa test transition nào (xem `OQ-order-016`)

**Khác biệt môi trường (KB-437, INFERRED/LOW, NOT_TESTABLE, mức Case):** chưa có lời xác nhận gốc: tracking từ provider không test được trên staging; fulfill tay trên Shopify đi đường khác, không thay được. CHK-P27 ghi skipped, verdict NOT_APPLICABLE. Production: không rõ (OQ-order-039).

**Coverage:** portal (orders list, order-details, activity log, fulfill dialog POD-disconnected, change-status list) ✅ · fulfill với POD ĐÃ connect ❌ (unknown lớn nhất, rủi ro production thật) · change-status transition thực thi ❌ · Bulk Fulfill page ❌ (tồn tại ở sidebar, chưa mở) · non-owner/restricted role ❌ · DB cross-check ❌ (database observation bị tắt) · Edit/View customization ❌ · multi-item order ❌
**Confidence:** LOW toàn bộ (1 order, 1 line item, 1 role, 1 environment)
**Risks/Unknowns:**
- **OQ-order-001** (merchant-facing risk): order có thể silently không xuất hiện trong portal — feature này giả định order đã visible, nhưng precondition đó không được đảm bảo
- "Confirm & Send to fulfill" khi POD ĐÃ connect: hoàn toàn unknown, có thể có mutation/side-effect thật (rủi ro production) — đây là gap an toàn lớn nhất của object này (`OQ-order-012`)
- "Change status" transition, "Bulk Fulfill": chưa test, side effect (notification, POD call) hoàn toàn unknown (`OQ-order-016`, `OQ-order-017`)
- tib_status chỉ có 1 cặp giá trị quan sát (ready/6) — không suy enum đầy đủ (`OQ-order-014`)
- 3/5 network entry quanh action fulfill-click chưa xác định được
- Không có permission boundary nào được test (chỉ owner sub=<explorer>) (`OQ-order-009`)

**Cập nhật CBS-011 (TIB-5558, action Hide):**
- Preview customization, mockup và print file (order design PNG) áp điều kiện Hide giống storefront: item khớp Hide không có layer đó, item không khớp có layer với đúng chữ đã nhập (KB-239, CONFIRMED_EXPECTED/MEDIUM, nguồn: test case Testlane PASS trên staging 2026-10-28, chạy trước khi 6 PR của TIB-5558 merge (2026-10-29); production chưa xác nhận).
- Chưa chạy lại trên build sau merge/production, BUG-430 (print file rỗng ở lượt đầu) chưa rõ fix ở build nào (OQ-order-023); PDF, emboss, shape-cut với layer Hide chưa kiểm (OQ-order-024); PO chưa xác nhận đây là ý định cho merchant/nhà in (OQ-order-026).

**Gate:** publish này giữ điều kiện — KB-022 phải giữ scope POD-disconnected; `OQ-order-001` giữ UNRESOLVED

**Cập nhật CBS-096:**
- Đề xuất, chưa ship (TIB-5563): Order details / Edit order hiện nguyên giá trị customization_id trong "Options" của item khi bật "show line item properties", ẩn sau "Show more", HTML-escape (KB-764, PROPOSED/LOW). Chưa quan sát; không dùng làm expected (OQ-order-050).

---

**Cập nhật CBS-015 (TIB-5633, Group nhiều layer):** Regenerate design trong order detail cho item có artwork Group ~250 layer tạo xong design mới (Item Activity log 'generated a new design'), không kẹt generating (KB-392, `CONFIRMED_EXPECTED`/MEDIUM, test case Testlane PASS staging 2026-10-29; PO chưa xác nhận ý định — OQ-order-030; chạy lại sau merge/production — OQ-order-029). Toast 'put your design in queue', việc Item Activity logs không có dòng 'is generating' riêng và việc order vẫn ở Ready sau Regenerate chỉ là quan sát (KB-393, `OBSERVED_CURRENT`/LOW, OQ-order-028). Checklist CHK-P24..CHK-P26 (CHK-P25, CHK-P26 NEEDS_CONFIRMATION). Theo spec-hub (CBS-138, KB-782, PROPOSED/LOW, rule đọc từ code, chưa Dev xác nhận, không phải oracle): item active/personalized thành Ready khi design file lưu xong, item đã fulfilled được re-generate vẫn fulfilled (OQ-order-085). Render order design của Group nhiều layer nằm ở object `artwork` (feature `group-layer-order-design-render`).

## edit-customization-after-order — Buyer mở Edit Customization sau khi đặt order

**Surface:** storefront (Thank You page và Order status page; role buyer; cần block Edit Customization đã có trên trang) và portal (Order details, role staff/owner: Re-generate design, Edit customization).

- **Campaign Shopify product (KB-435, PROPOSED/LOW, đề xuất chưa xác minh):** theo test case, customizer mở với design editable ở cả hai trang. Bước lưu thay đổi và ghi đè artwork chưa có lượt chạy.
- **Campaign by product base (KB-436, PROPOSED/LOW, đề xuất chưa xác minh):** theo test case, link vẫn hiện; click thì sang trang customize và báo "Your design does not support edit for now, contact shop owner". Lượt chạy chỉ ở Thank You page; hai nguồn chưa chốt (OQ-order-044).
- **Checklist:** CHK-001..CHK-004 đều NEEDS_CONFIRMATION, oracle NONE: chỉ ghi nhận, chưa kết luận PASS/FAIL.
- **Không dùng làm expected cho:** /cart (OQ-order-031), bước lưu (OQ-order-033), nút cùng tên ở Portal (OQ-order-011).
- **Portal, staff/owner (CBS-114, OBSERVED_CURRENT/LOW, nguồn QA, không có xác nhận PO/Dev, không phải oracle):** KB-779: sau khi đổi populate config của artwork, Re-generate design mặc định "No, keep current artwork version" dựng lại bản render byte-identical (QA-3353 TC-76); KB-780: mở Edit customization, không sửa field nào rồi Save thì design không đổi (QA-3386 TC-41). Nhánh Re-generate "Yes. Upgrade latest artwork version." và trường hợp sửa field thật rồi Save chưa có lượt chạy. CHK-005, CHK-006 (BASELINE). Các item này là quan sát về nút ở Portal nhưng chưa đóng OQ-order-011.
- **Theo spec-hub (CBS-138, KB-781, PROPOSED/LOW, rule đọc từ code, chưa Dev/PO xác nhận, không phải oracle):** design của order render từ artwork version shopper đã personalize; sửa/restore artwork sau khi đặt không đổi design, trừ khi merchant chọn upgrade. Cùng chiều KB-779, KB-780 (OQ-order-082).
- **Còn mở:** OQ-order-031..038, OQ-order-040..044, OQ-order-082..084.

---

## shopify-order-import — Import đơn Shopify vào Teeinblue khi line item có customization_id
**Goal:** Đơn Shopify (webhook create/update, re-sync, FixMissingCustomization) được import vào Teeinblue; line item có customization_id sai định dạng không làm hỏng cả đơn.
**Phạm vi:** backend import/đồng bộ đơn Shopify, khôi phục customization, usage. Không gồm flow đặt hàng storefront và review/fulfill ở portal.

**Trạng thái:** mọi item là PROPOSED/LOW (KB-760..KB-763, KB-765), theo câu trả lời của Dev trên TIB-5563 ngày 2026-10-26 cho bản fix **chưa ship**. Không item nào là expected; mọi check (CHK-001..CHK-009) oracle NONE.
- Đề xuất: customization_id chỉ dùng để tìm customization khi đúng UUID 8-4-4-4-12 (không trim, không trích từ chuỗi dài hơn), cả `_customization_id` và `customization_id`; nhánh id số giữ nguyên.
- Đề xuất: đơn có line sai định dạng vẫn import, line đó không có design và không tạo usage; khôi phục qua cart token không áp cho line đó; chỉ luồng đơn Shopify dùng check này; đơn lỗi trước fix không import lại.
- Theo spec-hub (CBS-138, KB-783, PROPOSED/LOW, mô tả code hiện tại): chỉ khi không item nào trong order có id, Teeinblue tìm personalization cùng cart, cùng variant trong một tháng dương lịch, mỗi personalization một item (OQ-order-086).

**Risks/Unknowns:**
- Lượt QA staging 2026-10-28 thấy đơn có line sai định dạng không vào Teeinblue (OQ-order-046, liên quan OQ-order-001).
- Chờ test case PASS sau fix và sau release (OQ-order-045, OQ-order-047..OQ-order-049, OQ-order-086).

---

## order-design-vector-render — Order design PNG/SVG của vector layer đã đổi màu
**Goal:** Order design của vector layer có màu render đúng: PNG tô kín, SVG gộp có id duy nhất và tham chiếu đúng.
**Phạm vi:** order design PNG và SVG của vector layer có màu. Không gồm preview storefront, file SVG nguồn (artwork), luồng Regenerate và fulfillment.

**Quan sát (OBSERVED_CURRENT/LOW, staging, không ghi build, chỉ khi mọi layer cùng một màu):**
- PNG sau Re-generate tô kín mọi vector có clipPath id trùng, không vùng trong suốt, bố cục giống preview (KB-767).
- SVG gộp mọi layer: id duy nhất toàn file, có prefix `svg-…-`, không tham chiếu treo, màu đúng (KB-768).

**Risks/Unknowns:**
- Chưa xác nhận là hành vi đúng; trạng thái deploy TIB-5350 chưa rõ (OQ-order-052, OQ-order-053).
- Mỗi layer giữ màu riêng, PDF và production chưa kiểm. Fixture khác artwork KB-418.

---

## order-design-print-resolution — Độ phân giải (DPI) của file order design theo print area
**Goal:** File order design (PNG) ghi resolution bằng DPI của print area, kích thước pixel giữ nguyên.
**Phạm vi:** file order design PNG khi tạo order và khi regenerate design. Không gồm cấu hình DPI trên Product Base (object `product-base`, feature `printarea-definition`, nơi cũng có các quy tắc về JPG/PDF, pixel, validation và import print area: KB-505..KB-513), nội dung render layer, chọn design format.

**Đã xác nhận (CONFIRMED_EXPECTED/MEDIUM, test case PASS staging 2026-10-29 và production 2026-11-02):**
- Print area có DPI trống: file design ghi 300 DPI, pixel không đổi (KB-769).
- Đổi DPI của print area (vd 150) rồi regenerate design: file ghi DPI mới, pixel không đổi (KB-770).
- Tạo order với print area có DPI đã đặt (vd 200): file design ghi đúng DPI đó (KB-771).

**Risks/Unknowns:** chưa có điều chưa biết nào mà canon không phủ.

---

## fulfillment-provider-request — Request TIB gửi nhà in qua API (Myze, PosterFlow, CustomCat)
**Goal:** Khi đơn được gửi fulfill tới nhà in kết nối qua API, TIB dựng payload Create Order, tách hoặc gộp request theo provider và lưu response của provider.
**Phạm vi:** payload và request gửi nhà in, lưu response, tách/gộp theo provider, URL webhook tracking. Không gồm kết nối/cấu hình provider ở trang Fulfillments (object `product-base`, chưa có feature này trong canon) và review/gửi fulfill ở portal (`review-and-initiate-fulfillment-portal`). Setup: store explorer đã kết nối Myze/PosterFlow trên staging.

**Đã xác nhận (CONFIRMED_EXPECTED/MEDIUM, test case PASS staging, chỉ phạm vi đã chạy):**
- Payload gửi Myze mang `pickUp` có mặt, giá trị true (quan sát là boolean); đơn pickup (shippingAddress null) được Myze nhận (KB-772).
- Payload Create Order gửi PosterFlow không có field giá (KB-774); không suy rộng cho provider khác.

**Quan sát hiện tại (OBSERVED_CURRENT/LOW, chờ Dev xác nhận):** vị trí lưu response PosterFlow (KB-773), shape payload PosterFlow thật lệch ví dụ dev (không `id`, `shipping_address.state` null ở phần lớn đơn, KB-775, UNRESOLVED), gộp cùng provider khi `order_combine_by` = 1 và đơn nhiều provider tách theo provider ở lượt đã chạy (KB-776, KB-777; chưa rõ mọi giá trị `order_combine_by`), URL webhook `shipment_notification_url` (KB-778).

**Theo spec-hub (CBS-138, KB-784, PROPOSED/LOW, rule đọc từ code, chưa Dev xác nhận, không phải oracle):** Confirm & Send gom item theo print provider rồi theo order, hoặc theo shipping address khi store gộp đơn theo shipping address; mỗi nhóm một provider order. Tên setting `order_combine_by` chưa có nguồn xác nhận (OQ-order-087).

**CustomCat (CBS-148, CONFIRMED_EXPECTED/MEDIUM, lời Dev 2026-11-10, test case PASS staging với CustomCat sandbox):**
- Item gửi CustomCat chỉ mang `preset_id`/`preset_back_id` từ `default_options` của Product Base khi key có giá trị (không null, không chuỗi rỗng); không key nào khác của `default_options` được gửi (KB-785).
- CustomCat từ chối preset không hợp lệ: order item hiện lần gửi thất bại kèm lý do của CustomCat (KB-787).
- Quan sát (LOW): shape item quantity, catalog_sku, design_url (+ preset như đã lưu) (KB-786, OQ-order-088); item lỗi ở Failed / Items Have Error, lý do chỉ ở Item Activity logs / Latest log (KB-788, OQ-order-089).
- Khác biệt môi trường ALTERNATIVE_SETUP (KB-789, OQ-order-090): test qua CustomCat sandbox trên staging; production không có sandbox, không gửi test. Cách đọc payload: `_flows/orders-fulfillment.md`.

**Risks/Unknowns:** 18 OQ mở (OQ-order-068..081, OQ-order-087..090), gồm 2 CONFLICT (OQ-order-077, OQ-order-078) về shape payload PosterFlow; payload Myze (country/state, phone/supplement), retry, header outbound, địa chỉ Shopify, text buyer attach, stub lỗi provider chưa có xác nhận nên chưa vào KB.
**Coverage:** 13 KB item, 10 check (5 READY, 5 chờ xác nhận); chưa có RBAC, production, provider khác Myze/PosterFlow/CustomCat.

---

## Gaps ở cấp Object (áp dụng cho MỌI feature trên)

| Gap | Ghi chú |
|---|---|
| **Store scope** | Authoritative store cho context version này là `store TIB_STORE_URL_2`, KHÔNG PHẢI `store TIB_STORE_URL_1` — xem `OQ-order-013`. Store `store TIB_STORE_URL_1` cần điều tra riêng lỗi add-to-cart trước khi mở rộng KB này sang đó. |
| **OQ-order-001 (order sync)** | UNRESOLVED, ảnh hưởng cả 2 feature — entry point của review-and-initiate-fulfillment-portal phụ thuộc vào bước sync không đáng tin cậy của place-personalized-order-storefront. Claim "đã fix webhook" của user CHƯA được verify độc lập bởi bất kỳ exploration nào. |
| **POD-connected fulfill branch** | Hoàn toàn chưa quan sát — đây là rủi ro an toàn/production lớn nhất trong toàn bộ object (`OQ-order-012`); không được suy rộng từ nhánh POD-disconnected đã quan sát. |
| **Data layer (DB) thật** | Database observation bị tắt cho lần khám phá này — không có bằng chứng DB nào trong toàn bộ KB (`OQ-order-010`). |
| **Code-level facts** | Không có exploration ở tầng code trong lần khám phá này — code = NOT_OBSERVED cho cả 2 feature. |
| **Raw API/network payload** | Payload thô của POST /cart/add và của order-details GraphQL/REST chưa từng được capture — các KB item liên quan giữ LOW/INFERRED, không nâng cấp (`OQ-order-008`, `OQ-order-015`). |
| **RBAC / non-owner / signed-in buyer** | Chưa test trên bất kỳ feature nào — storefront chỉ GUEST, portal chỉ owner (sub=<explorer>) (`OQ-order-006`, `OQ-order-009`). |
| **'portal/fulfills' route & 'Bulk Fulfill'** | Không có route `/fulfills` riêng biệt được tìm thấy; "Bulk Fulfill" tồn tại ở sidebar flyout nhưng chưa mở — hành vi hoàn toàn unknown, không suy đoán từ flow order-details (`OQ-order-017`). |
| **Checklist confidence nguồn** | 34 KB item nguồn: 0 HIGH, 7 MEDIUM, 27 LOW — theo nguyên tắc "một sample → luôn LOW", không dùng làm hard assertion. 53 check trong 3 checklist, 28/53 là `NEEDS_CONFIRMATION`. |
