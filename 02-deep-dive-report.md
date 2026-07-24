# 🏗️ Phase 3 — DEEP-DIVE (Nhóm, 85 min)
Nhóm quyết định chọn bài toán "Vinmec - Soạn thảo tóm tắt hồ sơ xuất viện" để thực hiện Deep-Dive.

## 3.2. Problem Statement (6-field) & Metrics (15 min)
Điền đầy đủ 6 trường thông tin của bài toán:

| Field | Nội dung chi tiết |
| --- | --- |
| **1. Actor / Operator** | Nhân viên Phân tích Vận hành (Back-office / Operations Analyst) của Trung tâm điều hành Xanh SM. |
| **2. Current Workflow** | Hằng ngày, nhân viên truy xuất danh sách các cuốc xe bị hủy từ cơ sở dữ liệu. Họ phải tải xuống, mở từng file ghi âm cuộc gọi giữa tài xế và khách hàng hoặc đọc các ghi chú thô. Sau đó, họ nghe, ghi chú thủ công lý do chính (VD: tài xế đến trễ, khách đổi ý, app định vị sai) và tổng hợp vào file Excel để làm báo cáo cải tiến. |
| **3. Bottleneck** | Bước nghe lại file ghi âm và đọc hiểu chuỗi văn bản thô tốn cực kỳ nhiều thời gian (khoảng 10 phút/cuốc). Do giới hạn sức người, team hiện tại chỉ có thể lấy mẫu ngẫu nhiên (sample 5-10%) thay vì phân tích 100% dữ liệu cuốc hủy. |
| **4. Business Impact** | Việc chỉ phân tích mẫu ngẫu nhiên dẫn đến bỏ lọt các lỗi mang tính hệ thống (ví dụ: rớt mạng nội bộ ở một khu vực, hoặc lỗi định vị GPS sai lệch). Hậu quả là tỷ lệ hủy chuyến không được cải thiện tận gốc, gây rò rỉ doanh thu, lãng phí thời gian di chuyển của tài xế và giảm SLA dịch vụ. |
| **5. Success Metric** | Hệ thống có khả năng tự động xử lý và phân loại **100%** cuốc hủy trong ngày. Thời gian trích xuất và gán nhãn giảm từ 10 phút xuống **dưới 30 giây/cuốc**. Độ chính xác của việc phân loại đạt ngưỡng **> 90%** so với con người. |
| **6. Operational Boundary** | AI được phép chuyển đổi giọng nói thành văn bản, sử dụng LLM API (ví dụ: Gemini) để tóm tắt transcript và gán nhãn vào 10 danh mục có sẵn. Bắt buộc phải trả về dữ liệu định dạng **cấu trúc JSON nghiêm ngặt** để ghi vào cơ sở dữ liệu (như PostgreSQL). <br/>**TUYỆT ĐỐI KHÔNG:** AI không được quyền tự động ban hành quyết định xử phạt tài xế hoặc hoàn tiền cho khách hàng dựa trên lý do hủy. Mọi quyết định liên quan đến tài chính/nhân sự phải do con người duyệt. |

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