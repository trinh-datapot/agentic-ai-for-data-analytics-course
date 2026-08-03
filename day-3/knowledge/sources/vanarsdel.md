---
type: Source Card
title: "Thẻ nguồn — VanArsdel"
status: draft
domain: sales
---

# Thẻ nguồn — VanArsdel

> **Bài 3 (buổi 2).** Ghi lại kết quả **profiling** (khảo sát chất lượng dữ liệu) của nguồn VanArsdel. Mỗi
> vấn đề kèm **bằng chứng** (số dòng lỗi hoặc ví dụ giá trị sai). Chỉ giữ vấn đề thật sự ảnh hưởng tới bài
> toán. **Che PII trước khi đưa dữ liệu cho AI.** Xóa gợi ý trong ngoặc khi điền xong.

## Nguồn là gì

Hai file: `VanArsdel_Actuals.xlsx` (nhiều bảng, dữ liệu bán hàng thực tế) và `VanArsdel_Budget.csv` (ngân
sách và dự báo). Đường dẫn file xem `data/README.md`.

**Phạm vi profiling lần này:** chỉ khảo sát được `VanArsdel_Budget.csv`.
`VanArsdel_Actuals.xlsx` **không có trong máy** — `Get-ChildItem day-2/data` chỉ trả về `README.md` và
`VanArsdel_Budget.csv`; tìm `*.xlsx` toàn repo trả về 0 kết quả. Đúng như `data/README.md` ghi, file này để
ngoài repo và do giảng viên phát riêng. Vì vậy mọi ô liên quan tới Actuals dưới đây để trống, **không suy đoán**.

## Các bảng và điểm khảo sát

> Mở file, với mỗi bảng ghi số dòng và vấn đề chất lượng phát hiện (kiểu dữ liệu sai, giá trị thiếu, trùng,
> ngoại lệ, sai chính tả, khoảng trắng thừa, định dạng lạ...).

| Bảng / sheet | Số dòng | Vấn đề chất lượng phát hiện (kèm bằng chứng) |
|---|---|---|
| Sales | — | **Chưa khảo sát được:** thiếu file `VanArsdel_Actuals.xlsx` (xem mục "Nguồn là gì") |
| Product | — | Chưa khảo sát được — thiếu file Actuals |
| Customer | — | Chưa khảo sát được — thiếu file Actuals |
| Geography (Geo) | — | Chưa khảo sát được — thiếu file Actuals |
| Campaign | — | Chưa khảo sát được — thiếu file Actuals |
| Date | — | Chưa khảo sát được — thiếu file Actuals |
| Budget (CSV) | 15 dòng vật lý = 3 dòng tiêu đề phụ + 3 dòng header + **9 dòng dữ liệu**; 38 cột | Xem chi tiết B-01 → B-10 bên dưới |

### Chi tiết profiling `VanArsdel_Budget.csv`

**Cấu trúc thực tế đo được:** 15 dòng × 38 cột, phân cách `,`, kết thúc dòng CRLF (15/15), không BOM,
0 byte non-ASCII, 0 ô có dấu nháy/escape.

- Dòng 1: tiêu đề tự do `Budget Spreadsheet for VanArsdel` (1 ô có giá trị / 38)
- Dòng 2–3: rỗng hoàn toàn (0/38 ô có giá trị)
- Dòng 4: loại chỉ tiêu — `Forecast` ×12, `Budget` ×24
- Dòng 5: năm — `2016` ×24, `2015` ×12
- Dòng 6: header thật — `Category`, `Segment`, rồi 36 cột tháng (`Dec`…`Jan`, mỗi tháng lặp 3 lần)
- Dòng 7–15: 9 dòng dữ liệu

