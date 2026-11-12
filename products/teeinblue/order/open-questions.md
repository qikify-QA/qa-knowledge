# Open Questions — Order

_Regenerated from `kb.json` (object-level + per-feature) and `checklists/*.json` at context version 1 (published 2026-09-13). This file does not itself resolve any entry — resolution requires the proper authority (orchestrator + reviewer for conflicts, PO/Dev for business questions)._

## Summary

| Type | Count |
|---|---|
| CONFLICT | 1 |
| NEEDS_CONFIRMATION | 26 |
| OPEN_ISSUE | 17 |

## OQ-order-001 — CONFLICT

```json
{"oq_id": "OQ-order-001", "type": "CONFLICT", "feature_id": "place-personalized-order-storefront", "summary": "An order completed successfully at storefront checkout (confirmation JTEL87JY0) never appeared in the portal Orders list (GET /api/orders?by_teeinblue=1), even after 90+ minutes, checked across all TIB statuses, both stores, and a 30-day date range. A second order placed afterward, following the user's claim that a webhook configuration issue had been fixed, DID sync successfully (portal #1002 / id 4322). This affects both place-personalized-order-storefront (the sync step) and review-and-initiate-fulfillment-portal (the entry precondition).", "side_a": "Storefront checkout completed successfully for order confirmation JTEL87JY0 (staging store TIB_STORE_URL_2, GUEST buyer), placed approximately 2026-09-13T07:08 UTC, total $63.99, single line item — the order exists as a real, completed Shopify order.", "side_b": "GET /api/orders?by_teeinblue=1 from the portal never returned this order — checked across all TIB statuses, both stores, a 30-day date range, and repeatedly over more than 90 minutes after placement. It only ever showed a different, later order (confirmation PE7AU1Y53 / portal #1002 / id 4322)."}
```

Root cause (claimed webhook configuration fix) has never been independently verified by dev/infra logs or backend records — the user's statement is recorded as an unverified claim, not a confirmed fact. Do not mark this resolved based on that claim alone.

## OQ-order-002 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-002", "type": "NEEDS_CONFIRMATION", "feature_id": "place-personalized-order-storefront", "summary": "What is the expected checkout behavior/error message for declined (test card '2') and gateway-failure (test card '3') payments? Is any partial/failed order record created on the portal side? Never observed — only the approved-card path was exercised."}
```

## OQ-order-003 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-003", "type": "NEEDS_CONFIRMATION", "feature_id": "place-personalized-order-storefront", "summary": "Is add-to-cart actually blocked when a required personalization field is empty, and if so what validation message is shown? Never observed — 'required' is only an inferred label from the field UI, not a tested behavior."}
```

## OQ-order-004 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-004", "type": "NEEDS_CONFIRMATION", "feature_id": "place-personalized-order-storefront", "summary": "What happens at exactly 10 characters and on attempting an 11th character in the max-10 personalization text fields (Woman Name, Cat Name #1/#2) — hard client-side block, server-side validation error, or silently unenforced? Only 9/10 and 8/10 counter states (below the boundary) were observed."}
```

## OQ-order-005 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-005", "type": "NEEDS_CONFIRMATION", "feature_id": "place-personalized-order-storefront", "summary": "Does completing checkout with Express shipping succeed, and what is the actual (evidence-backed) Express price and resulting total? The $15.00 price was only summarized from observation text, with no screenshot/dom snapshot confirming it, and the Express path was never completed end-to-end."}
```

## OQ-order-006 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-006", "type": "NEEDS_CONFIRMATION", "feature_id": "place-personalized-order-storefront", "summary": "Does the checkout flow behave identically for a signed-in buyer, or are there differences (e.g. saved addresses, different payment options, order attribution)? Only the unauthenticated GUEST path was ever exercised."}
```

## OQ-order-007 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-007", "type": "NEEDS_CONFIRMATION", "feature_id": "place-personalized-order-storefront", "summary": "Does the cart (including the personalized mockup reference) survive a page reload without data loss or corruption? Never tested — the cart was only observed once, immediately after add-to-cart."}
```

## OQ-order-008 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-008", "type": "NEEDS_CONFIRMATION", "feature_id": "place-personalized-order-storefront", "summary": "What is the true, evidence-backed request/response schema of the add-to-cart call (POST /cart/add), and does it ever return a non-200 status (e.g. sold-out variant, invalid personalization payload)? Current knowledge is INFERRED only, summarized from a browser tool narrative with no raw request/response body captured."}
```

## OQ-order-009 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-009", "type": "NEEDS_CONFIRMATION", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "Does any non-owner/restricted-permission portal role see the same orders list, order-details, and fulfill/status actions as the owner (sub=<explorer>)? Never tested — only the owner role was exercised against every capability of this feature."}
```

## OQ-order-010 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-010", "type": "NEEDS_CONFIRMATION", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "Do the DB-layer order/order-item records match the UI/API-displayed state exactly, including for fields never independently verified at raw-payload level (order-details header, tib_status cross-layer mapping)? Database observation was disabled for this bootstrap, so no DB-layer evidence exists at all."}
```

## OQ-order-011 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-011", "type": "NEEDS_CONFIRMATION", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "What do 'Edit customization' and 'View customization' actually do — do they affect the design, the order, or trigger downstream regeneration? Neither button was ever exercised."}
```

