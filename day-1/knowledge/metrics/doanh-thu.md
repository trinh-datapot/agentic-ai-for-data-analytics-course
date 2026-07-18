---
type: Metric
title: Doanh thu (Net Revenue)
description: Tổng giá trị bán ra, dùng cột Amount.
domain: sales
owner: ban quản lý kinh doanh
status: governed
measure_names: [Doanh thu]
signed_off: {by: giảng viên Datapot, date: 2026-07-18}
timestamp: 2026-07-18
---

# Chỉ số: Doanh thu

## Định nghĩa
Tổng giá trị bán ra của các dòng hàng. Đây là chỉ số chính để đánh giá kết quả kinh doanh
theo sản phẩm, vùng và thời gian.

## Công thức (bằng lời)
Cộng cột `Amount` của các dòng hàng thuộc phạm vi cần xem. `Amount` của một dòng bằng `Qty`
nhân `UPrice` (đơn giá bán thực tế), đã đối chiếu đúng toàn bộ dữ liệu.

## Trường hợp cần lưu ý
- Dùng `Amount`, không dùng `ListUPrice` (giá niêm yết) để tính doanh thu.
- Doanh thu khác lợi nhuận: repo này không có sẵn cột lợi nhuận.

## Kiểm chứng
- Tổng doanh thu toàn file ≈ 2.407.533 (đối chiếu khi nghi ngờ một con số tổng hợp).

## Nguồn
- [knowledge/sources/sales-adventureworks.md](../sources/sales-adventureworks.md)
