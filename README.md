# Agentic AI for Data Analytics — Repo thực hành khóa học

Repo này chứa dữ liệu, tài liệu ngữ cảnh và bộ skill cho các buổi thực hành khóa
**Agentic AI for Data Analytics** của Datapot Analytics.

## Cách dùng

1. Clone repo về máy:
   ```
   git clone https://github.com/trinh-datapot/agentic-ai-for-data-analytics-course
   ```
2. Mở **thư mục gốc** của repo bằng **VSCode** đã đăng nhập **GitHub Copilot**. Không mở riêng thư
   mục một buổi, vì bộ quy tắc và các skill nằm ở gốc repo, agent chỉ đọc được khi thư mục gốc là
   nơi làm việc.
3. Mở cửa sổ Copilot Chat và chọn chế độ **Agent**. Chế độ Ask chỉ trả lời bằng văn bản, không tạo
   được file.
4. **Đầu mỗi buổi chạy `git pull`** để nhận skill mới của buổi đó.

## Bộ khung làm việc

| Đường dẫn | Nội dung |
|---|---|
| `.github/copilot-instructions.md` | Bộ quy tắc agent luôn đọc trước khi làm việc: sáu nguyên tắc nền, khuôn mở đầu và kết thúc mỗi lượt, bản đồ thư mục |
| `.github/prompts/` | Các skill của khóa. Gõ `/<tên skill>` trong Copilot Chat để chạy |

## Skill theo buổi

| Skill | Buổi | Công việc |
|---|---|---|
| `/quick-analysis` | 1 | Phân tích nhanh và kết xuất báo cáo HTML |
| `/profile-sources` | 2 | Khảo sát nguồn dữ liệu và viết thẻ nguồn |
| `/gather-requirements` | 3 | Biến một yêu cầu chưa rõ ràng thành Report Proposal |
| `/prepare-data` | 4 | Làm sạch dữ liệu và ghi lại các bước xử lý |
| `/business-model` | 5 | Dựng KPI tree và mô tả bộ chỉ số |
| `/build-model` | 6 | Dựng mô hình dữ liệu star schema qua MCP |
| `/check` | 7 | Kiểm chứng số liệu, mô hình và công thức |
| `/review` | 8 | Rà soát toàn bộ dự án trước cửa nghiệm thu |
| `/design-report` | 9 | Chốt report spec trước khi dựng báo cáo |
| `/build-report` | 9 | Dựng trang báo cáo theo spec đã duyệt |

Mỗi skill có cùng sáu phần: tình huống sử dụng, tình huống không nên dùng, yêu cầu đầu vào,
các bước thực hiện, kết quả đầu ra, ranh giới của skill. Đọc file skill trước khi chạy để biết agent sẽ dừng lại chờ duyệt ở bước nào.

## Cấu trúc theo buổi

- `day-1/`: Buổi 1, tạo báo cáo HTML đầu tiên từ dữ liệu bán hàng AdventureWorks (demo).
- `vanarsdel/`: **Dự án thực hành trên lớp, dùng từ buổi 2 đến buổi 8.** Toàn bộ sản phẩm nằm ở đây:
  `tai-lieu-nghiep-vu.md`, `org-context/`, `knowledge/`, `data/`, `work/`. Khung dựng sẵn, bạn điền
  dần qua từng buổi. Bảng sản phẩm của từng buổi và nơi ghi nằm trong `vanarsdel/README.md`.

Từ buổi 2 trở đi không có thư mục riêng theo buổi. Mọi việc làm trong `vanarsdel/`.

## Yêu cầu công cụ

- VSCode và GitHub Copilot (đã đăng nhập).
- Power BI Desktop, dùng từ buổi 4.
- Cầu nối MCP tới Power BI, dùng từ buổi 6.

## Lưu ý về dữ liệu

Dữ liệu gốc của dự án không được commit lên repo. Các trường dữ liệu cá nhân phải được che hoặc loại
trước khi đưa dữ liệu cho agent.
