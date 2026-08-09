# vanarsdel — Dự án thực hành trên lớp, dùng từ buổi 2 đến buổi 8

> Đây là dự án cả lớp cùng làm trong suốt khóa AI for Data Analytics, trên dữ liệu của công ty
> **VanArsdel**. Từ buổi 2 trở đi, mọi sản phẩm bạn dựng ra đều nằm trong thư mục này.

Buổi 1 là buổi làm quen, chạy riêng trong `day-1/` trên dữ liệu demo AdventureWorks, không thuộc dự án này.

**Đây không phải Final Project.** Final Project là một dự án riêng, có checkpoint review với giảng viên,
học viên thực hiện ở cuối khóa. Thông tin đăng ký được gửi riêng sau buổi 2.

## Kho ngữ cảnh chia hai lớp

Đây là cách agent (và cả nhóm) tổ chức hiểu biết về dự án. Hai lớp tách nhau rõ:

| Thư mục | Là gì | Ai tạo |
|---|---|---|
| **`org-context/`** | **Ngữ cảnh khai báo**: những gì doanh nghiệp cho biết trước (họ là ai, thuật ngữ, có nguồn dữ liệu nào). | Bạn khai báo, ít thay đổi. |
| **`knowledge/`** | **Tri thức tích lũy**: những gì công việc tạo ra (kết quả profiling, mô tả dữ liệu, chỉ số, mô hình, báo cáo). | Bạn bồi đắp dần qua các buổi. |

Ý tưởng: đổi `org-context/` là đổi sang dự án khác, còn `knowledge/` bắt đầu lại từ đầu cho mỗi dự án.
Đây là cách làm rút gọn từ framework agent thật của Datapot, giữ đúng tên và cấu trúc để bạn quen dần.

## Cấu trúc

| Thư mục | Nội dung | Buổi tạo ra |
|---|---|---|
| `tai-lieu-nghiep-vu.md` | Tài liệu nghiệp vụ có sẵn của doanh nghiệp, đọc ở buổi 2 | có sẵn |
| `org-context/` | Business requirement, Business Glossary, danh mục nguồn | 2 |
| `knowledge/sources/` | Thẻ nguồn: cấu trúc, quy tắc chất lượng dữ liệu | 2 |
| `knowledge/models/` | Data Dictionary, bản ghi xử lý, thẻ mô hình, bảng kiểm chứng | 2, 4, 6, 7 |
| `knowledge/reports/` | Yêu cầu phân tích, business question, Report Proposal, mockup | 3 |
| `knowledge/metrics/` | KPI tree và thẻ chỉ số | 5 |
| `knowledge/records/` | Báo cáo rà soát | 8 |
| `data/raw/` | Dữ liệu gốc của dự án. Không sửa đè lên các file trong này | có sẵn |
| `data/clean/` | Dữ liệu đã làm sạch | 4 |
| `work/` | Bản nháp và kết quả trung gian. Không dùng làm nguồn chốt | mọi buổi |

File `.pbix` của dự án đặt ngay tại `vanarsdel/`.

## Bạn điền gì ở buổi 2 và buổi 3

| Phần thực hành | Sản phẩm | Điền vào |
|---|---|---|
| Buổi 2 · Bài 1 | Business requirement, tóm tắt bài toán có dẫn nguồn | `org-context/org-profile.md` |
| Buổi 2 · Bài 2 | Business Glossary, một thuật ngữ một định nghĩa | `org-context/glossary.md` |
| Buổi 2 · Bài 3 | Kết quả profiling, vấn đề chất lượng kèm bằng chứng | `knowledge/sources/vanarsdel.md` |
| Buổi 2 · Bài 4 | Data Dictionary, mô tả các bảng và trường dữ liệu | `knowledge/models/vanarsdel-sales/dictionary.md` |
| Buổi 3 · Bài 1 đến 4 | Yêu cầu phân tích, business question, Report Proposal, mockup | `knowledge/reports/bao-cao-cua-ban/` |

## Lưu ý về dữ liệu

Dữ liệu gốc trong `data/raw/` không được commit lên GitHub. Mỗi học viên tự đặt dataset vào máy của
mình theo hướng dẫn của trợ giảng.

Các trường dữ liệu cá nhân phải được che hoặc loại trước khi đưa dữ liệu cho agent. Quy tắc này nằm
trong `.github/copilot-instructions.md` và được nhắc lại trong từng skill có chạm dữ liệu.

## Nguyên tắc

- **Che dữ liệu cá nhân (PII)** trước khi đưa cho AI (xem lưu ý trong `data/README.md`).
- **Kiểm chứng trước khi dùng**: mỗi ý nghiệp vụ dẫn nguồn, mỗi con số đối chiếu dữ liệu thực tế.
- **Một thuật ngữ một định nghĩa** trong glossary.
- **Chốt phạm vi trước khi build**: Report Proposal phải có mục phạm vi không làm trong đợt này.
