# Nộp bài (hạn 16:35, Ngày 11)

Nộp đúng 5 file lên kênh nộp bài coach chỉ định. Không gửi file GT, không gửi ảnh và không đăng file lên kênh chung của lớp.

- [x] `<tên>-front.zip`: CVAT for images 1.1, **không kèm ảnh**; gồm task front (A01–A12) và front-extra nếu có làm.
- [x] `<tên>-fisheye.zip`: CVAT for images 1.1, **không kèm ảnh**; gồm task fisheye (B01–B08) và fisheye-extra nếu có làm.
- [x] `<tên>-manifest.json`: manifest bàn giao, không chấm điểm (xem [đặc tả bàn giao](docs/delivery_road_v1.0.md)).
- [ ] `<tên>-qc1-for-<tên bạn được kiểm>.md`: Phiếu QC 1 đã điền theo [`templates/qc1_form.md`](templates/qc1_form.md).
- [x] `<tên>-report.md`: báo cáo theo [`templates/report.md`](templates/report.md).

Trước khi nộp:

- [x] Mọi job ở trạng thái **completed**.
- [ ] Đã mở lại hai file zip và chạy `PYTHONPATH=src python3 -m road_lab.road_check lint <tên>-front.zip <tên>-fisheye.zip`; không còn dòng nào mức nặng. Nếu còn QC1-02 "chưa có L1/R1" ở ảnh thật sự không thấy vạch: đừng vẽ thêm vạch, gọi coach xác nhận và ghi mã ảnh vào phiếu.
- [x] Đã tạo manifest: thêm `--manifest <tên>-manifest.json --name <tên> --revision 1` vào lệnh trên; trong file, `contains_images` là `false`.
- [x] Mọi ảnh có đủ bốn tag, tag camera đúng.
- [x] Báo cáo có ảnh chụp màn hình và bảng kiểm file (mục 5 của báo cáo).

Sửa sau buffer: trước khi export lại, chép hai zip và manifest cũ vào thư mục `r1/` trên máy (manifest cũ đổi tên thành `<tên>-manifest-r1.json`). Sau đó nộp hai file zip **cùng tên** và manifest mới với `--revision 2`. Ghi vào mục 4 của báo cáo đã sửa những gì.

## Trạng thái bản nộp ngày 23/11/2026

**Hold — revision 3.** Hai ZIP trong thư mục [submission](submission/) khớp SHA-256 của manifest. Lint ghi nhận 5 cảnh báo QC1-02 trên 20 ảnh. A05 thiếu L1 và R1, A06 thiếu R1, A07 và A08 thiếu L1. Các ca này đang chờ coach xác nhận. Trạng thái completed của hai job được ghi theo báo cáo cá nhân.

[Phiếu QC 1 cho Hồ Xuân Hùng](submission/nguyenxuananh-qc1-for-hoxuanhung.md) đang chờ bộ export hoặc liên kết CVAT của Hùng để kiểm mẫu 6 ảnh và điền kết quả.
