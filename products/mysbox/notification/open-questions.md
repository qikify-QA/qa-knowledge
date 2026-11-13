# Open Questions — notification

## OQ-notification-001 — CONFLICT

```json
{"oq_id":"OQ-notification-001","type":"CONFLICT","feature_id":"dashboard-notification-banners","summary":"Hai tài liệu ghi khác nhau nhãn của lựa chọn gói Shopify khớp tên gói grow/shopify trong bộ lọc đối tượng banner. Cần dev/PO xác nhận nhãn hiển thị thật để tester chọn đúng đối tượng.","side_a":"Tài liệu \"Banner thông báo trong admin và mọi email/thông báo của app\" §Ai thấy banner: lựa chọn \"Shopify\" khớp tên gói grow và shopify.","side_b":"Tài liệu \"Banner, widget dashboard, Analytic, export, các màn nhỏ khác\" §Notifications (banner dashboard): bộ lọc gói Shopify có các giá trị Basic, Grow, Advanced, Plus, Trial.","conflict_group":"CONF-automation-growth-02","kb_ids":["dashboard-notification-banners#KB-049","dashboard-notification-banners#KB-050"],"check_ids":["dashboard-notification-banners:CHK-010"],"supersedes":"OQ-automation-growth-003"}
```

## OQ-notification-002 — CONFLICT

```json
{"oq_id":"OQ-notification-002","type":"CONFLICT","feature_id":"system-emails-and-notifications","summary":"Email hết dung lượng có được gửi cho shop đã vượt hạn mức từ trước khi shop cài lại app hoặc bị chuyển về Free/hạ gói hay không. Cùng tài liệu banner và email nói hai điều khác nhau; cũng cần rõ hạ gói giữa hai gói trả phí có gửi email không.","side_a":"Tài liệu \"Banner thông báo trong admin và mọi email/thông báo của app\" — bảng email gửi merchant và bảng mọi sự kiện: email được gửi cả khi shop bị chuyển về Free/hạ gói hoặc cài lại app trong lúc đã vượt hạn mức (tài liệu \"Nâng, hạ, huỷ plan và trang xem trước thay đổi\" có ví dụ huỷ rồi cài lại cũng gửi email).","side_b":"Tài liệu \"Banner thông báo trong admin và mọi email/thông báo của app\" — mục câu hỏi thường gặp: email dung lượng chỉ gửi đúng lúc vượt, nên merchant đã vượt hạn mức từ trước không nhận email.","conflict_group":"CONF-automation-growth-10","kb_ids":["system-emails-and-notifications#KB-022","system-emails-and-notifications#KB-023","system-emails-and-notifications#KB-024","system-emails-and-notifications#KB-025","system-emails-and-notifications#KB-026"],"check_ids":["system-emails-and-notifications:CHK-017"],"supersedes":"OQ-automation-growth-011"}
```

## OQ-notification-003 — CONFLICT

```json
{"oq_id":"OQ-notification-003","type":"CONFLICT","feature_id":"system-emails-and-notifications","summary":"Nội dung email hết dung lượng hiện chạy trên production gồm những gì: có link trang giá/link quản lý đơn và tên shop hay vẫn là bản cũ (tên chủ shop, quota, phí usage, không link).","side_a":"Tài liệu \"Banner thông báo trong admin và mọi email/thông báo của app\" — bảng email gửi merchant: email gói Free chứa tên shop, giới hạn box, ngày kết thúc dung lượng, link trang giá; email gói trả phí chứa tên shop, giới hạn, ngày, phí tối thiểu, link quản lý đơn — không gắn thẻ chỉ có trên staging.","side_b":"Tài liệu \"Plan và capacity (quota)\" mục Chạm giới hạn và \"Playbook 4: billing, plan, capacity, mã giảm giá\" mục email capacity reached: nội dung mới có link chỉ có trên nhánh build-staging; production vẫn gửi bản cũ (tên chủ shop, quota, phí usage, không link).","conflict_group":"CONF-automation-growth-11","kb_ids":["system-emails-and-notifications#KB-027","system-emails-and-notifications#KB-028","system-emails-and-notifications#KB-029"],"check_ids":["system-emails-and-notifications:CHK-018"],"supersedes":"OQ-automation-growth-012"}
```

