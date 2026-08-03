# Tổng kết kết quả chạy Lab buổi 2 và buổi 3

Người chạy: vinhtq · Ngày: 2026-08-03 · Nhánh: `vinhtest`

Tài liệu này tổng kết kết quả thực hành Lab buổi 2 (chuẩn bị ngữ cảnh và dữ liệu) và buổi 3 (lên kế hoạch
phân tích) trên bộ dữ liệu VanArsdel, kèm các điểm vướng khi prompt agent.

---

## Buổi 2 — Sản phẩm đã hoàn thành

| Bài | Sản phẩm | File |
|---|---|---|
| Bài 1 | Business requirement, mỗi ý dẫn nguồn về đúng mục tài liệu nghiệp vụ | `day-2/org-context/org-profile.md` |
| Bài 2 | Business Glossary — 26 thuật ngữ, mỗi thuật ngữ một định nghĩa + một ví dụ + cột nguồn | `day-2/org-context/glossary.md` |
| Bài 3 | Thẻ nguồn (profiling) — 10 vấn đề chất lượng kèm bằng chứng + kết quả quét PII | `day-2/knowledge/sources/vanarsdel.md` |
| Bài 4 | Data Dictionary — 4 bảng (1 fact + 2 dimension + 1 bảng thô) | `day-2/knowledge/models/vanarsdel-sales/dictionary.md` |

### Kết quả profiling đáng chú ý

`VanArsdel_Budget.csv`: 15 dòng × 38 cột, trong đó **9 dòng dữ liệu**, 324 ô đo lường.

- Không phải bảng phẳng mà là **bảng ma trận 3 tầng header** (dòng 4, 5, 6) + 3 dòng rác đầu file.
- **0 ô thiếu**, **0 ô non-numeric**, **0 dòng trùng**.
- **Thiếu ở mức thiết kế:** có Budget 2015, Budget 2016, Forecast 2016 nhưng **không có Forecast 2015**.
- **7 ô Budget 2016 trùng khít Budget 2015 cùng tháng** (ví dụ Accessory/Accessory Jan = `52269.26591`) — nghi
  copy số năm trước, chưa kết luận là lỗi.
- Ngoại lệ theo IQR: Urban/Extreme (6 ô, tháng 10–11) và Urban/Regular (3 ô, tháng 10); vì lặp nhất quán ở cả
  ba khối nên nhiều khả năng là mùa vụ.
- Chênh lệch quy mô giữa các dòng tới **~1.600 lần** (Urban/Moderation vs Rural/Select).
- **Không ghi đơn vị tiền tệ** ở bất kỳ đâu trong file.
- **Quét PII: sạch** — 0 email, 0 số điện thoại, 0 SSN. Mẫu ZIP khớp 298 lần nhưng đều là false positive
  (phần thập phân của số tiền).

---

## Buổi 3 — Sản phẩm đã hoàn thành

| Bài | Sản phẩm | File |
|---|---|---|
| Bài 1 | Yêu cầu phân tích theo 4 thành phần data story | `day-3/knowledge/reports/bao-cao-cua-ban/analysis-requirement.md` |
| Bài 2 | 8 business question (A1–A4 làm được ngay, B1–B4 chờ Actuals) | `day-3/.../business-questions.md` |
| Bài 3 | Report Proposal có mục phạm vi không làm + bảng rủi ro R1–R5 | `day-3/.../report-proposal.md` |
| Bài 4 | Mockup Markdown + `mockup.html` tự chứa (8 khối, mỗi khối một business question) | `day-3/.../mockup.md`, `mockup.html` |

Trong mockup, khối A dùng **số thật** tính từ `VanArsdel_Budget.csv` (tổng Budget 2016 = 10.986.388, tổng
Forecast 2016 = 10.991.884, lệch +0,05%); khối B dùng **số minh họa** và được gắn nhãn rõ vì thiếu file
Actuals.

---

## Khó khăn và chỗ bị stuck khi prompt agent

### 1. Thiếu file `VanArsdel_Actuals.xlsx` — ảnh hưởng xuyên suốt hai buổi

Trong `day-2/data/` chỉ có `VanArsdel_Budget.csv`. Đây là chỗ vướng lớn nhất:

