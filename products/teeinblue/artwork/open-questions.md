# Open Questions — Artwork

## OQ-artwork-005 — CONFLICT

```json
{"oq_id":"OQ-artwork-005","type":"CONFLICT","feature_id":"artwork-save-persist","summary":"Whether a published OpenAPI spec for the Artwork API actually exists on staging is unconfirmed; 9 candidate paths all returned 404.","side_a":"Project configuration assumes an OpenAPI spec is published at a known base path on staging.","side_b":"All 9 standard candidate paths tried (the configured base path plus common variants like /docs, /swagger.json) returned an HTML 404 page, not a JSON spec."}
```

## OQ-artwork-007 — CONFLICT

```json
{"oq_id":"OQ-artwork-007","type":"CONFLICT","feature_id":"artwork-save-persist","summary":"Unclear whether artwork re-read after save goes through a dedicated GraphQL query, or is simply the client re-using the PUT response body labeled as 'GraphQL' by convention.","side_a":"Portal observation notes label the read-back surface for several observations as 'GraphQL artworks.templates', implying a separate read query runs after save.","side_b":"The two network captures available for those exact same observations contain only the validate-default-value POST and the PUT — no GraphQL request at all; the PUT response body alone already contains the full dependency/retrieval_* shape being described."}
```

## OQ-artwork-013 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-013","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","summary":"Chưa có evidence trực tiếp quan sát hành vi Cancel trên dialog này (chỉ có evidence cho việc dialog xuất hiện, không có evidence cho luồng Cancel). Đây là suy luận hợp lý theo UX convention, KHÔNG phải xác nhận — cần chạy thử để lấy oracle thật trước khi coi là expected chính thức."}
```

## OQ-artwork-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-014","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","summary":"unknown_areas của feature profile: kết quả thực sự của 'Mark as archive' sau khi click chưa từng được quan sát trong KB gốc — cần chạy 1 lần và ghi lại trước/sau trạng thái để có oracle."}
```

## OQ-artwork-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-015","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","summary":"unknown_areas của feature profile: chưa quan sát luồng dịch thuật artwork hoạt động thế nào — cần khám phá riêng."}
```

## OQ-artwork-016 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-016","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","kb_ids":["KB-1031"],"summary":"Chưa xác nhận đây là soft hay hard delete — ảnh hưởng trực tiếp policy mutation an toàn khi test. Cần dev/PO xác nhận trước khi chạy case này trên bất kỳ artwork nào ngoài artwork test chuyên dụng. [Cập nhật CBS-107, 2026-11-12] Phần soft/hard đã có nguồn: spec-hub rule artwork-editor-delete-to-trash (sure green) nói xoá artwork chuyển vào trash, không xoá hẳn (KB-1031). Còn mở: cơ chế đó có phải cột deleted_at trên bảng artworks không (QA quan sát GraphQL vẫn trả row đã xoá nếu query không lọc deleted_at:{_is_null:true}), và artwork có bị xoá hẳn khỏi DB sau 365 ngày như spec-hub rule trash-permanent-cleanup (feature trash) nói không. Cần: Dev xác nhận."}
```

## OQ-artwork-017 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-017","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","summary":"coverage_gaps #3 của KB gốc: cả 3 run chỉgi test đúng 1 role (owner) trên 1 tenant. Hoàn toàn chưa có evidence permission/cross-tenant cho feature này."}
```

## OQ-artwork-018 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-018","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"coverage_gaps #5 của KB gốc: 2 lần 'thất bại' quan sát được trong 3 run đều do client chặn trước khi gửi request (circular dependency), KHÔNG phải server reject thật. Chưa có sample lỗi server thật nào — cần dev/PO cho biết điều kiện nào khiến endpoint này trả lỗi để dựng test case."}
```

## OQ-artwork-019 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-019","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"KB-021 flag đây là unknown — chưa rõ 2 field này bị loại khỏi serialization đọc lại hay lưu ở chỗ khác."}
```

## OQ-artwork-020 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-020","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"CONF-007 UNRESOLVED: 1 phía nói có GraphQL riêng (dựa trên nhãn surface=GraphQL trong evidence capture), phía kia nói 2 network capture cho đúng các ACT-ID liên quan chỉ có validate-default-value + PUT, KHÔNG có POST /v1/graphql nào. Cần capture network đầy đủ (không lọc bớt) ở bước mở lại editor để phân xử."}
```

