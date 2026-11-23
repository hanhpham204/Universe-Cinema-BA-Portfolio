# UC-004 – Bán vé xem phim: Đặc tả chi tiết

> ⚠️ **Đề xuất bổ sung (PROPOSED).** Tài liệu học phần chỉ có mô tả ngắn cho UC004 (SRS B.III, A.I.1.d). Mục đặc tả luồng của UC004 trong SRS mục C là bản sao của UC002 (ISS-09). Bản đặc tả dưới đây được **viết thêm cho portfolio**, để minh họa cách hoàn thiện một use case cốt lõi. **Đây không phải sản phẩm của học phần.**
>
> Mỗi bước có cột **Căn cứ**, ghi rõ bước đó lấy từ tài liệu gốc (VERIFIED), suy ra từ mockup (INFERRED) hay do portfolio đề xuất (PROPOSED).
>
> **Phạm vi đã xác nhận (23/11/2026):** Nhân viên bán vé tại quầy; không hoàn vé, không đổi suất, không hủy vé sau khi thanh toán (ISS-01, ISS-02 đã giải quyết).

## 1. Thông tin chung

| Mục | Nội dung | Căn cứ |
|---|---|---|
| Use Case ID | UC-004 (mã gốc UC004) | SRS B.III |
| Tên | Bán vé xem phim | SRS B.III |
| Actor chính | Nhân viên bán vé | SRS B.II, A.I; UCD |
| Actor phụ | Hệ thống thanh toán | SRS A.II (INFERRED là actor) |
| Stakeholder và mối quan tâm | **Khách hàng:** nhận đúng vé, đúng ghế, đúng suất. **Người quản lí:** doanh thu ghi nhận chính xác, không bán trùng ghế. | INFERRED |
| Mục tiêu | Bán vé cho khách hàng: chọn suất chiếu, ghế, dịch vụ đi kèm, thanh toán, xuất vé | SRS A.I.1.d; DT II.1.e |
| Kích hoạt (Trigger) | Khách hàng tới quầy và chọn phim, suất chiếu muốn xem | SRS A.I ("Khi khách hàng chọn một phim và suất chiếu cụ thể…") |
| Tiền điều kiện | P1. Nhân viên đã đăng nhập (BR-009). P2. Đã có phim, phòng chiếu, suất chiếu trên hệ thống (UC-005, UC-009, UC-011). | P1: UCD. P2: INFERRED |
| Hậu điều kiện thành công | S1. Ghế đã chọn được ghi nhận là đã bán cho suất chiếu đó. S2. Số ghế còn trống được cập nhật. S3. Giao dịch được ghi nhận để thống kê doanh thu. S4. Khách nhận vé in hoặc vé điện tử. | S2: SRS A.I.1.d. S3: SRS A.I.2.g (INFERRED). S4: SRS A.I.1.d. S1: PROPOSED |
| Hậu điều kiện thất bại | Không ghế nào bị đánh dấu đã bán; số ghế trống giữ nguyên | PROPOSED |
| Quy tắc nghiệp vụ | BR-001, BR-002, BR-003, BR-004, BR-005, BR-008; đề xuất BR-P03, BR-P04, BR-P05, BR-P06 | Business Rules |
| Yêu cầu liên quan | FR-008 → FR-012; NFR-001, NFR-004, NFR-007; NFR-P04 | FR, NFR |
| Mockup | [WF-02](../assets/wireframes/wf02_booking_select_movie.png), [WF-03](../assets/wireframes/wf03_booking_select_seat.png), [WF-04](../assets/wireframes/wf04_booking_concession_payment.png) | SRS A.I.1.d |

## 2. Luồng chính (Basic Flow)

| Bước | Actor | Hệ thống | Căn cứ |
|---|---|---|---|
| 1 | Chọn chức năng "Booking Movies" | | MU WF-02 (INFERRED) |
| 2 | | Hiển thị bước 1 "Chọn Phim": ô chọn ngày, ô tìm kiếm, danh sách phim chiếu trong ngày | MU WF-02 (INFERRED) |
| 3 | Chọn ngày và phim theo yêu cầu của khách | | MU WF-02 (INFERRED) |
| 4 | | Hiển thị thông tin phim và danh sách suất chiếu của phim trong ngày: giờ chiếu, phòng chiếu, số ghế còn trống | SRS A.I.1.c (VERIFIED); hiển thị suất chiếu ở bước này: PROPOSED (ISS-22) |
| 5 | Chọn suất chiếu, nhấn "Next" | | SRS A.I.1.d (VERIFIED) |
| 6 | | Kiểm tra suất chiếu còn ghế trống và chưa bắt đầu; hiển thị bước 2 "Chọn ghế": sơ đồ ghế, màn hình, lối vào, trạng thái ghế | BR-002 (VERIFIED); BR-P04 (PROPOSED); MU WF-03 |
| 7 | Chọn một hoặc nhiều ghế theo yêu cầu của khách | | SRS A.I.1.d (VERIFIED) |
| 8 | | Hiển thị danh sách "Ghế đang chọn" và giá vé | MU WF-03 (INFERRED); quy tắc giá: TBD (BR-P05) |
| 9 | Nhấn "Next" | | MU WF-03 |
| 10 | | Hiển thị bước 3 "Bắp/Nước": danh sách loại/combo, tóm tắt tên phim, giá vé, tổng tiền | MU WF-04 (INFERRED) |
| 11 | Chọn hình thức thanh toán, xác nhận thanh toán | | SRS A.I (VERIFIED); MU WF-04 |
| 12 | | Gửi yêu cầu thanh toán tới Hệ thống thanh toán, nhận kết quả thành công | SRS A.II (VERIFIED) |
| 13 | | Kiểm tra lại các ghế vẫn còn trống, ghi nhận vé, cập nhật số ghế còn trống | BR-008 (VERIFIED); kiểm tra lại: NFR-P04 (PROPOSED) |
| 14 | Nhấn "In hóa đơn" / in vé, hoặc chọn gửi vé điện tử | | SRS A.I.1.d (VERIFIED); MU WF-04 |
| 15 | | Xuất vé, kết thúc use case | SRS A.I.1.d (VERIFIED) |

