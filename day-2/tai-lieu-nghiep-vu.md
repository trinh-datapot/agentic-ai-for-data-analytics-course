# Tài liệu nghiệp vụ — Công ty VanArsdel

> **Vai trò tài liệu:** đây là tài liệu bối cảnh dự án cho khóa AI for Data Analytics. Từ buổi 2, học viên
> dùng AI để **tóm tắt tài liệu này thành business requirement có kiểm chứng** (mỗi ý dẫn nguồn về đúng mục
> bên dưới), **rút thuật ngữ cho Business Glossary**, và làm nền cho việc chuẩn bị dữ liệu ở các buổi sau.
>
> **Dataset đi kèm:** thư mục `VanArsdel_advanced_dataset`, gồm `VanArsdel_Actuals.xlsx` (dữ liệu bán hàng
> thực tế) và `VanArsdel_Budget.csv` (ngân sách và dự báo).

---

## 1. Về công ty VanArsdel

VanArsdel Ltd là một doanh nghiệp hàng tiêu dùng hoạt động trên thị trường Mỹ. Công ty vừa **sản xuất** các
dòng sản phẩm mang thương hiệu VanArsdel, vừa **bán lẻ** trực tiếp tới người tiêu dùng. Toàn bộ sản phẩm bán
ra đều do chính VanArsdel làm ra, công ty không phân phối hàng của các hãng khác.

Hoạt động bán hàng diễn ra chủ yếu qua **kênh trực tuyến**. Mỗi lần một khách mua một sản phẩm đều được ghi
nhận thành một giao dịch, kèm theo sản phẩm nào được mua, khách nào mua, mua vào thời điểm nào, và chiến dịch
tiếp thị nào đã dẫn khách tới giao dịch đó. Cách ghi nhận chi tiết tới từng đơn vị sản phẩm cho phép công ty
theo dõi bức tranh bán hàng ở mức rất chi tiết, đồng thời tổng hợp lên các mức cao hơn khi cần.

Công ty đã hoạt động và tích lũy dữ liệu bán hàng qua nhiều năm, đủ dài để phân tích xu hướng theo thời gian
và so sánh giữa các giai đoạn.

## 2. Sản phẩm và danh mục

Sản phẩm của VanArsdel là các model có tên riêng, ví dụ các model thuộc dòng "Maximus". Để quản lý một danh
mục nhiều sản phẩm, công ty phân loại mỗi sản phẩm theo hai cấp:

- **Nhóm ngành hàng (Category):** năm nhóm gồm Accessory, Mix, Rural, Urban, Youth. Nhóm ngành hàng thể hiện
  định hướng sử dụng của sản phẩm và nhóm khách mà sản phẩm hướng tới.
- **Phân khúc (Segment):** chi tiết hơn nhóm ngành hàng, gồm các phân khúc như Accessory, All Season,
  Convenience, Extreme, Moderation, Productivity, Regular, Select, Youth. Phân khúc giúp công ty nhìn danh
  mục ở mức tinh hơn khi lập kế hoạch và đánh giá kết quả.

Mỗi sản phẩm gắn với hai mức giá: **giá vốn** là chi phí công ty bỏ ra cho một đơn vị sản phẩm, và **giá bán**
là giá bán ra cho khách trên một đơn vị. Phần chênh lệch giữa giá bán và giá vốn là lợi nhuận công ty thu được
trên mỗi đơn vị bán ra. Đây là con số ban lãnh đạo theo dõi sát theo từng nhóm ngành hàng và phân khúc, vì nó
quyết định danh mục nào thực sự mang lại hiệu quả.

## 3. Khách hàng

Khách hàng của VanArsdel là người mua lẻ trải khắp nước Mỹ. Mỗi khách hàng có một hồ sơ gồm mã khách hàng,
thông tin liên hệ và khu vực sinh sống. Khu vực của khách được xác định qua mã bưu chính (ZIP), từ đó suy ra
thành phố, bang, vùng và địa hạt bán hàng tương ứng.

