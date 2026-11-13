# Open Questions — multibuy

## OQ-multibuy-001 — CONFLICT

```json
{"oq_id":"OQ-multibuy-001","type":"CONFLICT","feature_id":"multibuy-discount-setup","summary":"[CONF-DOC04-001] Business Rules > Appearance & style (QVD-107)","side_a":"Theo tài liệu \"Multibuy – Mix & Match Combo\" §`Business Rules > Appearance & style (QVD-107)`, nêu rằng live-observed default của Badge border radius slider trong Appearance & style là 6px — khác với 10px mà QVD-132 document; tài liệu nêu rõ discrepancy này chưa được giải quyết.","side_b":"Theo tài liệu \"Multibuy – Mix & Match Combo\" §`Business Rules > Multibuy discount badge (QVD-132)`, (ticket QVD-132, chưa được QA xác nhận lại ở mục này) nêu rằng Badge border radius slider default là 10px.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ CONFLICT): Form Multibuy mới: Badge border radius mặc định 6px. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["multibuy-mix-match-combo#KB-090"],"supersedes":"OQ-discount-offers-002"}
```

## OQ-multibuy-002 — CONFLICT

```json
{"oq_id":"OQ-multibuy-002","type":"CONFLICT","feature_id":"multibuy-discount-setup","summary":"[CONF-DOC04-002] Business Rules > Appearance & style (QVD-107)","side_a":"Theo tài liệu \"Multibuy – Mix & Match Combo\" §`Business Rules > Appearance & style (QVD-107)`, nêu rằng live example quan sát được cho Badge text trong Appearance & style là \"MULTIBUY\" (chữ hoa) — khác với default \"Multi buy\" mà QVD-132 document; tài liệu nêu rõ chưa xác nhận giá trị nào là true out-of-the-box default so với giá trị đã bị merchant chỉnh.","side_b":"Theo tài liệu \"Multibuy – Mix & Match Combo\" §`Business Rules > Multibuy discount badge (QVD-132)`, (ticket QVD-132, chưa được QA xác nhận lại ở mục này) nêu rằng Badge text default là \"Multi buy\"; để trống thì ẩn badge; recommend khoảng 20-25 ký tự.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ CONFLICT): Form Multibuy mới: Badge text mặc định 'MULTIBUY'; render 'MULTIBUY' trên collection/search; PDP không đánh giá được (không ảnh). (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["multibuy-mix-match-combo#KB-091"],"supersedes":"OQ-discount-offers-003"}
```

## OQ-multibuy-003 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-003","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-019"],"summary":"NEEDS_CONFIRMATION — Pooling across different products có áp dụng cho trigger Collection/Specific products không?","detail":"Quantity pooling across different products (đã confirm cho trigger 'All products', KB-032) có áp dụng nhất quán cho trigger 'Collection' và 'Specific products' không? Cơ chế pooling là core mechanic của Multibuy; nếu khác nhau giữa trigger type thì coverage hiện tại (chỉ test All products) không đủ.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Trigger Specific products 2 product: số lượng gộp giữa product (1+1 → tier 2, 1+2 → tier 3, 2+2 → tier 4). (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["multibuy-mix-match-combo#KB-095"],"supersedes":"OQ-discount-offers-019"}
```

## OQ-multibuy-004 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-004","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-028","multibuy-mix-match-combo:CHK-071"],"summary":"NEEDS_CONFIRMATION — Customer product selection behavior: radio Popup (default) vs Redirect","detail":"Customer product selection behavior có đúng là radio 2 option (Open selection popup [default] Redirect to a specific page/URL) như ticket QVD-106 mô tả không? Cần QA re-confirm live trước khi dùng làm oracle, vì tài liệu này đã phát hiện ≥3 case khác nơi ticket không khớp hành vi live.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): 3 radio: Open selection popup / Redirect to specific page/URL (mặc định) / Direct to collection page; lưu được với URL rỗng. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["multibuy-mix-match-combo#KB-088"],"supersedes":"OQ-discount-offers-020"}
```

