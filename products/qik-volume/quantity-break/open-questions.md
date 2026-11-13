# Open Questions — quantity-break

## OQ-quantity-break-001 — CONFLICT

```json
{"oq_id":"OQ-quantity-break-001","type":"CONFLICT","feature_id":"quantity-break-trigger-and-tiers","summary":"[DCONF-001] [CONFLICT - phía A] Banner: automatic discount hoạt động dù app block bị tắt","side_a":"Theo tài liệu \"Quantity Break\" §Shared cross-variant rules, màn hình tạo offer có banner cảnh báo (ghi nhận live 2026-09-03): 'Automatic discounts work even if the app block is disabled. For testing, we recommend using Discount code to prevent customers from receiving unintended discounts.' Đây là 1 phía của xung đột DCONF-001 — xem conflicts[] — mâu thuẫn với hành vi hiện tại được ghi ở §Shared rules sau fix QVD-167 (phía B).","side_b":"Theo tài liệu \"Quantity Break\" §Shared cross-variant rules + §Edge Cases, hiện tại (sau fix QVD-167), discount Function của Quantity Break check theme-embed status và skip áp dụng discount nếu app block không được enable trong theme editor, ngay cả khi cart content khớp 1 tier hợp lệ; regression test của gating này đã được verified: với app/embed bị disable, 1 cart vốn đủ điều kiện 1 tier sẽ không được auto-discount. Đây là phía B của xung đột DCONF-001 — xem conflicts[] — mâu thuẫn với banner cảnh báo ở phía A vẫn còn hiển thị trên UI tạo offer.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ CONFLICT): Banner 'Automatic discounts work even if the app block is disabled…' còn hiện nguyên văn trên form cả 3 loại offer khi chọn Automatic discount; Dashboard báo embed Active và discount Quantity Break áp trong cart. Nhánh embed tắt (gating QVD-167) NOT_COVERED. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-083"],"supersedes":"OQ-discount-offers-001"}
```

## OQ-quantity-break-002 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-002","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-054"],"summary":"[Cần xác nhận] Phân cấp quyền staff sub-role khi cấu hình Quantity Break","detail":"Một tài khoản staff bị hạn chế quyền app (không phải Owner/Full-access) có bị giới hạn khả năng cấu hình offer Quantity Break so với Owner/staff full-access hay không? Tài liệu nguồn không có bằng chứng về phân cấp quyền staff cho riêng feature này.","supersedes":"OQ-discount-offers-005"}
```

## OQ-quantity-break-003 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-003","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-056"],"summary":"[Cần xác nhận] Giá quantity-break có tự recompute khi subscription discount đổi/mất giữa session","detail":"Khi discount của subscription app thay đổi hoặc bị xoá giữa session, giá quantity-break hiển thị cho shopper có tự recompute ngay lập tức hay giữ giá cũ (stale) cho tới khi reload/điều hướng? Tài liệu nguồn tự gắn cờ chưa chắc cho mô tả này.","supersedes":"OQ-discount-offers-006"}
```

## OQ-quantity-break-004 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-004","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-057"],"summary":"[Cần xác nhận] Tier/trigger/gift/subscription/display settings reload đúng sau khi refresh trang Portal","detail":"Sau khi Save và refresh toàn bộ trang Settings, mọi field (trigger/tier/gift/subscription/display/appearance/combination/scheduling/advanced) có reload lại đúng khớp dữ liệu đã lưu không? KB hiện chỉ xác nhận success toast xuất hiện ngay sau Save, chưa có xác nhận riêng cho bước reload.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Reload sau khi lưu 3 loại offer: mọi field bằng giá trị đã lưu; GET trả đúng response lưu (khác duy nhất kiểu shopify_connection_id). Một mẫu mỗi loại. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["_object-level#KB-032"],"supersedes":"OQ-discount-offers-007"}
```

## OQ-quantity-break-005 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-005","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-060"],"summary":"[Cần xác nhận] Biến quyết định offer nào thắng khi ≥2 offer type overlap trên cùng cart","detail":"Khi ≥2 offer type (bao gồm Quantity Break) cùng qualify trên 1 cart, biến nào quyết định offer nào thắng (discount rank/order trong Shopify admin? thứ tự Function evaluate? thứ tự add-to-cart?)? Đã xác nhận chắc là đúng 1 offer thắng (không chia/không cả hai), nhưng kết quả bị flip giữa 2 lần test live trên cùng 1 cặp offer — cần PO/Dev xác định rule trước khi viết test case regression xác định cho mọi tình huống overlap.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Overlap trên staging: cùng giỏ 3 đơn vị, đường add qua composer/ATC theme (property Quantity Break) → mã Quantity Break; qua popup Multibuy hoặc add không property → mã Multibuy; lặp lại ổn định theo đường add. Giỏ 11 đơn vị add không property → 2 line với 2 mã khác nhau. Chỉ quan sát, không suy quy tắc. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["_object-level#KB-026","_object-level#KB-027","_object-level#KB-028","_object-level#KB-014"],"supersedes":"OQ-discount-offers-008"}
```

