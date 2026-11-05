# Product guide — teeinblue

Tổng quan và setup của Teeinblue: product làm gì, chức năng ở đâu, cần env, account gì để chạy. File được cập nhật cùng các lần publish knowledge: setup mức product mới thì thêm vào đây. Config riêng và khác biệt staging/production của một feature nằm ở `profile.json` của feature đó.

Đọc theo vai trò:

| Bạn là | Đọc | Để làm gì |
|---|---|---|
| Newbie / agent mới | §0 → §4 → §9 | hiểu product, biết chức năng nằm ở đâu |
| Agent kiểm thử | §0 → §2 → §5 → §8 → §10 | dựng data và test một feature bất kỳ |

**Guide này trả lời "vào đâu, làm thế nào". KB và checklist cùng thư mục trả lời "đúng phải là gì".** Không dùng guide này làm expected result. Không ghi credential, email hay tên người thật vào file này.

**Độ tin cậy của từng thông tin:**

| Nhãn | Nghĩa |
|---|---|
| `[KB]` | Có trong knowledge đã publish |
| `[QA]` | Từ sổ tay QA hằng ngày, đã kiểm chứng trên staging |
| `[?]` | Chưa biết. Ai gặp thì ghi lại và báo operator |

## 0. Product trong 5 phút

Teeinblue là app cá nhân hoá sản phẩm in theo yêu cầu (print-on-demand). Merchant dựng sản phẩm trên portal, buyer tự điền nội dung trên storefront, order đi kèm file design để in. `[KB]`

Luồng chính:

1. Merchant tạo **Product base**: phôi có variant, print area, mockup. Hoặc dùng sẵn Shopify product.
2. Merchant thiết kế **Artwork** gồm nhiều layer, cấu hình personalization, điều kiện hiển thị, giá trị tự điền.
3. Merchant ghép thành **Campaign** rồi publish lên store.
4. Buyer mở product page, **SDK** hiện form và live preview, buyer điền rồi add to cart. Customization đi kèm cart qua line item properties.
5. Order về portal, teeinblue render design, merchant review và gửi fulfillment.

Phần phụ trợ: thư viện asset (clipart, vector, color, map style, font, image), Global Option dùng chung nhiều campaign, translation cho storefront.

**Knowledge hiện có:** 10 object, 62 feature, 715 KB item (110 `CONFIRMED_EXPECTED`, 581 `OBSERVED_CURRENT`, 19 `INFERRED`, 5 `PROPOSED`), 1085 check (558 `READY`, 526 `NEEDS_CONFIRMATION`), 579 Open Question (36 `CONFLICT`). Phần lớn KB là quan sát, nên nhiều check chưa đủ làm oracle.

## 1. Surfaces và entry point

| Surface | Staging | Ghi chú |
|---|---|---|
| Portal (merchant) | `staging-portal.teeinblue.com` | SPA, biến `TIB_PORTAL_BASE` |
| API portal | `staging-api.teeinblue.com/api` | Cookie session, REST và GraphQL `/api/graphql` |
| API merchant (SDK gọi) | `staging-api.teeinblue.com/api/merchant/...` | Public, cần tham số `shop` |
| SDK storefront | `staging-sdk.teeinblue.com` | `shopify/app-v1.js`, `app-v2.js`, `open/index.js` |
| Customize page | `staging-sdk.teeinblue.com/customize/` | |
| Upload | `upload-staging.teeinblue.com` | |
| Open API | Biến `TIB_OPENAPI_BASE` | Bearer token, xem §2 |

**Nhận biết production để dừng lại:** `portal.teeinblue.com`, `api.teeinblue.com`, `portal-api.teeinblue.com`, `sdk.teeinblue.com`, `customize.teeinblue.com`, `photo-api.teeinblue.com`. Trên storefront, xem script SDK: `staging-sdk` là staging. `[QA]`

Trang chính của portal `[QA]`:

| Menu | Route |
|---|---|
| Campaigns by Product Base | `/campaigns` |
| Campaigns by Shopify Products | `/platform-products` |
| Product Base | `/products` |
| Artworks | `/artworks` |
| Assets | `/cliparts`, `/vectors`, `/fonts`, `/global-options` |
| Extras > Dynamic Translations | `/artwork-translations` |
| Store Settings | `/general-settings`, `/product-page-settings`, `/product-page-content` |
| Trash, Activity logs | `/trash`, `/activity-logs` |

`/settings` trả 404. Sau login portal luôn về `/`, phải tự mở lại trang đích.

