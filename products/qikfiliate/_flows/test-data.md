# Dựng test data

Dựng theo thứ tự phụ thuộc. Giá trị cụ thể (ngưỡng, %, số ngày) lấy từ KB. Ghi lại id từng thứ đã tạo.

```
F1 affiliate ──┐
F2 Program ────┴─► F3 shop ─► F4 CSV ─► balance ─► F6 đủ điều kiện rút ─► F7 invoice
                                         ▲
                           F5 New conversion (đường tắt)
```

## F0 — Login và xác minh

Làm theo `login-account.md`. Không bỏ qua.

## F1 — Affiliate mới

1. Mở `#/signup`, điền `name`, alias `+qa-<run>-NN` của `KOIN_SIGNUP_BASE_EMAIL`, password, `ref` dạng `qa-<run>-<n>`. Với `ref`, kiểm tra trước blocklist trong KB của `affiliate-signup`. Thành công chuyển sang `#/verification`.
2. Mở mail, click link. Admin → Activities xác nhận status đổi cùng lúc với verify.
3. Login, xác minh `GET /api/user`.

## F2 — Program và rate card

1. Admin → Programs: `name` `QA-<run>`, `slug` `qa-<run>`.
2. Admin → Program Commissions: tạo một dòng cho mỗi Level đang có. Thiếu dòng sẽ làm lỗi import.
3. Muốn test usage: bật `handle_usage_charge` và điền 2 field kèm theo.

## F3 — Shop được giới thiệu

Cần `X-API-Key`, chưa có thì hỏi operator. Admin → Customers có tạo tay được không `[?]`.

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

Xác minh ở Admin → Customers và Dashboard → Customers. Đặt cả `name` và `related_id` là domain: tài liệu lệch nhau về trường nào dùng để khớp CSV.

## F4 — CSV Payout tối thiểu

Tự viết file, không dùng file thật. Upload ở Admin → Upload Payouts `[RG]`. Header đầy đủ chưa được ghi lại `[?]`: lần đầu xin QA file đã upload thành công làm mẫu, rồi gửi khối C để bổ sung vào đây.

| Cột | Giá trị |
|---|---|
| `Shop` | domain của F3 |
| `app_slug` | slug của F2 |
| `Charge Type` | `App sale – 30-day subscription`, `App sale – usage`, `App refund`, `App downgrade`. Dấu là en dash |
| `Charge ID` | chuỗi bất kỳ; để trống với downgrade |
| `Charge Creation Time` | timestamp; thiếu cột là file bị từ chối |
| `Partner Share` | số; âm với refund, downgrade |
| kỳ payout và payout date | tên cột chính xác `[?]` |

Đối chiếu banner với số dòng sau khi upload.

## F5 — Có balance nhanh

Admin → Conversions → New conversion → chọn affiliate, shop, `amount`, `reason` `[RG]`. Không dùng khi test Level hoặc first-month, vì `custom` không tham gia các cơ chế đó.

## F6 — Affiliate đủ điều kiện rút

Điền Payment Info ở Account bằng dữ liệu giả. `GET /api/user` → `can_create_invoice` cho biết kết quả.

- Đường nhanh: bật `is_vip`, đặt `level` trùng một `level_index` đang có, rồi F5.
- Đường không VIP: đủ số shop và balance theo KB của `payout-request-eligibility`. Cách đếm shop còn là `OQ-invoice-payout-003`, nên dùng shop có conversion `first`/`recurring` qua F3 + F4 để đúng theo cả hai cách hiểu.

## F7 — Invoice ở từng trạng thái

Cần `KOIN_ALLOW_CREATE_INVOICE=yes`. Dùng affiliate `QA-` riêng, không dùng account approved chung.

- `pending`: Dashboard → Request Payment → Send Request.
- `cancel`: Dashboard → icon thùng rác → Cancel Request, khi còn pending.
- `approved`, `completed`: Admin → Invoices → gõ status → Save.
- Request Payment rút toàn bộ balance, nên nạp lại bằng F5 cho invoice tiếp theo.

## F8 — Trạng thái đặc biệt của affiliate

- Disapprove: Admin → Affiliate Users → row action, hoặc Edit `status` + `disapproved_reason`. Account phải đã verify, nếu không login sẽ báo lý do khác.
- Approve lại: form Edit.
- Chưa verify: dừng F1 trước bước click link.

## Cleanup balance

Khôi phục balance chỉ bằng New conversion ghi rõ lý do; nó thêm một dòng vào lịch sử. Xoá Conversion có hoàn balance không `[?]`: kiểm lại sau khi xoá.
