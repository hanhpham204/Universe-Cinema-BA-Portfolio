# Functional Requirements – Yêu cầu chức năng

> **Phạm vi tài liệu:** Danh sách yêu cầu chức năng của hệ thống Universe Cinema, được hợp nhất từ hai tài liệu học phần [SRS] và [DT].
> **Quy ước nguồn và trạng thái:** xem [Source Traceability](../07_Traceability/Source_Traceability.md).
> **Lưu ý:** Mã FR-xxx do portfolio đặt để truy vết. Tài liệu gốc không đánh mã yêu cầu chức năng mà chỉ đánh mã use case (UC001–UC013).

## 1. Bảng tổng hợp

| ID | Tên yêu cầu | Actor | Use Case | Trạng thái |
|---|---|---|---|---|
| FR-001 | Đăng nhập hệ thống | Nhân viên bán vé, Người quản lí | UC-001 | VERIFIED |
| FR-002 | Đăng ký tài khoản | Người dùng (theo DT) | – | OUT OF SCOPE |
| FR-003 | Tìm kiếm phim theo tiêu chí | Nhân viên bán vé | UC-002 | VERIFIED |
| FR-004 | Lọc phim đang chiếu / sắp chiếu | Nhân viên bán vé | UC-002 | VERIFIED |
| FR-005 | Xem thông tin chi tiết phim | Nhân viên bán vé | UC-002 (INFERRED) | VERIFIED |
| FR-006 | Xem lịch chiếu theo rạp và ngày | Nhân viên bán vé | UC-003 | VERIFIED |
| FR-007 | Hiển thị thông tin và ghế trống của suất chiếu | Nhân viên bán vé | UC-003 | VERIFIED |
| FR-008 | Bán vé: chọn phim, suất chiếu, ghế ngồi | Nhân viên bán vé | UC-004 | VERIFIED |
| FR-009 | Chọn dịch vụ đi kèm (bắp, nước, snack) | Nhân viên bán vé | UC-004 | INFERRED |
| FR-010 | Thanh toán giao dịch | Nhân viên bán vé | UC-004 | VERIFIED |
| FR-011 | In vé hoặc gửi vé điện tử | Nhân viên bán vé | UC-004 | VERIFIED |
| FR-012 | Kiểm tra và cập nhật tự động ghế trống | Hệ thống | UC-004 | VERIFIED |
| FR-013 | Thêm phim | Người quản lí | UC-005 | VERIFIED |
| FR-014 | Sửa thông tin phim | Người quản lí | UC-006 | VERIFIED |
| FR-015 | Xóa phim | Người quản lí | UC-007 | VERIFIED |
| FR-016 | Xem danh sách phim | Người quản lí | UC-005/006/007 (INFERRED) | VERIFIED |
| FR-017 | Thêm rạp chiếu phim | Người quản lí | UC-008 | VERIFIED |
| FR-018 | Sửa thông tin rạp chiếu phim | Người quản lí | UC-008 | VERIFIED |
| FR-019 | Xem danh sách rạp chiếu phim | Người quản lí | UC-008 | VERIFIED |
| FR-020 | Xóa rạp chiếu phim | Người quản lí | UC-008 | TBD |
| FR-021 | Quản lý phòng chiếu | Người quản lí | UC-009 | VERIFIED |
| FR-022 | Quản lý ghế ngồi trong phòng chiếu | Người quản lí | UC-009 | VERIFIED |
| FR-023 | Quản lý lịch chiếu | Người quản lí | UC-010 | VERIFIED |
| FR-024 | Quản lý suất chiếu | Người quản lí | UC-011 | VERIFIED |
| FR-025 | Quản lý người dùng | Người quản lí | UC-012 | VERIFIED |
| FR-026 | Báo cáo doanh thu | Người quản lí | UC-013 | VERIFIED |
| FR-027 | Lọc báo cáo doanh thu | Người quản lí | UC-013 | VERIFIED |
| FR-028 | Xuất báo cáo doanh thu (Excel/PDF) | Người quản lí | UC-013 | VERIFIED |
| FR-029 | Màn hình tổng quan (dashboard) | Người quản lí | UC-013 (INFERRED) | VERIFIED |
| FR-030 | Phân quyền người dùng | Người quản lí | – | VERIFIED |
| FR-031 | Theo dõi và quản lý đơn đặt vé | Nhân viên bán vé, Người quản lí | – | VERIFIED |
| FR-032 | Quản lý khuyến mãi và giá vé | Người quản lí | – | TBD |
| FR-033 | Kiểm tra tính hợp lệ của vé tại rạp | Nhân viên | – | TBD |
| FR-034 | Đổi suất chiếu / hoàn vé | Nhân viên | – | OUT OF SCOPE |
| FR-035 | Quản lý nhân viên | Người quản lí | – | TBD |

