# Artwork
**Published context version:** 49

**Product:** teeinblue · **Object:** `artwork` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `artwork-live-preview-asset-load` — Live preview của artwork tải ảnh clipart lớn kèm version của clipart category (?v=) | Là merchant, khi mở Live preview của artwork (trong Artwork editor hoặc từ Campaign editor), mình thấy layer clipart / group clipart / background clipart hiể… | 6 | 7 | 5 | 1 |
| `artwork-save-persist` — Lưu và đọc lại artwork (Save & Close, API/auth dependency) | Store owner lưu toàn bộ thay đổi (layer/template) của artwork từ editor xuống server một cách đáng tin cậy, và hệ thống đọc lại đúng dữ liệu đã lưu ở lần mở … | 30 | 37 | 30 | 2 |
| `artwork-template-management` — Quản lý template bên trong 1 artwork | Store owner tạo/nhân bản/sửa/ẩn/convert các phiên bản template (biến thể layout) trong cùng 1 artwork, qua thanh Template ở panel trái editor; với global tem… | 5 | 17 | 11 | 0 |
| `psd-import` — Import artwork từ file PSD (giữ trạng thái ẩn của folder) | Store owner tạo artwork từ file PSD qua Artworks > Import > PSD Single template và nhận được artwork giữ đúng cấu trúc/trạng thái ẩn của file: folder ẩn tron… | 3 | 8 | 3 | 0 |
| `artwork-list-and-clone` — Danh sách artwork và clone sang store khác | Store owner/staff xem và thao tác nhanh trên các artwork đã tạo (preview, sửa chi tiết, nhân bản, gửi dịch, archive, xoá) từ trang danh sách /artworks. | 11 | 22 | 19 | 0 |

KB object-level: 0 (`kb.json`).

## Open questions

CONFLICT 5 · NEEDS_CONFIRMATION 53 · OPEN_ISSUE 14 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`artwork-cross-store-clone` · `artwork-list-management`
