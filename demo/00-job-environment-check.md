# 00 — Job: Environment / ADO Preflight

**Orca Job prompt — chỉ click Run; không hardcode máy, project hoặc credential.**

> Kiểm tra phiên bản worker, plugin `ai-workflow` và native Skill discovery, Orca Run/Task/Dispatch, Git/GitHub permissions, repo demo, test/build tools và Azure DevOps MCP của chính worker này. Thực hiện read-only ADO organization/project/work-item type/search và xác minh khả năng read/write qua quyền được cấp, nhưng **không thực hiện bất cứ thao tác ghi nào**. Nếu ADO chưa thiết lập, xác định hướng cấu hình tương thích với môi trường hiện tại, yêu cầu người dùng hoàn tất authentication bằng kênh bảo mật nếu cần, sau đó kiểm tra lại. Không yêu cầu dán PAT/token vào chat hoặc commit secret. Nếu ADO chưa sẵn sàng, báo BLOCKED_ADO và đề xuất GitHub Issues làm fallback **chỉ sau khi người dùng chấp thuận rõ ràng**. Trước khi hoàn tất preflight, thiết lập hoặc xác minh RUN_ID duy nhất và shared handover tại repository demo có quyền phù hợp (gợi ý `workflow-demo/runs/<run-id>/context.md`), đảm bảo Worker Chat bước 01 và Orca Job bước 02 có thể đọc và cập nhật qua cùng một repository/branch; nếu không xác minh được thì BLOCKED_HANDOVER, không báo PASS. Lưu URI/repository/branch, RUN_ID, kết quả kiểm thử công cụ, backend được lựa chọn và project đã xác minh. Không push dữ liệu ADO nội bộ sang repository công khai. NEXT_EXPECTED_STEP=01-worker-chat-idea-to-backlog.

> Đây chỉ là kiểm tra preflight: không tạo, cập nhật, close, delete, link Issue; không tạo PR, merge hoặc release.

## Kết quả
`STATUS`, `SKILL_DISCOVERY`, `ADO_MCP_STATUS`, `ISSUE_BACKEND`, `AUTHORIZED_TARGET`, `GITHUB_ACCESS`, `BUILD_TOOLS`, `RUN_ID`, `HANDOVER_LOCATION`, `HANDOVER_REPO`, `HANDOVER_BRANCH`, `HANDOVER_ACCESS_STATUS`, `NEXT_EXPECTED_STEP`.
