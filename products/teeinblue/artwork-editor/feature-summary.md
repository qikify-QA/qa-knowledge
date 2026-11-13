# Artwork editor — thao tác canvas dùng chung cho mọi layer
**Published context version:** 1

**Product:** teeinblue · **Object:** `artwork-editor` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `editor-layer-workspace` — Không gian làm việc chung của Editor (thêm layer, chọn layer, toolbar/action bar) | Store owner thêm layer mới vào artwork và thao tác chọn/toolbar dùng chung trong canvas editor, độc lập với việc cấu hình chi tiết bên trong từng layer type. | 27 | 47 | 37 | 0 |
| `layer-bulk-edit` — Bulk edit layer và bản HD của layer ảnh | Store owner / staff có quyền sửa artwork chọn một hoặc nhiều layer trong artwork editor và sửa một lần các setting chung cho mọi layer editable đã chọn (Opti… | 30 | 31 | 21 | 0 |
| `transform-multi-select` — Transform popover khi chọn nhiều layer: Apply for Group/Individual, box cá nhân và box nhóm, Flip nhóm (Artwork 2.0), popover không có Apply for (Artwork 1.0) và Reverse reposition direction | Là seller (owner/staff) trong artwork editor, khi chọn nhiều layer và mở Transform, mình chỉnh kích thước/vị trí cho cả nhóm hoặc từng layer: ở Artwork 2.0 c… | 21 | 20 | 24 | 0 |
| `layer-duplicate-link-copy` — Nhân bản layer với liên kết cấu hình (Duplicate & Link options) | Store owner nhân bản 1 layer, tuỳ chọn giữ đồng bộ cấu hình (design/personalization) với layer gốc thông qua nút 'Duplicate & Link options' trên layer action… | 24 | 33 | 30 | 0 |
| `group-layer-effective-visibility` — Effective visibility của Group layer (ẩn Group ẩn cả nhánh, giữ cờ riêng của layer con) | Store owner ẩn/hiện một Group trong Artwork Editor 2.0 để tạm ẩn cả nhánh layer bên dưới (kể cả Group lồng, Group có mask) mà không làm mất cờ ẩn/hiện riêng … | 11 | 15 | 7 | 0 |

KB object-level: 7 (`kb.json`).

## Open questions

CONFLICT 20 · NEEDS_CONFIRMATION 90 · OPEN_ISSUE 9 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`editor-layer-workspace` · `layer-common-config` · `layer-bulk-edit` · `layer-image-hd-copy` · `transform-multi-select` · `layer-duplicate-link-copy` · `group-layer-effective-visibility` · `artwork-editor`