## OQ-order-012 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-012", "type": "NEEDS_CONFIRMATION", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "Does 'Confirm & Send to fulfill' fire a mutation and/or call the POD provider once a POD account (e.g. Printify) IS connected, and does it create a real fulfillment/purchase order? This is the single biggest safety gap for this feature — the only observed behavior (review dialog only, no mutation) is scoped strictly to a POD-disconnected instance, which is not the state a real merchant using this feature would be in. Must be answered by PO/Dev, or verified very carefully in a sandboxed POD account, before any automated or exploratory test attempts it."}
```

## OQ-order-013 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-013", "type": "OPEN_ISSUE", "feature_id": "place-personalized-order-storefront", "summary": "Exploration for this KB version ran against store TIB_STORE_URL_2, not the originally-intended store TIB_STORE_URL_1. store TIB_STORE_URL_1 is known (from a separate prior observation) to have an add-to-cart failure that never completes for the same campaign, so no order could be placed there with available evidence. Any future work targeting store TIB_STORE_URL_1 specifically must treat this object's storefront findings as unverified there and should first re-investigate that store's add-to-cart issue."}
```

## OQ-order-014 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-014", "type": "OPEN_ISSUE", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "The full tib_status enum and its integer<->label mapping is unknown. Only one value pair has ever been observed (UI label 'ready' <-> API integer 6) for one order. Do not build validation or transition tests assuming a known, exhaustive enum."}
```

## OQ-order-015 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-015", "type": "OPEN_ISSUE", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "The true raw payload of GET /api/orders (order-details) and the GraphQL orders_by_pk query for an order have never been captured — current knowledge of their field shapes (order header, tib_status) is UI/name-only, not payload-verified. Schema-level assertions should not be built on this yet."}
```

## OQ-order-016 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-016", "type": "OPEN_ISSUE", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "'Change status' dropdown transitions (Ready/Sent/Fulfilled/Paused/Canceled) have only ever been seen as a displayed option list — no transition was ever executed, so the target endpoint, side effects (notifications, POD calls), and reversibility of any transition are completely unknown."}
```

## OQ-order-017 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-017", "type": "OPEN_ISSUE", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "The 'Bulk Fulfill' sidebar flyout item exists but has never been opened or explored. Its behavior is completely unknown and must not be inferred from the single-order 'Confirm & Send to fulfill' flow — it may operate at a different (higher-risk, multi-order) scope."}
```

## OQ-order-018 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-018", "type": "OPEN_ISSUE", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "Print file của layout emboss / shape-cut khi artwork có Group ẩn chưa verify: TC-TIB-6071 Blocked (Product Base 3385 không có cell layout emboss), TC-TIB-6070 (shape cut) actualResult rỗng. Cần chạy lại với Product Base có layout emboss/shape-cut.", "kb_ids": ["KB-183"]}
```

## OQ-order-019 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-019", "type": "OPEN_ISSUE", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "Rule print file PNG/PDF theo Group ẩn (TC-TIB-6068/6069) có giữ nguyên trên build staging sau khi toàn bộ 6 PR của TIB-5584 merge, và trên production khi TIB-5584 release không?", "kb_ids": ["KB-182"]}
```

## OQ-order-020 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-020", "type": "NEEDS_CONFIRMATION", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "Print file PNG/PDF của order bỏ nội dung của Group ẩn (và các layer con) — đây là thay đổi đầu ra fulfillment. PO xác nhận đây là hành vi đúng cho merchant/nhà in (kể cả order đã đặt trước khi TIB-5584 release) để check P1 về print file giữ oracle hiện tại? Đồng thời xác nhận layout emboss/shape-cut có phải theo cùng quy tắc (KB-183 mới là quan sát, chưa verify).", "kb_ids": ["KB-182", "KB-183"]}
```

## OQ-order-021 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-021", "type": "OPEN_ISSUE", "feature_id": "place-personalized-order-storefront", "summary": "Hành vi 'layer bị Hide không chặn Add to cart và giá trị đã nhập không vào cart/order/print file' có giữ nguyên trên build staging sau khi 6 PR của TIB-5558 merge (2026-10-29) và trên production khi TIB-5558 release không?", "kb_ids": ["KB-238"]}
```

## OQ-order-022 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-022", "type": "OPEN_ISSUE", "feature_id": "place-personalized-order-storefront", "summary": "Layer Hide Required kiểu khác text (image, clipart, …) hoặc nhiều layer Hide cùng bị ẩn có cùng hành vi không chặn Add to cart và không vào cart/order không? KB-238 chỉ kiểm một layer text Required với một điều kiện.", "kb_ids": ["KB-238"]}
```

## OQ-order-023 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-023", "type": "OPEN_ISSUE", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "Print file / preview / mockup của order theo điều kiện Hide có giữ nguyên trên build staging sau khi 6 PR của TIB-5558 merge (2026-10-29) và trên production khi TIB-5558 release không; BUG-430 (print file order rỗng ở lượt đầu) đã được fix trên build nào?", "kb_ids": ["KB-239"]}
```

## OQ-order-024 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-024", "type": "OPEN_ISSUE", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "Print file PDF và layout emboss / shape-cut có loại bỏ layer bị Hide như print file PNG layout thường không? KB-239 chỉ kiểm PNG layout thường.", "kb_ids": ["KB-239"]}
```

## OQ-order-025 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-025", "type": "NEEDS_CONFIRMATION", "feature_id": "place-personalized-order-storefront", "summary": "PO xác nhận đây là hành vi đúng cho merchant: layer action Hide có field Required đang bị ẩn không chặn Add to cart, và giá trị buyer đã nhập trước khi layer bị ẩn không vào cart, order và print file (bị bỏ đi, không lưu lại)? KB-238 đến từ test case PASS, chưa có PO/business xác nhận ý định.", "kb_ids": ["KB-238"]}
```

