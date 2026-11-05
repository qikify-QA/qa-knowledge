# Product guide — teeinblue

Bản chỉ dẫn của Teeinblue: product làm gì, feature ở đâu, môi trường nào test được gì, setup ra sao. Chi tiết của từng feature nằm ở `<object>/features/<feature>/profile.json`.

| Đang làm | Đọc |
|---|---|
| Phân tích yêu cầu, viết test case | Phần A |
| Dựng data, chạy test | Phần A, Phần B |

**Guide trả lời "vào đâu, làm thế nào". KB và checklist trả lời "đúng phải là gì".** Không dùng guide làm expected result. Không ghi giá trị credential, id account, id instance, tên store vào file này: biến env ở `_env.example`, giá trị ở `.env` local.

<!-- PART-A:start -->
# Phần A: Bản đồ

## A1. Product

Teeinblue là app cá nhân hoá sản phẩm in theo yêu cầu (print-on-demand). Luồng chính:

1. Merchant tạo **Product base** (phôi có variant, print area, mockup) hoặc dùng sẵn Shopify product.
2. Merchant thiết kế **Artwork** nhiều layer, cấu hình personalization, condition, populate.
3. Merchant ghép thành **Campaign** rồi publish lên store.
4. Buyer mở product page, **SDK** hiện form và live preview, buyer điền rồi add to cart. **Customization** đi kèm cart qua line item properties.
5. Order về portal, teeinblue render design, merchant review và gửi fulfillment.

| Thuật ngữ | Nghĩa |
|---|---|
| Instance | Một store gắn với account trên teeinblue |
| Personalization option | Input buyer điền trên storefront, map vào layer |
| Global Option | Option định nghĩa một lần, gắn vào nhiều artwork |
| Populate values | Tự điền giá trị layer từ layer khác |
| Conditional setting | Điều kiện hiện hoặc ẩn layer |
| Boundless / open platform | Kênh không phải Shopify, nhúng SDK qua iframe |

## A2. Object và feature

Từ khoá ticket sang object: `_registry.json`. Trạng thái, version, dùng làm oracle được không: `manifest.json`. Mỗi feature có `features/<key>/profile.json` (entry point, precondition, `environment_differences`) và `checklists/<key>.json`.

| Object | Phạm vi | Không thuộc | Feature |
|---|---|---|---|
| `campaign` | Tạo, duyệt, xoá campaign, đồng bộ media Shopify | Phía storefront (`sdk`) | `campaign-delete` `campaign-list-browse` `campaign-navigation` `campaign-security-permissions` `campaign-shopify-media-sync` `create-campaign-by-product-base` `create-campaign-by-shopify` |
| `product-base` | Print area, variant, mockup, vòng đời, liên kết campaign | Thư viện ảnh mockup (`image-library`) | `mockup-attachment` `printarea-definition` `product-base-browse` `product-base-campaign-link` `product-base-create` `product-base-identity` `product-base-lifecycle` `variant-add-to-campaigns` `variant-catalog` |
| `artwork` | Editor, layer, config, condition, populate, render | Form buyer trên storefront (`sdk`) | **Quản lý:** `artwork-list-management` `artwork-save-persist` `artwork-template-management` `editor-layer-workspace` `psd-import` · **Layer:** `layer-common-config` `layer-config-form-elements` `layer-config-image` `layer-config-maps-astronomy` `layer-config-others` `layer-config-puzzles` `layer-config-text` `layer-config-vector` `layer-duplicate-link-copy` `layer-print-effects` `text-multi-stroke` · **Logic:** `condition-cycle-validation` `conditional-setting-config` `layer-condition-value-binding` `populate-values` · **Group, render:** `group-layer-effective-visibility` `group-layer-order-design-render` `text-color-sequence-render` `clipart-category-storefront-behavior` |
| `asset-category` | 6 loại category: Clipart, Vector, Color, Additional Option, Map Style, Font Category | Font (`font`) | `asset-category-bulk-upload` `asset-category-crud` `asset-category-item-management` `asset-category-route-entity-clarification` |
| `font` | `/fonts` | Font category (`asset-category`) | `manage-uploaded-font` `upload-custom-font` `use-custom-font-in-artwork-editor` `view-and-configure-font-list` |
| `image-library` | Thư viện ảnh của Image layer và Mockup layer, không có trang riêng | Clipart (`asset-category`) | `image-layer-library` `mockup-layer-library` |
| `global-option` | Option dùng chung nhiều campaign | | `artwork-personalization-global-option-link` `global-option-additional-option-items` `global-option-instance-management` |
| `translation` | Dynamic Translations, Product Page Content, chọn ngôn ngữ | | `dynamic-translations` `language-locale-switcher` `product-page-content-translation` |
| `order` | Đặt order, review, fulfillment | | `place-personalized-order-storefront` `review-and-initiate-fulfillment-portal` |
| `sdk` | Runtime personalization của buyer, Product Page Settings, open platform | | `genai-personalization-runtime` `open-platform-customization-callback` `product-page-settings-config` `storefront-buyer-facing` |

