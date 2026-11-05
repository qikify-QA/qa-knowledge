# Product guide — qikfiliate

Tổng quan và setup của Qikfiliate: product làm gì, chức năng ở đâu, cần env, account, config gì để chạy. File được cập nhật cùng các lần publish knowledge: setup mức product mới thì thêm vào đây. Config riêng và khác biệt staging/production của một feature nằm ở `profile.json` của feature đó.

Đọc theo vai trò:

| Bạn là | Đọc | Để làm gì |
|---|---|---|
| Newbie / agent mới | §0 → §4 → §9 | hiểu product, biết chức năng nằm ở đâu |
| Agent kiểm thử | §0 → §2 → §5 → §8 → §10 | dựng data và test một feature bất kỳ |

**Guide này trả lời "vào đâu, làm thế nào". KB và checklist cùng thư mục trả lời "đúng phải là gì".** Không dùng guide này làm expected result. Không ghi credential, email hay tên người thật vào file này.

**Độ tin cậy của từng thông tin:**

| Nhãn | Nghĩa |
|---|---|
| `[RG]` | Thấy trên staging sau upgrade, trong regression Koin 2026-10-22. Mới nhất |
| `[TC]` | Thấy trên staging qua test case QAF-001 / QAF-002, **trước** upgrade |
| `[DOC]` | Chỉ có trong tài liệu dev (2026-08-20), chưa xác minh sau upgrade. Nhãn nút và đường dẫn có thể đã đổi |
| `[?]` | Chưa biết. Ai gặp thì ghi lại và báo operator |

> **KB v1 cũ hơn hệ thống hiện tại.** KB viết từ source trước đợt upgrade Laravel và đổi URL. Admin mô tả trong KB là `encore/laravel-admin`; staging hiện chạy Filament. Check nào nhắc nút, route hay màn hình admin thì đối chiếu §3 trước. Lệch về **giao diện** là KB cũ, không phải bug. Lệch về **hành vi tiền** thì ghi evidence và hỏi PO.

## 0. Product trong 5 phút

Qikfiliate là hệ thống affiliate dùng chung của Qikify. Affiliate giới thiệu shop Shopify cài app; khi shop trả phí, affiliate nhận hoa hồng và tự yêu cầu rút tiền.

| Actor | Dùng gì | Làm gì |
|---|---|---|
| Affiliate (`User`) | Dashboard, Vue SPA | Đăng ký, lấy link, xem hoa hồng, yêu cầu rút tiền |
| Admin (Ops/Finance) | Admin panel, Filament `[RG]` | Quản lý affiliate, rate card, upload CSV, xử lý invoice |
| Client app (vd mysbox) | Integration API, `X-API-Key` | Báo shop đã click, cài, subscribe, gỡ app. Server-to-server, không có UI |

**Luồng chính — mỗi bước là một chỗ có thể test:**

```
Affiliate lấy link (Links)
   │  khách click
   ▼
Client app: POST /api/tracking-id ─► TrackingInformation (có hạn)
   │  khách cài app
   ▼
Client app: POST /api/customers ──► Customer gắn với affiliate
            POST /api/customer-events ─► trạng thái shop (KHÔNG mang tiền)

Admin upload CSV Payout của Shopify ─► tính hoa hồng từng dòng ─► Conversion
   │                                    (Level × Program → rate card)
   ▼
balance của affiliate tăng
   │  affiliate bấm Request Payment
   ▼
Invoice (pending) ─► admin chuyển tiền thật ngoài hệ thống ─► đổi status completed
```

**Ba điều phải nhớ:**

1. Tiền chỉ vào hệ thống qua CSV Payout hoặc conversion nhập tay. API không mang số tiền.
2. Payout là tiền Shopify trả Ownego; Invoice là tiền Ownego trả affiliate. Hai dòng tiền chỉ nối qua `balance`.
3. `Customer` là **shop**, `User` là **affiliate**. Xem §4 trước khi đọc bất kỳ KB item nào.

**Một KB, nhiều brand:** tài liệu viết từ instance `koin-partners`. Item có `scope.brand` khác `null` chỉ đúng cho brand đó. Staging ở §1 là instance Koin/Mysbox, tiêu đề "Mysbox Affiliate" `[RG]`. Test instance khác thì ghi rõ vào kết quả.

## 1. Surfaces và entry point