| # | Chiều | Vấn đề | Bằng chứng |
|---|---|---|---|
| B-01 | Kiểu dữ liệu / cấu trúc | File **không phải bảng phẳng** mà là bảng ma trận (pivot) với **3 tầng header** nằm ở dòng 4, 5, 6 và 3 dòng rác ở đầu; đọc thẳng bằng `read_csv` mặc định sẽ lấy dòng 1 làm header và hỏng toàn bộ | Dòng 1 chỉ có 1/38 ô có giá trị; dòng 2–3 có 0/38; header thật ở dòng 6 |
| B-02 | Kiểu dữ liệu | Không có cột định danh cho **loại chỉ tiêu, năm, tháng** — ba chiều này nằm ở tên cột. 36 cột đo lường phải unpivot về 4 cột (Category, Segment, Metric, Year, Month, Value) trước khi dùng | Cột 3–38 chỉ có tên tháng; `Dec`, `Nov`, … mỗi tháng xuất hiện **3 lần** (Counter trả về mỗi tháng = 3) |
| B-03 | Kiểu dữ liệu | Tháng lưu dạng **chữ viết tắt tiếng Anh** (`Jan`…`Dec`), không phải kiểu ngày; và **xếp giảm dần Dec → Jan**, dễ vẽ biểu đồ ngược thứ tự nếu sort theo thứ tự cột | Dòng 6: `Dec,Nov,Oct,Sep,...,Feb,Jan` |
| B-04 | Kiểu dữ liệu | Toàn bộ 324 ô đo lường (9 dòng × 36 cột) parse được sang số thực; **0 ô non-numeric**, 0 ô âm, 0 ô bằng 0 | Script kiểm tra: `non-numeric cells: 0`, `negative/zero: 0`, min = `148.08528`, max = `790160.642` |
| B-05 | Kiểu dữ liệu | Số **không làm tròn**, số chữ số thập phân không đồng nhất: 3 đến 7 chữ số | Phân bố: 3 chữ số ×11 ô, 4 ×93, 5 ×155, 6 ×44, 7 ×21. Ví dụ `44190.57888` (5), `1381.096238` (6), `1028.908721` (6), `662.79129` (5), `311.708775` (6) |
| B-06 | Kiểu dữ liệu | **Không ghi đơn vị tiền tệ** ở bất kỳ đâu trong file (không có ký hiệu `$`, không có dòng ghi chú đơn vị) | 0 byte non-ASCII, không có ký tự `$` trong file; dòng tiêu đề chỉ ghi `Budget Spreadsheet for VanArsdel` |
| B-07 | Giá trị thiếu | **0 ô thiếu** trong vùng dữ liệu (9 × 36 = 324 ô đều có giá trị) | Script: `missing cells: 0` |
| B-08 | Giá trị thiếu (mức thiết kế) | **Thiếu khối `Forecast` cho năm 2015**: có Budget 2015 + Budget 2016 + Forecast 2016, không có Forecast 2015 → không so sánh Forecast–Budget được cho 2015 | Đếm tổ hợp (loại chỉ tiêu, năm): `(Forecast, 2016)=12`, `(Budget, 2016)=12`, `(Budget, 2015)=12` |
| B-09 | Trùng lặp | **Không có dòng trùng**: 9 cặp (Category, Segment) đều duy nhất, không có khoảng trắng thừa ở hai cột khóa | Danh sách khóa: Accessory–Accessory, Mix–All Season, Mix–Productivity, Rural–Select, Urban–Convenience, Urban–Extreme, Urban–Moderation, Urban–Regular, Youth–Youth; `duplicate keys: []`; `whitespace issues: []` |
| B-10 | Trùng lặp (giá trị) | Có **33 giá trị lặp lại** giữa các ô khác nhau, trong đó **7 ô Budget 2016 trùng khít Budget 2015 cùng tháng** — nghi ngờ copy số của năm trước, cần hỏi lại nghiệp vụ chứ chưa kết luận là lỗi | 7 ô: Accessory/Accessory Jan = `52269.26591`; Rural/Select Nov = `172.2601125`; Urban/Convenience Aug = `343268.5292`; Urban/Convenience Oct = `161079.2266`; Urban/Regular Jun = `148.08528`; Urban/Regular Dec = `676.1375775`; Youth/Youth Nov = `3066.217875`. Giá trị lặp nhiều nhất: `318.271065` ×4, `311.708775` ×3, `172.2601125` ×3, `167.338395` ×3 (đều ở dòng Rural/Select) |

**Ngoại lệ (outlier).** Dùng quy tắc IQR trong từng dòng (so 36 giá trị của cùng một Category–Segment):

| Dòng | Ô ngoại lệ | Bằng chứng |
|---|---|---|
| Urban / Extreme | 6 ô, đều rơi vào **tháng 10 và 11 của cả ba khối** | Oct: `70793.03` (F2016), `73028.60` (B2016), `78244.93` (B2015); Nov: `46971.33` (F2016), `47574.88` (B2016), `45547.96` (B2015) — trong khi trung vị của dòng chỉ là `14729.71`, min `5340.80`. Tỷ lệ max/min của dòng = **14.7 lần** |
| Urban / Regular | 3 ô, đều là **tháng 10** | `2989.28` (F2016), `3060.91` (B2016), `3031.19` (B2015); trung vị dòng `676.14`, min `148.09`. Tỷ lệ max/min = **20.7 lần** |

Vì các ô này lặp lại nhất quán ở cả ba khối và cùng rơi vào tháng cuối năm, **chưa đủ bằng chứng để kết luận
là lỗi nhập liệu** — nhiều khả năng là tính mùa vụ, cần hỏi lại nghiệp vụ.

