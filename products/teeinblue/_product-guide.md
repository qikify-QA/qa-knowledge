# Product guide — teeinblue

Bản đồ của product: có gì, ở đâu, test được không. Mọi bước đều đọc file này.

- Đúng phải là gì: `<object>/features/<feature>/kb.json`, `checklists/`.
- Làm thế nào: `_flows/`, đọc `_flows/README.md` rồi đúng file theo chủ đề.
- Biến env: `_env.example`.

Không dùng guide làm expected result. Không ghi giá trị credential, id, tên store.

## 1. Product

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

## 2. Object và feature

Từ khoá ticket sang object: `_registry.json`. Feature của object: `<object>/feature-summary.md`. Trạng thái, version, oracle: `manifest.json`. Mỗi feature có `features/<key>/profile.json` (entry point, precondition, `environment_differences`) và `checklists/<key>.json`.

| Object | Phạm vi | Không thuộc |
|---|---|---|
| `campaign` | Tạo, duyệt, xoá campaign, đồng bộ media Shopify | Phía storefront (`sdk`) |
| `product-base` | Print area, variant, mockup, vòng đời, liên kết campaign | Thư viện ảnh mockup (`image-library`) |
| `artwork` | Editor, layer, config, condition, populate, render | Form buyer trên storefront (`sdk`) |
| `asset-category` | 6 loại category: Clipart, Vector, Color, Additional Option, Map Style, Font Category | Font (`font`) |
| `font` | `/fonts` | Font category (`asset-category`) |
| `image-library` | Thư viện ảnh của Image layer và Mockup layer, không có trang riêng | Clipart (`asset-category`) |
| `global-option` | Option dùng chung nhiều campaign |  |
| `translation` | Dynamic Translations, Product Page Content, chọn ngôn ngữ |  |
| `order` | Đặt order, review, fulfillment |  |
| `sdk` | Runtime personalization của buyer, Product Page Settings, cài đặt model GenAI, open platform |  |
| `account-security` | Login portal, trạng thái bảo mật staff, thao tác nhạy cảm | Quyền riêng của campaign (`campaign`) |
| `open-api` | API token: `/openapi/v1` (asset), `/api/open` (publish campaign) | Route `/api` của portal |
| `subscription` | Plan, pricing (plan cũ, gói Blue theo order item), chữ hiển thị plan/tier, usage, quota theo chu kỳ | Webhook billing (`account-security`), thanh toán thật |
| `third-party-services` | Extras > 3rd-party Services: dịch vụ xoá nền, API key provider (`private_config` cấp account) | Chạy effect và warning thiếu key (`artwork`), upload của buyer (`sdk`) |
| `mcp` | MCP server: endpoint `{TIB_API_BASE}/mcp`, Bearer token `mcp:access`, trang `/mcp`, nhóm tool (artwork, upload layer image) | Upload layer image trên portal (`image-library`), Open API (`open-api`) |
| `store-settings` | General Settings của store (`/general-settings`), gồm Order storage time (`expired_time`) | Product Page Settings (`sdk`), 3rd-party Services, plan (`subscription`) |

Ticket không khớp key nào: ghi knowledge gap, đề xuất key mới trong CCR.

## 3. Môi trường

Thấy host production thì dừng: `portal.teeinblue.com`, `api.teeinblue.com`, `portal-api.teeinblue.com`, `sdk.teeinblue.com`, `customize.teeinblue.com`, `photo-api.teeinblue.com`.

| Biến | Đặc điểm | Dùng cho | Không dùng cho |
|---|---|---|---|
| `TIB_STORE_URL`, `TIB_STORE_INSTANCE_ID` | Dev store, non-Plus | Mặc định: portal, storefront, Thank You, Order status | App block trên Checkout page, Generate test design |
| `TIB_SDK_V2`, `TIB_SDK_V2_INSTANCE_ID` | Shopify Plus | App block trên Checkout page, storefront SDK v2 | |
| `TIB_BOUNDLESS_*`, `TIB_BOUNDLESS_INSTANCE_ID` | Boundless, không có storefront thật | Case Boundless trên portal | Campaign by Shopify; chạy song song với store mặc định (chung account) |
| `TIB_BOUNDLESS_STOREFRONT_INSTANCE_ID` | Storefront Boundless | Case Boundless cần storefront | Tạo data mới |
| `TIB_ONBOARDING_*` | Chưa connect fulfillment | Luồng onboarding | Chỉ đọc, giữ sạch |
| `TIB_USER_A_*`, `TIB_USER_B_*` | Hai tenant | Permission, cross-tenant | Thiếu biến thì `NOT_COVERED`, không thay account khác |
| `TIB_STAFF_VIEW_ONLY*`, `TIB_STAFF_GEN_ONLY*` | Staff quyền hạn chế | Phân quyền | |
| `TIB_FULL_ACCESS_TOKEN` | Token Open API | Route `/openapi/v1` | `GET /api/user` (401) |

## 4. Test được gì

**Nhãn test case:** không test được cả case là `env-blocked`: không execute, Testlane `skipped` kèm lý do, verdict `NOT_APPLICABLE`. Không test được một vế: giữ case, ghi "vế X: skip — <lý do>", kết luận theo các vế còn lại.