## OQ-multibuy-005 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-005","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-029","multibuy-mix-match-combo:CHK-072"],"summary":"NEEDS_CONFIRMATION — Popup mode detail (variant picker slide-up, overlay, no-variant instant add)","detail":"Popup mode detail (variant picker slide-up từ đáy card + overlay semi-transparent cho product có variant; instant add-to-cart + icon đổi state cho product không variant) theo ticket QVD-121 còn khớp hành vi live hiện tại không?","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Popup là modal căn giữa, fade; '+' chỉ mở rộng thẻ (stepper/select + Pick), không instant add; Pick không thêm cart, Done mới thêm và chuyển /cart; lỗi console mỗi lần Pick. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["multibuy-mix-match-combo#KB-094","multibuy-mix-match-combo#KB-093"],"supersedes":"OQ-discount-offers-021"}
```

## OQ-multibuy-006 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-006","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-043"],"summary":"NEEDS_CONFIRMATION — Badge border radius true default: 6px (live-observed) hay 10px (ticket QVD-132)?","detail":"True out-of-the-box default của Multibuy discount badge border radius là 6px (live-observed, KB-081) hay 10px (ticket QVD-132, KB-082)? Hai giá trị khác nhau trong cùng 1 tài liệu, chưa resolve — không dùng được làm expected default cho test case badge appearance.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): = OQ-002: 6px. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["multibuy-mix-match-combo#KB-090"],"supersedes":"OQ-discount-offers-022"}
```

## OQ-multibuy-007 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-007","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-044"],"summary":"NEEDS_CONFIRMATION — Badge text true default: \"MULTIBUY\" (live example) hay \"Multi buy\" (ticket QVD-132)?","detail":"True out-of-the-box default của Multibuy discount badge text là \"MULTIBUY\" (live example, KB-083) hay \"Multi buy\" (ticket, KB-084), hoặc liệu giá trị live đã bị merchant chỉnh? Không dùng được làm expected default cho test case badge text cho tới khi xác nhận.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): = OQ-003: 'MULTIBUY'. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["multibuy-mix-match-combo#KB-091"],"supersedes":"OQ-discount-offers-023"}
```

## OQ-multibuy-008 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-008","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-046"],"summary":"NEEDS_CONFIRMATION — Discount combination checkboxes (Order/Product/Shipping), default off","detail":"Discount combination section (checkbox combine Order/Product/Shipping discount, theo ticket QVD-108) có đúng cả 3 default off như tài liệu mô tả không? Cần QA re-confirm live.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Combination trên form Multibuy (và QB, WH): 3 checkbox đều CHECKED mặc định + dropdown 'One per product (best value wins)'. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["_object-level#KB-012"],"supersedes":"OQ-discount-offers-024"}
```

## OQ-multibuy-009 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-009","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-048"],"summary":"NEEDS_CONFIRMATION — Offer scheduling: start date required/not-past, end date optional toggle","detail":"Offer scheduling base rule (start date required, default = creation time, không thể là ngày quá khứ, dùng store timezone; end date optional sau toggle 'Enable end date', default off = chạy vô thời hạn) theo ticket QVD-109 còn khớp hành vi live không?","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Start mặc định = lúc mở form (timezone store), ngày quá khứ disabled trong picker; end date tắt mặc định; trên offer đã lưu end date điền sẵn hôm nay, giờ ≈ hiện tại + 1h. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["_object-level#KB-013","quantity-break#KB-084"],"supersedes":"OQ-discount-offers-025"}
```

## OQ-multibuy-010 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-010","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-050"],"summary":"NEEDS_CONFIRMATION — Internal name auto-default \"Offer #N\", merchant-only","detail":"Internal name có đúng auto-default theo pattern \"Offer #N\" và chỉ merchant thấy (không hiển thị customer) như ticket QVD-103 mô tả không? Cần QA re-confirm live.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Internal name mặc định 'Offer N' (không '#'); không hiện trên UI storefront nhưng có trong JSON cấu hình nhúng ở HTML PDP. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["_object-level#KB-010","_object-level#KB-029"],"supersedes":"OQ-discount-offers-026"}
```

