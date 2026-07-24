Tên nhóm: AI slop
Họ và tên kèm Mã số sinh viên (MSSV) 
Nguyen Minh Nhat  - 2A202601131
Nguyễn Kim Trung Đức - 2A202601325
Thach Minh Quan  - 2A202601585 
Nguyễn Huy Nghĩa - 2A202601943
Phạm Thái Sơn - 2A202601984

# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)
Nhóm quyết định chọn bài toán "Vinmec - Soạn thảo tóm tắt hồ sơ xuất viện" để thực hiện Deep-Dive.

## 3.2. Problem Statement (6-field) & Metrics (15 min)
| Field | Nội dung chi tiết |
| --- | --- |
| **1. Actor / Operator** | Bác sĩ điều trị hoặc Điều dưỡng hành chính tại bệnh viện Vinmec. |
| **2. Current Workflow** | Khi bệnh nhân chuẩn bị xuất viện, bác sĩ phải tổng hợp thông tin từ nhiều phân hệ trong Bệnh án điện tử (EMR): lý do nhập viện, sinh hiệu, kết quả cận lâm sàng (xét nghiệm, siêu âm, X-quang), chẩn đoán, quá trình điều trị và đơn thuốc. Sau đó, họ phải tự tổng hợp, chắt lọc và gõ thủ công báo cáo tóm tắt xuất viện vào form hệ thống. |
| **3. Bottleneck** | Việc tra cứu dữ liệu rải rác ở nhiều tab/phần mềm khác nhau và viết lại thành một đoạn văn bản tóm tắt y khoa mạch lạc tiêu tốn quá nhiều thời gian (thường từ 10-15 phút cho mỗi hồ sơ). Quá trình này hoàn toàn mang tính thủ tục hành chính, lặp đi lặp lại và dễ gây mệt mỏi (burnout) cho đội ngũ y tế. |
| **4. Business Impact** | Bác sĩ tốn quá nhiều thời gian cho giấy tờ hành chính thay vì thăm khám bệnh nhân. Về mặt vận hành, thủ tục xuất viện bị kéo dài khiến bệnh nhân phải chờ đợi lâu, làm giảm sự hài lòng (NPS) và làm chậm tốc độ luân chuyển giường bệnh (bed turnover rate) của bệnh viện. |
| **5. Success Metric** | Hệ thống tự động trích xuất và tạo bản nháp (draft) tóm tắt xuất viện trong thời gian **dưới 10 giây/hồ sơ**. Giảm thời gian hoàn thiện hồ sơ của bác sĩ từ 15 phút xuống **< 2 phút**. Tỷ lệ chấp nhận bản nháp của AI (ít hoặc không cần chỉnh sửa tay) đạt **> 85%**. |
| **6. Operational Boundary** | AI (ví dụ: thông qua Gemini API) được cấp quyền đọc văn bản EMR (sau khi đã che giấu/ẩn danh thông tin định danh bệnh nhân PII) và buộc phải trả về dữ liệu tuân thủ **cấu trúc JSON nghiêm ngặt** (bao gồm các keys cố định như: `symptoms`, `diagnosis`, `treatment_summary`, `prescriptions`, `follow_up_advice`) để map thẳng vào form UI của hệ thống. **TUYỆT ĐỐI KHÔNG:** AI không được phép đưa ra phác đồ điều trị mới, không thay đổi chẩn đoán, và không được phép tự động ký duyệt xuất viện. Toàn bộ đầu ra của mô hình phải qua bước Human-in-the-loop (HITL) để bác sĩ chỉnh sửa và phê duyệt cuối cùng. |

## 3.3. Future-State Flow & AI Fit (25 min)
Xác định mức AI Fit (AI-Fit Matrix): Giải pháp thuộc nhóm [x] LLM Feature (Áp dụng trực tiếp năng lực tóm tắt và xử lý ngôn ngữ của LLM vào một quy trình đã có cấu trúc tĩnh, không cần Agentic Loop vì quy trình y tế cần sự kiểm soát luồng nghiêm ngặt).

* **Vẽ Future-State Flow:

```text
┌──────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│ Bước 1       │     │ Bước 2       │     │ Bước 3       │     │ Bước 4       │
│ Bác sĩ bấm   │     │ 🔵 AI Step   │     │ 🟢 Human Step│     │ In giấy &    │
│ "Tạo tóm tắt │ ──→ │ API gọi LLM  │ ──→ │ (HITL) Bác sĩ│ ──→ │ Ký xuất viện │
│ xuất viện"   │     │ đọc EMR & trả│     │ đọc lại, sửa │     │ cho bệnh nhân│
│ trên app     │     │ về JSON draft│     │ & phê duyệt  │     │              │
└──────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
                            │
                            ▼
                     ↩️ Fallback:
                     Nếu API quá tải hoặc LLM từ chối 
                     trả lời do vi phạm safety filter, 
                     hệ thống hiển thị form trống để 
                     bác sĩ tự gõ tay như cũ.
```
---

## 🏁 Phase 5 — EVALUATE (Nhóm)
### AI Readiness Checklist:

1. [x] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test? (Hệ thống bệnh án điện tử nội bộ đã có sẵn hàng ngàn mẫu tóm tắt xuất viện chuẩn để làm few-shot prompting).

2. [x] Rủi ro khi AI sai có nằm trong tầm kiểm soát? (Được kiểm soát hoàn toàn thông qua cơ chế Human-in-the-loop, bác sĩ chịu trách nhiệm review cuối cùng).

3. [x] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ? (Rất sẵn sàng, vì bác sĩ đang trực tiếp "pain" với khối lượng giấy tờ hành chính hiện tại).

Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
1. [x] GO (Bắt đầu xây dựng Prototype): Bắt đầu phát triển với scope hẹp.
2. [ ] NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline).
3. [ ] NO-GO (Không khả thi / Rule-based tốt hơn).

**Justification (Lý giải quyết định dựa trên bằng chứng kỹ thuật và chi phí):**
Bài toán này mang lại giá trị vận hành nội bộ cực kỳ rõ ràng, giải phóng trực tiếp sức lao động chuyên môn của bác sĩ. Việc tổng hợp dữ liệu lâm sàng và viết tài liệu chuyên ngành (technical writing) là thế mạnh cốt lõi của các mô hình LLM hiện tại.

Về mặt kỹ thuật, việc gọi API LLM và định dạng kết quả dưới dạng JSON hoàn toàn dễ dàng tích hợp vào hệ thống microservices hiện tại của viện. Chi phí gọi API cho mỗi 1000 tokens văn bản rẻ hơn rất nhiều so với chi phí thời gian vàng ngọc của một bác sĩ chuyên khoa. Rủi ro về sai lệch y khoa (hallucination) được chặn đứng hoàn toàn bởi thiết kế bắt buộc bác sĩ phê duyệt (HITL), biến AI thành một "trợ lý nháp văn bản" an toàn và hiệu quả.