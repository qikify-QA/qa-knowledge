# B2B Shopping List — list đã lưu, gửi duyệt / duyệt theo role, re-approval sau order, lưu sản phẩm / cart vào list, list do merchant quản lý / tạo hộ, reminder re-order
**Published context version:** 3

**Product:** duos · **Object:** `shopping-list` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `re-approval-after-order` — Đưa list đã duyệt về chờ duyệt sau mỗi order | Merchant bật setting để shopping list Approved tự về trạng thái chờ duyệt ngay khi order được submit từ list, buộc duyệt lại trước lần đặt sau; reminder của … | 9 | 9 | 5 | 0 |
| `reorder-reminder` — Nhắc re-order theo lịch | Người dùng shopping list đặt lịch nhắc re-order cho list (bật / tắt, tần suất, Pause / Resume, Skip next, View upcoming, Reschedule) và nhận email có CTA dẫn… | 5 | 7 | 1 | 0 |
| `shopping-list-approval` — Gửi duyệt và duyệt shopping list theo role | Junior Buyer gửi shopping list cho Senior Buyer hoặc Admin duyệt trước khi đặt hàng; nút submit / approve và quyền sửa list phụ thuộc role của người xem và s… | 12 | 11 | 2 | 0 |
| `save-and-add-to-cart` — Tạo list: lưu sản phẩm/cart vào list và list do merchant quản lý | Buyer lưu sản phẩm hoặc cart thành shopping list và thêm lại vào cart; merchant tạo/quản lý list hộ buyer. | 11 | 15 | 8 | 1 |

KB object-level: 2 (`kb.json`).

## Open questions

CONFLICT 1 · NEEDS_CONFIRMATION 13 · OPEN_ISSUE 6 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`merchant-managed-lists`
