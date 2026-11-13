# Campaigns — list & folder, wizard 4 bước, preview & test, gửi/lên lịch, report & Analytics API
**Published context version:** 3

**Product:** mailtro · **Object:** `campaigns` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `campaign-list-and-folders` — Danh sách campaign: tìm, lọc, folder, nhân bản và xoá | Người dùng workspace tìm và tổ chức campaign theo trạng thái và folder, mở đúng màn theo trạng thái của campaign (wizard cho bản nháp, report cho campaign đã… | 41 | 30 | 8 | 4 |
| `campaign-preview-and-test` — Preview & test send campaign | Người dùng xem email của campaign hiển thị thế nào trên desktop/mobile và gửi bản test cho mình hoặc đồng đội trước khi gửi thật. | 6 | 8 | 4 | 0 |
| `campaign-send-and-schedule` — Gửi ngay / lên lịch campaign và điều kiện được gửi | Người dùng gửi campaign tới segment ngay lập tức hoặc theo lịch, và campaign chỉ được gửi khi đủ điều kiện (đủ 4 bước, segment và email hợp lệ, workspace khô… | 19 | 17 | 5 | 3 |
| `campaign-report-metrics` — Định nghĩa metric của campaign report và analytics | Người dùng hiểu đúng cách tính sent/open/click/complaint/unsubscribe và rate trong report và analytics. | 22 | 15 | 3 | 0 |
| `analytics-api` — Analytics API cho campaign report và analytics toàn cục | Hệ thống ngoài/MCP đọc số liệu campaign và global qua analytics API với scope và định dạng đúng. | 10 | 7 | 4 | 0 |
| `campaign-report` — Report của campaign: các tab, trạng thái chưa gửi và lỗi route | Người dùng mở report của campaign và đọc đúng số liệu, tab, audience, preview ở mọi trạng thái campaign. | 40 | 15 | 12 | 6 |
| `campaign-wizard-recipients` — Wizard campaign: bước Recipients | Người dùng chọn segment người nhận và khối Email preferences cho campaign. | 14 | 8 | 3 | 1 |
| `campaign-wizard-contents` — Wizard campaign: bước Contents | Người dùng chọn, tạo hoặc reset email design cho campaign. | 14 | 12 | 3 | 0 |
| `campaign-wizard` — Wizard campaign: stepper, lưu, bước Campaign details và Sender | Người dùng đi qua stepper wizard, lưu draft và điền Campaign details, Sender. | 33 | 23 | 5 | 4 |

KB object-level: 0 (`kb.json`).

## Open questions

CONFLICT 1 · NEEDS_CONFIRMATION 32 · OPEN_ISSUE 14 — chi tiết trong `open-questions.md`.
