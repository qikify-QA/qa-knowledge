# Open Questions — MCP server

Các mục dưới đây còn mở. Không dùng phần còn mở làm expected result.

## Tóm tắt

| Loại | Số lượng |
|---|---|
| NEEDS_CONFIRMATION | 25 |
| OPEN_ISSUE | 4 |
| CONFLICT | 1 |
| **Tổng** | **30** |

## OQ-mcp-001 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-001","type":"NEEDS_CONFIRMATION","feature_id":"mcp-client-connection","summary":"Danh mục tool của MCP server staging (tools/list đã xác thực: tên, description, inputSchema, annotations), gồm nhóm layer image (upload/create/confirm/view/list layer image) và nhóm artwork, chưa quan sát được vì không có token MCP đã xác minh thuộc account explore. Cần operator cấp token đó hoặc output tools/list đã redact, và Dev xác nhận contract (KB-1614, KB-1615)."}
```

## OQ-mcp-002 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-002","type":"NEEDS_CONFIRMATION","feature_id":"mcp-client-connection","summary":"initialize đã xác thực trả gì (protocolVersion, capabilities, serverInfo) và server có gửi instructions không? Chưa quan sát (KB-1614)."}
```

## OQ-mcp-003 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-003","type":"NEEDS_CONFIRMATION","feature_id":"mcp-client-connection","summary":"Request đã xác thực nhưng sai (method lạ, params sai, input tool sai) trả lỗi dạng JSON-RPC (jsonrpc/id/error) hay dạng {message} như response 401 (KB-1614)? Cần Dev xác nhận shape lỗi mong đợi."}
```

## OQ-mcp-004 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-004","type":"NEEDS_CONFIRMATION","feature_id":"mcp-client-connection","summary":"Token hết hạn, token đã xoá và token hợp lệ nhưng thiếu ability mcp:access gọi /mcp trả status gì (401 hay 403, www-authenticate, body)? Mới quan sát thiếu token và token giả, hai trường hợp cho response giống nhau (KB-1615, KB-1612)."}
```

## OQ-mcp-005 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-005","type":"NEEDS_CONFIRMATION","feature_id":"mcp-client-connection","summary":"MCP server có nhận cookie session portal (không Bearer) không, và việc preflight không trả CORS header cho origin portal có chủ ý không (MCP chỉ dành cho client ngoài trình duyệt)? Fetch từ portal bị chặn nên chưa trả lời được (KB-1617, KB-1618, KB-1619)."}
```

## OQ-mcp-006 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-006","type":"NEEDS_CONFIRMATION","feature_id":"mcp-client-connection","summary":"/mcp có rate limit không (giới hạn, header, response khi vượt)? Response 401 không có header x-ratelimit-*; response đã xác thực chưa quan sát (KB-1616)."}
```

## OQ-mcp-007 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-007","type":"NEEDS_CONFIRMATION","feature_id":"mcp-client-connection","summary":"Nút Generate MCP token tạo token thế nào: chỉ ability mcp:access hay thêm ability khác, có hạn dùng, có hỏi tên, hiện một lần rồi điền vào config client không? Mọi token có mcp:access (kể cả tạo qua Create new key ở /api-keys) có dùng được cho MCP không (KB-1603, KB-1609, KB-1611, KB-1612)?"}
```

## OQ-mcp-008 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-008","type":"NEEDS_CONFIRMATION","feature_id":"mcp-client-connection","summary":"Config Claude Desktop dùng npx mcp-remote (bắc cầu stdio sang HTTP) có phải cách kết nối được hỗ trợ không, khác biệt macOS/Linux và Windows là gì, và QA có cần kiểm kết nối thật từ Claude Code, Claude Desktop, Codex không (KB-1606, KB-1607, KB-1608)?"}
```

