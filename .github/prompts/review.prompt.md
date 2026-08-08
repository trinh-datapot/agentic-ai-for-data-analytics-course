---
description: Rà soát đối kháng toàn bộ dự án trước một cửa nghiệm thu, kết luận đi tiếp hay dừng.
argument-hint: phạm vi cần rà soát, ví dụ toàn bộ dự án trước Checkpoint 1
---

# /review — Rà soát trước cửa nghiệm thu

Rà soát toàn bộ một phần việc trước khi nó được chấp nhận, với thái độ tìm lỗi chứ không tìm cách
xác nhận là ổn. Skill này chỉ nêu phát hiện và kết luận, không sửa.

## Tình huống sử dụng

Trước một cửa nghiệm thu: chuyển giai đoạn, bàn giao cho người khác, hoặc trước khi báo cáo được
đưa ra ngoài.

## Tình huống không nên dùng

- Kiểm chứng một con số hoặc một measure cụ thể: dùng `/check`.
- Sửa lỗi vừa phát hiện: dùng skill tương ứng với tầng bị lỗi.
- Rà soát khi chưa có gì để rà: hoàn thành phần việc trước đã.

## Một luật bắt buộc

Người dựng không phải là người đánh giá bản dựng của chính mình. Khi rà soát, agent phải rà lại từ
đầu bằng bằng chứng trong file và trong model, không được dựa vào lý do đã đưa ra lúc dựng. Nếu một
phát hiện chỉ dựa trên "lúc trước đã làm đúng rồi", phát hiện đó không có giá trị.

## Yêu cầu đầu vào

1. Checklist hoặc tiêu chí của cửa nghiệm thu đang hướng tới.
2. Toàn bộ sản phẩm trong phạm vi rà soát: kho ngữ cảnh, thẻ nguồn, Data Dictionary, thẻ chỉ số, thẻ
   mô hình, bản ghi xử lý, bảng kết quả kiểm chứng.

## Các bước thực hiện

1. **Chốt phạm vi và các mặt sẽ rà.** Trình bày: rà những gì, theo checklist nào, và bốn mặt sẽ đi
   qua. Dừng lại chờ học viên xác nhận phạm vi trước khi đọc dữ liệu và model.
2. **Rà từng mặt, mỗi mặt một lượt sạch.** Bốn mặt: dữ liệu và tài liệu nguồn, mô hình và mối quan
   hệ, công thức và số liệu, tính đầy đủ của tài liệu. Mỗi lượt bắt đầu lại từ bằng chứng, không dùng
   kết luận của lượt trước.
3. **Lọc theo bằng chứng.** Một phát hiện chỉ được giữ lại khi dẫn được bằng chứng cụ thể: tên file
   và dòng, tên bảng hoặc measure, hoặc một con số so với một mốc đối chiếu độc lập. Phát hiện không
   dẫn được bằng chứng thì bỏ, không ghi vào danh sách.
4. **Xếp theo mức nghiêm trọng.** Giữ tối đa 15 phát hiện, nặng nhất lên đầu. Mỗi phát hiện ghi:
   vấn đề, bằng chứng, hậu quả nếu bỏ qua, và skill nên dùng để sửa.
5. **Kết luận bằng một trong ba mức.** Đi tiếp, thận trọng, hoặc dừng lại. Không dùng đạt hoặc không
   đạt, vì quyết định cuối cùng thuộc về học viên chứ không thuộc về agent.
6. **Không sửa gì.** Kết thúc bằng danh sách phát hiện và đề xuất thứ tự xử lý.

## Kết quả đầu ra

- Báo cáo rà soát ghi vào `knowledge/records/review-<ngày>.md`: phạm vi, danh sách phát hiện kèm bằng
  chứng, kết luận ba mức.
- Ba dòng kết thúc: Sản phẩm, Trạng thái, Bước tiếp theo.

## Ranh giới của skill

- Sửa bất cứ thứ gì trong lượt rà soát.
- Giữ lại một phát hiện không dẫn được bằng chứng.
- Kết luận đi tiếp khi còn phát hiện ở mức nghiêm trọng chưa được xử lý.
- Dựa vào lý do đã đưa ra lúc dựng để kết luận là đúng.
