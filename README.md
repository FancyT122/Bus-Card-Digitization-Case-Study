<h1 align="center">Hệ Thống Số Hóa Cấp Phát Thẻ Xe Buýt (Case Study)</h1>

<p align="center">
  <i>Dự án nhằm giải quyết bài toán ách tắc trong quy trình cấp phát thẻ xe buýt miễn phí. Thay vì người dân phải nộp hồ sơ giấy để nhân viên nhập liệu lại một cách thủ công, hệ thống mới tự động hóa việc trích xuất dữ liệu và quản lý luồng phê duyệt tập trung.</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Process_Modeling-BPMN_2.0-F24E1E?style=for-the-badge&logo=bpmn" alt="BPMN" />
  <img src="https://img.shields.io/badge/Tools-Draw.io%20%7C%20Figma-FF7262?style=for-the-badge&logo=figma" alt="Tools" />
  <img src="https://img.shields.io/badge/Methodology-Agile%2FSCRUM-0052CC?style=for-the-badge&logo=jira" alt="Agile" />
</p>

---

## 📖 1. Tổng quan dự án
* **Bối cảnh:** Quy trình cấp phát thẻ xe buýt miễn phí trước đây thực hiện hoàn toàn thủ công thông qua nhiều công đoạn giấy tờ, dẫn đến việc xử lý chậm, rườm rà và dễ sai sót dữ liệu.
* **Quy mô nhóm:** 39 thành viên (bao gồm BA, Dev Front-end, Dev Back-end và Tester).
* **Vai trò của tôi:** Business Analyst member.

**Hệ thống phục vụ 3 nhóm tác nhân chính:**
1. **Người dùng không đăng nhập (End-users):** Thực hiện đăng ký trực tuyến, sử dụng tính năng quét mã QR CCCD để tự động điền thông tin và tra cứu tiến độ hồ sơ.
2. **Quản lý duyệt thẻ:** Tham gia vào các nghiệp vụ cốt lõi gồm tiếp nhận, thẩm định hồ sơ, quản lý danh sách hồ sơ đăng ký và xuất dữ liệu in thẻ.
3. **Quản trị viên (Admin):** Đảm nhận chức năng quản lý tài khoản, phân quyền và cấu hình danh mục để duy trì vận hành toàn bộ hệ thống.

---

## 🎯 2. Công việc thực hiện của tôi
* **Mô hình hóa quy trình (BPMN):** Khảo sát nghiệp vụ thực tế, phân tích và vẽ sơ đồ luồng logic As-Is và To-Be. Đề xuất các cải tiến quan trọng như quét mã QR trên CCCD để tự động trích xuất thông tin, loại bỏ bước nộp hồ sơ giấy và luân chuyển USB thủ công.
* **Viết tài liệu Hướng dẫn sử dụng:** Đóng vai trò lead trong việc xây dựng tài liệu HDSD cho các nhóm người dùng. Xác định rõ hành trình (User journey) để đảm bảo hệ thống dễ tiếp cận nhất, đặc biệt với nhóm đối tượng người cao tuổi.
* **Phối hợp làm việc nhóm:** Làm việc cùng nhóm 39 người để rà soát và cập nhật tài liệu Đặc tả Use Case. Đóng vai trò cầu nối giúp thống nhất yêu cầu nghiệp vụ giữa nhóm Kỹ thuật (Dev/Tester) và thực tiễn vận hành tại bến xe.

---

## 🚀 3. Cải tiến Nghiệp vụ Nổi bật 
*   **Tự động hóa nhập liệu:** Ứng dụng quét mã QR trên CCCD giúp bóc tách chính xác thông tin nhân khẩu học, giảm thời gian nhập liệu từ 5 phút xuống dưới 1 phút/hồ sơ.
*   **Chuẩn hóa luồng quy trình (BPMN):** Loại bỏ hoàn toàn các bước trung gian thừa (viết tay, gửi ảnh qua Zalo, chép USB) trong khâu luân chuyển hồ sơ giữa Bến xe buýt và trụ sở Trung tâm.
*   **Single Source of Truth:** Hệ thống tài liệu (Use Case, BRD) đồng nhất giúp đội ngũ phát triển nắm bắt chính xác yêu cầu, xóa bỏ tình trạng bất đồng bộ dữ liệu.

