# Open Questions — artwork-layer-config

## OQ-artwork-layer-config-001 — CONFLICT

```json
{"oq_id":"OQ-artwork-layer-config-001","type":"CONFLICT","feature_id":"conditional-setting-config","summary":"Evidence linking a toggle-source condition action to its network capture is unreliable, casting doubt on the API-level oracle for that specific observation (KB-066 area).","side_a":"The recorded action ('choose Toggle as condition source, set value On') was linked to a specific network capture file as its evidence.","side_b":"The actual content of that linked network capture file describes a completely different action (browsing 8 source options on a curve-text layer, then Cancel) and contains no PUT request at all — so the linkage was wrong or the two actions shared one capture window.","supersedes":"OQ-artwork-001"}
```

## OQ-artwork-layer-config-002 — CONFLICT

```json
{"oq_id":"OQ-artwork-layer-config-002","type":"CONFLICT","feature_id":"conditional-setting-config","summary":"Two observation passes on the same test artwork (4087) recorded different data state for addon-charge/json-list layers — most likely the fixture changed between passes, not a real product behavior conflict, but not confirmed.","side_a":"First observation pass: layer addon-charge had no option values configured yet; layer json-list had no JSON URL configured yet.","side_b":"Second observation pass (same artwork, later): addon-charge already had 2 options configured; json-list already had a source URL configured.","supersedes":"OQ-artwork-002"}
```

## OQ-artwork-layer-config-003 — CONFLICT

```json
{"oq_id":"OQ-artwork-layer-config-003","type":"CONFLICT","feature_id":"photo-upload-layer-config","summary":"Whether the layer-level 'Custom class' field exists on the Clipart Category (single) sub-type is disputed: the canonical 33/35 boundary says yes, a later deep-dive found no trace of it.","side_a":"Canonical boundary knowledge (KB-011): 'Custom class' is present on 33/35 layer types, with only Static Image and Static Vector as named exceptions — implying Clipart Category (single) has it.","side_b":"A later deep-dive on Clipart Category (single), scrolling the full Bulk Edit dialog (Design/Personalization/Extra) and checking the layer's API response directly, found no 'Custom class' field and no custom_class key anywhere.","supersedes":"OQ-artwork-008"}
```

## OQ-artwork-layer-config-004 — CONFLICT

```json
{"oq_id":"OQ-artwork-layer-config-004","type":"CONFLICT","feature_id":"photo-upload-layer-config","summary":"Text to Image (AI) personalization option count is disputed: canonical KB-019 says 2 choices (no 'No personalization'), a later re-observation (CCR CBS-003) found 3, corroborated by an independent observation on a different object (global-option).","side_a":"Canon KB-019 (observed 2026-09-10): only 2 personalization choices exist for Text to Image (AI) — 'Create a new option' / 'Use an existing global option'. No 'No personalization' option.","side_b":"Re-observation on 2026-09-25 (artwork 4416, layer 'hair'): all three choices are present — 'No personalization', 'Create a new option' (default), 'Use an existing global option'.","side_c":"Corroborating, cross-object: an independent observation 10 days earlier on object global-option (CFL-01, artwork 4167) also saw all three choices; its escalation to the artwork object owner was never actioned before KB-019 was republished unchanged. No build/version/deploy-date is available to tell whether behavior genuinely changed or KB-019 was wrong from the start. KNOWN RISK: canonical checklist item CHK-007 for layer-config-image currently asserts '2 choices' with automation_suitability SUITABLE — any automation relying on it as an oracle should be audited.","supersedes":"OQ-artwork-011"}
```

## OQ-artwork-layer-config-005 — CONFLICT

```json
{"oq_id":"OQ-artwork-layer-config-005","type":"CONFLICT","feature_id":"vector-layer-config","summary":"x-ratelimit-remaining behavior for POST /api/layer-images/svg is inconsistent between two single-sample observations at different status codes; not enough evidence to state a rule.","side_a":"Direct API test: 3 consecutive calls missing the required 'file' field (422 each time) — x-ratelimit-remaining stayed at 1000 (unchanged) across all 3 calls, while x-ratelimit-limit correctly showed 1000 each time.","side_b":"UI-driven upload: 1 successful call (201) — x-ratelimit-remaining showed 999 (limit minus 1) on that request. Possibly the counter only increments on requests that pass validation, but with only 1 sample per side at different status codes, this is not confirmed as a rule.","supersedes":"OQ-artwork-012"}
```

## OQ-artwork-layer-config-006 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-006","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"BLK-API-002 (unknown nghiêm trọng nhất KB gốc): TOÀN BỘ evidence 3 run — PUT chưa BAO GIỜ được gửi với payload vòng vì client luôn chặn trước. validate-default-value vẫn 204 ngay cả 2 lần bị chặn — KHÔNG phải endpoint kiểm vòng. KHÔNG có evidence nào xác nhận hay bác bỏ việc server tự chặn vòng độc lập. Case này CẦN orchestrator duyệt trước khi chạy (direct-API mutation, ngoài SAFE_REVERSIBLE_ONLY mặc định nếu tạo dữ liệu vòng thật trong DB).","supersedes":"OQ-artwork-036"}
```

## OQ-artwork-layer-config-007 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-007","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"KB-041: self-loop chưa từng thử qua API trực tiếp (ngoài phạm vi portal-explorer/api-runtime-trace).","supersedes":"OQ-artwork-037"}
```

## OQ-artwork-layer-config-008 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-008","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"2/2 sample gốc đều ra 'Word Search' chỉ vì trùng hợp cấu trúc test data (layer duy nhất phụ thuộc cả 8 nguồn) — chưa tách biệt coincidence vs quy luật thật (vd theo thứ tự template/layer).","supersedes":"OQ-artwork-038"}
```

## OQ-artwork-layer-config-009 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-009","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"coverage_gaps #1 của KB gốc: 0 evidence storefront cho toàn bộ object Artwork. Đặc biệt quan trọng ở đây vì đây là edge case bảo vệ tính toàn vẹn dữ liệu — nếu server không chặn (CHK-008), hành vi render cần được biết trước khi coi tính năng này an toàn.","supersedes":"OQ-artwork-039"}
```

## OQ-artwork-layer-config-010 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-010","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"CONF-001: network_ref của action nguồn (chọn nguồn Toggle, giá trị On) trong evidence gốc trỏ nhầm vào 1 file mô tả action khác (không chứa PUT nào). Check này VẪN dùng được vì oracle chính là quan sát UI (screenshot), nhưng nếu cần verify thêm ở tầng API cho đúng action này, kết quả API-side hiện KHÔNG đáng tin cho tới khi CONF-001 được làm rõ.","supersedes":"OQ-artwork-040"}
```

## OQ-artwork-layer-config-011 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-011","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Test tối đa đã thử là 8 condition (hết đúng số nguồn khả dụng trong artwork test), KHÔNG phải giới hạn thật của hệ thống — cần nhiều nguồn hơn 8 để xác định ngưỡng thật.","supersedes":"OQ-artwork-041"}
```

## OQ-artwork-layer-config-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-012","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Không có UI cho lồng nhóm AND trong OR trong toàn bộ evidence hiện có — chưa xác nhận đây là giới hạn thiết kế cố ý hay chưa khám phá hết.","supersedes":"OQ-artwork-042"}
```

## OQ-artwork-layer-config-013 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-013","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"KB-033 chỉ observed_count=1 — chỉ quan sát đúng 2 dạng control, KHÔNG nên coi đây là toàn bộ tập toán tử hệ thống hỗ trợ.","supersedes":"OQ-artwork-043"}
```

## OQ-artwork-layer-config-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-014","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Chưa có evidence nào cho việc server có validate 'layer type nào được phép có dependency' độc lập với UI hay không.","supersedes":"OQ-artwork-044"}
```

## OQ-artwork-layer-config-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-015","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"KB-037 (nguồn duy nhất cho pattern này) có knowledge_kind INFERRED, KHÔNG phải OBSERVED_CURRENT hay CONFIRMED_EXPECTED — theo contract chỉ 2 loại đó mới là oracle hợp lệ. Pattern 'element luôn là layer id' được suy ra từ 10 sample (không có UI nào tạo element khác layer id) nhưng CHƯA được xác nhận là quy tắc hệ thống chính thức — không dùng làm assertion cứng cho tới khi có xác nhận.","supersedes":"OQ-artwork-049"}
```

## OQ-artwork-layer-config-016 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-016","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Mọi sample có toggle làm nguồn condition trong 3 run nguồn đều chọn On (true) — KHÔNG nên giả định symmetry với true khi chưa xác nhận; ảnh hưởng trực tiếp tới test data cho negative case.","supersedes":"OQ-artwork-050"}
```

## OQ-artwork-layer-config-017 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-017","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Multi-value chỉ xác nhận THẬT ở nguồn clipart-category (layer paragraph pre-existing, 2 giá trị webp path, KB-036). 6/8 type nguồn dạng array còn lại chỉ test với đúng 1 giá trị/condition — shape khi chọn ≥2 giá trị hoàn toàn chưa xác nhận cho 6 type này.","supersedes":"OQ-artwork-051"}
```

## OQ-artwork-layer-config-018 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-018","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"CONF-002 UNRESOLVED: R2 ghi nhận addon-charge CHƯA có option, json-list CHƯA có URL; R3 (cùng artwork 4087) ghi nhận CẢ HAI đã có dữ liệu. Nhiều khả năng do state đổi giữa 2 run (ai đó cấu hình thêm giữa 2 lần chạy) chứ không phải mâu thuẫn hành vi sản phẩm, nhưng KHÔNG tự kết luận theo contract §8 — PHẢI kiểm tra trạng thái thật của test data trước khi dùng làm precondition cho case khác.","supersedes":"OQ-artwork-052"}
```

## OQ-artwork-layer-config-019 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-019","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","summary":"Quan sát 1 lần (capture Conditional Setting, KB-041): Color có Option Title đầy đủ nhưng KHÔNG xuất hiện làm nguồn condition, khác Font. Chưa xác nhận đây là thiết kế cố ý hay giới hạn kỹ thuật — cần dev/PO xác nhận trước khi coi là expected behavior.","supersedes":"OQ-artwork-053"}
```

## OQ-artwork-layer-config-020 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-020","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"bundle-registry (INFERRED) gợi ý 2 field cùng mục đích nhưng key khác nhau (text_to_image_provider/multi_image_provider) — chưa cross-check qua PUT body thật của chính 2 type này.","supersedes":"OQ-artwork-054"}
```

## OQ-artwork-layer-config-021 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-021","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"'Select a group of clipart categories' có hỗ trợ multi-category thật hay chỉ 1 category có nested children (Parent Category field)? Ảnh hưởng trực tiếp thiết kế test data & assertion cho group type — nếu chỉ 1-category-nested thì tên field 'group' gây hiểu nhầm.","supersedes":"OQ-artwork-055"}
```

## OQ-artwork-layer-config-022 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-022","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"3-way conflict CONF-CTX20260921-03-02: url drive canvas portal (nhánh a, CHK-024) / default_value drive form widget storefront (nhánh b, xem FEAT-19 CHK-018) / KHÔNG bên nào drive compositing cuối cùng (nhánh c, CRITICAL KB-030, xem FEAT-19 CHK-017). Ở PHẠM VI PORTAL: layer.default_value có ý nghĩa/tác dụng nào trên canvas editor hay hoàn toàn vô dụng ở đây (chỉ có tác dụng phía storefront)? Cần PO/Dev xác nhận trước khi viết assertion chính thức. KHÔNG gộp kết luận với 2 nhánh còn lại — xem full narrative ở FEAT-19 (owner chính của conflict).","supersedes":"OQ-artwork-056"}
```

## OQ-artwork-layer-config-023 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-023","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Combobox hiện 'List is empty.' dù category có 2 item xác nhận tồn tại server-side VÀ đã render đúng ở picker default-value của layer single-type CÙNG PHIÊN. correlation_note: PLAUSIBLE (KHÔNG CONFIRMED) cùng root cause với CONF-API-CTX20260921-03-01 (REST[]/GraphQL10-rows) — đây là 1 UI surface RIÊNG BIỆT, KHÔNG gộp thành 1 statement cho tới khi db-explorer/api-explorer xác nhận. Cần điều tra: request nào backing combobox này, filter gì khác so với picker default-value single-type.","supersedes":"OQ-artwork-057"}
```

## OQ-artwork-layer-config-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-024","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"GET REST trả [] (0 rows) trong khi GraphQL trả 10 rows cùng user/session cùng khoảng thời gian — root cause CHƯA chẩn đoán (filter khác nhau hay cache/data issue riêng staging). Cần db-explorer/api-explorer follow-up trước khi coi là defect xác nhận. Correlation PLAUSIBLE (không CONFIRMED) với KB-013 (CHK-026, portal) và KB-021 (FEAT-19, storefront) — 3 bề mặt riêng biệt, KHÔNG gộp thành 1 statement.","supersedes":"OQ-artwork-058"}
```

## OQ-artwork-layer-config-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-025","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"canonical v2 (published, MEDIUM confidence) khẳng định field 'Custom class:' là baseline PERSONALIZATION SETTINGS cho clipart-category (single). Evidence v3 (, LOW confidence, đã scroll hết Bulk Edit + kiểm tra API response cho cả layer 'cat1' single lẫn 'body' group) KHÔNG tìm thấy field này ở bất kỳ đâu. KHÔNG kết luận field đã bị xoá (regression thật) hay CHƯA từng tồn tại đúng như baseline claim (v2 sai) — cần PO/Dev xác nhận hoặc phát hiện panel single-layer settings riêng (khác Bulk Edit) trước khi kết luận. Xem thêm CHK-002 (v2 cũ, giữ nguyên, KHÔNG tự sửa).","supersedes":"OQ-artwork-059"}
```

