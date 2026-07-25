# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
| --- | --- | --- | --- |
| 1 | **VinFast** | Lặp lại (Repetitive) | So khớp dữ liệu sạc điện hằng tuần từ hàng nghìn trụ sạc liên kết ngoài với hóa đơn thực tế gửi về hệ thống tài chính.|
| 2 | **Xanh SM** | Tốn thời gian (Time-consuming) | Tối ưu hóa điểm đón taxi điện Xanh SM dựa trên phân tích ngôn ngữ tự nhiên từ tin nhắn tài xế và tọa độ GPS thực tế.|
| 3 | **Vinhomes** | Lặp lại (Repetitive) | Phân loại tự động các khiếu nại (ví dụ: mất nước, hỏng đèn, ồn ào) gửi qua App Vinhomes Resident đến đúng ban quản lý từng tòa nhà.|
| 4 | **Vinmec** | Tốn thời gian (Time-consuming) | Trích xuất thông tin lâm sàng từ bệnh án điện tử, xét nghiệm và ghi chú của bác sĩ để soạn thảo bản tóm tắt xuất viện bằng ngôn ngữ dễ hiểu cho bệnh nhân.|
| 5 | **Xanh SM** | Pain từ người khác (Stakeholder Pain) | Tự động nghe ghi âm cuộc gọi hủy chuyến và ghi chú của tài xế để phân loại 10 lý do phổ biến nhất gây rò rỉ cuốc.|

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #___                                     │
│                                                             │
│ Bài toán (1 câu): ________________________________________  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? ______________________________________ │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. ___ ──> 2. ___ ──> 3. ___ ──> 4. ___                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? ___ (⏱ ___ phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? _____________________ │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? ______________________ │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

> [!TIP]
> **🤖 AI Prompts — Stress-Test thẻ bài toán:**
> Hãy dán nội dung thẻ bài toán của bạn vào LLM để nhận phản biện:
> *"Đây là một thẻ bài toán vận hành tôi đề xuất cho Vin Smart Future: [Dán nội dung]. Hãy đóng vai trò là một CFO và Trưởng phòng Vận hành cực kỳ khắt khe, chỉ ra cho tôi 3 điểm yếu về logic, metric, và giải thích vì sao rule-based code thông thường có thể giải quyết bài toán này tốt hơn là dùng AI."*

---

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Trích xuất thông tin lâm sàng từ bệnh án  │
│ điện tử và ghi chú để soạn tóm tắt xuất viện.[cite: 1]     │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [x] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Bác sĩ điều trị.                       │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Mở hồ sơ bệnh án điện tử (EMR) ──> 2. Đọc kết quả xét  │
│   nghiệm ──> 3. Xem ghi chú khám ──> 4. Gõ tay bản tóm tắt  │
│   xuất viện bằng ngôn ngữ dễ hiểu.                          │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 4 (⏱ 20-30 phút/lượt) │
│[cite: 1]                                                   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 4 (AI tự động    │
│ tổng hợp dữ liệu thô và draft bản tóm tắt xuất viện).       │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Giảm thời gian soạn tóm tắt xuất viện từ 25 phút ──> dưới │
│   5 phút/bệnh nhân.                                         │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Phân loại tự động khiếu nại của cư dân    │
│ gửi qua App để chuyển hướng đến đúng ban quản lý.[cite: 1] │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên CSKH / Ban quản lý tòa nhà.  │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Cư dân gửi khiếu nại qua App ──> 2. CSKH trực đọc nội  │
│   dung ──> 3. Xác định loại lỗi (điện, nước...) và tòa nhà  │
│   ──> 4. Chuyển ticket cho Ban quản lý tương ứng.           │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 5 phút/lượt) │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3 (AI đọc    │
│ hiểu ngôn ngữ tự nhiên, gắn thẻ và điều hướng tự động).     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Tỉ lệ phân loại ticket đúng > 95%, giảm thời gian xử lý   │
│   bước đầu từ 12 tiếng ──> dưới 1 phút.[cite: 1]           │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```text
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Nghe ghi âm và đọc ghi chú để phân loại   │
│ 10 lý do phổ biến gây hủy chuyến taxi điện.[cite: 1]       │
│ Công ty thành viên: [ ] VinFast  [x] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên Vận hành (Back-office).      │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Trích xuất danh sách cuốc hủy ──> 2. Mở file ghi âm /  │
│   ghi chú ──> 3. Nghe và note tay lý do ──> 4. Tổng hợp vào │
│   file Excel báo cáo tìm nguyên nhân cốt lõi.               │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 10 phút/lượt)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3 (AI tự động│
│ chuyển đổi Speech-to-Text và trích xuất lý do bằng LLM).    │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                       │
│   Quét được 100% data hủy chuyến thay vì lấy mẫu thủ công,  │
│   thời gian phân tích giảm từ 10 phút ──> dưới 30 giây/cuốc.│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```
