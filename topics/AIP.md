# Lĩnh vực: AIP - Mô hình nền tảng AI – Hạ tầng AI doanh nghiệp

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `AIP-01` | [AI Agent Gateway định tuyến model đa nhà cung cấp theo chi phí & chất lượng](#aip-01) |
| `AIP-02` | [AI Agent quản lý & versioning Prompt tập trung cho toàn tập đoàn](#aip-02) |
| `AIP-03` | [AI Agent tự động chạy Eval & Benchmark LLM và sinh báo cáo](#aip-03) |
| `AIP-04` | [AI Agent RAG Platform tự đánh giá & tối ưu chất lượng truy hồi (RAGAS)](#aip-04) |
| `AIP-05` | [AI Agent giám sát Guardrails & phát hiện Prompt Injection / rò rỉ PII](#aip-05) |
| `AIP-06` | [AI Agent Builder – Trợ lý dựng Agent mới từ mô tả ngôn ngữ tự nhiên](#aip-06) |
| `AIP-07` | [AI Agent tối ưu chi phí Token & chiến lược Caching cho dịch vụ LLM](#aip-07) |
| `AIP-08` | [AI Agent theo dõi Drift & suy giảm chất lượng model trên Production](#aip-08) |
| `AIP-09` | [AI Agent tổng hợp & phân loại phản hồi người dùng về sản phẩm AI](#aip-09) |
| `AIP-10` | [AI Agent Red-Team tự động dò lỗ hổng an toàn của hệ thống LLM](#aip-10) |
| `AIP-11` | [AI Agent quản lý & tra cứu tri thức nội bộ MLOps/AI của tập đoàn](#aip-11) |
| `AIP-12` | [AI Agent tự động sinh Test Case cho tính năng LLM](#aip-12) |
| `AIP-13` | [AI Agent điều phối quy trình Fine-tune & Data Labeling](#aip-13) |
| `AIP-14` | [AI Agent giám sát Độ trễ & SLA của các dịch vụ AI nội bộ](#aip-14) |
| `AIP-15` | [AI Agent so sánh & tuyển chọn Model LLM mới cho nền tảng](#aip-15) |
| `AIP-16` | [AI Agent quản lý Vòng đời Dataset huấn luyện (Data Lifecycle)](#aip-16) |
| `AIP-17` | [AI Agent Trợ lý Tuân thủ AI Governance & chính sách nội bộ](#aip-17) |
| `AIP-18` | [AI Agent quan sát & gỡ lỗi hệ thống Multi-Agent (AgentOps Tracing)](#aip-18) |
| `AIP-19` | [AI Agent FinOps – quản lý ngân sách & phân bổ chi phí LLM theo đơn vị](#aip-19) |
| `AIP-20` | [AI Agent tự động tối ưu Prompt (Prompt Optimization) theo mục tiêu](#aip-20) |

---

## [AIP-01] AI Agent Gateway định tuyến model đa nhà cung cấp theo chi phí & chất lượng

### 📝 Mô tả đề tài
📍 Thực trạng: Nền tảng AI của tập đoàn phục vụ hàng chục ứng dụng nội bộ (doanh nghiệp bất động sản, doanh nghiệp ô tô, hệ thống y tế / bệnh viện...) gọi tới nhiều LLM khác nhau (OpenAI, Anthropic, Gemini, model nội bộ của doanh nghiệp). Các đội tự chọn model cứng trong code, không tối ưu được chi phí/chất lượng và không có điểm kiểm soát tập trung.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent gateway thông minh nhận request, phân tích độ khó tác vụ, tự lập kế hoạch định tuyến tới model phù hợp nhất (rẻ cho task đơn giản, mạnh cho task khó), fallback khi lỗi/timeout, và ghi nhận metrics để tối ưu liên tục; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL cho việc thay đổi chính sách định tuyến production; bảo mật khóa API và che PII trước khi gửi ra nhà cung cấp ngoài; eval chất lượng định tuyến phải đạt ngưỡng thỏa thuận; cảnh báo khi chi phí/độ trễ vượt ngân sách. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LiteLLM (unified gateway đa provider) + LangGraph điều phối agent định tuyến
• LLM: GPT-4o/Claude/Gemini/model nội bộ
• classifier độ khó bằng LLM nhỏ + embeddings (pgvector)
• observability Langfuse
• backend FastAPI
• Redis cache
• PostgreSQL lưu log & policy
• frontend Next.js + Tailwind (dashboard định tuyến)
• deploy Docker trên Render/Railway/VPS.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy online, đăng nhập ≥2 vai trò (Kỹ sư AI dùng gateway, Admin nền tảng)
• agent nhận prompt, phân loại độ khó, định tuyến tới ≥3 model, fallback khi lỗi
• dashboard hiển thị chi phí/độ trễ/chất lượng theo model.

Nâng cao:
• Agent tự học lại policy từ metrics lịch sử, A/B test định tuyến, cảnh báo vượt ngân sách qua email/Slack, HITL phê duyệt thay đổi policy, memory lưu preference theo từng ứng dụng
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-02] AI Agent quản lý & versioning Prompt tập trung cho toàn tập đoàn

### 📝 Mô tả đề tài
📍 Thực trạng: Prompt của các sản phẩm AI nằm rải rác trong code, Google Sheet, Notion; mỗi lần chỉnh sửa không có lịch sử, không rollback được, không biết phiên bản nào đang chạy production. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng có agent hỗ trợ tạo/sửa/versioning prompt, tự đề xuất cải tiến, chạy eval so sánh phiên bản mới vs cũ trước khi phát hành, và đồng bộ prompt tới ứng dụng qua API/SDK; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL bắt buộc để duyệt promote phiên bản lên production; phân quyền chỉnh sửa theo vai trò; eval hồi quy để đảm bảo không giảm chất lượng; cảnh báo thay đổi làm tăng token/chi phí. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph agent + LLM đa provider
• DeepEval/Promptfoo để eval so sánh phiên bản
• embeddings + pgvector tìm prompt tương tự
• Langfuse tracing
• backend FastAPI, PostgreSQL (version history), Redis
• frontend Next.js (diff viewer, playground)
• Git-like versioning
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Prompt Engineer, Reviewer/Admin)
• CRUD prompt có version, diff, rollback
• agent chạy eval so sánh 2 phiên bản trên bộ test
• API phát hành prompt cho ứng dụng.

Nâng cao:
• Agent tự đề xuất cải tiến prompt và giải thích lý do, canary release theo %, HITL phê duyệt promote, memory lưu bài học tối ưu, cảnh báo tăng chi phí token
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-03] AI Agent tự động chạy Eval & Benchmark LLM và sinh báo cáo

### 📝 Mô tả đề tài
📍 Thực trạng: Khi có model mới hoặc thay đổi prompt, đội AI phải chạy benchmark thủ công, tốn thời gian và không nhất quán về bộ tiêu chí. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự lập kế hoạch chạy bộ eval (accuracy, hallucination, toxicity, format, latency, cost) trên nhiều model/dataset, tổng hợp kết quả và sinh báo cáo có khuyến nghị chọn model; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt bộ tiêu chí & dataset nhạy cảm; bảo mật dữ liệu test nội bộ; đảm bảo độ chính xác của LLM-as-judge (đối chiếu human sampling); kiểm soát chi phí khi chạy nhiều model. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph orchestrator
• DeepEval + Ragas + LLM-as-judge
• LLM đa provider qua LiteLLM
• datasets lưu PostgreSQL/S3
• Langfuse
• backend FastAPI, Celery/queue chạy batch
• frontend Next.js (bảng leaderboard, biểu đồ Recharts)
• export PDF/Markdown
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Kỹ sư eval, Quản lý)
• agent chạy ≥4 loại metric trên ≥3 model, lưu kết quả, sinh báo cáo có bảng xếp hạng & khuyến nghị.

Nâng cao:
• Lập lịch benchmark định kỳ, phát hiện regression, human-in-the-loop chấm lại mẫu để hiệu chỉnh judge, cảnh báo chi phí, memory theo dõi lịch sử benchmark theo thời gian
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-04] AI Agent RAG Platform tự đánh giá & tối ưu chất lượng truy hồi (RAGAS)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhiều ứng dụng RAG nội bộ (tra cứu tài liệu hệ thống y tế / bệnh viện, sổ tay kỹ thuật xe) bị trả lời sai/bịa do chất lượng chunk & retrieval kém, nhưng không đội nào đo được chất lượng RAG một cách hệ thống. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng cho phép nạp tài liệu, dựng pipeline RAG, và một agent tự đánh giá bằng RAGAS (faithfulness, context precision/recall, answer relevancy), tự đề xuất chỉnh chunking/embedding/reranker; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt thay đổi cấu hình production; bảo mật tài liệu phân quyền theo đơn vị; ngưỡng chất lượng eval tối thiểu; kiểm soát chi phí embedding & LLM judge. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• Ragas eval
• vector DB Qdrant/pgvector
• embeddings đa provider
• reranker Cohere/bge
• LiteLLM
• Langfuse
• backend FastAPI, PostgreSQL
• frontend Next.js (upload, cấu hình pipeline, dashboard chất lượng)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Kỹ sư RAG, Chủ dữ liệu)
• upload tài liệu, dựng pipeline RAG hỏi đáp, agent tính điểm RAGAS trên bộ câu hỏi test.

Nâng cao:
• Agent tự thử nghiệm nhiều cấu hình chunk/embedding/reranker và đề xuất tối ưu, HITL duyệt cấu hình, cảnh báo suy giảm chất lượng theo thời gian, memory lưu cấu hình tốt nhất
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-05] AI Agent giám sát Guardrails & phát hiện Prompt Injection / rò rỉ PII

### 📝 Mô tả đề tài
📍 Thực trạng: Các sản phẩm LLM nội bộ mở cho người dùng cuối tiềm ẩn rủi ro prompt injection, jailbreak và rò rỉ dữ liệu cá nhân/nhạy cảm nhưng chưa có lớp giám sát tập trung. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent chốt chặn real-time luồng input/output: phát hiện injection, PII, nội dung độc hại, chặn hoặc che thông tin, và lập báo cáo sự cố kèm khuyến nghị; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL xử lý cảnh báo mức cao trước khi chặn diện rộng; tuân thủ bảo mật/PDPA; độ chính xác phát hiện (giảm false positive/negative); độ trễ thấp để không ảnh hưởng UX; cảnh báo khi tải cao. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph + guardrails (NeMo Guardrails/Guardrails AI/Llama Guard)
• PII detection Presidio
• LLM classifier
• Langfuse
• backend FastAPI, PostgreSQL, Redis
• frontend Next.js (bảng cảnh báo, phân loại sự cố)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Kỹ sư bảo mật AI, Vận hành)
• agent quét input/output real-time, phát hiện injection/PII/độc hại, chặn/che và ghi log
• dashboard sự cố.

Nâng cao:
• Agent tự phân loại mức độ nghiêm trọng, HITL duyệt hành động chặn, sinh báo cáo & rule mới, memory học mẫu tấn công đã gặp, cảnh báo tần suất tấn công tăng đột biến
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-06] AI Agent Builder – Trợ lý dựng Agent mới từ mô tả ngôn ngữ tự nhiên

### 📝 Mô tả đề tài
📍 Thực trạng: Mỗi đội sản phẩm muốn có agent riêng nhưng thiếu kỹ sư AI; việc dựng agent (chọn tool, prompt, luồng) mất nhiều tuần. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng meta-agent nhận mô tả nghiệp vụ, tự lập kế hoạch kiến trúc agent (tools, bước, guardrails), sinh cấu hình/luồng LangGraph, chạy thử và cho phép triển khai; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt trước khi deploy agent do người dùng tạo; kiểm soát quyền truy cập tool nhạy cảm; eval agent sinh ra đạt tiêu chí tối thiểu; cảnh báo chi phí/độ trễ dự kiến. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph (meta-agent + agent sinh ra)
• LLM đa provider
• thư viện tool chuẩn (search, DB, API)
• DeepEval smoke test
• Langfuse
• backend FastAPI, PostgreSQL lưu định nghĩa agent
• frontend Next.js (wizard + visual graph)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Người tạo agent, Admin duyệt)
• nhập mô tả → agent sinh cấu hình, chọn tool, chạy thử trong sandbox
• xem luồng trực quan.

Nâng cao:
• Agent tự eval agent sinh ra, đề xuất cải thiện, HITL phê duyệt deploy, versioning agent, memory tái sử dụng mẫu, cảnh báo tool rủi ro
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-07] AI Agent tối ưu chi phí Token & chiến lược Caching cho dịch vụ LLM

### 📝 Mô tả đề tài
📍 Thực trạng: Chi phí gọi LLM toàn tập đoàn tăng nhanh, nhiều request trùng lặp hoặc prompt dài dư thừa nhưng không có cơ chế caching/nén tập trung. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent phân tích log sử dụng, phát hiện cơ hội tiết kiệm (semantic cache, prompt compression, chọn model rẻ hơn), tự áp dụng và đo lường tác động chi phí; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt các thay đổi ảnh hưởng chất lượng; đảm bảo cache không rò rỉ dữ liệu giữa người dùng/đơn vị; eval đảm bảo chất lượng không giảm sau tối ưu; cảnh báo khi tỷ lệ cache-hit bất thường. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• semantic cache (GPTCache/Redis + embeddings)
• LLMLingua nén prompt
• LiteLLM
• Langfuse phân tích cost
• backend FastAPI, PostgreSQL, Redis
• frontend Next.js (dashboard tiết kiệm)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (FinOps AI, Kỹ sư)
• agent phân tích log, bật semantic cache & nén prompt, hiển thị chi phí trước/sau.

Nâng cao:
• Agent tự đề xuất & mô phỏng tác động tiết kiệm, HITL duyệt áp dụng, kiểm soát rò rỉ cache theo tenant, cảnh báo cache-hit thấp, memory lưu chiến lược hiệu quả
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-08] AI Agent theo dõi Drift & suy giảm chất lượng model trên Production

### 📝 Mô tả đề tài
📍 Thực trạng: Các model AI đang chạy production dần suy giảm do dữ liệu đầu vào thay đổi (data drift) nhưng đội vận hành chỉ phát hiện khi có khiếu nại. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent giám sát liên tục phân phối input/output, chất lượng phản hồi (LLM-judge trên mẫu), phát hiện drift, điều tra nguyên nhân và đề xuất hành động (retrain, đổi model, rollback); đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt hành động khắc phục; bảo mật dữ liệu sản xuất khi lấy mẫu; độ chính xác phát hiện drift (ngưỡng thống kê + eval); kiểm soát chi phí lấy mẫu judge. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• Evidently AI / thống kê drift
• LLM-as-judge (DeepEval)
• Langfuse traces
• backend FastAPI, PostgreSQL/TimescaleDB, Redis
• frontend Next.js (biểu đồ drift, alert)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (MLOps, Quản lý)
• agent theo dõi phân phối & chất lượng, phát hiện drift, hiển thị dashboard & cảnh báo.

Nâng cao:
• Agent điều tra nguyên nhân, đề xuất hành động kèm bằng chứng, HITL duyệt rollback/retrain, memory lưu sự cố drift, cảnh báo chi phí lấy mẫu
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-09] AI Agent tổng hợp & phân loại phản hồi người dùng về sản phẩm AI

### 📝 Mô tả đề tài
📍 Thực trạng: Phản hồi (rating, comment, báo lỗi) về các tính năng AI nội bộ đến từ nhiều kênh, khối lượng lớn, đội sản phẩm không kịp đọc và phân loại. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent thu thập phản hồi, phân loại (bug, hallucination, UX, feature request), gom cụm chủ đề, chấm mức nghiêm trọng, và sinh báo cáo insight kèm đề xuất ưu tiên cho từng đội; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt phân loại nhạy cảm/khiếu nại nghiêm trọng; che PII trong phản hồi; độ chính xác phân loại (đánh giá bằng mẫu gán nhãn); kiểm soát chi phí xử lý batch lớn. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• LLM phân loại + embeddings clustering (pgvector/HDBSCAN)
• Presidio che PII
• Langfuse
• backend FastAPI, PostgreSQL
• frontend Next.js (dashboard chủ đề, xu hướng)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (PM sản phẩm AI, Vận hành)
• agent phân loại & gom cụm phản hồi, hiển thị top chủ đề & mức nghiêm trọng.

Nâng cao:
• Agent sinh báo cáo insight định kỳ, đề xuất ưu tiên, phát hiện chủ đề mới nổi, HITL sửa nhãn để agent học lại, cảnh báo tăng đột biến khiếu nại
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-10] AI Agent Red-Team tự động dò lỗ hổng an toàn của hệ thống LLM

### 📝 Mô tả đề tài
📍 Thực trạng: Trước khi phát hành, các sản phẩm LLM cần kiểm thử an toàn (jailbreak, injection, thiên kiến, rò rỉ) nhưng làm thủ công không đủ độ phủ. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent red-team tự lập kế hoạch tấn công, sinh & biến thể prompt tấn công, tự thực thi với hệ thống mục tiêu, đánh giá thành công/thất bại và sinh báo cáo lỗ hổng có mức độ & khuyến nghị vá; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL cấp phép trước khi chạy trên hệ thống thật; giới hạn phạm vi tấn công & môi trường; đánh giá chính xác thành công tấn công; cảnh báo chi phí/độ trễ khi chạy hàng loạt. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• framework red-team (Garak/PyRIT) + LLM sinh tấn công
• DeepEval chấm
• Langfuse
• backend FastAPI, PostgreSQL
• frontend Next.js (báo cáo lỗ hổng, mức nghiêm trọng)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Kỹ sư an toàn AI, Chủ hệ thống)
• agent chạy ≥3 loại tấn công vào endpoint mục tiêu, đánh giá & báo cáo lỗ hổng.

Nâng cao:
• Agent tự tiến hóa biến thể tấn công, HITL cấp phép & giới hạn phạm vi, đề xuất guardrail vá lỗi, memory lưu chiến thuật hiệu quả, cảnh báo chi phí
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-11] AI Agent quản lý & tra cứu tri thức nội bộ MLOps/AI của tập đoàn

### 📝 Mô tả đề tài
📍 Thực trạng: Kiến thức vận hành AI (runbook, sự cố, best practice, cấu hình model) nằm rải rác ở Confluence, Slack, code; kỹ sư mới mất nhiều thời gian tìm kiếm. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tri thức trả lời câu hỏi vận hành có trích dẫn nguồn, gợi ý runbook xử lý sự cố, phát hiện tài liệu lỗi thời và tự đề xuất cập nhật; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt cập nhật tài liệu; phân quyền truy cập tri thức theo đơn vị; độ chính xác & chống bịa (grounded RAG, đo bằng Ragas); kiểm soát chi phí truy vấn. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph RAG agent
• vector DB Qdrant/pgvector
• Ragas eval
• embeddings
• kết nối Confluence/Notion/Slack
• Langfuse
• backend FastAPI, PostgreSQL
• frontend Next.js (chat có citation, quản lý tài liệu)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Kỹ sư AI, Quản trị tri thức)
• agent hỏi đáp có trích dẫn nguồn từ tài liệu nội bộ
• tìm kiếm ngữ nghĩa.

Nâng cao:
• Agent phát hiện tài liệu lỗi thời/mâu thuẫn và đề xuất cập nhật, HITL duyệt, gợi ý runbook sự cố, memory theo phiên, cảnh báo câu hỏi không tìm được nguồn
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-12] AI Agent tự động sinh Test Case cho tính năng LLM

### 📝 Mô tả đề tài
📍 Thực trạng: Các tính năng dùng LLM khó test vì output không xác định; đội thường thiếu bộ test bao phủ edge case, adversarial. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent phân tích đặc tả tính năng & prompt, tự sinh bộ test đa dạng (happy path, edge case, adversarial, đa ngôn ngữ), định nghĩa tiêu chí pass, chạy và báo cáo độ phủ/độ ổn định; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt bộ test trước khi đưa vào CI; bảo mật dữ liệu mẫu; độ chính xác của assertion/LLM-judge; kiểm soát chi phí sinh & chạy test lớn. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• DeepEval/Promptfoo
• LLM đa provider
• embeddings đo đa dạng test
• Langfuse
• backend FastAPI, PostgreSQL
• tích hợp GitHub Actions CI
• frontend Next.js (quản lý test suite, kết quả)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (QA/Kỹ sư, Lead)
• agent sinh ≥4 loại test từ đặc tả, chạy & báo cáo pass/fail.

Nâng cao:
• Agent tự mở rộng edge/adversarial, đo độ phủ, tích hợp CI, HITL duyệt test, memory tái dùng mẫu test, cảnh báo chi phí chạy
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-13] AI Agent điều phối quy trình Fine-tune & Data Labeling

### 📝 Mô tả đề tài
📍 Thực trạng: Quy trình fine-tune model nội bộ (chuẩn bị data, gán nhãn, kiểm chất lượng, huấn luyện, đánh giá) làm thủ công qua nhiều công cụ, dễ thiếu bước và khó theo dõi. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent điều phối end-to-end: lập kế hoạch, phân bổ nhiệm vụ gán nhãn, kiểm tra chất lượng nhãn, khởi chạy fine-tune, đánh giá và báo cáo, với con người tham gia ở các chốt quan trọng; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt dataset & quyết định huấn luyện; bảo mật dữ liệu huấn luyện; đảm bảo chất lượng nhãn (inter-annotator agreement, eval); kiểm soát chi phí GPU/gán nhãn. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph orchestrator
• tích hợp Label Studio
• job huấn luyện (HuggingFace/Modal/Replicate)
• DeepEval đánh giá
• Langfuse
• backend FastAPI, PostgreSQL, queue
• frontend Next.js (kanban pipeline, trạng thái job)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Kỹ sư ML, Người gán nhãn/Reviewer)
• agent điều phối các bước gán nhãn → kiểm chất lượng → kích hoạt fine-tune (mock/thật) → đánh giá
• theo dõi trạng thái.