**Không có:** agent không có DB access. Khi expected nằm ở bảng nội bộ, người có quyền chạy query read-only do agent soạn. Job theo lịch thì nhờ Dev chạy command trên staging, không chờ tới giờ chạy. `[QA]`

## 2. Auth và xác minh account

**Biến env.** Chỉ ghi tên, giá trị do operator cấp trong `.env` không commit.

| Nhóm | Biến | Dùng cho |
|---|---|---|
| Account chính | `TIB_STAGING_EMAIL`, `TIB_STAGING_PASSWORD` | Login portal |
| Host | `TIB_STAGING_PORTAL`, `TIB_API_BASE`, `TIB_OPENAPI_BASE` | Portal, API, Open API. Một số bộ env đặt portal là `TIB_PORTAL_BASE` |
| Storefront | `TIB_STORE_URL`, `TIB_STORE_PASSWORD` | Storefront SDK v1 |
| Storefront v2 | `TIB_SDK_V2`, `TIB_SDK_V2_PASSWORD` | Storefront SDK v2 |
| Public | `TIB_STAGING_PUBLIC_USER`, `TIB_STAGING_PUBLIC_INSTANCE_ID` | `[?]` chưa rõ mục đích |
| Hai tenant | `TIB_USER_A_*`, `TIB_USER_B_*` | Permission, cross-tenant |
| Account đặc thù | `TIB_BOUNDLESS_*`, `TIB_ONBOARDING_*`, `TIB_STAFF_VIEW_ONLY*`, `TIB_STAFF_GEN_ONLY*` | Boundless, store chưa connect fulfillment, staff quyền hạn chế |
| Token Open API | `TIB_FULL_ACCESS_TOKEN`, `TIB_ORDERS_*_TOKEN`, `TIB_CUSTOMIZATIONS_READ_TOKEN`, `TIB_ASSETS_*_TOKEN`, `TIB_USER_B_*_TOKEN` | Theo ability |
| Token negative | `TIB_FORBIDDEN_TOKEN`, `TIB_INVALID_TOKEN`, `TIB_REVOKED_TOKEN`, `TIB_ASSETS_REVOKED_TOKEN` | Negative auth |
| Điều kiện đặc biệt | `TIB_NO_MAPBOX_KEY_TOKEN` | Account không có Mapbox |

Tạo token bằng `POST /api/tokens` với `name` và `abilities`. Giá trị chỉ hiện lúc tạo. Ability: `orders:read`, `orders:write`, `customizations:read`, `campaigns:read`, `products:read`, `mcp:access`. `[QA]`

**Login, làm lại sau mỗi lần session hết hạn:**

1. Mở `/login?staff=true`. Route `/login` là đường Shopify owner, không dùng.
2. Ghi đè cả email lẫn password. Form có thể autofill email của account khác; chỉ điền password là vào nhầm.
3. `GET /api/user` và sidebar phải khớp account của biến đang dùng. Sai thì dừng, không tạo data.

**Session:** cookie Laravel Sanctum, không còn JWT trong `localStorage`, TTL khoảng 15 phút, login lại thay vì dùng lại storageState cũ. Gọi API ngoài UI: chạy `fetch()` trong page với `credentials: 'include'` và header `X-XSRF-TOKEN`. Ngoài browser: `GET /sanctum/csrf-cookie` với Origin/Referer của portal, rồi `POST /api/login`. Thiếu User-Agent thì 403. Trang login có Cloudflare Turnstile; hiện challenge thì dừng và nhờ người login tay. 2FA tắt từ 2026-10-28; `/login/two-factor` hiện lại thì nhờ người nhập mã. `[QA]`

**Instance active lưu phía server theo account**, dùng chung giữa các phiên, có thể bị phiên khác đổi giữa chừng. Kiểm lại sidebar trước khi tạo data. `[QA]`

## 3. Object map

Danh sách object hợp lệ và alias: `_registry.json`.

| `object_key` | Surface chính | Phạm vi |
|---|---|---|
| `campaign` | portal | Tạo, duyệt, xoá campaign, đồng bộ media Shopify. Phía storefront thuộc `sdk` |
| `product-base` | portal | Duyệt, tạo, print area, variant, mockup, vòng đời, liên kết campaign |
| `artwork` | portal + storefront preview | Editor, layer, config, điều kiện, populate, render |
| `asset-category` | portal | 6 loại category: Clipart, Vector, Color, Additional Option, Map Style, Font Category |
| `font` | portal | `/fonts`, khác font category |
| `image-library` | portal | Thư viện ảnh của Image layer và Mockup layer, không có trang riêng |
| `global-option` | portal | Option dùng chung nhiều campaign |
| `translation` | portal + storefront | Dynamic Translations, Product Page Content, chọn ngôn ngữ |
| `order` | storefront + portal | Đặt order, review, fulfillment |
| `sdk` | storefront | Runtime personalization của buyer, Product Page Settings, open platform |

