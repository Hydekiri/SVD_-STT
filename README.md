# Phân Tích SVD Và Ứng Dụng Trong Xử Lý Ảnh

Notebook `test.ipynb` minh họa cách dùng SVD để xấp xỉ hạng thấp, giảm nhiễu và so sánh trực quan ảnh gốc với ảnh tái tạo ở nhiều giá trị `k`.

## Cấu Trúc Thư Mục

- `test.ipynb`: notebook chính để chạy toàn bộ quy trình.
- `image/`: thư mục chứa ảnh đầu vào.
- `ma_tran_day_du/`: nơi lưu các ma trận kênh ảnh dạng CSV.
- `ket_qua_svd/`: nơi lưu ảnh kết quả và hình so sánh.

## Dữ Liệu Đầu Vào

Notebook hiện đang mặc định dùng file:

- `image/noise_hoa.jpg`

Nếu muốn dùng ảnh khác, hãy mở `test.ipynb` và sửa biến `IMAGE_PATH` ở phần cấu hình.

## Yêu Cầu

Notebook sẽ tự kiểm tra và cài các thư viện cần thiết nếu máy chưa có:

- `numpy`
- `pillow`
- `matplotlib`
- `scikit-image`

Bạn chỉ cần đảm bảo đang chạy trong môi trường có thể sử dụng Jupyter Notebook.

## Cách Chạy

1. Mở `test.ipynb` bằng VS Code hoặc Jupyter Notebook.
2. Chạy lần lượt toàn bộ các ô trong notebook.
3. Notebook sẽ:
   - đọc ảnh đầu vào,
   - phân biệt ảnh xám hoặc ảnh màu,
   - tách ma trận từng kênh,
   - phân tích SVD,
   - tái tạo ảnh theo nhiều giá trị `k`,
   - đánh giá bằng MSE, PSNR, SSIM, tỷ lệ nén và chuẩn Frobenius,
   - lưu kết quả ra thư mục đầu ra.

## Kết Quả Sinh Ra

Sau khi chạy xong, bạn sẽ thấy:

- các file CSV trong `ma_tran_day_du/` tương ứng với từng kênh ảnh,
- ảnh so sánh đa mức `k` trong `ket_qua_svd/`,
- ảnh kết quả tốt nhất theo ngưỡng năng lượng trong `ket_qua_svd/`.

## Thông Số Có Thể Chỉnh

Trong notebook, bạn có thể thay đổi các biến sau:

- `IMAGE_PATH`: đường dẫn ảnh đầu vào.
- `K_VALUES`: danh sách các giá trị hạng `k` cần thử.
- `NGUONG_NANG_LUONG`: ngưỡng năng lượng để chọn `k` tối ưu.

## Ghi Chú

- Nếu ảnh đầu vào là ảnh màu, notebook sẽ tách thành 3 kênh `R`, `G`, `B`.
- Nếu ảnh đầu vào là ảnh xám, notebook sẽ xử lý trên một ma trận cường độ sáng.
- Kết quả đầu ra có thể bị ghi đè nếu bạn chạy notebook lại với cùng tên ảnh.
