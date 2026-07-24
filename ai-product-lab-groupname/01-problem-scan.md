# BÁO CÁO TOÀN DIỆN: PHÂN TÍCH BOTTLENECK VẬN HÀNH & CHI TIẾT 3 QUICK PROBLEM CARDS CHO VINGROUP

**Đơn vị thực hiện:** AI Engineering Team - Vin Smart Future (Vingroup)  
**Khối trọng điểm phân tích:** VinFast (Xe điện & Hạ tầng) & VinMed / Vinmec (Y tế)  
**Khung phân tích:** 4 Lenses AI Framework (Repetitive, Time-consuming, AI-upgrade, Stakeholder Pain)

---

## I. TỔNG QUAN & PHƯƠNG PHÁP TIẾP CẬN

Nhằm nâng cao hiệu suất vận hành và giảm thiểu tối đa các rò rỉ tài chính / năng suất trong hệ sinh thái Vingroup, đội ngũ **Vin Smart Future** đã tiến hành rà soát chuyên sâu chuỗi quy trình nghiệp vụ tại hai khối đơn vị thành viên trọng điểm: **VinFast** và **VinMed (Vinmec)**.

Quá trình quét bottleneck vận hành được thực hiện dựa trên **4 Lenses AI Framework**:

1. **Lặp lại (Repetitive):** Các tác vụ có tính chu kỳ, tần suất cao, theo quy tắc cố định.
2. **Tốn thời gian (Time-consuming):** Các mắt xích đòi hỏi nhân sự phải thao tác thủ công, xử lý lượng dữ liệu lớn.
3. **AI có thể làm tốt hơn (AI-upgrade):** Các quy trình hiện có độ trễ cao, phản hồi rập khuôn hoặc dễ sai sót do con người quá tải.
4. **Pain từ Stakeholder (Stakeholder Pain):** Điểm nghẽn trực tiếp tạo ra sự không hài lòng từ phía khách hàng (chủ xe, bệnh nhân) hoặc nhân viên thực địa (kỹ thuật viên, bác sĩ, điều dưỡng, tài xế).

---

## II. QUÉT BOTTLENECK VẬN HÀNH THỰC TẾ (5 QUY TRÌNH NGHIỆP VỤ)

### 1. VinFast: Chẩn đoán sự cố pin & lỗi điện tử tại Xưởng dịch vụ (After-sales Diagnostics)

- **Bối cảnh & Quy trình thủ công:** Khi xe điện VinFast gặp sự cố về BMS (Battery Management System), sụt pin bất thường, lỗi mạng CAN Bus hoặc lỗi ECU, kỹ thuật viên (KTV) phải cắm thiết bị đọc mã DTC. Sau đó, KTV trích xuất hàng trăm megabyte dữ liệu log dạng _time-series_, tra cứu thủ công sơ đồ mạch điện và tài liệu kỹ thuật để tìm nguyên nhân gốc (Root Cause).
- **Quét qua 4 Lenses:**
  - **Repetitive:** KTV lặp lại các bước trích xuất log, tra cứu sơ đồ mạch và đo đạc thông số trên từng xe vào xưởng mỗi ngày.
  - **Time-consuming:** Mất từ **1.5 đến 3 tiếng/xe** cho các ca lỗi điện tử phức tạp hoặc chẩn đoán chai/lỗi cell pin đơn lẻ.
  - **AI-upgrade:** Ứng dụng **Time-series Anomaly Detection + LLM Diagnostics Agent** để phân tích log BMS/ECU tức thì (trong 30 giây), đối soát tự động với sơ đồ mạch và xuất quy trình sửa chữa khuyến nghị.
  - **Stakeholder Pain:** Khách hàng phải gửi xe lại xưởng 1–2 ngày chỉ để chờ chẩn đoán lỗi, gây bức xúc và tạo áp lực quá tải lên diện tích khoang sửa chữa (bay) tại xưởng.
- **Tổn thất ước tính:** Lãng phí **25–30% quỹ thời gian** của KTV bậc cao vào việc "mò lỗi" thủ công. Giảm **15–20% năng suất thông qua (throughput)** của mỗi khoang dịch vụ.

