# Lĩnh vực: VSOC - An ninh mạng – Trung tâm Giám sát An toàn thông tin (SOC)

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `VSOC-01` | [SentinelTriage - AI Agent phân loại & khử trùng lặp kết quả SAST/DAST](#vsoc-01) |
| `VSOC-02` | [ReconMapper - AI Agent lập bản đồ bề mặt tấn công (Attack Surface Map)](#vsoc-02) |
| `VSOC-03` | [FuzzMind - AI Agent fuzzing API có định hướng LLM](#vsoc-03) |
| `VSOC-04` | [PentestSyndicate - Hệ đa agent mô phỏng đội pentest tự động](#vsoc-04) |
| `VSOC-05` | [AgentGuardIAM - AI Agent quản trị định danh & quyền tối thiểu cho AI agent (MCP/A2A)](#vsoc-05) |
| `VSOC-06` | [ThreatIntelRAG - AI Agent tri thức tình báo mối đe dọa chính xác cao](#vsoc-06) |
| `VSOC-07` | [AlertSense - AI Agent phân loại cảnh báo SOC & giảm false positive](#vsoc-07) |
| `VSOC-08` | [PhishHunter - AI Agent phân tích email lừa đảo & báo cáo người dùng](#vsoc-08) |
| `VSOC-09` | [AutoSOAR - AI Agent điều phối ứng phó sự cố & tự khắc phục có kiểm soát](#vsoc-09) |
| `VSOC-10` | [HuntHypothesis - AI Agent săn mối đe dọa theo giả thuyết](#vsoc-10) |
| `VSOC-11` | [RootCauseAI - AI Agent tương quan log/SIEM & truy nguyên nguyên nhân gốc](#vsoc-11) |
| `VSOC-12` | [RuleForge - AI Agent sinh & kiểm thử luật phát hiện Sigma/YARA](#vsoc-12) |
| `VSOC-13` | [MalwareBriefer - AI Agent tóm tắt & phân tích báo cáo sandbox mã độc](#vsoc-13) |
| `VSOC-14` | [TimelineDFIR - AI Agent dựng lại dòng thời gian điều tra số (DFIR)](#vsoc-14) |
| `VSOC-15` | [RiskRank - AI Agent xếp hạng ưu tiên lỗ hổng theo rủi ro & khả năng khai thác](#vsoc-15) |
| `VSOC-16` | [CloudPosture - AI Agent đánh giá cấu hình an ninh cloud (CSPM) & quét IaC](#vsoc-16) |
| `VSOC-17` | [PromptShield - AI Agent guardrails chống indirect prompt injection cho hệ AI-SOC](#vsoc-17) |
| `VSOC-18` | [PIIRedactor - AI Agent che dữ liệu nhạy cảm/PII thời gian thực cho agent SOC](#vsoc-18) |
| `VSOC-19` | [RedTeamAI - AI Agent red-team tự động kiểm thử đối kháng chính hệ AI-SOC](#vsoc-19) |
| `VSOC-20` | [ComplianceAuditor - AI Agent kiểm toán tuân thủ & đối chiếu chuẩn an ninh](#vsoc-20) |

---

## [VSOC-01] SentinelTriage - AI Agent phân loại & khử trùng lặp kết quả SAST/DAST

### 📝 Mô tả đề tài
📍 Thực trạng: Mỗi lần chạy pipeline CI/CD, các công cụ SAST (Semgrep) và DAST (OWASP ZAP) đẩy ra hàng nghìn dòng cảnh báo JSON/XML vào data lake của Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp; đội bảo mật ngập trong trùng lặp và false positive, xử lý thủ công mất nhiều ngày.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tự động đọc log SAST/DAST khổng lồ, gom nhóm & khử trùng lặp các phát hiện tương đương, đối chiếu RAG (CVE/OWASP) để xác thực, chấm điểm ưu tiên theo mức độ nghiêm trọng và ngữ cảnh ứng dụng, rồi sinh phiếu triage kèm bằng chứng và gợi ý khắc phục; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Chỉ đọc dữ liệu quét trên môi trường staging/mô phỏng, không tự sửa code hay đóng ticket khi chưa có HITL duyệt; agent chạy least-privilege (chỉ đọc data lake, không quyền ghi repo); mọi kết luận phải grounded trên bằng chứng dòng log + CVE cụ thể (chống bịa); phải giảm rõ rệt false positive so với baseline và kiểm soát độ trễ/chi phí token khi xử lý log lớn; làm sạch dữ liệu đầu vào chống prompt injection ẩn trong nội dung file/stack trace.

### 🛠️ Tech Stack
• LLM (GPT-4o/Claude)
• LangGraph điều phối
• RAG với Qdrant + BGE reranker nạp CVE/OWASP
• parser Semgrep + OWASP ZAP JSON/XML
• NeMo Guardrails lọc input
• FastAPI backend
• Next.js + React frontend (dashboard triage)
• Postgres lưu phiếu
• Langfuse observability
• RAGAS + LLM-as-Judge eval
• Docker deploy.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark an ninh ứng dụng SastBench / OWASP Benchmark / Juliet Test Suite, danh mục lỗ hổng bị khai thác thực tế CISA KEV + NVD CVE/EPSS và mẫu hạ tầng lỗi CloudGoat / TerraGoat.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app đã deploy có đăng nhập, ≥2 vai trò (Analyst xem/duyệt, Manager cấu hình)
• upload/kết nối log SAST/DAST, agent gom nhóm-khử trùng lặp-chấm ưu tiên, hiển thị bằng chứng, HITL để Analyst xác nhận/bác bỏ trước khi đóng phiếu, có xử lý lỗi khi file hỏng/thiếu.

Nâng cao:
• Multi-agent (Parser Agent + Correlation Agent + Prioritization Agent) phối hợp qua LangGraph
• eval pipeline đo tỉ lệ khử trùng lặp đúng và giảm false positive (LLM-as-Judge + RAGAS cho phần RAG)
• trace toàn bộ reasoning trên Langfuse
• guardrails chống prompt injection
• tối ưu token bằng batching/summarization và báo cáo chi phí/độ trễ
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-02] ReconMapper - AI Agent lập bản đồ bề mặt tấn công (Attack Surface Map)

### 📝 Mô tả đề tài
📍 Thực trạng: Trước mỗi đợt pentest staging, đội Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp phải thu thập thủ công thông tin về endpoint, cổng, dịch vụ, công nghệ, phiên bản của ứng dụng mục tiêu rồi tự đối chiếu lỗ hổng đã biết — tốn công và dễ bỏ sót.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent Recon tự động thu thập dữ liệu trinh sát (đọc output scan, cấu hình, log DAST), tổng hợp thành 'Attack Surface Map' có cấu trúc (asset → dịch vụ → công nghệ → CVE liên quan), đối chiếu Threat Intelligence RAG để gắn cờ điểm yếu tiềm năng và đề xuất vector tấn công ưu tiên.

🎯; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Chỉ trinh sát trên phạm vi staging được cấp phép, tuyệt đối không quét hệ thống thật/ngoài scope; agent least-privilege qua API Gateway; không thực hiện hành động khai thác, chỉ lập bản đồ; mọi liên kết CVE phải grounded, chống bịa; kiểm soát false positive khi gán lỗ hổng; bảo vệ dữ liệu nhạy cảm phát hiện được và làm sạch input chống prompt injection; kiểm soát chi phí/độ trễ.

### 🛠️ Tech Stack
• LLM
• LangGraph
• RAG hybrid search Qdrant + GraphRAG (Neo4j) nạp CVE/OWASP/MITRE
• Custom Tools bọc Nmap/httpx/DAST parser qua MCP
• Kong API Gateway kiểm soát scope
• FastAPI
• React/Next.js hiển thị graph attack surface (D3/Cytoscape)
• Langfuse trace
• DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark an ninh ứng dụng SastBench / OWASP Benchmark / Juliet Test Suite, danh mục lỗ hổng bị khai thác thực tế CISA KEV + NVD CVE/EPSS và mẫu hạ tầng lỗi CloudGoat / TerraGoat.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy có đăng nhập, ≥2 vai trò (Recon Analyst, Lead)
• nhập phạm vi staging, agent thu thập & sinh Attack Surface Map trực quan kèm CVE gợi ý, có HITL xác nhận scope trước khi chạy tool, xử lý lỗi khi target không phản hồi.

Nâng cao:
• Multi-agent (Collector + Enrichment + Mapping) với GraphRAG đo retrieval accuracy
• eval đo độ chính xác gán CVE (RAGAS/LLM-as-Judge)
• trace communication trên Langfuse
• guardrails + least-privilege qua Gateway
• tối ưu token & báo cáo chi phí/độ trễ
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-03] FuzzMind - AI Agent fuzzing API có định hướng LLM

### 📝 Mô tả đề tài
📍 Thực trạng: Fuzzing API truyền thống sinh payload ngẫu nhiên, tốn nhiều request mà ít trúng lỗ hổng, và con người phải đọc thủ công hàng loạt HTTP response để phát hiện bất thường. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent fuzzing thông minh: gửi request dị dạng tới API ứng dụng staging qua Gateway, phân tích HTTP response (mã 500, stack trace, thời gian phản hồi, thông điệp lỗi) để suy luận điểm yếu, rồi tự mutate payload theo hướng có khả năng khai thác cao (SQLi, path traversal, IDOR...) — biến fuzzing mù thành fuzzing có định hướng; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Chỉ fuzz trên staging/mô phỏng được phép, không đụng hệ thống production; agent least-privilege, không gửi payload state-changing gây hỏng dữ liệu nếu chưa qua HITL; grounded trên response thật khi kết luận có lỗ hổng (chống bịa); giới hạn tần suất request tránh DoS ngoài ý muốn; làm sạch response chống indirect prompt injection (app có thể trả nội dung hijack LLM); kiểm soát chi phí token & độ trễ.

### 🛠️ Tech Stack
• LLM
• LangGraph
• Custom Python fuzzing tools + API wrapper qua MCP
• Tyk/Kong Gateway rate-limit
• NeMo Guardrails làm sạch response
• FastAPI
• React/Next.js dashboard theo dõi payload/kết quả
• Postgres lưu case
• Langfuse trace
• DeepEval eval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark an ninh ứng dụng SastBench / OWASP Benchmark / Juliet Test Suite, danh mục lỗ hổng bị khai thác thực tế CISA KEV + NVD CVE/EPSS và mẫu hạ tầng lỗi CloudGoat / TerraGoat.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Tester, Reviewer)
• cấu hình target API staging, agent fuzz-phân tích-mutate và liệt kê phát hiện kèm bằng chứng response, HITL duyệt trước khi thử payload rủi ro, xử lý lỗi timeout/rate-limit.

Nâng cao:
• Multi-agent (Payload Generator + Response Analyzer + Mutator)
• eval đo hit-rate lỗ hổng thật & false positive (LLM-as-Judge)
• trace chiến lược mutate trên Langfuse
• guardrails chống prompt injection từ response
• tối ưu số request/chi phí và báo cáo độ trễ
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-04] PentestSyndicate - Hệ đa agent mô phỏng đội pentest tự động

### 📝 Mô tả đề tài
📍 Thực trạng: Một đợt pentest thủ công cần nhiều chuyên gia phối hợp (trinh sát, dò lỗ hổng, khai thác) kéo dài nhiều ngày và khó nhân rộng cho toàn bộ ứng dụng của doanh nghiệp. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng 'Pentest Syndicate' đa agent: một Supervisor điều phối chiến lược, giao việc cho Recon Agent, Fuzzing Agent và Exploit Agent để thực hiện chuỗi breach mô phỏng an toàn trên staging, tổng hợp thành báo cáo pentest có đường tấn công (kill chain) và mức độ ảnh hưởng; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Toàn bộ chỉ chạy trên môi trường staging/mô phỏng an toàn, tuyệt đối không tấn công hệ thống thật; Exploit Agent KHÔNG được chạy payload state-changing (SQLi/Command Injection) nếu chưa có HITL duyệt qua Slack/Teams (hiện payload + lý do → Approve/Reject); mỗi agent least-privilege theo vai trò qua Agent IAM; kết luận grounded trên bằng chứng; bảo vệ PII nếu dump được; chống prompt injection từ app mục tiêu; kiểm soát chi phí/độ trễ toàn hệ.

### 🛠️ Tech Stack
• LLM
• LangGraph/CrewAI multi-agent (Supervisor + Recon + Fuzzing + Exploit)
• RAG Threat Intel Qdrant + GraphRAG
• MCP/A2A + Kong Gateway cho Agent IAM có scope
• NeMo Guardrails
• Slack/Teams bot cho HITL
• FastAPI
• Next.js dashboard kill chain
• LangSmith/Langfuse trace
• RAGAS/DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark an ninh ứng dụng SastBench / OWASP Benchmark / Juliet Test Suite, danh mục lỗ hổng bị khai thác thực tế CISA KEV + NVD CVE/EPSS và mẫu hạ tầng lỗi CloudGoat / TerraGoat.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Operator, Approver)
• khởi động đợt pentest staging, xem tiến trình các agent và HITL approval gate cho hành động khai thác rủi ro, báo cáo kết quả + xử lý lỗi khi agent thất bại.

Nâng cao:
• Điều phối đa agent đầy đủ với xử lý conflict giữa agent
• observability trace reasoning & communication (LangSmith)
• eval đo tỉ lệ phát hiện đúng đường tấn công & false positive
• least-privilege qua Agent IAM (agent chỉ query endpoint được cấp scope)
• tối ưu chi phí/độ trễ và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-05] AgentGuardIAM - AI Agent quản trị định danh & quyền tối thiểu cho AI agent (MCP/A2A)

### 📝 Mô tả đề tài
📍 Thực trạng: Khi Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp triển khai nhiều AI agent gọi API nội bộ qua MCP/A2A, việc cấp quyền thường quá rộng khiến một agent bị chiếm quyền có thể truy cập cả endpoint quản trị nhạy cảm. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent quản trị IAM cho các agent khác: phân tích hành vi và nhu cầu truy cập thực tế của từng agent, đề xuất chính sách least-privilege có scope (ví dụ được query /api/users nhưng KHÔNG /api/admin), phát hiện quyền dư thừa và truy cập bất thường, sinh cấu hình policy cho API Gateway; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Mọi thay đổi policy phải qua HITL duyệt trước khi áp dụng (không tự khóa/mở quyền), đặc biệt với hành động thu hồi quyền; agent quản trị cũng chạy least-privilege, chỉ đọc log và đề xuất; grounded trên bằng chứng truy cập thật (chống bịa); chỉ chạy trên môi trường staging/mô phỏng; bảo vệ dữ liệu định danh nhạy cảm, chống prompt injection; giảm false positive khi gắn cờ quyền dư; kiểm soát độ trễ/chi phí.

### 🛠️ Tech Stack
• LLM
• LangGraph
• MCP/A2A + Kong/Tyk Gateway (policy engine)
• RAG chuẩn least-privilege/OWASP API Top 10 trên pgvector
• Presidio bảo vệ PII trong log
• FastAPI
• React/Next.js dashboard policy & recommendation
• Langfuse trace
• DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Security Admin, Auditor)
• hiển thị các agent và quyền hiện tại, agent đề xuất policy least-privilege, HITL duyệt trước khi sinh cấu hình Gateway, xử lý lỗi cấu hình.

Nâng cao:
• Multi-agent (Behavior Analyzer + Policy Recommender + Anomaly Detector)
• eval đo độ chính xác đề xuất & false positive
• mô phỏng agent thử truy cập vượt scope và Gateway chặn
• trace + guardrails
• tối ưu chi phí/độ trễ và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-06] ThreatIntelRAG - AI Agent tri thức tình báo mối đe dọa chính xác cao

### 📝 Mô tả đề tài
📍 Thực trạng: Analyst của Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp phải tra cứu thủ công qua nhiều nguồn rời rạc (CVE, OWASP, MITRE ATT&CK, báo cáo pentest cũ) để hiểu một mối đe dọa, dễ bỏ sót liên hệ và mất thời gian. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent Threat Intelligence dựa trên RAG chính xác cao (Hybrid Search + GraphRAG) nạp CVE/OWASP/MITRE ATT&CK và báo cáo pentest nội bộ, trả lời truy vấn của analyst kèm trích dẫn nguồn, liên kết kỹ thuật ATT&CK ↔ CVE ↔ biện pháp giảm thiểu, và tự tổng hợp brief mối đe dọa; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Mọi câu trả lời phải grounded trên tài liệu có trích dẫn, tuyệt đối chống bịa (nếu không đủ bằng chứng phải nói không biết); đo retrieval accuracy và giảm thông tin sai; bảo vệ dữ liệu pentest nội bộ nhạy cảm với phân quyền; chống prompt injection ẩn trong tài liệu nạp vào; least-privilege khi truy cập kho tri thức; kiểm soát độ trễ/chi phí truy vấn.

### 🛠️ Tech Stack
• LLM
• RAG Hybrid Search (BM25 + dense) Qdrant + reranker (Cohere/BGE) + GraphRAG Neo4j
• LangGraph
• nguồn CVE/NVD, OWASP, MITRE ATT&CK
• FastAPI
• React/Next.js chat + graph viewer
• NeMo Guardrails
• Langfuse
• RAGAS eval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark an ninh ứng dụng SastBench / OWASP Benchmark / Juliet Test Suite, danh mục lỗ hổng bị khai thác thực tế CISA KEV + NVD CVE/EPSS và mẫu hạ tầng lỗi CloudGoat / TerraGoat.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Analyst, Admin quản trị nguồn)
• truy vấn threat intel có trích dẫn nguồn, HITL để Admin duyệt tài liệu nạp vào KB, xử lý lỗi khi thiếu dữ liệu.

Nâng cao:
• GraphRAG liên kết ATT&CK-CVE-mitigation
• eval retrieval accuracy & faithfulness bằng RAGAS
• trace truy vấn
• guardrails chống prompt injection trong tài liệu
• tối ưu chi phí/độ trễ (cache, re-ranking) và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-07] AlertSense - AI Agent phân loại cảnh báo SOC & giảm false positive

### 📝 Mô tả đề tài
📍 Thực trạng: SOC của doanh nghiệp nhận hàng chục nghìn cảnh báo mỗi ngày từ SIEM/EDR, phần lớn là false positive, khiến analyst mệt mỏi cảnh báo và bỏ sót đe dọa thật. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent triage cảnh báo: làm giàu ngữ cảnh (đối chiếu threat intel, tài sản, lịch sử), suy luận mức độ nghiêm trọng và độ tin cậy, gom nhóm cảnh báo liên quan thành một sự cố, đề xuất phân loại (true/false positive) kèm lý do và hành động tiếp theo; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Agent chỉ đề xuất, không tự đóng cảnh báo mức cao hay chặn IP khi chưa có HITL duyệt (nhất là hành động khóa tài khoản/chặn); chạy trên dữ liệu log mô phỏng/staging; grounded trên bằng chứng log + threat intel (chống bịa); phải đo và giảm rõ rệt false positive mà không tăng false negative; bảo vệ PII trong log; least-privilege truy cập SIEM; chống prompt injection từ nội dung log; kiểm soát độ trễ để kịp thời gian thực & chi phí.

### 🛠️ Tech Stack
• LLM
• LangGraph
• SIEM Elastic/Wazuh
• RAG threat intel Qdrant
• Presidio redact PII
• FastAPI
• React/Next.js dashboard alert queue
• NeMo Guardrails
• Langfuse
• DeepEval/LLM-as-Judge
• vLLM cho throughput
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Tier-1 Analyst, Tier-2/Lead)
• hàng đợi cảnh báo với phân loại & lý do của agent, HITL duyệt cảnh báo mức cao trước khi hành động, xử lý lỗi khi thiếu ngữ cảnh.

Nâng cao:
• Multi-agent (Enrichment + Correlation + Classifier)
• eval đo tỉ lệ giảm false positive & độ chính xác (confusion matrix, LLM-as-Judge)
• trace
• guardrails + PII redaction
• triển khai vLLM tối ưu throughput/độ trễ và báo cáo chi phí
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-08] PhishHunter - AI Agent phân tích email lừa đảo & báo cáo người dùng

### 📝 Mô tả đề tài
📍 Thực trạng: Nhân viên doanh nghiệp báo cáo email nghi ngờ về hộp thư phishing của SOC; analyst phải mở thủ công từng email, kiểm tra header, URL, tệp đính kèm — chậm và không đồng nhất. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích email: bóc tách header/URL/đính kèm, đối chiếu threat intel và dấu hiệu lừa đảo (spoofing, look-alike domain, mồi khẩn cấp), chấm điểm rủi ro, sinh phán quyết (phishing/an toàn/nghi ngờ) kèm bằng chứng và khuyến nghị xử lý (cách ly, cảnh báo toàn hệ); đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Không tự cách ly hộp thư/chặn người gửi hay xóa email khi chưa có HITL duyệt; xử lý URL/đính kèm trong sandbox an toàn, không mở trên máy thật; grounded trên bằng chứng kỹ thuật (chống bịa); cực kỳ cảnh giác indirect prompt injection vì nội dung email do kẻ tấn công soạn (làm sạch trước khi đưa vào LLM); bảo vệ PII trong email; least-privilege truy cập mailbox; giảm false positive; kiểm soát độ trễ/chi phí.

### 🛠️ Tech Stack
• LLM
• LangGraph
• parser email (header/SPF/DKIM/DMARC), URL sandbox, phân tích đính kèm
• RAG threat intel + phishing DB Qdrant
• NeMo Guardrails chống prompt injection
• Presidio PII
• FastAPI
• React/Next.js
• Langfuse
• DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (SOC Analyst, Admin)
• nộp email nghi ngờ, agent phân tích & phán quyết kèm bằng chứng, HITL duyệt trước khi cách ly/cảnh báo, xử lý lỗi khi email hỏng định dạng.

Nâng cao:
• Multi-agent (Header + URL + Attachment Analyzer)
• eval đo độ chính xác phân loại & false positive
• guardrails mạnh chống indirect prompt injection từ nội dung email
• trace
• PII redaction
• tối ưu chi phí/độ trễ và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-09] AutoSOAR - AI Agent điều phối ứng phó sự cố & tự khắc phục có kiểm soát

### 📝 Mô tả đề tài
📍 Thực trạng: Khi có sự cố (máy nhiễm mã độc, tài khoản bị chiếm), quy trình ứng phó của Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp gồm nhiều bước thủ công theo playbook, phản ứng chậm khiến thiệt hại lan rộng. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent SOAR: nhận sự cố, lập kế hoạch ứng phó theo playbook phù hợp, gọi các tool khắc phục (cách ly host, reset session, chặn IOC) theo trình tự, ghi lại toàn bộ hành động và cập nhật trạng thái sự cố; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Mọi hành động state-changing/ảnh hưởng lớn (cách ly host, khóa tài khoản, chặn IP) BẮT BUỘC qua HITL approval gate (hiện hành động + lý do + phạm vi ảnh hưởng → chờ Approve/Reject qua Slack/Teams); chỉ chạy trên môi trường mô phỏng/staging, không tác động hạ tầng thật; agent least-privilege theo playbook; grounded trên bằng chứng sự cố (chống bịa hành động); chống prompt injection từ dữ liệu sự cố; bảo vệ PII; kiểm soát độ trễ để ứng phó kịp & chi phí.

### 🛠️ Tech Stack
• LLM
• LangGraph orchestration
• playbook engine + Custom Tools (EDR/firewall/IdP mock) qua MCP
• RAG playbook/threat intel Qdrant
• Slack/Teams HITL bot
• NeMo Guardrails
• Presidio
• FastAPI
• React/Next.js incident console
• Langfuse
• DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Responder, Approver)
• tạo sự cố, agent lập & thực thi kế hoạch với HITL approval cho mỗi hành động rủi ro, timeline hành động, xử lý lỗi khi tool thất bại + rollback.

Nâng cao:
• Multi-agent (Planner + Executor + Scribe)
• eval đo độ đúng của kế hoạch ứng phó vs playbook chuẩn (LLM-as-Judge)
• trace
• guardrails + least-privilege
• tối ưu độ trễ/chi phí và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-10] HuntHypothesis - AI Agent săn mối đe dọa theo giả thuyết

### 📝 Mô tả đề tài
📍 Thực trạng: Threat hunting chủ động ở Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp phụ thuộc vào ít chuyên gia biết đặt giả thuyết và viết truy vấn săn tìm phức tạp trên kho log; khó nhân rộng và không đều tay. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent threat hunting: từ một kỹ thuật MITRE ATT&CK hoặc dấu hiệu, tự sinh giả thuyết săn tìm, chuyển thành truy vấn trên SIEM, chạy và phân tích kết quả, tinh chỉnh giả thuyết theo vòng lặp, rồi tổng hợp phát hiện kèm mức độ tin cậy và khuyến nghị; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Agent chỉ đọc log (read-only), không thực hiện hành động ngăn chặn khi chưa có HITL; chạy trên tập dữ liệu log mô phỏng/staging; grounded trên bằng chứng truy vấn thật, chống bịa phát hiện; giảm false positive; bảo vệ PII trong log; least-privilege truy cập SIEM; chống prompt injection từ nội dung log; kiểm soát chi phí truy vấn/độ trễ khi quét dữ liệu lớn.

### 🛠️ Tech Stack
• LLM
• LangGraph
• SIEM Elastic/Wazuh (KQL/Lucene)
• RAG MITRE ATT&CK + TTP Qdrant/GraphRAG
• Presidio
• FastAPI
• React/Next.js hunt board
• NeMo Guardrails
• Langfuse
• RAGAS/DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Hunter, Lead)
• chọn kỹ thuật ATT&CK, agent sinh giả thuyết + truy vấn + phân tích kết quả, HITL duyệt truy vấn trước khi chạy trên dữ liệu lớn, xử lý lỗi truy vấn.

Nâng cao:
• Vòng lặp tự tinh chỉnh giả thuyết đa bước
• eval đo tỉ lệ phát hiện đúng & false positive trên dataset có ground truth
• trace reasoning
• guardrails + PII
• tối ưu chi phí truy vấn/độ trễ và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-11] RootCauseAI - AI Agent tương quan log/SIEM & truy nguyên nguyên nhân gốc

### 📝 Mô tả đề tài
📍 Thực trạng: Khi một sự cố xảy ra, analyst phải ghép nối thủ công log từ nhiều nguồn (firewall, app, auth, endpoint) theo dòng thời gian để tìm nguyên nhân gốc — chậm và dễ sai khi dữ liệu khổng lồ. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tương quan đa nguồn: chuẩn hóa & liên kết sự kiện theo thời gian và thực thể (user/host/IP), dựng chuỗi nhân-quả, xác định điểm khởi phát và nguyên nhân gốc, giải thích bằng ngôn ngữ tự nhiên kèm bằng chứng log cụ thể; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Agent chỉ đọc/phân tích, không hành động khắc phục khi chưa có HITL; chạy trên log mô phỏng/staging; mọi kết luận nhân-quả phải grounded trên bằng chứng log, chống bịa suy diễn; giảm false correlation; bảo vệ PII trong log (redact trước khi vào RAG/log server); least-privilege; chống prompt injection từ nội dung log; kiểm soát chi phí/độ trễ với khối lượng log lớn.

### 🛠️ Tech Stack
• LLM
• LangGraph
• SIEM Elastic/Wazuh
• GraphRAG Neo4j dựng đồ thị sự kiện-thực thể
• Qdrant
• Presidio redact PII
• FastAPI
• React/Next.js timeline & graph viewer
• NeMo Guardrails
• Langfuse
• DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Analyst, Lead)
• nạp bộ log sự cố, agent tương quan & trình bày chuỗi nhân-quả + nguyên nhân gốc kèm bằng chứng, HITL xác nhận kết luận, xử lý lỗi khi log thiếu/lệch thời gian.

Nâng cao:
• Đồ thị thực thể-sự kiện GraphRAG
• eval đo độ chính xác truy nguyên nguyên nhân gốc (LLM-as-Judge trên case có ground truth)
• trace
• guardrails + PII redaction
• tối ưu chi phí/độ trễ và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-12] RuleForge - AI Agent sinh & kiểm thử luật phát hiện Sigma/YARA

### 📝 Mô tả đề tài
📍 Thực trạng: Đội detection engineering của Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp viết luật Sigma/YARA thủ công dựa trên mẫu tấn công mới, quá trình chậm, dễ tạo luật quá rộng (nhiều false positive) hoặc quá hẹp (bỏ sót). Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent detection engineering: từ mô tả TTP hoặc mẫu mã độc/log tấn công, tự sinh luật Sigma/YARA, kiểm thử trên tập dữ liệu lành tính và độc hại để đo hiệu quả, tự tinh chỉnh giảm false positive, và sinh tài liệu luật kèm ánh xạ MITRE ATT&CK; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Luật chỉ được triển khai sau HITL duyệt (không tự đẩy vào SIEM production); mọi luật phải grounded trên mẫu/bằng chứng thật, chống bịa; đo và tối ưu tỉ lệ phát hiện đúng vs false positive trên tập test; chạy kiểm thử trong môi trường mô phỏng/staging an toàn (mẫu mã độc trong sandbox); bảo vệ dữ liệu mẫu nhạy cảm; least-privilege; chống prompt injection từ mẫu đầu vào; kiểm soát chi phí/độ trễ khi kiểm thử.

### 🛠️ Tech Stack
• LLM
• LangGraph
• Sigma/YARA engine + bộ test benign/malicious
• RAG MITRE ATT&CK + rule repo Qdrant
• sandbox
• FastAPI
• React/Next.js rule studio
• NeMo Guardrails
• Langfuse
• DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Detection Engineer, Reviewer)
• nhập TTP/mẫu, agent sinh luật Sigma/YARA + chạy test hiển thị precision/recall, HITL duyệt trước khi 'ban hành', xử lý lỗi cú pháp luật.

