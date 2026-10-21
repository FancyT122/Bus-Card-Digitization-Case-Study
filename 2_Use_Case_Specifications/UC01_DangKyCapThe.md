# Đặc tả Use Case 01: Đăng ký hồ sơ cấp thẻ mới

<p align="center">
  <img width="907" height="807" alt="uc01" src="https://github.com/user-attachments/assets/1396fee0-1ffe-45b9-8abf-2e5ac067f9f7" />

  <br>
  <i>Sơ đồ Use Case 01: Đăng ký hồ sơ cấp thẻ mới</i>
</p>
## 1. Tóm tắt
Use Case này cho phép người dùng thực hiện đăng ký hồ sơ cấp thẻ xe buýt mới trực tuyến trên ứng dụng BUSGO hoặc nền tảng trình duyệt Web. Quy trình bao gồm việc khai báo thông tin định danh, lựa chọn đối tượng, cung cấp giấy tờ minh chứng và nộp hồ sơ để chờ xét duyệt.

## 2. Tiền điều kiện
*   Hệ thống đăng ký đang mở và thiết bị của người dùng có kết nối mạng.
*   Không yêu cầu người dùng phải đăng nhập hệ thống.

## 3. Hậu điều kiện
*   **Thành công:** Hồ sơ được ghi nhận thành công, tự động cấp một Case ID riêng biệt và chính thức chuyển sang trạng thái "Chờ duyệt". 
*   **Thất bại:** Hồ sơ không được tạo, hệ thống giữ nguyên trạng thái và yêu cầu người dùng kiểm tra lại thông tin.

## 4. Luồng sự kiện

### 4.1. Luồng đăng ký tiêu chuẩn (Main Flow - Dành cho công dân có CCCD)
1.  **Bước 1 - Tiếp nhận thông tin định danh:** Người dùng chọn "Quét QR CCCD" và đưa phần mã QR in trên thẻ vào khung camera. Hệ thống tự động bóc tách và điền dữ liệu (Số CCCD, Họ và tên, Ngày sinh, Giới tính, Địa chỉ, Ngày cấp) trong thời gian không quá 2 giây.
2.  **Bước 2 - Khai báo Địa chỉ:** Hệ thống hiển thị "Địa chỉ chuẩn hóa" bằng cách tự động chuyển đổi địa chỉ theo đơn vị hành chính mới nhất. Người dùng tích chọn "Nơi ở hiện tại trùng khớp với địa chỉ trên CCCD" để xác nhận.
3.  **Bước 3 - Chọn Đối tượng & Nhận thẻ:** Hệ thống tự động gợi ý nhóm đối tượng ưu tiên dựa trên ngày sinh. Người dùng bắt buộc nhập Số điện thoại liên hệ (10 chữ số, bắt đầu bằng số 0) và chọn một bến xe tại mục Điểm nhận thẻ.
4.  **Bước 4 - Cung cấp Giấy tờ:** Người dùng chụp hoặc tải lên Ảnh chân dung và Ảnh CCCD 2 mmặt. Hệ thống hỗ trợ công cụ cắt, phóng to/thu nhỏ và xoay ảnh ngay sau khi chọn.
5.  **Bước 5 - Xác nhận & Nộp hồ sơ:** Người dùng rà soát lại dữ liệu, có thể chạm vào ảnh để xem to hơn hoặc nhấn "Chỉnh sửa" nếu cần. Người dùng tích chọn ô đồng ý cho phép thu thập dữ liệu cá nhân và nhấn nút "Nộp hồ sơ".
6.  Hệ thống hiển thị màn hình thông báo "Nộp hồ sơ thành công" và cung cấp Case ID.

### 4.2. Luồng thay thế
*   **4.2.1. Đăng ký thủ công:** Áp dụng khi thẻ CCCD không quét được QR. Người dùng trực tiếp nhập liệu các trường bắt buộc (*), đảm bảo Số CCCD phải đủ 12 chữ số và đúng định dạng.
*   **4.2.2. Nơi ở hiện tại khác CCCD:** Tại Bước 2, người dùng tích chọn "Nơi ở hiện tại khác với địa chỉ thường trú". Hệ thống sẽ mở ra các ô nhập liệu để người dùng tự nhập tay địa chỉ đang ở thực tế (dành cho người ở trọ, tạm trú).
*   **4.2.3. Cung cấp giấy tờ bổ sung:** Tại Bước 4, nếu người dùng chọn diện ưu tiên là Người có công hoặc Người khuyết tật, hệ thống sẽ tự động hiển thị thêm mục yêu cầu nộp Giấy tờ bổ sung.
*   **4.2.4. Luồng đăng ký đặc biệt cho Trẻ em (Dưới 6 tuổi):** 
    *   Người dùng khai báo thông tin dựa trên Giấy khai sinh, nhập đúng 12 chữ số mã định danh trên giấy khai sinh.
    *   Bắt buộc khai báo thông tin "Người giám hộ" (Họ và tên, Quan hệ với trẻ, Số điện thoại liên hệ).
    *   Hình ảnh minh chứng yêu cầu là ảnh chân dung trẻ (tỉ lệ 3:4) và ảnh chụp rõ 4 góc của Giấy khai sinh.

### 4.3. Luồng ngoại lệ
*   **4.3.1. Ràng buộc tuổi trẻ em:** Khi đăng ký luồng đặc biệt cho trẻ em, hệ thống ràng buộc Ngày sinh nhập vào phải đảm bảo trẻ dưới 6 tuổi tại ngày đăng ký.
*   **4.3.2. Ràng buộc số điện thoại:** Hệ thống từ chối nếu số điện thoại liên hệ không đúng định dạng 10 chữ số hoặc không bắt đầu bằng số 0.
*   **4.3.3. Ràng buộc định danh:** Số định danh cá nhân/CCCD nhập thủ công hoặc trên Web bắt buộc phải đủ 12 chữ số.

## 5. Điểm mở rộng
Không có.
*   `Tải giấy tờ minh chứng bắt buộc`, `Chụp/Tải ảnh CCCD 2 mặt`, `Nhập thông tin người giám hộ` tùy thuộc vào Nhóm đối tượng ưu tiên được chọn[cite: 8].

## 6. Yêu cầu đặc biệt (Special Requirements)
*   **Tính khả dụng đa nền tảng:** Giao diện đăng ký trực tuyến phải tương thích trên cả ứng dụng di động (BUSGO) và trình duyệt Web tại địa chỉ cổng thông tin công dân (Đã ẩn danh)[cite: 8].