## OQ-artwork-layer-config-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-026","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Field API 'show_clipart_name' chỉ quan sát giá trị null, CHƯA test bật/tắt toggle tương ứng — chỉ trùng tên, chưa xác nhận đây có đúng backing field cho UI toggle 'Show option name on hover' hay không. Nếu sai, có thể có 1 field UI khác chưa được map.","supersedes":"OQ-artwork-060"}
```

## OQ-artwork-layer-config-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-027","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"CHK-032 chỉ quan sát 1 sample (layer ĐÃ cấu hình làm destination) — chưa xác nhận thứ tự accordion 'Populate Values đầu tiên' có cố định cho MỌI layer photo (kể cả chưa cấu hình gì) hay chỉ xuất hiện khi Populate Values đã được cấu hình/bật trước đó. Ảnh hưởng cách viết test case assert thứ tự UI accordion — nếu chỉ đúng khi đã bật Populate Values, test case cần setup đúng precondition.","supersedes":"OQ-artwork-061"}
```

## OQ-artwork-layer-config-028 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-028","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Chỉ quan sát trạng thái mặc định OFF của toggle 'Use Template Default Size' — chưa test tác dụng khi bật ON (ảnh hưởng size ảnh generate? disable field khác?). Không thể viết assertion chính thức tới khi có evidence.","supersedes":"OQ-artwork-062"}
```

## OQ-artwork-layer-config-029 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-029","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Rule 'prompt required' (CHK-037, CHK-046) chỉ xác nhận với provider Gemini cho cả Multiple Uploads lẫn Text to Image — OpenAI/Flux/ImagenHub có cùng rule không? Rủi ro viết test case negative (prompt trống) chỉ đúng cho 1 provider rồi tổng quát sai cho provider khác.","supersedes":"OQ-artwork-063"}
```

## OQ-artwork-layer-config-030 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-030","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"CHK-040 chỉ test Maximum photos=3 (thấy token indexed {{input.1..3}}) — chưa test Maximum photos=1, không rõ token có đổi thành dạng trần '{{input}}' hay vẫn giữ '{{input.1}}'. Ảnh hưởng thiết kế test case populate content khi Multiple Uploads chỉ cho phép 1 ảnh.","supersedes":"OQ-artwork-064"}
```

## OQ-artwork-layer-config-031 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-031","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"1 lần thử ở UI cấu hình portal (chọn Flux) KHÔNG thấy cảnh báo unsupported-provider — nhưng cảnh báo có thể chỉ hiện lúc generate thật (chưa thử). Nếu cảnh báo chỉ hiện lúc generate, test case cấu hình UI hiện tại sẽ không phát hiện được vấn đề thật. Liên quan FEAT-02-genai-personalization-runtime (object sdk) cho phần generate thật.","supersedes":"OQ-artwork-065"}
```

## OQ-artwork-layer-config-032 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-032","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"CHK-044 chỉ quan sát trạng thái RỖNG (message hướng dẫn) khi CHƯA có layer Text/Additional Option khác — chưa quan sát behavior thật của picker khi CÓ option để chọn. Ảnh hưởng test case cho luồng variable binding trong prompt.","supersedes":"OQ-artwork-066"}
```

## OQ-artwork-layer-config-033 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-033","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Trong 1 lần kiểm tra, Source option dropdown của Populate Content KHÔNG offer layer Text to Image (AI) làm nguồn (chỉ offer Multiple Uploads cùng session) — 1 SAMPLE PHỦ ĐỊNH, CHƯA đủ để kết luận Text-to-Image không bao giờ được offer làm nguồn populate. Cần re-test sau khi save artwork hoặc với artwork khác trước khi viết assertion chính thức (dù là assertion phủ định).","supersedes":"OQ-artwork-067"}
```

## OQ-artwork-layer-config-034 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-034","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"KHÔNG tìm thấy Beta badge/text nào gắn với Text to Image (AI) ở CẢ portal config UI LẪN storefront Live Preview widget panel — nhưng 2 bề mặt này đều staff-authenticated proxy (KHÔNG phải guest thật), mỗi bề mặt chỉ 1 lần thử. KHÔNG kết luận 'không có Beta badge' cho storefront PDP/theme Shopify thật tới khi có evidence guest thật.","supersedes":"OQ-artwork-068"}
```

## OQ-artwork-layer-config-035 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-035","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"CONF-CBS003-01 (UNRESOLVED, CCR CBS-003): canon KB-019 (kb_version 3.0, đã publish) ghi 2 lựa chọn; quan sát (2026-09-25, artwork 4416, layer 'hair') ghi 3 lựa chọn (thêm 'No personalization'). KHÔNG có build/version/deploy-date nguồn để phân biệt 'hành vi đã đổi thật' vs 'KB-019 từng ghi sai lúc verify trước' (CCR CBS-003 Phần 3 để trống 'không rõ'). Cần authority (orchestrator/context-quality-reviewer, hoặc PO/Dev qua CCR) quyết định theo §8 của contract. KHÔNG được dùng làm oracle chính thức cho tới khi resolve — KHÔNG viết test case assert cứng '2 lựa chọn' hay '3 lựa chọn'.","supersedes":"OQ-artwork-069"}
```

## OQ-artwork-layer-config-036 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-036","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"TIB-5188 (thứ tự resize/crop và minimum-resolution validation của pipeline GenAI khi generate ảnh từ Multiple Uploads) HOÀN TOÀN CHƯA TEST — 'Set minimum size' để OFF trên fixture duy nhất của mọi run tính tới nay, bật toggle bị đánh giá ngoài ngân sách run. KHÔNG suy diễn thành 'không có vấn đề' hay pass/fail mặc định — coverage gap thật, cần run tiếp theo với ngân sách riêng.","supersedes":"OQ-artwork-070"}
```

## OQ-artwork-layer-config-037 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-037","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Trong lần thử duy nhất, CẢ HAI route (chính và fallback) đều fail cùng lý do (ảnh bị client re-encode xuống dưới ngưỡng 10000 byte trước khi tới cả 2 route). Route fallback multipart THẬT SỰ TỒN TẠI và được tự động thử khi route chính lỗi (xác nhận), nhưng chưa có lần route fallback THÀNH CÔNG để so sánh downstream GenAI generate là sync hay async. KHÔNG suy diễn kết quả so sánh — cần fixture/ảnh input phù hợp hơn ở run tiếp theo.","supersedes":"OQ-artwork-071"}
```

## OQ-artwork-layer-config-038 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-038","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"'Duplicate & Share' (TIB-5326) KHÔNG tìm thấy ở CẢ portal editor lẫn storefront Live Preview cho layer Text to Image (AI)/Multiple Uploads — 2 agent độc lập cùng không tìm thấy, KHÔNG kết luận feature không tồn tại (có thể bị gate bởi điều kiện chưa trigger: nhiều biến thể generated, cart/order thật, plan cụ thể). Cần hỏi dev/PO trước khi viết test case chính thức.","supersedes":"OQ-artwork-072"}
```

## OQ-artwork-layer-config-039 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-039","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"Statement gốc (KB-024) tự ghi 'chưa verify trực tiếp trong evidence này' — map không render nếu thiếu Mapbox token là suy luận hợp lý, chưa phải quan sát thật.","supersedes":"OQ-artwork-073"}
```

## OQ-artwork-layer-config-040 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-040","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"Chưa xác nhận 'seacher' là typo THẬT của product code hay lỗi ghi chép evidence — nếu viết test/assertion theo tên field JSON, phải dùng đúng chuỗi thật trong code, không tự sửa chính tả.","supersedes":"OQ-artwork-074"}
```

## OQ-artwork-layer-config-041 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-041","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"Giới hạn 4296 ký tự (KB-034) là hint text UI quan sát 1 lần — CHƯA từng thử nhập vượt giới hạn để xác nhận hành vi thật, không tổng quát hoá thành validation rule chính thức.","supersedes":"OQ-artwork-075"}
```

## OQ-artwork-layer-config-042 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-042","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"DOM dump gốc (KB-030) cho thấy 'Custom class:' xuất hiện 2 lần trong cùng panel — CHƯA XÁC NHẬN đây là 2 field JSON riêng hay lỗi render trùng của portal. Cần portal-explorer verify lại trực tiếp.","supersedes":"OQ-artwork-076"}
```

## OQ-artwork-layer-config-043 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-043","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Hint 'enter number from 20' chỉ quan sát 1 lần (observed_count=1, KB-014) — chưa từng thử nhập giá trị <20 để biết đây là hard validation hay chỉ gợi ý UI.","supersedes":"OQ-artwork-077"}
```

## OQ-artwork-layer-config-044 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-044","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"bundle-registry hiện tại KHÔNG liệt kê field này gắn với layer type cụ thể nào — không thể viết assertion API/DB cho field này tới khi xác nhận được key.","supersedes":"OQ-artwork-078"}
```

## OQ-artwork-layer-config-045 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-045","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"Static Vector chưa có per-type DOM dump riêng nào khác ngoài ngoại lệ Custom class — nếu type này có field riêng trong tương lai, cần tạo KB item per-type mới, không sửa KB-011.","supersedes":"OQ-artwork-079"}
```

## OQ-artwork-layer-config-046 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-046","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"CONF-CBS004-001 (UNRESOLVED): 1 nguồn (api-explorer) quan sát 3 lần gọi liên tiếp 422 → remaining giữ nguyên = 1000 (không giảm); 1 nguồn khác (portal-explorer) quan sát 1 lần gọi 201 → remaining giảm 1 (999). Mỗi phía chỉ 1 sample, mỗi phía ở 1 status code khác nhau — KHÔNG đủ để khẳng định remaining chỉ giảm khi request THÀNH CÔNG hay theo quy tắc khác. KHÔNG tự resolve (đúng contract §8), KHÔNG dùng làm oracle behavior 'remaining' cho tới khi có thêm sample ở cả 2 status code. Cần orchestrator/reviewer quyết định hướng verify tiếp theo (vd chạy thêm N sample mỗi phía).","supersedes":"OQ-artwork-080"}
```

## OQ-artwork-layer-config-047 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-047","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Stack stroke của Paragraph (tối đa 3 lớp, width là độ dày riêng từng vòng, xếp từ mép chữ ra ngoài theo thứ tự row, xoá/đổi thứ tự giữ dữ liệu) có phải hành vi đúng theo PO/business, và có giữ nguyên trên build TIB-5580 khi ship không? Mới là quan sát một lượt chạy test staging trước khi ship; checklist không có oracle xác nhận cho các check cốt lõi của feature.","kb_ids":["KB-129","KB-130","KB-131"],"supersedes":"OQ-artwork-100"}
```

## OQ-artwork-layer-config-048 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-048","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Gửi thẳng PUT /api/artworks/{id} cho Paragraph với stroke_layers có entry thứ 4, hoặc width không phải số, thì server từ chối, cắt bớt hay lưu nguyên? Giới hạn 3 lớp chỉ thấy ở UI (nút 'Add stroke' disable); không có oracle cho validate phía server của artwork.","kb_ids":["KB-129"],"supersedes":"OQ-artwork-101"}
```

## OQ-artwork-layer-config-049 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-049","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Paragraph mới tạo khi stroke còn tắt có lưu sẵn entry stroke_layers không, và mặc định (tắt; bật lên 1 row #FF0000 / 1px; stroke_color/stroke_width bằng lớp trong cùng) có phải hành vi đúng? Dữ liệu lưu khi stroke tắt chưa quan sát; check dữ liệu mặc định của paragraph mới không có oracle.","kb_ids":["KB-132"],"supersedes":"OQ-artwork-102"}
```

## OQ-artwork-layer-config-050 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-050","type":"OPEN_ISSUE","feature_id":"text-layer-config","summary":"Preview storefront (SDK) hiển thị Paragraph nhiều lớp stroke thế nào (thứ tự vành, round, autoscale, layer linked) khi SDK staging có code TIB-5580? SDK staging chưa có code TIB-5580 nên mọi phần storefront của các test case bị Blocked; buyer thấy preview storefront trước khi đặt hàng.","kb_ids":["KB-133","KB-138","KB-139"],"supersedes":"OQ-artwork-103"}
```

## OQ-artwork-layer-config-051 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-051","type":"OPEN_ISSUE","feature_id":"text-layer-config","summary":"Bản SVG (vectorize) của order design có đúng thứ tự vành, góc round, không vẽ vành khi stroke tắt, không cắt vành khi autoscale — cho Paragraph và Text 1 dòng? Không có đường tải SVG order design trên portal staging; SVG là một đầu ra in nhưng hoàn toàn chưa được kiểm.","kb_ids":["KB-133","KB-134","KB-135","KB-139","KB-143"],"supersedes":"OQ-artwork-104"}
```

