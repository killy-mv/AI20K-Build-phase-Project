# Lĩnh vực: SC - Smart City – IoT / Smart Home / Đô thị thông minh

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `SC-01` | [AI Agent Trợ Lý Điều Khiển & Tự Động Hóa Smart Home Bằng Ngôn Ngữ Tự Nhiên](#sc-01) |
| `SC-02` | [AI Agent Tối Ưu Năng Lượng Hộ Gia Đình & Tòa Nhà doanh nghiệp bất động sản](#sc-02) |
| `SC-03` | [AI Agent Giám Sát & Cảnh Báo An Ninh Từ Camera AI Khu Đô Thị](#sc-03) |
| `SC-04` | [AI Agent Phát Hiện Bất Thường Cảm Biến IoT (Rò Rỉ Gas, Cháy, Ngập Nước)](#sc-04) |
| `SC-05` | [AI Agent Đỗ Xe Thông Minh & Dẫn Đường Trong Bãi](#sc-05) |
| `SC-06` | [AI Agent Quản Lý Chiếu Sáng Đô Thị Thích Ứng](#sc-06) |
| `SC-07` | [AI Agent Giám Sát Chất Lượng Không Khí & Môi Trường Đô Thị](#sc-07) |
| `SC-08` | [AI Agent Dự Báo & Điều Tiết Giao Thông Nội Khu Đô Thị](#sc-08) |
| `SC-09` | [AI Agent Bảo Trì Dự Đoán Thiết Bị IoT & Hạ Tầng Kỹ Thuật](#sc-09) |
| `SC-10` | [AI Agent Trợ Lý Cư Dân Điều Khiển Thiết Bị & Quản Lý Kịch Bản (Scene)](#sc-10) |
| `SC-11` | [AI Agent Quản Lý Thu Gom Rác Thải Thông Minh Khu Đô Thị](#sc-11) |
| `SC-12` | [AI Agent Giám Sát Tiêu Thụ Nước & Phát Hiện Thất Thoát](#sc-12) |
| `SC-13` | [AI Agent Điều Phối Thang Máy Thông Minh Tòa Nhà Cao Tầng](#sc-13) |
| `SC-14` | [AI Agent An Toàn Cháy Nổ & Điều Phối Sơ Tán Thông Minh](#sc-14) |
| `SC-15` | [AI Agent Digital Twin Vận Hành Khu Đô Thị Thông Minh](#sc-15) |
| `SC-16` | [AI Agent Quản Lý & Tối Ưu Trạm Sạc Xe Điện doanh nghiệp ô tô Trong Khu](#sc-16) |
| `SC-17` | [AI Agent Tối Ưu Điều Hòa & HVAC Tòa Nhà Theo Ngữ Cảnh](#sc-17) |
| `SC-18` | [AI Agent Cảnh Báo Thời Tiết Cực Đoan & Ứng Phó Thiên Tai Khu Đô Thị](#sc-18) |
| `SC-19` | [AI Agent Trợ Lý Vận Hành & Chăm Sóc Cư Dân Đa Kênh (Smart Building Concierge)](#sc-19) |
| `SC-20` | [AI Agent Giám Sát Ra Vào & Kiểm Soát Cửa An Ninh Bằng Thị Giác Máy](#sc-20) |

---

## [SC-01] AI Agent Trợ Lý Điều Khiển & Tự Động Hóa Smart Home Bằng Ngôn Ngữ Tự Nhiên

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân doanh nghiệp bất động sản có hàng chục thiết bị thông minh (đèn, rèm, điều hòa, khóa cửa, TV) từ nhiều hãng, mỗi thứ một app; việc điều khiển rời rạc và không ai lập được kịch bản tự động phức tạp. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hiểu yêu cầu tiếng Việt tự nhiên ('tối nay có khách, chuẩn bị phòng khách'), tự lập kế hoạch chuỗi hành động, gọi tool điều khiển từng thiết bị, ghi nhớ thói quen và sở thích của từng thành viên để tự động hóa theo ngữ cảnh (giờ, thời tiết, người ở nhà); đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Mọi lệnh chạm tới an ninh (mở khóa cửa, tắt camera) hoặc thiết bị công suất lớn phải qua human-in-the-loop xác nhận; dữ liệu thói quen sinh hoạt là riêng tư phải mã hóa và phân quyền theo hộ; agent phải cảnh báo khi lệnh mâu thuẫn hoặc vượt giới hạn an toàn (ví dụ bật bình nóng lạnh khi không ai ở nhà nhiều giờ); độ trễ phản hồi điều khiển < 2s.

### 🛠️ Tech Stack
• LLM (GPT-4o/Claude/Llama-3) cho NLU & tool-calling
• LangGraph điều phối agent (plan → act → verify)
• MQTT broker (Mosquitto/EMQX) + Home Assistant làm IoT hub mô phỏng thiết bị
• Redis cho session memory + Postgres/pgvector cho long-term memory thói quen
• FastAPI backend
• React/Next.js dashboard + WebSocket realtime
• deploy Docker trên Render/Railway/VPS.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy online có đăng nhập 2 vai trò (Chủ hộ / Thành viên), dashboard hiển thị & điều khiển ≥8 thiết bị mô phỏng
• agent nhận lệnh tiếng Việt, lập kế hoạch multi-step, gọi tool bật/tắt/điều chỉnh, HITL xác nhận lệnh nhạy cảm, log lịch sử hành động.

Nâng cao:
• Memory học thói quen đề xuất scene tự động, tự kích hoạt theo ngữ cảnh (thời tiết/giờ/vắng nhà), xử lý lệnh mơ hồ bằng hỏi lại, phát hiện & cảnh báo xung đột lệnh, phân quyền chi tiết trẻ em không được mở khóa cửa
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-02] AI Agent Tối Ưu Năng Lượng Hộ Gia Đình & Tòa Nhà doanh nghiệp bất động sản

### 📝 Mô tả đề tài
📍 Thực trạng: Hóa đơn điện các căn hộ và tòa nhà tăng cao vào giờ cao điểm; cư dân không biết thiết bị nào ngốn điện, ban quản lý không tối ưu được phụ tải chung. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phân tích dữ liệu tiêu thụ điện theo thời gian thực từ các đồng hồ/cảm biến, dự báo phụ tải, đề xuất và (khi được phép) tự động dịch chuyển tải, tắt thiết bị chờ, tối ưu điều hòa để giảm chi phí mà vẫn đảm bảo tiện nghi; lập kế hoạch tối ưu theo biểu giá điện bậc thang/giờ; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Lệnh tự động tắt/giảm tải thiết bị phải HITL với thiết bị ưu tiên (y tế, tủ lạnh, làm việc); dữ liệu tiêu thụ điện gắn với riêng tư hộ gia đình phải ẩn danh & bảo mật; dự báo phải đạt sai số MAPE hợp lý; agent cảnh báo khi tối ưu có thể ảnh hưởng an toàn/tiện nghi; độ trễ ra quyết định điều tiết realtime.

### 🛠️ Tech Stack
• LLM cho reasoning & giải thích khuyến nghị
• LangGraph agent (forecast → optimize → recommend/act)
• mô hình dự báo phụ tải (Prophet/LSTM/XGBoost)
• time-series DB (InfluxDB/TimescaleDB)
• MQTT giả lập smart meter & thiết bị
• thuật toán tối ưu (rule + LP/heuristic)
• FastAPI + Celery
• React dashboard biểu đồ (Recharts)
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy đăng nhập 2 vai trò (Cư dân / BQL tòa nhà), dashboard tiêu thụ realtime + dự báo
• agent phân tích, xác định thiết bị ngốn điện, đề xuất tối ưu có giải thích, HITL trước khi điều tiết.

Nâng cao:
• Tự động dịch tải theo biểu giá giờ, tối ưu phụ tải toàn tòa (peak shaving), mô phỏng tiết kiệm kịch bản 'nếu-thì', tích hợp điện mặt trời/pin, cảnh báo bất thường tiêu thụ (thiết bị hỏng/rò)
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-03] AI Agent Giám Sát & Cảnh Báo An Ninh Từ Camera AI Khu Đô Thị

### 📝 Mô tả đề tài
📍 Thực trạng: Khu đô thị có hàng trăm camera nhưng bảo vệ không thể xem hết; sự cố an ninh (đột nhập, người lạ, tụ tập, để quên đồ) thường bị phát hiện muộn qua xem lại. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát luồng camera, dùng computer vision phát hiện sự kiện bất thường (xâm nhập vùng cấm, té ngã, đám đông, vật thể bỏ lại), tự đánh giá mức độ nghiêm trọng, lập kế hoạch phản ứng (thông báo bảo vệ, ghi nhận, gọi hỗ trợ), ghi nhớ ngữ cảnh khu vực để giảm báo động giả; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Mọi hành động escalation (báo động, khóa cổng) với sự cố nghiêm trọng phải HITL do người trực xác nhận; dữ liệu hình ảnh khuôn mặt/cư dân cực kỳ nhạy cảm phải làm mờ, phân quyền chặt, tuân thủ quyền riêng tư; độ chính xác phát hiện cao & kiểm soát false positive; độ trễ cảnh báo realtime cho sự cố an toàn.

### 🛠️ Tech Stack
• Vision model (YOLOv8/v11, có thể kết hợp VLM cho mô tả cảnh)
• LLM cho reasoning phân loại mức độ & sinh báo cáo
• LangGraph agent (detect → assess → plan → alert/HITL)
• OpenCV + luồng video mẫu/RTSP giả lập
• vector DB lưu embedding sự kiện
• Postgres
• FastAPI + WebSocket
• React dashboard grid camera + timeline
• deploy Docker (GPU tùy chọn).
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Bảo vệ trực / Quản lý an ninh), grid camera mô phỏng, agent phát hiện ≥3 loại sự kiện, phân loại mức độ, gửi cảnh báo có ảnh & mô tả, HITL xác nhận escalation, nhật ký sự cố.

Nâng cao:
• Giảm báo động giả bằng memory ngữ cảnh khu vực/giờ, theo dõi đối tượng qua nhiều camera, sinh báo cáo tự động, làm mờ khuôn mặt tự động, dashboard heatmap điểm nóng an ninh
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-04] AI Agent Phát Hiện Bất Thường Cảm Biến IoT (Rò Rỉ Gas, Cháy, Ngập Nước)

### 📝 Mô tả đề tài
📍 Thực trạng: Căn hộ và tầng hầm được lắp cảm biến khói, gas, nhiệt, ngập nước nhưng chỉ kêu chuông tại chỗ, không phân tích tương quan, dễ bỏ sót sự cố sớm hoặc báo động nhiễu. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent liên tục thu dữ liệu đa cảm biến, phát hiện bất thường & tương quan (nhiệt tăng + khói = nguy cơ cháy), đánh giá mức nguy hiểm, lập kế hoạch ứng phó (thông báo cư dân/BQL, hướng dẫn xử lý, kích van/quạt khi được phép), ghi nhớ mẫu bình thường của từng khu để giảm nhiễu; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Lệnh vật lý (đóng van gas/nước, ngắt điện, kích chuông toàn khu) phải HITL trừ ngưỡng nguy hiểm tính mạng đã định trước; dữ liệu cảm biến & vị trí căn hộ bảo mật; độ chính xác & độ nhạy phải cân bằng để không bỏ sót lẫn không nhiễu; độ trễ cực thấp cho sự cố an toàn tính mạng. Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho reasoning tương quan & sinh hướng dẫn
• LangGraph agent (ingest → detect anomaly → correlate → plan → act/HITL)
• mô hình anomaly detection (Isolation Forest/thresholding + LSTM)
• MQTT giả lập cảm biến
• InfluxDB/TimescaleDB
• FastAPI
• React dashboard realtime + bản đồ tầng
• push/email cảnh báo
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Cư dân / Kỹ thuật BQL), giám sát ≥4 loại cảm biến mô phỏng, agent phát hiện bất thường & phân mức nguy hiểm, cảnh báo đa kênh, HITL cho lệnh vật lý, log sự cố.

Nâng cao:
• Tương quan đa cảm biến phát hiện sớm cháy/rò, tự động ứng phó ngưỡng nguy cấp có ghi nhận, học baseline giảm nhiễu, mô phỏng lan truyền sự cố & gợi ý sơ tán, báo cáo sau sự cố
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-05] AI Agent Đỗ Xe Thông Minh & Dẫn Đường Trong Bãi

### 📝 Mô tả đề tài
📍 Thực trạng: Bãi đỗ xe tầng hầm khu doanh nghiệp bất động sản lớn, giờ cao điểm tài xế loanh quanh tìm chỗ trống gây tắc và bực bội; hệ thống hiện chỉ hiển thị số chỗ trống tổng. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent theo dõi trạng thái từng ô đỗ (cảm biến/camera), nhận yêu cầu của tài xế qua ngôn ngữ tự nhiên (gần thang máy, gần cửa ra, sạc điện), lập kế hoạch phân bổ & dẫn đường tối ưu tới ô trống, cập nhật động khi tình huống thay đổi, ghi nhớ ưu tiên của cư dân; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Lệnh dành riêng ô ưu tiên / mở barrier phải HITL với BQL; dữ liệu biển số & lịch trình ra vào là riêng tư phải bảo mật; định vị & chỉ đường phải chính xác đúng ô; độ trễ realtime để tránh xung đột hai xe cùng ô. Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho hiểu yêu cầu & sinh chỉ dẫn
• LangGraph agent (allocate → route → monitor → re-plan)
• thuật toán tìm đường (A*) trên sơ đồ bãi
• vision/cảm biến giả lập trạng thái ô
• Redis trạng thái realtime
• Postgres
• MQTT
• FastAPI + WebSocket
• React bản đồ bãi tương tác
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Tài xế / BQL bãi), sơ đồ bãi realtime hiển thị ô trống/đầy, agent nhận yêu cầu tự nhiên, phân ô & chỉ đường từng bước, cập nhật khi ô bị chiếm, HITL cho ô ưu tiên.

Nâng cao:
• Dự báo lấp đầy theo giờ, gợi ý ô sạc EV, tối ưu phân bổ toàn bãi giảm tắc, đặt chỗ trước, cảnh báo đỗ sai/quá giờ, thống kê lưu lượng cho BQL
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-06] AI Agent Quản Lý Chiếu Sáng Đô Thị Thích Ứng

### 📝 Mô tả đề tài
📍 Thực trạng: Đèn đường và chiếu sáng công cộng khu đô thị bật/tắt theo lịch cứng, gây lãng phí điện khi vắng người và thiếu sáng khi cần; sự cố đèn hỏng phát hiện chậm. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent điều tiết độ sáng thích ứng theo lưu lượng người/xe, thời tiết, ánh sáng tự nhiên và sự kiện; lập kế hoạch điều chỉnh dimming theo tuyến/khu để tiết kiệm điện nhưng đảm bảo an toàn; giám sát sức khỏe đèn, ghi nhớ mẫu sử dụng để tối ưu; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Giảm sáng dưới ngưỡng an toàn ở khu vực nhạy cảm (ngã tư, lối đi bộ) phải HITL/khóa cứng ngưỡng tối thiểu; dữ liệu cảm biến chuyển động không được nhận diện cá nhân; độ chính xác phát hiện hiện diện; độ trễ điều chỉnh hợp lý; đảm bảo an toàn giao thông ban đêm. Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho reasoning chính sách chiếu sáng & giải thích
• LangGraph agent (sense → decide → actuate → monitor)
• cảm biến chuyển động/độ sáng & đèn giả lập qua MQTT
• time-series DB
• rule engine + tối ưu tiết kiệm
• FastAPI
• React dashboard bản đồ tuyến đèn
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Vận hành / Giám sát đô thị), bản đồ tuyến đèn realtime, agent điều chỉnh dimming thích ứng theo hiện diện & thời tiết, giữ ngưỡng an toàn (HITL khi vượt), log tiết kiệm điện.

Nâng cao:
• Dự báo lịch tối ưu theo mùa/sự kiện, phát hiện đèn hỏng & tạo yêu cầu bảo trì, tối ưu toàn khu giảm % điện, mô phỏng kịch bản, báo cáo tiết kiệm & an toàn
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-07] AI Agent Giám Sát Chất Lượng Không Khí & Môi Trường Đô Thị

### 📝 Mô tả đề tài
📍 Thực trạng: Khu đô thị có cảm biến bụi mịn, CO2, tiếng ồn, nhiệt độ nhưng dữ liệu rời rạc, cư dân không có cảnh báo kịp thời khi ô nhiễm vượt ngưỡng ảnh hưởng sức khỏe. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tổng hợp dữ liệu môi trường đa điểm, phát hiện & dự báo đợt ô nhiễm, đánh giá mức ảnh hưởng sức khỏe theo nhóm (trẻ em, người già, người bệnh hô hấp), lập kế hoạch cảnh báo cá nhân hóa và khuyến nghị hành động (đóng cửa, bật lọc khí, hạn chế ra ngoài), có thể liên động điều khiển hệ thống thông gió; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Lệnh liên động hệ thống thông gió/lọc khí chung phải HITL với BQL; dữ liệu vị trí & tình trạng sức khỏe cư dân bảo mật; độ chính xác cảm biến & dự báo; cảnh báo phải kịp thời trước khi ngưỡng nguy hại; tránh cảnh báo nhiễu gây mệt mỏi. Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho diễn giải chỉ số & khuyến nghị cá nhân hóa
• LangGraph agent (aggregate → forecast → assess → alert)
• dự báo chuỗi thời gian (Prophet/LSTM)
• cảm biến môi trường giả lập MQTT
• TimescaleDB
• FastAPI
• React dashboard bản đồ nhiệt AQI
• push/email
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Cư dân / BQL môi trường), dashboard AQI realtime đa điểm, agent đánh giá mức ảnh hưởng, cảnh báo khi vượt ngưỡng kèm khuyến nghị, HITL cho liên động thiết bị.

Nâng cao:
• Dự báo ô nhiễm nhiều giờ tới, cảnh báo cá nhân hóa theo nhóm sức khỏe, bản đồ nhiệt lan truyền, tự động điều tiết thông gió (có ghi nhận), báo cáo môi trường định kỳ
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-08] AI Agent Dự Báo & Điều Tiết Giao Thông Nội Khu Đô Thị

### 📝 Mô tả đề tài
📍 Thực trạng: Cổng ra vào và trục đường chính khu đô thị ùn tắc giờ cao điểm và sự kiện; đèn tín hiệu & phân luồng cố định không thích ứng. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent thu dữ liệu lưu lượng từ camera/cảm biến, dự báo ùn tắc, lập kế hoạch điều tiết (đề xuất pha đèn, mở làn, gợi ý lộ trình thay thế cho cư dân), phối hợp đa nút giao, ghi nhớ mẫu giao thông theo giờ/ngày/sự kiện để tối ưu; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Thay đổi pha đèn tín hiệu thực tế phải HITL với trung tâm điều hành; dữ liệu biển số/hành trình phải ẩn danh; dự báo phải đủ chính xác để tránh điều tiết sai gây tắc nặng hơn; độ trễ realtime; ưu tiên an toàn (xe cứu thương/cứu hỏa). Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho reasoning & giải thích chiến lược điều tiết
• LangGraph agent (predict → plan → coordinate → recommend/act)
• mô hình dự báo lưu lượng (LSTM/GNN đơn giản)
• vision đếm xe giả lập
• time-series DB
• mô phỏng mạng giao thông (SUMO tùy chọn)
• FastAPI + WebSocket
• React bản đồ giao thông
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Cư dân / Điều hành giao thông), bản đồ lưu lượng realtime, agent dự báo ùn tắc & đề xuất điều tiết + lộ trình thay thế, HITL cho đổi pha đèn, log.

Nâng cao:
• Điều phối đa nút giao tối ưu tổng thể, ưu tiên xe khẩn cấp (green wave), mô phỏng kịch bản sự kiện, cảnh báo cư dân trước ùn tắc, thống kê hiệu quả điều tiết
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-09] AI Agent Bảo Trì Dự Đoán Thiết Bị IoT & Hạ Tầng Kỹ Thuật

### 📝 Mô tả đề tài
📍 Thực trạng: Thang máy, máy bơm, máy phát, HVAC, camera trong khu đô thị hỏng đột ngột gây gián đoạn và chi phí sửa chữa cao; bảo trì hiện theo lịch cố định, không theo tình trạng. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent theo dõi dữ liệu vận hành & cảm biến (rung, nhiệt, dòng điện, giờ chạy), dự đoán hư hỏng sớm, đánh giá mức độ khẩn, lập kế hoạch bảo trì (tạo lệnh công việc, xếp lịch kỹ thuật, đặt vật tư), ghi nhớ lịch sử thiết bị để cải thiện dự đoán; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Lệnh dừng thiết bị để bảo trì phải HITL do kỹ thuật xác nhận; dữ liệu vận hành hạ tầng bảo mật; dự đoán phải giảm cả false alarm lẫn bỏ sót; cảnh báo kịp thời trước khi hỏng gây mất an toàn; ưu tiên thiết bị an toàn (thang máy, PCCC). Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho phân tích & sinh lệnh công việc
• LangGraph agent (monitor → predict → prioritize → schedule/HITL)
• mô hình predictive maintenance (RUL, anomaly detection)
• cảm biến rung/nhiệt/dòng giả lập MQTT
• TimescaleDB
• FastAPI
• React dashboard sức khỏe thiết bị + lịch bảo trì
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Kỹ thuật viên / Quản lý kỹ thuật), dashboard sức khỏe ≥5 thiết bị mô phỏng, agent dự đoán hư hỏng & phân mức khẩn, tự tạo & xếp lịch lệnh bảo trì, HITL dừng máy.

Nâng cao:
• Ước tính thời gian còn lại (RUL), tối ưu lịch bảo trì theo nguồn lực/vật tư, cảnh báo bất thường sớm, phân tích nguyên nhân gốc, báo cáo & KPI độ tin cậy thiết bị
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-10] AI Agent Trợ Lý Cư Dân Điều Khiển Thiết Bị & Quản Lý Kịch Bản (Scene)

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân muốn các 'kịch bản' sinh hoạt (đi ngủ, ra khỏi nhà, xem phim, đón khách) nhưng thiết lập scene trong app rất rối và không linh hoạt theo ngữ cảnh. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent trợ lý cư dân hiểu mô tả kịch bản bằng ngôn ngữ tự nhiên, tự sinh & tinh chỉnh scene (chuỗi hành động đa thiết bị), gợi ý scene mới từ thói quen, thực thi có điều kiện (nếu trời mưa thì đóng rèm), và cho phép cư dân xem trước/hỏi lại trước khi lưu; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Scene chứa hành động an ninh (khóa/mở cửa, tắt camera) khi kích hoạt phải HITL; dữ liệu thói quen & lịch trình riêng tư bảo mật, phân quyền theo thành viên; hành vi agent phải nhất quán & giải thích được; độ trễ thực thi scene thấp; cảnh báo scene xung đột. Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho sinh & chỉnh scene từ ngôn ngữ tự nhiên
• LangGraph agent (understand → compose scene → simulate → confirm → execute)
• MQTT + Home Assistant giả lập thiết bị
• Postgres lưu scene + pgvector gợi ý
• Redis
• FastAPI
• React trình soạn scene trực quan
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Chủ hộ / Thành viên), tạo scene bằng mô tả tự nhiên với ≥6 thiết bị, agent sinh chuỗi hành động + xem trước, kích hoạt scene, HITL cho hành động an ninh, thư viện scene.

Nâng cao:
• Gợi ý scene từ thói quen (memory), scene có điều kiện theo thời tiết/giờ/hiện diện, phát hiện & giải quyết xung đột scene, phân quyền chỉnh sửa, lịch tự động kích hoạt
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-11] AI Agent Quản Lý Thu Gom Rác Thải Thông Minh Khu Đô Thị

### 📝 Mô tả đề tài
📍 Thực trạng: Thùng rác công cộng và điểm tập kết trong khu đô thị đầy tràn không đúng lịch, xe thu gom chạy theo tuyến cố định gây lãng phí và mất vệ sinh. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát mức đầy các thùng rác (cảm biến/ảnh), dự báo thời điểm đầy, lập kế hoạch & tối ưu tuyến thu gom động theo mức đầy và ưu tiên, điều phối xe/nhân sự, phân loại rác qua ảnh và cảnh báo đổ rác sai; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Điều phối tuyến/lệnh cho đội thu gom phải HITL với điều phối viên; ảnh khu vực/cư dân đổ rác phải bảo mật & làm mờ; dự báo mức đầy đủ chính xác để không bỏ sót; ưu tiên điểm phát sinh mùi/nguy hại; độ trễ cập nhật hợp lý. Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho reasoning điều phối & giải thích
• LangGraph agent (monitor → predict → optimize route → dispatch/HITL)
• dự báo mức đầy (regression/time-series)
• vision phân loại rác (CNN) tùy chọn
• thuật toán tối ưu tuyến (VRP heuristic)
• cảm biến giả lập MQTT
• Postgres + PostGIS
• FastAPI
• React bản đồ tuyến
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Điều phối viên / Đội thu gom), bản đồ thùng rác & mức đầy realtime, agent dự báo đầy & đề xuất tuyến thu gom tối ưu, HITL duyệt tuyến, log.

Nâng cao:
• Tối ưu VRP đa xe theo thời gian/quãng đường, phân loại rác qua ảnh & cảnh báo sai quy định, dự báo theo mùa/sự kiện, thống kê khối lượng & hiệu quả, cảnh báo điểm quá tải
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-12] AI Agent Giám Sát Tiêu Thụ Nước & Phát Hiện Thất Thoát

