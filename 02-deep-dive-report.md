Phase 3:

**Case study lựa chọn:** Nâng cấp Chatbot CSKH Vinhomes (Bài toán #2)

## 3.1. Current-State Workflow Mapping (25 min)
**Tổng cộng thời gian:** **~15 phút/lượt** (Bao gồm cả thời gian khách chờ và thời gian Agent tra cứu).

* **Bước 1:** Cư dân mở App Vinhomes, chọn mục "Hỗ trợ" và nhập câu hỏi. 🔄 *(Handoff: Cư dân -> Hệ thống)*
* **Bước 2:** Chatbot cũ (Rule-based) yêu cầu chọn menu 1-2-3. Cư dân không thấy đúng ý nên gõ câu hỏi phức tạp (VD: "Tôi muốn đăng ký vân tay cho người thân đến chơi 1 tháng thì làm sao?").
* **Bước 3:** 🔴 **Bottleneck 1:** Chatbot không hiểu, báo lỗi *"Xin lỗi tôi không hiểu"* và tự động chuyển ticket sang Tổng đài viên. Khách hàng phải vào hàng đợi (chờ 5-10 phút).
* **Bước 4:** Tổng đài viên (Agent) tiếp nhận ticket, đọc tin nhắn. 🔄 *(Handoff: Hệ thống -> Agent)*
* **Bước 5:** 🔴 **Bottleneck 2:** Agent phải tra cứu thủ công trong hàng chục file PDF Cẩm nang cư dân/Quy định nội khu để tìm thủ tục chính xác.
* **Bước 6:** Agent gõ lại câu trả lời, copy-paste link biểu mẫu gửi cho cư dân.

---

## 3.2. Problem Statement (6-field) & Metrics (15 min)

| Field | Nội dung chi tiết |
|---|---|
| **1. Actor / Operator** | Cư dân (Người đặt câu hỏi) và Nhân viên Tổng đài CSKH Vinhomes (Người xử lý). |
| **2. Current Workflow** | Khách chat -> Chatbot cũ không hiểu -> Chuyển ticket cho Agent -> Agent tra cứu thủ công cẩm nang dạng file PDF -> Gõ phản hồi và gửi biểu mẫu. |
| **3. Bottleneck** | Chatbot hiện tại quá cứng nhắc, không có khả năng hiểu ngôn ngữ tự nhiên. Agent tốn quá nhiều thời gian để tra cứu tài liệu nội bộ và soạn câu trả lời cho các câu hỏi lặp đi lặp lại. |
| **4. Business Impact** | Tăng tỷ lệ phàn nàn của cư dân do thời gian chờ (Queue time) lâu. Chi phí vận hành Call Center cao, Agent bị quá tải (đặc biệt vào mùa cao điểm bàn giao nhà hoặc thu phí). |
| **5. Success Metric** | Tăng tỷ lệ tự động giải quyết (Deflection Rate) của AI từ 20% lên **75%**. Giảm thời gian phản hồi (Response Time) xuống **dưới 10 giây/ticket**. |
| **6. Operational Boundary** | **Được phép:** Trả lời các thông tin nằm trong cẩm nang, hướng dẫn quy trình, cấp link biểu mẫu.<br>**KHÔNG được làm:** Tiết lộ thông tin cá nhân của cư dân khác, tự ý hứa hẹn đền bù thiệt hại vật chất.<br>**Điểm cần duyệt:** Các khiếu nại gay gắt có từ khóa nhạy cảm (VD: "kiện", "báo chí") phải chuyển cho con người xử lý. |

---

## 3.3. Future-State Flow & AI Fit (25 min)

**Xác định mức AI Fit (AI-Fit Matrix):** 
[ ] Rule / State-Machine 
[ ] LLM Feature 
[x] Agentic Loop (Kết hợp RAG để truy xuất tài liệu và Agent để quyết định chuyển tiếp)

**Future-State Flow:**
* **Bước 1:** Cư dân nhập câu hỏi tự do vào App Vinhomes.
* **Bước 2:** 🔵 **AI Step (Router):** AI phân tích cảm xúc (Sentiment) và ý định của câu hỏi.
* **Bước 3:** 🔵 **AI Step (RAG & Generate):** AI tự động tìm kiếm trong kho Cẩm nang cư dân, trích xuất đúng quy định và soạn câu trả lời tự nhiên, thân thiện kèm link biểu mẫu. Thời gian xử lý: 3 giây.
* **Bước 4:** 🟢 **Human Step (HITL):** Nếu ở Bước 2, AI phát hiện khách hàng đang rất tức giận (Negative Sentiment) hoặc dùng từ ngữ nhạy cảm, AI sẽ không tự trả lời mà tóm tắt sự việc, đẩy ticket lên cho Ca trưởng/Agent duyệt trước khi gửi.
* **Bước 5:** ↩️ **Fallback:** Nếu câu hỏi của khách nằm ngoài dữ liệu Cẩm nang (AI có độ tự tin thấp dưới ngưỡng 80%), AI tự động kích hoạt kịch bản: *"Dạ thông tin này hiện chưa có trong hệ thống, em xin phép nối máy với tư vấn viên ngay lập tức ạ"* và thực hiện Handoff cho con người.

Phase 5: 
### AI Readiness Checklist:
1. [x] Chúng tôi có sẵn dữ liệu mẫu/logs sạch để test? *(Kho dữ liệu chat lịch sử và các bộ tài liệu Cẩm nang cư dân dạng PDF/Word đã được chuẩn hóa).*
2. [x] Rủi ro khi AI sai có nằm trong tầm kiểm soát (qua HITL hoặc Fallback)? *(Có luồng tự động chuyển ticket cho Agent khi AI có độ tự tin <80% hoặc phát hiện khách hàng đang bức xúc).*
3. [x] Stakeholders sẵn sàng thay đổi quy trình làm việc cũ? *(Khối CSKH đang gặp áp lực quá tải và rất cần giải pháp giảm tải số lượng ticket lặp lại hằng ngày).*

### Quyết định cuối cùng của Ban Giám Đốc Vin Smart Future:
[x] **GO (Bắt đầu xây dựng Prototype):** Bắt đầu phát triển với scope hẹp.
[ ] **NOT YET (Cần tích lũy thêm dữ liệu/xác lập baseline):** Trì hoãn để chuẩn bị thêm.
[ ] **NO-GO (Không khả thi / Rule-based tốt hơn):** Hủy bỏ dự án AI này.