## OQ-mcp-009 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-009","type":"NEEDS_CONFIRMATION","feature_id":"mcp-client-connection","summary":"GET và DELETE trên /mcp (có trong header allow của preflight) dùng để làm gì (SSE stream, kết thúc session) và có thuộc phạm vi QA không (KB-1618)?"}
```

## OQ-mcp-010 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-010","type":"NEEDS_CONFIRMATION","feature_id":"mcp-client-connection","summary":"Role khác merchant-owner (vd staff quyền hạn chế) và account chưa có token nào: sidebar có mục AI Assistant (MCP) không, trang /mcp và /api-keys hiện gì, có được Generate MCP token không? Run chỉ quan sát owner trên một account đã có một token (KB-1601, KB-1603, KB-1610)."}
```

## OQ-mcp-011 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-mcp-011", "type": "NEEDS_CONFIRMATION", "feature_id": "mcp-layer-image-upload", "summary": "[CBS-152, TIB-5709] upload-layer-image-tool (KB-1621, quan sát TC-TIB-8770 không ghi build): note \"Image variants are generated asynchronously. Poll view-layer-image-tool (or list-layer-images-tool) until the thumbnail is set, then use the returned url in layers.\", bản large ở artwork_max_width của merchant, ready sau khoảng 14 giây — có phải expected? Job trên queue make-previewable-images không quan sát được trên staging.", "kb_ids": ["KB-1621"], "needs": "Dev xác nhận kèm nguyên văn có ngày."}
```

## OQ-mcp-012 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-mcp-012", "type": "NEEDS_CONFIRMATION", "feature_id": "mcp-layer-image-upload", "summary": "[CBS-152, TIB-5709] Description của upload-layer-image-tool, server instructions và overview workflow nói raster trả processing, phải poll view-layer-image-tool trước khi dùng url (KB-1622, quan sát TC-TIB-8782 không ghi build). Đây có phải contract cho agent?", "kb_ids": ["KB-1622"], "needs": "Dev xác nhận."}
```

## OQ-mcp-013 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-mcp-013", "type": "NEEDS_CONFIRMATION", "feature_id": "mcp-layer-image-upload", "summary": "[CBS-152, TIB-5709] SVG không bị kiểm pixel trên upload-layer-image-tool và confirm-layer-image-upload-tool; confirm tool với SVG trả status ready, note 'Nothing to poll.' (KB-1624, quan sát không ghi build) — xác nhận?", "kb_ids": ["KB-1624"], "needs": "Dev xác nhận."}
```

## OQ-mcp-014 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-mcp-014", "type": "NEEDS_CONFIRMATION", "feature_id": "mcp-layer-image-upload", "summary": "[CBS-152, TIB-5709] Kết quả queue của upload-layer-image-tool giống đường inline portal /file (KB-1625) chỉ được so ở điều kiện layer_width = artwork_width do QA chọn; inline đổi large theo layer_width. Dev muốn so ở điều kiện nào?", "kb_ids": ["KB-1625"], "needs": "Dev xác nhận điều kiện so sánh."}
```

## OQ-mcp-015 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-mcp-015", "type": "NEEDS_CONFIRMATION", "feature_id": "mcp-layer-image-upload", "summary": "[CBS-152, TIB-5709] Lỗi cap 128 MP trên tool MCP (KB-1627, quan sát không ghi build): message cap, đuôi ' The upload has been removed.' của confirm tool, message confirm lại 'Upload not found or expired. Mint a new one with create-layer-image-upload-tool.', batch: file over-cap failed, file hợp lệ processing, created_count/failed_count — có phải expected?", "kb_ids": ["KB-1627"], "needs": "Dev xác nhận."}
```

## OQ-mcp-016 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-mcp-016", "type": "NEEDS_CONFIRMATION", "feature_id": "mcp-layer-image-upload", "summary": "[CBS-152, TIB-5709] Ranh giới 128 MP qua upload-layer-image-tool (KB-1628): một lượt không ghi build; confirm tool chưa chạy ranh giới. Quy tắc 'bằng hoặc dưới cap không bị từ chối' theo open-api KB-057.", "kb_ids": ["KB-1628"], "needs": "QA chạy lại có build, thêm confirm tool."}
```

