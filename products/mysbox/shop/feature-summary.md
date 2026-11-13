# Shop — vòng đời shop merchant: cài đặt, kết nối, gỡ, kill switch, GDPR, quản lý shop trong admin
**Published context version:** 1

**Product:** mysbox · **Object:** `shop` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `install-and-onboarding` — Cài app, wizard onboarding và setup guide | Merchant cài app qua OAuth và cấp các quyền app cần, hệ thống tạo bản ghi shop ở gói Free với dữ liệu lấy từ Shopify, rồi merchant đi qua wizard onboarding (… | 67 | 30 | 23 | 1 |
| `shop-connection-and-reauth` — Kết nối Shopify của shop: token, làm mới, re-auth | Shop luôn giữ được kết nối với Shopify để app thay mặt shop làm việc khi merchant không online (token có hạn tự làm mới, job gia hạn hằng ngày, token kiểu cũ… | 43 | 26 | 12 | 1 |
| `shop-uninstall-reinstall-lifecycle` — Gỡ app, cài lại, store frozen — dữ liệu được giữ/khôi phục | Merchant gỡ app mà không mất dữ liệu kinh doanh (shop chỉ bị xoá mềm, phiên/token bị xoá, subscription bị huỷ) và khi cài lại thì lấy lại đúng bản ghi shop c… | 54 | 24 | 13 | 1 |
| `account-kill-switch` — Công tắc tài khoản shop (Security status) — chặn truy cập app | Nhân viên Mysbox bật/tắt quyền dùng app của một shop bằng Status ở mục Security: khi Tắt, merchant bị chặn portal và khách không mở được box, trong khi webho… | 26 | 16 | 11 | 0 |
| `gdpr-data-requests` — Yêu cầu GDPR (customers/data_request, customers/redact, shop/redact) | Khi Shopify chuyển tới app ba loại yêu cầu dữ liệu GDPR (khách yêu cầu dữ liệu, khách yêu cầu xoá, shop yêu cầu xoá 48 giờ sau khi gỡ app), yêu cầu được tiếp… | 9 | 7 | 4 | 4 |
| `admin-shop-management` — Màn Shops trong admin: tra cứu, chi tiết, sửa, row action | Support tra cứu shop (filter, shop đã gỡ), xem chi tiết shop (install status, plan, capacity, token, đơn, charge), sửa dữ liệu shop qua form Edit, và chạy đú… | 97 | 26 | 14 | 0 |

KB object-level: 19 (`kb.json`).

## Open questions

CONFLICT 5 · NEEDS_CONFIRMATION 35 · OPEN_ISSUE 39 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`install-and-onboarding` · `shop-connection-and-reauth` · `shop-uninstall-reinstall-lifecycle` · `account-kill-switch` · `gdpr-data-requests` · `admin-shop-management` · `merchant-app` · `kết nối shopify của shop: token, làm mới, re-auth`