## OQ-notification-004 — CONFLICT

```json
{"oq_id":"OQ-notification-004","type":"CONFLICT","feature_id":"system-emails-and-notifications","summary":"Lưu form Edit shop ở admin panel có đồng bộ shop sang Brevo/CRM khi chỉ đổi trường không nằm trong danh sách theo dõi hay không.","side_a":"Tài liệu \"Màn Shops (danh sách, chi tiết, sửa, action)\" — form Edit: lưu bất kỳ trường nào cũng đồng bộ shop sang công cụ email/CRM.","side_b":"Tài liệu \"Banner thông báo trong admin và mọi email/thông báo của app\" — bảng mọi sự kiện: cập nhật contact Brevo do hồ sơ shop đổi chỉ xảy ra khi một trường được theo dõi thay đổi.","conflict_group":"CONF-automation-growth-12","kb_ids":["system-emails-and-notifications#KB-046","system-emails-and-notifications#KB-047"],"check_ids":["system-emails-and-notifications:CHK-016"],"supersedes":"OQ-automation-growth-013"}
```

## OQ-notification-005 — OPEN_ISSUE

```json
{"oq_id":"OQ-notification-005","type":"OPEN_ISSUE","feature_id":"dashboard-notification-banners","summary":"Màn Upload Image chỉ phục vụ banner hay dùng chung cho mục đích khác của admin panel? — Quyết định giữ capability này trong feature banner hay tách feature riêng.","kb_ids":["dashboard-notification-banners#KB-070"],"supersedes":"OQ-automation-growth-020"}
```

## OQ-notification-006 — OPEN_ISSUE

```json
{"oq_id":"OQ-notification-006","type":"OPEN_ISSUE","feature_id":"system-emails-and-notifications","summary":"'Vượt vạch' của email mẫu trả phí là lúc số box đã dùng chạm đúng quota hay lúc box đầu tiên vượt; email gửi một lần mỗi chu kỳ hay mỗi lần vượt? — Kiểm số lượng và thời điểm email gói trả phí.","kb_ids":["system-emails-and-notifications#KB-016","system-emails-and-notifications#KB-017"],"supersedes":"OQ-automation-growth-044"}
```

## OQ-notification-007 — OPEN_ISSUE

```json
{"oq_id":"OQ-notification-007","type":"OPEN_ISSUE","feature_id":"system-emails-and-notifications","summary":"'Kèm hệ quả: box bị unpublish khỏi storefront' là nội dung email báo trước hay hành vi hệ thống xảy ra cùng lúc gửi email? — Ảnh hưởng expected state của box sau khi chạm hạn mức.","kb_ids":["system-emails-and-notifications#KB-021"],"supersedes":"OQ-automation-growth-045"}
```

## OQ-notification-008 — OPEN_ISSUE

```json
{"oq_id":"OQ-notification-008","type":"OPEN_ISSUE","feature_id":"system-emails-and-notifications","summary":"Khi Mailgun gửi lỗi thì có retry hoặc ghi nhận ở đâu không? — Chỉ có luật bỏ qua im lặng khi thiếu template/email; lỗi gửi chưa được mô tả.","kb_ids":["system-emails-and-notifications#KB-001","system-emails-and-notifications#KB-003"],"supersedes":"OQ-automation-growth-046"}
```

## OQ-notification-009 — OPEN_ISSUE

