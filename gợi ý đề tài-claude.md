# GỢI Ý ĐỀ TÀI – AI THỰC CHIẾN (3–6 THÁNG)

> **Phạm vi:** chỉ chọn đề tài **có sẵn trong `TOPICS.md`** (447 đề tài).
> **Ràng buộc dữ liệu:** team **không có dữ liệu doanh nghiệp**, chỉ đóng góp hiểu biết nghiệp vụ. Dữ liệu lấy từ **bộ công khai** (Kaggle, Hugging Face, GitHub, cổng dữ liệu mở), **tự cào nguồn công khai**, hoặc **tổng hợp** theo nghiệp vụ.
> **Tính chất sản phẩm:** chỉ để **tham khảo** – không ra quyết định thay người dùng, không chẩn đoán, không kê đơn, không khuyến nghị đầu tư; mọi kết quả kèm nguồn và ngày cập nhật.
> **Cấu trúc file:** **Phần 1** – tổng hợp từng đề tài (tên tổng quan, đối tượng, input, output). **Phần 2** – phân tích sâu từng đề tài kèm các đề tài phụ đi kèm. **Phần 3** – so sánh và khuyến nghị.
> Ngày cập nhật: 14/11/2026.

**Team**
| Thành viên | Đóng góp |
|---|---|
| Marketing (du lịch, vận hành, mua hàng, giáo dục, SEO; có startup xe du lịch) | Nghiệp vụ, golden set, khảo sát người dùng, kéo người dùng thử |
| AI Data Engineer (1 năm AI + 1 năm web Amazon/Shopify) | Cào dữ liệu, pipeline, RAG, agent, bộ đánh giá |
| Dev fullstack (6 tháng hệ thống mạng nhà nước) | Hạ tầng, CI/CD, bảo mật, phân quyền |
| Dev năm 4 | Giao diện, dashboard, màn hình duyệt, test |
| Mentor | Giáo dục, fintech |

---

## <a id="phan-1"></a>PHẦN 1 – TỔNG HỢP CÁC ĐỀ TÀI

### Bảng tổng quan