## OQ-multibuy-011 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-011","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-051"],"summary":"NEEDS_CONFIRMATION — Offer title default template {{quantity_tier}} for {{total_price}}","detail":"Offer title default template có đúng là {{quantity_tier}} for {{total_price}} (double braces, theo ticket QVD-103) hay dùng single-brace notation như đã confirm cho Tier Title/Badge (KB-020/021)? Notation đã bị phát hiện sai ở phần Tier settings — rủi ro drift tương tự ở đây chưa loại trừ.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Offer title (Fixed price) mặc định BUY ANY {quantity_tier} ITEMS FOR {discount} (ngoặc đơn, không nháy). (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["multibuy-mix-match-combo#KB-085"],"supersedes":"OQ-discount-offers-027"}
```

## OQ-multibuy-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-012","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-052"],"summary":"NEEDS_CONFIRMATION — Discount method default automatic; limit 25/code → contact support","detail":"Discount method default có đúng là automatic discount, và hành vi khi chạm giới hạn 25/muốn dùng discount code (hướng dẫn liên hệ support, không self-serve) theo ticket QVD-103 còn khớp hành vi live không?","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Discount method mặc định Automatic; option Discount code không khoá, chọn được (form chưa lưu). (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["_object-level#KB-011"],"supersedes":"OQ-discount-offers-028"}
```

## OQ-multibuy-013 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-013","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-056"],"summary":"NEEDS_CONFIRMATION — \"Silent\" mode (discount tự áp dụng, widget UI ẩn qua custom CSS)","detail":"Compare-at-Price logic có thực sự hỗ trợ 1 \"silent\" mode (discount tự áp dụng, widget UI ẩn qua custom CSS) như tài liệu mô tả (feasible, chưa verify) không? Nếu có, giới hạn 25-automatic-discount của Shopify có cần cảnh báo riêng cho merchant khi dùng mode này?","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): (bucket b — chỉ ghi kèm) Custom CSS vẫn khoá sau 'contact our support team to enable' trên cả 3 form; silent mode không kiểm được. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["multibuy-mix-match-combo#KB-089"],"supersedes":"OQ-discount-offers-029"}
```

## OQ-multibuy-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-014","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-060"],"summary":"NEEDS_CONFIRMATION — Offer nào thắng khi Multibuy overlap trigger với Quantity Break (2-way)?","detail":"Biến nào quyết định offer nào thắng khi trigger của Multibuy overlap với Quantity Break (2-way)? Kết quả đã bị 'flip' giữa 2 lần test live trên cùng 1 cặp offer, không biến nào được xác định. Cần PO/Dev confirm trước khi viết được regression test case xác định cho trigger-overlap.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): = OQ-008. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["_object-level#KB-026","_object-level#KB-028"],"supersedes":"OQ-discount-offers-030"}
```

## OQ-multibuy-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-015","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-061"],"summary":"NEEDS_CONFIRMATION — Offer nào thắng khi cả 3 offer type (Multibuy, Quantity Break, Wholesale Pricing) cùng trigger và ≥2 discount đang active (3-way)?","detail":"Khi Wholesale Pricing's own tier có discount nonzero và đồng thời qualify cho tier của Quantity Break/Multibuy, offer nào thắng trong 3-way overlap? Test 3-way hiện có (qty=3) không phải test priority sạch; chưa có dữ liệu trả lời priority thật khi 2 discount active cùng lúc.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): 3 offer cùng product với mức khác 0 (11 đơn vị): qua composer → 1 line mã Quantity Break; add không property → 2 line, mã Multibuy (4 món) + mã Quantity Break (7 món); không thấy mã Wholesale. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["_object-level#KB-028","_object-level#KB-026"],"supersedes":"OQ-discount-offers-031"}
```

## OQ-multibuy-016 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-016","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-064"],"summary":"NEEDS_CONFIRMATION — Có permission/role boundary chi tiết hơn (sub-role, plan/feature-flag) kiểm soát quyền cấu hình Multibuy không?","detail":"Có permission/role boundary nào (vd Portal staff sub-role, plan/feature-flag gating) kiểm soát việc ai được cấu hình Multibuy không? permissions[] hiện chỉ phân biệt ở mức merchant (Portal) vs buyer (storefront) — không phải 1 authorization model.","supersedes":"OQ-discount-offers-032"}
```