Nâng cao:
• Vòng lặp tự tinh chỉnh giảm false positive
• eval benchmark trên dataset chuẩn (đo detection rate & FP)
• trace
• guardrails
• ánh xạ ATT&CK coverage
• tối ưu chi phí/độ trễ và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-13] MalwareBriefer - AI Agent tóm tắt & phân tích báo cáo sandbox mã độc

### 📝 Mô tả đề tài
📍 Thực trạng: Báo cáo sandbox (Cuckoo/Any.Run) cho mỗi mẫu mã độc dài hàng chục trang JSON hành vi, IOC, API call; analyst mất nhiều thời gian đọc để rút ra bản chất và mức độ nguy hiểm. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích: đọc báo cáo sandbox, trích xuất IOC, hành vi chính (persistence, C2, exfiltration), ánh xạ kỹ thuật MITRE ATT&CK, đánh giá mức độ nguy hiểm và họ mã độc khả dĩ, rồi sinh brief ngắn gọn cho analyst kèm khuyến nghị; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Không tự tạo blocklist/chặn IOC trên hệ thống thật khi chưa có HITL; chỉ phân tích báo cáo/mẫu trong môi trường sandbox mô phỏng an toàn, không thực thi mã độc ngoài sandbox; grounded trên dữ liệu báo cáo thật, chống bịa họ mã độc/kỹ thuật; giảm false positive khi gán ATT&CK; bảo vệ dữ liệu nhạy cảm; least-privilege; chống prompt injection ẩn trong chuỗi/log mã độc; kiểm soát chi phí/độ trễ với báo cáo lớn.

