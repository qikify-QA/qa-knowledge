# Object: Account & Security (product: teeinblue) — Feature Profile Summary
**Published context version:** 5

- **Object:** login portal gồm Google login, trạng thái bảo mật staff, thao tác nhạy cảm, header acting-user, quyền ghi qua Hasura, webhook giá của Paddle. Không gồm quyền riêng của campaign (`campaign/campaign-security-permissions`).
- **Quan sát:** staging, role `merchant-owner`, một account owner đang 2FA off. Explorer không chủ động ghi gì ngoài một lần login hợp lệ; các POST tự phát sau login chưa xác định, xem OQ-account-security-015.
- **Knowledge:** 51 KB item: 15 `OBSERVED_CURRENT`/`LOW` từ quan sát; 31 `CONFIRMED_EXPECTED`/`MEDIUM` (29 từ lời dev ở Jira, KB-039 và KB-040 từ rule spec-hub), chưa được quan sát đối chiếu; 2 `INFERRED`/`LOW` về khác biệt môi trường (KB-049, KB-050), không làm oracle; 2 `OBSERVED_CURRENT`/`LOW` với status `KNOWN_DEFECT` theo lời dev (KB-025, KB-038); 1 `PROPOSED`/`LOW` (KB-031). 67 check: 46 `STRONG`, 12 `BASELINE`, 9 `NONE`. Hành vi quan sát được không phải expected requirement.
- **Chưa rõ ở mức object:** role áp dụng của các item role unspecified (OQ-account-security-054), hành vi đã lên production chưa (OQ-account-security-055), ý định sản phẩm của các hành vi rủi ro cao (OQ-account-security-056).
- **Open question:** 61 mục ở `open-questions.md`.

---

## `portal-login-paths` — Vào portal bằng đường đăng nhập đúng loại account

**Entry points:** `/login`, `/login?staff=true`; `/campaigns` khi chưa có session về `/login` (mới thử route này).

**Đã quan sát:**
1. `/login`: form store domain cho Shopify owner, link sang `/login?staff=true` và `/register`.
2. `/login?staff=true`: form email và password, widget Cloudflare, link Forgot password, Continue with Google, Shopify owner, Register, Re-send verification.
3. Login hợp lệ: `POST /api/login` 200, URL về `/`, không có bước 2FA với account 2FA off.

**Theo rule spec-hub (KB-039), chưa quan sát:** 2FA tuỳ chọn theo từng staff, không có setting ép cho cả organization. Khi bật, password đúng chỉ mở challenge 2FA có hiệu lực 5 phút; sai 5 mã thì phải làm lại từ đầu. Ý đồ sản phẩm chờ PO (OQ-account-security-058).

**Chưa quan sát:** nhánh lỗi, social login flow (lời dev ở `social-login`), account bật 2FA và `/login/two-factor`, các trang `/forgot-password`, `/register`, `/resend-verification`, cơ chế cookie session.
**Checklist:** 11 check, 9 `BASELINE`, 2 `STRONG` (CHK-010, CHK-011 cho account bật 2FA). **KB:** KB-001 đến KB-009, KB-039.

## `confirm-password-dialog` — Dialog xác nhận password (chưa quan sát được)

Dialog chưa quan sát được. Các quy tắc dưới đây là lời dev, chưa quan sát đối chiếu.

**Theo lời dev (KB-016 đến KB-020):**
1. Xác nhận xong có hiệu lực 15 phút, trong thời gian đó các action yêu cầu xác nhận chạy luôn.
2. Password toàn khoảng trắng: API trả "The provided password was incorrect.". Để trống: FE hiện "Enter your password." và không gọi API.
3. Dùng ở các nhóm action Staff, Role, Sessions, 2FA, API token (chỉ owner).
4. Hidden username là email của staff đang đăng nhập, không gửi lên API.

