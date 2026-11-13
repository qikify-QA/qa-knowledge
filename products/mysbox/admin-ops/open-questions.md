# Open Questions — admin-ops

## OQ-admin-ops-001 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-001","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Bộ tài liệu nguồn không chỉ định role mặc định cho object này (bootstrap-request để role null): các KB item mang scope.role theo vai trò tài liệu nêu cho từng hành vi, hoặc \"unspecified\" khi tài liệu không nêu. Cần PO/Dev xác nhận ma trận role → quyền thực tế trên production (merchant owner/staff, khách, admin Mysbox theo từng role) trước khi dùng các check PERMISSION làm oracle.","supersedes":"OQ-admin-panel-001"}
```

## OQ-admin-ops-002 — CONFLICT

```json
{"oq_id":"OQ-admin-ops-002","type":"CONFLICT","feature_id":"background-jobs-and-queue-monitoring","summary":"Có bao nhiêu lệnh vận hành chỉ có trên nhánh build-staging? Mâu thuẫn nội bộ trong tài liệu job nền: câu hỏi thường gặp nói \"hai lệnh\", bảng lệnh chỉ gắn thẻ chỉ-có-trên-staging cho một lệnh (backfill token hàng đợi của pool refill). Cần dev xác nhận lệnh thứ hai, hoặc \"hai lệnh\" có tính lượt --dry-run và lượt chạy thật của cùng một lệnh hay không.","side_a":"Tài liệu \"Job chạy định kỳ và lệnh vận hành\" §Câu hỏi thường gặp: hai lệnh chỉ có trên staging và dòng lịch kiểm tra nguồn đơn.","side_b":"Tài liệu \"Job chạy định kỳ và lệnh vận hành\" §3. Lệnh artisan: chỉ dòng lệnh backfill token hàng đợi của pool refill mang thẻ chỉ có trên staging.","conflict_group":"CONF-admin-panel-01","kb_ids":["background-jobs-and-queue-monitoring#KB-021","pool-refill#KB-050"],"check_ids":["background-jobs-and-queue-monitoring:CHK-013"],"supersedes":"OQ-admin-panel-003"}
```

## OQ-admin-ops-003 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-003","type":"OPEN_ISSUE","feature_id":null,"summary":"Hạn chế đã biết theo tài liệu (theo dõi như regression watch; cần xác nhận trạng thái sửa và mức ảnh hưởng): sản phẩm không có công cụ dò lại (đối soát) khi các bộ đếm total opened, resell expires, resell processing at, trạng thái đơn hoặc inventory bị lệch.","kb_ids":["_object-level#KB-016"],"check_ids":["admin-box-management:CHK-021","admin-order-inspection-and-retry:CHK-018"],"supersedes":"OQ-admin-panel-004"}
```

## OQ-admin-ops-004 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-004","type":"OPEN_ISSUE","feature_id":"admin-activity-log","summary":"Row action/Retry (không phải CRUD) có được ghi vào Activity log không? — Tài liệu chỉ nói mọi thao tác CRUD; check Activity log cho thao tác retry/sync cần biết phạm vi.","kb_ids":["admin-activity-log#KB-001"],"supersedes":"OQ-admin-panel-005"}
```

## OQ-admin-ops-005 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-005","type":"OPEN_ISSUE","feature_id":"admin-activity-log","summary":"Những thay đổi nào khác trên màn Shops (ngoài Generate recurring payment link), ví dụ sửa capacity hay Security status, được ghi vào Activity log? — Cần để kiểm truy vết thay đổi của nhân viên trên shop.","kb_ids":["admin-activity-log#KB-004"],"supersedes":"OQ-admin-panel-006"}
```

## OQ-admin-ops-006 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-006","type":"OPEN_ISSUE","feature_id":"admin-activity-log","summary":"Role admin nào được xem Activity log? — Thiếu thì không viết được check PERMISSION cho màn Activity.","kb_ids":["admin-activity-log#KB-003"],"supersedes":"OQ-admin-panel-007"}
```

## OQ-admin-ops-007 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-007","type":"OPEN_ISSUE","feature_id":"admin-activity-log","summary":"Tài liệu không nêu route/endpoint hay bảng dữ liệu nào cho Activity log. — Không kiểm được contract API hay dữ liệu lưu.","supersedes":"OQ-admin-panel-008"}
```

