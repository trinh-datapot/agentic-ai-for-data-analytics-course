# Yêu cầu báo cáo

## Ai đọc và quyết định gì
- **Người đọc:** ban quản lý kinh doanh (không chuyên kỹ thuật).
- **Quyết định cần hỗ trợ:** nên tập trung nguồn lực vào nhóm sản phẩm và thị trường nào, dựa trên
  doanh thu theo sản phẩm, vùng và thời gian.

## Câu hỏi kinh doanh cần trả lời
1. Doanh thu theo nhóm sản phẩm (`Cat`) và theo vùng (`Rgn`).
2. Xu hướng doanh thu theo tháng (dựa trên `Dt`).
3. Top 5 thành phố theo doanh thu (`City`).

## Định dạng kết quả mong đợi
- Một báo cáo dạng trang HTML tự chứa, mở được trên trình duyệt, mỗi câu hỏi một biểu đồ.
- Số liệu tính từ đúng dữ liệu trong file, không bịa số. Nếu có cột không rõ nghĩa hoặc dữ liệu
  thiếu thì nêu ra thay vì tự suy đoán.

## Ràng buộc và ghi chú
- Doanh thu dùng cột `Amount`.
- Nếu báo cáo cần mốc thời gian, dùng `Dt` gộp theo tháng.
- Ghi lại nguồn dữ liệu (file `sales_adventureworks.csv`) trong báo cáo, đúng nguyên tắc mỗi con số
  biết nguồn gốc.
