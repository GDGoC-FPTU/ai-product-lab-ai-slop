Phase 1:
### 📝 List bài toán của tôi:

| # | Subsidiary | Lens | Mô tả ngắn bài toán |
|---|---|---|---|
| 1 | Vinhomes | Tốn thời gian & Stakeholder Pain | Phân loại và điều phối thủ công các yêu cầu bảo trì, sửa chữa từ cư dân đến kỹ thuật viên, dễ gây chậm trễ SLA. |
| 2 | Vinhomes | Lặp lại | Kế toán tốn nhiều ngày cuối tháng để tra soát, đối khớp thủ công các khoản chuyển khoản đóng phí sai cú pháp của cư dân. |
| 3 | Vinhomes | Stakeholder Pain | Nhân viên an ninh giám sát hàng ngàn camera CCTV 24/7 bằng mắt thường, dễ mất tập trung và bỏ lọt sự cố (đỗ xe sai, rác thải). |
| 4 | Vinhomes | AI có thể tốt hơn | Chatbot CSKH hiện tại cứng nhắc, tỷ lệ tự động hóa thấp khiến khối lượng lớn yêu cầu giải đáp quy định đổ dồn lên nhân viên tổng đài. |
| 5 | Vinhomes | Lặp lại & Tốn thời gian | Nhân viên bàn giao nhà phải ghi chép lỗi thủ công bằng giấy, sau đó về văn phòng gõ lại vào Excel và khớp ảnh chụp để gửi nhà thầu. |

Phase 2:
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                       │
│                                                             │
│ Bài toán (1 câu): Đối khớp thủ công hàng ngàn giao dịch     │
│ chuyển khoản đóng phí sai cú pháp vào mỗi kỳ chốt sổ.       │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên Kế toán Ban quản lý.         │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Tải sao kê NH ──> 2. Lọc GD sai cú pháp ──> 3. Dò tìm  │
│   thủ công (tiền, tên) trên Excel ──> 4. Gạch nợ thủ công   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (⏱ 5-10 phút/lượt)  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 & 3 (Sử dụng   │
│ NLP/LLM để phân tích ý định chuyển khoản & so khớp tự động).│
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian xử lý  │
│ giao dịch sai cú pháp từ 5 phút/GD ──> dưới 10 giây/GD.     │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                       │
│                                                             │
│ Bài toán (1 câu): Chatbot CSKH quá cứng nhắc, đẩy khối lượng│
│ lớn yêu cầu tư vấn quy định phức tạp lên nhân viên tổng đài.│
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Cư dân (chờ lâu) & Tổng đài viên (OT). │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Cư dân chat app ──> 2. Chatbot cũ kẹt ──> 3. Chuyển cho│
│   Agent ──> 4. Agent tra cứu cẩm nang ──> 5. Gõ phản hồi    │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 4&5 (⏱ 10 phút/lượt)  │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 2 (Thay bằng AI  │
│ Agent đọc hiểu ngữ cảnh & truy xuất cẩm nang trả lời ngay). │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Tăng tỷ lệ tự động    │
│ giải quyết (Deflection rate) từ 20% ──> 70-80%.             │
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent │
└─────────────────────────────────────────────────────────────┘
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                       │
│                                                             │
│ Bài toán (1 câu): Quy trình ghi nhận lỗi (defect) khi bàn   │
│ giao nhà làm thủ công, mất nhiều thời gian nhập liệu lại.   │
│                                                             │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [x] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Nhân viên CSKH thực địa (Bàn giao).    │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Chụp ảnh/Ghi giấy ──> 2. Về văn phòng ──> 3. Gõ lại    │
│   vào Excel ──> 4. Khớp ảnh ──> 5. Gửi nhà thầu             │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3&4 (⏱ 45 phút/căn)   │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 1 (Thu âm giọng  │
│ nói tại chỗ, AI tự bóc băng, phân loại lỗi và tạo báo cáo). │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian tạo hồ │
│ sơ defect từ 45 phút/căn ──> 2 phút/căn ngay tại hiện trường│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [x] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