## OQ-admin-ops-008 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-008","type":"OPEN_ISSUE","feature_id":"admin-login-and-roles","summary":"Admin host đúng của từng môi trường là gì, và 'host sai' gồm những trường hợp nào? — Cần để dựng check 'chỉ mở trên admin host' và 404 trên host khác.","kb_ids":["admin-login-and-roles#KB-003","admin-login-and-roles#KB-004"],"supersedes":"OQ-admin-panel-018"}
```

## OQ-admin-ops-009 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-009","type":"OPEN_ISSUE","feature_id":"admin-login-and-roles","summary":"Giới hạn 20 lần/phút tính theo IP, tài khoản Slack hay phiên; chạm giới hạn thì thông báo, mã lỗi và thời gian chờ cụ thể là gì? — Có boundary nhưng thiếu expected result khi chạm boundary; không viết được negative check đầy đủ.","kb_ids":["admin-login-and-roles#KB-025"],"supersedes":"OQ-admin-panel-019"}
```

## OQ-admin-ops-010 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-010","type":"OPEN_ISSUE","feature_id":"admin-login-and-roles","summary":"'Một lần tự thử lại' khi lỗi phía Slack do hệ thống tự làm hay người dùng bấm lại? — Quyết định cách dựng case lỗi Slack.","kb_ids":["admin-login-and-roles#KB-019"],"supersedes":"OQ-admin-panel-020"}
```

## OQ-admin-ops-011 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-011","type":"OPEN_ISSUE","feature_id":"admin-login-and-roles","summary":"Cấu hình role và quyền thực tế trên production là gì, và ranh giới quyền giữa các nhóm nhân viên nội bộ (support, support lead, engineer, billing/partnership, marketing) ra sao? — Ma trận role cho check permission của mọi màn admin phụ thuộc cấu hình này; tài liệu chỉ nêu việc từng nhóm làm, không nêu giới hạn quyền.","kb_ids":["admin-login-and-roles#KB-046","admin-login-and-roles#KB-047"],"supersedes":"OQ-admin-panel-021"}
```

## OQ-admin-ops-012 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-012","type":"OPEN_ISSUE","feature_id":"admin-login-and-roles","summary":"Mã định danh thật của từng quyền (ngoài export, advanced_filter, use_paginated_has_overview) là gì; các màn Plans/Discounts/Promote codes/Admin Users/Roles tách quyền xem/tạo/sửa/xoá riêng hay một quyền cho cả nhóm? — Không ánh xạ được sang tick box trên màn Roles và không biết số tổ hợp permission cần kiểm.","kb_ids":["_object-level#KB-013","admin-login-and-roles#KB-048","admin-login-and-roles#KB-049"],"supersedes":"OQ-admin-panel-022"}
```

## OQ-admin-ops-013 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-013","type":"OPEN_ISSUE","feature_id":"admin-login-and-roles","summary":"So khớp email admin user với email Slack có phân biệt hoa thường/khoảng trắng không? — Ảnh hưởng case 'email lệch = not authorized'.","kb_ids":["admin-login-and-roles#KB-015","admin-login-and-roles#KB-022"],"supersedes":"OQ-admin-panel-023"}
```

## OQ-admin-ops-014 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-014","type":"OPEN_ISSUE","feature_id":"admin-login-and-roles","summary":"Sau khi đã gắn Slack id ở lần đầu, nếu đổi email trên dòng admin user thì còn đăng nhập được không? — Luật 'liên kết Slack đã gắn luôn ưu tiên' gợi ý có, nhưng không được nêu rõ.","kb_ids":["admin-login-and-roles#KB-013","admin-login-and-roles#KB-023"],"supersedes":"OQ-admin-panel-024"}
```

## OQ-admin-ops-015 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-015","type":"OPEN_ISSUE","feature_id":"admin-login-and-roles","summary":"Truy cập trực tiếp URL của màn hình/action không có quyền thì nhận gì (403, 404, chuyển hướng)? — Chỉ biết mục không có quyền bị ẩn; thiếu expected result cho truy cập trực tiếp.","kb_ids":["admin-login-and-roles#KB-028"],"supersedes":"OQ-admin-panel-025"}
```

