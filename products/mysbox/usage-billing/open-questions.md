# Open Questions — usage-billing

## OQ-usage-billing-001 — CONFLICT

```json
{"oq_id":"OQ-usage-billing-001","type":"CONFLICT","feature_id":"capacity-limit-enforcement","summary":"Huỷ gói có tự làm toàn bộ box biến mất khỏi store không, hay box chỉ bị unpublish khi shop huỷ plan trong lúc đang vượt capacity của plan Free (và thời điểm là ngay khi huỷ hay sau khi kỳ đã trả kết thúc)?","side_a":"Tài liệu \"Tạo box và vòng đời Draft / Active\" §Câu hỏi thường gặp nêu toàn bộ box biến mất khi gói Free hết quota hoặc gói bị huỷ, không kèm điều kiện vượt capacity.","side_b":"Tài liệu \"Playbook 3: storefront, widget, theme và trang khách\" §Box tự unpublish nêu nguyên nhân là plan bị huỷ khi shop đang vượt capacity Free.","conflict_group":"CONF-plans-billing-06","kb_ids":["capacity-limit-enforcement#KB-004","capacity-limit-enforcement#KB-005"],"check_ids":["capacity-limit-enforcement:CHK-014"],"supersedes":"OQ-plans-billing-005"}
```

## OQ-usage-billing-002 — CONFLICT

```json
{"oq_id":"OQ-usage-billing-002","type":"CONFLICT","feature_id":"daily-usage-charge-and-charge-status","summary":"Tài liệu mâu thuẫn về số loại Charge: hai tài liệu nói Charge có hai loại (Recurring, Usage), playbook billing liệt kê thêm loại One-time. Cần xác nhận danh sách loại Charge và khi nào phát sinh One-time.","side_a":"Tài liệu \"Domain entities\" §Quan hệ giữa các đối tượng và \"Chu kỳ billing, job tạo phí và trạng thái Charge\" §Trạng thái Charge: Charge có hai loại, Recurring (subscription) và Usage (phí box vượt).","side_b":"Tài liệu \"Playbook 4: billing, plan, capacity, mã giảm giá\" §\"Tôi bị tính phí hai lần\": tab Charges của shop có các loại Recurring, Usage và One-time.","conflict_group":"CONF-plans-billing-09","kb_ids":["daily-usage-charge-and-charge-status#KB-006","daily-usage-charge-and-charge-status#KB-074"],"check_ids":["daily-usage-charge-and-charge-status:CHK-018"],"supersedes":"OQ-plans-billing-006"}
```

## OQ-usage-billing-003 — CONFLICT

```json
{"oq_id":"OQ-usage-billing-003","type":"CONFLICT","feature_id":"usage-fee-pricing","summary":"Đổi plan sau khi đã bán box có làm tính lại phí usage không? Tài liệu support nói không tính lại usage cũ, trong khi tài liệu nâng/hạ plan và tài liệu cách tính phí mô tả việc tính lại phí cho phần box dư khi hạ plan (dựa trên mức phí \"nếu không có quota\" ghi lúc bán). Cần PO/dev xác nhận phạm vi của câu \"không tính lại\" (chỉ nâng plan, hay mọi lần đổi plan).","side_a":"Tài liệu \"Playbook 4: billing, plan, capacity, mã giảm giá\" §Số phí usage nhìn sai: mức giá cố định lúc bán box, đổi plan sau không tính lại usage cũ.","side_b":"Tài liệu \"Nâng, hạ, huỷ plan và trang xem trước thay đổi\" §Hạ plan (quota nhỏ hơn): hạ plan khi used ≥ quota mới thì phần dư được tính lại phí theo mức đã ghi lúc bán và gửi ngay; tài liệu \"Cách tính phí box vượt (usage pricing)\" §Mỗi đơn tạo ra gì: phí \"nếu không có quota\" dùng để tính lại khi hạ plan.","conflict_group":"CONF-plans-billing-13","kb_ids":["plan-upgrade-downgrade-cancel#KB-060","plan-upgrade-downgrade-cancel#KB-068","usage-fee-pricing#KB-009"],"check_ids":["plan-upgrade-downgrade-cancel:CHK-021","usage-fee-pricing:CHK-010"],"supersedes":"OQ-plans-billing-015"}
```

