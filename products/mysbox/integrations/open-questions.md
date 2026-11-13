# Open Questions — integrations

Tổng: 34 mục (CONFLICT 1 · OPEN_ISSUE 19 · NEEDS_CONFIRMATION 14). Sinh từ bootstrap DOC_BOOTSTRAP đầu tiên của Mysbox (nguồn: bộ Product KB v1 do dev viết từ source code, 2026-10-16); REFRESH trên staging 2026-10-17 thêm mục mới, ghi `staging_observation` (OBSERVED_CURRENT, không resolve NEEDS_CONFIRMATION/CONFLICT) và gỡ OPEN_ISSUE đã được quan sát trả lời (xem CHANGELOG). Mỗi mục là một khối json; `kb_ids` dạng `<feature_key>#KB-xxx` (hoặc `_object-level#KB-xxx` cho tầng object), `check_ids` dạng `<feature_key>:CHK-xxx`.

## OQ-integrations-001 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-001",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": null,
  "summary": "Bộ tài liệu nguồn không chỉ định role mặc định cho object này (bootstrap-request để role null): các KB item mang scope.role theo vai trò tài liệu nêu cho từng hành vi, hoặc \"unspecified\" khi tài liệu không nêu. Cần PO/Dev xác nhận ma trận role → quyền thực tế trên production (merchant owner/staff, khách, admin Mysbox theo từng role) trước khi dùng các check PERMISSION làm oracle."
}
```

## OQ-integrations-002 — CONFLICT

```json
{
  "oq_id": "OQ-integrations-002",
  "type": "CONFLICT",
  "feature_id": "webhook-ingestion",
  "summary": "Các tài liệu dev Mysbox Product KB v1 liệt kê khác nhau tập topic webhook Shopify mà app nhận: ba sự kiện, bốn webhook, hay bốn topic cộng ba topic compliance. Cần chủ sở hữu xác nhận danh sách topic thực sự đăng ký (đặc biệt bulk_operations/finish và các topic dữ liệu cá nhân).",
  "side_a": "Tài liệu \"Huỷ đơn và refund từ Shopify\" §App lắng nghe gì và \"Chu kỳ billing, job tạo phí và trạng thái Charge\" §Trạng thái Charge: app chỉ nhận ba sự kiện orders/paid, app/uninstalled, shop/update.",
  "side_b": "Tài liệu \"Webhook mà app nhận\" §Topic nào, làm gì và §Câu hỏi thường gặp: cấu hình app đăng ký app/uninstalled, shop/update, orders/paid, bulk_operations/finish cùng ba topic compliance, bulk_operations/finish có trong cấu hình staging và production; tài liệu \"Tạo box và vòng đời Draft / Active\" §Bước 4 — App tạo/đổi gì trong Shopify: chỉ có bốn webhook uninstall, shop update, orders paid, bulk finish (không nêu topic compliance).",
  "conflict_group": "CONF-integrations-01",
  "kb_ids": [
    "webhook-ingestion#KB-002",
    "webhook-ingestion#KB-003",
    "webhook-ingestion#KB-004",
    "webhook-ingestion#KB-005"
  ],
  "check_ids": [
    "webhook-ingestion:CHK-013",
    "webhook-ingestion:CHK-017"
  ]
}
```

## OQ-integrations-003 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-003",
  "type": "OPEN_ISSUE",
  "feature_id": "request-authentication",
  "summary": "Endpoint POST api/shopify-app/review (nhận review App Store từ ngoài) không có xác thực phía trước theo tài liệu dev. Cần xác nhận đây là lỗ hổng đã biết hay thiết kế có chủ đích, và có cơ chế chống lạm dụng nào (giới hạn, kiểm nguồn) không; không dùng làm oracle hành vi đúng.",
  "kb_ids": [
    "request-authentication#KB-015"
  ],
  "check_ids": [
    "request-authentication:CHK-013"
  ]
}
```

## OQ-integrations-004 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-004",
  "type": "OPEN_ISSUE",
  "feature_id": "request-authentication",
  "summary": "Session token của portal nhúng có thời hạn bao lâu, và Mysbox trả mã lỗi / redirect gì khi token sai chữ ký, hết hạn, hoặc shop chưa cài app / không có quyền? — Thiếu oracle cho các case negative của portal nhúng (status code, redirect).",
  "kb_ids": [
    "request-authentication#KB-006",
    "request-authentication#KB-008",
    "request-authentication#KB-009"
  ]
}
```

## OQ-integrations-005 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-005",
  "type": "OPEN_ISSUE",
  "feature_id": "request-authentication",
  "summary": "Request từ extension cho đơn không tồn tại ở Shopify nhận phản hồi gì? — Tài liệu chỉ nói Mysbox xác nhận đơn tồn tại trước khi trả dữ liệu, không nêu phản hồi khi không tồn tại.",
  "kb_ids": [
    "request-authentication#KB-014"
  ]
}
```

## OQ-integrations-006 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-006",
  "type": "OPEN_ISSUE",
  "feature_id": "request-authentication",
  "summary": "Khi Shopify Flow vượt giới hạn tần suất gọi theo shop, Mysbox phản hồi thế nào (status code, xếp hàng hay bỏ)? — Cần oracle cho case rate limit; giới hạn được mô tả ở feature Shopify Flow actions, phản hồi khi vượt chưa được tài liệu nêu.",
  "kb_ids": [
    "request-authentication#KB-010"
  ]
}
```

## OQ-integrations-007 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-007",
  "type": "OPEN_ISSUE",
  "feature_id": "request-authentication",
  "summary": "Lời gọi API từ banner 'Unbox alert' (lấy số box chưa mở) xác thực bằng cơ chế nào? — Tài liệu chỉ nêu xác thực bằng tên shop cho block trang cảm ơn / trạng thái đơn.",
  "kb_ids": [
    "request-authentication#KB-013"
  ]
}
```

