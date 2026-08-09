# Dữ liệu dự án — VanArsdel

| Thư mục | Nội dung |
|---|---|
| `raw/` | Dữ liệu gốc. Không sửa đè lên các file trong này. |
| `clean/` | Dữ liệu đã làm sạch, sinh ra từ buổi 4. |

Dự án dùng hai nguồn dữ liệu, cả hai đặt trong `raw/`:

| File | Ở đâu | Nội dung |
|---|---|---|
| `VanArsdel_Budget.csv` | có sẵn trong `raw/` | Ngân sách và dự báo doanh thu (dạng bảng ma trận) |
| `VanArsdel_Actuals.xlsx` | **ngoài repo** (file lớn ~32 MB) | Dữ liệu bán hàng thực tế: nhiều bảng (Sales và các bảng mô tả) |

## Lấy file Actuals

File `VanArsdel_Actuals.xlsx` (~32 MB) không để trong repo vì dung lượng lớn. Giảng viên phát riêng file
này (hoặc link tải); bạn tải về và **đặt vào thư mục `vanarsdel/data/raw/`** để đường dẫn trong các bài lab
hoạt động đúng.


## Lưu ý an toàn dữ liệu cá nhân (PII)

Bảng khách hàng trong dữ liệu chứa **thông tin cá nhân (email, họ tên)**. Che hoặc loại các trường này
**trước khi** đưa dữ liệu cho AI, và không đưa lên báo cáo công khai.
