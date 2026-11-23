# Assumptions and Open Questions – Giả định và vấn đề cần xác minh

> Tài liệu này ghi nhận các **mâu thuẫn, khoảng trống và điểm chưa rõ** phát hiện khi đối chiếu [SRS], [DT], [UCD] và [MU].
> Nguyên tắc: khi hai tài liệu mâu thuẫn, portfolio **ghi nhận cả hai phiên bản** và **không tự chọn**.

## 1. Danh sách vấn đề (Issue Log)

Phân loại: **Mâu thuẫn** (hai nguồn nói khác nhau) · **Khoảng trống** (thiếu thông tin) · **Không nhất quán** (tên gọi/cấu trúc lệch nhau) · **Chất lượng** (lỗi biên soạn).

| ID | Loại | Mô tả | Phiên bản A | Phiên bản B | Ảnh hưởng | Trạng thái |
|---|---|---|---|---|---|---|
| ISS-01 | Mâu thuẫn | **Kênh bán vé và actor Khách hàng** | DT II.1: "người dùng" tự đăng ký, tìm phim, đặt vé, chọn bắp nước, thanh toán **trên trang web**. UCD đặt tên ranh giới là "Website đặt vé xem phim online". | SRS A.I: "**Nhân viên** sẽ là người thực hiện việc đặt vé cho khách hàng". Bảng actor SRS B.II và UCD chỉ có Nhân viên và Người quản lí. Mockup có dạng cửa sổ ứng dụng. | Phạm vi hệ thống, actor, FR-002, FR-009, BR-001 | **Đã giải quyết** (xác nhận 23/11/2026): phần mềm bán vé tại quầy; khách hàng không phải actor; FR-002 ngoài phạm vi |
| ISS-02 | Mâu thuẫn | **Hoàn vé / đổi suất chiếu** | DT II: nhân viên "xử lý các vấn đề phát sinh như đổi suất chiếu hoặc hoàn vé". | SRS A.I: "không cho phép hoàn vé sau khi đã thanh toán… không có tùy chọn hủy vé". | BR-003, BR-004, FR-034 | **Đã giải quyết** (xác nhận 23/11/2026): không hoàn vé, không đổi suất, không hủy vé; FR-034 ngoài phạm vi |
| ISS-03 | Mâu thuẫn | **Xóa rạp chiếu phim** | SRS A.I.2.b, DT II.2.c: chỉ thêm, sửa, xem danh sách. | SRS B.III UC008: "thêm, sửa, hoặc **xóa**". | FR-020, UC-008 | Mở – TBD |
| ISS-04 | Không nhất quán | **Tiêu chí tìm kiếm phim** có 5 phiên bản | SRS A.I.1.b: tên phim, thể loại, thời gian chiếu, rạp chiếu. SRS B.III: tên phim, thể loại, thời gian chiếu. UCD: tên phim, thời gian chiếu, thể loại. | DT II.1.b: tên phim, thể loại, diễn viên, đạo diễn, năm phát hành. SRS C.II: tên phim, thể loại, diễn viên, đạo diễn, năm sản xuất. | FR-003, UC-002 | Mở – TBD |
| ISS-05 | Không nhất quán | **Tên và số lượng actor** | SRS B.II: 2 actor (Nhân viên bán vé, Người quản lí). UCD: Nhân viên, Quản trị viên. | SRS A.II: 3 nhóm (Nhân viên bán vé, Nhân viên quản lý phòng chiếu, Quản lý rạp phim). DT dùng "Nhân viên quản lý rạp chiếu", "Admin", "Nhân viên quản lí rạp" cho cùng một nhóm chức năng. | Actor, phân quyền | Giả định A-01 |
| ISS-06 | Không nhất quán | **Tên hệ thống** | "Universe Cinema" (SRS, DT). | "CinemaPro" (DT II – một lần, đoạn mô tả Admin). | Thuật ngữ | Giả định A-02 |
| ISS-07 | Khoảng trống | **Lịch chiếu và Suất chiếu** là hai UC riêng (UC-010, UC-011) nhưng chưa được định nghĩa khác nhau thế nào. Bảng thuật ngữ SRS A.III để trống. | Lịch chiếu: ngày giờ chiếu, phòng chiếu. | Suất chiếu: giờ bắt đầu, giờ kết thúc, phòng chiếu. | UC-010, UC-011, ERD | Mở – TBD |
| ISS-08 | Không nhất quán | **Quản lý phim**: danh mục tách 3 UC, sơ đồ gộp làm 1 | SRS B.III: UC005 Thêm, UC006 Sửa, UC007 Xóa phim. | UCD: một use case "Quản lí phim". | UCD, Catalog | Mở |
| ISS-09 | Chất lượng | **Đặc tả UC003–UC013 trong SRS mục C là bản sao của UC002**: mục đích, mô tả, điều kiện đều nói về tìm kiếm phim; tên UC trong bảng chỉ ghi "UC00x_". | – | – | Không dùng làm căn cứ cho UC-003 → UC-013 | Đã xử lý trong portfolio |
| ISS-10 | Khoảng trống | UC002 – điều kiện sau nhắc tới "**đánh giá**" và "**thêm vào danh sách yêu thích**", nhưng không có chức năng/UC nào khác đề cập. | – | – | UC-002 | Mở – TBD |
| ISS-11 | Khoảng trống | **Chức năng có mô tả nhưng chưa có UC/trên sơ đồ**: Xem chi tiết phim, Đăng ký tài khoản, Dashboard tổng quan, Phân quyền, Quản lý đơn đặt vé/đơn hàng, Quản lý khuyến mãi và giá vé, Kiểm tra vé hợp lệ, Quản lý nhân viên, Quản lý thiết bị (SRS A.II). | – | – | FR-002, FR-005, FR-029 → FR-035 | Mở – TBD |
| ISS-12 | Khoảng trống | **"Người dùng" trong UC-012 là ai?** | Mockup WF-07: menu "Customers"; DT II.2.a: thống kê "khách hàng mới đăng ký". | Mockup WF-07: cột Gender, **Shift**, **Role** (thông tin nhân viên); SRS A.I: "quản lý nhân viên". | UC-012, FR-025, FR-035 | Mở – TBD |
| ISS-13 | Không nhất quán | **Phạm vi thống kê** khác nhau giữa hai tài liệu (không đối lập trực tiếp) | DT II.2.a: doanh thu theo ngày, tháng, phim, rạp; khách hàng mới; tổng vé trong ngày. | SRS A.I.2.g: theo ngày, tuần, tháng, rạp; lọc theo phim, phòng, khuyến mãi; xuất Excel/PDF. | UC-013, FR-026 → FR-029 | Đã hợp nhất ở mức yêu cầu |
| ISS-14 | Khoảng trống | **Quản lý suất chiếu**: câu mô tả có "thêm, sửa, xóa, xem", nhưng chi tiết chỉ có Thêm và Danh sách. | – | – | FR-024 | Mở |
| ISS-15 | Không nhất quán | **Ai được bán vé / tìm phim?** | UCD: chỉ Nhân viên. | SRS C.II (UC002): "Nhân viên và Người quản lý"; mockup bán vé hiển thị "Welcome Admin". | UC-002 → UC-004, phân quyền | Mở – TBD |
| ISS-16 | Chất lượng | **Ký pháp UCD**: mọi UC «include» Đăng nhập; UC Đăng nhập không nối trực tiếp với actor. Về thực hành, đăng nhập thường là tiền điều kiện. | – | – | UCD | Nhận xét review |
| ISS-17 | Khoảng trống | **Thanh toán và giá vé**: chưa có phương thức thanh toán, quy tắc tính giá, cách áp dụng khuyến mãi. | – | – | FR-010, BR-P05 | Mở – TBD |
| ISS-18 | Chất lượng | **NFR chưa đo lường được** (không có chỉ số, ngưỡng). | – | – | NFR-001 → NFR-005 | Đã đề xuất NFR-P01 → P07 |
| ISS-19 | Khoảng trống | **Các mục mẫu còn trống**: SRS A.III (thuật ngữ), A.III.1 (tài liệu tham khảo), B.IV (điều kiện phụ thuộc), D (thông tin hỗ trợ), mục "Biểu đồ" của từng UC; DT V (Sơ đồ lớp). | – | – | Không có căn cứ công nghệ, mô hình dữ liệu | Ghi nhận |
| ISS-20 | Chất lượng | **Dữ liệu minh họa trong mockup Dashboard**: số liệu tổng doanh thu/số vé và biểu đồ mẫu (nhãn "Fiat/Audi/Ford") không phải dữ liệu thật. | – | – | WF-08 | Đã chú thích |
| ISS-21 | Khoảng trống | SRS B.II: nhân viên "kiểm tra tình trạng vé, **xác nhận đặt chỗ**". Chưa rõ có đặt chỗ trước (giữ ghế) hay không. | – | – | UC-004, FR-031 | Mở – TBD |
| ISS-22 | Không nhất quán | **Cách chọn vé** | SRS A.I: "chọn **số lượng vé**". | SRS A.I.1.d và mockup WF-03: chọn **ghế cụ thể**. Mockup WF-02 chưa có bước chọn suất chiếu. | UC-004, BP-02 | Mở – TBD |

