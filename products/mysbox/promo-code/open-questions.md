# Open Questions — promo-code

## OQ-promo-code-001 — CONFLICT

```json
{"oq_id":"OQ-promo-code-001","type":"CONFLICT","feature_id":"billing-discount-codes","summary":"Merchant nhập mã billing discount ở đâu: portal có hộp nhập mã (trang Pricing, hành động \"Apply discount\") hay mã chỉ áp được qua tham số `code` của yêu cầu lấy đường dẫn duyệt subscription? Ngoài mâu thuẫn giữa các tài liệu, tài liệu billing discount còn tự mâu thuẫn trong cùng một đoạn (nói merchant nhập mã khi chọn plan nhưng tự khai chưa tìm thấy ô nhập mã).","side_a":"Tài liệu \"Plans, Charges, Discounts, Promote codes\" §3. Discounts (giảm giá subscription) và \"Playbook 4: billing, plan, capacity, mã giảm giá\" §Mã giảm giá (discount code) bị từ chối nêu merchant nhập mã trong hộp nhập mã ở portal / trang Pricing; \"Merchant app — tổng quan\" §Màn hình trong menu trái liệt kê hành động \"Apply discount\" trên Pricing.","side_b":"Tài liệu \"Billing discount (mã giảm giá và thêm ngày trial)\" §Cách admin \"gắn\" mã cho shop tự khai chưa xác nhận: không tìm thấy ô nhập mã billing trong portal, chỉ thấy tham số `code` ở server.","conflict_group":"CONF-plans-billing-04","kb_ids":["billing-discount-codes#KB-048","billing-discount-codes#KB-049","billing-discount-codes#KB-050","billing-discount-codes#KB-051"],"check_ids":["billing-discount-codes:CHK-021"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-003 / CONF-plans-billing-04: 2026-10-17: Staging có ô nhập mã trên Pricing: \"Have a discount code?\" → dialog \"Apply discount code\" (textbox, Check, Apply discount). Không submit mã nên đường đi của mã tới tham số code không quan sát.","staging_observation_kb_ids":["billing-discount-codes#KB-067"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-plans-billing-003"}
```

## OQ-promo-code-002 — CONFLICT

```json
{"oq_id":"OQ-promo-code-002","type":"CONFLICT","feature_id":"billing-discount-codes","summary":"Thông điệp lỗi khi dùng billing discount: mỗi điều kiện từ chối có thông điệp riêng (\"Out of discount code\" chỉ cho hết lượt, \"not active\", \"not been applied yet\" / \"expired\", \"has been used\"), hay \"Out of discount code\" được hiển thị cho nhiều điều kiện khác nhau?","side_a":"Tài liệu \"Playbook 4: billing, plan, capacity, mã giảm giá\" §Mã giảm giá (discount code) bị từ chối gán mỗi thông điệp với một nguyên nhân: \"Out of discount code\" là hết lượt; \"not active\" là công tắc Active tắt; \"not been applied yet\" / \"expired\" là ngoài khoảng start/end; \"has been used\" là cặp (shop, plan) đã dùng.","side_b":"Tài liệu \"Billing discount (mã giảm giá và thêm ngày trial)\" §Câu hỏi thường gặp hướng dẫn khi gặp \"Out of discount code\" thì kiểm tra Total amount, Active, ngày hiệu lực, plan trong danh sách và shop đã dùng chưa, tức gắn thông điệp này với nhiều điều kiện.","conflict_group":"CONF-plans-billing-05","kb_ids":["billing-discount-codes#KB-052","billing-discount-codes#KB-053","billing-discount-codes#KB-054","billing-discount-codes#KB-055","billing-discount-codes#KB-056"],"check_ids":["billing-discount-codes:CHK-020"],"supersedes":"OQ-plans-billing-004"}
```

## OQ-promo-code-003 — CONFLICT

```json
{"oq_id":"OQ-promo-code-003","type":"CONFLICT","feature_id":"promote-codes","summary":"Hai tài liệu nói khác nhau về cách lưu Code của promote code: tự chuyển thành chữ HOA khi lưu, hay giữ nguyên như admin gõ. Hệ quả: merchant phải nhập chữ HOA hay nhập đúng như admin đã gõ. Cần dev/PO xác nhận.","side_a":"Tài liệu \"Promote code (mã cộng thêm quota)\" §Ai tạo: Code được tự viết HOA khi lưu, tra cứu khớp tuyệt đối nên merchant phải nhập đúng chữ HOA.","side_b":"Tài liệu \"Plans, Charges, Discounts, Promote codes\" §4. Promote codes (tặng capacity): code phân biệt hoa/thường và được lưu đúng như admin gõ.","conflict_group":"CONF-plans-billing-12","kb_ids":["promote-codes#KB-007","promote-codes#KB-008","promote-codes#KB-009"],"check_ids":["promote-codes:CHK-006"],"supersedes":"OQ-plans-billing-014"}
```

