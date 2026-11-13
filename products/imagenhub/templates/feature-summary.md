# Templates — recipe tái sử dụng (model + prompt/variables + default inputs + post-processing + fallback), quản lý trên portal và gọi qua template_id
**Published context version:** 3

**Product:** imagenhub · **Object:** `templates` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `dynamic-upload-ratio` — Dynamic Upload Ratio (Aspect Ratio = Auto) | Người cấu hình đặt ratio của template là Auto để một template dùng được cho ảnh input nhiều shape: mỗi lần gọi, output được snap về ratio khả dụng gần nhất m… | 17 | 11 | 4 | 0 |
| `fallback-template` — Fallback template (IGH-226) | Người cấu hình gắn một template dự phòng (B) vào template chính (A) để khi A fail vì một trong các loại lỗi đã chốt, hệ thống tự động chạy B mà không cần xác… | 32 | 22 | 13 | 3 |
| `template-authoring` — Tạo, sửa và xoá template | Người cấu hình template tạo template mới từ một model (tên, mô tả, category, prompt và các param của model), cập nhật model/param của template có sẵn, thử te… | 30 | 21 | 10 | 2 |
| `template-library` — Thư viện template — duyệt, tìm kiếm, lọc, category và template public | Người dùng tìm được template cần dùng — template riêng hoặc template public do hệ thống cung cấp — qua trang Templates của portal (danh sách, tìm kiếm, lọc t… | 19 | 20 | 5 | 0 |
| `template-post-processing` — Post-processing của template — cấu hình chuỗi bước xử lý sau generate | Người cấu hình template nối thêm các bước xử lý ảnh (upscale, remove background, resize, face cutout...) chạy sau bước generate của template, biết trước chi … | 17 | 11 | 4 | 0 |
| `template-run-history` — Chạy template từ trang chi tiết và xem Run history | Người dùng chạy thử template ngay trên trang chi tiết (Run, Run in Batch) và xem lại các lần chạy trước của chính template đó — danh sách run, lightbox ảnh f… | 25 | 13 | 5 | 0 |
| `template-variables` — Biến {{variables}} trong prompt template | Người cấu hình khai báo biến {{...}} trong prompt của template để cùng một template sinh nội dung khác nhau theo giá trị được truyền vào lúc chạy — từ portal… | 19 | 8 | 4 | 0 |
| `teeinblue-ai-effect-setup` — Teeinblue AI Effect — kết nối ImagenHub vào Teeinblue | Người cấu hình store Teeinblue kết nối ImagenHub và gắn template ImagenHub vào Photo Upload Layer, để ảnh khách upload trên product Teeinblue được áp hiệu ứn… | 11 | 14 | 5 | 0 |

KB object-level: 3 (`kb.json`).

## Open questions

CONFLICT 0 · NEEDS_CONFIRMATION 27 · OPEN_ISSUE 24 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`teeinblue-ai-effect-setup` · `teeinblue-integration`
