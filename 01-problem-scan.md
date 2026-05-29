# 🔍 Phase 1 — SCAN: Tìm kiếm cơ hội (Cá nhân)

Dùng **4 Lenses** quét qua vận hành của các công ty thành viên Vingroup.

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|------------|------|---------------------|
| 1 | **Xanh SM** | Tốn thời gian | Bộ phận vận hành phải kiểm tra thủ công camera cabin khi có khiếu nại “tài xế thái độ không tốt” hoặc tranh chấp với khách hàng. |
| 2 | **VinFast** | Pain từ người khác | Khách hàng liên tục phản ánh khó hiểu các cảnh báo kỹ thuật hiển thị trên màn hình xe EV, dẫn đến tăng tải hotline hỗ trợ kỹ thuật. |
| 3 | **Vinmec** | AI-upgrade | Hệ thống đặt lịch khám hiện tại chưa tối ưu phân bổ bác sĩ và khung giờ, khiến nhiều khoa quá tải trong khi khoa khác trống lịch. |
| 4 | **Vinhomes** | Lặp lại | Nhân viên an ninh phải xác minh thủ công biển số cư dân/khách vãng lai tại cổng giờ cao điểm mỗi ngày. |
| 5 | **VinWonders** | Tốn thời gian | Nhân viên vận hành phải theo dõi thủ công mật độ khách tại từng khu trò chơi để điều phối nhân sự và mở line mới. |

---

# 🃏 Phase 2 — QUICK-ASSESS: 3 Quick Problem Cards (Cá nhân)

Chọn top 3 từ danh sách SCAN: **#2 (Xanh SM Sự cố sạc), #4 (Vinhomes CSKH), #6 (Xanh SM Hủy chuyến).**

## Thẻ bài toán tiêu biểu: Card #2 — Xanh SM Xử lý sự cố sạc pin thực địa

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán: Hotline VinFast bị quá tải vì khách hàng không    │
│ hiểu các cảnh báo kỹ thuật hiển thị trên xe điện.           │
│ Công ty thành viên: [x] VinFast                             │
│                                                             │
│ Ai đang đau? Chủ xe EV, nhân viên hotline hỗ trợ kỹ thuật   │
│                                                             │
│ Workflow thủ công hiện tại (4 bước):                        │
│   1. Xe hiển thị mã cảnh báo                                │
│   → 2. Khách gọi hotline                                    │
│   → 3. Nhân viên tra cứu mã lỗi                             │
│   → 4. Giải thích nguyên nhân và hướng dẫn xử lý            │
│                                                             │
│ Bước nào tốn nhất?  Bước 3-4 (⏱ 7-10 phút/cuộc gọi)        │
│ AI có thể nhảy vào hỗ trợ ở bước nào?                       │
│ AI giải thích cảnh báo bằng ngôn ngữ dễ hiểu trong app xe   │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│ Giảm 40% cuộc gọi hotline liên quan cảnh báo kỹ thuật       │
│                                                             │
│ Quick Architecture: [x] LLM Feature                         │
└─────────────────────────────────────────────────────────────┘
```

---

# 🗳️ Quyết định lựa chọn của nhóm:
Nhóm quyết định chọn bài toán **"Card #2 — Xanh SM Xử lý sự cố sạc pin thực địa"** để thực hiện Deep-Dive.

## Lý do lựa chọn và loại bỏ các thẻ khác:
* **Card #4 (Vinhomes CSKH):** Mặc dù tốn thời gian nhưng rủi ro sai sót thông tin liên quan đến phí quản lý, tranh chấp căn hộ có thể dẫn đến khiếu nại pháp lý nặng cho Vinhomes. Cần gom thêm dữ liệu và xử lý bằng Rule-based router trước.
* **Card #6 (Xanh SM Hủy chuyến):** Đây là tác vụ phân tích offline (back-office), không ảnh hưởng trực tiếp đến hiệu suất vận hành thời gian thực (real-time) như sự cố hết pin của tài xế trên đường đón khách.

---