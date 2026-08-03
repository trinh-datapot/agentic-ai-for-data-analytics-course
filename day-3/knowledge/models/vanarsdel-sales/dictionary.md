---
type: Data Dictionary
title: "Data Dictionary — VanArsdel Sales"
status: draft
model: vanarsdel-sales
---

# Data Dictionary — VanArsdel Sales

> **Bài 4 (buổi 2, nghiệm thu).** Mô tả các bảng và trường dữ liệu sẽ dùng để trả lời câu hỏi phân tích.
> **Must:** đủ các trường cần dùng cho tối thiểu **1 bảng fact và 1 bảng dimension**, mỗi trường đủ: tên
> bảng, tên trường, kiểu dữ liệu, ý nghĩa. Bám đúng dữ liệu thực tế (kết quả profiling) và Business Glossary.
> Xóa gợi ý trong ngoặc khi điền xong.

## Phạm vi và nguyên tắc

Data Dictionary này **chỉ mô tả các trường quan sát được trên dữ liệu thực tế**. Tại thời điểm lập, trong
`day-2/data/` chỉ có `VanArsdel_Budget.csv`; `VanArsdel_Actuals.xlsx` chưa có trong máy (xem
`knowledge/sources/vanarsdel.md`, mục "Nguồn là gì"). Vì vậy:

- Các bảng của Actuals (Sales, Product, Customer, Geography, Campaign, Date) **để trống, không bịa trường**.
- Ý nghĩa mỗi trường lấy nguyên từ Business Glossary (`org-context/glossary.md`) và tài liệu nghiệp vụ
  (`tai-lieu-nghiep-vu.md`); trường nào tài liệu không định nghĩa thì ghi rõ là chưa xác nhận.

## Tổng quan các bảng

| Bảng | Vai trò (fact / dimension) | Mô tả ngắn |
|---|---|---|
| `Budget_Raw` | nguồn thô | File `VanArsdel_Budget.csv` ở dạng bảng ma trận: 15 dòng × 38 cột, 3 tầng header (dòng 4–6), 9 dòng dữ liệu. Không dùng trực tiếp để phân tích |
| `Budget` | **fact** | Bảng ngân sách/kế hoạch sau khi unpivot 36 cột tháng. Mỗi dòng = một giá trị kế hoạch hoặc ngân sách của **một nhóm ngành hàng × một phân khúc × một loại chỉ tiêu × một tháng của một năm**. Hạt: 9 cặp Category–Segment × 3 khối (Forecast 2016, Budget 2016, Budget 2015) × 12 tháng = **324 dòng** |
| `Dim_Category` | dimension | Danh mục 5 nhóm ngành hàng, suy ra từ giá trị phân biệt của cột `Category` trong `Budget_Raw` |
| `Dim_Segment` | dimension | Danh mục 9 phân khúc kèm nhóm ngành hàng chứa nó, suy ra từ 9 cặp (Category, Segment) trong `Budget_Raw` |
| Sales | fact | **Chưa lập được** — thiếu file `VanArsdel_Actuals.xlsx` |
| Product / Customer / Geography / Campaign / Date | dimension | **Chưa lập được** — thiếu file `VanArsdel_Actuals.xlsx` |

## Mô tả trường

### Bảng `Budget_Raw` (nguồn thô, dạng ma trận)

| Trường | Kiểu dữ liệu | Ý nghĩa |
|---|---|---|
| `Category` (cột 1, từ dòng 7) | Text | Nhóm ngành hàng — cách phân loại cấp cao của sản phẩm theo định hướng sử dụng và nhóm khách hướng tới. 5 giá trị: Accessory, Mix, Rural, Urban, Youth |
| `Segment` (cột 2, từ dòng 7) | Text | Phân khúc — cách phân loại sản phẩm chi tiết hơn nhóm ngành hàng. 9 giá trị: Accessory, All Season, Convenience, Extreme, Moderation, Productivity, Regular, Select, Youth |
| Dòng 4, cột 3–38 | Text (header) | Loại chỉ tiêu của cột: `Forecast` (12 cột) hoặc `Budget` (24 cột) |
| Dòng 5, cột 3–38 | Text (header) | Năm của cột: `2016` (24 cột) hoặc `2015` (12 cột) |
| Dòng 6, cột 3–38 | Text (header) | Tháng của cột, viết tắt tiếng Anh `Jan`…`Dec`, xếp **giảm dần Dec → Jan**; mỗi tháng lặp 3 lần |
| Cột 3–38 (dòng 7–15) | Decimal | Giá trị kế hoạch/ngân sách của ô tương ứng. 324 ô, tất cả đều là số dương, min `148.08528`, max `790160.642`, 3–7 chữ số thập phân |

