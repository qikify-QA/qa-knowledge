# Open Questions — Subscription

Các mục dưới đây còn mở. Không dùng phần còn mở làm expected result.

## Tóm tắt

| Loại | Số lượng |
|---|---|
| CONFLICT | 4 |
| NEEDS_CONFIRMATION | 22 |
| OPEN_ISSUE | 10 |
| **Tổng** | **36** |

## OQ-subscription-001 — CONFLICT

```json
{"oq_id":"OQ-subscription-001","type":"CONFLICT","feature_id":"view-current-subscription-plan","summary":"Cột PRICE ở /subscriptions hiện USD 0.00 cho gói Blue test trên dev store, trong khi API (/api/user, all-subscriptions) trả 49 và bảng Pricing Plans hiện \"$49/month\". Cột PRICE lấy từ đâu, 0.00 có phải hành vi đúng cho subscription test?","side_a":"UI /subscriptions cột PRICE: USD 0.00","side_b":"API /api/user, GET /api/user/all-subscriptions và bảng Pricing Plans: 49 / \"$49/month\""}
```

## OQ-subscription-002 — CONFLICT

```json
{"oq_id":"OQ-subscription-002","type":"CONFLICT","feature_id":"view-current-subscription-plan","summary":"trial_days của gói Blue khác nhau theo endpoint dù cùng plan id: GET /api/platforms/shopify/tier-plans trả 0, /api/user tier_subscription.tier_plan trả 1, tier-subscriptions và all-subscriptions (phía Shopify) trả 7. Giá trị nào có hiệu lực và nguồn nào là chuẩn?","side_a":"tier-plans: trial_days 0; /api/user tier_plan: trial_days 1","side_b":"tier-subscriptions, all-subscriptions: trialDays 7"}
```

## OQ-subscription-003 — OPEN_ISSUE

```json
{"oq_id":"OQ-subscription-003","type":"OPEN_ISSUE","feature_id":"view-current-subscription-plan","summary":"Chưa quan sát trạng thái chưa subscribe (Active Plan, nút Subscribe/Choose plan): account đã quan sát đang có Blue test ACTIVE. Cần account hoặc fixture phù hợp mà không phải subscribe thật."}
```

## OQ-subscription-004 — OPEN_ISSUE

```json
{"oq_id":"OQ-subscription-004","type":"OPEN_ISSUE","feature_id":"view-current-subscription-plan","summary":"\"Cancel subscription\" và \"Change Default billing store\" chưa được bấm (thao tác ghi billing): chưa biết có dialog xác nhận hay thực thi ngay, và kết quả ra sao."}
```

## OQ-subscription-005 — OPEN_ISSUE

```json
{"oq_id":"OQ-subscription-005","type":"OPEN_ISSUE","feature_id":"view-current-subscription-plan","summary":"Chưa quan sát gói Blue trên store live (không phải test): NEXT BILL DATE khác N/A, giá thật, banner, trạng thái trả phí."}
```

## OQ-subscription-006 — OPEN_ISSUE

```json
{"oq_id":"OQ-subscription-006","type":"OPEN_ISSUE","feature_id":"view-current-subscription-plan","summary":"Bảng /subscriptions hiển thị thế nào khi có nhiều nền tảng hoặc khi không có subscription nào? Mới thấy một dòng Shopify."}
```

## OQ-subscription-007 — OPEN_ISSUE

```json
{"oq_id":"OQ-subscription-007","type":"OPEN_ISSUE","feature_id":null,"summary":"Mọi quan sát của object dùng role owner; chưa biết staff role khác có xem được /subscriptions, /subscriptions/shopify-tier, /platform-usages/* và các control billing không."}
```

## OQ-subscription-008 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-008","type":"NEEDS_CONFIRMATION","feature_id":null,"summary":"Ranh giới object: webhook billing (Paddle price.created, Shopify Billing) giữ ở account-security/billing-webhook. Các trang subscription không có control hay response nào nhắc tới webhook, nên chưa có bằng chứng xác nhận hay bác bỏ ranh giới này. Cần Dev xác nhận."}
```

## OQ-subscription-010 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-010","type":"NEEDS_CONFIRMATION","feature_id":"legacy-plan-pricing-display","summary":"Route /subscriptions/etsy-tier có tồn tại không và dùng cho trường hợp nào? Chưa có quan sát lưu lại."}
```

## OQ-subscription-011 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-011","type":"NEEDS_CONFIRMATION","feature_id":"legacy-plan-pricing-display","summary":"Điều kiện nào chọn route plan cũ (/subscriptions/<platform>) thay vì route Blue (/subscriptions/shopify-tier) khi bấm Manage? Mới thấy account has_new_pricing true."}
```

## OQ-subscription-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-012","type":"NEEDS_CONFIRMATION","feature_id":"legacy-plan-pricing-display","summary":"Route plan cũ /subscriptions/<platform> hiện \"Subscription Details\" trống trên account không có plan cũ: đây là hành vi đúng hay nên redirect hoặc hiện thông báo?"}
```

