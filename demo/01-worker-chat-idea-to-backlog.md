# 01 — Worker Chat: Idea → Backlog + Issue thật

**Không tạo Orca Job ở bước này. Mở Worker Chat và gửi prompt:**

> Sử dụng Skill `idea-to-backlog` của `ai-workflow`. Hỏi tôi ý tưởng cần phát triển; không hardcode idea, repo hoặc project. Đọc kết quả preflight bước 00, lấy RUN_ID và HANDOVER_LOCATION đã xác minh; nếu không tìm thấy hoặc không thể truy cập bằng worker hiện tại thì BLOCKED_HANDOVER, không tự tạo run mới hoặc đoán vị trí. cùng tôi tạo backlog ban đầu gồm Epic/Features/Issues/Tasks, acceptance criteria, dependencies. Xác định ADO MCP/project từ preflight; nếu ADO không sẵn sàng, chỉ dùng GitHub Issues nếu tôi đã cho phép fallback. **Hiển thị trước nội dung và tất cả thao tác CREATE/LINK dự kiến, chờ human approval chính xác** rồi mới tạo những Issue thật (cùng hierarchy nếu đã approve). Kiểm tra trùng/uncertain retry; đọc lại để xác minh ID, URL, type, project và revision. Lưu references và handover tại đúng HANDOVER_REPO/BRANCH/RUN_ID của bước 00, read-back context.md để xác minh Job 02 có thể tìm. Nếu không có approval hoặc không có issue backend khả dụng, dừng PENDING_HUMAN_APPROVAL/BLOCKED; không giả lập Issue. Không tự chạy bước 02.

> NEXT_EXPECTED_STEP=02-auto-brainstorm.

## Handover
Lưu `RUN_ID`, `HANDOVER_REPO`, `HANDOVER_BRANCH`, `HANDOVER_LOCATION`, `ISSUE_BACKEND`, `ISSUE_IDS/URLS`, `SOURCE_REVISIONS`, `BACKLOG_ARTIFACT`, `APPROVAL_EVIDENCE`, `NEXT_EXPECTED_STEP`. Không lưu credentials.
