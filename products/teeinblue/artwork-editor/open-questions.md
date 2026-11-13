# Open Questions — artwork-editor

## OQ-artwork-editor-001 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-001","type":"CONFLICT","feature_id":"layer-duplicate-link-copy","summary":"An earlier assumption that linked-layer copies are marked with a chain icon on the layer row was checked directly and found false.","side_a":"Assumption going into the run: a layer duplicated via 'Duplicate & Link options' shows a chain icon before its name on the layer row.","side_b":"Direct observation across 35 layer types: the layer row icon set is always the same 5 fixed icons regardless of linked state; the only real signal that a layer is a linked copy is the config panel collapsing to just the LINKED LAYER + EXTRA accordions.","supersedes":"OQ-artwork-003"}
```

## OQ-artwork-editor-002 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-002","type":"CONFLICT","feature_id":"editor-layer-workspace","summary":"Two different-quality sources disagree on how many of the 35 layer types have a 'custom_class' field: code-derived list says 29, direct UI observation says 33.","side_a":"Code-derived (bundle-registry, INFERRED): exactly 29 specific data-types carry a custom_class field.","side_b":"Direct DOM observation across all 35 layer type config panels: the 'Custom class:' field renders on 33/35 types (absent only on Static Image and Static Vector).","supersedes":"OQ-artwork-006"}
```

## OQ-artwork-editor-003 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-003","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Ungroup luôn disabled trong mọi sample nguồn vì chưa từng có group nào được tạo — chưa test được cặp Group/Ungroup end-to-end dù đây là action chính trên action bar.","supersedes":"OQ-artwork-045"}
```

## OQ-artwork-editor-004 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-004","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Chỉ test 1 account/1 plan (Blue Test) trong cả 3 run — chưa biết danh sách layer type có phụ thuộc plan/feature-flag không.","supersedes":"OQ-artwork-046"}
```

## OQ-artwork-editor-005 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-005","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"KB-015 chỉ test riêng thư viện Vector — chưa rõ đây là hành vi chung cho mọi picker cần asset hay đặc thù riêng Vector.","supersedes":"OQ-artwork-047"}
```

## OQ-artwork-editor-006 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-006","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"CONF-006 UNRESOLVED: 2 nguồn evidence khác loại (code-derived INFERRED 29 type vs UI observed 33 type) không khớp phạm vi — cần đối chiếu chéo trực tiếp từng type trong 9 type chênh lệch để xác định nguồn nào đúng, hoặc cả 2 đều đúng theo nghĩa khác nhau.","supersedes":"OQ-artwork-048"}
```

## OQ-artwork-editor-007 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-007","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Đây là hành vi cốt lõi được message UI khẳng định ('Design and personalization are synced from it') nhưng CHƯA được test end-to-end trong 3 run nguồn — chỉ xác nhận trạng thái NGAY SAU KHI tạo, chưa test sync thực sự qua 1 vòng sửa-lại-gốc.","supersedes":"OQ-artwork-081"}
```

## OQ-artwork-editor-008 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-008","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Chưa rõ quy luật vì sao đúng 15/35 type rơi vào PLAIN_COPY — theo nhóm layer (form-elements/AI/upload) hay theo implementation riêng lẻ từng type — không dự đoán được cho layer type mới.","supersedes":"OQ-artwork-082"}
```

## OQ-artwork-editor-009 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-009","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"KB-020/KB-022 chỉ có full body cho 1 sample không chứa layer linked — chưa có oracle ở tầng API cho trạng thái linked, chỉ có oracle UI (accordion LINKED LAYER).","supersedes":"OQ-artwork-083"}
```

## OQ-artwork-editor-010 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-010","type":"NEEDS_CONFIRMATION","feature_id":"group-layer-effective-visibility","summary":"Group ẩn: mục Mask/nút Edit mask biến mất khỏi quick toolbar (quan sát TC-TIB-6060, 2026-10-16) trong khi expectedResult của case và R16 trong file RA/đáp án Slack Q6d (không ghi người trả lời) ghi 'disable'. Cần PO chốt: ẩn hay disable. Ghi chú QA local cũ (2026-09-30: Group ẩn vẫn có Edit mask) đã lỗi thời và không thuộc KB base.","kb_ids":["KB-167"],"supersedes":"OQ-artwork-138"}
```

## OQ-artwork-editor-011 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-editor-011","type":"OPEN_ISSUE","feature_id":"group-layer-effective-visibility","summary":"Render phía server (print file / render-design-preview) cho layer hoặc Group thiếu key visible chưa được đối chiếu — bước 3 của TC-TIB-6055 không chạy (không có tool server-side trong phiên). KB-166 chỉ phủ canvas editor + Live preview portal.","kb_ids":["KB-166"],"supersedes":"OQ-artwork-139"}
```

## OQ-artwork-editor-012 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-editor-012","type":"OPEN_ISSUE","feature_id":"group-layer-effective-visibility","summary":"Q11 (treo): fixture 'Group ẩn + con visible:true' dùng cho phần lớn test case được dựng qua MCP/API, chưa được PO/dev xác nhận là dữ liệu hợp lệ; repair command artwork:show-hidden-groups-with-visible-children đã chạy nên dữ liệu thật có thể không còn trạng thái này.","kb_ids":["KB-158","KB-159","KB-162","KB-163","KB-168"],"supersedes":"OQ-artwork-140"}
```

## OQ-artwork-editor-013 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-editor-013","type":"OPEN_ISSUE","feature_id":"group-layer-effective-visibility","summary":"Q10(b) (treo): Artwork 1.0 có hỗ trợ Group không — chưa thử; các item về effective visibility của run này chỉ phủ Artwork 2.0.","kb_ids":["KB-158"],"supersedes":"OQ-artwork-141"}
```

## OQ-artwork-editor-014 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-editor-014","type":"OPEN_ISSUE","feature_id":"group-layer-effective-visibility","summary":"Các mục 'Not for QA' trong QA plan của dev (#54766) chưa có test và không được nạp: dependency trên Group bị bỏ qua; layer trỏ tới Group không tồn tại render ở top level; MCP form preview khớp storefront form; command repair artwork:show-hidden-groups-with-visible-children.","kb_ids":["KB-158","KB-168"],"supersedes":"OQ-artwork-142"}
```

## OQ-artwork-editor-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-015","type":"NEEDS_CONFIRMATION","feature_id":"group-layer-effective-visibility","summary":"Ẩn hết mọi con thì Group vẫn ON và canvas không vẽ gì — hành vi có đúng như QA plan dev khi chạy TC-TIB-6159/6160 không?","kb_ids":["KB-161"],"supersedes":"OQ-artwork-143"}
```

## OQ-artwork-editor-016 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-editor-016","type":"OPEN_ISSUE","feature_id":"group-layer-effective-visibility","summary":"TIB-5584 đã deploy production ở bản release nào, và hành vi có giữ nguyên trên build sau khi 3 PR còn mở lúc 16:14 16/10 được merge không?","kb_ids":["KB-158","KB-159","KB-162","KB-168"],"supersedes":"OQ-artwork-144"}
```

## OQ-artwork-editor-017 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-017","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Group ẩn: quick toolbar vẫn hiển thị mục Align với 6 nút không disable, bấm không tác dụng (TC-TIB-6058/6059, staging 2026-10-16). QA plan dev (#54766 mục A bước 6) ghi 'quick toolbar offers no transform or align' và expectedResult TC-TIB-6059 ghi 'Align không khả dụng'. Quan sát cùng lượt: quick toolbar của Group ẩn không thấy Print Effects và Mask (KB-170). Cần PO chốt khi Group ẩn thì Align và Print Effects nên ẩn, disable hay hiển thị (Mask hỏi riêng ở OQ-artwork-138). Không phải conflict với KB base (KB-042 không nói về Group ẩn).","kb_ids":["KB-170"],"supersedes":"OQ-artwork-145"}
```

## OQ-artwork-editor-018 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-018","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Khi Group đang ẩn, chọn một layer con trong layer panel có hiện box transform không, và các hành vi chọn/kéo theo QA plan dev có đúng khi chạy TC-TIB-6161/6162 không?","kb_ids":["KB-171","KB-172"],"supersedes":"OQ-artwork-146"}
```

## OQ-artwork-editor-019 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-019","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"layer_display chỉ đặt ở Group (con null, dữ liệu tạo qua JSON/API) thì storefront không áp cascade — đây là hành vi đúng (dữ liệu ngoài đường editor không được hỗ trợ) hay lỗi?","kb_ids":["KB-175"],"supersedes":"OQ-artwork-147"}
```

## OQ-artwork-editor-020 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-editor-020","type":"OPEN_ISSUE","feature_id":"editor-layer-workspace","summary":"Print file (order design) của Group đặt display 'Design only' có chứa nội dung con như kỳ vọng không?","kb_ids":["KB-174"],"supersedes":"OQ-artwork-148"}
```

## OQ-artwork-editor-021 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-021","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Trên build đã merge, import artwork, copy/paste layer (trong artwork và sang artwork 2.0 khác) và global template replica có giữ action Hide không; import từ file export định dạng v1 xử lý action thế nào? Chỉ có nguồn tài liệu dev, chưa test case nào chạy.","kb_ids":["KB-230"],"supersedes":"OQ-artwork-156"}
```

## OQ-artwork-editor-022 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-editor-022","type":"OPEN_ISSUE","feature_id":"layer-duplicate-link-copy","summary":"'Duplicate & Link options' trên layer có action Hide: bản LINKED/PLAIN_COPY có mang action và điều kiện của layer gốc không? Chưa có evidence cho chính thao tác này với layer Hide.","kb_ids":["KB-230"],"supersedes":"OQ-artwork-157"}
```

