---
type: Mockup
title: "Mockup — Báo cáo đối chiếu Thực tế (Actuals) với Ngân sách (Budget)"
status: draft
timestamp: 2026-08-03
---

# Mockup

Bản phác hình hài để xin duyệt. Xem bản trực quan tại **`mockup.html`** (file tự chứa, mở bằng trình duyệt).

**Quy ước dữ liệu trong mockup:**

- Phần **A1–A4**: dùng **số thật** tính từ `VanArsdel_Budget.csv` (đã có dữ liệu).
- Phần **B1–B4**: dùng **số minh họa** vì `VanArsdel_Actuals.xlsx` chưa có — mọi khối B đều gắn nhãn
  ⚠️ *số minh họa*.

## Bố cục phác

Báo cáo 1 trang, chia 2 khối theo `report-proposal.md`:

```
┌───────────────────────────────────────────────────────────────────────────┐
│ TIÊU ĐỀ · Bộ lọc: Năm [2016 ▾]  Nhóm ngành hàng [Tất cả ▾]  Phân khúc [▾] │
├───────────────────────────────────────────────────────────────────────────┤
│ KHỐI A — Kế hoạch (Forecast) và Ngân sách (Budget)   [dữ liệu đã có]      │
│ ┌─────────────┬─────────────┬─────────────┬─────────────┐                 │
│ │ Thẻ số: Tổng Budget 2016 · Tổng Forecast 2016 · Lệch · Số Segment lệch>2%│
│ └─────────────┴─────────────┴─────────────┴─────────────┘                 │
│ ┌───────────────────────────────┬───────────────────────────────────────┐ │
│ │ A1 Bar ngang: %lệch F−B       │ A2 Bar đôi: B2016 vs B2015 theo       │ │
│ │    theo 9 Phân khúc (Segment) │    5 Nhóm ngành hàng (Category)       │ │
│ ├───────────────────────────────┼───────────────────────────────────────┤ │
│ │ A3 Bảng tỷ trọng Budget 2016  │ A4 Line: Budget 2016 theo 12 tháng    │ │
│ └───────────────────────────────┴───────────────────────────────────────┘ │
├───────────────────────────────────────────────────────────────────────────┤
│ KHỐI B — Đối chiếu Thực tế (Actuals)   ⚠️ chờ VanArsdel_Actuals.xlsx      │
│ ┌───────────────────────────────┬───────────────────────────────────────┐ │
│ │ B1 Heatmap % đạt ngân sách    │ B2 Bar phân kỳ: vượt kế hoạch /       │ │
│ │    Category × 12 tháng        │    hụt so với dự kiến theo Segment    │ │
│ ├───────────────────────────────┼───────────────────────────────────────┤ │
│ │ B3 Bảng: số tháng vượt liên   │ B4 Bảng so sai số: Forecast vs Budget │ │
│ │    tục theo Segment           │    cái nào sát Actuals hơn            │ │
│ └───────────────────────────────┴───────────────────────────────────────┘ │
└───────────────────────────────────────────────────────────────────────────┘
```

## Mỗi phần trả lời câu hỏi nào

| Phần | Business question | Loại hình | Chỉ số hiển thị |
|---|---|---|---|
| A1 | Kế hoạch (Forecast) 2016 lệch bao nhiêu so với Ngân sách (Budget) 2016 theo Phân khúc (Segment)? | Bar ngang có mốc 0 | % lệch = (Forecast − Budget) / Budget |
| A2 | Budget 2016 tăng/giảm bao nhiêu so với Budget 2015 theo Nhóm ngành hàng (Category)? | Bar đôi + nhãn % thay đổi | Tổng 12 tháng B2016, B2015, % thay đổi |
| A3 | Nhóm nào chiếm tỷ trọng lớn nhất trong tổng Budget 2016? | Bảng xếp hạng + thanh tỷ trọng | Tổng Budget và % tỷ trọng |
| A4 | Budget 2016 phân bổ theo tháng thế nào, tháng nào là đỉnh? | Đường theo 12 tháng | Tổng Budget theo tháng |
| B1 | Từng tháng, Thực tế (Actuals) đạt bao nhiêu % Ngân sách (Budget) theo Category? | Heatmap Category × tháng | % đạt ngân sách = Actuals / Budget |
| B2 | Segment nào **vượt kế hoạch**, Segment nào **hụt so với dự kiến**? | Bar phân kỳ quanh mốc 0 | Chênh lệch Actuals − Budget |
| B3 | Segment nào vượt liên tục nhiều tháng nhất? | Bảng + dải 12 ô tháng | Số tháng có Actuals − Budget > 0 |
| B4 | Forecast hay Budget sát Actuals hơn? | Bảng so sánh 2 cột | Sai số tuyệt đối trung bình |

## Điểm thiết kế cần duyệt

- **A3 dùng bảng chứ không dùng biểu đồ tròn**: Urban chiếm 83,98% tổng Budget 2016 còn Rural chỉ 0,03%
  (chênh ~1.600 lần, xem R5 trong `report-proposal.md`), biểu đồ tròn/cột chung trục sẽ làm mất nhóm nhỏ.
- **A1 dùng % lệch thay vì số tuyệt đối** để 9 Phân khúc (Segment) so được với nhau bất kể quy mô.
- **Không hiển thị đơn vị tiền tệ** cho tới khi nghiệp vụ xác nhận (R2) — mockup ghi trục là "giá trị".
- **Ngưỡng vượt/hụt tạm dùng mốc 0** (R3); nếu nghiệp vụ chốt ngưỡng %, đổi màu theo ngưỡng đó.
- **Khối B để nguyên khung rỗng có nhãn cảnh báo** nếu tới ngày duyệt vẫn chưa có Actuals (R1).

