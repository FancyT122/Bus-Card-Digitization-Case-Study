# Phân tích Quy trình TO-BE 01: Tiếp nhận và Khởi tạo hồ sơ số 

*(Bạn nhớ upload file ảnh tobe01.jpg lên cùng thư mục trên GitHub, sau đó thay link ảnh vào dòng bên dưới nhé)*
![Sơ đồ TO-BE 01 - Tiếp nhận hồ sơ số](link_hinh_anh_cua_ban)

**1. Bối cảnh luồng nghiệp vụ:**
Đây là luồng tương tác trực tiếp dành cho công dân hoặc nhân viên hỗ trợ tại quầy thông qua Ứng dụng di động hoặc Cổng Web công khai. Luồng này được thiết kế nhằm số hóa và hợp nhất hai công đoạn rời rạc, thủ công của quy trình cũ là "Viết đơn giấy" (AS-IS 01) và "Chụp ảnh qua điện thoại cá nhân" (AS-IS 02).

**2. Cơ chế hoạt động và tính năng cốt lõi:**
*   **Tự động hóa bóc tách dữ liệu:** Ứng dụng công nghệ quét mã QR trên CCCD gắn chip để tự động giải mã và điền các trường thông tin cá nhân (Số định danh, Họ tên, Ngày sinh, Địa chỉ thường trú...) với thời gian phản hồi cực nhanh (≤ 2 giây).
*   **Xử lý địa chỉ linh hoạt và Chuẩn hóa:** Hỗ trợ tùy chọn "Nơi ở hiện tại giống/khác địa chỉ CCCD". Tích hợp danh mục đơn vị hành chính thông minh (Searchable Dropdown) giúp người dân tra cứu và chọn nhanh Phường/Xã mới nhất, tự động chuẩn hóa dữ liệu sau các đợt sáp nhập.
*   **Kiểm soát chất lượng ảnh tức thì:** Người dùng chụp ảnh chân dung và giấy tờ minh chứng trực tiếp trên nền tảng. Hệ thống cung cấp ngay công cụ cắt, thu phóng, xoay ảnh và tự động nén dung lượng (≤ 500KB) trước khi mã hóa đẩy thẳng lên máy chủ, loại bỏ rủi ro chất lượng ảnh kém.
*   **Kiểm soát toàn vẹn dữ liệu:** Thuật toán tự động đối soát toàn hệ thống để chặn đứng việc nộp trùng hồ sơ. Ngay khi nộp thành công, hệ thống tự động sinh Case ID duy nhất để quản lý.

**3. Giá trị nghiệp vụ mang lại:**
*   **Tối ưu hóa hành trình người dùng (User Journey):** Rút ngắn tổng thời gian đăng ký và chụp ảnh từ 10-15 phút xuống chỉ còn khoảng 3 phút/hồ sơ.
*   **Triệt tiêu lỗi nhập liệu:** Loại bỏ 100% rủi ro sai lỗi chính tả thông tin cá nhân nhờ bóc tách trực tiếp từ mã định danh chuẩn quốc gia.
*   **Bảo mật dữ liệu cá nhân:** Hồ sơ và hình ảnh được đẩy thẳng vào cơ sở dữ liệu mã hóa của hệ thống trung tâm, triệt tiêu nguy cơ rò rỉ khi sử dụng các kênh trung gian hoặc thiết bị cá nhân.