---

## 🚧 4. Phân Tích Hiện Trạng & Điểm Nghẽn (AS-IS Process)

Qua khảo sát thực địa, quy trình thủ công hiện tại được mô hình hóa thành 1 sơ đồ tổng quan (00) và 5 sơ đồ chu trình con (01 đến 05). 

*(Lưu ý: Để tuân thủ bảo mật nội bộ, tài liệu này chỉ trình bày luồng tổng quan và các luồng tương tác trực tiếp tại quầy gồm 00, 01, 02, 05. Các luồng 03 - nhập liệu excel và 04 - xét duyệt hộp đen được ẩn đi).*

### AS-IS 00: Tổng quan quy trình hiện tại
Mô tả bức tranh toàn cảnh về luồng luân chuyển hồ sơ vật lý giữa các bên liên quan: từ lúc người dân nộp đơn trực tiếp tại bến xe, qua các khâu xử lý nội bộ, chuyển xưởng in gia công, đến khi nhận thẻ cứng tại quầy.

<p align="center">
  
<img width="16384" height="7048" alt="as00" src="https://github.com/user-attachments/assets/182c49ed-077b-433b-831b-601a5f49fc33" />
</p>

### AS-IS 01: Phân luồng, tiếp nhận kê khai và viết tay đơn giấy
*   **Hiện trạng:** Cán bộ tiếp nhận phải trực tiếp cầm bút viết tay toàn bộ thông tin cá nhân hộ người dân vào tờ khai đơn giấy (do đa phần là người cao tuổi, khuyết tật) và viết tay giấy hẹn trả thẻ.
*   **Điểm nghẽn (Pain points):** Việc biến động địa giới hành chính (sáp nhập phường/quận) khiến người dân khai báo địa chỉ cũ. Cán bộ phải dừng thao tác để tra cứu thủ công và ánh xạ (mapping) sang phường/quận mới, gây ùn tắc cục bộ kéo dài. Nhập liệu kép bằng tay gây mệt mỏi và rủi ro sai sót thông tin rất cao.

<p align="center">
  <img width="16384" height="9333" alt="as-01" src="https://github.com/user-attachments/assets/8e20392a-f841-4f22-b3b1-5e81dd2d6ea5" />

</p>

### AS-IS 02: Chụp ảnh và truyền dữ liệu phân tán qua Zalo/USB
*   **Hiện trạng:** Cán bộ/Tình nguyện viên dùng điện thoại cá nhân chụp 03 tệp ảnh (chân dung, CCCD mặt trước/sau, giấy tờ ưu tiên). Sau đó, gom ảnh và gửi trung gian qua Zalo hoặc cắm cáp USB để cóp vào máy tính bàn.
*   **Điểm nghẽn (Pain points):** 
    *   Nguy cơ rò rỉ dữ liệu cá nhân (PII) cực kỳ nghiêm trọng khi lưu trữ trên thiết bị cá nhân và truyền qua mạng xã hội.
    *   Chất lượng ảnh suy giảm (do Zalo tự nén ảnh nếu không chọn HD).
    *   Việc quản lý file phân tán bằng cách tạo thư mục cục bộ dễ dẫn đến nhầm lẫn tên file ảnh giữa các công dân, gây khó khăn cho khâu đối chiếu.

<p align="center">
 <img width="9776" height="5340" alt="as02" src="https://github.com/user-attachments/assets/cbae8dae-1486-4d3f-8f51-f5270040510f" />

</p>

