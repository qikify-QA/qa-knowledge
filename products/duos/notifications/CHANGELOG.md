# CHANGELOG — notifications

- 2026-10-09 (`bootstrap`, DOC_BOOTSTRAP) — Bootstrap đầu tiên từ bộ tài liệu QA-authored Duos B2B trên Testlane (24 tài liệu, snapshot v1 2026-10-09). 4 feature, 41 KB item, 0 nhóm conflict mở, 28 open question.
- 2026-11-08 (maintenance-2026-11-08) — Chuẩn hoá reference theo namespace; sửa OQ và phân loại oracle/expected theo nguồn hiện có. Không xác nhận thêm requirement hoặc thay đổi hành vi sản phẩm.
- 2026-11-13 (restructure-2026-11-13) — Đổi cấu trúc theo contract §5 "Độ hạt object/feature": notifications/sender-reply-to + notifications/merchant-transactional-emails + notifications/flow-email-triggers → notifications/email-sender-and-routing. Giữ nguyên kb_id, statement, nguồn và test steps; OQ chuyển object được mint id mới kèm `supersedes`.
