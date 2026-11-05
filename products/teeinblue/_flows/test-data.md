# Dựng test data

Login theo `login-instance.md` trước. Mỗi fixture ghi lại id.

| Mã | Fixture | Cách dựng | Lưu ý |
|---|---|---|---|
| F0 | Session | Login theo `login-instance.md` | Bắt buộc cho mọi fixture |
| F1 | Product base | `/products/new`, thêm print area, variant, mockup | Có thể duplicate thay vì tạo mới |
| F2 | Artwork | `/artworks`, thêm layer cần test, Save từng chặng | `Save & Close` chỉ tạo artwork, chưa gắn vào print area |
| F3 | Campaign by Product Base | `/campaigns/new`, add F1, gắn F2 vào print area | |
| F4 | Campaign by Shopify | `/platform-products/new`, chọn Shopify product, connect variant | Product phải bật Online Store |
| F5 | Storefront | Publish F3 hoặc F4, mở store theo guide mục 3 | Dùng context sạch |
| F6 | Order | Add to cart từ F5 rồi checkout | Bogus gateway, hiển thị "Credit card": thẻ `1` thành công, `2` fail, `3` exception |
| F7 | Asset | Category, item, font, ảnh trong trang Assets | Tạo layer-image dồn dập có thể bị 429 |
| F8 | Global Option | `/global-options/create` | Bật Show in cart nếu cần thấy ở cart |
| F9 | Hai tenant | `TIB_USER_A_*`, `TIB_USER_B_*` | |