Nâng cao:
• Agent kiểm tra chất lượng nhãn tự động, đề xuất mẫu cần gán thêm, HITL duyệt từng chốt, memory lưu cấu hình, cảnh báo chi phí GPU
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-14] AI Agent giám sát Độ trễ & SLA của các dịch vụ AI nội bộ

### 📝 Mô tả đề tài
📍 Thực trạng: Nhiều dịch vụ AI có cam kết SLA (độ trễ, uptime) với các khối như doanh nghiệp ô tô, dịch vụ gọi xe của doanh nghiệp nhưng việc giám sát rời rạc, phát hiện vi phạm chậm. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent theo dõi metrics thời gian thực (latency p95/p99, error rate, throughput), phát hiện suy giảm & nguy cơ vi phạm SLA, điều tra nguyên nhân (model nào, tenant nào) và đề xuất hành động; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt hành động can thiệp (scale, đổi model); bảo mật dữ liệu vận hành; độ chính xác cảnh báo (giảm nhiễu); cảnh báo sớm trước khi vi phạm SLA/vượt ngân sách. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• Prometheus/Grafana + Langfuse traces
• phân tích nguyên nhân bằng LLM
• backend FastAPI, TimescaleDB/PostgreSQL, Redis
• frontend Next.js (SLA dashboard, timeline sự cố)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (SRE/Vận hành AI, Quản lý dịch vụ)
• agent theo dõi latency/error/uptime, phát hiện vi phạm SLA, hiển thị dashboard & cảnh báo.

