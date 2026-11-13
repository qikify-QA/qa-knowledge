# Admin ops — vận hành back-office nội bộ (đăng nhập/quyền, activity log, job/queue, release portal)
**Published context version:** 1

**Product:** mysbox · **Object:** `admin-ops` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `admin-login-and-roles` — Đăng nhập admin panel bằng Slack, role và quyền (Shield) | Chỉ nhân viên nội bộ có sẵn dòng admin user khớp tài khoản Slack, truy cập trên đúng admin host, mới vào được admin panel; mỗi người chỉ thấy và làm được phầ… | 53 | 19 | 14 | 0 |
| `admin-activity-log` — Activity log — ai đã làm gì trên admin panel | Nhân viên Mysbox truy được ai đã tạo/sửa/xoá gì trên admin panel (và ai đã tạo payment link) qua màn Activity log, với log lưu vô thời hạn. | 10 | 10 | 9 | 0 |
| `background-jobs-and-queue-monitoring` — Job định kỳ, độ trễ và theo dõi hàng đợi (Horizon) | Engineer/support hiểu job nền chạy thế nào (scheduler cho job theo lịch, hàng đợi cho việc theo sự kiện) để chẩn đoán trễ, theo dõi hàng đợi và job lỗi qua H… | 21 | 13 | 10 | 2 |
| `portal-release-version-control` — Embedded Version và Customer Portal Resource — đúng bản portal sau release | Engineer đổi giá trị Embedded Version / Customer Portal Resource trên admin panel để mọi merchant (portal nhúng) và mọi khách (trang khách trên storefront) t… | 14 | 10 | 11 | 0 |

KB object-level: 15 (`kb.json`).

## Open questions

CONFLICT 1 · NEEDS_CONFIRMATION 22 · OPEN_ISSUE 24 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`admin-login-and-roles` · `admin-activity-log` · `background-jobs-and-queue-monitoring` · `portal-release-version-control` · `admin-panel` · `admin-ops`
