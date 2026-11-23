# Activity Diagram – Quy trình nghiệp vụ

> ⚠️ **Lưu ý về nguồn gốc:** Tài liệu học phần **không có Activity Diagram**. Các mục "Biểu đồ" trong SRS mục C đều để trống. Các sơ đồ dưới đây được **dựng mới cho portfolio** từ mô tả nghiệp vụ trong [SRS]/[DT] và mockup [MU]. Chúng **không phải sản phẩm đã thực hiện trong học phần**.
>
> Mỗi bước được tô màu theo mức độ căn cứ:
>
> | Màu | Ý nghĩa |
> |---|---|
> | 🟩 Xanh lá | **VERIFIED** – bước có trong tài liệu gốc |
> | 🟨 Vàng | **INFERRED** – thứ tự hoặc bước suy ra từ mockup/tài liệu, chưa xác nhận |
> | 🟪 Tím, viền nét đứt | **PROPOSED** – đề xuất bổ sung |
>
> Sơ đồ dùng Mermaid `flowchart` và hiển thị trực tiếp trên GitHub.

## 1. Danh sách quy trình nghiệp vụ được xác định

| Mã | Quy trình | Actor | Căn cứ | Mức căn cứ |
|---|---|---|---|---|
| BP-01 | Đăng nhập hệ thống | Nhân viên bán vé, Người quản lí | SRS C.I (UC001) – có luồng chính và luồng phụ | Đủ để dựng sơ đồ |
| BP-02 | Bán vé tại quầy | Nhân viên bán vé | SRS A.I, A.I.1.d; DT II.1.e; MU `wf02`–`wf04` | Đủ để dựng; thứ tự suy ra từ mockup |
| BP-03 | Thiết lập dữ liệu chiếu phim (phim → phòng → suất chiếu) | Người quản lí | SRS A.I.2; quan hệ dữ liệu ở SRS A.I, DT II | Chỉ có chức năng rời rạc; trình tự là đề xuất |
| BP-04 | Hoàn vé / đổi suất chiếu | Nhân viên | DT II | **Không dựng sơ đồ**: đã xác nhận ngoài phạm vi (ISS-02) |
| BP-05 | Thống kê doanh thu | Người quản lí | SRS A.I.2.g | Không dựng: chưa có luồng nghiệp vụ trong nguồn |

---

## 2. BP-01 – Đăng nhập hệ thống

**Căn cứ:** SRS mục C.I – UC001, luồng chính bước 1–5 và luồng phụ 4.1–4.2. Toàn bộ bước là VERIFIED. Điểm rẽ nhánh "Thông tin hợp lệ?" là cách biểu diễn điều kiện dẫn tới luồng phụ 4.1.

```mermaid
flowchart TD
    S(["Bắt đầu"]) --> A1["Hệ thống hiển thị giao diện đăng nhập"]
    A1 --> A2["Nhân viên / Người quản lí nhập tài khoản, mật khẩu"]
    A2 --> A3["Chọn nút Đăng nhập"]
    A3 --> D1{"Tài khoản và mật khẩu đúng?"}
    D1 -- "Đúng" --> A4["Chuyển sang giao diện trang chủ"]
    D1 -- "Sai" --> A5["Thông báo tài khoản hoặc mật khẩu không đúng"]
    A5 --> A2
    A4 --> E(["Kết thúc"])

    classDef verified fill:#d9f2d9,stroke:#2e7d32,color:#1b1b1b
    class A1,A2,A3,D1,A4,A5 verified
```

---

## 3. BP-02 – Bán vé tại quầy

**Căn cứ:**

- VERIFIED: nhân viên đặt vé cho khách, chọn suất chiếu và ghế, thanh toán (SRS A.I, A.I.1.d); không bán vượt số ghế trống (SRS A.I); in vé hoặc gửi vé điện tử (SRS A.I.1.d); cập nhật số ghế còn trống (SRS A.I.1.d).
- INFERRED: thứ tự 3 bước "Chọn phim → Chọn ghế → Bắp/Nước" và bước "Chọn hình thức thanh toán" lấy từ mockup `wf02`–`wf04`. Bước chọn bắp nước có trong DT II.1.e và mockup, nhưng không có trong mô tả UC004 của SRS.
- PROPOSED: nhánh xử lý khi thanh toán thất bại.