## OQ-artwork-021 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-021","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"CONF-005 UNRESOLVED:.env/brief giả định có OpenAPI spec, nhưng 9 path thử đều 404 dạng HTML. Cho tới khi xác nhận, KHÔNG coi bảng field trong KB-020/021/022 là contract chính thức — mọi check field-shape ở checklist này chỉ ở mức BASELINE (quan sát), không phải STRONG (spec-confirmed)."}
```

## OQ-artwork-022 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-022","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"coverage_gaps #3 của KB gốc: chỉ 1 role 1 tenant được test trong cả 3 run nguồn. Hoàn toàn chưa có evidence permission cho toàn bộ luồng save/persist."}
```

## OQ-artwork-023 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-023","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"Chưa từng quan sát artwork có ≥2 template trong evidence nguồn (artwork test chỉ có 1 template) — hành vi nút này ở trạng thái enable hoàn toàn chưa biết."}
```

## OQ-artwork-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-024","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"unknown_areas: kết quả sau khi 'Convert to Global Template' hoàn tất chưa từng được quan sát — không biết global template có scope/state khác gì template thường."}
```

## OQ-artwork-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-025","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"Chưa đối chiếu được UI field 'Extra charge for this template' với field API thực tế (KB-020 chỉ ghi nhận addons:[] và charge_enabled ở mức observed_count=1, chưa gắn với action cụ thể bật field này)."}
```

## OQ-artwork-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-026","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"profile_relationships đánh dấu quan hệ này là INFERRED, chưa xác nhận — 'Import from artwork' có thể liên quan tới danh sách /artworks nhưng chưa có evidence trực tiếp."}
```

## OQ-artwork-095 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-095","type":"OPEN_ISSUE","feature_id":"artwork-save-persist","summary":"3 of 4 successful PUT saves observed across the source runs only captured method/status (no full request+response body) — most field-level PUT behavior beyond the one fully-captured sample is unverified."}
```

## OQ-artwork-096 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-096","type":"OPEN_ISSUE","feature_id":"object-wide","summary":"No direct database (Postgres) access has been used for any Artwork observation to date — every 'data' claim in this object is inferred from Hasura GraphQL responses or PUT response echoes, never verified against the actual DB schema/rows."}
```

## OQ-artwork-097 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-097","type":"OPEN_ISSUE","feature_id":"object-wide","summary":"Every JSON field key attributed to a layer type via bundle-registry (code) across all layer-config-* features is INFERRED, not cross-checked directly against a live API/DB field for that specific type — treat as non-authoritative until confirmed."}
```

## OQ-artwork-098 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-098","type":"OPEN_ISSUE","feature_id":"object-wide","summary":"Storefront (buyer-facing) rendering has zero evidence for the large majority of layer types/features in this object (only Clipart Category and parts of Multiple Uploads/Text to Image/Photo Upload have any storefront evidence) — most storefront behavior for Artwork is completely unexplored."}
```

## OQ-artwork-099 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-099","type":"OPEN_ISSUE","feature_id":"object-wide","summary":"Every run to date tested exactly one role (store owner/staff, account explorer (TIB_STAGING_EMAIL)) on one tenant/organization — no permission or cross-tenant behavior has been verified for any Artwork feature."}
```

## OQ-artwork-114 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-114","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Vì sao PUT /api/artworks/5187 trả 500 'Server Error' kể cả khi Save không đổi gì trên bản copy Artwork 1.0 chưa có version đã lưu — lỗi dữ liệu của bản copy, lỗi sản phẩm với artwork Artwork 1.0 chưa có version, hay liên quan TIB-5580? Quyết định đây là bug sản phẩm cần check hồi quy hay chỉ là fixture hỏng; cần log server để phân biệt.","kb_ids":["KB-145"]}
```

