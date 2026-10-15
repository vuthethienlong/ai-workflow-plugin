# 11 — Job: Build + Release

**Job prompt (click Run):**

> Truy xuất merged Implementation PR, SHA trên main và approval record bước 10. Chạy full tests/lint/build thật. Xác định semantic version/tag, release notes và artifacts. Trình bày release plan và **dừng xin human authorization rõ ràng để publish release** (ngoài approval PR). Chỉ sau khi được phép: kiểm tra duplicate tag/release trước khi retry, tạo Git tag và GitHub Release thật, đính kèm artifact khi được hỗ trợ. Lưu tag, commit, release URL, test logs và NEXT_EXPECTED_STEP=12-verify-release. Nếu quyền hoặc approval thiếu, BLOCKED; không đánh dấu PASS.



## Quy tắc chung
- Thực thi thật, không mock Issues/PR/reviews/tests/releases; không nhận PASS nếu thiếu bằng chứng.
- Không hardcode tên ý tưởng, repository, project, đường dẫn máy, worker hay Issue ID.
- Đọc trạng thái Run/Task, handover và artifacts có thể truy cập trước khi thao tác. Nếu Chat và Job không chia sẻ context, lưu handover vào repository/đường dẫn chung có kiểm chứng; không giả định đồng bộ tự động.
- Phát hiện artifact/Issue/PR/tag trùng trước khi ghi hoặc retry; không tự tạo trùng.
- Không giả mạo approval; thao tác bên ngoài cần quyền phù hợp và phê duyệt chính xác khi policy yêu cầu.
- Kết thúc với STATUS (PASS/PARTIAL/BLOCKED/FAIL), references/URLs, commit SHA nếu có, evidence, blocker và NEXT_EXPECTED_STEP.
