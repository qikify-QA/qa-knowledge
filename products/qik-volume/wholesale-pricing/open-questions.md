# Open Questions — wholesale-pricing

## OQ-wholesale-pricing-001 — CONFLICT

```json
{"oq_id":"OQ-wholesale-pricing-001","type":"CONFLICT","feature_id":"wholesale-tier-setup","summary":"[DCONF-001] Storefront — drawer doesn't exist (structural correction)","side_a":"Tài liệu §Storefront nêu rằng, trái với spec, hành vi live trên store test-vl-1 (product 'Clay Plant Pot', offer 'Offer 17') render toàn bộ variant-composition UI trực tiếp inline trên PDP — không có preview card, không có link 'Select now', không slide-in panel, không backdrop. Lưu ý: (Table layout) lại mô tả nội dung render 'inside the Variant Selection Drawer' — xem DCONF-001, hai mô tả này chưa được hoà giải trong tài liệu.","side_b":"Tài liệu §Table layout nêu rằng cùng table này cũng render bên trong Variant Selection Drawer, compact hơn (giảm font size/padding) để fit chiều rộng drawer; hành vi active-row highlight giống hệt và vẫn update live theo stepper. Lưu ý: điều này nhắc tới 'Variant Selection Drawer' như một UI đang tồn tại, trong khi ở §Storefront nêu rằng rendering thực tế trên test-vl-1 là inline, không có drawer — xem DCONF-001, chưa được hoà giải.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ CONFLICT): Composer Wholesale inline trên PDP, không preview card/'Select now'/drawer, desktop + mobile, theme 'Generated Data Theme'. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["wholesale-pricing-offer#KB-WPO-083"],"supersedes":"OQ-discount-offers-004"}
```

## OQ-wholesale-pricing-002 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-002","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","check_ids":["wholesale-pricing-offer:CHK-015"],"summary":"Variant Selection UI pattern thật trên storefront — inline-on-PDP hay slide-in Drawer (DCONF-001)","detail":"Wholesale Pricing Offer storefront: 'Variant Selection Drawer' (slide-in panel, theo spec QVD-143 và theo mô tả Table layout) có thực sự tồn tại, hay inline-rendering-on-PDP (đã quan sát live trên test-vl-1) là hành vi chuẩn/cuối? Nếu drawer tồn tại, nó xuất hiện trong điều kiện nào (theme khác, device khác, config khác) mà test-vl-1 chưa cover?","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): = OQ-004. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["wholesale-pricing-offer#KB-WPO-083"],"supersedes":"OQ-discount-offers-037"}
```

## OQ-wholesale-pricing-003 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-003","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","check_ids":["wholesale-pricing-offer:CHK-018"],"summary":"Để Max của tier cuối trống — display label vs discount math thật","detail":"Khi merchant để trống Max của tier cuối (hint 'leave Max empty for unlimited'), việc này chỉ thay đổi display label của tier đó, hay cũng thay đổi discount math thật áp dụng cho quantity vượt ngưỡng? Hint text hiện tại có thể gây hiểu lầm — cần xác nhận hành vi thật trước khi viết oracle cho boundary case này.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Max trống → nhãn '21+ Items', lưu null; 42 đơn vị nhận mức tier cuối cho toàn bộ. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["wholesale-pricing-offer#KB-WPO-080"],"supersedes":"OQ-discount-offers-038"}
```