## OQ-artwork-115 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-115","type":"OPEN_ISSUE","feature_id":"artwork-save-persist","summary":"Các artwork Artwork 1.0 khác (không phải bản copy #5187, kể cả artwork gốc #2164 hoặc artwork 1.0 đã có version lưu) có Save được không? Cần một artwork Artwork 1.0 Save được làm fixture để chạy lại check Paragraph Artwork 1.0; hiện chưa biết phạm vi của lỗi 500.","kb_ids":["KB-145"]}
```

## OQ-artwork-116 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-116","type":"OPEN_ISSUE","feature_id":"artwork-save-persist","summary":"Khi PUT /api/artworks/{id} trả 500, Artwork Editor hiển thị gì cho người dùng (toast/thông báo lỗi, giữ thay đổi chưa lưu hay không)? KB-145 chỉ ghi artwork không Save được, không ghi phản hồi UI; check negative cho lỗi server khi Save chưa có oracle.","kb_ids":["KB-145"]}
```

## OQ-artwork-149 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-149","type":"OPEN_ISSUE","feature_id":"artwork-template-management","summary":"Q9 (treo): linked template đã có cờ visible cụ thể (true/false) rồi global template đổi — linked đổi theo hay giữ riêng? KB-176/177 chỉ phủ null-kế thừa và bật lại ở linked; không suy ra trường hợp này.","kb_ids":["KB-176","KB-177"]}
```

## OQ-artwork-150 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-150","type":"OPEN_ISSUE","feature_id":"psd-import","summary":"Artwork import từ PSD có folder ẩn: storefront (form/preview) và print file chưa được kiểm (TC-TIB-6078 chỉ kiểm layer panel, canvas và response API). Liên quan OQ-artwork-120 (import PSD với paragraph nhiều lớp stroke).","kb_ids":["KB-178"]}
```

## OQ-artwork-151 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-151","type":"OPEN_ISSUE","feature_id":"psd-import","summary":"Các phần khác của luồng PSD import (Multiple template, folder lồng nhiều cấp, mapping loại layer, file lỗi) hoạt động thế nào?","kb_ids":["KB-178"]}
```

## OQ-artwork-160 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-160","type":"OPEN_ISSUE","feature_id":"artwork-list-and-clone","summary":"Khi duplicate artwork có điều kiện, element trong dependencies của bản copy có được map sang layer id của chính bản copy (không trỏ về layer của artwork gốc) không? Test case duplicate không ghi tường minh việc map element.","kb_ids":["KB-229"]}
```

## OQ-artwork-331 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-331","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","kb_ids":["KB-970"],"summary":"KB-970: hai tab cùng sửa một layer thì lần save sau ghi đè cả layer, thay đổi của tab kia mất, không cảnh báo (QA-3435 TC-34, một lượt, TC chỉ ghi nhận). Last-save-wins cho cả layer có phải hành vi mong muốn không, có cần cảnh báo xung đột không? Có áp cho loại layer khác ngoài field AI provider không? Thêm (diff): mất dữ liệu chỉ giới hạn ở layer hai tab cùng sửa, hay lần Save sau ghi đè cả artwork (KB-052: PUT ghi toàn bộ artwork)?"}
```

## OQ-artwork-332 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-332","type":"OPEN_ISSUE","feature_id":"artwork-save-persist","kb_ids":["KB-971"],"summary":"KB-971 (known defect): PUT /api/artworks/{id} tự dựng vẫn lưu thay đổi trên layer locked: true (200), quan sát 2026-10-23 và 2026-10-30. Server có nên từ chối thay đổi trên layer locked không? Chưa có bug chính thức (chỉ draft)."}
```

## OQ-artwork-333 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-333","type":"OPEN_ISSUE","feature_id":"artwork-save-persist","kb_ids":["KB-972"],"summary":"KB-972 (known defect): Option title chứa ký tự NUL làm request lưu artwork trả 500, dữ liệu không đổi (build 2026-10-23). Bug NUL có sẵn đã sửa chưa, và hành vi mong muốn là từ chối có thông báo hay loại bỏ ký tự?"}
```

## OQ-artwork-334 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-334","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","kb_ids":["KB-973"],"summary":"KB-973: thứ tự field sau khi thả ở tab Re-order giữ nguyên sau Save và mở lại editor, khớp GraphQL (QA-3352 TC-08, AI, một lượt, không ghi build). Cần xác nhận đây là hành vi mong muốn."}
```

