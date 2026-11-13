# Open Questions — sdk-genai

## OQ-sdk-genai-001 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-001","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[NEW, NEEDS_CONFIRMATION] Text to Image (AI) qua Live Preview — chưa test nhập prompt MỚI qua chính surface này — CHK-002 chỉ quan sát generate dùng prompt ĐÃ LƯU sẵn ở portal — chưa test khả năng nhập prompt mới qua chính Live Preview widget (nếu UI có field này). Ảnh hưởng thiết kế test case cho luồng buyer tự tuỳ biến prompt (nếu tính năng này tồn tại).","related":"CHK-003 (genai-personalization-runtime)","supersedes":"OQ-sdk-034"}
```

## OQ-sdk-genai-002 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-002","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[NEW, NEEDS_CONFIRMATION, GAP] TIB-5339 — so sánh sync vs async giữa route chính và route fallback KHI route fallback THÀNH CÔNG — Trong lần thử duy nhất (CHK-004/005), CẢ HAI route (chính và fallback) đều fail cùng lý do (ảnh bị client re-encode xuống dưới ngưỡng 10000 byte trước khi tới cả 2 route). Route fallback multipart THẬT SỰ TỒN TẠI và được tự động thử khi route chính lỗi (xác nhận ở CHK-005), nhưng chưa có lần route fallback THÀNH CÔNG để so sánh downstream GenAI generate là sync hay async. KHÔNG suy diễn kết quả so sánh — cần fixture/ảnh input phù hợp hơn và nguyên nhân lỗi khác ở run tiếp theo.","related":"CHK-006 (genai-personalization-runtime)","supersedes":"OQ-sdk-035"}
```

## OQ-sdk-genai-003 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-003","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[NEW, NEEDS_CONFIRMATION] 'Select a previously generated image' với ≥2 item lịch sử — gallery/modal thật sự hiển thị gì, chưa thử — Với chỉ 1 item lịch sử (CHK-007), bấm nút 'Select a previously generated image' KHÔNG mở gallery/modal riêng biệt quan sát được — chưa ép mở gallery với ≥2 item để biết UI thật sự hiển thị gì. Chỉ có evidence cho trường hợp 1 item; chưa biết UI khi có nhiều lựa chọn lịch sử.","related":"CHK-008 (genai-personalization-runtime)","supersedes":"OQ-sdk-036"}
```

## OQ-sdk-genai-004 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-004","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[NEW, NEEDS_CONFIRMATION, GAP] 'Duplicate & Share' (TIB-5326) — control không tìm thấy ở Live Preview widget — 'Duplicate & Share' (TIB-5326) KHÔNG tìm thấy ở CẢ portal editor lẫn storefront Live Preview cho layer Text to Image (AI)/Multiple Uploads — 2 agent độc lập cùng không tìm thấy, KHÔNG kết luận feature không tồn tại (có thể bị gate bởi điều kiện chưa trigger: nhiều biến thể generated, cart/order thật, plan cụ thể). Cần hỏi dev/PO trước khi viết test case chính thức. (Trùng với CHK-053 trong checklist layer-config-image.json — cùng 1 gap quan sát từ 2 bề mặt khác nhau, KHÔNG phải duplicate giả tạo để tăng số lượng.)","related":"CHK-009 (genai-personalization-runtime)","supersedes":"OQ-sdk-037"}
```

## OQ-sdk-genai-005 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-005","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[NEW, NEEDS_CONFIRMATION] Ngưỡng '>=2 ảnh' để enable nút Generate — ngưỡng thật hay chỉ render-lag nhất thời? — CHK-010 chỉ 1 sample (Maximum photos=3) — chưa phân biệt được đây là ngưỡng thật (>=2 ảnh bắt buộc bất kể Maximum photos config) hay chỉ là render-lag nhất thời. KHÔNG suy thành validation rule tổng quát tới khi có ≥2 sample độc lập ở cấu hình khác nhau.","related":"CHK-011 (genai-personalization-runtime)","supersedes":"OQ-sdk-038"}
```

## OQ-sdk-genai-006 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-006","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[NEW, NEEDS_CONFIRMATION] Toàn bộ feature — hành vi có giữ nguyên trên guest session thật hay không (hiện chỉ staff-authenticated proxy) — TOÀN BỘ evidence của feature này là staff-authenticated PROXY cho buyer (account explorer (TIB_STAGING_EMAIL) dùng Live Preview widget), KHÔNG PHẢI guest session thật — mọi rate-limit, session-boundary, hoặc UI khác biệt trên theme Shopify thật CHƯA được loại trừ. KHÔNG dùng làm oracle 100% cho hành vi buyer thật tới khi có test với guest session.","related":"CHK-013 (genai-personalization-runtime)","supersedes":"OQ-sdk-039"}
```

