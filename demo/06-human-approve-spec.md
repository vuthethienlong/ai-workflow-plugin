# 06 — Human Approval: Spec PR

**Không phải Auto Job; người dùng thao tác GitHub/Orca thực tế.**

1. Kiểm tra PR và review checklist, đối chiếu exact HEAD SHA với SHA đã review.
2. Nếu muốn sửa, báo findings cho tác giả bước 04 và chạy lại bước 05 sau commit mới.
3. Nếu chấp nhận, human approve đúng revision trên GitHub; khi có yêu cầu merge rõ ràng, merge PR thật.
4. Lưu PR URL, merge commit SHA, người phê duyệt và evidence để Job 07 đọc.
5. Không tự suy ra approve từ `recommend_approve`; không tự merge.

NEXT_EXPECTED_STEP=07-auto-implement.