| # | Mã đề gốc | Tên tổng quan | Đối tượng chính | Sản phẩm cuối | Điểm /30 | Phân tích sâu |
|---|---|---|---|---|:---:|---|
| 1 | [BDSO2O-11](topics/BDSO2O.md#bdso2o-11) | **Phễu chuyển đổi: rơi ở đâu, vì sao** | Marketer, chủ shop | Web app phân tích + chat hỏi dữ liệu | **28** | [→](#c2-funnel) |
| 2 | [BO-13](topics/BO.md#bo-13) | **Tra cứu thuế có trích điều khoản cho hộ kinh doanh** | Hộ kinh doanh, kế toán nhỏ | Chatbot + máy tính thuế | **26** | [→](#c2-bo13) |
| 3 | [FIN-19](topics/FIN.md#fin-19) | **Cảnh báo lừa đảo trước khi tin, trước khi chuyển tiền** | Người dùng phổ thông | Web + bot Zalo/Telegram | 26 | [→](#d-fin19) |
| 4 | [GSM-15](topics/GSM.md#gsm-15) | **Social listening cho thương hiệu nhỏ** | Marketer, chủ doanh nghiệp | Dashboard + cảnh báo | 25 | [→](#c2-gsm15) |
| 5 | [GSM-06](topics/GSM.md#gsm-06) | **Review du lịch theo khía cạnh** | Nhà xe, khách sạn, tour nhỏ | Dashboard + báo cáo tuần | 24 | [→](#d-gsm06) |
| 6 | [EDU-12](topics/EDU.md#edu-12) | **Trợ lý tuyển sinh liên trường có trích dẫn** | Học sinh, phụ huynh | Chatbot + trang so sánh ngành | 23 | [→](#d-edu12) |
| 7 | [VMEC-15](topics/VMEC.md#vmec-15) | **So sánh & hiểu gói khám trước khi mua** | Người đi khám, nhân sự doanh nghiệp | Website so sánh + chatbot | 22 | [→](#c2-vmec15) |
| 8 | [IDP-03](topics/IDP.md#idp-03) | **Chuẩn hóa bảng giá nhà cung cấp** | Người mua hàng, chủ shop | Web app tải file → bảng chuẩn | 22 | [→](#d-idp03) |
| 9 | [EDU-17](topics/EDU.md#edu-17) | **CV & phỏng vấn thử theo JD thật** | Sinh viên, người mới đi làm | Web app + phòng phỏng vấn thử | 21 | [→](#d-edu17) |
| 10 | [CHAT-37](topics/CHAT.md#chat-37) | **Kiểm chứng tin forward** | Người dùng phổ thông | Chatbot + tiện ích chia sẻ | 21 | [→](#d-chat37) |
| 11 | [FIN-09](topics/FIN.md#fin-09) | **Đọc hiểu sao kê: tiền đi đâu** | Người dùng cá nhân | Web app tải sao kê → dashboard | 20 | [→](#d-fin09) |
| 12 | [GSM-19](topics/GSM.md#gsm-19) | **Lên lộ trình & ước tính chi phí du lịch** | Khách du lịch, tour nhỏ | Chatbot + bản đồ | 19 | [→](#c2-gsm19) |
| 13 | [VFO2O-19](topics/VFO2O.md#vfo2o-19) | **Lộ trình đường dài có điểm sạc xe điện** | Chủ xe điện | Web app bản đồ | 19 | [→](#d-vfo2o19) |
| 14 | [BDSO2O-16](topics/BDSO2O.md#bdso2o-16) | **Khoảng giá căn hộ thứ cấp từ tin rao** | Người mua/bán căn hộ | Web app định giá tham khảo | 18 | [→](#d-bdso2o16) |
| 15 | [EDU-09](topics/EDU.md#edu-09) | **Tổng quan tài liệu có trích dẫn kiểm chứng** | Sinh viên, nghiên cứu viên | Web app nghiên cứu | 18 | [→](#d-edu09) |
| 16 | [VMEC-08](topics/VMEC.md#vmec-08) | **Nhật ký huyết áp có hướng dẫn tham khảo** | Người lớn tuổi, người thân | PWA + bot nhắc đo | 16 | [→](#c2-vmec08) |

> Điểm /30 = 6 tiêu chí × thang 5: khớp background team · khớp mentor · dữ liệu công khai có sẵn · đo được độ chính xác · ảnh hưởng thấp tới người dùng · đề tài phụ dễ và làm sâu được. Điểm mang tính định hướng, nên chấm lại cùng mentor.

---

### Chi tiết tổng hợp từng đề tài

#### 1. Phễu chuyển đổi: rơi ở đâu, vì sao — [BDSO2O-11](topics/BDSO2O.md#bdso2o-11) · [phân tích sâu](#c2-funnel)
- **Đề gốc:** FunnelOptimizer AI Agent (bất động sản O2O). Team gọi là AI20K-062. → Mở rộng cho **TMĐT và du lịch**.
- **Phân tích nhanh:** khớp nhất với marketing (SEO, funnel); dữ liệu công khai sẵn (GA4 sample, Olist, REES46); mọi con số do SQL tính nên kiểm chứng được; rủi ro người dùng rất thấp.
- **Đối tượng:** marketer, chủ shop online, doanh nghiệp du lịch nhỏ.
- **Input:** file xuất GA4/CSV sự kiện hoặc kết nối GA4 chỉ đọc; chi phí quảng cáo; câu hỏi tự nhiên.
- **Output:** web app gồm sơ đồ phễu, danh sách điểm rơi đáng chú ý, ô chat trả lời "vì sao" kèm số liệu, biểu đồ và **câu SQL đã chạy**; thanh trượt mô phỏng "nếu cải thiện bước X"; báo cáo tuần qua email.

#### 2. Tra cứu thuế có trích điều khoản cho hộ kinh doanh — [BO-13](topics/BO.md#bo-13) · [phân tích sâu](#c2-bo13)
- **Đề gốc:** Tax & Compliance Agent.
- **Phân tích nhanh:** văn bản pháp luật công khai, miễn phí; đo được độ đúng trích dẫn; mentor fintech hỗ trợ trực tiếp; cần luôn ghi phạm vi tham khảo.
- **Đối tượng:** hộ kinh doanh, chủ shop online, kế toán doanh nghiệp nhỏ.
- **Input:** câu hỏi tự nhiên; loại hình kinh doanh; doanh thu, số lao động (tùy chọn).
- **Output:** chatbot trả lời bằng ngôn ngữ đời thường + danh sách căn cứ (số hiệu, điều, khoản, còn hiệu lực/đã bị thay thế) + mở văn bản gốc đúng đoạn; máy tính thuế/BHXH ra số kèm công thức.

#### 3. Cảnh báo lừa đảo trước khi tin, trước khi chuyển tiền — [FIN-19](topics/FIN.md#fin-19) · [phân tích sâu](#d-fin19)
- **Đề gốc:** AI Agent chống lừa đảo & cảnh báo giao dịch rủi ro.
- **Phân tích nhanh:** dữ liệu công khai nhiều (PhishTank, OpenPhish, URLhaus, tin cảnh báo trên báo chí); mentor fintech; dev mạng có lợi thế an toàn thông tin; demo trực quan; cạnh tranh đông nên USP phải là **kịch bản Việt + giải thích lý do**.
- **Đối tượng:** người dùng phổ thông, đặc biệt người lớn tuổi; nhóm cộng đồng.
- **Input:** tin nhắn dán vào, ảnh chụp màn hình, đường link, số tài khoản/số điện thoại người yêu cầu chuyển tiền.
- **Output:** mức nghi ngờ (thấp/vừa/cao) + 3 lý do kèm bằng chứng (tên miền giống thật, đòi OTP, tạo áp lực…) + việc nên làm tiếp; người dùng tự quyết định.

#### 4. Social listening cho thương hiệu nhỏ — [GSM-15](topics/GSM.md#gsm-15) · [phân tích sâu](#c2-gsm15)
- **Đề gốc:** lắng nghe mạng xã hội về dịch vụ gọi xe. → Mở rộng cho **mọi thương hiệu/ngành**.
- **Phân tích nhanh:** đúng thế mạnh marketing; dữ liệu cào công khai; rủi ro người dùng rất thấp; là đề tài phụ tự nhiên của #1.
- **Đối tượng:** marketer, chủ doanh nghiệp nhỏ, agency nhỏ.
- **Input:** tên thương hiệu, từ khóa, đối thủ, khoảng thời gian.
- **Output:** dashboard cảm xúc theo khía cạnh, chủ đề mới nổi kèm câu gốc (ẩn tên người viết), cảnh báo tiêu cực tăng đột biến qua email/Telegram, báo cáo tuần.

#### 5. Review du lịch theo khía cạnh — [GSM-06](topics/GSM.md#gsm-06) · [phân tích sâu](#d-gsm06)
- **Đề gốc:** phân tích đánh giá & chấm điểm chất lượng chuyến đi.
- **Phân tích nhanh:** sát nghiệp vụ du lịch nhất; có bộ nhãn sẵn (VLSP 2018 ABSA khách sạn/nhà hàng); bài toán ABSA phổ biến nên USP nằm ở **ngách du lịch Việt + việc nên sửa**.
- **Đối tượng:** nhà xe, khách sạn, công ty tour nhỏ.
- **Input:** tên doanh nghiệp/đối thủ, nguồn review công khai hoặc file review tự xuất.
- **Output:** dashboard khen/chê theo khía cạnh (xe, tài xế, đúng giờ, giá, sạch sẽ) đa ngôn ngữ, câu trích gốc, "3 việc nên sửa trước", so sánh đối thủ.

#### 6. Trợ lý tuyển sinh liên trường có trích dẫn — [EDU-12](topics/EDU.md#edu-12) · [phân tích sâu](#d-edu12)
- **Đề gốc:** trợ lý tuyển sinh AI tư vấn ứng viên.
- **Phân tích nhanh:** mentor giáo dục; marketing giáo dục + SEO; dữ liệu đề án, điểm chuẩn công khai; mùa vụ (tháng 3–8); mỗi đề án một định dạng.
- **Đối tượng:** học sinh lớp 11–12, phụ huynh.
- **Input:** điểm dự kiến, tổ hợp môn, khu vực, ngành quan tâm, câu hỏi tự nhiên.
- **Output:** chatbot trả lời có trích trang đề án; trang so sánh ngành giữa các trường; ước tính khả năng đỗ theo điểm chuẩn lịch sử (code thống kê, ghi rõ là tham khảo).

#### 7. So sánh & hiểu gói khám trước khi mua — [VMEC-15](topics/VMEC.md#vmec-15) · [phân tích sâu](#c2-vmec15)
- **Đề gốc:** đặt & quản lý gói khám sức khỏe định kỳ. → Bỏ đặt lịch thật, giữ so sánh và giải thích.
- **Phân tích nhanh:** dữ liệu là bảng giá/gói công bố công khai; tái dùng kỹ năng chuẩn hóa bảng giá; rủi ro thấp vì không đụng chẩn đoán.
- **Đối tượng:** người đi khám định kỳ, nhân sự doanh nghiệp mua gói cho nhân viên.
- **Input:** tuổi, giới, ngân sách, khu vực, mối quan tâm.
- **Output:** website so sánh 3–5 gói (hạng mục chuẩn hóa, giá, nguồn, ngày cập nhật), hạng mục trùng/thiếu so với khuyến cáo, chatbot giải thích từng hạng mục có trích nguồn.

#### 8. Chuẩn hóa bảng giá nhà cung cấp — [IDP-03](topics/IDP.md#idp-03) · [phân tích sâu](#d-idp03)
- **Đề gốc:** PriceSheet Normalizer.
- **Phân tích nhanh:** khớp nghiệp vụ mua hàng + kinh nghiệm TMĐT; bảng giá công khai trên website NCC + dữ liệu tổng hợp; ít "wow" khi demo.
- **Đối tượng:** người mua hàng, chủ shop, doanh nghiệp nhỏ.
- **Input:** file bảng giá Excel/PDF/ảnh từ nhiều nhà cung cấp.
- **Output:** bảng chuẩn (mã, tên, đơn vị, đơn giá, hiệu lực), mỗi số chỉ đúng ô gốc; bảng so giá giữa các NCC; cảnh báo NCC tăng giá.

#### 9. CV & phỏng vấn thử theo JD thật — [EDU-17](topics/EDU.md#edu-17) · [phân tích sâu](#d-edu17)
- **Đề gốc:** agent tối ưu CV và phỏng vấn thử cho sinh viên.
- **Phân tích nhanh:** mentor giáo dục; ESCO/O*NET công khai; thị trường đông đối thủ; cào tin tuyển dụng phải tôn trọng điều khoản.
- **Đối tượng:** sinh viên năm cuối, người mới đi làm.
- **Input:** CV (PDF), vị trí ứng tuyển hoặc link JD.
- **Output:** bảng khoảng trống kỹ năng có dẫn chứng từ JD, gợi ý viết lại (không bịa kinh nghiệm), phiên phỏng vấn thử có chấm theo rubric.

#### 10. Kiểm chứng tin forward — [CHAT-37](topics/CHAT.md#chat-37) · [phân tích sâu](#d-chat37)
- **Đề gốc:** chatbot kiểm tra tin giả và xác minh thông tin.
- **Phân tích nhanh:** dữ liệu công khai (FEVER, X-Fact, báo chính thống); khó đánh giá đúng/sai khách quan; ghép tốt với #3.
- **Đối tượng:** người dùng phổ thông, quản trị nhóm cộng đồng.
- **Input:** đoạn tin/ảnh chụp màn hình được forward.
- **Output:** từng khẳng định trong tin + bằng chứng ủng hộ/bác bỏ từ nguồn chính thống + kết luận "chưa đủ dữ liệu" khi cần.

#### 11. Đọc hiểu sao kê: tiền đi đâu — [FIN-09](topics/FIN.md#fin-09) · [phân tích sâu](#d-fin09)
- **Đề gốc:** phân loại & phân tích giao dịch tự động.
- **Phân tích nhanh:** mentor fintech; dataset nước ngoài + **sao kê tổng hợp** theo định dạng Việt; USP mỏng vì thiếu dữ liệu thật tiếng Việt.
- **Đối tượng:** người dùng cá nhân, sinh viên quản lý chi tiêu.
- **Input:** file sao kê CSV/PDF tự tải từ ngân hàng.
- **Output:** dashboard chi tiêu theo danh mục và merchant, khoản định kỳ (subscription), thống kê tính bằng code.

#### 12. Lên lộ trình & ước tính chi phí du lịch — [GSM-19](topics/GSM.md#gsm-19) · [phân tích sâu](#c2-gsm19)
- **Đề gốc:** trợ lý đặt xe đa phương thức. → Bỏ đặt xe thật, giữ lập lộ trình và chi phí.
- **Phân tích nhanh:** khớp nghiệp vụ du lịch; dữ liệu giá phân tán, khó đo độ đúng; cạnh tranh với công cụ bản đồ lớn ở phần đường đi.
- **Đối tượng:** khách du lịch trong nước và nước ngoài, công ty tour nhỏ.
- **Input:** câu tự nhiên: điểm đi/đến, ngày, số người, hành lý, ngân sách.
- **Output:** chatbot + bản đồ hiện 2–3 thẻ lộ trình (chặng, phương tiện, thời gian, khoảng giá, nguồn giá), chỉnh điểm dừng, chia sẻ link.

#### 13. Lộ trình đường dài có điểm sạc xe điện — [VFO2O-19](topics/VFO2O.md#vfo2o-19) · [phân tích sâu](#d-vfo2o19)
- **Đề gốc:** lập kế hoạch chuyến đi & sạc pin.
- **Phân tích nhanh:** bài toán "code tính" rõ; OpenChargeMap, OSM công khai; dữ liệu trạm Việt Nam có thể thiếu.
- **Đối tượng:** chủ xe điện, người thuê xe điện đi đường dài.
- **Input:** điểm đi/đến, mẫu xe, % pin hiện tại.
- **Output:** bản đồ lộ trình có điểm sạc, % pin dự kiến từng chặng, cảnh báo đoạn thiếu trạm.

#### 14. Khoảng giá căn hộ thứ cấp từ tin rao — [BDSO2O-16](topics/BDSO2O.md#bdso2o-16) · [phân tích sâu](#d-bdso2o16)
- **Đề gốc:** định giá & thẩm định căn hộ chuyển nhượng.
- **Phân tích nhanh:** dữ liệu tin rao nhiều; không khớp nghiệp vụ team; giá rao khác giá chốt.
- **Đối tượng:** người mua/bán căn hộ, môi giới.
- **Input:** địa chỉ/dự án, diện tích, tầng, số phòng, nội thất.
- **Output:** khoảng giá tham khảo + căn so sánh + yếu tố ảnh hưởng + cảnh báo dữ liệu mỏng.

#### 15. Tổng quan tài liệu có trích dẫn kiểm chứng — [EDU-09](topics/EDU.md#edu-09) · [phân tích sâu](#d-edu09)
- **Đề gốc:** LitReview Agent.
- **Phân tích nhanh:** mentor giáo dục; API học thuật miễn phí; đối thủ quốc tế rất mạnh nên khó tạo USP.
- **Đối tượng:** sinh viên làm khóa luận, nghiên cứu viên.
- **Input:** chủ đề/câu hỏi nghiên cứu, khoảng năm.
- **Output:** danh sách bài báo đã sàng lọc, bảng tổng hợp phương pháp/kết quả, mọi khẳng định gắn DOI kiểm chứng được.

#### 16. Nhật ký huyết áp có hướng dẫn tham khảo — [VMEC-08](topics/VMEC.md#vmec-08) · [phân tích sâu](#c2-vmec08)
- **Đề gốc:** theo dõi & quản lý tăng huyết áp tại nhà. → Chỉ nhật ký, nhắc, giáo dục; không đổi thuốc.
- **Phân tích nhanh:** rủi ro cao nhất danh sách; cần chuyên gia y tế đồng hành; dữ liệu test công khai (NHANES, Synthea).
- **Đối tượng:** người lớn tuổi có tăng huyết áp, người thân chăm sóc.
- **Input:** số đo tự nhập hoặc ảnh màn hình máy đo; bữa ăn (tùy chọn).
- **Output:** PWA nhật ký + biểu đồ, phân độ theo khuyến cáo, cảnh báo đi khám/cấp cứu khi vượt ngưỡng, nhắc đo qua bot, báo cáo PDF cho bác sĩ.

---

## <a id="phan-2"></a>PHẦN 2 – PHÂN TÍCH SÂU TỪNG ĐỀ TÀI KÈM ĐỀ TÀI PHỤ

> [!IMPORTANT]
> **Nguyên tắc chính – phụ**
> 1. **Một đề tài chính** quyết định người dùng, dữ liệu và chỉ số. Đề tài phụ chỉ được chọn nếu **dùng chung dữ liệu hoặc chung người dùng** với đề tài chính và **làm sâu thêm** đề tài chính, không mở sang hướng mới.
> 2. Đề tài phụ phải **không quá khó**: tái dùng lõi kỹ thuật đã có, không cần dữ liệu doanh nghiệp, không huấn luyện mô hình lớn.
> 3. **Thứ tự:** làm đề tài chính đến khi đạt chỉ số → thêm phụ 1 → phụ 2. Không làm song song.
> 4. Tên, quy mô và giấy phép các bộ dữ liệu cần kiểm tra lại trên trang nguồn trước khi chốt kế hoạch.

### Bảng chính – phụ

| Đề tài chính | Phụ 1 | Phụ 2 | Phụ 3 (tùy chọn) | Lõi kỹ thuật dùng chung |
|---|---|---|---|---|
| [**BDSO2O-11** Phễu](#c2-funnel) | DATA-01 Hỏi dữ liệu bằng câu tự nhiên | GSM-15 Tín hiệu mạng xã hội | GSM-11 Ưu đãi theo uplift | Kho sự kiện + SQL kiểm chứng + LLM diễn giải |
| [**BO-13** Thuế](#c2-bo13) | BO-12 Máy tính thuế TNCN/BHXH | BO-18 Quy định lao động | IDP-01 Hóa đơn điện tử XML | RAG pháp luật + đồ thị hiệu lực + máy tính quy tắc |
| [**FIN-19** Lừa đảo](#d-fin19) | CHAT-08 Link độc & tin giả | CHAT-37 Kiểm chứng tin | CHAT-26 Kiểm duyệt theo ngữ cảnh | Trích xuất thực thể + kiểm tra link + phân loại kịch bản |
| [**GSM-15** Mạng xã hội](#c2-gsm15) | GSM-06 Khía cạnh | CHAT-25 Chủ đề mới nổi | CHAT-37 Kiểm chứng tin | Cào → cảm xúc/khía cạnh → gom cụm theo thời gian |
| [**GSM-06** Review du lịch](#d-gsm06) | CHAT-25 Chủ đề mới nổi | BDSO2O-09 Theo dõi đối thủ | CHAT-03 Đa ngôn ngữ | ABSA + gom cụm + báo cáo có trích câu |
| [**EDU-12** Tuyển sinh](#d-edu12) | EDU-04 Kho tri thức có trích dẫn | EDU-06 Lộ trình học | EDU-17 Ngành → nghề | RAG đa trường + thống kê điểm chuẩn |
| [**VMEC-15** Gói khám](#c2-vmec15) | IDP-03 Chuẩn hóa bảng giá | VMEC-09 Giáo dục sức khỏe | VMEC-17 Phản hồi bệnh nhân | Cào → chuẩn hóa danh mục/giá → RAG giải thích |
| [**IDP-03** Bảng giá NCC](#d-idp03) | IDP-09 EvidenceView | BO-04 So sánh nhà cung cấp | IDP-11 Định tuyến rẻ | Trích bảng + ánh xạ cột + kiểm tra bằng code |
| [**EDU-17** CV](#d-edu17) | BO-15 JD & khung năng lực | EDU-06 Lộ trình học | EDU-12 Tuyển sinh | ESCO/O*NET + so khớp kỹ năng |
| [**CHAT-37** Tin giả](#d-chat37) | CHAT-08 Link độc | CHAT-24 Tìm kiếm có trích nguồn | FIN-19 Lừa đảo | Tách khẳng định + truy hồi bằng chứng |
| [**FIN-09** Sao kê](#d-fin09) | FIN-01 Ngân sách cá nhân | FIN-18 Dự báo dòng tiền | – | Phân loại giao dịch + thống kê bằng code |
| [**GSM-19** Lộ trình](#c2-gsm19) | BDSO2O-19 Lịch trình nhiều điểm | GSM-06 Chất lượng nhà xe | CHAT-03 Đa ngôn ngữ | OSM/OSRM + bảng giá + tối ưu lộ trình |
| [**VFO2O-19** Xe điện](#d-vfo2o19) | VFO2O-11 Chi phí sử dụng xe điện | GSM-19 Lộ trình đa phương thức | – | OSM/OSRM + mô hình tiêu hao bằng code |
| [**BDSO2O-16** Căn hộ](#d-bdso2o16) | BDSO2O-09 Theo dõi thị trường | BDSO2O-05 Gợi ý căn theo nhu cầu | – | Kho tin rao + căn so sánh + hồi quy |
| [**EDU-09** Tài liệu](#d-edu09) | VIN-10 Cổng học giả | EDU-04 Kho tri thức | – | API học thuật + RAG có DOI |
| [**VMEC-08** Huyết áp](#c2-vmec08) | VMEC-09 Giáo dục sức khỏe | VMEC-10 Dinh dưỡng | VMEC-04 Nhắc thuốc (chỉ nhắc lịch) | Nhật ký + ngưỡng bằng code + RAG |

---

### <a id="c2-vmec15"></a>1. Chính: `[VMEC-15]` Gói khám sức khỏe định kỳ → "So sánh & hiểu gói khám trước khi mua"

**Định vị lại:** bỏ phần đặt lịch thật của đề gốc (cần hệ thống bệnh viện), giữ phần **tư vấn và so sánh gói**. Người dùng biết gói nào phù hợp tuổi/giới, hạng mục nào trùng, giá ở đâu, rồi tự liên hệ cơ sở.

**Đề tài phụ**
| Phụ | Lấy gì từ đề tài phụ | Làm sâu đề tài chính ở chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **IDP-03** PriceSheet Normalizer | Kỹ thuật chuẩn hóa bảng giá nhiều bố cục | Gom gói khám của nhiều cơ sở (PDF, ảnh, bảng HTML) về **một danh mục hạng mục chuẩn** → so sánh được | Thấp | Bảng giá/gói khám cào |
| **VMEC-09** Giáo dục sức khỏe có nguồn | RAG chỉ trả lời từ tài liệu đã duyệt | Giải thích **từng hạng mục** (xét nghiệm gì, phát hiện gì, ai nên làm) có trích nguồn | Thấp | Tài liệu công khai của Bộ Y tế, WHO, khuyến cáo tầm soát công khai |
| **VMEC-17** Phản hồi bệnh nhân (tùy chọn) | Phân loại chủ đề + cảm xúc | Bổ sung **trải nghiệm thực tế** (thời gian chờ, trả kết quả) cho từng cơ sở | Trung bình | Review công khai (cào, ẩn danh) |

**Tầng đào sâu theo dữ liệu**
| Tầng | Cần thêm dữ liệu gì | Năng lực mới |
|---|---|---|
| L0 | Gói khám của 10 cơ sở | Danh mục hạng mục chuẩn, so sánh giá |
| L1 | 50+ cơ sở, nhiều tỉnh | Bản đồ giá theo khu vực, phát hiện gói "đắt bất thường" so với tổng hạng mục |
| L2 | Khuyến cáo tầm soát theo tuổi/giới | Gợi ý "gói tối thiểu nên có" + hạng mục thừa/thiếu |
| L3 | Tài liệu giải thích hạng mục | Giải thích từng hạng mục (VMEC-09) |
| L4 | Review công khai | Điểm trải nghiệm từng cơ sở (VMEC-17) |

**Đối tượng:** người đi khám định kỳ; doanh nghiệp/nhân sự mua gói khám cho nhân viên; (sau này) phòng khám muốn so sánh với đối thủ.

**Input → Output**
| Input | Output |
|---|---|
| Tuổi, giới, ngân sách, khu vực, mối quan tâm (tim mạch, tiêu hóa…) | Bảng so sánh 3–5 gói: hạng mục chuẩn hóa, giá, nguồn + ngày cập nhật; hạng mục trùng/thiếu so với khuyến cáo; giải thích từng hạng mục có trích nguồn; danh bạ cơ sở để tự liên hệ |

**Hình thái sản phẩm & cách tương tác**
- **Sản phẩm:** website so sánh gói khám + chatbot hỏi đáp ở góc trang; trang quản trị cho người duyệt.
- **Người đi khám:** chọn tuổi, giới, ngân sách, khu vực → hệ thống hiện 3–5 gói phù hợp dạng thẻ → bấm "So sánh" để xem bảng hạng mục cạnh nhau (có/không có) → bấm vào một hạng mục để chatbot giải thích kèm nguồn → bấm "Liên hệ cơ sở" để mở trang chính thức của cơ sở (hệ thống **không** đặt lịch).
- **Nhân sự doanh nghiệp:** nhập số nhân viên theo nhóm tuổi → nhận bảng so sánh tổng chi phí giữa các cơ sở, xuất Excel.
- **Người duyệt (team/mentor):** xem hàng chờ hạng mục chưa ánh xạ được về danh mục chuẩn → chọn mục đúng hoặc tạo mục mới → duyệt phần giải thích hạng mục trước khi hiển thị.
- **Kịch bản demo 3 phút:** "Nữ 45 tuổi, ngân sách 3 triệu, Hà Nội" → 4 gói → so sánh → hỏi "xét nghiệm CA 15-3 là gì" → câu trả lời có trích nguồn.

**Dataset & cách làm:** (1) danh sách cơ sở y tế công khai → (2) cào trang/PDF gói khám, lưu bản gốc + thời điểm cào → (3) trích hạng mục bằng LLM có cấu trúc, ánh xạ về danh mục chuẩn (marketing + mentor duyệt danh mục) → (4) giá xử lý bằng code → (5) golden set 30 gói nhập tay để đo độ đúng trích xuất.

**Triển khai:** T1–4 cào + danh mục chuẩn · T5–8 MVP so sánh (IDP-03) · T9–12 gợi ý theo tuổi/giới + giải thích (VMEC-09) · T13–18 mở rộng cơ sở/tỉnh, cập nhật định kỳ · T19–24 review (VMEC-17) và thử với người dùng.

**Tư duy ngược:** giá cũ → hiển thị ngày cập nhật, cào định kỳ; ánh xạ sai hạng mục → ô không chắc chắn hiện cho người duyệt; người dùng coi là lời khuyên y khoa → câu chữ "tham khảo", khuyên hỏi bác sĩ; cơ sở phản đối bị so sánh → chỉ dùng thông tin họ tự công bố, ghi nguồn.

**Chỉ số:** độ đúng trích hạng mục/giá; tỷ lệ gói được ánh xạ đủ; độ đúng trích dẫn giải thích; số người dùng thử.

---

### <a id="c2-vmec08"></a>2. Chính: `[VMEC-08]` Theo dõi huyết áp tại nhà → "Nhật ký huyết áp có hướng dẫn tham khảo"

**Định vị lại:** chỉ **ghi nhận, vẽ xu hướng, nhắc đo, giáo dục**; khi vượt ngưỡng theo khuyến cáo thì **khuyên đi khám/cấp cứu**; tuyệt đối không đổi thuốc hay chẩn đoán.

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **VMEC-09** Giáo dục sức khỏe | RAG có nguồn, từ chối ngoài phạm vi | Trả lời "đo thế nào cho đúng", "chỉ số này nghĩa là gì" | Thấp | Khuyến cáo công khai của WHO, Bộ Y tế, các hội tim mạch |
| **VMEC-10** Dinh dưỡng | Tính dinh dưỡng bằng code | Gợi ý **giảm muối** theo bữa ăn người dùng ghi, theo nguyên tắc DASH | Trung bình | Bảng thành phần thực phẩm công bố, Open Food Facts (hàm lượng natri) |
| **VMEC-04** Nhắc thuốc (tùy chọn, giới hạn) | Lịch nhắc | Chỉ nhắc theo **lịch người dùng/bác sĩ đã nhập**, ghi nhận đã uống | Thấp | Không cần dữ liệu ngoài |

**Tầng đào sâu**
| Tầng | Dữ liệu | Năng lực |
|---|---|---|
| L0 | Số đo tự nhập | Nhật ký, biểu đồ, phân độ theo khuyến cáo |
| L1 | Ảnh màn hình máy đo | Đọc số từ ảnh (OCR màn hình số) để nhập nhanh |
| L2 | Chuỗi nhiều tuần | Xu hướng sáng/tối, phát hiện chuỗi đo cao liên tiếp → khuyên đi khám |
| L3 | Tài liệu giáo dục | Hỏi đáp có nguồn (VMEC-09) |
| L4 | Nhật ký ăn uống | Ước tính natri, gợi ý giảm muối (VMEC-10) |
| L5 | Báo cáo | PDF tổng hợp mang theo khi tái khám |

**Đối tượng:** người lớn tuổi có tăng huyết áp, người thân chăm sóc.

**Input → Output**
| Input | Output |
|---|---|
| Số đo (tâm thu, tâm trương, nhịp tim, thời điểm) hoặc ảnh màn hình máy đo; bữa ăn (tùy chọn) | Biểu đồ xu hướng; phân độ theo khuyến cáo kèm nguồn; cảnh báo "nên đi khám / gọi cấp cứu" khi vượt ngưỡng; nhắc đo; gợi ý giảm muối; báo cáo PDF cho bác sĩ |

**Hình thái sản phẩm & cách tương tác**
- **Sản phẩm:** ứng dụng web di động (PWA, cài như app, không qua kho ứng dụng) + bot Zalo/Telegram để nhắc đo và nhận số đo nhanh.
- **Người bệnh:** mở app hoặc nhắn bot "135/85, mạch 78" hoặc gửi ảnh màn hình máy đo → hệ thống đọc số, hỏi xác nhận → lưu → hiện biểu đồ 7/30 ngày kèm phân độ theo khuyến cáo → nếu vượt ngưỡng khẩn: màn hình đỏ "Hãy gọi 115 / đến cơ sở y tế ngay" kèm nút gọi → hỏi kiến thức chung ở tab "Hỏi" → bấm "Xuất báo cáo" để có PDF mang theo khi tái khám.
- **Người thân:** được người bệnh mời → xem biểu đồ, nhận thông báo khi chỉ số vượt ngưỡng hoặc người bệnh quên đo nhiều ngày.
- **Người duyệt nội dung y khoa (mentor/chuyên gia):** duyệt kho tài liệu giáo dục và bảng ngưỡng trước khi đưa lên.
- **Kịch bản demo 3 phút:** gửi ảnh máy đo → xác nhận số → biểu đồ cập nhật → nhập số đo cao bất thường → màn hình cảnh báo → xuất PDF.

**Dataset & cách làm:** NHANES (số đo huyết áp công khai nhiều năm) và Synthea (bệnh nhân tổng hợp) để **test** biểu đồ, phát hiện chuỗi bất thường; khuyến cáo công khai làm kho RAG và **bảng ngưỡng viết bằng code**; ảnh màn hình máy đo tự chụp (team tự tạo 200–300 ảnh) để đo OCR. Không thu dữ liệu người dùng thật trong giai đoạn đầu.

**Triển khai:** T1–4 nhật ký + ngưỡng bằng code + test NHANES · T5–8 MVP + cảnh báo · T9–12 OCR màn hình máy đo · T13–16 giáo dục (VMEC-09) · T17–22 dinh dưỡng (VMEC-10) · T23–24 báo cáo PDF + rà soát an toàn với mentor.

**Tư duy ngược:** bỏ sót cơn tăng huyết áp nguy hiểm → ngưỡng khẩn viết cứng bằng code, test 100%; người dùng tự giảm thuốc theo app → không có chức năng nào nói về liều; OCR đọc sai → luôn cho người dùng xác nhận số trước khi lưu; lộ dữ liệu sức khỏe → mã hóa, không chia sẻ, cho xóa dữ liệu.

**Chỉ số:** 100% ca vượt ngưỡng khẩn được cảnh báo; độ đúng OCR; độ đúng trích dẫn; tỷ lệ người dùng thử duy trì ghi nhật ký.

> ⚠️ Đây là đề tài **rủi ro cao nhất** trong 6 đề tài. Nên có ý kiến chuyên gia y tế trước khi chọn làm đề tài chính.

---

### <a id="c2-gsm15"></a>3. Chính: `[GSM-15]` Lắng nghe mạng xã hội → "Social listening cho thương hiệu nhỏ"

**Định vị lại:** đề gốc dành cho dịch vụ gọi xe; mở rộng cho **mọi thương hiệu/ngành** (du lịch, phòng khám, shop online) – đúng thế mạnh marketing của team.

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **GSM-06** Phân tích đánh giá | Phân tích theo khía cạnh (ABSA) | Không chỉ "tích cực/tiêu cực" mà **khen/chê khía cạnh nào** (giá, thái độ, đúng giờ) | Thấp | VLSP 2018 ABSA, bộ cảm xúc tiếng Việt của UIT |
| **CHAT-25** Community Intelligence | Gom cụm chủ đề, chủ đề nổi lên | Phát hiện **chủ đề mới nổi** và **đột biến** theo thời gian | Trung bình | Chính dữ liệu đã cào |
| **CHAT-37** Kiểm chứng tin (tùy chọn) | Tách khẳng định, tìm bằng chứng | Khi khủng hoảng: tin đồn về thương hiệu **đúng hay sai** so với báo chính thống | Trung bình | Báo chính thống cào |

**Tầng đào sâu**
| Tầng | Dữ liệu | Năng lực |
|---|---|---|
| L0 | Bình luận/bài công khai 1 thương hiệu | Cảm xúc + chủ đề + dashboard |
| L1 | Nhãn khía cạnh | ABSA (GSM-06) |
| L2 | 6–12 tháng dữ liệu | Chủ đề nổi lên, phát hiện đột biến (CHAT-25) |
| L3 | Dữ liệu đối thủ | So sánh với đối thủ cùng ngành |
| L4 | Báo chính thống | Cảnh báo khủng hoảng + kiểm chứng tin (CHAT-37) |
| L5 | Lịch sử phản hồi | Nháp phản hồi truyền thông (người duyệt trước khi đăng) |

**Đối tượng:** marketing/chủ doanh nghiệp nhỏ, agency nhỏ.

**Input → Output**
| Input | Output |
|---|---|
| Tên thương hiệu, từ khóa, đối thủ, khoảng thời gian | Dashboard cảm xúc theo khía cạnh; top chủ đề + câu trích gốc; chủ đề mới nổi; cảnh báo tiêu cực tăng đột biến; báo cáo tuần |

**Hình thái sản phẩm & cách tương tác**
- **Sản phẩm:** dashboard web cho doanh nghiệp + cảnh báo qua email/Telegram + báo cáo PDF hằng tuần.
- **Marketer / chủ doanh nghiệp:** tạo "dự án theo dõi" (tên thương hiệu, từ khóa, 2–3 đối thủ) → hệ thống cào định kỳ → dashboard hiện biểu đồ cảm xúc theo thời gian, bảng khía cạnh (giá, thái độ, chất lượng…) được khen/chê, danh sách chủ đề nổi lên → bấm vào một chủ đề để xem các câu gốc (đã ẩn tên người viết) → nhận tin nhắn khi bình luận tiêu cực tăng đột biến → (tầng L5) xem nháp phản hồi truyền thông và tự quyết định có dùng hay không.
- **Người gán nhãn (marketing):** mở màn hình gán nhãn, sửa khía cạnh/cảm xúc AI gán sai → dữ liệu đã sửa dùng để đo và cải thiện.
- **Kịch bản demo 3 phút:** chọn một thương hiệu du lịch → dashboard 3 tháng → bấm khía cạnh "đúng giờ" đang đỏ → xem câu gốc → mô phỏng một đợt tiêu cực → cảnh báo Telegram đến.

**Dataset & cách làm:** chỉ cào nguồn có API hoặc điều khoản cho phép (bình luận video công khai qua API, diễn đàn, báo điện tử, review bản đồ); ẩn danh tên người viết; nhãn: marketing gán 500 câu theo bộ khía cạnh của ngành chọn; đánh giá bằng VLSP/UIT + golden set tự gán.

**Triển khai:** T1–4 pipeline cào + lọc spam · T5–8 MVP cảm xúc + chủ đề · T9–12 ABSA (GSM-06) · T13–18 chủ đề nổi lên + đột biến (CHAT-25) · T19–24 so sánh đối thủ, kiểm chứng tin (CHAT-37) nếu kịp.

**Tư duy ngược:** nền tảng chặn cào → ưu tiên nguồn có API, tốc độ thấp; mỉa mai tiếng Việt bị hiểu sai → đo riêng tập mỉa mai, hiển thị câu gốc; báo động giả → ngưỡng đột biến thống kê, người duyệt xác nhận; vi phạm quyền riêng tư → không lưu tên người dùng, chỉ thống kê.

**Chỉ số:** F1 cảm xúc và khía cạnh; độ chính xác cảnh báo đột biến; thời gian từ lúc xuất hiện đến lúc cảnh báo.

---

### <a id="c2-gsm19"></a>4. Chính: `[GSM-19]` Lộ trình đa phương thức → "Lên lộ trình & ước tính chi phí du lịch"

**Định vị lại:** bỏ phần đặt và thanh toán loạt chuyến (cần hệ thống nhà xe – "bẫy" của đề gốc); giữ **lập lộ trình nhiều điểm, so sánh phương tiện, ước tính chi phí**.

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **BDSO2O-19** TourConcierge | Tối ưu thứ tự điểm dừng (OR-Tools) | Lịch trình **nhiều ngày nhiều điểm** tối ưu thời gian/chi phí | Trung bình | OSM/OSRM |
| **GSM-06** Phân tích đánh giá | ABSA review | Gợi ý **nhà xe/nhà ga đáng tin** theo đúng giờ, an toàn, thái độ | Thấp | Review công khai cào |
| **CHAT-03** Dịch đa ngôn ngữ (tùy chọn) | Dịch có glossary | Phục vụ **khách nước ngoài** (thế mạnh nghiệp vụ của marketing) | Thấp | FLORES-200, glossary địa danh tự biên soạn |

**Tầng đào sâu**
| Tầng | Dữ liệu | Năng lực |
|---|---|---|
| L0 | OSM + giá xe riêng tham chiếu | Lộ trình 1 chặng + ước tính chi phí bằng code |
| L1 | Lịch/giá vé xe khách, tàu công khai | So sánh phương tiện |
| L2 | — | Lịch trình nhiều điểm tối ưu (BDSO2O-19) |
| L3 | Review | Chọn nhà xe uy tín (GSM-06) |
| L4 | Glossary đa ngôn ngữ | Khách nước ngoài (CHAT-03) |

**Đối tượng:** khách du lịch trong nước và nước ngoài; (sau này) công ty tour nhỏ dùng để báo giá nhanh.

**Input → Output**
| Input | Output |
|---|---|
| Câu tự nhiên: điểm đi/đến, ngày, số người, hành lý, ngân sách | 2–3 phương án lộ trình; thời gian; khoảng chi phí kèm nguồn giá; gợi ý nhà xe theo review; bản tiếng nước ngoài |

**Hình thái sản phẩm & cách tương tác**
- **Sản phẩm:** chatbot trên website kèm bản đồ; mỗi phương án là một "thẻ lộ trình" (chặng, phương tiện, thời gian, khoảng giá, nguồn giá).
- **Khách du lịch:** gõ "Hà Nội đi Ninh Bình 2 ngày, 4 người, có trẻ nhỏ, ngân sách 3 triệu" → bot hỏi lại phần thiếu (ngày đi, có muốn xe riêng không) → hiện 2–3 phương án trên bản đồ → kéo thả để thêm/bớt điểm dừng, hệ thống tính lại → xem nhà xe gợi ý kèm điểm review → lưu hoặc chia sẻ link lộ trình; đặt xe/vé thì tự liên hệ nhà cung cấp (hệ thống **không** đặt hộ).
- **Khách nước ngoài:** dùng cùng giao diện bằng tiếng Anh (thêm ngôn ngữ khác ở giai đoạn sau).
- **Công ty tour nhỏ:** dùng bản nội bộ để lên nhanh lịch trình và khoảng giá cho khách, chỉnh trước khi gửi.
- **Người duyệt (marketing):** cập nhật bảng giá tham chiếu xe riêng, duyệt glossary địa danh.
- **Kịch bản demo 3 phút:** gõ yêu cầu → 3 phương án trên bản đồ → thêm điểm Tràng An → giá và thời gian cập nhật → đổi sang tiếng Anh.

**Dataset & cách làm:** Geofabrik OSM Việt Nam + OSRM tự host; cào lịch/giá vé công khai của nhà xe, tàu (lưu thời điểm cào); bảng giá xe riêng tham chiếu do marketing lập từ kinh nghiệm nghiệp vụ (ghi rõ là tham chiếu); MultiWOZ, Schema-Guided Dialogue để test phần hiểu yêu cầu.

**Triển khai:** T1–4 OSRM + bảng giá · T5–8 MVP 1 chặng · T9–12 đa phương tiện · T13–18 nhiều ngày (BDSO2O-19) · T19–24 review (GSM-06) + đa ngôn ngữ (CHAT-03).

**Tư duy ngược:** giá cào lỗi thời → luôn hiện ngày cập nhật, dải giá thay vì một số; cạnh tranh với Google Maps/Rome2Rio ở phần đường đi → USP nằm ở **chi phí và lịch trình du lịch Việt Nam**, không ở bản đồ; khó đo độ đúng → golden set 100 yêu cầu do marketing giải tay.

**Chỉ số:** độ đúng trích yêu cầu; sai số chi phí so với golden set; tỷ lệ lộ trình khả thi.

---

### <a id="c2-funnel"></a>5. Chính: `[BDSO2O-11]` FunnelOptimizer (AI20K-062) → "Phễu chuyển đổi: rơi ở đâu, vì sao"

**Định vị lại:** đề gốc dành cho bất động sản; mở rộng cho **TMĐT và du lịch** – nơi có dữ liệu phễu công khai và đúng kinh nghiệm SEO/funnel của marketing.

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **DATA-01** Text-to-SQL | Câu hỏi tự nhiên → SQL kiểm tra trước khi chạy | Người dùng **hỏi bất kỳ** ("vì sao tháng 3 giảm?") thay vì chỉ xem phễu cố định | Trung bình | Chính kho dữ liệu phễu; BIRD/Spider để học cách đánh giá |
| **GSM-15** Lắng nghe mạng xã hội | Cảm xúc + chủ đề | Giải thích **vì sao** khách rơi (khách đang chê gì) | Trung bình | Cào công khai |
| **GSM-11** Ưu đãi theo uplift (tùy chọn) | Mô hình uplift | Gợi ý **nhóm nào nên nhận ưu đãi** để kéo bước rơi | Trung bình | Criteo Uplift dataset (công khai) |

**Tầng đào sâu**
| Tầng | Dữ liệu | Năng lực |
|---|---|---|
| L0 | GA4 sample / Olist | Phễu, tỷ lệ chuyển đổi từng bước bằng SQL |
| L1 | Thêm chiều nguồn, thiết bị, thời gian | Phân khúc, cohort, phát hiện điểm rơi bất thường |
| L2 | — | Hỏi đáp tự nhiên (DATA-01) |
| L3 | Dữ liệu chi phí quảng cáo | Hiệu quả theo kênh, mô phỏng "nếu cải thiện bước X" |
| L4 | Bình luận công khai | Giải thích nguyên nhân (GSM-15) |
| L5 | Criteo Uplift | Gợi ý nhóm nhận ưu đãi (GSM-11) |

**Đối tượng:** marketer, chủ shop online, doanh nghiệp du lịch nhỏ.

**Input → Output**
| Input | Output |
|---|---|
| File xuất GA4/CSV sự kiện (hoặc kết nối GA4 đọc-only), chi phí quảng cáo, câu hỏi tự nhiên | Phễu từng bước; điểm rơi lớn nhất; giả thuyết nguyên nhân **kèm số liệu và câu SQL đã chạy**; mô phỏng tác động; báo cáo tuần |

**Hình thái sản phẩm & cách tương tác**
- **Sản phẩm:** web app phân tích gồm 3 vùng: (1) sơ đồ phễu, (2) danh sách "điểm rơi đáng chú ý", (3) ô chat hỏi dữ liệu; báo cáo tuần gửi email.
- **Marketer / chủ shop:** tải file CSV xuất từ GA4 hoặc kết nối GA4 quyền chỉ đọc → hệ thống kiểm tra chất lượng dữ liệu (thiếu cột, ngày trống) → hiện phễu xem → giỏ hàng → thanh toán → mua → bấm vào bước rơi mạnh nhất để xem phân tách theo nguồn/thiết bị → gõ "vì sao khách mobile rơi ở bước thanh toán tháng 3?" → nhận trả lời gồm số liệu, biểu đồ và **câu SQL đã chạy** (bấm để xem) → kéo thanh trượt "nếu tăng tỷ lệ bước này 5%" để xem doanh thu ước tính → (tầng L4) xem bình luận khách liên quan đến bước đó.
- **Quản trị / Data Engineer:** xem nhật ký câu hỏi, câu SQL lỗi, câu trả lời bị đánh giá "không hữu ích" để cải thiện.
- **Kịch bản demo 3 phút:** tải GA4 sample → phễu → điểm rơi thanh toán trên mobile → hỏi "vì sao" → số liệu + SQL → mô phỏng doanh thu.

**Dataset & cách làm:** Google Analytics sample dataset (GA4 ecommerce trên BigQuery public), Olist Marketing Funnel (Kaggle), REES46 e-commerce behavior (Kaggle) → nạp DuckDB/Postgres; **mọi con số do SQL/pandas tính**, LLM chỉ chọn câu hỏi phân tích và diễn giải; golden set 50 câu hỏi có đáp án do marketing + Data Engineer viết.

**Triển khai:** T1–4 kho dữ liệu + phễu SQL · T5–8 MVP phễu + điểm rơi + diễn giải · T9–12 hỏi đáp tự nhiên (DATA-01) + eval gate · T13–16 mô phỏng + cảnh báo bất thường · T17–22 tín hiệu mạng xã hội (GSM-15) · T23–24 uplift (GSM-11) nếu kịp, thử với 5–10 doanh nghiệp.

**Tư duy ngược:** LLM bịa số → số chỉ đến từ truy vấn, hiển thị câu SQL; nhầm tương quan là nhân quả → ghi "giả thuyết", đề xuất cách kiểm chứng (A/B); dữ liệu người dùng thật bẩn → bước kiểm tra chất lượng dữ liệu trước khi phân tích; lộ dữ liệu khách → chỉ đọc, không lưu dữ liệu thô quá thời gian cần.

**Chỉ số:** độ đúng câu trả lời trên golden set; tỷ lệ SQL chạy được; số giả thuyết được người dùng đánh giá hữu ích.

---

### <a id="c2-bo13"></a>6. Chính: `[BO-13]` Thuế & tuân thủ → "Tra cứu thuế có trích điều khoản cho hộ kinh doanh"

**Định vị lại:** tập trung **hộ kinh doanh, shop online, doanh nghiệp nhỏ**; trả lời có trích số hiệu/điều/khoản và **trạng thái hiệu lực** văn bản.

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **BO-12** Bảng lương | Tính thuế TNCN, BHXH **bằng code** | Từ "giải thích quy định" sang **tính ra số** cho từng tình huống | Thấp | Quy định công khai; bảng lương tổng hợp để test |
| **BO-18** Nội quy & vi phạm lao động | RAG Bộ luật Lao động | Câu hỏi về lao động thường đi kèm thuế/BHXH (hợp đồng, phụ cấp) | Thấp | Văn bản luật công khai |
| **IDP-01** Hóa đơn điện tử (tùy chọn) | Đọc XML hóa đơn điện tử | Kiểm tra hóa đơn có hợp lệ về mặt hình thức (trường bắt buộc, thuế suất) | Trung bình | Định dạng XML công khai + hóa đơn tổng hợp |

**Tầng đào sâu**
| Tầng | Dữ liệu | Năng lực |
|---|---|---|
| L0 | Văn bản thuế cho hộ kinh doanh | Hỏi đáp có trích dẫn |
| L1 | Metadata sửa đổi/thay thế | Đồ thị hiệu lực, cảnh báo văn bản hết hiệu lực |
| L2 | Quy tắc tính thuế | Máy tính thuế khoán/TNCN/BHXH bằng code (BO-12) |
| L3 | Văn bản lao động | Câu hỏi lao động – thuế (BO-18) |
| L4 | Văn bản mới hằng tháng | Theo dõi văn bản mới, tóm tắt thay đổi ảnh hưởng ngành |
| L5 | XML hóa đơn | Kiểm tra hình thức hóa đơn (IDP-01) |

**Đối tượng:** hộ kinh doanh, chủ shop online, kế toán doanh nghiệp nhỏ, sinh viên kế toán (nhánh giáo dục).

**Input → Output**
| Input | Output |
|---|---|
| Câu hỏi tự nhiên; loại hình kinh doanh; doanh thu, số lao động (tùy chọn) | Câu trả lời trích số hiệu/điều/khoản; trạng thái hiệu lực; kết quả tính thuế/BHXH kèm công thức; khuyến nghị hỏi cán bộ thuế khi tình huống phức tạp |

**Hình thái sản phẩm & cách tương tác**
- **Sản phẩm:** chatbot hỏi đáp trên website + máy tính thuế/BHXH dạng biểu mẫu + trang xem văn bản gốc có đánh dấu điều khoản được trích.
- **Hộ kinh doanh / chủ shop:** gõ "bán hàng online doanh thu 600 triệu/năm phải nộp thuế gì?" → bot hỏi lại loại hàng hóa, hình thức kinh doanh → trả lời ngắn gọn bằng ngôn ngữ đời thường + danh sách căn cứ (số hiệu, điều, khoản, **còn hiệu lực / đã bị thay thế**) → bấm căn cứ để mở văn bản gốc tại đúng đoạn → chuyển sang tab "Tính thử", nhập doanh thu và nhận số thuế tạm tính kèm công thức → khi tình huống phức tạp, bot ghi rõ "nên hỏi cán bộ thuế" và tóm tắt câu hỏi để người dùng mang đi hỏi.
- **Kế toán doanh nghiệp nhỏ:** dùng máy tính TNCN/BHXH cho từng nhân viên (BO-12), hỏi tình huống lao động (BO-18).
- **Chuyên gia duyệt (mentor fintech):** xem hàng chờ câu trả lời bị người dùng đánh dấu "nghi sai" và câu hỏi hệ thống từ chối → duyệt, sửa, bổ sung vào golden set.
- **Kịch bản demo 3 phút:** hỏi câu thuế hộ kinh doanh → trả lời có căn cứ → mở văn bản gốc → hỏi về một văn bản cũ → hệ thống báo đã bị thay thế → tính thử thuế.

**Dataset & cách làm:** cào văn bản pháp luật thuế, lao động công khai kèm metadata (ngày ban hành, hiệu lực, văn bản sửa đổi/thay thế) → tách theo điều/khoản → RAG lai (từ khóa + vector) + reranker; bộ truy hồi văn bản luật tiếng Việt trên Hugging Face để đánh giá; cào câu hỏi công khai trên mục hỏi đáp của cơ quan thuế làm bộ test; mentor fintech duyệt golden set 100 câu.

**Triển khai:** T1–4 kho văn bản + metadata · T5–8 MVP hỏi đáp có trích dẫn · T9–12 đồ thị hiệu lực + eval gate · T13–16 máy tính thuế/BHXH (BO-12) · T17–20 lao động (BO-18) · T21–24 theo dõi văn bản mới, hóa đơn XML (IDP-01) nếu kịp.

**Tư duy ngược:** trích nhầm văn bản hết hiệu lực → đồ thị hiệu lực kiểm tra bằng code trước khi trả lời; LLM tự tính thuế sai → mọi phép tính do hàm code; câu hỏi ngoài kho → trả lời "chưa đủ căn cứ"; người dùng coi là tư vấn chính thức → ghi rõ phạm vi tham khảo.

**Chỉ số:** độ đúng trích dẫn (điều/khoản đúng); tỷ lệ trả lời đúng trên golden set; tỷ lệ phát hiện văn bản hết hiệu lực; 100% phép tính đúng trên bộ test.

---

### <a id="d-fin19"></a>7. Chính: `[FIN-19]` Cảnh báo lừa đảo → "Kiểm tra trước khi tin, trước khi chuyển tiền"

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **CHAT-08** Phát hiện tin giả/link độc | Phân tích URL, WHOIS, chuyển hướng | Phần kiểm tra **link** chặt hơn (tên miền giống thật, tuổi tên miền) | Thấp | PhishTank, OpenPhish, URLhaus, Tranco |
| **CHAT-37** Kiểm chứng tin | Tách khẳng định + bằng chứng | Tin mạo danh cơ quan/ngân hàng được đối chiếu với **thông báo chính thức** | Trung bình | Báo chính thống, thông báo cảnh báo công khai |
| **CHAT-26** Kiểm duyệt theo ngữ cảnh (tùy chọn) | Phân tích chuỗi tin nhắn | Phát hiện kịch bản lừa đảo **nhiều bước** (làm quen → nhờ chuyển tiền) | Trung bình | Kịch bản tổng hợp do marketing viết |

**Tầng đào sâu**
| Tầng | Dữ liệu | Năng lực |
|---|---|---|
| L0 | Danh sách URL độc + top domain hợp lệ | Kiểm tra link, giải thích |
| L1 | Tin cảnh báo trên báo chí (cào) | Phân loại kịch bản lừa đảo Việt |
| L2 | Ảnh chụp màn hình | OCR → phân tích |
| L3 | Chuỗi hội thoại tổng hợp | Kịch bản nhiều bước (CHAT-26) |
| L4 | Dữ liệu theo thời gian | Gom cụm chiến dịch mới nổi, cảnh báo cộng đồng |
| L5 | – | API cảnh báo trước chuyển tiền cho ví/sàn TMĐT |

**Dataset & cách làm:** tải feed URL độc + danh sách tên miền phổ biến làm đối chứng; cào tin cảnh báo lừa đảo trên báo điện tử → LLM trích kịch bản, mẫu câu, tên miền → người duyệt xác nhận; marketing viết 100 kịch bản gốc, LLM sinh biến thể (đánh dấu là dữ liệu tổng hợp); golden set 300 mẫu có nhãn.

**Hình thái & tương tác:** website "dán vào để kiểm tra" + bot Zalo/Telegram. Người dùng dán tin/ảnh/link → nhận thẻ kết quả (mức nghi ngờ, 3 lý do, việc nên làm). Người duyệt (team) xem hàng chờ mẫu cộng đồng gửi, xác nhận trước khi đưa vào kho. Demo: dán tin giả ngân hàng có link → mức "cao" + chỉ ra tên miền giả + nút xem bài báo cảnh báo tương tự.

**Triển khai:** T1–4 pipeline cào + golden set · T5–8 MVP link + nội dung · T9–12 OCR ảnh + bot · T13–16 kiểm chứng tin (CHAT-37) · T17–20 kịch bản nhiều bước (CHAT-26) · T21–24 gom cụm chiến dịch, thử cộng đồng.

**Tư duy ngược:** vu oan trang hợp lệ → hiện mức tin cậy và bằng chứng, không khẳng định tuyệt đối; bỏ sót kịch bản mới → kênh cộng đồng gửi mẫu + cập nhật định kỳ; bị lợi dụng để tạo tin lừa đảo "qua mặt" → không công bố chi tiết quy tắc phát hiện.

**Chỉ số:** precision/recall, tỷ lệ báo động giả, thời gian phản hồi.

---

### <a id="d-gsm06"></a>8. Chính: `[GSM-06]` Review du lịch theo khía cạnh

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **CHAT-25** Community Intelligence | Gom cụm chủ đề theo thời gian | Phát hiện vấn đề **mới nổi** (ví dụ: than phiền tăng sau mùa cao điểm) | Trung bình | Chính dữ liệu review |
| **BDSO2O-09** MarketWatch | Thu thập thông tin đối thủ | So sánh khía cạnh với **đối thủ cùng tuyến/khu vực** | Thấp | Review công khai của đối thủ |
| **CHAT-03** Dịch đa ngôn ngữ (tùy chọn) | Dịch có glossary | Gộp review tiếng Anh/Hàn/Trung với tiếng Việt | Thấp | FLORES-200, glossary tự biên soạn |

**Tầng đào sâu:** L0 cảm xúc tổng → L1 khía cạnh (VLSP 2018) → L2 đa ngôn ngữ → L3 xu hướng/vấn đề mới nổi → L4 so sánh đối thủ → L5 nháp trả lời review (người duyệt trước khi đăng).

**Dataset & cách làm:** VLSP 2018 ABSA (hotel, restaurant), TripAdvisor/Booking review datasets trên Kaggle, bộ cảm xúc UIT; cào review công khai (ẩn danh); marketing định nghĩa bộ khía cạnh riêng cho xe du lịch/tour và gán nhãn 500 câu.

**Hình thái & tương tác:** dashboard web cho chủ doanh nghiệp: bảng khía cạnh khen/chê, bấm khía cạnh xem câu gốc, mục "3 việc nên sửa", tab đối thủ; báo cáo tuần qua email. Người gán nhãn sửa nhãn sai trên màn hình riêng.

**Tư duy ngược:** review giả làm lệch kết quả → lọc review bất thường (đăng dồn, nội dung lặp); khía cạnh chung chung không hành động được → bộ khía cạnh do người làm nghề định nghĩa; mỉa mai bị hiểu sai → hiện câu gốc.

**Chỉ số:** F1 theo khía cạnh, độ đúng cảm xúc, đánh giá hữu ích của "việc nên sửa" từ người dùng thử.

---

### <a id="d-edu12"></a>9. Chính: `[EDU-12]` Trợ lý tuyển sinh liên trường có trích dẫn

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **EDU-04** Kho tri thức học thuật | RAG nhiều trợ lý, hybrid search | Truy hồi chính xác trên **hàng trăm đề án PDF** | Trung bình | Đề án tuyển sinh cào |
| **EDU-06** PathPlanner | Lộ trình học theo mục tiêu | Sau khi chọn ngành: **chương trình học** của ngành đó gồm gì | Thấp | Chương trình đào tạo công khai trên website trường |
| **EDU-17** CV & nghề (tùy chọn) | Bản đồ kỹ năng – nghề | Ngành → nghề → kỹ năng thị trường cần | Trung bình | ESCO, O*NET |

**Tầng đào sâu:** L0 hỏi đáp 1 trường → L1 nhiều trường + so sánh ngành → L2 điểm chuẩn nhiều năm, ước tính khả năng đỗ bằng thống kê → L3 chương trình học từng ngành (EDU-06) → L4 ngành → nghề (EDU-17).

**Dataset & cách làm:** cào đề án và thông báo tuyển sinh PDF; điểm chuẩn các năm (báo chí, cổng tuyển sinh); điểm thi THPT trên Kaggle; câu hỏi thường gặp cào từ diễn đàn tuyển sinh công khai → golden set 150 câu; mentor giáo dục duyệt.

**Hình thái & tương tác:** chatbot trên website + trang so sánh ngành. Học sinh nhập điểm dự kiến, tổ hợp, khu vực → nhận danh sách ngành/trường kèm điểm chuẩn các năm → hỏi chi tiết, mỗi câu trả lời có link trang đề án. Phụ huynh dùng cùng giao diện. Người duyệt cập nhật đề án mới mỗi mùa.

**Tư duy ngược:** đề án năm cũ → hiển thị năm của đề án, cảnh báo khi chưa có đề án năm mới; ước tính đỗ bị hiểu là cam kết → ghi rõ "tham khảo, dựa trên điểm chuẩn các năm trước"; mùa vụ → ngoài mùa chuyển sang nội dung chọn ngành và chương trình học.

**Chỉ số:** độ đúng trích dẫn, tỷ lệ trả lời đúng trên golden set, số lượt dùng mùa tuyển sinh.

---

### <a id="d-idp03"></a>10. Chính: `[IDP-03]` Chuẩn hóa bảng giá nhà cung cấp

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **IDP-09** EvidenceView | Khung bằng chứng trên trang gốc | Người dùng **thấy ngay** mỗi số lấy từ ô nào | Thấp | Không cần thêm |
| **BO-04** Procurement Agent | So sánh nhà cung cấp | Từ bảng chuẩn → **so sánh giá, điều kiện giữa NCC** | Thấp | Bảng giá đã chuẩn hóa |
| **IDP-11** CheapPath Router (tùy chọn) | Định tuyến file rẻ/đắt | File có text layer đi parser rẻ, ảnh/scan mới dùng mô hình thị giác | Trung bình | Bộ file hỗn hợp |

**Tầng đào sâu:** L0 Excel → L1 PDF → L2 ảnh/scan → L3 so sánh NCC (BO-04) → L4 theo dõi thay đổi giá giữa các phiên bản bảng giá → L5 định tuyến chi phí (IDP-11).

**Dataset & cách làm:** cào bảng giá công khai (vật liệu xây dựng, linh kiện, văn phòng phẩm, thiết bị); script sinh bảng giá tổng hợp theo đúng các kiểu lỗi marketing gặp khi mua hàng (tiêu đề lệch dòng, ô gộp, đơn vị trong tiêu đề, dòng tổng xen kẽ); PubTabNet/FinTabNet cho nhận diện bảng; golden set 100 file.

**Hình thái & tương tác:** web app: người mua kéo thả nhiều file → xem bảng chuẩn bên trái, file gốc bên phải với ô được tô sáng → sửa ánh xạ cột nếu cần (hệ thống ghi nhớ cho lần sau) → xuất Excel → mở tab so sánh NCC.

**Tư duy ngược:** LLM gõ lại số sai → số luôn được code sao chép từ ô gốc; dòng tổng bị lẫn vào dữ liệu → quy tắc phát hiện dòng tổng + kiểm tra cộng; bố cục mới chưa gặp → đo riêng trên file chưa từng thấy.

**Chỉ số:** độ đúng tìm dòng tiêu đề, ánh xạ cột, giá trị ô; số dòng bị mất/nhân đôi.

---

### <a id="d-edu17"></a>11. Chính: `[EDU-17]` CV & phỏng vấn thử theo JD thật

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **BO-15** JD & khung năng lực | Chuẩn hóa JD thành khung năng lực | So khớp CV với **năng lực chuẩn**, không chỉ từ khóa | Thấp | ESCO, O*NET |
| **EDU-06** PathPlanner | Lộ trình học | Thiếu kỹ năng nào → **học gì, học ở đâu** | Thấp | Khóa học công khai |
| **EDU-12** Tuyển sinh (tùy chọn) | – | Nối ngược về chọn ngành cho học sinh | Trung bình | Như #6 |

**Tầng đào sâu:** L0 so CV với 1 JD → L1 nhiều JD cùng vị trí, thống kê kỹ năng thị trường cần → L2 phỏng vấn thử chấm rubric STAR → L3 lộ trình học (EDU-06) → L4 theo dõi tiến bộ qua nhiều lần.

**Dataset & cách làm:** ESCO, O*NET; cào tin tuyển dụng công khai (giới hạn, tôn trọng điều khoản); resume datasets trên Kaggle/HF; bộ câu hỏi phỏng vấn công khai; mentor giáo dục duyệt rubric.

**Hình thái & tương tác:** web app: sinh viên tải CV + dán JD → bảng khoảng trống kỹ năng có trích câu JD → gợi ý viết lại từng mục (chỉ dựa trên kinh nghiệm có thật) → vào "phòng phỏng vấn" chat hoặc nói → nhận điểm và nhận xét. Cố vấn hướng nghiệp xem báo cáo tiến bộ của nhóm sinh viên.

**Tư duy ngược:** AI thổi phồng kinh nghiệm → chặn mọi gợi ý thêm thông tin không có trong CV; chấm phỏng vấn thiếu công bằng → rubric công khai, đo đồng thuận với người chấm thật.

**Chỉ số:** độ đúng trích kỹ năng, mức đồng thuận chấm điểm với cố vấn, mức hài lòng.

---

### <a id="d-chat37"></a>12. Chính: `[CHAT-37]` Kiểm chứng tin forward

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **CHAT-08** Link độc | Kiểm tra URL | Tin forward kèm link được kiểm tra luôn | Thấp | PhishTank, URLhaus |
| **CHAT-24** Tìm kiếm có trích nguồn | Hybrid search + reranker | Truy hồi bằng chứng chính xác hơn trên kho báo | Trung bình | Kho báo cào |
| **FIN-19** Lừa đảo (tùy chọn) | Kịch bản lừa đảo | Tin forward dạng lừa đảo được chuyển sang luồng cảnh báo | Trung bình | Như #3 |

**Tầng đào sâu:** L0 tách khẳng định → L1 truy hồi bằng chứng từ báo chính thống → L2 ảnh chụp màn hình (OCR) → L3 kiểm tra link → L4 theo dõi tin đồn lan theo thời gian.

**Dataset & cách làm:** FEVER, X-Fact, AVeriTeC để đánh giá phương pháp; tìm bộ fact-check tiếng Việt trên Hugging Face (kiểm tra license); cào báo chính thống làm kho bằng chứng; golden set 200 tin forward thật được biên tập lại (ẩn danh).

**Hình thái & tương tác:** chatbot + bot Zalo: người dùng dán/forward tin → nhận danh sách khẳng định, mỗi khẳng định có nhãn "có bằng chứng ủng hộ / bị bác bỏ / chưa đủ dữ liệu" kèm link bài báo → nút chia sẻ kết quả vào nhóm.

**Tư duy ngược:** kết luận sai về vấn đề nhạy cảm → luôn có lựa chọn "chưa đủ dữ liệu", chỉ dựa trên nguồn chính thống; nguồn bị nghi thiên lệch → hiển thị nhiều nguồn.

**Chỉ số:** độ chính xác nhãn trên golden set, độ đúng trích dẫn, tỷ lệ "chưa đủ dữ liệu" hợp lý.

---

### <a id="d-fin09"></a>13. Chính: `[FIN-09]` Đọc hiểu sao kê: tiền đi đâu

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **FIN-01** Trợ lý tài chính cá nhân | Lập ngân sách | Từ "đã tiêu gì" sang **đặt ngân sách theo danh mục** | Thấp | Kết quả phân loại |
| **FIN-18** Dự báo dòng tiền | Dự báo số dư | Cảnh báo **thiếu hụt cuối tháng** | Trung bình | Chuỗi giao dịch đã phân loại |

**Tầng đào sâu:** L0 phân loại danh mục → L1 nhận diện merchant và khoản định kỳ → L2 ngân sách (FIN-01) → L3 dự báo dòng tiền (FIN-18).

**Dataset & cách làm:** Kaggle bank transaction categorization datasets, Czech Financial (Berka); **sao kê tổng hợp** theo định dạng ngân hàng Việt (mô tả viết tắt, không dấu) do team sinh; danh sách merchant cào công khai; golden set 1.000 dòng giao dịch gán nhãn.

**Hình thái & tương tác:** web app: người dùng tải file sao kê (xử lý trong phiên, không lưu lâu) → dashboard theo danh mục/merchant → sửa nhãn sai (hệ thống học quy tắc cá nhân) → đặt ngân sách → nhận cảnh báo.

**Tư duy ngược:** dữ liệu tài chính nhạy cảm → xử lý cục bộ/xóa sau phiên; thiếu dữ liệu thật tiếng Việt → báo cáo kết quả riêng trên dữ liệu tổng hợp, ghi rõ giới hạn.

**Chỉ số:** độ đúng phân loại, độ đúng nhận diện khoản định kỳ.

---

### <a id="d-vfo2o19"></a>14. Chính: `[VFO2O-19]` Lộ trình đường dài có điểm sạc xe điện

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **VFO2O-11** Trạm sạc & chi phí | Tính chi phí sử dụng | Chi phí sạc từng chặng, so với xe xăng | Thấp | Biểu giá điện/sạc công khai |
| **GSM-19** Lộ trình đa phương thức | Lập lộ trình nhiều điểm | Chuyến du lịch nhiều ngày có điểm tham quan | Trung bình | OSM/OSRM |

**Tầng đào sâu:** L0 lộ trình + tiêu hao theo khoảng cách → L1 theo địa hình (độ cao) → L2 điểm sạc tối ưu → L3 chi phí (VFO2O-11) → L4 lịch trình du lịch nhiều ngày (GSM-19).

**Dataset & cách làm:** OpenChargeMap (trạm sạc công khai), cào danh sách trạm công khai trên website đơn vị vận hành; Geofabrik OSM + OSRM; OpenElevation; thông số xe công khai; mô hình tiêu hao viết bằng code (ghi rõ là ước tính).

**Hình thái & tương tác:** web app bản đồ: nhập điểm đi/đến, chọn mẫu xe, % pin → lộ trình có ghim trạm sạc, biểu đồ % pin theo chặng, cảnh báo đoạn thiếu trạm → kéo thả đổi trạm.

**Tư duy ngược:** ước tính pin lạc quan → luôn để biên an toàn và cảnh báo; dữ liệu trạm thiếu/cũ → hiển thị nguồn và ngày cập nhật, cho người dùng báo trạm sai.

**Chỉ số:** sai số quãng đường/thời gian, tỷ lệ lộ trình khả thi.

---

### <a id="d-bdso2o16"></a>15. Chính: `[BDSO2O-16]` Khoảng giá căn hộ thứ cấp từ tin rao

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **BDSO2O-09** MarketWatch | Thu thập thị trường khu vực | Xu hướng giá khu vực theo thời gian | Thấp | Tin rao cào định kỳ |
| **BDSO2O-05** HomeMatch | Gợi ý căn theo nhu cầu | Từ định giá sang **gợi ý căn phù hợp ngân sách** | Trung bình | Kho tin rao |

**Tầng đào sâu:** L0 căn so sánh → L1 khoảng giá bằng hồi quy có giải thích → L2 xu hướng khu vực (BDSO2O-09) → L3 gợi ý căn (BDSO2O-05).

**Dataset & cách làm:** Kaggle Vietnam housing/real estate datasets; cào tin rao công khai (giới hạn, tôn trọng điều khoản), khử trùng lặp tin đăng lại; Ames Housing làm baseline phương pháp.

**Hình thái & tương tác:** web app: nhập thông tin căn → khoảng giá p25–p75 + 5 căn so sánh + yếu tố tăng/giảm giá + cảnh báo khi dữ liệu mỏng.

**Tư duy ngược:** giá rao ≠ giá chốt → ghi rõ "dựa trên giá rao"; tin rao ảo/trùng → lọc trùng và ngoại lai; bị dùng để ép giá → chỉ hiện khoảng, không hiện một con số.

**Chỉ số:** sai số so với tập kiểm tra, tỷ lệ cảnh báo dữ liệu mỏng.

---

### <a id="d-edu09"></a>16. Chính: `[EDU-09]` Tổng quan tài liệu có trích dẫn kiểm chứng

**Đề tài phụ**
| Phụ | Lấy gì | Làm sâu chỗ nào | Độ khó | Dữ liệu |
|---|---|---|---|---|
| **VIN-10** Cổng thông tin học giả | Đồng bộ, khử trùng lặp tác giả/công trình | Gợi ý **chuyên gia/nhóm nghiên cứu** theo chủ đề | Trung bình | OpenAlex, ORCID, Crossref |
| **EDU-04** Kho tri thức | RAG nhiều tài liệu | Hỏi đáp trên **bộ bài báo đã chọn** | Thấp | PDF bài báo mở |

**Tầng đào sâu:** L0 tìm & sàng lọc bài báo → L1 tóm tắt có DOI → L2 bảng so sánh phương pháp/kết quả → L3 hỏi đáp trên bộ bài báo (EDU-04) → L4 gợi ý chuyên gia (VIN-10).

**Dataset & cách làm:** OpenAlex, Semantic Scholar, arXiv, Crossref (API miễn phí); QASPER, SciFact, LitQA2 để đánh giá.

**Hình thái & tương tác:** web app: nhập câu hỏi nghiên cứu → danh sách bài báo có lý do chọn/loại → bảng tổng hợp → xuất danh mục tài liệu tham khảo. Giảng viên hướng dẫn xem bản nháp của sinh viên.

**Tư duy ngược:** trích dẫn bịa → mọi DOI được kiểm tra tồn tại bằng API trước khi hiển thị; sinh viên dùng để viết hộ → chỉ tổng hợp, không viết thành bài.

**Chỉ số:** 0% DOI không tồn tại, độ đúng tóm tắt, độ phủ bài báo liên quan.

---

## <a id="phan-3"></a>PHẦN 3 – SO SÁNH & KHUYẾN NGHỊ

| Đề tài | Background | Mentor | Dữ liệu | Đo được | Ảnh hưởng thấp | Phụ dễ | **Tổng** |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| BDSO2O-11 Phễu | 5 | 3 | 5 | 5 | 5 | 5 | **28** |
| BO-13 Thuế | 3 | 5 | 5 | 5 | 4 | 4 | **26** |
| FIN-19 Lừa đảo | 4 | 5 | 5 | 4 | 4 | 4 | **26** |
| GSM-15 Mạng xã hội | 5 | 3 | 4 | 4 | 5 | 4 | **25** |
| GSM-06 Review du lịch | 5 | 2 | 5 | 4 | 5 | 3 | **24** |
| EDU-12 Tuyển sinh | 4 | 5 | 4 | 4 | 3 | 3 | **23** |
| VMEC-15 Gói khám | 4 | 2 | 4 | 4 | 4 | 4 | **22** |
| IDP-03 Bảng giá | 5 | 2 | 3 | 5 | 4 | 3 | **22** |
| EDU-17 CV | 3 | 5 | 4 | 3 | 3 | 3 | **21** |
| CHAT-37 Tin giả | 3 | 3 | 4 | 3 | 4 | 4 | **21** |
| FIN-09 Sao kê | 3 | 5 | 3 | 4 | 3 | 2 | **20** |
| GSM-19 Lộ trình | 4 | 2 | 3 | 3 | 4 | 3 | **19** |
| VFO2O-19 Xe điện | 4 | 2 | 3 | 3 | 4 | 3 | **19** |
| BDSO2O-16 Căn hộ | 2 | 3 | 4 | 3 | 3 | 3 | **18** |
| EDU-09 Tài liệu | 2 | 4 | 5 | 4 | 2 | 1 | **18** |
| VMEC-08 Huyết áp | 2 | 2 | 3 | 4 | 2 | 3 | **16** |

**Khuyến nghị**
1. **Chính: BDSO2O-11 Phễu chuyển đổi**, phụ DATA-01 → GSM-15 → GSM-11. Khớp thế mạnh marketing nhất, dữ liệu công khai sẵn, mọi con số kiểm chứng bằng truy vấn, rủi ro người dùng rất thấp.
2. **Dự phòng mentor fintech: BO-13 Thuế** (phụ BO-12 → BO-18) hoặc **FIN-19 Lừa đảo** (phụ CHAT-08 → CHAT-37).
3. **Nếu muốn bám du lịch:** GSM-06 hoặc GSM-15 (hai đề tài dùng chung lõi, có thể đổi qua lại).
4. **Nếu muốn mảng y tế:** VMEC-15 khả thi; VMEC-08 chỉ làm khi có chuyên gia y tế đồng hành.

**Lõi kỹ thuật dùng chung:** BDSO2O-11, GSM-15, GSM-06, VMEC-15 và IDP-03 đều xoay quanh **cào → chuẩn hóa → phân tích (SQL/ABSA) → báo cáo có trích nguồn**. Team dựng lõi này một lần; nếu phải đổi đề tài giữa chừng thì không phải làm lại từ đầu.

**CI/CD chung:** mỗi PR chạy unit test cho các hàm tính bằng code (phải đúng 100%) + đánh giá trên golden set; điểm giảm thì chặn merge; merge vào `main` tự deploy staging; thứ Sáu gắn tag phiên bản, deploy demo và cập nhật bảng chỉ số tuần cho mentor.

## Lưu ý dữ liệu & pháp lý
- Chỉ cào **nội dung công khai**, tôn trọng `robots.txt` và điều khoản sử dụng, giới hạn tốc độ, ghi nguồn từng bản ghi.
- **Không thu hoặc ẩn danh ngay** dữ liệu cá nhân (tên, số điện thoại, tài khoản); tuân thủ quy định bảo vệ dữ liệu cá nhân của Việt Nam (Nghị định 13/2023 và Luật Bảo vệ dữ liệu cá nhân hiệu lực từ 2026 – nên đọc bản chính thức).
- Kiểm tra **license** từng dataset, ghi vào `DATA_SOURCES.md`.
- Dữ liệu tổng hợp phải **đánh dấu là tổng hợp**; báo cáo kết quả riêng giữa dữ liệu thật và tổng hợp.
- Tên, quy mô, tình trạng và license các nguồn nêu trong file này cần được xác minh trực tiếp trên trang nguồn; phần so sánh với hệ thống trên thế giới viết theo hiểu biết sẵn có, chưa tra cứu web.