Việc gắn khách hàng với khu vực giúp công ty hiểu tập khách của mình đang tập trung ở đâu, khu vực nào mua
nhiều, và nhóm khách nào gắn với nhóm ngành hàng hay phân khúc nào. Đây là nền tảng để phân tích thị trường
theo địa lý và theo nhóm khách.

## 4. Thị trường và địa bàn bán hàng

Thị trường của VanArsdel là toàn nước Mỹ. Để quản lý bán hàng trên phạm vi rộng, công ty chia thị trường
thành ba **vùng (Region)** lớn: Central, East, West. Trong mỗi vùng lại chia nhỏ thành nhiều **địa hạt
(District)**, là đơn vị quản lý bán hàng theo địa lý.

Cách chia vùng và địa hạt giúp công ty phân bổ nguồn lực, đặt mục tiêu và đánh giá kết quả bán hàng theo từng
khu vực, thay vì chỉ nhìn con số tổng của cả nước.

## 5. Kênh bán hàng và tiếp thị

Vì bán chủ yếu qua kênh trực tuyến, VanArsdel đầu tư nhiều vào tiếp thị để đưa khách tới nơi mua và tạo ra
đơn hàng. Mỗi giao dịch bán hàng được gắn với một **chiến dịch (Campaign)**, cho biết khách đã đến từ đâu.
Một chiến dịch là tổ hợp của hai yếu tố:

- **Kênh tiếp thị:** cách khách tiếp cận công ty, gồm Organic Search (khách tự tìm thấy qua công cụ tìm kiếm),
  SEO, SEM, SMO, Banner, Email, Mail, và Affiliate (kênh liên kết, do đối tác giới thiệu).
- **Thiết bị:** thiết bị khách dùng khi mua, gồm Desktop, Mobile, Tablet, và Paper (đặt hàng theo hình thức
  ngoại tuyến).

Nhờ gắn mỗi đơn hàng với một chiến dịch, công ty biết được kênh nào và thiết bị nào mang lại nhiều đơn hàng.
Thông tin này là cơ sở để quyết định phân bổ ngân sách tiếp thị sao cho hiệu quả.

## 6. Chu kỳ kế hoạch và ngân sách

Hằng năm, VanArsdel lập **kế hoạch (Forecast)** và **ngân sách (Budget)** cho doanh thu, chi tiết tới từng
nhóm ngành hàng, từng phân khúc và từng tháng trong năm. Ngân sách là mục tiêu công ty đặt ra từ đầu kỳ.

Trong và sau kỳ kinh doanh, kết quả **thực tế (Actuals)** được đối chiếu với ngân sách để xem công ty có đạt
kế hoạch hay không, nhóm ngành hàng hay phân khúc nào vượt kế hoạch, nhóm nào hụt so với dự kiến. Việc so sánh
thực tế với kế hoạch là một trong những cách đánh giá quan trọng nhất của ban lãnh đạo.

## 7. Định hướng và ưu tiên kinh doanh

VanArsdel đặt trọng tâm vào tăng trưởng doanh thu và lợi nhuận trên thị trường Mỹ. Ban lãnh đạo đặc biệt
quan tâm tới:

- Nhóm ngành hàng và phân khúc nào đang đóng góp nhiều nhất và còn dư địa tăng trưởng.
- Thị trường (vùng, bang, địa hạt) nào là trọng điểm, nơi nào cần đẩy mạnh.
- Kênh tiếp thị và thiết bị nào mang lại hiệu quả bán hàng cao để ưu tiên đầu tư.
- Mức độ bám sát giữa kết quả kinh doanh thực tế và kế hoạch, ngân sách đã đặt ra.

Những mối quan tâm này định hình cách công ty theo dõi và đánh giá hoạt động bán hàng, và cũng là điểm khởi
đầu để xác định các báo cáo và phân tích mà đội ngũ dữ liệu cần xây dựng.
