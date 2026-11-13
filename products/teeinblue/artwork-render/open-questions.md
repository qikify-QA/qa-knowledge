# Open Questions — artwork-render

## OQ-artwork-render-001 — CONFLICT

```json
{"oq_id":"OQ-artwork-render-001","type":"CONFLICT","feature_id":"print-design-render","summary":"An assumption that Print Effects includes an emboss capability (gated by a 3rd-party service) could not be confirmed on the tested account/plan; absence was not proven either.","side_a":"Assumption going into the run: Print Effects (formerly 'Shape Cut') now also includes an emboss effect that depends on a 3rd-party service.","side_b":"Direct observation on 4 layer types plus the Extras > 3rd-party Services page: the Print Effects popover only ever shows shape-cut layout options; no mention of 'emboss' or '3rd-party' found anywhere on those surfaces.","supersedes":"OQ-artwork-004"}
```

## OQ-artwork-render-002 — CONFLICT

```json
{"oq_id":"OQ-artwork-render-002","type":"CONFLICT","feature_id":"storefront-clipart-selection","summary":"Three-way disagreement on what actually drives the final rendered image for a Clipart Category layer: portal canvas, storefront pre-check, and the final compositing output each point to a different (or no) source.","side_a":"In the portal editor, layer.url (set when picking an image via the 'Upload an image' tab at add-layer time) drives what renders on the canvas, both immediately and after Save & Close + reopen.","side_b":"On the storefront personalization form, layer.default_value (set via the category default-value picker) is what gets pre-checked in the buyer-facing radiogroup on first load — layer.url is not even a selectable option there.","side_c":"Neither layer.url, nor layer.default_value, nor the buyer's own explicit selection ever appears in the final compositing output (Preview modal or cart customization image) — see KB-112 (CRITICAL).","supersedes":"OQ-artwork-009"}
```

## OQ-artwork-render-003 — CONFLICT

```json
{"oq_id":"OQ-artwork-render-003","type":"CONFLICT","feature_id":"storefront-clipart-selection","summary":"Two API surfaces disagree on the clipart category list for the same user/session: REST returns an empty list, GraphQL returns 10 rows.","side_a":"GET /api/layer-image-categories?type=clipart returns 200 with an empty array.","side_b":"A GraphQL query for clipart_categories, run for the same user in the same time window, returns 200 with 10 rows.","supersedes":"OQ-artwork-010"}
```

## OQ-artwork-render-004 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-004","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"<select> chỉ có 1 option placeholder disabled 'Choose a design', 0 item selectable, dù category có 2 item xác nhận tồn tại server-side (no1, no2). correlation_note PLAUSIBLE (không CONFIRMED) cùng root cause với CONF-API-CTX20260921-03-01 (xem CHK-020, layer api) và KB-013 (layer-config-image.json CHK-026, layer portal) — 3 bề mặt riêng biệt, KHÔNG gộp thành 1 statement. Cần db-explorer/api-explorer follow-up trước khi báo bug chính thức.","supersedes":"OQ-artwork-027"}
```

## OQ-artwork-render-005 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-005","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Server thêm key 'artwork-4339': 11533 (numeric) vào response mà client localStorage KHÔNG hề có tại thời điểm ghi trước đó — mục đích field này CHƯA xác định. Có thể là ID nội bộ quan trọng cho fulfillment/print — cần dev xác nhận trước khi coi absence trong client write là bình thường/vô hại.","supersedes":"OQ-artwork-028"}
```

## OQ-artwork-render-006 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-006","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Giả thuyết CHƯA XÁC NHẬN: '_large' có thể bị giới hạn (capped) bởi độ phân giải gốc file upload gốc, không upscale vượt quá — độ phân giải gốc no1.png/no2.png KHÔNG được verify độc lập trong run (INFERRED). Nếu giả thuyết sai, nghĩa là Preview size setting (500px) đang KHÔNG hoạt động đúng bất kể ảnh gốc, cần điều tra thêm như 1 defect riêng.","supersedes":"OQ-artwork-029"}
```

## OQ-artwork-render-007 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-007","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Đây là defect sản phẩm đã xác nhận (canvas/preview/cart PHẢI composite clipart đã chọn — nếu đúng, hiện tại đang FAIL nghiêm trọng) hay là artifact của test fixture (artwork:4339 layer sai z-order/position/opacity trên canvas 1600x1600, không phản ánh sản phẩm thật)? Cần: (1) PO/Dev xác nhận business rule mong đợi cho compositing; (2) re-test trên artwork/campaign MỚI (fixture cũ đã ARCHIVED/DELETED) để loại trừ nguyên nhân do fixture; (3) cross-check api-explorer/db-explorer. correlation_note: PLAUSIBLE (KHÔNG CONFIRMED) cùng root cause dữ liệu category/artwork test với CONF-API-CTX20260921-03-01 (CHK-003/CHK-020) và anomaly group default-value (layer-config-image.json CHK-026) do cùng category/artwork test — KHÔNG coi là đã xác nhận cùng nguyên nhân.","supersedes":"OQ-artwork-030"}
```

## OQ-artwork-render-008 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-008","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"3-way conflict CONF-CTX20260921-03-02 — SUB-SCOPE WIDGET (khác sub-scope compositing ở CHK-017): quan sát cho thấy layer.default_value ('no2') là giá trị PRE-CHECK trên storefront personalization RADIOGROUP lúc load đầu tiên; 'cat1' (url-pick) THẬM CHÍ KHÔNG PHẢI 1 option chọn được vì không phải item của category. Đây có đúng là business rule dự kiến (default_value luôn là nguồn pre-check hợp lệ duy nhất cho storefront, url chỉ dùng nội bộ portal) hay là 1 gap khác cần điều tra? Cần PO/Dev xác nhận. KHÔNG gộp kết luận với CHK-017 (sub-scope compositing) hay layer-config-image.json CHK-024/025 (sub-scope portal canvas) — 3 sub-scope riêng biệt của cùng 1 conflict.","supersedes":"OQ-artwork-031"}
```

## OQ-artwork-render-009 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-009","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Chưa có evidence nào cho role/market/viewport khác — check này tồn tại để đóng coverage gap đã biết (PERMISSION/device dimension), KHÔNG dựa trên observation cụ thể nào. Cần storefront-explorer chạy thêm trước khi có thể chuyển sang READY.","supersedes":"OQ-artwork-032"}
```

## OQ-artwork-render-010 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-010","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"GET /api/layer-image-categories?type=clipart trả 200, body [] (rỗng); POST /api/graphql clipart_categories(where: {type: clipart, deleted_at: null, parent id: null}, limit: 25) trả 200, 10 rows, CÙNG user/session, CÙNG khoảng thời gian. Root cause CHƯA chẩn đoán (filter khác nhau trên endpoint REST vs GraphQL, hay data/cache issue riêng ở staging). Cần db-explorer/api-explorer follow-up trước khi coi là defect xác nhận. Hệ quả buyer-facing trực tiếp là <select> group-type storefront rỗng 0 item selectable (CHK-003). Correlation PLAUSIBLE (không CONFIRMED) với KB-013 (layer-config-image.json CHK-026, portal).","supersedes":"OQ-artwork-033"}
```

## OQ-artwork-render-011 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-011","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Conflict CONF-CTX20260921-03-01 không có nhánh buyer-facing/storefront — liệt kê ở đây CHỈ để tracking đầy đủ 3 conflict của run trong checklist của feature này, KHÔNG lặp lại narrative. Xem layer-config-image.json (FEAT-13, owner chính) CHK-028 cho nội dung đầy đủ.","supersedes":"OQ-artwork-034"}
```

## OQ-artwork-render-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-012","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"'Show option to select default value' OFF có ẩn/hiện gì khác trên personalization form storefront so với ON hay không — chỉ test ở trạng thái ON trong run này. Chưa đủ để viết checklist cho cấu hình OFF, có thể bỏ sót 1 nhánh hành vi hoàn toàn khác trên storefront. Check này tồn tại để đóng coverage gap, KHÔNG dựa trên observation cụ thể.","supersedes":"OQ-artwork-035"}
```

## OQ-artwork-render-013 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-013","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"CONF-004 UNRESOLVED: brief giả định Print Effects đã có emboss phụ thuộc dịch vụ 3rd-party; quan sát thực tế trên 4/35 layer type + trang 3rd-party Services (plan Blue Test) không tìm thấy chuỗi 'emboss'/'3rd-party' ở đâu. KHÔNG kết luận emboss không tồn tại — có thể gate theo plan, layer type khác chưa thử, hoặc cấu hình 3rd-party service chưa bật. Cần dev/PO xác nhận.","supersedes":"OQ-artwork-084"}
```

## OQ-artwork-render-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-014","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Chưa đối chiếu Print Effects với KB-020/KB-022 — chỉ có oracle UI (popover), chưa có oracle ở tầng API cho tính năng này.","supersedes":"OQ-artwork-085"}
```

## OQ-artwork-render-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-015","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"'Order Design' hoàn toàn chưa được khám phá trong 3 run nguồn — chỉ biết qua nội dung footnote, chưa xác nhận luồng production guide thật sự hoạt động ra sao.","supersedes":"OQ-artwork-086"}
```

## OQ-artwork-render-016 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-016","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Chỉ 1 sample quan sát (observed_count=1) — chưa xác nhận 13 nhóm này có tương ứng 1-1 đầy đủ với mọi layer/output type hay còn nhóm khác chưa liệt kê.","supersedes":"OQ-artwork-087"}
```

## OQ-artwork-render-017 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-017","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"11 template biến đổi giá trị được liệt kê tên nhưng cú pháp thật sự hỗ trợ biểu thức/range gì của formula/context chưa từng được test với input cụ thể. Bổ sung CBS-110 (2026-11-11): rule QA FACT-022/FACT-024 (S2, KB-987, KB-988, KB-991) ghi kết quả của token context/formula sai, không hoàn chỉnh và hằng số năm 365.2425, chưa PO/Dev xác nhận (OQ-artwork-455, OQ-artwork-456, OQ-artwork-459); cú pháp hỗ trợ đầy đủ vẫn chưa có nguồn nên câu hỏi vẫn mở.","supersedes":"OQ-artwork-088"}
```

## OQ-artwork-render-018 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-018","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Chỉ test 2 channel Font và Color — chưa rõ cơ chế khoá theo Google Font có áp dụng cho Background/Shape hay là đặc thù riêng của Font.","supersedes":"OQ-artwork-089"}
```

## OQ-artwork-render-019 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-019","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"0 evidence storefront cho Font/Color/Word Cloud/dynamic-by-text — đây là feature có mức độ 'chưa test nơi giá trị thực sự được dùng' cao nhất trong toàn bộ checklist (dù nay đã có 1 luồng khác — Multiple Uploads→Photo — có evidence storefront MỘT PHẦN, xem CHK-022).","supersedes":"OQ-artwork-090"}
```

## OQ-artwork-render-020 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-020","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"CHK-019 chỉ test Maximum photos=3 (thấy token indexed {{input.1..3}}) — chưa test Maximum photos=1, không rõ token có đổi thành dạng trần '{{input}}' hay vẫn giữ '{{input.1}}'. Ảnh hưởng thiết kế test case populate content khi Multiple Uploads chỉ cho phép 1 ảnh.","supersedes":"OQ-artwork-091"}
```

## OQ-artwork-render-021 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-021","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Trong session cấu hình artwork 4416, Source option dropdown của Populate Content trên layer đích 'body' CHỈ liệt kê layer Multiple Uploads ('top'); layer Text to Image (AI) ('hair') KHÔNG xuất hiện. Quan sát 1 lần duy nhất trong 1 cấu hình cụ thể — KHÔNG kết luận Text-to-Image không bao giờ được offer làm nguồn populate; cần re-test ở cấu hình/thời điểm khác trước khi viết assertion chính thức (dù là assertion phủ định).","supersedes":"OQ-artwork-092"}
```

