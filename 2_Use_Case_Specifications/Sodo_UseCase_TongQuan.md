# Phân tích Sơ đồ Use Case Tổng quan Toàn hệ thống

*(Bạn nhớ upload file ảnh uc 00.png lên cùng thư mục trên GitHub, sau đó thay link ảnh vào dòng bên dưới nhé)*
![Sơ đồ Use Case Tổng quan](link_hinh_anh_cua_ban)

**1. Phạm vi hệ thống:**
Hệ thống quản lý đăng ký và cấp thẻ điện tử được thiết kế để phục vụ tương tác đa nền tảng, xoay quanh 03 nhóm tác nhân chính với các mức độ phân quyền độc lập nhằm đảm bảo an toàn thông tin và tính chuyên biệt hóa trong khâu vận hành.

**2. Phân tích chức năng theo tác nhân:**

*   **Tác nhân 1: Người dùng không đăng nhập (Công dân / Nhân viên hỗ trợ tại quầy)**
    *   **Quyền hạn:** Không yêu cầu tài khoản xác thực.
    *   **Nhiệm vụ:** Tương tác với cổng Front-end (Web Public/Mobile App) để thực hiện 2 Use Case cốt lõi: **Đăng ký cấp thẻ** (tạo mới hồ sơ chờ duyệt) và **Tra cứu hồ sơ** (kiểm tra trạng thái thông qua Số định danh). 
    *   *Lưu ý bảo mật:* Luồng tra cứu được áp dụng Data Masking để ẩn các thông tin nhạy cảm của người dân.

*   **Tác nhân 2: Quản lý duyệt thẻ**
    *   **Quyền hạn:** Tài khoản nội bộ được cấp quyền Reviewer.
    *   **Nhiệm vụ:** Tham gia vào các luồng nghiệp vụ xương sống của hệ thống qua cổng Web Admin, bao gồm: **Thẩm định hồ sơ** (kiểm tra, đối chiếu ảnh, duyệt/từ chối) và **Quản lý hồ sơ đăng ký, xuất dữ liệu in** (gom lô hồ sơ, đóng gói dữ liệu xuất xưởng in.

*   **Tác nhân 3: Quản trị viên**
    *   **Quyền hạn:** Tài khoản cấp cao nhất (ROLE_ADMIN).
    *   **Nhiệm vụ:** Đảm nhận việc duy trì vận hành toàn bộ hệ thống thông qua các chức năng **Quản lý tài khoản** (tạo mới, khóa, đặt lại mật khẩu, phân quyền) và **Quản lý danh mục** (hành chính, đối tượng ưu tiên).

**3. Giá trị nghiệp vụ trong thiết kế:**
*   **Tách biệt logic:** Việc phân tách rõ ràng luồng người dùng công khai và luồng nội bộ giúp hệ thống dễ dàng mở rộng quy mô và bảo trì sau này mà không ảnh hưởng chéo.
*   **Bảo mật chặt chẽ:** Đảm bảo 100% các API xử lý dữ liệu hồ sơ và xuất danh sách in đều phải được xác thực và phân quyền đúng vai trò cán bộ nghiệp vụ.