## OQ-quantity-break-006 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-006","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-061"],"summary":"[Cần xác nhận — KHÔNG dùng 1 phía làm oracle] DCONF-001: automatic discount có áp dụng khi app block/theme embed bị tắt hay không","detail":"DCONF-001: Automatic discount của Quantity Break có áp dụng khi app block/theme embed bị tắt hay không? Banner UI (KB-060) nói 'có vẫn hoạt động', nhưng fix QVD-167 sau 1 incident thật (77 đơn live, KB-062) cho thấy discount Function SKIP khi app block/theme-embed tắt (KB-061). Cần PO/Dev xác nhận: banner đang là copy cũ chưa update sau fix, hay 'app block' và 'theme embed' là 2 khái niệm Shopify khác nhau mà fix chỉ cover 1 trong 2, hay đây là 1 gap thật cần fix thêm.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Như OQ-001: banner nguyên văn, embed Active, discount áp trong cart khi embed Active; nhánh embed tắt NOT_COVERED. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-083"],"supersedes":"OQ-discount-offers-009"}
```

## OQ-quantity-break-007 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-007","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-065","quantity-break:CHK-081"],"summary":"[Cần xác nhận] Portal preview pricing khớp storefront live rendering — chỉ 1 sample, chưa đủ để tổng quát hoá","detail":"Portal tier-settings preview pricing có LUÔN khớp chính xác với giá render thực tế trên storefront cho mọi offer/sản phẩm, hay ví dụ khớp đã quan sát (offer 'Offer 15') chỉ là 1 trường hợp đơn lẻ? Cần thêm ≥1 sample độc lập khác (sản phẩm/offer khác) để nâng cấp thành rule tổng quát CONFIRMED_EXPECTED.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Preview form dùng giá mẫu cố định ($100/$180/$240) không theo product trigger; PDP dùng giá thật và khớp cart. Mẫu thứ 2 cho thấy preview KHÔNG phản ánh giá product. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-086"],"supersedes":"OQ-discount-offers-010"}
```

## OQ-quantity-break-008 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-008","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-066"],"summary":"[Cần xác nhận] True default của field 'Position' (Above vs Below volume tiers)","detail":"True default của field Position (Volume discount for subscription) là 'Above volume tiers' hay 'Below volume tiers'? Ticket gốc và ví dụ live quan sát mâu thuẫn nhau; cần 1 lần test trên offer hoàn toàn mới (chưa qua tay merchant) để xác định default ngoài-hộp.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Form subscription mới: Position mặc định 'Above volume tiers'. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-077"],"supersedes":"OQ-discount-offers-011"}
```

## OQ-quantity-break-009 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-009","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-067"],"summary":"[Cần xác nhận] Sự tồn tại của group 'Content' trong Display settings","detail":"Group 'Content' trong Display settings có tồn tại/được ship cho Quantity Break hay không? 3 ví dụ live kiểm tra đều không thấy group này. Cần PO/Dev xác nhận group này có áp dụng cho offer type này hay chỉ tồn tại ở ticket.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Display settings có đúng 2 nhóm Variant display / Pricing display; không có nhóm Content. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-079"],"supersedes":"OQ-discount-offers-012"}
```

