# Phân tích Quy trình AS-IS 05: Tra cứu và Bàn giao thẻ tại quầy

*(Bạn nhớ upload file ảnh as-05.jpg lên cùng thư mục trên GitHub, sau đó thay link ảnh vào dòng bên dưới nhé)*
![Sơ đồ AS-IS 05 - Tra cứu và trả thẻ](link_hinh_anh_cua_ban)

**1. Bối cảnh luồng nghiệp vụ:**
Đây là công đoạn cuối cùng của quy trình cấp thẻ. Khi người dân mang giấy hẹn/giấy tờ tùy thân đến bến xe để nhận thẻ, nhân viên tại quầy phải thực hiện quy trình tra cứu hai tầng:
*   **Tầng 1 (Tra cứu số):** Nhập thông tin lên hệ thống website tra cứu nội bộ để kiểm tra trạng thái thẻ đã được duyệt và in hay chưa.
*   **Tầng 2 (Tra cứu vật lý):** Nếu hệ thống báo đã có, nhân viên tiến hành lục tìm thủ công thẻ nhựa trong các khay/hộp lưu trữ được sắp xếp theo bảng chữ cái A-Z.
Sau khi tìm thấy, nhân viên đối chiếu với giấy tờ gốc và bàn giao thẻ cho người dân.

**2. Các điểm nghẽn cốt lõi:**
*   **Sự cố bất đồng bộ vật lý (Thẻ ảo):** Rủi ro lớn nhất nằm ở việc hệ thống số (Website) báo thẻ "Đã duyệt/Đã in", nhưng thực tế phôi thẻ bị thất lạc trong khâu luân chuyển từ xưởng in về bến xe, dẫn đến việc nhân viên không tìm thấy thẻ trong hộp. Điều này gây bức xúc lớn cho người dân khi họ đến nơi nhưng phải đi về tay không.
*   **Nút thắt tra cứu thủ công:** Việc lật tìm từng thẻ nhựa bằng tay trong hộp lưu trữ A-Z cực kỳ kém hiệu quả và mất thời gian, đặc biệt trong các khung giờ cao điểm.
*   **Lỗi sai lệch phôi in:** Do di chứng của việc nhập liệu kép thủ công ở AS-IS 01, thông tin trên phôi thẻ nhựa khi giao về bến đôi khi bị sai, buộc nhân viên phải lập biên bản hủy thẻ và bắt đầu lại chu trình từ đầu.

**3. Định hướng giải pháp số hóa (TO-BE):**
*   **Tra cứu công khai:** Cung cấp API/Cổng tra cứu Web/App cho phép công dân chủ động kiểm tra trạng thái hồ sơ bằng số CCCD ngay tại nhà, giảm thiểu tình trạng đến bến xe nhưng thẻ chưa in xong.
*   **Quản lý vòng đời lô thẻ:** Bổ sung trạng thái `DA_XUAT` để đối soát chặt chẽ quá trình bàn giao lô thẻ vật lý từ xưởng in về bến, triệt tiêu hiện tượng "thẻ ảo".
*   **Đảm bảo chất lượng dữ liệu in:** Kế thừa dữ liệu 100% chính xác từ việc bóc tách mã QR CCCD ở bước đầu vào, kết hợp thuật toán chuẩn hóa dữ liệu in (≤ 20 ký tự), đảm bảo thẻ vật lý phát hành không còn sai sót.
