# Lĩnh vực: RAV - Robot & Xe tự hành

> Tổng số đề tài: **26 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `RAV-01` | [Real2Sim Studio - Công cụ dựng lại cảnh đường/kho từ video & LiDAR thành scene mô phỏng chỉnh sửa được](#rav-01) |
| `RAV-02` | [Sim2Real Gap Analyzer - Công cụ domain randomization & đo khoảng cách sim-to-real cho policy robot/AV](#rav-02) |
| `RAV-03` | [Scenario Forge - Agent sinh & quản lý kịch bản corner-case bằng LLM cho CARLA/Isaac](#rav-03) |
| `RAV-04` | [AutoLabel 3D - Công cụ tự động gán nhãn ảnh & LiDAR (2D/3D box, segmentation) với human-in-the-loop](#rav-04) |
| `RAV-05` | [Fleet Miner - Active learning & khai thác corner-case từ dữ liệu fleet để chọn dữ liệu gán nhãn](#rav-05) |
| `RAV-06` | [Closed-Loop Bench - Nền tảng đánh giá closed-loop & scenario replay cho mô hình lái (regression testing)](#rav-06) |
| `RAV-07` | [Label Guardian - Trợ lý agent kiểm định chất lượng nhãn (Label QA) cho dữ liệu perception](#rav-07) |
| `RAV-08` | [CalibCheck - Công cụ hiệu chỉnh & đồng bộ cảm biến camera-LiDAR-radar có kiểm tra tự động](#rav-08) |
| `RAV-09` | [BEV Vision - Công cụ sensor fusion & perception BEV/occupancy kèm trực quan hóa](#rav-09) |
| `RAV-10` | [Synthetic Trajectory Engine - Data engine sinh dữ liệu tổng hợp cho robot thao tác qua Isaac Sim (VLA)](#rav-10) |
| `RAV-11` | [Factory Twin - Digital twin nhà máy/robot để mô phỏng & giám sát vận hành](#rav-11) |
| `RAV-12` | [TeleCollect - Nền tảng teleoperation & thu thập demonstration cho imitation learning](#rav-12) |
| `RAV-13` | [ROS2 Doctor - Trợ lý agent gỡ lỗi & chẩn đoán hệ thống ROS2 từ rosbag](#rav-13) |
| `RAV-14` | [SceneSearch - Công cụ tìm kiếm ngữ nghĩa trong dữ liệu lái ("tìm cảnh mưa có người băng qua")](#rav-14) |
| `RAV-15` | [Safety Sentinel - Nền tảng đánh giá an toàn & phát hiện hồi quy từ phân tích disengagement](#rav-15) |
| `RAV-16` | [AdverTest - Công cụ sinh & kiểm thử adversarial cho perception (robustness testing)](#rav-16) |
| `RAV-17` | [MapWatch - Công cụ tự động phát hiện thay đổi & cập nhật HD map từ dữ liệu fleet](#rav-17) |
| `RAV-18` | [IncidentLens - Trợ lý VLM phân tích & tóm tắt sự cố lái/disengagement từ log + video](#rav-18) |
| `RAV-19` | [PlanBench - Simulator & benchmark path/motion planning cho robot di động (AMR/AGV)](#rav-19) |
| `RAV-20` | [GraspTransfer - Sim-to-real cho robot grasping/manipulation với VLA & đánh giá thành công](#rav-20) |
| `RAV-21` | [doanh nghiệp sản xuất ô tô 3D Data Hub - Nền tảng quản trị dữ liệu 3D đa cảm biến cho ADAS](#rav-21) |
| `RAV-22` | [Vietnam Synthetic Street - Engine sinh dữ liệu tổng hợp giao thông Việt Nam cho perception ADAS](#rav-22) |
| `RAV-23` | [doanh nghiệp sản xuất ô tô Real2Sim ODD Builder - Chuyển log fleet thành scene mô phỏng chỉnh sửa được](#rav-23) |
| `RAV-24` | [Sim2Real Perception Gap - Công cụ đo và giảm khoảng cách synthetic-to-real cho ADAS](#rav-24) |
| `RAV-25` | [4D Occupancy Lab - Perception BEV/occupancy từ camera-LiDAR-radar cho ADAS đô thị](#rav-25) |
| `RAV-26` | [Data Curation Copilot - Agent chọn dữ liệu giá trị cao cho huấn luyện ADAS/Robotics](#rav-26) |

---

## [RAV-01] Real2Sim Studio - Công cụ dựng lại cảnh đường/kho từ video & LiDAR thành scene mô phỏng chỉnh sửa được

### 📝 Mô tả đề tài
📍 Thực trạng: Kỹ sư AV/robotics cần rất nhiều cảnh mô phỏng đa dạng để huấn luyện và kiểm thử policy, nhưng dựng scene 3D thủ công trong CARLA/Isaac rất tốn công, còn dữ liệu thật quay được lại không chỉnh sửa được (không thêm được người đi bộ, xe cắt ngang, đổi thời tiết).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ real2sim tái tạo lại một đoạn đường hoặc góc kho từ video RGB và/hoặc point cloud LiDAR thành một scene mô phỏng bằng 3D Gaussian Splatting/NeRF, cho phép kỹ sư chèn/xóa/di chuyển vật thể (agent, chướng ngại), đổi ánh sáng - thời tiết, rồi export sang định dạng dùng lại được để mô phỏng; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư phải review và duyệt scene tái tạo (human-in-the-loop) trước khi đưa vào tập huấn luyện; mọi thử nghiệm policy chỉ chạy trên mô phỏng, không điều khiển xe/robot thật; chất lượng tái tạo phải đo được bằng PSNR/SSIM/LPIPS và độ khớp hình học (Chamfer distance) so với ground truth; tối ưu thời gian huấn luyện GS và độ trễ render (mục tiêu render tương tác được trên 1 GPU); dữ liệu thu thập phải ẩn danh biển số và khuôn mặt trước khi xử lý.

### 🛠️ Tech Stack
• Python, PyTorch
• 3D Gaussian Splatting (nerfstudio/gsplat), NeRF
• Open3D, PCL để xử lý point cloud
• nuScenes/KITTI/Waymo Open làm dữ liệu đầu vào
• CARLA/Isaac Sim để export & mô phỏng
• SAM2 để tách vật thể
• FastAPI backend
• React/Next.js + three.js/WebGL để trực quan và chỉnh sửa scene 3D
• DVC + MLflow quản lý phiên bản scene
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app dựng lại 1 scene mẫu từ dữ liệu công khai, trình xem 3D trên trình duyệt, cho phép xoay/zoom và bật/tắt vật thể, có ≥2 vai trò (người dựng scene và kỹ sư duyệt), báo cáo metric PSNR/SSIM/Chamfer, HITL duyệt scene trước khi lưu.

Nâng cao:
• pipeline khép kín từ video/LiDAR ra scene chỉnh sửa được, chèn agent động và đổi thời tiết, export tự động sang CARLA/Isaac để chạy closed-loop, benchmark chất lượng tái tạo trên nhiều scene và tối ưu tốc độ render/thời gian train
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-02] Sim2Real Gap Analyzer - Công cụ domain randomization & đo khoảng cách sim-to-real cho policy robot/AV

### 📝 Mô tả đề tài
📍 Thực trạng: Policy huấn luyện trong mô phỏng thường hoạt động kém khi transfer sang môi trường thật vì sim-to-real gap (khác biệt texture, ánh sáng, động lực học, nhiễu cảm biến), nhưng đội kỹ sư thường không có công cụ định lượng gap này hay tự động hóa domain randomization.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ cấu hình và chạy domain randomization (ngẫu nhiên hóa texture, ánh sáng, ma sát, nhiễu cảm biến) khi huấn luyện policy trong mô phỏng, đồng thời đánh giá và trực quan hóa sim-to-real gap bằng cách so sánh phân bố quan sát/hành vi giữa sim và tập dữ liệu thật; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt cấu hình randomization và kết quả đánh giá trước khi dùng để chốt policy (human-in-the-loop); mọi đánh giá transfer chỉ thực hiện trên mô phỏng hoặc dữ liệu thật đã ghi sẵn, không vận hành robot/xe thật khi chưa validate; gap phải đo được (success rate sim vs real-log, khoảng cách phân bố đặc trưng, ADE/FDE hoặc IoU tùy bài); tối ưu chi phí GPU và thời gian mỗi vòng randomization; dữ liệu thật dùng để so sánh phải ẩn danh khuôn mặt/biển số.

### 🛠️ Tech Stack
• Python, PyTorch
• NVIDIA Isaac Sim/Isaac Lab, MuJoCo hoặc CARLA
• ROS2 để đọc log thật
• domain randomization API của simulator
• scikit-learn/PyTorch cho đo khoảng cách phân bố (MMD, FID đặc trưng)
• Weights & Biases để theo dõi thí nghiệm
• FastAPI + React/Next.js dashboard trực quan gap
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• tool cấu hình randomization qua UI, chạy huấn luyện 1 policy đơn giản trong sim, dashboard so sánh phân bố sim vs dữ liệu thật mẫu và báo cáo chỉ số gap, ≥2 vai trò, HITL duyệt cấu hình.

Nâng cao:
• agent tự động quét dải tham số randomization để tối thiểu hóa gap, benchmark nhiều policy, đánh giá transfer định lượng trên tập real-log và tối ưu số vòng/chi phí GPU
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-03] Scenario Forge - Agent sinh & quản lý kịch bản corner-case bằng LLM cho CARLA/Isaac

### 📝 Mô tả đề tài
📍 Thực trạng: Việc kiểm thử xe tự lái/robot đòi hỏi rất nhiều tình huống hiếm và nguy hiểm (người băng qua bất ngờ, xe ngược chiều, vật rơi), nhưng viết kịch bản mô phỏng thủ công cho từng corner-case vừa chậm vừa dễ bỏ sót. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng AI agent nhận mô tả ngôn ngữ tự nhiên ("xe máy tạt đầu khi trời mưa ở ngã tư") và sinh ra kịch bản mô phỏng chạy được trong CARLA/Isaac (vị trí, quỹ đạo, thời tiết, tác nhân), kèm hệ quản lý thư viện kịch bản để tái sử dụng, phân loại và tổ chức bộ test; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư phải review và phê duyệt kịch bản sinh ra (human-in-the-loop) trước khi đưa vào bộ kiểm thử chính thức; kịch bản chỉ chạy trên mô phỏng, tuyệt đối không thử nghiệm trên xe/robot thật; chất lượng đo được (tỷ lệ kịch bản chạy hợp lệ, độ đa dạng/coverage tình huống, tỷ lệ kích hoạt được hành vi nguy hiểm mong muốn); kiểm soát chi phí gọi LLM và thời gian sinh; không có dữ liệu cá nhân thật nên đảm bảo an toàn nội dung sinh.

### 🛠️ Tech Stack
• Python
• LLM + LangGraph để dựng agent
• CARLA/Isaac Sim (ScenarioRunner/OpenSCENARIO)
• PyTorch nếu cần đánh giá
• vector DB (Qdrant) để lưu và tìm kiếm thư viện kịch bản
• DeepEval để đánh giá đầu ra agent
• FastAPI + React/Next.js quản lý và preview kịch bản
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web tool nhập mô tả tự nhiên và sinh ra file kịch bản CARLA chạy được, preview kịch bản, thư viện lưu trữ có tag, ≥2 vai trò (người tạo và người duyệt), HITL phê duyệt, báo cáo tỷ lệ kịch bản hợp lệ.

Nâng cao:
• agent tự động sinh bộ kịch bản đa dạng phủ ODD, tự chạy trong sim và thu chỉ số coverage/nguy hiểm, tích hợp closed-loop với mô hình lái để lọc kịch bản làm mô hình thất bại, tối ưu chi phí sinh
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-04] AutoLabel 3D - Công cụ tự động gán nhãn ảnh & LiDAR (2D/3D box, segmentation) với human-in-the-loop

### 📝 Mô tả đề tài
📍 Thực trạng: Gán nhãn dữ liệu perception cho AV (2D box, 3D box, segmentation trên ảnh và point cloud) là công đoạn tốn kém nhất, làm thủ công vừa chậm vừa không đồng nhất giữa các annotator. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ tự động sinh nhãn sơ bộ bằng mô hình pretrained (2D/3D detection, segmentation) rồi đưa vào giao diện để kỹ sư/annotator chỉnh sửa, xác nhận; hỗ trợ đồng bộ nhãn giữa ảnh và LiDAR (chiếu 2D-3D); đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: mọi nhãn tự động phải qua kỹ sư/annotator duyệt trước khi đưa vào tập train (human-in-the-loop bắt buộc); công cụ chỉ xử lý dữ liệu đã ghi, không điều khiển phương tiện; chất lượng đo được (mAP/IoU của nhãn tự động so với ground truth, thời gian gán nhãn tiết kiệm được, tỷ lệ nhãn phải sửa); tối ưu độ trễ inference và chi phí GPU khi chạy batch lớn; ẩn danh khuôn mặt và biển số trong ảnh trước khi hiển thị.

### 🛠️ Tech Stack
• Python, PyTorch
• YOLO, SAM/SAM2 cho 2D
• MMDetection3D/BEVFusion cho 3D box trên point cloud
• Open3D, PCL
• định dạng nuScenes/KITTI
• CVAT hoặc Label Studio để tích hợp giao diện gán nhãn
• FastAPI backend
• React/Next.js + three.js xem point cloud
• DVC quản lý phiên bản nhãn
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web tool nạp 1 frame ảnh + LiDAR, tự sinh box/segmentation sơ bộ, giao diện sửa nhãn 2D và 3D, xuất nhãn theo chuẩn nuScenes/KITTI, ≥2 vai trò (annotator và reviewer), báo cáo IoU/mAP so ground truth.

Nâng cao:
• pipeline auto-label chạy batch cả sequence với đồng bộ 2D-3D và tracking qua frame, thống kê năng suất và độ chính xác, tích hợp active learning ưu tiên frame khó, tối ưu throughput inference
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-05] Fleet Miner - Active learning & khai thác corner-case từ dữ liệu fleet để chọn dữ liệu gán nhãn

### 📝 Mô tả đề tài
📍 Thực trạng: Fleet xe/robot sinh ra khối lượng dữ liệu khổng lồ, nhưng gán nhãn tất cả là bất khả thi và lãng phí, còn phần lớn dữ liệu lại giống nhau (đường thẳng, trời quang). Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ active learning tự động chấm điểm và chọn ra những frame/đoạn dữ liệu giá trị nhất để gán nhãn (mẫu mà mô hình không chắc chắn, mẫu hiếm/corner-case, mẫu khác biệt so với tập đã có), giúp giảm chi phí gán nhãn mà vẫn tăng chất lượng mô hình; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt danh sách mẫu được đề xuất trước khi gửi đi gán nhãn (human-in-the-loop); chỉ xử lý dữ liệu đã ghi, không điều khiển phương tiện thật; hiệu quả đo được (đường cong mô hình cải thiện theo số mẫu gán nhãn - so với chọn ngẫu nhiên, độ đa dạng tập chọn, tỷ lệ corner-case thu được); tối ưu chi phí tính embedding/uncertainty trên dữ liệu lớn; ẩn danh khuôn mặt/biển số.

### 🛠️ Tech Stack
• Python, PyTorch
• mô hình perception pretrained để lấy uncertainty
• embedding ảnh (CLIP) cho đo đa dạng
• nuScenes/Waymo Open làm proxy cho fleet
• vector DB (Qdrant) để clustering và tìm mẫu hiếm
• scikit-learn
• FastAPI + React/Next.js dashboard chọn mẫu
• Weights & Biases
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• tool tính uncertainty/độ hiếm trên tập dữ liệu mẫu, dashboard xếp hạng và cho kỹ sư duyệt danh sách mẫu để gán nhãn, ≥2 vai trò, báo cáo so sánh với chọn ngẫu nhiên.

Nâng cao:
• vòng active learning khép kín (chọn - gán nhãn mô phỏng - huấn luyện lại - đo cải thiện), nhiều chiến lược lựa chọn kết hợp, benchmark đường cong hiệu quả gán nhãn và tối ưu chi phí tính toán trên dữ liệu lớn
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-06] Closed-Loop Bench - Nền tảng đánh giá closed-loop & scenario replay cho mô hình lái (regression testing)

### 📝 Mô tả đề tài
📍 Thực trạng: Khi cập nhật mô hình lái, đội kỹ sư cần biết phiên bản mới có tốt hơn hay gây hồi quy (regression) ở tình huống nào, nhưng đánh giá open-loop trên tập tĩnh không phản ánh được hành vi thực khi mô hình điều khiển vòng kín. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng chạy đánh giá closed-loop cho mô hình lái trong mô phỏng trên một bộ kịch bản chuẩn, tự động replay và so sánh nhiều phiên bản mô hình, phát hiện kịch bản bị hồi quy và báo cáo trực quan; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư review kết quả và phê duyệt phiên bản trước khi coi là đạt (human-in-the-loop); toàn bộ đánh giá chạy trên mô phỏng, không triển khai thật khi chưa validate; chỉ số rõ ràng (tỷ lệ hoàn thành route, số va chạm/vi phạm luật, driving score, ADE/FDE, so sánh delta giữa các phiên bản); tối ưu thời gian chạy bộ test và chi phí GPU (song song hóa); dữ liệu là mô phỏng nên không có PII nhưng vẫn bảo mật cấu hình kịch bản.

### 🛠️ Tech Stack
• Python
• CARLA (Leaderboard/ScenarioRunner) hoặc Isaac Sim
• ROS2 tùy chọn
• PyTorch cho mô hình lái
• cơ chế replay xác định (deterministic)
• MLflow để lưu kết quả các lần chạy
• FastAPI + React/Next.js dashboard so sánh phiên bản
• Docker + GPU, hỗ trợ chạy song song.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• nền tảng chạy 1 mô hình lái qua bộ kịch bản mẫu trong sim, thu chỉ số và hiển thị dashboard, replay lại một lần chạy để xem lỗi, ≥2 vai trò, HITL duyệt kết quả.

Nâng cao:
• so sánh tự động nhiều phiên bản với phát hiện regression theo từng kịch bản, chạy song song bộ test lớn, tích hợp thư viện scenario và báo cáo driving score định lượng, tối ưu thời gian/chi phí GPU
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-07] Label Guardian - Trợ lý agent kiểm định chất lượng nhãn (Label QA) cho dữ liệu perception

### 📝 Mô tả đề tài
📍 Thực trạng: Nhãn do nhiều annotator tạo ra thường có lỗi (box lệch, thiếu vật thể, sai class, id tracking nhảy) mà rà soát thủ công toàn bộ là không khả thi, nhưng nhãn lỗi làm hỏng mô hình. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent QA nhãn tự động phát hiện các nhãn nghi ngờ sai (dựa vào bất nhất hình học, so với dự đoán mô hình, bất nhất theo thời gian, luật miền) và đề xuất sửa, xếp ưu tiên để kỹ sư review nhanh những chỗ có khả năng lỗi cao nhất; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: agent chỉ đề xuất, mọi thay đổi nhãn phải được kỹ sư duyệt (human-in-the-loop); công cụ làm việc trên dữ liệu đã ghi, không điều khiển phương tiện; hiệu quả đo được (precision/recall của việc phát hiện nhãn lỗi so với tập lỗi đã biết, tỷ lệ lỗi giảm sau QA, thời gian review tiết kiệm); tối ưu chi phí chạy kiểm tra trên dataset lớn; ẩn danh khuôn mặt/biển số khi hiển thị.

### 🛠️ Tech Stack
• Python, PyTorch
• mô hình perception làm reference (YOLO, MMDetection3D)
• luật hình học/thời gian
• định dạng nuScenes/KITTI
• CVAT/Label Studio để hiển thị và sửa
• LLM + LangGraph cho phần lý giải/đề xuất
• FastAPI + React/Next.js dashboard QA
• DVC
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• tool quét một tập nhãn mẫu, gắn cờ và xếp hạng nhãn nghi ngờ sai, giao diện cho kỹ sư xác nhận/sửa, ≥2 vai trò, báo cáo precision/recall phát hiện lỗi.

Nâng cao:
• agent QA đa quy tắc chạy trên cả sequence với kiểm tra nhất quán theo thời gian, tự sinh báo cáo chất lượng dataset, tích hợp vòng phản hồi cho annotator và tối ưu thông lượng kiểm tra
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-08] CalibCheck - Công cụ hiệu chỉnh & đồng bộ cảm biến camera-LiDAR-radar có kiểm tra tự động

### 📝 Mô tả đề tài
📍 Thực trạng: Xe/robot đa cảm biến cần hiệu chỉnh ngoại/nội (extrinsic/intrinsic) và đồng bộ thời gian chính xác giữa camera, LiDAR, radar; sai lệch nhỏ làm hỏng sensor fusion, nhưng kiểm tra calibration hiện thường thủ công và khó phát hiện trôi.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ hỗ trợ hiệu chỉnh và kiểm tra chất lượng calibration: chiếu point cloud LiDAR lên ảnh để đánh giá độ khớp, đo lệch thời gian, tự động cảnh báo khi calibration sai lệch vượt ngưỡng, hỗ trợ kỹ sư tinh chỉnh tham số; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt và xác nhận tham số calibration trước khi đưa vào pipeline (human-in-the-loop); công cụ chạy trên dữ liệu ghi sẵn, không vận hành phương tiện thật khi chưa validate; chất lượng đo được (reprojection error, độ lệch thời gian ms, IoU chiếu 2D-3D, tỷ lệ phát hiện miscalibration); tối ưu tốc độ xử lý để dùng được gần realtime khi cần; ẩn danh khuôn mặt/biển số trong ảnh.

### 🛠️ Tech Stack
• Python
• Open3D, PCL, OpenCV
• định dạng nuScenes/KITTI (có sẵn calibration ground truth)
• ROS2 (rosbag) cho dữ liệu đa cảm biến
• NumPy/SciPy tối ưu tham số
• FastAPI + React/Next.js + three.js trực quan chiếu LiDAR-ảnh
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• tool nạp dữ liệu đa cảm biến mẫu, chiếu LiDAR lên ảnh, hiển thị reprojection error, cho kỹ sư chỉnh tham số extrinsic và xem lại, ≥2 vai trò, báo cáo metric.

Nâng cao:
• tự động ước lượng/tinh chỉnh extrinsic, phát hiện miscalibration và trôi calibration theo thời gian trên cả sequence, kiểm tra đồng bộ thời gian, benchmark trên nhiều bộ dữ liệu và tối ưu tốc độ
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-09] BEV Vision - Công cụ sensor fusion & perception BEV/occupancy kèm trực quan hóa

### 📝 Mô tả đề tài
📍 Thực trạng: Perception hiện đại của AV chuyển sang biểu diễn Bird's-Eye-View và occupancy network từ hợp nhất camera-LiDAR, nhưng kỹ sư thiếu công cụ trực quan để hiểu, gỡ lỗi và so sánh đầu ra fusion giữa các cấu hình. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ chạy một mô hình sensor fusion BEV/occupancy trên dữ liệu đa cảm biến và trực quan hóa kết quả (bản đồ BEV, ô occupancy, vật thể phát hiện) chồng lên ảnh và point cloud, cho phép kỹ sư so sánh cấu hình fusion và soi các trường hợp lỗi; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư review đầu ra perception trước khi kết luận/dùng cho hạ nguồn (human-in-the-loop); công cụ chạy trên dữ liệu ghi/mô phỏng, không điều khiển phương tiện; chỉ số rõ ràng (mAP phát hiện, IoU occupancy/BEV segmentation, độ trễ inference); tối ưu chi phí GPU và độ trễ để dùng được gần realtime; ẩn danh khuôn mặt/biển số trong ảnh hiển thị.

### 🛠️ Tech Stack
• Python, PyTorch
• BEVFusion, MMDetection3D
• nuScenes/Waymo Open
• Open3D, PCL
• FastAPI backend
• React/Next.js + three.js/WebGL để render BEV và occupancy 3D
• Weights & Biases
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web tool chạy mô hình fusion pretrained trên frame mẫu, hiển thị BEV/occupancy và vật thể chồng lên ảnh + point cloud, ≥2 vai trò, báo cáo mAP/IoU và độ trễ.

Nâng cao:
• chạy cả sequence với so sánh nhiều cấu hình fusion, phân tích trường hợp lỗi (false positive/negative), benchmark định lượng trên nhiều điều kiện và tối ưu độ trễ/chi phí GPU
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-10] Synthetic Trajectory Engine - Data engine sinh dữ liệu tổng hợp cho robot thao tác qua Isaac Sim (VLA)

### 📝 Mô tả đề tài
📍 Thực trạng: Huấn luyện robot thao tác (gắp, đặt, thao tác vật) cần hàng chục nghìn quỹ đạo demonstration, nhưng thu thập bằng robot thật rất chậm và đắt; các data engine hiện đại sinh quỹ đạo tổng hợp trong mô phỏng để giải bài toán này. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng data engine chạy trong Isaac Sim/Isaac Lab tự động sinh hàng loạt quỹ đạo thao tác đa dạng (ngẫu nhiên hóa vật thể, vị trí, tư thế) kèm nhãn (ảnh, độ sâu, hành động, thành công/thất bại), đóng gói thành dataset chuẩn để huấn luyện chính sách/VLA; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt chất lượng dữ liệu sinh (mẫu quỹ đạo, tỷ lệ thành công) trước khi dùng để train (human-in-the-loop); tất cả sinh trên mô phỏng, không chạy robot thật khi chưa validate; chất lượng đo được (tỷ lệ quỹ đạo thành công, độ đa dạng, và success rate của policy huấn luyện từ dữ liệu sinh); tối ưu thông lượng sinh (số quỹ đạo/giờ trên GPU) và chi phí; dữ liệu tổng hợp không chứa PII.

### 🛠️ Tech Stack
• Python
• NVIDIA Isaac Sim/Isaac Lab, MuJoCo (đối chứng)
• ROS2 tùy chọn
• PyTorch
• VLA/VLM (OpenVLA) để huấn luyện thử policy
• định dạng dataset kiểu RLDS/LeRobot
• FastAPI + React/Next.js dashboard giám sát sinh dữ liệu
• DVC + Weights & Biases
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• tool cấu hình một task thao tác trong Isaac Sim, sinh tự động một tập quỹ đạo có nhãn, dashboard xem mẫu và thống kê tỷ lệ thành công, ≥2 vai trò, HITL duyệt dữ liệu.

Nâng cao:
• engine sinh quy mô lớn với domain randomization, tự lọc quỹ đạo lỗi, huấn luyện một policy/VLA từ dữ liệu sinh và báo cáo success rate, benchmark thông lượng sinh và tối ưu chi phí GPU
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-11] Factory Twin - Digital twin nhà máy/robot để mô phỏng & giám sát vận hành

### 📝 Mô tả đề tài
📍 Thực trạng: Vận hành đội robot trong nhà máy cần thử nghiệm bố trí, luồng di chuyển và kịch bản trước khi triển khai thật, đồng thời giám sát trạng thái theo thời gian thực, nhưng thiếu một bản sao số thống nhất để làm cả hai. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng digital twin của một khu vực nhà máy/kho với robot di động, cho phép mô phỏng bố trí và luồng công việc, đồng thời phản chiếu trạng thái robot (vị trí, trạng thái, cảnh báo) từ dữ liệu/telemetry mô phỏng lên giao diện giám sát 3D; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt các thay đổi bố trí/kịch bản trước khi áp dụng (human-in-the-loop); mọi thử nghiệm điều khiển chỉ trên digital twin/mô phỏng, không tác động robot thật khi chưa validate; chỉ số đo được (throughput luồng công việc, thời gian chu trình, tỷ lệ tắc nghẽn/va chạm mô phỏng, độ trễ cập nhật trạng thái); tối ưu hiệu năng render và tần suất cập nhật realtime; bảo mật dữ liệu telemetry và cấu hình nhà máy.

### 🛠️ Tech Stack
• Python
• Gazebo hoặc Isaac Sim
• ROS2 cho telemetry và điều phối robot
• FastAPI backend + WebSocket
• React/Next.js + three.js/WebGL cho giám sát 3D
• time-series DB (hoặc lưu log) cho telemetry
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• digital twin một khu vực với vài robot mô phỏng, giao diện 3D hiển thị vị trí/trạng thái realtime, cho phép đổi bố trí và chạy lại, ≥2 vai trò (người thiết kế và người giám sát), báo cáo throughput/thời gian chu trình.

Nâng cao:
• đồng bộ hai chiều với mô phỏng ROS2 nhiều robot, phát cảnh báo khi bất thường, chạy so sánh các phương án bố trí và tối ưu luồng, benchmark hiệu năng và độ trễ cập nhật
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-12] TeleCollect - Nền tảng teleoperation & thu thập demonstration cho imitation learning

### 📝 Mô tả đề tài
📍 Thực trạng: Imitation learning cho robot cần dữ liệu demonstration do người điều khiển tạo ra, nhưng thiếu công cụ teleoperation tiện dụng để thu, ghi lại đồng bộ (quan sát + hành động) và quản lý các bản ghi chất lượng cao. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng cho phép người điều khiển teleoperate một robot mô phỏng qua giao diện (bàn phím/gamepad/chuột), ghi lại đồng bộ luồng quan sát và hành động thành dataset demonstration, kèm công cụ xem lại, cắt và gắn nhãn thành công/thất bại cho từng bản ghi; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư review và duyệt các demonstration trước khi đưa vào tập huấn luyện (human-in-the-loop); teleoperation chỉ trên robot mô phỏng, không điều khiển robot thật khi chưa validate; chất lượng đo được (số demo hợp lệ, tỷ lệ thành công, và success rate của policy imitation huấn luyện từ dữ liệu thu); tối ưu độ trễ điều khiển realtime và chi phí lưu trữ; nếu có hình ảnh người thì ẩn danh khuôn mặt.

### 🛠️ Tech Stack
• Python
• MuJoCo hoặc Isaac Sim/Gazebo
• ROS2 để truyền lệnh/quan sát
• PyTorch cho huấn luyện imitation (behavior cloning)
• định dạng LeRobot/RLDS
• FastAPI + WebSocket
• React/Next.js giao diện teleop và xem lại
• DVC
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• nền tảng teleop một robot mô phỏng qua trình duyệt, ghi lại đồng bộ observation-action, xem lại và gắn nhãn bản ghi, ≥2 vai trò, HITL duyệt demo.

Nâng cao:
• thu dataset nhiều task, huấn luyện policy behavior cloning từ dữ liệu thu và đánh giá success rate trong sim, tối ưu độ trễ teleop và pipeline xử lý dữ liệu
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-13] ROS2 Doctor - Trợ lý agent gỡ lỗi & chẩn đoán hệ thống ROS2 từ rosbag

### 📝 Mô tả đề tài
📍 Thực trạng: Kỹ sư robotics tốn nhiều thời gian đọc rosbag để tìm nguyên nhân lỗi (topic chết, tần số tụt, timestamp lệch, TF gãy, node crash), công việc lặp đi lặp lại và đòi hỏi kinh nghiệm. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent phân tích file rosbag, tự động phát hiện bất thường (topic mất, drop rate cao, lệch thời gian, cây TF không nhất quán), giải thích khả năng nguyên nhân bằng ngôn ngữ tự nhiên và đề xuất hướng khắc phục, kèm trực quan timeline các topic; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: agent chỉ chẩn đoán và gợi ý, kỹ sư quyết định và duyệt hành động khắc phục (human-in-the-loop); phân tích trên log ghi sẵn, không tự động can thiệp hệ thống robot đang chạy; hiệu quả đo được (độ chính xác phát hiện lỗi so với tập lỗi đã gán, thời gian chẩn đoán tiết kiệm); tối ưu chi phí gọi LLM và thời gian phân tích bag lớn; bảo mật nội dung log (loại bỏ dữ liệu nhạy cảm nếu có).

### 🛠️ Tech Stack
• Python
• ROS2 + rosbag2 API
• pandas để phân tích chuỗi thời gian
• LLM + LangGraph cho agent chẩn đoán
• DeepEval để đánh giá chất lượng chẩn đoán
• FastAPI + React/Next.js dashboard timeline và báo cáo
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• tool nạp một rosbag mẫu, hiển thị danh sách topic/tần số/timeline, tự phát hiện vài loại bất thường cơ bản và báo cáo, ≥2 vai trò, HITL duyệt kết luận.

Nâng cao:
• agent chẩn đoán đa lỗi có lý giải nguyên nhân và đề xuất khắc phục, kiểm tra TF và đồng bộ thời gian, benchmark độ chính xác phát hiện trên bộ bag có lỗi đã biết và tối ưu thời gian/chi phí phân tích
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-14] SceneSearch - Công cụ tìm kiếm ngữ nghĩa trong dữ liệu lái ("tìm cảnh mưa có người băng qua")

### 📝 Mô tả đề tài
📍 Thực trạng: Kho dữ liệu lái khổng lồ nhưng kỹ sư khó tìm nhanh những cảnh cụ thể (ví dụ "trời mưa, có người đi bộ băng qua trước xe") để phân tích, gán nhãn hay xây bộ test; duyệt tay hàng nghìn giờ video là bất khả thi. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ tìm kiếm ngữ nghĩa cho phép kỹ sư nhập truy vấn bằng ngôn ngữ tự nhiên và trả về các frame/đoạn khớp, dựa trên embedding hình ảnh-văn bản và metadata (thời tiết, vật thể, hành vi), kèm giao diện xem và lọc kết quả; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư review và xác nhận kết quả tìm kiếm trước khi dùng để lập bộ dữ liệu/test (human-in-the-loop); công cụ chạy trên dữ liệu đã ghi, không điều khiển phương tiện; chất lượng đo được (precision@k, recall trên truy vấn có ground truth, thời gian truy vấn); tối ưu chi phí tạo và lưu embedding, độ trễ truy vấn trên tập lớn; ẩn danh khuôn mặt/biển số trong ảnh hiển thị.

### 🛠️ Tech Stack
• Python, PyTorch
• CLIP/BLIP để tạo embedding ảnh-văn bản
• mô hình detection (YOLO) và phân loại thời tiết để làm metadata
• vector DB (Qdrant) tìm kiếm
• nuScenes/Waymo Open
• FastAPI + React/Next.js giao diện tìm kiếm và xem cảnh
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web tool đánh chỉ mục một tập dữ liệu mẫu, tìm kiếm bằng câu tự nhiên trả về frame khớp có preview, lọc theo metadata, ≥2 vai trò, báo cáo precision@k.

Nâng cao:
• tìm kiếm kết hợp ngữ nghĩa + metadata + hành vi thời gian trên tập lớn, xuất trực tiếp bộ dữ liệu/test từ kết quả, benchmark chất lượng truy vấn và tối ưu độ trễ/chi phí index
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-15] Safety Sentinel - Nền tảng đánh giá an toàn & phát hiện hồi quy từ phân tích disengagement

### 📝 Mô tả đề tài
📍 Thực trạng: Đánh giá độ an toàn của phiên bản mô hình lái đòi hỏi tổng hợp các sự kiện nguy hiểm và disengagement (thời điểm phải can thiệp) qua nhiều lần chạy, nhưng việc này thường thủ công và khó thấy được xu hướng hồi quy an toàn giữa các phiên bản.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng thu thập và phân tích các sự kiện an toàn từ log chạy mô phỏng (va chạm, vi phạm luật, phanh gấp, disengagement), tính các chỉ số an toàn, phân loại nguyên nhân và phát hiện hồi quy khi so sánh phiên bản, kèm dashboard cảnh báo; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư an toàn review và phê duyệt kết luận trước khi coi phiên bản đạt (human-in-the-loop); phân tích dựa trên log mô phỏng, không dùng để cấp phép vận hành thật khi chưa validate đầy đủ; chỉ số rõ ràng (tần suất sự kiện an toàn/1000km mô phỏng, phân bố mức nghiêm trọng, delta giữa phiên bản); tối ưu chi phí xử lý log lớn; bảo mật log và ẩn danh mọi dữ liệu người xuất hiện.

### 🛠️ Tech Stack
• Python
• CARLA/Isaac Sim để tạo log chạy
• pandas cho phân tích
• PyTorch/scikit-learn phân loại nguyên nhân sự kiện
• MLflow lưu kết quả các phiên bản
• FastAPI + React/Next.js dashboard an toàn
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• tool nạp log chạy mô phỏng, trích các sự kiện an toàn, tính chỉ số và hiển thị dashboard, ≥2 vai trò, HITL duyệt.

Nâng cao:
• phân loại nguyên nhân sự kiện tự động, so sánh nhiều phiên bản phát hiện hồi quy an toàn và liên kết tới scenario replay, benchmark trên bộ chạy lớn và tối ưu xử lý log
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-16] AdverTest - Công cụ sinh & kiểm thử adversarial cho perception (robustness testing)

### 📝 Mô tả đề tài
📍 Thực trạng: Mô hình perception có thể bị đánh lừa bởi nhiễu nhỏ, thời tiết xấu, che khuất hay patch adversarial, gây rủi ro an toàn, nhưng đội kỹ sư thiếu công cụ hệ thống để kiểm thử độ bền vững trước khi triển khai. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ sinh các phép biến đổi và tấn công adversarial (nhiễu, corruption thời tiết, che khuất, patch) áp lên dữ liệu perception và đo mức suy giảm hiệu năng của mô hình, giúp kỹ sư tìm điểm yếu và đánh giá robustness; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư review các trường hợp lỗi và quyết định biện pháp (human-in-the-loop); chỉ kiểm thử trên dữ liệu/mô phỏng, kết quả không dùng để triển khai thật khi chưa validate; chỉ số đo được (mAP/IoU trước và sau tấn công, robustness accuracy theo mức độ nhiễu, tỷ lệ tấn công thành công); tối ưu chi phí GPU khi chạy nhiều biến thể; ẩn danh khuôn mặt/biển số trong dữ liệu.

### 🛠️ Tech Stack
• Python, PyTorch
• thư viện adversarial/corruption (torchattacks, imagecorruptions)
• mô hình perception (YOLO, SAM2, MMDetection3D)
• nuScenes/KITTI
• FastAPI + React/Next.js dashboard so sánh trước/sau tấn công
• Weights & Biases
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• tool áp một số phép biến đổi/tấn công lên ảnh mẫu, chạy mô hình và hiển thị suy giảm hiệu năng trực quan, ≥2 vai trò, báo cáo mAP/IoU trước-sau.

Nâng cao:
• sinh và quét nhiều loại tấn công theo mức độ, tự động lập bảng robustness và tìm biến thể làm mô hình thất bại nhiều nhất, benchmark định lượng và tối ưu chi phí GPU
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-17] MapWatch - Công cụ tự động phát hiện thay đổi & cập nhật HD map từ dữ liệu fleet

### 📝 Mô tả đề tài
📍 Thực trạng: HD map cho xe tự lái phải luôn cập nhật (làn đường mới, biển báo thay đổi, công trình), nhưng dò tìm thay đổi thủ công từ dữ liệu fleet rất chậm và dễ bỏ sót, trong khi map cũ gây nguy hiểm. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ so khớp dữ liệu quan sát mới (ảnh/point cloud/quỹ đạo) với HD map hiện có để tự động phát hiện các điểm khác biệt (làn, vạch, biển báo thay đổi), khoanh vùng nghi ngờ và đề xuất cập nhật cho kỹ sư duyệt; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư map phải review và phê duyệt mọi thay đổi trước khi cập nhật vào map chính thức (human-in-the-loop); công cụ chạy trên dữ liệu ghi sẵn, không tác động phương tiện; chất lượng đo được (precision/recall phát hiện thay đổi so ground truth, độ chính xác vị trí thay đổi); tối ưu chi phí xử lý dữ liệu fleet lớn; ẩn danh khuôn mặt/biển số.

### 🛠️ Tech Stack
• Python
• Open3D, PCL cho point cloud và định vị
• OpenCV
• mô hình detection vạch/biển báo (YOLO, segmentation)
• nuScenes/Waymo Open (có HD map)
• FastAPI + React/Next.js + three.js hiển thị map và điểm thay đổi
• DVC quản lý phiên bản map
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• tool nạp một đoạn dữ liệu và HD map mẫu, phát hiện và khoanh vùng thay đổi, giao diện cho kỹ sư duyệt, ≥2 vai trò, HITL, báo cáo precision/recall.

Nâng cao:
• pipeline tổng hợp nhiều lần quan sát từ fleet để xác nhận thay đổi bền vững, tự sinh đề xuất bản vá map và quản lý phiên bản, benchmark phát hiện và tối ưu chi phí xử lý
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-18] IncidentLens - Trợ lý VLM phân tích & tóm tắt sự cố lái/disengagement từ log + video

### 📝 Mô tả đề tài
📍 Thực trạng: Sau mỗi sự cố hoặc disengagement, kỹ sư phải xem lại video cùng log cảm biến/điều khiển để hiểu chuyện gì xảy ra và viết báo cáo, việc này tốn thời gian và không đồng nhất giữa các người. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng trợ lý dùng VLM đọc đoạn video cùng dữ liệu log quanh thời điểm sự cố, tự động mô tả diễn biến, xác định thời điểm và yếu tố then chốt (tác nhân, hành vi, điều kiện), rồi sinh bản tóm tắt sự cố có cấu trúc để kỹ sư hoàn thiện; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: bản tóm tắt do trợ lý sinh chỉ là nháp, kỹ sư phải review và duyệt trước khi lưu chính thức (human-in-the-loop); phân tích trên log/video ghi sẵn, không can thiệp phương tiện; chất lượng đo được (độ chính xác nhận diện yếu tố sự cố so nhãn chuyên gia, độ đầy đủ của tóm tắt, tỷ lệ được kỹ sư chấp nhận); tối ưu chi phí gọi VLM và thời gian xử lý; ẩn danh khuôn mặt/biển số trong video.

### 🛠️ Tech Stack
• Python
• VLM/LLM (LLaVA, mô hình đa phương thức) + LangGraph
• đọc log ROS2/CSV
• CARLA để tạo tình huống sự cố mẫu
• DeepEval đánh giá chất lượng tóm tắt
• FastAPI + React/Next.js hiển thị video, timeline và báo cáo
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• tool nạp một đoạn video + log sự cố mẫu, sinh mô tả diễn biến và tóm tắt có cấu trúc, giao diện cho kỹ sư sửa và duyệt, ≥2 vai trò, HITL.

Nâng cao:
• trợ lý tự định vị thời điểm sự cố trong log dài, phân loại nguyên nhân, tổng hợp báo cáo hàng loạt và liên kết sự cố tương tự, benchmark chất lượng tóm tắt và tối ưu chi phí VLM
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-19] PlanBench - Simulator & benchmark path/motion planning cho robot di động (AMR/AGV)

### 📝 Mô tả đề tài
📍 Thực trạng: Có nhiều thuật toán lập quỹ đạo cho robot di động (A*, RRT*, DWA, học tăng cường), nhưng đội kỹ sư khó so sánh công bằng chúng trên cùng bản đồ/kịch bản và khó biết cái nào phù hợp với môi trường mục tiêu. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng simulator 2D/2.5D và bộ benchmark cho phép nạp bản đồ và kịch bản (chướng ngại tĩnh/động), chạy nhiều thuật toán planning, đo và so sánh hiệu năng, kèm trực quan hóa quỹ đạo và va chạm; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư review kết quả và phê duyệt thuật toán trước khi triển khai (human-in-the-loop); chỉ chạy trên mô phỏng, không điều khiển robot thật khi chưa validate; chỉ số rõ ràng (tỷ lệ tới đích, độ dài/độ mượt đường đi, thời gian tính, số va chạm, thời gian di chuyển); tối ưu tốc độ chạy benchmark và chi phí; dữ liệu là mô phỏng nên không có PII.

### 🛠️ Tech Stack
• Python
• Gazebo/ROS2 (Nav2) hoặc simulator 2D tự dựng
• các thuật toán planning (A*, RRT*, DWA), tùy chọn RL bằng PyTorch
• FastAPI + React/Next.js + Canvas/WebGL trực quan quỹ đạo
• MLflow lưu kết quả benchmark
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• simulator nạp bản đồ mẫu, chạy ít nhất 2 thuật toán planning và hiển thị quỹ đạo, ≥2 vai trò, báo cáo chỉ số so sánh.

Nâng cao:
• bộ benchmark với chướng ngại động và nhiều bản đồ/kịch bản, bảng xếp hạng thuật toán định lượng, tích hợp Nav2/ROS2 cho closed-loop và tối ưu tốc độ chạy benchmark
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-20] GraspTransfer - Sim-to-real cho robot grasping/manipulation với VLA & đánh giá thành công

### 📝 Mô tả đề tài
📍 Thực trạng: Robot gắp-thao tác dùng mô hình VLA huấn luyện trong mô phỏng nhưng khó chuyển sang thật do sim-to-real gap về hình ảnh và động lực học; đội phát triển cần công cụ huấn luyện, đánh giá và ước lượng khả năng transfer trước khi thử trên phần cứng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ huấn luyện chính sách grasping/manipulation trong mô phỏng (kèm domain randomization), đánh giá success rate trên nhiều vật thể/tư thế, và ước lượng độ bền transfer bằng cách kiểm thử trên các biến thể mô phỏng gần thực tế (nhiễu cảm biến, ánh sáng, vật thể mới); đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư review kết quả đánh giá và phê duyệt trước khi cân nhắc thử thật (human-in-the-loop); toàn bộ huấn luyện và đánh giá chỉ trên mô phỏng, không vận hành robot thật khi chưa validate; chỉ số rõ ràng (success rate theo vật thể/tư thế, độ bền dưới nhiễu, khoảng suy giảm giữa điều kiện chuẩn và điều kiện gần thực); tối ưu chi phí GPU và thời gian huấn luyện; dữ liệu tổng hợp không chứa PII.

### 🛠️ Tech Stack
• Python, PyTorch
• NVIDIA Isaac Sim/Isaac Lab hoặc MuJoCo
• VLA (OpenVLA), SAM2 cho tri giác vật thể
• ROS2 tùy chọn
• domain randomization
• Weights & Biases
• FastAPI + React/Next.js dashboard đánh giá
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• tool huấn luyện một policy grasping trong sim cho vài vật thể, đánh giá và hiển thị success rate, ≥2 vai trò, HITL duyệt kết quả.

Nâng cao:
• huấn luyện với domain randomization và đánh giá trên vật thể/điều kiện mới (unseen), ước lượng độ bền transfer định lượng qua các biến thể gần thực, benchmark nhiều cấu hình và tối ưu chi phí GPU/thời gian huấn luyện
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-21] doanh nghiệp sản xuất ô tô 3D Data Hub - Nền tảng quản trị dữ liệu 3D đa cảm biến cho ADAS

### 📝 Mô tả đề tài
📍 Thực trạng: Đội ADAS/Robotics cần quản lý dữ liệu camera, LiDAR, radar, GPS/IMU và annotation theo từng phiên bản xe, tuyến đường, thời tiết, ODD; dữ liệu rời rạc khiến việc tìm scene, kiểm soát chất lượng và tái huấn luyện mô hình rất chậm. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng data hub cho dữ liệu 3D xe tự lái của doanh nghiệp sản xuất ô tô: ingest log đa cảm biến, đồng bộ thời gian, chuẩn hóa metadata ODD, xem lại scene 3D, tìm kiếm theo tình huống và quản lý phiên bản dataset/label/model; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: Chỉ xử lý dữ liệu đã ghi, không điều khiển xe thật; bắt buộc ẩn danh biển số/khuôn mặt trước khi hiển thị; kỹ sư duyệt dataset trước khi đưa vào train; đo chất lượng dữ liệu bằng coverage ODD, tỷ lệ frame lỗi, độ lệch đồng bộ cảm biến và thời gian truy vấn; kiểm soát quyền truy cập theo dự án/đội xe.

### 🛠️ Tech Stack
• Python, PyTorch
• nuScenes/ASAM OpenLABEL/KITTI format
• ROS2/rosbag2, MCAP, GPS/IMU parser
• Open3D/PCL cho point cloud
• Qdrant/FAISS cho tìm kiếm scene bằng embedding
• DVC/LakeFS + MLflow quản lý phiên bản dataset/model
• FastAPI backend
• React/Next.js + three.js/WebGL xem scene 3D
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app nạp một bộ log camera-LiDAR mẫu, chuẩn hóa metadata, xem scene 3D và tìm kiếm theo object/thời tiết/tình huống, ≥2 vai trò (data engineer và kỹ sư ADAS), HITL duyệt dataset, báo cáo coverage ODD và lỗi dữ liệu.

Nâng cao:
• Pipeline ingest log quy mô lớn, đồng bộ đa cảm biến tự động, semantic search cho corner-case, versioning dataset/label/model, audit quyền truy cập và benchmark tốc độ truy vấn/chi phí lưu trữ
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-22] Vietnam Synthetic Street - Engine sinh dữ liệu tổng hợp giao thông Việt Nam cho perception ADAS

### 📝 Mô tả đề tài
📍 Thực trạng: Mô hình perception ADAS thường thiếu dữ liệu cho tình huống Việt Nam như xe máy dày đặc, đường hẹp, biển báo địa phương, mưa lớn, ngập, ánh sáng ban đêm; thu thập và gán nhãn dữ liệu thật tốn kém và không đủ corner-case. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng engine sinh synthetic data trong CARLA/Unreal/Isaac với ODD Việt Nam: tạo scene đường phố, xe máy/người đi bộ/ô tô, biến đổi thời tiết/ánh sáng, camera-LiDAR/radar giả lập, tự sinh nhãn 2D/3D box, segmentation, depth và optical flow để huấn luyện perception; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: Dữ liệu tổng hợp phải được kỹ sư review chất lượng trước khi dùng train; đo sim realism và hữu ích bằng FID/LPIPS, mAP tăng thêm sau khi train, coverage corner-case; không tuyên bố thay thế hoàn toàn dữ liệu thật; tối ưu throughput sinh dữ liệu và chi phí GPU. Tách biệt rõ bước kiểm chứng hình học/vật lý xác định bằng code với bước suy luận của mô hình; đánh giá định lượng trên tập dữ liệu thực tế kèm phân tích độ trễ xử lý.

### 🛠️ Tech Stack
• CARLA/Unreal Engine hoặc NVIDIA Isaac Sim
• Python, PyTorch
• domain randomization, procedural generation
• OpenSCENARIO/OpenDRIVE
• sensor simulation camera-LiDAR-radar
• format nuScenes/KITTI/COCO
• CVAT/Label Studio để kiểm tra nhãn
• FastAPI + React/Next.js dashboard sinh dữ liệu
• DVC + Weights & Biases
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Tool cấu hình một ODD Việt Nam, sinh batch ảnh/point cloud kèm nhãn 2D/3D/segmentation, preview dữ liệu và thống kê coverage, ≥2 vai trò, HITL duyệt dataset, báo cáo FID/LPIPS và số mẫu sinh/giờ.

Nâng cao:
• Sinh hàng loạt corner-case theo kịch bản, tích hợp domain randomization, train thử mô hình perception với dữ liệu synthetic + real và đo uplift mAP/IoU, tối ưu throughput và chi phí GPU
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-23] doanh nghiệp sản xuất ô tô Real2Sim ODD Builder - Chuyển log fleet thành scene mô phỏng chỉnh sửa được

### 📝 Mô tả đề tài
📍 Thực trạng: Khi xe chạy thử gặp tình huống hiếm, đội ADAS cần tái hiện lại đúng scene đó trong mô phỏng để phân tích, biến đổi và kiểm thử lại nhiều phiên bản mô hình; dựng tay từng scene từ log rất chậm. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng pipeline real2sim từ video/point cloud/log định vị của fleet doanh nghiệp sản xuất ô tô thành scene mô phỏng chỉnh sửa được: tái tạo hình học 3D, vật thể động, làn đường, thời tiết/ánh sáng; cho phép thay đổi tốc độ/tác nhân rồi replay trong CARLA/Isaac; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: Chỉ replay trong mô phỏng, không áp dụng trực tiếp lên xe thật; kỹ sư duyệt scene trước khi vào bộ regression test; phải ẩn danh dữ liệu thật; đo PSNR/SSIM/LPIPS, Chamfer distance, độ khớp trajectory và tỷ lệ replay chạy hợp lệ; tối ưu thời gian tái tạo scene. Tách biệt rõ bước kiểm chứng hình học/vật lý xác định bằng code với bước suy luận của mô hình; đánh giá định lượng trên tập dữ liệu thực tế kèm phân tích độ trễ xử lý.

### 🛠️ Tech Stack
• 3D Gaussian Splatting/NeRF (nerfstudio/gsplat)
• Open3D/PCL, SLAM/structure-from-motion
• SAM2/GroundingDINO để tách vật thể
• tracking quỹ đạo object
• CARLA/Isaac Sim + OpenSCENARIO
• Python, PyTorch
• FastAPI backend
• React/Next.js + three.js editor scene
• DVC/MLflow
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web app tái tạo một scene từ log/video mẫu, xem 3D và chỉnh sửa vài vật thể/điều kiện, export kịch bản sim, ≥2 vai trò, HITL duyệt scene, báo cáo PSNR/SSIM/Chamfer.

Nâng cao:
• Pipeline từ fleet log sang scene động có replay closed-loop, tự sinh biến thể corner-case, quản lý thư viện ODD và regression test, benchmark chất lượng tái tạo và thời gian xử lý
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-24] Sim2Real Perception Gap - Công cụ đo và giảm khoảng cách synthetic-to-real cho ADAS

### 📝 Mô tả đề tài
📍 Thực trạng: Dữ liệu synthetic giúp mở rộng corner-case nhưng mô hình perception có thể giảm hiệu năng khi chạy trên dữ liệu thật do khác texture, camera model, nhiễu LiDAR/radar, ánh sáng và phân bố giao thông. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ đo sim2real gap cho perception ADAS: so sánh feature distribution giữa synthetic và real-log, đánh giá model theo từng ODD, đề xuất domain randomization/style adaptation/finetune để giảm gap và theo dõi hiệu quả qua phiên bản dataset; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: Kỹ sư duyệt kết luận trước khi dùng để thay đổi tập train; chỉ đánh giá trên dữ liệu ghi sẵn hoặc mô phỏng; đo rõ mAP/IoU real holdout, FID/MMD feature, calibration error và gap theo ODD; không dùng synthetic làm bằng chứng an toàn duy nhất; ẩn danh dữ liệu thật. Tách biệt rõ bước kiểm chứng hình học/vật lý xác định bằng code với bước suy luận của mô hình; đánh giá định lượng trên tập dữ liệu thực tế kèm phân tích độ trễ xử lý.

### 🛠️ Tech Stack
• Python, PyTorch
• mô hình perception YOLO/BEVFusion/MMDetection3D
• metric FID, MMD, t-SNE/UMAP feature
• domain adaptation/style transfer (CycleGAN/DINO features tùy chọn)
• CARLA/Isaac synthetic data + nuScenes/Waymo/KITTI real proxy
• Weights & Biases/MLflow
• FastAPI + React/Next.js dashboard gap
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Dashboard so sánh synthetic vs real theo ODD, chạy một mô hình perception và báo cáo mAP/IoU + FID/MMD, ≥2 vai trò, HITL duyệt khuyến nghị.

Nâng cao:
• Agent tự đề xuất cấu hình randomization/finetune để giảm gap, chạy nhiều vòng thí nghiệm, tracking dataset version và chứng minh cải thiện trên real holdout/corner-case
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-25] 4D Occupancy Lab - Perception BEV/occupancy từ camera-LiDAR-radar cho ADAS đô thị

### 📝 Mô tả đề tài
📍 Thực trạng: ADAS đô thị cần hiểu không gian 3D động quanh xe: vật thể bị che khuất, vùng trống/chiếm dụng, hướng chuyển động và rủi ro va chạm; chỉ detection 2D/3D box đơn lẻ chưa đủ để hỗ trợ planning an toàn. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng lab huấn luyện và trực quan hóa mô hình BEV/4D occupancy fusion từ camera-LiDAR-radar, sinh bản đồ occupancy theo thời gian, occupancy flow và cảnh báo vùng rủi ro; giúp kỹ sư so sánh cấu hình sensor fusion cho doanh nghiệp sản xuất ô tô ADAS; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: Công cụ chỉ phân tích dữ liệu/mô phỏng, không điều khiển xe; kỹ sư review đầu ra trước khi dùng cho hạ nguồn; đo IoU occupancy, mAP detection, ADE/FDE occupancy flow và độ trễ inference; tối ưu chi phí GPU; ẩn danh dữ liệu thật khi hiển thị. Tách biệt rõ bước kiểm chứng hình học/vật lý xác định bằng code với bước suy luận của mô hình; đánh giá định lượng trên tập dữ liệu thực tế kèm phân tích độ trễ xử lý.

### 🛠️ Tech Stack
• Python, PyTorch
• BEVFusion/BEVFormer/OccNet-style models
• MMDetection3D, Open3D/PCL
• nuScenes/Waymo Open/KITTI
• radar point cloud processing
• FastAPI backend
• React/Next.js + three.js/WebGL render BEV/occupancy
• Weights & Biases
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Web tool chạy model fusion pretrained trên frame/sequence mẫu, hiển thị BEV + occupancy + vật thể chồng lên ảnh/point cloud, ≥2 vai trò, báo cáo IoU/mAP/độ trễ.

Nâng cao:
• So sánh nhiều cấu hình camera-LiDAR-radar, chạy sequence 4D occupancy flow, phân tích false positive/negative theo ODD và tối ưu latency/chi phí GPU
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [RAV-26] Data Curation Copilot - Agent chọn dữ liệu giá trị cao cho huấn luyện ADAS/Robotics

### 📝 Mô tả đề tài
📍 Thực trạng: Fleet log và synthetic data tạo ra quá nhiều frame/sequence; nếu chọn dữ liệu thủ công, đội kỹ sư dễ bỏ sót tình huống hiếm hoặc gán nhãn trùng lặp, làm chi phí annotation tăng mà mô hình không cải thiện tương xứng. Trong điều kiện vận hành thực tế (mật độ phương tiện hỗn hợp cao, che khuất, thời tiết xấu, cảm biến nhiễu hoặc trôi lệch), các thuật toán đơn lẻ rất dễ suy giảm hiệu năng đột ngột ở các ca biên (corner cases).

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng agent curation cho doanh nghiệp sản xuất ô tô ADAS/Robotics: tự chấm điểm dữ liệu theo độ hiếm, uncertainty của mô hình, diversity, coverage ODD và rủi ro an toàn; đề xuất batch cần gán nhãn/huấn luyện lại, kèm giải thích và dashboard so sánh hiệu quả chọn mẫu; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: Kỹ sư dữ liệu duyệt danh sách trước khi gửi gán nhãn/train; chỉ xử lý dữ liệu đã ghi hoặc synthetic; ẩn danh PII; đo hiệu quả bằng uplift mAP/IoU theo số mẫu, diversity score, tỷ lệ corner-case và chi phí annotation tiết kiệm; tránh thiên lệch chỉ chọn mẫu dễ hoặc một ODD duy nhất.

### 🛠️ Tech Stack
• Python, PyTorch
• embedding CLIP/DINOv2 cho ảnh và point cloud features
• uncertainty sampling từ mô hình perception
• Qdrant/FAISS clustering & semantic search
• active learning loop
• CVAT/Label Studio integration
• DVC + MLflow/Weights & Biases
• FastAPI + React/Next.js dashboard curation
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• Tool chấm điểm và xếp hạng dữ liệu mẫu, lọc theo ODD/corner-case, kỹ sư duyệt batch cần gán nhãn, ≥2 vai trò, báo cáo diversity và uplift mô phỏng so với chọn ngẫu nhiên.

Nâng cao:
• Vòng active learning khép kín từ chọn mẫu - gán nhãn - train lại - đánh giá, kết hợp real + synthetic data, tối ưu chi phí annotation và tự tạo báo cáo dataset readiness
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---