## OQ-mcp-017 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-mcp-017", "type": "NEEDS_CONFIRMATION", "feature_id": "mcp-layer-image-upload", "summary": "[CBS-152, TIB-5709] Message header hỏng trên upload-layer-image-tool và confirm-layer-image-upload-tool (KB-1629, quan sát không ghi build) — có phải expected?", "kb_ids": ["KB-1629"], "needs": "Dev xác nhận."}
```

## OQ-mcp-018 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-mcp-018", "type": "NEEDS_CONFIRMATION", "feature_id": "mcp-layer-image-upload", "summary": "[CBS-152, TIB-5709] Chưa chạy cho feature mcp-layer-image-upload: production (verify NOT-RUN theo CCR), lượt chạy bằng token MCP của account explore (chưa có, xem OQ-mcp-001), list-layer-images-tool và các lỗi khác của create-layer-image-upload-tool.", "kb_ids": ["KB-1620", "KB-1626"], "needs": "Operator cấp token MCP của account explore; QA chạy lượt production."}
```

## OQ-mcp-019 — OPEN_ISSUE

```json
{"oq_id":"OQ-mcp-019","type":"OPEN_ISSUE","feature_id":"mcp-artwork-tools","kb_ids":["KB-1003"],"summary":"[CBS-120] Hành vi chưa ship (TIB-5486 còn QA Review, re-open 2026-10-28; lượt QA-3423 ngày 2026-11-02 tool trả not found): KB-1003 là đề xuất theo câu trả lời của Dev 2026-10-26 (RQ16). Khi ship, cap mỗi lần gọi của import-artwork-json-tool (20 clipart category, 20 global option inline, 50 item mỗi category, không vượt cap clipart của category) có đúng không, và message lỗi khi vượt là gì? Cần: test case Testlane PASS trên build có TIB-5486, kèm căn cứ expected.","owner":"Dev","supersedes":"OQ-artwork-475"}
```

## OQ-mcp-020 — OPEN_ISSUE

```json
{"oq_id":"OQ-mcp-020","type":"OPEN_ISSUE","feature_id":"mcp-artwork-tools","kb_ids":["KB-1004"],"summary":"[CBS-120] Hành vi chưa ship: KB-1004 là đề xuất theo câu trả lời của Dev 2026-10-26 (RQ16). Khi TIB-5486 ship, quota theo ngày của import-artwork-json-tool (clipart_category 1000, clipart 4000, cửa sổ 24h; global_option không có quota ngày) có đúng không? Các số là giá trị cấu hình qua env, có thể đổi. Cần: test case Testlane PASS trên build có TIB-5486 (Dev chỉ cách hạ giới hạn bằng cột giới hạn của users cho merchant test).","owner":"Dev","supersedes":"OQ-artwork-476"}
```

## OQ-mcp-021 — CONFLICT

```json
{"oq_id":"OQ-mcp-021","type":"CONFLICT","feature_id":"mcp-artwork-tools","kb_ids":[],"summary":"[CBS-120] CLAIM-03 (S0, không nạp KB): bộ đếm quota clipart và clipart_category của MCP import-artwork-json-tool dùng chung limiter với REST (POST /api/cliparts/svg, POST /api/clipart-categories) hay riêng cho tool? Câu trả lời của Dev 2026-10-26 chỉ nêu số quota và tên env, không nói chung hay riêng; chưa ai gọi REST và MCP trên cùng account rồi so bộ đếm. Cần: Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected.","owner":"Dev","side_a":"asset-category KB-035, KB-036 (đo trên REST, staging): route tạo clipart dùng resource user_rate_limiter:clipart limit 4000, route tạo category dùng user_rate_limiter:clipart_category limit 1000 — cùng số với quota Dev nêu cho MCP import, gợi ý có thể cùng limiter.","side_b":"Rule QA FACT-171 (kho QA local, không có path mở lại được; suy diễn của QA, không phải lời Dev/PO): quota clipart và clipart_category của import tool là riêng cho tool này, không phải baseline portal-api chung.","supersedes":"OQ-artwork-477"}
```