Ticket không khớp key nào: ghi knowledge gap, đề xuất key mới trong CCR.

## A3. Môi trường

Host từng môi trường: B1. Nhận biết môi trường của storefront: xem script SDK.

**Store theo việc:**

| Biến | Đặc điểm | Dùng cho | Không dùng cho |
|---|---|---|---|
| `TIB_STORE_URL`, `TIB_STORE_INSTANCE_ID` | Dev store, non-Plus | Mặc định: portal, storefront, Thank You, Order status | App block trên Checkout page, Generate test design |
| `TIB_SDK_V2`, `TIB_SDK_V2_INSTANCE_ID` | Shopify Plus | App block trên Checkout page, storefront SDK v2 | |
| `TIB_BOUNDLESS_*`, `TIB_BOUNDLESS_INSTANCE_ID` | Boundless, không có storefront thật | Case Boundless trên portal | Campaign by Shopify; chạy song song với store mặc định (chung account) |
| `TIB_BOUNDLESS_STOREFRONT_INSTANCE_ID` | Storefront Boundless | Case Boundless cần storefront | Tạo data mới |
| `TIB_ONBOARDING_*` | Chưa connect fulfillment | Luồng onboarding | Chỉ đọc, giữ sạch |
| `TIB_USER_A_*`, `TIB_USER_B_*` | Hai tenant | Permission, cross-tenant | Thiếu biến thì `NOT_COVERED`, không thay account khác |
| `TIB_STAFF_VIEW_ONLY*`, `TIB_STAFF_GEN_ONLY*` | Staff quyền hạn chế | Phân quyền | |

**Cần người hỗ trợ:**

- Bảng nội bộ không lộ qua GraphQL: agent soạn query read-only, người có quyền chạy.
- Job theo lịch: nhờ Dev chạy command trên staging, không chờ tới giờ.
- Config server (provider key, branch, migration): là điều kiện tiên quyết cho Dev.

## A4. Index giới hạn môi trường

Chi tiết và cách test: `environment_differences` trong profile của feature. `type`: `NOT_TESTABLE` không chạy, `ALTERNATIVE_SETUP` test theo cách khác, `DIFFERENT_VALUE` test theo giá trị của staging.

| Hạng mục | Feature | `type` | Mức |
|---|---|---|---|
| Generate test design trên dev store | `campaign/create-campaign-by-product-base` | `ALTERNATIVE_SETUP` | Vế |
| Horizon (job failed, queued) | Nhiều feature | `NOT_TESTABLE` | Vế |
| Strava trong Route Maps | `artwork/layer-config-maps-astronomy`, `sdk/storefront-buyer-facing` | `NOT_TESTABLE` | Vế |
| Tracking từ provider | `order/review-and-initiate-fulfillment-portal` | `NOT_TESTABLE` | Case |
| Size gốc của provider | `product-base/printarea-definition` | `NOT_TESTABLE` | Vế |
| `photo_endpoint=snap` | `sdk/storefront-buyer-facing` | `DIFFERENT_VALUE` | Case hoặc vế |
| Upload CORS, preconnect tới host production | `sdk/storefront-buyer-facing` | `NOT_TESTABLE` | Vế |
| Network timing | `sdk/storefront-buyer-facing` | `ALTERNATIVE_SETUP` | Vế |
| Browser chặn site data, ITP | `sdk/storefront-buyer-facing` | `ALTERNATIVE_SETUP` | Vế |

## A5. Bẫy làm sai kết luận

| Dấu hiệu | Cách hiểu |
|---|---|
| Bản dịch vừa Save chưa lên storefront | Cache theo `translation_version`. Đợi rồi reload, hoặc mở context sạch |
| Toggle mặc định khác mong đợi | Mặc định theo config shop (`default_value`). Đọc config trước khi báo bug |
| `ERR_FAILED` kèm lỗi CORS khi body có `<script` hoặc `onload=` | WAF chặn. Không suy ra app an toàn |
| Ngưỡng rate limit khác ticket | Staging cố ý đặt nhỏ hơn. Tin header `x-ratelimit-limit` |
| Link Edit Customization trên staging 404 | Link luôn trỏ customize production. Đổi host sang customize staging, giữ nguyên query |
| Upload qua Playwright lọt `accept` | Tool bypass, merchant thật bị chặn ở FE. Không log bug |

