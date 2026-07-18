---
type: Report
title: Báo cáo tổng quan doanh thu
description: Báo cáo HTML trả lời 3 câu hỏi doanh thu cho ban quản lý kinh doanh.
domain: sales
owner: ban quản lý kinh doanh
status: proposed
timestamp: 2026-07-18
---

# Báo cáo: Tổng quan doanh thu

## Ai đọc, quyết định gì
- Người đọc: ban quản lý kinh doanh (không chuyên kỹ thuật).
- Quyết định cần hỗ trợ: nên tập trung nguồn lực vào nhóm sản phẩm và thị trường nào.

## Câu hỏi cần trả lời
1. Doanh thu theo nhóm sản phẩm (`Cat`) và theo vùng (`Rgn`).
2. Xu hướng doanh thu theo tháng (dựa trên `Dt`).
3. Top 5 thành phố theo doanh thu (`City`).

## Định dạng mong đợi
- Một trang HTML tự chứa, mở được trên trình duyệt, mỗi câu hỏi một biểu đồ.
- Số liệu tính từ đúng dữ liệu trong file, không bịa số; nếu thiếu hoặc không rõ thì nêu ra.
- Ghi rõ nguồn dữ liệu (`sales_adventureworks.csv`) trong báo cáo.

## Chỉ số dùng
- [Doanh thu](../metrics/doanh-thu.md) (dùng cột `Amount`).
