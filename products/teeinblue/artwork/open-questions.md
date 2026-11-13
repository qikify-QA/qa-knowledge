# Open Questions — Artwork

## OQ-artwork-001 — CONFLICT

```json
{"oq_id": "OQ-artwork-001", "type": "CONFLICT", "feature_id": "conditional-setting-config", "summary": "Evidence linking a toggle-source condition action to its network capture is unreliable, casting doubt on the API-level oracle for that specific observation (KB-066 area).", "side_a": "The recorded action ('choose Toggle as condition source, set value On') was linked to a specific network capture file as its evidence.", "side_b": "The actual content of that linked network capture file describes a completely different action (browsing 8 source options on a curve-text layer, then Cancel) and contains no PUT request at all — so the linkage was wrong or the two actions shared one capture window."}
```

## OQ-artwork-002 — CONFLICT

```json
{"oq_id": "OQ-artwork-002", "type": "CONFLICT", "feature_id": "layer-condition-value-binding", "summary": "Two observation passes on the same test artwork (4087) recorded different data state for addon-charge/json-list layers — most likely the fixture changed between passes, not a real product behavior conflict, but not confirmed.", "side_a": "First observation pass: layer addon-charge had no option values configured yet; layer json-list had no JSON URL configured yet.", "side_b": "Second observation pass (same artwork, later): addon-charge already had 2 options configured; json-list already had a source URL configured."}
```

## OQ-artwork-003 — CONFLICT

```json
{"oq_id": "OQ-artwork-003", "type": "CONFLICT", "feature_id": "layer-duplicate-link-copy", "summary": "An earlier assumption that linked-layer copies are marked with a chain icon on the layer row was checked directly and found false.", "side_a": "Assumption going into the run: a layer duplicated via 'Duplicate & Link options' shows a chain icon before its name on the layer row.", "side_b": "Direct observation across 35 layer types: the layer row icon set is always the same 5 fixed icons regardless of linked state; the only real signal that a layer is a linked copy is the config panel collapsing to just the LINKED LAYER + EXTRA accordions."}
```

## OQ-artwork-004 — CONFLICT

```json
{"oq_id": "OQ-artwork-004", "type": "CONFLICT", "feature_id": "layer-print-effects", "summary": "An assumption that Print Effects includes an emboss capability (gated by a 3rd-party service) could not be confirmed on the tested account/plan; absence was not proven either.", "side_a": "Assumption going into the run: Print Effects (formerly 'Shape Cut') now also includes an emboss effect that depends on a 3rd-party service.", "side_b": "Direct observation on 4 layer types plus the Extras > 3rd-party Services page: the Print Effects popover only ever shows shape-cut layout options; no mention of 'emboss' or '3rd-party' found anywhere on those surfaces."}
```

## OQ-artwork-005 — CONFLICT

```json
{"oq_id": "OQ-artwork-005", "type": "CONFLICT", "feature_id": "artwork-save-persist", "summary": "Whether a published OpenAPI spec for the Artwork API actually exists on staging is unconfirmed; 9 candidate paths all returned 404.", "side_a": "Project configuration assumes an OpenAPI spec is published at a known base path on staging.", "side_b": "All 9 standard candidate paths tried (the configured base path plus common variants like /docs, /swagger.json) returned an HTML 404 page, not a JSON spec."}
```

## OQ-artwork-006 — CONFLICT

```json
{"oq_id": "OQ-artwork-006", "type": "CONFLICT", "feature_id": "layer-common-config", "summary": "Two different-quality sources disagree on how many of the 35 layer types have a 'custom_class' field: code-derived list says 29, direct UI observation says 33.", "side_a": "Code-derived (bundle-registry, INFERRED): exactly 29 specific data-types carry a custom_class field.", "side_b": "Direct DOM observation across all 35 layer type config panels: the 'Custom class:' field renders on 33/35 types (absent only on Static Image and Static Vector)."}
```

## OQ-artwork-007 — CONFLICT

```json
{"oq_id": "OQ-artwork-007", "type": "CONFLICT", "feature_id": "artwork-save-persist", "summary": "Unclear whether artwork re-read after save goes through a dedicated GraphQL query, or is simply the client re-using the PUT response body labeled as 'GraphQL' by convention.", "side_a": "Portal observation notes label the read-back surface for several observations as 'GraphQL artworks.templates', implying a separate read query runs after save.", "side_b": "The two network captures available for those exact same observations contain only the validate-default-value POST and the PUT — no GraphQL request at all; the PUT response body alone already contains the full dependency/retrieval_* shape being described."}
```

## OQ-artwork-008 — CONFLICT

```json
{"oq_id": "OQ-artwork-008", "type": "CONFLICT", "feature_id": "layer-config-image", "summary": "Whether the layer-level 'Custom class' field exists on the Clipart Category (single) sub-type is disputed: the canonical 33/35 boundary says yes, a later deep-dive found no trace of it.", "side_a": "Canonical boundary knowledge (KB-011): 'Custom class' is present on 33/35 layer types, with only Static Image and Static Vector as named exceptions — implying Clipart Category (single) has it.", "side_b": "A later deep-dive on Clipart Category (single), scrolling the full Bulk Edit dialog (Design/Personalization/Extra) and checking the layer's API response directly, found no 'Custom class' field and no custom_class key anywhere."}
```

## OQ-artwork-009 — CONFLICT

```json
{"oq_id": "OQ-artwork-009", "type": "CONFLICT", "feature_id": "clipart-category-storefront-behavior", "summary": "Three-way disagreement on what actually drives the final rendered image for a Clipart Category layer: portal canvas, storefront pre-check, and the final compositing output each point to a different (or no) source.", "side_a": "In the portal editor, layer.url (set when picking an image via the 'Upload an image' tab at add-layer time) drives what renders on the canvas, both immediately and after Save & Close + reopen.", "side_b": "On the storefront personalization form, layer.default_value (set via the category default-value picker) is what gets pre-checked in the buyer-facing radiogroup on first load — layer.url is not even a selectable option there.", "side_c": "Neither layer.url, nor layer.default_value, nor the buyer's own explicit selection ever appears in the final compositing output (Preview modal or cart customization image) — see KB-112 (CRITICAL)."}
```

## OQ-artwork-010 — CONFLICT

```json
{"oq_id": "OQ-artwork-010", "type": "CONFLICT", "feature_id": "clipart-category-storefront-behavior", "summary": "Two API surfaces disagree on the clipart category list for the same user/session: REST returns an empty list, GraphQL returns 10 rows.", "side_a": "GET /api/layer-image-categories?type=clipart returns 200 with an empty array.", "side_b": "A GraphQL query for clipart_categories, run for the same user in the same time window, returns 200 with 10 rows."}
```

## OQ-artwork-011 — CONFLICT

```json
{"oq_id": "OQ-artwork-011", "type": "CONFLICT", "feature_id": "layer-config-image", "summary": "Text to Image (AI) personalization option count is disputed: canonical KB-019 says 2 choices (no 'No personalization'), a later re-observation (CCR CBS-003) found 3, corroborated by an independent observation on a different object (global-option).", "side_a": "Canon KB-019 (observed 2026-09-10): only 2 personalization choices exist for Text to Image (AI) — 'Create a new option' / 'Use an existing global option'. No 'No personalization' option.", "side_b": "Re-observation on 2026-09-25 (artwork 4416, layer 'hair'): all three choices are present — 'No personalization', 'Create a new option' (default), 'Use an existing global option'.", "side_c": "Corroborating, cross-object: an independent observation 10 days earlier on object global-option (CFL-01, artwork 4167) also saw all three choices; its escalation to the artwork object owner was never actioned before KB-019 was republished unchanged. No build/version/deploy-date is available to tell whether behavior genuinely changed or KB-019 was wrong from the start. KNOWN RISK: canonical checklist item CHK-007 for layer-config-image currently asserts '2 choices' with automation_suitability SUITABLE — any automation relying on it as an oracle should be audited."}
```

## OQ-artwork-012 — CONFLICT

```json
{"oq_id": "OQ-artwork-012", "type": "CONFLICT", "feature_id": "layer-config-vector", "summary": "x-ratelimit-remaining behavior for POST /api/layer-images/svg is inconsistent between two single-sample observations at different status codes; not enough evidence to state a rule.", "side_a": "Direct API test: 3 consecutive calls missing the required 'file' field (422 each time) — x-ratelimit-remaining stayed at 1000 (unchanged) across all 3 calls, while x-ratelimit-limit correctly showed 1000 each time.", "side_b": "UI-driven upload: 1 successful call (201) — x-ratelimit-remaining showed 999 (limit minus 1) on that request. Possibly the counter only increments on requests that pass validation, but with only 1 sample per side at different status codes, this is not confirmed as a rule."}
```

## OQ-artwork-013 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-013", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-list-management", "summary": "Chưa có evidence trực tiếp quan sát hành vi Cancel trên dialog này (chỉ có evidence cho việc dialog xuất hiện, không có evidence cho luồng Cancel). Đây là suy luận hợp lý theo UX convention, KHÔNG phải xác nhận — cần chạy thử để lấy oracle thật trước khi coi là expected chính thức."}
```

## OQ-artwork-014 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-014", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-list-management", "summary": "unknown_areas của feature profile: kết quả thực sự của 'Mark as archive' sau khi click chưa từng được quan sát trong KB gốc — cần chạy 1 lần và ghi lại trước/sau trạng thái để có oracle."}
```

## OQ-artwork-015 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-015", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-list-management", "summary": "unknown_areas của feature profile: chưa quan sát luồng dịch thuật artwork hoạt động thế nào — cần khám phá riêng."}
```

## OQ-artwork-016 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-016", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-list-management", "kb_ids": ["KB-1031"], "summary": "Chưa xác nhận đây là soft hay hard delete — ảnh hưởng trực tiếp policy mutation an toàn khi test. Cần dev/PO xác nhận trước khi chạy case này trên bất kỳ artwork nào ngoài artwork test chuyên dụng. [Cập nhật CBS-107, 2026-11-12] Phần soft/hard đã có nguồn: spec-hub rule artwork-editor-delete-to-trash (sure green) nói xoá artwork chuyển vào trash, không xoá hẳn (KB-1031). Còn mở: cơ chế đó có phải cột deleted_at trên bảng artworks không (QA quan sát GraphQL vẫn trả row đã xoá nếu query không lọc deleted_at:{_is_null:true}), và artwork có bị xoá hẳn khỏi DB sau 365 ngày như spec-hub rule trash-permanent-cleanup (feature trash) nói không. Cần: Dev xác nhận."}
```

## OQ-artwork-017 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-017", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-list-management", "summary": "coverage_gaps #3 của KB gốc: cả 3 run chỉgi test đúng 1 role (owner) trên 1 tenant. Hoàn toàn chưa có evidence permission/cross-tenant cho feature này."}
```

## OQ-artwork-018 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-018", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "summary": "coverage_gaps #5 của KB gốc: 2 lần 'thất bại' quan sát được trong 3 run đều do client chặn trước khi gửi request (circular dependency), KHÔNG phải server reject thật. Chưa có sample lỗi server thật nào — cần dev/PO cho biết điều kiện nào khiến endpoint này trả lỗi để dựng test case."}
```

## OQ-artwork-019 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-019", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "summary": "KB-021 flag đây là unknown — chưa rõ 2 field này bị loại khỏi serialization đọc lại hay lưu ở chỗ khác."}
```

## OQ-artwork-020 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-020", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "summary": "CONF-007 UNRESOLVED: 1 phía nói có GraphQL riêng (dựa trên nhãn surface=GraphQL trong evidence capture), phía kia nói 2 network capture cho đúng các ACT-ID liên quan chỉ có validate-default-value + PUT, KHÔNG có POST /v1/graphql nào. Cần capture network đầy đủ (không lọc bớt) ở bước mở lại editor để phân xử."}
```

## OQ-artwork-021 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-021", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "summary": "CONF-005 UNRESOLVED:.env/brief giả định có OpenAPI spec, nhưng 9 path thử đều 404 dạng HTML. Cho tới khi xác nhận, KHÔNG coi bảng field trong KB-020/021/022 là contract chính thức — mọi check field-shape ở checklist này chỉ ở mức BASELINE (quan sát), không phải STRONG (spec-confirmed)."}
```

## OQ-artwork-022 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-022", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "summary": "coverage_gaps #3 của KB gốc: chỉ 1 role 1 tenant được test trong cả 3 run nguồn. Hoàn toàn chưa có evidence permission cho toàn bộ luồng save/persist."}
```

## OQ-artwork-023 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-023", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-template-management", "summary": "Chưa từng quan sát artwork có ≥2 template trong evidence nguồn (artwork test chỉ có 1 template) — hành vi nút này ở trạng thái enable hoàn toàn chưa biết."}
```

## OQ-artwork-024 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-024", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-template-management", "summary": "unknown_areas: kết quả sau khi 'Convert to Global Template' hoàn tất chưa từng được quan sát — không biết global template có scope/state khác gì template thường."}
```

## OQ-artwork-025 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-025", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-template-management", "summary": "Chưa đối chiếu được UI field 'Extra charge for this template' với field API thực tế (KB-020 chỉ ghi nhận addons:[] và charge_enabled ở mức observed_count=1, chưa gắn với action cụ thể bật field này)."}
```

## OQ-artwork-026 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-026", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-template-management", "summary": "profile_relationships đánh dấu quan hệ này là INFERRED, chưa xác nhận — 'Import from artwork' có thể liên quan tới danh sách /artworks nhưng chưa có evidence trực tiếp."}
```

## OQ-artwork-027 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-027", "type": "NEEDS_CONFIRMATION", "feature_id": "clipart-category-storefront-behavior", "summary": "<select> chỉ có 1 option placeholder disabled 'Choose a design', 0 item selectable, dù category có 2 item xác nhận tồn tại server-side (no1, no2). correlation_note PLAUSIBLE (không CONFIRMED) cùng root cause với CONF-API-CTX20260921-03-01 (xem CHK-020, layer api) và KB-013 (layer-config-image.json CHK-026, layer portal) — 3 bề mặt riêng biệt, KHÔNG gộp thành 1 statement. Cần db-explorer/api-explorer follow-up trước khi báo bug chính thức."}
```

## OQ-artwork-028 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-028", "type": "NEEDS_CONFIRMATION", "feature_id": "clipart-category-storefront-behavior", "summary": "Server thêm key 'artwork-4339': 11533 (numeric) vào response mà client localStorage KHÔNG hề có tại thời điểm ghi trước đó — mục đích field này CHƯA xác định. Có thể là ID nội bộ quan trọng cho fulfillment/print — cần dev xác nhận trước khi coi absence trong client write là bình thường/vô hại."}
```

## OQ-artwork-029 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-029", "type": "NEEDS_CONFIRMATION", "feature_id": "clipart-category-storefront-behavior", "summary": "Giả thuyết CHƯA XÁC NHẬN: '_large' có thể bị giới hạn (capped) bởi độ phân giải gốc file upload gốc, không upscale vượt quá — độ phân giải gốc no1.png/no2.png KHÔNG được verify độc lập trong run (INFERRED). Nếu giả thuyết sai, nghĩa là Preview size setting (500px) đang KHÔNG hoạt động đúng bất kể ảnh gốc, cần điều tra thêm như 1 defect riêng."}
```

## OQ-artwork-030 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-030", "type": "NEEDS_CONFIRMATION", "feature_id": "clipart-category-storefront-behavior", "summary": "Đây là defect sản phẩm đã xác nhận (canvas/preview/cart PHẢI composite clipart đã chọn — nếu đúng, hiện tại đang FAIL nghiêm trọng) hay là artifact của test fixture (artwork:4339 layer sai z-order/position/opacity trên canvas 1600x1600, không phản ánh sản phẩm thật)? Cần: (1) PO/Dev xác nhận business rule mong đợi cho compositing; (2) re-test trên artwork/campaign MỚI (fixture cũ đã ARCHIVED/DELETED) để loại trừ nguyên nhân do fixture; (3) cross-check api-explorer/db-explorer. correlation_note: PLAUSIBLE (KHÔNG CONFIRMED) cùng root cause dữ liệu category/artwork test với CONF-API-CTX20260921-03-01 (CHK-003/CHK-020) và anomaly group default-value (layer-config-image.json CHK-026) do cùng category/artwork test — KHÔNG coi là đã xác nhận cùng nguyên nhân."}
```

## OQ-artwork-031 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-031", "type": "NEEDS_CONFIRMATION", "feature_id": "clipart-category-storefront-behavior", "summary": "3-way conflict CONF-CTX20260921-03-02 — SUB-SCOPE WIDGET (khác sub-scope compositing ở CHK-017): quan sát cho thấy layer.default_value ('no2') là giá trị PRE-CHECK trên storefront personalization RADIOGROUP lúc load đầu tiên; 'cat1' (url-pick) THẬM CHÍ KHÔNG PHẢI 1 option chọn được vì không phải item của category. Đây có đúng là business rule dự kiến (default_value luôn là nguồn pre-check hợp lệ duy nhất cho storefront, url chỉ dùng nội bộ portal) hay là 1 gap khác cần điều tra? Cần PO/Dev xác nhận. KHÔNG gộp kết luận với CHK-017 (sub-scope compositing) hay layer-config-image.json CHK-024/025 (sub-scope portal canvas) — 3 sub-scope riêng biệt của cùng 1 conflict."}
```

## OQ-artwork-032 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-032", "type": "NEEDS_CONFIRMATION", "feature_id": "clipart-category-storefront-behavior", "summary": "Chưa có evidence nào cho role/market/viewport khác — check này tồn tại để đóng coverage gap đã biết (PERMISSION/device dimension), KHÔNG dựa trên observation cụ thể nào. Cần storefront-explorer chạy thêm trước khi có thể chuyển sang READY."}
```

## OQ-artwork-033 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-033", "type": "NEEDS_CONFIRMATION", "feature_id": "clipart-category-storefront-behavior", "summary": "GET /api/layer-image-categories?type=clipart trả 200, body [] (rỗng); POST /api/graphql clipart_categories(where: {type: clipart, deleted_at: null, parent id: null}, limit: 25) trả 200, 10 rows, CÙNG user/session, CÙNG khoảng thời gian. Root cause CHƯA chẩn đoán (filter khác nhau trên endpoint REST vs GraphQL, hay data/cache issue riêng ở staging). Cần db-explorer/api-explorer follow-up trước khi coi là defect xác nhận. Hệ quả buyer-facing trực tiếp là <select> group-type storefront rỗng 0 item selectable (CHK-003). Correlation PLAUSIBLE (không CONFIRMED) với KB-013 (layer-config-image.json CHK-026, portal)."}
```

## OQ-artwork-034 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-034", "type": "NEEDS_CONFIRMATION", "feature_id": "clipart-category-storefront-behavior", "summary": "Conflict CONF-CTX20260921-03-01 không có nhánh buyer-facing/storefront — liệt kê ở đây CHỈ để tracking đầy đủ 3 conflict của run trong checklist của feature này, KHÔNG lặp lại narrative. Xem layer-config-image.json (FEAT-13, owner chính) CHK-028 cho nội dung đầy đủ."}
```

## OQ-artwork-035 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-035", "type": "NEEDS_CONFIRMATION", "feature_id": "clipart-category-storefront-behavior", "summary": "'Show option to select default value' OFF có ẩn/hiện gì khác trên personalization form storefront so với ON hay không — chỉ test ở trạng thái ON trong run này. Chưa đủ để viết checklist cho cấu hình OFF, có thể bỏ sót 1 nhánh hành vi hoàn toàn khác trên storefront. Check này tồn tại để đóng coverage gap, KHÔNG dựa trên observation cụ thể."}
```

## OQ-artwork-036 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-036", "type": "NEEDS_CONFIRMATION", "feature_id": "condition-cycle-validation", "summary": "BLK-API-002 (unknown nghiêm trọng nhất KB gốc): TOÀN BỘ evidence 3 run — PUT chưa BAO GIỜ được gửi với payload vòng vì client luôn chặn trước. validate-default-value vẫn 204 ngay cả 2 lần bị chặn — KHÔNG phải endpoint kiểm vòng. KHÔNG có evidence nào xác nhận hay bác bỏ việc server tự chặn vòng độc lập. Case này CẦN orchestrator duyệt trước khi chạy (direct-API mutation, ngoài SAFE_REVERSIBLE_ONLY mặc định nếu tạo dữ liệu vòng thật trong DB)."}
```

## OQ-artwork-037 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-037", "type": "NEEDS_CONFIRMATION", "feature_id": "condition-cycle-validation", "summary": "KB-041: self-loop chưa từng thử qua API trực tiếp (ngoài phạm vi portal-explorer/api-runtime-trace)."}
```

## OQ-artwork-038 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-038", "type": "NEEDS_CONFIRMATION", "feature_id": "condition-cycle-validation", "summary": "2/2 sample gốc đều ra 'Word Search' chỉ vì trùng hợp cấu trúc test data (layer duy nhất phụ thuộc cả 8 nguồn) — chưa tách biệt coincidence vs quy luật thật (vd theo thứ tự template/layer)."}
```

## OQ-artwork-039 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-039", "type": "NEEDS_CONFIRMATION", "feature_id": "condition-cycle-validation", "summary": "coverage_gaps #1 của KB gốc: 0 evidence storefront cho toàn bộ object Artwork. Đặc biệt quan trọng ở đây vì đây là edge case bảo vệ tính toàn vẹn dữ liệu — nếu server không chặn (CHK-008), hành vi render cần được biết trước khi coi tính năng này an toàn."}
```

## OQ-artwork-040 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-040", "type": "NEEDS_CONFIRMATION", "feature_id": "conditional-setting-config", "summary": "CONF-001: network_ref của action nguồn (chọn nguồn Toggle, giá trị On) trong evidence gốc trỏ nhầm vào 1 file mô tả action khác (không chứa PUT nào). Check này VẪN dùng được vì oracle chính là quan sát UI (screenshot), nhưng nếu cần verify thêm ở tầng API cho đúng action này, kết quả API-side hiện KHÔNG đáng tin cho tới khi CONF-001 được làm rõ."}
```

## OQ-artwork-041 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-041", "type": "NEEDS_CONFIRMATION", "feature_id": "conditional-setting-config", "summary": "Test tối đa đã thử là 8 condition (hết đúng số nguồn khả dụng trong artwork test), KHÔNG phải giới hạn thật của hệ thống — cần nhiều nguồn hơn 8 để xác định ngưỡng thật."}
```

## OQ-artwork-042 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-042", "type": "NEEDS_CONFIRMATION", "feature_id": "conditional-setting-config", "summary": "Không có UI cho lồng nhóm AND trong OR trong toàn bộ evidence hiện có — chưa xác nhận đây là giới hạn thiết kế cố ý hay chưa khám phá hết."}
```

## OQ-artwork-043 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-043", "type": "NEEDS_CONFIRMATION", "feature_id": "conditional-setting-config", "summary": "KB-033 chỉ observed_count=1 — chỉ quan sát đúng 2 dạng control, KHÔNG nên coi đây là toàn bộ tập toán tử hệ thống hỗ trợ."}
```

## OQ-artwork-044 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-044", "type": "NEEDS_CONFIRMATION", "feature_id": "conditional-setting-config", "summary": "Chưa có evidence nào cho việc server có validate 'layer type nào được phép có dependency' độc lập với UI hay không."}
```

## OQ-artwork-045 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-045", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "summary": "Ungroup luôn disabled trong mọi sample nguồn vì chưa từng có group nào được tạo — chưa test được cặp Group/Ungroup end-to-end dù đây là action chính trên action bar."}
```

## OQ-artwork-046 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-046", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "summary": "Chỉ test 1 account/1 plan (Blue Test) trong cả 3 run — chưa biết danh sách layer type có phụ thuộc plan/feature-flag không."}
```

## OQ-artwork-047 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-047", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "summary": "KB-015 chỉ test riêng thư viện Vector — chưa rõ đây là hành vi chung cho mọi picker cần asset hay đặc thù riêng Vector."}
```

## OQ-artwork-048 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-048", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-common-config", "summary": "CONF-006 UNRESOLVED: 2 nguồn evidence khác loại (code-derived INFERRED 29 type vs UI observed 33 type) không khớp phạm vi — cần đối chiếu chéo trực tiếp từng type trong 9 type chênh lệch để xác định nguồn nào đúng, hoặc cả 2 đều đúng theo nghĩa khác nhau."}
```

## OQ-artwork-049 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-049", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-condition-value-binding", "summary": "KB-037 (nguồn duy nhất cho pattern này) có knowledge_kind INFERRED, KHÔNG phải OBSERVED_CURRENT hay CONFIRMED_EXPECTED — theo contract chỉ 2 loại đó mới là oracle hợp lệ. Pattern 'element luôn là layer id' được suy ra từ 10 sample (không có UI nào tạo element khác layer id) nhưng CHƯA được xác nhận là quy tắc hệ thống chính thức — không dùng làm assertion cứng cho tới khi có xác nhận."}
```

## OQ-artwork-050 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-050", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-condition-value-binding", "summary": "Mọi sample có toggle làm nguồn condition trong 3 run nguồn đều chọn On (true) — KHÔNG nên giả định symmetry với true khi chưa xác nhận; ảnh hưởng trực tiếp tới test data cho negative case."}
```

## OQ-artwork-051 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-051", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-condition-value-binding", "summary": "Multi-value chỉ xác nhận THẬT ở nguồn clipart-category (layer paragraph pre-existing, 2 giá trị webp path, KB-036). 6/8 type nguồn dạng array còn lại chỉ test với đúng 1 giá trị/condition — shape khi chọn ≥2 giá trị hoàn toàn chưa xác nhận cho 6 type này."}
```

## OQ-artwork-052 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-052", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-condition-value-binding", "summary": "CONF-002 UNRESOLVED: R2 ghi nhận addon-charge CHƯA có option, json-list CHƯA có URL; R3 (cùng artwork 4087) ghi nhận CẢ HAI đã có dữ liệu. Nhiều khả năng do state đổi giữa 2 run (ai đó cấu hình thêm giữa 2 lần chạy) chứ không phải mâu thuẫn hành vi sản phẩm, nhưng KHÔNG tự kết luận theo contract §8 — PHẢI kiểm tra trạng thái thật của test data trước khi dùng làm precondition cho case khác."}
```

## OQ-artwork-053 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-053", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-form-elements", "summary": "Quan sát 1 lần (capture Conditional Setting, KB-041): Color có Option Title đầy đủ nhưng KHÔNG xuất hiện làm nguồn condition, khác Font. Chưa xác nhận đây là thiết kế cố ý hay giới hạn kỹ thuật — cần dev/PO xác nhận trước khi coi là expected behavior."}
```

## OQ-artwork-054 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-054", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "bundle-registry (INFERRED) gợi ý 2 field cùng mục đích nhưng key khác nhau (text_to_image_provider/multi_image_provider) — chưa cross-check qua PUT body thật của chính 2 type này."}
```

## OQ-artwork-055 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-055", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "'Select a group of clipart categories' có hỗ trợ multi-category thật hay chỉ 1 category có nested children (Parent Category field)? Ảnh hưởng trực tiếp thiết kế test data & assertion cho group type — nếu chỉ 1-category-nested thì tên field 'group' gây hiểu nhầm."}
```

## OQ-artwork-056 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-056", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "3-way conflict CONF-CTX20260921-03-02: url drive canvas portal (nhánh a, CHK-024) / default_value drive form widget storefront (nhánh b, xem FEAT-19 CHK-018) / KHÔNG bên nào drive compositing cuối cùng (nhánh c, CRITICAL KB-030, xem FEAT-19 CHK-017). Ở PHẠM VI PORTAL: layer.default_value có ý nghĩa/tác dụng nào trên canvas editor hay hoàn toàn vô dụng ở đây (chỉ có tác dụng phía storefront)? Cần PO/Dev xác nhận trước khi viết assertion chính thức. KHÔNG gộp kết luận với 2 nhánh còn lại — xem full narrative ở FEAT-19 (owner chính của conflict)."}
```

## OQ-artwork-057 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-057", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "Combobox hiện 'List is empty.' dù category có 2 item xác nhận tồn tại server-side VÀ đã render đúng ở picker default-value của layer single-type CÙNG PHIÊN. correlation_note: PLAUSIBLE (KHÔNG CONFIRMED) cùng root cause với CONF-API-CTX20260921-03-01 (REST[]/GraphQL10-rows) — đây là 1 UI surface RIÊNG BIỆT, KHÔNG gộp thành 1 statement cho tới khi db-explorer/api-explorer xác nhận. Cần điều tra: request nào backing combobox này, filter gì khác so với picker default-value single-type."}
```

## OQ-artwork-058 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-058", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "GET REST trả [] (0 rows) trong khi GraphQL trả 10 rows cùng user/session cùng khoảng thời gian — root cause CHƯA chẩn đoán (filter khác nhau hay cache/data issue riêng staging). Cần db-explorer/api-explorer follow-up trước khi coi là defect xác nhận. Correlation PLAUSIBLE (không CONFIRMED) với KB-013 (CHK-026, portal) và KB-021 (FEAT-19, storefront) — 3 bề mặt riêng biệt, KHÔNG gộp thành 1 statement."}
```

## OQ-artwork-059 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-059", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "canonical v2 (published, MEDIUM confidence) khẳng định field 'Custom class:' là baseline PERSONALIZATION SETTINGS cho clipart-category (single). Evidence v3 (, LOW confidence, đã scroll hết Bulk Edit + kiểm tra API response cho cả layer 'cat1' single lẫn 'body' group) KHÔNG tìm thấy field này ở bất kỳ đâu. KHÔNG kết luận field đã bị xoá (regression thật) hay CHƯA từng tồn tại đúng như baseline claim (v2 sai) — cần PO/Dev xác nhận hoặc phát hiện panel single-layer settings riêng (khác Bulk Edit) trước khi kết luận. Xem thêm CHK-002 (v2 cũ, giữ nguyên, KHÔNG tự sửa)."}
```

## OQ-artwork-060 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-060", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "Field API 'show_clipart_name' chỉ quan sát giá trị null, CHƯA test bật/tắt toggle tương ứng — chỉ trùng tên, chưa xác nhận đây có đúng backing field cho UI toggle 'Show option name on hover' hay không. Nếu sai, có thể có 1 field UI khác chưa được map."}
```

## OQ-artwork-061 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-061", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "CHK-032 chỉ quan sát 1 sample (layer ĐÃ cấu hình làm destination) — chưa xác nhận thứ tự accordion 'Populate Values đầu tiên' có cố định cho MỌI layer photo (kể cả chưa cấu hình gì) hay chỉ xuất hiện khi Populate Values đã được cấu hình/bật trước đó. Ảnh hưởng cách viết test case assert thứ tự UI accordion — nếu chỉ đúng khi đã bật Populate Values, test case cần setup đúng precondition."}
```

## OQ-artwork-062 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-062", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "Chỉ quan sát trạng thái mặc định OFF của toggle 'Use Template Default Size' — chưa test tác dụng khi bật ON (ảnh hưởng size ảnh generate? disable field khác?). Không thể viết assertion chính thức tới khi có evidence."}
```

## OQ-artwork-063 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-063", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "Rule 'prompt required' (CHK-037, CHK-046) chỉ xác nhận với provider Gemini cho cả Multiple Uploads lẫn Text to Image — OpenAI/Flux/ImagenHub có cùng rule không? Rủi ro viết test case negative (prompt trống) chỉ đúng cho 1 provider rồi tổng quát sai cho provider khác."}
```

## OQ-artwork-064 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-064", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "CHK-040 chỉ test Maximum photos=3 (thấy token indexed {{input.1..3}}) — chưa test Maximum photos=1, không rõ token có đổi thành dạng trần '{{input}}' hay vẫn giữ '{{input.1}}'. Ảnh hưởng thiết kế test case populate content khi Multiple Uploads chỉ cho phép 1 ảnh."}
```

## OQ-artwork-065 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-065", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "1 lần thử ở UI cấu hình portal (chọn Flux) KHÔNG thấy cảnh báo unsupported-provider — nhưng cảnh báo có thể chỉ hiện lúc generate thật (chưa thử). Nếu cảnh báo chỉ hiện lúc generate, test case cấu hình UI hiện tại sẽ không phát hiện được vấn đề thật. Liên quan FEAT-09-genai-personalization-runtime (object sdk) cho phần generate thật."}
```

## OQ-artwork-066 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-066", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "CHK-044 chỉ quan sát trạng thái RỖNG (message hướng dẫn) khi CHƯA có layer Text/Additional Option khác — chưa quan sát behavior thật của picker khi CÓ option để chọn. Ảnh hưởng test case cho luồng variable binding trong prompt."}
```

## OQ-artwork-067 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-067", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "Trong 1 lần kiểm tra, Source option dropdown của Populate Content KHÔNG offer layer Text to Image (AI) làm nguồn (chỉ offer Multiple Uploads cùng session) — 1 SAMPLE PHỦ ĐỊNH, CHƯA đủ để kết luận Text-to-Image không bao giờ được offer làm nguồn populate. Cần re-test sau khi save artwork hoặc với artwork khác trước khi viết assertion chính thức (dù là assertion phủ định)."}
```

## OQ-artwork-068 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-068", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "KHÔNG tìm thấy Beta badge/text nào gắn với Text to Image (AI) ở CẢ portal config UI LẪN storefront Live Preview widget panel — nhưng 2 bề mặt này đều staff-authenticated proxy (KHÔNG phải guest thật), mỗi bề mặt chỉ 1 lần thử. KHÔNG kết luận 'không có Beta badge' cho storefront PDP/theme Shopify thật tới khi có evidence guest thật."}
```

## OQ-artwork-069 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-069", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "CONF-CBS003-01 (UNRESOLVED, CCR CBS-003): canon KB-019 (kb_version 3.0, đã publish) ghi 2 lựa chọn; quan sát (2026-09-25, artwork 4416, layer 'hair') ghi 3 lựa chọn (thêm 'No personalization'). KHÔNG có build/version/deploy-date nguồn để phân biệt 'hành vi đã đổi thật' vs 'KB-019 từng ghi sai lúc verify trước' (CCR CBS-003 Phần 3 để trống 'không rõ'). Cần authority (orchestrator/context-quality-reviewer, hoặc PO/Dev qua CCR) quyết định theo §8 của contract. KHÔNG được dùng làm oracle chính thức cho tới khi resolve — KHÔNG viết test case assert cứng '2 lựa chọn' hay '3 lựa chọn'."}
```

## OQ-artwork-070 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-070", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "TIB-5188 (thứ tự resize/crop và minimum-resolution validation của pipeline GenAI khi generate ảnh từ Multiple Uploads) HOÀN TOÀN CHƯA TEST — 'Set minimum size' để OFF trên fixture duy nhất của mọi run tính tới nay, bật toggle bị đánh giá ngoài ngân sách run. KHÔNG suy diễn thành 'không có vấn đề' hay pass/fail mặc định — coverage gap thật, cần run tiếp theo với ngân sách riêng."}
```

