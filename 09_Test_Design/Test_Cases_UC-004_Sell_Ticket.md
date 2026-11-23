# Test Cases – UC-004 Bán vé xem phim

> ⚠️ **Đề xuất bổ sung (PROPOSED) – thiết kế test case, chưa thực thi.**
> - Học phần **không có test case** nào. Bộ test case này được **viết thêm cho portfolio**, dựa trên [đặc tả chi tiết UC-004](../03_Use_Case/UC-004_Sell_Ticket_Detailed_Specification.md) (cũng là bản đề xuất).
> - Các test case **chưa được chạy** trên hệ thống nào, nên **không có kết quả thực tế** (cột "Kết quả thực tế" để trống, trạng thái "Chưa thực hiện").
> - Dữ liệu test (TD) là dữ liệu giả định để thiết kế, không phải dữ liệu của dự án.

## 1. Dữ liệu test giả định

| Mã | Dữ liệu |
|---|---|
| TD-01 | Tài khoản nhân viên bán vé hợp lệ, đã đăng nhập |
| TD-02 | Phim M1 có suất chiếu S1 tại phòng P1, chưa bắt đầu. P1 có 90 ghế (6 hàng A–F × 15 ghế, như WF-03). S1 đã bán ghế A1, A2. |
| TD-03 | Suất chiếu S2 tại phòng P1 đã bán hết 90/90 ghế |
| TD-04 | Suất chiếu S3 đã bắt đầu trước thời điểm test |
| TD-05 | Combo bắp nước C1 có trong danh mục |
| TD-06 | Hệ thống thanh toán ở chế độ thử, có thể trả về "thành công" hoặc "thất bại" |

## 2. Danh sách test case

| TC ID | Tên test case | Loại | Truy vết | Độ ưu tiên đề xuất |
|---|---|---|---|---|
| TC-UC004-01 | Bán 1 vé thành công, không mua bắp nước | Positive | Luồng chính; FR-008, FR-010, FR-011, FR-012; BR-008 | Cao |
| TC-UC004-02 | Bán nhiều vé kèm combo bắp nước | Positive | A1; FR-009 | Trung bình |
| TC-UC004-03 | Không cho bán vé suất chiếu đã hết ghế | Negative | E1; BR-002 | Cao |
| TC-UC004-04 | Không cho chọn ghế đã bán | Negative | E3; BR-P03 | Cao |
| TC-UC004-05 | Không cho sang bước tiếp khi chưa chọn ghế | Negative | E4 | Trung bình |
| TC-UC004-06 | Thanh toán thất bại không làm mất ghế trống | Negative | E5; BR-008 | Cao |
| TC-UC004-07 | Hai quầy cùng bán một ghế cùng lúc | Concurrency | E6; SR1; NFR-P04 | Cao |
| TC-UC004-08 | Không cho bán vé suất chiếu đã bắt đầu | Negative | E2; BR-P04 | Trung bình |
| TC-UC004-09 | Không có chức năng hoàn/hủy vé đã thanh toán | Negative | E8; BR-003, BR-004 | Trung bình |
| TC-UC004-10 | Phải đăng nhập mới truy cập được chức năng bán vé | Security | Tiền điều kiện P1; BR-009, BR-010 | Cao |

TC-UC004-09 kiểm tra quy tắc "không hoàn, không đổi, không hủy vé" đã được chủ portfolio xác nhận ngày 23/11/2026 (ISS-02).

## 3. Chi tiết test case

### TC-UC004-01 – Bán 1 vé thành công, không mua bắp nước

| Mục | Nội dung |
|---|---|
| Tiền điều kiện | TD-01, TD-02, TD-06 (thành công) |
| Các bước | 1. Chọn "Booking Movies". 2. Chọn ngày chiếu của S1, chọn phim M1. 3. Chọn suất S1, nhấn Next. 4. Chọn ghế B5, nhấn Next. 5. Không chọn combo; chọn hình thức thanh toán, xác nhận. 6. Nhấn "In hóa đơn". |
| Kết quả mong đợi | Bước 4: hiển thị "Ghế đang chọn: B5" và giá. Bước 5: tổng tiền bằng giá 1 vé. Sau bước 5: B5 chuyển sang trạng thái đã bán; số ghế trống của S1 giảm từ 88 xuống 87. Bước 6: vé được in. |
| Kết quả thực tế | – |
| Trạng thái | Chưa thực hiện |

### TC-UC004-02 – Bán nhiều vé kèm combo bắp nước

| Mục | Nội dung |
|---|---|
| Tiền điều kiện | TD-01, TD-02, TD-05, TD-06 (thành công) |
| Các bước | 1–3 như TC-01. 4. Chọn ghế C7, C8. 5. Chọn combo C1, số lượng 1. 6. Thanh toán. |
| Kết quả mong đợi | Tổng tiền = 2 × giá vé + giá C1. Sau thanh toán: C7, C8 đã bán; số ghế trống giảm 2. Doanh thu bắp nước được ghi nhận riêng (phục vụ FR-026). |
| Kết quả thực tế | – |
| Trạng thái | Chưa thực hiện |

### TC-UC004-03 – Không cho bán vé suất chiếu đã hết ghế

