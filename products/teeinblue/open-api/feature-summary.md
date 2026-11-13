# Object: Open API (product: teeinblue) — Feature Profile Summary
**Published context version:** 6

- **Object:** API cho merchant gọi bằng token: `/openapi/v1` (personal access token; xác thực, tra cứu layer image và clipart, upload asset) và route Open `/api/open/...` (guard `auth:public-api`, user API token; publish campaign), mở rộng theo quyết định operator 2026-11-13. Các nhóm route khác chưa có danh sách route đầy đủ và chưa có quan sát (đã biết `GET /openapi/v1/customizations/{uuid}` từ `_flows/storefront-sdk.md`, chưa gọi), xem OQ-open-api-013.
- **Quan sát:** staging, role `merchant-owner`, một account, một token, chỉ tầng API. Chưa có quan sát trên production hay tầng UI.
- **Knowledge:** 65 KB item (`open-api-asset-upload` 61, `open-api-campaign-publish` 4). `open-api-asset-upload`: 43 `OBSERVED_CURRENT`, 3 `INFERRED`, 13 `CONFIRMED_EXPECTED`/`MEDIUM` từ lời dev ở Jira TIB-5536 (10) và TIB-5709 (3), 2 `PROPOSED`/`LOW` từ rule spec-hub, chưa được Dev xác nhận. 75 check: 21 `STRONG`, 31 `BASELINE`, 23 `NONE`. Đa số hành vi quan sát chỉ có một sample. Hành vi quan sát được không phải expected requirement.
- **Giới hạn về account:** `GET /api/user` trả 401 với token Open API, nên account chỉ xác minh gián tiếp qua đường dẫn lưu trữ của asset. Store không xác minh được qua Open API. Xem OQ-open-api-008.
- **Open question:** 67 mục ở `open-questions.md`.

---

## `open-api-asset-upload` — Upload và tra cứu asset qua Open API

**Entry points:** `GET /openapi/v1/layer-images`, `/layer-image-categories`, `/clipart-categories`, `/cliparts`; `POST /openapi/v1/uploads`; `POST` và `DELETE` trên `/openapi/v1/layer-images`. Token trong biến `TIB_FULL_ACCESS_TOKEN`.

**Đã quan sát:**
1. Xác thực: có token thì route đọc trả 200; không token thì 401 hoặc 302 tới `/api/login` tuỳ header Accept.
2. Tra cứu: list layer image và clipart, phân trang cursor, đổi sang dạng page khi có search; `search` trên `cliparts` trả 422.
3. Upload: `POST /uploads`, PUT file lên `upload_url`, rồi finalize bằng `POST /layer-images` với `upload_id`. Finalize trước khi PUT trả 422.
4. Trùng tên: `on_duplicate=skip` trả lại asset đã có. Xoá: `DELETE` asset do chính token tạo trả 204.
5. Quota: header `x-ratelimit-limit` và `x-ratelimit-remaining` trên staging. Trong quan sát của object này chưa có lần vượt ngưỡng; asset-category KB-568 có ghi nhận của QA về 429 trên Open API, xem OQ-open-api-007.

**Theo lời dev (KB-043 đến KB-052), chưa quan sát đối chiếu:**
1. Lỗi: không token hoặc token revoked 401, thiếu quyền `assets:*` 403, id của account khác trên URL 404, `category_id`/`parent_id` của account khác trong body 422, hết daily limit hoặc vượt 60 request/phút 429.
2. Search: `search` dùng Typesense trên layer image, layer image category, clipart category; `name` là exact match, dùng cùng `search` trả 422; cliparts không có `search`.
3. Asset không có status failed: xử lý lỗi thì giữ `processing` với `url: null`. Layer image đang dùng không xoá được (400); clipart xoá vào Trash của portal, khôi phục trong 60 ngày.
4. Nguồn URL chỉ nhận http/https, chặn địa chỉ nội bộ và redirect, tối đa 64 MB, timeout 30 giây. Upload URL sống 5 phút, `upload_id` sống 30 phút, lỗi `upload_id` đều 422.
5. `on_duplicate`: `create` mặc định, `skip` trả item đã có, `replace` chỉ cho raster clipart; so theo tên, không theo nội dung.