## OQ-integrations-008 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-008",
  "type": "OPEN_ISSUE",
  "feature_id": "request-authentication",
  "summary": "HTTP status, field kỹ thuật và cơ chế xác thực của POST api/affiliate/tracking-id và POST api/affiliate/customers là gì? — Không kiểm được contract API và negative auth của hai endpoint này."
}
```

## OQ-integrations-009 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-009",
  "type": "OPEN_ISSUE",
  "feature_id": "request-authentication",
  "summary": "Request từ trang đơn hàng của khách được xác thực bằng cơ chế nào? — Đây là một loại client được liệt kê nhưng shard này không có rule xác thực cho nó; có thể thuộc profile khác — cần xác nhận để không bỏ sót coverage.",
  "kb_ids": [
    "request-authentication#KB-001"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-integrations-009: 2026-10-17: Trang khách gửi header customer-token + customer-id qua app proxy (không JWT; ?parameters= không gửi lại lên API); block trang cảm ơn chỉ gửi query shop. Cách server kiểm và chữ ký app proxy không quan sát được từ trình duyệt.",
  "staging_observation_kb_ids": [
    "request-authentication#KB-017",
    "request-authentication#KB-018"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền)."
}
```

## OQ-integrations-010 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-010",
  "type": "OPEN_ISSUE",
  "feature_id": "webhook-ingestion",
  "summary": "Khi bộ xử lý webhook ném lỗi lúc xếp việc, lỗi bị nuốt và Shopify nhận 204 nên không gửi lại; đơn đã trả có thể không có trong Mysbox. Đây là lỗi đã biết theo tài liệu dev: cần xác nhận có kế hoạch sửa không và hành vi mong đợi (trả mã lỗi để Shopify gửi lại?). Mục này là regression watch, không phải oracle.",
  "kb_ids": [
    "webhook-ingestion#KB-032"
  ],
  "check_ids": [
    "webhook-ingestion:CHK-019"
  ]
}
```

## OQ-integrations-011 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-011",
  "type": "OPEN_ISSUE",
  "feature_id": "webhook-ingestion",
  "summary": "Job webhook đã xếp hàng mà thất bại (vd orders/paid) không tự thử lại và phải chạy lại thủ công. Lỗi đã biết theo tài liệu dev: cần xác nhận có kế hoạch thêm retry tự động không và hành vi mong đợi.",
  "kb_ids": [
    "webhook-ingestion#KB-034"
  ],
  "check_ids": [
    "webhook-ingestion:CHK-020"
  ]
}
```

## OQ-integrations-012 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-012",
  "type": "OPEN_ISSUE",
  "feature_id": "webhook-ingestion",
  "summary": "Đơn từ POS hoặc kênh bán khác không gửi thông báo \"đơn đã trả\" chuẩn nên có thể không có đơn/box trong Mysbox. Cần xác nhận phạm vi kênh bị ảnh hưởng và hành vi mong đợi (vd dùng action Shopify Flow cho kênh bán khác).",
  "kb_ids": [
    "webhook-ingestion#KB-042"
  ],
  "check_ids": [
    "webhook-ingestion:CHK-021"
  ]
}
```

## OQ-integrations-013 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-013",
  "type": "OPEN_ISSUE",
  "feature_id": "webhook-ingestion",
  "summary": "Webhook qua EventBridge có X-Api-Key chưa cấu hình bị từ chối với status code nào? — Tài liệu chỉ nói 'từ chối tất cả', không có mã.",
  "kb_ids": [
    "webhook-ingestion#KB-015"
  ]
}
```

## OQ-integrations-014 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-014",
  "type": "OPEN_ISSUE",
  "feature_id": "webhook-ingestion",
  "summary": "Bước 'kiểm hợp lệ' của bộ nhận chung gồm những gì ngoài HMAC / X-Api-Key? — Phạm vi kiểm tra không rõ, không thiết kế được case biên.",
  "kb_ids": [
    "webhook-ingestion#KB-017"
  ]
}
```

## OQ-integrations-015 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-015",
  "type": "OPEN_ISSUE",
  "feature_id": "webhook-ingestion",
  "summary": "Quy tắc chuẩn hoá tên topic là gì (vd khác biệt tên topic giữa HTTP và EventBridge)? — Không kiểm được topic nào được nhận dạng sau chuẩn hoá.",
  "kb_ids": [
    "webhook-ingestion#KB-018"
  ]
}
```

## OQ-integrations-016 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-016",
  "type": "OPEN_ISSUE",
  "feature_id": "webhook-ingestion",
  "summary": "'Dọn dữ liệu liên quan' khi nhận app/uninstalled gồm dữ liệu nào? — Tài liệu chỉ nói box/đơn được giữ lại; không biết dữ liệu nào bị xoá để kiểm.",
  "kb_ids": [
    "webhook-ingestion#KB-025"
  ]
}
```

## OQ-integrations-017 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-017",
  "type": "OPEN_ISSUE",
  "feature_id": "webhook-ingestion",
  "summary": "'Thử lại tối đa 3 lần' của shop/update nghĩa là gì (job retry hay chống trùng), và shop/update có chống xử lý trùng không? — Giá trị nằm trong cột chống trùng nhưng mô tả retry; không suy được hành vi khi giao trùng.",
  "kb_ids": [
    "webhook-ingestion#KB-026"
  ]
}
```

## OQ-integrations-018 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-018",
  "type": "OPEN_ISSUE",
  "feature_id": "webhook-ingestion",
  "summary": "Khoá chống trùng (đơn + event id) và (mã tác vụ + event id) tồn tại bao lâu? — Giao trùng sau thời hạn khoá có thể bị xử lý lại; tài liệu không nêu thời hạn.",
  "kb_ids": [
    "webhook-ingestion#KB-023",
    "webhook-ingestion#KB-029"
  ]
}
```

## OQ-integrations-019 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-019",
  "type": "OPEN_ISSUE",
  "feature_id": "webhook-ingestion",
  "summary": "Thời gian chờ khoá đơn của orders/paid được quy định là bao nhiêu? — Giá trị duy nhất trong tài liệu chỉ là ví dụ; không dùng được làm boundary.",
  "kb_ids": [
    "webhook-ingestion#KB-024",
    "webhook-ingestion#KB-036"
  ]
}
```

