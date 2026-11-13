# Object: Subscription (product: teeinblue) — Feature Profile Summary
**Published context version:** 3

- **Object:** plan và subscription của merchant trên portal: Organization > Subscriptions (`/subscriptions`), Subscription Details của gói Blue/new pricing (`/subscriptions/shopify-tier`), card Plan (Home, Subscription Details, Usages), trang Usages (`/platform-usages/<platform>`), bảng giá tier và calculator. Gồm plan cũ (Shopify theo store, Etsy, Boundless) và gói Blue tính theo order item.
- **Không thuộc:** webhook billing (Paddle `price.created`) ở `account-security/billing-webhook`, xem OQ-subscription-008; luồng thanh toán thật (subscribe, upgrade, downgrade, cancel, charge); render và regenerate design của order (`order`); admin Tier usages nội bộ.
- **Quan sát:** staging, role `merchant-owner`, một account có `has_new_pricing` true đang dùng gói Blue test ACTIVE trên dev store, Order items 0 trong chu kỳ. Mọi trang billing chỉ xem, không bấm control ghi. Từ v2 có thêm kết quả test case staging (TIB-5711) cho Active Plan chưa subscribe và trang plan cũ. Từ v3 có quy tắc Dev và kết quả test case staging (TIB-5625) cho tier usage và email chuyển tier. Chưa quan sát popup "View other plans", store live.
- **Knowledge:** 40 KB item: 10 `CONFIRMED_EXPECTED`/`MEDIUM` (comment Dev TIB-5711 về chữ "order items" và "orders"; comment Dev TIB-5625 và rule spec-hub về tier usage và email chuyển tier), 27 `OBSERVED_CURRENT` (10 `MEDIUM`, 17 `LOW`), 3 `INFERRED`/`LOW`. 53 check: 10 `STRONG`, 33 `BASELINE`, 10 `NONE`. Hành vi quan sát được không phải expected requirement. 4 conflict `UNRESOLVED`.
- **Open question:** 36 mục ở `open-questions.md`. Check `BASELINE` của mỗi feature chờ PO/Dev xác nhận ở OQ-subscription-024 đến 027; quy tắc tier usage chờ PO xác nhận ý định ở OQ-subscription-034.

---

## `view-current-subscription-plan` — Xem plan subscription hiện tại

**Entry points:** badge plan dưới tên store ở sidebar (link tới `/subscriptions`); Organization > Subscriptions (`/subscriptions`); nút Manage tới `/subscriptions/shopify-tier`; card Plan ở Home và `/platform-usages/shopify`.

**Đã quan sát:** badge plan và tooltip; bảng Subscriptions theo nền tảng; Subscription Details của Blue với khối Store và Default billing store; card Plan giống nhau ở ba trang; banner test plan trên dev store; field plan trong `GET /api/user` và `GET /api/user/all-subscriptions`. KB-1201 đến KB-1209, KB-1215.
**Conflict:** KB-1203 (cột PRICE USD 0.00 so với giá 49 của API, OQ-subscription-001), KB-1215 (`trial_days` 0/1/7 theo endpoint, OQ-subscription-002). Không dùng làm oracle.
**Chưa quan sát:** trạng thái chưa subscribe, Cancel subscription và Change Default billing store, store live, nhiều nền tảng, role khác owner (OQ-subscription-003 đến 007).
**Checklist:** 13 check, 10 `BASELINE`, 3 `NONE`.

## `legacy-plan-pricing-display` — Hiển thị bảng giá và Manage của plan cũ

**Entry points:** test case staging dùng `/subscriptions/<instance-id>` (Shopify plan cũ), `/subscriptions/platform/etsy`, `/subscriptions/manage-domains` (Boundless); các route `/subscriptions/shopify`, `/subscriptions/etsy`, `/subscriptions/boundless` render trống trên account không có plan cũ (OQ-subscription-033).

**Expected:** plan cũ (Shopify theo store, Etsy, Boundless) giữ chữ "orders", không có "order items" (KB-1232, comment Dev 2026-11-10).
**Đã quan sát:** bộ nhãn plan cũ qua test case staging: Shopify "Orders in cycle", "Free orders", "Extra orders", "Free Orders/Month", "Transaction Fee (per extra order)", "Number of orders/month:"; Etsy cùng nhãn nhưng calculator "Number of Orders per month:"; Boundless "No transaction fees. Unlimited orders." (KB-1233, chờ xác nhận ở OQ-subscription-032). Route plan cũ render trống trên account không có plan cũ (KB-1211).
**Chưa rõ:** điều kiện chọn route plan cũ hay route Blue, route `/subscriptions/etsy-tier` (OQ-subscription-010 đến 012).
**Checklist:** 7 check, 1 `STRONG`, 4 `BASELINE`, 2 `NONE`.