## OQ-promo-code-004 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-004","type":"OPEN_ISSUE","feature_id":"billing-discount-codes","summary":"Promote code và billing discount có áp đồng thời cho cùng một shop/plan được không? — Quy tắc kết hợp không được nêu.","kb_ids":["billing-discount-codes#KB-002","promote-codes#KB-002"],"supersedes":"OQ-plans-billing-016"}
```

## OQ-promo-code-005 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-005","type":"OPEN_ISSUE","feature_id":"billing-discount-codes","summary":"Route/method của yêu cầu lấy đường dẫn duyệt và mã HTTP của phản hồi \"forbidden\"? — Cần cho API-level test và assert phản hồi lỗi.","kb_ids":["billing-discount-codes#KB-028","billing-discount-codes#KB-031"],"supersedes":"OQ-plans-billing-017"}
```

## OQ-promo-code-006 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-006","type":"OPEN_ISSUE","feature_id":"billing-discount-codes","summary":"Khi merchant nhập mã trên plan có discount mang sẵn, discount của plan bị thay thế hay cộng dồn? — Tài liệu chỉ nói discount của plan dùng khi không nhập mã.","kb_ids":["billing-discount-codes#KB-026"],"supersedes":"OQ-plans-billing-018"}
```

## OQ-promo-code-007 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-007","type":"OPEN_ISSUE","feature_id":"billing-discount-codes","summary":"Giới hạn hợp lệ của Value (percentage > 100, amount lớn hơn giá plan, âm), Extra trial days, Intervals âm? — Boundary test form admin và tính giá.","kb_ids":["billing-discount-codes#KB-017","billing-discount-codes#KB-018","billing-discount-codes#KB-020"],"supersedes":"OQ-plans-billing-019"}
```

## OQ-promo-code-008 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-008","type":"OPEN_ISSUE","feature_id":"billing-discount-codes","summary":"Total used tăng chính xác lúc nào ('kích hoạt xong' = merchant duyệt trên Shopify?) và có giảm khi merchant huỷ/không duyệt/subscription bị huỷ không? — Ảnh hưởng đếm lượt và điều kiện 'shop đã dùng mã này trên plan này'.","kb_ids":["billing-discount-codes#KB-038","billing-discount-codes#KB-040"],"supersedes":"OQ-plans-billing-020"}
```

## OQ-promo-code-009 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-009","type":"OPEN_ISSUE","feature_id":"billing-discount-codes","summary":"Mã nhập chữ thường có được chấp nhận không (mã luôn lưu chữ HOA)? — Case merchant nhập mã chữ thường.","kb_ids":["billing-discount-codes#KB-008"],"supersedes":"OQ-plans-billing-021"}
```

## OQ-promo-code-010 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-010","type":"OPEN_ISSUE","feature_id":"billing-discount-codes","summary":"Cơ chế tự áp mã affiliate (giá trị prefix, cờ môi trường, thứ tự ưu tiên giữa dạng mã có REF và dạng ngắn) hoạt động thế nào? — Case tự áp mã affiliate; không có KB item nào mô tả.","supersedes":"OQ-plans-billing-022"}
```

## OQ-promo-code-011 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-011","type":"OPEN_ISSUE","feature_id":"billing-discount-codes","summary":"Quyền trên màn Discounts tách riêng xem/tạo/sửa/xoá hay một quyền cho cả nhóm? — Quyết định số tổ hợp permission cần kiểm.","kb_ids":["billing-discount-codes#KB-058"],"supersedes":"OQ-plans-billing-023"}
```

