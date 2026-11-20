# Báo cáo cá nhân — Ngày 11
Họ tên: Phạm Lâm Anh               Mã học viên: 03029  
Phiên bản CVAT (Help → About): v2.82.0  
Guideline: Road v1.0    Lần nộp (`revision` trong manifest): 1  
Thời điểm export (ngày giờ trên CVAT): 20/11/2026    Số lần nộp lại sau Rework: 0  

## 1. Kiểm project
| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Đúng | Đủ 6 label: lane, road_curb (polyline), crosswalk, drivable (polygon), traffic_light, traffic_sign (rectangle) |
| Thuộc tính và giá trị | Đúng | Khớp hoàn toàn với configs/road_v1_labels.json |
| 4 tag ảnh | Đúng | camera, timeofday, weather, source đều có thuộc tính select value |
Cách kết thúc polyline trên bản CVAT này: Bấm phím **N** (hoặc click đúp vào điểm cuối)  
Cách đặt tag ảnh trên bản CVAT này: Chọn công cụ Tag ở thanh công cụ bên trái, chọn label tag, sau đó mở bảng Objects → Details để chọn giá trị `value`  

## 2. Số lượng đã gán
| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 29 | 4 | 5 | 27 | 27 | 6 |
| front-extra (đã làm 4 / 4) | 4 | 10 | 2 | 7 | 9 | 9 | 6 |
| fisheye | 8 | 6 | 1 | 8 | 10 | 3 | 5 |
| fisheye-extra (đã làm 4 / 4) | 4 | 0 | 2 | 4 | 4 | 0 | 0 |

## 3. Bảng ca khó
| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| A01 | lane | Vạch ngoài cùng bên trái có gán không | Gán L2 solid yellow single | Vạch mép trái của đường cao tốc 1 chiều ở Mỹ, là vạch giới hạn làn ngoài cùng nên thuộc tính là L2. |
| A03 | lane | Dừng trước xe che hay vẽ xuyên qua | Nối xuyên qua và bật occluded | Guideline quy định đoạn bị che ngắn bởi xe/người thì nối liền qua và bật cờ occluded. |
| A04 | lane | Hai vạch chạy song song sát nhau | L1 (vàng đôi) và L2 (trắng đơn) | Vạch vàng đôi phân cách làn mình đang đi với làn ngược chiều, vạch trắng phân làn ngoài. |
| A10 | traffic_sign | Biển phụ đi kèm biển chính gán chung hay riêng | Vẽ box riêng group=supplementary | Theo guideline mục 3, biển phụ chữ nhật nhỏ bên dưới biển chính phải có hộp riêng với group=supplementary. |
| B07 | lane | Có đặt L1/R1 ở camera sườn xe không | Gán position=other | Theo quy tắc fisheye mục 4, camera hai bên (fisheye_left, fisheye_right) mọi lane đều phải gán position=other. |

## 4. Phiếu QC 1 nhận được
Bạn kiểm lô của tôi: Nguyễn Viết Tiến (nguyenviettien)  Quyết định nhận được: Release  
| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |
| QC1-01 | 0 | Đồng ý | Không có |
| QC1-02 | 0 | Đồng ý | Các ca thiếu vạch do mặt đường không có vạch sơn thực tế |
| QC1-03 | 0 | Đồng ý | Đã chỉnh đúng position |
| QC1-06 | 0 | Đồng ý | Đã chuẩn hóa style, color |

## 5. Kiểm file export
| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| phamlamanh-front.zip | Có | 9 | 6 | Có (value = front) |
| phamlamanh-fisheye.zip | Có | 2 | 4 | Có (value = fisheye_front) |

## 6. Ảnh chụp màn hình
1. Tab Labels của project: `docs/images/screens/01_project_labels.png`
2. Một ảnh camera trước đã gán đủ (làn, vùng lái, đèn/biển): `docs/images/screens/02_front_A01.png`
3. Một ảnh fisheye đã gán, phóng to đoạn polyline cong: `docs/images/screens/03_fisheye_B01.png`
4. Một đoạn XML có `<polyline label="lane">`: `docs/images/screens/04_xml_snippet.png`

## 7. Tự đánh giá
- **Lỗi bạn mắc nhiều nhất hôm nay (theo mã QC1-xx), và cách tránh ở Ngày 20**:  
  Lỗi hay gặp nhất là quên sửa Details ngay sau khi vẽ hoặc đặt tag (QC1-01, QC1-06), vì CVAT luôn tự điền giá trị mặc định đầu danh sách (như L1/solid/white hay weather=clear). Cách tránh: Luôn tạo thói quen kiểm tra bảng Details ở cột bên phải ngay sau khi hoàn thành mỗi shape hoặc tag trước khi bấm Save.

- **Nhãn của bạn đi vào model ở đâu? Chọn một lỗi đã sửa và nói nó làm model học sai thế nào**:  
  Nhãn `lane` (vạch làn đường) là ground truth để huấn luyện mô hình phát hiện làn xe (Lane Detection như mạng Ultra-Fast-Lane-Detection hoặc SVM trích xuất đặc trưng cạnh). Nếu vạch bị gán sai chiều (từ xa về gần thay vì từ gần ra xa), mô hình sẽ học sai thứ tự chuỗi điểm định hướng di chuyển. Nếu gán nhầm vạch ngoài L2 thành L1, thuật toán giữ làn tự động (LKA - Lane Keeping Assist) sẽ tính sai độ lệch tâm của xe so với làn đường, dẫn đến việc điều khiển vô lăng đánh lái lệch khỏi làn chạy an toàn, có thể gây va chạm với dải phân cách hoặc phương tiện làn bên cạnh.

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor
| y | 720 | 680 | 640 | 600 | 560 |
| --- | ---: | ---: | ---: | ---: | ---: |
| x của chúng tôi | 830 | 800 | 772 | 745 | 720 |
| x của bạn kia | 828 | 798 | 770 | 744 | 718 |

Trả lời 3 câu:
1. Năm số x đó chính là đích mà một model row-anchor học cho vạch này. Nếu bạn dừng polyline sớm 40 px, hàng nào đổi thành "không có làn"?  
   -> Hàng **y = 560** sẽ bị đổi thành "không có làn" (do vạch kết thúc trước khi chạm tới hàng quét này).
2. So với bạn được kiểm (cùng ảnh): ở hàng 720 và hàng 560, hai bạn lệch nhau bao nhiêu pixel? Lệch ở hàng nào ảnh hưởng LKA nhiều hơn (slide 25)?  
   -> Ở hàng 720 lệch 2 px, ở hàng 560 lệch 2 px. Lệch ở hàng **720 (sát xe nhất)** ảnh hưởng tới LKA nhiều hơn, vì điểm sát xe quyết định trực tiếp góc lệch tức thời (heading angle) và sai số khoảng cách ngang (lateral offset) để xe điều chỉnh góc lái ngay lập tức.
3. Nếu polyline vẽ từ xa về gần (ngược quy tắc 2), cách tính trên có đổi không? Script nào sẽ gặp khó?  
   -> Cách nội suy tọa độ x theo các hàng y vẫn có thể tính được nếu thuật toán sắp xếp lại theo y, nhưng các script xử lý tuần tự (như tính hướng vector di chuyển, vector định hướng của làn, hoặc các script đánh giá độ cong từ gần ra xa) sẽ gặp khó khăn hoặc nhận diện sai điểm bắt đầu của làn xe.
