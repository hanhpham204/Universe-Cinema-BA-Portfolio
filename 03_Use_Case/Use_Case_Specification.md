# Use Case Specification – Đặc tả Use Case

> **Cách đọc tài liệu này**
>
> - Phần **"Theo tài liệu học phần"** chỉ chứa nội dung có trong [SRS]/[DT]/[UCD]/[MU], kèm nguồn. Ô nào nguồn không có thì ghi **"Chưa có dữ liệu nguồn"**.
> - Phần **"Luồng suy ra từ mockup (INFERRED)"** sắp xếp các bước dựa trên màn hình mockup gốc. Đây là suy luận, chưa được nhóm xác nhận.
> - Phần **"⚠️ Đề xuất bổ sung (PROPOSED)"** là nội dung viết thêm cho portfolio, **không phải sản phẩm của học phần**.
>
> **Hiện trạng nguồn:** Trong [SRS] mục C, chỉ **UC001** có đặc tả đầy đủ luồng sự kiện. **UC002** có mục đích, mô tả, tác nhân và điều kiện nhưng chưa có luồng. Mục C cho **UC003–UC013** là bản sao nội dung của UC002 (mô tả tìm kiếm phim), nên không được dùng làm căn cứ (ISS-09). Với các UC này, portfolio chỉ dùng mô tả ngắn ở SRS B.III và mô tả chức năng ở SRS A.I / DT II.

---

## UC-001 – Đăng nhập hệ thống

### Theo tài liệu học phần (VERIFIED – SRS C.I)

| Mục | Nội dung |
|---|---|
| Mã gốc | UC001 |
| Actor | Nhân viên và Người quản lý |
| Mục tiêu | Đăng nhập vào phần mềm |
| Mô tả | Use case thực hiện chức năng đăng nhập vào phần mềm |
| Tiền điều kiện | Nhân viên hoặc người quản lý đã có tài khoản |
| Hậu điều kiện | Nhân viên hoặc người quản lý đăng nhập thành công vào phần mềm |
| Business Rules | BR-010, BR-011 |
| Requirement | FR-001 |
| Mockup | [`wf01_login.png`](../assets/wireframes/wf01_login.png) |

**Luồng chính (Basic Flow)**

| Bước | Actor | Hệ thống |
|---|---|---|
| 1 | | Hiển thị giao diện đăng nhập |
| 2 | Nhập tài khoản, mật khẩu | |
| 3 | Chọn nút đăng nhập | |
| 4 | | Chuyển sang giao diện trang chủ |
| 5 | | Kết thúc use case |

**Luồng thay thế (Alternative Flow)**

| Bước | Actor | Hệ thống |
|---|---|---|
| 4.1 | | Thông báo tài khoản hoặc mật khẩu không đúng |
| 4.2 | | Quay lại bước 2 |

**Luồng ngoại lệ (Exception Flow):** Chưa có dữ liệu nguồn.

### ⚠️ Đề xuất bổ sung (PROPOSED)

| Mã | Luồng đề xuất |
|---|---|
| E1 | Người dùng để trống tên đăng nhập hoặc mật khẩu → hệ thống yêu cầu nhập đủ thông tin, quay lại bước 2. |
| E2 | Không kết nối được tới hệ thống quản lý dữ liệu → hệ thống thông báo lỗi, use case kết thúc. |
| A1 | Sau bước 4, hệ thống hiển thị menu theo vai trò (Nhân viên bán vé / Người quản lí), theo BR-010. |

---

## UC-002 – Tìm kiếm các bộ phim

### Theo tài liệu học phần (VERIFIED – SRS C.II, B.III; UCD)

| Mục | Nội dung |
|---|---|
| Mã gốc | UC002 |
| Actor | SRS C.II: Nhân viên và Người quản lý · UCD: Nhân viên (TBD – ISS-15) |
| Mục tiêu | Cho phép người dùng tìm kiếm và tìm thấy các bộ phim đáp ứng tiêu chí tìm kiếm của họ |
| Mô tả | Người dùng nhập một hoặc nhiều từ khóa liên quan đến phim (tên phim, thể loại, diễn viên, đạo diễn, năm sản xuất…), hệ thống trả về danh sách phim phù hợp |
| Tiền điều kiện | Người dùng đã đăng nhập vào hệ thống |
| Hậu điều kiện | Hệ thống hiển thị danh sách phim tìm thấy (poster, tên phim, năm sản xuất, thể loại, diễn viên chính). Người dùng có thể xem chi tiết từng phim, "đánh giá, hoặc thêm vào danh sách yêu thích" (*hai chức năng sau không xuất hiện ở bất kỳ mục nào khác – ISS-10*) |
| Biến thể trên UCD | Tìm theo tên phim; Tìm theo thời gian chiếu; Tìm theo thể loại |
| Business Rules | BR-009 |
| Requirement | FR-003, FR-004, FR-005 |
| Luồng chính | Chưa có dữ liệu nguồn (ô trong SRS còn để chữ mẫu) |
| Luồng thay thế | Chưa có dữ liệu nguồn |
| Luồng ngoại lệ | Chưa có dữ liệu nguồn |