## OQ-promo-code-012 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-012","type":"OPEN_ISSUE","feature_id":"promote-codes","summary":"Redemption Pending có được tính là 'đã đổi mã này' hoặc 'đang có mã Active khác' không? — Biên khi đổi mã thứ hai lúc đang có redemption Pending.","kb_ids":["promote-codes#KB-050","promote-codes#KB-051","promote-codes#KB-055"],"supersedes":"OQ-plans-billing-070"}
```

## OQ-promo-code-013 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-013","type":"OPEN_ISSUE","feature_id":"promote-codes","summary":"Redemption Pending có hết hạn không, và khi First upgrade chuyển Active thì số chu kỳ được đếm từ thời điểm nào? — Biên thời gian của mã First upgrade có Valid Cycles hữu hạn.","kb_ids":["promote-codes#KB-036","promote-codes#KB-059"],"supersedes":"OQ-plans-billing-071"}
```

## OQ-promo-code-014 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-014","type":"OPEN_ISSUE","feature_id":"promote-codes","summary":"Khi mã bị tắt hoặc xoá, quota thêm có còn được cộng ở chu kỳ mới trước lần đổi plan kế tiếp không? — Hết hạn 'lười' có thể để shop giữ quota thêm; cần expected rõ.","kb_ids":["promote-codes#KB-057","promote-codes#KB-061","promote-codes#KB-063","promote-codes#KB-064"],"supersedes":"OQ-plans-billing-072"}
```

## OQ-promo-code-015 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-015","type":"OPEN_ISSUE","feature_id":"promote-codes","summary":"Validation của Code (độ dài, ký tự cho phép) và hành vi khi tạo trùng mã? — Thiếu biên nhập liệu cho form admin.","kb_ids":["promote-codes#KB-006"],"supersedes":"OQ-plans-billing-073"}
```

## OQ-promo-code-016 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-016","type":"OPEN_ISSUE","feature_id":"promote-codes","summary":"Ràng buộc biên của Valid Cycles và Max Uses ngoài -1 (có cho 0 hay số âm khác không)? — Chỉ Free Boxes Per Cycle có biên '>= 1'.","kb_ids":["promote-codes#KB-014","promote-codes#KB-019"],"supersedes":"OQ-plans-billing-074"}
```

## OQ-promo-code-017 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-017","type":"OPEN_ISSUE","feature_id":"promote-codes","summary":"Starts At / Ends At áp theo múi giờ nào? — Biên cửa sổ đổi mã.","kb_ids":["promote-codes#KB-024"],"supersedes":"OQ-plans-billing-075"}
```

## OQ-promo-code-018 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-018","type":"OPEN_ISSUE","feature_id":"promote-codes","summary":"Công tắc Active của promote code 'có hiệu lực ngay' có áp cả khi chưa bấm Save không (như billing discount)? — Tài liệu chỉ ghi 'có hiệu lực ngay' cho promote code.","kb_ids":["billing-discount-codes#KB-011","promote-codes#KB-026"],"supersedes":"OQ-plans-billing-076"}
```

## OQ-promo-code-019 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-019","type":"OPEN_ISSUE","feature_id":"promote-codes","summary":"Quyền trên màn Promote codes tách riêng xem/tạo/sửa/xoá hay một quyền cho cả nhóm? — Quyết định số tổ hợp permission cần kiểm.","kb_ids":["promote-codes#KB-005"],"supersedes":"OQ-plans-billing-077"}
```

## OQ-promo-code-020 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-020","type":"NEEDS_CONFIRMATION","feature_id":"billing-discount-codes","summary":"Bản ghi billing discount id 1 trên production có đúng là mã extend trial dựng sẵn (+7 ngày, cho mọi shop trừ development store) không; số 7 ngày có cấu hình được không; nếu id 1 là mã khác thì thao tác extend trial hành xử thế nào? Các giá trị hiện có chỉ là của bản ghi seed (seeder không tự chạy).","kb_ids":["billing-discount-codes#KB-044","billing-discount-codes#KB-045","billing-discount-codes#KB-046"],"supersedes":"OQ-plans-billing-084"}
```

## OQ-promo-code-021 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-021","type":"NEEDS_CONFIRMATION","feature_id":"billing-discount-codes","summary":"Tài liệu plan và capacity nêu billing discount \"có thể\" cộng thêm ngày trial mà không nêu điều kiện; cần xác nhận Extra trial days áp thế nào, kể cả với plan không có trial.","kb_ids":["billing-discount-codes#KB-021"],"supersedes":"OQ-plans-billing-085"}
```

