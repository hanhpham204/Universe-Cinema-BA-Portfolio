# Requirements Traceability Matrix (RTM)

> Ma trận liên kết **Requirement → Use Case → Business Rule → Mockup → Nguồn**.
> Truy vết chi tiết đến trang/mục: [Source Traceability](Source_Traceability.md).
>
> **Test Case ID:** Học phần **không có test case** nào trong tài liệu được cung cấp, nên cột Test Case ghi "Chưa có". Portfolio không tạo mã test case giả.

## 1. Functional Requirements ↔ Use Case

| Requirement ID | Tên yêu cầu | Use Case ID | Business Rules | Mockup | Nguồn | Trạng thái | Test Case ID |
|---|---|---|---|---|---|---|---|
| FR-001 | Đăng nhập hệ thống | UC-001 | BR-010, BR-011 | WF-01 | SRS, DT, UCD | VERIFIED | Chưa có |
| FR-002 | Đăng ký tài khoản | – | – | – | DT | OUT OF SCOPE | – |
| FR-003 | Tìm kiếm phim theo tiêu chí | UC-002 | BR-009 | WF-02 | SRS, DT, UCD | VERIFIED | Chưa có |
| FR-004 | Lọc phim đang chiếu / sắp chiếu | UC-002 | BR-009 | – | SRS, DT | VERIFIED | Chưa có |
| FR-005 | Xem thông tin chi tiết phim | UC-002 *(INFERRED)* | BR-009 | WF-02 | DT, SRS | VERIFIED | Chưa có |
| FR-006 | Xem lịch chiếu theo rạp và ngày | UC-003 | BR-009 | WF-02 | SRS, DT, UCD | VERIFIED | Chưa có |
| FR-007 | Hiển thị thông tin, ghế trống của suất chiếu | UC-003 | BR-008 | – | SRS | VERIFIED | Chưa có |
| FR-008 | Bán vé: chọn phim, suất chiếu, ghế | UC-004 | BR-001, BR-002, BR-005 | WF-02, WF-03 | SRS, DT, UCD | VERIFIED | Chưa có |
| FR-009 | Chọn dịch vụ đi kèm | UC-004 | – | WF-04 | DT, SRS | INFERRED | Chưa có |
| FR-010 | Thanh toán giao dịch | UC-004 | BR-003, BR-004 | WF-04 | SRS, DT | VERIFIED | Chưa có |
| FR-011 | In vé / gửi vé điện tử | UC-004 | – | WF-04 | SRS | VERIFIED | Chưa có |
| FR-012 | Kiểm tra, cập nhật tự động ghế trống | UC-004 | BR-002, BR-008 | WF-03 | SRS | VERIFIED | Chưa có |
| FR-013 | Thêm phim | UC-005 | BR-012 | WF-05 | SRS, DT | VERIFIED | Chưa có |
| FR-014 | Sửa thông tin phim | UC-006 | BR-012 | WF-05 | SRS, DT | VERIFIED | Chưa có |
| FR-015 | Xóa phim | UC-007 | BR-012 | WF-05 | SRS, DT | VERIFIED | Chưa có |
| FR-016 | Xem danh sách phim | UC-005, UC-006, UC-007 *(INFERRED)* | – | WF-05 | SRS, DT | VERIFIED | Chưa có |
| FR-017 | Thêm rạp chiếu phim | UC-008 | BR-012 | – | SRS, DT | VERIFIED | Chưa có |
| FR-018 | Sửa thông tin rạp | UC-008 | BR-012 | – | SRS, DT | VERIFIED | Chưa có |
| FR-019 | Xem danh sách rạp | UC-008 | – | – | SRS, DT | VERIFIED | Chưa có |
| FR-020 | Xóa rạp chiếu phim | UC-008 | – | – | SRS (B.III) | TBD | Chưa có |
| FR-021 | Quản lý phòng chiếu | UC-009 | BR-006 | – | SRS, DT | VERIFIED | Chưa có |
| FR-022 | Quản lý ghế ngồi | UC-009 | BR-002 | – | SRS, DT | VERIFIED | Chưa có |
| FR-023 | Quản lý lịch chiếu | UC-010 | BR-007 | WF-06 | SRS, DT | VERIFIED | Chưa có |
| FR-024 | Quản lý suất chiếu | UC-011 | BR-005, BR-006, BR-007 | WF-06 | SRS, DT | VERIFIED | Chưa có |
| FR-025 | Quản lý người dùng | UC-012 | BR-012 | WF-07 | SRS, DT | VERIFIED | Chưa có |
| FR-026 | Báo cáo doanh thu | UC-013 | BR-012 | WF-08 | SRS | VERIFIED | Chưa có |
| FR-027 | Lọc báo cáo doanh thu | UC-013 | – | – | SRS | VERIFIED | Chưa có |
| FR-028 | Xuất báo cáo Excel/PDF | UC-013 | – | – | SRS | VERIFIED | Chưa có |
| FR-029 | Màn hình tổng quan | UC-013 *(INFERRED)* | – | WF-08 | DT | VERIFIED | Chưa có |
| FR-030 | Phân quyền người dùng | – *(gap)* | BR-010, BR-012 | – | SRS | VERIFIED | Chưa có |
| FR-031 | Theo dõi, quản lý đơn đặt vé | – *(gap)* | – | – | SRS, DT | VERIFIED | Chưa có |
| FR-032 | Quản lý khuyến mãi, giá vé | – *(gap)* | – | – | DT | TBD | Chưa có |
| FR-033 | Kiểm tra vé hợp lệ tại rạp | – *(gap)* | – | – | DT | TBD | Chưa có |
| FR-034 | Đổi suất chiếu / hoàn vé | – | BR-003, BR-004 | – | DT | OUT OF SCOPE | – |
| FR-035 | Quản lý nhân viên | UC-012 *(TBD)* | – | WF-07 | SRS | TBD | Chưa có |