### ⚠️ Đề xuất bổ sung (PROPOSED)

**Luồng chính đề xuất:** (1) Hệ thống hiển thị ô tìm kiếm và bộ lọc → (2) Nhân viên nhập từ khóa và/hoặc chọn tiêu chí (tên phim / thể loại / thời gian chiếu) → (3) Hệ thống tìm và hiển thị danh sách phim phù hợp → (4) Nhân viên chọn một phim → (5) Hệ thống hiển thị thông tin chi tiết phim (FR-005).
**Luồng thay thế đề xuất:** 3a. Không có phim phù hợp → hệ thống thông báo "Không tìm thấy phim", giữ nguyên tiêu chí để nhân viên sửa.

---

## UC-003 – Xem lịch chiếu

### Theo tài liệu học phần (VERIFIED – SRS B.III, A.I.1.c; DT II.1.d)

| Mục | Nội dung |
|---|---|
| Mã gốc | UC003 |
| Actor | Nhân viên bán vé |
| Mục tiêu | Xem lịch chiếu phim cho từng rạp và từng ngày cụ thể; dùng lịch chiếu để tư vấn khách hàng chọn suất chiếu phù hợp |
| Mô tả | Hệ thống hiển thị chi tiết thời gian chiếu, phòng chiếu và số lượng ghế còn trống cho từng suất chiếu. DT bổ sung cách xem theo phim (chọn một phim để xem lịch chiếu tại các rạp). |
| Tiền điều kiện | Đã đăng nhập (UCD – «include» Đăng nhập; BR-009) |
| Hậu điều kiện | Chưa có dữ liệu nguồn |
| Business Rules | BR-008, BR-009 |
| Requirement | FR-006, FR-007 |
| Luồng chính / thay thế / ngoại lệ | Chưa có dữ liệu nguồn |

### ⚠️ Đề xuất bổ sung (PROPOSED)

**Luồng chính đề xuất:** (1) Nhân viên chọn rạp và ngày → (2) Hệ thống hiển thị danh sách suất chiếu gồm phim, giờ chiếu, phòng chiếu, số ghế còn trống → (3) Nhân viên chọn một suất chiếu để chuyển sang UC-004 (tùy chọn).
**Luồng thay thế đề xuất:** 2a. Không có suất chiếu trong ngày đã chọn → hệ thống thông báo.

---

## UC-004 – Bán vé xem phim

### Theo tài liệu học phần (VERIFIED – SRS B.III, A.I, A.I.1.d; DT II.1.e)

| Mục | Nội dung |
|---|---|
| Mã gốc | UC004 |
| Actor | Nhân viên bán vé (UCD). Mockup hiển thị người dùng "Admin" ở màn hình Booking (ISS-15). |
| Mục tiêu | Bán vé xem phim cho khách hàng thông qua hệ thống |
| Mô tả | Khi khách hàng chọn phim và suất chiếu, nhân viên thực hiện đặt vé, chọn ghế ngồi / số lượng vé và thanh toán. Hệ thống cung cấp giao diện bán vé trực quan và cập nhật số ghế còn trống. Sau khi thanh toán thành công, nhân viên có thể in vé hoặc gửi vé điện tử. |
| Tiền điều kiện | Đã đăng nhập (UCD; BR-009) |
| Hậu điều kiện | Số ghế còn trống được cập nhật (SRS A.I.1.d). Vé đã thanh toán không thể hoàn hoặc hủy (SRS A.I). |
| Business Rules | BR-001, BR-002, BR-003, BR-004, BR-005, BR-008 |
| Requirement | FR-008, FR-009, FR-010, FR-011, FR-012 |
| Luồng chính / thay thế / ngoại lệ dạng bảng | Chưa có dữ liệu nguồn |

> 📄 Bản đặc tả đầy đủ (đề xuất bổ sung) của use case này: [UC-004 Detailed Specification](UC-004_Sell_Ticket_Detailed_Specification.md).

