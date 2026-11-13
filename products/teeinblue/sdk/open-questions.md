# Open Questions — SDK

## OQ-sdk-001 — CONFLICT

```json
{"oq_id":"OQ-sdk-001","type":"CONFLICT","feature_id":"object-level (storefront-buyer-facing + product-page-settings-config)","summary":"SDK version thực sự đang được serve cho từng store (instance 609 / store TIB_STORE_URL_1 vs instance 613 / store TIB_STORE_URL_2) trên campaign 2595 — 3 nguồn evidence mâu thuẫn nhau, UNRESOLVED. Trực tiếp implicate tính CURRENT của KB-004/KB-005/KB-007/KB-010/KB-011 (nhãn 'store1 = SDK v1') và của mọi capability/check phân biệt v1/v2 theo store. Tương ứng conflict_group CFL-004 trên các KB item (KB-004/KB-007/KB-010/KB-011 phía cũ; KB-037/KB-040 phía mới). Chỉ orchestrator + reviewer được quyết resolution; KHÔNG tự chọn phía, KHÔNG tự đánh dấu KB nào là stale, KHÔNG dùng nhãn v1/v2 theo store làm điều kiện rẽ nhánh chắc chắn cho store1 trước khi có resolution.","side_a":"store1 (instance 609) chạy storefront SDK v1 (nested radiogroup ~10 clipart, lightbox mockup TĨNH kiểu PhotoSwipe, header x-sdk-version: 1.0.3, script tag app-v1.js, container class tee-campaign-v1); store2 (instance 613) chạy SDK v2 (grouped_clipart grid ~9 clipart, SVG mockup sống với id artwork-layer--layer-<n>, script tag app-v2.js, container class tee-campaign-v2). Quan sát trực tiếp storefront runtime của campaign 2595, 2026-09-12 — HIGH confidence TẠI THỜI ĐIỂM ghi nhận, phía cũ nhất.","side_b":"GET /api/instances?trashed (portal, 2026-09-21) trả field sdk_version = 2 cho CẢ instance 609 và 613; instance.config object được ghi nhận giống hệt nhau giữa 2 instance trong sample này. LOW confidence — chỉ 1 sample full-body, không byte-diff độc lập.","side_c":"Storefront runtime re-check 2026-09-21 trên CÙNG URL campaign 2595 đã dùng để lập side_a: store1 nay serve https://staging-sdk.teeinblue.com/shopify/app-v2.js (+ async.js?v=2) và container class 'tee-campaign tee-campaign-v2 tee-customization-wrapper' — ngược hẳn marker app-v1.js/tee-campaign-v1 của side_a; store2 không đổi (vẫn v2). Toàn bộ DOM personalization quan sát được (element id, field label, số clipart, giá, CSS custom property) nay byte-identical giữa 2 store, cross-check bằng 2 lượt script độc lập. HIGH confidence, mới nhất, hội tụ với side_b.","related":"CHK-038 (storefront-buyer-facing), CHK-021 (product-page-settings-config)"}
```

## OQ-sdk-002 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-002","type":"OPEN_ISSUE","feature_id":"object-level","summary":"Object sdk hiện chỉ có 3 feature profile (storefront-buyer-facing, product-page-settings-config, genai-personalization-runtime). Không rõ SDK còn bề mặt/feature nào khác chưa vào scope — cần qa-context-scope-planner xác nhận đây đã là toàn bộ phạm vi object hay còn thiếu. '3/3 feature có profile' KHÔNG phải tín hiệu completeness cấp object."}
```

## OQ-sdk-003 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-003","type":"OPEN_ISSUE","feature_id":"object-level","summary":"Data layer (DB) NOT_OBSERVED hoàn toàn cho cả object — mọi state chỉ dựa trên response API, localStorage và DOM; chưa có xác nhận nào qua DB thật (không có access trong phạm vi các lần khám phá tới nay)."}
```

## OQ-sdk-004 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-004","type":"OPEN_ISSUE","feature_id":"object-level","summary":"Toàn bộ evidence buyer-facing của object chỉ đến từ 1 campaign duy nhất (campaign 2595, by product base). CHƯA xác nhận kiến thức này áp dụng y hệt cho product Shopify gốc (by-shopify flow) — đây là giả định ngầm của việc tách object sdk (SDK độc lập với loại campaign) và chưa được test chéo."}
```

## OQ-sdk-005 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-005","type":"OPEN_ISSUE","feature_id":"object-level","summary":"Các chiều biến thiên phổ biến chưa test ở bất kỳ feature nào: buyer đã login, market/locale/currency ngoài US/USD/en, mobile/tablet viewport, và role portal khác owner. 0% coverage — không suy diễn hành vi cho các chiều này."}
```

## OQ-sdk-006 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-006","type":"OPEN_ISSUE","feature_id":"object-level","summary":"Template coverage: mọi evidence về dependency 2 cấp, grouped_clipart 2-step và preview mechanism chỉ dựa trên template option 1-2 của campaign 2595; template option 3 chưa từng được test trên bất kỳ store nào. Chưa rõ các cơ chế đã ghi nhận có generalize sang template khác hay chỉ đúng cho template này."}
```

## OQ-sdk-007 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-007","type":"OPEN_ISSUE","feature_id":"object-level","summary":"Cross-object pointer (KHÔNG thuộc dữ liệu object sdk, nêu ở đây để downstream biết): companion feature của genai-personalization-runtime là FEAT-02-photo-upload-layer-config bên object artwork đang có 1 conflict UNRESOLVED (artwork CONF-CBS003-01, corroborated bởi global-option) cần authority quyết định. Khi dựng test case cho genai-personalization-runtime phải đọc kèm profile/checklist của companion feature đó."}
```

## OQ-sdk-008 — CONFLICT

```json
{"oq_id":"OQ-sdk-008","type":"CONFLICT","feature_id":"storefront-buyer-facing","summary":"Store1 (SDK v1, campaign 2595): Add-to-cart có hoàn tất thành công được hay không sau khi điền đủ mọi field cá nhân hoá. UNRESOLVED — conflict_group CFL-001 trên KB-005 (phía automation); phía còn lại là lời khai manual-test của user, KHÔNG có KB item tương ứng nên được giữ nguyên văn tại đây. Cần (a) một lần re-test thật bằng thao tác click/type từng bước (không .fill()/force-check hàng loạt) để thu evidence nhất quán hoặc mâu thuẫn với lời khai user, hoặc (b) code-config-explorer/api-explorer review logic validate client-side của staging-sdk.teeinblue.com/shopify/app-v1.js. KHÔNG kết luận ATC store1 PASS hay FAIL trước đó.","side_a":"Add-to-cart BỊ CHẶN: banner lỗi chung 'Error: Some fields are required or invalid data' vẫn xuất hiện và click ADD TO CART bắn 0 network request, kể cả sau khi mọi field required hiển thị đã điền/checked đầy đủ, không còn lỗi inline riêng lẻ. Tái hiện với 2 cấu hình template khác nhau (template-277843/1-cat, template-578330/2-cat), nhiều kỹ thuật chọn/dispatch event khác nhau. Nguồn: storefront-explorer store1, phiên automated (Playwright headless), HIGH confidence.","side_b":"Add-to-cart hoạt động BÌNH THƯỜNG khi test bằng tay (mouse/keyboard thật), bao gồm 1 lần deliberate recheck điền đủ mọi field trước khi submit. Nguồn: user, manual interactive test trên store1 (báo cáo bằng lời qua orchestrator, không do storefront-explorer trực tiếp thực hiện hay chứng kiến), LOW confidence, không có evidence file.","related":"CHK-007 (storefront-buyer-facing), KB-005, KB-006 (hypothesis INFERRED, không phải một phía)"}
```

## OQ-sdk-009 — CONFLICT

```json
{"oq_id":"OQ-sdk-009","type":"CONFLICT","feature_id":"storefront-buyer-facing","summary":"Store2 (SDK v2, campaign 2595): tên nhóm option cấp cha 'Poster - Woman and dog clipart template' không khớp nhãn các field con 'Choose Cat Breed #1/#2' / 'Cat Name #1/#2' trong cùng khung template. UNRESOLVED. Cần xác nhận từ merchant/PM đây là lỗi copy khi tạo campaign hay quy ước đặt tên nội bộ không nhất quán của template config; hoặc code-config-explorer kiểm tra nguồn config template xem 'dog' có phải leftover/placeholder text. KHÔNG tự chọn nhãn nào làm chuẩn, KHÔNG coi đây là bug đã xác nhận. Lưu ý: không có KB item nào trong object mang 2 phía này (chúng chỉ tồn tại ở entry này và ở CHK-017), nên không có conflict_group tương ứng trong features/*/kb.json.","side_a":"Heading cấp cha của template hiển thị 'Poster - Woman and dog clipart template' (nói tới 'dog'). Nguồn: storefront-explorer store2, MEDIUM confidence.","side_b":"Các field cá nhân hoá con trong cùng khung lại dùng nhãn 'Choose Cat Breed #1/#2', 'Cat Name #1/#2' (nói tới 'cat'). Nguồn: storefront-explorer store2, MEDIUM confidence.","related":"CHK-017 (storefront-buyer-facing)"}
```

## OQ-sdk-010 — CONFLICT

```json
{"oq_id":"OQ-sdk-010","type":"CONFLICT","feature_id":"storefront-buyer-facing","summary":"Store2 (SDK v2, campaign 2595): liệu Add-to-cart trên store2 thực sự đã là đường đi 'known-working' từ lần quan sát 2026-09-12, hay lần thử ATC ĐẦU TIÊN (2026-09-12, lượt localStorage) thất bại thật vì thiếu bước click con của field grouped_clipart. UNRESOLVED — conflict_group CFL-003 trên KB-008 và KB-018. Hai khả năng KHÔNG xác nhận: (a) tooling lần trước có thể đã vô tình bao gồm bước click con như phần của thao tác click thumbnail nhóm mà không ghi chú tách riêng; (b) synthetic/scripted click có thể khác pointer click thật về số lần re-render DOM. Cần orchestrator/reviewer đối chiếu lại log tương tác thực tế của lần quan sát trước. Ghi chú (CHƯA XÁC NHẬN, KHÔNG merge): dạng 'dependency 2 tầng cần thao tác thêm' ở đây CÓ THỂ liên quan tới hypothesis 'automation-interaction gap' của OQ-sdk-008 (KB-006) nhưng là 2 field/2 SDK version khác nhau.","side_a":"Framing kế thừa: store2/SDK v2 add-to-cart 'đã biết ATC thành công' từ lần quan sát 2026-09-12, ngụ ý đường đi ATC store2 là baseline đã ổn định, không cần re-verify (KB-008: ATC hoàn tất thành công đầu-cuối). LOW confidence cho phần framing.","side_b":"Khi điền đủ 8 field cá nhân hoá trên store2 (guest, campaign 2595, SDK v2) NHƯNG chỉ click radio nhóm của 3 field grouped_clipart (Hairstyle, Cat Breed #1, Cat Breed #2) mà KHÔNG click thêm thumbnail con, rồi bấm ADD TO CART: banner lỗi 'Error: Some fields are required or invalid data' + lỗi inline 'This field is required!' dưới cả 3 field; GET /cart.js ngay sau đó cho item_count=0; log network xác nhận ZERO request tới POST /api/merchant/shopify/customization. Đây là lần thử ĐẦU TIÊN, không phải lỗi giả lập; ATC chỉ thành công ở lần thử THỨ HAI sau khi thêm bước click con (KB-018). HIGH confidence, corroborated cross-layer.","related":"CHK-032 (storefront-buyer-facing), KB-008, KB-018"}
```