## OQ-artwork-071 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-071", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "Trong lần thử duy nhất, CẢ HAI route (chính và fallback) đều fail cùng lý do (ảnh bị client re-encode xuống dưới ngưỡng 10000 byte trước khi tới cả 2 route). Route fallback multipart THẬT SỰ TỒN TẠI và được tự động thử khi route chính lỗi (xác nhận), nhưng chưa có lần route fallback THÀNH CÔNG để so sánh downstream GenAI generate là sync hay async. KHÔNG suy diễn kết quả so sánh — cần fixture/ảnh input phù hợp hơn ở run tiếp theo."}
```

## OQ-artwork-072 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-072", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "summary": "'Duplicate & Share' (TIB-5326) KHÔNG tìm thấy ở CẢ portal editor lẫn storefront Live Preview cho layer Text to Image (AI)/Multiple Uploads — 2 agent độc lập cùng không tìm thấy, KHÔNG kết luận feature không tồn tại (có thể bị gate bởi điều kiện chưa trigger: nhiều biến thể generated, cart/order thật, plan cụ thể). Cần hỏi dev/PO trước khi viết test case chính thức."}
```

## OQ-artwork-073 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-073", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-maps-astronomy", "summary": "Statement gốc (KB-024) tự ghi 'chưa verify trực tiếp trong evidence này' — map không render nếu thiếu Mapbox token là suy luận hợp lý, chưa phải quan sát thật."}
```

## OQ-artwork-074 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-074", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-maps-astronomy", "summary": "Chưa xác nhận 'seacher' là typo THẬT của product code hay lỗi ghi chép evidence — nếu viết test/assertion theo tên field JSON, phải dùng đúng chuỗi thật trong code, không tự sửa chính tả."}
```

## OQ-artwork-075 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-075", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-others", "summary": "Giới hạn 4296 ký tự (KB-034) là hint text UI quan sát 1 lần — CHƯA từng thử nhập vượt giới hạn để xác nhận hành vi thật, không tổng quát hoá thành validation rule chính thức."}
```

## OQ-artwork-076 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-076", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-puzzles", "summary": "DOM dump gốc (KB-030) cho thấy 'Custom class:' xuất hiện 2 lần trong cùng panel — CHƯA XÁC NHẬN đây là 2 field JSON riêng hay lỗi render trùng của portal. Cần portal-explorer verify lại trực tiếp."}
```

## OQ-artwork-077 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-077", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-text", "summary": "Hint 'enter number from 20' chỉ quan sát 1 lần (observed_count=1, KB-014) — chưa từng thử nhập giá trị <20 để biết đây là hard validation hay chỉ gợi ý UI."}
```

## OQ-artwork-078 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-078", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-text", "summary": "bundle-registry hiện tại KHÔNG liệt kê field này gắn với layer type cụ thể nào — không thể viết assertion API/DB cho field này tới khi xác nhận được key."}
```

## OQ-artwork-079 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-079", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-vector", "summary": "Static Vector chưa có per-type DOM dump riêng nào khác ngoài ngoại lệ Custom class — nếu type này có field riêng trong tương lai, cần tạo KB item per-type mới, không sửa KB-011."}
```

## OQ-artwork-080 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-080", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-vector", "summary": "CONF-CBS004-001 (UNRESOLVED): 1 nguồn (api-explorer) quan sát 3 lần gọi liên tiếp 422 → remaining giữ nguyên = 1000 (không giảm); 1 nguồn khác (portal-explorer) quan sát 1 lần gọi 201 → remaining giảm 1 (999). Mỗi phía chỉ 1 sample, mỗi phía ở 1 status code khác nhau — KHÔNG đủ để khẳng định remaining chỉ giảm khi request THÀNH CÔNG hay theo quy tắc khác. KHÔNG tự resolve (đúng contract §8), KHÔNG dùng làm oracle behavior 'remaining' cho tới khi có thêm sample ở cả 2 status code. Cần orchestrator/reviewer quyết định hướng verify tiếp theo (vd chạy thêm N sample mỗi phía)."}
```

## OQ-artwork-081 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-081", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "summary": "Đây là hành vi cốt lõi được message UI khẳng định ('Design and personalization are synced from it') nhưng CHƯA được test end-to-end trong 3 run nguồn — chỉ xác nhận trạng thái NGAY SAU KHI tạo, chưa test sync thực sự qua 1 vòng sửa-lại-gốc."}
```

## OQ-artwork-082 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-082", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "summary": "Chưa rõ quy luật vì sao đúng 15/35 type rơi vào PLAIN_COPY — theo nhóm layer (form-elements/AI/upload) hay theo implementation riêng lẻ từng type — không dự đoán được cho layer type mới."}
```

## OQ-artwork-083 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-083", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "summary": "KB-020/KB-022 chỉ có full body cho 1 sample không chứa layer linked — chưa có oracle ở tầng API cho trạng thái linked, chỉ có oracle UI (accordion LINKED LAYER)."}
```

## OQ-artwork-084 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-084", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-print-effects", "summary": "CONF-004 UNRESOLVED: brief giả định Print Effects đã có emboss phụ thuộc dịch vụ 3rd-party; quan sát thực tế trên 4/35 layer type + trang 3rd-party Services (plan Blue Test) không tìm thấy chuỗi 'emboss'/'3rd-party' ở đâu. KHÔNG kết luận emboss không tồn tại — có thể gate theo plan, layer type khác chưa thử, hoặc cấu hình 3rd-party service chưa bật. Cần dev/PO xác nhận."}
```

## OQ-artwork-085 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-085", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-print-effects", "summary": "Chưa đối chiếu Print Effects với KB-020/KB-022 — chỉ có oracle UI (popover), chưa có oracle ở tầng API cho tính năng này."}
```

## OQ-artwork-086 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-086", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-print-effects", "summary": "'Order Design' hoàn toàn chưa được khám phá trong 3 run nguồn — chỉ biết qua nội dung footnote, chưa xác nhận luồng production guide thật sự hoạt động ra sao."}
```

## OQ-artwork-087 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-087", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "Chỉ 1 sample quan sát (observed_count=1) — chưa xác nhận 13 nhóm này có tương ứng 1-1 đầy đủ với mọi layer/output type hay còn nhóm khác chưa liệt kê."}
```

## OQ-artwork-088 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-088", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "11 template biến đổi giá trị được liệt kê tên nhưng cú pháp thật sự hỗ trợ biểu thức/range gì của formula/context chưa từng được test với input cụ thể. Bổ sung CBS-110 (2026-11-11): rule QA FACT-022/FACT-024 (S2, KB-987, KB-988, KB-991) ghi kết quả của token context/formula sai, không hoàn chỉnh và hằng số năm 365.2425, chưa PO/Dev xác nhận (OQ-artwork-455, OQ-artwork-456, OQ-artwork-459); cú pháp hỗ trợ đầy đủ vẫn chưa có nguồn nên câu hỏi vẫn mở."}
```

## OQ-artwork-089 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-089", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "Chỉ test 2 channel Font và Color — chưa rõ cơ chế khoá theo Google Font có áp dụng cho Background/Shape hay là đặc thù riêng của Font."}
```

## OQ-artwork-090 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-090", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "0 evidence storefront cho Font/Color/Word Cloud/dynamic-by-text — đây là feature có mức độ 'chưa test nơi giá trị thực sự được dùng' cao nhất trong toàn bộ checklist (dù nay đã có 1 luồng khác — Multiple Uploads→Photo — có evidence storefront MỘT PHẦN, xem CHK-022)."}
```

## OQ-artwork-091 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-091", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "CHK-019 chỉ test Maximum photos=3 (thấy token indexed {{input.1..3}}) — chưa test Maximum photos=1, không rõ token có đổi thành dạng trần '{{input}}' hay vẫn giữ '{{input.1}}'. Ảnh hưởng thiết kế test case populate content khi Multiple Uploads chỉ cho phép 1 ảnh."}
```

## OQ-artwork-092 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-092", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "Trong session cấu hình artwork 4416, Source option dropdown của Populate Content trên layer đích 'body' CHỈ liệt kê layer Multiple Uploads ('top'); layer Text to Image (AI) ('hair') KHÔNG xuất hiện. Quan sát 1 lần duy nhất trong 1 cấu hình cụ thể — KHÔNG kết luận Text-to-Image không bao giờ được offer làm nguồn populate; cần re-test ở cấu hình/thời điểm khác trước khi viết assertion chính thức (dù là assertion phủ định)."}
```

## OQ-artwork-093 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-093", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "KB-008 (CHK-022) CHỈ xác nhận nửa 'giá trị gốc lan truyền ngay, không chờ Generate của layer nguồn'. Nửa còn lại (layer đích tự động trigger effect chain riêng của nó lên giá trị được populate, mô tả liên quan TIB-5302) KHÔNG xác nhận được trong run này vì layer 'body' của fixture không có effect nào cấu hình. KHÔNG suy diễn cơ chế effect tự trigger là đúng dù có TIB-5302 làm nguồn gợi ý (Jira KHÔNG phải authority theo §12.4 rule 2 của contract). Nếu sai giả định, test case cho layer đích CÓ effect cấu hình sẵn sẽ thiếu coverage quan trọng."}
```

## OQ-artwork-094 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-094", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "Phần storefront của KB-008 (CHK-022) quan sát qua Live Preview widget với vai trò staff-authenticated PROXY cho buyer (account explorer (TIB_STAGING_EMAIL)), KHÔNG PHẢI guest session thật. KHÔNG dùng làm bằng chứng hành vi buyer thật 100% (vd cross-tenant, rate-limit, hoặc UI khác biệt trên theme Shopify thật chưa loại trừ) tới khi có evidence guest thật."}
```

## OQ-artwork-095 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-095", "type": "OPEN_ISSUE", "feature_id": "artwork-save-persist", "summary": "3 of 4 successful PUT saves observed across the source runs only captured method/status (no full request+response body) — most field-level PUT behavior beyond the one fully-captured sample is unverified."}
```

## OQ-artwork-096 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-096", "type": "OPEN_ISSUE", "feature_id": "object-wide", "summary": "No direct database (Postgres) access has been used for any Artwork observation to date — every 'data' claim in this object is inferred from Hasura GraphQL responses or PUT response echoes, never verified against the actual DB schema/rows."}
```

## OQ-artwork-097 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-097", "type": "OPEN_ISSUE", "feature_id": "object-wide", "summary": "Every JSON field key attributed to a layer type via bundle-registry (code) across all layer-config-* features is INFERRED, not cross-checked directly against a live API/DB field for that specific type — treat as non-authoritative until confirmed."}
```

## OQ-artwork-098 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-098", "type": "OPEN_ISSUE", "feature_id": "object-wide", "summary": "Storefront (buyer-facing) rendering has zero evidence for the large majority of layer types/features in this object (only Clipart Category and parts of Multiple Uploads/Text to Image/Photo Upload have any storefront evidence) — most storefront behavior for Artwork is completely unexplored."}
```

## OQ-artwork-099 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-099", "type": "OPEN_ISSUE", "feature_id": "object-wide", "summary": "Every run to date tested exactly one role (store owner/staff, account explorer (TIB_STAGING_EMAIL)) on one tenant/organization — no permission or cross-tenant behavior has been verified for any Artwork feature."}
```

## OQ-artwork-100 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-100", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "Stack stroke của Paragraph (tối đa 3 lớp, width là độ dày riêng từng vòng, xếp từ mép chữ ra ngoài theo thứ tự row, xoá/đổi thứ tự giữ dữ liệu) có phải hành vi đúng theo PO/business, và có giữ nguyên trên build TIB-5580 khi ship không? Mới là quan sát một lượt chạy test staging trước khi ship; checklist không có oracle xác nhận cho các check cốt lõi của feature.", "kb_ids": ["KB-129", "KB-130", "KB-131"]}
```

## OQ-artwork-101 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-101", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "Gửi thẳng PUT /api/artworks/{id} cho Paragraph với stroke_layers có entry thứ 4, hoặc width không phải số, thì server từ chối, cắt bớt hay lưu nguyên? Giới hạn 3 lớp chỉ thấy ở UI (nút 'Add stroke' disable); không có oracle cho validate phía server của artwork.", "kb_ids": ["KB-129"]}
```

## OQ-artwork-102 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-102", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "Paragraph mới tạo khi stroke còn tắt có lưu sẵn entry stroke_layers không, và mặc định (tắt; bật lên 1 row #FF0000 / 1px; stroke_color/stroke_width bằng lớp trong cùng) có phải hành vi đúng? Dữ liệu lưu khi stroke tắt chưa quan sát; check dữ liệu mặc định của paragraph mới không có oracle.", "kb_ids": ["KB-132"]}
```

## OQ-artwork-103 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-103", "type": "OPEN_ISSUE", "feature_id": "text-multi-stroke", "summary": "Preview storefront (SDK) hiển thị Paragraph nhiều lớp stroke thế nào (thứ tự vành, round, autoscale, layer linked) khi SDK staging có code TIB-5580? SDK staging chưa có code TIB-5580 nên mọi phần storefront của các test case bị Blocked; buyer thấy preview storefront trước khi đặt hàng.", "kb_ids": ["KB-133", "KB-138", "KB-139"]}
```

## OQ-artwork-104 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-104", "type": "OPEN_ISSUE", "feature_id": "text-multi-stroke", "summary": "Bản SVG (vectorize) của order design có đúng thứ tự vành, góc round, không vẽ vành khi stroke tắt, không cắt vành khi autoscale — cho Paragraph và Text 1 dòng? Không có đường tải SVG order design trên portal staging; SVG là một đầu ra in nhưng hoàn toàn chưa được kiểm.", "kb_ids": ["KB-133", "KB-134", "KB-135", "KB-139", "KB-143"]}
```

## OQ-artwork-105 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-105", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "PNG order design khớp preview Artwork Editor (fill trên mọi vành, góc round, autoscale không cắt vành) có phải hành vi đúng, và mức chênh lệch bề dày vành nào là chấp nhận được khi đo pixel? Kết luận render đều dựa trên so sánh bằng mắt, chưa có xác nhận PO/business; check render không có ngưỡng đo khách quan.", "kb_ids": ["KB-130", "KB-133", "KB-134", "KB-139"]}
```

## OQ-artwork-106 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-106", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "Tắt stroke giữ nguyên stroke_layers (stroke_enabled=false) và bật lại khôi phục các lớp cũ có phải hành vi đúng? Quyết định check 'tắt rồi bật lại' kỳ vọng khôi phục hay reset; chưa có xác nhận.", "kb_ids": ["KB-135"]}
```

## OQ-artwork-107 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-107", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "Convert Paragraph nhiều lớp sang Spiral Text và các loại layer khác ngoài Curve/Warp Text cho kết quả gì, và việc gộp về lớp trong cùng (bỏ lớp ngoài) có phải hành vi đúng? Mới quan sát Curve và Warp; người dùng mất lớp ngoài khi convert, cần biết đó là thiết kế hay lỗi. Cần PO xác nhận việc bỏ các lớp stroke ngoài khi convert sang Curve/Warp là chủ đích (dữ liệu stroke ngoài bị mất khỏi bản lưu).", "kb_ids": ["KB-136", "KB-137"]}
```

## OQ-artwork-108 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-108", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "Vành của Paragraph linked scale chính xác theo tỉ lệ kích thước (đo được) không, và PNG order design của layer linked có đúng như preview editor không? Tỉ lệ mới đánh giá bằng mắt trên preview editor; PNG của layer linked chưa kiểm.", "kb_ids": ["KB-138"]}
```

## OQ-artwork-109 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-109", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "Việc Custom Shape text và Paragraph trên Artwork 1.0 chỉ có 1 stroke (không có stack) là quyết định sản phẩm đã duyệt chưa, và Paragraph Artwork 1.0 sau khi đổi width lưu payload thế nào? Phạm vi loại trừ mới là quan sát hiện tại; payload Paragraph Artwork 1.0 chưa kiểm được vì fixture không Save được.", "kb_ids": ["KB-140", "KB-141", "KB-142"]}
```

## OQ-artwork-110 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-110", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "Multi-stroke của Text 1 dòng (TIB-5417) có giữ nguyên trong editor, API và PNG trên build TIB-5580 khi ship không? Regression mới kiểm trên build staging chưa ship; cần kiểm lại sau khi ship.", "kb_ids": ["KB-143"]}
```

## OQ-artwork-111 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-111", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "Server phải từ chối/loại bỏ stroke_layers sai do buyer gửi kèm personalization (4 entry, width không phải số), hay chấp nhận nhưng bỏ qua khi render là đủ? API hiện trả 201 và echo phần chèn (BUG-357); chưa ai phân xử nên check của luồng này không có expected result. Cần PO xác nhận ý định (item mới chạm ranh giới ghi dữ liệu của buyer chưa đăng nhập, BUG-357).", "kb_ids": ["KB-144"]}
```

## OQ-artwork-112 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-112", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "Server có thực sự lưu stroke_layers do buyer chèn vào customization, hay chỉ echo trong response? Việc lưu chỉ suy từ response echo; nếu được lưu, phần chèn có thể ảnh hưởng đầu ra khác (storefront, SVG) chưa kiểm.", "kb_ids": ["KB-144"]}
```

## OQ-artwork-113 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-113", "type": "OPEN_ISSUE", "feature_id": "text-multi-stroke", "summary": "Ai đã đổi status Testlane của task TIB-220 sau lượt chạy, và status hay actualResult mới là kết quả đúng của các test case lệch ('passed' trong khi actualResult ghi Blocked; TC-TIB-6338 'skipped' trong khi actualResult ghi Fail)? Các test case này không dùng được làm nguồn xác nhận cho tới khi status và actualResult khớp.", "kb_ids": ["KB-133", "KB-138", "KB-139", "KB-142", "KB-144"]}
```

## OQ-artwork-114 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-114", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "summary": "Vì sao PUT /api/artworks/5187 trả 500 'Server Error' kể cả khi Save không đổi gì trên bản copy Artwork 1.0 chưa có version đã lưu — lỗi dữ liệu của bản copy, lỗi sản phẩm với artwork Artwork 1.0 chưa có version, hay liên quan TIB-5580? Quyết định đây là bug sản phẩm cần check hồi quy hay chỉ là fixture hỏng; cần log server để phân biệt.", "kb_ids": ["KB-145"]}
```

## OQ-artwork-115 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-115", "type": "OPEN_ISSUE", "feature_id": "artwork-save-persist", "summary": "Các artwork Artwork 1.0 khác (không phải bản copy #5187, kể cả artwork gốc #2164 hoặc artwork 1.0 đã có version lưu) có Save được không? Cần một artwork Artwork 1.0 Save được làm fixture để chạy lại check Paragraph Artwork 1.0; hiện chưa biết phạm vi của lỗi 500.", "kb_ids": ["KB-145"]}
```

## OQ-artwork-116 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-116", "type": "OPEN_ISSUE", "feature_id": "artwork-save-persist", "summary": "Khi PUT /api/artworks/{id} trả 500, Artwork Editor hiển thị gì cho người dùng (toast/thông báo lỗi, giữ thay đổi chưa lưu hay không)? KB-145 chỉ ghi artwork không Save được, không ghi phản hồi UI; check negative cho lỗi server khi Save chưa có oracle.", "kb_ids": ["KB-145"]}
```

## OQ-artwork-117 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-117", "type": "OPEN_ISSUE", "feature_id": "text-multi-stroke", "summary": "Global template: stroke_layers của Paragraph có là field local (không bị merge từ global template) và spiral/shape text vẫn 1 stroke không? Chưa kiểm được: fixture global template dựng qua API không mở được trong Artwork Editor trên staging (chưa rõ lỗi fixture hay lỗi sản phẩm).", "kb_ids": []}
```

## OQ-artwork-118 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-118", "type": "OPEN_ISSUE", "feature_id": "text-multi-stroke", "summary": "Shadow của Paragraph: theo mô tả dev của TIB-5580 (PR api #4016), shadow áp 1 lần cho cả khối ở vectorize và PNG, và preview/PNG/SVG không được lệch; thay đổi này có thể làm sai ghi nhận cũ về shadow paragraph của TIB-5472. Trong lượt test staging 2026-10-21→22, editor và PNG order design cho thấy một khối shadow cho cả paragraph và PNG khớp editor (2 order Bogus); SVG và preview storefront SDK chưa kiểm. Phần editor + PNG đã quan sát nay là KB-251 (OBSERVED_CURRENT/LOW, CBS-017); quy tắc cho cả 3 renderer chưa có nguồn xác nhận. Cần chạy lại khi SDK staging có code và tải được SVG, hoặc nguồn PO/dev xác nhận.", "kb_ids": ["KB-251"]}
```

## OQ-artwork-119 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-119", "type": "OPEN_ISSUE", "feature_id": "text-multi-stroke", "summary": "Fill opacity < 1 với Paragraph nhiều lớp stroke: quy tắc 'bleed trong 1 dòng là known issue, vùng stroke 2 dòng chồng nhau đậm gấp đôi là lỗi' chỉ là đáp án của QA, chưa kiểm (SVG không tải được, SDK chưa có code). Ngoài ra ở một order PNG trên staging, vành stroke trắng trông mỏng hơn hẳn so với preview editor (ước lượng bằng mắt, chưa rõ nguyên nhân) — KB-133 chỉ áp cho các stack đã so khớp, chưa áp cho trường hợp này.", "kb_ids": ["KB-133"]}
```

## OQ-artwork-120 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-120", "type": "OPEN_ISSUE", "feature_id": "text-multi-stroke", "summary": "Import PSD có paragraph nhiều lớp stroke: chưa có test case, chưa có kiến thức về cách stroke_layers được tạo khi import.", "kb_ids": []}
```

## OQ-artwork-121 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-121", "type": "OPEN_ISSUE", "feature_id": "text-multi-stroke", "summary": "Chọn nhiều layer cùng lúc (Text + Paragraph) rồi chỉnh stroke: ngoài phạm vi kiểm của TIB-5580 theo trao đổi nội bộ QA, chưa có kiến thức; chưa có xác nhận PO đây là ngoài phạm vi sản phẩm.", "kb_ids": []}
```

## OQ-artwork-122 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-122", "type": "NEEDS_CONFIRMATION", "feature_id": "text-color-sequence-render", "summary": "Hành vi đúng (PO/business) của render text rainbow trên Locate Artwork và Order Design PNG — căn phải/giữa/trái, độ rộng bằng text 1 màu, autoscale tên dài, letter spacing, kerning — có đúng như đang quan sát (khớp preview SDK) không? Hiện chỉ là quan sát một lượt chạy trên staging, chưa ai xác nhận; checklist không có oracle cho các nhánh này.", "kb_ids": ["KB-146", "KB-147", "KB-148", "KB-149", "KB-151", "KB-152"]}
```

## OQ-artwork-123 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-123", "type": "NEEDS_CONFIRMATION", "feature_id": "text-color-sequence-render", "summary": "Text font thường (Roboto) và text 1 màu trên Order Design PNG có thật khớp preview SDK không, khi đo lại có số đo và fixture? Chỉ có tóm tắt kết quả, không có actualResult chi tiết; muốn làm baseline cho nhánh không rainbow cần chạy lại có số đo.", "kb_ids": ["KB-150"]}
```

## OQ-artwork-124 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-124", "type": "NEEDS_CONFIRMATION", "feature_id": "text-color-sequence-render", "summary": "Stroke 1 lớp liền mạch ở chỗ nối chữ và text RTL giữ màu từng chữ theo thứ tự preview SDK có phải hành vi đúng không? Quan sát một lượt trên staging (stroke đánh giá bằng mắt, RTL chỉ font Heebo), chưa có PO/business xác nhận.", "kb_ids": ["KB-153", "KB-155"]}
```

## OQ-artwork-125 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-125", "type": "NEEDS_CONFIRMATION", "feature_id": "text-color-sequence-render", "summary": "Với text rainbow mang multi-stroke, Order Design PNG đúng ra phải thế nào — stroke liền mạch ở chỗ nối chữ như preview SDK? PNG hiện có sợi màu chữ đè lên stroke (BUG-363); không có expected được xác nhận thì không viết được check pass/fail cho nhánh này.", "kb_ids": ["KB-154"]}
```

## OQ-artwork-126 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-126", "type": "OPEN_ISSUE", "feature_id": "text-color-sequence-render", "summary": "BUG-363 (sợi màu chữ đè stroke ở chỗ nối, rainbow + multi-stroke) có từ trước bản fix TIB-5606 hay do bản fix gây ra? Một nguồn ngoài (TC-TIB-4045, verified 2026-10-01) ghi rainbow + multi-stroke render đúng 3 vành, màu từng chữ giữ nguyên — khác build/font với lượt chạy 2026-10-22. Nếu bản fix gây ra, đây là regression của multi-stroke.", "kb_ids": ["KB-154"]}
```

## OQ-artwork-127 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-127", "type": "NEEDS_CONFIRMATION", "feature_id": "text-color-sequence-render", "summary": "Curve Text rainbow ở căn phải render thế nào, Curve Text trước bản fix có lỗi không, và bản fix có áp dụng cho Curve Text không? Chỉ chạy được căn giữa vì Curve Text không có tuỳ chọn căn lề (FEAT-12, KB-157); phạm vi bản fix cho Curve Text chưa được PO xác nhận.", "kb_ids": ["KB-156"]}
```

## OQ-artwork-128 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-128", "type": "OPEN_ISSUE", "feature_id": "text-color-sequence-render", "summary": "Text rainbow dùng font Carattere (font của case báo lỗi gốc) render thế nào trên Locate Artwork và Order Design PNG? Staging không có font này; mọi quan sát dùng font thay thế, nên case gốc chưa được tái hiện hay kiểm sau bản fix.", "kb_ids": ["KB-146", "KB-154"]}
```

## OQ-artwork-129 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-129", "type": "OPEN_ISSUE", "feature_id": "text-color-sequence-render", "summary": "Hành vi render text rainbow trên production sau khi TIB-5606 ship có giống quan sát trên staging không? TIB-5606 chưa ship; mọi item chỉ đúng cho build staging 2026-10-22 (build hash không rõ).", "kb_ids": ["KB-146", "KB-154", "KB-156"]}
```

## OQ-artwork-130 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-130", "type": "OPEN_ISSUE", "feature_id": "text-color-sequence-render", "summary": "Trước bản fix, text rainbow căn trái, text font thường và text 1 màu render thế nào — kết quả hiện tại có 'không đổi so với trước' không? Staging đã có bản fix khi chạy, không có baseline trước deploy; không phân biệt được hành vi mới và hành vi cũ.", "kb_ids": ["KB-147", "KB-150"]}
```

## OQ-artwork-131 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-131", "type": "OPEN_ISSUE", "feature_id": "text-color-sequence-render", "summary": "Design đã render trước khi deploy bản fix, khi Re-generate design cho order cũ, có đổi (cỡ chữ, vị trí) so với bản đã in không? Merchant regenerate order cũ có thể nhận ảnh khác bản đã in; trường hợp này chưa kiểm được vì không có order cũ.", "kb_ids": ["KB-149"]}
```

## OQ-artwork-132 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-132", "type": "OPEN_ISSUE", "feature_id": "text-color-sequence-render", "summary": "Nhánh font fallback của PNG renderer (ký tự không có trong font, emoji) với text rainbow hoạt động thế nào? Nhánh này chưa có quan sát nào tới được renderer; nếu fallback vẫn đo theo cách cũ, lỗi tràn/mất chữ có thể còn ở nhánh này. Lượt test staging 2026-10-22 không tới được nhánh này: ô nhập storefront bỏ emoji ngay lúc gõ (khớp ghi nhận emoji bị chặn mặc định), nên cần ký tự fallback lọt qua ô nhập (vd bật cho phép emoji) để kiểm.", "kb_ids": []}
```

## OQ-artwork-133 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-133", "type": "OPEN_ISSUE", "feature_id": "text-color-sequence-render", "summary": "SVG/vector export (vectorize) của text rainbow có cùng hành vi căn lề và độ rộng như Order Design PNG không? Chưa tải được file vector nào để kiểm; không biết renderer SVG có cùng lỗi gốc hay đã được sửa.", "kb_ids": []}
```

## OQ-artwork-134 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-134", "type": "OPEN_ISSUE", "feature_id": "text-color-sequence-render", "summary": "Ngoài Locate Artwork và Order Design PNG, những ảnh nào khác (thumbnail, mockup render phía server, ảnh product) có render text rainbow và có bị lỗi gốc ảnh hưởng không? Phạm vi ảnh bị ảnh hưởng chưa được xác nhận bằng quan sát hay nguồn thẩm quyền; checklist có thể bỏ sót surface.", "kb_ids": []}
```

## OQ-artwork-135 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-135", "type": "OPEN_ISSUE", "feature_id": "text-color-sequence-render", "summary": "Warp Text dùng Color Sequence và sequence màu do buyer chọn (Populate Color) render thế nào trên ảnh in? Hai tổ hợp này chưa được kiểm; chưa biết bản fix có bao phủ không.", "kb_ids": []}
```

## OQ-artwork-136 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-136", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-text", "summary": "Layer Curve Text không có tuỳ chọn căn lề text (lưu align center) là thiết kế có chủ đích hay là tính năng còn thiếu? Quyết định checklist coi việc thiếu căn lề là đúng hay là gap; ảnh hưởng phạm vi kiểm render Curve Text rainbow (hiện chỉ kiểm được căn giữa).", "kb_ids": ["KB-157"]}
```

## OQ-artwork-137 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-137", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-text", "summary": "Nút 'Align' trên canvas toolbar khi chọn layer curve-text (KB-042 của editor-layer-workspace) là căn vị trí layer trên canvas hay căn lề text? Nếu 'Align' là căn lề text, KB-157 ('không có tuỳ chọn căn lề') có thể sai và Curve Text căn phải dựng được; nếu là căn vị trí layer, hai item không mâu thuẫn.", "kb_ids": ["KB-157"]}
```

## OQ-artwork-138 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-138", "type": "NEEDS_CONFIRMATION", "feature_id": "group-layer-effective-visibility", "summary": "Group ẩn: mục Mask/nút Edit mask biến mất khỏi quick toolbar (quan sát TC-TIB-6060, 2026-10-16) trong khi expectedResult của case và R16 trong file RA/đáp án Slack Q6d (không ghi người trả lời) ghi 'disable'. Cần PO chốt: ẩn hay disable. Ghi chú QA local cũ (2026-09-30: Group ẩn vẫn có Edit mask) đã lỗi thời và không thuộc KB base.", "kb_ids": ["KB-167"]}
```

## OQ-artwork-139 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-139", "type": "OPEN_ISSUE", "feature_id": "group-layer-effective-visibility", "summary": "Render phía server (print file / render-design-preview) cho layer hoặc Group thiếu key visible chưa được đối chiếu — bước 3 của TC-TIB-6055 không chạy (không có tool server-side trong phiên). KB-166 chỉ phủ canvas editor + Live preview portal.", "kb_ids": ["KB-166"]}
```

## OQ-artwork-140 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-140", "type": "OPEN_ISSUE", "feature_id": "group-layer-effective-visibility", "summary": "Q11 (treo): fixture 'Group ẩn + con visible:true' dùng cho phần lớn test case được dựng qua MCP/API, chưa được PO/dev xác nhận là dữ liệu hợp lệ; repair command artwork:show-hidden-groups-with-visible-children đã chạy nên dữ liệu thật có thể không còn trạng thái này.", "kb_ids": ["KB-158", "KB-159", "KB-162", "KB-163", "KB-168"]}
```

## OQ-artwork-141 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-141", "type": "OPEN_ISSUE", "feature_id": "group-layer-effective-visibility", "summary": "Q10(b) (treo): Artwork 1.0 có hỗ trợ Group không — chưa thử; các item về effective visibility của run này chỉ phủ Artwork 2.0.", "kb_ids": ["KB-158"]}
```

## OQ-artwork-142 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-142", "type": "OPEN_ISSUE", "feature_id": "group-layer-effective-visibility", "summary": "Các mục 'Not for QA' trong QA plan của dev (#54766) chưa có test và không được nạp: dependency trên Group bị bỏ qua; layer trỏ tới Group không tồn tại render ở top level; MCP form preview khớp storefront form; command repair artwork:show-hidden-groups-with-visible-children.", "kb_ids": ["KB-158", "KB-168"]}
```

## OQ-artwork-143 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-143", "type": "NEEDS_CONFIRMATION", "feature_id": "group-layer-effective-visibility", "summary": "Ẩn hết mọi con thì Group vẫn ON và canvas không vẽ gì — hành vi có đúng như QA plan dev khi chạy TC-TIB-6159/6160 không?", "kb_ids": ["KB-161"]}
```

## OQ-artwork-144 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-144", "type": "OPEN_ISSUE", "feature_id": "group-layer-effective-visibility", "summary": "TIB-5584 đã deploy production ở bản release nào, và hành vi có giữ nguyên trên build sau khi 3 PR còn mở lúc 16:14 16/10 được merge không?", "kb_ids": ["KB-158", "KB-159", "KB-162", "KB-168"]}
```

## OQ-artwork-145 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-145", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "summary": "Group ẩn: quick toolbar vẫn hiển thị mục Align với 6 nút không disable, bấm không tác dụng (TC-TIB-6058/6059, staging 2026-10-16). QA plan dev (#54766 mục A bước 6) ghi 'quick toolbar offers no transform or align' và expectedResult TC-TIB-6059 ghi 'Align không khả dụng'. Quan sát cùng lượt: quick toolbar của Group ẩn không thấy Print Effects và Mask (KB-170). Cần PO chốt khi Group ẩn thì Align và Print Effects nên ẩn, disable hay hiển thị (Mask hỏi riêng ở OQ-artwork-138). Không phải conflict với KB base (KB-042 không nói về Group ẩn).", "kb_ids": ["KB-170"]}
```

## OQ-artwork-146 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-146", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "summary": "Khi Group đang ẩn, chọn một layer con trong layer panel có hiện box transform không, và các hành vi chọn/kéo theo QA plan dev có đúng khi chạy TC-TIB-6161/6162 không?", "kb_ids": ["KB-171", "KB-172"]}
```

## OQ-artwork-147 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-147", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-common-config", "summary": "layer_display chỉ đặt ở Group (con null, dữ liệu tạo qua JSON/API) thì storefront không áp cascade — đây là hành vi đúng (dữ liệu ngoài đường editor không được hỗ trợ) hay lỗi?", "kb_ids": ["KB-175"]}
```

## OQ-artwork-148 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-148", "type": "OPEN_ISSUE", "feature_id": "layer-common-config", "summary": "Print file (order design) của Group đặt display 'Design only' có chứa nội dung con như kỳ vọng không?", "kb_ids": ["KB-174"]}
```

## OQ-artwork-149 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-149", "type": "OPEN_ISSUE", "feature_id": "artwork-template-management", "summary": "Q9 (treo): linked template đã có cờ visible cụ thể (true/false) rồi global template đổi — linked đổi theo hay giữ riêng? KB-176/177 chỉ phủ null-kế thừa và bật lại ở linked; không suy ra trường hợp này.", "kb_ids": ["KB-176", "KB-177"]}
```

## OQ-artwork-150 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-150", "type": "OPEN_ISSUE", "feature_id": "psd-import", "summary": "Artwork import từ PSD có folder ẩn: storefront (form/preview) và print file chưa được kiểm (TC-TIB-6078 chỉ kiểm layer panel, canvas và response API). Liên quan OQ-artwork-120 (import PSD với paragraph nhiều lớp stroke).", "kb_ids": ["KB-178"]}
```