| Surface | Base URL | Entry point | Ghi chú |
|---|---|---|---|
| Affiliate dashboard | `KOIN_DASHBOARD_URL` = `https://staging-partners.mysbox.io/` `[RG]` | `#/login`, `#/signup`, `#/verification`, `#/verified`, `#/resend-verification`, `#/forgot-password`, `#/dashboard`, `#/links`, `#/conversions`, `#/customers`, `#/invoices`, `#/account` `[RG]` | Selector ngôn ngữ chỉ có ở trang login. Nav Resources mở Google Drive. QAF-001 từng dùng `staging-partners.qikify.com`; host đó còn chạy không `[?]`, mặc định dùng host trên |
| Admin panel | host `[?]` | 16 mục, xem §3 | QA tự đăng nhập; chưa có credential cho agent |
| API dashboard | `<KOIN_DASHBOARD_URL>/api` `[RG]` | §6 | JWT, chỉ dữ liệu của chính affiliate |
| Integration API | 5 endpoint `[DOC]`; host `[?]` | §6 | Header `X-API-Key`; chưa có key staging |
| Email | Brevo | 8 template, §7 | Dashboard có banner báo email platform lỗi `[RG]`: mail có thể không về |
| Slack kênh `affiliate` | nội bộ | Bắn khi affiliate mới xác thực và khi có yêu cầu thanh toán `[DOC]` | Staging có bắn kênh thật không `[?]`, xem §5 |
| Console command | CLI server, chỉ dev | `user-level:update`, `conversion-type:update`, `charge_creation_time:fill` `[DOC]` | Không có UI |

Không có storefront. Không có DB access. **Production là stop condition** cho mọi thao tác ghi. QAF-002 từng đối chiếu nội dung trang public và Brevo production: chỉ làm khi operator giao, và chỉ đọc.

## 2. Auth và xác minh account

**File env:** `.env.koin` do operator cấp. Tên biến và công dụng:

| Biến | Dùng cho |
|---|---|
| `KOIN_DASHBOARD_URL`, `KOIN_DASHBOARD_OLD_URL` | URL dashboard hiện tại, và URL cũ để kiểm redirect |
| `KOIN_AFF_APPROVED_EMAIL` / `_PASSWORD` | Affiliate đã verify, approved, có data. Account chính để xem hiển thị |
| `KOIN_AFF_UNVERIFIED_EMAIL` / `_PASSWORD` | Chưa verify email, để test chặn login |
| `KOIN_AFF_DISAPPROVED_EMAIL` / `_PASSWORD` | Bị từ chối. Đọc §7 trước khi dùng |
| `KOIN_AFF_WITH_BALANCE_EMAIL` / `_PASSWORD` | Có balance đủ để test Request Payment; trống thì dùng account approved |
| `KOIN_AFF_MAIN_EMAIL` / `_PASSWORD` | Đăng ký bằng email chính, happy case signup |
| `KOIN_SIGNUP_BASE_EMAIL` | Email gốc cho plus-addressing, vd `+qa-<run>-01`. Phải mở được hộp thư này |
| `KOIN_ALLOW_CREATE_INVOICE` | `yes`/`no`. `no` thì không tạo Invoice, các case đó là `BLOCKED` |

Chưa có trong file env: credential admin, `X-API-Key`, host admin, host Integration API.

**Dashboard:** `POST /api/login` trả JWT `access_token`, `expires_in` 3600. `POST /api/refresh` cấp token mới. Mọi request phải có `Accept: application/json`, thiếu thì bị 302 về `#/login` `[RG]`. Email phân biệt hoa thường khi login `[RG]`.

**Admin:** agent không tự login. QA đăng nhập trong profile browser riêng rồi bàn giao session, hoặc tự làm phần admin theo hướng dẫn `[RG]`.

**Xác minh account — bước đầu tiên, và sau MỖI lần login lại:**

1. Host đang mở là staging, không phải production.
2. `GET /api/user` trả `data.email` đúng biến env của account đang dùng `[RG]`. Sai → DỪNG, `BLOCKED`.
3. Với admin: tài khoản hiển thị ở Profile đúng tài khoản QA bàn giao.

**Chỉ thao tác trên account trong `.env.koin` và account `QA-` tự tạo.** Account, email, shop trong test case cũ là của người khác. Bị chặn bởi permission classifier ở trang login → không thử vòng; trả `BLOCKED` để operator xử lý.

## 3. Object map

Object hợp lệ và alias: `_registry.json` cùng thư mục. Có 13 object, 45 feature; từng feature ở §9.