## OQ-order-026 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-026", "type": "NEEDS_CONFIRMATION", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "PO xác nhận đây là hành vi đúng cho merchant và nhà in: preview customization, mockup và print file của order áp điều kiện Hide giống storefront (item khớp điều kiện Hide không có layer đó trong print file)? KB-239 đến từ test case PASS, chưa có PO/business xác nhận ý định.", "kb_ids": ["KB-239"]}
```

## OQ-order-027 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-order-027","type":"NEEDS_CONFIRMATION","feature_id":"place-personalized-order-storefront","summary":"PO/Dev xác nhận: chuỗi Add to cart → checkout → order trên portal → file design có giá trị layer + Global Option mới chỉ quan sát 1 lượt (TC-TIB-7405) trên build trước redeploy (ảnh hưởng order/fulfillment). Chạy lại trên build đã merge TIB-5203 và production.","kb_ids":["KB-369"]}
```

## OQ-order-028 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-order-028","type":"NEEDS_CONFIRMATION","feature_id":"review-and-initiate-fulfillment-portal","summary":"Dev/PO: toast 'put your design in queue' khi Regenerate và việc Item Activity logs không ghi dòng 'is generating' cho lần regenerate chỉ có ở actualResult của TC-TIB-7630 — có phải hành vi mong đợi không? Tương tự cho việc order vẫn ở trạng thái Ready sau Regenerate (chỉ ở actualResult TC-TIB-7630). Không dùng để diễn giải lại chuỗi sự kiện Item Activity logs hiện có. Bổ sung CBS-138 (2026-11-11): spec-hub rule design-generation-ready (S2, KB-782) nêu item active/personalized thành Ready khi design file lưu xong, và item đã fulfilled được re-generate vẫn fulfilled; phần CCR trích không nói item đang Ready ở trạng thái nào sau re-generate, nên câu hỏi về trạng thái sau Regenerate vẫn mở. Xem OQ-order-085.","kb_ids":["KB-393","KB-782"]}
```

## OQ-order-029 — OPEN_ISSUE

```json
{"oq_id":"OQ-order-029","type":"OPEN_ISSUE","feature_id":"review-and-initiate-fulfillment-portal","summary":"Chạy lại sau merge và trên production: Regenerate design của order item có artwork Group nhiều layer chỉ được chạy 2026-10-29 trên staging, trước khi PR thứ hai của TIB-5633 cập nhật lần cuối; ngày deploy production chưa rõ.","kb_ids":["KB-392","KB-393"]}
```

## OQ-order-030 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-order-030","type":"NEEDS_CONFIRMATION","feature_id":"review-and-initiate-fulfillment-portal","summary":"PO xác nhận đây là hành vi đúng cho merchant và nhà in: Regenerate design của order item có artwork Group nhiều layer tạo xong design mới và không kẹt generating? KB-392 đến từ test case PASS, chưa có PO/business xác nhận ý định.","kb_ids":["KB-392"]}
```

## OQ-order-031 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-031", "type": "NEEDS_CONFIRMATION", "feature_id": "edit-customization-after-order", "summary": "Trên /cart có đường sửa design không, theo SDK, loại campaign và toggle nào? 'Edit design' ở cart (SDK) và link Edit Customization sau order có phải cùng một feature không? KB-435 và KB-436 không phát biểu về /cart, không dùng làm expected cho /cart. Liên quan OQ-sdk-012.", "side_a": "Không có: ghi chú đề 2026-10-29 (tib-product-behaviors dòng 33); TC-TIB-7191 skipped (không có link hay property edit ở dòng parent); sdk KB-009 (OBSERVED_CURRENT, SDK v2, không tìm thấy đường edit từ cart).", "side_b": "Có: sdk KB-058 và translation KB-029 (modal 'Edit design' ở cart, SDK v1), sdk KB-057; flow storefront-sdk ghi Edit link trong cart của campaign product base.", "kb_ids": ["KB-435", "KB-436"]}
```

## OQ-order-032 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-032", "type": "NEEDS_CONFIRMATION", "feature_id": "edit-customization-after-order", "summary": "Ở Order status page, campaign by product base có hiện link Edit Customization và báo không hỗ trợ edit giống Thank You page không? TC-TIB-982 chỉ chạy ở Thank You page; CHK-004 chờ câu trả lời này.", "kb_ids": ["KB-436"]}
```

## OQ-order-033 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-033", "type": "NEEDS_CONFIRMATION", "feature_id": "edit-customization-after-order", "summary": "Sau khi customizer mở, buyer lưu thay đổi thì có ghi đè artwork của order không, và order item có nhận design mới không? TC-TIB-978 và TC-TIB-981 dừng ở mức design editable, TC-TIB-980 skipped. Ghi chú task Testlane TIB-042 nói artwork bị ghi đè; flow storefront-sdk chỉ ghi nút Update cart cập nhật customization.", "kb_ids": ["KB-435"]}
```

## OQ-order-034 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-034", "type": "NEEDS_CONFIRMATION", "feature_id": "edit-customization-after-order", "summary": "Edit Customization có bị chặn theo fulfillment status không? Ghi chú task Testlane TIB-042 nêu đây là câu hỏi mở với PO/Dev và là rủi ro production, vì artwork bị ghi đè.", "kb_ids": ["KB-435"]}
```

## OQ-order-035 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-035", "type": "NEEDS_CONFIRMATION", "feature_id": "edit-customization-after-order", "summary": "Classic customer accounts và New customer accounts có cùng nằm trong phạm vi của Edit Customization ở Order status page không? TC-TIB-981 không nói lượt chạy thuộc loại nào; flow storefront-sdk có ghi nhận link ở customer account mới, chưa có ghi nhận cho classic.", "kb_ids": ["KB-435", "KB-436"]}
```

## OQ-order-036 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-036", "type": "NEEDS_CONFIRMATION", "feature_id": "edit-customization-after-order", "summary": "Order đặt trước khi bản này deploy có còn dùng được Edit Customization không? Ghi chú task Testlane TIB-042 còn để mở; ngày deploy cũng chưa rõ.", "kb_ids": ["KB-435", "KB-436"]}
```

