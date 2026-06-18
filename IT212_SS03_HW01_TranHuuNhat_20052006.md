Đáp án: Phương án B
1. Vì sao phương án B là tối ưu nhất?

Phương án B tận dụng đúng sức mạnh của các công cụ AI hỗ trợ phân tích mã nguồn ở cấp độ repository (toàn bộ dự án) thay vì chỉ nhìn từng đoạn code riêng lẻ.

Trong tình huống này, logic Checkout không nằm trong một file duy nhất mà phân tán qua:

Controller
Service
Repository
JWT Security Filter
Các DTO/Entity liên quan

Để viết tài liệu SRS chính xác, AI cần hiểu:

Người dùng gọi API nào.
Security Filter xác thực JWT ra sao.
Controller tiếp nhận request như thế nào.
Service xử lý nghiệp vụ thanh toán.
Repository thao tác dữ liệu gì.
Các trường hợp lỗi và ngoại lệ phát sinh.

Khi index toàn bộ dự án trong Antigravity:

AI có thể truy vết luồng xử lý xuyên file.
Hiểu được dependency giữa các lớp.
Tự động xây dựng call graph.
Phân tích được luồng nghiệp vụ end-to-end.

Prompt:

"Act as a System Analyst. Đọc toàn bộ luồng xử lý từ API endpoint /api/v1/checkout..."

giúp AI chuyển từ góc nhìn lập trình viên sang góc nhìn Business Analyst/System Analyst.

Kết quả tạo ra sẽ gần với tài liệu SRS thực tế hơn:

Pre-conditions
Main Flow
Alternative Flow
Exception Flow

thay vì chỉ mô tả code.

2. Liên hệ với kiến thức Session 10

Session 10 tập trung vào:

Repository-wide Context

AI không chỉ nhìn:

CheckoutController.java

mà còn hiểu:

CheckoutController
↓
CheckoutService
↓
PaymentService
↓
OrderRepository
↓
Security Filter

Đây là năng lực mà các công cụ Agentic IDE hỗ trợ rất mạnh.

Giảm Context Switching

Người dùng không phải:

Mở từng file.
Copy từng đoạn code.
Ghép thông tin thủ công.

AI tự tổng hợp ngữ cảnh toàn hệ thống.

Giảm Context Loss

Do toàn bộ source code đã được index nên AI có thể:

Truy vết hàm.
Tìm dependency.
Theo dõi luồng dữ liệu.

Từ đó giảm nguy cơ bỏ sót nghiệp vụ.

3. Nhược điểm của phương án A
Phương án A

Đọc từng file bằng Copilot Chat rồi tự tổng hợp.

Ưu điểm
Có thể hiểu từng đoạn code khá tốt.
Không cần công cụ mới.
Nhược điểm lớn nhất: Context Loss

Copilot thường tập trung vào:

File hiện tại.
Vài file lân cận.

Ví dụ:

CheckoutController

Copilot giải thích được controller.

Nhưng chưa chắc biết:

JwtAuthenticationFilter

đã xử lý gì trước đó.

Dễ bỏ sót luồng nghiệp vụ

Người dùng phải tự:

Đọc Controller.
Đọc Service.
Đọc Repository.
Ghép lại.

Trong quá trình đó dễ:

Quên dependency.
Hiểu sai thứ tự xử lý.
Bỏ sót Exception Flow.
Tốn thời gian

Mỗi file phải:

Mở.
Chọn code.
Hỏi.
Tổng hợp.

Đây là công việc thủ công khá lớn.

4. Nhược điểm của phương án C
Phương án C

Copy 5 file vào ChatGPT/Gemini.

Đây là phương án rủi ro nhất.

Nguy cơ Context Loss cực cao

Bạn chỉ copy:

5 file

Nhưng logic thực tế có thể liên quan:

DTO
Entity
Mapper
Configuration
Filter
Exception Handler
Utility Class

AI không nhìn thấy các phần này.

Thiếu ngữ cảnh hệ thống

Ví dụ:

Trong code có:

jwtService.extractUser()

Nếu không gửi:

JwtService.java

AI phải suy đoán.

Điều này dễ dẫn đến Hallucination.

Nguy cơ vượt giới hạn Context Window

Dự án lớn có thể:

Hàng nghìn dòng code.
Nhiều file phụ thuộc.

Không thể copy toàn bộ vào cửa sổ chat.

Khi phải cắt bớt:

Mất thông tin.
Sai luồng xử lý.
Không cập nhật theo dự án

Khi code thay đổi:

Phải copy lại toàn bộ.
Tốn công sức.
Dễ nhầm phiên bản.
Kết luận

Lựa chọn đúng: B

Vì phương án B:

Tận dụng khả năng phân tích toàn repository của Antigravity.
Giảm tối đa Context Loss.
Giảm Context Switching.
Hiểu được luồng Checkout xuyên suốt từ Security Filter → Controller → Service → Repository.
Sinh ra tài liệu SRS gần với nghiệp vụ thực tế nhất.

Trong khi đó:

A hiểu tốt từng file nhưng khó tổng hợp toàn hệ thống.
C dễ mất ngữ cảnh, dễ hallucination và không phù hợp với các dự án có quy mô lớn.

⇒ Phương án B là lựa chọn tối ưu nhất để tài liệu hóa nghiệp vụ từ mã nguồn lớn