# Open Questions — unbox-sharing

## OQ-unbox-sharing-001 — CONFLICT

```json
{"oq_id":"OQ-unbox-sharing-001","type":"CONFLICT","feature_id":"recent-pulls-feed","summary":"Lượt reveal xảy ra khi \"Show recent pulls\" đang tắt có được Resync đưa lên feed sau khi bật công tắc không, trên production. Mâu thuẫn trong cùng tài liệu Recent pulls; cần dev xác nhận câu hỏi thường gặp áp cho môi trường nào.","side_a":"Mysbox Product KB v1 \"Recent pulls (feed \"vừa trúng\" ở trang sản phẩm)\" §Bước 1 — Một lượt reveal xảy ra (trước thay đổi trên build-staging, chỉ ghi lịch sử khi feed bật) và Mysbox Product KB v1 \"Playbook 3: storefront, widget, theme và trang khách\" §Feed recent pulls thiếu / sai / hiện đơn test (trên production feed tắt thì không ghi gì)","side_b":"Mysbox Product KB v1 \"Recent pulls (feed \"vừa trúng\" ở trang sản phẩm)\" §Câu hỏi thường gặp (sau khi bật công tắc, lượt cũ chỉ lên feed sau khi bấm Resync — hàm ý lượt cũ có trong lịch sử)","conflict_group":"CONF-automation-growth-03","kb_ids":["recent-pulls-feed#KB-021","recent-pulls-feed#KB-061"],"check_ids":["recent-pulls-feed:CHK-014"],"supersedes":"OQ-automation-growth-004"}
```

## OQ-unbox-sharing-002 — CONFLICT

```json
{"oq_id":"OQ-unbox-sharing-002","type":"CONFLICT","feature_id":"recent-pulls-feed","summary":"Entry feed công khai có trường box_count hay không: danh sách trường \"chỉ chứa\" không có box_count, trong khi ví dụ có số ghi một entry (box_count 2). Mâu thuẫn trong cùng tài liệu Recent pulls; không ảnh hưởng tính ẩn danh nhưng cần dev xác nhận danh sách trường đầy đủ.","side_a":"Mysbox Product KB v1 \"Recent pulls (feed \"vừa trúng\" ở trang sản phẩm)\" §Ẩn danh (feed chỉ chứa mã entry, thời điểm mở, variant id + pool/tier id)","side_b":"Mysbox Product KB v1 \"Recent pulls (feed \"vừa trúng\" ở trang sản phẩm)\" §Ví dụ có số (một entry có box_count 2)","conflict_group":"CONF-automation-growth-04","kb_ids":["recent-pulls-feed#KB-033","recent-pulls-feed#KB-034"],"check_ids":["recent-pulls-feed:CHK-019"],"staging_observation":"Ghi chú quan sát staging cho OQ-automation-growth-005 / CONF-automation-growth-04: 2026-10-17: Feed rỗng nên không có danh sách field entry; chỉ thấy cơ chế addFeed lưu feed.entries theo variant id.","staging_observation_kb_ids":["recent-pulls-feed#KB-083","recent-pulls-feed#KB-084"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-automation-growth-005"}
```

## OQ-unbox-sharing-003 — CONFLICT

```json
{"oq_id":"OQ-unbox-sharing-003","type":"CONFLICT","feature_id":"recent-pulls-feed","summary":"Setting \"visible from\" của Recent pulls có trên màn hình Style settings của merchant app không, và ai đổi được nó. Tài liệu Recent pulls nói không có màn hình (tài liệu General Settings xếp nó vào nhóm setting ẩn do nhân viên Mysbox đổi trong back-office), còn playbook hỗ trợ liệt kê nó trong cài đặt portal Style settings → Recent pulls cùng với \"publish test orders\" (vốn chỉ có trên build-staging).","side_a":"Mysbox Product KB v1 \"Recent pulls (feed \"vừa trúng\" ở trang sản phẩm)\" §Setting (Style Settings → \"Recent pulls\") (recent_pulls_visible_from không có màn hình)","side_b":"Mysbox Product KB v1 \"Playbook 3: storefront, widget, theme và trang khách\" §Feed recent pulls thiếu / sai / hiện đơn test (portal Style settings → Recent pulls: công tắc, \"visible from\", \"publish test orders\")","conflict_group":"CONF-automation-growth-05","kb_ids":["recent-pulls-feed#KB-055","recent-pulls-feed#KB-056"],"check_ids":["recent-pulls-feed:CHK-016"],"staging_observation":"Ghi chú quan sát staging cho OQ-automation-growth-006 / CONF-automation-growth-05: 2026-10-17: Style Settings → Recent pulls (công tắc tắt) không có \"visible from\" hay \"publish test orders\"; chưa biết khi bật có hiện không, và ai đổi được visible-from (back-office) không quan sát.","staging_observation_kb_ids":["recent-pulls-feed#KB-082"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-automation-growth-006"}
```