## OQ-usage-billing-004 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-004","type":"OPEN_ISSUE","feature_id":"capacity-limit-enforcement","summary":"Một đơn Free mua nhiều box làm used vượt quota (ví dụ còn 1 nhưng mua 3) có được bán và tạo lượt mở cho phần vượt không? — Tài liệu chỉ nêu điều kiện lớn-hơn-hoặc-bằng, không nêu số phận box vượt trong đơn Free.","kb_ids":["capacity-limit-enforcement#KB-002","capacity-limit-enforcement#KB-003"],"supersedes":"OQ-plans-billing-024"}
```

## OQ-usage-billing-005 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-005","type":"OPEN_ISSUE","feature_id":"capacity-limit-enforcement","summary":"Hai \"plan đặc biệt vĩnh viễn\" được miễn điều kiện ẩn widget là plan nào? — Cần để kiểm điều kiện ẩn widget / khối Unbox theo plan.","kb_ids":["capacity-limit-enforcement#KB-009"],"supersedes":"OQ-plans-billing-025"}
```

## OQ-usage-billing-006 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-006","type":"OPEN_ISSUE","feature_id":"capacity-limit-enforcement","summary":"Widget dùng metafield trạng thái shop thế nào (ẩn widget, ẩn nút, hiện thông báo), và hạn chế cờ capacity cũ còn tồn tại có mức nghiêm trọng / trạng thái sửa ra sao? — Tài liệu tự khai chưa xác nhận; không kiểm được hành vi widget theo trạng thái shop.","kb_ids":["capacity-limit-enforcement#KB-007","capacity-limit-enforcement#KB-008"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-026: 2026-10-17: Config storefront có subscription Free và capabilities {over_capacity false, capacity_expires_at 2025-07-30}; widget render. Hành vi khi over_capacity true/hết hạn không quan sát; giá trị lệch merchant (CONF-plans-billing-21).","staging_observation_kb_ids":["capacity-limit-enforcement#KB-046"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-plans-billing-026"}
```

## OQ-usage-billing-007 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-007","type":"OPEN_ISSUE","feature_id":"capacity-limit-enforcement","summary":"Câu chữ, subject của email capacity mẫu Free / Paid; gửi một lần mỗi chu kỳ hay mỗi lần đơn mới vượt; \"vượt vạch\" của mẫu Paid là lúc chạm đúng quota hay box đầu tiên vượt; tên template theo môi trường? — Không có oracle cho nội dung, số lượng và thời điểm email.","kb_ids":["capacity-limit-enforcement#KB-013","capacity-limit-enforcement#KB-016","capacity-limit-enforcement#KB-020","capacity-limit-enforcement#KB-022"],"supersedes":"OQ-plans-billing-027"}
```

## OQ-usage-billing-008 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-008","type":"OPEN_ISSUE","feature_id":"capacity-limit-enforcement","summary":"Merchant (hoặc admin) publish lại box khi shop Free vẫn vượt capacity thì bị chặn với thông báo nào, hay box bị unpublish lại? — Tài liệu chỉ nói box bị gỡ tự động, không nêu hành vi khi cố publish lại.","kb_ids":["capacity-limit-enforcement#KB-018"],"supersedes":"OQ-plans-billing-028"}
```

## OQ-usage-billing-009 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-009","type":"OPEN_ISSUE","feature_id":"capacity-limit-enforcement","summary":"Khách bấm Unbox khi shop vượt capacity thấy lỗi gì? — Không có text lỗi để làm oracle.","kb_ids":["capacity-limit-enforcement#KB-010"],"supersedes":"OQ-plans-billing-029"}
```

## OQ-usage-billing-010 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-010","type":"OPEN_ISSUE","feature_id":"capacity-limit-enforcement","summary":"Shop trả phí có thấy cảnh báo hạn mức và nút Upgrade không; admin nâng capacity used trên plan trả phí có gây unpublish hay phát sinh phí không? — Tài liệu chỉ nêu hệ quả trên plan Free.","kb_ids":["capacity-limit-enforcement#KB-011","capacity-limit-enforcement#KB-021"],"supersedes":"OQ-plans-billing-030"}
```

## OQ-usage-billing-011 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-011","type":"OPEN_ISSUE","feature_id":"capacity-limit-enforcement","summary":"Khi cài lại app, box được khôi phục \"thường đã unpublish\" — trường hợp nào box không bị unpublish, và dữ liệu nào được khôi phục? — Không viết được expected state sau reinstall.","kb_ids":["capacity-limit-enforcement#KB-019","capacity-limit-enforcement#KB-038"],"supersedes":"OQ-plans-billing-031"}
```