### 🛠️ Tech Stack
• LLM
• LangGraph
• parser báo cáo Cuckoo/CAPE JSON
• RAG MITRE ATT&CK + malware KB Qdrant/GraphRAG
• NeMo Guardrails
• FastAPI
• React/Next.js report viewer
• Langfuse
• DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Malware Analyst, Lead)
• nạp báo cáo sandbox, agent trích IOC + tóm tắt hành vi + ánh xạ ATT&CK, HITL duyệt trước khi xuất IOC vào watchlist, xử lý lỗi báo cáo hỏng.

Nâng cao:
• Multi-agent (IOC Extractor + Behavior Analyzer + ATT&CK Mapper)
• eval đo độ chính xác trích IOC & ánh xạ ATT&CK
• trace
• guardrails chống prompt injection từ chuỗi mã độc
• tối ưu chi phí/độ trễ và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-14] TimelineDFIR - AI Agent dựng lại dòng thời gian điều tra số (DFIR)

### 📝 Mô tả đề tài
📍 Thực trạng: Trong điều tra pháp y số, chuyên gia phải ghép nối bằng chứng từ nhiều artifact (log, registry, filesystem, network) để dựng lại dòng thời gian sự cố — công việc tỉ mỉ, tốn hàng giờ và dễ bỏ sót mắt xích. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent DFIR: thu nhận các artifact điều tra, chuẩn hóa mốc thời gian, dựng lại timeline sự kiện tấn công (từ xâm nhập ban đầu đến hành động cuối), xác định các mốc quan trọng và khoảng trống bằng chứng, sinh báo cáo điều tra có trích dẫn artifact nguồn; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Agent chỉ đọc/phân tích artifact, không thay đổi/tác động lên bằng chứng (bảo toàn chain-of-custody), không hành động khắc phục khi chưa có HITL; chỉ chạy trên dữ liệu điều tra mô phỏng/staging; mọi mốc timeline grounded trên artifact cụ thể, chống bịa; giảm suy diễn sai; bảo vệ PII trong bằng chứng; least-privilege; chống prompt injection từ nội dung artifact; kiểm soát chi phí/độ trễ.