## OQ-artwork-335 — CONFLICT

```json
{"oq_id":"OQ-artwork-335","type":"CONFLICT","feature_id":"artwork-save-persist","kb_ids":["KB-053","KB-974"],"summary":"Nghĩa của templates[].positions: thứ tự render của layer (KB-053) hay thứ tự field của tab Re-order trong Form panel (KB-974)? Nếu là thứ tự form thì reorder ở tab Re-order có đổi thứ tự render không, và thứ tự render nằm ở đâu (templates[].layers?). Thêm (diff): reorder ở tab Re-order có đổi thứ tự render / order design không?","side_a":"KB-053 (bootstrap 2026-09-10, một sample PUT full body): positions là mảng layer id theo thứ tự render.","side_b":"KB-974 (ghi chú QA khi duyệt spec QA-3352 TC-03, 2026-09-28, không assert): thứ tự field của tab Re-order đọc lại ở positions, templates[].layers không đổi thứ tự khi reorder."}
```

## OQ-artwork-348 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-348","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-004 “Click 'Cancel' trên dialog xoá artwork không thực hiện xoá” của feature artwork-list-management. missing_or_unresolved_oracle"}
```

## OQ-artwork-349 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-349","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-005 “Kết quả sau khi click 'Mark as archive'” của feature artwork-list-management. missing_or_unresolved_oracle"}
```

## OQ-artwork-350 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-350","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006 “Kết quả sau khi click 'Import to Translation'” của feature artwork-list-management. missing_or_unresolved_oracle"}
```

## OQ-artwork-351 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-351","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “Delete artwork — soft-delete hay hard-delete, có khôi phục được không” của feature artwork-list-management. missing_or_unresolved_oracle"}
```

## OQ-artwork-352 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-352","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Truy cập /artworks và các action list với role/tenant khác” của feature artwork-list-management. missing_or_unresolved_oracle"}
```

## OQ-artwork-353 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-353","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “GET /api/artworks/{id} trả 405 Method Not Allowed” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

## OQ-artwork-354 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-354","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011 “validate-default-value trả lỗi 4xx/5xx thật từ server” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

## OQ-artwork-355 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-355","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-013 “2 field artwork_category_id/global_option_ids có thực sự persist ở nơi khác không” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

## OQ-artwork-356 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-356","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-015 “Đọc lại artwork sau save — GraphQL riêng hay chỉ từ response PUT (CONF-007)” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

## OQ-artwork-357 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-357","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-016 “Xác nhận OpenAPI spec cho Artwork API có tồn tại trên staging hay không (CONF-005)” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

## OQ-artwork-358 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-358","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-017 “Save/đọc artwork với role khác owner / cross-tenant (TIB_USER_B)” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

## OQ-artwork-359 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-359","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Hành vi btn-set-invisible khi artwork có ≥2 template” của feature artwork-template-management. missing_or_unresolved_oracle"}
```

## OQ-artwork-360 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-360","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-009 “Kết quả sau khi 'Convert to Global Template'” của feature artwork-template-management. missing_or_unresolved_oracle"}
```

## OQ-artwork-361 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-361","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-010 “Field 'Extra charge for this template' map tới field nào trong PUT body” của feature artwork-template-management. missing_or_unresolved_oracle"}
```

