# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Nguyễn Viết Tiến (nguyenviettien)        Người kiểm (học viên): Phạm Lâm Anh (03029)  
Ngày: 20/11/2026                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): nguyenviettien-front.zip, nguyenviettien-fisheye.zip (revision 1)  
Số ảnh kiểm: 6 (+ 0 ảnh thêm, ghi riêng)   Số nhãn đã kiểm (shape + tag): 45  

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 6 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 12 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 15 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 15 | 1 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 6 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 15 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 8 | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 10 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 4 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 4 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 6 | 1 | chính |
| QC1-12 file | lỗi file | 2 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-04 | A02 | lane (L1) | chính | Điểm cuối vạch đứt dừng hơi sớm khoảng 10px so với điểm nhìn rõ trên ảnh |
| 2 | QC1-11 | B03 | lane (L2) | chính | Đoạn cong ở rìa ngoài còn ít điểm, nên bổ sung thêm điểm để ôm sát cung cong |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A05 | Vạch bên phải bị mòn sát lề cỏ không có vạch sơn rõ thì có cần vẽ R1 không? | Xác nhận không thấy vạch sơn thì không vẽ R1, được miễn theo CHECKPOINTS |

## Quyết định
Lỗi nặng: 0   Lỗi chính: 2 / 45 nhãn = 4.4 %   Lỗi nhẹ: 0   Ca chờ lead: 0  
Quyết định (Release / Hold / Rework): **Release**  
Lý do (theo luật của phiếu): Không có lỗi nặng nào; tỉ lệ lỗi chính là 4.4% (dưới ngưỡng 5%); các file mở lại tốt và đúng chuẩn định dạng CVAT 1.1.