### 🛠️ Tech Stack
• LLM
• LangGraph
• parser artifact (EVTX, registry, MFT, pcap) + timeline builder
• GraphRAG Neo4j
• Qdrant
• Presidio
• FastAPI
• React/Next.js timeline viewer
• NeMo Guardrails
• Langfuse
• DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Forensic Investigator, Lead)
• nạp bộ artifact, agent dựng timeline sự cố kèm trích dẫn nguồn, HITL xác nhận các mốc quan trọng, xử lý lỗi artifact thiếu/lệch múi giờ.

Nâng cao:
• Multi-agent (Artifact Parser + Correlator + Reporter)
• eval đo độ chính xác timeline vs ground truth (LLM-as-Judge)
• trace
• guardrails + PII redaction + bảo toàn bằng chứng
• tối ưu chi phí/độ trễ và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-15] RiskRank - AI Agent xếp hạng ưu tiên lỗ hổng theo rủi ro & khả năng khai thác

### 📝 Mô tả đề tài
📍 Thực trạng: Máy quét lỗ hổng trả về hàng nghìn CVE với điểm CVSS, nhưng đội Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp không thể vá tất cả; ưu tiên chỉ theo CVSS bỏ qua ngữ cảnh khai thác thực tế và tầm quan trọng tài sản. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent xếp hạng lỗ hổng: kết hợp CVSS với dữ liệu exploit thực tế (EPSS, CISA KEV, PoC công khai), tầm quan trọng tài sản và khả năng tiếp cận, đối chiếu threat intel để tính điểm rủi ro ưu tiên vá, kèm giải thích và lộ trình khắc phục; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Agent chỉ khuyến nghị, không tự tạo/đóng ticket vá hay thay đổi cấu hình khi chưa có HITL; grounded trên bằng chứng CVE/EPSS/KEV thật, chống bịa điểm rủi ro; giảm false positive trong xếp hạng; chỉ dùng dữ liệu tài sản mô phỏng/staging; bảo vệ dữ liệu tài sản nhạy cảm; least-privilege; chống prompt injection từ mô tả CVE; kiểm soát chi phí/độ trễ khi xử lý danh sách lớn.