```json
{"oq_id":"OQ-notification-009","type":"OPEN_ISSUE","feature_id":"system-emails-and-notifications","summary":"Tên template email (capacity reached, reconnect) theo từng môi trường là gì? — Không kiểm được việc gửi email ở từng môi trường nếu không biết template nào đang cấu hình.","kb_ids":["system-emails-and-notifications#KB-002"],"supersedes":"OQ-automation-growth-047"}
```

## OQ-notification-010 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-notification-010","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-notification-banners","summary":"Toàn bộ banner thông báo (thẻ trên Dashboard merchant và màn Notifications ở admin panel) chỉ có trên nhánh build-staging, chưa lên production. Cần PO xác nhận khi nào lên production và hành vi production có giữ nguyên các luật đã mô tả (luật nhập form, điều kiện hiển thị, banner mới nhất thắng, độ trễ sau khi lưu) hay không. Tài liệu cũng chưa nêu trên production đội marketing đăng banner bằng màn nào.","kb_ids":["dashboard-notification-banners#KB-001","dashboard-notification-banners#KB-002","dashboard-notification-banners#KB-003","dashboard-notification-banners#KB-004","dashboard-notification-banners#KB-005","dashboard-notification-banners#KB-006","dashboard-notification-banners#KB-007","dashboard-notification-banners#KB-008","dashboard-notification-banners#KB-009","dashboard-notification-banners#KB-010","dashboard-notification-banners#KB-011","dashboard-notification-banners#KB-012","dashboard-notification-banners#KB-013","dashboard-notification-banners#KB-014","dashboard-notification-banners#KB-015","dashboard-notification-banners#KB-016","dashboard-notification-banners#KB-017","dashboard-notification-banners#KB-018","dashboard-notification-banners#KB-019","dashboard-notification-banners#KB-020","dashboard-notification-banners#KB-021","dashboard-notification-banners#KB-022","dashboard-notification-banners#KB-023","dashboard-notification-banners#KB-024","dashboard-notification-banners#KB-025","dashboard-notification-banners#KB-026","dashboard-notification-banners#KB-027","dashboard-notification-banners#KB-028","dashboard-notification-banners#KB-029","dashboard-notification-banners#KB-030","dashboard-notification-banners#KB-031","dashboard-notification-banners#KB-032","dashboard-notification-banners#KB-033","dashboard-notification-banners#KB-034","dashboard-notification-banners#KB-035","dashboard-notification-banners#KB-036","dashboard-notification-banners#KB-037","dashboard-notification-banners#KB-038","dashboard-notification-banners#KB-039","dashboard-notification-banners#KB-040","dashboard-notification-banners#KB-041","dashboard-notification-banners#KB-042","dashboard-notification-banners#KB-043","dashboard-notification-banners#KB-044","dashboard-notification-banners#KB-045","dashboard-notification-banners#KB-046","dashboard-notification-banners#KB-047","dashboard-notification-banners#KB-048","dashboard-notification-banners#KB-049","dashboard-notification-banners#KB-050","dashboard-notification-banners#KB-051","dashboard-notification-banners#KB-052","dashboard-notification-banners#KB-053","dashboard-notification-banners#KB-054","dashboard-notification-banners#KB-055","dashboard-notification-banners#KB-056","dashboard-notification-banners#KB-057","dashboard-notification-banners#KB-058","dashboard-notification-banners#KB-059","dashboard-notification-banners#KB-060","dashboard-notification-banners#KB-061","dashboard-notification-banners#KB-062","dashboard-notification-banners#KB-063","dashboard-notification-banners#KB-064","dashboard-notification-banners#KB-065","dashboard-notification-banners#KB-066","dashboard-notification-banners#KB-067","dashboard-notification-banners#KB-068","dashboard-notification-banners#KB-069"],"check_ids":["dashboard-notification-banners:CHK-001","dashboard-notification-banners:CHK-002","dashboard-notification-banners:CHK-003","dashboard-notification-banners:CHK-004","dashboard-notification-banners:CHK-005","dashboard-notification-banners:CHK-006","dashboard-notification-banners:CHK-007","dashboard-notification-banners:CHK-008","dashboard-notification-banners:CHK-009","dashboard-notification-banners:CHK-011","dashboard-notification-banners:CHK-012","dashboard-notification-banners:CHK-013","dashboard-notification-banners:CHK-014","dashboard-notification-banners:CHK-015","dashboard-notification-banners:CHK-016","dashboard-notification-banners:CHK-017","dashboard-notification-banners:CHK-018","dashboard-notification-banners:CHK-019","dashboard-notification-banners:CHK-022"],"supersedes":"OQ-automation-growth-053"}
```

## OQ-notification-011 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-notification-011","type":"NEEDS_CONFIRMATION","feature_id":"system-emails-and-notifications","summary":"Nội dung mới của email hết dung lượng (link tới Pricing/Orders, domain, phí tối thiểu và phần trăm phí value-tiered) chỉ có trên nhánh build-staging. Khi nào lên production, và hành vi production hiện tại là gì?","kb_ids":["system-emails-and-notifications#KB-030","system-emails-and-notifications#KB-031","system-emails-and-notifications#KB-032","system-emails-and-notifications#KB-033"],"check_ids":["system-emails-and-notifications:CHK-019"],"supersedes":"OQ-automation-growth-094"}
```