| Mục | Nội dung |
|---|---|
| Tiền điều kiện | TD-01, TD-03 |
| Các bước | 1. Chọn phim của S2. 2. Chọn suất S2, nhấn Next. |
| Kết quả mong đợi | Hệ thống thông báo suất chiếu đã hết ghế, không chuyển sang bước chọn ghế. Số vé đã bán của S2 vẫn là 90. |
| Kết quả thực tế | – |
| Trạng thái | Chưa thực hiện |

### TC-UC004-04 – Không cho chọn ghế đã bán

| Mục | Nội dung |
|---|---|
| Tiền điều kiện | TD-01, TD-02 |
| Các bước | 1. Vào bước chọn ghế của S1. 2. Nhấn vào ghế A1. |
| Kết quả mong đợi | A1 và A2 hiển thị trạng thái đã bán; nhấn vào A1 không làm thay đổi "Ghế đang chọn". |
| Kết quả thực tế | – |
| Trạng thái | Chưa thực hiện |

### TC-UC004-05 – Không cho sang bước tiếp khi chưa chọn ghế

| Mục | Nội dung |
|---|---|
| Tiền điều kiện | TD-01, TD-02 |
| Các bước | 1. Vào bước chọn ghế của S1. 2. Không chọn ghế, nhấn Next. |
| Kết quả mong đợi | Hệ thống không chuyển sang bước Bắp/Nước, đồng thời yêu cầu chọn ít nhất một ghế. |
| Kết quả thực tế | – |
| Trạng thái | Chưa thực hiện |

### TC-UC004-06 – Thanh toán thất bại không làm mất ghế trống

| Mục | Nội dung |
|---|---|
| Tiền điều kiện | TD-01, TD-02, TD-06 (thất bại) |
| Các bước | 1. Chọn S1, ghế D10. 2. Thanh toán. |
| Kết quả mong đợi | Hệ thống thông báo thanh toán thất bại, quay lại bước chọn hình thức thanh toán. D10 vẫn trống; số ghế trống của S1 không đổi (88); không có vé nào được ghi nhận. |
| Kết quả thực tế | – |
| Trạng thái | Chưa thực hiện |

### TC-UC004-07 – Hai quầy cùng bán một ghế cùng lúc

| Mục | Nội dung |
|---|---|
| Tiền điều kiện | Hai tài khoản nhân viên đăng nhập trên hai máy (TD-01); TD-02; TD-06 (thành công) |
| Các bước | 1. Cả hai quầy cùng chọn S1, ghế E5. 2. Quầy 1 thanh toán thành công. 3. Quầy 2 thanh toán ngay sau đó. |
| Kết quả mong đợi | Chỉ một vé E5 được ghi nhận. Quầy 2 nhận thông báo ghế không còn trống và được yêu cầu chọn ghế khác. Số ghế trống chỉ giảm 1. |
| Kết quả thực tế | – |
| Trạng thái | Chưa thực hiện |

### TC-UC004-08 – Không cho bán vé suất chiếu đã bắt đầu

| Mục | Nội dung |
|---|---|
| Tiền điều kiện | TD-01, TD-04 |
| Các bước | 1. Chọn phim của S3. 2. Chọn suất S3. |
| Kết quả mong đợi | S3 không hiển thị trong danh sách, hoặc hiển thị nhưng không cho chọn kèm thông báo. Không có vé nào được bán. |
| Kết quả thực tế | – |
| Trạng thái | Chưa thực hiện |

### TC-UC004-09 – Không có chức năng hoàn/hủy vé đã thanh toán

| Mục | Nội dung |
|---|---|
| Tiền điều kiện | Vé B5 của S1 đã bán ở TC-UC004-01 |
| Các bước | 1. Tìm giao dịch của vé B5. 2. Tìm thao tác hủy hoặc hoàn vé. |
| Kết quả mong đợi | Không có thao tác hủy, hoàn hay đổi suất cho vé đã thanh toán; B5 vẫn ở trạng thái đã bán. |
| Kết quả thực tế | – |
| Trạng thái | Chưa thực hiện |

### TC-UC004-10 – Phải đăng nhập mới truy cập được chức năng bán vé

| Mục | Nội dung |
|---|---|
| Tiền điều kiện | Chưa đăng nhập |
| Các bước | 1. Mở ứng dụng. 2. Thử truy cập màn hình "Booking Movies" mà không đăng nhập. |
| Kết quả mong đợi | Hệ thống hiển thị màn hình đăng nhập; không truy cập được chức năng bán vé. |
| Kết quả thực tế | – |
| Trạng thái | Chưa thực hiện |

## 4. Độ phủ

| Hạng mục | Được phủ bởi |
|---|---|
| Luồng chính | TC-01 |
| A1 (bắp nước) | TC-02 |
| E1, E2, E3, E4, E5, E6, E8 | TC-03, TC-08, TC-04, TC-05, TC-06, TC-07, TC-09 |
| BR-002, BR-008 | TC-01, TC-03, TC-06, TC-07 |
| BR-003, BR-004 | TC-09 |
| BR-009, BR-010 | TC-10 |
| **Chưa phủ** | A2 (tìm theo tên), A3 (nút Back), A4 (vé điện tử – kênh gửi TBD), E7 (lỗi máy in), tính giá vé (BR-P05 – TBD) |