## OQ-artwork-151 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-151", "type": "OPEN_ISSUE", "feature_id": "psd-import", "summary": "Các phần khác của luồng PSD import (Multiple template, folder lồng nhiều cấp, mapping loại layer, file lỗi) hoạt động thế nào?", "kb_ids": ["KB-178"]}
```

## OQ-artwork-152 — CONFLICT

```json
{"oq_id": "OQ-artwork-152", "type": "CONFLICT", "feature_id": "layer-condition-value-binding", "summary": "Shape dependency của layer có điều kiện sau tính năng Hide đang mâu thuẫn: KB-067 (base) mô tả {match_type, show_by_default, dependencies}, còn KB-227 (test case PASS 2026-10-28 trên staging, trước khi các PR merge) cho thấy bản lưu mới có thêm key action ('hide'/'show') và bản ghi cũ không có action được hiểu là Show. PO chọn: (a) thay KB-067 bằng KB-227, (b) giữ cả hai như hai thời điểm dữ liệu (KB-067 thu phạm vi thành 'bản ghi trước tính năng Hide'), hay (c) giữ base? Cho tới khi chốt, mọi check oracle tầng API/data dựa vào shape dependency không có expected.", "kb_ids": ["KB-067", "KB-227"], "side_a": "KB-067 (base, quan sát 2026-09-10): layer có condition có dependency = {match_type: 'all'|'any', show_by_default: boolean, dependencies: [{element, value},...]}.", "side_b": "KB-227 (test case PASS 2026-10-28, staging lượt đầu): PUT gửi dependency có key action 'hide'/'show' cùng match_type, show_by_default, dependencies; bản ghi cũ không có key action được hiểu là Show, không bị migrate."}
```

## OQ-artwork-153 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-153", "type": "NEEDS_CONFIRMATION", "feature_id": "conditional-setting-config", "summary": "Trên build đã merge, chọn Hide có đổi tooltip match type thành 'hide when all / any options are selected' và toggle 'Hide this layer on first load' có nhãn/tooltip riêng không; chuyển lại Show có khôi phục nhãn cũ không? Nguồn duy nhất là tài liệu dev viết trước khi code còn đổi, chưa test case nào kiểm.", "kb_ids": ["KB-223"]}
```

## OQ-artwork-154 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-154", "type": "NEEDS_CONFIRMATION", "feature_id": "conditional-setting-config", "summary": "Bulk apply Conditional setting trên build đã merge có dropdown Show/Hide và áp đúng action cho mọi layer được chọn (kể cả khi các layer đang mang action khác nhau) không? Chỉ có nguồn tài liệu dev, chưa test case nào.", "kb_ids": ["KB-225"]}
```

## OQ-artwork-155 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-155", "type": "NEEDS_CONFIRMATION", "feature_id": "conditional-setting-config", "summary": "Conditional Setting (Show/Hide) có được hỗ trợ ở cấp Group không? Ghi nhận tay của QA trái expected của test case và BUG-436 còn gắn; nếu có hỗ trợ thì UI đặt ở đâu, nếu không thì điều kiện chỉ đặt cho từng layer con.", "kb_ids": ["KB-226"]}
```

## OQ-artwork-156 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-156", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "summary": "Trên build đã merge, import artwork, copy/paste layer (trong artwork và sang artwork 2.0 khác) và global template replica có giữ action Hide không; import từ file export định dạng v1 xử lý action thế nào? Chỉ có nguồn tài liệu dev, chưa test case nào chạy.", "kb_ids": ["KB-230"]}
```

## OQ-artwork-157 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-157", "type": "OPEN_ISSUE", "feature_id": "layer-duplicate-link-copy", "summary": "'Duplicate & Link options' trên layer có action Hide: bản LINKED/PLAIN_COPY có mang action và điều kiện của layer gốc không? Chưa có evidence cho chính thao tác này với layer Hide.", "kb_ids": ["KB-230"]}
```

## OQ-artwork-158 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-158", "type": "OPEN_ISSUE", "feature_id": "layer-condition-value-binding", "summary": "Khi action = 'hide', key show_by_default (giữ tên cũ) mang nghĩa 'Hide this layer on first load' — đây là thiết kế chủ đích của data model hay chỉ là cách hiển thị của editor/SDK? API có chấp nhận giá trị action nào khác ngoài 'hide'/'show' không?", "kb_ids": ["KB-227"]}
```

## OQ-artwork-159 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-159", "type": "OPEN_ISSUE", "feature_id": "condition-cycle-validation", "summary": "Dòng 'Conditions haven't been finished' đi kèm thông báo vòng điều kiện ở test Hide/Show là do fixture (điều kiện chưa hoàn tất) hay luôn xuất hiện khi có vòng? Quyết định phần nào của thông báo được dùng làm expected nguyên văn.", "kb_ids": ["KB-228"]}
```

## OQ-artwork-160 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-160", "type": "OPEN_ISSUE", "feature_id": "artwork-list-management", "summary": "Khi duplicate artwork có điều kiện, element trong dependencies của bản copy có được map sang layer id của chính bản copy (không trỏ về layer của artwork gốc) không? Test case duplicate không ghi tường minh việc map element.", "kb_ids": ["KB-229"]}
```

## OQ-artwork-161 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-161", "type": "OPEN_ISSUE", "feature_id": "conditional-setting-config", "summary": "Các hành vi Show/Hide ở portal (dropdown action, một action mỗi layer, Artwork 1.0 và Convert to 2.0, vòng điều kiện giữa layer Hide, Duplicate artwork giữ action — KB-221, KB-222, KB-224, KB-228, KB-229) có giữ nguyên trên build staging sau khi 6 PR của TIB-5558 merge (2026-10-29) và trên production khi TIB-5558 release không? Kèm theo: layer của artwork 1.0 sau Convert to 2.0 và layer cũ không có key action có ẩn/hiện đúng chiều Show trên storefront chạy SDK đã có code Hide không — lượt test duy nhất cho phần storefront này chạy trên SDK bản 2026-10-14 chưa có code Hide nên chưa xác minh.", "kb_ids": ["KB-221", "KB-222", "KB-224", "KB-228", "KB-229"]}
```

## OQ-artwork-162 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-162", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "PO quyết: các test case Testlane PASS trên staging (2026-10-21/22, trước khi 7 PR TIB-5580 merge) khẳng định cùng hành vi với 11 item quan sát KB-129, KB-130, KB-131, KB-132, KB-134, KB-135, KB-136, KB-137, KB-140, KB-141, KB-143 (stack tối đa 3 lớp, width từng vòng, xoá/đổi thứ tự, paragraph mới 1 row, góc round, tắt stroke giữ stroke_layers, convert sang Text/Curve/Warp, stroke legacy, Custom Shape 1 stroke, regression Text 1 dòng). teeinblue không bật supersede nên các item vẫn là OBSERVED_CURRENT/LOW và các check liên quan chưa có expected xác nhận. PO chọn: (a) nâng các hành vi này thành expected, (b) giữ là quan sát, hay (c) giữ cả hai như hai thời điểm? Cặp convert sang Curve/Warp làm mất các lớp ngoài (KB-137) có ảnh hưởng cao.", "kb_ids": ["KB-129", "KB-130", "KB-131", "KB-132", "KB-134", "KB-135", "KB-136", "KB-137", "KB-140", "KB-141", "KB-143"]}
```

## OQ-artwork-163 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-163", "type": "OPEN_ISSUE", "feature_id": "text-multi-stroke", "summary": "Chạy lại sau merge/production: mọi lượt test multi-stroke của Paragraph (TIB-5580) chạy trên staging 2026-10-21/22, trước khi 7 PR merge (2026-10-22); SDK staging lúc đó chưa có PR sdk #2124. Ticket đã Done 2026-10-22 nhưng việc ship production chưa xác nhận. Cần chạy lại trên build đã merge (staging) và production cho editor, dữ liệu lưu, PNG order design, SVG vectorize và preview storefront rồi gửi CCR mới.", "kb_ids": ["KB-129", "KB-130", "KB-131", "KB-132", "KB-133", "KB-134", "KB-135", "KB-136", "KB-137", "KB-138", "KB-139", "KB-140", "KB-141", "KB-142", "KB-143", "KB-144", "KB-251"]}
```

## OQ-artwork-164 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-164", "type": "NEEDS_CONFIRMATION", "feature_id": "text-multi-stroke", "summary": "Shadow của Paragraph có nhiều lớp stroke: PNG order design (API) vẽ 1 khối shadow cho cả paragraph, không lặp theo dòng, khớp preview Artwork Editor — có phải hành vi đúng không, và có giữ nguyên ở preview storefront và SVG vectorize khi SDK staging có code TIB-5580 và tải được SVG? Mới là quan sát bằng mắt trên 2 order (#1091, #1096) trong lượt test staging trước khi TIB-5580 merge, hai test case Blocked; check shadow paragraph (CHK-027) chưa có oracle xác nhận. Cần nguồn S3 (test case PASS đủ 3 renderer trên build có code, hoặc PO/dev xác nhận nguyên văn). Liên quan OQ-artwork-118.", "kb_ids": ["KB-251"]}
```

## OQ-artwork-165 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-165","type":"NEEDS_CONFIRMATION","feature_id":"group-layer-order-design-render","summary":"PO: ngưỡng thời gian chấp nhận cho generate order design của artwork có Group nhiều layer (~250) là bao nhiêu? Số đo hiện có (khoảng 33–68 giây) chỉ đo 1 lần mỗi fixture qua mốc thời gian Item Activity logs, không có baseline trước fix; ngưỡng 1–2 phút chưa được PO xác nhận. Không dùng số đo này làm SLA hay điều kiện pass/fail cho tới khi PO trả lời. Ngoài ra: order item hiển thị Ready/'Ready to fulfill' sau khi order design generate xong (chỉ thấy ở actualResult của TC-TIB-7614/7616, expectedResult không khẳng định) — có phải hành vi mong đợi không?","kb_ids":["KB-381"]}
```

## OQ-artwork-166 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-166","type":"NEEDS_CONFIRMATION","feature_id":"group-layer-order-design-render","summary":"Dev/PO: phần shadow của layer con vượt ra ngoài printarea bị cắt theo printarea trên order design — có phải hành vi mong đợi không? Chỉ thấy ở actualResult của TC-TIB-7617; expectedResult của case không khẳng định điều này.","kb_ids":["KB-384"]}
```

## OQ-artwork-167 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-167","type":"NEEDS_CONFIRMATION","feature_id":"group-layer-order-design-render","summary":"Hướng/vị trí shadow của layer con trong Group trên order design sau fix chưa được đối chiếu với bản trước fix (TC-TIB-7620 kiểm bằng mắt, offset của fixture khác test data). PO xác nhận hướng/vị trí shadow hiện thấy trên order design có phải ý định cho merchant và nhà in không; dev/QA đối chiếu toạ độ/pixel với bản trước fix.","kb_ids":["KB-385"]}
```

## OQ-artwork-168 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-168","type":"NEEDS_CONFIRMATION","feature_id":"group-layer-order-design-render","summary":"Dev/PO: text căn giữa khai báo cỡ 601 chỉ render cao khoảng 22px trên order design (có vẻ co theo box) — đúng hay lỗi? Text có thực sự tràn box của Group không; đường canvas mở rộng cho text tràn box chưa được chứng minh (TC-TIB-7619).","kb_ids":["KB-386"]}
```

## OQ-artwork-169 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-169","type":"NEEDS_CONFIRMATION","feature_id":"group-layer-order-design-render","summary":"Dev: ngưỡng route-large 150 Mpx đo trên canvas artwork hay trên printarea? Route-large (hàng đợi final-render-large) chưa được kích hoạt trong lượt chạy (printarea 72 Mpx) — cần fixture có printarea đủ lớn để kiểm.","kb_ids":["KB-390"]}
```

## OQ-artwork-170 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-170","type":"OPEN_ISSUE","feature_id":"group-layer-order-design-render","summary":"Chạy lại sau merge và trên production: lượt chạy test 2026-10-29 trên staging (build hash không rõ) diễn ra trước khi PR thứ hai của TIB-5633 cập nhật lần cuối 2026-10-30; ngày deploy production chưa rõ. Cần chạy lại bộ TIB-268 trên build đã merge và xác nhận trên production trước khi coi các item CONFIRMED của feature này là ổn định.","kb_ids":["KB-380","KB-381","KB-382","KB-383","KB-384","KB-385","KB-386","KB-387","KB-388","KB-389","KB-390"]}
```

## OQ-artwork-171 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-171","type":"OPEN_ISSUE","feature_id":"group-layer-order-design-render","summary":"Phạm vi render order design của Group nhiều layer chưa được kiểm: mask hình tròn/custom shape; order design PDF của Group có mask; Group khoảng 250 layer có layer tràn box (đường canvas mở rộng); layer chia ở 2 cấp Group (100 + 150); Group cha bị ẩn hoặc visibility theo điều kiện trong Group nhiều layer. Chưa có expected cho các nhánh này.","kb_ids":["KB-383","KB-386","KB-387","KB-388","KB-389"]}
```

## OQ-artwork-172 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-172","type":"OPEN_ISSUE","feature_id":"group-layer-order-design-render","summary":"Blend mode của layer con, layer gắn tag Context trong Group, và Artwork 1.0 chưa có quan sát nào cho render order design của Group nhiều layer (case liên quan bị bỏ qua, nguồn chưa đủ thẩm quyền). Hành vi mong đợi là gì và ai xác nhận?","kb_ids":[]}
```

## OQ-artwork-173 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-173","type":"NEEDS_CONFIRMATION","feature_id":"group-layer-order-design-render","summary":"PO xác nhận đây là hành vi đúng cho merchant và nhà in: order design của artwork có Group khoảng 250 layer generate hoàn tất (design Completed, không auto-stop/timeout, không kẹt Generating); print file của Group giống pixel bản không group; shadow/layer xoay tràn box hiện đủ trong vùng in; Group có mask chỉ hiện phần trong mask; Group lồng nhau không lệch layer; layer con tắt visible không xuất hiện. Các item này đến từ test case PASS trên staging, chưa có PO/business xác nhận ý định.","kb_ids":["KB-380","KB-382","KB-383","KB-387","KB-388","KB-389"]}
```

## OQ-artwork-174 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-174","type":"NEEDS_CONFIRMATION","feature_id":"layer-print-effects","summary":"Dev/PO: photo_border contour cut trên print file của Group có đi qua cùng đường xử lý với preset shape-cut của Print Effects (KB-044) không, và đường cắt đang thấy có phải ý định không? Group shape-cut khoảng 250 layer chưa được kiểm — fixture chỉ là Group 3 layer photo_border contour cut.","kb_ids":["KB-391","KB-044"]}
```

## OQ-artwork-175 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-175","type":"OPEN_ISSUE","feature_id":"layer-print-effects","summary":"Emboss áp cho Group nhiều layer chưa từng được chạy (case bị bỏ qua, nguồn chưa đủ thẩm quyền). Print file emboss của Group nên ra sao? Không suy ra gì về việc emboss có hay không trên account/plan hiện tại.","kb_ids":[]}
```

## OQ-artwork-176 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-176","type":"OPEN_ISSUE","feature_id":"layer-print-effects","summary":"Chạy lại sau merge và trên production cho print file photo_border contour cut của Group (lượt chạy 2026-10-29 trước khi PR thứ hai của TIB-5633 cập nhật lần cuối; ngày deploy production chưa rõ).","kb_ids":["KB-391"]}
```

## OQ-artwork-177 — CONFLICT

```json
{"oq_id":"OQ-artwork-177","type":"CONFLICT","feature_id":"text-color-sequence-render","conflict_group":"CONF-CBS-016-01","summary":"Text rainbow 32 ký tự bật autoscale, căn phải (staging, lượt chạy 2026-10-22): kết luận của kết quả test và số đo của chính lượt đó không khớp nhau về độ rộng Order Design PNG so với preview SDK. Độ rộng PNG sau autoscale so với preview SDK được kỳ vọng thế nào, dung sai chấp nhận là bao nhiêu? Hai item KB-149 và KB-404 đang UNRESOLVED, không bên nào là oracle. Quyết định này đi cùng quyết định của PO cho cặp KB-149 trong OQ-artwork-182.","side_a":{"kb_id":"KB-149","value":"Kết luận của kết quả test: Order Design PNG sau autoscale chênh 2px, không nhỏ hơn preview SDK."},"side_b":{"kb_id":"KB-404","value":"Số đo của cùng lượt chạy: PNG 495–910 (w=415), preview SDK 493–910 (w=417) — PNG hẹp hơn SDK 2px."},"kb_ids":["KB-149","KB-404"]}
```

## OQ-artwork-178 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-178","type":"NEEDS_CONFIRMATION","feature_id":"text-color-sequence-render","summary":"Số đo một lượt chạy: rainbow font Roboto căn phải PNG 560–905 so với preview SDK 558–904 (lệch 1–2px); text 1 màu font script PNG 624–912 so với SDK 624–913. Lệch 1–2px này có nằm trong dung sai chấp nhận và có lặp lại trên build sau merge / production không?","kb_ids":["KB-406"]}
```

## OQ-artwork-179 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-179","type":"NEEDS_CONFIRMATION","feature_id":"text-color-sequence-render","summary":"Theo mô tả dev (comment #55257, PR #4044), đoạn text dùng font fallback giữ cách đặt vị trí cũ của PNG renderer. Trên build đã merge, text rainbow có ký tự rơi vào font fallback render ra sao (đủ ký tự? khớp preview SDK?), và đây có phải hành vi mong muốn không?","kb_ids":["KB-412"]}
```

## OQ-artwork-180 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-180","type":"NEEDS_CONFIRMATION","feature_id":"text-color-sequence-render","summary":"Theo mô tả dev, preview / order design render trước khi deploy bản sửa TIB-5606 không tự cập nhật và phải regenerate. Đã kiểm trên staging/production chưa, và regenerate cho kết quả đúng (đủ ký tự, vị trí khớp preview SDK) không?","kb_ids":["KB-413"]}
```

## OQ-artwork-181 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-181","type":"NEEDS_CONFIRMATION","feature_id":"text-color-sequence-render","summary":"Theo mô tả dev, chỉ PNG renderer đổi; SVG renderer teeinblue-vectorize không bị ảnh hưởng và cho cùng hình glyph như text 1 màu. QA chưa tải được file vector trên staging — SVG của text rainbow căn phải có thật đủ ký tự, khớp preview SDK không?","kb_ids":["KB-414"]}
```

## OQ-artwork-182 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-182","type":"NEEDS_CONFIRMATION","feature_id":"text-color-sequence-render","summary":"PO quyết: các test case Testlane TIB-230 PASS trên staging (chạy 2026-10-22, trước khi PR teeinblue-api #4044 merge) khẳng định cùng hành vi với 10 item quan sát KB-146, KB-147, KB-148, KB-149, KB-150, KB-151, KB-152, KB-153, KB-155, KB-156 (rainbow căn phải/giữa/trái, độ rộng bằng text 1 màu, autoscale tên dài, Roboto và text 1 màu, letter spacing, kerning, stroke 1 lớp, RTL, Curve căn giữa). teeinblue không bật supersede nên các item vẫn là OBSERVED_CURRENT/LOW và các check liên quan chưa có expected xác nhận. PO chọn: (a) nâng các hành vi này thành expected, (b) giữ là quan sát, hay (c) giữ cả hai như hai thời điểm? Riêng KB-149: test case không xác nhận vế độ rộng autoscale so với preview SDK, nên quyết định cho KB-149 phải đi cùng OQ-artwork-177.","kb_ids":["KB-146","KB-147","KB-148","KB-149","KB-150","KB-151","KB-152","KB-153","KB-155","KB-156"]}
```

## OQ-artwork-183 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-183","type":"OPEN_ISSUE","feature_id":"text-color-sequence-render","summary":"Chạy lại sau merge/production: lượt chạy Testlane TIB-230 (staging 2026-10-22 14:20) diễn ra trước khi PR teeinblue-api #4044 merge (2026-10-22 15:44), chỉ trên font thay thế (Dancing Script/Roboto/Heebo); ngày ship production chưa xác nhận. Cần chạy lại trên build đã merge (staging) và production cho Locate Artwork và Order Design PNG (có số đo), rồi gửi CCR mới.","kb_ids":["KB-146","KB-147","KB-148","KB-149","KB-150","KB-151","KB-152","KB-153","KB-155","KB-156","KB-154","KB-404","KB-406","KB-412","KB-413","KB-414"]}
```

## OQ-artwork-184 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-184","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Role áp dụng của KB-420..KB-429 là gì (owner, staff hay buyer), cho từng item? scope.role đang là \"unspecified\" vì CCR ghi không rõ, checklist chưa biết chạy các item này với role nào. Câu hỏi chung cho ba feature: layer-config-image (KB-420..KB-424, CHK-054..CHK-059), layer-print-effects (KB-425, CHK-011, CHK-012), editor-layer-workspace (KB-426..KB-429, CHK-019..CHK-023).","kb_ids":["KB-420","KB-421","KB-422","KB-423","KB-424","KB-425","KB-426","KB-427","KB-428","KB-429"]}
```

## OQ-artwork-185 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-185","type":"OPEN_ISSUE","feature_id":"layer-config-image","summary":"KB-415..KB-429 chưa biết build và ngày deploy production. TIB-5212, TIB-5465, TIB-5516 là Done trên Jira, Done không chứng minh đã lên production; bản đối chiếu không ghi status của TIB-5512, TIB-5534, TIB-5538, TIB-5539. Trong lúc đó các item chỉ dùng cho staging. Áp cho bảy feature có item mới của CBS-079, không riêng layer-config-image.","kb_ids":["KB-415","KB-416","KB-417","KB-418","KB-419","KB-420","KB-421","KB-422","KB-423","KB-424","KB-425","KB-426","KB-427","KB-428","KB-429"]}
```

## OQ-artwork-186 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-186","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-others","summary":"Calendar giữ default typography Heebo/regular có phải giá trị đúng không? TC-TIB-4853 và actual của TC-TIB-4858 ghi Heebo, expected của TC-TIB-4858 ghi Heebo chuyển Roboto. Cần PO hoặc Dev xác nhận nguyên văn, có ngày; hoặc test case PASS có build.","kb_ids":["KB-415"]}
```

## OQ-artwork-187 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-187","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-text","summary":"PO xác nhận: ba nhánh của KB-416 có phải hành vi đúng không — paragraph rỗng không render trong design, chỉ khoảng trắng thì preview và design trống, xoá field nguồn populate thì preview về default text? Theo CCR, mô tả TIB-5538 ghi \"should fall back to its default text\", khác kết quả. Rủi ro cao vì ảnh hưởng nội dung design của buyer.","kb_ids":["KB-416"]}
```

## OQ-artwork-188 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-188","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-vector","summary":"Upload .svg qua Static Vector tạo layer static-vector và còn sau reload có phải hành vi đúng không? Mới có một lượt chạy (TC-TIB-5705, 2026-10-14), record không ghi build.","kb_ids":["KB-417"]}
```

## OQ-artwork-189 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-189","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-vector","summary":"PO xác nhận: các kết quả Design format của KB-418 có đúng không (chỉ static-vector + SVG ra file .svg; PNG_RGB báo \"Line item cannot generate design\"; lưu SVG khi còn raster layer trả HTTP 400), và SVG có phải format đúng duy nhất cho artwork chỉ có static-vector không?","kb_ids":["KB-418"]}
```

## OQ-artwork-190 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-190","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-maps-astronomy","summary":"Strava trong Route Maps (strava-upload) có thật sự không chạy được trên môi trường test không, lý do là gì, và production hoạt động thế nào? Nguồn của KB-419 chỉ là ghi chú ngôi thứ ba.","kb_ids":["KB-419"]}
```

## OQ-artwork-191 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-191","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Per-field warning và nút \"+ variable\" có nhận title của layer Global Option không? Comment dev #55232 của TIB-5465 nói cùng rule match; ghi chú QA audit #40 nói không nhận và lỗi có cả trên production. KB-424 chỉ phát biểu về warning \"Some ImagenHub variables have no matching layer\".","kb_ids":["KB-424"]}
```

## OQ-artwork-192 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-192","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Route POST /layer-images/create-master-large/batch, env MASTER_LARGE_BATCH_LIMIT (mặc định 10) và status 422 khi quá limit có đúng trên build hiện tại không? Nguồn là comment #54785 của TIB-5212 tự sinh từ branch diff, chưa kiểm trên hệ thống; comment #55717 không phát biểu lại các điểm này. Cần Dev xác nhận nguyên văn, có ngày; hoặc test case PASS có build.","kb_ids":["KB-422"]}
```

## OQ-artwork-193 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-193","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"PO xác nhận ý định của KB-427: khi multi-select có giá trị Photo Border khác nhau, bật toggle Border thay các giá trị riêng của mọi layer đang chọn, và đổi một thuộc tính cũng bật border cho cả selection. Liên quan CHK-020.","kb_ids":["KB-427"]}
```

## OQ-artwork-194 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-194","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Rule \"chọn một group: ẩn Photo Border, Shadow và HD vẫn hiện\" của KB-429 có áp cho Group đang ẩn không? KB-429 không nêu trạng thái group; KB-170 quan sát Group ẩn chỉ còn mục Align, expected của trường hợp đó chưa chốt. CHK-022 chỉ kiểm Group hiện, chưa check nào assert Group ẩn.","kb_ids":["KB-429","KB-170"]}
```

## OQ-artwork-195 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-195","type":"NEEDS_CONFIRMATION","feature_id":"layer-print-effects","summary":"Sau khi bỏ file pre-render của border custom_shape, order design (print file) lấy border từ đâu, và border size có đúng không? Comment #53942 chỉ nói SDK vẽ trên canvas; scope.surface của KB-425 ghi \"render\" chung, CHK-011, CHK-012 không kiểm print file. Nếu print file đổi đường xử lý thì KB-425 phải lên impact HIGH.","kb_ids":["KB-425"]}
```

## OQ-artwork-196 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-196","type":"NEEDS_CONFIRMATION","feature_id":"svg-to-image-rendering","summary":"KB-570: design PNG của artwork có layer SVG clip-path lồng nhiều cấp vẽ đúng hình đã mask ở cả 4 format PNG_*, theo dev doc auto-generated; quan sát mới có ở PNG_RGB. Đây có phải hành vi đúng ở cả PNG_RGBA, PNG_ADOBE_RGB, PNG_SRGB không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-001, CHK-002.","kb_ids":["KB-570"]}
```

## OQ-artwork-197 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-197","type":"NEEDS_CONFIRMATION","feature_id":"svg-to-image-rendering","summary":"KB-571: chỉ nhánh PNG đổi sang resvg, EPS/AI/PDF vẫn qua Inkscape, theo dev doc auto-generated; EPS và AI chưa có quan sát. Có xác nhận được export EPS/AI/PDF vẫn hoạt động như trước không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-003.","kb_ids":["KB-571"]}
```

## OQ-artwork-198 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-198","type":"NEEDS_CONFIRMATION","feature_id":"svg-to-image-rendering","summary":"KB-572: SVG có <image href=\"data:…\"> (href trần) vẫn hiện ảnh nhúng ở thumbnail và design PNG, theo dev doc auto-generated. Đây có phải hành vi đúng không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-004.","kb_ids":["KB-572"]}
```

## OQ-artwork-199 — CONFLICT

```json
{"oq_id":"OQ-artwork-199","type":"CONFLICT","feature_id":"svg-to-image-rendering","summary":"Nền design file PNG_RGB, PNG_ADOBE_RGB, PNG_SRGB khi render SVG: tài liệu dev và số đo staging nói ngược nhau. Nền đúng của từng format PNG_* là gì? Chờ PO/Dev trả lời câu hỏi PENDING-09 của bộ test QA-3395; số đo phía side_b cũng cần lặp lại trên build ghi rõ. Hai item UNRESOLVED, không làm oracle; CHK-008 chỉ ghi nhận, không kết luận.","side_a":"Dev doc auto-generated của PR teeinblue-api #3836 (2026-09-23, KB-573): PNG_RGB, PNG_ADOBE_RGB, PNG_SRGB nền trắng đục, giữ như mặc định Inkscape cũ; PNG_RGBA nền trong suốt.","side_b":"Lượt đo QA trên staging 2026-10-07 (KB-574, mỗi format một order, không ghi build): PNG_RGB, PNG_ADOBE_RGB, PNG_SRGB là PNG RGBA nền trong suốt (pixel góc alpha 0), giống một order PNG_RGB trước fix.","kb_ids":["KB-573","KB-574"]}
```

## OQ-artwork-200 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-200","type":"NEEDS_CONFIRMATION","feature_id":"svg-to-image-rendering","summary":"KB-573: theo dev doc auto-generated, PNG_RGBA có nền trong suốt; PNG_RGBA chưa được thử (TC-09 tạm dừng). Đây có phải hành vi đúng không? (Phần PNG_RGB/ADOBE_RGB/SRGB xem OQ-artwork-199.) Cần PO xác nhận (ảnh hưởng file in).","kb_ids":["KB-573"]}
```

## OQ-artwork-201 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-201","type":"NEEDS_CONFIRMATION","feature_id":"svg-to-image-rendering","summary":"KB-575: design PNG_ADOBE_RGB nhúng ICC \"Adobe RGB (1998)\" và PNG_SRGB nhúng ICC \"sRGB IEC61966-2.1\", một mẫu mỗi format ngày 2026-10-07. Đây có phải hành vi đúng không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-007.","kb_ids":["KB-575"]}
```

## OQ-artwork-202 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-202","type":"NEEDS_CONFIRMATION","feature_id":"svg-to-image-rendering","summary":"KB-576: clip-path trỏ id không tồn tại thì shape không bị clip, clip-path khai qua CSS style vẫn clip đúng ở thumbnail, quan sát một lượt 2026-10-07. Đây có phải hành vi đúng không? Liên quan CHK-005, CHK-006.","kb_ids":["KB-576"]}
```

## OQ-artwork-203 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-203","type":"OPEN_ISSUE","feature_id":"svg-to-image-rendering","summary":"Design file và thumbnail của SVG được sinh lúc nào, do sự kiện gì (tạo order, upload, regenerate thủ công)? KB-570..576 không mô tả trigger, nên check của feature này chưa có bước dựng đầu ra rõ ràng.","kb_ids":[]}
```

## OQ-artwork-204 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-204","type":"OPEN_ISSUE","feature_id":"svg-to-image-rendering","summary":"Chạy lại trên build ghi rõ và production: mọi lượt chạy làm nguồn cho KB-570..584 (staging 2026-10-07/08, AI chạy) không ghi build, CCR ghi SHIPPED nhưng chưa có bằng chứng production; role khác merchant-owner và cross-tenant chưa quan sát. Cần lượt chạy có build (hoặc nguồn PO/Dev nguyên văn) rồi gửi CCR mới để nâng các item này.","kb_ids":["KB-570","KB-571","KB-572","KB-573","KB-574","KB-575","KB-576","KB-577","KB-578","KB-579","KB-580","KB-581","KB-582","KB-583","KB-584"]}
```

## OQ-artwork-205 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-205","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-puzzles","summary":"KB-577: Word Cloud với shape SVG clip-path lồng nhiều cấp chỉ đặt chữ trong vùng đã mask, quan sát một lượt 2026-10-07; chưa so preview storefront/editor với final render. Đây có phải hành vi đúng không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-006.","kb_ids":["KB-577"]}
```

## OQ-artwork-206 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-206","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-puzzles","summary":"KB-578: Word Cloud bật \"Use shape's color\" trên shape SVG clip-path chỉ lấy màu từ vùng nhìn thấy, quan sát một lượt 2026-10-07. Đây có phải hành vi đúng không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-007.","kb_ids":["KB-578"]}
```

## OQ-artwork-207 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-207","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-puzzles","summary":"KB-579: Word Cloud với shape SVG đơn giản, shape PNG lấp chữ trong shape, tắt custom shape thì lấp đầy ô vuông, quan sát một lượt 2026-10-07 không có baseline trước fix. Đây có phải hành vi đúng không? Liên quan CHK-008.","kb_ids":["KB-579"]}
```

## OQ-artwork-208 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-208","type":"OPEN_ISSUE","feature_id":"layer-config-puzzles","summary":"Preview Word Cloud trên storefront và artwork editor với shape SVG clip-path lồng nhiều cấp có khớp final render (design PNG) không? Lượt test tương ứng đang tạm dừng; KB-577, KB-578 chỉ nói về final render.","kb_ids":["KB-577","KB-578"]}
```

## OQ-artwork-209 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-209","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-others","summary":"KB-580: layer QR Code render nguyên vẹn và decode đúng chuỗi ở cả design PNG và PDF của cùng đơn, quan sát một lượt 2026-10-07. Đây có phải hành vi đúng không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-007.","kb_ids":["KB-580"]}
```

## OQ-artwork-210 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-210","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-vector","summary":"KB-581: SVG layer image upload 05/2025 re-render design PNG bình thường, mẫu 3 file ngày 2026-10-07. Đây có phải hành vi đúng không, kể cả SVG cũ có <text> sống? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-012.","kb_ids":["KB-581"]}
```

## OQ-artwork-211 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-211","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-vector","summary":"KB-582: upload SVG làm layer image thì bản lưu bỏ DOCTYPE, ENTITY, <script> và không trả 500, quan sát một lượt 2026-10-07; SSRF, DoS, file cực lớn chưa kiểm. Đây có phải hành vi đúng không? Cần PO xác nhận (bảo mật). Liên quan CHK-013.","kb_ids":["KB-582"]}
```

## OQ-artwork-212 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-212","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-vector","summary":"KB-583: tên file SVG upload được làm sạch, key lưu ngẫu nhiên, tên > 255 ký tự bị validate chặn, quan sát một lượt 2026-10-07 qua API. Đây có phải hành vi đúng không, và UI hiển thị tên ra sao? Cần PO xác nhận (bảo mật). Liên quan CHK-014, CHK-015.","kb_ids":["KB-583"]}
```

## OQ-artwork-213 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-213","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-vector","summary":"KB-584: file SVG nguồn trên CDN giữ nguyên tập id, không prefix svg- sau recolor và đặt order, 2 file mẫu ngày 2026-10-08. Đây có phải hành vi đúng không? Liên quan CHK-016.","kb_ids":["KB-584"]}
```

## OQ-artwork-214 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-214","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-vector","summary":"KB-418 (lượt chạy 2026-10-14) ghi artwork chỉ có layer static-vector, Design format PNG_RGB thì order báo \"Line item cannot generate design\"; KB-570 và KB-581 (lượt chạy 2026-10-07) thấy design PNG của artwork có layer SVG render bình thường. Nguồn không nói artwork của hai lượt khác nhau ở điểm nào (có layer raster hay không). Đây là hai fixture khác nhau hay một hành vi chưa ổn định? Liên quan OQ-artwork-189, CHK-010.","kb_ids":["KB-418","KB-570","KB-581"]}
```

## OQ-artwork-215 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-215","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Một lượt chạy dùng ảnh gốc full-resolution, áp effect tuần tự, progress dừng 95%, all or nothing: chỉ có dev doc tự sinh (2026-10-08). Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-802"]}
```

## OQ-artwork-216 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-216","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Chạy thành công thay ảnh layer (một bước undo), lưu ảnh mới vào image library, ảnh cũ giữ nguyên: chỉ có dev doc tự sinh (2026-10-08). Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-803"]}
```

## OQ-artwork-217 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-217","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Chạy lại lấy ảnh hiện tại; đổi cấu hình effect không tự cập nhật ảnh: mục spec không xác định được người viết/ngày. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-806"]}
```

