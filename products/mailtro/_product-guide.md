# Product guide — Mailtro

Bản đồ của product: có gì, ở đâu, test được không. Mọi bước đều đọc file này. Tối đa 10 KB. Định nghĩa: contract §5c.

- Đúng phải là gì: `<object>/features/<feature>/kb.json`, `checklists/`.
- Làm thế nào: `_flows/` (chưa có file nào; thêm qua khối C của CCR khi có cách thao tác đã verify).
- Biến env: chưa có `_env.example` (product chưa có môi trường explore).

Không dùng guide làm expected result. Không ghi giá trị credential, id, tên store.

## 1. Product
Mailtro là SaaS email marketing nhiều tenant theo workspace, **không phải Shopify app**. Hai domain: Mailtro ID (đăng nhập, đăng ký) và app của từng workspace. Gửi mail qua AWS SES nhiều region.

Luồng chính: đăng ký và tạo workspace → thêm contact (import/CSV, custom field) → segment → soạn email (library, editor, saved block, merge tag) → campaign (wizard 4 bước, gửi hoặc lên lịch) hoặc automation (trigger và step) → xem report → suppression và unsubscribe tác động lần gửi sau.

## 2. Object
Từ khoá ticket sang object: `_registry.json`. Feature của object: `<object>/feature-summary.md`. Không liệt kê feature key ở đây.

| Object | Phạm vi | Không thuộc |
|---|---|---|
| `auth` | Đăng ký, xác minh email, tạo workspace đầu, đăng nhập, 2FA, reset mật khẩu, chọn workspace, bảo mật tài khoản cá nhân | Quyền trong workspace (`workspace-settings`) |
| `contacts` | Danh sách/tìm kiếm, tạo/sửa, chi tiết, import/export CSV, custom field | Điều kiện động (`segments`) |
| `segments` | Segment động: list, builder, cách đánh giá audience | Danh sách contact thường |
| `deliverability` | Suppression (bounce/complaint), unsubscribe, chặn lúc gửi, pipeline sự kiện SES | Giới hạn lạm dụng (`abuse-guard`) |
| `email-content` | Email library, editor, saved blocks, merge tag | Preference page |
| `email-preferences` | Preference page cho người nhận chọn loại email, gắn vào campaign/automation | Unsubscribe (`deliverability`) |
| `campaigns` | List/folder, wizard 4 bước, preview/test, gửi/lên lịch, report, Analytics API | Automation |
| `automations` | List, builder (trigger/step), test dry-run, run history, report | Campaign |
| `workspace-settings` | Team member và role, API key và Public API, Claude connector, workspace profile, sending domain | Đăng nhập (`auth`) |
| `abuse-guard` | Giới hạn truy cập, kiểm nội dung, tự dừng gửi, màn staff, an toàn mail giao dịch (BE, MTRO-92) | Suppression do bounce (`deliverability`) |

## 3. Môi trường
Chưa có môi trường explore cho product này (`explore_enabled: false`): context chỉ đến từ tài liệu (dev doc, QA tự biên soạn, business rule), chưa có quan sát runtime do pipeline thực hiện. Chưa có biến env nào được khai. Mọi claim mang `scope.environment: documented`.

## 4. Test được gì
Chưa có khác biệt môi trường nào được ghi (`environment_differences` trống ở mọi feature). Khi test trên môi trường thật mà thấy khác tài liệu thì báo qua CCR, không sửa expected theo cảm tính.

Nhãn: `expected-unconfirmed` cho mục còn conflict (gửi campaign khi chưa có domain verified, cú pháp merge tag 1 hay 2 ngoặc, custom field key chuẩn hoá hay báo lỗi, segment count live hay chỉ khi Run, tên role thứ 3). Việc cần người hỗ trợ: workspace test, domain đã verify, hộp thư nhận mail test, quyền staff cho màn abuse guard.

## 5. Bẫy làm sai kết luận
| Dấu hiệu | Cách hiểu |
|---|---|
| `MTRO-inventory.md` tổng khác file module | Bản tổng lỗi thời, tin file theo module |
| Email library "đang đổi tên Templates" | Hai tên cùng một thứ, tìm theo cả hai |
| Mail không tới | Phân biệt suppression, abuse guard tự dừng gửi, domain chưa verify trước khi kết luận lỗi gửi |

## 6. Mutation guard
Chưa có môi trường explore nên chưa có quy tắc riêng. Khi test thật: không gửi tới danh sách contact thật, chỉ gửi tới hộp thư QA, không verify domain của khách, đặt tên workspace/campaign có tiền tố QA, che API key.
