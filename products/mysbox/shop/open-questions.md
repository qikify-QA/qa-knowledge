# Open Questions — shop

## OQ-shop-001 — CONFLICT

```json
{"oq_id":"OQ-shop-001","type":"CONFLICT","feature_id":"admin-shop-management","summary":"Shop đã gỡ app có hiện trong danh sách Shops của admin panel ở trạng thái mặc định hay không? Mâu thuẫn nội bộ trong tài liệu màn Shops; hai câu chỉ khớp nếu giá trị mặc định của filter Trashed đã lọc bỏ shop đã gỡ, điều tài liệu không nói. Cần xác nhận giá trị mặc định của filter Trashed.","side_a":"Tài liệu \"Màn Shops (danh sách, chi tiết, sửa, action)\" §1. Danh sách: shop đã gỡ app vẫn nằm trong danh sách (dữ liệu được giữ) trừ khi lọc bỏ.","side_b":"Tài liệu \"Màn Shops (danh sách, chi tiết, sửa, action)\" §Câu hỏi thường gặp (cùng tài liệu \"Trạng thái shop và vòng đời\" §3. Gỡ app): shop đã gỡ đang bị filter Trashed ẩn, phải chọn \"with trashed\" mới hiện.","conflict_group":"CONF-admin-panel-02","kb_ids":["admin-shop-management#KB-005","admin-shop-management#KB-006"],"check_ids":["admin-shop-management:CHK-002"],"supersedes":"OQ-admin-panel-002"}
```

## OQ-shop-002 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-002","type":"OPEN_ISSUE","feature_id":"admin-shop-management","summary":"Tên quyền cụ thể cho từng nhóm cột và từng row action/nút (View, Edit, Generate recurring payment link, Sync capacity to metafield, Refresh access token, Retry Handle Order, Export) là gì, và role nào (support, support lead, billing/partnership) giữ quyền nào? — Không dựng được ma trận quyền × role để kiểm.","kb_ids":["admin-shop-management#KB-008","admin-shop-management#KB-010","admin-shop-management#KB-038","admin-shop-management#KB-081"],"supersedes":"OQ-admin-panel-045"}
```

## OQ-shop-003 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-003","type":"OPEN_ISSUE","feature_id":"admin-shop-management","summary":"\"Plan mặc định\" mà shop được đưa về khi tắt cờ development store là plan nào? — Expected state sau khi chuyển dev store thành cửa hàng thật cần plan cụ thể.","kb_ids":["admin-shop-management#KB-076"],"supersedes":"OQ-admin-panel-046"}
```

## OQ-shop-004 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-004","type":"OPEN_ISSUE","feature_id":"admin-shop-management","summary":"Nâng capacity used bằng/vượt selling capacity trên plan trả phí có tác động gì (unpublish, usage fee)? — Chỉ biết hệ quả trên plan Free.","kb_ids":["admin-shop-management#KB-079"],"supersedes":"OQ-admin-panel-047"}
```

## OQ-shop-005 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-005","type":"OPEN_ISSUE","feature_id":"admin-shop-management","summary":"Khi Retry Handle Order không tạo gì (đơn không có box đã publish), UI hiển thị gì (thông báo thành công hay không phản hồi)? — Check cần expected message; tài liệu chỉ nói 'im lặng'.","kb_ids":["admin-shop-management#KB-070"],"supersedes":"OQ-admin-panel-048"}
```

## OQ-shop-006 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-006","type":"OPEN_ISSUE","feature_id":"admin-shop-management","summary":"Những thay đổi nào trên màn Shops được ghi vào Activity log (ví dụ sửa capacity, Security status)? — Cần để kiểm truy vết thay đổi của nhân viên.","kb_ids":["admin-shop-management#KB-036"],"supersedes":"OQ-admin-panel-049"}
```

## OQ-shop-007 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-007","type":"OPEN_ISSUE","feature_id":"admin-shop-management","summary":"Khoảng ngày của dải số trên trang chi tiết tính theo múi giờ nào? — Giá trị 'hôm nay' của Usage Charge/Boxes Sold/Orders phụ thuộc múi giờ.","kb_ids":["admin-shop-management#KB-050","admin-shop-management#KB-051"],"supersedes":"OQ-admin-panel-050"}
```

## OQ-shop-008 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-008","type":"OPEN_ISSUE","feature_id":"admin-shop-management","summary":"Khi Status (Security) tắt, webhook đơn, billing và storefront/reveal của khách bị ảnh hưởng thế nào; enum đầy đủ của Status là gì và Note có bắt buộc không? — Phạm vi chặn và required-ness của Note không được nêu.","kb_ids":["admin-shop-management#KB-084"],"supersedes":"OQ-admin-panel-051"}
```

## OQ-shop-009 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-009","type":"OPEN_ISSUE","feature_id":"admin-shop-management","summary":"Job hằng tuần chuyển token cũ chạy theo chu kỳ/thời điểm nào, và job nền nào làm mới token có thể đua với nút Refresh? — Cần để dựng điều kiện tái hiện đua token và kiểm sự xuất hiện của nút Refresh.","kb_ids":["admin-shop-management#KB-059","admin-shop-management#KB-061"],"supersedes":"OQ-admin-panel-052"}
```