## OQ-artwork-218 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-218","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Toast \"Could not run effects\" 10 giây và warning layer không còn trong template: chỉ có dev doc tự sinh. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-811"]}
```

## OQ-artwork-219 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-219","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Double-click Run effects chỉ một lượt: chỉ có quan sát TC-79, câu nguồn nằm ở Possible test cases. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-812"]}
```

## OQ-artwork-220 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-220","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Danh sách dịch vụ được kiểm API key trước khi chạy và kiểm lại phía server: chỉ có dev doc tự sinh. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-816"]}
```

## OQ-artwork-221 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-221","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Vế phụ CLAIM-08: đóng layer editor/chọn layer khác/mở lại artwork khi đang chạy không mất lượt chạy, progress bar hiện lại: chỉ từ dev doc tự sinh. Cần: PO hoặc Dev xác nhận nguyên văn vế này (có ngày, có link). Đây có phải hành vi đúng không?","kb_ids":["KB-808"]}
```

## OQ-artwork-222 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-222","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Vế phụ CLAIM-09: chữ toast \"Timed out waiting for the effects to finish.\" và quy tắc hàng đợi không tính vào 6 phút: chỉ từ dev doc tự sinh. Cần: PO hoặc Dev xác nhận nguyên văn vế này (có ngày, có link). Đây có phải hành vi đúng không?","kb_ids":["KB-810"]}
```

## OQ-artwork-223 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-223","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Vế phụ CLAIM-12: 5 lượt/phút/store dùng chung owner + staff, đổi được trong server config, tính vào giới hạn upload layer image: chỉ từ dev doc tự sinh. Cần: PO hoặc Dev xác nhận nguyên văn vế này (có ngày, có link). Đây có phải hành vi đúng không?","kb_ids":["KB-814"]}
```

## OQ-artwork-224 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-224","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Vế hover style của nút Run effects (nền primary blue, chữ trắng) đã bỏ khỏi KB: chỉ dựa mục spec \"Run effects\" trong description TIB-5470, không xác định được người viết/ngày. Cần: PO xác nhận nguyên văn style hover của nút Run effects. Đây có phải hành vi đúng không?","kb_ids":["KB-801"]}
```

## OQ-artwork-225 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-225","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Vế bỏ khỏi CLAIM-05: bật lại HD sau khi chạy thì HD dựng từ ảnh đã xử lý; chỉ có trong dev doc tự sinh, chưa quan sát (TC-09 tạm dừng). Cần: Dev/PO xác nhận nguyên văn và QA quan sát khi bật lại HD sau lượt chạy. Đây có phải hành vi đúng không? Quan hệ với KB-421/KB-423 (HD dựng từ ảnh trong image library) chưa rõ.","kb_ids":["KB-804"]}
```

## OQ-artwork-226 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-226","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"Vế bỏ khỏi CLAIM-08: reload trang khi đang chạy (progress bar mất, layer không bị thay, ảnh vẫn vào library); nguồn là mục Possible test cases, TC-14..16 không có kết quả có ngày. Cần: Dev/PO xác nhận nguyên văn hành vi khi reload trang lúc đang chạy. Đây có phải hành vi đúng không?","kb_ids":["KB-807"]}
```

## OQ-artwork-227 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-227","type":"OPEN_ISSUE","feature_id":"run-image-effects","summary":"Known limitation: chuỗi có cả Remove background và Face cutout vẫn đòi key Remove background dù server bỏ qua Remove background; workaround xoá effect Remove background. PO chỉ chấp nhận cho release (ok Q5, 2026-10-14); TC-31 tạm dừng. Cần: Ticket theo dõi việc sửa, hoặc PO xác nhận giữ giới hạn này lâu dài.","kb_ids":["KB-818"]}
```

## OQ-artwork-228 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-228","type":"OPEN_ISSUE","feature_id":"run-image-effects","summary":"Điều kiện hiển thị nút Run effects chưa kiểm hết: store Etsy chưa có lượt kiểm (TC-03 not-run); Linked/No customization mới kiểm 2/4 layer (TC-80 tạm dừng). Cần: QA chạy TC-03 trên store Etsy và hoàn tất TC-80.","kb_ids":["KB-800"]}
```

## OQ-artwork-229 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-229","type":"OPEN_ISSUE","feature_id":"run-image-effects","summary":"Face Cutout và Photo Enhancer có cần API key trước khi chạy hay không: chưa ai trả lời (PENDING-12). Cần: Dev trả lời nguyên văn Face Cutout / Photo Enhancer có nằm trong danh sách kiểm key không. Bổ sung CBS-140 (2026-11-11): spec-hub rule image-effects-needs-key (S2, KB-985) chỉ nói effect của dịch vụ ngoài cần key và effect của Teeinblue không cần key, không nói Face cutout thuộc loại nào; câu hỏi vẫn mở.","kb_ids":["KB-816"]}
```

## OQ-artwork-230 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-230","type":"OPEN_ISSUE","feature_id":"run-image-effects","summary":"Liên hệ object image-library (không sửa ở run này): image-library KB-012 đang ghi quota theo ngày là suy đoán (CHK-041, OQ-image-library-023), trong khi Dev Q10 nêu default 1000 ảnh/ngày/store cho giới hạn upload khi chạy effect. Khác sdk KB-051 (rate limit buyer). Cần: Đối chiếu ở run của object image-library; không đổi item image-library ở đây. Cũng chưa rõ chu kỳ theo ngày lịch hay cửa sổ trượt, và giới hạn 5 lượt/phút của portal có dùng chung limiter với sdk KB-051 (buyer, storefront) không.","kb_ids":["KB-813","KB-814"]}
```

## OQ-artwork-231 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-231","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"KB-815 (quyền, Dev Q4 2026-10-14): Manage Artwork là quyền duy nhất cần để chạy Run effects, staff không có quyền không mở được artwork editor và server từ chối lượt chạy. Item đã CONFIRMED_EXPECTED nhưng thuộc chủ đề permission (rủi ro cao): PO xác nhận lại phạm vi quyền này, và QA cần một staff không có Manage Artwork để kiểm (CHK-021, CHK-022).","kb_ids":["KB-815"]}
```

## OQ-artwork-232 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-232","type":"OPEN_ISSUE","feature_id":"run-image-effects","summary":"Run effects và popover Fill in variables trên Photo layer dùng Global Option: KB-800 cố ý không phát biểu về layer Global Option (phần \"không hiện cho Global option\" của dev doc đã bị spec 2026-10-19 đảo lại); KB-819 (spec) nói popover áp cho cả normal và global options. Hành vi phía Global Option thuộc object global-option (đã publish, còn OQ mở ở đó). Cần đối chiếu hai object khi test layer dùng Global Option.","kb_ids":["KB-800","KB-819"]}
```

## OQ-artwork-233 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-233","type":"OPEN_ISSUE","feature_id":"run-image-effects","summary":"Rule đã xác nhận nhưng chưa có lượt quan sát trên staging: tooltip \"Save the artwork first...\" cho layer PSD/Canva chưa Save (TC-05 tạm dừng), timeout thật (TC-19 chỉ mô phỏng), toast hết giới hạn 1000 ảnh/ngày, staff không có Manage Artwork. Cần setup (dev hỗ trợ ép timeout/quota, staff test) để chạy CHK-005, CHK-013, CHK-019, CHK-021/022.","kb_ids":["KB-801","KB-809","KB-813","KB-815"]}
```

## OQ-artwork-234 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-234","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"artwork KB-049 (artwork-save-persist) ghi thao tác trong editor không gọi API và phiên chưa Save không để lại dấu vết DB; Run effects gọi API, để lại ảnh mới trong image library và tính vào giới hạn upload dù artwork không Save. KB-049 chỉ liệt kê add/edit/delete/accordion/duplicate nên chưa mâu thuẫn; cần xác nhận Run effects là ngoại lệ có chủ đích của quy tắc \"không Save thì không để lại dấu vết\".","kb_ids":["KB-802","KB-803","KB-814"]}
```

## OQ-artwork-235 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-235","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"\"Photo layer\" trong KB-800 có gồm layer Multiple Uploads (mục Image effects after generating, KB-018) hay Text to Image không? Nguồn chỉ nói Photo layer customization Normal; cả candidate và base đều không nói.","kb_ids":["KB-800"]}
```

## OQ-artwork-236 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-236","type":"NEEDS_CONFIRMATION","feature_id":"run-effects-fill-in-variables","summary":"Giá trị chỉ gồm khoảng trắng bị coi là trống (PENDING-19, PO chưa xác nhận). Cần: PO xác nhận nguyên văn expected của hành vi này; khi có, CCR mới có thể nâng lên CONFIRMED_EXPECTED. Đây có phải hành vi đúng không?","kb_ids":["KB-826"]}
```

## OQ-artwork-237 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-237","type":"NEEDS_CONFIRMATION","feature_id":"run-effects-fill-in-variables","summary":"Mọi biến không khớp thì chạy thẳng, không mở popover (PENDING-16; spec có thể đọc là popover rỗng). Cần: PO xác nhận nguyên văn expected của hành vi này; khi có, CCR mới có thể nâng lên CONFIRMED_EXPECTED. Đây có phải hành vi đúng không?","kb_ids":["KB-828"]}
```

## OQ-artwork-238 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-238","type":"NEEDS_CONFIRMATION","feature_id":"run-effects-fill-in-variables","summary":"Giá trị nhập hiển thị như text thường, payload XSS/HTML không render: chỉ là quan sát TC-86/87. Cần: PO xác nhận nguyên văn expected của hành vi này; khi có, CCR mới có thể nâng lên CONFIRMED_EXPECTED. Đây có phải hành vi đúng không? Chủ đề bảo mật (rủi ro cao): PO xác nhận giá trị nhập phải hiển thị như text thường.","kb_ids":["KB-830"]}
```

## OQ-artwork-239 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-239","type":"NEEDS_CONFIRMATION","feature_id":"run-effects-fill-in-variables","summary":"Vế phụ CLAIM-17: prompt không có biến thì chạy thẳng; đóng popover thì không chạy: chỉ là kết quả test, spec không ghi nguyên chữ. Cần: PO hoặc Dev xác nhận nguyên văn vế này (có ngày, có link). Đây có phải hành vi đúng không?","kb_ids":["KB-820"]}
```

## OQ-artwork-240 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-240","type":"NEEDS_CONFIRMATION","feature_id":"run-effects-fill-in-variables","summary":"Vế phụ CLAIM-18: giá trị lưu không hợp lệ với input type mới bị bỏ, field trống + hint (PENDING-20, PO chưa xác nhận). Cần: PO hoặc Dev xác nhận nguyên văn vế này (có ngày, có link). Đây có phải hành vi đúng không?","kb_ids":["KB-822"]}
```

## OQ-artwork-241 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-241","type":"NEEDS_CONFIRMATION","feature_id":"run-effects-fill-in-variables","summary":"Vế bỏ khỏi CLAIM-22: option bị đổi tên thì token cũ không còn khớp (hệ quả suy ra từ Q1 B, PENDING-21), PO không nói riêng. Cần: PO xác nhận nguyên văn hành vi khi option bị đổi tên. Đây có phải hành vi đúng không?","kb_ids":["KB-827"]}
```

## OQ-artwork-242 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-242","type":"NEEDS_CONFIRMATION","feature_id":"run-effects-fill-in-variables","summary":"Vế bỏ khỏi CLAIM-24: giá trị nhập trong popover không ghi vào default của option trong artwork; không có trong quote xác nhận. Cần: PO/Dev xác nhận nguyên văn giá trị nhập không ghi vào default của option. Đây có phải hành vi đúng không?","kb_ids":["KB-829"]}
```

## OQ-artwork-243 — CONFLICT

```json
{"oq_id":"OQ-artwork-243","type":"CONFLICT","feature_id":"run-effects-fill-in-variables","summary":"Chữ hint field trống trong popover Fill in variables: spec (PO, 2026-10-26) ghi \"No default value. Enter one to run.\", build staging 2026-10-30 (assets/index.BMgdZMSW.js) hiện \"No valid default value. Enter one to run.\" cho mọi field trống. Cần: PO hoặc QA lead chọn chữ đúng; nếu build đúng thì cần cập nhật spec.","kb_ids":["KB-824","KB-825"],"side_a":"Spec TIB-5470 description, Update: Prompt variables › Fields (PO, 2026-10-26): hint \"No default value. Enter one to run.\"","side_b":"QA-3406 TC-61 (tạm dừng) 2026-10-30, build assets/index.BMgdZMSW.js: hint \"No valid default value. Enter one to run.\" cho mọi field trống, kể cả option không có default.","conflict_group":"fill-variables-empty-hint-copy"}
```

## OQ-artwork-244 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-244","type":"OPEN_ISSUE","feature_id":"run-effects-fill-in-variables","summary":"Vế giá trị nhập không chia sẻ sang browser, tab hoặc staff khác đã được PO chọn (Q2 A) nhưng chưa kiểm trực tiếp. Cần: QA kiểm trên browser/tab khác và với staff khác.","kb_ids":["KB-829"]}
```

## OQ-artwork-245 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-245","type":"OPEN_ISSUE","feature_id":"run-effects-fill-in-variables","summary":"Liên hệ object sdk (không sửa ở run này): sdk KB-415 nói storefront JSON List điền được prompt variable, còn câu hỏi Dev 55823 xếp biến JSON list vào nhóm biến portal không khớp. Khác surface, không chọn phía. Cần: Dev xác nhận biến JSON list trong popover portal có khớp option không, đối chiếu với storefront.","kb_ids":["KB-827"]}
```

## OQ-artwork-246 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-246","type":"OPEN_ISSUE","feature_id":"run-effects-fill-in-variables","summary":"Biến của ImagenHub template (effect imagenhub:image_filter) có mở popover Fill in variables như biến trong prompt không? Chưa thử (TC-78, PENDING-18); liên quan artwork KB-424 (warning ImagenHub variables). Liên quan CHK-021.","kb_ids":["KB-819"]}
```

## OQ-artwork-247 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-247","type":"NEEDS_CONFIRMATION","feature_id":"run-effects-fill-in-variables","summary":"Nguồn biến của prompt effect trên Photo layer: KB-113/KB-115 (layer-config-image) chỉ mô tả \"+ Variable\" trong prompt GenAI của Multiple Uploads/Text to Image (lấy Option Title từ layer Text/Additional Option khác, quan sát một lần); KB-819/KB-821 khớp biến với option gồm text, Only numbers, Date picker, option layer. Base chưa có item nào cho biến trong prompt của Image effects trên Photo layer: cần xác nhận cùng một cơ chế khớp biến.","kb_ids":["KB-819","KB-821"]}
```

## OQ-artwork-248 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-248","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Effect có bật dùng kích thước layer: hai layer khác kích thước thì gọi riêng, mỗi lần trừ một lượt. Không nạp KB (S0). Tên công tắc trên portal chưa biết, không có test case. Cần: Dev (giangnth) xác nhận nguyên văn, có ngày và link (ví dụ comment trên Jira TIB-5577), lời sửa câu Q2 ngày 2026-10-29; hiện chỉ là lời QA QA chuyển lại, kênh gốc không rõ, không có trên Jira. Chưa xác nhận thì không nạp KB.","kb_ids":[]}
```

## OQ-artwork-249 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-249","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Effect Gen AI trên layer Photo Reposition không bật dùng kích thước layer: hai layer khác kích thước vẫn gọi chung một lần. Không nạp KB (S0), không có test case. Cần: Dev (giangnth) xác nhận nguyên văn, có ngày và link (ví dụ comment trên Jira TIB-5577), lời sửa câu Q2 ngày 2026-10-29; hiện chỉ là lời QA QA chuyển lại, kênh gốc không rõ, không có trên Jira. Chưa xác nhận thì không nạp KB.","kb_ids":[]}
```

## OQ-artwork-250 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-250","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Contour cut: khác chiều rộng thì gọi riêng, cùng chiều rộng khác chiều cao thì gọi chung. Không nạp KB (S0), không có test case; không đụng item contour cut của layer-print-effects. Cần: Dev (giangnth) xác nhận nguyên văn, có ngày và link (ví dụ comment trên Jira TIB-5577), lời sửa câu Q2 ngày 2026-10-29; hiện chỉ là lời QA QA chuyển lại, kênh gốc không rõ, không có trên Jira. Chưa xác nhận thì không nạp KB. Khi được xác nhận thì đối chiếu lại item contour cut KB-391 (layer-print-effects) và KB-044.","kb_ids":[]}
```

## OQ-artwork-251 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-251","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Các effect không phụ thuộc kích thước (gray_scale, remove background, watercolor, sketch…; danh sách chỉ là ví dụ) luôn gọi chung dù layer khác kích thước. Không nạp KB (S0); ngược với cách đọc rộng câu Q2 trên Jira (xem OQ CONFLICT populate-share-call-layer-size). Cần: Dev (giangnth) xác nhận nguyên văn, có ngày và link (ví dụ comment trên Jira TIB-5577), lời sửa câu Q2 ngày 2026-10-29; hiện chỉ là lời QA QA chuyển lại, kênh gốc không rõ, không có trên Jira. Chưa xác nhận thì không nạp KB.","kb_ids":[]}
```

## OQ-artwork-252 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-252","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"gray_scale trên hai layer Direct upload khác kích thước dùng chung một lần gọi derive: chỉ có quan sát QA-3434 TC-64 (2026-10-27, build không ghi), test case không có căn cứ expected có nguồn. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) đây là hành vi đúng; chạy lại trên build có ghi phiên bản (sau 2026-10-29 08:21 GMT).","kb_ids":["KB-853"]}
```

## OQ-artwork-253 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-253","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Option chained {{output}} bắt đầu từ ảnh đã xử lý của nguồn, effect nguồn chạy một lần cho mỗi ảnh: chỉ có dev doc tự sinh từ branch diff (TIB-5504 comment 56020, 2026-10-29). Comment 56446 TIB-5504 (Dev, 2026-11-04, ngoài CCR) nói đã đổi luật effect trùng giữa nguồn và option {{output}} (effect trùng chỉ chạy một lần); không phải claim, không nạp. Item này không resolve OQ-artwork-093, OQ đó giữ mở. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code; đồng thời làm rõ luật effect trùng theo comment 56446 qua một Proposal riêng.","kb_ids":["KB-854"]}
```

## OQ-artwork-254 — CONFLICT

```json
{"oq_id":"OQ-artwork-254","type":"CONFLICT","feature_id":"populate-values","summary":"Effect không phải Gen AI trên layer Direct upload / Cropper: hai layer khác kích thước có tách lần gọi (và lượt) hay không. Phần Gen AI (KB-851) không tranh chấp. Cần: Dev xác nhận nguyên văn có ngày + link phía nào đúng; lời sửa Q2 ngày 2026-10-29 (CLAIM-03/04/05/07, S0, không link) ủng hộ side_b nhưng không được dùng làm căn cứ. Liên quan: request Gen AI có mang kích thước layer không (KB-851 so với KB-853) chưa rõ. Liên quan CHK-030.","kb_ids":["KB-852","KB-853"],"conflict_group":"populate-share-call-layer-size","side_a":"Jira TIB-5577 comment 55689 (Dev, 2026-10-27, Q2): kích thước layer Direct upload / Cropper thuộc thiết lập effect, khác kích thước thì gọi riêng, tính lượt riêng; câu không giới hạn loại effect (KB-852).","side_b":"QA-3434 TC-64 PASS 2026-10-27 staging: gray_scale trên layer Direct upload 400×400 và 400×300 dùng chung một lần gọi derive, request không mang kích thước (KB-853)."}
```

## OQ-artwork-255 — CONFLICT

```json
{"oq_id":"OQ-artwork-255","type":"CONFLICT","feature_id":"populate-values","summary":"Option Photo Reposition {{output}} có effect riêng: điều kiện đi theo vị trí nguồn chỉ là tỷ lệ ảnh kết quả lệch ≤ 0.05, hay còn phụ thuộc tỷ lệ khung option so với khung nguồn. Cần: Dev trả lời về TC-28 (bug draft chưa file); chạy TC-27 và mốc 1.049/1.051. Liên quan CHK-040.","kb_ids":["KB-856","KB-857"],"conflict_group":"populate-reposition-follow-ratio","side_a":"Jira TIB-5504 comment 56059 (Dev, 2026-10-29, Q5): đi theo khi tỷ lệ kết quả lệch ≤ 0.05 so với ảnh nguồn (KB-856).","side_b":"QA-3441 TC-28 FAIL 2026-10-29 staging: khung option 400×400 khác khung nguồn 400×300 thì không đi theo dù lệch 0.04/0.05 (KB-857)."}
```

## OQ-artwork-256 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-256","type":"OPEN_ISSUE","feature_id":"populate-values","summary":"Known issue nguồn Photo Cropper: thay ảnh thì option {{output}} bắt đầu ngay từ ảnh mới, effect nguồn chạy hai lần, lỗi thì option và nguồn hiện ảnh khác nhau. Không do TIB-5504, có ticket riêng nhưng dev không nêu key; thấy một lần ở QA-3441 TC-24, chưa file bug. Cần: Key ticket riêng và trạng thái fix; không dùng làm expected. Liên quan CHK-045. Chưa rõ lần chạy effect nguồn thứ hai có tính thêm lượt không.","kb_ids":["KB-867"]}
```

## OQ-artwork-257 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-257","type":"OPEN_ISSUE","feature_id":"populate-values","summary":"Known preview vs print mismatch: preview storefront không vẽ vị trí populate từ Photo Reposition cho layer No personalization, vẫn fit ảnh vào khung, trong khi order render dùng vị trí đó. Cần: Ticket theo dõi lệch preview/bản in và kế hoạch xử lý; không dùng làm expected. PO xác nhận vị trí populate từ Photo Reposition dùng trong order render là chủ đích (rủi ro order, impact HIGH); chưa có lượt đặt đơn thật đối chiếu vị trí trên order design. Liên quan CHK-038, CHK-039.","kb_ids":["KB-859","KB-860"]}
```

## OQ-artwork-258 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-258","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Lượt bị trừ khi populated option dùng chung hoặc tách lần gọi effect: số lượt khi dùng chung một lần gọi chưa đo (QA-3434 TC-13 tạm dừng), và \"lượt\" là bộ đếm nào (Gen AI credit của store, rate-limit visitor của sdk, hay quota Run effects của portal) chưa rõ; cũng chưa rõ lần gọi lại sau reload (KB-865) có tính thêm lượt không. Cần: PO xác nhận ý định tính lượt (rủi ro tiền, impact HIGH). Liên quan CHK-031.","kb_ids":["KB-850","KB-851","KB-852","KB-853","KB-865"]}
```

## OQ-artwork-259 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-259","type":"OPEN_ISSUE","feature_id":"populate-values","summary":"Layer Cropper chưa có lượt kiểm cho Gen AI khác kích thước gọi riêng: QA-3434 TC-14 chỉ chạy Gemini trên Direct upload và chưa chạy lại trên build sau 2026-10-29 08:21 GMT. Cần: QA chạy trên layer Cropper với build có ghi phiên bản.","kb_ids":["KB-851"]}
```

## OQ-artwork-260 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-260","type":"OPEN_ISSUE","feature_id":"populate-values","summary":"Hành vi lỗi của option chained {{output}} mới kiểm với lỗi giả lập trong trang (HTTP 500 / status 3), chưa kiểm với lỗi thật từ provider. Cần: QA kiểm với lỗi thật (ví dụ prompt bị moderation chặn).","kb_ids":["KB-862","KB-863","KB-864"]}
```

## OQ-artwork-261 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-261","type":"OPEN_ISSUE","feature_id":"populate-values","summary":"Add to Cart bị chặn khi effect riêng của option chained {{output}} lỗi chưa được test riêng (rủi ro order, impact HIGH). Cần: QA kiểm vế Add to Cart; PO xác nhận nếu kết quả khác.","kb_ids":["KB-864"]}
```

## OQ-artwork-262 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-262","type":"OPEN_ISSUE","feature_id":"populate-values","summary":"Layer ảnh No personalization populate {{output}} từ nguồn Photo Cropper nhận ảnh đã crop: dev nói đúng theo code nhưng chưa kiểm trên UI (staging chưa có campaign có cấu hình này), CCR ghi QA-3441 TC-38 PASS. Cần: dựng fixture trên store explorer và kiểm trên UI.","kb_ids":["KB-858"]}
```

## OQ-artwork-263 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-263","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Chain populate {{output}} từ hai cấp trở lên: portal cho cấu hình nhưng chỉ một cấp được hỗ trợ; hành vi chain nhiều cấp không có expected. Cần: PO quyết portal có nên chặn cấu hình này hay ghi rõ không hỗ trợ. Liên quan CHK-036.","kb_ids":["KB-861"]}
```

## OQ-artwork-264 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-264","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Phạm vi token của KB-120 / CHK-022 (lan truyền ngay giá trị gốc): mới quan sát với {{input.1}} từ nguồn Multiple Uploads nhưng item không ghi rõ chỉ áp cho {{input.N}}. Với {{output}}, option bắt đầu từ ảnh đã xử lý của nguồn (KB-866, KB-854), và bắt đầu ngay từ ảnh mới với nguồn Photo Cropper là known defect (KB-867). Cần: ghi rõ phạm vi token của KB-120 ở lần cập nhật sau để không đọc rộng thành expected.","kb_ids":["KB-120","KB-866","KB-867"]}
```

## OQ-artwork-265 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-265","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Liên hệ object sdk (không sửa ở run này): sdk KB-487 nói layer populate target chạy effect lên ảnh buyer upload vào nguồn, có thể đọc là ảnh gốc; với {{output}} có effect nguồn, KB-866 nói option bắt đầu từ kết quả của nguồn. Cần: PO/Dev xác nhận KB-487 có phân biệt {{input}} và {{output}} không.","kb_ids":["KB-866","KB-854"]}
```

## OQ-artwork-266 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-266","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"KB-865 (reload thì option chained chạy lại từ đầu) ngầm cần ảnh nguồn còn sau reload, trong khi sdk KB-019 thấy full reload không khôi phục form (field text/clipart). Khác loại field, không kết luận mâu thuẫn. Cần: quan sát photo layer sau reload.","kb_ids":["KB-865"]}
```

## OQ-artwork-267 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-267","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Base chỉ có quan sát portal cho nguồn Multiple Uploads (KB-118, KB-119); delta ngầm cho phép layer Photo (Direct upload / Cropper / Reposition) làm nguồn {{output}}, chưa có quan sát portal nào cho cấu hình này. Cần: quan sát dropdown Source option với nguồn Photo.","kb_ids":["KB-118","KB-119","KB-858","KB-859"]}
```

## OQ-artwork-268 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-268","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Mọi item CBS-091 (KB-850..KB-867) có trạng thái ship UNKNOWN: TIB-5577 và TIB-5504 đang Passed, chỉ có scope staging, production chưa có quan sát. Cần: xác nhận ticket đã ship production và build tương ứng.","kb_ids":["KB-850","KB-855","KB-859","KB-866"]}
```

## OQ-artwork-269 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-269","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Nợ base có sẵn: KB-124 (layer-config-image), CHK-024 và OQ-artwork-093 tham chiếu \"KB-008 (feature populate-values)\" trong khi item tương ứng trong shard populate-values là KB-120. Cần: sửa tham chiếu ở lần cập nhật sau.","kb_ids":["KB-120"]}
```

## OQ-artwork-270 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-270","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-881: chọn 1 layer mở được Bulk edit; selection chỉ locked hoặc chỉ replica thì mục \"Bulk edit\" có nhưng disabled (lượt 2026-10-22 replica-only còn ẩn); selection lẫn editable + locked + replica chỉ ghi layer editable. Đây có phải hành vi đúng, disabled hay ẩn? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-881"]}
```

## OQ-artwork-271 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-271","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-882: chữ header / mô tả / footer (không dấu chấm), nút Cancel / Save, accordion đầu mở sẵn, rộng 620 px của modal Bulk edit chỉ là quan sát TC-07/08. Đây có phải chữ và bố cục chuẩn không? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-882"]}
```

## OQ-artwork-272 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-272","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-884: ghi lại đúng giá trị cũ thì không lỗi, 1 undo step; Cancel / Esc / click ngoài modal không ghi, không thêm undo step — chỉ quan sát 2026-10-23 trên build cũ. Đây có phải hành vi đúng trên build cuối? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-884"]}
```

## OQ-artwork-273 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-273","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-886: Populate Content (và Populate Color / Background của text) trong modal là radio On / No change / Off, mặc định No change — PO A2 và Dev 55846 không nói về Populate. Đây có phải hành vi đúng? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-886"]}
```

## OQ-artwork-274 — CONFLICT

```json
{"oq_id":"OQ-artwork-274","type":"CONFLICT","feature_id":"layer-bulk-edit","summary":"\"Personalization for this layer\" trong modal Bulk edit: PO A2 (49367, 2026-08-28) yêu cầu segmented control On / – / Off; Dev (55846, 2026-10-28) + TC-15 cho thấy vẫn là radio 3 lựa chọn, không có No change, và đã hỏi lại PO (PENDING-02). Cần: PO trả lời câu hỏi của Dev ở comment 55846: giữ radio-rỗng-là-no-change hay đổi UI sang tri-state thật.","kb_ids":["KB-887","KB-888"],"conflict_group":"CONF-CBS-092-03","side_a":"KB-887 (INFERRED, LOW): PO A2 comment 49367 (2026-08-28) — Personalization phải là segmented control On / – / Off.","side_b":"KB-888 (OBSERVED_CURRENT, LOW): Dev 55846 (2026-10-28) + TC-15 — radio 3 lựa chọn, không có No change; chỉ Cancel quay lại trạng thái không chọn."}
```

## OQ-artwork-275 — CONFLICT

```json
{"oq_id":"OQ-artwork-275","type":"CONFLICT","feature_id":"layer-bulk-edit","summary":"Layer linked khi bulk edit setting ngoài Conditional: TC-43 (2026-10-30) thấy LK1 giữ linked và form_label không đổi; Dev 49205 C3 (2026-08-27) nói các setting khác vẫn áp bình thường; Dev 55846 chỉ nói đã fix \"layer Link bị patch nhầm\". Cần: Dev hoặc PO nói rõ: sau fix 2026-10-28, setting ngoài Conditional có còn ghi lên layer linked không.","kb_ids":["KB-890","KB-891"],"conflict_group":"CONF-CBS-092-04","side_a":"KB-890 (OBSERVED_CURRENT, LOW): TC-43 — layer linked giữ customization_type linked, form_label không đổi.","side_b":"KB-891 (INFERRED, LOW): Dev 49205 C3 — layer linked, các setting khác ngoài Conditional vẫn áp bình thường."}
```

## OQ-artwork-276 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-276","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-893: danh sách field theo tổ hợp layer type (Text + Paragraph, 5 text type, cùng type clipart, Text + Clipart) chỉ là quan sát TC-16..19, một phần trên build cũ. Đây có phải tập field đúng không? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-893"]}
```

## OQ-artwork-277 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-277","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-896: panel Conditional Setting hiện khi ≥1 layer hỗ trợ; rule ghi cho mọi layer hỗ trợ, bỏ qua Dynamic Clipart by Text; rule cũ bị thay (mới thấy 1 layer, TC-42 chưa xong). Đây có phải hành vi đúng? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối. TC-42 chạy đủ bước xoá rule và undo.","kb_ids":["KB-896"]}
```

## OQ-artwork-278 — CONFLICT

```json
{"oq_id":"OQ-artwork-278","type":"CONFLICT","feature_id":"layer-bulk-edit","summary":"Vector category trong Design settings của Bulk edit: TC-26 (2026-10-22, build cũ) thấy \"Select one vector category\" + default value; Dev 49205 C5 (2026-08-27) nói Design settings chỉ gồm text, clipart, grouped_clipart, default_value. PENDING-01 chưa ai trả lời. Cần: Dev hoặc PO trả lời PENDING-01: vector category có thuộc scope Bulk edit không; chạy lại TC-26 trên build cuối kèm reset default.","kb_ids":["KB-906","KB-907"],"conflict_group":"CONF-CBS-092-05","side_a":"KB-906 (OBSERVED_CURRENT, LOW): TC-26 — V1 + V2 có field vector category.","side_b":"KB-907 (INFERRED, LOW): Dev 49205 C5 — Design settings chỉ gồm text, clipart, grouped_clipart, default_value."}
```

## OQ-artwork-279 — CONFLICT

```json
{"oq_id":"OQ-artwork-279","type":"CONFLICT","feature_id":"layer-bulk-edit","summary":"Danh sách nguồn Populate trong Bulk edit: TC-31 (2026-10-30, build index.BMgdZMSW.js) thấy loại mọi layer đang chọn (\"List is empty.\"); dev summary 49895 (2026-09-04) và QA 2026-10-29 (build index.acNZihq9.js) thấy chỉ loại layer đầu tiên. Không ai xác nhận thay đổi giữa 2 build. Cần: Dev xác nhận đã đổi logic nguồn Populate giữa 2 build (có ngày), hoặc PO nói hành vi đúng.","kb_ids":["KB-901","KB-902"],"conflict_group":"CONF-CBS-092-06","side_a":"KB-901 (OBSERVED_CURRENT, LOW): TC-31 — nguồn loại mọi layer đang chọn.","side_b":"KB-902 (OBSERVED_CURRENT, LOW): dev summary 49895 + QA 2026-10-29 — chỉ loại layer đầu tiên của selection."}
```

## OQ-artwork-280 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-280","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-903: Populate values + \"Use an existing global option\" set trong cùng 1 Save đều được ghi (global_option + retrieval_value_enabled / retrieval_layer), quan sát TC-31 2026-10-30. Đây có phải hành vi đúng? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-903"]}
```

## OQ-artwork-281 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-281","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"Khi selection không có setting chung: mục Bulk edit trên menu có vẫn bật không, và nút Save có bị disable không? Chỉ dev summary 49895 nói, chưa ai thấy (vế bị bỏ của CLAIM-20; empty state ở KB-904). Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối. Hoặc dựng được tổ hợp layer thật dẫn tới empty state (TC-22).","kb_ids":[]}
```

## OQ-artwork-282 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-282","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"Chọn group layer: layer con có được chọn theo và nhận Bulk edit, group không bị ghi, header đếm cả group không? Chỉ quan sát 1 lượt TC-04 2026-10-22 build cũ; Dev 49205 A3 nói selection loại layer group; PO chưa quyết PENDING-05. Không nạp KB. Cần: PO quyết PENDING-05; Dev xác nhận hành vi chọn group trên build cuối.","kb_ids":[]}
```

## OQ-artwork-283 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-283","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"Default text set qua Bulk edit có điền sẵn vào ô nhập storefront không; modal có cần field \"Prefill default text\" (autofill_default_value) như panel single-layer không? Chỉ quan sát TC-30 (chưa PASS, expected khác). Không nạp KB. Cần: PO hoặc Dev xác nhận nguyên văn, có ngày. TIB-5236 chỉ là ngữ cảnh regression, không phải nguồn.","kb_ids":[]}
```

## OQ-artwork-284 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-284","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"Known limitation theo dev summary 49895: field cùng tên nhưng khác kiểu giữa các layer type bị loại khỏi modal Bulk edit, không thông báo. PENDING-04 chưa trả lời, QA chưa thử. Không nạp KB. Cần: Dev hoặc PO trả lời PENDING-04; QA chạy tổ hợp layer có field cùng tên khác kiểu.","kb_ids":[]}
```