**Theo rule spec-hub (KB-040):** xoá role không yêu cầu xác nhận password, khác tạo và sửa role. Ý đồ sản phẩm chờ PO (OQ-account-security-059).

**Đã quan sát:** mở 12 trang/form về staff, role, profile, Integrations và API Keys không làm dialog hiện ra. Chỉ mở, không điền, không submit (KB-010 đến KB-012). Các item này không làm oracle.
**Chưa biết:** route và bước hiện dialog của từng action (OQ-account-security-016, OQ-account-security-035), mốc và phạm vi của 15 phút (OQ-account-security-033), request xác nhận (OQ-account-security-034).
**Checklist:** 14 check, 11 `STRONG`, 3 `NONE`. **KB:** KB-010 đến KB-012, KB-016 đến KB-020, KB-040.

## `staff-security-status` — Xem cột Security của staff trên danh sách staff

**Entry point:** sidebar Organization > Staff (`/staffs`).

**Đã quan sát:**
1. Bảng có các cột Avatar, Name, Email, Roles, Security, Last login, Action.
2. Chip trên 2 dòng mẫu, cả 2 role owner: "Password", "Shopify SSO", "Google", "2FA off"; và "Password", "2FA off".
3. Sau khi hover chip không thấy tooltip hay popover hiển thị.

**Theo lời dev (KB-030, KB-032), chưa quan sát đối chiếu:**
1. Staff cài từ Shopify có password hiện Password, Shopify SSO và chip 2FA thật. Staff không password đã đăng nhập Google hiện No password, Google, 2FA off. Invite pending chỉ hiện Pending invite.
2. Chip Google chỉ có sau lần Google login đầu tiên và vẫn còn sau logout; Google login bị từ chối không thêm chip Google.

**Đề xuất, chưa xác nhận (KB-031, không làm oracle):** một chip cho mỗi cách đăng nhập rồi tới chip 2FA; "2FA via Shopify" chỉ hiện khi Shopify là cách vào duy nhất. Câu chỉ có ở description ticket, không có comment id, xem OQ-account-security-057.

**Chưa biết:** role áp dụng của quy tắc chip (OQ-account-security-050), nhãn chip khi 2FA bật (OQ-account-security-051), nguồn dữ liệu chip, đường đăng nhập của staff không password, quy tắc cập nhật Last login.
**Checklist:** 9 check, 5 `STRONG`, 3 `BASELINE`, 1 `NONE` (CHK-007 chờ OQ-account-security-057). **KB:** KB-013 đến KB-015, KB-030 đến KB-032.

## `social-login` — Đăng nhập portal bằng Google

Toàn bộ là lời dev, flow chưa quan sát (OQ-account-security-001).

**Entry points:** nút "Continue with Google" ở view đăng nhập email/password của staff; `/auth/google/redirect` và `/callback`.

**Theo lời dev (KB-022 đến KB-024, KB-026 đến KB-029, KB-041 đến KB-048, KB-051):**
1. Vào default org khi access đã approved, nếu không thì fallback sang org approved khác, hết org thì `oauth_failed`. `invite_pending` chỉ hiện khi staff chưa từng accept invite nào; accept lời mời rồi thì Google login được. Staff bị owner xoá ở `/staffs` hoặc tự rời khỏi mọi org nhận `oauth_failed`.
2. Chỉ là đăng nhập, không tự tạo account. Email so khớp chính xác sau khi lowercase, không chuẩn hoá dấu chấm và +alias của Gmail; không khớp hoặc không có Staff thì `no_account`.
3. Staff chưa verify email bị từ chối, về `/login?social_error=email_unverified`. Mỗi mã từ chối về `/login?social_error=<code>` với toast và form email/password; text của `no_account`, `invite_pending`, `oauth_failed` ở KB-051. Cancel trên Google, đổi token lỗi, code Google đã dùng đều về `oauth_failed`.
4. Staff bật TOTP hoặc email 2FA qua cùng màn 2FA như sau password; mã hand-off sau callback dùng một lần, hết hạn theo `AUTH_EXCHANGE_TTL` (mặc định 60 giây), đổi trước 2FA. Cancel hoặc reload ở màn 2FA thì phải làm lại từ "Continue with Google". Staff tạo từ Shopify install vào được bằng Google, 2FA vẫn áp dụng.
5. Rate limit đặt bằng `GOOGLE_OAUTH_RATE_LIMIT`, theo IP, bucket riêng. Nút Google đã gỡ khỏi Register.

