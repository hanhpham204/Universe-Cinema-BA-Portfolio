# Use Case Catalog – Danh mục Use Case

> **Nguồn:** [SRS] mục B.III "Danh sách Use case và mô tả" (UC001–UC013) và [UCD].
> Mã UC-xxx trong portfolio tương ứng một-một với mã gốc UCxxx của SRS.

## 1. Danh sách tác nhân (Actors)

| Actor | Mô tả (theo SRS B.II) | Tên khác trong tài liệu gốc | Trạng thái |
|---|---|---|---|
| **Nhân viên bán vé** | Thực hiện các giao dịch bán vé, hỗ trợ khách hàng đặt vé và chọn suất chiếu; kiểm tra tình trạng vé, xác nhận đặt chỗ và xử lý thanh toán. | "Nhân viên" (UCD, SRS A.I.1), "Nhân viên quản lý rạp chiếu" (DT II) | VERIFIED |
| **Người quản lí** | Quản lý toàn bộ hệ thống: cấu hình và bảo trì hệ thống, quản lý lịch chiếu, theo dõi doanh thu, phân tích dữ liệu; có quyền truy cập và điều chỉnh tất cả thông tin và chức năng. | "Admin", "Quản lí hệ thống" (SRS A.I.2), "QuanTriVien" (UCD), "Người quản trị hệ thống (Admin)", "Nhân viên quản lí rạp" (DT) | VERIFIED |
| Khách hàng | Người nhận dịch vụ; mua vé thông qua nhân viên bán vé. DT mô tả "người dùng" tự đặt vé trên website, nhưng kênh này nằm ngoài phạm vi. | "Người dùng" (DT II.1) | **Không phải actor** – đã xác nhận 23/11/2026 (ISS-01) |
| Hệ thống thanh toán | Hệ thống con xử lý giao dịch bán vé và dịch vụ bổ sung. | – | INFERRED là actor phụ (SRS A.II chỉ gọi là "hệ thống con") |

> SRS A.II còn liệt kê ba nhóm người dùng là *Nhân viên bán vé*, *Nhân viên quản lý phòng chiếu* và *Quản lý rạp phim*, nhưng bảng tác nhân (B.II) chỉ có hai. Xem ISS-05.

## 2. Danh mục Use Case

