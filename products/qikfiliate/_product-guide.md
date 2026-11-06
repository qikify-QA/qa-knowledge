# Product guide — qikfiliate

Bản đồ của product: có gì, ở đâu, test được không. Mọi bước đều đọc file này.

- Đúng phải là gì: `<object>/features/<feature>/kb.json`, `checklists/`.
- Làm thế nào: `_flows/`, đọc `_flows/README.md` rồi đúng file theo chủ đề.
- Biến env: `_env.example`.

Không dùng guide làm expected result. Không ghi giá trị credential, id, tên store.

Nhãn nguồn: `[RG]` regression staging 2026-10-22, sau upgrade · `[TC]` test case trước upgrade · `[DOC]` chỉ có trong tài liệu dev 2026-08-20 · `[?]` chưa biết, gặp thì báo operator.

> **KB v1 cũ hơn hệ thống:** viết trước đợt upgrade Laravel và đổi URL, admin nay chạy Filament. Lệch về **giao diện** là KB cũ, không phải bug. Lệch về **hành vi tiền** thì ghi evidence và hỏi PO.

## 1. Product

Hệ thống affiliate dùng chung của Qikify. Một KB cho nhiều brand: item có `scope.brand` khác `null` chỉ đúng cho brand đó. Luồng chính:

1. Affiliate lấy link giới thiệu ở Dashboard (Vue SPA).
2. Client app báo qua Integration API, server-to-server, không có UI: `tracking-id` khi click, `customers` khi cài, `customer-events` cho vòng đời shop. API không mang số tiền.
3. Admin upload CSV Payout của Shopify ở Admin panel (Filament `[RG]`), hệ thống tính hoa hồng từng dòng theo Level × Program, sinh Conversion, `balance` tăng.
4. Affiliate bấm Request Payment, tạo Invoice `pending`.
5. Admin chuyển tiền ngoài hệ thống rồi đổi status Invoice.

| Thuật ngữ | Nghĩa | Hay nhầm với |
|---|---|---|
| User | Affiliate | Merchant, khách cuối |
| Customer | **Shop** Shopify được giới thiệu, theo cặp shop × app | Khách cuối của shop |
| `slug` (Program) | Khoá khớp `app_slug` trong CSV | `ref_slug` của link giới thiệu |
| `ref` | Slug link riêng của affiliate | `tracking_id` |
| Payout | Shopify → Ownego, đầu vào | Invoice |
| Invoice | Ownego → affiliate, đầu ra | Payout |
| Conversion | Một dòng hoa hồng: `first`, `recurring`, `usage`, `custom` | Chuyển đổi marketing |
| `partner_share` | Tiền Ownego nhận cho một dòng charge, gốc để nhân % | `amount` |
| `amount` | Hoa hồng sau % và cap | `partner_share` |

Định nghĩa đầy đủ: `_product-kb.json`.

## 2. Object và feature

Từ khoá sang object: `_registry.json`. Trạng thái, oracle: `manifest.json`. Vào đâu, cần fixture nào: `_flows/feature-entry.md`.

| Object | Phạm vi | Không thuộc | Feature |
|---|---|---|---|
| `affiliate-account` | Vòng đời tài khoản affiliate | Thông tin nhận tiền (`payment-method`) | `affiliate-signup` `email-verification-and-auto-approval` `affiliate-login-access-control` `admin-affiliate-review` `affiliate-dashboard-overview` `affiliate-profile-maintenance` `affiliate-email-notifications` `new-affiliate-bonus` |
| `affiliate-level` | Bậc theo số shop trả phí, VIP | Rate card (`commission-rate-card`) | `level-definition-management` `level-progression` `vip-level-override` |
| `program` | App được quảng bá | % hoa hồng (`commission-rate-card`) | `program-launch` `program-catalog-for-affiliates` |
| `commission-rate-card` | % và cap theo Program × Level | Tính tiền từng dòng (`commission-calculation`) | `rate-card-configuration` `usage-commission-enablement` |
| `referral-attribution` | Gắn shop với đúng affiliate | Endpoint và auth (`integration-api`) | `tracking-link-generation` `click-to-install-attribution` `tracking-information-log` |
| `customer-shop` | Shop được giới thiệu và vòng đời | | `customer-shop-registry` `customer-lifecycle-state` |
| `integration-api` | 5 endpoint cho client app | | `api-key-authentication` `customer-provisioning-api` `customer-event-reporting-api` |
| `payout-import` | Upload CSV, khớp shop, chống trùng | Tính tiền (`commission-calculation`) | `payout-csv-upload` `charge-type-classification` `customer-matching-and-dedup` `populate-reconcile-late-data` |
| `commission-calculation` | Engine tính tiền cho một dòng CSV | Hiển thị Conversion (`conversion-ledger`) | `commission-decision-flow` `first-month-commission` `recurring-commission` `refund-and-downgrade-adjustment` `usage-charge-commission` |
| `conversion-ledger` | Sổ hoa hồng | | `admin-conversion-review` `affiliate-conversion-view` `custom-conversion-entry` |
| `invoice-payout` | Balance và yêu cầu rút tiền | CSV Payout (`payout-import`) | `balance-accrual` `payout-request-eligibility` `payout-request-submission` `payout-request-cancellation` `admin-invoice-processing` |
| `payment-method` | Phương thức nhận tiền | | `affiliate-payment-info-setup` `payment-method-catalog` |
| `admin-console` | Trang chủ admin, Embedded Version, console command | | `admin-home-dashboard` `embedded-version-cache-bust` `data-maintenance-commands` |

## 3. Môi trường

