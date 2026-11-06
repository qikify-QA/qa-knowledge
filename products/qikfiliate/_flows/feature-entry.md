# Feature vào đâu, cần fixture nào

Cột Fixture trỏ tới `test-data.md`. Expected result và check: `<object>/checklists/<feature>.json`.

| Object | Feature | Vào đâu, làm gì | Fixture |
|---|---|---|---|
| affiliate-account | `affiliate-signup` | `#/signup`, thử field và `ref`; thử cả UI lẫn API | — |
| | `email-verification-and-auto-approval` | Click link trong email, `#/resend-verification` | F1 |
| | `affiliate-login-access-control` | Login ở từng trạng thái tài khoản | F1, F8 |
| | `admin-affiliate-review` | Admin → Affiliate Users: row action, Edit | F1, F8 |
| | `affiliate-dashboard-overview` | `#/dashboard`: bảng shop, khối Payout, banner bonus | F1 |
| | `affiliate-profile-maintenance` | `#/account`. Admin → Affiliate Users → Edit | F1 |
| | `affiliate-email-notifications` | Kích hoạt từng sự kiện, đọc hộp thư | F1, F7, F8 |
| | `new-affiliate-bonus` | Banner Dashboard, `bonus_at`. Staging có cấu hình không `[?]` | F1, F3, F4 |
| affiliate-level | `level-definition-management` | Admin → Levels. Chỉ đọc nếu chưa được phép (guide mục 6) | — |
| | `level-progression` | Tăng shop trả phí qua CSV, xem Level | F3, F4 |
| | `vip-level-override` | Affiliate Users → Edit `is_vip`, `level`, rồi upload CSV | F3, F4 |
| program | `program-launch` | Admin → Programs, rồi rate card | F2 |
| | `program-catalog-for-affiliates` | `#/links`, sort, `visible` | F2 |
| commission-rate-card | `rate-card-configuration` | Admin → Program Commissions | F2 |
| | `usage-commission-enablement` | Form rate card, switch usage | F2 |
| referral-attribution | `tracking-link-generation` | `#/links` → Get Link | F1, F2 |
| | `click-to-install-attribution` | Gọi `tracking-id` rồi `customers`. Không tua được giờ để test hết hạn | F3 |
| | `tracking-information-log` | Admin → Tracking Informations, chỉ xem | F3 |
| customer-shop | `customer-shop-registry` | Admin → Customers: list, Show, Skip First Month, Restore | F3 |
| | `customer-lifecycle-state` | Gửi event, xem Customer Events và `#/customers` | F3 |
| integration-api | `api-key-authentication` | Gọi không key, sai key, đúng key | — |
| | `customer-provisioning-api` | `customers`, `DELETE`, `trashed-customers` | F3 |
| | `customer-event-reporting-api` | `customer-events` với event đúng và sai | F3 |
| payout-import | `payout-csv-upload` | Upload Payouts: file đúng, thiếu cột, thiếu giá trị | F3, F4 |
| | `charge-type-classification` | Một file với đủ loại `Charge Type` | F3, F4 |
| | `customer-matching-and-dedup` | Upload lại cùng file, dòng không khớp shop | F3, F4 |
| | `populate-reconcile-late-data` | Trước hết tìm xem màn này còn không; không có thì ghi `NOT_COVERED` và báo | F3, F4 |
| commission-calculation | `commission-decision-flow` | Upload rồi đọc Conversions | F2, F3, F4 |
| | `first-month-commission` | Chuỗi charge theo ngày lịch, kể cả ranh giới | F2, F3, F4 |
| | `recurring-commission` | Charge sau tháng đầu, có và không cap | F2, F3, F4 |
| | `refund-and-downgrade-adjustment` | Dòng âm sau dòng dương | F2, F3, F4 |
| | `usage-charge-commission` | Nhiều dòng usage, nhiều kỳ, để chạm cap | F2, F3, F4 |
| conversion-ledger | `admin-conversion-review` | Admin → Conversions | F4 |
| | `affiliate-conversion-view` | `#/conversions`. Kiểm ngày ở 2 timezone | F4 |
| | `custom-conversion-entry` | Admin → Conversions → New conversion | F5 |
| invoice-payout | `balance-accrual` | So `balance` trước/sau từng sự kiện | F4 hoặc F5 |
| | `payout-request-eligibility` | Khối Payout ở từng tổ hợp điều kiện; `can_create_invoice`; gọi thẳng API | F6 |
| | `payout-request-submission` | Request Payment | F6 |
| | `payout-request-cancellation` | `#/invoices` → huỷ | F7 |
| | `admin-invoice-processing` | Admin → Invoices. Kiểm chuyển status và snapshot | F7 |
| payment-method | `affiliate-payment-info-setup` | `#/account` → Payout Information. Full reload sau khi đổi Country | F1 |
| | `payment-method-catalog` | Admin → Payment Methods. Tạo method `QA-`, không đụng PayPal, Payoneer | — |
| admin-console | `admin-home-dashboard` | Trang đầu admin | — |
| | `embedded-version-cache-bust` | Admin → Embedded Version (guide mục 6) | — |
| | `data-maintenance-commands` | Cần dev chạy; không thì `NOT_COVERED` | — |
