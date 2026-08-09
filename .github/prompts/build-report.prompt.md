---
description: Dựng hoặc sửa trang báo cáo trong Power BI theo đúng report spec đã duyệt, rồi kiểm chứng số trên trang.
argument-hint: trang cần dựng hoặc phần cần sửa
---

# /build-report — Dựng trang báo cáo

Biến report spec đã duyệt thành trang báo cáo thật trong Power BI. Nguyên tắc xuyên suốt: skill này
**thi công theo spec, không thiết kế lại**. Muốn đổi thiết kế thì quay lại `/design-report`.

## Tình huống sử dụng

Khi đã có report spec được duyệt và cần dựng trang, hoặc cần sửa một phần của trang đã dựng.

## Tình huống không nên dùng

- Chưa có report spec được duyệt: dùng `/design-report` trước.
- Muốn đổi loại biểu đồ hoặc bố cục so với spec: quay lại `/design-report`, không tự đổi ở đây.
- Sửa measure hoặc quan hệ trong model: dùng `/build-model`.
- Số trên trang nghi sai: dùng `/check`.

## Yêu cầu đầu vào

1. `knowledge/reports/*/report-spec.md` đã được duyệt. Không có spec, hoặc spec chưa duyệt, thì dừng
   lại và đề xuất chạy `/design-report` trước.
2. Kết nối MCP tới đúng dự án Power BI (`.pbip`) đang mở.
3. `knowledge/models/*/model-card.md`: tên measure và tên cột thật trong model.

## Các bước thực hiện

1. **Xác nhận đúng dự án trước khi làm gì khác.** Liệt kê các trang hiện có và hỏi học viên xác nhận
   đây đúng là báo cáo của dự án.
2. **Đọc lại spec và nêu phạm vi lượt này.** Dựng trang nào, gồm những visual nào, mỗi visual trả lời
   câu hỏi nào. Nếu spec thiếu thông tin để dựng, hỏi lại, không tự quyết thay.
3. **Điểm dừng phê duyệt.** Trình bày phạm vi và danh sách visual sẽ dựng, dừng lại chờ học viên xác
   nhận trước khi thao tác lên báo cáo.
4. **Dựng bản nháp trước, trang trí sau.** Dựng đúng bố cục và đúng loại visual theo spec, chưa chỉnh
   màu sắc và định dạng. Mục tiêu của bước này là kiểm xem trang có trả lời được câu hỏi không.
5. **Đối chiếu số trên trang với measure.** Với mỗi visual, so số hiển thị với kết quả tính trực tiếp
   từ measure. Lệch thì báo rõ, không tự sửa số bằng cách đổi bộ lọc.
6. **Áp theme và hoàn thiện định dạng** sau khi số đã đúng: màu theo quy ước, tiêu đề rõ nghĩa, định
   dạng số và đơn vị.
7. **Rà lại theo spec.** Đi từng dòng của spec cho trang này: mỗi câu hỏi trong spec có đúng một visual
   trả lời chưa. Câu nào chưa có thì nêu ra, đây là thiếu sót của bước dựng, không phải của spec.
8. **Ghi lại vào thẻ báo cáo.** Ghi vào `knowledge/reports/<tên-báo-cáo>/report-card.md`: danh sách
   trang đã dựng, mỗi trang gồm các visual và câu hỏi tương ứng, cùng kết quả đối chiếu số.

## Kết quả đầu ra

- Trang báo cáo trong dự án Power BI, đã lưu, thay đổi nằm trong `<Tên>.Report/`.
- Thẻ báo cáo trong `knowledge/reports/<tên-báo-cáo>/report-card.md`.
- Ba dòng kết thúc: Sản phẩm, Trạng thái, Bước tiếp theo.

## Ranh giới của skill

- Đổi loại biểu đồ, bố cục hoặc phạm vi so với spec đã duyệt. Đổi thiết kế thì quay lại `/design-report`.
- Dựng trang khi report spec chưa được duyệt.
- Báo hoàn thành khi chưa đối chiếu số trên trang với measure.
- Chỉnh bộ lọc của visual để số hiển thị khớp với kỳ vọng, thay vì truy nguyên chỗ lệch.
- Dựng visual dùng measure hoặc cột không có thật trong model.