## 3. Luồng thay thế (Alternative Flows)

| Mã | Tại bước | Điều kiện | Xử lý | Căn cứ |
|---|---|---|---|---|
| A1 | 10 | Khách mua thêm bắp/nước | A1.1 Nhân viên chọn loại/combo và số lượng. A1.2 Hệ thống cộng vào tổng tiền. Quay lại bước 11. | DT II.1.e; MU WF-04 (INFERRED) |
| A2 | 3 | Nhân viên tìm phim theo tên | A2.1 Nhập từ khóa vào ô Search. A2.2 Hệ thống lọc danh sách. Quay lại bước 3. | MU WF-02; UC-002 (INFERRED) |
| A3 | 7–10 | Nhân viên muốn quay lại bước trước (đổi phim, suất, ghế) | Nhấn "Back"; hệ thống giữ lựa chọn đã có của bước trước, bỏ chọn ghế nếu đổi suất chiếu | MU (nút Back – INFERRED) |
| A4 | 14 | Khách muốn nhận vé điện tử | Hệ thống gửi vé điện tử. Kênh gửi (email/SMS…): TBD | SRS A.I.1.d (VERIFIED); kênh: TBD |

## 4. Luồng ngoại lệ (Exception Flows)

| Mã | Tại bước | Điều kiện | Xử lý | Căn cứ |
|---|---|---|---|---|
| E1 | 6 | Suất chiếu đã hết ghế | Thông báo "Suất chiếu đã hết ghế", không cho sang bước 2; quay lại bước 4 để chọn suất khác | BR-002 (VERIFIED) |
| E2 | 6 | Suất chiếu đã bắt đầu | Thông báo, không cho bán; quay lại bước 4 | BR-P04 (PROPOSED) |
| E3 | 7 | Nhân viên chọn ghế đã bán | Ghế đã bán hiển thị khác màu và không chọn được | BR-P03 (PROPOSED); MU WF-03 có chú thích "Đã chọn" |
| E4 | 9 | Chưa chọn ghế nào | Nút "Next" bị vô hiệu hoặc hệ thống yêu cầu chọn ít nhất một ghế | PROPOSED |
| E5 | 12 | Thanh toán thất bại hoặc bị hủy | Thông báo lỗi; không ghi nhận vé; ghế vẫn trống; quay lại bước 11 | PROPOSED |
| E6 | 13 | Ghế vừa được bán ở quầy khác trong lúc đang thanh toán | Thông báo ghế không còn trống, yêu cầu chọn ghế khác (quay lại bước 7). Xử lý tiền đã thanh toán: TBD | NFR-P04 (PROPOSED) |
| E7 | 14 | Máy in lỗi | Cho phép in lại vé của giao dịch vừa hoàn tất mà không tạo giao dịch mới | PROPOSED |
| E8 | Sau 15 | Khách yêu cầu hoàn vé hoặc hủy vé | Hệ thống không hỗ trợ hoàn, đổi hay hủy vé | BR-003, BR-004 (VERIFIED, đã xác nhận) |

## 5. Yêu cầu đặc biệt

| Mã | Yêu cầu | Căn cứ |
|---|---|---|
| SR1 | Không được bán một ghế của một suất chiếu cho hai vé, kể cả khi hai quầy thao tác cùng lúc | BR-002; NFR-P04 |
| SR2 | Nhân viên mới hoàn thành được giao dịch mà không cần đào tạo chuyên sâu | NFR-002 |
| SR3 | Hiển thị phân loại độ tuổi của phim ở bước chọn phim | BR-P06; MU WF-02 |

## 6. Câu hỏi mở riêng cho UC-004

| # | Câu hỏi | Liên quan |
|---|---|---|
| 1 | Nhân viên chọn ghế cụ thể hay chỉ chọn số lượng vé? | ISS-22 |
| 2 | Có giữ ghế tạm thời ("xác nhận đặt chỗ") trước khi thanh toán không? Giữ bao lâu? | ISS-21 |
| 3 | Các hình thức thanh toán được chấp nhận? Giá vé tính theo tiêu chí nào? | ISS-17 |
| 4 | Người quản lí có được bán vé không (mockup ghi "Welcome Admin")? | ISS-15 |
| 5 | ~~Có hoàn vé / đổi suất không?~~ Đã trả lời: không (23/11/2026) | ISS-02 |

## 7. Sơ đồ quy trình

Xem [BP-02 – Bán vé tại quầy](../04_Business_Process/Activity_Diagram.md#3-bp-02--bán-vé-tại-quầy). Test case thiết kế cho use case này: [Test Cases – UC-004](../09_Test_Design/Test_Cases_UC-004_Sell_Ticket.md).
