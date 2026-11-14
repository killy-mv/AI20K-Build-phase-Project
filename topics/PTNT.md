# Lĩnh vực: PTNT - Kiến trúc & Tích hợp nền tảng ứng dụng doanh nghiệp

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `PTNT-01` | [AI Agent Concierge điều hướng dịch vụ cho siêu ứng dụng của doanh nghiệp](#ptnt-01) |
| `PTNT-02` | [AI Agent orchestrate đa dịch vụ hoàn thành tác vụ liên hoàn (đặt nhà → xe → dịch vụ)](#ptnt-02) |
| `PTNT-03` | [AI Agent tích hợp & tự ánh xạ (mapping) API giữa các hệ thống doanh nghiệp](#ptnt-03) |
| `PTNT-04` | [AI Agent tự sinh & kiểm thử API contract / integration test](#ptnt-04) |
| `PTNT-05` | [AI Agent trợ lý SSO & quản lý danh tính người dùng hợp nhất](#ptnt-05) |
| `PTNT-06` | [AI Agent tổng hợp & cá nhân hóa thông báo đa dịch vụ](#ptnt-06) |
| `PTNT-07` | [AI Agent Dev Portal hỗ trợ nhà phát triển mini-app trong siêu ứng dụng của doanh nghiệp](#ptnt-07) |
| `PTNT-08` | [AI Agent giám sát & tự chẩn đoán lỗi tích hợp giữa các dịch vụ](#ptnt-08) |
| `PTNT-09` | [AI Agent quản lý & tra cứu tài liệu kiến trúc / ADR](#ptnt-09) |
| `PTNT-10` | [AI Agent đề xuất & rà soát (review) thiết kế kiến trúc hệ thống](#ptnt-10) |
| `PTNT-11` | [AI Agent điều phối luồng nghiệp vụ liên phòng ban (BPM orchestration)](#ptnt-11) |
| `PTNT-12` | [AI Agent trợ lý migration & nâng cấp hệ thống](#ptnt-12) |
| `PTNT-13` | [AI Agent quản lý cấu hình & feature flag bằng ngôn ngữ tự nhiên](#ptnt-13) |
| `PTNT-14` | [AI Agent chuẩn hóa & xây catalog API toàn tập đoàn](#ptnt-14) |
| `PTNT-15` | [AI Agent hỗ trợ khách hàng xuyên dịch vụ (Unified Support)](#ptnt-15) |
| `PTNT-16` | [AI Agent tối ưu hành trình người dùng trong siêu ứng dụng](#ptnt-16) |
| `PTNT-17` | [AI Agent điều phối ví & thanh toán hợp nhất xuyên dịch vụ](#ptnt-17) |
| `PTNT-18` | [AI Agent quản lý rate limit, quota API & chiến lược fallback](#ptnt-18) |
| `PTNT-19` | [AI Agent thiết kế & sinh khung mini-app từ mô tả nghiệp vụ](#ptnt-19) |
| `PTNT-20` | [AI Agent điều phối ứng phó sự cố (incident response) tích hợp](#ptnt-20) |

---

## [PTNT-01] AI Agent Concierge điều hướng dịch vụ cho siêu ứng dụng của doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: siêu ứng dụng của doanh nghiệp hợp nhất hàng chục dịch vụ doanh nghiệp (doanh nghiệp bất động sản, doanh nghiệp ô tô, hệ thống y tế / bệnh viện, dịch vụ gọi xe của doanh nghiệp, thanh toán, mua sắm...) khiến người dùng bối rối, không biết vào đâu để hoàn thành nhu cầu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent 'concierge' hiểu ý định người dùng bằng ngôn ngữ tự nhiên, tự lập kế hoạch, tra cứu catalog dịch vụ, gọi đúng mini-app/endpoint và deep-link người dùng tới màn hình cụ thể; khi mơ hồ phải hỏi lại và xác nhận; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL xác nhận trước khi điều hướng tới hành động nhạy cảm (thanh toán, hủy đơn); định danh qua SSO, chỉ gợi ý dịch vụ người dùng có quyền; độ chính xác intent ≥85%, có fallback khi hiểu sai; độ trễ phản hồi <3s, cảnh báo khi vượt token/quota LLM. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM (GPT-4o/Claude qua API)
• LangGraph điều phối agent + tool-calling
• OpenAPI/Service Catalog làm registry dịch vụ
• vector DB (Qdrant/pgvector) cho semantic routing intent→dịch vụ
• backend FastAPI (Python)
• API gateway (Kong/APISIX) mô phỏng các mini-app
• frontend React/Next.js + Tailwind
• Auth qua Keycloak (OIDC SSO)
• deploy Docker trên Render/Railway/Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy online, đăng nhập SSO, ≥2 vai trò (người dùng cuối / quản trị catalog)
• agent nhận yêu cầu NL, lập kế hoạch, chọn dịch vụ đúng và deep-link, có memory hội thoại, hỏi lại khi mơ hồ, hiển thị lý do gợi ý.

Nâng cao:
• Dashboard quản trị đo tỉ lệ điều hướng đúng, học từ phản hồi (thumbs up/down), gợi ý cá nhân hóa theo lịch sử, xử lý đa ý định trong một câu, cảnh báo & degrade khi LLM quá tải
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-02] AI Agent orchestrate đa dịch vụ hoàn thành tác vụ liên hoàn (đặt nhà → xe → dịch vụ)

### 📝 Mô tả đề tài
📍 Thực trạng: Một nhu cầu thực tế (chuyển tới căn hộ doanh nghiệp bất động sản mới) đòi hỏi nhiều dịch vụ rời rạc: thuê/mua BĐS, đặt xe doanh nghiệp dọn nhà, đăng ký gói khám hệ thống y tế / bệnh viện, kích hoạt ví thanh toán — người dùng phải thao tác thủ công qua nhiều app.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent điều phối (orchestrator) tự phân rã mục tiêu thành các bước, gọi tuần tự/song song nhiều API dịch vụ, truyền dữ liệu giữa các bước, xử lý phụ thuộc và rollback khi một bước thất bại; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL duyệt từng bước tốn tiền trước khi thực thi; bảo mật token dịch vụ theo scope người dùng; đảm bảo tính nhất quán (saga/compensation) khi lỗi giữa chừng; độ trễ chấp nhận cho luồng dài, có tiến trình hiển thị realtime. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM + LangGraph (state machine cho luồng nhiều bước
• checkpointing)
• OpenAPI specs cho 4-5 dịch vụ giả lập
• saga orchestration tự viết
• message queue (RabbitMQ/Redis Streams) cho bước bất đồng bộ
• backend FastAPI/Node
• PostgreSQL lưu trạng thái saga
• frontend React với timeline tiến trình
• WebSocket cập nhật realtime
• deploy Docker Compose trên cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập, ≥2 vai trò (khách hàng / admin dịch vụ)
• agent lập kế hoạch nhiều bước, gọi ≥3 dịch vụ nối tiếp, truyền dữ liệu giữa bước, HITL duyệt, hiển thị tiến trình từng bước, xử lý lỗi cơ bản.

Nâng cao:
• Cơ chế compensation/rollback khi bước lỗi, chạy song song bước độc lập, tạm dừng/tiếp tục luồng (resume từ checkpoint), gợi ý điều chỉnh kế hoạch khi ràng buộc thay đổi, cảnh báo giới hạn chi phí
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-03] AI Agent tích hợp & tự ánh xạ (mapping) API giữa các hệ thống doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Khi kết nối hai hệ thống (ví dụ CRM doanh nghiệp công nghệ và hệ thống đặt lịch hệ thống y tế / bệnh viện), kỹ sư phải đọc tài liệu API hai bên rồi viết tay lớp mapping trường dữ liệu, tốn thời gian và dễ sai. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent đọc OpenAPI/schema của hệ nguồn và hệ đích, tự đề xuất ánh xạ trường (field mapping), phát hiện lệch kiểu/định dạng, sinh mã transform và kiểm thử với dữ liệu mẫu; con người rà soát và duyệt; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL bắt buộc duyệt mapping trước khi áp dụng; không để lộ dữ liệu nhạy cảm (PII) khi suy luận; độ chính xác mapping có điểm tin cậy, cảnh báo trường mơ hồ; hiệu năng khi schema lớn hàng trăm trường. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM cho suy luận ngữ nghĩa trường
• LangGraph cho luồng phân tích→đề xuất→kiểm thử
• parser OpenAPI/JSON Schema
• vector DB lưu embeddings tên/mô tả trường để gợi ý tương đồng
• backend FastAPI sinh code transform (Python/JS)
• sandbox chạy thử mapping
• PostgreSQL lưu phiên bản mapping
• frontend React dạng bảng kéo-thả xác nhận mapping
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, ≥2 vai trò (kỹ sư tích hợp / reviewer)
• upload 2 OpenAPI, agent đề xuất field mapping kèm độ tin cậy, sinh transform và chạy thử với dữ liệu mẫu, HITL duyệt.

Nâng cao:
• Phát hiện & xử lý lệch kiểu/enum/định dạng ngày, gợi ý transform phức tạp (concat, lookup), versioning mapping, tự sinh test regression, cảnh báo khi schema đích thay đổi phá vỡ mapping cũ
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-04] AI Agent tự sinh & kiểm thử API contract / integration test

### 📝 Mô tả đề tài
📍 Thực trạng: Các mini-app trong siêu ứng dụng của doanh nghiệp tích hợp qua API nhưng thiếu bộ integration test và contract test đầy đủ, dẫn tới lỗi tích hợp chỉ phát hiện khi lên production. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent đọc OpenAPI của một dịch vụ, tự sinh bộ test case (happy path, biên, lỗi, xác thực), thực thi test thật với môi trường sandbox, phân tích kết quả và đề xuất sửa; tạo contract test giữa consumer-provider; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL duyệt test có tác dụng phụ (POST/DELETE); chạy trên môi trường an toàn không đụng dữ liệu thật; độ bao phủ có báo cáo rõ, cảnh báo endpoint chưa test; giới hạn thời gian/song song để tránh quá tải dịch vụ. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM sinh test case
• LangGraph điều phối vòng sinh→chạy→phân tích→lặp
• OpenAPI parser
• framework test (pytest + schemathesis / Pact cho contract test)
• runner sandbox
• message queue cho chạy test song song
• backend FastAPI
• PostgreSQL lưu kết quả
• frontend React dashboard coverage & báo cáo lỗi
• deploy Docker + CI (GitHub Actions).
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập, ≥2 vai trò (QA/dev / xem báo cáo)
• nhập OpenAPI, agent sinh & chạy test, hiển thị pass/fail, coverage endpoint, HITL duyệt test ghi dữ liệu.

Nâng cao:
• Contract test consumer-provider, tự phân tích nguyên nhân fail và đề xuất fix, sinh test biên/fuzz thông minh, phát hiện breaking change giữa 2 phiên bản spec, tích hợp gate CI, cảnh báo rate limit dịch vụ
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-05] AI Agent trợ lý SSO & quản lý danh tính người dùng hợp nhất

### 📝 Mô tả đề tài
📍 Thực trạng: Người dùng siêu ứng dụng của doanh nghiệp có nhiều tài khoản rời rạc trên từng dịch vụ doanh nghiệp; việc hợp nhất định danh, cấp/thu quyền, xử lý yêu cầu truy cập chéo dịch vụ rất phức tạp cho cả người dùng lẫn admin. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hỗ trợ quản trị danh tính hợp nhất: hiểu yêu cầu NL ('cho tài khoản này quyền đặt xe nhưng cấm thanh toán'), tra cứu và diễn giải policy/role, đề xuất thay đổi quyền, phát hiện quyền dư thừa/xung đột và liên kết các danh tính; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL bắt buộc cho mọi thay đổi quyền; tuân thủ least-privilege, ghi audit log đầy đủ; độ chính xác cao khi diễn giải policy, không tự cấp quyền vượt phạm vi; hiệu năng khi tổ chức lớn nhiều nghìn role. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM cho hiểu yêu cầu & diễn giải policy
• LangGraph cho luồng đề xuất→duyệt→áp dụng
• Keycloak/OIDC làm IdP
• OPA/RBAC engine cho policy
• vector DB tra cứu chính sách
• backend FastAPI gọi Keycloak Admin API
• PostgreSQL + audit log
• frontend React quản trị danh tính & role
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập SSO thật (Keycloak), ≥2 vai trò (admin IAM / người dùng)
• agent nhận yêu cầu NL về quyền, tra cứu role hiện tại, đề xuất thay đổi, HITL duyệt rồi áp dụng, ghi audit.

Nâng cao:
• Phát hiện quyền dư thừa/xung đột & SoD, liên kết nhiều danh tính thành profile hợp nhất, giải thích 'vì sao user bị từ chối', mô phỏng tác động trước khi áp dụng, cảnh báo thay đổi rủi ro cao
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-06] AI Agent tổng hợp & cá nhân hóa thông báo đa dịch vụ

### 📝 Mô tả đề tài
📍 Thực trạng: Người dùng siêu ứng dụng của doanh nghiệp bị 'ngập' thông báo rời rạc từ nhiều dịch vụ (nhắc lịch khám hệ thống y tế / bệnh viện, trạm sạc xe điện, khuyến mãi mua sắm, hóa đơn ví...), gây nhiễu và bỏ lỡ thông tin quan trọng. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tổng hợp thông báo từ nhiều nguồn, khử trùng lặp, phân loại độ ưu tiên theo ngữ cảnh người dùng, gom nhóm và tóm tắt thành một digest cá nhân hóa, đề xuất hành động (đặt lịch, thanh toán) với HITL; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL trước khi agent thay người dùng thực hiện hành động; tôn trọng quyền riêng tư & tùy chọn kênh; độ chính xác phân loại ưu tiên, không được nén mất thông báo khẩn; xử lý realtime luồng sự kiện lớn với độ trễ thấp. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM cho phân loại/tóm tắt/xếp ưu tiên
• LangGraph điều phối
• message queue (Kafka/Redis Streams) thu sự kiện đa dịch vụ
• vector DB cho khử trùng lặp ngữ nghĩa
• backend FastAPI
• PostgreSQL lưu tùy chọn & lịch sử
• frontend React (inbox hợp nhất + digest)
• push/email (Firebase/SMTP)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập, ≥2 vai trò (người dùng / admin cấu hình nguồn)
• agent thu thông báo từ ≥3 nguồn giả lập, khử trùng lặp, xếp ưu tiên, tạo digest cá nhân hóa, đề xuất hành động có HITL.

Nâng cao:
• Học tùy chọn theo hành vi (mở/bỏ qua), chọn kênh & thời điểm tối ưu, phát hiện thông báo khẩn vượt lịch im lặng, gom nhóm theo 'sự kiện đời sống', cảnh báo khi luồng sự kiện tăng đột biến
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-07] AI Agent Dev Portal hỗ trợ nhà phát triển mini-app trong siêu ứng dụng của doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Nhiều đội trong hệ sinh thái muốn xây mini-app tích hợp vào siêu ứng dụng của doanh nghiệp nhưng phải tự đọc tài liệu SDK, quy chuẩn tích hợp, đăng ký scope, xin key... khiến onboarding chậm. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent trong dev portal trả lời câu hỏi kỹ thuật dựa trên tài liệu nội bộ (RAG), sinh code khung mini-app, hướng dẫn từng bước đăng ký/cấp credential, tự kiểm tra manifest mini-app có tuân chuẩn không và đề xuất sửa; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL khi cấp credential/scope thật; chỉ trả lời trong phạm vi tài liệu, trích nguồn, không bịa; độ chính xác kỹ thuật cao; kiểm soát rate limit gọi LLM khi nhiều dev dùng đồng thời. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM + RAG trên tài liệu SDK/guideline (vector DB Qdrant/pgvector)
• LangGraph cho luồng hỏi-đáp + tool (validate manifest
• tạo credential)
• backend FastAPI
• code scaffolding template
• JSON Schema validator cho manifest
• PostgreSQL
• frontend React (chat + wizard onboarding + validator)
• deploy Docker/Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Portal deploy, đăng nhập, ≥2 vai trò (dev mini-app / quản trị portal)
• agent trả lời từ tài liệu có trích nguồn, sinh scaffold mini-app, wizard đăng ký với HITL cấp key, validate manifest.

Nâng cao:
• Tự phát hiện vi phạm guideline trong code mini-app và gợi ý fix, chấm điểm 'độ sẵn sàng tích hợp', mô phỏng sandbox chạy thử mini-app, cập nhật tri thức khi tài liệu đổi, cảnh báo giới hạn quota
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-08] AI Agent giám sát & tự chẩn đoán lỗi tích hợp giữa các dịch vụ

### 📝 Mô tả đề tài
📍 Thực trạng: Khi một luồng liên dịch vụ trong siêu ứng dụng của doanh nghiệp lỗi (ví dụ thanh toán ví không xác nhận với đơn mua sắm), kỹ sư phải lần theo log nhiều hệ thống để tìm nguyên nhân, mất nhiều giờ. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát telemetry/trace/log liên dịch vụ, phát hiện bất thường, tự chẩn đoán điểm lỗi (dịch vụ nào, do timeout/schema/quyền), tương quan sự kiện qua trace ID và đề xuất/thực thi hành động khắc phục (retry, ngắt mạch); đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL trước hành động khắc phục ảnh hưởng production; không lộ dữ liệu nhạy cảm trong log; độ chính xác chẩn đoán có mức tin cậy, tránh cảnh báo giả; xử lý realtime độ trễ thấp trên luồng log lớn. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM cho chẩn đoán từ log/trace
• LangGraph cho luồng phát hiện→tương quan→chẩn đoán→hành động
• OpenTelemetry + Jaeger tracing
• log store (Loki/Elasticsearch)
• message queue thu telemetry
• vector DB cho similar-incident retrieval
• backend FastAPI
• PostgreSQL lưu incident
• frontend React dashboard trace & timeline
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập, ≥2 vai trò (SRE/kỹ sư / xem báo cáo)
• agent nhận log/trace từ ≥3 dịch vụ giả lập, phát hiện lỗi tích hợp, tương quan qua trace ID, chỉ ra điểm lỗi & nguyên nhân, đề xuất fix có HITL.

Nâng cao:
• Tự thực thi remediation (retry/circuit breaker) sau duyệt, học từ incident cũ để chẩn đoán nhanh, dự đoán lỗi lan truyền, sinh postmortem tự động, cảnh báo khi tần suất lỗi vượt ngưỡng
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-09] AI Agent quản lý & tra cứu tài liệu kiến trúc / ADR

### 📝 Mô tả đề tài
📍 Thực trạng: Kho tài liệu kiến trúc và ADR (Architecture Decision Records) của khối PTNT rải rác, khó tra cứu 'vì sao chọn công nghệ X', dẫn tới quyết định lặp lại hoặc mâu thuẫn. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent làm 'trí nhớ kiến trúc': trả lời câu hỏi dựa trên ADR/diagram (RAG có trích nguồn), phát hiện quyết định mâu thuẫn/lỗi thời, hỗ trợ soạn ADR mới đúng chuẩn từ hội thoại, và liên kết ADR tới thành phần hệ thống liên quan; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL duyệt trước khi ban hành/đánh dấu ADR superseded; kiểm soát quyền đọc theo phân loại tài liệu; độ chính xác cao, luôn trích dẫn, không suy diễn; hiệu năng tra cứu trên kho lớn. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM + RAG (vector DB pgvector/Qdrant) trên ADR (Markdown) & diagram
• LangGraph cho hỏi-đáp + tool phát hiện mâu thuẫn
• graph store (Neo4j) liên kết ADR↔thành phần
• backend FastAPI
• PostgreSQL
• frontend React (search
• viewer ADR
• trình soạn ADR có gợi ý)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, ≥2 vai trò (kiến trúc sư / thành viên đọc)
• agent trả lời từ ADR có trích nguồn, memory hội thoại, hỗ trợ soạn ADR mới theo template, HITL duyệt ban hành.

Nâng cao:
• Phát hiện ADR mâu thuẫn/lỗi thời & đề xuất supersede, đồ thị liên kết quyết định↔hệ thống, tóm tắt 'lý do lịch sử' cho một thành phần, cảnh báo khi quyết định mới đụng ADR cũ
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-10] AI Agent đề xuất & rà soát (review) thiết kế kiến trúc hệ thống

### 📝 Mô tả đề tài
📍 Thực trạng: Đội PTNT thường xuyên review đề xuất thiết kế (design doc) cho dịch vụ mới trong siêu ứng dụng của doanh nghiệp nhưng phụ thuộc kinh nghiệm cá nhân, thiếu checklist nhất quán về khả năng mở rộng, bảo mật, chi phí. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent đọc design doc/diagram, đối chiếu nguyên tắc kiến trúc & best practice, chỉ ra rủi ro (điểm nghẽn, SPOF, thiếu bảo mật), đề xuất phương án thay thế và ước lượng đánh đổi; sinh bản nháp thiết kế từ yêu cầu NL; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL — agent chỉ tư vấn, con người quyết định cuối; tuân thủ nguyên tắc kiến trúc nội bộ (RAG), không bịa; độ chính xác & khả năng giải thích rõ đánh đổi; hiệu năng với tài liệu dài kèm sơ đồ. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM (đa mô hình) + RAG nguyên tắc kiến trúc nội bộ
• LangGraph cho luồng phân tích→chấm điểm→đề xuất
• parser diagram (Mermaid/C4)
• vector DB
• backend FastAPI
• PostgreSQL
• frontend React (upload design doc
• báo cáo review có anchor
• sinh diagram C4)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, ≥2 vai trò (kiến trúc sư / người nộp thiết kế)
• agent nhận design doc, rà soát theo checklist, liệt kê rủi ro & đề xuất kèm lý do trích nguồn, HITL quyết định.

Nâng cao:
• Sinh bản nháp kiến trúc + diagram C4 từ yêu cầu NL, so sánh nhiều phương án theo tiêu chí (chi phí/độ trễ/mở rộng), phát hiện anti-pattern, ước lượng tải & điểm nghẽn, cảnh báo lệch nguyên tắc bắt buộc
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-11] AI Agent điều phối luồng nghiệp vụ liên phòng ban (BPM orchestration)

### 📝 Mô tả đề tài
📍 Thực trạng: Các quy trình liên phòng ban trong hệ sinh thái doanh nghiệp (ví dụ bàn giao căn hộ: pháp lý → tài chính → kỹ thuật → CSKH) chạy qua nhiều hệ thống và email thủ công, khó theo dõi, hay tắc ở một khâu. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent điều phối quy trình nghiệp vụ end-to-end: hiểu định nghĩa quy trình, phân công task tới đúng vai trò/hệ thống, theo dõi SLA, tự nhắc/escalate khi trễ, và cho phép người dùng thao tác bằng NL ('duyệt bước tài chính'); đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL tại các cổng phê duyệt bắt buộc; phân quyền theo vai trò, audit mọi chuyển trạng thái; độ chính xác định tuyến task; hiệu năng theo dõi nhiều tiến trình song song với cảnh báo SLA. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM cho hiểu lệnh NL & phân loại
• LangGraph điều phối state machine quy trình
• BPM engine (Camunda/Temporal) hoặc tự xây saga
• message queue cho task bất đồng bộ
• backend FastAPI
• PostgreSQL lưu process instance + audit
• frontend React (kanban quy trình
• timeline SLA)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập, ≥3 vai trò (ví dụ pháp lý/tài chính/CSKH)
• agent chạy 1 quy trình đa bước liên phòng ban, phân công task, HITL phê duyệt tại cổng, theo dõi trạng thái, audit log.

Nâng cao:
• Tự escalate khi trễ SLA, gợi ý tối ưu quy trình từ dữ liệu chạy thật, xử lý nhánh điều kiện & song song, mô phỏng 'what-if' thay đổi luồng, cảnh báo tắc nghẽn & bottleneck
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-12] AI Agent trợ lý migration & nâng cấp hệ thống

### 📝 Mô tả đề tài
📍 Thực trạng: Việc migrate một dịch vụ cũ sang kiến trúc mới (đổi DB, nâng version API, tách monolith) trong hệ sinh thái doanh nghiệp phức tạp, rủi ro cao, phụ thuộc kiến thức của vài người. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hỗ trợ migration: phân tích hệ hiện trạng (schema, endpoint, phụ thuộc), lập kế hoạch migrate theo giai đoạn, sinh script chuyển đổi & rollback, chạy kiểm thử tương thích và theo dõi tiến độ, cảnh báo breaking change; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL bắt buộc trước mỗi bước ghi/đổi dữ liệu thật; chạy trên bản sao/sandbox, có rollback; độ chính xác cao khi sinh script, kiểm thử trước áp dụng; hiệu năng với dữ liệu lớn & cảnh báo downtime. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM sinh & phân tích script
• LangGraph cho luồng phân tích→plan→sinh→test→rollback
• công cụ migration (Alembic/Flyway)
• DB (PostgreSQL/MySQL) nguồn-đích sandbox
• diff schema
• message queue cho batch lớn
• backend FastAPI
• frontend React (kế hoạch migrate
• tiến độ
• diff)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập, ≥2 vai trò (kỹ sư migrate / duyệt)
• agent phân tích hệ nguồn, lập kế hoạch nhiều giai đoạn, sinh script migrate + rollback, chạy thử trên sandbox, HITL duyệt từng bước.

Nâng cao:
• Phát hiện breaking change & phụ thuộc ẩn, migrate không downtime (dual-write/backfill), tự sinh test tương thích, ước lượng thời gian & rủi ro từng bước, cảnh báo khi dữ liệu lệch sau migrate
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-13] AI Agent quản lý cấu hình & feature flag bằng ngôn ngữ tự nhiên

### 📝 Mô tả đề tài
📍 Thực trạng: siêu ứng dụng của doanh nghiệp có nhiều feature flag và cấu hình theo môi trường/đối tượng người dùng; thay đổi thủ công dễ nhầm và khó biết tác động (ai đang bật, ảnh hưởng dịch vụ nào). Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent cho phép quản trị cấu hình/flag bằng NL ('bật tính năng ví trả góp cho 10% người dùng Hà Nội'), diễn giải thành thay đổi cụ thể, phân tích tác động & phụ thuộc, đề xuất chiến lược rollout và tự rollback khi có bất thường; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL bắt buộc trước khi áp dụng thay đổi production; phân quyền theo môi trường, audit đầy đủ; độ chính xác diễn giải lệnh NL, xác nhận lại khi mơ hồ; hiệu năng cập nhật flag realtime, cảnh báo thay đổi rủi ro. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM diễn giải lệnh NL→cấu hình
• LangGraph cho luồng diễn giải→phân tích tác động→duyệt→áp dụng
• feature-flag service (Unleash/tự xây)
• backend FastAPI
• PostgreSQL + audit
• Redis cache flag realtime
• frontend React (bảng flag
• diff thay đổi
• mô phỏng rollout)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập, ≥2 vai trò (admin cấu hình / xem)
• agent nhận lệnh NL, diễn giải thành thay đổi flag/config cụ thể, hiển thị diff & tác động, HITL duyệt rồi áp dụng, audit.

Nâng cao:
• Chiến lược rollout theo % / phân khúc, phân tích phụ thuộc giữa các flag, tự rollback khi metric xấu đi, phát hiện flag 'chết' cần dọn, cảnh báo xung đột cấu hình giữa môi trường
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-14] AI Agent chuẩn hóa & xây catalog API toàn tập đoàn

### 📝 Mô tả đề tài
📍 Thực trạng: Hàng trăm API rải rác khắp các đơn vị trong doanh nghiệp không theo chuẩn chung (đặt tên, versioning, tài liệu thiếu), khó tái sử dụng và dễ trùng lặp. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent quét & thu thập OpenAPI từ nhiều nguồn, tự phân loại/gắn thẻ theo domain, phát hiện API trùng chức năng, chấm điểm tuân thủ chuẩn thiết kế (naming, lỗi, bảo mật) và đề xuất chuẩn hóa; xây catalog tìm kiếm ngữ nghĩa; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL duyệt trước khi công bố API vào catalog chính thức; kiểm soát quyền xem theo phân loại; độ chính xác phân loại & phát hiện trùng, có điểm tin cậy; hiệu năng khi index số lượng API lớn. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM cho phân loại/chấm điểm/tóm tắt API
• LangGraph cho luồng thu thập→phân tích→chuẩn hóa
• OpenAPI parser + linter (Spectral)
• vector DB cho semantic search & phát hiện trùng
• backend FastAPI
• PostgreSQL
• frontend React (catalog tìm kiếm
• trang API
• báo cáo tuân thủ)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, ≥2 vai trò (API steward / dev tra cứu)
• agent nạp nhiều OpenAPI, phân loại theo domain, chấm điểm tuân thủ chuẩn, tìm kiếm ngữ nghĩa, HITL duyệt publish.

Nâng cao:
• Phát hiện API trùng chức năng & đề xuất hợp nhất, tự sinh mô tả/ví dụ còn thiếu, theo dõi thay đổi version & breaking change, gợi ý API tái sử dụng cho use case mới, cảnh báo API vi phạm chuẩn bảo mật
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-15] AI Agent hỗ trợ khách hàng xuyên dịch vụ (Unified Support)

### 📝 Mô tả đề tài
📍 Thực trạng: Khách hàng gặp vấn đề liên quan nhiều dịch vụ (đơn mua sắm trừ ví nhưng chưa giao, đặt xe dịch vụ gọi xe của doanh nghiệp lỗi) phải liên hệ nhiều tổng đài, kể lại từ đầu. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hỗ trợ hợp nhất: hiểu vấn đề, truy vấn trạng thái qua API nhiều dịch vụ (đơn, ví, chuyến xe), tổng hợp bối cảnh, tự xử lý được thì thực thi (hoàn tiền, đặt lại) còn không thì chuyển agent người kèm tóm tắt; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL/handoff cho hành động tài chính & ca phức tạp; xác thực danh tính trước khi tra cứu dữ liệu cá nhân; độ chính xác cao, không hứa sai; độ trễ thấp, cảnh báo khi ngoài phạm vi xử lý tự động. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM + RAG (chính sách hỗ trợ) + tool-calling tra cứu đa dịch vụ
• LangGraph cho luồng phân loại→điều tra→giải quyết/handoff
• vector DB
• backend FastAPI gọi API dịch vụ giả lập (đơn/ví/xe)
• PostgreSQL lưu ticket + memory
• frontend React (chat khách + màn hình agent người)
• WebSocket
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập, ≥2 vai trò (khách hàng / nhân viên hỗ trợ)
• agent xác thực, truy vấn trạng thái ≥3 dịch vụ, tổng hợp bối cảnh, tự xử lý ca đơn giản có HITL, handoff kèm tóm tắt cho ca khó.

Nâng cao:
• Phát hiện & liên kết vấn đề chéo dịch vụ, đề xuất bồi hoàn theo chính sách, dự đoán ca cần escalate, tóm tắt & phân loại ticket tự động, đo CSAT và cảnh báo khi vượt giới hạn xử lý
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-16] AI Agent tối ưu hành trình người dùng trong siêu ứng dụng

### 📝 Mô tả đề tài
📍 Thực trạng: Nhiều người dùng siêu ứng dụng của doanh nghiệp bỏ dở giữa chừng ở các luồng liên dịch vụ (đăng ký gói, thanh toán, đặt dịch vụ) nhưng đội sản phẩm khó biết tắc ở đâu và vì sao. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích dữ liệu hành vi/analytics đa dịch vụ, phát hiện điểm rơi (drop-off), suy luận nguyên nhân, đề xuất tối ưu (rút gọn bước, gợi ý đúng lúc) và mô phỏng tác động; đồng thời điều hướng người dùng realtime khi phát hiện họ mắc kẹt; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL duyệt trước khi áp thay đổi hành trình thật; ẩn danh & tuân thủ quyền riêng tư khi phân tích hành vi; độ chính xác phân tích có bằng chứng số liệu; hiệu năng trên tập sự kiện lớn, độ trễ thấp cho gợi ý realtime. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM cho suy luận nguyên nhân & đề xuất
• LangGraph điều phối
• kho sự kiện analytics (ClickHouse/PostgreSQL)
• phân tích funnel
• vector DB cho pattern hành trình
• message queue thu event
• backend FastAPI
• frontend React (funnel viz
• gợi ý tối ưu
• mô phỏng)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập, ≥2 vai trò (product/analyst / xem)
• agent phân tích dữ liệu hành trình đa dịch vụ, chỉ ra điểm drop-off kèm số liệu, đề xuất tối ưu, HITL duyệt.

Nâng cao:
• Suy luận nguyên nhân đa yếu tố, mô phỏng tác động thay đổi (A/B what-if), điều hướng/nudge realtime khi user mắc kẹt, phân khúc hành trình theo persona, cảnh báo khi tỉ lệ hoàn thành sụt giảm
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-17] AI Agent điều phối ví & thanh toán hợp nhất xuyên dịch vụ

### 📝 Mô tả đề tài
📍 Thực trạng: Thanh toán trong siêu ứng dụng của doanh nghiệp trải nhiều dịch vụ (mua sắm, trạm sạc xe điện, viện phí hệ thống y tế / bệnh viện) với ví, thẻ, điểm thưởng, trả góp — người dùng khó chọn phương thức tối ưu và khó theo dõi chi tiêu hợp nhất.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent điều phối thanh toán: hiểu yêu cầu ('thanh toán viện phí, ưu tiên dùng điểm rồi ví'), chọn & phối hợp nhiều nguồn tiền, gọi API thanh toán các dịch vụ, đảm bảo giao dịch nhất quán, đối soát và tổng hợp chi tiêu; cảnh báo bất thường; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL/xác thực mạnh bắt buộc trước mọi giao dịch; bảo mật PCI-mindset, không lưu dữ liệu nhạy cảm; độ chính xác tuyệt đối về số tiền, idempotency chống trùng; độ trễ thấp, cảnh báo hạn mức & rủi ro gian lận. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM cho hiểu yêu cầu & chiến lược nguồn tiền
• LangGraph cho luồng saga thanh toán (reserve→confirm→compensate)
• API gateway tới payment services giả lập
• message queue đảm bảo idempotent
• backend FastAPI
• PostgreSQL (ledger + đối soát)
• frontend React (ví hợp nhất
• xác nhận
• lịch sử chi tiêu)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập + xác thực bước 2, ≥2 vai trò (người dùng / admin đối soát)
• agent chọn & phối hợp nguồn tiền, gọi thanh toán ≥2 dịch vụ với saga nhất quán, HITL xác nhận, tổng hợp chi tiêu.

Nâng cao:
• Gợi ý phương thức tối ưu (điểm/trả góp), compensation khi lỗi giữa chừng, đối soát tự động & phát hiện lệch, cảnh báo gian lận/vượt hạn mức, chia hóa đơn đa dịch vụ
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-18] AI Agent quản lý rate limit, quota API & chiến lược fallback

### 📝 Mô tả đề tài
📍 Thực trạng: Cổng API của siêu ứng dụng của doanh nghiệp phục vụ nhiều mini-app với hạn mức khác nhau; khi tải tăng hoặc một mini-app gọi quá mức, dịch vụ backend quá tải và lan lỗi. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát lưu lượng & quota theo thời gian thực, dự báo nguy cơ vượt hạn, tự đề xuất/điều chỉnh rate limit và chính sách throttle công bằng, chọn fallback (cache, degrade) khi dịch vụ quá tải, và giải thích quyết định; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL trước khi thay đổi chính sách limit production; công bằng giữa các consumer, không chặn nhầm dịch vụ ưu tiên; độ chính xác dự báo có ngưỡng tin cậy; xử lý realtime độ trễ cực thấp, cảnh báo trước khi cạn quota. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM cho phân tích & đề xuất chính sách
• LangGraph điều phối giám sát→dự báo→hành động
• API gateway (Kong/Envoy) áp rate limit
• Redis đếm token bucket
• message queue metrics
• time-series DB (Prometheus)
• backend FastAPI
• frontend React (dashboard lưu lượng/quota
• mô phỏng chính sách)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập, ≥2 vai trò (platform admin / consumer xem quota)
• agent giám sát lưu lượng realtime, cảnh báo nguy cơ vượt hạn, đề xuất điều chỉnh rate limit, HITL duyệt áp dụng qua gateway.

Nâng cao:
• Dự báo tải & tự scale limit, throttle công bằng theo ưu tiên, chọn fallback (cache/degrade) tự động, phát hiện consumer bất thường/lạm dụng, mô phỏng tác động chính sách trước khi áp
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-19] AI Agent thiết kế & sinh khung mini-app từ mô tả nghiệp vụ

### 📝 Mô tả đề tài
📍 Thực trạng: Các đơn vị muốn nhanh chóng có mini-app tích hợp siêu ứng dụng của doanh nghiệp nhưng thiếu nhân lực dựng khung ban đầu (UI, gọi API nền tảng, luồng SSO/ví). Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent nhận mô tả nghiệp vụ bằng NL, tự thiết kế luồng màn hình & mô hình dữ liệu, chọn API nền tảng phù hợp từ catalog, sinh mã khung mini-app tuân chuẩn tích hợp (SSO, ví, thông báo) và tự kiểm tra manifest; con người review & tinh chỉnh; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL duyệt thiết kế & code trước khi triển khai; sinh code tuân guideline bảo mật (không hardcode secret), scope tối thiểu; độ chính xác ánh xạ nghiệp vụ→API; hiệu năng sinh nhanh, cảnh báo khi yêu cầu vượt năng lực nền tảng. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM sinh thiết kế & code
• LangGraph cho luồng hiểu yêu cầu→thiết kế→chọn API→sinh→validate
• RAG trên catalog API & guideline (vector DB)
• template scaffolding (React mini-app)
• JSON Schema validator manifest
• sandbox preview
• backend FastAPI
• PostgreSQL
• frontend React (wizard + preview trực tiếp)
• deploy Docker/Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, ≥2 vai trò (dev / reviewer nền tảng)
• agent nhận mô tả NL, sinh thiết kế màn hình + chọn API từ catalog + sinh scaffold mini-app tích hợp SSO/ví, validate manifest, HITL duyệt, preview sandbox.

Nâng cao:
• Sinh mô hình dữ liệu & CRUD API, tự phát hiện vi phạm guideline và sửa, đề xuất tối ưu UX, lặp tinh chỉnh theo phản hồi NL, cảnh báo yêu cầu vượt phạm vi/scope nền tảng
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---

## [PTNT-20] AI Agent điều phối ứng phó sự cố (incident response) tích hợp

### 📝 Mô tả đề tài
📍 Thực trạng: Khi sự cố siêu ứng dụng của doanh nghiệp xảy ra (một dịch vụ tích hợp sập, độ trễ tăng vọt), quy trình ứng phó thủ công: tập hợp người, dò log, cập nhật trạng thái — chậm và thiếu phối hợp. Trong kiến trúc nền tảng hợp nhất nhiều dịch vụ của doanh nghiệp, các hệ thống thành phần thường có chuẩn dữ liệu không đồng nhất, độ trễ biến thiên và nguy cơ lỗi một phần (partial failure) khi thực hiện chuỗi giao dịch liên dịch vụ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent điều phối incident: phát hiện & phân loại mức độ, tự tạo 'war room', thu thập bối cảnh (metric/trace/deploy gần đây), gợi ý giả thuyết nguyên nhân & runbook, phối hợp hành động khắc phục và cập nhật status page, cuối cùng sinh postmortem; đồng thời đảm bảo tính nhất quán của giao dịch phân tán xuyên dịch vụ (mẫu thiết kế Saga và giao dịch bù trừ rollback khi một bước gặp sự cố), kiểm chứng tương thích hợp đồng API và phân tích lan truyền lỗi trên đồ thị phụ thuộc hệ thống.

🔒 Ràng buộc: HITL bắt buộc trước mọi hành động khắc phục production (restart, rollback); phân quyền theo vai trò on-call, audit hành động; độ chính xác phân loại mức độ & chẩn đoán có bằng chứng; xử lý realtime độ trễ thấp, cảnh báo leo thang khi sự cố kéo dài. Đảm bảo tính lũy đẳng (idempotency), kiểm soát phân quyền xuyên dịch vụ (SSO/RBAC) và khả năng hoàn tác an toàn (compensating rollback) khi xảy ra lỗi một phần trong chuỗi gọi công cụ.

### 🛠️ Tech Stack
• LLM cho phân loại & suy luận nguyên nhân
• LangGraph cho luồng phát hiện→triệu tập→chẩn đoán→khắc phục→postmortem
• OpenTelemetry/Prometheus + log store
• RAG runbook (vector DB)
• message queue alerts
• backend FastAPI
• PostgreSQL lưu incident timeline + audit
• frontend React (war room
• timeline
• status page)
• WebSocket realtime
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ benchmark hệ thống phân tán & gọi API quy mô lớn DeathStarBench / Google Online Boutique, ToolBench / API-Bank, chuẩn đặc tả OpenAPI 3.1 / AsyncAPI / CloudEvents và log OpenTelemetry.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập, ≥2 vai trò (on-call/IC / xem status)
• agent phát hiện & phân loại sự cố, tạo war room, thu thập metric/trace, gợi ý nguyên nhân & runbook, đề xuất khắc phục có HITL, cập nhật status page.

Nâng cao:
• Tự tương quan deploy gần đây với sự cố, thực thi remediation sau duyệt, tự leo thang khi kéo dài, sinh postmortem & action item, học từ incident cũ, cảnh báo khi sự cố lan sang dịch vụ khác
• Hiện thực hóa cơ chế đảm bảo an toàn giao dịch phân tán (Saga rollback / Contract validation / Blast-radius analysis) và kiểm thử khả năng chịu lỗi khi dịch vụ thành phần bị trễ hoặc ngắt kết nối.

---