## OQ-admin-ops-016 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-016","type":"OPEN_ISSUE","feature_id":"admin-login-and-roles","summary":"Role nào được vào Horizon và các màn Development tools; admin không có super_admin mở Horizon thì nhận gì? — Cần để viết test phân quyền Horizon/Development tools.","kb_ids":["admin-login-and-roles#KB-045"],"supersedes":"OQ-admin-panel-026"}
```

## OQ-admin-ops-017 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-017","type":"OPEN_ISSUE","feature_id":"admin-login-and-roles","summary":"Xoá admin user có chấm dứt ngay phiên đang đăng nhập của người đó không; phiên kéo dài bao lâu, có logout không? — Xoá dòng = thu hồi quyền, nhưng không rõ thời điểm có hiệu lực với phiên hiện tại.","kb_ids":["admin-login-and-roles#KB-042"],"supersedes":"OQ-admin-panel-027"}
```

## OQ-admin-ops-018 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-018","type":"OPEN_ISSUE","feature_id":"background-jobs-and-queue-monitoring","summary":"Tài liệu job nền nêu: nếu tiến trình scheduler dừng thì mọi job theo lịch dừng im lặng, không có báo hiệu. Đây là hành vi hiện tại đã biết (rủi ro vận hành); có kế hoạch cảnh báo/giám sát không, và QA kiểm như regression watch thế nào?","kb_ids":["background-jobs-and-queue-monitoring#KB-016"],"check_ids":["background-jobs-and-queue-monitoring:CHK-011"],"supersedes":"OQ-admin-panel-055"}
```

## OQ-admin-ops-019 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-019","type":"OPEN_ISSUE","feature_id":"background-jobs-and-queue-monitoring","summary":"Tài liệu job nền nêu hàng đợi kẹt hoặc worker dừng là nguyên nhân phần lớn ticket \"trễ\". Đây là vấn đề vận hành đã biết; có cảnh báo khi worker dừng/queue kẹt không?","kb_ids":["background-jobs-and-queue-monitoring#KB-019"],"check_ids":["background-jobs-and-queue-monitoring:CHK-012"],"supersedes":"OQ-admin-panel-056"}
```

## OQ-admin-ops-020 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-020","type":"OPEN_ISSUE","feature_id":"background-jobs-and-queue-monitoring","summary":"Admin không có role super_admin truy cập /admin/horizon thì nhận gì (ẩn, 403 hay redirect)? Support có super_admin không? — Cần để viết check phân quyền Horizon.","kb_ids":["background-jobs-and-queue-monitoring#KB-003"],"supersedes":"OQ-admin-panel-057"}
```

## OQ-admin-ops-021 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-021","type":"OPEN_ISSUE","feature_id":"background-jobs-and-queue-monitoring","summary":"Khi scheduler đã dừng, Horizon có luôn cho thấy queue trống, không có job lỗi và không có job lịch chạy (như ví dụ minh hoạ) không? — Dấu hiệu chẩn đoán chỉ có trong ví dụ, chưa phải rule.","kb_ids":["background-jobs-and-queue-monitoring#KB-020"],"supersedes":"OQ-admin-panel-058"}
```

## OQ-admin-ops-022 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-022","type":"OPEN_ISSUE","feature_id":"background-jobs-and-queue-monitoring","summary":"Tài liệu không nêu endpoint hay bảng dữ liệu nào cho Horizon/hàng đợi ngoài route /admin/horizon. — Không kiểm được qua API/data layer.","supersedes":"OQ-admin-panel-059"}
```

## OQ-admin-ops-023 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-023","type":"OPEN_ISSUE","feature_id":"portal-release-version-control","summary":"Ô Embedded Version / Customer Portal Resource có ràng buộc định dạng hay validation nào cho giá trị nhập không (rỗng, ký tự đặc biệt)? — Tài liệu chỉ nói là ô chữ lưu version; không có oracle cho input sai.","kb_ids":["portal-release-version-control#KB-003"],"supersedes":"OQ-admin-panel-060"}
```

