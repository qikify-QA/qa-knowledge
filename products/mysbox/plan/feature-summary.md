# Plan — gói Mysbox, capacity theo chu kỳ, nâng/hạ/huỷ và catalog plan
**Published context version:** 1

**Product:** mysbox · **Object:** `plan` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `plan-capacity-and-cycle` — Plan, capacity box miễn phí theo chu kỳ 30 ngày và trial | Mỗi shop có một plan (Free, trả phí, trial, Early-bird) với hạn mức box miễn phí theo chu kỳ 30 ngày neo vào ngày cài app lần đầu; hệ thống đếm đúng số box đ… | 89 | 28 | 20 | 0 |
| `plan-upgrade-downgrade-cancel` — Nâng, hạ, huỷ plan và trang xem trước thay đổi | Merchant chọn và đổi plan Mysbox phù hợp với loại store của mình (nâng, hạ, hoặc huỷ về Free) qua màn Pricing hoặc link thanh toán, duyệt subscription trên S… | 114 | 36 | 29 | 2 |
| `plan-catalog-administration` — Quản lý catalog Plan trong admin panel | Đội billing / admin nội bộ tạo và sửa Plan trong admin panel (giá, trial, capacity, quy tắc phí usage, discount mang sẵn, Visible, cờ Plus / Shopify-paid / T… | 35 | 15 | 9 | 2 |

KB object-level: 12 (`kb.json`).

## Open questions

CONFLICT 10 · NEEDS_CONFIRMATION 22 · OPEN_ISSUE 28 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`plan-capacity-and-cycle` · `plan-upgrade-downgrade-cancel` · `plan-catalog-administration` · `plans-billing` · `cách tính phí box vượt capacity (count-based và value-tiered)`
