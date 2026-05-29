
### 📝 List bài toán của tôi:

| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
| --- | --- | --- | --- |
| 1 | Vinhomes | Tốn thời gian | Phân loại, điều phối và soạn phản hồi thủ công cho hàng trăm ticket phàn nàn/yêu cầu của cư dân mỗi ngày trên ứng dụng Vinhomes. |
| 2 | VinFast | Tốn thời gian | Kỹ thuật viên xưởng dịch vụ tốn quá nhiều thời gian đọc hiểu file log lỗi xe điện (hàng ngàn dòng) để tìm nguyên nhân gốc rễ và tra cứu sổ tay sửa chữa. |
| 3 | Vinmec | Lặp lại | Điều dưỡng phải gõ nhập liệu lại thủ công các chỉ số xét nghiệm, đơn thuốc từ hồ sơ giấy của bệnh viện tuyến dưới vào hệ thống EMR của Vinmec. |
| 4 | Xanh SM | Stakeholder Pain | Tài xế phàn nàn vì phải nhận những cuốc xe có lộ trình đón khách quá xa hoặc phải chạy xe không (empty run) trong thời tiết xấu do hệ thống điều phối thiếu ngữ cảnh thời gian thực. |
| 5 | Vinpearl | AI-upgrade | Chatbot CSKH hiện tại quá rập khuôn (rule-based), không thể tư vấn cá nhân hóa lịch trình vui chơi hoặc upsell chéo dịch vụ cho khách hàng dựa trên ngữ cảnh gia đình họ. |

1.QUICK PROBLEM CARD 1 : Vinhomes Smart Ticketing
Bài toán (1 câu): Tự động hóa quá trình đọc hiểu, phân loại tag, điều phối ticket và gợi ý phản hồi cho các yêu cầu/phàn nàn của cư dân trên app Vinhomes.

Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  [ ] Vinmec  [ ] Khác

Ai đang đau (Actor)? Nhân viên Chăm sóc khách hàng (BQL Tòa nhà).

Workflow thủ công hiện tại:

Cư dân tạo ticket trên app ──> 2. CSKH đọc để hiểu vấn đề ──> 3. CSKH phân loại và tag bộ phận (Kỹ thuật/Vệ sinh/An ninh) ──> 4. CSKH soạn tin nhắn phản hồi cư dân.

Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (Đọc hiểu và điều phối thủ công) (⏱ ~5-7 phút/ticket).

AI có thể nhảy vào hỗ trợ ở bước nào? Đứng giữa bước 1 và 2. AI đọc nội dung ticket, tự động gán tag (phân loại bộ phận), xác định mức độ khẩn cấp (SLA) và tạo bản nháp (draft) câu trả lời để CSKH chỉ cần duyệt.

Đo thành công bằng gì (Metric có số)?

Giảm thời gian xử lý ticket bước đầu từ 5 phút ──> dưới 30 giây/ticket.

Tỷ lệ tự động phân loại đúng bộ phận > 90%.

Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent

2.QUICK PROBLEM CARD #2: VinFast EV Log Analyzer
Bài toán (1 câu): Tóm tắt và phân tích nguyên nhân lỗi xe điện từ các file log chẩn đoán dài hàng ngàn dòng, kết hợp tra cứu tài liệu kỹ thuật để gợi ý hướng sửa chữa.

Công ty thành viên: [x] VinFast  [ ] Xanh SM  [ ] Vinhomes  [ ] Vinmec  [ ] Khác

Ai đang đau (Actor)? Kỹ thuật viên Xưởng dịch vụ & Chuyên viên chẩn đoán từ xa.

Workflow thủ công hiện tại:

Cắm máy chẩn đoán vào xe ──> 2. Xuất file log (nhiều mã lỗi nhiễu) ──> 3. Kỹ thuật viên đọc/search mã lỗi thủ công ──> 4. Mở tài liệu PDF đối chiếu phương án ──> 5. Tiến hành sửa.

Bước nào tốn thời gian/lỗi nhất? Bước 3 & 4 (Phân tích log và tra cứu chéo) (⏱ ~20-30 phút/xe).

AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3. AI tiếp nhận file log, lọc bỏ nhiễu, xác định chuỗi sự kiện gây lỗi chính và đối chiếu với cơ sở dữ liệu hướng dẫn (RAG) để xuất ra top 3 nguyên nhân và cách khắc phục.

Đo thành công bằng gì (Metric có số)?

Giảm thời gian chẩn đoán ban đầu từ 30 phút ──> dưới 3 phút/xe.

Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM (RAG)  [ ] Agent

3 QUICK PROBLEM CARD #3: Vinhomes Vendor Compliance Checker

Bài toán (1 câu): Trích xuất thông tin tự động từ hàng trăm trang hồ sơ nhà thầu định dạng PDF (chữ ký, ngày hết hạn chứng chỉ, thông số tài chính) để audit trước khi đấu thầu.

Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  [ ] Vinmec  [ ] Khác

Ai đang đau (Actor)? Chuyên viên Mua sắm & Đấu thầu (Procurement Executive).

Workflow thủ công hiện tại:

Vendor nộp file PDF hồ sơ ──> 2. Chuyên viên mở file ──> 3. Cầm checklist (Excel) dò từng trang tìm Giấy phép ĐKKD, Báo cáo tài chính, ISO ──> 4. Nhập tay số liệu/ngày hết hạn vào hệ thống ERP ──> 5. Đánh giá Đạt/Không đạt.

Bước nào tốn thời gian/lỗi nhất? Bước 3 & 4 (Dò tìm "mò kim đáy biển" trong file PDF scan không chuẩn) (⏱ 45-60 phút/bộ hồ sơ).

AI có thể nhảy vào hỗ trợ ở bước nào? Nằm ở bước 1 sang bước 2. Sử dụng Document AI (kết hợp OCR và LLM có Structured Output). Hệ thống đọc hàng loạt PDF, map thông tin vào chuẩn JSON theo yêu cầu (Ví dụ: {"ISO_9001_Valid_Until": "2027-12-01", "Revenue_2025": "15B"}) và tự highlight đỏ nếu phát hiện chứng chỉ hết hạn.

Đo thành công bằng gì (Metric có số)?

Rút ngắn thời gian audit hồ sơ từ 60 phút ──> 5 phút/bộ (Con người chỉ review lại JSON output).

Phát hiện 100% các chứng chỉ cận ngày hết hạn (< 30 ngày).

Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM (Structured Output & Document AI)  [ ] Agent