## OQ-artwork-editor-023 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-023","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Role áp dụng của KB-420..KB-429 là gì (owner, staff hay buyer), cho từng item? scope.role đang là \"unspecified\" vì CCR ghi không rõ, checklist chưa biết chạy các item này với role nào. Câu hỏi chung cho ba feature: layer-config-image (KB-420..KB-424, CHK-054..CHK-059), layer-print-effects (KB-425, CHK-011, CHK-012), editor-layer-workspace (KB-426..KB-429, CHK-019..CHK-023).","kb_ids":["artwork-layer-config/photo-upload-layer-config#KB-420","artwork-layer-config/photo-upload-layer-config#KB-421","artwork-layer-config/photo-upload-layer-config#KB-422","artwork-layer-config/clipart-layer-config#KB-423","artwork-layer-config/gen-ai-layer-config#KB-424","artwork-render/print-design-render#KB-425","KB-426","KB-427","KB-428","KB-429"],"supersedes":"OQ-artwork-184"}
```

## OQ-artwork-editor-024 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-editor-024","type":"OPEN_ISSUE","feature_id":"editor-layer-workspace","summary":"KB-415..KB-429 chưa biết build và ngày deploy production. TIB-5212, TIB-5465, TIB-5516 là Done trên Jira, Done không chứng minh đã lên production; bản đối chiếu không ghi status của TIB-5512, TIB-5534, TIB-5538, TIB-5539. Trong lúc đó các item chỉ dùng cho staging. Áp cho bảy feature có item mới của CBS-079, không riêng layer-config-image.","kb_ids":["artwork-layer-config/special-layer-config#KB-415","artwork-layer-config/text-layer-config#KB-416","artwork-layer-config/vector-layer-config#KB-417","artwork-layer-config/vector-layer-config#KB-418","artwork-layer-config/special-layer-config#KB-419","artwork-layer-config/photo-upload-layer-config#KB-420","artwork-layer-config/photo-upload-layer-config#KB-421","artwork-layer-config/photo-upload-layer-config#KB-422","artwork-layer-config/clipart-layer-config#KB-423","artwork-layer-config/gen-ai-layer-config#KB-424","artwork-render/print-design-render#KB-425","KB-426","KB-427","KB-428","KB-429"],"supersedes":"OQ-artwork-185"}
```

## OQ-artwork-editor-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-025","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"PO xác nhận ý định của KB-427: khi multi-select có giá trị Photo Border khác nhau, bật toggle Border thay các giá trị riêng của mọi layer đang chọn, và đổi một thuộc tính cũng bật border cho cả selection. Liên quan CHK-020.","kb_ids":["KB-427"],"supersedes":"OQ-artwork-193"}
```

## OQ-artwork-editor-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-026","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Rule \"chọn một group: ẩn Photo Border, Shadow và HD vẫn hiện\" của KB-429 có áp cho Group đang ẩn không? KB-429 không nêu trạng thái group; KB-170 quan sát Group ẩn chỉ còn mục Align, expected của trường hợp đó chưa chốt. CHK-022 chỉ kiểm Group hiện, chưa check nào assert Group ẩn.","kb_ids":["KB-429","KB-170"],"supersedes":"OQ-artwork-194"}
```

## OQ-artwork-editor-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-027","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-881: chọn 1 layer mở được Bulk edit; selection chỉ locked hoặc chỉ replica thì mục \"Bulk edit\" có nhưng disabled (lượt 2026-10-22 replica-only còn ẩn); selection lẫn editable + locked + replica chỉ ghi layer editable. Đây có phải hành vi đúng, disabled hay ẩn? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-881"],"supersedes":"OQ-artwork-270"}
```

## OQ-artwork-editor-028 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-028","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-882: chữ header / mô tả / footer (không dấu chấm), nút Cancel / Save, accordion đầu mở sẵn, rộng 620 px của modal Bulk edit chỉ là quan sát TC-07/08. Đây có phải chữ và bố cục chuẩn không? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-882"],"supersedes":"OQ-artwork-271"}
```

## OQ-artwork-editor-029 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-029","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-884: ghi lại đúng giá trị cũ thì không lỗi, 1 undo step; Cancel / Esc / click ngoài modal không ghi, không thêm undo step — chỉ quan sát 2026-10-23 trên build cũ. Đây có phải hành vi đúng trên build cuối? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-884"],"supersedes":"OQ-artwork-272"}
```

## OQ-artwork-editor-030 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-030","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-886: Populate Content (và Populate Color / Background của text) trong modal là radio On / No change / Off, mặc định No change — PO A2 và Dev 55846 không nói về Populate. Đây có phải hành vi đúng? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-886"],"supersedes":"OQ-artwork-273"}
```

## OQ-artwork-editor-031 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-031","type":"CONFLICT","feature_id":"layer-bulk-edit","summary":"\"Personalization for this layer\" trong modal Bulk edit: PO A2 (49367, 2026-08-28) yêu cầu segmented control On / – / Off; Dev (55846, 2026-10-28) + TC-15 cho thấy vẫn là radio 3 lựa chọn, không có No change, và đã hỏi lại PO (PENDING-02). Cần: PO trả lời câu hỏi của Dev ở comment 55846: giữ radio-rỗng-là-no-change hay đổi UI sang tri-state thật.","kb_ids":["KB-887","KB-888"],"conflict_group":"CONF-CBS-092-03","side_a":"KB-887 (INFERRED, LOW): PO A2 comment 49367 (2026-08-28) — Personalization phải là segmented control On / – / Off.","side_b":"KB-888 (OBSERVED_CURRENT, LOW): Dev 55846 (2026-10-28) + TC-15 — radio 3 lựa chọn, không có No change; chỉ Cancel quay lại trạng thái không chọn.","supersedes":"OQ-artwork-274"}
```

## OQ-artwork-editor-032 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-032","type":"CONFLICT","feature_id":"layer-bulk-edit","summary":"Layer linked khi bulk edit setting ngoài Conditional: TC-43 (2026-10-30) thấy LK1 giữ linked và form_label không đổi; Dev 49205 C3 (2026-08-27) nói các setting khác vẫn áp bình thường; Dev 55846 chỉ nói đã fix \"layer Link bị patch nhầm\". Cần: Dev hoặc PO nói rõ: sau fix 2026-10-28, setting ngoài Conditional có còn ghi lên layer linked không.","kb_ids":["KB-890","KB-891"],"conflict_group":"CONF-CBS-092-04","side_a":"KB-890 (OBSERVED_CURRENT, LOW): TC-43 — layer linked giữ customization_type linked, form_label không đổi.","side_b":"KB-891 (INFERRED, LOW): Dev 49205 C3 — layer linked, các setting khác ngoài Conditional vẫn áp bình thường.","supersedes":"OQ-artwork-275"}
```

## OQ-artwork-editor-033 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-033","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-893: danh sách field theo tổ hợp layer type (Text + Paragraph, 5 text type, cùng type clipart, Text + Clipart) chỉ là quan sát TC-16..19, một phần trên build cũ. Đây có phải tập field đúng không? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-893"],"supersedes":"OQ-artwork-276"}
```

## OQ-artwork-editor-034 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-034","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-896: panel Conditional Setting hiện khi ≥1 layer hỗ trợ; rule ghi cho mọi layer hỗ trợ, bỏ qua Dynamic Clipart by Text; rule cũ bị thay (mới thấy 1 layer, TC-42 chưa xong). Đây có phải hành vi đúng? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối. TC-42 chạy đủ bước xoá rule và undo.","kb_ids":["KB-896"],"supersedes":"OQ-artwork-277"}
```

## OQ-artwork-editor-035 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-035","type":"CONFLICT","feature_id":"layer-bulk-edit","summary":"Vector category trong Design settings của Bulk edit: TC-26 (2026-10-22, build cũ) thấy \"Select one vector category\" + default value; Dev 49205 C5 (2026-08-27) nói Design settings chỉ gồm text, clipart, grouped_clipart, default_value. PENDING-01 chưa ai trả lời. Cần: Dev hoặc PO trả lời PENDING-01: vector category có thuộc scope Bulk edit không; chạy lại TC-26 trên build cuối kèm reset default.","kb_ids":["KB-906","KB-907"],"conflict_group":"CONF-CBS-092-05","side_a":"KB-906 (OBSERVED_CURRENT, LOW): TC-26 — V1 + V2 có field vector category.","side_b":"KB-907 (INFERRED, LOW): Dev 49205 C5 — Design settings chỉ gồm text, clipart, grouped_clipart, default_value.","supersedes":"OQ-artwork-278"}
```

## OQ-artwork-editor-036 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-036","type":"CONFLICT","feature_id":"layer-bulk-edit","summary":"Danh sách nguồn Populate trong Bulk edit: TC-31 (2026-10-30, build index.BMgdZMSW.js) thấy loại mọi layer đang chọn (\"List is empty.\"); dev summary 49895 (2026-09-04) và QA 2026-10-29 (build index.acNZihq9.js) thấy chỉ loại layer đầu tiên. Không ai xác nhận thay đổi giữa 2 build. Cần: Dev xác nhận đã đổi logic nguồn Populate giữa 2 build (có ngày), hoặc PO nói hành vi đúng.","kb_ids":["KB-901","KB-902"],"conflict_group":"CONF-CBS-092-06","side_a":"KB-901 (OBSERVED_CURRENT, LOW): TC-31 — nguồn loại mọi layer đang chọn.","side_b":"KB-902 (OBSERVED_CURRENT, LOW): dev summary 49895 + QA 2026-10-29 — chỉ loại layer đầu tiên của selection.","supersedes":"OQ-artwork-279"}
```