## OQ-artwork-layer-config-052 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-052","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"PNG order design khớp preview Artwork Editor (fill trên mọi vành, góc round, autoscale không cắt vành) có phải hành vi đúng, và mức chênh lệch bề dày vành nào là chấp nhận được khi đo pixel? Kết luận render đều dựa trên so sánh bằng mắt, chưa có xác nhận PO/business; check render không có ngưỡng đo khách quan.","kb_ids":["KB-130","KB-133","KB-134","KB-139"],"supersedes":"OQ-artwork-105"}
```

## OQ-artwork-layer-config-053 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-053","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Tắt stroke giữ nguyên stroke_layers (stroke_enabled=false) và bật lại khôi phục các lớp cũ có phải hành vi đúng? Quyết định check 'tắt rồi bật lại' kỳ vọng khôi phục hay reset; chưa có xác nhận.","kb_ids":["KB-135"],"supersedes":"OQ-artwork-106"}
```

## OQ-artwork-layer-config-054 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-054","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Convert Paragraph nhiều lớp sang Spiral Text và các loại layer khác ngoài Curve/Warp Text cho kết quả gì, và việc gộp về lớp trong cùng (bỏ lớp ngoài) có phải hành vi đúng? Mới quan sát Curve và Warp; người dùng mất lớp ngoài khi convert, cần biết đó là thiết kế hay lỗi. Cần PO xác nhận việc bỏ các lớp stroke ngoài khi convert sang Curve/Warp là chủ đích (dữ liệu stroke ngoài bị mất khỏi bản lưu).","kb_ids":["KB-136","KB-137"],"supersedes":"OQ-artwork-107"}
```

## OQ-artwork-layer-config-055 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-055","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Vành của Paragraph linked scale chính xác theo tỉ lệ kích thước (đo được) không, và PNG order design của layer linked có đúng như preview editor không? Tỉ lệ mới đánh giá bằng mắt trên preview editor; PNG của layer linked chưa kiểm.","kb_ids":["KB-138"],"supersedes":"OQ-artwork-108"}
```

## OQ-artwork-layer-config-056 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-056","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Việc Custom Shape text và Paragraph trên Artwork 1.0 chỉ có 1 stroke (không có stack) là quyết định sản phẩm đã duyệt chưa, và Paragraph Artwork 1.0 sau khi đổi width lưu payload thế nào? Phạm vi loại trừ mới là quan sát hiện tại; payload Paragraph Artwork 1.0 chưa kiểm được vì fixture không Save được.","kb_ids":["KB-140","KB-141","KB-142"],"supersedes":"OQ-artwork-109"}
```

## OQ-artwork-layer-config-057 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-057","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Multi-stroke của Text 1 dòng (TIB-5417) có giữ nguyên trong editor, API và PNG trên build TIB-5580 khi ship không? Regression mới kiểm trên build staging chưa ship; cần kiểm lại sau khi ship.","kb_ids":["KB-143"],"supersedes":"OQ-artwork-110"}
```

## OQ-artwork-layer-config-058 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-058","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Server phải từ chối/loại bỏ stroke_layers sai do buyer gửi kèm personalization (4 entry, width không phải số), hay chấp nhận nhưng bỏ qua khi render là đủ? API hiện trả 201 và echo phần chèn (BUG-357); chưa ai phân xử nên check của luồng này không có expected result. Cần PO xác nhận ý định (item mới chạm ranh giới ghi dữ liệu của buyer chưa đăng nhập, BUG-357).","kb_ids":["KB-144"],"supersedes":"OQ-artwork-111"}
```

## OQ-artwork-layer-config-059 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-059","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Server có thực sự lưu stroke_layers do buyer chèn vào customization, hay chỉ echo trong response? Việc lưu chỉ suy từ response echo; nếu được lưu, phần chèn có thể ảnh hưởng đầu ra khác (storefront, SVG) chưa kiểm.","kb_ids":["KB-144"],"supersedes":"OQ-artwork-112"}
```

## OQ-artwork-layer-config-060 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-060","type":"OPEN_ISSUE","feature_id":"text-layer-config","summary":"Ai đã đổi status Testlane của task TIB-220 sau lượt chạy, và status hay actualResult mới là kết quả đúng của các test case lệch ('passed' trong khi actualResult ghi Blocked; TC-TIB-6338 'skipped' trong khi actualResult ghi Fail)? Các test case này không dùng được làm nguồn xác nhận cho tới khi status và actualResult khớp.","kb_ids":["KB-133","KB-138","KB-139","KB-142","KB-144"],"supersedes":"OQ-artwork-113"}
```

## OQ-artwork-layer-config-061 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-061","type":"OPEN_ISSUE","feature_id":"text-layer-config","summary":"Global template: stroke_layers của Paragraph có là field local (không bị merge từ global template) và spiral/shape text vẫn 1 stroke không? Chưa kiểm được: fixture global template dựng qua API không mở được trong Artwork Editor trên staging (chưa rõ lỗi fixture hay lỗi sản phẩm).","kb_ids":[],"supersedes":"OQ-artwork-117"}
```

## OQ-artwork-layer-config-062 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-062","type":"OPEN_ISSUE","feature_id":"text-layer-config","summary":"Shadow của Paragraph: theo mô tả dev của TIB-5580 (PR api #4016), shadow áp 1 lần cho cả khối ở vectorize và PNG, và preview/PNG/SVG không được lệch; thay đổi này có thể làm sai ghi nhận cũ về shadow paragraph của TIB-5472. Trong lượt test staging 2026-10-21→22, editor và PNG order design cho thấy một khối shadow cho cả paragraph và PNG khớp editor (2 order Bogus); SVG và preview storefront SDK chưa kiểm. Phần editor + PNG đã quan sát nay là KB-251 (OBSERVED_CURRENT/LOW, CBS-017); quy tắc cho cả 3 renderer chưa có nguồn xác nhận. Cần chạy lại khi SDK staging có code và tải được SVG, hoặc nguồn PO/dev xác nhận.","kb_ids":["KB-251"],"supersedes":"OQ-artwork-118"}
```

## OQ-artwork-layer-config-063 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-063","type":"OPEN_ISSUE","feature_id":"text-layer-config","summary":"Fill opacity < 1 với Paragraph nhiều lớp stroke: quy tắc 'bleed trong 1 dòng là known issue, vùng stroke 2 dòng chồng nhau đậm gấp đôi là lỗi' chỉ là đáp án của QA, chưa kiểm (SVG không tải được, SDK chưa có code). Ngoài ra ở một order PNG trên staging, vành stroke trắng trông mỏng hơn hẳn so với preview editor (ước lượng bằng mắt, chưa rõ nguyên nhân) — KB-133 chỉ áp cho các stack đã so khớp, chưa áp cho trường hợp này.","kb_ids":["KB-133"],"supersedes":"OQ-artwork-119"}
```

## OQ-artwork-layer-config-064 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-064","type":"OPEN_ISSUE","feature_id":"text-layer-config","summary":"Import PSD có paragraph nhiều lớp stroke: chưa có test case, chưa có kiến thức về cách stroke_layers được tạo khi import.","kb_ids":[],"supersedes":"OQ-artwork-120"}
```

## OQ-artwork-layer-config-065 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-065","type":"OPEN_ISSUE","feature_id":"text-layer-config","summary":"Chọn nhiều layer cùng lúc (Text + Paragraph) rồi chỉnh stroke: ngoài phạm vi kiểm của TIB-5580 theo trao đổi nội bộ QA, chưa có kiến thức; chưa có xác nhận PO đây là ngoài phạm vi sản phẩm.","kb_ids":[],"supersedes":"OQ-artwork-121"}
```

## OQ-artwork-layer-config-066 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-066","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Layer Curve Text không có tuỳ chọn căn lề text (lưu align center) là thiết kế có chủ đích hay là tính năng còn thiếu? Quyết định checklist coi việc thiếu căn lề là đúng hay là gap; ảnh hưởng phạm vi kiểm render Curve Text rainbow (hiện chỉ kiểm được căn giữa).","kb_ids":["KB-157"],"supersedes":"OQ-artwork-136"}
```

## OQ-artwork-layer-config-067 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-067","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Nút 'Align' trên canvas toolbar khi chọn layer curve-text (KB-042 của editor-layer-workspace) là căn vị trí layer trên canvas hay căn lề text? Nếu 'Align' là căn lề text, KB-157 ('không có tuỳ chọn căn lề') có thể sai và Curve Text căn phải dựng được; nếu là căn vị trí layer, hai item không mâu thuẫn.","kb_ids":["KB-157"],"supersedes":"OQ-artwork-137"}
```

## OQ-artwork-layer-config-068 — CONFLICT

```json
{"oq_id":"OQ-artwork-layer-config-068","type":"CONFLICT","feature_id":"conditional-setting-config","summary":"Shape dependency của layer có điều kiện sau tính năng Hide đang mâu thuẫn: KB-067 (base) mô tả {match_type, show_by_default, dependencies}, còn KB-227 (test case PASS 2026-10-28 trên staging, trước khi các PR merge) cho thấy bản lưu mới có thêm key action ('hide'/'show') và bản ghi cũ không có action được hiểu là Show. PO chọn: (a) thay KB-067 bằng KB-227, (b) giữ cả hai như hai thời điểm dữ liệu (KB-067 thu phạm vi thành 'bản ghi trước tính năng Hide'), hay (c) giữ base? Cho tới khi chốt, mọi check oracle tầng API/data dựa vào shape dependency không có expected.","kb_ids":["KB-067","KB-227"],"side_a":"KB-067 (base, quan sát 2026-09-10): layer có condition có dependency = {match_type: 'all'|'any', show_by_default: boolean, dependencies: [{element, value},...]}.","side_b":"KB-227 (test case PASS 2026-10-28, staging lượt đầu): PUT gửi dependency có key action 'hide'/'show' cùng match_type, show_by_default, dependencies; bản ghi cũ không có key action được hiểu là Show, không bị migrate.","supersedes":"OQ-artwork-152"}
```

## OQ-artwork-layer-config-069 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-069","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Trên build đã merge, chọn Hide có đổi tooltip match type thành 'hide when all / any options are selected' và toggle 'Hide this layer on first load' có nhãn/tooltip riêng không; chuyển lại Show có khôi phục nhãn cũ không? Nguồn duy nhất là tài liệu dev viết trước khi code còn đổi, chưa test case nào kiểm.","kb_ids":["KB-223"],"supersedes":"OQ-artwork-153"}
```

## OQ-artwork-layer-config-070 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-070","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Bulk apply Conditional setting trên build đã merge có dropdown Show/Hide và áp đúng action cho mọi layer được chọn (kể cả khi các layer đang mang action khác nhau) không? Chỉ có nguồn tài liệu dev, chưa test case nào.","kb_ids":["KB-225"],"supersedes":"OQ-artwork-154"}
```

## OQ-artwork-layer-config-071 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-071","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Conditional Setting (Show/Hide) có được hỗ trợ ở cấp Group không? Ghi nhận tay của QA trái expected của test case và BUG-436 còn gắn; nếu có hỗ trợ thì UI đặt ở đâu, nếu không thì điều kiện chỉ đặt cho từng layer con.","kb_ids":["KB-226"],"supersedes":"OQ-artwork-155"}
```

## OQ-artwork-layer-config-072 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-072","type":"OPEN_ISSUE","feature_id":"conditional-setting-config","summary":"Khi action = 'hide', key show_by_default (giữ tên cũ) mang nghĩa 'Hide this layer on first load' — đây là thiết kế chủ đích của data model hay chỉ là cách hiển thị của editor/SDK? API có chấp nhận giá trị action nào khác ngoài 'hide'/'show' không?","kb_ids":["KB-227"],"supersedes":"OQ-artwork-158"}
```

## OQ-artwork-layer-config-073 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-073","type":"OPEN_ISSUE","feature_id":"condition-cycle-validation","summary":"Dòng 'Conditions haven't been finished' đi kèm thông báo vòng điều kiện ở test Hide/Show là do fixture (điều kiện chưa hoàn tất) hay luôn xuất hiện khi có vòng? Quyết định phần nào của thông báo được dùng làm expected nguyên văn.","kb_ids":["KB-228"],"supersedes":"OQ-artwork-159"}
```

## OQ-artwork-layer-config-074 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-074","type":"OPEN_ISSUE","feature_id":"conditional-setting-config","summary":"Các hành vi Show/Hide ở portal (dropdown action, một action mỗi layer, Artwork 1.0 và Convert to 2.0, vòng điều kiện giữa layer Hide, Duplicate artwork giữ action — KB-221, KB-222, KB-224, KB-228, KB-229) có giữ nguyên trên build staging sau khi 6 PR của TIB-5558 merge (2026-10-29) và trên production khi TIB-5558 release không? Kèm theo: layer của artwork 1.0 sau Convert to 2.0 và layer cũ không có key action có ẩn/hiện đúng chiều Show trên storefront chạy SDK đã có code Hide không — lượt test duy nhất cho phần storefront này chạy trên SDK bản 2026-10-14 chưa có code Hide nên chưa xác minh.","kb_ids":["KB-221","KB-222","KB-224","KB-228","artwork/artwork-list-and-clone#KB-229"],"supersedes":"OQ-artwork-161"}
```