## OQ-wholesale-pricing-004 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-004","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","check_ids":["wholesale-pricing-offer:CHK-019"],"summary":"UI stepper/badge khi variant type cuối có số lượng value lớn (20+)","detail":"Với variant type cuối có số lượng value lớn (ví dụ 20+ màu), UI badge/quantity-stepper-per-value của Wholesale Pricing Offer có scale/scroll hợp lý không, hay thiết kế hiện tại giả định số lượng value nhỏ? Cần một test fixture cụ thể và xác nhận PO/Dev về kỳ vọng UX ở quy mô này.","supersedes":"OQ-discount-offers-039"}
```

## OQ-wholesale-pricing-005 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-005","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","check_ids":["wholesale-pricing-offer:CHK-020"],"summary":"Offer chỉ có 1 variant type (không multi-variant) — rule 'variant type cuối đặc cách' có còn áp dụng hợp lý","detail":"Khi offer Wholesale chỉ cấu hình trên product có đúng 1 variant type (không có type thứ hai để làm 'type đầu'), rule 'variant type cuối cùng nhận quantity stepper, type khác render single-select' áp dụng ra sao? Logic badge-counter (gắn theo value hiện tại của type đầu) có còn ý nghĩa khi không có type đầu riêng biệt, hay suy biến thành dạng khác?","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Product 1 option: VARIANTS chỉ có nhãn option + dòng stepper từng giá trị, không có hàng swatch (quan sát trên product cũng thuộc QB+MB). (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["wholesale-pricing-offer#KB-WPO-085"],"supersedes":"OQ-discount-offers-040"}
```

## OQ-wholesale-pricing-006 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-006","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","check_ids":["wholesale-pricing-offer:CHK-022"],"summary":"Chuyển Layout (card <-> table) có áp dụng live trên storefront không cần reload","detail":"Việc chuyển đổi Layout (card <-> table) trong Portal có thực sự áp dụng live trên storefront mà không cần reload trang, như ticket AC claim? Claim này chưa được independently verify — cần 1 lần test trực tiếp (hoặc xác nhận PO/Dev) trước khi dùng làm oracle cho check STATE_DATA này.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Preview đổi ngay khi chọn layout; storefront sau khi lưu hiện bảng; cập nhật live không cần reload không đo được. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["wholesale-pricing-offer#KB-WPO-082"],"supersedes":"OQ-discount-offers-041"}
```

## OQ-wholesale-pricing-007 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-007","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","check_ids":["wholesale-pricing-offer:CHK-023"],"summary":"Một chỉnh sửa tier HỢP LỆ (không gap) có persist sau khi reload Portal","detail":"Tài liệu nguồn chỉ xác nhận rằng một GAP do lỗi continuity vẫn tồn tại sau reload (KB-WPO-023, khung KNOWN_DEFECT) — không có statement riêng nào xác nhận rằng một chỉnh sửa tier HỢP LỆ (không tạo gap) cũng persist đúng sau reload. Đây có phải một gap documentation đơn giản (hành vi hiển nhiên, không cần ghi) hay cần 1 test riêng để xác nhận?","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Sửa tier hợp lệ được lưu và giữ sau reload (giá trị lưu dạng chuỗi). (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["wholesale-pricing-offer#KB-WPO-081"],"supersedes":"OQ-discount-offers-042"}
```

## OQ-wholesale-pricing-008 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-008","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","check_ids":["wholesale-pricing-offer:CHK-026","wholesale-pricing-offer:CHK-034"],"summary":"[NEEDS_CONFIRMATION] Offer nào thắng khi Wholesale overlap Quantity Break/Multibuy — biến quyết định CHƯA xác định","detail":"Khi Wholesale Pricing Offer overlap trigger với Quantity Break và/hoặc Multibuy trên cùng 1 cart VÀ cả hai offer đều có discount active khác 0% (không phải trường hợp qty=3 đã test, nơi Wholesale Tier 1 là 0%), biến nào quyết định offer nào thắng? Kết quả đã quan sát bị flip giữa 2 lần test live trên cùng cặp offer — cần PO/Dev xác nhận rule priority (discount rank trong Shopify Admin, thứ tự function evaluate, thứ tự add-to-cart, hay yếu tố khác) trước khi viết được oracle regression xác định cho trigger-overlap.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Wholesale × Quantity Break cả hai khác 0 (11/21 đơn vị): luôn mã Quantity Break (7 lần), cả có/không property. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["_object-level#KB-027","wholesale-pricing-offer#KB-WPO-087"],"supersedes":"OQ-discount-offers-043"}
```

## OQ-wholesale-pricing-009 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-009","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","check_ids":["wholesale-pricing-offer:CHK-030","wholesale-pricing-offer:CHK-033"],"summary":"[NEEDS_CONFIRMATION] Campaign scheduling thực sự gate offer availability cho Wholesale (chưa re-verify riêng)","detail":"Campaign scheduling (start/end date) của Wholesale Pricing Offer có thực sự gate việc hiển thị/áp dụng offer trên storefront đúng như Quantity Break/Multibuy, hay đây chỉ là một suy đoán từ sự tương tự UI chưa được live-test riêng cho Wholesale? Cần 1 lần test riêng hoặc xác nhận PO/Dev trước khi dùng CHK-011 (UI fields) làm proxy cho enforcement hành vi thật.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): Offer start ngày mai: Scheduled; trước giờ start không widget, không event view, không áp discount; sau start/end NOT_COVERED. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["wholesale-pricing-offer#KB-WPO-086"],"supersedes":"OQ-discount-offers-044"}
```