## OQ-usage-billing-012 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-012","type":"OPEN_ISSUE","feature_id":"capacity-limit-enforcement","summary":"Hạn mức Free trên production là bao nhiêu và chữ thông báo có đổi theo hạn mức đó không? — Ví dụ dùng số seed 10; boundary chạm trần chưa có oracle.","kb_ids":["capacity-limit-enforcement#KB-030","capacity-limit-enforcement#KB-040","capacity-limit-enforcement#KB-044"],"supersedes":"OQ-plans-billing-032"}
```

## OQ-usage-billing-013 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-013","type":"OPEN_ISSUE","feature_id":"daily-usage-charge-and-charge-status","summary":"Hạn chế đã biết: Usage charge bị kẹt ở trạng thái Pending nếu process chết trước khi Shopify trả lời; tài liệu không nêu cơ chế timeout hay khôi phục.","kb_ids":["daily-usage-charge-and-charge-status#KB-037"],"check_ids":["daily-usage-charge-and-charge-status:CHK-017"],"supersedes":"OQ-plans-billing-033"}
```

## OQ-usage-billing-014 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-014","type":"OPEN_ISSUE","feature_id":"daily-usage-charge-and-charge-status","summary":"Hạn chế đã biết: khi Shopify từ chối usage record, các dòng phí đã ở trạng thái \"completed\" nên job đêm sau không nhặt lại, không có lệnh retry hay cảnh báo — Mysbox mất khoản phí đó.","kb_ids":["daily-usage-charge-and-charge-status#KB-049","daily-usage-charge-and-charge-status#KB-050"],"check_ids":["daily-usage-charge-and-charge-status:CHK-014"],"supersedes":"OQ-plans-billing-034"}
```

## OQ-usage-billing-015 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-015","type":"OPEN_ISSUE","feature_id":"daily-usage-charge-and-charge-status","summary":"Hạn chế đã biết: Mysbox không nhận webhook thay đổi subscription, nên khi merchant huỷ trong Shopify admin hoặc Shopify tự huỷ vì không trả tiền, Mysbox vẫn hiện subscription Active/plan Paid cho tới lần đổi plan hoặc gỡ app kế tiếp.","kb_ids":["daily-usage-charge-and-charge-status#KB-045","daily-usage-charge-and-charge-status#KB-062","daily-usage-charge-and-charge-status#KB-065"],"check_ids":["daily-usage-charge-and-charge-status:CHK-015"],"supersedes":"OQ-plans-billing-035"}
```

## OQ-usage-billing-016 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-016","type":"OPEN_ISSUE","feature_id":"daily-usage-charge-and-charge-status","summary":"Hạn chế đã biết: Mysbox không kiểm tra capped amount trước khi gửi khoản usage sang Shopify, nên khoản vượt cap bị Shopify từ chối.","kb_ids":["daily-usage-charge-and-charge-status#KB-083"],"check_ids":["daily-usage-charge-and-charge-status:CHK-016"],"supersedes":"OQ-plans-billing-036"}
```

## OQ-usage-billing-017 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-017","type":"OPEN_ISSUE","feature_id":"daily-usage-charge-and-charge-status","summary":"\"1 tháng gần nhất\" là tháng lịch hay 30 ngày, tính từ thời điểm chạy job, có bao gồm biên không; dòng phí chưa gửi cũ hơn 1 tháng bị bỏ vĩnh viễn, đổi trạng thái hay hiện ở đâu? — Boundary cho dòng phí sát mốc và rủi ro mất phí âm thầm khi job lỡ nhiều ngày.","kb_ids":["daily-usage-charge-and-charge-status#KB-024"],"supersedes":"OQ-plans-billing-037"}
```

