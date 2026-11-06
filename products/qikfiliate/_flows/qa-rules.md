# Trình tự test và cách kết luận

## Trình tự cho một feature

1. Chọn feature: từ khoá sang `object_key` qua `_registry.json`, trạng thái qua `manifest.json`.
2. Đọc `<object>/feature-summary.md` → `features/<feature>/profile.json` → `checklists/<feature>.json` → `open-questions.md` lọc theo feature → guide mục 5.
3. Dựng data theo `feature-entry.md`, sau khi xác minh account.
4. Chạy từng check: `precondition` → `steps` → `observation_point` → so `expected_result`.
5. Ghi evidence: instance, tên biến account (không ghi email), id data, thời điểm, screenshot hoặc response đã che.
6. Dọn data theo guide mục 6.

## Kết luận mỗi check

| Tình huống | Kết luận |
|---|---|
| `status: READY`, khớp `expected_result` | `PASS` |
| `status: READY`, oracle `STRONG`, lệch, `confirmation_source.type` là `spec_doc` / `po_dev_confirm` / `test_case` | `FAIL` |
| `status: READY`, lệch, nguồn chỉ `dev_doc` | `SUSPECTED_FAIL`: ghi đủ evidence, đối chiếu PO/spec rồi mới chốt bug, kể cả khi manifest ghi `usable_as_oracle: true` |
| Check mô tả UI admin cũ (`routes-api.md`) | `OUTDATED_CHECK`: test lại mục tiêu của check trên UI mới, ghi cả hai |
| `status: NEEDS_CONFIRMATION`, oracle `NONE`, hoặc item `CONFLICTED` / `UNRESOLVED` | Chỉ ghi `OBSERVED: <hành vi thật>`, không kết luận |
| Item có `scope.brand` khác brand đang test | `NOT_APPLICABLE` |
| `environment_differences` có `NOT_TESTABLE` | `NOT_APPLICABLE` trên môi trường đó |
| Không quan sát được, thiếu quyền, thiếu data | `NOT_COVERED` hoặc `BLOCKED`, nêu rõ thiếu gì |

## Đừng hiểu sai checklist

- `applicability.environment: documented` chỉ nói nguồn là tài liệu, không có nghĩa là không chạy được trên staging.
- `steps` có thể nói theo hàm code, như `canCreateByUser`: quan sát qua UI hoặc API tương ứng.

## Sau khi test

- Hành vi thật khác knowledge, hoặc đã xác nhận một Open Question: gửi CCR (`consumer-guide.md` §5).
- Bug thật: báo trên Testlane. Không tự tạo hay comment Jira, không nhắn kênh ngoài khi operator chưa đồng ý.
- Guide hoặc flow sai, hoặc gặp `[?]` đã có đáp án: gửi CCR khối C.
