# 01 — Worker Chat: Idea → Backlog

**Không tạo Job cho bước này.** Mở Worker Chat và gửi nội dung sau.

> Sử dụng Skill `idea-to-backlog` của plugin `ai-workflow`. Hỏi tôi ý tưởng muốn phát triển, mục tiêu và giới hạn còn thiếu. Cùng tôi xây dựng backlog gồm Epic/Features/Issues/Tasks, acceptance criteria, dependencies. Không dùng ý tưởng hoặc repo demo hardcode. Đọc context/handover hiện có, lưu proposal vào artifact mà Job 02 có thể đọc. Cho tôi duyệt nội dung trước khi ghi Issue thật. Khi được duyệt và đã xác minh repository/project, kiểm tra trùng và tạo Issues thật qua ADO MCP nếu có; nếu ADO chưa kết nối, đề xuất dùng GitHub Issues thật và xin tôi đồng ý rõ ràng trước khi tạo. Trả về Issue URL/ID và read-back evidence. Không tự chạy bước 02. NEXT_EXPECTED_STEP=02-auto-brainstorm.



## Quy tắc chung
- Thực thi thật, không mock Issues/PR/reviews/tests/releases; không nhận PASS nếu thiếu bằng chứng.
- Không hardcode tên ý tưởng, repository, project, đường dẫn máy, worker hay Issue ID.
- Đọc trạng thái Run/Task, handover và artifacts có thể truy cập trước khi thao tác. Nếu Chat và Job không chia sẻ context, lưu handover vào repository/đường dẫn chung có kiểm chứng; không giả định đồng bộ tự động.
- Phát hiện artifact/Issue/PR/tag trùng trước khi ghi hoặc retry; không tự tạo trùng.
- Không giả mạo approval; thao tác bên ngoài cần quyền phù hợp và phê duyệt chính xác khi policy yêu cầu.
- Kết thúc với STATUS (PASS/PARTIAL/BLOCKED/FAIL), references/URLs, commit SHA nếu có, evidence, blocker và NEXT_EXPECTED_STEP.