## OQ-usage-billing-018 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-018","type":"OPEN_ISSUE","feature_id":"daily-usage-charge-and-charge-status","summary":"Ngưỡng $0.005 tính theo tiền tệ nào và số tiền usage được làm tròn ra sao? — Ngưỡng đánh dấu Accepted không gọi Shopify là boundary cần test chính xác.","kb_ids":["daily-usage-charge-and-charge-status#KB-013","daily-usage-charge-and-charge-status#KB-014","daily-usage-charge-and-charge-status#KB-040"],"supersedes":"OQ-plans-billing-038"}
```

## OQ-usage-billing-019 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-019","type":"OPEN_ISSUE","feature_id":"daily-usage-charge-and-charge-status","summary":"Danh sách đầy đủ trạng thái của Recurring charge (ngoài Active / Pending / Declined / Cancelled), ví dụ khi Shopify đóng băng shop? — Cần enum đầy đủ để kiểm hiển thị và logic kích hoạt.","kb_ids":["daily-usage-charge-and-charge-status#KB-038","daily-usage-charge-and-charge-status#KB-043"],"supersedes":"OQ-plans-billing-039"}
```

## OQ-usage-billing-020 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-020","type":"OPEN_ISSUE","feature_id":"daily-usage-charge-and-charge-status","summary":"Shop ở gói Free có sinh Charge không, và Recurring charge có tồn tại với gói giá 0 không? — Không có quy tắc tổng quát; ảnh hưởng dữ liệu kỳ vọng trên màn Charges.","kb_ids":["daily-usage-charge-and-charge-status#KB-005","daily-usage-charge-and-charge-status#KB-021"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-040: 2026-10-17: Phía client shop Free không có object/request charge hay recurring nào; bản ghi Charge phía server không quan sát được.","staging_observation_kb_ids":["daily-usage-charge-and-charge-status#KB-087"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-plans-billing-040"}
```

## OQ-usage-billing-021 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-021","type":"OPEN_ISSUE","feature_id":"daily-usage-charge-and-charge-status","summary":"Màn Payment > Charges có những bộ lọc và màn chi tiết nào (ví dụ lọc theo Declined/Failed)? — Chỉ có cột và tab; bộ lọc chỉ được ngụ ý trong ví dụ.","kb_ids":["daily-usage-charge-and-charge-status#KB-054","daily-usage-charge-and-charge-status#KB-070"],"supersedes":"OQ-plans-billing-041"}
```

## OQ-usage-billing-022 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-022","type":"OPEN_ISSUE","feature_id":"usage-fee-pricing","summary":"Phí value-tiered (giá trị × phần trăm / 100) được làm tròn thế nào (cent, nửa cent)? — Oracle chính xác cho từng đơn vị và tổng usage.","kb_ids":["usage-fee-pricing#KB-028"],"supersedes":"OQ-plans-billing-078"}
```

## OQ-usage-billing-023 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-023","type":"OPEN_ISSUE","feature_id":"usage-fee-pricing","summary":"Shop dùng tiền tệ khác USD thì doanh thu dòng hàng quy đổi sang USD thế nào, theo tỉ giá lúc nào; giảm giá mức đơn được chia cho từng đơn vị ra sao? — Quyết định đơn vị nằm trên hay dưới ngưỡng.","kb_ids":["usage-fee-pricing#KB-025"],"supersedes":"OQ-plans-billing-079"}
```

## OQ-usage-billing-024 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-024","type":"OPEN_ISSUE","feature_id":"usage-fee-pricing","summary":"Plan có đồng thời phí mỗi box và bộ tham số value-tiered thì dùng cách tính nào (trường/flag chọn cách tính)? — Tài liệu nói cách tính do plan quyết định nhưng không nêu cơ chế chọn.","kb_ids":["usage-fee-pricing#KB-005","usage-fee-pricing#KB-024"],"supersedes":"OQ-plans-billing-080"}
```

## OQ-usage-billing-025 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-025","type":"OPEN_ISSUE","feature_id":"usage-fee-pricing","summary":"Tiêu chí \"đơn test bị loại\" là gì; đơn preview (tag mysbox-preview-order) có bị tính phí usage không, kể cả trên staging; giá trị mặc định của \"Exclude test order\"? — Cần biết điều kiện để dựng data test cho dòng miễn phí.","kb_ids":["usage-fee-pricing#KB-036","usage-fee-pricing#KB-037","usage-fee-pricing#KB-038"],"supersedes":"OQ-plans-billing-081"}
```

