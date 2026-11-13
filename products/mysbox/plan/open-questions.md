# Open Questions — plan

## OQ-plan-001 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-001","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Bộ tài liệu nguồn không chỉ định role mặc định cho object này (bootstrap-request để role null): các KB item mang scope.role theo vai trò tài liệu nêu cho từng hành vi, hoặc \"unspecified\" khi tài liệu không nêu. Cần PO/Dev xác nhận ma trận role → quyền thực tế trên production (merchant owner/staff, khách, admin Mysbox theo từng role) trước khi dùng các check PERMISSION làm oracle.","supersedes":"OQ-plans-billing-001"}
```

## OQ-plan-002 — CONFLICT

```json
{"oq_id":"OQ-plan-002","type":"CONFLICT","feature_id":null,"summary":"Trong admin panel, nhánh Plans / Charges có phải read-only không: nhãn \"(tiền, read-only)\" trong sơ đồ áp cho Plans, Charges hay cả hai, khi cùng tài liệu nói đội billing/partnership tạo Plan? (Phía còn lại thuộc shard quản trị danh mục plan của cùng object.)","side_a":"Tài liệu \"Admin panel — tổng quan và bản đồ màn hình\" §Sơ đồ tổng quát ghi nhánh Plans / Charges là \"(tiền, read-only)\".","side_b":"Cùng tài liệu \"Admin panel — tổng quan và bản đồ màn hình\" §Ai dùng và dùng để làm gì nêu đội Billing / partnership tạo Plan (cùng Discount, Promote code, gửi link thanh toán).","conflict_group":"CONF-plans-billing-02","kb_ids":["_object-level#KB-020","plan-catalog-administration#KB-011"],"check_ids":["plan-catalog-administration:CHK-013"],"supersedes":"OQ-plans-billing-002"}
```

## OQ-plan-003 — CONFLICT

```json
{"oq_id":"OQ-plan-003","type":"CONFLICT","feature_id":"plan-capacity-and-cycle","summary":"Tài liệu mâu thuẫn về việc box bán trong thời gian trial có trừ quota (capacity) hay không. Cần dev/PO xác nhận hành vi đúng; không dùng phía nào làm oracle cho tới khi xác nhận.","side_a":"Tài liệu \"Plan và capacity (quota)\" §Cái gì tính là 1 box đã dùng và §Trial: đơn trong trial không dùng quota, không trừ quota (chỉ tăng \"sold in cycle\").","side_b":"Tài liệu \"Playbook 4: billing, plan, capacity, mã giảm giá\" §Nhầm lẫn về trial: trong trial box bán ra vẫn được tính vào capacity (dù không có phí usage). Tài liệu \"Trạng thái shop và vòng đời\" §2 chỉ nói \"box bán vẫn đếm\", không rõ đếm vào quota hay vào sold in cycle.","conflict_group":"CONF-plans-billing-07","kb_ids":["plan-capacity-and-cycle#KB-040","plan-capacity-and-cycle#KB-073","plan-capacity-and-cycle#KB-080"],"check_ids":["plan-capacity-and-cycle:CHK-021"],"supersedes":"OQ-plans-billing-007"}
```

## OQ-plan-004 — CONFLICT

```json
{"oq_id":"OQ-plan-004","type":"CONFLICT","feature_id":"plan-capacity-and-cycle","summary":"Trong ví dụ hoá đơn theo số lượng của tài liệu \"Cách tính phí box vượt (usage pricing)\", chỉ số \"Total sold in cycle\" = 145 không khớp tổng các đơn được liệt kê (135) và tổng phí đã gửi (tương đương 35 box vượt). Cần tác giả tài liệu xác nhận số đúng; không dùng 145 làm oracle.","side_a":"Tài liệu \"Cách tính phí box vượt (usage pricing)\" §Hoá đơn 1 — theo số lượng: \"Total sold in cycle\" hiển thị 145.","side_b":"Cùng tài liệu, cùng mục: các đơn liệt kê 95 + 4 + 6 + 3 + 27 = 135 box và tổng phí gửi đi $1.25 + $7.50 = $8.75 (tương đương 35 box vượt × $0.25). Các claim phía này thuộc feature usage-fee-pricing.","conflict_group":"CONF-plans-billing-03","kb_ids":["plan-capacity-and-cycle#KB-050","usage-fee-pricing#KB-045","usage-fee-pricing#KB-048","usage-fee-pricing#KB-049"],"supersedes":"OQ-plans-billing-008"}
```

## OQ-plan-005 — CONFLICT

```json
{"oq_id":"OQ-plan-005","type":"CONFLICT","feature_id":"plan-capacity-and-cycle","summary":"Hai kịch bản ví dụ của tài liệu \"Nâng, hạ, huỷ plan và trang xem trước thay đổi\" dùng hai giá trị quota khác nhau cho cùng plan minh hoạ \"Growth\" ($29). Cả hai là số minh hoạ, không phải số production; cần catalog plan thật nếu muốn làm test data.","side_a":"Tài liệu \"Nâng, hạ, huỷ plan và trang xem trước thay đổi\" §Nâng plan (quota lớn hơn): plan \"Growth\" $29, quota 100, trial 7 ngày, $0.25/box.","side_b":"Cùng tài liệu §Hạ plan (quota nhỏ hơn): plan \"Growth\" $29, quota 50.","conflict_group":"CONF-plans-billing-08","kb_ids":["plan-capacity-and-cycle#KB-052","plan-capacity-and-cycle#KB-057"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-009 / CONF-plans-billing-08: 2026-10-17: Có catalog thật của staging (Free 10, Nitro $24.9/100, Booster $114.9/500, Prime $299.9); Prime tự mâu thuẫn 400 vs 1500 (mở CONF-plans-billing-22). Không phải catalog production.","staging_observation_kb_ids":["plan-capacity-and-cycle#KB-082","plan-capacity-and-cycle#KB-083","plan-capacity-and-cycle#KB-084"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-plans-billing-009"}
```

## OQ-plan-006 — CONFLICT

```json
{"oq_id":"OQ-plan-006","type":"CONFLICT","feature_id":"plan-capacity-and-cycle","summary":"Khi cờ \"Exclude Test Order\" ở trạng thái mặc định (bật), đơn test của Shopify có trừ capacity/quota của shop hay không? Hai phía tài liệu nói trái nhau; không dùng phía nào làm oracle cho tới khi dev/PO xác nhận.","side_a":"Tài liệu \"Plan và capacity (quota)\" §Cái gì tính là 1 box đã dùng và tài liệu \"Overview\" §Key vocabulary: mặc định đơn test của Shopify không tính vào quota/hạn mức (cài đặt \"Exclude Test Order\" bật mặc định). Tài liệu \"Dashboard và analytics\" §Test order cũng nói đơn test chỉ trừ hạn mức khi cờ tắt. Cùng mục đó: preview order được xử lý như đơn test, không tính vào quota khi \"Exclude Test Order\" bật (KB-033).","side_b":"Tài liệu \"Playbook 1: đơn hàng, bốc thăm và mở box\" §Đơn test / preview cư xử lạ: đơn test vẫn bốc thật, tiêu thụ tồn kho và tính vào capacity; điều kiện \"nếu shop bật Exclude test order\" chỉ gắn với việc không tính phí usage, không gắn với capacity.","conflict_group":"CONF-plans-billing-20","kb_ids":["capacity-limit-enforcement#KB-029","plan-capacity-and-cycle#KB-007","plan-capacity-and-cycle#KB-033"],"check_ids":["plan-capacity-and-cycle:CHK-008"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-010 / CONF-plans-billing-20: 2026-10-17: Staging, exclude_test_order true: một đơn Bogus test không làm tăng Box sales limit (0/10 → 0/10, box_sold_in_cycle 0). Một mẫu; preview order không thử.","staging_observation_kb_ids":["plan-capacity-and-cycle#KB-085"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve.","supersedes":"OQ-plans-billing-010"}
```

## OQ-plan-007 — CONFLICT

```json
{"oq_id":"OQ-plan-007","type":"CONFLICT","feature_id":"plan-upgrade-downgrade-cancel","summary":"Mâu thuẫn trong cùng tài liệu: khi nâng từ Free trong thời gian ân hạn mà used vượt quota plan mới, có thực sự phát sinh phí vượt hay khối \"Over capacity fee\" chỉ là số hiển thị tính trong trình duyệt và không bị thu. Cần dev/PO xác nhận.","side_a":"Tài liệu \"Nâng, hạ, huỷ plan và trang xem trước thay đổi\" §Nâng plan (quota lớn hơn): shop Free còn trong ân hạn đã dùng hơn quota plan mới thì hộp thoại nâng hiện thêm khối \"Over capacity fee\".","side_b":"Cùng tài liệu §Hạ plan (quota nhỏ hơn), bảng quy tắc: Free sang Paid giữ used, không tính lại gì.","conflict_group":"CONF-plans-billing-10","kb_ids":["plan-upgrade-downgrade-cancel#KB-045","plan-upgrade-downgrade-cancel#KB-063"],"check_ids":["plan-upgrade-downgrade-cancel:CHK-017"],"supersedes":"OQ-plans-billing-011"}
```

## OQ-plan-008 — CONFLICT

```json
{"oq_id":"OQ-plan-008","type":"CONFLICT","feature_id":"plan-upgrade-downgrade-cancel","summary":"Mâu thuẫn về ngưỡng gỡ publish box trong thời gian ân hạn sau khi huỷ gói trả phí: theo quota Paid còn hiệu lực đến hết kỳ, theo quota Free (gỡ ngay nếu đã vượt), hay gỡ toàn bộ box ngay khi huỷ. Cần dev/PO xác nhận.","side_a":"Tài liệu \"Nâng, hạ, huỷ plan và trang xem trước thay đổi\" §Huỷ plan (chọn Free) và \"Playbook 4: billing, plan, capacity, mã giảm giá\": sau khi huỷ, shop vẫn dùng quota và điều khoản của plan Paid đến hết kỳ đã trả.","side_b":"Cùng tài liệu §Huỷ plan (chọn Free): nếu đã vượt quota Free thì box bị gỡ publish ngay; tài liệu \"Tạo box và vòng đời Draft / Active\" §Bước 5: huỷ gói trả phí cũng làm tất cả box bị tự unpublish.","conflict_group":"CONF-plans-billing-11","kb_ids":["plan-upgrade-downgrade-cancel#KB-084","plan-upgrade-downgrade-cancel#KB-085","plan-upgrade-downgrade-cancel#KB-086"],"check_ids":["plan-upgrade-downgrade-cancel:CHK-024"],"supersedes":"OQ-plans-billing-012"}
```

## OQ-plan-009 — CONFLICT

```json
{"oq_id":"OQ-plan-009","type":"CONFLICT","feature_id":"plan-upgrade-downgrade-cancel","summary":"Mâu thuẫn về gói hiệu lực của shop ngay sau khi gỡ app: về Free ngay, hay vẫn giữ quyền lợi / bị tính usage của gói trả phí trong thời gian ân hạn đến hết kỳ đã trả. Một số tài liệu nêu cả hai ý trong cùng một câu (gói về Free, gói trả phí vẫn còn hạn đến hết kỳ) nên có thể là hai khái niệm khác nhau (nhãn gói và subscription), nhưng tài liệu không nói rõ. Cần dev/PO xác nhận: hạn mức box, tính năng trả phí và phí usage áp theo gói nào trong thời gian ân hạn; và nếu cài lại trong thời gian ân hạn thì hạn mức nào áp dụng (tài liệu tự khai là chưa xác nhận). Ngày hết hạn của charge (cuối kỳ 30 ngày đã trả) không bị tranh chấp.","side_a":"Tài liệu \"Trạng thái shop và vòng đời\" §3. Gỡ app (uninstall), cùng \"Domain entities\", \"Tích hợp: tổng quan và cách xác thực request\", \"Webhook mà app nhận\" và \"Playbook 5: tài khoản, kết nối, gỡ/cài app và tích hợp\": khi gỡ app, gói của shop về Free.","side_b":"Tài liệu \"Trạng thái shop và vòng đời\" (bảng hạn mức: shop đã huỷ gói trả phí còn tính năng trả phí đến hết kỳ đã trả; §Câu hỏi thường gặp: shop đã gỡ app vẫn có thể bị tính usage vì subscription còn ân hạn), cùng \"Tích hợp: tổng quan và cách xác thực request\" và \"Playbook 5: tài khoản, kết nối, gỡ/cài app và tích hợp\": gói trả phí vẫn còn hạn đến hết kỳ đã trả.","conflict_group":"CONF-plans-billing-01","kb_ids":["plan-upgrade-downgrade-cancel#KB-091"],"check_ids":["plan-upgrade-downgrade-cancel:CHK-025"],"supersedes":"OQ-plans-billing-013"}
```

## OQ-plan-010 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-010","type":"OPEN_ISSUE","feature_id":"plan-capacity-and-cycle","summary":"Khi trial kết thúc giữa chu kỳ, box bán sau trial trừ quota từ 0 hay tính cả phần đã bán lúc trial? — Ranh giới chuyển trial sang trả phí chưa được nêu.","kb_ids":["plan-capacity-and-cycle#KB-039","plan-capacity-and-cycle#KB-041"],"supersedes":"OQ-plans-billing-042"}
```

## OQ-plan-011 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-011","type":"OPEN_ISSUE","feature_id":"plan-capacity-and-cycle","summary":"Mốc chu kỳ 30 ngày tính theo múi giờ nào, giờ nào trong ngày, có bao gồm ngày cuối không? — Cần để kiểm thời điểm used đọc về 0 quanh ranh giới chu kỳ.","kb_ids":["plan-capacity-and-cycle#KB-016","plan-capacity-and-cycle#KB-019"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-043: 2026-10-17: Chỉ có một mốc capacity_expires_at (ISO UTC \"Z\") và timezone shop America/New_York; UI không hiện ngày; hành vi quanh ranh giới không chờ được.","staging_observation_kb_ids":["plan-capacity-and-cycle#KB-086","plan-capacity-and-cycle#KB-087"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-plans-billing-043"}
```

## OQ-plan-012 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-012","type":"OPEN_ISSUE","feature_id":"plan-capacity-and-cycle","summary":"Ngưỡng 80% được làm tròn thế nào khi quota không chia hết và so sánh là lớn-hơn-hoặc-bằng hay lớn-hơn; màu thanh tiến độ ở từng mốc? — Boundary test cho cảnh báo \"You almost reach the box limit\".","kb_ids":["plan-capacity-and-cycle#KB-021"],"supersedes":"OQ-plans-billing-044"}
```

## OQ-plan-013 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-013","type":"OPEN_ISSUE","feature_id":"plan-capacity-and-cycle","summary":"Đơn nhiều variant box trừ hạn mức theo thứ tự nào (thứ tự dòng, giá, thời điểm tạo)? — Quyết định dòng nào bị tính phí vượt khi đơn chạm trần giữa chừng.","kb_ids":["plan-capacity-and-cycle#KB-009"],"supersedes":"OQ-plans-billing-045"}
```

## OQ-plan-014 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-014","type":"OPEN_ISSUE","feature_id":"plan-capacity-and-cycle","summary":"Cài đặt \"Exclude Test Order\" nằm ở màn nào, merchant có thấy không, và tiêu chí nhận biết đơn test là gì? — Không rõ surface và dữ liệu để kiểm việc loại trừ.","kb_ids":["plan-capacity-and-cycle#KB-030","plan-capacity-and-cycle#KB-031"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-046: 2026-10-17: Merchant không thấy control Exclude Test Order ở portal; exclude_test_order true trong dữ liệu; app không gắn nhãn test cho đơn Bogus. Màn chứa control (admin panel) và tiêu chí nhận biết đơn test không quan sát.","staging_observation_kb_ids":["plan-capacity-and-cycle#KB-088"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-plans-billing-046"}
```

## OQ-plan-015 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-015","type":"OPEN_ISSUE","feature_id":"plan-capacity-and-cycle","summary":"Early-bird: điều kiện để shop là Founding member, \"giữ nguyên\" nghĩa là gì, 50 box tính theo chu kỳ hay tổng? — Không xác định được phạm vi và boundary của gói.","kb_ids":["plan-capacity-and-cycle#KB-061","plan-capacity-and-cycle#KB-074"],"supersedes":"OQ-plans-billing-047"}
```

## OQ-plan-016 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-016","type":"OPEN_ISSUE","feature_id":"plan-capacity-and-cycle","summary":"Badge \"7 - days free trial\" là số cố định hay lấy từ số ngày trial của plan? — Kiểm hiển thị badge với plan có số ngày trial khác 7.","kb_ids":["plan-capacity-and-cycle#KB-043"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-048: 2026-10-17: Không thẻ nào có badge trial; cả 4 plan trial_days 0. Loại trừ được badge cố định hiện mọi thẻ, nhưng không phân biệt được chữ cố định hay theo số ngày khi trial > 0 (staging không có plan như vậy). | 2026-10-17: Staging không có plan nào trial_days > 0 — không có dữ liệu test cho badge trial trên staging.","staging_observation_kb_ids":["plan-upgrade-downgrade-cancel#KB-114"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-plans-billing-048"}
```

## OQ-plan-017 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-017","type":"OPEN_ISSUE","feature_id":"plan-catalog-administration","summary":"Hạn chế đã biết: nếu thiếu plan mặc định (On install) thì việc cài mới app bị hỏng; tài liệu không nêu panel có chặn lưu khi 0 hoặc nhiều hơn một plan bật On install hay không.","kb_ids":["plan-catalog-administration#KB-033"],"check_ids":["plan-catalog-administration:CHK-011"],"supersedes":"OQ-plans-billing-049"}
```

## OQ-plan-018 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-018","type":"OPEN_ISSUE","feature_id":"plan-catalog-administration","summary":"Hạn chế đã biết: plan trả phí bỏ trống điều khoản usage khiến đơn mới của shop lỗi ngay lúc nhập và đơn không được tạo; tài liệu không nêu form admin có chặn cấu hình này không.","kb_ids":["plan-catalog-administration#KB-035"],"check_ids":["plan-catalog-administration:CHK-012"],"supersedes":"OQ-plans-billing-050"}
```

## OQ-plan-019 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-019","type":"OPEN_ISSUE","feature_id":"plan-catalog-administration","summary":"Giới hạn hợp lệ của price, trial days, Box Selling Capacity, % phí, phí tối thiểu? — Boundary test form admin.","kb_ids":["plan-catalog-administration#KB-026","plan-catalog-administration#KB-028","plan-catalog-administration#KB-029"],"supersedes":"OQ-plans-billing-051"}
```

## OQ-plan-020 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-020","type":"OPEN_ISSUE","feature_id":"plan-catalog-administration","summary":"Quyền trên màn Plans tách riêng xem/tạo/sửa hay một quyền cho cả nhóm? — Quyết định số tổ hợp permission cần kiểm.","kb_ids":["plan-catalog-administration#KB-013"],"supersedes":"OQ-plans-billing-052"}
```

## OQ-plan-021 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-021","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Hạn chế đã biết: các hộp thoại nâng/hạ plan trên màn Pricing tự tính phí theo $0.25/box trong trình duyệt (không dùng endpoint xem trước), nên số tiền hiển thị lệch phí thật với plan có phí khác $0.25 hoặc khi dòng phí không chia đều. Cần dev/PO xác nhận hành vi đúng (hiển thị phí của plan đích) và trạng thái sửa; không dùng số trong hộp thoại làm expected result.","kb_ids":["plan-upgrade-downgrade-cancel#KB-046","plan-upgrade-downgrade-cancel#KB-101","plan-upgrade-downgrade-cancel#KB-102","plan-upgrade-downgrade-cancel#KB-103"],"check_ids":["plan-upgrade-downgrade-cancel:CHK-029"],"supersedes":"OQ-plans-billing-053"}
```

## OQ-plan-022 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-022","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Hạn chế đã biết: Mysbox không nhận thông báo khi subscription đổi trạng thái bên Shopify, nên huỷ, đóng băng hoặc lỗi thanh toán trong Shopify admin chưa phản ánh trong Mysbox (vẫn hiện Active) cho tới khi một luồng của Mysbox chạm tới shop. Cần xác nhận những luồng nào cập nhật lại trạng thái và trạng thái sửa của hạn chế này.","kb_ids":["plan-upgrade-downgrade-cancel#KB-111","plan-upgrade-downgrade-cancel#KB-112","plan-upgrade-downgrade-cancel#KB-113"],"check_ids":["plan-upgrade-downgrade-cancel:CHK-030"],"supersedes":"OQ-plans-billing-054"}
```

## OQ-plan-023 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-023","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Hết kỳ đã trả, shop bị áp capacity Free và có thể vượt capacity — capacity Free ở production là bao nhiêu và chính xác khi nào toàn bộ box bị gỡ? — Phát biểu chưa được xác nhận; số trong ví dụ không dùng làm oracle.","kb_ids":["plan-upgrade-downgrade-cancel#KB-089"],"supersedes":"OQ-plans-billing-055"}
```

## OQ-plan-024 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-024","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Khi chọn lại plan trả phí sau khi huỷ/cài lại, trial có bắt đầu lại không hay chỉ còn số ngày trial chưa dùng (feature này chỉ có ví dụ)? — Expected trial khi đăng ký lại; ví dụ không phải oracle.","kb_ids":["billing-discount-codes#KB-043","plan-upgrade-downgrade-cancel#KB-093","plan-upgrade-downgrade-cancel#KB-094"],"supersedes":"OQ-plans-billing-056"}
```

## OQ-plan-025 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-025","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Shopify xử lý phần chưa dùng của subscription cũ thế nào khi hạ plan? — Quyết định hoá đơn kế tiếp sau khi hạ; tài liệu tự khai chưa xác nhận.","kb_ids":["plan-upgrade-downgrade-cancel#KB-056","plan-upgrade-downgrade-cancel#KB-057"],"supersedes":"OQ-plans-billing-057"}
```

## OQ-plan-026 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-026","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Phí usage tạo trong thời gian ân hạn có bị tính nếu merchant đăng ký lại trong vòng một tháng? — Rủi ro thu dư/thu thiếu khi huỷ rồi đăng ký lại; tài liệu chỉ có suy luận.","kb_ids":["plan-upgrade-downgrade-cancel#KB-088","plan-upgrade-downgrade-cancel#KB-105"],"supersedes":"OQ-plans-billing-058"}
```

## OQ-plan-027 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-027","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Điều gì xảy ra khi merchant từ chối (decline) hoặc đóng trang duyệt của Shopify — plan/charge có bị đổi dở dang không? — Nhánh negative phổ biến, tài liệu không nêu.","kb_ids":["plan-upgrade-downgrade-cancel#KB-019","plan-upgrade-downgrade-cancel#KB-107"],"supersedes":"OQ-plans-billing-059"}
```

## OQ-plan-028 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-028","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Khi link có chữ ký quá hạn 7 ngày hoặc bị dùng lại thì hệ thống phản hồi thế nào (thông báo lỗi)? — Boundary của link xác nhận.","kb_ids":["plan-upgrade-downgrade-cancel#KB-031"],"supersedes":"OQ-plans-billing-060"}
```

## OQ-plan-029 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-029","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Đổi sang plan cùng quota (đi vào nhánh hộp thoại hạ) có tính lại phí không? — Quy tắc 'còn lại = hạ' gộp ca bằng quota; bảng quota không có dòng cho ca bằng.","kb_ids":["plan-upgrade-downgrade-cancel#KB-026","plan-upgrade-downgrade-cancel#KB-059"],"supersedes":"OQ-plans-billing-061"}
```

## OQ-plan-030 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-030","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Nâng plan có làm đổi/reset chu kỳ billing không (chỉ có ví dụ hạ plan nói chu kỳ không đổi)? — Ảnh hưởng used và thời điểm hoá đơn sau nâng.","kb_ids":["plan-upgrade-downgrade-cancel#KB-047","plan-upgrade-downgrade-cancel#KB-074"],"supersedes":"OQ-plans-billing-062"}
```

## OQ-plan-031 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-031","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Ngoài loại store, tiêu chí 'đủ điều kiện chọn plan' gồm những gì và thông báo lỗi cho từng tiêu chí? — Chỉ có thông báo \"Plan is not supported\" cho lọc loại store.","kb_ids":["plan-upgrade-downgrade-cancel#KB-016"],"supersedes":"OQ-plans-billing-063"}
```

## OQ-plan-032 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-032","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Hạ plan hoặc huỷ trong lúc đang trial thì phí tính lại và khoản usage cuối được xử lý thế nào? — Tương tác giữa trial và recalculation không được nêu.","kb_ids":["plan-upgrade-downgrade-cancel#KB-035","plan-upgrade-downgrade-cancel#KB-069","plan-upgrade-downgrade-cancel#KB-079"],"supersedes":"OQ-plans-billing-064"}
```

## OQ-plan-033 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-033","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Sau khi chọn \"Upgrade now\" ở hộp thoại rời Early-bird thì luồng tiếp theo là gì; Early-bird 'giữ nguyên' nghĩa là gì và hạn mức của gói tính theo kỳ hay tổng? — Nhánh UI riêng cho shop Early-bird; phạm vi và boundary của gói chưa rõ.","kb_ids":["plan-upgrade-downgrade-cancel#KB-021","plan-upgrade-downgrade-cancel#KB-023"],"supersedes":"OQ-plans-billing-065"}
```

## OQ-plan-034 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-034","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Khi dev store thành store thật, subscription bị huỷ tự động hay cần thao tác thủ công, và 'plan mặc định' là plan nào? — Không xác định được trigger và trạng thái cuối để viết case.","kb_ids":["plan-upgrade-downgrade-cancel#KB-108","plan-upgrade-downgrade-cancel#KB-110"],"supersedes":"OQ-plans-billing-066"}
```

## OQ-plan-035 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-035","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Khi nâng plan (không phải hạ), box đang vượt có được tính lại phí không? — Tài liệu chỉ nêu recalculation khi hạ.","kb_ids":["plan-upgrade-downgrade-cancel#KB-061"],"supersedes":"OQ-plans-billing-067"}
```

## OQ-plan-036 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-036","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Badge \"7 - days free trial\" là số cố định hay lấy từ số ngày trial của plan? — Kiểm hiển thị badge với plan có số ngày trial khác 7.","kb_ids":["plan-upgrade-downgrade-cancel#KB-006"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-068: 2026-10-17: Như OQ-plans-billing-048: không badge, trial_days 0 mọi plan; câu hỏi cố định hay theo plan chưa trả lời được trên staging.","staging_observation_kb_ids":["plan-upgrade-downgrade-cancel#KB-114"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).","supersedes":"OQ-plans-billing-068"}
```

## OQ-plan-037 — OPEN_ISSUE

```json
{"oq_id":"OQ-plan-037","type":"OPEN_ISSUE","feature_id":"plan-upgrade-downgrade-cancel","summary":"Link thanh toán do admin/support gửi dẫn tới đâu và dùng trong trường hợp nào? — Tài liệu chỉ nêu admin gửi được link, không mô tả luồng.","kb_ids":["_object-level#KB-007","plan-upgrade-downgrade-cancel#KB-043"],"supersedes":"OQ-plans-billing-069"}
```

## OQ-plan-038 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-038","type":"NEEDS_CONFIRMATION","feature_id":"plan-capacity-and-cycle","summary":"Số box miễn phí mỗi chu kỳ thật của plan Free trên production (bộ tài liệu chỉ ghi 10 là giá trị seed, hạn mức thật lấy từ gói mặc định trong DB) và quota thật của các plan trả phí là bao nhiêu? Các con số 10/100 trong tài liệu không dùng làm oracle.","kb_ids":["plan-capacity-and-cycle#KB-003","plan-capacity-and-cycle#KB-008","plan-capacity-and-cycle#KB-046","plan-capacity-and-cycle#KB-047","plan-capacity-and-cycle#KB-064"],"supersedes":"OQ-plans-billing-103"}
```

## OQ-plan-039 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-039","type":"NEEDS_CONFIRMATION","feature_id":"plan-capacity-and-cycle","summary":"Cần xác nhận các phát biểu có rào đón về bộ đếm quota: Used/Box Capacity Used có thể vượt nhẹ quota đúng bằng đơn gây vượt; \"tháng\" quota thường lệch ngày hoá đơn Shopify; sau khi gỡ và cài lại, số đếm có thể đang ở giữa chu kỳ với giá trị cũ.","kb_ids":["plan-capacity-and-cycle#KB-025","plan-capacity-and-cycle#KB-051","plan-capacity-and-cycle#KB-059"],"supersedes":"OQ-plans-billing-104"}
```

## OQ-plan-040 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-040","type":"NEEDS_CONFIRMATION","feature_id":"plan-capacity-and-cycle","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["plan-capacity-and-cycle:CHK-001","plan-capacity-and-cycle:CHK-002","plan-capacity-and-cycle:CHK-003","plan-capacity-and-cycle:CHK-004","plan-capacity-and-cycle:CHK-005","plan-capacity-and-cycle:CHK-006","plan-capacity-and-cycle:CHK-007","plan-capacity-and-cycle:CHK-013","plan-capacity-and-cycle:CHK-014","plan-capacity-and-cycle:CHK-015","plan-capacity-and-cycle:CHK-016","plan-capacity-and-cycle:CHK-019","plan-capacity-and-cycle:CHK-020","plan-capacity-and-cycle:CHK-023"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-105: 2026-10-17: CHK-001 Free $0 \"Selected\"; CHK-007 không có control Exclude Test Order; CHK-023 Settings > Plan \"Development store\"; used 0/10 trước và sau 1 đơn test. Các CHK khác không quan sát; không thay authority.","staging_observation_kb_ids":["plan-capacity-and-cycle#KB-082","plan-capacity-and-cycle#KB-085","plan-capacity-and-cycle#KB-088","plan-capacity-and-cycle#KB-089"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-plans-billing-105"}
```

## OQ-plan-041 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-041","type":"NEEDS_CONFIRMATION","feature_id":"plan-catalog-administration","summary":"Giá thật của các gói (vd \"Growth\") nằm trong DB và chưa được xác nhận; số $29/tháng trong tài liệu chỉ là giả định minh hoạ. Cần catalog plan thật trên production.","kb_ids":["plan-catalog-administration#KB-002","plan-catalog-administration#KB-003"],"supersedes":"OQ-plans-billing-106"}
```

## OQ-plan-042 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-042","type":"NEEDS_CONFIRMATION","feature_id":"plan-catalog-administration","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["plan-catalog-administration:CHK-002","plan-catalog-administration:CHK-007","plan-catalog-administration:CHK-008","plan-catalog-administration:CHK-009","plan-catalog-administration:CHK-014"],"supersedes":"OQ-plans-billing-107"}
```

## OQ-plan-043 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-043","type":"NEEDS_CONFIRMATION","feature_id":"plan-catalog-administration","summary":"Plan Paid không có ngưỡng lẫn phí mỗi box (hoặc phí bằng 0) được tài liệu coi là cấu hình sai; form admin có chặn lưu cấu hình này không, và thông báo là gì?","check_ids":["plan-catalog-administration:CHK-005"],"supersedes":"OQ-plans-billing-108"}
```

## OQ-plan-044 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-044","type":"NEEDS_CONFIRMATION","feature_id":"plan-catalog-administration","summary":"Phải có đúng một plan bật On install; admin panel có chặn lưu khi kết quả là 0 hoặc từ 2 plan bật On install không, và nếu không chặn thì hệ thống chọn plan mặc định thế nào?","check_ids":["plan-catalog-administration:CHK-010"],"supersedes":"OQ-plans-billing-109"}
```

## OQ-plan-045 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-045","type":"NEEDS_CONFIRMATION","feature_id":"plan-catalog-administration","summary":"Giới hạn hợp lệ của price, trial days, Box Selling Capacity, % phí và phí tối thiểu trong form plan là gì, và form có chặn giá trị ngoài giới hạn không?","check_ids":["plan-catalog-administration:CHK-015"],"supersedes":"OQ-plans-billing-110"}
```

## OQ-plan-046 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-046","type":"NEEDS_CONFIRMATION","feature_id":"plan-upgrade-downgrade-cancel","summary":"Việc làm mới dữ liệu storefront đúng lúc hết hạn sau khi huỷ plan chỉ có trên nhánh build-staging, chưa lên production. Cần dev/PO xác nhận khi nào hành vi này lên production, và trên production hiện tại storefront đổi plan hiển thị vào lúc nào sau khi huỷ.","kb_ids":["plan-upgrade-downgrade-cancel#KB-087"],"supersedes":"OQ-plans-billing-111"}
```

## OQ-plan-047 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-047","type":"NEEDS_CONFIRMATION","feature_id":"plan-upgrade-downgrade-cancel","summary":"Badge trial \"7 - days free trial\" trên thẻ plan là chữ cố định hay lấy theo số ngày trial của plan? Plan không có trial thì có hiện badge không?","check_ids":["plan-upgrade-downgrade-cancel:CHK-003"],"staging_observation":"Ghi chú quan sát staging cho OQ-plans-billing-112: 2026-10-17: Plan không có trial (cả 4, kể cả Free) không hiện badge; chữ cố định hay theo số ngày trial chưa phân biệt được.","staging_observation_kb_ids":["plan-upgrade-downgrade-cancel#KB-114"],"status_note":"Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.","supersedes":"OQ-plans-billing-112"}
```

## OQ-plan-048 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-048","type":"NEEDS_CONFIRMATION","feature_id":"plan-upgrade-downgrade-cancel","summary":"Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.","check_ids":["plan-upgrade-downgrade-cancel:CHK-009","plan-upgrade-downgrade-cancel:CHK-010","plan-upgrade-downgrade-cancel:CHK-011","plan-upgrade-downgrade-cancel:CHK-014","plan-upgrade-downgrade-cancel:CHK-015","plan-upgrade-downgrade-cancel:CHK-016","plan-upgrade-downgrade-cancel:CHK-019","plan-upgrade-downgrade-cancel:CHK-020","plan-upgrade-downgrade-cancel:CHK-022","plan-upgrade-downgrade-cancel:CHK-023","plan-upgrade-downgrade-cancel:CHK-031","plan-upgrade-downgrade-cancel:CHK-032","plan-upgrade-downgrade-cancel:CHK-033","plan-upgrade-downgrade-cancel:CHK-035","plan-upgrade-downgrade-cancel:CHK-036"],"supersedes":"OQ-plans-billing-113"}
```

## OQ-plan-049 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-049","type":"NEEDS_CONFIRMATION","feature_id":"plan-upgrade-downgrade-cancel","summary":"Khi merchant từ chối hoặc đóng trang duyệt subscription của Shopify, plan của shop có giữ nguyên không, có dòng charge nào bị đổi dở dang không, và dòng Recurring hiển thị trạng thái gì?","check_ids":["plan-upgrade-downgrade-cancel:CHK-012"],"supersedes":"OQ-plans-billing-114"}
```

## OQ-plan-050 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-050","type":"NEEDS_CONFIRMATION","feature_id":"plan-upgrade-downgrade-cancel","summary":"Link có chữ ký quay về Mysbox có hiệu lực 7 ngày; khi mở sau 7 ngày hoặc mở lại lần hai thì hệ thống phản hồi thế nào (thông báo gì) và có tạo thêm charge không?","check_ids":["plan-upgrade-downgrade-cancel:CHK-013"],"supersedes":"OQ-plans-billing-115"}
```

## OQ-plan-051 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-051","type":"NEEDS_CONFIRMATION","feature_id":"plan-upgrade-downgrade-cancel","summary":"Hành vi làm mới dữ liệu storefront đúng lúc hết hạn sau huỷ hiện chỉ có trên build-staging: trên staging đó có phải hành vi mong muốn không, khi nào lên production, và trên production hiện tại storefront đổi hiển thị plan vào lúc nào?","check_ids":["plan-upgrade-downgrade-cancel:CHK-026"],"supersedes":"OQ-plans-billing-116"}
```

## OQ-plan-052 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-052","type":"NEEDS_CONFIRMATION","feature_id":"plan-upgrade-downgrade-cancel","summary":"Route, method, tham số request, kiểu dữ liệu và status/lỗi của endpoint xem trước thay đổi plan là gì? Thiếu thông tin này check không chạy lại được.","kb_ids":["plan-upgrade-downgrade-cancel#KB-095","plan-upgrade-downgrade-cancel#KB-096","plan-upgrade-downgrade-cancel#KB-097","plan-upgrade-downgrade-cancel#KB-098"],"check_ids":["plan-upgrade-downgrade-cancel:CHK-027"],"supersedes":"OQ-plans-billing-117"}
```

## OQ-plan-053 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-053","type":"NEEDS_CONFIRMATION","feature_id":"plan-upgrade-downgrade-cancel","summary":"Khi hạ plan hoặc huỷ trong lúc đang trial, khoản tính lại phí và khoản usage cuối có được gửi lên Shopify không, và charge kết thúc ra sao?","check_ids":["plan-upgrade-downgrade-cancel:CHK-028"],"supersedes":"OQ-plans-billing-118"}
```

## OQ-plan-054 — CONFLICT

```json
{"oq_id":"OQ-plan-054","type":"CONFLICT","feature_id":"plan-capacity-and-cycle","summary":"Cùng shop staging, cùng ngày: merchant app trả capacity_expires_at 2026-10-23T04:58:05Z, còn config storefront (_Mysbox.capabilities) có 2025-07-30T04:58:05Z (over_capacity false, widget vẫn render). Giá trị nào là nguồn đúng, storefront có đang giữ metafield capabilities cũ không, và widget dùng capacity_expires_at thế nào?","side_a":"Quan sát KB-087: dữ liệu nhúng merchant app capacity_expires_at \"2026-10-23T04:58:05.000000Z\" (09:26Z và 10:09Z).","side_b":"Quan sát KB-046: script#mysbox-config render capabilities.capacity_expires_at \"2025-07-30T04:58:05.000000Z\".","conflict_group":"CONF-plans-billing-21","kb_ids":["plan-capacity-and-cycle#KB-087","capacity-limit-enforcement#KB-046"],"related_oq_ids":["OQ-usage-billing-006","OQ-plan-011","OQ-shop-settings-031"],"tags":["staging-observed"],"check_ids":["plan-capacity-and-cycle:CHK-028"],"supersedes":"OQ-plans-billing-132"}
```

## OQ-plan-055 — CONFLICT

```json
{"oq_id":"OQ-plan-055","type":"CONFLICT","feature_id":"plan-capacity-and-cycle","summary":"Plan Prime trên staging tự mâu thuẫn: box_selling_capacity 400 (UI \"Free 400 boxes sales/month\", \"from the 401st\") nhưng description/terms/feature ghi \"Free 1500 boxes sales/month\", \"from the 1501st\". Quota Prime đúng là bao nhiêu và terms nào được gửi Shopify khi merchant chọn Prime?","side_a":"Quan sát KB-083: Prime capacity 400, UI hiển thị 400/401st.","side_b":"Quan sát KB-084: Prime description/terms/feature 1500/1501st.","conflict_group":"CONF-plans-billing-22","kb_ids":["plan-capacity-and-cycle#KB-083","plan-capacity-and-cycle#KB-084"],"related_oq_ids":["OQ-plan-005"],"tags":["staging-observed"],"check_ids":["plan-capacity-and-cycle:CHK-027"],"supersedes":"OQ-plans-billing-133"}
```

## OQ-plan-056 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-056","type":"NEEDS_CONFIRMATION","feature_id":"plan-capacity-and-cycle","summary":"Catalog staging (1 lần đọc): Free 10 / Nitro 100 / Booster 500 box mỗi tháng, phí vượt 2% (min $0.25), không có plan năm, không có trial, không có Early-bird. Catalog production có giống không, và Free 10 box có phải hạn mức production?","kb_ids":["plan-capacity-and-cycle#KB-082"],"check_ids":["plan-capacity-and-cycle:CHK-024"],"tags":["staging-observed"],"supersedes":"OQ-plans-billing-135"}
```

## OQ-plan-057 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-057","type":"NEEDS_CONFIRMATION","feature_id":"plan-capacity-and-cycle","summary":"Staging: merchant không thấy ngày chu kỳ ở đâu; dữ liệu chỉ có capacity_expires_at. capacity_expires_at có phải mốc kết thúc chu kỳ quota không, và merchant nên xem ngày reset ở đâu?","kb_ids":["plan-capacity-and-cycle#KB-086"],"check_ids":["plan-capacity-and-cycle:CHK-025"],"tags":["staging-observed"],"supersedes":"OQ-plans-billing-136"}
```

## OQ-plan-058 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-058","type":"NEEDS_CONFIRMATION","feature_id":"plan-capacity-and-cycle","summary":"Staging: merchant không phân biệt được đơn test trong Manage orders. App nhận biết đơn test theo tiêu chí nào, và merchant có cần thấy nhãn đơn test không?","kb_ids":["plan-capacity-and-cycle#KB-088"],"check_ids":["plan-capacity-and-cycle:CHK-026"],"tags":["staging-observed"],"supersedes":"OQ-plans-billing-137"}
```

## OQ-plan-059 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-059","type":"NEEDS_CONFIRMATION","feature_id":"plan-capacity-and-cycle","summary":"Quan sát staging mới chạm vùng rủi ro cao (quyền truy cập / tiền / billing): Catalog plan trên Pricing staging (Free, Nitro, Booster); Thẻ Prime hiển thị 400 box theo box_selling_capacity; Mô tả/terms của plan Prime ghi 1500 box; Thẻ Box sales limit và dữ liệu chu kỳ phía merchant; capacity_expires_at phía merchant app. Item là OBSERVED_CURRENT; cần PO xác nhận đây là hành vi dự kiến trước khi dùng làm expected result.","kb_ids":["plan-capacity-and-cycle#KB-082","plan-capacity-and-cycle#KB-083","plan-capacity-and-cycle#KB-084","plan-capacity-and-cycle#KB-086","plan-capacity-and-cycle#KB-087"],"tags":["staging-observed","risk-flag"],"supersedes":"OQ-plans-billing-144"}
```

## OQ-plan-060 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-plan-060","type":"NEEDS_CONFIRMATION","feature_id":"plan-upgrade-downgrade-cancel","summary":"Quan sát staging mới chạm vùng rủi ro cao (quyền truy cập / tiền / billing): Thẻ plan trên Pricing staging: không badge trial, không tab năm. Item là OBSERVED_CURRENT; cần PO xác nhận đây là hành vi dự kiến trước khi dùng làm expected result.","kb_ids":["plan-upgrade-downgrade-cancel#KB-114"],"tags":["staging-observed","risk-flag"],"supersedes":"OQ-plans-billing-145"}
```
