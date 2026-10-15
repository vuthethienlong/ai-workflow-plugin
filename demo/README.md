# Portable Orca E2E demo — ai-workflow

Thư mục này chứa **prompts để copy sang Orca máy khác**; không có YAML, không tạo workflow engine, không hardcode Idea/repo/worker/project. Đây **không phải các Job đã được thực thi**.

## Setup trên từng máy

1. Cài `ai-workflow` và xác minh Skill discovery; chuẩn bị Orca worker, GitHub, Git và công cụ test/build.
2. Tạo **Job 00** từ `00-job-environment-check.md`, click Run. Kiểm tra ADO MCP thật (organization, project, work-item types và permissions) và cho phép cấu hình lại + read-only test. Nếu ADO không dùng được, yêu cầu người dùng chấp thuận fallback GitHub Issues thật. Không tự chọn backend hoặc giả lập ADO.
3. **Bước 01 là Worker Chat**, không phải Job: gửi prompt trong `01-worker-chat-idea-to-backlog.md`, nhập ý tưởng mới; lập backlog và **tạo Issue thật sau approval chính xác**.
4. Cấu hình Job cho bước **02, 04, 05, 07, 08, 09, 11, 12** bằng cách copy prompt của từng file vào Orca. Không chạy Job lúc setup.
5. **03 là Worker Chat**; **06 và 10 là human PR approval** (không phải auto Jobs). Bước 11 yêu cầu release approval riêng.
6. Chạy từng bước theo thứ tự; mỗi bước đọc predecessor output và xác minh gates, không yêu cầu nhập lại ID đã lưu.

## Flow thực tế

| Step | Mode | Outcome |
|---|---|---|
| 00 Environment/ADO preflight | Job / click Run | Skill + ADO/GitHub/tool availability, backend và target được xác minh |
| 01 Idea → Backlog | Worker Chat | Backlog + ADO Issues thật (hoặc GitHub Issues nếu được phép), sau human approval |
| 02 Auto Brainstorm | Job / click Run | **READ-ONLY** trên Issue thật, lưu draft suggested changes; **không update ADO** |
| 03 Manual Brainstorm | Worker Chat | Người dùng chốt suggestions, duyệt thao tác cụ thể, worker update và read-back Issue |
| 04 Issue → Spec + Draft PR | Job | Spec/Plan/Tasks và PR thật |
| 05 Independent Review Spec | Job (reviewer khác tác giả) | Findings và recommendation trên exact PR HEAD |
| 06 Human Spec Approval | Human | Approve SHA hiện tại và cho phép merge thật |
| 07 Auto Implement + TDD | Job | Code/commits + TDD evidence thật; **chưa tạo PR** |
| 08 Implementation Draft PR | Job | PR code thật |
| 09 Independent Review Code | Job (reviewer khác tác giả) | Findings trên exact PR HEAD |
| 10 Human Code Approval | Human | Approve và cho phép merge code |
| 11 Build + Release | Job + release approval | Test/build thật, tag và GitHub Release sau duyệt riêng |
| 12 Verify Release + Final E2E Report | Job | Verify tag/asset/build thật và tổng hợp URLs/SHAs/evidence cho flow 00–12 |

## Approval + ADO policy

- **00** chỉ kiểm tra read-only, không tạo Work Item.
- **01** có thể CREATE/LINK Issues thật **chỉ sau human approval của danh sách thao tác** và xác nhận project.
- **02** chỉ brainstorm và chuẩn bị proposal trên **chính Issues có sẵn**; không CREATE/UPDATE/SPLIT/LINK/DELETE/CLOSE/MERGE.
- **03** là nơi user chỉnh/chốt; với mọi CREATE, UPDATE, SPLIT, LINK/UNLINK, DELETE, CLOSE/REOPEN, đổi status, hoặc MERGE được đề xuất, phải hiển thị target, before/after, impact, xin approval rõ ràng, kiểm tra revision lại trước khi ghi, read-back sau ghi. Không lấy auto suggestion làm quyết định cuối.
- Các Spec/Code PR cần independent reviewer và **human approval** trên exact revision. `recommend_approve` không phải human approval; merge hay release không tự động.

## Handover portable giữa Worker Chat và Job

Một **handover artifact dùng chung** là bắt buộc. Ngay trong **Job 00**, worker phải chọn hoặc tạo RUN_ID duy nhất, xác minh repository/branch/path dùng chung mà **cả Worker Chat bước 01 và Job bước 02** có thể đọc và cập nhật; gợi ý `<demo-repo>/workflow-demo/runs/<run-id>/`, **không** hardcode ổ đĩa hoặc tên repo. Job 00 phải lưu `HANDOVER_REPO`, `HANDOVER_BRANCH`, `RUN_ID`, `HANDOVER_LOCATION` vào kết quả preflight. Các bước sau phải dùng **chính xác** reference này, không tạo run mới. Nếu Worker Chat/Job không thể truy xuất reference đã xác minh, trả `BLOCKED_HANDOVER`, không suy đoán. GitHub repo private hoặc lưu trữ có kiểm soát được ưu tiên nếu artifacts chứa metadata ADO nội bộ. Ví dụ các file lưu ở đó: `context.md`, `backlog.md`, `suggested-changes.md`, `decisions.md`, `evidence.md`.

`context.md` ghi tối thiểu (khi áp dụng): `RUN_ID`, `HANDOVER_REPO`, `HANDOVER_BRANCH`, `HANDOVER_LOCATION`, `STEP_ID`, `ISSUE_BACKEND`, `AUTHORIZED_TARGET`, `ISSUE_IDS/URLS`, `SOURCE_REVISIONS`, `ARTIFACT_PATHS`, `PR_URL`, `HEAD_SHA`, `APPROVAL_STATE`, `NEXT_EXPECTED_STEP`. Chỉ lưu approval evidence và URL có thể công khai trong phạm vi repo được cấp quyền, **không lưu tokens, PAT, secrets, logs nhạy cảm hoặc nội dung ADO confidential vào repo public**.

Mỗi bước phải:
1. Đọc trạng thái Orca trước; nếu không thể chia sẻ Chat → Job qua Orca, truy xuất artifact chung theo reference đã được xác minh.
2. Nếu không có context hoặc thiếu quyền truy cập, trả về `BLOCKED`, không tự đoán Issue ID.
3. Ghi checkpoint và evidence với `STATUS`, blocker, reference và `NEXT_EXPECTED_STEP`.
4. Kiểm tra duplicate và revision/approval trước mọi write/retry.

Máy khác cần cài lại plugin, cấu hình lại credentials của từng worker và trỏ đến **đúng artifact shared** của run đang muốn tiếp tục. Không sao chép credentials hoặc giả định Orca tự đồng bộ toàn bộ Chat history.

## Lưu ý kiểm thử

Prompt Markdown không có khả năng tự kích hoạt Skills hoặc thực hiện actions nếu runtime thiếu quyền/công cụ. Review tự thực hiện bởi tác giả **không** được tính independent. Khi có findings phải sửa trên branch và review lại exact HEAD. Không tự approve, merge, close hoặc publish.