> **Ghi chú về Actor:** Tài liệu gốc dùng nhiều tên khác nhau cho cùng một vai trò, chẳng hạn "Nhân viên", "Nhân viên bán vé", "Người quản lí", "Admin", "Quản trị viên". Portfolio dùng thống nhất hai tên trong bảng tác nhân của SRS (mục B.II) là **Nhân viên bán vé** và **Người quản lí**. Xem ISS-05.
>
> **Ghi chú về Priority:** Tài liệu gốc **không xác định độ ưu tiên**. Mục 3 có một bảng ưu tiên *đề xuất bổ sung* (PROPOSED).

---

## 2. Đặc tả chi tiết

### Nhóm A – Truy cập hệ thống

#### FR-001 – Đăng nhập hệ thống

| Thuộc tính | Nội dung |
|---|---|
| Description | Nhân viên dùng tài khoản cá nhân (tên đăng nhập và mật khẩu) để truy cập hệ thống. Hệ thống kiểm tra, xác thực quyền truy cập, rồi chuyển người dùng đến giao diện chính với các chức năng được phân quyền. |
| Actor | Nhân viên bán vé, Người quản lí |
| Preconditions | Người dùng đã có tài khoản (SRS C.I) |
| Inputs | Tên đăng nhập, mật khẩu |
| Outputs | Giao diện trang chủ; hoặc thông báo "tài khoản hoặc mật khẩu không đúng" |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.1.a, B.III UC001, C.I; DT II.1.a; UCD; MU `wf01` |
| Verification Status | VERIFIED |

#### FR-002 – Đăng ký tài khoản

| Thuộc tính | Nội dung |
|---|---|
| Description | Người dùng tạo tài khoản mới với email, mật khẩu và tên người dùng, sau đó đăng nhập để dùng các tính năng cá nhân hóa trên trang web. |
| Actor | "Người dùng" (DT không nói rõ là khách hàng hay nhân viên) |
| Inputs | Email, mật khẩu, tên người dùng |
| Priority | Chưa có căn cứ |
| Source Reference | DT II.1.a |
| Verification Status | OUT OF SCOPE – **Đã xác nhận** bởi chủ portfolio ngày 23/11/2026: hệ thống là phần mềm bán vé tại quầy, không có kênh cho khách hàng tự đăng ký. Tài khoản nhân viên đã có sẵn (SRS UC001). |

### Nhóm B – Tra cứu phim và lịch chiếu

#### FR-003 – Tìm kiếm phim theo tiêu chí

| Thuộc tính | Nội dung |
|---|---|
| Description | Người dùng tìm kiếm thông tin phim bằng bộ lọc. Hệ thống trả về danh sách phim phù hợp. |
| Actor | Nhân viên bán vé (theo UCD); SRS C.II ghi "Nhân viên và Người quản lý" |
| Preconditions | Người dùng đã đăng nhập (SRS C.II) |
| Inputs | Một hoặc nhiều tiêu chí tìm kiếm. **Danh sách tiêu chí chưa thống nhất** giữa các nguồn (xem ISS-04): tên phim, thể loại, thời gian chiếu, rạp chiếu, diễn viên, đạo diễn, năm phát hành/sản xuất |
| Outputs | Danh sách phim gồm poster, tên phim, năm sản xuất, thể loại, diễn viên chính (SRS C.II – điều kiện sau) |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.1.b, B.III UC002, C.II; DT II.1.b; UCD (Tìm theo tên phim / thời gian chiếu / thể loại) |
| Verification Status | VERIFIED (tiêu chí: TBD) |

#### FR-004 – Lọc phim đang chiếu / sắp chiếu

| Thuộc tính | Nội dung |
|---|---|
| Description | Người dùng lọc danh sách phim theo nhóm "đang chiếu" hoặc "sắp chiếu". |
| Actor | Nhân viên bán vé |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.1.b; DT II.1.b |
| Verification Status | VERIFIED |

