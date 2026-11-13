# CHANGELOG — shopping-list

- 2026-10-09 (`bootstrap`, DOC_BOOTSTRAP) — Bootstrap đầu tiên từ bộ tài liệu QA-authored Duos B2B trên Testlane (24 tài liệu, snapshot v1 2026-10-09). 5 feature, 39 KB item, 1 nhóm conflict mở, 20 open question.
- 2026-11-08 (maintenance-2026-11-08) — Chuẩn hoá reference theo namespace; sửa OQ và phân loại oracle/expected theo nguồn hiện có. Không xác nhận thêm requirement hoặc thay đổi hành vi sản phẩm.
- 2026-11-13 (restructure-2026-11-13) — Đổi cấu trúc theo contract §5 "Độ hạt object/feature": shopping-list/save-and-add-to-cart + shopping-list/merchant-managed-lists → shopping-list/save-and-add-to-cart. Giữ nguyên kb_id, statement, nguồn và test steps; OQ chuyển object được mint id mới kèm `supersedes`.