Nâng cao:
• Agent điều tra nguyên nhân theo model/tenant, dự báo nguy cơ vi phạm, đề xuất hành động, HITL duyệt can thiệp, memory sự cố, cảnh báo sớm
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-15] AI Agent so sánh & tuyển chọn Model LLM mới cho nền tảng

### 📝 Mô tả đề tài
📍 Thực trạng: Thị trường liên tục ra model mới; đội nền tảng khó quyết định có nên đưa vào danh mục hỗ trợ hay không vì thiếu quy trình đánh giá chuẩn theo use case của tập đoàn. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự thu thập thông tin model mới, chạy bộ eval nội bộ theo các use case (RAG, coding, tiếng Việt, tool-use), so sánh chi phí/chất lượng/độ trễ và đề xuất quyết định tuyển chọn kèm lý do; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt đưa model vào danh mục production; bảo mật dataset đánh giá; độ chính xác eval & công bằng so sánh; kiểm soát chi phí chạy nhiều model. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• LiteLLM kết nối model mới
• DeepEval + Ragas theo use case
• WebSearch thu thập thông tin model
• Langfuse
• backend FastAPI, PostgreSQL
• frontend Next.js (bảng so sánh, radar chart)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Kỹ sư nền tảng, Quản lý)
• agent chạy eval đa use case cho ≥3 model, bảng so sánh chi phí/chất lượng/độ trễ, khuyến nghị.

