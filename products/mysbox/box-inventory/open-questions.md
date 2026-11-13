# Open Questions — box-inventory

## OQ-box-inventory-001 — CONFLICT

```json
{"oq_id":"OQ-box-inventory-001","type":"CONFLICT","feature_id":"pool-refill","summary":"Mâu thuẫn nội bộ trong tài liệu pool refill: bảng \"Item nào được trả\" nói các chỉnh sửa box (box vẫn ở pool) giữa lúc mua và lúc resell vẫn trả item về pool, trong khi mục khác biệt production/staging nói trên production mọi chỉnh sửa sinh version mới đều làm lượt trả bị bỏ qua âm thầm (một known defect). Cần dev xác nhận bảng chỉ đúng cho staging (khớp queue token) hay không, và trên production các chỉnh sửa đó có sinh version mới và làm mất lượt trả không.","side_a":"Tài liệu \"Pool refill — trả item đã resell về pool\" §Item nào được trả, item nào không: đổi cài đặt hiển thị/animation, đổi chế độ nhóm, thêm/bớt item khác, đổi deactivate/draft (box vẫn ở pool), hoặc item bị bỏ rồi thêm lại trước khi resell — item vẫn được trả lại (bảng không ghi môi trường).","side_b":"Cùng tài liệu §Khác biệt production / staging (đồng thuận với Playbook 2 §Món đã bán lại không về pool , \"Box version — bản chụp cấu hình\" §Version và pool refill và \"Job chạy định kỳ và lệnh vận hành\" §3. Lệnh artisan — cần engineer): trên production chỉ cần box được sửa (sinh version mới) giữa lúc khách mua và lúc resell là lượt trả item bị bỏ qua âm thầm.","conflict_group":"CONF-box-03","kb_ids":["pool-refill#KB-038","pool-refill#KB-039","pool-refill#KB-040","pool-refill#KB-041","pool-refill#KB-042","pool-refill#KB-043","pool-refill#KB-044"],"check_ids":["pool-refill:CHK-017"],"supersedes":"OQ-box-004"}
```

## OQ-box-inventory-002 — CONFLICT

```json
{"oq_id":"OQ-box-inventory-002","type":"CONFLICT","feature_id":"pool-refill","summary":"Hai tài liệu nêu khác nhau về điều kiện dừng-khi-cạn để pool refill áp dụng: một bên bắt buộc chọn \"Automatically deactivate box\", bên kia chấp nhận tick \"Draft product when empty\" hoặc \"Deactivate box when empty\". Cần dev xác nhận box chỉ bật draft-when-empty (không deactivate) có được refill không.","side_a":"Tài liệu \"Pool refill — trả item đã resell về pool\" §Khi nào refill áp dụng: refill cần đủ ba điều kiện cùng lúc, trong đó box phải chọn \"Automatically deactivate box\".","side_b":"Tài liệu \"Playbook 2: resell, số tiền hoàn, pool refill, store credit\" §Món đã bán lại không về pool (refill): box Tier picking mode Pool phải được tick \"Draft product when empty\" HOẶC \"Deactivate box when empty\".","conflict_group":"CONF-box-04","kb_ids":["pool-refill#KB-011","pool-refill#KB-012","pool-refill#KB-013"],"check_ids":["pool-refill:CHK-016"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-005 / CONF-box-04: Shop gói Free: form không hiện option refill, deactivate/draft-when-empty hay pool; buyback khoá. Không có evidence cho phía nào.","staging_observation_kb_ids":["pool-refill#KB-053","pool-refill#KB-011","pool-refill#KB-012","pool-refill#KB-013"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-box-005"}
```

## OQ-box-inventory-003 — CONFLICT

```json
{"oq_id":"OQ-box-inventory-003","type":"CONFLICT","feature_id":"pool-refill","summary":"Hai tài liệu nêu khác nhau về bên áp dụng bộ đệm refill kiểu MANUAL: một bên nói merchant áp dụng, bên kia nói người vận hành gọi API (không có màn hình portal). Cần dev xác nhận merchant có cách nào tự áp dụng bộ đệm không, hay chỉ Mysbox team/support qua API.","side_a":"Tài liệu \"Playbook 2: resell, số tiền hoàn, pool refill, store credit\" §Món đã bán lại không về pool (refill): ở chế độ Manual, món bán lại nằm trong bộ đệm chờ merchant áp dụng (box vẫn hết hàng cho đến khi merchant áp dụng).","side_b":"Tài liệu \"Pool refill — trả item đã resell về pool\" §AUTO và MANUAL: ở kiểu MANUAL người vận hành gọi API áp dụng bộ đệm (chọn được từng item/số lượng); kiểu MANUAL không có màn hình portal, đặt bởi API/Mysbox team.","conflict_group":"CONF-box-05","kb_ids":["pool-refill#KB-021","pool-refill#KB-022"],"check_ids":["pool-refill:CHK-009"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-006 / CONF-box-05: Không thấy lựa chọn refill AUTO/MANUAL hay thao tác áp dụng bộ đệm trong portal merchant (gói Free). Không có evidence cho phía nào.","staging_observation_kb_ids":["pool-refill#KB-053","pool-refill#KB-021","pool-refill#KB-022"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-box-006"}
```

