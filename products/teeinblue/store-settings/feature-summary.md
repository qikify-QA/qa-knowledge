# Object: Store Settings (product: teeinblue) — Feature Profile Summary
**Published context version:** 2

- **Object:** cấu hình chung cấp store (instance) của merchant trên portal: trang General Settings (`/general-settings`, link đầu tiên của nhóm sidebar Store Settings). Trang hiển thị cài đặt của store đang chọn ("For store", "(Switch store?)"), có một cặp nút Save/Reset cấp trang và 10 card setting, trong đó có Order storage time (field và API `expired_time`).
- **Không thuộc:** Product Page Settings (`sdk/product-page-settings-config`); Product Page Content (`translation`); các trang khác trong nhóm Store Settings (Customization Image, Shipping Methods, Inventory Locations, SKU Mapping) chưa có object; Extras > 3rd-party Services (`third-party-services`); plan và pricing (`subscription`); token API và MCP (`open-api`, `mcp`); hành vi của Bulk Fulfill, order Shopify và cart storefront mà các card bật/tắt (`order`, `sdk`).
- **Quan sát:** staging, role `merchant-owner`, account explore, một store, một phiên. Chỉ xem: không bấm Save/Reset, không click radio/toggle, không gõ vào ô, không đổi store.
- **Knowledge:** 26 KB item, tất cả `OBSERVED_CURRENT`/`LOW`. Không có `CONFIRMED_EXPECTED`, không có conflict. 28 check: 18 `BASELINE`, 10 `NONE`. Hành vi quan sát được không phải expected requirement.
- **Open question:** 11 mục ở `open-questions.md`. Check `BASELINE` chờ PO/Dev xác nhận ở OQ-store-settings-010 và 011.

---

## `expired-time-setting` — Thời gian lưu order (Order storage time)

**Cập nhật CBS-163 (TIB-5689):** index/update có `expired_time`, không `instance_id`, trả `[]` khi chưa có giá trị (KB-1656, `CONFIRMED_EXPECTED`/MEDIUM theo Dev, trả lời một phần OQ-store-settings-003); quan sát test case: lưu rồi reload giữ giá trị (KB-1657, `OBSERVED_CURRENT`/LOW, ghi vào OQ-store-settings-004). CHK-007 nay `BASELINE`, CHK-008 `STRONG`.
**Entry points:** `/general-settings`, card "Order storage time".

**Đã quan sát:** card có help text về thời gian lưu order (gồm order item, design, customer info), không áp cho ảnh buyer (tự xoá sau 90 ngày); label "Delete orders after:" và 5 radio: Default (2 years), 30, 90, 180, 365 days. Nhãn UI là "Order storage time", còn field và API là `expired_time` / `expired-time-setting`. Không có tooltip và không có nút Save riêng. KB-1630 đến KB-1633.
**Store chưa đặt:** Default (2 years) checked; `GET /api/instances/{instance}/expired-time-setting` trả 200, mảng rỗng (2 mẫu cùng một store, không độc lập). KB-1634 đến KB-1636.
**Chưa rõ:** tác dụng thật (OQ-store-settings-001), Default ứng với dữ liệu lưu nào (002), shape khi đã đặt và response lỗi (003), request lưu, validation, giữ sau reload (004), giá trị theo từng store (005).
**Checklist:** 10 check: 5 `BASELINE`, 5 `NONE`.

## `general-settings-page` — Trang General Settings của store

**Entry points:** sidebar Store Settings > General Settings → `/general-settings`.

**Đã quan sát:** nhóm Store Settings có 7 link (General Settings, Product Page Settings, Product Page Content, Customization Image, Shipping Methods, Inventory Locations, SKU Mapping); header có heading, Save, Reset (enabled khi tải) và dòng "For store"; 10 card: Blacklisted Words, Sync Variant's SKU to platform, hai card Bulk Fulfill, Add Fulfillment ID to Shopify Order's tag, Order storage time, Add order design URL to Shopify Orders, Line Item Properties, Cart items, Assign Shopify product template; mỗi help icon cạnh "Add to:" mở một popover chỉ có ảnh mẫu (Order Notes, Line item property, Both), không có text; không có panel ẩn hay panel token. KB-1637 đến KB-1652, KB-1654, KB-1655.
**API:** khi tải trang chỉ có một request tới API host là `GET .../expired-time-setting`; giá trị các card khác không đến từ request nào trong cửa sổ đó. KB-1653.
**Chưa rõ:** Save/Reset (OQ-store-settings-006), nguồn giá trị các card khác (007), hành vi khi đổi control (008), Switch store và giá trị theo store (009).
**Checklist:** 18 check: 13 `BASELINE`, 5 `NONE`.