## OQ-artwork-render-022 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-022","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"KB-008 (CHK-022) CHỈ xác nhận nửa 'giá trị gốc lan truyền ngay, không chờ Generate của layer nguồn'. Nửa còn lại (layer đích tự động trigger effect chain riêng của nó lên giá trị được populate, mô tả liên quan TIB-5302) KHÔNG xác nhận được trong run này vì layer 'body' của fixture không có effect nào cấu hình. KHÔNG suy diễn cơ chế effect tự trigger là đúng dù có TIB-5302 làm nguồn gợi ý (Jira KHÔNG phải authority theo §12.4 rule 2 của contract). Nếu sai giả định, test case cho layer đích CÓ effect cấu hình sẵn sẽ thiếu coverage quan trọng.","supersedes":"OQ-artwork-093"}
```

## OQ-artwork-render-023 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-023","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Phần storefront của KB-008 (CHK-022) quan sát qua Live Preview widget với vai trò staff-authenticated PROXY cho buyer (account explorer (TIB_STAGING_EMAIL)), KHÔNG PHẢI guest session thật. KHÔNG dùng làm bằng chứng hành vi buyer thật 100% (vd cross-tenant, rate-limit, hoặc UI khác biệt trên theme Shopify thật chưa loại trừ) tới khi có evidence guest thật.","supersedes":"OQ-artwork-094"}
```

## OQ-artwork-render-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-024","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Hành vi đúng (PO/business) của render text rainbow trên Locate Artwork và Order Design PNG — căn phải/giữa/trái, độ rộng bằng text 1 màu, autoscale tên dài, letter spacing, kerning — có đúng như đang quan sát (khớp preview SDK) không? Hiện chỉ là quan sát một lượt chạy trên staging, chưa ai xác nhận; checklist không có oracle cho các nhánh này.","kb_ids":["KB-146","KB-147","KB-148","KB-149","KB-151","KB-152"],"supersedes":"OQ-artwork-122"}
```

## OQ-artwork-render-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-025","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Text font thường (Roboto) và text 1 màu trên Order Design PNG có thật khớp preview SDK không, khi đo lại có số đo và fixture? Chỉ có tóm tắt kết quả, không có actualResult chi tiết; muốn làm baseline cho nhánh không rainbow cần chạy lại có số đo.","kb_ids":["KB-150"],"supersedes":"OQ-artwork-123"}
```

## OQ-artwork-render-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-026","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Stroke 1 lớp liền mạch ở chỗ nối chữ và text RTL giữ màu từng chữ theo thứ tự preview SDK có phải hành vi đúng không? Quan sát một lượt trên staging (stroke đánh giá bằng mắt, RTL chỉ font Heebo), chưa có PO/business xác nhận.","kb_ids":["KB-153","KB-155"],"supersedes":"OQ-artwork-124"}
```

## OQ-artwork-render-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-027","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Với text rainbow mang multi-stroke, Order Design PNG đúng ra phải thế nào — stroke liền mạch ở chỗ nối chữ như preview SDK? PNG hiện có sợi màu chữ đè lên stroke (BUG-363); không có expected được xác nhận thì không viết được check pass/fail cho nhánh này.","kb_ids":["KB-154"],"supersedes":"OQ-artwork-125"}
```

## OQ-artwork-render-028 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-028","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"BUG-363 (sợi màu chữ đè stroke ở chỗ nối, rainbow + multi-stroke) có từ trước bản fix TIB-5606 hay do bản fix gây ra? Một nguồn ngoài (TC-TIB-4045, verified 2026-10-01) ghi rainbow + multi-stroke render đúng 3 vành, màu từng chữ giữ nguyên — khác build/font với lượt chạy 2026-10-22. Nếu bản fix gây ra, đây là regression của multi-stroke.","kb_ids":["KB-154"],"supersedes":"OQ-artwork-126"}
```

## OQ-artwork-render-029 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-029","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Curve Text rainbow ở căn phải render thế nào, Curve Text trước bản fix có lỗi không, và bản fix có áp dụng cho Curve Text không? Chỉ chạy được căn giữa vì Curve Text không có tuỳ chọn căn lề (FEAT-12, KB-157); phạm vi bản fix cho Curve Text chưa được PO xác nhận.","kb_ids":["KB-156"],"supersedes":"OQ-artwork-127"}
```

## OQ-artwork-render-030 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-030","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Text rainbow dùng font Carattere (font của case báo lỗi gốc) render thế nào trên Locate Artwork và Order Design PNG? Staging không có font này; mọi quan sát dùng font thay thế, nên case gốc chưa được tái hiện hay kiểm sau bản fix.","kb_ids":["KB-146","KB-154"],"supersedes":"OQ-artwork-128"}
```

## OQ-artwork-render-031 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-031","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Hành vi render text rainbow trên production sau khi TIB-5606 ship có giống quan sát trên staging không? TIB-5606 chưa ship; mọi item chỉ đúng cho build staging 2026-10-22 (build hash không rõ).","kb_ids":["KB-146","KB-154","KB-156"],"supersedes":"OQ-artwork-129"}
```

## OQ-artwork-render-032 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-032","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Trước bản fix, text rainbow căn trái, text font thường và text 1 màu render thế nào — kết quả hiện tại có 'không đổi so với trước' không? Staging đã có bản fix khi chạy, không có baseline trước deploy; không phân biệt được hành vi mới và hành vi cũ.","kb_ids":["KB-147","KB-150"],"supersedes":"OQ-artwork-130"}
```

## OQ-artwork-render-033 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-033","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Design đã render trước khi deploy bản fix, khi Re-generate design cho order cũ, có đổi (cỡ chữ, vị trí) so với bản đã in không? Merchant regenerate order cũ có thể nhận ảnh khác bản đã in; trường hợp này chưa kiểm được vì không có order cũ.","kb_ids":["KB-149"],"supersedes":"OQ-artwork-131"}
```

## OQ-artwork-render-034 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-034","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Nhánh font fallback của PNG renderer (ký tự không có trong font, emoji) với text rainbow hoạt động thế nào? Nhánh này chưa có quan sát nào tới được renderer; nếu fallback vẫn đo theo cách cũ, lỗi tràn/mất chữ có thể còn ở nhánh này. Lượt test staging 2026-10-22 không tới được nhánh này: ô nhập storefront bỏ emoji ngay lúc gõ (khớp ghi nhận emoji bị chặn mặc định), nên cần ký tự fallback lọt qua ô nhập (vd bật cho phép emoji) để kiểm.","kb_ids":[],"supersedes":"OQ-artwork-132"}
```

## OQ-artwork-render-035 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-035","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"SVG/vector export (vectorize) của text rainbow có cùng hành vi căn lề và độ rộng như Order Design PNG không? Chưa tải được file vector nào để kiểm; không biết renderer SVG có cùng lỗi gốc hay đã được sửa.","kb_ids":[],"supersedes":"OQ-artwork-133"}
```

## OQ-artwork-render-036 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-036","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Ngoài Locate Artwork và Order Design PNG, những ảnh nào khác (thumbnail, mockup render phía server, ảnh product) có render text rainbow và có bị lỗi gốc ảnh hưởng không? Phạm vi ảnh bị ảnh hưởng chưa được xác nhận bằng quan sát hay nguồn thẩm quyền; checklist có thể bỏ sót surface.","kb_ids":[],"supersedes":"OQ-artwork-134"}
```

## OQ-artwork-render-037 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-037","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Warp Text dùng Color Sequence và sequence màu do buyer chọn (Populate Color) render thế nào trên ảnh in? Hai tổ hợp này chưa được kiểm; chưa biết bản fix có bao phủ không.","kb_ids":[],"supersedes":"OQ-artwork-135"}
```

## OQ-artwork-render-038 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-038","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"PO: ngưỡng thời gian chấp nhận cho generate order design của artwork có Group nhiều layer (~250) là bao nhiêu? Số đo hiện có (khoảng 33–68 giây) chỉ đo 1 lần mỗi fixture qua mốc thời gian Item Activity logs, không có baseline trước fix; ngưỡng 1–2 phút chưa được PO xác nhận. Không dùng số đo này làm SLA hay điều kiện pass/fail cho tới khi PO trả lời. Ngoài ra: order item hiển thị Ready/'Ready to fulfill' sau khi order design generate xong (chỉ thấy ở actualResult của TC-TIB-7614/7616, expectedResult không khẳng định) — có phải hành vi mong đợi không?","kb_ids":["KB-381"],"supersedes":"OQ-artwork-165"}
```

## OQ-artwork-render-039 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-039","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Dev/PO: phần shadow của layer con vượt ra ngoài printarea bị cắt theo printarea trên order design — có phải hành vi mong đợi không? Chỉ thấy ở actualResult của TC-TIB-7617; expectedResult của case không khẳng định điều này.","kb_ids":["KB-384"],"supersedes":"OQ-artwork-166"}
```

## OQ-artwork-render-040 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-040","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Hướng/vị trí shadow của layer con trong Group trên order design sau fix chưa được đối chiếu với bản trước fix (TC-TIB-7620 kiểm bằng mắt, offset của fixture khác test data). PO xác nhận hướng/vị trí shadow hiện thấy trên order design có phải ý định cho merchant và nhà in không; dev/QA đối chiếu toạ độ/pixel với bản trước fix.","kb_ids":["KB-385"],"supersedes":"OQ-artwork-167"}
```

## OQ-artwork-render-041 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-041","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Dev/PO: text căn giữa khai báo cỡ 601 chỉ render cao khoảng 22px trên order design (có vẻ co theo box) — đúng hay lỗi? Text có thực sự tràn box của Group không; đường canvas mở rộng cho text tràn box chưa được chứng minh (TC-TIB-7619).","kb_ids":["KB-386"],"supersedes":"OQ-artwork-168"}
```

## OQ-artwork-render-042 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-042","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Dev: ngưỡng route-large 150 Mpx đo trên canvas artwork hay trên printarea? Route-large (hàng đợi final-render-large) chưa được kích hoạt trong lượt chạy (printarea 72 Mpx) — cần fixture có printarea đủ lớn để kiểm.","kb_ids":["KB-390"],"supersedes":"OQ-artwork-169"}
```

## OQ-artwork-render-043 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-043","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Chạy lại sau merge và trên production: lượt chạy test 2026-10-29 trên staging (build hash không rõ) diễn ra trước khi PR thứ hai của TIB-5633 cập nhật lần cuối 2026-10-30; ngày deploy production chưa rõ. Cần chạy lại bộ TIB-268 trên build đã merge và xác nhận trên production trước khi coi các item CONFIRMED của feature này là ổn định.","kb_ids":["KB-380","KB-381","KB-382","KB-383","KB-384","KB-385","KB-386","KB-387","KB-388","KB-389","KB-390"],"supersedes":"OQ-artwork-170"}
```