## OQ-sdk-011 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-011","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Pre-flight check khi theme app-block CHƯA enable (enabled=false) hoặc endpoint lỗi — chưa test — Chưa có instance nào ở trạng thái app-block chưa enable trong scope run này để test case negative của pre-flight gate — cần chuẩn bị fixture instance riêng ở lần chạy sau, KHÔNG phải vấn đề credential.","related":"CHK-015 (storefront-buyer-facing)"}
```

## OQ-sdk-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-012","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Coverage gap: template 1 và 3 chưa test (cả 2 SDK); đường 'edit personalization từ cart' chưa xác nhận tồn tại (SDK v2) — Template 1/3 chưa từng được test — không rõ có cùng pattern dependency 2 cấp như template 2 hay không, đây là gap coverage cụ thể của run này (không phải thiếu credential). Đường edit-from-cart trên SDK v2 không tìm thấy trong phiên test này nhưng chưa đủ để kết luận 'không tồn tại' — cần tìm kỹ hơn (vd kiểm tra theme section khác, hoặc hỏi PO/Dev về UX dự kiến).","related":"CHK-018 (storefront-buyer-facing)"}
```

## OQ-sdk-013 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-013","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Hành vi field cá nhân hoá khi buyer đổi variant SAU KHI đã điền — reset hay giữ nguyên? (chưa test, cả 2 SDK) — Interaction sequence phổ biến của buyer thật (điền field rồi đổi ý variant) chưa từng được test ở cả 2 SDK trong bất kỳ run nào — không rõ hệ thống reset field hay giữ nguyên; có thể lộ bug reset-state không đúng nếu không nhất quán.","related":"CHK-019 (storefront-buyer-facing)"}
```

## OQ-sdk-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-014","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Buyer đã login, non-US market/locale/currency, mobile/tablet viewport — chưa test — Toàn bộ evidence FEAT-07 tới nay chỉ ở guest/desktop/US-default. 3 chiều biến thiên phổ biến này (login state, market/locale, viewport) hoàn toàn chưa kiểm chứng — đây là gap coverage cụ thể của lần khám phá này, KHÔNG phải thiếu credential storefront.","related":"CHK-020 (storefront-buyer-facing)"}
```

## OQ-sdk-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-015","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Storefront phân biệt đúng campaign ĐÃ publish (truy cập/mua được) với object CHƯA publish (không truy cập được) — chưa re-test với credential hợp lệ trong run này — Chưa test lại case unpublished VỚI credential storefront hợp lệ trong run này — chỉ có evidence 'không credential' (route-agnostic block, cả published/unpublished) từ run trước. KB-001 hiện tại (run này) chỉ xác nhận gate được vượt qua cho campaign 2595 ĐÃ publish; KHÔNG có observation nào trong run này về việc truy cập 1 object unpublished SAU KHI đã có credential hợp lệ. Cần thực hiện lại phép so sánh trực tiếp (1 object published + 1 object unpublished, cùng credential) trước khi có thể kết luận storefront có phân biệt đúng published/unpublished hay không.","related":"CHK-021 (storefront-buyer-facing)"}
```

## OQ-sdk-016 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-016","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"'Generate test design' / preview storefront trước khi publish — chưa khám phá — Hoàn toàn chưa được khám phá trong bất kỳ run nào, kể cả run này — KHÔNG liên quan tới credential storefront (đây là 1 entry point khác, có thể ở phía portal, chưa từng được thử). Cần xác định entry point cụ thể trước khi có thể viết check thật với oracle rõ ràng.","related":"CHK-022 (storefront-buyer-facing)"}
```

## OQ-sdk-017 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-017","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Gap: Post-ATC persistence của localStorage draft trên SDK v1 (store1) — CHƯA xác nhận vì store1 chưa từng tới ATC trong bất kỳ run nào — SDK v1 (store1) chưa từng tới được bước Add-to-cart trong bất kỳ run nào (kể cả run này — dừng trước ATC theo chủ đích để tránh re-trigger CFL-001) — không có evidence nào để xác nhận hay phủ nhận hành vi post-ATC persistence tương tự SDK v2 (KB-021). Đây là gap coverage phụ thuộc trực tiếp vào việc CFL-001 được giải quyết trước; KHÔNG suy diễn hành vi SDK v1 giống SDK v2 dù cơ chế localStorage khác (KB-014..017, KB-019) đã xác nhận giống nhau.","related":"CHK-030 (storefront-buyer-facing)"}
```

## OQ-sdk-018 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-018","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","summary":"TTL/expiry của localStorage draft ('teeinblue-customizations', 'teeinblue-global-options'): cả 2 store chỉ có field 'timestamp' (epoch ms, last-write), không có field expiry nào và chưa thực hiện phép chờ dài hạn. Việc entry có bao giờ bị prune theo tuổi hay không là NOT_OBSERVED — cố ý không suy diễn theo bất kỳ hướng nào."}
```

## OQ-sdk-019 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-019","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","summary":"Hành vi ghi localStorage khi CHỈ click radio nhóm của field grouped_clipart (chưa click thumbnail con): có ghi giá trị placeholder nào trước bước click con, hay không ghi gì tới khi chọn con — chưa cô lập được ở granularity đó (2 click luôn nằm trong cùng cửa sổ ~600ms trước mỗi lần dump)."}
```

## OQ-sdk-020 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-020","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","summary":"Field-remount pre-fill (KB-020) chỉ xác nhận cho field dạng text (Woman Name); CHƯA xác nhận cho field dạng radio/clipart/grouped_clipart — không suy diễn là giống nhau."}
```

## OQ-sdk-021 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-021","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","summary":"Full contract của endpoint server-sync lúc ATC (POST /api/merchant/shopify/customization): request/response body, auth mechanism và error-path (4xx/5xx) chưa quan sát được — format network capture đã dùng không lưu headers/status/body cho entry nào. Chỉ có presence/absence tại thời điểm ATC."}
```

## OQ-sdk-022 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-022","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","summary":"Liệu store1 (SDK v1) có gọi POST /api/merchant/shopify/customization (hay endpoint tương đương) tại thời điểm ATC của chính nó hay không — store1 chưa từng tới được bước ATC trong bất kỳ lần khám phá nào, nên toàn bộ chuỗi server-sync/post-ATC của SDK v1 là NOT_OBSERVED (phụ thuộc OQ-sdk-008)."}
```

## OQ-sdk-023 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-023","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","summary":"Cross-origin isolation giữa store1 và store2 (2 origin riêng, localStorage không chia sẻ) được khẳng định như hành vi browser mặc định nhưng KHÔNG được test trực tiếp — đây là assumption, không phải OBSERVED_CURRENT cùng lần khám phá."}
```

## OQ-sdk-024 — CONFLICT

```json
{"oq_id":"OQ-sdk-024","type":"CONFLICT","feature_id":"product-page-settings-config","summary":"Config schema khai báo của GET /api/settings (config_registry.instance.config, ~38 key kèm metadata type/default/description/group) KHÔNG khớp payload .config thực tế trả về bởi GET /api/instances?trashed (~27 key quan sát cho instance 609/613) — chỉ 1 tên key ('add_design_links') xuất hiện ở cả 2 tập, và bản thân key đó cũng chưa khớp được với control UI cụ thể nào trong 67 control đã quan sát. UNRESOLVED — conflict_group CFL-005 trên KB-038 và KB-039. Cần code-config-explorer/backend source xác nhận: /api/instances chỉ trả key đã set (bỏ schema default chưa set)? hay 2 'instance.config' là 2 namespace khác nhau? hay schema đang stale/aspirational? KHÔNG tự resolve, giữ cả 2 phía.","side_a":"config_registry.instance.config (GET /api/settings) khai báo ~38 key config cấp instance dưới dạng schema dictionary, gồm những key đọc như ứng viên hợp lý cho các control Product Page Settings đã quan sát (vd show_cross_sell, group='Storefront SDK', có thể khớp control 'Show Cross-sell Personalization') — nhưng đây là schema tài liệu/aspirational, CHƯA xác nhận là thứ trang /product-page-settings thực sự đọc/ghi. LOW confidence.","side_b":"Object .config thực tế do GET /api/instances?trashed trả về cho instance 609 và 613 chỉ chứa ~27 key (style_variants, preview_content, add_design_links, atc_border_radius, ..., show_assigned_variant_images_only) — không có key nào tên show_cross_sell và không khớp phần lớn 38 entry schema theo đúng tên. LOW confidence.","related":"CHK-020 (product-page-settings-config), KB-038, KB-039"}
```

## OQ-sdk-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-025","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Gap: luong Upload logo day du (chon file, preview, luu) hoan toan chua test -- khong co duong revert an toan xac dinh duoc trong run nay — Upload logo chua tung duoc click trong bat ky run nao vi khong xac nhan duoc duong revert don gian trong pham vi SAFE_REVERSIBLE_ONLY ma khong keo theo nguy co phai Save (forbidden_actions). Can lam ro voi PO/Dev quy trinh revert an toan (hoac 1 test-instance rieng khong anh huong du lieu that) truoc khi viet duoc test case that cho luong nay.","related":"CHK-012 (product-page-settings-config)"}
```

## OQ-sdk-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-026","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Gap: gia tri hex chinh xac cua ~13 color-picker va lua chon dang chon cua cac icon-only swatch (Font size, Toggle style, Alignment, Field's border radius) KHONG doc duoc qua accessibility tree — Accessibility tree khong phan biet duoc gia tri hex cua color-picker hay lua chon dang active cua icon-only swatch trong run nay -- chi xac nhan duoc su hien dien/cau truc (xem CHK-013/014/015), khong xac nhan duoc gia tri dang chon. Can 1 phuong phap doc khac (DOM inspection truc tiep qua DevTools Protocol, hoac code review) o lan chay sau truoc khi co the viet oracle 'gia tri hien tai phai la X' cho cac field nay.","related":"CHK-016 (product-page-settings-config)"}
```

## OQ-sdk-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-027","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Tuong quan (INFERRED, KHONG PHAI contract da xac nhan) giua ~27 key trong .config va cac control UI da quan sat -- khong duoc dung nhu data contract field-by-field — Binding giua .config (~27 key, API-OP-001) va 67 control UI CHI la tuong quan theo ten/gia tri (INFERRED), KHONG PHAI 1 data contract da xac nhan field-by-field qua code reference hay qua response cua Save (write-path chua tung duoc test, xem CHK-022). KHONG duoc viet oracle 'thay doi checkbox X se ghi dung key Y trong .config' cho toi khi co code reference tu code-config-explorer hoac quan sat truc tiep response cua Save. Ngoai ra, .config THUC TE (~27 key) khong khop config_registry SCHEMA (~38 key, API-OP-002) -- xem CHK-020 (CFL-005) -- can resolve truoc khi coi bat ky key nao trong so ~11 key con lai cua schema la 'se xuat hien khi merchant thay doi tu UI'.","related":"CHK-018 (product-page-settings-config)"}
```