## 2. Use Case ↔ Requirement (chiều ngược)

| Use Case ID | Tên | Requirement IDs | Số FR |
|---|---|---|---|
| UC-001 | Đăng nhập hệ thống | FR-001 | 1 |
| UC-002 | Tìm kiếm các bộ phim | FR-003, FR-004, FR-005 | 3 |
| UC-003 | Xem lịch chiếu | FR-006, FR-007 | 2 |
| UC-004 | Bán vé xem phim | FR-008, FR-009, FR-010, FR-011, FR-012 | 5 |
| UC-005 | Thêm phim | FR-013, FR-016 | 2 |
| UC-006 | Sửa phim | FR-014, FR-016 | 2 |
| UC-007 | Xóa phim | FR-015, FR-016 | 2 |
| UC-008 | Quản lý rạp chiếu phim | FR-017, FR-018, FR-019, FR-020 | 4 |
| UC-009 | Quản lý phòng chiếu | FR-021, FR-022 | 2 |
| UC-010 | Quản lý lịch chiếu | FR-023 | 1 |
| UC-011 | Quản lý suất chiếu | FR-024 | 1 |
| UC-012 | Quản lý người dùng | FR-025, FR-035 | 2 |
| UC-013 | Thống kê doanh thu | FR-026, FR-027, FR-028, FR-029 | 4 |

**Kết quả kiểm tra độ phủ:**

- 13/13 use case đều có ít nhất một yêu cầu chức năng.
- 6/35 yêu cầu chức năng chưa gắn với use case nào. Trong đó FR-002 và FR-034 đã được xác nhận nằm ngoài phạm vi (23/11/2026). 4 yêu cầu còn lại là FR-030, FR-031, FR-032, FR-033. Đây là các khoảng trống phạm vi, đã được ghi nhận ở [Assumptions and Open Questions](../08_Review/Assumptions_and_Open_Questions.md) (ISS-11).

## 3. Non-functional Requirements ↔ phạm vi áp dụng

| NFR ID | Yêu cầu | Áp dụng cho | Nguồn | Trạng thái | Test Case ID |
|---|---|---|---|---|---|
| NFR-001 | Giao diện thân thiện, dễ sử dụng | Tất cả UC | DT, SRS | VERIFIED | Chưa có |
| NFR-002 | Không cần đào tạo chuyên sâu | Tất cả UC | SRS | VERIFIED | Chưa có |
| NFR-003 | Bảo mật, xác thực quyền truy cập | UC-001, UC-012 | DT, SRS | VERIFIED | Chưa có |
| NFR-004 | Chạy ổn định | Tất cả UC | DT, SRS | VERIFIED | Chưa có |
| NFR-005 | Dễ bảo trì, nâng cấp | Toàn hệ thống | DT | VERIFIED | Chưa có |
| NFR-006 | Quy mô rạp nhỏ – trung bình | Toàn hệ thống | SRS | VERIFIED | Chưa có |
| NFR-007 | Kết nối hệ thống thanh toán | UC-004 | SRS | VERIFIED | Chưa có |
| NFR-008 | Kết nối hệ thống quản lý dữ liệu | UC-003, UC-013 | SRS | VERIFIED | Chưa có |

## 4. Test case đề xuất (PROPOSED – chưa thực thi)

> Cột "Test Case ID" ở các bảng trên vẫn ghi "Chưa có", vì học phần không có test case thực tế. Bảng dưới đây liên kết các test case **thiết kế thêm cho portfolio**. Các test case này chưa được chạy và không có kết quả.

| Requirement / Rule | Test case đề xuất |
|---|---|
| FR-008 | TC-UC004-01, TC-UC004-02, TC-UC004-04, TC-UC004-05 |
| FR-009 | TC-UC004-02 |
| FR-010 | TC-UC004-01, TC-UC004-06 |
| FR-011 | TC-UC004-01 |
| FR-012 | TC-UC004-01, TC-UC004-03, TC-UC004-06, TC-UC004-07 |
| BR-002 | TC-UC004-03, TC-UC004-07 |
| BR-003, BR-004 | TC-UC004-09 |
| BR-008 | TC-UC004-01, TC-UC004-06 |
| BR-009, BR-010 | TC-UC004-10 |
| BR-P03, BR-P04 | TC-UC004-04, TC-UC004-08 |

Chi tiết: [Test Cases – UC-004](../09_Test_Design/Test_Cases_UC-004_Sell_Ticket.md).