## OQ-box-inventory-004 — CONFLICT

```json
{"oq_id":"OQ-box-inventory-004","type":"CONFLICT","feature_id":"pool-refill","summary":"Có bao nhiêu lệnh vận hành chỉ có trên nhánh build-staging? Mâu thuẫn nội bộ trong tài liệu job nền: câu hỏi thường gặp nói \"hai lệnh\", bảng lệnh chỉ gắn thẻ chỉ-có-trên-staging cho một lệnh (backfill token hàng đợi của pool refill). Cần dev xác nhận lệnh thứ hai, hoặc \"hai lệnh\" có tính lượt --dry-run và lượt chạy thật của cùng một lệnh hay không.","side_a":"Tài liệu \"Job chạy định kỳ và lệnh vận hành\" §Câu hỏi thường gặp: hai lệnh chỉ có trên staging và dòng lịch kiểm tra nguồn đơn.","side_b":"Tài liệu \"Job chạy định kỳ và lệnh vận hành\" §3. Lệnh artisan: chỉ dòng lệnh backfill token hàng đợi của pool refill mang thẻ chỉ có trên staging.","conflict_group":"CONF-admin-panel-01","kb_ids":["pool-refill#KB-050"],"supersedes":"OQ-box-007"}
```

## OQ-box-inventory-005 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-005","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Tài liệu mô tả một hạn chế đã biết: nếu shop cho phép \"continue selling when out of stock\", đơn bán vượt tồn kho có thể nhận ít prize hơn số hộp đã mua (hộp thừa không có gì để reveal). Cần dev xác nhận đây là lỗi hay thiết kế chủ đích, mức độ ảnh hưởng và trạng thái sửa; item này không dùng làm expected result.","kb_ids":["inventory-and-sold-out#KB-038"],"check_ids":["inventory-and-sold-out:CHK-035"],"supersedes":"OQ-box-033"}
```

## OQ-box-inventory-006 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-006","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Tài liệu mô tả một hạn chế đã biết: đơn nhiều hộp mà một nhóm cạn giữa chừng có thể có hộp \"rỗng\". Cần dev xác nhận đây là lỗi hay thiết kế chủ đích, mức độ ảnh hưởng và trạng thái sửa; item này không dùng làm expected result.","kb_ids":["inventory-and-sold-out#KB-049"],"check_ids":["inventory-and-sold-out:CHK-036"],"supersedes":"OQ-box-034"}
```

## OQ-box-inventory-007 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-007","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Tài liệu mô tả một hạn chế đã biết: đồng bộ và bốc thăm không dùng chung khoá, nên sync giữa lúc đang bán có thể chạy đua nhẹ với bốc thăm; mức độ ảnh hưởng thực tế được tài liệu tự khai là chưa xác nhận. Cần dev xác nhận đây là lỗi hay thiết kế chủ đích, mức độ ảnh hưởng và trạng thái sửa; item này không dùng làm expected result.","kb_ids":["inventory-and-sold-out#KB-059"],"check_ids":["inventory-and-sold-out:CHK-037"],"supersedes":"OQ-box-035"}
```

## OQ-box-inventory-008 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-008","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Tài liệu mô tả một hạn chế đã biết: triệu chứng đã biết là box Tier có thể rút không ra quà vì mất inventory. Cần dev xác nhận đây là lỗi hay thiết kế chủ đích, mức độ ảnh hưởng và trạng thái sửa; item này không dùng làm expected result.","kb_ids":["inventory-and-sold-out#KB-073"],"check_ids":["inventory-and-sold-out:CHK-038"],"supersedes":"OQ-box-036"}
```

## OQ-box-inventory-009 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-009","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Khi box tracked/pool hết tồn kho, điều kiện nào dẫn tới sold-out, tự deactivate, hay refill? — Sơ đồ chỉ liệt kê ba kết cục, không có điều kiện cho từng kết cục — không viết được expected result tổng quát.","kb_ids":["inventory-and-sold-out#KB-006"],"supersedes":"OQ-box-037"}
```

## OQ-box-inventory-010 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-010","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Tồn kho box giảm tại thời điểm nào (đơn paid, lúc bốc, hay lúc reveal) và giảm bao nhiêu mỗi đơn? — Kiểm tồn kho sau mua cần mốc thời gian và lượng giảm.","kb_ids":["inventory-and-sold-out#KB-001"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-038: 2026-10-17: inventory.bundles/Remaining giảm đúng item trúng: B1 2/2/1 → 1/1/0 sau đơn 3 box, B2 mỗi set giảm 1, B3 4 → 1 sau 3 box sealed. Không có mốc \"ngay sau paid, trước khi mở\" cho box digital.","staging_observation_kb_ids":["inventory-and-sold-out#KB-090"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-box-038"}
```