```mermaid
flowchart TD
    S(["Bắt đầu"]) --> B1["Khách hàng chọn phim và suất chiếu"]
    B1 --> B2["Nhân viên chọn phim trên hệ thống"]
    B2 --> B3["Nhân viên chọn suất chiếu"]
    B3 --> D1{"Suất chiếu còn ghế trống?"}
    D1 -- "Không" --> B4["Không cho phép bán vé, tư vấn suất chiếu khác"]
    B4 --> B2
    D1 -- "Có" --> B5["Nhân viên chọn ghế ngồi"]
    B5 --> D2{"Khách mua thêm bắp, nước?"}
    D2 -- "Có" --> B6["Chọn loại / combo bắp nước"]
    D2 -- "Không" --> B7["Hiển thị tổng tiền"]
    B6 --> B7
    B7 --> B8["Chọn hình thức thanh toán"]
    B8 --> B9["Thực hiện thanh toán"]
    B9 --> D3{"Thanh toán thành công?"}
    D3 -- "Không" --> B10["Thông báo lỗi, không ghi nhận ghế đã bán"]
    B10 --> B8
    D3 -- "Có" --> B11["Hệ thống cập nhật số ghế còn trống"]
    B11 --> B12["In vé hoặc gửi vé điện tử cho khách"]
    B12 --> N1["Vé đã thanh toán: không hoàn, không hủy"]
    N1 --> E(["Kết thúc"])

    classDef verified fill:#d9f2d9,stroke:#2e7d32,color:#1b1b1b
    classDef inferred fill:#fff4c2,stroke:#b58900,color:#1b1b1b
    classDef proposed fill:#ece2f7,stroke:#6a3d9a,stroke-dasharray: 5 5,color:#1b1b1b
    class B1,B3,D1,B4,B5,B9,B11,B12,N1 verified
    class B2,D2,B6,B7,B8 inferred
    class D3,B10 proposed
```

> **Điểm cần xác minh:** mockup `wf02` chưa thể hiện rõ bước chọn suất chiếu (ISS-22). Hiện có hai mô tả khác nhau là "chọn số lượng vé" (SRS A.I) và "chọn ghế cụ thể" (SRS A.I.1.d, mockup). Quy tắc "không hoàn, không hủy" đã được chủ portfolio xác nhận ngày 23/11/2026 (ISS-02).

---

## 4. BP-03 – Thiết lập dữ liệu chiếu phim (PROPOSED)

> ⚠️ **Đề xuất bổ sung.** Các chức năng trong sơ đồ (thêm phim, thêm phòng chiếu, quản lý ghế, thêm suất chiếu) đều VERIFIED (SRS A.I.2). Tuy nhiên tài liệu gốc **không mô tả trình tự** giữa chúng. Trình tự dưới đây được suy ra từ quan hệ dữ liệu: suất chiếu cần có phim và phòng chiếu (BR-005, BR-007). Kiểm tra trùng lịch là quy tắc đề xuất BR-P01.

```mermaid
flowchart TD
    S(["Bắt đầu"]) --> C1["Người quản lí đăng nhập"]
    C1 --> D1{"Phim đã có trên hệ thống?"}
    D1 -- "Chưa" --> C2["Thêm phim: tên, thể loại, đạo diễn, diễn viên, thời lượng, mô tả, hình ảnh"]
    D1 -- "Rồi" --> D2
    C2 --> D2{"Rạp và phòng chiếu đã có?"}
    D2 -- "Chưa" --> C3["Thêm rạp, thêm phòng chiếu và sơ đồ ghế"]
    D2 -- "Rồi" --> C4
    C3 --> C4["Thêm suất chiếu: phim, phòng chiếu, giờ bắt đầu, giờ kết thúc"]
    C4 --> D3{"Trùng lịch với suất khác trong cùng phòng?"}
    D3 -- "Có" --> C5["Thông báo trùng lịch, chọn giờ hoặc phòng khác"]
    C5 --> C4
    D3 -- "Không" --> C6["Lưu suất chiếu, suất chiếu sẵn sàng để bán vé"]
    C6 --> E(["Kết thúc"])

    classDef verified fill:#d9f2d9,stroke:#2e7d32,color:#1b1b1b
    classDef inferred fill:#fff4c2,stroke:#b58900,color:#1b1b1b
    classDef proposed fill:#ece2f7,stroke:#6a3d9a,stroke-dasharray: 5 5,color:#1b1b1b
    class C1,C2,C3,C4 verified
    class D1,D2,C6 inferred
    class D3,C5 proposed
```