Nâng cao:
• Agent tự phát hiện model mới trên thị trường và đề xuất đánh giá, HITL duyệt tuyển chọn, memory lịch sử đánh giá, cảnh báo chi phí, báo cáo xuất PDF
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-16] AI Agent quản lý Vòng đời Dataset huấn luyện (Data Lifecycle)

### 📝 Mô tả đề tài
📍 Thực trạng: Dataset huấn luyện AI trong tập đoàn thiếu quản lý phiên bản, nguồn gốc (lineage), chất lượng & tuân thủ; khó biết dataset nào an toàn để dùng. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent quản lý vòng đời dataset: đăng ký, versioning, kiểm chất lượng (trùng lặp, thiếu, độc hại, PII), theo dõi lineage và cảnh báo dataset rủi ro/hết hạn dùng; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt phát hành dataset dùng cho production; bảo mật & phân quyền dữ liệu nhạy cảm; độ chính xác kiểm chất lượng; cảnh báo dataset vi phạm chính sách/bản quyền. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• DVC/LakeFS versioning + S3
• Presidio + LLM kiểm chất lượng/PII
• embeddings dò trùng lặp
• Langfuse
• backend FastAPI, PostgreSQL
• frontend Next.js (data catalog, lineage graph)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Data Engineer, Chủ dữ liệu)
• đăng ký & version dataset, agent kiểm chất lượng (PII/trùng/độc hại), catalog & lineage.

