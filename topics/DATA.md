# Lĩnh vực: DATA - Dữ liệu – Khối dữ liệu tập trung doanh nghiệp

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `DATA-01` | [AI Agent Text-to-SQL Self-Service Analytics cho dữ liệu doanh nghiệp](#data-01) |
| `DATA-02` | [AI Agent xây dựng & kiểm tra Data Quality và phát hiện bất thường](#data-02) |
| `DATA-03` | [AI Agent Data Catalog & Discovery bằng ngôn ngữ tự nhiên](#data-03) |
| `DATA-04` | [AI Agent tự động sinh & duy trì Data Lineage](#data-04) |
| `DATA-05` | [AI Agent viết & tối ưu ETL/ELT Pipeline](#data-05) |
| `DATA-06` | [AI Agent phát hiện & masking PII phục vụ tuân thủ](#data-06) |
| `DATA-07` | [AI Agent quản trị Metadata & Data Contract](#data-07) |
| `DATA-08` | [AI Agent hỏi đáp dữ liệu đa nguồn theo mô hình Data Mesh](#data-08) |
| `DATA-09` | [AI Agent tự động sinh & duy trì tài liệu Dataset](#data-09) |
| `DATA-10` | [AI Agent giám sát Pipeline & phân tích Root-Cause khi lỗi](#data-10) |
| `DATA-11` | [AI Agent xây dựng Semantic Layer & định nghĩa chỉ số thống nhất](#data-11) |
| `DATA-12` | [AI Agent dọn dẹp & chuẩn hóa dữ liệu bẩn](#data-12) |
| `DATA-13` | [AI Agent Data Profiling & tự sinh hồ sơ dữ liệu](#data-13) |
| `DATA-14` | [AI Agent gợi ý & thiết kế mô hình dữ liệu](#data-14) |
| `DATA-15` | [AI Agent phân quyền & Audit truy cập dữ liệu](#data-15) |
| `DATA-16` | [AI Agent tự sinh Dashboard từ yêu cầu ngôn ngữ tự nhiên](#data-16) |
| `DATA-17` | [AI Agent phát hiện dữ liệu trùng & quản lý Master Data](#data-17) |
| `DATA-18` | [AI Agent phát hiện Data Drift & giám sát dữ liệu cho mô hình ML](#data-18) |
| `DATA-19` | [AI Agent trợ lý Data Governance & tra cứu chính sách dữ liệu](#data-19) |
| `DATA-20` | [AI Agent điều phối yêu cầu dữ liệu (Data Request Intake & Triage)](#data-20) |

---

## [DATA-01] AI Agent Text-to-SQL Self-Service Analytics cho dữ liệu doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Nhân viên nghiệp vụ tại doanh nghiệp cần số liệu bán hàng, tồn kho nhưng phải chờ đội Data viết SQL, thời gian phản hồi vài ngày. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent nhận câu hỏi tiếng Việt tự nhiên, tự lập kế hoạch truy vấn, sinh SQL đúng schema, chạy trên warehouse, trả về bảng + biểu đồ + diễn giải; biết hỏi lại khi câu hỏi mơ hồ và ghi nhớ ngữ cảnh hội thoại; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL người dùng xem SQL sinh ra và xác nhận trước khi chạy trên bảng lớn; governance phân quyền theo vai trò (analyst chỉ đọc, admin quản lý schema); độ chính xác SQL đo được; giới hạn chi phí quét dữ liệu (bytes scanned) và cảnh báo khi vượt ngưỡng. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM (GPT-4o/Claude) + function calling
• LangGraph điều phối agent (planner → SQL generator → validator → executor)
• LlamaIndex + vector DB (Qdrant/pgvector) lưu embedding schema & few-shot examples
• warehouse BigQuery/Snowflake (hoặc Trino trên dữ liệu mẫu)
• dbt semantic model
• backend FastAPI
• frontend Next.js + Recharts
• deploy Vercel + Render/Railway
• auth Supabase Auth.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark truy vấn dữ liệu doanh nghiệp độ khó cao BIRD-SQL (có dữ liệu nhiễu), Spider 2.0 (Enterprise dbt/warehouse workflows) và TPC-H / TPC-DS / Olist Warehouse.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy online, đăng nhập 2 vai trò (Analyst/Admin), agent nhận NL → sinh SQL → chạy → trả bảng + chart + giải thích, HITL duyệt SQL, log truy vấn.

Nâng cao:
• multi-agent (agent sửa lỗi SQL tự retry khi query fail), bộ eval đo execution accuracy trên tập câu hỏi mẫu (Spider-like), tự tối ưu prompt/few-shot theo phản hồi, ước tính & giới hạn chi phí quét
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-02] AI Agent xây dựng & kiểm tra Data Quality và phát hiện bất thường

### 📝 Mô tả đề tài
📍 Thực trạng: Dữ liệu vận hành doanh nghiệp có null, sai định dạng, giá trị ngoại lai nhưng đội data phải viết tay hàng trăm test dbt. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự khảo sát dataset, đề xuất bộ rule chất lượng (uniqueness, not-null, range, format, freshness), sinh test tự động, chạy định kỳ, phát hiện anomaly bằng thống kê/ML và gửi cảnh báo kèm chẩn đoán nguyên nhân; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL data steward duyệt rule trước khi áp dụng production; governance chỉ đọc metadata không lộ dữ liệu nhạy cảm; độ chính xác cảnh báo (giảm false positive); hiệu năng chạy check trên bảng lớn theo lịch, giới hạn tài nguyên. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM sinh rule & diễn giải
• LangGraph agent (profiler → rule proposer → test generator → anomaly detector)
• Great Expectations/dbt tests
• scikit-learn (Isolation Forest/z-score) cho anomaly
• Airflow/Dagster scheduler
• warehouse Snowflake/BigQuery
• vector DB lưu lịch sử rule
• backend FastAPI
• frontend React + Ant Design
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark phát hiện bất thường chuỗi thời gian NAB (Numenta Anomaly Benchmark), đối sánh thực thể Febrl/Splink và bộ dữ liệu nhận diện PII Microsoft Presidio.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Steward/Viewer), agent profiling dataset → đề xuất rule → HITL duyệt → sinh & chạy test → dashboard kết quả + cảnh báo.

Nâng cao:
• multi-agent kết hợp phát hiện anomaly ML, eval đo precision/recall cảnh báo trên dữ liệu có lỗi gán nhãn, tự đề xuất ngưỡng tối ưu, phân tích xu hướng chất lượng theo thời gian
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-03] AI Agent Data Catalog & Discovery bằng ngôn ngữ tự nhiên

### 📝 Mô tả đề tài
📍 Thực trạng: Toàn tập đoàn có hàng nghìn bảng/dataset rải rác, nhân viên không biết dataset nào tồn tại hay ai sở hữu. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent cho phép tìm kiếm dataset bằng câu hỏi tự nhiên ('dữ liệu doanh thu bán xe theo tháng ở đâu?'), agent hiểu ý định, tra catalog + metadata + lineage, gợi ý bảng phù hợp, giải thích ý nghĩa cột và độ tin cậy nguồn; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL owner xác nhận/bổ sung mô tả dataset; governance ẩn dataset ngoài quyền truy cập của người dùng; độ chính xác gợi ý (đúng bảng cần tìm); hiệu năng tìm kiếm nhanh trên catalog lớn, kiểm soát chi phí embedding. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM + RAG
• LlamaIndex + vector DB (Weaviate/pgvector) index metadata & mô tả cột
• DataHub/OpenMetadata API làm catalog nền
• LangGraph agent (intent → retrieve → rank → explain)
• warehouse information_schema
• backend FastAPI
• frontend Next.js
• deploy Cloud Run + Supabase.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn siêu dữ liệu mở OpenLineage, DataHub / OpenMetadata schemas và các dự án mẫu dbt-core đa tầng kèm lịch sử git/log lỗi pipeline.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Owner/User), tìm kiếm NL → gợi ý dataset kèm mô tả, lineage cơ bản & owner, HITL owner sửa metadata.

Nâng cao:
• multi-agent tự động sinh mô tả dataset còn thiếu, eval đo hit@k/recall trên tập truy vấn gán nhãn, cá nhân hóa gợi ý theo lịch sử người dùng, phản hồi cải thiện ranking
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-04] AI Agent tự động sinh & duy trì Data Lineage

### 📝 Mô tả đề tài
📍 Thực trạng: Khi một bảng đổi schema hoặc pipeline lỗi, không ai biết downstream nào bị ảnh hưởng vì lineage vẽ tay lỗi thời. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự parse SQL/dbt/ETL code để dựng đồ thị lineage cột-tới-cột, cập nhật khi code thay đổi, trả lời câu hỏi tác động ('nếu sửa cột này thì báo cáo nào hỏng?') và cảnh báo breaking change; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL người dùng xác nhận cạnh lineage suy luận không chắc; governance chỉ đọc code/metadata; độ chính xác đồ thị (đúng quan hệ phụ thuộc); hiệu năng parse hàng trăm query, giới hạn chi phí LLM khi phân tích. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM hỗ trợ parse SQL phức tạp
• sqlglot/sqllineage parser
• LangGraph agent (parse → build graph → validate → impact analysis)
• Neo4j/NetworkX lưu graph
• dbt manifest
• vector DB cho tra cứu
• backend FastAPI
• frontend React + react-flow (đồ thị)
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark truy vấn dữ liệu doanh nghiệp độ khó cao BIRD-SQL (có dữ liệu nhiễu), Spider 2.0 (Enterprise dbt/warehouse workflows) và TPC-H / TPC-DS / Olist Warehouse.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Engineer/Viewer), upload/kết nối SQL & dbt → sinh graph lineage cột, tra cứu impact, HITL duyệt cạnh nghi ngờ.

Nâng cao:
• multi-agent (agent phát hiện breaking change tự cảnh báo), eval so lineage sinh ra với ground-truth (precision cạnh), tự động cập nhật khi code thay đổi, gợi ý sửa downstream
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-05] AI Agent viết & tối ưu ETL/ELT Pipeline

### 📝 Mô tả đề tài
📍 Thực trạng: Data engineer mất nhiều thời gian viết pipeline dbt/Airflow lặp đi lặp lại và tối ưu query chậm. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent nhận yêu cầu NL ('gộp dữ liệu đơn hàng 3 nguồn, tính doanh thu ngày'), tự lập kế hoạch, sinh model dbt + DAG Airflow, chạy thử trên sandbox, phát hiện query chậm và đề xuất tối ưu (partition, index, rewrite); đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL engineer review & merge code trước khi lên prod; governance không chạy trực tiếp trên prod, chỉ sandbox; độ chính xác kết quả pipeline (so với kỳ vọng); hiệu năng/chi phí query được đo và tối ưu. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM code-gen
• LangGraph agent (planner → codegen → test-run → optimizer)
• dbt + Airflow/Dagster
• warehouse DuckDB/BigQuery sandbox
• sqlglot phân tích query plan
• vector DB lưu mẫu pipeline
• backend FastAPI
• frontend Next.js + Monaco editor
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark truy vấn dữ liệu doanh nghiệp độ khó cao BIRD-SQL (có dữ liệu nhiễu), Spider 2.0 (Enterprise dbt/warehouse workflows) và TPC-H / TPC-DS / Olist Warehouse.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Engineer/Reviewer), NL → sinh dbt model + DAG → chạy thử sandbox → HITL review diff & duyệt.

Nâng cao:
• multi-agent (agent optimizer đo & rewrite query chậm), eval đo tính đúng output pipeline + cải thiện thời gian/chi phí chạy so với baseline, tự sinh test cho pipeline
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-06] AI Agent phát hiện & masking PII phục vụ tuân thủ

### 📝 Mô tả đề tài
📍 Thực trạng: Dữ liệu doanh nghiệp chứa PII (CMND, SĐT, hồ sơ y tế) nằm rải rác, khó rà soát tuân thủ nghị định bảo vệ dữ liệu cá nhân. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự quét dataset, phát hiện & phân loại PII, đề xuất chính sách masking/tokenization phù hợp, sinh view đã che dữ liệu, tạo báo cáo tuân thủ và cảnh báo dataset rủi ro cao; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL DPO duyệt phân loại PII và chính sách trước khi áp dụng; governance nghiêm ngặt, không lộ giá trị PII thật ra ngoài, log audit đầy đủ; độ chính xác phát hiện PII cao; hiệu năng quét bảng lớn, giới hạn chi phí. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM + regex/NER (Presidio) phát hiện PII
• LangGraph agent (scan → classify → policy → mask → report)
• warehouse Snowflake/BigQuery dynamic masking
• vector DB lưu pattern
• backend FastAPI
• frontend React
• deploy Docker + Cloud Run
• hashing/tokenization vault.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark phát hiện bất thường chuỗi thời gian NAB (Numenta Anomaly Benchmark), đối sánh thực thể Febrl/Splink và bộ dữ liệu nhận diện PII Microsoft Presidio.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (DPO/Analyst), quét dataset → phát hiện & phân loại PII → đề xuất masking → HITL duyệt → sinh view masked + báo cáo tuân thủ.

Nâng cao:
• multi-agent (agent đánh giá rủi ro & xếp hạng dataset), eval đo precision/recall phát hiện PII trên tập gán nhãn, tự học pattern PII đặc thù tiếng Việt, audit log đầy đủ
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-07] AI Agent quản trị Metadata & Data Contract

### 📝 Mô tả đề tài
📍 Thực trạng: Các team producer đổi schema tùy tiện làm hỏng consumer downstream vì thiếu data contract được giám sát. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent hỗ trợ soạn & duy trì data contract (schema, SLA, ràng buộc), tự động kiểm tra dataset thực tế so với contract, phát hiện vi phạm (drift schema, trễ SLA), thương lượng thay đổi giữa producer-consumer và cảnh báo; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL producer & consumer cùng duyệt thay đổi contract; governance versioning contract, kiểm soát ai được sửa; độ chính xác phát hiện vi phạm; hiệu năng kiểm tra định kỳ, chi phí hợp lý. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM soạn/đối chiếu contract
• LangGraph agent (draft → validate → monitor → notify)
• JSON Schema/dbt contracts
• warehouse information_schema
• vector DB
• backend FastAPI
• frontend Next.js
• scheduler Airflow
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn siêu dữ liệu mở OpenLineage, DataHub / OpenMetadata schemas và các dự án mẫu dbt-core đa tầng kèm lịch sử git/log lỗi pipeline.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Producer/Consumer), soạn contract có hỗ trợ AI → kiểm tra dataset vs contract → cảnh báo vi phạm → HITL duyệt thay đổi.

Nâng cao:
• multi-agent điều phối thương lượng thay đổi contract & phân tích tác động, eval đo độ chính xác phát hiện schema drift, versioning & rollback contract, gợi ý điều khoản SLA
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-08] AI Agent hỏi đáp dữ liệu đa nguồn theo mô hình Data Mesh

### 📝 Mô tả đề tài
📍 Thực trạng: Dữ liệu phân tán theo domain (doanh nghiệp bất động sản, doanh nghiệp ô tô, dịch vụ gọi xe của doanh nghiệp) mỗi nơi một warehouse; câu hỏi liên domain phải ghép tay. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent điều phối truy vấn liên nhiều nguồn dữ liệu, tự lập kế hoạch phân rã câu hỏi, chọn đúng domain/data product, truy vấn từng nơi, hợp nhất kết quả và trả lời có trích nguồn; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL người dùng xem kế hoạch truy vấn liên nguồn trước khi chạy; governance tôn trọng quyền truy cập từng domain, không vượt rào; độ chính xác kết quả hợp nhất; hiệu năng/chi phí truy vấn nhiều nguồn được kiểm soát. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM planner
• LangGraph multi-agent (router → per-domain SQL agent → aggregator)
• Trino/federated query hoặc nhiều connector (Postgres, BigQuery, MySQL)
• LlamaIndex + vector DB catalog data product
• backend FastAPI
• frontend Next.js
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark truy vấn dữ liệu doanh nghiệp độ khó cao BIRD-SQL (có dữ liệu nhiễu), Spider 2.0 (Enterprise dbt/warehouse workflows) và TPC-H / TPC-DS / Olist Warehouse.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (User/Domain Owner), câu hỏi liên domain → agent phân rã → truy vấn ≥2 nguồn → hợp nhất & trả lời có nguồn, HITL duyệt kế hoạch.

Nâng cao:
• multi-agent chuyên biệt theo domain + agent điều phối, eval đo độ chính xác câu trả lời liên nguồn, tối ưu số lượng & chi phí truy vấn, xử lý xung đột dữ liệu giữa nguồn
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-09] AI Agent tự động sinh & duy trì tài liệu Dataset

### 📝 Mô tả đề tài
📍 Thực trạng: Phần lớn dataset không có tài liệu; cột không mô tả, người dùng đoán ý nghĩa dẫn tới dùng sai. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự khảo sát dataset (mẫu dữ liệu, thống kê, lineage, tên cột), sinh tài liệu mô tả bảng/cột/quan hệ/ví dụ dùng, phát hiện tài liệu lỗi thời và đề xuất cập nhật khi schema đổi; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL data owner duyệt/sửa mô tả AI sinh ra trước khi publish; governance chỉ dùng metadata & mẫu ẩn PII; độ chính xác mô tả (đúng ý nghĩa cột); hiệu năng & chi phí LLM khi tài liệu hóa nhiều bảng. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM sinh mô tả
• LangGraph agent (profile → draft doc → validate → publish)
• LlamaIndex + vector DB
• warehouse information_schema + sampling
• DataHub/OpenMetadata publish
• backend FastAPI
• frontend Next.js (wiki-style)
• deploy Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn siêu dữ liệu mở OpenLineage, DataHub / OpenMetadata schemas và các dự án mẫu dbt-core đa tầng kèm lịch sử git/log lỗi pipeline.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Owner/Reader), chọn dataset → agent sinh tài liệu bảng/cột + ví dụ → HITL duyệt & publish trang tài liệu.

Nâng cao:
• multi-agent (agent giám sát phát hiện doc lỗi thời khi schema đổi), eval đánh giá chất lượng mô tả bằng LLM-as-judge/đối chiếu ground-truth, tự cập nhật gia tăng, đa ngôn ngữ Việt-Anh
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-10] AI Agent giám sát Pipeline & phân tích Root-Cause khi lỗi

### 📝 Mô tả đề tài
📍 Thực trạng: Khi pipeline Airflow lỗi lúc 2h sáng, on-call phải lần mò log nhiều tầng để tìm nguyên nhân, mất thời gian phục hồi. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent giám sát trạng thái pipeline, khi có lỗi tự thu thập log/metric/lineage, suy luận nguyên nhân gốc (nguồn trễ, schema đổi, tài nguyên), đề xuất cách khắc phục và (khi được duyệt) thực hiện retry/backfill; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL kỹ sư duyệt trước mọi hành động khắc phục (retry/rollback); governance chỉ tác động môi trường được phép, log audit; độ chính xác chẩn đoán nguyên nhân; hiệu năng phản hồi nhanh, giới hạn chi phí phân tích. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM suy luận
• LangGraph agent (detect → collect logs → RCA → recommend → act-with-approval)
• Airflow/Dagster API + logs
• lineage graph (từ DATA-04)
• vector DB lưu sự cố lịch sử
• backend FastAPI
• frontend React + timeline
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn siêu dữ liệu mở OpenLineage, DataHub / OpenMetadata schemas và các dự án mẫu dbt-core đa tầng kèm lịch sử git/log lỗi pipeline.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (On-call/Viewer), giám sát pipeline → khi lỗi thu log & đưa chẩn đoán nguyên nhân + gợi ý fix, HITL duyệt retry/backfill.

Nâng cao:
• multi-agent (agent tra cứu sự cố tương tự trong lịch sử), eval đo độ chính xác RCA trên tập sự cố gán nhãn, tự học từ sự cố cũ, ước tính tác động & ưu tiên xử lý
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-11] AI Agent xây dựng Semantic Layer & định nghĩa chỉ số thống nhất

### 📝 Mô tả đề tài
📍 Thực trạng: Cùng chỉ số 'doanh thu' mỗi phòng tính một kiểu, báo cáo lệch nhau gây tranh cãi. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent hỗ trợ định nghĩa semantic layer (metric, dimension, công thức) thống nhất, phát hiện định nghĩa trùng/mâu thuẫn, cho phép hỏi chỉ số bằng NL và tự dịch sang query dựa trên metric đã chuẩn hóa; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL data lead duyệt định nghĩa metric trước khi ban hành chuẩn; governance versioning & phân quyền sửa metric; độ chính xác số liệu (khớp định nghĩa chuẩn); hiệu năng truy vấn & chi phí hợp lý. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM
• LangGraph agent (extract metric → dedupe → define → NL-to-metric query)
• dbt Semantic Layer/Cube.dev/MetricFlow
• warehouse BigQuery/Snowflake
• vector DB lưu định nghĩa
• backend FastAPI
• frontend Next.js
• deploy Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark truy vấn dữ liệu doanh nghiệp độ khó cao BIRD-SQL (có dữ liệu nhiễu), Spider 2.0 (Enterprise dbt/warehouse workflows) và TPC-H / TPC-DS / Olist Warehouse.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Data Lead/Analyst), định nghĩa metric có hỗ trợ AI → phát hiện trùng/mâu thuẫn → HITL duyệt → hỏi chỉ số NL trả về số chuẩn.

Nâng cao:
• multi-agent phát hiện & hòa giải định nghĩa mâu thuẫn giữa phòng ban, eval đo độ khớp số liệu qua semantic layer vs query thủ công, versioning metric, gợi ý chuẩn hóa
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-12] AI Agent dọn dẹp & chuẩn hóa dữ liệu bẩn

### 📝 Mô tả đề tài
📍 Thực trạng: Dữ liệu khách hàng/địa chỉ/tên sản phẩm nhập tay không nhất quán (viết hoa, dấu, viết tắt, sai chính tả) làm gộp & báo cáo sai. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự phát hiện vấn đề chuẩn hóa (định dạng ngày, số điện thoại, địa chỉ VN, tên riêng), đề xuất & áp dụng luật làm sạch, chuẩn hóa giá trị theo từ điển chuẩn, giữ log biến đổi để có thể hoàn tác; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL người dùng duyệt luật làm sạch trên mẫu trước khi áp toàn bộ; governance không ghi đè dữ liệu gốc, giữ bản sao & audit; độ chính xác chuẩn hóa (không làm hỏng giá trị đúng); hiệu năng trên bảng lớn, chi phí kiểm soát. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM + rapidfuzz/fuzzy matching
• LangGraph agent (profile → propose rule → preview → apply → log)
• pandas/DuckDB xử lý
• từ điển chuẩn hóa VN (địa danh)
• vector DB
• backend FastAPI
• frontend React + diff view
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark phát hiện bất thường chuỗi thời gian NAB (Numenta Anomaly Benchmark), đối sánh thực thể Febrl/Splink và bộ dữ liệu nhận diện PII Microsoft Presidio.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Editor/Approver), upload/kết nối dữ liệu → agent phát hiện & đề xuất luật làm sạch → preview → HITL duyệt → áp dụng + log hoàn tác.

Nâng cao:
• multi-agent (agent chuẩn hóa entity theo từ điển master), eval đo accuracy chuẩn hóa trên tập gán nhãn, tự học luật đặc thù tiếng Việt, đề xuất ngưỡng fuzzy tối ưu
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-13] AI Agent Data Profiling & tự sinh hồ sơ dữ liệu

