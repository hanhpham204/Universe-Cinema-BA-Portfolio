# Non-functional Requirements – Yêu cầu phi chức năng

> **Nguồn:** [DT] mục III "Yêu cầu phi chức năng" và [SRS] mục A.I "Mục đích", A.II "Phạm vi".
> Quy ước trạng thái: xem [Source Traceability](../07_Traceability/Source_Traceability.md).

## 1. Yêu cầu phi chức năng từ tài liệu học phần

| ID | Nhóm | Yêu cầu | Source Reference | Trạng thái |
|---|---|---|---|---|
| NFR-001 | Usability | Giao diện thân thiện, dễ sử dụng | DT III; SRS A.I, A.II | VERIFIED |
| NFR-002 | Usability | Người dùng mới có thể làm quen và sử dụng hiệu quả mà không cần đào tạo chuyên sâu; giao diện và chức năng dựa trên quy trình nghiệp vụ thực tế tại rạp | SRS A.II | VERIFIED |
| NFR-003 | Security | Hệ thống có tính bảo mật cao; kiểm tra và xác thực quyền truy cập để đảm bảo an toàn thông tin | DT III; SRS A.I, A.I.1.a | VERIFIED |
| NFR-004 | Reliability | Hệ thống chạy ổn định | DT III; SRS A.I | VERIFIED |
| NFR-005 | Maintainability | Hệ thống dễ bảo trì và nâng cấp | DT III | VERIFIED |
| NFR-006 | Scope / Capacity | Hướng đến quy mô rạp chiếu phim từ nhỏ đến trung bình | SRS A.II | VERIFIED |
| NFR-007 | Interface | Kết nối với hệ thống con **Hệ thống thanh toán** để xử lý giao dịch bán vé và dịch vụ bổ sung | SRS A.II | VERIFIED |
| NFR-008 | Interface | Kết nối với hệ thống con **Hệ thống quản lý dữ liệu** để lưu trữ và xử lý lịch chiếu, doanh thu, dữ liệu khách hàng | SRS A.II | VERIFIED |

### Nhận xét chất lượng (review)

- Các yêu cầu NFR-001 đến NFR-005 **chưa đo lường được**: không có chỉ số, ngưỡng hay phương pháp kiểm chứng. Vì vậy chưa thể dùng làm tiêu chí nghiệm thu (ISS-18).
- [SRS] mục B.IV "Các điều kiện phụ thuộc" (cấu hình phần cứng, phần mềm, hệ quản trị CSDL, công cụ phát triển) **vẫn để trống theo mẫu**. Portfolio **không ghi nhận** bất kỳ công nghệ nào của dự án.

## 2. Đề xuất bổ sung – NFR có thể đo lường (PROPOSED)

> ⚠️ **Đề xuất bổ sung.** Phần này **không có trong tài liệu học phần**. Đây là cách viết lại NFR theo hướng đo lường được, để minh họa kỹ năng BA. Mọi giá trị ngưỡng để ở dạng `[TBD]` vì tài liệu gốc không cung cấp số liệu. Portfolio không tự đặt con số.

| ID | Làm rõ cho | Yêu cầu đề xuất | Cách kiểm chứng đề xuất |
|---|---|---|---|
| NFR-P01 | NFR-001, NFR-002 | Nhân viên mới hoàn thành một giao dịch bán vé (chọn phim → ghế → thanh toán) sau tối đa `[TBD]` phút hướng dẫn | Kiểm thử khả dụng với người dùng chưa qua đào tạo |
| NFR-P02 | NFR-003 | Mật khẩu không được lưu dưới dạng văn bản thuần | Review thiết kế/CSDL |
| NFR-P03 | NFR-003 | Mỗi chức năng chỉ hiển thị và thực thi được với vai trò được phân quyền (Nhân viên bán vé / Người quản lí) | Test case phân quyền theo ma trận vai trò – chức năng |
| NFR-P04 | NFR-004 | Hai giao dịch đồng thời không thể bán cùng một ghế của cùng một suất chiếu | Test đồng thời (concurrency) trên cùng suất chiếu |
| NFR-P05 | NFR-004 | Thời gian phản hồi khi tải sơ đồ ghế của một suất chiếu ≤ `[TBD]` giây | Đo hiệu năng |
| NFR-P06 | NFR-006 | Hỗ trợ tối thiểu `[TBD]` rạp, `[TBD]` phòng chiếu/rạp, `[TBD]` người dùng đồng thời | Xác nhận với khách hàng / giảng viên |
| NFR-P07 | NFR-005 | Mỗi thay đổi yêu cầu được cập nhật trong Requirements Traceability Matrix | Review tài liệu |
