# Source Traceability – Truy vết nguồn tài liệu

> Tài liệu này cho biết **mỗi yêu cầu, quy tắc và use case trong portfolio được lấy từ đâu** trong tài liệu gốc của học phần, và mức độ xác minh của từng mục.

## 1. Tài liệu nguồn

| Mã nguồn | Tên file gốc | Tiêu đề trong tài liệu | Thời điểm | Ghi chú |
|---|---|---|---|---|
| **[SRS]** | `Nhom07_3_ApplicationDevelopment_SRS.docx` | Hệ thống quản lí rạp chiếu phim – Đặc tả yêu cầu ứng dụng – V1.0 | Tháng 08/2024 | Tài liệu SRS theo mẫu của học phần. Mục C (đặc tả chi tiết use case) mới hoàn thiện UC001. |
| **[DT]** | `Nhom07_DacTa.docx` | Phát triển ứng dụng – Đề tài: Hệ thống quản lí rạp chiếu phim | 19/08/2024 | Tài liệu đặc tả/giới thiệu đề tài. Mục "V. Sơ đồ lớp" chỉ có tiêu đề, không có nội dung. |
| **[UCD]** | Ảnh nhúng trong [SRS] mục B.I và [DT] mục IV | Sơ đồ Use Case | 08/2024 | Hai ảnh **giống hệt nhau** (đã so sánh từng byte). Lưu tại [`assets/diagrams/use_case_diagram_original.png`](../assets/diagrams/use_case_diagram_original.png). |
| **[MU]** | 8 ảnh nhúng trong [SRS] mục A.I.1–A.I.2 | Mockup giao diện | 08/2024 | Lưu tại [`assets/wireframes/`](../assets/wireframes/) (đã ẩn poster phim và tên thành viên). Xem [06_UI_Wireframes](../06_UI_Wireframes/README.md). |

### Giới hạn khi truy vết

- Hai file gốc là `.docx`, **không có số trang cố định**. Số trang ghi trong bảng (`tr.`) là số trang của bản PDF được chuyển đổi bằng LibreOffice (SRS: 28 trang, DT: 5 trang). Số trang này có thể lệch so với khi mở bằng Microsoft Word. Mục lục trong [SRS] cũng không khớp với số trang thực tế, nên **tên mục (Mục) là căn cứ tham chiếu chính**.
- Ở chân trang [SRS] ghi "Trang N". Giá trị N thường nhỏ hơn số trang PDF 1 đơn vị, vì trang bìa không được đánh số.
- Mục C của [SRS], từ UC003 đến UC013, là bản sao nội dung của UC002 (mục đích, mô tả, điều kiện đều nói về tìm kiếm phim). Vì vậy các mục này **không được dùng làm căn cứ** cho nội dung của từng use case (xem ISS-09 trong [Assumptions and Open Questions](../08_Review/Assumptions_and_Open_Questions.md)).
- Không có tài liệu nào về công nghệ, cơ sở dữ liệu, test case hay kết quả triển khai.

## 2. Quy ước trạng thái xác minh

| Trạng thái | Ý nghĩa |
|---|---|
| `VERIFIED` | Có căn cứ trực tiếp trong tài liệu gốc. |
| `INFERRED` | Suy luận hợp lý từ tài liệu gốc nhưng chưa được xác nhận. |
| `PROPOSED` | Đề xuất bổ sung cho portfolio, không phải sản phẩm của học phần. |
| `TBD` | Cần chủ sở hữu portfolio xác nhận (thường do tài liệu mâu thuẫn hoặc thiếu). |
| `OUT OF SCOPE` | Chủ portfolio đã xác nhận nằm ngoài phạm vi hệ thống. |

> **Ghi chú "Đã xác nhận":** Ngày 23/11/2026, chủ portfolio xác nhận ba điểm: (1) hệ thống là **phần mềm bán vé tại quầy** cho nhân viên; (2) **không hoàn vé, không đổi suất, không hủy vé**; (3) nhóm và giảng viên đồng ý công khai tài liệu. Xác nhận này giải quyết ISS-01 và ISS-02. Đây là xác nhận của chủ sở hữu, **không phải nội dung mới trong tài liệu gốc**.