## OQ-subscription-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-014","type":"NEEDS_CONFIRMATION","feature_id":"tier-plan-pricing-display","summary":"Giá $49/month, các mốc tier 2/6/10 và đơn giá 0.5/0.2/0.1 mới chỉ quan sát trên staging. Giá trị production là bao nhiêu và có phải cấu hình theo môi trường không?"}
```

## OQ-subscription-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-015","type":"NEEDS_CONFIRMATION","feature_id":"tier-plan-pricing-display","summary":"Calculator có tính Total fee lũy tiến theo bậc (item 1 $0, 2-5 $0.5, 6-9 $0.2, từ 10 $0.1, cộng giá plan) như suy ra từ output không, và phí thật trên hoá đơn có tính giống calculator không?"}
```

## OQ-subscription-016 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-016","type":"NEEDS_CONFIRMATION","feature_id":"tier-plan-pricing-display","summary":"Calculator nhận số thập phân (2.5 cho $49.75), đổi -1 thành 0, và slider không đồng bộ tuyến tính với ô nhập: có phải hành vi mong muốn?"}
```

## OQ-subscription-017 — CONFLICT

```json
{"oq_id":"OQ-subscription-017","type":"CONFLICT","feature_id":"tier-usage-metering","summary":"Chu kỳ usage tính theo mốc nào: /api/user cycle.reset_at (interval_days 30) hay currentPeriodStart/End của Shopify tier-subscriptions (lệch khoảng 7 tuần)? Ngày \"reset on\" ở UI sớm hơn ngày UTC của reset_at một ngày: hiển thị theo timezone nào?","side_a":"/api/user cycle.reset_at (interval_days 30); UI \"Current cycle (reset on <ngày>)\"","side_b":"GET /api/user/shopify/tier-subscriptions currentPeriodStart/currentPeriodEnd"}
```

## OQ-subscription-018 — CONFLICT

```json
{"oq_id":"OQ-subscription-018","type":"CONFLICT","feature_id":"tier-usage-metering","summary":"Card Plan hiện \"Order items: 0\" (cycle.unit_count 0) nhưng bảng Usages có 1 dòng quantity 1 tạo trước chu kỳ hiện tại. Quy tắc đếm order items theo chu kỳ là gì, và \"Order items\" lấy từ cycle.unit_count hay GET /api/instances/{id}/order-count?","side_a":"card Plan và /api/user cycle.unit_count: 0","side_b":"tier_usages_connection và bảng Usages: 1 dòng, quantity 1"}
```

## OQ-subscription-019 — OPEN_ISSUE

```json
{"oq_id":"OQ-subscription-019","type":"OPEN_ISSUE","feature_id":"tier-usage-metering","summary":"Chưa quan sát khi order items > 0: Next tier đổi thế nào, nhãn ở bậc cao nhất (10+), progressbar và Usages $ khác 0."}
```

## OQ-subscription-021 — OPEN_ISSUE

```json
{"oq_id":"OQ-subscription-021","type":"OPEN_ISSUE","feature_id":"tier-usage-metering","summary":"Page-size selector của bảng Usages không nhận thay đổi khi thử, nút Export chưa bấm: hành vi phân trang và nội dung file export chưa quan sát."}
```

## OQ-subscription-022 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-022","type":"NEEDS_CONFIRMATION","feature_id":"tier-usage-metering","summary":"Trang /platform-usages/etsy hiện nguyên văn \"You have to active a plan to start selling\" và lặp lưu ý về test order của Shopify; trang Boundless không có khối \"No plan\". Wording và khác biệt này có phải ý định?"}
```

## OQ-subscription-023 — OPEN_ISSUE

```json
{"oq_id":"OQ-subscription-023","type":"OPEN_ISSUE","feature_id":"tier-usage-metering","summary":"Bộ lọc \"Store\" của bảng Usages lọc ra sao khi chọn một store? Mới mở dropdown."}
```

## OQ-subscription-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-024","type":"NEEDS_CONFIRMATION","feature_id":"legacy-plan-pricing-display","summary":"Các check BASELINE CHK-001 của feature plan cũ chỉ dựa trên hành vi quan sát trên staging (account gói Blue test, không có plan cũ). Cần PO/Dev xác nhận đây là hành vi đúng trước khi dùng làm expected requirement."}
```

## OQ-subscription-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-025","type":"NEEDS_CONFIRMATION","feature_id":"tier-plan-pricing-display","summary":"Các check BASELINE CHK-001, CHK-002, CHK-003, CHK-004, CHK-005, CHK-006, CHK-008, CHK-009, CHK-010, CHK-011 của feature bảng giá tier và calculator chỉ dựa trên hành vi quan sát trên staging (gói Blue test, Order items 0). Cần PO/Dev xác nhận đây là hành vi đúng trước khi dùng làm expected requirement."}
```