## OQ-artwork-editor-037 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-037","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"KB-903: Populate values + \"Use an existing global option\" set trong cùng 1 Save đều được ghi (global_option + retrieval_value_enabled / retrieval_layer), quan sát TC-31 2026-10-30. Đây có phải hành vi đúng? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối.","kb_ids":["KB-903"],"supersedes":"OQ-artwork-280"}
```

## OQ-artwork-editor-038 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-038","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"Khi selection không có setting chung: mục Bulk edit trên menu có vẫn bật không, và nút Save có bị disable không? Chỉ dev summary 49895 nói, chưa ai thấy (vế bị bỏ của CLAIM-20; empty state ở KB-904). Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối. Hoặc dựng được tổ hợp layer thật dẫn tới empty state (TC-22).","kb_ids":[],"supersedes":"OQ-artwork-281"}
```

## OQ-artwork-editor-039 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-039","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"Chọn group layer: layer con có được chọn theo và nhận Bulk edit, group không bị ghi, header đếm cả group không? Chỉ quan sát 1 lượt TC-04 2026-10-22 build cũ; Dev 49205 A3 nói selection loại layer group; PO chưa quyết PENDING-05. Không nạp KB. Cần: PO quyết PENDING-05; Dev xác nhận hành vi chọn group trên build cuối.","kb_ids":[],"supersedes":"OQ-artwork-282"}
```

## OQ-artwork-editor-040 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-040","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"Default text set qua Bulk edit có điền sẵn vào ô nhập storefront không; modal có cần field \"Prefill default text\" (autofill_default_value) như panel single-layer không? Chỉ quan sát TC-30 (chưa PASS, expected khác). Không nạp KB. Cần: PO hoặc Dev xác nhận nguyên văn, có ngày. TIB-5236 chỉ là ngữ cảnh regression, không phải nguồn.","kb_ids":[],"supersedes":"OQ-artwork-283"}
```

## OQ-artwork-editor-041 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-041","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"Known limitation theo dev summary 49895: field cùng tên nhưng khác kiểu giữa các layer type bị loại khỏi modal Bulk edit, không thông báo. PENDING-04 chưa trả lời, QA chưa thử. Không nạp KB. Cần: Dev hoặc PO trả lời PENDING-04; QA chạy tổ hợp layer có field cùng tên khác kiểu.","kb_ids":[],"supersedes":"OQ-artwork-284"}
```

## OQ-artwork-editor-042 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-042","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Option title và Add instruction được chèn như HTML trên form storefront và form preview portal (<b>, <img> hiện thật; <script>, onerror bị bỏ) — quan sát TC-35, có từ trước TIB-5299; Dev 55846 chỉ nói không liên quan ticket. Đây là defect (khả năng bảo mật) hay hành vi chấp nhận? Không nạp KB. Cần: PO hoặc Dev nói rõ đúng/sai; nếu là defect thì ticket theo dõi. Không tự tạo issue Jira, hỏi operator trước.","kb_ids":[],"supersedes":"OQ-artwork-285"}
```

## OQ-artwork-editor-043 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-043","type":"CONFLICT","feature_id":"editor-layer-workspace","summary":"Menu overflow trên layer action bar: KB-043 (bootstrap 2026-09-10) ghi action bar không có menu '...'; KB-085 (layer-config-image, bootstrap 2026-09-21) ghi panel cấu hình chỉ tiếp cận qua '...' > 'Bulk edit', không có panel single-layer; KB-908 (TC-01 2026-10-30) ghi menu More (…) có Bulk edit đứng đầu + Replace image layer, Link with another layer, Convert to another layer, 6 mục bulk cũ không còn. Cần: Operator/owner quyết resolve (supersede tắt ở teeinblue); run explore hoặc test case có căn cứ expected đọc lại action bar và panel single-layer trên build cuối; cập nhật CHK-005, CHK-015 theo kết quả. Ghi chú thêm: KB-043 và KB-085 đã lệch nhau từ base về việc có menu '...' hay không, KB-908 cùng chiều KB-085 ở điểm đó; KB-908 không nói gì về panel single-layer. Check mất oracle: CHK-005, CHK-024 (editor-layer-workspace), CHK-015 (layer-config-image). [CBS-113] Bổ sung KB-1037 (TIB-5211, 2026-07-20, nguồn sớm hơn KB-043) và KB-1038 vào side_b; CHK-020 (layer-duplicate-link-copy) chờ resolve.","kb_ids":["KB-043","artwork-layer-config/clipart-layer-config#KB-085","KB-908","artwork-editor/layer-duplicate-link-copy#KB-1037","artwork-editor/layer-duplicate-link-copy#KB-1038"],"conflict_group":"CONF-CBS-092-01","side_a":"KB-043 (OBSERVED_CURRENT, MEDIUM, 2026-09-10): không có menu overflow (CHK-005); KB-085 (OBSERVED_CURRENT, LOW, 2026-09-21): panel cấu hình chỉ qua '...' > 'Bulk edit', không panel single-layer (CHK-015).","side_b":"KB-908 (OBSERVED_CURRENT, LOW, CBS-092 CLAIM-01, TC-01 2026-10-30): menu More (…) có Bulk edit đứng đầu + 3 mục; 6 mục bulk cũ không còn. [CBS-113] Thêm cùng phía: KB-1037 (CONFIRMED_EXPECTED, LOW, UNRESOLVED; spec_doc Jira TIB-5211 description mục Solution, 2026-07-20: 'Convert to another layer' nằm trong menu '...' More actions của layer toolbar) và KB-1038 (PROPOSED, rule QA FACT-038 2026-09-04: link layer sẵn có qua '...' → 'Link with another layer') ở layer-duplicate-link-copy.","check_ids":["CHK-005","CHK-024","CHK-015","artwork-editor/layer-duplicate-link-copy#CHK-020"],"supersedes":"OQ-artwork-286"}
```

## OQ-artwork-editor-044 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-044","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"KB-908: nội dung và nhãn menu More (…) (Bulk edit, Replace image layer, Link with another layer, Convert to another layer; Artwork 1.0 vẫn ghi \"Share with another layer\") chỉ là quan sát TC-01, khác nhãn trong TC expected và ticket. Đây có phải nội dung và nhãn đúng? Cần: PO hoặc Dev xác nhận nguyên văn, có ngày (Jira TIB-5299), hoặc test case PASS có căn cứ expected trên build cuối. [CBS-113] Rule QA FACT-038 (2026-09-04, KB-1038, PROPOSED) dùng mục 'Link with another layer' của menu '...' làm entry point link một layer sẵn có vào origin ở Artwork 2.0; cần Dev xác nhận cùng câu hỏi này.","kb_ids":["KB-908","artwork-editor/layer-duplicate-link-copy#KB-1038"],"supersedes":"OQ-artwork-287"}
```

## OQ-artwork-editor-045 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-045","type":"CONFLICT","feature_id":"editor-layer-workspace","summary":"Bar hành động khi selection có replica Global Template: KB-042 (bootstrap 2026-09-10) ghi bar Deselect/Group/Duplicate/Delete không đổi theo loại/số lượng layer chọn; KB-909 (Dev 55846, 2026-10-28) nói cờ canMutate chặn Group / Duplicate / Delete khi selection có replica. Sample của KB-042 không có replica nên có thể chỉ khác state. Cần: Operator/owner quyết resolve (supersede tắt); đọc lại action bar với selection có replica trên build cuối; cập nhật CHK-006 theo kết quả. Ghi chú thêm: KB-909 và KB-042 có thể chỉ khác state (sample của KB-042 không có replica); nếu PO xác nhận khác state thì là item mới, không phải mâu thuẫn. Check mất oracle: CHK-002, CHK-003, CHK-004, CHK-006, CHK-025.","kb_ids":["KB-042","KB-909"],"conflict_group":"CONF-CBS-092-02","side_a":"KB-042 (OBSERVED_CURRENT, MEDIUM, 2026-09-10): bar hành động không đổi theo loại/số lượng layer chọn (CHK-006).","side_b":"KB-909 (CONFIRMED_EXPECTED, LOW, UNRESOLVED; po_dev_confirm Dev 55846 2026-10-28): replica → canMutate chặn Group / Duplicate / Delete.","check_ids":["CHK-002","CHK-003","CHK-004","CHK-006","CHK-025"],"supersedes":"OQ-artwork-288"}
```

## OQ-artwork-editor-046 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-046","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Live Preview trong portal artwork editor dùng teeinblue-sdk qua git submodule src/sdk, chỉ có fix TIB-5412 sau khi submodule được bump riêng (note Dev TIB-5412 comment 51755, 2026-09-23). Submodule đã được bump chưa? Không nạp KB. Cần: Dev xác nhận đã bump submodule src/sdk (commit/PR, có ngày).","kb_ids":[],"supersedes":"OQ-artwork-290"}
```

## OQ-artwork-editor-047 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-047","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","kb_ids":["KB-883","KB-897"],"summary":"Hai hành vi ghi đè hàng loạt được publish với cờ rủi ro cao: chạm field rồi để rỗng thì ghi rỗng cho mọi layer đã chọn (KB-883); đổi clipart category / group mà không chạm Default value thì default_value thành null trên mọi layer đã chọn (KB-897). Cả hai có nguồn Dev và đang làm oracle cho check P1. Mức HIGH là đánh giá của bước diff. Cần: PO xác nhận đây là ý định sản phẩm (ghi đè không cảnh báo).","supersedes":"OQ-artwork-291"}
```

## OQ-artwork-editor-048 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-048","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","kb_ids":["KB-880"],"summary":"Quyền: staff không có quyền Manage Artwork có thấy / dùng được Bulk edit không? TC-06 chưa chạy, chưa có item nào về quyền (CHK-026 là gap). Cần: account staff không có quyền do operator cấp, hoặc PO/Dev xác nhận nguyên văn có ngày.","supersedes":"OQ-artwork-292"}
```