## OQ-quantity-break-010 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-010","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-068"],"summary":"[Cần xác nhận] Hành vi accordion (collapse-by-default) của Display settings","detail":"Display settings có hành vi accordion (collapsed-by-default, click để mở) như spec mô tả, hay luôn hiển thị (always-visible section) như quan sát qua accessibility-tree gợi ý? Cần 1 lần click-test trực tiếp trên Portal thật để xác nhận.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Display settings luôn mở, không collapse; accordion có ở Appearance & style (thu gọn mặc định, click mở/đóng). (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-079"],"supersedes":"OQ-discount-offers-013"}
```

## OQ-quantity-break-011 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-011","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-069"],"summary":"[Cần xác nhận] 2 field điều kiện của Variant display xuất hiện khi checkbox cha ON","detail":"Khi bật checkbox cha của Variant display, 2 field con ('Allow customer to choose variant for single-item offer', 'Variant swatch settings') có thực sự xuất hiện như ticket mô tả hay không? Chưa có ví dụ live nào bật thử checkbox cha này.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Không có checkbox cha 'Variant display' (là nhãn nhóm); bật checkbox con không làm xuất hiện field con, chỉ preview đổi. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-079","quantity-break#KB-080"],"supersedes":"OQ-discount-offers-014"}
```

## OQ-quantity-break-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-012","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-070"],"summary":"[Cần xác nhận] 'Enable countdown timer' và quan hệ với QVD-147","detail":"Checkbox 'Enable countdown timer' có hành vi/validation bổ sung nào liên quan QVD-147 ngoài việc hiện/ẩn 1 countdown timer đơn giản không? Ticket chưa được phân tích sâu; cần PO/Dev xác nhận phạm vi đầy đủ trước khi viết test case regression chi tiết.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): (bucket b — chỉ ghi kèm) Countdown: checkbox chỉ hiện sau khi bật end date, mặc định 'HURRY UP!'/'Sale end in'; trên PDP nằm đầu widget Quantity Break, đếm ngược live. Phạm vi QVD-147 vẫn cần PO/Dev. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-084","quantity-break#KB-085","_object-level#KB-013"],"supersedes":"OQ-discount-offers-015"}
```

## OQ-quantity-break-013 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-013","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-071","quantity-break:CHK-076"],"summary":"[Cần xác nhận] UI hiển thị khi 1 tier có nhiều gift PRODUCT KHÁC NHAU","detail":"Khi 1 tier có nhiều gift PRODUCT KHÁC NHAU (không cùng loại) được gắn cùng lúc, badge đếm gift và dòng giá hiển thị trên storefront có dạng gì? Tài liệu nguồn chỉ quan sát trường hợp nhiều gift cùng loại; cần 1 lần test live để xác định UI thật.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Không tạo offer Buy X get Y kèm gift; chỉ quan sát form (khối Gifts trên tier 1). (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-078"],"supersedes":"OQ-discount-offers-016"}
```

## OQ-quantity-break-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-014","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-072"],"summary":"[Cần xác nhận] Checkbox 'Allow customers to choose different variants for each item' có nối với config Variant Swatches hay không","detail":"Checkbox 'Allow customers to choose different variants for each item' (Display settings của Quantity Break) có thực sự nối với/chia sẻ configuration của feature Variant Swatches riêng hay không, và nếu có, UI 'Variant swatch settings' hình dạng gì? Hiện Preview chỉ hiện mock data chung, chưa rõ liên kết thật.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Bật 'Allow customers to choose different variants for each item': không có 'Variant swatch settings' hay link Variant swatches; chỉ preview đổi. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-080"],"supersedes":"OQ-discount-offers-017"}
```

## OQ-quantity-break-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-015","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","check_ids":["quantity-break:CHK-074"],"summary":"[Cần xác nhận] Toggle hiện/ẩn selector riêng của widget đồng bộ động với theme","detail":"Khi merchant bật toggle cho widget hiện variant selector riêng, selector đó có thực sự đồng bộ động 2 chiều với variant selector gốc của theme, hay là 2 selector độc lập có thể lệch nhau? Tài liệu tự gắn cờ chưa chắc cho phần đồng bộ này.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Widget không có selector variant riêng khi checkbox tắt; đổi variant theme thì widget giữ nguyên. Đồng bộ hai chiều không kiểm được. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-087"],"supersedes":"OQ-discount-offers-018"}
```