| `object_key` | Là gì | Màn hình chính | Test bằng |
|---|---|---|---|
| `affiliate-account` | Vòng đời tài khoản affiliate | Dashboard: signup, login, Account. Admin: Affiliate Users | UI + email |
| `affiliate-level` | Bậc theo số shop trả phí, VIP | Admin: Levels, Affiliate Users | Admin + CSV |
| `program` | App Shopify được quảng bá | Admin: Programs. Dashboard: Links | UI |
| `commission-rate-card` | % và cap theo cặp Program × Level | Admin: Program Commissions | UI + CSV |
| `referral-attribution` | Gắn shop với đúng affiliate | Dashboard: Links. Admin: Tracking Informations | Integration API |
| `customer-shop` | Shop được giới thiệu và vòng đời | Admin: Customers, Customer Events. Dashboard: Customers | Integration API + UI |
| `integration-api` | 5 endpoint cho client app | Không có UI | Integration API |
| `payout-import` | Upload CSV, khớp shop, chống trùng | Admin: Upload Payouts | CSV |
| `commission-calculation` | Engine tính tiền cho một dòng CSV | Kết quả ở Conversions | CSV |
| `conversion-ledger` | Sổ hoa hồng | Admin: Conversions. Dashboard: Conversions | UI |
| `invoice-payout` | Balance và yêu cầu rút tiền | Dashboard: khối Payout, Invoices. Admin: Invoices | UI + email |
| `payment-method` | Phương thức nhận tiền | Dashboard: Account. Admin: Payment Methods | UI |
| `admin-console` | Trang chủ admin, Embedded Version, console command | Admin: Embedded Version | UI; command cần dev |

**Admin hiện tại khác KB ở đâu** (Filament 5.6.3, 16 mục: Profile, Embedded Version, Admin Users, Roles, Activities, Upload Payouts, Conversions, Customer Events, Customers, Tracking Informations, Affiliate Users, Invoices, Payment Methods, Levels, Program Commissions, Programs) `[RG]`:

| KB nói | Staging hiện tại |
|---|---|
| Mọi admin có quyền như nhau | Có Admin Users, Roles (Shield). Phân quyền thực tế `[?]` |
| Nút "Approve" trên danh sách | Không có; approve qua form Edit |
| Disapprove qua form Edit | Có thêm row action "Disapproved" và "Disapproved and send notification" |
| Màn Custom Conversion, nút "Add Custom Conversion" | "New conversion" ở Conversions |
| Upload ở menu Conversion | Màn riêng Upload Payouts |
| Màn Populate/reconcile | Không thấy |
| Switch `visible` sửa nhanh trên danh sách | Không còn sửa nhanh trên danh sách |
| Không có audit log | Activities ghi lại thay đổi, kể cả thay đổi do hệ thống |

## 4. Vocabulary

| Thuật ngữ | Nghĩa | Hay nhầm với |
|---|---|---|
| User | Affiliate / partner | Merchant, khách cuối |
| Customer | **Shop** Shopify được giới thiệu, theo cặp shop × app | Khách cuối của shop |
| Program | App Shopify được quảng bá | Chương trình khuyến mãi |
| `slug` (Program) | Khoá khớp với `app_slug` trong CSV | `ref_slug`, dùng cho link giới thiệu |
| `ref` | Slug link giới thiệu riêng của affiliate | `tracking_id` |
| Tracking information | Một lượt click, dùng một lần, có hạn | Link giới thiệu |
| Payout | Shopify → Ownego, đầu vào | Invoice |
| Invoice | Ownego → affiliate, đầu ra, do affiliate tự yêu cầu | Payout |
| Conversion | Một dòng hoa hồng. Type: `first`, `recurring`, `usage`, `custom` | Chuyển đổi marketing |
| `partner_share` | Tiền Ownego thực nhận cho một dòng charge; gốc để nhân % | `amount` |
| `amount` | Hoa hồng affiliate nhận sau % và cap | `partner_share` |
| Level | Bậc affiliate, dùng chung mọi Program | Plan của app |
| Rate card | `ProgramCommission`, một dòng cho một cặp Program × Level | % toàn hệ thống |
| Cap | `maximum_amount` theo từng dòng; `usage_maximum_amount` cộng dồn cả đời | Cap theo tháng |

Nhóm feature theo user goal (kiếm hoa hồng, rút tiền, vận hành kỳ payout), không theo tên control.

## 5. Mutation guard riêng

Staging dùng chung và admin có quyền rộng. Mặc định chỉ đụng data của mình.