### 📝 Mô tả đề tài
📍 Thực trạng: Trước khi dùng một dataset mới, analyst phải tự chạy thống kê mô tả thủ công để hiểu phân phối, null, cardinality. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự động profiling dataset (thống kê từng cột, phân phối, null, outlier, tương quan, khóa ứng viên), sinh báo cáo hồ sơ dữ liệu dễ đọc kèm nhận xét & cảnh báo rủi ro chất lượng, trả lời câu hỏi NL về đặc điểm dữ liệu; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL người dùng xác nhận suy luận (ví dụ đâu là khóa chính) trước khi ghi vào metadata; governance ẩn mẫu PII trong báo cáo; độ chính xác thống kê & nhận định; hiệu năng sampling thông minh trên bảng lớn để tiết kiệm chi phí. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM diễn giải
• LangGraph agent (sample → compute stats → summarize → QA)
• ydata-profiling/DuckDB
• warehouse BigQuery sampling
• vector DB
• backend FastAPI
• frontend Next.js + Recharts
• deploy Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark phát hiện bất thường chuỗi thời gian NAB (Numenta Anomaly Benchmark), đối sánh thực thể Febrl/Splink và bộ dữ liệu nhận diện PII Microsoft Presidio.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Analyst/Viewer), chọn dataset → agent profiling → báo cáo thống kê + biểu đồ + nhận xét, hỏi đáp NL, HITL xác nhận khóa/kiểu.