Nâng cao:
• Agent chấm điểm chất lượng & sẵn sàng dùng, đề xuất làm sạch, HITL duyệt phát hành, cảnh báo dataset rủi ro/hết hạn, memory theo dõi thay đổi
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-17] AI Agent Trợ lý Tuân thủ AI Governance & chính sách nội bộ

### 📝 Mô tả đề tài
📍 Thực trạng: Các dự án AI của tập đoàn phải tuân thủ chính sách nội bộ, PDPA và định hướng EU AI Act, nhưng đội sản phẩm không nắm hết yêu cầu, rủi ro pháp lý cao. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tuân thủ: nhận mô tả dự án AI, đối chiếu chính sách, phân loại mức rủi ro, checklist yêu cầu bắt buộc, phát hiện thiếu sót và sinh báo cáo tuân thủ có trích dẫn điều khoản; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL bắt buộc cho kết luận tuân thủ chính thức; bảo mật thông tin dự án; độ chính xác & chống bịa (grounded trên văn bản chính sách); cảnh báo dự án rủi ro cao cần rà soát pháp lý. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph RAG agent trên kho chính sách
• vector DB Qdrant/pgvector
• Ragas đo grounded
• LLM đa provider
• Langfuse
• backend FastAPI, PostgreSQL
• frontend Next.js (wizard đánh giá, báo cáo có citation)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Chủ dự án AI, Cán bộ tuân thủ)
• agent phân loại rủi ro & sinh checklist tuân thủ có trích dẫn chính sách.