## OQ-artwork-render-044 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-044","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Phạm vi render order design của Group nhiều layer chưa được kiểm: mask hình tròn/custom shape; order design PDF của Group có mask; Group khoảng 250 layer có layer tràn box (đường canvas mở rộng); layer chia ở 2 cấp Group (100 + 150); Group cha bị ẩn hoặc visibility theo điều kiện trong Group nhiều layer. Chưa có expected cho các nhánh này.","kb_ids":["KB-383","KB-386","KB-387","KB-388","KB-389"],"supersedes":"OQ-artwork-171"}
```

## OQ-artwork-render-045 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-045","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Blend mode của layer con, layer gắn tag Context trong Group, và Artwork 1.0 chưa có quan sát nào cho render order design của Group nhiều layer (case liên quan bị bỏ qua, nguồn chưa đủ thẩm quyền). Hành vi mong đợi là gì và ai xác nhận?","kb_ids":[],"supersedes":"OQ-artwork-172"}
```

## OQ-artwork-render-046 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-046","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"PO xác nhận đây là hành vi đúng cho merchant và nhà in: order design của artwork có Group khoảng 250 layer generate hoàn tất (design Completed, không auto-stop/timeout, không kẹt Generating); print file của Group giống pixel bản không group; shadow/layer xoay tràn box hiện đủ trong vùng in; Group có mask chỉ hiện phần trong mask; Group lồng nhau không lệch layer; layer con tắt visible không xuất hiện. Các item này đến từ test case PASS trên staging, chưa có PO/business xác nhận ý định.","kb_ids":["KB-380","KB-382","KB-383","KB-387","KB-388","KB-389"],"supersedes":"OQ-artwork-173"}
```

## OQ-artwork-render-047 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-047","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Dev/PO: photo_border contour cut trên print file của Group có đi qua cùng đường xử lý với preset shape-cut của Print Effects (KB-044) không, và đường cắt đang thấy có phải ý định không? Group shape-cut khoảng 250 layer chưa được kiểm — fixture chỉ là Group 3 layer photo_border contour cut.","kb_ids":["KB-391","KB-044"],"supersedes":"OQ-artwork-174"}
```

## OQ-artwork-render-048 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-048","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Emboss áp cho Group nhiều layer chưa từng được chạy (case bị bỏ qua, nguồn chưa đủ thẩm quyền). Print file emboss của Group nên ra sao? Không suy ra gì về việc emboss có hay không trên account/plan hiện tại.","kb_ids":[],"supersedes":"OQ-artwork-175"}
```

## OQ-artwork-render-049 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-049","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Chạy lại sau merge và trên production cho print file photo_border contour cut của Group (lượt chạy 2026-10-29 trước khi PR thứ hai của TIB-5633 cập nhật lần cuối; ngày deploy production chưa rõ).","kb_ids":["KB-391"],"supersedes":"OQ-artwork-176"}
```

## OQ-artwork-render-050 — CONFLICT

```json
{"oq_id":"OQ-artwork-render-050","type":"CONFLICT","feature_id":"print-design-render","conflict_group":"CONF-CBS-016-01","summary":"Text rainbow 32 ký tự bật autoscale, căn phải (staging, lượt chạy 2026-10-22): kết luận của kết quả test và số đo của chính lượt đó không khớp nhau về độ rộng Order Design PNG so với preview SDK. Độ rộng PNG sau autoscale so với preview SDK được kỳ vọng thế nào, dung sai chấp nhận là bao nhiêu? Hai item KB-149 và KB-404 đang UNRESOLVED, không bên nào là oracle. Quyết định này đi cùng quyết định của PO cho cặp KB-149 trong OQ-artwork-182.","side_a":{"kb_id":"KB-149","value":"Kết luận của kết quả test: Order Design PNG sau autoscale chênh 2px, không nhỏ hơn preview SDK."},"side_b":{"kb_id":"KB-404","value":"Số đo của cùng lượt chạy: PNG 495–910 (w=415), preview SDK 493–910 (w=417) — PNG hẹp hơn SDK 2px."},"kb_ids":["KB-149","KB-404"],"supersedes":"OQ-artwork-177"}
```

## OQ-artwork-render-051 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-051","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Số đo một lượt chạy: rainbow font Roboto căn phải PNG 560–905 so với preview SDK 558–904 (lệch 1–2px); text 1 màu font script PNG 624–912 so với SDK 624–913. Lệch 1–2px này có nằm trong dung sai chấp nhận và có lặp lại trên build sau merge / production không?","kb_ids":["KB-406"],"supersedes":"OQ-artwork-178"}
```

## OQ-artwork-render-052 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-052","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Theo mô tả dev (comment #55257, PR #4044), đoạn text dùng font fallback giữ cách đặt vị trí cũ của PNG renderer. Trên build đã merge, text rainbow có ký tự rơi vào font fallback render ra sao (đủ ký tự? khớp preview SDK?), và đây có phải hành vi mong muốn không?","kb_ids":["KB-412"],"supersedes":"OQ-artwork-179"}
```

## OQ-artwork-render-053 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-053","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Theo mô tả dev, preview / order design render trước khi deploy bản sửa TIB-5606 không tự cập nhật và phải regenerate. Đã kiểm trên staging/production chưa, và regenerate cho kết quả đúng (đủ ký tự, vị trí khớp preview SDK) không?","kb_ids":["KB-413"],"supersedes":"OQ-artwork-180"}
```

## OQ-artwork-render-054 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-054","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Theo mô tả dev, chỉ PNG renderer đổi; SVG renderer teeinblue-vectorize không bị ảnh hưởng và cho cùng hình glyph như text 1 màu. QA chưa tải được file vector trên staging — SVG của text rainbow căn phải có thật đủ ký tự, khớp preview SDK không?","kb_ids":["KB-414"],"supersedes":"OQ-artwork-181"}
```

## OQ-artwork-render-055 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-055","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"PO quyết: các test case Testlane TIB-230 PASS trên staging (chạy 2026-10-22, trước khi PR teeinblue-api #4044 merge) khẳng định cùng hành vi với 10 item quan sát KB-146, KB-147, KB-148, KB-149, KB-150, KB-151, KB-152, KB-153, KB-155, KB-156 (rainbow căn phải/giữa/trái, độ rộng bằng text 1 màu, autoscale tên dài, Roboto và text 1 màu, letter spacing, kerning, stroke 1 lớp, RTL, Curve căn giữa). teeinblue không bật supersede nên các item vẫn là OBSERVED_CURRENT/LOW và các check liên quan chưa có expected xác nhận. PO chọn: (a) nâng các hành vi này thành expected, (b) giữ là quan sát, hay (c) giữ cả hai như hai thời điểm? Riêng KB-149: test case không xác nhận vế độ rộng autoscale so với preview SDK, nên quyết định cho KB-149 phải đi cùng OQ-artwork-177.","kb_ids":["KB-146","KB-147","KB-148","KB-149","KB-150","KB-151","KB-152","KB-153","KB-155","KB-156"],"supersedes":"OQ-artwork-182"}
```

## OQ-artwork-render-056 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-056","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Chạy lại sau merge/production: lượt chạy Testlane TIB-230 (staging 2026-10-22 14:20) diễn ra trước khi PR teeinblue-api #4044 merge (2026-10-22 15:44), chỉ trên font thay thế (Dancing Script/Roboto/Heebo); ngày ship production chưa xác nhận. Cần chạy lại trên build đã merge (staging) và production cho Locate Artwork và Order Design PNG (có số đo), rồi gửi CCR mới.","kb_ids":["KB-146","KB-147","KB-148","KB-149","KB-150","KB-151","KB-152","KB-153","KB-155","KB-156","KB-154","KB-404","KB-406","KB-412","KB-413","KB-414"],"supersedes":"OQ-artwork-183"}
```

## OQ-artwork-render-057 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-057","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Sau khi bỏ file pre-render của border custom_shape, order design (print file) lấy border từ đâu, và border size có đúng không? Comment #53942 chỉ nói SDK vẽ trên canvas; scope.surface của KB-425 ghi \"render\" chung, CHK-011, CHK-012 không kiểm print file. Nếu print file đổi đường xử lý thì KB-425 phải lên impact HIGH.","kb_ids":["KB-425"],"supersedes":"OQ-artwork-195"}
```

## OQ-artwork-render-058 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-058","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"KB-570: design PNG của artwork có layer SVG clip-path lồng nhiều cấp vẽ đúng hình đã mask ở cả 4 format PNG_*, theo dev doc auto-generated; quan sát mới có ở PNG_RGB. Đây có phải hành vi đúng ở cả PNG_RGBA, PNG_ADOBE_RGB, PNG_SRGB không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-001, CHK-002.","kb_ids":["KB-570"],"supersedes":"OQ-artwork-196"}
```

## OQ-artwork-render-059 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-059","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"KB-571: chỉ nhánh PNG đổi sang resvg, EPS/AI/PDF vẫn qua Inkscape, theo dev doc auto-generated; EPS và AI chưa có quan sát. Có xác nhận được export EPS/AI/PDF vẫn hoạt động như trước không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-003.","kb_ids":["KB-571"],"supersedes":"OQ-artwork-197"}
```

## OQ-artwork-render-060 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-060","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"KB-572: SVG có <image href=\"data:…\"> (href trần) vẫn hiện ảnh nhúng ở thumbnail và design PNG, theo dev doc auto-generated. Đây có phải hành vi đúng không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-004.","kb_ids":["KB-572"],"supersedes":"OQ-artwork-198"}
```

## OQ-artwork-render-061 — CONFLICT

```json
{"oq_id":"OQ-artwork-render-061","type":"CONFLICT","feature_id":"print-design-render","summary":"Nền design file PNG_RGB, PNG_ADOBE_RGB, PNG_SRGB khi render SVG: tài liệu dev và số đo staging nói ngược nhau. Nền đúng của từng format PNG_* là gì? Chờ PO/Dev trả lời câu hỏi PENDING-09 của bộ test QA-3395; số đo phía side_b cũng cần lặp lại trên build ghi rõ. Hai item UNRESOLVED, không làm oracle; CHK-008 chỉ ghi nhận, không kết luận.","side_a":"Dev doc auto-generated của PR teeinblue-api #3836 (2026-09-23, KB-573): PNG_RGB, PNG_ADOBE_RGB, PNG_SRGB nền trắng đục, giữ như mặc định Inkscape cũ; PNG_RGBA nền trong suốt.","side_b":"Lượt đo QA trên staging 2026-10-07 (KB-574, mỗi format một order, không ghi build): PNG_RGB, PNG_ADOBE_RGB, PNG_SRGB là PNG RGBA nền trong suốt (pixel góc alpha 0), giống một order PNG_RGB trước fix.","kb_ids":["KB-573","KB-574"],"supersedes":"OQ-artwork-199"}
```

## OQ-artwork-render-062 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-062","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"KB-573: theo dev doc auto-generated, PNG_RGBA có nền trong suốt; PNG_RGBA chưa được thử (TC-09 tạm dừng). Đây có phải hành vi đúng không? (Phần PNG_RGB/ADOBE_RGB/SRGB xem OQ-artwork-199.) Cần PO xác nhận (ảnh hưởng file in).","kb_ids":["KB-573"],"supersedes":"OQ-artwork-200"}
```

## OQ-artwork-render-063 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-063","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"KB-575: design PNG_ADOBE_RGB nhúng ICC \"Adobe RGB (1998)\" và PNG_SRGB nhúng ICC \"sRGB IEC61966-2.1\", một mẫu mỗi format ngày 2026-10-07. Đây có phải hành vi đúng không? Cần PO xác nhận (ảnh hưởng file in). Liên quan CHK-007.","kb_ids":["KB-575"],"supersedes":"OQ-artwork-201"}
```