## OQ-integrations-020 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-020",
  "type": "OPEN_ISSUE",
  "feature_id": "webhook-ingestion",
  "summary": "Lịch gửi lại của Shopify khi nhận 401 (số lần, khoảng cách) là gì? — Thuộc Shopify; tài liệu chỉ nói 'theo lịch của Shopify', cần biết để quan sát retry khi test.",
  "kb_ids": [
    "webhook-ingestion#KB-009"
  ]
}
```

## OQ-integrations-021 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-021",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "request-authentication",
  "summary": "Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.",
  "check_ids": [
    "request-authentication:CHK-001",
    "request-authentication:CHK-003",
    "request-authentication:CHK-005",
    "request-authentication:CHK-006",
    "request-authentication:CHK-007",
    "request-authentication:CHK-008",
    "request-authentication:CHK-010",
    "request-authentication:CHK-011"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-integrations-021: 2026-10-17: CHK-001 một phần: GET /api/boxes với Bearer hợp lệ → 200. CHK-010: block trang cảm ơn thành công chỉ với tham số shop, response {customer_id, token}. Các nhánh token sai/thiếu, uninstall, multi-shop, Flow: không làm.",
  "staging_observation_kb_ids": [
    "request-authentication#KB-016",
    "request-authentication#KB-018"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-integrations-022 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-022",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "request-authentication",
  "summary": "Request gọi Mysbox API của portal nhúng mà không kèm session token thì bị xử lý thế nào (bị chặn với mã lỗi nào, hay redirect về Shopify)?",
  "check_ids": [
    "request-authentication:CHK-004"
  ]
}
```

## OQ-integrations-023 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-023",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "request-authentication",
  "summary": "Khi Shopify Flow gọi action của Mysbox vượt giới hạn tần suất theo shop, Mysbox phản hồi thế nào (mã trạng thái nào, request bị xếp hàng hay bị bỏ)?",
  "check_ids": [
    "request-authentication:CHK-009"
  ]
}
```

## OQ-integrations-024 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-024",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "request-authentication",
  "summary": "Khi request từ extension (không ký) mang tên một shop nhưng mã đơn thuộc shop khác, Mysbox có kiểm đơn thuộc đúng shop đó không, và phản hồi thế nào?",
  "check_ids": [
    "request-authentication:CHK-012"
  ]
}
```

