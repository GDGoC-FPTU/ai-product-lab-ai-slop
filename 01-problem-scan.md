---

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

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | VinFast / V-GREEN|Lặp lại (Repetitive) | Phân loại log lỗi và xử lý ticket chẩn đoán sự cố trạm sạc tự động bị trùng lặp |
| 2 |Xanh SM |Pain từ người khác (Stakeholder Pain) |Lệch vị trí đón/trả khách (PUDO) tại sảnh/hầm các KĐT Vinhomes & TTTM Vincom |
| 3 |Vinhomes |Tốn thời gian (Time-consuming) |Phân loại, tổng hợp và định tuyến ý kiến/khiếu nại cư dân trên app Vinhomes Resident |
| 4 |Vinpearl / VinWonders |AI có thể tốt hơn (AI-upgrade) |Chatbot CSKH theo kịch bản cứng (rule-based) không cá nhân hóa được combo nghỉ dưỡng phức tạp |
| 5 |Vinmec |Tốn thời gian (Time-consuming) |Trích xuất và đối soát dữ liệu bệnh án/hóa đơn phi cấu trúc (PDF/ảnh quét) cho bảo hiểm |

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

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                      │
│                                                             │
│ Bài toán (1 câu): Định vị GPS bị lệch tại các đại đô thị/  │
│ TTTM gây khó khăn cho việc tìm nhau giữa tài xế và khách,   │
│ làm tăng thời gian chờ và tỷ lệ hủy chuyến.                 │
│ Công ty thành viên: [ ] VinFast  [X] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác                   │
│                                                             │
│ Ai đang đau (Actor)? Tài xế Xanh SM & Khách hàng đặt xe     │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Khách cắm pin vị trí trên app                          │
│   ──> 2. Tài xế di chuyển theo chỉ dẫn GPS                  │
│   ──> 3. Lệch vị trí (sảnh/hầm), 2 bên gọi điện tìm nhau    │
│   ──> 4. Tài xế tìm điểm đỗ/đón hoặc hủy chuyến             │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 & 4 (⏱ 5-7 phút/lượt)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1 & 2 (Tự động   │
│ gom cụm điểm đón chuẩn - Smart PUDO dựa trên không gian 3D  │
│ và lịch sử chuyến đi thay vì cắm pin thô).                  │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ "Giảm thời gian tài xế tìm khách từ 6 min ──> under 1.5 min │
│  và giảm tỷ lệ hủy chuyến do không thấy khách từ 15% ──> 4%"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [X] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #02                                      │
│                                                             │
│ Bài toán (1 câu): Ban quản lý mất nhiều thời gian đọc, phân │
│ loại và chuyển tiếp thủ công hàng ngàn phản ánh/khiếu nại   │
│ của cư dân trên app Vinhomes Resident, gây trễ SLA xử lý.   │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [X] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác                   │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên Ban quản lý (BQL) & Cư dân   │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Cư dân gửi phản ánh (chữ + ảnh) qua app                │
│   ──> 2. BQL đọc nội dung phản ánh thủ công                 │
│   ──> 3. Đánh giá mức độ ưu tiên & chọn phòng ban xử lý     │
│   ──> 4. Điều phối ticket & gõ câu phản hồi khởi tạo        │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 10-15 min/lượt)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2, 3 & 4 (Đọc    │
│ hiểu phản ánh đa phương thức, phân loại mức độ khẩn cấp,    │
│ route đúng bộ phận và gợi ý sẵn câu phản hồi cho BQL).     │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ "Giảm thời gian định tuyến ticket từ 15 min ──> under 1 min │
│  và nâng tỷ lệ xử lý khiếu nại đúng SLA từ 75% ──> over 95%"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03                                      │
│                                                             │
│ Bài toán (1 câu): Kỹ thuật viên mất nhiều thời gian đọc log │
│ thủ công để chẩn đoán nguyên nhân sự cố trạm sạc V-GREEN    │
│ và lọc các cảnh báo lỗi bị trùng lặp.                       │
│ Công ty thành viên: [X] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [X] Khác (V-GREEN)         │
│                                                             │
│ Ai đang đau (Actor)? Kỹ thuật viên vận hành trạm sạc        │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Trạm sạc gặp lỗi gửi chuỗi log telemetry về hệ thống  │
│   ──> 2. Bị spam hàng loạt ticket trùng lặp cùng 1 sự cố    │
│   ──> 3. KTV tải file log, tra cứu mã lỗi thủ công          │
│   ──> 4. Phân loại nguyên nhân (xe/trụ/lưới) & phân công KTV │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (⏱ 30-45 phút/sự cố)│
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3 (Gom nhóm  │
│ ticket trùng bằng Anomaly Detection, LLM đọc log chẩn đoán  │
│ root-cause và đề xuất phương án sửa chữa cho KTV).          │
│                                                             │
│ Đo thành công bằng gì (Metric có số)?                        │
│ "Giảm thời gian chẩn đoán lỗi từ 40 min ──> under 3 min     │
│  và giảm thời gian gián đoạn trạm sạc (downtime) đi 25%"    │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [X] Agent │
└─────────────────────────────────────────────────────────────┘