## OQ-notification-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-notification-012","type":"NEEDS_CONFIRMATION","feature_id":"system-emails-and-notifications","summary":"Tài liệu tự khai câu chữ chính xác của template email hết dung lượng (Free và trả phí, bản production và bản mới) chưa được xác nhận; subject, người gửi và ngôn ngữ email cũng chưa được nêu.","kb_ids":["system-emails-and-notifications#KB-029","system-emails-and-notifications#KB-030","system-emails-and-notifications#KB-031","system-emails-and-notifications#KB-033"],"supersedes":"OQ-automation-growth-095"}
```

## OQ-notification-013 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-notification-013","type":"NEEDS_CONFIRMATION","feature_id":"system-emails-and-notifications","summary":"Tác giả chỉ nói không tìm thấy trong code các email chào mừng, hết trial, gỡ app và biên nhận resell. Cần xác nhận app thật sự không gửi các email này.","kb_ids":["system-emails-and-notifications#KB-010","system-emails-and-notifications#KB-011","system-emails-and-notifications#KB-012","system-emails-and-notifications#KB-013"],"check_ids":["system-emails-and-notifications:CHK-026"],"supersedes":"OQ-automation-growth-096"}
```

## OQ-notification-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-notification-014","type":"NEEDS_CONFIRMATION","feature_id":"system-emails-and-notifications","summary":"Phạm vi \"một lần\" của email cấp quyền lại chưa rõ: một tài liệu nói gửi khi cờ cần cấp quyền lại lần đầu được bật, tài liệu khác nói một lần cho mỗi giai đoạn token chết. Nếu cờ bị xoá rồi đặt lại thì email có gửi lại không, và \"gói mở\" gồm những gói nào?","kb_ids":["system-emails-and-notifications#KB-036","system-emails-and-notifications#KB-039","system-emails-and-notifications#KB-040"],"supersedes":"OQ-automation-growth-097"}
```

## OQ-notification-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-notification-015","type":"NEEDS_CONFIRMATION","feature_id":"system-emails-and-notifications","summary":"Công tắc cấu hình nội bộ để tắt thông báo 'order updated' của Shopify khi quà được thêm vào đơn tên là gì, đặt ở đâu và ai được bật?","kb_ids":["system-emails-and-notifications#KB-008"],"check_ids":["system-emails-and-notifications:CHK-011"],"supersedes":"OQ-automation-growth-098"}
```

## OQ-notification-016 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-notification-016","type":"NEEDS_CONFIRMATION","feature_id":"system-emails-and-notifications","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["system-emails-and-notifications:CHK-024"],"supersedes":"OQ-automation-growth-099"}
```