## OQ-box-inventory-011 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-011","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Dựng lại tồn kho khi tạo version mới ảnh hưởng thế nào tới pool/tồn kho đã trừ của đơn chưa mở? — Side effect trên inventory khi sửa box đang có đơn chưa mở.","kb_ids":["inventory-and-sold-out#KB-024","inventory-and-sold-out#KB-026"],"supersedes":"OQ-box-039"}
```

## OQ-box-inventory-012 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-012","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Giới hạn số lần ghi Shopify mỗi giây mỗi shop và độ trễ tối đa của hiển thị tồn kho trên widget là bao nhiêu, cơ chế cập nhật thế nào? — 'vài giây' không đủ làm boundary để kiểm độ trễ.","kb_ids":["inventory-and-sold-out#KB-070"],"supersedes":"OQ-box-040"}
```

## OQ-box-inventory-013 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-013","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Công thức chia lại chance cho các nhóm còn lại khi chọn \"Continuously randomize items in the remaining groups\" với hơn hai nhóm? — Tài liệu chỉ có ví dụ hai nhóm; không đủ làm oracle cho trường hợp tổng quát.","kb_ids":["inventory-and-sold-out#KB-045","inventory-and-sold-out#KB-048"],"supersedes":"OQ-box-041"}
```

## OQ-box-inventory-014 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-014","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Toàn văn thông báo lỗi \"Box tracking settings do not match...\" là gì? — Tài liệu cắt bằng '...'; không kiểm khớp nguyên văn được.","kb_ids":["inventory-and-sold-out#KB-033"],"supersedes":"OQ-box-042"}
```

## OQ-box-inventory-015 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-015","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Box Bundle tracked có dùng được \"Show remaining stock\" hoặc availability không? — Tài liệu chỉ nêu Single tracked, Group pool và Bundle untracked; thiếu expected cho Bundle tracked.","kb_ids":["inventory-and-sold-out#KB-065","inventory-and-sold-out#KB-069"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-043: 2026-10-17: Tuỳ chọn là radio \"Show remaining stock\" trong mục \"Chance display\" của form box (Single, Sealed và cả Bundle), không bị disable, mặc định \"Show original chance\"; không hiện ở group mode. Card \"Item list\" của Style Settings chưa mở.","staging_observation_kb_ids":["inventory-and-sold-out#KB-093","inventory-and-sold-out#KB-094"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-box-043"}
```

## OQ-box-inventory-016 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-016","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"\"Draft product when empty\" và \"Deactivate box when empty\" trong Configure Tier Settings chỉ áp dụng cho Picking Mode BasePool hay cả Draw? — Phạm vi không rõ, ảnh hưởng ma trận test Configure Tier Settings.","kb_ids":["inventory-and-sold-out#KB-019"],"supersedes":"OQ-box-044"}
```

## OQ-box-inventory-017 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-017","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Toast \"Cannot publish: inventory pools are exhausted.\" (và toast yêu cầu sync xong mới publish) hiện ở portal hay admin panel? — Surface của check publish chưa rõ.","kb_ids":["inventory-and-sold-out#KB-053"],"supersedes":"OQ-box-045"}
```

## OQ-box-inventory-018 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-018","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Khi sync lại pool theo collection, con trỏ bốc được dời tới đâu và món bị gỡ khỏi collection được xử lý thế nào? — Cần để kiểm hành vi giữ item đã bốc và xáo phần còn lại.","kb_ids":["inventory-and-sold-out#KB-057","inventory-and-sold-out#KB-058"],"supersedes":"OQ-box-046"}
```

## OQ-box-inventory-019 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-019","type":"OPEN_ISSUE","feature_id":"picking-modes","summary":"Ở mode mặc định, một hộp Bundle có nhận được cùng một item từ các set khác nhau không? — Tài liệu nêu khả năng này ở dạng chưa xác nhận; ảnh hưởng expected của Bundle có item trùng giữa các set.","kb_ids":["picking-modes#KB-023"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-047: 2026-10-17: Form Bundle không chặn cùng một item ở 2 set khi tồn kho box 1 (không cảnh báo, Save bật); run không lưu cấu hình này nên không có đơn để xem A+A hay lỗi.","staging_observation_kb_ids":["picking-modes#KB-056"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-box-047"}
```

## OQ-box-inventory-020 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-020","type":"OPEN_ISSUE","feature_id":"picking-modes","summary":"Với Bundle nhiều set, \"Unique in an order\" tính unique theo từng set hay trên toàn hộp/toàn đơn? — Ví dụ chỉ dùng một set; Bundle nhiều set không được minh hoạ.","kb_ids":["picking-modes#KB-026"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-048: 2026-10-17: Bundle 3 set bật Unique, đơn 2 box: trong từng set hai hộp nhận item khác nhau, mỗi hộp 1 item/set; các set không có item chung và đơn chỉ 2 box nên chưa phân biệt unique theo set hay theo hộp.","staging_observation_kb_ids":["picking-modes#KB-055"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-box-048"}
```