| Hạng mục | Feature | `type` | Mức |
|---|---|---|---|
| Generate test design trên dev store | `campaign/create-campaign-by-product-base` | `ALTERNATIVE_SETUP` | Vế |
| Horizon (job failed, queued) | Nhiều feature | `NOT_TESTABLE` | Vế |
| Strava trong Route Maps | `artwork/layer-config-maps-astronomy` `sdk/storefront-buyer-facing` | `NOT_TESTABLE` | Vế |
| Tracking từ provider | `order/review-and-initiate-fulfillment-portal` | `NOT_TESTABLE` | Case |
| Size gốc của provider | `product-base/printarea-definition` | `NOT_TESTABLE` | Vế |
| `photo_endpoint=snap` | `sdk/storefront-buyer-facing` | `DIFFERENT_VALUE` | Case hoặc vế |
| Upload CORS, preconnect tới host production | `sdk/storefront-buyer-facing` | `NOT_TESTABLE` | Vế |
| Network timing | `sdk/storefront-buyer-facing` | `ALTERNATIVE_SETUP` | Vế |
| Browser chặn site data, ITP | `sdk/storefront-buyer-facing` | `ALTERNATIVE_SETUP` | Vế |
| Outage Nano Banana 2.1 | `sdk/genai-personalization-runtime` | `ALTERNATIVE_SETUP` | Vế |
| Gửi item CustomCat | `order/fulfillment-provider-request` | `ALTERNATIVE_SETUP` | Vế |
| Advanced options PB Gelato | `product-base/provider-required-options` | `DIFFERENT_VALUE` | Vế |
| Accelerated checkout (Shop Pay, PayPal, Apple Pay, Google Pay) | `sdk/required-addon-validation` | `NOT_TESTABLE` | Vế |
| App chiếm nút add to cart (race với autofixer) | `sdk/cart-addon-autofixer` | `ALTERNATIVE_SETUP` | Case |
| Rate limit route games (preview game text) | `sdk/game-text-preview-render` | `DIFFERENT_VALUE` | Vế |
| Retry window job image-effect (upload kẹt khi worker crash) | `sdk/photo-genai-image-filter-runtime` | `NOT_TESTABLE` | Vế |
| Copy artwork sang account khác | `artwork/artwork-cross-store-clone` | `ALTERNATIVE_SETUP` | Vế |
| Google consent screen Testing | `account-security/social-login` | `ALTERNATIVE_SETUP` | Case |
| Rate limit Google login | `account-security/social-login` | `DIFFERENT_VALUE` | Vế |
| Job cleanup `trashed_images` (đêm 01:00) | `campaign/mockup-preview-render-lifecycle` | `ALTERNATIVE_SETUP` | Vế |
| Order test Bogus được đếm tier usage | `subscription/tier-usage-metering` | `DIFFERENT_VALUE` | Case |
| Remove.BG sau mốc shutdown (ẩn provider, migration seller) | `third-party-services/remove-background-provider` | `ALTERNATIVE_SETUP` | Vế |

Cách xử lý từng khác biệt (`how_to_test`) chỉ nằm ở `environment_differences` trong `profile.json` của feature (contract §5b). Horizon không thuộc một feature nào: bỏ vế Horizon, verify UI và API.

**Cần người hỗ trợ:**

- Bảng nội bộ không lộ qua GraphQL: agent soạn query read-only, người có quyền chạy.
- Job theo lịch: nhờ Dev chạy command trên staging, không chờ tới giờ.
- Config server (provider key, branch, migration): là điều kiện tiên quyết cho Dev.

## 5. Bẫy làm sai kết luận

| Dấu hiệu | Cách hiểu |
|---|---|
| Toggle mặc định khác mong đợi | Mặc định theo config shop (`default_value`). Đọc config trước khi báo bug |
| `ERR_FAILED` kèm lỗi CORS khi body có `<script` hoặc `onload=` | WAF chặn. Không suy ra app an toàn |
| Ngưỡng rate limit khác ticket | Staging cố ý đặt nhỏ hơn. Tin header `x-ratelimit-limit` |
| Link Edit Customization trên staging 404 | Link luôn trỏ customize production. Đổi host sang customize staging, giữ nguyên query |
| Upload qua Playwright lọt `accept` | Tool bypass, merchant thật bị chặn ở FE. Không log bug |
| Theme editor, checkout editor không có data teeinblue | Chỉ là placeholder. Verify bằng storefront thật |
| Storefront vẫn cũ sau khi sửa | Cache `app-v1.js` hoặc `translation_version`, localStorage. Cách xử lý: `_flows/environment.md` |

## 6. Mutation guard

- **Production chỉ đọc**, trừ khi operator giao đúng việc đó.
- Data tạo cho một ticket đặt tên theo title ticket và giữ lại sau test. Không sửa data có sẵn của người khác.
- Thay đổi tạm (config store, throttle, route) phải trả về giá trị cũ sau khi test.
- Order chỉ đặt bằng thanh toán test.
- Evidence phải che token: `GET /api/instances/<id>` và một số response trả kèm `token`, API key.
