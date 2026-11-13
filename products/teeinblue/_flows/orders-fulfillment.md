# Orders, line item status, fulfillment provider

Order từ storefront và cách xem trong portal: `storefront-sdk.md` mục Checkout & order.

## Đổi status line item (quan sát 2026-10-29, TIB-5439)

- **Item-level** chỉ có ở `Bulk Fulfill` → danh sách theo status → tick item → `Change status` ⇒ `PUT /api/instances/{id}/order-items/status`.
- Order detail và Orders list đổi ở **order-level** ⇒ `PUT /api/orders/tib-status`.
- Paused có endpoint riêng `POST /order-items/pause` kèm reason.
- Item ở tab Canceled không có `Change status`.
- Regenerate design không đổi status item.
- Re-generate design trên order detail là theo từng printarea: icon refresh (tooltip "Re-generate design") trên từng design, không có nút cho cả item; mỗi lần xong thêm 1 dòng "Line item has generated a new design" vào Item Activity logs. (quan sát 2026-11-10, TIB-5625)

## Fulfillment provider

- merchOne = Picanova (đổi tên): portal hiện `merchOne`, route vẫn `/fulfillments/picanova`; toast có thể `[Picanova]` hoặc `[merchOne]` theo `fulfillments.display_name`. (TIB-5548)
- Store chưa connect fulfillment: account onboarding trong catalog data của QA.

## Đọc payload đã gửi provider (TIB-5724, 2026-11-10)

- Portal UI không hiện body gửi provider: Item Activity logs chỉ có subject; danh sách Bulk Fulfill chỉ có cột Fulfiller ID.
- Body đã gửi đọc qua network của trang Bulk Fulfill: `GET /api/instances/{id}/order-items?status=<n>` (Items Sent = 8) → mỗi item có `fulfiller.request_data` (body đã gửi; key có thể bị sắp lại thứ tự, không dùng để kiểm vị trí key) và `fulfiller.metadata` (response provider).
- Item gửi lỗi (status 7, Failed) không có `fulfiller`; lý do lỗi chỉ ở Item Activity logs / Latest log của order detail.
- `request_data` có `api_key` của provider: che trước khi lưu evidence.
- Gửi chỉ 1 item khi còn item khác cùng địa chỉ → modal "Send only selected / Send all items"; chỉ có 1 item → modal "Confirm & send".

## Đọc tier usage gói Blue sau khi đặt order (TIB-5625, 2026-11-10/11)

- QA không có quyền admin "Tier usages"; đọc từ portal merchant.
- Organization > Subscriptions > Shopify Manage (`/subscriptions/shopify-tier`): "Current cycle (reset on …)", "Order items: N", "Next tier", Usages. Đối chiếu N với `cycle.unit_count` của `GET /api/user`.
- Nút View usages (`/platform-usages/shopify`): mỗi tier usage một dòng, cột PLATFORM, DOMAIN, ORDER, QUANTITY, FEE, FREE, CHARGED, CREATED AT. Dòng usage xuất hiện vài giây sau order. Cách đếm usage: KB của `subscription/tier-usage-metering`.
- Mốc tier: `GET /api/platforms/shopify/tier-plans`, `starting_from` của từng tier. Mốc gửi email chuyển tier và count cần đẩy tới: KB của `subscription/tier-usage-metering`.
- Ghi baseline Order items và số dòng ngay trước khi đặt order. [?] Cycle hiển thị có thể là cycle cũ đã quá ngày reset; order đầu tiên sau đó mở cycle mới (OQ-subscription-038).
- Order test Bogus trên dev store staging có được đếm, khác chữ lưu ý trên trang Usages (OQ-subscription-035).