### 📝 Mô tả đề tài
📍 Thực trạng: Hệ thống cấp nước khu đô thị bị rò rỉ, vỡ ống ngầm, hoặc rò trong căn hộ gây thất thoát lớn và phát hiện chậm qua hóa đơn; tiêu thụ bất thường không được cảnh báo. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent theo dõi lưu lượng & áp suất nước theo tuyến/căn hộ, phát hiện bất thường (rò rỉ, vỡ ống, dùng bất thường ban đêm), khoanh vùng vị trí nghi ngờ, đánh giá mức nghiêm trọng, lập kế hoạch xử lý (cảnh báo, tạo lệnh sửa, đề xuất đóng van khu vực), ghi nhớ mẫu tiêu thụ bình thường; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Lệnh đóng van cấp nước khu vực phải HITL với kỹ thuật vì ảnh hưởng nhiều hộ; dữ liệu tiêu thụ hộ gia đình riêng tư bảo mật; độ chính xác khoanh vùng để không cắt nhầm; cảnh báo kịp thời hạn chế thất thoát; tránh báo động giả với dao động bình thường. Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho reasoning & sinh hướng dẫn xử lý
• LangGraph agent (monitor → detect leak → localize → plan → act/HITL)
• anomaly detection + phân tích cân bằng lưu lượng theo phân vùng (DMA)
• cảm biến lưu lượng/áp suất giả lập MQTT
• TimescaleDB
• FastAPI
• React dashboard sơ đồ mạng nước
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Cư dân / Kỹ thuật cấp nước), dashboard tiêu thụ & áp suất realtime, agent phát hiện bất thường & khoanh vùng nghi rò, cảnh báo phân mức, HITL cho đóng van, log sự cố.