## OQ-box-inventory-021 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-021","type":"OPEN_ISSUE","feature_id":"picking-modes","summary":"\"Unique in an order\" có áp dụng khi một đơn chứa nhiều hộp thuộc các variant/box khác nhau không? — Tài liệu chỉ nói có ý nghĩa với nhiều hộp cùng variant; hành vi đơn trộn không được nêu.","kb_ids":["picking-modes#KB-028"],"supersedes":"OQ-box-049"}
```

## OQ-box-inventory-022 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-022","type":"OPEN_ISSUE","feature_id":"picking-modes","summary":"Nhãn bảng \"Refill / Redistribute / Deactivate\" ánh xạ chính xác thế nào với ba lựa chọn UI (đặc biệt Redistribute ↔ \"Continuously randomize items in the remaining groups\")? — Tài liệu không nói thẳng ánh xạ; suy theo thứ tự hàng là phỏng đoán.","kb_ids":["picking-modes#KB-037","picking-modes#KB-040"],"supersedes":"OQ-box-050"}
```

## OQ-box-inventory-023 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-023","type":"OPEN_ISSUE","feature_id":"picking-modes","summary":"Đổi picking mode trên box đã publish/đã bán áp dụng cho đơn cũ hay chỉ version mới; mode có nằm trong box version không? — Ảnh hưởng tính bất biến của bốc thăm (prize-draw là topic không được supersede).","kb_ids":["picking-modes#KB-016"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-051: 2026-10-17: picking_mode \"unique\" khi bật, null khi tắt — thấy ở POST/GET và box version lúc tạo; bật/tắt rồi Save (PUT) và so version mới/cũ không làm.","staging_observation_kb_ids":["picking-modes#KB-053"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-box-051"}
```

## OQ-box-inventory-024 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-024","type":"OPEN_ISSUE","feature_id":"picking-modes","summary":"Đổi qua lại giữa Single và Bundle, hoặc giữa draw và pool, có reset danh sách item không? — Tài liệu chỉ nêu trường hợp đổi single item → group.","kb_ids":["picking-modes#KB-034","picking-modes#KB-036"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-052: 2026-10-17: Đổi Single item ↔ group reset item cả hai chiều; draw ↔ pool không có trên form gói Free.","staging_observation_kb_ids":["box-type-and-prize-setup#KB-065"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-box-052"}
```

## OQ-box-inventory-025 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-025","type":"OPEN_ISSUE","feature_id":"pool-refill","summary":"Tài liệu mô tả một hạn chế đã biết: box được lưu trước khi có tuỳ chọn refill có thể hiển thị \"Automatically refill\" trên giao diện trong khi server coi refill là tắt cho tới khi form được lưu lại (giao diện và server lệch nhau). Cần dev xác nhận đây là lỗi hay thiết kế chủ đích, mức độ ảnh hưởng và trạng thái sửa; item này không dùng làm expected result.","kb_ids":["pool-refill#KB-017"],"check_ids":["pool-refill:CHK-020"],"supersedes":"OQ-box-053"}
```

## OQ-box-inventory-026 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-026","type":"OPEN_ISSUE","feature_id":"pool-refill","summary":"Support bật kiểu MANUAL ở đâu (admin panel hay cách khác), và đổi AUTO ↔ MANUAL ảnh hưởng thế nào tới bộ đệm đang chờ? — Chuyển cấu hình có thể làm mất hoặc tự áp dụng item đang chờ; check permission cần biết surface.","kb_ids":["pool-refill#KB-007","pool-refill#KB-020"],"supersedes":"OQ-box-054"}
```

## OQ-box-inventory-027 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-027","type":"OPEN_ISSUE","feature_id":"pool-refill","summary":"Nhãn đầy đủ của lựa chọn \"Not refill...\" là gì? — Tài liệu cắt bằng '...'; không có oracle cho nhãn UI nguyên văn.","kb_ids":["pool-refill#KB-008"],"supersedes":"OQ-box-055"}
```

## OQ-box-inventory-028 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-028","type":"OPEN_ISSUE","feature_id":"pool-refill","summary":"Sau refill, box đã deactivate có tự Activate lại không hay merchant phải bấm Activate? — Tài liệu chỉ nói 'có thể được Activate lại'; ví dụ cho thấy merchant Activate.","kb_ids":["pool-refill#KB-031"],"supersedes":"OQ-box-056"}
```

## OQ-box-inventory-029 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-029","type":"OPEN_ISSUE","feature_id":"pool-refill","summary":"Job AUTO áp dụng bộ đệm chạy với độ trễ bao lâu, retry/thất bại thì sao? — 'ngay' không định lượng; ảnh hưởng thời điểm kiểm tra pool sau resell.","kb_ids":["pool-refill#KB-019"],"supersedes":"OQ-box-057"}
```

## OQ-box-inventory-030 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-030","type":"NEEDS_CONFIRMATION","feature_id":"inventory-and-sold-out","summary":"Tài liệu tồn kho nêu một mẹo chuyển box pool → draw → pool để tạo hàng đợi mới cho box đã cạn nhưng tự khai chưa xác nhận đây có phải quy trình support chính thức. Cần dev/support xác nhận mẹo này có được dùng chính thức không và hàng đợi sau khi chuyển hoạt động thế nào.","kb_ids":["inventory-and-sold-out#KB-054"],"supersedes":"OQ-box-069"}
```

