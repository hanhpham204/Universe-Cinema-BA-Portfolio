# Case Study – Rà soát và xử lý mâu thuẫn trong tài liệu yêu cầu

> ⚠️ **Phạm vi:** Case study mô tả công việc rà soát tài liệu khi **xây dựng portfolio** (11/2026), không phải hoạt động đã làm trong học phần (08/2024). Các vấn đề được nêu là có thật trong tài liệu học phần. **Hướng xử lý là đề xuất**, chưa được nhóm xác nhận.

## 1. Bối cảnh

Nhóm có hai tài liệu mô tả cùng một hệ thống:

- **SRS V1.0**: theo mẫu đặc tả yêu cầu ứng dụng, có 13 use case.
- **Tài liệu đặc tả đề tài**: phần giới thiệu và mô tả chức năng.

Hai tài liệu được viết gần như cùng thời điểm (08/2024), nhưng không qua một vòng đối chiếu chéo. Khi gom lại thành một bộ yêu cầu thống nhất, cần trả lời: **yêu cầu nào đáng tin, yêu cầu nào đang mâu thuẫn, và cái gì còn thiếu?**

## 2. Cách làm

| Bước | Hoạt động | Sản phẩm |
|---|---|---|
| 1 | Đọc toàn bộ hai tài liệu, kể cả hình nhúng (sơ đồ use case, 8 mockup). Chuyển sang PDF để có số trang trích dẫn. | Danh sách nguồn [SRS], [DT], [UCD], [MU] |
| 2 | Tách từng câu mô tả chức năng thành một yêu cầu nguyên tử, đánh mã FR/NFR/BR | 35 FR, 8 NFR, 12 BR |
| 3 | Ghi nguồn cho từng yêu cầu: tài liệu, mục, trang | [Source Traceability](../07_Traceability/Source_Traceability.md) |
| 4 | Đối chiếu cùng một chủ đề giữa các nguồn: văn bản ↔ văn bản, văn bản ↔ sơ đồ, văn bản ↔ mockup | 22 vấn đề trong [Issue Log](../08_Review/Assumptions_and_Open_Questions.md) |
| 5 | Phân loại vấn đề: Mâu thuẫn / Khoảng trống / Không nhất quán / Chất lượng | Cột "Loại" trong Issue Log |
| 6 | Gắn nhãn độ tin cậy cho từng yêu cầu: VERIFIED / INFERRED / PROPOSED / TBD | Toàn bộ tài liệu |
| 7 | Với mâu thuẫn: ghi cả hai phiên bản, không tự chọn; chuyển thành câu hỏi cho stakeholder | Q-01 → Q-13 |
| 8 | Lập RTM để tìm yêu cầu "mồ côi" (không có use case) | [RTM](../07_Traceability/Requirements_Traceability_Matrix.md): 6 FR chưa có UC |

## 3. Ba phát hiện tiêu biểu

### 3.1 Hệ thống bán vé tại quầy hay website khách tự đặt? (ISS-01)

| Nguồn | Nói gì |
|---|---|
| SRS A.I | "Nhân viên sẽ là người thực hiện việc đặt vé cho khách hàng" |
| SRS B.II, sơ đồ use case | Chỉ có 2 actor: Nhân viên, Quản trị viên |
| Đặc tả đề tài II.1 | "Người dùng" tự đăng ký, đặt vé, chọn bắp nước, thanh toán **trên trang web** |
| Sơ đồ use case | Ranh giới hệ thống tên "Website đặt vé xem phim online" |
| Mockup | Dạng cửa sổ ứng dụng; người dùng là "Admin" |

**Vì sao quan trọng:** Câu trả lời quyết định có actor Khách hàng hay không, có chức năng đăng ký hay không, và quy trình bán vé (BP-02) khác hẳn.
**Xử lý:** Không chọn bên nào. Portfolio tạm theo SRS vì đây là bảng actor chính thức và khớp với sơ đồ (giả định A-01). Mọi nội dung phụ thuộc được đánh 🔁/TBD, và câu hỏi Q-01 được chuyển cho nhóm.
**Kết quả:** Chủ portfolio xác nhận (23/11/2026) hệ thống là **phần mềm bán vé tại quầy**. Khách hàng không phải actor; chức năng đăng ký tài khoản và đặt vé online được đưa ra ngoài phạm vi.

### 3.2 Có hoàn vé hay không? (ISS-02)

- SRS: *"Hệ thống không cho phép hoàn vé sau khi đã thanh toán… không có tùy chọn hủy vé"*.
- Đặc tả đề tài: nhân viên *"xử lý các vấn đề phát sinh như đổi suất chiếu hoặc hoàn vé"*.

**Vì sao quan trọng:** Đây là quy tắc nghiệp vụ ảnh hưởng tới doanh thu, dữ liệu vé và test case.
**Xử lý:** BR-003, BR-004 giữ nhãn VERIFIED (trong SRS) nhưng thêm TBD. Hoàn vé (FR-034) không được dựng quy trình. Test case TC-UC004-09 được đánh dấu phụ thuộc vào kết luận này.
**Kết quả:** Đã xác nhận (23/11/2026) **không hoàn vé, không đổi suất, không hủy vé**. BR-003, BR-004 được chốt; FR-034 đưa ra ngoài phạm vi.

### 3.3 Đặc tả use case bị sao chép (ISS-09)

Trong SRS mục C, đặc tả UC003 đến UC013 có cùng nội dung với UC002 ("Cho phép người dùng tìm kiếm… các bộ phim"), kể cả UC "Thống kê doanh thu".

**Vì sao quan trọng:** Nếu dùng nguyên văn, bộ tài liệu sẽ chứa 11 đặc tả sai.
**Xử lý:** Không dùng các mục này làm căn cứ. Thay vào đó lấy mô tả ngắn ở bảng B.III và mô tả chức năng ở mục A. Luồng sự kiện ghi "Chưa có dữ liệu nguồn". UC-004 (cốt lõi nhất) được viết lại thành [đặc tả chi tiết](../03_Use_Case/UC-004_Sell_Ticket_Detailed_Specification.md), có đánh dấu rõ là đề xuất.

## 4. Kết quả

| Chỉ số | Giá trị |
|---|---|
| Yêu cầu chức năng được đánh mã, có nguồn | 35 (28 VERIFIED, 1 INFERRED, 4 TBD, 2 ngoài phạm vi) |
| Vấn đề được ghi nhận | 22 (mâu thuẫn, khoảng trống, không nhất quán, chất lượng) |
| Câu hỏi chuyển cho stakeholder | 13 (đã trả lời 4) |
| Yêu cầu chưa có use case | 6 |

*(Đây là số đếm trên bộ tài liệu, không phải chỉ số hiệu quả của dự án.)*

## 5. Bài học

1. **Đối chiếu chéo cả hình ảnh**, không chỉ văn bản. Hai trong ba phát hiện lớn đến từ việc so sơ đồ và mockup với văn bản.
2. **Không âm thầm chọn một phiên bản.** Ghi cả hai, kèm ảnh hưởng, rồi hỏi người có thẩm quyền.
3. **Gắn nhãn độ tin cậy** giúp người đọc biết phần nào là yêu cầu đã chốt, phần nào là đề xuất.
4. **Ma trận truy vết** là công cụ tìm lỗ hổng phạm vi, không chỉ là bảng bàn giao.
