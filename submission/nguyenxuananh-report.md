# Báo cáo cá nhân — Ngày 11

- Họ tên **Nguyễn Xuân Anh** · Mã học viên **2A202603117**
- Project `d11-road-NguyenXuanAnh` · CVAT v2.74.1 · Road v1.0
- Bản sau Rework và rà soát box đèn A08 `revision 3` · Manifest tạo lúc 21/11/2026 08:39:13 UTC+7
- Hai job `front` và `fisheye` đều ở trạng thái `completed`.

## 1. Kiểm project

| Mục | Kết quả | Ghi chú |
| --- | --- | --- |
| 6 label và kiểu | Đủ | Lane và road_curb dùng polyline. Crosswalk và drivable dùng polygon. Đèn và biển dùng rectangle. |
| Thuộc tính và giá trị | Theo taxonomy Road v1.0 | Kiểm position, style, color, kind, area_type và thuộc tính đèn, biển. |
| 4 tag ảnh | 20/20 ảnh | camera, timeofday, weather, source. Tag camera khớp tên ảnh. |

Kết thúc polyline bằng `N`. Đặt tag bằng công cụ Tag, sau đó kiểm `value` trong Objects → Details.

## 2. Số lượng đã gán

| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 26 | 7 | 4 | 24 | 25 | 20 |
| fisheye | 8 | 6 | 12 | 9 | 4 | 6 | 4 |

Ảnh thêm A13–A16 và B09–B12 chưa thực hiện. Đèn ở phần gán bổ sung có dùng YOLO11l để đề xuất vị trí, sau đó đối chiếu ảnh. Hình học được vẽ và rà theo Road v1.0.

## 3. Bảng ca khó và tự kiểm

| Ảnh | Nhãn hoặc mã | Đã chọn và lý do |
| --- | --- | --- |
| A03 | L1 | Đổi đường bám vạch sơn vàng thành lane L1. Chọn nét liền phía làn xe, tại biên vùng gạch chéo. |
| A01, A04, A09, A11 | QC1-05 | Giữ một polyline `kind=double` cho mỗi vạch đôi và dùng nét phía làn xe làm đường đại diện. |
| A06 | QC1-05 | Vạch đôi có một nét liền và một nét đứt. Chọn cách biểu diễn `double / dashed` theo nét gần làn xe. |
| A10 | R1 | Vạch trắng liền bị mòn và khó thấy do mặt đường ướt. Gán đoạn còn thấy trước khi mất dấu. |
| A12 | R1 | Gán vạch trắng đứt nhìn thấy phía bên kia vạch sang đường. Dừng trước vùng không còn phân biệt được vạch. |
| A05 | QC1-02 · L1, R1 | Đoạn đường có xe đỗ hai bên. Quan sát thấy vết vá và dấu phun trên mặt đường, chưa thấy sơn giới hạn L1/R1. Chờ coach xác nhận. |
| A06 | QC1-02 · R1 | Vạch trắng ngang là vạch sang đường. Nét dọc rõ sát lề nằm bên kia dãy cột, ngoài phần đường xe đang đi. Chưa thấy R1 dọc làn đang đi. Chờ coach xác nhận. |
| A07 | QC1-02 · L1 | Nét sáng bên trái đi cùng mép dải chắn và dải mặt đường sát chân chắn. Chưa thấy vạch sơn L1 tách riêng. R1 trắng liền đã có nhãn. Chờ coach xác nhận. |
| A08 | QC1-02 · L1 | Nét chéo mờ giữa giao lộ có dạng đường nối mặt đường. Vạch trắng rõ nằm xa hơn về phía trái. Chưa thấy sơn xác nhận L1 của làn đang đi. R1 trắng đứt đã có nhãn. Chờ coach xác nhận. |

Đã xem lại ảnh gốc và vùng phóng to của A05–A08. Chưa xác định được vạch cần bổ sung nên giữ nhãn CVAT khi xuất lại. Còn 5 cảnh báo QC1-02 trên 4 ảnh, đã ghi vào mục tự kiểm của phiếu và đang chờ coach xác nhận.

## 4. Phiếu QC 1 nhận được và kết quả tự QC

Chưa nhận phiếu QC 1 từ bạn kiểm. Các kết quả dưới đây đến từ tự QC lô Nguyễn Xuân Anh. Hai bản xuất trước được lưu trong `r1/` và `r2/` kèm manifest tương ứng.