## A6. Mutation guard

- **Production chỉ đọc**, trừ khi operator giao đúng việc đó.
- Data tạo cho một ticket đặt tên theo title ticket và giữ lại sau test. Không sửa data có sẵn của người khác.
- Thay đổi tạm (config store, throttle, route) phải trả về giá trị cũ sau khi test.
- Order chỉ đặt bằng thanh toán test.
- Evidence phải che token: `GET /api/instances/<id>` và một số response trả kèm `token`, API key.
<!-- PART-A:end -->

<!-- PART-B:start -->
# Phần B: Thực thi

## B1. Env và login

| Surface | Staging | Production (thấy host này thì dừng) |
|---|---|---|
| Portal | `staging-portal.teeinblue.com` | `portal.teeinblue.com` |
| API portal, REST và GraphQL `/api/graphql` | `staging-api.teeinblue.com/api` | `portal-api.teeinblue.com/api` |
| API merchant (SDK gọi) | `staging-api.teeinblue.com/api/merchant/...` | `api.teeinblue.com` |
| SDK storefront | `staging-sdk.teeinblue.com` | `sdk.teeinblue.com` |
| Customize page | `staging-sdk.teeinblue.com/customize/` | `customize.teeinblue.com` |
| Upload | `upload-staging.teeinblue.com` | `photo-api.teeinblue.com` |
| CDN design order | `cdn.ownego.com/teeinblue-staging/designs/` | `cdn.teeinblue.com/designs/` |
| Open API | `TIB_OPENAPI_BASE` | |

Chép `_env.example` thành `.env` rồi điền giá trị do operator cấp. Tạo token bằng `POST /api/tokens` với `name` và `abilities`, giá trị chỉ hiện lúc tạo. Ability: `orders:read`, `orders:write`, `customizations:read`, `campaigns:read`, `products:read`, `mcp:access`.

**Login, làm lại sau mỗi lần session hết hạn:**

1. Mở `/login?staff=true`. Route `/login` là đường Shopify owner, không dùng.
2. Ghi đè cả email lẫn password. Form có thể autofill email của account khác.
3. `GET /api/user` và sidebar phải khớp account của biến đang dùng. Sai thì dừng, không tạo data.

**Session:** cookie Laravel Sanctum, TTL khoảng 15 phút. storageState hết hạn thì tạo lại. Gọi API trong page: `fetch()` với `credentials: 'include'` và header `X-XSRF-TOKEN`. Ngoài browser: `GET /sanctum/csrf-cookie` với Origin/Referer của portal, rồi `POST /api/login`. Thiếu User-Agent thì 403. Cloudflare Turnstile hiện challenge thì nhờ người login tay. `/login/two-factor` hiện lại thì nhờ người nhập mã.

**Instance active lưu phía server theo account**, phiên khác có thể đổi giữa chừng. Kiểm sidebar trước khi tạo data.

## B2. Dựng test data

| Mã | Fixture | Cách dựng | Lưu ý |
|---|---|---|---|
| F0 | Session | Login theo B1 | Bắt buộc cho mọi fixture |
| F1 | Product base | `/products/new`, thêm print area, variant, mockup | Có thể duplicate thay vì tạo mới |
| F2 | Artwork | `/artworks`, thêm layer cần test, Save từng chặng | `Save & Close` chỉ tạo artwork, chưa gắn vào print area |
| F3 | Campaign by Product Base | `/campaigns/new`, add F1, gắn F2 vào print area | |
| F4 | Campaign by Shopify | `/platform-products/new`, chọn Shopify product, connect variant | Product phải bật Online Store |
| F5 | Storefront | Publish F3 hoặc F4, mở store bằng biến ở A3 | Dùng context sạch |
| F6 | Order | Add to cart từ F5 rồi checkout | Bogus gateway, hiển thị "Credit card": thẻ `1` thành công, `2` fail, `3` exception |
| F7 | Asset | Category, item, font, ảnh trong trang Assets | Tạo layer-image dồn dập có thể bị 429 |
| F8 | Global Option | `/global-options/create` | Bật Show in cart nếu cần thấy ở cart |
| F9 | Hai tenant | `TIB_USER_A_*`, `TIB_USER_B_*` | |

## B3. Route và API

| Menu | Route |
|---|---|
| Campaigns | `/campaigns`, `/platform-products` |
| Product Base, Artworks | `/products`, `/artworks` |
| Assets | `/cliparts`, `/vectors`, `/fonts`, `/global-options` |
| Dynamic Translations | `/artwork-translations` |
| Store Settings | `/general-settings`, `/product-page-settings`, `/product-page-content` |
| Trash, Activity logs | `/trash`, `/activity-logs` |