## OQ-sdk-028 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-028","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Gap: write-path (Save/Reset) hoan toan chua co evidence -- nut hien dien/enabled nhung chua tung duoc click — Save/Reset hoan toan chua co evidence trong bat ky run nao tinh toi nay (forbidden_actions cua exploration_policy). Moi gia dinh ve hanh vi luu/validate-khi-luu (bao gom co goi API-OP-001 dang PUT/POST khong, co field nao trong .config duoc ghi, co validation loi nao khong) deu la suy dien, KHONG co evidence. Can explicit policy tu orchestrator/PO cho phep 1 lan mutation co kiem soat (vd tren test-instance rieng) truoc khi co the viet duoc test case that cho write-path nay.","related":"CHK-022 (product-page-settings-config)"}
```

## OQ-sdk-029 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-029","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Gap: bien thien permission/role tren /product-page-settings hoan toan chua duoc quan sat -- chi 1 role (owner) duoc test — Chi role owner (explorer (TIB_STAGING_EMAIL), user_id <explorer>) duoc test trong run nay -- khong co credential role khac (TIB_USER_A_*/TIB_USER_B_*) san co. Khong co evidence nao cho biet role thap hon co bi gioi han xem/sua control nao tren trang nay hay khong. Can credential role khac o lan chay sau truoc khi viet duoc test case PERMISSION that cho trang nay.","related":"CHK-023 (product-page-settings-config)"}
```

## OQ-sdk-030 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-030","type":"OPEN_ISSUE","feature_id":"product-page-settings-config","summary":"Các giá trị khác của dropdown 'Form type' (popup / expand-collapse) và mọi sub-field chúng có thể hé lộ (KB-026) chưa được thử — time-boxed out, zero evidence."}
```

## OQ-sdk-031 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-031","type":"OPEN_ISSUE","feature_id":"product-page-settings-config","summary":"Các trang 'Store Settings' lân cận (General Settings, Product Page Content, Customization Image, Shipping Methods, Inventory Locations, SKU Mapping) nằm ngoài object target đã khám phá — zero evidence, không suy diễn hành vi."}
```

## OQ-sdk-032 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-032","type":"OPEN_ISSUE","feature_id":"product-page-settings-config","summary":"Entry point thứ hai ngay trên trang — link '(Switch store?)' cạnh heading 'For store: <store>' — chưa test riêng hành vi click (chỉ dùng sidebar store switcher). DOM tách biệt với sidebar switcher nên không suy diễn hành vi giống nhau."}
```

## OQ-sdk-033 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-033","type":"OPEN_ISSUE","feature_id":"product-page-settings-config","summary":"Liệu store thứ 3 trở lên có xuất hiện trong store switcher với account khác hay không — account đang test được xác nhận exhaustively là đúng 2 store (KB-024), không tổng quát hoá cho account khác."}
```

## OQ-sdk-050 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-050","type":"OPEN_ISSUE","feature_id":"storefront-translations","summary":"Các hành vi SDK về translations nạp từ CCR CBS-001 (KB-053..KB-060) mới được verify trên staging cho TIB-5352 (Jira status QA Review, 3 PR còn OPEN, chỉ deploy staging); chưa release production. Cần re-verify (hoặc xác nhận) sau khi TIB-5352 lên production; trong lúc đó không dùng các item này để đánh giá hành vi production.","kb_ids":["KB-053","KB-054","KB-055","KB-056","KB-057","KB-058","KB-059","KB-060"]}
```

## OQ-sdk-051 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-051","type":"NEEDS_CONFIRMATION","feature_id":"storefront-translations","summary":"Fallback chữ gốc khi API translations trả 500/503 hoặc bị abort (KB-054) chỉ quan sát trong test case FAILED TC-TIB-4696; cần test PASS hoặc Dev/PO xác nhận trước khi làm oracle.","kb_ids":["KB-054"]}
```

## OQ-sdk-052 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-052","type":"NEEDS_CONFIRMATION","feature_id":"storefront-translations","summary":"Khi translations API timeout, console có pageerror 'signal is aborted without reason' (KB-055). CCR 4.2 nói không coi đây là hành vi mong muốn. Cần Dev xác nhận đây là lỗi cần sửa hay chấp nhận được.","kb_ids":["KB-055"]}
```

## OQ-sdk-053 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-053","type":"NEEDS_CONFIRMATION","feature_id":"storefront-translations","summary":"Thiết kế retry khi fetch translations lỗi: staging quan sát retry lazy (tối đa 2 fetch, lần 2 chỉ ở lần gọi kế tiếp trong cùng page session, không retry khi load trang — KB-057), trong khi Dev mô tả 'SDK chỉ thử lại đúng 1 lần' không nêu điều kiện và test case TC-TIB-4696 FAILED vì kỳ vọng '1 retry khi load'. Cần Dev xác nhận hành vi retry mong muốn.","kb_ids":["KB-057"]}
```

## OQ-sdk-054 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-054","type":"NEEDS_CONFIRMATION","feature_id":"storefront-translations","summary":"Dictionary inline chỉ in 1 lần trong HTML /zh-zh/ (KB-059); điều kiện 'trang render cả theme app extension và theme script' (KB-060) chỉ suy từ dấu hiệu HTML, chưa mở theme editor xác nhận cấu hình. Cần owner chấp nhận dấu hiệu HTML, hoặc chạy lại với cấu hình theme đã xác nhận.","kb_ids":["KB-059","KB-060"]}
```

## OQ-sdk-055 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-055","type":"NEEDS_CONFIRMATION","feature_id":"storefront-translations","summary":"Mốc 5 giây (timeout headers đọc từ bundle, KB-056) có phải ngưỡng chính thức không, và widget hiển thị gì khi response translations đến ngay dưới 5 giây?","kb_ids":["KB-056","KB-053"]}
```

## OQ-sdk-056 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-056","type":"OPEN_ISSUE","feature_id":"storefront-translations","summary":"Chưa kiểm trường hợp translations API timeout lúc load rồi buyer gọi lần thứ hai trong cùng page session (vd 'Edit design' trong cart): widget có lấy được bản dịch không hay vẫn hiện chữ gốc?","kb_ids":["KB-057"]}
```

## OQ-sdk-057 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-057","type":"OPEN_ISSUE","feature_id":"storefront-translations","summary":"Mọi evidence về fallback/retry/nhãn thiếu của translations (KB-053..KB-058) đến từ bundle app-v1.js; bundle app-v2.js chưa được kiểm.","kb_ids":["KB-053","KB-054","KB-055","KB-056","KB-057","KB-058"]}
```

## OQ-sdk-058 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-058","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Với customization từ 2 artwork trở lên: design_urls có đúng 1 phần tử cho mỗi artwork không, thứ tự có theo thứ tự artwork trong form không, mỗi URL có lấy đuôi theo design_format riêng của artwork khi các artwork khác định dạng không, và nền tảng có cho phép design_format khác nhau trong cùng customization không? Mới verify được trường hợp 1 artwork (KB-061); phần nhiều artwork chỉ đọc từ bundle (KB-062), các test case nhiều artwork đều skipped.","kb_ids":["KB-062"]}
```

## OQ-sdk-059 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-059","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Khi 1 artwork trong customization nhiều artwork tạo design thất bại, design_urls xử lý thế nào (bỏ phần tử, null, cờ lỗi, hay chặn cả payload)? Yêu cầu không định nghĩa, test case tương ứng skipped.","kb_ids":["KB-062"]}
```

## OQ-sdk-060 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-060","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Bảng ánh xạ design_format → đuôi file của open-platform SDK (svg, eps, ai, jpeg, jpeg_cmyk*, pdf giữ định dạng; còn lại mặc định png) có đúng là hành vi chủ đích không? Mới quan sát nhánh 'rgb' → .png; phần còn lại chỉ đọc từ bundle (KB-063).","kb_ids":["KB-063"]}
```

## OQ-sdk-061 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-061","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Khi widget open-platform chạy trong iframe, payload (kể cả design_urls) có được gửi tới trang cha qua window.parent.postMessage không, và payload đầy đủ gồm những key nào? Mới quan sát nhánh gọi trực tiếp window.teeinblue.onCustomizationCreated (KB-064).","kb_ids":["KB-064"]}
```

## OQ-sdk-062 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-062","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Bundle Shopify theme-embed app-v1.js không có design_urls / onCustomizationCreated, và hằng EVENT_CUSTOMIZATION_CREATED được định nghĩa nhưng không được dispatch (KB-065). Đây là phạm vi chủ đích của TIB-5427 (chỉ open-platform) hay là thiếu sót cần bổ sung cho kênh theme-embed? Cần Dev/PO trả lời.","kb_ids":["KB-065","KB-009"]}
```

## OQ-sdk-063 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-063","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Bundle app-v2.js có giống app-v1.js về design_urls / onCustomizationCreated / EVENT_CUSTOMIZATION_CREATED không? KB-065 chỉ kiểm app-v1.js, trong khi store đang serve app-v2.js (KB-040).","kb_ids":["KB-065","KB-040"]}
```

## OQ-sdk-064 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-064","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Ở kênh theme-embed, cart line-item property _tib_design_link_N (KB-009) có phải cơ chế giao design link theo từng artwork duy nhất không? Điều này mới chỉ suy ra từ việc grep bundle không thấy cơ chế khác.","kb_ids":["KB-065","KB-009"]}
```

## OQ-sdk-065 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-065","type":"OPEN_ISSUE","feature_id":"product-page-settings-config","summary":"Kiểm soát truy cập của design URL trả trong design_urls/design_url chưa có kết luận: test case bảo mật (một design URL có dùng được để lần ra design của customization khác hay không) đang bị chặn chờ PO/Dev. Chưa có oracle cho chiều PERMISSION của feature này.","kb_ids":["KB-061"]}
```

## OQ-sdk-066 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-066","type":"NEEDS_CONFIRMATION","feature_id":"storefront-customization-storage","summary":"'teeinblue-customizations' giữ tối đa bao nhiêu entry (người chạy test ghi khoảng 10, chưa đếm độc lập) và entry bị loại theo tiêu chí nào — timestamp cũ nhất hay thứ tự thêm? Check về draft localStorage khi buyer thao tác nhiều product cần biết giới hạn và thứ tự loại chính xác; hiện chỉ có 1 lượt quan sát, chưa có nguồn dev/spec.","kb_ids":["KB-066"]}
```

## OQ-sdk-067 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-067","type":"OPEN_ISSUE","feature_id":"storefront-customization-storage","summary":"Giới hạn khoảng 10 entry có áp dụng cho key đồng hành 'teeinblue-global-options' và cho cả hai bundle app-v1.js / app-v2.js không? Quan sát KB-066 không ghi bundle/SDK version của store test và chỉ nói về 'teeinblue-customizations'; không được suy giới hạn sang key hay bundle khác khi viết check.","kb_ids":["KB-066","KB-015"]}
```

## OQ-sdk-068 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-068","type":"OPEN_ISSUE","feature_id":"storefront-customization-storage","summary":"Known defect BUG-321..324: field required trong Group ẩn vẫn chặn Add to cart (TC-TIB-6064 Fail 2026-10-16). Testlane hiện ghi passed và bugId đã bị gỡ khỏi case nhưng không có lần chạy lại có ngày. Bug đã fix chưa, fix trên build nào? Cần chạy lại TC-TIB-6063/6064 có ngày + build.","kb_ids":["KB-179"]}
```

## OQ-sdk-069 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-069","type":"OPEN_ISSUE","feature_id":"storefront-layer-visibility","summary":"Known defect BUG-321: field của layer con trong Group ẩn vẫn có trong form storefront, kể cả khi condition buyer-side thoả (TC-TIB-6066, TC-TIB-6067 Fail 2026-10-16; ghi chú '=>> Do bị cache' không có ngày chạy lại; TC-TIB-6065 rỗng). Đã fix chưa? Cần chạy lại có ngày; tách riêng hiệu ứng 'Show this layer on first load' khỏi condition.","kb_ids":["KB-180"]}
```