## OQ-shop-010 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-010","type":"OPEN_ISSUE","feature_id":"admin-shop-management","summary":"'Một shop = một dòng' là dòng trong database hay dòng trong danh sách Shops; shop cài lại có tạo dòng mới không? — Ảnh hưởng cách kiểm (DB vs UI) và hành vi reinstall.","kb_ids":["_object-level#KB-011","admin-shop-management#KB-003"],"supersedes":"OQ-admin-panel-053"}
```

## OQ-shop-011 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-011","type":"OPEN_ISSUE","feature_id":"admin-shop-management","summary":"Nút chạy lại webhook ở trang Shop là cho webhook 'order paid' (Retry Handle Order) hay cho webhook khác? — Câu nguồn mơ hồ về đối tượng; ảnh hưởng nơi tester tìm action.","kb_ids":["admin-shop-management#KB-072"],"supersedes":"OQ-admin-panel-054"}
```

## OQ-shop-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-012","type":"NEEDS_CONFIRMATION","feature_id":"admin-shop-management","summary":"Filter \"Valid Shopify plan\" của màn Shops trong admin panel hiện chỉ có trên nhánh build-staging. Khi nào filter này lên production, và trước đó production có cách nào lọc/ẩn shop có plan Shopify cancelled, fraudulent, frozen không?","kb_ids":["admin-shop-management#KB-031"],"check_ids":["admin-shop-management:CHK-008"],"supersedes":"OQ-admin-panel-085"}
```

## OQ-shop-013 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-013","type":"NEEDS_CONFIRMATION","feature_id":"admin-shop-management","summary":"Tài liệu màn Shops nói thay đổi lưu từ form Edit \"có thể\" kích hoạt job nền nhưng không nêu section nào kích hoạt job nào. Cần dev xác nhận ánh xạ section → job nền.","kb_ids":["admin-shop-management#KB-037"],"check_ids":["admin-shop-management:CHK-026"],"supersedes":"OQ-admin-panel-086"}
```

## OQ-shop-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-014","type":"NEEDS_CONFIRMATION","feature_id":"admin-shop-management","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["admin-shop-management:CHK-004","admin-shop-management:CHK-005","admin-shop-management:CHK-006","admin-shop-management:CHK-010","admin-shop-management:CHK-015","admin-shop-management:CHK-016","admin-shop-management:CHK-019","admin-shop-management:CHK-020","admin-shop-management:CHK-021","admin-shop-management:CHK-024","admin-shop-management:CHK-025"],"supersedes":"OQ-admin-panel-087"}
```

## OQ-shop-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-015","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Bộ tài liệu nguồn không chỉ định role mặc định cho object này (bootstrap-request để role null): các KB item mang scope.role theo vai trò tài liệu nêu cho từng hành vi, hoặc \"unspecified\" khi tài liệu không nêu. Cần PO/Dev xác nhận ma trận role → quyền thực tế trên production (merchant owner/staff, khách, admin Mysbox theo từng role) trước khi dùng các check PERMISSION làm oracle.","supersedes":"OQ-merchant-app-001"}
```

## OQ-shop-016 — CONFLICT

```json
{"oq_id":"OQ-shop-016","type":"CONFLICT","feature_id":"account-kill-switch","summary":"Thông điệp portal của merchant khi công tắc tài khoản (Status Security) tắt không thống nhất giữa các tài liệu; cần dev xác nhận chữ thực tế (hoặc điều kiện hiện từng thông điệp) trước khi viết expected result.","side_a":"Tài liệu \"Trạng thái shop và vòng đời\" §1. Công tắc tài khoản: portal hiện banner \"Access to Mysbox is currently restricted\" kèm nút \"Contact support\".","side_b":"Tài liệu \"Màn Shops (danh sách, chi tiết, sửa, action)\" §3. Form Edit và \"Playbook 5: tài khoản, kết nối, gỡ/cài app và tích hợp\": portal hiện \"App is not available yet. Please wait for the app to be ready or try again later.\"","conflict_group":"CONF-merchant-app-02","kb_ids":["account-kill-switch#KB-003","account-kill-switch#KB-004"],"check_ids":["account-kill-switch:CHK-003"],"supersedes":"OQ-merchant-app-002"}
```

## OQ-shop-017 — CONFLICT

```json
{"oq_id":"OQ-shop-017","type":"CONFLICT","feature_id":"account-kill-switch","summary":"Phản hồi API của app nhúng khi công tắc tài khoản tắt được mô tả bằng hai thông điệp khác nhau; cần xác nhận status code và nội dung chính xác.","side_a":"Tài liệu \"Trạng thái shop và vòng đời\" §1. Công tắc tài khoản: mọi API của portal trả 403 \"Your account is not activated. Please contact support.\"","side_b":"Tài liệu \"Màn Shops (danh sách, chi tiết, sửa, action)\" §3. Form Edit và \"Playbook 5: tài khoản, kết nối, gỡ/cài app và tích hợp\": app nhúng trả \"access denied\" cho mọi thao tác.","conflict_group":"CONF-merchant-app-03","kb_ids":["account-kill-switch#KB-005","account-kill-switch#KB-006"],"check_ids":["account-kill-switch:CHK-004"],"supersedes":"OQ-merchant-app-003"}
```

## OQ-shop-018 — CONFLICT