## OQ-order-037 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-037", "type": "OPEN_ISSUE", "feature_id": "edit-customization-after-order", "summary": "Phạm vi surface của Edit Customization chưa chốt: KB-435 và KB-436 chỉ nói về Thank You page và Order status page, không khẳng định không có ở nơi khác. Nút cùng tên ở Portal vẫn thuộc OQ-order-011.", "kb_ids": ["KB-435", "KB-436"]}
```

## OQ-order-038 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-038", "type": "OPEN_ISSUE", "feature_id": "edit-customization-after-order", "summary": "Điều kiện để block Edit Customization render chưa rõ: do cấu hình block hay do loại store. Test case ghi block phải được thêm vào trang; flow storefront-sdk ghi store theo <TIB_STORE_URL> không render block, còn <TIB_SDK_V2> có link. Nhãn link cũng khác nhau giữa hai trang ('Customize', 'Customization edit link'), nên chưa dùng nhãn làm expected.", "kb_ids": ["KB-435", "KB-436"]}
```

## OQ-order-039 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-039", "type": "NEEDS_CONFIRMATION", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "Người có thẩm quyền xác nhận hai phía của KB-437: staging có đúng là không test được tracking từ provider không (nguồn chỉ là ghi chú đề 2026-10-29, TC-TIB-7771 skipped cùng lý do, chưa có lời xác nhận gốc), và trên production tracking từ provider hoạt động thế nào (KB-437 ghi 'không rõ'; ngày deploy của ticket ngữ cảnh TIB-5439 cũng chưa rõ). CHK-P27 chờ câu trả lời này.", "kb_ids": ["KB-437"]}
```

## OQ-order-040 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-040", "type": "NEEDS_CONFIRMATION", "feature_id": "edit-customization-after-order", "summary": "PO xác nhận đây là hành vi đúng: sau order, buyer của campaign Shopify product mở được customizer với design editable ở Thank You page và Order status page? KB-435 là đề xuất chưa xác minh: chỉ có test case PASS không ghi build và một dòng ghi chú, chưa có lời xác nhận gốc; đường này có thể đổi design của order đã đặt. CHK-001, CHK-002 chờ câu trả lời này.", "kb_ids": ["KB-435"]}
```

## OQ-order-041 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-041", "type": "OPEN_ISSUE", "feature_id": "edit-customization-after-order", "summary": "Chạy lại trên build hiện hành và trên production: TC-TIB-978, TC-TIB-981, TC-TIB-982 chạy 2026-08-27, không ghi build; ngày deploy chưa rõ. URL customize của staging đã đổi sau lượt chạy (flow storefront-sdk), nên chưa có lượt nào xác nhận design editable trên URL hiện hành; hành vi production của KB-435 và KB-436 chưa có lượt chạy.", "kb_ids": ["KB-435", "KB-436"]}
```

## OQ-order-042 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-042", "type": "OPEN_ISSUE", "feature_id": "edit-customization-after-order", "summary": "Message 'Your design does not support edit for now, contact shop owner' của KB-436 có đổi theo locale của buyer không? Knowledge translation chưa có item về customize page.", "kb_ids": ["KB-436"]}
```

## OQ-order-043 — OPEN_ISSUE

```json
{"oq_id": "OQ-order-043", "type": "OPEN_ISSUE", "feature_id": "edit-customization-after-order", "summary": "Việc đổi host customize khi test trên staging có ở bảng bẫy của guide nhưng chưa có KB item environment_difference, nên profile feature này chưa có dòng environment_differences. Cần CCR riêng nếu muốn ghi nhận.", "kb_ids": ["KB-435", "KB-436"]}
```

