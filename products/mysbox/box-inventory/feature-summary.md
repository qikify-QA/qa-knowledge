# Box inventory — tồn kho, picking mode và pool refill của box
**Published context version:** 1

**Product:** mysbox · **Object:** `box-inventory` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `inventory-and-sold-out` — Tồn kho tracked/untracked, pool, sold-out và hiển thị tồn kho | Merchant theo dõi tồn kho món thưởng (tracked/pool) và chọn cách box xử lý khi hết món, để box ngừng bán, tự tắt hoặc tiếp tục bán đúng lúc, đồng bộ với Shop… | 94 | 42 | 25 | 4 |
| `picking-modes` — Picking mode — cách bốc item (mặc định, unique trong đơn, unique giữa các set, Group draw/pool) | Merchant chọn cách hệ thống bốc item cho mỗi hộp để kiểm soát trùng lặp và phân phối quà: bốc độc lập mặc định, không lặp item trong một đơn, hay với box Gro… | 56 | 26 | 23 | 0 |
| `pool-refill` — Pool refill — trả món đã resell về pool (AUTO/MANUAL) | Merchant có box Group (Tier) chế độ pool muốn món khách đã resell được trả lại pool — tự động (AUTO) hoặc giữ trong bộ đệm chờ áp dụng (MANUAL) — để nhóm khô… | 53 | 22 | 15 | 1 |

KB object-level: 1 (`kb.json`).

## Open questions

CONFLICT 5 · NEEDS_CONFIRMATION 28 · OPEN_ISSUE 30 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`inventory-and-sold-out` · `picking-modes` · `pool-refill` · `box-inventory`