**Được phép trên staging:**

- Tạo affiliate, Program, shop có tiền tố `QA-` / `qa-`. Với `ref` kiểm tra trước blocklist trong KB của `affiliate-signup`.
- Upload CSV **chỉ chứa dòng của shop `QA-`**.
- New conversion, bật VIP, disapprove trên affiliate `QA-`.
- Tạo và đổi status Invoice của affiliate `QA-`, khi `KOIN_ALLOW_CREATE_INVOICE=yes`. Không phát sinh chuyển tiền thật.
- Gọi Integration API với shop `qa-…`, khi có key.

**Cấm:**

- Sửa hoặc xoá Program, rate card, Payment Method, affiliate, shop không phải của mình.
- Xoá hoặc tạo lại Payment Method PayPal / Payoneer: frontend hardcode id `1` và `2`. Muốn test thì tạo method `QA-` mới.
- Tạo hoặc sửa Level khi chưa được cho phép. Level là cấu hình toàn hệ thống; thiếu rate card cho Level mới sẽ làm lỗi import của Program khác.
- Upload file Payout thật hoặc file chứa shop thật.
- Gửi tiền thật, hoặc dùng thông tin thanh toán thật trong Payment Info.
- Chạy console command, sửa DB.
- Dùng Embedded Version khi người khác đang test dashboard: nó ép mọi affiliate tải lại.

**Tác dụng phụ cần biết trước:**

- Signup, verify, tạo Invoice bắn Slack kênh `affiliate` `[DOC]`: hỏi operator trước khi chạy hàng loạt.
- Thao tác ở `affiliate-account` và `invoice-payout` gửi email Brevo. Chỉ dùng alias của `KOIN_SIGNUP_BASE_EMAIL`.
- Test invoice làm `balance` về 0 mà **không khôi phục được qua field Balance** (§7). Dùng affiliate `QA-` riêng, đừng dùng account approved chung.
- Register bằng API bỏ qua blocklist `ref` `[RG]`: gọi thử sẽ tạo tài khoản rác thật.

**Cleanup:** ghi id mọi thứ đã tạo và `balance` trước/sau. Khôi phục balance chỉ bằng New conversion ghi rõ lý do, và nó thêm một dòng vào lịch sử. Xoá Conversion có hoàn balance không `[?]`: kiểm lại sau khi xoá. Action không có trong danh sách được phép và không có đường cleanup → DỪNG, báo operator.

**Redact trong evidence:** JWT, `X-API-Key`, password, `payment_info`, `payment_details`, email. Staging bật `APP_DEBUG`, response lỗi có trace và đường dẫn server: cắt bỏ. Form Edit affiliate chứa password hash trong HTML: không lưu HTML của form này.

## 6. Network / API hints

**API dashboard (JWT, Bearer), `[RG]` trừ khi ghi khác:**

| Method + path | Việc |
|---|---|
| `POST /api/register` | Đăng ký |
| `POST /api/login`, `/api/refresh`, `/api/logout` | Phiên đăng nhập |
| `POST /api/email/resend`, `POST /api/password/email` | Gửi lại xác thực, quên mật khẩu |
| `GET /email/verify/{id}/{hash}?expires&signature` | Link xác thực; redirect về `/` |
| `GET /api/user` | Thông tin affiliate: `balance`, `can_create_invoice`, `bonus_at`, `payment_method`, `payment_details` |
| `GET /api/payment-methods`, `PUT /api/user/payment-method` | Danh sách theo country, lưu thông tin nhận tiền |
| `POST /api/invoices`, `PUT /api/invoices/{code}` | Tạo, huỷ yêu cầu thanh toán. `{code}` là mã invoice, không phải id số |

**Integration API (`X-API-Key`), tất cả `[DOC]`, payload ở F3 §8:**

| Method + path | Việc |
|---|---|
| `POST /api/tracking-id` | Ghi một lượt click |
| `POST /api/customers` | Tạo shop, tiêu thụ `tracking_id` |
| `DELETE /api/customers` | Soft-delete shop |
| `PUT /api/trashed-customers` | Khôi phục shop |
| `POST /api/customer-events` | Ghi sự kiện vòng đời |

Không có OpenAPI hay Postman collection. API list phân trang có `meta.total`. Link giới thiệu dạng `https://getkoin.io/staging-install/mysbox?ref=<ref>` `[RG]`.

## 7. Gotchas

