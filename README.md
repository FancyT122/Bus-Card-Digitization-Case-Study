<h1 align="center">🚌 Hệ Thống Số Hóa Cấp Phát Thẻ Xe Buýt (MCPT Case Study)</h1>

<p align="center">
  <i>Giải pháp chuyển đổi số quy trình tiếp nhận, thẩm định và quản lý dữ liệu thẻ giao thông công cộng, loại bỏ 100% hồ sơ giấy.</i>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Process_Modeling-BPMN_2.0-F24E1E?style=for-the-badge&logo=bpmn" alt="BPMN" />
  <img src="https://img.shields.io/badge/Tools-Draw.io%20%7C%20Figma-FF7262?style=for-the-badge&logo=figma" alt="Tools" />
  <img src="https://img.shields.io/badge/Methodology-Agile%2FSCRUM-0052CC?style=for-the-badge&logo=jira" alt="Agile" />
</p>

---

## 📖 Giới thiệu
Dự án nhằm giải quyết bài toán ách tắc trong quy trình cấp phát thẻ xe buýt miễn phí. Thay vì người dân phải nộp hồ sơ giấy và gửi ảnh qua Zalo để nhân viên nhập liệu lại một cách thủ công, hệ thống mới tự động hóa việc trích xuất dữ liệu và quản lý luồng phê duyệt tập trung.

Hệ thống phục vụ 4 nhóm người dùng:
1. **Người dân (End-users):** Đăng ký trực tuyến, quét mã QR CCCD để tự động điền thông tin, theo dõi trạng thái hồ sơ.
2. **Nhân viên xử lý:** Tiếp nhận và kiểm tra thông tin điện tử.
3. **Nhân viên thẩm định:** Phê duyệt hồ sơ dựa trên các rule nghiệp vụ được cấu hình sẵn.
4. **Admin:** Quản lý phân quyền và trích xuất báo cáo dữ liệu.

---

## ✨ Cải tiến Nghiệp vụ Nổi bật (Business Impact)
*   🚀 **Tự động hóa nhập liệu:** Ứng dụng quét mã QR trên CCCD giúp trích xuất chính xác thông tin nhân khẩu học, giảm thời gian nhập liệu từ 5 phút xuống còn 5 giây/hồ sơ.
*   🔄 **Chuẩn hóa luồng quy trình (BPMN):** Loại bỏ hoàn toàn các bước trung gian thừa trong khâu luân chuyển hồ sơ giấy giữa các phòng ban.
*   📑 **Single Source of Truth:** Hệ thống tài liệu (Use Case, BRD) đồng nhất giúp đội ngũ 39 thành viên (bao gồm 16 BAs, Dev, QA) nắm bắt chính xác yêu cầu phát triển.

---

## 🏗️ Cấu trúc Tài liệu Bàn giao (Deliverables)
*(Tài liệu đã được ẩn danh để bảo mật thông tin nội bộ)*
1. 📁 `01_Process_Modeling`: Sơ đồ luồng nghiệp vụ As-Is và To-Be (BPMN).
2. 📁 `02_System_Specifications`: Tài liệu Đặc tả Use Case và Functional Requirements.
3. 📁 `03_User_Manuals`: Tài liệu hướng dẫn sử dụng đa nền tảng (Web, iOS, Android).

---

## 🛠️ Luồng Trạng Thái Hồ Sơ (Application State Machine)
Hệ thống quản lý chặt chẽ vòng đời của một hồ sơ đăng ký thẻ:

```mermaid
stateDiagram-v2
    [*] --> Draft : Dân điền Form/Quét QR
    Draft --> Pending_Review : Nộp hồ sơ
    Pending_Review --> Rejected : Sai thông tin (Trả về)
    Pending_Review --> Pending_Approval : NV Xử lý xác nhận
    Pending_Approval --> Approved : NV Thẩm định duyệt
    Approved --> Card_Issued : Đã in thẻ
    Card_Issued --> [*]