## OQ-multibuy-017 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-017","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-065"],"summary":"NEEDS_CONFIRMATION — Hành vi khi checkbox \"Allow to apply multiplier discounts per order\" bị UNCHECK","detail":"Khi checkbox \"Allow to apply multiplier discounts per order\" (Maximum discount uses) bị UNCHECK, hành vi chính xác là gì? Setting này chỉ áp dụng cho Fixed-price mode hay cũng ảnh hưởng Percentage mode cùng với toggle riêng của QVD-178?","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Multiplier tắt: chỉ một combo được áp dù đủ nhiều combo (6/8/12/18 món); bật (mặc định): nhiều combo. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["multibuy-mix-match-combo#KB-087"],"supersedes":"OQ-discount-offers-033"}
```

## OQ-multibuy-018 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-018","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-066"],"summary":"NEEDS_CONFIRMATION — Tie-break rule khi nhiều unit cùng giá 'cheapest' trong remainder calculation","detail":"Khi nhiều unit cùng share giá 'cheapest' trong remainder calculation của Fixed total price tier (pooled quantity có remainder), quy tắc tie-break chọn unit nào bị để lại full price là gì — cart order, product ID, hay yếu tố khác?","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): 5 món (2 giá khác nhau): đơn vị giá rẻ hơn ở giá gốc, Shopify tách line; tie-break khi cùng giá chưa kiểm. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["multibuy-mix-match-combo#KB-095"],"supersedes":"OQ-discount-offers-034"}
```

## OQ-multibuy-019 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-019","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-067"],"summary":"NEEDS_CONFIRMATION — Discount-combination checkboxes là component UI chung hay per-offer-type riêng?","detail":"Discount-combination checkboxes (Order/Product/Shipping, QVD-108) có phải là 1 UI component chung dùng lại across cả 3 offer type (Quantity Break/Multibuy/Wholesale), hay mỗi offer type có bản copy riêng? Ảnh hưởng tới phạm vi regression.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Section Combination giống hệt nguyên văn trên 3 form (chỉ ghi, không kết luận component). (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["_object-level#KB-012"],"supersedes":"OQ-discount-offers-035"}
```

## OQ-multibuy-020 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-020","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","check_ids":["multibuy-mix-match-combo:CHK-068","quantity-break:CHK-078"],"summary":"NEEDS_CONFIRMATION — Hành vi/placement thật của \"Enable countdown timer\" trên storefront","detail":"\"Enable countdown timer\" checkbox (Offer scheduling) có hành vi/placement chính xác là gì trên storefront, và quan hệ của nó với QVD-147 \"Countdown timer to offer\" ra sao?","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Countdown: checkbox chỉ hiện sau khi bật end date; trên PDP nằm đầu widget Quantity Break, 'HURRY UP!'/'Sale end in'/đếm ngược live. Không quan sát trên widget Multibuy; lúc hết giờ NOT_COVERED. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-085","_object-level#KB-013"],"supersedes":"OQ-discount-offers-036"}
```

## OQ-multibuy-021 — CONFLICT

```json
{"oq_id":"OQ-multibuy-021","type":"CONFLICT","feature_id":"multibuy-discount-setup","summary":"Tier mặc định khi tạo Multibuy: tài liệu 1 tier (qty 1, $10), staging 3 tier (2→$10, 3→$20, 4→$30).","side_a":"Base KB-022: 1 tier quantity 1 $10.","side_b":"Staging KB-086: 3 tier 2/$10, 3/$20, 4/$30.","conflict_group":"CONF-discount-offers-R1018-04","kb_ids":["multibuy-mix-match-combo#KB-022","multibuy-mix-match-combo#KB-086"],"check_ids":["multibuy-mix-match-combo:CHK-009"],"supersedes":"OQ-discount-offers-052"}
```

