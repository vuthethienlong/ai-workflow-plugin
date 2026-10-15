# 03 — Worker Chat: Manual Brainstorm + Human Approval

**Chat tương tác thật, không phải Auto Job.**

> Sử dụng Skill `manual-brainstorm` của `ai-workflow`. Đọc Issue thật, source revision và toàn bộ suggestions từ bước 02. Thảo luận từng thay đổi với tôi, xác định quyết định cuối cùng; không mặc định auto-brainstorm đã đúng hoặc được duyệt. Trước khi ghi ADO/GitHub, hiển thị **danh sách thao tác cụ thể** CREATE, UPDATE, LINK/UNLINK, SPLIT, DELETE, CLOSE/REOPEN, status hoặc MERGE nếu được đề xuất, kèm Issue ID, project, before/after và ảnh hưởng. Yêu cầu **human approval rõ ràng cho từng phạm vi thao tác**, không hiểu review recommendation là approval. Nếu chưa approve, lưu draft và dừng. Sau khi approve, đọc lại source revision; nếu đã thay đổi, trình bày diff và xin approve lại. Chỉ thực hiện thao tác đã duyệt bằng công cụ được cấp quyền; tránh duplicate; read-back và lưu ID/URL/revision/evidence. Không tự tạo thêm Issues/Tasks/hierarchy, delete/close/merge ngoài phê duyệt cụ thể. Chốt scope/AC để bước 04 tạo Spec.

> NEXT_EXPECTED_STEP=04-issue-to-spec.

## Kết quả
`FINAL_DECISIONS`, `APPROVAL_ACTOR`, `APPROVED_OPERATIONS`, `APPROVED_REVISIONS`, `ISSUE_IDS/URLS`, `READBACK_EVIDENCE`, `HANDOVER_LOCATION`, `NEXT_EXPECTED_STEP`.
