# Đặc tả Use Case 02: Tra cứu trạng thái hồ sơ

*(Bạn nhớ upload file ảnh uc02.png lên cùng thư mục trên GitHub, sau đó thay link ảnh vào dòng bên dưới nhé)*
![Sơ đồ chi tiết Use Case 02](link_hinh_anh_cua_ban)

## 1. Tóm tắt (Summary)
Use Case này cho phép người dùng (công dân hoặc nhân viên hỗ trợ) tra cứu thông tin và theo dõi tiến độ xử lý hồ sơ cấp thẻ xe buýt trên Ứng dụng di động hoặc cổng Web công dân mà không cần đăng nhập vào hệ thống. Người dùng sử dụng Số định danh cá nhân (CCCD) để truy vấn kết quả.

## 2. Tiền điều kiện (Pre-conditions)
*   Hệ thống đang hoạt động và thiết bị của người dùng có kết nối mạng.
*   Người dùng đã từng nộp hồ sơ và có Số định danh cá nhân/CCCD hợp lệ.
*   Không yêu cầu xác thực tài khoản (Unauthenticated user)[cite: 9].

## 3. Hậu điều kiện (Post-conditions)
*   **Thành công:** Hệ thống trả về thông tin và trạng thái mới nhất của hồ sơ (Chờ duyệt, Đã duyệt, Từ chối). Hệ thống không thay đổi bất kỳ trạng thái dữ liệu nào trong CSDL.
*   **Thất bại:** Trả về thông báo lỗi hoặc không tìm thấy hồ sơ. Hệ thống giữ nguyên trạng thái.

## 4. Luồng sự kiện (Flow of Events)

### 4.1. Luồng cơ bản (Main Flow)
1.  **Bước 1 - Truy cập:** Người dùng truy cập chức năng “Tra cứu hồ sơ” tại trang chủ của Ứng dụng di động hoặc cổng Web (đã ẩn danh domain).
2.  **Bước 2 - Nhập thông tin:** Hệ thống hiển thị biểu mẫu yêu cầu nhập thông tin tra cứu[cite: 9]. Người dùng nhập chính xác 12 chữ số CCCD đã sử dụng khi đăng ký (và mã xác nhận captcha nếu tra cứu trên Web).
3.  **Bước 3 - Xử lý:** Người dùng nhấn nút “Tra cứu hồ sơ” (hoặc "Tra cứu"). Hệ thống kiểm tra tính hợp lệ của thông tin và truy vấn cơ sở dữ liệu.
4.  **Bước 4 - Hiển thị kết quả:** Hệ thống hiển thị trang “Kết quả tra cứu hồ sơ” bao gồm 6 trường thông tin cơ bản: Họ tên (đã che một phần), Số CCCD (đã che một phần, VD: 079***456), Bến xe nhận thẻ, Trạng thái hồ sơ, Lý do từ chối (nếu có) và Thời gian cập nhật.

### 4.2. Luồng thay thế (Alternative Flows)
*   **4.2.1. Xử lý hồ sơ bị từ chối:** 
    *   Nếu hồ sơ ở trạng thái “Từ chối”, hệ thống sẽ hiển thị chi tiết nguyên nhân từ chối do cán bộ thẩm định ghi nhận ngay trên màn hình kết quả.
    *   Người dùng xem lý do và có thể nhấn nút “Nộp lại hồ sơ”. Hệ thống sẽ chuyển hướng người dùng trở lại biểu mẫu đăng ký để thực hiện làm lại hồ sơ mới.

### 4.3. Luồng ngoại lệ (Exception Flows)
*   **4.3.1. Thông tin không hợp lệ:** Nếu số CCCD không đúng định dạng (thiếu số, chứa ký tự chữ), hệ thống hiển thị thông báo lỗi và yêu cầu nhập lại.
*   **4.3.2. Không tìm thấy hồ sơ:** Nếu không có bản ghi nào khớp với số CCCD được cung cấp, hệ thống hiển thị thông báo “Không tìm thấy hồ sơ” và cho phép thử lại.
*   **4.3.3. Lỗi hệ thống:** Nếu gián đoạn kết nối CSDL, hệ thống thông báo “Không thể thực hiện tra cứu, vui lòng thử lại sau”.

## 5. Điểm mở rộng (Extension Points)
Theo sơ đồ Use Case cung cấp, luồng "Nhập thông tin tra cứu" có một điểm mở rộng chính:
*   `Nhập CCCD` (<<extend>>): Là phương thức định danh bắt buộc được mở rộng để phục vụ việc truy vấn dữ liệu từ luồng thông tin tra cứu[cite: 9].

## 6. Yêu cầu đặc biệt (Special Requirements)
*   **Quy tắc ẩn danh (Data Masking - BR-TRC-04):** Để đảm bảo an toàn thông tin PII khi tra cứu công khai, hệ thống tuyệt đối không hiển thị ảnh chân dung, ảnh thẻ CCCD, địa chỉ chi tiết và tệp đính kèm. Tên và số CCCD phải được ẩn đi một phần (Masking).
*   **Bảo mật & Chống dò quét (NFR-SEC-01):** API tra cứu công khai phải tích hợp cơ chế Rate Limit (Giới hạn tỷ lệ: ví dụ 10 requests/phút/IP) để chống lại các cuộc tấn công Brute-force hoặc rà quét dữ liệu tự động.
*   **Hiệu năng (NFR-PERF-03):** Thời gian phản hồi cho mỗi lượt tra cứu API không vượt quá 2.0 giây.
