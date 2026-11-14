# Lĩnh vực: VFO2O - Ô tô & Xe điện – Kinh doanh O2O

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `VFO2O-01` | [AI Agent Tư vấn chọn xe doanh nghiệp ô tô theo nhu cầu & ngân sách](#vfo2o-01) |
| `VFO2O-02` | [AI Agent Quản lý & chấm điểm lead mua xe (Lead Scoring)](#vfo2o-02) |
| `VFO2O-03` | [AI Agent Đặt lịch lái thử & booking showroom](#vfo2o-03) |
| `VFO2O-04` | [AI Agent Cấu hình xe & báo giá/khuyến mãi tự động](#vfo2o-04) |
| `VFO2O-05` | [AI Agent Hỗ trợ hồ sơ trả góp, đăng ký & biển số](#vfo2o-05) |
| `VFO2O-06` | [AI Agent Chăm sóc sau bán & lịch bảo dưỡng xe điện](#vfo2o-06) |
| `VFO2O-07` | [AI Agent So sánh & xử lý phản đối (Objection Handling) khi tư vấn doanh nghiệp ô tô](#vfo2o-07) |
| `VFO2O-08` | [AI Agent Quản lý đại lý & phân phối doanh nghiệp ô tô](#vfo2o-08) |
| `VFO2O-09` | [AI Agent Phân tích phễu chuyển đổi Online→Offline](#vfo2o-09) |
| `VFO2O-10` | [AI Agent Sinh nội dung marketing & lập chiến dịch xe điện](#vfo2o-10) |
| `VFO2O-11` | [AI Agent Trợ lý trạm sạc & chi phí sử dụng xe điện](#vfo2o-11) |
| `VFO2O-12` | [AI Agent Quản lý đơn đặt cọc & bàn giao xe](#vfo2o-12) |
| `VFO2O-13` | [AI Agent Chăm sóc cộng đồng chủ xe của doanh nghiệp](#vfo2o-13) |
| `VFO2O-14` | [AI Agent Dự báo nhu cầu & tồn kho theo mẫu xe](#vfo2o-14) |
| `VFO2O-15` | [AI Agent Hỗ trợ chương trình đổi xe cũ (Trade-in)](#vfo2o-15) |
| `VFO2O-16` | [AI Agent Bán phụ kiện & gói dịch vụ theo xe (Upsell/Cross-sell)](#vfo2o-16) |
| `VFO2O-17` | [AI Agent Tư vấn & bán xe máy điện của doanh nghiệp cho khách phổ thông](#vfo2o-17) |
| `VFO2O-18` | [AI Agent Tổng đài đa kênh định tuyến & xử lý yêu cầu khách hàng của doanh nghiệp](#vfo2o-18) |
| `VFO2O-19` | [AI Agent Lập kế hoạch chuyến đi & sạc pin cho chủ xe của doanh nghiệp](#vfo2o-19) |
| `VFO2O-20` | [AI Agent Huấn luyện & hỗ trợ tư vấn viên bán xe (Sales Enablement)](#vfo2o-20) |

---

## [VFO2O-01] AI Agent Tư vấn chọn xe doanh nghiệp ô tô theo nhu cầu & ngân sách

### 📝 Mô tả đề tài
📍 Thực trạng: Khách quan tâm doanh nghiệp ô tô (VF3, VF5, VF6, VF7, VF8, VF9, xe máy điện) truy cập website/fanpage nhưng bối rối giữa nhiều mẫu, phiên bản, gói pin (thuê/mua) và không tự đối chiếu được với nhu cầu sử dụng, ngân sách, thói quen di chuyển. Tư vấn viên showroom quá tải và trả lời không đồng nhất.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hội thoại chủ động khai thác nhu cầu (số người, quãng đường/ngày, có chỗ sạc tại nhà không, ngân sách, mục đích gia đình/kinh doanh), lập kế hoạch hỏi–đáp nhiều bước, truy xuất catalog sản phẩm chính xác và đề xuất 1-3 mẫu phù hợp kèm lý do, ước tính tổng chi phí sở hữu, rồi chuyển tiếp đặt lịch lái thử (online→offline); đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Thông số kỹ thuật, giá niêm yết và chính sách pin phải lấy từ nguồn catalog được kiểm soát (không bịa số liệu); có bước human-in-the-loop cho tư vấn viên duyệt/hiệu chỉnh đề xuất trước khi gửi báo giá; bảo mật thông tin liên hệ & tài chính của khách; cảnh báo rõ mọi con số là ước tính; kiểm soát chi phí gọi LLM.

### 🛠️ Tech Stack
• LLM (GPT-4o/Claude qua API) điều phối bằng LangGraph (state machine hỏi nhu cầu → truy xuất → đề xuất → chốt lịch)
• RAG trên catalog sản phẩm xe của doanh nghiệp (thông số, giá, khuyến mãi, chính sách pin) với vector DB Qdrant/pgvector + reranking
• tool tính toán TCO (giá xe, phí lăn bánh, chi phí sạc/pin, bảo dưỡng)
• backend FastAPI, frontend Next.js/React + Tailwind
• auth 2 vai trò (khách & tư vấn viên)
• deploy Vercel + Render/Railway, DB Postgres.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy online có đăng nhập 2 vai trò (khách/tư vấn viên)
• agent hội thoại khai thác nhu cầu và đề xuất mẫu xe kèm lý do dựa trên catalog thật
• bảng ước tính TCO
• lưu hồ sơ khách
• HITL cho tư vấn viên duyệt đề xuất
• xử lý câu hỏi ngoài phạm vi.

Nâng cao:
• So sánh song song 2-3 mẫu theo tiêu chí cá nhân hóa
• memory nhớ hội thoại cũ của khách quay lại
• eval độ chính xác thông số bằng LLM-as-Judge trên ≥50 câu hỏi
• nút chuyển thẳng sang đặt lịch lái thử
• dashboard tỷ lệ hội thoại → lead
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-02] AI Agent Quản lý & chấm điểm lead mua xe (Lead Scoring)

### 📝 Mô tả đề tài
📍 Thực trạng: Lead mua xe của doanh nghiệp đổ về từ nhiều kênh (website, form, fanpage, hotline, sự kiện) với chất lượng rất khác nhau; đội sales xử lý theo cảm tính, lead nóng bị bỏ lỡ còn lead rác ngốn thời gian. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tự động gom lead đa kênh, làm giàu & phân loại, chấm điểm khả năng chuyển đổi (hot/warm/cold) dựa trên hành vi và thông tin khai báo, đề xuất hành động tiếp theo (gọi ngay, nuôi dưỡng, đặt lịch lái thử) và phân bổ cho tư vấn viên phù hợp; agent tự lên lịch nhắc và soạn nội dung liên hệ; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Con người duyệt việc phân bổ và nội dung trước khi gửi (HITL); giải thích được lý do điểm số (không hộp đen); bảo mật dữ liệu cá nhân khách hàng theo nguyên tắc tối thiểu hóa; tránh phân biệt đối xử; kiểm soát chi phí xử lý hàng loạt. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối pipeline ingest → enrich → score → route
• LLM cho phân loại & sinh giải thích/nội dung
• mô hình chấm điểm kết hợp rule + LLM reasoning
• vector DB lưu ngữ cảnh lead
• backend FastAPI + Postgres, hàng đợi Celery/Redis cho xử lý nền
• frontend React (kanban lead + bảng điểm)
• tích hợp webhook form/Zalo OA giả lập
• deploy Railway/Render + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Hệ thống deploy có 2 vai trò (quản lý sales/tư vấn viên)
• màn kanban lead với điểm số + nhãn nóng/ấm/lạnh + lý do
• agent gợi ý hành động tiếp theo và soạn tin nhắn nháp
• HITL duyệt phân bổ/nội dung
• xử lý lead trùng/lỗi.

Nâng cao:
• Tự động nuôi dưỡng lead theo chuỗi thời gian
• cảnh báo lead nóng sắp nguội
• eval độ chính xác chấm điểm so với nhãn thực tế + baseline rule
• dashboard phễu và tỷ lệ chuyển đổi theo tư vấn viên
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-03] AI Agent Đặt lịch lái thử & booking showroom

### 📝 Mô tả đề tài
📍 Thực trạng: Đặt lịch lái thử xe của doanh nghiệp hiện qua hotline/inbox thủ công, dễ trùng lịch, thiếu xe/tư vấn viên tại khung giờ, khách phải chờ xác nhận lâu và tỷ lệ no-show cao. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hội thoại giúp khách chọn showroom gần nhất, mẫu xe muốn lái thử, khung giờ trống; agent kiểm tra tồn xe demo và lịch tư vấn viên theo thời gian thực, giữ chỗ, gửi xác nhận & nhắc lịch, cho phép đổi/hủy, và tối ưu phân bổ nguồn lực showroom; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Không double-booking (kiểm soát trạng thái chắc chắn); HITL cho quản lý showroom duyệt các khung đặc biệt/VIP; bảo mật thông tin khách & giấy phép lái xe; thông tin lịch/xe demo phải chính xác; kiểm soát chi phí nhắc lịch tự động. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph quản lý luồng đặt lịch (chọn xe → chọn showroom → chọn giờ → giữ chỗ → xác nhận)
• LLM hiểu ngôn ngữ tự nhiên + trích xuất slot
• tool lịch (calendar service) & kiểm tra tồn xe demo qua API nội bộ giả lập
• RAG địa chỉ/thông tin showroom
• backend FastAPI + Postgres (khóa giao dịch chống trùng), Redis
• frontend Next.js có bản đồ showroom
• thông báo email/Zalo giả lập
• deploy Vercel + Railway.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web đặt lịch deploy, 2 vai trò (khách/quản lý showroom)
• agent hội thoại chốt được lịch lái thử không trùng
• xác nhận + nhắc lịch
• đổi/hủy lịch
• xử lý hết chỗ/lỗi.

Nâng cao:
• Tối ưu gợi ý khung giờ theo tải showroom
• cơ chế giảm no-show (nhắc nhiều bước, xác nhận lại)
• dashboard tỷ lệ đặt→đến→chuyển đổi
• eval độ chính xác trích xuất thời gian/mẫu xe ≥50 ca
• đồng bộ với agent lead
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-04] AI Agent Cấu hình xe & báo giá/khuyến mãi tự động

### 📝 Mô tả đề tài
📍 Thực trạng: Khách muốn tự cấu hình xe của doanh nghiệp (phiên bản, màu, gói pin thuê/mua, phụ kiện) và biết giá cuối cùng gồm khuyến mãi, nhưng bảng giá + chương trình ưu đãi thay đổi liên tục, tư vấn viên báo giá thủ công dễ sai và không nhất quán.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hướng dẫn khách cấu hình xe theo bước, áp dụng đúng quy tắc giá & khuyến mãi hiện hành (theo mẫu, thời điểm, đối tượng), tính giá lăn bánh theo tỉnh, sinh bảng báo giá chi tiết, và cảnh báo khi lựa chọn xung đột; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Giá & khuyến mãi phải khớp tuyệt đối nguồn dữ liệu được kiểm soát; mọi báo giá chính thức cần tư vấn viên duyệt (HITL); ghi log phiên bản bảng giá dùng để tính; bảo mật thông tin khách; cảnh báo giá chỉ mang tính tham khảo; kiểm soát chi phí. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối luồng cấu hình + quy tắc giá
• LLM cho hội thoại & giải thích
• rule engine áp khuyến mãi
• RAG bảng giá/chương trình ưu đãi + phí trước bạ theo tỉnh trên vector DB
• tool tính toán deterministic (không để LLM tự cộng tiền)
• backend FastAPI + Postgres, frontend React (car configurator trực quan)
• xuất PDF báo giá
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Configurator deploy, 2 vai trò (khách/tư vấn viên)
• cấu hình xe từng bước + tính giá cuối gồm khuyến mãi & phí lăn bánh theo tỉnh
• xuất báo giá PDF
• HITL duyệt báo giá
• xử lý cấu hình không hợp lệ.

Nâng cao:
• Cảnh báo/khuyến nghị gói tối ưu theo ngân sách
• so sánh giá mua pin vs thuê pin theo thời gian dùng
• lịch sử báo giá của khách
• eval độ chính xác giá 100% trên bộ test giá
• dashboard chương trình khuyến mãi hiệu quả nhất
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-05] AI Agent Hỗ trợ hồ sơ trả góp, đăng ký & biển số

### 📝 Mô tả đề tài
📍 Thực trạng: Sau khi chốt mua xe của doanh nghiệp, khách phải chuẩn bị hồ sơ trả góp ngân hàng, đăng ký xe, đăng kiểm, biển số — quy trình nhiều giấy tờ, dễ thiếu/sai, kéo dài thời gian bàn giao và gây bức xúc. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hướng dẫn khách theo tình huống (trả thẳng/trả góp, cá nhân/doanh nghiệp, theo tỉnh), lập checklist hồ sơ cá nhân hóa, kiểm tra giấy tờ khách upload (đủ/thiếu/mờ), ước tính khoản vay & lịch trả góp theo lãi suất các gói, và theo dõi tiến độ hồ sơ đến khi ra biển số; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Không tự nộp/duyệt hồ sơ — chỉ hỗ trợ, quyết định cuối do nhân viên & ngân hàng (HITL); bảo mật nghiêm ngặt giấy tờ tùy thân/tài chính; thông tin thủ tục & lãi suất phải chính xác theo nguồn; cảnh báo con số vay là ước tính; kiểm soát chi phí OCR/LLM. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối theo nhánh tình huống
• LLM + OCR (Tesseract/vision model) kiểm tra giấy tờ
• tool tính lịch trả góp (amortization) deterministic
• RAG quy định thủ tục đăng ký/biển số theo tỉnh + gói vay ngân hàng đối tác
• backend FastAPI + Postgres, lưu file mã hóa (S3-compatible)
• frontend React (wizard hồ sơ + tracker)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (khách/nhân viên hồ sơ)
• checklist hồ sơ cá nhân hóa
• upload & kiểm tra giấy tờ (thiếu/mờ)
• bảng ước tính trả góp
• tracker tiến độ
• HITL nhân viên duyệt
• xử lý giấy tờ lỗi.

Nâng cao:
• So sánh nhiều gói vay & tối ưu theo khả năng chi trả
• nhắc bổ sung giấy tờ tự động
• eval độ chính xác OCR/phân loại giấy tờ ≥10 loại
• dashboard thời gian trung bình hoàn tất hồ sơ
• cảnh báo rủi ro hồ sơ khó duyệt
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-06] AI Agent Chăm sóc sau bán & lịch bảo dưỡng xe điện

### 📝 Mô tả đề tài
📍 Thực trạng: Chủ xe doanh nghiệp ô tô cần bảo dưỡng định kỳ theo km/thời gian, nhưng dễ quên lịch, không rõ hạng mục/chi phí, và việc đặt lịch xưởng dịch vụ còn thủ công; chăm sóc sau bán rời rạc làm giảm giữ chân khách. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent theo dõi tình trạng từng xe (mốc km, lịch sử dịch vụ), chủ động nhắc bảo dưỡng đúng thời điểm, tư vấn hạng mục & ước tính chi phí, đặt lịch xưởng gần nhất, và trả lời thắc mắc vận hành/bảo hành; gợi ý gói dịch vụ phù hợp; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Thông tin bảo hành/khuyến nghị kỹ thuật phải theo nguồn chính hãng (không tự chế); HITL cho kỹ thuật viên duyệt báo giá dịch vụ; bảo mật dữ liệu xe & chủ xe; cảnh báo ước tính chi phí; kiểm soát chi phí nhắc tự động. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối theo dõi & nhắc lịch (event-driven)
• LLM hội thoại chăm sóc
• RAG cẩm nang bảo dưỡng/bảo hành + bảng giá dịch vụ trên vector DB
• tool lịch xưởng + tính chi phí
• scheduler (cron/Celery beat) cho nhắc lịch
• backend FastAPI + Postgres
• frontend React (hồ sơ xe + lịch)
• thông báo Zalo/email giả lập
• deploy Vercel + Railway.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (chủ xe/kỹ thuật viên)
• hồ sơ xe + lịch sử dịch vụ
• nhắc bảo dưỡng theo mốc
• tư vấn hạng mục + ước tính chi phí
• đặt lịch xưởng
• HITL duyệt báo giá
• xử lý lỗi.

Nâng cao:
• Cá nhân hóa nhắc theo thói quen chạy xe
• gợi ý gói bảo dưỡng trọn gói tối ưu
• eval độ đúng khuyến nghị hạng mục theo mốc km
• dashboard tỷ lệ quay lại bảo dưỡng & NPS
• phát hiện xe quá hạn
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-07] AI Agent So sánh & xử lý phản đối (Objection Handling) khi tư vấn doanh nghiệp ô tô

### 📝 Mô tả đề tài
📍 Thực trạng: Khách thường so sánh doanh nghiệp ô tô với xe xăng/xe điện đối thủ và nêu nhiều phản đối (lo ngại pin, trạm sạc, giá trị bán lại, thương hiệu). Tư vấn viên trả lời không đồng đều, thiếu dẫn chứng, dễ mất khách ở bước cuối. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent nhận diện loại phản đối, truy xuất luận điểm & dữ liệu đối chứng khách quan (ưu điểm chi phí sử dụng, chính sách pin, bảo hành, mạng lưới sạc), sinh phản hồi thuyết phục nhưng trung thực theo ngữ cảnh khách, và hỗ trợ tư vấn viên realtime; đồng thời huấn luyện tư vấn viên qua tình huống mô phỏng; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Chỉ dùng dữ liệu so sánh có nguồn kiểm chứng, tránh nói xấu/sai lệch đối thủ (tuân thủ & đạo đức); HITL tư vấn viên chọn/hiệu chỉnh phản hồi trước khi dùng với khách; bảo mật hội thoại; cảnh báo khi thiếu dữ liệu; kiểm soát chi phí. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph phân loại objection → truy xuất luận điểm → sinh phản hồi
• LLM + RAG kho luận điểm/so sánh sản phẩm (có trích nguồn) trên vector DB
• guardrail chống nội dung sai lệch/nói xấu
• backend FastAPI + Postgres
• frontend React (co-pilot cho tư vấn viên + chế độ luyện tập role-play)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (tư vấn viên/quản lý đào tạo)
• nhận diện & phân loại phản đối
• gợi ý phản hồi kèm dẫn chứng có nguồn
• HITL chỉnh sửa
• guardrail chặn nội dung sai
• xử lý câu hỏi thiếu dữ liệu.

Nâng cao:
• Chế độ mô phỏng khách khó tính để luyện tập + chấm điểm
• thư viện objection cập nhật
• eval chất lượng phản hồi bằng rubric/LLM-as-Judge ≥30 tình huống
• dashboard objection phổ biến & tỷ lệ vượt qua
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-08] AI Agent Quản lý đại lý & phân phối doanh nghiệp ô tô

### 📝 Mô tả đề tài
📍 Thực trạng: Hệ thống đại lý/showroom của doanh nghiệp phân bố nhiều tỉnh, dữ liệu doanh số, tồn kho, chỉ tiêu, nhân sự phân tán; quản lý vùng khó nắm bức tranh tổng thể và can thiệp kịp thời khi đại lý dưới chỉ tiêu. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tổng hợp dữ liệu đa đại lý, theo dõi KPI theo thời gian thực, phát hiện bất thường (tụt doanh số, tồn kho lệch, lead ứ đọng), giải thích nguyên nhân bằng ngôn ngữ tự nhiên, và đề xuất hành động (điều chuyển xe, đẩy khuyến mãi, hỗ trợ nhân sự); trả lời truy vấn quản lý bằng hội thoại; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Phân quyền dữ liệu theo vai trò/khu vực nghiêm ngặt (đại lý chỉ thấy dữ liệu của mình); HITL cho quản lý duyệt hành động điều phối; số liệu phải chính xác từ nguồn; cảnh báo giả định trong phân tích; kiểm soát chi phí truy vấn. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối phân tích + cảnh báo
• LLM cho text-to-insight & giải thích
• tool truy vấn dữ liệu (text-to-SQL có kiểm soát) trên Postgres
• RAG chính sách phân phối
• phát hiện bất thường (rule + thống kê)
• backend FastAPI
• frontend React (dashboard đa đại lý + chat hỏi dữ liệu)
• phân quyền RBAC
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, ≥2 vai trò (quản lý vùng/quản lý đại lý) với phân quyền dữ liệu
• dashboard KPI đa đại lý
• chat hỏi dữ liệu bằng ngôn ngữ tự nhiên
• cảnh báo bất thường + giải thích
• HITL duyệt đề xuất
• xử lý truy vấn sai.

Nâng cao:
• Đề xuất điều chuyển tồn kho giữa đại lý
• xếp hạng & benchmark đại lý
• eval độ đúng text-to-SQL ≥30 truy vấn
• dự báo khả năng đạt chỉ tiêu
• cảnh báo sớm đại lý rủi ro
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-09] AI Agent Phân tích phễu chuyển đổi Online→Offline

### 📝 Mô tả đề tài
📍 Thực trạng: Hành trình khách hàng của doanh nghiệp trải dài từ chạm online (web, ads, fanpage) đến hành động offline (lái thử, đến showroom, chốt cọc), nhưng dữ liệu đứt gãy giữa các kênh khiến không biết khách rơi rớt ở đâu và vì sao. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent ghép nối hành trình khách across kênh, dựng phễu O2O, định vị điểm rơi lớn nhất, phân tích nguyên nhân theo phân khúc/nguồn/mẫu xe, và đề xuất hành động cải thiện (nội dung, thời điểm liên hệ, ưu đãi); trả lời câu hỏi phân tích ad-hoc của marketing/sales; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Ẩn danh & tối thiểu hóa dữ liệu cá nhân trong phân tích (bảo mật); HITL cho marketing duyệt đề xuất trước khi triển khai; phân biệt tương quan vs nhân quả, cảnh báo giả định; số liệu chính xác từ nguồn; kiểm soát chi phí xử lý. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối phân tích nhiều bước
• LLM cho insight & đề xuất
• tool text-to-SQL/analytics trên Postgres + mô hình attribution đơn giản
• RAG định nghĩa chỉ số/kênh
• backend FastAPI
• frontend React (sơ đồ phễu tương tác + chat phân tích)
• deploy Vercel + Render
• dữ liệu hành trình giả lập nhiều kênh.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (marketing/sales)
• phễu O2O trực quan + tỷ lệ rớt từng bước
• chat hỏi phân tích
• agent chỉ ra điểm nghẽn + nguyên nhân giả định
• HITL duyệt đề xuất
• xử lý câu hỏi ngoài dữ liệu.

Nâng cao:
• Phân tích theo cohort/nguồn/mẫu xe
• mô phỏng tác động khi cải thiện một bước
• eval độ đúng phân tích trên bộ câu hỏi chuẩn
• cảnh báo tự động khi tỷ lệ chuyển đổi tụt
• gợi ý A/B test
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-10] AI Agent Sinh nội dung marketing & lập chiến dịch xe điện

### 📝 Mô tả đề tài
📍 Thực trạng: Đội marketing đại lý của doanh nghiệp phải liên tục sản xuất nội dung đa kênh (bài fanpage, tin nhắn, kịch bản quảng cáo, email) cho nhiều mẫu xe và chương trình, thủ công, chậm và thiếu nhất quán thương hiệu. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent lập kế hoạch chiến dịch theo mục tiêu (ra mắt mẫu, đẩy lái thử, khuyến mãi cuối tháng), sinh bộ nội dung đa kênh bám thông tin sản phẩm chính xác & tông giọng thương hiệu, cá nhân hóa theo phân khúc khách, và đề xuất lịch đăng; hỗ trợ chỉnh sửa lặp; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Thông số/giá/khuyến mãi trong nội dung phải khớp nguồn (không sai lệch quảng cáo); HITL bắt buộc duyệt trước khi xuất bản; guardrail tránh cam kết sai/so sánh vi phạm; bảo mật dữ liệu chiến dịch; kiểm soát chi phí sinh nội dung. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối brief → kế hoạch → sinh nội dung → duyệt
• LLM sáng tạo có ràng buộc brand voice
• RAG thông tin sản phẩm/khuyến mãi + brand guideline trên vector DB
• tool kiểm tra tính nhất quán số liệu
• backend FastAPI + Postgres
• frontend React (workspace chiến dịch + editor + lịch nội dung)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (marketer/quản lý duyệt)
• lập kế hoạch chiến dịch
• sinh bộ nội dung đa kênh bám sản phẩm thật + brand voice
• HITL duyệt/chỉnh
• guardrail chặn số liệu sai
• xử lý brief thiếu thông tin.

Nâng cao:
• Cá nhân hóa theo phân khúc
• gợi ý biến thể A/B
• lịch đăng tự động đề xuất
• eval độ nhất quán số liệu & chất lượng nội dung bằng rubric/LLM-as-Judge
• dashboard hiệu quả nội dung giả lập
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-11] AI Agent Trợ lý trạm sạc & chi phí sử dụng xe điện

### 📝 Mô tả đề tài
📍 Thực trạng: Rào cản lớn khi mua xe điện của doanh nghiệp là lo ngại về trạm sạc và chi phí vận hành so với xe xăng; khách thiếu công cụ trực quan để tự đánh giá theo tuyến đường & thói quen của mình. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tư vấn về mạng lưới trạm sạc (vị trí, loại sạc, quy hoạch tuyến đi dài), tính chi phí sử dụng thực tế (điện/thuê pin theo km, so sánh xăng), lập kế hoạch sạc cho chuyến đi, và giải đáp lo ngại vận hành; chuyển hóa lo ngại thành động lực mua; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Dữ liệu trạm sạc & giá điện/pin phải từ nguồn được kiểm soát, cảnh báo khi ngoài vùng phủ; HITL cho tư vấn viên khi liên hệ chốt khách; bảo mật lộ trình/vị trí khách; cảnh báo con số là ước tính; kiểm soát chi phí gọi bản đồ/LLM. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối tư vấn + lập kế hoạch tuyến
• LLM hội thoại
• tool bản đồ/định tuyến (Mapbox/OSM) + tính chi phí năng lượng deterministic
• RAG dữ liệu trạm sạc & biểu giá pin/điện trên vector DB
• backend FastAPI + Postgres
• frontend React (bản đồ trạm sạc + máy tính chi phí)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (khách/tư vấn viên)
• bản đồ trạm sạc + tra cứu
• máy tính chi phí sử dụng so với xăng theo km
• lập kế hoạch sạc cơ bản cho tuyến
• HITL chuyển tư vấn viên
• xử lý điểm ngoài vùng phủ.

Nâng cao:
• Lập lộ trình dài nhiều điểm sạc tối ưu
• cá nhân hóa theo mẫu xe & thói quen
• so sánh kịch bản mua pin vs thuê pin
• eval độ chính xác gợi ý trạm/chi phí ≥30 ca
• dashboard mối lo phổ biến & tỷ lệ giải tỏa
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-12] AI Agent Quản lý đơn đặt cọc & bàn giao xe

### 📝 Mô tả đề tài
📍 Thực trạng: Từ lúc khách đặt cọc doanh nghiệp ô tô đến khi nhận xe trải qua nhiều bước (xác nhận cọc, phân bổ xe, hoàn thiện hồ sơ, kiểm tra xe, hẹn bàn giao), thông tin phân tán khiến khách sốt ruột hỏi liên tục và nhân viên khó điều phối. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent quản lý vòng đời đơn cọc, cập nhật & giải thích trạng thái cho khách chủ động, điều phối các bước phụ thuộc (phân bổ VIN, hồ sơ, lịch bàn giao), cảnh báo tắc nghẽn/chậm trễ, và trả lời thắc mắc; hỗ trợ nhân viên xử lý ngoại lệ; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Cập nhật trạng thái phải chính xác, nhất quán với hệ thống (không hứa sai ngày); HITL cho nhân viên xác nhận các mốc quan trọng (phân bổ VIN, ngày giao); bảo mật thông tin đơn hàng & thanh toán; cảnh báo mốc thời gian là dự kiến; kiểm soát chi phí. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph mô hình hóa state machine đơn hàng (cọc → phân bổ → hồ sơ → kiểm tra → bàn giao)
• LLM giải thích trạng thái & hội thoại
• tool cập nhật/điều phối trên Postgres (transaction)
• RAG chính sách cọc/bàn giao
• scheduler cảnh báo trễ
• backend FastAPI
• frontend React (order tracker cho khách + bảng điều phối cho nhân viên)
• deploy Vercel + Railway.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (khách/nhân viên giao xe)
• tracker trạng thái đơn cọc theo thời gian thực + giải thích
• agent trả lời thắc mắc tiến độ
• HITL xác nhận mốc quan trọng
• cảnh báo chậm trễ
• xử lý ngoại lệ đơn.

Nâng cao:
• Dự báo ngày bàn giao & cập nhật khi thay đổi
• điều phối tự động thứ tự ưu tiên
• checklist bàn giao số hóa
• eval độ chính xác trạng thái/thông báo
• dashboard thời gian trung bình cọc→giao & điểm nghẽn
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-13] AI Agent Chăm sóc cộng đồng chủ xe của doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Cộng đồng chủ xe của doanh nghiệp rất lớn và sôi động trên nhiều nhóm, đặt vô số câu hỏi lặp về sử dụng, sạc, bảo hành, mẹo vặt; đội chăm sóc không xuể và chất lượng trả lời không đồng đều, ảnh hưởng trải nghiệm thương hiệu. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent làm trợ lý cộng đồng: trả lời câu hỏi thường gặp dựa trên kho tri thức chính hãng + kinh nghiệm đã kiểm duyệt, phát hiện chủ đề nóng/khủng hoảng, tổng hợp phản hồi/góp ý sản phẩm gửi về hãng, và gợi ý nội dung gắn kết cộng đồng; chuyển ca khó cho con người; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Chỉ trả lời khi đủ độ tin cậy, ngược lại chuyển người thật (HITL); thông tin kỹ thuật/bảo hành phải chính xác theo nguồn; guardrail tránh cam kết sai/nội dung nhạy cảm; bảo mật thông tin thành viên; kiểm soát chi phí trả lời hàng loạt. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối phân loại câu hỏi → truy xuất → trả lời/escalate
• LLM + RAG kho FAQ chính hãng & bài đã kiểm duyệt trên vector DB
• phân loại chủ đề & phát hiện khủng hoảng (sentiment)
• backend FastAPI + Postgres
• frontend React (bảng điều hành cộng đồng + widget hỏi đáp)
• tích hợp nguồn nhóm giả lập
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (thành viên/quản trị cộng đồng)
• trả lời FAQ dựa nguồn có trích dẫn
• tự chuyển ca khó cho người thật
• phát hiện chủ đề nóng
• HITL duyệt câu trả lời nhạy cảm
• xử lý câu hỏi ngoài kho.

Nâng cao:
• Tổng hợp góp ý sản phẩm định kỳ gửi hãng
• gợi ý nội dung/sự kiện gắn kết
• cảnh báo sớm khủng hoảng truyền thông
• eval độ chính xác & tỷ lệ escalate hợp lý trên ≥30 ca
• dashboard sức khỏe cộng đồng
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-14] AI Agent Dự báo nhu cầu & tồn kho theo mẫu xe

### 📝 Mô tả đề tài
📍 Thực trạng: Đại lý doanh nghiệp ô tô khó cân đối tồn kho theo mẫu/phiên bản/màu: mẫu hot thì thiếu hàng mất khách, mẫu chậm thì tồn đọng vốn; quyết định nhập/điều chuyển chủ yếu theo cảm tính. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích dữ liệu bán hàng, lead, mùa vụ, khuyến mãi để dự báo nhu cầu ngắn hạn theo mẫu xe từng khu vực, cảnh báo nguy cơ thiếu/thừa, đề xuất kế hoạch nhập & điều chuyển giữa đại lý, và giải thích cơ sở dự báo bằng ngôn ngữ tự nhiên; cho phép quản lý hỏi kịch bản what-if; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Dự báo phải minh bạch giả định & khoảng tin cậy, cảnh báo bất định (không tuyệt đối hóa); HITL cho quản lý duyệt kế hoạch nhập/điều chuyển; số liệu chính xác từ nguồn; bảo mật dữ liệu kinh doanh; kiểm soát chi phí tính toán. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối phân tích → dự báo → đề xuất
• mô hình dự báo (Prophet/thống kê/ML nhẹ) + tool tính toán
• LLM giải thích & hỏi what-if bằng ngôn ngữ tự nhiên
• RAG ghi chú thị trường/khuyến mãi
• backend FastAPI + Postgres
• frontend React (dashboard tồn kho & dự báo)
• deploy Vercel + Render
• dữ liệu bán hàng giả lập theo thời gian.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (quản lý chuỗi/quản lý đại lý)
• dự báo nhu cầu theo mẫu xe & khu vực + khoảng tin cậy
• cảnh báo thiếu/thừa tồn
• agent giải thích dự báo
• HITL duyệt kế hoạch
• xử lý dữ liệu thiếu.

Nâng cao:
• Đề xuất điều chuyển tối ưu giữa đại lý
• mô phỏng what-if (khuyến mãi, mùa vụ)
• eval sai số dự báo (MAPE) so với baseline naïve
• cảnh báo sớm lệch cung-cầu
• ưu tiên nhập theo lợi nhuận
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-15] AI Agent Hỗ trợ chương trình đổi xe cũ (Trade-in)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhiều khách muốn đổi xe cũ (xăng hoặc xe khác) lấy xe điện của doanh nghiệp nhưng quy trình định giá xe cũ chậm, thiếu minh bạch, mỗi nơi báo một giá khiến khách e ngại và giao dịch kéo dài. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hướng dẫn khách khai thông tin xe cũ (hãng, đời, km, tình trạng, ảnh), ước tính giá thu mua sơ bộ dựa trên dữ liệu thị trường, tính chênh lệch để lên đời xe doanh nghiệp ô tô (gồm trả góp phần còn lại), đặt lịch thẩm định thực tế, và theo dõi tiến trình trade-in; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Giá ước tính phải kèm cảnh báo rõ là tạm tính, giá chính thức do thẩm định viên quyết (HITL bắt buộc); dữ liệu định giá từ nguồn kiểm soát, tránh sai lệch; bảo mật thông tin xe & khách; minh bạch cơ sở định giá; kiểm soát chi phí xử lý ảnh/LLM. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối khai thông tin → định giá → quy đổi → đặt lịch thẩm định
• LLM hội thoại + vision model đánh giá ảnh tình trạng xe
• tool định giá (rule + dữ liệu thị trường) & tính chênh lệch/trả góp deterministic
• RAG bảng giá xe cũ & chính sách trade-in
• backend FastAPI + Postgres, lưu ảnh mã hóa
• frontend React (wizard trade-in + tracker)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (khách/thẩm định viên)
• khai thông tin + ảnh xe cũ
• ước tính giá thu mua + chênh lệch lên đời doanh nghiệp ô tô
• đặt lịch thẩm định
• HITL thẩm định viên chốt giá
• cảnh báo giá tạm tính
• xử lý thiếu thông tin.

Nâng cao:
• Đánh giá tình trạng qua ảnh
• đề xuất mẫu doanh nghiệp ô tô phù hợp ngân sách sau trade-in
• tracker tiến trình
• eval sai lệch giá ước tính vs giá thẩm định ≥20 ca
• dashboard tỷ lệ trade-in chuyển đổi
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-16] AI Agent Bán phụ kiện & gói dịch vụ theo xe (Upsell/Cross-sell)

### 📝 Mô tả đề tài
📍 Thực trạng: Sau khi mua xe của doanh nghiệp, khách có nhu cầu phụ kiện (thảm, camera, bọc ghế, sạc tại nhà) và gói dịch vụ (bảo hành mở rộng, chăm sóc xe), nhưng việc gợi ý còn thủ công, không đúng mẫu xe/nhu cầu, bỏ lỡ doanh thu và trải nghiệm.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tư vấn phụ kiện & gói dịch vụ tương thích đúng mẫu/phiên bản xe của khách, cá nhân hóa gợi ý theo nhu cầu & lịch sử, kiểm tra tồn kho & tương thích, tạo giỏ hàng và báo giá gói combo tối ưu, rồi chốt đơn/đặt lắp đặt; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Chỉ gợi ý phụ kiện tương thích thật với mẫu xe (không bán nhầm); giá & tồn kho chính xác từ nguồn; HITL cho nhân viên xác nhận đơn/lịch lắp; bảo mật thông tin khách; tránh chèo kéo quá mức (đạo đức); kiểm soát chi phí. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối tư vấn → kiểm tương thích → dựng combo → chốt
• LLM gợi ý cá nhân hóa
• RAG catalog phụ kiện/gói dịch vụ + ma trận tương thích theo mẫu xe trên vector DB
• tool kiểm tồn kho & tính giá combo
• recommender đơn giản
• backend FastAPI + Postgres
• frontend React (cửa hàng phụ kiện + giỏ hàng)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (khách/nhân viên bán phụ kiện)
• gợi ý phụ kiện/gói đúng mẫu xe + cá nhân hóa
• kiểm tra tương thích & tồn
• giỏ hàng + báo giá combo
• HITL xác nhận đơn/lịch lắp
• xử lý hết hàng/không tương thích.

Nâng cao:
• Đề xuất combo tối ưu theo ngân sách & nhu cầu
• nhắc phụ kiện theo mùa/sự kiện
• eval độ chính xác tương thích & chất lượng gợi ý ≥30 ca
• dashboard doanh thu upsell & tỷ lệ chốt
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-17] AI Agent Tư vấn & bán xe máy điện của doanh nghiệp cho khách phổ thông

### 📝 Mô tả đề tài
📍 Thực trạng: Phân khúc xe máy điện của doanh nghiệp (Evo, Feliz, Klara, Vento, Theon...) nhắm khách phổ thông, học sinh-sinh viên, shipper với hành vi mua nhanh, nhạy giá, quan tâm quãng đường/sạc/độ bền; nhu cầu tư vấn khác hẳn ô tô và showroom khó phục vụ số đông này hiệu quả.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tư vấn chọn xe máy điện theo nhu cầu (đi học/đi làm/chở hàng), ngân sách và quãng đường/ngày; giải thích pin/quãng đường thực tế, chi phí so với xe xăng; đề xuất mẫu + phiên bản, gợi ý trả góp nhẹ, và chốt đặt cọc/đến cửa hàng gần nhất; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Thông số quãng đường/giá phải chính xác & tránh phóng đại (đạo đức quảng cáo); HITL cho nhân viên với đơn trả góp; bảo mật thông tin khách (nhiều khách trẻ); cảnh báo ước tính; kiểm soát chi phí cho lưu lượng lớn. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối hội thoại nhanh gọn
• LLM (ưu tiên model chi phí thấp) + routing để tiết kiệm
• RAG catalog xe máy điện + chi phí/pin trên vector DB
• tool tính chi phí sử dụng & trả góp
• backend FastAPI + Postgres
• frontend React responsive tối ưu mobile + bản đồ cửa hàng
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web/app mobile-first deploy, 2 vai trò (khách/nhân viên cửa hàng)
• agent tư vấn nhanh chọn xe máy điện theo nhu cầu-ngân sách
• so sánh chi phí với xe xăng
• đề xuất mẫu + đặt cọc/tìm cửa hàng
• HITL cho trả góp
• xử lý câu hỏi ngoài phạm vi.

Nâng cao:
• Cá nhân hóa cho nhóm shipper (chở hàng, quãng đường lớn)
• so sánh nhiều mẫu
• model routing tối ưu chi phí + đo chi phí/hội thoại
• eval độ chính xác thông số ≥50 câu
• dashboard chuyển đổi theo phân khúc trẻ
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-18] AI Agent Tổng đài đa kênh định tuyến & xử lý yêu cầu khách hàng của doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Yêu cầu khách hàng của doanh nghiệp đổ về nhiều kênh (chat web, Zalo, hotline, email) với đủ loại ý định (mua xe, bảo dưỡng, khiếu nại, hỏi sạc), hiện phân loại & chuyển tiếp thủ công gây chậm, sai bộ phận và trải nghiệm rời rạc. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tổng đài hợp nhất: hiểu ý định & mức khẩn, tự giải quyết yêu cầu đơn giản (tra cứu, FAQ, đặt lịch), định tuyến chính xác yêu cầu phức tạp đến đúng agent chuyên biệt/bộ phận, giữ ngữ cảnh xuyên kênh, và theo dõi đến khi đóng ticket; điều phối như một orchestrator đa agent; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Yêu cầu nhạy cảm (khiếu nại, tài chính) bắt buộc chuyển người thật (HITL); phân loại sai phải phát hiện & sửa được; bảo mật hội thoại & danh tính khách xuyên kênh; thông tin trả lời chính xác từ nguồn; kiểm soát chi phí định tuyến LLM. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph làm orchestrator đa agent (intent router → sub-agent: bán hàng/dịch vụ/sạc/khiếu nại)
• LLM phân loại ý định & mức khẩn
• RAG kho tri thức từng lĩnh vực
• tool tạo/chuyển ticket + tra cứu
• backend FastAPI + Postgres, Redis cho session xuyên kênh
• frontend React (giao diện tổng đài + inbox hợp nhất)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, ≥2 vai trò (khách/nhân viên tổng đài)
• nhận diện ý định & định tuyến đúng bộ phận
• tự xử lý yêu cầu đơn giản
• giữ ngữ cảnh hội thoại
• HITL chuyển ca nhạy cảm
• theo dõi & đóng ticket
• xử lý phân loại sai.

Nâng cao:
• Phối hợp nhiều sub-agent chuyên biệt + trace chuỗi xử lý
• ưu tiên theo mức khẩn/khách VIP
• eval độ chính xác intent routing ≥50 ca + tỷ lệ tự giải quyết
• dashboard SLA, tồn ticket & CSAT
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-19] AI Agent Lập kế hoạch chuyến đi & sạc pin cho chủ xe của doanh nghiệp

### 📝 Mô tả đề tài
📍 Thực trạng: Chủ xe điện của doanh nghiệp lo lắng khi đi đường dài liên tỉnh: không chắc pin đủ, không biết bố trí điểm sạc/đổi pin dọc đường, dẫn tới 'range anxiety' và ngại dùng xe cho chuyến xa. Trong kinh doanh và dịch vụ hậu mãi ô tô/xe điện theo mô hình O2O, quyết định của khách hàng phụ thuộc chặt chẽ vào bài toán tài chính thực tế (giá lăn bánh, trả góp, chi phí sở hữu TCO), hạ tầng trạm sạc theo lộ trình di chuyển và lịch sử bảo dưỡng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent lập kế hoạch chuyến đi theo điểm đầu-cuối, mẫu xe & dung lượng pin, thói quen lái; tính tiêu hao theo tuyến/địa hình, chèn điểm sạc/đổi pin tối ưu (thời gian & chi phí), dự phòng rủi ro (trạm bận/hỏng), và điều chỉnh động khi lộ trình thay đổi; giải thích rõ kế hoạch; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Cảnh báo rõ ước tính tiêu hao phụ thuộc điều kiện thực tế (không đảm bảo tuyệt đối); dữ liệu trạm sạc chính xác, cảnh báo vùng thiếu trạm; HITL để người dùng xác nhận/điều chỉnh kế hoạch; bảo mật lộ trình & vị trí; kiểm soát chi phí gọi API bản đồ. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối lập kế hoạch nhiều bước + tái lập khi thay đổi
• LLM diễn giải & hỏi đáp
• tool định tuyến (Mapbox/OSRM) + mô hình tiêu hao năng lượng theo quãng đường/địa hình
• RAG mạng lưới trạm sạc/đổi pin & công suất
• backend FastAPI + Postgres
• frontend React (bản đồ lộ trình + timeline sạc)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (chủ xe/hỗ trợ viên)
• lập kế hoạch tuyến có điểm sạc/đổi pin phù hợp pin xe
• ước tính thời gian & chi phí
• timeline sạc rõ ràng
• HITL xác nhận kế hoạch
• cảnh báo vùng thiếu trạm
• xử lý tuyến bất khả thi.

Nâng cao:
• Tái lập kế hoạch động khi lệch lộ trình/trạm bận
• tối ưu đa mục tiêu (nhanh nhất vs rẻ nhất)
• cá nhân hóa theo thói quen lái
• eval độ hợp lý kế hoạch ≥20 tuyến
• cảnh báo rủi ro hết pin giữa chặng
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---

## [VFO2O-20] AI Agent Huấn luyện & hỗ trợ tư vấn viên bán xe (Sales Enablement)

### 📝 Mô tả đề tài
📍 Thực trạng: Tư vấn viên doanh nghiệp ô tô mới liên tục được tuyển, nhưng đào tạo kiến thức sản phẩm (nhiều mẫu, chính sách pin, khuyến mãi thay đổi) và kỹ năng bán hàng O2O tốn thời gian, không đồng đều, khiến chất lượng tư vấn dao động và hiệu suất bán thấp giai đoạn đầu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent vừa là trợ lý tra cứu tức thời (sản phẩm, giá, chính sách) khi tư vấn viên đang làm việc, vừa là huấn luyện viên: tạo tình huống khách mô phỏng để luyện tập, chấm điểm phần trình bày/xử lý phản đối theo rubric, chỉ ra điểm yếu và đề xuất lộ trình học cá nhân hóa; theo dõi tiến bộ; đồng thời kết hợp mô-đun tính toán xác định (TCO 5 năm, lịch trả góp, ước tính tiêu hao pin theo địa hình/thời tiết, khấu hao xe) với khả năng tư vấn, xử lý phản đối dựa trên bằng chứng và điều phối dịch vụ đa bước của AI Agent.

🔒 Ràng buộc: Nội dung sản phẩm/chính sách phải chính xác & cập nhật từ nguồn (không dạy sai); HITL cho quản lý đào tạo duyệt đánh giá & lộ trình; bảo mật dữ liệu nhân sự & hiệu suất; guardrail tránh mô phỏng phản cảm; kiểm soát chi phí luyện tập lặp. Toàn bộ phép tính giá lăn bánh, trả góp, so sánh TCO và ước lượng pin/trạm sạc phải thực hiện bằng công thức code xác định có kiểm chứng; không để LLM tự ước lượng số học.

### 🛠️ Tech Stack
• LangGraph điều phối 2 chế độ (trợ lý tra cứu & huấn luyện role-play + chấm điểm)
• LLM đóng vai khách + chấm theo rubric (LLM-as-Judge)
• RAG kho kiến thức sản phẩm/chính sách/kịch bản bán hàng trên vector DB
• backend FastAPI + Postgres
• frontend React (co-pilot tra cứu + phòng luyện tập + bảng tiến bộ)
• deploy Vercel + Render.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu trạm sạc & tiêu hao năng lượng xe điện ACN-Data / OpenChargeMap, bộ dữ liệu nhận diện hư hỏng & định giá xe CarDD / Used Car Valuation, định tuyến địa hình OSRM/OpenElevation và thông số kỹ thuật chuẩn WLTP.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, 2 vai trò (tư vấn viên/quản lý đào tạo)
• trợ lý tra cứu sản phẩm-chính sách chính xác có trích nguồn
• mô phỏng khách để luyện tập
• chấm điểm theo rubric + nhận xét
• HITL quản lý duyệt đánh giá
• xử lý câu hỏi ngoài kho.

Nâng cao:
• Lộ trình học cá nhân hóa theo điểm yếu
• tình huống khó tăng dần độ khó
• theo dõi tiến bộ theo thời gian
• eval độ tin cậy chấm điểm so với chuyên gia ≥20 ca
• dashboard năng lực đội ngũ & lỗ hổng kiến thức
• Kết hợp động cơ tính toán TCO/lộ trình năng lượng/định giá xác định với hệ thống tác tử tư vấn để cá nhân hóa phương án theo dữ liệu di chuyển và tài chính thực tế của từng khách hàng.

---