Nâng cao:
• multi-agent (agent so sánh profile giữa 2 phiên bản dữ liệu phát hiện drift), eval đo độ chính xác nhận định (đúng khóa, đúng kiểu) trên dữ liệu gán nhãn, sampling tối ưu chi phí, gợi ý bước làm sạch
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-14] AI Agent gợi ý & thiết kế mô hình dữ liệu

### 📝 Mô tả đề tài
📍 Thực trạng: Team mới xây data warehouse cho một nghiệp vụ (ví dụ đặt xe dịch vụ gọi xe của doanh nghiệp) tốn nhiều thời gian thiết kế schema star/snowflake đúng chuẩn. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent nhận mô tả nghiệp vụ + dữ liệu nguồn, đề xuất mô hình dữ liệu (fact/dimension, khóa, quan hệ, grain), sinh DDL & sơ đồ ERD, giải thích lựa chọn và cảnh báo anti-pattern; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL kiến trúc sư duyệt & tinh chỉnh mô hình trước khi tạo bảng; governance chỉ sinh DDL sandbox, không tác động prod; độ chính xác mô hình (chuẩn hóa/grain đúng); hiệu năng & chi phí LLM khi mô hình lớn. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM thiết kế
• LangGraph agent (analyze source → propose model → generate DDL/ERD → critique)
• sqlglot
• warehouse DuckDB/BigQuery sandbox
• vector DB mẫu mô hình
• backend FastAPI
• frontend React + react-flow ERD
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark truy vấn dữ liệu doanh nghiệp độ khó cao BIRD-SQL (có dữ liệu nhiễu), Spider 2.0 (Enterprise dbt/warehouse workflows) và TPC-H / TPC-DS / Olist Warehouse.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Architect/Reviewer), mô tả nghiệp vụ + nguồn → agent đề xuất fact/dim + ERD + DDL + giải thích, HITL chỉnh sửa.

