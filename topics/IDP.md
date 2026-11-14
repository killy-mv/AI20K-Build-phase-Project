# Lĩnh vực: IDP - Intelligent Document Processing – Xử lý tài liệu doanh nghiệp

> Tổng số đề tài: **15 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `IDP-01` | [InvoiceReader VN - Đọc hóa đơn GTGT điện tử dạng PDF (có text layer) thành bản ghi có cấu trúc, mỗi trường kèm bằng chứng và độ tin cậy](#idp-01) |
| `IDP-02` | [ScanInvoice VN - Đọc hóa đơn GTGT dạng scan hoặc ảnh chụp (xoay nghiêng, dấu mộc, chữ viết tay) thành bản ghi có cấu trúc kèm độ tin cậy](#idp-02) |
| `IDP-03` | [PriceSheet Normalizer - Chuẩn hóa bảng giá và bảng kê Excel của nhà cung cấp (nhiều bố cục) thành một bảng chuẩn, tự tìm dòng tiêu đề của từng sheet](#idp-03) |
| `IDP-04` | [DeliveryNote Reader - Đọc phiếu giao hàng của nhà cung cấp thành dòng hàng (hàng hóa, đơn vị, số lượng) sẵn sàng cho đối chiếu tồn kho](#idp-04) |
| `IDP-05` | [ClaimDossier Splitter - Tách và phân loại hồ sơ bồi thường bảo hiểm gồm nhiều tài liệu trong một tệp, rồi trích các trường chính của từng tài liệu](#idp-05) |
| `IDP-06` | [DriverDocs Check - Đọc bộ giấy tờ đăng ký tài xế (căn cước, giấy phép lái xe, giấy tờ xe) và kiểm tra tính hợp lệ của từng trường](#idp-06) |
| `IDP-07` | [HandoverCheck - Đọc giấy tờ bàn giao xe, kiểm tra thông tin xe/người mua/ngày tháng và phát hiện chữ ký hoặc trang bị thiếu](#idp-07) |
| `IDP-08` | [Template Studio - Đề xuất mẫu trích xuất (template) mới từ 3-5 tài liệu mẫu đã gán nhãn, người duyệt phê duyệt trước khi đưa vào dùng](#idp-08) |
| `IDP-09` | [EvidenceView - Màn hình duyệt tài liệu hiển thị mỗi trường trích xuất kèm khung vị trí trên ảnh trang để người duyệt kiểm tra trong một cái nhìn](#idp-09) |
| `IDP-10` | [DocSplitter - Tìm điểm bắt đầu và kết thúc của từng tài liệu trong một tệp PDF gộp, đánh giá theo từng ranh giới](#idp-10) |
| `IDP-11` | [CheapPath Router - Định tuyến trang có text layer sang parser rẻ, chỉ trang scan mới dùng mô hình thị giác, và chứng minh khoản tiết kiệm bằng số đo](#idp-11) |
| `IDP-12` | [CorrectionLoop - Cập nhật template hoặc ví dụ few-shot từ lần sửa của người duyệt và đo mức cải thiện trên tập giữ riêng](#idp-12) |
| `IDP-13` | [StatementReader - Đọc sao kê ngân hàng dạng PDF hoặc ảnh thành bảng giao dịch chuẩn (ngày, mô tả, ghi nợ/ghi có, số dư) có kiểm tra số dư chạy](#idp-13) |
| `IDP-14` | [ContractFields - Trích các thông tin chính của hợp đồng dịch vụ/mua bán (các bên, ngày, giá trị, thời hạn, điều khoản thanh toán) kèm trích dẫn nguồn trong văn bản](#idp-14) |
| `IDP-15` | [Template Registry - Quản lý vòng đời mẫu trích xuất (phiên bản, kiểm thử hồi quy, phát hiện trôi lệch khi nhà cung cấp đổi mẫu chứng từ)](#idp-15) |

---

## [IDP-01] InvoiceReader VN - Đọc hóa đơn GTGT điện tử dạng PDF (có text layer) thành bản ghi có cấu trúc, mỗi trường kèm bằng chứng và độ tin cậy

### 📝 Mô tả đề tài
📍 Thực trạng: Nhà cung cấp gửi hóa đơn GTGT điện tử cho hàng chục pháp nhân trong tập đoàn; cùng một trường (số hóa đơn, mã số thuế, tổng tiền) nằm ở vị trí khác nhau theo từng mẫu của từng nhà cung cấp nên kế toán vẫn phải nhập tay. Một mã số thuế hoặc tổng tiền sai lọt qua tốn công sửa ở khâu sau hơn nhiều so với việc đọc chậm.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng ứng dụng nhận hóa đơn PDF có text layer và trả về bản ghi có cấu trúc (đầu hóa đơn, bên bán/bên mua, mã số thuế, dòng hàng, thuế GTGT, tổng cộng), mỗi trường kèm bằng chứng (trích đoạn nguồn) và độ tin cậy đã được đo; các trường không chắc chắn chuyển cho người duyệt, sửa của người duyệt được lưu lại để lần sau đọc tốt hơn; mẫu hóa đơn mới là một template mới chứ không phải một bản phát hành code mới; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng hóa đơn công khai hoặc do nhóm tự sinh, tuyệt đối không có chứng từ thật của doanh nghiệp trong repo, prompt, log hay demo; kiểm tra số học (tổng tiền, thuế) và định dạng (mã số thuế, ngày) do code đảm nhiệm, không giao cho mô hình; mô hình chỉ chỉ ra giá trị nằm ở đâu, code sao chép giá trị từ văn bản gốc; độ tin cậy là điểm đã được hiệu chuẩn trên golden set chứ không phải điểm mô hình tự báo; báo cáo accuracy theo từng trường kèm n và tỷ lệ confident-wrong, chi phí US$/trang và chi phí theo tháng ở khối lượng thực tế nêu rõ; không bao giờ trả kết quả rỗng một cách im lặng; không tự động hạch toán.

### 🛠️ Tech Stack
• Python, FastAPI
• PyMuPDF/pdfplumber để lấy text layer và tọa độ
• LLM/VLM có structured output (Claude, GPT, Gemini hoặc Qwen2.5-VL mã nguồn mở) để chỉ vị trí giá trị
• Pydantic/JSON Schema để mô tả template và kiểm tra dữ liệu
• bộ sinh hóa đơn tổng hợp theo định dạng hóa đơn điện tử công khai của Việt Nam (ReportLab/WeasyPrint, Faker)
• bộ dữ liệu biểu mẫu/biên lai công khai (FUNSD, CORD, SROIE, MC-OCR) để tham khảo bố cục
• pytest + ghi lại lời gọi mô hình (fixtures) để test không gọi mô hình thật
• PostgreSQL/SQLite
• React/Next.js + PDF.js cho màn hình duyệt
• Langfuse để đo token và chi phí
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• một lệnh chạy hóa đơn từ đầu vào đến bản ghi trên bản clone sạch; golden set 50-150 hóa đơn tổng hợp (có ca khó: nhiều dòng hàng, nhiều mức thuế suất, số tiền ngắt dòng, mã số thuế sai định dạng) kèm n; kiểm tra số học/định dạng bằng code; màn hình duyệt các trường dưới ngưỡng, ≥2 vai trò (kế toán duyệt và người quản lý), báo cáo accuracy theo từng trường, tỷ lệ confident-wrong và chi phí US$/trang.

Nâng cao:
• hiệu chuẩn độ tin cậy và chọn ngưỡng bằng đường cong rủi ro - độ phủ (tỷ lệ tự động qua mà không sai), thêm template cho ≥3 nhà cung cấp mới mà không sửa code, so sánh ≥2 mô hình đọc theo chất lượng/chi phí, held-out set giữ riêng từ ngày đầu để tránh đánh giá trên chính tài liệu dùng dựng template, báo cáo chi phí theo tháng ở khối lượng thực tế và đường rẻ nhất vẫn đạt acceptance.

---

## [IDP-02] ScanInvoice VN - Đọc hóa đơn GTGT dạng scan hoặc ảnh chụp (xoay nghiêng, dấu mộc, chữ viết tay) thành bản ghi có cấu trúc kèm độ tin cậy

### 📝 Mô tả đề tài
📍 Thực trạng: Rất nhiều hóa đơn vẫn đến dưới dạng ảnh chụp bằng điện thoại hoặc bản scan: nghiêng, mờ, có dấu mộc đè lên số, có ghi chú viết tay, đôi khi lộn ngược trang. Nếu coi 'đọc scan' là bài toán OCR thuần thì lỗi một chữ số trong tổng tiền hay mã số thuế vẫn lọt đến kế toán với vẻ ngoài rất tự tin.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng pipeline đọc hóa đơn dạng ảnh/scan: tiền xử lý (xoay, chỉnh nghiêng), đọc chữ (OCR hoặc mô hình thị giác), trích các trường như bài đọc PDF có text layer, và chỉ rõ trường nào đọc từ vùng bị nhiễu (dấu mộc, chữ tay); đo chất lượng theo từng mức suy giảm ảnh để biết hệ thống đáng tin đến đâu và khi nào phải chuyển cho người duyệt; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng hóa đơn công khai hoặc tự sinh rồi in ra và chụp lại, không dùng chứng từ thật; kiểm tra số học và định dạng do code đảm nhiệm, kết quả OCR không được tin hơn phép cộng; mô hình chỉ chỉ ra giá trị ở đâu, code sao chép từ văn bản đọc được; độ tin cậy phải được hiệu chuẩn trên golden set, không dùng điểm tự báo của mô hình; báo cáo accuracy theo trường và theo mức suy giảm ảnh kèm n, tỷ lệ confident-wrong, chi phí US$/trang; nhóm không dành sprint 1 để huấn luyện OCR mới, hướng đi bắt đầu từ PDF text layer rồi nâng lên scan.

### 🛠️ Tech Stack
• Python, FastAPI
• OpenCV (deskew, perspective correction), Augraphy để mô phỏng suy giảm ảnh
• Tesseract/PaddleOCR/VietOCR cho OCR tiếng Việt
• VLM đọc ảnh (Qwen2.5-VL, Claude, GPT, Gemini) làm phương án so sánh
• bộ sinh hóa đơn tổng hợp rồi in và chụp lại bằng điện thoại
• SROIE, CORD, MC-OCR làm dữ liệu tham khảo
• Pydantic để kiểm tra trường
• pytest + fixtures ghi sẵn lời gọi mô hình
• React/Next.js + PDF.js/canvas cho màn hình duyệt
• Langfuse đo chi phí
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• một lệnh chạy ảnh hóa đơn đến bản ghi; golden set 50-150 ảnh hóa đơn tổng hợp có ca khó (nghiêng, mờ, dấu mộc đè số, chữ tay) kèm n; màn hình duyệt trường dưới ngưỡng, ≥2 vai trò, báo cáo accuracy theo trường và theo loại suy giảm, tỷ lệ confident-wrong, chi phí US$/trang.

Nâng cao:
• so sánh OCR + trích bằng luật/mô hình với VLM đọc trực tiếp theo chất lượng và chi phí, hiệu chuẩn độ tin cậy riêng cho vùng bị dấu mộc/chữ tay, đường cong accuracy theo mức suy giảm để đề xuất 'ảnh đủ tốt để tự động', định tuyến trang sạch sang đường rẻ, tăng độ bền cho ảnh chụp lộn ngược/nhiều trang, báo cáo chi phí theo tháng
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-03] PriceSheet Normalizer - Chuẩn hóa bảng giá và bảng kê Excel của nhà cung cấp (nhiều bố cục) thành một bảng chuẩn, tự tìm dòng tiêu đề của từng sheet

### 📝 Mô tả đề tài
📍 Thực trạng: Nhà cung cấp gửi bảng giá và bảng kê bằng Excel với muôn hình muôn vẻ: dòng tiêu đề nằm ở hàng 3 hoặc hàng 9, ô gộp, tiêu đề nhiều tầng, đơn vị nằm trong tiêu đề, nhiều sheet, dòng ghi chú xen kẽ, dòng tổng cộng lẫn trong dữ liệu; nhân viên phải sao chép và chỉnh tay từng file trước khi dùng được.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ nhận file Excel, tìm dòng tiêu đề của từng sheet, ánh xạ cột về lược đồ chuẩn (mã hàng, tên hàng, đơn vị, đơn giá, tiền tệ, hiệu lực từ ngày), loại bỏ dòng ghi chú và dòng tổng, chuẩn hóa số và ngày, rồi xuất một bảng chuẩn duy nhất kèm bằng chứng (ô nguồn) và độ tin cậy cho từng ánh xạ; ánh xạ không chắc chắn chuyển cho người duyệt; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng bảng giá công khai hoặc do nhóm tự sinh nhiều bố cục khác nhau, không dùng bảng giá thật của nhà cung cấp; phân tích số (định dạng 1.234,56 so với 1,234.56), đơn vị, ngày và kiểm tra tổng do code đảm nhiệm; mô hình chỉ đề xuất ánh xạ cột/dòng tiêu đề còn giá trị được code sao chép từ ô nguồn, không để mô hình gõ lại số; không trả bảng rỗng một cách im lặng khi không tìm thấy dòng tiêu đề, phải nêu rõ; báo cáo accuracy theo từng loại (tìm dòng tiêu đề, ánh xạ cột, giá trị ô) kèm n, số dòng bị mất/nhân đôi, chi phí US$/file.

### 🛠️ Tech Stack
• Python, FastAPI
• openpyxl/pandas/xlrd để đọc Excel (kể cả ô gộp và dòng ẩn)
• LLM có structured output để đề xuất ánh xạ cột và dòng tiêu đề
• RapidFuzz để so khớp tên cột/từ đồng nghĩa
• Pydantic/pandera để kiểm tra lược đồ chuẩn
• bộ sinh bảng giá tổng hợp nhiều bố cục (Faker + openpyxl)
• pytest + fixtures lời gọi mô hình
• PostgreSQL/SQLite
• React/Next.js (xem ô nguồn và bảng chuẩn cạnh nhau)
• Langfuse
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• một lệnh chạy một file Excel nhiều sheet ra bảng chuẩn; golden set 50-150 file tổng hợp có ca khó (tiêu đề ở dòng lệch, ô gộp, tiêu đề nhiều tầng, đơn vị trong tiêu đề, dòng tổng lẫn dữ liệu) kèm n; màn hình duyệt ánh xạ không chắc chắn, ≥2 vai trò, báo cáo accuracy theo loại lỗi và chi phí US$/file.

Nâng cao:
• học ánh xạ từ lần sửa của người duyệt để lần sau không hỏi lại, xử lý quy đổi đơn vị và tiền tệ bằng bảng quy tắc có phiên bản, phát hiện bảng giá có dòng trùng hoặc thiếu so với phiên bản trước, so sánh đường 'luật trước, mô hình sau' với 'mô hình cho tất cả' về chi phí/chất lượng, báo cáo chi phí theo tháng ở khối lượng thực tế
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-04] DeliveryNote Reader - Đọc phiếu giao hàng của nhà cung cấp thành dòng hàng (hàng hóa, đơn vị, số lượng) sẵn sàng cho đối chiếu tồn kho

### 📝 Mô tả đề tài
📍 Thực trạng: Mỗi tháng bộ phận kho và kế toán của khối khách sạn - nghỉ dưỡng nhận hàng trăm phiếu giao hàng từ nhiều nhà cung cấp thực phẩm và vật tư: tên hàng viết tắt, đơn vị lúc là thùng lúc là kg, số lượng ghi tay, chữ ký đè lên bảng; việc nhập tay các dòng này để đối chiếu với tồn kho vừa chậm vừa dễ sai.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng ứng dụng đọc phiếu giao hàng (PDF text layer, ảnh hoặc scan) thành các dòng hàng có cấu trúc gồm tên hàng, đơn vị, số lượng (và đơn giá nếu có), kèm bằng chứng vị trí trên trang và độ tin cậy từng dòng; chuẩn hóa đơn vị bằng bảng quy tắc, kiểm tra tính hợp lý (số lượng dương, đơn vị hợp lệ, tổng khớp nếu có) và chuyển các dòng không chắc chắn cho thủ kho duyệt; đầu ra sẵn sàng để đối chiếu tồn kho ở bước sau; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng phiếu giao hàng công khai hoặc do nhóm tự sinh, không dùng chứng từ thật; việc đối chiếu với tồn kho nằm ngoài phạm vi bài này, bài chỉ đọc và chuẩn bị dữ liệu; chuẩn hóa đơn vị và kiểm tra số học do code đảm nhiệm, mô hình chỉ chỉ ra giá trị ở đâu và code sao chép từ văn bản; không bỏ sót dòng hàng một cách im lặng (đếm số dòng đọc được so với số dòng hệ thống nhận ra); báo cáo accuracy theo trường và theo dòng kèm n, tỷ lệ confident-wrong, chi phí US$/trang.

### 🛠️ Tech Stack
• Python, FastAPI
• PyMuPDF/pdfplumber cho phiếu có text layer; OCR (PaddleOCR/Tesseract) hoặc VLM cho phiếu scan
• LLM/VLM có structured output
• nhận diện bảng (Table Transformer, Docling hoặc Camelot/pdfplumber)
• RapidFuzz để chuẩn hóa tên hàng và đơn vị
• bộ sinh phiếu giao hàng tổng hợp nhiều bố cục (ReportLab, Faker)
• Pydantic để kiểm tra
• pytest + fixtures
• React/Next.js + PDF.js màn hình duyệt cho thủ kho
• Langfuse
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• một lệnh chạy phiếu giao hàng ra danh sách dòng hàng; golden set 50-150 phiếu tổng hợp có ca khó (tên viết tắt, nhiều đơn vị, số lượng viết tay, giao một phần, bảng ngắt trang) kèm n; màn hình duyệt dòng không chắc chắn, ≥2 vai trò (thủ kho và kế toán), báo cáo accuracy theo trường/dòng, tỷ lệ confident-wrong và chi phí US$/trang.

Nâng cao:
• từ điển đồng nghĩa tên hàng học dần từ lần duyệt của thủ kho, xử lý phiếu giao một phần và phiếu nhiều trang, đường đi rẻ cho phiếu có text layer và đường thị giác cho phiếu scan, đo tỷ lệ phiếu tự động qua mà không sai, báo cáo chi phí theo tháng ở khối lượng thực tế
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-05] ClaimDossier Splitter - Tách và phân loại hồ sơ bồi thường bảo hiểm gồm nhiều tài liệu trong một tệp, rồi trích các trường chính của từng tài liệu

### 📝 Mô tả đề tài
📍 Thực trạng: Một hồ sơ bồi thường bảo hiểm y tế thường được nộp thành một tệp PDF gộp: đơn yêu cầu, hóa đơn viện phí, đơn thuốc, kết quả xét nghiệm, giấy ra viện, đôi khi cả trang scan dấu mộc; chuyên viên mất nhiều thời gian chỉ để xác định tài liệu nào bắt đầu và kết thúc ở đâu, thiếu tài liệu nào, rồi mới đọc từng cái.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng ứng dụng nhận một tệp hồ sơ gộp, tách thành các tài liệu riêng (chỉ ra ranh giới), phân loại từng tài liệu (đơn yêu cầu, hóa đơn, đơn thuốc, kết quả xét nghiệm, giấy ra viện...), trích các trường chính theo từng loại với bằng chứng và độ tin cậy, báo hồ sơ còn thiếu loại tài liệu nào theo danh mục yêu cầu; các ranh giới hoặc trường không chắc chắn chuyển cho chuyên viên duyệt; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng hồ sơ hoàn toàn tổng hợp với danh tính và thông tin y tế giả, không có dữ liệu bệnh nhân hay hồ sơ thật nào trong repo, prompt, log hay demo; bài này chỉ đọc, tách và phân loại, việc quyết định hồ sơ có đủ điều kiện chi trả nằm ngoài phạm vi và thuộc về người có thẩm quyền; mô hình phân loại/chỉ vị trí, kiểm tra định dạng và phép tính do code đảm nhiệm; đo ranh giới theo từng ranh giới (precision/recall/F1 kèm n), độ chính xác phân loại, accuracy trường và tỷ lệ confident-wrong; chi phí US$/hồ sơ; không để lọt thông tin cá nhân vào log.

### 🛠️ Tech Stack
• Python, FastAPI
• PyMuPDF để tách trang và lấy text/ảnh trang
• phân loại trang/tài liệu: LLM/VLM few-shot hoặc LayoutLMv3/Donut tinh chỉnh (RVL-CDIP để khởi tạo)
• phát hiện ranh giới: đặc trưng trang (tiêu đề, số trang 'trang 1/n', mẫu đầu trang) + mô hình
• OCR (PaddleOCR/Tesseract) cho trang scan
• bộ sinh hồ sơ gộp tổng hợp (ReportLab/Faker + ghép tệp)
• Pydantic/JSON Schema
• pytest + fixtures
• React/Next.js + PDF.js (hiển thị ranh giới tách)
• Langfuse
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• một lệnh chạy một tệp hồ sơ gộp ra danh sách tài liệu đã tách + loại + trường chính; golden set 50-150 hồ sơ tổng hợp có ca khó (tài liệu nhiều trang, trang trắng, trang scan dấu mộc, hai tài liệu cùng loại nối nhau) kèm n; màn hình duyệt ranh giới và trường không chắc chắn, ≥2 vai trò (chuyên viên và trưởng nhóm), báo cáo F1 ranh giới, độ chính xác phân loại, accuracy trường, chi phí US$/hồ sơ.

Nâng cao:
• phát hiện hồ sơ thiếu tài liệu theo danh mục yêu cầu, hiệu chuẩn độ tin cậy ranh giới và loại, so sánh phân loại bằng mô hình nhỏ tinh chỉnh với LLM/VLM few-shot theo chi phí/chất lượng, xử lý tệp nhiều trăm trang, định tuyến trang có text layer sang đường rẻ, báo cáo chi phí theo tháng ở khối lượng thực tế
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-06] DriverDocs Check - Đọc bộ giấy tờ đăng ký tài xế (căn cước, giấy phép lái xe, giấy tờ xe) và kiểm tra tính hợp lệ của từng trường

### 📝 Mô tả đề tài
📍 Thực trạng: Khi tuyển và đăng ký tài xế cho dịch vụ gọi xe, nhân viên phải nhập tay thông tin từ căn cước, giấy phép lái xe và giấy tờ xe, rồi kiểm tra bằng mắt hạn giấy phép, hạng bằng, tên có khớp giữa các giấy tờ hay không; khối lượng lớn vào mùa tuyển khiến sai sót dễ xảy ra và hồ sơ chờ xử lý lâu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng ứng dụng đọc ảnh/PDF bộ giấy tờ của tài xế, trích các trường (họ tên, ngày sinh, số giấy tờ, hạng bằng, ngày hết hạn, biển số, đăng kiểm/bảo hiểm nếu có), kèm bằng chứng vị trí và độ tin cậy, rồi chạy các kiểm tra hợp lệ bằng code (định dạng số giấy tờ, ngày hợp lệ, giấy phép còn hạn, hạng bằng phù hợp loại xe, họ tên và ngày sinh khớp giữa các giấy tờ); các trường không chắc chắn hoặc không khớp chuyển cho nhân viên duyệt; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng danh tính hoàn toàn tổng hợp (giấy tờ do nhóm tự sinh với tên, số giấy tờ và ảnh giả), tuyệt đối không dùng giấy tờ thật của bất kỳ ai; hệ thống chỉ đề xuất, nhân viên mới quyết định có chấp nhận tài xế, không có đường tự động phê duyệt; mọi kiểm tra hợp lệ do code thực hiện và giải thích được; dữ liệu cá nhân (dù tổng hợp) được che trong log; báo cáo accuracy theo trường kèm n, tỷ lệ confident-wrong và tỷ lệ phát hiện đúng giấy tờ không hợp lệ/không khớp được cài chủ đích, chi phí US$/hồ sơ.

### 🛠️ Tech Stack
• Python, FastAPI
• OpenCV (chỉnh nghiêng/xoay), PaddleOCR/VietOCR/Tesseract
• VLM đọc ảnh giấy tờ có structured output
• Pydantic + bộ kiểm tra hợp lệ (định dạng số giấy tờ, ngày, hạng bằng) viết bằng code
• bộ sinh giấy tờ tổng hợp (Pillow/Faker + nền mẫu tự thiết kế, không sao chép giấy tờ thật) và chụp lại để tạo ca khó
• pytest + fixtures
• PostgreSQL
• React/Next.js màn hình duyệt (ảnh + trường + kết quả kiểm tra)
• Langfuse
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• một lệnh chạy bộ giấy tờ tổng hợp ra bản ghi tài xế + kết quả kiểm tra; golden set 50-150 bộ giấy tờ tổng hợp có ca khó (ảnh mờ/lóa, hết hạn, sai hạng bằng, tên khác giữa hai giấy tờ) kèm n; màn hình duyệt cho nhân viên với các cờ cảnh báo, ≥2 vai trò (nhân viên duyệt và quản lý), báo cáo accuracy trường, tỷ lệ phát hiện bất thường và confident-wrong, chi phí US$/hồ sơ.

Nâng cao:
• đối chiếu liên giấy tờ (tên, ngày sinh, số giấy tờ) với dung sai chính tả tiếng Việt (dấu, viết hoa/thường), nhận diện ảnh bị chỉnh sửa ở mức cơ bản trên dữ liệu tổng hợp, hiệu chuẩn độ tin cậy theo chất lượng ảnh, nhật ký quyết định của nhân viên, định tuyến ảnh sạch sang đường rẻ, báo cáo chi phí theo tháng ở khối lượng tuyển dụng thực tế
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-07] HandoverCheck - Đọc giấy tờ bàn giao xe, kiểm tra thông tin xe/người mua/ngày tháng và phát hiện chữ ký hoặc trang bị thiếu

### 📝 Mô tả đề tài
📍 Thực trạng: Mỗi xe bàn giao cho khách kèm một bộ giấy tờ: biên bản bàn giao, phiếu kiểm tra xe, giấy xác nhận; nhân viên đại lý và bộ phận hậu kiểm phải kiểm tra từng bộ xem thông tin xe, người mua và ngày tháng có khớp, có đủ chữ ký, có thiếu trang nào hay không. Làm thủ công từng tài liệu nên chậm, và sót lỗi thường chỉ bị phát hiện khi đã phát sinh khiếu nại.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng ứng dụng đọc bộ giấy tờ bàn giao xe (PDF/scan), trích thông tin xe (mẫu xe, số khung, màu), người mua, các ngày quan trọng và trạng thái từng ô chữ ký (có/thiếu), kiểm tra bằng code tính nhất quán (số khung đúng định dạng, các ngày hợp logic, thông tin khớp giữa các tài liệu trong bộ, đủ trang), và xuất báo cáo 'đủ/thiếu' có bằng chứng; mục không chắc chắn chuyển cho người hậu kiểm; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng giấy tờ tổng hợp do nhóm tự thiết kế, không dùng hồ sơ bàn giao thật hay thông tin khách hàng thật; chỉ báo có/thiếu chữ ký chứ không xác thực chữ ký là của ai; kiểm tra định dạng số khung, logic ngày tháng và khớp thông tin do code đảm nhiệm; bài này chỉ đọc và kiểm tra, không tự quyết định bàn giao hợp lệ hay không (người hậu kiểm quyết định); đo accuracy trường, precision/recall phát hiện chữ ký có/thiếu, tỷ lệ confident-wrong kèm n, chi phí US$/bộ hồ sơ.

### 🛠️ Tech Stack
• Python, FastAPI
• PyMuPDF, OpenCV
• VLM/mô hình phát hiện đối tượng (YOLO/Grounding DINO) để phát hiện vùng chữ ký/dấu
• OCR (PaddleOCR/Tesseract) và LLM/VLM có structured output để trích trường
• Pydantic + kiểm tra số khung (17 ký tự theo chuẩn VIN), ngày tháng
• bộ sinh biên bản bàn giao tổng hợp (có/không chữ ký, thiếu trang) bằng ReportLab/Pillow
• pytest + fixtures
• PostgreSQL
• React/Next.js + PDF.js (khung đánh dấu ô chữ ký)
• Langfuse
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• một lệnh chạy một bộ giấy tờ bàn giao tổng hợp ra bản ghi + danh sách mục thiếu; golden set 50-150 bộ có ca khó (thiếu chữ ký, thiếu trang, ngày sai logic, số khung sai định dạng, thông tin lệch giữa hai tài liệu) kèm n; màn hình hậu kiểm hiển thị bằng chứng trên ảnh trang, ≥2 vai trò (nhân viên đại lý và người hậu kiểm), báo cáo accuracy, precision/recall chữ ký có/thiếu, chi phí US$/bộ.

Nâng cao:
• đối chiếu thông tin xuyên các tài liệu trong bộ và giải thích từng điểm không khớp bằng một câu có trích dẫn, hiệu chuẩn độ tin cậy phát hiện chữ ký theo chất lượng scan, so sánh phát hiện bằng mô hình thị giác chuyên biệt với VLM tổng quát về chi phí/chất lượng, báo cáo tỷ lệ bộ hồ sơ tự động qua và chi phí theo tháng ở khối lượng thực tế
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-08] Template Studio - Đề xuất mẫu trích xuất (template) mới từ 3-5 tài liệu mẫu đã gán nhãn, người duyệt phê duyệt trước khi đưa vào dùng

### 📝 Mô tả đề tài
📍 Thực trạng: Khi xuất hiện một loại biểu mẫu mới, trước đây phải có kỹ sư viết code riêng; từng có lần xây 1.200 template bằng tay mất 11 người trong 25 ngày. Cái cần là một nơi mà 'biểu mẫu mới' chỉ là 'template mới' do chuyên viên nghiệp vụ tạo từ vài tài liệu mẫu, không phải một bản phát hành phần mềm mới.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ nhận 3-5 tài liệu mẫu đã được gán nhãn các trường cần lấy, tự đề xuất một template trích xuất (vị trí/ngữ cảnh/quy tắc nhận diện từng trường kèm kiểu dữ liệu và kiểm tra định dạng), chạy thử trên các tài liệu cùng loại, hiển thị kết quả để người duyệt chỉnh và phê duyệt, rồi mới đưa template vào dùng và lưu có phiên bản; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: template do mô hình đề xuất không được áp dụng khi chưa có người duyệt phê duyệt, mọi phê duyệt được ghi nhật ký; chỉ dùng tài liệu công khai hoặc tự sinh; template phải đo được trên tập giữ riêng (held-out) gồm các tài liệu cùng loại mà mô hình chưa thấy khi dựng template, tránh báo cáo accuracy trên chính tài liệu đã dùng dựng; mô hình chỉ chỉ ra vị trí/quy tắc, giá trị được code sao chép từ văn bản; báo cáo accuracy theo trường kèm n, chi phí US$ cho mỗi lần dựng template và thời gian từ mẫu đến template dùng được.

### 🛠️ Tech Stack
• Python, FastAPI
• LLM/VLM có structured output để suy ra quy tắc từ mẫu đã gán nhãn
• PyMuPDF/pdfplumber, OCR khi cần
• định dạng template dạng JSON/YAML có phiên bản (Pydantic/JSON Schema)
• Git/DVC hoặc PostgreSQL để lưu phiên bản template
• bộ sinh tài liệu cùng loại nhiều biến thể (Faker, ReportLab) để làm tập kiểm tra
• pytest + fixtures
• React/Next.js + PDF.js (công cụ gán nhãn và duyệt template)
• Langfuse
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app cho phép tải 3-5 tài liệu mẫu, gán nhãn trường, nhận template đề xuất, chạy thử trên ≥20 tài liệu cùng loại giữ riêng, hiển thị accuracy theo trường (kèm n), ≥2 vai trò (chuyên viên nghiệp vụ tạo/duyệt và quản trị), phê duyệt trước khi dùng và lưu phiên bản; có một lệnh chạy end-to-end trên bản clone sạch.

Nâng cao:
• so sánh template do mô hình đề xuất với template viết tay (accuracy, thời gian tạo, chi phí), đo accuracy theo số mẫu (3, 4, 5) để biết cần bao nhiêu mẫu, tự đề xuất sửa template khi chạy thử còn sai, kiểm tra hồi quy khi chỉnh template, quản lý phiên bản và quay lui, báo cáo chi phí theo tháng với giả định số template mới mỗi tháng
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-09] EvidenceView - Màn hình duyệt tài liệu hiển thị mỗi trường trích xuất kèm khung vị trí trên ảnh trang để người duyệt kiểm tra trong một cái nhìn

### 📝 Mô tả đề tài
📍 Thực trạng: Câu hỏi đầu tiên của kế toán và chuyên viên nghiệp vụ là 'tôi kiểm tra được không?'. Nếu hệ thống trả ra giá trị mà không chỉ nó nằm ở đâu trên trang, người duyệt phải tự lục lại tài liệu, nên chậm và họ dần mất niềm tin hoặc duyệt ẩu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng màn hình duyệt (reviewer workbench) cho kết quả trích xuất: mỗi trường hiển thị giá trị, độ tin cậy và khung bao (bounding box) trên ảnh trang gốc; bấm vào trường thì trang cuộn đến đúng vùng; người duyệt chấp nhận, sửa hoặc từ chối từng trường; trường không có bằng chứng định vị được bị đánh dấu rõ; mọi thao tác được ghi nhật ký; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng tài liệu công khai hoặc tự sinh; một giá trị không có bằng chứng định vị phải bị gắn cờ chứ không được hiển thị như đã được xác nhận; không có đường nào để tiền hoặc quyết định đi tiếp mà không qua người duyệt ở các trường bị gắn cờ; đo độ chính xác của khung bằng IoU so với nhãn, tỷ lệ trường có bằng chứng, và thời gian duyệt trung bình mỗi tài liệu khi có và không có bằng chứng (đo trên người thử nghiệm với n nêu rõ); báo cáo kèm n.

### 🛠️ Tech Stack
• Python, FastAPI
• PyMuPDF/pdfplumber (tọa độ từ text layer), OCR có tọa độ (PaddleOCR/Tesseract) cho trang scan
• so khớp giá trị với từ/dòng trên trang để suy ra khung bao
• LLM/VLM có structured output
• React/Next.js + PDF.js/react-pdf, lớp phủ canvas/SVG
• PostgreSQL lưu nhật ký thao tác duyệt
• bộ tài liệu tổng hợp kèm nhãn khung (sinh bằng ReportLab để biết tọa độ chính xác)
• pytest + Playwright (kiểm thử giao diện)
• Langfuse
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app hiển thị trang tài liệu với khung bao cho từng trường, bấm trường để nhảy đến vùng, nút chấp nhận/sửa/từ chối, nhật ký thao tác, ≥2 vai trò (người duyệt và quản lý xem nhật ký), báo cáo IoU khung và tỷ lệ trường có bằng chứng trên golden set 50-150 tài liệu.

Nâng cao:
• đo thực nghiệm thời gian duyệt có và không có bằng chứng với nhóm người thử và n rõ ràng, xử lý giá trị trải nhiều dòng/nhiều vùng, sắp xếp thứ tự duyệt theo mức rủi ro, phím tắt và duyệt hàng loạt có kiểm soát, so sánh lấy khung từ text layer với lấy từ OCR/VLM theo chất lượng và chi phí
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-10] DocSplitter - Tìm điểm bắt đầu và kết thúc của từng tài liệu trong một tệp PDF gộp, đánh giá theo từng ranh giới

### 📝 Mô tả đề tài
📍 Thực trạng: Chứng từ thường được nộp theo lô: một tệp PDF gộp hóa đơn, phiếu giao hàng và ảnh scan dấu mộc nối liền nhau; hóa đơn có thể dài 1-3 trang, có trang trắng xen kẽ, hai hóa đơn cùng nhà cung cấp nối nhau trông gần như giống hệt. Nếu tách sai ranh giới thì tất cả các bước đọc phía sau đều sai, mà lỗi lại khó thấy.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ nhận tệp gộp và xác định ranh giới từng tài liệu (trang bắt đầu, trang kết thúc), kèm loại tài liệu của mỗi đoạn và độ tin cậy cho từng ranh giới; hiển thị các ranh giới trên dải ảnh thu nhỏ các trang để người duyệt kéo chỉnh; ranh giới không chắc chắn chuyển cho người duyệt trước khi cắt tệp thành các tài liệu riêng; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng tệp gộp tổng hợp do nhóm tự ghép từ tài liệu công khai/tự sinh, không dùng lô chứng từ thật; ranh giới là kết quả được đo theo từng ranh giới (không chỉ accuracy trên cả tệp) với precision/recall/F1 kèm n; phải phân biệt lỗi cắt thừa với lỗi bỏ sót vì hậu quả khác nhau; việc cắt tệp và chuyển tiếp chỉ diễn ra sau khi người duyệt chấp nhận các ranh giới bị gắn cờ; chi phí US$ trên mỗi trăm trang được báo cáo; không trả kết quả 'một tài liệu duy nhất' một cách im lặng khi không chắc.

### 🛠️ Tech Stack
• Python, FastAPI
• PyMuPDF để lấy ảnh/text từng trang và tách tệp
• đặc trưng trang: tiêu đề, 'trang x/y', mẫu đầu trang, nhà cung cấp, độ giống trang liền trước (embedding ảnh/văn bản)
• phân loại trang/ranh giới bằng LLM/VLM few-shot hoặc mô hình nhỏ (LayoutLMv3, scikit-learn/LightGBM trên đặc trưng)
• OCR cho trang scan (PaddleOCR/Tesseract)
• bộ ghép tệp gộp tổng hợp có kiểm soát (ca khó: trang trắng, tài liệu nhiều trang, hai tài liệu giống nhau nối nhau)
• pytest + fixtures
• React/Next.js (dải thumbnail + ranh giới kéo thả)
• Langfuse
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• một lệnh chạy tệp gộp ra danh sách đoạn tài liệu (trang đầu, trang cuối, loại); golden set 50-150 tệp gộp tổng hợp có ca khó, báo cáo precision/recall/F1 theo ranh giới kèm n; màn hình duyệt ranh giới, ≥2 vai trò, chi phí US$/100 trang.

Nâng cao:
• hiệu chuẩn độ tin cậy ranh giới và chọn ngưỡng theo chi phí lỗi (cắt thừa so với bỏ sót), so sánh luật + đặc trưng với mô hình ngôn ngữ/thị giác theo chất lượng và chi phí, xử lý tệp nhiều trăm trang với cửa sổ trượt, kiểm tra tính nhất quán số trang của tài liệu, định tuyến trang có text layer sang đường rẻ
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-11] CheapPath Router - Định tuyến trang có text layer sang parser rẻ, chỉ trang scan mới dùng mô hình thị giác, và chứng minh khoản tiết kiệm bằng số đo

### 📝 Mô tả đề tài
📍 Thực trạng: Dùng mô hình thị giác cho mọi trang là đơn giản nhưng đắt khi khối lượng lên hàng trăm nghìn trang mỗi tháng, trong khi nhiều tài liệu đến dưới dạng PDF có text layer có thể đọc bằng parser gần như miễn phí và nhanh. Câu hỏi của quản lý luôn là 'mỗi trang tốn bao nhiêu, mỗi tháng tốn bao nhiêu ở khối lượng thực tế của chúng ta?'.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng bộ định tuyến cho pipeline đọc tài liệu: tự động phân loại từng trang là 'có text layer đáng tin' hay 'là ảnh/scan' (và trang lai), gửi trang tốt sang đường parser rẻ, trang scan sang đường OCR/mô hình thị giác, có cơ chế chuyển sang đường đắt khi đường rẻ không đủ tự tin; báo cáo tỷ lệ trang đi mỗi đường, chất lượng so với phương án 'tất cả qua thị giác', và khoản tiết kiệm; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng tài liệu công khai hoặc tự sinh gồm cả PDF sạch, PDF text layer lỗi (ký tự rác, sai thứ tự) và scan; quyết định định tuyến dựa trên đặc trưng đo được bằng code (độ phủ text, tỷ lệ ký tự lỗi, có ảnh nền hay không), không để mô hình tự quyết; đường rẻ phải không kém đường đắt có ý nghĩa trên golden set (kiểm định không thua kém, kèm n) trước khi được dùng; báo cáo chi phí đo thực tế (token và US$ mỗi trang) và chi phí theo tháng ở khối lượng nêu rõ, không ước lượng từ bảng giá; lời gọi chưa có giá phải hiển thị là 'chưa định giá', không phải 0.

### 🛠️ Tech Stack
• Python, FastAPI
• PyMuPDF/pdfplumber để đo độ phủ text layer và phát hiện ký tự rác
• OpenCV để đánh giá chất lượng ảnh trang
• parser rẻ: pdfplumber/Docling/Unstructured; đường đắt: OCR + VLM
• LLM/VLM có structured output
• bộ tài liệu tổng hợp với 3 nhóm: text layer sạch, text layer lỗi, scan
• Langfuse hoặc bảng đo token/US$ tự xây
• pytest + fixtures
• React/Next.js (bảng điều khiển tỷ lệ định tuyến và chi phí)
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• pipeline đọc tài liệu có router hai đường, chạy một lệnh trên golden set 50-150 tài liệu hỗn hợp, báo cáo tỷ lệ trang mỗi đường, accuracy theo trường của từng phương án (kèm n), chi phí US$/trang và chi phí theo tháng ở khối lượng nêu rõ, ≥2 vai trò (kỹ sư vận hành và quản lý xem báo cáo).

Nâng cao:
• kiểm định không thua kém giữa đường rẻ và đường đắt theo từng loại tài liệu, quy tắc leo thang (escalation) khi đường rẻ không tự tin, đường cong chi phí - chất lượng theo ngưỡng định tuyến, thêm tầng thứ ba (mô hình nhỏ rẻ hơn mô hình lớn), mô phỏng chi phí theo nhiều kịch bản khối lượng và tỷ lệ scan
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-12] CorrectionLoop - Cập nhật template hoặc ví dụ few-shot từ lần sửa của người duyệt và đo mức cải thiện trên tập giữ riêng

### 📝 Mô tả đề tài
📍 Thực trạng: Người duyệt sửa cùng một lỗi lặp lại hàng tuần (ví dụ luôn đọc nhầm một trường của một nhà cung cấp), nhưng các lần sửa đó chỉ đi vào cơ sở dữ liệu mà không giúp lần đọc tiếp theo tốt hơn; hệ thống 'không học' nên người duyệt dần mất kiên nhẫn và giá trị của việc duyệt bị bỏ phí.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng vòng phản hồi cho pipeline đọc tài liệu: ghi lại mọi lần sửa của người duyệt, phân tích để đề xuất cập nhật (sửa quy tắc template, thêm ví dụ few-shot cho nhà cung cấp/loại tài liệu liên quan), đề xuất đó được người có thẩm quyền duyệt, áp dụng có phiên bản, và hiệu quả được đo trước/sau trên tập giữ riêng; có kiểm tra hồi quy để một cập nhật cho nhà cung cấp A không làm hỏng nhà cung cấp B; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: cập nhật template/ví dụ do hệ thống đề xuất không tự áp dụng khi chưa có người duyệt đồng ý, mọi thay đổi có phiên bản và quay lui được; chỉ dùng tài liệu công khai hoặc tự sinh, lần sửa của người duyệt trong thí nghiệm là do thành viên nhóm thực hiện trên dữ liệu tổng hợp; mức cải thiện phải đo trên tập giữ riêng chưa từng dùng để sinh cập nhật, báo cáo kèm n và khoảng dao động; phải đo cả hồi quy trên các nhóm khác; không được dùng chính các tài liệu đã sửa để chứng minh cải thiện.

### 🛠️ Tech Stack
• Python, FastAPI
• PostgreSQL lưu tài liệu - trường - lần sửa - phiên bản template/ví dụ
• LLM có structured output để phân tích mẫu lỗi lặp lại và đề xuất cập nhật
• chọn ví dụ few-shot theo độ tương đồng (embedding + Qdrant/pgvector)
• định dạng template có phiên bản (JSON/YAML, Git/DVC)
• bộ tài liệu tổng hợp nhiều nhà cung cấp, chia train/held-out từ ngày đầu
• pytest + fixtures, bộ kiểm thử hồi quy theo nhà cung cấp
• React/Next.js (màn hình xem đề xuất cập nhật và biểu đồ trước/sau)
• Langfuse/MLflow
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• pipeline đọc tài liệu có ghi lần sửa, đề xuất cập nhật cho ≥1 nhà cung cấp, người duyệt phê duyệt rồi áp dụng, báo cáo accuracy theo trường trước/sau trên tập giữ riêng (n nêu rõ) và kiểm tra hồi quy, ≥2 vai trò (người duyệt tài liệu và người phê duyệt thay đổi).

Nâng cao:
• đường cong cải thiện theo số lần sửa, so sánh cập nhật template với cập nhật ví dụ few-shot về mức cải thiện/chi phí, phát hiện lỗi lặp lại tự động và ưu tiên cập nhật theo tác động, cơ chế quay lui khi hồi quy, báo cáo chi phí vòng học (token và US$) trên mỗi cập nhật
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-13] StatementReader - Đọc sao kê ngân hàng dạng PDF hoặc ảnh thành bảng giao dịch chuẩn (ngày, mô tả, ghi nợ/ghi có, số dư) có kiểm tra số dư chạy

### 📝 Mô tả đề tài
📍 Thực trạng: Bộ phận ngân quỹ nhận sao kê từ nhiều ngân hàng, mỗi ngân hàng một bố cục: mô tả giao dịch ngắt xuống nhiều dòng, tiêu đề lặp lại ở mỗi trang, định dạng số khác nhau, dòng 'số dư chuyển sang'. Việc nhập lại thành bảng để đối chiếu với sổ cái vừa tốn thời gian vừa dễ sai một dòng hay một chữ số.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng ứng dụng đọc sao kê (PDF có text layer hoặc ảnh/scan) thành bảng giao dịch chuẩn gồm ngày, mô tả, ghi nợ, ghi có, số dư; mỗi dòng kèm bằng chứng vị trí và độ tin cậy; kiểm tra bằng code rằng số dư đầu kỳ cộng các giao dịch bằng số dư cuối kỳ và số dư chạy khớp từng dòng; dòng hoặc đoạn không khớp được chỉ ra cho người duyệt; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng sao kê hoàn toàn tổng hợp do nhóm tự sinh theo nhiều bố cục ngân hàng, không dùng sao kê hay số tài khoản thật; việc đối chiếu sao kê với sổ cái nằm ngoài phạm vi bài này (chỉ đọc và chuẩn hóa dữ liệu đầu vào cho bước đối chiếu); kiểm tra số dư chạy, dấu ghi nợ/ghi có và thứ tự ngày do code đảm nhiệm, mô hình không được tự điền số; không bỏ sót giao dịch một cách im lặng; báo cáo accuracy theo dòng và theo trường kèm n, tỷ lệ sao kê qua được kiểm tra số dư, tỷ lệ confident-wrong, chi phí US$/trang.

### 🛠️ Tech Stack
• Python, FastAPI
• pdfplumber/Camelot/PyMuPDF để lấy bảng từ PDF có text layer; OCR hoặc VLM cho sao kê scan
• LLM/VLM có structured output để ghép dòng ngắt và tìm vùng bảng
• Pydantic + kiểm tra số dư chạy (Decimal) bằng code
• bộ sinh sao kê tổng hợp nhiều bố cục (ReportLab, Faker) kèm ca khó
• pytest + fixtures
• PostgreSQL/SQLite
• React/Next.js + PDF.js (xem dòng lỗi cạnh trang gốc)
• Langfuse
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• một lệnh chạy một sao kê ra bảng giao dịch chuẩn; golden set 50-150 sao kê tổng hợp có ca khó (mô tả ngắt nhiều dòng, tiêu đề lặp, số dư chuyển sang, định dạng số khác nhau, trang scan) kèm n; màn hình duyệt dòng không khớp số dư, ≥2 vai trò (nhân viên ngân quỹ và kế toán), báo cáo accuracy, tỷ lệ qua kiểm tra số dư, chi phí US$/trang.

Nâng cao:
• tự định vị và sửa dòng lỗi khi số dư chạy lệch (gợi ý dòng nghi ngờ), template cho nhiều ngân hàng thêm mới không cần sửa code, định tuyến trang sạch sang đường rẻ, xuất bảng chuẩn sẵn sàng cho bước đối chiếu với sổ cái, báo cáo chi phí theo tháng ở khối lượng thực tế
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-14] ContractFields - Trích các thông tin chính của hợp đồng dịch vụ/mua bán (các bên, ngày, giá trị, thời hạn, điều khoản thanh toán) kèm trích dẫn nguồn trong văn bản

### 📝 Mô tả đề tài
📍 Thực trạng: Nhân viên pháp chế và tài chính phải đọc từng hợp đồng để ghi lại các bên, ngày hiệu lực, giá trị, thời hạn, điều khoản thanh toán; thông tin nằm rải rác, giá trị ghi cả bằng số và bằng chữ, phụ lục có thể thay đổi giá trị hợp đồng gốc, và rất khó biết một trường 'không có trong hợp đồng' hay là bị bỏ sót.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng ứng dụng đọc hợp đồng (văn bản/PDF) và trích 8-20 trường chính (các bên, ngày ký, ngày hiệu lực, thời hạn, giá trị, đơn vị tiền tệ, hạn thanh toán, phạt vi phạm nếu có...), mỗi trường kèm câu trích nguyên văn từ hợp đồng làm bằng chứng; trường không có trong văn bản được trả là 'không tìm thấy' chứ không phải đoán; kiểm tra chéo bằng code (số tiền bằng số và bằng chữ khớp nhau, ngày hiệu lực không sau ngày hết hạn); đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng hợp đồng tự soạn hoặc mẫu công khai, không dùng hợp đồng thật; bài này chỉ đọc và trích trường, mọi đánh giá pháp lý (hợp đồng có hợp lệ, có rủi ro) nằm ngoài phạm vi và thuộc về người có thẩm quyền; mô hình chỉ chỉ ra câu chứa giá trị, code sao chép giá trị từ văn bản gốc; một trường mô hình không trích dẫn được từ văn bản thì để trống, không đoán; không trả kết quả rỗng một cách im lặng; báo cáo accuracy theo trường kèm n, tỷ lệ confident-wrong, tỷ lệ đúng khi trả 'không tìm thấy', chi phí US$/hợp đồng.

### 🛠️ Tech Stack
• Python, FastAPI
• PyMuPDF/pdfplumber/Docling để lấy văn bản và cấu trúc điều khoản
• LLM có structured output + yêu cầu trích dẫn nguyên văn
• kiểm tra trích dẫn có thật sự xuất hiện trong văn bản (khớp chuỗi bằng code)
• chuyển số bằng chữ tiếng Việt sang số (bộ quy tắc tự viết) để kiểm tra chéo
• bộ sinh hợp đồng và phụ lục tổng hợp (có ca khó: phụ lục đổi giá trị, nhiều ngày, thiếu trường)
• pytest + fixtures
• PostgreSQL
• React/Next.js (highlight trích dẫn trong văn bản)
• Langfuse
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• một lệnh chạy một hợp đồng ra bản ghi 8-20 trường kèm trích dẫn; golden set 50-150 hợp đồng tổng hợp có ca khó (số và chữ khác nhau, phụ lục thay đổi, nhiều ngày, thiếu trường) kèm n; màn hình duyệt với highlight trích dẫn, ≥2 vai trò (chuyên viên pháp chế/tài chính và người phê duyệt), báo cáo accuracy theo trường, tỷ lệ 'không tìm thấy' đúng, chi phí US$/hợp đồng.

Nâng cao:
• xử lý phụ lục ghi đè giá trị hợp đồng gốc và chỉ ra mâu thuẫn giữa các tài liệu, kiểm tra chéo số-chữ và logic ngày bằng code, hiệu chuẩn độ tin cậy theo từng trường, so sánh chia nhỏ văn bản theo điều khoản với đưa toàn văn theo chi phí/chất lượng, báo cáo chi phí theo tháng ở khối lượng thực tế
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---

## [IDP-15] Template Registry - Quản lý vòng đời mẫu trích xuất (phiên bản, kiểm thử hồi quy, phát hiện trôi lệch khi nhà cung cấp đổi mẫu chứng từ)

### 📝 Mô tả đề tài
📍 Thực trạng: Khi số lượng template tăng lên hàng trăm, vấn đề không còn là viết thêm template mà là giữ cho chúng đúng: nhà cung cấp lặng lẽ đổi mẫu hóa đơn, dịch chuyển một cột, thêm một dòng, và độ chính xác tụt dần mà không ai hay cho đến khi kế toán phát hiện sai ở khâu sau. Nhóm cần một nơi quản lý template như một tài sản có phiên bản, có kiểm thử và có giám sát.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng kho quản lý template trích xuất: lưu mỗi template theo phiên bản kèm bộ tài liệu kiểm thử riêng, tự động chạy kiểm thử hồi quy khi có thay đổi, giám sát tài liệu đến để phát hiện 'trôi lệch' (tài liệu không còn khớp template: bố cục đổi, trường biến mất, độ tin cậy giảm bất thường), cảnh báo và đề xuất tạo phiên bản mới; việc phát hành phiên bản mới do người có thẩm quyền phê duyệt, có thể quay lui; đồng thời tự thích ứng nhanh với mẫu bố cục tài liệu mới mà không cần sửa code, xử lý tài liệu nhiễu/đa trang và tối ưu hóa luồng phối hợp kiểm duyệt giữa máy với người dùng nghiệp vụ.

🔒 Ràng buộc: chỉ dùng tài liệu công khai hoặc tự sinh, trôi lệch được cài chủ đích bằng bộ sinh của nhóm; việc phát hành hoặc quay lui template phải do người phê duyệt, không có phát hành tự động; phát hiện trôi lệch dựa trên số đo bằng code (độ khớp bố cục, tỷ lệ trường tìm thấy, phân bố độ tin cậy) chứ không để mô hình tự cảm nhận; đo precision/recall của việc phát hiện trôi lệch trên các thay đổi mẫu được cài sẵn kèm n, tỷ lệ cảnh báo giả, thời gian từ lúc trôi lệch đến lúc cảnh báo; báo cáo chi phí giám sát (US$/1000 tài liệu).

### 🛠️ Tech Stack
• Python, FastAPI
• PostgreSQL + Git/DVC để lưu template có phiên bản và bộ kiểm thử
• đặc trưng bố cục (tọa độ khối văn bản, embedding bố cục/ảnh trang) và so sánh với tài liệu tham chiếu
• phát hiện trôi lệch thống kê (so sánh phân bố, ngưỡng và kiểm định đơn giản trong SciPy)
• LLM/VLM để mô tả sự thay đổi mẫu bằng ngôn ngữ tự nhiên (không quyết định phát hành)
• pytest + CI (GitHub Actions) chạy hồi quy template
• bộ sinh tài liệu tổng hợp có thay đổi mẫu theo thời gian
• React/Next.js (lịch sử phiên bản, cảnh báo trôi lệch, so sánh hai phiên bản)
• Grafana/Prometheus hoặc Langfuse để giám sát
• Docker.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app lưu ≥3 template có phiên bản kèm bộ kiểm thử, chạy hồi quy khi chỉnh template, giám sát luồng tài liệu tổng hợp và cảnh báo khi một nhà cung cấp đổi mẫu, người phê duyệt phát hành hoặc quay lui, ≥2 vai trò (chuyên viên template và người phê duyệt), báo cáo precision/recall phát hiện trôi lệch kèm n.

Nâng cao:
• đề xuất bản sửa template khi phát hiện trôi lệch và đo thời gian từ cảnh báo đến phiên bản mới, so sánh các số đo trôi lệch (bố cục, trường thiếu, độ tin cậy) về độ nhạy/cảnh báo giả, giải thích thay đổi mẫu bằng ngôn ngữ tự nhiên có kèm ảnh so sánh, báo cáo chi phí giám sát theo tháng ở khối lượng thực tế
• Phát triển cơ chế tự thích ứng mẫu tài liệu mới và công cụ phân tích lỗi trực quan giúp giảm tối đa tỷ lệ phải can thiệp thủ công trong vận hành doanh nghiệp.

---