```json
{"oq_id":"OQ-shop-018","type":"CONFLICT","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"Mâu thuẫn về gói hiệu lực của shop ngay sau khi gỡ app: về Free ngay, hay vẫn giữ quyền lợi / bị tính usage của gói trả phí trong thời gian ân hạn đến hết kỳ đã trả. Một số tài liệu nêu cả hai ý trong cùng một câu (gói về Free, gói trả phí vẫn còn hạn đến hết kỳ) nên có thể là hai khái niệm khác nhau (nhãn gói và subscription), nhưng tài liệu không nói rõ. Cần dev/PO xác nhận: hạn mức box, tính năng trả phí và phí usage áp theo gói nào trong thời gian ân hạn; và nếu cài lại trong thời gian ân hạn thì hạn mức nào áp dụng (tài liệu tự khai là chưa xác nhận). Ngày hết hạn của charge (cuối kỳ 30 ngày đã trả) không bị tranh chấp.","side_a":"Tài liệu \"Trạng thái shop và vòng đời\" §3. Gỡ app (uninstall), cùng \"Domain entities\", \"Tích hợp: tổng quan và cách xác thực request\", \"Webhook mà app nhận\" và \"Playbook 5: tài khoản, kết nối, gỡ/cài app và tích hợp\": khi gỡ app, gói của shop về Free.","side_b":"Tài liệu \"Trạng thái shop và vòng đời\" (bảng hạn mức: shop đã huỷ gói trả phí còn tính năng trả phí đến hết kỳ đã trả; §Câu hỏi thường gặp: shop đã gỡ app vẫn có thể bị tính usage vì subscription còn ân hạn), cùng \"Tích hợp: tổng quan và cách xác thực request\" và \"Playbook 5: tài khoản, kết nối, gỡ/cài app và tích hợp\": gói trả phí vẫn còn hạn đến hết kỳ đã trả.","conflict_group":"CONF-plans-billing-01","kb_ids":["plan-upgrade-downgrade-cancel#KB-091","shop-uninstall-reinstall-lifecycle#KB-001","shop-uninstall-reinstall-lifecycle#KB-002","shop-uninstall-reinstall-lifecycle#KB-003"],"check_ids":["shop-uninstall-reinstall-lifecycle:CHK-004","shop-uninstall-reinstall-lifecycle:CHK-005"],"supersedes":"OQ-merchant-app-007"}
```

## OQ-shop-019 — CONFLICT

```json
{"oq_id":"OQ-shop-019","type":"CONFLICT","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"Mâu thuẫn giữa hai tài liệu về lịch kiểm nguồn đơn (order source) của shop sau khi gỡ app: bị huỷ khi nhận thông báo app/uninstalled, hay vẫn còn nguyên trên production (việc huỷ chỉ có trên nhánh build-staging). Cần dev xác nhận hành vi production hiện tại.","side_a":"Tài liệu \"Webhook mà app nhận\" §Topic nào, làm gì: khi nhận app/uninstalled, app huỷ lịch kiểm nguồn đơn của shop.","side_b":"Tài liệu \"Trạng thái shop và vòng đời\" §3. Gỡ app (uninstall): trên production lịch thăm dò nguồn đơn của shop vẫn còn nguyên sau khi gỡ app; việc huỷ lịch chỉ có trên nhánh build-staging.","conflict_group":"CONF-merchant-app-06","kb_ids":["shop-uninstall-reinstall-lifecycle#KB-018","shop-uninstall-reinstall-lifecycle#KB-019"],"check_ids":["shop-uninstall-reinstall-lifecycle:CHK-014","shop-uninstall-reinstall-lifecycle:CHK-015"],"supersedes":"OQ-merchant-app-008"}
```

## OQ-shop-020 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-020","type":"OPEN_ISSUE","feature_id":"account-kill-switch","summary":"Khi công tắc Tắt, storefront (widget, theme block, block Unbox, store credit) có bị ẩn/chặn không ngoài trang reveal, và widget dùng metafield user_status thế nào? — Hiệu ứng lên storefront chưa xác nhận; chưa có expected result cho case kill switch trên storefront.","kb_ids":["account-kill-switch#KB-007","account-kill-switch#KB-015"],"supersedes":"OQ-merchant-app-009"}
```

## OQ-shop-021 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-021","type":"OPEN_ISSUE","feature_id":"account-kill-switch","summary":"Shop trial vừa cài (chưa nhận thông báo shop update chứa tên plan) có bị nhận diện là trial thiếu tỉnh/thành và chặn portal ngay không? — Điều kiện dựa vào plan 'trial' nhưng tên plan Shopify chỉ đến qua thông báo shop update, không phải lúc cài.","kb_ids":["account-kill-switch#KB-012"],"supersedes":"OQ-merchant-app-010"}
```

## OQ-shop-022 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-022","type":"OPEN_ISSUE","feature_id":"account-kill-switch","summary":"Field Status (Security) trong admin có những giá trị hiển thị nào ngoài OFF, và Note có bắt buộc khi đổi Status không? — Chưa có enum hiển thị đầy đủ hay tính bắt buộc của Note.","kb_ids":["account-kill-switch#KB-018","account-kill-switch#KB-019"],"supersedes":"OQ-merchant-app-011"}
```

## OQ-shop-023 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-023","type":"OPEN_ISSUE","feature_id":"gdpr-data-requests","summary":"Hạn chế đã biết: handler cho ba webhook GDPR (customers/data_request, customers/redact, shop/redact) chỉ ghi log, không xuất và không xoá dữ liệu; không có công cụ trích/xoá, phải làm tay trong database. Cần PO/dev xác nhận đây là hành vi chấp nhận hay lỗi cần sửa (nghĩa vụ quyền riêng tư); checklist chỉ dùng làm regression watch.","kb_ids":["gdpr-data-requests#KB-001","gdpr-data-requests#KB-002","gdpr-data-requests#KB-003","gdpr-data-requests#KB-008"],"check_ids":["gdpr-data-requests:CHK-003","gdpr-data-requests:CHK-004","gdpr-data-requests:CHK-005"],"supersedes":"OQ-merchant-app-024"}
```

