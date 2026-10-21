<h1 align="center">Hệ Thống Số Hóa Cấp Phát Thẻ Xe Buýt (Case Study)</h1>
<p align="center">
  <i>⚠️ Lưu ý bảo mật: Do yêu cầu bảo mật thông tin, toàn bộ tên cơ quan ban hành, dữ liệu định danh công dân và các quy trình nội bộ nhạy cảm đã được ẩn danh, đổi tên hoặc loại bỏ khỏi kho lưu trữ này. Repository này chỉ nhằm mục đích minh họa tư duy hệ thống và kỹ năng.</i>
<p align="center">
  <img src="https://img.shields.io/badge/Process_Modeling-BPMN_2.0-F24E1E?style=for-the-badge" alt="BPMN 2.0" />
  <img src="https://img.shields.io/badge/System_Analysis-Use_Case_%7C_UML-0052CC?style=for-the-badge" alt="Use Case & UML" />
  <img src="https://img.shields.io/badge/Tools-Draw.io-F08705?style=for-the-badge&logo=diagramsdotnet&logoColor=white" alt="Draw.io" />
  <img src="https://img.shields.io/badge/Documentation-User_Manual-00C7B7?style=for-the-badge" alt="Documentation" />
</p>

## 1. Tổng quan dự án
*   **Bối cảnh:** Chuyển đổi số toàn diện quy trình cấp phát thẻ giao thông công cộng ưu tiên cho hơn 100.000+ công dân (Người cao tuổi, Trẻ em, Người khuyết tật, Người có công) trên đa nền tảng (Web/Mobile App).
*   **Vấn đề nghiệp vụ:** 
    *   Quy trình cũ vận hành 100% thủ công trên giấy tờ, gây ùn tắc tại quầy (10-15 phút/hồ sơ).
    *   Truyền tải dữ liệu qua kênh trung gian gây phân mảnh hệ thống, giảm chất lượng ảnh in thẻ và tiềm ẩn rủi ro rò rỉ dữ liệu cá nhân.
    *   Thiếu đồng bộ vật lý dẫn đến hiện tượng "thẻ ảo" (hệ thống báo có nhưng không tìm thấy thẻ thực tế).
*   **Giải pháp:** Xây dựng hệ thống phần mềm tập trung. Ứng dụng công nghệ quét OCR từ mã QR trên thẻ CCCD gắn chip để tự động bóc tách dữ liệu, chuẩn hóa địa chỉ cư trú thông minh và quản lý vòng đời hồ sơ, kết xuất lô in tự động.

## 2. Vai trò & Đóng góp
Trong dự án quy mô 39 thành viên, với vai trò là **Business Analyst Intern**, tôi chịu trách nhiệm thực thi các hạng mục cốt lõi:
*   **Mô hình hóa quy trình:** Trực tiếp khảo sát thực địa, phân tích nút thắt cổ chai và vẽ chuẩn hóa 6 luồng quy trình hiện tại (AS-IS) cùng 3 luồng quy trình tương lai (TO-BE) bằng chuẩn BPMN 2.0.
*   **Phân tích hệ thống:** Phối hợp cùng team Product định nghĩa phạm vi hệ thống, phân quyền tác nhân (RBAC) và viết tài liệu Đặc tả Use Case cho các luồng Front-end.
*   **Tài liệu hóa:** Dẫn dắt quá trình biên soạn Tài liệu Hướng dẫn sử dụng (User Manual) cho đa nền tảng (Web, Android, iOS).

## 3. Giá trị nghiệp vụ mang lại
*   **Tối ưu hóa thời gian:** Ứng dụng QR OCR giúp rút ngắn thời gian tiếp nhận và xử lý hồ sơ tại quầy từ 15-20 phút xuống **dưới 3 phút/người**.
*   **Nâng cao chất lượng dữ liệu:** Triệt tiêu hoàn toàn lỗi sai chính tả trong khâu nhập liệu thủ công; tự động chuẩn hóa đơn vị hành chính sau sáp nhập.
*   **Bảo mật & Tự động hóa:** Loại bỏ khâu luân chuyển trung gian, ứng dụng xử lý ảnh trực tiếp và phân luồng tra cứu an toàn.

---

## 4. Cấu trúc tài liệu
Dưới đây là các tài liệu phân tích nghiệp vụ đã được trích xuất/ẩn danh:

### 📁 [1. Phân tích Quy trình Nghiệp vụ (BPMN 2.0)](./1_BPMN_Process_Flows)
*   [Luồng AS-IS 00 - Tổng quan luồng thủ công](./1_BPMN_Process_Flows/AS_IS_Process/AS_IS_00_TongQuan.md)
*   [Luồng AS-IS 01 - Tiếp nhận đơn giấy và dữ liệu](./1_BPMN_Process_Flows/AS_IS_Process/AS_IS_01_TiepNhanVaKiemTraHoSo.md)
*   [Luồng AS-IS 02 - Chụp ảnh và bàn giao dữ liệu](./1_BPMN_Process_Flows/AS_IS_Process/AS_IS_02_ChupAnhVaBanGiao.md)
*   [Luồng TO-BE 00 - Kiến trúc tổng quan hệ thống số hóa](./1_BPMN_Process_Flows/TO_BE_Process/TO_BE_00_TongQuan.md)
*   [Luồng TO-BE 01 - Tự động hóa khởi tạo hồ sơ số](./1_BPMN_Process_Flows/TO-BE_Process/TO_BE_01_TiepNhanVaKhoiTao.md)

### 📁 [2. Đặc tả Use Case (Use Case Specifications)](./2_Use_Case_Specifications)
*   [Sơ đồ Use Case Tổng quan và Phân quyền Tác nhân](./2_Use_Case_Specifications/Sodo_UseCase_TongQuan.md)
*   [Đặc tả UC_01: Đăng ký hồ sơ cấp thẻ mới](./2_Use_Case_Specifications/UC01_DangKyCapThe.md)
*   [Đặc tả UC_02: Tra cứu trạng thái hồ sơ công khai](./2_Use_Case_Specifications/UC02_TraCuuHoSo.md)

### 📁 [3. Tài liệu Hướng dẫn sử dụng (User Manuals)](./3_User_Manuals)
*   *(Trích đoạn) Hướng dẫn sử dụng nền tảng Web/App dành cho Công dân.*
---