## OQ-box-inventory-031 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-031","type":"NEEDS_CONFIRMATION","feature_id":"inventory-and-sold-out","summary":"Không thấy ô chỉnh cờ show_item_availability trong portal; tài liệu tự khai chưa xác nhận ai bật cờ (có thể là Mysbox team). Cần dev xác nhận ai bật cờ này và bật ở đâu.","kb_ids":["inventory-and-sold-out#KB-068"],"supersedes":"OQ-box-070"}
```

## OQ-box-inventory-032 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-032","type":"NEEDS_CONFIRMATION","feature_id":"inventory-and-sold-out","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["inventory-and-sold-out:CHK-001","inventory-and-sold-out:CHK-002","inventory-and-sold-out:CHK-003","inventory-and-sold-out:CHK-004","inventory-and-sold-out:CHK-005","inventory-and-sold-out:CHK-006","inventory-and-sold-out:CHK-007","inventory-and-sold-out:CHK-010","inventory-and-sold-out:CHK-011","inventory-and-sold-out:CHK-012","inventory-and-sold-out:CHK-013","inventory-and-sold-out:CHK-015","inventory-and-sold-out:CHK-022","inventory-and-sold-out:CHK-023","inventory-and-sold-out:CHK-030","inventory-and-sold-out:CHK-033"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-071: 2026-10-17: Remaining giảm đúng item trúng (Single và Bundle tracked); item về 0 hiện Chance 0%, item khác giữ chance gốc; sau bán product vẫn available và widget không đổi. Box untracked và Sold out không quan sát.","staging_observation_kb_ids":["inventory-and-sold-out#KB-090","inventory-and-sold-out#KB-091"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-box-071"}
```

## OQ-box-inventory-033 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-033","type":"NEEDS_CONFIRMATION","feature_id":"inventory-and-sold-out","summary":"Mẹo chuyển box Group đã cạn từ pool sang draw rồi về pool để tạo hàng đợi mới có phải quy trình support chính thức không? Sau khi chuyển, hàng đợi các nhóm có đầy đủ lại item không và box có Activate được không?","check_ids":["inventory-and-sold-out:CHK-018"],"supersedes":"OQ-box-072"}
```

## OQ-box-inventory-034 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-034","type":"NEEDS_CONFIRMATION","feature_id":"inventory-and-sold-out","summary":"Ai bật cờ show_item_availability cho box và bật ở đâu (portal không có ô chỉnh)? Cần biết để dựng được precondition kiểm nhãn \"Pulled\" và \"N of M pulled\".","kb_ids":["inventory-and-sold-out#KB-066","inventory-and-sold-out#KB-067"],"check_ids":["inventory-and-sold-out:CHK-028"],"supersedes":"OQ-box-073"}
```

## OQ-box-inventory-035 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-035","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Picking mode \"Unique across pools\" (box Bundle có cùng item ở nhiều set) chỉ có trên nhánh build-staging, chưa lên production; mọi mô tả hành vi của mode này chưa dùng được làm expected result production. Cần dev xác nhận khi nào mode lên production, cách đặt mode cho box (API/Mysbox team) và hành vi production lúc đó.","kb_ids":["picking-modes#KB-001","picking-modes#KB-002","picking-modes#KB-003","picking-modes#KB-004","picking-modes#KB-005","picking-modes#KB-006","picking-modes#KB-007","picking-modes#KB-008","picking-modes#KB-009","picking-modes#KB-010","picking-modes#KB-011","picking-modes#KB-012","picking-modes#KB-013","picking-modes#KB-014","picking-modes#KB-015"],"supersedes":"OQ-box-074"}
```

## OQ-box-inventory-036 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-036","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Tài liệu tự khai chưa xác nhận bên nào đặt pick_count khác 1 (portal không có ô chỉnh). Cần dev xác nhận ai/qua đâu đặt pick_count và hành vi khi pick_count > 1.","kb_ids":["picking-modes#KB-046"],"supersedes":"OQ-box-075"}
```

## OQ-box-inventory-037 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-037","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["picking-modes:CHK-002","picking-modes:CHK-003","picking-modes:CHK-004","picking-modes:CHK-005","picking-modes:CHK-006","picking-modes:CHK-007","picking-modes:CHK-010","picking-modes:CHK-011","picking-modes:CHK-013"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-076: 2026-10-17: B1 Single tracked bật Unique, đơn 3 box: 3 item khác nhau, Remaining 2/2/1 → 1/1/0; B2 mỗi set giảm 1 ở item trúng. Cấu hình {A,B} đặt lại khi hết và pool chưa quan sát.","staging_observation_kb_ids":["inventory-and-sold-out#KB-090","picking-modes#KB-054","picking-modes#KB-055"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-box-076"}
```

## OQ-box-inventory-038 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-038","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"\"Unique in an order\" có áp dụng khi một đơn chứa nhiều hộp thuộc các variant/box khác nhau không, hay chỉ trong phạm vi các hộp cùng variant?","check_ids":["picking-modes:CHK-009"],"supersedes":"OQ-box-077"}
```