Nâng cao:
• Khoanh vùng chính xác theo cân bằng DMA, phân biệt rò rỉ vs dùng nhiều, ước tính lượng thất thoát & chi phí, tạo lệnh sửa tự động, dự báo tiêu thụ & phát hiện dùng bất thường ban đêm
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-13] AI Agent Điều Phối Thang Máy Thông Minh Tòa Nhà Cao Tầng

### 📝 Mô tả đề tài
📍 Thực trạng: Tòa nhà doanh nghiệp bất động sản nhiều thang máy nhưng giờ cao điểm cư dân chờ lâu; thuật toán điều phối truyền thống không thích ứng với mẫu lưu lượng thực tế. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent thu dữ liệu gọi thang, tải, vị trí cabin và mẫu lưu lượng theo giờ; dự báo nhu cầu; lập kế hoạch điều phối nhóm thang tối ưu (giảm thời gian chờ & di chuyển), gán cabin thông minh, ưu tiên tình huống đặc biệt (khẩn cấp, chuyển nhà, người khuyết tật), ghi nhớ mẫu lưu lượng để cải thiện; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Ghi đè thủ công/chế độ khẩn cấp (khóa tầng, ưu tiên cứu hỏa) phải HITL với BQL; dữ liệu di chuyển cư dân riêng tư bảo mật; thuật toán phải an toàn tuyệt đối (không vượt tải, không kẹt); độ trễ ra quyết định realtime; đảm bảo công bằng không để ai chờ quá lâu. Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho reasoning chiến lược & giải thích
• LangGraph agent (predict demand → dispatch → optimize → adapt)
• thuật toán điều phối nhóm thang (heuristic/RL đơn giản)
• mô phỏng thang máy & gọi tầng
• Redis realtime
• time-series DB mẫu lưu lượng
• FastAPI + WebSocket
• React mô phỏng tòa nhà & cabin
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Cư dân / BQL tòa nhà), mô phỏng ≥3 thang & nhiều tầng realtime, agent điều phối gán cabin giảm thời gian chờ, dự báo giờ cao điểm, HITL cho chế độ khẩn/ghi đè, log hiệu năng.

