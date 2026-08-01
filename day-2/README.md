# Dự án của bạn — Khung bắt đầu (scaffold)

> Đây là khung dự án dựng sẵn cho khóa AI for Data Analytics, dùng từ buổi 2. Bạn mở thư mục này trong
> VSCode và điền dần các sản phẩm qua từng buổi. Bản mẫu đi kèm dữ liệu **VanArsdel**; nhóm có dữ liệu
> riêng thì thay dữ liệu và điền lại theo cùng cấu trúc.

## Kho ngữ cảnh chia hai lớp

Đây là cách agent (và cả nhóm) tổ chức hiểu biết về dự án. Hai lớp tách nhau rõ:

| Thư mục | Là gì | Ai tạo |
|---|---|---|
| **`org-context/`** | **Ngữ cảnh khai báo**: những gì doanh nghiệp cho biết trước (họ là ai, thuật ngữ, có nguồn dữ liệu nào). | Bạn khai báo, ít thay đổi. |
| **`knowledge/`** | **Tri thức tích lũy**: những gì công việc tạo ra (kết quả profiling, mô tả dữ liệu, sau này là chỉ số, mô hình, báo cáo). | Bạn bồi đắp dần qua các buổi. |

Ý tưởng: đổi `org-context/` là đổi sang dự án khác, còn `knowledge/` bắt đầu lại từ đầu cho mỗi dự án.
Đây là cách làm rút gọn từ framework agent thật của Datapot, giữ đúng tên và cấu trúc để bạn quen dần.

## Bạn điền gì ở buổi 2

| Phần thực hành | Sản phẩm | Điền vào |
|---|---|---|
| Bài 1 · business requirement | Tóm tắt bài toán từ tài liệu nghiệp vụ, có dẫn nguồn | `org-context/org-profile.md` |
| Bài 2 · Business Glossary | Bộ thuật ngữ nghiệp vụ, một thuật ngữ một định nghĩa | `org-context/glossary.md` |
| Bài 3 · profiling | Vấn đề chất lượng dữ liệu kèm bằng chứng | `knowledge/sources/vanarsdel.md` |
| Bài 4 · Data Dictionary | Mô tả các bảng và trường dữ liệu | `knowledge/models/vanarsdel-sales/dictionary.md` |

## Nội dung thư mục

```
du-an-cua-ban/
├── tai-lieu-nghiep-vu.md        # tài liệu nghiệp vụ có sẵn của doanh nghiệp (đọc ở Bài 1)
├── data/                        # dữ liệu dự án
│   ├── VanArsdel_Budget.csv
│   └── README.md                # đường dẫn file dữ liệu lớn (Actuals)
├── org-context/                 # ngữ cảnh khai báo
│   ├── org-profile.md
│   ├── glossary.md
│   └── sources.md
└── knowledge/                   # tri thức tích lũy
    ├── sources/vanarsdel.md
    └── models/vanarsdel-sales/dictionary.md
```

## Nguyên tắc

- **Che dữ liệu cá nhân (PII)** trước khi đưa cho AI (xem lưu ý trong `data/README.md`).
- **Kiểm chứng trước khi dùng**: mỗi ý nghiệp vụ dẫn nguồn, mỗi con số đối chiếu dữ liệu thực tế.
- **Một thuật ngữ một định nghĩa** trong glossary.
