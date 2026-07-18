# Dữ liệu

## Nguồn
- File: `sales_adventureworks.csv` (một bảng phẳng, định dạng CSV, mã hóa UTF-8).
- Số dòng: 7.496. Mỗi dòng là **một dòng hàng trong một đơn** (một đơn `SOID` có thể gồm nhiều dòng).
- Khoảng thời gian: từ 2022-01-01 đến 2025-06-28.
- Quy mô: 844 khách hàng, 10 nhân viên bán hàng. Tổng doanh thu toàn file khoảng 2.407.533.

## Ý nghĩa các cột

| Cột | Ý nghĩa | Kiểu | Ghi chú |
|---|---|---|---|
| `SOID` | Mã đơn hàng | text | một đơn có thể có nhiều dòng hàng |
| `Dt` | Ngày đặt hàng | ngày | 2022-01-01 đến 2025-06-28 |
| `CustID` | Mã khách hàng | text | 844 khách hàng |
| `Gen` | Giới tính khách hàng | text | F, M |
| `Ctry` | Quốc gia | text | 6 nước: United States, United Kingdom, Germany, Canada, France, Australia |
| `Rgn` | Vùng | text | 10 giá trị. **Lưu ý:** không đồng cấp, với United States là vùng con (Northwest, Southwest, Southeast, Central...), với các nước khác `Rgn` trùng tên nước |
| `City` | Thành phố | text | |
| `Grp` | Nhóm châu lục | text | North America, Europe, Pacific |
| `Prod` | Tên sản phẩm | text | |
| `SubCat` | Loại sản phẩm | text | 19 loại (Tires, Bottles, Helmets, Road Bikes, Mountain Bikes...) |
| `Cat` | Nhóm sản phẩm | text | Accessories, Clothing, Bikes, Components |
| `Color` | Màu sản phẩm | text | **"Không"** nghĩa là sản phẩm không có thuộc tính màu (phần lớn phụ kiện), không phải thiếu dữ liệu; còn lại Black, Silver, Red, Yellow, Blue |
| `Qty` | Số lượng | số nguyên | |
| `UPrice` | Đơn giá bán thực tế | số | giá đã bán, thấp hơn `ListUPrice` khi có chiết khấu |
| `ListUPrice` | Đơn giá niêm yết | số | giá gốc trước chiết khấu |
| `DiscPct` | Tỷ lệ chiết khấu | số (0 đến 1) | |
| `DiscAmount` | Số tiền chiết khấu | số | |
| `UCost` | Giá vốn đơn vị | số | |
| `Amount` | Doanh thu dòng hàng | số | bằng `Qty` nhân `UPrice`, đã đối chiếu đúng toàn bộ dữ liệu |
| `Channel` | Kênh bán | text | Đại lý, Online, Cửa hàng |
| `Payment` | Hình thức thanh toán | text | Thẻ, Chuyển khoản, Tiền mặt |
| `ShipMode` | Phương thức giao | text | Tiêu chuẩn, Nhận tại cửa hàng, Giao nhanh |
| `Campaign` | Chiến dịch khuyến mãi | text | Không (ngoài chiến dịch), Giữa năm, Tết, Black Friday |
| `SalesRep` | Nhân viên bán hàng | text | 10 người, tên thật, là **dữ liệu cá nhân (PII)**, xử lý kỹ ở buổi S4 |
| `Segment` | Phân khúc khách hàng | text | Thường, VIP, Mới |
| `CustType` | Loại khách hàng | text | Cá nhân, Doanh nghiệp |
| `CustSince` | Khách hàng từ năm | số (năm) | 2018 đến 2024, là năm chứ không phải ngày đầy đủ |

## Điểm cần lưu ý khi phân tích (kiểm chứng trước khi dùng)
- **Không có sẵn cột lợi nhuận.** Lợi nhuận gộp một dòng phải tự tính: `Amount` trừ `Qty` nhân `UCost`.
- **"Theo vùng" cần thống nhất:** dùng `Rgn` hay `Grp`, vì `Rgn` không đồng cấp giữa các nước.
- Giá trị phân loại đã Việt hóa, còn tên cột viết tắt tiếng Anh.
- Trước khi tin một con số tổng hợp, đối chiếu lại với dữ liệu thực tế, ví dụ tổng doanh thu khoảng
  2.407.533.