## OQ-shop-024 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-024","type":"OPEN_ISSUE","feature_id":"gdpr-data-requests","summary":"Khi nhiều bảng không nối khoá tới khách, làm sao xác định đủ dữ liệu của một khách để xuất/xoá? — Không kiểm được tính đầy đủ của việc xuất/xoá.","kb_ids":["gdpr-data-requests#KB-009"],"supersedes":"OQ-merchant-app-025"}
```

## OQ-shop-025 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-025","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Hạn chế đã biết: con số 10 trong chữ thông báo gói Free được gõ cứng, không lấy từ hạn mức thật, nên chữ có thể lệch với hạn mức thật của gói mặc định. Cần xác nhận có sửa không; checklist chỉ dùng làm regression watch.","kb_ids":["install-and-onboarding#KB-057"],"check_ids":["install-and-onboarding:CHK-024"],"supersedes":"OQ-merchant-app-035"}
```

## OQ-shop-026 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-026","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Bấm \"Skip\" và xác nhận có đánh dấu onboarding là xong không, và Dashboard/Setup guide/menu trái hiện gì sau đó? — Xác định trạng thái sau khi bỏ qua wizard.","kb_ids":["install-and-onboarding#KB-039","install-and-onboarding#KB-040"],"supersedes":"OQ-merchant-app-036"}
```

## OQ-shop-027 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-027","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Onboarding kết thúc khi nào (tạo box đầu tiên hay hoàn tất màn kết) để menu trái hiện đủ màn hình? — Check chuyển trạng thái menu trái cần trigger chính xác.","kb_ids":["_object-level#KB-007","install-and-onboarding#KB-007"],"supersedes":"OQ-merchant-app-037"}
```

## OQ-shop-028 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-028","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Tên và nội dung 4 bước onboarding là gì, khi bảng wizard có các bước 1, 2, 2b, 3 và màn kết? — Checklist cần số bước và tên bước thống nhất.","kb_ids":["install-and-onboarding#KB-006","install-and-onboarding#KB-032"],"supersedes":"OQ-merchant-app-038"}
```

## OQ-shop-029 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-029","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Sau khi lưu box lần đầu (shop đã có box), nếu merchant tải lại trang ở bước Launch thì wizard còn hiện hay chuyển sang Dashboard? — Hai quy tắc (lưu lần đầu sang bước 3; wizard chỉ hiện khi chưa có box) giao nhau ở biên này.","kb_ids":["install-and-onboarding#KB-033","install-and-onboarding#KB-041"],"supersedes":"OQ-merchant-app-039"}
```

## OQ-shop-030 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-030","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Lựa chọn Physical/Digital ở bước 1 có ánh xạ chính thức với thẻ \"Sealed box\"/\"Instantly opening box\" không, và ảnh hưởng thế nào tới box tạo ở bước 2b? — Tài liệu đặt hai cặp tên cạnh nhau nhưng không phát biểu ánh xạ.","kb_ids":["install-and-onboarding#KB-028","install-and-onboarding#KB-029"],"supersedes":"OQ-merchant-app-040"}
```

## OQ-shop-031 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-031","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Danh sách đầy đủ các trường của bản ghi shop lấy từ Shopify lúc cài, có gồm múi giờ không? — Mục tiêu feature kỳ vọng dữ liệu shop (tên, tiền tệ, múi giờ) lấy đúng; danh sách trường lúc cài được ghi là không đầy đủ và không nêu múi giờ.","kb_ids":["install-and-onboarding#KB-021","install-and-onboarding#KB-063"],"supersedes":"OQ-merchant-app-041"}
```

## OQ-shop-032 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-032","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Chuỗi topic chính xác của các webhook đăng ký lúc cài và tên của 3 webhook quyền riêng tư bắt buộc? — Tester cần topic để đối chiếu đăng ký webhook sau khi cài.","kb_ids":["install-and-onboarding#KB-024","install-and-onboarding#KB-025"],"supersedes":"OQ-merchant-app-042"}
```

## OQ-shop-033 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-033","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Dashboard phát hiện app embed/block đã cài như thế nào và hiển thị gì khi chưa cài? — Expected result cho trạng thái setup trên Dashboard.","kb_ids":["install-and-onboarding#KB-048","install-and-onboarding#KB-053"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-043: 2026-10-17: Trạng thái đọc qua Admin GraphQL (file theme settings_data.json/templates/product.json, checkoutProfiles) và 3 cờ localStorage, không qua backend Mysbox; chỉ thấy trạng thái đã cài — hiển thị khi chưa cài chưa quan sát.","staging_observation_kb_ids":["install-and-onboarding#KB-064","install-and-onboarding#KB-065","install-and-onboarding#KB-066"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-043"}
```