### Luồng suy ra từ mockup (INFERRED – MU `wf02`, `wf03`, `wf04`)

Mockup bán vé có thanh tiến trình 3 bước: **1. Chọn Phim → 2. Chọn ghế → 3. Bắp/Nước**.

| Bước | Actor | Hệ thống | Căn cứ |
|---|---|---|---|
| 1 | Chọn chức năng "Booking Movies" | Hiển thị bước 1: ô ngày (Ngày/Tháng/Năm), ô tìm kiếm, danh sách phim (Movie Title, Genre, Duration, Showing Date) | `wf02` |
| 2 | Chọn ngày và phim | Hiển thị thông tin phim (đạo diễn, diễn viên, thể loại, khởi chiếu, thời lượng, ngôn ngữ, phân loại độ tuổi) | `wf02` |
| 3 | Nhấn "Next" | Hiển thị bước 2: sơ đồ ghế theo màn hình, lối vào, trạng thái ghế "Chưa chọn"/"Đã chọn" | `wf03` |
| 4 | Chọn ghế | Hiển thị "Ghế đang chọn" và "Giá" | `wf03` |
| 5 | Nhấn "Next" | Hiển thị bước 3: danh sách loại/combo bắp nước; tóm tắt tên phim, giá, combo, tổng tiền | `wf04` |
| 6 | Chọn combo (tùy chọn), chọn hình thức thanh toán | | `wf04` |
| 7 | Nhấn "In hóa đơn" | | `wf04`; SRS A.I.1.d |
| 8 | | Cập nhật số ghế còn trống | SRS A.I.1.d (BR-008) |

> Mockup **không thể hiện rõ bước chọn suất chiếu**: bước 1 chỉ có chọn ngày và phim. Đây là điểm cần xác minh (ISS-22).

### ⚠️ Đề xuất bổ sung (PROPOSED)

| Mã | Luồng đề xuất |
|---|---|
| A1 | Bước 4: ghế đã bán hiển thị ở trạng thái không chọn được (BR-002, BR-P03). |
| A2 | Bước 6: khách không mua bắp nước → bỏ qua, tổng tiền chỉ gồm vé. |
| E1 | Bước 4: suất chiếu đã hết ghế → hệ thống thông báo, quay lại bước 1 (BR-002). |
| E2 | Bước 7: thanh toán thất bại → hệ thống thông báo, ghế không bị đánh dấu đã bán, quay lại bước 6. |
| E3 | Ghế vừa được bán ở giao dịch khác trong lúc chọn → hệ thống thông báo, yêu cầu chọn ghế khác (NFR-P04). |

---

## UC-005 – Thêm phim

### Theo tài liệu học phần (VERIFIED – SRS B.III, A.I.2.a; DT II.2.b)

| Mục | Nội dung |
|---|---|
| Mã gốc | UC005 |
| Actor | Người quản lí |
| Mục tiêu | Thêm phim mới vào hệ thống |
| Mô tả | Cung cấp thông tin tên phim, thể loại, đạo diễn, diễn viên, ngày phát hành, thời lượng, mô tả; có thể tải lên hình ảnh và trailer |
| Tiền điều kiện | Đã đăng nhập (UCD; BR-009) |
| Hậu điều kiện | Chưa có dữ liệu nguồn |
| Business Rules | BR-009, BR-012 |
| Requirement | FR-013, FR-016 |
| Mockup | [`wf05_movie_management.png`](../assets/wireframes/wf05_movie_management.png) – trường Movie Title, Genre, Duration, Date; nút Import, Insert, Update, Delete, Clear |
| Luồng chính / thay thế / ngoại lệ | Chưa có dữ liệu nguồn |

### ⚠️ Đề xuất bổ sung (PROPOSED)

**Luồng chính đề xuất:** (1) Người quản lí mở màn hình quản lý phim → (2) Nhập thông tin phim, nhấn "Import" để tải ảnh → (3) Nhấn "Insert" → (4) Hệ thống kiểm tra dữ liệu bắt buộc, lưu phim và cập nhật danh sách.
**Luồng ngoại lệ đề xuất:** 4a. Thiếu trường bắt buộc hoặc thời lượng không hợp lệ → hệ thống báo lỗi tại trường tương ứng. 4b. Trùng phim đã có (`[TBD – tiêu chí trùng]`) → hệ thống cảnh báo.

---

## UC-006 – Sửa phim