## 2. Giả định đang áp dụng trong portfolio

| ID | Giả định | Lý do | Liên quan |
|---|---|---|---|
| A-01 | Dùng thống nhất 2 actor **Nhân viên bán vé** và **Người quản lí** theo SRS B.II. | SRS B.II là bảng actor chính thức duy nhất; khớp số actor trên UCD. | ISS-05 |
| A-02 | Tên hệ thống là **Universe Cinema**. "CinemaPro" được xem là lỗi biên soạn. | "Universe Cinema" xuất hiện ở cả hai tài liệu và trên mockup (logo). | ISS-06 |
| A-03 | Mã UC-xxx giữ nguyên thứ tự và nội dung của UC001–UC013 trong SRS B.III. | Bảo toàn truy vết về tài liệu gốc. | Catalog |
| A-04 | Số trang trích dẫn lấy từ bản PDF chuyển đổi bằng LibreOffice. | File gốc là .docx, không có trang cố định. | Source Traceability |
| A-05 | Portfolio **không giả định** công nghệ, hệ quản trị CSDL hay việc hệ thống đã được lập trình/triển khai. | Không có tài liệu nào nói về điều này. | ISS-19 |

## 3. Câu hỏi cần chủ portfolio xác nhận (TBD)

### Về nội dung nghiệp vụ

