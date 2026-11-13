# Open Questions — analytics

## OQ-analytics-001 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-001","type":"OPEN_ISSUE","feature_id":"admin-platform-analytics-and-export","summary":"Hạn chế đã biết theo tài liệu (theo dõi như regression watch; cần xác nhận trạng thái sửa và mức ảnh hưởng): nút \"Metric\" trên trang Analytic trỏ tới địa chỉ trống (nút chết).","kb_ids":["admin-platform-analytics-and-export#KB-009"],"check_ids":["admin-platform-analytics-and-export:CHK-006"],"supersedes":"OQ-admin-panel-038"}
```

## OQ-analytics-002 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-002","type":"OPEN_ISSUE","feature_id":"admin-platform-analytics-and-export","summary":"Hạn chế đã biết theo tài liệu (theo dõi như regression watch; cần xác nhận trạng thái sửa và mức ảnh hưởng): hai nhóm báo cáo định nghĩa \"shop thật\" hơi khác nhau (một bên theo cờ test của đơn, một bên theo cờ development của shop), nên số toàn nền tảng (trang Analytic của admin, bảng tính báo cáo) có thể lệch nhỏ, không khớp hoàn toàn với số của merchant.","kb_ids":["admin-platform-analytics-and-export#KB-010"],"check_ids":["admin-platform-analytics-and-export:CHK-007"],"supersedes":"OQ-admin-panel-039"}
```

## OQ-analytics-003 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-003","type":"OPEN_ISSUE","feature_id":"admin-platform-analytics-and-export","summary":"Khoảng ngày của widget App Overview có mặc định/giới hạn không, và chỉ số nào (Total Installs, Active, Free, Paid, Users without Box) phụ thuộc khoảng ngày? — Expected result khi đổi khoảng ngày trên trang Analytic.","kb_ids":["admin-platform-analytics-and-export#KB-003"],"supersedes":"OQ-admin-panel-040"}
```

## OQ-analytics-004 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-004","type":"OPEN_ISSUE","feature_id":"admin-platform-analytics-and-export","summary":"Khoảng ngày của Export áp cho cột nào (chỉ \"số box bán trong khoảng\" hay cả danh sách shop), và export có tôn trọng filter đang chọn trên danh sách Shops không? — Quyết dữ liệu mong đợi trong file khi đổi khoảng ngày/filter.","kb_ids":["admin-platform-analytics-and-export#KB-015","admin-platform-analytics-and-export#KB-017"],"supersedes":"OQ-admin-panel-041"}
```

## OQ-analytics-005 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-005","type":"OPEN_ISSUE","feature_id":"admin-platform-analytics-and-export","summary":"Ghi chú (tên \"shop\") là tên file CSV hay tên thông báo; link tải có hết hạn không? — Expected result của bước tải file export.","kb_ids":["admin-platform-analytics-and-export#KB-014"],"supersedes":"OQ-admin-panel-042"}
```

## OQ-analytics-006 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-006","type":"OPEN_ISSUE","feature_id":"admin-platform-analytics-and-export","summary":"Báo cáo nào bỏ qua shop có plan frozen/cancelled/fraudulent (trang Analytic, export, bảng tính báo cáo)? — Không biết màn hình nào để kiểm ảnh hưởng của trạng thái plan lên số liệu.","supersedes":"OQ-admin-panel-043"}
```

## OQ-analytics-007 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-007","type":"OPEN_ISSUE","feature_id":"admin-platform-analytics-and-export","summary":"Tài liệu không nêu route/endpoint hay bảng dữ liệu nào cho Analytic và Export. — Không kiểm được contract API hay dữ liệu lưu; chỉ kiểm được qua giao diện và file.","supersedes":"OQ-admin-panel-044"}
```

## OQ-analytics-008 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-008","type":"NEEDS_CONFIRMATION","feature_id":"admin-platform-analytics-and-export","summary":"Khi chọn khoảng ngày dài hơn 180 ngày trên trang Analytic của admin panel, hệ thống chặn không cho chọn, tự cắt bớt khoảng ngày hay trả về 0? Khoảng ngày có giá trị mặc định và giới hạn nào, và chỉ số nào của widget App Overview phụ thuộc khoảng ngày?","check_ids":["admin-platform-analytics-and-export:CHK-005"],"supersedes":"OQ-admin-panel-082"}
```