## OQ-artwork-render-064 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-064","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"KB-576: clip-path trỏ id không tồn tại thì shape không bị clip, clip-path khai qua CSS style vẫn clip đúng ở thumbnail, quan sát một lượt 2026-10-07. Đây có phải hành vi đúng không? Liên quan CHK-005, CHK-006.","kb_ids":["KB-576"],"supersedes":"OQ-artwork-202"}
```

## OQ-artwork-render-065 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-065","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Design file và thumbnail của SVG được sinh lúc nào, do sự kiện gì (tạo order, upload, regenerate thủ công)? KB-570..576 không mô tả trigger, nên check của feature này chưa có bước dựng đầu ra rõ ràng.","kb_ids":[],"supersedes":"OQ-artwork-203"}
```

## OQ-artwork-render-066 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-066","type":"OPEN_ISSUE","feature_id":"print-design-render","summary":"Chạy lại trên build ghi rõ và production: mọi lượt chạy làm nguồn cho KB-570..584 (staging 2026-10-07/08, AI chạy) không ghi build, CCR ghi SHIPPED nhưng chưa có bằng chứng production; role khác merchant-owner và cross-tenant chưa quan sát. Cần lượt chạy có build (hoặc nguồn PO/Dev nguyên văn) rồi gửi CCR mới để nâng các item này.","kb_ids":["KB-570","KB-571","KB-572","KB-573","KB-574","KB-575","KB-576","artwork-layer-config/special-layer-config#KB-577","artwork-layer-config/special-layer-config#KB-578","artwork-layer-config/special-layer-config#KB-579","artwork-layer-config/special-layer-config#KB-580","artwork-layer-config/vector-layer-config#KB-581","artwork-layer-config/vector-layer-config#KB-582","artwork-layer-config/vector-layer-config#KB-583","artwork-layer-config/vector-layer-config#KB-584"],"supersedes":"OQ-artwork-204"}
```

## OQ-artwork-render-067 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-067","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Một lượt chạy dùng ảnh gốc full-resolution, áp effect tuần tự, progress dừng 95%, all or nothing: chỉ có dev doc tự sinh (2026-10-08). Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-802"],"supersedes":"OQ-artwork-215"}
```

## OQ-artwork-render-068 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-068","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Chạy thành công thay ảnh layer (một bước undo), lưu ảnh mới vào image library, ảnh cũ giữ nguyên: chỉ có dev doc tự sinh (2026-10-08). Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-803"],"supersedes":"OQ-artwork-216"}
```

## OQ-artwork-render-069 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-069","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Chạy lại lấy ảnh hiện tại; đổi cấu hình effect không tự cập nhật ảnh: mục spec không xác định được người viết/ngày. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-806"],"supersedes":"OQ-artwork-217"}
```

## OQ-artwork-render-070 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-070","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Toast \"Could not run effects\" 10 giây và warning layer không còn trong template: chỉ có dev doc tự sinh. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-811"],"supersedes":"OQ-artwork-218"}
```

## OQ-artwork-render-071 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-071","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Double-click Run effects chỉ một lượt: chỉ có quan sát TC-79, câu nguồn nằm ở Possible test cases. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-812"],"supersedes":"OQ-artwork-219"}
```

## OQ-artwork-render-072 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-072","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Danh sách dịch vụ được kiểm API key trước khi chạy và kiểm lại phía server: chỉ có dev doc tự sinh. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code.","kb_ids":["KB-816"],"supersedes":"OQ-artwork-220"}
```

## OQ-artwork-render-073 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-073","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Vế phụ CLAIM-08: đóng layer editor/chọn layer khác/mở lại artwork khi đang chạy không mất lượt chạy, progress bar hiện lại: chỉ từ dev doc tự sinh. Cần: PO hoặc Dev xác nhận nguyên văn vế này (có ngày, có link). Đây có phải hành vi đúng không?","kb_ids":["KB-808"],"supersedes":"OQ-artwork-221"}
```

## OQ-artwork-render-074 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-074","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Vế phụ CLAIM-09: chữ toast \"Timed out waiting for the effects to finish.\" và quy tắc hàng đợi không tính vào 6 phút: chỉ từ dev doc tự sinh. Cần: PO hoặc Dev xác nhận nguyên văn vế này (có ngày, có link). Đây có phải hành vi đúng không?","kb_ids":["KB-810"],"supersedes":"OQ-artwork-222"}
```

## OQ-artwork-render-075 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-075","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Vế phụ CLAIM-12: 5 lượt/phút/store dùng chung owner + staff, đổi được trong server config, tính vào giới hạn upload layer image: chỉ từ dev doc tự sinh. Cần: PO hoặc Dev xác nhận nguyên văn vế này (có ngày, có link). Đây có phải hành vi đúng không?","kb_ids":["KB-814"],"supersedes":"OQ-artwork-223"}
```

## OQ-artwork-render-076 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-076","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Vế hover style của nút Run effects (nền primary blue, chữ trắng) đã bỏ khỏi KB: chỉ dựa mục spec \"Run effects\" trong description TIB-5470, không xác định được người viết/ngày. Cần: PO xác nhận nguyên văn style hover của nút Run effects. Đây có phải hành vi đúng không?","kb_ids":["KB-801"],"supersedes":"OQ-artwork-224"}
```

## OQ-artwork-render-077 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-077","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Vế bỏ khỏi CLAIM-05: bật lại HD sau khi chạy thì HD dựng từ ảnh đã xử lý; chỉ có trong dev doc tự sinh, chưa quan sát (TC-09 tạm dừng). Cần: Dev/PO xác nhận nguyên văn và QA quan sát khi bật lại HD sau lượt chạy. Đây có phải hành vi đúng không? Quan hệ với KB-421/KB-423 (HD dựng từ ảnh trong image library) chưa rõ.","kb_ids":["KB-804"],"supersedes":"OQ-artwork-225"}
```

## OQ-artwork-render-078 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-078","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Vế bỏ khỏi CLAIM-08: reload trang khi đang chạy (progress bar mất, layer không bị thay, ảnh vẫn vào library); nguồn là mục Possible test cases, TC-14..16 không có kết quả có ngày. Cần: Dev/PO xác nhận nguyên văn hành vi khi reload trang lúc đang chạy. Đây có phải hành vi đúng không?","kb_ids":["KB-807"],"supersedes":"OQ-artwork-226"}
```

## OQ-artwork-render-079 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-079","type":"OPEN_ISSUE","feature_id":"image-effects-run","summary":"Known limitation: chuỗi có cả Remove background và Face cutout vẫn đòi key Remove background dù server bỏ qua Remove background; workaround xoá effect Remove background. PO chỉ chấp nhận cho release (ok Q5, 2026-10-14); TC-31 tạm dừng. Cần: Ticket theo dõi việc sửa, hoặc PO xác nhận giữ giới hạn này lâu dài.","kb_ids":["KB-818"],"supersedes":"OQ-artwork-227"}
```

## OQ-artwork-render-080 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-080","type":"OPEN_ISSUE","feature_id":"image-effects-run","summary":"Điều kiện hiển thị nút Run effects chưa kiểm hết: store Etsy chưa có lượt kiểm (TC-03 not-run); Linked/No customization mới kiểm 2/4 layer (TC-80 tạm dừng). Cần: QA chạy TC-03 trên store Etsy và hoàn tất TC-80.","kb_ids":["KB-800"],"supersedes":"OQ-artwork-228"}
```

## OQ-artwork-render-081 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-081","type":"OPEN_ISSUE","feature_id":"image-effects-run","summary":"Face Cutout và Photo Enhancer có cần API key trước khi chạy hay không: chưa ai trả lời (PENDING-12). Cần: Dev trả lời nguyên văn Face Cutout / Photo Enhancer có nằm trong danh sách kiểm key không. Bổ sung CBS-140 (2026-11-11): spec-hub rule image-effects-needs-key (S2, KB-985) chỉ nói effect của dịch vụ ngoài cần key và effect của Teeinblue không cần key, không nói Face cutout thuộc loại nào; câu hỏi vẫn mở.","kb_ids":["KB-816"],"supersedes":"OQ-artwork-229"}
```

## OQ-artwork-render-082 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-082","type":"OPEN_ISSUE","feature_id":"image-effects-run","summary":"Liên hệ object image-library (không sửa ở run này): image-library KB-012 đang ghi quota theo ngày là suy đoán (CHK-041, OQ-image-library-023), trong khi Dev Q10 nêu default 1000 ảnh/ngày/store cho giới hạn upload khi chạy effect. Khác sdk KB-051 (rate limit buyer). Cần: Đối chiếu ở run của object image-library; không đổi item image-library ở đây. Cũng chưa rõ chu kỳ theo ngày lịch hay cửa sổ trượt, và giới hạn 5 lượt/phút của portal có dùng chung limiter với sdk KB-051 (buyer, storefront) không.","kb_ids":["KB-813","KB-814"],"supersedes":"OQ-artwork-230"}
```

## OQ-artwork-render-083 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-083","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"KB-815 (quyền, Dev Q4 2026-10-14): Manage Artwork là quyền duy nhất cần để chạy Run effects, staff không có quyền không mở được artwork editor và server từ chối lượt chạy. Item đã CONFIRMED_EXPECTED nhưng thuộc chủ đề permission (rủi ro cao): PO xác nhận lại phạm vi quyền này, và QA cần một staff không có Manage Artwork để kiểm (CHK-021, CHK-022).","kb_ids":["KB-815"],"supersedes":"OQ-artwork-231"}
```

## OQ-artwork-render-084 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-084","type":"OPEN_ISSUE","feature_id":"image-effects-run","summary":"Run effects và popover Fill in variables trên Photo layer dùng Global Option: KB-800 cố ý không phát biểu về layer Global Option (phần \"không hiện cho Global option\" của dev doc đã bị spec 2026-10-19 đảo lại); KB-819 (spec) nói popover áp cho cả normal và global options. Hành vi phía Global Option thuộc object global-option (đã publish, còn OQ mở ở đó). Cần đối chiếu hai object khi test layer dùng Global Option.","kb_ids":["KB-800","KB-819"],"supersedes":"OQ-artwork-232"}
```

## OQ-artwork-render-085 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-085","type":"OPEN_ISSUE","feature_id":"image-effects-run","summary":"Rule đã xác nhận nhưng chưa có lượt quan sát trên staging: tooltip \"Save the artwork first...\" cho layer PSD/Canva chưa Save (TC-05 tạm dừng), timeout thật (TC-19 chỉ mô phỏng), toast hết giới hạn 1000 ảnh/ngày, staff không có Manage Artwork. Cần setup (dev hỗ trợ ép timeout/quota, staff test) để chạy CHK-005, CHK-013, CHK-019, CHK-021/022.","kb_ids":["KB-801","KB-809","KB-813","KB-815"],"supersedes":"OQ-artwork-233"}
```

## OQ-artwork-render-086 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-086","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"artwork KB-049 (artwork-save-persist) ghi thao tác trong editor không gọi API và phiên chưa Save không để lại dấu vết DB; Run effects gọi API, để lại ảnh mới trong image library và tính vào giới hạn upload dù artwork không Save. KB-049 chỉ liệt kê add/edit/delete/accordion/duplicate nên chưa mâu thuẫn; cần xác nhận Run effects là ngoại lệ có chủ đích của quy tắc \"không Save thì không để lại dấu vết\".","kb_ids":["KB-802","KB-803","KB-814"],"supersedes":"OQ-artwork-234"}
```

## OQ-artwork-render-087 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-087","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"\"Photo layer\" trong KB-800 có gồm layer Multiple Uploads (mục Image effects after generating, KB-018) hay Text to Image không? Nguồn chỉ nói Photo layer customization Normal; cả candidate và base đều không nói.","kb_ids":["KB-800"],"supersedes":"OQ-artwork-235"}
```

