# Lĩnh vực: ADAS - ADAS – Hệ thống hỗ trợ lái & Xe tự hành

> Tổng số đề tài: **30 đề tài**

## 📌 Danh sách đề tài

| Mã đề tài | Tên đề tài |
|---|---|
| `ADAS-01` | [Detection Doctor - Công cụ chẩn đoán lỗi phát hiện vật thể 2D/3D theo khoảng cách, mức che khuất và điều kiện môi trường](#adas-01) |
| `ADAS-02` | [TrackSense - Nền tảng đánh giá và gỡ lỗi theo dõi đa đối tượng (MOT) trong cảnh giao thông đông xe máy](#adas-02) |
| `ADAS-03` | [Panoptic Street VN - Phân vùng ngữ nghĩa/panoptic cho đường phố Việt Nam với nhãn bán tự động và phân tích lớp hiếm](#adas-03) |
| `ADAS-04` | [OccuGuard - Ước lượng occupancy 3D kèm độ bất định và cảnh báo vùng chưa chắc chắn](#adas-04) |
| `ADAS-05` | [DriveSpace - Phát hiện free-space và vùng có thể đi được trên đường Việt Nam không vạch, đường hẻm và đường bị lấn chiếm](#adas-05) |
| `ADAS-06` | [LaneScope - Nhận dạng làn đường và ranh giới đường (road boundary) khi vạch mờ, mất vạch hoặc bị che](#adas-06) |
| `ADAS-07` | [SignalWatch - Nhận dạng đèn giao thông (đèn tròn, đèn mũi tên, đèn đếm ngược) và gán đèn với làn tương ứng](#adas-07) |
| `ADAS-08` | [SignGuard VN - Nhận dạng biển báo giao thông Việt Nam theo quy chuẩn báo hiệu đường bộ và cảnh báo xung đột](#adas-08) |
| `ADAS-09` | [DepthTrust - Ước lượng độ sâu đơn mục (monocular depth) kèm kiểm tra độ tin cậy bằng LiDAR và stereo](#adas-09) |
| `ADAS-10` | [FlowLens - Ước lượng optical flow/scene flow và phát hiện vật thể chuyển động bất thường hoặc không thuộc lớp đã biết](#adas-10) |
| `ADAS-11` | [FusionTrace - Đánh giá độ bền của fusion camera-LiDAR-radar và fusion theo thời gian khi cảm biến suy giảm hoặc lệch hiệu chuẩn](#adas-11) |
| `ADAS-12` | [VisLoc VN - Định vị bằng thị giác (nhận diện địa điểm và tái định vị 6-DoF) trong đô thị khi thay đổi ngày/đêm, mùa và công trình](#adas-12) |
| `ADAS-13` | [LiDAR Loc Bench - Định vị LiDAR trên bản đồ điểm (scan-to-map) và phát hiện suy biến, trôi lệch và mất định vị](#adas-13) |
| `ADAS-14` | [VIO Studio - Gỡ lỗi và benchmark visual-inertial odometry (VIO) với phân tích nguyên nhân mất bám](#adas-14) |
| `ADAS-15` | [Multi-Session Mapper - Dựng và hợp nhất bản đồ đa chuyến (multi-session SLAM) từ log của nhiều xe/nhiều ngày](#adas-15) |
| `ADAS-16` | [OnlineMap Lab - Dựng bản đồ vector trực tuyến (online HD map construction) từ camera/LiDAR và đánh giá cấu trúc topology](#adas-16) |
| `ADAS-17` | [HDMap Auditor - Kiểm định chất lượng và tính nhất quán của HD map (Lanelet2/OpenDRIVE) bằng quy tắc và agent](#adas-17) |
| `ADAS-18` | [ChangeTriage - Phân loại và ưu tiên sự kiện thay đổi bản đồ (công trường, vạch/biển mới, làn tạm) để giảm cảnh báo giả](#adas-18) |
| `ADAS-19` | [MapLite Drive - Định vị và hiểu đường theo hướng 'map-light': bản đồ SD/OpenStreetMap kết hợp perception trực tuyến thay cho HD map](#adas-19) |
| `ADAS-20` | [SensorSim Lab - Mô phỏng cảm biến camera/LiDAR/radar với mô hình nhiễu thực tế và hiệu chỉnh tham số theo dữ liệu thật](#adas-20) |
| `ADAS-21` | [VehicleTwin - Mô hình hóa động lực học xe và hiệu chỉnh tham số xe từ log CAN để mô phỏng sát thực tế](#adas-21) |
| `ADAS-22` | [VN Traffic Sim - Mô phỏng giao thông hỗn hợp nhiều xe máy kiểu Việt Nam và hiệu chỉnh hành vi theo video thực](#adas-22) |
| `ADAS-23` | [WeatherForge - Mô phỏng điều kiện môi trường (mưa, sương, nắng gắt, đêm, mặt đường ướt) và ma trận phủ ODD cho kiểm thử perception](#adas-23) |
| `ADAS-24` | [ScenarioMiner - Khai thác kịch bản từ log lái thực và chuyển thành kịch bản OpenSCENARIO tham số hóa](#adas-24) |
| `ADAS-25` | [CriticalScenario Search - Tìm kịch bản nguy hiểm cho bộ lập kế hoạch bằng tối ưu hóa và tìm kiếm đối kháng trong mô phỏng](#adas-25) |
| `ADAS-26` | [RouteTwin - Digital twin tuyến đường thử dựng từ bản đồ OSM, ảnh vệ tinh và dữ liệu GNSS, có đối chiếu twin với thực tế](#adas-26) |
| `ADAS-27` | [CounterfactualLab - Phát lại log và đánh giá phản thực (what-if) khi thay đổi bộ lập kế hoạch, độ trễ hoặc hành vi tác nhân](#adas-27) |
| `ADAS-28` | [SimCI - Hạ tầng kiểm thử closed-loop trong CI/CD với chọn lọc test, phát hiện test chập chờn và đảm bảo tính tái lặp](#adas-28) |
| `ADAS-29` | [XIL Orchestrator - Điều phối kiểm thử SIL - HIL - VIL từ một đặc tả test duy nhất kèm truy vết yêu cầu và đo trễ thời gian thực](#adas-29) |
| `ADAS-30` | [Fidelity Scorecard - Chấm điểm độ trung thực mô phỏng và kiểm chứng sim-to-real ở mức cảm biến, hành vi và kết quả kiểm thử](#adas-30) |

---

## [ADAS-01] Detection Doctor - Công cụ chẩn đoán lỗi phát hiện vật thể 2D/3D theo khoảng cách, mức che khuất và điều kiện môi trường

### 📝 Mô tả đề tài
📍 Thực trạng: Mô hình object detection có mAP/NDS tổng thể cao vẫn có thể bỏ sót người đi xe máy bị che khuất hoặc vật thể ở xa 60-80 m; kỹ sư perception thường chỉ nhìn một con số tổng nên mất nhiều ngày lọc thủ công để biết mô hình sai ở đâu và vì sao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ nạp dự đoán box 2D/3D và ground truth, tự động phân loại lỗi (bỏ sót, dương tính giả, sai vị trí, sai kích thước/hướng, nhầm lớp), cắt lát theo khoảng cách, mức che khuất, thời tiết, ngày/đêm, sau đó dùng một agent (LLM/VLM) gom các lỗi cùng nguyên nhân, nêu giả thuyết nguyên nhân kèm frame minh chứng và đề xuất loại dữ liệu cần bổ sung; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư perception phải duyệt giả thuyết của agent trước khi đưa vào backlog cải tiến (human-in-the-loop); chỉ dùng dữ liệu công khai hoặc log đã ghi sẵn, đã ẩn danh khuôn mặt/biển số; mọi kết luận phải truy ngược được về frame cụ thể; hiệu quả đo bằng mAP/NDS, AP theo dải khoảng cách, tỷ lệ từng loại lỗi và thời gian triage tiết kiệm so với làm tay; công cụ không tự sửa dữ liệu hay mô hình.

### 🛠️ Tech Stack
• Python, PyTorch
• MMDetection3D/OpenPCDet (CenterPoint, PointPillars, BEVFusion) hoặc Ultralytics YOLO/RT-DETR
• nuScenes/Waymo Open/KITTI devkit
• Open3D để xem point cloud
• CLIP/DINOv2 embedding + Qdrant/FAISS để gom cụm lỗi
• VLM (Qwen2.5-VL/InternVL) + LangGraph cho agent chẩn đoán
• FastAPI backend
• React/Next.js + three.js để xem box 3D
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp dự đoán và ground truth của một mô hình detection trên bộ dữ liệu công khai, phân loại lỗi tự động, dashboard cắt lát theo khoảng cách/che khuất/thời tiết, xem chi tiết từng frame lỗi, ≥2 vai trò (kỹ sư perception và trưởng nhóm), HITL duyệt giả thuyết, báo cáo AP theo lát cắt và tỷ lệ các loại lỗi.

Nâng cao:
• agent gom cụm lỗi bằng embedding và sinh báo cáo nguyên nhân có trích dẫn frame, so sánh hai phiên bản mô hình để phát hiện hồi quy theo lát cắt, đề xuất danh sách dữ liệu cần thu thập thêm, đo mức đồng thuận giữa chẩn đoán của agent và kỹ sư, benchmark thời gian xử lý trên bộ dữ liệu lớn
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-02] TrackSense - Nền tảng đánh giá và gỡ lỗi theo dõi đa đối tượng (MOT) trong cảnh giao thông đông xe máy

### 📝 Mô tả đề tài
📍 Thực trạng: Trong giao thông đô thị Việt Nam, hàng chục xe máy đi sát nhau, che khuất và đổi làn liên tục khiến tracker dễ đổi ID, đứt quỹ đạo hoặc nhập hai xe thành một; điều này làm sai dự đoán quỹ đạo và quyết định phanh/né phía sau, nhưng đội kỹ sư thiếu công cụ chỉ ra tracker hỏng ở đâu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng chạy và so sánh nhiều thuật toán tracking (tracking-by-detection 2D/3D) trên cùng dữ liệu, tự động phát hiện các sự kiện lỗi như ID switch, fragmentation, track ma, track bị trễ khởi tạo, hiển thị từng sự kiện trên timeline kèm video/BEV và agent giải thích nguyên nhân khả dĩ (che khuất, detection chớp tắt, gating sai, motion model không phù hợp); đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư phải xác nhận nguyên nhân do agent đề xuất trước khi chỉnh tham số tracker (human-in-the-loop); chỉ xử lý dữ liệu đã ghi sẵn hoặc công khai, ẩn danh khuôn mặt/biển số; đo bằng HOTA, IDF1, MOTA/AMOTA, số ID switch trên 1000 frame và tỷ lệ track fragment; so sánh các tracker phải dùng cùng detection đầu vào để công bằng; theo dõi tốc độ xử lý (FPS) và bộ nhớ của từng tracker.

### 🛠️ Tech Stack
• Python, PyTorch
• ByteTrack/OC-SORT/StrongSORT (2D), AB3DMOT/SimpleTrack/CenterPoint tracking (3D)
• TrackEval để tính HOTA/IDF1
• nuScenes/Waymo Open/BDD100K MOT
• OpenCV, Open3D
• LLM/VLM + LangGraph cho agent giải thích sự kiện lỗi
• FastAPI backend
• React/Next.js với timeline + BEV viewer
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app chạy ≥2 tracker trên cùng chuỗi dữ liệu công khai, phát hiện và liệt kê ID switch/fragmentation, timeline sự kiện với video + BEV, báo cáo HOTA/IDF1, ≥2 vai trò (kỹ sư tracking và người duyệt), HITL xác nhận nguyên nhân.

Nâng cao:
• agent phân loại nguyên nhân lỗi tự động và gợi ý tinh chỉnh tham số (gating, thời gian sống của track), tìm kiếm tham số tự động trên tập validation, đánh giá riêng cho nhóm xe máy/người đi bộ trong cảnh đông, benchmark FPS và độ ổn định khi một cảm biến mất khung hình
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-03] Panoptic Street VN - Phân vùng ngữ nghĩa/panoptic cho đường phố Việt Nam với nhãn bán tự động và phân tích lớp hiếm

### 📝 Mô tả đề tài
📍 Thực trạng: Mô hình segmentation huấn luyện trên Cityscapes hay Mapillary hoạt động kém trên đường Việt Nam: vỉa hè bị lấn chiếm, xe máy dày đặc, hàng quán ven đường, đường hẻm hẹp, vạch kẻ mờ; các lớp này hiếm và chưa có nhãn chuẩn nên khó đo và khó cải thiện.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ dựng bộ dữ liệu segmentation cho đường Việt Nam theo hướng bán tự động: dùng mô hình nền (SAM2/Mask2Former) sinh nhãn nháp, người gán nhãn chỉnh sửa, huấn luyện/tinh chỉnh model và phân tích hiệu năng theo từng lớp, đặc biệt lớp hiếm đặc thù Việt Nam; agent đề xuất ảnh nào nên gán nhãn tiếp theo; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: người gán nhãn và kỹ sư phải duyệt nhãn trước khi đưa vào tập huấn luyện (human-in-the-loop), nhãn nháp của mô hình không được coi là ground truth; ảnh phải được ẩn danh khuôn mặt/biển số; đo bằng mIoU, PQ và IoU riêng cho lớp hiếm, số thao tác sửa nhãn trên mỗi ảnh và chi phí gán nhãn tiết kiệm so với gán thủ công; tuân thủ giấy phép của dữ liệu công khai được dùng.

### 🛠️ Tech Stack
• Python, PyTorch
• Mask2Former/SegFormer/OneFormer
• SAM2 để sinh nhãn nháp
• Cityscapes/Mapillary Vistas/BDD100K làm dữ liệu nền
• CVAT hoặc Label Studio tích hợp
• active learning (entropy/margin sampling), CLIP/DINOv2 embedding
• FastAPI backend
• React/Next.js (trình xem mask, so sánh trước/sau)
• DVC + MLflow quản lý phiên bản dataset/model
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp một tập ảnh đường phố, sinh nhãn nháp bằng SAM2/Mask2Former, giao diện chỉnh sửa và duyệt nhãn, huấn luyện/tinh chỉnh một model nhỏ, báo cáo mIoU theo lớp, ≥2 vai trò (người gán nhãn và kỹ sư duyệt), HITL duyệt nhãn.

Nâng cao:
• vòng active learning khép kín (chọn ảnh - gán nhãn - train - đánh giá) với agent đề xuất ảnh theo độ bất định và độ hiếm, đo đường cong mIoU theo số ảnh gán nhãn so với chọn ngẫu nhiên, phân tích lỗi theo lớp hiếm (xe máy chở hàng cồng kềnh, vỉa hè bị lấn), kiểm tra độ đồng nhất giữa các người gán nhãn
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-04] OccuGuard - Ước lượng occupancy 3D kèm độ bất định và cảnh báo vùng chưa chắc chắn

### 📝 Mô tả đề tài
📍 Thực trạng: Occupancy network cho biết ô không gian nào bị chiếm, nhưng thường chỉ xuất ra một dự đoán cứng, không nói ô nào mô hình không chắc (phía sau vật che khuất, xa cảm biến, trời tối); ADAS đưa ra quyết định dựa trên vùng 'trống' sai có thể gây nguy hiểm.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng hệ thống chạy mô hình semantic occupancy từ camera (và tùy chọn LiDAR), đồng thời ước lượng độ bất định theo từng voxel (ensemble/MC-dropout/evidential), hiển thị bản đồ occupancy 3D với lớp phủ độ tin cậy, đánh dấu vùng 'không biết' và để agent tóm tắt những vùng rủi ro cao trong từng cảnh; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư phải duyệt ngưỡng cảnh báo độ bất định trước khi dùng để đánh giá (human-in-the-loop); chỉ chạy offline trên dữ liệu đã ghi, không đưa kết quả vào điều khiển xe thật; độ bất định phải được hiệu chuẩn và đo bằng ECE/AUROC khi dự đoán lỗi, kèm mIoU/IoU occupancy; theo dõi độ trễ suy luận trên GPU; ảnh và point cloud phải ẩn danh PII.

### 🛠️ Tech Stack
• Python, PyTorch
• BEVFormer/FB-OCC/SurroundOcc/TPVFormer hoặc mô hình occupancy mã nguồn mở tương đương
• Occ3D-nuScenes, OpenOccupancy, SemanticKITTI
• MC-dropout/deep ensemble/evidential learning
• Open3D, three.js để dựng voxel
• LLM + LangGraph để tóm tắt vùng rủi ro
• FastAPI backend
• React/Next.js
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp một chuỗi dữ liệu công khai, chạy mô hình occupancy, hiển thị voxel 3D theo lớp và lớp phủ độ bất định, kèm bảng IoU và ECE, ≥2 vai trò (kỹ sư perception và reviewer an toàn), HITL duyệt ngưỡng cảnh báo.

Nâng cao:
• so sánh nhiều phương pháp ước lượng độ bất định, kiểm tra độ bất định có dự báo được vùng dự đoán sai hay không (risk-coverage curve), agent tóm tắt từng cảnh bằng ngôn ngữ tự nhiên ('vùng sau xe tải bên phải chưa chắc chắn'), phân tích hồi quy theo thời tiết/ngày-đêm, benchmark độ trễ và bộ nhớ
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-05] DriveSpace - Phát hiện free-space và vùng có thể đi được trên đường Việt Nam không vạch, đường hẻm và đường bị lấn chiếm

### 📝 Mô tả đề tài
📍 Thực trạng: Nhiều bài toán free-space/drivable-area giả định đường có vạch và lề rõ ràng; trong khi ở Việt Nam có đường hẻm, đường không vạch, mặt đường ngập nước, ổ gà, xe đỗ lấn làn khiến vùng có thể đi được khó định nghĩa và mô hình dễ ước lượng sai.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ xác định vùng có thể đi được từ ảnh camera (có thể kết hợp LiDAR/depth), phân biệt mặt đường, vỉa hè, vùng bị che bởi xe đỗ, vũng nước; kiểm tra chéo kết quả với độ sâu hoặc point cloud để đánh dấu vùng mâu thuẫn và cho phép kỹ sư xem, so sánh và gán nhãn lại các tình huống khó; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt các tình huống bị gắn cờ 'mâu thuẫn' trước khi đưa vào tập huấn luyện/đánh giá (human-in-the-loop); chỉ chạy trên dữ liệu đã ghi sẵn, không điều khiển xe; ẩn danh khuôn mặt/biển số; đo bằng IoU/F1 vùng drivable, tỷ lệ drivable dương tính giả (nguy hiểm hơn bỏ sót) và độ nhất quán camera-LiDAR; theo dõi độ trễ suy luận để hướng tới thời gian thực.

### 🛠️ Tech Stack
• Python, PyTorch
• SegFormer/Mask2Former hoặc PIDNet cho drivable area
• BDD100K drivable area, Cityscapes, KITTI Road, nuScenes
• Depth Anything/UniDepth hoặc LiDAR projection để kiểm tra chéo
• OpenCV
• VLM để mô tả vùng khó
• FastAPI backend
• React/Next.js (overlay mask trên ảnh/BEV)
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp ảnh/chuỗi video công khai, dự đoán vùng drivable, overlay lên ảnh và BEV, báo cáo IoU và tỷ lệ dương tính giả, ≥2 vai trò (kỹ sư và người duyệt), HITL xác nhận các ca khó.

Nâng cao:
• kiểm tra chéo bằng LiDAR/depth để tự động gắn cờ vùng drivable nghi ngờ, phân loại tình huống khó (đường hẻm, ngập nước, xe đỗ lấn), xây bộ đánh giá nhỏ riêng cho đường Việt Nam, benchmark độ trễ khi lượng tử hóa (TensorRT/ONNX) và phân tích đánh đổi độ chính xác - tốc độ
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-06] LaneScope - Nhận dạng làn đường và ranh giới đường (road boundary) khi vạch mờ, mất vạch hoặc bị che

### 📝 Mô tả đề tài
📍 Thực trạng: Lane keeping và lane centering phụ thuộc vào nhận dạng làn; trên thực tế vạch sơn mờ, bị che bởi xe, bóng đổ, nước phản chiếu, hoặc không có vạch (đường nông thôn, đường đang thi công) làm thuật toán lane detection xuống cấp mạnh nhưng rất khó biết khi nào và vì sao.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng hệ thống nhận dạng làn và ranh giới đường (đường cong 2D/3D, loại vạch, làn ego/làn kề), có module ước lượng độ tin cậy và nhận biết khi vạch bị suy giảm, đồng thời dashboard phân tích lỗi theo điều kiện (đêm, mưa, vạch mờ, đường cong gắt, ngã ba) kèm agent tóm tắt các điều kiện làm hệ thống thất bại; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt các tình huống thất bại và nhãn bổ sung (human-in-the-loop); chỉ chạy offline trên dữ liệu công khai hoặc đã ghi sẵn, không điều khiển xe; đo bằng F1 theo ngưỡng khoảng cách, lỗi lệch ngang (lateral error) theo khoảng nhìn, độ chính xác phân loại loại vạch và hiệu chuẩn độ tin cậy; theo dõi độ trễ để đáp ứng thời gian thực; ẩn danh PII trong ảnh.

### 🛠️ Tech Stack
• Python, PyTorch
• CLRNet/UFLD/LaneATT (2D), PersFormer/BEV-LaneDet/LaneSegNet (3D)
• OpenLane, CULane, TuSimple, Argoverse 2/nuScenes map layers
• OpenCV
• LLM/VLM + LangGraph để tóm tắt nhóm lỗi
• FastAPI backend
• React/Next.js (overlay đường cong, so sánh dự đoán và nhãn)
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp ảnh/video công khai, vẽ đường cong làn dự đoán và nhãn, báo cáo F1 và lỗi lệch ngang, bộ lọc theo điều kiện, ≥2 vai trò (kỹ sư và reviewer), HITL duyệt ca thất bại.

Nâng cao:
• ước lượng độ tin cậy và phát hiện 'vạch suy giảm' để cảnh báo sớm, mô hình ranh giới đường khi không có vạch, agent gom nhóm điều kiện thất bại và đề xuất dữ liệu bổ sung, benchmark độ trễ và độ ổn định theo thời gian (flicker của đường cong giữa các frame)
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-07] SignalWatch - Nhận dạng đèn giao thông (đèn tròn, đèn mũi tên, đèn đếm ngược) và gán đèn với làn tương ứng

### 📝 Mô tả đề tài
📍 Thực trạng: Nhận biết trạng thái đèn giao thông là yêu cầu bắt buộc ở giao lộ, nhưng đèn rất nhỏ ở xa, bị chói/ngược sáng, bị cây hoặc xe tải che, nhiều cụm đèn cùng lúc; ở Việt Nam còn có đèn đếm ngược và đèn mũi tên cho từng hướng, nên việc gán đúng đèn với làn của xe là khó và dễ sai.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng hệ thống phát hiện đèn giao thông và phân loại trạng thái (đỏ/vàng/xanh, mũi tên, đèn đếm ngược, tắt/nhấp nháy), theo dõi theo thời gian để giảm nhấp nháy dự đoán và gán đèn cho làn ego dựa trên bố cục giao lộ; agent giải thích vì sao đưa ra trạng thái cuối cùng và liệt kê các ca không chắc chắn; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư phải duyệt các ca 'không chắc chắn' và nhãn gán đèn-làn (human-in-the-loop); chỉ chạy offline trên dữ liệu đã ghi, tuyệt đối không dùng kết quả để điều khiển xe thật; ưu tiên không bỏ sót đèn đỏ, đo tỷ lệ nhận nhầm đỏ thành xanh riêng; đo bằng mAP phát hiện, accuracy trạng thái theo kích thước đèn, độ chính xác gán đèn-làn và độ ổn định theo thời gian; ẩn danh PII.

### 🛠️ Tech Stack
• Python, PyTorch
• YOLO/RT-DETR cho phát hiện vật nhỏ, ROI classifier cho trạng thái
• Bosch Small Traffic Lights, LISA Traffic Light, DriveU Traffic Light, BDD100K
• OpenCV, bộ lọc thời gian (Kalman/HMM)
• OpenStreetMap/HD map để biết bố cục giao lộ
• VLM để giải thích ca khó
• FastAPI backend
• React/Next.js
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp video giao lộ công khai, phát hiện đèn và trạng thái, hiển thị timeline trạng thái, báo cáo mAP và accuracy theo kích thước đèn, ≥2 vai trò (kỹ sư và người duyệt), HITL duyệt ca không chắc chắn.

Nâng cao:
• gán đèn với làn bằng thông tin bản đồ/bố cục giao lộ, bộ lọc thời gian để loại nhấp nháy, nhận dạng đèn đếm ngược và đèn mũi tên, kiểm thử độ bền với chói sáng/mưa/đêm, đo tỷ lệ nhầm đỏ-xanh và benchmark độ trễ ở độ phân giải cao
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-08] SignGuard VN - Nhận dạng biển báo giao thông Việt Nam theo quy chuẩn báo hiệu đường bộ và cảnh báo xung đột

### 📝 Mô tả đề tài
📍 Thực trạng: Biển báo Việt Nam khác nhiều so với các bộ dữ liệu quốc tế: biển cấm theo giờ, biển phụ, biển tạm thời tại công trường, biển bị che hoặc mờ, thậm chí hai biển mâu thuẫn trên cùng đoạn đường; mô hình huấn luyện trên dữ liệu nước ngoài dễ nhận nhầm hoặc hiểu sai ý nghĩa.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng hệ thống phát hiện và phân loại biển báo Việt Nam (cấm, nguy hiểm, hiệu lệnh, chỉ dẫn, biển phụ), kèm module RAG trên quy chuẩn báo hiệu đường bộ (QCVN 41) để giải thích ý nghĩa, đọc điều kiện kèm theo của biển phụ (giờ, loại xe) và phát hiện xung đột giữa các biển liên tiếp để cảnh báo kỹ sư; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt các ca xung đột và ca ý nghĩa biển không chắc chắn trước khi đưa vào dữ liệu đánh giá (human-in-the-loop); phần giải thích bằng RAG phải trích dẫn điều khoản nguồn và không được tự suy diễn ngoài quy chuẩn; chỉ dùng dữ liệu công khai hoặc đã ghi, ẩn danh PII; đo bằng mAP phát hiện, accuracy phân loại theo lớp hiếm, độ chính xác trích xuất điều kiện biển phụ và faithfulness của giải thích.

### 🛠️ Tech Stack
• Python, PyTorch
• YOLO/RT-DETR + classifier tinh chỉnh (ViT/ConvNeXt)
• Mapillary Traffic Sign Dataset, TT100K, GTSRB làm dữ liệu khởi tạo, bổ sung ảnh tự gán nhãn
• OCR (PaddleOCR) để đọc chữ trên biển phụ
• RAG trên văn bản QCVN 41: embedding + Qdrant/pgvector, reranker
• LLM + LangGraph
• FastAPI backend
• React/Next.js
• RAGAS/DeepEval
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp ảnh/video đường phố, phát hiện và phân loại biển, hiển thị ý nghĩa có trích dẫn điều khoản, đọc biển phụ cơ bản, báo cáo mAP/accuracy theo lớp, ≥2 vai trò (kỹ sư và chuyên gia luật giao thông), HITL duyệt ca không chắc chắn.

Nâng cao:
• phát hiện xung đột/hết hiệu lực giữa các biển liên tiếp trên một đoạn đường, xử lý biển tạm thời tại công trường, tổng hợp dữ liệu hiếm bằng sinh ảnh có kiểm soát, đánh giá chất lượng RAG (faithfulness, citation accuracy), benchmark độ trễ và độ bền với mờ/che/ngược sáng
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-09] DepthTrust - Ước lượng độ sâu đơn mục (monocular depth) kèm kiểm tra độ tin cậy bằng LiDAR và stereo

### 📝 Mô tả đề tài
📍 Thực trạng: Camera đơn rẻ và phổ biến trên xe, nhưng độ sâu ước lượng từ một ảnh có thể sai số lớn ở xa, trên vật thể trong suốt/phản chiếu hoặc ngoài phân phối huấn luyện; kỹ sư khó biết khi nào có thể tin độ sâu này cho các chức năng ADAS như ước lượng khoảng cách tới xe phía trước.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng chạy nhiều mô hình depth (metric depth và relative depth), so sánh với LiDAR/stereo làm tham chiếu, đo sai số theo khoảng cách và loại vật thể, ước lượng độ bất định theo pixel và tạo bản đồ 'vùng không đáng tin' để kỹ sư xem; agent tóm tắt điều kiện làm mô hình sai nhiều nhất; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt ngưỡng tin cậy và kết luận 'dùng được/không dùng được' theo từng điều kiện (human-in-the-loop); chỉ chạy offline trên dữ liệu đã ghi, không dùng cho điều khiển thật; đo bằng AbsRel, RMSE, δ<1.25 theo dải khoảng cách và chất lượng độ bất định (AUSE/ECE); phân biệt rõ độ sâu metric và độ sâu tương đối để tránh so sánh sai; theo dõi độ trễ suy luận.

### 🛠️ Tech Stack
• Python, PyTorch
• Depth Anything V2, UniDepth, Metric3D v2, ZoeDepth, Monodepth2
• KITTI Depth, DDAD, nuScenes, Argoverse 2 (LiDAR projection làm ground truth thưa)
• Open3D, OpenCV
• LLM/VLM + LangGraph để tóm tắt điều kiện lỗi
• FastAPI backend
• React/Next.js (viewer depth map, point cloud, bản đồ sai số)
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp ảnh và LiDAR công khai, chạy ≥2 mô hình depth, hiển thị depth map và bản đồ sai số so với LiDAR, báo cáo AbsRel/RMSE theo dải khoảng cách, ≥2 vai trò (kỹ sư và reviewer), HITL duyệt ngưỡng tin cậy.

Nâng cao:
• ước lượng độ bất định và đánh giá chất lượng của nó, hiệu chỉnh scale metric bằng thông tin phụ (chiều cao camera, kích thước vật thể đã biết), phân tích sai số theo điều kiện (đêm, mưa, kính, bề mặt phản chiếu), benchmark độ trễ khi tối ưu TensorRT và đánh đổi chính xác - tốc độ
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-10] FlowLens - Ước lượng optical flow/scene flow và phát hiện vật thể chuyển động bất thường hoặc không thuộc lớp đã biết

### 📝 Mô tả đề tài
📍 Thực trạng: Detector chỉ nhận ra các lớp đã được huấn luyện; vật thể lạ (hàng rơi, xe cải tiến chở đồ cồng kềnh, động vật) vẫn có thể là chướng ngại nguy hiểm. Thông tin chuyển động (optical flow 2D, scene flow 3D) là tín hiệu bổ sung giúp phát hiện vật thể chuyển động mà không cần biết lớp, nhưng thường nhiễu và ít được đánh giá có hệ thống.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ ước lượng optical flow từ video và scene flow từ cặp point cloud liên tiếp, bù chuyển động của xe (ego-motion) để tách vật thể động, phát hiện vật thể chuyển động không thuộc danh mục lớp, trực quan hóa vector chuyển động trên ảnh/BEV và để agent tóm tắt những vật thể động nghi ngờ trong từng cảnh; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt các phát hiện 'vật thể động không rõ lớp' trước khi dùng làm dữ liệu đánh giá hay gán nhãn (human-in-the-loop); chỉ chạy offline trên dữ liệu công khai/đã ghi, không điều khiển xe; đo bằng EPE (2D/3D), Acc strict/relaxed, EPE riêng cho điểm động và recall/precision phát hiện vật thể động; ẩn danh PII; theo dõi thời gian xử lý trên mỗi cặp frame.

### 🛠️ Tech Stack
• Python, PyTorch
• RAFT/GMFlow cho optical flow
• FastFlow3D, Neural Scene Flow Prior (NSFP), Flow4D/DeFlow cho scene flow
• KITTI Scene Flow, Argoverse 2 Sensor/Scene Flow, Waymo Open, nuScenes
• Open3D
• VLM để mô tả vật thể động nghi ngờ
• FastAPI backend
• React/Next.js + three.js
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp chuỗi dữ liệu công khai, tính optical flow và/hoặc scene flow, bù ego-motion, hiển thị vector chuyển động trên ảnh/BEV, báo cáo EPE và precision/recall điểm động, ≥2 vai trò (kỹ sư và reviewer), HITL duyệt phát hiện.

Nâng cao:
• phát hiện vật thể động không thuộc lớp đã biết và so sánh với detector, đánh giá theo vận tốc và khoảng cách vật thể, agent tóm tắt cảnh và đề xuất frame cần gán nhãn bổ sung, benchmark tốc độ và bộ nhớ giữa các mô hình flow
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-11] FusionTrace - Đánh giá độ bền của fusion camera-LiDAR-radar và fusion theo thời gian khi cảm biến suy giảm hoặc lệch hiệu chuẩn

### 📝 Mô tả đề tài
📍 Thực trạng: Các mô hình fusion (BEVFusion, fusion theo thời gian) cho kết quả tốt khi mọi cảm biến hoạt động bình thường, nhưng khi một camera bị bẩn, LiDAR mất điểm trong mưa hoặc extrinsic lệch nhẹ thì hiệu năng có thể giảm mạnh và không ai biết sai ở cảm biến nào hay do khung thời gian nào.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng kiểm thử độ bền cho mô hình fusion: tự động tạo các kịch bản suy giảm (mất một camera, giảm mật độ LiDAR, nhiễu radar, lệch hiệu chuẩn, trễ đồng bộ thời gian, bỏ frame), chạy đánh giá, trực quan hóa mức đóng góp của từng cảm biến và của lịch sử thời gian, và để agent lập báo cáo điểm yếu cùng khuyến nghị cải thiện; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt kịch bản suy giảm và kết luận trước khi đưa vào báo cáo độ bền chính thức (human-in-the-loop); chỉ thực hiện trên dữ liệu công khai/đã ghi và mô phỏng, không can thiệp cảm biến trên xe thật; đo bằng mAP/NDS giảm theo từng mức suy giảm, tỷ lệ giữ hiệu năng so với baseline và độ ổn định theo thời gian; báo cáo phải nêu rõ giới hạn của các suy giảm tổng hợp so với suy giảm thực.

### 🛠️ Tech Stack
• Python, PyTorch
• BEVFusion/TransFusion/BEVFormer, mô hình temporal fusion (BEVDet4D/StreamPETR)
• nuScenes (có radar), Waymo Open, Argoverse 2
• thư viện corruption cho nuScenes/robustness benchmark
• Open3D
• LLM + LangGraph để lập báo cáo độ bền
• FastAPI backend
• React/Next.js (ma trận suy giảm, viewer BEV)
• MLflow/Weights & Biases
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app cấu hình ≥4 kịch bản suy giảm (mất camera, giảm LiDAR, lệch hiệu chuẩn, trễ đồng bộ), chạy đánh giá một mô hình fusion trên dữ liệu công khai, hiển thị ma trận suy giảm - mAP/NDS, ≥2 vai trò (kỹ sư và reviewer), HITL duyệt báo cáo độ bền.

Nâng cao:
• phân tích đóng góp của từng cảm biến và của số frame lịch sử (ablation tự động), phát hiện cảm biến suy giảm trực tuyến từ tín hiệu mô hình, agent đề xuất chiến lược dự phòng (fallback) và dữ liệu huấn luyện tăng cường, benchmark chi phí tính toán của các biến thể fusion
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-12] VisLoc VN - Định vị bằng thị giác (nhận diện địa điểm và tái định vị 6-DoF) trong đô thị khi thay đổi ngày/đêm, mùa và công trình

### 📝 Mô tả đề tài
📍 Thực trạng: Khi GNSS bị nhiễu hoặc mất tín hiệu (hầm chui, khu nhà cao tầng), xe cần định vị bằng hình ảnh so với bản đồ đã lập; nhưng cảnh đô thị thay đổi theo giờ, thời tiết, mùa, biển quảng cáo và công trình mới khiến việc nhận diện lại địa điểm sai hoặc thất bại, nhất là ban đêm.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng hệ thống định vị bằng thị giác hai tầng: (1) nhận diện địa điểm (visual place recognition) để truy xuất các ảnh tham chiếu gần nhất trong cơ sở dữ liệu bản đồ, (2) tái định vị 6-DoF bằng khớp đặc trưng cục bộ và PnP; kèm dashboard phân tích thất bại theo điều kiện (đêm, mưa, thay đổi cảnh) và agent giải thích nguyên nhân từng ca thất bại; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt các ca thất bại và ngưỡng chấp nhận kết quả định vị (human-in-the-loop); chỉ xử lý dữ liệu công khai hoặc đã ghi sẵn, ẩn danh khuôn mặt/biển số trước khi lưu trong cơ sở dữ liệu bản đồ; không dùng kết quả để điều khiển xe thật; đo bằng Recall@N của truy xuất, tỷ lệ định vị thành công theo ngưỡng (0.25m/2°, 0.5m/5°, 5m/10°), sai số trung vị về vị trí và góc; theo dõi độ trễ truy xuất và kích thước chỉ mục.

### 🛠️ Tech Stack
• Python, PyTorch
• NetVLAD/MixVPR/AnyLoc/DINOv2 cho nhận diện địa điểm
• SuperPoint + LightGlue/LoFTR, hloc (Hierarchical Localization) cho tái định vị
• Oxford RobotCar, Mapillary Street-level Sequences, Aachen Day-Night, nuScenes
• FAISS/Qdrant lập chỉ mục ảnh tham chiếu
• OpenCV, COLMAP
• LLM/VLM + LangGraph để giải thích ca thất bại
• FastAPI backend
• React/Next.js + bản đồ
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app lập chỉ mục tập ảnh tham chiếu công khai, nhận ảnh truy vấn và trả về top-N địa điểm cùng pose ước lượng, hiển thị trên bản đồ, báo cáo Recall@N và tỷ lệ định vị thành công, ≥2 vai trò (kỹ sư bản đồ và reviewer), HITL duyệt ngưỡng chấp nhận.

Nâng cao:
• phân tích thất bại theo ngày/đêm, mưa, thay đổi cảnh vật, agent gợi ý cách bổ sung ảnh tham chiếu, kết hợp truy xuất với bộ lọc thời gian/ràng buộc chuyển động, so sánh nhiều mô hình VPR, đo độ trễ - bộ nhớ chỉ mục theo quy mô và đề xuất nén chỉ mục
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-13] LiDAR Loc Bench - Định vị LiDAR trên bản đồ điểm (scan-to-map) và phát hiện suy biến, trôi lệch và mất định vị

### 📝 Mô tả đề tài
📍 Thực trạng: Định vị bằng LiDAR cho độ chính xác cao nhưng dễ hỏng ở nơi hình học nghèo nàn (đường hầm dài, đường cao tốc thẳng, bãi đỗ trống), khi có nhiều vật thể động hoặc khi bản đồ đã lỗi thời; kỹ sư khó biết hệ thống đang suy biến trước khi sai số tích lũy lớn.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng benchmark các thuật toán LiDAR odometry/localization (scan-to-scan, scan-to-map) trên cùng dữ liệu, tính sai số quỹ đạo, phát hiện đoạn suy biến hình học (degeneracy) và trôi lệch, trực quan hóa quỹ đạo trên bản đồ điểm và để agent tóm tắt các đoạn có nguy cơ mất định vị cùng nguyên nhân khả dĩ; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt các đoạn bị gắn cờ suy biến trước khi dùng làm kết luận đánh giá (human-in-the-loop); chỉ xử lý dữ liệu công khai/đã ghi, không đưa vào điều khiển thật; so sánh các thuật toán phải cùng cấu hình dữ liệu và ghi rõ tham số; đo bằng ATE, RPE, tỷ lệ mất định vị và độ trễ/FPS; kiểm soát bộ nhớ khi bản đồ lớn; ẩn danh PII nếu có ảnh đi kèm.

### 🛠️ Tech Stack
• Python/C++ (ROS2)
• KISS-ICP, FAST-LIO2, LIO-SAM, NDT/GICP (Open3D, small_gicp)
• evo để tính ATE/RPE
• KITTI Odometry, MulRan, Newer College, nuScenes, Argoverse 2 LiDAR
• Open3D/PCL, rosbag2/MCAP
• LLM + LangGraph để tóm tắt đoạn rủi ro
• FastAPI backend
• React/Next.js + three.js
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app chạy ≥2 thuật toán LiDAR odometry trên chuỗi công khai, vẽ quỹ đạo so với ground truth, báo cáo ATE/RPE, đánh dấu đoạn sai số lớn, ≥2 vai trò (kỹ sư định vị và reviewer), HITL duyệt kết luận.

Nâng cao:
• phát hiện suy biến hình học bằng phân tích giá trị riêng của ma trận thông tin/độ nhạy ICP, cảnh báo sớm mất định vị, kiểm thử với vật thể động và bản đồ lỗi thời, agent đề xuất cấu hình (voxel size, lọc vật thể động) cho từng môi trường, benchmark FPS và bộ nhớ theo quy mô bản đồ
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-14] VIO Studio - Gỡ lỗi và benchmark visual-inertial odometry (VIO) với phân tích nguyên nhân mất bám

### 📝 Mô tả đề tài
📍 Thực trạng: VIO kết hợp camera và IMU để ước lượng chuyển động, nhưng dễ mất bám khi ảnh mờ do rung, cảnh thiếu kết cấu, chói sáng, rolling shutter, hoặc khi IMU bias/đồng bộ thời gian sai; log của các hệ thống VIO rất dày và kỹ sư thường mất nhiều giờ đọc thủ công để tìm nguyên nhân.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ chạy và so sánh các hệ thống VIO mã nguồn mở trên cùng dữ liệu, thu thập chỉ số nội bộ (số đặc trưng, tỷ lệ inlier, bias IMU, residual), trực quan hóa timeline chất lượng bám, đánh dấu thời điểm suy giảm và dùng agent đọc log + video để chẩn đoán nguyên nhân (mờ, thiếu kết cấu, IMU, đồng bộ) kèm khuyến nghị tham số; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt chẩn đoán của agent trước khi đổi cấu hình hay kết luận benchmark (human-in-the-loop); chỉ chạy offline trên dữ liệu công khai/đã ghi, không điều khiển xe/robot thật; mọi chẩn đoán phải trỏ về số liệu log và frame minh chứng; đo bằng ATE, RPE, tỷ lệ mất bám, độ chính xác chẩn đoán so với nguyên nhân ground truth trên các ca gây lỗi tổng hợp; ẩn danh PII.

### 🛠️ Tech Stack
• Python/C++ (ROS2)
• OpenVINS, VINS-Fusion, ORB-SLAM3 (chế độ visual-inertial), Basalt
• evo để tính ATE/RPE
• EuRoC, TUM-VI, KITTI (kèm IMU), nuScenes
• OpenCV, rosbag2/MCAP
• LLM/VLM + LangGraph đọc log và video
• FastAPI backend
• React/Next.js (timeline chất lượng + quỹ đạo)
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app chạy ≥2 hệ thống VIO trên chuỗi công khai, vẽ quỹ đạo, timeline số đặc trưng/inlier, báo cáo ATE/RPE và số lần mất bám, ≥2 vai trò (kỹ sư và reviewer), HITL duyệt chẩn đoán.

Nâng cao:
• tạo ca gây lỗi tổng hợp có kiểm soát (làm mờ ảnh, giảm kết cấu, thêm nhiễu IMU, lệch thời gian) để đo độ chính xác chẩn đoán của agent, đề xuất tham số cho từng nguyên nhân, đánh giá độ nhạy với hiệu chuẩn camera-IMU, benchmark CPU/độ trễ trên phần cứng nhúng
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-15] Multi-Session Mapper - Dựng và hợp nhất bản đồ đa chuyến (multi-session SLAM) từ log của nhiều xe/nhiều ngày

### 📝 Mô tả đề tài
📍 Thực trạng: Một chuyến đi chỉ phủ một phần đường và ở một điều kiện nhất định; để có bản đồ đầy đủ và cập nhật cần hợp nhất log của nhiều chuyến, nhiều xe, nhiều ngày, nhưng việc nối bản đồ dễ sai (loop closure giả, trôi lệch, chồng lấn) và khó kiểm soát chất lượng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng pipeline dựng bản đồ từ nhiều chuỗi log: odometry từng chuyến, phát hiện loop closure giữa các chuyến, tối ưu pose graph toàn cục, hợp nhất thành bản đồ thống nhất; có giao diện xem từng chuyến, các cạnh loop closure và độ nhất quán bản đồ; agent đánh dấu các loop closure nghi ngờ để kỹ sư duyệt; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư phải duyệt các loop closure nghi ngờ trước khi hợp nhất vào bản đồ chính thức (human-in-the-loop); chỉ dùng dữ liệu công khai/đã ghi và ẩn danh PII; giữ bản đồ có phiên bản để quay lui; đo bằng precision/recall của loop closure, sai số nhất quán giữa các chuyến (ATE sau căn chỉnh), độ phủ bản đồ và thời gian tối ưu; kiểm soát chi phí tính toán khi số chuyến tăng.

### 🛠️ Tech Stack
• Python/C++
• GTSAM hoặc g2o cho pose graph optimization
• Scan Context/ISC hoặc MixVPR/NetVLAD cho nhận diện loop
• KISS-ICP/LIO-SAM/ORB-SLAM3 làm odometry
• MulRan, KITTI-360, Oxford RobotCar, nuScenes (nhiều scene cùng khu vực)
• Open3D, evo
• FastAPI backend
• React/Next.js + three.js
• DVC để versioning bản đồ
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp ≥2 chuỗi log công khai cùng khu vực, phát hiện loop closure giữa chuyến, tối ưu và hợp nhất bản đồ, hiển thị các cạnh loop, báo cáo precision/recall loop và sai số nhất quán, ≥2 vai trò (kỹ sư bản đồ và reviewer), HITL duyệt loop closure.

Nâng cao:
• lọc loop closure sai bằng kiểm tra nhất quán hình học và robust optimization (switchable constraints/GNC), agent xếp hạng cạnh nghi ngờ, hợp nhất tăng dần khi có thêm chuyến mới, quản lý phiên bản bản đồ và đo chi phí tối ưu theo số chuyến
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-16] OnlineMap Lab - Dựng bản đồ vector trực tuyến (online HD map construction) từ camera/LiDAR và đánh giá cấu trúc topology

### 📝 Mô tả đề tài
📍 Thực trạng: HD map truyền thống rất đắt để lập và duy trì; xu hướng mới là xe tự dựng bản đồ vector (vạch kẻ, ranh giới đường, vạch qua đường, quan hệ làn) từ cảm biến trong lúc chạy. Tuy nhiên mô hình thường đúng về hình học nhưng sai về topology (làn nào nối làn nào), vốn là điều chức năng lập kế hoạch cần nhất.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng chạy và đánh giá mô hình online map construction: sinh phần tử bản đồ vector trong hệ BEV, so sánh với bản đồ tham chiếu, đánh giá cả độ chính xác hình học lẫn topology (kết nối làn, quan hệ làn - phần tử giao thông), trực quan hóa lỗi và để agent tóm tắt kiểu lỗi phổ biến theo loại giao lộ/điều kiện; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt phân loại lỗi và kết luận so sánh mô hình (human-in-the-loop); chỉ chạy offline trên dữ liệu công khai/đã ghi, không đưa bản đồ dự đoán vào điều khiển thật; đo bằng mAP theo khoảng cách Chamfer cho từng lớp phần tử, chỉ số topology (TOP/OLS của OpenLane-V2) và độ ổn định theo thời gian giữa các frame; theo dõi độ trễ suy luận; ẩn danh PII.

### 🛠️ Tech Stack
• Python, PyTorch
• MapTR/MapTRv2, VectorMapNet, HDMapNet, TopoNet/LaneSegNet (topology)
• nuScenes + map expansion, Argoverse 2 Map Change/Sensor, OpenLane-V2
• Shapely để tính Chamfer/IoU hình học
• networkx để đánh giá đồ thị topology
• LLM + LangGraph tóm tắt lỗi
• FastAPI backend
• React/Next.js (viewer bản đồ vector BEV)
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app chạy một mô hình online map trên dữ liệu công khai, hiển thị bản đồ vector dự đoán và tham chiếu, báo cáo mAP theo Chamfer và chỉ số topology, ≥2 vai trò (kỹ sư và reviewer), HITL duyệt phân loại lỗi.

Nâng cao:
• phân tích lỗi topology theo loại giao lộ (ngã ba, vòng xoay, đường nhập làn), đánh giá độ ổn định theo thời gian và hợp nhất bản đồ qua các frame, so sánh ≥2 mô hình, agent đề xuất loại dữ liệu cần thêm, benchmark độ trễ và bộ nhớ
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-17] HDMap Auditor - Kiểm định chất lượng và tính nhất quán của HD map (Lanelet2/OpenDRIVE) bằng quy tắc và agent

### 📝 Mô tả đề tài
📍 Thực trạng: HD map được dựng từ nhiều nguồn và nhiều lần chỉnh sửa nên dễ có lỗi: làn không nối, hướng làn sai, vạch kẻ lệch so với ảnh thực, quy tắc ưu tiên mâu thuẫn, tốc độ giới hạn thiếu; những lỗi này thường chỉ bị phát hiện khi xe chạy thử, rất tốn kém.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ kiểm định tự động cho tệp HD map (Lanelet2/OpenDRIVE): bộ quy tắc kiểm tra hình học và topology (làn đứt, giao cắt bất thường, hướng đi, kết nối giao lộ, thuộc tính thiếu), đối chiếu với ảnh/LiDAR đã ghi, hiển thị lỗi trên bản đồ và agent giải thích từng lỗi bằng ngôn ngữ tự nhiên, đề xuất cách sửa; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: bản sửa do agent đề xuất chỉ được áp dụng sau khi kỹ sư bản đồ duyệt (human-in-the-loop), mọi thay đổi có lịch sử và quay lui được; chỉ dùng bản đồ mẫu công khai hoặc mô phỏng, không dùng bản đồ độc quyền thật; đo bằng precision/recall của việc phát hiện lỗi trên bản đồ được chèn lỗi có chủ đích, tỷ lệ gợi ý sửa đúng, và thời gian kiểm định tiết kiệm so với làm tay.

### 🛠️ Tech Stack
• Python/C++
• Lanelet2 và thư viện kiểm tra, esmini/pyOpenDRIVE/ASAM OpenDRIVE parser
• bản đồ mẫu từ Lanelet2 examples, Argoverse 2 maps, CARLA OpenDRIVE, OpenStreetMap
• Shapely/GeoPandas, networkx
• LLM + LangGraph, structured output
• FastAPI backend
• React/Next.js + Leaflet/Deck.gl
• PostgreSQL/PostGIS để lưu lịch sử thay đổi
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp một bản đồ mẫu, chạy bộ quy tắc kiểm tra, hiển thị lỗi trên bản đồ theo mức độ, agent giải thích lỗi, báo cáo số lỗi theo loại, ≥2 vai trò (kỹ sư bản đồ và người duyệt), HITL duyệt đề xuất sửa.

Nâng cao:
• chèn lỗi có chủ đích để đo precision/recall, đối chiếu bản đồ với ảnh/LiDAR để phát hiện lệch hình học, agent đề xuất và áp dụng bản sửa có kiểm tra lại sau khi sửa, quản lý phiên bản bản đồ và audit log, benchmark thời gian kiểm định trên bản đồ lớn
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-18] ChangeTriage - Phân loại và ưu tiên sự kiện thay đổi bản đồ (công trường, vạch/biển mới, làn tạm) để giảm cảnh báo giả

### 📝 Mô tả đề tài
📍 Thực trạng: Khi đội xe gửi về tín hiệu 'bản đồ khác thực tế', phần lớn là cảnh báo giả (xe che, thời tiết, lỗi định vị) hoặc thay đổi tạm thời; đội bản đồ bị ngập trong hàng nghìn sự kiện, khó biết sự kiện nào thật sự ảnh hưởng an toàn và cần cập nhật bản đồ trước.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng hệ thống tiếp nhận các sự kiện nghi ngờ thay đổi bản đồ (từ so sánh perception với bản đồ), gom nhóm các sự kiện lặp lại từ nhiều chuyến, phân loại (vĩnh viễn, tạm thời như công trường, cảnh báo giả), chấm điểm mức ưu tiên theo tác động an toàn và độ tin cậy, tạo hàng đợi duyệt cho kỹ sư với bằng chứng ảnh/point cloud; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư bản đồ phải duyệt trước khi bất kỳ thay đổi nào được ghi nhận vào bản đồ (human-in-the-loop), hệ thống không tự sửa bản đồ; chỉ dùng dữ liệu công khai/mô phỏng/đã ghi, ẩn danh PII; đo bằng precision/recall phân loại thay đổi thật, tỷ lệ giảm cảnh báo giả, độ chính xác xếp hạng ưu tiên và thời gian duyệt trung bình mỗi sự kiện; tránh bỏ sót thay đổi nguy hiểm hơn là giảm cảnh báo giả.

### 🛠️ Tech Stack
• Python, PyTorch
• Argoverse 2 Map Change Detection dataset, nuScenes + map expansion, dữ liệu mô phỏng CARLA có chỉnh sửa bản đồ
• so khớp perception - bản đồ (Shapely, networkx)
• DBSCAN/HDBSCAN và embedding để gom sự kiện
• LLM/VLM + LangGraph để mô tả và phân loại
• PostgreSQL/PostGIS
• FastAPI backend
• React/Next.js + bản đồ
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp bộ sự kiện thay đổi mẫu, gom nhóm sự kiện, phân loại thật/tạm thời/giả, hàng đợi duyệt xếp theo ưu tiên, báo cáo precision/recall và mức giảm cảnh báo giả, ≥2 vai trò (kỹ sư bản đồ và quản lý), HITL duyệt thay đổi.

Nâng cao:
• hợp nhất bằng chứng nhiều chuyến để tăng độ tin cậy, mô hình hóa vòng đời thay đổi tạm thời (công trường mở/đóng), agent tóm tắt sự kiện với bằng chứng, huấn luyện mô hình xếp ưu tiên theo tác động an toàn, đo thời gian xử lý hàng đợi theo quy mô
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-19] MapLite Drive - Định vị và hiểu đường theo hướng 'map-light': bản đồ SD/OpenStreetMap kết hợp perception trực tuyến thay cho HD map

### 📝 Mô tả đề tài
📍 Thực trạng: HD map cho độ chính xác cao nhưng chi phí lập và cập nhật lớn, khó mở rộng toàn quốc; hướng 'map-light' dùng bản đồ thường (SD map như OpenStreetMap) làm tiên nghiệm, kết hợp perception trực tuyến để suy ra cấu trúc làn, nhưng chưa rõ mất bao nhiêu độ chính xác và khi nào cần quay về HD map.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng hệ thống map-light: dùng đồ thị đường từ OpenStreetMap làm tiên nghiệm, kết hợp mô hình perception trực tuyến để ước lượng làn và vị trí so với đường, so sánh với phương án dùng HD map đầy đủ, định lượng đánh đổi độ chính xác - chi phí, và agent chỉ ra những loại đoạn đường (giao lộ phức tạp, vòng xoay, đường hẻm) cần HD map; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt kết luận về ngưỡng 'đoạn đường nào đủ dùng map-light' (human-in-the-loop); chỉ chạy offline trên dữ liệu công khai/đã ghi hoặc mô phỏng, không điều khiển xe thật; tuân thủ giấy phép ODbL của OpenStreetMap; đo bằng sai số định vị ngang/dọc, độ chính xác topology làn, tỷ lệ đoạn đường đạt yêu cầu và chi phí lập bản đồ ước tính so với HD map.

### 🛠️ Tech Stack
• Python, PyTorch
• OpenStreetMap (osmnx, OSRM/Valhalla), SD map prior
• mô hình online map có SD prior (SMERF, P-MapNet hoặc biến thể tự huấn luyện)
• nuScenes, Argoverse 2 + OSM tương ứng
• bộ lọc Kalman/particle filter map-matching
• Shapely/GeoPandas
• LLM + LangGraph để phân tích đoạn đường
• FastAPI backend
• React/Next.js + Leaflet
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp chuỗi dữ liệu công khai kèm đoạn OSM, thực hiện map-matching và dựng làn với SD prior, so sánh với phương án HD map, báo cáo sai số định vị và topology, ≥2 vai trò (kỹ sư bản đồ và reviewer), HITL duyệt kết luận.

Nâng cao:
• phân loại đoạn đường theo độ phù hợp map-light, mô hình hóa đánh đổi chi phí - chất lượng trên nhiều đoạn, agent đề xuất đoạn cần ưu tiên lập HD map, đánh giá độ bền khi OSM lỗi/thiếu, benchmark độ trễ suy luận
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-20] SensorSim Lab - Mô phỏng cảm biến camera/LiDAR/radar với mô hình nhiễu thực tế và hiệu chỉnh tham số theo dữ liệu thật

### 📝 Mô tả đề tài
📍 Thực trạng: Cảm biến mô phỏng mặc định thường 'quá sạch': LiDAR không rơi điểm khi mưa, camera không có nhiễu/rolling shutter/chói sáng, radar không có ghost target; vì vậy perception huấn luyện hoặc kiểm thử trên mô phỏng cho kết quả lạc quan hơn thực tế và không ai biết nên chỉnh tham số mô phỏng ra sao cho khớp.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ cấu hình mô hình cảm biến trong mô phỏng (nhiễu ảnh, rolling shutter, vignetting, độ phân giải/độ trễ; LiDAR dropout, nhiễu khoảng cách, giảm cường độ khi mưa/sương; radar clutter) và hiệu chỉnh tham số tự động sao cho thống kê dữ liệu mô phỏng khớp với dữ liệu thật đã ghi; agent đề xuất và chạy các vòng chỉnh tham số; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt bộ tham số cuối cùng trước khi dùng cho đánh giá chính thức (human-in-the-loop); chỉ chạy trên mô phỏng và dữ liệu thật đã ghi, ẩn danh PII; mức khớp phải đo được (khoảng cách phân bố cường độ/mật độ điểm/histogram nhiễu như MMD hoặc Wasserstein, và độ chênh AP của cùng một detector giữa sim và thật); theo dõi chi phí GPU mỗi vòng hiệu chỉnh; nêu rõ giới hạn của mô hình nhiễu.

### 🛠️ Tech Stack
• Python, PyTorch
• CARLA hoặc Isaac Sim (camera/LiDAR/radar sensor API)
• dữ liệu thật nuScenes/Waymo Open/KITTI làm tham chiếu
• Optuna/Bayesian optimization cho hiệu chỉnh tham số
• MMD/Wasserstein trong scikit-learn/POT
• Open3D, OpenCV
• LLM + LangGraph điều phối vòng hiệu chỉnh
• FastAPI backend
• React/Next.js
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app cấu hình mô hình nhiễu cho ≥2 loại cảm biến, sinh dữ liệu từ CARLA/Isaac, so sánh thống kê với dữ liệu thật mẫu, báo cáo chỉ số khớp trước/sau hiệu chỉnh, ≥2 vai trò (kỹ sư mô phỏng và reviewer), HITL duyệt bộ tham số.

Nâng cao:
• agent tự chạy vòng hiệu chỉnh (đề xuất tham số - sinh dữ liệu - đo khớp), mở rộng ra mưa/sương/đêm, đo độ chênh AP của detector giữa sim đã hiệu chỉnh và dữ liệu thật, phân tích độ nhạy từng tham số, benchmark chi phí GPU và tốc độ sinh dữ liệu
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-21] VehicleTwin - Mô hình hóa động lực học xe và hiệu chỉnh tham số xe từ log CAN để mô phỏng sát thực tế

### 📝 Mô tả đề tài
📍 Thực trạng: Kết quả mô phỏng closed-loop chỉ đáng tin khi mô hình xe phản ứng giống xe thật (độ trễ phanh/lái, tăng tốc, độ trượt); nhưng tham số xe thường là giá trị mặc định hoặc ước tính thô, làm xe mô phỏng phanh và vào cua khác xe thật, dẫn tới đánh giá sai về an toàn và độ êm.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ nhận dạng tham số mô hình động lực học xe (mô hình xe đạp, độ trễ chấp hành, đáp ứng phanh/ga/lái) từ log điều khiển và trạng thái xe đã ghi, tích hợp mô hình vào mô phỏng, so sánh phản ứng mô phỏng và log thật trên các thao tác (phanh gấp, đánh lái, tăng tốc) và agent chỉ ra vùng vận hành nơi mô hình sai nhiều nhất; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư dynamics phải duyệt tham số đã nhận dạng và vùng hợp lệ (envelope) của mô hình trước khi dùng cho đánh giá (human-in-the-loop); chỉ dùng log công khai hoặc dữ liệu mô phỏng, không điều khiển xe thật; mức khớp đo bằng RMSE của tốc độ/gia tốc/góc yaw rate trên tập validation giữ riêng; phải nêu rõ giới hạn khi ngoại suy ra ngoài vùng dữ liệu (tốc độ cao, mặt đường trơn).

### 🛠️ Tech Stack
• Python
• CasADi/SciPy/PyTorch cho nhận dạng tham số (system identification)
• mô hình xe: kinematic/dynamic bicycle, tire model (Pacejka đơn giản)
• comma2k19 (CAN + GNSS/IMU công khai), nuScenes CAN bus, dữ liệu CARLA
• CARLA vehicle physics/PythonAPI hoặc Autoware simulator
• python-can để đọc log CAN
• FastAPI backend
• React/Next.js (biểu đồ so sánh sim vs log)
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp log điều khiển - trạng thái xe mẫu, nhận dạng tham số mô hình xe đạp, chạy mô phỏng phát lại cùng lệnh điều khiển, vẽ so sánh với log và báo cáo RMSE, ≥2 vai trò (kỹ sư dynamics và reviewer), HITL duyệt tham số.

Nâng cao:
• mô hình hóa độ trễ chấp hành và phi tuyến lốp, xác định envelope hợp lệ của mô hình, agent phát hiện vùng vận hành sai nhiều và đề xuất thao tác cần thu thêm dữ liệu, so sánh mô hình đơn giản và phức tạp bằng cross-validation, tích hợp mô hình vào CARLA và đo ảnh hưởng tới kết quả test
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-22] VN Traffic Sim - Mô phỏng giao thông hỗn hợp nhiều xe máy kiểu Việt Nam và hiệu chỉnh hành vi theo video thực

### 📝 Mô tả đề tài
📍 Thực trạng: Các bộ mô phỏng giao thông phổ biến mô hình hóa ô tô đi theo làn; giao thông Việt Nam có hàng chục xe máy luồn lách, đi sát nhau, không theo làn rõ ràng, hành vi của người đi bộ khó đoán; kịch bản kiểm thử ADAS dựa trên hành vi 'sạch' nên bỏ sót các tình huống thực tế phổ biến.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ mô phỏng giao thông hỗn hợp: cấu hình mô hình hành vi xe máy/ô tô/người đi bộ (khoảng cách ngang, khoảng cách thời gian, tốc độ), hiệu chỉnh tham số hành vi từ quỹ đạo trích xuất từ video thực công khai/đã ghi, so sánh phân bố hành vi mô phỏng với dữ liệu thật và cho phép xuất cảnh giao thông sang CARLA để kiểm thử ADAS; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt tham số hành vi và kết luận về độ thực của mô phỏng (human-in-the-loop); video thực phải ẩn danh khuôn mặt/biển số và chỉ dùng dữ liệu công khai hoặc đã được phép; mức thực đo bằng khoảng cách phân bố (Jensen-Shannon/Wasserstein) của khoảng cách ngang, khoảng cách thời gian, tốc độ và tỷ lệ va chạm/near-miss so với dữ liệu thật; kiểm soát thời gian chạy khi số tác nhân lớn.

### 🛠️ Tech Stack
• Python
• SUMO (sublane model, mô hình xe máy) hoặc MetaDrive/CARLA traffic manager
• trích xuất quỹ đạo từ video: YOLO + tracker (ByteTrack), homography về mặt phẳng đường
• dữ liệu video giao thông công khai, drone dataset (inD/rounD để tham khảo phương pháp)
• Optuna để hiệu chỉnh tham số hành vi
• LLM + LangGraph để mô tả/tinh chỉnh kịch bản
• FastAPI backend
• React/Next.js
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp quỹ đạo trích từ ≥1 video công khai, hiệu chỉnh tham số hành vi cho SUMO/mô phỏng, so sánh phân bố khoảng cách ngang và tốc độ giữa sim và thật, ≥2 vai trò (kỹ sư mô phỏng và reviewer), HITL duyệt tham số.

Nâng cao:
• mô hình hóa riêng hành vi xe máy luồn lách và người đi bộ băng ngang tùy tiện, hiệu chỉnh tự động bằng tối ưu, xuất cảnh sang CARLA để chạy thử ADAS, đo ảnh hưởng của độ thực lên tỷ lệ near-miss phát hiện được, benchmark hiệu năng theo số tác nhân
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-23] WeatherForge - Mô phỏng điều kiện môi trường (mưa, sương, nắng gắt, đêm, mặt đường ướt) và ma trận phủ ODD cho kiểm thử perception

### 📝 Mô tả đề tài
📍 Thực trạng: Perception thường được kiểm thử chủ yếu trong thời tiết đẹp vì dữ liệu mưa/sương/đêm khó thu thập có kiểm soát; còn khi mô phỏng thì điều kiện môi trường thường chỉnh thủ công, không có ma trận rõ ràng cho biết các tổ hợp điều kiện (ODD) đã được kiểm thử đủ chưa.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ sinh điều kiện môi trường có kiểm soát (cường độ mưa, độ dày sương, góc mặt trời/chói, ban đêm, mặt đường ướt phản chiếu) trong mô phỏng hoặc bằng biến đổi ảnh có điều kiện, chạy perception qua ma trận điều kiện, hiển thị độ phủ ODD và độ giảm hiệu năng theo từng ô, và để agent đề xuất các tổ hợp điều kiện chưa được kiểm thử; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt định nghĩa ODD và ngưỡng chấp nhận hiệu năng (human-in-the-loop); chỉ chạy trên mô phỏng và dữ liệu công khai, không dùng ảnh biến đổi như thể là dữ liệu thật khi báo cáo; độ thực của ảnh sinh đo bằng FID/KID hoặc so với ảnh thật cùng điều kiện, kèm độ giảm AP của detector; phải ghi rõ giới hạn của phương pháp sinh; kiểm soát chi phí GPU khi sinh dữ liệu hàng loạt.

### 🛠️ Tech Stack
• Python, PyTorch
• CARLA weather/lighting API hoặc Isaac Sim
• image-to-image/diffusion có điều kiện để thêm sương/mưa/đêm (có kiểm soát)
• ACDC, BDD100K, nuScenes (cảnh mưa/đêm) làm tham chiếu thực
• detector mẫu (YOLO/RT-DETR)
• clean-fid/torchmetrics để tính FID/KID
• FastAPI backend
• React/Next.js (ma trận ODD dạng heatmap)
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app định nghĩa ma trận điều kiện (≥3 chiều: ánh sáng, mưa/sương, mặt đường), sinh dữ liệu từ mô phỏng, chạy một detector, heatmap AP theo ô điều kiện và độ phủ ODD, ≥2 vai trò (kỹ sư và reviewer), HITL duyệt ngưỡng chấp nhận.

Nâng cao:
• agent đề xuất tổ hợp điều kiện chưa phủ và tự sinh dữ liệu kiểm thử bổ sung, đánh giá độ thực của ảnh sinh (FID/KID, so với ảnh thật), phân tích loại lỗi tăng mạnh nhất theo điều kiện, đo chi phí - thời gian sinh trên mỗi ô điều kiện
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-24] ScenarioMiner - Khai thác kịch bản từ log lái thực và chuyển thành kịch bản OpenSCENARIO tham số hóa

### 📝 Mô tả đề tài
📍 Thực trạng: Kịch bản kiểm thử viết tay tốn công và dễ lệch khỏi thực tế, trong khi log lái thực chứa vô số tình huống thật (xe cắt ngang, phanh gấp, người đi bộ băng đường); nhưng log thô khó tái sử dụng vì không có công cụ trích đúng đoạn tình huống và chuyển nó thành kịch bản chạy được, thay đổi được tham số.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng pipeline trích xuất tình huống từ log (cut-in, phanh gấp, xe đi ngược chiều, người đi bộ băng ngang) bằng bộ phát hiện luật + mô hình, chuẩn hóa thành kịch bản logic có tham số (tốc độ, khoảng cách, thời gian), sinh kịch bản cụ thể bằng cách quét tham số, xuất sang OpenSCENARIO để chạy trong mô phỏng, kèm thư viện kịch bản có tìm kiếm; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt kịch bản trích ra và khoảng tham số trước khi vào bộ kiểm thử chính thức (human-in-the-loop); chỉ dùng log công khai/đã ghi, ẩn danh PII, kịch bản chỉ chạy trên mô phỏng; đo bằng precision/recall của việc phát hiện tình huống so với nhãn tay, tỷ lệ kịch bản xuất ra chạy hợp lệ trong mô phỏng, độ khớp giữa kịch bản tái hiện và log gốc (sai số quỹ đạo) và độ đa dạng của bộ kịch bản.

### 🛠️ Tech Stack
• Python
• nuScenes, Waymo Open Motion, Argoverse 2 Motion, nuPlan (log và bản đồ)
• ASAM OpenSCENARIO XML/DSL, esmini hoặc CARLA ScenarioRunner
• Scenic để mô tả kịch bản xác suất (tùy chọn)
• scikit-learn/HDBSCAN để gom nhóm tình huống
• LLM + LangGraph hỗ trợ gán nhãn tình huống và sinh mô tả
• Qdrant/pgvector để tìm kiếm kịch bản
• FastAPI backend
• React/Next.js
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp một tập log công khai, phát hiện ≥3 loại tình huống, xuất kịch bản OpenSCENARIO chạy được trong esmini/CARLA, thư viện kịch bản có tag và tìm kiếm, báo cáo precision/recall phát hiện, ≥2 vai trò (kỹ sư kịch bản và người duyệt), HITL phê duyệt kịch bản.

Nâng cao:
• tham số hóa tự động và quét tham số để sinh kịch bản cụ thể từ kịch bản logic, đo độ khớp tái hiện với log gốc, gom nhóm và loại trùng lặp để tối đa độ đa dạng, agent mô tả tình huống và gợi ý khoảng tham số nguy hiểm, benchmark thời gian xử lý theo số log
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-25] CriticalScenario Search - Tìm kịch bản nguy hiểm cho bộ lập kế hoạch bằng tối ưu hóa và tìm kiếm đối kháng trong mô phỏng

### 📝 Mô tả đề tài
📍 Thực trạng: Duyệt ngẫu nhiên không gian kịch bản rất tốn kém vì phần lớn kịch bản đều an toàn; lỗi quan trọng lại nằm ở những tổ hợp tham số hiếm (xe cắt ngang đúng thời điểm, người đi bộ xuất hiện sau xe đỗ), đòi hỏi phương pháp tìm kiếm có định hướng để phát hiện lỗi với ngân sách mô phỏng hạn chế.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng công cụ tìm kiếm kịch bản nguy hiểm: định nghĩa không gian tham số kịch bản, dùng tối ưu Bayes/thuật toán tiến hóa/RL đối kháng để tìm tổ hợp làm bộ lập kế hoạch hoặc hệ thống ADAS thất bại (va chạm, near-miss, vi phạm), kiểm tra tính hợp lý (plausibility) của kịch bản tìm được và đóng gói thành ca kiểm thử hồi quy kèm báo cáo; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt kịch bản nguy hiểm tìm được (có hợp lý/có thể xảy ra ngoài đời không) trước khi đưa vào bộ test (human-in-the-loop); mọi thử nghiệm chỉ chạy trên mô phỏng, tuyệt đối không thực hiện trên xe thật; đo bằng số lỗi phát hiện được trên mỗi 100 lần mô phỏng so với lấy mẫu ngẫu nhiên, độ đa dạng của lỗi tìm được, tỷ lệ kịch bản hợp lý và chi phí mô phỏng; phải loại các lỗi do kịch bản không thể tránh (unavoidable collision).

### 🛠️ Tech Stack
• Python
• CARLA/MetaDrive/Waymax làm môi trường mô phỏng
• bộ lập kế hoạch/AV stack mẫu (IDM, rule-based, Autoware/Apollo bản mô phỏng hoặc policy học được)
• Optuna/BoTorch (Bayesian optimization), DEAP/pymoo (tiến hóa), Stable-Baselines3 (RL)
• kiểm tra hợp lý: giới hạn gia tốc/hành vi hợp lý của tác nhân
• LLM + LangGraph mô tả kịch bản tìm được
• FastAPI backend
• React/Next.js
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app định nghĩa không gian tham số cho ≥1 loại kịch bản, chạy tìm kiếm Bayes hoặc tiến hóa trong mô phỏng, liệt kê kịch bản gây thất bại kèm video phát lại, so sánh với lấy mẫu ngẫu nhiên, ≥2 vai trò (kỹ sư kiểm thử và người duyệt), HITL duyệt kịch bản.

Nâng cao:
• tìm kiếm đa mục tiêu (mức nguy hiểm, độ hợp lý, độ đa dạng), loại tự động lỗi không thể tránh, gom nhóm lỗi tìm được thành họ lỗi, agent mô tả nguyên nhân khả dĩ, tự đóng gói thành bộ hồi quy và đo tốc độ phát hiện lỗi theo ngân sách mô phỏng
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-26] RouteTwin - Digital twin tuyến đường thử dựng từ bản đồ OSM, ảnh vệ tinh và dữ liệu GNSS, có đối chiếu twin với thực tế

### 📝 Mô tả đề tài
📍 Thực trạng: Kiểm thử ADAS trên đường thật mất thời gian và có rủi ro, nhưng tuyến đường mô phỏng thường là bản đồ chung chung, không phản ánh các tuyến cụ thể mà xe sẽ chạy; việc dựng digital twin của một tuyến thử từ dữ liệu địa lý sẵn có thường làm thủ công, không có kiểm chứng twin khớp thực tế đến đâu.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng pipeline dựng digital twin cho một tuyến đường: lấy hình học đường từ OpenStreetMap, tinh chỉnh bằng ảnh vệ tinh/dữ liệu GNSS đã ghi, sinh bản đồ OpenDRIVE và cảnh 3D cơ bản dùng được trong CARLA, rồi đối chiếu twin với thực tế (độ dài, độ cong, độ dốc, số giao lộ, vị trí biển/đèn) và nêu các sai khác để kỹ sư chỉnh; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt twin trước khi dùng cho đánh giá, đặc biệt các sai khác lớn được đánh dấu (human-in-the-loop); chỉ dùng dữ liệu địa lý công khai và dữ liệu GNSS đã ẩn danh/đã được phép, tuân thủ giấy phép OSM; độ khớp đo bằng sai số hình học trung bình (m), sai khác độ cong/độ dốc, tỷ lệ phần tử giao thông khớp; không dùng twin để suy ra kết luận an toàn trên đường thật khi chưa kiểm chứng.

### 🛠️ Tech Stack
• Python
• OpenStreetMap (osmnx), osm2xodr/netconvert (SUMO) hoặc RoadRunner/Blender để sinh OpenDRIVE
• CARLA (nhập OpenDRIVE + dựng cảnh), Unreal Engine/Blender
• GeoPandas/Shapely/rasterio
• dữ liệu GNSS công khai (comma2k19, nuScenes ego pose) để đối chiếu
• LLM + LangGraph để tóm tắt sai khác
• FastAPI backend
• React/Next.js + bản đồ
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu định vị & bản đồ KITTI Odometry, Argoverse 2 Map Change, NuPlan / Lanelet2 / ASAM OpenDRIVE và OpenStreetMap.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nhập vùng/tuyến trên bản đồ, sinh OpenDRIVE và nạp vào CARLA, đối chiếu twin với dữ liệu GNSS mẫu, báo cáo độ dài/độ cong/sai số hình học, ≥2 vai trò (kỹ sư mô phỏng và reviewer), HITL duyệt twin.

Nâng cao:
• tinh chỉnh hình học bằng dữ liệu GNSS/LiDAR, thêm biển báo/đèn/vạch từ nguồn dữ liệu có sẵn, tính điểm 'độ trung thực twin' theo từng đoạn, agent chỉ ra đoạn cần chỉnh thủ công, benchmark thời gian dựng twin theo chiều dài tuyến
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-27] CounterfactualLab - Phát lại log và đánh giá phản thực (what-if) khi thay đổi bộ lập kế hoạch, độ trễ hoặc hành vi tác nhân

### 📝 Mô tả đề tài
📍 Thực trạng: Đánh giá open-loop trên log (chỉ so dự đoán với quỹ đạo thật) dễ gây hiểu lầm: mô hình có ADE/FDE tốt vẫn có thể gây va chạm khi xe thật sự làm theo nó vì tác nhân khác không phản ứng như trong log; trong khi để đánh giá phản thực cần dựng lại cảnh và cho phép chỉnh sửa, việc này chưa có công cụ thuận tiện.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng phát lại log và đánh giá phản thực: nạp log thật, cho phép chỉnh sửa (bỏ/thêm tác nhân, đổi độ trễ, đổi tốc độ), chạy lại với xe ego do planner mới điều khiển và tác nhân phản ứng (reactive) hoặc phát lại (log-replay), so sánh kết quả open-loop và closed-loop, và agent giải thích vì sao hai kết quả khác nhau; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt kết luận phản thực và giả định về hành vi tác nhân (human-in-the-loop); chỉ chạy trên mô phỏng và log đã ghi, không điều khiển xe thật; phải nêu rõ giới hạn của tác nhân phản ứng so với người thật; đo bằng ADE/FDE (open-loop) so với tỷ lệ va chạm, tiến độ, độ êm và vi phạm luật (closed-loop), kèm tương quan giữa hai loại đánh giá; theo dõi thời gian chạy mỗi cảnh.

### 🛠️ Tech Stack
• Python
• nuPlan devkit (closed-loop có tác nhân phản ứng), Waymax (JAX, Waymo Open Motion)
• bộ lập kế hoạch mẫu (IDM, rule-based, mô hình học PlanTF/GameFormer ở mức tham khảo)
• nuScenes/Waymo Open Motion/Argoverse 2
• ROS2 bag/MCAP và Foxglove để xem log
• LLM + LangGraph để giải thích khác biệt
• FastAPI backend
• React/Next.js (viewer phát lại, bảng so sánh)
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp một tập cảnh từ log công khai, chạy 1 planner ở chế độ open-loop và closed-loop (tác nhân log-replay hoặc IDM), so sánh ADE/FDE với va chạm/tiến độ, viewer phát lại, ≥2 vai trò (kỹ sư kiểm thử và reviewer), HITL duyệt kết luận.

Nâng cao:
• giao diện chỉnh sửa phản thực (xóa/thêm tác nhân, thêm độ trễ, đổi tốc độ) và chạy lại hàng loạt, tính tương quan giữa chỉ số open-loop và closed-loop, agent giải thích cảnh mà hai chỉ số mâu thuẫn, phân tích độ nhạy với mô hình tác nhân, benchmark thông lượng (cảnh/giờ)
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-28] SimCI - Hạ tầng kiểm thử closed-loop trong CI/CD với chọn lọc test, phát hiện test chập chờn và đảm bảo tính tái lặp

### 📝 Mô tả đề tài
📍 Thực trạng: Bộ test mô phỏng ngày càng lớn (hàng nghìn kịch bản), chạy toàn bộ cho mỗi lần commit là không khả thi; hơn nữa mô phỏng có yếu tố ngẫu nhiên khiến test 'chập chờn' (lúc qua lúc hỏng), làm đội phát triển mất niềm tin vào kết quả và bỏ qua cảnh báo thật.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng hạ tầng CI cho kiểm thử mô phỏng: chạy kịch bản trong container có seed cố định, đo mức tái lặp, tự động phát hiện test chập chờn, chọn/ưu tiên tập test theo thay đổi mã và lịch sử lỗi để giảm chi phí mà vẫn bắt được hồi quy, tổng hợp KPI (va chạm, tiến độ, vi phạm) và agent viết báo cáo hồi quy cho từng commit; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt trước khi một thay đổi bị chặn hay được chấp nhận dựa trên kết quả mô phỏng (human-in-the-loop), hệ thống không tự động merge/chặn; chỉ chạy trên mô phỏng, không điều khiển xe thật; đo bằng tỷ lệ phát hiện hồi quy so với chạy toàn bộ khi dùng ngân sách nhỏ hơn, tỷ lệ test chập chờn, độ lệch kết quả khi chạy lại cùng seed và chi phí/thời gian CI; ghi rõ giới hạn của tập test.

### 🛠️ Tech Stack
• Python
• CARLA/MetaDrive/Waymax headless trong Docker
• pytest + GitHub Actions/GitLab CI/Jenkins
• ScenarioRunner/OpenSCENARIO để chạy kịch bản
• test selection/prioritization (học máy trên lịch sử lỗi, scikit-learn/XGBoost)
• MLflow/Prometheus + Grafana để theo dõi KPI
• LLM + LangGraph viết báo cáo hồi quy
• FastAPI backend
• React/Next.js dashboard
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu xe tự hành nuScenes, Waymo Open Dataset, KITTI-360, BDD100K, nuPlan / CARLA và chuẩn kịch bản ASAM OpenSCENARIO.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• pipeline CI chạy một bộ ≥20 kịch bản trên mô phỏng headless cho mỗi commit mẫu, dashboard KPI theo commit, phát hiện test chập chờn bằng chạy lặp, ≥2 vai trò (kỹ sư phát triển và trưởng nhóm), HITL duyệt cổng hồi quy.

Nâng cao:
• mô hình học chọn/ưu tiên test để giảm số kịch bản chạy mà vẫn bắt được hồi quy, đo hiệu quả bằng đường cong phát hiện lỗi theo ngân sách, kiểm soát tính tái lặp (seed, phiên bản asset), agent phân tích nguyên nhân hồi quy từ commit và log, tối ưu chi phí hạ tầng
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-29] XIL Orchestrator - Điều phối kiểm thử SIL - HIL - VIL từ một đặc tả test duy nhất kèm truy vết yêu cầu và đo trễ thời gian thực

### 📝 Mô tả đề tài
📍 Thực trạng: Một chức năng ADAS thường được kiểm thử ở nhiều tầng (software-in-the-loop, hardware-in-the-loop, vehicle-in-the-loop) nhưng mỗi tầng dùng công cụ và định dạng riêng, kết quả khó so sánh; yêu cầu - test case - kết quả rời rạc nên khó truy vết, và vấn đề timing/độ trễ chỉ lộ ra khi chạy trên phần cứng.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng nền tảng định nghĩa một test case một lần rồi điều phối chạy ở nhiều tầng: SIL (stack chạy trên mô phỏng/ROS2), HIL (chạy trên module tính toán nhúng như Jetson với tín hiệu CAN/cảm biến phát lại hoặc giả lập), VIL ở chế độ dữ liệu/bench đã ghi; thu thập kết quả và độ trễ end-to-end, truy vết về yêu cầu và để agent so sánh kết quả giữa các tầng, chỉ ra khác biệt do timing hay do mô hình; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: kỹ sư duyệt test plan và kết quả trước khi kết luận đạt/không đạt (human-in-the-loop); mọi thử nghiệm HIL/VIL chỉ dùng tín hiệu giả lập hoặc dữ liệu đã ghi trên bàn thử, tuyệt đối không điều khiển xe thật trên đường; đo bằng độ trễ end-to-end (p50/p95/p99), jitter, tỷ lệ khớp kết quả giữa SIL và HIL, độ phủ yêu cầu được truy vết; ghi rõ phần nào là giả lập thay vì phần cứng thật.

### 🛠️ Tech Stack
• Python/C++
• ROS2 + CARLA hoặc Gazebo cho SIL
• NVIDIA Jetson Orin/TensorRT hoặc máy giả lập ECU cho HIL (nếu không có phần cứng thì dùng container giới hạn tài nguyên để mô phỏng)
• SocketCAN/python-can, MCAP/rosbag2 để phát lại tín hiệu
• ros2_tracing/LTTng để đo độ trễ
• pytest/Robot Framework
• PostgreSQL để truy vết yêu cầu - test - kết quả
• LLM + LangGraph so sánh kết quả giữa các tầng
• FastAPI backend
• React/Next.js dashboard
• Docker.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app quản lý yêu cầu và test case, chạy cùng một test ở SIL và ≥1 tầng giả lập HIL (dữ liệu CAN/cảm biến phát lại), thu độ trễ end-to-end, ma trận truy vết yêu cầu - test - kết quả, ≥2 vai trò (kỹ sư kiểm thử và reviewer), HITL duyệt kết quả.

Nâng cao:
• so sánh tự động kết quả SIL/HIL, agent giải thích khác biệt do timing, tài nguyên hay mô hình, đo p99 độ trễ và jitter theo tải, mô phỏng hỏng tín hiệu (mất gói CAN, trễ cảm biến) để kiểm thử độ bền, báo cáo độ phủ yêu cầu và xuất hồ sơ kiểm thử
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---

## [ADAS-30] Fidelity Scorecard - Chấm điểm độ trung thực mô phỏng và kiểm chứng sim-to-real ở mức cảm biến, hành vi và kết quả kiểm thử

### 📝 Mô tả đề tài
📍 Thực trạng: Kết quả mô phỏng chỉ có giá trị khi mô phỏng đủ trung thực cho mục đích kiểm thử, nhưng thường chỉ nhìn bằng mắt ('trông giống thật'); thiếu phương pháp có hệ thống để nói mô phỏng đáng tin ở đâu, không đáng tin ở đâu, và liệu xếp hạng mô hình trong mô phỏng có khớp xếp hạng trên dữ liệu thật hay không.

🎯 Vấn đề: Bài toán đặt ra là làm thế nào để xây dựng bộ chấm điểm độ trung thực nhiều tầng: (1) mức cảm biến/dữ liệu (thống kê ảnh, point cloud), (2) mức hành vi (phân bố quỹ đạo, khoảng cách, phản ứng tác nhân), (3) mức kết quả kiểm thử (tương quan chỉ số trong sim với chỉ số trên log/dữ liệu thật cho cùng tập mô hình/kịch bản); tổng hợp thành scorecard theo ODD và agent viết báo cáo về phạm vi mô phỏng đủ tin cậy; đồng thời kết hợp mô hình học sâu/VLM với tầng kiểm tra ràng buộc hình học – động học xác định, ước lượng độ bất định có hiệu chuẩn và hỗ trợ kỹ sư khoanh vùng nguyên nhân lỗi hoặc khai thác ca khó tự động.

🔒 Ràng buộc: chuyên gia an toàn/kỹ sư phải duyệt báo cáo trước khi dùng kết quả mô phỏng làm bằng chứng kiểm thử (human-in-the-loop); chỉ dùng dữ liệu thật đã ghi/công khai và mô phỏng, không kết luận an toàn cho xe thật chỉ từ scorecard; mức trung thực đo bằng các chỉ số định lượng (khoảng cách phân bố, tương quan hạng Kendall/Spearman giữa sim và thật, sai số chỉ số KPI); phải nêu rõ giới hạn thống kê khi mẫu nhỏ.

### 🛠️ Tech Stack
• Python
• scikit-learn/SciPy/POT cho khoảng cách phân bố và tương quan hạng
• CARLA/Isaac Sim/MetaDrive làm môi trường mô phỏng
• dữ liệu thật nuScenes/Waymo Open/KITTI và bản sao dựng lại trong mô phỏng (Virtual KITTI 2, bản dựng lại của nuScenes)
• MLflow để lưu kết quả đánh giá
• LLM + LangGraph để viết báo cáo phạm vi tin cậy
• FastAPI backend
• React/Next.js (scorecard theo ODD)
• Docker + GPU.
• Dữ liệu & benchmark thực tế tham chiếu: Bộ dữ liệu Robotics Open X-Embodiment, BridgeData V2, GraspNet-1Billion, YCB Object Set cùng log chuẩn ROS2 MCAP và NVIDIA Isaac Sim / MuJoCo.

### 📦 Deliverables (Yêu cầu bàn giao)
Cơ bản:
• web app nạp kết quả từ sim và dữ liệu thật tương ứng cho ≥1 detector hoặc planner, tính chỉ số khoảng cách phân bố và tương quan hạng sim-vs-real, scorecard theo ≥3 điều kiện ODD, ≥2 vai trò (kỹ sư mô phỏng và chuyên gia an toàn), HITL duyệt báo cáo.

Nâng cao:
• đánh giá 3 tầng (cảm biến - hành vi - kết quả) với trọng số theo mục đích kiểm thử, kiểm tra xếp hạng nhiều mô hình có giữ nguyên giữa sim và thật không, ước lượng khoảng tin cậy bằng bootstrap, agent viết báo cáo phạm vi mô phỏng đủ tin cậy và khuyến nghị cải thiện, so sánh nhiều cấu hình mô phỏng
• Kết hợp kiểm chứng ràng buộc vật lý/hình học xác định với bộ benchmark đánh giá độ bền vững trên các ca biên thực tế và mở rộng công cụ chẩn đoán chuyên sâu cho đội ngũ kỹ sư.

---