#### FR-005 – Xem thông tin chi tiết phim

| Thuộc tính | Nội dung |
|---|---|
| Description | Hiển thị thông tin chi tiết của một phim. |
| Actor | Nhân viên bán vé |
| Outputs | Tóm tắt nội dung, dàn diễn viên, đạo diễn, thời lượng, thể loại, trailer (DT II.1.c); thời gian chiếu, mô tả ngắn (SRS A.I.1.b) |
| Priority | Chưa có căn cứ |
| Source Reference | DT II.1.c; SRS A.I.1.b, C.II; MU `wf02` (khung thông tin phim bên phải) |
| Verification Status | VERIFIED. Chưa có UC riêng; việc gắn với UC-002 là INFERRED. |

#### FR-006 – Xem lịch chiếu theo rạp và ngày

| Thuộc tính | Nội dung |
|---|---|
| Description | Xem lịch chiếu phim theo từng rạp và từng ngày. DT bổ sung thêm cách xem theo phim (chọn một phim để xem lịch chiếu tại các rạp). Nhân viên dùng lịch chiếu để tư vấn khách chọn suất chiếu phù hợp. |
| Actor | Nhân viên bán vé |
| Inputs | Rạp, ngày (và phim, theo DT) |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.1.c, B.III UC003; DT II.1.d; UCD |
| Verification Status | VERIFIED |

#### FR-007 – Hiển thị thông tin và ghế trống của suất chiếu

| Thuộc tính | Nội dung |
|---|---|
| Description | Với mỗi suất chiếu, hệ thống hiển thị thời gian chiếu, phòng chiếu và số lượng ghế còn trống. |
| Actor | Nhân viên bán vé |
| Outputs | Thời gian chiếu, phòng chiếu, số ghế còn trống |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.1.c, B.III UC003 |
| Verification Status | VERIFIED |

### Nhóm C – Bán vé

#### FR-008 – Bán vé: chọn phim, suất chiếu, ghế ngồi

| Thuộc tính | Nội dung |
|---|---|
| Description | Khi khách hàng chọn phim và suất chiếu, nhân viên thực hiện đặt vé trên hệ thống: chọn suất chiếu, chọn ghế ngồi, chọn số lượng vé. |
| Actor | Nhân viên bán vé |
| Preconditions | Người dùng đã đăng nhập (UCD – «include» Đăng nhập) |
| Inputs | Phim, suất chiếu, ghế ngồi / số lượng vé |
| Outputs | Ghế được chọn, giá (MU `wf03`) |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I, A.I.1.d, B.III UC004; DT II.1.e; UCD; MU `wf02`, `wf03` |
| Verification Status | VERIFIED |

#### FR-009 – Chọn dịch vụ đi kèm

| Thuộc tính | Nội dung |
|---|---|
| Description | Trong quá trình mua vé, chọn thêm dịch vụ đi kèm như bắp rang, nước, snack. |
| Actor | Nhân viên bán vé (MU: bước 3 "Bắp/Nước" trong màn hình Booking). DT mô tả người dùng tự chọn trên website, nhưng kênh này đã được xác nhận nằm ngoài phạm vi (ISS-01). |
| Inputs | Loại / combo bắp nước (MU `wf04`) |
| Priority | Chưa có căn cứ |
| Source Reference | DT II.1.e; MU `wf04`; SRS A.I.2.g (doanh thu từ bắp rang, nước uống) |
| Verification Status | INFERRED – có trong DT và mockup nhưng không có trong mô tả UC004 của SRS |

#### FR-010 – Thanh toán giao dịch

| Thuộc tính | Nội dung |
|---|---|
| Description | Xử lý thanh toán cho vé và dịch vụ đi kèm thông qua hệ thống thanh toán. |
| Actor | Nhân viên bán vé |
| Inputs | Hình thức thanh toán (MU `wf04` – "Chọn hình thức thanh toán"); danh sách hình thức **chưa có căn cứ** |
| Outputs | Tổng tiền (MU `wf04`); giao dịch được ghi nhận |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I, A.II (Hệ thống thanh toán); DT II.1.e; MU `wf04` |
| Verification Status | VERIFIED (phương thức thanh toán: TBD – ISS-17) |