## OQ-sdk-genai-007 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-007","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[NEW, NEEDS_CONFIRMATION] Mọi finding về Generate/upload chỉ xác nhận cho Gemini — chưa test OpenAI/Flux/ImagenHub qua runtime này — Toàn bộ finding về async job+polling/minimum-filesize/select-previous-image trong checklist này CHỈ phản ánh hành vi CỦA Gemini (assumption 'rẻ nhất' để test, không có nguồn giá xác nhận) — chưa xác nhận cho OpenAI/Flux/ImagenHub. Rủi ro tổng quát hoá sai nếu provider khác có endpoint/shape/validation khác.","related":"CHK-014 (genai-personalization-runtime)","supersedes":"OQ-sdk-040"}
```

## OQ-sdk-genai-008 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-008","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Thứ tự resize/crop khi bật 'Set minimum size' (minimum-resolution) trên layer Multiple Uploads (TIB-5188) HOÀN TOÀN CHƯA TEST — cần bật option đó bên companion feature của object artwork trước khi có thể quan sát.","supersedes":"OQ-sdk-041"}
```

## OQ-sdk-genai-009 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-009","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Add-to-cart / cart / checkout-boundary của luồng GenAI hoàn toàn KHÔNG chạm tới được: Live Preview widget là preview cấp artwork, không gắn product/campaign/cart. Đây là giới hạn cấu trúc của surface đã dùng, không phải policy — cần quyền publish có kiểm soát (hoặc guest session thật trên PDP) ở lần chạy sau. Không viết check nào cho phần này (0 evidence tuyệt đối).","supersedes":"OQ-sdk-042"}
```

## OQ-sdk-genai-010 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-010","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Persistence/reload của state runtime (job history, danh sách ảnh đã generate) sau khi reload trang: 0 evidence — Live Preview widget chưa được test reload giữa các bước, nên dimension STATE_DATA bị loại khỏi checklist thay vì viết check giả định.","supersedes":"OQ-sdk-043"}
```

## OQ-sdk-genai-011 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-011","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[CCR CBS-005/TIB-5460] Root-cause collision fallback-ID theo device-info (KB-049): fixture ≥2 visitor dùng thiết bị/khu vực tương tự, upload AI-effect trước khi thumbmark fetch xong — ID fallback được sinh ra có thực sự collide giữa các visitor không? Hiện tượng chỉ được báo cáo qua Jira TIB-5460 (description + comment id 51194, huyenntk, 2026-09-17/18), CHƯA reproduce độc lập trên fixture nhiều device/visitor trong bất kỳ run nào. Đồng thời cần xác nhận vai trò kỹ thuật (dev/PM) của huyenntk trước khi dùng KB-049 làm oracle cho test case.","related":"CHK-018 (genai-personalization-runtime), KB-049","supersedes":"OQ-sdk-044"}
```

## OQ-sdk-genai-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-012","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[CCR CBS-005/TIB-5460] KB-050 phần 1 (fix TIB-5460, ĐANG QA Review, CHƯA SHIP): sau khi ticket ship, fallback ID có thực sự random-per-browser (khác nhau giữa các visitor cùng thiết bị) thay vì suy từ device-info không? Cần re-verify bằng >=1/13 test case Testlane task TIB-116 (TC-TIB-3296..TC-TIB-3308, hiện 0/13 đã chạy) PASS đúng hành vi tương ứng trước khi coi đây là capability đã hoạt động.","related":"CHK-019 (genai-personalization-runtime), KB-050","supersedes":"OQ-sdk-045"}
```

## OQ-sdk-genai-013 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-013","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[CCR CBS-005/TIB-5460] KB-050 phần 2 (fix TIB-5460, ĐANG QA Review, CHƯA SHIP): sau khi ticket ship, request GET /merchant/{platform}/thumbmark có thực sự fire ngay khi page load (thay vì lazy khi upload đầu tiên như hiện tại) không? Chưa có môi trường nào để quan sát timing thật tại thời điểm ghi nhận (2026-09-28).","related":"CHK-020 (genai-personalization-runtime), KB-050","supersedes":"OQ-sdk-046"}
```

## OQ-sdk-genai-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-014","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[CCR CBS-005/TIB-5460] KB-050 phần 3 (fix TIB-5460, ĐANG QA Review, CHƯA SHIP): sau khi ticket ship, SDK có retry đúng 1 lần khi network-error/5xx lúc fetch thumbmark, và KHÔNG retry khi 429 không? Chưa verify được logic retry thật tại thời điểm ghi nhận.","related":"CHK-021 (genai-personalization-runtime), KB-050","supersedes":"OQ-sdk-047"}
```