## OQ-analytics-009 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-009","type":"NEEDS_CONFIRMATION","feature_id":"admin-platform-analytics-and-export","summary":"Khoảng ngày khi export danh sách Shops chỉ áp cho cột số box đã bán trong khoảng hay cũng lọc danh sách shop trong file? Export có tôn trọng filter đang chọn trên danh sách Shops không? Ghi chú tên \"shop\" là tên file hay tên thông báo, và link tải có hết hạn không?","check_ids":["admin-platform-analytics-and-export:CHK-011"],"supersedes":"OQ-admin-panel-083"}
```

## OQ-analytics-010 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-010","type":"NEEDS_CONFIRMATION","feature_id":"admin-platform-analytics-and-export","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["admin-platform-analytics-and-export:CHK-012","admin-platform-analytics-and-export:CHK-013"],"supersedes":"OQ-admin-panel-084"}
```

## OQ-analytics-011 — CONFLICT

```json
{"oq_id":"OQ-analytics-011","type":"CONFLICT","feature_id":"dashboard-and-analytics","summary":"Thông báo cho shop gói Free trên màn Analytics được mô tả khác nhau giữa các tài liệu; cần xác nhận chữ hiển thị thực tế.","side_a":"Tài liệu \"Dashboard và analytics\" §Quy tắc làm đổi con số: màn Analytics báo \"Analytics is not available in the Free plan. Upgrade your plan to unlock detailed performance insights and analytics.\"","side_b":"Tài liệu \"Playbook 5: tài khoản, kết nối, gỡ/cài app và tích hợp\" §Trang Analytics ra 0 hoặc số lạ: merchant plan Free thấy banner \"paid plan required\".","conflict_group":"CONF-merchant-app-04","kb_ids":["dashboard-and-analytics#KB-052","dashboard-and-analytics#KB-053"],"check_ids":["dashboard-and-analytics:CHK-025"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-004 / CONF-merchant-app-04: 2026-10-17: Staging gói Free hiện tiêu đề \"Analytics is not available in the Free plan\" + mô tả \"Upgrade your plan to unlock detailed performance insights and analytics.\" + nút \"Upgrade\"; không có \"paid plan required\". Khớp phía KB-052; conflict không tự đóng — orchestrator quyết.","staging_observation_kb_ids":["dashboard-and-analytics#KB-070"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-merchant-app-004"}
```

## OQ-analytics-012 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-012","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Hạn chế đã biết: không có lệnh dựng lại analytics của merchant (vd sau khi job analytics lỗi hoặc đơn trả lúc mất kết nối không được ghi). Cần xác nhận có kế hoạch sửa hay chấp nhận; checklist chỉ dùng làm regression watch.","kb_ids":["dashboard-and-analytics#KB-069"],"check_ids":["dashboard-and-analytics:CHK-035"],"supersedes":"OQ-merchant-app-012"}
```

## OQ-analytics-013 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-013","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Khi chọn khoảng ngày vượt 180 ngày hoặc ngày bắt đầu sớm hơn ngày cài app, server trả lỗi, cắt khoảng, trả 0 hay hiển thị thông báo gì? — Boundary test cần expected result cụ thể cho giá trị vượt giới hạn.","kb_ids":["dashboard-and-analytics#KB-041","dashboard-and-analytics#KB-042","dashboard-and-analytics#KB-067"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-013: 2026-10-17: Picker không chặn khoảng >180 ngày hay ngày trước ngày tạo shop, không báo lỗi; gói Free không phát request nên phản hồi server (lỗi/cắt/0) không quan sát.","staging_observation_kb_ids":["dashboard-and-analytics#KB-075","dashboard-and-analytics#KB-073"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-013"}
```

## OQ-analytics-014 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-014","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Ngưỡng chính xác để hiện \"You almost reach the box limit...\" và \"You have reached the box limit...\", và màu cụ thể của thanh tiến độ? — Tài liệu chỉ nêu thứ tự hai thông điệp và mốc đổi màu 80%.","kb_ids":["dashboard-and-analytics#KB-022","dashboard-and-analytics#KB-023"],"supersedes":"OQ-merchant-app-014"}
```

## OQ-analytics-015 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-015","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Hai con số ở Analytics center trên Dashboard hiển thị gì với gói Free (có hiện \"-\" như bốn thẻ không)? — Quy tắc gói Free chỉ nói bốn thẻ và màn Analytics.","kb_ids":["dashboard-and-analytics#KB-008","dashboard-and-analytics#KB-051"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-015: 2026-10-17: Shop gói Free: hai con số Analytics center hiện \"-\" (như bốn thẻ), giữ \"-\" khi đổi khoảng ngày; không có response API tương ứng.","staging_observation_kb_ids":["dashboard-and-analytics#KB-072"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-015"}
```