## OQ-box-inventory-039 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-039","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Ai và qua kênh nào đặt pick_count khác 1? Khi pick_count lớn hơn 1, các item trong một lần tung có được trùng nhau không, tương tác với draw/pool thế nào, và nếu nhóm còn ít item hơn pick_count thì sao?","check_ids":["picking-modes:CHK-015"],"supersedes":"OQ-box-078"}
```

## OQ-box-inventory-040 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-040","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Picking Mode Draw/BasePool và Tier Mode Shared/Independent ở admin panel ánh xạ chính xác thế nào với các lựa chọn của merchant trong portal (draw/pool và ba lựa chọn khi nhóm cạn, kể cả nhãn Refill / Redistribute / Deactivate)? Khi hai surface lệch nhau thì surface nào là nguồn sự thật?","check_ids":["picking-modes:CHK-017"],"supersedes":"OQ-box-079"}
```

## OQ-box-inventory-041 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-041","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Đổi picking mode trên box đã publish/đã bán có ảnh hưởng tới các đơn đã có quà hay chỉ áp dụng cho đơn mới? Picking mode có nằm trong bản chụp version của box không?","check_ids":["picking-modes:CHK-018"],"supersedes":"OQ-box-080"}
```

## OQ-box-inventory-042 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-042","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Ở mode Mặc định, một hộp Bundle có thể nhận cùng một item từ các set khác nhau không (ví dụ A ở set 1 và A ở set 2)?","check_ids":["picking-modes:CHK-019"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-081: 2026-10-17: Như OQ-box-047: form không chặn item trùng giữa 2 set; không lưu, không đặt đơn.","staging_observation_kb_ids":["picking-modes#KB-056"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-box-081"}
```

## OQ-box-inventory-043 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-043","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Khi nào picking mode \"Unique across pools\" lên production? Trên production, với box Bundle có cùng item ở nhiều set, mode này có đảm bảo một hộp không chứa cùng item hai lần (với cấu hình ví dụ thì cả 3 hộp đều là một A và một B) không?","check_ids":["picking-modes:CHK-020"],"supersedes":"OQ-box-082"}
```

## OQ-box-inventory-044 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-044","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Với \"Unique across pools\", số hộp chứa một item có luôn bằng floor hoặc ceil của tổng số đơn vị item đó chia cho số hộp còn lại không (với cấu hình ví dụ: C ở cả 3 hộp, A ở 2 hộp, B ở 1 hộp), và hành vi này có giữ nguyên khi lên production không?","check_ids":["picking-modes:CHK-021"],"supersedes":"OQ-box-083"}
```

## OQ-box-inventory-045 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-045","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Khi \"Unique across pools\" để một hộp rỗng vì mọi phương án đều không chia được: khách thấy gì, đơn và yêu cầu mở hộp xử lý ra sao, tồn kho và phí sử dụng có bị tính không? Cấu hình nào tái hiện được tình huống này?","check_ids":["picking-modes:CHK-022"],"supersedes":"OQ-box-084"}
```

## OQ-box-inventory-046 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-046","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Với \"Unique across pools\" và item untracked, ứng viên có được xếp hạng theo số lần đã ra trong lượt rồi mới ngẫu nhiên theo chance không, \"lượt\" được đặt lại khi nào, và khi hết cách tránh trùng thì ứng viên tốt nhất được chọn theo tiêu chí gì?","check_ids":["picking-modes:CHK-023"],"supersedes":"OQ-box-085"}
```

## OQ-box-inventory-047 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-047","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Kênh đặt \"Unique across pools\" cho một box là gì (route, method, field, vai trò được gọi)? Có đúng merchant không có màn hình bật mode này trong portal và box mới mặc định không dùng mode này không, kể cả khi lên production?","check_ids":["picking-modes:CHK-024"],"supersedes":"OQ-box-086"}
```

## OQ-box-inventory-048 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-048","type":"NEEDS_CONFIRMATION","feature_id":"pool-refill","summary":"Cơ chế khớp refill theo queue token (refill gắn với hàng đợi, không gắn version) và bản sửa cho lượt refill bị mất chỉ có trên nhánh build-staging, chưa lên production. Cần dev xác nhận khi nào thay đổi này lên production và hành vi refill trên production sau khi lên (box đổi version giữa lúc mua và resell có còn mất lượt trả không).","kb_ids":["pool-refill#KB-046","pool-refill#KB-047","pool-refill#KB-048","pool-refill#KB-049"],"supersedes":"OQ-box-087"}
```

