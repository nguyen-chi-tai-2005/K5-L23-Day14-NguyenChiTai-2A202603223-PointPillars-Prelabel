# Báo cáo Day 14 — Nguyễn Chí Tài — 2A202603223

- Mã học viên dùng với `--student`: `223`
- `seed_tag` trong `frames_A.txt`: `393590736f`

## 1. Dự đoán trước sweep (bước 5b)

- Tham số tôi nghĩ giảm công sửa nhiều nhất: Tăng `score_thr` (từ `0.1` lên khoảng `0.35`).
- Vì sao (nhìn ảnh BEV tập A: box thừa nhiều hay box sót nhiều?): Ở 3 frame tập A, số hộp thừa phải xóa áp đảo (`xóa = 81` chiếm `24.3/30.8` điểm chi phí, so với `thêm = 5` và `sửa = 3`). Khi tự kiểm trên CVAT, phần lớn hộp thừa là hộp nhiễu có độ tin cậy (`score`) thấp nên tăng `score_thr` lên khoảng `0.35` kỳ vọng sẽ lọc bớt nhiều hộp thừa mà không làm tăng mạnh số hộp bị sót.

## 2. Tập A: sửa tay và tune

| Cấu hình | Xóa | Thêm | Sửa | Chi phí |
|---|---:|---:|---:|---:|
| Gốc | 81 | 5 | 3 | 30.8 |
| `best_config.json` | | | | |

- Tham số đã đổi trong `best_config.json`: ...
- Kết quả leave-one-out (dán các dòng `scripts/pp_sweep.py` in ra): ...
- Cấu hình có ổn định trên từng frame không? Vì sao tôi vẫn chọn (hoặc không chọn) nó: ...

## 3. Trước/sau (bước 8)

![so sánh](../../d14_223/compare/<frame>.jpg)

- `scripts/pp_compare.py` báo giảm (hoặc tăng) ...% công sửa trên tập A.
- Dự đoán ở mục 1 đúng hay sai? Giải thích bằng số box xóa/thêm/sửa: ...

## 4. Tập B

Số đo từ `scripts/pp_prelabel.py --frames d14_223/frames_B.txt --config d14_223/best_config.json --gt d14_223/ref_B.json`:

| Xóa | Thêm | Sửa | Chi phí |
|---:|---:|---:|---:|
| | | | |

- Loại box tốn công sửa nhất ở tập B: ...

## 5. Giới hạn

- Nêu ít nhất 2 giới hạn (ví dụ: chỉ 3 frame tune; model KITTI không có Truck/Bus; chi phí là công thức, chưa phải thời gian sửa thật): ...
