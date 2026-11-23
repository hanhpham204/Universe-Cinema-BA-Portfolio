# Documentation Review Checklist – Kiểm tra chất lượng tài liệu

Tài liệu gồm hai phần:

- **Phần A:** kết quả review **tài liệu gốc của học phần** ([SRS], [DT]), dùng làm căn cứ cho [Issue Log](Assumptions_and_Open_Questions.md).
- **Phần B:** kết quả tự kiểm tra **repository portfolio** trước khi xuất bản.

Ký hiệu: ✅ Đạt · ⚠️ Đạt một phần · ❌ Chưa đạt

---

## Phần A – Review tài liệu gốc của học phần

| # | Tiêu chí | Kết quả | Ghi chú / Bằng chứng |
|---|---|---|---|
| A1 | Có mục đích, phạm vi hệ thống | ✅ | SRS A.I, A.II; DT I, II |
| A2 | Có danh sách actor và mô tả | ⚠️ | SRS B.II có 2 actor; không khớp 3 nhóm người dùng ở SRS A.II (ISS-05) |
| A3 | Có danh sách use case có mã | ✅ | SRS B.III: UC001–UC013 |
| A4 | Use case diagram khớp với danh sách use case | ⚠️ | Quản lý phim gộp/tách khác nhau; 3 UC con tìm kiếm chỉ có trên sơ đồ (ISS-08) |
| A5 | Mỗi use case có đặc tả luồng sự kiện | ❌ | Chỉ UC001 đầy đủ; UC002 thiếu luồng; UC003–UC013 là bản sao UC002 (ISS-09) |
| A6 | Có quy tắc nghiệp vụ rõ ràng | ⚠️ | Có trong đoạn văn SRS A.I nhưng chưa tách thành danh sách có mã |
| A7 | Yêu cầu phi chức năng đo lường được | ❌ | 4 NFR định tính (DT III) (ISS-18) |
| A8 | Thống nhất giữa hai tài liệu | ❌ | Mâu thuẫn kênh bán vé, hoàn vé, xóa rạp, tiêu chí tìm kiếm (ISS-01 → ISS-04) |
| A9 | Thống nhất thuật ngữ, tên actor, tên hệ thống | ❌ | Nhiều tên cho cùng actor; "CinemaPro" (ISS-05, ISS-06) |
| A10 | Có bảng thuật ngữ | ❌ | SRS A.III để trống (ISS-19) |
| A11 | Có điều kiện kỹ thuật / ràng buộc | ❌ | SRS B.IV để trống (ISS-19) |
| A12 | Có mô hình dữ liệu / sơ đồ lớp | ❌ | DT V chỉ có tiêu đề (ISS-19) |
| A13 | Có mockup giao diện gắn với chức năng | ⚠️ | 8 mockup; một ảnh dùng lại cho 4 chức năng; chưa có mockup rạp, phòng, ghế, lịch chiếu |
| A14 | Có tiêu chí nghiệm thu / test case | ❌ | Không có |
| A15 | Có lịch sử phiên bản, phân công | ❌ | SRS ghi V1.0, không có bảng lịch sử và phân công |

---

## Phần B – Kiểm tra repository portfolio

Kiểm tra lần cuối trước khi đóng gói. Các kiểm tra tự động được chạy bằng script cục bộ.

| # | Tiêu chí | Kết quả | Cách kiểm tra / Ghi chú |
|---|---|---|---|
| B1 | Các link nội bộ (file và anchor) hoạt động | ✅ | Script kiểm tra toàn bộ link Markdown tương đối, tạo anchor theo quy tắc GitHub. Không còn link hỏng. |
| B2 | Tên file, thư mục nhất quán, tiếng Anh theo thuật ngữ BA | ✅ | Đúng cấu trúc yêu cầu; ảnh đặt tên `wfNN_*`, `use_case_diagram_*` |
| B3 | Requirement ID không trùng | ✅ | FR: 35/35 duy nhất · NFR: 15/15 · BR: 18/18 |
| B4 | Use Case ID không trùng | ✅ | Catalog 13/13, Specification 13/13 |
| B5 | Mọi ID được tham chiếu đều có định nghĩa | ✅ | Script đối chiếu FR/NFR/BR/UC/ISS: không có ID nào được tham chiếu mà chưa định nghĩa |
| B6 | Tài liệu có nguồn tham chiếu | ✅ | Mỗi FR/NFR/BR/UC có cột Source Reference; [Source Traceability](../07_Traceability/Source_Traceability.md) ghi mục, trang |
| B7 | Sơ đồ hiển thị được | ✅ | 5 sơ đồ Mermaid đã parse và render thành công bằng Mermaid 11. PlantUML đạt kiểm tra cú pháp `-checkonly` và render ra PNG. |
| B8 | Không có thông tin cá nhân nhạy cảm | ✅ | Đã loại họ tên, MSSV thành viên, tên giảng viên, mã lớp; che tên thành viên trên mockup WF-07; ảnh PNG không chứa metadata tác giả. Repo chỉ còn tên file gốc có chữ "Nhom07" (số nhóm). |
| B9 | Không trình bày suy đoán như sự thật | ✅ | Mọi nội dung có nhãn VERIFIED / INFERRED / PROPOSED / TBD; phần đề xuất có khung "⚠️ Đề xuất bổ sung" |
| B10 | Không tuyên bố quá mức về đóng góp cá nhân | ✅ | Vai trò ghi "theo thông tin chủ portfolio", đánh TBD; ghi rõ Activity Diagram, ERD không phải sản phẩm học phần; không nhận mockup, test case, UAT |
| B11 | Không có link demo, badge, số liệu, chứng nhận giả | ✅ | Không có link ngoài; số liệu mockup được chú thích là minh họa |
| B12 | Không có file hoặc thư mục trống | ✅ | Kiểm tra `find -empty`: không có |
| B13 | Không chứa tài liệu gốc (.docx) | ✅ | `.gitignore` chặn `*.docx` |
| B14 | Hình ảnh bản quyền bên thứ ba | ✅ | Poster phim thương mại trên mockup đã được che |
| B15 | Test case đề xuất không bị trình bày như đã thực thi | ✅ | 10 TC ghi "Chưa thực hiện", cột kết quả thực tế để trống; cột Test Case ID trong RTM chính vẫn ghi "Chưa có" |
| B16 | Test Case ID không trùng | ✅ | TC-UC004-01 → 10: 10/10 duy nhất |

### Hạn chế còn lại

- Chưa kiểm tra hiển thị thực tế trên GitHub (repo chưa được push). Mermaid trên GitHub có thể khác nhẹ về bố cục so với bản render cục bộ.
- Số trang trích dẫn phụ thuộc vào bản PDF chuyển đổi (A-04).
