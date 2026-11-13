# Box (mystery box = 1 variant Shopify): loại box Single/Bundle/Group-Tier, phần thưởng + xác suất, tạo/publish/xoá, version bất biến, tồn kho/pool, picking mode, pool refill
**Published context version:** 5

**Product:** mysbox · **Object:** `box` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `box-create-and-publish` — Tạo box, Draft/Active, publish, unpublish, xoá | Merchant tạo box từ một variant Shopify, điền Box settings, lưu (gặp đúng lỗi validation khi cấu hình sai), rồi publish/unpublish/xoá box để khách mua được h… | 106 | 51 | 32 | 2 |
| `box-type-and-prize-setup` — Chọn loại box và khai phần thưởng, xác suất, tier | Merchant chọn loại box (Single / Bundle / Group; tracked hoặc untracked; Group draw hoặc pool) cùng category giao prize, rồi khai danh sách item, số lượng ho… | 72 | 28 | 17 | 0 |
| `box-versioning` — Box version bất biến — đơn giữ cấu hình lúc mua | Merchant sửa box mà không làm đổi quà hay điều khoản buyback của đơn đã mua: thay đổi cấu hình khi lưu tạo version bất biến mới, đơn luôn đọc version đã gắn … | 55 | 22 | 15 | 1 |
| `admin-box-management` — Trang Box trong admin: Publish/Unpublish, Versions, Inventory, Recent pulls | Support xem box của một shop từ admin (overview, tier config, versions, inventory, recent pulls) và thao tác hộ merchant (publish/unpublish, resync/ẩn recent… | 59 | 23 | 12 | 2 |

KB object-level: 21 (`kb.json`).

## Open questions

CONFLICT 4 · NEEDS_CONFIRMATION 35 · OPEN_ISSUE 40 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`admin-box-management`