## OQ-quantity-break-016 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-016","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","summary":"Card \"Appstle℠ Subscriptions App\" dưới info banner của Volume discount for subscription (Quantity Break) được tài liệu nguồn tự diễn giải (hedged, chưa xác nhận) thành \"app Quantity Break không tự có hạ tầng subscription riêng mà phụ thuộc vào 1 app subscription riêng\" — cách diễn đạt chung của app có thể tương thích app subscription khác ngoài Appstle. Cần PO/Dev xác nhận app Quantity Break có phụ thuộc cứng vào một app subscription ngoài hay không, và nếu có thì giới hạn ở app nào (KB-074, INFERRED/LOW, tách riêng khỏi KB-043 vì mang nội dung hedged mà KB-043 không có).","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Form subscription mới: banner nguyên văn + card 'Recommended app:' chỉ nhắc Appstle (Free to install). (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["quantity-break#KB-077"],"supersedes":"OQ-discount-offers-047"}
```

## OQ-quantity-break-017 — CONFLICT

```json
{"oq_id":"OQ-quantity-break-017","type":"CONFLICT","feature_id":"quantity-break-trigger-and-tiers","summary":"Mặc định 3 checkbox Combination (Product/Order/Shipping) của offer Quantity Break: tài liệu nói tắt hết, staging hiện bật hết (kèm dropdown 'One per product (best value wins)'). Expected mặc định là gì?","side_a":"Base KB-055: tất cả default unchecked (QVD-25).","side_b":"Staging KB-082: cả 3 CHECKED mặc định; offer lưu combinesWith true/true/true.","conflict_group":"CONF-discount-offers-R1018-01","kb_ids":["quantity-break#KB-055","quantity-break#KB-082"],"check_ids":["quantity-break:CHK-034"],"related_oq_ids":["OQ-multibuy-008","OQ-multibuy-019"],"supersedes":"OQ-discount-offers-049"}
```

## OQ-quantity-break-018 — CONFLICT

```json
{"oq_id":"OQ-quantity-break-018","type":"CONFLICT","feature_id":"quantity-break-trigger-and-tiers","summary":"Màu mặc định Appearance & style của offer Quantity Break: tài liệu #2196F3/#262626/#FC81C7/#FFFFFF, staging #606B57/#1C1D21/#D75E60/#FFFFFF. Default hiện hành là bộ nào?","side_a":"Base KB-054: #2196F3 / #262626 / #FC81C7 / #FFFFFF.","side_b":"Staging KB-081: #606B57 / #1C1D21 / #D75E60 / #FFFFFF.","conflict_group":"CONF-discount-offers-R1018-02","kb_ids":["quantity-break#KB-054","quantity-break#KB-081"],"check_ids":["quantity-break:CHK-033"],"supersedes":"OQ-discount-offers-050"}
```

## OQ-quantity-break-019 — CONFLICT

```json
{"oq_id":"OQ-quantity-break-019","type":"CONFLICT","feature_id":"quantity-break-trigger-and-tiers","summary":"Label type mặc định của tier 2 Quantity Break: tài liệu 'Flat', staging 'Classic' (dropdown không có 'Flat').","side_a":"Base KB-017: tier 2 label 'Flat' text 'Most popular'.","side_b":"Staging KB-076: tier 2 Label type 'Classic', options Classic/Oval/Tag/Callout.","conflict_group":"CONF-discount-offers-R1018-03","kb_ids":["quantity-break#KB-017","quantity-break#KB-076"],"check_ids":["quantity-break:CHK-008"],"supersedes":"OQ-discount-offers-051"}
```

## OQ-quantity-break-020 — CONFLICT

```json
{"oq_id":"OQ-quantity-break-020","type":"CONFLICT","feature_id":"quantity-break-trigger-and-tiers","summary":"End time mặc định khi end date = start date: tài liệu 11:59 PM; staging (tick end date trên offer đã lưu, start hôm nay) điền End date = hôm nay, End time ≈ hiện tại + 1 giờ. Quy tắc hiện hành là gì (khác nhau giữa form mới và offer đã lưu?)","side_a":"Base KB-057: start = end date → end time default 11:59 PM.","side_b":"Staging KB-084: End date = hôm nay, End time ≈ giờ hiện tại + 1h (form mới: start + 1 ngày).","conflict_group":"CONF-discount-offers-R1018-08","kb_ids":["quantity-break#KB-057","quantity-break#KB-084"],"check_ids":["quantity-break:CHK-036","quantity-break:CHK-077"],"related_oq_ids":["OQ-multibuy-009"],"supersedes":"OQ-discount-offers-055"}
```

## OQ-quantity-break-021 — CONFLICT

```json
{"oq_id":"OQ-quantity-break-021","type":"CONFLICT","feature_id":"quantity-break-trigger-and-tiers","summary":"Slots QVD-127 trên widget Quantity Break: tài liệu nói có slot hiện dần theo số unit còn thiếu; staging (layout mặc định) không có slot (slot chỉ ở widget Multibuy). Slot phụ thuộc layout/cấu hình, hay đã bỏ?","side_a":"Base KB-024: storefront hiển thị slots đến tier kế tiếp (QVD-127).","side_b":"Staging KB-087: widget Quantity Break không có slot.","conflict_group":"CONF-discount-offers-R1018-07","kb_ids":["quantity-break#KB-024","quantity-break#KB-087"],"check_ids":["quantity-break:CHK-029","quantity-break:CHK-079"],"supersedes":"OQ-discount-offers-056"}
```

## OQ-quantity-break-022 — OPEN_ISSUE

```json
{"oq_id":"OQ-quantity-break-022","type":"OPEN_ISSUE","feature_id":"quantity-break-trigger-and-tiers","summary":"[Regression watch — known defect] [Regression-watch, KNOWN_DEFECT — KHÔNG dùng làm oracle đúng/sai] Giá trị discount âm nhập trực tiếp không bị chặn","detail":"Known defect KB-063: Discount value âm gõ/paste trực tiếp không bị chặn (chỉ nút mũi tên bị chặn). Đây vẫn là defect mở? Expected sau fix là chặn mọi giá trị âm bằng inline error? Nếu lần chạy thấy hành vi khác (đã chặn, hoặc ảnh hưởng giá storefront), báo QA/Dev — không tự kết luận đâu là đúng.","kb_ids":["quantity-break#KB-063"],"check_ids":["quantity-break:CHK-047"],"supersedes":"OQ-discount-offers-077"}
```

## OQ-quantity-break-023 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-023","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","summary":"Form 'Quantity breaks for same product' mới: Offer title mặc định và trigger mặc định 'All products'","detail":"Offer title mặc định 'Buy more, save more' và trigger mặc định 'All products' của form Quantity Break mới (quan sát staging) có phải là mặc định mong muốn không? Tài liệu chỉ xác nhận 5 radio và vị trí 'Exclude products', không nêu giá trị mặc định.","kb_ids":["quantity-break#KB-075"],"check_ids":["quantity-break:CHK-075"],"supersedes":"OQ-discount-offers-078"}
```

