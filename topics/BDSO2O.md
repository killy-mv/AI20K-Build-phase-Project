# Lĩnh vực: BDSO2O - Bất động sản – Kinh doanh O2O

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `BDSO2O-01` | [LeadScorer AI Agent – Trợ lý chấm điểm & phân luồng lead khách mua nhà doanh nghiệp bất động sản](#bdso2o-01) |
| `BDSO2O-02` | [SalesMate AI Agent – Trợ lý tư vấn dự án & căn hộ theo thời gian thực cho sale](#bdso2o-02) |
| `BDSO2O-03` | [FollowUp AI Agent – Trợ lý tự động soạn kịch bản & nhắc nhở chăm sóc khách đa kênh](#bdso2o-03) |
| `BDSO2O-04` | [BookingBot AI Agent – Trợ lý đặt lịch xem nhà & giữ căn tự động](#bdso2o-04) |
| `BDSO2O-05` | [HomeMatch AI Agent – Trợ lý gợi ý căn hộ theo nhu cầu và năng lực tài chính](#bdso2o-05) |
| `BDSO2O-06` | [PricePolicy AI Agent – Trợ lý phân tích chính sách bán hàng & tính giá, khuyến mãi](#bdso2o-06) |
| `BDSO2O-07` | [LoanDoc AI Agent – Trợ lý chuẩn bị hồ sơ vay & kiểm tra pháp lý mua bán](#bdso2o-07) |
| `BDSO2O-08` | [SalesCoach AI Agent – Trợ lý huấn luyện & luyện tập bán hàng cho đội O2O](#bdso2o-08) |
| `BDSO2O-09` | [MarketWatch AI Agent – Trợ lý phân tích thị trường & đối thủ khu vực](#bdso2o-09) |
| `BDSO2O-10` | [MoveIn AI Agent – Trợ lý onboarding cư dân & chăm sóc sau bàn giao](#bdso2o-10) |
| `BDSO2O-11` | [FunnelOptimizer AI Agent – Trợ lý phân tích & tối ưu phễu chuyển đổi Online→Offline](#bdso2o-11) |
| `BDSO2O-12` | [ContentForge AI Agent – Trợ lý sản xuất nội dung marketing dự án đa kênh](#bdso2o-12) |
| `BDSO2O-13` | [AgencyHub AI Agent – Trợ lý quản lý & điều phối sàn/đại lý phân phối](#bdso2o-13) |
| `BDSO2O-14` | [AbsorptionForecast AI Agent – Trợ lý dự báo tồn kho & tốc độ hấp thụ căn hộ](#bdso2o-14) |
| `BDSO2O-15` | [InboundQualifier AI Agent – Trợ lý sàng lọc & bàn giao khách inbound đa kênh](#bdso2o-15) |
| `BDSO2O-16` | [ResaleValuer AI Agent – Trợ lý định giá & thẩm định căn hộ chuyển nhượng thứ cấp](#bdso2o-16) |
| `BDSO2O-17` | [ContractGuard AI Agent – Trợ lý rà soát hợp đồng mua bán & phụ lục](#bdso2o-17) |
| `BDSO2O-18` | [VoiceOfCustomer AI Agent – Trợ lý phân tích phản hồi & cảm xúc khách hàng](#bdso2o-18) |
| `BDSO2O-19` | [TourConcierge AI Agent – Trợ lý điều phối tour tham quan dự án & trải nghiệm tại chỗ](#bdso2o-19) |
| `BDSO2O-20` | [KPIPulse AI Agent – Trợ lý theo dõi cam kết & báo cáo hiệu suất đội sale tự động](#bdso2o-20) |

---

## [BDSO2O-01] LeadScorer AI Agent – Trợ lý chấm điểm & phân luồng lead khách mua nhà doanh nghiệp bất động sản

### 📝 Mô tả đề tài
📍 Thực trạng: Mỗi ngày đội O2O nhận hàng nghìn lead từ landing page, Facebook Lead Ads, hotline, Zalo... nhưng sale phải tự đọc và đoán ai là khách tiềm năng, dẫn đến bỏ sót khách nóng và lãng phí thời gian vào khách rác. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tự lập kế hoạch làm giàu dữ liệu lead (enrich), chấm điểm theo nhu cầu-ngân sách-độ nóng, phân luồng tự động về đúng sale/phân khu và giải thích lý do điểm số để sale tin dùng; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: Bắt buộc human-in-the-loop cho phép trưởng nhóm xem lại, chỉnh điểm và override phân luồng; dữ liệu khách hàng (SĐT, tài chính) phải mã hóa, ẩn danh khi log và tuân thủ chính sách bảo vệ dữ liệu; độ chính xác điểm số phải kèm confidence; kiểm soát chi phí gọi LLM bằng cache và batch.

### 🛠️ Tech Stack
• LLM GPT-4o-mini/Gemini Flash cho phân loại
• LangGraph điều phối pipeline enrich→score→route
• Postgres lưu lead + pgvector cho similar-lead matching
• FastAPI backend
• React/Next.js dashboard
• Redis cache
• deploy trên Railway/Render
• webhook nhận lead từ Meta/Zalo.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chuyển đổi phễu khách hàng đa kênh Olist Marketing Funnel / Criteo Uplift, benchmark hội thoại tác vụ τ-bench và dữ liệu giỏ hàng bất động sản đa phân khu.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app đăng nhập 2 vai trò (sale, trưởng nhóm), nhập/import lead, agent tự chấm điểm 0-100 kèm giải thích và tự phân về sale, HITL duyệt/sửa, cảnh báo khi thiếu dữ liệu.

Nâng cao:
• Multi-agent (agent enrich + agent scoring + agent routing), học từ feedback duyệt của người dùng (feedback loop), bộ eval đo độ chính xác dự đoán chuyển đổi trên dữ liệu lịch sử, A/B test ngưỡng điểm và dashboard đo tỉ lệ lead nóng chốt được
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-02] SalesMate AI Agent – Trợ lý tư vấn dự án & căn hộ theo thời gian thực cho sale

### 📝 Mô tả đề tài
📍 Thực trạng: doanh nghiệp bất động sản có hàng chục đại dự án với hàng trăm loại căn, chính sách và tiện ích thay đổi liên tục; sale mới không thể nhớ hết và thường tư vấn sai thông tin khi khách hỏi tại điểm bán. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tra cứu RAG trên kho tài liệu dự án (bảng giá, mặt bằng, chính sách, tiện ích) để trả lời chính xác câu hỏi của sale/khách, biết dùng công cụ tra tồn kho căn, và luôn trích nguồn tài liệu; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: Human-in-the-loop bắt buộc sale xác nhận trước khi gửi thông tin giá/cam kết cho khách; chống 'ảo giác' bằng ràng buộc chỉ trả lời theo tài liệu có nguồn; phân quyền tài liệu nội bộ vs công khai; tối ưu chi phí RAG và độ trễ dưới vài giây tại hiện trường. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM Claude/GPT-4o
• LlamaIndex cho ingestion + RAG
• vector DB Qdrant/Weaviate
• re-ranker
• tool tra cứu tồn kho qua API
• FastAPI backend
• Next.js + giao diện mobile-first cho sale
• deploy Vercel + Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu giao dịch & định giá bất động sản công khai (Zillow ZTRAX / Ames Housing / Kaggle Property Sales) kết hợp bảng chính sách bán hàng và lịch dòng tiền trả góp đa phương án.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App đăng nhập (sale, admin nội dung), chat hỏi-đáp có trích nguồn tài liệu, tra được thông tin căn/giá/chính sách, admin upload và cập nhật tài liệu.

Nâng cao:
• Agent tự đối chiếu nhiều tài liệu và cảnh báo mâu thuẫn, gợi ý câu trả lời mẫu kèm hình mặt bằng, bộ eval faithfulness/relevance, memory theo từng khách để cá nhân hóa tư vấn tiếp theo
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-03] FollowUp AI Agent – Trợ lý tự động soạn kịch bản & nhắc nhở chăm sóc khách đa kênh

### 📝 Mô tả đề tài
📍 Thực trạng: Sale bận đi dẫn khách nên hay quên follow-up đúng thời điểm; tin nhắn chăm sóc bị lặp mẫu, thiếu cá nhân hóa khiến khách nguội dần trong phễu O2O. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent lập kế hoạch chuỗi chăm sóc (cadence) theo giai đoạn khách, tự soạn nội dung Zalo/SMS/email cá nhân hóa theo lịch sử tương tác và nhắc sale gửi đúng lúc, biết dừng khi khách phản hồi tiêu cực; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: Bắt buộc HITL – mọi tin nhắn phải được sale duyệt trước khi gửi; tuân thủ chống spam và opt-out; không bịa thông tin ưu đãi; kiểm soát tần suất và chi phí sinh nội dung. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM GPT-4o-mini sinh nội dung
• LangGraph quản lý state chuỗi cadence
• cron/Celery scheduler
• Postgres lưu timeline khách
• tích hợp Zalo OA/email API
• FastAPI + React
• deploy Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chuyển đổi phễu khách hàng đa kênh Olist Marketing Funnel / Criteo Uplift, benchmark hội thoại tác vụ τ-bench và dữ liệu giỏ hàng bất động sản đa phân khu.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App 2 vai trò (sale, quản lý), agent đề xuất lịch follow-up và soạn nội dung cá nhân hóa, sale duyệt/sửa/gửi, nhật ký tương tác.

Nâng cao:
• Multi-agent (agent lập kế hoạch + agent viết nội dung + agent phân tích phản hồi), tối ưu thời điểm gửi bằng dữ liệu, phân tích sentiment phản hồi để tự điều chỉnh cadence, eval tỉ lệ phản hồi theo mẫu
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-04] BookingBot AI Agent – Trợ lý đặt lịch xem nhà & giữ căn tự động

### 📝 Mô tả đề tài
📍 Thực trạng: Việc hẹn khách xem nhà mẫu/căn thực tế phải phối hợp lịch sale, xe đưa đón, tình trạng căn và phòng chờ; điều phối thủ công qua chat gây trùng lịch và bỏ lỡ khách. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hiểu yêu cầu khách bằng ngôn ngữ tự nhiên, dùng công cụ kiểm tra lịch trống của sale và trạng thái căn, đề xuất khung giờ, đặt lịch và giữ căn tạm thời (soft-hold), tự gửi nhắc và xử lý dời/hủy; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL cho sale xác nhận trước khi chốt lịch và giữ căn; tránh double-booking bằng khóa giao dịch; bảo mật thông tin khách; xử lý lỗi khi API lịch/căn không phản hồi và cảnh báo giới hạn giữ căn. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM function-calling (GPT-4o)
• CrewAI/LangGraph điều phối tool
• Google/Outlook Calendar API
• Postgres inventory với row-lock
• FastAPI + Next.js
• WebSocket cập nhật real-time
• deploy Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chuyển đổi phễu khách hàng đa kênh Olist Marketing Funnel / Criteo Uplift, benchmark hội thoại tác vụ τ-bench và dữ liệu giỏ hàng bất động sản đa phân khu.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App đăng nhập (khách/sale hoặc sale/điều phối viên), agent hội thoại đặt lịch xem nhà, kiểm tra & giữ căn, gửi xác nhận, HITL duyệt.

Nâng cao:
• Tối ưu lộ trình dẫn nhiều khách trong ngày, tự động dời lịch khi xung đột, tích hợp bản đồ tiện ích, eval tỉ lệ đặt lịch thành công và no-show, memory ưu tiên khung giờ của từng khách
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-05] HomeMatch AI Agent – Trợ lý gợi ý căn hộ theo nhu cầu và năng lực tài chính

### 📝 Mô tả đề tài
📍 Thực trạng: Khách thường mô tả nhu cầu mơ hồ ('gần trường, thoáng, tầm 3 tỷ, view đẹp') còn sale phải lọc tay hàng trăm căn nên gợi ý chậm và thiếu tối ưu. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phỏng vấn khai thác nhu cầu, chuyển thành tiêu chí, kiểm tra khả năng tài chính (ngân sách + ước tính vay), truy vấn kho căn và xếp hạng gợi ý top căn phù hợp kèm lý giải đánh đổi; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL để sale duyệt danh sách gợi ý trước khi trình khách; minh bạch lý do gợi ý, không thiên vị căn tồn; bảo mật thông tin tài chính khách; tối ưu chi phí truy vấn ngữ nghĩa. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM GPT-4o
• embedding + pgvector cho matching semantic
• LangGraph
• engine tính vay đơn giản
• FastAPI
• React với so sánh trực quan
• deploy Railway.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu giao dịch & định giá bất động sản công khai (Zillow ZTRAX / Ames Housing / Kaggle Property Sales) kết hợp bảng chính sách bán hàng và lịch dòng tiền trả góp đa phương án.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App 2 vai trò (sale, khách), agent hỏi nhu cầu và trả về top căn kèm giải thích và ước tính tài chính, sale duyệt/lọc.

Nâng cao:
• Multi-agent (agent khai thác nhu cầu + agent tài chính + agent xếp hạng), so sánh cạnh nhau nhiều căn, mô phỏng kịch bản vay, học sở thích qua các phiên (memory), eval độ hài lòng/độ chính xác gợi ý
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-06] PricePolicy AI Agent – Trợ lý phân tích chính sách bán hàng & tính giá, khuyến mãi

### 📝 Mô tả đề tài
📍 Thực trạng: Chính sách bán hàng doanh nghiệp bất động sản nhiều tầng (chiết khấu thanh toán nhanh, hỗ trợ lãi suất, quà tặng, ưu đãi theo đợt) khiến sale tính giá cuối tay dễ sai và không giải thích được cho khách. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent đọc chính sách hiện hành, lập kế hoạch áp dụng đúng điều kiện khách, tính giá cuối theo từng phương án thanh toán và diễn giải minh bạch từng khoản ưu đãi; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL bắt buộc quản lý duyệt bảng tính giá trước khi gửi khách; con số phải chính xác tuyệt đối, dùng công cụ tính toán thay vì để LLM tự tính; kiểm soát phiên bản chính sách và audit trail; bảo mật bảng giá nội bộ. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM để hiểu chính sách + tool calculator xác định (Python)
• RAG trên văn bản chính sách (LlamaIndex + Qdrant)
• LangGraph
• FastAPI
• Next.js xuất bảng tính giá PDF
• deploy Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu giao dịch & định giá bất động sản công khai (Zillow ZTRAX / Ames Housing / Kaggle Property Sales) kết hợp bảng chính sách bán hàng và lịch dòng tiền trả góp đa phương án.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (sale, quản lý), nhập thông tin căn + phương án thanh toán, agent tính giá cuối và liệt kê ưu đãi có trích chính sách, xuất báo giá, HITL duyệt.

Nâng cao:
• So sánh nhiều phương án thanh toán và gợi ý phương án tối ưu cho khách, phát hiện chính sách chồng chéo/mâu thuẫn, quản lý phiên bản chính sách theo thời gian, bộ test kiểm chứng tính đúng của công thức
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-07] LoanDoc AI Agent – Trợ lý chuẩn bị hồ sơ vay & kiểm tra pháp lý mua bán

### 📝 Mô tả đề tài
📍 Thực trạng: Khách mua nhà thường vướng ở khâu hồ sơ vay ngân hàng và giấy tờ pháp lý; sale không rành nên tư vấn thiếu, hồ sơ bị trả đi trả lại làm chậm chốt deal. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hướng dẫn checklist hồ sơ theo tình huống khách (thu nhập, ngân hàng liên kết), kiểm tra tính đầy đủ của giấy tờ tải lên, ước tính khả năng được duyệt vay và soạn hồ sơ mẫu; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – chuyên viên pháp lý/tín dụng phải rà soát trước khi khẳng định; không đưa tư vấn pháp lý ràng buộc, luôn cảnh báo giới hạn; bảo mật cao dữ liệu tài chính/CMND; xử lý lỗi OCR tài liệu. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM đa phương thức đọc tài liệu (GPT-4o vision)
• OCR
• RAG quy định vay/pháp lý
• LangGraph
• FastAPI
• React upload tài liệu
• lưu trữ mã hóa
• deploy Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu giao dịch & định giá bất động sản công khai (Zillow ZTRAX / Ames Housing / Kaggle Property Sales) kết hợp bảng chính sách bán hàng và lịch dòng tiền trả góp đa phương án.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (khách/sale, chuyên viên), agent đưa checklist, kiểm tra tài liệu upload thiếu/đủ, ước tính khả năng vay, HITL duyệt.

Nâng cao:
• Multi-agent (agent tín dụng + agent pháp lý), tự trích và đối chiếu thông tin trên giấy tờ, so sánh gói vay nhiều ngân hàng, cảnh báo rủi ro pháp lý (sổ, quy hoạch), eval độ chính xác trích xuất tài liệu
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-08] SalesCoach AI Agent – Trợ lý huấn luyện & luyện tập bán hàng cho đội O2O

### 📝 Mô tả đề tài
📍 Thực trạng: Đội sale O2O tuyển mới liên tục, chất lượng tư vấn không đồng đều và không có kênh luyện tập xử lý phản đối của khách trước khi ra hiện trường. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent đóng vai khách hàng khó tính để sale luyện hội thoại, chấm điểm theo khung kỹ năng (khai thác nhu cầu, xử lý phản đối, chốt), đưa phản hồi cải thiện và lập lộ trình học cá nhân; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – quản lý xem lại điểm và phản hồi trước khi ghi nhận đánh giá chính thức; đảm bảo công bằng khi chấm; không lộ dữ liệu khách thật trong kịch bản; kiểm soát chi phí phiên role-play dài. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM GPT-4o (persona khách)
• LangGraph quản lý phiên hội thoại + rubric scoring
• speech-to-text tùy chọn cho luyện nói
• Postgres lưu tiến độ
• FastAPI + Next.js
• deploy Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chuyển đổi phễu khách hàng đa kênh Olist Marketing Funnel / Criteo Uplift, benchmark hội thoại tác vụ τ-bench và dữ liệu giỏ hàng bất động sản đa phân khu.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (sale, quản lý), agent role-play khách theo kịch bản, chấm điểm và phản hồi, quản lý theo dõi tiến độ.

Nâng cao:
• Nhiều persona khách đa dạng, chấm điểm theo rubric có giải thích, lộ trình học thích ứng theo điểm yếu, bảng xếp hạng đội, eval độ tương quan điểm AI với đánh giá quản lý
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-09] MarketWatch AI Agent – Trợ lý phân tích thị trường & đối thủ khu vực

### 📝 Mô tả đề tài
📍 Thực trạng: Để định vị bán hàng, đội O2O cần nắm giá, chính sách và động thái của các dự án đối thủ quanh khu vực, nhưng việc thu thập tin từ web/tin rao/mạng xã hội đang làm thủ công, chậm và rời rạc. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent lập kế hoạch thu thập dữ liệu thị trường từ nhiều nguồn, tổng hợp mặt bằng giá và điểm mạnh-yếu đối thủ, sinh báo cáo so sánh định kỳ và cảnh báo biến động bất thường; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – chuyên viên duyệt báo cáo trước khi phát hành nội bộ; tôn trọng điều khoản thu thập dữ liệu và ghi rõ nguồn; đánh dấu độ tin cậy thông tin chưa kiểm chứng; kiểm soát chi phí crawl và tần suất. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM tổng hợp + trích xuất
• web scraping/search tool
• LangGraph điều phối thu thập→chuẩn hóa→phân tích
• vector DB lưu tin
• FastAPI
• Next.js dashboard biểu đồ
• scheduler
• deploy Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu giao dịch & định giá bất động sản công khai (Zillow ZTRAX / Ames Housing / Kaggle Property Sales) kết hợp bảng chính sách bán hàng và lịch dòng tiền trả góp đa phương án.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (nhân viên phân tích, quản lý), agent thu thập và tổng hợp giá/chính sách đối thủ khu vực, báo cáo so sánh có nguồn, HITL duyệt.

Nâng cao:
• Multi-agent thu thập đa nguồn, phát hiện xu hướng & cảnh báo biến động giá, phân tích điểm bán độc nhất (USP) để gợi ý luận điểm bán, báo cáo tự động định kỳ, eval độ chính xác trích xuất số liệu
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-10] MoveIn AI Agent – Trợ lý onboarding cư dân & chăm sóc sau bàn giao

### 📝 Mô tả đề tài
📍 Thực trạng: Sau khi khách nhận nhà, quy trình onboarding (thủ tục bàn giao, kích hoạt tiện ích, hướng dẫn cư dân, xử lý lỗi căn hộ) rời rạc khiến trải nghiệm sau bán kém và giảm giới thiệu khách mới. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent dẫn dắt cư dân qua từng bước onboarding cá nhân hóa, trả lời câu hỏi về tiện ích/quy định, tiếp nhận và phân loại yêu cầu sửa lỗi, theo dõi trạng thái đến khi hoàn tất; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – ban quản lý duyệt trước khi tạo ticket/cam kết thời hạn; bảo mật thông tin cư dân; không cam kết ngoài thẩm quyền; xử lý lỗi khi hệ thống ticket không phản hồi và cảnh báo quá tải. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM GPT-4o-mini
• RAG sổ tay cư dân + quy định (LlamaIndex)
• LangGraph quản lý checklist stateful
• tool tạo ticket
• Postgres
• FastAPI + React
• deploy Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu hợp đồng thương mại CUAD (Contract Understanding Atticus Dataset) kết hợp mẫu Hợp đồng Mua bán và tiêu chuẩn bàn giao bất động sản.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (cư dân, ban quản lý), agent hướng dẫn onboarding theo checklist, hỏi-đáp có nguồn, tạo yêu cầu sửa lỗi, HITL duyệt.

Nâng cao:
• Phân loại và định tuyến yêu cầu theo mức ưu tiên, nhắc mốc bàn giao, memory theo từng cư dân, khảo sát hài lòng và tổng hợp insight cho ban quản lý, eval độ giải quyết đúng luồng
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-11] FunnelOptimizer AI Agent – Trợ lý phân tích & tối ưu phễu chuyển đổi Online→Offline

### 📝 Mô tả đề tài
📍 Thực trạng: Hành trình khách từ click quảng cáo online đến đặt lịch và tới điểm bán offline bị rơi rớt qua nhiều bước mà đội marketing-sale không biết chính xác nghẽn ở đâu và vì sao. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích dữ liệu phễu theo từng nguồn/chiến dịch, phát hiện điểm rơi, chẩn đoán nguyên nhân và đề xuất hành động tối ưu (nội dung, thời điểm liên hệ, phân bổ sale) kèm ước tính tác động; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – trưởng phòng duyệt đề xuất trước khi áp dụng; phân tích phải dựa số liệu thực, không suy diễn thiếu căn cứ; bảo mật dữ liệu khách và ngân sách; kiểm soát chi phí phân tích định kỳ. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM cho diễn giải + tool phân tích dữ liệu (Python/pandas
• code-interpreter agent)
• LangGraph
• kho dữ liệu phễu (Postgres/DuckDB)
• FastAPI
• Next.js dashboard
• deploy Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chuyển đổi phễu khách hàng đa kênh Olist Marketing Funnel / Criteo Uplift, benchmark hội thoại tác vụ τ-bench và dữ liệu giỏ hàng bất động sản đa phân khu.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (marketing, quản lý), nạp dữ liệu phễu, agent phân tích điểm rơi và đề xuất hành động có số liệu, HITL duyệt.

Nâng cao:
• Agent tự viết & chạy truy vấn phân tích, mô phỏng what-if tác động khi thay đổi, cảnh báo bất thường theo thời gian thực, giải thích nguyên nhân theo cohort, eval độ chính xác dự báo cải thiện
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-12] ContentForge AI Agent – Trợ lý sản xuất nội dung marketing dự án đa kênh

### 📝 Mô tả đề tài
📍 Thực trạng: Đội O2O cần liên tục ra bài đăng, tin nhắn, kịch bản livestream và mô tả dự án cho nhiều kênh, nhưng viết tay chậm, thiếu nhất quán thương hiệu và dễ sai thông tin dự án. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent lập kế hoạch nội dung theo chiến dịch, lấy dữ kiện dự án chuẩn từ kho (RAG), sinh nội dung đa định dạng theo tông thương hiệu và điều chỉnh theo từng kênh/tệp khách; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – marketing duyệt và chỉnh trước khi xuất bản; ràng buộc chỉ dùng số liệu dự án đã xác thực để tránh sai lệch pháp lý quảng cáo; tuân thủ nguyên tắc thương hiệu; kiểm soát chi phí sinh nội dung số lượng lớn. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM GPT-4o/Claude
• RAG dữ kiện dự án + brand guideline (LlamaIndex + Qdrant)
• LangGraph pipeline lập kế hoạch→viết→kiểm duyệt
• FastAPI
• Next.js editor
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chuyển đổi phễu khách hàng đa kênh Olist Marketing Funnel / Criteo Uplift, benchmark hội thoại tác vụ τ-bench và dữ liệu giỏ hàng bất động sản đa phân khu.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (marketer, quản lý), chọn dự án + kênh, agent sinh nhiều biến thể nội dung đúng dữ kiện, HITL sửa/duyệt, thư viện nội dung.

Nâng cao:
• Multi-agent (agent lập kế hoạch + agent viết + agent kiểm duyệt tuân thủ), tự động cảnh báo tuyên bố sai/quá đà, lịch nội dung theo chiến dịch, A/B gợi ý tiêu đề, eval độ bám dữ kiện và giọng thương hiệu
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-13] AgencyHub AI Agent – Trợ lý quản lý & điều phối sàn/đại lý phân phối

### 📝 Mô tả đề tài
📍 Thực trạng: doanh nghiệp bất động sản bán qua nhiều sàn/đại lý F1-F2; việc phân bổ quỹ căn, theo dõi hiệu suất sàn, đối soát booking và giải đáp thắc mắc đại lý đang xử lý phân tán qua email/nhóm chat. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent trợ giúp điều phối: trả lời chính sách phân phối cho đại lý, kiểm tra quỹ căn được phân, tổng hợp hiệu suất từng sàn và cảnh báo sàn dưới chỉ tiêu; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – quản lý kênh duyệt phân bổ quỹ và cảnh báo trước khi gửi đại lý; phân quyền dữ liệu theo từng sàn (không lộ chéo); độ chính xác đối soát tuyệt đối; kiểm soát chi phí và audit thao tác. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM function-calling
• RAG chính sách phân phối
• LangGraph
• Postgres phân quyền theo tenant
• FastAPI
• Next.js dashboard đại lý
• deploy Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chuyển đổi phễu khách hàng đa kênh Olist Marketing Funnel / Criteo Uplift, benchmark hội thoại tác vụ τ-bench và dữ liệu giỏ hàng bất động sản đa phân khu.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App đa vai trò (đại lý, quản lý kênh), agent trả lời chính sách phân phối và tra quỹ căn được phân, báo cáo hiệu suất sàn, HITL duyệt phân bổ.

Nâng cao:
• Multi-agent điều phối phân bổ quỹ theo hiệu suất, phát hiện đối soát lệch booking, xếp hạng & cảnh báo sàn rủi ro, memory theo từng đại lý, eval độ chính xác đối soát
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-14] AbsorptionForecast AI Agent – Trợ lý dự báo tồn kho & tốc độ hấp thụ căn hộ

### 📝 Mô tả đề tài
📍 Thực trạng: Ban kinh doanh cần biết phân khu/loại căn nào sắp hết, loại nào ế để điều chỉnh chính sách và tập trung sale, nhưng dự báo hiện dựa cảm tính và bảng Excel cập nhật chậm. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích dữ liệu bán và tồn theo thời gian, dự báo tốc độ hấp thụ và thời điểm cạn hàng theo phân khu/loại căn, giải thích yếu tố tác động và đề xuất hành động (đẩy hàng chậm, giữ hàng hot); đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – quản lý kinh doanh duyệt dự báo trước khi ra quyết định chính sách; dự báo phải kèm khoảng tin cậy và giả định rõ ràng; bảo mật dữ liệu bán hàng; kiểm soát chi phí tính toán định kỳ. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM diễn giải + tool dự báo (Python
• mô hình chuỗi thời gian đơn giản/Prophet)
• LangGraph agent phân tích
• DuckDB/Postgres
• FastAPI
• Next.js dashboard biểu đồ
• deploy Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu giao dịch & định giá bất động sản công khai (Zillow ZTRAX / Ames Housing / Kaggle Property Sales) kết hợp bảng chính sách bán hàng và lịch dòng tiền trả góp đa phương án.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (nhân viên kinh doanh, quản lý), nạp dữ liệu bán/tồn, agent dự báo tốc độ hấp thụ và cảnh báo cạn hàng, giải thích, HITL duyệt.

Nâng cao:
• Agent tự chọn & so sánh mô hình dự báo, mô phỏng kịch bản khi thay chính sách/giá, gợi ý ưu tiên đẩy hàng, cảnh báo lệch dự báo thực tế, bộ eval sai số dự báo (MAPE)
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-15] InboundQualifier AI Agent – Trợ lý sàng lọc & bàn giao khách inbound đa kênh

### 📝 Mô tả đề tài
📍 Thực trạng: Khách nhắn tới qua website chat, Zalo, Messenger, comment quảng cáo với nhiều mức độ nghiêm túc; sale trực chat bị quá tải và phản hồi chậm khiến khách nóng nguội đi. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tiếp nhận hội thoại đầu vào 24/7, khai thác nhu cầu cơ bản, phân loại khách đủ điều kiện, thu thập thông tin liên hệ và bàn giao mượt mà cho sale phù hợp kèm tóm tắt ngữ cảnh; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – agent phải chuyển người thật khi khách yêu cầu hoặc khi vượt phạm vi; không cam kết giá/pháp lý; bảo mật thông tin thu thập; cảnh báo và xử lý khi không hiểu ý khách thay vì bịa. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM GPT-4o-mini
• LangGraph quản lý luồng qualify + handoff
• kết nối đa kênh (webchat
• Zalo
• Messenger)
• Postgres + memory hội thoại
• FastAPI + Next.js widget
• deploy Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu hợp đồng thương mại CUAD (Contract Understanding Atticus Dataset) kết hợp mẫu Hợp đồng Mua bán và tiêu chuẩn bàn giao bất động sản.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Widget chat + app (sale, quản lý), agent hội thoại sàng lọc và tạo lead có tóm tắt, chuyển người thật, HITL giám sát.

Nâng cao:
• Multi-kênh hợp nhất một hồ sơ khách, chấm mức độ sẵn sàng theo hội thoại, tự đặt lịch/định tuyến sale, phân tích lý do rớt khách, eval tỉ lệ qualify đúng và độ hài lòng hội thoại
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-16] ResaleValuer AI Agent – Trợ lý định giá & thẩm định căn hộ chuyển nhượng thứ cấp

### 📝 Mô tả đề tài
📍 Thực trạng: Trong mảng O2O còn có giao dịch chuyển nhượng thứ cấp trong nội khu doanh nghiệp bất động sản; sale/khách khó định giá hợp lý căn resale vì phụ thuộc tầng, view, nội thất, thời điểm và giao dịch tương đồng. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent thu thập các yếu tố căn, tìm giao dịch/tin rao tương đồng, ước tính khoảng giá hợp lý kèm diễn giải các yếu tố điều chỉnh và độ tin cậy; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – chuyên viên định giá duyệt trước khi trình khách; luôn nêu đây là ước tính tham khảo và giới hạn dữ liệu; bảo mật thông tin giao dịch; kiểm soát chi phí tra cứu so sánh. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM + tool định giá theo phương pháp so sánh
• embedding + pgvector tìm căn tương đồng
• LangGraph
• dữ liệu giao dịch nội bộ + tin rao
• FastAPI
• Next.js
• deploy Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu giao dịch & định giá bất động sản công khai (Zillow ZTRAX / Ames Housing / Kaggle Property Sales) kết hợp bảng chính sách bán hàng và lịch dòng tiền trả góp đa phương án.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (sale/khách, chuyên viên định giá), nhập thông tin căn, agent trả về khoảng giá ước tính kèm căn so sánh và giải thích, HITL duyệt.

Nâng cao:
• Agent tự điều chỉnh trọng số yếu tố (tầng/view/nội thất), cập nhật theo giao dịch mới, đưa dải giá theo kịch bản bán nhanh/bán tối ưu, cảnh báo dữ liệu mỏng, eval sai số định giá so với giá chốt thực
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-17] ContractGuard AI Agent – Trợ lý rà soát hợp đồng mua bán & phụ lục

### 📝 Mô tả đề tài
📍 Thực trạng: Hợp đồng mua bán căn hộ và phụ lục dài, nhiều điều khoản; sale và khách khó phát hiện điểm cần lưu ý (thời hạn thanh toán, phạt, bàn giao, cam kết) dẫn tới tranh chấp về sau. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent đọc bản hợp đồng, đối chiếu với mẫu chuẩn và chính sách, tóm tắt điều khoản quan trọng, phát hiện sai lệch/thiếu sót và giải thích cho khách bằng ngôn ngữ dễ hiểu; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – pháp chế phải rà soát và phê duyệt, agent chỉ hỗ trợ không thay thế; cảnh báo rõ giới hạn (không phải tư vấn pháp lý chính thức); bảo mật cao tài liệu hợp đồng; chống bịa điều khoản không có trong văn bản. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM GPT-4o/Claude đọc tài liệu dài
• RAG mẫu hợp đồng chuẩn + quy định (LlamaIndex)
• LangGraph pipeline trích→đối chiếu→cảnh báo
• lưu trữ mã hóa
• FastAPI + React
• deploy Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu hợp đồng thương mại CUAD (Contract Understanding Atticus Dataset) kết hợp mẫu Hợp đồng Mua bán và tiêu chuẩn bàn giao bất động sản.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (sale/pháp chế), upload hợp đồng, agent tóm tắt điều khoản chính và điểm cần lưu ý có trích dẫn vị trí, HITL duyệt.

Nâng cao:
• Đối chiếu tự động với mẫu chuẩn và highlight sai lệch, so sánh nhiều phiên bản/phụ lục, giải thích điều khoản cho khách theo mức độ dễ hiểu, eval độ chính xác phát hiện điều khoản rủi ro
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-18] VoiceOfCustomer AI Agent – Trợ lý phân tích phản hồi & cảm xúc khách hàng

### 📝 Mô tả đề tài
📍 Thực trạng: Phản hồi khách rải rác ở khảo sát, ghi chú sale, comment mạng xã hội, cuộc gọi CSKH; ban kinh doanh không có bức tranh tổng hợp về điều khách khen/chê ở từng dự án. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent gom phản hồi đa nguồn, phân loại chủ đề (giá, tiện ích, thái độ sale, tiến độ), chấm sentiment, phát hiện vấn đề nổi cộm và đề xuất hành động cải thiện theo dự án; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – quản lý duyệt insight và hành động trước khi triển khai; ẩn danh dữ liệu cá nhân khách khi phân tích; nêu rõ mẫu dữ liệu và độ tin cậy; kiểm soát chi phí xử lý khối lượng lớn. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM phân loại + sentiment
• embedding gom cụm chủ đề
• LangGraph pipeline ingest→cluster→tổng hợp
• vector DB
• FastAPI
• Next.js dashboard
• deploy Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu giao dịch & định giá bất động sản công khai (Zillow ZTRAX / Ames Housing / Kaggle Property Sales) kết hợp bảng chính sách bán hàng và lịch dòng tiền trả góp đa phương án.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (nhân viên CSKH, quản lý), nạp phản hồi đa nguồn, agent phân loại chủ đề + sentiment và tổng hợp insight, HITL duyệt.

Nâng cao:
• Multi-agent (gom cụm + tổng hợp + đề xuất), phát hiện xu hướng & cảnh báo khủng hoảng sớm, drill-down theo dự án/thời gian, gợi ý hành động ưu tiên, eval độ chính xác phân loại chủ đề/sentiment
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-19] TourConcierge AI Agent – Trợ lý điều phối tour tham quan dự án & trải nghiệm tại chỗ

### 📝 Mô tả đề tài
📍 Thực trạng: doanh nghiệp bất động sản tổ chức nhiều tour đưa khách tham quan đại dự án (nhà mẫu, tiện ích, phân khu) nhưng việc gom nhóm khách, sắp lộ trình, phân xe và cá nhân hóa điểm dừng theo nhu cầu đang làm thủ công, kém tối ưu. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent lập kế hoạch tour cá nhân hóa theo nhu cầu từng khách, tối ưu lộ trình điểm dừng và thời lượng, điều phối xe/hướng dẫn viên và cung cấp thuyết minh theo từng điểm đến; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – điều phối viên duyệt lịch trình và phân bổ nguồn lực trước khi chốt; bảo mật thông tin khách; xử lý lỗi khi nguồn lực thiếu và cảnh báo giới hạn sức chứa; tối ưu chi phí điều phối. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM lập kế hoạch + tool tối ưu lộ trình (thuật toán TSP/OR-Tools)
• LangGraph
• RAG thuyết minh dự án
• Maps API
• Postgres nguồn lực
• FastAPI + Next.js
• deploy Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chuyển đổi phễu khách hàng đa kênh Olist Marketing Funnel / Criteo Uplift, benchmark hội thoại tác vụ τ-bench và dữ liệu giỏ hàng bất động sản đa phân khu.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (điều phối viên, hướng dẫn viên/sale), agent tạo lịch trình tour theo nhu cầu và phân bổ xe/HDV, thuyết minh điểm dừng, HITL duyệt.

Nâng cao:
• Tối ưu lộ trình đa khách/đa nhóm, tự điều chỉnh khi thay đổi thời tiết/nguồn lực, cá nhân hóa điểm dừng theo hồ sơ khách, thu thập phản hồi sau tour, eval độ hài lòng và hiệu suất sử dụng nguồn lực
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---

## [BDSO2O-20] KPIPulse AI Agent – Trợ lý theo dõi cam kết & báo cáo hiệu suất đội sale tự động

### 📝 Mô tả đề tài
📍 Thực trạng: Quản lý đội O2O phải tổng hợp thủ công số cuộc gọi, lịch xem nhà, booking và doanh số của từng sale từ nhiều bảng, khiến báo cáo chậm và khó phát hiện sale đang tụt hoặc cam kết không đạt. Trong thực tế kinh doanh của doanh nghiệp, dữ liệu khách hàng đa kênh thường trùng lặp, nhiễu hoặc khuyết thiếu, trong khi chính sách bán hàng, chiết khấu và trạng thái giỏ hàng thay đổi liên tục theo từng phân khu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tự thu thập số liệu hoạt động, đối chiếu với cam kết/KPI, sinh báo cáo hiệu suất theo cá nhân/nhóm, phát hiện lệch cam kết và đề xuất hành động kèm nhắc nhở tự động; đồng thời hợp nhất dữ liệu đa nguồn, kết hợp mô hình suy luận/tư vấn của Agent với động cơ tính toán tài chính – kiểm tra chính sách – phân bổ nguồn lực xác định bằng code nhằm tối ưu hóa tỷ lệ chuyển đổi thực tế cho doanh nghiệp.

🔒 Ràng buộc: HITL – quản lý duyệt báo cáo và cảnh báo trước khi gửi cho sale; công bằng và minh bạch cách tính KPI; bảo mật dữ liệu hiệu suất cá nhân; độ chính xác số liệu tuyệt đối và có audit trail. Tách biệt tuyệt đối các phép tính giá bán, chiết khấu, lãi suất vay, dòng tiền và luật phân bổ bằng hàm code xác định khỏi phần diễn giải của LLM; điểm dự báo phải được hiệu chuẩn (calibrated confidence) và kiểm chứng trên dữ liệu thực tế.

### 🛠️ Tech Stack
• LLM diễn giải + tool tổng hợp dữ liệu (Python/SQL)
• LangGraph agent báo cáo
• Postgres/DuckDB
• scheduler
• FastAPI
• Next.js dashboard
• tích hợp Zalo/email nhắc việc
• deploy Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chuyển đổi phễu khách hàng đa kênh Olist Marketing Funnel / Criteo Uplift, benchmark hội thoại tác vụ τ-bench và dữ liệu giỏ hàng bất động sản đa phân khu.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App (sale, quản lý), agent tổng hợp số liệu hoạt động và đối chiếu KPI, sinh báo cáo cá nhân/nhóm, cảnh báo lệch cam kết, HITL duyệt.

Nâng cao:
• Agent tự truy vấn & giải thích nguyên nhân tụt hạng, dự báo khả năng đạt chỉ tiêu cuối kỳ, gợi ý hành động cá nhân hóa và nhắc tự động, tổng hợp báo cáo định kỳ, eval độ chính xác số liệu và dự báo đạt KPI
• Tách biệt động cơ tính toán tài chính/kiểm tra điều khoản xác định với hệ thống đa tác tử, xây dựng bộ benchmark đánh giá độ chính xác trên dữ liệu lịch sử và mở rộng các tính năng hỗ trợ chốt giao dịch sát thực tế doanh nghiệp.

---
