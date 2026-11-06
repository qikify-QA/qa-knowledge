# Gỡ block khi vận hành

Tra theo dấu hiệu, làm theo cách xử lý, rồi xác minh. Cách xử lý chỉ áp cho bước setup, không áp cho luồng đang kiểm thử, và không bao giờ là tiêu chí Pass.

## Mail không về
- Dấu hiệu: không thấy mail verify; Dashboard có banner báo email platform lỗi `[RG]`.
- Cách xử lý: nhờ dev sinh link.
- Cách xác minh: Admin → Activities thấy status đổi.

## API bị 302 về `#/login`
- Dấu hiệu: request trả 302 thay vì JSON.
- Cách xử lý: thêm `Accept: application/json` `[RG]`.
- Cách xác minh: `GET /api/user` trả JSON.

## Bị chặn ở trang login
- Dấu hiệu: permission classifier chặn thao tác.
- Cách xử lý: không thử vòng, trả `BLOCKED` để operator xử lý.

## Không thấy payment method sau khi đổi Country
- Dấu hiệu: danh sách vẫn như cũ `[TC]`.
- Cách xử lý: full reload, danh sách bị cache trong SPA.
- Cách xác minh: danh sách theo Country mới hiện ra.

## Sửa Balance ở admin không có tác dụng
- Dấu hiệu: báo "Saved" nhưng số không đổi `[RG]`.
- Cách xử lý: dùng New conversion ghi rõ lý do, không dùng field Balance.
- Cách xác minh: `GET /api/user` trả `balance` mới.

## Import báo lỗi sau khi thêm Program hoặc Level
- Dấu hiệu: dòng CSV không ra Conversion.
- Cách xử lý: kiểm Program Commissions có đủ dòng cho mọi Level.
- Cách xác minh: upload file `QA-` mới ra đúng số Conversion.

## Không có Conversion cho dòng usage
- Dấu hiệu: upload xong dòng `App sale – usage` không ra Conversion.
- Cách xử lý: kiểm rate card, `handle_usage_charge` có thể đang tắt `[DOC]`.
- Cách xác minh: bật ở rate card `QA-`, upload file mới.

## Không tìm thấy `tracking_id` đã dùng
- Dấu hiệu: tìm ở Tracking Informations không ra.
- Cách xử lý: không phải block, `tracking_id` bị xoá sau khi tạo shop `[DOC]`. Xác minh qua Customers.

## Thiếu `X-API-Key` hoặc session admin
- Dấu hiệu: không có giá trị trong env, không có session.
- Cách xử lý: hỏi operator. Không có thì case phụ thuộc là `BLOCKED`.