## OQ-integrations-025 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-025",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "webhook-ingestion",
  "summary": "Tài liệu nói webhook cho đơn test vẫn được nhận nhưng tự khai chưa xác nhận chi tiết. Cần xác nhận đơn test có được xử lý như đơn thật không (tạo yêu cầu mở box, rút thăm, ghi usage).",
  "kb_ids": [
    "webhook-ingestion#KB-041"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-integrations-025: 2026-10-17: Đơn test Bogus được tạo đơn Mysbox, bốc thăm, mở được (như đơn thật); Box sales limit 0/10 → 0/10 (exclude_test_order true). Ghi usage billing chưa quan sát.",
  "staging_observation_kb_ids": [
    "webhook-ingestion#KB-043",
    "webhook-ingestion#KB-045"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-integrations-026 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-026",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "webhook-ingestion",
  "summary": "Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.",
  "check_ids": [
    "webhook-ingestion:CHK-001",
    "webhook-ingestion:CHK-002",
    "webhook-ingestion:CHK-004",
    "webhook-ingestion:CHK-005",
    "webhook-ingestion:CHK-006",
    "webhook-ingestion:CHK-010",
    "webhook-ingestion:CHK-012",
    "webhook-ingestion:CHK-014",
    "webhook-ingestion:CHK-016"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-integrations-026: 2026-10-17: Gián tiếp cho CHK-001: đơn Mysbox ~5 giây sau paid, link Unbox ≤ 9 giây. Các check khác (forge webhook, Horizon, uninstall...) NOT_OBSERVED.",
  "staging_observation_kb_ids": [
    "webhook-ingestion#KB-044"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-integrations-027 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-027",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "webhook-ingestion",
  "summary": "Những header nào là header bắt buộc của webhook, và request thiếu một header bắt buộc bị từ chối với mã trạng thái nào?",
  "kb_ids": [
    "webhook-ingestion#KB-021"
  ],
  "check_ids": [
    "webhook-ingestion:CHK-007"
  ]
}
```

## OQ-integrations-028 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-028",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "webhook-ingestion",
  "summary": "Khi Mysbox nhận hai webhook orders/paid cho cùng một đơn nhưng khác event id, đơn có bị xử lý (rút thăm) lần thứ hai không, hay có lớp bảo vệ theo đơn?",
  "check_ids": [
    "webhook-ingestion:CHK-011"
  ]
}
```

## OQ-integrations-029 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-029",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "webhook-ingestion",
  "summary": "'Thử lại tối đa 3 lần' của shop/update là số lần job tự thử lại khi lỗi hay là cơ chế chống trùng? shop/update giao trùng có bị xử lý hai lần không?",
  "check_ids": [
    "webhook-ingestion:CHK-015"
  ]
}
```

## OQ-integrations-030 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-030",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "webhook-ingestion",
  "summary": "Webhook cho đơn test có được xử lý như đơn thật không (tạo yêu cầu mở box, rút thăm, ghi usage)?",
  "check_ids": [
    "webhook-ingestion:CHK-018"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-integrations-030: 2026-10-17: Như OQ-integrations-025: bốc thăm có, có trong Manage orders, bộ đếm không tăng; billing usage NOT_OBSERVED.",
  "staging_observation_kb_ids": [
    "webhook-ingestion#KB-043",
    "webhook-ingestion#KB-045"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve."
}
```

## OQ-integrations-031 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-031",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "request-authentication",
  "summary": "Trên staging, trang đơn hàng của khách xác thực API bằng header customer-token + customer-id qua app proxy. Server kiểm customer-token thế nào (gắn với đơn hay khách nào, hết hạn khi nào) và trả gì khi token sai, thiếu hoặc thuộc khách khác?",
  "kb_ids": [
    "request-authentication#KB-017"
  ],
  "check_ids": [
    "request-authentication:CHK-014"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-integrations-032 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-032",
  "type": "OPEN_ISSUE",
  "feature_id": "request-authentication",
  "summary": "Endpoint customer của block trang cảm ơn (/api/orders/{shopify_order_id}/customer?shop=...) trả customer_id + token chỉ dựa trên order id + tên shop: có kiểm đơn thuộc shop đó và yêu cầu đến từ extension không, gọi với order id của shop khác hoặc order id đoán thì trả gì, và host staging-api có phải backend chính thức của staging không? — Endpoint không xác thực trả token khách; không có oracle cho nhánh negative và host chưa được operator xác nhận.",
  "kb_ids": [
    "request-authentication#KB-018",
    "request-authentication#KB-013",
    "request-authentication#KB-014"
  ],
  "tags": [
    "staging-observed"
  ]
}
```

## OQ-integrations-033 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-033",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "request-authentication",
  "summary": "Quan sát staging mới chạm vùng rủi ro cao (quyền truy cập / tiền / billing): Request của merchant app tới backend: Bearer session token, không có shop id do client chọn; Trang đơn hàng của khách gửi header customer-token + customer-id qua app proxy; Block trang cảm ơn gọi backend chỉ với tham số shop, nhận customer_id + token. Item là OBSERVED_CURRENT; cần PO xác nhận đây là hành vi dự kiến trước khi dùng làm expected result.",
  "kb_ids": [
    "request-authentication#KB-016",
    "request-authentication#KB-017",
    "request-authentication#KB-018"
  ],
  "tags": [
    "staging-observed",
    "risk-flag"
  ]
}
```

## OQ-integrations-034 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-034",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "webhook-ingestion",
  "summary": "Quan sát staging mới chạm vùng rủi ro cao (quyền truy cập / tiền / billing): Đơn test Bogus được xử lý như đơn thật: có đơn Mysbox, bốc thăm, mở được, quà thêm vào đơn Shopify; Đơn test không làm tăng Box sales limit khi Exclude Test Order bật. Item là OBSERVED_CURRENT; cần PO xác nhận đây là hành vi dự kiến trước khi dùng làm expected result.",
  "kb_ids": [
    "webhook-ingestion#KB-043",
    "webhook-ingestion#KB-045"
  ],
  "tags": [
    "staging-observed",
    "risk-flag"
  ]
}
```

## OQ-integrations-035 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-035",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": null,
  "summary": "Bộ tài liệu nguồn không chỉ định role mặc định cho object này (bootstrap-request để role null): các KB item mang scope.role theo vai trò tài liệu nêu cho từng hành vi, hoặc \"unspecified\" khi tài liệu không nêu. Cần PO/Dev xác nhận ma trận role → quyền thực tế trên production (merchant owner/staff, khách, admin Mysbox theo từng role) trước khi dùng các check PERMISSION làm oracle.",
  "supersedes": "OQ-automation-growth-001"
}
```

## OQ-integrations-036 — CONFLICT

```json
{
  "oq_id": "OQ-integrations-036",
  "type": "CONFLICT",
  "feature_id": "affiliate-referral-tracking",
  "summary": "Mâu thuẫn về sự kiện vòng đời shop gửi sang dịch vụ affiliate khi merchant gỡ hoặc cài lại app. Mâu thuẫn nằm ngay trong cùng một tài liệu. Cần dev xác nhận: khi gỡ/cài lại app, Mysbox có xoá/khôi phục Customer ở dịch vụ affiliate (bằng thao tác riêng hay bằng event) hay không làm gì.",
  "side_a": "Tài liệu \"Affiliate / referral tracking và sync Partner events\" §Journey từng bước: bản ghi shop ở dịch vụ affiliate bị xoá khi gỡ app và khôi phục khi cài lại; tài liệu \"Banner thông báo trong admin và mọi email/thông báo của app\" §Mọi sự kiện → kênh → người nhận → điều kiện cũng nêu sự kiện sang dịch vụ affiliate khi gỡ/cài lại app.",
  "side_b": "Tài liệu \"Affiliate / referral tracking và sync Partner events\" §Trường hợp biên: các event installed, trial, uninstalled, reinstalled có trong thư viện nhưng Mysbox chỉ gửi subscribed / unsubscribed.",
  "conflict_group": "CONF-automation-growth-01",
  "kb_ids": [
    "affiliate-referral-tracking#KB-006",
    "affiliate-referral-tracking#KB-021",
    "affiliate-referral-tracking#KB-022",
    "affiliate-referral-tracking#KB-027"
  ],
  "check_ids": [
    "affiliate-referral-tracking:CHK-011"
  ],
  "supersedes": "OQ-automation-growth-002"
}
```

## OQ-integrations-037 — CONFLICT

```json
{
  "oq_id": "OQ-integrations-037",
  "type": "CONFLICT",
  "feature_id": "shopify-flow-actions",
  "summary": "Cần dev xác nhận khoá của bộ giới hạn 60 lần gọi action Flow mỗi phút (theo shop hay toàn cục) và hành vi khi vượt giới hạn trước khi dùng làm boundary test. Mâu thuẫn nằm ngay trong cùng một tài liệu (câu sau tự khai chưa xác nhận).",
  "side_a": "Tài liệu \"Shopify Flow: trigger, action và công thức mẫu\" §Bước 3 (cùng \"Tích hợp: tổng quan và cách xác thực request\", \"Banner thông báo trong admin và mọi email/thông báo của app\", Playbook 5): giới hạn 60 lần gọi/phút/shop",
  "side_b": "Cùng tài liệu \"Shopify Flow: trigger, action và công thức mẫu\" §Bước 3, câu kế tiếp tự khai chưa xác nhận Flow có gửi mã shop cho bộ giới hạn; nếu không, mọi shop dùng chung một xô",
  "conflict_group": "CONF-automation-growth-06",
  "kb_ids": [
    "shopify-flow-actions#KB-031",
    "shopify-flow-actions#KB-032"
  ],
  "check_ids": [
    "shopify-flow-actions:CHK-016"
  ],
  "supersedes": "OQ-automation-growth-010"
}
```

## OQ-integrations-038 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-038",
  "type": "OPEN_ISSUE",
  "feature_id": "affiliate-referral-tracking",
  "summary": "Giới hạn đã biết: merchant cài app nhưng mở portal lần đầu quá 30 phút sau khi cài (ví dụ bỏ giữa chừng) thì không gắn được affiliate cho shop đó. Cần PO quyết định đây là hành vi chấp nhận hay lỗi cần sửa; trong lúc chờ, chỉ dùng làm regression watch, không làm oracle.",
  "kb_ids": [
    "affiliate-referral-tracking#KB-026"
  ],
  "check_ids": [
    "affiliate-referral-tracking:CHK-005"
  ],
  "supersedes": "OQ-automation-growth-014"
}
```

## OQ-integrations-039 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-039",
  "type": "OPEN_ISSUE",
  "feature_id": "affiliate-referral-tracking",
  "summary": "Mốc 30 phút tính từ thời điểm nào (tạo shop hay cài app), và đúng 30 phút thì được chấp nhận hay từ chối? — Boundary test của luật 'Instance is too old'.",
  "kb_ids": [
    "affiliate-referral-tracking#KB-016"
  ],
  "supersedes": "OQ-automation-growth-015"
}
```

