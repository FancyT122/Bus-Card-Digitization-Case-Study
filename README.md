<h1 align="center">Hệ Thống Số Hóa Cấp Phát Thẻ Xe Buýt (Case Study)</h1>

<p align="center">
  <i>Dự án nhằm giải quyết bài toán ách tắc trong quy trình cấp phát thẻ xe buýt miễn phí. Thay vì người dân phải nộp hồ sơ giấy để nhân viên nhập liệu lại một cách thủ công, hệ thống mới tự động hóa việc trích xuất dữ liệu và quản lý luồng phê duyệt tập trung.</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Process_Modeling-BPMN_2.0-F24E1E?style=for-the-badge&logo=bpmn" alt="BPMN" />
  <img src="https://img.shields.io/badge/Tools-Draw.io%20%7C%20Figma-FF7262?style=for-the-badge&logo=figma" alt="Tools" />
  <img src="https://img.shields.io/badge/Methodology-Agile%2FSCRUM-0052CC?style=for-the-badge&logo=jira" alt="Agile" />
</p>


## 1.Tổng quan dự án
* **Bối cảnh:** Quy trình cấp phát thẻ xe buýt miễn phí trước đây thực hiện hoàn toàn thủ công. Người dân phải nộp hồ sơ giấy, dẫn đến việc xử lý chậm, rườm rà và dễ sai sót dữ liệu.
* **Quy mô nhóm:** 39 thành viên (bao gồm BA, Dev Front-end, Dev Back-end và Tester).
* **Vai trò của tôi:** Business Analyst member.
Hệ thống phục vụ 4 nhóm người dùng:
1. **Người dùng không đăng nhập:** Đăng ký trực tuyến, quét mã QR CCCD để tự động điền thông tin, theo dõi trạng thái hồ sơ.
2. **Nhân viên xử lý:** Tiếp nhận và kiểm tra thông tin điện tử.
3. **Nhân viên thẩm định:** Phê duyệt hồ sơ dựa trên các rule nghiệp vụ được cấu hình sẵn.
4. **Admin:** Quản lý phân quyền và trích xuất báo cáo dữ liệu.

## 2. Công việc thực hiện của tôi
* **Mô hình hóa quy trình (BPMN):** Khảo sát và vẽ sơ đồ luồng logic As-Is và To-Be. Đề xuất áp dụng tính năng quét mã QR trên CCCD để tự động trích xuất thông tin, loại bỏ bước nộp hồ sơ giấy và nhập liệu thủ công.
* **Viết tài liệu Hướng dẫn sử dụng:** Đóng vai trò lead trong việc xây dựng tài liệu HDSD cho 4 nhóm (Admin, Nhân viên thẩm định, Nhân viên xử lý và Người dân). Xác định rõ hành trình người dùng (User journey) để đảm bảo hệ thống dễ sử dụng nhất.
* **Phối hợp làm việc nhóm:** Làm việc cùng nhóm 39 người để rà soát và cập nhật tài liệu. Đóng vai trò cầu nối giúp thống nhất yêu cầu nghiệp vụ giữa nhóm Kỹ thuật (Dev/Tester) và thực tế vận hành.


## 3. Cải tiến Nghiệp vụ Nổi bật 
*   **Tự động hóa nhập liệu:** Ứng dụng quét mã QR trên CCCD giúp trích xuất chính xác thông tin nhân khẩu học, giảm thời gian nhập liệu từ 5 phút xuống còn 5 giây/hồ sơ.
*   **Chuẩn hóa luồng quy trình (BPMN):** Loại bỏ hoàn toàn các bước trung gian thừa trong khâu luân chuyển hồ sơ giấy giữa các phòng ban.
*   **Single Source of Truth:** Hệ thống tài liệu (Use Case, BRD) đồng nhất giúp đội ngũ 39 thành viên (bao gồm 16 BAs, Dev, QA) nắm bắt chính xác yêu cầu phát triển.

## 4. Tài liệu minh chứng 
*(Tài liệu đã được ẩn danh để bảo mật thông tin nội bộ)*
1. `01_Process_Modeling`: Sơ đồ luồng nghiệp vụ As-Is và To-Be (BPMN).
2. `02_System_Specifications`: Tài liệu Đặc tả Use Case và Functional Requirements.
3. `03_User_Manuals`: Tài liệu hướng dẫn sử dụng đa nền tảng (Web, iOS, Android).