## OQ-order-044 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-044", "type": "NEEDS_CONFIRMATION", "feature_id": "edit-customization-after-order", "summary": "Với campaign by product base, hành vi đúng là gì? Hai nguồn chưa được chốt bằng lời xác nhận gốc. KB-436 ghi theo phía test case. CHK-003 chờ câu trả lời này.", "side_a": "Không có link: ghi chú đề 2026-10-29 (tib-product-behaviors dòng 33) ghi 'không có cho product base'; TC-TIB-7191 skipped ghi cùng ý.", "side_b": "Link vẫn hiện, click thì báo không hỗ trợ edit: TC-TIB-982 PASS 2026-08-27 không ghi build; ghi chú đề 2026-11-05 và mục #144 của ghi chú audit ghi theo phía này.", "kb_ids": ["KB-436"]}
```

## OQ-order-045 — OPEN_ISSUE

```json
{"oq_id":"OQ-order-045","type":"OPEN_ISSUE","feature_id":"shopify-order-import","summary":"Hành vi chưa ship (TIB-5563 còn ở QA Review): KB-760 là đề xuất theo câu trả lời của Dev 2026-10-26, chưa có test case PASS sau fix. Cần chạy lại trên build có fix và sau release production: customization_id chỉ dùng để tìm customization khi đúng UUID 8-4-4-4-12 (không trim; khoảng trắng, {…}, 32 hex không gạch, UUID nằm trong chuỗi dài hơn là sai định dạng), cả _customization_id và customization_id. Nhánh id số (hasCustomizationId) chỉ được nói là giữ nguyên, chưa có mô tả hành vi. CHK-001, CHK-002 chờ câu trả lời này.","kb_ids":["KB-760"]}
```

## OQ-order-046 — OPEN_ISSUE

```json
{"oq_id":"OQ-order-046","type":"OPEN_ISSUE","feature_id":"shopify-order-import","summary":"Hành vi chưa ship và có quan sát trái chiều: theo Dev (2026-10-26), đơn có line customization_id sai định dạng vẫn được import, line đó như item không có design và không tạo usage (KB-761). Lượt QA trên staging 2026-10-28 (QA-3430) thấy ngược lại: đơn có line sai định dạng không vào Teeinblue sau 33–38 phút, đơn đối chứng vào trong dưới 4 phút; bug chưa được file. Cần lượt chạy trên build có fix, và PO xác nhận ý định (mất đơn, usage/billing). Hành vi trên build hiện tại (trước fix) cũng chưa được ghi lại. Liên quan OQ-order-001, không đóng mục đó. CHK-003, CHK-004, CHK-005 chờ câu trả lời này.","kb_ids":["KB-761","KB-011","KB-017"]}
```

## OQ-order-047 — OPEN_ISSUE

```json
{"oq_id":"OQ-order-047","type":"OPEN_ISSUE","feature_id":"shopify-order-import","summary":"Hành vi chưa ship (TIB-5563): khôi phục customization qua cart token chạy theo đơn, chỉ khi không line nào có id số/UUID hợp lệ, và line có property không bao giờ được khôi phục (KB-762). Chưa quan sát. CHK-006 chờ câu trả lời này. Bổ sung CBS-138 (2026-11-11): spec-hub rule order-sync-match-personalization (S2, KB-783, mô tả code hiện tại) nêu nhánh cart chỉ chạy khi không item nào trong order có id, khớp cùng cart + cùng variant trong một tháng dương lịch, mỗi personalization một item; cùng chiều 'chạy theo đơn' của KB-762, nhưng không nói id thế nào là hợp lệ và không phải nguồn của bản fix TIB-5563. Câu hỏi vẫn mở. Xem OQ-order-086.","kb_ids":["KB-762","KB-783"]}
```

## OQ-order-048 — OPEN_ISSUE

```json
{"oq_id":"OQ-order-048","type":"OPEN_ISSUE","feature_id":"shopify-order-import","summary":"Hành vi chưa ship (TIB-5563): re-sync (SyncShopifyOrder / admin Order Sync) và command FixMissingCustomization đi cùng lookup đơn Shopify; Etsy và nền tảng khác không bị ảnh hưởng; _tib_customization_id đọc bằng method riêng (KB-763). Chưa chạy re-sync, FixMissingCustomization; chưa có mô tả cách xử lý _tib_customization_id; \"Etsy không ảnh hưởng\" chưa kiểm. CHK-007, CHK-008 chờ câu trả lời này.","kb_ids":["KB-763"]}
```

## OQ-order-049 — OPEN_ISSUE

```json
{"oq_id":"OQ-order-049","type":"OPEN_ISSUE","feature_id":"shopify-order-import","summary":"Theo Dev (2026-10-26), đơn đã lỗi SQLSTATE 22P02 trước bản fix sẽ không được import lại (KB-765). Hành vi chưa ship; PO cần xác nhận việc không khôi phục đơn lịch sử là chủ ý, và có đường nào (re-sync, FixMissingCustomization) đưa được các đơn đó vào không. CHK-009 chờ câu trả lời này.","kb_ids":["KB-765"]}
```

## OQ-order-050 — OPEN_ISSUE

```json
{"oq_id":"OQ-order-050","type":"OPEN_ISSUE","feature_id":"review-and-initiate-fulfillment-portal","summary":"Hành vi chưa ship theo quyết định operator cho mọi claim TIB-5563: Order details / Edit order hiện nguyên giá trị _customization_id / customization_id trong danh sách \"Options\" của item, chỉ khi store bật \"show line item properties\", ẩn sau \"Show more\", giá trị được HTML-escape (KB-764). Chưa quan sát (lượt staging 2026-10-28 bị chặn). Chưa rõ \"Options\" hiện gì khi tắt setting hoặc trên build trước fix. PO xác nhận ý định HTML-escape. CHK-P28, CHK-P29, CHK-P30 chờ câu trả lời này.","kb_ids":["KB-764","KB-017"]}
```

## OQ-order-051 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-order-051","type":"NEEDS_CONFIRMATION","feature_id":"place-personalized-order-storefront","summary":"KB-766 là một lượt chạy staging 2026-10-27, không ghi build, không có căn cứ expected: order design dùng ảnh AI đã generate và fit vào box layer (T2I GPT Default phủ đúng box; MU GPT 2K phủ hết chiều rộng, contain, không crop). Cần PO/Dev xác nhận cách fit đúng (contain hay cover), có áp cho mọi model và tỉ lệ box khác không, và hành vi trên production. CHK-023-ORDER01, CHK-024-ORDER01 chờ câu trả lời này.","kb_ids":["KB-766"]}
```

