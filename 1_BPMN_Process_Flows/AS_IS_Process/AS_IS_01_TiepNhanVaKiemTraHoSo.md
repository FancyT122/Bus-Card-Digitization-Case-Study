# Phân tích Quy trình AS-IS 01: Tiếp nhận đơn giấy, chụp ảnh và kiểm tra hồ sơ tại quầy
<p align="center">
  <img width="2428" height="1053" alt="AS_IS_01" src="https://github.com/user-attachments/assets/329fdd84-8f57-4f14-9391-ae5abc3bbefe" />
  <br>
  <i>Sơ đồ AS-IS 01: Quy trình tiếp nhận, chụp ảnh và kiểm tra hồ sơ tại quầy</i>
</p>

**1. Bối cảnh luồng nghiệp vụ:**
Quy trình này mô tả toàn bộ chuỗi tương tác tuyến đầu giữa Người đăng ký thẻ và Trung tâm giao thông công cộng. Do đặc thù người dân thường là người cao tuổi hoặc khuyết tật, quy trình đòi hỏi sự can thiệp thủ công rất lớn từ 3 bộ phận:
*   **Nhân viên tiếp nhận:** Xác nhận sơ bộ đối tượng, trực tiếp hỗ trợ viết tay thông tin vào phiếu đăng ký và phải đối chiếu, cập nhật thủ công nếu địa chỉ của người dân nằm trong diện sáp nhập[cite: 5].
*   **Nhân viên chụp ảnh:** Sử dụng thiết bị rời để chụp ảnh chân dung và giấy tờ minh chứng, sau đó tự kiểm tra độ nét bằng mắt thường[cite: 5].
*   **Nhân viên xác nhận:** Đối chiếu thông tin trên phiếu giấy với giấy tờ gốc[cite: 5]. Nếu có sai lệch, người dân phải quay lại bước bổ sung/chỉnh sửa; nếu khớp, nhân viên sẽ viết phiếu hẹn giấy và trả lại giấy tờ[cite: 5].

**2. Các điểm nghẽn cốt lõi:**
*   **Nút thắt cổ chai do tra cứu địa chỉ:** Việc TP.HCM liên tục biến động địa giới hành chính buộc nhân viên tiếp nhận phải kiểm tra và cập nhật địa chỉ thủ công, dẫn đến ùn tắc cục bộ trầm trọng tại quầy[cite: 5].
*   **Phân mảnh dữ liệu & Vi phạm bảo mật (PII):** Công đoạn chụp ảnh chân dung và giấy tờ minh chứng được thực hiện rời rạc, truyền tải qua kênh trung gian[cite: 5]. Điều này không chỉ làm giảm chất lượng ảnh in phôi thẻ, gây nguy cơ gắn nhầm ảnh người này sang hồ sơ người khác, mà còn vi phạm các quy tắc bảo mật dữ liệu cá nhân.
*   **Xác thực thủ công & Trải nghiệm người dùng kém:** Việc nhân viên xác nhận phải đối chiếu chéo phiếu giấy với giấy tờ gốc hoàn toàn bằng mắt thường rất mất thời gian[cite: 5]. Việc viết tay, xé cuống phiếu hẹn giấy trao cho công dân rất dễ dẫn đến rách, mờ chữ hoặc thất lạc.

**3. Định hướng giải pháp số hóa (TO-BE):**
*   **Không giấy tờ & Điền dữ liệu tự động:** Ứng dụng công công nghệ quét mã QR trên CCCD gắn chip để bóc tách thông tin cá nhân trong < 2 giây. Tự động hóa việc sinh Mã hồ sơ (Case ID) kỹ thuật số thay cho phiếu hẹn giấy.
*   **Chuẩn hóa dữ liệu hành chính:** Tích hợp API danh mục đơn vị hành chính, hệ thống tự động đối chiếu và ánh xạ địa chỉ thường trú từ dữ liệu cũ sang chuẩn mới nhất mà không cần cán bộ can thiệp.
*   **Thu nhận ảnh trực tiếp & Liên kết nguyên khối:** Tích hợp module chụp ảnh ngay trên ứng dụng nghiệp vụ tại quầy, có AI hỗ trợ kiểm tra độ lóa/mờ. Mỗi file ảnh chụp xong được hệ thống tự động gắn (mapping) khớp 100% với Case ID, triệt tiêu rủi ro nhầm lẫn hồ sơ và rò rỉ dữ liệu.
