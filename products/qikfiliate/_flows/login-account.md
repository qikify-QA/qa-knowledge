# Login, phiên, xác minh account

## Dashboard

- `POST /api/login` trả JWT `access_token`, kèm `expires_in`. `POST /api/refresh` cấp token mới.
- Mọi request phải có `Accept: application/json`, thiếu thì bị 302 về `#/login` `[RG]`.
- Email phân biệt hoa thường khi login `[RG]`: copy đúng giá trị trong env.
- Selector ngôn ngữ chỉ có ở trang login `[RG]`.

## Admin

Agent không tự login. QA đăng nhập trong profile browser riêng rồi bàn giao session, hoặc tự làm phần admin theo hướng dẫn `[RG]`.

## Xác minh account

Bước đầu tiên, và sau mỗi lần login lại:

1. Host đang mở đúng `KOIN_DASHBOARD_URL`.
2. `GET /api/user` trả `data.email` đúng biến env của account đang dùng `[RG]`. Sai thì dừng, `BLOCKED`.
3. Với admin: tài khoản ở Profile đúng tài khoản QA bàn giao.
