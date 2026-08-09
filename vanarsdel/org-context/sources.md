---
type: Source Inventory
title: Danh mục nguồn dữ liệu
status: draft
---

# Danh mục nguồn dữ liệu

> Mỗi nguồn dữ liệu của dự án một dòng. Ở đây chỉ ghi **có nguồn gì, chứa gì, độ nhạy cảm**. Chi tiết khảo
> sát chất lượng (profiling) ghi ở thẻ nguồn trong `knowledge/sources/`. Không ghi mật khẩu, chuỗi kết nối.

| Nguồn | Loại | Chứa gì | Độ nhạy cảm | Thẻ chi tiết |
|---|---|---|---|---|
| VanArsdel Actuals | Excel (`VanArsdel_Actuals.xlsx`) | Bán hàng thực tế: bảng Sales và các bảng mô tả (sản phẩm, khách hàng, thời gian, chiến dịch, địa lý) | Có PII (bảng khách hàng: email, họ tên) | [knowledge/sources/vanarsdel.md](../knowledge/sources/vanarsdel.md) |
| VanArsdel Budget | CSV (`VanArsdel_Budget.csv`) | Ngân sách và dự báo doanh thu theo ngành hàng, phân khúc, tháng | Nội bộ | [knowledge/sources/vanarsdel.md](../knowledge/sources/vanarsdel.md) |