## 4. Vocabulary

| Thuật ngữ | Nghĩa |
|---|---|
| Instance | Một store gắn với account trên teeinblue |
| Campaign | Sản phẩm bán ra: product base + artwork + cấu hình personalization |
| Product base | Phôi sản phẩm với variant, print area, mockup |
| Artwork | Thiết kế nhiều layer có thể cá nhân hoá. Có schema 1.0 và 2.0 |
| Personalization option | Input buyer điền trên storefront, map vào layer |
| Global Option | Option định nghĩa một lần, gắn vào nhiều artwork |
| Populate values | Tự điền giá trị layer từ layer khác |
| Conditional setting | Điều kiện hiện hoặc ẩn layer |
| Live preview | Ảnh xem trước cập nhật theo input của buyer |
| SDK | Runtime personalization trên storefront, không phải software package |
| Customization | Bộ giá trị buyer đã điền, lưu khi add to cart |
| Line item properties | Dữ liệu personalization đi kèm item trong cart |
| Boundless / open platform | Kênh không phải Shopify, nhúng SDK qua iframe |

## 5. Mutation guard

- **Production chỉ đọc**, trừ khi operator giao đúng việc đó.
- Data tự tạo có tiền tố `QA-`, dọn sau khi test. Chỉ xoá data mình tạo, không sửa data có sẵn của người khác.
- Order chỉ đặt bằng thanh toán test.
- Config dùng chung của store hoặc account: ghi lại giá trị trước khi đổi, trả về sau khi test.
- Evidence phải che token: `GET /api/instances/<id>` và một số response trả kèm `token`, API key. `[QA]`

## 6. Network / API hints

| Mục đích | Request `[QA]` |
|---|---|
| User hiện tại | `GET /api/user` |
| Danh sách instance | `GET /api/instances` |
| GraphQL portal | `POST /api/graphql`, id kiểu `bigint` |
| Đọc artwork | GraphQL `artworks_by_pk`. `GET /api/artworks/<id>` trả 405 |
| Config campaign công khai | `GET /api/merchant/campaigns/<shopifyProductId>.json?shop=<shop>` |
| Lưu customization | `POST /api/merchant/shopify/customization?shop=<shop>&id=<productId>` |
| Đọc customization | `GET /api/merchant/shopify/customization/<uuid>?shop=<shop>` |
| Shopify product id | Storefront `/products/<handle>.js` |

Gọi thẳng `staging-graphql.teeinblue.com` trả "Invalid response from authorization hook". Request analytics và chat widget là nhiễu. Endpoint lặp theo chu kỳ khi không có action là polling.

## 7. Gotchas

Áp dụng cho nhiều feature. `[QA]`

| Dấu hiệu | Cách hiểu |
|---|---|
| Sau `Save` không có lỗi console | Đọc toast: đây là cách duy nhất biết validate fail ở artwork editor |
| Mất layer chưa lưu | Session hết hạn im lặng. Save sớm, save từng chặng |
| Đã sửa mà storefront vẫn cũ | `app-v1.js` không có hash, cache rất lâu. So bundle trang đang chạy với `fetch(url, {cache:'no-store'})`, lệch thì bust rồi reload |
| Field storefront có sẵn giá trị cũ, gõ bị nối | SDK khôi phục từ localStorage. Dùng context sạch |
| Toggle mặc định khác mong đợi | Mặc định theo config shop (`default_value`). Đọc config trước khi báo bug |
| `ERR_FAILED` kèm lỗi CORS khi body có `<script` hoặc `onload=` | WAF chặn. Không suy ra app an toàn |
| Ngưỡng rate limit khác ticket | Staging cố ý đặt nhỏ hơn. Tin header `x-ratelimit-limit` |
| Storefront 404 dù campaign by Shopify đã publish | Shopify product chưa bật Online Store |
| Trang "Verify you are human" trên storefront | Bot protection của Shopify sau nhiều request. Nghỉ vài phút, dùng browser đã vào được |
| Upload qua Playwright lọt `accept` | Tool bypass, merchant thật bị chặn ở FE. Không log bug |
| Theme editor, checkout editor không có data teeinblue | Chỉ là placeholder. Verify bằng storefront thật |
| Sidebar collapse, label có icon | Chờ `attached`, match theo `href` |
| Click chữ của toggle không ăn | Toggle là `label.vue-js-switch` |
| Dialog Confirm password không hiện | Có hiệu lực 15 phút sau lần xác nhận trước |