## OQ-artwork-layer-config-075 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-075","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"PO quyết: các test case Testlane PASS trên staging (2026-10-21/22, trước khi 7 PR TIB-5580 merge) khẳng định cùng hành vi với 11 item quan sát KB-129, KB-130, KB-131, KB-132, KB-134, KB-135, KB-136, KB-137, KB-140, KB-141, KB-143 (stack tối đa 3 lớp, width từng vòng, xoá/đổi thứ tự, paragraph mới 1 row, góc round, tắt stroke giữ stroke_layers, convert sang Text/Curve/Warp, stroke legacy, Custom Shape 1 stroke, regression Text 1 dòng). teeinblue không bật supersede nên các item vẫn là OBSERVED_CURRENT/LOW và các check liên quan chưa có expected xác nhận. PO chọn: (a) nâng các hành vi này thành expected, (b) giữ là quan sát, hay (c) giữ cả hai như hai thời điểm? Cặp convert sang Curve/Warp làm mất các lớp ngoài (KB-137) có ảnh hưởng cao.","kb_ids":["KB-129","KB-130","KB-131","KB-132","KB-134","KB-135","KB-136","KB-137","KB-140","KB-141","KB-143"],"supersedes":"OQ-artwork-162"}
```

## OQ-artwork-layer-config-076 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-076","type":"OPEN_ISSUE","feature_id":"text-layer-config","summary":"Chạy lại sau merge/production: mọi lượt test multi-stroke của Paragraph (TIB-5580) chạy trên staging 2026-10-21/22, trước khi 7 PR merge (2026-10-22); SDK staging lúc đó chưa có PR sdk #2124. Ticket đã Done 2026-10-22 nhưng việc ship production chưa xác nhận. Cần chạy lại trên build đã merge (staging) và production cho editor, dữ liệu lưu, PNG order design, SVG vectorize và preview storefront rồi gửi CCR mới.","kb_ids":["KB-129","KB-130","KB-131","KB-132","KB-133","KB-134","KB-135","KB-136","KB-137","KB-138","KB-139","KB-140","KB-141","KB-142","KB-143","KB-144","KB-251"],"supersedes":"OQ-artwork-163"}
```

## OQ-artwork-layer-config-077 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-077","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Shadow của Paragraph có nhiều lớp stroke: PNG order design (API) vẽ 1 khối shadow cho cả paragraph, không lặp theo dòng, khớp preview Artwork Editor — có phải hành vi đúng không, và có giữ nguyên ở preview storefront và SVG vectorize khi SDK staging có code TIB-5580 và tải được SVG? Mới là quan sát bằng mắt trên 2 order (#1091, #1096) trong lượt test staging trước khi TIB-5580 merge, hai test case Blocked; check shadow paragraph (CHK-027) chưa có oracle xác nhận. Cần nguồn S3 (test case PASS đủ 3 renderer trên build có code, hoặc PO/dev xác nhận nguyên văn). Liên quan OQ-artwork-118.","kb_ids":["KB-251"],"supersedes":"OQ-artwork-164"}
```

## OQ-artwork-layer-config-078 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-078","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"Calendar giữ default typography Heebo/regular có phải giá trị đúng không? TC-TIB-4853 và actual của TC-TIB-4858 ghi Heebo, expected của TC-TIB-4858 ghi Heebo chuyển Roboto. Cần PO hoặc Dev xác nhận nguyên văn, có ngày; hoặc test case PASS có build.","kb_ids":["KB-415"],"supersedes":"OQ-artwork-186"}
```

## OQ-artwork-layer-config-079 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-079","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"PO xác nhận: ba nhánh của KB-416 có phải hành vi đúng không — paragraph rỗng không render trong design, chỉ khoảng trắng thì preview và design trống, xoá field nguồn populate thì preview về default text? Theo CCR, mô tả TIB-5538 ghi \"should fall back to its default text\", khác kết quả. Rủi ro cao vì ảnh hưởng nội dung design của buyer.","kb_ids":["KB-416"],"supersedes":"OQ-artwork-187"}
```

## OQ-artwork-layer-config-080 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-080","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"Upload .svg qua Static Vector tạo layer static-vector và còn sau reload có phải hành vi đúng không? Mới có một lượt chạy (TC-TIB-5705, 2026-10-14), record không ghi build.","kb_ids":["KB-417"],"supersedes":"OQ-artwork-188"}
```

## OQ-artwork-layer-config-081 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-081","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"PO xác nhận: các kết quả Design format của KB-418 có đúng không (chỉ static-vector + SVG ra file .svg; PNG_RGB báo \"Line item cannot generate design\"; lưu SVG khi còn raster layer trả HTTP 400), và SVG có phải format đúng duy nhất cho artwork chỉ có static-vector không?","kb_ids":["KB-418"],"supersedes":"OQ-artwork-189"}
```

## OQ-artwork-layer-config-082 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-082","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"Strava trong Route Maps (strava-upload) có thật sự không chạy được trên môi trường test không, lý do là gì, và production hoạt động thế nào? Nguồn của KB-419 chỉ là ghi chú ngôi thứ ba.","kb_ids":["KB-419"],"supersedes":"OQ-artwork-190"}
```

## OQ-artwork-layer-config-083 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-083","type":"NEEDS_CONFIRMATION","feature_id":"gen-ai-layer-config","summary":"Per-field warning và nút \"+ variable\" có nhận title của layer Global Option không? Comment dev #55232 của TIB-5465 nói cùng rule match; ghi chú QA audit #40 nói không nhận và lỗi có cả trên production. KB-424 chỉ phát biểu về warning \"Some ImagenHub variables have no matching layer\".","kb_ids":["KB-424"],"supersedes":"OQ-artwork-191"}
```

## OQ-artwork-layer-config-084 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-084","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Route POST /layer-images/create-master-large/batch, env MASTER_LARGE_BATCH_LIMIT (mặc định 10) và status 422 khi quá limit có đúng trên build hiện tại không? Nguồn là comment #54785 của TIB-5212 tự sinh từ branch diff, chưa kiểm trên hệ thống; comment #55717 không phát biểu lại các điểm này. Cần Dev xác nhận nguyên văn, có ngày; hoặc test case PASS có build.","kb_ids":["KB-422"],"supersedes":"OQ-artwork-192"}
```

## OQ-artwork-layer-config-085 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-085","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"KB-577: Word Cloud với shape SVG clip-path lồng nhiều cấp chỉ đặt chữ trong vùng đã mask, quan sát một lượt 2026-10-07; chưa so preview storefront/editor với final render. Đây có phải hành vi đúng không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-006.","kb_ids":["KB-577"],"supersedes":"OQ-artwork-205"}
```

## OQ-artwork-layer-config-086 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-086","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"KB-578: Word Cloud bật \"Use shape's color\" trên shape SVG clip-path chỉ lấy màu từ vùng nhìn thấy, quan sát một lượt 2026-10-07. Đây có phải hành vi đúng không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-007.","kb_ids":["KB-578"],"supersedes":"OQ-artwork-206"}
```

## OQ-artwork-layer-config-087 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-087","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"KB-579: Word Cloud với shape SVG đơn giản, shape PNG lấp chữ trong shape, tắt custom shape thì lấp đầy ô vuông, quan sát một lượt 2026-10-07 không có baseline trước fix. Đây có phải hành vi đúng không? Liên quan CHK-008.","kb_ids":["KB-579"],"supersedes":"OQ-artwork-207"}
```

## OQ-artwork-layer-config-088 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-088","type":"OPEN_ISSUE","feature_id":"special-layer-config","summary":"Preview Word Cloud trên storefront và artwork editor với shape SVG clip-path lồng nhiều cấp có khớp final render (design PNG) không? Lượt test tương ứng đang tạm dừng; KB-577, KB-578 chỉ nói về final render.","kb_ids":["KB-577","KB-578"],"supersedes":"OQ-artwork-208"}
```

## OQ-artwork-layer-config-089 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-089","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"KB-580: layer QR Code render nguyên vẹn và decode đúng chuỗi ở cả design PNG và PDF của cùng đơn, quan sát một lượt 2026-10-07. Đây có phải hành vi đúng không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-007.","kb_ids":["KB-580"],"supersedes":"OQ-artwork-209"}
```

## OQ-artwork-layer-config-090 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-090","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"KB-581: SVG layer image upload 05/2025 re-render design PNG bình thường, mẫu 3 file ngày 2026-10-07. Đây có phải hành vi đúng không, kể cả SVG cũ có <text> sống? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-012.","kb_ids":["KB-581"],"supersedes":"OQ-artwork-210"}
```

## OQ-artwork-layer-config-091 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-091","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"KB-582: upload SVG làm layer image thì bản lưu bỏ DOCTYPE, ENTITY, <script> và không trả 500, quan sát một lượt 2026-10-07; SSRF, DoS, file cực lớn chưa kiểm. Đây có phải hành vi đúng không? Cần PO xác nhận (bảo mật). Liên quan CHK-013.","kb_ids":["KB-582"],"supersedes":"OQ-artwork-211"}
```

## OQ-artwork-layer-config-092 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-092","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"KB-583: tên file SVG upload được làm sạch, key lưu ngẫu nhiên, tên > 255 ký tự bị validate chặn, quan sát một lượt 2026-10-07 qua API. Đây có phải hành vi đúng không, và UI hiển thị tên ra sao? Cần PO xác nhận (bảo mật). Liên quan CHK-014, CHK-015.","kb_ids":["KB-583"],"supersedes":"OQ-artwork-212"}
```

## OQ-artwork-layer-config-093 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-093","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"KB-584: file SVG nguồn trên CDN giữ nguyên tập id, không prefix svg- sau recolor và đặt order, 2 file mẫu ngày 2026-10-08. Đây có phải hành vi đúng không? Liên quan CHK-016.","kb_ids":["KB-584"],"supersedes":"OQ-artwork-213"}
```

## OQ-artwork-layer-config-094 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-094","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"KB-418 (lượt chạy 2026-10-14) ghi artwork chỉ có layer static-vector, Design format PNG_RGB thì order báo \"Line item cannot generate design\"; KB-570 và KB-581 (lượt chạy 2026-10-07) thấy design PNG của artwork có layer SVG render bình thường. Nguồn không nói artwork của hai lượt khác nhau ở điểm nào (có layer raster hay không). Đây là hai fixture khác nhau hay một hành vi chưa ổn định? Liên quan OQ-artwork-189, CHK-010.","kb_ids":["KB-418","artwork-render/print-design-render#KB-570","KB-581"],"supersedes":"OQ-artwork-214"}
```

## OQ-artwork-layer-config-095 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-095","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"KB-225 / CHK-017 mô tả lối vào \"Bulk apply Conditional setting\" từ layer action bar; theo KB-908 (TC-01 2026-10-30) mục \"Conditional setting\" đó đã bị TIB-5299 bỏ khỏi menu More (…), Conditional giờ nằm trong modal Bulk edit. KB-225 / CHK-017 còn đúng không? OQ-artwork-154 vẫn mở. Cần: Run có lock conditional-setting-config cập nhật KB-225 / CHK-017 sau khi CONF-CBS-092-01 được resolve; PO hoặc Dev xác nhận Show/Hide khi bulk apply Conditional trong modal.","kb_ids":["KB-225"],"check_ids":["CHK-017"],"related_oq_ids":["OQ-artwork-layer-config-070"],"supersedes":"OQ-artwork-289"}
```

## OQ-artwork-layer-config-096 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-096","type":"NEEDS_CONFIRMATION","feature_id":"clipart-layer-config","kb_ids":["KB-087","KB-088"],"summary":"KB-087, KB-088 (2026-09-21) mô tả field inventory của dialog Bulk Edit trước TIB-5299 (dialog mở cho 1 layer clipart-category). Modal Bulk edit mới (feature layer-bulk-edit: KB-883 field mở ra rỗng / No change, KB-885, KB-893 tập field chung) có thể làm hai item này cũ. CCR không khai quan hệ, không sửa. Cần: quan sát lại panel cấu hình 1 layer clipart-category trên build hiện tại.","supersedes":"OQ-artwork-295"}
```

## OQ-artwork-layer-config-097 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-097","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-910"],"summary":"KB-910: Contour cut ở Border size 1 vẽ viền theo outline phần đục của clipart, không thành khung vuông theo bounding box, chỉ là quan sát test case (một layer Clipart Category, Artwork editor, zoom 50%, không ghi build). Đây có phải hành vi đúng ở mọi size không? Bản fix đã được Dev xác nhận ở KB-912. Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5592), hoặc test case PASS có căn cứ expected và ghi build/bản đã test.","check_ids":["CHK-002"],"supersedes":"OQ-artwork-297"}
```

## OQ-artwork-layer-config-098 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-098","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-911"],"summary":"KB-911: Contour cut ở Border size 1–3 chỉ vẽ màu viền thành vòng ngoài hình, không ám màu lên clipart hay vùng trong suốt, ảnh viền nằm dưới ảnh clipart — chỉ là quan sát test case. Đây có phải cách vẽ đúng (kể cả thứ tự lớp viền dưới clipart) không? Size 2 và 3 khác nhau thế nào về độ dày? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5592), hoặc test case PASS có căn cứ expected và ghi build/bản đã test.","check_ids":["CHK-002"],"supersedes":"OQ-artwork-298"}
```