## OQ-usage-billing-026 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-026","type":"OPEN_ISSUE","feature_id":"usage-fee-pricing","summary":"Điều kiện gán cờ \"miễn phí\" cho dòng Usage ngoài trial / plan Free (trong hạn mức, promote code) là gì? — Field được nêu nhưng quy tắc gán chưa đầy đủ.","kb_ids":["usage-fee-pricing#KB-012","usage-fee-pricing#KB-014"],"supersedes":"OQ-plans-billing-082"}
```

## OQ-usage-billing-027 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-027","type":"OPEN_ISSUE","feature_id":"usage-fee-pricing","summary":"Giá trị Capped Amount của từng plan và nơi cấu hình; plan năm (không gửi Capped Amount) thu phí usage thế nào? — Cần để dựng ca chạm cap và hiểu usage của plan năm.","kb_ids":["usage-fee-pricing#KB-034","usage-fee-pricing#KB-035"],"supersedes":"OQ-plans-billing-083"}
```

## OQ-usage-billing-028 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-028","type":"NEEDS_CONFIRMATION","feature_id":"capacity-limit-enforcement","summary":"Tài liệu support playbook nói vượt capacity \"thường\" là gốc khiến cả shop sai nhiều thứ cùng lúc; cần xác nhận cụ thể những hành vi nào bị ảnh hưởng khi shop vượt capacity (box không hiện, đơn không xử lý, dữ liệu cũ).","kb_ids":["capacity-limit-enforcement#KB-028"],"supersedes":"OQ-plans-billing-094"}
```

## OQ-usage-billing-029 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-029","type":"NEEDS_CONFIRMATION","feature_id":"capacity-limit-enforcement","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["capacity-limit-enforcement:CHK-001","capacity-limit-enforcement:CHK-002","capacity-limit-enforcement:CHK-005","capacity-limit-enforcement:CHK-006","capacity-limit-enforcement:CHK-007","capacity-limit-enforcement:CHK-009","capacity-limit-enforcement:CHK-012"],"supersedes":"OQ-plans-billing-095"}
```

## OQ-usage-billing-030 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-030","type":"NEEDS_CONFIRMATION","feature_id":"capacity-limit-enforcement","summary":"Khi shop Free chỉ còn 1 box trong hạn mức mà một đơn mua 3 box, đơn có được bán và tạo lượt mở cho cả 3 box không, used dừng ở giá trị nào, và các box có bị gỡ ngay sau đơn đó không?","check_ids":["capacity-limit-enforcement:CHK-003"],"supersedes":"OQ-plans-billing-096"}
```

## OQ-usage-billing-031 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-031","type":"NEEDS_CONFIRMATION","feature_id":"capacity-limit-enforcement","summary":"Khi shop Free vẫn vượt capacity, merchant (hoặc admin) bấm publish lại một box thì bị chặn với thông báo nào, hay box được publish rồi bị gỡ lại?","check_ids":["capacity-limit-enforcement:CHK-011"],"supersedes":"OQ-plans-billing-097"}
```

## OQ-usage-billing-032 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-032","type":"NEEDS_CONFIRMATION","feature_id":"daily-usage-charge-and-charge-status","summary":"Job tạo phí usage chạy lúc nửa đêm theo giờ server; múi giờ thật của server ở production chưa được xác nhận, nên chưa xác định được đơn paid sát nửa đêm rơi vào lần chạy nào.","kb_ids":["daily-usage-charge-and-charge-status#KB-020"],"check_ids":["daily-usage-charge-and-charge-status:CHK-005"],"supersedes":"OQ-plans-billing-098"}
```

## OQ-usage-billing-033 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-033","type":"NEEDS_CONFIRMATION","feature_id":"daily-usage-charge-and-charge-status","summary":"Với shop bị Shopify đóng băng: shop có thực sự không phát sinh phí usage, và nếu còn phí chưa gửi thì Shopify trả phản hồi gì (tài liệu chỉ suy đoán charge thành Failed, không retry)?","kb_ids":["daily-usage-charge-and-charge-status#KB-059","daily-usage-charge-and-charge-status#KB-060"],"supersedes":"OQ-plans-billing-099"}
```