### 🛠️ Tech Stack
• LLM
• LangGraph
• nguồn NVD/EPSS/CISA KEV + Exploit-DB
• RAG threat intel Qdrant/GraphRAG
• FastAPI
• React/Next.js prioritization dashboard
• NeMo Guardrails
• Langfuse
• DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark an ninh ứng dụng SastBench / OWASP Benchmark / Juliet Test Suite, danh mục lỗ hổng bị khai thác thực tế CISA KEV + NVD CVE/EPSS và mẫu hạ tầng lỗi CloudGoat / TerraGoat.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Vuln Analyst, Manager)
• nạp danh sách lỗ hổng, agent tính điểm rủi ro & xếp hạng ưu tiên kèm lý do và trích dẫn, HITL duyệt trước khi tạo kế hoạch vá, xử lý lỗi dữ liệu thiếu.

Nâng cao:
• Multi-agent (Enrichment + Risk Scorer + Remediation Planner)
• eval đo tương quan xếp hạng với khai thác thực tế
• trace
• guardrails
• grounded qua RAG có trích dẫn
• tối ưu chi phí/độ trễ và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-16] CloudPosture - AI Agent đánh giá cấu hình an ninh cloud (CSPM) & quét IaC

### 📝 Mô tả đề tài
📍 Thực trạng: Hạ tầng cloud của doanh nghiệp mở rộng nhanh; cấu hình sai (S3 public, IAM quá rộng, security group mở) và lỗi trong mã IaC (Terraform) dễ lọt qua review thủ công gây phơi nhiễm. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent CSPM: quét cấu hình cloud và mã IaC (Terraform/CloudFormation), phát hiện cấu hình sai vi phạm chuẩn (CIS Benchmark), giải thích rủi ro và tác động, sinh bản vá cấu hình/IaC đề xuất kèm ưu tiên khắc phục; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Agent chỉ phát hiện & đề xuất, không tự áp dụng thay đổi cấu hình cloud khi chưa có HITL duyệt (đặc biệt hành động thay đổi quyền/mở-đóng tài nguyên); chỉ chạy trên tài khoản cloud sandbox/mô phỏng, không đụng production thật; grounded trên chuẩn CIS/bằng chứng cấu hình thật, chống bịa; giảm false positive; bảo vệ secret/credential (không log lộ); least-privilege (chỉ đọc cấu hình); chống prompt injection từ mô tả tài nguyên; kiểm soát chi phí/độ trễ.

