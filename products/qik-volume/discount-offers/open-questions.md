# Open Questions — discount-offers

## OQ-discount-offers-045 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-discount-offers-045","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Khi 2-3 offer type (Quantity Break / Multibuy – Mix & Match Combo / Wholesale Pricing Offer) cùng qualify trên 1 cart (trigger overlap), đúng 1 discount thắng -- xác nhận không bao giờ cả hai, không bao giờ chia -- nhưng biến quyết định offer nào thắng chưa được xác định. Kết quả live-test bị flip giữa 2 lần test trên cùng 1 cặp offer (store test-vl-1, 2026-09-03); test 3-way (2026-09-09) không đủ sạch để trả lời vì Wholesale Tier 1 = 0% ở mức quantity test đó, nên không có 2 discount active cùng lúc thật. Cần PO/Dev xác nhận rule độ ưu tiên (discount rank/order trong Shopify admin? function evaluate sau? thứ tự add-to-cart?) trước khi viết được test case regression xác định cho trigger-overlap.","staging_observation":"Ghi chú quan sát staging 2026-10-18 (OBSERVED_CURRENT, không resolve, giữ NEEDS_CONFIRMATION): = OQ-008: cùng đường add cho cùng kết quả (lặp lại ổn định); khác đường add cho mã khác; có trường hợp 2 mã trên 2 line cùng product. (store staging hiện tại, 2026-10-18)","staging_observation_kb_ids":["_object-level#KB-026","_object-level#KB-027","_object-level#KB-028"]}
```

## OQ-discount-offers-046 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-discount-offers-046","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Doc set nguồn cho object discount-offers trải cả merchant (Portal) và buyer (storefront) surface, không có 1 role duy nhất khai báo ở mức doc-set/object (bootstrap context.role=null, theo thiết kế). Từng claim riêng lẻ có role_stated rõ (merchant cho Portal settings, buyer cho storefront widget) nhưng ở mức object không có 1 role tổng quát -- cần xác nhận đây có phải invariant đúng (object luôn đa-role) hay chỉ là gap của bộ tài liệu nguồn."}
```

## OQ-discount-offers-048 — OPEN_ISSUE

```json
{"oq_id":"OQ-discount-offers-048","type":"OPEN_ISSUE","feature_id":null,"summary":"Quy ước confirmation_source.type cho toàn bộ product qik-volume (áp dụng cho 329 item CONFIRMED_EXPECTED trên cả 8 object, không riêng discount-offers): bộ tài liệu nguồn \"qa-volume-kb\" là KB do chính QA tự biên soạn từ live-test qua Playwright MCP trên store test-vl-1 -- KHÔNG phải tài liệu dev-gen từ source code, KHÔNG phải spec/PRD chính thức, và KHÔNG phải một hệ thống test case có track (không có test-case ID/PASS/build record). Claim không gắn 1 ngày live-test cụ thể (narrative chung) được gán type=\"spec_doc\", và claim gắn 1 ngày live-test cụ thể được gán type=\"test_case\" -- một pragmatic nearest-fit trong 4 giá trị enum cố định của §3, không giá trị nào khớp chữ nghĩa 100%. Hệ quả cần biết: theo §12.5, 192 item \"spec_doc\" (claim không gắn ngày, nguồn yếu hơn) KHÔNG có blocker (a) chặn một dev_doc tương lai ghi đè chúng, trong khi 137 item \"test_case\" (claim gắn ngày live-verify) CÓ. Đây là lựa chọn chấp nhận được cho lần bootstrap đầu (không có lựa chọn nào khớp 100% trong 4 giá trị enum cố định) nhưng cần ghi lại tường minh, không âm thầm hấp thụ. Revisit nếu/khi có Testlane test-case backfill chính thức hoặc spec_doc thật cho product này."}
```

## OQ-discount-offers-053 — CONFLICT