**SDK v1 và v2 khác nhau ở UI, cùng hợp đồng dữ liệu** `[QA]`:

| Điểm | v1 | v2 |
|---|---|---|
| Nút add to cart | `#teeAtcButton` | Nút của theme |
| Endpoint cart | `/cart/add.js` (JSON) | `/cart/add` (FormData) |
| Auto chọn template | Có | Không, phải chọn tay |

## 8. Dựng test data

Login theo §2 trước. Mỗi fixture ghi lại id.

| Mã | Fixture | Cách dựng | Lưu ý |
|---|---|---|---|
| F0 | Session | Login theo §2 | Bắt buộc cho mọi fixture |
| F1 | Product base | `/products/new`, thêm print area, variant, mockup | Có thể duplicate thay vì tạo mới |
| F2 | Artwork | `/artworks`, thêm layer cần test, Save từng chặng | `Save & Close` chỉ tạo artwork, chưa gắn vào print area |
| F3 | Campaign by Product Base | `/campaigns/new`, add F1, gắn F2 vào print area | Kiểm print area đã đổi |
| F4 | Campaign by Shopify | `/platform-products/new`, chọn Shopify product, connect variant | Product phải bật Online Store |
| F5 | Storefront | Publish F3 hoặc F4, mở `TIB_STORE_URL` bằng `TIB_STORE_PASSWORD` | Dùng context sạch |
| F6 | Order | Add to cart từ F5 rồi checkout | Bogus gateway, hiển thị "Credit card": thẻ `1` thành công, `2` fail, `3` exception |
| F7 | Asset | Category, item, font, ảnh trong trang Assets | Tên `QA-`. Tạo layer-image dồn dập có thể bị 429 |
| F8 | Global Option | `/global-options/create` | Bật Show in cart nếu cần thấy ở cart |
| F9 | Hai tenant | `TIB_USER_A_*`, `TIB_USER_B_*` | Thiếu biến thì check là `NOT_COVERED`, không thay account khác |

**Chọn biến theo việc** `[QA]`:

| Việc cần test | Dùng |
|---|---|
| Portal, storefront, Thank You, Order status | `TIB_STAGING_EMAIL`, `TIB_STORE_URL` |
| App block trên Checkout page (cần Shopify Plus) | `TIB_SDK_V2` |
| Open platform | `TIB_BOUNDLESS_*`. Dùng data sẵn có |
| Store chưa connect fulfillment | `TIB_ONBOARDING_*`. Chỉ đọc, giữ sạch |
| Staff quyền hạn chế | `TIB_STAFF_VIEW_ONLY*`, `TIB_STAFF_GEN_ONLY*` |

## 9. Bản đồ feature

Số check lấy từ checklist đã publish (`READY` / tổng). Cột Fixture trỏ về §8.

### `artwork` (version 12)