## OQ-artwork-362 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-362","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011 “'Import from artwork' lấy nguồn từ danh sách /artworks” của feature artwork-template-management. missing_or_unresolved_oracle"}
```

## OQ-artwork-454 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-454","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"[CBS-109, KB-986, rule QA FACT-179] Rule QA ghi format file order design (AI, EPS, PDF, SVG, PNG, JPEG…) do field 'Artwork design format' (multi-select) trong dialog 'Artwork details' của artwork quyết định, Save cùng artwork, và artwork editor không có nút Export/Download design riêng. Chưa có order thật đối chiếu (QA-3416 TC-29 tạm hoãn). Dev xác nhận: (1) đây có phải nơi duy nhất chọn format file design không; (2) khi chọn nhiều format thì một line item sinh file design cho mọi format đã chọn hay chỉ một; (3) lựa chọn multi-select lưu vào field nào và dạng gì, vì KB-053 mới thấy design_format là một chuỗi 'rgb' trong body PUT. Liên quan CHK-026.","kb_ids":["KB-986","KB-053"],"owner":"Dev"}
```

## OQ-artwork-494 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-494","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","kb_ids":["KB-1017"],"summary":"[CBS-143] KB-1017: Artwork editor chặn Save / Save & Close khi có layer static-photo không ảnh hoặc photo / clipart-category / group-clipart-categories No personalization không ảnh, toast nêu template + layer — PO/Dev xác nhận đây là hành vi mong muốn và cho biết đã lên production chưa. Thêm: layer photo No personalization không có ảnh mặc định nhưng có retrieval value (KB-937, KB-938) có bị chặn không? Nguồn hiện tại là change note của Dev (TIB-5446, 2026-11-06)."}
```

## OQ-artwork-495 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-495","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","kb_ids":["KB-1018"],"summary":"[CBS-143] KB-1018: ảnh vừa chọn nhưng chưa upload vẫn tính là có ảnh khi Save — trạng thái này xảy ra ở đường thao tác nào trên portal (hộp chọn ảnh upload xong mới cho Select)? Dev/PO xác nhận."}
```

## OQ-artwork-496 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-496","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","kb_ids":["KB-1019"],"summary":"[CBS-143] KB-1019: REST lưu artwork (tạo mới / cập nhật) trả 422 khi có layer ảnh không có ảnh — route tạo mới là gì, body lỗi 422 có shape nào (tên template, tên layer ở field nào)? Chưa quan sát; cần lượt test được phép gọi route ghi."}
```

## OQ-artwork-497 — CONFLICT

```json
{"oq_id":"OQ-artwork-497","type":"CONFLICT","feature_id":"artwork-save-persist","kb_ids":["KB-1020"],"summary":"[CBS-143] KB-1020: kiểm tra 'layer ảnh phải có ảnh' bỏ qua layer linked theo trường nào, và 'replica' là loại layer nào? Item không khẳng định trường hợp layer linked đã convert sang Static Image. Không có conflict_group (căng nằm trong claim, không với item base).","side_a":"Change note Dev TIB-5446 (2026-11-06, mục API): bỏ qua layer replica, linked, global option, layer ẩn và form-only vì chúng lấy ảnh nơi khác hoặc không render.","side_b":"Lượt test portal staging 2026-11-09: một layer linked sau khi convert sang Static Image (customization_type no_customization, vẫn giữ trường linked) bị chặn như layer thường; layer replica chưa kiểm vì chưa có định nghĩa."}
```

## OQ-artwork-498 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-498","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","kb_ids":["KB-1021"],"summary":"[CBS-143] KB-1021: artwork đã hỏng sẵn (layer ảnh không url) không Save được tới khi thêm ảnh hoặc xoá layer, không backfill — PO xác nhận chấp nhận hành vi này (seller không lưu được thay đổi khác trên artwork cũ) và có kế hoạch backfill riêng không? Chưa có lượt test."}
```

## OQ-artwork-506 — CONFLICT

```json
{"oq_id":"OQ-artwork-506","type":"CONFLICT","feature_id":"artwork-list-and-clone","kb_ids":["KB-1028"],"summary":"[CBS-107] Gọi thẳng DELETE /api/artworks/{id} cho artwork đang gắn campaign thì response đúng thiết kế là gì (status code, body JSON có nêu lý do không), và trang HTML 'Forbidden' 403 của Laravel mà QA đo được có phải lỗi không? Hai phía chưa ai phân xử; check tầng API CHK-015 chưa có oracle, check tầng portal CHK-013 dùng KB-1028. Cần: Dev trả lời.","side_a":"spec-hub rule artwork-editor-delete-blocked-when-used (sure green, đọc 2026-11-12, KB-1028): lỗi khi xoá artwork đang dùng nêu lý do; với artwork trong campaign, portal yêu cầu gỡ khỏi mọi campaign trước và có 'View campaigns list'.","side_b":"QA đo bằng API trên staging 2026-09-07 (rule QA FACT-049, chưa nạp vì xoá dữ liệu là P1): artwork có liên kết campaign nhận 403 với trang HTML 'Forbidden' trần của Laravel, không phải JSON; artwork không liên kết xoá được (204)."}
```