## OQ-unbox-sharing-004 — CONFLICT

```json
{"oq_id":"OQ-unbox-sharing-004","type":"CONFLICT","feature_id":"share-unboxing","summary":"Cần dev xác nhận đơn khác tiền tệ báo cáo có được đếm vào số đơn của link chia sẻ hay chỉ không được tính doanh thu, và đơn test có xuất hiện trong số đơn không. Mâu thuẫn nằm trong cùng một tài liệu (mục luồng ghi nhận và mục câu hỏi thường gặp).","side_a":"Tài liệu \"Share unboxing\" §Đơn đến từ link giới thiệu và độ trễ: doanh thu chỉ tính khi cùng tiền tệ báo cáo (không quy đổi) — ngụ ý đơn vẫn được ghi","side_b":"Cùng tài liệu §Câu hỏi thường gặp: liệt kê \"khác tiền tệ\" (và \"đơn test\") như lý do đơn từ link chưa được ghi","conflict_group":"CONF-automation-growth-07","kb_ids":["share-unboxing#KB-113","share-unboxing#KB-126"],"check_ids":["share-unboxing:CHK-017"],"supersedes":"OQ-automation-growth-007"}
```

## OQ-unbox-sharing-005 — CONFLICT

```json
{"oq_id":"OQ-unbox-sharing-005","type":"CONFLICT","feature_id":"share-unboxing","summary":"Cần xác nhận merchant có tự tắt được tính năng share unboxing trên màn hình Style settings hay công tắc chỉ nằm ở cấu hình nội bộ của nhân viên Mysbox.","side_a":"Tài liệu \"Share unboxing\" §Setting của merchant và \"General Settings\" §Setting ẩn: công tắc share_unboxing_enabled không có màn hình, chỉ nhân viên Mysbox đổi qua cấu hình nội bộ","side_b":"Playbook 5 (tài khoản, kết nối, gỡ/cài app và tích hợp) §Ảnh share bị thiếu / link share lỗi: merchant tắt share ở Style settings -> Share","conflict_group":"CONF-automation-growth-08","kb_ids":["share-unboxing#KB-011","share-unboxing#KB-136"],"check_ids":["share-unboxing:CHK-014"],"staging_observation":"Ghi chú quan sát staging cho OQ-automation-growth-008 / CONF-automation-growth-08: 2026-10-17: Style Settings staging có thẻ Share unboxing (màu, ẩn nút kênh) nhưng không có công tắc bật/tắt share và không có mục \"Share\" khác. Khớp phía KB-011; back-office không quan sát; conflict không tự đóng.","staging_observation_kb_ids":["share-unboxing#KB-149"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-automation-growth-008"}
```

## OQ-unbox-sharing-006 — CONFLICT

```json
{"oq_id":"OQ-unbox-sharing-006","type":"CONFLICT","feature_id":"share-unboxing","summary":"Cần xác nhận khi công tắc share của shop tắt thì nút Share ở storefront bị ẩn, hay nút vẫn hiện và tạo link báo lỗi \"forbidden\" kèm toast.","side_a":"Playbook 5 §Ảnh share bị thiếu / link share lỗi: công tắc share của shop tắt thì khách không thấy nút Share","side_b":"Tài liệu \"Share unboxing\" §Setting của merchant: khi công tắc tắt, gọi tạo link báo \"forbidden\" và hiện toast lỗi; tự ghi chưa xác nhận nút có bị ẩn","conflict_group":"CONF-automation-growth-09","kb_ids":["share-unboxing#KB-073","share-unboxing#KB-135"],"check_ids":["share-unboxing:CHK-013"],"supersedes":"OQ-automation-growth-009"}
```

## OQ-unbox-sharing-007 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-007","type":"OPEN_ISSUE","feature_id":"recent-pulls-feed","summary":"Hạn chế đã biết: resell, hoàn tiền và huỷ đơn không được phản ánh vào feed Recent pulls (món đã bán lại vẫn hiện). Theo dõi như regression watch; cần PO xác nhận vẫn là hạn chế được chấp nhận và có kế hoạch sửa hay không.","kb_ids":["recent-pulls-feed#KB-079"],"check_ids":["recent-pulls-feed:CHK-028"],"supersedes":"OQ-automation-growth-025"}
```

## OQ-unbox-sharing-008 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-008","type":"OPEN_ISSUE","feature_id":"recent-pulls-feed","summary":"Hạn chế lưu trữ đã biết của feed: entry lớn hơn 128 KB không ghi được, và khoá metafield của các trang feed cũ không được dọn. Chưa rõ entry quá lớn bị bỏ hẳn, thử lại hay có báo lỗi/log.","kb_ids":["recent-pulls-feed#KB-080","recent-pulls-feed#KB-081"],"check_ids":["recent-pulls-feed:CHK-029","recent-pulls-feed:CHK-030"],"supersedes":"OQ-automation-growth-026"}
```