```json
{"oq_id":"OQ-discount-offers-053","type":"CONFLICT","feature_id":null,"summary":"Overlap Quantity Break × Multibuy: tài liệu nói luôn đúng một discount, không bao giờ cả hai/không chia; staging thấy một giỏ (11 đơn vị, add không property) tách 2 line cùng product mang 2 mã khác nhau. Expected là gì? (Không suy quy tắc ưu tiên — topic discount-priority/discount-calculation không supersede.)","side_a":"Base KB-005: đúng một discount thắng, không cả hai, không chia (store test-vl-1).","side_b":"Staging KB-028: line 4 đơn vị mã Multibuy + line 7 đơn vị mã Quantity Break trên cùng product (2/2 lần); các giỏ khác mỗi line một mã, mã thắng tương quan với đường add (KB-026/027).","conflict_group":"CONF-discount-offers-R1018-05","kb_ids":["_object-level#KB-005","_object-level#KB-028"],"check_ids":["multibuy-mix-match-combo:CHK-059","quantity-break:CHK-082","wholesale-pricing-offer:CHK-025"],"related_oq_ids":["OQ-quantity-break-005","OQ-multibuy-014","OQ-multibuy-015","OQ-discount-offers-045"]}
```

## OQ-discount-offers-059 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-discount-offers-059","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Option 'Discount code' trên form Quantity Break/Multibuy staging không bị khoá (chọn được, có field Discount code + Generate), trong khi tài liệu nói chuyển sang discount code phải liên hệ support (Wholesale KB-WPO-007, ticket Multibuy KB-007). Discount code nay là self-serve cho mọi loại offer? (Form Wholesale và việc lưu offer discount code chưa kiểm.)","kb_ids":["_object-level#KB-011","wholesale-pricing-offer#KB-WPO-007","multibuy-mix-match-combo#KB-007"],"check_ids":[],"related_oq_ids":["OQ-multibuy-012"]}
```

## OQ-discount-offers-060 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-discount-offers-060","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Section Combination có dropdown mới 'One per product (best value wins)' (mặc định) / 'Multiple per product' dưới Product discount — tài liệu không nhắc. Ý nghĩa nghiệp vụ và quan hệ với overlap giữa các offer của app? (Chỉ hỏi, không suy quy tắc ưu tiên.)","kb_ids":["_object-level#KB-012"],"check_ids":[],"related_oq_ids":["OQ-quantity-break-005","OQ-discount-offers-045"]}
```

## OQ-discount-offers-061 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-discount-offers-061","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Manage offers staging có filter Status 'Scheduled' và các action 'Rename', 'Ask Sidekick about this offer', 'Deactivate', 'Duplicate' mà tài liệu không nhắc (tài liệu chỉ nêu Running/Expired, không Draft). Đây là phạm vi chính thức cần test?","kb_ids":["_object-level#KB-016"],"check_ids":["quantity-break:CHK-084"]}
```

## OQ-discount-offers-062 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-discount-offers-062","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Trang Create offer staging có thẻ thứ 6 'Product recommendations (Upselling)' (badge Recommended, 'Free to install' — app bên thứ ba). Thẻ này có thuộc phạm vi app (điều kiện hiển thị) không?","kb_ids":["_object-level#KB-009"],"check_ids":[]}
```

## OQ-discount-offers-063 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-discount-offers-063","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Modal 'How's your experience so far?' (xin review) xuất hiện sau khi lưu offer tạo tay thứ 2 (không phải offer AI), không xuất hiện ở offer 1 và 3. Điều kiện kích hoạt expected là gì? (Liên quan object ask-for-review — base nói overlay gắn với offer AI.)","kb_ids":["_object-level#KB-020"],"check_ids":[]}
```

## OQ-discount-offers-064 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-discount-offers-064","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Internal name không hiện trên UI storefront nhưng có trong JSON cấu hình nhúng ở HTML PDP (kèm discount id, lịch của offer Scheduled). Tài liệu nói internal name chỉ merchant thấy — việc lộ qua view-source có chấp nhận được không?","kb_ids":["_object-level#KB-029"],"check_ids":[],"related_oq_ids":["OQ-multibuy-010"]}
```

