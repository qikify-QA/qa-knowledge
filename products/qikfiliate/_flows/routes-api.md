# Route, menu admin, request

## Route Dashboard `[RG]`

`#/login`, `#/signup`, `#/verification`, `#/verified`, `#/resend-verification`, `#/forgot-password`, `#/dashboard`, `#/links`, `#/conversions`, `#/customers`, `#/invoices`, `#/account`. Nav Resources mở Google Drive.

## Menu admin `[RG]`

Profile, Embedded Version, Admin Users, Roles, Activities, Upload Payouts, Conversions, Customer Events, Customers, Tracking Informations, Affiliate Users, Invoices, Payment Methods, Levels, Program Commissions, Programs.

Check mô tả UI cũ thì đối chiếu bảng này rồi test mục tiêu của check trên UI mới:

| KB nói | Trên staging |
|---|---|
| Nút "Approve" trên danh sách | Approve qua form Edit |
| Disapprove qua form Edit | Có thêm row action "Disapproved" và "Disapproved and send notification" |
| Màn Custom Conversion, nút "Add Custom Conversion" | "New conversion" ở Conversions |
| Upload ở menu Conversion | Màn riêng Upload Payouts |
| Màn Populate/reconcile | Không thấy |
| Switch `visible` sửa nhanh trên danh sách | Không còn sửa nhanh trên danh sách |
| Không có audit log | Activities ghi lại thay đổi, kể cả do hệ thống |

## API Dashboard

JWT Bearer, base `<KOIN_DASHBOARD_URL>/api`, `[RG]`:

| Method + path | Việc |
|---|---|
| `POST /api/register` | Đăng ký |
| `POST /api/login`, `/api/refresh`, `/api/logout` | Phiên đăng nhập |
| `POST /api/email/resend`, `POST /api/password/email` | Gửi lại xác thực, quên mật khẩu |
| `GET /email/verify/{id}/{hash}?expires&signature` | Link xác thực, redirect về `/` |
| `GET /api/user` | Thông tin affiliate: `balance`, `can_create_invoice`, `bonus_at`, `payment_method`, `payment_details` |
| `GET /api/payment-methods`, `PUT /api/user/payment-method` | Danh sách theo country, lưu thông tin nhận tiền |
| `POST /api/invoices`, `PUT /api/invoices/{code}` | Tạo, huỷ yêu cầu thanh toán. `{code}` là mã invoice, không phải id số |

API list phân trang có `meta.total`.

## Integration API

Header `X-API-Key`, tất cả `[DOC]`, host `[?]`. Payload mẫu: `test-data.md` F3.

| Method + path | Việc |
|---|---|
| `POST /api/tracking-id` | Ghi một lượt click |
| `POST /api/customers` | Tạo shop, tiêu thụ `tracking_id` |
| `DELETE /api/customers` | Soft-delete shop |
| `PUT /api/trashed-customers` | Khôi phục shop |
| `POST /api/customer-events` | Ghi sự kiện vòng đời |

Console command, chỉ dev chạy trên server `[DOC]`: `user-level:update`, `conversion-type:update`, `charge_creation_time:fill`.