Nâng cao:
• Tối ưu nhóm thang theo mẫu lưu lượng học được, ưu tiên đặc biệt (khẩn/khuyết tật/chuyển nhà), mô phỏng so sánh thuật toán, cảnh báo tải/kẹt, thống kê thời gian chờ trung bình
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-14] AI Agent An Toàn Cháy Nổ & Điều Phối Sơ Tán Thông Minh

### 📝 Mô tả đề tài
📍 Thực trạng: Khi có cháy tại tòa nhà cao tầng, cư dân hoảng loạn, không biết lối thoát an toàn; hệ thống báo cháy chỉ hú còi mà không hướng dẫn sơ tán theo tình huống thực tế. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tổng hợp dữ liệu cảm biến cháy/khói/nhiệt & camera để định vị & đánh giá đám cháy, lập kế hoạch sơ tán động (tính toán lối thoát an toàn theo vị trí cháy & mật độ người), hướng dẫn cá nhân hóa cho từng cư dân qua app/loa, điều phối lực lượng cứu hộ và cập nhật liên tục khi tình huống thay đổi; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Kích hoạt sơ tán toàn tòa & liên động (mở cửa thoát hiểm, ngắt điện, tăng áp cầu thang) phải có HITL/ngưỡng an toàn được duyệt trước; dữ liệu vị trí cư dân nhạy cảm chỉ dùng cho cứu hộ; độ chính xác định vị đám cháy tối quan trọng; độ trễ cực thấp vì liên quan tính mạng; kế hoạch phải luôn có phương án dự phòng khi lối thoát bị chặn.

