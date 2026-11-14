# Lĩnh vực: ITOPS - Phần mềm dùng chung – IT Helpdesk, Hạ tầng & ERP

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `ITOPS-01` | [AI Agent Phân loại & Xử lý Ticket IT Help Desk (ITSM Triage Agent)](#itops-01) |
| `ITOPS-02` | [AI Agent Trợ lý Tự phục vụ IT (Reset mật khẩu, Cấp quyền cơ bản)](#itops-02) |
| `ITOPS-03` | [AI Agent Giám sát Hạ tầng & Chẩn đoán Sự cố (Infra Monitoring Agent)](#itops-03) |
| `ITOPS-04` | [AI Agent Trợ lý DevOps: Phân tích Log lỗi Build & CI/CD](#itops-04) |
| `ITOPS-05` | [AI Agent Hỏi đáp & Thao tác SAP bằng Ngôn ngữ Tự nhiên](#itops-05) |
| `ITOPS-06` | [AI Agent Tự động hóa Quy trình Mua hàng SAP (Tạo PO & Duyệt)](#itops-06) |
| `ITOPS-07` | [AI Agent Quản lý Tài sản CNTT (IT Asset Management Assistant)](#itops-07) |
| `ITOPS-08` | [AI Agent Tối ưu Chi phí Cloud (FinOps Hạ tầng)](#itops-08) |
| `ITOPS-09` | [AI Agent Trợ lý SOC: Phát hiện & Phản ứng Sự cố Bảo mật](#itops-09) |
| `ITOPS-10` | [AI Agent Quản lý Cấp phát & Thu hồi Quyền Truy cập (IAM Governance)](#itops-10) |
| `ITOPS-11` | [AI Agent Trợ lý Knowledge Base IT (IT KB Copilot)](#itops-11) |
| `ITOPS-12` | [AI Agent Tự động Phân tích & Xử lý Cảnh báo Giám sát (Alert Noise Reduction)](#itops-12) |
| `ITOPS-13` | [AI Agent Quản lý Thay đổi Hạ tầng (Change Management Agent)](#itops-13) |
| `ITOPS-14` | [AI Agent Hỗ trợ Migration & Nâng cấp Hệ thống](#itops-14) |
| `ITOPS-15` | [AI Agent Trợ lý Báo cáo SAP/BI bằng Ngôn ngữ Tự nhiên](#itops-15) |
| `ITOPS-16` | [AI Agent Phân tích Ticket Tồn đọng & Đề xuất Cải tiến (ITSM Analytics)](#itops-16) |
| `ITOPS-17` | [AI Agent Runbook Tự động Xử lý Sự cố Thường gặp (Auto-Remediation)](#itops-17) |
| `ITOPS-18` | [AI Agent Quản lý License & Tối ưu Chi phí Phần mềm (SAM)](#itops-18) |
| `ITOPS-19` | [AI Agent Onboarding/Offboarding Nhân sự IT (Access Provisioning)](#itops-19) |
| `ITOPS-20` | [AI Agent Trợ lý Vận hành SLA & Sức khỏe Dịch vụ IT (Service Health Copilot)](#itops-20) |

---

## [ITOPS-01] AI Agent Phân loại & Xử lý Ticket IT Help Desk (ITSM Triage Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Help desk của tập đoàn nhận hàng nghìn ticket/ngày từ nhân viên các công ty thành viên (doanh nghiệp bất động sản, doanh nghiệp ô tô, hệ thống y tế / bệnh viện...), phân loại và định tuyến thủ công, thời gian phản hồi chậm. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự đọc mô tả ticket, phân loại (category/priority/urgency), gợi ý giải pháp từ knowledge base, tự đóng ticket đơn giản và định tuyến ticket phức tạp đến đúng nhóm kỹ thuật, có leo thang SLA; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL bắt buộc trước khi tự đóng/định tuyến ticket ảnh hưởng đến hệ thống production hoặc VIP; phân quyền theo công ty thành viên & phòng ban; độ chính xác phân loại đo bằng accuracy/F1; audit log mọi hành động trên ticket; cảnh báo khi độ tin cậy phân loại thấp; kiểm soát chi phí token.

### 🛠️ Tech Stack
• LLM (GPT-4o/Claude) + LangGraph điều phối agent
• RAG trên knowledge base ITSM với vector DB (Qdrant/pgvector)
• tích hợp API ITSM (mô phỏng ServiceNow/Jira Service Management REST)
• classifier phân loại + confidence scoring
• backend FastAPI
• frontend Next.js (dashboard agent + hàng đợi ticket, phân vai người dùng/agent hỗ trợ)
• observability LangSmith/Langfuse
• deploy Vercel + Render/Railway.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy online có đăng nhập, ≥2 vai (nhân viên gửi ticket / kỹ thuật viên & quản lý), agent tự phân loại + gợi ý giải pháp từ RAG, nút phê duyệt HITL, audit log, dashboard SLA.

Nâng cao:
• Tự động đề xuất và thực thi runbook cho ticket đơn giản, memory học từ lịch sử xử lý, cảnh báo leo thang, báo cáo hiệu suất phân loại và phát hiện ticket lặp/bất thường
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-02] AI Agent Trợ lý Tự phục vụ IT (Reset mật khẩu, Cấp quyền cơ bản)

### 📝 Mô tả đề tài
📍 Thực trạng: Phần lớn yêu cầu IT là việc lặp lại như reset mật khẩu, mở khóa tài khoản, cấp quyền phần mềm cơ bản, gây tải cho help desk. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent hội thoại tự phục vụ hiểu yêu cầu bằng ngôn ngữ tự nhiên, xác thực danh tính người dùng, thực thi quy trình tự phục vụ (reset password, mở khóa, cấp/thu quyền theo chính sách) và bàn giao cho người khi vượt phạm vi; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL & xác thực đa yếu tố (MFA) bắt buộc trước hành động thay đổi tài khoản/quyền; phân quyền chặt theo vai trò & policy; không được cấp quyền vượt cấp; audit log đầy đủ ai-làm-gì-khi-nào; độ chính xác nhận diện ý định; cảnh báo hành vi bất thường/tấn công social engineering. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph state machine cho luồng xác thực
• RAG trên chính sách IAM
• tích hợp API IAM/AD mô phỏng (LDAP/SCIM mock)
• rule engine policy check
• MFA/OTP mock
• backend FastAPI
• frontend React (chat + trang admin duyệt yêu cầu)
• Langfuse tracing
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App online, đăng nhập ≥2 vai (người dùng cuối / IT admin), chat agent xử lý reset mật khẩu & mở khóa với xác thực, HITL cho cấp quyền, audit log.

Nâng cao:
• Agent tự kiểm tra policy trước khi cấp quyền, phát hiện yêu cầu rủi ro cần leo thang, memory hồ sơ người dùng, thống kê tỷ lệ tự động hóa & thời gian tiết kiệm
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-03] AI Agent Giám sát Hạ tầng & Chẩn đoán Sự cố (Infra Monitoring Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Hạ tầng đám mây & on-prem của doanh nghiệp sinh ra hàng loạt metric/alert (CPU, memory, latency, downtime) từ nhiều hệ thống; đội SRE khó theo dõi và chẩn đoán nguyên nhân gốc. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent theo dõi luồng metric/alert, phát hiện bất thường, tương quan nhiều tín hiệu để chẩn đoán root cause, đề xuất hành động khắc phục và tạo cảnh báo có ngữ cảnh; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL bắt buộc trước mọi hành động khắc phục trên production (restart service, scale); phân quyền theo cụm hạ tầng; độ chính xác chẩn đoán & tỷ lệ false-positive; audit log; kiểm soát độ trễ phát hiện và chi phí phân tích. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph agent phân tích
• time-series data mô phỏng (Prometheus/Grafana mock hoặc dataset)
• anomaly detection + tương quan
• RAG trên runbook & lịch sử sự cố (vector DB)
• tích hợp API alerting (mock PagerDuty)
• backend FastAPI + WebSocket cho realtime
• frontend Next.js dashboard giám sát
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark tự động hóa CNTT doanh nghiệp WorkArena (ITSM), SWE-bench, bộ dữ liệu log hệ thống phân tán Loghub (Kubernetes, Linux, HDFS) và chuẩn quan sát OpenTelemetry (Traces, Metrics, Logs).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard online realtime, đăng nhập ≥2 vai (SRE / trưởng nhóm vận hành), agent phát hiện bất thường + chẩn đoán nguyên nhân + đề xuất fix, HITL duyệt hành động, audit log.

Nâng cao:
• Tương quan đa nguồn cho root cause analysis, tự sinh báo cáo post-mortem, memory sự cố lặp lại, dự đoán sự cố tiềm ẩn, cảnh báo ngưỡng chi phí/độ trễ
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-04] AI Agent Trợ lý DevOps: Phân tích Log lỗi Build & CI/CD

### 📝 Mô tả đề tài
📍 Thực trạng: Các đội phát triển trong hệ sinh thái doanh nghiệp chạy nhiều pipeline CI/CD; khi build/deploy lỗi, kỹ sư mất nhiều thời gian đọc log để tìm nguyên nhân. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent theo dõi pipeline, tự đọc & phân tích log lỗi build/test/deploy, xác định nguyên nhân, gợi ý cách sửa và có thể trigger retry/rollback với phê duyệt; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL bắt buộc trước khi trigger deploy/rollback trên môi trường thật; phân quyền theo repo/team; độ chính xác chẩn đoán lỗi; audit log; cảnh báo pipeline hỏng liên tục; kiểm soát chi phí phân tích log lớn. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• tích hợp API CI/CD mô phỏng (GitHub Actions/GitLab CI/Jenkins mock)
• RAG trên tài liệu build & lỗi đã biết (vector DB)
• log parsing + chunking
• backend FastAPI
• frontend React (dashboard pipeline + chi tiết lỗi, vai kỹ sư/lead)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (dev / DevOps lead), agent phân tích log lỗi build + gợi ý fix từ RAG, HITL cho retry/rollback, audit log, dashboard trạng thái pipeline.

Nâng cao:
• Tự nhận diện lỗi lặp và đề xuất cải tiến pipeline, memory pattern lỗi theo repo, tự tạo ticket/PR gợi ý, thống kê tỷ lệ build fail & thời gian khắc phục
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-05] AI Agent Hỏi đáp & Thao tác SAP bằng Ngôn ngữ Tự nhiên

### 📝 Mô tả đề tài
📍 Thực trạng: Nhân viên nghiệp vụ (mua hàng, kho, kế toán) tại các đơn vị trong doanh nghiệp dùng SAP nhưng giao diện phức tạp, cần đào tạo nhiều; tra cứu dữ liệu SAP tốn thời gian. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent hiểu câu hỏi tiếng Việt, ánh xạ sang truy vấn/giao dịch SAP (tra cứu tồn kho, đơn hàng, tài liệu), trả kết quả có giải thích và thực hiện thao tác đơn giản qua API với phê duyệt; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL bắt buộc trước mọi giao dịch ghi/thay đổi trên SAP; phân quyền theo module & mã đơn vị (company code); độ chính xác ánh xạ truy vấn; audit log giao dịch; cảnh báo khi thao tác nhạy cảm; kiểm soát độ trễ. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• text-to-query/function-calling ánh xạ sang SAP OData/BAPI (mô phỏng SAP API layer)
• RAG trên tài liệu nghiệp vụ SAP (vector DB)
• backend FastAPI
• frontend Next.js (chat + bảng dữ liệu, vai người dùng nghiệp vụ / key user)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App online, đăng nhập ≥2 vai (nhân viên nghiệp vụ / key user SAP), agent trả lời truy vấn SAP mô phỏng (tồn kho, đơn hàng) bằng tiếng Việt, HITL cho thao tác ghi, audit log.

Nâng cao:
• Agent lập kế hoạch chuỗi giao dịch, giải thích nguồn dữ liệu, memory ngữ cảnh phiên, cảnh báo quyền hạn, gợi ý transaction code phù hợp
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-06] AI Agent Tự động hóa Quy trình Mua hàng SAP (Tạo PO & Duyệt)

### 📝 Mô tả đề tài
📍 Thực trạng: Quy trình tạo purchase requisition/purchase order trong SAP tại các đơn vị mua sắm gồm nhiều bước thủ công, dễ sai sót và chậm phê duyệt. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent hỗ trợ tạo PR/PO từ yêu cầu bằng ngôn ngữ tự nhiên, kiểm tra tồn kho & nhà cung cấp, điền dữ liệu, định tuyến duyệt theo hạn mức và theo dõi trạng thái; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL & workflow duyệt theo hạn mức bắt buộc trước khi tạo/gửi PO; phân quyền theo vai mua hàng/quản lý; độ chính xác dữ liệu PO; audit log; cảnh báo vượt ngân sách; kiểm soát chi phí & độ trễ. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph workflow
• tích hợp SAP MM API mô phỏng (tạo PR/PO, master data supplier)
• RAG trên chính sách mua sắm
• rule engine hạn mức duyệt
• backend FastAPI
• frontend React (form PO + luồng duyệt, vai người mua/quản lý duyệt)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (nhân viên mua hàng / quản lý duyệt), agent tạo bản nháp PO từ yêu cầu + kiểm tra tồn kho mô phỏng, HITL duyệt theo hạn mức, audit log.

Nâng cao:
• Agent tự chọn nhà cung cấp tối ưu theo tiêu chí, phát hiện bất thường giá, memory nhà cung cấp, cảnh báo ngân sách, dashboard theo dõi vòng đời PO
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-07] AI Agent Quản lý Tài sản CNTT (IT Asset Management Assistant)

### 📝 Mô tả đề tài
📍 Thực trạng: Tập đoàn quản lý lượng lớn thiết bị CNTT (laptop, máy chủ, thiết bị mạng) trên nhiều đơn vị; dữ liệu tài sản rời rạc, khó tra cứu vòng đời & bảo hành. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent quản lý CMDB, trả lời câu hỏi về tài sản, theo dõi cấp phát/thu hồi, cảnh báo hết bảo hành/khấu hao và hỗ trợ kiểm kê; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL trước khi thay đổi trạng thái tài sản (cấp phát/thu hồi/thanh lý); phân quyền theo đơn vị; độ chính xác dữ liệu CMDB; audit log; cảnh báo tài sản mất/quá hạn; kiểm soát chi phí. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• DB tài sản/CMDB (PostgreSQL)
• RAG trên chính sách tài sản (vector DB)
• tích hợp API ITAM mô phỏng
• backend FastAPI
• frontend Next.js (danh mục tài sản + dashboard vòng đời, vai nhân viên/quản trị tài sản)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (nhân viên yêu cầu / quản trị tài sản), agent tra cứu & báo cáo tài sản, HITL cho cấp phát/thu hồi, cảnh báo bảo hành, audit log.

Nâng cao:
• Agent dự báo nhu cầu thay thế thiết bị, tối ưu phân bổ, memory lịch sử tài sản, phát hiện tài sản không dùng, báo cáo kiểm kê tự động
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-08] AI Agent Tối ưu Chi phí Cloud (FinOps Hạ tầng)

### 📝 Mô tả đề tài
📍 Thực trạng: Chi phí đám mây của hệ sinh thái doanh nghiệp lớn và tăng nhanh; tài nguyên dư thừa, instance không dùng, thiếu tối ưu gây lãng phí. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent phân tích dữ liệu chi phí & sử dụng, phát hiện lãng phí (idle/oversized resource), đề xuất tối ưu (rightsizing, reserved, tắt tài nguyên) và mô phỏng tiết kiệm; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL bắt buộc trước khi thực thi hành động thay đổi tài nguyên production; phân quyền theo tài khoản/dự án cloud; độ chính xác ước tính tiết kiệm; audit log; cảnh báo vượt ngân sách; kiểm soát độ trễ phân tích dữ liệu lớn. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• dataset chi phí cloud mô phỏng (AWS/GCP billing mock)
• phân tích + đề xuất tối ưu
• RAG trên best practice FinOps
• tích hợp API cloud mô phỏng
• backend FastAPI
• frontend React (dashboard chi phí + đề xuất, vai kỹ sư/quản lý tài chính hạ tầng)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard online, đăng nhập ≥2 vai (kỹ sư hạ tầng / quản lý FinOps), agent phát hiện lãng phí + đề xuất tối ưu kèm ước tính tiết kiệm, HITL duyệt hành động, audit log.

Nâng cao:
• Agent lập kế hoạch tối ưu đa bước, dự báo chi phí, memory lịch sử tối ưu, cảnh báo ngân sách realtime, báo cáo tiết kiệm định kỳ
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-09] AI Agent Trợ lý SOC: Phát hiện & Phản ứng Sự cố Bảo mật

### 📝 Mô tả đề tài
📍 Thực trạng: Trung tâm giám sát an ninh (SOC) của tập đoàn nhận nhiều cảnh báo bảo mật (đăng nhập bất thường, malware, brute force); phân tích viên quá tải với cảnh báo nhiễu. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent phân loại & làm giàu ngữ cảnh cảnh báo (triage), tương quan sự kiện, đánh giá mức độ nghiêm trọng, đề xuất playbook phản ứng và hỗ trợ điều tra; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL bắt buộc trước mọi hành động containment (khóa tài khoản, cô lập máy) trên production; phân quyền chặt theo cấp bảo mật; độ chính xác & giảm false positive; audit log không thể sửa; cảnh báo sự cố nghiêm trọng; kiểm soát độ trễ phản ứng. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• dữ liệu log bảo mật/SIEM mô phỏng
• enrichment + tương quan sự kiện
• RAG trên playbook SOAR & threat intel (vector DB)
• tích hợp API SIEM/SOAR mô phỏng
• backend FastAPI
• frontend Next.js (bảng cảnh báo + timeline điều tra, vai phân tích viên/trưởng SOC)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark tự động hóa CNTT doanh nghiệp WorkArena (ITSM), SWE-bench, bộ dữ liệu log hệ thống phân tán Loghub (Kubernetes, Linux, HDFS) và chuẩn quan sát OpenTelemetry (Traces, Metrics, Logs).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (analyst / SOC lead), agent triage cảnh báo + xếp mức nghiêm trọng + gợi ý playbook, HITL cho containment, audit log.

Nâng cao:
• Tương quan đa nguồn dựng chuỗi tấn công, memory IOC, tự sinh báo cáo sự cố, cảnh báo leo thang, đo giảm tỷ lệ false positive
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-10] AI Agent Quản lý Cấp phát & Thu hồi Quyền Truy cập (IAM Governance)

### 📝 Mô tả đề tài
📍 Thực trạng: Việc cấp/thu hồi quyền truy cập ứng dụng trong tập đoàn phức tạp, thiếu rà soát định kỳ, dễ tồn tại quyền dư thừa (over-privilege) và rủi ro bảo mật. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent xử lý yêu cầu truy cập, kiểm tra chính sách & phân tách nhiệm vụ (SoD), đề xuất phê duyệt/thu hồi, và tự động rà soát quyền định kỳ (access review); đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL bắt buộc trước khi cấp/thu quyền; phân quyền & kiểm tra SoD nghiêm ngặt; độ chính xác đánh giá rủi ro; audit log đầy đủ; cảnh báo quyền dư/vi phạm SoD; kiểm soát chi phí. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• DB quyền & vai trò (RBAC model)
• rule engine SoD/policy
• RAG trên chính sách IAM
• tích hợp API IAM mô phỏng (SCIM)
• backend FastAPI
• frontend React (luồng yêu cầu + bảng rà soát quyền, vai người yêu cầu/quản trị IAM)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (nhân viên yêu cầu quyền / quản trị IAM), agent đánh giá yêu cầu theo policy + phát hiện vi phạm SoD, HITL duyệt, audit log.

Nâng cao:
• Agent chạy chiến dịch access review định kỳ, đề xuất thu hồi quyền dư, phân tích rủi ro theo vai, memory lịch sử quyền, báo cáo tuân thủ
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-11] AI Agent Trợ lý Knowledge Base IT (IT KB Copilot)

### 📝 Mô tả đề tài
📍 Thực trạng: Kho tri thức IT của tập đoàn (hướng dẫn, SOP, FAQ) rải rác trên nhiều nguồn, khó tìm, tài liệu lỗi thời; nhân viên hỏi lại help desk. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent hỏi-đáp trên toàn bộ knowledge base, trích nguồn, phát hiện tài liệu thiếu/mâu thuẫn/lỗi thời, và tự đề xuất/soạn thảo bài viết KB mới từ ticket đã giải quyết; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL bắt buộc trước khi xuất bản/sửa bài KB; phân quyền theo nhóm tài liệu; độ chính xác & bắt buộc trích dẫn nguồn (chống bịa); audit log thay đổi tài liệu; cảnh báo nội dung lỗi thời; kiểm soát chi phí. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• RAG nâng cao (hybrid search, reranking) trên vector DB (Qdrant/pgvector)
• tích hợp nguồn tài liệu (Confluence/SharePoint mock)
• phát hiện trùng lặp/mâu thuẫn
• backend FastAPI
• frontend Next.js (chat + trình soạn KB, vai người dùng/biên tập viên KB)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (người dùng tra cứu / biên tập KB), agent Q&A có trích nguồn, đề xuất bài KB từ ticket, HITL duyệt xuất bản, audit log.

Nâng cao:
• Agent phát hiện lỗ hổng kiến thức & mâu thuẫn, tự cập nhật tài liệu lỗi thời, memory truy vấn phổ biến, phân tích chủ đề hỏi nhiều, đánh giá chất lượng KB
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-12] AI Agent Tự động Phân tích & Xử lý Cảnh báo Giám sát (Alert Noise Reduction)

### 📝 Mô tả đề tài
📍 Thực trạng: Hệ thống giám sát tập đoàn phát ra lượng lớn cảnh báo, nhiều cảnh báo trùng/nhiễu (alert fatigue) khiến đội vận hành bỏ sót sự cố thật. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent gom nhóm & khử trùng cảnh báo, xác định cảnh báo thật đáng xử lý, gắn ngữ cảnh & mức ưu tiên, tự tạo incident và đề xuất hành động; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL trước khi tạo incident P1/thực thi khắc phục production; phân quyền theo hệ thống; độ chính xác gom nhóm & giảm nhiễu; audit log; cảnh báo sự cố nghiêm trọng bị chôn; kiểm soát độ trễ realtime. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• luồng cảnh báo mô phỏng (Alertmanager/Grafana mock)
• clustering/dedup + correlation
• RAG trên runbook (vector DB)
• tích hợp API incident (mock)
• backend FastAPI + streaming
• frontend React (bảng cảnh báo gom nhóm, vai vận hành/lead)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark tự động hóa CNTT doanh nghiệp WorkArena (ITSM), SWE-bench, bộ dữ liệu log hệ thống phân tán Loghub (Kubernetes, Linux, HDFS) và chuẩn quan sát OpenTelemetry (Traces, Metrics, Logs).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard online realtime, đăng nhập ≥2 vai (vận hành / lead), agent gom nhóm & khử nhiễu cảnh báo + xếp ưu tiên, HITL tạo incident, audit log.

Nâng cao:
• Agent tương quan cảnh báo thành sự cố, học ngưỡng theo phản hồi, memory pattern nhiễu, đề xuất tinh chỉnh rule cảnh báo, đo mức giảm alert fatigue
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-13] AI Agent Quản lý Thay đổi Hạ tầng (Change Management Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Các yêu cầu thay đổi hệ thống (RFC) trong tập đoàn cần đánh giá rủi ro, kiểm tra xung đột lịch, phê duyệt CAB; quy trình thủ công chậm và dễ bỏ sót rủi ro. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tiếp nhận RFC, tự đánh giá rủi ro & tác động, phát hiện xung đột với thay đổi khác, đề xuất cửa sổ triển khai và soạn kế hoạch rollback, định tuyến phê duyệt CAB; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL & phê duyệt CAB bắt buộc trước khi thay đổi production; phân quyền theo hệ thống & cấp thay đổi; độ chính xác đánh giá rủi ro; audit log; cảnh báo xung đột lịch/high-risk; kiểm soát chi phí. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• DB thay đổi & lịch triển khai
• RAG trên chính sách change & lịch sử sự cố
• rule engine đánh giá rủi ro
• tích hợp API ITSM change mô phỏng
• backend FastAPI
• frontend Next.js (form RFC + lịch & bảng duyệt CAB, vai người đề xuất/quản lý thay đổi)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark tự động hóa CNTT doanh nghiệp WorkArena (ITSM), SWE-bench, bộ dữ liệu log hệ thống phân tán Loghub (Kubernetes, Linux, HDFS) và chuẩn quan sát OpenTelemetry (Traces, Metrics, Logs).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (người đề xuất / quản lý CAB), agent đánh giá rủi ro RFC + phát hiện xung đột lịch + đề xuất rollback, HITL duyệt, audit log.

Nâng cao:
• Agent học từ thay đổi thất bại để tinh chỉnh rủi ro, tối ưu lịch triển khai, memory thay đổi liên quan, cảnh báo freeze period, báo cáo tỷ lệ thay đổi thành công
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-14] AI Agent Hỗ trợ Migration & Nâng cấp Hệ thống

### 📝 Mô tả đề tài
📍 Thực trạng: Việc migration/nâng cấp hệ thống (server, database, ứng dụng) giữa các đơn vị trong doanh nghiệp phức tạp, nhiều phụ thuộc, dễ sót bước và gây downtime. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent lập kế hoạch migration theo checklist, phân tích phụ thuộc & rủi ro, sinh runbook từng bước, theo dõi tiến độ và hỗ trợ xử lý khi bước lỗi; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL bắt buộc tại các bước cutover/thay đổi production; phân quyền theo dự án; độ chính xác kế hoạch & phụ thuộc; audit log từng bước; cảnh báo bước rủi ro cao/quá downtime; kiểm soát chi phí & độ trễ. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph planner
• RAG trên tài liệu migration & best practice (vector DB)
• dependency graph
• tích hợp API hệ thống mô phỏng
• backend FastAPI
• frontend React (kế hoạch + checklist tiến độ, vai kỹ sư/quản lý dự án)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark tự động hóa CNTT doanh nghiệp WorkArena (ITSM), SWE-bench, bộ dữ liệu log hệ thống phân tán Loghub (Kubernetes, Linux, HDFS) và chuẩn quan sát OpenTelemetry (Traces, Metrics, Logs).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (kỹ sư migration / PM), agent sinh kế hoạch & runbook từng bước + phân tích phụ thuộc, HITL tại cutover, theo dõi tiến độ, audit log.

Nâng cao:
• Agent lập lịch tối ưu giảm downtime, đề xuất rollback từng bước, memory bài học migration trước, cảnh báo rủi ro, báo cáo tiến độ & sự cố
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-15] AI Agent Trợ lý Báo cáo SAP/BI bằng Ngôn ngữ Tự nhiên

### 📝 Mô tả đề tài
📍 Thực trạng: Lãnh đạo & nhân viên nghiệp vụ cần báo cáo từ dữ liệu SAP/BI (doanh thu, tồn kho, chi phí) nhưng phụ thuộc đội BI, thời gian chờ lâu. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent hiểu yêu cầu báo cáo tiếng Việt, ánh xạ sang truy vấn dữ liệu, sinh bảng/biểu đồ, tóm tắt insight và cho phép đào sâu (drill-down) hội thoại; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL/kiểm chứng khi truy vấn nhạy cảm hoặc số liệu tài chính công bố; phân quyền dữ liệu theo vai & đơn vị (row-level security); độ chính xác truy vấn & chống bịa số; audit log truy vấn; cảnh báo số liệu bất thường; kiểm soát độ trễ. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• text-to-SQL/text-to-query trên data mart mô phỏng SAP BW/BI
• semantic layer
• sinh chart (Recharts/Plotly)
• RAG trên định nghĩa chỉ số (vector DB)
• backend FastAPI
• frontend Next.js (chat + dashboard báo cáo, vai nhân viên nghiệp vụ/lãnh đạo)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (nhân viên nghiệp vụ / lãnh đạo), agent trả lời yêu cầu báo cáo bằng bảng + biểu đồ + tóm tắt insight, phân quyền dữ liệu, audit log.

Nâng cao:
• Agent drill-down hội thoại, phát hiện xu hướng/bất thường, tự tạo báo cáo định kỳ, memory ngữ cảnh phân tích, cảnh báo ngưỡng KPI
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-16] AI Agent Phân tích Ticket Tồn đọng & Đề xuất Cải tiến (ITSM Analytics)

### 📝 Mô tả đề tài
📍 Thực trạng: Help desk tích lũy lượng lớn ticket lịch sử; ticket tồn đọng và vấn đề lặp lại không được phân tích để cải tiến (problem management). Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent phân tích kho ticket, phát hiện nhóm vấn đề lặp lại & nguyên nhân gốc, xác định điểm nghẽn quy trình, và đề xuất hành động cải tiến/automation; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL trước khi tạo problem record hoặc thay đổi quy trình; phân quyền dữ liệu ticket theo đơn vị & bảo mật thông tin cá nhân (PII masking); độ chính xác phân cụm & phân tích; audit log; cảnh báo vấn đề nghiêm trọng lặp lại; kiểm soát chi phí xử lý dữ liệu lớn. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• dataset ticket lịch sử
• clustering/topic modeling + embedding (vector DB)
• RAG
• PII masking
• tích hợp API ITSM mô phỏng
• backend FastAPI
• frontend React (dashboard phân tích + đề xuất, vai analyst/quản lý dịch vụ)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark tự động hóa CNTT doanh nghiệp WorkArena (ITSM), SWE-bench, bộ dữ liệu log hệ thống phân tán Loghub (Kubernetes, Linux, HDFS) và chuẩn quan sát OpenTelemetry (Traces, Metrics, Logs).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard online, đăng nhập ≥2 vai (analyst / quản lý dịch vụ IT), agent phân cụm vấn đề lặp + phân tích tồn đọng + đề xuất cải tiến, HITL tạo problem, audit log.

Nâng cao:
• Agent xếp ưu tiên cải tiến theo tác động, đề xuất automation candidate, memory xu hướng theo thời gian, dự báo khối lượng ticket, báo cáo điều hành
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-17] AI Agent Runbook Tự động Xử lý Sự cố Thường gặp (Auto-Remediation)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhiều sự cố hạ tầng lặp lại (service treo, disk đầy, cần restart, xoay log) được xử lý thủ công theo runbook, tốn thời gian đội trực. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent nhận sự cố, chọn đúng runbook, lập kế hoạch các bước khắc phục, thực thi hành động an toàn (có sandbox/dry-run) và xác minh kết quả, leo thang nếu thất bại; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL bắt buộc trước khi thực thi hành động thay đổi production; phân quyền theo hệ thống; độ chính xác chọn runbook & xác minh sau khắc phục; audit log từng lệnh; cảnh báo khi khắc phục thất bại/lặp; kiểm soát blast radius & độ trễ. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph agent với tool thực thi (mô phỏng SSH/API hạ tầng, dry-run mode)
• RAG trên runbook (vector DB)
• verification checks
• tích hợp API incident mô phỏng
• backend FastAPI
• frontend Next.js (bảng sự cố + nhật ký thực thi từng bước, vai kỹ sư trực/lead)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark tự động hóa CNTT doanh nghiệp WorkArena (ITSM), SWE-bench, bộ dữ liệu log hệ thống phân tán Loghub (Kubernetes, Linux, HDFS) và chuẩn quan sát OpenTelemetry (Traces, Metrics, Logs).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (kỹ sư trực / lead), agent chọn runbook + lập kế hoạch + thực thi mô phỏng có xác minh, HITL trước hành động, audit log từng bước.

Nâng cao:
• Agent tự học runbook mới từ sự cố đã giải, đánh giá blast radius, memory sự cố lặp, tự động rollback khi thất bại, đo tỷ lệ auto-remediation thành công
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-18] AI Agent Quản lý License & Tối ưu Chi phí Phần mềm (SAM)

### 📝 Mô tả đề tài
📍 Thực trạng: Tập đoàn mua nhiều license phần mềm (SAP, Microsoft, công cụ SaaS) cho nhiều đơn vị; nhiều license không dùng hoặc dùng sai, rủi ro tuân thủ và lãng phí chi phí. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent theo dõi license đã mua vs. thực dùng, phát hiện license nhàn rỗi/quá hạn/vi phạm, đề xuất thu hồi-tái phân bổ-gia hạn và cảnh báo tuân thủ; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL trước khi thu hồi/tái phân bổ/mua license; phân quyền theo đơn vị & nhà cung cấp; độ chính xác đối soát sử dụng; audit log; cảnh báo vi phạm tuân thủ & hết hạn; kiểm soát chi phí. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• DB license & dữ liệu sử dụng mô phỏng
• đối soát entitlement vs usage
• RAG trên điều khoản license
• tích hợp API SAM mô phỏng
• backend FastAPI
• frontend React (dashboard license + đề xuất, vai IT admin/quản lý mua sắm)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (IT admin / quản lý mua sắm), agent phát hiện license nhàn rỗi & sắp hết hạn + đề xuất tối ưu, HITL cho thu hồi/gia hạn, cảnh báo tuân thủ, audit log.

Nâng cao:
• Agent dự báo nhu cầu license, tối ưu tái phân bổ giảm chi phí, memory lịch sử sử dụng, phân tích vi phạm tuân thủ, báo cáo tiết kiệm
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-19] AI Agent Onboarding/Offboarding Nhân sự IT (Access Provisioning)

### 📝 Mô tả đề tài
📍 Thực trạng: Khi nhân sự vào/rời/chuyển bộ phận tại các đơn vị trong doanh nghiệp, việc cấp/thu tài khoản, quyền, thiết bị và license cần phối hợp nhiều hệ thống; làm thủ công dễ sót, gây rủi ro bảo mật (tài khoản ma). Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent điều phối quy trình onboarding/offboarding theo vai trò: xác định gói quyền & tài sản chuẩn theo chức danh, tạo/thu tài khoản qua nhiều hệ thống, theo dõi hoàn tất và tạo checklist; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL bắt buộc trước khi tạo/thu quyền & tài khoản; phân quyền theo HR & IT; độ chính xác gói quyền theo vai; audit log; cảnh báo tài khoản chưa thu hồi sau offboarding (bảo mật); kiểm soát độ trễ SLA onboarding. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph orchestrator đa hệ thống
• RAG trên chính sách quyền theo chức danh
• tích hợp API HR/IAM/ITAM mô phỏng (SCIM)
• rule engine role-based access template
• backend FastAPI
• frontend Next.js (quy trình + checklist trạng thái, vai HR/IT admin)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn giao thức nghiệp vụ ERP OData / BAPI schemas (PR, PO, GR, Invoice), ma trận kiểm toán phân quyền IAM / Segregation of Duties (SoD) và chuẩn quản trị chi phí đám mây FOCUS FinOps.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web online, đăng nhập ≥2 vai (HR/quản lý / IT admin), agent tạo checklist & điều phối cấp/thu quyền theo chức danh, HITL duyệt hành động, cảnh báo tài khoản tồn dư, audit log.

Nâng cao:
• Agent tự phát hiện quyền lệch chuẩn (drift) so với vai, xử lý chuyển bộ phận, memory template quyền, đo SLA onboarding, báo cáo tuân thủ offboarding
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---

## [ITOPS-20] AI Agent Trợ lý Vận hành SLA & Sức khỏe Dịch vụ IT (Service Health Copilot)

### 📝 Mô tả đề tài
📍 Thực trạng: Đội vận hành dịch vụ IT của tập đoàn phải theo dõi nhiều SLA/OLA, tình trạng dịch vụ và ticket đang mở trên nhiều đơn vị; khó có bức tranh tổng thể và cảnh báo sớm vi phạm SLA. Trong hạ tầng CNTT và hệ thống ERP của doanh nghiệp lớn, một sự cố hoặc yêu cầu thay đổi thường liên đới tới nhiều dịch vụ phụ thuộc, tạo ra hàng nghìn cảnh báo trùng lặp (alert storm) hoặc tiềm ẩn xung đột quyền hạn bảo mật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tổng hợp trạng thái dịch vụ & ticket, dự báo nguy cơ vi phạm SLA, giải thích nguyên nhân, ưu tiên hành động và trả lời hỏi đáp vận hành bằng ngôn ngữ tự nhiên; đồng thời tương quan sự kiện đa nguồn trên đồ thị phụ thuộc hệ thống (service topology) để khoanh vùng nguyên nhân gốc rễ, kiểm tra ràng buộc phân quyền/bất kiêm nhiệm xác định và thực thi tự động hóa có chế độ chạy thử (dry-run) kèm ước lượng bán kính ảnh hưởng.

🔒 Ràng buộc: HITL trước khi tái phân bổ nguồn lực/leo thang tự động ảnh hưởng vận hành; phân quyền theo dịch vụ & đơn vị; độ chính xác dự báo SLA; audit log; cảnh báo nguy cơ vi phạm SLA; kiểm soát độ trễ realtime & chi phí. Phân tách rõ lệnh chẩn đoán chỉ đọc (read-only) với lệnh thay đổi trạng thái hệ thống (state-mutating, bắt buộc qua HITL và có kế hoạch rollback); kiểm tra ràng buộc phân quyền/nghiệp vụ bằng quy tắc xác định.

### 🛠️ Tech Stack
• LLM + LangGraph
• tổng hợp dữ liệu ticket + metric dịch vụ mô phỏng
• dự báo SLA (heuristic/ML nhẹ)
• RAG trên định nghĩa SLA & runbook
• tích hợp API ITSM/monitoring mô phỏng
• backend FastAPI + streaming
• frontend Next.js (dashboard sức khỏe dịch vụ + chat vận hành, vai vận hành/quản lý dịch vụ)
• Langfuse
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark tự động hóa CNTT doanh nghiệp WorkArena (ITSM), SWE-bench, bộ dữ liệu log hệ thống phân tán Loghub (Kubernetes, Linux, HDFS) và chuẩn quan sát OpenTelemetry (Traces, Metrics, Logs).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard online, đăng nhập ≥2 vai (vận hành / quản lý dịch vụ), agent tổng hợp sức khỏe dịch vụ + cảnh báo nguy cơ vi phạm SLA + hỏi đáp vận hành, HITL cho leo thang, audit log.

Nâng cao:
• Agent dự báo vi phạm SLA sớm & đề xuất ưu tiên, phân tích nguyên nhân, memory xu hướng dịch vụ, tự sinh báo cáo vận hành định kỳ, cảnh báo ngưỡng KPI
• Kết hợp phân tích đồ thị phụ thuộc hạ tầng / kiểm tra ma trận phân quyền xác định với chế độ mô phỏng tác động trước khi thực thi (dry-run & blast-radius preview) và tự động hóa kiểm thử hồi quy.

---
