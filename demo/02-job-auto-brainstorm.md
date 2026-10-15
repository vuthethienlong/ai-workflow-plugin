# 02 — Job: Auto Brainstorm

**Job prompt (click Run):**

> Sử dụng Skill `auto-brainstorm` của `ai-workflow`. Truy xuất backlog/Issue references của bước 01 từ Orca state hoặc handover/artifact chung; không tự dựng ý tưởng mới. Phân tích sâu requirements, kiến trúc, alternatives, tradeoffs, risks, acceptance criteria, dependencies; cập nhật brainstorm summary và backlog proposal. Không tạo lại Issues hay PR, không làm thay bước manual brainstorming. Nếu không truy xuất được source, BLOCKED và nêu artifact còn thiếu. Lưu decisions, open questions và NEXT_EXPECTED_STEP=03-manual-brainstorm.



## Quy tắc chung
- Thực thi thật, không mock Issues/PR/reviews/tests/releases; không nhận PASS nếu thiếu bằng chứng.
- Không hardcode tên ý tưởng, repository, project, đường dẫn máy, worker hay Issue ID.
- Đọc trạng thái Run/Task, handover và artifacts có thể truy cập trước khi thao tác. Nếu Chat và Job không chia sẻ context, lưu handover vào repository/đường dẫn chung có kiểm chứng; không giả định đồng bộ tự động.
- Phát hiện artifact/Issue/PR/tag trùng trước khi ghi hoặc retry; không tự tạo trùng.
- Không giả mạo approval; thao tác bên ngoài cần quyền phù hợp và phê duyệt chính xác khi policy yêu cầu.
- Kết thúc với STATUS (PASS/PARTIAL/BLOCKED/FAIL), references/URLs, commit SHA nếu có, evidence, blocker và NEXT_EXPECTED_STEP.
