# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)
### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | | | |Duyệt thủ công biên bản giám sát chất lượng và phản hồi của khách hàng (QC & Feedback) có độ trễ cao 
| 2 | | | |Lập lịch bảo dưỡng Pin và Xe dựa trên mốc thời gian cứng (Fixed-interval Maintenance), không tối ưu được vòng đời pin
| 3 | | | |Điều phối thủ công và bù giá (Surge Pricing & Matching) theo vùng cứng, phản ứng chậm với các sự kiện đột ngột, hiện tượng lệch về cung - cầu
| 4 | | | |Kiểm tra và phê duyệt thủ công chứng từ hoàn tiền/đổi ca của Tài xế, đối soát mất nhiều thời gian, dễ gian lận
| 5 | | | |Dự báo thủ công nhu cầu tại các Trạm Sạc (Charging Station Demand Forecasting), phân phối không đều dẫn đến tình trạng quá tải.

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

Chọn top 3 từ danh sách SCAN:#2 Xanh SM lập lịch bảo dưỡng xe, #3 Xanh SM điều phối xe, #5 Xanh SM điều phối xe tại các trạm sạc


┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                      │
│                                                             │
│ Bài toán (1 câu): Lập lịch bảo dưỡng Pin và Xe dựa trên mốc │
│ thời gian cứng (Fixed-interval), gây lãng phí chi phí vận   │
│ hành và giảm tối đa vòng đời Pin (SoH).                     │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Đội quản lý đội xe (Fleet Management) &│
│ Đội ngũ kỹ thuật tại Xưởng dịch vụ (VinFast Service).        │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Đạt mốc Km/Ngày ──> 2. Fleet Manager gọi xe về xưởng ──>│
│   3. Kỹ thuật viên đo đạc thủ công thông số SoH/Lỗi ──>     │
│   4. Xử lý bảo dưỡng rập khuôn (thay linh kiện/xả pin).     │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 & 4 (⏱ 120-180 phút/xe)│
│ do phải kiểm tra thủ công và giữ xe lại xưởng kiểm thử lâu.  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1 & 2 (Dự báo     │
│ chủ động dựa trên Telemetry Data gửi về thời gian thực).   │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│   "Giảm Down-time của xe tại xưởng từ 1.5 ngày ──> dưới 4 giờ"│
│   "Tăng vòng đời pin thêm 12 - 15% (kéo dài thời gian SoH >80%)"│
│                                                             │
│ Quick Architecture: [ ] No AI  [x] Rule  [ ] LLM  [ ] Agent │ │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #02                                      │
│                                                             │
│ Bài toán (1 câu): Điều phối và cấu hình bù giá (Surge       │
│ Pricing) bằng Geofence cứng, phản ứng chậm với thời tiết/sự │
│ kiện đột ngột gây hiện tượng lệch cung - cầu nghiêm trọng.   │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Đội vận hành trung tâm (Dispatching    │
│ Operations Team) và trực tiếp là thu nhập của Tài xế.      │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Phát sinh điểm nóng (mưa/sự kiện) ──> 2. Ops Manager   │
│   phát hiện qua Dashboard trễ ──> 3. Cấu hình tăng hệ số giá│
│   hoặc đẩy thông báo khuyến khích tài xế di chuyển thủ công.│
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 15-20 phút độ trễ)│
│ khiến hệ thống lỡ mất "khung giờ vàng" khi nhu cầu đạt đỉnh.│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Toàn bộ quy trình từ  │
│ Dự báo dòng cầu (Demand prediction) đến Tự động tính giá.  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│   "Tăng tỷ lệ nhận chuyến thành công (Match rate) giờ cao   │
│    điểm từ 72% ──> trên 88%"                                │
│   "Giảm tỷ lệ hủy app của khách (Passenger Churn) do chờ    │
│    lâu xuống dưới 5%"                                       │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03                                      │
│                                                             │
│ Bài toán (1 câu): Tài xế tập trung sạc tự phát gây quá tải  │
│ cục bộ tại một số trạm sạc trọng điểm, trong khi các trạm   │
│ khác trống trụ.  │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Tài xế Xanh SM (mất thời gian chờ),    │
│ Đội vận hành hạ tầng trạm sạc (Charging Network Operations).│
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Xe sắp hết pin ──> 2. Tài xế nhìn app xem trạm gần nhất ──>│
│   3. Tự đi đến trạm sạc theo thói quen/bản năng ──> 4. Xếp    │
│   hàng thủ công chờ đến lượt sạc nếu trạm bị đông.          │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 4 (⏱ 45-60 phút/lượt chờ)│
│ gây ức chế lớn cho tài xế và làm giảm hiệu suất khai thác xe.│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3 (Gợi ý trạm │
│ sạc tối ưu và định tuyến phân luồng tự động).                │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│   "Giảm thời gian chờ xếp hàng sạc của tài xế từ 45 min     │
│    ──> dưới 10 min nhờ phân luồng thông minh"               │
│   "Tăng hiệu suất khai thác toàn hệ thống trạm thêm 18%"     │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