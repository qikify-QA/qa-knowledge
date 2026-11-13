# Artwork layer config — cấu hình riêng theo layer type và điều kiện hiển thị
**Published context version:** 1

**Product:** teeinblue · **Object:** `artwork-layer-config` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `text-layer-config` — Cấu hình layer nhóm TEXT (kể cả multi-stroke) | Store owner tạo viền nhiều lớp cho layer Paragraph trên artwork Artwork 2.0 (tối đa 3 vòng, mỗi vòng có màu và độ dày riêng, xếp từ mép chữ ra ngoài), sắp xế… | 31 | 42 | 40 | 0 |
| `photo-upload-layer-config` — Photo Border (viền ảnh) trên layer: cấu hình và kết quả vẽ viền | Store owner / staff có quyền sửa artwork bật và cấu hình viền ảnh (Border) cho layer trong Artwork editor — kiểu Contour cut hoặc Custom shape, màu, Border s… | 20 | 64 | 72 | 1 |
| `gen-ai-layer-config` — Cấu hình Gen AI trên layer ảnh | Store owner cấu hình Gen AI (provider, model, output size, prompt) cho layer ảnh trong artwork editor. | 30 | 23 | 7 | 2 |
| `clipart-layer-config` — Cấu hình layer clipart | Store owner cấu hình layer Clipart Category và Dynamic Clipart trong artwork editor. | 20 | 20 | 2 | 0 |
| `vector-layer-config` — Cấu hình layer — nhóm sidebar VECTOR (field/behavior riêng từng layer type) | Store owner cấu hình field/behavior CHỈ thuộc riêng từng layer type trong nhóm sidebar VECTOR khi thêm layer trong artwork editor. Nhóm gồm 3 layer type: Sta… | 11 | 16 | 14 | 0 |
| `special-layer-config` — Cấu hình layer nhóm PUZZLES, OTHERS, MAPS & ASTRONOMY | Store owner cấu hình field/behavior CHỈ thuộc riêng từng layer type trong nhóm sidebar MAPS & ASTRONOMY khi thêm layer trong artwork editor. Nhóm gồm 4 layer… | 28 | 32 | 23 | 0 |
| `form-elements-config` — Form elements và thứ tự field | Store owner cấu hình field/behavior CHỈ thuộc riêng từng layer type trong nhóm sidebar FORM ELEMENTS khi thêm layer trong artwork editor. Nhóm gồm 6 layer ty… | 16 | 18 | 14 | 1 |
| `conditional-setting-config` — Cấu hình điều kiện hiển thị layer (Conditional Setting) | Store owner cấu hình điều kiện show/hide 1 layer dựa trên giá trị của layer khác trong cùng artwork, qua accordion CONDITIONAL SETTING. | 15 | 33 | 26 | 0 |
| `condition-cycle-validation` — Ngăn vòng lặp phụ thuộc điều kiện (Circular Condition Validation) | Hệ thống ngăn không cho lưu 1 artwork mà đồ thị điều kiện hiển thị (Conditional Setting) giữa các layer tạo thành vòng lặp phụ thuộc, để tránh trạng thái khô… | 6 | 13 | 10 | 0 |

KB object-level: 0 (`kb.json`).

## Open questions

CONFLICT 6 · NEEDS_CONFIRMATION 178 · OPEN_ISSUE 24 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`text-multi-stroke` · `layer-config-text` · `layer-photo-border` · `layer-config-image` · `layer-config-vector` · `layer-config-maps-astronomy` · `layer-config-puzzles` · `layer-config-others` · `layer-config-form-elements` · `form-field-reorder` · `conditional-setting-config` · `layer-condition-value-binding` · `condition-cycle-validation` · `artwork-layer-config`