## OQ-unbox-sharing-009 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-009","type":"OPEN_ISSUE","feature_id":"recent-pulls-feed","summary":"Merchant có tự chạy Resync được không, hay chỉ nhân viên nội bộ trong admin panel? (tài liệu viết \"bấm Resync\" ở phía merchant nhưng thao tác nằm ở admin panel) — Role mơ hồ; quyết định ai thực hiện bước áp cấu hình mới cho feed đã publish.","kb_ids":["recent-pulls-feed#KB-038","recent-pulls-feed#KB-060","recent-pulls-feed#KB-074"],"staging_observation":"Ghi chú quan sát staging cho OQ-automation-growth-027: 2026-10-17: Không có nút Resync phía merchant ở Style Settings → Recent pulls (công tắc tắt); admin panel NOT_COVERED.","staging_observation_kb_ids":["recent-pulls-feed#KB-082"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-automation-growth-027"}
```

## OQ-unbox-sharing-010 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-010","type":"OPEN_ISSUE","feature_id":"recent-pulls-feed","summary":"Feed hiển thị mọi món trúng hay chỉ món hiếm? — Ví dụ ngụ ý món hiếm nhưng không có quy tắc lọc; không suy ra từ ví dụ.","kb_ids":["recent-pulls-feed#KB-005","recent-pulls-feed#KB-009"],"staging_observation":"Ghi chú quan sát staging cho OQ-automation-growth-028: 2026-10-17: Món trúng của đơn test là món 25%; feed tắt → không trả lời được lọc món.","staging_observation_kb_ids":["recent-pulls-feed#KB-084"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-automation-growth-028"}
```

## OQ-unbox-sharing-011 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-011","type":"OPEN_ISSUE","feature_id":"recent-pulls-feed","summary":"Quyền hide_recent_pull/resync_recent_pulls gán cho role admin nào, và trang admin hiển thị gì khi thiếu quyền? — Không có oracle permission negative cho tab Recent pulls.","kb_ids":["recent-pulls-feed#KB-065","recent-pulls-feed#KB-066","recent-pulls-feed#KB-067"],"supersedes":"OQ-automation-growth-029"}
```

## OQ-unbox-sharing-012 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-012","type":"OPEN_ISSUE","feature_id":"recent-pulls-feed","summary":"Resync và Hide from recent pulls báo hoàn tất hoặc thất bại cho nhân viên thế nào (ngoài nhãn \"Retry hiding\")? Unpublish/Delete box có hộp xác nhận không? — Các thao tác chạy nền; không có tín hiệu hoàn tất để kiểm.","kb_ids":["recent-pulls-feed#KB-073","recent-pulls-feed#KB-076","recent-pulls-feed#KB-077"],"supersedes":"OQ-automation-growth-030"}
```

## OQ-unbox-sharing-013 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-013","type":"OPEN_ISSUE","feature_id":"recent-pulls-feed","summary":"Mỗi sự kiện đầu vào của nhóm (mở box, resell xong, hết hàng, auto-unbox sắp tới) đi vào tính năng nào giữa Shopify Flow, Share unboxing và Recent pulls? — Sơ đồ tổng quan vẽ chung một danh sách sự kiện cho ba tính năng; tester không biết sự kiện nào kích hoạt feed.","kb_ids":["_object-level#KB-002"],"supersedes":"OQ-automation-growth-031"}
```

## OQ-unbox-sharing-014 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-014","type":"OPEN_ISSUE","feature_id":"share-unboxing","summary":"Trên bản staging đã kiểm, storefront không gọi endpoint ghi sự kiện mở popup và hành động chia sẻ nên \"Popup opens\" và \"Share actions\" có thể luôn bằng 0. Tài liệu tự ghi mới tìm trong code, chưa chạy end-to-end; cần xác nhận lỗi có thật không.","kb_ids":["share-unboxing#KB-097"],"check_ids":["share-unboxing:CHK-020"],"supersedes":"OQ-automation-growth-032"}
```