## OQ-box-inventory-049 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-049","type":"NEEDS_CONFIRMATION","feature_id":"pool-refill","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["pool-refill:CHK-003","pool-refill:CHK-004","pool-refill:CHK-005","pool-refill:CHK-007","pool-refill:CHK-008","pool-refill:CHK-010","pool-refill:CHK-011","pool-refill:CHK-012","pool-refill:CHK-013","pool-refill:CHK-014","pool-refill:CHK-015"],"supersedes":"OQ-box-088"}
```

## OQ-box-inventory-050 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-050","type":"NEEDS_CONFIRMATION","feature_id":"pool-refill","summary":"Sau khi refill trả item về nhóm đã cạn, box đang bị deactivate có tự Activate lại không hay merchant phải bấm Activate? Khi Activate, kiểm tra pool cạn có cho qua và khách kế tiếp có thể trúng item vừa được trả không?","check_ids":["pool-refill:CHK-006"],"supersedes":"OQ-box-089"}
```

## OQ-box-inventory-051 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-051","type":"NEEDS_CONFIRMATION","feature_id":"pool-refill","summary":"Cơ chế khớp refill theo hàng đợi (mỗi hàng đợi pool có mã nhận dạng, item được trả nếu mã khớp hàng đợi hiện tại) và bản sửa cho lượt refill bị mất hiện chỉ có trên build-staging. Khi nào thay đổi này lên production, và trên production sau khi lên, box đổi version giữa lúc mua và resell có còn làm mất lượt trả không?","check_ids":["pool-refill:CHK-021"],"supersedes":"OQ-box-090"}
```

## OQ-box-inventory-052 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-052","type":"NEEDS_CONFIRMATION","feature_id":"inventory-and-sold-out","summary":"Sau khi quà box digital được thêm vào đơn, inventory_quantity Shopify của variant quà về 0/-1 (variant không track). Đây là hiệu ứng order edit của Shopify hay Mysbox có trừ tồn kho Shopify với box digital (KB-072 nói không trừ)?","kb_ids":["inventory-and-sold-out#KB-089","inventory-and-sold-out#KB-072","inventory-and-sold-out#KB-002"],"check_ids":["inventory-and-sold-out:CHK-039"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-093: 2026-10-17: Prize của #1007/#1008 là \"Inventory not tracked\" nên không có lịch sử tồn kho; với prize tracked của đơn sealed trong run, thay đổi tồn kho ghi \"Inventory correction\" do \"Staging Mysbox\" tạo (-1, -2), không phải order edit.","staging_observation_kb_ids":["physical-sealed-box-fulfilment#KB-071","inventory-and-sold-out#KB-092"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-box-093"}
```

## OQ-box-inventory-053 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-053","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Cột Chance trên form portal sau khi box đã bán được tính thế nào (theo Original, theo Remaining, hay giữ giá trị lúc lưu) — vì sao Bundle hiện 0% cho item hết nhưng không chuẩn hoá phần còn lại? — Không có expected cho hiển thị chance sau bán trên portal (KB-087).","kb_ids":["inventory-and-sold-out#KB-087"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-099: 2026-10-17: Trước đơn B1 Chance 40.00/40.00/20.00 (Remaining 2/2/1); sau đơn 40.00/40.00/0% (Remaining 1/1/0); B2 mỗi set 66.67%/0%. Item còn hàng giữ chance gốc, item hết hiện 0%, API chance không đổi.","staging_observation_kb_ids":["inventory-and-sold-out#KB-091"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-box-099"}
```

## OQ-box-inventory-054 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-054","type":"OPEN_ISSUE","feature_id":"picking-modes","summary":"settings.picking_mode = null nghĩa là gì (mode mặc định simple/binned, hay chưa cấu hình), và giá trị enum khi bật \"Unique in an order\" là gì? — Không suy được mode từ null; cần để viết check API/data cho picking mode.","kb_ids":["picking-modes#KB-052","picking-modes#KB-017"],"staging_observation":"Ghi chú quan sát staging cho OQ-box-101: 2026-10-17: settings.picking_mode = \"unique\" khi bật \"Unique in an order\", null khi tắt (thấy ở POST/GET lúc tạo box, không phải PUT).","staging_observation_kb_ids":["picking-modes#KB-053"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-box-101"}
```

## OQ-box-inventory-055 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-055","type":"OPEN_ISSUE","feature_id":"pool-refill","summary":"Mục refill (\"When items are resold by customers:\") hiện ở gói nào / điều kiện nào; shop test nào (gói trả phí, có box Group pool, bật buyback) dùng được để kiểm refill? — Gói Free khoá buyback và không hiện mục refill (KB-053); không có môi trường để lập bằng chứng runtime cho feature.","kb_ids":["pool-refill#KB-053"],"supersedes":"OQ-box-102"}
```

## OQ-box-inventory-056 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-056","type":"NEEDS_CONFIRMATION","feature_id":"inventory-and-sold-out","summary":"Sau khi bán, cột Chance trên form box tracked giữ chance gốc (Single) nhưng hiện 0% cho item hết (Bundle) mà không chuẩn hoá phần còn lại về 100%. Cột này nên hiển thị chance gốc hay chance hiện hành, và cách hiển thị không nhất quán giữa Single/Bundle có chủ ý không?","kb_ids":["inventory-and-sold-out#KB-087"],"check_ids":["inventory-and-sold-out:CHK-040"],"supersedes":"OQ-box-113"}
```