## 3. Bảng truy vết – Functional Requirements

| Requirement ID | Nội dung | Nguồn | Trang/Mục | Trạng thái xác minh |
|---|---|---|---|---|
| FR-001 | Đăng nhập hệ thống bằng tên đăng nhập và mật khẩu; xác thực quyền truy cập | [SRS]; [DT]; [UCD]; [MU] | SRS mục A.I.1.a (tr.3), B.III UC001 (tr.16), C.I UC001 (tr.18); DT mục II.1.a (tr.2–3); MU `wf01` | VERIFIED |
| FR-002 | Đăng ký tài khoản mới (email, mật khẩu, tên người dùng) | [DT] | DT mục II.1.a (tr.2–3) | OUT OF SCOPE – chỉ có trong DT; hệ thống bán vé tại quầy (ISS-01, đã xác nhận) |
| FR-003 | Tìm kiếm phim theo tiêu chí | [SRS]; [DT]; [UCD] | SRS mục A.I.1.b (tr.4), B.III UC002 (tr.16), C.II UC002 (tr.19); DT mục II.1.b (tr.3) | VERIFIED (danh sách tiêu chí: TBD – ISS-04) |
| FR-004 | Lọc phim đang chiếu / sắp chiếu | [SRS]; [DT] | SRS mục A.I.1.b (tr.4); DT mục II.1.b (tr.3) | VERIFIED |
| FR-005 | Xem thông tin chi tiết phim | [DT]; [SRS] | DT mục II.1.c (tr.3); SRS mục A.I.1.b (tr.4), C.II điều kiện sau (tr.19–20); MU `wf02` | VERIFIED (chưa có UC riêng – ISS-11) |
| FR-006 | Xem lịch chiếu theo rạp và theo ngày | [SRS]; [DT]; [UCD] | SRS mục A.I.1.c (tr.5), B.III UC003 (tr.16); DT mục II.1.d (tr.3) | VERIFIED |
| FR-007 | Hiển thị thời gian chiếu, phòng chiếu, số ghế còn trống của từng suất chiếu | [SRS] | SRS mục A.I.1.c (tr.5), B.III UC003 (tr.16) | VERIFIED |
| FR-008 | Bán vé: chọn phim, suất chiếu và ghế ngồi | [SRS]; [DT]; [UCD]; [MU] | SRS mục A.I (tr.3), A.I.1.d (tr.6), B.III UC004 (tr.16); DT mục II.1.e (tr.3); MU `wf02`, `wf03` | VERIFIED |
| FR-009 | Chọn dịch vụ đi kèm (bắp rang, nước, snack) khi mua vé | [DT]; [MU]; [SRS] | DT mục II.1.e (tr.3); MU `wf04`; SRS mục A.I.2.g (tr.13) – doanh thu từ sản phẩm bổ sung | INFERRED – không có trong mô tả UC004 của SRS |
| FR-010 | Thanh toán giao dịch | [SRS]; [DT]; [MU] | SRS mục A.I (tr.3), A.II "Hệ thống thanh toán" (tr.14); DT mục II.1.e (tr.3); MU `wf04` | VERIFIED (phương thức thanh toán: TBD – ISS-17) |
| FR-011 | In vé hoặc gửi vé điện tử sau khi thanh toán thành công | [SRS]; [MU] | SRS mục A.I.1.d (tr.6); MU `wf04` ("In hóa đơn") | VERIFIED |
| FR-012 | Kiểm tra ghế trống và tự động cập nhật số ghế còn trống sau mỗi giao dịch | [SRS] | SRS mục A.I (tr.3), A.I.1.d (tr.6), B.III UC004 (tr.16) | VERIFIED |
| FR-013 | Thêm phim mới | [SRS]; [DT]; [MU] | SRS mục A.I.2.a (tr.7–8), B.III UC005 (tr.16); DT mục II.2.b (tr.4); MU `wf05` | VERIFIED |
| FR-014 | Sửa thông tin phim | [SRS]; [DT]; [MU] | SRS mục A.I.2.a (tr.8), B.III UC006 (tr.16); DT mục II.2.b (tr.4); MU `wf05` | VERIFIED |
| FR-015 | Xóa phim | [SRS]; [DT]; [MU] | SRS mục A.I.2.a (tr.8), B.III UC007 (tr.16); DT mục II.2.b (tr.4); MU `wf05` | VERIFIED |
| FR-016 | Xem danh sách phim | [SRS]; [DT]; [MU] | SRS mục A.I.2.a (tr.8); DT mục II.2.b (tr.4); MU `wf05` | VERIFIED |
| FR-017 | Thêm rạp chiếu phim (tên, địa chỉ, số điện thoại liên hệ) | [SRS]; [DT] | SRS mục A.I.2.b (tr.8), B.III UC008 (tr.16–17); DT mục II.2.c (tr.4) | VERIFIED |
| FR-018 | Sửa thông tin rạp chiếu phim | [SRS]; [DT] | SRS mục A.I.2.b (tr.8); DT mục II.2.c (tr.4) | VERIFIED |
| FR-019 | Xem danh sách rạp chiếu phim | [SRS]; [DT] | SRS mục A.I.2.b (tr.8); DT mục II.2.c (tr.4) | VERIFIED |
| FR-020 | Xóa rạp chiếu phim | [SRS] | SRS mục B.III UC008 (tr.16–17) | TBD – mâu thuẫn với SRS mục A.I.2.b và DT mục II.2.c (ISS-03) |
| FR-021 | Quản lý phòng chiếu (thêm, sửa, xóa, xem danh sách) | [SRS]; [DT]; [UCD] | SRS mục A.I.2.c (tr.9), B.III UC009 (tr.17); DT mục II.2.d (tr.4) | VERIFIED |
| FR-022 | Quản lý ghế ngồi trong từng phòng chiếu (thêm, sửa, xóa) | [SRS]; [DT] | SRS mục A.I.2.c (tr.9), B.III UC009 (tr.17); DT mục II.2.d (tr.4) | VERIFIED |
| FR-023 | Quản lý lịch chiếu (thêm, sửa, xóa, xem danh sách) | [SRS]; [DT]; [UCD] | SRS mục A.I.2.d (tr.10), B.III UC010 (tr.17); DT mục II.2.e (tr.4) | VERIFIED (khác biệt với suất chiếu: TBD – ISS-07) |
| FR-024 | Quản lý suất chiếu (thêm, sửa, xóa, xem danh sách) | [SRS]; [DT]; [UCD]; [MU] | SRS mục A.I.2.e (tr.11), B.III UC011 (tr.17); DT mục II.2.f (tr.5); MU `wf06` | VERIFIED |
| FR-025 | Quản lý người dùng (xem danh sách, xem chi tiết, sửa, xóa) | [SRS]; [DT]; [UCD]; [MU] | SRS mục A.I.2.f (tr.12), B.III UC012 (tr.17); DT mục II.2.g (tr.5); MU `wf07` | VERIFIED (đối tượng "người dùng": TBD – ISS-12) |
| FR-026 | Báo cáo doanh thu (vé, sản phẩm bổ sung, dịch vụ khác) theo ngày, tuần, tháng, theo rạp | [SRS]; [UCD]; [MU] | SRS mục A.I.2.g (tr.13), B.III UC013 (tr.17); MU `wf08` | VERIFIED |
| FR-027 | Lọc báo cáo doanh thu theo phim, phòng chiếu, chương trình khuyến mãi | [SRS] | SRS mục A.I.2.g (tr.13) | VERIFIED |
| FR-028 | Xuất báo cáo doanh thu ra Excel hoặc PDF | [SRS] | SRS mục A.I.2.g (tr.13), B.III UC013 (tr.17) | VERIFIED |
| FR-029 | Màn hình tổng quan (doanh thu ngày/tháng/phim/rạp, khách hàng mới, tổng vé bán trong ngày) | [DT]; [MU] | DT mục II.2.a (tr.3–4); MU `wf08` | VERIFIED (liên kết với UC-013: INFERRED) |
| FR-030 | Phân quyền người dùng | [SRS] | SRS mục A.I (tr.3), A.I.1.a (tr.3) | VERIFIED (chưa có UC – ISS-11) |
| FR-031 | Theo dõi và quản lý đơn đặt vé / đơn hàng | [SRS]; [DT] | SRS mục A.I (tr.3); DT mục II (tr.2) | VERIFIED (chưa có UC – ISS-11) |
| FR-032 | Quản lý chương trình khuyến mãi và giá vé | [DT] | DT mục II (tr.2) | TBD – chỉ có trong DT, chưa có UC |
| FR-033 | Kiểm tra tính hợp lệ của vé khi khách đến rạp | [DT] | DT mục II (tr.2) | TBD – chỉ có trong DT, chưa có UC |
| FR-034 | Đổi suất chiếu hoặc hoàn vé cho khách | [DT] | DT mục II (tr.2) | OUT OF SCOPE – không hoàn vé, không đổi suất (ISS-02, đã xác nhận) |
| FR-035 | Quản lý nhân viên | [SRS] | SRS mục A.I (tr.3), A.II (tr.14) | TBD – chưa rõ có trùng với UC-012 hay không (ISS-12) |

