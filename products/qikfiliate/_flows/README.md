# Sổ tay flow staging qikfiliate — index

Cách thao tác đã biết trên `KOIN_DASHBOARD_URL` và admin. Đọc file này trước, rồi mở đúng file theo việc cần làm. Nhãn `[RG]`, `[TC]`, `[DOC]`, `[?]`: guide, đầu file.

## Danh sách file

| File | Đọc khi |
|---|---|
| `login-account.md` | Login Dashboard, phiên JWT, bàn giao session admin, xác minh account |
| `routes-api.md` | Route Dashboard, menu admin và đối chiếu với KB, request hay dùng |
| `test-data.md` | Fixture F0–F8 |
| `feature-entry.md` | Một feature vào đâu, làm gì, cần fixture nào |
| `troubleshooting.md` | Gặp block: dấu hiệu, cách xử lý, cách xác minh |
| `qa-rules.md` | Trình tự test một feature, cách kết luận từng check |

## Cạm bẫy chung

- Xác minh account trước khi tạo data, và sau mỗi lần login lại: `login-account.md`.
- Request API phải có `Accept: application/json`.
- Ô status Invoice ở admin không validate: gõ chính xác.
- Upload CSV xong phải tự đối chiếu số dòng với số Conversion.
- Data lạ có sẵn trên staging có thể là rác từ đợt test trước: không dùng làm mẫu, đọc lại số trước khi dùng.
- Conversion cũ không đổi sau khi sửa rate card, Level, VIP `[DOC]`: test bằng dòng CSV mới.