Nâng cao:
• Agent phát hiện thiếu sót & đề xuất khắc phục, HITL duyệt kết luận, theo dõi trạng thái tuân thủ theo thời gian, cảnh báo dự án rủi ro cao, memory theo dự án
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-18] AI Agent quan sát & gỡ lỗi hệ thống Multi-Agent (AgentOps Tracing)

### 📝 Mô tả đề tài
📍 Thực trạng: Các hệ multi-agent nội bộ ngày càng phức tạp (nhiều agent, tool, vòng lặp); khi lỗi hoặc chậm, kỹ sư khó lần theo trace để tìm nguyên nhân. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent observability chuyên phân tích trace của các agent khác: dựng lại luồng thực thi, phát hiện vòng lặp vô hạn/lỗi tool/bước dư thừa, định vị điểm nghẽn và đề xuất tối ưu; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt thay đổi cấu hình agent production; bảo mật nội dung trace nhạy cảm; độ chính xác chẩn đoán nguyên nhân; cảnh báo agent tiêu tốn token/độ trễ bất thường. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• OpenTelemetry + Langfuse traces
• LLM phân tích trace
• embeddings gom cụm lỗi
• backend FastAPI, PostgreSQL/ClickHouse
• frontend Next.js (trace timeline, graph view)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Kỹ sư agent, Vận hành)
• nạp trace, agent dựng lại luồng, phát hiện lỗi/vòng lặp/nghẽn, hiển thị timeline.