## OQ-subscription-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-026","type":"NEEDS_CONFIRMATION","feature_id":"tier-usage-metering","summary":"Các check BASELINE CHK-001, CHK-002, CHK-003, CHK-004, CHK-005, CHK-006, CHK-010, CHK-011 của feature usage theo chu kỳ chỉ dựa trên hành vi quan sát trên staging (gói Blue test, Order items 0). Cần PO/Dev xác nhận đây là hành vi đúng trước khi dùng làm expected requirement."}
```

## OQ-subscription-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-subscription-027","type":"NEEDS_CONFIRMATION","feature_id":"view-current-subscription-plan","summary":"Các check BASELINE CHK-001, CHK-002, CHK-003, CHK-004, CHK-005, CHK-006, CHK-007, CHK-008, CHK-009, CHK-010 của feature xem plan subscription hiện tại chỉ dựa trên hành vi quan sát trên staging (gói Blue test, Order items 0). Cần PO/Dev xác nhận đây là hành vi đúng trước khi dùng làm expected requirement."}
```

## OQ-subscription-028 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-subscription-028", "type": "NEEDS_CONFIRMATION", "feature_id": "tier-plan-pricing-display", "summary": "[CBS-154, KB-1228, CHK-015] Popup \"View other plans\" dùng chung bảng giá nên cũng ghi \"order items\" theo lời Dev (TIB-5711, 2026-11-10), nhưng chưa quan sát: staging chỉ có 1 tier plan nên nút không render. Cần config có hơn 1 tier plan để kiểm popup; CHK-015 chưa có oracle. Phần Active Plan và \"Estimate your cost\" của OQ-subscription-013 đã có nguồn ở KB-1228, KB-1230."}
```

## OQ-subscription-029 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-subscription-029", "type": "NEEDS_CONFIRMATION", "feature_id": "tier-plan-pricing-display", "summary": "[CBS-154, KB-1230, CHK-014] Số trên nhãn giá Blue lấy từ tier config, tier cuối ghi \"{from}+\" và số có dấu phẩy (\"1,000\") có phải expected không? Hiện chỉ có quan sát test case staging (mốc 2/6/10) và đọc bundle; rule spec-hub usage-charges-new-tiers chỉ nói đơn giá theo bậc, không nói nhãn hay định dạng. Chưa quan sát nhãn từ 1,000 trở lên trên UI. Người trả lời: Dev/PO."}
```

## OQ-subscription-030 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-subscription-030", "type": "NEEDS_CONFIRMATION", "feature_id": "tier-plan-pricing-display", "summary": "[CBS-154, KB-1231] Tier config Blue trên production có phải 101 / 1,001 / 10,001 với free 100 order items như ticket TIB-5711 ghi không, và tier config có cấu hình riêng theo môi trường không? Production chưa có account Blue để quan sát; giá $49 và đơn giá production vẫn ở OQ-subscription-014. Người trả lời: Dev/PO."}
```

## OQ-subscription-031 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-subscription-031", "type": "NEEDS_CONFIRMATION", "feature_id": "tier-plan-pricing-display", "summary": "[CBS-154] New pricing có đếm quota free theo order item thay vì theo order không (quota free 100 trên production là 100 order items)? Lời xác nhận chỉ được ghi lại trong description TIB-5711, vai trò người xác nhận và ngày gốc không rõ, nên chưa nạp vào KB. Bối cảnh: rule spec-hub usage-charges-new-unit (green, chưa người duyệt) nói phí đếm theo design cá nhân hoá cho order item, không theo quantity. Cần Dev/PO chốt đơn vị đếm; liên quan OQ-subscription-018."}
```

## OQ-subscription-032 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-subscription-032", "type": "NEEDS_CONFIRMATION", "feature_id": "legacy-plan-pricing-display", "summary": "[CBS-154, KB-1233, CHK-006, CHK-007, CHK-008] Bộ nhãn plan cũ quan sát qua test case staging có phải expected không? Gợi ý regression của Dev trên TIB-5711 ghi Shopify plan cũ và Etsy cùng \"Free Orders/Month\", \"Number of Orders per month:\", còn test case thấy Shopify plan cũ ghi \"Number of orders/month:\" (chỉ Etsy ghi \"Number of Orders per month:\"): chuỗi nào đúng cho Shopify plan cũ? Bộ chữ Boundless chưa có lời Dev. Người trả lời: Dev/PO."}
```

## OQ-subscription-033 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-subscription-033", "type": "NEEDS_CONFIRMATION", "feature_id": "legacy-plan-pricing-display", "summary": "[CBS-154, KB-1233, KB-1211] Test case plan cũ dùng route /subscriptions/<instance-id> (Shopify), /subscriptions/platform/etsy (Etsy), /subscriptions/manage-domains (Boundless), khác các route /subscriptions/shopify, /subscriptions/etsy, /subscriptions/boundless render trống ở KB-1211. Route nào là điểm vào thật của trang Manage plan cũ, và các route ở KB-1211 còn dùng không? Liên quan OQ-subscription-011, OQ-subscription-012. Người trả lời: Dev."}
```