**Khác biệt môi trường, chưa xác nhận (KB-049, KB-050, không làm oracle):** QA thấy staging limit 6 request/phút/IP và 429 khi vượt; OAuth consent screen trên staging ở chế độ Testing nên Gmail phải là test user mới đăng nhập được.

**Known defect theo lời dev, không làm oracle:** KB-025 (tại 2026-10-27 callback chưa kiểm OAuth state, thay đổi kiểm state đang chờ, xem OQ-account-security-032), KB-038 (sau F5 toast hiện lại vì tham số social_error còn trên URL, xem OQ-account-security-047).
**Chưa biết:** giá trị rate limit theo môi trường (OQ-account-security-045), chế độ consent screen (OQ-account-security-060), `AUTH_EXCHANGE_TTL` của staging và route bước hand-off (OQ-account-security-061), ý định sản phẩm của các hành vi xác thực (OQ-account-security-062).
**Checklist:** 24 check, 21 `STRONG`, 3 `NONE`. **KB:** KB-022 đến KB-029, KB-038, KB-041 đến KB-051.

## `hasura-permission` — Giới hạn ghi và đọc qua Hasura GraphQL

Lời dev, chưa quan sát (OQ-account-security-027).

**Theo lời dev (KB-033 đến KB-036):** mutation ghi các cột ảnh trả lỗi và DB không đổi; các mutation xoá trực tiếp đã liệt kê trả lỗi và dòng vẫn còn; 33 bảng portal không query đã gỡ khỏi Hasura; `cliparts`, `clipart_categories`, `layer_images` chỉ trả dòng chưa soft-delete.
**Chưa biết:** danh sách mutation và cột ảnh (OQ-account-security-040), đọc cột ảnh (OQ-account-security-041), role và địa chỉ endpoint (OQ-account-security-042), tên 33 bảng (OQ-account-security-043).
**Checklist:** 4 check, 3 `STRONG`, 1 `NONE`. **KB:** KB-033 đến KB-036.

## `acting-user-organisation` — Header x-acting-user-id theo organisation đã duyệt

Lời dev, chưa quan sát (OQ-account-security-026).

**Theo lời dev (KB-021):** API kiểm header với danh sách organisation staff đã được duyệt ở mỗi request, không thuộc thì trả 403. Staff đã duyệt sửa được print area của org đó qua header này thì không phải lỗ phân quyền.
**Chưa biết:** phạm vi data ghi được (OQ-account-security-036), route áp dụng và body 403 (OQ-account-security-037).
**Checklist:** 3 check `STRONG`. **KB:** KB-021.

## `billing-webhook` — Webhook price.created của Paddle

Lời dev, chưa quan sát (OQ-account-security-028).

**Theo lời dev (KB-037):** giá tạo tay cho plan vẫn xử lý như trước; giá của usage charge được nhận diện và bỏ qua thay vì crash.
**Chưa biết:** endpoint và cách kích hoạt trên môi trường test (OQ-account-security-038), kết quả cụ thể của hai trường hợp (OQ-account-security-039).
**Checklist:** 2 check, 1 `STRONG`, 1 `NONE`. **KB:** KB-037.

## Chưa khám phá ở mức object

Multi-store (OQ-account-security-025), role khác owner (OQ-account-security-029). Nhóm cấu hình riêng trong response `GET /api/user`: OQ-account-security-030.
