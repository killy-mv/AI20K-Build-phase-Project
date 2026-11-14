# Lĩnh vực: FIN - Fintech – Ví điện tử & Dịch vụ tài chính số

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `FIN-01` | [AI Agent Trợ lý Tài chính Cá nhân & Quản lý Chi tiêu Thông minh](#fin-01) |
| `FIN-02` | [AI Agent Phát hiện Gian lận Giao dịch Realtime cho Ví điện tử](#fin-02) |
| `FIN-03` | [AI Agent KYC/eKYC & Xác minh Danh tính Tự động](#fin-03) |
| `FIN-04` | [AI Agent Chấm điểm Tín dụng Thay thế (Alternative Credit Scoring)](#fin-04) |
| `FIN-05` | [AI Agent CSKH Ví điện tử & Xử lý Khiếu nại Giao dịch](#fin-05) |
| `FIN-06` | [AI Agent Trợ lý Đầu tư & Tiết kiệm Cá nhân hóa](#fin-06) |
| `FIN-07` | [AI Agent Phát hiện Rửa tiền (AML) & Giám sát Tuân thủ](#fin-07) |
| `FIN-08` | [AI Agent Trợ lý Thanh toán Hóa đơn & Nhắc nợ Tự động](#fin-08) |
| `FIN-09` | [AI Agent Phân loại & Phân tích Giao dịch Tự động](#fin-09) |
| `FIN-10` | [AI Agent Tư vấn Sản phẩm Tài chính Cá nhân hóa](#fin-10) |
| `FIN-11` | [AI Agent Phát hiện Tài khoản Giả mạo & Bot](#fin-11) |
| `FIN-12` | [AI Agent Thu hồi Nợ Nhân văn & Cá nhân hóa](#fin-12) |
| `FIN-13` | [AI Agent Gợi ý Ưu đãi & Hoàn tiền Cá nhân hóa](#fin-13) |
| `FIN-14` | [AI Agent Quản lý Ngân sách Gia đình & Ví chung](#fin-14) |
| `FIN-15` | [AI Agent Hỗ trợ Tiểu thương: Báo cáo Doanh thu & Đối soát](#fin-15) |
| `FIN-16` | [AI Agent Phát hiện Bất thường Tài khoản & Cảnh báo An toàn](#fin-16) |
| `FIN-17` | [AI Agent Trợ lý Tuân thủ Quy định Ngân hàng Nhà nước](#fin-17) |
| `FIN-18` | [AI Agent Dự báo Dòng tiền Cá nhân & Cảnh báo Thiếu hụt](#fin-18) |
| `FIN-19` | [AI Agent Chống Lừa đảo & Cảnh báo Giao dịch Rủi ro cho Người dùng](#fin-19) |
| `FIN-20` | [AI Agent Trợ lý Onboarding & Hướng dẫn Nghiệp vụ Ví thông minh](#fin-20) |

---

## [FIN-01] AI Agent Trợ lý Tài chính Cá nhân & Quản lý Chi tiêu Thông minh

### 📝 Mô tả đề tài
📍 Thực trạng: Người dùng ví điện tử có hàng trăm giao dịch mỗi tháng nhưng không nắm được tiền đi đâu, không lập được ngân sách, ứng dụng chỉ liệt kê sao kê thô. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tự động phân tích dòng tiền, chủ động lập kế hoạch ngân sách, phát hiện chi tiêu bất thường, đối thoại tư vấn tiết kiệm và tự lập kế hoạch nhiều bước (đọc giao dịch → phân loại → tính toán → cảnh báo → đề xuất); đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi agent thực hiện bất kỳ hành động thay đổi tiền (đặt lệnh tiết kiệm tự động, chuyển tiền); mọi con số chi tiêu phải tính bằng code tool, CẤM LLM tự bịa số; tuân thủ PDPA khi xử lý dữ liệu tài chính cá nhân; cảnh báo khi dữ liệu không đủ để kết luận thay vì suy đoán.

### 🛠️ Tech Stack
• LLM (GPT-4o/Claude) điều phối
• LangGraph cho luồng agent đa bước + state/memory
• vector DB (Qdrant/Chroma) lưu lịch sử & sở thích người dùng
• Python code tool (pandas) tính toán chính xác ngân sách/thống kê
• mô hình phân loại giao dịch (scikit-learn/LightGBM)
• backend FastAPI
• PostgreSQL
• frontend React + Tailwind + Recharts
• deploy Render/Railway + Vercel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phòng chống tội phạm tài chính PaySim (giao dịch ví di động), IEEE-CIS Fraud Detection, IBM AMLSim / Elliptic Graph Dataset (đồ thị luồng tiền rửa tiền) và CelebA-Spoof / MIDV-500 (cho eKYC).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy online, đăng nhập, ≥2 vai trò (người dùng/admin)
• agent import giao dịch mô phỏng, tự phân loại, sinh báo cáo chi tiêu, đối thoại hỏi-đáp tài chính
• dashboard trực quan.

Nâng cao:
• Agent chủ động lập ngân sách theo mục tiêu, cảnh báo vượt hạn mức realtime, memory dài hạn ghi nhớ thói quen, HITL phê duyệt lệnh tiết kiệm tự động, dự báo số dư cuối tháng, xử lý lỗi khi dữ liệu thiếu
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-02] AI Agent Phát hiện Gian lận Giao dịch Realtime cho Ví điện tử

### 📝 Mô tả đề tài
📍 Thực trạng: Ví điện tử xử lý hàng nghìn giao dịch/giây, gian lận (chiếm đoạt tài khoản, giao dịch bất thường, thẻ giả) gây thiệt hại lớn; rule cứng dễ bị lách và tạo nhiều báo động giả. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát dòng giao dịch realtime, kết hợp mô hình ML tính điểm rủi ro với LLM giải thích & ra quyết định theo ngữ cảnh (chặn/xác minh thêm/cho qua), tự động điều tra và tổng hợp bằng chứng; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi KHÓA tài khoản hoặc chặn giao dịch giá trị lớn; điểm rủi ro phải từ mô hình ML/code, CẤM LLM tự bịa xác suất; tuân thủ NHNN & PDPA; giảm thiểu false positive; ghi log giải trình mọi quyết định. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM cho reasoning & giải thích quyết định
• LangGraph điều phối agent điều tra
• mô hình ML phát hiện gian lận (XGBoost/Isolation Forest/Autoencoder anomaly detection)
• feature store
• vector DB lưu pattern gian lận đã biết
• Python code tool tính điểm rủi ro
• Kafka/queue mô phỏng stream
• backend FastAPI
• PostgreSQL
• frontend React dashboard realtime
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phòng chống tội phạm tài chính PaySim (giao dịch ví di động), IEEE-CIS Fraud Detection, IBM AMLSim / Elliptic Graph Dataset (đồ thị luồng tiền rửa tiền) và CelebA-Spoof / MIDV-500 (cho eKYC).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò analyst/admin
• mô phỏng luồng giao dịch, agent chấm điểm rủi ro + gắn cờ giao dịch nghi vấn, giải thích lý do
• dashboard cảnh báo.

Nâng cao:
• Agent tự điều tra đa bước (truy vấn lịch sử, so pattern, dùng tool), hàng đợi HITL để analyst duyệt khóa tài khoản, memory học pattern mới, cảnh báo khi độ tin cậy thấp, mô phỏng tấn công để kiểm thử
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-03] AI Agent KYC/eKYC & Xác minh Danh tính Tự động

### 📝 Mô tả đề tài
📍 Thực trạng: Mở ví/tài khoản fintech yêu cầu định danh eKYC (CCCD, ảnh chân dung, đối chiếu) nhưng quy trình thủ công chậm, dễ sai sót và bị giả mạo giấy tờ. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent điều phối toàn bộ luồng eKYC: trích xuất thông tin giấy tờ (OCR), đối chiếu khuôn mặt, kiểm tra tính hợp lệ, phát hiện giả mạo/deepfake, đối chiếu blacklist, tự lập kế hoạch các bước xác minh và yêu cầu bổ sung khi thiếu; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC phê duyệt hồ sơ ở vùng rủi ro/nghi ngờ giả mạo trước khi kích hoạt tài khoản; CẤM LLM tự khẳng định khớp danh tính khi điểm khớp thấp; tuân thủ NHNN về định danh & PDPA về dữ liệu sinh trắc; chống gian lận giấy tờ; lưu vết audit. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM điều phối + giải thích
• LangGraph cho luồng KYC nhiều bước & state
• OCR (Tesseract/VietOCR/mô hình vision) trích xuất CCCD
• face matching (DeepFace/InsightFace)
• mô hình phát hiện giả mạo
• code tool kiểm tra checksum CCCD/định dạng
• vector DB đối chiếu
• backend FastAPI
• PostgreSQL + lưu trữ mã hóa
• frontend React upload & wizard
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phòng chống tội phạm tài chính PaySim (giao dịch ví di động), IEEE-CIS Fraud Detection, IBM AMLSim / Elliptic Graph Dataset (đồ thị luồng tiền rửa tiền) và CelebA-Spoof / MIDV-500 (cho eKYC).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò người dùng/nhân viên thẩm định
• luồng upload giấy tờ + selfie, agent OCR + đối chiếu khuôn mặt (dữ liệu mô phỏng), kết luận đạt/không đạt kèm giải thích.

Nâng cao:
• Agent tự yêu cầu bổ sung khi thiếu/mờ, chấm điểm rủi ro giả mạo, hàng đợi HITL cho thẩm định viên, memory hồ sơ, cảnh báo độ tin cậy, đối chiếu danh sách đen mô phỏng, audit log đầy đủ
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-04] AI Agent Chấm điểm Tín dụng Thay thế (Alternative Credit Scoring)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhiều người dùng ví (SV, lao động tự do, tiểu thương) không có lịch sử tín dụng ngân hàng nên khó tiếp cận vay tiêu dùng. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent chấm điểm tín dụng thay thế từ dữ liệu hành vi (lịch sử giao dịch ví, thanh toán hóa đơn, dòng tiền), lập kế hoạch thu thập-tính toán-diễn giải, đưa ra hạn mức đề xuất và giải thích minh bạch (explainable); đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC phê duyệt quyết định cấp/tăng hạn mức tín dụng; điểm số phải từ mô hình ML + code, CẤM LLM tự bịa điểm; tránh thiên vị/phân biệt đối xử; tuân thủ NHNN & PDPA; giải trình được (không hộp đen với khách hàng); cảnh báo khi dữ liệu không đủ. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM diễn giải & đối thoại
• LangGraph điều phối luồng chấm điểm
• mô hình ML scoring (LightGBM/Logistic) + SHAP giải thích
• code tool tính DTI/dòng tiền chính xác
• feature engineering từ giao dịch mô phỏng
• vector DB lưu hồ sơ
• backend FastAPI
• PostgreSQL
• frontend React dashboard + biểu đồ
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chấm điểm tín dụng & tài chính Home Credit Default Risk, LendingClub / German Credit Dataset, FinBen và kho văn bản quy định ngành ngân hàng – ví điện tử.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò người vay/cán bộ tín dụng
• agent tính điểm từ dữ liệu hành vi mô phỏng, đề xuất hạn mức, giải thích yếu tố ảnh hưởng (SHAP).

Nâng cao:
• Agent lập kế hoạch thu thập thêm dữ liệu khi thiếu, phân tích what-if cải thiện điểm, HITL duyệt cấp hạn mức, memory lịch sử, kiểm tra công bằng/bias, cảnh báo độ tin cậy thấp, báo cáo giải trình cho khách
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-05] AI Agent CSKH Ví điện tử & Xử lý Khiếu nại Giao dịch

### 📝 Mô tả đề tài
📍 Thực trạng: Tổng đài ví quá tải với khiếu nại giao dịch (chuyển nhầm, tiền chưa về, trừ tiền hai lần, hoàn tiền), khách phải chờ lâu, agent người phải tra cứu nhiều hệ thống. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent CSKH biết tra cứu trạng thái giao dịch qua tool, tự điều tra nguyên nhân, phân loại khiếu nại, đề xuất hướng xử lý/hoàn tiền, tạo ticket và chuyển cấp khi cần; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi phê duyệt hoàn tiền hoặc điều chỉnh số dư; CẤM LLM bịa trạng thái/số tiền giao dịch — phải tra từ hệ thống; tuân thủ PDPA (không lộ thông tin người khác); xác thực danh tính khách trước khi thao tác nhạy cảm; ghi log. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM đối thoại + reasoning
• LangGraph điều phối agent + tool-calling
• RAG trên KB chính sách/FAQ (vector DB)
• code tool tra cứu trạng thái giao dịch (API mô phỏng)
• mô hình phân loại intent/khiếu nại
• backend FastAPI
• PostgreSQL
• frontend React chat + màn hình agent người
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính FinQA, TAT-QA và dữ liệu chuỗi giao dịch tài chính cá nhân / phân loại merchant công khai (Czech Financial / Kaggle Personal Finance).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò khách/nhân viên CSKH
• agent chat trả lời, tra cứu giao dịch mô phỏng, phân loại và tạo ticket khiếu nại.

Nâng cao:
• Agent tự điều tra đa bước nguyên nhân, đề xuất phương án hoàn tiền với HITL phê duyệt, memory hội thoại & lịch sử khách, escalation thông minh, xử lý lỗi khi không tìm thấy giao dịch, cảnh báo khi ngoài thẩm quyền
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-06] AI Agent Trợ lý Đầu tư & Tiết kiệm Cá nhân hóa

### 📝 Mô tả đề tài
📍 Thực trạng: Người dùng trẻ muốn đầu tư (quỹ mở, tích lũy, vàng số) nhưng thiếu kiến thức, dễ FOMO, không rõ khẩu vị rủi ro và mục tiêu tài chính. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tư vấn tiết kiệm/đầu tư cá nhân hóa: đánh giá khẩu vị rủi ro, đề xuất phân bổ danh mục theo mục tiêu, mô phỏng kịch bản, lập kế hoạch tích lũy định kỳ và theo dõi tiến độ; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi thực hiện lệnh đặt/rút đầu tư; CẤM LLM bịa lợi suất/số liệu thị trường — dùng dữ liệu mô phỏng qua code tool; kèm cảnh báo rủi ro & miễn trừ tư vấn; tuân thủ quy định về tư vấn đầu tư & PDPA; không hứa hẹn lợi nhuận. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM đối thoại + reasoning
• LangGraph luồng tư vấn nhiều bước
• code tool tính toán lãi kép/phân bổ danh mục/mô phỏng Monte Carlo
• vector DB lưu hồ sơ & sản phẩm
• RAG kiến thức đầu tư
• backend FastAPI
• PostgreSQL
• frontend React + Recharts
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính FinQA, TAT-QA và dữ liệu chuỗi giao dịch tài chính cá nhân / phân loại merchant công khai (Czech Financial / Kaggle Personal Finance).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò nhà đầu tư/admin sản phẩm
• agent khảo sát khẩu vị rủi ro, đề xuất danh mục, mô phỏng tăng trưởng theo mục tiêu (dữ liệu mô phỏng).

Nâng cao:
• Agent lập kế hoạch tích lũy định kỳ, theo dõi & điều chỉnh danh mục, HITL phê duyệt lệnh, memory mục tiêu dài hạn, cảnh báo rủi ro/biến động, xử lý khi thông tin người dùng chưa đủ
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-07] AI Agent Phát hiện Rửa tiền (AML) & Giám sát Tuân thủ

### 📝 Mô tả đề tài
📍 Thực trạng: Fintech phải giám sát giao dịch chống rửa tiền theo quy định, nhưng mô hình luồng tiền phức tạp (structuring, tài khoản trung gian, giao dịch vòng) khó phát hiện thủ công. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát AML: phát hiện mẫu hình đáng ngờ, phân tích mạng lưới giao dịch, tự điều tra và tổng hợp hồ sơ nghi vấn (SAR), đối chiếu danh sách trừng phạt/PEP; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi phong tỏa tài khoản/báo cáo cơ quan; CẤM LLM bịa liên kết/số liệu — mọi cáo buộc phải có bằng chứng từ dữ liệu; tuân thủ NHNN/Luật PCRT & PDPA; giảm báo động giả; audit trail đầy đủ; giữ bí mật điều tra. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM reasoning + soạn báo cáo nghi vấn
• LangGraph điều phối agent điều tra
• phân tích đồ thị (NetworkX) phát hiện mạng lưới
• mô hình ML anomaly/typology detection
• code tool tính ngưỡng/tổng hợp
• vector DB đối chiếu danh sách đen/PEP
• backend FastAPI
• PostgreSQL/graph DB
• frontend React + graph visualization
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phòng chống tội phạm tài chính PaySim (giao dịch ví di động), IEEE-CIS Fraud Detection, IBM AMLSim / Elliptic Graph Dataset (đồ thị luồng tiền rửa tiền) và CelebA-Spoof / MIDV-500 (cho eKYC).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò compliance officer/admin
• agent quét giao dịch mô phỏng, gắn cờ mẫu đáng ngờ, trực quan mạng lưới, sinh tóm tắt nghi vấn.

Nâng cao:
• Agent tự điều tra đa bước theo dòng tiền, soạn hồ sơ SAR có bằng chứng, HITL duyệt phong tỏa/báo cáo, memory case, đối chiếu sanction list mô phỏng, cảnh báo mức độ tin cậy, log tuân thủ
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-08] AI Agent Trợ lý Thanh toán Hóa đơn & Nhắc nợ Tự động

### 📝 Mô tả đề tài
📍 Thực trạng: Người dùng có nhiều hóa đơn định kỳ (điện, nước, internet, thẻ tín dụng, trả góp) dễ quên hạn, bị phạt trễ; ví chỉ nhắc chung chung. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent quản lý hóa đơn: tổng hợp các khoản phải trả, dự báo lịch, nhắc nợ thông minh theo dòng tiền, tự lập kế hoạch thanh toán ưu tiên và thực hiện thanh toán khi được phép; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi agent thực hiện thanh toán/trích tiền tự động; CẤM LLM bịa số tiền/hạn thanh toán — lấy từ dữ liệu hóa đơn qua tool; tuân thủ PDPA; đảm bảo không thanh toán trùng/sai; cảnh báo khi số dư không đủ. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM đối thoại + lập kế hoạch
• LangGraph luồng agent + tool thanh toán (mô phỏng)
• code tool tính lịch/số tiền/ưu tiên
• vector DB lưu hóa đơn & sở thích
• scheduler (cron) nhắc lịch
• backend FastAPI
• PostgreSQL
• frontend React
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính FinQA, TAT-QA và dữ liệu chuỗi giao dịch tài chính cá nhân / phân loại merchant công khai (Czech Financial / Kaggle Personal Finance).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò người dùng/admin
• agent tổng hợp hóa đơn mô phỏng, hiển thị lịch, gửi nhắc nhở, đối thoại về khoản phải trả.

Nâng cao:
• Agent lập kế hoạch thanh toán ưu tiên theo dòng tiền, thực thi thanh toán với HITL phê duyệt, memory thói quen, cảnh báo số dư không đủ, xử lý lỗi thanh toán, dự báo áp lực chi tuần tới
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-09] AI Agent Phân loại & Phân tích Giao dịch Tự động

### 📝 Mô tả đề tài
📍 Thực trạng: Diễn giải giao dịch trong sao kê ví thường khó hiểu (mã merchant, mô tả cụt), người dùng không biết đã tiêu vào đâu, thống kê ngành hàng sai. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tự động làm giàu & phân loại giao dịch (gán danh mục, nhận diện merchant, phát hiện giao dịch định kỳ/subscription), phân tích xu hướng và trả lời câu hỏi phân tích bằng ngôn ngữ tự nhiên; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: Mọi thống kê phải tính bằng code tool trên dữ liệu thật, CẤM LLM bịa số/tỷ lệ; HITL cho phép người dùng sửa nhãn sai (human-in-the-loop cải thiện mô hình); tuân thủ PDPA; đảm bảo độ chính xác phân loại; cảnh báo khi không chắc chắn merchant. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM cho phân loại few-shot + text-to-analysis
• LangGraph điều phối
• mô hình ML phân loại (embeddings + classifier)
• vector DB nhận diện merchant
• code tool (pandas) tính thống kê/phát hiện định kỳ
• backend FastAPI
• PostgreSQL
• frontend React + biểu đồ
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính FinQA, TAT-QA và dữ liệu chuỗi giao dịch tài chính cá nhân / phân loại merchant công khai (Czech Financial / Kaggle Personal Finance).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò người dùng/admin
• agent phân loại giao dịch mô phỏng, nhận diện merchant, dashboard theo danh mục, hỏi-đáp phân tích.

Nâng cao:
• Agent phát hiện subscription & giao dịch định kỳ, HITL sửa nhãn để học lại, memory quy tắc cá nhân, phân tích xu hướng đa tháng, cảnh báo độ tin cậy nhãn thấp, xuất báo cáo
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-10] AI Agent Tư vấn Sản phẩm Tài chính Cá nhân hóa

### 📝 Mô tả đề tài
📍 Thực trạng: Ví điện tử có nhiều sản phẩm (vay tiêu dùng, thẻ tín dụng, bảo hiểm, tích lũy, trả góp) nhưng người dùng không biết chọn cái nào phù hợp, tư vấn thủ công không cá nhân hóa. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent tư vấn sản phẩm tài chính: hiểu nhu cầu qua đối thoại, đối chiếu điều kiện & hồ sơ người dùng, so sánh sản phẩm, tính chi phí thực (lãi, phí) và đề xuất phù hợp có giải thích; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi nộp hồ sơ/đăng ký sản phẩm thật; CẤM LLM bịa điều khoản/lãi suất — chỉ dùng dữ liệu sản phẩm qua RAG/tool; tính toán chi phí bằng code; kèm cảnh báo rủi ro & minh bạch phí; tuân thủ quy định tư vấn tài chính & PDPA; không tư vấn sai lệch. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM đối thoại
• LangGraph luồng tư vấn
• RAG trên catalog sản phẩm (vector DB)
• code tool tính lãi/APR/tổng chi phí
• mô hình gợi ý phù hợp (rule + ML)
• backend FastAPI
• PostgreSQL
• frontend React so sánh sản phẩm
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính FinQA, TAT-QA và dữ liệu chuỗi giao dịch tài chính cá nhân / phân loại merchant công khai (Czech Financial / Kaggle Personal Finance).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò khách/admin sản phẩm
• agent hỏi nhu cầu, đề xuất & so sánh sản phẩm mô phỏng, tính chi phí thực.

Nâng cao:
• Agent kiểm tra điều kiện đủ điều kiện theo hồ sơ, lập kế hoạch tư vấn nhiều bước, HITL trước khi đăng ký, memory nhu cầu, cảnh báo rủi ro/phí ẩn, xử lý khi không sản phẩm nào phù hợp
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-11] AI Agent Phát hiện Tài khoản Giả mạo & Bot

### 📝 Mô tả đề tài
📍 Thực trạng: Ví điện tử bị lạm dụng bởi tài khoản giả/bot để trục lợi khuyến mãi (promo abuse), tạo tài khoản hàng loạt, làm nhiễu hệ thống. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent phát hiện tài khoản giả/bot dựa trên hành vi (tốc độ thao tác, thiết bị, mạng lưới liên kết, mẫu đăng ký/khuyến mãi), tự điều tra cụm tài khoản liên quan và đề xuất xử lý; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi KHÓA/thu hồi ưu đãi tài khoản; điểm nghi vấn từ mô hình ML, CẤM LLM tự bịa; tránh khóa nhầm người dùng thật (false positive); tuân thủ PDPA; log giải trình; cảnh báo khi bằng chứng yếu. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM reasoning + giải thích
• LangGraph điều phối điều tra
• mô hình ML (behavior clustering, anomaly detection)
• phân tích đồ thị liên kết (device/IP) NetworkX
• code tool tính điểm
• vector DB pattern
• backend FastAPI
• PostgreSQL/graph
• frontend React + graph view
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phòng chống tội phạm tài chính PaySim (giao dịch ví di động), IEEE-CIS Fraud Detection, IBM AMLSim / Elliptic Graph Dataset (đồ thị luồng tiền rửa tiền) và CelebA-Spoof / MIDV-500 (cho eKYC).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò analyst/admin
• agent chấm điểm tài khoản mô phỏng, gắn cờ nghi vấn bot, hiển thị cụm liên kết, giải thích.

Nâng cao:
• Agent điều tra đa bước phát hiện cụm promo abuse, đề xuất hành động với HITL duyệt khóa, memory pattern mới, mô phỏng tấn công tạo tài khoản hàng loạt, cảnh báo độ tin cậy, audit
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-12] AI Agent Thu hồi Nợ Nhân văn & Cá nhân hóa

### 📝 Mô tả đề tài
📍 Thực trạng: Thu hồi nợ tiêu dùng qua ví thường máy móc, gây khó chịu, tỷ lệ thu hồi thấp; nhắc nợ hàng loạt không phù hợp hoàn cảnh từng người. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent thu hồi nợ nhân văn: phân khúc khách theo khả năng/thái độ trả nợ, cá nhân hóa thông điệp & kênh, đề xuất phương án cơ cấu/giãn nợ, thương lượng lịch trả và lập kế hoạch nhắc phù hợp; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi cam kết phương án cơ cấu nợ/miễn giảm; giọng điệu tôn trọng, không đe dọa/quấy rối (tuân thủ quy định thu hồi nợ); CẤM LLM bịa số dư nợ/lãi phạt — lấy từ hệ thống qua tool; tuân thủ PDPA; cảnh báo khi khách gặp khó khăn cần chuyển người. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM đối thoại đồng cảm
• LangGraph luồng thương lượng
• mô hình ML phân khúc & dự đoán khả năng trả
• code tool tính lịch trả/lãi/phương án cơ cấu
• vector DB lưu lịch sử tương tác
• backend FastAPI
• PostgreSQL
• frontend React
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chấm điểm tín dụng & tài chính Home Credit Default Risk, LendingClub / German Credit Dataset, FinBen và kho văn bản quy định ngành ngân hàng – ví điện tử.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò khách nợ/nhân viên thu hồi
• agent phân khúc, gửi thông điệp cá nhân hóa, đối thoại nhắc nợ lịch sự, tính số nợ chính xác (mô phỏng).

Nâng cao:
• Agent đề xuất & mô phỏng phương án giãn/cơ cấu nợ, thương lượng lịch trả với HITL phê duyệt, memory lịch sử cam kết, cảnh báo chuyển người khi khách khó khăn, đo tỷ lệ hồi đáp
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-13] AI Agent Gợi ý Ưu đãi & Hoàn tiền Cá nhân hóa

### 📝 Mô tả đề tài
📍 Thực trạng: Ví phát nhiều voucher/cashback nhưng không đúng nhu cầu, người dùng bỏ lỡ ưu đãi, hiệu quả marketing thấp, ngân sách khuyến mãi lãng phí. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent cá nhân hóa ưu đãi: phân tích hành vi chi tiêu, dự đoán ưu đãi phù hợp & thời điểm, tối ưu trong ngân sách khuyến mãi, giải thích lý do gợi ý và tránh trục lợi khuyến mãi; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC phê duyệt chiến dịch/ngân sách trước khi phát ưu đãi hàng loạt; CẤM LLM bịa số liệu ROI/tỷ lệ chuyển đổi — tính bằng code; tuân thủ PDPA (cá nhân hóa có kiểm soát); chống promo abuse; kiểm soát chi phí trong hạn mức; cảnh báo khi vượt ngân sách. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM giải thích + đối thoại
• LangGraph điều phối
• mô hình gợi ý (collaborative filtering/uplift modeling)
• code tool tối ưu ngân sách & tính ROI
• vector DB hồ sơ & ưu đãi
• backend FastAPI
• PostgreSQL
• frontend React dashboard chiến dịch
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính FinQA, TAT-QA và dữ liệu chuỗi giao dịch tài chính cá nhân / phân loại merchant công khai (Czech Financial / Kaggle Personal Finance).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò người dùng/marketing admin
• agent gợi ý ưu đãi cá nhân hóa từ hành vi mô phỏng, giải thích lý do, dashboard chiến dịch.

Nâng cao:
• Agent tối ưu phân bổ ngân sách khuyến mãi, dự đoán uplift, HITL duyệt chiến dịch phát hàng loạt, memory sở thích, phát hiện & chặn promo abuse, cảnh báo vượt ngân sách, đo hiệu quả
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-14] AI Agent Quản lý Ngân sách Gia đình & Ví chung

### 📝 Mô tả đề tài
📍 Thực trạng: Các gia đình dùng ví chung/nhiều thành viên khó theo dõi chi tiêu chung, phân bổ trách nhiệm, thống nhất ngân sách và mục tiêu tiết kiệm. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent quản lý ngân sách gia đình: tổng hợp chi tiêu nhiều thành viên, phân bổ hạn mức theo hạng mục, theo dõi mục tiêu chung (mua sắm lớn, du lịch), giải quyết mâu thuẫn ngân sách và lập kế hoạch tiết kiệm nhóm; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC (chủ hộ phê duyệt) trước khi thay đổi hạn mức chung/chuyển tiền quỹ chung; CẤM LLM bịa số — tính bằng code; phân quyền xem/sửa theo vai trò thành viên; tuân thủ PDPA (dữ liệu nhiều người); cảnh báo khi thành viên vượt hạn mức. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM đối thoại + lập kế hoạch
• LangGraph điều phối đa vai trò
• code tool tính ngân sách/phân bổ/tiến độ mục tiêu
• vector DB lưu ngữ cảnh gia đình
• backend FastAPI + phân quyền
• PostgreSQL
• frontend React (dashboard nhóm)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính FinQA, TAT-QA và dữ liệu chuỗi giao dịch tài chính cá nhân / phân loại merchant công khai (Czech Financial / Kaggle Personal Finance).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, ≥2 vai trò (chủ hộ/thành viên)
• agent tổng hợp chi tiêu nhóm mô phỏng, lập ngân sách hạng mục, theo dõi mục tiêu chung, dashboard gia đình.

Nâng cao:
• Agent đề xuất phân bổ tối ưu, cảnh báo thành viên vượt hạn mức realtime, HITL chủ hộ duyệt thay đổi quỹ chung, memory mục tiêu dài hạn, gợi ý điều chỉnh khi lệch kế hoạch, xử lý xung đột ngân sách
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-15] AI Agent Hỗ trợ Tiểu thương: Báo cáo Doanh thu & Đối soát

### 📝 Mô tả đề tài
📍 Thực trạng: Tiểu thương/merchant nhận thanh toán qua ví/QR nhưng khó tự đối soát giao dịch, tổng hợp doanh thu, phát hiện thiếu tiền về hay chênh lệch với sổ sách. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent hỗ trợ merchant: tự động đối soát giao dịch với sao kê, phát hiện chênh lệch/giao dịch thiếu, sinh báo cáo doanh thu, trả lời câu hỏi kinh doanh và cảnh báo bất thường doanh số; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi tạo yêu cầu tra soát/khiếu nại chính thức lên hệ thống; CẤM LLM bịa số doanh thu/chênh lệch — đối soát bằng code trên dữ liệu thật; tuân thủ PDPA; đảm bảo độ chính xác đối soát; cảnh báo khi dữ liệu không khớp cần kiểm tra tay. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM text-to-analysis + đối thoại
• LangGraph điều phối
• code tool đối soát (pandas reconciliation) & tính báo cáo
• mô hình phát hiện bất thường doanh số
• vector DB lưu ngữ cảnh cửa hàng
• backend FastAPI
• PostgreSQL
• frontend React + biểu đồ
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phòng chống tội phạm tài chính PaySim (giao dịch ví di động), IEEE-CIS Fraud Detection, IBM AMLSim / Elliptic Graph Dataset (đồ thị luồng tiền rửa tiền) và CelebA-Spoof / MIDV-500 (cho eKYC).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò merchant/admin
• agent đối soát giao dịch mô phỏng với sổ sách, phát hiện chênh lệch, sinh báo cáo doanh thu, hỏi-đáp kinh doanh.

Nâng cao:
• Agent tự điều tra giao dịch thiếu, đề xuất tạo yêu cầu tra soát với HITL duyệt, memory theo cửa hàng, cảnh báo bất thường doanh số realtime, dự báo doanh thu, xử lý dữ liệu lệch
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-16] AI Agent Phát hiện Bất thường Tài khoản & Cảnh báo An toàn

### 📝 Mô tả đề tài
📍 Thực trạng: Người dùng ví có thể bị chiếm đoạt tài khoản (ATO), lộ mật khẩu, đăng nhập lạ, thao tác bất thường mà không kịp nhận biết. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent giám sát an toàn tài khoản: phát hiện đăng nhập/thiết bị lạ, hành vi bất thường, chủ động cảnh báo người dùng, đề xuất biện pháp bảo vệ (xác thực lại, tạm khóa) và hướng dẫn xử lý khi bị xâm nhập; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC (xác nhận người dùng/duyệt admin) trước khi tạm KHÓA tài khoản hay reset bảo mật; điểm bất thường từ mô hình ML, CẤM LLM bịa; tuân thủ PDPA & NHNN; giảm cảnh báo giả gây phiền; cảnh báo mức độ rủi ro rõ ràng; log sự cố. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM giải thích + hướng dẫn
• LangGraph điều phối phản ứng sự cố
• mô hình ML (anomaly detection hành vi đăng nhập/giao dịch)
• code tool chấm điểm rủi ro & phân tích thiết bị/vị trí
• vector DB pattern
• backend FastAPI
• PostgreSQL
• frontend React + cảnh báo
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phòng chống tội phạm tài chính PaySim (giao dịch ví di động), IEEE-CIS Fraud Detection, IBM AMLSim / Elliptic Graph Dataset (đồ thị luồng tiền rửa tiền) và CelebA-Spoof / MIDV-500 (cho eKYC).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò người dùng/admin bảo mật
• agent phát hiện đăng nhập/hành vi bất thường mô phỏng, gửi cảnh báo, giải thích rủi ro.

Nâng cao:
• Agent lập kế hoạch ứng phó (yêu cầu xác thực lại, đề xuất tạm khóa với HITL), memory thiết bị tin cậy, hướng dẫn khôi phục khi bị ATO, cảnh báo mức rủi ro phân tầng, xử lý false positive
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-17] AI Agent Trợ lý Tuân thủ Quy định Ngân hàng Nhà nước

### 📝 Mô tả đề tài
📍 Thực trạng: Đội vận hành/pháp chế fintech phải nắm hàng loạt thông tư, quy định NHNN (hạn mức giao dịch, định danh, báo cáo, phí) liên tục thay đổi, tra cứu thủ công chậm và dễ bỏ sót. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent trợ lý tuân thủ: tra cứu & diễn giải quy định (RAG), kiểm tra một nghiệp vụ/giao dịch có tuân thủ không, cảnh báo vi phạm hạn mức, và hỗ trợ soạn checklist/báo cáo tuân thủ; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC — mọi kết luận tuân thủ phải được chuyên viên pháp chế phê duyệt trước khi áp dụng; CẤM LLM bịa điều khoản/số hiệu văn bản — bắt buộc trích dẫn nguồn từ KB (chống hallucination); tuân thủ PDPA; cảnh báo khi không tìm thấy căn cứ rõ ràng thay vì suy đoán. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM + RAG bắt buộc trích dẫn nguồn
• LangGraph điều phối tra cứu-kiểm tra-đối chiếu
• vector DB kho văn bản pháp lý
• code tool kiểm tra hạn mức/ngưỡng theo quy định
• backend FastAPI
• PostgreSQL
• frontend React (tra cứu + kiểm tra tuân thủ)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu chấm điểm tín dụng & tài chính Home Credit Default Risk, LendingClub / German Credit Dataset, FinBen và kho văn bản quy định ngành ngân hàng – ví điện tử.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò nhân viên/chuyên viên pháp chế
• agent tra cứu quy định (bộ văn bản mô phỏng) có trích dẫn, kiểm tra một nghiệp vụ tuân thủ hay không, giải thích.

Nâng cao:
• Agent kiểm tra tự động giao dịch/nghiệp vụ theo nhiều quy định, sinh checklist & báo cáo tuân thủ, HITL phê duyệt kết luận, memory case, cảnh báo thiếu căn cứ, theo dõi cập nhật quy định
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-18] AI Agent Dự báo Dòng tiền Cá nhân & Cảnh báo Thiếu hụt

### 📝 Mô tả đề tài
📍 Thực trạng: Người dùng khó biết trước cuối tháng có đủ tiền không, dễ rơi vào thiếu hụt hoặc phải vay nóng do không dự báo được thu-chi. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent dự báo dòng tiền cá nhân: học mẫu thu-chi định kỳ, dự báo số dư tương lai theo kịch bản, cảnh báo sớm nguy cơ thiếu hụt, đề xuất điều chỉnh chi tiêu/thời điểm thanh toán và mô phỏng what-if; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi agent tự động chuyển tiền/đặt lệnh dựa trên dự báo; CẤM LLM bịa con số dự báo — dùng mô hình + code tool; nêu rõ độ không chắc chắn (khoảng tin cậy); tuân thủ PDPA; cảnh báo khi dữ liệu lịch sử chưa đủ để dự báo tin cậy. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM diễn giải + đối thoại
• LangGraph điều phối
• mô hình dự báo chuỗi thời gian (Prophet/ARIMA/LightGBM) + phát hiện giao dịch định kỳ
• code tool tính dòng tiền & mô phỏng what-if
• vector DB hồ sơ
• backend FastAPI
• PostgreSQL
• frontend React + Recharts
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính FinQA, TAT-QA và dữ liệu chuỗi giao dịch tài chính cá nhân / phân loại merchant công khai (Czech Financial / Kaggle Personal Finance).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò người dùng/admin
• agent dự báo số dư & dòng tiền từ lịch sử mô phỏng, hiển thị biểu đồ kèm khoảng tin cậy, cảnh báo thiếu hụt.

Nâng cao:
• Agent mô phỏng kịch bản what-if, đề xuất điều chỉnh chi tiêu/lịch thanh toán, HITL trước hành động tự động, memory mẫu thu-chi, cảnh báo độ tin cậy dự báo thấp, xử lý dữ liệu thiếu
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-19] AI Agent Chống Lừa đảo & Cảnh báo Giao dịch Rủi ro cho Người dùng

### 📝 Mô tả đề tài
📍 Thực trạng: Người dùng ví bị lừa chuyển tiền (giả mạo người quen, đầu tư ảo, mạo danh cơ quan, link lừa đảo) với thủ đoạn ngày càng tinh vi. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent bảo vệ người dùng thời điểm giao dịch: phân tích ngữ cảnh chuyển tiền (người nhận lạ, số tiền, mô tả nghi ngờ, đối chiếu blacklist scam), cảnh báo & can thiệp trước khi chuyển, hướng dẫn kiểm chứng và giáo dục nhận biết lừa đảo; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC — agent chỉ CẢNH BÁO/tạm giữ, người dùng vẫn tự quyết định chuyển; CẤM LLM bịa nhận định lừa đảo không căn cứ; điểm rủi ro từ mô hình + đối chiếu dữ liệu; tuân thủ PDPA; tránh cảnh báo giả gây phiền; giải thích rõ lý do cảnh báo. Tuyệt đối cấm LLM tự cộng trừ số tiền hoặc tự quyết định giao dịch/khóa tài khoản khi chưa qua bước xác nhận (HITL); mọi kết luận rủi ro/tín dụng phải có giải thích định lượng minh bạch (SHAP/rule trace).

### 🛠️ Tech Stack
• LLM phân tích ngữ cảnh + hội thoại cảnh báo
• LangGraph luồng can thiệp giao dịch
• mô hình ML chấm điểm rủi ro scam + phân loại mẫu lừa đảo
• vector DB blacklist người nhận/kịch bản scam
• code tool kiểm tra ngưỡng/đối chiếu
• backend FastAPI
• PostgreSQL
• frontend React (luồng chuyển tiền + cảnh báo)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phòng chống tội phạm tài chính PaySim (giao dịch ví di động), IEEE-CIS Fraud Detection, IBM AMLSim / Elliptic Graph Dataset (đồ thị luồng tiền rửa tiền) và CelebA-Spoof / MIDV-500 (cho eKYC).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò người dùng/admin
• agent phân tích giao dịch chuyển tiền mô phỏng, cảnh báo rủi ro lừa đảo, giải thích dấu hiệu, đối chiếu blacklist.

Nâng cao:
• Agent hội thoại can thiệp nhiều bước trước khi chuyển (HITL người dùng quyết định), hướng dẫn kiểm chứng, memory người nhận tin cậy, cập nhật kịch bản scam mới, cảnh báo mức rủi ro phân tầng, giảm false positive
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---

## [FIN-20] AI Agent Trợ lý Onboarding & Hướng dẫn Nghiệp vụ Ví thông minh

### 📝 Mô tả đề tài
📍 Thực trạng: Người dùng mới lúng túng với các nghiệp vụ ví (liên kết ngân hàng, nạp/rút, QR, hạn mức, nâng hạng KYC), tỷ lệ bỏ dở onboarding cao, tổng đài quá tải câu hỏi lặp. Trong vận hành dịch vụ tài chính số và ví điện tử thực tế, dữ liệu giao dịch có tần suất lớn, tỷ lệ mất cân bằng nhãn cao và hành vi gian lận/biến động dòng tiền liên tục thay đổi, đòi hỏi độ chính xác số học tuyệt đối và khả năng giải thích minh bạch.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI Agent onboarding chủ động: dẫn dắt người dùng qua từng bước theo trạng thái tài khoản, thực hiện/kiểm tra tác vụ qua tool (kiểm tra liên kết, mức KYC, hạn mức), gợi ý bước tiếp theo và giải đáp nghiệp vụ dựa trên tài liệu; đồng thời tách biệt 100% tầng tính toán số học/dòng tiền/chấm điểm định lượng/phân tích đồ thị giao dịch bằng thuật toán xác định khỏi tầng suy luận của LLM, đồng thời tự động phát hiện bất thường, giải thích căn cứ rủi ro và hỗ trợ ra quyết định tài chính an toàn.

🔒 Ràng buộc: HITL BẮT BUỘC trước khi agent thực hiện thay khách các thao tác nhạy cảm (nâng hạng KYC, liên kết ngân hàng, thay đổi hạn mức); CẤM LLM bịa hạn mức/chính sách — RAG từ tài liệu chính thức có trích dẫn; xác thực danh tính trước tác vụ nhạy cảm; tuân thủ PDPA & NHNN; cảnh báo khi ngoài phạm vi hỗ trợ.

### 🛠️ Tech Stack
• LLM đối thoại + lập kế hoạch onboarding
• LangGraph điều phối agent theo trạng thái + tool-calling
• RAG tài liệu nghiệp vụ (vector DB)
• code tool kiểm tra trạng thái tài khoản/hạn mức (API mô phỏng)
• backend FastAPI
• PostgreSQL
• frontend React (wizard + chat)
• deploy cloud.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu phòng chống tội phạm tài chính PaySim (giao dịch ví di động), IEEE-CIS Fraud Detection, IBM AMLSim / Elliptic Graph Dataset (đồ thị luồng tiền rửa tiền) và CelebA-Spoof / MIDV-500 (cho eKYC).

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập, vai trò người dùng mới/admin
• agent dẫn dắt onboarding theo trạng thái mô phỏng, giải đáp nghiệp vụ có trích dẫn, kiểm tra tác vụ hoàn thành.

Nâng cao:
• Agent chủ động đề xuất bước tiếp theo cá nhân hóa, thực hiện tác vụ thay khách với HITL phê duyệt, memory tiến trình onboarding, cảnh báo ngoài phạm vi/chuyển người, đo tỷ lệ hoàn tất, xử lý lỗi luồng
• Kết hợp mô hình định lượng/đồ thị hoặc bộ giải tối ưu hóa tài chính xác định với tác tử điều tra/tư vấn có giải thích minh bạch, kiểm định chặt chẽ tỷ lệ báo động giả và độ an toàn trên tập dữ liệu chuẩn.

---