## OQ-unbox-sharing-015 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-015","type":"OPEN_ISSUE","feature_id":"share-unboxing","summary":"Token của link chia sẻ là công khai nên bất kỳ ai cũng có thể gắn ref=sl_<token> vào link mua để đơn được ghi cho link chia sẻ. Tài liệu coi là chỉ ảnh hưởng thống kê; cần xác nhận đây là giới hạn được chấp nhận hay lỗi cần sửa.","kb_ids":["share-unboxing#KB-114"],"check_ids":["share-unboxing:CHK-021"],"supersedes":"OQ-automation-growth-033"}
```

## OQ-unbox-sharing-016 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-016","type":"OPEN_ISSUE","feature_id":"share-unboxing","summary":"Chưa có màn hình nào cho merchant hay admin nội bộ xem kết quả share unboxing; số liệu chỉ nằm sau endpoint tóm tắt chưa được trang nào gọi. Cần xác nhận kế hoạch hiển thị.","kb_ids":["share-unboxing#KB-115"],"check_ids":["share-unboxing:CHK-022"],"supersedes":"OQ-automation-growth-034"}
```

## OQ-unbox-sharing-017 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-017","type":"OPEN_ISSUE","feature_id":"share-unboxing","summary":"Hệ thống không lên lịch bù kiểm tra nguồn đơn cho các đơn thanh toán trước khi shop tạo link chia sẻ đầu tiên. Cần xác nhận đây là hành vi chủ đích hay lỗi.","kb_ids":["share-unboxing#KB-146"],"check_ids":["share-unboxing:CHK-023"],"supersedes":"OQ-automation-growth-035"}
```

## OQ-unbox-sharing-018 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-018","type":"OPEN_ISSUE","feature_id":"share-unboxing","summary":"Số liệu analytics chia sẻ bị mất do job lỗi không được tính lại. Cần xác nhận có cơ chế tính lại hay đây là giới hạn đã biết.","kb_ids":["share-unboxing#KB-148"],"check_ids":["share-unboxing:CHK-024"],"supersedes":"OQ-automation-growth-036"}
```

## OQ-unbox-sharing-019 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-019","type":"NEEDS_CONFIRMATION","feature_id":"recent-pulls-feed","summary":"Một phần Recent pulls chỉ có trên nhánh build-staging, chưa lên production: ghi lịch sử mọi lượt reveal digital cho mọi shop (kể cả khi feed tắt) và tuỳ chọn \"publish test orders\". Cần xác nhận khi nào lên production, và cho tới lúc đó hành vi production là gì (lịch sử chỉ ghi khi feed bật; đơn test luôn bị loại khỏi feed).","kb_ids":["recent-pulls-feed#KB-021","recent-pulls-feed#KB-022","recent-pulls-feed#KB-056","recent-pulls-feed#KB-058","recent-pulls-feed#KB-059"],"staging_observation":"Ghi chú quan sát staging cho OQ-automation-growth-054: 2026-10-17: Staging build hiện tại không có tuỳ chọn \"publish test orders\" trên Style Settings; \"Show recent pulls\" tắt. Lộ trình production và hành vi production không quan sát.","staging_observation_kb_ids":["recent-pulls-feed#KB-082"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-automation-growth-054"}
```

## OQ-unbox-sharing-020 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-020","type":"NEEDS_CONFIRMATION","feature_id":"recent-pulls-feed","summary":"Các giới hạn của feed chỉ được nêu ở dạng xấp xỉ: dung lượng mỗi trang khoảng 100 KB, tổng lượt mở trọn đời xấp xỉ số trang × 100, publish khoảng 6 lần/phút mỗi box. Cần giá trị chính xác nếu dùng làm boundary test.","kb_ids":["recent-pulls-feed#KB-028","recent-pulls-feed#KB-029","recent-pulls-feed#KB-031"],"supersedes":"OQ-automation-growth-055"}
```

