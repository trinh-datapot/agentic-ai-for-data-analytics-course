# Nghiệp vụ

## Doanh nghiệp
AdventureWorks là một doanh nghiệp mẫu (của Microsoft, ở đây đã Việt hóa dữ liệu) chuyên **bán lẻ
xe đạp và phụ kiện xe đạp**. Doanh nghiệp bán hàng ở nhiều quốc gia, qua nhiều kênh, và có các
chương trình khuyến mãi theo mùa.

## Cách doanh nghiệp bán hàng (cách dữ liệu sinh ra)
- Mỗi lần khách mua hàng tạo ra một **đơn hàng**; một đơn có thể gồm nhiều **dòng hàng** (mỗi dòng
  là một sản phẩm trong đơn). Mỗi dòng hàng là một dòng trong dữ liệu.
- Sản phẩm chia theo bốn nhóm: Bikes (xe đạp), Components (linh kiện), Clothing (quần áo),
  Accessories (phụ kiện).
- Bán qua ba kênh: Đại lý, Online, Cửa hàng.
- Có khuyến mãi theo chiến dịch: Tết, Giữa năm, Black Friday, và các đơn ngoài chiến dịch.
- Khách hàng chia theo phân khúc (Thường, VIP, Mới) và loại (Cá nhân, Doanh nghiệp).

## Câu hỏi nghiệp vụ quan tâm
Ban quản lý kinh doanh muốn biết bán được bao nhiêu, ở đâu, nhóm sản phẩm nào mạnh, xu hướng theo
thời gian ra sao, để quyết định tập trung nguồn lực vào sản phẩm và thị trường nào.

## Thuật ngữ nội bộ
- **Doanh thu (Amount):** giá trị bán ra của một dòng hàng, tính theo số lượng nhân đơn giá bán thực tế.
- **Giá niêm yết và giá bán:** giá niêm yết là giá gốc; giá bán thực tế thấp hơn khi có chiết khấu.
- **Chiến dịch:** đợt khuyến mãi có tên, ví dụ Tết hoặc Black Friday.
