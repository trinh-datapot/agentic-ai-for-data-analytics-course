# Dữ liệu dự án — VanArsdel

Dự án dùng hai nguồn dữ liệu:

| File | Ở đâu | Nội dung |
|---|---|---|
| `VanArsdel_Budget.csv` | trong thư mục này | Ngân sách và dự báo doanh thu (dạng bảng ma trận) |
| `VanArsdel_Actuals.xlsx` | **ngoài repo** (file lớn ~32 MB) | Dữ liệu bán hàng thực tế: nhiều bảng (Sales và các bảng mô tả) |

## Lấy file Actuals

File `VanArsdel_Actuals.xlsx` (~32 MB) không để trong repo vì dung lượng lớn. Giảng viên phát riêng file
này (hoặc link tải); bạn tải về và **đặt vào chính thư mục `data/` này** để đường dẫn trong các bài lab
hoạt động đúng.

(Nhóm có dữ liệu riêng thì thay bằng dữ liệu của nhóm.)

## Lưu ý an toàn dữ liệu cá nhân (PII)

Bảng khách hàng trong dữ liệu chứa **thông tin cá nhân (email, họ tên)**. Che hoặc loại các trường này
**trước khi** đưa dữ liệu cho AI, và không đưa lên báo cáo công khai.
