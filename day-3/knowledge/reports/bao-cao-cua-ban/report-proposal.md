---
type: ReportProposal
title: "Report Proposal — Báo cáo đối chiếu Thực tế (Actuals) với Ngân sách (Budget)"
status: proposed
timestamp: 2026-08-03
---

# Report Proposal

## Mục tiêu

Cung cấp một báo cáo dùng chung để đối chiếu **Thực tế (Actuals)** với **Ngân sách (Budget)** ở mức **Nhóm
ngành hàng (Category)** × **Phân khúc (Segment)** × tháng, trả lời câu hỏi công ty có đạt kế hoạch hay không
và nhóm nào **vượt kế hoạch**, nhóm nào **hụt so với dự kiến** *(tài liệu nghiệp vụ mục 6)*.

## Đối tượng

- **Người đọc:** Ban lãnh đạo VanArsdel.
- **Người duyệt:** Ban lãnh đạo (chưa xác nhận chức danh cụ thể — tài liệu nghiệp vụ không nêu).

## Câu hỏi cần trả lời

Lấy từ `business-questions.md`:

- **Đợt này (dữ liệu đã có):** A1 lệch **Kế hoạch (Forecast)** vs **Ngân sách (Budget)** 2016 theo Segment ·
  A2 Budget 2016 vs 2015 theo Category · A3 tỷ trọng Budget 2016 · A4 phân bổ Budget theo tháng.
- **Bổ sung ngay khi có `VanArsdel_Actuals.xlsx`:** B1 % đạt ngân sách theo Category × tháng · B2 Segment
  **vượt kế hoạch** / **hụt so với dự kiến** · B3 số tháng vượt liên tục · B4 Forecast hay Budget sát Actuals hơn.

## Chỉ số

| Chỉ số | Công thức | Dùng cho |
|---|---|---|
| Chênh lệch Forecast − Budget | `Forecast − Budget` và `/ Budget` | A1 |
| Thay đổi Budget theo năm | `B2016 − B2015` và `/ B2015` | A2 |
| Tỷ trọng Ngân sách (Budget) | `Budget nhóm / tổng Budget` | A3, A4 |
| % đạt ngân sách | `Actuals / Budget` | B1 |
| Chênh lệch Actuals − Budget | `Actuals − Budget`; dương = **vượt kế hoạch**, âm = **hụt so với dự kiến** | B2, B3 |
| Sai số tuyệt đối trung bình | `avg(\|Actuals − Forecast\|)` so với `avg(\|Actuals − Budget\|)` | B4 |

Bốn chỉ số phái sinh (% đạt ngân sách, chênh lệch Actuals − Budget, sai số tuyệt đối trung bình, tỷ trọng)
**chưa có trong Business Glossary** — đề nghị duyệt kèm để bổ sung vào `org-context/glossary.md`.

## Phạm vi

**Làm trong đợt này**

- Chiều phân tích: **Nhóm ngành hàng (Category)** (5 giá trị), **Phân khúc (Segment)** (9 giá trị), tháng.
- Kỳ dữ liệu: **Ngân sách (Budget)** 2015 và 2016, **Kế hoạch (Forecast)** 2016.
- Nguồn: `VanArsdel_Budget.csv` (unpivot thành bảng fact `Budget`, 324 dòng) + `VanArsdel_Actuals.xlsx` khi có.
- Đầu ra: một báo cáo với bảng đối chiếu và biểu đồ theo tháng; mockup duyệt trước khi xây.

**Phạm vi không làm trong đợt này**

| Không làm | Lý do |
|---|---|
| Đối chiếu theo **Vùng (Region)**, **Địa hạt (District)**, bang, thành phố | `VanArsdel_Budget.csv` không có chiều địa lý; Budget chỉ lập tới Category và Segment *(mục 6)* |
| Đối chiếu theo **Chiến dịch (Campaign)**, **Kênh tiếp thị**, **Thiết bị** | Budget không có chiều chiến dịch |
| Đối chiếu theo **Sản phẩm** hoặc theo **Khách hàng** | Budget không lập tới mức sản phẩm/khách hàng |
| Phân tích **Lợi nhuận trên mỗi đơn vị**, **Giá vốn**, **Giá bán** | Budget chỉ có một cột giá trị, không chứa giá *(mục 2)* |
| So **Kế hoạch (Forecast)** với **Ngân sách (Budget)** cho năm 2015 | Dữ liệu không có khối Forecast 2015 |
| Phân tích xu hướng nhiều năm ngoài 2015–2016 | Budget hiện chỉ có 2 năm |
| Dự báo (forecasting) kỳ tiếp theo | Ngoài mục tiêu đợt này |
| Đưa trường **PII** (email, họ tên) của bảng khách hàng vào báo cáo | Nguyên tắc an toàn dữ liệu, xem `knowledge/sources/vanarsdel.md` |

## Rủi ro và điều kiện tiên quyết

| # | Vấn đề | Ảnh hưởng | Cần ai xử lý |
|---|---|---|---|
| R1 | `VanArsdel_Actuals.xlsx` chưa có trong máy | Toàn bộ nhóm câu hỏi B chưa làm được; đợt này chỉ ra được phần A | Người cấp dữ liệu |
| R2 | Chưa xác nhận đơn vị và ý nghĩa của giá trị Budget (là **Doanh thu**? đơn vị tiền tệ nào) | Không đặt Actuals cạnh Budget được nếu sai đơn vị | Nghiệp vụ |
| R3 | Chưa có ngưỡng để gọi là **vượt kế hoạch** / **hụt so với dự kiến** | Tạm dùng mốc chênh lệch bằng 0 | Nghiệp vụ |
| R4 | 7 ô Budget 2016 trùng khít Budget 2015 cùng tháng | Nếu là lỗi copy thì kết quả A2 sai | Nghiệp vụ xác nhận |
| R5 | Chênh lệch quy mô giữa các dòng tới ~1.600 lần (Urban/Moderation vs Rural/Select) | Biểu đồ dùng chung trục sẽ làm mất các nhóm nhỏ | Xử lý ở khâu thiết kế báo cáo |

## Đề nghị duyệt

Duyệt phạm vi trên để chuyển sang mockup. Nếu R1 chưa giải quyết, đề nghị duyệt bản **chỉ có nhóm A**, bổ
sung nhóm B ở đợt sau.