## 4. Bảng truy vết – Non-functional Requirements

| Requirement ID | Nội dung | Nguồn | Trang/Mục | Trạng thái xác minh |
|---|---|---|---|---|
| NFR-001 | Giao diện thân thiện, dễ sử dụng | [DT]; [SRS] | DT mục III (tr.5); SRS mục A.I (tr.3), A.II (tr.14) | VERIFIED |
| NFR-002 | Người dùng mới có thể sử dụng hiệu quả mà không cần đào tạo chuyên sâu | [SRS] | SRS mục A.II (tr.14) | VERIFIED |
| NFR-003 | Bảo mật cao; kiểm tra và xác thực quyền truy cập | [DT]; [SRS] | DT mục III (tr.5); SRS mục A.I (tr.3), A.I.1.a (tr.3) | VERIFIED |
| NFR-004 | Hệ thống chạy ổn định | [DT]; [SRS] | DT mục III (tr.5); SRS mục A.I (tr.3) | VERIFIED |
| NFR-005 | Dễ bảo trì và nâng cấp | [DT] | DT mục III (tr.5) | VERIFIED |
| NFR-006 | Phục vụ quy mô rạp chiếu phim nhỏ đến trung bình | [SRS] | SRS mục A.II (tr.14) | VERIFIED |
| NFR-007 | Kết nối với hệ thống thanh toán (hệ thống con) | [SRS] | SRS mục A.II (tr.14) | VERIFIED |
| NFR-008 | Kết nối với hệ thống quản lý dữ liệu (lịch chiếu, doanh thu, dữ liệu khách hàng) | [SRS] | SRS mục A.II (tr.14) | VERIFIED |