## OQ-artwork-285 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-285","type":"NEEDS_CONFIRMATION","feature_id":"layer-common-config","summary":"Option title và Add instruction được chèn như HTML trên form storefront và form preview portal (<b>, <img> hiện thật; <script>, onerror bị bỏ) — quan sát TC-35, có từ trước TIB-5299; Dev 55846 chỉ nói không liên quan ticket. Đây là defect (khả năng bảo mật) hay hành vi chấp nhận? Không nạp KB. Cần: PO hoặc Dev nói rõ đúng/sai; nếu là defect thì ticket theo dõi. Không tự tạo issue Jira, hỏi operator trước.","kb_ids":[]}
```

## OQ-artwork-286 — CONFLICT

```json
{"oq_id": "OQ-artwork-286", "type": "CONFLICT", "feature_id": "editor-layer-workspace", "summary": "Menu overflow trên layer action bar: KB-043 (bootstrap 2026-09-10) ghi action bar không có menu '...'; KB-085 (layer-config-image, bootstrap 2026-09-21) ghi panel cấu hình chỉ tiếp cận qua '...' > 'Bulk edit', không có panel single-layer; KB-908 (TC-01 2026-10-30) ghi menu More (…) có Bulk edit đứng đầu + Replace image layer, Link with another layer, Convert to another layer, 6 mục bulk cũ không còn. Cần: Operator/owner quyết resolve (supersede tắt ở teeinblue); run explore hoặc test case có căn cứ expected đọc lại action bar và panel single-layer trên build cuối; cập nhật CHK-005, CHK-015 theo kết quả. Ghi chú thêm: KB-043 và KB-085 đã lệch nhau từ base về việc có menu '...' hay không, KB-908 cùng chiều KB-085 ở điểm đó; KB-908 không nói gì về panel single-layer. Check mất oracle: CHK-005, CHK-024 (editor-layer-workspace), CHK-015 (layer-config-image). [CBS-113] Bổ sung KB-1037 (TIB-5211, 2026-07-20, nguồn sớm hơn KB-043) và KB-1038 vào side_b; CHK-020 (layer-duplicate-link-copy) chờ resolve.", "kb_ids": ["KB-043", "KB-085", "KB-908", "artwork/layer-duplicate-link-copy#KB-1037", "artwork/layer-duplicate-link-copy#KB-1038"], "conflict_group": "CONF-CBS-092-01", "side_a": "KB-043 (OBSERVED_CURRENT, MEDIUM, 2026-09-10): không có menu overflow (CHK-005); KB-085 (OBSERVED_CURRENT, LOW, 2026-09-21): panel cấu hình chỉ qua '...' > 'Bulk edit', không panel single-layer (CHK-015).", "side_b": "KB-908 (OBSERVED_CURRENT, LOW, CBS-092 CLAIM-01, TC-01 2026-10-30): menu More (…) có Bulk edit đứng đầu + 3 mục; 6 mục bulk cũ không còn. [CBS-113] Thêm cùng phía: KB-1037 (CONFIRMED_EXPECTED, LOW, UNRESOLVED; spec_doc Jira TIB-5211 description mục Solution, 2026-07-20: 'Convert to another layer' nằm trong menu '...' More actions của layer toolbar) và KB-1038 (PROPOSED, rule QA FACT-038 2026-09-04: link layer sẵn có qua '...' → 'Link with another layer') ở layer-duplicate-link-copy.", "check_ids": ["CHK-005", "CHK-024", "CHK-015", "artwork/layer-duplicate-link-copy#CHK-020"]}
```

## OQ-artwork-287 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-287", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "summary": "KB-908: nội dung và nhãn menu More (…) (Bulk edit, Replace image layer, Link with another layer, Convert to another layer; Artwork 1.0 vẫn ghi \"Share with another layer\") chỉ là quan sát TC-01, khác nhãn trong TC expected và ticket. Đây có phải nội dung và nhãn đúng? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối. [CBS-113] Rule QA FACT-038 (2026-09-04, KB-1038, PROPOSED) dùng mục 'Link with another layer' của menu '...' làm entry point link một layer sẵn có vào origin ở Artwork 2.0; cần Dev xác nhận cùng câu hỏi này.", "kb_ids": ["KB-908", "artwork/layer-duplicate-link-copy#KB-1038"]}
```

## OQ-artwork-288 — CONFLICT

```json
{"oq_id":"OQ-artwork-288","type":"CONFLICT","feature_id":"editor-layer-workspace","summary":"Bar hành động khi selection có replica Global Template: KB-042 (bootstrap 2026-09-10) ghi bar Deselect/Group/Duplicate/Delete không đổi theo loại/số lượng layer chọn; KB-909 (Dev 55846, 2026-10-28) nói cờ canMutate chặn Group / Duplicate / Delete khi selection có replica. Sample của KB-042 không có replica nên có thể chỉ khác state. Cần: Operator/owner quyết resolve (supersede tắt); đọc lại action bar với selection có replica trên build cuối; cập nhật CHK-006 theo kết quả. Ghi chú thêm: KB-909 và KB-042 có thể chỉ khác state (sample của KB-042 không có replica); nếu PO xác nhận khác state thì là item mới, không phải mâu thuẫn. Check mất oracle: CHK-002, CHK-003, CHK-004, CHK-006, CHK-025.","kb_ids":["KB-042","KB-909"],"conflict_group":"CONF-CBS-092-02","side_a":"KB-042 (OBSERVED_CURRENT, MEDIUM, 2026-09-10): bar hành động không đổi theo loại/số lượng layer chọn (CHK-006).","side_b":"KB-909 (CONFIRMED_EXPECTED, LOW, UNRESOLVED; po_dev_confirm Dev 55846 2026-10-28): replica → canMutate chặn Group / Duplicate / Delete.","check_ids":["CHK-002","CHK-003","CHK-004","CHK-006","CHK-025"]}
```

## OQ-artwork-289 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-289","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"KB-225 / CHK-017 mô tả lối vào \"Bulk apply Conditional setting\" từ layer action bar; theo KB-908 (TC-01 2026-10-30) mục \"Conditional setting\" đó đã bị TIB-5299 bỏ khỏi menu More (…), Conditional giờ nằm trong modal Bulk edit. KB-225 / CHK-017 còn đúng không? OQ-artwork-154 vẫn mở. Cần: Run có lock conditional-setting-config cập nhật KB-225 / CHK-017 sau khi CONF-CBS-092-01 được resolve; PO hoặc Dev xác nhận Show/Hide khi bulk apply Conditional trong modal.","kb_ids":["KB-225"],"check_ids":["CHK-017"],"related_oq_ids":["OQ-artwork-154"]}
```

## OQ-artwork-290 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-290","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Live Preview trong portal artwork editor dùng teeinblue-sdk qua git submodule src/sdk, chỉ có fix TIB-5412 sau khi submodule được bump riêng (note Dev TIB-5412 comment 51755, 2026-09-23). Submodule đã được bump chưa? Không nạp KB. Cần: Dev xác nhận đã bump submodule src/sdk (commit/PR, có ngày).","kb_ids":[]}
```

## OQ-artwork-291 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-291","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","kb_ids":["KB-883","KB-897"],"summary":"Hai hành vi ghi đè hàng loạt được publish với cờ rủi ro cao: chạm field rồi để rỗng thì ghi rỗng cho mọi layer đã chọn (KB-883); đổi clipart category / group mà không chạm Default value thì default_value thành null trên mọi layer đã chọn (KB-897). Cả hai có nguồn Dev và đang làm oracle cho check P1. Mức HIGH là đánh giá của bước diff. Cần: PO xác nhận đây là ý định sản phẩm (ghi đè không cảnh báo)."}
```

## OQ-artwork-292 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-292","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","kb_ids":["KB-880"],"summary":"Quyền: staff không có quyền Manage Artwork có thấy / dùng được Bulk edit không? TC-06 chưa chạy, chưa có item nào về quyền (CHK-026 là gap). Cần: account staff không có quyền do operator cấp, hoặc PO/Dev xác nhận nguyên văn có ngày."}
```

## OQ-artwork-293 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-293","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","kb_ids":["KB-898"],"summary":"Redo sau Undo của một lượt Bulk edit: TC-28 thấy Redo khôi phục toàn bộ, nhưng PO C1 (49367) chỉ nói về Undo. Cần: PO/Dev xác nhận Redo là một bước khôi phục toàn bộ lượt bulk edit."}
```

## OQ-artwork-294 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-294","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","kb_ids":["KB-042"],"summary":"KB-042 có hai vế: canvas toolbar đổi theo loại layer (không bị tranh chấp) và bar hành động không đổi theo selection (bị KB-909 tranh chấp). Vì conflict ở mức item, CHK-002, CHK-003, CHK-004 (chỉ dùng vế canvas toolbar) cũng mất oracle. Cần: khi PO quyết CONF-CBS-092-02 (OQ-artwork-288), quyết luôn có tách KB-042 thành hai item để trả oracle cho CHK-002..004 không.","check_ids":["CHK-002","CHK-003","CHK-004"]}
```

## OQ-artwork-295 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-295","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","kb_ids":["KB-087","KB-088"],"summary":"KB-087, KB-088 (2026-09-21) mô tả field inventory của dialog Bulk Edit trước TIB-5299 (dialog mở cho 1 layer clipart-category). Modal Bulk edit mới (feature layer-bulk-edit: KB-883 field mở ra rỗng / No change, KB-885, KB-893 tập field chung) có thể làm hai item này cũ. CCR không khai quan hệ, không sửa. Cần: quan sát lại panel cấu hình 1 layer clipart-category trên build hiện tại."}
```

## OQ-artwork-296 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-296","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","kb_ids":["KB-884","KB-893","KB-906"],"summary":"Mọi test case của QA-3419 là kết quả AI do máy chạy, chỉ trên staging; một số lượt (TC-18, TC-19, TC-26, TC-12/13/40) chạy trên build cũ index.BqS1iTCG.js, không phải build cuối index.BMgdZMSW.js. TIB-5299 Done nhưng production chưa có quan sát. Cần: chạy lại các TC này trên build cuối và quan sát production."}
```

## OQ-artwork-297 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-297", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-photo-border", "kb_ids": ["KB-910"], "summary": "KB-910: Contour cut ở Border size 1 vẽ viền theo outline phần đục của clipart, không thành khung vuông theo bounding box, chỉ là quan sát test case (một layer Clipart Category, Artwork editor, zoom 50%, không ghi build). Đây có phải hành vi đúng ở mọi size không? Bản fix đã được Dev xác nhận ở KB-912. Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5592), hoặc test case PASS có căn cứ expected và ghi build/bản đã test.", "check_ids": ["CHK-002"]}
```

## OQ-artwork-298 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-298", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-photo-border", "kb_ids": ["KB-911"], "summary": "KB-911: Contour cut ở Border size 1–3 chỉ vẽ màu viền thành vòng ngoài hình, không ám màu lên clipart hay vùng trong suốt, ảnh viền nằm dưới ảnh clipart — chỉ là quan sát test case. Đây có phải cách vẽ đúng (kể cả thứ tự lớp viền dưới clipart) không? Size 2 và 3 khác nhau thế nào về độ dày? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5592), hoặc test case PASS có căn cứ expected và ghi build/bản đã test.", "check_ids": ["CHK-002"]}
```

## OQ-artwork-299 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-299", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-photo-border", "kb_ids": ["KB-916"], "summary": "KB-916: thiết lập Border đọc lại đúng sau Save & Close + reload và field photo_border (size, type, color, display, line, enabled; display mockup_order = \"Mockup Preview & Order Design\") chỉ là quan sát một mẫu. Tập giá trị đầy đủ của type và display là gì, và đây có phải contract lưu chuẩn không? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5592), hoặc test case PASS có căn cứ expected và ghi build/bản đã test.", "check_ids": ["CHK-014", "CHK-015"]}
```

## OQ-artwork-300 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-300", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-photo-border", "kb_ids": ["KB-917"], "summary": "KB-917: Undo/Redo khi đổi Border size trả cả giá trị lẫn hình vẽ, Duplicate layer giữ nguyên thiết lập Border — chỉ là quan sát test case trên một layer đơn, bản copy không được lưu. Đây có phải hành vi đúng không, và Border của bản copy có giữ sau Save không? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5592), hoặc test case PASS có căn cứ expected và ghi build/bản đã test. Thêm: chưa rõ TC-27 dùng thao tác Duplicate nào — theo KB-045 layer Clipart Category có thể tạo bản LINKED, và KB-429 ẩn Photo Border khi selection có layer Linked, nên chưa rõ Border của bản copy được đọc thế nào; số phím gõ khi đổi size 3 → 1 không ghi, chưa đối chiếu được với luật mỗi phím là 1 undo step của KB-428 (nêu cho multi-select).", "check_ids": ["CHK-016", "CHK-017"]}
```

## OQ-artwork-301 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-301", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-photo-border", "kb_ids": ["KB-918", "KB-914"], "summary": "KB-918: Dev/PO cho biết Border size = 0 (min theo KB-914) phải vẽ gì — không có viền hay giá trị khác? Một lượt quan sát trong Artwork editor thấy size 0 vẽ viền dày như size 10; đây có phải lỗi không? Chưa chạy lại, chưa kiểm storefront và Order Design ở size 0; QA có bug draft chưa submit, chưa có ticket. Cần: Dev hoặc PO xác nhận nguyên văn, có ngày, expected của size 0 (Jira TIB-5592 hoặc ticket mới do operator quyết). Không tự tạo issue.", "check_ids": ["CHK-012"]}
```

## OQ-artwork-302 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-302", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-photo-border", "kb_ids": ["KB-915", "KB-429"], "summary": "KB-915: \"Linked clipart\" Dev liệt kê trong các loại layer dùng chung hàm vẽ viền có phải layer customization type Linked của KB-429 (Photo Border bị ẩn khi selection có layer Linked) không? Nếu là cùng loại thì Photo Border áp cho Linked theo đường nào (layer nguồn hay chính layer Linked)? Cần: Dev xác nhận nguyên văn, có ngày (Jira TIB-5592 hoặc TIB-5212).", "check_ids": ["CHK-008"]}
```

## OQ-artwork-303 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-303", "type": "OPEN_ISSUE", "feature_id": "layer-photo-border", "kb_ids": ["KB-912", "KB-913", "KB-915"], "summary": "Bề mặt và loại layer chưa kiểm sau fix TIB-5592: chưa chạy kết quả vẽ viền ở storefront live preview (mockup), cart Edit design, Portal View/Edit customization (KB-912), file Order Design và mockup render (KB-913); chưa kiểm các loại layer ngoài Clipart Category — Dynamic clipart (dynamic_by_text), Clipart group, Linked clipart, Static image, Photo Upload — và border kiểu Custom shape (KB-915). Cần: Chạy test case trên các bề mặt và loại layer này (store explorer), ghi build. Riêng Custom shape: KB-912 chỉ mô tả lỗi cho Contour cut, chưa rõ Custom shape ở size 1–3 phải vẽ thế nào (CHK-009 chưa có oracle). Các check READY CHK-003..CHK-007 đóng phần bề mặt khi được chạy.", "check_ids": ["CHK-009"]}
```

## OQ-artwork-304 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-304", "type": "OPEN_ISSUE", "feature_id": "layer-photo-border", "kb_ids": ["KB-914"], "summary": "KB-914: max (không có), step = 1 và cách ô Border size xử lý số thập phân chưa được kiểm runtime; kết quả vẽ ở giá trị lớn (vd size 100) chưa chạy. Cần: Chạy test case boundary cho ô Border size, ghi build.", "check_ids": ["CHK-013"]}
```

## OQ-artwork-305 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-305", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-photo-border", "kb_ids": ["KB-913"], "check_ids": ["CHK-005"], "summary": "PO xác nhận KB-913 (chạm order/fulfillment, oracle STRONG duy nhất của CHK-005 P1): server render (file Order Design, mockup render) vẽ Photo Border bằng code riêng, không bị lỗi TIB-5592, và đơn đã render không cần regenerate. Hiện chỉ có lời Dev (Jira TIB-5592 comment 55072, 2026-10-19), QA chưa kiểm Order Design file và mockup render. KB-913 không nói gì về border custom_shape trên print file: câu đó vẫn ở OQ-artwork-195 (còn mở). Cần: PO xác nhận nguyên văn, có ngày."}
```

## OQ-artwork-306 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-306", "type": "OPEN_ISSUE", "feature_id": "layer-config-image", "kb_ids": ["KB-930"], "summary": "KB-930: photo layer No personalization được coi là populated với mọi nguồn (Dev TIB-5521 55637 Q4), nhưng nguồn {{input}} trần chưa được QA kiểm (mới kiểm photo, Photo Reposition, Multiple Uploads {{input.1}}, output effect). Cần: Test case PASS có ngày/build cho nguồn {{input}} trần, hoặc run explore hẹp."}
```

## OQ-artwork-307 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-307", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-931"], "summary": "KB-931: photo layer No personalization bỏ qua Direct upload style (ảnh mặc định fill, populated contain) ở Mockup Editor, Campaign Editor, storefront preview và order design chỉ là quan sát QA-3402 (AI chạy 2026-10-26, căn cứ expected không rõ). Đây có phải fit rule đúng? Cần: PO hoặc Dev xác nhận nguyên văn có ngày trên Jira TIB-5521, hoặc test case Testlane PASS có căn cứ expected và build. Người quyết: PO (cờ requires_human_decision của diff cho KB-931).", "check_ids": ["CHK-064"]}
```

## OQ-artwork-308 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-308", "type": "OPEN_ISSUE", "feature_id": "layer-config-image", "kb_ids": ["KB-936"], "summary": "KB-936 (known defect): API áp placement position của layer No personalization đã populated, SDK preview thì không (Dev TIB-5521 55637 Q3, chỉ đề xuất chấp nhận). PO có chấp nhận khác biệt preview/design này không? QA TC-09 chưa tái hiện được lệch vị trí. Cần: PO trả lời Q3 trên TIB-5521; ai đó tái hiện lệch vị trí trên staging hoặc tách ticket bug. Người quyết: PO (cờ requires_human_decision của diff cho KB-936).", "check_ids": ["CHK-066"]}
```

## OQ-artwork-309 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-309", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-937"], "summary": "KB-937: layer No personalization không có ảnh mặc định và không có retrieval value thì SDK preview không vẽ gì (Dev 55639 RQ6 mô tả hiện trạng có từ trước). Đây có phải expected không? Cần: PO xác nhận nguyên văn có ngày (TIB-5521 hoặc ticket riêng).", "check_ids": ["CHK-065"]}
```

## OQ-artwork-310 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-310", "type": "OPEN_ISSUE", "feature_id": "layer-config-image", "kb_ids": ["KB-942"], "summary": "KB-942: Gen AI effect chỉ có ở Photo layer trên Artwork 2.0 (Dev TIB-5573 56104). Trạng thái ship khai UNKNOWN; Gen AI effect của layer clipart Artwork 1.0 chưa được thử. Cần: Xác nhận đã ship; test case cho clipart Artwork 1.0 nếu còn artwork 1.0 trên staging. Người quyết: PO (cờ requires_human_decision của diff cho KB-942)."}
```

## OQ-artwork-311 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-311", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-943"], "summary": "KB-943: danh sách field output size theo model (GPT gpt-image-2, Gemini pro/31, Flux 2, không field với Flux 1/gpt-image-1.5/ImagenHub; Default chọn sẵn) chỉ là quan sát QA-3435 2026-10-27, build không ghi. Field nằm sau Prompt / Example prompts, lệch mô tả 'under the provider' của Dev summary 55645. gpt-image-2.5-flare/sunburst chưa kiểm. Đây có phải danh sách và vị trí đúng? Cần: Dev/PO xác nhận nguyên văn có ngày (TIB-5561), hoặc test case Testlane PASS có build và căn cứ expected; kiểm gpt-image-2.5-flare/sunburst.", "check_ids": ["CHK-073"]}
```

## OQ-artwork-312 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-312", "type": "OPEN_ISSUE", "feature_id": "layer-config-image", "kb_ids": ["KB-944"], "summary": "KB-944: khi 0.5K lưu dưới nano_banana_31 và account chuyển sang pro, generate 2K (Dev 55697 Q1). TC-06 (build không ghi) thấy dropdown lúc đó không chọn gì (không hiện Default, không hiện 2K) — vế này chưa có xác nhận, không nạp. Cần: Dev xác nhận dropdown hiển thị gì ở pro với 0.5K đã lưu, hoặc test case có build."}
```

## OQ-artwork-313 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-313", "type": "OPEN_ISSUE", "feature_id": "layer-config-image", "kb_ids": ["KB-945"], "summary": "KB-945: qua API/MCP chỉ điền 1 field Flux thì được nhận nhưng bị bỏ qua, size theo tỉ lệ layer (Dev 55697 Q2) — phần này chưa được QA kiểm. Cần: Test case PASS có build gửi 1 field qua REST/MCP."}
```

## OQ-artwork-314 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-314", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-947"], "summary": "KB-947: portal không check 4 MP trước khi save, lỗi về từ server sau khi bấm Save và editor vẫn mở — chỉ từ Dev summary 55645 (Known limitation) và TC-15 (build không ghi). Đây có phải hành vi chấp nhận được? Cần: PO/Dev xác nhận nguyên văn có ngày (TIB-5561).", "check_ids": ["CHK-082"]}
```

## OQ-artwork-315 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-315", "type": "OPEN_ISSUE", "feature_id": "layer-config-image", "kb_ids": ["KB-948", "KB-946"], "summary": "KB-948 (known defect): thông báo 4 MP hiện ghi 'must be less than' trên cả 3 nơi dù biên là ≤ (KB-946). Dev đồng ý đổi sang 'must not exceed …' nhưng PO chưa trả lời (QA hỏi ở 55728, 2026-10-27). RA QA-3435 ghi Single upload là 'must not exceed' theo lịch sử QA-3181, trái quan sát TC-17 — chưa chọn bên nào. Cần: PO chốt chữ thông báo; sau khi ship, test case có build đọc lại chữ trên 3 nơi (kể cả GO Single upload).", "check_ids": ["CHK-084"]}
```

## OQ-artwork-316 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-316", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-950"], "summary": "KB-950: Gen AI effect của Single upload có Resolution 1K/2K/4K không có Default, GPT chọn sẵn 1K, Gemini 2K (TC-11, build không ghi; Dev summary 55645 gọi là khác biệt có chủ đích). Đây có phải expected? Cần: PO/Dev xác nhận nguyên văn có ngày (TIB-5561), hoặc test case có build và căn cứ expected.", "check_ids": ["CHK-074"]}
```

## OQ-artwork-317 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-317", "type": "OPEN_ISSUE", "feature_id": "layer-config-image", "kb_ids": ["KB-951"], "summary": "KB-951 (known limitation): sau khi chọn resolution không chọn lại Default được; GPT/Gemini phải tạo lại layer, Flux xoá cả 2 field. PO chưa xác nhận chấp nhận cho release (Dev 55697 Q5 'PO to confirm release'). Cần: PO trả lời trên TIB-5561 có chấp nhận cho release không; nếu không, ticket sửa.", "check_ids": ["CHK-076"]}
```

## OQ-artwork-318 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-318", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-952"], "summary": "KB-952: giá trị output size lưu dạng chuỗi trong layer JSON, giữ sau reload/duplicate, storefront generate dùng giá trị đó — chỉ là quan sát TC-08/09/27 (build không ghi, không có căn cứ expected cho lưu/reload/duplicate). Liên quan OQ-sdk-040 (object sdk, không gỡ). Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có build và căn cứ expected.", "check_ids": ["CHK-075"]}
```

## OQ-artwork-319 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-319", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-954"], "summary": "KB-954: ở đường portal/REST server không check lại allowed values của output size (Dev 55697 Q7 mô tả hiện trạng; TC-31 thấy giá trị lạ qua REST được lưu). Đây là hành vi chấp nhận hay cần thêm validate phía server? Cần: PO quyết; Dev xác nhận có ngày. Người quyết: PO (cờ requires_human_decision của diff cho KB-954).", "check_ids": ["CHK-081"]}
```

## OQ-artwork-320 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-320", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-955"], "summary": "KB-955: ô Flux width/height chỉ giữ số, Save ô rỗng báo required, tên GO chứa payload hiện nguyên chữ — chỉ là quan sát TC-33 (build không ghi, căn cứ expected KHÔNG CÓ). Đây có phải hành vi đúng? Cần: Dev/PO xác nhận, hoặc test case Testlane PASS có build và căn cứ expected. Người quyết: PO (cờ requires_human_decision của diff cho KB-955).", "check_ids": ["CHK-083"]}
```

## OQ-artwork-321 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-321", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-956"], "summary": "KB-956: cảnh báo thiếu API key trong danh sách effect của layer/GO editor mở rộng cho OpenAI/Flux/Gemini, Gen AI Effect khi chưa có default provider, Remove background khi chưa chọn remover — chỉ theo dev doc tự sinh từ branch diff (TIB-5470 53778), không có kết quả chạy có ngày. Đây có phải hành vi đúng? Cần: PO/Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có build (TC-32 hiện chỉ có status passed).", "check_ids": ["CHK-086"]}
```

## OQ-artwork-322 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-322", "type": "OPEN_ISSUE", "feature_id": "layer-config-image", "kb_ids": ["KB-957"], "summary": "KB-957: logic grouped_clipart theo chế độ manual/auto (Dev TIB-5412 52817). Manual/auto ứng với layer type nào (dynamic-by-text / clipart-frame là cách hiểu của QA) và 'option đầu tiên' theo thứ tự nào chưa rõ. TC-09 chưa viết lại, TC-10 chưa có kết quả chạy. Cần: Dev xác nhận mapping manual/auto sang layer type và thứ tự 'option đầu tiên', có ngày.", "check_ids": ["CHK-087"]}
```

## OQ-artwork-323 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-323", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["artwork/populate-values#KB-1000"], "summary": "CLAIM-27 (S0, không nạp KB): layer Dynamic Clipart by Text so khớp text buyer gõ với tên option clipart (origin_name/name) và group_name sau khi chuẩn hoá cả hai phía về Unicode NFC (tên lưu NFD khớp text gõ NFC và ngược lại; áp cho nguồn clipart và grouped_clipart). Chỉ có note kỹ thuật Dev TIB-5412 comment 51755 (2026-09-23), không ai xác nhận; TC QA Hub passed nhưng actualResult rỗng. Liên quan OQ-artwork-290, OQ-asset-category-045. Cần: Dev/PO xác nhận nguyên văn có ngày, PR teeinblue-sdk #2036 kèm diff (dev_doc), hoặc test case Testlane PASS có ngày, build và căn cứ expected. Thêm (CBS-115, 2026-11-11): rule QA FACT-164 (QA ghi nhận 2026-10-26, QA-3418 RQ10; QA nói chưa chắc cơ chế) ghi Dynamic Clipart by Text chọn clipart theo tên clipart khớp ký tự input ({{char1}}...), không theo tên file/asset — nạp KB-1000 (populate-values, PROPOSED/LOW), check CHK-058 của populate-values. Vẫn cần Dev/PO xác nhận cơ chế so khớp tên (và chuẩn hoá NFC).", "check_ids": ["CHK-088", "populate-values#CHK-058"]}
```

## OQ-artwork-324 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-324", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": [], "summary": "CLAIM-28 (S0, không nạp KB): sau chuẩn hoá NFC, tên ASCII vẫn khớp như cũ, so khớp vẫn phân biệt hoa thường, text rỗng hoặc chỉ khoảng trắng không khớp clipart nào. Chỉ có mục 'Possible test cases' trong note Dev TIB-5412 comment 51755 (2026-09-23), không ai xác nhận. Liên quan OQ-artwork-290, OQ-asset-category-045. Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected.", "check_ids": ["CHK-088"]}
```

## OQ-artwork-325 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-325", "type": "OPEN_ISSUE", "feature_id": "no-personalization-photo-render", "kb_ids": ["KB-932", "KB-933"], "summary": "KB-932, KB-933: mockup render ở danh sách Mockups chưa được kiểm theo fit rule của layer No personalization; chiều 'trước lần sync / Re-generate / save thì ảnh KHÔNG đổi' chưa được kiểm (không có đơn trước fix có layer ảnh mặc định trên staging). QA mới thấy chiều đổi sau sync/save (TC-21, TC-22). Cần: Test case có build cho mockup trong Mockups list và cho chiều chưa đổi trước sync/Re-generate/save (cần fixture dựng trước fix hoặc dữ liệu cũ).", "check_ids": ["CHK-003"]}
```

## OQ-artwork-326 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-326", "type": "OPEN_ISSUE", "feature_id": "no-personalization-photo-render", "kb_ids": ["KB-938"], "summary": "KB-938 (known defect): job order design fail khi layer No personalization không có ảnh mặc định và không có retrieval value (Dev 55639 RQ6, có từ trước TIB-5521). Ứng viên bug cho ticket riêng; chữ lỗi quan sát TC-30 'The url field is required.' khác tên exception dev nêu. Có cần ticket sửa và expected đúng là gì? Cần: PO quyết expected (vd chặn cấu hình hoặc render rỗng); Dev mở ticket riêng nếu sửa. Không tự tạo ticket — hỏi operator. Người quyết: PO (cờ requires_human_decision của diff cho KB-938).", "check_ids": ["CHK-004"]}
```

## OQ-artwork-327 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-327", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-931", "KB-860"], "summary": "KB-860 (populate-values) ghi preview storefront 'vẫn fit ảnh vào khung layer' với layer No personalization populate {{output}} từ Photo Reposition; KB-931 (quan sát) ghi ảnh populated thì contain. Chưa rõ 'fit' của KB-860 là contain hay fill; nếu là fill thì hai item lệch nhau. Không tự phân xử. Cần: Dev xác nhận có ngày (TIB-5504 hoặc TIB-5521)."}
```

## OQ-artwork-328 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-328", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-114", "KB-018", "KB-019", "KB-943"], "summary": "KB-114 (Flux Text to Image: ảnh theo tỉ lệ layer, không thấy field size) và inventory KB-018/KB-019 (quan sát 2026-09) có thể đã cũ với account dùng Flux 2 / GPT gpt-image-2 / Gemini, vì TIB-5561 thêm field output size theo model (KB-943). Base không ghi model của account lúc quan sát nên không tính là conflict. Cần: re-verify (REFRESH) field theo model của account, hoặc Dev xác nhận có ngày."}
```

## OQ-artwork-329 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-329", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-939", "KB-940", "KB-941", "KB-943", "KB-944"], "summary": "Tên model Gemini: KB-939..KB-941 dùng 'Nano Banana 2.1' (không có 0.5K), KB-943/KB-944 dùng key nano_banana_31 = 'Nano Banana 2 (3.1)' (có 0.5K). Hiện coi là hai model khác nhau; key API của Nano Banana 2.1 chưa ghi, và KB-943 chụp 2026-10-27, trước fix TIB-5573 Q2 (2026-10-30). Cần: Dev xác nhận key model và danh sách Resolution theo từng model."}
```

## OQ-artwork-330 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-330", "type": "NEEDS_CONFIRMATION", "feature_id": "no-personalization-photo-render", "kb_ids": ["KB-933"], "summary": "KB-933 (Dev TIB-5521 55637 Q2): sau fix TIB-5521 không có gì tự render lại; order design cũ chỉ đổi khi Re-generate, ảnh trên store đổi ở lần sync tới. Việc này chạm order/fulfillment. Người quyết: PO xác nhận ý định, và đơn đã render trước fix có cần regenerate không."}
```

## OQ-artwork-331 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-331", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "kb_ids": ["KB-970"], "summary": "KB-970: hai tab cùng sửa một layer thì lần save sau ghi đè cả layer, thay đổi của tab kia mất, không cảnh báo (QA-3435 TC-34, một lượt, TC chỉ ghi nhận). Last-save-wins cho cả layer có phải hành vi mong muốn không, có cần cảnh báo xung đột không? Có áp cho loại layer khác ngoài field AI provider không? Thêm (diff): mất dữ liệu chỉ giới hạn ở layer hai tab cùng sửa, hay lần Save sau ghi đè cả artwork (KB-052: PUT ghi toàn bộ artwork)?"}
```

## OQ-artwork-332 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-332", "type": "OPEN_ISSUE", "feature_id": "artwork-save-persist", "kb_ids": ["KB-971"], "summary": "KB-971 (known defect): PUT /api/artworks/{id} tự dựng vẫn lưu thay đổi trên layer locked: true (200), quan sát 2026-10-23 và 2026-10-30. Server có nên từ chối thay đổi trên layer locked không? Chưa có bug chính thức (chỉ draft)."}
```

## OQ-artwork-333 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-333", "type": "OPEN_ISSUE", "feature_id": "artwork-save-persist", "kb_ids": ["KB-972"], "summary": "KB-972 (known defect): Option title chứa ký tự NUL làm request lưu artwork trả 500, dữ liệu không đổi (build 2026-10-23). Bug NUL có sẵn đã sửa chưa, và hành vi mong muốn là từ chối có thông báo hay loại bỏ ký tự?"}
```

## OQ-artwork-334 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-334", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "kb_ids": ["KB-973"], "summary": "KB-973: thứ tự field sau khi thả ở tab Re-order giữ nguyên sau Save và mở lại editor, khớp GraphQL (QA-3352 TC-08, AI, một lượt, không ghi build). Cần xác nhận đây là hành vi mong muốn."}
```

## OQ-artwork-335 — CONFLICT

```json
{"oq_id": "OQ-artwork-335", "type": "CONFLICT", "feature_id": "artwork-save-persist", "kb_ids": ["KB-053", "KB-974"], "summary": "Nghĩa của templates[].positions: thứ tự render của layer (KB-053) hay thứ tự field của tab Re-order trong Form panel (KB-974)? Nếu là thứ tự form thì reorder ở tab Re-order có đổi thứ tự render không, và thứ tự render nằm ở đâu (templates[].layers?). Thêm (diff): reorder ở tab Re-order có đổi thứ tự render / order design không?", "side_a": "KB-053 (bootstrap 2026-09-10, một sample PUT full body): positions là mảng layer id theo thứ tự render.", "side_b": "KB-974 (ghi chú QA khi duyệt spec QA-3352 TC-03, 2026-09-28, không assert): thứ tự field của tab Re-order đọc lại ở positions, templates[].layers không đổi thứ tự khi reorder."}
```

## OQ-artwork-336 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-336", "type": "NEEDS_CONFIRMATION", "feature_id": "form-field-reorder", "kb_ids": ["KB-975"], "summary": "KB-975: kéo thả nhiều dòng liền nhau (≥10) ở tab Re-order đưa cả khối về ngay dưới dòng đích, giữ thứ tự (QA-3352 TC-03, AI, không ghi build). Cần xác nhận đây là hành vi mong muốn; căn cứ expected chỉ là dev summary ticket fix."}
```

## OQ-artwork-337 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-337", "type": "NEEDS_CONFIRMATION", "feature_id": "form-field-reorder", "kb_ids": ["KB-975", "KB-976"], "summary": "KB-975/KB-976: mỗi case multi-drag chỉ có một lượt PASS, trong khi lỗi gốc ngẫu nhiên theo index (dev gợi ý lặp 3–5 lần). Kết quả có ổn định qua nhiều lượt không?"}
```

