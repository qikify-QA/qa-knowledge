# Login, instance, store switcher, endpoint chung

## Endpoint đã quan sát (network log)

| Mục đích | Request |
|---|---|
| Login | `POST https://staging-api.teeinblue.com/api/login` (401 khi fail) |
| Lấy token (cũ) | `POST https://staging-api.teeinblue.com/api/token` |
| Thông tin user | `GET https://staging-api.teeinblue.com/api/user` |
| Danh sách instance (store) | `GET https://staging-api.teeinblue.com/api/instances` |
| Instance active | `GET /api/instances/<id>/popup-messages` (bắn sau login) |
| GraphQL portal | `POST https://staging-api.teeinblue.com/api/graphql` (cookie + header `X-XSRF-TOKEN`); relay: `POST /api/graphql/relay` |
| GraphQL cũ (list campaign, aggregate) | `POST https://staging-graphql.teeinblue.com/v1/graphql` — gọi thẳng từ browser trả `Invalid response from authorization hook` |
| Trash | `GET https://staging-api.teeinblue.com/api/trash?cursor=&per_page=20&sort=deleted_at&sort_type=desc` |
| Activity log | `GET https://staging-api.teeinblue.com/api/staff-activity-logs` |
| Đổi user/store | `POST /api/users/<userId>/login` (vd 64 = <org của TIB_USER_A>, 117 = <org Boundless>) |

`GET /api/artworks/<id>` trả **405**. Đọc artwork bằng GraphQL `artworks_by_pk(id){ templates }` hoặc merchant API công khai (xem `storefront-sdk.md`).
`GET /api/instances/<id>` trả cả `token`/`crisp_token` — đừng in ra output.

## Các trang chính

| Trang | URL |
|---|---|
| Campaigns by Product Base | `https://staging-portal.teeinblue.com/campaigns` |
| Campaigns (filter theo tên) | `https://staging-portal.teeinblue.com/campaigns?limit=20&name=<keyword>` |
| Campaigns by Shopify Products | `/platform-products` (mới: `/platform-products/new`) |
| Product Base | `/products` |
| Artworks | `/artworks` |
| Trash | `/trash` |
| Activity logs | `/activity-logs` |
| Global Options | `/global-options` (Assets) |
| Dynamic Translations | `/artwork-translations` (Extras) |
| General settings | `/general-settings` |
| Product Page Settings / Content | `/product-page-settings`, `/product-page-content` |

`/settings` là 404.

## Login (đã verify từ 2026-08-23)

Portal có 2 kiểu login:

| Kiểu | URL | Dùng cho |
|---|---|---|
| Shopify owner | `/login` | Nhập store domain → `Log in` |
| Teeinblue account (staff) | `/login?staff=true` | Email + password → `Log in` |

Agent dùng **`/login?staff=true`** (`.env` là email/password).

1. Navigate `https://staging-portal.teeinblue.com/campaigns` → chưa có session sẽ về `/login` (kiểu Shopify domain).
2. Navigate `https://staging-portal.teeinblue.com/login?staff=true`.
3. Điền textbox `Your email` (label `Enter your email *`) và `Your password` (label `Enter your password *`).
4. Click `Log in`.
5. Verify: URL rời `/login`, snapshot thấy dữ liệu.

- Lỗi hiện dạng text ngay dưới form (vd `Email address is not verified`). Đọc cả snapshot lẫn network để phân biệt sai password vs account chưa verify.
- Trang login có **Cloudflare Turnstile**. Nếu thành interactive challenge thì dừng, báo người dùng login tay.
- Account: `TIB_STAGING_EMAIL` (`.env`) → login OK (user `<org của TIB_USER_A>`, id `TIB_USER_A`). account phụ dạng `+auto` của cùng email chưa verify email → đừng dùng.
- Sau login portal về `/` (Home), không giữ trang đích. Tự navigate lại.
- SPA load chậm: sau navigate luôn `browser_wait_for` `textGone: "Initializing..."`. Trang Dynamic Translations có khi cần ~8s.
- Auth staging là Sanctum session (cookie). Request API tự gọi cần `credentials:'include'` + `X-XSRF-TOKEN` lấy từ cookie.

### 2FA
- 2026-10-27 portal từng bắt 2FA sau email/password (`/login/two-factor`). Người dùng đã tắt 2026-10-28; login lại `POST /api/login` 200 không hỏi mã.
- Nếu 2FA bật lại: agent không có TOTP/inbox → nhờ người dùng nhập mã trong browser Playwright rồi chạy tiếp.

### Continue with Google (staff login)
- Nút chỉ có ở `/login?staff=true` (href `<TIB_API_BASE>/api/auth/google/redirect`), không có ở `/login` (store domain) và `/register`.
- `GET /api/auth/google/redirect` → 302 tới `accounts.google.com` (scope `openid profile email`, `redirect_uri` là `<TIB_API_BASE>/api/auth/google/callback`).
- Google sign-in cần người dùng thao tác tay trong browser: env không có credential Google. Gmail dùng để test phải được Dev thêm làm test user của consent screen trước.
- Màn "Choose an account" của Google không có nút Cancel. Muốn test Cancel: chọn account rồi bấm Cancel ở màn consent.
- Kiểm toast của từng mã từ chối không cần qua Google: mở thẳng `/login?social_error=<no_account|invite_pending|email_unverified|oauth_failed>` (hiện view email/password + toast `.vue-notification`).
- Query có thẻ HTML gây nguy hiểm (kiểu `<img onerror>`) bị Cloudflare chặn 403 trước khi tới portal. Muốn kiểm portal có render HTML trong `social_error` không thì dùng thẻ vô hại đã URL-encode (vd `%3Cb%3Ex%3C%2Fb%3E`).
- Một lần Google login = 2 request vào bucket rate limit (redirect + callback). Test rate limit thì chạy cuối: sẽ khoá Google login của cả IP tới khi hết `retry-after`.

