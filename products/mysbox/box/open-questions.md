# Open Questions — box

Tổng: 130 mục (CONFLICT 9 · OPEN_ISSUE 61 · NEEDS_CONFIRMATION 60). Version 1 sinh từ bootstrap DOC_BOOTSTRAP (bộ Product KB v1 do dev viết từ source code, 2026-10-16); version 2 thêm mục từ REFRESH trên staging 2026-10-16 (quan sát OBSERVED_CURRENT); REFRESH trên staging 2026-10-17 thêm mục mới, ghi `staging_observation` (OBSERVED_CURRENT, không resolve NEEDS_CONFIRMATION/CONFLICT) và gỡ OPEN_ISSUE đã được quan sát trả lời (xem CHANGELOG). Mỗi mục là một khối json; `kb_ids` dạng `<feature_key>#KB-xxx` (hoặc `_object-level.<object>#KB-xxx` cho tầng object), `check_ids` dạng `<feature_key>:CHK-xxx`.

## OQ-box-001 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-001",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": null,
  "summary": "Bộ tài liệu nguồn không chỉ định role mặc định cho object này (bootstrap-request để role null): các KB item mang scope.role theo vai trò tài liệu nêu cho từng hành vi, hoặc \"unspecified\" khi tài liệu không nêu. Cần PO/Dev xác nhận ma trận role → quyền thực tế trên production (merchant owner/staff, khách, admin Mysbox theo từng role) trước khi dùng các check PERMISSION làm oracle."
}
```

## OQ-box-002 — CONFLICT

```json
{
  "oq_id": "OQ-box-002",
  "type": "CONFLICT",
  "feature_id": "box-versioning",
  "summary": "Box version được tạo ở mọi lần lưu box, hay chỉ khi lưu mà có ít nhất một thay đổi cấu hình (variant link, loại box, category, item, cài đặt, cờ tracked)? Hai tài liệu phát biểu khác nhau; một mục khác chỉ nói \"có thể\" tạo version. Cần xác nhận hành vi khi lưu box mà không đổi gì.",
  "side_a": "Tài liệu \"Overview\" (§Key vocabulary) và \"Domain entities\" (§Các đối tượng): một box version được tạo mỗi lần lưu box.",
  "side_b": "Tài liệu \"Box version — bản chụp cấu hình\" (§Bước 2 — Thay đổi nào tạo version mới): version mới sinh ra khi lưu và ít nhất một trong danh sách thuộc tính cấu hình thay đổi.",
  "conflict_group": "CONF-box-01",
  "kb_ids": [
    "box-versioning#KB-001",
    "box-versioning#KB-002",
    "box-versioning#KB-003"
  ],
  "check_ids": [
    "box-versioning:CHK-006"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-002 / CONF-box-01: Đổi animation và đổi quantity đều tạo version mới (khớp cả KB-001 và KB-002). Save bị disabled khi form không đổi nên không có mẫu 'lưu không thay đổi' để phân biệt hai phía. Không phía nào được xác nhận riêng.",
  "staging_observation_kb_ids": [
    "box-versioning#KB-045",
    "box-versioning#KB-001",
    "box-versioning#KB-002"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve."
}
```

## OQ-box-003 — CONFLICT

```json
{
  "oq_id": "OQ-box-003",
  "type": "CONFLICT",
  "feature_id": "box-versioning",
  "summary": "Đơn hàng được gắn với box version tại thời điểm mua (thanh toán) hay tại thời điểm bốc thăm? Nếu bốc thăm có thể bị trễ/xếp hàng so với lúc thanh toán thì hai mốc cho ra version khác nhau khi merchant sửa box ở giữa; tài liệu cũng nêu một khoảng hẹp với đơn thanh toán ngay trước lúc pause sales.",
  "side_a": "Tài liệu \"Overview\" (§Key vocabulary), \"Domain entities\" (§Các đối tượng) và \"Trang Box (Publish, Versions, Inventory, Recent pulls)\" (§3. Hệ quả cần nhớ): đơn nhớ box version tại thời điểm mua.",
  "side_b": "Tài liệu \"Box version — bản chụp cấu hình\" (§phần mở đầu, §Bước 3 — Ai dùng version nào) và \"Nhóm 02 — Boxes (hộp bí ẩn)\" (§Từ vựng nhóm): đơn nhớ version lúc được bốc thăm, gắn với version đang hiệu lực đúng lúc server bốc thăm.",
  "conflict_group": "CONF-box-02",
  "kb_ids": [
    "box-versioning#KB-004",
    "box-versioning#KB-005",
    "box-versioning#KB-034"
  ],
  "check_ids": [
    "box-versioning:CHK-012"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-003 / CONF-box-02: Đơn #1007/#1008 gắn box_version_id = version hiện hành cả lúc mua lẫn lúc bốc (box không bị sửa giữa paid và bốc) — không phân biệt được KB-004 (lúc mua) và KB-005 (lúc bốc).",
  "staging_observation_kb_ids": [
    "box-versioning#KB-047",
    "box-versioning#KB-004",
    "box-versioning#KB-005"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; conflict vẫn mở, chưa resolve."
}
```

## OQ-box-008 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-008",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Hạn chế đã biết: lỗi tạm thời của Shopify khi lưu box có thể hiện thành thông báo \"thiếu tài nguyên ở Shopify\" dù tài nguyên không thiếu (tài liệu diễn đạt là \"có thể\"). Cần xác nhận hành vi đúng và cách merchant/support phân biệt.",
  "kb_ids": [
    "box-create-and-publish#KB-044"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-024"
  ]
}
```

## OQ-box-009 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-009",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Hạn chế đã biết: khi merchant nhập thêm hàng hoặc sửa product/collection ở Shopify, bản sao dữ liệu trong Mysbox không tự cập nhật cho tới khi deactivate, lưu lại (hoặc Sync data với box Group) và activate. Cần xác nhận đây là hành vi chủ ý hay lỗi cần theo dõi.",
  "kb_ids": [
    "box-create-and-publish#KB-054",
    "box-create-and-publish#KB-055"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-025"
  ]
}
```

## OQ-box-010 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-010",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Khi Save box Group gặp \"Sync failed. Please contact support for assistance.\" thì box ở trạng thái nào và có retry được không? — Quyết định expected result của luồng lưu box Group khi sync lỗi.",
  "kb_ids": [
    "box-create-and-publish#KB-045",
    "box-create-and-publish#KB-048"
  ]
}
```

## OQ-box-011 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-011",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Metafield nào (namespace/key) được ghi lên variant khi publish, và deactivate/unpublish có xoá metafield không hay chỉ xoá khi delete? — Kiểm side effect trên Shopify và hành vi widget khi box về Draft.",
  "kb_ids": [
    "box-create-and-publish#KB-009",
    "box-create-and-publish#KB-052",
    "box-create-and-publish#KB-061"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-011: 2026-10-17: Khi box Active, variant có metafield \"mysbox.box\" (unstructured) và trang product nhúng bản sao trong window.mysboxStore; ~1 phút sau Deactivate metafield vẫn còn với published_at cũ (API trả null). Widget sau Deactivate chưa xem.",
  "staging_observation_kb_ids": [
    "box-create-and-publish#KB-104",
    "box-create-and-publish#KB-105"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-box-013 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-013",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "\"Duplicate box\" dùng được với mọi loại box và box Active không; box duplicate có giữ liên kết variant (vốn chỉ thuộc một box) không? — Luật một variant thuộc một box có thể làm box duplicate lỗi khi Save.",
  "kb_ids": [
    "box-create-and-publish#KB-016",
    "box-create-and-publish#KB-021",
    "box-create-and-publish#KB-036"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-013: 2026-10-17: Pass 1 không thấy control Duplicate; pass 2 thấy nút \"Duplicate box\" ở header form box (Active và Draft) — hai ghi nhận trái nhau. Không bấm nên chưa biết trường nào được copy.",
  "staging_observation_kb_ids": [
    "box-create-and-publish#KB-099",
    "box-create-and-publish#KB-100"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-box-014 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-014",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Đơn test tạo từ \"Preview\" có bốc thăm thật và có tính vào quota/usage không? — Ảnh hưởng đếm capacity và dữ liệu thử nghiệm.",
  "kb_ids": [
    "box-create-and-publish#KB-024"
  ]
}
```

## OQ-box-015 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-015",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "\"Pause sales\", \"deactivate\" và \"unpublish\" có phải cùng một thao tác/nút UI đưa box về Draft không? — Precondition sửa box được nêu bằng nhiều thuật ngữ khác nhau; cần đúng nút UI để viết bước test.",
  "kb_ids": [
    "box-create-and-publish#KB-058",
    "box-create-and-publish#KB-060",
    "box-create-and-publish#KB-067",
    "box-create-and-publish#KB-068"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-015: 2026-10-17: Nút \"Deactivate box\" trên banner gọi POST /api/boxes/{id}/unpublish (body rỗng, 200), không hỏi xác nhận; danh sách có tooltip \"Deactivate\" và combobox \"Status\" bật khi Active. Endpoint của combobox Status và Actions ở danh sách chưa bấm.",
  "staging_observation_kb_ids": [
    "box-create-and-publish#KB-097",
    "box-create-and-publish#KB-098"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-box-016 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-016",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Có điều kiện nào (ngoài trạng thái Draft) chặn xoá box khi box đã có đơn không? — Tài liệu tự khai chưa xác nhận; không viết được expected result cho xoá box có đơn.",
  "kb_ids": [
    "box-create-and-publish#KB-059",
    "box-create-and-publish#KB-066"
  ]
}
```

## OQ-box-017 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-017",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Khi Shopify lỗi và publish bị huỷ, người dùng thấy thông báo gì và sync status có đổi không? — Nhánh lỗi metafield không có thông điệp cụ thể.",
  "kb_ids": [
    "box-create-and-publish#KB-064",
    "box-create-and-publish#KB-072"
  ]
}
```

## OQ-box-018 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-018",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Route sửa box đã publish là route nào, và 'not found' là HTTP 404 hay thông báo UI? — Cần cho check API; tài liệu không nêu route.",
  "kb_ids": [
    "box-create-and-publish#KB-080"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-018: 2026-10-17: Mở form box Active chỉ gọi document 200 + GET /api/boxes/{id} 200, hiện banner \"The box is on sale and cannot be edited. Pause sales to make changes.\"; không có request 4xx/\"not found\" nào.",
  "staging_observation_kb_ids": [
    "box-create-and-publish#KB-101"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-box-019 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-019",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "'bundles' của box (điều kiện để widget hiện) cụ thể là gì? — Không kiểm được điều kiện hiển thị widget nếu không biết đối tượng.",
  "kb_ids": [
    "box-create-and-publish#KB-076"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-019: 2026-10-17: GET /api/boxes/{id} trả bundles[]{source_type, resources, items[]{linked_id, quantity, rate, position, settings{chance, chance_color, title, image, price}}, position, settings{title \"Prize #n\"}} (Single 1 set, Bundle 3 set); box-versions không có quantity/linked_id; bản nhúng storefront cùng shape với /api/boxes và widget hiện một nhóm cho mỗi bundle.",
  "staging_observation_kb_ids": [
    "_object-level.box#KB-022",
    "box-versioning#KB-054"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-box-020 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-020",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Hai thông báo \"Box sync is not complete.\" và \"Box must finish syncing before it can be published.\" (và \"Cannot publish: inventory pools are exhausted.\") hiện ở portal hay admin panel, và trong tình huống nào mỗi cái? — Hai text khác nhau cho cùng điều kiện sync chưa xong; check cần biết surface và text mong đợi.",
  "kb_ids": [
    "box-create-and-publish#KB-062",
    "box-create-and-publish#KB-063",
    "box-create-and-publish#KB-078"
  ]
}
```

## OQ-box-021 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-021",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Hệ thống tự unpublish box trong điều kiện nào? — KB chỉ nêu hệ quả (ngày publish trống), không nêu trigger; cần để test vòng đời và widget.",
  "kb_ids": [
    "box-create-and-publish#KB-073"
  ]
}
```

## OQ-box-022 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-022",
  "type": "OPEN_ISSUE",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Đội Mysbox bật tuỳ chọn Group cho shop ở đâu (admin panel, cờ shop) và bởi vai trò nào? — Cần để chuẩn bị dữ liệu test và viết check permission cho trường hợp shop chưa được bật.",
  "kb_ids": [
    "box-type-and-prize-setup#KB-007"
  ]
}
```

## OQ-box-023 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-023",
  "type": "OPEN_ISSUE",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Giới hạn Bundle 2-20 set được chặn ở portal, ở server, hay cả hai? — Quyết định test qua UI hay qua API.",
  "kb_ids": [
    "box-type-and-prize-setup#KB-016"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-023: 2026-10-17: Với 2 set nút xoá set bị disabled (bật khi từ 3 set); bấm \"Add prize set\" tới 21 set nút vẫn bật, không có thông báo. Không lưu nên phía server không kiểm.",
  "staging_observation_kb_ids": [
    "box-type-and-prize-setup#KB-068",
    "box-type-and-prize-setup#KB-069"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-box-024 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-024",
  "type": "OPEN_ISSUE",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Box Group chế độ pool khi một nhóm hết item thì xảy ra gì? — Tài liệu loại box chỉ chuyển hướng sang phần tồn kho/pool; feature này không có khẳng định.",
  "kb_ids": [
    "box-type-and-prize-setup#KB-021",
    "box-type-and-prize-setup#KB-023"
  ]
}
```

## OQ-box-025 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-025",
  "type": "OPEN_ISSUE",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Đổi qua lại giữa Single và Bundle, hoặc giữa draw và pool, có reset danh sách item không? — Tài liệu chỉ nêu trường hợp đổi single item sang group.",
  "kb_ids": [
    "box-type-and-prize-setup#KB-031"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-025: 2026-10-17: Đổi \"Random by single item(s)\" ↔ \"Random by group(s)\" reset danh sách item cả hai chiều; form không có control đổi Single ↔ Bundle (loại box cố định theo URL). Draw ↔ pool không có trên gói Free.",
  "staging_observation_kb_ids": [
    "box-type-and-prize-setup#KB-065"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-box-027 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-027",
  "type": "OPEN_ISSUE",
  "feature_id": "box-versioning",
  "summary": "Hạn chế đã biết: đơn vừa thanh toán ngay trước lúc merchant pause sales để sửa box rơi vào một khoảng hẹp; tài liệu không nêu đơn đó gắn với version nào và hệ quả (sai item, sai điều khoản buyback hay lỗi). Cần xác nhận mức độ và hướng xử lý.",
  "kb_ids": [
    "box-versioning#KB-034"
  ],
  "check_ids": [
    "box-versioning:CHK-013"
  ]
}
```

## OQ-box-029 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-029",
  "type": "OPEN_ISSUE",
  "feature_id": "box-versioning",
  "summary": "Khi collection trên Shopify đổi variant sau khi version đã bung, version mới chỉ đổi cài đặt có cập nhật danh sách variant không? — Version mới dùng lại danh sách đã bung và không hỏi lại Shopify; có thể lệch với collection hiện tại.",
  "kb_ids": [
    "box-versioning#KB-022",
    "box-versioning#KB-030",
    "box-versioning#KB-031"
  ]
}
```

## OQ-box-030 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-030",
  "type": "OPEN_ISSUE",
  "feature_id": "box-versioning",
  "summary": "'Trạng thái đồng bộ' (thay đổi không tạo version) cụ thể là trạng thái gì? — Cần biết thao tác nào thuộc nhóm không tạo version để test.",
  "kb_ids": [
    "box-versioning#KB-029"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-030: 2026-10-17: sync_status là \"completed\" ở mọi response box (POST, publish, GET, unpublish) của box single/bundle/sealed; current_version_id không đổi qua các bước. Box group (\"Syncing inventory...\") không lưu.",
  "staging_observation_kb_ids": [
    "box-versioning#KB-052"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-box-031 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-031",
  "type": "OPEN_ISSUE",
  "feature_id": "box-versioning",
  "summary": "Việc dựng lại tồn kho khi tạo version ảnh hưởng thế nào tới pool/tồn kho đã trừ của đơn đang mở dở? — Side effect trên inventory khi sửa box còn đơn chưa mở; KB không có item nào trả lời."
}
```

## OQ-box-032 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-032",
  "type": "OPEN_ISSUE",
  "feature_id": "box-versioning",
  "summary": "Edit (sửa JSON settings/bundles) ở admin panel có tạo box version mới không, và JSON không hợp lệ bị chặn thế nào? — Configure Tier Settings được nêu rõ là tạo version, còn Edit chỉ nói ảnh hưởng đơn mua sau.",
  "kb_ids": [
    "box-versioning#KB-041",
    "box-versioning#KB-042"
  ]
}
```

## OQ-box-058 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-058",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Thời gian chờ tối đa của màn hình \"Syncing inventory...\" khi lưu box Group được tài liệu nêu xấp xỉ (\"khoảng 60 giây\"); cần xác nhận giá trị chính xác và hành vi khi quá thời gian.",
  "kb_ids": [
    "box-create-and-publish#KB-049"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-039"
  ]
}
```

## OQ-box-059 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-059",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Bộ tài liệu không nêu role nào (chủ shop hay nhân viên shop) được tạo, publish, unpublish và xoá box; các item liên quan chỉ ghi role merchant chung. Cần xác nhận ma trận quyền.",
  "kb_ids": [
    "box-create-and-publish#KB-001",
    "box-create-and-publish#KB-003",
    "box-create-and-publish#KB-006",
    "box-create-and-publish#KB-057"
  ]
}
```

## OQ-box-060 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-060",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.",
  "check_ids": [
    "box-create-and-publish:CHK-030",
    "box-create-and-publish:CHK-031",
    "box-create-and-publish:CHK-037"
  ]
}
```

## OQ-box-061 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-061",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Vai trò nào trong shop (chủ shop hay nhân viên shop) được tạo, publish, unpublish và xoá box trong app merchant?",
  "check_ids": [
    "box-create-and-publish:CHK-040"
  ]
}
```

## OQ-box-062 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-062",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Box ở trạng thái Draft có đúng là khi ngày publish (published_at) để trống không, và deactivate box có xoá ngày publish không?",
  "kb_ids": [
    "box-create-and-publish#KB-056"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-041"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-062: 2026-10-17: POST /api/boxes trả published_at null, /publish gán published_at (Active), /unpublish trả published_at null (Draft) — 3/3 gồm Bundle và Single physical. Activate lại sau Deactivate không làm.",
  "staging_observation_kb_ids": [
    "box-create-and-publish#KB-096",
    "box-create-and-publish#KB-097"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-box-063 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-063",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Với box Group chế độ pool, tài liệu chỉ khuyến nghị bật \"Track quantity\" ở Shopify; cần xác nhận đây có phải điều kiện bắt buộc (portal chặn) hay chỉ khuyến nghị, và hành vi khi tắt.",
  "kb_ids": [
    "box-type-and-prize-setup#KB-022"
  ],
  "check_ids": [
    "box-type-and-prize-setup:CHK-016"
  ]
}
```

## OQ-box-064 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-064",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Tài liệu tự ghi chú chưa xác nhận rằng server không đặt trần cho số item mỗi set và số nhóm của box Group; cần xác nhận giới hạn thật (portal và server).",
  "kb_ids": [
    "box-type-and-prize-setup#KB-032",
    "box-type-and-prize-setup#KB-033"
  ],
  "check_ids": [
    "box-type-and-prize-setup:CHK-022"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-064: 2026-10-17: Group mode thêm tới 10 nhóm, \"Add tier\" vẫn bật, không có thông báo; số item mỗi set chưa thử tới trần.",
  "staging_observation_kb_ids": [
    "box-type-and-prize-setup#KB-066"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-box-065 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-065",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.",
  "check_ids": [
    "box-type-and-prize-setup:CHK-003",
    "box-type-and-prize-setup:CHK-010",
    "box-type-and-prize-setup:CHK-013",
    "box-type-and-prize-setup:CHK-014",
    "box-type-and-prize-setup:CHK-015",
    "box-type-and-prize-setup:CHK-018",
    "box-type-and-prize-setup:CHK-021"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-065: 2026-10-17: CHK-018: đổi single item → group reset item. CHK-010: Bundle 3 set, mỗi hộp 1 item/set. CHK-021: tiền trả = giá variant × số lượng. Group draw (CHK-014) không lưu.",
  "staging_observation_kb_ids": [
    "box-type-and-prize-setup#KB-065",
    "box-type-and-prize-setup#KB-072",
    "picking-modes#KB-055"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-box-066 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-066",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Các nhóm mặc định của box Group có tên và chance được điền sẵn không (bộ Common 50% / Rare 30% / Epic 15% / Legendary 5% là preset thật hay chỉ là số minh hoạ), tên nhóm cố định hay merchant tự đặt, và merchant sửa/xoá được không?",
  "kb_ids": [
    "box-type-and-prize-setup#KB-029"
  ],
  "check_ids": [
    "box-type-and-prize-setup:CHK-023"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-066: 2026-10-17: Nhóm mặc định \"Common\" 50, \"Rare\" 30, \"Epic\" 15, \"Legendary\" 5; \"Group name\" và \"Chance %\" sửa được; xoá nhóm ngay không hỏi; \"Add tier\" thêm \"Group #n\" chance 0.",
  "staging_observation_kb_ids": [
    "box-type-and-prize-setup#KB-066"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-box-067 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-067",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Ở box Single tracked, chance hiển thị của mỗi item có đúng bằng số lượng item chia tổng số lượng không, và được làm tròn theo quy tắc nào (vd 5/9)?",
  "kb_ids": [
    "box-type-and-prize-setup#KB-026"
  ],
  "check_ids": [
    "box-type-and-prize-setup:CHK-024"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-067: 2026-10-17: Quantity 5 và 4 hiện Chance \"55.56%\" / \"44.44%\" (bộ đếm \"9/5\"); 2/2/1 → 40.00/40.00/20.00; 2/1 → 66.67/33.33; 1 item → 100.00%.",
  "staging_observation_kb_ids": [
    "box-type-and-prize-setup#KB-064"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-box-068 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-068",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-versioning",
  "summary": "Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.",
  "check_ids": [
    "box-versioning:CHK-007",
    "box-versioning:CHK-008",
    "box-versioning:CHK-010",
    "box-versioning:CHK-011",
    "box-versioning:CHK-015",
    "box-versioning:CHK-017"
  ]
}
```

## OQ-box-091 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-091",
  "type": "OPEN_ISSUE",
  "feature_id": null,
  "summary": "access-control-allow-origin: * trên API merchant (<MYS_API_BASE>/api/*, kèm Allow-Header Authorization), app proxy /apps/mysbox/api/* và staging-api. Cần xác nhận cấu hình CORS này là chủ ý.",
  "kb_ids": [
    "_object-level.box#KB-021"
  ],
  "tags": [
    "security-observation"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-047"
  ]
}
```

## OQ-box-092 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-092",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Form box chế độ group (shop gói Free, chưa lưu) không hiện lựa chọn draw/pool, 'When one of groups has been all revealed' hay refill. Các mục này chỉ hiện ở điều kiện nào (gói trả phí, shop được bật Group, sau khi lưu, hay qua Configure Tier Settings của admin)?",
  "kb_ids": [
    "box-type-and-prize-setup#KB-057",
    "box-type-and-prize-setup#KB-038",
    "box-type-and-prize-setup#KB-039",
    "box-type-and-prize-setup#KB-018",
    "box-type-and-prize-setup#KB-021",
    "inventory-and-sold-out#KB-013",
    "inventory-and-sold-out#KB-014",
    "picking-modes#KB-037"
  ],
  "check_ids": [
    "box-type-and-prize-setup:CHK-025"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-092: 2026-10-17: Không lưu box group; trên form group chưa lưu ở gói Free không có lựa chọn draw/pool, \"When one of groups has been all revealed\" hay refill.",
  "staging_observation_kb_ids": [
    "box-type-and-prize-setup#KB-067"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-box-094 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-094",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": null,
  "summary": "Item mới quan sát trên staging (OBSERVED_CURRENT) chạm tiền/permission/token, được gắn cờ rủi ro khi diff: cần owner (PO) xác nhận hành vi quan sát là ý định sản phẩm trước khi dùng làm kỳ vọng. Item vẫn publish dạng OBSERVED_CURRENT; không phải xác nhận hành vi production.",
  "owner_role": "PO",
  "kb_ids": [
    "_object-level.box#KB-021",
    "box-type-and-prize-setup#KB-063"
  ]
}
```

## OQ-box-095 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-095",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "\"Bấm nút Activate\" (KB-057) là combobox Status trên sidebar hay một nút khác? Staging chỉ thấy combobox Status gọi /publish. — Bước test publish box Draft cần đúng control UI; quan sát mới 1 mẫu.",
  "kb_ids": [
    "box-create-and-publish#KB-083",
    "box-create-and-publish#KB-057"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-095: 2026-10-17: Control kích hoạt thấy được: tooltip \"Activate\" ở hàng Draft của danh sách và combobox \"Status\"; form Draft không có nút \"Activate\" riêng. Endpoint chỉ thấy /publish tự động sau Save lần đầu; không kích hoạt thủ công.",
  "staging_observation_kb_ids": [
    "box-create-and-publish#KB-097",
    "box-create-and-publish#KB-098"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-box-096 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-096",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Request body của POST /api/boxes, PUT /api/boxes/{id}, POST /publish, /unpublish gồm field nào, field nào bắt buộc, và lỗi 4xx/422 trả gì? — Body không capture được; không viết được check API contract/validation phía server.",
  "kb_ids": [
    "box-create-and-publish#KB-092",
    "box-create-and-publish#KB-093",
    "box-create-and-publish#KB-094",
    "box-create-and-publish#KB-082"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-096: 2026-10-17: Chuỗi endpoint: POST /api/boxes (201) → POST /publish (200) → GET; /unpublish body rỗng. Body của POST /api/boxes và /publish không lấy được (giới hạn công cụ capture); không có PUT.",
  "staging_observation_kb_ids": [
    "box-create-and-publish#KB-096",
    "box-create-and-publish#KB-097"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-box-097 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-097",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Vì sao Storefront getProducts trả metafield(namespace mysbox, key box) = null ở mọi variant node trong khi widget đọc dữ liệu từ window.mysboxStore? — Quyết định nguồn dữ liệu widget và oracle cho check 'publish ghi metafield' (KB-009).",
  "kb_ids": [
    "box-create-and-publish#KB-091",
    "box-create-and-publish#KB-009"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-097: 2026-10-17: Metafield \"mysbox.box\" của variant box có giá trị (unstructured, không definition), nhưng Storefront getProducts trả null 3/3; quyền Storefront access không hiện. Lý do gốc vẫn cần Dev.",
  "staging_observation_kb_ids": [
    "box-create-and-publish#KB-104",
    "box-create-and-publish#KB-105"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-box-098 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-098",
  "type": "OPEN_ISSUE",
  "feature_id": "box-versioning",
  "summary": "Server có kiểm box_version_id trong URL/query lệnh mở khớp với version gắn với đơn không, hay dùng giá trị client gửi? — box_version_id do trang khách gửi (KB-047); nếu server tin client, khách có thể mở theo version khác — cần cho check toàn vẹn kết quả.",
  "kb_ids": [
    "box-versioning#KB-047"
  ]
}
```

## OQ-box-103 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-103",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Check box-create-and-publish:CHK-042 \"Save lần đầu box Single/Bundle mới gọi POST /api/boxes rồi POST /api/boxes/{id}/publish\" có oracle BASELINE (chỉ dựa trên quan sát staging OBSERVED_CURRENT — lệch là cần điều tra, chưa phải bug). Cần PO/Dev xác nhận hành vi mong đợi.",
  "kb_ids": [
    "box-create-and-publish#KB-081",
    "box-create-and-publish#KB-093"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-042"
  ]
}
```

## OQ-box-104 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-104",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Check box-create-and-publish:CHK-043 \"Deactivate box gọi POST /api/boxes/{id}/unpublish, không hỏi xác nhận, box về Draft giữ nguyên version và inventory\" có oracle BASELINE (chỉ dựa trên quan sát staging OBSERVED_CURRENT — lệch là cần điều tra, chưa phải bug). Cần PO/Dev xác nhận hành vi mong đợi.",
  "kb_ids": [
    "box-create-and-publish#KB-084",
    "box-create-and-publish#KB-094"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-043"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-104: 2026-10-17: Deactivate trên Single digital/Bundle/Single physical: không có hộp xác nhận, /unpublish 200, version và inventory.bundles giữ nguyên. Box group không có.",
  "staging_observation_kb_ids": [
    "box-create-and-publish#KB-097"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-box-105 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-105",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Check box-create-and-publish:CHK-044 \"Save box Draft đã tồn tại chỉ gọi PUT /api/boxes/{id}, không gọi /publish\" có oracle BASELINE (chỉ dựa trên quan sát staging OBSERVED_CURRENT — lệch là cần điều tra, chưa phải bug). Cần PO/Dev xác nhận hành vi mong đợi.",
  "kb_ids": [
    "box-create-and-publish#KB-082"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-044"
  ]
}
```

## OQ-box-106 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-106",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Check box-create-and-publish:CHK-045 \"Tạo product mystery mới từ form box qua modal Add product của Shopify\" có oracle BASELINE (chỉ dựa trên quan sát staging OBSERVED_CURRENT — lệch là cần điều tra, chưa phải bug). Cần PO/Dev xác nhận hành vi mong đợi.",
  "kb_ids": [
    "box-create-and-publish#KB-088"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-045"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-106: 2026-10-17: \"create a new product\" mở modal Shopify \"Add product\" ngoài iframe; Save gọi ProductCreateSet + ProductCreatePublish và form gắn product, hiện \"<n> boxes in stock\" (3/3 gồm form Bundle).",
  "staging_observation_kb_ids": [
    "box-create-and-publish#KB-106"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-box-107 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-107",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Check box-create-and-publish:CHK-046 \"Danh sách box: GET /api/boxes lọc theo loại thẻ, có phân trang và meta.total\" có oracle BASELINE (chỉ dựa trên quan sát staging OBSERVED_CURRENT — lệch là cần điều tra, chưa phải bug). Cần PO/Dev xác nhận hành vi mong đợi.",
  "kb_ids": [
    "box-create-and-publish#KB-095",
    "box-create-and-publish#KB-090"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-046"
  ]
}
```

## OQ-box-108 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-108",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Check box-type-and-prize-setup:CHK-026 \"Prize picker: Browse mở dialog chọn sản phẩm trong app, Close không đổi form\" có oracle BASELINE (chỉ dựa trên quan sát staging OBSERVED_CURRENT — lệch là cần điều tra, chưa phải bug). Cần PO/Dev xác nhận hành vi mong đợi.",
  "kb_ids": [
    "box-type-and-prize-setup#KB-058"
  ],
  "check_ids": [
    "box-type-and-prize-setup:CHK-026"
  ]
}
```

## OQ-box-109 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-109",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Check box-type-and-prize-setup:CHK-027 \"Widget trang product hiện item và chance của box Single / Bundle khớp form portal\" có oracle BASELINE (chỉ dựa trên quan sát staging OBSERVED_CURRENT — lệch là cần điều tra, chưa phải bug). Cần PO/Dev xác nhận hành vi mong đợi.",
  "kb_ids": [
    "box-type-and-prize-setup#KB-062"
  ],
  "check_ids": [
    "box-type-and-prize-setup:CHK-027"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-109: 2026-10-17: Widget khớp form portal: B1 40.00/40.00/20.00, B2 66.67/33.33 theo set, B3 100.00; Bundle thêm \"You will receive a box of 3 premium products\", \"Get 1 out of 2 items\".",
  "staging_observation_kb_ids": [
    "box-type-and-prize-setup#KB-071"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-box-110 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-110",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-versioning",
  "summary": "Staging thấy mỗi lần Save có thay đổi (animation, quantity) đều sinh current_version_id mới qua PUT /api/boxes/{id} (mỗi loại 1 mẫu). Đây có phải hành vi mong đợi cho mọi loại thay đổi không, và có cách nào lưu box mà không có thay đổi (API trực tiếp) để phân xử CONF-box-01?",
  "kb_ids": [
    "box-versioning#KB-051",
    "box-versioning#KB-045"
  ],
  "check_ids": [
    "box-versioning:CHK-018"
  ]
}
```

## OQ-box-111 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-111",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-versioning",
  "summary": "Check box-versioning:CHK-019 \"Đơn có box mang box_version_id ở API merchant, trang khách và link Unbox\" có oracle BASELINE (chỉ dựa trên quan sát staging OBSERVED_CURRENT — lệch là cần điều tra, chưa phải bug). Cần PO/Dev xác nhận hành vi mong đợi.",
  "kb_ids": [
    "box-versioning#KB-047"
  ],
  "check_ids": [
    "box-versioning:CHK-019"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-111: 2026-10-17: box_version_id nhất quán ở GET /api/orders/{id} của merchant, GET /apps/mysbox/api/orders/{id}, path và ?parameters= của link Unbox, query POST open (3023, 3024, 3025).",
  "staging_observation_kb_ids": [
    "box-versioning#KB-053"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-box-112 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-112",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-versioning",
  "summary": "Check box-versioning:CHK-020 \"GET /api/box-versions/by-ids trả cấu hình bản chụp của version\" có oracle BASELINE (chỉ dựa trên quan sát staging OBSERVED_CURRENT — lệch là cần điều tra, chưa phải bug). Cần PO/Dev xác nhận hành vi mong đợi.",
  "kb_ids": [
    "box-versioning#KB-050"
  ],
  "check_ids": [
    "box-versioning:CHK-020"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-box-112: 2026-10-17: Chi tiết đơn merchant gọi GET /api/box-versions/by-ids?ids=<version của đơn>; settings gồm picking_mode, animation, bundles_animation, show_item_stock, buyback_enabled, randomization_method (vắng ở BUNDLES); trang khách gửi ids rỗng → 422.",
  "staging_observation_kb_ids": [
    "box-versioning#KB-054"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-box-115 — CONFLICT

```json
{
  "oq_id": "OQ-box-115",
  "type": "CONFLICT",
  "feature_id": "box-create-and-publish",
  "summary": "Hai pass portal cùng ngày ghi trái nhau về nút \"Duplicate box\" trên form box (pass 1 không thấy, pass 2 thấy ở header). Cần quan sát lại (và nếu có, bấm thử trên box QA- để biết trường nào được copy, đặc biệt variant link).",
  "side_a": "Quan sát pass 1 KB-100: không có control Duplicate ở danh sách và form box.",
  "side_b": "Quan sát pass 2 KB-099: form box 1025/1026/1027 có nút \"Duplicate box\" ở header.",
  "conflict_group": "CONF-box-12",
  "kb_ids": [
    "box-create-and-publish#KB-099",
    "box-create-and-publish#KB-100",
    "box-create-and-publish#KB-016"
  ],
  "related_oq_ids": [
    "OQ-box-013"
  ],
  "tags": [
    "staging-observed"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-051"
  ]
}
```

## OQ-box-116 — CONFLICT

```json
{
  "oq_id": "OQ-box-116",
  "type": "CONFLICT",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Tài liệu nói portal bắt box Bundle tối đa 20 prize set; trên staging form cho thêm tới 21 set, nút \"Add prize set\" vẫn bật, không có thông báo (chưa thử Save). Giới hạn 20 set được kiểm ở đâu (lúc thêm, lúc lưu, server) và báo gì?",
  "side_a": "Base KB-016 (CE, dev_doc): box Bundle có từ 2 đến 20 prize set (portal bắt ít nhất 2 set, tối đa 20 set).",
  "side_b": "Quan sát staging KB-069: form Bundle mới cho thêm tới 21 set, không chặn, không thông báo; Save không thử.",
  "conflict_group": "CONF-box-10",
  "kb_ids": [
    "box-type-and-prize-setup#KB-016",
    "box-type-and-prize-setup#KB-069"
  ],
  "related_oq_ids": [
    "OQ-box-023"
  ],
  "tags": [
    "staging-observed"
  ],
  "check_ids": [
    "box-type-and-prize-setup:CHK-009"
  ]
}
```

## OQ-box-118 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-118",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Staging (1 mẫu): cột Actions ở danh sách Single box có Deactivate/Edit/Analytics/Delete cho box Active và chỉ Activate/Edit cho box Draft. Đây có phải bộ thao tác đúng theo trạng thái không — đặc biệt box Draft không có \"Delete\" ở danh sách trong khi tài liệu nói chỉ xoá được box Draft (KB-059/KB-065)?",
  "kb_ids": [
    "box-create-and-publish#KB-098"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-048"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-box-119 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-119",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Sau Deactivate, metafield \"mysbox.box\" trên variant vẫn còn và giữ published_at cũ (staging, ~1 phút, 1 box). Metafield có được cập nhật/xoá muộn hơn không, và trong lúc đó widget có còn hiện/bán box đã về Draft không (tài liệu KB-061/KB-075: box Draft ẩn widget, widget chỉ hiện khi có ngày publish)?",
  "kb_ids": [
    "box-create-and-publish#KB-104"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-049"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-box-120 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-120",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-create-and-publish",
  "summary": "Storefront API trả null cho metafield mysbox.box (3/3 box) trong khi widget dùng bản nhúng Liquid window.mysboxStore. Đây có phải thiết kế (metafield không bật Storefront access) không, và có luồng nào của widget phụ thuộc vào metafield qua Storefront API không?",
  "kb_ids": [
    "box-create-and-publish#KB-105"
  ],
  "check_ids": [
    "box-create-and-publish:CHK-050"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-box-121 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-121",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Mức tối thiểu prize set của box Bundle là 2 (portal chặn bằng nút xoá disabled khi còn 2 set, staging) — nguồn tài liệu nêu con số này (KB-016) đang conflict ở phía tối đa 20 set (CONF-box-10). Cần PO/Dev xác nhận lại cả giới hạn tối thiểu và tối đa của prize set.",
  "kb_ids": [
    "box-type-and-prize-setup#KB-043",
    "box-type-and-prize-setup#KB-068"
  ],
  "check_ids": [
    "box-type-and-prize-setup:CHK-008"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-box-122 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-122",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Staging (1 mẫu): form Bundle mới không có \"Randomization method\" (box Bundle không có chế độ group) và Animation chỉ có Drawing / Card flip / None. Đây có phải bộ lựa chọn đúng cho box Bundle không?",
  "kb_ids": [
    "box-type-and-prize-setup#KB-068"
  ],
  "check_ids": [
    "box-type-and-prize-setup:CHK-028"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-box-123 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-123",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-versioning",
  "summary": "Staging (3 box): current_version_id có ngay khi POST /api/boxes và không đổi qua publish/unpublish — khớp tài liệu (KB-023, KB-029). Cần xác nhận thêm với box chế độ group (sync_status đổi) và với Save sửa box (PUT) trong cùng chuỗi.",
  "kb_ids": [
    "box-versioning#KB-052"
  ],
  "check_ids": [
    "box-versioning:CHK-021"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-box-124 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-124",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-versioning",
  "summary": "Trên staging, mở chi tiết đơn chỉ có box Sealed làm frontend gọi box-versions/by-ids với ids rỗng và nhận 422 \"The ids field is required.\". Đây là lỗi (frontend không nên gọi khi không có version digital) hay chủ ý, và trang chi tiết đơn phải hiển thị gì cho đơn chỉ có box Sealed?",
  "kb_ids": [
    "box-versioning#KB-054"
  ],
  "check_ids": [
    "box-versioning:CHK-022"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-box-128 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-128",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Server có kiểm lại \"The random set is empty\" (set rỗng) khi request đi thẳng tới POST /api/boxes không, hay chỉ chặn phía client? — Staging chỉ thấy chặn phía client (0 request); thiếu kiểm phía server là rủi ro dữ liệu box hỏng — cần cho check API validation.",
  "kb_ids": [
    "box-create-and-publish#KB-103",
    "box-create-and-publish#KB-030"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-box-129 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-129",
  "type": "OPEN_ISSUE",
  "feature_id": "box-create-and-publish",
  "summary": "Icon Actions \"Analytics\" ở hàng box Active và các icon \"Deactivate\"/\"Activate\"/\"Delete\" ở danh sách gọi endpoint nào và có hộp xác nhận không? — Danh sách là điểm vào thứ hai để đổi trạng thái/xoá box; chưa bấm nên chưa viết được bước test và expected cho các icon này.",
  "kb_ids": [
    "box-create-and-publish#KB-098"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-box-130 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-130",
  "type": "OPEN_ISSUE",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Save form box khi tổng quantity vượt tồn kho box (vd \"9/5\") — portal/server chặn với thông báo nào? — Form không chặn lúc nhập (KB-064); cần biết chặn ở bước lưu để viết check validation quantity (đối chiếu box-create-and-publish#KB-032).",
  "kb_ids": [
    "box-type-and-prize-setup#KB-064",
    "box-create-and-publish#KB-032"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-box-131 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-131",
  "type": "OPEN_ISSUE",
  "feature_id": "box-versioning",
  "summary": "Trang khách gọi /apps/mysbox/api/box-versions/by-ids với ids rỗng cho đơn chỉ có box sealed và nhận 422 — đây là hành vi chủ ý hay lỗi, và có ảnh hưởng hiển thị trang khách không? — Lỗi 422 ẩn trên trang khách; cần owner xác nhận trước khi viết check (regression watch hay expected).",
  "kb_ids": [
    "box-versioning#KB-054"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-box-134 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-134",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "box-type-and-prize-setup",
  "summary": "Quan sát staging mới chạm vùng rủi ro cao (quyền truy cập / tiền / billing): Tiền khách trả = giá variant mystery × số lượng (+ thuế, ship Free). Item là OBSERVED_CURRENT; cần PO xác nhận đây là hành vi dự kiến trước khi dùng làm expected result.",
  "kb_ids": [
    "box-type-and-prize-setup#KB-072"
  ],
  "tags": [
    "staging-observed",
    "risk-flag"
  ]
}
```

## OQ-box-135 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-135",
  "type": "OPEN_ISSUE",
  "feature_id": "admin-box-management",
  "summary": "Hạn chế đã biết theo tài liệu (theo dõi như regression watch; cần xác nhận trạng thái sửa và mức ảnh hưởng): sau khi xoá dòng ở tab Inventory, box không rút được cho tới khi inventory được dựng lại.",
  "kb_ids": [
    "admin-box-management#KB-054"
  ],
  "check_ids": [
    "admin-box-management:CHK-019"
  ],
  "supersedes": "OQ-admin-panel-009"
}
```

## OQ-box-136 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-136",
  "type": "OPEN_ISSUE",
  "feature_id": "admin-box-management",
  "summary": "Hạn chế đã biết theo tài liệu (theo dõi như regression watch; cần xác nhận trạng thái sửa và mức ảnh hưởng): với shop gói Free đã chạm trần capacity, việc admin publish lại từng box không tự giải quyết được việc tiếp tục bán vượt capacity.",
  "kb_ids": [
    "admin-box-management#KB-056"
  ],
  "check_ids": [
    "admin-box-management:CHK-020"
  ],
  "supersedes": "OQ-admin-panel-010"
}
```

## OQ-box-137 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-137",
  "type": "OPEN_ISSUE",
  "feature_id": "admin-box-management",
  "summary": "\"Draft on empty\" và \"Deactivate on empty\" chỉ áp dụng cho picking mode BasePool hay cả Draw? — Phạm vi không rõ, ảnh hưởng ma trận test Configure Tier Settings.",
  "kb_ids": [
    "admin-box-management#KB-010"
  ],
  "supersedes": "OQ-admin-panel-011"
}
```

## OQ-box-138 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-138",
  "type": "OPEN_ISSUE",
  "feature_id": "admin-box-management",
  "summary": "Unpublish và Delete có hộp xác nhận không? — Chỉ Publish và Hide from recent pulls được nêu có hộp xác nhận.",
  "kb_ids": [
    "admin-box-management#KB-030",
    "admin-box-management#KB-048"
  ],
  "supersedes": "OQ-admin-panel-012"
}
```

## OQ-box-139 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-139",
  "type": "OPEN_ISSUE",
  "feature_id": "admin-box-management",
  "summary": "Khi Shopify lỗi và publish bị huỷ, admin thấy thông báo gì; sync status có đổi không? — Nhánh lỗi Shopify không có thông điệp cụ thể.",
  "kb_ids": [
    "admin-box-management#KB-029"
  ],
  "supersedes": "OQ-admin-panel-013"
}
```

## OQ-box-140 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-140",
  "type": "OPEN_ISSUE",
  "feature_id": "admin-box-management",
  "summary": "Edit (sửa JSON settings/bundles) có tạo box version mới không, và JSON không hợp lệ bị chặn thế nào? — Không có expected result cho version và validation của Edit.",
  "kb_ids": [
    "admin-box-management#KB-043"
  ],
  "supersedes": "OQ-admin-panel-014"
}
```

## OQ-box-141 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-141",
  "type": "OPEN_ISSUE",
  "feature_id": "admin-box-management",
  "summary": "Resync recent pulls và Hide from recent pulls báo hoàn tất/thất bại cho admin thế nào (ngoài nhãn Retry hiding)? — Cả hai chạy qua job; không có tín hiệu hoàn tất được mô tả để kiểm.",
  "kb_ids": [
    "_object-level#KB-014",
    "admin-box-management#KB-036",
    "admin-box-management#KB-040"
  ],
  "supersedes": "OQ-admin-panel-015"
}
```

## OQ-box-142 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-142",
  "type": "OPEN_ISSUE",
  "feature_id": "admin-box-management",
  "summary": "Quyền publish, publish/unpublish, resync, hide recent pull, update, delete được gán cho role admin nào? — Chỉ có tên quyền theo nút; không có mapping role → quyền.",
  "kb_ids": [
    "admin-box-management#KB-018"
  ],
  "supersedes": "OQ-admin-panel-016"
}
```

## OQ-box-143 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-box-143",
  "type": "OPEN_ISSUE",
  "feature_id": "admin-box-management",
  "summary": "'Box Tier hết hàng' được xác định thế nào (mọi pool cạn hay một pool cạn)? — Điều kiện chặn publish 'inventory pools are exhausted' cần định nghĩa biên để dựng data.",
  "kb_ids": [
    "admin-box-management#KB-024"
  ],
  "supersedes": "OQ-admin-panel-017"
}
```

## OQ-box-144 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-144",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "admin-box-management",
  "summary": "Ngoài quyền delete, có điều kiện nào chặn xoá box khi box đã có đơn không? Tài liệu tự khai chưa xác nhận.",
  "kb_ids": [
    "admin-box-management#KB-052"
  ],
  "check_ids": [
    "admin-box-management:CHK-022"
  ],
  "supersedes": "OQ-admin-panel-069"
}
```

## OQ-box-145 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-145",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "admin-box-management",
  "summary": "Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.",
  "check_ids": [
    "admin-box-management:CHK-011",
    "admin-box-management:CHK-018"
  ],
  "supersedes": "OQ-admin-panel-070"
}
```

## OQ-box-146 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-box-146",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "admin-box-management",
  "summary": "Thông báo thành công sau khi Publish box từ admin panel có nội dung chính xác là gì?",
  "kb_ids": [
    "admin-box-management#KB-058"
  ],
  "check_ids": [
    "admin-box-management:CHK-023"
  ],
  "supersedes": "OQ-admin-panel-071"
}
```
