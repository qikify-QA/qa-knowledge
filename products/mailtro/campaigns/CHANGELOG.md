# CHANGELOG — campaigns

- 2026-10-08 (`bootstrap`, DOC_BOOTSTRAP) — Bootstrap đầu tiên từ bộ tài liệu QA-authored Mailtro trên Testlane (35 tài liệu, snapshot v1 2026-10-08). 5 feature, 199 KB item, 2 nhóm conflict mở, 47 open question.
- 2026-11-08 (maintenance-2026-11-08) — Chuẩn hoá reference theo namespace; sửa OQ và phân loại oracle/expected theo nguồn hiện có. Không xác nhận thêm requirement hoặc thay đổi hành vi sản phẩm.
- 2026-11-13 (restructure-2026-11-13) — Đổi cấu trúc theo contract §5 "Độ hạt object/feature": campaigns/campaign-report → campaigns/campaign-report-metrics; campaigns/campaign-report → campaigns/analytics-api; campaigns/campaign-report → campaigns/campaign-report; campaigns/campaign-wizard → campaigns/campaign-wizard-recipients; campaigns/campaign-wizard → campaigns/campaign-wizard-contents; campaigns/campaign-wizard → campaigns/campaign-wizard. Giữ nguyên kb_id, statement, nguồn và test steps; OQ chuyển object được mint id mới kèm `supersedes`.