## OQ-admin-ops-024 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-024","type":"OPEN_ISSUE","feature_id":"portal-release-version-control","summary":"Với từng nguyên nhân trang khách lỗi (chưa đăng nhập + link thiếu danh tính, shop tắt, đơn của khách khác, cache cũ), trang trả 404, trang trắng hay đẩy sang đăng nhập? — Expected result của từng case truy cập trang khách không xác định được.","kb_ids":["portal-release-version-control#KB-011"],"staging_observation":"Ghi chú quan sát staging cho OQ-admin-panel-061: 2026-10-17: Chỉ case khách chưa đăng nhập mở /apps/mysbox/orders không parameters: redirect sang đăng nhập customer account Shopify (không 404/trắng). Request API 401 là do explorer tự dựng. Các case còn lại NOT_OBSERVED.","staging_observation_kb_ids":["portal-release-version-control#KB-012","portal-release-version-control#KB-013"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-admin-panel-061"}
```

## OQ-admin-ops-025 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-025","type":"OPEN_ISSUE","feature_id":"portal-release-version-control","summary":"Tài liệu không nêu route/endpoint hay bảng dữ liệu nào cho Embedded Version / Customer Portal Resource. — Không kiểm được contract API hay dữ liệu lưu.","supersedes":"OQ-admin-panel-062"}
```

## OQ-admin-ops-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-026","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Tài liệu nêu giờ job trong playbook là giờ máy chủ, mặc định UTC, nhưng tự khai runtime production (ai chạy scheduler, múi giờ thực tế) chưa xác nhận. Cần dev/PO xác nhận nơi chạy scheduler và múi giờ thực tế trên production, vì mọi expected result về giờ chạy job (auto-unbox, usage charge hằng ngày, sync quà, nhắc Flow) phụ thuộc vào đó.","kb_ids":["_product-level#KB-PL-028"],"supersedes":"OQ-admin-panel-063"}
```

## OQ-admin-ops-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-027","type":"NEEDS_CONFIRMATION","feature_id":"admin-activity-log","summary":"Activity log có thực sự ghi đăng nhập của nhân viên không? Tài liệu nói cấu hình có bật nhưng tự khai chưa xác nhận và chưa kiểm thử.","kb_ids":["admin-activity-log#KB-005"],"check_ids":["admin-activity-log:CHK-007"],"supersedes":"OQ-admin-panel-064"}
```

## OQ-admin-ops-028 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-028","type":"NEEDS_CONFIRMATION","feature_id":"admin-activity-log","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["admin-activity-log:CHK-003","admin-activity-log:CHK-005","admin-activity-log:CHK-006"],"supersedes":"OQ-admin-panel-065"}
```

## OQ-admin-ops-029 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-029","type":"NEEDS_CONFIRMATION","feature_id":"admin-activity-log","summary":"Một dòng Activity log của thao tác sửa có luôn hiển thị người thực hiện, thời điểm và giá trị cũ, giá trị mới của từng trường đã đổi (như ví dụ sửa selling capacity) không, hay chỉ trong một số trường hợp?","kb_ids":["admin-activity-log#KB-010"],"check_ids":["admin-activity-log:CHK-008"],"supersedes":"OQ-admin-panel-066"}
```

## OQ-admin-ops-030 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-030","type":"NEEDS_CONFIRMATION","feature_id":"admin-activity-log","summary":"Màn Activity log có tìm hoặc lọc được theo shop không, và có lọc theo nhân viên, loại thao tác hay khoảng ngày không? Tài liệu chỉ nhắc việc tìm log theo shop trong một ví dụ minh hoạ.","kb_ids":["admin-activity-log#KB-009"],"check_ids":["admin-activity-log:CHK-009"],"supersedes":"OQ-admin-panel-067"}
```

## OQ-admin-ops-031 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-031","type":"NEEDS_CONFIRMATION","feature_id":"admin-activity-log","summary":"Ngoài tạo/sửa/xoá và tạo payment link, các row action khác trên admin panel (như retry, resync, đổi trạng thái bảo mật của shop) có được ghi vào Activity log không? Nếu có thì là những action nào?","check_ids":["admin-activity-log:CHK-010"],"supersedes":"OQ-admin-panel-068"}
```

## OQ-admin-ops-032 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-032","type":"NEEDS_CONFIRMATION","feature_id":"admin-login-and-roles","summary":"Giới hạn đăng nhập admin theo Slack workspace được bật ở môi trường nào (đặc biệt production)? Tài liệu login tự khai chưa xác nhận; playbook tài khoản thì nêu sai workspace sẽ báo \"Your Slack account is not authorized.\".","kb_ids":["admin-login-and-roles#KB-026"],"check_ids":["admin-login-and-roles:CHK-008"],"supersedes":"OQ-admin-panel-072"}
```

## OQ-admin-ops-033 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-033","type":"NEEDS_CONFIRMATION","feature_id":"admin-login-and-roles","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["admin-login-and-roles:CHK-001","admin-login-and-roles:CHK-003","admin-login-and-roles:CHK-004","admin-login-and-roles:CHK-005","admin-login-and-roles:CHK-006","admin-login-and-roles:CHK-007","admin-login-and-roles:CHK-011","admin-login-and-roles:CHK-012","admin-login-and-roles:CHK-015","admin-login-and-roles:CHK-016","admin-login-and-roles:CHK-017","admin-login-and-roles:CHK-018","admin-login-and-roles:CHK-019"],"supersedes":"OQ-admin-panel-073"}
```