## OQ-sdk-070 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-070","type":"NEEDS_CONFIRMATION","feature_id":"storefront-customization-storage","summary":"Hành vi đúng của form cá nhân hoá storefront khi artwork có Group ẩn là gì — form không có field của layer trong Group ẩn, required của các field đó không chặn Add to cart, condition trỏ vào layer ẩn hiệu dụng không bao giờ pass (như QA plan/ticket của dev mô tả) — PO có xác nhận không?","kb_ids":["KB-179","KB-180"]}
```

## OQ-sdk-071 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-071","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Layer con bật 'Show this layer on first load' dưới Group ẩn, khi không gắn condition, phải hiện hay không ở lần load đầu, và có field trong form không? (lượt 2026-10-16 không hiện nhưng layer đó còn gắn condition nên chưa tách được hiệu ứng)","kb_ids":[]}
```

## OQ-sdk-072 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-072","type":"OPEN_ISSUE","feature_id":"storefront-layer-visibility","summary":"Buyer preview storefront theo effective visibility (TC-TIB-6068) có giữ nguyên trên build staging sau khi toàn bộ 6 PR của TIB-5584 merge, trên production khi TIB-5584 release, và trên cả hai bundle app-v1.js / app-v2.js không?","kb_ids":["KB-181"]}
```

## OQ-sdk-073 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-073","type":"NEEDS_CONFIRMATION","feature_id":"storefront-layer-visibility","summary":"Với 'Hide this layer on first load' TẮT và nguồn chưa trả lời, layer action Hide có hiện trên artwork preview trên build đã merge không? Nhánh này chỉ có tài liệu dev viết trước khi code còn đổi, chưa test case nào kiểm.","kb_ids":["KB-233"]}
```

## OQ-sdk-074 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-074","type":"NEEDS_CONFIRMATION","feature_id":"storefront-layer-visibility","summary":"PO xác nhận trên build đã merge: điều kiện có nguồn đang bị ẩn được tính là không khớp, linked layer đi theo hiển thị cuối của layer gốc, điều kiện 2 cấp lan theo — và 'nguồn bị ẩn' có bao gồm nguồn nằm trong Group ẩn không (giao với known defect KB-180)? Chỉ có nguồn tài liệu dev.","kb_ids":["KB-235"]}
```

## OQ-sdk-075 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-075","type":"NEEDS_CONFIRMATION","feature_id":"storefront-customization-storage","summary":"Layer không điều kiện và layer Show có giữ nguyên hành vi trên SDK đã có code Hide (bản từ 2026-10-28 03:01:11 GMT hoặc build đã merge) không? Test case regression mới chạy trên SDK cũ.","kb_ids":["KB-236"]}
```

## OQ-sdk-076 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-076","type":"NEEDS_CONFIRMATION","feature_id":"storefront-layer-visibility","summary":"Sau khi deploy production, storefront có thể chạy SDK cũ đã cache trong bao lâu (max-age=14400 hay khác), trong thời gian đó layer Hide hiển thị thế nào (một lượt quan sát cho thấy đảo chiều, BUG-429), và có cần cảnh báo merchant không?","kb_ids":["KB-237"]}
```

## OQ-sdk-077 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-077","type":"OPEN_ISSUE","feature_id":"storefront-layer-visibility","summary":"Các rule Hide trên storefront (KB-231, KB-232, KB-234) có giữ nguyên trên build staging sau khi 6 PR của TIB-5558 merge (2026-10-29), trên production khi TIB-5558 release, và trên bundle app-v1.js không? Lượt PASS duy nhất chạy trước khi merge, chỉ trên app-v2.js.","kb_ids":["KB-231","KB-232","KB-234"]}
```

## OQ-sdk-078 — CONFLICT

```json
{"oq_id":"OQ-sdk-078","type":"CONFLICT","feature_id":"product-page-settings-config","summary":"Chuỗi label của setting lọc media theo variant đang chọn mâu thuẫn giữa hai nguồn; teeinblue không tự supersede nên KB-025 và KB-318 đều UNRESOLVED, CHK-003 không có oracle cho tới khi PO chọn: (a) thay chuỗi trong KB-025 bằng KB-318, (b) giữ cả hai như hai thời điểm (thu phạm vi KB-025 thành 'trước tính năng gán video'), hay (c) giữ base. Chỉ phần chuỗi label bị tranh chấp; các giá trị control khác trong KB-025 không bị claim chạm.","kb_ids":["KB-025","KB-318"],"side_a":"KB-025 (base, quan sát 2026-09-21 trên store1/store2): label là 'Show only the assigned images of the selected variant'.","side_b":"KB-318 (test case PASS 2026-10-22, staging, trước khi các PR merge): label là 'Show only the assigned images and videos of the selected variant' và trang không còn chuỗi cũ."}
```

## OQ-sdk-079 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-079","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Dev xác nhận config key của setting lọc media theo variant vẫn là show_assigned_variant_images_only sau khi tính năng mở rộng sang video (bản đã merge). Mới chỉ thấy trong actualResult.","kb_ids":["KB-319"]}
```

## OQ-sdk-080 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-080","type":"OPEN_ISSUE","feature_id":"product-page-settings-config","summary":"Kết quả kiểm label của setting lọc media theo variant (TC-TIB-6423) chỉ có một lượt PASS trên staging 2026-10-22, trước khi 4 PR của TIB-5428 merge (2026-10-27); cần chạy lại trên bản đã merge / production (sau khi PO chốt conflict label).","kb_ids":["KB-318"]}
```

## OQ-sdk-081 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-081","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"PO/dev xác nhận: đổi assignment mockup/video ↔ variant có chủ ý cần Update/Sync campaign thì storefront mới phản ánh không? Mới chỉ là ghi chú trong actualResult.","kb_ids":["KB-321"]}
```

## OQ-sdk-082 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-082","type":"OPEN_ISSUE","feature_id":"storefront-campaign-media-api","summary":"Lỗi đã biết BUG-359: video bật 'Always load first' chỉ được focus nhưng vẫn ở vị trí thứ 2 trong gallery. Đã fix/retest chưa, trên bản nào? KB-327 không làm oracle.","kb_ids":["KB-327"]}
```

## OQ-sdk-083 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-083","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"PO xác nhận: video bật 'Always load first' và được gán cho variant đang chọn có phải đứng đầu gallery và là item focus không? Một trao đổi nội bộ có nêu như vậy nhưng chưa phải nguồn xác nhận; sau khi fix BUG-359 cần chạy lại case tương ứng.","kb_ids":["KB-327"]}
```

## OQ-sdk-084 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-084","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"PO xác nhận ý định (ảnh hưởng đơn hàng/fulfillment): khi variant chỉ được gán video, form cá nhân hoá và design của đơn hàng hoạt động thế nào? KB-323 chỉ xác nhận gallery và khu vực preview.","kb_ids":["KB-323"]}
```

## OQ-sdk-085 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-085","type":"OPEN_ISSUE","feature_id":"storefront-campaign-media-api","summary":"Các rule gallery theo variant (KB-320, KB-322..KB-326) chỉ có lượt PASS trên staging 2026-10-22, trước khi 4 PR của TIB-5428 merge (2026-10-27); cần chạy lại trên bản đã merge, production và từng bundle SDK.","kb_ids":["KB-320","KB-322","KB-323","KB-324","KB-325","KB-326"]}
```

## OQ-sdk-086 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-086","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"Chạy lại sau merge/production: mọi quan sát và lượt PASS của TIB-5203 (payload campaign v2 + cache) đều chạy trên staging ngày 2026-10-28, TRƯỚC khi 2 PR merge 2026-10-29; chưa rõ dev có đẩy commit sau ~10:30 UTC không; production chưa kiểm. Cần chạy lại TC-TIB-7507 (shape response: có resource_type, không còn các field đã bỏ) trên build sau merge và trên production để xác nhận hành vi đã ship.","kb_ids":["KB-350","KB-352"]}
```

## OQ-sdk-087 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-087","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"Response campaigns/{id}.json đã bỏ một số field (theo TC-TIB-7507). Chưa ai kiểm consumer nào khác (theme custom, renderer, public API) còn đọc các field đã bỏ — Dev/PO xác nhận không có consumer nào bị ảnh hưởng.","kb_ids":["KB-352"]}
```

## OQ-sdk-088 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-088","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"Tập giá trị chính thức của resource_type (mới thấy \"campaign\" / \"platform_product\" ở 1 lượt chạy trước redeploy; TC-TIB-7507 không kiểm giá trị) — Dev xác nhận và chạy lại trên build đã merge.","kb_ids":["KB-351"]}
```

## OQ-sdk-089 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-089","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"Danh sách key artworks[] chính thức của payload platform product sau thay đổi TIB-5203 — mới chỉ thấy trong actualResult của 1 lượt test.","kb_ids":["KB-353"]}
```

## OQ-sdk-090 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-090","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"Shape artworks[]: URL v mới chỉ còn global_option_ids, nhưng URL ?v=1 SDK gọi vẫn có artworks[].global_options (BUG-437). Dev/PO xác nhận shape đúng và trạng thái BUG-437 (sửa/hoãn/chấp nhận); chạy lại trên URL SDK thật sau merge.","kb_ids":["KB-354"]}
```

## OQ-sdk-091 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-091","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"SDK được quan sát lấy platform product qua campaigns/{shopify product id}.json, lệch với kịch bản kiểm thử của dev (platform-products/{uuid}.json). Dev xác nhận endpoint chính thức và platform-products/{uuid}.json còn dùng ở trường hợp nào.","kb_ids":["KB-355"]}
```

## OQ-sdk-092 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-092","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"PO quyết ý định: sau Save artwork + Update/Sync campaign, URL ?v=1 SDK gọi vẫn trả bản cũ (BUG-446) trong khi URL v mới trả bản mới — storefront phải hiện thay đổi ngay hay chấp nhận độ trễ cache (bao lâu)? Rủi ro: buyer đặt hàng với design cũ. Trạng thái BUG-446 chưa rõ dù Jira Done. KB-321 (storefront phản ánh sau Update/Sync, quan sát 2026-10-22 trước khi có cache) có thể đã cũ — cần re-verify trên build sau merge.","kb_ids":["KB-356","KB-321"]}
```

## OQ-sdk-093 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-093","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"PO quyết ý định: sau sửa + Publish platform product, URL ?v=1 SDK gọi vẫn trả bản cũ (BUG-439) — đây là độ trễ cache chấp nhận được hay lỗi? Trạng thái BUG-439 chưa rõ; chạy lại sau merge.","kb_ids":["KB-357"]}
```

## OQ-sdk-094 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-094","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Nhóm hành vi form storefront với Global Option (form tải đủ, giống hệt sau reload, preview + payload customization, 2 layer dùng chung GO chỉ gửi 1 giá trị, GO tự điền khi mở campaign khác cùng trình duyệt) mới chỉ quan sát 1 lượt trên build trước redeploy mà dev yêu cầu recheck. Chạy lại trên build đã merge TIB-5203 và PO/Dev xác nhận đây là hành vi đúng.","kb_ids":["KB-358","KB-359","KB-360","KB-361","KB-362"]}
```