## OQ-unbox-sharing-021 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-021","type":"NEEDS_CONFIRMATION","feature_id":"recent-pulls-feed","summary":"Thuật ngữ \"box số\" trong điều kiện hiển thị block \"Mysbox recent pulls\" có đúng là box digital (instant) không, và block hiển thị gì khi đặt trên trang của box physical.","kb_ids":["recent-pulls-feed#KB-017","recent-pulls-feed#KB-040"],"staging_observation":"Ghi chú quan sát staging cho OQ-automation-growth-056: 2026-10-17: Trang box physical: block mount nhưng không hiện gì, giống box digital khi feed tắt; hành vi khi feed bật chưa quan sát.","staging_observation_kb_ids":["recent-pulls-feed#KB-085"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-automation-growth-056"}
```

## OQ-unbox-sharing-022 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-022","type":"NEEDS_CONFIRMATION","feature_id":"recent-pulls-feed","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["recent-pulls-feed:CHK-006","recent-pulls-feed:CHK-023","recent-pulls-feed:CHK-025"],"staging_observation":"Ghi chú quan sát staging cho OQ-automation-growth-057: 2026-10-17: Không có request riêng tới backend cho feed (dữ liệu chỉ qua Liquid inline); không có PII trong mysboxStore/_Mysbox. Field của entry thật chưa quan sát (feed rỗng). CHK-023/025 NOT_COVERED.","staging_observation_kb_ids":["recent-pulls-feed#KB-083"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-automation-growth-057"}
```

## OQ-unbox-sharing-023 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-023","type":"NEEDS_CONFIRMATION","feature_id":"recent-pulls-feed","summary":"Trên nhánh staging, Mysbox ghi lịch sử mọi lượt reveal digital bất kể feed bật hay tắt, và có tuỳ chọn \"publish test orders\" (mặc định tắt) để đưa đơn test vào feed. Khi nào hai thay đổi này lên production, và hành vi có giữ như mô tả không?","check_ids":["recent-pulls-feed:CHK-018"],"staging_observation":"Ghi chú quan sát staging cho OQ-automation-growth-058: 2026-10-17: Như OQ-automation-growth-054: không có tuỳ chọn \"publish test orders\" trên Style Settings staging.","staging_observation_kb_ids":["recent-pulls-feed#KB-082"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-automation-growth-058"}
```

## OQ-unbox-sharing-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-024","type":"NEEDS_CONFIRMATION","feature_id":"recent-pulls-feed","summary":"Lượt mở box do auto-unbox, do action Shopify Flow hoặc do admin mở hộ có được ghi lịch sử Recent pulls và đưa lên feed như lượt khách tự mở không? Feed hiển thị mọi món trúng hay chỉ món hiếm?","check_ids":["recent-pulls-feed:CHK-027"],"supersedes":"OQ-automation-growth-059"}
```

