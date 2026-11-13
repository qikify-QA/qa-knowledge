# Product guide — Qikify Volume Discounts

Bản đồ của product: có gì, ở đâu, test được không. Mọi bước đều đọc file này. Tối đa 10 KB. Định nghĩa: contract §5c.

- Đúng phải là gì: `<object>/features/<feature>/kb.json`, `checklists/`.
- Làm thế nào: `_flows/` (chưa có file nào; thêm qua khối C của CCR khi có cách thao tác đã verify).
- Biến env: `_env.example` (tên biến `QVL_*`).

Không dùng guide làm expected result. Không ghi giá trị credential, id, tên store.

## 1. Product
Qikify Volume Discounts (QVL trên Testlane, QVD trên Jira) là Shopify app giảm giá theo số lượng. Mỗi offer là một automatic app discount của Shopify. Ba loại offer chính hay stack/conflict với nhau: Quantity Break, Multibuy (Mix & Match Combo), Wholesale Pricing.

Luồng chính: merchant chọn template ở Create offer → cấu hình trigger, tier, giao diện, lịch → lưu thành discount Shopify → buyer thấy widget trên PDP/collection → thêm vào cart và nhận discount.

Custom CSS là shared setting của cả ba loại, không phải một loại offer.

## 2. Object
Từ khoá ticket sang object: `_registry.json`. Feature của object: `<object>/feature-summary.md`. Không liệt kê feature key ở đây.

| Object | Phạm vi | Không thuộc |
|---|---|---|
| `discount-offers` | Phần chung của mọi offer: form tạo/quản lý, Custom CSS, overlap/stacking giữa các loại, event analytics và hiển thị storefront | Luật riêng của một loại offer |
| `quantity-break` | Tier theo số lượng, quà tặng, subscription, hiển thị, lịch, storefront/cart | Luật chung của offer |
| `multibuy` | Combo Mix & Match: tính discount, chọn sản phẩm, giao diện, lịch | Luật chung của offer |
| `wholesale-pricing` | Bảng giá B2B theo tier min/max, giao diện, composer storefront | Luật chung của offer |
| `onboarding-dashboard` | Onboarding và dashboard của app | Analytics chi tiết |
| `ai-offer-creation` | Tạo offer bằng AI | Form tạo offer thủ công |
| `variant-swatches` | Variant swatch trên storefront | Widget offer |
| `translate-offers` | Dịch nội dung offer cho buyer | Dịch Portal |
| `translate-portal` | Dịch giao diện Portal merchant | Dịch offer |
| `analytics` | Số liệu offer cho merchant | Event ghi từ storefront (`discount-offers`) |
| `ask-for-review` | Modal xin đánh giá trong app | Luồng offer |

## 3. Môi trường
Chỉ test trên staging; production là điểm dừng. Iframe app còn tải từ một host embedded staging ngoài `expected_api_base` (đã được operator xác nhận).

| Biến | Đặc điểm | Dùng cho | Không dùng cho |
|---|---|---|---|
| `QVL_SHOPIFY_ADMIN_APP_URL` | URL app nhúng trong Shopify admin | Portal merchant | Storefront |
| `QVL_API_BASE` | Host API staging | Gọi API, event | Production |
| `QVL_STORE_HANDLE`, `QVL_STORE_DOMAIN` | Store test | Mọi test storefront | Store khác |
| `QVL_STOREFRONT_PASSWORD` | Mật khẩu storefront | Vào storefront bị khoá | Đăng nhập admin |

Không có email/password Shopify admin trong env: session do operator bàn giao. Tiền tố `QVL_` độc lập với biến của repo automation khác.

## 4. Test được gì
Chưa có dòng `environment_differences`. Thứ tự ưu tiên khi hai offer cùng qualify một cart còn là câu hỏi mở (NEEDS_CONFIRMATION): đừng chốt expected, gắn `expected-unconfirmed`. Một số file nguồn còn skeleton, nên phần môi trường và test data chưa có claim.

Việc cần người hỗ trợ: bàn giao session Shopify admin, dựng offer chồng trigger để test overlap.

## 5. Bẫy làm sai kết luận
| Dấu hiệu | Cách hiểu |
|---|---|
| Hai offer cùng trigger | Đúng một discount thắng, không cộng, không chia |
| Test 3-way overlap (qty=3) | Không phải test priority sạch, đừng suy ai thắng |
| Variant Swatches lộ text thô ở storefront | Known defect (QVD-28) |
| 11 đơn vị thêm trực tiếp tách 2 line | Shopify tách line theo từng mã, không phải lỗi tính |
| Request `/api/completions/review` trả 500 mỗi lần mở form | Quan sát trên staging, ghi nhận, không chặn thao tác |

## 6. Mutation guard
Chỉ thao tác hoàn tác được trên staging, không production. Tạo offer có tên tiền tố QA và xoá sau khi test (offer tạo discount thật trên Shopify store). Không nhập dữ liệu khách thật. Che token và session khi ghi log.