### 🛠️ Tech Stack
• LLM cho reasoning kế hoạch sơ tán & sinh hướng dẫn
• LangGraph agent (detect → localize → plan evacuation → guide → coordinate)
• thuật toán tìm đường an toàn (A* trên đồ thị tòa nhà, tránh vùng cháy)
• cảm biến & camera giả lập MQTT
• digital twin sơ đồ tòa nhà
• FastAPI + WebSocket
• React bản đồ sơ tán realtime
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Cư dân / Chỉ huy cứu hộ), sơ đồ tòa nhà + cảm biến mô phỏng, agent định vị cháy & sinh lối thoát an toàn cá nhân hóa, HITL kích hoạt sơ tán, log diễn biến.

Nâng cao:
• Tính lối thoát tránh vùng cháy & tắc nghẽn động, cập nhật realtime khi lối bị chặn, điều phối cứu hộ & điểm tập kết, mô phỏng kịch bản diễn tập, thống kê thời gian sơ tán
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-15] AI Agent Digital Twin Vận Hành Khu Đô Thị Thông Minh

### 📝 Mô tả đề tài
📍 Thực trạng: Ban quản lý khu đô thị vận hành nhiều hệ thống rời rạc (điện, nước, an ninh, giao thông, thiết bị) mà không có cái nhìn tổng thể realtime để ra quyết định và mô phỏng tác động. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent làm 'bộ não' trên bản sao số (digital twin) của khu đô thị: tổng hợp dữ liệu đa hệ thống, trả lời câu hỏi vận hành bằng ngôn ngữ tự nhiên, mô phỏng kịch bản 'nếu-thì' (mất điện, sự kiện đông người, thời tiết xấu), phát hiện tình huống cần chú ý và đề xuất/điều phối hành động qua các hệ thống con; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Mọi lệnh tác động thực tế lên hệ thống con phải HITL với quản lý vận hành; dữ liệu tổng hợp toàn khu rất nhạy cảm, phân quyền & bảo mật nghiêm ngặt; mô phỏng phải phản ánh đủ chính xác để tin cậy; độ trễ cập nhật twin hợp lý; agent phải nêu rõ giả định & giới hạn khi mô phỏng. Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho hỏi-đáp vận hành & reasoning kịch bản
• LangGraph agent điều phối multi-domain (tích hợp các hệ con qua API/tool)
• mô phỏng twin (dữ liệu tổng hợp từ các module SC khác/giả lập)
• MQTT + time-series DB + Postgres
• RAG trên tài liệu vận hành
• FastAPI
• React dashboard 2D/3D bản đồ khu đô thị
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Vận hành viên / Lãnh đạo BQL), bản đồ khu đô thị tổng hợp realtime ≥3 hệ thống mô phỏng, agent trả lời câu hỏi vận hành tự nhiên & cảnh báo tình huống, HITL cho lệnh liên hệ thống.