## OQ-artwork-editor-049 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-049","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","kb_ids":["KB-898"],"summary":"Redo sau Undo của một lượt Bulk edit: TC-28 thấy Redo khôi phục toàn bộ, nhưng PO C1 (49367) chỉ nói về Undo. Cần: PO/Dev xác nhận Redo là một bước khôi phục toàn bộ lượt bulk edit.","supersedes":"OQ-artwork-293"}
```

## OQ-artwork-editor-050 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-050","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","kb_ids":["KB-042"],"summary":"KB-042 có hai vế: canvas toolbar đổi theo loại layer (không bị tranh chấp) và bar hành động không đổi theo selection (bị KB-909 tranh chấp). Vì conflict ở mức item, CHK-002, CHK-003, CHK-004 (chỉ dùng vế canvas toolbar) cũng mất oracle. Cần: khi PO quyết CONF-CBS-092-02 (OQ-artwork-288), quyết luôn có tách KB-042 thành hai item để trả oracle cho CHK-002..004 không.","check_ids":["CHK-002","CHK-003","CHK-004"],"supersedes":"OQ-artwork-294"}
```

## OQ-artwork-editor-051 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-051","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","kb_ids":["KB-884","KB-893","KB-906"],"summary":"Mọi test case của QA-3419 là kết quả AI do máy chạy, chỉ trên staging; một số lượt (TC-18, TC-19, TC-26, TC-12/13/40) chạy trên build cũ index.BqS1iTCG.js, không phải build cuối index.BMgdZMSW.js. TIB-5299 Done nhưng production chưa có quan sát. Cần: chạy lại các TC này trên build cuối và quan sát production.","supersedes":"OQ-artwork-296"}
```

## OQ-artwork-editor-052 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-052","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-010 “Effect thật của Group/Ungroup sau khi bấm” của feature editor-layer-workspace. missing_or_unresolved_oracle","supersedes":"OQ-artwork-381"}
```

## OQ-artwork-editor-053 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-053","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011 “35 layer type trong popup có cố định qua các plan khác nhau không” của feature editor-layer-workspace. missing_or_unresolved_oracle","supersedes":"OQ-artwork-382"}
```

## OQ-artwork-editor-054 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-054","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-012 “Picker khác (image library, clipart) có rơi vào trạng thái rỗng tương tự Vector không” của feature editor-layer-workspace. missing_or_unresolved_oracle","supersedes":"OQ-artwork-383"}
```

## OQ-artwork-editor-055 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-055","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006 “Field 'Custom class:' có ở 33/35 type theo DOM (mâu thuẫn với bundle-registry code — CONF-006)” của feature layer-common-config. missing_or_unresolved_oracle","supersedes":"OQ-artwork-384"}
```

## OQ-artwork-editor-056 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-056","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Đối chiếu chéo trực tiếp 9 layer type nằm ngoài bundle-registry nhưng có 'Custom class' trên DOM” của feature layer-common-config. missing_or_unresolved_oracle","supersedes":"OQ-artwork-385"}
```

## OQ-artwork-editor-057 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-057","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-001 “Nút 'Duplicate & Link options' luôn hiện diện, tên giống nhau mọi layer type” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle","supersedes":"OQ-artwork-428"}
```

## OQ-artwork-editor-058 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-058","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “20 layer type nhóm LINKED — config panel rút gọn còn 2 accordion sau khi Duplicate & Link” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle","supersedes":"OQ-artwork-429"}
```

## OQ-artwork-editor-059 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-059","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-003 “15 layer type nhóm PLAIN_COPY — giữ nguyên đầy đủ accordion sau khi Duplicate & Link” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle","supersedes":"OQ-artwork-430"}
```

## OQ-artwork-editor-060 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-060","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-004 “Duplicate & Link options không sinh network request (client-side cho tới Save)” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle","supersedes":"OQ-artwork-431"}
```

## OQ-artwork-editor-061 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-061","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-005 “Layer row của bản LINKED KHÔNG có icon chain — icon set luôn cố định 5 icon (CONF-003)” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle","supersedes":"OQ-artwork-432"}
```

## OQ-artwork-editor-062 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-062","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006 “Sau Save, sửa layer gốc có thực sự đồng bộ (sync) sang bản LINKED không” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle","supersedes":"OQ-artwork-433"}
```

## OQ-artwork-editor-063 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-063","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “Layer type chưa test rơi vào nhóm LINKED hay PLAIN_COPY khi Duplicate & Link” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle","supersedes":"OQ-artwork-434"}
```

## OQ-artwork-editor-064 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-064","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Shape JSON của layer LINKED trong PUT body (field đánh dấu linked/source_layer_id)” của feature layer-duplicate-link-copy. missing_or_unresolved_oracle","supersedes":"OQ-artwork-435"}
```

## OQ-artwork-editor-065 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-065","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","summary":"[CBS-117, KB-1001] Mô tả của dev trong description TIB-5397 (2026-09-03) ghi Artwork 2.0 khi chọn nhiều layer ở Apply for Individual: ô Width hiện width chung hoặc Mixed khi các layer khác width, và group width tính lại từ bounding box của selection sau mỗi lần đổi width của layer bất kỳ. Dev/PO xác nhận đây là hành vi mong muốn? Bản tóm tắt của QA ghi 'Width hiện width thật của từng layer' — câu nào đúng? Liên quan CHK-001, CHK-002.","kb_ids":["KB-1001"],"owner":"Dev","supersedes":"OQ-artwork-467"}
```

## OQ-artwork-editor-066 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-066","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","summary":"[CBS-117, KB-1002] Change note của dev trên TIB-5397 (2026-09-10) ghi Artwork 1.0 bỏ hẳn Apply for: Group / Individual khỏi Transform popover, multi-select chỉ còn Width/Height/Top/Left/Rotate/Fit to canvas/Flip như trước TIB-5197, seller 1.0 đặt auto-scale max width theo từng layer. PO xác nhận đây là hành vi mong muốn của Artwork 1.0? Liên quan CHK-003.","kb_ids":["KB-1002"],"owner":"PO","supersedes":"OQ-artwork-468"}
```

## OQ-artwork-editor-067 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-067","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":[],"summary":"[CBS-117] CLAIM-04 (S0, không nạp KB): số đo QA trên fixture Artwork 1.0 staging 2026-09-16 ghi Undo/Redo 1 bước cho cả nhóm, Fit to canvas neo top-left (không căn giữa, ghi là cả 1.0 lẫn 2.0), Flip ở Artwork 1.0 lật ảnh từng layer tại chỗ (không group-mirror), ô số 0/âm/rỗng/chữ không đổi layer nhưng ô vẫn hiện giá trị đó, 99999/12.5/1e3 được chấp nhận. Đây có phải hành vi mong muốn không? Không có nguồn PO/Dev. Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected; hoặc locator rule QA có path trong repo QA.","owner":"Dev","supersedes":"OQ-artwork-469"}
```

## OQ-artwork-editor-068 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-068","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":[],"summary":"[CBS-117] CLAIM-05 (S0, không nạp KB): kết quả test local ghi Artwork 1.0 không vẽ box cá nhân (.artwork-layer-frame) dù account đang lưu preference Individual, sau khi fix bug nội bộ BUG-127; ghi chú cũ 'Artwork 1.0 vẫn đọc preference để vẽ box' được coi là lỗi thời. Xác nhận hành vi này, và Artwork 1.0 có cần đọc preference Apply for nữa không? Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected; hoặc locator rule QA có path trong repo QA.","owner":"QA lead","supersedes":"OQ-artwork-470"}
```

## OQ-artwork-editor-069 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-069","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":[],"summary":"[CBS-117] CLAIM-06 (S0, không nạp KB): QA chốt 'Group' trong radio Apply for: Group/Individual nghĩa là coi cả multi-selection trên canvas như một khối, không liên quan loại layer group (container lồng layer con). Dev/PO xác nhận hai khái niệm độc lập? Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected; hoặc locator rule QA có path trong repo QA.","owner":"Dev","supersedes":"OQ-artwork-471"}
```

## OQ-artwork-editor-070 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-070","type":"CONFLICT","feature_id":"transform-multi-select","kb_ids":[],"summary":"[CBS-117] CLAIM-07 (S0, không nạp KB): nhập 0 hoặc số âm vào ô Width/Height/Top/Left của Transform bị bỏ qua hoàn toàn hay clamp về 1px? Số đo cùng lượt QA: nhỏ nhất áp được là 1 (0.5 làm tròn lên 1), 99999 áp cho mọi layer đang chọn không có max, chữ bị input type=number lọc, để trống rồi blur trả về giá trị cũ, ô không gọi API khi blur. Hành vi mong muốn hay lỗi? Cần: Dev xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected.","owner":"Dev","side_a":"Dev dự đoán ở RQ6 (QA-3361, 2026-09-16, chưa có nguyên văn): 0/số âm clamp về 1px.","side_b":"Số đo QA staging 2026-09-16 (QA-3361 TC-35, kết quả local): 0/số âm bị bỏ qua hoàn toàn, ô hiện số vừa gõ nhưng layer không đổi, chọn lại layer thì ô về giá trị cũ.","supersedes":"OQ-artwork-472"}
```