Nâng cao:
• multi-agent (agent critic đánh giá & phát hiện anti-pattern), eval so mô hình sinh ra với thiết kế chuẩn (điểm chất lượng), gợi ý nhiều phương án đánh đổi, sinh dbt project khởi tạo
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-15] AI Agent phân quyền & Audit truy cập dữ liệu

### 📝 Mô tả đề tài
📍 Thực trạng: Yêu cầu cấp quyền truy cập dataset xử lý thủ công qua email/ticket, khó rà soát ai đang có quyền gì và có quyền thừa (over-privileged). Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tiếp nhận yêu cầu cấp quyền bằng NL, đánh giá theo chính sách (least privilege, phân loại độ nhạy), đề xuất grant tối thiểu, phát hiện quyền bất thường/thừa qua phân tích log truy cập và sinh báo cáo audit; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL data owner/security phê duyệt mọi cấp quyền (bắt buộc, không tự cấp); governance tuân chính sách phân loại dữ liệu, log audit đầy đủ; độ chính xác đánh giá rủi ro; hiệu năng phân tích log lớn, chi phí kiểm soát. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM
• LangGraph agent (parse request → policy check → recommend grant → anomaly on access log)
• OPA/policy engine
• warehouse access logs + information_schema
• vector DB chính sách
• backend FastAPI
• frontend Next.js
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark phát hiện bất thường chuỗi thời gian NAB (Numenta Anomaly Benchmark), đối sánh thực thể Febrl/Splink và bộ dữ liệu nhận diện PII Microsoft Presidio.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Requester/Approver), yêu cầu quyền NL → agent đề xuất grant tối thiểu theo chính sách → HITL owner phê duyệt → log audit.

