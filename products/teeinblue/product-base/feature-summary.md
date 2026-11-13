# Product Base
**Published context version:** 14

**Product:** teeinblue · **Object:** `product-base` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `mockup-attachment` — Upload va Gan Mockup cho Product Base | La owner, upload anh mockup moi hoac chon tu media library, va gan cho product base/variant de preview san pham. | 15 | 17 | 17 | 0 |
| `printarea-definition` — Dinh nghia va quan ly Printarea cua Product Base | La owner, tao/sua/xoa cac vung in (printarea) tren mot product base, de xac dinh noi thiet ke/artwork se duoc dat khi in san pham. | 31 | 33 | 23 | 0 |
| `product-base-browse` — Duyet va tim kiem danh sach Product Base | La owner, tim va xem danh sach product base hien co (theo tab Active/Archived, filter, search, tuy bien view list/grid) de tu do quan ly, tao moi, hoac thao … | 23 | 21 | 9 | 0 |
| `product-base-campaign-link` — Lien ket Product Base voi Campaign va Dong bo (Update campaign) | La owner, lien ket mot product base vao campaign, xem cac campaign dang dung mot product base, va (ngoai SDK) dong bo thay doi cua product base sang campaign… | 15 | 17 | 16 | 1 |
| `product-base-create` — Tao moi Product Base (thu cong) | La owner, tao moi mot product base qua form /products/new, voi validation toi thieu, de co ban ghi san sang cau hinh printarea/variant/mockup tiep theo. | 13 | 14 | 6 | 0 |
| `product-base-identity` — Sua thong tin co ban (Basic information) cua Product Base | La owner, xem va cap nhat thong tin co ban (title/label/tags/fulfillment/description/thumbnail) cua mot product base da ton tai. | 10 | 12 | 9 | 0 |
| `product-base-lifecycle` — Vong doi Product Base (Archive / Duplicate / Delete) | La owner, quan ly vong doi cua mot product base: archive/unarchive, nhan ban (duplicate), hoac xoa han khi khong con dung. | 10 | 10 | 6 | 0 |
| `variant-add-to-campaigns` — Thêm nhiều variant của Product Base vào campaign (bulk Add to campaigns) | Merchant chọn nhiều variant trong bảng Variants của Product Base rồi thêm chúng một lần vào các campaign đang dùng product base đó, các variant được thêm ở t… | 17 | 23 | 12 | 5 |
| `variant-catalog` — Quan ly Variant Catalog cua Product Base | La owner, quan ly catalog variant (SKU, mau/size, gia, ton kho) cua mot product base: them nhanh variant, cau hinh hien thi mau/size, gan printarea rieng the… | 14 | 17 | 10 | 0 |
| `provider-catalog-import` — Kết nối provider, import catalog và option bắt buộc | Merchant/owner tạo nhanh một Product Base bằng cách import một item từ catalog có sẵn của nhà in đã kết nối (fulfillment provider), kế thừa title/description… | 13 | 12 | 14 | 0 |

KB object-level: 0 (`kb.json`).

## Open questions

CONFLICT 2 · NEEDS_CONFIRMATION 101 · OPEN_ISSUE 19 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`provider-required-options` · `fulfillment-provider-connection`