## OQ-discount-offers-065 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-discount-offers-065","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Known defect chuỗi text thô dưới nút Add to cart (QVD-28) không tái hiện trên staging (theme khác Dawn, product không có swatch). Bug đã được sửa hay chỉ do khác theme/dữ liệu? Cần kiểm lại với product có swatch màu/ảnh.","kb_ids":["_object-level#KB-008","_object-level#KB-030"],"check_ids":["quantity-break:CHK-063","wholesale-pricing-offer:CHK-029"]}
```

## OQ-discount-offers-066 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-discount-offers-066","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Mở form offer MỚI (chưa sửa gì) đã hiện save bar 'Unsaved changes' và chặn điều hướng back/nav (không có modal), Discard không hỏi lại. Đây là hành vi mong muốn?","kb_ids":["_object-level#KB-018"],"check_ids":["quantity-break:CHK-085"]}
```

## OQ-discount-offers-067 — OPEN_ISSUE

```json
{"oq_id":"OQ-discount-offers-067","type":"OPEN_ISSUE","feature_id":null,"summary":"Document iframe app tải từ https://staging-bkv-embedded.qikify.com — host không nằm trong environments.staging.expected_api_base và config không khai host bổ sung. Chờ operator xác nhận host có hợp lệ cho staging (additional_api_hosts) hay không; item giữ LOW, không oracle.","kb_ids":["_object-level#KB-022"],"check_ids":[]}
```

## OQ-discount-offers-068 — OPEN_ISSUE

```json
{"oq_id":"OQ-discount-offers-068","type":"OPEN_ISSUE","feature_id":null,"summary":"POST /api/completions/review trên staging trả 500 với stack trace debug (đường dẫn nội bộ, thư viện vendor) mỗi lần mở form offer (9/9). Ghi nhận như issue staging — không tự escalate; operator quyết có báo dev không.","kb_ids":["_object-level#KB-021"],"check_ids":[]}
```

## OQ-discount-offers-070 — OPEN_ISSUE

```json
{"oq_id":"OQ-discount-offers-070","type":"OPEN_ISSUE","feature_id":null,"summary":"POST /api/events (ghi analytics) từ storefront nhận request guest không thấy header auth, response CORS allow-origin '*'. Khả năng gửi event giả chưa kiểm (ngoài policy). Ghi nhận bề mặt bảo mật — không tự escalate.","kb_ids":["_object-level#KB-024"],"check_ids":[]}
```

## OQ-discount-offers-090 — OPEN_ISSUE

```json
{"oq_id":"OQ-discount-offers-090","type":"OPEN_ISSUE","feature_id":null,"summary":"Gating QVD-167 trên staging chưa quan sát được: khi app embed bị tắt, discount của Quantity Break / Multibuy / Wholesale có còn áp trong cart không (run REFRESH chỉ quan sát với embed Active; tắt embed là theme_change bị cấm, cần operator chủ động tắt/bật).","kb_ids":[],"check_ids":[],"related_oq_ids":["OQ-quantity-break-001","OQ-quantity-break-006"]}
```

## OQ-discount-offers-101 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-discount-offers-101","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Xác nhận expected cho các hành vi rủi ro cao (tiền/discount, mất dữ liệu, quyền) mới quan sát trên staging 2026-10-18 — hiện chỉ là OBSERVED_CURRENT, chưa có nguồn thẩm quyền, không dùng làm oracle STRONG: KB-024 (permission: POST /api/events từ guest không thấy auth, CORS '*'. Item vẫn publish theo kno); KB-026 (tiền / discount-priority: mã thắng theo đường add khi overlap. Item vẫn publish theo knowl); KB-027 (tiền / discount-priority: overlap QB × Wholesale luôn thấy mã QB. Item vẫn publish theo kn)","kb_ids":["_object-level#KB-024","_object-level#KB-026","_object-level#KB-027"],"check_ids":[]}
```