## 5. Bảng truy vết – Business Rules

| Requirement ID | Nội dung | Nguồn | Trang/Mục | Trạng thái xác minh |
|---|---|---|---|---|
| BR-001 | Nhân viên là người thực hiện đặt vé cho khách hàng | [SRS] | SRS mục A.I (tr.3) | VERIFIED – đã xác nhận (ISS-01) |
| BR-002 | Không bán vé vượt quá số ghế còn trống của phòng chiếu | [SRS] | SRS mục A.I (tr.3) | VERIFIED |
| BR-003 | Không hoàn vé sau khi đã thanh toán | [SRS] | SRS mục A.I (tr.3) | VERIFIED – đã xác nhận (ISS-02) |
| BR-004 | Không có tùy chọn hủy vé sau khi vé đã được xác nhận và thanh toán | [SRS] | SRS mục A.I (tr.3) | VERIFIED – đã xác nhận (ISS-02) |
| BR-005 | Mỗi suất chiếu liên kết với một phòng chiếu cụ thể và có số lượng vé nhất định | [SRS] | SRS mục A.I (tr.3) | VERIFIED |
| BR-006 | Một phòng chiếu có thể phục vụ nhiều phim và nhiều suất chiếu | [SRS]; [DT] | SRS mục A.I (tr.3); DT mục II (tr.2) | VERIFIED |
| BR-007 | Một phim có thể có nhiều suất chiếu trong ngày hoặc qua nhiều ngày, tại các phòng chiếu khác nhau | [SRS]; [DT] | SRS mục A.I (tr.3); DT mục II (tr.2) | VERIFIED |
| BR-008 | Số ghế còn trống được cập nhật tự động sau mỗi giao dịch bán vé | [SRS] | SRS mục A.I.1.d (tr.6) | VERIFIED |
| BR-009 | Người dùng phải đăng nhập trước khi sử dụng các chức năng nghiệp vụ | [UCD]; [SRS] | UCD (quan hệ «include» tới "Đăng nhập hệ thống"); SRS mục C.II điều kiện trước (tr.19) | VERIFIED |
| BR-010 | Người dùng chỉ thực hiện được các chức năng đã được phân quyền | [SRS] | SRS mục A.I.1.a (tr.3) | VERIFIED |
| BR-011 | Đăng nhập sai tài khoản hoặc mật khẩu thì hệ thống thông báo và cho nhập lại | [SRS] | SRS mục C.I UC001 – luồng phụ 4.1, 4.2 (tr.18) | VERIFIED |
| BR-012 | Người quản lí có quyền truy cập và điều chỉnh tất cả thông tin và chức năng trong hệ thống | [SRS] | SRS mục B.II (tr.15–16) | VERIFIED |

