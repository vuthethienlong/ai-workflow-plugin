# 07 — Job: Auto Implement + TDD

**Job prompt (click Run):**

> Sử dụng `auto-implement` kết hợp `issue-tdd` của `ai-workflow`. Lấy approved spec chính xác, merged Spec PR và Issue từ handover/repository. Nếu thiếu approval hoặc Spec PR chưa merge, BLOCKED. Triển khai code trên feature branch bằng TDD RED → GREEN → REFACTOR; chạy tests thật, lint/build nếu có; lưu logs/evidence, mapping acceptance criteria, commit SHA và handover. **Không tạo Implementation PR trong Job 07** để Job 08 phụ trách riêng. Không thay đổi main. NEXT_EXPECTED_STEP=08-implementation-pr.



## Quy tắc chung
- Thực thi thật, không mock Issues/PR/reviews/tests/releases; không nhận PASS nếu thiếu bằng chứng.
- Không hardcode tên ý tưởng, repository, project, đường dẫn máy, worker hay Issue ID.
- Đọc trạng thái Run/Task, handover và artifacts có thể truy cập trước khi thao tác. Nếu Chat và Job không chia sẻ context, lưu handover vào repository/đường dẫn chung có kiểm chứng; không giả định đồng bộ tự động.
- Phát hiện artifact/Issue/PR/tag trùng trước khi ghi hoặc retry; không tự tạo trùng.
- Không giả mạo approval; thao tác bên ngoài cần quyền phù hợp và phê duyệt chính xác khi policy yêu cầu.
- Kết thúc với STATUS (PASS/PARTIAL/BLOCKED/FAIL), references/URLs, commit SHA nếu có, evidence, blocker và NEXT_EXPECTED_STEP.