## OQ-subscription-034 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-subscription-034", "type": "NEEDS_CONFIRMATION", "feature_id": "tier-usage-metering", "summary": "[CBS-161] Các quy tắc tier usage và email chuyển tier của gói Blue (KB-1234 đến KB-1241) quyết định số tiền merchant bị tính và email gửi cho merchant. Nguồn là comment Dev trên TIB-5625 và rule spec-hub design-generation-usage; chưa có PO xác nhận ý định. Cần PO xác nhận: 1 usage cho mỗi customization (không theo printarea, không theo order), re-generate không tính thêm, email TierUp/TierTopReached bắn một count trước mốc tier, email chỉ gửi sau commit."}
```

## OQ-subscription-035 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-subscription-035", "type": "NEEDS_CONFIRMATION", "feature_id": "tier-usage-metering", "summary": "[CBS-161, KB-1242] Trên staging, order test Shopify (Bogus) trên dev store vẫn tạo tier usage và tăng Order items, trong khi trang Usages ghi \"Shopify’s test orders will not be counted or charged\" (KB-1222). Đây có phải hành vi đúng của new pricing trên staging không, production có đếm order test không, và dòng lưu ý có áp cho gói Blue không? Mọi test case staging của TIB-5625 dùng order loại này."}
```

## OQ-subscription-036 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-subscription-036", "type": "NEEDS_CONFIRMATION", "feature_id": "tier-usage-metering", "summary": "[CBS-161] Email chuyển tier: (1) rule spec-hub usage-charges-free-limit-warning (green, chưa người duyệt) nói merchant được báo khi còn 1 unit free trước khi bắt đầu tính phí và khi chuyển sang tier mới, còn Dev (KB-1238) nói TierUp/TierTopReached bắn một count trước mốc tier: hai cách nói có cùng nghĩa không; (2) TierFreeExceeded bắn ở count nào trên plan có free từ 2 trở lên (vd production); (3) nội dung email: record TC-TIB-9036 ghi email TierUp \"reached 5 orders\", trong khi portal gói Blue ghi \"order items\" (KB-1228): chữ \"orders\" trong email có phải ý định không. TierTopReached ở count 9 chưa test trên staging. Thay phần điều kiện gửi của OQ-subscription-020 đã có nguồn Dev."}
```

## OQ-subscription-037 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-subscription-037", "type": "NEEDS_CONFIRMATION", "feature_id": "tier-usage-metering", "summary": "[CBS-161] Đơn vị đếm tier usage ở các trường hợp chưa có nguồn: order item quantity > 1 (rule spec-hub usage-charges-new-unit nói phí không tính theo quantity), cùng một customization dùng lại ở order item thứ hai (comment Solution 56145 của Dev để mở câu hỏi này và nói unique key hiện tại không tính lại), order Etsy. KB-1234, KB-1235 chỉ nói 1 usage cho mỗi customization. Liên quan OQ-subscription-031 (đơn vị đếm quota free)."}
```

## OQ-subscription-038 — OPEN_ISSUE

```json
{"oq_id": "OQ-subscription-038", "type": "OPEN_ISSUE", "feature_id": "tier-usage-metering", "summary": "[CBS-161] Record TC-TIB-9037 (staging 2026-11-10): trước order, Subscription details vẫn hiện cycle cũ đã quá ngày reset (Order items 8); order đầu tiên sau đó mở cycle mới và Order items về 1. Comment 56913 của Dev nói reset_at được đặt 30 ngày sau lúc tạo cycle. Chưa rõ cycle trên portal chỉ đổi khi có usage mới hay theo lịch; liên quan conflict OQ-subscription-017 (mốc chu kỳ) và OQ-subscription-018 (Order items 0 trong khi có dòng usage). Không đóng hai conflict này."}
```

## OQ-subscription-039 — OPEN_ISSUE

```json
{"oq_id": "OQ-subscription-039", "type": "OPEN_ISSUE", "feature_id": "tier-usage-metering", "summary": "[CBS-161] Setup: guide chưa có biến env cho account gói Blue được phép đặt order test để kiểm tier usage. Account Blue dùng trong test case TIB-5625 thuộc nhóm TIB_ONBOARDING_* mà guide ghi chỉ đọc, giữ sạch. Cần QA lead chỉ định account (tên biến env) cho CHK-012 đến CHK-018."}
```