## OQ-promo-code-022 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-022","type":"NEEDS_CONFIRMATION","feature_id":"billing-discount-codes","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["billing-discount-codes:CHK-002","billing-discount-codes:CHK-007","billing-discount-codes:CHK-008","billing-discount-codes:CHK-009","billing-discount-codes:CHK-010","billing-discount-codes:CHK-011","billing-discount-codes:CHK-012","billing-discount-codes:CHK-014","billing-discount-codes:CHK-015","billing-discount-codes:CHK-016","billing-discount-codes:CHK-017","billing-discount-codes:CHK-018","billing-discount-codes:CHK-022","billing-discount-codes:CHK-023","billing-discount-codes:CHK-024"],"supersedes":"OQ-plans-billing-086"}
```

## OQ-promo-code-023 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-023","type":"NEEDS_CONFIRMATION","feature_id":"billing-discount-codes","summary":"Khi trường Plans của billing discount để trống, form admin có chặn lưu không, hay mã được lưu nhưng không dùng được cho plan nào?","kb_ids":["billing-discount-codes#KB-009","billing-discount-codes#KB-010","billing-discount-codes#KB-037"],"check_ids":["billing-discount-codes:CHK-004"],"supersedes":"OQ-plans-billing-087"}
```

## OQ-promo-code-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-024","type":"NEEDS_CONFIRMATION","feature_id":"billing-discount-codes","summary":"Bản ghi billing discount id = 1 trên production có đúng là mã extend trial dựng sẵn (cộng 7 ngày, cho mọi shop trừ development store) không; số ngày có cấu hình được không và mã này có bị giới hạn lượt/plan như mã thường?","check_ids":["billing-discount-codes:CHK-013"],"supersedes":"OQ-plans-billing-088"}
```

## OQ-promo-code-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-025","type":"NEEDS_CONFIRMATION","feature_id":"billing-discount-codes","summary":"Total used của billing discount tăng chính xác vào lúc nào, và có giảm lại khi merchant không duyệt, từ chối trên Shopify hoặc huỷ subscription sau đó không? Cặp shop–plan đó có còn bị coi là 'đã dùng mã' không?","check_ids":["billing-discount-codes:CHK-019"],"supersedes":"OQ-plans-billing-089"}
```

## OQ-promo-code-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-026","type":"NEEDS_CONFIRMATION","feature_id":"billing-discount-codes","summary":"Khi merchant nhập billing discount trên plan đã mang sẵn discount, discount của plan bị thay thế hay cộng dồn? Promote code và billing discount có áp đồng thời cho cùng một shop/plan được không?","check_ids":["billing-discount-codes:CHK-025"],"supersedes":"OQ-plans-billing-090"}
```

## OQ-promo-code-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-027","type":"NEEDS_CONFIRMATION","feature_id":"billing-discount-codes","summary":"Giới hạn hợp lệ của Value (percentage trên 100, số âm, amount lớn hơn giá plan), Intervals âm và Extra trial days âm của billing discount là gì, form có chặn không?","check_ids":["billing-discount-codes:CHK-026"],"supersedes":"OQ-plans-billing-091"}
```

## OQ-promo-code-028 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-028","type":"NEEDS_CONFIRMATION","feature_id":"billing-discount-codes","summary":"Billing discount luôn lưu chữ HOA; mã merchant nhập chữ thường có được chuyển HOA rồi chấp nhận không, hay bị từ chối?","check_ids":["billing-discount-codes:CHK-027"],"supersedes":"OQ-plans-billing-092"}
```

## OQ-promo-code-029 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-029","type":"NEEDS_CONFIRMATION","feature_id":"billing-discount-codes","summary":"Quyền trên màn Discounts được tách riêng xem / tạo / sửa / xoá hay là một quyền cho cả nhóm, và tài khoản chỉ có quyền xem có gạt được công tắc Active (vốn có hiệu lực ngay) không?","check_ids":["billing-discount-codes:CHK-028"],"supersedes":"OQ-plans-billing-093"}
```

## OQ-promo-code-030 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-030","type":"NEEDS_CONFIRMATION","feature_id":"promote-codes","summary":"Tài liệu không tìm thấy màn hình nào trong portal để merchant tự nhập promote code và tự ghi chú chưa xác nhận rằng việc đổi mã do support làm hoặc qua giao diện ngoài các repo đã đọc. Cần dev/PO xác nhận kênh/UI thực tế dùng để đổi promote code (quyết định surface và role cho test end-to-end).","kb_ids":["promote-codes#KB-075","promote-codes#KB-076"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-119: 2026-10-17: Không thấy UI hay request promote code nào trong portal staging; kênh thực tế (support/giao diện khác) vẫn cần Dev/PO.","staging_observation_kb_ids":["promote-codes#KB-077"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-plans-billing-119"}
```

## OQ-promo-code-031 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-031","type":"NEEDS_CONFIRMATION","feature_id":"promote-codes","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["promote-codes:CHK-007","promote-codes:CHK-009","promote-codes:CHK-010","promote-codes:CHK-011","promote-codes:CHK-012","promote-codes:CHK-013","promote-codes:CHK-014","promote-codes:CHK-015","promote-codes:CHK-016","promote-codes:CHK-017","promote-codes:CHK-018","promote-codes:CHK-021","promote-codes:CHK-022","promote-codes:CHK-023","promote-codes:CHK-024","promote-codes:CHK-027"],"supersedes":"OQ-plans-billing-120"}
```