## OQ-usage-billing-034 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-034","type":"NEEDS_CONFIRMATION","feature_id":"daily-usage-charge-and-charge-status","summary":"Các dòng phí usage chưa gửi tạo trong thời gian ân hạn sau khi huỷ plan có được job tính phí nhặt khi merchant đăng ký lại không? Tài liệu chỉ có suy luận.","kb_ids":["daily-usage-charge-and-charge-status#KB-068"],"supersedes":"OQ-plans-billing-100"}
```

## OQ-usage-billing-035 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-035","type":"NEEDS_CONFIRMATION","feature_id":"daily-usage-charge-and-charge-status","summary":"Tài liệu nói usage bị tính trùng từ phía Mysbox \"gần như không xảy ra\" — cần xác nhận có trường hợp nào (vd chạy tay lệnh tạo phí song song với job) gây tính trùng không.","kb_ids":["daily-usage-charge-and-charge-status#KB-079"],"supersedes":"OQ-plans-billing-101"}
```

## OQ-usage-billing-036 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-036","type":"NEEDS_CONFIRMATION","feature_id":"daily-usage-charge-and-charge-status","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["daily-usage-charge-and-charge-status:CHK-001","daily-usage-charge-and-charge-status:CHK-002","daily-usage-charge-and-charge-status:CHK-003","daily-usage-charge-and-charge-status:CHK-004","daily-usage-charge-and-charge-status:CHK-006","daily-usage-charge-and-charge-status:CHK-007","daily-usage-charge-and-charge-status:CHK-008","daily-usage-charge-and-charge-status:CHK-009","daily-usage-charge-and-charge-status:CHK-010"],"supersedes":"OQ-plans-billing-102"}
```

## OQ-usage-billing-037 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-037","type":"NEEDS_CONFIRMATION","feature_id":"usage-fee-pricing","summary":"Phí mỗi box vượt ở production (count-based) là bao nhiêu? Tài liệu chỉ dùng $0.25/box làm giá trị giả định/minh hoạ và tự khai chưa xác nhận; không dùng làm oracle cho đến khi có bảng plan production.","kb_ids":["usage-fee-pricing#KB-040","usage-fee-pricing#KB-042","usage-fee-pricing#KB-044"],"supersedes":"OQ-plans-billing-127"}
```

## OQ-usage-billing-038 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-038","type":"NEEDS_CONFIRMATION","feature_id":"usage-fee-pricing","summary":"Xác nhận một đơn nhiều variant box có thể vừa có box miễn phí vừa có box bị tính phí (tài liệu diễn đạt dè dặt) và thứ tự trừ quota giữa các dòng (theo thứ tự line item, giá hay thời điểm).","kb_ids":["usage-fee-pricing#KB-016"],"supersedes":"OQ-plans-billing-128"}
```

## OQ-usage-billing-039 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-039","type":"NEEDS_CONFIRMATION","feature_id":"usage-fee-pricing","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["usage-fee-pricing:CHK-001","usage-fee-pricing:CHK-002","usage-fee-pricing:CHK-003","usage-fee-pricing:CHK-004","usage-fee-pricing:CHK-005","usage-fee-pricing:CHK-006","usage-fee-pricing:CHK-007","usage-fee-pricing:CHK-008","usage-fee-pricing:CHK-009","usage-fee-pricing:CHK-011","usage-fee-pricing:CHK-012","usage-fee-pricing:CHK-013"],"supersedes":"OQ-plans-billing-129"}
```

## OQ-usage-billing-040 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-040","type":"NEEDS_CONFIRMATION","feature_id":"usage-fee-pricing","summary":"Shop dùng tiền tệ khác USD thì doanh thu dòng hàng được quy đổi sang USD theo tỉ giá nào, lấy lúc nào; và phí value-tiered (giá trị × phần trăm / 100) được làm tròn thế nào (tới cent, nửa cent, lên hay xuống)?","check_ids":["usage-fee-pricing:CHK-014"],"supersedes":"OQ-plans-billing-130"}
```

## OQ-usage-billing-041 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-041","type":"NEEDS_CONFIRMATION","feature_id":"usage-fee-pricing","summary":"Khi một plan có cả phí mỗi box và bộ tham số value-tiered, hệ thống chọn cách tính nào và dựa trên trường hay cờ nào của plan?","check_ids":["usage-fee-pricing:CHK-015"],"supersedes":"OQ-plans-billing-131"}
```

