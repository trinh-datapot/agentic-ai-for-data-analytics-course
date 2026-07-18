# Buổi 1 — Tạo báo cáo HTML đầu tiên

## Nội dung thư mục

- `sales_adventureworks.csv`: dữ liệu bán hàng mẫu (AdventureWorks đã Việt hóa), mỗi dòng
  là một dòng hàng trong đơn.
- `org-context/`: **ngữ cảnh khai báo** (doanh nghiệp cho agent biết trước khi làm việc).
  - `org-profile.md`: doanh nghiệp là ai, phân tích lĩnh vực gì, ngôn ngữ.
  - `glossary.md`: các thuật ngữ kinh doanh.
  - `sources.md`: danh mục nguồn dữ liệu.
- `knowledge/`: **tri thức đã kiểm chứng**, ghi dưới dạng thẻ (card).
  - `sources/sales-adventureworks.md`: thẻ nguồn, ý nghĩa từng cột, điểm cần lưu ý.
  - `metrics/doanh-thu.md`: thẻ chỉ số doanh thu (cột `Amount`).
  - `reports/bao-cao-doanh-thu-tong-quan.md`: thẻ báo cáo, các câu hỏi cần trả lời.
- `handout/`: tài liệu tổng hợp phát cho học viên sau buổi.
  - `day-1-takeaway.html`: bản tóm tắt Buổi 1, mở trực tiếp bằng trình duyệt.

## Phần thực hành (LAB)

Mở thư mục `day-1` này trong VSCode, rồi giao cho agent prompt:

> đọc thư mục `org-context` và `knowledge`, rồi dựng report HTML trả lời các câu hỏi
> trong `knowledge/reports/bao-cao-doanh-thu-tong-quan.md`

Sản phẩm cuối: một trang báo cáo HTML mở được trên trình duyệt, mỗi câu hỏi một biểu đồ,
số liệu đã kiểm chứng.

## Nguyên tắc

Luôn kiểm chứng con số agent tạo ra (đối chiếu với dữ liệu thực tế) theo vòng lặp
Plan-Do-Check-Adjust. Mỗi con số phải truy được về nguồn. Ví dụ mốc kiểm chứng: tổng doanh
thu toàn file khoảng 2.407.533.
