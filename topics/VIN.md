# Lĩnh vực: VIN - Giáo dục Đại học & Quản trị Học thuật

> Tổng số đề tài: **16 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `VIN-01` | [Trợ lý đa tác tử đồng thiết kế chương trình đào tạo](#vin-01) |
| `VIN-02` | [Trợ lý AI dạy học Socratic – Động cơ hội thoại thời gian thực](#vin-02) |
| `VIN-03` | [ConsistencyGuard – AI Agent Phát Hiện Bất Nhất Dữ Liệu Giữa Các Báo Cáo Trong Fabric Dashboard](#vin-03) |
| `VIN-04` | [Hệ thống tuyển sinh/ Đào tạo 20K AI](#vin-04) |
| `VIN-05` | [Nền tảng Quản lý dự án nghiên cứu](#vin-05) |
| `VIN-06` | [Siêu ứng dụng khuôn viên số (Campus Super-App)](#vin-06) |
| `VIN-07` | [Nền tảng dữ liệu Datalake/ Datalake House](#vin-07) |
| `VIN-08` | [Tự động hóa quy trình phê duyệt Microsoft power automate](#vin-08) |
| `VIN-09` | [Nâng cấp e-hiring](#vin-09) |
| `VIN-10` | [Trợ lý AI cho cổng thông tin học giả của trường đại học](#vin-10) |
| `VIN-11` | [AI Report Factory – Một nguồn dữ liệu, nhiều báo cáo cho nhiều đối tượng](#vin-11) |
| `VIN-12` | [Rexcel – Nền tảng thiết kế đề cương nghiên cứu có hỗ trợ AI](#vin-12) |
| `VIN-13` | [Mô phỏng ca học tập bằng AI cho thư viện điện tử Dịch tễ học và học phần Liêm chính nghiên cứu](#vin-13) |
| `VIN-14` | [Trợ lý tri thức AI cho thư viện điện tử Dịch tễ học và học phần Liêm chính nghiên cứu](#vin-14) |
| `VIN-15` | [Hệ thống hỗ trợ thực tập bằng AI](#vin-15) |
| `VIN-16` | [Trợ lý phòng thí nghiệm thông minh cho quản lý nghiên cứu](#vin-16) |

---

## [VIN-01] Trợ lý đa tác tử đồng thiết kế chương trình đào tạo

### 📝 Mô tả đề tài
📍 Thực trạng: Việc thiết kế và cập nhật chương trình đào tạo tại trường đại học đòi hỏi đối chiếu đồng thời chuẩn đầu ra (PLO/CLO), khung kiểm định quốc tế (AUN-QA, ABET), đề cương hàng chục học phần và nhu cầu thị trường lao động; làm thủ công rời rạc giữa các giảng viên rất dễ dẫn đến trùng lặp nội dung, lệch chuẩn đánh giá hoặc thiếu hụt kỹ năng thực tế.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để hệ thống đa tác tử đồng thiết kế và kiểm định chương trình đào tạo một cách toàn diện: từ phân tích chuẩn đầu ra, khởi tạo đề cương học phần, kiểm tra ma trận căn chỉnh chuẩn kiểm định (Constructive Alignment & AUN-QA) đến tổng hợp phản hồi người học và xu hướng tuyển dụng để phát hiện khoảng trống kiến thức, mô phỏng tác động khi thay đổi cấu trúc học phần và đề xuất lộ trình cải tiến khả thi.

🔒 Ràng buộc: Mọi đề xuất chỉnh sửa chuẩn đầu ra hoặc cấu trúc học phần bắt buộc qua Hội đồng học thuật phê duyệt (HITL); tách biệt kiểm tra tính đầy đủ của ma trận PLO-CLO-Assessment và ràng buộc số tín chỉ bằng quy tắc code xác định khỏi suy luận của LLM; đánh giá chất lượng trên bộ đề cương thực tế công khai (MIT OCW / khung kỹ năng ESCO).

### 🛠️ Tech Stack
• LangGraph / CrewAI
• RAG trên kho tài liệu học thuật
• GPT-4o
• tìm kiếm embedding
• quy trình xuất PDF
• Dữ liệu & benchmark thực tế tham chiếu: Bộ đề cương học phần mở MIT OpenCourseWare (OCW), khung kỹ năng nghề nghiệp ESCO / O*NET và bộ tiêu chuẩn kiểm định AUN-QA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Ứng dụng web (≥2 vai trò: Giảng viên thiết kế & Hội đồng thẩm định) sinh gói chương trình đào tạo hoàn chỉnh (đề cương học phần, kế hoạch bài giảng, mục tiêu học tập, kế hoạch đánh giá).
• Kiểm tra tự động ma trận căn chỉnh chuẩn đầu ra (PLO–CLO), báo cáo khoảng trống kiến thức và có luồng HITL phê duyệt.

Nâng cao:
• Kiến trúc Multi-Agent có vòng lặp phản biện chéo (Planner – Curriculum Author – AUN-QA Auditor – Market Alignment Critic) kèm truy vết suy luận.
• Đối chiếu trực tiếp với dữ liệu nhu cầu kỹ năng thị trường (ESCO/O*NET), mô phỏng tác động khi thêm/bớt học phần và đánh giá định lượng độ phủ chuẩn đầu ra.

---

## [VIN-02] Trợ lý AI dạy học Socratic – Động cơ hội thoại thời gian thực

### 📝 Mô tả đề tài
📍 Thực trạng: Người học khi gặp bài tập khó thường có xu hướng hỏi AI để chép ngay lời giải cuối cùng dẫn đến học vẹt, trong khi giảng viên không thể kèm cặp Socratic 1-1 theo thời gian thực cho hàng trăm sinh viên có lỗ hổng kiến thức và kiểu hiểu sai (misconception) khác nhau.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng động cơ hội thoại dạy học Socratic thời gian thực kết hợp theo dõi trạng thái kiến thức (Bayesian/Deep Knowledge Tracing): thay vì đưa đáp án, tác tử chẩn đoán chính xác quan niệm sai từ lập luận của người học, điều chỉnh chiến lược đặt câu hỏi gợi mở theo vùng phát triển gần và cập nhật đồ thị năng lực sau mỗi lượt tương tác để giúp người học tự tìm ra lời giải.

🔒 Ràng buộc: Guardrail sư phạm bắt buộc đảm bảo 0% tiết lộ trực tiếp lời giải hoàn chỉnh khi người học chưa tự suy luận qua các bước gợi mở; phần cập nhật xác suất thành thạo kiến thức (BKT) phải tính bằng mô-đun toán học xác định; kiểm chứng độ trễ hội thoại thời gian thực và tỷ lệ sửa đúng quan niệm sai trên bộ dữ liệu tương tác học tập công khai.

### 🛠️ Tech Stack
• Tác tử ReAct
• Bayesian Knowledge Tracing
• đồ thị tri thức (Neo4j)
• LLM phát trực tuyến
• mô-đun bộ nhớ
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu tương tác học tập và chẩn đoán lỗi sai EdNet (Riiid), ASSISTments, Eedi Diagnostic Questions và GSM8K.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Hệ thống hội thoại Socratic thời gian thực có ≥2 vai trò (Người học & Giảng viên), dẫn dắt qua chuỗi câu hỏi gợi mở, phát hiện quan niệm sai và khuyến nghị khái niệm tiếp theo.
• Tích hợp mô-đun Bayesian Knowledge Tracing cập nhật trạng thái nắm vững kiến thức và lưu lịch sử tiến bộ.

Nâng cao:
• Kết hợp đồ thị tri thức tiên quyết (Knowledge Graph) với Multi-Agent (Pedagogical Planner + Misconception Detector + Guardrail Verifier) chống việc người học dùng prompt trick ép AI giải hộ.
• Bộ benchmark định lượng tỷ lệ giữ vững nguyên tắc Socratic, độ chính xác nhận diện lỗi sai và mức cải thiện năng lực người học.

---

## [VIN-03] ConsistencyGuard – AI Agent Phát Hiện Bất Nhất Dữ Liệu Giữa Các Báo Cáo Trong Fabric Dashboard

### 📝 Mô tả đề tài
📍 Thực trạng: Hệ thống báo cáo quản trị của doanh nghiệp trên nền tảng BI (như Microsoft Fabric / Power BI) thường gồm hàng chục report con lấy dữ liệu từ nhiều semantic model và pipeline khác nhau; do lịch refresh lệch pha, khác biệt công thức DAX hoặc lỗi quan hệ bảng, cùng một chỉ số KPI có thể hiển thị số liệu mâu thuẫn giữa các báo cáo mà không được phát hiện kịp thời.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để hệ thống AI Agent tự động quét định kỳ toàn bộ report, dataset và semantic model trong workspace, đối chiếu chéo các chỉ số trùng lặp hoặc liên đới nhằm phát hiện chính xác bất nhất về giá trị, độ trễ refresh, định nghĩa công thức (DAX/SQL) và lineage, đồng thời khoanh vùng nguyên nhân gốc rễ và giảm thiểu cảnh báo giả qua phản hồi của kỹ sư dữ liệu.

🔒 Ràng buộc: Mọi phép so sánh số học, kiểm tra lệch thời gian refresh và phân tích cấu trúc DAX/schema phải do công cụ code xác định thực hiện, LLM chỉ hỗ trợ đối sánh ngữ nghĩa tên chỉ số và tổng hợp giải thích; chỉ chạy chế độ đọc metadata/query an toàn và cần người phụ trách xác nhận (HITL) trước khi gắn cờ sự cố chính thức.

### 🛠️ Tech Stack
• Microsoft Fabric REST API / Power BI Admin & Scanner API – trích xuất metadata, lineage
• Semantic Link / Semantic Link Labs (Python, sempy) – phân tích sâu DAX & semantic model trong Fabric notebook
• Power BI Execute Queries API / XMLA endpoint – lấy giá trị KPI thực tế để đối chiếu
• Azure OpenAI / Azure AI Foundry + Fabric Data Agent – lớp reasoning LLM, RAG grounded trên OneLake
• Fabric Notebook (PySpark/Python) + Data Pipeline – orchestration, lịch quét định kỳ
• Lakehouse/Delta table trên OneLake – lưu log inconsistency & nhãn feedback
• Power BI report/Fabric Real-Time Dashboard – trực quan hóa xu hướng inconsistency
• Microsoft Teams/Power Automate – gửi cảnh báo
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu kho dữ liệu đa bảng TPC-DS / AdventureWorks / Contoso BI Semantic Models (Power BI `.pbip`/BIM schemas) có bơm kịch bản lệch refresh và xung đột công thức DAX.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Ứng dụng giám sát có ≥2 vai trò (BI Engineer & Quản trị viên), tự động quét metadata/giá trị KPI giữa các báo cáo, phát hiện và gắn cờ trực quan các thẻ/biểu đồ bị lệch số liệu hoặc lệch pha refresh.
• Sinh báo cáo giải thích nguyên nhân khả dĩ (lệch thời điểm refresh, khác công thức đo lường, lỗi relationship) kèm dẫn chứng.

Nâng cao:
• Phân tích tĩnh cây cú pháp công thức DAX/SQL kết hợp đồ thị lineage để khoanh vùng chính xác bước biến đổi gây sai lệch số liệu.
• Cơ chế học từ phản hồi (feedback loop) để giảm cảnh báo giả (false positive), theo dõi xu hướng sức khỏe hệ thống BI theo thời gian và cảnh báo tự động.

---

## [VIN-04] Hệ thống tuyển sinh/ Đào tạo 20K AI

### 📝 Mô tả đề tài
📍 Thực trạng: Các chương trình tuyển sinh và đào tạo nhân lực công nghệ quy mô lớn phải xử lý hàng nghìn hồ sơ đa dạng, theo dõi hành trình từ xét tuyển đến học tập và đánh giá chuẩn đầu ra; việc rà soát thủ công gây nghẽn cổ chai, phản hồi ứng viên chậm và khó liên kết chất lượng đầu vào với kết quả đào tạo thực tế.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng thông minh quản lý xuyên suốt vòng đời tuyển sinh và chất lượng đào tạo: hỗ trợ tiếp nhận – chuẩn hóa hồ sơ, giải đáp quy chế có trích dẫn nguồn, hỗ trợ hội đồng xét tuyển theo tiêu chí minh bạch, đồng thời phân tích dữ liệu học tập để đánh giá mức độ đạt chuẩn đầu ra, phát hiện sớm học viên có nguy cơ tụt tiến độ và đề xuất cải tiến chương trình.

🔒 Ràng buộc: Mọi quyết định xét duyệt hồ sơ, cấp học bổng hoặc đánh giá học vụ bắt buộc do người có thẩm quyền phê duyệt (HITL); ẩn danh thông tin nhạy cảm để chống thiên vị trong sàng lọc; chỉ dùng dữ liệu hồ sơ/đào tạo tổng hợp hoặc công khai và đo lường độ chính xác trích xuất, trích dẫn RAG.

### 🛠️ Tech Stack
• Next.js/React, FastAPI hoặc Node.js, PostgreSQL, Power BI, tích hợp CRM/LMS qua API
• LLM và RAG để trợ lý giải đáp quy trình tuyển sinh
• Docker và nền tảng cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích hành trình người học OULAD (Open University Learning Analytics Dataset) kết hợp bộ hồ sơ tuyển sinh và khung năng lực AI tổng hợp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Cổng thông tin tuyển sinh & quản trị đào tạo (≥2 vai trò: Ứng viên/Học viên & Quản trị/Hội đồng) hỗ trợ nộp hồ sơ, theo dõi trạng thái, luồng phê duyệt có lưu vết và dashboard chỉ số tuyển sinh – đào tạo.
• Trợ lý AI giải đáp quy chế tuyển sinh/đào tạo có trích dẫn nguồn chính xác.

Nâng cao:
• Tác tử phân tích chất lượng đào tạo theo chuẩn đầu ra, tự động phát hiện hồ sơ thiếu/bất thường và cảnh báo sớm học viên cần hỗ trợ học thuật.
• Kiểm định tính công bằng (fairness check) trong hỗ trợ chấm điểm hồ sơ và sinh báo cáo khuyến nghị cải tiến chương trình dựa trên dữ liệu thực nghiệm.

---

## [VIN-05] Nền tảng Quản lý dự án nghiên cứu

### 📝 Mô tả đề tài
📍 Thực trạng: Quản lý vòng đời dự án nghiên cứu tại các viện và trường đại học (từ thuyết minh, xét duyệt, phân bổ kinh phí, theo dõi mốc tiến độ đến nghiệm thu công bố) thường bị phân tán qua nhiều biểu mẫu và email, khiến việc kiểm soát tiến độ, đối chiếu quy định tài trợ và tổng hợp báo cáo tốn nhiều công sức.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng quản lý vòng đời dự án nghiên cứu tích hợp AI Agent: hợp nhất thông tin dự án – thành viên – kinh phí – mốc đầu ra, hỗ trợ tra cứu quy định tài trợ có dẫn chứng, tự động phát hiện nguy cơ trễ hạn đường găng hoặc lệch ngân sách và tổng hợp báo cáo tiến độ đa chiều giúp giảm tải hành chính cho nhà nghiên cứu.

🔒 Ràng buộc: Các phép tính ngân sách, tỷ lệ giải ngân và kiểm tra hạn mốc phải thực hiện bằng code xác định; mọi bước duyệt thuyết minh, điều chỉnh kinh phí hoặc nghiệm thu bắt buộc có phê duyệt của cấp có thẩm quyền (HITL) và lưu nhật ký kiểm toán.

### 🛠️ Tech Stack
• React/Next.js, FastAPI, PostgreSQL, lưu trữ tài liệu, workflow engine, dashboard Power BI
• RAG trên quy định và biểu mẫu nghiên cứu
• LangGraph hoặc agent workflow
• Docker và SSO/OIDC.
• Dữ liệu & benchmark thực tế tham chiếu: Dữ liệu dự án nghiên cứu mở từ CORDIS (EU Research Projects Dataset) / NSF Award Abstracts và OpenAlex API.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Hệ thống web quản lý dự án nghiên cứu (≥2 vai trò: Chủ nhiệm đề tài & Quản trị/Hội đồng) quản lý thành viên, mốc công việc, kinh phí, tài liệu, công bố và luồng phê duyệt.
• Trợ lý tra cứu quy định quản lý đề tài có trích dẫn điều khoản và tổng hợp báo cáo tiến độ.

Nâng cao:
• Tác tử phân tích rủi ro tiến độ & ngân sách dự án, tự động đối chiếu kết quả đầu ra thực tế (bài báo/sản phẩm qua OpenAlex/ORCID) với cam kết trong thuyết minh.
• Dashboard danh mục dự án toàn đơn vị kèm cảnh báo sớm các điểm nghẽn và kiểm thử định lượng độ chính xác tổng hợp báo cáo.

---

## [VIN-06] Siêu ứng dụng khuôn viên số (Campus Super-App)

### 📝 Mô tả đề tài
📍 Thực trạng: Sinh viên trong khuôn viên đại học phải sử dụng nhiều kênh và ứng dụng rời rạc để tra cứu bản đồ phòng học, lịch sự kiện, thông tin câu lạc bộ, thẻ sinh viên số và thủ tục hành chính, dẫn đến bỏ lỡ hoạt động phù hợp và mất nhiều thời gian tìm kiếm thông tin.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng siêu ứng dụng khuôn viên số (Campus Super-App) tích hợp AI Agent ngữ cảnh: hợp nhất bản đồ số, thẻ định danh, lịch hoạt động, câu lạc bộ và tiện ích học đường, đồng thời điều phối tác vụ liên dịch vụ và gợi ý lịch trình học tập – hoạt động ngoại khóa cá nhân hóa mà không gây quá tải thông báo.

🔒 Ràng buộc: Kiểm soát phân quyền chặt chẽ giữa Sinh viên, Ban chủ nhiệm CLB và Quản trị viên; mọi thao tác đăng ký dịch vụ có phí, duyệt nội dung sự kiện hoặc cấp quyền thẻ số phải có bước xác nhận (HITL); đảm bảo thời gian phản hồi nhanh và không rò rỉ dữ liệu vị trí/cá nhân.

### 🛠️ Tech Stack
• Flutter hoặc React Native, Next.js, FastAPI, PostgreSQL, bản đồ Mapbox/Google Maps, xác thực SSO, thông báo đẩy
• AI assistant/RAG trên tài liệu dịch vụ và nội dung câu lạc bộ
• Docker và cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Dữ liệu bản đồ OpenStreetMap khuôn viên trường học, chuẩn lịch iCal/GTFS và bộ dữ liệu hành vi sinh viên StudentLife Dataset (Dartmouth).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Ứng dụng triển khai online (≥2 vai trò: Sinh viên & Quản trị) tích hợp bản đồ khuôn viên, thẻ số mô phỏng, bảng tin hoạt động, danh mục câu lạc bộ và trợ lý hỏi-đáp dịch vụ nội khu có trích nguồn.
• Luồng đăng ký tham gia sự kiện/CLB và duyệt nội dung có kiểm soát.

Nâng cao:
• Agent điều phối lịch trình thông minh (tự động phát hiện xung đột giữa lịch học, sự kiện CLB và thời gian di chuyển giữa các tòa nhà để gợi ý lộ trình tối ưu).
• Hệ thống thông báo thông minh chống quá tải (anti-fatigue notification) và dashboard phân tích mức độ gắn kết sinh viên.

---

## [VIN-07] Nền tảng dữ liệu Datalake/ Datalake House

### 📝 Mô tả đề tài
📍 Thực trạng: Dữ liệu về người học, giảng dạy, nghiên cứu và vận hành tại tổ chức giáo dục/doanh nghiệp thường nằm ở các hệ thống silo khác nhau với định nghĩa trường và mã định danh không đồng nhất, khiến việc xây dựng hồ sơ 360° và phân tích ra quyết định gặp rủi ro sai lệch hoặc vi phạm quyền truy cập.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng dữ liệu theo kiến trúc Data Lakehouse (Bronze – Silver – Gold) phục vụ hồ sơ 360° và phân tích thông minh: tự động hóa quy trình nạp – đối sánh thực thể – kiểm định chất lượng dữ liệu đa nguồn, thiết lập tầng ngữ nghĩa (semantic layer) thống nhất và tích hợp AI Agent hỗ trợ truy vấn/giải thích biến động chỉ số theo đúng phân quyền.

🔒 Ràng buộc: Áp dụng kiểm soát truy cập theo vai trò và cấp độ dòng/cột (RBAC/RLS), che dấu dữ liệu nhạy cảm (PII masking); mọi truy vấn số liệu của Agent phải thông qua semantic model/SQL được kiểm tra xác định trước khi chạy và có kiểm soát chi phí quét dữ liệu.

### 🛠️ Tech Stack
• Microsoft Fabric hoặc Databricks, OneLake/Delta Lake, Data Factory, Spark/Python, Power BI, PostgreSQL
• catalog và kiểm soát chất lượng dữ liệu
• API/SSO, Docker và cơ chế phân quyền theo vai trò.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu giáo dục đa bảng OULAD + EdNet kết hợp chuẩn siêu dữ liệu OpenLineage và mô hình dbt Medallion.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Pipeline Lakehouse nạp và chuẩn hóa dữ liệu mẫu từ nhiều nguồn thành mô hình hồ sơ 360°, có bộ quy tắc kiểm tra chất lượng dữ liệu (Data Quality rules) và dashboard BI.
• Phân quyền tối thiểu 2 vai trò (Data Admin & Người dùng khai thác báo cáo) kèm trợ lý hỏi-đáp dữ liệu trong phạm vi được cấp quyền.

Nâng cao:
• Đồ thị truy vết dòng chảy dữ liệu (column-level lineage), tự động phát hiện bất thường/trôi lệch dữ liệu (data drift) giữa các kỳ cập nhật.
• Đánh giá định lượng độ chính xác Text-to-SQL/Semantic Query trên tập câu hỏi nghiệp vụ phức tạp và cơ chế kiểm toán truy cập dữ liệu.

---

## [VIN-08] Tự động hóa quy trình phê duyệt Microsoft power automate

### 📝 Mô tả đề tài
📍 Thực trạng: Các quy trình phê duyệt vận hành trong doanh nghiệp (mua sắm, công tác, hợp đồng, tờ trình nội bộ) thường đi qua nhiều cấp xét duyệt phức tạp với các điều kiện rẽ nhánh theo ngân sách/loại chứng từ; xử lý qua email hoặc biểu mẫu tĩnh dễ dẫn đến tắc nghẽn, gửi sai luồng, quá hạn SLA và khó kiểm toán.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng hệ thống tự động hóa và điều phối quy trình phê duyệt thông minh: kết hợp động cơ luồng công việc (workflow state machine) có phân quyền, ủy quyền, lưu vết kiểm toán với AI Agent hỗ trợ kiểm tra tính hợp lệ/xung đột của hồ sơ đính kèm trước khi trình ký, tóm tắt điểm trọng yếu cho người duyệt và phát hiện điểm nghẽn SLA.

🔒 Ràng buộc: Trạng thái quy trình, phân quyền phê duyệt và kiểm tra ngưỡng ngân sách phải do workflow engine xác định kiểm soát (AI tuyệt đối không tự ý duyệt thay con người); lưu nhật ký kiểm toán bất biến (immutable audit log) cho mọi thao tác.

### 🛠️ Tech Stack
• Microsoft Power Automate, Power Apps, SharePoint/Dataverse, Teams, Power BI
• Azure AD/SSO
• API kết nối hệ thống nội bộ
• Power Platform governance và audit log.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu nhật ký quy trình nghiệp vụ thực tế BPI Challenge (Business Process Intelligence datasets) kèm tập chứng từ đề nghị thanh toán/mua sắm tổng hợp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Hệ thống số hóa quy trình phê duyệt hoàn chỉnh (≥3 vai trò: Người đề xuất, Người phê duyệt, Quản trị) với biểu mẫu động, định tuyến đa bước theo điều kiện, thông báo và lịch sử kiểm toán.
• AI hỗ trợ kiểm tra thiếu sót hồ sơ đầu vào và tóm tắt nội dung tờ trình cho cấp duyệt.

Nâng cao:
• Hỗ trợ đa quy trình có cơ chế ủy quyền, leo thang tự động khi quá hạn SLA (escalation), phát hiện xung đột quyền hạn (Segregation of Duties).
• Phân tích Process Mining từ log xử lý để chỉ ra bước gây nghẽn cổ chai và đề xuất tối ưu hóa luồng quy trình.

---

## [VIN-09] Nâng cấp e-hiring

### 📝 Mô tả đề tài
📍 Thực trạng: Quy trình tuyển dụng điện tử (e-Hiring) tại doanh nghiệp thường bị gián đoạn giữa khâu đăng tuyển, sàng lọc hàng trăm CV không đồng nhất định dạng, điều phối lịch phỏng vấn đa bên và tổng hợp đánh giá từ hội đồng tuyển dụng, gây kéo dài thời gian tuyển (time-to-hire) và thiếu nhất quán.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để nâng cấp nền tảng tuyển dụng điện tử tích hợp hệ thống AI Agent hỗ trợ toàn trình: từ chuẩn hóa và đối sánh hồ sơ ứng viên với yêu cầu công việc (JD) dựa trên bằng chứng kỹ năng thực chất (có kiểm soát chống thiên vị), điều phối lịch phỏng vấn thông minh đến hỗ trợ hội đồng xây dựng bộ câu hỏi phỏng vấn đào sâu cá nhân hóa cho từng ứng viên.

🔒 Ràng buộc: AI chỉ đóng vai trò hỗ trợ phân tích và gợi ý theo tiêu chí minh bạch; mọi quyết định sàng lọc, mời phỏng vấn hay tuyển chọn bắt buộc do HR và Quản lý tuyển dụng phê duyệt (HITL); ẩn danh thông tin nhân khẩu học nhạy cảm và bảo mật tuyệt đối dữ liệu PII của ứng viên.

### 🛠️ Tech Stack
• Next.js/React, FastAPI, PostgreSQL, tích hợp email/lịch, lưu trữ CV, OCR/parser CV, workflow engine
• LLM/RAG và scoring có giải thích
• SSO, audit log, Docker và cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Khung phân loại kỹ năng chuẩn quốc tế ESCO / O*NET và bộ dữ liệu Resume–JD Matching công khai trên HuggingFace/Kaggle.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Nền tảng e-Hiring triển khai online (≥2 vai trò: HR Recruiter & Hiring Manager) quản lý vị trí tuyển, tiếp nhận và bóc tách CV, theo dõi pipeline ứng viên, đặt lịch phỏng vấn và lưu vết đánh giá.
• AI tóm tắt hồ sơ theo tiêu chí JD kèm trích dẫn minh chứng trực tiếp từ CV.

Nâng cao:
• Tự động phát hiện thông tin mâu thuẫn hoặc thiếu hụt trong hồ sơ để sinh câu hỏi phỏng vấn đào sâu cá nhân hóa cho từng ứng viên.
• Kiểm định độ công bằng (Counterfactual Fairness: thay đổi tên/giới tính không làm đổi điểm đánh giá) và dashboard phân tích hiệu quả phễu tuyển dụng.

---

## [VIN-10] Trợ lý AI cho cổng thông tin học giả của trường đại học

### 📝 Mô tả đề tài
📍 Thực trạng: Dữ liệu về hồ sơ năng lực học giả, công trình công bố, dự án và hướng nghiên cứu tại các trường đại học/viện nghiên cứu thường nằm rải rác và cập nhật chậm, khiến đối tác doanh nghiệp, sinh viên hoặc các nhóm nghiên cứu liên ngành rất khó tìm đúng chuyên gia để hợp tác hoặc hướng dẫn.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng cổng thông tin học giả tích hợp AI Agent khai thác tri thức nghiên cứu: tự động đồng bộ, chuẩn hóa và khử trùng lặp hồ sơ công bố từ các cơ sở dữ liệu học thuật quốc tế, hỗ trợ tìm kiếm ngữ nghĩa và hỏi-đáp có trích dẫn nguồn, đồng thời phân tích mạng lưới năng lực để gợi ý kết nối chuyên gia hợp tác liên ngành.

🔒 Ràng buộc: Chỉ hiển thị và trả lời dựa trên dữ liệu công bố/hồ sơ đã xác thực, gắn trích dẫn DOI/nguồn rõ ràng (0% bịa đặt công trình nghiên cứu); có cơ chế để nhà nghiên cứu/quản trị viên kiểm duyệt hồ sơ trước khi xuất bản công khai (HITL).

### 🛠️ Tech Stack
• Next.js/React
• FastAPI
• PostgreSQL
• OpenAlex/ORCID/Crossref API
• Elasticsearch hoặc OpenSearch
• RAG với vector database
• LLM
• SSO/OIDC
• Docker và phân quyền dữ liệu.
• Dữ liệu & benchmark thực tế tham chiếu: Dữ liệu thực tế từ OpenAlex API, ORCID, Crossref và Semantic Scholar Open Research Corpus (S2ORC).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Cổng thông tin học giả & công bố khoa học (≥2 vai trò: Người tra cứu & Quản trị/Học giả) hỗ trợ tìm kiếm theo tên/chủ đề, trang hồ sơ chi tiết và trợ lý hỏi-đáp có trích dẫn nguồn.
• Cơ chế rà soát và phê duyệt cập nhật hồ sơ trước khi công bố.

Nâng cao:
• Tự động đồng bộ và khử trùng lặp tác giả/công trình từ OpenAlex/ORCID/Crossref, phát hiện hồ sơ thiếu hoặc lỗi thời.
• Đồ thị tri thức gợi ý tổ hợp chuyên gia liên ngành phù hợp cho một chủ đề nghiên cứu/tài trợ mới kèm phân tích độ phủ năng lực.

---

## [VIN-11] AI Report Factory – Một nguồn dữ liệu, nhiều báo cáo cho nhiều đối tượng

### 📝 Mô tả đề tài
📍 Thực trạng: Doanh nghiệp và tổ chức giáo dục thường phải biên soạn hàng chục phiên bản báo cáo khác nhau (báo cáo điều hành, tờ trình hội đồng, báo cáo cơ quan quản lý, thông cáo đối tác, nội dung slide, Q&A) từ cùng một bộ dữ liệu và sự kiện gốc; việc viết lại thủ công vừa mất thời gian vừa dễ xảy ra sai lệch số liệu giữa các bản phát hành.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng 'AI Report Factory' chuyển hóa từ một nguồn dữ liệu/sự kiện gốc đã được phê duyệt (Single Source of Truth) sang nhiều định dạng và văn phong báo cáo phù hợp với từng nhóm đối tượng nhận (tiếng Việt và tiếng Anh), đồng thời tự động kiểm toán tính nhất quán số học, phát hiện dữ liệu mâu thuẫn/thiếu hụt và cập nhật dây chuyền khi dữ liệu gốc thay đổi.

🔒 Ràng buộc: Tuyệt đối cấm mô hình tự suy diễn hoặc làm tròn/thay đổi số liệu khác với nguồn gốc; mọi con số trong bản thảo phải liên kết ngược về đúng ô/bảng dữ liệu nguồn và được kiểm tra chéo bằng code xác định; bắt buộc có bước phê duyệt của người phụ trách (HITL) trước khi xuất bản.

### 🛠️ Tech Stack
• Mô hình ngôn ngữ doanh nghiệp: Azure OpenAI/ChatGPT Enterprise hoặc Claude Enterprise theo nền tảng được phê duyệt. Kho tri thức: SharePoint/OneDrive hoặc kho tài liệu nội bộ có phân quyền. RAG và tìm kiếm: Azure AI Search hoặc vector database tương đương. Điều phối agent: Azure AI Foundry
• LangGraph hoặc nền tảng agent nội bộ. Kết nối dữ liệu: Power BI semantic model/API và các hệ thống nguồn được cho phép. Giao diện: Microsoft Teams hoặc cổng nội bộ. Bắt buộc có SSO
• phân quyền theo vai trò
• nhật ký truy cập và cơ chế phê duyệt trước khi phát hành.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu báo cáo tài chính – vận hành đa bảng TAT-QA / FinQA kết hợp bộ sự kiện và báo cáo thường niên doanh nghiệp công khai.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Ứng dụng tạo báo cáo đa đối tượng (≥2 vai trò: Người biên soạn & Lãnh đạo phê duyệt) sinh tự động các phiên bản: executive summary, tờ trình, email, bài phát biểu, Q&A và dàn ý slide (Việt/Anh).
• Bảng đối chiếu số liệu – nguồn tham chiếu từng câu và danh sách các điểm thiếu/mâu thuẫn cần con người xác nhận.

Nâng cao:
• Tác tử kiểm toán chéo (Deterministic Fact & Number Verifier) tự động phát hiện bất kỳ sai lệch số liệu hoặc nhận định vượt quá bằng chứng nguồn giữa các phiên bản báo cáo.
• Quản lý lịch sử phiên bản (version diff) và tự động cập nhật đồng bộ toàn bộ các bản báo cáo phái sinh khi dữ liệu gốc thay đổi.

---

## [VIN-12] Rexcel – Nền tảng thiết kế đề cương nghiên cứu có hỗ trợ AI

### 📝 Mô tả đề tài
📍 Thực trạng: Người làm nghiên cứu mới thường gặp khó khăn khi chuyển hóa ý tưởng thành đề cương nghiên cứu chặt chẽ về phương pháp luận, cỡ mẫu, kế hoạch phân tích thống kê và các nguyên tắc liêm chính/đạo đức nghiên cứu; các lỗi thiết kế cơ bản thường chỉ được phát hiện muộn khi nộp lên hội đồng xét duyệt.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng không gian soạn thảo đề cương nghiên cứu thông minh tích hợp AI phản biện theo phương pháp Socratic: đồng hành ngay trong quá trình viết để rà soát tính nhất quán giữa Câu hỏi nghiên cứu – Thiết kế – Biến số – Kiểm định thống kê và mức độ tuân thủ chuẩn báo cáo quốc tế (STROBE, CONSORT, PRISMA), gợi ý học liệu đúng lỗ hổng kiến thức và cho phép chạy thử phân tích thống kê trên dữ liệu tổng hợp.

🔒 Ràng buộc: AI tuyệt đối không viết hộ đề cương mà chỉ đặt câu hỏi phản biện Socratic và chỉ ra điểm thiếu hụt dựa trên chuẩn mực phương pháp luận có trích dẫn; việc tính toán cỡ mẫu/kiểm định thống kê mẫu phải chạy trên môi trường thực thi code thực chất và có giảng viên hướng dẫn duyệt (HITL).

### 🛠️ Tech Stack
• Khung AI: LangGraph, AutoGen
• Tích hợp Canvas: LTI 1.3 và xAPI
• Mô hình ngôn ngữ lớn: GPT-4o, Claude
• Dữ liệu & benchmark thực tế tham chiếu: Bộ tiêu chuẩn báo cáo nghiên cứu quốc tế EQUATOR Network (CONSORT, STROBE, PRISMA checklists), bộ dữ liệu bài báo khoa học QASPER và dữ liệu dịch tễ học tổng hợp (Synthea).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Không gian soạn thảo đề cương tương tác (≥2 vai trò: Người nghiên cứu & Giảng viên hướng dẫn) cung cấp nhận xét thời gian thực, phản hồi Socratic và gợi ý học liệu cá nhân hóa có trích nguồn.
• Báo cáo đánh giá mức độ sẵn sàng trước khi nộp hội đồng đạo đức (IRB readiness report) theo checklist chuẩn (STROBE/CONSORT/PRISMA).

Nâng cao:
• Tích hợp sandbox sinh dữ liệu giả lập theo đúng thiết kế nghiên cứu của đề cương để người học chạy thử code phân tích thống kê và kiểm tra lực mẫu (statistical power) trước khi thu thập dữ liệu.
• Kiểm tra tự động sự khớp nối logic giữa Câu hỏi nghiên cứu – Thiết kế – Biến số – Phương pháp phân tích và đánh giá định lượng chất lượng phản biện.

---

## [VIN-13] Mô phỏng ca học tập bằng AI cho thư viện điện tử Dịch tễ học và học phần Liêm chính nghiên cứu

### 📝 Mô tả đề tài
📍 Thực trạng: Việc học các nguyên tắc thiết kế nghiên cứu, kiểm soát sai số/nhiễu (bias/confounding) và đạo đức/liêm chính học thuật qua tài liệu tĩnh thường khô khan, khiến người học khó nhận diện và xử lý các tình huống lưỡng nan thực tế khi bước vào dự án nghiên cứu thật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để hệ thống AI tự động kiến tạo và điều phối các ca mô phỏng tình huống tương tác phân nhánh (interactive branching case simulations) từ kho học liệu chuẩn: đặt người học vào các bối cảnh ra quyết định sát thực (xử lý dữ liệu ngoại lai, xung đột quyền tác giả, sai lệch chọn mẫu, sử dụng AI có trách nhiệm), thích ứng độ khó theo từng lựa chọn và mô phỏng trực quan hệ quả của quyết định sai.

🔒 Ràng buộc: Mọi tình huống, giải thích và khuyến nghị trong mô phỏng phải bám sát kho học liệu được phê duyệt kèm trích dẫn cụ thể (không bịa đặt quy tắc học thuật); giảng viên có quyền kiểm duyệt kịch bản (HITL) và theo dõi tiến độ của từng học viên.

### 🛠️ Tech Stack
• GPT-4o/5
• OpenAI Canvas
• Gemini
• Claude
• LangGraph/LangChain
• quy trình RAG
• cơ sở dữ liệu vector (FAISS/Chroma)
• tìm kiếm embedding
• Dữ liệu & benchmark thực tế tham chiếu: Kho tình huống đạo đức nghiên cứu công khai (ORI Casebook / COPE Cases), hướng dẫn EQUATOR và học liệu phương pháp nghiên cứu mở.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Ứng dụng mô phỏng ca học tập phân nhánh (≥2 vai trò: Người học & Giảng viên) tự động sinh tình huống theo mục tiêu học tập, đặt câu hỏi tương tác đa bước và đưa phản hồi giải thích có trích dẫn nguồn.
• Gợi ý học liệu liên quan (bài đọc, hướng dẫn, video) và báo cáo tổng kết tiến độ học tập.

Nâng cao:
• Động cơ điều chỉnh độ khó thích ứng (Adaptive Scenario Engine) tự động đưa ra các tình huống bẫy tinh vi hơn dựa trên lịch sử lỗi sai của từng người học.
• Kết hợp mô phỏng dữ liệu trực quan (cho người học thấy ngay kết quả nghiên cứu bị lệch như thế nào nếu chọn sai cách xử lý biến nhiễu) và bộ đo lường chất lượng ca học.

---

## [VIN-14] Trợ lý tri thức AI cho thư viện điện tử Dịch tễ học và học phần Liêm chính nghiên cứu

### 📝 Mô tả đề tài
📍 Thực trạng: Người học và nhà nghiên cứu thường phải tra cứu thông tin qua hàng trăm slide bài giảng, giáo trình phương pháp luận, quy định liêm chính học thuật, bài báo phản biện và video hướng dẫn nằm rải rác; việc tìm kiếm bằng từ khóa rời rạc tốn nhiều thời gian và dễ dẫn đến hiểu sai khái niệm hoặc áp dụng nhầm phương pháp.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng trợ lý tri thức nghiên cứu đa phương thức dựa trên bằng chứng (Evidence-based Research Knowledge Agent): không chỉ truy xuất chính xác đoạn văn bản/khung hình video từ kho học liệu đã kiểm duyệt, mà còn tổng hợp so sánh ưu – nhược điểm – điều kiện áp dụng giữa các phương pháp nghiên cứu, phát hiện mâu thuẫn giữa các nguồn và dẫn dắt người học đào sâu khái niệm.

🔒 Ràng buộc: 100% câu trả lời và bảng so sánh phương pháp phải gắn trích dẫn tới đúng trang tài liệu/mốc thời gian video gốc trong kho dữ liệu được cấp phép; tự động từ chối trả lời khi ngoài phạm vi học liệu và kiểm soát tỷ lệ ảo giác (hallucination rate) bằng bộ đánh giá tự động.

### 🛠️ Tech Stack
• OpenAI GPT-5
• OpenAI Canvas
• Retrieval-Augmented Generation (RAG)
• Cơ sở dữ liệu vector (FAISS/Chroma)
• Tìm kiếm embedding
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu hỏi-đáp trên bài báo khoa học QASPER, SciFact, LitQA2 kết hợp kho giáo trình mở về Dịch tễ học & Phương pháp nghiên cứu.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Hệ thống hỏi-đáp và khai thác học liệu (≥2 vai trò: Sinh viên/Nhà nghiên cứu & Giảng viên quản trị kho tri thức) trả lời theo ngữ cảnh kèm trích dẫn chính xác đến từng đoạn/trang nguồn.
• Hỗ trợ tóm tắt tài liệu, giải thích thuật ngữ chuyên ngành, so sánh phương pháp nghiên cứu và khuyến nghị học liệu liên quan.

Nâng cao:
• Pipeline Hybrid Graph-RAG + Reranker xử lý truy vấn đa bước (multi-hop reasoning) xuyên qua cả tài liệu PDF, bảng biểu và phụ đề video bài giảng.
• Bộ đánh giá định lượng tự động (RAGAS: Faithfulness, Context Precision/Recall) và giao diện đối chiếu trực quan đoạn trích nguồn cạnh câu trả lời.

---

## [VIN-15] Hệ thống hỗ trợ thực tập bằng AI

### 📝 Mô tả đề tài
📍 Thực trạng: Khi quy mô sinh viên đi thực tập doanh nghiệp tăng cao, giảng viên phụ trách và bộ phận quản lý đào tạo bị quá tải bởi hàng loạt câu hỏi lặp lại về thủ tục, điều kiện công nhận tín chỉ và việc theo dõi thủ công hồ sơ, nhật ký thực tập, đánh giá từ doanh nghiệp tiếp nhận.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng quản lý và đồng hành thực tập thông minh tích hợp AI Agent: tự động chuẩn hóa hồ sơ đăng ký thực tập, hướng dẫn quy trình – chính sách theo đúng ngữ cảnh cá nhân của từng sinh viên, đồng thời giám sát tiến độ theo các mốc bắt buộc để phát hiện sớm rủi ro trễ hạn, lệch chuẩn đầu ra hoặc thiếu điều kiện xét công nhận tín chỉ.

🔒 Ràng buộc: Mọi quyết định phê duyệt đề cương thực tập, xử lý ngoại lệ hoặc công nhận quy đổi tín chỉ bắt buộc có giảng viên/quản trị viên phê duyệt (HITL); câu trả lời chính sách phải trích dẫn đúng văn bản quy định hiện hành và bảo mật thông tin sinh viên – doanh nghiệp.

### 🛠️ Tech Stack
• Next.js/React, FastAPI, PostgreSQL, lưu trữ hồ sơ/tài liệu, tích hợp LMS hoặc biểu mẫu qua API
• RAG trên quy định và hướng dẫn thực tập
• LLM, workflow engine, SSO/OIDC, Docker và dashboard BI.
• Dữ liệu & benchmark thực tế tham chiếu: Khung kỹ năng nghề nghiệp ESCO / O*NET kết hợp bộ quy chế đào tạo, biểu mẫu thực tập và dữ liệu theo dõi tiến độ học tập mẫu.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Cổng quản lý thực tập trực tuyến (≥2 vai trò: Sinh viên & Giảng viên/Quản trị) cho phép khai báo – chuẩn hóa hồ sơ thực tập, theo dõi trạng thái từng mốc và xem danh sách tổng hợp.
• Trợ lý AI giải đáp thủ tục, yêu cầu học phần và chính sách thực tập có trích dẫn nguồn.

Nâng cao:
• Tác tử giám sát chủ động (Proactive Milestone & Compliance Monitor) tự động phát hiện hồ sơ thiếu minh chứng, chậm tiến độ hoặc nội dung công việc thực tập lệch chuẩn đầu ra để nhắc việc và cảnh báo.
• Luồng xử lý phê duyệt ngoại lệ có lưu vết, đồng bộ dữ liệu LMS và dashboard phân tích chất lượng thực tập toàn khóa.

---

## [VIN-16] Trợ lý phòng thí nghiệm thông minh cho quản lý nghiên cứu

### 📝 Mô tả đề tài
📍 Thực trạng: Các nhóm nghiên cứu và phòng thí nghiệm thường quản lý đề tài, thành viên, công bố, tài liệu, thiết bị và đối tác qua nhiều tệp bảng tính và thư mục rời rạc, khiến tri thức nghiên cứu bị phân mảnh, khó tái sử dụng dữ liệu, mất nhiều thời gian tìm chuyên gia nội bộ hoặc tổng hợp báo cáo.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng quản lý và khai thác tri thức phòng thí nghiệm thông minh dựa trên Đồ thị Tri thức (Research Knowledge Graph & Multi-Agent System): kết nối thống nhất Con người – Dự án – Công bố – Bộ dữ liệu – Thiết bị – Nguồn tài trợ, cho phép truy vấn ngôn ngữ tự nhiên có dẫn chứng, phát hiện khoảng trống kỹ năng để gợi ý ghép nhóm nghiên cứu và tự động hóa kiểm toán tiến độ/báo cáo.

🔒 Ràng buộc: Phân quyền truy cập chi tiết theo vai trò và dự án (OIDC/RBAC); mọi thông tin trả lời và báo cáo tổng hợp phải dẫn chiếu trực tiếp đến nút/cạnh trên đồ thị tri thức và tài liệu gốc; các thao tác cập nhật dữ liệu chính thức cần bước xác nhận (HITL).

### 🛠️ Tech Stack
• React/TypeScript
• FastAPI
• PostgreSQL
• Neo4j
• Elasticsearch/OpenSearch
• LangGraph hoặc CrewAI
• Graph-RAG
• sentence-transformers
• API LLM hoặc LLM mã nguồn mở
• Docker
• lưu trữ đối tượng
• OIDC/SSO
• Dữ liệu & benchmark thực tế tham chiếu: Dữ liệu đồ thị học thuật mở OpenAlex (Authors, Works, Institutions, Concepts, Funders) kết hợp dữ liệu quản lý dự án và thiết bị phòng thí nghiệm tổng hợp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Nền tảng web (≥2 vai trò: Thành viên nghiên cứu & Trưởng lab/Quản trị) tích hợp Đồ thị Tri thức nghiên cứu, bảng điều khiển dự án, quản lý thiết bị/công bố và tìm kiếm/hỏi-đáp ngôn ngữ tự nhiên có dẫn chứng.
• Gợi ý chuyên gia, phân tích khoảng trống kỹ năng của nhóm và xuất báo cáo tổng hợp (CSV/PDF).

Nâng cao:
• Kiến trúc Graph-RAG kết hợp Multi-Agent tự động suy luận trên đồ thị để đề xuất tổ hợp nhóm nghiên cứu tối ưu cho một đề bài tài trợ mới và cảnh báo xung đột nguồn lực/hạn chót.
• Đánh giá định lượng độ chính xác truy vấn đồ thị, độ trung thực trích dẫn và khả năng mở rộng trên tập dữ liệu hàng chục nghìn thực thể.

---