## OQ-analytics-016 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-016","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Các khoảng ngày khác ngoài Today (Yesterday, Last week, Month to date, ...) tính theo múi giờ trình duyệt hay múi giờ shop? — Lệch múi giờ làm đổi số liệu.","kb_ids":["dashboard-and-analytics#KB-038","dashboard-and-analytics#KB-039"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-016: 2026-10-17: Ghi được khoảng hiển thị của từng preset (Last week = CN–T7) và hai múi giờ (trình duyệt UTC+7, shop New York); không có request nên không thấy from/to, và cùng ngày lịch nên không phân biệt múi giờ.","staging_observation_kb_ids":["dashboard-and-analytics#KB-074"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-016"}
```

## OQ-analytics-017 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-017","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Huỷ đơn/refund từ Shopify ảnh hưởng thế nào tới doanh thu analytics? — Shard chỉ nói resell không bị trừ; refund/cancel chưa có expected result.","kb_ids":["dashboard-and-analytics#KB-005"],"supersedes":"OQ-merchant-app-017"}
```

## OQ-analytics-018 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-018","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Đơn test được nhận biết thế nào (ngoài cờ test của Shopify và đơn preview)? — Cần dựng data kiểm luật loại đơn test.","kb_ids":["dashboard-and-analytics#KB-001","dashboard-and-analytics#KB-044","dashboard-and-analytics#KB-048"],"supersedes":"OQ-merchant-app-018"}
```

## OQ-analytics-019 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-019","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Endpoint nào portal gọi để lấy số liệu Dashboard/Analytics và tham số test:false nằm ở đâu trong request? — Không có route thì không kiểm được contract API của analytics.","kb_ids":["dashboard-and-analytics#KB-043"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-019: 2026-10-17: Trên gói Free không có endpoint số liệu nào được gọi (Dashboard chỉ GET /api/boxes...order_by=published_at); endpoint analytics và vị trí test:false chưa quan sát.","staging_observation_kb_ids":["dashboard-and-analytics#KB-073"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-019"}
```

## OQ-analytics-020 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-020","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Trạng thái extension trên Dashboard có những giá trị nào ngoài \"Active\"? — Chỉ có \"Active\" trong ví dụ; không suy enum được.","kb_ids":["dashboard-and-analytics#KB-014"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-020: 2026-10-17: Chỉ thấy giá trị hiện tại \"Active\" (Theme extension) và \"Installed\" (5 block); không có response Mysbox chứa enum; giá trị khác chưa quan sát. | 2026-10-17: Giá trị trạng thái extension hiện tại \"Active\" ghi ở install-and-onboarding#KB-064 (bảng App extension status thuộc shard đó); enum đầy đủ không quan sát. | 2026-10-17: Trạng thái hiện tại \"Active\" + 5 block Installed; enum khác không quan sát.","staging_observation_kb_ids":["install-and-onboarding#KB-064","install-and-onboarding#KB-065"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-020"}
```

## OQ-analytics-021 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-021","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Thứ tự khi trùng số lượng trong \"Top selling boxes\", và \"5 box mới nhất\" sắp theo thời điểm tạo nào? — Ảnh hưởng expected result khi kiểm sắp xếp.","kb_ids":["dashboard-and-analytics#KB-010","dashboard-and-analytics#KB-035"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-021: 2026-10-17: \"Recently created\" lấy order_by=published_at (Draft trước, box đã publish theo published_at giảm dần) — mâu thuẫn KB-010, mở CONF-merchant-app-07. Tie-break trong nhóm Draft không ổn định; Top selling boxes khoá trên Free (NOT_COVERED).","staging_observation_kb_ids":["dashboard-and-analytics#KB-076"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-021"}
```

## OQ-analytics-022 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-022","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Thao tác Delete trong \"Recently created mystery boxes\" có hộp xác nhận không và hệ quả gì với box đã bán? — Hành động phá huỷ cần expected result.","kb_ids":["dashboard-and-analytics#KB-016"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-022: 2026-10-17: Delete mở hộp \"Delete box\" / \"Are you sure you want to delete this box?\" (Cancel/Delete), không nhắc đơn đã bán; Delete bật cả với box Active. Hệ quả xoá box đã bán chưa quan sát (không xoá).","staging_observation_kb_ids":["dashboard-and-analytics#KB-078","dashboard-and-analytics#KB-077"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-022"}
```

## OQ-analytics-023 — OPEN_ISSUE

```json
{"oq_id":"OQ-analytics-023","type":"OPEN_ISSUE","feature_id":"dashboard-and-analytics","summary":"Sau khi shop gói Free nâng lên gói trả phí, số liệu đã thu thập trong thời gian Free có hiển thị không? — Dữ liệu vẫn được thu thập khi Free nhưng hành vi hiển thị sau khi nâng gói chưa được mô tả.","kb_ids":["dashboard-and-analytics#KB-054"],"supersedes":"OQ-merchant-app-023"}
```

## OQ-analytics-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-024","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Với gói Free, thông điệp \"You almost reach the box limit...\" và \"You have reached the box limit...\" hiện ở ngưỡng used chính xác nào, và shop gói trả phí có thấy cảnh báo hạn mức cùng nút \"Upgrade\" không?","check_ids":["dashboard-and-analytics:CHK-004"],"supersedes":"OQ-merchant-app-067"}
```