## OQ-artwork-338 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-338", "type": "NEEDS_CONFIRMATION", "feature_id": "form-field-reorder", "kb_ids": ["KB-976"], "summary": "KB-976: các dòng không liền nhau sau khi kéo được gom theo thứ tự gốc của danh sách, không theo thứ tự click (QA-3352 TC-04, AI). Đây có phải hành vi mong muốn? Repro gốc của QA (2026-08-25) ghi kỳ vọng \"9-10-19...\" cho chuỗi click 9-10-19-11..18 — đó là thứ tự click hay tên dòng? Nếu là kỳ vọng theo thứ tự click thì trái quan sát."}
```

## OQ-artwork-339 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-339", "type": "NEEDS_CONFIRMATION", "feature_id": "form-field-reorder", "kb_ids": ["KB-977"], "summary": "KB-977: click thường (không phím bổ trợ) vào dòng chưa chọn thêm dòng đó vào selection ở tab Re-order. Cơ chế này chỉ có ghi nhận Slack không rõ người xác nhận; cần xác nhận là hành vi mong muốn."}
```

## OQ-artwork-340 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-340", "type": "NEEDS_CONFIRMATION", "feature_id": "form-field-reorder", "kb_ids": ["KB-978"], "summary": "KB-978: click lại dòng đang chọn bỏ chọn riêng dòng đó, click ra ngoài danh sách bỏ chọn tất cả (ảnh chụp máy TC-22, chưa ai tick). Cần người xác nhận; click ngoài danh sách mới thử ở tiêu đề tab, vùng khác chưa thử."}
```

## OQ-artwork-341 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-341", "type": "OPEN_ISSUE", "feature_id": "form-field-reorder", "kb_ids": ["KB-979"], "summary": "KB-979 (giới hạn đã biết): cụm nhiều dòng thả sát mép trên/dưới danh sách Re-order rơi về đầu/cuối danh sách thay vì đúng chỗ con trỏ. PO có chấp nhận giới hạn này không, có kế hoạch sửa không?"}
```

## OQ-artwork-342 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-342", "type": "NEEDS_CONFIRMATION", "feature_id": "form-field-reorder", "kb_ids": ["KB-980"], "summary": "KB-980: kéo một dòng ở tab Re-order thì dòng nằm ngay dưới dòng đích (automation, chưa kiểm tay). Cần xác nhận là hành vi mong muốn."}
```

## OQ-artwork-343 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-343", "type": "NEEDS_CONFIRMATION", "feature_id": "form-field-reorder", "kb_ids": ["KB-980"], "summary": "Tab Re-order: kéo một dòng thả xuống cuối danh sách luôn dừng ngay trước dòng cuối cùng ở lượt automation 2026-09-28 (lượt 2026-09-18 thì qua). Đây là giới hạn thật của widget (không có vùng thả sau dòng cuối) hay do cách giả lập chuột? Phần này không đưa vào KB."}
```

## OQ-artwork-344 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-344", "type": "NEEDS_CONFIRMATION", "feature_id": "form-field-reorder", "kb_ids": ["KB-981"], "summary": "KB-981: label chứa HTML/script hiển thị dạng chữ thường trong tab Re-order, không tạo node thật (QA-3352 TC-18, AI, không build). Phía storefront (form và console) chưa chạy vì thiếu campaign đã publish; artifact trích không thể hiện riêng bước reload. Cần xác nhận hành vi mong muốn và chạy phần storefront."}
```

## OQ-artwork-345 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-345", "type": "NEEDS_CONFIRMATION", "feature_id": "form-field-reorder", "kb_ids": ["KB-982"], "summary": "KB-982: label dài (5000 ký tự trong lượt test) và label có ký tự điều khiển được lưu nguyên, reorder/Save vẫn chạy (QA-3352 TC-20, AI). Giới hạn độ dài label theo field là bao nhiêu, vượt giới hạn thì cắt hay báo lỗi? Thêm (diff): ký tự điều khiển trong lượt test có gồm NUL không; NUL trong label có gây 500 như Option title (KB-972) không?"}
```

## OQ-artwork-346 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-346", "type": "NEEDS_CONFIRMATION", "feature_id": "form-field-reorder", "summary": "Shift-click trong tab Re-order làm gì? Hai quan sát ngược nhau: (a) ghi nhận Slack không rõ người xác nhận nói chọn dòng đó và mọi dòng phía trên tới đầu danh sách; (b) ảnh chụp máy TC-21 (2026-09-18, chưa tick) thấy chỉ chọn dải liền giữa hai lần click. Không nạp KB, không check nào assert shift-click."}
```

## OQ-artwork-347 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-347", "type": "NEEDS_CONFIRMATION", "feature_id": "form-field-reorder", "summary": "Dev summary ticket fix TIB-5354 (2026-09-07) nói fix chỉ nằm trong portal (tab Re-order, chỉ luồng multi-drag), API và SDK không đổi, thư viện kéo thả gốc chưa sửa. Chưa ai xác nhận phạm vi này. Các danh sách kéo thả nhiều dòng khác dùng cùng thư viện có bị lỗi sắp index tương tự không?"}
```

```json
{"oq_id":"OQ-artwork-348","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-004 “Click 'Cancel' trên dialog xoá artwork không thực hiện xoá” của feature artwork-list-management. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-349","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-005 “Kết quả sau khi click 'Mark as archive'” của feature artwork-list-management. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-350","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006 “Kết quả sau khi click 'Import to Translation'” của feature artwork-list-management. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-351","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “Delete artwork — soft-delete hay hard-delete, có khôi phục được không” của feature artwork-list-management. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-352","type":"NEEDS_CONFIRMATION","feature_id":"artwork-list-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Truy cập /artworks và các action list với role/tenant khác” của feature artwork-list-management. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-353","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “GET /api/artworks/{id} trả 405 Method Not Allowed” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-354","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011 “validate-default-value trả lỗi 4xx/5xx thật từ server” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-355","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-013 “2 field artwork_category_id/global_option_ids có thực sự persist ở nơi khác không” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-356","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-015 “Đọc lại artwork sau save — GraphQL riêng hay chỉ từ response PUT (CONF-007)” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-357","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-016 “Xác nhận OpenAPI spec cho Artwork API có tồn tại trên staging hay không (CONF-005)” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-358","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-017 “Save/đọc artwork với role khác owner / cross-tenant (TIB_USER_B)” của feature artwork-save-persist. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-359","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Hành vi btn-set-invisible khi artwork có ≥2 template” của feature artwork-template-management. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-360","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-009 “Kết quả sau khi 'Convert to Global Template'” của feature artwork-template-management. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-361","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-010 “Field 'Extra charge for this template' map tới field nào trong PUT body” của feature artwork-template-management. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-362","type":"NEEDS_CONFIRMATION","feature_id":"artwork-template-management","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011 “'Import from artwork' lấy nguồn từ danh sách /artworks” của feature artwork-template-management. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-363","type":"NEEDS_CONFIRMATION","feature_id":"clipart-category-storefront-behavior","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Single-type (Clipart Category›1) widget render RADIOGROUP thumbnail, item ứng layer.default_value pre-checked” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-364","type":"NEEDS_CONFIRMATION","feature_id":"clipart-category-storefront-behavior","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-003 “[NEEDS_CONFIRMATION] Group-type <select> chỉ có placeholder disabled, 0 item selectable dù category có 2 item xác nhận server-side” của feature clipart-category-storefront-behavior. current_behavior_only"}
```

```json
{"oq_id":"OQ-artwork-365","type":"NEEDS_CONFIRMATION","feature_id":"clipart-category-storefront-behavior","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “[NEEDS_CONFIRMATION] Server thêm key lạ 'artwork-<id>': <numeric> vào response customization save, không có ở client localStorage lúc ghi” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-366","type":"NEEDS_CONFIRMATION","feature_id":"clipart-category-storefront-behavior","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-013 “[NEEDS_CONFIRMATION] Preview size=500px 'không hoạt động đúng' (chỉ ra 250px) hay bị giới hạn bởi độ phân giải gốc file upload (no1.png/no2.png)?” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-367","type":"NEEDS_CONFIRMATION","feature_id":"clipart-category-storefront-behavior","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-017 “[CRITICAL, NEEDS_CONFIRMATION] Canvas/Preview modal/cart customization image compositing gap — chosen clipart never appears in rendered output” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-368","type":"NEEDS_CONFIRMATION","feature_id":"clipart-category-storefront-behavior","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-018 “[NEEDS_CONFIRMATION] Conflict CONF-CTX20260921-03-02 — nhánh WIDGET STOREFRONT: layer.default_value (không phải layer.url) là giá trị PRE-CHECK — đây có phải business rule dự kiến, và layer.url có nên là 1 lựa chọn hợp lệ trên storefront không?” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-369","type":"NEEDS_CONFIRMATION","feature_id":"clipart-category-storefront-behavior","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-019 “[GAP, NEEDS_CONFIRMATION] Hành vi buyer đã login / non-US market-locale-currency / mobile-tablet viewport cho personalization form clipart-category — 0 evidence trong run này” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-370","type":"NEEDS_CONFIRMATION","feature_id":"clipart-category-storefront-behavior","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-020 “[NEEDS_CONFIRMATION] Conflict CONF-API-CTX20260921-03-01 nhánh API ROOT EVIDENCE: GET /api/layer-image-categories trả [] vs GraphQL trả 10 rows cùng user/session (layer api, khác CHK-003 layer storefront)” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-371","type":"NEEDS_CONFIRMATION","feature_id":"clipart-category-storefront-behavior","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-021 “[POINTER, NEEDS_CONFIRMATION] CONF-CTX20260921-03-01 (Custom class field presence, layer-level) — KHÔNG có nhánh storefront, xem layer-config-image.json cho nội dung đầy đủ” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-372","type":"NEEDS_CONFIRMATION","feature_id":"clipart-category-storefront-behavior","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-022 “[GAP, NEEDS_CONFIRMATION] Hành vi personalization form khi 'Show option to select default value' = OFF — 0 evidence trong run này (chỉ test ON)” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-373","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “[CRITICAL] PUT trực tiếp với payload chứa đồ thị vòng — server có tự chặn độc lập với client?” của feature condition-cycle-validation. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-374","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-009 “PUT trực tiếp với self-loop (element trỏ chính layer đó)” của feature condition-cycle-validation. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-375","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-010 “Thuật toán chọn 'layer gốc' hiển thị đầu message lỗi với cấu trúc dependency khác” của feature condition-cycle-validation. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-376","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011 “Hành vi storefront nếu 1 artwork có vòng lọt qua được validation” của feature condition-cycle-validation. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-377","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Giới hạn số condition tối đa trên 1 layer” của feature conditional-setting-config. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-378","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-009 “Hỗ trợ lồng nhóm AND trong OR (nested logic)” của feature conditional-setting-config. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-379","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-010 “Toán tử condition ngoài 'is any of' và on/off (is-none-of, contains, so sánh số/ngày)” của feature conditional-setting-config. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-380","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011 “2 layer type không có accordion CONDITIONAL SETTING — có đường API bypass để set condition không” của feature conditional-setting-config. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-381","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-010 “Effect thật của Group/Ungroup sau khi bấm” của feature editor-layer-workspace. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-382","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011 “35 layer type trong popup có cố định qua các plan khác nhau không” của feature editor-layer-workspace. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-383","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-012 “Picker khác (image library, clipart) có rơi vào trạng thái rỗng tương tự Vector không” của feature editor-layer-workspace. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-384","type":"NEEDS_CONFIRMATION","feature_id":"layer-common-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006 “Field 'Custom class:' có ở 33/35 type theo DOM (mâu thuẫn với bundle-registry code — CONF-006)” của feature layer-common-config. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-385","type":"NEEDS_CONFIRMATION","feature_id":"layer-common-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Đối chiếu chéo trực tiếp 9 layer type nằm ngoài bundle-registry nhưng có 'Custom class' trên DOM” của feature layer-common-config. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-386","type":"NEEDS_CONFIRMATION","feature_id":"layer-condition-value-binding","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “dependencies[].element luôn có dạng 'layer-<6 chữ số>'” của feature layer-condition-value-binding. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-387","type":"NEEDS_CONFIRMATION","feature_id":"layer-condition-value-binding","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “toggle=false (Off) serialize thành gì — chưa từng được lưu qua Save” của feature layer-condition-value-binding. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-388","type":"NEEDS_CONFIRMATION","feature_id":"layer-condition-value-binding","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-009 “Multi-value (≥2 phần tử) cho 6/8 type nguồn dạng array còn lại (ngoài clipart-category)” của feature layer-condition-value-binding. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-389","type":"NEEDS_CONFIRMATION","feature_id":"layer-condition-value-binding","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-010 “Trạng thái data addon-charge/json-list trên artwork 4087 khác nhau giữa 2 run (CONF-002)” của feature layer-condition-value-binding. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-390","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-form-elements","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-009 “Color (color) — KHÔNG xuất hiện được làm nguồn Conditional Setting dù có đầy đủ Option Title (khác Font CÓ xuất hiện được) — nguyên nhân chưa xác nhận” của feature layer-config-form-elements. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-391","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Static Image (static-photo) — theo baseline chung NHƯNG là 1/2 type KHÔNG có field 'Custom class:'” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-392","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “Clipart Category › 1 Clipart category (clipart-category) — theo baseline chung, không có deviation riêng ghi nhận” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-393","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-003 “Clipart Category › Group of clipart categories (group-clipart-categories) — theo baseline chung, không có deviation riêng ghi nhận” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-394","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “Text to Image (AI) (text-to-image) — KHÔNG có DESIGN SETTINGS/POPULATE VALUES, thiếu option 'No personalization', nhãn GenAI service khác Multiple Uploads” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-395","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Text to Image (AI) vs Multiple Uploads — key JSON GenAI provider (text_to_image_provider vs multi_image_provider) chưa xác nhận qua PUT thật” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-396","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-018 “[NEW v3] Clipart Category (single) — full field inventory qua Bulk Edit (DESIGN/PERSONALIZATION/EXTRA)” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-397","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-021 “[NEW v3, NEEDS_CONFIRMATION] 'Select a group of clipart categories' có thực sự hỗ trợ multi-category hay chỉ 1 category nested children?” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-398","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-024 “[NEW v3] Portal canvas render tiếp tục dùng layer.url (KHÔNG dùng layer.default_value) sau Save & Close + mở lại” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-399","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-025 “[NEW v3, NEEDS_CONFIRMATION] Conflict CONF-CTX20260921-03-02 — nhánh PORTAL: lựa chọn tường minh 'default value' của merchant có NÊN ảnh hưởng canvas portal hay không?” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-400","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-026 “[NEW v3, NEEDS_CONFIRMATION] Group's default value combobox hiện 'List is empty.' dù category có 2 item xác nhận tồn tại cùng phiên” của feature layer-config-image. current_behavior_only"}
```

```json
{"oq_id":"OQ-artwork-401","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-027 “[NEW v3, NEEDS_CONFIRMATION] Conflict CONF-API-CTX20260921-03-01 nhánh PORTAL: GET /api/layer-image-categories trả [] rỗng trong khi GraphQL clipart_categories trả 10 rows cùng user/session” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-402","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-028 “[NEW v3, NEEDS_CONFIRMATION] Conflict CONF-CTX20260921-03-01 — field 'Custom class:' (layer-level, Clipart Category›1) có tồn tại thật hay đã mất so với canonical v2?” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-403","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-030 “[NEW v3, NEEDS_CONFIRMATION] API field 'show_clipart_name' (null observed) có đúng backing field cho UI toggle 'Show option name on hover'?” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-404","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-033 “[NEW v4, NEEDS_CONFIRMATION] Thứ tự accordion 'Populate Values đầu tiên' có cố định cho MỌI layer photo, hay chỉ khi Populate Values đã được cấu hình trước?” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-405","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-036 “[NEW v4, NEEDS_CONFIRMATION] Toggle 'Use Template Default Size' (ImagenHub, Multiple Uploads) — tác dụng khi bật ON chưa được test” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-406","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-038 “[NEW v4, NEEDS_CONFIRMATION] Rule 'prompt required' (Save & Close) — chỉ xác nhận với Gemini, chưa test OpenAI/Flux/ImagenHub (cả Multiple Uploads lẫn Text to Image)” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-407","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-041 “[NEW v4, NEEDS_CONFIRMATION] Token '{{input}}' trần có xuất hiện khi Maximum photos=1 (chưa test)?” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-408","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-043 “[NEW v4, NEEDS_CONFIRMATION] Cảnh báo unsupported-provider (Flux, Text to Image) — chỉ thử ở UI cấu hình, chưa thử lúc generate thật” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-409","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-045 “[NEW v4, NEEDS_CONFIRMATION] '+ Variable' picker hiển thị option gì khi artwork CÓ ≥1 layer Text/Additional Option khác?” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-410","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-048 “[NEW v4, NEEDS_CONFIRMATION] Text to Image (AI) có bao giờ được offer làm Populate Content source hay không — chỉ 1 sample phủ định” của feature layer-config-image. current_behavior_only"}
```

```json
{"oq_id":"OQ-artwork-411","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-049 “[NEW v4, NEEDS_CONFIRMATION] Beta badge KHÔNG xuất hiện cho Text to Image (AI) — chỉ xác nhận trên 2 bề mặt staff-authenticated, chưa test storefront PDP/theme thật” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-412","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-050 “[NEW v4, CONFLICTED, CONF-CBS003-01, NEEDS_CONFIRMATION] Verify hiện trạng số lượng/tên lựa chọn Personalization của Text to Image (AI) — KHÔNG chọn 1 phía làm oracle” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-413","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-051 “[NEW v4, NEEDS_CONFIRMATION, GAP] TIB-5188 — thứ tự resize/crop và minimum-resolution validation của pipeline GenAI (Multiple Uploads) HOÀN TOÀN CHƯA TEST” của feature layer-config-image. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-414","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-052 “[NEW v4, NEEDS_CONFIRMATION, GAP] TIB-5339 — so sánh sync vs async giữa route upload chính (presigned-S3) và route fallback (multipart) KHÔNG so sánh được” của feature layer-config-image. current_behavior_only"}
```

```json
{"oq_id":"OQ-artwork-415","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-image","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-053 “[NEW v4, NEEDS_CONFIRMATION, GAP] 'Duplicate & Share' (TIB-5326) — control không tìm thấy ở portal editor lẫn storefront Live Preview cho Multiple Uploads/Text to Image” của feature layer-config-image. current_behavior_only"}
```

```json
{"oq_id":"OQ-artwork-416","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-maps-astronomy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “Street Maps (maps) — hành vi khi thiếu Mapbox access token (3rd-party Services) chưa xác nhận” của feature layer-config-maps-astronomy. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-417","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-maps-astronomy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006 “Moon Phase (moon-phase) — chính tả field code 'maps_seacher_enabled' cần giữ nguyên khi viết assertion, không tự sửa thành 'searcher'” của feature layer-config-maps-astronomy. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-418","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-others","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-004 “QR Code (qr-code) — hành vi khi nhập vượt quá 4296 ký tự chưa được thử (chặn/cắt/lỗi)” của feature layer-config-others. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-419","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-puzzles","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-004 “Word Search (word-search) — chuỗi 'Custom class:' xuất hiện HAI LẦN trong panel DOM, chưa xác nhận 2 field riêng hay lỗi duplicate render” của feature layer-config-puzzles. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-420","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-text","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Single-line Text (text) — tuân theo baseline chung, không có deviation field riêng ghi nhận” của feature layer-config-text. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-421","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-text","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “Curve Text (curve-text) — tuân theo baseline chung, không có deviation field riêng ghi nhận” của feature layer-config-text. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-422","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-text","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-005 “Other › Spiral Text (spiral-text) — hành vi khi nhập Inner radius < 20 chưa xác nhận” của feature layer-config-text. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-423","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-text","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “Paragraph › Normal (paragraph) — key JSON thật của 'Remove line breaks' chưa xác nhận, chưa viết được assertion API” của feature layer-config-text. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-424","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-vector","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Static Vector (static-vector) — theo baseline chung NHƯNG là 1/2 type KHÔNG có field 'Custom class:'” của feature layer-config-vector. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-425","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-vector","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “Static Vector (static-vector) — chưa có per-type DOM dump riêng ngoài việc thiếu Custom class” của feature layer-config-vector. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-426","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-vector","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “[MỚI,, CBS-004] Rate-limit Static Vector (POST /api/layer-images/svg, resource user_rate_limiter:layer_image) — giá trị limit=1000, reset=86400s (24h)” của feature layer-config-vector. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-427","type":"NEEDS_CONFIRMATION","feature_id":"layer-config-vector","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “[MỚI,, CBS-004] Hành vi giảm của x-ratelimit-remaining trên POST /api/layer-images/svg — CONF-CBS004-001 UNRESOLVED, KHÔNG dùng làm oracle” của feature layer-config-vector. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-428","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Nút 'Duplicate & Link options' luôn hiện diện, tên giống nhau mọi layer type” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-429","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “20 layer type nhóm LINKED — config panel rút gọn còn 2 accordion sau khi Duplicate & Link” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-430","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-003 “15 layer type nhóm PLAIN_COPY — giữ nguyên đầy đủ accordion sau khi Duplicate & Link” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-431","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-004 “Duplicate & Link options không sinh network request (client-side cho tới Save)” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-432","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-005 “Layer row của bản LINKED KHÔNG có icon chain — icon set luôn cố định 5 icon (CONF-003)” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-433","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006 “Sau Save, sửa layer gốc có thực sự đồng bộ (sync) sang bản LINKED không” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-434","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “Layer type chưa test rơi vào nhóm LINKED hay PLAIN_COPY khi Duplicate & Link” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-435","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Shape JSON của layer LINKED trong PUT body (field đánh dấu linked/source_layer_id)” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-436","type":"NEEDS_CONFIRMATION","feature_id":"layer-print-effects","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Nút Print Effects mở popover shape-cut với 5 preset + Customize” của feature layer-print-effects. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-437","type":"NEEDS_CONFIRMATION","feature_id":"layer-print-effects","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “Nút 'Apply layout' disabled khi 0 shape-cut được chọn” của feature layer-print-effects. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-438","type":"NEEDS_CONFIRMATION","feature_id":"layer-print-effects","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-003 “Customize cho phép tuỳ chỉnh grid rows/columns” của feature layer-print-effects. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-439","type":"NEEDS_CONFIRMATION","feature_id":"layer-print-effects","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-004 “Footnote nguyên văn trong popover Print Effects” của feature layer-print-effects. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-440","type":"NEEDS_CONFIRMATION","feature_id":"layer-print-effects","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-005 “[CONF-004] Tính năng emboss có tồn tại hay không — KHÔNG được khẳng định là không tồn tại” của feature layer-print-effects. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-441","type":"NEEDS_CONFIRMATION","feature_id":"layer-print-effects","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006 “Print Effects config lưu vào field nào trong PUT body” của feature layer-print-effects. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-442","type":"NEEDS_CONFIRMATION","feature_id":"layer-print-effects","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “Trang 'Order Design' — nơi effect layer thực sự hiển thị làm production guide” của feature layer-print-effects. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-443","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-015 “13 nhóm nguồn Browse values có bao phủ đầy đủ mọi layer/output type không” của feature populate-values. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-444","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-016 “Cú pháp thật của {{value.formula(<expression>)}} và {{value.context.<from>To<to>}}” của feature populate-values. missing_or_unresolved_oracle. Bổ sung CBS-110 (2026-11-11): KB-987, KB-988, KB-991 (PROPOSED, rule QA) mô tả một phần kết quả token formula/context sai; chưa đủ làm expected cho CHK-016, xem CHK-046, CHK-047, CHK-050"}
```

```json
{"oq_id":"OQ-artwork-445","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-017 “Cơ chế khoá Google-Font-lock có áp dụng cho channel Background/Shape không (chỉ test Font/Color)” của feature populate-values. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-446","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-018 “Layer đã populate hiển thị giá trị thật (không phải placeholder) trên storefront” của feature populate-values. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-447","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-020 “[NEW v3, NEEDS_CONFIRMATION] Token '{{input}}' trần có xuất hiện khi Maximum photos=1 hay không?” của feature populate-values. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-448","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-021 “[NEW v3, NEEDS_CONFIRMATION] Text to Image (AI) có bao giờ được offer làm Populate Content source hay không — chỉ 1 sample phủ định” của feature populate-values. current_behavior_only"}
```

```json
{"oq_id":"OQ-artwork-449","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-023 “[NEW v3, NEEDS_CONFIRMATION] Nửa 'layer đích tự động trigger effect chain riêng khi nhận giá trị populate' (liên quan TIB-5302) — chưa xác nhận” của feature populate-values. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-artwork-450","type":"NEEDS_CONFIRMATION","feature_id":"populate-values","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-024 “[NEW v3, NEEDS_CONFIRMATION] Hành vi propagation (KB-008, CHK-022) có giữ nguyên trên guest session thật hay không — hiện chỉ có staff-authenticated proxy” của feature populate-values. missing_or_unresolved_oracle"}
```

## OQ-artwork-451 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-451","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"[CBS-140, KB-983, spec-hub rule conditional-options-no-loops và artwork-editor-layer-checks] Spec-hub ghi condition giữa các layer không được tạo vòng (A phụ thuộc B và B phụ thuộc A), artwork không lưu được tới khi gỡ vòng, và editor kiểm điều này trước khi save. Dev xác nhận đây là hành vi đúng không? Rule không nói server có chặn payload vòng gửi thẳng qua API (OQ-artwork-036) hay self-loop (OQ-artwork-037); nếu server cũng chặn thì Dev nêu rõ.","kb_ids":["KB-983"]}
```

## OQ-artwork-452 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-452","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"[CBS-140, KB-984, spec-hub rule photo-upload-effect-rate-limit và photo-upload-network-limit] Spec-hub ghi shopper upload ảnh có effect AI/xử lý bị giới hạn 5 lần mỗi giờ cho mỗi option (mặc định, đổi được theo shop) và 50 lần mỗi giờ cho mỗi network trên mọi option và shop; upload có effect từ portal tính vào giới hạn network. Dev xác nhận các ngưỡng mặc định này không? Lượt Run effects trong artwork editor (quota riêng KB-814) có tính vào giới hạn network 50/giờ không? Spec-hub có hai chữ thông báo cho giới hạn theo option ('You've reached the image effect upload limit for this option...' và 'Upload limit exceeded for this field...'): shopper thấy chữ nào? sdk KB-051 (Dev, Jira TIB-5460, 2026-09-17) ghi giới hạn tính theo visitor và cửa sổ trên staging là 5 phút thay vì 1 giờ: giới hạn tính theo shopper theo option hay theo visitor, và trên staging cửa sổ là bao lâu?","kb_ids":["KB-984"]}
```

## OQ-artwork-453 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-453","type":"NEEDS_CONFIRMATION","feature_id":"run-image-effects","summary":"[CBS-140, KB-985, spec-hub rule image-effects-background-remover và image-effects-needs-key] Spec-hub ghi xoá nền dùng remover merchant chọn (account remove.bg/Removal.AI/Cutout.Pro của merchant, remover built-in của Teeinblue, hoặc gói Teeinblue x Removal.ai), và khi xử lý ảnh shopper upload thì effect của dịch vụ ngoài thiếu key bị bỏ qua âm thầm, effect của Teeinblue không cần key. Rule không nêu surface; run suy scope là xử lý ảnh shopper upload từ ví dụ của rule. Dev xác nhận đây là hành vi đúng khi xử lý ảnh shopper upload không? Rule 'bỏ qua âm thầm' có áp cho cả Run effects trong artwork editor không? Nếu có thì trái KB-816 (thiếu key thì không chạy và hiện warning); nếu không thì hai đường có cố ý khác nhau không?","kb_ids":["KB-985"]}
```

## OQ-artwork-454 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-454","type":"NEEDS_CONFIRMATION","feature_id":"artwork-save-persist","summary":"[CBS-109, KB-986, rule QA FACT-179] Rule QA ghi format file order design (AI, EPS, PDF, SVG, PNG, JPEG…) do field 'Artwork design format' (multi-select) trong dialog 'Artwork details' của artwork quyết định, Save cùng artwork, và artwork editor không có nút Export/Download design riêng. Chưa có order thật đối chiếu (QA-3416 TC-29 tạm hoãn). Dev xác nhận: (1) đây có phải nơi duy nhất chọn format file design không; (2) khi chọn nhiều format thì một line item sinh file design cho mọi format đã chọn hay chỉ một; (3) lựa chọn multi-select lưu vào field nào và dạng gì, vì KB-053 mới thấy design_format là một chuỗi 'rgb' trong body PUT. Liên quan CHK-026.","kb_ids":["KB-986","KB-053"],"owner":"Dev"}
```

## OQ-artwork-455 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-455", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-110, KB-987, rule QA FACT-022 nhóm 1] Rule QA ghi token có shape hợp lệ nhưng nội dung sai ra layer đích rỗng ('Default text'): {{value.context.<from>To<to>}} với đơn vị không hỗ trợ hoặc typo (yearToFortnight, yaerToMonth); {{value.formula(...)}} đủ ngoặc nhưng biểu thức sai (chia 0, thiếu vế, ký tự % hoặc ^); hậu tố .N hỏng nằm trong ngoặc. Mới là hành vi quan sát ở Live Preview trên staging (lượt chạy tự động QA-3353), mô tả của Dev chỉ nói 'formula/unit không hiểu thì layer để trống'. PO xác nhận đây là hành vi đúng không? Storefront và design file có cho cùng kết quả không? Liên quan CHK-046.", "kb_ids": ["KB-987"], "owner": "PO"}
```

## OQ-artwork-456 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-456", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-110, KB-988, rule QA FACT-022 nhóm 2] Rule QA ghi token trong namespace value. không phải format hợp lệ hoàn chỉnh ({{value.context.yearTo}}, {{value.context}}, {{value.wibble}}, {{value.contextt.yearToMonth}}, {{value.formula(origin+}}, {{value.formula(origin/3).abc}}) ra raw-value fallback: layer đích hiện giá trị nguồn, không rỗng. PO có duyệt việc hiện giá trị nguồn thay vì rỗng cho các token này không, và ranh giới 'ký tự sai trong hay ngoài ngoặc' có phải hành vi chủ ý không? Liên quan CHK-047.", "kb_ids": ["KB-988"], "owner": "PO"}
```

## OQ-artwork-457 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-457", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-110, KB-989, rule QA FACT-022 nhóm 3] Rule QA ghi token {{...}} không có prefix value ({{7*7}}, {{foobar}}, {{name}}) trong layer populate ra rỗng, không tính biểu thức, raw-value fallback chỉ áp trong namespace value. và resolver không in token chưa resolve ra nguyên văn. PO/Dev xác nhận đây là hành vi đúng không, kể cả trên storefront và design file? Liên quan CHK-048.", "kb_ids": ["KB-989"], "owner": "PO"}
```

## OQ-artwork-458 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-458", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-110, KB-990, rule QA FACT-023] Rule QA ghi nguồn Date picker (giá trị YYYY-MM-DD) cho {{value}} ra đúng ngày nhưng {{value.context.*}} và {{value.formula(...)}} ra rỗng, và nhóm 'Text & Curve Text' không có token ngày/now nên không tính được số ngày kể từ một ngày. Đây là giới hạn mong muốn hay lỗi? Nếu là lỗi thì ghi nhận như known defect; Calendar layer với token {{date.<format>}} chưa kiểm. Liên quan CHK-049.", "kb_ids": ["KB-990"], "owner": "PO"}
```

## OQ-artwork-459 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-459", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-110, KB-991, rule QA FACT-024] Rule QA ghi {{value.context.*}} dùng năm 365.2425 ngày, tháng 1/12 năm, dựng cứng, không có tuỳ chọn 365 ngày (đo: 40 yearToDay = 14610). Bản 'Change summary & test cases' của Dev trên Jira TIB-5385 (2026-09-07) mô tả đây là quyết định sản phẩm có chủ ý. Dev xác nhận nguyên văn có ngày đây là hành vi đã chốt và không có cấu hình khác không? Liên quan CHK-050.", "kb_ids": ["KB-991"], "owner": "Dev"}
```

## OQ-artwork-460 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-460", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-110, KB-992, rule QA FACT-100] Rule QA đo {{value.<N>char}}: .0char rỗng, X vượt độ dài ra nguyên chuỗi, .abcchar raw fallback, .-1char cắt bớt 1 ký tự cuối (khác initialofword.-1 ra raw fallback), .1.5char nhận số thập phân. Dev xác nhận đây là hành vi đúng hay lỗi (nhất là X âm và X thập phân), và bản đo đã ship production chưa? Liên quan CHK-051.", "kb_ids": ["KB-992"], "owner": "Dev"}
```

## OQ-artwork-461 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-461", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-110, KB-993, rule QA FACT-063] Rule QA ghi text layer tĩnh (không gắn populate/personalization config) không đi qua populate resolver, content {{7*7}} hay <b>bold</b> hiện nguyên văn ở editor và ở render server-side (Preview/mockup). Lượt chạy chỉ thấy phía server-side sinh thumbnail thành công, không đọc được chữ. Dev xác nhận nguyên văn có ngày cho cả editor, Preview/mockup và design file không? Liên quan CHK-052.", "kb_ids": ["KB-993"], "owner": "Dev"}
```

## OQ-artwork-462 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-462", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-115, KB-994, rule QA FACT-094] Rule QA ghi option {{value.initialofword.X}} có trong Available values và resolve đúng trên Single-line Text, Curve Text, Warp Text, Paragraph (làm đích) và QR Code (QR mã hoá chuỗi đã resolve), picker không có type 'Shape Text'/'Clipart Frame'. Nguồn là lượt chạy tự động QA-3364 do AI ghi, build không rõ. Dev xác nhận danh sách layer đích này, kể cả storefront và design file? Liên quan CHK-053.", "kb_ids": ["KB-994"], "owner": "Dev"}
```

## OQ-artwork-463 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-463", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-115, KB-995, rule QA FACT-094] Rule QA (đo 2026-09-16) ghi Spiral Text và Clipart Category làm đích không có nhóm token text trong Browse values, không chọn được layer text làm nguồn. Theo CCR QA-3393, TIB-5271 (production 2026-10-26) đổi nhóm thành 'Text, Curve Text, Warp Text & Spiral Text' và cho Spiral làm nguồn. Vế Spiral Text còn đúng không, nên bỏ hay sửa? Vế Clipart Category còn đúng không? Liên quan CHK-054.", "kb_ids": ["KB-995"], "owner": "Dev"}
```

## OQ-artwork-464 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-464", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-115, KB-997, rule QA FACT-096] Rule QA (QA đính chính 2026-10-15, QA-2844) ghi 'Populate X from another option' luôn trỏ tới một layer cụ thể, không bao giờ trỏ trực tiếp tới Global Option; Global Option chỉ là container. Dev xác nhận đây là thiết kế đã chốt? Liên quan CHK-055.", "kb_ids": ["KB-997"], "owner": "Dev"}
```

