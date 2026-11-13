# Artwork render — kết quả buyer, nhà in và hệ thống nhận được
**Published context version:** 1

**Product:** teeinblue · **Object:** `artwork-render` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `image-effects-run` — Run effects trên Photo layer | Merchant (owner hoặc staff có quyền Manage Artwork) bấm Run effects ở header "Image effects" của Photo layer (customization Normal, store không phải Etsy) để… | 36 | 53 | 37 | 1 |
| `storefront-clipart-selection` — Buyer chọn & xem clipart-category / group-clipart-categories trên storefront (personalization form → Preview → cart) | Buyer chọn 1 clipart (single-type) hoặc 1 nhóm clipart (group-type) trên personalization form của storefront, kỳ vọng: (1) lựa chọn được lưu lại qua reload/a… | 17 | 22 | 21 | 0 |
| `populate-value-tokens` — Token {{value.*}} của populate | Store owner dùng token {{value.*}} để điền giá trị layer từ input của buyer. | 14 | 6 | 12 | 2 |
| `populate-output-chain` — Populate {{output}} chain | Buyer nhận option populate {{output}} lấy kết quả đã xử lý của option nguồn. | 20 | 17 | 18 | 2 |
| `populate-channels-config` — Cấu hình kênh populate (content/font/color) | Store owner cấu hình các kênh populate content, font, color giữa các layer. | 12 | 40 | 24 | 0 |
| `print-design-render` — Render design file và ảnh in | Khi buyer đặt order với layer text dùng Color Sequence (rainbow, màu lặp theo từng chữ), ảnh Locate Artwork trên portal và Order Design PNG dùng để in phải t… | 40 | 59 | 57 | 2 |

KB object-level: 0 (`kb.json`).

## Open questions

CONFLICT 8 · NEEDS_CONFIRMATION 126 · OPEN_ISSUE 35 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`run-image-effects` · `run-effects-fill-in-variables` · `clipart-category-storefront-behavior` · `populate-values` · `text-color-sequence-render` · `group-layer-order-design-render` · `svg-to-image-rendering` · `layer-print-effects` · `no-personalization-photo-render` · `artwork-render`
