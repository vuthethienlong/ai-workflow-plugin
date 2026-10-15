# 09 — Job: Independent Implementation Review

**Job prompt (click Run trên worker/session khác tác giả):**

> Sử dụng Skill `auto-review`. Lấy Implementation PR từ Job 08, xác minh reviewer độc lập, exact HEAD SHA, approved spec/AC và kết quả chạy tests thật. Review correctness, security, regression, TDD evidence và checklist; lưu findings và recommendation. Nếu issues còn tồn tại, trả về tác giả để fix/retest, rồi review HEAD mới. Chỉ khi PASS và PR HEAD không đổi mới recommend_approve/Ready for Review. Không human-approve/merge. NEXT_EXPECTED_STEP=10-human-code-approval.



## Quy tắc chung
- Thực thi thật, không mock Issues/PR/reviews/tests/releases; không nhận PASS nếu thiếu bằng chứng.
- Không hardcode tên ý tưởng, repository, project, đường dẫn máy, worker hay Issue ID.
- Đọc trạng thái Run/Task, handover và artifacts có thể truy cập trước khi thao tác. Nếu Chat và Job không chia sẻ context, lưu handover vào repository/đường dẫn chung có kiểm chứng; không giả định đồng bộ tự động.
- Phát hiện artifact/Issue/PR/tag trùng trước khi ghi hoặc retry; không tự tạo trùng.
- Không giả mạo approval; thao tác bên ngoài cần quyền phù hợp và phê duyệt chính xác khi policy yêu cầu.
- Kết thúc với STATUS (PASS/PARTIAL/BLOCKED/FAIL), references/URLs, commit SHA nếu có, evidence, blocker và NEXT_EXPECTED_STEP.