## OQ-unbox-sharing-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-025","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Toàn bộ tính năng share unboxing (link chia sẻ, ảnh preview, theo dõi click và ghi nguồn đơn) chỉ có trên nhánh build-staging. Cần xác nhận khi nào lên production và hành vi production có giữ nguyên như tài liệu mô tả không; trước đó các item này không dùng làm expected result.","kb_ids":["share-unboxing#KB-001","share-unboxing#KB-002","share-unboxing#KB-003","share-unboxing#KB-004","share-unboxing#KB-005","share-unboxing#KB-006","share-unboxing#KB-007","share-unboxing#KB-008","share-unboxing#KB-009","share-unboxing#KB-010","share-unboxing#KB-011","share-unboxing#KB-012","share-unboxing#KB-013","share-unboxing#KB-014","share-unboxing#KB-015","share-unboxing#KB-016","share-unboxing#KB-017","share-unboxing#KB-018","share-unboxing#KB-019","share-unboxing#KB-020","share-unboxing#KB-021","share-unboxing#KB-022","share-unboxing#KB-023","share-unboxing#KB-024","share-unboxing#KB-025","share-unboxing#KB-026","share-unboxing#KB-027","share-unboxing#KB-028","share-unboxing#KB-029","share-unboxing#KB-030","share-unboxing#KB-031","share-unboxing#KB-032","share-unboxing#KB-033","share-unboxing#KB-034","share-unboxing#KB-035","share-unboxing#KB-036","share-unboxing#KB-037","share-unboxing#KB-038","share-unboxing#KB-039","share-unboxing#KB-040","share-unboxing#KB-041","share-unboxing#KB-042","share-unboxing#KB-043","share-unboxing#KB-044","share-unboxing#KB-045","share-unboxing#KB-046","share-unboxing#KB-047","share-unboxing#KB-048","share-unboxing#KB-049","share-unboxing#KB-050","share-unboxing#KB-051","share-unboxing#KB-052","share-unboxing#KB-053","share-unboxing#KB-054","share-unboxing#KB-055","share-unboxing#KB-056","share-unboxing#KB-057","share-unboxing#KB-058","share-unboxing#KB-059","share-unboxing#KB-060","share-unboxing#KB-061","share-unboxing#KB-062","share-unboxing#KB-063","share-unboxing#KB-064","share-unboxing#KB-065","share-unboxing#KB-066","share-unboxing#KB-067","share-unboxing#KB-068","share-unboxing#KB-069","share-unboxing#KB-070","share-unboxing#KB-071","share-unboxing#KB-072","share-unboxing#KB-073","share-unboxing#KB-074","share-unboxing#KB-075","share-unboxing#KB-076","share-unboxing#KB-077","share-unboxing#KB-078","share-unboxing#KB-079","share-unboxing#KB-080","share-unboxing#KB-081","share-unboxing#KB-082","share-unboxing#KB-083","share-unboxing#KB-084","share-unboxing#KB-085","share-unboxing#KB-086","share-unboxing#KB-087","share-unboxing#KB-088","share-unboxing#KB-089","share-unboxing#KB-090","share-unboxing#KB-091","share-unboxing#KB-092","share-unboxing#KB-093","share-unboxing#KB-094","share-unboxing#KB-095","share-unboxing#KB-096","share-unboxing#KB-097","share-unboxing#KB-098","share-unboxing#KB-099","share-unboxing#KB-100","share-unboxing#KB-101","share-unboxing#KB-102","share-unboxing#KB-103","share-unboxing#KB-104","share-unboxing#KB-105","share-unboxing#KB-106","share-unboxing#KB-107","share-unboxing#KB-108","share-unboxing#KB-109","share-unboxing#KB-110","share-unboxing#KB-111","share-unboxing#KB-112","share-unboxing#KB-113","share-unboxing#KB-114","share-unboxing#KB-115","share-unboxing#KB-116","share-unboxing#KB-117","share-unboxing#KB-118","share-unboxing#KB-119","share-unboxing#KB-120","share-unboxing#KB-121","share-unboxing#KB-122","share-unboxing#KB-123","share-unboxing#KB-124","share-unboxing#KB-125","share-unboxing#KB-126","share-unboxing#KB-127","share-unboxing#KB-128","share-unboxing#KB-129","share-unboxing#KB-130","share-unboxing#KB-131","share-unboxing#KB-132","share-unboxing#KB-133","share-unboxing#KB-134","share-unboxing#KB-135","share-unboxing#KB-136","share-unboxing#KB-137","share-unboxing#KB-138","share-unboxing#KB-139","share-unboxing#KB-140","share-unboxing#KB-141","share-unboxing#KB-142","share-unboxing#KB-143","share-unboxing#KB-144","share-unboxing#KB-145","share-unboxing#KB-146","share-unboxing#KB-147","share-unboxing#KB-148"],"supersedes":"OQ-automation-growth-060"}
```

## OQ-unbox-sharing-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-026","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Một số mô tả share unboxing được tài liệu tự ghi là chưa xác nhận: nút \"Share unboxing\" có hiện khi khách mở lại đơn cũ từ danh sách không, và trên bản staging chỉ link visits cùng số đơn là đo được thật. Cần dev xác nhận trước khi dùng làm expected result.","kb_ids":["share-unboxing#KB-019","share-unboxing#KB-098"],"supersedes":"OQ-automation-growth-061"}
```

## OQ-unbox-sharing-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-027","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Share unboxing hiện chỉ có trên nhánh staging: khi nào lên production, và trên production luồng \"mở box digital → bấm Share unboxing → có ảnh preview và link công khai\" có giữ đúng như tài liệu mô tả không?","check_ids":["share-unboxing:CHK-001"],"supersedes":"OQ-automation-growth-062"}
```

## OQ-unbox-sharing-028 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-028","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Ảnh preview chia sẻ có phải luôn 1200 x 630, gồm tiêu đề chúc mừng, tối đa 5 món với món hiếm nhất ở giữa, gộp món trùng, nhãn \"Best pull\" khi mở nhiều box, logo shop, watermark, nút \"Open your own box\" và ẩn chance khi merchant ẩn không? Quy tắc chọn 5 món khi có nhiều hơn 5 là gì?","check_ids":["share-unboxing:CHK-002"],"supersedes":"OQ-automation-growth-063"}
```

## OQ-unbox-sharing-029 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-029","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Mỗi lượt mở box có đúng một link chia sẻ, và ảnh cùng chữ preview có giữ nguyên như lần tạo đầu kể cả khi merchant đổi giao diện hoặc nội dung sau đó không?","check_ids":["share-unboxing:CHK-003"],"supersedes":"OQ-automation-growth-064"}
```

## OQ-unbox-sharing-030 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-030","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Hành vi các nút trong popup chia sẻ (tên file mysbox-unboxing.png hoặc .jpg khi phải nén dưới 2 MB, nội dung Message mặc định, Copy, Facebook/X/Whatsapp, Instagram mở khay chia sẻ hoặc lưu ảnh và copy tin nhắn khi máy không hỗ trợ) có đúng là hành vi mong muốn khi lên production không?","check_ids":["share-unboxing:CHK-004"],"supersedes":"OQ-automation-growth-065"}
```