Host khác `KOIN_DASHBOARD_URL` thì dừng và hỏi operator. Host production `[?]`. Production là stop condition cho mọi thao tác ghi.

| Biến | Đặc điểm | Dùng cho | Không dùng cho |
|---|---|---|---|
| `KOIN_DASHBOARD_URL` | Dashboard staging, instance Koin/Mysbox `[RG]` | Mọi test Dashboard | Kết luận cho brand khác |
| `KOIN_DASHBOARD_OLD_URL` | URL cũ | Kiểm redirect | |
| `KOIN_AFF_APPROVED_*` | Đã verify, approved, có data | Xem hiển thị | Test invoice (làm mất balance) |
| `KOIN_AFF_UNVERIFIED_*` | Chưa verify email | Chặn login | |
| `KOIN_AFF_DISAPPROVED_*` | Bị từ chối, có thể chưa verify | | Test disapprove khi chưa xác nhận đã verify |
| `KOIN_AFF_WITH_BALANCE_*` | Có balance | Request Payment | |
| `KOIN_AFF_MAIN_*` | Email chính | Happy case signup | |
| `KOIN_SIGNUP_BASE_EMAIL` | Plus-addressing | Affiliate mới, đọc mail | |
| `KOIN_ALLOW_CREATE_INVOICE` | `yes`/`no` | `no` thì case tạo Invoice là `BLOCKED` | |

Chưa có biến: credential admin, `X-API-Key`, host admin, host Integration API. Không có storefront, DB access, OpenAPI.

## 4. Test được gì

**Nhãn test case:** không test được cả case là `env-blocked`: Testlane `skipped` kèm lý do, verdict `NOT_APPLICABLE`. Không test được một vế: giữ case, ghi "vế X: skip — <lý do>", kết luận theo các vế còn lại.

Chưa feature nào có `environment_differences`: cột `type` để `—` tới khi có khối B.

| Hạng mục | Feature | `type` | Mức | Cách xử lý |
|---|---|---|---|---|
| Hết hạn tracking | `referral-attribution/click-to-install-attribution` | — | Vế | Không tua được giờ, skip vế này |
| Console command | `admin-console/data-maintenance-commands` | — | Case | Cần dev chạy, không thì `NOT_COVERED` |
| Check `layer: db` | Nhiều feature | — | Vế | Quan sát qua Admin, Activities, `GET /api/user`; không có thì `NOT_COVERED` |
| Integration API | `integration-api/*`, fixture F3 | — | Case | Chưa có key và host, hỏi operator |

**Cần người hỗ trợ:** agent không tự login admin, QA bàn giao session hoặc tự làm phần admin. Mail không về, CSV mẫu: `_flows/troubleshooting.md`, `_flows/test-data.md`.

## 5. Bẫy làm sai kết luận

| Dấu hiệu | Cách hiểu |
|---|---|
| Check nhắc nút Approve, Custom Conversion, menu Upload | UI admin cũ, đối chiếu `_flows/routes-api.md` |
| KB nói mọi admin có quyền như nhau, staging có Roles | Phân quyền thực tế `[?]`, không kết luận |
| Modal Request Payment không có ô nhập số tiền | Luôn rút toàn bộ `[RG]`, khác KB. Hỏi PO, chưa kết luận |
| `usage_maximum_amount` hiện "$0" | `0` là không giới hạn `[RG]` |
| Login account disapproved báo "not verified" | Account chưa verify, không phải lỗi login. Dùng F8 |
| Upload lại cùng file báo "0 created" | Chống trùng, không phải lỗi `[DOC]` |
| Banner upload không báo dòng lỗi | Dòng lỗi bị bỏ âm thầm `[DOC]`, tự đối chiếu số dòng |

## 6. Mutation guard

Staging dùng chung. Production chỉ đọc, và chỉ khi operator giao đúng việc đó.

**Được phép:** tạo affiliate, Program, shop tiền tố `QA-`/`qa-` · upload CSV chỉ chứa shop `QA-` · New conversion, VIP, disapprove, Invoice trên affiliate `QA-` (Invoice cần `KOIN_ALLOW_CREATE_INVOICE=yes`) · gọi Integration API với shop `qa-…`.

**Cấm:**

- Sửa, xoá Program, rate card, Payment Method, affiliate, shop không phải của mình. Chỉ dùng account trong env và account `QA-` tự tạo.
- Xoá hoặc tạo lại Payment Method PayPal, Payoneer: frontend hardcode id. Muốn test thì tạo method `QA-`.
- Tạo, sửa Level khi chưa được phép: thiếu rate card cho Level mới làm lỗi import của Program khác.
- Upload file Payout thật. Gửi tiền thật. Dùng thông tin thanh toán thật.
- Chạy console command, sửa DB.
- Dùng Embedded Version khi người khác đang test: nó ép mọi affiliate tải lại.

**Tác dụng phụ:** signup, verify, tạo Invoice bắn Slack kênh `affiliate` `[DOC]`, có vào kênh thật không `[?]`: hỏi operator trước khi chạy hàng loạt · `affiliate-account`, `invoice-payout` gửi email Brevo: chỉ dùng alias của `KOIN_SIGNUP_BASE_EMAIL` · Register bằng API bỏ qua blocklist `ref` `[RG]`: gọi thử là tạo tài khoản rác thật.

**Cleanup:** ghi id mọi thứ đã tạo và `balance` trước/sau. Action ngoài danh sách được phép và không có đường cleanup thì dừng, báo operator.

**Evidence phải che:** JWT, `X-API-Key`, password, `payment_info`, `payment_details`, email. Staging bật `APP_DEBUG`: cắt trace và đường dẫn server. Không lưu HTML form Edit affiliate: có password hash.