## OQ-integrations-040 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-040",
  "type": "OPEN_ISSUE",
  "feature_id": "affiliate-referral-tracking",
  "summary": "HTTP status, field kỹ thuật và cơ chế xác thực của POST api/affiliate/tracking-id và POST api/affiliate/customers là gì? — Không kiểm được contract API và negative auth.",
  "kb_ids": [
    "affiliate-referral-tracking#KB-012",
    "affiliate-referral-tracking#KB-015"
  ],
  "supersedes": "OQ-automation-growth-016"
}
```

## OQ-integrations-041 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-041",
  "type": "OPEN_ISSUE",
  "feature_id": "affiliate-referral-tracking",
  "summary": "Khi dịch vụ affiliate lỗi lúc cấp tracking id hoặc đăng ký Customer thì Mysbox xử lý thế nào (retry, thông báo, lưu trạng thái)? — Referral có thể mất im lặng.",
  "kb_ids": [
    "affiliate-referral-tracking#KB-013",
    "affiliate-referral-tracking#KB-018"
  ],
  "supersedes": "OQ-automation-growth-017"
}
```

## OQ-integrations-042 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-042",
  "type": "OPEN_ISSUE",
  "feature_id": "affiliate-referral-tracking",
  "summary": "Thời hạn sống của cookie koin_trkcd là bao lâu? — Ảnh hưởng việc ghi nhận referral khi merchant cài app muộn sau khi bấm link.",
  "kb_ids": [
    "affiliate-referral-tracking#KB-014",
    "affiliate-referral-tracking#KB-041"
  ],
  "supersedes": "OQ-automation-growth-018"
}
```

## OQ-integrations-043 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-043",
  "type": "OPEN_ISSUE",
  "feature_id": "affiliate-referral-tracking",
  "summary": "Giá trị PREFIX, tên cờ môi trường pricing affiliate, mã giảm giá đặc biệt cụ thể và thứ tự ưu tiên giữa mã dạng có REF và dạng ngắn khi cả hai tồn tại là gì? — Cần để dựng case tự áp mã affiliate.",
  "kb_ids": [
    "affiliate-referral-tracking#KB-001",
    "affiliate-referral-tracking#KB-002"
  ],
  "supersedes": "OQ-automation-growth-019"
}
```

## OQ-integrations-044 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-044",
  "type": "OPEN_ISSUE",
  "feature_id": "partner-events-bigquery-sync",
  "summary": "Lỗi đã biết: sync Partner events sang BigQuery chỉ nối thêm và BigQuery không khử trùng, nên chạy lại một ngày đã sync (kể cả bằng lệnh backfill) làm nhân đôi dòng. Cần dev/PO xác nhận hướng xử lý (khử trùng, idempotency) và quy trình an toàn khi nạp bù; trong lúc chờ, chỉ dùng làm regression watch.",
  "kb_ids": [
    "partner-events-bigquery-sync#KB-016"
  ],
  "check_ids": [
    "partner-events-bigquery-sync:CHK-009"
  ],
  "supersedes": "OQ-automation-growth-021"
}
```

## OQ-integrations-045 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-045",
  "type": "OPEN_ISSUE",
  "feature_id": "partner-events-bigquery-sync",
  "summary": "Khi không tìm thấy bản ghi shop của Mysbox, các cột gói / quốc gia / email trong BigQuery được ghi giá trị gì? — Kỳ vọng dữ liệu cho shop không còn bản ghi.",
  "kb_ids": [
    "partner-events-bigquery-sync#KB-009"
  ],
  "supersedes": "OQ-automation-growth-022"
}
```

## OQ-integrations-046 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-046",
  "type": "OPEN_ISSUE",
  "feature_id": "partner-events-bigquery-sync",
  "summary": "Endpoint cụ thể của Shopify Partner API được gọi là gì, và khi một trang lỗi giữa chừng thì dữ liệu một phần có được ghi không? — Job chỉ thử một lần; cần biết trạng thái dữ liệu sau lỗi giữa chừng.",
  "kb_ids": [
    "partner-events-bigquery-sync#KB-002",
    "partner-events-bigquery-sync#KB-010",
    "partner-events-bigquery-sync#KB-018"
  ],
  "supersedes": "OQ-automation-growth-023"
}
```

## OQ-integrations-047 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-047",
  "type": "OPEN_ISSUE",
  "feature_id": "partner-events-bigquery-sync",
  "summary": "'Chạy lệnh sync' của nhân viên admin (nêu ở mức nhóm tính năng) có phải là lệnh sync Partner events sang BigQuery không? — Nếu đúng, có thêm actor admin-staff và entry point ở admin panel cho feature này.",
  "kb_ids": [
    "_object-level#KB-001"
  ],
  "supersedes": "OQ-automation-growth-024"
}
```