## OQ-shop-034 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-034","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Mục \"Set up your first mystery box\" có tính box ở trạng thái nháp/không Active không? — Biên của điều kiện hoàn thành Setup guide (\"box bất kỳ\").","kb_ids":["install-and-onboarding#KB-050"],"supersedes":"OQ-merchant-app-044"}
```

## OQ-shop-035 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-035","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Ẩn thẻ Setup guide 30 ngày tính theo shop hay chỉ theo trình duyệt, và có cách hiện lại sớm hơn không? — Biên thời gian và phạm vi ẩn của thẻ.","kb_ids":["install-and-onboarding#KB-052"],"staging_observation":"Ghi chú quan sát staging cho OQ-merchant-app-046: 2026-10-17: Không thấy control mở lại thẻ trên Dashboard; thu gọn không lưu gì và localStorage không có key dismiss. Không bấm \"x\" nên nơi lưu/thời hạn ẩn chưa quan sát.","staging_observation_kb_ids":["install-and-onboarding#KB-067"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-merchant-app-046"}
```

## OQ-shop-036 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-036","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"App trừ tồn kho món thưởng của sealed box bằng cơ chế nào khi quyền Inventory/fulfillment orders chỉ là quyền đọc? — Mục đích trừ tồn kho không khớp với quyền đọc; tester cần cơ chế thật.","kb_ids":["install-and-onboarding#KB-019"],"supersedes":"OQ-merchant-app-047"}
```

## OQ-shop-037 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-037","type":"OPEN_ISSUE","feature_id":"install-and-onboarding","summary":"Khi merchant từ chối màn hình xin quyền của Shopify lúc cài thì điều gì xảy ra? — Luồng lỗi của cài đặt chưa có expected result.","kb_ids":["install-and-onboarding#KB-002"],"supersedes":"OQ-merchant-app-048"}
```

## OQ-shop-038 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-038","type":"OPEN_ISSUE","feature_id":"shop-connection-and-reauth","summary":"Lỗi đã biết: bấm \"Refresh access token\" trong admin nhiều lần, hoặc thao tác này chạy đua với job nền làm mới token, khiến một bên bị lỗi (tài liệu gọi là vô hại vì khoá làm mới chỉ dùng một lần). Cần xác nhận có fix/kế hoạch không, và trạng thái cờ cần cấp quyền lại sau khi một bên lỗi.","kb_ids":["shop-connection-and-reauth#KB-033"],"check_ids":["shop-connection-and-reauth:CHK-026"],"supersedes":"OQ-merchant-app-049"}
```

## OQ-shop-039 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-039","type":"OPEN_ISSUE","feature_id":"shop-connection-and-reauth","summary":"Nội dung, tiêu đề và tên template theo môi trường của email \"reconnect the app\"; email có gửi lại nếu cờ bị xoá rồi đặt lại không? — Không có oracle cho email và không kiểm được việc gửi ở staging/production.","kb_ids":["shop-connection-and-reauth#KB-020","shop-connection-and-reauth#KB-021"],"supersedes":"OQ-merchant-app-050"}
```

## OQ-shop-040 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-040","type":"OPEN_ISSUE","feature_id":"shop-connection-and-reauth","summary":"Merchant từ chối màn xin quyền của Shopify lúc cài thì hệ thống làm gì? — Luồng lỗi của cài đặt chưa có expected result.","kb_ids":["shop-connection-and-reauth#KB-037"],"supersedes":"OQ-merchant-app-051"}
```

## OQ-shop-041 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-041","type":"OPEN_ISSUE","feature_id":"shop-connection-and-reauth","summary":"Trong 10 ngày gia hạn token lỗi trước khi phải cấp quyền lại, merchant có thấy thông báo gì không? — Ảnh hưởng trải nghiệm re-auth và test luồng token hết hạn.","kb_ids":["shop-connection-and-reauth#KB-008"],"supersedes":"OQ-merchant-app-052"}
```

## OQ-shop-042 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-042","type":"OPEN_ISSUE","feature_id":"shop-connection-and-reauth","summary":"'Shop không liên lạc được nhiều tuần' là bao lâu, và cờ cần cấp quyền lại được đặt đúng lúc nào? — Không có boundary để dựng case chuyển sang cần re-auth.","kb_ids":["shop-connection-and-reauth#KB-009","shop-connection-and-reauth#KB-010"],"supersedes":"OQ-merchant-app-053"}
```

## OQ-shop-043 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-043","type":"OPEN_ISSUE","feature_id":"shop-connection-and-reauth","summary":"Shop còn 'đã cài' mà token chết được phát hiện thế nào (thành phần nào bật cờ, khi nào)? — Tài liệu chỉ nêu hệ quả, không nêu cơ chế.","kb_ids":["shop-connection-and-reauth#KB-041"],"supersedes":"OQ-merchant-app-054"}
```

## OQ-shop-044 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-044","type":"OPEN_ISSUE","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"Lỗi đã biết: nếu thông báo gỡ app bị mất, shop vẫn ở trạng thái INSTALLED trong khi token đã chết; job nền của shop thất bại dần với lỗi re-auth cho tới lần đăng nhập kế tiếp. Cần xác nhận có cơ chế phát hiện / tự sửa trạng thái không, và ai bật cờ cấp quyền lại vào lúc nào.","kb_ids":["shop-uninstall-reinstall-lifecycle#KB-022"],"check_ids":["shop-uninstall-reinstall-lifecycle:CHK-013"],"supersedes":"OQ-merchant-app-055"}
```

## OQ-shop-045 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-045","type":"OPEN_ISSUE","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"'Dọn dữ liệu liên quan' khi nhận app/uninstalled gồm những dữ liệu nào? — Tài liệu chỉ nói box/đơn được giữ; không biết dữ liệu nào bị xoá để kiểm.","kb_ids":["shop-uninstall-reinstall-lifecycle#KB-017"],"supersedes":"OQ-merchant-app-056"}
```

