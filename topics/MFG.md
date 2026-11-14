# Lĩnh vực: MFG - Hệ thống sản xuất thông minh doanh nghiệp

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `MFG-01` | [AI Agent Lập & Tối Ưu Kế Hoạch Sản Xuất Đa Dây Chuyền (Production Planning Agent)](#mfg-01) |
| `MFG-02` | [AI Agent Trợ Lý MES Hỏi-Đáp Trạng Thái Dây Chuyền Realtime (Shopfloor Copilot)](#mfg-02) |
| `MFG-03` | [AI Agent Bảo Trì Dự Đoán Từ Dữ Liệu Cảm Biến Máy (Predictive Maintenance Agent)](#mfg-03) |
| `MFG-04` | [AI Agent Kiểm Tra Chất Lượng Bề Mặt Bằng Computer Vision (Visual QC Agent)](#mfg-04) |
| `MFG-05` | [AI Agent Phân Tích Nguyên Nhân Gốc Lỗi Sản Xuất (Root Cause Analysis Agent)](#mfg-05) |
| `MFG-06` | [AI Agent Trợ Lý An Toàn Lao Động & Tuân Thủ EHS (EHS Safety Agent)](#mfg-06) |
| `MFG-07` | [AI Agent Tối Ưu Tồn Kho Nguyên Vật Liệu & Chuỗi Cung Ứng Nhà Máy (Inventory & Supply Agent)](#mfg-07) |
| `MFG-08` | [AI Agent Điều Phối Lệnh Sản Xuất (Work Order Orchestration Agent)](#mfg-08) |
| `MFG-09` | [AI Agent Trợ Lý Kỹ Sư Tra Cứu SOP & Bản Vẽ Kỹ Thuật (Engineering Knowledge Agent)](#mfg-09) |
| `MFG-10` | [AI Agent Giám Sát Năng Lượng Nhà Máy & Tối Ưu Tiêu Thụ (Energy Optimization Agent)](#mfg-10) |
| `MFG-11` | [AI Agent Dự Báo Năng Suất & Tối Ưu OEE (OEE Analytics Agent)](#mfg-11) |
| `MFG-12` | [AI Agent Truy Xuất Nguồn Gốc Linh Kiện & Pin (Traceability Agent)](#mfg-12) |
| `MFG-13` | [AI Agent Kiểm Soát Chất Lượng Đầu Vào IQC (Incoming Quality Control Agent)](#mfg-13) |
| `MFG-14` | [AI Agent Phát Hiện Bất Thường Quy Trình (SPC & Process Anomaly Agent)](#mfg-14) |
| `MFG-15` | [AI Agent Đào Tạo & Hỗ Trợ Công Nhân Vận Hành (Operator Training Agent)](#mfg-15) |
| `MFG-16` | [AI Agent Quản Lý Bảo Trì Thiết Bị & Phụ Tùng (CMMS Agent)](#mfg-16) |
| `MFG-17` | [AI Agent Phân Tích Phế Phẩm & Lãng Phí (Scrap & Waste Reduction Agent)](#mfg-17) |
| `MFG-18` | [AI Agent Cảnh Báo & Xử Lý Sự Cố Dây Chuyền Realtime (Line Incident Response Agent)](#mfg-18) |
| `MFG-19` | [AI Agent Lập & Tối Ưu Lịch Chạy Máy Giảm Thời Gian Chuyển Đổi (Machine Scheduling & Changeover Agent)](#mfg-19) |
| `MFG-20` | [AI Agent Giám Sát An Toàn PPE & Khu Vực Nguy Hiểm Bằng Computer Vision (PPE & Zone Safety Agent)](#mfg-20) |

---

## [MFG-01] AI Agent Lập & Tối Ưu Kế Hoạch Sản Xuất Đa Dây Chuyền (Production Planning Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhà máy sản xuất của doanh nghiệp lắp ráp nhiều dòng xe trên các dây chuyền chung, kế hoạch sản xuất do kỹ sư lập thủ công trên Excel, mất nhiều giờ và khó phản ứng khi có đơn gấp hoặc thiếu vật tư. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tự lập lịch sản xuất tối ưu (thứ tự lệnh, phân bổ dây chuyền, ca kíp) dựa trên đơn hàng, năng lực máy, tồn kho, thời gian giao hàng; tự động lập lại kế hoạch khi có biến động (máy hỏng, đơn khẩn); đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Mọi kế hoạch tác động đến dây chuyền phải qua HITL (quản đốc duyệt trước khi ban hành); tôn trọng ràng buộc an toàn ca làm việc; bảo mật dữ liệu đơn hàng & năng lực nhà máy; kế hoạch phải khả thi (không vi phạm capacity); cảnh báo khi bài toán vượt giới hạn tối ưu hóa. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM (GPT-4o/Claude) làm reasoning + LangGraph điều phối agent (planner → optimizer → validator → HITL)
• solver tối ưu OR-Tools/PuLP cho scheduling
• PostgreSQL lưu đơn hàng/BOM/lịch máy
• giả lập MES qua REST API
• backend FastAPI
• frontend React + Gantt chart (dhtmlx/frappe-gantt)
• deploy Render/Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark lập lịch sản xuất Job-Shop Taillard / OR-Library, dữ liệu định mức vật tư đa cấp (multi-level BOM & MRP) và chuẩn nhà máy ISA-95 / OPC-UA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy online, đăng nhập 2 vai trò (Kỹ sư kế hoạch & Quản đốc duyệt)
• agent nhận danh sách đơn + trạng thái máy mô phỏng, sinh kế hoạch dạng Gantt, giải thích lý do sắp xếp
• HITL duyệt/từ chối
• memory lưu lịch sử kế hoạch.

Nâng cao:
• Tự động re-planning khi inject sự cố máy realtime
• tối ưu đa mục tiêu (giao hàng đúng hạn + tối thiểu chuyển đổi khuôn)
• cảnh báo capacity vượt ngưỡng và đề xuất tăng ca
• dashboard KPI (tỷ lệ đúng hạn, utilization)
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-02] AI Agent Trợ Lý MES Hỏi-Đáp Trạng Thái Dây Chuyền Realtime (Shopfloor Copilot)

### 📝 Mô tả đề tài
📍 Thực trạng: Quản lý sản xuất phải mở nhiều màn hình SCADA/MES để biết dây chuyền đang chạy gì, sản lượng, máy nào dừng; thông tin phân tán, khó tổng hợp nhanh. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hội thoại (tiếng Việt) cho phép hỏi 'dây chuyền 3 đang thế nào', 'vì sao sản lượng ca sáng thấp', agent tự truy vấn MES, tổng hợp, giải thích và đề xuất hành động; hỗ trợ hỏi-đáp đa lượt có ngữ cảnh; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Agent chỉ được ĐỌC dữ liệu; mọi lệnh tác động (dừng/khởi động máy) phải chuyển sang luồng HITL riêng; phân quyền theo vai trò; bảo mật dữ liệu sản xuất; độ trễ trả lời thấp; không được bịa số liệu (bắt buộc trích nguồn từ MES). Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + LangGraph (agent với tool-calling: query_line_status, get_oee, get_downtime)
• RAG trên tài liệu quy trình
• time-series DB (TimescaleDB/InfluxDB) mô phỏng dữ liệu dây chuyền
• MES giả lập sinh dữ liệu realtime (Python + MQTT/WebSocket)
• backend FastAPI
• frontend React + realtime charts
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark lập lịch sản xuất Job-Shop Taillard / OR-Library, dữ liệu định mức vật tư đa cấp (multi-level BOM & MRP) và chuẩn nhà máy ISA-95 / OPC-UA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Công nhân/tổ trưởng & Quản lý sản xuất)
• chat agent trả lời trạng thái dây chuyền từ dữ liệu mô phỏng, có trích nguồn
• memory hội thoại
• hiển thị dashboard trạng thái máy.

Nâng cao:
• Agent chủ động cảnh báo khi có bất thường (máy dừng, sản lượng tụt)
• tool tính OEE theo yêu cầu
• đề xuất nguyên nhân & hành động
• HITL cho đề xuất can thiệp
• xử lý câu hỏi mơ hồ bằng hỏi lại
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-03] AI Agent Bảo Trì Dự Đoán Từ Dữ Liệu Cảm Biến Máy (Predictive Maintenance Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Thiết bị trong xưởng dập/hàn của nhà máy được bảo trì theo lịch cố định hoặc chỉ sửa khi hỏng, gây dừng máy đột xuất tốn kém. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát dữ liệu cảm biến (rung, nhiệt độ, dòng điện) để dự đoán hư hỏng sớm, ước lượng thời gian còn lại (RUL), lập kế hoạch bảo trì và tạo phiếu công việc; giải thích dấu hiệu bất thường; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Đề xuất dừng máy để bảo trì phải qua HITL (kỹ sư bảo trì duyệt); tuân thủ an toàn khi thao tác thiết bị; bảo mật thông số vận hành thiết bị; cân bằng giữa cảnh báo sớm (giảm downtime) và false alarm; độ trễ phát hiện hợp lý cho realtime. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + LangGraph điều phối
• mô hình time-series anomaly detection (Isolation Forest/LSTM autoencoder) + hồi quy RUL
• InfluxDB/TimescaleDB
• bộ giả lập cảm biến máy (Python phát dữ liệu + kịch bản suy thoái)
• backend FastAPI
• frontend React dashboard
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark lập lịch sản xuất Job-Shop Taillard / OR-Library, dữ liệu định mức vật tư đa cấp (multi-level BOM & MRP) và chuẩn nhà máy ISA-95 / OPC-UA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Kỹ sư bảo trì & Quản lý xưởng)
• nhận stream cảm biến mô phỏng, phát hiện bất thường, agent giải thích và đề xuất bảo trì
• tạo phiếu bảo trì
• memory lịch sử thiết bị.

Nâng cao:
• Dự đoán RUL và xếp ưu tiên nhiều máy
• agent lập lịch bảo trì tối ưu tránh dừng dây chuyền
• HITL duyệt kế hoạch dừng máy
• cảnh báo mức độ tin cậy dự đoán
• báo cáo tiết kiệm downtime
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-04] AI Agent Kiểm Tra Chất Lượng Bề Mặt Bằng Computer Vision (Visual QC Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Kiểm tra lỗi bề mặt thân vỏ xe/tấm pin (xước, móp, lỗi sơn) chủ yếu bằng mắt thường, phụ thuộc kinh nghiệm và mệt mỏi của công nhân, dễ bỏ sót. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent nhận ảnh sản phẩm từ trạm kiểm tra, phát hiện & phân loại lỗi, khoanh vùng, quyết định PASS/FAIL/cần người kiểm, ghi nhận và thống kê lỗi theo lô; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Sản phẩm nghi ngờ hoặc lỗi nghiêm trọng phải chuyển HITL (QC duyệt trước khi loại bỏ); an toàn khi tích hợp trạm; bảo mật hình ảnh sản phẩm (bí mật thiết kế); cân bằng độ chính xác (không để lọt lỗi lẫn không loại nhầm hàng tốt); độ trễ đủ nhanh cho nhịp dây chuyền. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• Computer Vision (YOLOv8/Detectron2 phát hiện lỗi) + LLM đa phương thức (mô tả/giải thích lỗi)
• LangGraph điều phối (detect → classify → decide → HITL)
• dataset ảnh lỗi mô phỏng/công khai
• backend FastAPI + lưu ảnh (S3/MinIO)
• frontend React hiển thị bounding box
• deploy cloud có GPU/CPU inference.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu kiểm tra khuyết tật bề mặt công nghiệp MVTec AD / VisA / NEU Surface Defect, bộ dữ liệu bảo hộ lao động SH17 / Pictor-PPE và tài liệu SOP / FMEA / bản vẽ kỹ thuật.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Công nhân trạm QC & Trưởng QC)
• upload/stream ảnh, agent phát hiện lỗi có khoanh vùng, quyết định PASS/FAIL, giải thích
• HITL review
• thống kê lỗi theo lô.

Nâng cao:
• Phân loại nhiều loại lỗi + mức nghiêm trọng
• agent phân tích xu hướng lỗi theo thời gian/ca và cảnh báo cụm lỗi bất thường
• đề xuất nguyên nhân
• ngưỡng tin cậy để tự động chuyển người khi mơ hồ
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-05] AI Agent Phân Tích Nguyên Nhân Gốc Lỗi Sản Xuất (Root Cause Analysis Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Khi tỷ lệ lỗi tăng đột biến, kỹ sư chất lượng phải truy vết thủ công qua log thông số máy, lô nguyên liệu, ca công nhân để tìm nguyên nhân, tốn nhiều ngày. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tự động phân tích dữ liệu đa nguồn (thông số quy trình, nguyên liệu, thiết bị, con người), lập giả thuyết nguyên nhân gốc theo phương pháp 5-Why/Fishbone, kiểm chứng bằng dữ liệu và đề xuất hành động khắc phục; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Kết luận & hành động khắc phục phải được kỹ sư duyệt (HITL); bảo mật dữ liệu quy trình & bí mật công nghệ; đảm bảo agent lập luận dựa trên bằng chứng (không suy diễn vô căn cứ); minh bạch chuỗi suy luận. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + LangGraph (agent nhiều bước: thu thập → tương quan → giả thuyết → kiểm chứng → khuyến nghị)
• phân tích tương quan/thống kê (pandas, scipy) và feature importance
• PostgreSQL + dữ liệu sản xuất mô phỏng có 'nguyên nhân ẩn'
• RAG trên lịch sử sự cố
• backend FastAPI
• frontend React (Fishbone/5-Why viz)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark lập lịch sản xuất Job-Shop Taillard / OR-Library, dữ liệu định mức vật tư đa cấp (multi-level BOM & MRP) và chuẩn nhà máy ISA-95 / OPC-UA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Kỹ sư chất lượng & Quản lý)
• nhập sự cố lỗi tăng, agent phân tích dữ liệu mô phỏng, đưa cây nguyên nhân có bằng chứng, đề xuất khắc phục
• HITL duyệt
• memory lưu case.

Nâng cao:
• Xếp hạng giả thuyết theo xác suất, agent tự chạy kiểm chứng thống kê bằng tool
• đối chiếu sự cố tương tự trong quá khứ (RAG)
• theo dõi hiệu quả sau khắc phục
• cảnh báo khi dữ liệu không đủ để kết luận
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-06] AI Agent Trợ Lý An Toàn Lao Động & Tuân Thủ EHS (EHS Safety Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Quy định an toàn (EHS) tại nhà máy pin nhà máy sản xuất pin của doanh nghiệp rất nhiều (hóa chất, điện áp cao, PCCC), công nhân khó tra cứu nhanh; báo cáo sự cố an toàn còn thủ công, chậm. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent trợ lý an toàn: hỏi-đáp quy định EHS, hướng dẫn xử lý tình huống nguy hiểm, tiếp nhận & phân loại báo cáo sự cố/near-miss, đánh giá rủi ro và tạo hành động khắc phục; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Sự cố an toàn nghiêm trọng phải escalate ngay tới người phụ trách (HITL bắt buộc); tư vấn phải bám quy định chính thức (RAG, không bịa); ưu tiên tính mạng con người; bảo mật dữ liệu sự cố; cảnh báo rõ khi câu hỏi vượt phạm vi an toàn cho phép tự trả lời. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + RAG trên bộ quy định EHS/MSDS (vector DB: Chroma/pgvector)
• LangGraph (triage → tra cứu → đánh giá rủi ro → escalate)
• backend FastAPI
• frontend React (form báo cáo + chat)
• tích hợp cảnh báo (email/webhook)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu kiểm tra khuyết tật bề mặt công nghiệp MVTec AD / VisA / NEU Surface Defect, bộ dữ liệu bảo hộ lao động SH17 / Pictor-PPE và tài liệu SOP / FMEA / bản vẽ kỹ thuật.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Công nhân & Cán bộ an toàn EHS)
• chat tra cứu quy định có trích nguồn
• form báo cáo sự cố, agent phân loại mức độ
• escalate sự cố nặng
• memory lịch sử.

Nâng cao:
• Agent đánh giá rủi ro (ma trận likelihood/severity) và sinh CAPA
• dashboard thống kê sự cố theo khu vực
• nhắc nhở kiểm tra định kỳ
• phát hiện cụm near-miss bất thường
• đa ngôn ngữ
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-07] AI Agent Tối Ưu Tồn Kho Nguyên Vật Liệu & Chuỗi Cung Ứng Nhà Máy (Inventory & Supply Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Kho nguyên vật liệu nhà máy vừa tồn dư linh kiện chậm luân chuyển, vừa thiếu hụt vật tư quan trọng gây dừng chuyền; kế hoạch mua thủ công theo kinh nghiệm. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent dự báo nhu cầu vật tư theo kế hoạch sản xuất, tính điểm đặt hàng/safety stock, phát hiện nguy cơ thiếu hụt, đề xuất đơn mua và cảnh báo rủi ro nhà cung cấp; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Đề xuất tạo đơn mua phải qua HITL (bộ phận mua duyệt); bảo mật dữ liệu giá/nhà cung cấp; độ chính xác dự báo có khoảng tin cậy; cảnh báo khi dữ liệu lịch sử không đủ; không tự động đặt hàng. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + LangGraph (forecast → phân tích tồn kho → đề xuất mua → HITL)
• mô hình dự báo (Prophet/statsmodels)
• PostgreSQL (BOM, tồn kho, lead time mô phỏng)
• mô phỏng ERP qua API
• backend FastAPI
• frontend React dashboard tồn kho
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark lập lịch sản xuất Job-Shop Taillard / OR-Library, dữ liệu định mức vật tư đa cấp (multi-level BOM & MRP) và chuẩn nhà máy ISA-95 / OPC-UA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Nhân viên kế hoạch vật tư & Trưởng mua hàng)
• agent dự báo nhu cầu từ kế hoạch SX mô phỏng, cảnh báo vật tư sắp thiếu, đề xuất đơn mua
• HITL duyệt
• memory.

Nâng cao:
• Tối ưu safety stock đa vật tư theo lead time & biến động
• mô phỏng kịch bản gián đoạn nhà cung cấp
• agent xếp ưu tiên vật tư rủi ro cao
• dashboard cảnh báo & KPI (fill rate, tồn kho ứ đọng)
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-08] AI Agent Điều Phối Lệnh Sản Xuất (Work Order Orchestration Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Lệnh sản xuất (work order) được phát và theo dõi qua giấy/Excel, khó biết lệnh nào trễ, thiếu vật tư hay chờ máy; điều độ viên phản ứng chậm với thay đổi. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent quản lý vòng đời work order: kiểm tra điều kiện sẵn sàng (vật tư, máy, nhân lực), phát lệnh, theo dõi tiến độ, tự động điều chỉnh thứ tự khi có tắc nghẽn và thông báo các bên; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Phát/hủy/đổi lệnh tác động dây chuyền phải qua HITL (điều độ viên duyệt); bảo mật dữ liệu sản xuất; đảm bảo không phát lệnh khi thiếu điều kiện; độ trễ cập nhật trạng thái thấp; log đầy đủ để truy vết. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + LangGraph (state machine work order: created → ready check → released → in-progress → done, có nhánh HITL)
• PostgreSQL
• MES/kho giả lập qua API
• backend FastAPI + WebSocket
• frontend React (Kanban work order)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark lập lịch sản xuất Job-Shop Taillard / OR-Library, dữ liệu định mức vật tư đa cấp (multi-level BOM & MRP) và chuẩn nhà máy ISA-95 / OPC-UA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Điều độ viên & Tổ trưởng chuyền)
• agent kiểm tra điều kiện và đề xuất phát lệnh, theo dõi tiến độ Kanban, cảnh báo lệnh trễ
• HITL duyệt phát lệnh
• memory.

Nâng cao:
• Tự động đề xuất tái sắp thứ tự khi tắc nghẽn
• agent phối hợp với kho để giữ vật tư
• thông báo đa bên
• dashboard OTIF & WIP
• xử lý ngoại lệ (thiếu vật tư giữa chừng)
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-09] AI Agent Trợ Lý Kỹ Sư Tra Cứu SOP & Bản Vẽ Kỹ Thuật (Engineering Knowledge Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Kỹ sư & công nhân mất nhiều thời gian tìm đúng phiên bản SOP, hướng dẫn công việc, thông số kỹ thuật trong hàng nghìn tài liệu; dùng nhầm bản cũ gây lỗi. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hỏi-đáp trên kho tài liệu kỹ thuật (SOP, WI, thông số, bản vẽ), trả lời chính xác kèm trích dẫn đúng phiên bản, tóm tắt các bước, so sánh phiên bản và hướng dẫn thao tác; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Luôn trích nguồn & phiên bản tài liệu (không bịa thông số); chỉ trả tài liệu theo phân quyền; bảo mật bí mật công nghệ/bản vẽ; cảnh báo khi tài liệu đã hết hiệu lực; câu hỏi ngoài phạm vi phải nói rõ không đủ căn cứ. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + RAG nâng cao (vector DB pgvector/Chroma, hybrid search, re-ranking)
• OCR/parse PDF & bản vẽ (unstructured/pymupdf)
• LangGraph (retrieve → verify version → answer với citation)
• backend FastAPI
• frontend React (chat + viewer tài liệu highlight)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu kiểm tra khuyết tật bề mặt công nghiệp MVTec AD / VisA / NEU Surface Defect, bộ dữ liệu bảo hộ lao động SH17 / Pictor-PPE và tài liệu SOP / FMEA / bản vẽ kỹ thuật.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Công nhân vận hành & Kỹ sư quản lý tài liệu)
• chat tra cứu SOP có trích dẫn phiên bản, mở đúng đoạn tài liệu
• memory hội thoại
• upload tài liệu.

Nâng cao:
• So sánh & cảnh báo phiên bản lỗi thời
• agent tóm tắt quy trình theo bước có checklist
• phân quyền tài liệu theo vai trò
• phản hồi 'không tìm thấy' trung thực
• multi-hop qua nhiều tài liệu
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-10] AI Agent Giám Sát Năng Lượng Nhà Máy & Tối Ưu Tiêu Thụ (Energy Optimization Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhà máy thép doanh nghiệp sản xuất vật liệu tiêu thụ điện lớn, chi phí năng lượng cao, khó nhận diện thiết bị/khung giờ lãng phí và tối ưu theo giá điện theo giờ. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát tiêu thụ điện theo khu vực/thiết bị, phát hiện bất thường & lãng phí, dự báo phụ tải, đề xuất dịch chuyển tải và lịch vận hành tối ưu theo giá điện, ước tính tiết kiệm & giảm CO2; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Đề xuất điều chỉnh vận hành thiết bị phải qua HITL (kỹ sư năng lượng duyệt); không được ảnh hưởng an toàn & sản lượng; bảo mật dữ liệu vận hành; dự báo có khoảng tin cậy; cảnh báo khi vượt ngưỡng công suất hợp đồng. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + LangGraph (giám sát → phát hiện bất thường → dự báo → khuyến nghị → HITL)
• time-series (InfluxDB) + mô hình dự báo phụ tải
• anomaly detection
• bộ giả lập đồng hồ điện & giá điện TOU
• backend FastAPI
• frontend React dashboard năng lượng
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark lập lịch sản xuất Job-Shop Taillard / OR-Library, dữ liệu định mức vật tư đa cấp (multi-level BOM & MRP) và chuẩn nhà máy ISA-95 / OPC-UA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Kỹ sư năng lượng & Quản lý nhà máy)
• agent giám sát tiêu thụ mô phỏng, phát hiện lãng phí, đề xuất tối ưu, ước tính tiết kiệm
• HITL
• memory.

Nâng cao:
• Dự báo phụ tải & tối ưu lịch chạy theo giá điện TOU
• cảnh báo peak vượt hợp đồng
• phân bổ chi phí năng lượng theo sản phẩm
• báo cáo phát thải CO2
• kịch bản what-if
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-11] AI Agent Dự Báo Năng Suất & Tối Ưu OEE (OEE Analytics Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Chỉ số OEE (khả dụng, hiệu suất, chất lượng) được tổng hợp cuối ca, chậm, khó biết yếu tố nào kéo tụt hiệu quả và dự báo năng suất còn lại của ca. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tính OEE realtime, phân rã tổn thất (six big losses), dự báo sản lượng cuối ca, xác định nút thắt và đề xuất cải thiện; giải thích rõ nguyên nhân tụt OEE; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Đề xuất can thiệp vận hành qua HITL (quản đốc duyệt); bảo mật dữ liệu năng suất; số liệu OEE phải nhất quán & truy vết được; dự báo kèm độ tin cậy; độ trễ cập nhật thấp. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + LangGraph (tính OEE → phân rã tổn thất → dự báo → khuyến nghị)
• time-series DB
• mô hình dự báo sản lượng (regression/Prophet)
• giả lập dữ liệu máy (downtime, cycle time, phế phẩm)
• backend FastAPI
• frontend React (OEE waterfall, gauge)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark lập lịch sản xuất Job-Shop Taillard / OR-Library, dữ liệu định mức vật tư đa cấp (multi-level BOM & MRP) và chuẩn nhà máy ISA-95 / OPC-UA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Tổ trưởng & Quản đốc)
• agent tính & giải thích OEE theo dây chuyền từ dữ liệu mô phỏng, phân rã 6 tổn thất
• memory
• dashboard.

Nâng cao:
• Dự báo sản lượng cuối ca + cảnh báo sớm không đạt target
• xác định nút thắt & đề xuất hành động ưu tiên
• so sánh ca/dây chuyền
• theo dõi hiệu quả cải tiến
• HITL cho hành động
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-12] AI Agent Truy Xuất Nguồn Gốc Linh Kiện & Pin (Traceability Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Với pin xe điện của doanh nghiệp, khi phát hiện lỗi cần truy ngược lô nguyên liệu, thông số quá trình, thiết bị đã dùng cho từng cell/pack; tra cứu thủ công rất chậm, khó khoanh vùng thu hồi. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent truy xuất genealogy: từ serial sản phẩm truy ngược toàn bộ chuỗi (lô vật liệu, máy, ca, thông số), khoanh vùng sản phẩm bị ảnh hưởng khi có lỗi lô, và hỗ trợ quyết định thu hồi; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Quyết định thu hồi/cách ly lô phải qua HITL (quản lý chất lượng duyệt); bảo mật dữ liệu truy xuất & bí mật công nghệ; dữ liệu genealogy phải chính xác & bất biến; cảnh báo phạm vi ảnh hưởng rõ ràng; độ trễ truy vấn thấp. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + LangGraph (query genealogy → phân tích ảnh hưởng → khuyến nghị → HITL)
• graph model (Neo4j hoặc PostgreSQL quan hệ) mô phỏng liên kết vật liệu-quá trình-sản phẩm
• backend FastAPI
• frontend React (genealogy graph viz)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu bảo trì dự đoán & kiểm soát quy trình sản xuất NASA C-MAPSS (ước lượng RUL), AI4I 2020 Predictive Maintenance, CWRU Bearing Vibration, SECOM và chuẩn phả hệ linh kiện GS1 EPCIS.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Kỹ sư QC & Quản lý chất lượng)
• nhập serial/lô, agent truy xuất chuỗi genealogy và hiển thị cây nguồn gốc
• khoanh vùng sản phẩm cùng lô lỗi
• memory.

Nâng cao:
• Phân tích ảnh hưởng khi lỗi 1 lô vật liệu → liệt kê toàn bộ pack/cell liên quan
• đề xuất phạm vi thu hồi tối thiểu
• HITL duyệt cách ly
• báo cáo truy xuất
• hỏi-đáp bằng ngôn ngữ tự nhiên
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-13] AI Agent Kiểm Soát Chất Lượng Đầu Vào IQC (Incoming Quality Control Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Nguyên vật liệu/linh kiện nhập về được kiểm tra thủ công theo checklist và chứng từ CoA của nhà cung cấp; quyết định chấp nhận lô dựa nhiều vào kinh nghiệm, thiếu đánh giá rủi ro nhà cung cấp. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hỗ trợ IQC: đọc/đối chiếu CoA với tiêu chuẩn, đề xuất mức kiểm mẫu theo AQL & lịch sử nhà cung cấp, tổng hợp kết quả đo, quyết định chấp nhận/từ chối/kiểm bổ sung; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Quyết định từ chối/chấp nhận lô phải qua HITL (nhân viên IQC duyệt); đối chiếu tiêu chuẩn không được bịa (RAG chuẩn kỹ thuật); bảo mật dữ liệu nhà cung cấp; độ chính xác cao; cảnh báo khi chứng từ thiếu/không khớp. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM (đọc CoA, đối chiếu) + RAG tiêu chuẩn kỹ thuật
• LangGraph (parse CoA → so tiêu chuẩn → tính AQL → decide → HITL)
• OCR chứng từ
• PostgreSQL (lịch sử NCC, lô)
• backend FastAPI
• frontend React (form IQC)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark lập lịch sản xuất Job-Shop Taillard / OR-Library, dữ liệu định mức vật tư đa cấp (multi-level BOM & MRP) và chuẩn nhà máy ISA-95 / OPC-UA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Nhân viên IQC & Trưởng QC)
• upload CoA + nhập kết quả đo, agent đối chiếu tiêu chuẩn và đề xuất chấp nhận/từ chối có lý do
• HITL
• memory lịch sử lô.

Nâng cao:
• Đánh giá & xếp hạng rủi ro nhà cung cấp theo lịch sử, tự điều chỉnh mức kiểm mẫu (skip-lot/tightened)
• cảnh báo NCC suy giảm chất lượng
• dashboard IQC
• phát hiện CoA bất thường
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-14] AI Agent Phát Hiện Bất Thường Quy Trình (SPC & Process Anomaly Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Thông số quy trình (nhiệt độ lò, áp suất, mô-men siết) được ghi nhưng ít được giám sát liên tục; sai lệch nhỏ tích lũy dẫn tới lỗi hàng loạt mới bị phát hiện muộn. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát SPC realtime, phát hiện xu hướng trôi/vi phạm luật kiểm soát (Western Electric rules), cảnh báo sớm out-of-control, giải thích và đề xuất hiệu chỉnh trước khi phát sinh phế phẩm; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Đề xuất hiệu chỉnh thông số máy phải qua HITL (kỹ sư quá trình duyệt); an toàn thiết bị; bảo mật thông số công nghệ; giảm false alarm; độ trễ phát hiện thấp cho realtime. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + LangGraph (giám sát → áp luật SPC/anomaly → giải thích → khuyến nghị → HITL)
• time-series DB
• thư viện SPC (control charts) + anomaly detection
• giả lập dữ liệu quá trình có drift/shift
• backend FastAPI + WebSocket
• frontend React (control chart realtime)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu bảo trì dự đoán & kiểm soát quy trình sản xuất NASA C-MAPSS (ước lượng RUL), AI4I 2020 Predictive Maintenance, CWRU Bearing Vibration, SECOM và chuẩn phả hệ linh kiện GS1 EPCIS.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Vận hành & Kỹ sư quá trình)
• agent giám sát thông số mô phỏng, vẽ control chart, phát hiện vi phạm SPC và giải thích
• cảnh báo
• memory.

Nâng cao:
• Phát hiện đa biến (nhiều thông số tương quan)
• phân biệt nguyên nhân thông thường/đặc biệt
• dự báo nguy cơ out-of-spec
• HITL duyệt hiệu chỉnh
• tổng hợp Cp/Cpk theo lô
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-15] AI Agent Đào Tạo & Hỗ Trợ Công Nhân Vận Hành (Operator Training Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Công nhân mới cần thời gian dài để thành thạo quy trình vận hành máy; đào tạo phụ thuộc người kèm, không đồng đều, khó đánh giá năng lực. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent gia sư: hướng dẫn quy trình vận hành theo từng bước, trả lời thắc mắc dựa trên SOP, tạo bài kiểm tra tình huống, chấm & phản hồi, theo dõi tiến độ và đề xuất lộ trình học cá nhân hóa; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Hướng dẫn thao tác phải bám SOP chính thức (RAG, không bịa bước); nội dung an toàn phải chính xác tuyệt đối; escalate cho người phụ trách khi tình huống nguy hiểm/ngoài phạm vi (HITL); bảo mật tài liệu đào tạo; phân quyền theo vai trò. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + RAG trên SOP/WI
• LangGraph (tutor: giảng → hỏi → chấm → cá nhân hóa)
• vector DB
• PostgreSQL (tiến độ học)
• backend FastAPI
• frontend React (learning UI + quiz)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu kiểm tra khuyết tật bề mặt công nghiệp MVTec AD / VisA / NEU Surface Defect, bộ dữ liệu bảo hộ lao động SH17 / Pictor-PPE và tài liệu SOP / FMEA / bản vẽ kỹ thuật.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Công nhân học viên & Quản lý đào tạo)
• agent hướng dẫn quy trình theo bước từ SOP, hỏi-đáp có trích nguồn, tạo & chấm quiz
• memory tiến độ
• dashboard.

Nâng cao:
• Lộ trình học cá nhân hóa theo điểm yếu
• tình huống mô phỏng ra quyết định
• đánh giá năng lực & cấp chứng nhận
• agent nhắc ôn tập
• escalate câu hỏi an toàn cho người thật
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-16] AI Agent Quản Lý Bảo Trì Thiết Bị & Phụ Tùng (CMMS Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Công việc bảo trì (phòng ngừa & sửa chữa) và kho phụ tùng quản lý rời rạc; kỹ thuật viên nhận việc qua bộ đàm/giấy, phụ tùng thay thế thiếu khi cần, lịch sử thiết bị không đầy đủ. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent CMMS: tự tạo & phân công phiếu bảo trì, gợi ý quy trình sửa chữa và phụ tùng cần dùng từ lịch sử, kiểm tra tồn kho phụ tùng, đặt trước và lập lịch bảo trì phòng ngừa tối ưu; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Lệnh dừng máy để bảo trì & xuất phụ tùng phải qua HITL (trưởng bảo trì duyệt); an toàn khóa nguồn (LOTO); bảo mật dữ liệu thiết bị; đảm bảo không lập lịch trùng gây dừng chuyền ngoài kế hoạch; truy vết đầy đủ. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + RAG lịch sử bảo trì & tài liệu thiết bị
• LangGraph (tạo phiếu → gợi ý phụ tùng → kiểm kho → lập lịch → HITL)
• PostgreSQL (asset, WO, spare parts)
• backend FastAPI
• frontend React (lịch bảo trì + kho phụ tùng)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark lập lịch sản xuất Job-Shop Taillard / OR-Library, dữ liệu định mức vật tư đa cấp (multi-level BOM & MRP) và chuẩn nhà máy ISA-95 / OPC-UA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Kỹ thuật viên & Trưởng bảo trì)
• agent tạo/phân công phiếu bảo trì, gợi ý phụ tùng & bước sửa từ lịch sử, kiểm tồn kho
• HITL duyệt
• memory hồ sơ thiết bị.

Nâng cao:
• Tối ưu lịch bảo trì phòng ngừa tránh trùng dừng chuyền
• cảnh báo phụ tùng sắp hết & tự đề xuất bổ sung
• phân tích MTBF/MTTR
• gợi ý chẩn đoán từ triệu chứng
• báo cáo chi phí bảo trì
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-17] AI Agent Phân Tích Phế Phẩm & Lãng Phí (Scrap & Waste Reduction Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Phế phẩm và lãng phí (scrap, rework, nguyên liệu dư) làm tăng chi phí nhưng dữ liệu phân tán, khó biết công đoạn/sản phẩm nào tốn kém nhất và vì sao. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tổng hợp dữ liệu phế phẩm theo công đoạn/sản phẩm/ca, phân tích Pareto các loại lãng phí, quy đổi chi phí, tìm tương quan nguyên nhân và đề xuất hành động giảm thải theo tư duy Lean; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Hành động thay đổi quy trình phải qua HITL (kỹ sư cải tiến duyệt); phân tích dựa bằng chứng; bảo mật dữ liệu chi phí; số liệu chi phí phải nhất quán; cảnh báo khi dữ liệu thiếu để kết luận. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + LangGraph (tổng hợp → Pareto → tương quan → khuyến nghị Lean → HITL)
• phân tích dữ liệu (pandas), quy đổi chi phí
• PostgreSQL dữ liệu phế phẩm mô phỏng
• backend FastAPI
• frontend React (Pareto, cost dashboard)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu bảo trì dự đoán & kiểm soát quy trình sản xuất NASA C-MAPSS (ước lượng RUL), AI4I 2020 Predictive Maintenance, CWRU Bearing Vibration, SECOM và chuẩn phả hệ linh kiện GS1 EPCIS.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Kỹ sư cải tiến & Quản lý sản xuất)
• agent phân tích phế phẩm mô phỏng, vẽ Pareto, quy đổi chi phí lãng phí, đề xuất cải tiến
• HITL
• memory.

Nâng cao:
• Tương quan phế phẩm với thông số/nguyên liệu/ca
• ưu tiên hành động theo ROI
• theo dõi hiệu quả trước-sau cải tiến
• mô phỏng tiết kiệm
• cảnh báo tăng đột biến scrap
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-18] AI Agent Cảnh Báo & Xử Lý Sự Cố Dây Chuyền Realtime (Line Incident Response Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Khi dây chuyền gặp sự cố (kẹt, dừng, lỗi máy), thông tin đến chậm, xử lý phụ thuộc kinh nghiệm người trực; thời gian dừng kéo dài gây thiệt hại lớn. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát tín hiệu dây chuyền, phát hiện & phân loại sự cố realtime, gợi ý quy trình xử lý (playbook) theo loại sự cố, thông báo đúng người, theo dõi đến khi khắc phục và ghi nhận báo cáo sự cố; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Mọi lệnh dừng/khởi động lại dây chuyền phải qua HITL (trưởng ca duyệt); ưu tiên an toàn con người & thiết bị; bảo mật dữ liệu; độ trễ phát hiện & thông báo cực thấp; escalate tự động khi quá thời gian xử lý; log truy vết đầy đủ. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM + RAG playbook xử lý sự cố
• LangGraph (detect → phân loại → gợi ý playbook → thông báo → theo dõi → HITL/escalate)
• giả lập tín hiệu dây chuyền + kịch bản sự cố (WebSocket/MQTT)
• backend FastAPI
• frontend React (bảng điều khiển sự cố realtime)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu bảo trì dự đoán & kiểm soát quy trình sản xuất NASA C-MAPSS (ước lượng RUL), AI4I 2020 Predictive Maintenance, CWRU Bearing Vibration, SECOM và chuẩn phả hệ linh kiện GS1 EPCIS.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Trưởng ca & Kỹ thuật trực)
• inject sự cố mô phỏng, agent phát hiện, phân loại, gợi ý playbook và thông báo
• HITL cho lệnh dừng/khởi động
• memory nhật ký sự cố.

Nâng cao:
• Escalate tự động theo SLA thời gian
• ước lượng tác động (mất sản lượng)
• gợi ý ưu tiên khi nhiều sự cố
• tự sinh báo cáo sự cố sau xử lý
• thống kê MTTR & sự cố lặp lại
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-19] AI Agent Lập & Tối Ưu Lịch Chạy Máy Giảm Thời Gian Chuyển Đổi (Machine Scheduling & Changeover Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Trên một máy/tổ máy chạy nhiều loại sản phẩm, thứ tự chạy chưa tối ưu khiến thời gian chuyển đổi khuôn/màu/thông số (changeover) lớn, giảm năng suất. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent sắp xếp thứ tự lệnh trên từng máy để tối thiểu tổng thời gian changeover và trễ hạn, xét ma trận thời gian chuyển đổi phụ thuộc trình tự, ràng buộc khuôn/nhân lực, và tái tối ưu khi có lệnh chèn; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Áp dụng lịch xuống máy phải qua HITL (điều độ duyệt); bảo mật dữ liệu sản xuất; lịch phải khả thi (không xung đột khuôn/nhân lực); giải thích được đánh đổi; cảnh báo khi bài toán quá lớn vượt khả năng tối ưu trong thời gian cho phép. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• LLM (diễn giải ràng buộc & giải thích) + LangGraph
• solver tối ưu (OR-Tools CP-SAT cho sequence-dependent setup scheduling)
• PostgreSQL (ma trận changeover, khuôn, đơn)
• MES giả lập
• backend FastAPI
• frontend React (Gantt theo máy)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark lập lịch sản xuất Job-Shop Taillard / OR-Library, dữ liệu định mức vật tư đa cấp (multi-level BOM & MRP) và chuẩn nhà máy ISA-95 / OPC-UA.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Điều độ viên & Quản đốc)
• agent nhận đơn + ma trận changeover mô phỏng, sinh thứ tự chạy tối ưu trên máy dạng Gantt, giải thích lợi ích
• HITL
• memory.

Nâng cao:
• Tái tối ưu khi chèn lệnh gấp
• tối ưu đa mục tiêu (changeover + đúng hạn)
• xét ràng buộc khuôn/nhân lực dùng chung nhiều máy
• so sánh kịch bản
• cảnh báo giới hạn thời gian giải & đưa lời giải tốt nhất hiện có
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---

## [MFG-20] AI Agent Giám Sát An Toàn PPE & Khu Vực Nguy Hiểm Bằng Computer Vision (PPE & Zone Safety Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhà máy có khu vực nguy hiểm (máy dập, xe nâng, hóa chất) yêu cầu đội mũ/kính/găng đúng quy định và không xâm nhập vùng cấm; giám sát bằng người không xuể, vi phạm dễ bị bỏ sót. Trong môi trường nhà máy sản xuất công nghiệp, kế hoạch chuyền, định mức vật tư (BOM), thông số cảm biến máy móc và tiêu chuẩn chất lượng có ràng buộc vật lý chặt chẽ; một sự cố máy hỏng đột xuất hoặc lô linh kiện lỗi đều gây hiệu ứng dây chuyền.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích luồng camera phát hiện thiếu PPE và người xâm nhập vùng cấm khi máy đang chạy, cảnh báo realtime, ghi nhận vi phạm và thống kê tuân thủ theo khu vực/ca; đồng thời kết hợp bộ giải tối ưu hóa toán học (OR-Tools cho lập lịch/vật tư), kiểm soát thống kê quy trình (SPC/FFT cho bảo trì) hoặc thị giác máy tính định vị lỗi với khả năng suy luận nguyên nhân gốc rễ (5-Whys/Ishikawa) và điều phối phương án đánh đổi của AI Agent.

🔒 Ràng buộc: Cảnh báo nguy hiểm nghiêm trọng (người trong vùng nguy hiểm) escalate ngay tới người phụ trách (HITL); tôn trọng quyền riêng tư (làm mờ danh tính, chỉ lưu vi phạm); bảo mật dữ liệu hình ảnh; cân bằng độ chính xác/false alarm; độ trễ phát hiện thấp; ưu tiên an toàn con người. Mọi bài toán lập lịch chuyền, tính toán tồn kho BOM và ngưỡng cảnh báo rung động/SPC phải do solver/thuật toán xác định tính toán; LLM đảm nhiệm biên dịch ràng buộc phát sinh, đối chiếu SOP/FMEA và giải thích phương án.

### 🛠️ Tech Stack
• Computer Vision (YOLOv8 phát hiện người + PPE, định nghĩa vùng cấm) + LLM (mô tả sự việc, sinh cảnh báo/báo cáo)
• LangGraph (detect → đối chiếu quy tắc vùng/máy → cảnh báo → escalate)
• xử lý video (OpenCV), làm mờ khuôn mặt
• backend FastAPI + WebSocket
• frontend React (live view + nhật ký vi phạm)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu kiểm tra khuyết tật bề mặt công nghiệp MVTec AD / VisA / NEU Surface Defect, bộ dữ liệu bảo hộ lao động SH17 / Pictor-PPE và tài liệu SOP / FMEA / bản vẽ kỹ thuật.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Cán bộ an toàn & Quản lý khu vực)
• phân tích video/ảnh mô phỏng, phát hiện thiếu PPE & xâm nhập vùng cấm, cảnh báo realtime có khoanh vùng, làm mờ danh tính
• nhật ký vi phạm
• memory.

Nâng cao:
• Kết hợp trạng thái máy (chỉ cảnh báo khi máy chạy) giảm false alarm
• escalate tự động sự cố nghiêm trọng
• dashboard tỷ lệ tuân thủ theo khu vực/ca
• báo cáo an toàn định kỳ
• ngưỡng tin cậy chuyển người khi mơ hồ
• Kết hợp chặt chẽ bộ giải tối ưu hóa/phân tích tín hiệu xác định với suy luận đa tác tử để tái lập kế hoạch sản xuất hoặc truy vết phả hệ lô hàng – nguyên nhân gốc rễ trong thời gian thực.

---