## OQ-multibuy-022 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-022","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","summary":"Customer product selection behavior trên staging có 3 lựa chọn (thêm 'Direct to collection page'), mặc định 'Redirect to specific page/URL' và lưu được với URL rỗng (khi đó slot '+' trên storefront không phản hồi); tài liệu nói 2 cách (popup/redirect) và ticket nói mặc định popup. Expected mặc định và có nên chặn lưu URL rỗng?","kb_ids":["multibuy-mix-match-combo#KB-003","multibuy-mix-match-combo#KB-045","multibuy-mix-match-combo#KB-088"],"check_ids":[],"related_oq_ids":["OQ-multibuy-004"],"supersedes":"OQ-discount-offers-057"}
```

## OQ-multibuy-023 — OPEN_ISSUE

```json
{"oq_id":"OQ-multibuy-023","type":"OPEN_ISSUE","feature_id":"multibuy-discount-setup","summary":"Popup Multibuy trên staging: mỗi lần 'Pick' console báo 'TypeError: Cannot read properties of null (reading 'url')' và subtotal/slot trong popup không cập nhật (dù 'Done' vẫn thêm đúng item vào cart). Có thể liên quan product không có ảnh — cần xác nhận là defect hay do dữ liệu thử.","kb_ids":["multibuy-mix-match-combo#KB-094"],"check_ids":[],"related_oq_ids":["OQ-multibuy-005"],"supersedes":"OQ-discount-offers-069"}
```

## OQ-multibuy-024 — OPEN_ISSUE

```json
{"oq_id":"OQ-multibuy-024","type":"OPEN_ISSUE","feature_id":"multibuy-discount-setup","summary":"[Regression watch — known defect] [Regression-watch, KNOWN_DEFECT/limitation — KHÔNG dùng làm oracle] Đổi quantity trực tiếp trong cart có thể hiện discount/compare price inconsistent","detail":"Known limitation KB-069: đổi quantity trực tiếp trong cart có thể hiện discount/compare price không nhất quán (ràng buộc hiển thị cart của Shopify, đã được accept). Limitation này còn được chấp nhận không, và mức lệch nào thì coi là regression?","kb_ids":["multibuy-mix-match-combo#KB-069"],"check_ids":["multibuy-mix-match-combo:CHK-055"],"supersedes":"OQ-discount-offers-072"}
```

## OQ-multibuy-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-025","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","summary":"Backend lưu \"How discount is applied\" dưới field tier_application_method, xử lý trong multibuy-discount Function","detail":"Phanh derivation: oracle duy nhất KB-043 có derivation code_artifact (suy từ cách dữ liệu tổ chức trong code). Tên field tier_application_method và 2 giá trị per_group/highest_tier_all có đúng với backend hiện hành không? Lưu ý staging 2026-10-18 thấy offer lưu giá trị ẩn discount_apply_type 'per_combo' (KB-086) — cần Dev xác nhận tên field/giá trị thật.","kb_ids":["multibuy-mix-match-combo#KB-043","multibuy-mix-match-combo#KB-086"],"check_ids":["multibuy-mix-match-combo:CHK-026"],"supersedes":"OQ-discount-offers-073"}
```