## OQ-shop-046 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-046","type":"OPEN_ISSUE","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"Email capacity khi chạm trần được gửi một lần hay mỗi lần vượt; khi nào reset? — Kiểm số lượng email gửi khi cài lại vượt hạn mức.","kb_ids":["shop-uninstall-reinstall-lifecycle#KB-034"],"supersedes":"OQ-merchant-app-057"}
```

## OQ-shop-047 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-047","type":"OPEN_ISSUE","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"Giá trị mặc định của bộ lọc Trashed khi mở màn Shops là gì? — Quyết định shop đã gỡ có hiện trong danh sách mặc định không.","kb_ids":["shop-uninstall-reinstall-lifecycle#KB-043"],"supersedes":"OQ-merchant-app-058"}
```

## OQ-shop-048 — OPEN_ISSUE

```json
{"oq_id":"OQ-shop-048","type":"OPEN_ISSUE","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"shop/update có chống xử lý trùng không; 'thử lại tối đa 3 lần' là retry của job hay chống trùng? — Không suy được hành vi khi Shopify giao trùng thông báo.","kb_ids":["shop-uninstall-reinstall-lifecycle#KB-052"],"supersedes":"OQ-merchant-app-059"}
```

## OQ-shop-049 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-049","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Các phát biểu mức object này không nêu vai trò áp dụng (role để 'unspecified' vì yêu cầu bootstrap không cố định role); cần xác nhận vai trò/bề mặt áp dụng trước khi dùng làm oracle theo role.","kb_ids":["_object-level#KB-001","_object-level#KB-011","_object-level#KB-012","_object-level#KB-013","_object-level#KB-016","_object-level#KB-019"],"supersedes":"OQ-merchant-app-060"}
```

## OQ-shop-050 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-050","type":"NEEDS_CONFIRMATION","feature_id":"account-kill-switch","summary":"Tài liệu ghi kèm 'chưa xác nhận' rằng webhook không đi qua lớp chặn của công tắc tài khoản; cần dev xác nhận webhook (orders/paid, shop/update...) có bỏ qua công tắc hay không.","kb_ids":["account-kill-switch#KB-011"],"supersedes":"OQ-merchant-app-061"}
```

## OQ-shop-051 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-051","type":"NEEDS_CONFIRMATION","feature_id":"account-kill-switch","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["account-kill-switch:CHK-002","account-kill-switch:CHK-005","account-kill-switch:CHK-006","account-kill-switch:CHK-007","account-kill-switch:CHK-008","account-kill-switch:CHK-009","account-kill-switch:CHK-010","account-kill-switch:CHK-012"],"supersedes":"OQ-merchant-app-062"}
```

## OQ-shop-052 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-052","type":"NEEDS_CONFIRMATION","feature_id":"account-kill-switch","summary":"Portal chỉ bị chặn khi shop vừa có plan Shopify \"trial\" vừa thiếu tỉnh hoặc thành phố phải không (shop trial đủ địa chỉ và shop không phải trial thiếu địa chỉ đều không bị chặn)? Shop trial vừa cài, chưa nhận thông báo shop update chứa tên plan, có bị chặn ngay không?","check_ids":["account-kill-switch:CHK-013"],"supersedes":"OQ-merchant-app-063"}
```

## OQ-shop-053 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-053","type":"NEEDS_CONFIRMATION","feature_id":"account-kill-switch","summary":"Khi công tắc tài khoản Tắt, ngoài trang reveal thì widget, theme block, block Unbox ở trang cảm ơn/order status và mua box bằng store credit trên storefront có bị ẩn hay chặn không, và storefront dùng metafield trạng thái tài khoản thế nào?","check_ids":["account-kill-switch:CHK-014"],"supersedes":"OQ-merchant-app-064"}
```

## OQ-shop-054 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-054","type":"NEEDS_CONFIRMATION","feature_id":"account-kill-switch","summary":"Khi công tắc tài khoản Tắt, các webhook khác ngoài webhook đơn (shop update, app uninstalled, bulk operation finished) có bỏ qua lớp chặn và vẫn được xử lý không? Tài liệu ghi điều này nhưng kèm chú thích chưa xác nhận.","check_ids":["account-kill-switch:CHK-015"],"supersedes":"OQ-merchant-app-065"}
```

## OQ-shop-055 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-055","type":"NEEDS_CONFIRMATION","feature_id":"account-kill-switch","summary":"Khi công tắc tài khoản Tắt, trang my orders và trang unbox của khách phải trả gì cụ thể (404, trang trắng, đẩy sang đăng nhập hay một thông báo bị từ chối), với status code nào?","check_ids":["account-kill-switch:CHK-016"],"supersedes":"OQ-merchant-app-066"}
```

## OQ-shop-056 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-056","type":"NEEDS_CONFIRMATION","feature_id":"gdpr-data-requests","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["gdpr-data-requests:CHK-001","gdpr-data-requests:CHK-002"],"supersedes":"OQ-merchant-app-076"}
```

## OQ-shop-057 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-057","type":"NEEDS_CONFIRMATION","feature_id":"gdpr-data-requests","summary":"Khi nhiều bảng dữ liệu không nối khoá tới khách, làm sao xác định đủ dữ liệu của một khách để xuất hoặc xoá, và bảng nào thuộc phạm vi?","check_ids":["gdpr-data-requests:CHK-007"],"supersedes":"OQ-merchant-app-077"}
```

## OQ-shop-058 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-058","type":"NEEDS_CONFIRMATION","feature_id":"install-and-onboarding","summary":"Chữ thông báo gói Free nêu giới hạn 10 box sales; 10 là giá trị gõ cứng/seed, không phải hạn mức production đã xác nhận. Cần xác nhận hạn mức thật của gói Free trên production và chữ hiển thị tương ứng.","kb_ids":["install-and-onboarding#KB-056"],"supersedes":"OQ-merchant-app-087"}
```