### Bảng `Budget` (fact — sau khi unpivot)

| Trường | Kiểu dữ liệu | Ý nghĩa |
|---|---|---|
| `Category` | Text (5 giá trị) | **Nhóm ngành hàng (Category)** — cách phân loại cấp cao của sản phẩm, thể hiện định hướng sử dụng và nhóm khách hướng tới (glossary; tài liệu mục 2). Giá trị thực tế: Accessory, Mix, Rural, Urban, Youth |
| `Segment` | Text (9 giá trị) | **Phân khúc (Segment)** — cách phân loại chi tiết hơn nhóm ngành hàng, dùng để nhìn danh mục ở mức tinh hơn khi lập kế hoạch và đánh giá kết quả (glossary; tài liệu mục 2). Giá trị thực tế: Accessory, All Season, Convenience, Extreme, Moderation, Productivity, Regular, Select, Youth |
| `Metric` | Text (2 giá trị) | Loại chỉ tiêu của dòng: `Forecast` = **kế hoạch** (dự báo doanh thu lập hằng năm), `Budget` = **ngân sách** (mục tiêu doanh thu đặt ra từ đầu kỳ) — glossary; tài liệu mục 6 |
| `Year` | Integer (2 giá trị) | Năm của giá trị kế hoạch/ngân sách. Thực tế chỉ có `2015` và `2016`; **không có `Forecast` cho 2015** |
| `Month` | Text (12 giá trị) | Tháng trong năm, viết tắt tiếng Anh `Jan`…`Dec`. Không phải kiểu ngày; phải map sang số tháng trước khi sắp xếp theo thời gian |
| `Value` | Decimal | Giá trị kế hoạch/ngân sách của tổ hợp Category × Segment × Metric × Year × Month. **Đơn vị chưa xác nhận:** tài liệu mục 6 nói kế hoạch và ngân sách được lập cho **doanh thu**, nhưng file không ghi đơn vị tiền tệ — cần nghiệp vụ xác nhận trước khi cộng với Actuals |

**Khóa dòng:** (`Category`, `Segment`, `Metric`, `Year`, `Month`) — duy nhất, không trùng.

### Bảng `Dim_Category` (dimension)

| Trường | Kiểu dữ liệu | Ý nghĩa |
|---|---|---|
| `Category` | Text (khóa, 5 giá trị) | Tên nhóm ngành hàng: Accessory, Mix, Rural, Urban, Youth |

### Bảng `Dim_Segment` (dimension)

| Trường | Kiểu dữ liệu | Ý nghĩa |
|---|---|---|
| `Segment` | Text (khóa, 9 giá trị) | Tên phân khúc |
| `Category` | Text | Nhóm ngành hàng chứa phân khúc này. Quan hệ 1 Category – nhiều Segment, quan sát trực tiếp từ 9 cặp trong dữ liệu: Accessory→Accessory; Mix→All Season, Productivity; Rural→Select; Urban→Convenience, Extreme, Moderation, Regular; Youth→Youth |

### Bảng `Sales` (fact) — chưa lập được

Thiếu file `VanArsdel_Actuals.xlsx`. Tài liệu nghiệp vụ mục 1 mô tả mỗi giao dịch ghi nhận *sản phẩm nào được
mua, khách nào mua, mua vào thời điểm nào, chiến dịch nào dẫn tới giao dịch* — nhưng **tên trường và kiểu dữ
liệu thật chưa quan sát được**, nên không điền vào đây.

Các bảng dimension của Actuals (Product, Customer, Geography, Campaign, Date) cũng ở tình trạng tương tự.

## Trường chưa xác nhận được ý nghĩa

- `Value` trong bảng `Budget`: là doanh thu hay số lượng, đơn vị tiền tệ nào — file không ghi, tài liệu nghiệp
  vụ không nêu công thức doanh thu (đã ghi trong phần gap của `glossary.md`).
- Vì sao Budget có 2 năm (2015, 2016) còn Forecast chỉ có 2016 — tài liệu mục 6 chỉ nói lập hằng năm, không
  giải thích khác biệt này.

---

> Ghi chú: bảng khách hàng có trường PII (email, họ tên) — **không đưa vào Data Dictionary dùng chung /
> báo cáo** nếu không cần thiết. `VanArsdel_Budget.csv` đã quét: **không có PII** (0 email, 0 số điện thoại,
> 0 SSN; chỉ có 2 cột chữ là Category và Segment).