## OQ-artwork-render-088 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-088","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Giá trị chỉ gồm khoảng trắng bị coi là trống (PENDING-19, PO chưa xác nhận). Cần: PO xác nhận nguyên văn expected của hành vi này; khi có, CCR mới có thể nâng lên CONFIRMED_EXPECTED. Đây có phải hành vi đúng không?","kb_ids":["KB-826"],"supersedes":"OQ-artwork-236"}
```

## OQ-artwork-render-089 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-089","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Mọi biến không khớp thì chạy thẳng, không mở popover (PENDING-16; spec có thể đọc là popover rỗng). Cần: PO xác nhận nguyên văn expected của hành vi này; khi có, CCR mới có thể nâng lên CONFIRMED_EXPECTED. Đây có phải hành vi đúng không?","kb_ids":["KB-828"],"supersedes":"OQ-artwork-237"}
```

## OQ-artwork-render-090 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-090","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Giá trị nhập hiển thị như text thường, payload XSS/HTML không render: chỉ là quan sát TC-86/87. Cần: PO xác nhận nguyên văn expected của hành vi này; khi có, CCR mới có thể nâng lên CONFIRMED_EXPECTED. Đây có phải hành vi đúng không? Chủ đề bảo mật (rủi ro cao): PO xác nhận giá trị nhập phải hiển thị như text thường.","kb_ids":["KB-830"],"supersedes":"OQ-artwork-238"}
```

## OQ-artwork-render-091 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-091","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Vế phụ CLAIM-17: prompt không có biến thì chạy thẳng; đóng popover thì không chạy: chỉ là kết quả test, spec không ghi nguyên chữ. Cần: PO hoặc Dev xác nhận nguyên văn vế này (có ngày, có link). Đây có phải hành vi đúng không?","kb_ids":["KB-820"],"supersedes":"OQ-artwork-239"}
```

## OQ-artwork-render-092 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-092","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Vế phụ CLAIM-18: giá trị lưu không hợp lệ với input type mới bị bỏ, field trống + hint (PENDING-20, PO chưa xác nhận). Cần: PO hoặc Dev xác nhận nguyên văn vế này (có ngày, có link). Đây có phải hành vi đúng không?","kb_ids":["KB-822"],"supersedes":"OQ-artwork-240"}
```

## OQ-artwork-render-093 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-093","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Vế bỏ khỏi CLAIM-22: option bị đổi tên thì token cũ không còn khớp (hệ quả suy ra từ Q1 B, PENDING-21), PO không nói riêng. Cần: PO xác nhận nguyên văn hành vi khi option bị đổi tên. Đây có phải hành vi đúng không?","kb_ids":["KB-827"],"supersedes":"OQ-artwork-241"}
```

## OQ-artwork-render-094 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-094","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Vế bỏ khỏi CLAIM-24: giá trị nhập trong popover không ghi vào default của option trong artwork; không có trong quote xác nhận. Cần: PO/Dev xác nhận nguyên văn giá trị nhập không ghi vào default của option. Đây có phải hành vi đúng không?","kb_ids":["KB-829"],"supersedes":"OQ-artwork-242"}
```

## OQ-artwork-render-095 — CONFLICT

```json
{"oq_id":"OQ-artwork-render-095","type":"CONFLICT","feature_id":"image-effects-run","summary":"Chữ hint field trống trong popover Fill in variables: spec (PO, 2026-10-26) ghi \"No default value. Enter one to run.\", build staging 2026-10-30 (assets/index.BMgdZMSW.js) hiện \"No valid default value. Enter one to run.\" cho mọi field trống. Cần: PO hoặc QA lead chọn chữ đúng; nếu build đúng thì cần cập nhật spec.","kb_ids":["KB-824","KB-825"],"side_a":"Spec TIB-5470 description, Update: Prompt variables › Fields (PO, 2026-10-26): hint \"No default value. Enter one to run.\"","side_b":"QA-3406 TC-61 (tạm dừng) 2026-10-30, build assets/index.BMgdZMSW.js: hint \"No valid default value. Enter one to run.\" cho mọi field trống, kể cả option không có default.","conflict_group":"fill-variables-empty-hint-copy","supersedes":"OQ-artwork-243"}
```

## OQ-artwork-render-096 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-096","type":"OPEN_ISSUE","feature_id":"image-effects-run","summary":"Vế giá trị nhập không chia sẻ sang browser, tab hoặc staff khác đã được PO chọn (Q2 A) nhưng chưa kiểm trực tiếp. Cần: QA kiểm trên browser/tab khác và với staff khác.","kb_ids":["KB-829"],"supersedes":"OQ-artwork-244"}
```

## OQ-artwork-render-097 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-097","type":"OPEN_ISSUE","feature_id":"image-effects-run","summary":"Liên hệ object sdk (không sửa ở run này): sdk KB-415 nói storefront JSON List điền được prompt variable, còn câu hỏi Dev 55823 xếp biến JSON list vào nhóm biến portal không khớp. Khác surface, không chọn phía. Cần: Dev xác nhận biến JSON list trong popover portal có khớp option không, đối chiếu với storefront.","kb_ids":["KB-827"],"supersedes":"OQ-artwork-245"}
```

## OQ-artwork-render-098 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-098","type":"OPEN_ISSUE","feature_id":"image-effects-run","summary":"Biến của ImagenHub template (effect imagenhub:image_filter) có mở popover Fill in variables như biến trong prompt không? Chưa thử (TC-78, PENDING-18); liên quan artwork KB-424 (warning ImagenHub variables). Liên quan CHK-021.","kb_ids":["KB-819"],"supersedes":"OQ-artwork-246"}
```

## OQ-artwork-render-099 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-099","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Nguồn biến của prompt effect trên Photo layer: KB-113/KB-115 (layer-config-image) chỉ mô tả \"+ Variable\" trong prompt GenAI của Multiple Uploads/Text to Image (lấy Option Title từ layer Text/Additional Option khác, quan sát một lần); KB-819/KB-821 khớp biến với option gồm text, Only numbers, Date picker, option layer. Base chưa có item nào cho biến trong prompt của Image effects trên Photo layer: cần xác nhận cùng một cơ chế khớp biến.","kb_ids":["KB-819","KB-821"],"supersedes":"OQ-artwork-247"}
```

## OQ-artwork-render-100 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-100","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Effect có bật dùng kích thước layer: hai layer khác kích thước thì gọi riêng, mỗi lần trừ một lượt. Không nạp KB (S0). Tên công tắc trên portal chưa biết, không có test case. Cần: Dev (giangnth) xác nhận nguyên văn, có ngày và link (ví dụ comment trên Jira TIB-5577), lời sửa câu Q2 ngày 2026-10-29; hiện chỉ là lời QA QA chuyển lại, kênh gốc không rõ, không có trên Jira. Chưa xác nhận thì không nạp KB.","kb_ids":[],"supersedes":"OQ-artwork-248"}
```

## OQ-artwork-render-101 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-101","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Effect Gen AI trên layer Photo Reposition không bật dùng kích thước layer: hai layer khác kích thước vẫn gọi chung một lần. Không nạp KB (S0), không có test case. Cần: Dev (giangnth) xác nhận nguyên văn, có ngày và link (ví dụ comment trên Jira TIB-5577), lời sửa câu Q2 ngày 2026-10-29; hiện chỉ là lời QA QA chuyển lại, kênh gốc không rõ, không có trên Jira. Chưa xác nhận thì không nạp KB.","kb_ids":[],"supersedes":"OQ-artwork-249"}
```

## OQ-artwork-render-102 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-102","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Contour cut: khác chiều rộng thì gọi riêng, cùng chiều rộng khác chiều cao thì gọi chung. Không nạp KB (S0), không có test case; không đụng item contour cut của layer-print-effects. Cần: Dev (giangnth) xác nhận nguyên văn, có ngày và link (ví dụ comment trên Jira TIB-5577), lời sửa câu Q2 ngày 2026-10-29; hiện chỉ là lời QA QA chuyển lại, kênh gốc không rõ, không có trên Jira. Chưa xác nhận thì không nạp KB. Khi được xác nhận thì đối chiếu lại item contour cut KB-391 (layer-print-effects) và KB-044.","kb_ids":[],"supersedes":"OQ-artwork-250"}
```

## OQ-artwork-render-103 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-103","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Các effect không phụ thuộc kích thước (gray_scale, remove background, watercolor, sketch…; danh sách chỉ là ví dụ) luôn gọi chung dù layer khác kích thước. Không nạp KB (S0); ngược với cách đọc rộng câu Q2 trên Jira (xem OQ CONFLICT populate-share-call-layer-size). Cần: Dev (giangnth) xác nhận nguyên văn, có ngày và link (ví dụ comment trên Jira TIB-5577), lời sửa câu Q2 ngày 2026-10-29; hiện chỉ là lời QA QA chuyển lại, kênh gốc không rõ, không có trên Jira. Chưa xác nhận thì không nạp KB.","kb_ids":[],"supersedes":"OQ-artwork-251"}
```

## OQ-artwork-render-104 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-104","type":"NEEDS_CONFIRMATION","feature_id":"populate-output-chain","summary":"gray_scale trên hai layer Direct upload khác kích thước dùng chung một lần gọi derive: chỉ có quan sát QA-3434 TC-64 (2026-10-27, build không ghi), test case không có căn cứ expected có nguồn. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) đây là hành vi đúng; chạy lại trên build có ghi phiên bản (sau 2026-10-29 08:21 GMT).","kb_ids":["KB-853"],"supersedes":"OQ-artwork-252"}
```