Nâng cao:
• Agent phân tích nguyên nhân gốc & đề xuất tối ưu luồng, gom cụm lỗi lặp lại, HITL duyệt sửa cấu hình, memory mẫu lỗi, cảnh báo agent tốn token/độ trễ
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-19] AI Agent FinOps – quản lý ngân sách & phân bổ chi phí LLM theo đơn vị

### 📝 Mô tả đề tài
📍 Thực trạng: Chi phí LLM dùng chung khó phân bổ (chargeback) cho từng khối/đơn vị và không có cơ chế ngân sách; dễ vượt chi ngoài kiểm soát. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent FinOps theo dõi chi phí theo tenant/dự án/model, phân bổ chargeback, dự báo chi tiêu, phát hiện bất thường (tăng đột biến, lạm dụng) và đề xuất tối ưu, thực thi hạn mức ngân sách; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt hành động chặn/giới hạn khi vượt ngân sách; bảo mật dữ liệu tài chính; độ chính xác phân bổ & dự báo; cảnh báo sớm khi sắp vượt hạn mức. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• Langfuse/LiteLLM cost tracking
• mô hình dự báo (Prophet/LLM reasoning)
• phát hiện bất thường
• backend FastAPI, PostgreSQL/TimescaleDB
• frontend Next.js (dashboard chi phí, chargeback, biểu đồ)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (FinOps, Trưởng đơn vị)
• agent theo dõi & phân bổ chi phí theo đơn vị/model, dashboard chargeback & ngân sách.

