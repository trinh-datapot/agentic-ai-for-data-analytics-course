# Buổi 1 — Tạo báo cáo HTML đầu tiên

## Nội dung thư mục

- `sales_adventureworks.csv`: dữ liệu bán hàng mẫu (AdventureWorks đã Việt hóa), mỗi dòng
  là một dòng hàng trong đơn.
- `context-adventureworks/`: tài liệu ngữ cảnh cho agent đọc trước khi làm việc.
  - `01-nghiep-vu.md`: bối cảnh nghiệp vụ.
  - `02-du-lieu.md`: mô tả dữ liệu, ý nghĩa từng cột.
  - `03-yeu-cau-bao-cao.md`: câu hỏi kinh doanh cần trả lời.

## Phần thực hành (LAB)

Mở thư mục `day-1` này trong VSCode, rồi giao cho agent prompt:

> đọc thư mục `context-adventureworks` và dựng report HTML trả lời các câu hỏi
> trong `03-yeu-cau-bao-cao.md`

Sản phẩm cuối: một trang báo cáo HTML mở được trên trình duyệt, mỗi câu hỏi một biểu đồ,
số liệu đã kiểm chứng.

## Nguyên tắc

Luôn kiểm chứng con số agent tạo ra (đối chiếu với dữ liệu thực tế) theo vòng lặp
Plan-Do-Check-Adjust. Ví dụ mốc kiểm chứng: tổng doanh thu toàn file khoảng 2.407.533.
