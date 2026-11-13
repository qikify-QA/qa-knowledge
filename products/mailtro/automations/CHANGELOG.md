# CHANGELOG — automations

- 2026-10-08 (`bootstrap`, DOC_BOOTSTRAP) — Bootstrap đầu tiên từ bộ tài liệu QA-authored Mailtro trên Testlane (35 tài liệu, snapshot v1 2026-10-08). 7 feature, 219 KB item, 4 nhóm conflict mở, 48 open question.
- 2026-11-08 (maintenance-2026-11-08) — Chuẩn hoá reference theo namespace; sửa OQ và phân loại oracle/expected theo nguồn hiện có. Không xác nhận thêm requirement hoặc thay đổi hành vi sản phẩm.
- 2026-11-13 (restructure-2026-11-13) — Đổi cấu trúc theo contract §5 "Độ hạt object/feature": automations/automation-steps → automations/automation-wait-and-split-steps; automations/automation-steps → automations/automation-update-contact-field-step; automations/automation-steps → automations/automation-steps. Giữ nguyên kb_id, statement, nguồn và test steps; OQ chuyển object được mint id mới kèm `supersedes`.