| Feature | Vào ở đâu | Check | Fixture |
|---|---|---|---|
| `artwork-list-management` | `/artworks` | 5 / 12 | F0 |
| `artwork-save-persist` | Artwork editor, `Save`, `Save & Close` | 12 / 20 | F2 |
| `artwork-template-management` | Editor, Template bar | 10 / 15 | F2 |
| `clipart-category-storefront-behavior` | Storefront, form và Preview của layer clipart | 13 / 22 | F5, F7 |
| `condition-cycle-validation` | Editor, accordion Conditional Setting, Save | 8 / 13 | F2 |
| `conditional-setting-config` | Editor, accordion Conditional Setting | 13 / 21 | F2 |
| `editor-layer-workspace` | Editor, `+ Layer`, canvas | 13 / 18 | F2 |
| `group-layer-effective-visibility` | Editor 2.0, mắt của Group trong layer panel | 10 / 15 | F2 |
| `group-layer-order-design-render` | Order detail, Item Activity logs | 6 / 16 | F6 |
| `layer-common-config` | Editor, config panel của layer | 10 / 13 | F2 |
| `layer-condition-value-binding` | Layer đã có condition, đọc qua PUT response hoặc GraphQL | 5 / 12 | F2 |
| `layer-config-form-elements` | Editor, nhóm Form Elements | 8 / 9 | F2 |
| `layer-config-image` | Editor, nhóm Image | 34 / 53 | F2, F7 |
| `layer-config-maps-astronomy` | Editor, nhóm Maps & Astronomy | 4 / 6 | F2 |
| `layer-config-others` | Editor, nhóm Others | 4 / 5 | F2 |
| `layer-config-puzzles` | Editor, nhóm Puzzles | 4 / 5 | F2 |
| `layer-config-text` | Editor, nhóm Text | 6 / 9 | F2 |
| `layer-config-vector` | Editor, nhóm Vector | 6 / 8 | F2, F7 |
| `layer-duplicate-link-copy` | Editor, layer action bar, Copy to clipboard | 5 / 12 | F2 |
| `layer-print-effects` | Editor, toolbar canvas, Print Effects | 4 / 10 | F2 |
| `populate-values` | Editor, accordion Populate Values | 17 / 25 | F2 |
| `psd-import` | `/artworks`, Import, PSD Single template | 1 / 5 | F0 |
| `text-color-sequence-render` | Storefront, rồi Locate Artwork của line item | 0 / 19 | F5, F6 |
| `text-multi-stroke` | Editor 2.0, popover Stroke | 0 / 25 | F2 |

### `asset-category` (version 1)

| Feature | Vào ở đâu | Check | Fixture |
|---|---|---|---|
| `asset-category-bulk-upload` | Trang category, bulk upload zip | 7 / 10 | F7 |
| `asset-category-crud` | `/cliparts`, `/vectors` và các trang category | 13 / 18 | F7 |
| `asset-category-item-management` | Trang chi tiết category | 9 / 17 | F7 |
| `asset-category-route-entity-clarification` | Các route category trong Assets | 5 / 7 | F0 |

### `campaign` (version 6)

| Feature | Vào ở đâu | Check | Fixture |
|---|---|---|---|
| `campaign-delete` | `/campaigns`, menu `...`, Delete campaign | 3 / 9 | F3 |
| `campaign-list-browse` | `/campaigns` | 5 / 15 | F0 |
| `campaign-navigation` | Sidebar, Campaigns | 3 / 6 | F0 |
| `campaign-security-permissions` | Campaign của tenant khác | 3 / 9 | F3, F9 |
| `campaign-shopify-media-sync` | Campaign editor, Update hoặc publish | 1 / 5 | F3 |
| `create-campaign-by-product-base` | `/campaigns/new` | 21 / 38 | F1, F2 |
| `create-campaign-by-shopify` | `/platform-products/new` | 12 / 20 | F2, F4 |

### `font` (version 1)

| Feature | Vào ở đâu | Check | Fixture |
|---|---|---|---|
| `manage-uploaded-font` | `/fonts`, action trên font card | 4 / 9 | F7 |
| `upload-custom-font` | `/fonts`, Upload fonts | 4 / 10 | F0 |
| `use-custom-font-in-artwork-editor` | Editor, text layer, Custom Fonts | 1 / 6 | F2, F7 |
| `view-and-configure-font-list` | `/fonts` | 9 / 12 | F0 |

### `global-option` (version 3)

| Feature | Vào ở đâu | Check | Fixture |
|---|---|---|---|
| `artwork-personalization-global-option-link` | Editor, Personalization Settings | 15 / 28 | F2, F8 |
| `global-option-additional-option-items` | `/global-options/<id>/edit` | 8 / 14 | F8 |
| `global-option-instance-management` | `/global-options`, `/global-options/create` | 11 / 24 | F0 |

### `order` (version 5)

| Feature | Vào ở đâu | Check | Fixture |
|---|---|---|---|
| `place-personalized-order-storefront` | Storefront, product page đến cart | 11 / 22 | F5 |
| `review-and-initiate-fulfillment-portal` | Portal, Orders, order detail | 14 / 26 | F6 |

### `product-base` (version 6)

| Feature | Vào ở đâu | Check | Fixture |
|---|---|---|---|
| `mockup-attachment` | `/products/{id}/edit`, section Mockup | 9 / 17 | F1 |
| `printarea-definition` | `/products/{id}/edit`, section Printareas | 15 / 16 | F1 |
| `product-base-browse` | `/products`, `?tab=archived` | 14 / 16 | F0 |
| `product-base-campaign-link` | `/products`, icon Update campaign | 12 / 17 | F3 |
| `product-base-create` | `/products/new` | 13 / 14 | F0 |
| `product-base-identity` | `/products/{id}/edit` | 9 / 9 | F1 |
| `product-base-lifecycle` | `/products`, menu `...` | 10 / 10 | F1 |
| `variant-add-to-campaigns` | Product base, bảng Variants, Add to campaigns | 10 / 23 | F3 |
| `variant-catalog` | `/products/{id}/edit`, section Variants | 13 / 16 | F1 |

