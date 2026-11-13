# Hạ tầng tích hợp: xác thực từng kênh gọi API (portal nhúng, extension, Flow) và nhận webhook Shopify/EventBridge
**Published context version:** 4

**Product:** mysbox · **Object:** `integrations` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `request-authentication` — Xác thực request vào Mysbox API theo từng kênh | Mỗi loại client gọi vào Mysbox API (portal nhúng của merchant trong Shopify admin, Shopify Flow, các extension ở checkout / trang cảm ơn / tài khoản khách / … | 18 | 14 | 14 | 1 |
| `webhook-ingestion` — Nhận webhook Shopify / EventBridge an toàn và đúng một lần | Webhook Shopify đến Mysbox (HTTP trực tiếp tại /webhook ở staging, qua AWS EventBridge tại /webhook/event-bridge ở production) được xác thực, kiểm hợp lệ, gi… | 45 | 21 | 19 | 3 |
| `shopify-flow-actions` — Shopify Flow action gọi vào Mysbox | Merchant dùng các action Shopify Flow của Mysbox để mở mọi box digital chưa mở của một đơn, gỡ dòng box digital khỏi đơn đã hoàn tất, hoặc đưa đơn đã thanh t… | 38 | 17 | 12 | 0 |
| `shopify-flow-triggers` — Shopify Flow trigger từ Mysbox | Merchant có Shopify Flow bật trigger Mysbox và dựng workflow tự động trên 5 trigger (All box opened, Order unboxing soon, Resell completed, Box sold out, Dig… | 67 | 29 | 12 | 2 |
| `partner-events-bigquery-sync` — Đồng bộ Shopify Partner events sang BigQuery (báo cáo nội bộ) | Team nội bộ có các sự kiện Shopify Partner của ngày UTC hôm trước trong bảng BigQuery mỗi ngày lúc 07:00 UTC để làm báo cáo nội bộ; khi cần, engineer nạp bù … | 20 | 10 | 4 | 1 |
| `affiliate-referral-tracking` — Affiliate / referral tracking merchant mới (Qikfiliate) | Đối tác affiliate được ghi nhận khi giới thiệu merchant mới: link đối tác cấp tracking id và cookie theo dõi, lần vào app nhúng đầu tiên trong 30 phút sau cà… | 44 | 16 | 10 | 1 |

KB object-level: 6 (`kb.json`).

## Open questions

CONFLICT 3 · NEEDS_CONFIRMATION 37 · OPEN_ISSUE 36 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`shopify-flow-actions` · `shopify-flow-triggers` · `partner-events-bigquery-sync` · `affiliate-referral-tracking` · `automation-growth`
