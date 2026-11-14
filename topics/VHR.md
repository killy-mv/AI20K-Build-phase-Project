# Lĩnh vực: VHR - Bất động sản – Ứng dụng cư dân & Quản lý khu đô thị

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `VHR-01` | [ResidentGPT – AI Agent Trợ lý Cư dân Hỏi-Đáp Nội quy & Tiện ích](#vhr-01) |
| `VHR-02` | [AmenityBook AI – Agent Đặt & Tối ưu Lịch Tiện ích (Gym, Bể bơi, Tennis, BBQ)](#vhr-02) |
| `VHR-03` | [FeeSense AI – Agent Tra cứu, Giải thích & Nhắc Phí Dịch vụ Thông minh](#vhr-03) |
| `VHR-04` | [FixIt Agent – AI Tiếp nhận, Phân loại & Định tuyến Phản ánh/Sự cố Tự động](#vhr-04) |
| `VHR-05` | [HomeCare Agent – AI Đặt lịch & Điều phối Bảo trì Căn hộ](#vhr-05) |
| `VHR-06` | [GateKeeper AI – Agent Quản lý Ra vào, Đăng ký Khách & Thẻ Cư dân](#vhr-06) |
| `VHR-07` | [NeighborMarket AI – Agent Chợ Cư dân & Kiểm duyệt Tin đăng Tự động](#vhr-07) |
| `VHR-08` | [ConciergeVin AI – Agent Đặt Dịch vụ Gia đình (Giúp việc, Giặt là, Gửi trẻ)](#vhr-08) |
| `VHR-09` | [BQL Copilot – Agent Tổng hợp Phản ánh & Sinh Báo cáo Vận hành](#vhr-09) |
| `VHR-10` | [EcoSaver AI – Agent Phân tích & Gợi ý Tiết kiệm Điện Nước](#vhr-10) |
| `VHR-11` | [ParkSmart AI – Agent Quản lý & Điều phối Gửi xe Thông minh](#vhr-11) |
| `VHR-12` | [CommunityVoice AI – Agent Khảo sát & Phân tích Mức độ Hài lòng Cư dân](#vhr-12) |
| `VHR-13` | [SOS Resident AI – Agent Hỗ trợ Khẩn cấp & Điều phối An ninh](#vhr-13) |
| `VHR-14` | [EventHub AI – Agent Tổ chức & Điều phối Sự kiện Cộng đồng](#vhr-14) |
| `VHR-15` | [NotifyMe AI – Agent Thông báo Cộng đồng Cá nhân hóa & Chống Nhiễu](#vhr-15) |
| `VHR-16` | [MoveInMate AI – Agent Hỗ trợ Cư dân Mới Onboarding vào Khu](#vhr-16) |
| `VHR-17` | [GreenBin AI – Agent Phân loại Rác & Điều phối Thu gom Tái chế](#vhr-17) |
| `VHR-18` | [PetPal AI – Agent Quản lý Thú cưng & Dịch vụ Thú cưng trong Khu](#vhr-18) |
| `VHR-19` | [ShuttleBus AI – Agent Đặt chỗ & Điều phối Xe buýt Nội khu/dịch vụ gọi xe của doanh nghiệp](#vhr-19) |
| `VHR-20` | [ResiDeals AI – Agent Ưu đãi Nội khu & Gợi ý Tiện ích Thương mại Cá nhân hóa](#vhr-20) |

---

## [VHR-01] ResidentGPT – AI Agent Trợ lý Cư dân Hỏi-Đáp Nội quy & Tiện ích

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân doanh nghiệp bất động sản liên tục gọi tổng đài/hỏi nhóm Zalo cư dân về giờ mở bể bơi, quy định nuôi thú cưng, cách đăng ký thẻ xe... khiến Ban Quản Lý (BQL) quá tải và thông tin trả lời không nhất quán. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hiểu bộ tài liệu nội quy/tiện ích của từng khu, tự lập kế hoạch tra cứu nhiều nguồn (RAG), trả lời chính xác kèm trích dẫn điều khoản, biết chuyển tiếp (escalate) tới nhân viên khi không đủ tự tin; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho phép BQL duyệt/chỉnh câu trả lời mẫu và huấn luyện lại; bảo mật dữ liệu cư dân (không lộ SĐT/căn hộ giữa các cư dân); độ chính xác cao có trích nguồn, từ chối bịa; kiểm soát chi phí token và thời gian phản hồi < 5s. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini / Llama-3.1-8B
• Agent framework: LangGraph (router + retriever + answer node)
• RAG với embedding text-embedding-3-small
• Vector DB: Qdrant/Chroma
• Backend: FastAPI (Python)
• Frontend: Next.js + Tailwind
• Auth: Clerk/Supabase Auth (vai trò Cư dân & BQL)
• Deploy: Render/Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web đã deploy, đăng nhập 2 vai trò (Cư dân, BQL)
• agent RAG trả lời câu hỏi nội quy/tiện ích có trích dẫn, lưu lịch sử hội thoại (memory), escalate khi confidence thấp.

Nâng cao:
• Multi-agent (agent phân loại chủ đề + agent tra cứu + agent kiểm chứng), BQL upload/cập nhật tài liệu và duyệt câu trả lời (HITL), bảng eval độ chính xác (faithfulness/relevance) và dashboard tỉ lệ câu hỏi tự động giải quyết
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-02] AmenityBook AI – Agent Đặt & Tối ưu Lịch Tiện ích (Gym, Bể bơi, Tennis, BBQ)

### 📝 Mô tả đề tài
📍 Thực trạng: Đặt sân tennis, slot gym, khu BBQ ở doanh nghiệp bất động sản hiện làm thủ công qua lễ tân hoặc form rời rạc, gây trùng lịch, quá tải giờ cao điểm và tranh chấp. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hiểu yêu cầu ngôn ngữ tự nhiên ("đặt sân tennis chiều mai cho 2 người gần block S1"), kiểm tra tình trạng trống theo thời gian thực bằng tool-use, đề xuất khung giờ tối ưu, xử lý xung đột và giữ chỗ; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL khi đặt vượt hạn mức/ngoài giờ cần BQL duyệt; bảo mật lịch cá nhân cư dân; chính xác về tình trạng slot (không double-booking); hiệu năng khi nhiều cư dân đặt đồng thời và giới hạn số lần đặt/tuần. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph với function-calling (check_availability, hold_slot, confirm_booking)
• DB: PostgreSQL (lịch tiện ích)
• Backend: FastAPI
• Frontend: Next.js + FullCalendar
• Auth: Supabase (Cư dân, BQL)
• Realtime: Supabase Realtime
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập 2 vai trò
• agent nhận yêu cầu tự nhiên, gọi tool kiểm tra & đặt tiện ích, tránh trùng lịch, gửi xác nhận, ghi nhớ sở thích cư dân.

Nâng cao:
• Agent gợi ý khung giờ tối ưu dựa trên dữ liệu tải sử dụng, hàng chờ (waitlist) tự động lấp slot bị hủy, HITL cho BQL duyệt yêu cầu đặc biệt, eval tỉ lệ đặt thành công & mức lấp đầy tiện ích
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-03] FeeSense AI – Agent Tra cứu, Giải thích & Nhắc Phí Dịch vụ Thông minh

### 📝 Mô tả đề tài
📍 Thực trạng: Hóa đơn phí dịch vụ, phí gửi xe, điện nước ở doanh nghiệp bất động sản gồm nhiều khoản mục khiến cư dân khó hiểu, hay thắc mắc "vì sao tháng này tăng?" và quên hạn thanh toán. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent truy vấn dữ liệu hóa đơn của đúng căn hộ, giải thích từng khoản bằng ngôn ngữ đời thường, so sánh với tháng trước, phát hiện bất thường và chủ động nhắc/hỗ trợ thanh toán; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho khiếu nại hóa đơn phải chuyển kế toán BQL duyệt; bảo mật nghiêm ngặt dữ liệu tài chính từng hộ (phân quyền theo căn hộ); tính toán chính xác tuyệt đối; kiểm soát chi phí và thời gian phản hồi. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph (NL2SQL/tool truy vấn hóa đơn + agent giải thích)
• DB: PostgreSQL
• Payment (mock/sandbox): VNPay/MoMo sandbox
• Backend: FastAPI
• Frontend: Next.js + Recharts
• Auth: Supabase (Cư dân, Kế toán BQL)
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập theo căn hộ
• agent tra cứu & giải thích hóa đơn, hiển thị biểu đồ khoản mục, tạo link thanh toán sandbox, nhắc hạn.

Nâng cao:
• Agent phát hiện bất thường/tăng đột biến và cảnh báo, dự báo phí tháng tới, quy trình khiếu nại có HITL (kế toán duyệt), dashboard công nợ cho BQL và eval độ chính xác giải thích
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-04] FixIt Agent – AI Tiếp nhận, Phân loại & Định tuyến Phản ánh/Sự cố Tự động

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân gửi phản ánh (rò nước, hỏng đèn hành lang, ồn ào, thang máy lỗi) rải rác qua nhiều kênh, BQL phân loại thủ công nên chậm, thất lạc và khó theo dõi tiến độ. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent nhận mô tả (kèm ảnh), tự phân loại loại sự cố & mức ưu tiên, định tuyến đúng bộ phận (kỹ thuật/vệ sinh/an ninh), tạo ticket, ước tính thời gian xử lý và cập nhật trạng thái cho cư dân; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho sự cố khẩn/nghiêm trọng cần điều phối viên xác nhận trước khi cử người; bảo mật thông tin & ảnh trong căn hộ; phân loại chính xác để không định tuyến sai; hiệu năng xử lý hàng loạt ticket giờ cao điểm. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o (đa phương thức đọc ảnh) + GPT-4o-mini
• Agent: LangGraph (classify → prioritize → route → notify)
• Vision cho ảnh sự cố
• DB: PostgreSQL (ticket)
• Backend: FastAPI
• Frontend: Next.js
• Auth: Supabase (Cư dân, Điều phối viên BQL, Kỹ thuật viên)
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, 3 vai trò
• agent nhận phản ánh + ảnh, phân loại & gán mức ưu tiên, tạo và định tuyến ticket, cư dân theo dõi trạng thái.

Nâng cao:
• Multi-agent (triage + routing + SLA-tracker), tự phát hiện ticket trùng/liên quan gộp lại, HITL điều phối viên duyệt định tuyến, dashboard SLA & eval độ chính xác phân loại/ưu tiên
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-05] HomeCare Agent – AI Đặt lịch & Điều phối Bảo trì Căn hộ

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân cần bảo trì định kỳ (vệ sinh điều hòa, kiểm tra điện nước, bơm ga) nhưng việc đặt lịch với đội kỹ thuật thủ công, hay trùng giờ và thiếu nhắc nhở bảo trì định kỳ. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tư vấn hạng mục bảo trì phù hợp thiết bị trong căn hộ, đề xuất & đặt lịch theo lịch trống của kỹ thuật viên, ước tính chi phí, gửi nhắc và lập lịch bảo trì định kỳ tự động; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho hạng mục chi phí cao/ngoài gói dịch vụ cần cư dân xác nhận; bảo mật dữ liệu thiết bị & lịch cư dân; chính xác lịch và tránh trùng đội kỹ thuật; tối ưu tuyến di chuyển của kỹ thuật viên để tiết kiệm chi phí. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph (recommend → schedule → remind)
• Tool: check kỹ thuật viên availability, tạo lịch
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js + calendar UI
• Auth: Supabase (Cư dân, Kỹ thuật viên, BQL)
• Cron/scheduler cho nhắc định kỳ
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent tư vấn hạng mục, đặt lịch bảo trì theo slot kỹ thuật viên, gửi nhắc, lưu hồ sơ bảo trì thiết bị (memory).

Nâng cao:
• Agent lập lịch bảo trì định kỳ tự động & tối ưu tuyến cho nhiều căn cùng khu, ước tính chi phí thông minh, HITL xác nhận hạng mục đắt, eval mức lấp đầy lịch kỹ thuật viên
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-06] GateKeeper AI – Agent Quản lý Ra vào, Đăng ký Khách & Thẻ Cư dân

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân đăng ký khách đến chơi, shipper, người giúp việc qua nhiều bước thủ công tại chốt bảo an, gây ùn tắc và khó kiểm soát người lạ. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent cho phép cư dân đăng ký khách bằng ngôn ngữ tự nhiên, sinh mã QR/OTP ra vào, xác minh danh tính, cảnh báo bảo an khi có bất thường và ghi nhận lịch sử ra vào theo căn hộ; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho khách ở lại qua đêm/ra vào ngoài khung giờ cần bảo an duyệt; bảo mật danh tính khách & dữ liệu ra vào; chính xác trong nhận diện/khớp mã; hiệu năng thời gian thực tại chốt cổng. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph (register → verify → issue_pass → alert)
• Tool sinh QR/OTP
• DB: PostgreSQL (access log)
• Backend: FastAPI
• Frontend: Next.js (app cư dân + màn hình chốt bảo an)
• Auth: Supabase (Cư dân, Bảo an, BQL)
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent đăng ký khách, sinh QR/OTP, ghi log ra vào, bảo an quét & xác nhận.

Nâng cao:
• Agent phát hiện bất thường (khách lạ tần suất cao, ngoài giờ) và cảnh báo, phân tích lưu lượng ra vào theo khung giờ, HITL bảo an duyệt trường hợp đặc biệt, dashboard an ninh & eval tỉ lệ cảnh báo đúng
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-07] NeighborMarket AI – Agent Chợ Cư dân & Kiểm duyệt Tin đăng Tự động

### 📝 Mô tả đề tài
📍 Thực trạng: Nhóm mua-bán/second-hand trong doanh nghiệp bất động sản trên Zalo/Facebook lộn xộn, khó tìm món cần, nhiều tin rác/lừa đảo và không có kiểm duyệt. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giúp cư dân đăng tin (tự viết mô tả, gợi ý giá, gắn nhãn), kiểm duyệt nội dung cấm/lừa đảo, tìm kiếm ngữ nghĩa và kết nối người mua-bán trong cùng khu; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho tin bị gắn cờ nghi ngờ cần BQL/kiểm duyệt viên duyệt; bảo mật thông tin liên hệ (ẩn SĐT, chat trong app); chính xác trong kiểm duyệt (tránh chặn nhầm); tối ưu chi phí embedding cho lượng tin lớn. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini + moderation API
• Agent: LangGraph (draft_listing → moderate → embed → match)
• Vector DB: Qdrant (tìm kiếm ngữ nghĩa)
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js
• Auth: Supabase (Cư dân, Kiểm duyệt viên)
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent hỗ trợ đăng tin & gợi ý giá, kiểm duyệt tự động, tìm kiếm ngữ nghĩa, chat ẩn danh trong app.

Nâng cao:
• Agent phát hiện lừa đảo/tin trùng, gợi ý sản phẩm cá nhân hóa theo lịch sử, HITL hàng đợi kiểm duyệt, eval độ chính xác moderation (precision/recall) và dashboard hoạt động chợ
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-08] ConciergeVin AI – Agent Đặt Dịch vụ Gia đình (Giúp việc, Giặt là, Gửi trẻ)

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân cần đặt giúp việc theo giờ, giặt là, trông trẻ nhưng phải tự tìm và liên hệ nhiều nhà cung cấp, thiếu đánh giá và khó so sánh. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hiểu nhu cầu ("cần giúp việc 3 tiếng sáng thứ 7 dọn 2 phòng ngủ"), khớp nhà cung cấp phù hợp theo lịch/khu/đánh giá, báo giá, đặt lịch và điều phối; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho đơn giá trị cao/dịch vụ trông trẻ cần xác nhận nhà cung cấp đã xác minh; bảo mật thông tin gia đình & lịch sinh hoạt; chính xác trong khớp lịch & báo giá; tối ưu chi phí và tránh spam nhà cung cấp. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: CrewAI/LangGraph (need-parser + matcher + booking)
• DB: PostgreSQL (NCC, đơn)
• Backend: FastAPI
• Frontend: Next.js
• Auth: Supabase (Cư dân, Nhà cung cấp, BQL)
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent phân tích nhu cầu, khớp & đề xuất nhà cung cấp, đặt lịch, thu thập đánh giá sau dịch vụ (memory sở thích).

Nâng cao:
• Multi-agent (matching + pricing + review-analyzer), gợi ý cá nhân hóa & định giá động theo cung cầu, HITL xác minh NCC cho dịch vụ nhạy cảm, eval mức độ khớp và dashboard vận hành
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-09] BQL Copilot – Agent Tổng hợp Phản ánh & Sinh Báo cáo Vận hành

### 📝 Mô tả đề tài
📍 Thực trạng: BQL doanh nghiệp bất động sản nhận hàng trăm phản ánh/ticket mỗi tuần nhưng tổng hợp báo cáo tình hình vận hành, điểm nóng, xu hướng bằng tay rất mất thời gian và thiếu insight. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent đọc toàn bộ ticket/phản ánh, gom cụm chủ đề, phát hiện vấn đề lặp lại & điểm nóng theo tòa, tự sinh báo cáo tuần/tháng có biểu đồ và đề xuất hành động; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho báo cáo trước khi phát hành phải BQL duyệt/chỉnh; bảo mật dữ liệu vận hành nội bộ (chỉ BQL); chính xác trong trích số liệu (không bịa số); tối ưu chi phí khi xử lý khối lượng lớn văn bản. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o + GPT-4o-mini
• Agent: LangGraph (cluster → analyze → draft_report)
• Embedding + clustering
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js + Recharts
• Xuất PDF/Docx
• Auth: Supabase (chỉ vai trò BQL, phân cấp Trưởng BQL/nhân viên)
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy cho BQL
• agent gom cụm phản ánh, thống kê điểm nóng, sinh báo cáo có biểu đồ & xuất file.

Nâng cao:
• Multi-agent (data-analyst + writer + reviewer), phát hiện xu hướng bất thường & cảnh báo sớm, đề xuất hành động ưu tiên, HITL duyệt báo cáo, eval độ chính xác số liệu trích xuất so với dữ liệu gốc
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-10] EcoSaver AI – Agent Phân tích & Gợi ý Tiết kiệm Điện Nước

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân doanh nghiệp bất động sản chỉ thấy tổng tiền điện nước cuối tháng, không hiểu vì sao cao và thiếu gợi ý tiết kiệm cụ thể cho căn hộ mình. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích dữ liệu tiêu thụ theo thời gian, so sánh với căn tương tự, phát hiện thiết bị/thời điểm ngốn điện nước, và đưa ra gợi ý hành động cá nhân hóa kèm ước tính tiền tiết kiệm; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho cảnh báo bất thường (nghi rò nước) cần cư dân/BQL xác nhận; bảo mật dữ liệu tiêu thụ từng hộ; chính xác trong phân tích & ước tính; tối ưu chi phí tính toán khi chạy định kỳ cho nhiều hộ. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph (analyze_usage → detect_anomaly → recommend)
• Tool phân tích chuỗi thời gian (pandas)
• DB: PostgreSQL/TimescaleDB
• Backend: FastAPI
• Frontend: Next.js + Recharts
• Auth: Supabase (Cư dân, BQL)
• Scheduler định kỳ
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent phân tích tiêu thụ, biểu đồ xu hướng, đưa gợi ý tiết kiệm cá nhân hóa với ước tính tiền.

Nâng cao:
• Agent phát hiện bất thường (rò rỉ, thiết bị lỗi) và cảnh báo HITL, so sánh benchmark ẩn danh với căn tương tự, dự báo hóa đơn, đặt mục tiêu tiết kiệm & theo dõi, eval độ chính xác dự báo
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-11] ParkSmart AI – Agent Quản lý & Điều phối Gửi xe Thông minh

### 📝 Mô tả đề tài
📍 Thực trạng: Hầm gửi xe doanh nghiệp bất động sản giờ cao điểm thường quá tải, cư dân khó tìm chỗ, khách vãng lai không rõ chỗ trống, đăng ký thẻ xe/đổi xe rườm rà. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hỗ trợ cư dân đăng ký/quản lý thẻ xe, tra cứu & đặt chỗ ưu tiên, hướng dẫn tầng/khu còn trống theo thời gian thực và xử lý đăng ký xe cho khách; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho đăng ký thêm xe vượt định mức căn hộ cần BQL duyệt; bảo mật biển số & dữ liệu ra vào; chính xác về tình trạng chỗ trống; hiệu năng thời gian thực và chống gian lận đăng ký. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph (register → check_slot → guide → alert)
• Tool quản lý slot bãi xe
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js + sơ đồ bãi xe
• Auth: Supabase (Cư dân, Bảo vệ bãi xe, BQL)
• Realtime
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent đăng ký/quản lý thẻ xe, tra cứu chỗ trống, đăng ký xe khách, thông báo trạng thái.

Nâng cao:
• Agent dự báo cao điểm & gợi ý khu đỗ tối ưu, phát hiện xe lạ/vượt định mức cảnh báo, HITL BQL duyệt vượt định mức, dashboard sử dụng bãi & eval độ chính xác dự báo tải
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-12] CommunityVoice AI – Agent Khảo sát & Phân tích Mức độ Hài lòng Cư dân

### 📝 Mô tả đề tài
📍 Thực trạng: BQL doanh nghiệp bất động sản thỉnh thoảng phát khảo sát giấy/Google Form nhưng tỉ lệ trả lời thấp, câu hỏi cứng nhắc và phân tích thủ công không ra insight kịp thời. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tạo & dẫn dắt khảo sát dạng hội thoại thích ứng (hỏi sâu theo câu trả lời), phân tích cảm xúc/chủ đề phản hồi mở, và tổng hợp báo cáo mức hài lòng theo dịch vụ/tòa; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho BQL duyệt bộ câu hỏi & báo cáo trước khi công bố; bảo mật & ẩn danh phản hồi cư dân; chính xác trong phân tích cảm xúc tiếng Việt; tối ưu chi phí khi khảo sát diện rộng. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini (phân tích sentiment/topic tiếng Việt)
• Agent: LangGraph (adaptive-survey + analyzer + reporter)
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js + Recharts
• Auth: Supabase (Cư dân, BQL)
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent dẫn khảo sát hội thoại thích ứng, thu thập & phân tích cảm xúc/chủ đề, dashboard hài lòng cơ bản.

Nâng cao:
• Multi-agent (survey-designer + analyst + reporter), phát hiện chủ đề nổi cộm & cảnh báo NPS giảm, gợi ý hành động cho BQL, HITL duyệt khảo sát/báo cáo, eval độ chính xác phân loại cảm xúc
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-13] SOS Resident AI – Agent Hỗ trợ Khẩn cấp & Điều phối An ninh

### 📝 Mô tả đề tài
📍 Thực trạng: Khi có sự cố khẩn (cháy, y tế, an ninh) trong doanh nghiệp bất động sản, cư dân lúng túng không biết gọi ai, mô tả vị trí kém, khiến phản ứng chậm. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tiếp nhận báo khẩn, xác định loại & mức độ, hướng dẫn cư dân xử lý tức thời theo kịch bản, đồng thời điều phối cảnh báo tới bảo an/y tế/PCCC và cư dân lân cận đúng lúc; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL bắt buộc điều phối viên an ninh xác nhận & giám sát mọi cảnh báo diện rộng; bảo mật vị trí & tình trạng cư dân; độ chính xác & độ tin cậy cực cao (an toàn tính mạng); phản hồi thời gian thực, có phương án dự phòng khi LLM lỗi. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o (ưu tiên độ tin cậy) + fallback quy tắc cứng
• Agent: LangGraph (triage → guide → dispatch → notify) có guardrails
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js (nút SOS, màn điều phối)
• Auth: Supabase (Cư dân, An ninh, Y tế/BQL)
• Realtime + push
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• nút SOS, agent phân loại khẩn cấp & hướng dẫn theo kịch bản, tạo cảnh báo tới điều phối an ninh với vị trí.

Nâng cao:
• Multi-agent điều phối đa bên, cảnh báo cư dân lân cận theo bán kính, cơ chế fallback/guardrail khi LLM không chắc, HITL giám sát bắt buộc, eval thời gian phản hồi & độ chính xác phân loại khẩn cấp
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-14] EventHub AI – Agent Tổ chức & Điều phối Sự kiện Cộng đồng

### 📝 Mô tả đề tài
📍 Thực trạng: Sự kiện cộng đồng doanh nghiệp bất động sản (Trung thu, chợ phiên, giải thể thao) tổ chức thủ công: đăng ký rời rạc, khó chốt số lượng, phân bổ nguồn lực & thông báo lộn xộn. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hỗ trợ BQL/cư dân đề xuất & lập kế hoạch sự kiện, mở đăng ký thông minh, quản lý danh sách, phân bổ khu vực/tài nguyên và gửi nhắc cá nhân hóa; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho BQL duyệt kế hoạch & ngân sách sự kiện; bảo mật danh sách người tham gia; chính xác trong quản lý số lượng/tài nguyên; tối ưu chi phí thông báo và tránh spam cư dân. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph (plan → register → allocate → remind)
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js
• Auth: Supabase (Cư dân, Ban tổ chức/BQL)
• Scheduler nhắc
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent hỗ trợ lập kế hoạch sự kiện, mở đăng ký, quản lý danh sách & gửi nhắc, ghi nhớ sở thích cư dân.

Nâng cao:
• Agent gợi ý ý tưởng & phân bổ tài nguyên tối ưu, đề xuất sự kiện cá nhân hóa theo lịch sử tham gia, HITL BQL duyệt kế hoạch/ngân sách, dashboard tham gia & eval tỉ lệ chốt đăng ký
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-15] NotifyMe AI – Agent Thông báo Cộng đồng Cá nhân hóa & Chống Nhiễu

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân doanh nghiệp bất động sản bị ngập thông báo chung (cắt nước, bảo trì, sự kiện, quảng cáo) không liên quan tới mình, dẫn tới bỏ lỡ thông báo quan trọng. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent lọc, tóm tắt và cá nhân hóa thông báo theo tòa/căn hộ/sở thích cư dân, xác định mức khẩn, chọn kênh & thời điểm gửi phù hợp, tránh làm phiền; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho thông báo quan trọng/diện rộng phải BQL duyệt trước khi phát; bảo mật hồ sơ sở thích cư dân; chính xác trong phân loại mức khẩn & đối tượng nhận; tối ưu chi phí và tần suất gửi. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph (classify → target → summarize → schedule_send)
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js (feed cư dân + soạn thảo BQL)
• Push/Email
• Auth: Supabase (Cư dân, BQL/Truyền thông)
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, 2 vai trò
• agent phân loại & cá nhân hóa thông báo theo đối tượng, tóm tắt, feed cư dân theo mức ưu tiên.

Nâng cao:
• Agent chọn kênh & thời điểm tối ưu, gộp/nén thông báo chống nhiễu, học sở thích theo tương tác, HITL BQL duyệt thông báo diện rộng, eval tỉ lệ mở/độ liên quan
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-16] MoveInMate AI – Agent Hỗ trợ Cư dân Mới Onboarding vào Khu

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân mới nhận nhà ở doanh nghiệp bất động sản phải tự mò hàng loạt thủ tục: đăng ký thẻ cư dân, thẻ xe, internet, nội quy, kích hoạt tiện ích, gây choáng ngợp và sót việc. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent dẫn dắt onboarding cá nhân hóa, lập checklist thủ tục theo tình huống từng hộ, hướng dẫn từng bước, tự tạo yêu cầu tới đúng bộ phận và theo dõi tiến độ hoàn tất; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho các thủ tục cần BQL xác nhận hồ sơ/giấy tờ; bảo mật giấy tờ & thông tin cá nhân cư dân mới; chính xác trong hướng dẫn thủ tục theo từng khu; tối ưu chi phí & trải nghiệm nhiều bước. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph (profile → build_checklist → guide → create_requests → track)
• RAG tài liệu thủ tục
• Vector DB: Chroma
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js
• Auth: Supabase (Cư dân mới, BQL)
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent tạo checklist onboarding cá nhân hóa, hướng dẫn từng bước có trích tài liệu, theo dõi tiến độ (memory).

Nâng cao:
• Agent tự tạo & định tuyến yêu cầu tới các bộ phận, nhắc việc còn thiếu, HITL BQL duyệt hồ sơ, dashboard tiến độ onboarding & eval tỉ lệ hoàn tất thủ tục
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-17] GreenBin AI – Agent Phân loại Rác & Điều phối Thu gom Tái chế

### 📝 Mô tả đề tài
📍 Thực trạng: Chương trình phân loại rác tại nguồn ở doanh nghiệp bất động sản gặp khó vì cư dân không biết phân loại đúng, và việc đăng ký thu gom đồ cồng kềnh/tái chế còn thủ công. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hướng dẫn phân loại rác qua ảnh/mô tả, giải đáp bỏ đâu-khi nào, nhận đăng ký thu gom đồ cồng kềnh/tái chế và điều phối lịch tới đội vệ sinh; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho đăng ký thu gom khối lượng lớn cần BQL/đội vệ sinh xác nhận; bảo mật thông tin & ảnh cư dân; chính xác trong phân loại (tránh hướng dẫn sai); tối ưu chi phí vision và lịch thu gom. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o (vision đọc ảnh rác) + GPT-4o-mini
• Agent: LangGraph (classify_waste → advise → schedule_pickup)
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js
• Auth: Supabase (Cư dân, Đội vệ sinh/BQL)
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent phân loại rác qua ảnh/mô tả & hướng dẫn, nhận đăng ký thu gom, tạo lịch cho đội vệ sinh.

Nâng cao:
• Agent tối ưu tuyến & gộp lịch thu gom, gamification tích điểm tái chế, HITL xác nhận thu gom lớn, dashboard tỉ lệ phân loại đúng & eval độ chính xác nhận diện rác
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-18] PetPal AI – Agent Quản lý Thú cưng & Dịch vụ Thú cưng trong Khu

### 📝 Mô tả đề tài
📍 Thực trạng: doanh nghiệp bất động sản có nhiều hộ nuôi thú cưng nhưng quản lý đăng ký, quy định khu vực cho phép, lịch tiêm phòng và các phàn nàn liên quan (tiếng ồn, vệ sinh) còn rời rạc. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hỗ trợ đăng ký hồ sơ thú cưng, giải đáp quy định/khu vực được phép, nhắc lịch tiêm phòng, kết nối dịch vụ (spa, dắt chó, khách sạn thú cưng) và tiếp nhận-hòa giải phản ánh liên quan; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho phản ánh vi phạm cần BQL xử lý; bảo mật hồ sơ thú cưng & chủ nuôi; chính xác trong tra cứu quy định từng khu; tối ưu chi phí và trải nghiệm. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph (register → advise(RAG) → remind → connect_service → handle_complaint)
• Vector DB: Chroma (quy định)
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js
• Auth: Supabase (Cư dân, BQL, NCC dịch vụ)
• Scheduler nhắc
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent đăng ký thú cưng, giải đáp quy định (RAG có trích dẫn), nhắc tiêm phòng, tiếp nhận phản ánh.

Nâng cao:
• Agent kết nối & đặt dịch vụ thú cưng, định tuyến phản ánh có HITL cho BQL, gợi ý cá nhân hóa theo hồ sơ, dashboard & eval độ chính xác tra cứu quy định
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-19] ShuttleBus AI – Agent Đặt chỗ & Điều phối Xe buýt Nội khu/dịch vụ gọi xe của doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân doanh nghiệp bất động sản dùng xe buýt nội khu/kết nối dịch vụ gọi xe của doanh nghiệp nhưng không rõ lịch, giờ xe tới, chỗ trống giờ cao điểm, phải chờ đợi và khó lập kế hoạch di chuyển. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tra cứu lịch tuyến, ước tính giờ xe tới, cho đặt chỗ/giữ chỗ giờ cao điểm, gợi ý tuyến & giờ đi tối ưu và thông báo thay đổi; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho điều chỉnh tuyến/tăng chuyến cần điều phối viên vận hành duyệt; bảo mật lịch di chuyển cư dân; chính xác về giờ & chỗ trống; hiệu năng thời gian thực và tối ưu chi phí gọi API bản đồ. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph (query_route → estimate_eta → reserve → notify)
• Tool bản đồ/ETA (mock hoặc Mapbox)
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js + bản đồ
• Auth: Supabase (Cư dân, Điều phối vận hành)
• Realtime
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent tra cứu lịch tuyến, ước tính ETA, đặt/giữ chỗ, thông báo thay đổi, ghi nhớ tuyến hay đi.

Nâng cao:
• Agent gợi ý tuyến/giờ tối ưu theo tải & lịch cá nhân, dự báo cao điểm gợi ý tăng chuyến (HITL điều phối duyệt), dashboard sử dụng tuyến & eval độ chính xác ETA
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---

## [VHR-20] ResiDeals AI – Agent Ưu đãi Nội khu & Gợi ý Tiện ích Thương mại Cá nhân hóa

### 📝 Mô tả đề tài
📍 Thực trạng: Khu thương mại doanh nghiệp bất động sản (nhà hàng, spa, siêu thị, phòng khám) có nhiều ưu đãi cho cư dân nhưng thông tin phân tán, cư dân không biết ưu đãi nào phù hợp và cửa hàng khó tiếp cận đúng khách. Trong vận hành khu đô thị quy mô lớn với hàng chục nghìn hộ dân, các yêu cầu dịch vụ, phản ánh sự cố (kèm ảnh/video) và tranh chấp phí thường dồn dập vào giờ cao điểm với nhiều ngoại lệ và giới hạn tài nguyên.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hiểu sở thích & lịch sử cư dân, gợi ý ưu đãi/tiện ích thương mại phù hợp, đặt bàn/đặt lịch/nhận voucher qua hội thoại và thu thập phản hồi; đồng thời kết hợp khả năng hiểu ngữ cảnh đa phương thức (văn bản, hình ảnh, hóa đơn) của Agent với thuật toán phân bổ tài nguyên công bằng và kiểm chứng quy định/biểu phí xác định, tạo ra quy trình xử lý khép kín từ cư dân tới Ban Quản lý.

🔒 Ràng buộc: HITL cho cửa hàng duyệt & kích hoạt ưu đãi trước khi phát tới cư dân; bảo mật hồ sơ sở thích & hành vi cư dân; chính xác trong khớp ưu đãi & tồn kho voucher; tối ưu chi phí gợi ý và tránh spam. Cách ly tuyệt đối dữ liệu riêng tư giữa các hộ cư dân (tenant isolation); mọi phép tính phí dịch vụ/điện nước bậc thang và kiểm tra hạn mức đặt tiện ích phải thực hiện bằng code xác định.

### 🛠️ Tech Stack
• LLM: GPT-4o-mini
• Agent: LangGraph (profile → recommend → book/issue_voucher → collect_feedback)
• Vector DB: Qdrant (khớp ưu đãi)
• DB: PostgreSQL
• Backend: FastAPI
• Frontend: Next.js
• Auth: Supabase (Cư dân, Cửa hàng, BQL)
• Deploy: Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu yêu cầu dịch vụ đô thị NYC 311 Service Requests, dữ liệu tiêu thụ năng lượng tòa nhà Building Data Genome Project 2 / UK-DALE, chuẩn giao thông GTFS và dữ liệu vận hành khu đô thị mô phỏng.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App deploy, đăng nhập
• agent gợi ý ưu đãi cá nhân hóa, đặt bàn/lịch & phát voucher qua hội thoại, thu phản hồi (memory sở thích).

Nâng cao:
• Multi-agent (recommender + inventory + feedback-analyzer), định giá/ưu đãi động theo hành vi, HITL cửa hàng duyệt ưu đãi, dashboard hiệu quả chiến dịch & eval độ liên quan của gợi ý (CTR/hài lòng)
• Tích hợp cơ chế tối ưu hóa phân bổ nguồn lực/kiểm chứng hóa đơn xác định bằng code và mở rộng trải nghiệm xử lý tác vụ khép kín (end-to-end) giúp giảm tải thực chất cho Ban Quản lý khu đô thị.

---