## OQ-multibuy-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-026","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","summary":"Empty \"+\" combo slot tồn tại trong DOM với id qvl-multibuy-tier_add-more","detail":"Phanh derivation: oracle duy nhất KB-051 có derivation code_artifact. Slot '+' trống được đánh dấu bằng id hay class `qvl-multibuy-tier_add-more`? Staging 2026-10-18 (KB-092) ghi nhận class `qvl-multibuy-tier_add-more` — cần Dev xác nhận selector ổn định trước khi dùng cho automation.","kb_ids":["multibuy-mix-match-combo#KB-051","multibuy-mix-match-combo#KB-092"],"check_ids":["multibuy-mix-match-combo:CHK-032"],"supersedes":"OQ-discount-offers-074"}
```

## OQ-multibuy-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-027","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","summary":"Widget Multibuy trên PDP: cấu trúc, phản ánh cart thật, không chặn nút Add to cart của theme","detail":"Cấu trúc widget Multibuy trên PDP staging (progress 3 mốc, slot '+', recommendation inline có stepper + 'Pick', nút ATC của theme không bị chặn) có phải thiết kế mong muốn? Tài liệu chỉ mô tả từng phần (remaining message, progress, slot).","kb_ids":["multibuy-mix-match-combo#KB-092"],"check_ids":["multibuy-mix-match-combo:CHK-069"],"supersedes":"OQ-discount-offers-075"}
```

## OQ-multibuy-028 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-028","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","summary":"Số trên badge 'Saved' của widget Multibuy so với discount thực trong cart","detail":"Badge 'Saved' của widget Multibuy trên staging hiện số khác discount thực trong cart (cart 6 món giảm $41.00, badge $27.00). Badge 'Saved' tính theo công thức nào (theo tier hiện tại, theo một combo, hay theo cart)? Lệch này có phải lỗi hiển thị gây hiểu nhầm cho buyer?","kb_ids":["multibuy-mix-match-combo#KB-092"],"check_ids":["multibuy-mix-match-combo:CHK-070"],"supersedes":"OQ-discount-offers-076"}
```

## OQ-multibuy-029 — OPEN_ISSUE

```json
{"oq_id":"OQ-multibuy-029","type":"OPEN_ISSUE","feature_id":"multibuy-discount-setup","summary":"Chế độ Percentage và 'How discount is applied' (Apply per combo / highest tier) tính giá thế nào trên storefront staging?","detail":"Run giữ mặc định Fixed total price nên control ẩn; 2 mode tính giá chưa có quan sát.","kb_ids":[],"check_ids":[],"supersedes":"OQ-discount-offers-087"}
```

## OQ-multibuy-030 — OPEN_ISSUE

```json
{"oq_id":"OQ-multibuy-030","type":"OPEN_ISSUE","feature_id":"multibuy-discount-setup","summary":"Badge Multibuy có ẩn khi offer ngoài lịch, và countdown có hiện trên widget Multibuy không; offer sau giờ start/hết hạn hiển thị thế nào?","detail":"KB-076 chưa kiểm được riêng cho Multibuy; chuyển trạng thái theo thời gian NOT_COVERED.","kb_ids":[],"check_ids":[],"supersedes":"OQ-discount-offers-088"}
```

## OQ-multibuy-031 — OPEN_ISSUE

```json
{"oq_id":"OQ-multibuy-031","type":"OPEN_ISSUE","feature_id":"multibuy-discount-setup","summary":"Popup và widget Multibuy trên mobile và với product có ảnh hiển thị thế nào?","detail":"Popup chỉ kiểm desktop; product thử không có ảnh (badge trên ảnh, lỗi console).","kb_ids":[],"check_ids":[],"supersedes":"OQ-discount-offers-089"}
```

## OQ-multibuy-032 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-multibuy-032","type":"NEEDS_CONFIRMATION","feature_id":"multibuy-discount-setup","summary":"Xác nhận expected cho các hành vi rủi ro cao (tiền/discount, mất dữ liệu, quyền) mới quan sát trên staging 2026-10-18 — hiện chỉ là OBSERVED_CURRENT, chưa có nguồn thẩm quyền, không dùng làm oracle STRONG: KB-087 (tiền / discount-calculation: multiplier bật mặc định → nhiều combo trong 1 cart. Item vẫn ); KB-095 (tiền / discount-calculation: pooling Multibuy và phân bổ theo tỷ lệ giá. Item vẫn publish )","kb_ids":["multibuy-mix-match-combo#KB-087","multibuy-mix-match-combo#KB-095"],"check_ids":[],"supersedes":"OQ-discount-offers-102"}
```
