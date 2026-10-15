# 05 — Job: Independent Spec Review

**Job prompt (click Run trên worker/session khác tác giả):**

> Sử dụng Skill `auto-review` của `ai-workflow`. Xác minh reviewer độc lập với tác giả PR bước 04. Truy xuất Draft Spec PR, đọc trạng thái và exact HEAD SHA, review acceptance criteria, spec/plan/tasks, security, tests/evidence và hoàn thành review checklist. Ghi findings có severity và recommendation; kiểm tra HEAD SHA lại trước khi thay đổi trạng thái PR. Nếu còn findings hoặc SHA thay đổi, báo changes_required/stale và gửi lại tác giả sửa, rồi re-review. Khi PASS, recommend_approve và có thể mark Ready for Review nếu quyền/policy cho phép; tuyệt đối không human-approve hay merge. NEXT_EXPECTED_STEP=06-human-spec-approval.



## Quy tắc chung
- Thực thi thật, không mock Issues/PR/reviews/tests/releases; không nhận PASS nếu thiếu bằng chứng.
- Không hardcode tên ý tưởng, repository, project, đường dẫn máy, worker hay Issue ID.
- Đọc trạng thái Run/Task, handover và artifacts có thể truy cập trước khi thao tác. Nếu Chat và Job không chia sẻ context, lưu handover vào repository/đường dẫn chung có kiểm chứng; không giả định đồng bộ tự động.
- Phát hiện artifact/Issue/PR/tag trùng trước khi ghi hoặc retry; không tự tạo trùng.
- Không giả mạo approval; thao tác bên ngoài cần quyền phù hợp và phê duyệt chính xác khi policy yêu cầu.
- Kết thúc với STATUS (PASS/PARTIAL/BLOCKED/FAIL), references/URLs, commit SHA nếu có, evidence, blocker và NEXT_EXPECTED_STEP.