| Mục | Nội dung |
|---|---|
| Mã gốc | UC006 |
| Actor | Người quản lí |
| Mục tiêu / Mô tả | Sửa thông tin của phim đã có khi có thay đổi hoặc bổ sung (VERIFIED – SRS B.III, A.I.2.a; DT II.2.b) |
| Tiền điều kiện | Đã đăng nhập (BR-009); phim đã tồn tại (INFERRED) |
| Hậu điều kiện | Chưa có dữ liệu nguồn |
| Business Rules | BR-009, BR-012 |
| Requirement | FR-014 |
| Luồng chính / thay thế / ngoại lệ | Chưa có dữ liệu nguồn |
| ⚠️ Đề xuất bổ sung | Chọn phim trong danh sách → hệ thống điền thông tin vào form → sửa → nhấn "Update" → hệ thống kiểm tra và lưu. |

## UC-007 – Xóa phim

| Mục | Nội dung |
|---|---|
| Mã gốc | UC007 |
| Actor | Người quản lí |
| Mục tiêu / Mô tả | Xóa phim khỏi hệ thống (VERIFIED – SRS B.III, A.I.2.a; DT II.2.b) |
| Tiền điều kiện | Đã đăng nhập (BR-009) |
| Hậu điều kiện | Chưa có dữ liệu nguồn |
| Business Rules | BR-009, BR-012 |
| Requirement | FR-015 |
| Luồng chính / thay thế / ngoại lệ | Chưa có dữ liệu nguồn |
| ⚠️ Đề xuất bổ sung | Chọn phim → nhấn "Delete" → hệ thống yêu cầu xác nhận → xóa. Ngoại lệ: phim đã có suất chiếu/vé bán → không cho xóa (BR-P02). |

## UC-008 – Quản lý rạp chiếu phim

| Mục | Nội dung |
|---|---|
| Mã gốc | UC008 |
| Actor | Người quản lí |
| Mục tiêu / Mô tả | Thêm, sửa và xem danh sách rạp chiếu phim (tên rạp, địa chỉ, số điện thoại liên hệ). SRS B.III có thêm "xóa" – **mâu thuẫn**, xem ISS-03. (VERIFIED – SRS B.III, A.I.2.b; DT II.2.c) |
| Tiền điều kiện | Đã đăng nhập (BR-009) |
| Hậu điều kiện | Chưa có dữ liệu nguồn |
| Business Rules | BR-009, BR-012 |
| Requirement | FR-017, FR-018, FR-019, FR-020 |
| Luồng chính / thay thế / ngoại lệ | Chưa có dữ liệu nguồn |
| ⚠️ Đề xuất bổ sung | Tách thành các luồng con Thêm / Sửa / Xem danh sách; quyết định có giữ "Xóa" hay không sau khi xác nhận ISS-03. |

## UC-009 – Quản lý phòng chiếu

| Mục | Nội dung |
|---|---|
| Mã gốc | UC009 |
| Actor | Người quản lí |
| Mục tiêu / Mô tả | Thêm, sửa, xóa, xem danh sách phòng chiếu (tên phòng, số lượng ghế); quản lý ghế ngồi trong từng phòng để sơ đồ ghế luôn chính xác (VERIFIED – SRS B.III, A.I.2.c; DT II.2.d) |
| Tiền điều kiện | Đã đăng nhập (BR-009) |
| Hậu điều kiện | Chưa có dữ liệu nguồn |
| Business Rules | BR-006, BR-009, BR-012 |
| Requirement | FR-021, FR-022 |
| Luồng chính / thay thế / ngoại lệ | Chưa có dữ liệu nguồn |
| ⚠️ Đề xuất bổ sung | Khi thêm phòng: nhập tên phòng, số hàng/số ghế mỗi hàng → hệ thống sinh sơ đồ ghế (như mẫu A1–F15 ở `wf03`) → người quản lí chỉnh từng ghế. Ngoại lệ: không xóa phòng đã có suất chiếu (BR-P02). |

## UC-010 – Quản lý lịch chiếu

