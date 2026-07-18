---
type: OrgProfile
title: AdventureWorks (dữ liệu mẫu khóa học)
description: Hồ sơ tổ chức mẫu cho phần thực hành Buổi 1, bán lẻ xe đạp.
response_language: vi
doc_language: vi
domains: [sales]
owner: giảng viên Datapot
status: sample
timestamp: 2026-07-18
---

# Hồ sơ tổ chức: AdventureWorks (dữ liệu mẫu)

## Doanh nghiệp
AdventureWorks là doanh nghiệp mẫu chuyên **bán lẻ xe đạp và phụ kiện xe đạp**, bán ở nhiều
quốc gia, qua nhiều kênh, có các chương trình khuyến mãi theo mùa. Dữ liệu đã được Việt hóa.

## Cách dữ liệu sinh ra
- Mỗi lần khách mua tạo một **đơn hàng** (`SOID`); một đơn gồm nhiều **dòng hàng**, mỗi dòng
  hàng là một dòng dữ liệu.
- Sản phẩm chia bốn nhóm: Bikes, Components, Clothing, Accessories.
- Bán qua ba kênh: Đại lý, Online, Cửa hàng.
- Khuyến mãi theo chiến dịch: Tết, Giữa năm, Black Friday, và các đơn ngoài chiến dịch.

## Lĩnh vực phân tích (domains)
- `sales`: doanh thu bán hàng theo sản phẩm, vùng và thời gian.

## Ngôn ngữ
- Trả lời người dùng: tiếng Việt.
- Tài liệu: tiếng Việt (phục vụ khóa học).

## Người phụ trách nghiệp vụ
- Ban quản lý kinh doanh (mô phỏng), là người quyết định và ký duyệt kết quả.
