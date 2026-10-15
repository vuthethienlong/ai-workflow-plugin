# 02 — Job: Auto Brainstorm (suggestions only)

**Orca Job prompt — click Run:**

> Sử dụng Skill `auto-brainstorm` của `ai-workflow`. Truy xuất Issue thật đã tạo ở bước 01 và nguồn handover chung (Orca state khi khả dụng, nếu không là artifact trong repository demo được xác minh). Đọc Issue ở ADO qua worker-owned MCP hoặc GitHub backend đã chọn; ghi lại Issue ID/URL và source revision. Brainstorm **ngay trên Issue hiện có**, làm rõ requirements, acceptance criteria, architecture options, edge cases, risks và dependencies. Tạo `brainstorm-summary` và `suggested-changes` dạng draft với before/after, rationale, impact và outstanding questions. Đề xuất chia Issue hoặc tạo Task nếu thực sự cần nhưng **chỉ dưới dạng suggestion**, không thực hiện. Auto brainstorming không phải quyết định cuối cùng.

> **READ ONLY đối với ADO/GitHub Issues**: tuyệt đối không CREATE, UPDATE, SPLIT, LINK/UNLINK, DELETE, CLOSE/REOPEN, đổi status hoặc MERGE. Không tạo PR. Chuyển proposals sang bước 03 để người dùng thảo luận/chốt và approve; không giả lập approval.

> NEXT_EXPECTED_STEP=03-manual-brainstorm.

## Kết quả
`STATUS`, `ISSUE_BACKEND`, `ISSUE_IDS/URLS`, `SOURCE_REVISIONS`, `BRAINSTORM_SUMMARY`, `SUGGESTED_CHANGES`, `HANDOVER_LOCATION`, `NEXT_EXPECTED_STEP`.