Nâng cao:
• Mô phỏng kịch bản 'nếu-thì' đa hệ thống, phát hiện tương quan sự cố chéo hệ, đề xuất & điều phối hành động end-to-end, dashboard KPI đô thị, báo cáo tự động & giải thích giả định mô phỏng
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-16] AI Agent Quản Lý & Tối Ưu Trạm Sạc Xe Điện doanh nghiệp ô tô Trong Khu

### 📝 Mô tả đề tài
📍 Thực trạng: Số cột sạc EV trong khu đô thị có hạn, giờ cao điểm cư dân tranh chỗ sạc, phụ tải sạc đồng thời gây quá tải lưới nội khu và chi phí điện giờ cao điểm. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent quản lý hàng đợi & lịch sạc thông minh, nhận yêu cầu cư dân (cần đầy trước giờ nào), lập kế hoạch phân bổ cột & lịch sạc tối ưu, điều tiết công suất sạc (smart charging) để tránh quá tải và tận dụng giờ điện rẻ, ghi nhớ thói quen sạc để dự báo nhu cầu; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Lệnh giảm/ngắt công suất sạc xe đang sạc phải HITL/thông báo & đồng ý cư dân; dữ liệu hành trình & pin xe riêng tư bảo mật; tối ưu phải đảm bảo xe đủ pin đúng cam kết thời gian; không vượt giới hạn tải lưới nội khu (an toàn); độ trễ realtime cho phân bổ. Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho hiểu yêu cầu & giải thích lịch sạc
• LangGraph agent (request → schedule → load-balance → adapt)
• thuật toán smart charging / tối ưu phụ tải (LP/heuristic)
• dự báo nhu cầu sạc
• cột sạc & xe giả lập MQTT
• time-series DB
• FastAPI + WebSocket
• React dashboard trạm sạc & hàng đợi
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Cư dân / Vận hành trạm), dashboard cột sạc realtime & hàng đợi, agent nhận yêu cầu sạc, phân bổ cột & lập lịch, điều tiết công suất tránh quá tải, HITL/thông báo khi giảm công suất.