## OQ-sdk-genai-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-015","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"[CCR CBS-005/TIB-5460] End-to-end re-verify sau khi TIB-5460 ship: lặp lại đúng fixture đã dùng để phát hiện collision fallback-ID (KB-049, CHK-018) — collision còn tái diễn không? Phụ thuộc CẢ 2 điều kiện: CHK-018 đã chạy ít nhất 1 lần để có baseline 'trước fix', VÀ TIB-5460 đã ship — hiện CẢ 2 đều chưa thoả.","related":"CHK-022 (genai-personalization-runtime), KB-050, KB-049","supersedes":"OQ-sdk-048"}
```

## OQ-sdk-genai-016 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-016","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"[CCR CBS-005/TIB-5460] Follow-up chưa có ticket con Jira riêng: endpoint issuance thumbmark (GET /merchant/{platform}/thumbmark) rate-limit theo IP (không theo shop/visitor) — dev tự nêu (hedged, dùng từ 'occasionally'), buyer đứng sau CGNAT/mobile carrier share IP có thể VẪN OCCASIONALLY rơi vào dùng ID fallback (KB-049) dù fix TIB-5460 (KB-050) đã ship. Giá trị cụ thể (số lượt/window) của rate-limit theo IP CHƯA được Dev nêu rõ. Khuyến khích người gửi CCR/PO tạo ticket con Jira riêng để theo dõi độc lập với TIB-5460.","related":"CHK-023 (genai-personalization-runtime), KB-052","supersedes":"OQ-sdk-049"}
```

## OQ-sdk-genai-017 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-017","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"TIB-5583 merge và deploy lên staging ở build nào, ngày nào, và đã lên production chưa? Nguồn không nêu build và ngày deploy, nên chưa rõ 2 item của ticket này đã ship hay chưa.","kb_ids":["KB-415","KB-436"],"supersedes":"OQ-sdk-119"}
```

## OQ-sdk-genai-018 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-018","type":"NEEDS_CONFIRMATION","feature_id":"genai-model-settings","summary":"Hành vi migration (successor, giữ cài đặt khác, picker disable model cũ) mới chỉ quan sát một lượt chạy QA-3408 TC-07/TC-14 không ghi build; chưa có nguồn xác nhận expected. Nếu PO coi việc migration tự đổi model đã lưu của merchant là thay đổi dữ liệu nhạy cảm thì cần nâng impact lên HIGH và hỏi owner.","kb_ids":["KB-458"],"needs":"Dev hoặc PO xác nhận nguyên văn hành vi migration, hoặc test case chạy lại có build ghi rõ.","supersedes":"OQ-sdk-126"}
```

## OQ-sdk-genai-019 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-019","type":"NEEDS_CONFIRMATION","feature_id":"genai-model-settings","summary":"Model mặc định khi lưu không chọn model chỉ quan sát phía sau ngày migrate (QA-3408 TC-05), build không ghi; phía trước ngày migrate chưa test.","kb_ids":["KB-462"],"needs":"Dev hoặc PO xác nhận quy tắc model mặc định trước và sau ngày migrate; chạy lại phía trước ngày migrate.","supersedes":"OQ-sdk-127"}
```

## OQ-sdk-genai-020 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-020","type":"NEEDS_CONFIRMATION","feature_id":"genai-model-settings","summary":"Validate key với model retired trả code model_retired và không chọn model thì validate theo model mặc định: chỉ có quan sát QA-3408 TC-06/TC-22, không có căn cứ expected, build không ghi.","kb_ids":["KB-463"],"needs":"Dev hoặc PO xác nhận response mong muốn của Validate key với model retired và khi không gửi model.","supersedes":"OQ-sdk-128"}
```

## OQ-sdk-genai-021 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-021","type":"NEEDS_CONFIRMATION","feature_id":"genai-model-settings","summary":"Request lưu từ tab cũ còn gửi model retired: quan sát 200, lưu cài đặt khác, giữ model (QA-3408 TC-20), không có căn cứ expected.","kb_ids":["KB-465"],"needs":"Dev hoặc PO xác nhận đây là hành vi mong muốn của save rule sau ngày migrate.","supersedes":"OQ-sdk-129"}
```

## OQ-sdk-genai-022 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-022","type":"NEEDS_CONFIRMATION","feature_id":"genai-model-settings","summary":"API lưu Gen AI Effects đang nhận mọi giá trị model (id lạ, script, SQL/NoSQL) với 200 và lưu nguyên văn. Dev xác nhận ticket không đổi hành vi này, nhưng đó không phải mong muốn. Có nên chặn giá trị model không hợp lệ bằng 4xx không?","kb_ids":["KB-467"],"needs":"PO quyết có chặn 4xx cho giá trị model không hợp lệ (và theo ticket nào); đến lúc đó item không dùng làm expected.","supersedes":"OQ-sdk-130"}
```

## OQ-sdk-genai-023 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-023","type":"NEEDS_CONFIRMATION","feature_id":"genai-model-settings","summary":"Toggle auto-switch (nhãn, mô tả, mặc định OFF, lưu/giữ sau reload) khớp spec PO trong description TIB-5554 theo đối chiếu, nhưng CCR không trích spec và build không ghi; mới là quan sát QA-3408 TC-01/TC-02.","kb_ids":["KB-469"],"needs":"Trích nguyên văn spec PO (label, Default state OFF, description) kèm ngày, hoặc test case chạy lại có build.","supersedes":"OQ-sdk-131"}
```

## OQ-sdk-genai-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-024","type":"NEEDS_CONFIRMATION","feature_id":"genai-model-settings","summary":"Phạm vi toggle auto-switch: hiện tại 1 toggle cho mọi provider GenAI (1 field genai_auto_fallback), trong khi spec PO ghi \"applies to the account's active AI service and model\". Ý định là toggle theo service/model đang active hay 1 toggle cho mọi provider?","kb_ids":["KB-470"],"needs":"PO chốt phạm vi toggle.","supersedes":"OQ-sdk-132"}
```