Nâng cao:
• multi-agent (agent phát hiện quyền thừa & truy cập bất thường từ log), eval đo độ chính xác gợi ý least-privilege & cảnh báo, báo cáo tuân thủ định kỳ, mô phỏng thu hồi quyền
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-16] AI Agent tự sinh Dashboard từ yêu cầu ngôn ngữ tự nhiên

### 📝 Mô tả đề tài
📍 Thực trạng: Lãnh đạo doanh nghiệp bất động sản muốn dashboard theo dõi KPI nhưng phải chờ team BI dựng trên Looker/Power BI vài ngày. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent nhận yêu cầu NL ('dashboard doanh số theo khu vực & quý'), tự chọn dataset/metric, sinh truy vấn, đề xuất loại biểu đồ phù hợp, dựng dashboard tương tác và cho tinh chỉnh bằng hội thoại, ghi nhớ ngữ cảnh; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL người dùng xem & duyệt bố cục/biểu đồ trước khi lưu; governance chỉ hiển thị dữ liệu trong quyền người dùng; độ chính xác số liệu & chọn chart hợp lý; hiệu năng render & chi phí truy vấn kiểm soát. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM
• LangGraph agent (understand → pick metrics → SQL → choose viz → layout)
• semantic layer (Cube.dev)
• warehouse BigQuery/Snowflake
• frontend Next.js + Recharts/ECharts
• vector DB
• backend FastAPI
• deploy Vercel + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark truy vấn dữ liệu doanh nghiệp độ khó cao BIRD-SQL (có dữ liệu nhiễu), Spider 2.0 (Enterprise dbt/warehouse workflows) và TPC-H / TPC-DS / Olist Warehouse.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Viewer/Builder), yêu cầu NL → agent sinh dashboard nhiều biểu đồ tương tác + tinh chỉnh hội thoại, HITL duyệt & lưu.