## OQ-mcp-022 — OPEN_ISSUE

```json
{"oq_id":"OQ-mcp-022","type":"OPEN_ISSUE","feature_id":"mcp-artwork-tools","kb_ids":["KB-1005"],"summary":"[CBS-120] Hành vi chưa ship: KB-1005 là đề xuất theo câu trả lời của Dev 2026-10-26 (RQ17): clipart category tạo qua import-artwork-json-tool hay create-clipart-category-tool đều có source = mcp. Response của create-clipart-category-tool không trả field source (QA-3423 TC-32), nên đọc source ở đâu để kiểm (DB, GraphQL, UI)? Source của clipart item có cũng là mcp không (câu trả lời chỉ nói category)? Cần: Dev chỉ nơi đọc, và test case Testlane PASS trên build có TIB-5486.","owner":"Dev","supersedes":"OQ-artwork-478"}
```

## OQ-mcp-023 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-023","type":"NEEDS_CONFIRMATION","feature_id":"mcp-artwork-tools","kb_ids":["KB-1023"],"summary":"[CBS-143] KB-1023: kiểm tra artwork của MCP có chặn layer static-photo và photo No personalization không có ảnh không (AC5 TIB-5446 nói API hoặc MCP save không được tạo layer static-photo không url), và áp ở tool MCP nào? Change note chỉ nói chặn thêm clipart-category / group-clipart-categories.","supersedes":"OQ-artwork-500"}
```

## OQ-mcp-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-024","type":"NEEDS_CONFIRMATION","feature_id":"mcp-artwork-tools","kb_ids":["KB-1052"],"check_ids":["CHK-005"],"summary":"[CBS-122] Rule QA FACT-174 (KB-1052, PROPOSED): khi đọc qua get-artwork-tool / archive-artwork-tool, status của artwork Archived có đúng là 1 (\"Status Archive\") và Active là 0 (\"Status Default\") không? Change note Dev TIB-5488 chỉ nêu 0 = Active, 2 = Pending, 3 = Importing, 4 = Import failed, không nêu giá trị Archived. Record Testlane TC-TIB-6943 (QA-3425 TC-27) đang skipped. CHK-005 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-524"}
```

## OQ-mcp-025 — OPEN_ISSUE

```json
{"oq_id":"OQ-mcp-025","type":"OPEN_ISSUE","feature_id":"mcp-artwork-tools","kb_ids":["KB-1052","KB-1053"],"check_ids":["CHK-006"],"summary":"[CBS-122] Hành vi chưa ship: KB-1052 và KB-1053 thuộc đợt TIB-5488 (QA Review, PR #4050 còn mở ngày 2026-11-12). KB-1053 (update-artwork-tool trên artwork Active/Archived không đổi status) theo change note Dev 2026-10-22, dòng Regression, tức Dev coi là hành vi có từ trước TIB-5488. Cần: Dev cho biết hành vi này đã live trước TIB-5488 chưa; operator chọn giữ PROPOSED tới khi TIB-5488 Done, hay gửi CCR sau khai SHIPPED (nguồn change note dev chỉ cho OBSERVED_CURRENT; muốn làm expected cần Dev xác nhận trực tiếp hoặc test case PASS có build). Khi ship, QA chạy lại TC-27 cả dòng artwork activate từ PSD, ghi build. CHK-006 chưa có oracle.","supersedes":"OQ-artwork-525"}
```

