---
type: AnalysisRequirement
title: "Yêu cầu phân tích — Báo cáo đối chiếu Thực tế (Actuals) với Ngân sách (Budget)"
status: draft
timestamp: 2026-08-03
---

# Yêu cầu phân tích (data story)

> ⚠️ **Yêu cầu gốc chưa được cung cấp.** Bản làm rõ dưới đây được dựng từ **ưu tiên số 4 trong
> `org-context/org-profile.md` — "Bám sát kế hoạch"** (dẫn nguồn: tài liệu nghiệp vụ mục 6 và mục 7) và từ
> phạm vi dữ liệu thực tế đã profiling ở `knowledge/sources/vanarsdel.md`. Khi có yêu cầu báo cáo thật của
> dự án, dán vào mục "Yêu cầu gốc" bên dưới và soát lại bốn thành phần.

| Thành phần | Nội dung |
|---|---|
| **Đối tượng** | Ban lãnh đạo VanArsdel — người theo dõi sát lợi nhuận trên mỗi đơn vị theo từng **Nhóm ngành hàng (Category)** và **Phân khúc (Segment)** *(mục 2)*, và coi việc so sánh **Thực tế (Actuals)** với **Ngân sách (Budget)** là một trong những cách đánh giá quan trọng nhất *(mục 6)*. <br>**Chưa xác nhận:** tài liệu không nêu chức danh, phòng ban hay người dùng cấp dưới cụ thể của báo cáo. |
| **Tình huống** | VanArsdel lập **Kế hoạch (Forecast)** và **Ngân sách (Budget)** cho **Doanh thu** hằng năm, chi tiết tới từng **Nhóm ngành hàng (Category)**, từng **Phân khúc (Segment)** và từng tháng trong năm *(mục 6)*. Trong và sau kỳ kinh doanh, kết quả **Thực tế (Actuals)** cần được đối chiếu với **Ngân sách (Budget)** để biết công ty có đạt kế hoạch hay không, nhóm nào **vượt kế hoạch**, nhóm nào **hụt so với dự kiến** *(mục 6)*. Hiện việc đối chiếu này chưa có báo cáo dùng chung; hai nguồn nằm ở hai file tách rời (`VanArsdel_Actuals.xlsx` và `VanArsdel_Budget.csv`). |
| **Quyết định** | Báo cáo phục vụ hai quyết định đã nêu trong business requirement: <br>1. **Điều chỉnh kế hoạch** — xác định **Nhóm ngành hàng (Category)** hoặc **Phân khúc (Segment)** nào **vượt kế hoạch**, nhóm nào **hụt so với dự kiến** để xử lý *(mục 6)*. <br>2. **Quyết định về danh mục** — xác định **Nhóm ngành hàng (Category)** và **Phân khúc (Segment)** nào đang đóng góp nhiều nhất và còn dư địa tăng trưởng *(mục 7)*. |
| **Kết quả kỳ vọng** | Một báo cáo cho phép, ở mức **Nhóm ngành hàng (Category)** × **Phân khúc (Segment)** × tháng: <br>• So **Thực tế (Actuals)** với **Ngân sách (Budget)** cùng kỳ và thấy ngay chênh lệch. <br>• Chỉ ra danh sách **Phân khúc (Segment)** đang **vượt kế hoạch** và danh sách đang **hụt so với dự kiến**. <br>• Xem diễn biến theo từng tháng trong năm để thấy xu hướng bám sát kế hoạch. <br>• So **Kế hoạch (Forecast)** với **Ngân sách (Budget)** — chỉ áp dụng cho năm 2016, vì dữ liệu không có khối **Kế hoạch (Forecast)** cho năm 2015. |

## Ràng buộc đã biết từ dữ liệu (không suy đoán)

- Báo cáo **chỉ làm được ở mức Nhóm ngành hàng (Category) × Phân khúc (Segment) × tháng**. `VanArsdel_Budget.csv` không có chiều **Vùng (Region)**, **Địa hạt (District)**, **Khách hàng**, **Chiến dịch (Campaign)** hay **Sản phẩm**, nên không đối chiếu **Thực tế (Actuals)** với **Ngân sách (Budget)** theo các chiều đó được.
- Phạm vi thời gian hiện có của Budget: **Ngân sách (Budget)** 2015 và 2016, **Kế hoạch (Forecast)** chỉ 2016.
- `VanArsdel_Actuals.xlsx` **chưa có trong máy** — chưa xác nhận được Actuals phủ những năm nào và có cùng mức chi tiết Category/Segment hay không.
- **Đơn vị của giá trị Budget chưa được xác nhận** (tài liệu mục 6 nói lập cho **Doanh thu** nhưng file không ghi đơn vị tiền tệ); cần chốt trước khi đặt hai nguồn cạnh nhau.

## Thông tin yêu cầu gốc cần bổ sung

- Người dùng cụ thể và tần suất xem báo cáo.
- Kỳ báo cáo mong muốn (năm nào, tới tháng nào).
- Ngưỡng để coi là **vượt kế hoạch** hay **hụt so với dự kiến** (tài liệu không nêu con số).
- Công thức tính **Doanh thu** trên dữ liệu **Thực tế (Actuals)** để so được với **Ngân sách (Budget)**.

## Yêu cầu gốc (trước khi làm rõ)

<chưa được cung cấp — dán yêu cầu báo cáo ban đầu của dự án vào đây, giữ nguyên văn>

