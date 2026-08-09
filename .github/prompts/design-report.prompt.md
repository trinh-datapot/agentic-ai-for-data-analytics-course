---
description: Biến kế hoạch phân tích đã duyệt thành một report spec dựng được, chốt trước khi bắt tay dựng báo cáo.
argument-hint: báo cáo cần thiết kế
---

# /design-report — Thiết kế báo cáo trước khi dựng

Chốt hình hài báo cáo thành một bản đặc tả (report spec) đủ rõ để dựng: mỗi trang trả lời câu hỏi
nào, dùng biểu đồ gì, lấy chỉ số nào, trình bày theo quy ước giao diện nào. Đây là cửa thiết kế,
chạy trước khi có bất kỳ trang báo cáo nào.

## Tình huống sử dụng

Khi đã có business question, bộ chỉ số và model đã kiểm chứng, và cần chốt thiết kế trước khi dựng.

## Tình huống không nên dùng

- Chưa có business question và Report Proposal: dùng `/gather-requirements` trước.
- Đã có spec được duyệt và đang dựng trang: dùng `/build-report`.
- Chỉ cần một trang HTML trình bày kết quả đã có: dùng `/quick-analysis`.

## Yêu cầu đầu vào

1. `knowledge/reports/*/report-proposal.md` và `business-questions.md`: báo cáo phục vụ ai, trả lời
   câu hỏi nào. Không có thì dừng lại, đề xuất chạy `/gather-requirements` trước.
2. `knowledge/metrics/`: thẻ chỉ số của bộ KPI ưu tiên, để biết mỗi câu hỏi đo bằng chỉ số nào.
3. `knowledge/models/*/model-card.md`: bảng, quan hệ và measure đang có thật trong model.
4. Quy ước giao diện của dự án nếu có: màu, font, kích thước trang.

## Các bước thực hiện

1. **Đối chiếu đầu vào trước khi thiết kế.** Với mỗi business question, kiểm ba thứ: có chỉ số nào
   trả lời được không, chỉ số đó đã có measure trong model chưa, mức chi tiết của model có đủ để cắt
   theo chiều mà câu hỏi cần không. Câu nào chưa đủ thì nêu rõ, không thiết kế trang cho nó rồi mới
   phát hiện không dựng được.
2. **Chốt ba nhóm yêu cầu.** Nghiệp vụ: đối tượng đọc từng trang, tình huống họ mở báo cáo, câu hỏi
   trang đó trả lời. Kỹ thuật: kích thước trang, theme màu và font, quy ước đặt tên trang và visual.
   Trải nghiệm: thứ bậc thông tin trên trang, chỉ số tổng đặt ở đâu, chi tiết đặt ở đâu.
3. **Lập kế hoạch trang.** Mỗi trang một dòng: tên trang, đối tượng đọc, câu hỏi trả lời, các chỉ số
   dùng, và luồng đi từ trang này sang trang khác.
4. **Chọn loại biểu đồ theo loại câu hỏi, kèm lý do.** Mỗi visual ghi rõ: trả lời câu hỏi nào, dùng
   measure nào, cắt theo chiều nào. Không đề xuất biểu đồ chỉ vì nó nhìn đẹp.
5. **Điểm dừng phê duyệt.** Trình bày toàn bộ spec trong câu trả lời và dừng lại chờ học viên duyệt.
   Không ghi file, và tuyệt đối không dựng trang nào khi spec chưa được duyệt.
6. **Ghi report spec.** Ghi vào `knowledge/reports/<tên-báo-cáo>/report-spec.md`: ba nhóm yêu cầu,
   bảng kế hoạch trang, và với mỗi trang là danh sách visual kèm câu hỏi, measure và chiều phân tích.
7. **Nêu phần không thiết kế trong đợt này**, kèm lý do, để phạm vi không bị hiểu là đã hứa.

## Kết quả đầu ra

- `knowledge/reports/<tên-báo-cáo>/report-spec.md`.
- Ba dòng kết thúc: Sản phẩm, Trạng thái, Bước tiếp theo.

## Ranh giới của skill

- Dựng trang báo cáo trong lượt này. Thiết kế và dựng là hai việc, dựng thuộc `/build-report`.
- Thiết kế một visual dùng measure hoặc cột không có thật trong model.
- Ghi spec khi học viên chưa duyệt.
- Đề xuất biểu đồ mà không nêu được nó trả lời câu hỏi nào.