## OQ-sdk-095 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-095","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"Campaign không dùng Global Option (1 input text): form chỉ có input thường và giá trị text còn sau reload — mới quan sát 1 lượt trước redeploy. Chạy lại sau merge và xác nhận hành vi đúng; lưu ý KB-019 (form template không khôi phục lựa chọn sau reload) là phạm vi khác (field phụ thuộc template).","kb_ids":["KB-363"]}
```

## OQ-sdk-096 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-096","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","summary":"Theo dõi BUG-310: trang storefront thật của platform product không render form personalization (console SyntaxError / \"TypeError: e is not iterable\"; tester ghi nguyên nhân là tên category chứa <script> không được escape — rủi ro XSS, buyer không mua được). Trạng thái fix chưa rõ; sau khi sửa cần chạy lại trên trang thật để cập nhật/retire KB-364. PO/Dev cho biết trạng thái và mức ưu tiên.","kb_ids":["KB-364"]}
```

## OQ-sdk-097 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-097","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Form platform product mới chỉ được thấy render trên HTML đã patch (né BUG-310); chưa có quan sát trên trang thật. Chạy lại trên trang thật (sau khi BUG-310 được xử lý hoặc với category sạch) trên build đã merge.","kb_ids":["KB-365"]}
```

## OQ-sdk-098 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-098","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Request /products/<id>.js trả 404 mỗi lần load campaign — chưa rõ là gì, có từ trước TIB-5203 không, và có phải lỗi cần theo dõi không.","kb_ids":["KB-366"]}
```

## OQ-sdk-099 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-099","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"PO/Dev xác nhận config.maps_api_key (Mapbox, tiền tố 'pk.') được phép xuất hiện trong response public không cần auth của campaigns/{id}.json; nếu chính sách là không public key nào thì đây là lỗi.","kb_ids":["KB-367"]}
```

## OQ-sdk-100 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-100","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"PO quyết ý định: sau đổi setting store (PUT /api/instances/{id}/config 200), config trong URL SDK ?v=1 và link preload vẫn trả giá trị cũ (BUG-440) — setting phải áp dụng ngay sau reload hay chấp nhận độ trễ cache (bao lâu)? Trạng thái BUG-440 chưa rõ. KB-319 (quan sát 2026-10-22 trước khi có cache) có thể đã cũ — re-verify sau merge.","kb_ids":["KB-368","KB-319"]}
```

## OQ-sdk-101 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-101","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Storefront preview của sản phẩm có Group khoảng 250 layer: TC-TIB-7632 chỉ đếm DOM toàn trang, không tách popup Preview khỏi mockup chính, không so với trước fix. Cần kiểm lại phần tử thuộc popup Preview. Không dùng quan sát này để giải conflict của KB-011 hay thay mô tả KB-042.","kb_ids":["KB-394"]}
```

## OQ-sdk-102 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-102","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","summary":"Chạy lại sau merge và trên production cho storefront preview của sản phẩm có Group nhiều layer (lượt chạy 2026-10-29 trước khi PR thứ hai của TIB-5633 cập nhật lần cuối; ngày deploy production chưa rõ).","kb_ids":["KB-394"]}
```

## OQ-sdk-103 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-103","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Strava (route maps, strava-upload) có chạy được trên staging không, và trên production thế nào?","kb_ids":["KB-409"]}
```

## OQ-sdk-104 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-104","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"photo_endpoint=snap: Portal có setting nào cho giá trị này không, ai set được, URL snap trên staging có trùng URL photo-api không, và trên production trỏ đâu?","kb_ids":["KB-410"]}
```

## OQ-sdk-105 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-105","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Trên staging, photo-api và preconnect cdn có còn trỏ host production không, và ai được kiểm phía production? Config teeinblue cấm môi trường production, nên how_to_test của KB-411 chưa có người thực hiện.","kb_ids":["KB-411"]}
```

## OQ-sdk-106 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-106","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Số đo preconnect, connection reuse, TTFB có phải kết luận trên Chrome thật thay vì headless không, và quy tắc này áp cho những check nào?","kb_ids":["KB-412"]}
```

## OQ-sdk-107 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-107","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"Vế \"tab cũ, add-on từ hết hàng thành có hàng, SDK vẫn chặn ATC tới khi reload\" của KB-442 (TIB-5510 #55732, 2026-10-27) có chỉ đúng khi store đã đặt blockAtcUnavailableAddon = true không, sau khi #56209 (2026-11-02) đổi mặc định thành tắt?","kb_ids":["KB-442","KB-443"]}
```

## OQ-sdk-108 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-108","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Endpoint upload nào trả Retry-After, và endpoint nào expose header đó qua CORS?","kb_ids":["KB-451"]}
```

## OQ-sdk-109 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-109","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"Store chưa đặt blockAtcUnavailableAddon (mặc định tắt, KB-443), add-on hết hàng: bấm ATC thì sản phẩm chính có vào giỏ không, có message gì không, và buyer bị chặn ở đâu?","kb_ids":["KB-443"]}
```

## OQ-sdk-110 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-110","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"Function kiểm add-on đối chiếu child line bằng property nào: _tib_customization_id (KB-416) và _customization_id (KB-009, quan sát 2026-09-12 trên sản phẩm không nêu add-on) là hai property khác nhau hay cùng một property bị lệch tên? QA đề xuất (KB-542, CBS-155, 2026-11-10): hai property trên hai line, line chính mang _customization_id, addon charge line mang _tib_customization_id cùng giá trị; Dev xác nhận?","kb_ids":["KB-416","KB-009","KB-542"]}
```

## OQ-sdk-111 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-111","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Portal hiện có block General error messages với key request_rate_limited, request_rate_limited_retry_after trong product page content không? KB-449 (TIB-5539 #55557, 2026-10-23) nói có; KB-002 của object translation (2026-09-21) liệt kê 21 section không có block này.","kb_ids":["KB-449"]}
```

## OQ-sdk-112 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-112","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"Đổi toggle hoặc tên menu của Quick navigation thì URL SDK campaigns/{id}.json?v=1 có trả giá trị mới ngay không? KB-427 (TIB-5349 #52793, 2026-09-30, PR còn mở) nói cache được xoá ngay; KB-356, KB-357, KB-368 (2026-10-28) thấy URL này vẫn trả bản cũ sau các thao tác khác.","kb_ids":["KB-427","KB-356","KB-357","KB-368"]}
```

## OQ-sdk-113 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-113","type":"NEEDS_CONFIRMATION","feature_id":"storefront-campaign-media-api","summary":"Hàm xoá cache campaign dùng chung của KB-435 có xoá cache mà URL SDK ?v=1 đọc không, và có chạy với campaign có store liên kết đầy đủ không? KB-356 (2026-10-28) thấy URL này trả bản cũ sau sửa artwork + sync.","kb_ids":["KB-435","KB-356","KB-357"]}
```

## OQ-sdk-115 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-115","type":"OPEN_ISSUE","feature_id":"form-artwork-navigation","summary":"TIB-5349 merge và deploy lên staging ở build nào, ngày nào, và đã lên production chưa? Nguồn không nêu build và ngày deploy, nên chưa rõ 16 item của ticket này đã ship hay chưa. Comment nguồn #52793 ghi PR đang mở lúc viết.","kb_ids":["KB-413","KB-414","KB-422","KB-423","KB-424","KB-425","KB-426","KB-427","KB-428","KB-429","KB-430","KB-431","KB-432","KB-433","KB-434","KB-435"]}
```

## OQ-sdk-116 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-116","type":"OPEN_ISSUE","feature_id":"required-addon-validation","summary":"TIB-5510 merge và deploy lên staging ở build nào, ngày nào, và đã lên production chưa? Nguồn không nêu build và ngày deploy, nên chưa rõ 13 item của ticket này đã ship hay chưa.","kb_ids":["KB-416","KB-417","KB-437","KB-438","KB-439","KB-440","KB-441","KB-442","KB-443","KB-444","KB-445","KB-446","KB-455"]}
```

## OQ-sdk-117 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-117","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","summary":"TIB-5539 merge và deploy lên staging ở build nào, ngày nào, và đã lên production chưa? Nguồn không nêu build và ngày deploy, nên chưa rõ 7 item của ticket này đã ship hay chưa.","kb_ids":["KB-418","KB-419","KB-447","KB-448","KB-449","KB-450","KB-451"]}
```

## OQ-sdk-118 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-118","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","summary":"TIB-5418 merge và deploy lên staging ở build nào, ngày nào, và đã lên production chưa? Nguồn không nêu build và ngày deploy, nên chưa rõ 6 item của ticket này đã ship hay chưa.","kb_ids":["KB-408","KB-420","KB-421","KB-452","KB-453","KB-454"]}
```

## OQ-sdk-120 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-120","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"PO xác nhận ý định: đơn thiếu add-on hoặc add-on không đủ số lượng (parentQuantity * rate) phải bị chặn hoàn tất ở Checkout đúng như KB-416, KB-417 không? Hai item chạm đơn hàng, chỉ có nguồn dev.","kb_ids":["KB-416","KB-417"]}
```

## OQ-sdk-121 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-121","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"PO xác nhận ý định: popup cross-sell, khi tổ hợp option không tồn tại, phải tự chuyển sang variant có thật và luôn hiện giá thực của variant đó như KB-452 không? Item chạm giá, chỉ có nguồn dev.","kb_ids":["KB-452"]}
```

## OQ-sdk-122 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-122","type":"NEEDS_CONFIRMATION","feature_id":"form-artwork-navigation","summary":"Nhập quá 255 ký tự vào ô Menu Item's name thì ô chặn gõ hay báo lỗi khi lưu, và lỗi hiện ra thế nào?","kb_ids":["KB-431"]}
```

## OQ-sdk-123 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-123","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Nguyên văn mặc định của câu chung 429, câu 429 có thời gian, câu lỗi mạng và câu lỗi upload chung là gì? KB không có text, nên các check chỉ nêu được loại câu.","kb_ids":["KB-418","KB-447","KB-450","KB-451"]}
```

## OQ-sdk-124 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-124","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần cấu hình gì để popup cross-sell hiện trên storefront (ngoài checkbox Show Cross-sell Personalization của KB-028)? KB chưa có setup này.","kb_ids":["KB-420","KB-421"]}
```

## OQ-sdk-125 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-125","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"\"Áp dụng cho tất cả merchant\" của KB-455 (TIB-5510 #55732, 2026-10-27) còn đúng cho cả chặn ATC ở SDK và rule Checkout không, hay chỉ còn đúng cho rule Checkout, sau khi #56209 (2026-11-02, KB-443) đổi chặn ATC ở SDK thành mặc định tắt cho toàn bộ store?","kb_ids":["KB-455","KB-443"]}
```

## OQ-sdk-163 — CONFLICT

```json
{"oq_id":"OQ-sdk-163","type":"CONFLICT","feature_id":"template-switch-photo-sync","conflict_group":"CONF-CBS098-01","summary":"Hành vi tại độ lệch tỉ lệ đúng 5% (tính theo layer đích, ví dụ 1000×1000 → 1000×1050) khi đổi template: giữ position không warning hay reset kèm warning. Hai nguồn nói ngược nhau, chưa phân xử; không phía nào là oracle.","side_a":"KB-494 (OBSERVED_CURRENT/LOW): Testlane TC-06 của QA-3415, chạy 2026-10-21 trên staging SDK app-v1.js 2026-10-21 05:56 GMT, 2/2 lượt: cặp lệch đúng 5% bị reset về placement mặc định và hiện warning; phép tính trên trang cho 0.05000000000000006 > 0.05. Bug draft chưa file, dev chưa trả lời.","side_b":"KB-515 (CONFIRMED_EXPECTED/LOW, đang UNRESOLVED): dev trả lời Q1 ở Jira TIB-5566 comment 55235 (2026-10-21): độ lệch đúng 5% được tính là cùng tỉ lệ — giữ position, không warning.","kb_ids":["KB-494","KB-515"],"needs":"PO/Dev phân xử: đúng 5% là giữ hay reset; nếu giữ là đúng thì đây là bug làm tròn số thực (cần ticket theo dõi)."}
```

## OQ-sdk-164 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-164","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Xoá ảnh ở template A rồi đổi sang B thì B rỗng, không warning, ảnh mới ở B bắt đầu ở placement mặc định (KB-499): chỉ là quan sát TC-36 (2026-10-21), không có căn cứ expected; localStorage vẫn giữ key position cũ sau khi xoá ảnh.","kb_ids":["KB-499"],"needs":"Dev/PO xác nhận nguyên văn đây là hành vi đúng, và việc giữ key position cũ là chủ đích."}
```

