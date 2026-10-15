# 03 — Worker Chat: Manual Brainstorm

**Đây là chat với người dùng, không phải Job tự chạy.**

> Sử dụng `manual-brainstorm` của `ai-workflow`. Đọc backlog bước 01, brainstorm bước 02 và handover thật. Trình bày các phương án và quyết định còn mở; thảo luận với tôi, không tự giả lập câu trả lời của tôi. Cập nhật quyết định thiết kế, acceptance criteria, phạm vi và các artifact dùng chung. Khi tôi xác nhận chốt, ghi rõ ai duyệt, artifact revision và NEXT_EXPECTED_STEP=04-issue-to-spec. Nếu chưa chốt, dừng.



## Quy tắc chung
- Thực thi thật, không mock Issues/PR/reviews/tests/releases; không nhận PASS nếu thiếu bằng chứng.
- Không hardcode tên ý tưởng, repository, project, đường dẫn máy, worker hay Issue ID.
- Đọc trạng thái Run/Task, handover và artifacts có thể truy cập trước khi thao tác. Nếu Chat và Job không chia sẻ context, lưu handover vào repository/đường dẫn chung có kiểm chứng; không giả định đồng bộ tự động.
- Phát hiện artifact/Issue/PR/tag trùng trước khi ghi hoặc retry; không tự tạo trùng.
- Không giả mạo approval; thao tác bên ngoài cần quyền phù hợp và phê duyệt chính xác khi policy yêu cầu.
- Kết thúc với STATUS (PASS/PARTIAL/BLOCKED/FAIL), references/URLs, commit SHA nếu có, evidence, blocker và NEXT_EXPECTED_STEP.
