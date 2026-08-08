---
description: Kiểm chứng một con số, một measure, một mô hình hoặc một file trước khi chia sẻ, và kết luận đạt hay lệch kèm bằng chứng.
argument-hint: đối tượng cần kiểm chứng, ví dụ measure Doanh thu
---

# /check — Kiểm chứng

Kiểm tra một thứ có đúng không, và kết luận bằng bằng chứng đối chiếu được. Skill này chỉ kết luận,
không tự sửa.

## Tình huống sử dụng

Khi cần biết một con số, một measure, một mối quan hệ trong model, hoặc một file có đúng và có an
toàn để chia sẻ hay không.

## Tình huống không nên dùng

- Sửa lỗi vừa phát hiện: quay lại skill đã tạo ra nó, ví dụ `/build-model` cho measure sai.
- Rà soát toàn bộ dự án trước một cửa nghiệm thu: dùng `/review`.
- Tạo mới một measure: dùng `/build-model`.

## Bốn mặt kiểm chứng

| Mặt | Kiểm cái gì |
|---|---|
| Dữ liệu | Số dòng, mức chi tiết, giá trị thiếu, đối chiếu với nguồn |
| Mô hình | Mối quan hệ, chiều lọc, số liệu có bị nhân đôi không |
| Công thức | Measure so với một con số tính độc lập |
| An toàn | Dữ liệu cá nhân và thông tin nhạy cảm còn sót trước khi chia sẻ |

Ba mức độ sâu: kiểm nhanh (đạt hoặc lệch), kiểm chuẩn (đối chiếu có bằng chứng, mặc định), truy
nguyên (tìm nguyên nhân gốc của một con số sai).

## Yêu cầu đầu vào

1. Đối tượng cần kiểm chứng, do học viên nêu rõ. Không tự chọn thay.
2. Thẻ chỉ số trong `knowledge/metrics/`: định nghĩa và cách kiểm chứng đã ghi.
3. Một mốc đối chiếu độc lập: số liệu trong thẻ nguồn, bản ghi xử lý, hoặc con số tính trực tiếp từ
   file dữ liệu gốc.

## Các bước thực hiện

1. **Trình bày kế hoạch kiểm chứng trước khi chạy.** Nêu ba thứ: kiểm mặt nào, điều gì được coi là
   đúng (con số kỳ vọng hoặc mức sai lệch chấp nhận được), và lấy mốc đối chiếu độc lập từ đâu.
2. **Đối chiếu với nguồn độc lập, không tự chấm bài của mình.** Không được lấy chính công thức đang
   kiểm chứng chạy lại lần hai rồi kết luận là đúng. Mốc đối chiếu phải đến từ nơi khác: file dữ liệu
   gốc, bản ghi xử lý, hoặc một cách tính khác.
3. **Chạy ở chế độ chỉ đọc.** Không sửa model, không sửa dữ liệu, không sửa file trong khi kiểm chứng.
4. **Lập bảng kết quả.** Mỗi dòng một hạng mục: tên hạng mục, giá trị đang có, giá trị đối chiếu, kết
   luận đạt hoặc lệch, nguồn của mốc đối chiếu. Hạng mục nào không kiểm được thì ghi rõ là chưa kiểm
   được và nêu lý do, không im lặng bỏ qua.
5. **Truy nguyên khi lệch.** Với mỗi dòng lệch, chỉ ra tầng nào sai: dữ liệu nguồn, bước làm sạch,
   mối quan hệ trong model, hay công thức. Nêu bằng chứng cho kết luận đó.
6. **Bàn giao, không tự sửa.** Kết thúc bằng đề xuất bước sửa và skill tương ứng, để học viên quyết
   định. Việc sửa thuộc về lượt làm việc sau.

## Kết quả đầu ra

- Bảng kết quả kiểm chứng, ghi vào `knowledge/models/<tên-mô-hình>/test-log.md` khi học viên yêu cầu
  lưu lại.
- Ba dòng kết thúc: Sản phẩm, Trạng thái, Bước tiếp theo.

## Ranh giới của skill

- Sửa bất cứ thứ gì trong lượt kiểm chứng.
- Kết luận đạt mà không nêu được mốc đối chiếu độc lập.
- Bỏ qua một hạng mục không kiểm được mà không ghi lý do.
- Đưa giá trị của trường dữ liệu cá nhân vào bảng kết quả.