### AS-IS 05: Tra cứu hai tầng và bàn giao thẻ thủ công
*   **Hiện trạng:** Khi công dân mang phiếu hẹn đến, cán bộ thực hiện tra cứu 2 tầng: (1) Nhập mã lên website nội bộ để check trạng thái; (2) Trực tiếp dùng tay lật tìm thẻ vật lý trong các khay/hộp xếp theo bảng chữ cái A-Z và giới tính.
*   **Điểm nghẽn (Pain points):** 
    *   Hiện tượng "thẻ ảo": Website báo thẻ đã duyệt in nhưng thực tế trong hộp không tìm thấy do thất lạc trong khâu vận chuyển từ xưởng in về bến xe.
    *   Thông tin in trên phôi thẻ bị dập sai lỗi chính tả so với giấy tờ gốc (hệ quả từ việc nhập liệu thủ công nhiều bước), buộc phải lập biên bản hủy thẻ và làm lại quy trình từ đầu.

<p align="center">
  <img width="11092" height="5428" alt="as-05" src="https://github.com/user-attachments/assets/1838ce41-e373-4122-972c-596d946bbfa3" />

</p>

---

## 💡 5. Đề Xuất Giải Pháp Số Hóa (TO-BE Process)

Hệ thống TO-BE được tái thiết kế theo hướng số hóa toàn diện, bao gồm 1 sơ đồ tổng quan (00) và 2 chu trình con (01, 02). 
*(Lưu ý: Chu trình TO-BE-02 là luồng dành riêng cho Quản lý/Thẩm định nên được ẩn đi nhằm tuân thủ NDA).*

### TO-BE 00: Tổng quan End-to-End quy trình số hóa
*   **Giải pháp:** Xây dựng kiến trúc luồng dữ liệu mới, kết nối xuyên suốt từ Người dân (qua App/Website) đến Nhân viên duyệt thẻ và Đơn vị in ấn.
*   **Giá trị mang lại:** 
    *   Dữ liệu hồ sơ truyền tải tức thời (Real-time), loại bỏ hoàn toàn việc đóng gói, vận chuyển đơn giấy và USB.
    *   Bảo đảm tính toàn vẹn dữ liệu (Single Source of Truth) giữa các bộ phận, mọi thao tác đều ghi nhận trên một cơ sở dữ liệu tập trung, xóa bỏ tình trạng "thẻ ảo".

<p align="center">
 <img width="5812" height="4696" alt="tobe 00" src="https://github.com/user-attachments/assets/416e0fbd-1318-45b3-8693-6218df8fec49" />

</p>

### TO-BE 01: Tự động hóa khâu Tiếp nhận và Xử lý hồ sơ
*   **Giải pháp:** Thay thế việc viết đơn giấy bằng biểu mẫu điện tử (E-form) tích hợp tính năng quét mã QR CCCD. Hình ảnh chân dung/giấy tờ được mã hóa và tải trực tiếp vào hệ thống cơ sở dữ liệu.
*   **Giá trị mang lại:** 
    *   Tự động giải mã và điền (Auto-fill) thông tin nhân khẩu học, giải quyết triệt để lỗi sai lệch địa chỉ hành chính.
    *   Giảm thời gian tiếp nhận từ 5 phút xuống dưới 1 phút/hồ sơ.
    *   Triệt tiêu hoàn toàn rủi ro bảo mật PII phát sinh từ các ứng dụng truyền tải trung gian.

<p align="center">
  <img width="16384" height="3760" alt="tobe01" src="https://github.com/user-attachments/assets/e6d2bf44-99ca-437b-bfb3-cf23960c6b73" />

</p>

---

## ⚙️ 6. Đặc Tả Use Case (Use Case Specifications)
<img width="906" height="526" alt="uc 00" src="https://github.com/user-attachments/assets/d20fa385-dfcc-4645-82fc-7ab3c21aaf91" />