**Chênh lệch quy mô giữa các dòng (không phải lỗi, nhưng phải biết khi vẽ biểu đồ):** tổng năm chênh nhau tới
**~1.600 lần** — Urban/Moderation B2016 = `6.207.821` so với Rural/Select B2016 = `3.827`.
Đầy đủ (tổng 12 tháng): Accessory `897.093`, Mix/All Season `296.898`, Mix/Productivity `472.912`,
Rural/Select `3.827`, Urban/Convenience `2.755.536`, Urban/Extreme `252.751`, Urban/Moderation `6.207.821`,
Urban/Regular `9.980`, Youth/Youth `89.570` (đơn vị không rõ — xem B-06).

**Đối chiếu với tài liệu nghiệp vụ:** 5 giá trị Category trong file (Accessory, Mix, Rural, Urban, Youth) **khớp
đúng** danh sách ở mục 2; 9 giá trị Segment (Accessory, All Season, Convenience, Extreme, Moderation,
Productivity, Regular, Select, Youth) cũng **khớp đúng** mục 2. Tuy nhiên file chỉ có **9 cặp Category–Segment**,
tức mỗi Segment thuộc đúng một Category, không phải tích chéo 5 × 9.

## Trường dữ liệu cá nhân (PII)

> Liệt kê các trường là dữ liệu cá nhân, đã che/loại trước khi đưa cho AI.

**Kết quả quét PII trên `VanArsdel_Budget.csv`: KHÔNG phát hiện PII còn sót.**

| Mẫu quét | Số khớp | Ghi chú |
|---|---|---|
| Email (`...@....`) | 0 | — |
| Số điện thoại (`###-###-####`) | 0 | — |
| SSN (`###-##-####`) | 0 | — |
| Chuỗi 5 chữ số kiểu ZIP | 298 (**false positive**) | Tất cả nằm bên trong phần thập phân của số tiền, ví dụ `44190.57888`, không phải mã bưu chính. Đã kiểm tra thủ công, file chỉ có 2 cột chữ là `Category` và `Segment` |

File này chỉ có 2 cột định danh (Category, Segment) và 36 cột số tiền — **không có trường cá nhân nào**.

⚠️ **Cảnh báo cho bước sau:** rủi ro PII nằm ở `VanArsdel_Actuals.xlsx`, chưa quét được vì thiếu file.
`data/README.md` ghi rõ bảng khách hàng chứa **email và họ tên**; tài liệu nghiệp vụ mục 3 cũng ghi hồ sơ khách
hàng gồm **mã khách hàng, thông tin liên hệ và khu vực sinh sống (ZIP)**. Khi có file Actuals, **phải che/loại
các trường này trước khi đưa cho AI**, và quét lại ZIP thật ở bảng khách hàng/địa lý.

## Điểm cần lưu ý khi dùng dữ liệu

> Những điều dễ hiểu sai hoặc dễ tính sai nếu không biết trước.

- **Phải bỏ 5 dòng đầu khi đọc CSV.** Header thật ở dòng 6; đọc mặc định sẽ lấy dòng tiêu đề tự do làm header (B-01).
- **Phải unpivot 36 cột tháng** thành các cột Metric / Year / Month / Value; nếu không, mỗi tháng sẽ bị lẫn 3 giá trị khác nhau (Forecast 2016, Budget 2016, Budget 2015) vì tên cột trùng nhau (B-02).
- **Không so được Forecast với Budget cho năm 2015** vì không có khối Forecast 2015 (B-08).
- **Tháng xếp giảm dần Dec → Jan** và ở dạng chữ; phải map sang số tháng trước khi sort hoặc vẽ theo thời gian (B-03).
- **Không rõ đơn vị tiền tệ** và không rõ giá trị là doanh thu hay số lượng — tài liệu nghiệp vụ mục 6 nói ngân sách/kế hoạch lập cho **doanh thu**, nhưng bản thân file không ghi (B-06). Cần xác nhận trước khi cộng với dữ liệu Actuals.
- **Chênh lệch quy mô rất lớn giữa các dòng** (Urban/Moderation gấp ~1.600 lần Rural/Select); biểu đồ dùng chung trục sẽ làm mất hoàn toàn các dòng nhỏ.
- **7 ô Budget 2016 trùng khít Budget 2015** — cần hỏi nghiệp vụ xem có phải copy số năm trước không (B-10).
- **File chỉ ở mức Category × Segment × Tháng**, không có chiều Vùng/Địa hạt, Khách hàng, Chiến dịch hay Sản phẩm. Vì vậy **không thể so Actuals với Budget theo vùng, kênh hay sản phẩm** — chỉ so được theo nhóm ngành hàng, phân khúc và tháng, đúng như mô tả ở mục 6 của tài liệu nghiệp vụ.
- **Chưa profiling được Actuals**; mọi kết luận về Sales, Product, Customer, Geo, Campaign, Date phải chờ có file `VanArsdel_Actuals.xlsx`.