## OQ-artwork-layer-config-099 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-099","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-916"],"summary":"KB-916: thiết lập Border đọc lại đúng sau Save & Close + reload và field photo_border (size, type, color, display, line, enabled; display mockup_order = \"Mockup Preview & Order Design\") chỉ là quan sát một mẫu. Tập giá trị đầy đủ của type và display là gì, và đây có phải contract lưu chuẩn không? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5592), hoặc test case PASS có căn cứ expected và ghi build/bản đã test.","check_ids":["CHK-014","CHK-015"],"supersedes":"OQ-artwork-299"}
```

## OQ-artwork-layer-config-100 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-100","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-917"],"summary":"KB-917: Undo/Redo khi đổi Border size trả cả giá trị lẫn hình vẽ, Duplicate layer giữ nguyên thiết lập Border — chỉ là quan sát test case trên một layer đơn, bản copy không được lưu. Đây có phải hành vi đúng không, và Border của bản copy có giữ sau Save không? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5592), hoặc test case PASS có căn cứ expected và ghi build/bản đã test. Thêm: chưa rõ TC-27 dùng thao tác Duplicate nào — theo KB-045 layer Clipart Category có thể tạo bản LINKED, và KB-429 ẩn Photo Border khi selection có layer Linked, nên chưa rõ Border của bản copy được đọc thế nào; số phím gõ khi đổi size 3 → 1 không ghi, chưa đối chiếu được với luật mỗi phím là 1 undo step của KB-428 (nêu cho multi-select).","check_ids":["CHK-016","CHK-017"],"supersedes":"OQ-artwork-300"}
```

## OQ-artwork-layer-config-101 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-101","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-918","KB-914"],"summary":"KB-918: Dev/PO cho biết Border size = 0 (min theo KB-914) phải vẽ gì — không có viền hay giá trị khác? Một lượt quan sát trong Artwork editor thấy size 0 vẽ viền dày như size 10; đây có phải lỗi không? Chưa chạy lại, chưa kiểm storefront và Order Design ở size 0; QA có bug draft chưa submit, chưa có ticket. Cần: Dev hoặc PO xác nhận nguyên văn, có ngày, expected của size 0 (Jira TIB-5592 hoặc ticket mới do operator quyết). Không tự tạo issue.","check_ids":["CHK-012"],"supersedes":"OQ-artwork-301"}
```

## OQ-artwork-layer-config-102 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-102","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-915","artwork-editor/editor-layer-workspace#KB-429"],"summary":"KB-915: \"Linked clipart\" Dev liệt kê trong các loại layer dùng chung hàm vẽ viền có phải layer customization type Linked của KB-429 (Photo Border bị ẩn khi selection có layer Linked) không? Nếu là cùng loại thì Photo Border áp cho Linked theo đường nào (layer nguồn hay chính layer Linked)? Cần: Dev xác nhận nguyên văn, có ngày (Jira TIB-5592 hoặc TIB-5212).","check_ids":["CHK-008"],"supersedes":"OQ-artwork-302"}
```

## OQ-artwork-layer-config-103 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-103","type":"OPEN_ISSUE","feature_id":"photo-upload-layer-config","kb_ids":["KB-912","KB-913","KB-915"],"summary":"Bề mặt và loại layer chưa kiểm sau fix TIB-5592: chưa chạy kết quả vẽ viền ở storefront live preview (mockup), cart Edit design, Portal View/Edit customization (KB-912), file Order Design và mockup render (KB-913); chưa kiểm các loại layer ngoài Clipart Category — Dynamic clipart (dynamic_by_text), Clipart group, Linked clipart, Static image, Photo Upload — và border kiểu Custom shape (KB-915). Cần: Chạy test case trên các bề mặt và loại layer này (store explorer), ghi build. Riêng Custom shape: KB-912 chỉ mô tả lỗi cho Contour cut, chưa rõ Custom shape ở size 1–3 phải vẽ thế nào (CHK-009 chưa có oracle). Các check READY CHK-003..CHK-007 đóng phần bề mặt khi được chạy.","check_ids":["CHK-009"],"supersedes":"OQ-artwork-303"}
```

## OQ-artwork-layer-config-104 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-104","type":"OPEN_ISSUE","feature_id":"photo-upload-layer-config","kb_ids":["KB-914"],"summary":"KB-914: max (không có), step = 1 và cách ô Border size xử lý số thập phân chưa được kiểm runtime; kết quả vẽ ở giá trị lớn (vd size 100) chưa chạy. Cần: Chạy test case boundary cho ô Border size, ghi build.","check_ids":["CHK-013"],"supersedes":"OQ-artwork-304"}
```

## OQ-artwork-layer-config-105 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-105","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-913"],"check_ids":["CHK-005"],"summary":"PO xác nhận KB-913 (chạm order/fulfillment, oracle STRONG duy nhất của CHK-005 P1): server render (file Order Design, mockup render) vẽ Photo Border bằng code riêng, không bị lỗi TIB-5592, và đơn đã render không cần regenerate. Hiện chỉ có lời Dev (Jira TIB-5592 comment 55072, 2026-10-19), QA chưa kiểm Order Design file và mockup render. KB-913 không nói gì về border custom_shape trên print file: câu đó vẫn ở OQ-artwork-195 (còn mở). Cần: PO xác nhận nguyên văn, có ngày.","supersedes":"OQ-artwork-305"}
```

## OQ-artwork-layer-config-106 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-106","type":"OPEN_ISSUE","feature_id":"photo-upload-layer-config","kb_ids":["KB-930"],"summary":"KB-930: photo layer No personalization được coi là populated với mọi nguồn (Dev TIB-5521 55637 Q4), nhưng nguồn {{input}} trần chưa được QA kiểm (mới kiểm photo, Photo Reposition, Multiple Uploads {{input.1}}, output effect). Cần: Test case PASS có ngày/build cho nguồn {{input}} trần, hoặc run explore hẹp.","supersedes":"OQ-artwork-306"}
```

## OQ-artwork-layer-config-107 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-107","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-931"],"summary":"KB-931: photo layer No personalization bỏ qua Direct upload style (ảnh mặc định fill, populated contain) ở Mockup Editor, Campaign Editor, storefront preview và order design chỉ là quan sát QA-3402 (AI chạy 2026-10-26, căn cứ expected không rõ). Đây có phải fit rule đúng? Cần: PO hoặc Dev xác nhận nguyên văn có ngày trên Jira TIB-5521, hoặc test case Testlane PASS có căn cứ expected và build. Người quyết: PO (cờ requires_human_decision của diff cho KB-931).","check_ids":["CHK-064"],"supersedes":"OQ-artwork-307"}
```

## OQ-artwork-layer-config-108 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-108","type":"OPEN_ISSUE","feature_id":"photo-upload-layer-config","kb_ids":["KB-936"],"summary":"KB-936 (known defect): API áp placement position của layer No personalization đã populated, SDK preview thì không (Dev TIB-5521 55637 Q3, chỉ đề xuất chấp nhận). PO có chấp nhận khác biệt preview/design này không? QA TC-09 chưa tái hiện được lệch vị trí. Cần: PO trả lời Q3 trên TIB-5521; ai đó tái hiện lệch vị trí trên staging hoặc tách ticket bug. Người quyết: PO (cờ requires_human_decision của diff cho KB-936).","check_ids":["CHK-066"],"supersedes":"OQ-artwork-308"}
```

## OQ-artwork-layer-config-109 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-109","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-937"],"summary":"KB-937: layer No personalization không có ảnh mặc định và không có retrieval value thì SDK preview không vẽ gì (Dev 55639 RQ6 mô tả hiện trạng có từ trước). Đây có phải expected không? Cần: PO xác nhận nguyên văn có ngày (TIB-5521 hoặc ticket riêng).","check_ids":["CHK-065"],"supersedes":"OQ-artwork-309"}
```

## OQ-artwork-layer-config-110 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-110","type":"OPEN_ISSUE","feature_id":"gen-ai-layer-config","kb_ids":["KB-942"],"summary":"KB-942: Gen AI effect chỉ có ở Photo layer trên Artwork 2.0 (Dev TIB-5573 56104). Trạng thái ship khai UNKNOWN; Gen AI effect của layer clipart Artwork 1.0 chưa được thử. Cần: Xác nhận đã ship; test case cho clipart Artwork 1.0 nếu còn artwork 1.0 trên staging. Người quyết: PO (cờ requires_human_decision của diff cho KB-942).","supersedes":"OQ-artwork-310"}
```

## OQ-artwork-layer-config-111 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-111","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-943"],"summary":"KB-943: danh sách field output size theo model (GPT gpt-image-2, Gemini pro/31, Flux 2, không field với Flux 1/gpt-image-1.5/ImagenHub; Default chọn sẵn) chỉ là quan sát QA-3435 2026-10-27, build không ghi. Field nằm sau Prompt / Example prompts, lệch mô tả 'under the provider' của Dev summary 55645. gpt-image-2.5-flare/sunburst chưa kiểm. Đây có phải danh sách và vị trí đúng? Cần: Dev/PO xác nhận nguyên văn có ngày (TIB-5561), hoặc test case Testlane PASS có build và căn cứ expected; kiểm gpt-image-2.5-flare/sunburst.","check_ids":["CHK-073"],"supersedes":"OQ-artwork-311"}
```

## OQ-artwork-layer-config-112 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-112","type":"OPEN_ISSUE","feature_id":"gen-ai-layer-config","kb_ids":["KB-944"],"summary":"KB-944: khi 0.5K lưu dưới nano_banana_31 và account chuyển sang pro, generate 2K (Dev 55697 Q1). TC-06 (build không ghi) thấy dropdown lúc đó không chọn gì (không hiện Default, không hiện 2K) — vế này chưa có xác nhận, không nạp. Cần: Dev xác nhận dropdown hiển thị gì ở pro với 0.5K đã lưu, hoặc test case có build.","supersedes":"OQ-artwork-312"}
```

## OQ-artwork-layer-config-113 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-113","type":"OPEN_ISSUE","feature_id":"gen-ai-layer-config","kb_ids":["KB-945"],"summary":"KB-945: qua API/MCP chỉ điền 1 field Flux thì được nhận nhưng bị bỏ qua, size theo tỉ lệ layer (Dev 55697 Q2) — phần này chưa được QA kiểm. Cần: Test case PASS có build gửi 1 field qua REST/MCP.","supersedes":"OQ-artwork-313"}
```

## OQ-artwork-layer-config-114 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-114","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-947"],"summary":"KB-947: portal không check 4 MP trước khi save, lỗi về từ server sau khi bấm Save và editor vẫn mở — chỉ từ Dev summary 55645 (Known limitation) và TC-15 (build không ghi). Đây có phải hành vi chấp nhận được? Cần: PO/Dev xác nhận nguyên văn có ngày (TIB-5561).","check_ids":["CHK-082"],"supersedes":"OQ-artwork-314"}
```

## OQ-artwork-layer-config-115 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-115","type":"OPEN_ISSUE","feature_id":"gen-ai-layer-config","kb_ids":["KB-948","KB-946"],"summary":"KB-948 (known defect): thông báo 4 MP hiện ghi 'must be less than' trên cả 3 nơi dù biên là ≤ (KB-946). Dev đồng ý đổi sang 'must not exceed …' nhưng PO chưa trả lời (QA hỏi ở 55728, 2026-10-27). RA QA-3435 ghi Single upload là 'must not exceed' theo lịch sử QA-3181, trái quan sát TC-17 — chưa chọn bên nào. Cần: PO chốt chữ thông báo; sau khi ship, test case có build đọc lại chữ trên 3 nơi (kể cả GO Single upload).","check_ids":["CHK-084"],"supersedes":"OQ-artwork-315"}
```

## OQ-artwork-layer-config-116 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-116","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-950"],"summary":"KB-950: Gen AI effect của Single upload có Resolution 1K/2K/4K không có Default, GPT chọn sẵn 1K, Gemini 2K (TC-11, build không ghi; Dev summary 55645 gọi là khác biệt có chủ đích). Đây có phải expected? Cần: PO/Dev xác nhận nguyên văn có ngày (TIB-5561), hoặc test case có build và căn cứ expected.","check_ids":["CHK-074"],"supersedes":"OQ-artwork-316"}
```

## OQ-artwork-layer-config-117 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-117","type":"OPEN_ISSUE","feature_id":"photo-upload-layer-config","kb_ids":["KB-951"],"summary":"KB-951 (known limitation): sau khi chọn resolution không chọn lại Default được; GPT/Gemini phải tạo lại layer, Flux xoá cả 2 field. PO chưa xác nhận chấp nhận cho release (Dev 55697 Q5 'PO to confirm release'). Cần: PO trả lời trên TIB-5561 có chấp nhận cho release không; nếu không, ticket sửa.","check_ids":["CHK-076"],"supersedes":"OQ-artwork-317"}
```

## OQ-artwork-layer-config-118 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-118","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-952"],"summary":"KB-952: giá trị output size lưu dạng chuỗi trong layer JSON, giữ sau reload/duplicate, storefront generate dùng giá trị đó — chỉ là quan sát TC-08/09/27 (build không ghi, không có căn cứ expected cho lưu/reload/duplicate). Liên quan OQ-sdk-040 (object sdk, không gỡ). Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có build và căn cứ expected.","check_ids":["CHK-075"],"supersedes":"OQ-artwork-318"}
```

## OQ-artwork-layer-config-119 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-119","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-954"],"summary":"KB-954: ở đường portal/REST server không check lại allowed values của output size (Dev 55697 Q7 mô tả hiện trạng; TC-31 thấy giá trị lạ qua REST được lưu). Đây là hành vi chấp nhận hay cần thêm validate phía server? Cần: PO quyết; Dev xác nhận có ngày. Người quyết: PO (cờ requires_human_decision của diff cho KB-954).","check_ids":["CHK-081"],"supersedes":"OQ-artwork-319"}
```

## OQ-artwork-layer-config-120 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-120","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-955"],"summary":"KB-955: ô Flux width/height chỉ giữ số, Save ô rỗng báo required, tên GO chứa payload hiện nguyên chữ — chỉ là quan sát TC-33 (build không ghi, căn cứ expected KHÔNG CÓ). Đây có phải hành vi đúng? Cần: Dev/PO xác nhận, hoặc test case Testlane PASS có build và căn cứ expected. Người quyết: PO (cờ requires_human_decision của diff cho KB-955).","check_ids":["CHK-083"],"supersedes":"OQ-artwork-320"}
```