## `tier-plan-pricing-display` — Hiển thị bảng giá tier và calculator ước tính phí

**Entry points:** `/subscriptions/shopify-tier` (account Blue đã subscribe); `/active-plan` (account `has_new_pricing` có store Shopify chưa subscribe).

**Expected:** account new pricing ghi free quota và các mức phí theo "order items": Active Plan (dòng free quota, dòng transaction fee, "Lower fees as your sales increase", hai tooltip, calculator "Estimate your cost"), Subscription details (usage bar "Order items:", bảng giá, calculator), popup "View other plans" (KB-1228, comment Dev 2026-11-10; chỉ chữ, không phải con số).
**Đã quan sát:** bảng "Pricing Plans for Shopify" ghi theo "order items"; dữ liệu tier từ `GET /api/platforms/shopify/tier-plans`; calculator "Number of order items per month:" tính phía client, không phát request. KB-1213, KB-1214, KB-1216, KB-1217, KB-1219. Active Plan staging qua test case: nhãn số theo tier config (KB-1230, OQ-subscription-029).
**Khác biệt môi trường:** tier staging 2/6/10, free 1 order item, 1 tier plan; production theo ticket 101 / 1,001 / 10,001, free 100, chưa quan sát (KB-1231, OQ-subscription-030). Không so số production trên staging.
**Không dùng làm oracle:** KB-1218 (`INFERRED`: Total fee khớp cách tính lũy tiến theo bậc), xem OQ-subscription-015; KB-1231.
**Chưa quan sát:** popup "View other plans" (OQ-subscription-028). Đơn vị đếm quota free chưa có xác nhận (OQ-subscription-031).
**Checklist:** 15 check, 2 `STRONG`, 11 `BASELINE`, 2 `NONE`.

## `tier-usage-metering` — Theo dõi usage order items theo chu kỳ

**Entry points:** card Plan (Home, `/subscriptions/shopify-tier`); "View usages" tới `/platform-usages/shopify`; `/platform-usages/etsy`, `/platform-usages/boundless`.

**Expected:** gói Blue trên Shopify tạo 1 tier usage cho mỗi customization, ở design đầu tiên: item 2 printarea vẫn 1 usage, cycle count +1 (KB-1234); 2 customization trong một order là 2 usage (KB-1235); item 1 printarea 1 usage (KB-1236); re-generate không tính thêm (KB-1237). Email TierUp/TierTopReached bắn khi count = mốc tier kế tiếp − 1 (staging 2/6/10: count 5 và 9), TierFreeExceeded không bắn trên plan 2/6/10 (KB-1238); order multi-printarea qua mốc gửi đúng 1 email (KB-1239); email chỉ gửi sau commit (KB-1240) và hai job đồng thời chỉ 1 usage (KB-1241), hai điều này không kiểm được trên staging. Nguồn: comment Dev TIB-5625 và rule spec-hub; chờ PO xác nhận ý định (OQ-subscription-034).
**Đã quan sát:** card Plan ở Order items 0 ("Order items", "Next tier", "Usages"); trang Usages với bảng lấy từ query đọc `tier_usages_connection` (gói Blue); bộ lọc Store; trang Etsy và Boundless khi không có plan. KB-1220, KB-1222, KB-1223, KB-1225, KB-1212.
**Khác biệt môi trường:** staging đếm order test Bogus trên dev store vào tier usage, dù trang Usages ghi test order không được đếm; production chưa rõ (KB-1242, OQ-subscription-035). Không suy hành vi production từ staging.
**Conflict:** KB-1221 (mốc reset chu kỳ giữa UI, `/api/user` và Shopify, OQ-subscription-017), KB-1224 (Order items 0 trong khi bảng có 1 dòng usage, OQ-subscription-018). Không dùng làm oracle. Cycle hiển thị có thể là cycle cũ tới khi có order mới (OQ-subscription-038).
**Chưa rõ:** nhãn khi order items > 0, phân trang và Export, lọc theo store (OQ-subscription-019, 021 đến 023); thời điểm và nội dung email, TierTopReached chưa test (OQ-subscription-036); quantity > 1, customization dùng lại, Etsy (OQ-subscription-037); account Blue được phép đặt order test (OQ-subscription-039).
**Checklist:** 18 check, 7 `STRONG`, 8 `BASELINE`, 3 `NONE`.

**KB mức object:** KB-1226 (xem các trang subscription không phát sinh request ghi), KB-1227 (role owner xem được các trang subscription).
