# Phân tích Quy trình AS-IS 00: Tổng quan toàn trình cấp phát thẻ

*(Bạn nhớ upload file ảnh as00.jpg lên cùng thư mục trên GitHub, sau đó thay link ảnh vào dòng bên dưới nhé)*
![Sơ đồ AS-IS 00 - Tổng quan](link_hinh_anh_cua_ban)

**1. Bối cảnh luồng nghiệp vụ toàn trình:**
Quy trình cấp phát thẻ ưu tiên hiện tại đang diễn ra hoàn toàn thủ công qua 6 công đoạn tuần tự, liên quan đến nhiều địa điểm vật lý và luồng dữ liệu phân tán:
*   **Điểm tiếp nhận trực tiếp:** Phân luồng, viết tay tờ khai, kiểm tra hồ sơ giấy, viết giấy hẹn thủ công, chụp ảnh minh chứng và gom file ảnh gửi qua kênh trung gian.
*   **Văn phòng xử lý trung tâm:** Nhận túi hồ sơ vật lý, đối chiếu ảnh chụp, thực hiện nhập liệu kép từ giấy sang Excel, sau đó tiếp tục nhập lên hệ thống nội bộ.
*   **Thẩm định & Bàn giao:** Xét duyệt trên hệ thống, trích xuất dữ liệu chuyển xưởng in thẻ nhựa, sau đó vận chuyển thẻ vật lý về lại bến xe để tra cứu và bàn giao cho công dân.

**2. Các điểm nghẽn cốt lõi:**
*   **Nhập liệu kép & Rủi ro sai sót:** Toàn bộ quy trình phụ thuộc vào thao tác viết tay và gõ lại dữ liệu nhiều lần, dẫn đến tỷ lệ sai sót thông tin hành chính cao.
*   **Nguy cơ bảo mật dữ liệu:** Truyền tệp ảnh cá nhân qua các ứng dụng nhắn tin trung gian làm suy giảm chất lượng phôi in và tiềm ẩn rủi ro rò rỉ dữ liệu.
*   **Tổn thất thời gian:** Thời gian chờ đợi để nhận được thẻ kéo dài từ 7–14 ngày làm việc do độ trễ trong việc luân chuyển hồ sơ vật lý.

**3. Định hướng giải pháp số hóa (TO-BE):**
*   Triển khai hệ thống tiếp nhận đa nền tảng, ứng dụng công nghệ quét OCR từ mã QR trên thẻ Căn cước để tự động hóa khâu điền thông tin, loại bỏ 100% đơn từ giấy.
*   Đồng bộ dữ liệu và hình ảnh trực tiếp, mã hóa lên máy chủ, khai tử các kênh truyền file trung gian.
*   Tự động hóa luồng xét duyệt và đóng gói dữ liệu kết xuất in ấn theo lô.