## OQ-integrations-048 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-048",
  "type": "OPEN_ISSUE",
  "feature_id": "shopify-flow-actions",
  "summary": "Route, method, header chữ ký và mã phản hồi của các action (thành công, chữ ký sai, đơn không tìm thấy) là gì? — Không có contract cụ thể để kiểm request bị từ chối hay thông báo lỗi trả về Flow.",
  "kb_ids": [
    "shopify-flow-actions#KB-016",
    "shopify-flow-actions#KB-017",
    "shopify-flow-actions#KB-022"
  ],
  "supersedes": "OQ-automation-growth-037"
}
```

## OQ-integrations-049 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-049",
  "type": "OPEN_ISSUE",
  "feature_id": "shopify-flow-actions",
  "summary": "\"Remove order boxes\" phản hồi thế nào khi đơn chỉ có box physical hoặc khi dùng cho dòng box physical? — Negative case cho điều kiện chỉ áp cho dòng box digital.",
  "kb_ids": [
    "shopify-flow-actions#KB-008",
    "shopify-flow-actions#KB-009"
  ],
  "supersedes": "OQ-automation-growth-038"
}
```

## OQ-integrations-050 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-050",
  "type": "OPEN_ISSUE",
  "feature_id": "shopify-flow-triggers",
  "summary": "Tài liệu mô tả như lỗi đã biết: trigger Shopify Flow gửi bằng job nền không retry nên khi Shopify từ chối hoặc hàng đợi lỗi thì sự kiện mất, và không có công cụ admin nào để phát lại trigger. Cần biết đây là hành vi được chấp nhận hay lỗi có kế hoạch sửa, và QA nên kiểm thế nào.",
  "kb_ids": [
    "shopify-flow-triggers#KB-015",
    "shopify-flow-triggers#KB-016"
  ],
  "check_ids": [
    "shopify-flow-triggers:CHK-028",
    "shopify-flow-triggers:CHK-029"
  ],
  "supersedes": "OQ-automation-growth-039"
}
```

## OQ-integrations-051 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-051",
  "type": "OPEN_ISSUE",
  "feature_id": "shopify-flow-triggers",
  "summary": "Khoảng hợp lệ và validation của \"Auto-unbox after\" và \"Trigger before\" (min/max, số nguyên, cho phép 0, để trống)? — Không có boundary để viết test validation cho hai ô cấu hình nhắc.",
  "kb_ids": [
    "shopify-flow-triggers#KB-031",
    "shopify-flow-triggers#KB-032"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-automation-growth-040: 2026-10-17: Validation không quan sát (classifier). Không có item.",
  "staging_observation_kb_ids": [],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; mục vẫn mở (câu hỏi chưa được trả lời đủ, hoặc cần nguồn thẩm quyền).",
  "supersedes": "OQ-automation-growth-040"
}
```

## OQ-integrations-052 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-052",
  "type": "OPEN_ISSUE",
  "feature_id": "shopify-flow-triggers",
  "summary": "\"Resell completed\" bắn một lần cho mỗi lượt resell hay mỗi item, và Amount/Currency là tiền theo tiền tệ shop hay tiền khách thanh toán? — Workflow lọc theo Amount cần ngữ nghĩa tiền tệ đúng.",
  "kb_ids": [
    "shopify-flow-triggers#KB-046",
    "shopify-flow-triggers#KB-049"
  ],
  "supersedes": "OQ-automation-growth-041"
}
```

## OQ-integrations-053 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-053",
  "type": "OPEN_ISSUE",
  "feature_id": "shopify-flow-triggers",
  "summary": "Tắt công tắc trigger khi đã có trigger nằm trong hàng đợi thì trigger đó còn được gửi không? — Tài liệu chỉ nói bật xong không phát lại sự kiện cũ; chiều ngược lại chưa có oracle.",
  "kb_ids": [
    "shopify-flow-triggers#KB-006",
    "shopify-flow-triggers#KB-012"
  ],
  "supersedes": "OQ-automation-growth-042"
}
```

## OQ-integrations-054 — OPEN_ISSUE

```json
{
  "oq_id": "OQ-integrations-054",
  "type": "OPEN_ISSUE",
  "feature_id": "shopify-flow-triggers",
  "summary": "Scheduler trên production chạy ở đâu và theo múi giờ nào; phút :30 của bộ quét tính theo giờ server hay giờ shop? — Thời điểm bắn Order unboxing soon và mọi expected result về giờ job phụ thuộc múi giờ; tài liệu tự khai chưa xác nhận.",
  "kb_ids": [
    "_product-level#KB-PL-028",
    "shopify-flow-triggers#KB-036",
    "shopify-flow-triggers#KB-037"
  ],
  "supersedes": "OQ-automation-growth-043"
}
```