#### FR-011 – In vé hoặc gửi vé điện tử

| Thuộc tính | Nội dung |
|---|---|
| Description | Sau khi thanh toán thành công, nhân viên có thể in vé hoặc gửi vé điện tử cho khách hàng. |
| Actor | Nhân viên bán vé |
| Preconditions | Thanh toán thành công |
| Outputs | Vé in / vé điện tử; MU `wf04` có nút "In hóa đơn" |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.1.d; MU `wf04` |
| Verification Status | VERIFIED |

#### FR-012 – Kiểm tra và cập nhật tự động ghế trống

| Thuộc tính | Nội dung |
|---|---|
| Description | Hệ thống tự động kiểm tra số ghế còn trống của phòng chiếu, không cho bán vé vượt quá số ghế có sẵn, và cập nhật số ghế còn trống sau mỗi giao dịch bán vé. |
| Actor | Hệ thống |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I, A.I.1.d, B.III UC004 |
| Verification Status | VERIFIED – liên quan BR-002, BR-008 |

### Nhóm D – Quản lý phim

#### FR-013 – Thêm phim

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí thêm phim mới vào hệ thống và có thể tải lên hình ảnh, trailer phim. |
| Actor | Người quản lí |
| Inputs | Tên phim, thể loại, đạo diễn, diễn viên, ngày phát hành, thời lượng, mô tả phim, hình ảnh, trailer (SRS A.I.2.a; DT II.2.b). MU `wf05` chỉ có: Movie Title, Genre, Duration, Date, ảnh (Import). |
| Outputs | Phim mới xuất hiện trong danh sách phim |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.a, B.III UC005; DT II.2.b; MU `wf05` |
| Verification Status | VERIFIED |

#### FR-014 – Sửa thông tin phim

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí chỉnh sửa thông tin phim khi có thay đổi hoặc cần bổ sung. |
| Actor | Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.a, B.III UC006; DT II.2.b; MU `wf05` (nút Update) |
| Verification Status | VERIFIED |

#### FR-015 – Xóa phim

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí xóa phim khỏi hệ thống. |
| Actor | Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.a, B.III UC007; DT II.2.b; MU `wf05` (nút Delete) |
| Verification Status | VERIFIED. Ràng buộc khi phim đã có suất chiếu/vé: **chưa có căn cứ** (xem BR-P02, đề xuất). |

#### FR-016 – Xem danh sách phim

| Thuộc tính | Nội dung |
|---|---|
| Description | Hiển thị danh sách tất cả phim trên hệ thống kèm các thông tin cơ bản. |
| Actor | Người quản lí |
| Outputs | Movie Title, Genre, Duration, Showing Date (MU `wf05`) |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.a; DT II.2.b; MU `wf05` |
| Verification Status | VERIFIED |

### Nhóm E – Quản lý rạp, phòng chiếu, ghế

#### FR-017 – Thêm rạp chiếu phim

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí thêm rạp chiếu phim mới. |
| Actor | Người quản lí |
| Inputs | Tên rạp, địa chỉ, số điện thoại liên hệ, thông tin liên quan khác |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.b, B.III UC008; DT II.2.c |
| Verification Status | VERIFIED |

#### FR-018 – Sửa thông tin rạp chiếu phim

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí chỉnh sửa thông tin rạp khi có thay đổi. |
| Actor | Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.b, B.III UC008; DT II.2.c |
| Verification Status | VERIFIED |

#### FR-019 – Xem danh sách rạp chiếu phim

| Thuộc tính | Nội dung |
|---|---|
| Description | Hiển thị danh sách tất cả các rạp trên hệ thống kèm thông tin cơ bản. |
| Actor | Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.b; DT II.2.c |
| Verification Status | VERIFIED |

#### FR-020 – Xóa rạp chiếu phim

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí xóa thông tin rạp chiếu phim. |
| Actor | Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | SRS B.III UC008 ("thêm, sửa, hoặc xóa") |
| Verification Status | TBD – SRS A.I.2.b và DT II.2.c chỉ có thêm, sửa, xem danh sách (ISS-03) |

#### FR-021 – Quản lý phòng chiếu

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí thêm mới, sửa đổi, xóa và xem danh sách phòng chiếu. |
| Actor | Người quản lí |
| Inputs | Tên phòng, số lượng ghế, thông tin liên quan khác |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.c, B.III UC009; DT II.2.d; UCD |
| Verification Status | VERIFIED |

