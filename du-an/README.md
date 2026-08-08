# du-an — Thư mục dự án của bạn, dùng từ buổi 4 đến buổi 8

Từ buổi 4, năm buổi liên tiếp cùng thao tác trên một kho tri thức, nên toàn bộ dự án được gom về
thư mục này. Buổi 1 đến buổi 3 vẫn nằm trong `day-1/`, `day-2/`, `day-3/`; ở buổi 4 bạn copy sản
phẩm buổi 2 và buổi 3 sang đây.

## Cấu trúc

| Thư mục | Nội dung | Buổi tạo ra |
|---|---|---|
| `org-context/` | Business requirement, Business Glossary, danh mục nguồn | 2 |
| `knowledge/sources/` | Thẻ nguồn: cấu trúc, quy tắc chất lượng dữ liệu | 2 |
| `knowledge/models/` | Data Dictionary, bản ghi xử lý, thẻ mô hình, bảng kiểm chứng | 2, 4, 6, 7 |
| `knowledge/metrics/` | KPI tree và thẻ chỉ số | 5 |
| `knowledge/reports/` | Yêu cầu phân tích, business question, Report Proposal, mockup | 3 |
| `knowledge/records/` | Báo cáo rà soát | 8 |
| `data/raw/` | Dữ liệu gốc của dự án. Không sửa đè lên các file trong này | 4 |
| `data/clean/` | Dữ liệu đã làm sạch | 4 |
| `work/` | Bản nháp và kết quả trung gian. Không dùng làm nguồn chốt | mọi buổi |

File `.pbix` của dự án đặt ngay tại `du-an/`.

## Lưu ý về dữ liệu

Dữ liệu gốc trong `data/raw/` không được commit lên GitHub. Mỗi học viên tự đặt dataset vào máy của
mình theo hướng dẫn của trợ giảng.

Các trường dữ liệu cá nhân phải được che hoặc loại trước khi đưa dữ liệu cho agent. Quy tắc này nằm
trong `.github/copilot-instructions.md` và được nhắc lại trong từng skill có chạm dữ liệu.
