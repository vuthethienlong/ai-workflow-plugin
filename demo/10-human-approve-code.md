# 10 — Human Approval: Implementation PR

**Không phải Auto Job; người dùng thao tác thực tế.**

1. Đọc Implementation PR và review evidence từ Job 09, so SHA hiện tại với SHA được review.
2. Nếu có thay đổi/new commit, yêu cầu re-review; không dùng approval cũ.
3. Human approve phiên bản code cụ thể; merge **chỉ khi có quyền và lệnh merge rõ ràng**.
4. Lưu approver, PR URL, merge commit SHA; xác nhận trạng thái main/build.
5. Quyền merge Implementation PR **không phải** quyền publish Release; Job 11 có gate riêng.

NEXT_EXPECTED_STEP=11-release.
