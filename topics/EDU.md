# Lĩnh vực: EDU - A · AI Giáo dục B · AI Nghiên cứu C · AI Vận hành D · Quản trị & Năng lực

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `EDU-01` | [Trợ lý học tập cá nhân: Trợ lý học tập AI đồng hành theo chu trình Plan-Do-Reflect](#edu-01) |
| `EDU-02` | [Trợ lý giảng dạy: Trợ lý giảng dạy AI tổng hợp vướng mắc lớp học realtime](#edu-02) |
| `EDU-03` | [SimFeedback AI: Trợ lý phản hồi cá nhân hóa cho học nhóm tại Trung tâm Mô phỏng](#edu-03) |
| `EDU-04` | [Kho tri thức hỗ trợ học thuật: Bộ trợ lý học thuật & học tập AI cho Trung tâm hỗ trợ học thuật](#edu-04) |
| `EDU-05` | [AI Literacy Coach: Ứng dụng phổ cập năng lực dùng AI cá nhân hóa cho toàn trường](#edu-05) |
| `EDU-06` | [PathPlanner AI: Agent xây lộ trình học cá nhân hóa theo mục tiêu và năng lực](#edu-06) |
| `EDU-07` | [PeerBridge AI: Nền tảng hỗ trợ học ngang hàng (peer support) do AI điều phối](#edu-07) |
| `EDU-08` | [ClassPulse AI: Dashboard phát hiện realtime điểm cả lớp đang gặp khó](#edu-08) |
| `EDU-09` | [LitReview Agent: Trợ lý AI tổng quan tài liệu và phân tích dữ liệu nghiên cứu](#edu-09) |
| `EDU-10` | [GrantFinder AI: Trợ lý xây đề xuất nghiên cứu và rà soát nguồn tài trợ](#edu-10) |
| `EDU-11` | [ReviewSynth AI: Agent tổng hợp phản biện và soạn báo cáo tiến độ nghiên cứu](#edu-11) |
| `EDU-12` | [Trợ lý tuyển sinh: Trợ lý tuyển sinh AI tư vấn và tăng gắn kết ứng viên](#edu-12) |
| `EDU-13` | [AdmitScreen AI: Agent sơ loại hồ sơ tuyển sinh và đề xuất học bổng (người phê duyệt cuối)](#edu-13) |
| `EDU-14` | [Campus 24/7: Trợ lý ảo AI cho sinh viên giải đáp và xử lý yêu cầu](#edu-14) |
| `EDU-15` | [PolicyMate AI: Trợ lý ảo tra cứu quy định quy chế cho lãnh đạo và cán bộ giảng viên](#edu-15) |
| `EDU-16` | [TalentScreen AI: Trợ lý tuyển dụng và nhân sự sàng lọc CV (agent đề xuất, HR quyết định)](#edu-16) |
| `EDU-17` | [Trợ lý nghề nghiệp: Agent tối ưu CV và phỏng vấn thử cho sinh viên](#edu-17) |
| `EDU-18` | [AI Faculty Academy: Nền tảng đào tạo năng lực AI cho giảng viên, TA và cán bộ](#edu-18) |
| `EDU-19` | [AI Competency Compass: Công cụ đánh giá và bản đồ hóa khung năng lực AI toàn trường](#edu-19) |
| `EDU-20` | [AI Governance Monitor: Trợ lý giám sát tuân thủ và chất lượng các sản phẩm AI của trường](#edu-20) |

---

## [EDU-01] Trợ lý học tập cá nhân: Trợ lý học tập AI đồng hành theo chu trình Plan-Do-Reflect

### 📝 Mô tả đề tài
📍 Thực trạng: Sinh viên trường đại học học trên Canvas LMS với nhiều môn, deadline dày đặc; phần lớn chỉ 'chạy theo bài' mà thiếu một người đồng hành giúp lập kế hoạch, theo dõi tiến độ và tự nhìn lại việc học của mình. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng 'learning companion' AI đồng hành từng SV theo chu trình Plan (đặt mục tiêu tuần, chia nhỏ nhiệm vụ từ syllabus/assignment) → Do (nhắc việc, gợi ý tài nguyên môn học có trích nguồn) → Reflect (đối thoại phản tư sau mỗi mốc, tự đánh giá điểm mạnh/yếu), giúp tăng tỷ lệ nộp bài đúng hạn và cải thiện tiến độ; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: AI chỉ hỗ trợ tư duy và tổ chức việc học, KHÔNG làm hộ bài tập tính điểm (liêm chính học thuật, có cơ chế chống lạm dụng khi SV yêu cầu 'giải giúp'); dữ liệu học tập của SV được phân quyền và ẩn danh khi tổng hợp (FERPA-mindset); gợi ý tài nguyên phải grounded trên tài liệu môn học và có trích nguồn (chống bịa); có HITL để giảng viên xem tổng quan tiến độ lớp; đo được KPI tỷ lệ nộp đúng hạn và mức cải thiện tiến độ; kiểm soát chi phí/độ trễ token cho quy mô 1000 SV dùng đồng thời.

### 🛠️ Tech Stack
• LLM (GPT-4o-mini/Claude Haiku cho tác vụ thường, model lớn cho phản tư)
• RAG với Qdrant lưu embedding syllabus/tài liệu môn + reranker (bge-reranker/Cohere Rerank)
• tích hợp Canvas LMS qua REST API + LTI 1.3 để lấy assignment, deadline, submission
• agent lập kế hoạch bằng LangGraph (planner + reflector node) có memory dài hạn (Postgres)
• guardrails (NeMo Guardrails/Llama Guard) chặn yêu cầu làm hộ bài
• eval bằng RAGAS + LLM-as-Judge cho chất lượng phản tư
• backend FastAPI
• frontend Next.js (React)
• deploy Docker + cloud (Render/GCP Cloud Run), caching Redis giảm chi phí.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy online, đăng nhập ≥2 vai trò (sinh viên/giảng viên)
• SV tạo mục tiêu tuần, AI chia nhỏ nhiệm vụ từ syllabus và nhắc deadline (đọc từ Canvas hoặc dữ liệu mô phỏng), có phiên phản tư cuối tuần
• giảng viên xem dashboard tiến độ tổng quan (ẩn danh)
• metric cơ bản: tỷ lệ nộp đúng hạn trước/sau khi dùng.

Nâng cao:
• Multi-agent Plan-Do-Reflect với memory cá nhân hóa, tích hợp Canvas LMS thật qua LTI
• eval pipeline RAGAS đối chiếu KPI (1000 SV đồng thời qua load test, mức cải thiện tiến độ)
• dashboard giảng viên có cảnh báo SV nguy cơ trễ
• guardrails liêm chính học thuật + tối ưu chi phí/độ trễ bằng caching và routing model theo độ khó
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-02] Trợ lý giảng dạy: Trợ lý giảng dạy AI tổng hợp vướng mắc lớp học realtime

### 📝 Mô tả đề tài
📍 Thực trạng: Giảng viên trường đại học khó nắm nhanh cả lớp đang gặp khó ở điểm nào — phản hồi rải rác qua email, diễn đàn Canvas, quiz; đến khi nhận ra thì đã trễ. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng trợ lý giảng dạy tổng hợp vướng mắc và phản hồi của SV theo thời gian thực (câu hỏi diễn đàn, kết quả quiz, mức độ hoàn thành bài), phát hiện 'điểm nghẽn' chung của lớp, gợi ý giải pháp và bài tập ôn tập bám chuẩn đầu ra (learning outcomes) — giảng viên toàn quyền quyết định dùng hay không; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: AI chỉ TƯ VẤN, giảng viên và TA giữ quyền quyết định chuyên môn cuối (HITL bắt buộc); dữ liệu SV được ẩn danh khi phân tích ở cấp lớp, phân quyền chặt (chỉ GV môn đó xem); gợi ý bài tập phải grounded trên tài liệu môn + learning outcomes có trích nguồn (chống bịa); đo độ chính xác của phát hiện điểm nghẽn và độ hữu ích của gợi ý; chịu tải 2500 SV đồng thời với chi phí/độ trễ hợp lý.

### 🛠️ Tech Stack
• LLM đa tầng
• RAG với pgvector lưu tài liệu môn + learning outcomes + reranker
• pipeline gom dữ liệu Canvas (discussion, quiz, gradebook) qua Canvas API, ẩn danh bằng hashing
• agent phân cụm vướng mắc (embedding clustering + LLM tóm tắt) trên LangGraph
• sinh bài tập với template bám Bloom taxonomy
• eval DeepEval + LLM-as-Judge so gợi ý với đáp án chuẩn của GV
• guardrails phân quyền
• backend FastAPI + Celery cho xử lý nền
• frontend React (Next.js) dashboard realtime
• deploy Docker + Kubernetes/Cloud Run, autoscaling.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, đăng nhập ≥2 vai trò (giảng viên/TA)
• nạp dữ liệu quiz + câu hỏi diễn đàn (mô phỏng), AI phân cụm và trình bày 'top 3 điểm lớp đang khó' kèm gợi ý bài ôn
• GV duyệt/bác bỏ từng gợi ý (HITL)
• metric cơ bản: độ chính xác phát hiện điểm nghẽn so nhãn GV.

Nâng cao:
• Tích hợp Canvas API realtime, sinh bài tập bám learning outcomes tự động
• eval pipeline đối chiếu KPI (2500 SV đồng thời, độ chính xác & hiệu quả gợi ý)
• dashboard nhiệt độ lớp theo thời gian
• guardrails ẩn danh + phân quyền + tối ưu chi phí bằng batch xử lý
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-03] SimFeedback AI: Trợ lý phản hồi cá nhân hóa cho học nhóm tại Trung tâm Mô phỏng

### 📝 Mô tả đề tài
📍 Thực trạng: Tại Simulation Center (đào tạo y khoa/kỹ năng thực hành), SV học theo nhóm nhưng giảng viên khó đưa nhận xét cá nhân hóa cho từng người trong buổi mô phỏng đông; phản hồi thường chung chung. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng trợ lý AI phân tích vai trò và hành động của từng SV trong buổi học nhóm (ghi chú quan sát, transcript trao đổi, checklist thao tác) rồi sinh nhận xét cá nhân hóa cho từng SV, hướng cải thiện cụ thể — mục tiêu độ tương đồng ≥80% với đánh giá của giảng viên; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: AI chỉ GỢI Ý nhận xét, giảng viên rà soát và phê duyệt trước khi gửi SV (HITL bắt buộc); đo độ tương đồng phản hồi AI vs GV (KPI ≥80%); dữ liệu buổi mô phỏng nhạy cảm phải phân quyền, ẩn danh khi phân tích tổng hợp; nhận xét grounded trên checklist/rubric chuẩn của buổi học (chống bịa); tránh thiên vị giữa các SV; kiểm soát chi phí xử lý transcript dài.

### 🛠️ Tech Stack
• LLM (Claude/GPT-4o cho phản hồi chất lượng)
• RAG với Qdrant lưu rubric/checklist buổi mô phỏng + reranker
• ASR (Whisper) chuyển transcript nếu có audio
• agent gán hành động theo vai trò từng SV (LangGraph)
• eval: đo cosine similarity + LLM-as-Judge + rubric scoring so với nhãn GV, báo cáo độ tương đồng
• guardrails chống nhận xét thiên vị/xúc phạm
• backend FastAPI
• frontend React với giao diện duyệt-sửa phản hồi
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (giảng viên/SV)
• nhập ghi chú buổi mô phỏng + rubric, AI sinh nhận xét riêng cho từng SV
• GV chỉnh sửa và phê duyệt (HITL)
• metric cơ bản: độ tương đồng phản hồi AI vs bản GV chỉnh sửa.

Nâng cao:
• Xử lý transcript audio, gán hành động theo vai trò tự động
• eval pipeline đo similarity ≥80% trên tập kiểm chứng
• dashboard theo dõi tiến bộ từng SV qua nhiều buổi
• guardrails chống thiên vị + tối ưu chi phí xử lý transcript dài bằng chunking
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-04] Kho tri thức hỗ trợ học thuật: Bộ trợ lý học thuật & học tập AI cho Trung tâm hỗ trợ học thuật

### 📝 Mô tả đề tài
📍 Thực trạng: Trung tâm hỗ trợ học thuật có kho tài liệu học thuật (giáo trình, slide, đề cương, tài liệu tham khảo) lớn nhưng phân tán; SV và giảng viên mất thời gian tìm và tổng hợp kiến thức. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng bộ giải pháp gồm Trợ lý Học thuật (Academic Assistant - hỏi đáp chuyên sâu theo môn), Trợ lý Học tập (Learning Assistant - giải thích khái niệm, gợi ý lộ trình ôn) và Trung tâm Tri thức (Knowledge Hub - tìm kiếm và tổng hợp tài liệu), đạt độ chính xác câu trả lời ≥80% trên tập dữ liệu học thuật kiểm chứng; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Câu trả lời phải grounded trên kho tài liệu Trung tâm hỗ trợ học thuật, có trích nguồn (chống bịa); đo độ chính xác ≥80% trên bộ test có nhãn (KPI); AI hỗ trợ hiểu bài, KHÔNG cung cấp đáp án bài tập tính điểm (liêm chính học thuật); phân quyền tài liệu theo vai trò/môn; HITL cho giảng viên phê duyệt tài liệu đưa vào Hub; kiểm soát chi phí/độ trễ khi kho tài liệu lớn.

### 🛠️ Tech Stack
• LLM
• RAG nâng cao với pgvector/Qdrant, hybrid search (BM25 + vector) + reranker
• ingestion pipeline xử lý PDF/slide (OCR khi cần)
• citation tracking gắn nguồn từng câu
• multi-assistant routing (một agent điều phối 3 trợ lý con) bằng LangGraph
• eval RAGAS (faithfulness, answer relevancy, context precision) trên bộ test có nhãn
• guardrails chống lộ đáp án bài tập
• backend FastAPI
• frontend Next.js với 3 giao diện trợ lý
• deploy Docker + cloud, caching.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (SV/giảng viên)
• Academic + Learning Assistant hỏi đáp có trích nguồn trên kho tài liệu mẫu
• Knowledge Hub tìm kiếm tài liệu
• metric cơ bản: độ chính xác trên ~30 câu hỏi test có nhãn.

Nâng cao:
• Đủ 3 trợ lý với router thông minh, hybrid search + reranker
• eval RAGAS đạt độ chính xác ≥80% trên tập kiểm chứng
• dashboard cho GV quản lý tài liệu Hub + duyệt nội dung
• guardrails liêm chính + tối ưu chi phí/độ trễ bằng caching và semantic dedup
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-05] AI Literacy Coach: Ứng dụng phổ cập năng lực dùng AI cá nhân hóa cho toàn trường

### 📝 Mô tả đề tài
📍 Thực trạng: trường đại học muốn phổ cập năng lực dùng AI cho mọi đối tượng (giảng viên, sinh viên, nghiên cứu viên, quản lý, cán bộ phòng ban) nhưng nhu cầu và nền tảng mỗi nhóm rất khác nhau, đào tạo đại trà không hiệu quả. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng ứng dụng học năng lực AI cá nhân hóa theo vai trò và trình độ — chẩn đoán năng lực đầu vào, đề xuất lộ trình micro-learning (prompt engineering, dùng AI có đạo đức, phát hiện bịa/thiên vị), bài thực hành tương tác với AI thật và đánh giá tiến bộ; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Nội dung học grounded trên khung năng lực AI của trường có trích nguồn (chống bịa); dạy chính SV/CBNV cách nhận diện thiên vị và giới hạn của AI; dữ liệu tiến độ học cá nhân phân quyền, ẩn danh khi thống kê; HITL cho quản trị viên duyệt nội dung lộ trình; đo độ chính xác chẩn đoán năng lực và mức cải thiện; kiểm soát chi phí ở quy mô toàn trường.

### 🛠️ Tech Stack
• LLM
• RAG với Qdrant lưu khung năng lực + tài liệu học AI + reranker
• adaptive learning engine (bandit/rule-based) đề xuất bài theo trình độ
• agent chấm bài thực hành prompt (LangGraph)
• eval LLM-as-Judge cho bài thực hành + đo delta năng lực
• guardrails
• backend FastAPI
• frontend Next.js đa persona
• deploy Docker + cloud, phân tích tiến độ bằng dashboard.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (người học/quản trị nội dung)
• bài test chẩn đoán năng lực + lộ trình micro-learning theo persona + ≥1 bài thực hành AI được AI chấm
• metric cơ bản: điểm trước/sau.

Nâng cao:
• Adaptive path đa persona (GV/SV/quản lý/phòng ban), thư viện bài thực hành có eval tự động
• dashboard quản trị theo dõi độ phủ và mức cải thiện toàn trường
• guardrails + tối ưu chi phí bằng caching nội dung học chung
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-06] PathPlanner AI: Agent xây lộ trình học cá nhân hóa theo mục tiêu và năng lực

### 📝 Mô tả đề tài
📍 Thực trạng: SV trường đại học có mục tiêu nghề nghiệp khác nhau (nghiên cứu, startup, đi làm) nhưng chọn môn và lộ trình học chủ yếu theo cảm tính hoặc lời khuyên rời rạc, khó tối ưu theo năng lực và tiến độ thực tế. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent lập lộ trình học cá nhân hóa — nhận mục tiêu, năng lực hiện tại (điểm, kỹ năng), ràng buộc (tín chỉ, tiên quyết) rồi đề xuất lộ trình môn học/kỹ năng theo học kỳ, cập nhật động khi tiến độ thay đổi, giải thích lý do từng đề xuất; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Đề xuất grounded trên chương trình đào tạo/điều kiện tiên quyết thật, có trích nguồn (chống bịa); cố vấn học tập (advisor) phê duyệt lộ trình trước khi SV theo (HITL); dữ liệu điểm SV bảo mật, phân quyền (FERPA-mindset); tránh thiên vị đẩy SV theo hướng cứng nhắc; giải thích được từng gợi ý; kiểm soát chi phí/độ trễ khi tính toán lộ trình phức tạp.

### 🛠️ Tech Stack
• LLM
• RAG với pgvector lưu catalog môn học + điều kiện tiên quyết + reranker
• agent planning (LangGraph) kết hợp constraint solver (OR-Tools) cho ràng buộc tín chỉ/tiên quyết
• memory hồ sơ SV (Postgres)
• eval: đo tính hợp lệ lộ trình (thỏa ràng buộc) + LLM-as-Judge chất lượng giải thích
• guardrails
• backend FastAPI
• frontend Next.js hiển thị lộ trình dạng timeline
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (SV/cố vấn học tập)
• nhập mục tiêu + điểm, agent đề xuất lộ trình học kỳ có giải thích + kiểm tra ràng buộc tiên quyết
• cố vấn duyệt (HITL)
• metric cơ bản: tỷ lệ lộ trình hợp lệ.

Nâng cao:
• Cập nhật động khi điểm thay đổi, đối chiếu nhiều mục tiêu nghề
• eval pipeline đo tính hợp lệ + chất lượng giải thích
• dashboard cố vấn quản lý nhiều SV
• guardrails chống thiên vị + tối ưu chi phí bằng cache constraint
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-07] PeerBridge AI: Nền tảng hỗ trợ học ngang hàng (peer support) do AI điều phối

### 📝 Mô tả đề tài
📍 Thực trạng: SV học tốt nhất khi trao đổi với bạn cùng lớp, nhưng việc ghép cặp/nhóm học phù hợp và giữ chất lượng trao đổi (không biến thành chép bài) rất khó tự tổ chức. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng AI-mediated peer support — ghép SV cần giúp với SV có thể giúp (theo điểm mạnh/yếu từng chủ đề), gợi ý câu hỏi dẫn dắt để người giúp không đưa thẳng đáp án, tóm tắt và kiểm duyệt phiên trao đổi để đảm bảo học thật; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: AI hướng người hỗ trợ dùng phương pháp Socratic, KHÔNG khuyến khích đưa đáp án bài tập tính điểm (liêm chính học thuật, chống lạm dụng); dữ liệu điểm mạnh/yếu SV ẩn danh khi ghép, phân quyền (FERPA-mindset); giảng viên giám sát và can thiệp khi cần (HITL); tránh thiên vị trong ghép cặp; kiểm soát chi phí điều phối realtime.

### 🛠️ Tech Stack
• LLM
• RAG với Qdrant lưu tài liệu môn để gợi ý câu hỏi dẫn dắt + reranker
• matching engine (embedding kỹ năng + thuật toán ghép cặp)
• agent kiểm duyệt hội thoại phát hiện 'đưa đáp án' (LangGraph + classifier)
• eval: đo chất lượng ghép cặp + tỷ lệ phiên tuân thủ Socratic (LLM-as-Judge)
• guardrails liêm chính
• backend FastAPI + WebSocket realtime
• frontend Next.js chat
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (SV/giảng viên giám sát)
• ghép cặp theo chủ đề, phòng chat có AI gợi ý câu hỏi dẫn dắt
• GV xem log kiểm duyệt (HITL)
• metric cơ bản: tỷ lệ phiên không lộ đáp án.

Nâng cao:
• Matching tối ưu đa tiêu chí, kiểm duyệt realtime cảnh báo lệch liêm chính
• eval pipeline đo chất lượng ghép + tuân thủ Socratic
• dashboard GV theo dõi mạng lưới peer support
• guardrails + tối ưu chi phí bằng model nhỏ cho kiểm duyệt
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-08] ClassPulse AI: Dashboard phát hiện realtime điểm cả lớp đang gặp khó

### 📝 Mô tả đề tài
📍 Thực trạng: Trong lớp đông, giảng viên không thể biết ngay khái niệm nào cả lớp đang mắc — thường phải chờ kết quả bài kiểm tra mới phát hiện, khi đó đã lỡ nhịp dạy. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng dashboard AI phân tích realtime tín hiệu học tập (câu hỏi trong buổi, poll/quiz nhanh, mức tương tác tài liệu, từ khóa SV hay hỏi lại) để phát hiện và trực quan hóa 'điểm nóng khó khăn' của lớp theo thời gian thực, gợi ý can thiệp ngay trong buổi; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Phân tích ẩn danh ở cấp lớp, không lộ danh tính SV nào đang yếu (FERPA-mindset, phân quyền); phát hiện phải grounded trên nội dung buổi học/khái niệm môn (chống bịa); AI chỉ cảnh báo và gợi ý, GV quyết định can thiệp (HITL); đo độ chính xác phát hiện điểm khó so nhận định GV; độ trễ thấp để dùng realtime; chi phí hợp lý.

### 🛠️ Tech Stack
• LLM cho tóm tắt/gán khái niệm
• embedding clustering câu hỏi SV
• RAG với pgvector map câu hỏi về khái niệm trong syllabus + reranker
• stream processing (WebSocket + queue) cho realtime
• eval: đo precision/recall phát hiện điểm khó so nhãn GV
• guardrails ẩn danh
• backend FastAPI + Redis stream
• frontend React dashboard heatmap realtime
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (giảng viên/TA)
• nhận luồng câu hỏi + kết quả poll (mô phỏng), hiển thị top khái niệm khó dạng heatmap
• GV xem gợi ý can thiệp (HITL)
• metric cơ bản: độ chính xác phát hiện so nhãn.

Nâng cao:
• Realtime stream với độ trễ thấp, gán khái niệm tự động về syllabus
• eval precision/recall trên buổi mẫu
• dashboard xu hướng qua nhiều buổi + cảnh báo
• guardrails ẩn danh + tối ưu chi phí bằng model nhỏ cho phân loại nhanh
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-09] LitReview Agent: Trợ lý AI tổng quan tài liệu và phân tích dữ liệu nghiên cứu

### 📝 Mô tả đề tài
📍 Thực trạng: Nghiên cứu viên và SV nghiên cứu trường đại học tốn nhiều tuần để làm tổng quan tài liệu (literature review) và bước đầu phân tích dữ liệu; công việc lặp lại, dễ sót nguồn quan trọng. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng trợ lý AI hỗ trợ tổng quan tài liệu (tìm, sàng lọc, tóm tắt, tổng hợp chủ đề, phát hiện khoảng trống nghiên cứu, dựng bảng so sánh) và phân tích dữ liệu ban đầu (gợi ý phương pháp, sinh code phân tích, diễn giải kết quả) — mục tiêu giảm ≥50% thời gian ra bản dự thảo đầu tiên với ≥80% độ chính xác thông tin; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Mọi khẳng định phải grounded trên bài báo thật có trích dẫn đầy đủ (chống bịa nguồn — rủi ro lớn nhất của LLM trong nghiên cứu); đo độ chính xác thông tin ≥80% và mức giảm thời gian (KPI); nghiên cứu viên rà soát và chịu trách nhiệm nội dung cuối (HITL); cảnh báo giới hạn khi dữ liệu không đủ; kiểm soát chi phí xử lý nhiều tài liệu dài.

### 🛠️ Tech Stack
• LLM (model mạnh cho tổng hợp)
• RAG với Qdrant lưu embedding bài báo + reranker
• tích hợp API học thuật (Semantic Scholar/OpenAlex/arXiv) để lấy metadata + trích dẫn
• agent multi-step (LangGraph): search → screen → summarize → synthesize
• code interpreter sandbox cho phân tích dữ liệu
• eval RAGAS (faithfulness, citation accuracy) đo độ chính xác + đo thời gian tiết kiệm
• guardrails chống bịa DOI/trích dẫn
• backend FastAPI
• frontend Next.js
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Cơ sở dữ liệu học thuật mở OpenAlex, Semantic Scholar (S2ORC), Crossref, arXiv API và bộ benchmark QASPER / SciFact / LitQA2.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (nghiên cứu viên/reviewer)
• nhập chủ đề, agent tìm + tóm tắt + tổng hợp tài liệu có trích dẫn kiểm chứng được
• người dùng rà soát (HITL)
• metric cơ bản: độ chính xác trích dẫn trên tập mẫu.

Nâng cao:
• Pipeline đầy đủ search-screen-synthesize + phân tích dữ liệu với code sandbox
• eval RAGAS đạt ≥80% + đo giảm ≥50% thời gian dự thảo
• dashboard quản lý dự án review nhiều đề tài
• guardrails chống bịa trích dẫn + tối ưu chi phí bằng map-reduce summarization
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-10] GrantFinder AI: Trợ lý xây đề xuất nghiên cứu và rà soát nguồn tài trợ

### 📝 Mô tả đề tài
📍 Thực trạng: Nhà nghiên cứu trường đại học bỏ lỡ cơ hội tài trợ (grant) vì thông tin phân tán và mất thời gian soạn đề xuất khớp yêu cầu từng quỹ. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng trợ lý AI rà soát và ghép nguồn tài trợ phù hợp với hướng nghiên cứu của nhà khoa học (theo lĩnh vực, quy mô, điều kiện đủ), hỗ trợ dựng khung đề xuất nghiên cứu bám yêu cầu từng quỹ (mục tiêu, phương pháp, ngân sách, tác động), và kiểm tra độ khớp với tiêu chí xét duyệt; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Thông tin quỹ và điều kiện phải grounded trên tài liệu call-for-proposal thật, có trích nguồn (chống bịa — không được bịa deadline/điều kiện); đo độ chính xác thông tin ≥80% và giảm ≥50% thời gian ra bản nháp; nhà nghiên cứu phê duyệt và chịu trách nhiệm nội dung nộp (HITL); tránh thiên vị ưu tiên quỹ; cảnh báo khi thiếu thông tin; kiểm soát chi phí.

### 🛠️ Tech Stack
• LLM
• RAG với pgvector lưu database quỹ tài trợ + tiêu chí + reranker
• matching agent ghép hướng nghiên cứu với quỹ (embedding + rule)
• agent soạn thảo theo template từng quỹ (LangGraph)
• eval: đo độ chính xác thông tin quỹ (faithfulness) + đo thời gian tiết kiệm
• guardrails chống bịa deadline/điều kiện
• backend FastAPI
• frontend Next.js
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Cơ sở dữ liệu học thuật mở OpenAlex, Semantic Scholar (S2ORC), Crossref, arXiv API và bộ benchmark QASPER / SciFact / LitQA2.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (nghiên cứu viên/quản lý phòng KHCN)
• nhập hướng nghiên cứu, AI đề xuất quỹ phù hợp có trích nguồn + khung đề xuất nháp
• người dùng duyệt (HITL)
• metric cơ bản: độ chính xác thông tin quỹ.

Nâng cao:
• Matching đa tiêu chí + kiểm tra độ khớp tiêu chí xét duyệt, soạn đề xuất theo template từng quỹ
• eval đạt ≥80% chính xác + giảm ≥50% thời gian
• dashboard theo dõi cơ hội tài trợ và deadline
• guardrails chống bịa + tối ưu chi phí
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-11] ReviewSynth AI: Agent tổng hợp phản biện và soạn báo cáo tiến độ nghiên cứu

### 📝 Mô tả đề tài
📍 Thực trạng: Quá trình xét duyệt đề xuất và nghiệm thu đề tài ở trường đại học tạo ra nhiều ý kiến phản biện (peer review) rời rạc, và nhóm nghiên cứu tốn công soạn báo cáo tiến độ/nghiệm thu lặp lại. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent (1) tóm tắt đề xuất để hội đồng xét duyệt nhanh, (2) tổng hợp nhiều ý kiến phản biện thành bản đánh giá thống nhất nêu điểm mạnh/yếu/mâu thuẫn giữa các reviewer, (3) hỗ trợ soạn báo cáo tiến độ và nghiệm thu bám mẫu — giảm ≥50% thời gian ra bản dự thảo đầu, ≥80% độ chính xác; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Tổng hợp phải grounded trên nội dung phản biện/đề xuất thật, trích rõ ý của từng reviewer (chống bịa, không tự thêm nhận định); đo độ chính xác ≥80% và giảm thời gian ≥50% (KPI); hội đồng/chủ nhiệm đề tài phê duyệt bản cuối (HITL); ẩn danh reviewer khi tổng hợp, phân quyền dữ liệu nhạy cảm; tránh thiên vị nghiêng về một phản biện; kiểm soát chi phí.

### 🛠️ Tech Stack
• LLM
• RAG với Qdrant lưu đề xuất + phản biện + mẫu báo cáo + reranker
• agent multi-step (LangGraph): trích ý → gom theo tiêu chí → phát hiện mâu thuẫn → tổng hợp
• eval: đo faithfulness + độ bao phủ ý phản biện (LLM-as-Judge) + đo thời gian
• guardrails ẩn danh + chống thêm nhận định
• backend FastAPI
• frontend Next.js với chế độ so sánh phản biện
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Cơ sở dữ liệu học thuật mở OpenAlex, Semantic Scholar (S2ORC), Crossref, arXiv API và bộ benchmark QASPER / SciFact / LitQA2.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (thư ký hội đồng/chủ nhiệm đề tài)
• nhập nhiều phản biện, AI tổng hợp bản đánh giá nêu đồng thuận/mâu thuẫn có trích ý từng reviewer
• hội đồng duyệt (HITL)
• metric cơ bản: độ bao phủ ý phản biện.

Nâng cao:
• Đủ 3 chức năng (tóm tắt xét duyệt + tổng hợp phản biện + soạn báo cáo tiến độ/nghiệm thu)
• eval đạt ≥80% + giảm ≥50% thời gian
• dashboard quản lý vòng xét duyệt
• guardrails ẩn danh + chống thiên vị + tối ưu chi phí
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-12] Trợ lý tuyển sinh: Trợ lý tuyển sinh AI tư vấn và tăng gắn kết ứng viên

### 📝 Mô tả đề tài
📍 Thực trạng: Phòng tuyển sinh trường đại học nhận rất nhiều câu hỏi lặp về quy trình, ngành, học phí, học bổng qua nhiều kênh; cán bộ quá tải, ứng viên chờ lâu và dễ bỏ cuộc. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng chatbot tuyển sinh tư vấn ứng viên 24/7, hướng dẫn quy trình nộp hồ sơ, cá nhân hóa theo hồ sơ/ngành quan tâm, chủ động dẫn dắt để tăng applicant engagement — mục tiêu trả lời ≥70% câu hỏi với độ chính xác ≥85%, giảm ≥50% câu hỏi trực tiếp cho cán bộ; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Trả lời grounded trên quy chế/thông tin tuyển sinh chính thức có trích nguồn (chống bịa — không được bịa điều kiện/hạn nộp/học phí); đo tỷ lệ trả lời được ≥70% và độ chính xác ≥85% (KPI); handover cho cán bộ khi câu hỏi vượt phạm vi/nhạy cảm (HITL); không thu thập dữ liệu cá nhân ứng viên quá mức, bảo mật thông tin; tránh thiên vị/hứa hẹn sai; kiểm soát chi phí/độ trễ ở mùa cao điểm.

### 🛠️ Tech Stack
• LLM
• RAG với pgvector lưu tài liệu tuyển sinh chính thức + reranker
• intent detection + fallback/handover logic
• multi-turn memory theo hồ sơ ứng viên
• eval: đo answer rate + accuracy (LLM-as-Judge + bộ test có nhãn)
• guardrails chống bịa cam kết + phát hiện câu nhạy cảm
• backend FastAPI
• frontend Next.js widget chat
• deploy Docker + cloud, caching câu hỏi thường gặp.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (ứng viên/cán bộ tuyển sinh)
• chatbot trả lời câu hỏi tuyển sinh có trích nguồn, handover khi không chắc
• cán bộ xem hàng chờ handover (HITL)
• metric cơ bản: answer rate + accuracy trên bộ test.

Nâng cao:
• Cá nhân hóa theo hồ sơ + chủ động nurture ứng viên
• eval pipeline đạt KPI (≥70% trả lời, ≥85% chính xác, giảm ≥50% câu hỏi cho cán bộ)
• dashboard engagement ứng viên
• guardrails chống bịa cam kết + tối ưu chi phí bằng caching
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-13] AdmitScreen AI: Agent sơ loại hồ sơ tuyển sinh và đề xuất học bổng (người phê duyệt cuối)

### 📝 Mô tả đề tài
📍 Thực trạng: Đánh giá hồ sơ tuyển sinh (đơn, bảng điểm, bài luận, điểm thi) theo nhiều tiêu chí là công việc nặng và dễ thiếu nhất quán giữa các cán bộ. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự động đọc hồ sơ ứng viên, chấm theo bộ tiêu chí (rubric) minh bạch, đề xuất Đạt/Không đạt kèm lý do và gợi ý mức học bổng phù hợp — nhưng chỉ ở mức ĐỀ XUẤT, cán bộ tuyển sinh phê duyệt cuối; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Quyết định đạt/không đạt và học bổng BẮT BUỘC có người phê duyệt, agent chỉ đề xuất kèm lý do minh bạch (HITL nghiêm ngặt); giảm thiên vị là yêu cầu tối quan trọng — công bằng theo giới/vùng miền/trường, giải thích được từng điểm số, có audit log; dữ liệu ứng viên bảo mật cao, phân quyền, ẩn danh khi phân tích thống kê; đánh giá grounded trên rubric + nội dung hồ sơ thật, không suy diễn ngoài dữ liệu (chống bịa); đo độ tương đồng với đánh giá của cán bộ; kiểm soát chi phí.

### 🛠️ Tech Stack
• LLM (model mạnh cho đọc luận)
• RAG với Qdrant lưu rubric + tiêu chí học bổng + reranker
• document parsing (bảng điểm/luận)
• scoring agent (LangGraph) chấm từng tiêu chí có giải thích
• bias/fairness eval (đo chênh lệch điểm theo nhóm nhân khẩu ẩn danh) + đo similarity với nhãn cán bộ
• guardrails chống dùng thuộc tính nhạy cảm
• audit log
• backend FastAPI
• frontend Next.js giao diện review có giải thích
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (cán bộ tuyển sinh/quản lý)
• agent chấm hồ sơ mô phỏng theo rubric, đề xuất Đạt/Không + lý do
• cán bộ phê duyệt/điều chỉnh (HITL)
• metric cơ bản: độ tương đồng với nhãn cán bộ.

Nâng cao:
• Đề xuất học bổng + fairness dashboard đo thiên vị theo nhóm ẩn danh
• eval pipeline đo độ chính xác/độ tương đồng + kiểm định công bằng
• audit log đầy đủ + giải thích từng tiêu chí
• guardrails chống thiên vị nghiêm ngặt + tối ưu chi phí
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-14] Campus 24/7: Trợ lý ảo AI cho sinh viên giải đáp và xử lý yêu cầu

### 📝 Mô tả đề tài
📍 Thực trạng: SV trường đại học cần tra thông tin (lịch học, quy định, thủ tục, dịch vụ) và gửi yêu cầu (xin giấy tờ, đặt phòng, báo sự cố) mọi lúc, nhưng phòng ban chỉ hỗ trợ giờ hành chính. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng trợ lý ảo 24/7 giải đáp truy vấn thông tin, nhắc lịch học/lịch cá nhân, tiếp nhận và xử lý (tạo ticket/định tuyến) yêu cầu của SV, với cơ chế handover cho người thật ở ca phức tạp/nhạy cảm/khẩn cấp — mục tiêu trả lời ≥70% câu hỏi, ≥50% SV dùng hàng tháng; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Trả lời grounded trên quy định/thủ tục chính thức có trích nguồn (chống bịa); đo tỷ lệ trả lời ≥70% và tỷ lệ dùng hàng tháng (KPI); handover ngay với ca khẩn cấp/tâm lý/nhạy cảm, không tự xử lý (HITL); dữ liệu cá nhân SV bảo mật, phân quyền (FERPA-mindset); phân biệt rõ việc tra cứu và hành động thực thi (tool-use có xác nhận); kiểm soát chi phí/độ trễ.

### 🛠️ Tech Stack
• LLM
• RAG với pgvector lưu quy định/thủ tục + reranker
• agent tool-use (LangGraph) gọi API tạo ticket/tra lịch
• classifier phát hiện ca nhạy cảm/khẩn cấp để handover
• memory hội thoại
• eval: đo answer rate + độ chính xác + tỷ lệ handover đúng
• guardrails an toàn (tâm lý/khẩn cấp)
• backend FastAPI
• frontend Next.js chat + web
• deploy Docker + cloud, caching.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (SV/cán bộ hỗ trợ)
• trợ lý trả lời câu hỏi thủ tục có trích nguồn + tạo ticket mô phỏng + handover ca nhạy cảm
• cán bộ xử lý hàng chờ (HITL)
• metric cơ bản: answer rate.

Nâng cao:
• Tool-use đa dịch vụ (lịch, ticket, đặt phòng) có xác nhận, phát hiện ca khẩn cấp
• eval đạt KPI (≥70% trả lời, mô phỏng ≥50% dùng hàng tháng)
• dashboard vận hành ticket
• guardrails an toàn + tối ưu chi phí bằng routing model
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-15] PolicyMate AI: Trợ lý ảo tra cứu quy định quy chế cho lãnh đạo và cán bộ giảng viên

### 📝 Mô tả đề tài
📍 Thực trạng: Lãnh đạo, nhân viên và giảng viên trường đại học mất nhiều thời gian tìm văn bản, quy định, quy chế (QĐQC) đúng và mới nhất trong kho tài liệu nội bộ đồ sộ, dễ áp dụng nhầm phiên bản cũ. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng trợ lý ảo giải đáp nghiệp vụ, tra cứu văn bản/QĐQC có trích dẫn chính xác điều khoản, nhắc việc, hỗ trợ tạo báo cáo và tác vụ chuyên môn — mục tiêu độ chính xác ≥85%, giảm ≥50% thời gian tìm thông tin; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Câu trả lời grounded trên văn bản QĐQC chính thức, trích rõ số hiệu/điều khoản/phiên bản có hiệu lực (chống bịa — sai điều khoản gây hậu quả pháp lý); đo độ chính xác ≥85% và mức giảm thời gian tìm (KPI); phân quyền theo cấp/phòng ban (không lộ văn bản mật cho người không thẩm quyền); người dùng chịu trách nhiệm quyết định cuối, AI chỉ tư vấn (HITL); cảnh báo khi văn bản có thể đã hết hiệu lực; kiểm soát chi phí.

### 🛠️ Tech Stack
• LLM
• RAG với Qdrant lưu QĐQC có metadata (số hiệu, ngày hiệu lực, phòng ban) + hybrid search + reranker
• version tracking để ưu tiên bản mới
• RBAC phân quyền tài liệu
• agent tool-use (nhắc việc, sinh báo cáo) trên LangGraph
• eval RAGAS (faithfulness, citation accuracy) đo ≥85%
• guardrails chống bịa điều khoản + kiểm soát quyền
• backend FastAPI
• frontend Next.js
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (cán bộ/quản trị tài liệu)
• tra cứu QĐQC trả lời kèm trích dẫn điều khoản + số hiệu
• phân quyền cơ bản theo vai trò
• metric cơ bản: độ chính xác trích dẫn trên bộ test.

Nâng cao:
• Version tracking cảnh báo văn bản hết hiệu lực, tool-use nhắc việc + sinh báo cáo
• eval RAGAS đạt ≥85% + đo giảm ≥50% thời gian tìm
• dashboard quản trị tài liệu + RBAC đầy đủ
• guardrails chống bịa + tối ưu chi phí bằng caching
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-16] TalentScreen AI: Trợ lý tuyển dụng và nhân sự sàng lọc CV (agent đề xuất, HR quyết định)

### 📝 Mô tả đề tài
📍 Thực trạng: Bộ phận nhân sự trường đại học nhận lượng lớn CV cho các vị trí, sàng lọc thủ công tốn thời gian và thiếu nhất quán. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng trợ lý tuyển dụng phân tích CV theo mô tả công việc, phỏng vấn sàng lọc bằng câu hỏi cấu trúc, chấm độ phù hợp với vị trí và văn hóa tổ chức, gợi ý ứng viên nên vào vòng tiếp — ở mức ĐỀ XUẤT, HR quyết định cuối; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Đề xuất chỉ mang tính tham khảo, HR phê duyệt và chịu trách nhiệm (HITL); giảm thiên vị là bắt buộc — không dùng thuộc tính nhạy cảm (giới, tuổi, quê quán, trường), chấm dựa năng lực, giải thích được và có audit log công bằng; dữ liệu ứng viên bảo mật, phân quyền, xóa theo yêu cầu; đánh giá grounded trên nội dung CV + JD thật (chống bịa/suy diễn); đo độ tương đồng với đánh giá HR; kiểm soát chi phí.

### 🛠️ Tech Stack
• LLM
• RAG với pgvector lưu JD + khung năng lực + reranker
• CV parsing (trích kỹ năng/kinh nghiệm)
• matching + scoring agent (LangGraph) có giải thích
• interview agent sinh câu hỏi cấu trúc
• fairness eval (đo chênh lệch điểm theo nhóm ẩn danh) + similarity với nhãn HR
• guardrails loại bỏ thuộc tính nhạy cảm
• audit log
• backend FastAPI
• frontend Next.js
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (HR/quản lý tuyển dụng)
• agent phân tích CV theo JD, chấm phù hợp + giải thích
• HR duyệt/điều chỉnh (HITL)
• metric cơ bản: độ tương đồng với nhãn HR.

Nâng cao:
• Phỏng vấn sàng lọc tự động + gợi ý mức phù hợp tổ chức + fairness dashboard đo thiên vị theo nhóm ẩn danh
• eval pipeline đo chính xác + công bằng
• audit log + giải thích từng tiêu chí
• guardrails chống thiên vị + tối ưu chi phí
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-17] Trợ lý nghề nghiệp: Agent tối ưu CV và phỏng vấn thử cho sinh viên

### 📝 Mô tả đề tài
📍 Thực trạng: SV trường đại học chuẩn bị đi làm nhưng CV chưa khớp vị trí ứng tuyển và thiếu luyện phỏng vấn thực tế, tự tin thấp khi ra thị trường lao động. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent hướng nghiệp — dựa trên CV và vị trí ứng tuyển, phân tích khoảng cách và tối ưu CV để qua vòng hồ sơ (gợi ý cụ thể, không bịa kinh nghiệm), tổ chức phỏng vấn thử theo vị trí, chấm điểm và hướng dẫn cải thiện — mục tiêu ≥60% SV dùng, CSAT ≥4/5; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: AI tối ưu cách trình bày dựa trên kinh nghiệm THẬT của SV, TUYỆT ĐỐI không bịa/thổi phồng thành tích (liêm chính); phản hồi phỏng vấn mang tính huấn luyện, SV tự chịu trách nhiệm nội dung CV cuối (HITL); dữ liệu CV cá nhân bảo mật, phân quyền; đo tỷ lệ dùng ≥60% và CSAT ≥4/5 (KPI); phản hồi công bằng, không thiên vị theo ngành/hồ sơ; cảnh báo giới hạn (AI không đảm bảo trúng tuyển); kiểm soát chi phí.

### 🛠️ Tech Stack
• LLM
• RAG với Qdrant lưu JD thị trường + tiêu chí ATS + mẫu phỏng vấn + reranker
• CV gap analysis agent (LangGraph)
• mock interview agent (hỏi-đáp đa vòng, chấm theo rubric STAR)
• eval: đo chất lượng phản hồi (LLM-as-Judge) + thu CSAT + đo tỷ lệ dùng
• guardrails chống bịa kinh nghiệm
• backend FastAPI
• frontend Next.js (upload CV, phòng phỏng vấn)
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (SV/cố vấn hướng nghiệp)
• phân tích CV vs JD + gợi ý tối ưu (không bịa) + phỏng vấn thử chấm theo rubric
• cố vấn xem báo cáo (HITL)
• metric cơ bản: CSAT + điểm phỏng vấn trước/sau.

Nâng cao:
• Tối ưu CV theo ATS đa vị trí + phỏng vấn thử nhiều vòng có phản hồi chi tiết
• eval đo chất lượng phản hồi + đạt KPI (≥60% dùng, CSAT ≥4/5)
• dashboard cố vấn theo dõi tiến bộ SV
• guardrails chống bịa kinh nghiệm + tối ưu chi phí
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-18] AI Faculty Academy: Nền tảng đào tạo năng lực AI cho giảng viên, TA và cán bộ

### 📝 Mô tả đề tài
📍 Thực trạng: trường đại học triển khai nhiều công cụ AI nhưng giảng viên, TA, cán bộ có mức hiểu và kỹ năng AI rất khác nhau; thiếu chương trình đào tạo bài bản gắn với công việc thực tế của họ. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng đào tạo năng lực và hiểu biết AI cho GV/TA/CBNV — mô-đun theo vai trò (dùng AI soạn bài, chấm hỗ trợ, nghiên cứu, vận hành), bài thực hành gắn tình huống công việc, đánh giá năng lực theo khung năng lực AI của trường và cấp chứng nhận; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Nội dung grounded trên khung năng lực AI + chính sách dùng AI của trường có trích nguồn (chống bịa); dạy chính đội ngũ về liêm chính học thuật, HITL và bảo mật dữ liệu SV khi dùng AI trong giảng dạy; dữ liệu tiến độ học của CBNV phân quyền, ẩn danh khi thống kê; người quản lý chương trình duyệt nội dung và kết quả cấp chứng nhận (HITL); đo mức đạt khung năng lực; kiểm soát chi phí.

### 🛠️ Tech Stack
• LLM
• RAG với pgvector lưu khung năng lực + chính sách AI + tài liệu đào tạo + reranker
• adaptive module theo vai trò
• agent chấm bài thực hành tình huống (LangGraph)
• eval LLM-as-Judge cho bài thực hành + mapping kết quả vào khung năng lực
• guardrails
• backend FastAPI
• frontend Next.js LMS-lite + cấp chứng nhận
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Cơ sở dữ liệu học thuật mở OpenAlex, Semantic Scholar (S2ORC), Crossref, arXiv API và bộ benchmark QASPER / SciFact / LitQA2.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (người học GV/TA-CBNV / quản trị chương trình)
• mô-đun theo vai trò + bài thực hành tình huống được AI chấm + đánh giá năng lực
• quản trị duyệt chứng nhận (HITL)
• metric cơ bản: mức đạt khung năng lực.

Nâng cao:
• Adaptive path đa vai trò + gắn tình huống công việc thật
• eval pipeline mapping vào khung năng lực AI + dashboard độ phủ đào tạo toàn đội ngũ
• cấp chứng nhận số
• guardrails + tối ưu chi phí bằng caching nội dung chung
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-19] AI Competency Compass: Công cụ đánh giá và bản đồ hóa khung năng lực AI toàn trường

### 📝 Mô tả đề tài
📍 Thực trạng: trường đại học cần một khung năng lực AI chung và cách đo lường năng lực AI của từng cá nhân/phòng ban để quản trị nguồn lực và lập kế hoạch đào tạo, nhưng hiện chưa có công cụ đánh giá chuẩn hóa. Trong môi trường đào tạo và nghiên cứu thực tế, dữ liệu học tập và tài liệu học thuật thường phân tán, đa phiên bản và đòi hỏi độ chính xác trích dẫn cũng như chuẩn mực sư phạm rất cao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ đánh giá năng lực AI (self-assessment + bài test tình huống + AI phỏng vấn năng lực), bản đồ hóa năng lực theo khung của trường, phát hiện khoảng trống kỹ năng theo phòng ban và đề xuất lộ trình đào tạo — phục vụ quản trị; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Bài đánh giá và diễn giải grounded trên khung năng lực AI chính thức có trích nguồn (chống bịa); kết quả cá nhân bảo mật, phân quyền — cá nhân thấy chi tiết mình, quản lý chỉ thấy tổng hợp ẩn danh cấp phòng (FERPA/privacy-mindset); AI chỉ đề xuất, lãnh đạo quyết định kế hoạch đào tạo/nhân sự (HITL, không dùng để đánh giá kỷ luật cá nhân); tránh thiên vị trong chấm năng lực, giải thích được; đo độ tin cậy đánh giá; kiểm soát chi phí.

### 🛠️ Tech Stack
• LLM
• RAG với Qdrant lưu khung năng lực + tiêu chí + reranker
• assessment engine (test tình huống có chấm rubric) + AI interview agent (LangGraph)
• analytics bản đồ năng lực (aggregation ẩn danh)
• eval: đo độ tin cậy chấm (so nhãn chuyên gia) + fairness
• guardrails phân quyền dữ liệu
• backend FastAPI
• frontend Next.js dashboard heatmap năng lực
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (cá nhân/quản trị nhân lực)
• bài self-assessment + test tình huống chấm theo khung, cá nhân xem kết quả + gợi ý học
• quản trị xem tổng hợp ẩn danh (HITL)
• metric cơ bản: độ tin cậy chấm so nhãn.

Nâng cao:
• AI phỏng vấn năng lực + bản đồ khoảng trống kỹ năng theo phòng ban + đề xuất lộ trình đào tạo
• eval đo độ tin cậy + fairness
• dashboard quản trị heatmap năng lực toàn trường (ẩn danh)
• guardrails phân quyền nghiêm ngặt + tối ưu chi phí
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---

## [EDU-20] AI Governance Monitor: Trợ lý giám sát tuân thủ và chất lượng các sản phẩm AI của trường

### 📝 Mô tả đề tài
📍 Thực trạng: Khi trường đại học triển khai nhiều sản phẩm AI (học tập, tuyển sinh, vận hành), ban quản trị cần giám sát việc tuân thủ nguyên tắc đạo đức (HITL, liêm chính, bảo mật, chống thiên vị) và chất lượng đầu ra, nhưng chưa có công cụ theo dõi tập trung.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng trợ lý quản trị AI thu thập log/metric từ các hệ thống AI, đánh giá tuân thủ chính sách dùng AI của trường (có HITL không, có trích nguồn không, có ẩn danh dữ liệu không, có cảnh báo giới hạn không), phát hiện vi phạm/rủi ro và tổng hợp báo cáo cho hội đồng quản trị AI; đồng thời kết hợp suy luận đa tác tử với các mô-đun kiểm chứng nguồn học thuật hoặc theo dõi trạng thái năng lực xác định, giúp giải quyết tận gốc điểm nghẽn nhận thức và vận hành mà không làm bài thay người học.

🔒 Ràng buộc: Đánh giá tuân thủ grounded trên chính sách/khung đạo đức AI chính thức có trích nguồn (chống bịa); AI chỉ phát hiện và cảnh báo, hội đồng quản trị quyết định xử lý (HITL); dữ liệu log có thể chứa thông tin nhạy cảm — ẩn danh, phân quyền chặt; đánh giá công bằng giữa các hệ thống, giải thích được từng cảnh báo; đo độ chính xác phát hiện vi phạm; kiểm soát chi phí.

### 🛠️ Tech Stack
• LLM
• RAG với pgvector lưu chính sách/khung đạo đức AI + reranker
• log ingestion + rule engine + LLM đánh giá tuân thủ theo checklist
• anomaly/risk detection agent (LangGraph)
• eval: đo precision/recall phát hiện vi phạm so nhãn chuyên gia
• guardrails ẩn danh log
• backend FastAPI
• frontend Next.js dashboard tuân thủ + báo cáo
• deploy Docker + cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phân tích giáo dục mở EdNet (Riiid), ASSISTments, OULAD (Open University Learning Analytics), khung kỹ năng ESCO / O*NET và chuẩn LMS LTI 1.3.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app deploy, ≥2 vai trò (quản trị AI/kiểm toán)
• nạp log mô phỏng từ vài hệ thống AI, đánh giá tuân thủ theo checklist có trích chính sách + gắn cờ vi phạm
• hội đồng xem và xử lý (HITL)
• metric cơ bản: độ chính xác gắn cờ so nhãn.

Nâng cao:
• Ingestion nhiều nguồn + phát hiện rủi ro/bất thường + sinh báo cáo định kỳ cho hội đồng
• eval precision/recall phát hiện vi phạm
• dashboard tuân thủ toàn cảnh (điểm tuân thủ từng hệ thống, xu hướng)
• guardrails ẩn danh log + tối ưu chi phí bằng lọc rule trước khi gọi LLM
• Kết hợp mô-đun kiểm chứng dữ liệu xác định với đánh giá định lượng trên bộ dữ liệu giáo dục/học thuật thực tế, mở rộng các tính năng phân tích chiều sâu hỗ trợ người học và giảng viên.

---