## OQ-sdk-165 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-165","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Template đích có 2 photo layer cùng option title nhưng khác tỉ lệ thì mỗi layer được xét riêng, warning chỉ ở field của layer reset (KB-500): chỉ là quan sát TC-37, không có căn cứ expected.","kb_ids":["KB-500"],"needs":"Dev/PO xác nhận nguyên văn việc xét giữ/reset và warning theo từng layer."}
```

## OQ-sdk-166 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-166","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Layer populate target (TIB-5302) bị sync bỏ qua và theo luật populate (KB-504, lời dev): TC-18 chưa chạy trên build thật; hành vi chạm object artwork (populate-values) mà run này không ghi vào. artwork có conflict riêng về ngưỡng 0.05 của populate (khác đại lượng, không gộp).","kb_ids":["KB-504"],"needs":"Chạy TC-18; operator quyết có cần CCR riêng ghi tham chiếu chéo ở artwork-render/populate-channels-config."}
```

## OQ-sdk-167 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-167","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Đổi template nhanh liên tục và popup desktop / mobile 390×844 vẫn giữ position (KB-513): chỉ là quan sát (TC-26; TC-28 trên Testlane chỉ ghi tạm dừng), không có căn cứ expected; nhánh \"Enable Reposition on main gallery\" = ON chưa kiểm.","kb_ids":["KB-513"],"needs":"Dev/PO xác nhận expected cho đổi nhanh và popup/mobile; chạy nhánh toggle ON."}
```

## OQ-sdk-168 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-168","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Chữ đầy đủ của warning tỉ lệ (KB-514) chỉ có ở lượt chạy SDK cache cũ, không hợp lệ; lượt chạy sạch chỉ ghi phần đầu \"Your photo doesn't match this design's aspect ratio\".","kb_ids":["KB-514"],"needs":"Chữ đầy đủ từ nguồn (dictionary/dev) hoặc lượt chạy sạch ghi nguyên chữ."}
```

## OQ-sdk-169 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-169","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Đổi Size hoặc option map sang template/artwork khác chạy cùng logic giữ/reset (KB-503) chỉ có lời dev đọc code; TC-14, TC-15 chưa chạy.","kb_ids":["KB-503"],"needs":"Chạy TC-14, TC-15 trên build có TIB-5566."}
```

## OQ-sdk-170 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-170","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Layer Multiple Uploads có reposition giữ một position cho ảnh ghép khi đổi template (KB-501) chưa có lượt chạy (TC-19, TC-20).","kb_ids":["KB-501"],"needs":"Chạy TC-19, TC-20."}
```

## OQ-sdk-171 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-171","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Ảnh không sync giữa field type khác nhau (KB-502) chưa có lượt chạy (TC-21..TC-23, TC-34).","kb_ids":["KB-502"],"needs":"Chạy TC-21..TC-23, TC-34."}
```

## OQ-sdk-172 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-172","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Edit design từ cart và order design / file in dùng position đã giữ (KB-505) chỉ dựa trên dev đồng ý đề xuất QA; TC-16 phần Edit và TC-17 chưa chạy; order KB-369 không nói về position.","kb_ids":["KB-505"],"needs":"Chạy TC-16 (Edit design) và TC-17 (order design)."}
```

## OQ-sdk-173 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-173","type":"OPEN_ISSUE","feature_id":"template-switch-photo-sync","summary":"Photo layer dùng Global Option không thuộc feature này (TIB-5416). Trên staging khi TIB-5416 bị revert, layer Global Option dùng chung một position cho mọi template (global-option có known defect riêng); khi TIB-5416 lên lại cần xem lại hai phía.","kb_ids":[],"needs":"Theo dõi TIB-5416; không viết check sync cho photo layer Global Option dựa trên feature này."}
```

## OQ-sdk-174 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-174","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Field status Testlane của task TIB-223 (QA-3415) không phản ánh kết quả: mọi test case đều \"passed\", kể cả TC-06 ❌, TC-30 ❌ và các TC chưa chạy. Kết quả của KB-490, KB-492, KB-498 chỉ đọc được ở actualResult.","kb_ids":["KB-490","KB-492","KB-498"],"needs":"QA sửa status trên Testlane cho khớp actualResult."}
```

## OQ-sdk-175 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-175","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Scale position theo layer đích (KB-491) và mức giãn trong ngưỡng 5% (KB-495) mới có số đo một lượt (TC-02, TC-09); chưa kiểm nhiều cặp kích thước.","kb_ids":["KB-491","KB-495"],"needs":"Chạy thêm vài cặp kích thước nếu cần check định lượng."}
```

## OQ-sdk-176 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-176","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Tên setting: KB-490 nói \"khi bật sync giữa template\", KB-513 nói nhánh \"Enable Reposition on main gallery\"; product-page-settings hiện chỉ ghi \"Sync customer's selection between same title options\", \"Enable Text Reposition on main gallery\" và \"Photo Reposition on Mockup\". Chưa rõ control nào ứng với hai tên này.","kb_ids":["KB-490","KB-513"],"needs":"Dev/QA chỉ đúng control trong Product page settings."}
```

## OQ-sdk-177 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-177","type":"NEEDS_CONFIRMATION","feature_id":"storefront-customization-storage","summary":"Sau reload, template picker không khôi phục nhưng chọn lại template thì ảnh và position đã giữ hiện lại đúng (KB-506): chỉ là quan sát TC-35 (2026-10-22), không có căn cứ expected. Vế picker không khôi phục trùng nghĩa KB-019 (không thay KB-019).","kb_ids":["KB-506"],"needs":"Dev/PO xác nhận expected sau reload."}
```

## OQ-sdk-178 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-178","type":"NEEDS_CONFIRMATION","feature_id":"storefront-customization-storage","summary":"Position buyer sửa tay trong localStorage không bị clamp hay bỏ qua: customization POST trả 201 lưu nguyên giá trị, \"abc\" gây lỗi console, thumbnail cart mất ảnh hoặc lệch (KB-507, quan sát TC-30 ❌ 2/2). Bug draft chưa file, dev chưa trả lời; order design với các giá trị này chưa kiểm. Cùng dạng với known issue ở artwork (server 201 với payload buyer chèn).","kb_ids":["KB-507"],"needs":"PO/Dev quyết đây là giới hạn chấp nhận hay bug; ý định validate phía server."}
```

## OQ-sdk-179 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-179","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Tên file payload không render, SVG có script / HTML đổi đuôi .jpg bị từ chối với thông báo \"Cannot upload because the image is too small. Please upload a bigger image\", payload text hiển thị literal (KB-508): chỉ là quan sát TC-31..TC-33, không có căn cứ expected; thông báo cho file sai định dạng có thể không đúng; order design của TC-33 dùng đơn tạo trên SDK cũ.","kb_ids":["KB-508"],"needs":"PO xác nhận thông báo đúng cho file sai định dạng; chạy lại order design trên SDK mới."}
```

## OQ-sdk-180 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-180","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Namespace id SVG khi vector layer áp màu (KB-509) có nguồn dev summary TIB-5501 nhưng product tắt allow_dev_doc_supersede nên ở OBSERVED_CURRENT/LOW; quan sát chỉ khi mọi layer cùng một Color option — \"mỗi layer giữ màu riêng\" khi nhiều Color option chưa kiểm (TC-01, TC-03 tạm dừng).","kb_ids":["KB-509"],"needs":"Chạy với nhiều Color option; xác nhận có cần nguồn spec/PO để lên expected."}
```

## OQ-sdk-181 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-181","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Vector layer chưa áp màu không bị namespace id (KB-510) có nguồn dev summary TIB-5501, bị hạ OBSERVED_CURRENT/LOW; vế render qua <image href> chỉ là quan sát TC-18.","kb_ids":["KB-510"],"needs":"Xác nhận nếu cần dùng làm expected."}
```

## OQ-sdk-182 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-182","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Prefix id được sinh lại mỗi lần đổi màu hay cố định theo layer (KB-512 chỉ là quan sát phụ TC-26): dev chưa trả lời vế này của Q3 (TIB-5501).","kb_ids":["KB-512"],"needs":"Dev trả lời vế prefix của Q3."}
```

## OQ-sdk-183 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-183","type":"NEEDS_CONFIRMATION","feature_id":"storefront-customization-storage","summary":"Field status Testlane của task TIB-223 không phản ánh kết quả (mọi TC \"passed\", kể cả TC-30 ❌ và TC chưa chạy); KB-506..KB-508 đọc kết quả ở actualResult.","kb_ids":["KB-506","KB-507","KB-508"],"needs":"QA sửa status trên Testlane cho khớp actualResult."}
```

## OQ-sdk-184 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-184","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Kết quả QA-3394 (TC-18, TC-26, 2026-10-08) không ghi build portal/SDK nên KB-509, KB-510, KB-512 chưa gắn được với bản đã test.","kb_ids":["KB-509","KB-510","KB-512"],"needs":"Chạy lại có ghi build, hoặc QA bổ sung build vào kết quả."}
```

## OQ-sdk-185 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-185","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","summary":"Known issue chưa rõ nội dung: vector layer có Drop shadow, đổi màu khi SVG trùng id với layer khác — Testlane TC-05 của task TIB-166 failed, gắn BUG-255; không ngày chạy, không người xác nhận, actualResult rỗng. Không nạp KB.","kb_ids":[],"needs":"QA/Dev cho biết nội dung BUG-255, ngày, build, đã ship chưa."}
```

## OQ-sdk-186 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-186","type":"NEEDS_CONFIRMATION","feature_id":"storefront-customization-storage","summary":"KB-015 (shape của teeinblue-customizations, quan sát 2026-09) không liệt kê key position; sau TIB-5566 localStorage có key position dạng 0–1 (KB-491, KB-499). KB-015 và check BASELINE dựa trên nó có thể đã lỗi thời.","kb_ids":["KB-015"],"needs":"Quan sát lại shape localStorage trên SDK hiện tại."}
```

## OQ-sdk-187 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-187","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-012 “Gap: luong Upload logo day du (chon file, preview, luu) hoan toan chua test -- khong co duong revert an toan xac dinh duoc trong run nay” của feature product-page-settings-config. missing_or_unresolved_oracle"}
```

## OQ-sdk-188 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-188","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-016 “Gap: gia tri hex chinh xac cua ~13 color-picker va lua chon dang chon cua cac icon-only swatch (Font size, Toggle style, Alignment, Field's border radius) KHONG doc duoc qua accessibility tree” của feature product-page-settings-config. missing_or_unresolved_oracle"}
```