Hệ thống bao gồm tổng cộng 5 Use Case cốt lõi. Nhằm tuân thủ quy định bảo mật thông tin nội bộ (NDA), 3 Use Case thuộc luồng Quản lý/Thẩm định được ẩn đi. Dưới đây là đặc tả chi tiết 2 Use Case tương tác trực tiếp với Người dùng không đăng nhập (End-users).


### 📌 6.1. UC_01: Đăng ký cấp thẻ xe buýt

<p align="center">
  <img width="907" height="807" alt="uc01" src="https://github.com/user-attachments/assets/0beab09d-2b06-4476-8148-f031b612bffe" />

</p>

**6.1.1. Mô tả tóm tắt (Summary)**
Cho phép người dân hoặc nhân viên hỗ trợ tại quầy đăng ký cấp thẻ qua ứng dụng hoặc cổng Web công khai mà không cần đăng nhập. Chức năng hỗ trợ quét mã QR trên CCCD để tự động trích xuất và điền thông tin nhằm tối ưu thời gian nhập liệu.

**6.1.2. Luồng sự kiện (Flow of events)**

**6.1.2.1. Luồng cơ bản (Main flow)**
1. Người dùng truy cập ứng dụng/web và chọn đăng ký cấp thẻ.
2. Người dùng chọn chức năng Quét/Chụp QR CCCD.
3. Hệ thống bóc tách thông tin từ mã QR và tự động điền các trường thông tin cá nhân.
4. Hệ thống yêu cầu khai báo địa chỉ hiện tại; người dùng xác nhận địa chỉ hiện tại giống trên CCCD để hệ thống tự động sao chép.
5. Hệ thống tính tuổi theo ngày sinh và tự động đề xuất nhóm đối tượng phù hợp.
6. Người dùng nhập số điện thoại liên hệ và chọn điểm nhận thẻ.
7. Người dùng thực hiện chụp/tải ảnh chân dung và ảnh CCCD 2 mặt.
8. Người dùng kiểm tra thông tin hồ sơ, xác nhận và nộp hồ sơ.
9. Hệ thống kiểm tra chống trùng lặp số CCCD, sinh mã Case ID duy nhất và lưu hồ sơ với trạng thái `DANG_CHO_DUYET`.

**6.1.2.2. Luồng thay thế (Alternative flow)**
*   **A1 (Không quét được QR):** Nếu hệ thống không đọc được mã QR (ảnh mờ, sai vùng quét), hệ thống cho phép người dùng mở rộng sang luồng Nhập thủ công.
*   **A2 (Địa chỉ hiện tại khác CCCD):** Nếu nơi ở hiện tại khác địa chỉ trên CCCD, hệ thống yêu cầu nhập địa chỉ chi tiết và tự động chuẩn hóa địa chỉ hành chính.
*   **A3 (Trùng lặp hồ sơ):** Nếu số CCCD đã tồn tại hồ sơ đang xử lý, hệ thống hiển thị cảnh báo và chặn tạo mới. Hệ thống chỉ cho phép tạo mới nếu hồ sơ cũ đã ở trạng thái TỪ CHỐI.
*   **A4 (Đăng ký cho đối tượng đặc biệt):** Nếu đăng ký cho trẻ em dưới 6 tuổi, hệ thống yêu cầu nhập thêm thông tin người giám hộ và tải giấy tờ minh chứng bắt buộc.

**6.1.3. Yêu cầu đặc biệt (Special requirement)**
*   `BR-01`: Phải parse (giải mã) chính xác chuỗi cấu trúc dữ liệu từ mã QR CCCD của Bộ Công An.
*   `NFR-PERF-01`: Thời gian phản hồi quét QR và bóc tách dữ liệu phải `<= 2 giây`.

**6.1.4. Tiền điều kiện (Pre-condition)**
Hệ thống đăng ký đang hoạt động. Người dùng truy cập thiết bị có hỗ trợ camera và đã cấp quyền truy cập camera cho trình duyệt/ứng dụng.

