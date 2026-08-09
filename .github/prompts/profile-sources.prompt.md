---
description: Khảo sát một nguồn dữ liệu lần đầu một cách an toàn, rồi ghi kết quả thành thẻ nguồn.
argument-hint: tên file hoặc tên bảng cần khảo sát
---

# /profile-sources — Khảo sát nguồn dữ liệu

Gặp một nguồn dữ liệu lần đầu: khảo sát chất lượng bằng các chỉ số tổng hợp, phát hiện các vấn đề
kèm bằng chứng, và kết thúc bằng một thẻ nguồn dùng lại được cho cả dự án.

Nguyên tắc xuyên suốt: giá trị thô ở lại trong file dữ liệu, chỉ cấu trúc và chỉ số tổng hợp mới
được đưa vào tài liệu.

## Tình huống sử dụng

Khi cần biết trong một nguồn dữ liệu thực tế có gì: bảng nào, cột nào, kiểu dữ liệu, mức độ thiếu,
trùng lặp, giá trị bất thường.

## Tình huống không nên dùng

- Cần một con số hoặc một lát cắt số liệu: dùng `/quick-analysis`.
- Cần làm sạch và biến đổi dữ liệu: dùng `/prepare-data`.
- Thẻ nguồn đã có và đã trả lời được câu hỏi: đọc lại thẻ, không khảo sát lại.

## Yêu cầu đầu vào

1. `knowledge/sources/` trước tiên. Nếu đã có thẻ cho nguồn này, đọc thẻ và báo lại, chỉ khảo sát
   phần còn thiếu.
2. `org-context/glossary.md`: thuật ngữ nghiệp vụ, để gọi tên các trường cho đúng.
3. Tài liệu nghiệp vụ của dự án nếu có, để biết trường nào quan trọng với bài toán.

Học viên phải nói rõ khảo sát nguồn nào. Không tự chọn nguồn thay học viên.

## Các bước thực hiện

1. **Nhận diện dữ liệu cá nhân trước khi đọc dữ liệu.** Liệt kê các trường có khả năng là dữ liệu
   cá nhân: họ tên, email, số điện thoại, địa chỉ, mã định danh cá nhân. Báo danh sách này cho học
   viên trước khi làm bất cứ việc gì khác.
2. **Khảo sát bằng chỉ số tổng hợp.** Với mỗi bảng: số dòng, danh sách cột và kiểu dữ liệu, tỷ lệ ô
   trống theo cột, số giá trị phân biệt, số dòng trùng lặp, khoảng giá trị của các cột số và cột
   ngày. Chỉ dùng số tổng hợp, không trích giá trị thô của các trường cá nhân.
3. **Nêu vấn đề kèm bằng chứng.** Mỗi vấn đề chất lượng ghi kèm bằng chứng đếm được: bao nhiêu dòng,
   ở cột nào. Không có bằng chứng thì không ghi thành vấn đề.
4. **Chốt mốc số liệu.** Với mỗi bảng sẽ dùng, ghi lại số dòng, một cột số chính kèm tổng của cột
   đó, và khoảng thời gian nếu bảng có cột ngày. Chốt các số này **trước khi dữ liệu bị làm sạch hay
   biến đổi**, vì đây là bộ số duy nhất để đối chiếu về sau. Chỉ ghi số tổng hợp, không ghi giá trị
   của từng dòng.
5. **Điểm dừng phê duyệt.** Trình bày danh sách vấn đề và đề xuất tối đa 10 quy tắc chất lượng dữ liệu, dừng
   lại chờ học viên chọn quy tắc nào giữ lại. Chỉ giữ những vấn đề ảnh hưởng tới câu hỏi phân tích
   của dự án.
6. **Ghi thẻ nguồn.** Ghi vào `knowledge/sources/<tên-nguồn>.md` với bốn phần: thông tin nguồn (tên
   file, cách lấy, thời điểm khảo sát), bảng cấu trúc từng bảng và cột, danh sách quy tắc chất lượng
   dữ liệu đã chốt, và bảng "Dùng gì từ nguồn này" liệt kê các bảng sẽ dùng cho bài toán.
7. **Nêu phần không dùng.** Với mỗi bảng không đưa vào bảng "Dùng gì từ nguồn này", ghi một dòng lý
   do. Không im lặng bỏ qua.

## Kết quả đầu ra

- Một thẻ nguồn trong `knowledge/sources/`, có mục mốc số liệu điền đầy đủ.
- Bản khảo sát chi tiết, nếu dài, ghi vào `work/`. Không đưa vào thẻ.
- Ba dòng kết thúc: Sản phẩm, Trạng thái, Bước tiếp theo.

## Ranh giới của skill

- Trích giá trị thô của trường dữ liệu cá nhân vào thẻ nguồn, vào file khác, hoặc vào câu trả lời.
  Khi học viên yêu cầu, từ chối và đề xuất phương án thay thế: báo chỉ số tổng hợp, hoặc che trường.
- Kết luận về chất lượng dữ liệu khi chưa đếm được bằng chứng.
- Chốt mốc số liệu sau khi dữ liệu đã bị làm sạch. Mốc chốt muộn không còn là mốc độc lập.
- Ghi đè một thẻ nguồn đã có khi chưa được học viên duyệt.
