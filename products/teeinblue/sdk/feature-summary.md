# SDK / Storefront runtime
**Published context version:** 26

**Product:** teeinblue · **Object:** `sdk` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `form-artwork-navigation` — Form Artwork Navigation (Quick navigation theo Product Base) | Merchant bật/tắt và đặt tên menu navigation riêng cho từng Product Base trong campaign; buyer trên storefront thấy thanh nav, tiêu đề section và pill gallery… | 16 | 13 | 2 | 0 |
| `game-text-preview-render` — Render preview live của layer shape-text, spiral, warp-text | Là buyer trên storefront, khi gõ text vào layer shape-text, spiral hoặc warp-text, tôi thấy preview của đúng text đã gõ mà không bị trống layer, và server kh… | 9 | 8 | 4 | 0 |
| `required-addon-validation` — Addon bắt buộc: chặn orphan và autofix giỏ hàng | Đơn có sản phẩm chính yêu cầu add-on không hoàn tất được khi thiếu hoặc không đủ add-on, và đơn chỉ còn addon line mà không có line chính cũng không hoàn tất… | 31 | 27 | 15 | 0 |
| `product-page-settings-config` — Cài đặt trang sản phẩm và callback open platform | La merchant (owner), cau hinh cach Teeinblue hien thi va van hanh tren trang san pham Shopify cua tung store (instance) da ket noi voi account -- gallery/moc… | 24 | 30 | 29 | 0 |
| `template-switch-photo-sync` — Ảnh buyer khi đổi template và reposition | Là buyer trên storefront, khi template đang chọn đổi (buyer chọn trực tiếp hoặc đổi Size/option map sang template/artwork khác), ảnh đã upload vào photo laye… | 35 | 39 | 31 | 0 |
| `storefront-customization-storage` — Lưu customization của buyer (localStorage, sync server) | Buyer giữ lại lựa chọn personalization qua reload và đến lúc Add to cart. | 16 | 11 | 9 | 1 |
| `storefront-translations` — Dịch giao diện widget storefront | Buyer thấy widget theo ngôn ngữ storefront, và chữ gốc khi API dịch lỗi. | 8 | 7 | 8 | 0 |
| `storefront-layer-visibility` — Hiển thị layer và option theo điều kiện trên storefront | Buyer thấy đúng layer và option theo điều kiện Hide/Show và Group ẩn. | 8 | 8 | 6 | 1 |
| `storefront-campaign-media-api` — Gallery media theo variant và API campaign storefront | Buyer thấy gallery đúng variant; SDK đọc đúng response campaign/platform product và cache. | 23 | 13 | 17 | 1 |
| `storefront-buyer-facing` — Campaign Storefront / Buyer-Facing Behavior | Là buyer/guest, xem và tương tác với sản phẩm của 1 campaign đã publish trên storefront (vượt password-gate, xem trang sản phẩm, chọn variant/personalize — b… | 47 | 90 | 68 | 1 |

KB object-level: 0 (`kb.json`).

## Open questions

CONFLICT 9 · NEEDS_CONFIRMATION 147 · OPEN_ISSUE 40 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`cart-addon-autofixer` · `open-platform-customization-callback` · `buyer-reposition` · `sync-selection-between-templates`