## OQ-order-052 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-order-052","type":"NEEDS_CONFIRMATION","feature_id":"order-design-vector-render","summary":"KB-767 là một lượt chạy staging 2026-10-08, không ghi build, không có căn cứ expected: order design PNG (Re-generate) của vector layer đã đổi màu có clipPath id trùng tô kín mọi vector, bố cục giống preview, khi mọi layer cùng một màu. Cần xác nhận đây là hành vi đúng; trạng thái deploy của TIB-5350 (hỗ trợ clipPath khi chuyển SVG sang ảnh) chưa rõ, câu trả lời của Dev trên TIB-5501 chỉ trỏ sang TIB-5350. Chưa kiểm khi mỗi layer giữ màu riêng, định dạng PDF và production. Fixture khác với artwork KB-418 nên chưa coi là conflict. CHK-001, CHK-003, CHK-004 chờ câu trả lời này.","kb_ids":["KB-767"]}
```

## OQ-order-053 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-order-053","type":"NEEDS_CONFIRMATION","feature_id":"order-design-vector-render","summary":"KB-768 là một lượt chạy staging (file render 2026-10-07), không ghi build: order design SVG gộp mọi layer có id duy nhất, đều mang prefix svg-…-, không tham chiếu treo, màu đúng, khi mọi layer cùng một màu. Căn cứ expected chỉ là lời tóm tắt của Dev trên TIB-5501, không trích nguyên văn. Cần Dev xác nhận, và lượt chạy khi mỗi layer giữ màu riêng. CHK-002 chờ câu trả lời này.","kb_ids":["KB-768"]}
```

```json
{"oq_id":"OQ-order-054","type":"NEEDS_CONFIRMATION","feature_id":"order-design-vector-render","summary":"Cần xác định KB đích cho các reference của order-design-vector-render: KB-418. Chưa có đích duy nhất; các ref được tách khỏi liên kết đang hoạt động, không dùng chúng làm căn cứ kết luận."}
```

```json
{"oq_id":"OQ-order-055","type":"NEEDS_CONFIRMATION","feature_id":"place-personalized-order-storefront","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-006-ORDER01-SYNC “Order appears in portal Orders list within a reasonable time after storefront checkout completes (known-flaky area, OQ-order-001)” của feature place-personalized-order-storefront. current_behavior_only"}
```

```json
{"oq_id":"OQ-order-056","type":"NEEDS_CONFIRMATION","feature_id":"place-personalized-order-storefront","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-011-ORDER01 “Checkout behavior with a non-approved Test Payment Gateway card (declined '2' or gateway-failure '3')” của feature place-personalized-order-storefront. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-order-057","type":"NEEDS_CONFIRMATION","feature_id":"place-personalized-order-storefront","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-012-ORDER01 “Add-to-cart / checkout attempt with one or more required personalization fields left empty” của feature place-personalized-order-storefront. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-order-058","type":"NEEDS_CONFIRMATION","feature_id":"place-personalized-order-storefront","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-013-ORDER01 “Personalization text field behavior at the stated 10-character max length boundary” của feature place-personalized-order-storefront. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-order-059","type":"NEEDS_CONFIRMATION","feature_id":"place-personalized-order-storefront","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-014-ORDER01 “Complete checkout end-to-end using the Express shipping option” của feature place-personalized-order-storefront. insufficient_authority"}
```

```json
{"oq_id":"OQ-order-060","type":"NEEDS_CONFIRMATION","feature_id":"place-personalized-order-storefront","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-015-ORDER01 “Signed-in buyer can complete the same personalized checkout flow” của feature place-personalized-order-storefront. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-order-061","type":"NEEDS_CONFIRMATION","feature_id":"place-personalized-order-storefront","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-016-ORDER01 “Cart contents and mockup persist correctly after a page reload” của feature place-personalized-order-storefront. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-order-062","type":"NEEDS_CONFIRMATION","feature_id":"place-personalized-order-storefront","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-017-ORDER01 “POST /cart/add request/response contract for a personalized add-to-cart” của feature place-personalized-order-storefront. insufficient_authority"}
```

```json
{"oq_id":"OQ-order-063","type":"NEEDS_CONFIRMATION","feature_id":"review-and-initiate-fulfillment-portal","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-P12-SYNC-VISIBILITY “Merchant-facing signal (or lack thereof) when an order fails to sync from storefront checkout into the portal” của feature review-and-initiate-fulfillment-portal. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-order-064","type":"NEEDS_CONFIRMATION","feature_id":"review-and-initiate-fulfillment-portal","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-P13-PERMISSION “Non-owner / restricted-permission portal role access to orders list, order-details, fulfill action, and change-status dropdown” của feature review-and-initiate-fulfillment-portal. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-order-065","type":"NEEDS_CONFIRMATION","feature_id":"review-and-initiate-fulfillment-portal","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-P14-DB-CROSSCHECK “Order/order-item database rows match what the portal UI and API display” của feature review-and-initiate-fulfillment-portal. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-order-066","type":"NEEDS_CONFIRMATION","feature_id":"review-and-initiate-fulfillment-portal","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-P15-CUSTOMIZATION-EDIT “'Edit customization' / 'View customization' effect on the design/order state” của feature review-and-initiate-fulfillment-portal. missing_or_unresolved_oracle"}
```

```json
{"oq_id":"OQ-order-067","type":"NEEDS_CONFIRMATION","feature_id":"review-and-initiate-fulfillment-portal","summary":"Cần xác nhận expected behavior và nguồn cho check CHK-P16-FULFILL-POD-CONNECTED “'Confirm & Send to fulfill' behavior when a POD account (e.g. Printify) IS connected” của feature review-and-initiate-fulfillment-portal. missing_or_unresolved_oracle"}
```

```json
{"oq_id": "OQ-order-068", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "PO/dev Myze có chấp nhận payload gửi recipient.country dạng full name và không gửi recipient.state không? Hiện chỉ QA chấp nhận lệch so với expected gốc (ISO + state), không có xác nhận PO/Dev. Người trả lời: PO."}
```

```json
{"oq_id": "OQ-order-069", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "Payload gửi Myze có thật sự gửi phone/supplement là null khi vắng, và Myze có bỏ qua không validate không? Không có nguồn, và QA-3348 TC-12 không ghi giá trị null cụ thể. Người trả lời: Dev."}
```