### 🛠️ Tech Stack
• LLM
• LangGraph
• công cụ Checkov/tfsec/Prowler + parser IaC
• RAG CIS Benchmark/best practices Qdrant
• Presidio/secret scanner
• FastAPI
• React/Next.js findings dashboard
• NeMo Guardrails
• Langfuse
• DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark an ninh ứng dụng SastBench / OWASP Benchmark / Juliet Test Suite, danh mục lỗ hổng bị khai thác thực tế CISA KEV + NVD CVE/EPSS và mẫu hạ tầng lỗi CloudGoat / TerraGoat.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Cloud Security Engineer, Lead)
• nạp cấu hình cloud/IaC, agent phát hiện cấu hình sai + đề xuất bản vá kèm chuẩn CIS, HITL duyệt trước khi xuất/áp dụng vá, xử lý lỗi khi IaC không parse được.

Nâng cao:
• Multi-agent (Scanner + Risk Explainer + Fix Generator)
• eval đo độ chính xác phát hiện & false positive trên dataset cấu hình sai
• trace
• guardrails + bảo vệ secret
• grounded qua RAG
• tối ưu chi phí/độ trễ và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-17] PromptShield - AI Agent guardrails chống indirect prompt injection cho hệ AI-SOC

### 📝 Mô tả đề tài
📍 Thực trạng: Các agent AI-SOC của Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp phải đọc dữ liệu do bên ngoài kiểm soát (response ứng dụng mục tiêu, nội dung email, log), và kẻ tấn công có thể nhúng chỉ thị độc hại nhằm hijack agent (indirect prompt injection).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng lớp AI Agent guardrails đứng giữa: kiểm tra và làm sạch mọi dữ liệu ngoài trước khi vào LLM của agent khác, phát hiện mưu đồ tiêm chỉ thị (jailbreak, đảo vai, rò rỉ system prompt), gắn cờ/vô hiệu hóa nội dung độc và ghi nhận sự kiện tấn công; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Guardrail không được tự thay đổi luồng nghiệp vụ khi chặn nhầm mà phải cho HITL xem lại các trường hợp gắn cờ mức cao; phải grounded trên bằng chứng mẫu tấn công, giảm false positive để không cản trở agent hợp lệ; chạy trên dữ liệu mô phỏng/staging chứa payload tấn công đã biết; bảo vệ PII và system prompt; least-privilege; đo hiệu quả chặn injection; kiểm soát độ trễ (guardrail nằm trên đường tới hạn) & chi phí.