Nâng cao:
• multi-agent (agent tư vấn chọn loại biểu đồ tối ưu theo dữ liệu), eval đo độ phù hợp chart & độ chính xác số liệu, tự sinh insight/annotation, chia sẻ & lập lịch cập nhật dashboard
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-17] AI Agent phát hiện dữ liệu trùng & quản lý Master Data

### 📝 Mô tả đề tài
📍 Thực trạng: Cùng một khách hàng/nhà cung cấp tồn tại nhiều bản ghi khác biệt nhỏ trên các hệ thống doanh nghiệp, gây trùng lặp & sai báo cáo 360 độ. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent thực hiện entity resolution: sinh khóa so khớp, phát hiện bản ghi trùng qua fuzzy/semantic matching, đề xuất gộp thành golden record, giải thích lý do khớp và duy trì bản ghi master; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL data steward duyệt từng cặp gộp nghi ngờ trước khi hợp nhất; governance giữ nguồn gốc & khả năng tách lại, audit gộp; độ chính xác matching (precision/recall); hiệu năng blocking để so khớp hiệu quả trên khối lớn, chi phí kiểm soát. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM + embedding matching
• LangGraph agent (blocking → pairwise match → cluster → golden record)
• recordlinkage/dedupe/Splink
• vector DB (embedding tên/địa chỉ)
• warehouse
• backend FastAPI
• frontend React + review UI
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark truy vấn dữ liệu doanh nghiệp độ khó cao BIRD-SQL (có dữ liệu nhiễu), Spider 2.0 (Enterprise dbt/warehouse workflows) và TPC-H / TPC-DS / Olist Warehouse.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Steward/Viewer), kết nối dữ liệu → agent phát hiện cặp trùng + độ tin cậy + giải thích → HITL duyệt gộp → sinh golden record.

