# Lĩnh vực: DEV - AI Thiết bị & Edge AI

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `DEV-01` | [Smart Cabin Copilot - Trợ lý giọng nói & đa phương thức trong xe chạy trên edge](#dev-01) |
| `DEV-02` | [DriverGuard - Hệ thống giám sát tài xế (DMS) phát hiện buồn ngủ & mất tập trung on-device](#dev-02) |
| `DEV-03` | [CabinSentinel - Giám sát trong khoang xe: chống bỏ quên trẻ em/vật nuôi & phát hiện đồ để quên](#dev-03) |
| `DEV-04` | [RoadWatch Copilot - Trợ lý cảnh báo hỗ trợ lái (ADAS) đa phương thức trên edge](#dev-04) |
| `DEV-05` | [AutoDoc - Trợ lý chẩn đoán xe & bảo dưỡng dự đoán từ dữ liệu OBD/CAN trên edge](#dev-05) |
| `DEV-06` | [EV RangeMind - Trợ lý sạc & lập lộ trình thông minh cho xe điện chạy on-device](#dev-06) |
| `DEV-07` | [MyCabin - Cá nhân hóa khoang lái theo hồ sơ & nhận diện tài xế trên edge](#dev-07) |
| `DEV-08` | [HandsFree Messenger - Trợ lý an toàn khi lái: đọc/soạn tin & tóm tắt thông báo bằng giọng nói](#dev-08) |
| `DEV-09` | [EcoDrive Coach - Phân tích hành trình & huấn luyện lái xe tiết kiệm trên edge](#dev-09) |
| `DEV-10` | [CrashGuard eCall - Phát hiện sự cố/tai nạn & tự động gọi cứu hộ từ thiết bị trên xe](#dev-10) |
| `DEV-11` | [HomeMind Hub - Trợ lý điều khiển nhà thông minh bằng ngôn ngữ tự nhiên chạy trên edge hub](#dev-11) |
| `DEV-12` | [GuardianCam Home - An ninh gia đình on-device: phát hiện người lạ & té ngã người già](#dev-12) |
| `DEV-13` | [EnergySense Home - Tối ưu năng lượng & tự động hóa theo thói quen trên edge hub](#dev-13) |
| `DEV-14` | [TrafficEye Edge - Camera giao thông đếm xe & phát hiện vi phạm ngay tại biên](#dev-14) |
| `DEV-15` | [SmartLight & ParkSense - Đèn chiếu sáng thích ứng & bãi đỗ thông minh trên edge](#dev-15) |
| `DEV-16` | [AirWatch Edge - Cảm biến môi trường & cảnh báo chất lượng không khí/ngập lụt thông minh](#dev-16) |
| `DEV-17` | [RetailVision Edge - Phân tích sự kiện tại biên cho camera bán lẻ (đếm người, hàng đợi, heatmap) ẩn danh](#dev-17) |
| `DEV-18` | [CamSearch NL - Tìm kiếm & tra soát sự kiện camera an ninh bằng ngôn ngữ tự nhiên trên edge](#dev-18) |
| `DEV-19` | [SmartCheck-in Kiosk - Kiosk tự check-in khách sạn: nhận diện khuôn mặt + OCR giấy tờ + cấp thẻ phòng](#dev-19) |
| `DEV-20` | [Concierge Kiosk - Trợ lý concierge/kiosk đa ngôn ngữ tại sảnh khách sạn chạy trên edge](#dev-20) |

---

## [DEV-01] Smart Cabin Copilot - Trợ lý giọng nói & đa phương thức trong xe chạy trên edge

### 📝 Mô tả đề tài
📍 Thực trạng: Xe hơi hiện đại có màn hình IVI và trợ lý giọng nói, nhưng phần lớn phụ thuộc cloud nên mất mạng trong hầm/vùng phủ sóng kém là 'câm', độ trễ cao gây khó chịu khi lái, và người dùng vẫn phải thao tác tay nhiều để chỉnh điều hòa/nhạc/dẫn đường.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent giọng nói + cảm ứng đa phương thức chạy trên cụm IVI/edge gateway, hiểu tiếng Việt tự nhiên, dùng tool điều khiển tính năng xe (điều hòa, ghế, nhạc, cửa sổ, dẫn đường), và tra cứu sổ tay hướng dẫn xe bằng RAG grounded để trả lời 'đèn báo này nghĩa là gì', 'cách bật chế độ eco'. Agent có memory ngữ cảnh chuyến đi và lập kế hoạch đa bước ('tìm quán cà phê gần, đặt điều hòa 24 độ rồi dẫn đường'); đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: AI chỉ HỖ TRỢ, mọi lệnh điều khiển vật lý (mở cửa, kính) cần xác nhận HITL và chỉ chạy mô phỏng; thiết kế rảnh tay/giọng nói, hạn chế thao tác màn hình khi xe đang chạy; câu trả lời sổ tay phải grounded chống bịa; phải chạy OFFLINE khi mất mạng với SLM lượng tử hóa; đo độ trễ từ nói đến phản hồi (ms).

### 🛠️ Tech Stack
• SLM lượng tử hóa chạy edge (Qwen2.5-3B/Phi-3-mini GGUF q4) qua llama.cpp/Ollama
• STT tiếng Việt PhoWhisper/Whisper.cpp
• TTS tiếng Việt (VietTTS/Piper)
• LangGraph điều phối agent + tool-use (function calling điều khiển CAN giả lập)
• RAG sổ tay xe với vector DB (Chroma/FAISS) + embedding đa ngôn ngữ
• MQTT mô phỏng bus tín hiệu xe
• backend FastAPI
• frontend React/Next.js mô phỏng màn hình IVI + dashboard kỹ sư
• mô phỏng Jetson Nano/Orin edge
• Docker deploy.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App mô phỏng IVI có đăng nhập ≥2 vai trò (tài xế & kỹ sư hệ thống), nhận lệnh giọng nói/text tiếng Việt, điều khiển tính năng xe mô phỏng qua tool-use, RAG trả lời từ sổ tay xe có trích nguồn, HITL xác nhận lệnh nhạy cảm, xử lý lỗi khi không hiểu lệnh, metric độ chính xác intent & tỷ lệ trả lời grounded.

Nâng cao:
• Chạy hoàn toàn offline với mô hình lượng tử hóa, đo & hiển thị độ trễ end-to-end (ms), kích thước mô hình, so sánh q4/q8
• multi-agent (agent điều khiển + agent tra cứu + agent an toàn)
• eval pipeline đánh giá intent/hallucination
• dashboard OTA giám sát nhiều xe & cập nhật mô hình
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-02] DriverGuard - Hệ thống giám sát tài xế (DMS) phát hiện buồn ngủ & mất tập trung on-device

### 📝 Mô tả đề tài
📍 Thực trạng: Buồn ngủ và mất tập trung (dùng điện thoại) là nguyên nhân hàng đầu gây tai nạn. Camera DMS trong xe hiện đại cần phát hiện realtime nhưng gửi ảnh khuôn mặt tài xế lên cloud vi phạm quyền riêng tư và không kịp thời gian thực. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent thị giác chạy 100% on-device phân tích luồng camera hồng ngoại/ RGB: phát hiện nhắm mắt kéo dài (PERCLOS), ngáp, gục đầu, quay đi khỏi đường, cầm điện thoại; agent lập luận mức rủi ro theo ngữ cảnh (tốc độ, thời gian lái liên tục) và đưa cảnh báo phân cấp (âm thanh, rung ghế, gợi ý nghỉ). Có memory theo dõi xu hướng mệt mỏi cả chuyến; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Xử lý on-device, KHÔNG lưu/gửi ảnh khuôn mặt ra ngoài (chỉ metadata trạng thái); chống báo động giả (false positive) vì cảnh báo sai gây mất tin tưởng & xao nhãng; realtime ≥15 FPS trên edge; AI chỉ cảnh báo không can thiệp lái; hoạt động cả ban đêm/đeo kính. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• CV model nhẹ lượng tử hóa: face/landmark detection (MediaPipe/BlazeFace), eye-state & head-pose (MobileNet/YOLOv8-nano) qua ONNX Runtime/TFLite
• luật PERCLOS + temporal smoothing
• SLM nhỏ cho lập luận ngữ cảnh mức cảnh báo (tùy chọn)
• mô phỏng cảm biến tốc độ qua CAN giả lập
• backend FastAPI
• frontend React dashboard giám sát + mô phỏng màn hình cảnh báo trong xe
• dữ liệu mẫu video DMS công khai
• mô phỏng Jetson
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App phát hiện buồn ngủ/mất tập trung trên video mẫu, phân cấp cảnh báo, đăng nhập ≥2 vai trò (tài xế & kỹ sư an toàn/fleet manager), HITL cho hiệu chỉnh ngưỡng, dashboard nhật ký sự kiện, metric độ chính xác/precision/recall & tỷ lệ false positive.

Nâng cao:
• Tối ưu mô hình lượng tử hóa đo FPS/độ trễ/kích thước trên edge, chạy offline
• hiệu chỉnh cá nhân hóa theo từng tài xế giảm false positive
• eval trên nhiều điều kiện ánh sáng
• giám sát đội xe nhiều thiết bị + OTA cập nhật ngưỡng/model
• guardrails chống lạm dụng dữ liệu khuôn mặt
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-03] CabinSentinel - Giám sát trong khoang xe: chống bỏ quên trẻ em/vật nuôi & phát hiện đồ để quên

### 📝 Mô tả đề tài
📍 Thực trạng: Mỗi năm có trẻ em/vật nuôi tử vong do bị bỏ quên trong xe nóng; hành khách thường để quên ví, điện thoại, laptop trên xe (đặc biệt xe dịch vụ/taxi điện). Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent thị giác + cảm biến trong khoang chạy edge phát hiện còn người/vật nuôi khi xe đã tắt máy và khóa, ước tính nhiệt độ khoang, kích hoạt chuỗi cảnh báo leo thang (còi, thông báo app chủ xe, gọi khẩn cấp); đồng thời sau mỗi chuyến quét phát hiện đồ vật để quên trên ghế/sàn và nhắc hành khách. Agent lập kế hoạch escalation và giữ memory trạng thái khoang; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: On-device, làm mờ/ẩn danh khuôn mặt, không lưu hình ảnh trẻ em; chống false positive (bóng, túi giống người) nhưng tuyệt đối không bỏ sót trẻ (ưu tiên recall cho phát hiện sự sống); mọi hành động vật lý (hạ kính, bật điều hòa) chỉ mô phỏng + HITL; realtime, hoạt động khi mất mạng.

### 🛠️ Tech Stack
• Occupancy/person detection YOLOv8-nano + pose, presence-of-life qua radar/vi chuyển động giả lập
• CV lượng tử hóa ONNX/TFLite
• object detection cho đồ để quên
• state machine + agent escalation (LangGraph) với tool gọi cảnh báo mô phỏng
• MQTT cảm biến nhiệt/cửa giả lập
• backend FastAPI
• frontend React (app chủ xe mô phỏng + dashboard)
• mô phỏng Raspberry Pi/Jetson
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App phát hiện người/vật nuôi còn trong xe & đồ để quên trên dữ liệu mô phỏng, chuỗi cảnh báo leo thang, đăng nhập ≥2 vai trò (chủ xe & quản trị dịch vụ), HITL, xử lý lỗi, metric recall/precision + độ trễ phát hiện.

Nâng cao:
• Tối ưu edge (FPS, kích thước model, offline), làm mờ danh tính
• kết hợp đa cảm biến (camera + nhiệt + radar giả lập) giảm bỏ sót
• eval kịch bản khó
• giám sát nhiều xe + OTA
• guardrails quyền riêng tư trẻ em
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-04] RoadWatch Copilot - Trợ lý cảnh báo hỗ trợ lái (ADAS) đa phương thức trên edge

### 📝 Mô tả đề tài
📍 Thực trạng: Camera trước xe có thể nhận diện vật cản, biển báo, làn đường, nhưng nhiều hệ thống chỉ cảnh báo cứng nhắc bằng tiếng bíp, không giải thích, và phụ thuộc cloud. Tài xế Việt gặp giao thông hỗn hợp (xe máy, người đi bộ) phức tạp. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent thị giác chạy edge phân tích camera trước: phát hiện xe/xe máy/người đi bộ cắt ngang, cảnh báo va chạm phía trước (FCW), lệch làn (LDW), nhận diện & đọc biển báo tốc độ, khoảng cách an toàn. Agent tổng hợp thành cảnh báo bằng giọng nói tiếng Việt tự nhiên có ngữ cảnh ('xe máy phía trước bên phải, giảm tốc'), ưu tiên theo mức nguy hiểm để không làm tài xế quá tải; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: AI CHỈ cảnh báo/hỗ trợ, TUYỆT ĐỐI không tự lái/phanh/đánh lái; realtime thấp trễ (an toàn-quan trọng); chống false positive gây 'cảnh báo mệt mỏi'; chạy offline; cảnh báo không gây xao nhãng (ưu tiên âm thanh); metric độ trễ & độ chính xác phát hiện. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• Object detection realtime YOLOv8/v10-nano + lane detection lượng tử hóa TensorRT/ONNX Runtime
• đọc biển báo (OCR nhẹ)
• logic ước lượng TTC (time-to-collision)
• TTS tiếng Việt Piper cho cảnh báo giọng nói
• luồng ưu tiên cảnh báo (rule + SLM tùy chọn)
• mô phỏng camera bằng video lái xe công khai (BDD/KITTI-style)
• backend FastAPI
• frontend React HUD mô phỏng + dashboard
• mô phỏng Jetson Orin
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App phân tích video lái xe phát hiện vật cản/làn/biển báo, cảnh báo phân cấp giọng nói tiếng Việt, đăng nhập ≥2 vai trò (tài xế & kỹ sư ADAS), HITL cấu hình ngưỡng, metric mAP/độ trễ, xử lý lỗi khung hình.

Nâng cao:
• Tối ưu TensorRT/lượng tử hóa đo FPS & độ trễ realtime, chạy offline
• hợp nhất nhiều cảnh báo thông minh giảm quá tải
• eval trên nhiều điều kiện
• giám sát fleet + OTA model
• guardrails chống hiểu nhầm là tự lái
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-05] AutoDoc - Trợ lý chẩn đoán xe & bảo dưỡng dự đoán từ dữ liệu OBD/CAN trên edge

### 📝 Mô tả đề tài
📍 Thực trạng: Đèn 'check engine' và mã lỗi OBD khó hiểu với người dùng phổ thông; hỏng hóc thường được phát hiện muộn gây tốn kém và nguy hiểm; dữ liệu CAN/OBD phong phú nhưng chưa được khai thác realtime trên xe. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent chạy edge đọc luồng dữ liệu OBD/CAN giả lập (tốc độ, vòng tua, nhiệt độ động cơ, điện áp pin, mã DTC), phát hiện bất thường & dự đoán hỏng hóc (bảo dưỡng dự đoán), giải thích mã lỗi cho tài xế bằng ngôn ngữ đơn giản qua RAG sổ tay kỹ thuật, và lập kế hoạch bảo dưỡng (gợi ý mức độ khẩn, đặt lịch xưởng). Có memory lịch sử vận hành xe; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Chẩn đoán grounded chống bịa (dựa sổ tay/DTC chuẩn); cảnh báo an toàn (lỗi phanh/lái) phải rõ mức nghiêm trọng & khuyến nghị dừng xe; xử lý on-device khi mất mạng; dữ liệu hành trình nhạy cảm cần ẩn danh; đo độ trễ phân tích & kích thước mô hình. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• Mô hình phát hiện bất thường chuỗi thời gian nhẹ (Isolation Forest/LSTM lượng tử hóa) chạy ONNX/TFLite
• SLM (Phi-3/Qwen) giải thích + RAG sổ tay DTC với vector DB
• agent lập kế hoạch bảo dưỡng (LangGraph, tool đặt lịch)
• mô phỏng OBD-II/CAN bus (python-can, dữ liệu mẫu)
• backend FastAPI
• frontend React dashboard sức khỏe xe + app tài xế
• mô phỏng edge Raspberry Pi
• MQTT
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App đọc dữ liệu OBD/CAN mô phỏng, phát hiện bất thường, giải thích mã lỗi grounded qua RAG, gợi ý bảo dưỡng, đăng nhập ≥2 vai trò (tài xế & kỹ thuật viên xưởng), HITL duyệt khuyến nghị, metric độ chính xác phát hiện & tỷ lệ grounded.

Nâng cao:
• Dự đoán hỏng hóc trước (RUL/predictive), tối ưu mô hình edge đo độ trễ/kích thước/offline
• multi-agent chẩn đoán
• eval trên bộ dữ liệu lỗi
• giám sát nhiều xe + OTA ngưỡng
• guardrails cảnh báo an toàn phanh/lái
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-06] EV RangeMind - Trợ lý sạc & lập lộ trình thông minh cho xe điện chạy on-device

### 📝 Mô tả đề tài
📍 Thực trạng: Tài xế xe điện lo 'range anxiety' - sợ hết pin giữa đường; ứng dụng lập lộ trình sạc thường cần mạng liên tục, không tính chính xác tiêu hao theo địa hình/điều hòa/phong cách lái. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent chạy edge ước tính quãng đường còn lại thực tế dựa trên trạng thái pin (SoC), địa hình, tải, điều hòa, phong cách lái; lập kế hoạch lộ trình có điểm sạc tối ưu (agent planning: cân nhắc trạm sạc công cộng, thời gian sạc, độ dài), và trả lời câu hỏi tự nhiên về sạc/tầm hoạt động. Có memory thói quen lái & hồ sơ tiêu hao; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Chạy offline khi mất mạng (bản đồ/trạm sạc cache on-device); ước tính grounded không lạc quan quá mức gây kẹt đường; dữ liệu vị trí/hành trình nhạy cảm xử lý on-device; đề xuất chỉ tư vấn, tài xế quyết định (HITL); đo độ trễ tính toán lộ trình. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• Mô hình ước lượng tiêu hao năng lượng (regression nhẹ/GBDT) ONNX
• thuật toán lập lộ trình (A*/graph có ràng buộc sạc)
• SLM cho hỏi-đáp tự nhiên + tool truy vấn trạm sạc
• dữ liệu địa hình/trạm sạc cache offline
• mô phỏng BMS/telemetry xe điện
• backend FastAPI
• frontend React bản đồ lộ trình + dashboard
• mô phỏng edge Jetson
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App ước tính tầm hoạt động & gợi ý lộ trình sạc trên dữ liệu mô phỏng, hỏi-đáp tự nhiên, đăng nhập ≥2 vai trò (tài xế & quản trị mạng lưới sạc), HITL chọn phương án, metric sai số ước tính (MAE km) & chất lượng lộ trình.

Nâng cao:
• Chạy offline với bản đồ/trạm cache, tối ưu mô hình edge đo độ trễ/kích thước
• cá nhân hóa tiêu hao theo lịch sử lái
• multi-agent (ước lượng + lập lộ trình + tư vấn)
• eval độ chính xác
• giám sát fleet + OTA dữ liệu trạm sạc
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-07] MyCabin - Cá nhân hóa khoang lái theo hồ sơ & nhận diện tài xế trên edge

### 📝 Mô tả đề tài
📍 Thực trạng: Xe gia đình/dịch vụ nhiều người dùng chung; mỗi lần lên xe phải chỉnh lại ghế, gương, điều hòa, nhạc, bản đồ - bất tiện và mất tập trung. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent chạy edge nhận diện tài xế qua khuôn mặt/giọng nói (on-device), tự động khôi phục hồ sơ cá nhân hóa (vị trí ghế/gương, nhiệt độ điều hòa, playlist, tuyến hay đi, ngôn ngữ trợ lý), và học dần sở thích theo ngữ cảnh (thời tiết, giờ, người ngồi cạnh) để đề xuất chủ động. Agent lập kế hoạch áp dụng cấu hình và giữ memory hồ sơ đa người dùng; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Nhận diện khuôn mặt/giọng nói xử lý on-device, template sinh trắc mã hóa, không gửi cloud; mọi điều chỉnh cơ khí (ghế/gương) mô phỏng + HITL xác nhận; chống nhận nhầm người; chạy offline; đo độ trễ nhận diện & áp cấu hình. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• Face recognition nhẹ (MobileFaceNet/ArcFace lượng tử hóa) + speaker verification (ECAPA-TDNN nhỏ) ONNX/TFLite
• lưu trữ template sinh trắc mã hóa on-device
• recommender học sở thích (bandit/collaborative nhẹ)
• agent áp cấu hình (LangGraph, tool điều khiển ghế/điều hòa giả lập qua CAN)
• backend FastAPI
• frontend React (màn hình cá nhân hóa mô phỏng + dashboard quản trị hồ sơ)
• mô phỏng Jetson
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App nhận diện tài xế & khôi phục hồ sơ trên dữ liệu mô phỏng, đề xuất cấu hình, đăng nhập ≥2 vai trò (người dùng & quản trị hệ thống), HITL xác nhận điều chỉnh, metric độ chính xác nhận diện & FAR/FRR.

Nâng cao:
• Tối ưu mô hình sinh trắc edge đo độ trễ/kích thước/offline, mã hóa template
• học sở thích chủ động theo ngữ cảnh
• chống spoofing/liveness
• eval nhận diện
• giám sát nhiều xe + đồng bộ hồ sơ có bảo mật
• guardrails quyền riêng tư sinh trắc
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-08] HandsFree Messenger - Trợ lý an toàn khi lái: đọc/soạn tin & tóm tắt thông báo bằng giọng nói

### 📝 Mô tả đề tài
📍 Thực trạng: Tài xế thường liếc điện thoại đọc/trả lời tin nhắn khi lái - cực kỳ nguy hiểm và vi phạm luật; các trợ lý đọc tin hiện có máy móc, không tóm tắt, phụ thuộc cloud. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent giọng nói chạy edge tích hợp với luồng thông báo (tin nhắn, cuộc gọi, lịch, cảnh báo) mô phỏng: đọc to, tóm tắt thông minh các tin dài, soạn & gửi trả lời bằng giọng nói tiếng Việt, lọc ưu tiên (chặn spam, chỉ đọc tin quan trọng khi đang lái tốc độ cao). Agent lập kế hoạch hội thoại nhiều lượt và có memory ngữ cảnh liên lạc; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Thiết kế 100% rảnh tay/giọng nói, KHÔNG hiển thị nội dung dài trên màn hình khi xe chạy (chống xao nhãng); dữ liệu tin nhắn riêng tư xử lý on-device không gửi cloud; xác nhận HITL trước khi gửi tin; chạy offline; đo độ trễ STT→hiểu→TTS. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• STT tiếng Việt PhoWhisper/Whisper.cpp
• TTS Piper/VietTTS
• SLM (Qwen2.5-3B q4) cho tóm tắt & soạn tin + tool gửi tin giả lập
• phân loại ưu tiên thông báo (classifier nhẹ)
• agent hội thoại đa lượt (LangGraph)
• mô phỏng luồng thông báo & tín hiệu tốc độ
• backend FastAPI
• frontend React mô phỏng IVI giọng nói + dashboard
• mô phỏng edge
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App đọc/tóm tắt/soạn tin bằng giọng nói tiếng Việt trên dữ liệu mô phỏng, lọc ưu tiên, đăng nhập ≥2 vai trò (tài xế & quản trị), HITL xác nhận gửi, metric chất lượng tóm tắt & độ chính xác STT (WER).

Nâng cao:
• Chạy offline với SLM lượng tử hóa đo độ trễ end-to-end/kích thước
• chế độ 'đang lái' hạn chế tương tác theo tốc độ
• multi-agent (đọc + tóm tắt + soạn)
• eval tóm tắt/WER
• giám sát fleet + OTA
• guardrails chống xao nhãng & bảo mật tin nhắn
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-09] EcoDrive Coach - Phân tích hành trình & huấn luyện lái xe tiết kiệm trên edge

### 📝 Mô tả đề tài
📍 Thực trạng: Phong cách lái (tăng/phanh gấp, chạy tốc độ cao) ảnh hưởng lớn đến tiêu hao năng lượng, tuổi thọ pin/phanh và an toàn, nhưng tài xế ít nhận phản hồi cụ thể; dữ liệu telemetry chưa được biến thành lời khuyên hữu ích. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent chạy edge phân tích telemetry hành trình (tốc độ, gia tốc, phanh, tiêu hao) phát hiện thói quen chưa tối ưu, chấm điểm eco/an toàn từng chuyến, và huấn luyện bằng phản hồi ngôn ngữ tự nhiên tiếng Việt (gợi ý cụ thể, kịp thời khi an toàn). Agent lập kế hoạch coaching cá nhân hóa dài hạn và giữ memory tiến bộ tài xế; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Phản hồi realtime chỉ dạng nhắc nhẹ không gây xao nhãng, khuyến nghị chi tiết để sau chuyến; dữ liệu hành trình/vị trí nhạy cảm xử lý on-device ẩn danh; chấm điểm grounded công bằng; chạy offline; đo độ trễ phân tích & kích thước mô hình. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• Phân tích chuỗi thời gian & phát hiện sự kiện lái (rule + mô hình nhẹ) ONNX/TFLite
• SLM sinh phản hồi coaching tiếng Việt + tool chấm điểm
• recommender mục tiêu cải thiện
• mô phỏng telemetry hành trình (dữ liệu GPS/gia tốc mẫu)
• backend FastAPI
• frontend React dashboard hành trình + app coaching
• mô phỏng edge Raspberry Pi/Jetson
• MQTT
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App phân tích chuyến & chấm điểm eco/an toàn trên telemetry mô phỏng, phản hồi ngôn ngữ tự nhiên, đăng nhập ≥2 vai trò (tài xế & quản lý đội xe), HITL điều chỉnh mục tiêu, metric độ chính xác phát hiện sự kiện & tính hữu ích phản hồi.

Nâng cao:
• Tối ưu mô hình edge đo độ trễ/kích thước/offline
• coaching cá nhân hóa theo dõi tiến bộ
• multi-agent (phân tích + coaching)
• eval chất lượng lời khuyên
• leaderboard & giám sát đội xe + OTA
• guardrails chống xao nhãng realtime
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-10] CrashGuard eCall - Phát hiện sự cố/tai nạn & tự động gọi cứu hộ từ thiết bị trên xe

### 📝 Mô tả đề tài
📍 Thực trạng: Sau tai nạn, nạn nhân có thể bất tỉnh không gọi được cứu hộ; thời gian vàng cấp cứu bị bỏ lỡ; nhiều xe chưa có hệ thống eCall tự động phù hợp Việt Nam. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent chạy edge hợp nhất cảm biến (gia tốc kế/va chạm, camera trong khoang, âm thanh, airbag giả lập) phát hiện va chạm, phân loại mức nghiêm trọng, đánh giá tình trạng người trong xe, và thực thi chuỗi eCall: xác nhận với tài xế (nếu tỉnh), rồi tự động gọi cứu hộ với vị trí & thông tin xe/số người nếu không phản hồi. Agent lập kế hoạch escalation và giữ memory ngữ cảnh sự cố; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Chống false positive (ổ gà, phanh gấp không phải tai nạn) nhưng không bỏ sót tai nạn thật (ưu tiên recall); phải hoạt động OFFLINE/độ trễ cực thấp (cứu người); có cửa sổ HITL để tài xế hủy báo động giả trước khi gọi; dữ liệu vị trí/khoang nhạy cảm chỉ gửi khi khẩn cấp có mã hóa; mọi hành động chỉ mô phỏng.

### 🛠️ Tech Stack
• Phát hiện va chạm đa cảm biến (gia tốc kế + ngưỡng + mô hình nhẹ) ONNX/TFLite
• CV đánh giá khoang (person/pose) YOLO-nano
• phân loại âm thanh sự cố
• agent escalation eCall (state machine + LangGraph, tool gọi cứu hộ giả lập)
• mô phỏng IMU/airbag/GPS
• backend FastAPI
• frontend React dashboard trung tâm cứu hộ + màn hình xe mô phỏng
• mô phỏng edge
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App phát hiện & phân loại va chạm trên dữ liệu mô phỏng, chuỗi eCall có cửa sổ hủy, đăng nhập ≥2 vai trò (tài xế & tổng đài cứu hộ), HITL hủy báo động, xử lý lỗi, metric recall/precision & tỷ lệ false positive.

Nâng cao:
• Chạy offline độ trễ cực thấp đo ms/kích thước model
• hợp nhất đa cảm biến giảm false positive không bỏ sót
• đánh giá tình trạng nạn nhân
• eval kịch bản va chạm
• giám sát fleet + OTA ngưỡng
• guardrails an toàn & mã hóa dữ liệu khẩn cấp
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-11] HomeMind Hub - Trợ lý điều khiển nhà thông minh bằng ngôn ngữ tự nhiên chạy trên edge hub

### 📝 Mô tả đề tài
📍 Thực trạng: Nhà thông minh tại khu đô thị có nhiều thiết bị (đèn, điều hòa, rèm, khóa, camera) nhưng điều khiển rời rạc qua app; trợ lý giọng nói phụ thuộc cloud gây trễ, lo ngại quyền riêng tư khi giọng nói gửi ra ngoài, và 'chết' khi mất mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent chạy trên hub edge tại nhà, hiểu lệnh tiếng Việt tự nhiên & đa bước ('tối nay có khách, bật đèn phòng khách ấm, mở nhạc nhẹ, đặt điều hòa 26 độ'), điều khiển thiết bị qua tool-use, tạo & gợi ý kịch bản (scene/automation) theo ngữ cảnh, giải quyết lệnh mơ hồ bằng hỏi lại. Agent có memory thói quen & trạng thái nhà; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Xử lý giọng nói & suy luận ON-DEVICE trên hub, không gửi cloud (quyền riêng tư gia đình); chạy OFFLINE khi mất mạng; hành động nhạy cảm (mở khóa cửa, tắt an ninh) cần HITL xác nhận; chống hiểu nhầm lệnh; tối ưu bộ nhớ/điện năng hub; đo độ trễ lệnh→hành động. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• SLM lượng tử hóa (Qwen2.5-3B/Phi-3 q4) llama.cpp trên hub
• STT tiếng Việt Whisper.cpp/PhoWhisper + TTS Piper
• agent tool-use & lập kế hoạch (LangGraph, function calling)
• MQTT/Matter giả lập điều khiển thiết bị
• RAG hướng dẫn thiết bị
• backend FastAPI
• frontend React dashboard nhà + mô phỏng loa/hub
• mô phỏng Raspberry Pi/Jetson hub
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App/hub mô phỏng nhận lệnh tiếng Việt điều khiển thiết bị giả lập, tạo kịch bản, đăng nhập ≥2 vai trò (thành viên gia đình & quản trị nhà), HITL cho lệnh nhạy cảm, xử lý lệnh mơ hồ, metric độ chính xác intent & tỷ lệ hoàn thành tác vụ.

Nâng cao:
• Chạy hoàn toàn offline với SLM lượng tử hóa đo độ trễ/kích thước/RAM
• gợi ý automation chủ động theo thói quen
• multi-agent
• eval intent/task
• giám sát nhiều hub + OTA
• guardrails an ninh (khóa cửa) & quyền riêng tư giọng nói
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-12] GuardianCam Home - An ninh gia đình on-device: phát hiện người lạ & té ngã người già

### 📝 Mô tả đề tài
📍 Thực trạng: Camera an ninh gia đình gửi video lên cloud gây lo ngại quyền riêng tư và tốn băng thông; báo động chuyển động thô sinh quá nhiều thông báo rác; người già sống một mình có nguy cơ té ngã không ai biết. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent thị giác chạy on-device (camera/hub của khu đô thị) phân biệt người quen/người lạ, phát hiện xâm nhập ngoài giờ, và phát hiện té ngã/bất động của người già để cảnh báo người thân; agent lập luận ngữ cảnh (giờ giấc, khu vực, thành viên) để giảm báo động giả và mô tả sự kiện bằng ngôn ngữ tự nhiên ('có người lạ ở cửa sau lúc 2h sáng'). Có memory lịch trình & khuôn mặt thành viên; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Xử lý ON-DEVICE, làm mờ/ẩn danh khuôn mặt người ngoài, không lưu/gửi video thô ra cloud (quyền riêng tư gia đình); chống false positive (thú cưng, bóng) nhưng không bỏ sót té ngã (ưu tiên recall an toàn); realtime; chạy offline; đo FPS/độ trễ/kích thước model. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• Person/face detection + recognition nhẹ (YOLOv8-nano, MobileFaceNet) ONNX/TFLite
• fall detection qua pose estimation (MoveNet/BlazePose) + temporal logic
• SLM mô tả sự kiện tiếng Việt (tùy chọn) + agent cảnh báo
• mô phỏng camera bằng video mẫu
• backend FastAPI
• frontend React app gia đình + dashboard
• mô phỏng edge camera/Jetson
• MQTT
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App phát hiện người lạ & té ngã trên video mô phỏng, cảnh báo có mô tả, đăng nhập ≥2 vai trò (thành viên & quản trị/người chăm sóc), HITL xác nhận báo động, làm mờ danh tính, metric precision/recall & tỷ lệ false positive.

Nâng cao:
• Tối ưu edge đo FPS/độ trễ/kích thước/offline
• nhận diện thành viên giảm báo động giả
• lập luận ngữ cảnh giờ giấc
• eval fall/intrusion
• giám sát nhiều camera + OTA
• guardrails quyền riêng tư & lưu video mã hóa cục bộ
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-13] EnergySense Home - Tối ưu năng lượng & tự động hóa theo thói quen trên edge hub

### 📝 Mô tả đề tài
📍 Thực trạng: Hộ gia đình lãng phí điện do thiết bị chạy không cần thiết (đèn/điều hòa khi không có người); hóa đơn cao mà người dùng khó biết tối ưu ở đâu; automation cứng nhắc không thích ứng thói quen. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent chạy trên hub edge học thói quen sinh hoạt & mẫu tiêu thụ điện từ cảm biến (hiện diện, nhiệt độ, công suất thiết bị), đề xuất & tự động điều chỉnh (tắt thiết bị thừa, lịch điều hòa tối ưu, tận dụng giờ điện rẻ), giải thích tiết kiệm bằng ngôn ngữ tự nhiên. Agent lập kế hoạch tối ưu đa mục tiêu (tiện nghi vs tiết kiệm) và giữ memory thói quen; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Tối ưu không hy sinh tiện nghi/an toàn quá mức; hành động điều khiển thiết bị cần HITL/chế độ tự động có giới hạn; dữ liệu sinh hoạt riêng tư xử lý on-device; chạy offline; đo độ trễ & kích thước mô hình; đề xuất grounded trên dữ liệu thực đo. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• Mô hình dự báo tải & phát hiện lãng phí (time-series nhẹ, GBDT/LSTM lượng tử hóa) ONNX/TFLite
• phát hiện hiện diện
• agent tối ưu đa mục tiêu + tool điều khiển (LangGraph)
• SLM giải thích tiếng Việt
• mô phỏng smart meter & cảm biến (MQTT, dữ liệu mẫu)
• backend FastAPI
• frontend React dashboard năng lượng + app
• mô phỏng edge hub Raspberry Pi
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App phân tích tiêu thụ & đề xuất tối ưu trên dữ liệu mô phỏng, tự động hóa theo thói quen, đăng nhập ≥2 vai trò (thành viên & quản trị nhà), HITL duyệt hành động, metric tiết kiệm ước tính & độ chính xác dự báo tải.

Nâng cao:
• Tối ưu mô hình edge đo độ trễ/kích thước/offline
• học thói quen thích ứng & tận dụng biểu giá điện
• multi-agent (dự báo + tối ưu + giải thích)
• eval dự báo
• giám sát nhiều hộ + OTA
• guardrails tiện nghi/an toàn
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-14] TrafficEye Edge - Camera giao thông đếm xe & phát hiện vi phạm ngay tại biên

### 📝 Mô tả đề tài
📍 Thực trạng: Camera giao thông smart city truyền toàn bộ video về trung tâm gây quá tải băng thông & xử lý chậm; đếm lưu lượng và phát hiện vi phạm (vượt đèn đỏ, đi sai làn, dừng đỗ sai) thủ công không kịp thời. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent thị giác chạy on-edge tại cột camera đường phố: đếm & phân loại phương tiện theo làn/hướng, ước tính mật độ/ùn tắc, phát hiện vi phạm (vượt đèn đỏ, sai làn, đi ngược chiều) và chỉ gửi metadata/sự kiện + ảnh bằng chứng đã làm mờ về trung tâm. Agent lập luận ngữ cảnh (pha đèn, giờ cao điểm) giảm cảnh báo sai và tổng hợp báo cáo; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Xử lý ON-EDGE chỉ gửi metadata (băng thông/quyền riêng tư), LÀM MỜ biển số/khuôn mặt trừ khi vi phạm cần bằng chứng có phân quyền; chống false positive vi phạm (hậu quả pháp lý) - ưu tiên precision cao; realtime ≥15 FPS; chạy offline khi mất kết nối trung tâm; đo FPS/độ trễ/kích thước model.

### 🛠️ Tech Stack
• Vehicle detection + tracking (YOLOv8-nano + ByteTrack/DeepSORT) lượng tử hóa TensorRT/ONNX
• ANPR/OCR biển số nhẹ (dùng khi vi phạm)
• logic pha đèn & vạch làn
• agent tổng hợp + tool báo cáo
• mô phỏng camera bằng video giao thông mẫu
• backend FastAPI
• frontend React dashboard trung tâm giao thông + bản đồ
• mô phỏng Jetson edge
• MQTT
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App đếm/phân loại xe & phát hiện vi phạm trên video mô phỏng, gửi sự kiện+bằng chứng làm mờ, đăng nhập ≥2 vai trò (người vận hành & quản trị/CSGT), HITL duyệt vi phạm trước khi ghi nhận, metric mAP/độ chính xác đếm & precision vi phạm.

Nâng cao:
• Tối ưu edge đo FPS/độ trễ/kích thước/offline
• ước tính ùn tắc & gợi ý điều phối
• multi-camera phối hợp
• eval đếm/vi phạm
• giám sát nhiều camera + OTA
• guardrails làm mờ danh tính & phân quyền truy cập bằng chứng
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-15] SmartLight & ParkSense - Đèn chiếu sáng thích ứng & bãi đỗ thông minh trên edge

### 📝 Mô tả đề tài
📍 Thực trạng: Đèn đường thành phố chạy lịch cứng gây lãng phí điện khi không có người/xe; tìm chỗ đỗ xe ở khu đô thị/thành phố tốn thời gian, gây ùn tắc & khí thải. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent chạy trên gateway edge khu phố điều khiển chiếu sáng thích ứng (giảm/tăng sáng theo hiện diện người/xe, thời tiết, giờ) tiết kiệm điện, đồng thời quản lý bãi đỗ thông minh: phát hiện chỗ trống qua camera/cảm biến, dẫn tài xế đến chỗ gần nhất, dự báo lấp đầy. Agent lập kế hoạch tối ưu năng lượng-an toàn & điều phối chỗ đỗ, giữ memory mẫu lưu lượng; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Chiếu sáng đảm bảo an toàn tối thiểu (không tắt hẳn nơi có người); camera bãi đỗ làm mờ biển số/khuôn mặt xử lý on-edge; điều khiển thiết bị có HITL/giới hạn tự động; chạy offline khi mất kết nối; đo độ trễ phát hiện & kích thước model; tiết kiệm điện đo được. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• Presence/vehicle detection nhẹ (YOLOv8-nano) ONNX/TFLite
• nhận diện ô đỗ trống (CV + cảm biến giả lập)
• dự báo lấp đầy (time-series nhẹ)
• agent điều khiển đèn & điều phối đỗ (LangGraph + MQTT)
• mô phỏng đèn/cảm biến/camera bãi
• backend FastAPI
• frontend React dashboard thành phố + app tìm chỗ đỗ
• mô phỏng Jetson/RPi gateway
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App điều khiển chiếu sáng thích ứng & phát hiện/dẫn đường chỗ đỗ trên dữ liệu mô phỏng, đăng nhập ≥2 vai trò (người dùng/tài xế & quản trị đô thị), HITL, metric tiết kiệm điện & độ chính xác phát hiện chỗ trống/hiện diện.

Nâng cao:
• Tối ưu edge đo độ trễ/kích thước/offline
• dự báo lấp đầy & điều phối động
• multi-gateway phối hợp khu vực
• eval phát hiện
• giám sát nhiều thiết bị + OTA
• guardrails an toàn chiếu sáng & quyền riêng tư camera bãi
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-16] AirWatch Edge - Cảm biến môi trường & cảnh báo chất lượng không khí/ngập lụt thông minh

### 📝 Mô tả đề tài
📍 Thực trạng: Ô nhiễm không khí, tiếng ồn, và ngập lụt đô thị ảnh hưởng sức khỏe & sinh hoạt; dữ liệu cảm biến rải rác, cảnh báo chậm và thiếu diễn giải hữu ích cho người dân. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent chạy trên node cảm biến/edge gateway thu thập dữ liệu môi trường (PM2.5, khí, nhiệt-ẩm, tiếng ồn, mực nước) mô phỏng, phát hiện bất thường & dự báo ngắn hạn (đỉnh ô nhiễm, nguy cơ ngập), sinh cảnh báo phân cấp và khuyến nghị hành động bằng ngôn ngữ tự nhiên tiếng Việt cho người dân/chính quyền ('AQI xấu 2 giờ tới, hạn chế ra ngoài'). Agent lập kế hoạch cảnh báo theo khu vực & giữ memory xu hướng; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Xử lý on-edge giảm phụ thuộc trung tâm, chạy offline; cảnh báo grounded trên dữ liệu đo chống thổi phồng/bỏ sót; hiệu chỉnh cảm biến & xử lý dữ liệu lỗi/nhiễu; khuyến nghị chỉ tư vấn, quyết định khẩn cấp qua HITL cơ quan; đo độ trễ & kích thước mô hình dự báo. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• Phát hiện bất thường & dự báo chuỗi thời gian nhẹ (Prophet/LSTM/GBDT lượng tử hóa) ONNX/TFLite
• hiệu chỉnh/lọc nhiễu cảm biến
• SLM sinh cảnh báo & khuyến nghị tiếng Việt + tool phát cảnh báo
• mô phỏng mạng cảm biến IoT (MQTT, dữ liệu môi trường mẫu)
• backend FastAPI
• frontend React dashboard bản đồ môi trường + app dân cư
• mô phỏng edge node RPi
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App thu thập & phân tích dữ liệu môi trường mô phỏng, phát hiện bất thường & cảnh báo có khuyến nghị, đăng nhập ≥2 vai trò (người dân & quản trị/chính quyền), HITL duyệt cảnh báo diện rộng, metric độ chính xác dự báo (MAE) & phát hiện.

Nâng cao:
• Tối ưu mô hình edge đo độ trễ/kích thước/offline
• dự báo ngắn hạn nhiều chỉ số & bản đồ nhiệt
• multi-node hợp nhất khu vực
• eval dự báo/cảnh báo
• giám sát mạng cảm biến + OTA
• guardrails chống báo động giả & xử lý cảm biến hỏng
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-17] RetailVision Edge - Phân tích sự kiện tại biên cho camera bán lẻ (đếm người, hàng đợi, heatmap) ẩn danh

### 📝 Mô tả đề tài
📍 Thực trạng: Cửa hàng/TTTM (trung tâm thương mại) muốn hiểu lưu lượng khách, điểm nóng, thời gian chờ quầy để tối ưu vận hành, nhưng gửi video khách hàng lên cloud vi phạm quyền riêng tư & tốn kém; đếm thủ công không chính xác. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent thị giác chạy on-edge trên camera bán lẻ: đếm người vào/ra, ước tính hàng đợi & thời gian chờ tại quầy, tạo heatmap khu vực đông, phát hiện sự kiện (quầy quá tải, khu vực trống nhân viên) và cảnh báo quản lý; chỉ xuất metadata/thống kê ẩn danh. Agent tổng hợp báo cáo & gợi ý điều phối nhân sự, giữ memory mẫu lưu lượng theo giờ/ngày; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Xử lý ON-EDGE chỉ gửi số liệu ẩn danh, LÀM MỜ/không lưu khuôn mặt (quyền riêng tư khách hàng, tuân thủ bảo vệ dữ liệu); không nhận dạng cá nhân; realtime; chống đếm trùng/sai (độ chính xác đo được); chạy offline; đo FPS/độ trễ/kích thước model. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• Person detection + tracking (YOLOv8-nano + ByteTrack) lượng tử hóa ONNX/TFLite
• line-crossing counting & zone heatmap
• ước tính hàng đợi (density/queue logic)
• agent tổng hợp báo cáo + tool cảnh báo (LangGraph)
• mô phỏng camera bằng video bán lẻ mẫu
• backend FastAPI
• frontend React dashboard analytics + heatmap
• mô phỏng Jetson/camera edge
• MQTT
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App đếm người/hàng đợi & heatmap trên video mô phỏng, cảnh báo sự kiện vận hành, đăng nhập ≥2 vai trò (quản lý cửa hàng & quản trị hệ thống), HITL, làm mờ danh tính, metric độ chính xác đếm (MAE) & precision sự kiện.

Nâng cao:
• Tối ưu edge đo FPS/độ trễ/kích thước/offline
• phân tích theo giờ & gợi ý điều phối nhân sự
• multi-camera hợp nhất mặt bằng
• eval đếm/queue
• giám sát nhiều cửa hàng + OTA
• guardrails ẩn danh & tuân thủ bảo vệ dữ liệu khách
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-18] CamSearch NL - Tìm kiếm & tra soát sự kiện camera an ninh bằng ngôn ngữ tự nhiên trên edge

### 📝 Mô tả đề tài
📍 Thực trạng: Rà soát hàng giờ video an ninh (Trung tâm Giám sát An ninh mạng (SOC) của doanh nghiệp/khu đô thị) để tìm 'người mặc áo đỏ mang balo lúc chiều' cực kỳ tốn thời gian; hệ thống hiện tại chỉ tua tay theo thời gian. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent trên edge/gateway lập chỉ mục ngữ nghĩa các sự kiện từ camera (mô tả người/vật/hành động, thuộc tính như màu áo, mang vật, phương tiện) và cho phép tìm kiếm bằng ngôn ngữ tự nhiên tiếng Việt ('tìm xe máy màu đen đi vào cổng sau sau 18h'), trả về đoạn clip khớp có timeline. Agent hiểu truy vấn, lập kế hoạch tìm kiếm đa điều kiện & tóm tắt kết quả. Grounded trên bằng chứng thực; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Trích xuất đặc trưng & lập chỉ mục ON-EDGE, LÀM MỜ khuôn mặt trong kết quả trừ khi có phân quyền điều tra; không nhận dạng danh tính tùy tiện; kết quả grounded chống bịa (chỉ trả sự kiện thực có timestamp/clip); chạy offline; đo độ trễ truy vấn & kích thước index. Xử lý dữ liệu nhạy cảm (camera/giọng nói/sinh trắc học) ngay trên thiết bị biên (on-device privacy); tích hợp lớp kiểm tra an toàn xác định bằng code trước mọi lệnh điều khiển và báo cáo đầy đủ benchmark phần cứng (RAM/VRAM, p95 latency, Q4 vs Q8 accuracy).

### 🛠️ Tech Stack
• VLM/open-vocabulary detection nhẹ (YOLO-World/GroundingDINO nhỏ, CLIP) lượng tử hóa ONNX
• trích thuộc tính người/xe
• vector DB sự kiện (FAISS/Chroma) + text-to-embedding truy vấn
• agent hiểu truy vấn & lập kế hoạch tìm kiếm (LangGraph) + SLM tóm tắt
• mô phỏng camera bằng video mẫu
• backend FastAPI
• frontend React giao diện tìm kiếm + timeline clip
• mô phỏng Jetson edge
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App lập chỉ mục sự kiện & tìm kiếm ngôn ngữ tự nhiên trên video mô phỏng, trả clip khớp có timeline, đăng nhập ≥2 vai trò (nhân viên an ninh & quản trị/điều tra), HITL duyệt truy cập nhạy cảm, làm mờ danh tính, metric recall@k/precision truy vấn.

Nâng cao:
• Tối ưu edge đo độ trễ truy vấn/kích thước index/offline
• truy vấn đa điều kiện & đa camera
• agent tóm tắt & tái hiện hành trình đối tượng
• eval retrieval
• giám sát nhiều camera + OTA
• guardrails phân quyền & chống lạm dụng nhận dạng
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-19] SmartCheck-in Kiosk - Kiosk tự check-in khách sạn: nhận diện khuôn mặt + OCR giấy tờ + cấp thẻ phòng

### 📝 Mô tả đề tài
📍 Thực trạng: Check-in khách sạn hệ thống khách sạn/khu nghỉ dưỡng giờ cao điểm xếp hàng dài, nhân viên nhập liệu thủ công từ CCCD/hộ chiếu dễ sai, đối chiếu danh tính thủ công chậm. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent chạy trên kiosk edge tự động hóa check-in: quét & OCR giấy tờ (CCCD/passport) trích thông tin, chụp ảnh khách đối chiếu khuôn mặt với ảnh giấy tờ (face match + liveness chống giả mạo), xác thực đặt phòng, xử lý ngoại lệ (giấy tờ mờ, không khớp) chuyển lễ tân, và cấp thẻ phòng/mã. Agent lập kế hoạch quy trình đa bước & trợ giúp khách bằng hội thoại. Giữ memory phiên check-in; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Dữ liệu giấy tờ tùy thân CỰC KỲ nhạy cảm - xử lý ON-DEVICE, mã hóa, KHÔNG lưu ảnh giấy tờ quá thời gian cần thiết, tuân thủ bảo vệ dữ liệu; liveness chống giả mạo (ảnh/mask); trường hợp không khớp/nghi ngờ BẮT BUỘC HITL lễ tân (không tự cấp phòng); chống nhận nhầm; đo độ trễ & độ chính xác OCR/face match.

### 🛠️ Tech Stack
• OCR CCCD/passport (PaddleOCR/VietOCR + MRZ parser) ONNX
• face detection + matching (ArcFace/MobileFaceNet lượng tử hóa) + liveness (anti-spoofing nhẹ)
• agent quy trình check-in (LangGraph, tool xác thực đặt phòng/cấp thẻ giả lập)
• SLM trợ giúp hội thoại đa ngôn ngữ
• mã hóa dữ liệu on-device
• backend FastAPI
• frontend React giao diện kiosk + dashboard lễ tân
• mô phỏng Jetson kiosk
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App kiosk OCR giấy tờ + face match + cấp thẻ trên dữ liệu mẫu, đăng nhập ≥2 vai trò (khách & lễ tân/quản trị), HITL cho ca không khớp, xử lý lỗi giấy tờ mờ, mã hóa dữ liệu, metric độ chính xác OCR & FAR/FRR face match.

Nâng cao:
• Tối ưu mô hình edge đo độ trễ/kích thước/offline
• liveness chống giả mạo
• xử lý đa loại giấy tờ & đa ngôn ngữ
• eval OCR/face/liveness
• giám sát nhiều kiosk + OTA
• guardrails bảo vệ dữ liệu định danh & xóa dữ liệu sau phiên
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---

## [DEV-20] Concierge Kiosk - Trợ lý concierge/kiosk đa ngôn ngữ tại sảnh khách sạn chạy trên edge

### 📝 Mô tả đề tài
📍 Thực trạng: Khách quốc tế tại hệ thống khách sạn/khu nghỉ dưỡng cần thông tin (dịch vụ, giờ mở, nhà hàng, tour, hỏi đường trong khu nghỉ) nhưng nhân viên không phải lúc nào cũng rảnh & đa ngôn ngữ; thông tin phân tán. Trong vận hành thực tế trên thiết bị biên (khoang lái phương tiện, camera/box thông minh, kiosk tự phục vụ), hệ thống bị giới hạn nghiêm ngặt về bộ nhớ (RAM/VRAM), chịu nhiễu môi trường lớn (tiếng ồn, ngược sáng) và phải đảm bảo an toàn ngay cả khi mất kết nối mạng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để agent kiosk/robot sảnh chạy edge trả lời câu hỏi khách bằng nhiều ngôn ngữ (Việt/Anh/Trung/Hàn) qua giọng nói & màn hình, dùng RAG grounded trên cẩm nang dịch vụ/bản đồ khu nghỉ, thực hiện tác vụ qua tool (đặt bàn nhà hàng, gọi dọn phòng, đặt tour, chỉ đường), và chuyển nhân viên khi ngoài phạm vi. Agent lập kế hoạch đa bước & giữ memory ngữ cảnh hội thoại/khách; đồng thời giải quyết sự đánh đổi giữa dung lượng mô hình lượng tử hóa trên phần cứng biên, độ trễ phản hồi tức thì ở chế độ offline và cơ chế khóa liên động an toàn xác định theo ngữ cảnh vận hành thực tế.

🔒 Ràng buộc: Trả lời grounded chống bịa (chỉ dựa cẩm nang chính thức, không bịa giá/giờ); tác vụ tạo yêu cầu dịch vụ cần xác nhận HITL/nhân viên duyệt; ưu tiên xử lý on-device đảm bảo hoạt động khi mạng chập chờn; dữ liệu khách xử lý riêng tư; đa ngôn ngữ chính xác; đo độ trễ phản hồi & tỷ lệ grounded.

### 🛠️ Tech Stack
• SLM đa ngôn ngữ lượng tử hóa (Qwen2.5/Gemma q4) llama.cpp
• STT đa ngôn ngữ (Whisper) + TTS đa ngôn ngữ (Piper/XTTS)
• RAG cẩm nang dịch vụ + vector DB (Chroma/FAISS)
• agent tool-use & lập kế hoạch (LangGraph, tool đặt dịch vụ giả lập)
• backend FastAPI
• frontend React giao diện kiosk/robot + dashboard quản lý sảnh
• mô phỏng Jetson kiosk edge
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu AI tại biên: VIVOS / FLEURS + tiếng ồn DEMAND (giọng nói), DMD / YawDD (giám sát tài xế), CelebA-Spoof / MIDV-500 (chống giả mạo eKYC), UR Fall Detection, log OBD-II/CAN-bus và chuẩn đo hiệu năng biên MLPerf Tiny/Edge.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• App kiosk hỏi-đáp đa ngôn ngữ grounded qua RAG & thực hiện tác vụ dịch vụ giả lập, đăng nhập ≥2 vai trò (khách & nhân viên/quản trị), HITL duyệt yêu cầu dịch vụ, xử lý câu ngoài phạm vi, metric tỷ lệ grounded & độ chính xác intent/ngôn ngữ.

Nâng cao:
• Chạy offline với SLM lượng tử hóa đo độ trễ/kích thước
• hỗ trợ giọng nói đa ngôn ngữ end-to-end
• multi-agent (hỏi-đáp + đặt dịch vụ + điều phối)
• eval RAG/hallucination
• giám sát nhiều kiosk + OTA cập nhật cẩm nang
• guardrails chống bịa giá/giờ & bảo mật dữ liệu khách
• Tối ưu hóa kiến trúc phối hợp Edge – Cloud (hoạt động mượt mà cả khi offline hoàn toàn với mô hình lượng tử hóa) kèm cơ chế khóa an toàn theo ngữ cảnh vận hành và bảng đo telemetry phần cứng thực tế.

---