## OQ-artwork-render-105 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-105","type":"NEEDS_CONFIRMATION","feature_id":"populate-output-chain","summary":"Option chained {{output}} bắt đầu từ ảnh đã xử lý của nguồn, effect nguồn chạy một lần cho mỗi ảnh: chỉ có dev doc tự sinh từ branch diff (TIB-5504 comment 56020, 2026-10-29). Comment 56446 TIB-5504 (Dev, 2026-11-04, ngoài CCR) nói đã đổi luật effect trùng giữa nguồn và option {{output}} (effect trùng chỉ chạy một lần); không phải claim, không nạp. Item này không resolve OQ-artwork-093, OQ đó giữ mở. Cần: PO hoặc Dev xác nhận nguyên văn (có ngày, có link) rằng đây là hành vi đúng, không chỉ là mô tả code; đồng thời làm rõ luật effect trùng theo comment 56446 qua một Proposal riêng.","kb_ids":["KB-854"],"supersedes":"OQ-artwork-253"}
```

## OQ-artwork-render-106 — CONFLICT

```json
{"oq_id":"OQ-artwork-render-106","type":"CONFLICT","feature_id":"populate-output-chain","summary":"Effect không phải Gen AI trên layer Direct upload / Cropper: hai layer khác kích thước có tách lần gọi (và lượt) hay không. Phần Gen AI (KB-851) không tranh chấp. Cần: Dev xác nhận nguyên văn có ngày + link phía nào đúng; lời sửa Q2 ngày 2026-10-29 (CLAIM-03/04/05/07, S0, không link) ủng hộ side_b nhưng không được dùng làm căn cứ. Liên quan: request Gen AI có mang kích thước layer không (KB-851 so với KB-853) chưa rõ. Liên quan CHK-030.","kb_ids":["KB-852","KB-853"],"conflict_group":"populate-share-call-layer-size","side_a":"Jira TIB-5577 comment 55689 (Dev, 2026-10-27, Q2): kích thước layer Direct upload / Cropper thuộc thiết lập effect, khác kích thước thì gọi riêng, tính lượt riêng; câu không giới hạn loại effect (KB-852).","side_b":"QA-3434 TC-64 PASS 2026-10-27 staging: gray_scale trên layer Direct upload 400×400 và 400×300 dùng chung một lần gọi derive, request không mang kích thước (KB-853).","supersedes":"OQ-artwork-254"}
```

## OQ-artwork-render-107 — CONFLICT

```json
{"oq_id":"OQ-artwork-render-107","type":"CONFLICT","feature_id":"populate-output-chain","summary":"Option Photo Reposition {{output}} có effect riêng: điều kiện đi theo vị trí nguồn chỉ là tỷ lệ ảnh kết quả lệch ≤ 0.05, hay còn phụ thuộc tỷ lệ khung option so với khung nguồn. Cần: Dev trả lời về TC-28 (bug draft chưa file); chạy TC-27 và mốc 1.049/1.051. Liên quan CHK-040.","kb_ids":["KB-856","KB-857"],"conflict_group":"populate-reposition-follow-ratio","side_a":"Jira TIB-5504 comment 56059 (Dev, 2026-10-29, Q5): đi theo khi tỷ lệ kết quả lệch ≤ 0.05 so với ảnh nguồn (KB-856).","side_b":"QA-3441 TC-28 FAIL 2026-10-29 staging: khung option 400×400 khác khung nguồn 400×300 thì không đi theo dù lệch 0.04/0.05 (KB-857).","supersedes":"OQ-artwork-255"}
```

## OQ-artwork-render-108 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-108","type":"OPEN_ISSUE","feature_id":"populate-output-chain","summary":"Known issue nguồn Photo Cropper: thay ảnh thì option {{output}} bắt đầu ngay từ ảnh mới, effect nguồn chạy hai lần, lỗi thì option và nguồn hiện ảnh khác nhau. Không do TIB-5504, có ticket riêng nhưng dev không nêu key; thấy một lần ở QA-3441 TC-24, chưa file bug. Cần: Key ticket riêng và trạng thái fix; không dùng làm expected. Liên quan CHK-045. Chưa rõ lần chạy effect nguồn thứ hai có tính thêm lượt không.","kb_ids":["KB-867"],"supersedes":"OQ-artwork-256"}
```

## OQ-artwork-render-109 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-109","type":"OPEN_ISSUE","feature_id":"populate-output-chain","summary":"Known preview vs print mismatch: preview storefront không vẽ vị trí populate từ Photo Reposition cho layer No personalization, vẫn fit ảnh vào khung, trong khi order render dùng vị trí đó. Cần: Ticket theo dõi lệch preview/bản in và kế hoạch xử lý; không dùng làm expected. PO xác nhận vị trí populate từ Photo Reposition dùng trong order render là chủ đích (rủi ro order, impact HIGH); chưa có lượt đặt đơn thật đối chiếu vị trí trên order design. Liên quan CHK-038, CHK-039.","kb_ids":["KB-859","KB-860"],"supersedes":"OQ-artwork-257"}
```

## OQ-artwork-render-110 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-110","type":"NEEDS_CONFIRMATION","feature_id":"populate-output-chain","summary":"Lượt bị trừ khi populated option dùng chung hoặc tách lần gọi effect: số lượt khi dùng chung một lần gọi chưa đo (QA-3434 TC-13 tạm dừng), và \"lượt\" là bộ đếm nào (Gen AI credit của store, rate-limit visitor của sdk, hay quota Run effects của portal) chưa rõ; cũng chưa rõ lần gọi lại sau reload (KB-865) có tính thêm lượt không. Cần: PO xác nhận ý định tính lượt (rủi ro tiền, impact HIGH). Liên quan CHK-031.","kb_ids":["KB-850","KB-851","KB-852","KB-853","KB-865"],"supersedes":"OQ-artwork-258"}
```

## OQ-artwork-render-111 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-111","type":"OPEN_ISSUE","feature_id":"populate-output-chain","summary":"Layer Cropper chưa có lượt kiểm cho Gen AI khác kích thước gọi riêng: QA-3434 TC-14 chỉ chạy Gemini trên Direct upload và chưa chạy lại trên build sau 2026-10-29 08:21 GMT. Cần: QA chạy trên layer Cropper với build có ghi phiên bản.","kb_ids":["KB-851"],"supersedes":"OQ-artwork-259"}
```

## OQ-artwork-render-112 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-112","type":"OPEN_ISSUE","feature_id":"populate-output-chain","summary":"Hành vi lỗi của option chained {{output}} mới kiểm với lỗi giả lập trong trang (HTTP 500 / status 3), chưa kiểm với lỗi thật từ provider. Cần: QA kiểm với lỗi thật (ví dụ prompt bị moderation chặn).","kb_ids":["KB-862","KB-863","KB-864"],"supersedes":"OQ-artwork-260"}
```

## OQ-artwork-render-113 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-113","type":"OPEN_ISSUE","feature_id":"populate-output-chain","summary":"Add to Cart bị chặn khi effect riêng của option chained {{output}} lỗi chưa được test riêng (rủi ro order, impact HIGH). Cần: QA kiểm vế Add to Cart; PO xác nhận nếu kết quả khác.","kb_ids":["KB-864"],"supersedes":"OQ-artwork-261"}
```

## OQ-artwork-render-114 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-114","type":"OPEN_ISSUE","feature_id":"populate-output-chain","summary":"Layer ảnh No personalization populate {{output}} từ nguồn Photo Cropper nhận ảnh đã crop: dev nói đúng theo code nhưng chưa kiểm trên UI (staging chưa có campaign có cấu hình này), CCR ghi QA-3441 TC-38 PASS. Cần: dựng fixture trên store explorer và kiểm trên UI.","kb_ids":["KB-858"],"supersedes":"OQ-artwork-262"}
```

## OQ-artwork-render-115 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-115","type":"NEEDS_CONFIRMATION","feature_id":"populate-output-chain","summary":"Chain populate {{output}} từ hai cấp trở lên: portal cho cấu hình nhưng chỉ một cấp được hỗ trợ; hành vi chain nhiều cấp không có expected. Cần: PO quyết portal có nên chặn cấu hình này hay ghi rõ không hỗ trợ. Liên quan CHK-036.","kb_ids":["KB-861"],"supersedes":"OQ-artwork-263"}
```

## OQ-artwork-render-116 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-116","type":"NEEDS_CONFIRMATION","feature_id":"populate-output-chain","summary":"Phạm vi token của KB-120 / CHK-022 (lan truyền ngay giá trị gốc): mới quan sát với {{input.1}} từ nguồn Multiple Uploads nhưng item không ghi rõ chỉ áp cho {{input.N}}. Với {{output}}, option bắt đầu từ ảnh đã xử lý của nguồn (KB-866, KB-854), và bắt đầu ngay từ ảnh mới với nguồn Photo Cropper là known defect (KB-867). Cần: ghi rõ phạm vi token của KB-120 ở lần cập nhật sau để không đọc rộng thành expected.","kb_ids":["KB-120","KB-866","KB-867"],"supersedes":"OQ-artwork-264"}
```

## OQ-artwork-render-117 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-117","type":"NEEDS_CONFIRMATION","feature_id":"populate-output-chain","summary":"Liên hệ object sdk (không sửa ở run này): sdk KB-487 nói layer populate target chạy effect lên ảnh buyer upload vào nguồn, có thể đọc là ảnh gốc; với {{output}} có effect nguồn, KB-866 nói option bắt đầu từ kết quả của nguồn. Cần: PO/Dev xác nhận KB-487 có phân biệt {{input}} và {{output}} không.","kb_ids":["KB-866","KB-854"],"supersedes":"OQ-artwork-265"}
```

## OQ-artwork-render-118 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-118","type":"NEEDS_CONFIRMATION","feature_id":"populate-output-chain","summary":"KB-865 (reload thì option chained chạy lại từ đầu) ngầm cần ảnh nguồn còn sau reload, trong khi sdk KB-019 thấy full reload không khôi phục form (field text/clipart). Khác loại field, không kết luận mâu thuẫn. Cần: quan sát photo layer sau reload.","kb_ids":["KB-865"],"supersedes":"OQ-artwork-266"}
```

## OQ-artwork-render-119 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-119","type":"NEEDS_CONFIRMATION","feature_id":"populate-output-chain","summary":"Base chỉ có quan sát portal cho nguồn Multiple Uploads (KB-118, KB-119); delta ngầm cho phép layer Photo (Direct upload / Cropper / Reposition) làm nguồn {{output}}, chưa có quan sát portal nào cho cấu hình này. Cần: quan sát dropdown Source option với nguồn Photo.","kb_ids":["KB-118","KB-119","KB-858","KB-859"],"supersedes":"OQ-artwork-267"}
```

## OQ-artwork-render-120 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-120","type":"NEEDS_CONFIRMATION","feature_id":"populate-output-chain","summary":"Mọi item CBS-091 (KB-850..KB-867) có trạng thái ship UNKNOWN: TIB-5577 và TIB-5504 đang Passed, chỉ có scope staging, production chưa có quan sát. Cần: xác nhận ticket đã ship production và build tương ứng.","kb_ids":["KB-850","KB-855","KB-859","KB-866"],"supersedes":"OQ-artwork-268"}
```

## OQ-artwork-render-121 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-121","type":"NEEDS_CONFIRMATION","feature_id":"populate-output-chain","summary":"Nợ base có sẵn: KB-124 (layer-config-image), CHK-024 và OQ-artwork-093 tham chiếu \"KB-008 (feature populate-values)\" trong khi item tương ứng trong shard populate-values là KB-120. Cần: sửa tham chiếu ở lần cập nhật sau.","kb_ids":["KB-120"],"supersedes":"OQ-artwork-269"}
```

## OQ-artwork-render-122 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-122","type":"OPEN_ISSUE","feature_id":"print-design-render","kb_ids":["KB-932","KB-933"],"summary":"KB-932, KB-933: mockup render ở danh sách Mockups chưa được kiểm theo fit rule của layer No personalization; chiều 'trước lần sync / Re-generate / save thì ảnh KHÔNG đổi' chưa được kiểm (không có đơn trước fix có layer ảnh mặc định trên staging). QA mới thấy chiều đổi sau sync/save (TC-21, TC-22). Cần: Test case có build cho mockup trong Mockups list và cho chiều chưa đổi trước sync/Re-generate/save (cần fixture dựng trước fix hoặc dữ liệu cũ).","check_ids":["CHK-058"],"supersedes":"OQ-artwork-325"}
```

## OQ-artwork-render-123 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-123","type":"OPEN_ISSUE","feature_id":"print-design-render","kb_ids":["KB-938"],"summary":"KB-938 (known defect): job order design fail khi layer No personalization không có ảnh mặc định và không có retrieval value (Dev 55639 RQ6, có từ trước TIB-5521). Ứng viên bug cho ticket riêng; chữ lỗi quan sát TC-30 'The url field is required.' khác tên exception dev nêu. Có cần ticket sửa và expected đúng là gì? Cần: PO quyết expected (vd chặn cấu hình hoặc render rỗng); Dev mở ticket riêng nếu sửa. Không tự tạo ticket — hỏi operator. Người quyết: PO (cờ requires_human_decision của diff cho KB-938).","check_ids":["CHK-059"],"supersedes":"OQ-artwork-326"}
```

## OQ-artwork-render-124 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-124","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","kb_ids":["KB-933"],"summary":"KB-933 (Dev TIB-5521 55637 Q2): sau fix TIB-5521 không có gì tự render lại; order design cũ chỉ đổi khi Re-generate, ảnh trên store đổi ở lần sync tới. Việc này chạm order/fulfillment. Người quyết: PO xác nhận ý định, và đơn đã render trước fix có cần regenerate không.","supersedes":"OQ-artwork-330"}
```