Nâng cao:
• multi-agent (agent embedding + agent rule kết hợp quyết định), eval đo precision/recall/F1 trên tập gán nhãn, blocking tối ưu, học ngưỡng khớp từ phản hồi steward, xử lý tách/gộp lại
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-18] AI Agent phát hiện Data Drift & giám sát dữ liệu cho mô hình ML

### 📝 Mô tả đề tài
📍 Thực trạng: Mô hình ML của doanh nghiệp giảm chất lượng âm thầm do phân phối dữ liệu đầu vào thay đổi mà không ai phát hiện kịp. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent giám sát feature/label theo thời gian, phát hiện data drift & concept drift bằng thống kê, chẩn đoán feature nào lệch & nguyên nhân, cảnh báo và đề xuất hành động (retrain, sửa nguồn); đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL ML engineer duyệt trước khi kích hoạt retrain/hành động; governance chỉ đọc feature store & metadata; độ chính xác phát hiện drift (giảm cảnh báo giả); hiệu năng giám sát định kỳ, chi phí tính toán kiểm soát. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM diễn giải & chẩn đoán
• LangGraph agent (monitor → detect drift → diagnose → recommend)
• Evidently/scipy (KS, PSI)
• feature store (Feast)
• warehouse
• vector DB lịch sử drift
• backend FastAPI
• frontend Next.js + Recharts
• scheduler Airflow
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark phát hiện bất thường chuỗi thời gian NAB (Numenta Anomaly Benchmark), đối sánh thực thể Febrl/Splink và bộ dữ liệu nhận diện PII Microsoft Presidio.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (ML Engineer/Viewer), giám sát dataset feature → phát hiện drift + biểu đồ + feature lệch → cảnh báo, HITL duyệt hành động.

Nâng cao:
• multi-agent (agent chẩn đoán nguyên nhân drift từ lineage/nguồn), eval đo độ chính xác phát hiện drift trên dữ liệu mô phỏng, tự đề xuất & (khi duyệt) trigger retrain, ưu tiên cảnh báo theo tác động
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-19] AI Agent trợ lý Data Governance & tra cứu chính sách dữ liệu

