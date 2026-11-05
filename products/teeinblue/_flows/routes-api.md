# Route và API

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
