---
type: Source
title: Nguồn dữ liệu bán hàng AdventureWorks
description: Bảng bán hàng phẳng, mỗi dòng một dòng hàng trong đơn.
domain: sales
owner: ban quản lý kinh doanh
status: governed
file: ../../sales_adventureworks.csv
signed_off: {by: giảng viên Datapot, date: 2026-07-18}
timestamp: 2026-07-18
---

# Nguồn: sales_adventureworks.csv

## Tổng quan
- File: `sales_adventureworks.csv` (CSV, mã hóa UTF-8), nằm ở thư mục `day-1/`.
- Số dòng: 7.496. Mỗi dòng là **một dòng hàng trong một đơn** (`SOID` có thể lặp lại).
- Khoảng thời gian: 2022-01-01 đến 2025-06-28.
- Quy mô: 844 khách hàng, 10 nhân viên bán hàng.
- **Mốc kiểm chứng:** tổng doanh thu toàn file ≈ 2.407.533.

## Ý nghĩa các cột

| Cột | Ý nghĩa | Kiểu | Ghi chú |
|---|---|---|---|
| `SOID` | Mã đơn hàng | text | một đơn có thể có nhiều dòng hàng |
| `Dt` | Ngày đặt hàng | ngày | 2022-01-01 đến 2025-06-28 |
| `CustID` | Mã khách hàng | text | 844 khách hàng |
| `Gen` | Giới tính khách hàng | text | F, M |
| `Ctry` | Quốc gia | text | 6 nước: United States, United Kingdom, Germany, Canada, France, Australia |
| `Rgn` | Vùng | text | 10 giá trị. **Lưu ý:** không đồng cấp, với United States là vùng con (Northwest, Southwest...), với các nước khác `Rgn` trùng tên nước |
| `City` | Thành phố | text | |
| `Grp` | Nhóm châu lục | text | North America, Europe, Pacific |
| `Prod` | Tên sản phẩm | text | |
| `SubCat` | Loại sản phẩm | text | 19 loại (Tires, Bottles, Helmets, Road Bikes...) |
| `Cat` | Nhóm sản phẩm | text | Accessories, Clothing, Bikes, Components |
| `Color` | Màu sản phẩm | text | **"Không"** nghĩa là sản phẩm không có thuộc tính màu, không phải thiếu dữ liệu |
| `Qty` | Số lượng | số nguyên | |
| `UPrice` | Đơn giá bán thực tế | số | thấp hơn `ListUPrice` khi có chiết khấu |
| `ListUPrice` | Đơn giá niêm yết | số | giá gốc trước chiết khấu |
| `DiscPct` | Tỷ lệ chiết khấu | số (0 đến 1) | |
| `DiscAmount` | Số tiền chiết khấu | số | |
| `UCost` | Giá vốn đơn vị | số | |
| `Amount` | Doanh thu dòng hàng | số | bằng `Qty` nhân `UPrice`, đã đối chiếu đúng toàn bộ dữ liệu |
| `Channel` | Kênh bán | text | Đại lý, Online, Cửa hàng |
| `Payment` | Hình thức thanh toán | text | Thẻ, Chuyển khoản, Tiền mặt |
| `ShipMode` | Phương thức giao | text | Tiêu chuẩn, Nhận tại cửa hàng, Giao nhanh |
| `Campaign` | Chiến dịch khuyến mãi | text | Không, Giữa năm, Tết, Black Friday |
| `SalesRep` | Nhân viên bán hàng | text | 10 người, là **dữ liệu cá nhân (PII)** |
| `Segment` | Phân khúc khách hàng | text | Thường, VIP, Mới |
| `CustType` | Loại khách hàng | text | Cá nhân, Doanh nghiệp |
| `CustSince` | Khách hàng từ năm | số (năm) | 2018 đến 2024, là năm chứ không phải ngày |

## Điểm cần lưu ý (kiểm chứng trước khi dùng)
- **Không có sẵn cột lợi nhuận.** Lợi nhuận gộp một dòng phải tự tính: `Amount` trừ `Qty` nhân `UCost`.
- **"Theo vùng" cần thống nhất:** dùng `Rgn` hay `Grp`, vì `Rgn` không đồng cấp giữa các nước.
- `SalesRep` là dữ liệu cá nhân (PII), không đưa lên báo cáo công khai.
- Giá trị phân loại đã Việt hóa, tên cột viết tắt tiếng Anh.