## OQ-admin-ops-034 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-034","type":"NEEDS_CONFIRMATION","feature_id":"admin-login-and-roles","summary":"Đổi quyền của role có hiệu lực ngay khi nhân viên tải lại trang (không cần đăng nhập lại) như một quy tắc chung không, cả khi thêm lẫn khi bỏ quyền?","kb_ids":["admin-login-and-roles#KB-050","admin-login-and-roles#KB-051"],"check_ids":["admin-login-and-roles:CHK-013"],"supersedes":"OQ-admin-panel-074"}
```

## OQ-admin-ops-035 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-035","type":"NEEDS_CONFIRMATION","feature_id":"admin-login-and-roles","summary":"Khi nhân viên thiếu quyền mở trực tiếp URL của một màn hình hoặc action trong admin panel, hệ thống trả gì (403, 404 hay chuyển hướng) và có chặn hoàn toàn dữ liệu không?","check_ids":["admin-login-and-roles:CHK-014"],"supersedes":"OQ-admin-panel-075"}
```

## OQ-admin-ops-036 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-036","type":"NEEDS_CONFIRMATION","feature_id":"background-jobs-and-queue-monitoring","summary":"Tài liệu job nền nói job trên hàng đợi \"thường\" chỉ thử một lần nên job lỗi cần retry thủ công trong Horizon, nhưng không nêu job nào là ngoại lệ có retry tự động và số lần retry. Cần dev xác nhận chính sách retry của từng loại job.","kb_ids":["background-jobs-and-queue-monitoring#KB-008","background-jobs-and-queue-monitoring#KB-009"],"check_ids":["background-jobs-and-queue-monitoring:CHK-007"],"supersedes":"OQ-admin-panel-088"}
```

## OQ-admin-ops-037 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-037","type":"NEEDS_CONFIRMATION","feature_id":"background-jobs-and-queue-monitoring","summary":"Giờ chạy của các job theo lịch được tài liệu ghi theo đồng hồ máy chủ và \"mặc định coi là UTC\", tài liệu tự khai chưa xác nhận múi giờ scheduler trên production. Cần xác nhận múi giờ thực tế của scheduler production.","kb_ids":["background-jobs-and-queue-monitoring#KB-014"],"check_ids":["background-jobs-and-queue-monitoring:CHK-010"],"supersedes":"OQ-admin-panel-089"}
```

## OQ-admin-ops-038 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-038","type":"NEEDS_CONFIRMATION","feature_id":"background-jobs-and-queue-monitoring","summary":"Hai lệnh vận hành và dòng lịch kiểm tra nguồn đơn hiện chỉ có trên nhánh build-staging. Khi nào lên production, và hành vi production hiện tại (không có các phần này) là gì?","kb_ids":["background-jobs-and-queue-monitoring#KB-021"],"supersedes":"OQ-admin-panel-090"}
```

## OQ-admin-ops-039 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-039","type":"NEEDS_CONFIRMATION","feature_id":"background-jobs-and-queue-monitoring","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["background-jobs-and-queue-monitoring:CHK-002"],"supersedes":"OQ-admin-panel-091"}
```