#### FR-022 – Quản lý ghế ngồi trong phòng chiếu

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí thêm mới, sửa đổi, xóa ghế ngồi trong từng phòng chiếu để sơ đồ ghế luôn chính xác và cập nhật. |
| Actor | Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.c, B.III UC009; DT II.2.d. MU `wf03` minh họa sơ đồ ghế (hàng A–F, 15 ghế/hàng) ở màn hình bán vé. |
| Verification Status | VERIFIED |

### Nhóm F – Quản lý lịch chiếu và suất chiếu

#### FR-023 – Quản lý lịch chiếu

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí thêm mới, sửa đổi, xóa và xem danh sách lịch chiếu phim. |
| Actor | Người quản lí |
| Inputs | Ngày giờ chiếu, phòng chiếu, thông tin liên quan khác |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.d, B.III UC010; DT II.2.e; UCD |
| Verification Status | VERIFIED. Khác biệt giữa "lịch chiếu" và "suất chiếu" chưa được định nghĩa (ISS-07). |

#### FR-024 – Quản lý suất chiếu

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí thêm mới, sửa đổi, xóa và xem danh sách suất chiếu. |
| Actor | Người quản lí |
| Inputs | Giờ bắt đầu, giờ kết thúc, phòng chiếu, thông tin liên quan khác |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.e, B.III UC011; DT II.2.f; UCD; MU `wf06` (Edit Screening) |
| Verification Status | VERIFIED. Nguồn chỉ mô tả chi tiết thao tác Thêm và Danh sách (ISS-14). |

### Nhóm G – Quản lý người dùng và phân quyền

#### FR-025 – Quản lý người dùng

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí xem danh sách người dùng, xem chi tiết, sửa thông tin và xóa người dùng khi cần. |
| Actor | Người quản lí |
| Outputs | Danh sách gồm Name, Gender, Shift, Role (MU `wf07`) |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.f, B.III UC012; DT II.2.g; UCD; MU `wf07` |
| Verification Status | VERIFIED. "Người dùng" là nhân viên hay khách hàng: TBD (ISS-12). |

#### FR-030 – Phân quyền người dùng

| Thuộc tính | Nội dung |
|---|---|
| Description | Các quản lý cấp cao có thể phân quyền người dùng và cập nhật chức năng. Sau khi đăng nhập, người dùng chỉ thực hiện các chức năng được phân quyền. |
| Actor | Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I, A.I.1.a |
| Verification Status | VERIFIED. Chưa có UC tương ứng (ISS-11). |

#### FR-035 – Quản lý nhân viên

| Thuộc tính | Nội dung |
|---|---|
| Description | SRS nêu "quản lý nhân viên" là một chức năng chính, và trong phạm vi hệ thống, "Quản lý rạp phim" có chức năng quản lý nhân viên. |
| Actor | Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I, A.II |
| Verification Status | TBD – chưa rõ có trùng với UC-012 hay không (ISS-12) |

### Nhóm H – Báo cáo và thống kê

#### FR-026 – Báo cáo doanh thu

| Thuộc tính | Nội dung |
|---|---|
| Description | Người quản lí xem thống kê doanh thu từ bán vé, sản phẩm bổ sung (bắp rang, nước uống) và các dịch vụ khác, theo ngày, tuần, tháng hoặc theo từng rạp. |
| Actor | Người quản lí |
| Outputs | Báo cáo doanh thu; MU `wf08` có Tổng doanh thu, Sản phẩm đã bán, Tổng số vé, biểu đồ doanh thu theo thời gian, tỷ lệ % doanh số theo phim |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.g, B.III UC013; UCD; MU `wf08` |
| Verification Status | VERIFIED |

#### FR-027 – Lọc báo cáo doanh thu

| Thuộc tính | Nội dung |
|---|---|
| Description | Lọc báo cáo doanh thu theo phim, phòng chiếu hoặc chương trình khuyến mãi. |
| Actor | Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.g |
| Verification Status | VERIFIED |

#### FR-028 – Xuất báo cáo doanh thu

| Thuộc tính | Nội dung |
|---|---|
| Description | Xuất báo cáo doanh thu ra file Excel hoặc PDF để lưu trữ hoặc trình bày. |
| Actor | Người quản lí |
| Outputs | File Excel hoặc PDF |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I.2.g, B.III UC013 |
| Verification Status | VERIFIED |

