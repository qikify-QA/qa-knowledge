# Order và bốc thăm: webhook orders/paid → order + opening request, chốt quà (winning), trạng thái đơn, đưa quà vào đơn Shopify, box physical vs digital
**Published context version:** 5

**Product:** mysbox · **Object:** `order-draw` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `physical-sealed-box-fulfilment` — Box physical (Sealed box): quà giấu kín, metafield/tag/note, trừ kho | Merchant bán box vật lý (Sealed box) mà khách không biết trước quà: sau khi bốc thăm, hệ thống tự đánh dấu box đã mở và chạy hậu xử lý một lần — ghi quà lên … | 74 | 31 | 21 | 2 |
| `prizes-added-to-order` — Quà được thêm vào đơn Shopify (dòng $0) | Merchant nhận quà digital ngay trên chính đơn Shopify (dòng quà giá gốc kèm giảm 100% "MYSBOX", giá cuối 0, chưa fulfill) để fulfil như hàng thường, đúng thờ… | 83 | 31 | 24 | 2 |
| `purchase-and-prize-draw` — Mua box và bốc thăm quà khi đơn paid | Khi khách thanh toán đơn có box qua checkout Shopify, hệ thống nhận thông báo đơn paid, tạo bản ghi đơn và opening request cho từng variant box, bốc thăm chố… | 73 | 37 | 30 | 1 |
| `admin-order-inspection-and-retry` — Màn Orders trong admin: tra đơn, retry, winning bundles | Support tra cứu đơn mua box của mọi shop, kiểm tra khách đã trúng gì và đã mở box chưa (tab Boxes, winning bundles, hậu xử lý box vật lý), chạy an toàn Retry… | 75 | 21 | 16 | 2 |

KB object-level: 34 (`kb.json`).

## Open questions

CONFLICT 6 · NEEDS_CONFIRMATION 46 · OPEN_ISSUE 43 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`admin-order-inspection-and-retry` · `order-draw`