## OQ-artwork-507 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-507","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","kb_ids":["KB-1029","KB-1030"],"summary":"[CBS-107] (1) Ngưỡng 60 lần/phút cho lưu thay đổi artwork có sẵn (KB-1029) là setting server: staging và production có cùng giá trị không? (2) Khi vượt rate limit, response là 429 'Too Many Requests' dạng trang HTML (rule QA FACT-050, KB-1030, PROPOSED) có phải thiết kế không, hay phải là JSON? CHK-033 và CHK-034 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-508 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-508","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","kb_ids":["KB-1028","KB-1031"],"summary":"[CBS-107] Thao tác xoá là P1 (mất dữ liệu). KB-1028 và KB-1031 là rule spec-hub đọc từ code (sure green): artwork đang dùng (campaign, platform product, order design, có duplicate) không xoá được, artwork đã dùng cho order design chỉ archive được; xoá artwork chuyển vào trash. Đây có phải hành vi chủ đích không? CHK-013, CHK-014, CHK-016 đang dùng hai item này làm oracle STRONG. Cần: PO xác nhận."}
```

## OQ-artwork-547 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-547","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","kb_ids":["KB-1080"],"check_ids":["CHK-016"],"owner":"Dev","summary":"[CBS-111] Rule QA FACT-010 (KB-1080, PROPOSED; rule QA không có ngày cụ thể, có trước 2026-09-11, ngày ghi nhận lấy theo ngày gửi Proposal 2026-11-10): ở template không phải global của artwork có Global Template, layer đồng bộ chỉ khoá font family, còn màu chữ, font size min/max, drop shadow, background, Transform, Align sửa được, và các panel settings không mở được. Có đúng và còn hiện hành không? 'Panel settings không mở được' là những panel nào? spec-hub không có rule về việc này. CHK-016 chưa có oracle. Cần: Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày chạy, build, căn cứ expected."}
```

## OQ-artwork-548 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-548","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","kb_ids":["KB-1081"],"check_ids":["CHK-017"],"owner":"Dev","summary":"[CBS-111] Rule QA FACT-016 (KB-1081, PROPOSED; ngày ghi nhận lấy theo ngày gửi Proposal 2026-11-10): Global Template chỉ global trong một artwork (đồng bộ giữa các template của artwork đó), không dùng chung giữa các artwork. Có đúng không? Mô tả dữ liệu 'Templates' của feature artwork-editor trên spec-hub (không phải rule) chỉ nói layer của template global lặp lại ở mọi template khác và giữ đồng bộ, không nói giữa các artwork. Phủ một phần OQ-artwork-024 / OQ-artwork-360 (CHK-009, kết quả sau Convert to Global Template), các OQ đó giữ mở. CHK-017 chưa có oracle. Cần: Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày chạy, build, căn cứ expected."}
```

## OQ-artwork-549 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-549","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","kb_ids":["KB-1085"],"check_ids":["CHK-022"],"owner":"Dev","summary":"[CBS-157] Sau admin import artwork sang account khác, design preview của từng template của artwork bên đích phải render xong và giống template tương ứng của nguồn (ảnh clipart và static photo lấy từ clipart hiện đủ, không vùng trống) có phải hành vi đúng không? KB-1085 chỉ là quan sát một lần (test case TC-TIB-8113, staging 2026-11-04, không ghi build); expected do QA chốt, comment Dev TIB-5619 không nói về design preview. CHK-005 oracle BASELINE. Cần: Dev xác nhận, hoặc test case Testlane PASS có build và căn cứ expected."}
```