## OQ-usage-billing-042 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-042","type":"NEEDS_CONFIRMATION","feature_id":"daily-usage-charge-and-charge-status","summary":"Staging: shop Free không có dữ liệu charge/recurring phía client. Phía server, shop Free có bản ghi Charge/Recurring giá 0 nào không, và merchant có màn hình nào trong app để xem lịch sử charge không?","kb_ids":["daily-usage-charge-and-charge-status#KB-087"],"check_ids":["daily-usage-charge-and-charge-status:CHK-019"],"tags":["staging-observed"],"supersedes":"OQ-plans-billing-134"}
```

## OQ-usage-billing-043 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-043","type":"NEEDS_CONFIRMATION","feature_id":"usage-fee-pricing","summary":"Staging: mọi plan trả phí tính phí value-tiered 2% (min $0.25, ngưỡng $12.50), không có phí theo box cố định, cap 10000. Cấu hình production có giống không, và ngưỡng $12.50 có khớp mức min $0.25 / 2% như thiết kế không?","kb_ids":["usage-fee-pricing#KB-060"],"check_ids":["usage-fee-pricing:CHK-017"],"tags":["staging-observed"],"supersedes":"OQ-plans-billing-138"}
```

## OQ-usage-billing-044 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-044","type":"NEEDS_CONFIRMATION","feature_id":"usage-fee-pricing","summary":"Staging (1 lần đọc, giá trị mặc định): công cụ ước tính đề xuất Booster với $489.90/tháng. Công thức ước tính là gì (có dùng đúng phí value-tiered của plan không) để QA kiểm được với giá trị khác mặc định?","kb_ids":["usage-fee-pricing#KB-060"],"check_ids":["usage-fee-pricing:CHK-018"],"tags":["staging-observed"],"supersedes":"OQ-plans-billing-139"}
```

## OQ-usage-billing-045 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-045","type":"OPEN_ISSUE","feature_id":"capacity-limit-enforcement","summary":"Widget dùng capacity_expires_at thế nào khi giá trị đã ở quá khứ nhưng over_capacity false (widget vẫn render)? — KB-046: capacity_expires_at 2025-07-30 đã qua mà widget vẫn hiện; điều kiện 'chu kỳ chưa kết thúc' của KB-009 cần cách đọc giá trị này.","kb_ids":["capacity-limit-enforcement#KB-046","capacity-limit-enforcement#KB-009"],"tags":["staging-observed"],"supersedes":"OQ-plans-billing-141"}
```

## OQ-usage-billing-046 — OPEN_ISSUE

```json
{"oq_id":"OQ-usage-billing-046","type":"OPEN_ISSUE","feature_id":"usage-fee-pricing","summary":"Công cụ \"Estimate your app charge\" tính \"Estimated monthly cost\" và \"Recommended plan\" theo công thức nào (giá plan + phí value-tiered với ngưỡng/min fee)? — Có một mẫu staging ($489.90 với 10 USD × 2000) nhưng không suy được công thức; không có oracle cho công cụ ước tính.","kb_ids":["usage-fee-pricing#KB-060","usage-fee-pricing#KB-039"],"tags":["staging-observed"],"supersedes":"OQ-plans-billing-142"}
```

## OQ-usage-billing-047 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-047","type":"NEEDS_CONFIRMATION","feature_id":"capacity-limit-enforcement","summary":"Quan sát staging mới chạm vùng rủi ro cao (quyền truy cập / tiền / billing): subscription/capabilities render trên trang product (storefront). Item là OBSERVED_CURRENT; cần PO xác nhận đây là hành vi dự kiến trước khi dùng làm expected result.","kb_ids":["capacity-limit-enforcement#KB-046"],"tags":["staging-observed","risk-flag"],"supersedes":"OQ-plans-billing-143"}
```

## OQ-usage-billing-048 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-usage-billing-048","type":"NEEDS_CONFIRMATION","feature_id":"usage-fee-pricing","summary":"Quan sát staging mới chạm vùng rủi ro cao (quyền truy cập / tiền / billing): Cấu hình phí box vượt của các plan trả phí trên staging và công cụ ước tính. Item là OBSERVED_CURRENT; cần PO xác nhận đây là hành vi dự kiến trước khi dùng làm expected result.","kb_ids":["usage-fee-pricing#KB-060"],"tags":["staging-observed","risk-flag"],"supersedes":"OQ-plans-billing-146"}
```
