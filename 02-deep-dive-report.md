- Nguyễn Thành Đạt
- Đoàn Hải Phong
- Nguyễn Kim Hoàng
- Đặng Minh Chức


**3.1. Current-State Workflow**
Quy trình xử lý tiếp nhận bệnh nhân khiếm thính tại phòng khám/cấp cứu Vinmec hiện tại:
```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Tiếp nhận BN │     │ Cố gắng giao │     │ Liên hệ tìm  │     │ Chờ đợi      │
│ khiếm thính  │ ──→ │ tiếp bằng    │ ──→ │ người nhà /  │ ──→ │ người hỗ trợ │
│ vào cấp cứu  │     │ giấy bút     │     │ phiên dịch   │     │ có mặt       │
│ Ai: Triage   │     │ Ai: Triage   │     │ Ai: Hành chính│    │ Ai: Bệnh nhân│
│ ⏱ 2 phút     │     │ ⏱ 5 phút 🔴  │     │ ⏱ 10 phút 🔴 │     │ ⏱ 20-30m 🔴  │
│ In: BN đến   │     │ In: Giấy/Tay │     │ In: Hồ sơ BN │     │ In: Pending  │
│ Out: Ghi nhận│     │ Out: Rời rạc │     │ Out: Cuộc gọi│     │ Out: N/A     │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ┌──────────────┐
                                                               │ Bước 5       │
                                                               │ Khai thác    │
                                                               │ lâm sàng qua │
                                                               │ trung gian   │
                                                               │ Ai: Bác sĩ ER│
                                                               │ ⏱ 10-15 phút │
                                                               └──────────────┘
🔴 = Bottlenecks
⏱ Tổng thời gian xử lý thủ công: 45 - 60 phút/lượt.
```


**3.2. Problem Statement (6-field) — Vin Smart Future Standard**
Field,Nội dung
1. Actor / Operator,"Điều dưỡng Triage (Phân luồng), Bác sĩ Cấp cứu (ER), và Bệnh nhân khiếm thính."
2. Current Workflow,"Khi bệnh nhân khiếm thính vào cấp cứu, điều dưỡng cố gắng dùng giấy bút nhưng kém hiệu quả do bệnh nhân đau đớn/hoảng loạn. Hành chính phải gọi điện tìm người nhà hoặc điều phối phiên dịch viên ngôn ngữ ký hiệu. Quá trình khai thác tiền sử, triệu chứng lâm sàng bị đình trệ hoàn toàn cho đến khi có người trung gian tới dịch thuật. 5 bước thủ công, mất gần 1 tiếng đồng hồ."
3. Bottleneck,"Bước 3 & 4 (mất 30-40 phút): Khâu tìm kiếm và chờ đợi người phiên dịch chuyên môn y khoa. Đây là ""nút thắt cổ chai"" chí mạng trong môi trường cấp cứu nơi tính mạng tính bằng phút."
4. Business Impact,"Đe dọa an toàn y khoa do làm lỡ ""thời gian vàng"" cấp cứu (đặc biệt với đột quỵ, nhồi máu cơ tim, tai nạn). Gây kẹt băng ca tại khu vực Triage. Trải nghiệm khám chữa bệnh của nhóm người yếu thế giảm sút nghiêm trọng."
5. Success Metric,1. Rút ngắn thời gian khai thác thông tin lâm sàng ban đầu từ >45 phút xuống dưới 2 phút (Efficiency).2. Độ chính xác dịch thuật y khoa chuyên ngành Text-to-Gloss đạt chỉ số BLEU-4 > 40 (Quality).
6. Operational Boundary,AI được phép dịch thuật 2 chiều (Sign-to-Text từ camera và Text-to-Gloss lên màn hình) đối với các câu hỏi khai thác triệu chứng chuẩn. CẤM: AI tuyệt đối không được đưa ra chẩn đoán y khoa; văn bản dịch phải hiển thị song song với hình ảnh để bác sĩ đối chiếu (HITL); dữ liệu video cử chỉ không được lưu trữ hoặc phải ẩn danh hoàn toàn để tuân thủ bảo mật dữ liệu y tế.

**3.3. Future-State Flow & AI Fit**
AI Fit: Chọn AI Agent Đa phương thức (Multimodal Agent) kết hợp Computer Vision. Hệ thống cần luân chuyển liên tục giữa việc dùng Camera bắt chuyển động tay (Sign-to-Text) để báo cáo triệu chứng cho bác sĩ, và render ra avatar 3D (Text-to-Gloss) để truyền đạt câu hỏi của bác sĩ đến bệnh nhân theo thời gian thực (real-time interaction).

Quy trình tương lai (Future-State):
```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Tiếp nhận BN │     │ 🔵 AI Agent  │     │ 🔵 AI Agent  │     │ 🟢 Bác sĩ    │
│ khiếm thính  │ ──→ │ bắt cử chỉ & │ ──→ │ dịch y lệnh  │ ──→ │ nhìn màn hình│
│ vào cấp cứu  │     │ dịch ra Text │     │ ra màn hình  │     │ & ra quyết   │
│              │     │ (Sign-to-text│     │(Text-to-Gloss│     │ định y khoa  │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                                                                      │
                                                                      ▼
                                                               ↩️ Fallback:
                                                               Nếu AI không hiểu
                                                               cử chỉ bất thường,
                                                               Triage gọi người nhà.

```