## OQ-artwork-465 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-465", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-115, KB-998, rule QA FACT-096] Rule QA ghi dropdown nguồn lọc theo type: Content nhận Single-line Text (Paragraph không làm nguồn), Color chỉ layer color (layer text ra 'List is empty' dù set qua API vẫn lưu field), Background chỉ clipart-category/group-clipart-categories. Dev xác nhận? Vế Paragraph không làm nguồn Content còn đúng sau TIB-5271 không? API nhận nguồn sai type là chủ ý hay thiếu validate? Liên quan CHK-056.", "kb_ids": ["KB-998"], "owner": "Dev"}
```

## OQ-artwork-466 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-466", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "summary": "[CBS-115, KB-999, rule QA FACT-162] Rule QA (2026-10-23, QA-3416 BUG-05) ghi Populate Color của shape/vector/text chỉ trỏ vào một layer Color trong cùng artwork, không có field trỏ Shopify Color variant, nên fixture chỉ cần một layer Color thường. Dev xác nhận? TIB-4726 chưa Passed: khi nào ship, và canvas editor có đồng bộ màu không (claim đồng bộ không nạp vì không nguồn)? Liên quan CHK-057, OQ-artwork-090.", "kb_ids": ["KB-999"], "owner": "Dev"}
```

## OQ-artwork-467 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-467", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "summary": "[CBS-117, KB-1001] Mô tả của dev trong description TIB-5397 (2026-09-03) ghi Artwork 2.0 khi chọn nhiều layer ở Apply for Individual: ô Width hiện width chung hoặc Mixed khi các layer khác width, và group width tính lại từ bounding box của selection sau mỗi lần đổi width của layer bất kỳ. Dev/PO xác nhận đây là hành vi mong muốn? Bản tóm tắt của QA ghi 'Width hiện width thật của từng layer' — câu nào đúng? Liên quan CHK-001, CHK-002.", "kb_ids": ["KB-1001"], "owner": "Dev"}
```

## OQ-artwork-468 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-468", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "summary": "[CBS-117, KB-1002] Change note của dev trên TIB-5397 (2026-09-10) ghi Artwork 1.0 bỏ hẳn Apply for: Group / Individual khỏi Transform popover, multi-select chỉ còn Width/Height/Top/Left/Rotate/Fit to canvas/Flip như trước TIB-5197, seller 1.0 đặt auto-scale max width theo từng layer. PO xác nhận đây là hành vi mong muốn của Artwork 1.0? Liên quan CHK-003.", "kb_ids": ["KB-1002"], "owner": "PO"}
```

## OQ-artwork-469 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-469", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": [], "summary": "[CBS-117] CLAIM-04 (S0, không nạp KB): số đo QA trên fixture Artwork 1.0 staging 2026-09-16 ghi Undo/Redo 1 bước cho cả nhóm, Fit to canvas neo top-left (không căn giữa, ghi là cả 1.0 lẫn 2.0), Flip ở Artwork 1.0 lật ảnh từng layer tại chỗ (không group-mirror), ô số 0/âm/rỗng/chữ không đổi layer nhưng ô vẫn hiện giá trị đó, 99999/12.5/1e3 được chấp nhận. Đây có phải hành vi mong muốn không? Không có nguồn PO/Dev. Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected; hoặc locator rule QA có path trong repo QA.", "owner": "Dev"}
```

## OQ-artwork-470 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-470", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": [], "summary": "[CBS-117] CLAIM-05 (S0, không nạp KB): kết quả test local ghi Artwork 1.0 không vẽ box cá nhân (.artwork-layer-frame) dù account đang lưu preference Individual, sau khi fix bug nội bộ BUG-127; ghi chú cũ 'Artwork 1.0 vẫn đọc preference để vẽ box' được coi là lỗi thời. Xác nhận hành vi này, và Artwork 1.0 có cần đọc preference Apply for nữa không? Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected; hoặc locator rule QA có path trong repo QA.", "owner": "QA lead"}
```

## OQ-artwork-471 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-471", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": [], "summary": "[CBS-117] CLAIM-06 (S0, không nạp KB): QA chốt 'Group' trong radio Apply for: Group/Individual nghĩa là coi cả multi-selection trên canvas như một khối, không liên quan loại layer group (container lồng layer con). Dev/PO xác nhận hai khái niệm độc lập? Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected; hoặc locator rule QA có path trong repo QA.", "owner": "Dev"}
```

## OQ-artwork-472 — CONFLICT

```json
{"oq_id": "OQ-artwork-472", "type": "CONFLICT", "feature_id": "transform-multi-select", "kb_ids": [], "summary": "[CBS-117] CLAIM-07 (S0, không nạp KB): nhập 0 hoặc số âm vào ô Width/Height/Top/Left của Transform bị bỏ qua hoàn toàn hay clamp về 1px? Số đo cùng lượt QA: nhỏ nhất áp được là 1 (0.5 làm tròn lên 1), 99999 áp cho mọi layer đang chọn không có max, chữ bị input type=number lọc, để trống rồi blur trả về giá trị cũ, ô không gọi API khi blur. Hành vi mong muốn hay lỗi? Cần: Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected.", "owner": "Dev", "side_a": "Dev dự đoán ở RQ6 (QA-3361, 2026-09-16, chưa có nguyên văn): 0/số âm clamp về 1px.", "side_b": "Số đo QA staging 2026-09-16 (QA-3361 TC-35, kết quả local): 0/số âm bị bỏ qua hoàn toàn, ô hiện số vừa gõ nhưng layer không đổi, chọn lại layer thì ô về giá trị cũ."}
```

## OQ-artwork-473 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-473", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": [], "summary": "[CBS-117] CLAIM-08 (S0, không nạp KB): kết quả test local ghi preference Apply for: Group/Individual lưu theo account, chỉ đọc lúc load editor, không sync live giữa các tab cùng account; tab đổi mode sau cùng là giá trị cho lần load kế tiếp. Ghi chú 'dev chốt RQ11 2026-09-16' chưa có nguyên văn. Dev xác nhận? Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected; hoặc locator rule QA có path trong repo QA.", "owner": "Dev"}
```

## OQ-artwork-474 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-474", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": [], "summary": "[CBS-117] CLAIM-09 (S0, không nạp KB): QA quan sát Apply for không mặc định Group khi mở popover mà là state per-account để lại từ lần trước (production thấy Individual), nên test phải tự set tường minh. Mặc định thiết kế cho account mới là gì? Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected; hoặc locator rule QA có path trong repo QA.", "owner": "PO"}
```

## OQ-artwork-479 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-479", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-puzzles", "kb_ids": ["KB-1006"], "summary": "[CBS-123] KB-1006 (rule QA FACT-004): layer Word Cloud luôn required, buyer không thể để trống. PO xác nhận đây là hành vi đúng đã ship? Thêm: field có hiện dấu bắt buộc và aria-required không, và 'Default words (only for preview)' chỉ dùng cho preview trong editor hay là fallback khi input rỗng (vế này chưa nạp vì chỉ có ghi chú QA không mã rule và test local). Liên quan CHK-009. Cần: PO/Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS kèm căn cứ expected."}
```

## OQ-artwork-480 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-480", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-puzzles", "kb_ids": ["KB-1007"], "summary": "[CBS-123] KB-1007 (rule QA FACT-009): dedupe từ trùng của Word Cloud là case-sensitive và chạy sau transform Text case (Normal giữ Love/love/LOVE là 3 từ; UPPERCASE/lowercase/Capitalize gộp thành 1). Dev xác nhận, kể cả nhánh Capitalize (phân tích yêu cầu còn ghi cần kiểm phía nào của transform áp dụng, chưa có test case riêng)? Liên quan CHK-010."}
```

## OQ-artwork-481 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-481", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-puzzles", "kb_ids": ["KB-1008"], "summary": "[CBS-123] KB-1008 (rule QA FACT-012): Word Cloud có Drop shadow và shadow của origin propagate sang linked copy. Dev xác nhận đã ship? Linked copy có control shadow riêng không (vế này chưa nạp, chỉ có kết quả test local)? KB-031 hiện không liệt kê Drop shadow trong Design settings. Liên quan CHK-011."}
```

## OQ-artwork-482 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-482", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-puzzles", "kb_ids": [], "summary": "[CBS-123] CLAIM-02 (S0, không nạp KB): bấm 'Regenerate layout' nhiều lần ra layout khác nhau là đúng (mỗi lần bấm seed tăng 1, từ/shape/màu/số từ giữ nguyên, chỉ layout đổi)? Đã ship chưa? Mới thấy qua seed và request render trong test local, chưa so ảnh. Cần: Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS kèm căn cứ expected, hoặc rule QA FACT-005 kèm ngày ghi nhận."}
```

## OQ-artwork-483 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-483", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "kb_ids": ["KB-1009"], "summary": "[CBS-127] KB-1009 (rule QA FACT-032): popup Convert to another layer hiện type hiện tại ở dòng 'FROM X TO Y' (.convert-layer-popup__value là type đích chọn sẵn); convert tự áp dụng không cần Save nhưng chỉ ghi vào draft local của browser, GraphQL trả bản cũ tới khi Save; Cancel editor + confirm native thì hoàn lại. Dev xác nhận đây là hành vi chủ ý đã ship? Liên quan CHK-026. Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS kèm căn cứ expected."}
```

## OQ-artwork-484 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-484", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-common-config", "kb_ids": ["KB-1010"], "summary": "[CBS-127] KB-1010 (rule QA FACT-048): bộ property cấu hình (design/personalization) của layer khác nhau theo từng layer type, không có danh sách dùng chung; font size ở typography.size lồng bên trong, Word Cloud có font_size_min/max riêng; convert để lại key thừa. Dev xác nhận còn đúng và có schema theo type để đối chiếu không? Rule không chạm 7 field common envelope của KB-055. Liên quan CHK-014 (layer-common-config). Cần: Dev xác nhận nguyên văn có ngày."}
```

## OQ-artwork-485 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-485", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "kb_ids": ["KB-1011"], "summary": "[CBS-127] KB-1011 (rule QA FACT-073): layer vector-family (static-vector, vector-category, vector-upload, legacy vector) không có nút Replace (la-exchange-alt) ở layer row lẫn panel la-pen. PO xác nhận đây là thiết kế đã ship? ('đúng thiết kế' trong rule là lời QA chốt khi test). Vế image-family có Replace chưa nạp, chờ operator quyết cách đọc so với KB-002 (5 icon trên layer row). Liên quan CHK-027. Cần: PO xác nhận nguyên văn có ngày."}
```

## OQ-artwork-486 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-486", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "kb_ids": ["KB-1012"], "summary": "[CBS-127] KB-1012 (rule QA FACT-074): thumbnail layer vector trong layer panel là file .svg gốc trong img, không có biến thể _thumbnail; tắt cache thì SVG tải 2 lần (canvas + row 28px), bật cache thì lần 2 trúng HTTP cache. Dev xác nhận là thiết kế được chấp nhận? (bug draft đã rút 2026-09-11, chỉ là QA chấp nhận). Liên quan CHK-028. Cần: Dev xác nhận nguyên văn có ngày."}
```

## OQ-artwork-487 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-487", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "kb_ids": ["KB-1013"], "summary": "[CBS-127] KB-1013 (rule QA FACT-074): SVG thiếu viewBox/kích thước không upload được: POST /api/layer-images/svg trả 500, dropzone hiện '[object Object]' (rule ghi là bug riêng mức Low). Dev xác nhận còn hiện hành không, expected đúng khi từ chối file là gì (status, message), và bug đã có ticket chưa? Liên quan CHK-029. Cần: Dev xác nhận nguyên văn có ngày."}
```

## OQ-artwork-488 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-488", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "kb_ids": ["KB-1014"], "summary": "[CBS-127] KB-1014 (rule QA FACT-074): layer vector chỉ được thêm vào editor từ storage của TIB, không có nguồn vector bên ngoài. Dev xác nhận? (nguồn chỉ là 'user chốt' trong rule). Liên quan CHK-030. Cần: Dev xác nhận nguyên văn có ngày."}
```

## OQ-artwork-489 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-489", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "kb_ids": ["KB-1015"], "summary": "[CBS-127] KB-1015 (rule QA FACT-098): trong popup 'Select a layer type' của Artwork 2.0, 'shape text' là layer Paragraph (không phải type riêng) và 'clipart frame' không tồn tại. Dev xác nhận? Liên quan CHK-031. Danh sách 28 type của rule so với 29 item/35 type của KB-001 chưa nạp, chờ operator quyết. Cần: Dev xác nhận nguyên văn có ngày."}
```

## OQ-artwork-490 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-490", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "kb_ids": ["KB-1016"], "summary": "[CBS-127] KB-1016 (rule QA FACT-140): bấm nút Undo/Redo trên toolbar làm layer đang chọn mất focus (warp-point-handle, chip resize ẩn), còn Cmd/Ctrl+Z thì không. Dev xác nhận đây là hành vi chủ ý hay lỗi, đã ship chưa? Liên quan CHK-032. Cần: Dev xác nhận nguyên văn có ngày."}
```

## OQ-artwork-491 — CONFLICT

```json
{"oq_id": "OQ-artwork-491", "type": "CONFLICT", "feature_id": "editor-layer-workspace", "kb_ids": [], "summary": "[CBS-127] CLAIM-08 (S0, không nạp KB): TIB đã có layer type 'shape' (Rectangle/Ellipse/Line) chưa, và danh sách layer type hiện hành sau TIB-4726 (Add basic shapes, đang QA Review) gồm những type nào? Hai ghi chép của QA ngược nhau; KB-001 (29 item / 35 data-type, oracle CHK-001/CHK-009) giữ nguyên, không vào conflict_group. Cần: Dev xác nhận nguyên văn có ngày danh sách type hiện hành.", "side_a": "Ghi chép QA (CBS-127 CLAIM-08): đo qua MCP schema 2026-09-17 (QA-3361) thấy 33 layer type, không type nào tên shape.", "side_b": "Ghi chép QA FACT-158 (2026-10) nêu trong CBS-127: popup type có Rectangle/Ellipse/Line, nhiều khả năng do TIB-4726; base KB-001 ghi 35 data-type."}
```

## OQ-artwork-492 — CONFLICT

```json
{"oq_id": "OQ-artwork-492", "type": "CONFLICT", "feature_id": "editor-layer-workspace", "kb_ids": [], "summary": "[CBS-127] CLAIM-03 vế b (chưa nạp KB, chờ quyết định): layer image-family (static-photo, photo, clipart-category, group-clipart-categories, dynamic-by-text, legacy clipart) có nút Replace ở đâu — icon la-exchange-alt trên layer row (khi đó layer row có hơn 5 icon), hay chỉ trong panel la-pen / menu More (…)? PO xác nhận thiết kế. KB-002 (object-level, oracle BASELINE nhiều check) giữ nguyên, không vào conflict_group. Cần: PO trả lời nguyên văn có ngày.", "side_a": "Rule QA FACT-073 nêu trong CBS-127 (QA chốt 2026-09-11): chỉ image-family có Replace; câu rule ghi vector-family không có Replace 'ở row (la-exchange-alt) lẫn trong panel la-pen', ngụ ý image-family có Replace ở row.", "side_b": "Base KB-002 (bootstrap 2026-09-10): layer row của 34/35 type có đúng 5 icon la-eye · la-unlock · la-pen · la-copy · la-trash-alt, không có la-exchange-alt; KB-908 ghi menu More (…) có mục 'Replace image layer'."}
```

## OQ-artwork-493 — CONFLICT

```json
{"oq_id": "OQ-artwork-493", "type": "CONFLICT", "feature_id": "editor-layer-workspace", "kb_ids": [], "summary": "[CBS-127] CLAIM-07 vế b (chưa nạp KB, chờ quyết định): popup 'Select a layer type' của Artwork 2.0 hiện có bao nhiêu type và gồm những gì — danh sách 28 tên của rule QA hay 29 item / 35 data-type của KB-001, và có thêm Rectangle/Ellipse/Line sau TIB-4726 không? Dev xác nhận danh sách hiện hành. KB-001 (oracle BASELINE của CHK-001, CHK-009) giữ nguyên, không vào conflict_group. Liên quan OQ-artwork-491. Cần: Dev trả lời nguyên văn có ngày.", "side_a": "Rule QA FACT-098 nêu trong CBS-127 (QA xác nhận 2026-09-17): danh sách đủ 28 type (Single-line Text, Paragraph, Curve Text, Warp Text, Spiral Text, Static Image, Clipart Category, Photo Upload, Text to Image (AI), Dynamic Clipart by Text, Static Vector, Vector Category, Vector Upload, Street/Route/Star Maps, Moon Phase, Scrabble, Word Search/Cloud, Song Search, Calendar, QR Code, Clock, Toggle Switch, Additional Option, Addon Charge, JSON List, Font, Color).", "side_b": "Base KB-001 (bootstrap 2026-09-10): 29 item chia 7 nhóm, 6 item có submenu, tổng 35 data-type; ghi chép FACT-158 (2026-10) nêu trong CBS-127 thấy thêm Rectangle/Ellipse/Line."}
```

## OQ-artwork-494 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-494", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "kb_ids": ["KB-1017"], "summary": "[CBS-143] KB-1017: Artwork editor chặn Save / Save & Close khi có layer static-photo không ảnh hoặc photo / clipart-category / group-clipart-categories No personalization không ảnh, toast nêu template + layer — PO/Dev xác nhận đây là hành vi mong muốn và cho biết đã lên production chưa. Thêm: layer photo No personalization không có ảnh mặc định nhưng có retrieval value (KB-937, KB-938) có bị chặn không? Nguồn hiện tại là change note của Dev (TIB-5446, 2026-11-06)."}
```

## OQ-artwork-495 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-495", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "kb_ids": ["KB-1018"], "summary": "[CBS-143] KB-1018: ảnh vừa chọn nhưng chưa upload vẫn tính là có ảnh khi Save — trạng thái này xảy ra ở đường thao tác nào trên portal (hộp chọn ảnh upload xong mới cho Select)? Dev/PO xác nhận."}
```

## OQ-artwork-496 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-496", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "kb_ids": ["KB-1019"], "summary": "[CBS-143] KB-1019: REST lưu artwork (tạo mới / cập nhật) trả 422 khi có layer ảnh không có ảnh — route tạo mới là gì, body lỗi 422 có shape nào (tên template, tên layer ở field nào)? Chưa quan sát; cần lượt test được phép gọi route ghi."}
```

## OQ-artwork-497 — CONFLICT

```json
{"oq_id": "OQ-artwork-497", "type": "CONFLICT", "feature_id": "artwork-save-persist", "kb_ids": ["KB-1020"], "summary": "[CBS-143] KB-1020: kiểm tra 'layer ảnh phải có ảnh' bỏ qua layer linked theo trường nào, và 'replica' là loại layer nào? Item không khẳng định trường hợp layer linked đã convert sang Static Image. Không có conflict_group (căng nằm trong claim, không với item base).", "side_a": "Change note Dev TIB-5446 (2026-11-06, mục API): bỏ qua layer replica, linked, global option, layer ẩn và form-only vì chúng lấy ảnh nơi khác hoặc không render.", "side_b": "Lượt test portal staging 2026-11-09: một layer linked sau khi convert sang Static Image (customization_type no_customization, vẫn giữ trường linked) bị chặn như layer thường; layer replica chưa kiểm vì chưa có định nghĩa."}
```

## OQ-artwork-498 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-498", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "kb_ids": ["KB-1021"], "summary": "[CBS-143] KB-1021: artwork đã hỏng sẵn (layer ảnh không url) không Save được tới khi thêm ảnh hoặc xoá layer, không backfill — PO xác nhận chấp nhận hành vi này (seller không lưu được thay đổi khác trên artwork cũ) và có kế hoạch backfill riêng không? Chưa có lượt test."}
```

## OQ-artwork-499 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-499", "type": "NEEDS_CONFIRMATION", "feature_id": "editor-layer-workspace", "kb_ids": ["KB-1022"], "summary": "[CBS-143] KB-1022: change note Dev nói convert static-photo chưa có ảnh bị chặn ở cả nút 'Convert to Photo Upload' trên layer và popup 'Convert to another layer'; lượt test chỉ thấy popup. Nút riêng hiện ở đâu / với layer nào (vd layer cần convert type)?"}
```

## OQ-artwork-501 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-501", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-image", "kb_ids": ["KB-1024"], "summary": "[CBS-143] KB-1024: layer photo personalization thường không có ảnh mặc định vẫn lưu được trên portal / REST (Dev ghi là giới hạn đã biết, MCP vẫn chặn) — PO có muốn giữ hành vi này không?"}
```

## OQ-artwork-502 — CONFLICT

```json
{"oq_id": "OQ-artwork-502", "type": "CONFLICT", "feature_id": "editor-layer-workspace", "kb_ids": [], "summary": "[CBS-143] CLAIM-09 (chưa nạp KB, chờ PO quyết AC3 TIB-5446): convert Artwork 1.0 → 2.0 với text layer có background_image — layer tạo ra phải là static-photo có url hay clipart-category có url, và AC3 có tính là đạt với converter hiện tại không? Canon chưa có feature cho convert 1.0 → 2.0. Cần: PO trả lời nguyên văn có ngày.", "side_a": "Description TIB-5446 (Dev, 2026-09-15): Root cause #2 nói convert là bug đã xác nhận — layer static-photo tạo từ background của text layer không được gán url khi text layer có background_image; AC3 yêu cầu ra layer static-photo có url.", "side_b": "Change note Dev TIB-5446 (2026-11-06, Known limitations): convert Artwork 1.0 có background image đã đúng sẵn trên dev (layer tạo ra có url), không sửa; câu hỏi kèm đọc code trên ticket (2026-10-31) nói layer tạo ra là clipart-category, không phải static-photo."}
```

## OQ-artwork-503 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-503", "type": "OPEN_ISSUE", "feature_id": "populate-values", "kb_ids": ["KB-1025", "KB-1026"], "summary": "[CBS-118] KB-1025, KB-1026 (known defect): từ bắt đầu bằng ký tự astral (emoji, chữ toán học) làm {{value.initialofword.X}} và bare {{value.initialofword}} trả nửa surrogate pair, hiển thị glyph vỡ. Emoji trong tên có phải kịch bản thật không, và nếu có thì có mở ticket riêng như dev gợi ý không? 'Giới hạn kế thừa, không phải regression' mới là nhận định của một dev, chưa qua PO. Cần: PO trả lời."}
```

## OQ-artwork-504 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-504", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "kb_ids": ["KB-1026"], "summary": "[CBS-118] KB-1026: lỗi astral ở bare {{value.initialofword}} có từ trước TIB-5331, không phải regression do nhánh TIB-5331, có đúng không? Chưa ai đối chiếu bare token trước và sau TIB-5331. Cần: Dev xác nhận."}
```

## OQ-artwork-505 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-505", "type": "NEEDS_CONFIRMATION", "feature_id": "populate-values", "kb_ids": ["KB-1027"], "summary": "[CBS-118] KB-1027: chữ Latin có dấu và tiếng Việt (É, Đ) không bị ảnh hưởng bởi lỗi astral, họ token initialofword lấy đúng chữ đầu — đúng không, với giá trị nhập và kết quả cụ thể nào? Mới là một câu của dev, chưa có test case kiểm độc lập. Cần: Dev xác nhận."}
```

## OQ-artwork-506 — CONFLICT

```json
{"oq_id": "OQ-artwork-506", "type": "CONFLICT", "feature_id": "artwork-list-management", "kb_ids": ["KB-1028"], "summary": "[CBS-107] Gọi thẳng DELETE /api/artworks/{id} cho artwork đang gắn campaign thì response đúng thiết kế là gì (status code, body JSON có nêu lý do không), và trang HTML 'Forbidden' 403 của Laravel mà QA đo được có phải lỗi không? Hai phía chưa ai phân xử; check tầng API CHK-015 chưa có oracle, check tầng portal CHK-013 dùng KB-1028. Cần: Dev trả lời.", "side_a": "spec-hub rule artwork-editor-delete-blocked-when-used (sure green, đọc 2026-11-12, KB-1028): lỗi khi xoá artwork đang dùng nêu lý do; với artwork trong campaign, portal yêu cầu gỡ khỏi mọi campaign trước và có 'View campaigns list'.", "side_b": "QA đo bằng API trên staging 2026-09-07 (rule QA FACT-049, chưa nạp vì xoá dữ liệu là P1): artwork có liên kết campaign nhận 403 với trang HTML 'Forbidden' trần của Laravel, không phải JSON; artwork không liên kết xoá được (204)."}
```

## OQ-artwork-507 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-507", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "kb_ids": ["KB-1029", "KB-1030"], "summary": "[CBS-107] (1) Ngưỡng 60 lần/phút cho lưu thay đổi artwork có sẵn (KB-1029) là setting server: staging và production có cùng giá trị không? (2) Khi vượt rate limit, response là 429 'Too Many Requests' dạng trang HTML (rule QA FACT-050, KB-1030, PROPOSED) có phải thiết kế không, hay phải là JSON? CHK-033 và CHK-034 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-508 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-508", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-list-management", "kb_ids": ["KB-1028", "KB-1031"], "summary": "[CBS-107] Thao tác xoá là P1 (mất dữ liệu). KB-1028 và KB-1031 là rule spec-hub đọc từ code (sure green): artwork đang dùng (campaign, platform product, order design, có duplicate) không xoá được, artwork đã dùng cho order design chỉ archive được; xoá artwork chuyển vào trash. Đây có phải hành vi chủ đích không? CHK-013, CHK-014, CHK-016 đang dùng hai item này làm oracle STRONG. Cần: PO xác nhận."}
```

## OQ-artwork-509 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-509", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1032"], "check_ids": ["CHK-015"], "summary": "[CBS-113] Rule QA FACT-013/FACT-037 (KB-1032, PROPOSED): Duplicate & Link trên một layer đã là linked copy thì bản mới link về layer origin gốc, không tạo chain và không bị chặn (đã thấy với Word Cloud, Warp Text). Đây có phải rule chung của cơ chế link cho mọi type nhóm LINKED không? Nguồn là kết quả QA/AI trước lần dev sửa TIB-5265 ngày 2026-09-08. CHK-015 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-510 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-510", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1033"], "check_ids": ["CHK-016"], "summary": "[CBS-113] Rule QA FACT-015 (KB-1033, PROPOSED): Duplicate & Link trên multi-select có lẫn layer type không support link thì type đó được duplicate thường (bản copy độc lập), không bị bỏ qua. Đúng không? Comment dev TIB-5265 2026-08-18 chỉ nói 'only the allowed types get linked'. CHK-016 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-511 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-511", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1034"], "check_ids": ["CHK-017"], "summary": "[CBS-113] Rule QA FACT-036 (KB-1034, PROPOSED): Duplicate & Link áp dụng ngay, không có bước xác nhận, cho Warp Text và mọi type khác. Còn đúng sau lần dev sửa TIB-5265 ngày 2026-09-08 không? CHK-017 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-512 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-512", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1036"], "check_ids": ["CHK-019"], "summary": "[CBS-113] KB-1036 (OBSERVED_CURRENT, LOW): theo checklist dev sinh từ branch diff (comment TIB-5265, 2026-08-18), Warp Text layer legacy ở Artwork 1.0 không có Duplicate & Link. Đây có phải hành vi chủ đích không? Testlane case Artwork 1.0 (TC-TIB-1212) bị skip. Cần: Dev hoặc PO xác nhận."}
```

## OQ-artwork-513 — CONFLICT

```json
{"oq_id": "OQ-artwork-513", "type": "CONFLICT", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1039"], "check_ids": ["CHK-021"], "conflict_group": "CONF-CBS-113-01", "summary": "[CBS-113] Option 'Share with another layer' ở Artwork 2.0 đã bị bỏ hẳn hay vẫn còn trong Bulk edit khi chọn nhiều layer? Supersede tắt ở teeinblue, không chọn phe; KB-1039 và CHK-021 không làm oracle. Cần: Dev trả lời.", "side_a": "Rule QA FACT-038 (QA, 2026-09-04, QA-3345; KB-1039 PROPOSED): radio 'Share with another layer' trong Personalization Options đã bỏ ở AW2.0 (disabled + display:none ở mọi layer type), thấy nó ẩn không phải regression.", "side_b": "spec-hub teeinblue feature artwork-editor v3, rule artwork-editor-bulk-edit (sure yellow, suy ra; nguồn code và TIB-4024/4026/4025 năm 2025): khi chọn nhiều layer, bulk edit đổi được option 'Share with another layer'."}
```