## OQ-unbox-sharing-031 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-031","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Khi không tạo được link chia sẻ, popup có vẫn hiện ảnh, hiện toast \"Couldn't prepare your share. Please try again.\" và nút \"Try again\" tạo lại được link không?","check_ids":["share-unboxing:CHK-005"],"supersedes":"OQ-automation-growth-066"}
```

## OQ-unbox-sharing-032 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-032","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Nút \"Share unboxing\" có đúng chỉ hiện cho khách đã đăng nhập, với box digital, trên trình duyệt vừa thực hiện lượt mở đó không? Khi khách mở lại đơn cũ từ danh sách đơn thì có nút không, và đơn có cả box physical lẫn digital thì ảnh có gồm món của box physical không?","check_ids":["share-unboxing:CHK-006"],"supersedes":"OQ-automation-growth-067"}
```

## OQ-unbox-sharing-033 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-033","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Khi khách gửi yêu cầu tạo link chia sẻ cho lượt mở không thuộc mình, hệ thống có trả đúng cùng phản hồi \"Not found\" như với lượt mở không tồn tại (để chống dò) không? Status code và route của endpoint tạo link là gì?","check_ids":["share-unboxing:CHK-007"],"supersedes":"OQ-automation-growth-068"}
```

## OQ-unbox-sharing-034 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-034","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Trang link chia sẻ có đúng hiện thẻ preview với tiêu đề chỉ dùng tên riêng của khách (\"I\" khi không có tên) và mô tả \"Try your luck at {store name}\", rồi chuyển về trang sản phẩm của box (khi chỉ một loại box có trang online store) hoặc trang chủ shop, luôn trên domain shop, kèm ref=sl_{token}, tham số kênh c và utm cắt tối đa 100 ký tự không?","check_ids":["share-unboxing:CHK-008"],"supersedes":"OQ-automation-growth-069"}
```

## OQ-unbox-sharing-035 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-035","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Trang link chia sẻ phản hồi thế nào (status code, nội dung, có chuyển về shop không) khi token không tồn tại hoặc sai định dạng?","check_ids":["share-unboxing:CHK-009"],"supersedes":"OQ-automation-growth-070"}
```

## OQ-unbox-sharing-036 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-036","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Giới hạn mỗi khách tối đa 10 yêu cầu tạo link chia sẻ mỗi phút và 60 mỗi giờ tính theo cửa sổ trượt hay cố định, và khi vượt thì khách thấy thông báo gì (\"Too many requests\")?","check_ids":["share-unboxing:CHK-010"],"supersedes":"OQ-automation-growth-071"}
```

## OQ-unbox-sharing-037 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-037","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Hạn mức ảnh share hằng ngày (mặc định 300) tính theo shop hay theo shop và box, theo 24 giờ trượt hay reset theo mốc giờ; chỉ link tạo ảnh mới mới tốn hạn mức phải không; khi vượt thì mọi khách của shop nhận \"Daily limit reached\" và log cảnh báo tối đa một lần mỗi shop mỗi ngày phải không? Khi mở nhiều box cùng lúc thì tốn bao nhiêu ảnh?","check_ids":["share-unboxing:CHK-011"],"supersedes":"OQ-automation-growth-072"}
```

## OQ-unbox-sharing-038 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-038","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Khi ảnh share sai kích thước 1200 x 630, sai định dạng hoặc lớn hơn 2 MB, hay tiêu đề/mô tả preview vượt 150/300 ký tự, hệ thống cắt, từ chối hay báo lỗi — thông điệp và status code cụ thể là gì? Ảnh lưu có luôn được nén JPEG và xoá metadata không?","check_ids":["share-unboxing:CHK-012"],"supersedes":"OQ-automation-growth-073"}
```

