---
description: Phân tích nhanh dữ liệu của dự án và kết xuất thành một trang báo cáo HTML tự chứa.
argument-hint: câu hỏi kinh doanh cần trả lời, hoặc tên thẻ báo cáo cần dựng
---

# /quick-analysis — Phân tích nhanh và kết xuất báo cáo

Trả lời một câu hỏi kinh doanh bằng số liệu tính từ dữ liệu thực tế của dự án, và kết xuất thành
một trang HTML mở được trên trình duyệt.

## Tình huống sử dụng

Khi học viên cần một lát cắt số liệu ("doanh thu theo vùng năm nay") hoặc một trang báo cáo tổng
hợp các câu hỏi đã có trong thẻ báo cáo.

## Tình huống không nên dùng

- Hỏi định nghĩa một thuật ngữ hoặc nguồn gốc một trường dữ liệu: trả lời trực tiếp từ
  `org-context/glossary.md` và thẻ nguồn, không cần dựng báo cáo.
- Số liệu đang nghi sai: dùng `/check`.
- Dựng trang báo cáo trong Power BI: việc đó thuộc các buổi sau, không làm ở đây.

## Yêu cầu đầu vào

Trước khi tính bất kỳ số nào, đọc:

1. `org-context/org-profile.md` và `org-context/glossary.md`: doanh nghiệp là ai, thuật ngữ hiểu thế nào.
2. Thẻ nguồn trong `knowledge/sources/`: ý nghĩa từng cột và các điểm cần lưu ý của dữ liệu.
3. Thẻ chỉ số trong `knowledge/metrics/` nếu câu hỏi có liên quan tới một chỉ số đã định nghĩa.
4. Thẻ báo cáo trong `knowledge/reports/` nếu học viên chỉ định một báo cáo cụ thể.

Thiếu ngữ cảnh thì hỏi lại, không đoán.

## Các bước thực hiện

1. **Xác định phạm vi.** Nêu lại: câu hỏi nào cần trả lời, ai đọc báo cáo, dữ liệu lấy từ file nào.
2. **Nêu cách tính trước khi tính.** Với mỗi câu hỏi, nói rõ sẽ dùng cột nào, phép tính nào, lọc gì.
   Nếu một cột có điểm cần lưu ý trong thẻ nguồn, nêu ra ngay tại đây.
3. **Điểm dừng phê duyệt.** Trình bày phạm vi và cách tính, dừng lại chờ học viên xác nhận. Không kết xuất
   báo cáo khi chưa được duyệt.
4. **Tính số liệu từ dữ liệu thực tế.** Đọc trực tiếp file dữ liệu. Không ước lượng, không dùng số
   nhớ từ lượt trước.
5. **Kết xuất một trang HTML tự chứa.** Mỗi câu hỏi một biểu đồ kèm một câu nhận định. Ghi rõ tên
   file dữ liệu nguồn và thời điểm kết xuất ở cuối trang.
6. **Tự kiểm chứng.** Báo lại một mốc kiểm chứng để học viên đối chiếu: tổng của chỉ số chính trên
   toàn bộ dữ liệu, và số dòng đã đọc. Nêu rõ nếu có dòng bị loại và lý do.

## Kết quả đầu ra

- Một file HTML trong thư mục của buổi học, đặt tên theo nội dung báo cáo.
- Ba dòng kết thúc: Sản phẩm, Trạng thái, Bước tiếp theo.

## Ranh giới của skill

- Đưa giá trị của trường dữ liệu cá nhân vào báo cáo hoặc vào câu trả lời.
- Đưa vào báo cáo một con số không tính được từ dữ liệu trong repo.
- Sửa dữ liệu gốc. Mọi kết quả trung gian ghi vào `work/`.
