# Usage billing — phí usage, charge hằng ngày, giới hạn capacity
**Published context version:** 1

**Product:** mysbox · **Object:** `usage-billing` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `usage-fee-pricing` — Cách tính phí box vượt capacity (count-based và value-tiered) | Merchant trên plan trả phí bị tính đúng phí cho mỗi box bán vượt quota của chu kỳ theo cách tính của plan (theo số lượng hoặc theo giá trị dòng hàng với Min … | 60 | 18 | 16 | 0 |
| `daily-usage-charge-and-charge-status` — Job usage charge hằng ngày và trạng thái Charge | Mysbox gom phí box vượt quota của mỗi shop trả phí thành một Shopify usage charge mỗi ngày (đánh dấu dòng phí đã tính trước khi gọi Shopify, nên lỗi thì thu … | 87 | 19 | 16 | 7 |
| `capacity-limit-enforcement` — Chạm trần capacity (Free): gỡ xuất bản box và ẩn storefront | Khi shop plan Free chạm trần capacity của chu kỳ, hệ thống chặn bán box mới: gỡ xuất bản mọi box, khoá nút tạo box, ẩn widget / khối Unbox / danh sách món / … | 46 | 14 | 16 | 0 |

KB object-level: 10 (`kb.json`).

## Open questions

CONFLICT 3 · NEEDS_CONFIRMATION 19 · OPEN_ISSUE 26 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`usage-fee-pricing` · `daily-usage-charge-and-charge-status` · `capacity-limit-enforcement` · `usage-billing`