- Bài 3 buổi 2 chỉ profiling được 1/7 bảng; 6 bảng Sales, Product, Customer, Geography, Campaign, Date phải
  để trống.
- Bài 4 buổi 2 không lập được Data Dictionary cho bảng fact `Sales` thật.
- Buổi 3: 4/8 business question (B1–B4) không tính được, mockup phải dùng số minh họa.

Cách xử lý: ghi rõ "chưa khảo sát được — thiếu file" thay vì để agent suy đoán tên trường.

### 2. Prompt không nói agent ghi thẳng vào file mẫu

Các prompt trong tài liệu lab yêu cầu "tóm tắt", "liệt kê", "lập..." nhưng **không nói ghi vào file `.md` mẫu
nào**. Nếu không tự mở/đính kèm file mẫu thì agent chỉ trả lời trong chat, phải copy tay vào file. Đề xuất
thêm ngay trong prompt: *"ghi kết quả vào `org-context/org-profile.md`, giữ nguyên cấu trúc mục có sẵn"*.

### 3. Prompt buổi 3 có placeholder chưa thay

Prompt bài 1 buổi 3 để nguyên `[dán yêu cầu của dự án vào đây]`. Agent không có yêu cầu báo cáo thật nên phải
dừng lại hỏi; nếu agent tự bịa một yêu cầu thì cả chuỗi bài 2–3–4 sẽ lệch theo. Hiện `analysis-requirement.md`
đang dựng tạm theo ưu tiên "Bám sát kế hoạch" (mục 6, 7) và có ghi cảnh báo ở đầu file.

### 4. Bước mang sản phẩm buổi 2 sang buổi 3 chưa rõ

README buổi 3 nói "copy hai thư mục `org-context/` và `knowledge/` từ buổi 2 sang", nhưng không nói rõ copy
vào đâu trong cây thư mục buổi 3, và `day-3/knowledge/` đã có sẵn thư mục `reports/` nên dễ copy nhầm chỗ.
Thực tế đã có 3 file (`glossary.md`, `org-profile.md`, `dictionary.md`) bị đặt nhầm vào
`day-3/knowledge/reports/bao-cao-cua-ban/` và phải dọn lại.

Đường dẫn đúng đã dùng:

```
day-3/org-context/                              <- từ day-2/org-context/
day-3/knowledge/models/vanarsdel-sales/         <- từ day-2/knowledge/models/
day-3/knowledge/sources/                        <- từ day-2/knowledge/sources/
```

### 5. Một vài prompt thiếu dữ kiện

Ví dụ prompt "profiling dataset này" không nói rõ dataset gồm những file nào và ở đường dẫn nào; prompt lập
Data Dictionary không nói phạm vi là toàn bộ dataset hay chỉ file đang có. Phải tự đọc `data/README.md` và
`knowledge/sources/*.md` mới suy ra được.

### 6. Prompt cuối (dựng mockup HTML) chạy lâu

Bước dựng `mockup.html` mất khoảng **5 phút** vì agent phải tính lại số thật từ CSV, sinh HTML/CSS/SVG tự
chứa, rồi mở trình duyệt kiểm tra hiển thị.

### 7. Lỗi chính tả trong một số câu prompt của tài liệu lab

Đã ghi nhận, xem ảnh đính kèm trong comment PR.

---

## Việc còn treo, cần bên nghiệp vụ hoặc giảng viên xử lý

| # | Vấn đề | Chặn việc gì |
|---|---|---|
| R1 | Chưa có `VanArsdel_Actuals.xlsx` | Toàn bộ nhóm câu hỏi B, bảng fact Sales |
| R2 | Chưa xác nhận đơn vị và ý nghĩa giá trị Budget (là Doanh thu? đơn vị tiền tệ nào) | Không đặt Actuals cạnh Budget được |
| R3 | Chưa có ngưỡng gọi là "vượt kế hoạch" / "hụt so với dự kiến" | Tạm dùng mốc chênh lệch bằng 0 |
| R4 | 7 ô Budget 2016 trùng khít Budget 2015 | Kết quả so sánh năm có thể sai |
| R5 | Chênh lệch quy mô ~1.600 lần giữa các nhóm | Ảnh hưởng cách chọn biểu đồ |
| — | 4 chỉ số phái sinh chưa có trong Business Glossary | Cần bổ sung định nghĩa nếu proposal được duyệt |
