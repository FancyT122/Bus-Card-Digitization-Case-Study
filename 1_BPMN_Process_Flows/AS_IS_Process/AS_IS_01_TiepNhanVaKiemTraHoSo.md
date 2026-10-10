# Phân tích Quy trình AS-IS 01: Tiếp nhận đơn giấy và kiểm tra hồ sơ tại quầy

*(Bạn nhớ upload file ảnh as01.jpg lên cùng thư mục trên GitHub, sau đó thay link ảnh vào dòng bên dưới nhé)*
![Sơ đồ AS-IS 01 - Tiếp nhận và kiểm tra hồ sơ](link_hinh_anh_cua_ban)

**1. Bối cảnh luồng nghiệp vụ:**
Đây là công đoạn tương tác tuyến đầu giữa công dân và cán bộ tại điểm tiếp nhận. Do đặc thù đối tượng thụ hưởng chính sách là người cao tuổi, người khuyết tật thường gặp trở ngại về vận động và thị lực, cán bộ tiếp nhận phải trực tiếp cầm bút viết tay toàn bộ thông tin cá nhân hộ người dân vào tờ khai. Sau đó, cán bộ thực hiện đối chiếu giấy tờ tùy thân bằng mắt thường và viết phiếu hẹn trả thẻ thủ công.

**2. Các điểm nghẽn cốt lõi:**
*   **Nút thắt cổ chai do tra cứu địa chỉ:** TP.HCM liên tục biến động sáp nhập địa giới hành chính. Khi người dân khai báo phường/khu phố cũ, cán bộ phải tạm dừng quy trình để tra cứu thủ công danh mục phường mới, dẫn đến ùn tắc cục bộ trầm trọng tại quầy.
*   **Xác thực thủ công & Trải nghiệm người dùng kém:** Việc kiểm tra chéo giấy tờ gốc hoàn toàn bằng mắt thường tốn nhiều thời gian. Nếu phát hiện sai lệch hoặc thiếu minh chứng, người dân buộc phải đi về bổ sung, gây tâm lý mệt mỏi và bức xúc.
*   **Rủi ro thất lạc phiếu hẹn:** Thao tác viết tay, xé cuống phiếu giấy trao cho công dân rất dễ dẫn đến rách, mờ chữ hoặc thất lạc, gây khó khăn cho việc đối soát lúc trả thẻ.

**3. Định hướng giải pháp số hóa (TO-BE):**
*   **Không giấy tờ:** Ứng dụng công nghệ quét mã QR trên CCCD gắn chip để hệ thống tự động bóc tách và điền thông tin cá nhân trong vòng < 2 giây.
*   **Chuẩn hóa dữ liệu hành chính:** Tích hợp API danh mục đơn vị hành chính, tự động đối chiếu và ánh xạ địa chỉ thường trú từ dữ liệu cũ sang chuẩn mới nhất mà không cần cán bộ can thiệp.
*   **Số hóa quy trình định danh:** Tự động sinh Mã hồ sơ (Case ID) duy nhất lưu trực tiếp vào cơ sở dữ liệu thay vì phát hành cuống phiếu hẹn giấy.
