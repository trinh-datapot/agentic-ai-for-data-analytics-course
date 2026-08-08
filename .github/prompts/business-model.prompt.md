---
description: Dựng KPI tree từ business question, chọn bộ chỉ số ưu tiên và viết thẻ chỉ số.
argument-hint: KPI chính hoặc lĩnh vực cần phân rã
---

# /business-model — Dựng bộ chỉ số

Quyết định sẽ đo cái gì trước khi dựng mô hình: phân rã chỉ số chính thành KPI tree, chọn bộ chỉ số
ưu tiên, và mô tả từng chỉ số đủ để người khác tính lại ra cùng một con số.

## Tình huống sử dụng

Khi đã có business question và cần biết đo bằng chỉ số nào, chỉ số đó cấu thành từ đâu.

## Tình huống không nên dùng

- Viết công thức DAX trong Power BI: dùng `/build-model`.
- Làm rõ yêu cầu báo cáo: dùng `/gather-requirements`.
- Kiểm tra một con số đang nghi sai: dùng `/check`.

## Yêu cầu đầu vào

1. `knowledge/reports/*/business-questions.md`: trục để quyết định giữ hay bỏ một nhánh.
2. `knowledge/models/*/dictionary.md`: để biết công thức có trường dữ liệu thật hay không.
3. `org-context/glossary.md`: tên chỉ số phải dùng đúng cách gọi đã thống nhất.

## Các bước thực hiện

1. **Xác định chỉ số chính.** Với mỗi business question, nêu chỉ số chính cần đo và một câu lý do.
2. **Dựng bản nháp KPI tree và đánh dấu giả định.** Phân rã theo cách chỉ số được cấu thành, ví dụ
   doanh thu bằng số đơn vị bán nhân đơn giá, rồi phân rã tiếp theo các chiều phân tích có trong dữ
   liệu. Mọi dòng chưa có căn cứ trong tài liệu dự án phải ghi rõ là giả định cần xác nhận.
3. **Trình bày cây trong câu trả lời.** Bản nháp phải hiện ra trong chat để học viên phản biện, không
   ghi thẳng vào file. Một bản nháp không ai nhìn thấy thì không thu được ý kiến nào.
4. **Cắt nhánh không gắn câu hỏi.** Mỗi nhánh phải phục vụ một business question cụ thể. Nhánh không
   gắn được với câu hỏi nào thì đề xuất bỏ, kèm lý do.
5. **Xếp ưu tiên theo ba tiêu chí.** Với từng chỉ số: có bám business question không, có đo được
   không, dữ liệu hiện tại có đủ trường để tính không. Đề xuất bộ chỉ số ưu tiên và danh sách loại,
   mỗi chỉ số bị loại kèm một câu lý do.
6. **Điểm dừng phê duyệt.** Dừng lại chờ học viên chốt bộ chỉ số ưu tiên, rồi mới ghi file.
7. **Viết thẻ chỉ số.** Mỗi chỉ số ưu tiên một thẻ gồm năm phần: tên, định nghĩa một câu, công thức
   tính, đơn vị đo, và cách kiểm chứng (con số nào đối chiếu được với dữ liệu thực tế).
8. **Kiểm chéo Data Dictionary.** Đối chiếu mọi trường xuất hiện trong công thức với Data Dictionary.
   Trường nào chưa có thì nêu thành câu hỏi mở, không tự suy ra ý nghĩa.

## Kết quả đầu ra

- `knowledge/metrics/kpi-tree.md`: cây chỉ số, kèm danh sách nhánh đã cắt và lý do.
- `knowledge/metrics/<tên-chỉ-số>.md`: mỗi chỉ số ưu tiên một thẻ.
- Ba dòng kết thúc: Sản phẩm, Trạng thái, Bước tiếp theo.

## Ranh giới của skill

- Tự đặt định nghĩa nghiệp vụ cho một chỉ số. Định nghĩa là việc của người sở hữu chỉ số, chỗ nào
  chưa rõ thì ghi thành câu hỏi mở.
- Giữ lại nhánh phân rã không gắn với business question nào cho đủ hình thức.
- Ghi thẻ chỉ số khi học viên chưa chốt bộ ưu tiên.
- Viết công thức dùng trường dữ liệu không có trong Data Dictionary.