### 🛠️ Tech Stack
• LLM + classifier chuyên biệt
• LangGraph
• NeMo Guardrails + prompt-injection detector
• RAG thư viện mẫu injection Qdrant
• Presidio
• FastAPI middleware
• React/Next.js dashboard sự kiện
• Langfuse
• DeepEval/promptfoo
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Security Engineer, Reviewer)
• pipeline nhận dữ liệu ngoài, agent làm sạch & gắn cờ injection với log sự kiện, HITL xem lại các gắn cờ mức cao, xử lý lỗi.

Nâng cao:
• Benchmark chống một bộ payload prompt injection đa dạng, đo tỉ lệ chặn & false positive
• trace
• tích hợp bảo vệ cho ≥1 agent thật (ví dụ FuzzMind/PhishHunter)
• tối ưu độ trễ lớp guardrail & chi phí, báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-18] PIIRedactor - AI Agent che dữ liệu nhạy cảm/PII thời gian thực cho agent SOC

### 📝 Mô tả đề tài
📍 Thực trạng: Trong quá trình pentest/điều tra, agent có thể dump được cơ sở dữ liệu mock chứa PII (email, mật khẩu, SSN, số thẻ) và dữ liệu này chảy vào memory, log, RAG — vi phạm quyền riêng tư và tạo rủi ro rò rỉ. Trong vận hành an ninh mạng thực tế của doanh nghiệp, dữ liệu log và cảnh báo bảo mật có khối lượng khổng lồ với tỷ lệ nhiễu (false positive) rất cao, trong khi các cuộc tấn công hiện đại thường ẩn mình qua nhiều bước tinh vi và thậm chí chèn payload độc hại vào dữ liệu đầu vào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent che PII thời gian thực: chặn ở luồng dữ liệu của các agent SOC, phát hiện và redact PII/secret trước khi ghi vào logging server, memory hoặc RAG, giữ lại đủ ngữ cảnh để phân tích mà không lộ dữ liệu gốc, và ghi nhận thống kê loại PII đã che; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Redaction phải diễn ra realtime trước khi dữ liệu vào bất kỳ nơi lưu trữ nào; trường hợp gỡ che (un-redact) nếu có phải qua HITL duyệt chặt chẽ; chạy trên DB mock/staging, không dùng dữ liệu người thật; grounded và giảm cả false negative (bỏ sót PII) lẫn false positive (che nhầm dữ liệu cần thiết); least-privilege; chống prompt injection lợi dụng để làm lộ PII; kiểm soát độ trễ (nằm trên đường tới hạn) & chi phí.

### 🛠️ Tech Stack
• LLM + NER
• LangGraph
• Microsoft Presidio + regex/checksum (thẻ, SSN)
• tích hợp middleware log/memory/RAG
• Qdrant
• FastAPI
• React/Next.js dashboard PII
• NeMo Guardrails
• Langfuse
• DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Privacy Officer, Analyst)
• luồng dữ liệu agent đi qua bộ redact realtime, dashboard thống kê PII đã che, HITL duyệt yêu cầu un-redact, xử lý lỗi khi phát hiện định dạng lạ.