## OQ-artwork-514 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-514", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1040"], "check_ids": ["CHK-023"], "summary": "[CBS-113] KB-1040 (TIB-5211): convert một linked layer thì gỡ link và thành 'independent layer (No personalization)'. (1) Layer sau convert có mất hết personalization (thành layer tĩnh) không? (2) Origin và các linked copy còn lại có giữ nguyên type và link không (ticket không nói)? (3) Quy tắc có áp cho Warp Text sau TIB-5265 không? CHK-023 chỉ phán phần gỡ link và đổi type của layer vừa convert; các phần còn lại chỉ ghi quan sát. Cần: Dev xác nhận."}
```

## OQ-artwork-515 — CONFLICT

```json
{"oq_id": "OQ-artwork-515", "type": "CONFLICT", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1041"], "check_ids": ["CHK-024"], "conflict_group": "CONF-CBS-113-02", "summary": "[CBS-113] Convert Single-line Text origin có linked copy sang Warp Text trên build hiện tại có còn gỡ link của linked copy không? Expected theo TIB-5211 (KB-1040) là giữ link; hai phía về trạng thái build mâu thuẫn, không chọn phe; KB-1041 và CHK-024 không làm oracle. Cần: QA chạy lại TC-44 và ghi record Testlane có ngày chạy + build; nếu vẫn gỡ link thì Dev trả lời; kèm xác nhận đã lên production chưa.", "side_a": "Testlane TC-TIB-1580 (QA-3345 TC-44, task TIB-046): status passed nhưng actualResult 'source conversion drops the link' (❌), không ngày chạy, không build.", "side_b": "Rule QA FACT-031 (recheck 2026-09-08; KB-1041 PROPOSED): lỗi gỡ link đã được dev sửa; convert origin sang Warp Text thì cả nhóm convert cùng, linked copy giữ link."}
```

## OQ-artwork-516 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-516", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1042"], "check_ids": ["CHK-025"], "summary": "[CBS-113] Rule QA FACT-045 (KB-1042, PROPOSED): Duplicate & Link trên Color layer chạy như Duplicate thường (copy default_value một lần, customization_type 'normal', không field linked, sửa origin không lan sang copy). Đây có phải thiết kế, và đúng trên production không (release-verification TIB-5241 không kiểm Duplicate & Link)? CHK-025 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-517 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-517", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1043"], "check_ids": ["CHK-026"], "summary": "[CBS-116] Rule QA FACT-014/FACT-043 (KB-1043, PROPOSED): ẩn origin (con mắt) thì linked copy vẫn hiện ở editor preview nhưng bị loại khỏi final render (storefront và bản in), cho cả Word Cloud và Warp Text. Đúng thiết kế không, và áp cho mọi type nhóm LINKED không? Cả hai bề mặt chưa được verify đủ: record Testlane TC-TIB-1112 (QA-3343 TC-56) đang passed với kết quả trống, còn nợ phần generated design. CHK-026 chưa có oracle. Cần: Dev xác nhận; QA chạy lại TC-56 phần generated design và ghi record có kết quả, ngày chạy, build."}
```

## OQ-artwork-518 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-518", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1044"], "check_ids": ["CHK-027"], "summary": "[CBS-116] Rule QA FACT-035 (KB-1044, PROPOSED): background của linked layer hành xử y hệt origin (lệch là sai lệch cần báo). Có đúng trên build sau lần dev sửa TIB-5265 ngày 2026-09-08 không (ảnh chụp kiểm trước lần sửa)? Checklist dev TIB-5265 ghi cover crop canh theo box của linked layer và fallback contain khi không đo được ảnh; đó có phải expected không? CHK-027 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-519 — CONFLICT

```json
{"oq_id": "OQ-artwork-519", "type": "CONFLICT", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1045", "KB-1046"], "check_ids": ["CHK-028"], "conflict_group": "CONF-CBS-116-01", "summary": "[CBS-116] Thay background image đã lưu của Warp Text origin thì linked copy có render theo trên build hiện tại không? Hai phía mâu thuẫn, supersede tắt ở teeinblue, không chọn phe; KB-1045, KB-1046 và CHK-028 không làm oracle. Liên quan OQ-artwork-081 (đồng bộ sau khi sửa origin). Cần: QA chạy lại TC-25 và ghi record Testlane có ngày chạy + build + ảnh; nếu canvas copy không đổi thì Dev trả lời đó là bug hay giới hạn đã biết; kèm xác nhận trên production.", "side_a": "Testlane TC-TIB-1229 (QA-3345 TC-25, task TIB-046): status passed nhưng actualResult và expectedResult ghi 'replacing the saved background does not refresh the rendered image' (❌), không ngày chạy, không build, không ảnh.", "side_b": "Rule QA FACT-030 (QA ghi nhận 2026-09-08 bằng ảnh canvas staging; KB-1045 PROPOSED): linked copy không lưu background_image riêng, canvas đổi theo origin ngay khi origin đổi background rồi Save; cùng hướng checklist dev TIB-5265 #48238 2026-08-18 (KB-1046 OBSERVED_CURRENT LOW): 'Set / change / remove a background image on the origin → reflected on the linked copy.'"}
```

## OQ-artwork-520 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-520", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1047"], "check_ids": ["CHK-029"], "summary": "[CBS-116] Rule QA FACT-040 (KB-1047, PROPOSED): linked Warp Text copy chỉ sửa được accordion Extra và các action trong menu '...' (align, geometry, duplicate, delete); design, typography, warp preset, control point, background read-only. Có đúng sau lần dev sửa TIB-5265 ngày 2026-09-08 không? CHK-029 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-521 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-521", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1048"], "check_ids": ["CHK-030"], "summary": "[CBS-116] Rule QA FACT-011 (KB-1048, PROPOSED; chính QA đính chính câu trả lời đầu 'word cloud không có align' cùng ngày 2026-08-26): Word Cloud có Align, Align nằm trong nhóm sửa được của linked copy và chỉ dịch copy; hợp lệ trên origin, linked copy và multi-selection. Đúng thiết kế không? CHK-030 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-522 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-522", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1049"], "check_ids": ["CHK-031"], "summary": "[CBS-116] Rule QA FACT-044 (KB-1049, PROPOSED): Align hợp lệ trên linked Warp Text copy và chỉ dịch box của copy, không đổi origin (record Testlane TC-TIB-1238 ghi giả định giống Word Cloud). Có đúng sau lần dev sửa TIB-5265 ngày 2026-09-08 không? CHK-031 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-523 — CONFLICT

```json
{"oq_id": "OQ-artwork-523", "type": "CONFLICT", "feature_id": "layer-duplicate-link-copy", "kb_ids": ["KB-1050", "KB-1051"], "check_ids": ["CHK-032"], "conflict_group": "CONF-CBS-116-02", "summary": "[CBS-116] Sau khi xoá origin của linked Warp Text, linked copy hiển thị gì ở editor, storefront render và design file? Hai rule QA mâu thuẫn, supersede tắt ở teeinblue, không chọn phe; KB-1050, KB-1051 và CHK-032 không làm oracle. Checklist dev sinh từ branch diff (TIB-5265 2026-08-18: 'degrades gracefully (no crash, no blank canvas)'; TIB-5242 2026-08-24: 'no crash, sensible fallback') không nói copy hiển thị gì. Cần: Dev trả lời.", "side_a": "Rule QA FACT-033 (QA ghi nhận 2026-08-26, TIB-5265; KB-1050 PROPOSED; cũng là expectedResult của Testlane TC-TIB-1239): xoá origin thì linked copy render rỗng (không ẩn layer, không tự gỡ link, không placeholder).", "side_b": "Kết quả QA recheck 2026-09-07 (QA-3345 TC-35, cặp clone; KB-1051 PROPOSED; actualResult của TC-TIB-1239): linked copy Warp Text vẫn hiện nội dung origin đã xoá, giống hệt Single-line Text, QA ghi là đúng hành vi."}
```

## OQ-artwork-527 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-527", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1056", "KB-1057"], "check_ids": ["CHK-011"], "summary": "[CBS-124] Rule QA FACT-064 (KB-1057, PROPOSED): flag flip lưu bằng flip_horizontal_enabled / flip_vertical_enabled chỉ trên layer ảnh (photo/clipart); text và curve-text không bao giờ có hai field này. Change note Dev TIB-5435 (2026-09-14, KB-1056 OBSERVED_CURRENT) chỉ nói text/curve text được mirror vị trí và đảo góc, nội dung không lật gương; không nêu tên field. Hai điều này có đúng và là hành vi mong muốn không? CHK-011 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-528 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-528", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1058"], "check_ids": ["CHK-010"], "summary": "[CBS-124] Rule QA FACT-065 (KB-1058, PROPOSED): mọi thay đổi trong popover Transform (Flip, Width/Height/Top/Left/Rotate) chỉ được lưu khi bấm Save & Close, không autosave hay debounce. Đây có phải hành vi thiết kế không? spec-hub rule artwork-editor-unsaved-warning chỉ nói có hỏi xác nhận khi đóng editor còn thay đổi chưa lưu. CHK-010 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-529 — CONFLICT

```json
{"oq_id": "OQ-artwork-529", "type": "CONFLICT", "feature_id": "transform-multi-select", "kb_ids": ["KB-1059"], "check_ids": ["CHK-006"], "conflict_group": "CONF-CBS-124-01", "summary": "[CBS-124] Đổi Apply for Group → Individual khi Flip H đang tick: layer tính lại từ vị trí gốc hay giữ vị trí đã lật? Hai phía mâu thuẫn, supersede tắt ở teeinblue, không chọn phe; KB-1059 và CHK-006 không làm oracle. Change note Dev TIB-5435 chỉ nói Individual lật tại chỗ, không nói trường hợp đổi mode khi đang tick. Nếu chọn side_a thì expected của TC-TIB-3105 cần sửa. Cần: PO/Dev chọn.", "side_a": "Rule QA QA-3362 BR-2 mở rộng 2026-09-24 (quyết định QA, BUG-126 đóng by design; KB-1059 PROPOSED): đổi sang Individual thì layer tính lại từ vị trí gốc (về 100/250, photo vẫn mirror), đổi lại Group cho đúng giá trị lần tick đầu.", "side_b": "Record Testlane TC-TIB-3105 (QA-3362 TC-16, status passed, gắn BUG-126), expectedResult: layer giữ nguyên vị trí đã đảo ở step 1, đổi mode không tự đưa layer về vị trí gốc."}
```

## OQ-artwork-530 — CONFLICT

```json
{"oq_id": "OQ-artwork-530", "type": "CONFLICT", "feature_id": "transform-multi-select", "kb_ids": ["KB-1060"], "check_ids": ["CHK-007"], "conflict_group": "CONF-CBS-124-02", "summary": "[CBS-124] Layer hidden trong vùng chọn có bị dịch khi Group flip không? Hai phía mâu thuẫn, supersede tắt ở teeinblue, không chọn phe; KB-1060 và CHK-007 không làm oracle. Change note Dev TIB-5355 (2026-09-10, box cá nhân) nói layer ẩn hoặc khoá không nằm trong vùng chọn hợp lệ của Transform nhưng không nói về Flip. Cần: Dev trả lời.", "side_a": "RQ1 cũ trong phân tích QA-3362 (QA thuật lại câu trả lời Dev, không có nguyên văn Dev): layer hidden vẫn bị dịch khi Group flip.", "side_b": "Rule QA FACT-068 (QA chốt 2026-09-16, TC-17 / TC-TIB-3106; KB-1060 PROPOSED): layer hidden được đối xử như locked, không vào bounding box và giữ nguyên vị trí/góc."}
```

## OQ-artwork-531 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-531", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1061", "KB-1062"], "check_ids": ["CHK-004", "CHK-005"], "summary": "[CBS-124] KB-1061 (OBSERVED_CURRENT, change note Dev TIB-5435 2026-09-14): Group flip lật cả vùng chọn như một khối (mirror qua tâm khung vùng chọn, góc đảo dấu, ảnh lật), Individual lật tại chỗ, bỏ tick về vị trí/góc ban đầu — có phải hành vi mong muốn đã chốt không? KB-1062 (PROPOSED, rule QA FACT-069): tick cả Flip H và Flip V ở Group thì rotate giữ nguyên (30° vẫn là 30°, không thành −30° hay 30°+180°) — có đúng không? CHK-004 chỉ có oracle BASELINE; CHK-005 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-532 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-532", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1063"], "check_ids": [], "summary": "[CBS-124] Rule QA FACT-070 (KB-1063, PROPOSED): vị trí đo thật sau Group flip lệch khoảng 20px mỗi layer, theo hướng ngược nhau, so với công thức newLeft = 2·cx − left − width; cơ chế chưa rõ, chưa hỏi Dev. Nguyên nhân độ lệch là gì và vị trí nào mới đúng? Tới khi có câu trả lời, check Group flip chỉ kiểm invariant (thứ tự đảo, flag, bỏ tick về giá trị ban đầu). Cần: Dev trả lời."}
```

## OQ-artwork-533 — OPEN_ISSUE

```json
{"oq_id": "OQ-artwork-533", "type": "OPEN_ISSUE", "feature_id": "transform-multi-select", "kb_ids": ["KB-1064"], "check_ids": ["CHK-009"], "summary": "[CBS-124] KB-1064 (CONFIRMED_EXPECTED theo spec TIB-5440): Reverse reposition direction bật thì ảnh buyer kéo đi ngược chiều theo trục đã lật. Record Testlane TC-TIB-3320 và TC-TIB-3321 (task TIB-117) có status passed nhưng actualResult ghi Fail: kéo ngang (Flip H) và kéo dọc (Flip V) không bị đảo chiều, tham chiếu BUG-160/BUG-161; không ngày chạy, không build. Lỗi này đã sửa chưa, trên build nào? Change note Dev TIB-5440 (2026-09-16) còn nêu artwork v1 không có checkbox và layer No personalization vẫn hiện checkbox nhưng không có tác dụng — chưa nạp. Cần: QA chạy lại CHK-009 và ghi record Testlane có ngày chạy + build; Dev cho biết trạng thái BUG-160/161."}
```

## OQ-artwork-534 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-534", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1065"], "check_ids": [], "summary": "[CBS-124] Rule QA FACT-072 (KB-1065, PROPOSED): khi chỉ chọn một layer (nhất là text), ô Top/Left trong popover Transform hiện và ghi giá trị khác field top/left thật (đặt 100 thì GraphQL đọc 153.89). Đây là hành vi mong muốn hay lỗi? Cần: Dev trả lời."}
```

## OQ-artwork-535 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-535", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-text", "kb_ids": ["KB-1066", "KB-1067"], "check_ids": ["CHK-011"], "owner": "Dev", "summary": "[CBS-126] Rule QA FACT-042 (KB-1066, PROPOSED): payload GET api/merchant/games/warp_text/<base64>.json có points là mảng phẳng 20 số (10 điểm, x rồi y), toạ độ pixel tuyệt đối trong [0,width]×[0,height] với width = height = 1000, không phải 10 object {x,y} chuẩn hoá 0-1; resize layer không đổi points/width/height. Nguồn là lượt AI đọc payload 2026-09-30/10-01, trước lần giao QA lại TIB-5325. Change note Dev TIB-5325 (KB-1067, 2026-10-09) chỉ nói payload render không đổi và vùng render 1000x1000, không nói dạng points hay ảnh hưởng của resize. Đây có phải hợp đồng API không? CHK-011 chưa có oracle. Cần: Dev xác nhận nguyên văn có ngày."}
```

## OQ-artwork-536 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-536", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-text", "kb_ids": ["KB-1068"], "check_ids": ["CHK-012"], "owner": "Dev", "summary": "[CBS-126] Rule QA FACT-137 (KB-1068, PROPOSED, đo 2026-09-30 trước khi TIB-5325 re-open): popup Warp cũ có Mirror X (.la-arrows-alt-h) và Mirror Y (.la-arrows-alt-v) là 2 nút icon cạnh nút Free dưới canvas preview, không có chữ 'mirror' trong DOM. Sau TIB-5325, dialog 'Advanced editor' còn hai nút này không, hay đã thay bằng lựa chọn Vertical/Horizontal của Warp mode (change note Dev ghi chế độ dùng chung hai chiều giữa popover và dialog)? Record Testlane TC-TIB-4195 (TC-14) có expected 'Mirror X/Y không có khi kéo trên canvas, chỉ có trong popup' dựa trên giới hạn mà change note Dev nay ghi đã làm xong, có thể cần sửa. CHK-012 chưa có oracle. Cần: Dev xác nhận nguyên văn có ngày."}
```

## OQ-artwork-537 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-537", "type": "NEEDS_CONFIRMATION", "feature_id": "layer-config-text", "kb_ids": ["KB-1069"], "check_ids": ["CHK-013"], "owner": "Dev", "summary": "[CBS-126] Rule QA FACT-138 (KB-1069, PROPOSED, AI đo staging 2026-09-30 và TC-34 2026-10-01): bật Mirror X trong popup Warp không tự lật điểm sẵn có; kéo một điểm thì điểm đối xứng nhận x' = 2×centerX − x, và theo cả hai lượt đo y của điểm đối xứng bằng y của điểm vừa kéo (point[4] y 400→458.70 theo point[0]; lượt 2 y = 436.5782). Câu chữ 'y giữ nguyên' trong rule và 'không đổi theo điểm vừa kéo' trong expected record Testlane TC-TIB-4215 lệch với số đo; không có quan sát nào cho y đứng yên nên không mở CONFLICT. Dev: khi mirror theo trục dọc (Mirror X cũ hoặc Warp mode Vertical), điểm đối xứng có nhận x' = 2×centerX − x và y bằng đúng y điểm vừa kéo không, và bật mirror có tự lật điểm đã có không? Nếu đúng, expected của TC-TIB-4215 cần sửa câu chữ. CHK-013 chưa có oracle. Cần: Dev xác nhận nguyên văn có ngày."}
```

## OQ-artwork-538 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-538", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1070", "KB-1071"], "check_ids": ["CHK-012", "CHK-013"], "owner": "Dev", "summary": "[CBS-129] Rule QA FACT-063 (KB-1071, PROPOSED): lock/hide một layer giữa multi-selection thì layer đó vẫn được tính là đang chọn (\"N selected\" không đổi), box nhóm chỉ bao các layer không khoá/ẩn và co lại ngay khi lock/hide (nở lại khi unlock/unhide), stepper +/- ở ô Top/Left/Width/Height chỉ dịch layer không khoá/ẩn. Change note Dev TIB-5355 (2026-09-10, KB-1070 OBSERVED_CURRENT) chỉ nói layer ẩn/khoá không được vẽ khung riêng vì không nằm trong vùng chọn hợp lệ của Transform. Các điều này có đúng và là hành vi mong muốn không? CHK-013 chưa có oracle, CHK-012 chỉ BASELINE. Cần: Dev xác nhận."}
```

## OQ-artwork-539 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-539", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1072"], "check_ids": ["CHK-014"], "owner": "Dev", "summary": "[CBS-129] Rule QA FACT-063 (KB-1072, PROPOSED): ở Apply for: Individual, khi selection 2–3 layer chỉ còn đúng 1 layer không khoá/ẩn thì canvas xử lý như chọn 1 layer — không box cá nhân, box nhóm co về layer đó, popover Transform mất radio Apply for và hiện số đo của layer đó. Ghi chú \"dev chốt by design 2026-09-16\" là QA thuật lại, chưa có nguyên văn Dev; change note TIB-5355 chỉ nói khung riêng hiện khi chọn từ 2 layer. Dev có xác nhận đây là chủ ý không? CHK-014 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-540 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-540", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1073"], "check_ids": ["CHK-015"], "owner": "Dev", "summary": "[CBS-129] Rule QA FACT-063 (KB-1073, PROPOSED): double-click sửa text khi đang chọn nhiều layer thì selection thu về đúng layer đó; ô cỡ chữ trên quick toolbar (.qte-font-size) chỉ hiện khi mọi layer đang chọn là text, giá trị nhập áp cho tất cả, selection lẫn photo thì ô ẩn hẳn. spec-hub artwork-editor-bulk-edit (yellow) không nói hai điều này. Có đúng và là hành vi mong muốn không? CHK-015 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-541 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-541", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1074"], "check_ids": ["CHK-016"], "owner": "Dev", "summary": "[CBS-129] Rule QA FACT-063 (KB-1074, PROPOSED): box cá nhân (.artwork-layer-frame) viền solid 1px và box nhóm (.drr::before) viền dashed 2px, cùng màu #00c4cc, cả hai không nhận chuột, không box-shadow. Change note TIB-5355 chỉ nói khung riêng chỉ để nhìn. Màu và kiểu nét này có phải thiết kế chủ đích không? CHK-016 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-542 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-542", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1075"], "check_ids": ["CHK-017"], "owner": "Dev/PO", "summary": "[CBS-129] Delete khi chọn nhiều layer (KB-1075, OBSERVED_CURRENT/LOW, record Testlane TC-TIB-3086 chỉ tick [AI], không ngày chạy, không build): Delete xoá cả 3 layer đang chọn, Ctrl+Z trả lại 3 layer nhưng selection rỗng; expected của test case ghi Undo khôi phục cả box Individual. Expected đúng là gì (Undo có khôi phục selection và box không)? Có cách xoá riêng 1 layer trong khi vẫn giữ các layer khác đang chọn không (QA chốt là không, chưa có nguồn)? Đây là hành vi xoá dữ liệu (P1): cần test case Testlane PASS có ngày chạy, build và căn cứ expected, hoặc Dev/PO xác nhận nguyên văn có ngày. CHK-017 (P1) chưa có oracle. Cần: Dev/PO xác nhận."}
```

## OQ-artwork-543 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-543", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1076"], "check_ids": ["CHK-018"], "owner": "Dev", "summary": "[CBS-129] Rule QA FACT-063 (KB-1076, PROPOSED, QA chốt 2026-09-16): Align dùng target riêng \"Align to:\", không theo radio Apply for; editor không có phím tắt Ctrl+D để duplicate và không có phím mũi tên để nudge layer, di chuyển bằng số là stepper +/- ở ô Transform. spec-hub artwork-editor-shortcuts (yellow) liệt kê Ctrl+J duplicate, không có Ctrl+D hay phím mũi tên, nhưng không nói thẳng là không có. Có đúng không? CHK-018 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-544 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-544", "type": "NEEDS_CONFIRMATION", "feature_id": "transform-multi-select", "kb_ids": ["KB-1077"], "check_ids": ["CHK-019"], "owner": "Dev", "summary": "[CBS-129] Rule QA FACT-063 (KB-1077, PROPOSED): chọn layer con trong Group qua layer panel (Cmd/Ctrl/Shift-click) không nâng lên chọn Group cha, mỗi con có box riêng; chọn chính Group container kéo theo mọi layer con; box nhóm bao union mọi layer, luôn axis-aligned. Ghi chú \"dev chốt RQ5 2026-09-16\" là QA thuật lại, chưa có nguyên văn Dev. Có đúng và là chủ ý không? CHK-019 chưa có oracle. Cần: Dev xác nhận."}
```

## OQ-artwork-545 — CONFLICT

```json
{"oq_id": "OQ-artwork-545", "type": "CONFLICT", "feature_id": "transform-multi-select", "kb_ids": ["KB-1078"], "check_ids": ["CHK-020"], "conflict_group": "CONF-CBS-129-01", "owner": "Dev", "summary": "[CBS-129] Group layer (container) trong selection Apply for: Individual có box cá nhân không? Hai phía mâu thuẫn, supersede tắt ở teeinblue, không chọn phe; KB-1078 và CHK-020 không làm oracle. Cả hai phía đều từ QA (side_a là QA thuật lại câu Dev, không có nguyên văn). Nếu chọn side_a thì expected của TC-TIB-3059 cần sửa. Cần: Dev chọn.", "side_a": "RQ13 trong phân tích QA-3361 (QA thuật lại câu Dev trả lời 2026-09-16, không có nguyên văn Dev): Group layer có individual box bằng union bounding box của các layer con.", "side_b": "Rule QA FACT-063 + expected Testlane TC-TIB-3059 (QA-3361 TC-6, đo trên staging 2026-09-16/17; KB-1078 PROPOSED): Group container không bao giờ có .artwork-layer-frame, chỉ từng layer con có box riêng."}
```

## OQ-artwork-547 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-547", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-template-management", "kb_ids": ["KB-1080"], "check_ids": ["CHK-016"], "owner": "Dev", "summary": "[CBS-111] Rule QA FACT-010 (KB-1080, PROPOSED; rule QA không có ngày cụ thể, có trước 2026-09-11, ngày ghi nhận lấy theo ngày gửi Proposal 2026-11-10): ở template không phải global của artwork có Global Template, layer đồng bộ chỉ khoá font family, còn màu chữ, font size min/max, drop shadow, background, Transform, Align sửa được, và các panel settings không mở được. Có đúng và còn hiện hành không? 'Panel settings không mở được' là những panel nào? spec-hub không có rule về việc này. CHK-016 chưa có oracle. Cần: Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày chạy, build, căn cứ expected."}
```

## OQ-artwork-548 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-548", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-template-management", "kb_ids": ["KB-1081"], "check_ids": ["CHK-017"], "owner": "Dev", "summary": "[CBS-111] Rule QA FACT-016 (KB-1081, PROPOSED; ngày ghi nhận lấy theo ngày gửi Proposal 2026-11-10): Global Template chỉ global trong một artwork (đồng bộ giữa các template của artwork đó), không dùng chung giữa các artwork. Có đúng không? Mô tả dữ liệu 'Templates' của feature artwork-editor trên spec-hub (không phải rule) chỉ nói layer của template global lặp lại ở mọi template khác và giữ đồng bộ, không nói giữa các artwork. Phủ một phần OQ-artwork-024 / OQ-artwork-360 (CHK-009, kết quả sau Convert to Global Template), các OQ đó giữ mở. CHK-017 chưa có oracle. Cần: Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày chạy, build, căn cứ expected."}
```

## OQ-artwork-549 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-549", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-cross-store-clone", "kb_ids": ["KB-1085"], "check_ids": ["CHK-005"], "owner": "Dev", "summary": "[CBS-157] Sau admin import artwork sang account khác, design preview của từng template của artwork bên đích phải render xong và giống template tương ứng của nguồn (ảnh clipart và static photo lấy từ clipart hiện đủ, không vùng trống) có phải hành vi đúng không? KB-1085 chỉ là quan sát một lần (test case TC-TIB-8113, staging 2026-11-04, không ghi build); expected do QA chốt, comment Dev TIB-5619 không nói về design preview. CHK-005 oracle BASELINE. Cần: Dev xác nhận, hoặc test case Testlane PASS có build và căn cứ expected."}
```

## OQ-artwork-550 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-550", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-cross-store-clone", "kb_ids": ["KB-1086"], "check_ids": [], "owner": "Dev", "summary": "[CBS-157] Khác biệt môi trường (ALTERNATIVE_SETUP, ghi nhận QA 2026-11-03, KB-1086 INFERRED): trên staging QA không duplicate được campaign sang store của account khác từ portal (clone campaign Product Base không chọn store; clone platform product chỉ chọn instance cùng account), nên test bằng import TIB Library hoặc admin import. Đúng không, có đường nào khác trên staging, và trên production duplicate campaign sang store khác chạy thế nào? Cần: Dev xác nhận."}
```

## OQ-artwork-551 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-551", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-cross-store-clone", "kb_ids": ["KB-1082"], "check_ids": ["CHK-001", "CHK-002"], "owner": "Dev", "summary": "[CBS-157] Remap ảnh gốc khi copy artwork sang account khác (KB-1082) có áp cho layer Group of clipart categories, Vector Category và artwork 1.0 không? Comment Dev TIB-5619 (2026-10-29) nói áp cho cả artwork 1.0 và 2.0, nhưng test case chỉ phủ layer Clipart Category tự giữ category trên artwork 2.0 (các case 1.0, Group of clipart categories, Vector Category bị skip). Cần: test case Testlane PASS cho các loại layer này, hoặc Dev xác nhận phạm vi."}
```

## OQ-artwork-552 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-552", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-cross-store-clone", "kb_ids": [], "check_ids": [], "owner": "Dev", "summary": "[CBS-157] Layer lấy category từ Global Option (layer không tự giữ category, clipart của layer null ở nguồn) khi artwork được import qua TIB Library sang account khác: ảnh gốc có được remap sang category của bên đích không? QA ghi nhận ngoài claim trên staging 2026-11-04: url vẫn giữ id category nguồn (file trả 403), layer trong suốt trên canvas. Chưa có kết luận Dev/PO, không nạp KB, không có expected. Cần: Dev/PO xác nhận hành vi đúng, hoặc mở bug."}
```

## OQ-artwork-553 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-553", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-cross-store-clone", "kb_ids": [], "check_ids": [], "owner": "Dev", "summary": "[CBS-157] Khi copy ảnh clipart dùng làm Static photo sang bên đích (KB-1083), QA ghi nhận ngoài claim (staging 2026-11-04): chỉ file _large được copy, file _thumbnail ở đường dẫn đích trả 403 nên dòng layer ở layer list hiện icon chung; QA coi là lỗi nhỏ không chặn. Đây là lỗi hay chủ ý? Chưa có kết luận Dev, không nạp KB. Cần: Dev xác nhận."}
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

## OQ-artwork-559 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-559","type":"NEEDS_CONFIRMATION","feature_id":"text-multi-stroke","kb_ids":["KB-1096"],"check_ids":["CHK-030"],"owner":"Dev","summary":"[CBS-149] Sau TIB-5699, layer Text và Paragraph có 2 lớp stroke vẫn render đủ 2 vòng trong PNG và SVG, và sau đổi text + Save + mở lại vẫn hiện 2 lớp, PUT gửi 2 entry stroke_layers — có phải expected không? KB-1096 là quan sát test case TC-TIB-8986 (staging 2026-11-10, không ghi build); CCR chỉ nêu tên căn cứ expected (TIB-5699 comment 56557 U3/Q4, QA plan 56595 bước D7), không trích nguyên văn. CHK-030 oracle BASELINE. Cần: Dev xác nhận kèm trích nguyên văn, hoặc test case PASS có build."}
```

## OQ-artwork-560 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-560","type":"NEEDS_CONFIRMATION","feature_id":"text-multi-stroke","kb_ids":["KB-1097"],"check_ids":["CHK-031"],"owner":"Dev","summary":"[CBS-149] Đổi stroke của layer curve text nhiều lần (tăng, giảm width, đổi màu), Save và render lại sau mỗi lần thì PNG luôn theo stroke mới nhất của editor, không quay về giá trị cũ — có phải expected không, và có áp cho spiral / shape / warp text và SVG không? KB-1097 là quan sát test case TC-TIB-8982 (staging 2026-11-10, không ghi build); câu tương ứng trong QA plan của Dev (56595 bước A2) không được trích trong CCR. CHK-031 oracle BASELINE."}
```

## OQ-artwork-561 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-561","type":"NEEDS_CONFIRMATION","feature_id":"text-multi-stroke","kb_ids":["KB-1094","KB-1095","KB-1096","KB-1097"],"check_ids":[],"owner":"QA","summary":"[CBS-149] Trên production, ảnh render PNG và preview của curve / spiral / shape / warp text sau TIB-5699 có khớp stroke editor khi người xem duyệt không? Production 2026-11-11 chỉ phần kiểm bằng máy pass (dữ liệu lưu không còn stroke_layers, SVG đúng màu/độ dày); phần duyệt ảnh NOT-RUN ở mức task, regression thiếu fixture production. KB-1096, KB-1097 và vế convert của KB-1095 chỉ chạy staging; linked copy (layer-duplicate-link-copy KB-1098) cũng chỉ chạy staging."}
```

## OQ-artwork-562 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-562","type":"NEEDS_CONFIRMATION","feature_id":"text-multi-stroke","kb_ids":["KB-1094"],"check_ids":[],"owner":"Dev","summary":"[CBS-149] Ngoài claim (ghi chú trong CCR, quan sát staging): spiral text trên SVG design với width 5 cho stroke-width=\"3\", trong khi các loại khác stroke-width = width × 0.875 — đây là hành vi đúng hay lệch? Chưa có trả lời của Dev, không nạp KB."}
```

## OQ-artwork-563 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-563","type":"NEEDS_CONFIRMATION","feature_id":"text-multi-stroke","kb_ids":["KB-1094","KB-1095"],"check_ids":[],"owner":"Dev","summary":"[CBS-149] Layer curve / spiral / shape / warp text đã giữ sẵn stroke_layers cũ (tình huống gốc của TIB-5699) có render theo cặp và bị xoá list khi save lại không? Dev ghi \"Not for QA (covered by unit tests)\" và dặn không sửa data bằng tay; QA chưa có fixture để verify. Checklist hiện chỉ kiểm layer mới đặt stroke."}
```

## OQ-artwork-564 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-564","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1098"],"check_ids":[],"owner":"Dev","summary":"[CBS-149] Ngoài claim (quan sát staging ghi trong CCR): dữ liệu lưu của linked copy curve / warp text vẫn giữ cặp stroke_color / stroke_width cũ của chính nó, trong khi render dùng cặp của gốc. Đây là thiết kế hay dữ liệu thừa cần dọn? Có trường hợp nào (gỡ link, convert, copy artwork, đọc qua API/MCP) mà cặp cũ của copy được dùng lại không? Không nạp KB."}
```

## OQ-artwork-567 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-567","type":"NEEDS_CONFIRMATION","feature_id":"text-multi-stroke","kb_ids":["KB-1094"],"check_ids":[],"owner":"Dev","summary":"[CBS-149] Warp text bật stroke mà stroke_width rỗng hoặc 0: preview SDK không vẽ stroke, còn render api vẽ width mặc định 1. Dev tự nêu ở mục Open questions của TIB-5699 comment 56557 (2026-11-05): hành vi có từ trước, bản sửa giữ nguyên, hỏi có tách ticket riêng không. Đây là lệch chấp nhận hay bug cần ticket? Vế 'design khớp preview' của KB-1094 không áp cho trường hợp này; CHK-028 đặt width khác mặc định."}
```

## OQ-artwork-568 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-artwork-568",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "layer-image-hd-copy",
  "summary": "Bản HD (master_large) của layer ảnh: cạnh dài 4096, giữ tỉ lệ, xoay EXIF đúng một lần, file không còn EXIF chỉ là quan sát staging 2026-11-10 (KB-1102, CHK-001/CHK-002 BASELINE). Quy tắc cap 4096 (TIB-5420/TIB-5543) chưa có trong canon (CCR backfill chưa publish). PNG có alpha có giữ transparency không: chưa kiểm vì PNG test không có alpha (CHK-003).",
  "kb_ids": [
    "KB-1102"
  ],
  "needs": "CCR backfill quy tắc HD (TIB-5420/TIB-5543) có nguồn Dev/PO; chạy HD với PNG có alpha."
}
```

## OQ-artwork-569 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-artwork-569",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "layer-image-hd-copy",
  "summary": "Toast/spinner trạng thái khi bản HD đang tạo hoặc tạo lỗi hiển thị thế nào: CCR nêu trong phạm vi feature nhưng không có nguồn hay quan sát (quan sát toast thành công nằm ở _flows/toolbar-transform.md).",
  "kb_ids": [],
  "needs": "Dev/PO hoặc test case cho trường hợp HD lỗi."
}
```

## OQ-artwork-570 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-artwork-570",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "run-image-effects",
  "summary": "Run effects có [Gemini] image filter dùng ref image rất lớn (12000x12000) hoàn tất, layer thay bằng ảnh đã lọc, đứng thẳng (KB-1103, PROPOSED): expected là suy luận QA (giả định A3, ngoài QA plan của Dev). Comment Dev TIB-5615 chỉ liệt kê ApplyLayerImageEffectsJob trên image-effect-queue, không nói job này đi qua applyImageFilter(). Dev xác nhận?",
  "kb_ids": [
    "KB-1103"
  ],
  "needs": "Dev xác nhận ApplyLayerImageEffectsJob dùng applyImageFilter() (ref image cap) và expected của trường hợp này."
}
```

## OQ-artwork-571 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-artwork-571",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "layer-config-maps-astronomy",
  "summary": "[CBS-106, TIB-5609] 'Display in date format' của layer Star Map (KB-1105, OBSERVED_CURRENT/LOW): danh sách 7 preset dạng 24h HH:mm không giây (MM/DD/YYYY, DD/MM/YYYY, DD-MM-YY, YYYY-MM-DD, YYYY/MM/DD, DD.MM.YYYY, MM.DD.YYYY) + Custom, field lưu star_maps_date_format / star_maps_custom_date_format, key custom vắng trong body Save khi chọn preset — có đúng ý PO/Dev không, PO có chấp nhận preset 24h không? Setting chỉ có ở Artwork 2.0 (Artwork 1.0, Global Option Star Maps chưa kiểm)?",
  "kb_ids": [
    "KB-1105"
  ],
  "needs": "PO xác nhận danh sách preset; Dev xác nhận tên field và phạm vi Artwork 2.0 / Global Option, kèm nguyên văn có ngày."
}
```

## OQ-artwork-572 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-artwork-572",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "layer-config-maps-astronomy",
  "summary": "[CBS-106, TIB-5609] Ô giờ Star Map trên storefront (KB-1107, OBSERVED_CURRENT/LOW): ô hiện theo format đã chọn (kể cả Custom 12h AM/PM) còn giá trị lưu trong customization/localStorage vẫn dạng máy yyyy-MM-ddTHH:mm — Dev xác nhận? SDK v1 có giống SDK v2 không (chưa kiểm vì thiếu store SDK v1; record Testlane TC-TIB-8819 ghi passed nhưng actual là blocked)?",
  "kb_ids": [
    "KB-1107"
  ],
  "needs": "Dev xác nhận nguyên văn có ngày; một lượt chạy trên store SDK v1 có ghi build."
}
```

## OQ-artwork-573 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-artwork-573",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "layer-config-maps-astronomy",
  "summary": "[CBS-106, TIB-5609] Khi store tắt UI date picker của Teeinblue (picker native), text layer populate {{time}} từ Star Map vẫn in theo 'Display in date format' của Star Map (KB-1111, quan sát TC-TIB-8812). Câu Scope của TIB-5609 ('applies to Teeinblue's own date picker only', KB-1110) chỉ nói ô hiển thị hay cả populate? Expected của {{time}} khi dùng picker native là gì?",
  "kb_ids": [
    "KB-1111",
    "KB-1110"
  ],
  "needs": "PO/Dev trả lời nguyên văn có ngày."
}
```

## OQ-artwork-574 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-artwork-574",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "populate-values",
  "summary": "[CBS-106, TIB-5609] Populate từ Star Map (KB-1109, OBSERVED_CURRENT/LOW): Star Map chưa set format vẫn cho {{time}} = yyyy-MM-dd HH:mm (mặc định ghi theo TIB-4913, chưa có nguồn trích), Moon Phase {{date}} và Route {{route_start_date}} không đổi, text layer đích Input type Date picker nhận ngày ISO và hiện theo format của chính nó — Dev xác nhận? {{name}}/{{lat}} của Star Map có đổi không (chưa kiểm)?",
  "kb_ids": [
    "KB-1109"
  ],
  "needs": "Dev xác nhận nguyên văn có ngày; lượt chạy có fixture {{name}}/{{lat}}."
}
```

## OQ-artwork-575 — NEEDS_CONFIRMATION

```json
{
  "oq_id": "OQ-artwork-575",
  "type": "NEEDS_CONFIRMATION",
  "feature_id": "layer-config-maps-astronomy",
  "summary": "[CBS-106, TIB-5609] Star Map không vẽ ngày lên design (KB-1112, theo TIB-5609): lượt chạy TC-TIB-8816 chỉ kiểm print area front của design order; print area khác (back) và mockup chưa kiểm.",
  "kb_ids": [
    "KB-1112"
  ],
  "needs": "Lượt chạy design order có Star Map ở print area khác, ghi build."
}
```

## OQ-artwork-576 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-576", "type": "NEEDS_CONFIRMATION", "feature_id": "psd-import", "summary": "[CBS-152, TIB-5709] Import PSD có layer 144 MP (KB-1114, quan sát TC-TIB-8788 build e96975614): toast \"Your artwork has been created\" và artwork lưu được qua PSD Single template và Group-to-template — expected? Bulk upload PSD (chỉ user beta) với layer > 128 MP chưa chạy; production chưa chạy; TIB-5718 (layer PSD portal lên queue) có đổi luồng này không?", "kb_ids": ["KB-1114"], "needs": "Dev xác nhận; QA cần account beta cho Bulk upload PSD và lượt production."}
```

## OQ-artwork-577 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-577", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-list-management", "kb_ids": ["KB-1118"], "check_ids": [], "owner": "Dev", "summary": "[CBS-163] Duplicate artwork 201 trả bản copy, archive 200 với status 1 (artwork vào tab Archived), unarchive 200 với status 0, response không relation, không user_id (KB-1118, một lượt staging, build không ghi): Dev xác nhận là expected? Câu trả lời cũng đóng được OQ-artwork-014 / OQ-artwork-349 (kết quả Mark as archive, CHK-005)."}
```

## OQ-artwork-578 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-578", "type": "NEEDS_CONFIRMATION", "feature_id": "artwork-save-persist", "kb_ids": ["KB-1117"], "check_ids": ["CHK-037"], "owner": "Dev", "summary": "[CBS-163] Tạo artwork 201, lưu 200, khôi phục version 200 với data và schema_version, không relation, không user_id, editor hiện design của version đã khôi phục (KB-1117, một lượt staging, build không ghi): Dev xác nhận đây là expected? Production mới có một lượt cho thao tác lưu."}
```

## OQ-artwork-579 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-artwork-579", "type": "NEEDS_CONFIRMATION", "feature_id": "run-image-effects", "kb_ids": ["KB-1120"], "check_ids": [], "owner": "Dev", "summary": "[CBS-163] Run effects tới khi xong: layer nhận ảnh kết quả, response trạng thái lượt chạy có status và layer_image (id, url, thumbnail, width, height), không user_id (KB-1120, một lượt staging, build không ghi): Dev xác nhận là expected? error_message có mặt (null) khi lượt chạy thành công không?"}
```