## OQ-sdk-189 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-189","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-017 “GET /api/instances?trashed tra ve field sdk_version va .config (~27 key) cho ca 2 instance trong 1 lan goi account-wide” của feature product-page-settings-config. missing_or_unresolved_oracle"}
```

## OQ-sdk-190 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-190","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-018 “Tuong quan (INFERRED, KHONG PHAI contract da xac nhan) giua ~27 key trong .config va cac control UI da quan sat -- khong duoc dung nhu data contract field-by-field” của feature product-page-settings-config. missing_or_unresolved_oracle"}
```

## OQ-sdk-191 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-191","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-019 “GET /api/settings fire tren trang nay nhung CHUA khop field cu the nao voi 1 trong 67 control da quan sat” của feature product-page-settings-config. missing_or_unresolved_oracle"}
```

## OQ-sdk-192 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-192","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-020 “CFL-005 UNRESOLVED: config_registry.instance.config (~38 key schema, API-OP-002) khong khop .config thuc te (~27 key, API-OP-001) -- chi 1 ten key trung, KHONG tu resolve” của feature product-page-settings-config. missing_or_unresolved_oracle"}
```

## OQ-sdk-193 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-193","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-021 “CFL-004 UNRESOLVED (goc rieng cua FEAT-08): sdk_version=2 ca 2 instance (evidence_b) doi lap voi baseline storefront 2026-09-12 (store1=v1) va hoi tu voi storefront re-check 2026-09-21 -- khong tu chon phia dung” của feature product-page-settings-config. missing_or_unresolved_oracle"}
```

## OQ-sdk-194 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-194","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-022 “Gap: write-path (Save/Reset) hoan toan chua co evidence -- nut hien dien/enabled nhung chua tung duoc click” của feature product-page-settings-config. missing_or_unresolved_oracle"}
```

## OQ-sdk-195 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-195","type":"NEEDS_CONFIRMATION","feature_id":"product-page-settings-config","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-023 “Gap: bien thien permission/role tren /product-page-settings hoan toan chua duoc quan sat -- chi 1 role (owner) duoc test” của feature product-page-settings-config. missing_or_unresolved_oracle"}
```

## OQ-sdk-196 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-196","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-002 “Chọn variant (Color/Size) cập nhật giá hiển thị đúng (SDK v1, store1)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-197 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-197","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-003 “Personalization dependency 2 cấp: chọn template hé lộ đúng bộ field phụ thuộc; chọn breed cấp cha hé lộ thêm field con bắt buộc (SDK v1, store1, template 1 và 2)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-198 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-198","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-004 “Validation chặn submit khi thiếu field cá nhân hoá, hiện lỗi inline theo field (SDK v1, store1)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-199 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-199","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-005 “Personalization dependency cha-con: chọn field cấp cha hé lộ field con lồng, cặp cha+con là 1 đơn vị required (SDK v2, store2, template 2)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-200 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-200","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006 “Validation 'This field is required!' vẫn gắn với heading cha cho tới khi field con lồng cũng được chọn (SDK v2, store2)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-201 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-201","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-007 “Add-to-cart sau khi điền đủ personalization (SDK v1, store1) — CFL-001 UNRESOLVED, chưa thể kết luận pass hay fail” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-202 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-202","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-008 “Add-to-cart hoàn tất thành công toàn trình sau khi điền đủ personalization (SDK v2, store2)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-203 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-203","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-009 “Cập nhật quantity trong cart tăng total_price tuyến tính, cleanup về 0 thành công (SDK v2, store2)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-204 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-204","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011 “Nút Preview mở lightbox mockup TĨNH, ảnh không đổi theo lựa chọn cá nhân hoá (SDK v1, store1, 1 sample)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-205 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-205","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-012 “Mockup SVG sống cập nhật theo layer-id khớp field-id (SDK v2, store2, 1 sample)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-206 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-206","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-015 “Pre-flight check khi theme app-block CHƯA enable (enabled=false) hoặc endpoint lỗi — chưa test” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-207 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-207","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-017 “Xác minh nhãn hiển thị nhất quán giữa heading nhóm field (cha) và field con cùng khung (SDK v2, store2) — CFL-002, không khẳng định là bug” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-208 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-208","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-018 “Coverage gap: template 1 và 3 chưa test (cả 2 SDK); đường 'edit personalization từ cart' chưa xác nhận tồn tại (SDK v2)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-209 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-209","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-019 “Hành vi field cá nhân hoá khi buyer đổi variant SAU KHI đã điền — reset hay giữ nguyên? (chưa test, cả 2 SDK)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-210 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-210","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-020 “Buyer đã login, non-US market/locale/currency, mobile/tablet viewport — chưa test” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-211 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-211","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-021 “Storefront phân biệt đúng campaign ĐÃ publish (truy cập/mua được) với object CHƯA publish (không truy cập được) — chưa re-test với credential hợp lệ trong run này” của feature storefront-buyer-facing. current_behavior_only"}
```

## OQ-sdk-212 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-212","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-022 “'Generate test design' / preview storefront trước khi publish — chưa khám phá” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-213 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-213","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-026 “Field grouped_clipart (Hairstyle, Cat Breed #1/#2) yêu cầu ĐỦ 2 bước (click radio nhóm + click thumbnail con) mới có giá trị hợp lệ; ADD TO CART thất bại thật nếu thiếu bước con (SDK v2, store2, template 2)” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-214 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-214","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-030 “Gap: Post-ATC persistence của localStorage draft trên SDK v1 (store1) — CHƯA xác nhận vì store1 chưa từng tới ATC trong bất kỳ run nào” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-215 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-215","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-032 “CFL-003 UNRESOLVED: liệu framing 'ATC store2/SDK v2 known-working' kế thừa từ 2026-09-12 có do automation bỏ sót bước click con của grouped_clipart, hay 2-step thực sự luôn là điều kiện đã tồn tại từ trước — chưa thể kết luận” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-216 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-216","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-033 “SDK bundle/version marker phuc vu cho campaign 2595 (script src + widget root class) -- re-check baseline, lien quan CFL-004, KHONG khang dinh phien ban nao 'dung'” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-217 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-217","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-038 “CFL-004 UNRESOLVED: SDK version thuc su dang serve cho tung store (campaign 2595) mau thuan giua 3 nguon evidence portal+storefront -- KHONG tu chon 1 phia lam oracle mac dinh” của feature storefront-buyer-facing. missing_or_unresolved_oracle"}
```

## OQ-sdk-218 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-218","type":"OPEN_ISSUE","feature_id":"template-switch-photo-sync","summary":"Curve Text (GraphQL type: \"curve-text\") không có affordance Reposition nào ở cả hai cơ chế (KB-516). Chưa xác nhận đây là ý định thiết kế hay giới hạn hiện tại — QA chỉ xác nhận hành vi quan sát được (2026-10-02, QA-3374 TC-61), TC-61 chỉ phủ Single-line Text. Người trả lời: PO."}
```

## OQ-sdk-219 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-219","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Ranh giới \"Portal chỉ có công tắc BẬT/TẮT Reposition, cơ chế thật chỉ test được trên storefront\" (KB-517) có đúng không, khi nút seller 'Re-position' trong Artwork Editor (KB-521) cũng nằm trong Portal? Chưa PO/Dev nào xác nhận. Người trả lời: Dev."}
```

## OQ-sdk-220 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-220","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Popup Reposition đứng riêng chỉ liệt kê target đã customize (KB-518) có đúng cả ở staging không? Staging hiện 6 target trong popup còn production chỉ 2 trên fixture tương tự, chưa giải thích được (do customize hay do build). Người trả lời: Dev."}
```

## OQ-sdk-221 — CONFLICT

```json
{"oq_id":"OQ-sdk-221","type":"CONFLICT","feature_id":"product-page-settings-config","summary":"Nhãn đúng của toggle 'Enable Reposition on main gallery' ở build hiện tại là gì, và toggle này có thật sự đổi hẳn cơ chế UI Reposition (inline main gallery khi BẬT, popup riêng khi TẮT) không (CBS-128 CLAIM-04)? Candidate KB-529 CONFLICTED với KB-026, requires_human_decision=true, chưa có input/approvals.json nên KB-529 không publish — chỉ giữ OQ này. Người trả lời: Dev.","side_a":"FACT-120 (QA, xác nhận 2026-09-25, lại 2026-10-16, QA-3374/QA-3410): nhãn \"Enable Reposition on main gallery\"; toggle BẬT thì không có nút Reposition riêng, nút+khung kéo thả hiện trực tiếp trên main gallery; TẮT thì có nút riêng mở popup.","side_b":"KB-026 (bootstrap, 2026-09-21): nhãn \"Enable Text Reposition on main gallery\" = unchecked, quan sát trực tiếp trên portal cả hai store explorer; cùng nhãn trong checklist product-page-settings-config.json (~dòng 119)."}
```

## OQ-sdk-222 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-222","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Với Clipart/Group of Clipart/Vector Category, việc tự select artwork trên main gallery khi chọn giá trị radio (KB-519) có phải là control Reposition chính thức không? Chỉ dựa trên screenshot QA, không có TC, TC-08 cần retest theo cơ chế này. Người trả lời: Dev."}
```

## OQ-sdk-223 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-223","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Static Image/Static Vector bật Reposition có thật sự render component .tee-static-reposition trong panel form không (KB-520), khi BUG-12 (không render field nào trên storefront) bị QA skip 2026-10-29 vì issue đã Done, chưa kết luận? Người trả lời: Dev."}
```

## OQ-sdk-224 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-224","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Nút 'Re-position' của seller trong Artwork Editor (KB-521) có hoạt động như mô tả không? TC-19 (QA-3410) ⏸️ chưa kết luận: Form Mode:Preview không persist, cần xác nhận cách vào đúng Live preview. Ranh giới với KB-517 (\"Portal chỉ có công tắc\") chưa được PO/Dev xác nhận. Người trả lời: Dev."}
```

## OQ-sdk-225 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-225","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Cơ chế kích hoạt Reposition của Clipart Category (chọn radio khác, ~400ms hiện control, mất sau Add to cart — KB-522) có đúng ở mọi campaign và là hành vi thiết kế không? Mới verify tay một campaign (2026-09-27), không có TC riêng; tick TC-08 trên Jira từng ❌ do script cold-start flaky. Người trả lời: Dev."}
```

## OQ-sdk-226 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-226","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Công thức lưu vị trí tỉ lệ cho Category/Image layer (delta / kích thước ô kéo .tee-drr của layer — KB-524) có đúng cho ô không vuông và theo build production hiện hành không? Chỉ khớp 4 số lẻ trong một phép đo trên production không ghi lại build; verdict release-verification tổng thể là INCONCLUSIVE (3/8 TC PASS). Người trả lời: Dev."}
```

## OQ-sdk-227 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-227","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Text layer lưu vị trí px tuyệt đối (khác Category/Image layer lưu tỉ lệ 0-1 — KB-525/KB-524) có phải là hành vi chủ ý và còn đúng ở build hiện tại không? Chỉ đo tay trên staging (TC-37, 2026-09-27), không có TC riêng cho đơn vị lưu của Text. Người trả lời: Dev."}
```

## OQ-sdk-228 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-228","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Linked copy có base size khác origin sync position/scale theo tỉ lệ tương ứng (không \"y hệt origin\" như TIB-5265 — KB-526) có được Dev xác nhận là hành vi đúng không? Mới đo một fixture (ratio ~0.67, 2026-10-05); TC-38 chỉ test copy cùng kích thước nên chưa phủ ca base size khác nhau. Người trả lời: Dev."}
```

## OQ-sdk-229 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-229","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Sync scale của linked copy trên storefront thật (cả POSITION và SCALE) có đúng như trong admin Live preview không (KB-527)? Mới verify SCALE trong Live preview (2026-10-05, không save); POSITION trên storefront thật cần đo lại. Người trả lời: Dev."}
```