Nâng cao:
• Đánh giá độ chính xác redaction (precision/recall theo loại PII) trên dataset gán nhãn
• tích hợp bảo vệ cho ≥1 agent thật (ví dụ PentestSyndicate)
• trace
• guardrails chống rò rỉ
• tối ưu độ trễ realtime & chi phí, báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-19] RedTeamAI - AI Agent red-team tự động kiểm thử đối kháng chính hệ AI-SOC

### 📝 Mô tả đề tài
📍 Thực trạng: Hệ AI-SOC của Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp ngày càng phức tạp với nhiều agent LLM; bản thân chúng có thể bị tấn công (prompt injection, jailbreak, đầu độc dữ liệu, lạm quyền) nhưng chưa được kiểm thử đối kháng có hệ thống.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent red-team tự động tấn công chính các agent phòng thủ AI-SOC: sinh và thử các kỹ thuật đối kháng (indirect prompt injection, jailbreak, vượt scope IAM, đầu độc RAG), đo agent mục tiêu có bị hijack/lộ dữ liệu/hành động sai không, rồi tổng hợp báo cáo điểm yếu và khuyến nghị vá guardrails; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Chỉ tấn công các agent nội bộ trong môi trường mô phỏng/staging được cấp phép, tuyệt đối không nhắm hệ thống ngoài; hành động tấn công có tính phá hoại/thay đổi trạng thái phải qua HITL duyệt; red-team agent least-privilege, không tự vá; grounded trên bằng chứng phản hồi thật của agent mục tiêu, chống bịa lỗ hổng; giảm false positive; bảo vệ PII lộ ra trong quá trình test; chống chính red-team agent bị lợi dụng; kiểm soát chi phí/độ trễ.

### 🛠️ Tech Stack
• LLM
• LangGraph/CrewAI
• thư viện adversarial (garak/PyRIT) + custom attack tools qua MCP
• RAG kỹ thuật tấn công LLM Qdrant
• Kong Gateway kiểm soát scope
• Slack/Teams HITL
• FastAPI
• React/Next.js report
• Langfuse/LangSmith
• DeepEval/promptfoo
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark bảo mật AI Agent: BIPIA (Indirect Prompt Injection), HarmBench, JailbreakBench, Garak / PyRIT payloads và dữ liệu kiểm tra rò rỉ thông tin nhạy cảm Microsoft Presidio / Gitleaks.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Red-teamer, Approver)
• chọn agent mục tiêu nội bộ, chạy bộ tấn công đối kháng, báo cáo điểm yếu kèm bằng chứng, HITL duyệt các tấn công rủi ro, xử lý lỗi.

Nâng cao:
• Multi-agent (Attack Planner + Executor + Evaluator)
• benchmark tỉ lệ tấn công thành công theo loại (đo attack success rate & false positive)
• trace
• least-privilege qua Gateway
• tối ưu chi phí/độ trễ và báo cáo, khép vòng với đội blue-team
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---

## [VSOC-20] ComplianceAuditor - AI Agent kiểm toán tuân thủ & đối chiếu chuẩn an ninh

### 📝 Mô tả đề tài
📍 Thực trạng: Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp phải chứng minh tuân thủ nhiều khung (ISO 27001, PCI-DSS, MITRE ATT&CK coverage, NIST CSF); việc thu thập bằng chứng và đối chiếu từng điều khoản với cấu hình/chính sách thực tế là thủ công, tốn kém và dễ lỗi thời.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent kiểm toán tuân thủ: đọc chính sách, cấu hình, log kiểm soát của tổ chức, đối chiếu với từng điều khoản của chuẩn qua RAG, đánh giá đạt/không đạt/một phần kèm bằng chứng và khoảng trống (gap), sinh báo cáo audit và khuyến nghị khắc phục có ưu tiên; đồng thời vượt qua việc chấm điểm cảnh báo tĩnh bằng cách phân tích khả năng tiếp cận và đường dẫn khai thác thực tế (reachability/attack-path graph), tương quan chuỗi tấn công đa nguồn theo chuẩn MITRE ATT&CK và ước lượng bán kính ảnh hưởng trước khi phản ứng.

🔒 Ràng buộc: Agent chỉ đánh giá & báo cáo, không tự thay đổi cấu hình/chính sách khi chưa có HITL; mọi phán quyết tuân thủ phải grounded trên bằng chứng thật + điều khoản chuẩn có trích dẫn, tuyệt đối chống bịa (audit sai gây hậu quả pháp lý); giảm false positive/negative trong đánh giá; chạy trên dữ liệu chính sách/cấu hình mô phỏng/staging; bảo vệ dữ liệu nhạy cảm & PII trong bằng chứng; least-privilege (chỉ đọc); chống prompt injection từ tài liệu chính sách; kiểm soát chi phí/độ trễ khi đối chiếu nhiều điều khoản.

### 🛠️ Tech Stack
• LLM
• LangGraph
• RAG các khung ISO 27001/PCI-DSS/NIST CSF/MITRE ATT&CK Qdrant + GraphRAG mapping điều khoản-kiểm soát
• Presidio
• FastAPI
• React/Next.js compliance dashboard (heatmap coverage)
• NeMo Guardrails
• Langfuse
• RAGAS/DeepEval
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark an ninh ứng dụng SastBench / OWASP Benchmark / Juliet Test Suite, danh mục lỗ hổng bị khai thác thực tế CISA KEV + NVD CVE/EPSS và mẫu hạ tầng lỗi CloudGoat / TerraGoat.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập, ≥2 vai trò (Auditor, Compliance Manager)
• chọn chuẩn, nạp chính sách/cấu hình, agent đối chiếu & chấm đạt/không đạt kèm bằng chứng trích dẫn điều khoản, HITL duyệt kết luận trước khi phát hành báo cáo, xử lý lỗi tài liệu thiếu.

Nâng cao:
• GraphRAG ánh xạ điều khoản-kiểm soát & coverage MITRE ATT&CK
• eval đo độ chính xác phán quyết tuân thủ & faithfulness (RAGAS/LLM-as-Judge)
• trace
• guardrails + bảo vệ PII
• grounded có trích dẫn
• tối ưu chi phí/độ trễ và báo cáo
• Tích hợp phân tích đồ thị đường dẫn tấn công / khả năng khai thác thực tế (reachability & blast-radius analysis) và kiểm chứng tự động giúp cắt giảm tỷ lệ cảnh báo giả (false positive) trên dữ liệu benchmark.

---