## OQ-analytics-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-025","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["dashboard-and-analytics:CHK-005","dashboard-and-analytics:CHK-006","dashboard-and-analytics:CHK-018","dashboard-and-analytics:CHK-028"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-068: 2026-10-17: CHK-018: không có control Exclude Test Order (cờ shop true). CHK-028 một phần: request không mang shop id do client chọn, xác thực Bearer session token. CHK-005/006 (billing) NOT_COVERED. | 2026-10-17: CHK-018: không có control Exclude Test Order (KB-080). CHK-028 một phần: request merchant không mang shop id do client chọn (request-authentication#KB-016, object integrations). CHK-005/006 (billing) NOT_COVERED.","staging_observation_kb_ids":["dashboard-and-analytics#KB-080","request-authentication#KB-016"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-merchant-app-068"}
```

## OQ-analytics-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-026","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Server giới hạn khoảng ngày analytics tối đa 180 ngày: khi merchant chọn khoảng dài hơn 180 ngày thì server trả lỗi, tự cắt khoảng, hay trả 0, và màn Analytics hiện thông báo gì?","check_ids":["dashboard-and-analytics:CHK-014"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-069: 2026-10-17: Khoảng ~290 ngày: picker không chặn, không thông báo, không request; phản hồi server chưa quan sát.","staging_observation_kb_ids":["dashboard-and-analytics#KB-075","dashboard-and-analytics#KB-073"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-merchant-app-069"}
```

## OQ-analytics-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-027","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Server không cho ngày bắt đầu của khoảng analytics sớm hơn ngày shop cài app: khi merchant chọn ngày sớm hơn thì server báo lỗi, tự dời về ngày cài app, hay trả 0, và màn hình hiện gì?","check_ids":["dashboard-and-analytics:CHK-015"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-070: 2026-10-17: Ngày bắt đầu trước ngày tạo shop: picker không chặn, nhãn \"Jan 01 - Oct 17, 2026\", không request; phản hồi server chưa quan sát.","staging_observation_kb_ids":["dashboard-and-analytics#KB-075"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-merchant-app-070"}
```

## OQ-analytics-028 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-028","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Khi đơn có box bị huỷ hoặc được refund (toàn phần hoặc một phần) từ Shopify, doanh thu, số box và AOV trên analytics có bị trừ đi không?","check_ids":["dashboard-and-analytics:CHK-023"],"supersedes":"OQ-merchant-app-071"}
```

## OQ-analytics-029 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-029","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Shop đang trong thời gian trial của gói trả phí có xem được số liệu analytics không, hay bị chặn như gói Free?","check_ids":["dashboard-and-analytics:CHK-027"],"supersedes":"OQ-merchant-app-072"}
```

## OQ-analytics-030 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-030","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Thao tác Delete box trên Dashboard có hộp xác nhận không, và xoá một box đã có đơn bán thì đơn, quà đã bốc và trang mở box của khách bị ảnh hưởng thế nào?","check_ids":["dashboard-and-analytics:CHK-030"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-073: 2026-10-17: Có hộp xác nhận chung (không nhắc đơn); hệ quả xoá box đã có đơn chưa quan sát (không xoá).","staging_observation_kb_ids":["dashboard-and-analytics#KB-078"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-merchant-app-073"}
```

## OQ-analytics-031 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-031","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Điều kiện để một shop được coi là early-bird (Founding member) là gì và dựng dữ liệu thế nào để kiểm hộp \"Hello, Founding member!\"; shop không phải early-bird có chắc không thấy hộp này không?","kb_ids":["dashboard-and-analytics#KB-020"],"check_ids":["dashboard-and-analytics:CHK-033"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-074: 2026-10-17: Shop Free không early-bird không thấy hộp Founding member; embedded data không có field early-bird. Điều kiện early-bird chưa quan sát.","staging_observation_kb_ids":["dashboard-and-analytics#KB-079"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-merchant-app-074"}
```

## OQ-analytics-032 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-032","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Các khoảng ngày khác \"Today\" (Yesterday, Last week, Last month, Week to date, Month to date, Custom) tính mốc ngày theo múi giờ trình duyệt hay múi giờ shop?","check_ids":["dashboard-and-analytics:CHK-036"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-075: 2026-10-17: Như OQ-merchant-app-016: không có from/to để so; không phân biệt múi giờ.","staging_observation_kb_ids":["dashboard-and-analytics#KB-074"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-merchant-app-075"}
```