---

### 2. VinFast: Thẩm định & Xác minh yêu cầu bảo hành linh kiện toàn cầu (Warranty Claim Verification)

- **Bối cảnh & Quy trình thủ công:** Bộ phận Warranty Operations xử lý hàng nghìn yêu cầu bảo hành phụ tùng/linh kiện gửi về từ đại lý và xưởng dịch vụ trên toàn cầu. Nhân sự thẩm định phải mở từng hồ sơ, soi ảnh chụp linh kiện hỏng, đối chiếu số VIN, hóa đơn vật tư và lịch sử bảo dưỡng xe trên ERP để quyết định duyệt chi trả.
- **Quét qua 4 Lenses:**
  - **Repetitive:** Đọc chứng từ, kiểm tra mã linh kiện, so sánh ảnh chụp chi tiết hỏng hóc lặp đi lặp lại hàng nghìn lần mỗi tháng.
  - **Time-consuming:** Trung bình mất **15–25 phút/hồ sơ** để xác minh tính hợp lệ và trung thực của linh kiện cần thay thế.
  - **AI-upgrade:** Tích hợp **Computer Vision (CV)** thẩm định vết nứt/hỏng hóc thực tế trên linh kiện kết hợp **OCR/NLP** đối soát chứng từ và mô hình **Fraud Detection AI** để phát hiện gian lận, khai khống.
  - **Stakeholder Pain:** Đại lý/Xưởng dịch vụ bị đọng vốn do thời gian chờ VinFast phê duyệt chi trả bảo hành kéo dài (14–30 ngày).
- **Tổn thất ước tính:** Rò rỉ tài chính ước tính **3–5% tổng ngân sách bảo hành hàng năm** do phê duyệt sai lệch, bỏ sót gian lận từ đại lý/đối tác hoặc chi phí nhân lực thẩm định quá lớn.

---

### 3. VinMed (Vinmec): Tầm soát & Phân loại ảnh chụp y tế tiền chẩn đoán (Radiology Triage & Draft Reporting)

- **Bối cảnh & Quy trình thủ công:** Tại Vinmec, bác sĩ Chẩn đoán hình ảnh (CĐHA) phải phân tích hàng trăm lát cắt CT, MRI hoặc phim X-quang mỗi ngày. Bác sĩ thực hiện đo đạc kích thước tổn thương/khối u bằng công cụ thước đo thủ công trên phần mềm PACS và nhập (hoặc đọc cho trợ lý gõ) toàn bộ bản báo cáo mô tả kết quả.
- **Quét qua 4 Lenses:**
  - **Repetitive:** Đo kích thước tổn thương, ghi chép chỉ số và nhập dữ liệu kết quả theo biểu mẫu y khoa chuẩn.
  - **Time-consuming:** Mất **15–30 phút/ca** CT/MRI phức tạp để bác sĩ xem qua từng lát cắt và hoàn thành văn bản kết quả chẩn đoán.
  - **AI-upgrade:** **Medical Imaging AI (Deep Learning)** tự động khoanh vùng tổn thương, gợi ý kích thước 3D, phân loại độ nguy cơ và điền trước bản nháp báo cáo (Draft Report) để bác sĩ chỉ cần kiểm tra và ký duyệt.
  - **Stakeholder Pain:** Bệnh nhân khám ngoại trú phải chờ 2–3 tiếng mới có kết quả CĐHA; Bác sĩ CĐHA chịu áp lực công việc lớn, tăng nguy cơ bỏ sót tổn thương nhỏ khi làm việc ca đêm quá tải.
- **Tổn thất ước tính:** Công suất khai thác hệ thống máy CT/MRI bị giới hạn (chỉ đạt **60–70% công suất tối đa/ngày**). Thời gian quay vòng kết quả kéo dài làm giảm **10–15% chỉ số hài lòng (CSAT)** của bệnh nhân.

---

### 4. VinMed (Vinmec): Tổng hợp bệnh án & Lập kế hoạch theo dõi sau xuất viện (EHR Synthesis & Post-Discharge Care)

