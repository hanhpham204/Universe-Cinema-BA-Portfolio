# Business Rules – Quy tắc nghiệp vụ

> **Nguồn chính:** [SRS] mục A.I "Mục đích", A.I.1, C.I (UC001); [DT] mục II; [UCD].
> Quy ước trạng thái: xem [Source Traceability](../07_Traceability/Source_Traceability.md).
> Tài liệu gốc không đánh mã quy tắc nghiệp vụ. Mã BR-xxx do portfolio đặt để truy vết.

## 1. Quy tắc nghiệp vụ từ tài liệu học phần

| ID | Quy tắc | Áp dụng cho | Source Reference | Trạng thái |
|---|---|---|---|---|
| BR-001 | Nhân viên là người thực hiện đặt vé cho khách hàng. Khi khách chọn phim và suất chiếu, nhân viên đặt vé, chọn số lượng vé và thực hiện thanh toán. | UC-004 | SRS A.I | VERIFIED – **Đã xác nhận** bởi chủ portfolio ngày 23/11/2026 (ISS-01). Không có kênh khách tự đặt vé. |
| BR-002 | Hệ thống tự động kiểm tra số ghế còn trống trong phòng chiếu và **không cho phép bán vé vượt quá số ghế có sẵn**. | UC-004 | SRS A.I | VERIFIED |
| BR-003 | Hệ thống **không cho phép hoàn vé** sau khi đã thanh toán. Không hỗ trợ đổi suất chiếu. | UC-004 | SRS A.I | VERIFIED – **Đã xác nhận** bởi chủ portfolio ngày 23/11/2026 (ISS-02) |
| BR-004 | Khi vé đã được xác nhận và thanh toán thì **không có tùy chọn hủy vé**. | UC-004 | SRS A.I | VERIFIED – **Đã xác nhận** bởi chủ portfolio ngày 23/11/2026 (ISS-02) |
| BR-005 | Mỗi suất chiếu liên kết với **một** phòng chiếu cụ thể và có số lượng vé nhất định. | UC-004, UC-011 | SRS A.I | VERIFIED |
| BR-006 | Một phòng chiếu có thể phục vụ nhiều phim và nhiều suất chiếu khác nhau. | UC-009, UC-011 | SRS A.I; DT II | VERIFIED |
| BR-007 | Một phim có thể được chiếu ở nhiều suất chiếu trong ngày hoặc qua nhiều ngày khác nhau, tại các phòng chiếu khác nhau. | UC-010, UC-011 | SRS A.I; DT II | VERIFIED |
| BR-008 | Số lượng ghế còn trống được cập nhật tự động sau mỗi giao dịch bán vé. | UC-003, UC-004 | SRS A.I.1.d | VERIFIED |
| BR-009 | Người dùng phải đăng nhập trước khi sử dụng các chức năng nghiệp vụ. | UC-002 → UC-013 | UCD (các UC đều «include» "Đăng nhập hệ thống"); SRS C.II (điều kiện trước) | VERIFIED |
| BR-010 | Sau khi đăng nhập, người dùng chỉ thực hiện được các chức năng đã được phân quyền. | Tất cả UC | SRS A.I.1.a | VERIFIED |
| BR-011 | Nếu tài khoản hoặc mật khẩu không đúng, hệ thống thông báo và cho người dùng nhập lại. | UC-001 | SRS C.I – luồng phụ 4.1, 4.2 | VERIFIED |
| BR-012 | Người quản lí có quyền truy cập và điều chỉnh tất cả thông tin và chức năng trong hệ thống. | UC-005 → UC-013 | SRS B.II | VERIFIED |

## 2. Đề xuất bổ sung – Quy tắc cần làm rõ (PROPOSED)

> ⚠️ **Đề xuất bổ sung.** Các quy tắc dưới đây **không có trong tài liệu học phần**. Đây là những câu hỏi nghiệp vụ mà một BA thường cần hỏi để hoàn thiện đặc tả. Tất cả cần được xác nhận trước khi đưa vào yêu cầu chính thức.

| ID | Quy tắc đề xuất | Liên quan | Lý do đề xuất |
|---|---|---|---|
| BR-P01 | Hai suất chiếu trong cùng một phòng chiếu không được trùng hoặc chồng lấn thời gian (giờ bắt đầu – giờ kết thúc). | UC-011, BR-005 | Nguồn có giờ bắt đầu/kết thúc và phòng chiếu cho suất chiếu nhưng chưa có quy tắc chống trùng lịch |
| BR-P02 | Không được xóa phim, phòng chiếu hoặc suất chiếu đã có vé được bán; chỉ cho phép ngừng sử dụng. | UC-007, UC-009, UC-011 | Bảo toàn dữ liệu doanh thu (UC-013) và BR-003 |
| BR-P03 | Một ghế của một suất chiếu chỉ được bán cho một vé. | UC-004, BR-002 | Làm rõ BR-002 ở mức từng ghế |
| BR-P04 | Không bán vé cho suất chiếu đã bắt đầu. | UC-004 | Chưa có quy tắc về thời điểm ngừng bán |
| BR-P05 | Giá vé được xác định theo `[TBD – loại ghế / suất chiếu / khuyến mãi]`. | UC-004, FR-032 | Nguồn nhắc tới giá vé và khuyến mãi nhưng không có quy tắc tính giá |
| BR-P06 | Phim có phân loại độ tuổi (ví dụ T18) cần được hiển thị khi bán vé. | UC-004 | Mockup `wf02` có dòng "Rated: T18…" nhưng chưa có quy tắc kiểm tra |
