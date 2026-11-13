# Object: Third-party Services (product: teeinblue) — Feature Profile Summary
**Published context version:** 2

- **Object:** trang cấu hình dịch vụ bên thứ ba cấp account của merchant, Extras > 3rd-party Services (`/extras/extra-services`): chọn dịch vụ xoá nền, API key của từng provider, các tab dịch vụ khác (Maps, Gen AI Effects, Cutout.Pro, ImagenHub, Emboss, Upload limit settings, Canva). Cấu hình lưu ở `private_config` của `GET /api/user`, áp cho mọi store của account. Gồm cả việc ngừng Remove.BG (TIB-5399) và migration seller khỏi Remove.BG.
- **Không thuộc:** chạy effect trong editor và warning thiếu key (`artwork/run-image-effects`, KB-816, KB-985; chưa giới hạn theo mốc shutdown, OQ-third-party-services-004); cách gắn effect Remove background vào layer photo (`artwork/layer-config-image`); upload và apply effect của buyer (`sdk/storefront-buyer-facing`, chỉ là đường chạy); chất lượng ảnh của từng provider.
- **Nguồn:** quan sát staging khi bootstrap (role `merchant-owner`, chỉ xem trang và đọc bundle portal) và nguồn Dev của TIB-5399 (Jira comment, 2026-10-12) nạp qua CCR.
- **Mốc shutdown Remove.BG:** production là 1 Dec 2026 9:00 CET, chưa tới mốc và chưa verify production. Hành vi sau mốc chỉ được verify trên staging bằng mốc giả lập do Dev đặt; không dùng làm expected cho production trước mốc. Bundle staging ngày 2026-11-13 vẫn compile mốc giả lập trong quá khứ (KB-1509, OQ-third-party-services-001), nên check trước mốc cần Dev đặt lại mốc.
- **Knowledge:** 48 KB item: 14 `CONFIRMED_EXPECTED`/`MEDIUM` (nguồn Dev), 30 `OBSERVED_CURRENT` (6 `MEDIUM`, 24 `LOW`), 4 `INFERRED`/`LOW`. 48 check: 15 `STRONG`, 18 `BASELINE`, 15 `NONE`. Không có conflict, không supersede.
- **Open question:** 26 mục ở `open-questions.md`. Check `BASELINE` chờ PO/Dev xác nhận ở OQ-third-party-services-010 và 017. Việc migration xoá key và đổi provider của seller chờ PO xác nhận ở OQ-third-party-services-025.

---

## `remove-background-provider` — Chọn dịch vụ xoá nền và trạng thái deprecation Remove.BG

**Entry points:** Extras > 3rd-party Services (`/extras/extra-services`), tab Remove Background.