## OQ-artwork-550 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-550","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","kb_ids":["KB-1086"],"check_ids":[],"owner":"Dev","summary":"[CBS-157] Khác biệt môi trường (ALTERNATIVE_SETUP, ghi nhận QA 2026-11-03, KB-1086 INFERRED): trên staging QA không duplicate được campaign sang store của account khác từ portal (clone campaign Product Base không chọn store; clone platform product chỉ chọn instance cùng account), nên test bằng import TIB Library hoặc admin import. Đúng không, có đường nào khác trên staging, và trên production duplicate campaign sang store khác chạy thế nào? Cần: Dev xác nhận."}
```

## OQ-artwork-551 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-551","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","kb_ids":["KB-1082"],"check_ids":["CHK-018","CHK-019"],"owner":"Dev","summary":"[CBS-157] Remap ảnh gốc khi copy artwork sang account khác (KB-1082) có áp cho layer Group of clipart categories, Vector Category và artwork 1.0 không? Comment Dev TIB-5619 (2026-10-29) nói áp cho cả artwork 1.0 và 2.0, nhưng test case chỉ phủ layer Clipart Category tự giữ category trên artwork 2.0 (các case 1.0, Group of clipart categories, Vector Category bị skip). Cần: test case Testlane PASS cho các loại layer này, hoặc Dev xác nhận phạm vi."}
```

## OQ-artwork-552 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-552","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","kb_ids":[],"check_ids":[],"owner":"Dev","summary":"[CBS-157] Layer lấy category từ Global Option (layer không tự giữ category, clipart của layer null ở nguồn) khi artwork được import qua TIB Library sang account khác: ảnh gốc có được remap sang category của bên đích không? QA ghi nhận ngoài claim trên staging 2026-11-04: url vẫn giữ id category nguồn (file trả 403), layer trong suốt trên canvas. Chưa có kết luận Dev/PO, không nạp KB, không có expected. Cần: Dev/PO xác nhận hành vi đúng, hoặc mở bug."}
```

## OQ-artwork-553 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-553","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","kb_ids":[],"check_ids":[],"owner":"Dev","summary":"[CBS-157] Khi copy ảnh clipart dùng làm Static photo sang bên đích (KB-1083), QA ghi nhận ngoài claim (staging 2026-11-04): chỉ file _large được copy, file _thumbnail ở đường dẫn đích trả 403 nên dòng layer ở layer list hiện icon chung; QA coi là lỗi nhỏ không chặn. Đây là lỗi hay chủ ý? Chưa có kết luận Dev, không nạp KB. Cần: Dev xác nhận."}
```

## OQ-artwork-554 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-554","type":"NEEDS_CONFIRMATION","feature_id":"artwork-live-preview-asset-load","kb_ids":["KB-1088"],"check_ids":["CHK-003"],"owner":"Dev","summary":"[CBS-150] Trong Live preview, background clipart cùng kích thước printarea phải được vẽ phủ kín printarea có phải hành vi đúng không? KB-1088 chỉ là quan sát (test case TC-TIB-8991, TC-TIB-8994, staging 2026-11-10, không ghi build); CCR nói căn cứ là phần Expectation của ticket TIB-5685 nhưng không trích nguyên văn. Triệu chứng gốc (background co lại vì CDN còn giữ bản ảnh cũ ở ?v=1) không tái hiện được trên staging. CHK-003 oracle BASELINE. Cần: Dev xác nhận kèm trích nguyên văn, hoặc test case Testlane PASS có build và căn cứ expected."}
```

## OQ-artwork-555 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-555","type":"NEEDS_CONFIRMATION","feature_id":"artwork-live-preview-asset-load","kb_ids":["KB-1089"],"check_ids":["CHK-004"],"owner":"Dev","summary":"[CBS-150] Đổi lựa chọn clipart nhiều lần trong Live preview: mỗi URL ảnh large có đúng một tham số ?v=<version của category> (không lặp ?v=…?v= hay &v=), canvas hiện đúng clipart vừa chọn — có phải expected không? KB-1089 là quan sát test case TC-TIB-8992 (staging 2026-11-10, production 2026-11-11, không ghi build); CCR chỉ nêu tên căn cứ expected (gợi ý test của Dev trên TIB-5685), không trích nguyên văn. CHK-004 oracle BASELINE. Cần: CCR gửi lại kèm trích nguyên văn gợi ý test của Dev, hoặc test case có build."}
```