## OQ-artwork-layer-config-121 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-121","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-956"],"summary":"KB-956: cảnh báo thiếu API key trong danh sách effect của layer/GO editor mở rộng cho OpenAI/Flux/Gemini, Gen AI Effect khi chưa có default provider, Remove background khi chưa chọn remover — chỉ theo dev doc tự sinh từ branch diff (TIB-5470 53778), không có kết quả chạy có ngày. Đây có phải hành vi đúng? Cần: PO/Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có build (TC-32 hiện chỉ có status passed).","check_ids":["CHK-086"],"supersedes":"OQ-artwork-321"}
```

## OQ-artwork-layer-config-122 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-122","type":"OPEN_ISSUE","feature_id":"clipart-layer-config","kb_ids":["KB-957"],"summary":"KB-957: logic grouped_clipart theo chế độ manual/auto (Dev TIB-5412 52817). Manual/auto ứng với layer type nào (dynamic-by-text / clipart-frame là cách hiểu của QA) và 'option đầu tiên' theo thứ tự nào chưa rõ. TC-09 chưa viết lại, TC-10 chưa có kết quả chạy. Cần: Dev xác nhận mapping manual/auto sang layer type và thứ tự 'option đầu tiên', có ngày.","check_ids":["CHK-087"],"supersedes":"OQ-artwork-322"}
```

## OQ-artwork-layer-config-123 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-123","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["artwork-render/populate-channels-config#KB-1000"],"summary":"CLAIM-27 (S0, không nạp KB): layer Dynamic Clipart by Text so khớp text buyer gõ với tên option clipart (origin_name/name) và group_name sau khi chuẩn hoá cả hai phía về Unicode NFC (tên lưu NFD khớp text gõ NFC và ngược lại; áp cho nguồn clipart và grouped_clipart). Chỉ có note kỹ thuật Dev TIB-5412 comment 51755 (2026-09-23), không ai xác nhận; TC QA Hub passed nhưng actualResult rỗng. Liên quan OQ-artwork-290, OQ-asset-category-045. Cần: Dev/PO xác nhận nguyên văn có ngày, PR teeinblue-sdk #2036 kèm diff (dev_doc), hoặc test case Testlane PASS có ngày, build và căn cứ expected. Thêm (CBS-115, 2026-11-11): rule QA FACT-164 (QA ghi nhận 2026-10-26, QA-3418 RQ10; QA nói chưa chắc cơ chế) ghi Dynamic Clipart by Text chọn clipart theo tên clipart khớp ký tự input ({{char1}}...), không theo tên file/asset — nạp KB-1000 (populate-values, PROPOSED/LOW), check CHK-058 của populate-values. Vẫn cần Dev/PO xác nhận cơ chế so khớp tên (và chuẩn hoá NFC).","check_ids":["CHK-088","populate-values#CHK-058"],"supersedes":"OQ-artwork-323"}
```

## OQ-artwork-layer-config-124 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-124","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":[],"summary":"CLAIM-28 (S0, không nạp KB): sau chuẩn hoá NFC, tên ASCII vẫn khớp như cũ, so khớp vẫn phân biệt hoa thường, text rỗng hoặc chỉ khoảng trắng không khớp clipart nào. Chỉ có mục 'Possible test cases' trong note Dev TIB-5412 comment 51755 (2026-09-23), không ai xác nhận. Liên quan OQ-artwork-290, OQ-asset-category-045. Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected.","check_ids":["CHK-088"],"supersedes":"OQ-artwork-324"}
```

## OQ-artwork-layer-config-125 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-125","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-931","artwork-render/populate-output-chain#KB-860"],"summary":"KB-860 (populate-values) ghi preview storefront 'vẫn fit ảnh vào khung layer' với layer No personalization populate {{output}} từ Photo Reposition; KB-931 (quan sát) ghi ảnh populated thì contain. Chưa rõ 'fit' của KB-860 là contain hay fill; nếu là fill thì hai item lệch nhau. Không tự phân xử. Cần: Dev xác nhận có ngày (TIB-5504 hoặc TIB-5521).","supersedes":"OQ-artwork-327"}
```

## OQ-artwork-layer-config-126 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-126","type":"NEEDS_CONFIRMATION","feature_id":"gen-ai-layer-config","kb_ids":["KB-114","KB-018","KB-019","KB-943"],"summary":"KB-114 (Flux Text to Image: ảnh theo tỉ lệ layer, không thấy field size) và inventory KB-018/KB-019 (quan sát 2026-09) có thể đã cũ với account dùng Flux 2 / GPT gpt-image-2 / Gemini, vì TIB-5561 thêm field output size theo model (KB-943). Base không ghi model của account lúc quan sát nên không tính là conflict. Cần: re-verify (REFRESH) field theo model của account, hoặc Dev xác nhận có ngày.","supersedes":"OQ-artwork-328"}
```

## OQ-artwork-layer-config-127 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-127","type":"NEEDS_CONFIRMATION","feature_id":"gen-ai-layer-config","kb_ids":["KB-939","KB-940","KB-941","KB-943","KB-944"],"summary":"Tên model Gemini: KB-939..KB-941 dùng 'Nano Banana 2.1' (không có 0.5K), KB-943/KB-944 dùng key nano_banana_31 = 'Nano Banana 2 (3.1)' (có 0.5K). Hiện coi là hai model khác nhau; key API của Nano Banana 2.1 chưa ghi, và KB-943 chụp 2026-10-27, trước fix TIB-5573 Q2 (2026-10-30). Cần: Dev xác nhận key model và danh sách Resolution theo từng model.","supersedes":"OQ-artwork-329"}
```

## OQ-artwork-layer-config-128 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-128","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","kb_ids":["KB-975"],"summary":"KB-975: kéo thả nhiều dòng liền nhau (≥10) ở tab Re-order đưa cả khối về ngay dưới dòng đích, giữ thứ tự (QA-3352 TC-03, AI, không ghi build). Cần xác nhận đây là hành vi mong muốn; căn cứ expected chỉ là dev summary ticket fix.","supersedes":"OQ-artwork-336"}
```

## OQ-artwork-layer-config-129 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-129","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","kb_ids":["KB-975","KB-976"],"summary":"KB-975/KB-976: mỗi case multi-drag chỉ có một lượt PASS, trong khi lỗi gốc ngẫu nhiên theo index (dev gợi ý lặp 3–5 lần). Kết quả có ổn định qua nhiều lượt không?","supersedes":"OQ-artwork-337"}
```

## OQ-artwork-layer-config-130 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-130","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","kb_ids":["KB-976"],"summary":"KB-976: các dòng không liền nhau sau khi kéo được gom theo thứ tự gốc của danh sách, không theo thứ tự click (QA-3352 TC-04, AI). Đây có phải hành vi mong muốn? Repro gốc của QA (2026-08-25) ghi kỳ vọng \"9-10-19...\" cho chuỗi click 9-10-19-11..18 — đó là thứ tự click hay tên dòng? Nếu là kỳ vọng theo thứ tự click thì trái quan sát.","supersedes":"OQ-artwork-338"}
```

## OQ-artwork-layer-config-131 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-131","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","kb_ids":["KB-977"],"summary":"KB-977: click thường (không phím bổ trợ) vào dòng chưa chọn thêm dòng đó vào selection ở tab Re-order. Cơ chế này chỉ có ghi nhận Slack không rõ người xác nhận; cần xác nhận là hành vi mong muốn.","supersedes":"OQ-artwork-339"}
```

## OQ-artwork-layer-config-132 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-132","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","kb_ids":["KB-978"],"summary":"KB-978: click lại dòng đang chọn bỏ chọn riêng dòng đó, click ra ngoài danh sách bỏ chọn tất cả (ảnh chụp máy TC-22, chưa ai tick). Cần người xác nhận; click ngoài danh sách mới thử ở tiêu đề tab, vùng khác chưa thử.","supersedes":"OQ-artwork-340"}
```

## OQ-artwork-layer-config-133 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-layer-config-133","type":"OPEN_ISSUE","feature_id":"form-elements-config","kb_ids":["KB-979"],"summary":"KB-979 (giới hạn đã biết): cụm nhiều dòng thả sát mép trên/dưới danh sách Re-order rơi về đầu/cuối danh sách thay vì đúng chỗ con trỏ. PO có chấp nhận giới hạn này không, có kế hoạch sửa không?","supersedes":"OQ-artwork-341"}
```

## OQ-artwork-layer-config-134 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-134","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","kb_ids":["KB-980"],"summary":"KB-980: kéo một dòng ở tab Re-order thì dòng nằm ngay dưới dòng đích (automation, chưa kiểm tay). Cần xác nhận là hành vi mong muốn.","supersedes":"OQ-artwork-342"}
```

## OQ-artwork-layer-config-135 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-135","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","kb_ids":["KB-980"],"summary":"Tab Re-order: kéo một dòng thả xuống cuối danh sách luôn dừng ngay trước dòng cuối cùng ở lượt automation 2026-09-28 (lượt 2026-09-18 thì qua). Đây là giới hạn thật của widget (không có vùng thả sau dòng cuối) hay do cách giả lập chuột? Phần này không đưa vào KB.","supersedes":"OQ-artwork-343"}
```

## OQ-artwork-layer-config-136 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-136","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","kb_ids":["KB-981"],"summary":"KB-981: label chứa HTML/script hiển thị dạng chữ thường trong tab Re-order, không tạo node thật (QA-3352 TC-18, AI, không build). Phía storefront (form và console) chưa chạy vì thiếu campaign đã publish; artifact trích không thể hiện riêng bước reload. Cần xác nhận hành vi mong muốn và chạy phần storefront.","supersedes":"OQ-artwork-344"}
```

## OQ-artwork-layer-config-137 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-137","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","kb_ids":["KB-982"],"summary":"KB-982: label dài (5000 ký tự trong lượt test) và label có ký tự điều khiển được lưu nguyên, reorder/Save vẫn chạy (QA-3352 TC-20, AI). Giới hạn độ dài label theo field là bao nhiêu, vượt giới hạn thì cắt hay báo lỗi? Thêm (diff): ký tự điều khiển trong lượt test có gồm NUL không; NUL trong label có gây 500 như Option title (KB-972) không?","supersedes":"OQ-artwork-345"}
```

## OQ-artwork-layer-config-138 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-138","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","summary":"Shift-click trong tab Re-order làm gì? Hai quan sát ngược nhau: (a) ghi nhận Slack không rõ người xác nhận nói chọn dòng đó và mọi dòng phía trên tới đầu danh sách; (b) ảnh chụp máy TC-21 (2026-09-18, chưa tick) thấy chỉ chọn dải liền giữa hai lần click. Không nạp KB, không check nào assert shift-click.","supersedes":"OQ-artwork-346"}
```

## OQ-artwork-layer-config-139 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-139","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","summary":"Dev summary ticket fix TIB-5354 (2026-09-07) nói fix chỉ nằm trong portal (tab Re-order, chỉ luồng multi-drag), API và SDK không đổi, thư viện kéo thả gốc chưa sửa. Chưa ai xác nhận phạm vi này. Các danh sách kéo thả nhiều dòng khác dùng cùng thư viện có bị lỗi sắp index tương tự không?","supersedes":"OQ-artwork-347"}
```

## OQ-artwork-layer-config-140 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-140","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “[CRITICAL] PUT trực tiếp với payload chứa đồ thị vòng — server có tự chặn độc lập với client?” của feature condition-cycle-validation. missing_or_unresolved_oracle","supersedes":"OQ-artwork-373"}
```

## OQ-artwork-layer-config-141 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-141","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-009 “PUT trực tiếp với self-loop (element trỏ chính layer đó)” của feature condition-cycle-validation. missing_or_unresolved_oracle","supersedes":"OQ-artwork-374"}
```

## OQ-artwork-layer-config-142 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-142","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-010 “Thuật toán chọn 'layer gốc' hiển thị đầu message lỗi với cấu trúc dependency khác” của feature condition-cycle-validation. missing_or_unresolved_oracle","supersedes":"OQ-artwork-375"}
```

## OQ-artwork-layer-config-143 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-143","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011 “Hành vi storefront nếu 1 artwork có vòng lọt qua được validation” của feature condition-cycle-validation. missing_or_unresolved_oracle","supersedes":"OQ-artwork-376"}
```

## OQ-artwork-layer-config-144 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-144","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Giới hạn số condition tối đa trên 1 layer” của feature conditional-setting-config. missing_or_unresolved_oracle","supersedes":"OQ-artwork-377"}
```

## OQ-artwork-layer-config-145 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-145","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-009 “Hỗ trợ lồng nhóm AND trong OR (nested logic)” của feature conditional-setting-config. missing_or_unresolved_oracle","supersedes":"OQ-artwork-378"}
```

## OQ-artwork-layer-config-146 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-146","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-010 “Toán tử condition ngoài 'is any of' và on/off (is-none-of, contains, so sánh số/ngày)” của feature conditional-setting-config. missing_or_unresolved_oracle","supersedes":"OQ-artwork-379"}
```

