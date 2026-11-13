# Product guide — ImagenHub

Bản đồ của product: có gì, ở đâu, test được không. Mọi bước đều đọc file này. Tối đa 10 KB. Định nghĩa: contract §5c.

- Đúng phải là gì: `<object>/features/<feature>/kb.json`, `checklists/`.
- Làm thế nào: `_flows/` (chưa có file nào; thêm qua khối C của CCR khi có cách thao tác đã verify).
- Biến env: chưa có `_env.example` (product chưa có môi trường explore).

Không dùng guide làm expected result. Không ghi giá trị credential, id, tên store.

## 1. Product
ImagenHub là Generative Media API: một endpoint `/process` gọi nhiều model ảnh AI (OpenAI, Google, Flux, Recraft, model nội bộ Teeinblue), kèm portal quản lý. Teeinblue tích hợp native qua layer Photo Upload với effect "[ImagenHub] AI Effect".

Luồng chính: chọn model (hoặc dựng template = model + prompt/biến + input mặc định + post-processing + fallback) → gọi API hoặc chạy ở Playground/Batch → task chạy và trả ảnh output → xem Task history, webhook/alert.

Thuật ngữ: **template** = recipe tái dùng, gọi qua `template_id`; **BYOK** = key provider của chính khách; **task** = một yêu cầu generate.

## 2. Object
Từ khoá ticket sang object: `_registry.json`. Feature của object: `<object>/feature-summary.md`. Không liệt kê feature key ở đây.

| Object | Phạm vi | Không thuộc |
|---|---|---|
| `templates` | Template, biến, post-processing, fallback template, run history, tỉ lệ upload động, thiết lập AI Effect cho Teeinblue | Model catalog (`models`) |
| `tasks` | Yêu cầu generate, vòng đời task, ảnh output, Task history | Cấu hình template |
| `models` | Catalog model/provider và Playground chạy model trực tiếp | Template dùng model |
| `bulk-tools` | Batch (một template cho nhiều ảnh) và Design (mockup sang file in), đều Beta | Task đơn lẻ |
| `developer-settings` | API keys, Provider keys (BYOK), Webhook, Alert, MCP server | Org và credit |
| `organization-billing` | Organization, member, role, subscription, credit, rate limit, analytics | Key kỹ thuật (`developer-settings`) |

## 3. Môi trường
Chưa có môi trường explore cho product này (`explore_enabled: false`): context chỉ đến từ tài liệu (dev doc, QA tự biên soạn, business rule), chưa có quan sát runtime do pipeline thực hiện. Chưa có biến env nào được khai. Mọi claim mang `scope.environment: documented`.

## 4. Test được gì
Chưa có khác biệt môi trường nào được ghi (`environment_differences` trống ở mọi feature). Khi test trên môi trường thật mà thấy khác tài liệu thì báo qua CCR, không sửa expected theo cảm tính.

Nhãn: `expected-unconfirmed` cho mục còn NEEDS_CONFIRMATION (run history có hiện run Error không, retry/timeout của fallback A, URL ảnh công khai vĩnh viễn). Các mảng provider keys, organization, webhooks/alerts, subscription, MCP chỉ có mức tóm tắt từ doc chính thức: coi là chưa đủ để kết luận PASS/FAIL.

## 5. Bẫy làm sai kết luận
| Dấu hiệu | Cách hiểu |
|---|---|
| Rule fallback template (IGH-226) | Có phần PO/Dev đã chốt và phần chỉ verify trên staging; đọc nguồn từng KB |
| Task lỗi hoặc provider chậm | Có thể do provider ngoài, kiểm `scope` và trạng thái task trước khi kết luận |
| Tính năng Beta (Batch, Design) | Hành vi chưa ổn định, không coi lệch là bug ngay |

## 6. Mutation guard
Chưa có môi trường explore nên chưa có quy tắc riêng. Khi test thật: không dùng production, tránh chạy generate hàng loạt (tốn credit), không dùng provider key thật của khách, che API key và webhook secret trong log.