### 📝 Mô tả đề tài
📍 Thực trạng: Chính sách quản trị dữ liệu (phân loại, lưu trữ, tuân thủ) nằm rải rác trong nhiều tài liệu, nhân viên không biết dataset của mình phải tuân quy định nào. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tra cứu chính sách bằng NL, gắn chính sách phù hợp cho từng dataset dựa trên metadata & phân loại, kiểm tra mức tuân thủ hiện tại, cảnh báo vi phạm (giữ dữ liệu quá hạn, thiếu phân loại) và hướng dẫn khắc phục; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL governance lead phê duyệt gán nhãn chính sách & kế hoạch khắc phục; governance trích dẫn nguồn chính sách chính xác, không bịa; độ chính xác ánh xạ chính sách-dataset; hiệu năng RAG trên kho tài liệu lớn, chi phí kiểm soát. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM + RAG
• LlamaIndex + vector DB (Qdrant) index tài liệu chính sách
• LangGraph agent (retrieve policy → map to dataset → check compliance → guide)
• warehouse metadata
• backend FastAPI
• frontend Next.js
• deploy Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark phát hiện bất thường chuỗi thời gian NAB (Numenta Anomaly Benchmark), đối sánh thực thể Febrl/Splink và bộ dữ liệu nhận diện PII Microsoft Presidio.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Governance Lead/Employee), hỏi chính sách NL trả lời có trích nguồn → gán chính sách cho dataset → kiểm tra tuân thủ, HITL duyệt gán nhãn.

Nâng cao:
• multi-agent (agent kiểm tra tuân thủ tự động theo lịch), eval đo độ chính xác trả lời có trích nguồn & ánh xạ chính sách, phát hiện dataset quá hạn lưu trữ, sinh báo cáo tuân thủ định kỳ
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---

## [DATA-20] AI Agent điều phối yêu cầu dữ liệu (Data Request Intake & Triage)

### 📝 Mô tả đề tài
📍 Thực trạng: Đội Dữ liệu tập trung nhận hàng trăm yêu cầu (thêm dataset, sửa pipeline, cấp báo cáo) qua nhiều kênh, phân loại & ưu tiên thủ công gây tồn đọng. Trong kho dữ liệu thực tế của doanh nghiệp, schema thường gồm hàng chục bảng phức tạp, tên cột viết tắt, dữ liệu bẩn/trôi lệch (drift) và định nghĩa chỉ số dễ bị hiểu khác nhau giữa các phòng ban.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tiếp nhận yêu cầu bằng NL, tự phân loại loại việc, làm rõ thông tin thiếu qua hội thoại, kiểm tra xem đã có dataset/báo cáo sẵn (tránh trùng), ước lượng độ ưu tiên/công sức, định tuyến tới đúng team và theo dõi trạng thái; đồng thời đảm bảo tính nhất quán với tầng định nghĩa ngữ nghĩa (semantic layer), kết hợp phân tích cấu trúc truy vấn/dòng chảy dữ liệu (AST/lineage) và kiểm định thống kê xác định để tự động phát hiện – xử lý sai lệch dữ liệu và giải thích nguyên nhân biến động.

🔒 Ràng buộc: HITL trưởng nhóm duyệt phân loại & ưu tiên trước khi giao việc; governance chỉ gợi ý dựa trên catalog trong quyền, log yêu cầu; độ chính xác phân loại & định tuyến; hiệu năng xử lý nhiều yêu cầu, chi phí kiểm soát. Mọi truy vấn SQL/quy tắc biến đổi dữ liệu phải qua bước kiểm tra cú pháp, phân quyền (RBAC/RLS) và ước lượng chi phí quét xác định bằng code trước khi thực thi; mọi con số diễn giải phải khớp 100% với kết quả truy vấn.

### 🛠️ Tech Stack
• LLM
• LangGraph agent (intake → clarify → dedupe check → classify → prioritize → route)
• RAG catalog (LlamaIndex + vector DB) tìm tài nguyên sẵn có
• backend FastAPI
• frontend Next.js (kanban)
• tích hợp Jira/Slack API
• deploy Docker + Cloud Run.
• Dữ liệu & benchmark thực tế tham chiếu: Chuẩn siêu dữ liệu mở OpenLineage, DataHub / OpenMetadata schemas và các dự án mẫu dbt-core đa tầng kèm lịch sử git/log lỗi pipeline.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web deploy, 2 vai trò (Requester/Team Lead), yêu cầu NL → agent làm rõ + phân loại + kiểm tra trùng + gợi ý ưu tiên & định tuyến, HITL lead duyệt & giao.

Nâng cao:
• multi-agent (agent tra catalog phát hiện tài nguyên đã tồn tại + agent ước lượng công sức), eval đo độ chính xác phân loại & định tuyến trên tập gán nhãn, tự động tạo ticket, học ưu tiên từ lịch sử
• Kết hợp phân tích tĩnh cấu trúc dữ liệu (SQL AST / Schema Lineage / Kiểm định thống kê) với suy luận đa tác tử trên bộ benchmark thực tế phức tạp, mở rộng các tính năng khai thác và quản trị dữ liệu tự phục vụ cho doanh nghiệp.

---