#### FR-029 – Màn hình tổng quan (dashboard)

| Thuộc tính | Nội dung |
|---|---|
| Description | Xem tổng quan hoạt động kinh doanh: doanh thu theo ngày, khách hàng mới đăng ký hằng ngày, tổng số vé bán trong ngày, doanh thu theo tháng, theo phim, theo rạp chiếu phim. |
| Actor | DT ghi "Nhân viên quản lí rạp" / "admin" → portfolio quy về Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | DT II.2.a; MU `wf08` |
| Verification Status | VERIFIED (nội dung). Gắn với UC-013 là INFERRED. |

### Nhóm I – Yêu cầu có mô tả nhưng chưa có use case

#### FR-031 – Theo dõi và quản lý đơn đặt vé

| Thuộc tính | Nội dung |
|---|---|
| Description | Hệ thống hỗ trợ nhân viên theo dõi và quản lý các đơn đặt vé. Admin quản lý các đơn hàng để hệ thống vận hành ổn định. |
| Actor | Nhân viên bán vé, Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | SRS A.I; DT II |
| Verification Status | VERIFIED (nội dung); chưa có UC (ISS-11) |

#### FR-032 – Quản lý khuyến mãi và giá vé

| Thuộc tính | Nội dung |
|---|---|
| Description | Admin quản lý các chương trình khuyến mãi, kiểm soát thông tin giá vé và khuyến mãi. |
| Actor | Người quản lí |
| Priority | Chưa có căn cứ |
| Source Reference | DT II |
| Verification Status | TBD – chỉ có trong DT. SRS chỉ nhắc "chương trình khuyến mãi" như một tiêu chí lọc báo cáo (FR-027). |

#### FR-033 – Kiểm tra tính hợp lệ của vé tại rạp

| Thuộc tính | Nội dung |
|---|---|
| Description | Nhân viên kiểm tra tính hợp lệ của vé khi khách hàng đến rạp. |
| Actor | Nhân viên |
| Priority | Chưa có căn cứ |
| Source Reference | DT II |
| Verification Status | TBD – chỉ có trong DT, chưa có UC |

#### FR-034 – Đổi suất chiếu / hoàn vé

| Thuộc tính | Nội dung |
|---|---|
| Description | Nhân viên xử lý các vấn đề phát sinh như đổi suất chiếu hoặc hoàn vé. |
| Actor | Nhân viên |
| Priority | Chưa có căn cứ |
| Source Reference | DT II |
| Verification Status | OUT OF SCOPE – **Đã xác nhận** bởi chủ portfolio ngày 23/11/2026: không hoàn vé, không đổi suất chiếu, không hủy vé (BR-003, BR-004; ISS-02). |

---

## 3. Đề xuất bổ sung – Độ ưu tiên (PROPOSED)

> ⚠️ **Đề xuất bổ sung.** Bảng này **không có trong tài liệu học phần**. Đây là phân loại MoSCoW do portfolio đề xuất, dựa trên vai trò của chức năng trong quy trình bán vé cốt lõi. Cần xác nhận trước khi sử dụng.

| Mức | Requirement ID | Lý do đề xuất |
|---|---|---|
| Must have | FR-001, FR-006, FR-007, FR-008, FR-010, FR-012, FR-013, FR-021, FR-022, FR-024 | Bắt buộc để bán được một vé đúng suất chiếu, đúng ghế |
| Should have | FR-003, FR-004, FR-005, FR-011, FR-014, FR-015, FR-016, FR-017, FR-018, FR-019, FR-023, FR-025, FR-026, FR-030 | Hỗ trợ vận hành và quản trị hằng ngày |
| Could have | FR-009, FR-027, FR-028, FR-029, FR-031 | Giá trị gia tăng, phân tích |
| Ngoài phạm vi (đã xác nhận) | FR-002, FR-034 | Hệ thống bán vé tại quầy; không hoàn/đổi/hủy vé |
| Cần quyết định phạm vi | FR-020, FR-032, FR-033, FR-035 | Đang mâu thuẫn hoặc chưa có use case – xem [Assumptions and Open Questions](../08_Review/Assumptions_and_Open_Questions.md) |