## OQ-wholesale-pricing-010 — CONFLICT

```json
{"oq_id":"OQ-wholesale-pricing-010","type":"CONFLICT","feature_id":"wholesale-tier-setup","summary":"Header cột thứ 3 bảng Wholesale (layout table): tài liệu 'Unit price', staging 'ITEM PRICE'.","side_a":"Base KB-WPO-059: Quantity | Discount | Unit price.","side_b":"Staging KB-WPO-082: QUANTITY | DISCOUNT | ITEM PRICE.","conflict_group":"CONF-discount-offers-R1018-06","kb_ids":["wholesale-pricing-offer#KB-WPO-059","wholesale-pricing-offer#KB-WPO-082"],"check_ids":["wholesale-pricing-offer:CHK-012"],"related_oq_ids":["OQ-wholesale-pricing-006"],"supersedes":"OQ-discount-offers-054"}
```

## OQ-wholesale-pricing-011 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-011","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","summary":"Trên product thuộc cả Wholesale (layout table) và Quantity Break, composer Wholesale ở 11/21 đơn vị không đánh dấu hàng active và 'Subtotal' hiện giá gốc (không trừ 15%/20%), trong khi tài liệu nói hàng active được highlight và subtotal gạch giá gốc khi có discount. Đây là hành vi đúng khi overlap (offer khác thắng ở cart) hay lỗi hiển thị?","kb_ids":["wholesale-pricing-offer#KB-WPO-054","wholesale-pricing-offer#KB-WPO-060","wholesale-pricing-offer#KB-WPO-087"],"check_ids":[],"related_oq_ids":["OQ-wholesale-pricing-008"],"supersedes":"OQ-discount-offers-058"}
```

## OQ-wholesale-pricing-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-012","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","summary":"Tạo offer có start date tương lai: discount Shopify được tạo ở trạng thái ACTIVE (startsAt = lúc lưu) rồi vài giây sau mới update sang SCHEDULED. Khoảng ACTIVE ngắn này có được chấp nhận (rủi ro áp discount sớm) không?","kb_ids":["wholesale-pricing-offer#KB-WPO-086"],"check_ids":[],"related_oq_ids":["OQ-wholesale-pricing-009"],"supersedes":"OQ-discount-offers-071"}
```

## OQ-wholesale-pricing-013 — OPEN_ISSUE

```json
{"oq_id":"OQ-wholesale-pricing-013","type":"OPEN_ISSUE","feature_id":"wholesale-tier-setup","summary":"[Regression watch — known defect] [Regression-watch, KNOWN_DEFECT] Sửa Max của 1 tier tạo gap — save không báo lỗi validation","detail":"Known defect KB-WPO-023: tier continuity không được validate (sửa Max tạo gap vẫn lưu được, gap còn sau reload), trái AC gốc 'must be validated for continuity'. Defect còn mở? Expected sau fix là chặn lưu với thông báo gì?","kb_ids":["wholesale-pricing-offer#KB-WPO-023"],"check_ids":["wholesale-pricing-offer:CHK-016"],"supersedes":"OQ-discount-offers-082"}
```