## OQ-sdk-genai-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-025","type":"NEEDS_CONFIRMATION","feature_id":"genai-model-settings","summary":"Id lưu nano_banana_21 của Nano Banana 2.1 chỉ là quan sát (QA-3442 TC-01), không có căn cứ expected.","kb_ids":["KB-471"],"needs":"Dev xác nhận id lưu của Nano Banana 2.1.","supersedes":"OQ-sdk-133"}
```

## OQ-sdk-genai-026 — CONFLICT

```json
{"oq_id":"OQ-sdk-genai-026","type":"CONFLICT","feature_id":"genai-model-settings","summary":"Model Gemini sau migration: global-option/KB-031 (quan sát 2026-09-16, trước khi TIB-5554 ship) ghi job generate trả model='nano_banana' và global-option CHK-02-011 expect model='nano_banana'; sdk KB-459 (dev, Jira TIB-5554 comment #54687 Q9, 2026-10-15) nói account ở nano_banana được chuyển sang nano_banana_31. Lưu ý: \"KB-031\" ở đây là của object global-option, không phải sdk KB-031. Có thể chỉ là hai mốc thời gian khác nhau (giá trị cũ nano_banana khớp vế đầu của KB-459); điểm lệch thực là CHK-02-011 có còn đúng sau migrate_at không, chưa ai chạy lại sau 2026-10-16. Phía global-option chưa được đánh dấu vì object đó ngoài lock của run này.","kb_ids":["KB-459"],"needs":"PO quyết; hoặc một run có lock object global-option cập nhật KB-031 / CHK-02-011 theo model sau migration.","conflict_group":"CONF-CBS089-01","side_a":"global-option/KB-031 (feature artwork-personalization-global-option-link): job generate GO#862 trả model='nano_banana' (OBSERVED_CURRENT, LOW, 1 mẫu, 2026-09-16); global-option CHK-02-011 expect model='nano_banana'.","side_b":"sdk KB-459: giá trị lưu Gemini cũ là nano_banana, account ở nano_banana được chuyển sang nano_banana_31 (CONFIRMED_EXPECTED, po_dev_confirm 2026-10-15).","supersedes":"OQ-sdk-134"}
```

## OQ-sdk-genai-027 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-027","type":"OPEN_ISSUE","feature_id":"genai-model-settings","summary":"migrated_at sau lượt chạy sạch và known limitation (account bị ép về model retired, email lần hai) chưa có người xác nhận, test case chưa chạy. Claim trong CCR thiếu người xác nhận nên chưa có KB item.","kb_ids":[],"needs":"Dev hoặc PO xác nhận nguyên văn, hoặc chạy TC-09/12/13/17 của QA-3408.","supersedes":"OQ-sdk-135"}
```

## OQ-sdk-genai-028 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-028","type":"OPEN_ISSUE","feature_id":"genai-model-settings","summary":"Từ ngày migrate chọn model retired bị 422 + toast retired: dev nói 422 nhưng QA-3408 TC-18, TC-21 (2026-10-16) ra 200. Claim trong CCR thiếu người xác nhận nên chưa có KB item.","kb_ids":[],"needs":"Dev nêu trạng thái tái hiện được 422 trên staging.","supersedes":"OQ-sdk-136"}
```

## OQ-sdk-genai-029 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-029","type":"OPEN_ISSUE","feature_id":"genai-model-settings","summary":"Email sau khi đổi model (1 email, nêu model cũ/mới, chỉ account có API key provider đó) chưa có người xác nhận, test case chưa chạy. Claim trong CCR thiếu người xác nhận nên chưa có KB item.","kb_ids":[],"needs":"Dev trả lời Q3 hoặc chạy TC-08/10/11/40 của QA-3408.","supersedes":"OQ-sdk-137"}
```

## OQ-sdk-genai-030 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-030","type":"OPEN_ISSUE","feature_id":"genai-model-settings","summary":"Admin > Settings từ chối giá trị sai của genai_model_retirements và genai_model_fallbacks chưa có người xác nhận; QA không có quyền Admin. Claim trong CCR thiếu người xác nhận nên chưa có KB item.","kb_ids":[],"needs":"Người có quyền Admin chạy TC-23/24/39/42, hoặc dev xác nhận nguyên văn.","supersedes":"OQ-sdk-138"}
```

## OQ-sdk-genai-031 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-031","type":"NEEDS_CONFIRMATION","feature_id":"genai-model-settings","summary":"Key Gemini hợp lệ nhưng không có quyền với Nano Banana 2.1: Validate key có báo not valid với câu chung \"Key is not working. Please check & try again.\" như dev nói (KB-457) không? TC-26 của QA-3442 chưa chạy, cần fixture key không có quyền với 2.1. Testlane TC-TIB-7927 ghi quyết định QA 2026-11-01: không tạo được key Gemini không có quyền 2.1 trên staging.","kb_ids":["KB-457"],"supersedes":"OQ-sdk-139"}
```

