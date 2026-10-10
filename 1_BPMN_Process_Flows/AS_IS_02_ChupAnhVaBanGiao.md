# Phân tích Quy trình AS-IS 02: Chụp ảnh minh chứng và truyền tải dữ liệu

*(Bạn nhớ upload file ảnh as02.jpg lên cùng thư mục trên GitHub, sau đó thay link ảnh vào dòng bên dưới nhé)*
![Sơ đồ AS-IS 02 - Chụp ảnh và bàn giao hồ sơ](link_hinh_anh_cua_ban)

**1. Bối cảnh luồng nghiệp vụ:**
Sau khi hoàn tất đơn giấy, công dân di chuyển sang vị trí chụp ảnh. Nhân viên sử dụng điện thoại di động cá nhân để chụp 3 loại tệp: ảnh chân dung (3:4), mặt trước/sau CCCD và giấy tờ ưu tiên (nếu có). Sau khi dùng mắt thường kiểm tra độ rõ nét, ảnh được gom lại và gửi qua kênh trung gian sang máy tính bàn tại bến xe để lưu vào các thư mục cục bộ. Hồ sơ giấy được đóng túi chờ luân chuyển vật lý về văn phòng K.

**2. Các điểm nghẽn cốt lõi:**
*   **Phân mảnh luồng dữ liệu & Suy giảm chất lượng in:** Việc thiết bị chụp hoàn toàn tách rời với hệ thống quản lý khiến dữ liệu bị phân mảnh. Việc gửi ảnh qua trung gian làm file bị nén tự động, khiến chất lượng ảnh chân dung giảm sút nghiêm trọng, ảnh hưởng trực tiếp đến chất lượng phôi thẻ nhựa khi in ấn.
*   **Rủi ro nhầm lẫn dữ liệu:** Gom hàng trăm tệp ảnh thủ công mỗi ngày, tạo folder cục bộ trên ổ cứng máy tính cá nhân tốn rất nhiều thời gian và tiềm ẩn rủi ro cực cao về việc gắn nhầm ảnh của người này sang hồ sơ người khác.
*   **Data Privacy/PII:** Sử dụng thiết bị di động cá nhân và kênh trung gian để truyền tải hình ảnh CCCD, giấy tờ ưu tiên của người dân vi phạm các quy tắc bảo mật dữ liệu cá nhân.

**3. Định hướng giải pháp số hóa (TO-BE):**
*   **Thu nhận ảnh trực tiếp:** Tích hợp tính năng chụp ảnh ngay trên ứng dụng nghiệp vụ, loại bỏ hoàn toàn các kênh trung gian.
*   **Tự động hóa xử lý ảnh:** Ứng dụng tích hợp công cụ tự động căn chỉnh tỷ lệ 3:4, tối ưu dung lượng (≤ 500KB) và upload mã hóa trực tiếp lên máy chủ trung tâm.
*   **Liên kết dữ liệu nguyên khối:** Mỗi file ảnh chụp xong được hệ thống tự động gắn (mapping) và đổi tên khớp 100% với Case ID, triệt tiêu hoàn toàn rủi ro nhầm lẫn.