## OQ-wholesale-pricing-014 — OPEN_ISSUE

```json
{"oq_id":"OQ-wholesale-pricing-014","type":"OPEN_ISSUE","feature_id":"wholesale-tier-setup","summary":"[Regression watch — known defect] [Regression-watch, KNOWN_DEFECT] Quantity rơi vào gap do misconfiguration — full price, không lỗi hiển thị cho buyer","detail":"Known defect KB-WPO-024: quantity rơi vào gap (do lỗi continuity) nhận full price, không tier highlight, không thông báo cho shopper. Defect còn mở và có kế hoạch xử lý (chặn gap ở portal hay cảnh báo ở storefront) không?","kb_ids":["wholesale-pricing-offer#KB-WPO-024"],"check_ids":["wholesale-pricing-offer:CHK-017"],"supersedes":"OQ-discount-offers-083"}
```

## OQ-wholesale-pricing-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-015","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","summary":"Add to cart từ composer Wholesale: 1 request nhiều item kèm property ẩn; tier tính trên tổng số lượng các variant line","detail":"Đường add-to-cart của composer Wholesale trên staging (1 request nhiều item, property _qvl-wholesale-id, tier theo tổng số lượng các variant line của cùng product) có phải hành vi mong muốn? Tài liệu nêu tier theo tổng số lượng nhưng không mô tả cơ chế add/property.","kb_ids":["wholesale-pricing-offer#KB-WPO-084"],"check_ids":["wholesale-pricing-offer:CHK-031"],"supersedes":"OQ-discount-offers-084"}
```

## OQ-wholesale-pricing-016 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-016","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","summary":"Nút Add to cart của theme bị disable khi composer Wholesale đang ở số lượng 0","detail":"Trên product thuộc cả Wholesale và Quantity Break, nút Add to cart của theme bị disable khi composer Wholesale = 0 dù widget Quantity Break đã chọn tier — buyer muốn mua theo tier Quantity Break bị chặn. Đây là hành vi mong muốn?","kb_ids":["_object-level#KB-025"],"check_ids":["wholesale-pricing-offer:CHK-032"],"supersedes":"OQ-discount-offers-085"}
```