## OQ-analytics-033 — CONFLICT

```json
{"oq_id":"OQ-analytics-033","type":"CONFLICT","feature_id":"dashboard-and-analytics","summary":"Tài liệu nói khối \"Recently created mystery boxes\" hiện 5 box mới tạo nhất; trên staging khối gọi /api/boxes?order_by=published_at, box Draft đứng trước và box vừa tạo đang Active không xuất hiện. Expected là sắp theo thời điểm tạo hay theo published_at (và box Active có được hiện không)?","side_a":"Base KB-010 (CE, dev_doc): khối hiển thị 5 box mới tạo nhất.","side_b":"Quan sát staging KB-076: order_by=published_at, published_at null trước, box vừa tạo + Active không vào top 5; thứ tự giữa box null không ổn định.","conflict_group":"CONF-merchant-app-07","kb_ids":["dashboard-and-analytics#KB-010","dashboard-and-analytics#KB-076"],"related_oq_ids":["OQ-analytics-021"],"tags":["staging-observed"],"supersedes":"OQ-merchant-app-107"}
```

## OQ-analytics-034 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-034","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Khối \"Recently created mystery boxes\" phải hiện 5 box mới tạo nhất như tài liệu, hay sắp theo published_at như staging (box Draft đứng trước, box vừa tạo đang Active có thể không vào 5 dòng)? Thứ tự giữa các box Draft có cần ổn định không?","kb_ids":["dashboard-and-analytics#KB-016","dashboard-and-analytics#KB-073","dashboard-and-analytics#KB-077"],"check_ids":["dashboard-and-analytics:CHK-029"],"tags":["staging-observed"],"supersedes":"OQ-merchant-app-108"}
```

## OQ-analytics-035 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-035","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Staging gói Free: hai con số Analytics center hiện \"-\" như bốn thẻ của màn Analytics và portal không gọi API số liệu nào. Đây có phải hành vi mong muốn cho gói Free (chặn ở phía client, không gọi server) không?","kb_ids":["dashboard-and-analytics#KB-072","dashboard-and-analytics#KB-073"],"check_ids":["dashboard-and-analytics:CHK-037"],"tags":["staging-observed"],"supersedes":"OQ-merchant-app-109"}
```

## OQ-analytics-036 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-036","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Trên staging, Last week là Chủ nhật–thứ Bảy và Custom chỉ chọn được bằng cách gõ ngày tay. Tuần bắt đầu từ Chủ nhật có phải quy ước đúng (hay theo locale/cài đặt shop), và Custom bị disable trong combobox có phải thiết kế không?","kb_ids":["dashboard-and-analytics#KB-074"],"check_ids":["dashboard-and-analytics:CHK-038"],"tags":["staging-observed"],"supersedes":"OQ-merchant-app-110"}
```

## OQ-analytics-037 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-037","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Trên staging, Deactivate một box đang Active (đang bán) có hiệu lực ngay, không hỏi xác nhận. Đây có phải thiết kế không, hay cần hộp xác nhận vì thao tác ngừng bán box?","kb_ids":["dashboard-and-analytics#KB-077"],"check_ids":["dashboard-and-analytics:CHK-039"],"tags":["staging-observed"],"supersedes":"OQ-merchant-app-111"}
```

## OQ-analytics-038 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-analytics-038","type":"NEEDS_CONFIRMATION","feature_id":"dashboard-and-analytics","summary":"Quan sát staging mới chạm vùng rủi ro cao (quyền truy cập / tiền / billing): Màn Analytics gói Free: bốn thẻ hiện \"-\", Top selling boxes \"No box found\"; Analytics center trên Dashboard gói Free: hai con số hiện \"-\"; Gói Free: Dashboard và Analytics không gọi endpoint số liệu nào; Delete box trên Dashboard mở hộp xác nhận chung, không nhắc đơn đã bán. Item là OBSERVED_CURRENT; cần PO xác nhận đây là hành vi dự kiến trước khi dùng làm expected result.","kb_ids":["dashboard-and-analytics#KB-071","dashboard-and-analytics#KB-072","dashboard-and-analytics#KB-073","dashboard-and-analytics#KB-078"],"tags":["staging-observed","risk-flag"],"supersedes":"OQ-merchant-app-117"}
```
