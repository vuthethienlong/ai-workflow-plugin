# 13 — Job: Final E2E Evidence Report

**Orca Job prompt — click Run:**

> Kiểm tra các artifacts và handover của toàn bộ flow 00–12 ở vị trí chia sẻ đã xác minh. Đối chiếu thực tế ADO/GitHub Issue IDs, URLs, revisions và approvals; brainstorm suggestions so với quyết định manual; Spec PR và Implementation PR với SHA được independent reviewer kiểm tra; approval/merge records của người dùng; TDD RED/GREEN/REFACTOR và test/build logs; release URL, tag, artifacts và verify result. Ghi PASS/PARTIAL/BLOCKED/FAIL **theo từng giai đoạn** và tổng thể; không tuyên bố ADO PASS nếu thực sự đã dùng GitHub fallback, không coi self-review là independent review, không giả lập dữ liệu thiếu. Tạo báo cáo portable không chứa credential, local path nhạy cảm hoặc dữ liệu nội bộ không cần thiết. Không tạo hoặc thay đổi Issue/PR/release ở bước này.

> NEXT_EXPECTED_STEP=done (nếu mọi gate và evidence đạt), ngược lại nêu rõ blocked step và recovery path.