## OQ-wholesale-pricing-017 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-017","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","summary":"Badge Wholesale trên card collection/search: 'BULK SAVING' góc trên-trái","detail":"Badge Wholesale 'BULK SAVING' trên collection/search (góc trên-trái, bo 6px) quan sát trên staging có phải hành vi mong muốn? Badge trên ảnh PDP chưa đánh giá được (product thử không có ảnh); badge không phân biệt offer Running với Scheduled.","kb_ids":["_object-level#KB-031"],"check_ids":["wholesale-pricing-offer:CHK-035"],"supersedes":"OQ-discount-offers-086"}
```

## OQ-wholesale-pricing-018 — OPEN_ISSUE

```json
{"oq_id":"OQ-wholesale-pricing-018","type":"OPEN_ISSUE","feature_id":"wholesale-tier-setup","summary":"Trên product nằm trong trigger của cả Wholesale và Quantity Break, có đường thêm cart nào tạo line mang property _qvl-wholesale-id không, và khi đó mã nào áp?","detail":"Staging: composer Wholesale trên product overlap gắn property Quantity Break; chưa có line mang _qvl-wholesale-id trên product overlap, chưa kiểm cart trộn line có/không property — không biết Wholesale có thể thắng khi overlap.","kb_ids":[],"check_ids":[],"related_oq_ids":["OQ-wholesale-pricing-008"],"supersedes":"OQ-discount-offers-095"}
```

## OQ-wholesale-pricing-019 — OPEN_ISSUE

```json
{"oq_id":"OQ-wholesale-pricing-019","type":"OPEN_ISSUE","feature_id":"wholesale-tier-setup","summary":"Offer Wholesale Scheduled khi tới giờ start có tự chuyển Running và widget/discount xuất hiện; khi tới end date chuyển Expired thì sao?","detail":"Offer Scheduled bị xoá trước giờ start; chuyển trạng thái theo thời gian NOT_COVERED.","kb_ids":[],"check_ids":[],"related_oq_ids":["OQ-wholesale-pricing-009"],"supersedes":"OQ-discount-offers-096"}
```

## OQ-wholesale-pricing-020 — OPEN_ISSUE

```json
{"oq_id":"OQ-wholesale-pricing-020","type":"OPEN_ISSUE","feature_id":"wholesale-tier-setup","summary":"Composer product 1 option khi Wholesale đứng riêng, và layout table ở số lượng có giảm khi product chỉ thuộc Wholesale, hiển thị thế nào?","detail":"Hai trường hợp chỉ quan sát trên product overlap (1 option) hoặc ở 2 đơn vị tier 0% (table).","kb_ids":[],"check_ids":[],"supersedes":"OQ-discount-offers-097"}
```

## OQ-wholesale-pricing-021 — OPEN_ISSUE

```json
{"oq_id":"OQ-wholesale-pricing-021","type":"OPEN_ISSUE","feature_id":"wholesale-tier-setup","summary":"Typography của form Wholesale có nhóm 'Normal text' (KB-WPO-032) không?","detail":"Explorer chỉ ghi 3 nhóm Heading/Body/Badge, không khẳng định vắng — test case Typography chưa có quan sát đủ.","kb_ids":[],"check_ids":[],"supersedes":"OQ-discount-offers-098"}
```

## OQ-wholesale-pricing-022 — OPEN_ISSUE

```json
{"oq_id":"OQ-wholesale-pricing-022","type":"OPEN_ISSUE","feature_id":"wholesale-tier-setup","summary":"Account staff hạn quyền có cấu hình offer Wholesale được không; khi store chạm 25 automatic discount thì tạo offer báo gì?","detail":"Không có account phụ; store 5/25 chưa chạm ngưỡng.","kb_ids":[],"check_ids":[],"supersedes":"OQ-discount-offers-099"}
```

## OQ-wholesale-pricing-023 — OPEN_ISSUE

```json
{"oq_id":"OQ-wholesale-pricing-023","type":"OPEN_ISSUE","feature_id":"wholesale-tier-setup","summary":"Tier continuity (gap) trên store staging hiện tại có còn không được validate như KNOWN_DEFECT KB-WPO-023?","detail":"Run chỉ sửa tier hợp lệ, không thử lại tạo gap; known defect chưa được re-check.","kb_ids":[],"check_ids":[],"supersedes":"OQ-discount-offers-100"}
```

## OQ-wholesale-pricing-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-024","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","summary":"Xác nhận expected cho các hành vi rủi ro cao (tiền/discount, mất dữ liệu, quyền) mới quan sát trên staging 2026-10-18 — hiện chỉ là OBSERVED_CURRENT, chưa có nguồn thẩm quyền, không dùng làm oracle STRONG: KB-WPO-080 (tiền: Max trống ở tier cuối, 42 đơn vị vẫn nhận mức tier cuối. Item vẫn publish theo knowl)","kb_ids":["wholesale-pricing-offer#KB-WPO-080"],"check_ids":[],"supersedes":"OQ-discount-offers-104"}
```

## OQ-wholesale-pricing-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-025","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","summary":"Cần xác định KB đích cho các reference của wholesale-pricing-offer: KB-WPO-057. Chưa có đích duy nhất; các ref được tách khỏi liên kết đang hoạt động, không dùng chúng làm căn cứ kết luận.","supersedes":"OQ-discount-offers-106"}
```

## OQ-wholesale-pricing-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-wholesale-pricing-026","type":"NEEDS_CONFIRMATION","feature_id":"wholesale-tier-setup","summary":"Cần xác định KB đích cho các reference của wholesale-pricing-offer: KB-WPO-076. Chưa có đích duy nhất; các ref được tách khỏi liên kết đang hoạt động, không dùng chúng làm căn cứ kết luận.","supersedes":"OQ-discount-offers-107"}
```
