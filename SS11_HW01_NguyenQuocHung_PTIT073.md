# Bài 1: Phân Tích & Lựa Chọn Phương Án Tạo Mã Nguồn (Lesson 01)

## 1. Phương án lựa chọn tối ưu
**Đáp án:** **Phương án B**

## 2. Phân tích lý do chọn Phương án B
Phương án B là phương án tối ưu nhất vì nó tuân thủ đầy đủ và rõ ràng cấu trúc 5 thành phần của một Prompt tiêu chuẩn, giúp AI hiểu chính xác yêu cầu và tránh được việc tự bịa ra thông tin (hallucination):

*   **Vai trò (Role):** "Đóng vai Senior Java Developer." -> Thiết lập mức độ chuyên môn cao, giúp mã nguồn sinh ra đạt chuẩn công nghiệp, tối ưu và tuân thủ best practice của Java.
*   **Nhiệm vụ (Task):** "Viết class PaymentValidator kiểm tra tính hợp lệ của thẻ tín dụng." -> Xác định rõ ràng công việc cụ thể cần làm.
*   **Ngữ cảnh (Context):** "Hệ thống E-commerce, cần validate trước khi gửi API thanh toán." -> Cung cấp thông tin nền để AI hiểu luồng hoạt động, từ đó có thể tổ chức code một cách hợp lý và sát với thực tế dự án.
*   **Ràng buộc (Constraint):** "Dùng Java 17, triển khai thuật toán Luhn, ném ra ngoại lệ IllegalArgumentException nếu thẻ rỗng hoặc chứa chữ cái." -> Rất quan trọng để đảm bảo mã nguồn tương thích với hệ thống hiện tại của TechShop, xử lý được các edge cases theo đúng chuẩn dự án.
*   **Định dạng (Format):** "Chỉ trả về mã nguồn Java trong một code block, không giải thích." -> Giúp dễ dàng tích hợp ngay vào source code mà không phải cắt xén các lời giải thích thừa thãi.

## 3. Phân tích các phương án bị loại trừ

### Phương án A
*   **Lỗ hổng & Rủi ro:** 
    *   Prompt quá ngắn gọn và mơ hồ, thiếu đi các yếu tố cốt lõi như ngữ cảnh, vai trò, ràng buộc và định dạng trả về.
    *   **Rủi ro ảo tưởng (Hallucination) / Sai lệch ngữ cảnh:** AI có thể sinh ra code dùng các thư viện không tương thích (ví dụ: dùng tính năng của phiên bản Java cũ/mới hơn quy định), viết thêm hàm `main` dư thừa, hoặc áp dụng cách xử lý lỗi tùy tiện (ví dụ: `return false` thay vì ném ra Exception) khiến hệ thống không bắt được lỗi đúng chuẩn. Không kiểm soát được output (AI có thể giải thích rất dài dòng).

### Phương án C
*   **Lỗ hổng & Rủi ro:** 
    *   Prompt đưa ra yêu cầu quá lan man, nhồi nhét nhiều tác vụ không liên quan trực tiếp đến nhiệm vụ chính (kiểm tra thuật toán Luhn) như sinh cấu trúc database SQL, hướng dẫn cài đặt và kết nối JDBC.
    *   **Rủi ro ảo tưởng (Hallucination) / Sai lệch ngữ cảnh:** Việc yêu cầu làm quá nhiều việc cùng lúc (cả logic, DB, hướng dẫn) khiến AI bị mất tập trung (Prompt drift). Kết quả trả về có thể là một đống mã nguồn lộn xộn, mã kiểm tra Luhn sơ sài để nhường chỗ cho phần JDBC, và cấu trúc DB sinh ra có thể hoàn toàn sai lệch với thiết kế thực tế của dự án TechShop.
