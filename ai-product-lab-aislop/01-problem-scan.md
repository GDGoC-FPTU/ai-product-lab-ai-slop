# 01 — Problem Scan & Quick Cards

**Họ và tên:** Thạch Minh Quân
**MSSV:** 2A202601585
**Nhóm:** ai slop
**Lab 02 — AI Product Scoping (Vin Smart Future)** · Phase 1 + Phase 2

---

## Phase 1 — SCAN

Quét hoạt động vận hành của các công ty thành viên Vingroup qua 4 lenses.

| #   | Subsidiary        | Lens             | Mô tả ngắn bài toán                                                                                                                                                                                                                    |
| --- | ----------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Vinhomes          | Tốn thời gian    | Yêu cầu bảo trì cư dân gửi qua app dưới dạng văn bản tự do. Nhân viên trực phải đọc từng yêu cầu, đoán ra hạng mục (điện / nước / thang máy / vệ sinh), tìm số căn hộ trong câu, rồi mới tạo ticket và gán tổ kỹ thuật.                |
| 2   | VinFast (V-Green) | Lặp lại          | Đối soát log phiên sạc từ trụ sạc với sao kê từ cổng thanh toán. Kế toán vận hành mở hai file Excel và so khớp thủ công từng dòng theo mã phiên, thời gian và số tiền, mỗi ngày.                                                       |
| 3   | Vinmec            | Tốn thời gian    | Soạn tóm tắt bệnh án ra viện. Bác sĩ ghi chú rời rạc suốt quá trình điều trị, đến ngày ra viện phải ngồi tổng hợp lại thành văn bản hoàn chỉnh theo mẫu, rồi chuyển trưởng khoa duyệt.                                                 |
| 4   | Xanh SM           | Stakeholder Pain | Khiếu nại của khách về tài xế được phân loại thủ công và hay bị gán sai nhóm (thái độ / lộ trình / cước phí / vệ sinh xe). Tài xế phàn nàn bị trừ điểm oan vì khiếu nại về cước bị xếp nhầm sang lỗi thái độ.                          |
| 5   | VinWonders        | AI-upgrade       | Câu hỏi đặt vé của khách quốc tế ngoài giờ hành chính chỉ được chatbot kịch bản cứng trả lời. Câu hỏi lệch khỏi kịch bản (combo vé, chính sách trẻ em, thời tiết đóng cửa trò chơi) bị đẩy sang hàng đợi email, trả lời sau 12–24 giờ. |