Nâng cao:
• Smart charging tối ưu giờ điện rẻ, đảm bảo cam kết thời gian đầy pin, dự báo nhu cầu & gợi ý khung giờ, cân bằng tải lưới nội khu, đặt lịch trước & thanh toán mô phỏng, thống kê sử dụng
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-17] AI Agent Tối Ưu Điều Hòa & HVAC Tòa Nhà Theo Ngữ Cảnh

### 📝 Mô tả đề tài
📍 Thực trạng: Hệ thống điều hòa trung tâm tòa nhà văn phòng/thương mại trung tâm thương mại của doanh nghiệp chạy theo cài đặt cố định, lạnh thừa nơi vắng người và thiếu nơi đông, tiêu tốn năng lượng lớn. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent điều khiển HVAC thích ứng theo số người thực tế, nhiệt độ ngoài trời, độ ẩm, giờ hoạt động và phản hồi tiện nghi; lập kế hoạch tối ưu setpoint & luồng khí theo vùng, dự báo tải nhiệt để làm mát/sưởi trước, cân bằng tiết kiệm năng lượng với tiện nghi, ghi nhớ sở thích & mẫu sử dụng từng khu; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Thay đổi setpoint vượt ngưỡng tiện nghi/an toàn (khu vực đặc biệt, kho lạnh) phải HITL với quản lý tòa nhà; dữ liệu hiện diện không nhận diện cá nhân; độ chính xác cảm biến & dự báo tải nhiệt; độ trễ điều khiển hợp lý; đảm bảo chất lượng không khí trong nhà (CO2) không xuống dưới ngưỡng an toàn.

### 🛠️ Tech Stack
• LLM cho reasoning chính sách & giải thích khuyến nghị
• LangGraph agent (sense → predict load → optimize setpoint → actuate → monitor)
• dự báo tải nhiệt (regression/LSTM)
• tối ưu (rule + MPC/heuristic)
• cảm biến nhiệt/ẩm/CO2/hiện diện & HVAC giả lập MQTT
• TimescaleDB
• FastAPI
• React dashboard vùng HVAC
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Cư dân/Nhân viên / Quản lý tòa nhà), dashboard HVAC đa vùng realtime, agent điều chỉnh setpoint thích ứng theo hiện diện & thời tiết, giữ ngưỡng tiện nghi/CO2, HITL khi vượt ngưỡng, log tiết kiệm.

Nâng cao:
• Làm mát/sưởi trước theo dự báo tải nhiệt, tối ưu đa vùng cân bằng tiện nghi-năng lượng, học sở thích khu vực, phát hiện lãng phí & thiết bị HVAC lỗi, báo cáo tiết kiệm % & tiện nghi
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-18] AI Agent Cảnh Báo Thời Tiết Cực Đoan & Ứng Phó Thiên Tai Khu Đô Thị

### 📝 Mô tả đề tài
📍 Thực trạng: Khu đô thị đối mặt mưa lớn gây ngập, bão, giông sét, nắng nóng cực đoan nhưng cư dân & BQL thường bị động, không có cảnh báo sớm cá nhân hóa và kế hoạch ứng phó phối hợp. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tổng hợp dữ liệu thời tiết (API dự báo + cảm biến khu vực: mực nước, mưa, gió), đánh giá rủi ro cho từng khu vực (hầm xe, khu trũng), lập kế hoạch ứng phó (cảnh báo cư dân theo vị trí, đề xuất di dời xe khỏi hầm ngập, kích hoạt bơm chống ngập, chuẩn bị lực lượng), điều phối & cập nhật liên tục theo diễn biến, ghi nhớ vùng rủi ro; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Lệnh liên động (kích bơm, đóng cửa chống ngập, sơ tán hầm xe) phải HITL với BQL; dữ liệu vị trí & tài sản cư dân bảo mật; độ chính xác dự báo & đánh giá rủi ro; cảnh báo phải sớm & kịp thời trước sự kiện; tránh cảnh báo nhiễu làm giảm độ tin cậy. Mọi lệnh điều khiển thiết bị phải đi qua lớp kiểm tra bất biến an toàn xác định (chống xung đột lệnh hoặc vòng lặp bật-tắt vô hạn) trước khi thực thi trên môi trường mô phỏng và có HITL cho tác vụ nhạy cảm.

### 🛠️ Tech Stack
• LLM cho đánh giá rủi ro & sinh cảnh báo/hướng dẫn
• LangGraph agent (fetch forecast → assess risk → plan → alert → coordinate)
• WebFetch/API thời tiết (mô phỏng) + cảm biến mực nước/mưa giả lập MQTT
• mô hình rủi ro ngập theo địa hình
• TimescaleDB + PostGIS
• FastAPI
• React bản đồ rủi ro
• push/email/SMS mô phỏng
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Cư dân / BQL ứng phó), dashboard thời tiết & cảm biến realtime, agent đánh giá rủi ro theo khu & gửi cảnh báo sớm cá nhân hóa kèm hướng dẫn, HITL cho liên động chống ngập, log.

Nâng cao:
• Dự báo ngập theo địa hình & mưa, kế hoạch ứng phó phối hợp đa lực lượng, đề xuất di dời xe khỏi hầm, cập nhật realtime theo diễn biến, mô phỏng kịch bản bão/ngập, báo cáo sau sự kiện
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-19] AI Agent Trợ Lý Vận Hành & Chăm Sóc Cư Dân Đa Kênh (Smart Building Concierge)

