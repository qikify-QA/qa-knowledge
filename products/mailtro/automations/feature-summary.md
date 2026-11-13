# Automations — list, builder (trigger/step), test dry-run, run history và Reports
**Published context version:** 3

**Product:** mailtro · **Object:** `automations` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `automation-builder` — Builder automation: dựng, lưu, kích hoạt và sửa flow trên canvas | Người dùng dựng flow trigger → step → action trên canvas, chỉ lưu và kích hoạt được khi flow đã đủ cấu hình, và biết điều gì xảy ra khi sửa một flow đang chạy. | 38 | 19 | 7 | 8 |
| `automation-list` — Danh sách automation: xem trạng thái, tìm, bật / tạm dừng, nhân bản và xoá flow | Người dùng workspace nắm được mọi flow automation cùng trạng thái draft / active / paused, tìm và lọc được flow cần xử lý, và từ danh sách bật, tạm dừng, nhâ… | 26 | 18 | 4 | 3 |
| `automation-reports` — Automation Reports: số liệu hiệu quả của flow trên canvas và theo step | Người dùng xem hiệu quả của flow (contact vào / hoàn thành, số qua từng step, gửi, mở, click, bounce, unsubscribe) theo khoảng thời gian, với định nghĩa số l… | 27 | 14 | 6 | 2 |
| `automation-run-history` — Run history và Run detail: theo dõi từng lượt contact chạy qua flow và thử lại run lỗi | Người dùng xem từng lượt contact đi qua flow cùng trạng thái / outcome, hiểu vì sao một run dừng, và thử lại run lỗi khi được phép. | 37 | 18 | 8 | 2 |
| `automation-test-run` — Test this flow: chạy thử (dry-run) flow đã lưu với một contact | Người dùng chạy thử flow đã lưu với một contact thật để xem contact sẽ đi qua những step nào mà không gửi, ghi hay mở gì thật. | 7 | 6 | 3 | 0 |
| `automation-triggers-and-entry` — Trigger và luật contact vào flow (khởi chạy theo sự kiện, re-entry, chống vòng lặp, nguồn không kích hoạt) | Flow bắt đầu đúng lúc một contact được tạo hoặc có field thay đổi, mỗi contact vào flow đúng số lần cho phép, và các flow không tự kích hoạt nhau thành vòng … | 23 | 11 | 8 | 1 |
| `automation-wait-and-split-steps` — Step Wait và Conditional split | Người dùng cấu hình độ trễ Wait và nhánh Conditional split trong automation. | 21 | 10 | 4 | 4 |
| `automation-update-contact-field-step` — Step Update contact field | Người dùng cấu hình action ghi custom field của contact trong automation. | 14 | 5 | 2 | 4 |
| `automation-steps` — Step Send email và biến/merge tag trong step | Người dùng cấu hình step Send email (sender, template, subject) và chèn biến. | 26 | 10 | 5 | 2 |

KB object-level: 0 (`kb.json`).

## Open questions

CONFLICT 3 · NEEDS_CONFIRMATION 24 · OPEN_ISSUE 21 — chi tiết trong `open-questions.md`.
