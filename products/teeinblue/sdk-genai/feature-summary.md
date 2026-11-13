# SDK Gen AI — cài đặt model và personalization Gen AI trên storefront
**Published context version:** 1

**Product:** teeinblue · **Object:** `sdk-genai` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `genai-model-settings` — Cài đặt model GenAI ở Gen AI Effects — chọn model, validate key, retirement và migration model cũ, toggle auto-switch | Merchant cấu hình model GenAI (Gemini, GPT) và API key dùng cho Gen AI Effects ở Extras > 3rd-party Services > Gen AI Effects: chọn và lưu model (gồm Nano Ba… | 16 | 19 | 16 | 0 |
| `genai-personalization-runtime` — GenAI Personalization Runtime (buyer-facing) — async generate, polling, minimum-filesize, select-previous-image; kích thước ảnh theo provider/Resolution, model dùng khi generate, fallback khi model down | Buyer (qua storefront/Live Preview) upload ảnh và/hoặc bấm Generate để hệ thống tạo ảnh bằng GenAI (Multiple Uploads hoặc Text to Image), theo dõi tiến trình… | 33 | 57 | 43 | 1 |
| `photo-genai-image-filter-runtime` — Gen AI image filter trên Photo layer (storefront) — ref image, hướng ảnh, tỉ lệ kết quả, hàng đợi job | Là buyer trên storefront, khi upload ảnh vào Photo layer có effect Gen AI image filter (kể cả Use Reference Image), tôi nhận được ảnh kết quả đúng hướng và p… | 6 | 8 | 4 | 0 |

KB object-level: 0 (`kb.json`).

## Open questions

CONFLICT 1 · NEEDS_CONFIRMATION 41 · OPEN_ISSUE 21 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`genai-model-settings` · `genai-personalization-runtime` · `photo-genai-image-filter-runtime` · `sdk-genai`