### 📝 Mô tả đề tài
📍 Thực trạng: Cư dân doanh nghiệp bất động sản gửi yêu cầu dịch vụ (báo hỏng, đặt tiện ích, hỏi thông tin, phản ánh) qua nhiều kênh rời rạc; BQL xử lý thủ công, chậm, thiếu theo dõi và thường phải điều phối nhiều bộ phận. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tiếp nhận yêu cầu cư dân bằng ngôn ngữ tự nhiên, phân loại & định tuyến, tự lập kế hoạch xử lý (tra cứu thông tin qua RAG, tạo ticket, đặt lịch kỹ thuật, kiểm tra trạng thái thiết bị IoT liên quan, đặt tiện ích), theo dõi tới khi hoàn tất và cập nhật cư dân, ghi nhớ lịch sử & sở thích từng hộ; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Hành động phát sinh chi phí hoặc điều phối nhân sự/kỹ thuật phải HITL xác nhận (cư dân và/hoặc BQL); dữ liệu cá nhân & yêu cầu cư dân bảo mật, phân quyền; agent phải trả lời chính xác dựa trên tài liệu chính thức (chống bịa); độ trễ phản hồi hợp lý; cảnh báo khi vượt thẩm quyền hoặc yêu cầu khẩn cấp cần con người.

### 🛠️ Tech Stack
• LLM cho hội thoại, phân loại & tool-calling
• LangGraph agent (understand → route → plan → act → follow-up)
• RAG (pgvector) trên tài liệu/quy định khu
• tích hợp tool giả lập (ticket, đặt tiện ích, tra trạng thái IoT qua MQTT)
• Postgres
• FastAPI + WebSocket
• React portal cư dân + trang BQL
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Cư dân / Nhân viên BQL), portal tiếp nhận yêu cầu tự nhiên, agent phân loại & định tuyến, tạo & theo dõi ticket, trả lời từ tài liệu (RAG), HITL cho hành động phát sinh chi phí, lịch sử yêu cầu.

Nâng cao:
• Điều phối đa bộ phận end-to-end, kiểm tra trạng thái thiết bị IoT liên quan trước khi cử kỹ thuật, đặt lịch/tiện ích tự động, cá nhân hóa theo lịch sử hộ, phát hiện yêu cầu khẩn chuyển người, dashboard SLA & mức hài lòng
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---

## [SC-20] AI Agent Giám Sát Ra Vào & Kiểm Soát Cửa An Ninh Bằng Thị Giác Máy

### 📝 Mô tả đề tài
📍 Thực trạng: Cổng, sảnh và cửa khu vực hạn chế trong khu đô thị kiểm soát ra vào thủ công hoặc thẻ từ, dễ bị đi kèm (tailgating), khó phát hiện người lạ/khách chưa đăng ký và không có cái nhìn tổng thể lưu lượng ra vào. Trong vận hành tòa nhà và đô thị thông minh thực tế, luồng dữ liệu cảm biến IoT thường có nhiễu, trễ hoặc mất kết nối cục bộ, trong khi các quy tắc tự động hóa đơn lẻ dễ xung đột lẫn nhau (như tiết kiệm điện mâu thuẫn với tiện nghi hoặc an toàn).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát các điểm ra vào qua camera, nhận diện cư dân/khách đã đăng ký vs người lạ, phát hiện hành vi bất thường (tailgating, lảng vảng, cố mở cửa), đánh giá rủi ro và lập kế hoạch phản ứng (cấp quyền mở cửa cho người hợp lệ, cảnh báo bảo vệ, ghi nhận khách), quản lý khách mời (mã QR/pre-registration) và ghi nhớ lịch sử ra vào; đồng thời kết hợp điều khiển tối ưu đa mục tiêu (năng lượng – tiện nghi – an toàn) và bộ kiểm tra xung đột quy tắc vật lý xác định với khả năng suy luận, lập kế hoạch và xử lý sự cố liên hệ thống của AI Agent.

🔒 Ràng buộc: Lệnh mở cửa khu vực an ninh & escalation phải HITL trừ trường hợp danh tính đã xác thực rõ ràng theo chính sách; dữ liệu sinh trắc/khuôn mặt cực nhạy cảm phải mã hóa, hạn chế lưu, làm mờ với người không liên quan, tuân thủ quyền riêng tư; độ chính xác nhận diện cao & kiểm soát nhận nhầm; độ trễ realtime để không gây tắc cổng; luôn có phương án dự phòng khi nhận diện thất bại.

### 🛠️ Tech Stack
• Vision (face/person detection: YOLO + face recognition/embedding, hoặc VLM)
• LLM cho reasoning rủi ro, quản lý khách & sinh báo cáo
• LangGraph agent (detect → identify → assess → decide → act/HITL)
• OpenCV + luồng camera giả lập
• vector DB lưu embedding đăng ký
• Postgres
• FastAPI + WebSocket
• React dashboard điểm ra vào + quản lý khách
• deploy Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu đô thị & tòa nhà thông minh quốc tế: Building Data Genome Project 2, ASHRAE Energy Predictor, UK-DALE, METR-LA (giao thông), EPANET / BattLeDIM (mạng lưới nước), OpenAQ và chuẩn giao thức Matter / Home Assistant.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy 2 vai trò (Bảo vệ / Quản lý an ninh), giám sát ≥2 điểm ra vào mô phỏng, agent nhận diện cư dân/khách vs người lạ, phát hiện ≥2 hành vi bất thường, đề xuất mở cửa/cảnh báo với HITL, nhật ký ra vào & làm mờ khuôn mặt.

Nâng cao:
• Quản lý khách mời qua QR/pre-registration, phát hiện tailgating & lảng vảng, đánh giá rủi ro thích ứng theo giờ/khu, phương án dự phòng khi nhận diện thất bại, thống kê lưu lượng & báo cáo sự cố an ninh
• Tích hợp bộ kiểm tra xung đột luật điều khiển/tối ưu hóa đa mục tiêu xác định và mô phỏng kịch bản biến động môi trường hoặc sự cố khẩn cấp trên mô hình số (Digital Twin).

---
