# 🔍 Phase 1 — SCAN (Cá nhân)

### 📝 List bài toán của tôi (Tối thiểu 5 bài toán Vingroup):

| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | Xanh SM (GSM) | Lặp lại, Tốn thời gian | Kiểm tra ngoại quan xe tự động bằng AI để phát hiện vết trầy xước/hư hỏng khi giao nhận ca tài xế. |
| 2 | Vinmec | Stakeholder Pain, Tốn thời gian | Tóm tắt hồ sơ bệnh án điện tử, chỉ số lâm sàng & tiền sử bệnh phức tạp giúp bác sĩ nắm bắt tình trạng bệnh nhân trong 1 phút. |
| 3 | Vinhomes | Lặp lại, AI-upgrade | Tự động đọc, phân loại và định tuyến ticket phản ánh từ cư dân (tiếng Việt không dấu/viết tắt) về đúng phòng ban xử lý. |
| 4 | VinFast | Lặp lại, Tốn thời gian | Tự động đối soát và so khớp hóa đơn sạc điện giữa trụ sạc thông minh và tài khoản thanh toán của khách hàng. |
| 5 | Vinpearl / VinWonders | AI-upgrade, Stakeholder Pain | Chatbot trợ lý AI hỗ trợ tư vấn lộ trình vui chơi, giải đáp thắc mắc và tự động xử lý yêu cầu đặt vé/đổi lịch 24/7. |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân)

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Tự động nhận diện vết trầy xước, móp méo  │
│                   ngoại quan xe điện khi giao nhận ca.       │
│ Công ty thành viên: [X] Xanh SM  [ ] VinFast  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác                   │
│                                                             │
│ Ai đang đau (Actor)? Tài xế Xanh SM & Dispatcher quản lý xe │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Kiểm tra mắt ──> 2. Chụp ảnh ──> 3. Tải ảnh lên app    │
│   ──> 4. Dispatcher đối chiếu ảnh cũ/mới & ký biên bản.     │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 1 & 4 (⏱ 15-20 min)   │
│ AI hỗ trợ ở bước nào? Bước 4 (Quét ảnh phát hiện vết xước)  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Giảm thời gian kiểm xe từ 15 phút ──> dưới 3 phút/lượt;   │
│   Độ chính xác nhận diện lỗi > 92%.                         │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Tóm tắt nhanh hồ sơ bệnh án phức tạp giúp │
│                   bác sĩ chuẩn bị trước ca thăm khám.       │
│ Công ty thành viên: [ ] Xanh SM  [ ] VinFast  [ ] Vinhomes  │
│                     [X] Vinmec   [ ] Khác                   │
│                                                             │
│ Ai đang đau (Actor)? Bác sĩ thăm khám & Bệnh nhân Vinmec    │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Mở EMR ──> 2. Đọc từng trang lịch sử khám & xét nghiệm │
│   ──> 3. Tự ghi chép tóm tắt ──> 4. Tiến hành thăm khám.    │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 (⏱ 8-12 min)        │
│ AI hỗ trợ ở bước nào? Bước 2 & 3 (LLM tổng hợp EMR ngắn gọn)│
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Giảm thời gian đọc hồ sơ từ 10 phút ──> dưới 1 phút;      │
│   100% chỉ số dị ứng/chống chỉ định được highlight.         │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Tự động phân loại và định tuyến ticket   │
│                   phản ánh từ cư dân đô thị Vinhomes.       │
│ Công ty thành viên: [ ] Xanh SM  [ ] VinFast  [X] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác                   │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên Ban quản lý & Cư dân         │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Cư dân gửi phản ánh ──> 2. BQL đọc nội dung thủ công   │
│   ──> 3. Phân loại chủ đề ──> 4. Giao ticket cho kỹ thuật.  │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 5-10 min)    │
│ AI hỗ trợ ở bước nào? Bước 2 & 3 (Phân loại & gán nhãn AI)  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Giảm thời gian phân loại ticket từ 10 min ──> under 10s;  │
│   Tỷ lệ định tuyến đúng phòng ban > 90%.                    │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```