## OQ-integrations-055 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-055",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": null,
  "summary": "Tài liệu Shopify Flow chỉ tự khai là không tìm thấy giới hạn theo gói Mysbox cho tích hợp Shopify Flow, không khẳng định là không có. Cần dev/PO xác nhận gói Mysbox (Free hoặc gói trả phí) có giới hạn quyền dùng trigger/action Shopify Flow hay không.",
  "kb_ids": [
    "_object-level#KB-004",
    "_object-level#KB-005"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-automation-growth-048: 2026-10-17: Shop Free: công tắc Flow không khoá/không badge; Pricing không nhắc Flow. Không bật nên giới hạn phía server chưa biết.",
  "staging_observation_kb_ids": [
    "_object-level.automation-growth#KB-006"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.",
  "supersedes": "OQ-automation-growth-048"
}
```

## OQ-integrations-056 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-056",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": null,
  "summary": "Yêu cầu bootstrap không nêu role; các item của nhóm tự động hoá và tăng trưởng không có role được tài liệu nêu rõ mang scope.role unspecified. Cần PO xác nhận role áp dụng (merchant, admin/nhân viên nội bộ hay hệ thống) cho các phát biểu mức nhóm, ví dụ việc phần còn lại của nhóm đã chạy trên production.",
  "kb_ids": [
    "_object-level#KB-003"
  ],
  "supersedes": "OQ-automation-growth-049"
}
```

## OQ-integrations-057 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-057",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "affiliate-referral-tracking",
  "summary": "Tài liệu tự khai chưa xác nhận từ phía Mysbox rằng tiền hoa hồng 30% do nền tảng affiliate tính (kể cả con số minh hoạ 14,7 USD/tháng cho gói giả định 49 USD). Cần PO/dev xác nhận nơi tính hoa hồng, cơ sở phí, thời hạn hưởng và cách xử lý refund/discount.",
  "kb_ids": [
    "affiliate-referral-tracking#KB-008",
    "affiliate-referral-tracking#KB-025",
    "affiliate-referral-tracking#KB-031"
  ],
  "check_ids": [
    "affiliate-referral-tracking:CHK-016"
  ],
  "supersedes": "OQ-automation-growth-050"
}
```

## OQ-integrations-058 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-058",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "affiliate-referral-tracking",
  "summary": "Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.",
  "check_ids": [
    "affiliate-referral-tracking:CHK-007",
    "affiliate-referral-tracking:CHK-012",
    "affiliate-referral-tracking:CHK-013"
  ],
  "supersedes": "OQ-automation-growth-051"
}
```

## OQ-integrations-059 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-059",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "affiliate-referral-tracking",
  "summary": "Việc job 'unsubscribe' chạy cho mọi shop (kể cả shop không phải affiliate) khi hạ từ gói test sang gói thật có phải chủ đích không, và job đó gửi gì sang dịch vụ affiliate cho shop không phải affiliate?",
  "kb_ids": [
    "affiliate-referral-tracking#KB-028"
  ],
  "check_ids": [
    "affiliate-referral-tracking:CHK-010"
  ],
  "supersedes": "OQ-automation-growth-052"
}
```

## OQ-integrations-060 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-060",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-actions",
  "summary": "Tên action Shopify Flow không thống nhất giữa các tài liệu: \"Open all mystery boxes in an order\" (tài liệu Hành trình reveal, Quà được thêm vào đơn Shopify) so với \"Open order boxes\" (tài liệu Shopify Flow, Playbook 5); \"Handle paid order from external sales channel with mystery boxes\" (tài liệu Mua box và random quà) so với \"Handle external sales channel order paid\". Cần xác nhận tên hiển thị chính xác trong Shopify Flow.",
  "kb_ids": [
    "shopify-flow-actions#KB-002",
    "shopify-flow-actions#KB-003",
    "shopify-flow-actions#KB-005",
    "shopify-flow-actions#KB-006",
    "shopify-flow-actions#KB-019",
    "shopify-flow-actions#KB-024"
  ],
  "supersedes": "OQ-automation-growth-078"
}
```

## OQ-integrations-061 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-061",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-actions",
  "summary": "Khoảng chờ ít nhất 10 giây sau khi đơn thanh toán trước khi gọi \"Open order boxes\" là khuyến nghị (theo tài liệu Shopify Flow) hay điều kiện bắt buộc (theo cách diễn đạt của Playbook 5)? Cần xác nhận trước khi viết check theo thời gian chờ.",
  "kb_ids": [
    "shopify-flow-actions#KB-020",
    "shopify-flow-actions#KB-037"
  ],
  "supersedes": "OQ-automation-growth-079"
}
```

## OQ-integrations-062 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-062",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-actions",
  "summary": "Tên hiển thị chính xác của các action Mysbox trong Shopify Flow là gì: \"Open order boxes\" hay \"Open all mystery boxes in an order\"; \"Handle external sales channel order paid\" hay \"Handle paid order from external sales channel with mystery boxes\"?",
  "kb_ids": [
    "shopify-flow-actions#KB-013",
    "shopify-flow-actions#KB-014",
    "shopify-flow-actions#KB-015"
  ],
  "check_ids": [
    "shopify-flow-actions:CHK-001"
  ],
  "supersedes": "OQ-automation-growth-080"
}
```

## OQ-integrations-063 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-063",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-actions",
  "summary": "Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.",
  "check_ids": [
    "shopify-flow-actions:CHK-002",
    "shopify-flow-actions:CHK-008",
    "shopify-flow-actions:CHK-011",
    "shopify-flow-actions:CHK-012",
    "shopify-flow-actions:CHK-014"
  ],
  "supersedes": "OQ-automation-growth-081"
}
```

## OQ-integrations-064 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-064",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-actions",
  "summary": "Khoảng chờ ít nhất 10 giây sau khi đơn thanh toán trước khi gọi action mở box là khuyến nghị hay điều kiện bắt buộc? Một tài liệu ghi là khuyến nghị, playbook hỗ trợ lại hướng dẫn như yêu cầu.",
  "check_ids": [
    "shopify-flow-actions:CHK-005"
  ],
  "supersedes": "OQ-automation-growth-082"
}
```

## OQ-integrations-065 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-065",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-actions",
  "summary": "Khi merchant mở box qua action Shopify Flow và quà được thêm vào đơn ngay, khách có mất quyền resell món đó không? Tài liệu chỉ nêu điều này trong ví dụ.",
  "check_ids": [
    "shopify-flow-actions:CHK-006"
  ],
  "supersedes": "OQ-automation-growth-083"
}
```

## OQ-integrations-066 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-066",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-actions",
  "summary": "Với đơn nhiều box đã mở một phần, khi gọi action mở box qua Flow thì quà của box nào được thêm vào đơn ngay: chỉ các box vừa mở hay cả box khách đã mở trước đó; và winningItems gồm những quà nào?",
  "check_ids": [
    "shopify-flow-actions:CHK-007"
  ],
  "supersedes": "OQ-automation-growth-084"
}
```

