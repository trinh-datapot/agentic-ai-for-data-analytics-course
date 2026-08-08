---
description: Dựng hoặc sửa mô hình dữ liệu trong Power BI qua MCP, gồm bảng, mối quan hệ và measure DAX.
argument-hint: phần model cần dựng hoặc sửa
---

# /build-model — Dựng mô hình dữ liệu

Dựng mô hình star schema và viết measure trên model Power BI đang mở, qua cầu nối MCP. Nguyên tắc
xuyên suốt: trình bày thiết kế trong câu trả lời trước, thao tác trên model sau.

## Khi nào dùng

Khi cần tạo hoặc sửa: bảng trong model, mối quan hệ giữa các bảng, measure DAX, hoặc đánh dấu bảng
thời gian.

## Khi nào không dùng

- Làm sạch dữ liệu trước khi nạp: dùng `/prepare-data`.
- Quyết định đo chỉ số gì: dùng `/business-model`.
- Một con số đang nghi sai: dùng `/check`.

## Đầu vào bắt buộc

1. `knowledge/metrics/`: thẻ chỉ số của bộ KPI ưu tiên, gồm công thức và cách kiểm chứng.
2. `knowledge/models/*/dictionary.md`: tên bảng và tên cột thật trong dữ liệu.
3. Kết nối MCP tới đúng file `.pbix` của dự án đang mở.

## Các bước thực hiện

1. **Xác nhận đúng model trước khi làm gì khác.** Liệt kê các bảng trong model đang kết nối và hỏi
   học viên xác nhận đây đúng là model của dự án. Sai model thì mọi thao tác sau đều sai chỗ.
2. **Chốt mức chi tiết của bảng fact.** Nêu rõ một dòng trong bảng fact là gì, ví dụ một đơn vị bán
   ra, hay một dòng hàng trong đơn. Mức chi tiết sai thì mọi con số về sau đều sai.
3. **Trình bày thiết kế trong câu trả lời.** Với việc dựng model: danh sách bảng fact và dimension,
   và bảng các mối quan hệ gồm cột khóa hai bên, kiểu quan hệ, chiều lọc. Với việc viết measure:
   công thức DAX đầy đủ kèm một câu giải thích cách hoạt động.
4. **Cửa duyệt.** Dừng lại chờ học viên xác nhận thiết kế. Không thao tác lên model khi chưa được
   duyệt.
5. **Thực hiện qua MCP.** Tạo bảng, quan hệ hoặc measure đúng như thiết kế đã duyệt. Đánh dấu bảng
   thời gian là Date table nếu model có phân tích theo thời gian.
6. **Kiểm thử ngay sau khi dựng.** Chạy tối thiểu hai truy vấn: đếm số dòng bảng fact và đối chiếu
   với nguồn, và tính tổng một chỉ số theo một chiều rồi so với tổng chung. Hai tổng phải bằng nhau.
   Lệch thì báo rõ nghi ngờ nguyên nhân, thường là sai chiều lọc hoặc khóa trùng.
7. **Ghi thẻ mô hình.** Ghi vào `knowledge/models/<tên-mô-hình>/model-card.md`: danh sách bảng, bảng
   các mối quan hệ, danh sách measure kèm công thức, và kết quả hai truy vấn kiểm thử.

## Sản phẩm ra

- Model trong Power BI đã cập nhật, đã lưu file `.pbix`.
- Thẻ mô hình trong `knowledge/models/<tên-mô-hình>/model-card.md`.
- Ba dòng kết thúc: Sản phẩm, Trạng thái, Bước tiếp theo.

## Không được làm

- Thao tác lên model khi chưa xác nhận đang kết nối đúng model của dự án.
- Sửa model khi học viên chưa duyệt thiết kế.
- Báo hoàn thành khi chưa chạy truy vấn kiểm thử.
- Tạo quan hệ lọc hai chiều mà không nêu lý do và không được duyệt riêng, vì quan hệ hai chiều là
  nguyên nhân phổ biến của số liệu bị nhân đôi.
- Viết measure dùng tên bảng hoặc tên cột không có thật trong model.