**Lỗi đã thấy ở regression 2026-10-22** (mã theo báo cáo đó, không phải ID Testlane; đã fix hay chưa `[?]`). Gặp lại thì ghi là tái hiện:

| Mã | Mức | Hiện tượng |
|---|---|---|
| INV-1 | Critical | Status invoice ở admin là ô text tự do: chuyển được `cancel → completed`, lưu được giá trị rác. Đổi status ở admin không đụng balance |
| INV-2 | High | Completed qua admin không chốt fee, method, payment info. Dashboard hiện Fee "-$null", Net sai |
| INV-3 | Medium | Sửa Balance ở admin báo "Saved" nhưng không lưu |
| BUG-1 | High | BE không validate `ref`, blocklist chỉ còn ở frontend |
| BUG-2 | Medium | Throttle resend verification bị đếm 2 lần |
| BUG-3 | Medium | Ngày trả về dạng UTC, payout date lệch theo timezone browser |
| BUG-4 | Low | BE nhận `payment_info` sai định dạng cho PayPal |
| SEC-1 | Medium | Form Edit affiliate gửi bcrypt hash xuống HTML |
| ADM-3 | Low | Lưu form Edit làm `payment_details` thành object toàn `null` |

**Cần xác nhận, chưa phải bug:** sau verify bị redirect về login không có thông báo; tiền hiển thị 3 chữ số thập phân; login phân biệt hoa thường ở email; admin tải chậm 2.5–10.5 giây/trang.

**Khác KB, cần biết khi test:**

- Modal Request Payment không có ô nhập số tiền, luôn rút toàn bộ `[RG]`. KB nói tự nhập được.
- `usage_maximum_amount = 0` nghĩa là không giới hạn, dù UI hiện "$0" `[RG]`.
- Tài khoản disapproved trong env có thể chưa verify email, nên login báo "not verified", không phải lỗi login. Muốn test disapprove phải có account đã verify: dùng F8.

**Dữ liệu staging:**

- Account approved có thể đang balance $0 và có invoice cũ từ đợt test: đọc lại trước khi dùng, đừng tin số trong báo cáo.
- 4 tài khoản rác `qa-upg-1022-api1..4` với `ref` chứa từ cấm có thể còn tồn tại: không phải hành vi đúng của signup.
- Conversions #40–47 có năm charge lệch payout date: nghi do CSV test, không dùng làm mẫu.

**Từ test case trước upgrade `[TC]`:**

- Danh sách payment method bị cache trong SPA: đổi Country xong phải **full reload**.
- Bank transfer (Japan) chỉ hiện khi Country = Japan, form 7 field; nhãn không dịch là đúng thiết kế theo dev. Số tài khoản nhận 6–7 chữ số đang chờ PO xác nhận. Kết quả này chưa vào KB: đọc TC-QAF-002 trên Testlane.
- QAF-002 để lại BUG-108 đến BUG-112 về email và link: request_invoice, invoice_canceled không thấy gửi; link login trong email approved trỏ sang Koin; template reward; chữ "Koin Affiliate" trong email approved invoice; link referral ở trang Register.
- Brevo template brand Mysbox: 892 verify, 893 reset_password, 894 invoice_completed, 895 invoice_canceled, 896 approved, 897 disapproved, 898 request_invoice, 899 reward.

**Từ tài liệu dev `[DOC]`:**

- Upload CSV bỏ dòng lỗi **âm thầm**: banner chỉ báo số đã tạo. Tự đối chiếu số dòng với số Conversion. "0 created" khi upload lại cùng file là đúng.
- Không có Conversion cho dòng usage có thể do `handle_usage_charge` tắt, không phải bug. Kiểm rate card trước.
- Tìm `tracking_id` đã dùng mà không thấy là bình thường: nó bị xoá sau khi tạo shop.
- Admin không thấy `is_capped`; chỉ dashboard có badge "cap reached". Dòng usage cap về $0 không hiện trên dashboard.
- Đổi rate card, Level, VIP không tính lại Conversion cũ.
- `transfer_fee` để trống nghĩa là Ownego chịu phí.

**Tài liệu lệch nhau:** khớp CSV dùng `Customer.name` = cột `Shop`, nhưng ví dụ Integration API đặt `name` là tên shop và domain ở `related_id`. F3 tránh bằng cách đặt cả hai là domain.

## 8. Dựng test data

Dựng theo thứ tự phụ thuộc. Giá trị cụ thể (ngưỡng, %, số ngày) lấy từ KB, đừng dùng số trong ví dụ của tài liệu.