### 4.1. Mẫu kiểm lại sau Rework

Đối chiếu A05–A08, B03 và B06 với ảnh gốc và lớp phủ từ `annotations.xml` của `revision 2`, sau đó phóng to riêng box đèn A08 và xác minh bản xuất `revision 3`. Bản r3 chỉ thay đổi hai thuộc tính của cùng một box, nên mẫu vẫn gồm sáu ảnh. Sau khi bỏ một vùng lái gán thừa, mẫu còn **52 shape và 24 tag**, tổng cộng 76 nhãn. Mỗi nhãn tính một lần vào mẫu số.

| Ảnh | Camera | Shape | Tag | Kết quả kiểm lại |
| --- | --- | ---: | ---: | --- |
| A05 | front | 3 | 4 | L1 và R1 chờ coach xác nhận. |
| A06 | front | 13 | 4 | Bỏ vùng lái ngược chiều và chỉnh nhóm ba biển. R1 chờ coach xác nhận. |
| A07 | front | 5 | 4 | Vùng direct tiếp tục dưới phần xe phía trước che khuất. L1 chờ coach xác nhận. |
| A08 | front | 17 | 4 | R1 đã có. L1 chờ coach xác nhận. Box đèn ID 3167 đã rà lại trên ảnh gốc. |
| B03 | fisheye rear | 10 | 4 | Vạch R2 bám lại theo tâm các đoạn sơn. |
| B06 | fisheye left | 4 | 4 | Đường road_curb đi theo chân dải bê tông. Lane vẫn có position other. |

### 4.2. Tổng hợp theo mã

| Mã | Mục kiểm trên bản mới | Lỗi xác nhận ở r1 | Lỗi còn lại ở r3 |
| --- | --- | ---: | ---: |
| QC1-01 | 24 tag trên 6 ảnh | 0 | 0 |
| QC1-02 | 8 vị trí L1/R1 trên 4 ảnh front | 0 | 0 · 5 cảnh báo còn chờ |
| QC1-03 | 8 polyline lane, gồm position other trên B06 | 0 | 0 |
| QC1-04 | 5 polyline lane front | 0 | 0 |
| QC1-05 | 8 polyline lane, rà vạch đứt và đoạn che | 0 | 0 |
| QC1-06 | 8 polyline lane, rà style, color và kind | 0 | 0 |
| QC1-07 | 8 vùng lái và 4 vùng sang đường | 2 | 0 |
| QC1-08 | 17 box đèn và ảnh gốc | 0 | 0 xác nhận |
| QC1-09 | 17 box đèn và 8 box biển | 3 | 0 |
| QC1-10 | 8 box biển và ảnh gốc | 0 | 0 xác nhận |
| QC1-11 | 6 polyline và 5 box trên 2 ảnh fisheye | 2 | 0 tại các điểm kiểm |
| QC1-12 | 2 ZIP và 76 nhãn trong mẫu | 0 | 0 |

### 4.3. Bảy lỗi chính đã xử lý

Dùng ID shape trên CVAT để đối chiếu giữa hai lần export vì thứ tự shape trong XML có thể đổi.

| Mã | Ảnh | ID CVAT | Sửa và xác nhận |
| --- | --- | ---: | --- |
| QC1-07 | A06 | 3131 | Bỏ polygon `alternative` lấn sang phần đường xe ngược chiều. |
| QC1-09 | A06 | 3134 | Đổi biển cảnh báo công trường từ `prohibitory` sang `warning`. |
| QC1-09 | A06 | 3132 | Đổi biển cảnh báo hình thoi vàng từ `other` sang `warning`. |
| QC1-09 | A06 | 3133 | Đổi biển ONE WAY từ `information` sang `mandatory`. |
| QC1-07 | A07 | 3146 | Vẽ lại polygon `direct` giữa mép dải chắn và R1, bao phần mặt đường bị xe trước che. |
| QC1-11 | B03 | 3218 | Vẽ lại R2 theo tâm các đoạn vạch đứt. Lệch lớn nhất đo ở bốn điểm lấy mẫu khoảng 0.9 px. |
| QC1-11 | B06 | 3239 | Vẽ lại `road_curb` dọc mép tiếp giáp giữa chân dải bê tông và mặt đường. Lệch lớn nhất ở năm điểm lấy mẫu khoảng 0.9 px. |

Tọa độ mốc được đọc trực tiếp trên ảnh gốc rồi đo khoảng cách tới polyline trong XML.