## OQ-box-inventory-057 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-057","type":"NEEDS_CONFIRMATION","feature_id":"pool-refill","summary":"Trên gói Free, buyback bị khoá và form box không có mục refill. Mục \"When items are resold by customers:\" chỉ hiện trên gói nào / điều kiện nào (gói trả phí, box Group pool, sau khi lưu)?","kb_ids":["pool-refill#KB-053"],"check_ids":["pool-refill:CHK-022"],"supersedes":"OQ-box-114"}
```

## OQ-box-inventory-058 — CONFLICT

```json
{"oq_id":"OQ-box-inventory-058","type":"CONFLICT","feature_id":"inventory-and-sold-out","summary":"Form Bundle tracked trên staging cho chọn \"Show remaining stock\" (radio không disable) trong khi tài liệu nói chế độ này chỉ dùng được cho Single tracked hoặc Group pool. Lưu Bundle với \"Show remaining stock\" có hợp lệ không và storefront hiển thị gì?","side_a":"Base KB-065 (CE, dev_doc): chế độ \"Show remaining stock\" chỉ dùng được cho box Single tracked hoặc Group pool.","side_b":"Quan sát staging KB-094: form Bundle tracked hiện radio \"Show remaining stock\" bật được (chưa lưu).","conflict_group":"CONF-box-11","kb_ids":["inventory-and-sold-out#KB-065","inventory-and-sold-out#KB-094"],"related_oq_ids":["OQ-box-inventory-015"],"tags":["staging-observed"],"check_ids":["inventory-and-sold-out:CHK-041"],"supersedes":"OQ-box-117"}
```

## OQ-box-inventory-059 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-059","type":"NEEDS_CONFIRMATION","feature_id":"inventory-and-sold-out","summary":"Staging: box Sealed tracked trừ tồn kho box ngay sau đơn (4 → 1 sau 3 box, không có bước mở). Với box digital tracked, tồn kho box bị trừ lúc đơn paid hay lúc khách mở box? (Mẫu box digital chỉ đo sau khi đã mở hết.)","kb_ids":["inventory-and-sold-out#KB-090"],"check_ids":["inventory-and-sold-out:CHK-042"],"tags":["staging-observed"],"supersedes":"OQ-box-125"}
```

## OQ-box-inventory-060 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-060","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Staging: ô \"Unique in an order\" lưu thành settings.picking_mode \"unique\", tắt thì null (quan sát lúc tạo box, chưa thử bật/tắt rồi Save). Bật/tắt ô này trên box đã có rồi lưu có sinh version mới với picking_mode tương ứng không?","kb_ids":["picking-modes#KB-053"],"check_ids":["picking-modes:CHK-025"],"tags":["staging-observed"],"supersedes":"OQ-box-126"}
```

## OQ-box-inventory-061 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-box-inventory-061","type":"NEEDS_CONFIRMATION","feature_id":"picking-modes","summary":"Form Bundle cho chọn cùng một item ở hai set khi tồn kho box chỉ 1 (staging, không chặn, không cảnh báo). Cấu hình này có hợp lệ không; nếu lưu được thì hộp nhận A+A hay lỗi lúc bốc?","kb_ids":["picking-modes#KB-056"],"check_ids":["picking-modes:CHK-026"],"tags":["staging-observed"],"supersedes":"OQ-box-127"}
```

## OQ-box-inventory-062 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-062","type":"OPEN_ISSUE","feature_id":"inventory-and-sold-out","summary":"Storefront ở \"Show original chance\" có nên tiếp tục hiện chance gốc cho item đã hết (Remaining 0) không, trong khi form portal hiện 0% cho item đó? — Hai surface lệch nhau sau khi item hết (KB-091); cần expected để viết check hiển thị cho khách và tránh khách thấy món không còn trúng được.","kb_ids":["inventory-and-sold-out#KB-091","inventory-and-sold-out#KB-061"],"tags":["staging-observed"],"supersedes":"OQ-box-132"}
```

## OQ-box-inventory-063 — OPEN_ISSUE

```json
{"oq_id":"OQ-box-inventory-063","type":"OPEN_ISSUE","feature_id":"picking-modes","summary":"Lưu box Bundle có cùng một item ở nhiều set khi tồn kho item chỉ đủ cho một (vd quantity 1) có bị chặn ở bước Save/server không, và thông báo gì? — Form không cảnh báo (KB-056); nếu Save chấp nhận, kết quả bốc có thể đòi nhiều đơn vị hơn tồn kho — cần expected cho check validation.","kb_ids":["picking-modes#KB-056","picking-modes#KB-023"],"tags":["staging-observed"],"supersedes":"OQ-box-133"}
```