## OQ-integrations-067 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-067",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-actions",
  "summary": "\"Remove order boxes\" phản hồi thế nào với đơn chỉ có box physical, và với đơn hỗn hợp thì dòng box physical có được giữ nguyên không?",
  "check_ids": [
    "shopify-flow-actions:CHK-010"
  ],
  "supersedes": "OQ-automation-growth-085"
}
```

## OQ-integrations-068 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-068",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-actions",
  "summary": "Gọi \"Handle external sales channel order paid\" nhiều lần cho cùng một đơn thì Mysbox bỏ qua lần sau hay xử lý lại (bốc thăm lại, nhân quà, trừ tồn kho thêm)?",
  "check_ids": [
    "shopify-flow-actions:CHK-013"
  ],
  "supersedes": "OQ-automation-growth-086"
}
```

## OQ-integrations-069 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-069",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-triggers",
  "summary": "Tài liệu chỉ có ví dụ số (48 - 6 = 42 giờ sau đơn) cho giờ thông báo của trigger \"Order unboxing soon\", không có công thức tổng quát; chưa rõ hành vi khi \"Trigger before\" lớn hơn hoặc bằng thời gian auto-unbox, phút :30 của bộ quét theo múi giờ nào, và câu \"đổi setting không ảnh hưởng đơn đã tạo\" áp cho những setting nào (có gồm công tắc Flow không).",
  "kb_ids": [
    "shopify-flow-triggers#KB-033",
    "shopify-flow-triggers#KB-042",
    "shopify-flow-triggers#KB-063",
    "shopify-flow-triggers#KB-064",
    "shopify-flow-triggers#KB-065"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-automation-growth-087: 2026-10-17: Như OQ-040.",
  "staging_observation_kb_ids": [],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.",
  "supersedes": "OQ-automation-growth-087"
}
```

## OQ-integrations-070 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-070",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-triggers",
  "summary": "Giờ thông báo của trigger \"Order unboxing soon\" được tính theo công thức nào (tài liệu chỉ có ví dụ số)? Khi \"Trigger before\" lớn hơn hoặc bằng thời gian auto-unbox thì hệ thống chặn lưu, bỏ qua không nhắc hay nhắc ngay? Khoảng giá trị hợp lệ của \"Auto-unbox after\" và \"Trigger before\" là gì (tối thiểu, tối đa, có cho 0 hay để trống)?",
  "check_ids": [
    "shopify-flow-triggers:CHK-016"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-automation-growth-088: 2026-10-17: Như OQ-040; công thức giờ bắn NOT_OBSERVED.",
  "staging_observation_kb_ids": [],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.",
  "supersedes": "OQ-automation-growth-088"
}
```

## OQ-integrations-071 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-071",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-triggers",
  "summary": "Câu \"đổi setting không ảnh hưởng đơn đã tạo\" áp cho những setting nào: chỉ \"Trigger before\" và thời gian auto-unbox, hay cả việc tắt \"Enable auto-unbox trigger\"/Auto-unbox và công tắc trigger Shopify Flow sau khi đơn đã tạo?",
  "kb_ids": [
    "shopify-flow-triggers#KB-041",
    "shopify-flow-triggers#KB-042"
  ],
  "check_ids": [
    "shopify-flow-triggers:CHK-017"
  ],
  "supersedes": "OQ-automation-growth-089"
}
```

## OQ-integrations-072 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-072",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-triggers",
  "summary": "Khi khách resell nhiều item trong một lượt, \"Resell completed\" bắn một lần cho cả lượt hay một lần cho mỗi item? Amount và Currency tính theo tiền tệ của shop hay tiền tệ khách đã thanh toán?",
  "check_ids": [
    "shopify-flow-triggers:CHK-020"
  ],
  "supersedes": "OQ-automation-growth-090"
}
```

## OQ-integrations-073 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-073",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-triggers",
  "summary": "Các check P1 (tiền / billing / bốc thăm / refund / store credit / permission / xoá dữ liệu) của feature này có oracle STRONG nhưng chỉ dựa trên tài liệu dev (dev_doc). Theo luật oracle, chúng giữ NEEDS_CONFIRMATION cho tới khi có test_case PASS (hoặc PO/Dev xác nhận trực tiếp) cho đúng hành vi. Danh sách check ở check_ids.",
  "check_ids": [
    "shopify-flow-triggers:CHK-025"
  ],
  "supersedes": "OQ-automation-growth-091"
}
```

## OQ-integrations-074 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-074",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-triggers",
  "summary": "Gói Mysbox (Free hoặc gói trả phí) có giới hạn quyền dùng trigger Shopify Flow không? Tài liệu chỉ nói không tìm thấy giới hạn, chưa khẳng định là không có.",
  "check_ids": [
    "shopify-flow-triggers:CHK-026"
  ],
  "staging_observation": "Ghi chú quan sát staging cho OQ-automation-growth-092: 2026-10-17: Như OQ-automation-growth-048.",
  "staging_observation_kb_ids": [
    "_object-level.automation-growth#KB-006"
  ],
  "status_note": "Quan sát staging chỉ là OBSERVED_CURRENT; vẫn cần PO/Dev xác nhận, chưa resolve.",
  "supersedes": "OQ-automation-growth-092"
}
```

## OQ-integrations-075 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-075",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "shopify-flow-triggers",
  "summary": "Nếu merchant tắt công tắc trigger Shopify Flow khi một trigger đã vào hàng đợi nhưng chưa gửi tới Flow, trigger đó còn được gửi hay bị bỏ?",
  "check_ids": [
    "shopify-flow-triggers:CHK-027"
  ],
  "supersedes": "OQ-automation-growth-093"
}
```

## OQ-integrations-076 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-integrations-076",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": null,
  "summary": "Quan sát staging mới chạm vùng rủi ro cao (quyền truy cập / tiền / billing): Shopify Flow trên shop gói Free: công tắc không khoá, Pricing không nhắc Flow. Item là OBSERVED_CURRENT; cần PO xác nhận đây là hành vi dự kiến trước khi dùng làm expected result.",
  "kb_ids": [
    "_object-level.automation-growth#KB-006"
  ],
  "tags": [
    "staging-observed",
    "risk-flag"
  ],
  "supersedes": "OQ-automation-growth-103"
}
```