| UC ID | Mã gốc | Tên Use Case | Actor chính | Mô tả ngắn (theo SRS B.III) | Nhóm chức năng | Có trên UCD | Mức đặc tả trong nguồn |
|---|---|---|---|---|---|---|---|
| UC-001 | UC001 | Đăng nhập hệ thống | Nhân viên bán vé, Người quản lí | Dùng tài khoản cá nhân để truy cập; hệ thống kiểm tra và xác thực quyền truy cập. | Đăng nhập | Có | **Đầy đủ** (SRS C.I) |
| UC-002 | UC002 | Tìm kiếm các bộ phim | Nhân viên bán vé | Tìm phim đang chiếu hoặc sắp chiếu bằng bộ lọc theo tên phim, thể loại, thời gian chiếu. | Tìm kiếm | Có (kèm 3 UC con) | Một phần (SRS C.II, chưa có luồng) |
| UC-003 | UC003 | Xem lịch chiếu | Nhân viên bán vé | Xem lịch chiếu cho từng rạp, từng ngày; hiển thị thời gian, phòng chiếu, số ghế còn trống. | Lịch chiếu | Có | Mô tả ngắn |
| UC-004 | UC004 | Bán vé xem phim | Nhân viên bán vé | Bán vé cho khách hàng, gồm chọn ghế ngồi và suất chiếu; cập nhật số ghế còn trống. | Bán vé | Có | Mô tả ngắn |
| UC-005 | UC005 | Thêm phim | Người quản lí | Thêm phim mới với tên phim, thể loại, đạo diễn, diễn viên, mô tả. | Quản lý phim | Gộp trong "Quản lí phim" | Mô tả ngắn |
| UC-006 | UC006 | Sửa phim | Người quản lí | Sửa thông tin phim đã có. | Quản lý phim | Gộp trong "Quản lí phim" | Mô tả ngắn |
| UC-007 | UC007 | Xóa phim | Người quản lí | Xóa phim khỏi hệ thống. | Quản lý phim | Gộp trong "Quản lí phim" | Mô tả ngắn |
| UC-008 | UC008 | Quản lý rạp chiếu phim | Người quản lí | Thêm, sửa hoặc xóa thông tin rạp chiếu phim. | Quản lý rạp | Có | Mô tả ngắn |
| UC-009 | UC009 | Quản lý phòng chiếu | Người quản lí | Thêm, sửa, xóa phòng chiếu; quản lý danh sách ghế ngồi trong từng phòng. | Quản lý phòng chiếu | Có | Mô tả ngắn |
| UC-010 | UC010 | Quản lý lịch chiếu | Người quản lí | Thêm, sửa, xóa lịch chiếu phim. | Quản lý lịch chiếu | Có | Mô tả ngắn |
| UC-011 | UC011 | Quản lý suất chiếu | Người quản lí | Thêm, sửa, xóa suất chiếu. | Quản lý suất chiếu | Có | Mô tả ngắn |
| UC-012 | UC012 | Quản lý người dùng | Người quản lí | Xem danh sách người dùng, xem chi tiết, sửa thông tin và xóa người dùng khi cần. | Quản lý người dùng | Có | Mô tả ngắn |
| UC-013 | UC013 | Thống kê doanh thu | Người quản lí | Xem báo cáo doanh thu từ bán vé và dịch vụ bổ sung, lọc theo nhiều tiêu chí và xuất báo cáo. | Thống kê | Có | Mô tả ngắn |

### Use case con chỉ xuất hiện trên sơ đồ (UCD)

Sơ đồ gốc có ba use case con kế thừa (generalization) từ "Tìm kiếm phim". Các use case này **không có trong danh sách SRS B.III** nên portfolio không cấp mã UC riêng. Chúng được ghi nhận như biến thể của UC-002.

| Tên trên UCD | Quan hệ | Ghi chú |
|---|---|---|
| Tìm theo tên phim | Generalization → Tìm kiếm phim | VERIFIED (UCD) |
| Tìm theo thời gian chiếu | Generalization → Tìm kiếm phim | VERIFIED (UCD) |
| Tìm theo thể loại | Generalization → Tìm kiếm phim | VERIFIED (UCD) |

### Chức năng có mô tả nhưng chưa có Use Case

| Chức năng | Nguồn | Requirement liên quan | Ghi chú |
|---|---|---|---|
| Xem thông tin chi tiết phim | DT II.1.c | FR-005 | Có thể là một phần của UC-002 (INFERRED) |
| Đăng ký tài khoản | DT II.1.a | FR-002 | OUT OF SCOPE (đã xác nhận) |
| Màn hình tổng quan (dashboard) | DT II.2.a | FR-029 | Có thể là một phần của UC-013 (INFERRED) |
| Phân quyền người dùng | SRS A.I | FR-030 | Chưa có UC |
| Theo dõi / quản lý đơn đặt vé | SRS A.I; DT II | FR-031 | Chưa có UC |
| Quản lý khuyến mãi, giá vé | DT II | FR-032 | TBD |
| Kiểm tra vé hợp lệ tại rạp | DT II | FR-033 | TBD |
| Đổi suất chiếu / hoàn vé | DT II | FR-034 | OUT OF SCOPE (đã xác nhận) |
| Quản lý nhân viên | SRS A.I, A.II | FR-035 | TBD |

Chi tiết từng use case: [Use Case Specification](Use_Case_Specification.md) · Sơ đồ: [Use Case Diagram](Use_Case_Diagram.md)
