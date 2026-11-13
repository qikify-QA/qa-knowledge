# Product guide — Mysbox

Bản đồ của product: có gì, ở đâu, test được không. Mọi bước đều đọc file này. Tối đa 10 KB. Định nghĩa: contract §5c.

- Đúng phải là gì: `<object>/features/<feature>/kb.json`, `checklists/`.
- Làm thế nào: `_flows/` (chưa có file nào; thêm qua khối C của CCR khi có cách thao tác đã verify).
- Biến env: `_env.example` (tên biến `MYS_*`).

Không dùng guide làm expected result. Không ghi giá trị credential, id, tên store.

## 1. Product
Mysbox là Shopify app bán mystery box. Merchant biến một variant Shopify thành "box", khai phần thưởng và xác suất rồi publish. Khách mua như hàng thường; phần thưởng **được bốc thăm khi webhook `orders/paid` về server**, không phải lúc bấm mở.

Luồng chính: tạo và publish box → khách mua → webhook paid, bốc thăm, chốt quà (QUEUED/COMPLETED/FAILED) → khách reveal (trang cảm ơn, order status, app proxy, magic link) → hết cửa sổ resell thì quà được thêm vào đơn Shopify dưới dạng dòng giá 0.

Thuật ngữ: "User" trong code = SHOP; khách cuối = Customer; draw/pull ≠ unbox/reveal; **redeem** (khách tự mở) ≠ **unbox** (merchant/job/Flow mở, bỏ qua cửa sổ resell). Box Digital (reveal trên web) khác Physical (sealed, ghi metafield đơn). Test order mặc định bị loại khỏi hạn mức, billing, analytics.

## 2. Object
Từ khoá ticket sang object: `_registry.json`. Feature của object: `<object>/feature-summary.md`. Không liệt kê feature key ở đây.

| Object | Phạm vi | Không thuộc |
|---|---|---|
| `box` | Box, loại Single/Bundle/Group-Tier, phần thưởng, xác suất, tạo/publish/xoá, version bất biến, quản lý box ở admin | Tồn kho/pool (`box-inventory`) |
| `box-inventory` | Tồn kho, picking mode, pool refill | Cấu hình phần thưởng (`box`) |
| `order-draw` | Webhook paid, order và opening request, chốt quà, trạng thái đơn, quà vào đơn Shopify, Digital vs Physical, retry đơn ở admin | Refund (`resell-refund-credit`) |
| `reveal` | Khách mở box, đăng nhập/magic link, merchant unbox, auto-unbox | Bốc thăm (`order-draw`) |
| `resell-refund-credit` | Resell box/items, số tiền hoàn, store credit Koin, ticket, huỷ/refund từ Shopify | Bốc thăm |
| `shop` | Vòng đời shop: cài đặt, onboarding, kết nối/re-auth, gỡ/cài lại, kill switch, GDPR, quản lý shop ở admin | Cấu hình storefront (`shop-settings`) |
| `shop-settings` | General settings, theme embed, custom code, bản dịch widget, đồng bộ dữ liệu storefront | Vòng đời shop (`shop`) |
| `analytics` | Dashboard merchant, báo cáo và export nền tảng | Phí usage (`usage-billing`) |
| `unbox-sharing` | Chia sẻ unboxing, feed recent pulls | Reveal |
| `notification` | Email hệ thống, banner thông báo dashboard | Flow trigger (`integrations`) |
| `plan` | Gói, capacity theo chu kỳ 30 ngày, nâng/hạ/huỷ, catalog plan | Phí vượt hạn mức (`usage-billing`) |
| `usage-billing` | Usage fee, charge hằng ngày gộp một Shopify usage charge, giới hạn capacity | Gói (`plan`) |
| `promo-code` | Promote code (thêm hạn mức) và billing discount (giảm giá/trial); hai thứ này khác nhau | Plan |
| `integrations` | Xác thực từng kênh API (portal nhúng, extension, Flow), webhook Shopify/EventBridge, Shopify Flow action/trigger, đồng bộ BigQuery, affiliate tracking | Logic nghiệp vụ của webhook |
| `admin-ops` | Back-office nội bộ: đăng nhập/quyền, activity log, job và queue, release portal | Thao tác admin lên shop/box/đơn (nằm ở object entity) |

## 3. Môi trường
Chỉ test trên staging; production là điểm dừng (`environments.forbidden`). Admin panel nội bộ (Filament) chỉ đăng nhập qua Slack, không nằm trong phạm vi explore.

| Biến | Đặc điểm | Dùng cho | Không dùng cho |
|---|---|---|---|
| `MYS_SHOPIFY_ADMIN_APP_URL` | URL app nhúng trong Shopify admin | Portal merchant | Storefront |
| `MYS_API_BASE` | Host API staging (có thêm host api và proxy khác) | Gọi API | Production |
| `MYS_STORE_HANDLE`, `MYS_STORE_DOMAIN` | Store test | Mọi test storefront | Store khác |
| `MYS_STOREFRONT_PASSWORD` | Mật khẩu storefront | Vào storefront bị khoá | Đăng nhập admin |
| `MYS_TEST_BUYER_EMAIL` | Hộp thư QA nhận email đơn test và magic link | Reveal, email | Khách thật |

Không có email/password Shopify admin trong env: session do operator bàn giao.

## 4. Test được gì
Store staging đang gói Free nên Analytics, Content & Translation và buyback bị khoá. Resell/buyback là `env-blocked` cho tới khi đổi gói. Tính năng gắn `[chỉ có trên staging]` (share unboxing, banner, ...) chỉ quan sát được trên staging, không chứng minh hành vi production. Chưa có dòng `environment_differences` nào.

Việc cần người hỗ trợ: bàn giao session Shopify admin, đổi gói store, bật Koin/box digital có "Buy back function".

## 5. Bẫy làm sai kết luận
| Dấu hiệu | Cách hiểu |
|---|---|
| Bấm mở box mà không thấy bốc thăm | Bốc thăm xảy ra ở webhook paid, không ở lúc mở |
| Số liệu analytics/billing thiếu đơn test | Test order mặc định bị loại |
| Seed Free 10 box/kỳ | Giá trị seed, không phải số production |
| Quà chưa vào đơn Shopify | Chờ mọi box mở xong và hết cửa sổ resell (mặc định 24h) |

## 6. Mutation guard
`mutation_policy = SAFE_REVERSIBLE_ONLY`: chỉ thao tác hoàn tác được trên staging, không production. Đặt tên box/data có tiền tố QA. Không đổi gói/billing thật. Thanh toán chỉ qua test order. Che token và session khi ghi log.