## OQ-quantity-break-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-024","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","summary":"Add to cart với widget Quantity Break: số lượng = tier đang chọn, property ẩn; không chọn tier thì theme thêm 1 đơn vị","detail":"Đường add-to-cart của widget Quantity Break trên staging (add.js?qvl-discount với số lượng = tier và property _qvl-volume-id; không chọn tier thì theme thêm 1 đơn vị không property) có phải hành vi mong muốn? Property này còn ảnh hưởng mã thắng khi product thuộc nhiều offer (object:KB-026) — cần xác nhận vai trò của property.","kb_ids":["quantity-break#KB-088"],"check_ids":["quantity-break:CHK-080"],"supersedes":"OQ-discount-offers-079"}
```

## OQ-quantity-break-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-025","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","summary":"[Mức object] Mỗi offer = một automatic discount Shopify: tạo/sửa/xoá offer đồng bộ discount","detail":"Vòng đời offer ↔ automatic discount Shopify (tạo discount trước khi lưu offer; xoá discount phía client sau DELETE API) quan sát trên staging có phải thiết kế mong muốn? Khi một bước phía client thất bại (ví dụ discountAutomaticDelete lỗi sau khi offer đã xoá) có cơ chế dọn discount mồ côi không — chưa kiểm.","kb_ids":["_object-level#KB-015","_object-level#KB-017"],"check_ids":["quantity-break:CHK-083"],"supersedes":"OQ-discount-offers-080"}
```