**6.1.5. Hậu điều kiện (Post-condition)**
Hệ thống tạo thành công hồ sơ mới với mã Case ID duy nhất. Thông tin định danh, hình ảnh chân dung và giấy tờ được lưu trữ an toàn; hồ sơ chuyển sang trạng thái chờ thẩm định.

**6.1.6. Điểm mở rộng (Extension Points)**
*   **Nhập thủ công:** Khởi chạy từ điểm "Quét/Chụp QR CCCD" trong trường hợp thiết bị lỗi camera hoặc thẻ xước hỏng không thể quét.
*   **Tải giấy tờ minh chứng bắt buộc & Nhập thông tin người giám hộ:** Khởi chạy từ điểm "Chọn đối tượng" dựa trên Business Rules về độ tuổi hoặc đối tượng ưu tiên.

---

### 📌 6.2. UC_02: Tra cứu hồ sơ

<p align="center">
  <img width="906" height="420" alt="uc02" src="https://github.com/user-attachments/assets/0825a2f5-2a44-4261-8373-8c70d7759466" />

</p>

**6.2.1. Mô tả tóm tắt (Summary)**
Cho phép người dùng không cần đăng nhập tra cứu thông tin và trạng thái xử lý thực tế của hồ sơ cấp thẻ bằng cách nhập số CCCD.

**6.2.2. Luồng sự kiện (Flow of events)**

**6.2.2.1. Luồng cơ bản (Main flow)**
1. Người dùng truy cập chức năng Tra cứu hồ sơ.
2. Hệ thống hiển thị giao diện và yêu cầu nhập thông tin tra cứu.
3. Người dùng nhập số CCCD để tra cứu.
4. Hệ thống kiểm tra tính hợp lệ của CCCD và truy vấn dữ liệu hồ sơ tương ứng.
5. Hệ thống hiển thị kết quả bao gồm: Họ tên, Số CCCD (đã che khuất một phần), Điểm nhận thẻ, Trạng thái hồ sơ, Lý do từ chối (nếu có) và Thời gian cập nhật mới nhất.

**6.2.2.2. Luồng thay thế (Alternative flow)**
*   **A1 (Thông tin không hợp lệ):** Nếu số CCCD không đúng định dạng (thiếu số, sai cấu trúc), hệ thống báo lỗi và yêu cầu nhập lại thông tin.
*   **A2 (Không tìm thấy hồ sơ):** Nếu số CCCD không khớp với dữ liệu bất kỳ hồ sơ nào trên hệ thống, màn hình hiển thị thông báo "Không tìm thấy hồ sơ" và cho phép tra cứu lại.

**6.2.3. Yêu cầu đặc biệt (Special requirement)**
*   `BR-TRC-04` (Tối thiểu hóa dữ liệu / Data Minimization): Tuyệt đối không hiển thị ảnh chân dung, ảnh thẻ CCCD và địa chỉ chi tiết ra màn hình kết quả để bảo vệ quyền riêng tư.
*   `NFR-SEC-01` (Bảo mật số liệu / Data Masking): Số CCCD hiển thị phải được làm mờ (Ví dụ: `079***456`) và hệ thống phải giới hạn số lượt tra cứu để chống tấn công cào dữ liệu (Rate Limit: 10 req/phút/IP).

**6.2.4. Tiền điều kiện (Pre-condition)**
Hệ thống truy vấn đang hoạt động ổn định. Người dùng nắm rõ số CCCD hợp lệ đã dùng để đăng ký hồ sơ.

**6.2.5. Hậu điều kiện (Post-condition)**
Hệ thống trả về chính xác thông tin và trạng thái cập nhật mới nhất của hồ sơ mà không làm lộ lọt dữ liệu nhạy cảm của cá nhân.

**6.2.6. Điểm mở rộng (Extension Points)**
*Không có.*

---

*Lưu ý: Vui lòng xem thêm tài liệu Hướng dẫn sử dụng (User Manuals) định dạng PDF trong thư mục đính kèm của Repository.*
