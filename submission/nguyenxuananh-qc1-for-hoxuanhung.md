# Phiếu QC 1 — Road v1.0

> Phiếu đang chờ lô nhãn. Các số mục, lỗi và quyết định sẽ điền sau khi kiểm dữ liệu của Hồ Xuân Hùng.

- Lô cần kiểm **Hồ Xuân Hùng**
- Người kiểm **Nguyễn Xuân Anh**
- Ngày kiểm đang chờ · Guideline Road v1.0
- File và revision đang chờ bộ export CVAT hoặc liên kết project đã chia sẻ.
- Mẫu cần kiểm 6 ảnh · Số ảnh và số nhãn đã kiểm sẽ điền sau khi nhận lô.

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót |  |  | nặng |
| QC1-02 đủ L1, R1 | bỏ sót |  |  | nặng |
| QC1-03 position | sai thuộc tính / thừa |  |  | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót |  |  | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính |  |  | chính |
| QC1-06 style, color, kind | sai thuộc tính |  |  | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa |  |  | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính |  |  | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính |  |  | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi |  |  | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính |  |  | chính |
| QC1-12 file | lỗi file |  |  | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |

## Quyết định
Lỗi nặng: __   Lỗi chính: __ / __ nhãn = __ %   Lỗi nhẹ: __   Ca chờ lead: __
Quyết định (Release / Hold / Rework):
Lý do (theo luật của phiếu):

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).

## Ghi chú tự kiểm lô Nguyễn Xuân Anh

| Ảnh | QC1-02 cần xác nhận | Quan sát |
| --- | --- | --- |
| A05 | L1 và R1 | Đoạn đường có xe đỗ hai bên. Quan sát thấy vết vá và dấu phun trên mặt đường, chưa thấy sơn giới hạn L1/R1. |
| A06 | R1 | Vạch trắng ngang là vạch sang đường. Nét dọc rõ sát lề nằm bên kia dãy cột, ngoài phần đường xe đang đi. Chưa thấy R1 dọc làn đang đi. |
| A07 | L1 | Nét sáng bên trái đi cùng mép dải chắn và dải mặt đường sát chân chắn. Chưa thấy vạch sơn L1 tách riêng. R1 trắng liền đã có nhãn. |
| A08 | L1 | Nét chéo mờ giữa giao lộ có dạng đường nối mặt đường. Vạch trắng rõ nằm xa hơn về phía trái. Chưa thấy sơn xác nhận L1 của làn đang đi. R1 trắng đứt đã có nhãn. |

Các trường hợp này đang chờ coach xác nhận. Đây là ghi chú của lô Nguyễn Xuân Anh.
