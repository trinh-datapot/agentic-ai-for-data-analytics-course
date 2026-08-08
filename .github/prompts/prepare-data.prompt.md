---
description: Làm sạch và biến đổi dữ liệu thô thành bộ dữ liệu sẵn sàng đưa vào mô hình, kèm bản ghi xử lý.
argument-hint: bảng hoặc file cần làm sạch
---

# /prepare-data — Làm sạch và chuẩn bị dữ liệu

Đưa dữ liệu thô về trạng thái dùng được cho phân tích: che dữ liệu cá nhân, xử lý các vấn đề chất
lượng đã ghi trong thẻ nguồn, và để lại một bản ghi xử lý đủ để người khác lặp lại được.

## Khi nào dùng

Khi đã biết dữ liệu có vấn đề gì và cần xử lý: sai kiểu dữ liệu, nhãn không thống nhất, cột gộp
nhiều thông tin, bảng dạng ma trận cần chuyển về dạng dài, dòng trùng lặp.

## Khi nào không dùng

- Chưa biết trong dữ liệu có gì: dùng `/profile-sources` trước.
- Viết công thức tính chỉ số: việc của `/build-model`.
- Chỉ cần một con số để trả lời một câu hỏi: dùng `/quick-analysis`.

## Đầu vào bắt buộc

1. Thẻ nguồn trong `knowledge/sources/`: danh sách vấn đề chất lượng dữ liệu đã ghi nhận.
2. Data Dictionary trong `knowledge/models/`: đặc biệt là cột đánh dấu dữ liệu cá nhân.
3. Business question trong `knowledge/reports/`: để biết vấn đề nào cần xử lý, vấn đề nào bỏ qua.

Không có thẻ nguồn thì dừng lại, đề xuất chạy `/profile-sources` trước.

## Các bước thực hiện

1. **Che dữ liệu cá nhân trước tiên.** Đọc cột đánh dấu dữ liệu cá nhân trong Data Dictionary, liệt
   kê các cột sẽ loại hoặc thay bằng mã ẩn danh, và làm việc đó trước mọi bước xử lý khác. Giá trị
   gốc của các cột này không được hiển thị và không được ghi ra file nào.
2. **Trình bày kế hoạch xử lý trước khi làm.** Lập bảng: mỗi dòng một bảng dữ liệu, gồm vấn đề sẽ
   xử lý, cách xử lý, và kết quả kỳ vọng sau xử lý. Nêu rõ những vấn đề cố tình không xử lý vì không
   ảnh hưởng tới business question.
3. **Cửa duyệt.** Dừng lại chờ học viên xác nhận kế hoạch. Không sửa dữ liệu khi chưa được duyệt.
4. **Thực hiện từng bước, ghi lại từng bước.** Mỗi bước xử lý ghi một dòng: bảng nào, cột nào, làm
   gì, số dòng bị ảnh hưởng.
5. **Đối chiếu sau xử lý.** Với mỗi bảng đã xử lý, báo hai con số để học viên kiểm chứng: số dòng
   trước và sau, và tổng của một cột số chính trước và sau. Chênh lệch nào cũng phải giải thích được.
6. **Ghi bản ghi xử lý.** Ghi vào `knowledge/models/<tên-mô-hình>/prep-log.md`: danh sách các bước đã
   làm, các con số đối chiếu, và các vấn đề cố tình bỏ qua kèm lý do.

## Sản phẩm ra

- Bộ dữ liệu đã làm sạch, ghi vào `data/clean/`. Dữ liệu gốc trong `data/raw/` giữ nguyên.
- Bản ghi xử lý trong `knowledge/models/<tên-mô-hình>/prep-log.md`.
- Ba dòng kết thúc: Sản phẩm, Trạng thái, Bước tiếp theo.

## Không được làm

- Đọc, hiển thị hoặc ghi ra giá trị gốc của trường dữ liệu cá nhân.
- Sửa đè lên file dữ liệu gốc trong `data/raw/`.
- Làm sạch tràn lan những vấn đề không ảnh hưởng tới business question của dự án.
- Xử lý dữ liệu mà không ghi lại bước xử lý. Một bước không ghi lại là một bước không lặp lại được.