## OQ-sdk-genai-032 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-032","type":"OPEN_ISSUE","feature_id":"genai-model-settings","summary":"Feature genai-model-settings chưa có KB cho role khác merchant-owner, cross-tenant và production; mọi item scope staging. Không viết check cho các vùng này từ evidence hiện tại.","kb_ids":[],"supersedes":"OQ-sdk-140"}
```

## OQ-sdk-genai-033 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-033","type":"NEEDS_CONFIRMATION","feature_id":"genai-model-settings","summary":"Đặt migrate_at về ngày hiện tại trên staging làm quy tắc lưu và model mặc định áp cho MỌI account staging (KB-461). Các check cần chạy job migration hoặc cần phía trước ngày migrate (CHK-010..CHK-015) ai được chạy, trên account nào, và cần dev/admin phối hợp thế nào?","kb_ids":["KB-461","KB-466"],"supersedes":"OQ-sdk-141"}
```

## OQ-sdk-genai-034 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-034","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Endpoint effect storefront customer-uploads/{id}/image-filter-effects/async dùng resolution do browser gửi thay vì giá trị đã lưu trên layer (QA-3442 TC-33, 2 repro, 2026-10-30). Ý dev chấp nhận để đó chỉ có trong tin Slack QA lưu, không có link; đã ship hay chưa không rõ; chưa thử derive hay field khác.","kb_ids":["KB-475"],"needs":"Dev xác nhận nguyên văn có link (Jira/PR) rằng đây là giới hạn chấp nhận hay bug cần sửa; nếu sửa, ticket theo dõi.","supersedes":"OQ-sdk-142"}
```

## OQ-sdk-genai-035 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-035","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Server bỏ qua model/gemini_model giả mạo trong request effect storefront và dùng model của account: chỉ là quan sát QA (TC-TIB-7934, skip, 2 lần), chưa ai xác nhận. Chưa ai quan sát generate khi model đã lưu là giá trị lạ (API lưu không kiểm, KB-467 của genai-model-settings).","kb_ids":["KB-476"],"needs":"Dev xác nhận nguyên văn server luôn lấy model từ private_config của store owner cho request effect storefront.","supersedes":"OQ-sdk-143"}
```

## OQ-sdk-genai-036 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-036","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Hành vi Resolution \"Default\" theo provider có nguồn dev_doc (Jira TIB-5561 #55645) nhưng product tắt allow_dev_doc_supersede nên item ở OBSERVED_CURRENT/LOW; GPT Default mới chạy layer 3:2 (1:1, 2:3 chưa chạy). Trả lời một phần OQ-sdk-040.","kb_ids":["KB-477"],"needs":"PO/dev xác nhận nguyên văn (po_dev_confirm) hoặc test case PASS có build ghi rõ; chạy GPT Default trên layer 1:1 và 2:3.","supersedes":"OQ-sdk-144"}
```

## OQ-sdk-genai-037 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-037","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Dung sai test cho ảnh GPT khi chọn resolution: dev \"ok\" mức ±16 px / tỉ lệ ±1%, nhưng quy tắc làm tròn xuống bội 16 ở 1K tỉ lệ 3:2 cho lệch tỉ lệ khoảng 1.6% (QA-3435 TC-21, 2026-10-27), vượt ±1%. Quy tắc làm tròn và dung sai không cùng đúng được.","kb_ids":["KB-478"],"needs":"Dev/PO chốt dung sai test (hoặc công thức kích thước kỳ vọng theo từng tỉ lệ) cho GPT.","supersedes":"OQ-sdk-145"}
```

## OQ-sdk-genai-038 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-038","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Flux ra đúng width × height có nguồn dev_doc (Jira TIB-5561 #55645) nhưng product tắt allow_dev_doc_supersede nên item ở OBSERVED_CURRENT/LOW; quan sát duy nhất QA-3435 TC-25 bước 2 không ghi build.","kb_ids":["KB-480"],"needs":"PO/dev xác nhận nguyên văn hoặc test case PASS có build ghi rõ.","supersedes":"OQ-sdk-146"}
```

## OQ-sdk-genai-039 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-039","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Layer Text to Image có sẵn giữ Gemini resolution chọn lúc ở nano_banana_pro, nay dùng khi account ở nano_banana_31 (trước bị bỏ qua). Dev ghi \"PO to confirm\" việc chấp nhận cho merchant đang live và việc Text to Image chỉ dành cho beta (TIB-5561 #55697 Q6); QA đã hỏi PO (#55728), chưa có trả lời (Q4/Q5/Q6). Ranh giới với KB-489 (layer có sẵn mở ở Default) chưa rõ.","kb_ids":["KB-481"],"needs":"PO trả lời Q4/Q5/Q6 của TIB-5561.","supersedes":"OQ-sdk-147"}
```