```json
{"oq_id": "OQ-order-070", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "shippingAddress của Shopify order có phải chỉ null khi là đơn pickup (null cả object, không có trạng thái rỗng từng phần) không? Chưa có test case hay tài liệu Shopify chứng minh. Người trả lời: Dev."}
```

```json
{"oq_id": "OQ-order-071", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "billingAddress của Shopify order có bao giờ null hoặc rỗng không, tức ca \"cả shipping lẫn billing đều rỗng\" có tồn tại không? Không có test case kiểm điều này. Người trả lời: Dev."}
```

```json
{"oq_id": "OQ-order-072", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "Việc combine đơn pickup với đơn ship cùng địa chỉ hiệu dụng được xử lý thế nào: quyết định won't-fix có được PO/Dev duyệt không, và trạng thái ship ra sao? Hiện chỉ là quyết định của QA, TIB-5400 không tra được trên Jira. Người trả lời: PO."}
```

```json
{"oq_id": "OQ-order-073", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "Text buyer nhập có phải chỉ được gửi nguyên văn cho provider khi layer text bật \"Attach customer input for fulfillment\", và quy tắc đó có áp dụng cho mọi provider dùng flow này không? Nguồn là ghi chú QA về thread Slack của Dev, không có quote, QA-3365 TC-39 bị skip. Người trả lời: Dev."}
```

```json
{"oq_id": "OQ-order-074", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "Khi Create Order gửi provider thất bại, TIB có tự động retry không, hay chỉ staff resend thủ công, và điều này có giống nhau cho mọi provider không? Nguồn là ghi chú QA về thread Slack, không có quote, QA-3365 TC-19 bị skip. Người trả lời: Dev."}
```

```json
{"oq_id": "OQ-order-075", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "TIB có lưu header outbound (Authorization) của request gửi provider không, hay chỉ lưu body request? Bảng lưu phần request chưa được xác nhận lại, và QA-3365 TC-27 chỉ kiểm việc không lộ raw API key. Người trả lời: Dev."}
```

```json
{"oq_id": "OQ-order-076", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "KB-773: response PosterFlow được lưu ở fulfillers.metadata (id, status, reference_order_id) và fulfillers.fulfillment_linked_id được set — đây có phải vị trí lưu đúng theo thiết kế không? Portal hiển thị gì cho đơn gửi provider API: có phải chỉ fulfillment_linked_id và thông tin tracking không? Expected của QA-3365 TC-15 ghi \"dev confirmed\" nhưng không có tên hay quote, và TC không mở màn Portal. Người trả lời: Dev.", "kb_ids": ["KB-773"]}
```

```json
{"oq_id": "OQ-order-077", "type": "CONFLICT", "feature_id": "fulfillment-provider-request", "summary": "KB-775: payload Create Order gửi PosterFlow có chủ ý bỏ key id và thêm shipping_address.state: null không, và shape nào là chuẩn? Người trả lời: Dev.", "side_a": "Ví dụ request của dev trong Jira TIB-4778 comment 51328 (2026-09-18, ví dụ, không phải sign-off): payload có key id và shipping_address không có state.", "side_b": "Quan sát payload thật gửi PosterFlow từ 2026-10-05 (QA-3365 BUG-05, re-check 2026-10-06): 4/4 order không có id trong request_data, 3/4 có shipping_address.state: null (KB-775).", "kb_ids": ["KB-775"]}
```

```json
{"oq_id": "OQ-order-078", "type": "CONFLICT", "feature_id": "fulfillment-provider-request", "summary": "shipping_address trong payload gửi PosterFlow có field state hay không (và có dùng province/province_code thay cho state không)? Người trả lời: Dev.", "side_a": "Ghi chú QA FACT-084 về thread Slack của Dev (2026-09-16, không có quote): shipping_address gửi PosterFlow không có field state, dùng province/province_code.", "side_b": "Payload thật gửi PosterFlow từ 2026-10-05 có shipping_address.state: null (QA-3365 BUG-05, QA đóng 2026-10-07; QA-3365 TC-12 fail rồi chuyển skip)."}
```

```json
{"oq_id": "OQ-order-079", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "TIB có stub hay sandbox nào để ép PosterFlow trả 4xx/5xx không, và khi PosterFlow trả lỗi thì TIB xử lý status/message thế nào? Nguồn là ghi chú QA về thread Slack, không có quote, QA-3365 TC-17 không kiểm điều này. Người trả lời: Dev."}
```

```json
{"oq_id": "OQ-order-080", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "KB-776, KB-777: với order_combine_by khác 1, các line item cùng provider được gửi thế nào (một request cho mỗi line item?), và việc tách theo provider có luôn xảy ra ở mọi giá trị order_combine_by không? QA-3365 TC-33 chỉ chạy với giá trị 1; expected của TC-34 ghi \"Dev-confirmed 2026-09-22 (RQ6)\" không có tên hay quote. Người trả lời: Dev. Bổ sung CBS-138 (2026-11-11): spec-hub rule bulk-fulfill-grouping (S2, KB-784) nêu Confirm & Send gom item theo print provider rồi theo order, hoặc theo shipping address khi store gộp đơn theo shipping address; mỗi nhóm một provider order. Rule cùng chiều việc tách theo provider nhưng không nêu tên hay giá trị của setting gộp đơn, nên không trả lời câu hỏi về order_combine_by khác 1. Tên setting: OQ-order-087.", "kb_ids": ["KB-776", "KB-777", "KB-784"]}
```

