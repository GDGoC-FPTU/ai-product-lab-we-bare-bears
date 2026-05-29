## Bài Tập Tự Luận: Nhật Ký Chiêm Nghiệm Tương Tác Cùng AI

*Góc nhìn từ kỹ sư làm chủ công nghệ - Khi người học mới là kiến trúc sư thực thụ*

Trong suốt buổi học, em đã sử dụng các mô hình ngôn ngữ lớn (LLMs) như ChatGPT, Gemini hay Claude đóng vai trò như những "thought-partners" – đối tác tư duy để hỗ trợ em hiện thực hóa các ý tưởng kiến trúc hệ thống. Tuy nhiên, càng đi sâu vào các bài toán phức tạp mà Thầy/Cô đã định hướng, em càng nhận ra một nguyên lý cốt lõi: AI chỉ thực sự phát huy sức mạnh khi có tư duy của người học/người kỹ sư trực tiếp bẻ lái và kiểm soát. Trong quá trình làm việc, em luôn là người cầm trịch luồng logic, còn AI chỉ đóng vai trò công cụ gia công chi tiết.

### 1. AI đã hỗ trợ em làm gì? (Tự động hóa những cấu trúc em đã định hình)

Em đã dành phần lớn thời gian để tự tư duy và vạch ra luồng dữ liệu (data flow) cho một hệ sinh thái RAG đa phương thức và module dịch thuật Text-to-Gloss (ngôn ngữ ký hiệu) trong y tế. Sau khi tự chốt được kiến trúc tổng thể, em mới dùng AI để tăng tốc độ triển khai:

* **Viết Boilerplate Code:** Em yêu cầu AI dựng khung API bằng Python/FastAPI và thiết lập các kết nối cơ bản đến MongoDB cùng cơ sở dữ liệu vector. Việc này giúp em tiết kiệm được đáng kể thời gian thao tác lặp đi lặp lại.
* **Viết Script tính toán Metric:** Khi cần đo lường độ chính xác của mô hình dịch thuật, em chỉ định AI viết nhanh một hàm tính điểm BLEU-4 dựa trên logic em đã chọn.
* **Red-teaming & Brainstorming:** Em chủ động đưa ra các kịch bản tấn công đầu độc dữ liệu (Data Poisoning) vào hệ thống học máy để xem AI phản ứng ra sao, từ đó em tự đối chiếu, phản biện và chắt lọc ra các phương án phòng thủ thực sự phù hợp với thiết kế của mình.

### 2. Sự "ngây ngô" và ảo giác của AI (Những lỗ hổng em đã phát hiện)

Dù được huấn luyện trên lượng dữ liệu khổng lồ, AI tỏ ra khá máy móc và thiếu tư duy hệ thống khi đối mặt với các bài toán bảo mật thực tế.

* **Đề xuất Rule-based rườm rà, kém hiệu quả:** Khi em thử yêu cầu đề xuất phương án phòng chống Prompt Injection cho hệ thống RAG, AI lập tức sinh ra "ảo giác" (hallucination) với một giải pháp rất tồi: Nó khuyên em viết một bộ lọc Rule-based bằng Regex khổng lồ để chặn từ khóa. Với kiến thức đã học, em nhận thấy ngay giải pháp này vừa ngốn tài nguyên tính toán vừa cực kỳ dễ bị kẻ tấn công vượt mặt.
* **Dễ dàng bị bypass ranh giới an toàn:** Để kiểm chứng điểm yếu trên, em đã tự tay soạn một đoạn prompt "đóng vai" (roleplay bypass) lồng ghép các kỹ thuật thao túng ngữ cảnh. Kết quả là mô hình base đã ngoan ngoãn "nhả" ra toàn bộ system prompt ẩn bên trong, hoàn toàn bỏ qua các ranh giới an toàn. Điều này minh chứng cho em thấy AI không tự hiểu được bảo mật, nó chỉ đang khớp mẫu.

### 3. Bàn tay kỹ sư: Cách em ép khuôn và điều chỉnh AI

Nhận thấy AI bắt đầu đi chệch hướng bằng các giải pháp nông cạn, em đã lập tức can thiệp và giành lại quyền kiểm soát luồng tư duy thay vì để AI tự do suy diễn.

* **Tái định nghĩa cấu trúc lệnh:** Thay vì hỏi những câu mở như "Làm thế nào", em chuyển sang dùng cấu trúc mệnh lệnh giới hạn không gian hoạt động. Em vạch ra các bước tuần tự (1, 2, 3) một cách tuyến tính và dứt khoát, cắt đứt thói quen sinh văn bản lồng ghép phức tạp của mô hình.
* **Thiết lập Operational Boundaries (Ranh giới vận hành):** Em viết lại prompt sửa lỗi code Python bằng các từ khóa mang tính mệnh lệnh tuyệt đối: *"CẤM sử dụng Regex. Chỉ được phép áp dụng logic so sánh khoảng cách trong không gian nhúng (embedding distance) để phát hiện dị thường."*
* **Cung cấp Context tĩnh:** Em ép AI phải viết lại cơ chế phòng thủ dựa trên nền tảng ChromaDB bằng đúng thuật toán mà em đã ấn định. Lúc này, AI không còn quyền "sáng tạo" lan man mà buộc phải tuân thủ nghiêm ngặt định hướng toán học do em vạch ra.

**Chiêm nghiệm rút ra:**
Thưa Thầy/Cô, qua bài tập và quá trình thực hành này, em nhận thấy rõ rằng cuộc chơi với AI không phải là "nhờ AI làm hộ", mà là nghệ thuật "bắt AI làm theo ý mình". Mọi ý tưởng đột phá, mọi kiến trúc tối ưu hay khả năng nhận diện điểm mù của hệ thống đều phải xuất phát từ kinh nghiệm và tư duy phản biện của chính người học. AI là một người thợ xây siêu tốc, nhưng bản thiết kế vĩ đại và linh hồn của hệ thống luôn phải nằm trong tay người kiến trúc sư.