## OQ-sdk-genai-040 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-040","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Account còn ở model retired sau ngày shutdown: dev chọn \"plain failure\" (buyer thấy lỗi, không cảnh báo/CTA cho seller, không tự fallback) như giới hạn dev chấp nhận (TIB-5554 #54687 Q8); QA từng muốn cảnh báo seller; chưa có PO chốt và TC-36/TC-47 chưa chạy. Vế portal từ chối lưu model retired bằng 422 còn nghi vấn (OQ-sdk-136).","kb_ids":["KB-483"],"needs":"PO chốt hành vi mong muốn (A cảnh báo + CTA / B plain failure / C auto-fallback); chạy TC-36, TC-47.","supersedes":"OQ-sdk-148"}
```

## OQ-sdk-genai-041 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-041","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Quality low/medium/high và generate nền trong suốt bằng gpt-image-1.5 không fallback_model sau migration chỉ là quan sát QA-3408 TC-16 (2026-10-16), không có căn cứ expected, build không ghi.","kb_ids":["KB-484"],"needs":"Dev/PO xác nhận nguyên văn, hoặc test case chạy lại có build ghi rõ.","supersedes":"OQ-sdk-149"}
```

## OQ-sdk-genai-042 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-042","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Generate chạy bằng backup cùng provider và ghi fallback_model khi model down (GPT, Gemini, Flux) chỉ là quan sát QA tick tay QA-3408 TC-25 với lỗi do dev stub; vế model đã lưu không đổi chưa có trong kết quả ghi lại.","kb_ids":["KB-485"],"needs":"Dev xác nhận nguyên văn hành vi failover; chạy lại TC-25 ghi cả model đã lưu và build.","supersedes":"OQ-sdk-150"}
```

## OQ-sdk-genai-043 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-043","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Layer có sẵn mở ở Resolution \"Default\" và Save & Close không đổi thì không thêm key *_resolution / flux_output_* chỉ là quan sát QA-3435 TC-02 (build không ghi); dev notes chỉ nói layer có sẵn không bị ảnh hưởng.","kb_ids":["KB-489"],"needs":"Dev xác nhận nguyên văn hành vi lưu key size của layer có sẵn.","supersedes":"OQ-sdk-151"}
```

## OQ-sdk-genai-044 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-044","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Ngưỡng coi model là down (cửa sổ 5 phút, ≥ 50 lỗi và ≥ 50%; chỉ timeout/408/5xx được đếm; ngưỡng là biến env GENAI_FALLBACK_*) chưa có người xác nhận, test case liên quan (TC-27, 28, 46) chưa chạy. Claim trong CCR thiếu người xác nhận nên chưa có KB item.","kb_ids":[],"needs":"Dev hoặc PO xác nhận nguyên văn, hoặc chạy TC-27/28/46 của QA-3408.","supersedes":"OQ-sdk-152"}
```

## OQ-sdk-genai-045 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-045","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Retry 1 lần trên backup trong 60 s, thử lại model gốc sau 30 phút, không có backup thứ hai, toggle tắt hoặc không có backup thì lỗi provider như cũ: chưa có người xác nhận, TC-26/29/30/31/45 chưa chạy. Claim trong CCR thiếu người xác nhận nên chưa có KB item.","kb_ids":[],"needs":"Dev hoặc PO xác nhận nguyên văn, hoặc chạy TC-26/29/30/31/45 của QA-3408.","supersedes":"OQ-sdk-153"}
```

## OQ-sdk-genai-046 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-046","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Cấu hình backup genai_model_fallbacks (default theo model, override theo user, danh sách cặp mặc định, backup retired theo successor; áp cho image filter, text-to-image, multi-image) chưa có người xác nhận; QA không có quyền Admin, TC-32/33/35 chưa chạy. Claim trong CCR thiếu người xác nhận nên chưa có KB item.","kb_ids":[],"needs":"Người có quyền Admin đọc genai_model_fallbacks, hoặc dev xác nhận nguyên văn.","supersedes":"OQ-sdk-154"}
```

## OQ-sdk-genai-047 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-047","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Known limitation của fallback (quay về model gốc trễ tới 30 phút; bộ đếm chung nên một account có thể đẩy mọi account opt-in sang backup; call treo chỉ được đếm sau TIB-5389; deadline polling Flux không tính là outage) chưa có người xác nhận. Claim trong CCR thiếu người xác nhận nên chưa có KB item.","kb_ids":[],"needs":"Dev hoặc PO xác nhận nguyên văn.","supersedes":"OQ-sdk-155"}
```