- **Bối cảnh & Quy trình thủ công:** Khi bệnh nhân xuất viện, bác sĩ/điều dưỡng phải truy xuất dữ liệu từ nhiều hệ thống chuyên khoa khác nhau (xét nghiệm, phẫu thuật, đơn thuốc) để viết bản tóm tắt hồ sơ bệnh án (EHR Summary) và dặn dò lịch tái khám. Sau đó, bộ phận CSKH gọi điện thủ công để nhắc lịch và thăm hỏi tình hình sức khỏe.
- **Quét qua 4 Lenses:**
  - **Repetitive:** Đặt câu hỏi theo dõi chỉ số sức khỏe tiêu chuẩn sau phẫu thuật và nhắc lịch tái khám theo kịch bản cố định.
  - **Time-consuming:** Mất **30–45 phút/bệnh nhân** để điều dưỡng/bác sĩ tổng hợp xong một hồ sơ tóm tắt xuất viện hoàn chỉnh.
  - **AI-upgrade:** **LLM Medical Agent** tự động trích xuất EHR để tạo bản hướng dẫn chăm sóc cá nhân hóa (dạng ngôn ngữ bình dân, dễ hiểu) và kích hoạt **AI Voicebot/Chatbot** tự động tương tác theo dõi qua ứng dụng Vinmec App/Zalo.
  - **Stakeholder Pain:** Bệnh nhân quên phác đồ uống thuốc hoặc hướng dẫn vận động tại nhà; Bác sĩ mất nhiều thời gian cá nhân trả lời tin nhắn lẻ tẻ của bệnh nhân.
- **Tổn thất ước tính:** Điều dưỡng tiêu tốn **~20% quỹ thời gian làm việc** vào tác vụ hành chính nhập liệu. Tỷ lệ tái nhập viện không mong muốn trong vòng 30 ngày (Unplanned Readmission) ở mức **7–10%** do bệnh nhân tuân thủ phác đồ kém.

---

### 5. VinFast: Bảo trì dự đoán & Điều phối tải cho Hệ thống Trạm sạc (Predictive Maintenance for EV Chargers)

- **Bối cảnh & Quy trình thủ công:** Đội ngũ vận hành trạm sạc VinFast hiện đang ứng phó theo cơ chế phản ứng (Reactive Maintenance) – khi trụ sạc báo lỗi đỏ trên dashboard, bị ngắt kết nối hoặc có tài xế Xanh SM / chủ xe phản ánh thì mới điều động kỹ thuật viên (KTV) đến địa bàn kiểm tra.
- **Quét qua 4 Lenses:**
  - **Repetitive:** Nhân viên vận hành lọc thủ công các thông báo lỗi ngắt kết nối và phân loại mức độ sự cố trên hệ thống hàng ngày.
  - **Time-consuming:** Mất trung bình **4–8 tiếng** từ lúc trụ sạc phát sinh sự cố đến khi KTV tiếp cận và xử lý xong tại hiện trường.
  - **AI-upgrade:** **IoT Telemetry AI Model** phân tích dữ liệu dòng điện, nhiệt độ súng sạc, độ biến động điện áp theo thời gian thực để dự báo nguy cơ hỏng hóc tụ điện/mạch sạc trước **48–72 giờ**.
  - **Stakeholder Pain:** Tài xế Xanh SM và chủ xe VinFast di chuyển đến trạm sạc nhưng cắm sạc không vào hoặc bị ngắt giữa chừng, gây ùn tắc tại trạm sạc trọng điểm.
- **Tổn thất ước tính:** Tỷ lệ Downtime trụ sạc trung bình **3–5%**, làm giảm trực tiếp doanh thu bán điện sạc và giảm **5–8% số chuyến phục vụ/ca** của tài xế Xanh SM. Chi phí ứng cứu khẩn cấp cao hơn **2.5 lần** so với bảo trì định kỳ.

---

## III. MA TRẬN ĐÁNH GIÁ ƯU TIÊN (QUICK-WIN MATRIX)