## OQ-artwork-556 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-556","type":"OPEN_ISSUE","feature_id":"artwork-live-preview-asset-load","kb_ids":["KB-1091"],"check_ids":["CHK-006"],"owner":"Dev","summary":"[CBS-150] Known defect ở SDK (ngoài phạm vi TIB-5685, Dev xác nhận ở comment 56822, 2026-11-10): layer Group of clipart categories không có grouped setting / grouped reposition thì ảnh large cuối cùng trên canvas (Live preview, và theo Dev cả storefront) tải với ?v=1 do transformer group clipart của SDK; lỗi có từ 03/2025. Có ticket sửa chưa, kế hoạch thế nào? CHK-006 là watch, không có expected. QA chưa quan sát phía storefront."}
```

## OQ-artwork-557 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-557","type":"NEEDS_CONFIRMATION","feature_id":"artwork-live-preview-asset-load","kb_ids":[],"check_ids":[],"owner":"Dev","summary":"[CBS-150] Ngoài claim (ghi trong actual result của TC-TIB-8994, staging 2026-11-10): preview của trang Campaign editor (không phải Live preview) tải ảnh large của layer có clipart category v null với query ?v=null (chuỗi \"null\"); ảnh vẫn hiển thị. Đây là lỗi hay chấp nhận được (so với Live preview dùng ?v=1, KB-1092)? Chưa có kết luận Dev, không nạp KB."}
```

## OQ-artwork-558 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-558","type":"NEEDS_CONFIRMATION","feature_id":"artwork-live-preview-asset-load","kb_ids":[],"check_ids":[],"owner":"Dev","summary":"[CBS-150] Ngoài claim (ghi trong actual result của TC-TIB-8997, staging 2026-11-10): dropdown chọn sub-category của layer Group of clipart categories hiện thumbnail sub-category với đường dẫn ảnh dạng <cdn>/null?v=<v> (category không có thumbnail), ảnh lỗi tải, ô trống. Đây là lỗi hay chủ ý? Chưa có kết luận Dev, không nạp KB."}
```

## OQ-artwork-576 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-576","type":"NEEDS_CONFIRMATION","feature_id":"psd-import","summary":"[CBS-152, TIB-5709] Import PSD có layer 144 MP (KB-1114, quan sát TC-TIB-8788 build e96975614): toast \"Your artwork has been created\" và artwork lưu được qua PSD Single template và Group-to-template — expected? Bulk upload PSD (chỉ user beta) với layer > 128 MP chưa chạy; production chưa chạy; TIB-5718 (layer PSD portal lên queue) có đổi luồng này không?","kb_ids":["KB-1114"],"needs":"Dev xác nhận; QA cần account beta cho Bulk upload PSD và lượt production."}
```

## OQ-artwork-577 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-577","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-and-clone","kb_ids":["KB-1118"],"check_ids":[],"owner":"Dev","summary":"[CBS-163] Duplicate artwork 201 trả bản copy, archive 200 với status 1 (artwork vào tab Archived), unarchive 200 với status 0, response không relation, không user_id (KB-1118, một lượt staging, build không ghi): Dev xác nhận là expected? Câu trả lời cũng đóng được OQ-artwork-014 / OQ-artwork-349 (kết quả Mark as archive, CHK-005)."}
```

## OQ-artwork-578 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-578","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","kb_ids":["KB-1117"],"check_ids":["CHK-037"],"owner":"Dev","summary":"[CBS-163] Tạo artwork 201, lưu 200, khôi phục version 200 với data và schema_version, không relation, không user_id, editor hiện design của version đã khôi phục (KB-1117, một lượt staging, build không ghi): Dev xác nhận đây là expected? Production mới có một lượt cho thao tác lưu."}
```
