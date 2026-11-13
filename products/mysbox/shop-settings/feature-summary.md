# Shop settings — cấu hình shop và storefront widget (theme embed, custom code, bản dịch, đồng bộ dữ liệu)
**Published context version:** 1

**Product:** mysbox · **Object:** `shop-settings` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `general-settings` — General Settings và setting ẩn | Merchant cấu hình General Settings (Auto-unbox, thời gian resell, thông tin quà của sealed box, store credit Koin, Shopify Flow) với đúng giá trị mặc định, l… | 65 | 26 | 24 | 0 |
| `widget-custom-code` — Custom CSS / JS cho widget — ai được sửa | Shop tuỳ biến giao diện widget ngoài Style Settings bằng custom CSS/JS do Mysbox staff nhập ở admin panel (merchant không tự nhập), và biết custom code có hi… | 26 | 14 | 11 | 1 |
| `widget-theme-embed-setup` — Bật app embed, đặt block Mysbox và chỉnh Style Settings | Merchant tự bật theme app embed "Mysbox App" và đặt các block Mysbox (list box item, buy box by store credit, recent pulls, unboxing ở Thank-you/Order status… | 51 | 36 | 18 | 2 |
| `widget-translations` — Dịch văn bản khách thấy (Content & Translation) | Merchant (gói trả phí) chọn ngôn ngữ và sửa/dịch chữ khách thấy trên widget, trang reveal, checkout, tài khoản và trang đơn ở màn Content & Translation, để k… | 38 | 25 | 15 | 3 |
| `storefront-data-sync` — Dữ liệu storefront qua metafield / app proxy và độ mới | Khách thấy dữ liệu box, món, giá, tồn kho và trạng thái plan đúng và đủ mới trên widget trang sản phẩm, block checkout/tài khoản và trang đơn app proxy; merc… | 53 | 30 | 22 | 4 |

KB object-level: 6 (`kb.json`).

## Open questions

CONFLICT 9 · NEEDS_CONFIRMATION 45 · OPEN_ISSUE 37 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`general-settings` · `widget-custom-code` · `widget-theme-embed-setup` · `widget-translations` · `storefront-data-sync` · `storefront-widget` · `shop-settings`