## OQ-unbox-sharing-039 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-039","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Giá trị mặc định của phần tuỳ chỉnh share (bốn nút kênh đều hiện, màu popup và nút \"Save image\" theo theme, màu CTA trong ảnh là gì) và danh sách đầy đủ 11 đoạn chữ của share unboxing (mặc định tiếng Anh) là gì?","check_ids":["share-unboxing:CHK-015"],"staging_observation":"Ghi chú quan sát staging cho OQ-automation-growth-074: 2026-10-17: Ghi được giá trị mặc định trên form (popup #ffffff/#1a1a1a/#2563eb, 4 nút kênh hiện, CTA #1a1a1a/#ffffff); translations/share-unboxing?locale=default trả data null nên 11 đoạn chữ mặc định chưa đọc được.","staging_observation_kb_ids":["share-unboxing#KB-150","share-unboxing#KB-151"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-automation-growth-074"}
```

## OQ-unbox-sharing-040 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-040","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Quy tắc ghi nguồn đơn từ link chia sẻ (đến hạn khoảng 20 phút sau thanh toán, job mỗi 30 phút đọc customer journey, ghi theo lượt ghé cuối có ref trước khi mua, thử lại tối đa 60 phút rồi chốt \"no source\", đơn test lưu nhưng ẩn) có đúng không, khoảng trễ có được cam kết không, và merchant/admin xem nguồn đơn ở đâu?","check_ids":["share-unboxing:CHK-016"],"supersedes":"OQ-automation-growth-075"}
```

## OQ-unbox-sharing-041 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-041","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Các sự kiện theo dõi chia sẻ (View kể cả bot nhưng không hiện trong tóm tắt, Click qua beacon theo kênh, Popup open, Share action) có không lưu dữ liệu khách, IP hay order id, và giới hạn tần suất áp theo link cho loại sự kiện nào? Endpoint tóm tắt số liệu có những field, tham số, quyền truy cập nào và xử lý thế nào khi khoảng ngày vượt 180 ngày?","check_ids":["share-unboxing:CHK-018"],"supersedes":"OQ-automation-growth-076"}
```

## OQ-unbox-sharing-042 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-042","type":"NEEDS_CONFIRMATION","feature_id":"share-unboxing","summary":"Khi gỡ app, lịch kiểm tra nguồn đơn có bị xoá và dữ liệu chia sẻ có được giữ không? Cài lại app thì lịch có được tạo lại và link cũ còn dùng được không; dữ liệu chia sẻ có bị xoá theo yêu cầu GDPR không?","check_ids":["share-unboxing:CHK-019"],"supersedes":"OQ-automation-growth-077"}
```

## OQ-unbox-sharing-043 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-043","type":"OPEN_ISSUE","feature_id":"recent-pulls-feed","summary":"Trên staging, khi \"Show recent pulls\" tắt, trang Style Settings → Recent pulls chỉ có công tắc; tài liệu liệt kê thêm Item image shape, Hide item name/chance/price, Image size, Maximum items shown ở màn này. Các thiết lập đó chỉ hiện khi bật công tắc hay không có trên màn hình? Cần quan sát lại với công tắc bật (cần operator cho phép sửa Style Settings rồi khôi phục).","kb_ids":["recent-pulls-feed#KB-082","recent-pulls-feed#KB-006","recent-pulls-feed#KB-045","recent-pulls-feed#KB-046","recent-pulls-feed#KB-047","recent-pulls-feed#KB-048","recent-pulls-feed#KB-049","recent-pulls-feed#KB-051"],"related_oq_ids":["OQ-unbox-sharing-003","OQ-unbox-sharing-019"],"tags":["staging-observed"],"supersedes":"OQ-automation-growth-100"}
```

## OQ-unbox-sharing-044 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-unbox-sharing-044","type":"NEEDS_CONFIRMATION","feature_id":"recent-pulls-feed","summary":"Staging (công tắc tắt): block recent pulls vẫn mount nhưng rỗng, và lượt mở của đơn test không vào feed. Khi bật \"Show recent pulls\", feed có được nạp bằng lời gọi addFeed inline (Liquid) như cấu trúc này không, và box Sealed box có bao giờ hiện entry không?","kb_ids":["recent-pulls-feed#KB-083","recent-pulls-feed#KB-084","recent-pulls-feed#KB-085"],"check_ids":["recent-pulls-feed:CHK-031"],"tags":["staging-observed"],"supersedes":"OQ-automation-growth-101"}
```

## OQ-unbox-sharing-045 — OPEN_ISSUE

```json
{"oq_id":"OQ-unbox-sharing-045","type":"OPEN_ISSUE","feature_id":"share-unboxing","summary":"Khách vãng lai (vào trang reveal bằng magic link) thấy nút \"Share unboxing\" sau khi mở box — bấm thì tạo được link/ảnh, bị chặn (thông báo gì), hay nút lẽ ra phải ẩn với guest? — Tài liệu nói chỉ khách đã đăng nhập chia sẻ được (KB-016/KB-017) nhưng staging hiện nút cho guest; không có expected result cho nhánh guest bấm Share.","kb_ids":["share-unboxing#KB-152","share-unboxing#KB-016","share-unboxing#KB-017"],"tags":["staging-observed"],"supersedes":"OQ-automation-growth-102"}
```
