# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).


### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 |**Vinhomes** |**Time-consuming**, **Stackholder Pain** |Giấy tờ thủ tục xác minh quá lằng nhằng gây ra tốn thời gian của người dân và cả nhân viên. Ngoài ra còn phải tốn chi phí thuê nhân công |
| 2 |**Vinhomes** |**Stakcholder Pain** |Người dân phàn nàn nhưng không nhận được sự phản hồi thích đáng từ ban quản lý tòa nhà dẫn đến sự bực bội. Và còn những câu hỏi có tính lặp đi lặp lại nhiều như tiền điện, tiền nước ... khiến cho chi phí nhân viên tăng cao |
| 3 |**Vinhomes** |**AI upgrade** |Camera AI hoàn toàn có thể bị đánh lừa bằng các patch vật lý được sinh ra bằng các phương pháp sinh hiện đại, đây là các patch mang hình hài rất binhf thường nhưng lại chữa đựng rất nhiều nhiễu khiến cho camera ai khó có thể phát hiện được |
| 4 |**Xanh SM** |**AI upgrade** |trong thời đại AI nói chung và thuật toán RL ngày càng phát triển, cần có một hệ thống xe tự lái, chọn lộ trình, chọn địa điểm đông khách ... thật hợp lý. Thuật toán RL sẽ hộ trợ thực hiện những điều này, hiện tại chỉ cần triển khai trong nội phu Vinhomes, sau đó sẽ mở rộng ra các khu vực đông đúc hơn |
| 5 |**Vinmec** |**AI upgrade** |Phụ thuộc hoàn toàn vào người nhà hoặc phải chờ điều phối phiên dịch viên ngôn ngữ ký hiệu khi bệnh nhân khiếm thính đến khám cấp cứu. Gây trễ "thời gian vàng" trong cấp cứu. Trải nghiệm bệnh nhân giảm sút nghiêm trọng do rào cản giao tiếp. |
| 6 |**Vinmec** |**Time Consuming** |Bác sĩ phải tự gõ lại toàn bộ diễn biến lâm sàng, kết quả xét nghiệm và chỉ định thuốc vào báo cáo xuất viện cuối ngày.|

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                      │
│                                                             │
│ Bài toán (1 câu): Quy trình xác minh hồ sơ thủ công phức tạp│
│ gây thiếu sót, khiến khách hàng đi lại nhiều lần và tạo áp  │
│ lực quá tải cho nhân viên.                                  │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Khách hàng (cư dân), Nhân viên BQL     │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Khách hàng mang hồ sơ trực tiếp đến nộp ──> 2. Nhân    │
│   viên rà soát thủ công, đối chiếu quy định và báo thiếu ──>│
│   3. Khách hàng quay về lấy bổ sung ──> 4. Vòng lặp này gây │
│   ùn ứ, nhân viên căng thẳng, phát sinh thái độ với khách.  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 (Khâu rà soát và    │
│ xác minh giấy tờ - ⏱ 10 - 15 phút/lượt).                    │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1 & 2 (Hệ thống  │
│ LLM tự động trích xuất thông tin, đối chiếu checklist. Thay │
│ thế nhân viên check lỗi sơ cấp, chỉ cần 1 người duyệt tổng).│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   - Giảm thời gian rà soát hồ sơ từ 10-15m ──> dưới 2 phút. │
│   - Giảm >80% số lượt khách phải xuống quầy đối mặt trực    │
│     tiếp với nhân viên.                                     │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #05                                      │
│                                                             │
│ Bài toán (1 câu): Giao tiếp y khoa khẩn cấp với bệnh nhân   │
│ khiếm thính bị chậm trễ do rào cản ngôn ngữ, làm lỡ giờ vàng│
│                                                             │
│ Công ty thành viên: [x] VinFast  [x] Xanh SM  [x] Vinhomes  │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Điều dưỡng Triage, Bác sĩ ER, Bệnh nhân│
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Tiếp nhận ca bệnh ──> 2. Giao tiếp cơ bản thất bại do  │
│   rào cản ──> 3. Liên hệ tìm người nhà/phiên dịch viên ──>  │
│   4. Chờ đợi ──> 5. Tiến hành chẩn đoán qua trung gian      │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 & 4 (⏱ 30-60 phút/lượt)
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3 (Thay thế  │
│ phiên dịch viên bằng màn hình thông minh dịch thuật 2 chiều)│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   - Rút ngắn thời gian khai thác lâm sàng từ >30m ──> <1m   │
│   - Chất lượng dịch thuật: Đạt chỉ số BLEU-4 > 40 cho các   │
│     tác vụ Text-to-Gloss y khoa chuyên ngành.               │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #04                                      │
│                                                             │
│ Bài toán (1 câu): Ứng dụng Học tăng cường (RL) để điều phối │
│ xe tự lái di chuyển đến điểm "nóng" và tối ưu lộ trình nội  │
│ khu Vinhomes.                                               │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Đội ngũ điều phối, Khách hàng, Tài xế  │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Xe chạy rỗng không định hướng chờ app nổ cuốc ──> 2.   │
│   Hệ thống gán cuốc dựa trên khoảng cách (Rule-based) ──>   │
│   3. Lái xe thủ công đến điểm đón ──> 4. Lựa chọn đường đi  │
│   dựa vào kinh nghiệm để tránh tắc nội khu.                 │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 1 & 4 (⏱ 10-15 phút/  │
│ lượt lãng phí do chạy rỗng và tìm đường).                   │
│                                                             │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Từ bước 1 đến 4 (Tự   │
│ động dự báo điểm đông khách, điều phối Agent tự lái và      │
│ cập nhật lộ trình real-time bằng Reinforcement Learning).   │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   - Giảm tỷ lệ chạy xe rỗng (empty cruising time) từ >30%   │
│     ──> dưới 10%.                                           │
│   - Giảm thời gian chờ xe (ETA) của khách ──> dưới 3 phút.  │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘
```