## OQ-sdk-230 — CONFLICT

```json
{"oq_id":"OQ-sdk-230","type":"CONFLICT","feature_id":"template-switch-photo-sync","summary":"Server-side design-file render có áp đúng transform của nguồn cho linked copy không (KB-528)? FACT-143 cũ (bên ngoài canon, trong qa-rules local product_facts.md) nói KHÔNG; TC-38 PASS 2026-10-06 (BUG-215 Passed) đo pixel cho thấy CÓ. Build không ghi lại ở cả hai lần đo, chưa kiểm lại trên production sau fix. Người trả lời: Dev.","side_a":"FACT-143 cũ (2026-10-05, trước khi đảo ngược cùng ngày): server-side design-file render KHÔNG áp transform đã sync đúng ở client — copy rơi về default (không scale), dù order data chỉ có override cho origin.","side_b":"TC-38 PASS 2026-10-06 (QA-3374, BUG-215 Passed, staging): đo lại bbox, nguồn+copy cùng 167×173px, cùng rotate ~44°, chỉ lệch vị trí in khác trên áo — linked copy nhận đúng transform nguồn trong render file."}
```

## OQ-sdk-231 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-231","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Cơ chế sync_between_templates chỉ đồng bộ selection của buyer, còn default value do seller đặt là độc lập theo từng layer/template (trừ Global Template/Global Option) — có đúng là hành vi PO/Dev chốt không (KB-530)? Expected do QA chốt 2026-09-11 (QA-3350 TC-42, QA-3286 TC-01), BR-12 từng viết sai và đã rút lại; không có nguồn PO/Dev. Người trả lời: Dev."}
```

## OQ-sdk-232 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-232","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Ngoại lệ Global Template: local template kế thừa default của GT layer (replica không ghi default riêng), seller không override được ở local — có đúng là hành vi PO/Dev chốt không (KB-531)? Expected do QA viết (QA-3350 TC-41), không có nguồn PO/Dev. Người trả lời: Dev."}
```

## OQ-sdk-233 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-233","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Ngoại lệ Global Option: layer liên kết cùng một GO dùng chung default của GO và đổi default GO propagate tới mọi layer liên kết — có đúng là hành vi PO/Dev chốt không (KB-532)? Expected do QA viết (QA-3350 TC-24/TC-26); chưa có TC kiểm riêng giữa hai template khác nhau. Người trả lời: Dev."}
```

## OQ-sdk-234 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-234","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Cross-type mismatch: khi hai template non-GT có Color option cùng Option title nhưng khác Color type (Solid vs Color Sequence) thì template đích không đổi (phương án a) — có phải hành vi PO/Dev chọn không (KB-533)? QA chọn phương án (a) 2026-09-11 (QA-3350 TC-56) trong 3 phương án (a không đổi / b blank / c báo lỗi), chưa ai xác nhận. Người trả lời: PO."}
```

## OQ-sdk-235 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-235","type":"NEEDS_CONFIRMATION","feature_id":"template-switch-photo-sync","summary":"Tiêu chí match khi sync selection giữa template có đúng là Option title cộng personalization type/settings (Layer name KHÔNG phải tiêu chí, Layer name khác nhau vẫn sync) không (CBS-130 CLAIM-01)? Không có test case kiểm riêng ca 'Layer name khác nhau vẫn sync' (ca âm Layer-name đã bị bỏ khỏi bộ TC); phát biểu trước đó (Layer name + Option title + type) đã bị QA đính chính 2026-08-25. Claim ở mức S0 (không nạp KB), chỉ ghi nhận làm unknown area. Người trả lời: Dev."}
```

## OQ-sdk-236 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-236","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"QA đề xuất (KB-538, CBS-155, 2026-11-10): cross-sell item không phải addon item, nên khi line chính bị xoá, line cross-sell còn lại không bị rule Teeinblue Required Addon Validation chặn; cross-sell line mang _parent_customization_id và _is_sub_item, không có _tib_customization_id. Dev xác nhận? Jira TIB-5715 không nói về cross-sell.","kb_ids":["KB-538"]}
```

## OQ-sdk-237 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-237","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"Vế accelerated checkout (Shop Pay, PayPal, Apple Pay, Google Pay) bị chặn khi cart có orphan addon chưa test được trên staging vì store dev chỉ có Bogus gateway (KB-541). Production đã verify vế này chưa? Người trả lời: QA hoặc PO.","kb_ids":["KB-541"]}
```

## OQ-sdk-238 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-238","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"Ngoài việc kích hoạt checkout rule Teeinblue Required Addon Validation ở Shopify Admin > Settings > Checkout > Checkout rules trên store đã deploy extension (KB-543), rule có điều kiện nào khác để chạy không (gói Shopify, loại checkout)? Nguồn Dev TIB-5715 không nêu. Người trả lời: Dev.","kb_ids":["KB-543"]}
```

## OQ-sdk-239 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-239","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"PO xác nhận ý định: rule chặn hoàn tất Checkout khi cart có addon item không còn line chính (KB-534), và khi rule Inactive thì đơn chỉ có addon line vẫn được đặt (KB-540)? Hai item chạm đơn hàng, nguồn là Dev và test case staging.","kb_ids":["KB-534","KB-540"]}
```

## OQ-sdk-240 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-240","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"QA đề xuất (KB-549, CBS-156, 2026-11-09): khi buyer xoá addon line mà line chính vẫn còn, autofixer thêm lại addon (cart/add.js) với quantity khớp line chính. Dev xác nhận? Jira TIB-5665 không nói về trường hợp này. Người trả lời: Dev.","kb_ids":["KB-549"]}
```

## OQ-sdk-241 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-241","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"QA ghi lời Dev do người dùng chuyển lại (KB-550, CBS-156, 2026-11-09): autofixer không ngăn buyer checkout ngay sau khi xoá line chính; vào checkout trước khi autofixer chạy (kể cả delay 0) thì checkout chỉ có addon line, việc chặn thuộc checkout rule Teeinblue Required Addon Validation (sdk/required-addon-validation KB-534). Dev hoặc PO xác nhận bằng nguyên văn? Người trả lời: Dev hoặc PO.","kb_ids":["KB-550"]}
```

## OQ-sdk-242 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-242","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"Race giữa add to cart có addon charge và request đọc cart của app khác chỉ được mô phỏng trên staging bằng Playwright route, vì store staging không có app chiếm nút add to cart (KB-551, ALTERNATIVE_SETUP). Cách mô phỏng có tương đương app thật (Foxkit Upsell & Bundles) không, và production đã verify với app thật chưa? Người trả lời: Dev hoặc QA.","kb_ids":["KB-551"]}
```

## OQ-sdk-243 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-243","type":"OPEN_ISSUE","feature_id":"required-addon-validation","summary":"Dev nêu trong QA plan TIB-5665 (#56269, 2026-11-03): nếu app thêm line chính bằng request không phải .js rồi redirect về /cart thì addon vẫn có thể bị autofixer xoá; đó là known open issue sdk #2181, không phải regression của TIB-5665 (KB-545). Issue đã được xử lý chưa? Người trả lời: Dev.","kb_ids":["KB-545"]}
```

## OQ-sdk-244 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-244","type":"NEEDS_CONFIRMATION","feature_id":"required-addon-validation","summary":"Sau khi autofixer sửa cart (đổi quantity hoặc xoá line chính trong cart drawer, KB-547), cart drawer có phải render lại không? QA quan sát (CBS-156, 2026-11-05 và 2026-11-09): callback mặc định chỉ reload khi đang ở trang /cart nên drawer không cập nhật; store có option autofixerCallback chỉ render lại cart-drawer và cart-icon-bubble thì trang /cart hiện số cũ. Đây là hành vi đúng hay lỗi? Người trả lời: Dev.","kb_ids":["KB-547"]}
```

## OQ-sdk-245 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-245","type":"NEEDS_CONFIRMATION","feature_id":"game-text-preview-render","summary":"Slot .1 của layer shape-text (cùng một layer hiện hai lần trên trang cùng lúc, vd sản phẩm addon hoặc cross-sell dùng chung artwork với sản phẩm chính) chưa kiểm trên storefront; Dev cho bỏ vế này khỏi test staging vì unit test U17 phủ (TIB-5666 #56619, KB-555). Cần setup staging để kiểm mỗi instance gửi slot riêng (.0 và .1), có preview riêng và không blank khi gõ không? Người trả lời: Dev hoặc QA.","kb_ids":["KB-555"]}
```

## OQ-sdk-246 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-246","type":"NEEDS_CONFIRMATION","feature_id":"game-text-preview-render","summary":"Rate limit của route games trên production là bao nhiêu (staging: 3 request/phút/IP theo Dev, KB-560)? Request preview bị SDK huỷ có tính vào limit không (QA suy luận là có)? Người trả lời: Dev.","kb_ids":["KB-560"]}
```

## OQ-sdk-247 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-247","type":"NEEDS_CONFIRMATION","feature_id":"game-text-preview-render","summary":"QA quan sát trên staging (CBS-159, 2026-11-06): khi request preview của layer shape-text, spiral, warp-text nhận 429, layer rỗng hẳn (không ảnh, không spinner) và form không báo lỗi. Theo định nghĩa của Dev (KB-553) đây là blank. Đây là hành vi đúng khi bị rate limit hay lỗi cần sửa? Người trả lời: Dev hoặc PO.","kb_ids":["KB-553","KB-560"]}
```

## OQ-sdk-248 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-248","type":"OPEN_ISSUE","feature_id":"game-text-preview-render","summary":"Lỗi mất từ cuối của layer shape-text cỡ lớn là bug có từ trước trong vectorize và có cả trên production trước bản sửa (TIB-5666 #56757, KB-556). Order đã lưu print file bị mất từ trước bản sửa cần regenerate design: order production bị ảnh hưởng có được rà và regenerate không, ai làm? Người trả lời: Dev hoặc PO.","kb_ids":["KB-556"]}
```

## OQ-sdk-258 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-258","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","kb_ids":["KB-573"],"check_ids":["CHK-127"],"owner":"Dev","summary":"[CBS-163] 6 route upload public trả đúng 3 key, không wrapper data, không user_id/instance_id/ip/geo_location/user_agent/master/thumbnail/effects, 201/200 (KB-573, quan sát staging không ghi build; production 2026-11-11 một lượt cho 4 route upload) — Dev xác nhận là expected?"}
```

## OQ-sdk-259 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-sdk-259","type":"NEEDS_CONFIRMATION","feature_id":"storefront-buyer-facing","kb_ids":["KB-575"],"check_ids":["CHK-129"],"owner":"Dev","summary":"[CBS-163] Upload không effect/crop/remove background/AI filter/vector/PDF hiện trên preview; cart line mang ảnh upload và property origin của field (KB-575, quan sát staging không ghi build; production một lượt smoke) — Dev xác nhận là expected?"}
```

## OQ-sdk-260 — OPEN_ISSUE

```json
{"oq_id":"OQ-sdk-260","type":"OPEN_ISSUE","feature_id":"storefront-buyer-facing","kb_ids":["KB-572","KB-574"],"check_ids":[],"owner":"Dev","summary":"[CBS-163] Theo Dev (comment 56448 Open questions), imageFilterStatus và các reply async 202 tới storefront vẫn gửi original, master, effects; Dev để cho một follow-up issue, ngoài contract của KB-572. Chưa có ticket follow-up và chưa có expected cho các reply này."}
```