## OQ-shop-059 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-059","type":"NEEDS_CONFIRMATION","feature_id":"install-and-onboarding","summary":"Sau khi merchant bấm Skip và xác nhận bỏ qua wizard, onboarding có được đánh dấu là xong không, và Dashboard, thẻ Setup guide, menu trái hiện gì (kể cả sau khi tải lại trang khi shop vẫn chưa có box)?","check_ids":["install-and-onboarding:CHK-008"],"supersedes":"OQ-merchant-app-088"}
```

## OQ-shop-060 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-060","type":"NEEDS_CONFIRMATION","feature_id":"install-and-onboarding","summary":"Khi merchant đã lưu box lần đầu (shop đã có box) nhưng chưa hoàn tất màn kết, tải lại trang ở bước Launch thì wizard còn hiện ở bước Launch hay app chuyển thẳng sang Dashboard?","check_ids":["install-and-onboarding:CHK-011"],"supersedes":"OQ-merchant-app-089"}
```

## OQ-shop-061 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-061","type":"NEEDS_CONFIRMATION","feature_id":"install-and-onboarding","summary":"Mục \"Set up your first mystery box\" của Setup guide có được tính là xong khi shop chỉ có box ở trạng thái nháp (chưa Active) không?","check_ids":["install-and-onboarding:CHK-016"],"supersedes":"OQ-merchant-app-090"}
```

## OQ-shop-062 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-062","type":"NEEDS_CONFIRMATION","feature_id":"install-and-onboarding","summary":"Việc ẩn thẻ Setup guide 30 ngày tính theo trình duyệt hay theo shop (trình duyệt khác có còn thấy thẻ không), thẻ có tự hiện lại đúng sau 30 ngày không, và có cách nào cho merchant hiện lại thẻ sớm hơn không?","check_ids":["install-and-onboarding:CHK-018"],"supersedes":"OQ-merchant-app-091"}
```

## OQ-shop-063 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-063","type":"NEEDS_CONFIRMATION","feature_id":"install-and-onboarding","summary":"Khi merchant từ chối màn hình xin quyền của Shopify lúc cài app thì merchant thấy gì, và hệ thống có tạo bản ghi shop hay gói Free nào không?","check_ids":["install-and-onboarding:CHK-021"],"supersedes":"OQ-merchant-app-092"}
```

## OQ-shop-064 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-064","type":"NEEDS_CONFIRMATION","feature_id":"install-and-onboarding","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["install-and-onboarding:CHK-023","install-and-onboarding:CHK-028"],"supersedes":"OQ-merchant-app-093"}
```

## OQ-shop-065 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-065","type":"NEEDS_CONFIRMATION","feature_id":"install-and-onboarding","summary":"Tài liệu nêu dev store thiếu địa chỉ là một nguyên nhân khiến app trống sau khi cài. Đây là hành vi chấp nhận được hay là lỗi cần sửa, và khi đó merchant phải thấy gì, bản ghi shop phải có những trường nào?","check_ids":["install-and-onboarding:CHK-025"],"supersedes":"OQ-merchant-app-094"}
```

## OQ-shop-066 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-066","type":"NEEDS_CONFIRMATION","feature_id":"shop-connection-and-reauth","summary":"Thời hạn chính xác của khoá truy cập (tài liệu ghi \"khoảng 1 giờ\") và thời điểm token đăng nhập của shop bị đóng băng chết (tài liệu ghi \"khoảng 90 ngày\") cần dev xác nhận; một tài liệu khác ghi khoá truy cập hết hạn sau đúng 1 giờ và khoá làm mới sống 90 ngày.","kb_ids":["shop-connection-and-reauth#KB-001","shop-connection-and-reauth#KB-005"],"check_ids":["shop-connection-and-reauth:CHK-023","shop-connection-and-reauth:CHK-024"],"supersedes":"OQ-merchant-app-095"}
```

## OQ-shop-067 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-067","type":"NEEDS_CONFIRMATION","feature_id":"shop-connection-and-reauth","summary":"Nhận định của support playbook rằng khi shop có ngày \"Re-auth Required At\" thì \"gần như mọi thứ\" của shop dừng và re-auth \"thường\" là gốc chung khi cả shop sai nhiều thứ cần xác nhận phạm vi chính xác: chức năng nào vẫn chạy khi shop cần cấp quyền lại.","kb_ids":["shop-connection-and-reauth#KB-027"],"supersedes":"OQ-merchant-app-096"}
```

## OQ-shop-068 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-068","type":"NEEDS_CONFIRMATION","feature_id":"shop-connection-and-reauth","summary":"Job gia hạn token hằng ngày có làm mới shop có khoá làm mới còn đúng 10 ngày không, và shop còn hơn 10 ngày có chắc chắn không bị job làm mới không?","check_ids":["shop-connection-and-reauth:CHK-004"],"supersedes":"OQ-merchant-app-097"}
```