## OQ-artwork-editor-071 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-071","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":[],"summary":"[CBS-117] CLAIM-08 (S0, không nạp KB): kết quả test local ghi preference Apply for: Group/Individual lưu theo account, chỉ đọc lúc load editor, không sync live giữa các tab cùng account; tab đổi mode sau cùng là giá trị cho lần load kế tiếp. Ghi chú 'dev chốt RQ11 2026-09-16' chưa có nguyên văn. Dev xác nhận? Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected; hoặc locator rule QA có path trong repo QA.","owner":"Dev","supersedes":"OQ-artwork-473"}
```

## OQ-artwork-editor-072 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-072","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":[],"summary":"[CBS-117] CLAIM-09 (S0, không nạp KB): QA quan sát Apply for không mặc định Group khi mở popover mà là state per-account để lại từ lần trước (production thấy Individual), nên test phải tự set tường minh. Mặc định thiết kế cho account mới là gì? Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS có ngày, build và căn cứ expected; hoặc locator rule QA có path trong repo QA.","owner":"PO","supersedes":"OQ-artwork-474"}
```

## OQ-artwork-editor-073 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-073","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","kb_ids":["KB-1009"],"summary":"[CBS-127] KB-1009 (rule QA FACT-032): popup Convert to another layer hiện type hiện tại ở dòng 'FROM X TO Y' (.convert-layer-popup__value là type đích chọn sẵn); convert tự áp dụng không cần Save nhưng chỉ ghi vào draft local của browser, GraphQL trả bản cũ tới khi Save; Cancel editor + confirm native thì hoàn lại. Dev xác nhận đây là hành vi chủ ý đã ship? Liên quan CHK-026. Cần: Dev/PO xác nhận nguyên văn có ngày, hoặc test case Testlane PASS kèm căn cứ expected.","supersedes":"OQ-artwork-483"}
```

## OQ-artwork-editor-074 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-074","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","kb_ids":["KB-1010"],"summary":"[CBS-127] KB-1010 (rule QA FACT-048): bộ property cấu hình (design/personalization) của layer khác nhau theo từng layer type, không có danh sách dùng chung; font size ở typography.size lồng bên trong, Word Cloud có font_size_min/max riêng; convert để lại key thừa. Dev xác nhận còn đúng và có schema theo type để đối chiếu không? Rule không chạm 7 field common envelope của KB-055. Liên quan CHK-014 (layer-common-config). Cần: Dev xác nhận nguyên văn có ngày.","supersedes":"OQ-artwork-484"}
```

## OQ-artwork-editor-075 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-075","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","kb_ids":["KB-1011"],"summary":"[CBS-127] KB-1011 (rule QA FACT-073): layer vector-family (static-vector, vector-category, vector-upload, legacy vector) không có nút Replace (la-exchange-alt) ở layer row lẫn panel la-pen. PO xác nhận đây là thiết kế đã ship? ('đúng thiết kế' trong rule là lời QA chốt khi test). Vế image-family có Replace chưa nạp, chờ operator quyết cách đọc so với KB-002 (5 icon trên layer row). Liên quan CHK-027. Cần: PO xác nhận nguyên văn có ngày.","supersedes":"OQ-artwork-485"}
```

## OQ-artwork-editor-076 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-076","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","kb_ids":["KB-1012"],"summary":"[CBS-127] KB-1012 (rule QA FACT-074): thumbnail layer vector trong layer panel là file .svg gốc trong img, không có biến thể _thumbnail; tắt cache thì SVG tải 2 lần (canvas + row 28px), bật cache thì lần 2 trúng HTTP cache. Dev xác nhận là thiết kế được chấp nhận? (bug draft đã rút 2026-09-11, chỉ là QA chấp nhận). Liên quan CHK-028. Cần: Dev xác nhận nguyên văn có ngày.","supersedes":"OQ-artwork-486"}
```

## OQ-artwork-editor-077 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-077","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","kb_ids":["KB-1013"],"summary":"[CBS-127] KB-1013 (rule QA FACT-074): SVG thiếu viewBox/kích thước không upload được: POST /api/layer-images/svg trả 500, dropzone hiện '[object Object]' (rule ghi là bug riêng mức Low). Dev xác nhận còn hiện hành không, expected đúng khi từ chối file là gì (status, message), và bug đã có ticket chưa? Liên quan CHK-029. Cần: Dev xác nhận nguyên văn có ngày.","supersedes":"OQ-artwork-487"}
```

## OQ-artwork-editor-078 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-078","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","kb_ids":["KB-1014"],"summary":"[CBS-127] KB-1014 (rule QA FACT-074): layer vector chỉ được thêm vào editor từ storage của TIB, không có nguồn vector bên ngoài. Dev xác nhận? (nguồn chỉ là 'user chốt' trong rule). Liên quan CHK-030. Cần: Dev xác nhận nguyên văn có ngày.","supersedes":"OQ-artwork-488"}
```

## OQ-artwork-editor-079 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-079","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","kb_ids":["KB-1015"],"summary":"[CBS-127] KB-1015 (rule QA FACT-098): trong popup 'Select a layer type' của Artwork 2.0, 'shape text' là layer Paragraph (không phải type riêng) và 'clipart frame' không tồn tại. Dev xác nhận? Liên quan CHK-031. Danh sách 28 type của rule so với 29 item/35 type của KB-001 chưa nạp, chờ operator quyết. Cần: Dev xác nhận nguyên văn có ngày.","supersedes":"OQ-artwork-489"}
```

## OQ-artwork-editor-080 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-080","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","kb_ids":["KB-1016"],"summary":"[CBS-127] KB-1016 (rule QA FACT-140): bấm nút Undo/Redo trên toolbar làm layer đang chọn mất focus (warp-point-handle, chip resize ẩn), còn Cmd/Ctrl+Z thì không. Dev xác nhận đây là hành vi chủ ý hay lỗi, đã ship chưa? Liên quan CHK-032. Cần: Dev xác nhận nguyên văn có ngày.","supersedes":"OQ-artwork-490"}
```

## OQ-artwork-editor-081 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-081","type":"CONFLICT","feature_id":"editor-layer-workspace","kb_ids":[],"summary":"[CBS-127] CLAIM-08 (S0, không nạp KB): TIB đã có layer type 'shape' (Rectangle/Ellipse/Line) chưa, và danh sách layer type hiện hành sau TIB-4726 (Add basic shapes, đang QA Review) gồm những type nào? Hai ghi chép của QA ngược nhau; KB-001 (29 item / 35 data-type, oracle CHK-001/CHK-009) giữ nguyên, không vào conflict_group. Cần: Dev xác nhận nguyên văn có ngày danh sách type hiện hành.","side_a":"Ghi chép QA (CBS-127 CLAIM-08): đo qua MCP schema 2026-09-17 (QA-3361) thấy 33 layer type, không type nào tên shape.","side_b":"Ghi chép QA FACT-158 (2026-10) nêu trong CBS-127: popup type có Rectangle/Ellipse/Line, nhiều khả năng do TIB-4726; base KB-001 ghi 35 data-type.","supersedes":"OQ-artwork-491"}
```

## OQ-artwork-editor-082 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-082","type":"CONFLICT","feature_id":"editor-layer-workspace","kb_ids":[],"summary":"[CBS-127] CLAIM-03 vế b (chưa nạp KB, chờ quyết định): layer image-family (static-photo, photo, clipart-category, group-clipart-categories, dynamic-by-text, legacy clipart) có nút Replace ở đâu — icon la-exchange-alt trên layer row (khi đó layer row có hơn 5 icon), hay chỉ trong panel la-pen / menu More (…)? PO xác nhận thiết kế. KB-002 (object-level, oracle BASELINE nhiều check) giữ nguyên, không vào conflict_group. Cần: PO trả lời nguyên văn có ngày.","side_a":"Rule QA FACT-073 nêu trong CBS-127 (QA chốt 2026-09-11): chỉ image-family có Replace; câu rule ghi vector-family không có Replace 'ở row (la-exchange-alt) lẫn trong panel la-pen', ngụ ý image-family có Replace ở row.","side_b":"Base KB-002 (bootstrap 2026-09-10): layer row của 34/35 type có đúng 5 icon la-eye · la-unlock · la-pen · la-copy · la-trash-alt, không có la-exchange-alt; KB-908 ghi menu More (…) có mục 'Replace image layer'.","supersedes":"OQ-artwork-492"}
```

## OQ-artwork-editor-083 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-083","type":"CONFLICT","feature_id":"editor-layer-workspace","kb_ids":[],"summary":"[CBS-127] CLAIM-07 vế b (chưa nạp KB, chờ quyết định): popup 'Select a layer type' của Artwork 2.0 hiện có bao nhiêu type và gồm những gì — danh sách 28 tên của rule QA hay 29 item / 35 data-type của KB-001, và có thêm Rectangle/Ellipse/Line sau TIB-4726 không? Dev xác nhận danh sách hiện hành. KB-001 (oracle BASELINE của CHK-001, CHK-009) giữ nguyên, không vào conflict_group. Liên quan OQ-artwork-491. Cần: Dev trả lời nguyên văn có ngày.","side_a":"Rule QA FACT-098 nêu trong CBS-127 (QA xác nhận 2026-09-17): danh sách đủ 28 type (Single-line Text, Paragraph, Curve Text, Warp Text, Spiral Text, Static Image, Clipart Category, Photo Upload, Text to Image (AI), Dynamic Clipart by Text, Static Vector, Vector Category, Vector Upload, Street/Route/Star Maps, Moon Phase, Scrabble, Word Search/Cloud, Song Search, Calendar, QR Code, Clock, Toggle Switch, Additional Option, Addon Charge, JSON List, Font, Color).","side_b":"Base KB-001 (bootstrap 2026-09-10): 29 item chia 7 nhóm, 6 item có submenu, tổng 35 data-type; ghi chép FACT-158 (2026-10) nêu trong CBS-127 thấy thêm Rectangle/Ellipse/Line.","supersedes":"OQ-artwork-493"}
```

## OQ-artwork-editor-084 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-084","type":"NEEDS_CONFIRMATION","feature_id":"editor-layer-workspace","kb_ids":["KB-1022"],"summary":"[CBS-143] KB-1022: change note Dev nói convert static-photo chưa có ảnh bị chặn ở cả nút 'Convert to Photo Upload' trên layer và popup 'Convert to another layer'; lượt test chỉ thấy popup. Nút riêng hiện ở đâu / với layer nào (vd layer cần convert type)?","supersedes":"OQ-artwork-499"}
```