## OQ-admin-ops-040 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-040","type":"NEEDS_CONFIRMATION","feature_id":"portal-release-version-control","summary":"Giá trị Customer Portal Resource gắn với tài nguyên nào của trang khách trên storefront (tên file hay tham số nào thay đổi theo giá trị), để kiểm được trang khách đã tải đúng bản mới sau khi đổi?","kb_ids":["portal-release-version-control#KB-009","portal-release-version-control#KB-010"],"check_ids":["portal-release-version-control:CHK-004"],"staging_observation":"Ghi chú quan sát staging cho OQ-admin-panel-092: 2026-10-17: Asset trang khách staging là mysbox-proxy.js/css tên cố định trên staging-proxy.mysbox.io, không ?v=/version trong HTML; không đối chiếu được với giá trị Customer Portal Resource (admin panel NOT_COVERED). Host ngoài expected_api_base.","staging_observation_kb_ids":["portal-release-version-control#KB-014"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-admin-panel-092"}
```

## OQ-admin-ops-041 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-041","type":"NEEDS_CONFIRMATION","feature_id":"portal-release-version-control","summary":"Khi trang proxy của khách bị cache bản cũ sau release, trang my orders / unbox hiển thị lỗi gì (trang trắng, 404 hay đẩy sang đăng nhập)? Đổi Customer Portal Resource có phải cách khắc phục chuẩn không, hay cần thêm bước xoá cache khác?","check_ids":["portal-release-version-control:CHK-006"],"supersedes":"OQ-admin-panel-093"}
```

## OQ-admin-ops-042 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-042","type":"NEEDS_CONFIRMATION","feature_id":"portal-release-version-control","summary":"Ô Embedded Version và Customer Portal Resource có ràng buộc định dạng nào cho giá trị nhập không? Lưu giá trị rỗng hoặc có ký tự đặc biệt bị chặn hay được chấp nhận, và nếu được chấp nhận thì portal của merchant và trang khách có còn tải được không?","check_ids":["portal-release-version-control:CHK-007"],"supersedes":"OQ-admin-panel-094"}
```

## OQ-admin-ops-043 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-043","type":"NEEDS_CONFIRMATION","feature_id":"portal-release-version-control","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["portal-release-version-control:CHK-008"],"supersedes":"OQ-admin-panel-095"}
```

## OQ-admin-ops-044 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-044","type":"NEEDS_CONFIRMATION","feature_id":"portal-release-version-control","summary":"Staging (1 lần, trang danh sách đơn): khách không có danh tính bị chuyển sang trang đăng nhập Shopify. Trang chi tiết đơn /apps/mysbox/orders/<id> không có parameters hoặc có parameters thiếu thông tin thì phản hồi thế nào, và đây có phải hành vi mong đợi cho mọi trang khách không?","kb_ids":["portal-release-version-control#KB-012"],"check_ids":["portal-release-version-control:CHK-009"],"tags":["staging-observed"],"supersedes":"OQ-admin-panel-096"}
```

## OQ-admin-ops-045 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-045","type":"NEEDS_CONFIRMATION","feature_id":"portal-release-version-control","summary":"Host phục vụ asset trang khách trên staging (nằm ngoài expected_api_base) có phải host hợp lệ của staging không, và production dùng host nào? Trên môi trường có version, Customer Portal Resource đổi phần nào của tham chiếu asset (tên file hay tham số), và thời gian cache mong đợi của asset trang khách là bao lâu?","kb_ids":[],"check_ids":["portal-release-version-control:CHK-010"],"tags":["staging-observed"],"supersedes":"OQ-admin-panel-097"}
```

## OQ-admin-ops-046 — OPEN_ISSUE

```json
{"oq_id":"OQ-admin-ops-046","type":"OPEN_ISSUE","feature_id":"portal-release-version-control","summary":"Host staging-proxy.mysbox.io phục vụ asset trang khách có phải host hợp lệ của staging (ngoài expected_api_base) không, và production dùng host nào? — KB-014 tag host_not_in_expected_api_base; ảnh hưởng việc dùng quan sát này cho check môi trường.","kb_ids":["portal-release-version-control#KB-014"],"tags":["staging-observed"],"supersedes":"OQ-admin-panel-098"}
```

## OQ-admin-ops-047 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-admin-ops-047","type":"NEEDS_CONFIRMATION","feature_id":"portal-release-version-control","summary":"Quan sát staging mới chạm vùng rủi ro cao (quyền truy cập / tiền / billing): Trang khách /apps/mysbox/orders khi không có danh tính; API đơn của trang khách trả 401 khi thiếu danh tính (request tự dựng, không phải app gọi). Item là OBSERVED_CURRENT; cần PO xác nhận đây là hành vi dự kiến trước khi dùng làm expected result.","kb_ids":["portal-release-version-control#KB-012","portal-release-version-control#KB-013"],"tags":["staging-observed","risk-flag"],"supersedes":"OQ-admin-panel-099"}
```
