# Project Overview – Tổng quan dự án

## 1. Giới thiệu dự án

| Thuộc tính | Nội dung |
|---|---|
| Tên dự án | **Universe Cinema – Hệ thống quản lý rạp chiếu phim** |
| Loại dự án | Dự án học phần *Phát triển ứng dụng* |
| Đơn vị | Khoa Công nghệ Thông tin – Trường Đại học Công nghiệp TP. Hồ Chí Minh (IUH) |
| Thời gian | 08/2024 |
| Quy mô nhóm | 5 thành viên |
| Sản phẩm học phần được dùng làm nguồn | Tài liệu Đặc tả yêu cầu ứng dụng (SRS) V1.0; Tài liệu đặc tả đề tài; Sơ đồ Use Case; 8 mockup giao diện |

Universe Cinema là hệ thống quản lý rạp chiếu phim. Hệ thống giúp quản lý lịch chiếu, theo dõi tình trạng ghế ngồi, xử lý giao dịch bán vé và theo dõi doanh thu, áp dụng được cho cả rạp lớn nhiều phòng chiếu lẫn rạp nhỏ. *(DT I)*

## 2. Bối cảnh và vấn đề nghiệp vụ

Một rạp chiếu phim cần điều phối nhiều đối tượng liên quan đến nhau: **rạp → phòng chiếu → ghế**, **phim → suất chiếu → vé**. Một phim có nhiều suất chiếu ở các phòng khác nhau, và một phòng chiếu phục vụ nhiều suất chiếu. *(SRS A.I; DT II)*

Từ mô tả này, có thể rút ra các vấn đề nghiệp vụ mà hệ thống hướng tới giải quyết:

| # | Vấn đề nghiệp vụ | Căn cứ trong nguồn | Trạng thái |
|---|---|---|---|
| 1 | Bán vé phải tránh vượt số ghế còn trống của phòng chiếu | SRS A.I: "không cho phép bán vé vượt quá số lượng ghế có sẵn" | VERIFIED |
| 2 | Hủy, hoàn vé gây sai lệch trong quản lý vé | SRS A.I: không hoàn vé "đảm bảo tính chính xác trong quản lý vé và giảm thiểu các vấn đề phát sinh liên quan đến hủy vé" | VERIFIED |
| 3 | Người quản lý cần số liệu vé, doanh thu theo phim, suất chiếu, rạp để tối ưu lịch chiếu và phân bổ phòng | DT II | VERIFIED |
| 4 | Nhân viên mới cần dùng được hệ thống mà không phải đào tạo chuyên sâu | SRS A.II | VERIFIED |

> Tài liệu gốc **không mô tả hiện trạng (as-is)** của một rạp cụ thể, và không có số liệu về vấn đề hiện tại. Portfolio không bổ sung số liệu.

## 3. Mục tiêu

| # | Mục tiêu | Nguồn |
|---|---|---|
| G-01 | Hỗ trợ quản lý thông tin và hoạt động của rạp dễ dàng, hiệu quả hơn | SRS A.I |
| G-02 | Giúp điều hành rạp nhanh chóng, thuận tiện, chính xác hơn cho người quản lý và nhân viên | SRS A.I |
| G-03 | Cung cấp báo cáo doanh thu, thống kê vé để tối ưu lịch chiếu và phân bổ phòng chiếu | SRS A.I; DT II |
| G-04 | Giao diện thân thiện để nhân viên phục vụ khách hàng hiệu quả | SRS A.I |

> Các mục tiêu trong nguồn mang tính định tính. Không có chỉ số KPI nào được đặt ra.

## 4. Stakeholders

| Stakeholder | Vai trò / Mối quan tâm | Tương tác với hệ thống | Nguồn | Trạng thái |
|---|---|---|---|---|
| Nhân viên bán vé | Bán vé nhanh, đúng ghế, đúng suất; tư vấn khách | Trực tiếp (actor) | SRS B.II, A.II | VERIFIED |
| Người quản lí / Quản trị viên | Quản lý dữ liệu rạp, phim, lịch chiếu; theo dõi doanh thu; phân quyền | Trực tiếp (actor) | SRS B.II | VERIFIED |
| Nhân viên quản lý phòng chiếu | Theo dõi phòng chiếu, phân bổ phòng cho suất chiếu, quản lý thiết bị | Chưa rõ (không phải actor trong B.II) | SRS A.II | TBD (ISS-05) |
| Khách hàng | Mua vé, chọn ghế, mua bắp nước | Gián tiếp qua nhân viên bán vé; không trực tiếp dùng hệ thống | SRS A.I | VERIFIED – đã xác nhận (ISS-01) |
| Nhóm phát triển ứng dụng | Người sử dụng tài liệu SRS | – | SRS A.II | VERIFIED |
| Giảng viên học phần | Người đánh giá sản phẩm học phần | – | DT (trang bìa) | INFERRED |

Hệ thống bên ngoài: **Hệ thống thanh toán**, **Hệ thống quản lý dữ liệu** (SRS A.II).

## 5. Phạm vi

### In Scope (VERIFIED – có use case trong SRS B.III)

| Nhóm chức năng | Use Case |
|---|---|
| Đăng nhập hệ thống | UC-001 |
| Tìm kiếm phim | UC-002 |
| Xem lịch chiếu | UC-003 |
| Bán vé xem phim (chọn suất chiếu, ghế, thanh toán, in vé) | UC-004 |
| Quản lý phim (thêm, sửa, xóa) | UC-005, UC-006, UC-007 |
| Quản lý rạp chiếu phim | UC-008 |
| Quản lý phòng chiếu và ghế ngồi | UC-009 |
| Quản lý lịch chiếu | UC-010 |
| Quản lý suất chiếu | UC-011 |
| Quản lý người dùng | UC-012 |
| Thống kê doanh thu | UC-013 |

