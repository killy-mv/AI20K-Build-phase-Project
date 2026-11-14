# Lĩnh vực: GSM - Kinh doanh & Vận hành dịch vụ gọi xe công nghệ

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `GSM-01` | [AI Agent Trợ lý CSKH đặt xe & xử lý khiếu nại dịch vụ gọi xe của doanh nghiệp](#gsm-01) |
| `GSM-02` | [AI Agent Điều phối & ghép chuyến, dự báo nhu cầu theo khu vực-giờ](#gsm-02) |
| `GSM-03` | [AI Agent Hỗ trợ tài xế: hỏi đáp chính sách, thu nhập & lộ trình](#gsm-03) |
| `GSM-04` | [AI Agent Tối ưu tuyến & lịch sạc pin cho đội xe điện](#gsm-04) |
| `GSM-05` | [AI Agent Phát hiện gian lận cuốc xe & hành vi tài xế bất thường](#gsm-05) |
| `GSM-06` | [AI Agent Phân tích đánh giá & chấm điểm chất lượng chuyến đi](#gsm-06) |
| `GSM-07` | [AI Agent Quản lý cho thuê xe điện: booking, hợp đồng & bàn giao](#gsm-07) |
| `GSM-08` | [AI Agent Tổng đài giọng nói đặt xe & tra cứu dịch vụ gọi xe của doanh nghiệp](#gsm-08) |
| `GSM-09` | [AI Agent Dự báo & quản lý vận hành trạm sạc](#gsm-09) |
| `GSM-10` | [AI Agent Phân tích hủy chuyến & giữ chân khách hàng](#gsm-10) |
| `GSM-11` | [AI Agent Gợi ý khuyến mãi cá nhân hóa cho khách dịch vụ gọi xe của doanh nghiệp](#gsm-11) |
| `GSM-12` | [AI Agent Hỗ trợ đăng ký & đào tạo tài xế mới (onboarding)](#gsm-12) |
| `GSM-13` | [AI Agent Giám sát sự cố & an toàn hành trình realtime](#gsm-13) |
| `GSM-14` | [AI Agent Tối ưu phân bổ & huy động xe giờ cao điểm](#gsm-14) |
| `GSM-15` | [AI Agent Lắng nghe & phân tích phản hồi mạng xã hội về dịch vụ gọi xe của doanh nghiệp](#gsm-15) |
| `GSM-16` | [AI Agent Hỗ trợ khách doanh nghiệp (B2B) đặt & quản lý xe](#gsm-16) |
| `GSM-17` | [AI Agent Trợ lý tìm kiếm đồ thất lạc & xử lý bồi thường](#gsm-17) |
| `GSM-18` | [AI Agent Trợ lý bảo dưỡng & chẩn đoán sức khỏe đội xe điện](#gsm-18) |
| `GSM-19` | [AI Agent Trợ lý đặt xe đa phương thức & lập lộ trình cho khách](#gsm-19) |
| `GSM-20` | [AI Agent Phân tích vận hành & báo cáo thông minh cho quản lý dịch vụ gọi xe của doanh nghiệp](#gsm-20) |

---

## [GSM-01] AI Agent Trợ lý CSKH đặt xe & xử lý khiếu nại dịch vụ gọi xe của doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Tổng đài dịch vụ gọi xe của doanh nghiệp nhận hàng nghìn yêu cầu đặt xe, hỏi cước phí, đổi điểm đến, khiếu nại tài xế/thất lạc đồ mỗi ngày; nhân viên phải tra cứu thủ công lịch sử chuyến, chính sách hoàn tiền nên thời gian phản hồi lâu, dễ sai sót.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent đa vai trò (khách hàng – nhân viên CSKH) tự tiếp nhận yêu cầu, phân loại ý định (đặt xe/hỏi cước/khiếu nại/hoàn tiền), truy vấn dữ liệu chuyến đi, đề xuất hướng giải quyết và tạo ticket, với khả năng lập kế hoạch nhiều bước và gọi tool đặt/hủy/hoàn tiền; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: Human-in-the-loop bắt buộc khi hoàn tiền > ngưỡng hoặc khiếu nại nghiêm trọng; bảo mật dữ liệu hành trình và PII (che số điện thoại, điểm đón/đến); độ chính xác phân loại intent ≥ 90%; độ trễ phản hồi < 3s, kiểm soát chi phí token bằng cache & tóm tắt hội thoại. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM (GPT-4o-mini/Gemini Flash) + LangGraph điều phối multi-step
• RAG với vector DB (Qdrant/pgvector) cho kho chính sách & FAQ
• PostgreSQL mô phỏng dữ liệu chuyến/khách
• tool functions (đặt/hủy/hoàn tiền/tạo ticket)
• backend FastAPI + WebSocket streaming
• frontend React (Next.js) + Tailwind
• auth JWT 2 vai trò
• deploy Vercel (FE) + Render/Railway (BE).
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy online, đăng nhập 2 vai trò (khách & CSKH)
• agent phân loại intent, trả lời từ RAG, đặt/hủy chuyến giả lập, tạo ticket khiếu nại
• lưu memory hội thoại
• log tool calls.

Nâng cao:
• HITL duyệt hoàn tiền qua dashboard CSKH
• dashboard thống kê ticket & CSAT
• cảnh báo khi vượt hạn mức hoàn tiền/token
• fallback khi tool lỗi và guardrail chống rò rỉ PII
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-02] AI Agent Điều phối & ghép chuyến, dự báo nhu cầu theo khu vực-giờ

### 📝 Mô tả đề tài
📍 Thực trạng: Cung – cầu xe dịch vụ gọi xe của doanh nghiệp lệch theo khu vực và khung giờ (giờ cao điểm thiếu xe trung tâm, thừa xe ngoại ô), việc ghép chuyến và điều xe chủ yếu theo kinh nghiệm. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent dự báo nhu cầu theo grid khu vực × khung giờ, đề xuất điều phối/relocate xe và ghép chuyến tối ưu quãng đường rỗng, có khả năng lập kế hoạch và ra khuyến nghị điều hành; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL cho lệnh điều xe hàng loạt; bảo mật dữ liệu vị trí realtime; sai số dự báo (MAPE) chấp nhận được và giải thích được; độ trễ cập nhật bản đồ nhiệt < 5s, tối ưu chi phí gọi routing API. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM reasoning + LangGraph
• mô hình dự báo chuỗi thời gian (Prophet/LightGBM) làm tool
• dữ liệu địa lý OpenStreetMap + OSRM/Google Directions cho ma trận khoảng cách
• H3 grid
• PostGIS
• backend FastAPI
• frontend React + Mapbox/Leaflet heatmap
• deploy Docker trên Railway/Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy có đăng nhập điều hành viên & tài xế
• bản đồ nhiệt dự báo nhu cầu theo giờ
• agent gợi ý relocate & ghép chuyến với lý do
• memory theo phiên điều hành.

Nâng cao:
• HITL duyệt lệnh điều xe
• mô phỏng what-if (đổi số xe/khu vực)
• cảnh báo vùng thiếu xe & khi API routing gần hạn mức
• xử lý lỗi khi thiếu dữ liệu realtime
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-03] AI Agent Hỗ trợ tài xế: hỏi đáp chính sách, thu nhập & lộ trình

### 📝 Mô tả đề tài
📍 Thực trạng: Tài xế dịch vụ gọi xe của doanh nghiệp thường xuyên thắc mắc về chính sách thưởng/phạt, cách tính thu nhập, quy định đồng phục, khu vực ưu tiên; thông tin nằm rải rác nhiều văn bản, khó tra khi đang chạy. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent trợ lý cho tài xế giải đáp chính sách bằng RAG, tính toán thu nhập theo dữ liệu chuyến, và gợi ý khung giờ/khu vực hiệu quả, hỗ trợ thao tác rảnh tay; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL/chuyển người thật khi câu hỏi vượt phạm vi hoặc liên quan kỷ luật; bảo mật thu nhập & thông tin tài xế; độ chính xác trích dẫn chính sách cao, chống bịa; độ trễ thấp, tối ưu chi phí. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph
• RAG vector DB (Qdrant) cho kho chính sách
• tool tính thu nhập truy vấn PostgreSQL
• (tùy chọn) Whisper cho hỏi bằng giọng nói
• backend FastAPI streaming
• frontend React (giao diện tối giản kiểu app tài xế) hoặc React Native web
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập tài xế & admin nội dung
• hỏi đáp chính sách có trích nguồn
• tra cứu & tính thu nhập theo ngày/tuần
• memory ưu tiên của tài xế.

Nâng cao:
• Gợi ý khung giờ/khu vực tối ưu thu nhập
• HITL leo thang tới quản lý
• cảnh báo khi câu trả lời độ tin cậy thấp
• admin cập nhật tài liệu và agent tự re-index
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-04] AI Agent Tối ưu tuyến & lịch sạc pin cho đội xe điện

### 📝 Mô tả đề tài
📍 Thực trạng: Đội xe điện dịch vụ gọi xe của doanh nghiệp cần cân bằng giữa nhận cuốc và sạc pin; tài xế thường sạc theo cảm tính dẫn tới hết pin giữa ca hoặc xếp hàng chờ sạc giờ cao điểm. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent lập kế hoạch tuyến trong ca kết hợp lịch sạc: dựa trên mức pin (SoC), quãng đường dự kiến, vị trí & tình trạng trạm sạc để khuyến nghị thời điểm/trạm sạc tối ưu; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL khi đề xuất ngắt ca để sạc; an toàn dữ liệu vị trí & tình trạng pin; độ chính xác ước lượng quãng đường/SoC; độ trễ realtime khi trạng thái trạm thay đổi, kiểm soát chi phí tính toán tuyến. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph orchestrator
• OSRM/Google Routes cho routing
• thuật toán tối ưu (OR-Tools) làm tool
• mô hình ước lượng tiêu hao pin
• PostGIS + Redis cho trạng thái trạm realtime
• backend FastAPI
• frontend React + Mapbox
• deploy Docker Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập tài xế & điều hành
• hiển thị tuyến + đề xuất trạm/thời điểm sạc
• mô phỏng SoC theo hành trình
• memory trạng thái ca.

Nâng cao:
• Tối ưu đa xe tránh dồn trạm
• HITL duyệt kế hoạch sạc đội xe
• cảnh báo nguy cơ hết pin & trạm quá tải
• xử lý lỗi khi mất dữ liệu trạm/routing
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-05] AI Agent Phát hiện gian lận cuốc xe & hành vi tài xế bất thường

### 📝 Mô tả đề tài
📍 Thực trạng: Xuất hiện các hành vi gian lận như tạo cuốc ảo để nhận thưởng, GPS spoofing, kéo dài lộ trình bất thường, tài xế và khách thông đồng; đội chống gian lận rà soát thủ công không xuể. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích chuyến đi phát hiện dấu hiệu bất thường (tuyến lệch, tốc độ phi lý, mẫu đặt lặp), điều tra đa bước và lập hồ sơ nghi vấn kèm giải thích; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL bắt buộc trước khi khóa tài khoản/từ chối thưởng; bảo mật dữ liệu điều tra & PII; giảm dương tính giả, giải thích được quyết định; xử lý luồng dữ liệu lớn với độ trễ hợp lý và chi phí kiểm soát. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM cho reasoning & sinh giải trình + LangGraph
• mô hình phát hiện bất thường (Isolation Forest/rule engine) làm tool
• PostGIS phân tích tuyến
• vector DB lưu mẫu gian lận
• backend FastAPI
• frontend React dashboard điều tra
• deploy Docker Railway.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard deploy, đăng nhập analyst & quản lý
• agent chấm điểm rủi ro từng cuốc, liệt kê tín hiệu bất thường có giải thích
• memory hồ sơ điều tra.

Nâng cao:
• Quy trình HITL duyệt/khóa
• graph liên kết tài xế–khách nghi vấn
• cảnh báo realtime chiến dịch gian lận
• feedback loop analyst dán nhãn để cải thiện
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-06] AI Agent Phân tích đánh giá & chấm điểm chất lượng chuyến đi

### 📝 Mô tả đề tài
📍 Thực trạng: Sau mỗi chuyến, khách để lại sao và nhận xét tự do; hàng loạt phản hồi tiêu cực (thái độ, vệ sinh xe, chạy ẩu) không được tổng hợp kịp thời để hành động. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tự động phân tích nhận xét (khía cạnh + cảm xúc), chấm điểm chất lượng tài xế/chuyến, phát hiện vấn đề lặp và đề xuất hành động (nhắc nhở, đào tạo, khen thưởng); đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL trước khi gửi cảnh cáo tài xế; bảo mật dữ liệu đánh giá & danh tính; độ chính xác aspect-based sentiment; xử lý khối lượng lớn với độ trễ/chi phí phù hợp. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM cho aspect-based sentiment + LangGraph
• vector DB gom cụm chủ đề
• PostgreSQL lưu điểm & xu hướng
• backend FastAPI
• frontend React + biểu đồ (Recharts)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập quản lý chất lượng & tài xế (xem điểm của mình)
• agent phân tích nhận xét theo khía cạnh, tổng hợp điểm & top vấn đề
• memory theo tài xế.

Nâng cao:
• Đề xuất hành động cá nhân hóa + HITL duyệt
• cảnh báo tài xế tụt hạng nhanh
• dashboard xu hướng theo vùng/thời gian
• xử lý phản hồi đa ngôn ngữ/nhiễu
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-07] AI Agent Quản lý cho thuê xe điện: booking, hợp đồng & bàn giao

### 📝 Mô tả đề tài
📍 Thực trạng: Mảng cho thuê xe điện của doanh nghiệp của dịch vụ gọi xe của doanh nghiệp cần xử lý đặt thuê, kiểm tra điều kiện khách, soạn hợp đồng, lịch bàn giao/thu hồi và ghi nhận tình trạng xe; quy trình nhiều bước, giấy tờ thủ công dễ nhầm.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent dẫn dắt toàn trình thuê xe: tư vấn gói, kiểm tra tồn xe & điều kiện, tạo hợp đồng, đặt lịch bàn giao và checklist tình trạng xe khi giao/nhận; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL ký duyệt hợp đồng & xử lý sự cố hư hỏng; bảo mật hợp đồng/PII/giấy phép lái xe; độ chính xác điều khoản & tính phí; độ trễ hợp lý, tối ưu chi phí sinh tài liệu. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph
• RAG cho điều khoản & bảng giá
• PostgreSQL quản lý xe/hợp đồng
• tool sinh hợp đồng PDF
• upload ảnh tình trạng xe (lưu object storage)
• backend FastAPI
• frontend React
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập khách & nhân viên
• luồng đặt thuê → kiểm tra tồn → tạo hợp đồng → lịch bàn giao
• checklist ảnh xe
• memory hồ sơ khách.

Nâng cao:
• HITL duyệt & ký hợp đồng
• agent tính phí phát sinh/quá hạn & đề xuất gia hạn
• cảnh báo xe sắp đến hạn/xung đột lịch
• xử lý lỗi khi thiếu giấy tờ
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-08] AI Agent Tổng đài giọng nói đặt xe & tra cứu dịch vụ gọi xe của doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Nhiều khách (đặc biệt lớn tuổi) quen gọi tổng đài đặt xe; nhân viên trực điện thoại tốn nguồn lực, giờ cao điểm nghẽn máy. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giọng nói (voice) tiếp nhận cuộc gọi: nghe yêu cầu đặt xe/tra cứu chuyến/hỏi cước, xác nhận điểm đón-đến bằng lời, gọi tool đặt xe và đọc xác nhận, chuyển người thật khi cần; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL/chuyển tổng đài viên khi nhận diện kém hoặc yêu cầu phức tạp; bảo mật ghi âm & PII; độ chính xác STT tiếng Việt & xác nhận địa chỉ; độ trễ hội thoại thấp (barge-in), kiểm soát chi phí STT/TTS. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• STT tiếng Việt (Whisper/PhoWhisper) + TTS (ElevenLabs/Google) + LLM + LangGraph
• tool geocoding (Mapbox/Google Places) xác nhận địa chỉ
• PostgreSQL chuyến
• backend FastAPI + WebRTC/WebSocket streaming
• frontend React (web call)
• deploy Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web call deploy, đăng nhập khách & tổng đài viên
• luồng thoại đặt xe + xác nhận địa chỉ + đọc kết quả
• transcript & memory hội thoại.

Nâng cao:
• Barge-in & xử lý ngắt lời
• HITL chuyển người thật kèm ngữ cảnh
• cảnh báo độ tin cậy nhận dạng thấp
• fallback sang nhập tay khi STT lỗi và guardrail PII
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-09] AI Agent Dự báo & quản lý vận hành trạm sạc

### 📝 Mô tả đề tài
📍 Thực trạng: Trạm sạc phục vụ đội xe điện dịch vụ gọi xe của doanh nghiệp có lúc quá tải, lúc trống; sự cố trụ sạc và lịch bảo trì chưa được dự báo, gây gián đoạn ca chạy. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent dự báo mức sử dụng trạm theo giờ, phát hiện trụ bất thường, đề xuất phân bổ xe tới trạm ít tải và lên lịch bảo trì phòng ngừa; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL cho lệnh đóng trạm/bảo trì; bảo mật dữ liệu vận hành; sai số dự báo tải & cảnh báo sớm sự cố; độ trễ cập nhật trạng thái trạm thấp, tối ưu chi phí. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph
• mô hình dự báo tải (LightGBM/Prophet) + phát hiện bất thường làm tool
• Redis realtime trạng thái trụ
• PostGIS bản đồ trạm
• backend FastAPI
• frontend React + Mapbox + Recharts
• deploy Docker Railway.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard deploy, đăng nhập vận hành trạm & điều hành đội xe
• dự báo tải theo trạm/giờ
• agent đề xuất phân bổ xe
• memory theo trạm.

Nâng cao:
• Lịch bảo trì phòng ngừa + HITL duyệt
• cảnh báo trụ lỗi/quá tải realtime
• mô phỏng thêm trụ/tăng nhu cầu
• xử lý lỗi khi mất tín hiệu trạm
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-10] AI Agent Phân tích hủy chuyến & giữ chân khách hàng

### 📝 Mô tả đề tài
📍 Thực trạng: Tỷ lệ hủy chuyến và khách rời bỏ (churn) ảnh hưởng doanh thu; nguyên nhân (chờ lâu, giá, trải nghiệm xấu) chưa được phân tích hệ thống để can thiệp kịp thời. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích nguyên nhân hủy chuyến theo phân khúc, dự đoán khách có nguy cơ rời bỏ và đề xuất hành động giữ chân (ưu đãi, xin lỗi, ưu tiên) cá nhân hóa; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL duyệt cấp ưu đãi/ngân sách giữ chân; bảo mật dữ liệu hành vi khách; độ chính xác mô hình churn & giải thích; kiểm soát chi phí ưu đãi và độ trễ chiến dịch. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph
• mô hình churn/hủy (LightGBM) + SHAP giải thích làm tool
• PostgreSQL dữ liệu khách
• vector DB gom lý do hủy dạng text
• backend FastAPI
• frontend React + Recharts
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard deploy, đăng nhập marketing & CSKH
• phân tích nguyên nhân hủy theo phân khúc
• danh sách khách nguy cơ churn có lý do
• memory theo khách.

Nâng cao:
• Đề xuất hành động giữ chân cá nhân hóa + HITL duyệt ngân sách
• mô phỏng tác động ưu đãi
• cảnh báo vượt ngân sách
• feedback loop cập nhật hiệu quả chiến dịch
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-11] AI Agent Gợi ý khuyến mãi cá nhân hóa cho khách dịch vụ gọi xe của doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Chương trình khuyến mãi phát đại trà gây lãng phí ngân sách và ít hiệu quả; khách nhận mã không phù hợp thói quen di chuyển. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent xây chân dung khách từ lịch sử chuyến (tuyến, giờ, tần suất, loại xe) và đề xuất gói khuyến mãi tối ưu chuyển đổi trên ngân sách cho trước, biết lập kế hoạch phân bổ; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL duyệt chiến dịch & hạn mức ngân sách; bảo mật dữ liệu hành vi; đo lường uplift, tránh khuyến mãi cho khách vốn đã trung thành; độ trễ & chi phí hợp lý. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph
• mô hình phân khúc (RFM/clustering) + uplift làm tool
• PostgreSQL
• vector DB hồ sơ khách
• backend FastAPI
• frontend React (bảng chiến dịch) + Recharts
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập marketer & quản lý
• agent tạo phân khúc & gợi ý voucher/khung giờ theo từng nhóm
• memory chiến dịch.

Nâng cao:
• Tối ưu phân bổ ngân sách + HITL duyệt
• mô phỏng uplift/ROI
• cảnh báo vượt ngân sách hoặc trùng lặp ưu đãi
• A/B test và cập nhật đề xuất theo kết quả
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-12] AI Agent Hỗ trợ đăng ký & đào tạo tài xế mới (onboarding)

### 📝 Mô tả đề tài
📍 Thực trạng: Quy trình gia nhập tài xế dịch vụ gọi xe của doanh nghiệp gồm nhiều bước (giấy tờ, kiểm tra điều kiện, học chính sách, làm bài kiểm tra); nhiều ứng viên bỏ dở vì thủ tục rối và thiếu hướng dẫn. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent dẫn dắt onboarding: hướng dẫn nộp & kiểm tra giấy tờ, giải đáp, tạo lộ trình học chính sách và tổ chức kiểm tra kiến thức, theo dõi tiến độ tới khi kích hoạt; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL phê duyệt hồ sơ & kết quả cuối; bảo mật giấy tờ tùy thân/GPLX; độ chính xác kiểm tra tính hợp lệ giấy tờ; độ trễ & chi phí OCR hợp lý. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph
• OCR (Tesseract/Vision API) kiểm tra giấy tờ làm tool
• RAG chính sách đào tạo
• PostgreSQL theo dõi tiến độ
• backend FastAPI
• frontend React (wizard nhiều bước)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập ứng viên & cán bộ tuyển
• luồng nộp giấy tờ + OCR kiểm tra + học & quiz chính sách
• memory tiến độ ứng viên.

Nâng cao:
• HITL duyệt hồ sơ/kết quả
• agent nhắc bước còn thiếu & cá nhân hóa nội dung học yếu
• cảnh báo giấy tờ không hợp lệ/hết hạn
• xử lý lỗi OCR và fallback nhập tay
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-13] AI Agent Giám sát sự cố & an toàn hành trình realtime

### 📝 Mô tả đề tài
📍 Thực trạng: Trong hành trình có thể xảy ra sự cố (dừng bất thường, lệch tuyến, tốc độ nguy hiểm, khách bấm SOS); trung tâm an toàn khó theo dõi đồng thời nhiều chuyến. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát tín hiệu hành trình, phát hiện dấu hiệu bất thường/rủi ro an toàn, phân loại mức độ và điều phối phản ứng (gọi tài xế/khách, báo trung tâm, gọi cứu hộ) theo kịch bản; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL bắt buộc cho các hành động khẩn (báo công an/cứu hộ); bảo mật dữ liệu vị trí/SOS; độ chính xác phân loại rủi ro & giảm báo động giả; độ trễ realtime rất thấp, chi phí kiểm soát. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM điều phối kịch bản + LangGraph
• rule/anomaly detection trên telemetry làm tool
• PostGIS + Redis stream vị trí realtime
• tool thông báo (SMS/call giả lập)
• backend FastAPI + WebSocket
• frontend React + Mapbox live
• deploy Fly.io.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard deploy, đăng nhập nhân viên an toàn & tài xế
• bản đồ live + phát hiện & phân loại sự cố
• agent đề xuất phản ứng theo mức
• memory nhật ký sự cố.

Nâng cao:
• Quy trình leo thang HITL cho tình huống khẩn
• playbook tự động (gọi/nhắn) có xác nhận
• cảnh báo cụm sự cố theo khu vực
• xử lý mất tín hiệu GPS
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-14] AI Agent Tối ưu phân bổ & huy động xe giờ cao điểm

### 📝 Mô tả đề tài
📍 Thực trạng: Giờ cao điểm/mưa/sự kiện, nhu cầu tăng đột biến gây thiếu xe cục bộ, thời gian chờ dài và khách hủy; việc huy động tài xế online và điều xe còn bị động. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent nhận biết sốt cầu theo khu vực, đề xuất kích hoạt ưu đãi cho tài xế, điều phối relocate và ước tính hệ số giá động hợp lý, có kế hoạch nhiều bước theo thời gian thực; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL duyệt giá động & gói huy động; bảo mật dữ liệu vận hành; độ chính xác nhận diện đột biến & công bằng giá; độ trễ realtime, kiểm soát chi phí ưu đãi. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph
• mô hình phát hiện đột biến cầu + tối ưu phân bổ (OR-Tools) làm tool
• dữ liệu địa lý H3 + PostGIS
• Redis realtime
• backend FastAPI + WebSocket
• frontend React + Mapbox heatmap
• deploy Docker Railway.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard deploy, đăng nhập điều hành & tài xế
• phát hiện vùng sốt cầu + đề xuất relocate/huy động
• memory phiên điều hành.

Nâng cao:
• Đề xuất hệ số giá động + HITL duyệt
• mô phỏng kịch bản mưa/sự kiện
• cảnh báo mất cân đối cung-cầu & vượt ngân sách ưu đãi
• xử lý thiếu dữ liệu realtime
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-15] AI Agent Lắng nghe & phân tích phản hồi mạng xã hội về dịch vụ gọi xe của doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Người dùng bàn luận về dịch vụ gọi xe của doanh nghiệp trên Facebook, TikTok, báo chí, review app; đội truyền thông khó theo dõi và phản ứng kịp với khủng hoảng hoặc xu hướng tiêu cực. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent thu thập & phân tích phản hồi social (cảm xúc, chủ đề, đối tượng nhắc đến), phát hiện khủng hoảng sớm, tổng hợp insight và đề xuất/nháp phản hồi truyền thông; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL bắt buộc trước khi đăng phản hồi chính thức; tuân thủ nguồn dữ liệu & bảo mật; độ chính xác sentiment/chủ đề tiếng Việt (mỉa mai, tiếng lóng); độ trễ phát hiện khủng hoảng thấp, tối ưu chi phí xử lý. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM cho sentiment/topic + LangGraph
• công cụ thu thập (RSS/API hoặc dataset mô phỏng) làm tool
• vector DB gom cụm chủ đề
• PostgreSQL lưu bài & xu hướng
• backend FastAPI
• frontend React + Recharts (word cloud, timeline)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard deploy, đăng nhập truyền thông & quản lý
• phân tích cảm xúc/chủ đề theo thời gian & kênh
• agent tóm tắt insight
• memory theo chiến dịch/chủ đề.

Nâng cao:
• Cảnh báo khủng hoảng sớm (spike tiêu cực)
• nháp phản hồi + HITL duyệt trước khi đăng
• phân loại influencer/độ lan truyền
• xử lý nhiễu spam & phát hiện mỉa mai
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-16] AI Agent Hỗ trợ khách doanh nghiệp (B2B) đặt & quản lý xe

### 📝 Mô tả đề tài
📍 Thực trạng: Khách doanh nghiệp dùng dịch vụ gọi xe của doanh nghiệp cho công tác/đưa đón nhân viên cần đặt nhiều chuyến, phân bổ hạn mức phòng ban, xuất hóa đơn và báo cáo chi phí; hiện xử lý thủ công qua email/nhân viên account. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent B2B hỗ trợ đặt chuyến theo lô/lịch, quản lý hạn mức & chính sách chi tiêu công ty, đối soát và tổng hợp báo cáo chi phí theo phòng ban; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL duyệt chuyến vượt hạn mức & xuất hóa đơn; bảo mật dữ liệu doanh nghiệp & nhân viên; độ chính xác đối soát chi phí; độ trễ & chi phí hợp lý khi xử lý khối lượng lớn. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph
• RAG chính sách chi tiêu công ty
• PostgreSQL đa tenant
• tool đặt chuyến lô & sinh báo cáo/hóa đơn (PDF/Excel)
• backend FastAPI
• frontend React (admin doanh nghiệp)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập admin doanh nghiệp & nhân viên
• đặt chuyến theo lịch/lô, kiểm tra hạn mức, xem lịch sử
• memory theo tổ chức.

Nâng cao:
• HITL duyệt vượt hạn mức & duyệt hóa đơn
• báo cáo chi phí theo phòng ban + phát hiện chi tiêu bất thường
• cảnh báo gần chạm hạn mức
• xử lý lỗi khi dữ liệu tổ chức thiếu
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-17] AI Agent Trợ lý tìm kiếm đồ thất lạc & xử lý bồi thường

### 📝 Mô tả đề tài
📍 Thực trạng: Khách để quên đồ trên xe dịch vụ gọi xe của doanh nghiệp khá phổ biến; quy trình báo mất, liên hệ tài xế, xác minh và hoàn trả/bồi thường rời rạc, tốn thời gian và dễ tranh cãi. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tiếp nhận báo mất đồ, xác định chuyến & tài xế liên quan, điều phối liên hệ tài xế, hướng dẫn nhận lại và xử lý bồi thường khi cần, theo quy trình nhiều bước; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL cho quyết định bồi thường & đối chất tranh chấp; bảo mật thông tin liên hệ hai bên (ẩn danh số điện thoại); độ chính xác khớp chuyến/mô tả đồ; độ trễ & chi phí hợp lý. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph
• RAG quy trình lost&found
• PostgreSQL chuyến/khiếu nại
• tool liên hệ ẩn danh (masking) & tạo ticket
• (tùy chọn) so khớp ảnh đồ
• backend FastAPI
• frontend React
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập khách & nhân viên L&F
• luồng báo mất → khớp chuyến/tài xế → tạo ticket → theo dõi
• memory hồ sơ vụ việc.

Nâng cao:
• HITL duyệt bồi thường & xử lý tranh chấp
• liên hệ ẩn danh giữa khách–tài xế
• cảnh báo vụ quá hạn/giá trị cao
• xử lý trường hợp không khớp được chuyến
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-18] AI Agent Trợ lý bảo dưỡng & chẩn đoán sức khỏe đội xe điện

### 📝 Mô tả đề tài
📍 Thực trạng: Đội xe điện dịch vụ gọi xe của doanh nghiệp cần bảo dưỡng theo km/thời gian và theo dõi sức khỏe pin, lốp, phanh; lịch bảo dưỡng thủ công dễ bỏ sót, xe hỏng đột xuất làm gián đoạn dịch vụ. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent theo dõi dữ liệu vận hành & cảnh báo lỗi từ tài xế, chẩn đoán sơ bộ mức độ nghiêm trọng, lập lịch bảo dưỡng phòng ngừa và điều phối xe vào xưởng tối ưu downtime; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL duyệt đưa xe ngừng chạy/vào xưởng; an toàn dữ liệu kỹ thuật xe; độ chính xác chẩn đoán & ưu tiên đúng mức; độ trễ cảnh báo thấp, chi phí hợp lý. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph
• RAG sổ tay kỹ thuật/triệu chứng lỗi
• mô hình dự báo hao mòn/bảo dưỡng làm tool
• PostgreSQL hồ sơ xe
• backend FastAPI
• frontend React + lịch/Gantt
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập kỹ thuật viên & tài xế
• nhận báo lỗi + chẩn đoán sơ bộ có trích tài liệu
• lịch bảo dưỡng theo km/thời gian
• memory theo xe.

Nâng cao:
• Dự báo bảo dưỡng phòng ngừa + HITL duyệt đưa xe vào xưởng
• tối ưu lịch giảm downtime đội
• cảnh báo lỗi nghiêm trọng/pin suy giảm
• xử lý dữ liệu thiếu
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-19] AI Agent Trợ lý đặt xe đa phương thức & lập lộ trình cho khách

### 📝 Mô tả đề tài
📍 Thực trạng: Khách thường có nhu cầu phức tạp: đi nhiều điểm, chọn loại phương tiện (taxi điện, xe máy điện, thuê xe), tối ưu chi phí/thời gian, hoặc đặt trước cho lịch trình cả ngày; app truyền thống chỉ đặt từng chuyến rời rạc. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hội thoại hiểu nhu cầu tự nhiên, lập lộ trình đa điểm, so sánh phương án phương tiện theo chi phí/thời gian và đặt loạt chuyến theo lịch, có lập kế hoạch và dùng tool bản đồ; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL xác nhận trước khi đặt loạt & thanh toán; bảo mật lịch trình/PII; độ chính xác ước tính thời gian/giá & khả thi lộ trình; độ trễ hợp lý, tối ưu chi phí gọi routing. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM + LangGraph
• routing & geocoding (Google Directions/Mapbox) + tối ưu điểm dừng làm tool
• PostgreSQL chuyến & lịch
• backend FastAPI streaming
• frontend React + Mapbox
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập khách & CSKH
• hội thoại lập lộ trình đa điểm + so sánh phương tiện + đặt theo lịch
• memory ngữ cảnh & sở thích.

Nâng cao:
• HITL xác nhận đặt loạt/thanh toán
• tối ưu thứ tự điểm dừng & đề xuất tiết kiệm
• cảnh báo lộ trình bất khả thi/ngoài vùng phục vụ
• xử lý lỗi routing & fallback
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---

## [GSM-20] AI Agent Phân tích vận hành & báo cáo thông minh cho quản lý dịch vụ gọi xe của doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Quản lý vùng cần theo dõi hàng loạt chỉ số (chuyến, doanh thu, tỷ lệ hoàn thành, thời gian chờ, hiệu suất tài xế, tình trạng pin) nằm rải rác nhiều báo cáo; việc hỏi số liệu và tìm nguyên nhân bất thường tốn nhiều thời gian. Trong vận hành dịch vụ gọi xe công nghệ quy mô lớn, dữ liệu hành trình GPS, biến động cung – cầu theo thời tiết/giờ cao điểm và trạng thái pin/trạm sạc của đội xe điện thay đổi từng phút với nhiều tình huống ngoại lệ.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích dạng hỏi-đáp bằng ngôn ngữ tự nhiên trên dữ liệu vận hành: tự sinh truy vấn, tạo biểu đồ, phát hiện bất thường theo khu vực/thời gian và diễn giải nguyên nhân kèm khuyến nghị; đồng thời kết hợp mô hình dự báo/tối ưu hóa không gian – thời gian và kiểm tra ràng buộc vận hành (lộ trình GPS, cước phí, dung lượng pin, thời gian chờ sạc) bằng thuật toán xác định với khả năng điều phối đa bước của AI Agent.

🔒 Ràng buộc: HITL duyệt trước khi gửi báo cáo/đề xuất hành động cấp cao; phân quyền & bảo mật dữ liệu theo vai trò/vùng; độ chính xác truy vấn (chống sai số/bịa số); độ trễ & chi phí truy vấn hợp lý. Mọi phép tính cước phí, hoàn tiền, lộ trình và ràng buộc dung lượng pin phải được kiểm chứng bằng công cụ tính toán xác định; đánh giá định lượng trên dữ liệu hành trình và kịch bản cao điểm thực tế.

### 🛠️ Tech Stack
• LLM text-to-SQL + LangGraph
• PostgreSQL kho dữ liệu vận hành
• tool sinh biểu đồ & phát hiện bất thường
• vector DB cho tự điển chỉ số/định nghĩa
• backend FastAPI
• frontend React + Recharts (dashboard hội thoại)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu vận hành di chuyển đô thị thực tế NYC TLC Trip Record Data, DiDi GAIA Open Dataset, lưới không gian lục giác Uber H3, bộ định tuyến OSRM/GTFS và dữ liệu sạc xe điện ACN-Data / NASA Battery.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard deploy, đăng nhập quản lý & analyst (phân quyền theo vùng)
• hỏi đáp NL sinh bảng/biểu đồ
• phát hiện bất thường cơ bản
• memory phiên phân tích.

Nâng cao:
• Diễn giải nguyên nhân & khuyến nghị + HITL duyệt báo cáo
• báo cáo định kỳ tự động
• cảnh báo KPI vượt ngưỡng & giới hạn truy vấn/chi phí
• guardrail chống truy vấn sai quyền và kiểm chứng số liệu
• Kết hợp mô hình tối ưu hóa vận trù/phân tích quỹ đạo không gian (H3/OSRM/OR-Tools) với hệ thống đa tác tử để xử lý các kịch bản biến động cung – cầu, gian lận hoặc sự cố thời gian thực.

---