## OQ-shop-069 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-069","type":"NEEDS_CONFIRMATION","feature_id":"shop-connection-and-reauth","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["shop-connection-and-reauth:CHK-017","shop-connection-and-reauth:CHK-018"],"supersedes":"OQ-merchant-app-098"}
```

## OQ-shop-070 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-070","type":"NEEDS_CONFIRMATION","feature_id":"shop-connection-and-reauth","summary":"Đơn khách đã trả trong lúc shop cần cấp quyền lại có tự được xử lý lại sau khi merchant cấp quyền không, hay bắt buộc support xử lý lại bằng tay cho từng đơn?","kb_ids":["shop-connection-and-reauth#KB-043"],"check_ids":["shop-connection-and-reauth:CHK-019"],"supersedes":"OQ-merchant-app-099"}
```

## OQ-shop-071 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-071","type":"NEEDS_CONFIRMATION","feature_id":"shop-connection-and-reauth","summary":"Khi merchant từ chối màn cấp quyền lúc cài app lần đầu, hệ thống có tạo bản ghi shop không và merchant thấy gì?","check_ids":["shop-connection-and-reauth:CHK-025"],"supersedes":"OQ-merchant-app-100"}
```

## OQ-shop-072 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-072","type":"NEEDS_CONFIRMATION","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"Hành vi huỷ lịch thăm dò nguồn đơn sau khi xoá shop (để không gọi Shopify bằng token đã thu hồi) chỉ có trên nhánh build-staging, chưa lên production. Khi nào thay đổi này lên production, và đến lúc đó hành vi production là gì?","kb_ids":["shop-uninstall-reinstall-lifecycle#KB-020"],"supersedes":"OQ-merchant-app-101"}
```

## OQ-shop-073 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-073","type":"NEEDS_CONFIRMATION","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"Sau khi gỡ app, theme embed và block checkout trên storefront có còn render hay không? Tài liệu cho rằng đây là hành vi của Shopify và tự ghi là chưa xác nhận.","kb_ids":["shop-uninstall-reinstall-lifecycle#KB-021"],"check_ids":["shop-uninstall-reinstall-lifecycle:CHK-017"],"supersedes":"OQ-merchant-app-102"}
```

## OQ-shop-074 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-074","type":"NEEDS_CONFIRMATION","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"Box được khôi phục khi cài lại \"thường\" ở trạng thái đã unpublish: trường hợp nào box không bị unpublish (vd shop chưa vượt hạn mức gói Free)? Cần xác nhận điều kiện chính xác.","kb_ids":["shop-uninstall-reinstall-lifecycle#KB-035"],"check_ids":["shop-uninstall-reinstall-lifecycle:CHK-009"],"supersedes":"OQ-merchant-app-103"}
```

## OQ-shop-075 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-075","type":"NEEDS_CONFIRMATION","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["shop-uninstall-reinstall-lifecycle:CHK-001","shop-uninstall-reinstall-lifecycle:CHK-002","shop-uninstall-reinstall-lifecycle:CHK-003","shop-uninstall-reinstall-lifecycle:CHK-006","shop-uninstall-reinstall-lifecycle:CHK-007","shop-uninstall-reinstall-lifecycle:CHK-008"],"supersedes":"OQ-merchant-app-104"}
```

## OQ-shop-076 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-076","type":"NEEDS_CONFIRMATION","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"'Dọn dữ liệu liên quan' khi nhận thông báo gỡ app gồm chính xác những dữ liệu nào (ngoài phiên, token và cờ re-auth)?","check_ids":["shop-uninstall-reinstall-lifecycle:CHK-016"],"supersedes":"OQ-merchant-app-105"}
```

## OQ-shop-077 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-077","type":"NEEDS_CONFIRMATION","feature_id":"shop-uninstall-reinstall-lifecycle","summary":"Báo cáo 'active' loại bỏ shop có plan Shopify đóng nằm ở màn hình hoặc bản xuất nào để kiểm được?","kb_ids":["_object-level#KB-019","shop-uninstall-reinstall-lifecycle#KB-045","shop-uninstall-reinstall-lifecycle#KB-046","shop-uninstall-reinstall-lifecycle#KB-047"],"check_ids":["shop-uninstall-reinstall-lifecycle:CHK-021"],"supersedes":"OQ-merchant-app-106"}
```

## OQ-shop-078 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-078","type":"NEEDS_CONFIRMATION","feature_id":"install-and-onboarding","summary":"Trên staging, trạng thái App extension status được đọc qua Admin API và cờ localStorage của trình duyệt, không qua backend Mysbox. Trạng thái \"Inactive\" / \"Not Installed\" được suy từ dữ liệu nào, và cờ localStorage có thể làm bảng hiện sai trên trình duyệt khác hoặc sau khi merchant gỡ block không?","kb_ids":["install-and-onboarding#KB-064","install-and-onboarding#KB-065"],"check_ids":["install-and-onboarding:CHK-029"],"tags":["staging-observed"],"supersedes":"OQ-merchant-app-114"}
```

## OQ-shop-079 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-shop-079","type":"NEEDS_CONFIRMATION","feature_id":"install-and-onboarding","summary":"Trên staging, thẻ Setup guide đã xong 3/3 vẫn hiện với các nút bị disable, và không thấy cách mở lại thẻ nếu merchant bấm đóng. Thẻ có nên tự ẩn khi đã xong hết không, và sau khi đóng thì merchant hiện lại thẻ bằng cách nào?","kb_ids":["install-and-onboarding#KB-066","install-and-onboarding#KB-067"],"check_ids":["install-and-onboarding:CHK-030"],"tags":["staging-observed"],"supersedes":"OQ-merchant-app-115"}
```