## 6. Bảng truy vết – Use Case

| Use Case ID | Mã gốc | Tên | Nguồn | Trang/Mục | Trạng thái xác minh |
|---|---|---|---|---|---|
| UC-001 | UC001 | Đăng nhập hệ thống | [SRS]; [UCD] | SRS B.III (tr.16), C.I (tr.18) | VERIFIED – đặc tả đầy đủ luồng chính và luồng phụ |
| UC-002 | UC002 | Tìm kiếm các bộ phim | [SRS]; [UCD] | SRS B.III (tr.16), C.II (tr.19–20) | VERIFIED – có mục đích, tác nhân, điều kiện; **chưa có luồng sự kiện** |
| UC-003 | UC003 | Xem lịch chiếu | [SRS]; [UCD] | SRS B.III (tr.16) | VERIFIED – chỉ có mô tả ngắn |
| UC-004 | UC004 | Bán vé xem phim | [SRS]; [UCD] | SRS B.III (tr.16) | VERIFIED – chỉ có mô tả ngắn |
| UC-005 | UC005 | Thêm phim | [SRS] | SRS B.III (tr.16) | VERIFIED – chỉ có mô tả ngắn; trên UCD gộp thành "Quản lí phim" (ISS-08) |
| UC-006 | UC006 | Sửa phim | [SRS] | SRS B.III (tr.16) | VERIFIED – như trên |
| UC-007 | UC007 | Xóa phim | [SRS] | SRS B.III (tr.16) | VERIFIED – như trên |
| UC-008 | UC008 | Quản lý rạp chiếu phim | [SRS]; [UCD] | SRS B.III (tr.16–17) | VERIFIED – chỉ có mô tả ngắn |
| UC-009 | UC009 | Quản lý phòng chiếu | [SRS]; [UCD] | SRS B.III (tr.17) | VERIFIED – chỉ có mô tả ngắn |
| UC-010 | UC010 | Quản lý lịch chiếu | [SRS]; [UCD] | SRS B.III (tr.17) | VERIFIED – chỉ có mô tả ngắn |
| UC-011 | UC011 | Quản lý suất chiếu | [SRS]; [UCD] | SRS B.III (tr.17) | VERIFIED – chỉ có mô tả ngắn |
| UC-012 | UC012 | Quản lý người dùng | [SRS]; [UCD] | SRS B.III (tr.17) | VERIFIED – chỉ có mô tả ngắn |
| UC-013 | UC013 | Thống kê doanh thu | [SRS]; [UCD] | SRS B.III (tr.17) | VERIFIED – chỉ có mô tả ngắn |