## OQ-artwork-editor-085 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-085","type":"CONFLICT","feature_id":"editor-layer-workspace","kb_ids":[],"summary":"[CBS-143] CLAIM-09 (chưa nạp KB, chờ PO quyết AC3 TIB-5446): convert Artwork 1.0 → 2.0 với text layer có background_image — layer tạo ra phải là static-photo có url hay clipart-category có url, và AC3 có tính là đạt với converter hiện tại không? Canon chưa có feature cho convert 1.0 → 2.0. Cần: PO trả lời nguyên văn có ngày.","side_a":"Description TIB-5446 (Dev, 2026-09-15): Root cause #2 nói convert là bug đã xác nhận — layer static-photo tạo từ background của text layer không được gán url khi text layer có background_image; AC3 yêu cầu ra layer static-photo có url.","side_b":"Change note Dev TIB-5446 (2026-11-06, Known limitations): convert Artwork 1.0 có background image đã đúng sẵn trên dev (layer tạo ra có url), không sửa; câu hỏi kèm đọc code trên ticket (2026-10-31) nói layer tạo ra là clipart-category, không phải static-photo.","supersedes":"OQ-artwork-502"}
```

## OQ-artwork-editor-086 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-086","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1032"],"check_ids":["CHK-015"],"summary":"[CBS-113] Rule QA FACT-013/FACT-037 (KB-1032, PROPOSED): Duplicate & Link trên một layer đã là linked copy thì bản mới link về layer origin gốc, không tạo chain và không bị chặn (đã thấy với Word Cloud, Warp Text). Đây có phải rule chung của cơ chế link cho mọi type nhóm LINKED không? Nguồn là kết quả QA/AI trước lần dev sửa TIB-5265 ngày 2026-09-08. CHK-015 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-509"}
```

## OQ-artwork-editor-087 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-087","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1033"],"check_ids":["CHK-016"],"summary":"[CBS-113] Rule QA FACT-015 (KB-1033, PROPOSED): Duplicate & Link trên multi-select có lẫn layer type không support link thì type đó được duplicate thường (bản copy độc lập), không bị bỏ qua. Đúng không? Comment dev TIB-5265 2026-08-18 chỉ nói 'only the allowed types get linked'. CHK-016 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-510"}
```

## OQ-artwork-editor-088 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-088","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1034"],"check_ids":["CHK-017"],"summary":"[CBS-113] Rule QA FACT-036 (KB-1034, PROPOSED): Duplicate & Link áp dụng ngay, không có bước xác nhận, cho Warp Text và mọi type khác. Còn đúng sau lần dev sửa TIB-5265 ngày 2026-09-08 không? CHK-017 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-511"}
```

## OQ-artwork-editor-089 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-089","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1036"],"check_ids":["CHK-019"],"summary":"[CBS-113] KB-1036 (OBSERVED_CURRENT, LOW): theo checklist dev sinh từ branch diff (comment TIB-5265, 2026-08-18), Warp Text layer legacy ở Artwork 1.0 không có Duplicate & Link. Đây có phải hành vi chủ đích không? Testlane case Artwork 1.0 (TC-TIB-1212) bị skip. Cần: Dev hoặc PO xác nhận.","supersedes":"OQ-artwork-512"}
```

## OQ-artwork-editor-090 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-090","type":"CONFLICT","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1039"],"check_ids":["CHK-021"],"conflict_group":"CONF-CBS-113-01","summary":"[CBS-113] Option 'Share with another layer' ở Artwork 2.0 đã bị bỏ hẳn hay vẫn còn trong Bulk edit khi chọn nhiều layer? Supersede tắt ở teeinblue, không chọn phe; KB-1039 và CHK-021 không làm oracle. Cần: Dev trả lời.","side_a":"Rule QA FACT-038 (QA, 2026-09-04, QA-3345; KB-1039 PROPOSED): radio 'Share with another layer' trong Personalization Options đã bỏ ở AW2.0 (disabled + display:none ở mọi layer type), thấy nó ẩn không phải regression.","side_b":"spec-hub teeinblue feature artwork-editor v3, rule artwork-editor-bulk-edit (sure yellow, suy ra; nguồn code và TIB-4024/4026/4025 năm 2025): khi chọn nhiều layer, bulk edit đổi được option 'Share with another layer'.","supersedes":"OQ-artwork-513"}
```

## OQ-artwork-editor-091 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-091","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1040"],"check_ids":["CHK-023"],"summary":"[CBS-113] KB-1040 (TIB-5211): convert một linked layer thì gỡ link và thành 'independent layer (No personalization)'. (1) Layer sau convert có mất hết personalization (thành layer tĩnh) không? (2) Origin và các linked copy còn lại có giữ nguyên type và link không (ticket không nói)? (3) Quy tắc có áp cho Warp Text sau TIB-5265 không? CHK-023 chỉ phán phần gỡ link và đổi type của layer vừa convert; các phần còn lại chỉ ghi quan sát. Cần: Dev xác nhận.","supersedes":"OQ-artwork-514"}
```

## OQ-artwork-editor-092 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-092","type":"CONFLICT","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1041"],"check_ids":["CHK-024"],"conflict_group":"CONF-CBS-113-02","summary":"[CBS-113] Convert Single-line Text origin có linked copy sang Warp Text trên build hiện tại có còn gỡ link của linked copy không? Expected theo TIB-5211 (KB-1040) là giữ link; hai phía về trạng thái build mâu thuẫn, không chọn phe; KB-1041 và CHK-024 không làm oracle. Cần: QA chạy lại TC-44 và ghi record Testlane có ngày chạy + build; nếu vẫn gỡ link thì Dev trả lời; kèm xác nhận đã lên production chưa.","side_a":"Testlane TC-TIB-1580 (QA-3345 TC-44, task TIB-046): status passed nhưng actualResult 'source conversion drops the link' (❌), không ngày chạy, không build.","side_b":"Rule QA FACT-031 (recheck 2026-09-08; KB-1041 PROPOSED): lỗi gỡ link đã được dev sửa; convert origin sang Warp Text thì cả nhóm convert cùng, linked copy giữ link.","supersedes":"OQ-artwork-515"}
```

## OQ-artwork-editor-093 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-093","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1042"],"check_ids":["CHK-025"],"summary":"[CBS-113] Rule QA FACT-045 (KB-1042, PROPOSED): Duplicate & Link trên Color layer chạy như Duplicate thường (copy default_value một lần, customization_type 'normal', không field linked, sửa origin không lan sang copy). Đây có phải thiết kế, và đúng trên production không (release-verification TIB-5241 không kiểm Duplicate & Link)? CHK-025 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-516"}
```

## OQ-artwork-editor-094 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-094","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1043"],"check_ids":["CHK-026"],"summary":"[CBS-116] Rule QA FACT-014/FACT-043 (KB-1043, PROPOSED): ẩn origin (con mắt) thì linked copy vẫn hiện ở editor preview nhưng bị loại khỏi final render (storefront và bản in), cho cả Word Cloud và Warp Text. Đúng thiết kế không, và áp cho mọi type nhóm LINKED không? Cả hai bề mặt chưa được verify đủ: record Testlane TC-TIB-1112 (QA-3343 TC-56) đang passed với kết quả trống, còn nợ phần generated design. CHK-026 chưa có oracle. Cần: Dev xác nhận; QA chạy lại TC-56 phần generated design và ghi record có kết quả, ngày chạy, build.","supersedes":"OQ-artwork-517"}
```

## OQ-artwork-editor-095 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-095","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1044"],"check_ids":["CHK-027"],"summary":"[CBS-116] Rule QA FACT-035 (KB-1044, PROPOSED): background của linked layer hành xử y hệt origin (lệch là sai lệch cần báo). Có đúng trên build sau lần dev sửa TIB-5265 ngày 2026-09-08 không (ảnh chụp kiểm trước lần sửa)? Checklist dev TIB-5265 ghi cover crop canh theo box của linked layer và fallback contain khi không đo được ảnh; đó có phải expected không? CHK-027 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-518"}
```

## OQ-artwork-editor-096 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-096","type":"CONFLICT","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1045","KB-1046"],"check_ids":["CHK-028"],"conflict_group":"CONF-CBS-116-01","summary":"[CBS-116] Thay background image đã lưu của Warp Text origin thì linked copy có render theo trên build hiện tại không? Hai phía mâu thuẫn, supersede tắt ở teeinblue, không chọn phe; KB-1045, KB-1046 và CHK-028 không làm oracle. Liên quan OQ-artwork-081 (đồng bộ sau khi sửa origin). Cần: QA chạy lại TC-25 và ghi record Testlane có ngày chạy + build + ảnh; nếu canvas copy không đổi thì Dev trả lời đó là bug hay giới hạn đã biết; kèm xác nhận trên production.","side_a":"Testlane TC-TIB-1229 (QA-3345 TC-25, task TIB-046): status passed nhưng actualResult và expectedResult ghi 'replacing the saved background does not refresh the rendered image' (❌), không ngày chạy, không build, không ảnh.","side_b":"Rule QA FACT-030 (QA ghi nhận 2026-09-08 bằng ảnh canvas staging; KB-1045 PROPOSED): linked copy không lưu background_image riêng, canvas đổi theo origin ngay khi origin đổi background rồi Save; cùng hướng checklist dev TIB-5265 #48238 2026-08-18 (KB-1046 OBSERVED_CURRENT LOW): 'Set / change / remove a background image on the origin → reflected on the linked copy.'","supersedes":"OQ-artwork-519"}
```