```
F1 affiliate ──┐
F2 Program ────┴─► F3 shop ─► F4 CSV ─► balance ─► F6 đủ điều kiện rút ─► F7 invoice
                                         ▲
                           F5 New conversion (đường tắt)
```

**F0 — Login và guard.** Làm §2. Không bỏ qua.

**F1 — Affiliate mới.**
1. Mở `#/signup`, điền `name`, alias `+qa-<run>-NN` của `KOIN_SIGNUP_BASE_EMAIL`, password, `ref` dạng `qa-<run>-<n>`. Thành công chuyển sang `#/verification`.
2. Mở mail, click link. Mail không về thì nhờ dev sinh link. Admin → Activities xác nhận status đổi cùng lúc với verify.
3. Login, xác minh `GET /api/user`.

**F2 — Program và rate card.**
1. Admin → Programs: `name` `QA-<run>`, `slug` `qa-<run>`.
2. Admin → Program Commissions: tạo **một dòng cho mỗi Level đang có**. Thiếu dòng sẽ làm lỗi import.
3. Muốn test usage: bật `handle_usage_charge` và điền 2 field kèm theo.

**F3 — Shop được giới thiệu.** Cần `X-API-Key`; chưa có thì hỏi operator. Admin → Customers có tạo tay được không `[?]`.
```http
POST /api/tracking-id
X-API-Key: <key>
{ "ref": "<ref của F1>", "source_url": "https://example.com/qa" }

POST /api/customers
X-API-Key: <key>
{ "tracking_id": "<từ bước trên>", "related_id": "qa-<run>-1.myshopify.com",
  "name": "qa-<run>-1.myshopify.com", "email": "<alias test>", "program_slug": "qa-<run>" }

POST /api/customer-events
X-API-Key: <key>
{ "customer_related_id": "qa-<run>-1.myshopify.com", "program_slug": "qa-<run>", "name": "installed" }
```
Xác minh ở Admin → Customers và Dashboard → Customers.

**F4 — CSV Payout tối thiểu.** Tự viết file, không dùng file thật. Upload ở Admin → Upload Payouts đã chạy được `[RG]`, nhưng header đầy đủ chưa được ghi lại `[?]`. Cột đã biết:

| Cột | Giá trị |
|---|---|
| `Shop` | domain của F3 |
| `app_slug` | slug của F2 |
| `Charge Type` | `App sale – 30-day subscription`, `App sale – usage`, `App refund`, `App downgrade`. Dấu là en dash |
| `Charge ID` | chuỗi bất kỳ; để trống với downgrade |
| `Charge Creation Time` | timestamp; **thiếu cột là file bị từ chối** |
| `Partner Share` | số; âm với refund/downgrade |
| kỳ payout và payout date | tên cột chính xác `[?]` |

Lần đầu xin QA file CSV đã upload thành công ngày 2026-10-22 làm mẫu, rồi ghi header vào đây. Đối chiếu banner với số dòng sau khi upload.

**F5 — Có balance nhanh.** Admin → Conversions → New conversion → chọn affiliate, shop, `amount`, `reason` `[RG]`. Không dùng khi test Level hoặc first-month, vì `custom` không tham gia các cơ chế đó.

**F6 — Affiliate đủ điều kiện rút.** Điền Payment Info ở Account bằng dữ liệu giả. `GET /api/user` → `can_create_invoice` cho biết kết quả.
- Đường nhanh: bật `is_vip`, đặt `level` trùng một `level_index` đang có, rồi F5.
- Đường không VIP: đủ số shop và balance theo KB của `payout-request-eligibility`. Cách đếm shop còn là `OQ-invoice-payout-003`, nên dùng shop có conversion `first`/`recurring` qua F3 + F4 để đúng theo cả hai cách hiểu.

**F7 — Invoice ở từng trạng thái.** Cần `KOIN_ALLOW_CREATE_INVOICE=yes`.
- `pending`: Dashboard → Request Payment → Send Request. Balance về 0.
- `cancel` có hoàn balance: Dashboard → icon thùng rác → Cancel Request, khi còn pending.
- `approved`, `completed`: Admin → Invoices → gõ status → Save. Gõ chính xác, ô này không validate.
- Mỗi lần Request Payment rút toàn bộ balance, nên cần nạp lại bằng F5 cho invoice tiếp theo.