Nâng cao:
• Agent dự báo chi tiêu, phát hiện bất thường/lạm dụng, đề xuất tối ưu, HITL duyệt thực thi hạn mức, cảnh báo sớm vượt ngân sách, memory theo tenant
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---

## [AIP-20] AI Agent tự động tối ưu Prompt (Prompt Optimization) theo mục tiêu

### 📝 Mô tả đề tài
📍 Thực trạng: Việc tinh chỉnh prompt để đạt chất lượng cao vừa tốn công vừa dựa cảm tính, khó tái lập giữa các đội trong tập đoàn. Khi doanh nghiệp vận hành hàng loạt ứng dụng AI ở quy mô lớn, hệ thống thường đối mặt với bài toán đánh đổi gay gắt giữa chi phí token – độ trễ – chất lượng, hiện tượng trôi lệch ngữ cảnh, lặp vô hạn giữa các tác tử và nguy cơ tấn công Prompt Injection.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự tối ưu prompt: nhận prompt gốc + bộ dữ liệu + tiêu chí, tự sinh biến thể (few-shot, viết lại, thêm ràng buộc), chạy eval, chọn phiên bản tốt nhất theo trade-off chất lượng/chi phí/độ trễ và giải thích cải tiến; đồng thời giải bài toán tối ưu hóa đa mục tiêu trên đường biên Pareto (Chi phí × Độ trễ × Chất lượng), tự động phát hiện điểm suy thoái hoặc lỗ hổng bảo mật từ dữ liệu trace thực tế và kiểm chứng tự động qua cổng kiểm thử hồi quy.

🔒 Ràng buộc: HITL duyệt prompt tối ưu trước khi áp dụng production; bảo mật dữ liệu ví dụ; độ chính xác eval khi so sánh biến thể; kiểm soát chi phí vòng lặp tối ưu. Mọi thay đổi cấu hình định tuyến, cập nhật prompt/model hoặc quy tắc chặn an toàn phải được kiểm định định lượng trên tập dữ liệu giữ riêng (held-out regression gate) trước khi áp dụng.

### 🛠️ Tech Stack
• LangGraph
• DSPy/APE prompt optimization
• DeepEval/Promptfoo eval
• LLM đa provider qua LiteLLM
• embeddings
• Langfuse
• backend FastAPI, PostgreSQL
• frontend Next.js (playground, so sánh biến thể, biểu đồ Pareto)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu & benchmark hạ tầng AI: RouterBench / LMSYS Chatbot Arena (định tuyến model), RAGBench / BEIR (truy hồi), BIPIA / HarmBench / Garak (an toàn & chống prompt injection), TRAIL (gỡ lỗi multi-agent) và chuẩn OpenTelemetry GenAI.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Prompt Engineer, Reviewer)
• agent sinh & eval các biến thể prompt trên bộ dữ liệu, chọn phiên bản tốt nhất, giải thích cải tiến.

Nâng cao:
• Tối ưu đa mục tiêu (chất lượng/chi phí/độ trễ) với đường Pareto, HITL duyệt áp dụng, dừng khi hội tụ để tiết kiệm, memory lưu chiến lược, cảnh báo chi phí tối ưu
• Xây dựng cơ chế đánh giá và mô phỏng định lượng trên dữ liệu trace thực tế (tối ưu hóa chi phí – chất lượng – độ trễ) kèm khả năng tự động phát hiện và khoanh vùng điểm lỗi của hệ thống AI.

---
