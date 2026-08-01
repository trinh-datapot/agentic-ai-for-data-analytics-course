# Dự án của bạn — Buổi 3: Lên kế hoạch phân tích (scaffold)

> Khung dựng sẵn cho buổi 3. Buổi này bạn **không đụng dữ liệu thô**, mà biến một yêu cầu báo cáo còn
> mơ hồ thành một **kế hoạch phân tích được duyệt** trước khi xây báo cáo. Làm tiếp trên dự án của nhóm.

## Chuẩn bị: mang sản phẩm buổi 2 sang

Buổi 3 xây trên nền buổi 2. Trước khi bắt đầu, mang các sản phẩm buổi 2 vào (copy hai thư mục
`org-context/` và `knowledge/` từ buổi 2 sang đây, hoặc mở song song thư mục buổi 2):

- **business requirement** — trong `org-context/org-profile.md`
- **Business Glossary** — trong `org-context/glossary.md`
- **Data Dictionary** — trong `knowledge/models/.../dictionary.md`

## Bạn điền gì ở buổi 3

Bốn sản phẩm nối tiếp nhau, gom trong một thẻ báo cáo tại
`knowledge/reports/bao-cao-cua-ban/` (đổi tên thư mục thành slug báo cáo của bạn):

| Phần thực hành | Sản phẩm | Điền vào |
|---|---|---|
| Bài 1 · Yêu cầu phân tích | Làm rõ yêu cầu theo bốn thành phần data story | `analysis-requirement.md` |
| Bài 2 · Business question | Các business question, mỗi câu gắn một quyết định | `business-questions.md` |
| Bài 3 · Report Proposal | Đề xuất báo cáo theo khung chuẩn, có phạm vi không làm | `report-proposal.md` |
| Bài 4 · Mockup và duyệt | Bản phác hình hài báo cáo + ý kiến duyệt (nghiệm thu) | `mockup.md` (+ `mockup.html`), `review-notes.md` |

## Nội dung thư mục

```
du-an-cua-ban/  (buổi 3)
└── knowledge/
    └── reports/
        └── bao-cao-cua-ban/         # một thẻ báo cáo (đổi tên theo báo cáo của bạn)
            ├── README.md
            ├── analysis-requirement.md   # Bài 1
            ├── business-questions.md      # Bài 2
            ├── report-proposal.md         # Bài 3
            ├── mockup.md                  # Bài 4 (phác Markdown; hoặc thêm mockup.html)
            └── review-notes.md            # Bài 4 (ý kiến duyệt)
```

`org-context/` và phần còn lại của `knowledge/` mang từ buổi 2 sang.

## Nguyên tắc

- **Kiểm chứng trước khi dùng**: thuật ngữ bám đúng Business Glossary buổi 2, không đổi cách gọi.
- **Chốt phạm vi trước khi build**: Report Proposal phải có mục **phạm vi không làm** trong đợt này.
- **Duyệt trước khi xây**: proposal và mockup được duyệt mới sang buổi 4.