## OQ-artwork-editor-097 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-097","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1047"],"check_ids":["CHK-029"],"summary":"[CBS-116] Rule QA FACT-040 (KB-1047, PROPOSED): linked Warp Text copy chỉ sửa được accordion Extra và các action trong menu '...' (align, geometry, duplicate, delete); design, typography, warp preset, control point, background read-only. Có đúng sau lần dev sửa TIB-5265 ngày 2026-09-08 không? CHK-029 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-520"}
```

## OQ-artwork-editor-098 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-098","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1048"],"check_ids":["CHK-030"],"summary":"[CBS-116] Rule QA FACT-011 (KB-1048, PROPOSED; chính QA đính chính câu trả lời đầu 'word cloud không có align' cùng ngày 2026-08-26): Word Cloud có Align, Align nằm trong nhóm sửa được của linked copy và chỉ dịch copy; hợp lệ trên origin, linked copy và multi-selection. Đúng thiết kế không? CHK-030 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-521"}
```

## OQ-artwork-editor-099 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-099","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1049"],"check_ids":["CHK-031"],"summary":"[CBS-116] Rule QA FACT-044 (KB-1049, PROPOSED): Align hợp lệ trên linked Warp Text copy và chỉ dịch box của copy, không đổi origin (record Testlane TC-TIB-1238 ghi giả định giống Word Cloud). Có đúng sau lần dev sửa TIB-5265 ngày 2026-09-08 không? CHK-031 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-522"}
```

## OQ-artwork-editor-100 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-100","type":"CONFLICT","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1050","KB-1051"],"check_ids":["CHK-032"],"conflict_group":"CONF-CBS-116-02","summary":"[CBS-116] Sau khi xoá origin của linked Warp Text, linked copy hiển thị gì ở editor, storefront render và design file? Hai rule QA mâu thuẫn, supersede tắt ở teeinblue, không chọn phe; KB-1050, KB-1051 và CHK-032 không làm oracle. Checklist dev sinh từ branch diff (TIB-5265 2026-08-18: 'degrades gracefully (no crash, no blank canvas)'; TIB-5242 2026-08-24: 'no crash, sensible fallback') không nói copy hiển thị gì. Cần: Dev trả lời.","side_a":"Rule QA FACT-033 (QA ghi nhận 2026-08-26, TIB-5265; KB-1050 PROPOSED; cũng là expectedResult của Testlane TC-TIB-1239): xoá origin thì linked copy render rỗng (không ẩn layer, không tự gỡ link, không placeholder).","side_b":"Kết quả QA recheck 2026-09-07 (QA-3345 TC-35, cặp clone; KB-1051 PROPOSED; actualResult của TC-TIB-1239): linked copy Warp Text vẫn hiện nội dung origin đã xoá, giống hệt Single-line Text, QA ghi là đúng hành vi.","supersedes":"OQ-artwork-523"}
```

## OQ-artwork-editor-101 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-101","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1056","KB-1057"],"check_ids":["CHK-011"],"summary":"[CBS-124] Rule QA FACT-064 (KB-1057, PROPOSED): flag flip lưu bằng flip_horizontal_enabled / flip_vertical_enabled chỉ trên layer ảnh (photo/clipart); text và curve-text không bao giờ có hai field này. Change note Dev TIB-5435 (2026-09-14, KB-1056 OBSERVED_CURRENT) chỉ nói text/curve text được mirror vị trí và đảo góc, nội dung không lật gương; không nêu tên field. Hai điều này có đúng và là hành vi mong muốn không? CHK-011 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-527"}
```

## OQ-artwork-editor-102 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-102","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1058"],"check_ids":["CHK-010"],"summary":"[CBS-124] Rule QA FACT-065 (KB-1058, PROPOSED): mọi thay đổi trong popover Transform (Flip, Width/Height/Top/Left/Rotate) chỉ được lưu khi bấm Save & Close, không autosave hay debounce. Đây có phải hành vi thiết kế không? spec-hub rule artwork-editor-unsaved-warning chỉ nói có hỏi xác nhận khi đóng editor còn thay đổi chưa lưu. CHK-010 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-528"}
```

## OQ-artwork-editor-103 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-103","type":"CONFLICT","feature_id":"transform-multi-select","kb_ids":["KB-1059"],"check_ids":["CHK-006"],"conflict_group":"CONF-CBS-124-01","summary":"[CBS-124] Đổi Apply for Group → Individual khi Flip H đang tick: layer tính lại từ vị trí gốc hay giữ vị trí đã lật? Hai phía mâu thuẫn, supersede tắt ở teeinblue, không chọn phe; KB-1059 và CHK-006 không làm oracle. Change note Dev TIB-5435 chỉ nói Individual lật tại chỗ, không nói trường hợp đổi mode khi đang tick. Nếu chọn side_a thì expected của TC-TIB-3105 cần sửa. Cần: PO/Dev chọn.","side_a":"Rule QA QA-3362 BR-2 mở rộng 2026-09-24 (quyết định QA, BUG-126 đóng by design; KB-1059 PROPOSED): đổi sang Individual thì layer tính lại từ vị trí gốc (về 100/250, photo vẫn mirror), đổi lại Group cho đúng giá trị lần tick đầu.","side_b":"Record Testlane TC-TIB-3105 (QA-3362 TC-16, status passed, gắn BUG-126), expectedResult: layer giữ nguyên vị trí đã đảo ở step 1, đổi mode không tự đưa layer về vị trí gốc.","supersedes":"OQ-artwork-529"}
```

## OQ-artwork-editor-104 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-104","type":"CONFLICT","feature_id":"transform-multi-select","kb_ids":["KB-1060"],"check_ids":["CHK-007"],"conflict_group":"CONF-CBS-124-02","summary":"[CBS-124] Layer hidden trong vùng chọn có bị dịch khi Group flip không? Hai phía mâu thuẫn, supersede tắt ở teeinblue, không chọn phe; KB-1060 và CHK-007 không làm oracle. Change note Dev TIB-5355 (2026-09-10, box cá nhân) nói layer ẩn hoặc khoá không nằm trong vùng chọn hợp lệ của Transform nhưng không nói về Flip. Cần: Dev trả lời.","side_a":"RQ1 cũ trong phân tích QA-3362 (QA thuật lại câu trả lời Dev, không có nguyên văn Dev): layer hidden vẫn bị dịch khi Group flip.","side_b":"Rule QA FACT-068 (QA chốt 2026-09-16, TC-17 / TC-TIB-3106; KB-1060 PROPOSED): layer hidden được đối xử như locked, không vào bounding box và giữ nguyên vị trí/góc.","supersedes":"OQ-artwork-530"}
```

## OQ-artwork-editor-105 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-105","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1061","KB-1062"],"check_ids":["CHK-004","CHK-005"],"summary":"[CBS-124] KB-1061 (OBSERVED_CURRENT, change note Dev TIB-5435 2026-09-14): Group flip lật cả vùng chọn như một khối (mirror qua tâm khung vùng chọn, góc đảo dấu, ảnh lật), Individual lật tại chỗ, bỏ tick về vị trí/góc ban đầu — có phải hành vi mong muốn đã chốt không? KB-1062 (PROPOSED, rule QA FACT-069): tick cả Flip H và Flip V ở Group thì rotate giữ nguyên (30° vẫn là 30°, không thành −30° hay 30°+180°) — có đúng không? CHK-004 chỉ có oracle BASELINE; CHK-005 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-531"}
```

## OQ-artwork-editor-106 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-106","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1063"],"check_ids":[],"summary":"[CBS-124] Rule QA FACT-070 (KB-1063, PROPOSED): vị trí đo thật sau Group flip lệch khoảng 20px mỗi layer, theo hướng ngược nhau, so với công thức newLeft = 2·cx − left − width; cơ chế chưa rõ, chưa hỏi Dev. Nguyên nhân độ lệch là gì và vị trí nào mới đúng? Tới khi có câu trả lời, check Group flip chỉ kiểm invariant (thứ tự đảo, flag, bỏ tick về giá trị ban đầu). Cần: Dev trả lời.","supersedes":"OQ-artwork-532"}
```

## OQ-artwork-editor-107 — OPEN_ISSUE

```json
{"oq_id":"OQ-artwork-editor-107","type":"OPEN_ISSUE","feature_id":"transform-multi-select","kb_ids":["KB-1064"],"check_ids":["CHK-009"],"summary":"[CBS-124] KB-1064 (CONFIRMED_EXPECTED theo spec TIB-5440): Reverse reposition direction bật thì ảnh buyer kéo đi ngược chiều theo trục đã lật. Record Testlane TC-TIB-3320 và TC-TIB-3321 (task TIB-117) có status passed nhưng actualResult ghi Fail: kéo ngang (Flip H) và kéo dọc (Flip V) không bị đảo chiều, tham chiếu BUG-160/BUG-161; không ngày chạy, không build. Lỗi này đã sửa chưa, trên build nào? Change note Dev TIB-5440 (2026-09-16) còn nêu artwork v1 không có checkbox và layer No personalization vẫn hiện checkbox nhưng không có tác dụng — chưa nạp. Cần: QA chạy lại CHK-009 và ghi record Testlane có ngày chạy + build; Dev cho biết trạng thái BUG-160/161.","supersedes":"OQ-artwork-533"}
```

