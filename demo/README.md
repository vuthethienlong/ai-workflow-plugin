# Portable Orca E2E demo — ai-workflow

Bộ prompt độc lập để **copy sang Orca trên máy khác**, không cần YAML, code Orca mới, ADO giả, hay Todo App hardcode. Đây là tài liệu cấu hình; **không phải Job đã được tạo hoặc chạy trong Orca**.

## Chuẩn bị một lần

1. Cài plugin `ai-workflow` vào agent workers; kiểm tra Skill discovery thực tế.
2. Chuẩn bị repository demo do người chạy chọn; cấp GitHub read/write, Git và môi trường chạy test/build. Azure DevOps MCP là tùy chọn; khi chưa có, dùng GitHub Issues **thật** sau approval, không báo ADO PASS.
3. Trong Orca, **Bước 01 là Worker Chat**, không phải Job: mở Worker và gửi prompt trong `01-worker-chat-idea-to-backlog.md`. Ý tưởng được nhập trong cuộc chat.
4. Lưu prompts `02`, `04`, `05`, `07`, `08`, `09`, `11`, `12` thành những Job độc lập (copy nội dung body của file vào phần prompt). Tên Job theo tên file. **Không chạy khi tạo Job**.
5. `03` là Worker Chat tương tác; `06`, `10` là điểm duyệt của con người, **không phải Job tự approve**. Release có một phê duyệt riêng ngay trong `11`.
6. Click Run theo thứ tự; mỗi Job đọc handover/artifacts từ bước trước, không yêu cầu người dùng paste dữ liệu đã lưu. Nếu Orca không hỗ trợ kết nối Chat → Job, lưu handover vào file hoặc GitHub artifact chung để worker kế tiếp có thể lấy.

## Trình tự

| Bước | Tên | Loại | Kết quả thật |
|---|---|---|---|
| 01 | Idea → Backlog | Worker Chat | Idea, backlog proposal; Issue thật **sau duyệt** |
| 02 | Auto Brainstorm | Job Run | Brainstorm và điều chỉnh backlog |
| 03 | Manual Brainstorm | Worker Chat | Quyết định thiết kế |
| 04 | Issue → Spec + PR | Job Run | Spec/Plan/Tasks, Draft PR |
| 05 | Review Spec | Job Run, reviewer độc lập | Findings trên đúng PR HEAD |
| 06 | Human Spec Approval | Người dùng | Approval + merge permission |
| 07 | Auto Implement / TDD | Job Run | Code và RED/GREEN/REFACTOR evidence |
| 08 | Implementation PR | Job Run | Draft code PR thật |
| 09 | Review Implementation | Job Run, reviewer độc lập | Findings trên đúng PR HEAD |
| 10 | Human Code Approval | Người dùng | Approval + merge permission |
| 11 | Release | Job Run sau release approval | Build, tag, GitHub Release |
| 12 | Verify Release | Job Run | Test và release evidence |

**Lưu ý:** Review chỉ đề xuất approve, không thay thế GitHub human review. Nếu có findings, chuyển worker tác giả sửa trên branch, tạo commit mới rồi chạy lại review. Nếu PR HEAD thay đổi, recommendation cũ hết hiệu lực. Bước 07 **chưa mở PR** để bước 08 thực hiện riêng.

## Kiểm thử và di chuyển máy

Sao chép cả thư mục `demo/` (hoặc clone plugin public), sau đó tạo các Job bằng copy/paste. Đừng copy credentials hoặc Orca Run/Task IDs từ máy nguồn. Bản ghi handover nên chứa `RUN_ID`, `TASK_ID`, `ARTIFACTS`, `ISSUE_URLS`, `PR_URL`, `HEAD_SHA`, `APPROVAL_STATE`, `NEXT_EXPECTED_STEP` phù hợp mỗi bước; chỉ báo những trường thực sự tồn tại.

Mọi prompt dùng Skill sẵn có, **không yêu cầu thêm các command wrappers**. Tên slash command phụ thuộc host; nếu cần hãy gọi Skill bằng lời trực tiếp.