## OQ-promo-code-032 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-032","type":"NEEDS_CONFIRMATION","feature_id":"promote-codes","summary":"Route, method, payload và mã HTTP của lời gọi tra cứu và đổi promote code là gì (\"forbidden\" là status 403 hay một field trong body)? Thiếu thông tin này check không chạy lại được.","kb_ids":["promote-codes#KB-039","promote-codes#KB-040"],"check_ids":["promote-codes:CHK-008"],"supersedes":"OQ-plans-billing-121"}
```

## OQ-promo-code-033 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-033","type":"NEEDS_CONFIRMATION","feature_id":"promote-codes","summary":"Cần test case PASS xác nhận khi mã vi phạm nhiều điều kiện, thông điệp trả về là của bước kiểm tra sớm nhất trong thứ tự 7 bước cố định?","kb_ids":["promote-codes#KB-041","promote-codes#KB-042","promote-codes#KB-043"],"check_ids":["promote-codes:CHK-019"],"supersedes":"OQ-plans-billing-122"}
```

## OQ-promo-code-034 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-034","type":"NEEDS_CONFIRMATION","feature_id":"promote-codes","summary":"Redemption ở trạng thái Pending có được tính là shop đã đổi mã đó (bị từ chối \"already redeemed\") hoặc là đang có mã Active khác (bị từ chối \"already has an active promote code\") không?","check_ids":["promote-codes:CHK-020"],"supersedes":"OQ-plans-billing-123"}
```

## OQ-promo-code-035 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-035","type":"NEEDS_CONFIRMATION","feature_id":"promote-codes","summary":"Merchant đổi promote code qua kênh nào: tự nhập trong portal, hay support đổi giúp qua một giao diện khác? Ai là người thực hiện đổi mã và thông điệp từ chối hiển thị cho merchant ở đâu?","check_ids":["promote-codes:CHK-026"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-124: 2026-10-17: Merchant không có chỗ nhập promote code hay thông điệp từ chối trên các màn đã duyệt; ai đổi mã và ở đâu vẫn cần PO.","staging_observation_kb_ids":["promote-codes#KB-077"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-plans-billing-124"}
```

## OQ-promo-code-036 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-036","type":"NEEDS_CONFIRMATION","feature_id":"promote-codes","summary":"Quyền trên màn Promote codes được tách riêng xem / xem chi tiết / tạo / sửa / xoá hay là một quyền cho cả nhóm, và tài khoản thiếu quyền thấy gì khi mở màn này?","check_ids":["promote-codes:CHK-028"],"supersedes":"OQ-plans-billing-125"}
```

## OQ-promo-code-037 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-promo-code-037","type":"NEEDS_CONFIRMATION","feature_id":"promote-codes","summary":"Khi admin sửa số box tặng hoặc số chu kỳ của một promote code đã có lượt đổi đang Active, thay đổi có áp lại cho các lượt đổi hiện có không?","check_ids":["promote-codes:CHK-029"],"supersedes":"OQ-plans-billing-126"}
```

## OQ-promo-code-038 — OPEN_ISSUE

```json
{"oq_id":"OQ-promo-code-038","type":"OPEN_ISSUE","feature_id":"billing-discount-codes","summary":"Nút \"Check\" trong dialog \"Apply discount code\" gọi endpoint nào, trả gì cho mã hợp lệ / bị từ chối, và \"Apply discount\" đưa mã vào luồng chọn plan (tham số code) thế nào? — UI nhập mã đã thấy trên staging (KB-067) nhưng hành vi kiểm/áp mã chưa có quan sát hay oracle.","kb_ids":["billing-discount-codes#KB-067","billing-discount-codes#KB-028","billing-discount-codes#KB-031"],"tags":["staging-observed"],"supersedes":"OQ-plans-billing-140"}
```