## OQ-artwork-editor-108 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-108","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1065"],"check_ids":[],"summary":"[CBS-124] Rule QA FACT-072 (KB-1065, PROPOSED): khi chỉ chọn một layer (nhất là text), ô Top/Left trong popover Transform hiện và ghi giá trị khác field top/left thật (đặt 100 thì GraphQL đọc 153.89). Đây là hành vi mong muốn hay lỗi? Cần: Dev trả lời.","supersedes":"OQ-artwork-534"}
```

## OQ-artwork-editor-109 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-109","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1070","KB-1071"],"check_ids":["CHK-012","CHK-013"],"owner":"Dev","summary":"[CBS-129] Rule QA FACT-063 (KB-1071, PROPOSED): lock/hide một layer giữa multi-selection thì layer đó vẫn được tính là đang chọn (\"N selected\" không đổi), box nhóm chỉ bao các layer không khoá/ẩn và co lại ngay khi lock/hide (nở lại khi unlock/unhide), stepper +/- ở ô Top/Left/Width/Height chỉ dịch layer không khoá/ẩn. Change note Dev TIB-5355 (2026-09-10, KB-1070 OBSERVED_CURRENT) chỉ nói layer ẩn/khoá không được vẽ khung riêng vì không nằm trong vùng chọn hợp lệ của Transform. Các điều này có đúng và là hành vi mong muốn không? CHK-013 chưa có oracle, CHK-012 chỉ BASELINE. Cần: Dev xác nhận.","supersedes":"OQ-artwork-538"}
```

## OQ-artwork-editor-110 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-110","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1072"],"check_ids":["CHK-014"],"owner":"Dev","summary":"[CBS-129] Rule QA FACT-063 (KB-1072, PROPOSED): ở Apply for: Individual, khi selection 2–3 layer chỉ còn đúng 1 layer không khoá/ẩn thì canvas xử lý như chọn 1 layer — không box cá nhân, box nhóm co về layer đó, popover Transform mất radio Apply for và hiện số đo của layer đó. Ghi chú \"dev chốt by design 2026-09-16\" là QA thuật lại, chưa có nguyên văn Dev; change note TIB-5355 chỉ nói khung riêng hiện khi chọn từ 2 layer. Dev có xác nhận đây là chủ ý không? CHK-014 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-539"}
```

## OQ-artwork-editor-111 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-111","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1073"],"check_ids":["CHK-015"],"owner":"Dev","summary":"[CBS-129] Rule QA FACT-063 (KB-1073, PROPOSED): double-click sửa text khi đang chọn nhiều layer thì selection thu về đúng layer đó; ô cỡ chữ trên quick toolbar (.qte-font-size) chỉ hiện khi mọi layer đang chọn là text, giá trị nhập áp cho tất cả, selection lẫn photo thì ô ẩn hẳn. spec-hub artwork-editor-bulk-edit (yellow) không nói hai điều này. Có đúng và là hành vi mong muốn không? CHK-015 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-540"}
```

## OQ-artwork-editor-112 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-112","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1074"],"check_ids":["CHK-016"],"owner":"Dev","summary":"[CBS-129] Rule QA FACT-063 (KB-1074, PROPOSED): box cá nhân (.artwork-layer-frame) viền solid 1px và box nhóm (.drr::before) viền dashed 2px, cùng màu #00c4cc, cả hai không nhận chuột, không box-shadow. Change note TIB-5355 chỉ nói khung riêng chỉ để nhìn. Màu và kiểu nét này có phải thiết kế chủ đích không? CHK-016 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-541"}
```

## OQ-artwork-editor-113 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-113","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1075"],"check_ids":["CHK-017"],"owner":"Dev/PO","summary":"[CBS-129] Delete khi chọn nhiều layer (KB-1075, OBSERVED_CURRENT/LOW, record Testlane TC-TIB-3086 chỉ tick [AI], không ngày chạy, không build): Delete xoá cả 3 layer đang chọn, Ctrl+Z trả lại 3 layer nhưng selection rỗng; expected của test case ghi Undo khôi phục cả box Individual. Expected đúng là gì (Undo có khôi phục selection và box không)? Có cách xoá riêng 1 layer trong khi vẫn giữ các layer khác đang chọn không (QA chốt là không, chưa có nguồn)? Đây là hành vi xoá dữ liệu (P1): cần test case Testlane PASS có ngày chạy, build và căn cứ expected, hoặc Dev/PO xác nhận nguyên văn có ngày. CHK-017 (P1) chưa có oracle. Cần: Dev/PO xác nhận.","supersedes":"OQ-artwork-542"}
```

## OQ-artwork-editor-114 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-114","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1076"],"check_ids":["CHK-018"],"owner":"Dev","summary":"[CBS-129] Rule QA FACT-063 (KB-1076, PROPOSED, QA chốt 2026-09-16): Align dùng target riêng \"Align to:\", không theo radio Apply for; editor không có phím tắt Ctrl+D để duplicate và không có phím mũi tên để nudge layer, di chuyển bằng số là stepper +/- ở ô Transform. spec-hub artwork-editor-shortcuts (yellow) liệt kê Ctrl+J duplicate, không có Ctrl+D hay phím mũi tên, nhưng không nói thẳng là không có. Có đúng không? CHK-018 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-543"}
```

## OQ-artwork-editor-115 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-115","type":"NEEDS_CONFIRMATION","feature_id":"transform-multi-select","kb_ids":["KB-1077"],"check_ids":["CHK-019"],"owner":"Dev","summary":"[CBS-129] Rule QA FACT-063 (KB-1077, PROPOSED): chọn layer con trong Group qua layer panel (Cmd/Ctrl/Shift-click) không nâng lên chọn Group cha, mỗi con có box riêng; chọn chính Group container kéo theo mọi layer con; box nhóm bao union mọi layer, luôn axis-aligned. Ghi chú \"dev chốt RQ5 2026-09-16\" là QA thuật lại, chưa có nguyên văn Dev. Có đúng và là chủ ý không? CHK-019 chưa có oracle. Cần: Dev xác nhận.","supersedes":"OQ-artwork-544"}
```

## OQ-artwork-editor-116 — CONFLICT

```json
{"oq_id":"OQ-artwork-editor-116","type":"CONFLICT","feature_id":"transform-multi-select","kb_ids":["KB-1078"],"check_ids":["CHK-020"],"conflict_group":"CONF-CBS-129-01","owner":"Dev","summary":"[CBS-129] Group layer (container) trong selection Apply for: Individual có box cá nhân không? Hai phía mâu thuẫn, supersede tắt ở teeinblue, không chọn phe; KB-1078 và CHK-020 không làm oracle. Cả hai phía đều từ QA (side_a là QA thuật lại câu Dev, không có nguyên văn). Nếu chọn side_a thì expected của TC-TIB-3059 cần sửa. Cần: Dev chọn.","side_a":"RQ13 trong phân tích QA-3361 (QA thuật lại câu Dev trả lời 2026-09-16, không có nguyên văn Dev): Group layer có individual box bằng union bounding box của các layer con.","side_b":"Rule QA FACT-063 + expected Testlane TC-TIB-3059 (QA-3361 TC-6, đo trên staging 2026-09-16/17; KB-1078 PROPOSED): Group container không bao giờ có .artwork-layer-frame, chỉ từng layer con có box riêng.","supersedes":"OQ-artwork-545"}
```

## OQ-artwork-editor-117 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-117","type":"NEEDS_CONFIRMATION","feature_id":"layer-duplicate-link-copy","kb_ids":["KB-1098"],"check_ids":[],"owner":"Dev","summary":"[CBS-149] Ngoài claim (quan sát staging ghi trong CCR): dữ liệu lưu của linked copy curve / warp text vẫn giữ cặp stroke_color / stroke_width cũ của chính nó, trong khi render dùng cặp của gốc. Đây là thiết kế hay dữ liệu thừa cần dọn? Có trường hợp nào (gỡ link, convert, copy artwork, đọc qua API/MCP) mà cặp cũ của copy được dùng lại không? Không nạp KB.","supersedes":"OQ-artwork-564"}
```

## OQ-artwork-editor-118 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-118","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"Bản HD (master_large) của layer ảnh: cạnh dài 4096, giữ tỉ lệ, xoay EXIF đúng một lần, file không còn EXIF chỉ là quan sát staging 2026-11-10 (KB-1102, CHK-001/CHK-002 BASELINE). Quy tắc cap 4096 (TIB-5420/TIB-5543) chưa có trong canon (CCR backfill chưa publish). PNG có alpha có giữ transparency không: chưa kiểm vì PNG test không có alpha (CHK-003).","kb_ids":["KB-1102"],"needs":"CCR backfill quy tắc HD (TIB-5420/TIB-5543) có nguồn Dev/PO; chạy HD với PNG có alpha.","supersedes":"OQ-artwork-568"}
```

## OQ-artwork-editor-119 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-artwork-editor-119","type":"NEEDS_CONFIRMATION","feature_id":"layer-bulk-edit","summary":"Toast/spinner trạng thái khi bản HD đang tạo hoặc tạo lỗi hiển thị thế nào: CCR nêu trong phạm vi feature nhưng không có nguồn hay quan sát (quan sát toast thành công nằm ở _flows/toolbar-transform.md).","kb_ids":[],"needs":"Dev/PO hoặc test case cho trường hợp HD lỗi.","supersedes":"OQ-artwork-569"}
```