## OQ-artwork-layer-config-147 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-147","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011 “2 layer type không có accordion CONDITIONAL SETTING — có đường API bypass để set condition không” của feature conditional-setting-config. missing_or_unresolved_oracle","supersedes":"OQ-artwork-380"}
```

## OQ-artwork-layer-config-148 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-148","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “dependencies[].element luôn có dạng 'layer-<6 chữ số>'” của feature layer-condition-value-binding. missing_or_unresolved_oracle","supersedes":"OQ-artwork-386"}
```

## OQ-artwork-layer-config-149 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-149","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “toggle=false (Off) serialize thành gì — chưa từng được lưu qua Save” của feature layer-condition-value-binding. missing_or_unresolved_oracle","supersedes":"OQ-artwork-387"}
```

## OQ-artwork-layer-config-150 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-150","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-009 “Multi-value (≥2 phần tử) cho 6/8 type nguồn dạng array còn lại (ngoài clipart-category)” của feature layer-condition-value-binding. missing_or_unresolved_oracle","supersedes":"OQ-artwork-388"}
```

## OQ-artwork-layer-config-151 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-151","type":"NEEDS_CONFIRMATION","feature_id":"conditional-setting-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-010 “Trạng thái data addon-charge/json-list trên artwork 4087 khác nhau giữa 2 run (CONF-002)” của feature layer-condition-value-binding. missing_or_unresolved_oracle","supersedes":"OQ-artwork-389"}
```

## OQ-artwork-layer-config-152 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-152","type":"NEEDS_CONFIRMATION","feature_id":"form-elements-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-009 “Color (color) — KHÔNG xuất hiện được làm nguồn Conditional Setting dù có đầy đủ Option Title (khác Font CÓ xuất hiện được) — nguyên nhân chưa xác nhận” của feature layer-config-form-elements. missing_or_unresolved_oracle","supersedes":"OQ-artwork-390"}
```

## OQ-artwork-layer-config-153 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-153","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Static Image (static-photo) — theo baseline chung NHƯNG là 1/2 type KHÔNG có field 'Custom class:'” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-391"}
```

## OQ-artwork-layer-config-154 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-154","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “Clipart Category › 1 Clipart category (clipart-category) — theo baseline chung, không có deviation riêng ghi nhận” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-392"}
```

## OQ-artwork-layer-config-155 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-155","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-003 “Clipart Category › Group of clipart categories (group-clipart-categories) — theo baseline chung, không có deviation riêng ghi nhận” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-393"}
```

## OQ-artwork-layer-config-156 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-156","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “Text to Image (AI) (text-to-image) — KHÔNG có DESIGN SETTINGS/POPULATE VALUES, thiếu option 'No personalization', nhãn GenAI service khác Multiple Uploads” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-394"}
```

## OQ-artwork-layer-config-157 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-157","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Text to Image (AI) vs Multiple Uploads — key JSON GenAI provider (text_to_image_provider vs multi_image_provider) chưa xác nhận qua PUT thật” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-395"}
```

## OQ-artwork-layer-config-158 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-158","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-018 “[NEW v3] Clipart Category (single) — full field inventory qua Bulk Edit (DESIGN/PERSONALIZATION/EXTRA)” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-396"}
```

## OQ-artwork-layer-config-159 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-159","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-021 “[NEW v3, NEEDS_CONFIRMATION] 'Select a group of clipart categories' có thực sự hỗ trợ multi-category hay chỉ 1 category nested children?” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-397"}
```

## OQ-artwork-layer-config-160 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-160","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-024 “[NEW v3] Portal canvas render tiếp tục dùng layer.url (KHÔNG dùng layer.default_value) sau Save & Close + mở lại” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-398"}
```

## OQ-artwork-layer-config-161 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-161","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-025 “[NEW v3, NEEDS_CONFIRMATION] Conflict CONF-CTX20260921-03-02 — nhánh PORTAL: lựa chọn tường minh 'default value' của merchant có NÊN ảnh hưởng canvas portal hay không?” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-399"}
```

## OQ-artwork-layer-config-162 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-162","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-026 “[NEW v3, NEEDS_CONFIRMATION] Group's default value combobox hiện 'List is empty.' dù category có 2 item xác nhận tồn tại cùng phiên” của feature layer-config-image. current_behavior_only","supersedes":"OQ-artwork-400"}
```

## OQ-artwork-layer-config-163 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-163","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-027 “[NEW v3, NEEDS_CONFIRMATION] Conflict CONF-API-CTX20260921-03-01 nhánh PORTAL: GET /api/layer-image-categories trả [] rỗng trong khi GraphQL clipart_categories trả 10 rows cùng user/session” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-401"}
```

## OQ-artwork-layer-config-164 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-164","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-028 “[NEW v3, NEEDS_CONFIRMATION] Conflict CONF-CTX20260921-03-01 — field 'Custom class:' (layer-level, Clipart Category›1) có tồn tại thật hay đã mất so với canonical v2?” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-402"}
```

## OQ-artwork-layer-config-165 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-165","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-030 “[NEW v3, NEEDS_CONFIRMATION] API field 'show_clipart_name' (null observed) có đúng backing field cho UI toggle 'Show option name on hover'?” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-403"}
```

## OQ-artwork-layer-config-166 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-166","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-033 “[NEW v4, NEEDS_CONFIRMATION] Thứ tự accordion 'Populate Values đầu tiên' có cố định cho MỌI layer photo, hay chỉ khi Populate Values đã được cấu hình trước?” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-404"}
```

## OQ-artwork-layer-config-167 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-167","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-036 “[NEW v4, NEEDS_CONFIRMATION] Toggle 'Use Template Default Size' (ImagenHub, Multiple Uploads) — tác dụng khi bật ON chưa được test” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-405"}
```

## OQ-artwork-layer-config-168 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-168","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-038 “[NEW v4, NEEDS_CONFIRMATION] Rule 'prompt required' (Save & Close) — chỉ xác nhận với Gemini, chưa test OpenAI/Flux/ImagenHub (cả Multiple Uploads lẫn Text to Image)” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-406"}
```

## OQ-artwork-layer-config-169 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-169","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-041 “[NEW v4, NEEDS_CONFIRMATION] Token '{{input}}' trần có xuất hiện khi Maximum photos=1 (chưa test)?” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-407"}
```

## OQ-artwork-layer-config-170 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-170","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-043 “[NEW v4, NEEDS_CONFIRMATION] Cảnh báo unsupported-provider (Flux, Text to Image) — chỉ thử ở UI cấu hình, chưa thử lúc generate thật” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-408"}
```

## OQ-artwork-layer-config-171 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-171","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-045 “[NEW v4, NEEDS_CONFIRMATION] '+ Variable' picker hiển thị option gì khi artwork CÓ ≥1 layer Text/Additional Option khác?” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-409"}
```

## OQ-artwork-layer-config-172 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-172","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-048 “[NEW v4, NEEDS_CONFIRMATION] Text to Image (AI) có bao giờ được offer làm Populate Content source hay không — chỉ 1 sample phủ định” của feature layer-config-image. current_behavior_only","supersedes":"OQ-artwork-410"}
```

## OQ-artwork-layer-config-173 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-173","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-049 “[NEW v4, NEEDS_CONFIRMATION] Beta badge KHÔNG xuất hiện cho Text to Image (AI) — chỉ xác nhận trên 2 bề mặt staff-authenticated, chưa test storefront PDP/theme thật” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-411"}
```

## OQ-artwork-layer-config-174 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-174","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-050 “[NEW v4, CONFLICTED, CONF-CBS003-01, NEEDS_CONFIRMATION] Verify hiện trạng số lượng/tên lựa chọn Personalization của Text to Image (AI) — KHÔNG chọn 1 phía làm oracle” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-412"}
```

## OQ-artwork-layer-config-175 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-175","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-051 “[NEW v4, NEEDS_CONFIRMATION, GAP] TIB-5188 — thứ tự resize/crop và minimum-resolution validation của pipeline GenAI (Multiple Uploads) HOÀN TOÀN CHƯA TEST” của feature layer-config-image. missing_or_unresolved_oracle","supersedes":"OQ-artwork-413"}
```

## OQ-artwork-layer-config-176 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-176","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-052 “[NEW v4, NEEDS_CONFIRMATION, GAP] TIB-5339 — so sánh sync vs async giữa route upload chính (presigned-S3) và route fallback (multipart) KHÔNG so sánh được” của feature layer-config-image. current_behavior_only","supersedes":"OQ-artwork-414"}
```

## OQ-artwork-layer-config-177 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-177","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-053 “[NEW v4, NEEDS_CONFIRMATION, GAP] 'Duplicate & Share' (TIB-5326) — control không tìm thấy ở portal editor lẫn storefront Live Preview cho Multiple Uploads/Text to Image” của feature layer-config-image. current_behavior_only","supersedes":"OQ-artwork-415"}
```

## OQ-artwork-layer-config-178 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-178","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “Street Maps (maps) — hành vi khi thiếu Mapbox access token (3rd-party Services) chưa xác nhận” của feature layer-config-maps-astronomy. missing_or_unresolved_oracle","supersedes":"OQ-artwork-416"}
```

## OQ-artwork-layer-config-179 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-179","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006 “Moon Phase (moon-phase) — chính tả field code 'maps_seacher_enabled' cần giữ nguyên khi viết assertion, không tự sửa thành 'searcher'” của feature layer-config-maps-astronomy. missing_or_unresolved_oracle","supersedes":"OQ-artwork-417"}
```

## OQ-artwork-layer-config-180 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-180","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-004 “QR Code (qr-code) — hành vi khi nhập vượt quá 4296 ký tự chưa được thử (chặn/cắt/lỗi)” của feature layer-config-others. missing_or_unresolved_oracle","supersedes":"OQ-artwork-418"}
```

## OQ-artwork-layer-config-181 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-181","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-004 “Word Search (word-search) — chuỗi 'Custom class:' xuất hiện HAI LẦN trong panel DOM, chưa xác nhận 2 field riêng hay lỗi duplicate render” của feature layer-config-puzzles. missing_or_unresolved_oracle","supersedes":"OQ-artwork-419"}
```

## OQ-artwork-layer-config-182 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-182","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Single-line Text (text) — tuân theo baseline chung, không có deviation field riêng ghi nhận” của feature layer-config-text. missing_or_unresolved_oracle","supersedes":"OQ-artwork-420"}
```

## OQ-artwork-layer-config-183 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-183","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “Curve Text (curve-text) — tuân theo baseline chung, không có deviation field riêng ghi nhận” của feature layer-config-text. missing_or_unresolved_oracle","supersedes":"OQ-artwork-421"}
```

## OQ-artwork-layer-config-184 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-184","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-005 “Other › Spiral Text (spiral-text) — hành vi khi nhập Inner radius < 20 chưa xác nhận” của feature layer-config-text. missing_or_unresolved_oracle","supersedes":"OQ-artwork-422"}
```

## OQ-artwork-layer-config-185 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-185","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “Paragraph › Normal (paragraph) — key JSON thật của 'Remove line breaks' chưa xác nhận, chưa viết được assertion API” của feature layer-config-text. missing_or_unresolved_oracle","supersedes":"OQ-artwork-423"}
```

## OQ-artwork-layer-config-186 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-186","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Static Vector (static-vector) — theo baseline chung NHƯNG là 1/2 type KHÔNG có field 'Custom class:'” của feature layer-config-vector. missing_or_unresolved_oracle","supersedes":"OQ-artwork-424"}
```

## OQ-artwork-layer-config-187 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-187","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “Static Vector (static-vector) — chưa có per-type DOM dump riêng ngoài việc thiếu Custom class” của feature layer-config-vector. missing_or_unresolved_oracle","supersedes":"OQ-artwork-425"}
```

## OQ-artwork-layer-config-188 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-188","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “[MỚI,, CBS-004] Rate-limit Static Vector (POST /api/layer-images/svg, resource user_rate_limiter:layer_image) — giá trị limit=1000, reset=86400s (24h)” của feature layer-config-vector. missing_or_unresolved_oracle","supersedes":"OQ-artwork-426"}
```

## OQ-artwork-layer-config-189 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-189","type":"NEEDS_CONFIRMATION","feature_id":"vector-layer-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “[MỚI,, CBS-004] Hành vi giảm của x-ratelimit-remaining trên POST /api/layer-images/svg — CONF-CBS004-001 UNRESOLVED, KHÔNG dùng làm oracle” của feature layer-config-vector. missing_or_unresolved_oracle","supersedes":"OQ-artwork-427"}
```

## OQ-artwork-layer-config-190 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-190","type":"NEEDS_CONFIRMATION","feature_id":"condition-cycle-validation","summary":"[CBS-140, KB-983, spec-hub rule conditional-options-no-loops và artwork-editor-layer-checks] Spec-hub ghi condition giữa các layer không được tạo vòng (A phụ thuộc B và B phụ thuộc A), artwork không lưu được tới khi gỡ vòng, và editor kiểm điều này trước khi save. Dev xác nhận đây là hành vi đúng không? Rule không nói server có chặn payload vòng gửi thẳng qua API (OQ-artwork-036) hay self-loop (OQ-artwork-037); nếu server cũng chặn thì Dev nêu rõ.","kb_ids":["KB-983"],"supersedes":"OQ-artwork-451"}
```

