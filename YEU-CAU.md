# Yêu cầu — Mini game Đập chuột

Game chạy trên trình duyệt, máy tính và điện thoại. Không cần máy chủ, không cần đăng nhập.

## 1. Luật chơi

| Mục | Quy định |
|---|---|
| Bàn chơi | Lưới 3×3 = 9 ô |
| Thời gian một lượt | 30 giây, đếm ngược |
| Chuột | Mỗi lúc chỉ có **1** con, hiện ở một ô ngẫu nhiên |
| Vị trí mới | Không trùng ô vừa hiện ngay trước đó |
| Thời gian chuột hiện | Nhanh dần: **1,2 giây** ở đầu lượt → giảm tuyến tính còn **0,6 giây** ở cuối lượt |
| Chuột biến mất khi | Bị bấm trúng, hoặc hết thời gian hiện |
| Sau khi chuột biến mất | Con tiếp theo hiện ngay (nghỉ ≤ 0,2 giây) |
| Hết 30 giây | Dừng ngay, chuột biến mất, không nhận thêm thao tác bấm, chuyển sang màn Kết quả |

## 2. Cách tính điểm

| Hành động | Điểm | Ghi nhận |
|---|---|---|
| Bấm/chạm trúng ô có chuột | **+1** | Tăng số lần trúng |
| Bấm/chạm vào ô trống (trượt) | 0 (không trừ) | Tăng số lần trượt |
| Chuột tự biến mất, không ai bấm | 0 | Tăng số chuột bị lỡ |

- Mỗi con chuột chỉ tính điểm **1 lần** (bấm liên tiếp vào cùng con không cộng thêm).
- Điểm bắt đầu từ 0 mỗi lượt.
- **Kỷ lục**: điểm cao nhất lưu trong trình duyệt (localStorage). Nếu trình duyệt chặn lưu trữ, game vẫn chạy bình thường, chỉ không giữ được kỷ lục.

## 3. Màn hình

| Màn | Nội dung | Thao tác |
|---|---|---|
| **Bắt đầu** | Tên game, luật tóm tắt 1–2 dòng, kỷ lục hiện tại | Nút **Bắt đầu** |
| **Đang chơi** | Thanh trên: Điểm · Thời gian còn lại (giây) · Kỷ lục. Bên dưới: lưới 3×3 | Bấm/chạm vào ô |
| **Kết quả** | Điểm lượt này, số trúng / trượt / lỡ, kỷ lục; dòng "Kỷ lục mới!" nếu phá kỷ lục | Nút **Chơi lại** (vào thẳng màn Đang chơi) |

Phản hồi khi chơi:
- Bấm trúng: chuột đổi hình "bị đập" ngắn (~0,2 giây), hiện "+1".
- Bấm trượt: ô rung nhẹ hoặc chớp màu.
- Còn ≤ 5 giây: đồng hồ đổi màu đỏ.

Thiết bị:
- Nhận cả chuột và chạm; chạm trên điện thoại không bị trễ hay phóng to trang.
- Lưới vuông, co theo màn hình; vừa khít màn hình dọc điện thoại (rộng từ 320px) mà không phải cuộn.

## 4. Tiêu chí hoàn thành

| # | Tiêu chí | Cách kiểm |
|---|---|---|
| 1 | Mở file trong trình duyệt là chơi được, không lỗi trong Console | Mở trên Chrome, Safari |
| 2 | Lưới đúng 3×3, mỗi lúc tối đa 1 chuột | Quan sát cả lượt |
| 3 | Chuột không hiện 2 lần liên tiếp cùng ô | Quan sát ≥ 20 lần hiện |
| 4 | Đầu lượt chuột hiện ~1,2 giây, cuối lượt ~0,6 giây | Đo hoặc ghi log |
| 5 | Bấm trúng +1, bấm trượt không trừ, mỗi con chỉ tính 1 lần | Bấm thử từng trường hợp, kể cả bấm nhanh 2 lần |
| 6 | Đồng hồ đếm đúng 30 giây, dừng đúng lúc về 0 | So với đồng hồ ngoài, sai số ≤ 0,5 giây |
| 7 | Sau khi hết giờ, bấm vào ô không đổi điểm | Bấm ngay sau khi về 0 |
| 8 | Màn Kết quả hiện đúng điểm, trúng, trượt, lỡ | Đối chiếu với lượt vừa chơi |
| 9 | Kỷ lục giữ nguyên sau khi tải lại trang; chỉ cập nhật khi điểm mới cao hơn | Chơi 2 lượt, tải lại trang |
| 10 | "Chơi lại" đưa điểm và thời gian về ban đầu | Chơi 2 lượt liên tiếp |
| 11 | Chơi được trên điện thoại màn dọc, không cuộn, chạm nhạy | Thử trên điện thoại thật hoặc giả lập 375px |

## Ngoài phạm vi

Âm thanh, nhiều người chơi, bảng xếp hạng online, nhiều loại chuột/vật cản, tạm dừng giữa lượt.
