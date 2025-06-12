# Giới thiệu Workflow Giám sát Website với n8n

File này mô tả chi tiết cách xây dựng một **workflow trong n8n** để **giám sát tình trạng các website**. Quy trình bao gồm:

- Lên lịch kiểm tra định kỳ (Schedule Trigger)
- Đọc danh sách tên miền từ Google Sheets
- Gửi các HTTP request để kiểm tra `sitemap.xml`, `robots.txt`, `ads.txt`, và `favicon.ico`
- Xử lý dữ liệu, phát hiện lỗi bất thường như redirect ngoài domain, nội dung rỗng, hoặc không tồn tại
- Ghi nhận kết quả vào Google Sheets
- Gửi thông báo lỗi hoặc cập nhật thành công qua Discord

Workflow được thiết kế theo logic phân nhánh với các node như `If`, `Merge`, `Set`, `Code`, và tích hợp đa dịch vụ.

https://drive.google.com/drive/folders/14MD4T_Lr7n_wGj9g16Iv7YvJVy9tVYCa?usp=drive_link