|  STT  | Tên quy trình / Bài toán AI                  | Đơn vị  |       Mức độ phức tạp AI        |      Tác động tài chính & Vận hành       | Thời gian triển khai dự kiến |
| :---: | :------------------------------------------- | :-----: | :-----------------------------: | :--------------------------------------: | :--------------------------: |
| **1** | **Chẩn đoán sự cố pin & lỗi điện tử xe**     | VinFast |   Trung bình (_Time-series_)    |   **Rất cao** (Tăng xưởng throughput)    |   Quick-win (3 – 5 tháng)    |
| **2** | **Thẩm định & Tự động duyệt bảo hành**       | VinFast |   Cao (_CV + OCR + Fraud AI_)   |    **Rất cao** (Chặn rò rỉ ngân sách)    |    Dài hạn (6 – 9 tháng)     |
| **3** | **Tầm soát & Nháp báo cáo CĐHA**             | VinMed  |    Cao (_Medical Vision AI_)    |      **Cao** (Tối ưu công suất máy)      |   Trung hạn (5 – 7 tháng)    |
| **4** | **Tóm tắt EHR & CSKH tự động sau xuất viện** | VinMed  |  Trung bình (_LLM + Voicebot_)  |  **Trung bình** (Tăng CSAT & Tái khám)   |   Quick-win (3 – 4 tháng)    |
| **5** | **Bảo trì dự đoán hạ tầng Trạm sạc**         | VinFast | Trung bình (_IoT Telemetry AI_) | **Cao** (Giảm Downtime & Tối ưu Xanh SM) |   Quick-win (3 – 5 tháng)    |

---

## IV. CHI TIẾT 3 QUICK PROBLEM CARDS TIỀM NĂNG NHẤT

Below are the 3 detailed Quick Problem Cards for the top implementation targets:

### PROBLEM CARD 01: Chẩn đoán sự cố Pin & Lỗi điện tử xe điện (After-sales Diagnostics)

- **Công ty thành viên:** VinFast Service (Khối Dịch vụ Sau bán hàng)
- **Tác nhân chịu đau (Actor/Operator):** Kỹ thuật viên (KTV) bậc cao tại các Showroom / Xưởng dịch vụ VinFast.

#### 1. Sơ đồ quy trình thủ công hiện tại

```text
[Nhận xe lỗi tại xưởng]
   └──> [Cắm thiết bị OBD đọc mã lỗi DTC]
           └──> [Trích xuất file Log BMS/ECU (~100MB-500MB)]
                   └──> [TRA CỨU THỦ CÔNG: Soi log time-series + Đối soát sơ đồ mạch]
                           └──> [Đo đạc vật lý từng mạch/cell pin bằng đồng hồ]
                                   └──> [Xác định nguyên nhân gốc & Sửa chữa]
```

#### 2. Bước tốn thời gian & gây lỗi nhiều nhất

- **Bước:** Tra cứu & Phân tích dữ liệu Log time-series kết hợp đối soát sơ đồ mạch điện.
- **Thời gian xử lý ước tính:** **1.5 đến 3 tiếng/xe** đối với các ca lỗi điện tử phức tạp hoặc chẩn đoán lệch áp/chai cell pin.
- **Rủi ro/Gây lỗi:** KTV quá tải dễ đoán sai nguyên nhân gốc, dẫn đến thay thế nhầm linh kiện đắt tiền hoặc ngâm xe của khách hàng quá lâu.

#### 3. Bước AI tham gia giải quyết

AI tự động ingest file Log BMS/ECU, phân tích biến động bất thường (Anomaly Detection) trên chuỗi thời gian, tự động tra cứu Vector DB chứa sơ đồ mạch điện/tri thức kỹ thuật và xuất kết quả chẩn đoán Root-Cause kèm vị trí lỗi tức thì.

#### 4. Metric đo thành công

- **Thời gian chẩn đoán lỗi:** Giảm từ **120 phút/xe** xuống dưới **5 phút/xe** (Giảm **>95%** thời gian mò lỗi).
- **Năng suất thông qua (Throughput) của xưởng:** Tăng **20%** số lượng xe phục vụ/ngày trên mỗi khoang sửa chữa.

#### 5. Đề xuất kiến trúc sơ bộ