## OQ-artwork-layer-config-191 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-191","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","kb_ids":["KB-1006"],"summary":"[CBS-123] KB-1006 (rule QA FACT-004): layer Word Cloud luôn required, buyer không thể để trống. PO xác nhận đây là hành vi đúng đã ship? Thêm: field có hiện dấu bắt buộc và aria-required không, và 'Default words (only for preview)' chỉ dùng cho preview trong editor hay là fallback khi input rỗng (vế này chưa nạp vì chỉ có ghi chú QA không mã rule và test local). Liên quan CHK-009. Cần: PO/Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS kèm căn cứ expected.","supersedes":"OQ-artwork-479"}
```

## OQ-artwork-layer-config-192 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-192","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","kb_ids":["KB-1007"],"summary":"[CBS-123] KB-1007 (rule QA FACT-009): dedupe từ trùng của Word Cloud là case-sensitive và chạy sau transform Text case (Normal giữ Love/love/LOVE là 3 từ; UPPERCASE/lowercase/Capitalize gộp thành 1). Dev xác nhận, kể cả nhánh Capitalize (phân tích yêu cầu còn ghi cần kiểm phía nào của transform áp dụng, chưa có test case riêng)? Liên quan CHK-010.","supersedes":"OQ-artwork-480"}
```

## OQ-artwork-layer-config-193 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-193","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","kb_ids":["KB-1008"],"summary":"[CBS-123] KB-1008 (rule QA FACT-012): Word Cloud có Drop shadow và shadow của origin propagate sang linked copy. Dev xác nhận đã ship? Linked copy có control shadow riêng không (vế này chưa nạp, chỉ có kết quả test local)? KB-031 hiện không liệt kê Drop shadow trong Design settings. Liên quan CHK-011.","supersedes":"OQ-artwork-481"}
```

## OQ-artwork-layer-config-194 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-194","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","kb_ids":[],"summary":"[CBS-123] CLAIM-02 (S0, không nạp KB): bấm 'Regenerate layout' nhiều lần ra layout khác nhau là đúng (mỗi lần bấm seed tăng 1, từ/shape/màu/số từ giữ nguyên, chỉ layout đổi)? Đã ship chưa? Mới thấy qua seed và request render trong test local, chưa so ảnh. Cần: Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS kèm căn cứ expected, hoặc rule QA FACT-005 kèm ngày ghi nhận.","supersedes":"OQ-artwork-482"}
```

## OQ-artwork-layer-config-195 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-195","type":"NEEDS_CONFIRMATION","feature_id":"photo-upload-layer-config","kb_ids":["KB-1024"],"summary":"[CBS-143] KB-1024: layer photo personalization thường không có ảnh mặc định vẫn lưu được trên portal / REST (Dev ghi là giới hạn đã biết, MCP vẫn chặn) — PO có muốn giữ hành vi này không?","supersedes":"OQ-artwork-501"}
```

## OQ-artwork-layer-config-196 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-196","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","kb_ids":["KB-1066","KB-1067"],"check_ids":["CHK-042"],"owner":"Dev","summary":"[CBS-126] Rule QA FACT-042 (KB-1066, PROPOSED): payload GET api/merchant/games/warp_text/<base64>.json có points là mảng phẳng 20 số (10 điểm, x rồi y), toạ độ pixel tuyệt đối trong [0,width]×[0,height] với width = height = 1000, không phải 10 object {x,y} chuẩn hoá 0-1; resize layer không đổi points/width/height. Nguồn là lượt AI đọc payload 2026-09-30/10-01, trước lần giao QA lại TIB-5325. Change note Dev TIB-5325 (KB-1067, 2026-10-09) chỉ nói payload render không đổi và vùng render 1000x1000, không nói dạng points hay ảnh hưởng của resize. Đây có phải hợp đồng API không? CHK-011 chưa có oracle. Cần: Dev xác nhận nguyên văn có ngày.","supersedes":"OQ-artwork-535"}
```

## OQ-artwork-layer-config-197 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-197","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","kb_ids":["KB-1068"],"check_ids":["CHK-043"],"owner":"Dev","summary":"[CBS-126] Rule QA FACT-137 (KB-1068, PROPOSED, đo 2026-09-30 trước khi TIB-5325 re-open): popup Warp cũ có Mirror X (.la-arrows-alt-h) và Mirror Y (.la-arrows-alt-v) là 2 nút icon cạnh nút Free dưới canvas preview, không có chữ 'mirror' trong DOM. Sau TIB-5325, dialog 'Advanced editor' còn hai nút này không, hay đã thay bằng lựa chọn Vertical/Horizontal của Warp mode (change note Dev ghi chế độ dùng chung hai chiều giữa popover và dialog)? Record Testlane TC-TIB-4195 (TC-14) có expected 'Mirror X/Y không có khi kéo trên canvas, chỉ có trong popup' dựa trên giới hạn mà change note Dev nay ghi đã làm xong, có thể cần sửa. CHK-012 chưa có oracle. Cần: Dev xác nhận nguyên văn có ngày.","supersedes":"OQ-artwork-536"}
```

## OQ-artwork-layer-config-198 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-198","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","kb_ids":["KB-1069"],"check_ids":["CHK-044"],"owner":"Dev","summary":"[CBS-126] Rule QA FACT-138 (KB-1069, PROPOSED, AI đo staging 2026-09-30 và TC-34 2026-10-01): bật Mirror X trong popup Warp không tự lật điểm sẵn có; kéo một điểm thì điểm đối xứng nhận x' = 2×centerX − x, và theo cả hai lượt đo y của điểm đối xứng bằng y của điểm vừa kéo (point[4] y 400→458.70 theo point[0]; lượt 2 y = 436.5782). Câu chữ 'y giữ nguyên' trong rule và 'không đổi theo điểm vừa kéo' trong expected record Testlane TC-TIB-4215 lệch với số đo; không có quan sát nào cho y đứng yên nên không mở CONFLICT. Dev: khi mirror theo trục dọc (Mirror X cũ hoặc Warp mode Vertical), điểm đối xứng có nhận x' = 2×centerX − x và y bằng đúng y điểm vừa kéo không, và bật mirror có tự lật điểm đã có không? Nếu đúng, expected của TC-TIB-4215 cần sửa câu chữ. CHK-013 chưa có oracle. Cần: Dev xác nhận nguyên văn có ngày.","supersedes":"OQ-artwork-537"}
```

## OQ-artwork-layer-config-199 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-199","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","kb_ids":["KB-1096"],"check_ids":["CHK-030"],"owner":"Dev","summary":"[CBS-149] Sau TIB-5699, layer Text và Paragraph có 2 lớp stroke vẫn render đủ 2 vòng trong PNG và SVG, và sau đổi text + Save + mở lại vẫn hiện 2 lớp, PUT gửi 2 entry stroke_layers — có phải expected không? KB-1096 là quan sát test case TC-TIB-8986 (staging 2026-11-10, không ghi build); CCR chỉ nêu tên căn cứ expected (TIB-5699 comment 56557 U3/Q4, QA plan 56595 bước D7), không trích nguyên văn. CHK-030 oracle BASELINE. Cần: Dev xác nhận kèm trích nguyên văn, hoặc test case PASS có build.","supersedes":"OQ-artwork-559"}
```

## OQ-artwork-layer-config-200 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-200","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","kb_ids":["KB-1097"],"check_ids":["CHK-031"],"owner":"Dev","summary":"[CBS-149] Đổi stroke của layer curve text nhiều lần (tăng, giảm width, đổi màu), Save và render lại sau mỗi lần thì PNG luôn theo stroke mới nhất của editor, không quay về giá trị cũ — có phải expected không, và có áp cho spiral / shape / warp text và SVG không? KB-1097 là quan sát test case TC-TIB-8982 (staging 2026-11-10, không ghi build); câu tương ứng trong QA plan của Dev (56595 bước A2) không được trích trong CCR. CHK-031 oracle BASELINE.","supersedes":"OQ-artwork-560"}
```

## OQ-artwork-layer-config-201 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-201","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","kb_ids":["KB-1094","KB-1095","KB-1096","KB-1097"],"check_ids":[],"owner":"QA","summary":"[CBS-149] Trên production, ảnh render PNG và preview của curve / spiral / shape / warp text sau TIB-5699 có khớp stroke editor khi người xem duyệt không? Production 2026-11-11 chỉ phần kiểm bằng máy pass (dữ liệu lưu không còn stroke_layers, SVG đúng màu/độ dày); phần duyệt ảnh NOT-RUN ở mức task, regression thiếu fixture production. KB-1096, KB-1097 và vế convert của KB-1095 chỉ chạy staging; linked copy (layer-duplicate-link-copy KB-1098) cũng chỉ chạy staging.","supersedes":"OQ-artwork-561"}
```

## OQ-artwork-layer-config-202 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-202","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","kb_ids":["KB-1094"],"check_ids":[],"owner":"Dev","summary":"[CBS-149] Ngoài claim (ghi chú trong CCR, quan sát staging): spiral text trên SVG design với width 5 cho stroke-width=\"3\", trong khi các loại khác stroke-width = width × 0.875 — đây là hành vi đúng hay lệch? Chưa có trả lời của Dev, không nạp KB.","supersedes":"OQ-artwork-562"}
```

## OQ-artwork-layer-config-203 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-203","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","kb_ids":["KB-1094","KB-1095"],"check_ids":[],"owner":"Dev","summary":"[CBS-149] Layer curve / spiral / shape / warp text đã giữ sẵn stroke_layers cũ (tình huống gốc của TIB-5699) có render theo cặp và bị xoá list khi save lại không? Dev ghi \"Not for QA (covered by unit tests)\" và dặn không sửa data bằng tay; QA chưa có fixture để verify. Checklist hiện chỉ kiểm layer mới đặt stroke.","supersedes":"OQ-artwork-563"}
```

## OQ-artwork-layer-config-204 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-204","type":"NEEDS_CONFIRMATION","feature_id":"text-layer-config","kb_ids":["KB-1094"],"check_ids":[],"owner":"Dev","summary":"[CBS-149] Warp text bật stroke mà stroke_width rỗng hoặc 0: preview SDK không vẽ stroke, còn render api vẽ width mặc định 1. Dev tự nêu ở mục Open questions của TIB-5699 comment 56557 (2026-11-05): hành vi có từ trước, bản sửa giữ nguyên, hỏi có tách ticket riêng không. Đây là lệch chấp nhận hay bug cần ticket? Vế 'design khớp preview' của KB-1094 không áp cho trường hợp này; CHK-028 đặt width khác mặc định.","supersedes":"OQ-artwork-567"}
```

## OQ-artwork-layer-config-205 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-205","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"[CBS-106, TIB-5609] 'Display in date format' của layer Star Map (KB-1105, OBSERVED_CURRENT/LOW): danh sách 7 preset dạng 24h HH:mm không giây (MM/DD/YYYY, DD/MM/YYYY, DD-MM-YY, YYYY-MM-DD, YYYY/MM/DD, DD.MM.YYYY, MM.DD.YYYY) + Custom, field lưu star_maps_date_format / star_maps_custom_date_format, key custom vắng trong body Save khi chọn preset — có đúng ý PO/Dev không, PO có chấp nhận preset 24h không? Setting chỉ có ở Artwork 2.0 (Artwork 1.0, Global Option Star Maps chưa kiểm)?","kb_ids":["KB-1105"],"needs":"PO xác nhận danh sách preset; Dev xác nhận tên field và phạm vi Artwork 2.0 / Global Option, kèm nguyên văn có ngày.","supersedes":"OQ-artwork-571"}
```

## OQ-artwork-layer-config-206 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-206","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"[CBS-106, TIB-5609] Ô giờ Star Map trên storefront (KB-1107, OBSERVED_CURRENT/LOW): ô hiện theo format đã chọn (kể cả Custom 12h AM/PM) còn giá trị lưu trong customization/localStorage vẫn dạng máy yyyy-MM-ddTHH:mm — Dev xác nhận? SDK v1 có giống SDK v2 không (chưa kiểm vì thiếu store SDK v1; record Testlane TC-TIB-8819 ghi passed nhưng actual là blocked)?","kb_ids":["KB-1107"],"needs":"Dev xác nhận nguyên văn có ngày; một lượt chạy trên store SDK v1 có ghi build.","supersedes":"OQ-artwork-572"}
```

## OQ-artwork-layer-config-207 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-207","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"[CBS-106, TIB-5609] Khi store tắt UI date picker của Teeinblue (picker native), text layer populate {{time}} từ Star Map vẫn in theo 'Display in date format' của Star Map (KB-1111, quan sát TC-TIB-8812). Câu Scope của TIB-5609 ('applies to Teeinblue's own date picker only', KB-1110) chỉ nói ô hiển thị hay cả populate? Expected của {{time}} khi dùng picker native là gì?","kb_ids":["KB-1111","KB-1110"],"needs":"PO/Dev trả lời nguyên văn có ngày.","supersedes":"OQ-artwork-573"}
```

## OQ-artwork-layer-config-208 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-layer-config-208","type":"NEEDS_CONFIRMATION","feature_id":"special-layer-config","summary":"[CBS-106, TIB-5609] Star Map không vẽ ngày lên design (KB-1112, theo TIB-5609): lượt chạy TC-TIB-8816 chỉ kiểm print area front của design order; print area khác (back) và mockup chưa kiểm.","kb_ids":["KB-1112"],"needs":"Lượt chạy design order có Star Map ở print area khác, ghi build.","supersedes":"OQ-artwork-575"}
```