**Giới hạn 128 MP (TIB-5709, theo Dev, KB-055, KB-057, KB-059):** `POST /layer-images` với `upload_id` hoặc `url` từ chối raster lớn hơn 128 MP hoặc có header không đọc được, trước khi tạo layer image; ảnh bằng hoặc dưới cap không bị từ chối. Presign `POST /uploads` vượt cap báo "file is too large to upload, maximum 128 megapixels.". Quan sát staging một lượt, không ghi build (KB-056, KB-058, KB-060, KB-061): 422 với message cap dưới `errors.url`/`errors.upload_id`, upload_id bị từ chối thành not found; header hỏng báo không đọc được kích thước; ảnh dưới cap vẫn processing rồi ready. Chưa chạy: ranh giới đúng 128 MP trên Open API, nhánh `file`, production (OQ-open-api-059..063). Đường upload qua tool MCP thuộc `mcp/mcp-layer-image-upload`.

**Theo spec-hub, chưa Dev xác nhận (KB-053, KB-054, `PROPOSED`):** 60 request/phút mỗi account; daily limit mặc định 1.000 clipart category, 4.000 clipart, 1.000 library image trong 24 giờ, chung cho portal, API và bulk upload; merchant xem được hạn mức, số còn lại và thời gian tới reset (OQ-open-api-057, OQ-open-api-058). Không dùng làm oracle.
**Chưa rõ về quota:** liên hệ giữa 60 request/phút, daily limit và header trên staging (OQ-open-api-049), nghĩa của câu trả lời "There's no reset." ở KB-049 (OQ-open-api-050). Không dùng 60 làm ngưỡng 429 trên staging. Mốc cửa sổ daily limit đang conflict ở asset-category, xem OQ-asset-category-031.
**Không dùng làm oracle:** KB-027, KB-033, KB-034 (`INFERRED`/`LOW`), vì host `oe-cdn.sgp1.digitaloceanspaces.com` và `cdn.ownego.com` chưa được xác nhận, xem OQ-open-api-001 và OQ-open-api-002.
**Conflict:** KB-007 `UNRESOLVED` trong CONF-open-api-001, khác artwork KB-057 về spec và token Open API, xem OQ-open-api-003.
**Chưa quan sát:** cô lập tenant, ability của token, nhánh `file` và `url` của finalize, vòng đời `upload_id` sau `expires_at`, việc dọn object tạm dưới `temporary-files/` (OQ-open-api-004, OQ-open-api-047).
**Checklist:** 75 check, 21 `STRONG`, 31 `BASELINE`, 23 `NONE` (CHK-069..CHK-075 cho giới hạn 128 MP). Mười check cần layer image tạo qua bước PUT giữ `NEEDS_CONFIRMATION` tới khi host được xác nhận (OQ-open-api-001). **KB:** KB-001 đến KB-061.

---

## `open-api-campaign-publish` — Lấy user API token và publish campaign qua Open API (mới từ CBS-163)

**Entry points:** `PUT /api/user/api-token` (phiên owner, sau xác nhận password; portal không có nút); `POST /api/open/instances/{instance}/campaigns/{campaign}/publish` với bearer là user API token.

**Theo Dev (TIB-5689, `CONFIRMED_EXPECTED`/MEDIUM, chỉ staging):** `PUT /api/user/api-token` trả chỉ plain token và thay token hiện tại của account (KB-062). Route publish dùng `auth:public-api` nên personal access token không dùng được; response là campaign có `campaign_instances`, không `artworks`, `campaign_artworks`, `campaign_products` (KB-064).
**Quan sát test case, không ghi build (KB-063, KB-065, `OBSERVED_CURRENT`/LOW):** PUT lần đầu 423, sau `confirm-password` thì 200 với body chuỗi token thuần; publish bằng user API token 200, row `campaign_instances` chọn theo `instance_id`, sản phẩm lên store; không bearer hoặc PAT thì 401; gọi từ trong trang portal (có Origin) thì 419 CSRF (OQ-open-api-064..066).
**Chưa chạy:** production, token cũ sau khi bị thay, token MCP làm bearer, dữ liệu account khác, campaign đã publish (OQ-open-api-067). Lấy token và publish là thao tác không hoàn tác dễ: cần operator đồng ý và dọn dẹp.
**Checklist:** 8 check, 3 `STRONG` (CHK-001, CHK-003, CHK-005), 5 `BASELINE`. **KB:** KB-062 đến KB-065.
