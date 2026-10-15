# 12 — Job: Verify Release

**Job prompt (click Run):**

> Đọc release URL, tag và commit SHA thật từ Job 11. Xác minh GitHub Release tồn tại, tag trỏ đúng commit được duyệt, assets/notes đúng yêu cầu và build/test verification evidence có thật. Nếu có môi trường phù hợp, kiểm tra artifact chạy được; không giả định có deploy nếu chỉ tạo GitHub Release. Báo PASS/PARTIAL/BLOCKED/FAIL kèm tất cả URLs, SHAs, checks, giới hạn và NEXT_EXPECTED_STEP=done.



## Quy tắc chung
- Thực thi thật, không mock Issues/PR/reviews/tests/releases; không nhận PASS nếu thiếu bằng chứng.
- Không hardcode tên ý tưởng, repository, project, đường dẫn máy, worker hay Issue ID.
- Đọc trạng thái Run/Task, handover và artifacts có thể truy cập trước khi thao tác. Nếu Chat và Job không chia sẻ context, lưu handover vào repository/đường dẫn chung có kiểm chứng; không giả định đồng bộ tự động.
- Phát hiện artifact/Issue/PR/tag trùng trước khi ghi hoặc retry; không tự tạo trùng.
- Không giả mạo approval; thao tác bên ngoài cần quyền phù hợp và phê duyệt chính xác khi policy yêu cầu.
- Kết thúc với STATUS (PASS/PARTIAL/BLOCKED/FAIL), references/URLs, commit SHA nếu có, evidence, blocker và NEXT_EXPECTED_STEP.