### 4.4. Rà soát bổ sung box đèn A08

Box `traffic_light` ID **3167** nằm quanh (429, 232), kích thước khoảng 11 × 10 px. Khi phóng to bằng cách nhân pixel gốc, thấy một vùng sáng màu cam trong cụm hộp nhỏ ở góc đường. Vị trí, dạng vỏ và màu phù hợp với đèn dành cho người đi bộ. Biểu tượng bên trong quá mờ để nhận diện chi tiết. Màu cam là tín hiệu thường dùng cho biểu tượng dừng của đèn người đi bộ tại Mỹ. [FHWA MUTCD, mục 4I.02](https://mutcd.fhwa.dot.gov/pdfs/11th_Edition/part4.pdf)

Đổi `type` từ `vehicle` sang `pedestrian`. Chọn `color=unknown` vì Road v1.0 có red, yellow, green, off và unknown, trong khi màu nhìn được là cam. XML bản r3 đã phản ánh hai giá trị mới.

### 4.5. Ca chờ xác nhận và kết luận

- **QC1-02:** A05 thiếu L1 và R1, A06 thiếu R1, A07 và A08 thiếu L1. Vẫn chưa thấy rõ vạch sơn tương ứng. Các trường hợp này chờ coach xác nhận.
- **Kết luận tự QC — Hold.** Bản r1 có 7/77 lỗi chính (9,1%). Bảy lỗi đã được sửa ở r2 và box đèn A08 được rà thêm ở r3. Trên mẫu 76 nhãn của bản r3, ghi nhận **0 lỗi nặng đã xác nhận, 0 lỗi chính còn lại và 0 lỗi nhẹ**. Năm cảnh báo QC1-02 vẫn cần coach xác nhận trước khi Release.

## 5. Kiểm file export

| File | Mở lại được | Shape ảnh 1 (job / file) | Shape ảnh 2 (job / file) | Tag camera trong XML |
| --- | --- | ---: | ---: | --- |
| nguyenxuananh-front.zip | Có | 9 / 9 | 5 / 5 | 12/12 |
| nguyenxuananh-fisheye.zip | Có | 5 / 5 | 6 / 6 | 8/8 |

Định dạng CVAT for images 1.1. Cả hai ZIP chỉ chứa `annotations.xml`. Manifest ghi `contains_images=false`, đủ 20 ảnh và 20 ảnh đủ tag. Dấu SHA-256 khớp từng ZIP.

**Đối chiếu trước khi nộp.** Hai job đều completed. Hai ZIP mở được, đủ 20 ảnh và tag camera khớp. Manifest là revision 3. Báo cáo có ảnh tab Labels, sơ đồ hình học nhãn và bảng kiểm file. Bộ nộp đang chờ hai điều kiện trong SUBMISSION.md gồm xác nhận 5 cảnh báo QC1-02 và Phiếu QC 1 đã điền từ lô của bạn được ghép.

## 6. Minh chứng

Ảnh 1 chụp phần Labels của giao diện CVAT. Hình 2 và 3 là sơ đồ dựng từ tọa độ nhãn trong ZIP bàn giao. Hình 4 là đoạn XML trích từ ZIP front. Bản minh chứng trên ảnh gốc được lưu tại máy theo quy định dữ liệu của lab.

1. Tab Labels project

   ![Tab Labels của project][labels]

2. Sơ đồ nhãn A08 với làn, vùng lái, đèn và biển

   ![Sơ đồ nhãn A08 từ XML][front]

3. Sơ đồ các polyline fisheye của B03

   ![Sơ đồ polyline B03 từ XML][fisheye]

4. Đoạn XML của vạch L1 ở A03

   ![XML của polyline A03][xml]

## 7. Tự đánh giá

QC1-02 là cảnh báo thường gặp nhất. Lần sau cần ghi mã ảnh ngay khi không thấy L1/R1 và hỏi coach trước khi xuất. Lỗi đã sửa ở A03 là dùng `road_curb` cho vạch sơn. Với mô hình row-anchor, hệ thống chỉ lấy tọa độ của các polyline lane. Gán nhầm loại khiến vạch đang thấy bị xem là vắng ở các hàng neo mà nó đi qua.

[labels]: evidence/01-project-labels.jpg
[front]: evidence/02-front-a08-diagram.jpg
[fisheye]: evidence/03-fisheye-b03-diagram.jpg
[xml]: evidence/04-lane-xml.jpg
