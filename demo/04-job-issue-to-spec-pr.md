# 04 — Job: Issue → Spec + Draft PR

**Job prompt (click Run):**

> Sử dụng Skill `issue-to-spec` của `ai-workflow`. Lấy Issue/backlog và quyết định đã chốt từ các bước 01–03, không bắt nhập lại Issue ID nếu context có. Kiểm tra GitHub repo demo, git state và approval/requirements. Tạo spec.md, plan.md, tasks.md theo Skill trong feature branch, chạy kiểm tra phù hợp, commit và mở **Draft Spec PR thật**. Không push thẳng main, không tạo PR trùng, không tự approve/merge. Lưu PR URL, HEAD SHA, artifact paths và NEXT_EXPECTED_STEP=05-review-spec. Nếu không có Issue/decisions hoặc thiếu quyền, BLOCKED.



## Quy tắc chung
- Thực thi thật, không mock Issues/PR/reviews/tests/releases; không nhận PASS nếu thiếu bằng chứng.
- Không hardcode tên ý tưởng, repository, project, đường dẫn máy, worker hay Issue ID.
- Đọc trạng thái Run/Task, handover và artifacts có thể truy cập trước khi thao tác. Nếu Chat và Job không chia sẻ context, lưu handover vào repository/đường dẫn chung có kiểm chứng; không giả định đồng bộ tự động.
- Phát hiện artifact/Issue/PR/tag trùng trước khi ghi hoặc retry; không tự tạo trùng.
- Không giả mạo approval; thao tác bên ngoài cần quyền phù hợp và phê duyệt chính xác khi policy yêu cầu.
- Kết thúc với STATUS (PASS/PARTIAL/BLOCKED/FAIL), references/URLs, commit SHA nếu có, evidence, blocker và NEXT_EXPECTED_STEP.