### Phạm vi chưa xác định (TBD)

Các chức năng dưới đây có mô tả trong tài liệu nhưng **chưa có use case**, hoặc đang mâu thuẫn. Cần xác nhận trước khi xếp vào In Scope hay Out of Scope.

- Kiểm tra vé hợp lệ khi khách đến rạp (DT)
- Quản lý chương trình khuyến mãi và giá vé (DT)
- Quản lý đơn đặt vé / đơn hàng; phân quyền người dùng; quản lý nhân viên (SRS A.I)
- Quản lý thiết bị phòng chiếu (SRS A.II)
- Đánh giá phim, danh sách yêu thích (SRS C.II – ISS-10)

### Out of Scope

Tài liệu gốc không có mục Out of Scope. Danh sách dưới đây được **chủ portfolio xác nhận ngày 23/11/2026**:

| Ngoài phạm vi | Requirement | Ghi chú |
|---|---|---|
| Website / kênh cho khách hàng tự đặt vé, tự đăng ký tài khoản | FR-002 | DT II.1 có mô tả; đã loại (ISS-01) |
| Hoàn vé, đổi suất chiếu, hủy vé sau thanh toán | FR-034 | DT II có mô tả; đã loại (ISS-02) |

Ngoài ra, theo SRS A.II, hệ thống hướng đến rạp quy mô nhỏ đến trung bình. Có thể hiểu rạp quy mô lớn/chuỗi rạp không phải trọng tâm, nhưng đây chỉ là suy luận (INFERRED).

## 6. Vai trò và đóng góp cá nhân

| Hạng mục | Nội dung | Trạng thái |
|---|---|---|
| Vai trò | Thành viên nhóm 5 người, trực tiếp tham gia **phân tích yêu cầu**, **viết SRS** và **thiết kế Use Case Diagram** | Đã xác nhận bởi chủ portfolio (23/11/2026). Tài liệu gốc không có bảng phân công để đối chiếu. |
| Phạm vi đóng góp trong SRS | Tham gia biên soạn toàn bộ các mục của SRS, cùng các thành viên khác trong nhóm | Đã xác nhận bởi chủ portfolio (23/11/2026) |
| Activity Diagram, ERD | **Không phải sản phẩm học phần.** Được dựng thêm cho portfolio (PROPOSED). | PROPOSED |
| Mockup giao diện | Sản phẩm của nhóm; chưa xác định người thực hiện | TBD (Q-10) |
| Test Case, UAT | Không có trong tài liệu học phần; không được tạo trong portfolio | – |
| Phần làm thêm cho portfolio | Biên tập lại SRS theo bố cục chuẩn, đánh mã yêu cầu, lập ma trận truy vết, review chất lượng tài liệu, ghi nhận mâu thuẫn, đề xuất BR/NFR/luồng UC | PROPOSED (portfolio) |

## 7. Danh sách tài liệu bàn giao

### Sản phẩm học phần (được trích/biên tập lại)

| Tài liệu | Vị trí trong repo | Ghi chú |
|---|---|---|
| Use Case Diagram gốc | [assets/diagrams/use_case_diagram_original.png](../assets/diagrams/use_case_diagram_original.png) | Nguyên bản |
| Danh sách actor, use case | [Use Case Catalog](../03_Use_Case/Use_Case_Catalog.md) | Biên tập lại từ SRS B.II, B.III |
| Đặc tả UC001 | [Use Case Specification](../03_Use_Case/Use_Case_Specification.md#uc-001--đăng-nhập-hệ-thống) | Nguyên nội dung |
| Mô tả chức năng, phạm vi, NFR | [SRS](../02_Requirements/Software_Requirements_Specification.md) | Biên tập lại, giữ nguyên nghĩa |
| 8 mockup giao diện | [UI Wireframes](../06_UI_Wireframes/README.md) | Đã ẩn poster phim và tên thành viên |

### Tài liệu bổ sung cho portfolio

| Tài liệu | Vị trí |
|---|---|
| Functional / Non-functional Requirements, Business Rules (có mã truy vết) | [02_Requirements](../02_Requirements/) |
| Use Case Diagram vẽ lại bằng PlantUML | [Use Case Diagram](../03_Use_Case/Use_Case_Diagram.md) |
| Activity Diagram (Mermaid) | [Activity Diagram](../04_Business_Process/Activity_Diagram.md) |
| ERD đề xuất (Mermaid) | [Entity Relationship Diagram](../05_Data_Model/Entity_Relationship_Diagram.md) |
| Requirements Traceability Matrix, Source Traceability | [07_Traceability](../07_Traceability/) |
| Issue log, giả định, câu hỏi mở; checklist review | [08_Review](../08_Review/) |
| Đặc tả chi tiết UC-004 Bán vé (PROPOSED) | [UC-004 Detailed Specification](../03_Use_Case/UC-004_Sell_Ticket_Detailed_Specification.md) |
| 10 test case thiết kế cho UC-004 (PROPOSED, chưa thực thi) | [Test Cases – UC-004](../09_Test_Design/Test_Cases_UC-004_Sell_Ticket.md) |
| Case study rà soát mâu thuẫn yêu cầu | [Case Study](Case_Study_Requirements_Review.md) |
