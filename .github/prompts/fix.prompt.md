---
description: Cập nhật sản phẩm đang chạy khi yêu cầu, đối tượng sử dụng hoặc nguồn dữ liệu thay đổi, kèm kiểm thử hồi quy.
argument-hint: thay đổi cần xử lý
---

# /fix — Xử lý một thay đổi trên sản phẩm đang chạy

Áp một thay đổi vào dự án đã bàn giao mà không phá vỡ những gì đang chạy: xác định phạm vi lan tỏa,
cập nhật tài liệu trước rồi mới tới sản phẩm, và kết thúc bằng kiểm thử hồi quy.

## Tình huống sử dụng

Khi có thay đổi về yêu cầu nghiệp vụ, về đối tượng sử dụng, hoặc về nguồn dữ liệu, và cần cập nhật
một dự án đang chạy.

## Tình huống không nên dùng

- Một thứ lẽ ra đúng mà đang sai: đó là lỗi, dùng `/check` để truy nguyên rồi sửa ở tầng gây lỗi.
- Dựng mới từ đầu: dùng skill của tầng tương ứng, `/build-model` hoặc `/build-report`.
- Chưa rõ thay đổi là gì: làm rõ với người yêu cầu trước, không đoán.

## Yêu cầu đầu vào

1. Mô tả thay đổi, càng cụ thể càng tốt: ai yêu cầu, vì sao, kỳ vọng kết quả ra sao.
2. Bộ tài liệu hiện có: `knowledge/reports/` (Report Proposal, business question, report spec),
   `knowledge/metrics/`, `knowledge/models/`, `knowledge/sources/`.
3. Với thay đổi về nguồn dữ liệu: đường dẫn nguồn mới.

## Các bước thực hiện

1. **Phân loại thay đổi trước khi làm gì khác.** Ba loại: thêm tình huống sử dụng (câu hỏi mới),
   thêm đối tượng sử dụng (cùng câu hỏi, khác mức chi tiết), hoặc thêm nguồn dữ liệu. Phân loại sai
   thì phạm vi lan tỏa ước lượng sai theo.
2. **Xác định phạm vi lan tỏa.** Lập bảng: tầng nào bị chạm, file nào phải sửa, và những gì đang chạy
   có thể bị ảnh hưởng. Đi theo thứ tự thẻ nguồn → Data Dictionary → model → measure → report spec →
   trang báo cáo. Nêu rõ tầng nào không bị chạm.
3. **Điểm dừng phê duyệt.** Trình bày bảng phạm vi lan tỏa và kế hoạch cập nhật, dừng chờ học viên
   duyệt. Không sửa bất cứ thứ gì khi chưa được duyệt.
4. **Cập nhật tài liệu trước, sản phẩm sau.** Sửa thẳng sản phẩm rồi mới quay lại tài liệu là cách
   làm hai thứ lệch nhau; sau vài lần thì không ai tin tài liệu nữa.
5. **Với thay đổi về nguồn dữ liệu, giữ nguyên tắc một thực thể một bảng dimension.** Nguồn mới có
   bảng mô tả cùng một thực thể nghiệp vụ với bảng đang có thì nối vào bảng cũ, không dựng bảng song
   song. Hai bảng cho cùng một thực thể sẽ làm số bị đếm hai lần.
6. **Kiểm thử hồi quy.** Trước khi sửa, ghi lại số hiện tại của các chỉ số chính. Sau khi sửa, chạy
   lại và đối chiếu. Mỗi chỗ đổi phải giải thích được là do thay đổi này, không phải do vỡ.
7. **Ghi lại thay đổi.** Ghi vào `knowledge/records/change-<ngày>.md`: thay đổi là gì, ai yêu cầu,
   các file đã cập nhật, và kết quả kiểm thử hồi quy.

## Kết quả đầu ra

- Tài liệu và sản phẩm đã cập nhật đồng bộ.
- `knowledge/records/change-<ngày>.md` kèm bảng kiểm thử hồi quy.
- Ba dòng kết thúc: Sản phẩm, Trạng thái, Bước tiếp theo.

## Ranh giới của skill

- Sửa sản phẩm mà không cập nhật tài liệu tương ứng.
- Báo hoàn thành khi chưa chạy kiểm thử hồi quy.
- Mở rộng phạm vi ngoài thay đổi được yêu cầu. Thấy chỗ khác đáng sửa thì ghi lại thành đề xuất, không tự làm.
- Dựng bảng dimension mới cho một thực thể nghiệp vụ đã có bảng.
