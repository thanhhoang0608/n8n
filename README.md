WORKFLOW N8N: KIỂM TRA WEBSITE & BÁO CÁO

Workflow n8n này tự động kiểm tra trạng thái website (sitemap, robots.txt, ads.txt, favicon.ico) và gửi thông báo qua Discord hoặc cập nhật Google Sheets. Giải pháp này giúp bạn chủ động giám sát sức khỏe website một cách hiệu quả.

1. Tổng quan Workflow
Workflow được thiết kế để tự động kiểm tra, xử lý và báo cáo trạng thái website.

(Tổng quan workflow - tham chiếu [Image 1] trong n8n.docx)

2. Các bước triển khai
Dưới đây là các bước chính để cấu hình workflow này trong n8n:

2.1. Lên lịch kiểm tra (Schedule Trigger)
Thiết lập node "On a schedule" để chạy workflow định kỳ (ví dụ: mỗi 30 phút).

(Tham chiếu [Image 3] trong n8n.docx)

2.2. Lấy tên miền từ Google Sheets
Sử dụng node "Google Sheets" với thao tác "Get row(s) in sheet" để đọc danh sách tên miền từ file Google Sheet của bạn.

(Tham chiếu [Image 6] trong n8n.docx)

2.3. Kiểm tra trạng thái Website (HTTP Request)
Tạo các node "HTTP Request" để kiểm tra sitemap, robots.txt, ads.txt, và favicon.ico cho từng tên miền. Đảm bảo bật "Never Error" và "Always Output Data".

(Tham chiếu [Image 8] trong n8n.docx)

2.4. Xử lý & Chuẩn hóa dữ liệu (Edit Fields & Code)
Sử dụng node "Edit Fields (Set)" để chuẩn hóa đầu ra HTTP và node "Code" để phân tích sâu hơn, xác định các trường hợp lỗi cụ thể (ví dụ: chuyển hướng sitemap bên ngoài).

(Tham chiếu [Image 13] trong n8n.docx)

(Tham chiếu [Image 17] trong n8n.docx)

2.5. Hợp nhất dữ liệu (Merge)
Sử dụng node "Merge" để kết hợp tất cả các kết quả kiểm tra vào một luồng dữ liệu duy nhất.

(Tham chiếu [Image 15] trong n8n.docx)

2.6. Phân nhánh báo cáo (If Node)
Node "If" sẽ phân nhánh workflow dựa trên việc có phát hiện lỗi hay không.

(Tham chiếu [Image 19] trong n8n.docx)

2.7. Cập nhật Google Sheets
Nếu không có lỗi, node "Google Sheets" với thao tác "Update row in sheet" sẽ cập nhật trạng thái vào file của bạn.

(Tham chiếu [Image 23] trong n8n.docx)

2.8. Gửi thông báo Discord
Các node "Discord" sẽ gửi cảnh báo (khi có lỗi) hoặc thông báo cập nhật thành công đến kênh Discord bạn chỉ định.

(Tham chiếu [Image 29] trong n8n.docx)

(Tham chiếu [Image 31] trong n8n.docx)

3. Thử nghiệm
Theo dõi luồng chạy trong n8n để xác nhận workflow hoạt động đúng với các kịch bản lỗi và không lỗi.

(Luồng khi có lỗi - tham chiếu [Image 33] trong n8n.docx)

(Luồng khi không có lỗi - tham chiếu [Image 34] trong n8n.docx)
