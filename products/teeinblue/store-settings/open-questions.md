# Open Questions — Store Settings

Các mục dưới đây còn mở. Không dùng phần còn mở làm expected result.

## Tóm tắt

| Loại | Số lượng |
|---|---|
| NEEDS_CONFIRMATION | 11 |
| **Tổng** | **11** |

## OQ-store-settings-001 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-store-settings-001", "type": "NEEDS_CONFIRMATION", "feature_id": "expired-time-setting", "summary": "Order storage time (expired_time) thực sự làm gì ngoài help text \"Set how long your orders (including order items, designs and customer info) are stored in the app\": xoá những gì, chạy lúc nào, tính mốc từ ngày nào, có áp lên order đã có khi rút ngắn thời hạn không, có ảnh hưởng storefront, customization, fulfillment không? Run chỉ đọc nên chưa quan sát (KB-1630, KB-1631). Cần PO hoặc Dev xác nhận."}
```

## OQ-store-settings-002 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-store-settings-002", "type": "NEEDS_CONFIRMATION", "feature_id": "expired-time-setting", "summary": "Option \"Default (2 years)\" (value 0) tương ứng với dữ liệu lưu thế nào: không có bản ghi hay bản ghi value 0, và backend có giữ order 2 năm khi ở Default không? Mới thấy một store: UI Default checked trong khi GET trả mảng rỗng (KB-1634, KB-1636). Cần Dev xác nhận."}
```

## OQ-store-settings-003 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-store-settings-003", "type": "NEEDS_CONFIRMATION", "feature_id": "expired-time-setting", "summary": "GET /api/instances/{instance}/expired-time-setting trả shape gì khi store đã đặt giá trị (phần tử, key, kiểu), mảng rỗng có là dạng chung cho store chưa đặt không, và response lỗi (không xác thực, role khác, store khác) là gì? Mới có 2 mẫu 200 mảng rỗng cùng một store (KB-1635). Cần Dev xác nhận. [CBS-163] Dev trả lời một phần (TIB-5689 comment 56448 test case U15, 2026-11-04; KB-1656): response index/update có expired_time, không instance_id, trả [] khi chưa có giá trị. Còn mở: shape đầy đủ khi đã đặt và response lỗi.", "kb_ids": ["KB-1656"]}
```

## OQ-store-settings-004 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-store-settings-004", "type": "NEEDS_CONFIRMATION", "feature_id": "expired-time-setting", "summary": "Lưu Order storage time đi qua request nào (method, path, body), cần bấm Save ở header hay click radio tự lưu, có validation hay thông báo thành công/lỗi, và giá trị có giữ sau reload không? Bị chặn bởi mutation policy nên chưa quan sát (KB-1631, KB-1633). Cần Dev xác nhận. [CBS-163] Quan sát test case TC-TIB-8599 (staging 2026-11-07, không ghi build; KB-1657, OBSERVED_CURRENT/LOW): lưu rồi reload thì giá trị còn giữ. Còn cần Dev xác nhận việc giữ giá trị là expected, và request/validation/thông báo khi lưu.", "kb_ids": ["KB-1657"]}
```

## OQ-store-settings-005 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-store-settings-005", "type": "NEEDS_CONFIRMATION", "feature_id": "expired-time-setting", "summary": "Giá trị Order storage time có riêng cho từng store (instance) của cùng account không? Endpoint có {instance} và trang ghi \"For store\", nhưng chưa bấm Switch store, mới thấy một store (KB-1654). Cần Dev xác nhận."}
```

## OQ-store-settings-006 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-store-settings-006", "type": "NEEDS_CONFIRMATION", "feature_id": "general-settings-page", "summary": "Save ở header lưu những card nào (mọi card một lần hay chỉ card đã đổi), có bị disabled cho tới khi có thay đổi không, và Reset làm gì (về giá trị đã lưu hay về mặc định)? Cả hai nút enabled khi tải và chưa được bấm (KB-1638, KB-1655). Cần Dev hoặc PO xác nhận."}
```

## OQ-store-settings-007 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-store-settings-007", "type": "NEEDS_CONFIRMATION", "feature_id": "general-settings-page", "summary": "Giá trị của các card ngoài Order storage time (Blacklisted Words, SKU prefix, các toggle, Add to) được nạp từ đâu? Không có request nào tới API host mang chúng trong cửa sổ tải trang (KB-1653). Cần Dev xác nhận."}
```

## OQ-store-settings-008 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-store-settings-008", "type": "NEEDS_CONFIRMATION", "feature_id": "general-settings-page", "summary": "Khi gõ, bật/tắt hoặc đổi control (thêm từ vào Blacklisted Words, SKU prefix, các toggle Bulk Fulfill, Fulfillment ID tag, Line Item Properties, Cart items, Assign Shopify product template, radio Add to) thì UI và hiệu ứng sau lưu là gì, rule Not case-sensitive/Exact match của Blacklisted Words có áp đúng như help text không? Run không tương tác control (KB-1641..KB-1650). Cần Dev hoặc PO xác nhận."}
```

## OQ-store-settings-009 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-store-settings-009", "type": "NEEDS_CONFIRMATION", "feature_id": "general-settings-page", "summary": "Switch store đổi gì trên trang General Settings, và giá trị setting có độc lập giữa các store (instance) của cùng account không? Chưa bấm Switch store, mới thấy một store (KB-1639, KB-1654). Cần Dev xác nhận."}
```

## OQ-store-settings-010 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-store-settings-010", "type": "NEEDS_CONFIRMATION", "feature_id": "expired-time-setting", "summary": "Hành vi baseline của card Order storage time (heading, help text, 5 radio, Default checked khi chưa đặt, GET trả mảng rỗng khi tải, tên field expired_time) mới quan sát một lần trên staging; đây có phải hành vi đúng không? Cần PO hoặc Dev xác nhận trước khi dùng làm expected."}
```

## OQ-store-settings-011 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-store-settings-011", "type": "NEEDS_CONFIRMATION", "feature_id": "general-settings-page", "summary": "Hành vi baseline của trang General Settings (vị trí trong nhóm Store Settings, header Save/Reset và dòng For store, 10 card với control và trạng thái khi tải, popover ảnh của help icon ở \"Add to:\", chỉ một GET tới API host khi tải) mới quan sát một lần trên staging; đây có phải hành vi đúng không? Cần PO hoặc Dev xác nhận trước khi dùng làm expected."}
```