| Mục | Nội dung |
|---|---|
| Mã gốc | UC010 |
| Actor | Người quản lí |
| Mục tiêu / Mô tả | Thêm, sửa, xóa, xem danh sách lịch chiếu (ngày giờ chiếu, phòng chiếu) (VERIFIED – SRS B.III, A.I.2.d; DT II.2.e) |
| Tiền điều kiện | Đã đăng nhập (BR-009) |
| Hậu điều kiện | Chưa có dữ liệu nguồn |
| Business Rules | BR-007, BR-009, BR-012 |
| Requirement | FR-023 |
| Luồng chính / thay thế / ngoại lệ | Chưa có dữ liệu nguồn |
| Ghi chú | Chưa phân biệt rõ với UC-011 (ISS-07) |
| ⚠️ Đề xuất bổ sung | Định nghĩa "lịch chiếu" là kế hoạch chiếu của một phim trong một khoảng ngày tại một rạp, và "suất chiếu" là một lần chiếu cụ thể (phim + phòng + giờ bắt đầu/kết thúc). Cần xác nhận. |

## UC-011 – Quản lý suất chiếu

| Mục | Nội dung |
|---|---|
| Mã gốc | UC011 |
| Actor | Người quản lí |
| Mục tiêu / Mô tả | Thêm, sửa, xóa, xem danh sách suất chiếu (giờ bắt đầu, giờ kết thúc, phòng chiếu) (VERIFIED – SRS B.III, A.I.2.e; DT II.2.f) |
| Tiền điều kiện | Đã đăng nhập (BR-009) |
| Hậu điều kiện | Chưa có dữ liệu nguồn |
| Business Rules | BR-005, BR-006, BR-007, BR-009 |
| Requirement | FR-024 |
| Mockup | [`wf06_edit_screening.png`](../assets/wireframes/wf06_edit_screening.png) – chọn phim, trường "Current", nút Update, Clear |
| Luồng chính / thay thế / ngoại lệ | Chưa có dữ liệu nguồn |
| ⚠️ Đề xuất bổ sung | Chọn phim → chọn phòng chiếu → nhập giờ bắt đầu (giờ kết thúc tính theo thời lượng phim) → hệ thống kiểm tra trùng lịch phòng (BR-P01) → lưu. Ngoại lệ: trùng lịch → thông báo, yêu cầu chọn giờ/phòng khác. |

## UC-012 – Quản lý người dùng

| Mục | Nội dung |
|---|---|
| Mã gốc | UC012 |
| Actor | Người quản lí |
| Mục tiêu / Mô tả | Xem danh sách người dùng, xem chi tiết, sửa thông tin và xóa người dùng khi cần (VERIFIED – SRS B.III, A.I.2.f; DT II.2.g) |
| Tiền điều kiện | Đã đăng nhập (BR-009) |
| Hậu điều kiện | Chưa có dữ liệu nguồn |
| Business Rules | BR-009, BR-010, BR-012 |
| Requirement | FR-025, FR-030 (INFERRED), FR-035 (TBD) |
| Mockup | [`wf07_user_management.png`](../assets/wireframes/wf07_user_management.png) – menu "Customers", cột Name, Gender, Shift, Role |
| Luồng chính / thay thế / ngoại lệ | Chưa có dữ liệu nguồn |
| Ghi chú | Chưa rõ "người dùng" là nhân viên hay khách hàng (ISS-12) |

## UC-013 – Thống kê doanh thu

| Mục | Nội dung |
|---|---|
| Mã gốc | UC013 |
| Actor | Người quản lí |
| Mục tiêu / Mô tả | Xem báo cáo doanh thu từ bán vé, sản phẩm bổ sung và dịch vụ khác theo ngày/tuần/tháng/rạp; lọc theo phim, phòng chiếu, khuyến mãi; xuất Excel/PDF (VERIFIED – SRS B.III, A.I.2.g) |
| Tiền điều kiện | Đã đăng nhập (BR-009) |
| Hậu điều kiện | Chưa có dữ liệu nguồn |
| Business Rules | BR-009, BR-012 |
| Requirement | FR-026, FR-027, FR-028, FR-029 (INFERRED) |
| Mockup | [`wf08_dashboard_revenue.png`](../assets/wireframes/wf08_dashboard_revenue.png) – Tổng doanh thu, Sản phẩm đã bán, Tổng số vé, doanh thu theo thời gian, tỷ lệ % doanh số theo phim (**số liệu và biểu đồ trong mockup là dữ liệu minh họa**, ISS-20) |
| Luồng chính / thay thế / ngoại lệ | Chưa có dữ liệu nguồn |
| ⚠️ Đề xuất bổ sung | Chọn kỳ báo cáo (ngày/tuần/tháng) và bộ lọc → hệ thống tổng hợp và hiển thị → (tùy chọn) chọn "Xuất" → chọn Excel/PDF → hệ thống tạo file. Ngoại lệ: không có dữ liệu trong kỳ → hiển thị trạng thái rỗng. |
