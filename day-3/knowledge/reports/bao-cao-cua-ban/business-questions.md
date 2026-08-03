---
type: BusinessQuestions
title: "Business question — Báo cáo đối chiếu Thực tế (Actuals) với Ngân sách (Budget)"
status: draft
timestamp: 2026-08-03
---

# Business question

> Nguồn: `analysis-requirement.md` (bốn thành phần data story) và ràng buộc dữ liệu trong
> `knowledge/sources/vanarsdel.md`. Thuật ngữ bám đúng `org-context/glossary.md`, không đổi cách gọi.

## Nhóm A — Trả lời được ngay với `VanArsdel_Budget.csv`

| # | Business question | Ai đọc | Phục vụ quyết định gì | Đo bằng chỉ số nào |
|---|---|---|---|---|
| A1 | **Kế hoạch (Forecast)** năm 2016 lệch bao nhiêu so với **Ngân sách (Budget)** năm 2016, ở từng **Phân khúc (Segment)**? | Ban lãnh đạo | Điều chỉnh kế hoạch: phát hiện sớm phân khúc mà bản dự báo đã lệch khỏi mục tiêu đầu kỳ, trước khi có **Thực tế (Actuals)** | Chênh lệch Forecast − Budget (tuyệt đối) và % lệch = (Forecast − Budget) / Budget, tính trên `Value`, theo 9 **Phân khúc (Segment)**, năm 2016 |
| A2 | **Ngân sách (Budget)** năm 2016 tăng hay giảm bao nhiêu so với **Ngân sách (Budget)** năm 2015, ở từng **Nhóm ngành hàng (Category)**? | Ban lãnh đạo | Quyết định về danh mục: thấy công ty đang dồn mục tiêu vào nhóm nào | Chênh lệch tổng 12 tháng B2016 − B2015 và % thay đổi, theo 5 **Nhóm ngành hàng (Category)** |
| A3 | **Nhóm ngành hàng (Category)** và **Phân khúc (Segment)** nào chiếm tỷ trọng lớn nhất trong tổng **Ngân sách (Budget)** năm 2016? | Ban lãnh đạo | Quyết định về danh mục: xác định nhóm đóng góp nhiều nhất để ưu tiên theo dõi | Tổng `Value` 12 tháng và % tỷ trọng trên tổng toàn bộ, xếp hạng 5 Category và 9 Segment |
| A4 | Trong năm 2016, **Ngân sách (Budget)** của từng **Phân khúc (Segment)** phân bổ theo tháng như thế nào, tháng nào là đỉnh? | Ban lãnh đạo | Điều chỉnh kế hoạch: biết tháng cao điểm để đặt kỳ vọng đúng khi đối chiếu với **Thực tế (Actuals)** | `Value` theo 12 tháng và tỷ trọng tháng / tổng năm, theo từng **Phân khúc (Segment)** |

## Nhóm B — Cần `VanArsdel_Actuals.xlsx` (chưa có file, xem `knowledge/sources/vanarsdel.md`)

| # | Business question | Ai đọc | Phục vụ quyết định gì | Đo bằng chỉ số nào |
|---|---|---|---|---|
| B1 | Từng tháng, **Thực tế (Actuals)** đạt bao nhiêu phần trăm **Ngân sách (Budget)** ở mức **Nhóm ngành hàng (Category)**? | Ban lãnh đạo | Điều chỉnh kế hoạch: biết công ty có đạt kế hoạch hay không, ở nhóm nào | % đạt ngân sách = Actuals / Budget, theo Category × tháng |
| B2 | **Phân khúc (Segment)** nào đang **vượt kế hoạch**, phân khúc nào **hụt so với dự kiến** trong kỳ đang xét? | Ban lãnh đạo | Điều chỉnh kế hoạch: chọn phân khúc cần can thiệp | Chênh lệch Actuals − Budget theo 9 **Phân khúc (Segment)**; dương = **vượt kế hoạch**, âm = **hụt so với dự kiến** |
| B3 | Trong các **Phân khúc (Segment)** đang **vượt kế hoạch**, phân khúc nào vượt liên tục nhiều tháng nhất? | Ban lãnh đạo | Quyết định về danh mục: xác định nhóm còn dư địa tăng trưởng | Số tháng có Actuals − Budget > 0 trong 12 tháng, theo từng **Phân khúc (Segment)** |
| B4 | Bản **Kế hoạch (Forecast)** 2016 có sát **Thực tế (Actuals)** hơn **Ngân sách (Budget)** 2016 không? | Ban lãnh đạo | Điều chỉnh kế hoạch: biết nên dựa vào Forecast hay Budget cho kỳ sau | Sai số tuyệt đối trung bình \|Actuals − Forecast\| so với \|Actuals − Budget\|, theo **Phân khúc (Segment)** × tháng, năm 2016 |

## Câu hỏi CHƯA đo được với dữ liệu dự án (không đưa vào báo cáo đợt này)

Ghi lại để tránh bị hỏi lại, kèm lý do:

- **Vùng (Region)** / **Địa hạt (District)** nào **vượt kế hoạch**? → `VanArsdel_Budget.csv` không có chiều địa lý; **Ngân sách (Budget)** chỉ lập tới **Nhóm ngành hàng (Category)** và **Phân khúc (Segment)** *(mục 6)*.
- **Kênh tiếp thị** / **Thiết bị** nào đạt kế hoạch tốt nhất? → Budget không có chiều **Chiến dịch (Campaign)**.
- **Sản phẩm** nào **hụt so với dự kiến**? → Budget không lập tới mức sản phẩm.
- Lợi nhuận so với kế hoạch? → Budget chỉ có một cột giá trị, không có **Giá vốn** / **Giá bán**; **Lợi nhuận trên mỗi đơn vị** nằm ở dữ liệu sản phẩm *(mục 2)*, không có trong Budget.
- So sánh **Kế hoạch (Forecast)** với **Ngân sách (Budget)** cho năm 2015 → dữ liệu **không có khối Forecast 2015**.

## Điểm cần chốt trước khi tính

- **Ngưỡng** để gọi là **vượt kế hoạch** / **hụt so với dự kiến**: hiện dùng mốc chênh lệch bằng 0. Tài liệu nghiệp vụ không nêu ngưỡng phần trăm — cần nghiệp vụ chốt.
- **Đơn vị và ý nghĩa của `Value`** trong Budget (là **Doanh thu**? đơn vị tiền tệ nào) — chưa xác nhận, xem `knowledge/models/vanarsdel-sales/dictionary.md`.
- Các chỉ số phái sinh dùng ở trên (**% đạt ngân sách**, **chênh lệch Actuals − Budget**, **sai số tuyệt đối trung bình**) **chưa có trong Business Glossary** — nếu chốt dùng thì phải bổ sung định nghĩa vào `org-context/glossary.md`.

> Giữ số lượng câu hỏi gọn và tập trung: đây là trục để các buổi sau chọn Data Dictionary, KPI và
> measure vừa đủ, tránh làm tràn lan.

