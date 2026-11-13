# MCP server
**Published context version:** 4

**Product:** teeinblue · **Object:** `mcp` · **Cập nhật cấu trúc:** 2026-11-13

## Features

| Feature | User goal | KB | Check | OQ | Known defect |
|---|---|---|---|---|---|
| `mcp-client-connection` — Kết nối MCP client tới MCP server Teeinblue | Merchant-owner kết nối một AI client (Claude Code, Claude Desktop, Codex) tới MCP server của Teeinblue: tìm endpoint, header Authorization và config theo từn… | 21 | 22 | 11 | 0 |
| `mcp-layer-image-upload` — Upload layer image qua tool MCP (URL và presigned), theo dõi processing → ready, giới hạn 128 MP | Là merchant (hoặc agent dùng token MCP của merchant), mình đưa ảnh vào thư viện layer image qua tool MCP — từ URL hoặc qua upload presigned — rồi theo dõi tớ… | 10 | 12 | 8 | 0 |
| `mcp-artwork-tools` — MCP tool của Artwork server: import-artwork-json-tool (cap mỗi lần gọi, quota theo ngày) và source của clipart category tạo qua MCP | Là merchant (hoặc agent dùng token MCP của merchant), mình import một artwork kèm clipart category và global option inline bằng một definition JSON qua MCP, … | 11 | 11 | 11 | 0 |

KB object-level: 0 (`kb.json`).

**Cập nhật CBS-163 (TIB-5689):** tạo token ở `/api-keys` và `/mcp` (`POST /api/tokens`) trả `accessToken` (id, name, abilities, last_used_at, expires_at, created_at; không `tokenable_id`/`tokenable_type`) và `plainTextToken` (KB-1658, `CONFIRMED_EXPECTED`/MEDIUM theo Dev); quan sát KB-1659: plain token hiện một lần, Regenerate trên `/mcp` xoá token cũ.

## Open questions

CONFLICT 1 · NEEDS_CONFIRMATION 25 · OPEN_ISSUE 4 — chi tiết trong `open-questions.md`.

## Tên cũ (alias)

`mcp-artwork-tools` · `import-artwork-json-tool` · `create-clipart-category-tool`