**F8 — Trạng thái đặc biệt của affiliate.**
- Disapprove: Admin → Affiliate Users → row action, hoặc Edit `status` + `disapproved_reason`. Account phải đã verify, nếu không login sẽ báo lý do khác.
- Approve lại: form Edit.
- Chưa verify: dừng F1 trước bước click link.

## 9. Bản đồ feature

Cột "Fixture" trỏ tới §8. Expected result và check: `<object>/checklists/<feature>.json`.

| Object | Feature | Vào đâu, làm gì | Fixture |
|---|---|---|---|
| affiliate-account | `affiliate-signup` | `#/signup`, thử field và `ref`; thử cả UI lẫn API | — |
| | `email-verification-and-auto-approval` | Click link trong email, `#/resend-verification` | F1 |
| | `affiliate-login-access-control` | Login ở từng trạng thái tài khoản | F1, F8 |
| | `admin-affiliate-review` | Admin → Affiliate Users: row action, Edit | F1, F8 |
| | `affiliate-dashboard-overview` | `#/dashboard`: bảng shop, khối Payout, banner bonus | F1 |
| | `affiliate-profile-maintenance` | `#/account`. Admin → Affiliate Users → Edit | F1 |
| | `affiliate-email-notifications` | Kích hoạt từng sự kiện, đọc hộp thư | F1, F7, F8 |
| | `new-affiliate-bonus` | Banner Dashboard, `bonus_at`. Staging có cấu hình không `[?]` | F1, F3, F4 |
| affiliate-level | `level-definition-management` | Admin → Levels. Chỉ đọc nếu chưa được phép (§5) | — |
| | `level-progression` | Tăng shop trả phí qua CSV, xem Level | F3, F4 |
| | `vip-level-override` | Affiliate Users → Edit `is_vip`, `level`, rồi upload CSV | F3, F4 |
| program | `program-launch` | Admin → Programs, rồi rate card | F2 |
| | `program-catalog-for-affiliates` | `#/links`, sort, `visible` | F2 |
| commission-rate-card | `rate-card-configuration` | Admin → Program Commissions | F2 |
| | `usage-commission-enablement` | Form rate card, switch usage | F2 |
| referral-attribution | `tracking-link-generation` | `#/links` → Get Link | F1, F2 |
| | `click-to-install-attribution` | Gọi `tracking-id` rồi `customers`. Không tua được giờ để test hết hạn | F3 |
| | `tracking-information-log` | Admin → Tracking Informations, chỉ xem | F3 |
| customer-shop | `customer-shop-registry` | Admin → Customers: list, Show, Skip First Month, Restore | F3 |
| | `customer-lifecycle-state` | Gửi event, xem Customer Events và `#/customers` | F3 |
| integration-api | `api-key-authentication` | Gọi không key, sai key, đúng key | — |
| | `customer-provisioning-api` | `customers`, `DELETE`, `trashed-customers` | F3 |
| | `customer-event-reporting-api` | `customer-events` với event đúng và sai | F3 |
| payout-import | `payout-csv-upload` | Upload Payouts: file đúng, thiếu cột, thiếu giá trị | F3, F4 |
| | `charge-type-classification` | Một file với đủ loại `Charge Type` | F3, F4 |
| | `customer-matching-and-dedup` | Upload lại cùng file, dòng không khớp shop | F3, F4 |
| | `populate-reconcile-late-data` | Trước hết tìm xem màn này còn không; không có thì ghi `NOT_COVERED` và báo | F3, F4 |
| commission-calculation | `commission-decision-flow` | Upload rồi đọc Conversions | F2, F3, F4 |
| | `first-month-commission` | Chuỗi charge theo ngày lịch, kể cả ranh giới | F2, F3, F4 |
| | `recurring-commission` | Charge sau tháng đầu, có và không cap | F2, F3, F4 |
| | `refund-and-downgrade-adjustment` | Dòng âm sau dòng dương | F2, F3, F4 |
| | `usage-charge-commission` | Nhiều dòng usage, nhiều kỳ, để chạm cap | F2, F3, F4 |
| conversion-ledger | `admin-conversion-review` | Admin → Conversions | F4 |
| | `affiliate-conversion-view` | `#/conversions`. Kiểm ngày ở 2 timezone | F4 |
| | `custom-conversion-entry` | Admin → Conversions → New conversion | F5 |
| invoice-payout | `balance-accrual` | So `balance` trước/sau từng sự kiện | F4 hoặc F5 |
| | `payout-request-eligibility` | Khối Payout ở từng tổ hợp điều kiện; `can_create_invoice`; gọi thẳng API | F6 |
| | `payout-request-submission` | Request Payment | F6 |
| | `payout-request-cancellation` | `#/invoices` → huỷ | F7 |
| | `admin-invoice-processing` | Admin → Invoices. Kiểm chuyển status và snapshot | F7 |
| payment-method | `affiliate-payment-info-setup` | `#/account` → Payout Information. Full reload sau khi đổi Country | F1 |
| | `payment-method-catalog` | Admin → Payment Methods. Tạo method `QA-`, không đụng id 1, 2 | — |
| admin-console | `admin-home-dashboard` | Trang đầu admin | — |
| | `embedded-version-cache-bust` | Admin → Embedded Version (xem §5) | — |
| | `data-maintenance-commands` | Cần dev chạy; không thì `NOT_COVERED` | — |

