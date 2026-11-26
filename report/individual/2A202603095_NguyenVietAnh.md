# Báo cáo Day 14 — Nguyễn Việt Anh — 2A202603095

> Sao chép file này thành `report/individual/<MSSV>_<HoTen>.md` (không dấu), ví dụ `2A20260000_NguyenVanAn.md`.

- Mã học viên dùng với `--student`: `095`
- `seed_tag` trong `frames_A.txt`: `393590736f`

## 1. Dự đoán trước sweep (bước 5b)

Ghi **trước** khi chạy `scripts/pp_sweep.py`, rồi commit và push ngay (lịch sử commit là bằng chứng thời điểm viết). Không sửa phần này sau khi có kết quả.

- Tham số tôi nghĩ giảm công sửa nhiều nhất: `score_thr=0.35` và `min_points=5`.
- Vì sao: Khi sửa 3 frame tập A, tôi thấy các hộp thừa thường nằm trên hàng cây và quanh vị trí xe mang cảm biến LiDAR. Cấu hình gốc có 30 hộp cần xóa và 3 hộp cần thêm. Tôi dự đoán lọc chặt hơn sẽ giảm công xóa hộp thừa.

## 2. Tập A: sửa tay và tune

| Cấu hình | Xóa | Thêm | Sửa | Chi phí |
|---|---:|---:|---:|---:|
| Gốc | 30 | 3 | 3 | 13.5 |
| `best_config.json` | | | | |

Ở cấu hình gốc, ba frame lần lượt có 5, 9 và 16 hộp cần xóa. Mỗi frame có 1 hộp cần thêm và 1 hộp cần sửa. Trong tổng chi phí 13,5 điểm, các thao tác xóa chiếm 9 điểm.

- Tham số đã đổi trong `best_config.json`: ...
- Kết quả leave-one-out (dán các dòng `scripts/pp_sweep.py` in ra): ...
- Cấu hình có ổn định trên từng frame không? Vì sao tôi vẫn chọn (hoặc không chọn) nó: ...

## 3. Trước/sau (bước 8)

![so sánh](../../d14_095/compare/<frame>.jpg)

- `scripts/pp_compare.py` báo giảm (hoặc tăng) ...% công sửa trên tập A.
- Dự đoán ở mục 1 đúng hay sai? Giải thích bằng số box xóa/thêm/sửa: ...

## 4. Tập B

Số đo từ `scripts/pp_prelabel.py --frames d14_095/frames_B.txt --config d14_095/best_config.json --gt d14_095/ref_B.json`:

| Xóa | Thêm | Sửa | Chi phí |
|---:|---:|---:|---:|
| | | | |

- Loại box tốn công sửa nhất ở tập B: ...

## 5. Giới hạn

- Nêu ít nhất 2 giới hạn (ví dụ: chỉ 3 frame tune; model KITTI không có Truck/Bus; chi phí là công thức, chưa phải thời gian sửa thật): ...