## OQ-artwork-render-125 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-125","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Single-type (Clipart Category›1) widget render RADIOGROUP thumbnail, item ứng layer.default_value pre-checked” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle","supersedes":"OQ-artwork-363"}
```

## OQ-artwork-render-126 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-126","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-003 “[NEEDS_CONFIRMATION] Group-type <select> chỉ có placeholder disabled, 0 item selectable dù category có 2 item xác nhận server-side” của feature clipart-category-storefront-behavior. current_behavior_only","supersedes":"OQ-artwork-364"}
```

## OQ-artwork-render-127 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-127","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “[NEEDS_CONFIRMATION] Server thêm key lạ 'artwork-<id>': <numeric> vào response customization save, không có ở client localStorage lúc ghi” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle","supersedes":"OQ-artwork-365"}
```

## OQ-artwork-render-128 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-128","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-013 “[NEEDS_CONFIRMATION] Preview size=500px 'không hoạt động đúng' (chỉ ra 250px) hay bị giới hạn bởi độ phân giải gốc file upload (no1.png/no2.png)?” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle","supersedes":"OQ-artwork-366"}
```

## OQ-artwork-render-129 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-129","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-017 “[CRITICAL, NEEDS_CONFIRMATION] Canvas/Preview modal/cart customization image compositing gap — chosen clipart never appears in rendered output” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle","supersedes":"OQ-artwork-367"}
```

## OQ-artwork-render-130 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-130","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-018 “[NEEDS_CONFIRMATION] Conflict CONF-CTX20260921-03-02 — nhánh WIDGET STOREFRONT: layer.default_value (không phải layer.url) là giá trị PRE-CHECK — đây có phải business rule dự kiến, và layer.url có nên là 1 lựa chọn hợp lệ trên storefront không?” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle","supersedes":"OQ-artwork-368"}
```

## OQ-artwork-render-131 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-131","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-019 “[GAP, NEEDS_CONFIRMATION] Hành vi buyer đã login / non-US market-locale-currency / mobile-tablet viewport cho personalization form clipart-category — 0 evidence trong run này” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle","supersedes":"OQ-artwork-369"}
```

## OQ-artwork-render-132 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-132","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-020 “[NEEDS_CONFIRMATION] Conflict CONF-API-CTX20260921-03-01 nhánh API ROOT EVIDENCE: GET /api/layer-image-categories trả [] vs GraphQL trả 10 rows cùng user/session (layer api, khác CHK-003 layer storefront)” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle","supersedes":"OQ-artwork-370"}
```

## OQ-artwork-render-133 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-133","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-021 “[POINTER, NEEDS_CONFIRMATION] CONF-CTX20260921-03-01 (Custom class field presence, layer-level) — KHÔNG có nhánh storefront, xem layer-config-image.json cho nội dung đầy đủ” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle","supersedes":"OQ-artwork-371"}
```

## OQ-artwork-render-134 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-134","type":"NEEDS_CONFIRMATION","feature_id":"storefront-clipart-selection","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-022 “[GAP, NEEDS_CONFIRMATION] Hành vi personalization form khi 'Show option to select default value' = OFF — 0 evidence trong run này (chỉ test ON)” của feature clipart-category-storefront-behavior. missing_or_unresolved_oracle","supersedes":"OQ-artwork-372"}
```

## OQ-artwork-render-135 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-135","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Nút Print Effects mở popover shape-cut với 5 preset + Customize” của feature layer-print-effects. missing_or_unresolved_oracle","supersedes":"OQ-artwork-436"}
```

## OQ-artwork-render-136 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-136","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “Nút 'Apply layout' disabled khi 0 shape-cut được chọn” của feature layer-print-effects. missing_or_unresolved_oracle","supersedes":"OQ-artwork-437"}
```

## OQ-artwork-render-137 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-137","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-003 “Customize cho phép tuỳ chỉnh grid rows/columns” của feature layer-print-effects. missing_or_unresolved_oracle","supersedes":"OQ-artwork-438"}
```

## OQ-artwork-render-138 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-138","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-004 “Footnote nguyên văn trong popover Print Effects” của feature layer-print-effects. missing_or_unresolved_oracle","supersedes":"OQ-artwork-439"}
```

## OQ-artwork-render-139 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-139","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-005 “[CONF-004] Tính năng emboss có tồn tại hay không — KHÔNG được khẳng định là không tồn tại” của feature layer-print-effects. missing_or_unresolved_oracle","supersedes":"OQ-artwork-440"}
```

## OQ-artwork-render-140 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-140","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006 “Print Effects config lưu vào field nào trong PUT body” của feature layer-print-effects. missing_or_unresolved_oracle","supersedes":"OQ-artwork-441"}
```

## OQ-artwork-render-141 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-141","type":"NEEDS_CONFIRMATION","feature_id":"print-design-render","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “Trang 'Order Design' — nơi effect layer thực sự hiển thị làm production guide” của feature layer-print-effects. missing_or_unresolved_oracle","supersedes":"OQ-artwork-442"}
```

## OQ-artwork-render-142 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-142","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-015 “13 nhóm nguồn Browse values có bao phủ đầy đủ mọi layer/output type không” của feature populate-values. missing_or_unresolved_oracle","supersedes":"OQ-artwork-443"}
```

## OQ-artwork-render-143 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-143","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-016 “Cú pháp thật của {{value.formula(<expression>)}} và {{value.context.<from>To<to>}}” của feature populate-values. missing_or_unresolved_oracle. Bổ sung CBS-110 (2026-11-11): KB-987, KB-988, KB-991 (PROPOSED, rule QA) mô tả một phần kết quả token formula/context sai; chưa đủ làm expected cho CHK-016, xem CHK-046, CHK-047, CHK-050","supersedes":"OQ-artwork-444"}
```

## OQ-artwork-render-144 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-144","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-017 “Cơ chế khoá Google-Font-lock có áp dụng cho channel Background/Shape không (chỉ test Font/Color)” của feature populate-values. missing_or_unresolved_oracle","supersedes":"OQ-artwork-445"}
```

## OQ-artwork-render-145 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-145","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-018 “Layer đã populate hiển thị giá trị thật (không phải placeholder) trên storefront” của feature populate-values. missing_or_unresolved_oracle","supersedes":"OQ-artwork-446"}
```

## OQ-artwork-render-146 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-146","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-020 “[NEW v3, NEEDS_CONFIRMATION] Token '{{input}}' trần có xuất hiện khi Maximum photos=1 hay không?” của feature populate-values. missing_or_unresolved_oracle","supersedes":"OQ-artwork-447"}
```

## OQ-artwork-render-147 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-147","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-021 “[NEW v3, NEEDS_CONFIRMATION] Text to Image (AI) có bao giờ được offer làm Populate Content source hay không — chỉ 1 sample phủ định” của feature populate-values. current_behavior_only","supersedes":"OQ-artwork-448"}
```

## OQ-artwork-render-148 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-148","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-023 “[NEW v3, NEEDS_CONFIRMATION] Nửa 'layer đích tự động trigger effect chain riêng khi nhận giá trị populate' (liên quan TIB-5302) — chưa xác nhận” của feature populate-values. missing_or_unresolved_oracle","supersedes":"OQ-artwork-449"}
```

## OQ-artwork-render-149 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-149","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-024 “[NEW v3, NEEDS_CONFIRMATION] Hành vi propagation (KB-008, CHK-022) có giữ nguyên trên guest session thật hay không — hiện chỉ có staff-authenticated proxy” của feature populate-values. missing_or_unresolved_oracle","supersedes":"OQ-artwork-450"}
```

## OQ-artwork-render-150 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-150","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"[CBS-140, KB-984, spec-hub rule photo-upload-effect-rate-limit và photo-upload-network-limit] Spec-hub ghi shopper upload ảnh có effect AI/xử lý bị giới hạn 5 lần mỗi giờ cho mỗi option (mặc định, đổi được theo shop) và 50 lần mỗi giờ cho mỗi network trên mọi option và shop; upload có effect từ portal tính vào giới hạn network. Dev xác nhận các ngưỡng mặc định này không? Lượt Run effects trong artwork editor (quota riêng KB-814) có tính vào giới hạn network 50/giờ không? Spec-hub có hai chữ thông báo cho giới hạn theo option ('You've reached the image effect upload limit for this option...' và 'Upload limit exceeded for this field...'): shopper thấy chữ nào? sdk KB-051 (Dev, Jira TIB-5460, 2026-09-17) ghi giới hạn tính theo visitor và cửa sổ trên staging là 5 phút thay vì 1 giờ: giới hạn tính theo shopper theo option hay theo visitor, và trên staging cửa sổ là bao lâu?","kb_ids":["KB-984"],"supersedes":"OQ-artwork-452"}
```

## OQ-artwork-render-151 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-151","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"[CBS-140, KB-985, spec-hub rule image-effects-background-remover và image-effects-needs-key] Spec-hub ghi xoá nền dùng remover merchant chọn (account remove.bg/Removal.AI/Cutout.Pro của merchant, remover built-in của Teeinblue, hoặc gói Teeinblue x Removal.ai), và khi xử lý ảnh shopper upload thì effect của dịch vụ ngoài thiếu key bị bỏ qua âm thầm, effect của Teeinblue không cần key. Rule không nêu surface; run suy scope là xử lý ảnh shopper upload từ ví dụ của rule. Dev xác nhận đây là hành vi đúng khi xử lý ảnh shopper upload không? Rule 'bỏ qua âm thầm' có áp cho cả Run effects trong artwork editor không? Nếu có thì trái KB-816 (thiếu key thì không chạy và hiện warning); nếu không thì hai đường có cố ý khác nhau không?","kb_ids":["KB-985"],"supersedes":"OQ-artwork-453"}
```

## OQ-artwork-render-152 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-152","type":"NEEDS_CONFIRMATION","feature_id":"populate-value-tokens","summary":"[CBS-110, KB-987, rule QA FACT-022 nhóm 1] Rule QA ghi token có shape hợp lệ nhưng nội dung sai ra layer đích rỗng ('Default text'): {{value.context.<from>To<to>}} với đơn vị không hỗ trợ hoặc typo (yearToFortnight, yaerToMonth); {{value.formula(...)}} đủ ngoặc nhưng biểu thức sai (chia 0, thiếu vế, ký tự % hoặc ^); hậu tố .N hỏng nằm trong ngoặc. Mới là hành vi quan sát ở Live Preview trên staging (lượt chạy tự động QA-3353), mô tả của Dev chỉ nói 'formula/unit không hiểu thì layer để trống'. PO xác nhận đây là hành vi đúng không? Storefront và design file có cho cùng kết quả không? Liên quan CHK-046.","kb_ids":["KB-987"],"owner":"PO","supersedes":"OQ-artwork-455"}
```