| # | Câu hỏi | Liên quan |
|---|---|---|
| Q-01 | Phiên bản cuối cùng của nhóm là hệ thống **nội bộ cho nhân viên bán vé tại quầy** (SRS) hay có cả **website cho khách hàng tự đặt vé** (DT)? → ✅ **Đã trả lời** (xác nhận 23/11/2026): phần mềm bán vé tại quầy. | ISS-01 |
| Q-02 | Quy tắc cuối cùng về **hoàn vé / đổi suất chiếu** là gì? → ✅ **Đã trả lời** (xác nhận 23/11/2026): không hoàn, không đổi, không hủy. | ISS-02 |
| Q-03 | Quản lý rạp có chức năng **xóa** không? | ISS-03 |
| Q-04 | Tiêu chí tìm kiếm phim chính thức gồm những gì? | ISS-04 |
| Q-05 | "Lịch chiếu" khác "Suất chiếu" như thế nào trong thiết kế của nhóm? | ISS-07 |
| Q-06 | "Người dùng" trong UC-012 là nhân viên hay khách hàng? | ISS-12 |
| Q-07 | Người quản lí có được bán vé / tìm phim không? | ISS-15 |
| Q-08 | Trong hai tài liệu, tài liệu nào là bản nộp cuối cùng? (DT ghi ngày 19/08/2024; SRS ghi tháng 08/2024, V1.0) | Tất cả mâu thuẫn |

### Về vai trò cá nhân và quyền xuất bản

| # | Câu hỏi | Liên quan |
|---|---|---|
| Q-09 | Tài liệu gốc **không có bảng phân công công việc**. Bạn có bằng chứng nào (bảng phân công, lịch sử chỉnh sửa, xác nhận của nhóm) cho phần bạn thực hiện: phân tích yêu cầu, viết SRS, thiết kế Use Case Diagram? Bạn phụ trách **những mục nào** của SRS? → ✅ **Đã trả lời** (xác nhận 23/11/2026): tham gia toàn bộ các mục của SRS (tự xác nhận; tài liệu gốc không có bảng phân công để đối chiếu). | Project Overview, README |
| Q-10 | Ai thiết kế mockup giao diện? Có nên ghi nhận tên vai trò (không ghi tên người) không? | 06_UI_Wireframes |
| Q-11 | Hệ thống có được lập trình/demo trong học phần không? Nếu có, dùng công nghệ gì? (Portfolio hiện **không ghi** công nghệ nào.) | ISS-19 |
| Q-12 | Nhóm và giảng viên có đồng ý cho công khai nội dung tài liệu học phần trên GitHub không? → ✅ **Đã trả lời** (xác nhận 23/11/2026): đồng ý. | README – Ghi chú học thuật |
| Q-13 | Bạn muốn hiển thị tên, LinkedIn, email của mình trong README không? (Hiện để trống.) | README |