- **Ingestion Layer (No AI):** Parsers tự động đọc file log Binary/CSV trích xuất từ OBD.
- **Filtering Layer (Rule):** Rule-engine lọc các mã lỗi DTC chuẩn đã có sẵn quy trình xử lý cố định.
- **Anomaly Detection Module (ML):** Mô hình _Time-series Anomaly Detection (Isolation Forest / Autoencoder)_ phát hiện điểm sụt áp/nhiệt độ bất thường.
- **Knowledge Base (RAG):** Vector Database chứa toàn bộ Sơ đồ mạch điện, Manual hướng dẫn kỹ thuật và Lịch sử sửa chữa.
- **Orchestrator & Output (Agent / LLM):** _Diagnostic LLM Agent_ tổng hợp anomaly + RAG để xuất báo cáo Root-Cause kèm checklist sửa chữa cho KTV.

---

### PROBLEM CARD 02: Tóm tắt bệnh án & Chăm sóc tự động sau xuất viện (Post-Discharge Care)

- **Công ty thành viên:** Bệnh viện Đa khoa Quốc tế Vinmec (VinMed)
- **Tác nhân chịu đau (Actor/Operator):** Bác sĩ điều trị, Điều dưỡng phụ trách xuất viện và Nhân viên CSKH.

#### 1. Sơ đồ quy trình thủ công hiện tại

```text
[Bệnh nhân hoàn thành điều trị]
   └──> [Mở các hệ thống EHR/HIS phân tán]
           └──> [TỔNG HỢP THỦ CÔNG: Đọc dữ liệu Xét nghiệm, Phẫu thuật, Đơn thuốc]
                   └──> [Gõ bản Tóm tắt xuất viện & Soạn dặn dò]
                           └──> [In hồ sơ & Dặn bệnh nhân trực tiếp]
                                   └──> [CSKH gọi điện thủ công nhắc lịch tái khám]
```

#### 2. Bước tốn thời gian & gây lỗi nhiều nhất

- **Bước:** Trích xuất, tổng hợp thủ công dữ liệu y tế từ nhiều phân hệ và biên soạn bản dặn dò cá nhân hóa.
- **Thời gian xử lý ước tính:** **30 đến 45 phút/bệnh nhân**.
- **Rủi ro/Gây lỗi:** Dùng thuật ngữ y khoa quá chuyên môn khiến bệnh nhân không hiểu rõ cách chăm sóc tại nhà, dẫn đến uống sai đơn thuốc hoặc bỏ lịch tái khám.

#### 3. Bước AI tham gia giải quyết

LLM tự động tổng hợp dữ liệu EHR thành bản tóm tắt y khoa cho bác sĩ ký duyệt, đồng thời dịch chuyển nội dung dặn dò sang ngôn ngữ bình dân cá nhân hóa và kích hoạt AI Agent tự động theo dõi bệnh nhân qua Zalo/Vinmec App.

#### 4. Metric đo thành công

- **Thời gian lập hồ sơ xuất viện:** Giảm từ **35 phút** xuống dưới **3 phút/bệnh nhân** (Giảm **>90%** thời gian hành chính).
- **Tỷ lệ tái nhập viện không mong muốn (Unplanned Readmission 30 ngày):** Giảm từ **8%** xuống dưới **5%**.

#### 5. Đề xuất kiến trúc sơ bộ

- **Data Integration (No AI):** ETL Pipeline kết nối EHR/HIS theo chuẩn dữ liệu y tế FHIR.
- **Data Masking & Safety (Rule):** Rule-engine làm sạch, ẩn danh thông tin định danh cá nhân (De-identification) để tuân thủ bảo mật y tế.
- **Summarization Engine (LLM):** _Medical LLM_ (được fine-tune hoặc RAG với Y văn Vinmec) trích xuất bệnh án và tạo bản dặn dò bình dân.
- **Patient Engagement (Agent):** _Follow-up Agent_ kết hợp AI Voicebot/Chatbot tự động tương tác, nhắc lịch tái khám và thu thập chỉ số sức khỏe định kỳ của bệnh nhân.

---

