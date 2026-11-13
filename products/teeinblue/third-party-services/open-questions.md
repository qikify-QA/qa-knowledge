# Open Questions — Third-party Services

Các mục dưới đây còn mở. Không dùng phần còn mở làm expected result.

## Tóm tắt

| Loại | Số lượng |
|---|---|
| NEEDS_CONFIRMATION | 26 |
| **Tổng** | **26** |

## OQ-third-party-services-001 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-001","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Bundle portal staging compile VITE_REMOVE_BG_SHUTDOWN_AT = 2026-11-01T00:00:00Z, trong khi notice trong bundle nói Remove.BG ngừng ngày \"1 Dec 2026\". Staging có cố ý đặt mốc trong quá khứ không, mốc production là gì, và bundle có ẩn Remove.BG khi đã qua mốc như cách đọc code ở KB-1510 không? Mốc production chưa quan sát (KB-1509, KB-1508, KB-1510)."}
```

## OQ-third-party-services-002 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-002","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Trước mốc shutdown, trang có render option Remove.BG disabled, badge \"Deprecate in Dec 1\", notice shutdown và ô key Remove.bg disabled cho mọi account hay chỉ account đang dùng/có key Remove.BG? Run chỉ thấy các phần này trong bundle staging, chưa thấy render vì staging đã qua mốc (KB-1506, KB-1507, KB-1508)."}
```

## OQ-third-party-services-003 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-003","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Migration seller khỏi Remove.BG (tự chuyển sang remover built-in Teeinblue sau shutdown, như notice trong bundle nêu) chưa được quan sát: cơ chế, thời điểm chạy, điều kiện, endpoint migrate nội bộ và biến env REMOVE_BG_SHUTDOWN_AT phía API (chỉ tên biến) cần Dev xác nhận (KB-1508)."}
```

## OQ-third-party-services-004 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-004","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"artwork/run-image-effects KB-816 và KB-985 liệt kê remove.bg là remover chọn được, trong khi trang staging hiện không render Remove.BG (đã qua mốc shutdown của staging). Hai item đó có cần giới hạn theo thời gian (trước/sau shutdown) không? Chưa dựng conflict, artwork chưa đổi (KB-1513, KB-1506)."}
```

## OQ-third-party-services-005 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-005","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Toggle remove_bg_master_only (\"Use the photo's original size for both Preview & Production file\") có trong schema bundle và private_config nhưng không render ở tab Remove Background khi provider là Teeinblue. Điều kiện render là gì (theo provider?), và nó có liên quan checkbox \"(for FaceCutout)\" ở tab Cutout.Pro không (KB-1512, KB-1529)?"}
```

## OQ-third-party-services-006 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-006","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Chọn provider khác rồi Save: request nào được gửi, phản hồi/toast ra sao, giá trị nào lưu vào private_config; chọn Removal.AI hoặc Cutout.pro khi chưa có key thì bị chặn hay vẫn lưu, báo gì? Save chưa được bấm trong run (KB-1504)."}
```

## OQ-third-party-services-007 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-007","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Notice dưới danh sách provider và section ô key có đổi theo provider đang chọn không? Run không click radio; bundle chỉ cho thấy section key gắn với removal.ai, remove.bg, cutout.pro."}
```

## OQ-third-party-services-008 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-008","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Giá trị hằng HIDE_BACKGROUND_REMOVER_ACCOUNT, việc option \"Teeinblue X Removal.AI\" (badge \"Premium & above\") có bị ẩn theo ngày tạo account như cách đọc code ở KB-1532 không, và điều kiện plan của option là gì? Option không hiện trên account explorer (KB-1511, KB-1532)."}
```

## OQ-third-party-services-009 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-009","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Role staff khác owner, hoặc account đã lưu provider khác (Removal.AI, Cutout.pro, ImagenHub) hoặc có key, thì tab Remove Background hiển thị và lưu thế nào? Chỉ quan sát role owner với provider Teeinblue (KB-1531)."}
```

## OQ-third-party-services-010 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-010","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Các check BASELINE của remove-background-provider chỉ dựa trên quan sát staging một account; cần PO/Dev xác nhận đây là hành vi đúng trước khi dùng làm expected."}
```

## OQ-third-party-services-011 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-011","type":"NEEDS_CONFIRMATION","feature_id":"provider-api-keys","summary":"GET /api/user trả các field API key provider trong private_config; capture đã che giá trị nên chưa biết client nhận key đầy đủ hay đã mask. Ô key trên trang hiển thị key đã lưu dạng mask (4 ký tự đầu, 4 ký tự cuối) trong input text. Việc mask chỉ ở UI hay cả ở API, và đó có phải thiết kế có chủ đích (KB-1517, KB-1518)?"}
```

## OQ-third-party-services-012 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-012","type":"NEEDS_CONFIRMATION","feature_id":"provider-api-keys","summary":"Save key Removal.AI/Cutout.pro gọi request nào, validate định dạng key ra sao (rỗng, khoảng trắng, sai định dạng), báo thành công/lỗi thế nào? Chưa bấm Save (KB-1515, KB-1516)."}
```