## OQ-sdk-genai-048 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-048","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Storefront không đổi sau TIB-5470 (effect vẫn chạy trên ảnh buyer upload, thiếu key vẫn lặng lẽ bỏ qua effect; mua với layer có ảnh đã xử lý thì order design dùng ảnh đã xử lý): nguồn chỉ là mục regression/possible test cases của dev doc TIB-5470, không phải phát biểu hành vi; TC-43/44 không có kết quả chạy có ngày. Vế order design thuộc object order (ngoài lock). Chưa có KB item.","kb_ids":[],"needs":"Dev/PO xác nhận nguyên văn hành vi storefront, hoặc test case PASS có ngày và build; vế order cần run có lock object order.","supersedes":"OQ-sdk-156"}
```

## OQ-sdk-genai-049 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-049","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"KB-482 (generate chỉ đọc model trong private_config của store owner; migration và email chỉ cho store owner, staff không nhận) chạm phân quyền owner/staff: item ADDED được diff đánh dấu cần owner xác nhận ý định. Scope item là buyer/api trong khi vế migration và email là hành vi phía account merchant.","kb_ids":["KB-482"],"needs":"PO xác nhận ý định cho staff account; reviewer/owner xem có cần tách scope vế migration và email.","supersedes":"OQ-sdk-157"}
```

## OQ-sdk-genai-050 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-050","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Outage/fallback của Nano Banana 2.1 chưa QA nào chạy (TC-27/28/39 skip, TC-29 pause); dev sau đó nói không cần test lại fallback cho 2.1; bảng genai_model_fallbacks chưa đọc được vì QA không có quyền Admin.","kb_ids":["KB-474","KB-488"],"needs":"Nếu cần test: nhờ Dev chuyển 2.1 sang down trên staging (KB-488) và người có quyền Admin đọc genai_model_fallbacks.","supersedes":"OQ-sdk-158"}
```

## OQ-sdk-genai-051 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-051","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Layer Text to Image có Resolution 512 đã lưu dưới Nano Banana 2 khi account ở Nano Banana 2.1 chưa test (QA chỉ test Multiple Uploads).","kb_ids":["KB-472"],"needs":"Chạy trên layer Text to Image.","supersedes":"OQ-sdk-159"}
```

## OQ-sdk-genai-052 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-052","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Gemini trên layer không vuông mới kiểm tỉ lệ 3:2 ở 1K/2K trên nano_banana_pro; 0.5K, 4K và các tỉ lệ khác chưa kiểm.","kb_ids":["KB-479"],"needs":"Chạy thêm 0.5K/4K trên layer không vuông.","supersedes":"OQ-sdk-160"}
```

## OQ-sdk-genai-053 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-053","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Production của khác biệt môi trường KB-488 (cách đưa Nano Banana 2.1 vào trạng thái down) không rõ; mọi item mới của CBS-094 chỉ có scope staging.","kb_ids":["KB-488"],"needs":"Dev mô tả phía production.","supersedes":"OQ-sdk-161"}
```

## OQ-sdk-genai-054 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-genai-054","type":"OPEN_ISSUE","feature_id":"genai-personalization-runtime","summary":"Kết quả QA-3435 (2026-10-27) và QA-3408 (2026-10-16) không ghi build, nên baseline của KB-477, KB-480, KB-481, KB-484, KB-485, KB-489 chưa gắn được với bản đã test.","kb_ids":["KB-477","KB-480","KB-481","KB-484","KB-485","KB-489"],"needs":"Chạy lại có ghi build, hoặc QA bổ sung build vào kết quả.","supersedes":"OQ-sdk-162"}
```

## OQ-sdk-genai-055 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-055","type":"NEEDS_CONFIRMATION","feature_id":"photo-genai-image-filter-runtime","summary":"Photo layer [Gemini] image filter có ref image rất lớn (12000x12000): effect hoàn tất (status 2), preview hiện kết quả, upload không kẹt Processing chỉ là quan sát một lượt staging (KB-562, CHK-001 BASELINE). Có phải expected không? QA plan TIB-5615 A.1 của Dev có ý này nhưng CCR không trích nguyên văn. Production mới chạy với ref 4000x5300.","kb_ids":["KB-562"],"needs":"CCR sau trích nguyên văn QA plan A.1 (Dev) hoặc Dev/PO xác nhận; production với ref ≥ 8000 px.","supersedes":"OQ-sdk-249"}
```

## OQ-sdk-genai-056 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-056","type":"NEEDS_CONFIRMATION","feature_id":"photo-genai-image-filter-runtime","summary":"Tỉ lệ kết quả GenAI của Photo layer: rule Dev chuyển qua QA (KB-565, PROPOSED) nói Photo Direct luôn gửi size = kích thước layer nên kết quả theo khung layer (quan sát layer 420x420 → kết quả vuông); QA plan TIB-5615 A.2 của Dev lại viết kết quả \"keeps the photo's portrait orientation and ratio\". Tỉ lệ theo khung layer hay theo ảnh buyer? Image Placement / Image Cropper chỉ gửi size khi bật is_layer_output_size: chưa chạy. Spec-hub rule image-effects-keep-ratio (green) đọc 2026-11-12 nói cùng nghĩa với KB-565.","kb_ids":["KB-565","KB-563"],"needs":"Dev/PO xác nhận trên nguồn dẫn được (Jira hoặc rule spec-hub trích nguyên văn); chạy Image Placement và Image Cropper có/không is_layer_output_size.","supersedes":"OQ-sdk-250"}
```

## OQ-sdk-genai-057 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-057","type":"NEEDS_CONFIRMATION","feature_id":"photo-genai-image-filter-runtime","summary":"Feature photo-genai-image-filter-runtime mới có nguồn cho Gemini image filter; transparency của ảnh kết quả và image filter của provider khác (gpt, flux, imagenhub) chưa có nguồn hay quan sát.","kb_ids":[],"needs":"CCR hoặc explore cho image filter GPT/Flux/ImagenHub và ảnh có alpha.","supersedes":"OQ-sdk-251"}
```