## OQ-artwork-render-153 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-153","type":"NEEDS_CONFIRMATION","feature_id":"populate-value-tokens","summary":"[CBS-110, KB-988, rule QA FACT-022 nhóm 2] Rule QA ghi token trong namespace value. không phải format hợp lệ hoàn chỉnh ({{value.context.yearTo}}, {{value.context}}, {{value.wibble}}, {{value.contextt.yearToMonth}}, {{value.formula(origin+}}, {{value.formula(origin/3).abc}}) ra raw-value fallback: layer đích hiện giá trị nguồn, không rỗng. PO có duyệt việc hiện giá trị nguồn thay vì rỗng cho các token này không, và ranh giới 'ký tự sai trong hay ngoài ngoặc' có phải hành vi chủ ý không? Liên quan CHK-047.","kb_ids":["KB-988"],"owner":"PO","supersedes":"OQ-artwork-456"}
```

## OQ-artwork-render-154 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-154","type":"NEEDS_CONFIRMATION","feature_id":"populate-value-tokens","summary":"[CBS-110, KB-989, rule QA FACT-022 nhóm 3] Rule QA ghi token {{...}} không có prefix value ({{7*7}}, {{foobar}}, {{name}}) trong layer populate ra rỗng, không tính biểu thức, raw-value fallback chỉ áp trong namespace value. và resolver không in token chưa resolve ra nguyên văn. PO/Dev xác nhận đây là hành vi đúng không, kể cả trên storefront và design file? Liên quan CHK-048.","kb_ids":["KB-989"],"owner":"PO","supersedes":"OQ-artwork-457"}
```

## OQ-artwork-render-155 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-155","type":"NEEDS_CONFIRMATION","feature_id":"populate-value-tokens","summary":"[CBS-110, KB-990, rule QA FACT-023] Rule QA ghi nguồn Date picker (giá trị YYYY-MM-DD) cho {{value}} ra đúng ngày nhưng {{value.context.*}} và {{value.formula(...)}} ra rỗng, và nhóm 'Text & Curve Text' không có token ngày/now nên không tính được số ngày kể từ một ngày. Đây là giới hạn mong muốn hay lỗi? Nếu là lỗi thì ghi nhận như known defect; Calendar layer với token {{date.<format>}} chưa kiểm. Liên quan CHK-049.","kb_ids":["KB-990"],"owner":"PO","supersedes":"OQ-artwork-458"}
```

## OQ-artwork-render-156 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-156","type":"NEEDS_CONFIRMATION","feature_id":"populate-value-tokens","summary":"[CBS-110, KB-991, rule QA FACT-024] Rule QA ghi {{value.context.*}} dùng năm 365.2425 ngày, tháng 1/12 năm, dựng cứng, không có tuỳ chọn 365 ngày (đo: 40 yearToDay = 14610). Bản 'Change summary & test cases' của Dev trên Jira TIB-5385 (2026-09-07) mô tả đây là quyết định sản phẩm có chủ ý. Dev xác nhận nguyên văn có ngày đây là hành vi đã chốt và không có cấu hình khác không? Liên quan CHK-050.","kb_ids":["KB-991"],"owner":"Dev","supersedes":"OQ-artwork-459"}
```

## OQ-artwork-render-157 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-157","type":"NEEDS_CONFIRMATION","feature_id":"populate-value-tokens","summary":"[CBS-110, KB-992, rule QA FACT-100] Rule QA đo {{value.<N>char}}: .0char rỗng, X vượt độ dài ra nguyên chuỗi, .abcchar raw fallback, .-1char cắt bớt 1 ký tự cuối (khác initialofword.-1 ra raw fallback), .1.5char nhận số thập phân. Dev xác nhận đây là hành vi đúng hay lỗi (nhất là X âm và X thập phân), và bản đo đã ship production chưa? Liên quan CHK-051.","kb_ids":["KB-992"],"owner":"Dev","supersedes":"OQ-artwork-460"}
```

## OQ-artwork-render-158 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-158","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"[CBS-110, KB-993, rule QA FACT-063] Rule QA ghi text layer tĩnh (không gắn populate/personalization config) không đi qua populate resolver, content {{7*7}} hay <b>bold</b> hiện nguyên văn ở editor và ở render server-side (Preview/mockup). Lượt chạy chỉ thấy phía server-side sinh thumbnail thành công, không đọc được chữ. Dev xác nhận nguyên văn có ngày cho cả editor, Preview/mockup và design file không? Liên quan CHK-052.","kb_ids":["KB-993"],"owner":"Dev","supersedes":"OQ-artwork-461"}
```

## OQ-artwork-render-159 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-159","type":"NEEDS_CONFIRMATION","feature_id":"populate-value-tokens","summary":"[CBS-115, KB-994, rule QA FACT-094] Rule QA ghi option {{value.initialofword.X}} có trong Available values và resolve đúng trên Single-line Text, Curve Text, Warp Text, Paragraph (làm đích) và QR Code (QR mã hoá chuỗi đã resolve), picker không có type 'Shape Text'/'Clipart Frame'. Nguồn là lượt chạy tự động QA-3364 do AI ghi, build không rõ. Dev xác nhận danh sách layer đích này, kể cả storefront và design file? Liên quan CHK-053.","kb_ids":["KB-994"],"owner":"Dev","supersedes":"OQ-artwork-462"}
```

## OQ-artwork-render-160 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-160","type":"NEEDS_CONFIRMATION","feature_id":"populate-value-tokens","summary":"[CBS-115, KB-995, rule QA FACT-094] Rule QA (đo 2026-09-16) ghi Spiral Text và Clipart Category làm đích không có nhóm token text trong Browse values, không chọn được layer text làm nguồn. Theo CCR QA-3393, TIB-5271 (production 2026-10-26) đổi nhóm thành 'Text, Curve Text, Warp Text & Spiral Text' và cho Spiral làm nguồn. Vế Spiral Text còn đúng không, nên bỏ hay sửa? Vế Clipart Category còn đúng không? Liên quan CHK-054.","kb_ids":["KB-995"],"owner":"Dev","supersedes":"OQ-artwork-463"}
```

## OQ-artwork-render-161 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-161","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"[CBS-115, KB-997, rule QA FACT-096] Rule QA (QA đính chính 2026-10-15, QA-2844) ghi 'Populate X from another option' luôn trỏ tới một layer cụ thể, không bao giờ trỏ trực tiếp tới Global Option; Global Option chỉ là container. Dev xác nhận đây là thiết kế đã chốt? Liên quan CHK-055.","kb_ids":["KB-997"],"owner":"Dev","supersedes":"OQ-artwork-464"}
```

## OQ-artwork-render-162 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-162","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"[CBS-115, KB-998, rule QA FACT-096] Rule QA ghi dropdown nguồn lọc theo type: Content nhận Single-line Text (Paragraph không làm nguồn), Color chỉ layer color (layer text ra 'List is empty' dù set qua API vẫn lưu field), Background chỉ clipart-category/group-clipart-categories. Dev xác nhận? Vế Paragraph không làm nguồn Content còn đúng sau TIB-5271 không? API nhận nguồn sai type là chủ ý hay thiếu validate? Liên quan CHK-056.","kb_ids":["KB-998"],"owner":"Dev","supersedes":"OQ-artwork-465"}
```

## OQ-artwork-render-163 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-163","type":"NEEDS_CONFIRMATION","feature_id":"populate-channels-config","summary":"[CBS-115, KB-999, rule QA FACT-162] Rule QA (2026-10-23, QA-3416 BUG-05) ghi Populate Color của shape/vector/text chỉ trỏ vào một layer Color trong cùng artwork, không có field trỏ Shopify Color variant, nên fixture chỉ cần một layer Color thường. Dev xác nhận? TIB-4726 chưa Passed: khi nào ship, và canvas editor có đồng bộ màu không (claim đồng bộ không nạp vì không nguồn)? Liên quan CHK-057, OQ-artwork-090.","kb_ids":["KB-999"],"owner":"Dev","supersedes":"OQ-artwork-466"}
```

## OQ-artwork-render-164 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-render-164","type":"OPEN_ISSUE","feature_id":"populate-value-tokens","kb_ids":["KB-1025","KB-1026"],"summary":"[CBS-118] KB-1025, KB-1026 (known defect): từ bắt đầu bằng ký tự astral (emoji, chữ toán học) làm {{value.initialofword.X}} và bare {{value.initialofword}} trả nửa surrogate pair, hiển thị glyph vỡ. Emoji trong tên có phải kịch bản thật không, và nếu có thì có mở ticket riêng như dev gợi ý không? 'Giới hạn kế thừa, không phải regression' mới là nhận định của một dev, chưa qua PO. Cần: PO trả lời.","supersedes":"OQ-artwork-503"}
```

## OQ-artwork-render-165 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-165","type":"NEEDS_CONFIRMATION","feature_id":"populate-value-tokens","kb_ids":["KB-1026"],"summary":"[CBS-118] KB-1026: lỗi astral ở bare {{value.initialofword}} có từ trước TIB-5331, không phải regression do nhánh TIB-5331, có đúng không? Chưa ai đối chiếu bare token trước và sau TIB-5331. Cần: Dev xác nhận.","supersedes":"OQ-artwork-504"}
```

## OQ-artwork-render-166 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-166","type":"NEEDS_CONFIRMATION","feature_id":"populate-value-tokens","kb_ids":["KB-1027"],"summary":"[CBS-118] KB-1027: chữ Latin có dấu và tiếng Việt (É, Đ) không bị ảnh hưởng bởi lỗi astral, họ token initialofword lấy đúng chữ đầu — đúng không, với giá trị nhập và kết quả cụ thể nào? Mới là một câu của dev, chưa có test case kiểm độc lập. Cần: Dev xác nhận.","supersedes":"OQ-artwork-505"}
```

## OQ-artwork-render-167 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-167","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","summary":"Run effects có [Gemini] image filter dùng ref image rất lớn (12000x12000) hoàn tất, layer thay bằng ảnh đã lọc, đứng thẳng (KB-1103, PROPOSED): expected là suy luận QA (giả định A3, ngoài QA plan của Dev). Comment Dev TIB-5615 chỉ liệt kê ApplyLayerImageEffectsJob trên image-effect-queue, không nói job này đi qua applyImageFilter(). Dev xác nhận?","kb_ids":["KB-1103"],"needs":"Dev xác nhận ApplyLayerImageEffectsJob dùng applyImageFilter() (ref image cap) và expected của trường hợp này.","supersedes":"OQ-artwork-570"}
```

## OQ-artwork-render-168 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-168","type":"NEEDS_CONFIRMATION","feature_id":"populate-value-tokens","summary":"[CBS-106, TIB-5609] Populate từ Star Map (KB-1109, OBSERVED_CURRENT/LOW): Star Map chưa set format vẫn cho {{time}} = yyyy-MM-dd HH:mm (mặc định ghi theo TIB-4913, chưa có nguồn trích), Moon Phase {{date}} và Route {{route_start_date}} không đổi, text layer đích Input type Date picker nhận ngày ISO và hiện theo format của chính nó — Dev xác nhận? {{name}}/{{lat}} của Star Map có đổi không (chưa kiểm)?","kb_ids":["KB-1109"],"needs":"Dev xác nhận nguyên văn có ngày; lượt chạy có fixture {{name}}/{{lat}}.","supersedes":"OQ-artwork-574"}
```

## OQ-artwork-render-169 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-render-169","type":"NEEDS_CONFIRMATION","feature_id":"image-effects-run","kb_ids":["KB-1120"],"check_ids":[],"owner":"Dev","summary":"[CBS-163] Run effects tới khi xong: layer nhận ảnh kết quả, response trạng thái lượt chạy có status và layer_image (id, url, thumbnail, width, height), không user_id (KB-1120, một lượt staging, build không ghi): Dev xác nhận là expected? error_message có mặt (null) khi lượt chạy thành công không?","supersedes":"OQ-artwork-579"}
```