## Instance / store đang active

- Account `TIB_STAGING_EMAIL` mặc định làm việc ở instance `TIB_STORE_INSTANCE_ID` `Enterprise (Test)`, store **`<TIB_STORE_URL>`** (sidebar dưới tên `<org của TIB_USER_A>`, và `Store Settings`). Đây là store đích khi publish.
- Instance id: <TIB_STORE_URL> = `TIB_STORE_INSTANCE_ID`, <TIB_SDK_V2> = `TIB_SDK_V2_INSTANCE_ID` (plan `Starter (Test)`), `TIB_BOUNDLESS_INSTANCE_ID` = `<org Boundless>` (Boundless, <domain Boundless>, plan `Basic - Picanova`).
- Plan badge của store mặc định có lúc hiện `Free for development`, có lúc `Enterprise (Test)` — cùng store, không phải lỗi switch.
- **Instance active lưu phía SERVER theo account**, dùng chung giữa các phiên. Phiên khác có thể đổi instance giữa chừng (đã gặp: `TIB_BOUNDLESS_INSTANCE_ID`, <TIB_SDK_V2> `TIB_SDK_V2_INSTANCE_ID`, <org của TIB_USER_B> `<store của TIB_USER_B>-2` acting_user 94, user account không Mapbox `sample-tib-campaign`). Dấu hiệu: `/orders/<id>` của store mặc định trả trang trống, dữ liệu lạ.
- **Luôn kiểm trước khi tạo data:** đọc tên store ở sidebar + `GET /api/user` (id phải là 64) + request `/api/instances/<id>/...`.
- Session còn sống nhưng là user account không Mapbox: login lại `/login?staff=true` vẫn ra 247. Phải đổi bằng switcher (dưới).

Sidebar instance `TIB_STORE_INSTANCE_ID`: `Home`, `Orders`, `Bulk Fulfill`, `Campaigns` (> `by Product Base` `/campaigns`, `by Shopify Products` `/platform-products`), `Product Base` `/products`, `Artworks` `/artworks`, `Assets`, `Store Settings`, `Extras`, `AI Assistant (MCP)`, `Organization`.

## Đổi store / instance (switcher)

Cách ổn định nhất (2026-10-28/29):
1. Click `.instance-domain:visible` (khối tên instance/domain góc trên sidebar; cũ: `.sidebar-users .user-switcher-toggle`, hoặc `page.mouse.click(150,98)`).
2. Popup `.user-switcher-popover` (`Switch to:`, ô `Search..`, danh sách user/org có mũi tên `>`).
3. Nếu org đang thu gọn: click org (`<org của TIB_USER_A>` / `<org Boundless>`) để xổ store con.
4. Click store theo domain: `<TIB_STORE_URL>` (hoặc `.user-item__instance__domain:visible`, `getByText('| <TIB_STORE_URL>')`, `getByTitle('<TIB_SDK_V2> | <store>...')`).
5. ⇒ `POST /api/users/<id>/login` 200, về `/`. Reload/navigate lại để sidebar cập nhật (reload có thể `ERR_ABORTED`, vô hại).

Ghi chú:
- Ô `Search..` có lúc lọc được (gõ `<TIB_STORE_URL>`), có lúc không — khi không lọc được thì xổ org rồi click domain.
- Org `<org Boundless>` có 2 dòng cùng tên `tester 4` (<domain Boundless> / <domain Boundless phụ>) → chọn theo domain: `page.getByText('<domain Boundless>').first()`.
- Dữ liệu Organization dùng chung: Product Base, campaign, artwork tạo ở store này hiện ở store khác cùng org. Header store là state phía server.
- `/platform-products/new` chọn store riêng trong form, không cần switch sidebar.

## Storefront

- `<TIB_STORE_URL>` và `<TIB_SDK_V2>` đều có password storefront: `TIB_STORE_PASSWORD`, `TIB_SDK_V2_PASSWORD`.
- Publish ảnh hưởng thật ra storefront staging → chỉ publish khi được yêu cầu.

## Xem portal bằng account khác mà không đụng session dùng chung

- Session của `playwright-2` có thể là user khác (2026-11-05: user `TIB_USER_B` ⇒ `GET /api/campaigns/<id của user `TIB_USER_A`>` 403, portal trống). Không `POST /api/logout`: lệnh này huỷ session chung trong `mcp-isolated.json`.
- Cách đã chạy: `browser_tabs` action `new` với `isolatedContext` → `/login?staff=true` → `pbcopy` email/password từ `.env` → click ô → `Meta+v` → xoá clipboard → `Log in`. Không có password trong output. Kiểm `GET /api/user`, xong đóng tab.