### PROBLEM CARD 03: Bảo trì dự đoán & Tối ưu vận hành Hạ tầng Trạm sạc (Predictive Maintenance)

- **Công ty thành viên:** VinFast Infrastructure / Vận hành Hạ tầng Trạm sạc (phục vụ Xanh SM & Chủ xe cá nhân)
- **Tác nhân chịu đau (Actor/Operator):** Đội ngũ Vận hành Trung tâm & Kỹ thuật viên (KTV) bảo trì trạm sạc thực địa.

#### 1. Sơ đồ quy trình thủ công hiện tại

```text
[Trụ sạc bị hỏng/ngắt kết nối]
   └──> [Hệ thống đẩy Alert đỏ lên Dashboard]
           └──> [NHÂN VIÊN LỌC VÀ XÁC MINH LỖI THỦ CÔNG]
                   └──> [Tạo Ticket & Gọi điện điều động KTV]
                           └──> [KTV di chuyển đến trạm]
                                   └──> [Mở tủ sạc đo đạc & Sửa chữa sự cố]
```

#### 2. Bước tốn thời gian & gây lỗi nhiều nhất

- **Bước:** Lọc cảnh báo thủ công và phát hiện sự cố theo cơ chế thụ động (chỉ xử lý khi trụ đã ngắt kết nối hoặc có phàn nàn từ tài xế).
- **Thời gian xử lý ước tính:** **4 đến 8 tiếng Downtime** cho mỗi sự cố trụ sạc.
- **Rủi ro/Gây lỗi:** Làm gián đoạn hoạt động đón khách của tài xế Xanh SM, gây ùn tắc tại các trạm sạc trọng điểm.

#### 3. Bước AI tham gia giải quyết

Mô hình AI phân tích dữ liệu Telemetry dòng điện, nhiệt độ súng sạc, điện áp theo thời gian thực để phát hiện các dấu hiệu suy hao linh kiện và dự báo lỗi trước 48–72 giờ, tự động điều động KTV đến bảo trì phòng ngừa.

#### 4. Metric đo thành công

- **Tỷ lệ Downtime trụ sạc đột xuất:** Giảm từ **4.5%** xuống dưới **1.5%** (Giảm **66%** thời gian ngừng hoạt động).
- **Cảnh báo trước sự cố:** Chuyển từ **0 giờ (thụ động)** sang chủ động trước **48 giờ**.

#### 5. Đề xuất kiến trúc sơ bộ

- **Data Streaming (No AI):** Kafka / IoT Hub tiếp nhận dữ liệu Telemetry time-series tần suất cao từ các trụ sạc.
- **Emergency Cut-off (Rule):** Hard-rules lập tức ngắt điện tự động nếu phát hiện quá nhiệt/quá áp vượt ngưỡng an toàn.
- **Predictive Model (ML):** Mô hình _Temporal Fusion Transformer / XGBoost_ phân tích chuỗi thời gian để tính toán xác suất hỏng hóc trong 72h tới.
- **Smart Dispatching (Agent):** _Route & Operations Optimization Agent_ tự động gộp các ticket bảo trì dự đoán và đề xuất lộ trình di chuyển tối ưu nhất cho KTV thực địa.

---

## V. ĐỀ XUẤT LỘ TRÌNH THỰC THI CHO VIN SMART FUTURE

1. **Giai đoạn Pilot (Tháng 1 – Month 3):**
   - Triển khai POC (Proof of Concept) cho bài toán **Chẩn đoán sự cố pin (Problem Card 01)** và **Tóm tắt EHR sau xuất viện (Problem Card 02)**.
2. **Giai đoạn Mở rộng (Tháng 4 – Month 6):**
   - Đưa vào vận hành chính thức 2 bài toán Quick-win.
   - Xây dựng luồng thu thập dữ liệu IoT và triển khai POC cho **Bảo trì trạm sạc (Problem Card 03)** và bài toán **Tầm soát CĐHA**.
3. **Giai đoạn Chuẩn hóa & Nhân rộng (Tháng 7 – Month 9):**
   - Triển khai mô hình **Thẩm định bảo hành chống gian lận VinFast** trên quy mô toàn cầu.