`/settings` trả 404. Sau login portal luôn về `/`, phải tự mở lại trang đích.

| Mục đích | Request |
|---|---|
| User hiện tại, instance | `GET /api/user`, `GET /api/instances` |
| GraphQL portal | `POST /api/graphql`, id kiểu `bigint` |
| Đọc artwork | GraphQL `artworks_by_pk`. `GET /api/artworks/<id>` trả 405 |
| Config campaign công khai | `GET /api/merchant/campaigns/<shopifyProductId>.json?shop=<shop>` |
| Lưu customization | `POST /api/merchant/shopify/customization?shop=<shop>&id=<productId>` |
| Đọc customization | `GET /api/merchant/shopify/customization/<uuid>?shop=<shop>` |
| Shopify product id | Storefront `/products/<handle>.js` |

Gọi thẳng `staging-graphql.teeinblue.com` trả "Invalid response from authorization hook". Request analytics và chat widget là nhiễu.

## B4. Giới hạn tool

| Tool | Giới hạn | Cách xử lý |
|---|---|---|
| Staging MCP, tạo Global Option | Không có `show_in_cart`; type `text` có lúc lỗi `top/left/width required` | Tạo bằng Portal hoặc `POST /api/global-options` |
| Staging MCP, tạo GO và layer | Không áp `default_layer_value` của user | Expected là payload truyền vào. Case phụ thuộc default thì tạo bằng Portal |
| Staging MCP, condition | `dependency.dependencies[].value` phải đúng kiểu id, sai kiểu vẫn nhận nhưng storefront không match | Lấy id từ `clipart_categories[].options[].id` của campaign JSON |
| Shopify MCP | Không tạo collection, không publish Online Store; `get-orders` chỉ trả order cũ nhất | Làm qua Shopify admin |
| Playwright headless | Timing mạng sai | Chạy headed |

## B5. Thao tác UI

| Dấu hiệu | Cách xử lý |
|---|---|
| Đã sửa mà storefront vẫn cũ | `app-v1.js` không có hash, cache rất lâu. So bundle trang đang chạy với `fetch(url, {cache:'no-store'})` |
| Field storefront có sẵn giá trị cũ, gõ bị nối | SDK khôi phục từ localStorage. Dùng context sạch |
| Storefront 404 dù campaign by Shopify đã publish | Shopify product chưa bật Online Store |
| Theme editor, checkout editor không có data teeinblue | Chỉ là placeholder. Verify bằng storefront thật |
| Dialog Confirm password không hiện | Có hiệu lực 15 phút sau lần xác nhận trước |
| Race condition chỉ thấy với `dispatchEvent` liền `blur` | Có thể là artifact của automation. Đo ngưỡng, chạy lại bằng thao tác thật |
| Sau `Save` không có lỗi console | Đọc toast: cách duy nhất biết validate fail ở artwork editor |
| Mất layer chưa lưu | Session hết hạn im lặng. Save từng chặng |
| Trang "Verify you are human" trên storefront | Bot protection của Shopify. Nghỉ vài phút, dùng browser đã vào được |
| Sidebar collapse, label có icon | Chờ `attached`, match theo `href` |
| Click chữ của toggle không ăn | Toggle là `label.vue-js-switch` |

| Điểm | SDK v1 | SDK v2 |
|---|---|---|
| Nút add to cart | `#teeAtcButton` | Nút của theme |
| Endpoint cart | `/cart/add.js` (JSON) | `/cart/add` (FormData) |
| Auto chọn template | Có | Không, phải chọn tay |

## B6. Kết luận check

| Tình huống | Kết luận |
|---|---|
| `status: READY`, khớp `expected_result` | `PASS` |
| `status: READY`, oracle `STRONG`, lệch | `FAIL`, sau khi loại trừ A5 và B5 |
| `status: READY`, oracle `BASELINE`, lệch | `SUSPECTED_FAIL`, đối chiếu PO/Dev |
| `status: NEEDS_CONFIRMATION`, oracle `NONE`, hoặc item `UNRESOLVED` | Chỉ ghi `OBSERVED: <hành vi thật>` |
| `environment_differences` có `NOT_TESTABLE` | `NOT_APPLICABLE` trên môi trường đó |
| Không quan sát được, thiếu quyền, thiếu data | `NOT_COVERED` hoặc `BLOCKED`, nêu rõ thiếu gì |

Hành vi thật khác knowledge, hoặc đã xác nhận một Open Question: gửi CCR (`how-to-request/consumer-guide.md` §5). Bug thật: báo trên Testlane theo quy trình của team.
<!-- PART-B:end -->