## OQ-sdk-genai-058 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-058","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Text to Image và Multiple Uploads luôn gửi size = kích thước layer (KB-568, PROPOSED, rule Dev chuyển qua QA 2026-11-10; quan sát layer 315x420 → kết quả 3:4). Dev xác nhận trên nguồn dẫn được?","kb_ids":["KB-568"],"needs":"Dev xác nhận nguyên văn có ngày (Jira) hoặc rule spec-hub green trích nguyên văn.","supersedes":"OQ-sdk-252"}
```

## OQ-sdk-genai-059 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-059","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Gemini snap tỉ lệ gần nhất trong 21:9, 16:9, 9:16, 3:2, 2:3, 4:3, 3:4, 5:4, 4:5, 1:1 (không có 9:21), 512 chỉ cho nano_banana_31 (KB-569, PROPOSED, rule Dev chuyển qua QA; bổ sung KB-479). Vế mặc định trái nguồn: rule chuyển lại nói không có hoặc sai size thì 1:1, còn unit test U3 của Dev trên Jira TIB-5615 #56735 nói applyImageFilter() không có size thì lấy tỉ lệ ảnh buyer. Mặc định theo từng luồng (image filter, Multiple Uploads, Text to Image) là gì?","kb_ids":["KB-569"],"needs":"Dev xác nhận nguyên văn có ngày cho danh sách tỉ lệ và mặc định theo từng luồng; quan sát request không có size.","supersedes":"OQ-sdk-253"}
```

## OQ-sdk-genai-060 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-060","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Resolution khi layer không lưu gemini_resolution: Photo image filter 2K; Multiple Uploads / Text to Image 1K với nano_banana_31 và nano_banana_21, 2K với nano_banana_pro (KB-570, PROPOSED). Dev (chuyển qua QA) nói 2K của nano_banana_pro là do nhầm lẫn trước đó, coi là lỗi hiếm gặp; KB-477 mô tả cùng hành vi như \"giữ 2K như trước\". 2K của pro là expected hay lỗi được chấp nhận? Vế nano_banana_pro / nano_banana_21 chưa chạy. Liên quan OQ-sdk-144.","kb_ids":["KB-570","KB-477"],"needs":"PO/Dev chốt 2K của nano_banana_pro; chạy nano_banana_pro và nano_banana_21 không lưu resolution.","supersedes":"OQ-sdk-254"}
```

## OQ-sdk-genai-061 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-061","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Rule tỉ lệ/kích thước output của GPT, Flux Kontext, ImagenHub (KB-571, PROPOSED, rule Dev QA chuyển lại, ngoài scope TIB-5615, chưa verify). Diff không thấy trái KB-477, KB-478, KB-480. Dev xác nhận?","kb_ids":["KB-571"],"needs":"Dev xác nhận nguyên văn có ngày; chạy GPT free-size, Flux không nhập WxH, ImagenHub use_template_default_size.","supersedes":"OQ-sdk-255"}
```

## OQ-sdk-genai-062 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-062","type":"NEEDS_CONFIRMATION","feature_id":"photo-genai-image-filter-runtime","summary":"Ảnh dọc, ngang, dọc EXIF 6 trên layer [Gemini] image filter có ref image lớn cho kết quả đúng hướng, không méo (KB-563) và ref nhỏ 200x200 vẫn hoàn tất như trước (KB-564) chỉ là quan sát: TC-TIB-8953/8954/8955/8957 PASS staging 2026-11-10 nhưng record không ghi build, không kiểm được bản đã test có chứa thay đổi TIB-5615. Expected tương ứng có ở QA plan A.2/A.3 của Dev (#56741) nhưng CCR không trích.","kb_ids":["KB-563","KB-564"],"needs":"Chạy lại các test case trên build ghi rõ (chứa TIB-5615) và gửi CCR trích QA plan A.2/A.3 làm căn cứ expected.","supersedes":"OQ-sdk-256"}
```

## OQ-sdk-genai-063 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-genai-063","type":"NEEDS_CONFIRMATION","feature_id":"genai-personalization-runtime","summary":"Multiple Uploads Gemini với 2 ảnh lớn, một ảnh EXIF 6: generate hoàn tất, không ảnh nào bị xoay ngang (KB-567) chỉ là quan sát: TC-TIB-8956 PASS staging 2026-11-10, record không ghi build. Expected có ở QA plan B.4 của Dev (#56741) nhưng CCR không trích.","kb_ids":["KB-567"],"needs":"Chạy lại TC-TIB-8956 trên build ghi rõ và gửi CCR trích QA plan B.4.","supersedes":"OQ-sdk-257"}
```