## 10. Quy trình kiểm thử

Làm theo thứ tự với một feature hoặc một ticket:

1. **Chọn feature:** map từ khoá sang `object_key` qua `_registry.json`. Đọc `manifest.json` ở gốc repo để biết object có `PUBLISHED`, version nào. Quy tắc đầy đủ: `how-to-request/consumer-guide.md` §2–§4.
2. **Đọc knowledge:** `<object>/feature-summary.md` → `features/<feature>/profile.json` → `checklists/<feature>.json` → `open-questions.md` lọc theo feature → §3, §7 của guide để biết chỗ nào đã đổi. Trong profile, xem `entry_points[].precondition` để biết config riêng của feature, và `environment_differences` nếu có.
3. **Dựng data:** theo cột Fixture ở §9, sau khi qua guard §2.
4. **Chạy từng check:** `precondition` → `steps` → xem `observation_point` → so `expected_result`. Check viết từ tài liệu dev nên `steps` có thể nói theo hàm code, như `canCreateByUser`: quan sát qua UI hoặc API tương ứng.
5. **Ghi evidence:** instance, tên biến account (không ghi email), id data, thời điểm, screenshot hoặc response đã redact.
6. **Dọn data** theo §5.

**Kết luận mỗi check:**

| Tình huống | Kết luận |
|---|---|
| `status: READY`, khớp `expected_result` | `PASS` |
| `status: READY`, oracle `STRONG`, lệch, `confirmation_source.type` là `spec_doc` / `po_dev_confirm` / `test_case` | `FAIL` |
| `status: READY`, lệch, nguồn chỉ `dev_doc` | `SUSPECTED_FAIL`: ghi đủ evidence, đối chiếu PO/spec rồi mới chốt bug. Ở v1 toàn bộ 368 item `CONFIRMED_EXPECTED` thuộc nhóm này, kể cả khi manifest ghi `usable_as_oracle: true` |
| Check mô tả UI admin cũ (bảng ở §3) | `OUTDATED_CHECK`: test lại mục tiêu của check trên UI mới, ghi cả hai |
| `status: NEEDS_CONFIRMATION`, oracle `NONE`, hoặc item `CONFLICTED` / `UNRESOLVED` | Chỉ ghi `OBSERVED: <hành vi thật>`, không kết luận |
| Item có `scope.brand` khác brand đang test | `NOT_APPLICABLE` |
| `environment_differences` có `NOT_TESTABLE` | `NOT_APPLICABLE` trên môi trường đó |
| Không quan sát được, thiếu quyền, thiếu data | `NOT_COVERED` hoặc `BLOCKED`, nêu rõ thiếu gì |

**Đừng hiểu sai checklist:**

- `applicability.environment: documented` chỉ nói nguồn là tài liệu, không có nghĩa là không chạy được trên staging.
- Check `layer: db` chiếm số lớn (224/540 ở v1) mà không có DB access. Quan sát tương đương qua Admin hoặc `GET /api/user`; Activities thường cho thấy thay đổi field. Không có thì `NOT_COVERED`.
- Ở v1 có 192 check `READY` và 348 `NEEDS_CONFIRMATION`. Đây là kết quả dự kiến của lần bootstrap đầu.

**Sau khi test:**

- Hành vi thật khác knowledge, hoặc đã xác nhận một Open Question → gửi CCR bằng skill `create-ccr` (`consumer-guide.md` §5).
- Bug thật → báo theo quy trình của team trên Testlane. Không tự tạo hay comment Jira, không nhắn kênh ngoài khi operator chưa đồng ý.
- Guide sai hoặc gặp `[?]` đã có đáp án → báo operator để cập nhật mục đó.