```json
{"oq_id": "OQ-order-081", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "KB-778: shipment_notification_url có luôn do TIB tự sinh cho từng request (không phải input staff/merchant cấu hình) không, áp dụng cho provider nào ngoài PosterFlow, và webhook này có tự cập nhật tracking cho đơn không? QA-3365 TC-31 kết luận \"N/A theo điều kiện\" nhưng tick PASS, TC-21 (webhook cập nhật tracking) bị skip. Người trả lời: Dev.", "kb_ids": ["KB-778"]}
```

```json
{"oq_id": "OQ-order-082", "type": "NEEDS_CONFIRMATION", "feature_id": "edit-customization-after-order", "summary": "KB-779: QA (không phải PO/Dev) xác nhận khi chạy QA-3353 TC-76 rằng Re-generate design với mặc định \"No, keep current artwork version\" trên order đã đặt dựng lại bản render byte-identical, không áp populate config (Value/formula/GO/màu) đổi sau khi đặt. Dev/PO xác nhận: đây có phải hành vi mong muốn không (customization đóng băng lúc đặt hàng, Re-generate chỉ re-apply format/layout), và có áp cho mọi populate format không? Liên quan OQ-order-011 (không đóng OQ đó). Người trả lời: Dev/PO. Bổ sung CBS-138 (2026-11-11): spec-hub rule design-generation-artwork-version và artwork-versions-orders-keep-version (S2, KB-781, đọc từ code, chưa người review) nêu design của order render từ artwork version shopper đã personalize, sửa/restore artwork sau khi đặt không đổi design, trừ khi merchant chọn upgrade. Cùng chiều KB-779, chưa phải xác nhận của Dev/PO; câu hỏi vẫn mở.", "kb_ids": ["KB-779", "KB-781"]}
```

```json
{"oq_id": "OQ-order-083", "type": "NEEDS_CONFIRMATION", "feature_id": "edit-customization-after-order", "summary": "KB-780: QA (không phải PO/Dev) xác nhận khi chạy QA-3386 TC-41 rằng mở Edit customization ở portal, không sửa field nào rồi Save thì design của order đã đặt không đổi (hash giữ nguyên) dù artwork vừa bật override và upload mask mới. Dev/PO xác nhận: đây có phải hành vi mong muốn không, và sửa field thật trong Edit customization rồi Save có đưa cấu hình artwork mới (vd mask override) vào design không? Liên quan OQ-order-011 (không đóng OQ đó). Người trả lời: Dev/PO.", "kb_ids": ["KB-780"]}
```

```json
{"oq_id": "OQ-order-084", "type": "NEEDS_CONFIRMATION", "feature_id": "edit-customization-after-order", "summary": "Re-generate với radio \"Yes. Upgrade latest artwork version.\" có thật sự đưa thay đổi artwork (vd mask override mới) vào order đã đặt không? Chưa có TC nào chạy nhánh này và PASS (liên quan OQ-order-011). Người trả lời: Dev. Bổ sung CBS-138 (2026-11-11): spec-hub rule design-generation-artwork-version (KB-781) chỉ nói merchant có thể chọn upgrade khi re-generate, không nói nhánh upgrade đưa những thay đổi nào vào bản render; câu hỏi vẫn mở."}
```

## OQ-order-085 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-085", "type": "NEEDS_CONFIRMATION", "feature_id": "review-and-initiate-fulfillment-portal", "summary": "Theo spec-hub (rule design-generation-ready; S2, KB-782), khi design file được lưu, item active hoặc personalized thành ready to fulfill khi mọi design đã xong, và item đã fulfilled trong Shopify được re-generate design vẫn fulfilled, không lùi về Ready. Dev xác nhận hành vi này; điều kiện đúng là 'active or personalized' hay 'generating or personalized' (spec-hub có rule bulk-fulfill-statuses ghi khác, không có trong CCR, không nạp); item đang Ready, Sent hoặc Paused sau re-generate ở trạng thái nào? Liên quan OQ-order-028. Người trả lời: Dev.", "kb_ids": ["KB-782"]}
```

## OQ-order-086 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-086", "type": "NEEDS_CONFIRMATION", "feature_id": "shopify-order-import", "summary": "Theo spec-hub (rule order-sync-match-personalization; S2, KB-783), Teeinblue tìm personalization theo id trên item; chỉ khi không item nào trong order có id, nó tìm personalization tạo trong cùng cart cho cùng variant trong một tháng dương lịch trở về trước, mỗi personalization dùng cho một item, không hứa dùng lần nào nếu shopper personalize cùng variant nhiều lần. Dev xác nhận hành vi này trên build hiện tại, và 'có id' nghĩa là gì so với 'id số hoặc UUID hợp lệ' của bản fix TIB-5563 (KB-762, OQ-order-047)? Người trả lời: Dev.", "kb_ids": ["KB-783"]}
```

## OQ-order-087 — NEEDS_CONFIRMATION

```json
{"oq_id": "OQ-order-087", "type": "NEEDS_CONFIRMATION", "feature_id": "fulfillment-provider-request", "summary": "Theo spec-hub (rule bulk-fulfill-grouping; S2, KB-784), Confirm & Send gom item theo print provider rồi theo order, hoặc theo shipping address khi store gộp đơn theo shipping address; mỗi nhóm một provider order. Dev xác nhận hành vi này, và tên setting thật của việc gộp đơn là gì: KB-776 và CHK-005 gọi là order_combine_by, spec-hub không nêu tên (CCR CBS-138 CLAIM-05, câu hỏi không nguồn); giá trị nào ứng với gộp theo order và theo shipping address? Liên quan OQ-order-080. Người trả lời: Dev.", "kb_ids": ["KB-784", "KB-776"]}
```
