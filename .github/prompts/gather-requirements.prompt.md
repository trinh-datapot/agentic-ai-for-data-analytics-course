---
description: Biến một yêu cầu báo cáo chưa rõ ràng thành bản yêu cầu phân tích, business question và Report Proposal duyệt được.
argument-hint: yêu cầu báo cáo cần làm rõ
---

# /gather-requirements — Làm rõ yêu cầu báo cáo

Biến một yêu cầu còn chung chung thành một kế hoạch phân tích đủ rõ để bắt tay vào làm: bối cảnh
báo cáo, business question, tiêu chí nghiệm thu đo được, và phạm vi không làm.

## Khi nào dùng

Khi có một yêu cầu báo cáo nhưng chưa rõ ai dùng, phục vụ quyết định gì, và thế nào là làm xong.

## Khi nào không dùng

- Chưa chắc có nên làm báo cáo này hay không: đó là câu chuyện trao đổi với người đặt hàng trước,
  không phải việc của skill này.
- Thiết kế bố cục trang và biểu đồ: việc của các buổi trực quan hóa.
- Đã có Report Proposal được duyệt và chỉ cần sửa một chi tiết: sửa thẳng file, không chạy lại.

## Đầu vào bắt buộc

1. `org-context/org-profile.md`: business requirement của dự án.
2. `org-context/glossary.md`: mọi thuật ngữ trong bản yêu cầu phải dùng đúng cách gọi ở đây.
3. `knowledge/models/*/dictionary.md` và `knowledge/sources/`: để biết dữ liệu có gì, phục vụ bước
   kiểm tra tính khả thi ở cuối.

## Các bước thực hiện

1. **Ghi lại yêu cầu nguyên văn.** Chép lại yêu cầu học viên đưa, không diễn giải, để về sau đối
   chiếu được bản kế hoạch với yêu cầu gốc.
2. **Dựng bối cảnh báo cáo, bốn thành phần.** Đối tượng sử dụng, tình huống cần giải quyết, quyết
   định mà báo cáo phục vụ, kết quả kỳ vọng. Suy luận từ ngữ cảnh dự án trước, rồi trình bày để học
   viên phủ quyết nhanh, thay vì hỏi trống từng ô.
3. **Soạn bản nháp dạng đề xuất.** Mỗi ô là một đề xuất kèm một câu lý do. Ô nào không có căn cứ
   trong ngữ cảnh dự án thì đánh dấu rõ là giả định cần xác nhận, không tự điền rồi bỏ qua.
4. **Hỏi tối đa ba câu mỗi vòng.** Câu hỏi ở dạng xác nhận hoặc điều chỉnh, không hỏi lại điều mà
   tài liệu dự án đã trả lời.
5. **Viết business question.** Mỗi câu ghi rõ ba điều: ai đọc câu trả lời, phục vụ quyết định gì, đo
   bằng chỉ số nào. Câu hỏi phải đo được với dữ liệu đang có.
6. **Viết tiêu chí nghiệm thu đo được.** Mỗi tiêu chí phải kiểm tra được bằng một con số, một file,
   hoặc một trạng thái nhìn thấy. Không dùng tính từ như "trực quan", "dễ hiểu", "đầy đủ".
7. **Cửa duyệt.** Trình bày toàn bộ bản nháp trong câu trả lời trước khi ghi ra file. Chỉ ghi file
   sau khi học viên xác nhận.
8. **Kiểm tra dữ liệu có trả lời được không.** Với từng business question, đối chiếu Data Dictionary
   và thẻ nguồn: trường cần thiết có tồn tại không, mức chi tiết có đủ không, có mốc so sánh không.
   Câu nào dữ liệu chưa đáp ứng thì nêu rõ và đề xuất hai hướng: thu hẹp câu hỏi, hoặc bổ sung một
   bước chuẩn bị dữ liệu trước.

## Sản phẩm ra

- `knowledge/reports/<tên-báo-cáo>/analysis-requirement.md`: bối cảnh báo cáo bốn thành phần.
- `knowledge/reports/<tên-báo-cáo>/business-questions.md`: danh sách business question.
- `knowledge/reports/<tên-báo-cáo>/report-proposal.md`: mục tiêu, đối tượng, câu hỏi trả lời, chỉ số,
  phạm vi, phạm vi không làm, tiêu chí nghiệm thu.
- Ba dòng kết thúc: Sản phẩm, Trạng thái, Bước tiếp theo.

## Không được làm

- Tự quyết định ý nghĩa nghiệp vụ thay người đặt hàng. Chỗ nào phải đoán thì ghi rõ là giả định.
- Ghi file khi học viên chưa duyệt bản nháp.
- Viết tiêu chí nghiệm thu bằng tính từ thay vì bằng thứ đo được.
- Bỏ qua bước kiểm tra dữ liệu ở cuối. Một kế hoạch mà dữ liệu không trả lời được là kế hoạch hỏng.
