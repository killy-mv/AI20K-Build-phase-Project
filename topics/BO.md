# Lĩnh vực: BO - Hỗ trợ vận hành – Back Office doanh nghiệp

> Tổng số đề tài: **20 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `BO-01` | [AI Agent Sàng lọc & Chấm điểm CV theo JD (Screening Agent)](#bo-01) |
| `BO-02` | [AI Agent Trợ lý Hỏi đáp Chính sách Nhân sự nội bộ (HR Helpdesk Agent)](#bo-02) |
| `BO-03` | [AI Agent Soạn thảo & Rà soát Rủi ro Hợp đồng (Legal Contract Agent)](#bo-03) |
| `BO-04` | [AI Agent Xử lý Đề nghị Mua sắm & So sánh Nhà cung cấp (Procurement Agent)](#bo-04) |
| `BO-05` | [AI Agent Đối soát Hóa đơn & Chứng từ Kế toán (Invoice Reconciliation Agent)](#bo-05) |
| `BO-06` | [AI Agent Trợ lý Onboarding Nhân viên mới (Onboarding Buddy Agent)](#bo-06) |
| `BO-07` | [AI Agent Lập & Duyệt Đơn Nghỉ phép / Công tác (Leave & Travel Agent)](#bo-07) |
| `BO-08` | [AI Agent Tổng hợp Báo cáo Chi phí & Tài chính (Finance Reporting Agent)](#bo-08) |
| `BO-09` | [AI Agent Phân loại & Định tuyến Email/Công văn nội bộ (Mail Routing Agent)](#bo-09) |
| `BO-10` | [AI Agent Trợ lý Lập Ngân sách & Dự báo (Budgeting & Forecast Agent)](#bo-10) |
| `BO-11` | [AI Agent Quản lý Tài sản & Cấp phát Thiết bị (IT Asset Agent)](#bo-11) |
| `BO-12` | [AI Agent Hỗ trợ Chấm công & Rà soát Bảng lương (Payroll Assist Agent)](#bo-12) |
| `BO-13` | [AI Agent Trả lời Câu hỏi Thuế & Tuân thủ (Tax & Compliance Agent)](#bo-13) |
| `BO-14` | [AI Agent Tóm tắt & Trích xuất Tri thức Tài liệu nội bộ (Doc Intelligence Agent)](#bo-14) |
| `BO-15` | [AI Agent Sinh Mô tả Công việc & Khung Năng lực (JD & Competency Agent)](#bo-15) |
| `BO-16` | [AI Agent Khảo sát Gắn kết & Phân tích Ý kiến Nhân viên (Engagement Analytics Agent)](#bo-16) |
| `BO-17` | [AI Agent Trợ lý Phỏng vấn & Tổng hợp Đánh giá Ứng viên (Interview Assist Agent)](#bo-17) |
| `BO-18` | [AI Agent Trợ lý Nội quy & Xử lý Vi phạm Lao động (Labor Policy Agent)](#bo-18) |
| `BO-19` | [AI Agent Xử lý Yêu cầu Hành chính & Cấp phát Văn bản (Admin Service Desk Agent)](#bo-19) |
| `BO-20` | [AI Agent Kiểm soát Chi tiêu & Duyệt Đề nghị Thanh toán (Expense Approval Agent)](#bo-20) |

---

## [BO-01] AI Agent Sàng lọc & Chấm điểm CV theo JD (Screening Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Bộ phận Tuyển dụng tại doanh nghiệp nhận hàng trăm CV mỗi vị trí, đọc thủ công tốn thời gian và thiếu nhất quán giữa các recruiter. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tự động đọc CV (PDF/ảnh), trích xuất thông tin, đối chiếu với JD, chấm điểm theo tiêu chí (kỹ năng, kinh nghiệm, học vấn), giải thích lý do và xếp hạng shortlist; recruiter xem lại/điều chỉnh trước khi mời phỏng vấn; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL bắt buộc ở bước duyệt shortlist và loại ứng viên; bảo mật dữ liệu ứng viên (PII), ẩn thông tin nhạy cảm để chống thiên vị; độ chính xác trích xuất cao, không bịa kỹ năng; kiểm soát chi phí gọi LLM khi lượng CV lớn (cache, batch). 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM (GPT-4o/Claude) + LangGraph điều phối agent
• OCR (Google Document AI/Tesseract) đọc CV scan
• embedding (text-embedding-3) + vector DB (Qdrant/Chroma) matching kỹ năng
• RAG trên thư viện JD chuẩn
• backend FastAPI
• frontend Next.js/React
• deploy Vercel + Railway/Render, PostgreSQL lưu hồ sơ.
• Dữ liệu & benchmark thực tế tham chiếu: Khung phân loại kỹ năng nghề nghiệp quốc tế ESCO / O*NET, bộ dữ liệu IBM HR Analytics và tập dữ liệu đối sánh hồ sơ nhân sự công khai.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy online, đăng nhập 2 vai trò (Recruiter, HR Manager)
• upload CV hàng loạt + JD
• agent trích xuất, chấm điểm, xếp hạng, hiển thị bảng shortlist kèm giải thích
• recruiter duyệt/loại thủ công.

Nâng cao:
• Agent lập kế hoạch phỏng vấn theo mức độ phù hợp, sinh bộ câu hỏi phỏng vấn cá nhân hóa, memory ghi nhớ tiêu chí ưu tiên của từng manager, phát hiện CV trùng lặp/gian lận, cảnh báo khi thiếu dữ liệu và giới hạn token
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-02] AI Agent Trợ lý Hỏi đáp Chính sách Nhân sự nội bộ (HR Helpdesk Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhân viên doanh nghiệp liên tục hỏi phòng Nhân sự về nghỉ phép, bảo hiểm, phúc lợi, nội quy; HR trả lời lặp lại, quá tải và phản hồi chậm. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent hỏi đáp dựa trên bộ tài liệu chính sách nội bộ, trả lời chính xác kèm trích dẫn nguồn, biết tạo ticket chuyển HR khi vượt phạm vi hoặc câu hỏi nhạy cảm; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL khi câu hỏi liên quan lương/kỷ luật/trường hợp đặc biệt (chuyển người thật); bảo mật tài liệu nội bộ theo phân quyền phòng ban; độ chính xác cao, bắt buộc trích dẫn, từ chối khi không có căn cứ (chống bịa); tối ưu chi phí qua caching câu hỏi thường gặp. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + RAG (LlamaIndex/LangChain)
• vector DB (Pinecone/Qdrant)
• LangGraph cho luồng escalation
• reranker (Cohere) tăng độ chính xác
• backend FastAPI
• frontend React
• auth theo role
• deploy Render/Fly.io, PostgreSQL lưu lịch sử & ticket.
• Dữ liệu & benchmark thực tế tham chiếu: Khung phân loại kỹ năng nghề nghiệp quốc tế ESCO / O*NET, bộ dữ liệu IBM HR Analytics và tập dữ liệu đối sánh hồ sơ nhân sự công khai.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Nhân viên, HR Admin)
• chat hỏi đáp có trích dẫn nguồn
• HR upload/cập nhật tài liệu chính sách
• tạo ticket escalation.

Nâng cao:
• Agent tự lập kế hoạch truy vấn đa tài liệu, memory hội thoại theo user, phân quyền tài liệu theo phòng ban, dashboard câu hỏi phổ biến & gợi ý cập nhật chính sách, cảnh báo độ tin cậy thấp và giới hạn sử dụng
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-03] AI Agent Soạn thảo & Rà soát Rủi ro Hợp đồng (Legal Contract Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Phòng Pháp chế doanh nghiệp rà soát lượng lớn hợp đồng NCC/lao động/dịch vụ thủ công, dễ bỏ sót điều khoản rủi ro và mất nhiều ngày mỗi hồ sơ. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent đọc hợp đồng, phát hiện điều khoản rủi ro/thiếu, đối chiếu template & checklist pháp lý nội bộ, đề xuất chỉnh sửa và soạn dự thảo từ yêu cầu; luật sư duyệt từng đề xuất; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL bắt buộc — mọi sửa đổi phải luật sư phê duyệt, agent chỉ đề xuất; bảo mật hợp đồng tuyệt đối (dữ liệu mật); độ chính xác cao, trích dẫn điều khoản gốc, không tự khẳng định pháp lý; kiểm soát chi phí với tài liệu dài (chunk + tóm tắt). 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM (Claude context dài) + LangGraph
• RAG trên kho template & quy định pháp luật (vector DB Qdrant)
• OCR (Document AI) cho hợp đồng scan
• diff engine so sánh điều khoản
• backend FastAPI
• frontend Next.js với editor track-changes
• deploy Vercel + Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu rà soát điều khoản hợp đồng CUAD (Contract Understanding Atticus Dataset - 41 nhóm rủi ro), LegalBench kết hợp văn bản pháp quy lao động – thuế doanh nghiệp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Chuyên viên pháp chế, Trưởng phòng duyệt)
• upload hợp đồng
• agent liệt kê điều khoản rủi ro + mức độ + đề xuất sửa
• luật sư accept/reject từng mục.

Nâng cao:
• Agent lập kế hoạch rà soát theo loại hợp đồng, soạn dự thảo mới từ prompt, memory ghi các điều khoản ưa dùng của tổ chức, so sánh nhiều phiên bản, cảnh báo điều khoản trái luật và giới hạn token
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-04] AI Agent Xử lý Đề nghị Mua sắm & So sánh Nhà cung cấp (Procurement Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Phòng Mua sắm nhận nhiều đề nghị (PR) và báo giá từ nhiều NCC, việc tổng hợp, so sánh giá/điều khoản và chọn NCC làm thủ công qua Excel, dễ sai và thiếu minh bạch. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tiếp nhận PR, trích xuất báo giá từ email/PDF, chuẩn hóa và so sánh NCC theo giá-chất lượng-thời gian giao, đề xuất lựa chọn kèm lý do; người phụ trách duyệt và tạo PO; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL ở bước chọn NCC và duyệt PO (không tự đặt hàng); bảo mật báo giá/thông tin thương mại; độ chính xác trích xuất số liệu tài chính cao; kiểm soát chi phí xử lý nhiều tài liệu. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph (multi-step)
• OCR/parser bảng (Document AI/Camelot) trích báo giá
• vector DB lưu hồ sơ NCC + RAG chính sách mua sắm
• backend FastAPI
• frontend React với bảng so sánh
• deploy Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính – kế toán FinQA, TAT-QA, SROIE/CORD kết hợp bộ chứng từ đối soát mua sắm (PR–PO–GRN–Invoice) và bảng lương đa ca kíp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Nhân viên mua sắm, Quản lý duyệt)
• nhập PR + upload báo giá
• agent chuẩn hóa & so sánh NCC, đề xuất lựa chọn có giải thích
• duyệt tạo PO.

Nâng cao:
• Agent tự soạn email hỏi báo giá, dùng tool tính TCO/điểm đánh giá NCC, memory lịch sử NCC & vi phạm, phát hiện báo giá bất thường, human-in-the-loop nhiều cấp phê duyệt theo hạn mức, cảnh báo ngân sách
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-05] AI Agent Đối soát Hóa đơn & Chứng từ Kế toán (Invoice Reconciliation Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Kế toán doanh nghiệp đối soát hóa đơn với PO và phiếu nhập hàng (3-way matching) thủ công, khối lượng lớn cuối tháng, dễ sai lệch số liệu và chậm thanh toán. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent đọc hóa đơn (ảnh/PDF/XML hóa đơn điện tử), đối chiếu PO và phiếu giao, phát hiện chênh lệch (giá, số lượng, thuế), đề xuất xử lý; kế toán duyệt trước khi ghi sổ/thanh toán; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL bắt buộc trước khi hạch toán/thanh toán; bảo mật dữ liệu tài chính; độ chính xác số liệu tuyệt đối, cảnh báo khi OCR thấp tin cậy; tối ưu chi phí xử lý số lượng lớn. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph
• OCR hóa đơn (Google Document AI/VietOCR) + parser XML hóa đơn điện tử VN
• rule engine đối soát
• vector DB tra cứu NCC/PO
• backend FastAPI
• frontend React dashboard
• deploy Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu rà soát điều khoản hợp đồng CUAD (Contract Understanding Atticus Dataset - 41 nhóm rủi ro), LegalBench kết hợp văn bản pháp quy lao động – thuế doanh nghiệp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Kế toán viên, Kế toán trưởng)
• upload hóa đơn + đối chiếu PO/phiếu nhập
• agent phát hiện chênh lệch, phân loại khớp/lệch
• duyệt hạch toán.

Nâng cao:
• Agent tự truy hồi chứng từ liên quan, tính thuế GTGT, memory quy tắc riêng từng NCC, phát hiện hóa đơn trùng/gian lận, quy trình duyệt nhiều cấp, cảnh báo độ tin cậy OCR và giới hạn xử lý
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-06] AI Agent Trợ lý Onboarding Nhân viên mới (Onboarding Buddy Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhân viên mới tại doanh nghiệp bối rối với thủ tục, hệ thống, người liên hệ trong tuần đầu; HR phải kèm thủ công từng người. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent dẫn dắt lộ trình onboarding cá nhân hóa theo vị trí/phòng ban, giao & theo dõi checklist (khai báo, cấp tài khoản, đào tạo), trả lời thắc mắc và nhắc việc; HR theo dõi/can thiệp khi tắc; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL khi cấp quyền hệ thống/xử lý ngoại lệ; bảo mật thông tin cá nhân nhân viên mới; độ chính xác thông tin quy trình; tối ưu chi phí với hội thoại dài. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph (stateful workflow)
• RAG tài liệu onboarding + vector DB
• memory dài hạn theo nhân viên
• tool gọi API tạo task/nhắc lịch
• backend FastAPI
• frontend Next.js
• deploy Vercel + Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Khung phân loại kỹ năng nghề nghiệp quốc tế ESCO / O*NET, bộ dữ liệu IBM HR Analytics và tập dữ liệu đối sánh hồ sơ nhân sự công khai.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Nhân viên mới, HR)
• agent sinh lộ trình + checklist cá nhân hóa, chat hỏi đáp, theo dõi tiến độ
• HR giám sát.

Nâng cao:
• Agent lập kế hoạch onboarding theo role, dùng tool tạo lịch/nhắc việc tự động, memory tiến trình từng người, human-in-the-loop duyệt cấp quyền, phát hiện nhân viên trễ mốc và cảnh báo, xử lý lỗi khi thiếu dữ liệu
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-07] AI Agent Lập & Duyệt Đơn Nghỉ phép / Công tác (Leave & Travel Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhân viên gửi đơn nghỉ phép/công tác qua email hoặc form rời rạc, quản lý duyệt thủ công, khó tra số ngày phép còn lại và trùng lịch nhóm. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tiếp nhận yêu cầu bằng ngôn ngữ tự nhiên, kiểm tra số dư phép/chính sách, phát hiện xung đột lịch, soạn đơn chuẩn và định tuyến duyệt; quản lý phê duyệt/từ chối; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL bắt buộc — quản lý phê duyệt cuối; bảo mật dữ liệu nhân sự & lịch; độ chính xác tính ngày phép/chính sách cao; kiểm soát chi phí. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph
• RAG chính sách nghỉ phép
• tool tính số dư phép & kiểm tra lịch (calendar API)
• backend FastAPI
• frontend React
• deploy Render, PostgreSQL
• queue thông báo.
• Dữ liệu & benchmark thực tế tham chiếu: Khung phân loại kỹ năng nghề nghiệp quốc tế ESCO / O*NET, bộ dữ liệu IBM HR Analytics và tập dữ liệu đối sánh hồ sơ nhân sự công khai.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Nhân viên, Quản lý duyệt)
• tạo đơn bằng chat, agent kiểm tra số dư & chính sách, sinh đơn chuẩn, gửi duyệt
• quản lý approve/reject.

Nâng cao:
• Agent phát hiện xung đột lịch nhóm & đề xuất ngày thay thế, memory pattern nghỉ, duyệt nhiều cấp theo số ngày, tính công tác phí công tác, cảnh báo vượt hạn mức phép và giới hạn
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-08] AI Agent Tổng hợp Báo cáo Chi phí & Tài chính (Finance Reporting Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Phòng Tài chính tổng hợp chi phí từ nhiều nguồn (Excel, ERP export, hóa đơn) để làm báo cáo định kỳ, tốn nhiều ngày và dễ lệch số. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent thu thập & chuẩn hóa dữ liệu chi phí, phân loại theo khoản mục/phòng ban, tính toán và sinh báo cáo có biểu đồ + nhận định; kế toán trưởng xem lại trước khi phát hành; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL trước khi phát hành báo cáo; bảo mật số liệu tài chính; độ chính xác tính toán tuyệt đối (dùng code chứ không nhẩm bằng LLM); kiểm soát chi phí xử lý dữ liệu lớn. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph với code-execution tool (pandas)
• phân loại chi phí bằng embedding
• RAG quy tắc kế toán nội bộ
• backend FastAPI
• frontend React + thư viện chart
• deploy Render, PostgreSQL
• xuất PDF/Excel.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính – kế toán FinQA, TAT-QA, SROIE/CORD kết hợp bộ chứng từ đối soát mua sắm (PR–PO–GRN–Invoice) và bảng lương đa ca kíp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Chuyên viên tài chính, Kế toán trưởng)
• upload dữ liệu, agent chuẩn hóa & phân loại, sinh báo cáo + biểu đồ + nhận định
• duyệt phát hành.

Nâng cao:
• Agent dùng tool tính toán chính xác, so sánh kỳ/ngân sách, phát hiện chi phí bất thường, memory cấu trúc báo cáo tổ chức, hỏi lại khi dữ liệu thiếu, human-in-the-loop chỉnh diễn giải, cảnh báo lệch số & giới hạn
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-09] AI Agent Phân loại & Định tuyến Email/Công văn nội bộ (Mail Routing Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Hộp thư chung phòng Hành chính doanh nghiệp công nghệ nhận hàng trăm email/công văn mỗi ngày (yêu cầu, khiếu nại, đề nghị), phân loại và chuyển đúng người thủ công gây trễ và thất lạc. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent đọc email/công văn, xác định loại-độ ưu tiên-phòng ban phụ trách, tóm tắt, đề xuất định tuyến và soạn phản hồi mẫu; nhân viên hành chính duyệt trước khi gửi/chuyển; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL trước khi chuyển tiếp/trả lời chính thức; bảo mật nội dung công văn nội bộ; độ chính xác phân loại & định tuyến cao; kiểm soát chi phí với lượng email lớn. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph
• phân loại đa nhãn (embedding + classifier)
• RAG danh bạ phòng ban & quy trình
• tool đọc mail (IMAP/Graph API)
• backend FastAPI
• frontend React inbox
• deploy Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Khung phân loại kỹ năng nghề nghiệp quốc tế ESCO / O*NET, bộ dữ liệu IBM HR Analytics và tập dữ liệu đối sánh hồ sơ nhân sự công khai.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Nhân viên hành chính, Trưởng phòng)
• agent phân loại + tóm tắt + đề xuất người nhận & bản nháp trả lời
• duyệt định tuyến/gửi.

Nâng cao:
• Agent tự học quy tắc định tuyến qua memory, phát hiện email khẩn/nhạy cảm để ưu tiên, gộp luồng liên quan, dashboard SLA xử lý, xử lý lỗi khi không xác định được người nhận và cảnh báo tồn đọng
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-10] AI Agent Trợ lý Lập Ngân sách & Dự báo (Budgeting & Forecast Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Các phòng ban nhà máy sản xuất pin của doanh nghiệp lập ngân sách và dự báo dựa trên số liệu lịch sử trong Excel, quy trình rời rạc, thiếu kịch bản và khó điều chỉnh nhanh. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent phân tích chi tiêu lịch sử, đề xuất ngân sách theo khoản mục, dự báo và mô phỏng kịch bản (what-if), giải thích giả định; quản lý xem lại và điều chỉnh trước khi chốt; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL bắt buộc khi chốt ngân sách; bảo mật dữ liệu tài chính; độ chính xác tính toán qua code (không nhẩm LLM); minh bạch giả định; kiểm soát chi phí. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph với code tool (pandas/statsmodels/Prophet)
• RAG hướng dẫn lập ngân sách
• backend FastAPI
• frontend React + chart tương tác
• deploy Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính – kế toán FinQA, TAT-QA, SROIE/CORD kết hợp bộ chứng từ đối soát mua sắm (PR–PO–GRN–Invoice) và bảng lương đa ca kíp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Chuyên viên, Quản lý)
• upload số liệu lịch sử, agent đề xuất ngân sách + dự báo + biểu đồ
• điều chỉnh & chốt.

Nâng cao:
• Agent mô phỏng nhiều kịch bản what-if, dùng tool dự báo thống kê, memory giả định của phòng ban, phát hiện khoản chi bất thường, human-in-the-loop tinh chỉnh giả định, cảnh báo vượt trần ngân sách và giới hạn
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-11] AI Agent Quản lý Tài sản & Cấp phát Thiết bị (IT Asset Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Phòng Hành chính/IT quản lý cấp phát laptop, thiết bị cho nhân viên bằng file rời rạc, khó biết thiết bị còn/trạng thái/ai giữ, xử lý yêu cầu cấp phát chậm. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tiếp nhận yêu cầu cấp phát/thu hồi, kiểm tra tồn kho & tiêu chuẩn cấp theo chức danh, đề xuất thiết bị phù hợp, tạo phiếu bàn giao và nhắc bảo trì; quản lý duyệt cấp phát; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL trước khi cấp phát/thu hồi tài sản; bảo mật thông tin tài sản & nhân viên; độ chính xác trạng thái tồn kho; kiểm soát chi phí. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph
• RAG chính sách cấp phát
• tool truy vấn/cập nhật kho tài sản (DB)
• vector DB tra cứu
• backend FastAPI
• frontend React dashboard tài sản
• deploy Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu suy luận số học tài chính – kế toán FinQA, TAT-QA, SROIE/CORD kết hợp bộ chứng từ đối soát mua sắm (PR–PO–GRN–Invoice) và bảng lương đa ca kíp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Nhân viên yêu cầu, Quản trị tài sản)
• tạo yêu cầu, agent kiểm tra tồn kho & tiêu chuẩn, đề xuất thiết bị, sinh phiếu bàn giao
• duyệt cấp phát.

Nâng cao:
• Agent theo dõi vòng đời tài sản, nhắc bảo trì/thu hồi khi nghỉ việc, memory lịch sử sử dụng, phát hiện thiếu hụt tồn kho & đề xuất mua bổ sung, human-in-the-loop nhiều cấp, cảnh báo giới hạn ngân sách thiết bị
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-12] AI Agent Hỗ trợ Chấm công & Rà soát Bảng lương (Payroll Assist Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: HR/Kế toán tổng hợp chấm công (vân tay, đơn nghỉ, tăng ca) và tính lương thủ công, dễ sai công-thuế-bảo hiểm và tốn thời gian cuối kỳ. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent hợp nhất dữ liệu chấm công, phát hiện bất thường (thiếu công, tăng ca lạ), tính toán bảng lương sơ bộ theo quy tắc, giải thích khoản mục; HR rà soát và duyệt trước khi chốt; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL bắt buộc trước khi chốt lương; bảo mật dữ liệu lương (nhạy cảm cao); độ chính xác tính toán tuyệt đối qua code; minh bạch công thức; kiểm soát chi phí. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph với code tool (pandas) cho tính lương/thuế TNCN/BHXH
• RAG quy chế lương thưởng
• rule engine
• backend FastAPI
• frontend React
• deploy Render, PostgreSQL (mã hóa dữ liệu lương).
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu rà soát điều khoản hợp đồng CUAD (Contract Understanding Atticus Dataset - 41 nhóm rủi ro), LegalBench kết hợp văn bản pháp quy lao động – thuế doanh nghiệp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (HR/Kế toán, Quản lý duyệt)
• upload dữ liệu chấm công, agent tính lương sơ bộ + phát hiện bất thường + giải thích
• rà soát & duyệt.

Nâng cao:
• Agent tính thuế/bảo hiểm bằng code chính xác, memory quy tắc riêng từng nhóm nhân sự, đối chiếu kỳ trước, phát hiện chênh lệch & gian lận công, human-in-the-loop điều chỉnh, cảnh báo độ tin cậy & giới hạn
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-13] AI Agent Trả lời Câu hỏi Thuế & Tuân thủ (Tax & Compliance Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Kế toán các đơn vị trong doanh nghiệp thường xuyên tra cứu quy định thuế, nghị định, thông tư thay đổi liên tục, dễ áp dụng sai và rủi ro tuân thủ. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent hỏi đáp về thuế/tuân thủ dựa trên kho văn bản pháp luật + hướng dẫn nội bộ, trả lời có trích dẫn điều khoản, cảnh báo khi quy định đã hết hiệu lực/thay đổi; chuyên gia thuế xác nhận với tình huống phức tạp; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL cho tư vấn có rủi ro pháp lý (chuyển chuyên gia); bảo mật số liệu doanh nghiệp; độ chính xác & trích dẫn bắt buộc, từ chối khi không chắc; kiểm soát chi phí truy vấn kho văn bản lớn. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + RAG (LangChain) trên kho văn bản thuế + reranker
• vector DB Qdrant
• LangGraph luồng escalation
• tool kiểm tra hiệu lực văn bản
• backend FastAPI
• frontend React
• deploy Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu rà soát điều khoản hợp đồng CUAD (Contract Understanding Atticus Dataset - 41 nhóm rủi ro), LegalBench kết hợp văn bản pháp quy lao động – thuế doanh nghiệp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Kế toán, Chuyên gia thuế)
• chat hỏi đáp có trích dẫn văn bản
• upload/cập nhật văn bản
• escalation lên chuyên gia.

Nâng cao:
• Agent lập kế hoạch truy vấn đa văn bản, cảnh báo văn bản hết hiệu lực/mâu thuẫn, memory tình huống doanh nghiệp, tính thử nghĩa vụ thuế qua tool, human-in-the-loop xác nhận, cảnh báo độ tin cậy thấp & giới hạn
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-14] AI Agent Tóm tắt & Trích xuất Tri thức Tài liệu nội bộ (Doc Intelligence Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Kho tài liệu nội bộ (quy trình, biên bản, quyết định) của khối công nghệ của doanh nghiệp rời rạc, nhân viên khó tìm và mất thời gian đọc tài liệu dài. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent thu thập, tóm tắt, trích xuất thông tin có cấu trúc (quyết định, trách nhiệm, deadline) và trả lời truy vấn xuyên tài liệu có trích dẫn; người dùng xác nhận thông tin trích xuất quan trọng; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL khi trích xuất phục vụ ra quyết định/lưu chính thức; bảo mật & phân quyền tài liệu; độ chính xác trích xuất, bắt buộc dẫn nguồn; kiểm soát chi phí tài liệu dài. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM (context dài) + LangGraph
• RAG + vector DB
• OCR (Document AI) cho tài liệu scan
• schema extraction có kiểm chứng
• backend FastAPI
• frontend Next.js
• deploy Vercel + Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Khung phân loại kỹ năng nghề nghiệp quốc tế ESCO / O*NET, bộ dữ liệu IBM HR Analytics và tập dữ liệu đối sánh hồ sơ nhân sự công khai.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Nhân viên, Quản trị tri thức)
• upload tài liệu, agent tóm tắt + trích xuất trường có cấu trúc + hỏi đáp trích dẫn.

Nâng cao:
• Agent tổng hợp xuyên nhiều tài liệu, phát hiện mâu thuẫn/trùng lặp, memory ngữ cảnh dự án, human-in-the-loop duyệt thông tin trích xuất, phân quyền theo phòng ban, cảnh báo độ tin cậy OCR & giới hạn token
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-15] AI Agent Sinh Mô tả Công việc & Khung Năng lực (JD & Competency Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: HR các đơn vị tự viết JD và khung năng lực không nhất quán, thiếu chuẩn hóa giữa các vị trí và tốn thời gian mỗi khi mở tuyển. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent sinh JD chuẩn và khung năng lực từ mô tả sơ bộ + thư viện vị trí, đảm bảo nhất quán ngôn ngữ/thương hiệu, gợi ý tiêu chí đánh giá; HR biên tập và phê duyệt; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL bắt buộc trước khi ban hành JD; bảo mật thông tin tổ chức/định biên; độ chính xác & ngôn ngữ trung tính (chống thiên vị giới/tuổi); kiểm soát chi phí. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph
• RAG thư viện JD & từ điển năng lực
• vector DB
• kiểm tra ngôn ngữ thiên vị
• backend FastAPI
• frontend React editor
• deploy Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Khung phân loại kỹ năng nghề nghiệp quốc tế ESCO / O*NET, bộ dữ liệu IBM HR Analytics và tập dữ liệu đối sánh hồ sơ nhân sự công khai.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (HR, Quản lý phê duyệt)
• nhập yêu cầu, agent sinh JD + khung năng lực chuẩn
• biên tập & duyệt ban hành.

Nâng cao:
• Agent đảm bảo nhất quán với vị trí liên quan, phát hiện & sửa ngôn ngữ thiên vị, memory phong cách thương hiệu, sinh câu hỏi phỏng vấn & tiêu chí chấm theo JD, human-in-the-loop nhiều cấp, cảnh báo mâu thuẫn định biên & giới hạn
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-16] AI Agent Khảo sát Gắn kết & Phân tích Ý kiến Nhân viên (Engagement Analytics Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: HR tổ chức khảo sát gắn kết nhưng phân tích hàng nghìn phản hồi mở thủ công, chậm và bỏ sót tín hiệu rủi ro nghỉ việc. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent thiết kế/thu thập khảo sát, phân tích cảm xúc & chủ đề từ phản hồi mở, tổng hợp insight theo phòng ban và đề xuất hành động; HR xem lại và chọn hành động trước khi triển khai; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL trước khi báo cáo lãnh đạo/hành động; bảo mật & ẩn danh phản hồi (dữ liệu nhân sự nhạy cảm); độ chính xác phân tích, tránh suy diễn quá mức; kiểm soát chi phí xử lý khối lượng lớn. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph
• phân tích cảm xúc & topic modeling (embedding + clustering)
• RAG best-practice engagement
• code tool thống kê
• backend FastAPI
• frontend React dashboard
• deploy Render, PostgreSQL (ẩn danh hóa).
• Dữ liệu & benchmark thực tế tham chiếu: Khung phân loại kỹ năng nghề nghiệp quốc tế ESCO / O*NET, bộ dữ liệu IBM HR Analytics và tập dữ liệu đối sánh hồ sơ nhân sự công khai.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Nhân viên trả lời, HR phân tích)
• tạo khảo sát, thu phản hồi, agent phân tích cảm xúc + chủ đề + dashboard theo phòng ban.

Nâng cao:
• Agent phát hiện tín hiệu rủi ro nghỉ việc, đề xuất hành động ưu tiên, so sánh kỳ, memory chủ đề tồn đọng, ẩn danh & lọc nhận dạng, human-in-the-loop duyệt insight, cảnh báo mẫu quá nhỏ & giới hạn
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-17] AI Agent Trợ lý Phỏng vấn & Tổng hợp Đánh giá Ứng viên (Interview Assist Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhiều người phỏng vấn tại doanh nghiệp ô tô ghi chú rời rạc, tiêu chí đánh giá khác nhau, khó tổng hợp và ra quyết định tuyển thống nhất. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent sinh bộ câu hỏi theo JD & cấp độ, hỗ trợ ghi chú/chấm điểm theo khung năng lực trong buổi phỏng vấn, tổng hợp đánh giá đa người phỏng vấn thành khuyến nghị; hội đồng ra quyết định cuối; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL bắt buộc — quyết định tuyển do con người; bảo mật dữ liệu ứng viên; độ chính xác tổng hợp, không thiên vị; công bằng & minh bạch tiêu chí; kiểm soát chi phí. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph
• RAG khung năng lực & JD
• vector DB
• tool ghi âm-chuyển văn bản (Whisper) tùy chọn
• backend FastAPI
• frontend React scorecard
• deploy Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Khung phân loại kỹ năng nghề nghiệp quốc tế ESCO / O*NET, bộ dữ liệu IBM HR Analytics và tập dữ liệu đối sánh hồ sơ nhân sự công khai.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Người phỏng vấn, Trưởng nhóm tuyển dụng)
• agent sinh câu hỏi theo JD, ghi nhận điểm theo khung, tổng hợp đánh giá đa người phỏng vấn + khuyến nghị.

Nâng cao:
• Agent chuyển giọng nói thành ghi chú, phát hiện tiêu chí chưa được hỏi, memory profile ứng viên qua các vòng, phát hiện bất đồng đánh giá, human-in-the-loop quyết định hội đồng, cảnh báo thiên vị & giới hạn
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-18] AI Agent Trợ lý Nội quy & Xử lý Vi phạm Lao động (Labor Policy Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Quản lý và HR lúng túng khi áp dụng nội quy lao động cho tình huống vi phạm cụ thể, tra cứu quy định & tiền lệ mất thời gian, rủi ro áp sai mức kỷ luật. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent phân tích tình huống vi phạm, đối chiếu nội quy & Bộ luật Lao động, đề xuất quy trình xử lý và khung hình thức kỷ luật kèm căn cứ; HR/pháp chế phê duyệt hướng xử lý; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL bắt buộc — quyết định kỷ luật do con người, agent chỉ tư vấn; bảo mật dữ liệu vụ việc/nhân sự; độ chính xác & trích dẫn căn cứ pháp lý; kiểm soát chi phí. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + RAG (nội quy + Bộ luật Lao động) + reranker
• vector DB Qdrant
• LangGraph luồng phân tích & escalation
• backend FastAPI
• frontend React
• deploy Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu rà soát điều khoản hợp đồng CUAD (Contract Understanding Atticus Dataset - 41 nhóm rủi ro), LegalBench kết hợp văn bản pháp quy lao động – thuế doanh nghiệp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Quản lý/HR, Pháp chế duyệt)
• nhập tình huống, agent phân tích + đối chiếu quy định + đề xuất quy trình & khung xử lý có trích dẫn
• duyệt hướng xử lý.

Nâng cao:
• Agent soạn biên bản/quyết định mẫu, tra tiền lệ nội bộ qua memory, cảnh báo rủi ro pháp lý & thời hiệu, human-in-the-loop nhiều cấp phê duyệt, phát hiện thiếu bằng chứng, cảnh báo độ tin cậy & giới hạn
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-19] AI Agent Xử lý Yêu cầu Hành chính & Cấp phát Văn bản (Admin Service Desk Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhân viên gửi yêu cầu hành chính (xác nhận công tác, giấy giới thiệu, đặt phòng họp, con dấu) qua nhiều kênh, phòng Hành chính xử lý thủ công gây trễ và khó theo dõi. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent tiếp nhận yêu cầu bằng ngôn ngữ tự nhiên, phân loại-kiểm tra điều kiện-soạn văn bản mẫu (giấy xác nhận, giấy giới thiệu), định tuyến duyệt & ký; cán bộ hành chính duyệt và phát hành; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL bắt buộc trước khi phát hành văn bản/dùng con dấu; bảo mật thông tin nhân viên & văn bản chính thức; độ chính xác nội dung văn bản; kiểm soát chi phí. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph
• RAG mẫu văn bản & quy trình hành chính
• tool điền template (docx) & đặt lịch phòng họp
• vector DB
• backend FastAPI
• frontend React
• deploy Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Khung phân loại kỹ năng nghề nghiệp quốc tế ESCO / O*NET, bộ dữ liệu IBM HR Analytics và tập dữ liệu đối sánh hồ sơ nhân sự công khai.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập 2 vai trò (Nhân viên, Cán bộ hành chính)
• tạo yêu cầu bằng chat, agent phân loại + kiểm tra điều kiện + sinh văn bản mẫu
• duyệt & phát hành, theo dõi trạng thái.

Nâng cao:
• Agent tự điền template & tạo bản in, định tuyến ký nhiều cấp, memory yêu cầu định kỳ của nhân viên, đặt lịch/tài nguyên qua tool, human-in-the-loop duyệt con dấu, dashboard SLA, cảnh báo tồn đọng & giới hạn
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---

## [BO-20] AI Agent Kiểm soát Chi tiêu & Duyệt Đề nghị Thanh toán (Expense Approval Agent)

### 📝 Mô tả đề tài
📍 Thực trạng: Nhân viên nộp đề nghị thanh toán/hoàn ứng kèm hóa đơn, kế toán kiểm tra chính sách chi tiêu và định mức thủ công, quá trình duyệt nhiều tầng chậm và thiếu nhất quán. Trong vận hành Back Office của doanh nghiệp, hồ sơ/chứng từ đầu vào thường không đồng nhất định dạng, phát sinh nhiều ngoại lệ (giao hàng từng phần, điều khoản sửa đổi bổ sung, văn bản hết hiệu lực) khiến việc đối chiếu thủ công dễ bỏ sót rủi ro.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent đọc đề nghị + hóa đơn, đối chiếu chính sách chi tiêu/định mức, phát hiện vi phạm & thiếu chứng từ, định tuyến duyệt theo hạn mức và giải thích quyết định; quản lý/kế toán phê duyệt cuối; đồng thời kết hợp khả năng bóc tách và suy luận ngữ nghĩa trên văn bản/chứng từ của Agent với động cơ kiểm tra quy tắc nghiệp vụ – đối soát số học – hiệu lực thời gian xác định bằng code để phát hiện sớm sai lệch và tối ưu hóa quy trình nội bộ.

🔒 Ràng buộc: HITL bắt buộc ở các cấp duyệt theo hạn mức (agent không tự chi); bảo mật dữ liệu tài chính & hóa đơn; độ chính xác đối chiếu định mức & số liệu (dùng code); kiểm soát chi phí xử lý nhiều hồ sơ. 100% phép tính lương, thuế, ngân sách và đối soát chứng từ 3 chiều phải do công cụ code xác định thực hiện (cấm LLM tự cộng trừ); kiểm soát thiên vị và lưu nhật ký kiểm toán đầy đủ.

### 🛠️ Tech Stack
• LLM + LangGraph (workflow duyệt đa cấp)
• OCR hóa đơn (Document AI)
• RAG chính sách chi tiêu
• rule/code tool kiểm tra định mức
• backend FastAPI
• frontend React
• deploy Render, PostgreSQL.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu rà soát điều khoản hợp đồng CUAD (Contract Understanding Atticus Dataset - 41 nhóm rủi ro), LegalBench kết hợp văn bản pháp quy lao động – thuế doanh nghiệp.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web deploy, đăng nhập ≥2 vai trò (Nhân viên đề nghị, Quản lý/Kế toán duyệt)
• nộp đề nghị + hóa đơn, agent trích xuất, đối chiếu chính sách, phát hiện vi phạm, đề xuất duyệt/từ chối có giải thích
• phê duyệt.

Nâng cao:
• Agent định tuyến duyệt đa cấp theo hạn mức, phát hiện hóa đơn trùng/quá định mức, memory lịch sử chi tiêu nhân viên, tính toán chính xác qua code, human-in-the-loop nhiều tầng, dashboard kiểm soát ngân sách, cảnh báo bất thường & giới hạn
• Tách biệt rõ tầng tính toán số học/kiểm tra hiệu lực quy định bằng code với tầng ngôn ngữ của mô hình, xử lý các ca chứng từ lệch chuẩn/ngoại lệ và đánh giá định lượng độ chính xác trên dữ liệu thực tế.

---