**Phủ lens:** Lặp lại (#2) · Tốn thời gian (#1, #3) · AI-upgrade (#5) · Stakeholder Pain (#4)

---

## Phase 2 — QUICK-ASSESS

Ba bài toán tiềm năng nhất từ bảng trên: #1, #3, #2.

---

### QUICK PROBLEM CARD #1

| Trường                  | Nội dung                                                                                                                                                                                |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Bài toán (1 câu)**    | Yêu cầu bảo trì cư dân Vinhomes gửi bằng văn bản tự do phải được nhân viên trực đọc và phân loại thủ công trước khi tạo ticket, làm chậm thời gian phản hồi và gây gán sai tổ kỹ thuật. |
| **Công ty thành viên**  | ☐ VinFast · ☐ Xanh SM · ☑ **Vinhomes** · ☐ Vinmec · ☐ Khác                                                                                                                              |
| **Ai đang đau (Actor)** | Nhân viên trực tổng đài Ban quản lý tòa nhà (ca 8 tiếng, 1–2 người/tòa)                                                                                                                 |

**Workflow thủ công hiện tại**

```
1. Cư dân gửi yêu cầu qua app (văn bản tự do, tiếng Việt, có khi kèm ảnh)
   ──> 2. NV trực đọc, đoán hạng mục, dò số căn hộ trong câu, đánh giá mức khẩn
   ──> 3. NV tạo ticket trên hệ thống, gán tổ kỹ thuật
   ──> 4. Tổ kỹ thuật nhận, xử lý
   ──> 5. NV nhắn lại cư dân kết quả
```

| Trường                            | Nội dung                                                                                                                                                 |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Bước tốn thời gian / lỗi nhất** | Bước 2 — đọc và phân loại thủ công (⏱ ~4 phút/yêu cầu; ~90 yêu cầu/ngày/tòa)                                                                             |
| **AI nhảy vào ở bước nào**        | Bước 2. LLM đọc văn bản tự do, trả về JSON có cấu trúc: hạng mục, số căn hộ, mức khẩn, tóm tắt 1 dòng. Nhân viên chỉ xác nhận hoặc sửa.                  |
| **Metric có số**                  | Giảm thời gian phân loại từ **4 phút → dưới 45 giây/yêu cầu**; **≥85%** yêu cầu được gán đúng tổ kỹ thuật ngay lần đầu (baseline hiện tại ước tính 70%). |
| **Quick Architecture**            | ☐ No AI · ☐ Rule · ☑ **LLM** · ☐ Agent                                                                                                                   |

**Vì sao LLM chứ không phải Rule:** đầu vào là tiếng Việt tự nhiên, không dấu, viết tắt, lẫn tiếng địa phương ("nước yếu quá bác ơi p2508"). Rule dựa trên từ khoá sẽ vỡ ngay khi cư dân mô tả triệu chứng thay vì gọi tên hạng mục ("nghe tiếng rít trong tường" = ống nước). Đây là bài toán hiểu ngôn ngữ, đúng vùng mạnh của LLM.

---

### QUICK PROBLEM CARD #2

| Trường                  | Nội dung                                                                                                                                                                  |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Bài toán (1 câu)**    | Bác sĩ Vinmec mất trung bình hơn 20 phút mỗi hồ sơ để tổng hợp ghi chú điều trị rời rạc thành tóm tắt bệnh án ra viện theo mẫu, chiếm thời gian lẽ ra dành cho khám bệnh. |
| **Công ty thành viên**  | ☐ VinFast · ☐ Xanh SM · ☐ Vinhomes · ☑ **Vinmec** · ☐ Khác                                                                                                                |
| **Ai đang đau (Actor)** | Bác sĩ điều trị nội trú; thứ cấp là điều dưỡng hành chính và trưởng khoa duyệt                                                                                            |

**Workflow thủ công hiện tại**

```
1. BS ghi chú rời rạc vào bệnh án trong suốt quá trình điều trị
   ──> 2. Ngày ra viện, BS đọc lại toàn bộ và tổng hợp thành tóm tắt theo mẫu
   ──> 3. Trưởng khoa đọc và duyệt
   ──> 4. In, ký, trả bệnh nhân
```

| Trường                            | Nội dung                                                                                                                                               |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Bước tốn thời gian / lỗi nhất** | Bước 2 — soạn tóm tắt (⏱ ~22 phút/hồ sơ, dồn vào cuối ca nên hay bị làm vội)                                                                           |
| **AI nhảy vào ở bước nào**        | Bước 2, và **chỉ sinh bản nháp**. LLM đọc ghi chú đã có, sắp xếp lại theo mẫu (diễn biến, chẩn đoán đã ghi, thuốc đã kê, dặn dò). Bác sĩ đọc, sửa, ký. |
| **Metric có số**                  | Giảm thời gian soạn từ **22 phút → dưới 7 phút/hồ sơ**; **100%** bản nháp bắt buộc có chữ ký bác sĩ trước khi phát hành — không có ngoại lệ.           |
| **Quick Architecture**            | ☐ No AI · ☐ Rule · ☑ **LLM** (bắt buộc Human-in-the-loop) · ☐ Agent                                                                                    |

**Operational Boundary sơ bộ (bài toán này rủi ro cao nhất trong 3 card):**

- AI **chỉ được sắp xếp lại thông tin đã có** trong ghi chú. Tuyệt đối không sinh chẩn đoán mới, không suy diễn liều thuốc, không thêm chỉ định theo dõi mà bác sĩ chưa ghi.
- Thông tin nào không có trong ghi chú thì để trống và đánh dấu `[THIẾU]`, không được điền cho đủ mẫu.
- Mọi output đều là bản nháp, không có đường nào phát hành thẳng tới bệnh nhân.
- Dữ liệu bệnh án là dữ liệu nhạy cảm — cần xác định rõ mô hình chạy ở đâu trước khi bàn tiếp về kỹ thuật.

---

### QUICK PROBLEM CARD #3

| Trường                  | Nội dung                                                                                                                                                      |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Bài toán (1 câu)**    | Kế toán vận hành V-Green đối soát thủ công trên Excel giữa log phiên sạc và sao kê cổng thanh toán, mỗi ngày khoảng 2.000 giao dịch, mất gần nửa ca làm việc. |
| **Công ty thành viên**  | ☑ **VinFast (V-Green)** · ☐ Xanh SM · ☐ Vinhomes · ☐ Vinmec · ☐ Khác                                                                                          |
| **Ai đang đau (Actor)** | Nhân viên kế toán vận hành trạm sạc                                                                                                                           |

**Workflow thủ công hiện tại**

```
1. Xuất log phiên sạc từ hệ thống trụ (CSV)
   ──> 2. Xuất sao kê giao dịch từ cổng thanh toán (CSV)
   ──> 3. So khớp thủ công trên Excel theo mã phiên, thời gian, số tiền
   ──> 4. Đánh dấu dòng lệch, soạn email tra soát gửi đối tác thanh toán
```

| Trường                            | Nội dung                                                                                                                        |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Bước tốn thời gian / lỗi nhất** | Bước 3 — so khớp thủ công (⏱ ~180 phút/ngày cho ~2.000 giao dịch)                                                               |
| **AI nhảy vào ở bước nào**        | **Không bước nào.** Xem lý giải dưới.                                                                                           |
| **Metric có số**                  | Tự động khớp **≥98%** giao dịch; chỉ **dưới 2%** còn lại cần người xem, đưa thời gian đối soát từ 180 phút → dưới 20 phút/ngày. |
| **Quick Architecture**            | ☐ No AI · ☑ **Rule / State-Machine** · ☐ LLM · ☐ Agent                                                                          |

**Vì sao cố ý không chọn LLM:** cả hai đầu vào đều là dữ liệu có cấu trúc, có khoá khớp tường minh (mã phiên) và hai khoá phụ (timestamp, số tiền). Đây là bài toán `JOIN` cộng vài luật dung sai, giải bằng vài chục dòng Python là xong — chạy trong vài giây, kết quả tất định, kiểm toán được từng dòng.

Đưa LLM vào đây làm hỏng đúng thứ mà nghiệp vụ kế toán cần nhất: **tính tất định và khả năng truy vết**. Một mô hình xác suất khớp sai 0,5% trên 2.000 giao dịch là 10 sai lệch tiền bạc mỗi ngày mà không ai giải thích được vì sao. Chi phí API cũng vô nghĩa so với một script chạy miễn phí.

Card này được giữ lại trong bộ 3 để làm đối chứng: **một bottleneck có thật, đáng tự động hoá, nhưng không phải bài toán AI.**

---

## So sánh nhanh 3 card

|                          | Card #1 Vinhomes            | Card #2 Vinmec               | Card #3 V-Green        |
| ------------------------ | --------------------------- | ---------------------------- | ---------------------- |
| Kiểu dữ liệu vào         | Văn bản tự do               | Văn bản tự do                | Có cấu trúc            |
| Kiến trúc                | LLM                         | LLM + HITL bắt buộc          | Rule                   |
| Rủi ro khi AI sai        | Thấp (gán sai tổ, sửa được) | **Cao** (an toàn người bệnh) | —                      |
| Có sẵn dữ liệu test      | Log ticket cũ, dồi dào      | Cần phê duyệt y đức          | CSV sẵn                |
| Làm được trong scope hẹp | ✅                          | ⚠️ vướng dữ liệu nhạy cảm    | ✅ nhưng không phải AI |

**Đề xuất mang ra nhóm thảo luận:** Card #1. Đủ khó về ngôn ngữ để LLM có đất diễn, rủi ro thấp nên ranh giới vận hành thiết kế được trong một buổi, và có sẵn log ticket cũ để test — thoả cả 3 mục trong AI Readiness Checklist ở Phase 5.

---

## Ghi chú về giả định

Các con số thời gian và sản lượng trong tài liệu này là **ước lượng của cá nhân tôi dựa trên suy luận về quy mô vận hành**, không phải số liệu đo được từ Vingroup. Cụ thể: 4 phút/yêu cầu và 90 yêu cầu/ngày (Card #1), 22 phút/hồ sơ (Card #2), 2.000 giao dịch/ngày và 180 phút (Card #3), tỉ lệ gán đúng 70% ở baseline.

Nếu bài toán được chọn để Deep-Dive, các số này cần được thay bằng số đo thật hoặc ít nhất một khoảng ước lượng có căn cứ trước khi đưa vào phần Business Impact của `02-deep-dive-report.md`.