**Expected theo nguồn Dev, trước mốc shutdown:** seller chưa từng dùng Remove.BG thấy Remove.BG có badge `Deprecate in Dec 1`, không chọn được (KB-1533); seller đang ở Remove.BG thấy nó được chọn nhưng greyed out (KB-1534), bật/tắt option "Use the photo's original size…" rồi Save vẫn ở Remove.BG (KB-1535), chuyển được sang provider khác nhưng không chuyển lại (KB-1536); API từ chối mọi yêu cầu chuyển seller sang Remove.BG (KB-1538); upload của buyer vẫn xoá nền bằng remove.bg (KB-1537).
**Expected theo nguồn Dev, sau mốc shutdown (chỉ mô phỏng trên staging):** Remove.BG và box key Remove.bg biến mất (KB-1539); upload của seller còn lưu Remove.BG dùng remover built-in Teeinblue ngay từ mốc (KB-1540); migration dry-run liệt kê seller liên quan mà không đổi gì (KB-1541), chạy thật chuyển seller ở Remove.BG sang Teeinblue và xoá key Remove.bg (KB-1542), chạy lại báo không còn seller (KB-1544); sau migration "Teeinblue" được chọn và remover built-in không có option original size (KB-1543).
**Khác biệt môi trường:** `ALTERNATIVE_SETUP` (KB-1546, `INFERRED`): trạng thái sau mốc chỉ dựng được khi Dev đặt `REMOVE_BG_SHUTDOWN_AT` và `VITE_REMOVE_BG_SHUTDOWN_AT` về quá khứ, rebuild portal, tạm dừng job hằng giờ và chạy migration; production chỉ có từ mốc thật.
**Đã quan sát:** 4 radio render và enabled: Removal.AI (badge "Recommended"), Cutout.pro, ImagenHub, Teeinblue (đang chọn); notice về remover built-in Teeinblue; nút Save của danh sách provider (KB-1501 đến KB-1505). Remove.BG không render trên staging ngày 2026-11-13 (KB-1506). Regression provider khác trước mốc theo test case không ghi build (KB-1545, `OBSERVED_CURRENT`/`LOW`, OQ-third-party-services-023).
**Chỉ thấy trong bundle portal staging, không render:** option Remove.BG disabled với badge, notice shutdown và ô key Remove.bg disabled; mốc shutdown compile trong quá khứ; option "Teeinblue X Removal.AI" và hằng `HIDE_BACKGROUND_REMOVER_ACCOUNT`; toggle `remove_bg_master_only` trong schema. KB-1507 đến KB-1509, KB-1511, KB-1512.
**Không dùng làm oracle:** KB-1510, KB-1532, KB-1513 (`INFERRED`), KB-1546 (`INFERRED`).
**Chưa rõ:** mốc staging (OQ-third-party-services-001), render trước mốc với từng nhóm account (002), thời điểm job hằng giờ (003), giới hạn thời gian của KB-816/KB-985 (004), điều kiện render và giá trị `remove_bg_master_only` sau migration (005, 022), Save/Check credits khi box key read-only (018), key còn lưu trước migration (019), mã lỗi và debug output khi API từ chối (020), không radio nào được chọn trước migration (021), cách dựng staging sau mốc (024), PO xác nhận migration xoá dữ liệu (025).
**Chưa quan sát:** Save provider và validation khi thiếu key, notice theo provider, option "Teeinblue X Removal.AI", role staff và account có provider khác (OQ-third-party-services-006 đến 009).
**Checklist:** 33 check: 12 `STRONG`, 12 `BASELINE`, 9 `NONE`.

## `provider-api-keys` — Quản lý API key của provider

**Entry points:** `/extras/extra-services`: section key Removal.AI ở tab Remove Background, tab Cutout.Pro, tab ImagenHub; box key Remove.bg trước mốc shutdown.

**Expected theo nguồn Dev:** trước mốc shutdown, với seller đang ở Remove.BG, ô key Remove.bg read-only và có notice shutdown (KB-1547). Sau mốc shutdown, key Remove.bg đã lưu bị xoá cho mọi seller, kể cả seller đã tự đổi provider trước mốc (KB-1548); chỉ mô phỏng trên staging, production chưa verify (OQ-third-party-services-026).
**Đã quan sát:** ô key Removal.AI và Cutout.pro rỗng kèm help text, Save và Check credits enabled; ô key ImagenHub hiển thị key đã lưu dạng mask (4 ký tự đầu, 4 ký tự cuối) trong input text, không có Check credits; trên account đã quan sát, field key của provider đã có key nằm trong `private_config` của `GET /api/user`, field của Removal.AI/Cutout.pro vắng khi ô rỗng (một trạng thái, chưa tổng quát hoá). KB-1514 đến KB-1518.
**Chưa rõ:** `GET /api/user` gửi key đầy đủ hay đã mask về client (OQ-third-party-services-011).
**Chưa quan sát:** Save key và validation, Check credits, đổi/xoá key, role staff, trang khi đã có key Removal.AI/Cutout.pro (OQ-third-party-services-012 đến 016).
**Checklist:** 15 check: 3 `STRONG`, 6 `BASELINE`, 6 `NONE`.

**KB mức object:** KB-1519 đến KB-1531 (entry point và phạm vi account, 8 tab chuyển phía client không phát request, request khi tải trang, `private_config` cấp account, cấu trúc các tab khác, mẫu option "Deprecated" ở Gen AI Effects, quyền xem ở role owner).