## OQ-third-party-services-013 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-013","type":"NEEDS_CONFIRMATION","feature_id":"provider-api-keys","summary":"Check credits (GET /api/user/credit) trả gì với key hợp lệ, key sai và ô rỗng? Chưa bấm (KB-1515, KB-1516)."}
```

## OQ-third-party-services-014 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-014","type":"NEEDS_CONFIRMATION","feature_id":"provider-api-keys","summary":"Đổi hoặc xoá key rồi Save và reload: ô key và private_config thay đổi thế nào, field key có luôn vắng khỏi private_config khi ô rỗng không (KB-1518)?"}
```

## OQ-third-party-services-015 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-015","type":"NEEDS_CONFIRMATION","feature_id":"provider-api-keys","summary":"Role staff không phải owner có xem hoặc sửa được API key ở 3rd-party Services không? Chỉ role owner được quan sát (KB-1531)."}
```

## OQ-third-party-services-016 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-016","type":"NEEDS_CONFIRMATION","feature_id":"provider-api-keys","summary":"Trang hiển thị thế nào khi account đã có key Removal.AI hoặc Cutout.pro (mask, nút Check credits)? Account explorer chưa có key hai provider này."}
```

## OQ-third-party-services-017 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-017","type":"NEEDS_CONFIRMATION","feature_id":"provider-api-keys","summary":"Các check BASELINE của provider-api-keys chỉ dựa trên quan sát staging một account; cần PO/Dev xác nhận đây là hành vi đúng trước khi dùng làm expected."}
```

## OQ-third-party-services-018 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-018","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Trước mốc shutdown, với seller đang ở Remove.BG: CCR ghi quan sát QA trên staging rằng nút Save và Check credits trong box Remove.bg vẫn bấm được dù ô key read-only, và Save khi key không đổi giữ nguyên key. Đây có phải hành vi đúng không, hay Save phải bị khoá (KB-1534, KB-1547)?"}
```

## OQ-third-party-services-019 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-019","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Seller đang ở Remove.BG tự chuyển sang provider khác trước mốc shutdown (KB-1536): key Remove.bg có còn trong private_config cho tới khi migration chạy không? Nguồn Dev chỉ nói key bị xoá cho mọi seller từ mốc shutdown (KB-1548)."}
```

## OQ-third-party-services-020 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-020","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Khi API từ chối chuyển seller sang Remove.BG (KB-1538), staging trả HTTP 422 với message \"Remove.BG is no longer available as a background remover.\" và response kèm debug output (file/line/trace). Mã lỗi và message có phải expected không, và debug output có xuất hiện trên production không? Dev chưa xác nhận."}
```

## OQ-third-party-services-021 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-021","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Sau mốc shutdown nhưng trước khi migration cập nhật setting, seller còn lưu Remove.BG mở tab Remove Background thì không radio nào được chọn (quan sát staging với mốc giả lập, ngoài nguồn Dev). Đây có phải hành vi đúng không, và trên production khoảng này kéo dài bao lâu (KB-1539)?"}
```

## OQ-third-party-services-022 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-022","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Sau migration, giá trị remove_bg_master_only đã lưu của seller từng ở Remove.BG được xử lý thế nào: giữ, reset hay bị bỏ qua với remover built-in? Nguồn Dev chỉ nói option không có cho remover Teeinblue (KB-1543, KB-1512; liên quan OQ-third-party-services-005)."}
```

## OQ-third-party-services-023 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-023","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Regression trước shutdown của Removal.AI, Cutout.pro, Teeinblue (chọn, Save, giữ sau reload, ô key sửa được, upload xoá nền) chỉ dựa trên test case PASS staging không ghi build (KB-1545). Cần PO/Dev xác nhận là expected, kèm build đã test. Seller ở Cutout.pro hoặc ImagenHub còn key Remove.bg được migration xử lý ra sao (KB-1542 chỉ nêu Removal.AI)?"}
```

## OQ-third-party-services-024 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-024","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Cách dựng trạng thái sau shutdown trên staging (KB-1546: Dev đặt REMOVE_BG_SHUTDOWN_AT và VITE_REMOVE_BG_SHUTDOWN_AT về quá khứ, rebuild portal, tạm dừng job hằng giờ, Dev chạy migration; seller ở Remove.BG hoặc còn key Remove.bg dựng qua DB) chỉ là lời kể trong CCR, chưa có trích nguyên văn. Cần Dev xác nhận cách test này đúng và đủ; production không test được trước 1 Dec 2026 9:00 CET."}
```

## OQ-third-party-services-025 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-025","type":"NEEDS_CONFIRMATION","feature_id":"remove-background-provider","summary":"Migration thật đổi provider của seller sang Teeinblue và xoá key Remove.bg đã lưu của mọi seller (KB-1542, KB-1548): mất dữ liệu cấu hình của merchant, impact HIGH. Nguồn là Dev; cần PO xác nhận đây là hành vi đúng (kể cả việc xoá key của seller đã tự đổi provider trước mốc)."}
```

## OQ-third-party-services-026 — NEEDS_CONFIRMATION

```json
{"oq_id":"OQ-third-party-services-026","type":"NEEDS_CONFIRMATION","feature_id":"provider-api-keys","summary":"Hành vi ô key Remove.bg và việc xoá key sau shutdown (KB-1547, KB-1548) mới chỉ verify trên staging, phần sau shutdown bằng mốc giả lập. Production chưa tới mốc 1 Dec 2026 9:00 CET và chưa verify; cần verify production sau mốc."}
```
