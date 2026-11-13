# Product guide — Duos B2B

Bản đồ của product: có gì, ở đâu, test được không. Mọi bước đều đọc file này. Tối đa 10 KB. Định nghĩa: contract §5c.

- Đúng phải là gì: `<object>/features/<feature>/kb.json`, `checklists/`.
- Làm thế nào: `_flows/` (chưa có file nào; thêm qua khối C của CCR khi có cách thao tác đã verify).
- Biến env: chưa có `_env.example` (product chưa có môi trường explore).

Không dùng guide làm expected result. Không ghi giá trị credential, id, tên store.

## 1. Product
Duos B2B là Shopify app đưa merchant từ B2C sang B2B trên Shopify B2B (Company, Company Location, catalog, payment term) và Customer Account extension. Từ 04/2026 chạy mọi plan Shopify; chỉ 2 tính năng chặn checkout cần Plus.

Luồng chính: buyer đăng ký B2B qua form → merchant duyệt submission (hoặc store bật tự tạo company) → company có member và role → buyer đặt hàng qua quote, quick order, shopping list, trong hạn mức credit của location → email thông báo theo sự kiện.

Giá theo module (modular pricing); nhiều hành vi bật theo `users.config` của từng merchant và không có UI. "Module" = gói tính năng được bán riêng.

## 2. Object
Từ khoá ticket sang object: `_registry.json`. Feature của object: `<object>/feature-summary.md`. Không liệt kê feature key ở đây.

| Object | Phạm vi | Không thuộc |
|---|---|---|
| `roles-permissions` | Role Duos mặc định/custom, ánh xạ contact role Shopify, gán/đổi role, Flow action assign role, chặn checkout theo quyền | Màn member trong Customer Account (`company-member`) |
| `company-member` | Trang quản lý member của company location: xem, mời, sửa, xoá, tìm/lọc | Định nghĩa role (`roles-permissions`) |
| `b2b-registration` | Form builder, form đăng ký storefront, regex field, reCAPTCHA, rate limit, EU VAT | Duyệt submission (`company-submissions`) |
| `company-submissions` | Duyệt submission, khớp customer có sẵn, tạo company (Approve hoặc tạo tự động) | Cấu hình form (`b2b-registration`) |
| `quote-request` | Yêu cầu báo giá, thương lượng, áp giá theo line item, PDF, lịch sử | Credit/payment term (`finance-credit`) |
| `quick-order` | Đặt nhanh theo SKU/CSV, hành động sau khi tạo order, tải catalog | Shopping list |
| `shopping-list` | List đã lưu, gửi duyệt/duyệt, re-approval, list do merchant quản lý, reorder reminder | Quick order |
| `finance-credit` | Credit limit theo location, ledger, validate credit ở checkout/draft order | Giá và gói (`pricing-subscription`) |
| `notifications` | Email merchant/buyer theo sự kiện, template, sender/reply-to, Flow trigger email | Nội dung email của luồng nghiệp vụ khác |
| `pricing-subscription` | Modular pricing, tier theo plan Shopify, trang Subscription, trial, banner giữ giá cũ, khoá theo module | Credit của buyer (`finance-credit`) |
| `auth-token` | Offline token expiring/legacy, phát hiện token chết, reconnect, refresh/migrate, uninstall/reinstall | Home, điều hướng (`portal-shell`) |
| `portal-shell` | Home/onboarding, điều hướng Portal, nội dung và dịch, banner DTC, admin panel nội bộ | Token (`auth-token`) |

## 3. Môi trường
Chưa có môi trường explore cho product này (`explore_enabled: false`): context chỉ đến từ tài liệu (dev doc, QA tự biên soạn, business rule), chưa có quan sát runtime do pipeline thực hiện. Chưa có biến env nào được khai. Mọi claim mang `scope.environment: documented`.

## 4. Test được gì
Chưa có khác biệt môi trường nào được ghi (`environment_differences` trống ở mọi feature). Khi test trên môi trường thật mà thấy khác tài liệu thì báo qua CCR, không sửa expected theo cảm tính.

Nhãn test case: `expected-unconfirmed` cho mọi mục còn conflict/NEEDS_CONFIRMATION (Reject submission, khoá sửa email/phone, U&P miễn phí hay trả phí, bundle/trial Oct 2026). Việc cần người hỗ trợ: store có Plus (2 tính năng chặn checkout), buyer Customer Account, cờ `users.config` do dev bật.

## 5. Bẫy làm sai kết luận
| Dấu hiệu | Cách hiểu |
|---|---|
| Hành vi không có nút bật trong Portal | Có thể là cờ `users.config`, không phải lỗi |
| Dòng "Lệch staging" trong tài liệu nguồn | Tài liệu và staging khác nhau; giữ conflict, không chọn bên |
| Tính năng bị khoá khi chưa mua module | Hành vi theo gói, không phải bug |
| Reject submission | Chưa rõ có tồn tại hay không, xem OQ của `company-submissions` |

## 6. Mutation guard
Chưa có môi trường explore nên chưa có quy tắc riêng. Khi test thật: không dùng production, đặt tên data có tiền tố QA, không đổi cờ `users.config` của merchant thật, che token Shopify trong log.