## OQ-quantity-break-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-026","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","summary":"Badge Quantity Break trên card collection/search: text theo tier cao nhất, góc trên-trái","detail":"Badge trên collection/search cho product thuộc nhiều offer chỉ hiện một badge (quan sát: Quantity Break + Wholesale → 'UP TO 20% OFF'; cả 3 loại → 'MULTIBUY'). Quy tắc chọn badge nào là gì? (không suy từ quan sát)","kb_ids":["_object-level#KB-031","_object-level#KB-025"],"check_ids":["quantity-break:CHK-086"],"supersedes":"OQ-discount-offers-081"}
```

## OQ-quantity-break-027 — OPEN_ISSUE

```json
{"oq_id":"OQ-quantity-break-027","type":"OPEN_ISSUE","feature_id":"quantity-break-trigger-and-tiers","summary":"Widget subscription (Subscribe & save / One-time purchase) trên storefront render và tính giá thế nào khi có app subscription (Appstle) và product eligible?","detail":"Template subscription chỉ quan sát được form; stacking formula và reset tier selection không có quan sát storefront — cài app bên thứ ba bị cấm trong run.","kb_ids":[],"check_ids":[],"supersedes":"OQ-discount-offers-091"}
```

## OQ-quantity-break-028 — OPEN_ISSUE

```json
{"oq_id":"OQ-quantity-break-028","type":"OPEN_ISSUE","feature_id":"quantity-break-trigger-and-tiers","summary":"Offer Scheduled khi tới giờ start có tự chuyển Running và widget/discount xuất hiện trên storefront không; khi tới end date, countdown về 0 và offer chuyển Expired thì widget/discount ra sao?","detail":"Run chỉ quan sát offer Running và Scheduled trước giờ start (offer bị xoá trước start); chuyển trạng thái theo thời gian NOT_COVERED.","kb_ids":[],"check_ids":[],"supersedes":"OQ-discount-offers-092"}
```

## OQ-quantity-break-029 — OPEN_ISSUE

```json
{"oq_id":"OQ-quantity-break-029","type":"OPEN_ISSUE","feature_id":"quantity-break-trigger-and-tiers","summary":"Khi store chạm giới hạn 25 automatic discount của Shopify, app báo gì khi tạo offer Quantity Break mới?","detail":"Store staging có 5/25, không thấy cảnh báo — ngưỡng chưa chạm; mỗi offer chiếm 1 automatic discount nên giới hạn ảnh hưởng trực tiếp việc tạo offer.","kb_ids":[],"check_ids":[],"supersedes":"OQ-discount-offers-093"}
```

## OQ-quantity-break-030 — OPEN_ISSUE

```json
{"oq_id":"OQ-quantity-break-030","type":"OPEN_ISSUE","feature_id":"quantity-break-trigger-and-tiers","summary":"Quantity Break có thật sự không gộp số lượng giữa các product khác nhau trên store staging hiện tại?","detail":"Run chỉ đo với offer 1 product; vế 'không pool giữa product khác' của KB-010 chưa có quan sát.","kb_ids":[],"check_ids":[],"supersedes":"OQ-discount-offers-094"}
```

## OQ-quantity-break-031 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-quantity-break-031","type":"NEEDS_CONFIRMATION","feature_id":"quantity-break-trigger-and-tiers","summary":"Xác nhận expected cho các hành vi rủi ro cao (tiền/discount, mất dữ liệu, quyền) mới quan sát trên staging 2026-10-18 — hiện chỉ là OBSERVED_CURRENT, chưa có nguồn thẩm quyền, không dùng làm oracle STRONG: KB-089 (tiền / discount-calculation: cart tự tính lại mức Quantity Break khi đổi số lượng. Item vẫ)","kb_ids":["quantity-break#KB-089"],"check_ids":[],"supersedes":"OQ-discount-offers-103"}
```

## OQ-quantity-break-032 — OPEN_ISSUE

```json
{"oq_id":"OQ-quantity-break-032","type":"OPEN_ISSUE","feature_id":"quantity-break-trigger-and-tiers","summary":"Known defect (tài liệu v1): casing của label đếm gift của Buy X get Y không nhất quán giữa các tier ('1 gift' / '2 Gifts' / '3 gifts') — chỉ là regression watch, không phải expected. Chưa tái kiểm trên staging (run REFRESH 2026-10-18 không tạo offer Buy X get Y).","kb_ids":["quantity-break#KB-039"],"check_ids":[],"supersedes":"OQ-discount-offers-105"}
```
