# 08 — Job: Create Implementation Draft PR

**Job prompt (click Run):**

> Đọc handover và feature branch code từ Job 07. Xác minh test evidence, commits, base branch và approved spec. Kiểm tra đã có Implementation PR cho branch chưa; nếu có, dùng lại và cập nhật evidence, không tạo trùng. Nếu chưa, push commit được phép và tạo **Draft Pull Request thật** chứa implementation + tests, liên kết Issue và Spec PR. Không tự review như reviewer độc lập, không approve/merge. Lưu PR URL, HEAD SHA, test evidence, NEXT_EXPECTED_STEP=09-review-implementation.



## Quy tắc chung
- Thực thi thật, không mock Issues/PR/reviews/tests/releases; không nhận PASS nếu thiếu bằng chứng.
- Không hardcode tên ý tưởng, repository, project, đường dẫn máy, worker hay Issue ID.
- Đọc trạng thái Run/Task, handover và artifacts có thể truy cập trước khi thao tác. Nếu Chat và Job không chia sẻ context, lưu handover vào repository/đường dẫn chung có kiểm chứng; không giả định đồng bộ tự động.
- Phát hiện artifact/Issue/PR/tag trùng trước khi ghi hoặc retry; không tự tạo trùng.
- Không giả mạo approval; thao tác bên ngoài cần quyền phù hợp và phê duyệt chính xác khi policy yêu cầu.
- Kết thúc với STATUS (PASS/PARTIAL/BLOCKED/FAIL), references/URLs, commit SHA nếu có, evidence, blocker và NEXT_EXPECTED_STEP.