## OQ-mcp-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-026","type":"NEEDS_CONFIRMATION","feature_id":"mcp-artwork-tools","kb_ids":["KB-1054","KB-1055"],"check_ids":["CHK-007"],"summary":"[CBS-122] KB-1054 (OBSERVED_CURRENT, change note Dev TIB-5572 2026-10-15): update/validate tool của MCP từ chối artwork 1.0, message trỏ tới bulk-convert-artworks-tool. KB-1055 (PROPOSED, rule QA FACT-176): mã lỗi là artwork.schema_version.not_2, tool chỉ đọc được 1.0, message gợi ý cả convert tay trong portal. Mã lỗi và nội dung message có đúng không, và có phải hành vi mong muốn không? CHK-007 chỉ có oracle BASELINE theo KB-1054. Cần: Dev xác nhận; QA chạy CHK-007 trên build có TIB-5572, ghi build.","supersedes":"OQ-artwork-526"}
```

## OQ-mcp-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-027","type":"NEEDS_CONFIRMATION","feature_id":"mcp-artwork-tools","kb_ids":["KB-1079"],"check_ids":["CHK-008"],"owner":"Dev","summary":"[CBS-108] Rule QA FACT-182 (KB-1079, PROPOSED): khi dựng fixture Artwork 1.0 cho test convert, sửa field qua API (vd đổi font của layer linked có nguồn là layer date) có tự đổi customization_type của layer từ linked sang no_customization trên server không, và đó có phải cơ chế chủ ý? Change note Dev TIB-5572 (2026-10-15) không nói side-effect này, mà nói converter map layer linked khác design nguồn thành populate layer và đưa layer linked có nguồn date input vào has-dropped-layers. Lượt API của QA-3409 TC-66 ra would-convert là do customization_type đã bị đổi, hay do layer đã khác design nguồn sau khi đổi font nên được map sang populate? Layer linked có nguồn date input nhưng khác design nguồn thì dry_run phải chặn hay cho convert? Nếu side-effect là có thật trên artwork của merchant (mất link khi sửa font qua API) thì cần đánh giá lại như hành vi P1 và gửi bằng test case Testlane. CHK-008 chưa có oracle. Cần: Dev xác nhận; QA chạy CHK-008 trên build có TIB-5572, ghi build.","supersedes":"OQ-artwork-546"}
```

## OQ-mcp-028 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-028","type":"NEEDS_CONFIRMATION","feature_id":"mcp-artwork-tools","kb_ids":["KB-1100"],"check_ids":["CHK-011"],"owner":"Dev","summary":"[CBS-149] MCP update-artwork-layer-tool patch cặp stroke_color / stroke_width mới cho layer curve text thì get-artwork-tool trả cặp mới, không có stroke_layers, và file design + preview storefront vẽ theo cặp mới — có phải expected không? KB-1100 là quan sát test case TC-TIB-8989 (staging 2026-11-10, production phần máy 2026-11-11, không ghi build; design lấy qua order vì generate-test-design-tool không dùng được trên dev store); CCR chỉ nêu tên căn cứ expected (QA plan 56595 bước E9). CHK-011 oracle BASELINE.","supersedes":"OQ-artwork-565"}
```

## OQ-mcp-029 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-mcp-029","type":"NEEDS_CONFIRMATION","feature_id":"mcp-artwork-tools","kb_ids":["KB-1099"],"check_ids":[],"owner":"Dev","summary":"[CBS-149] MCP write guard không cảnh báo field bị mất khi stroke_layers bị bỏ trên curve / spiral / shape / warp text (Dev mô tả ở TIB-5699 comment 56557, U13, ghi \"Not for QA\") — response của write tool đúng là không có warning layer.fields.lost cho 4 loại, còn Text vẫn có? QA chưa verify, không nạp KB.","supersedes":"OQ-artwork-566"}
```

## OQ-mcp-030 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-mcp-030", "type": "NEEDS_CONFIRMATION", "feature_id": "mcp-client-connection", "kb_ids": ["KB-1659"], "check_ids": ["CHK-022"], "owner": "Dev", "summary": "[CBS-163] Tạo token ở /api-keys và Regenerate ở /mcp: POST /api/tokens 200, không key token, plain token hiện một lần (reload không còn), Regenerate xoá token MCP cũ bằng DELETE /api/tokens/{id} 204 (KB-1659, quan sát TC-TIB-8587 không ghi build) — Dev xác nhận là expected? Liên quan OQ-mcp-007 (nút Generate chưa bấm ở bootstrap, KB-1603/KB-1610)."}
```