### `sdk` (version 13)

| Feature | Vào ở đâu | Check | Fixture |
|---|---|---|---|
| `genai-personalization-runtime` | Editor, Live Preview | 10 / 23 | F2 |
| `open-platform-customization-callback` | SDK open platform trong iframe | 1 / 5 | `TIB_BOUNDLESS_*` |
| `product-page-settings-config` | `/product-page-settings` | 15 / 25 | F0 |
| `storefront-buyer-facing` | Storefront, product page của campaign | 46 / 100 | F5 |

### `translation` (version 2)

| Feature | Vào ở đâu | Check | Fixture |
|---|---|---|---|
| `dynamic-translations` | `/artwork-translations`, storefront theo locale | 10 / 26 | F3, F5 |
| `language-locale-switcher` | Portal và header storefront | 5 / 9 | F5 |
| `product-page-content-translation` | `/product-page-content`, storefront | 9 / 13 | F5 |

### `image-library` (version 1)

| Feature | Vào ở đâu | Check | Fixture |
|---|---|---|---|
| `image-layer-library` | Editor, `+ Layer`, Image, hoặc Replace image layer | 0 / 43 | F2, F7 |
| `mockup-layer-library` | `/products/<id>/edit`, section Mockup | 0 / 30 | F1, F7 |

## 10. Quy trình kiểm thử

Làm theo thứ tự với một feature hoặc một ticket:

1. **Chọn feature:** map từ khoá sang `object_key` qua `_registry.json`. Đọc `manifest.json` ở gốc repo để biết object có `PUBLISHED`, version nào. Quy tắc đầy đủ: `how-to-request/consumer-guide.md` §2–§4.
2. **Đọc knowledge:** `<object>/feature-summary.md` → `features/<feature>/profile.json` → `checklists/<feature>.json` → `open-questions.md` lọc theo feature. Trong profile, xem `entry_points[].precondition` để biết config riêng của feature, và `environment_differences` nếu có.
3. **Dựng data:** theo cột Fixture ở §9, sau khi login theo §2.
4. **Chạy từng check:** `precondition` → `steps` → xem `observation_point` → so `expected_result`.
5. **Ghi evidence:** tên biến account (không ghi email), id data, thời điểm, screenshot hoặc response đã che token. Re-test SDK thì ghi thêm bundle đã bust hay chưa.
6. **Dọn data** theo §5.

**Kết luận mỗi check:**

| Tình huống | Kết luận |
|---|---|
| `status: READY`, khớp `expected_result` | `PASS` |
| `status: READY`, oracle `STRONG`, lệch | `FAIL`. Trước đó loại trừ §7: cache, config shop, môi trường |
| `status: READY`, oracle `BASELINE`, lệch | `SUSPECTED_FAIL`: baseline chỉ là hành vi đã thấy, ghi evidence rồi đối chiếu PO/Dev |
| `status: NEEDS_CONFIRMATION`, oracle `NONE`, hoặc item `UNRESOLVED` | Chỉ ghi `OBSERVED: <hành vi thật>`, không kết luận |
| `environment_differences` có `NOT_TESTABLE` | `NOT_APPLICABLE` trên môi trường đó |
| Không quan sát được, thiếu quyền, thiếu data | `NOT_COVERED` hoặc `BLOCKED`, nêu rõ thiếu gì |

**Trước khi báo bug:** race condition thì đo ngưỡng trigger và chạy lại bằng thao tác thật, vì `dispatchEvent` liền `blur` có thể chỉ là artifact của automation. Sai giá trị mặc định thì đọc config shop trước. `[QA]`

**Sau khi test:**

- Hành vi thật khác knowledge, hoặc đã xác nhận một Open Question → gửi CCR bằng skill `create-ccr` (`consumer-guide.md` §5).
- Bug thật → báo theo quy trình của team trên Testlane. Không tự tạo hay comment Jira, không nhắn kênh ngoài khi operator chưa đồng ý.
- Guide sai hoặc gặp `[?]` đã có đáp án → báo operator để cập nhật mục đó.
