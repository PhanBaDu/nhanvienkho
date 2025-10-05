# 7. NON-FUNCTIONAL REQUIREMENTS AND OTHERS

## Performance

| No. | Requirement |
|-----|-------------|
| 1. | Hệ thống phải hỗ trợ tối thiểu 1000 người dùng truy cập đồng thời mà không ảnh hưởng đến hiệu suất |
| 2. | Thời gian phản hồi API trung bình phải dưới 200ms cho các thao tác đơn giản (xem sách, giỏ hàng, tìm kiếm) |
| 3. | Thời gian tải trang không vượt quá 3 giây với kết nối internet tốc độ trung bình |
| 4. | Thời gian xử lý thanh toán và đặt hàng không vượt quá 5 giây |
| 5. | Real-time chat hỗ trợ khách hàng có độ trễ tối đa 1 giây (sử dụng Socket.IO) |
| 6. | Tính năng "đọc thử" sách phải tải nhanh với độ trễ tối đa 2 giây |

## Scalability

| No. | Requirement |
|-----|-------------|
| 1. | Database PostgreSQL phải có khả năng lưu trữ tối thiểu 50,000 đầu sách và 100,000 khách hàng |
| 2. | Hệ thống phải xử lý được ít nhất 2,000 đơn hàng mỗi ngày (bao gồm đơn online và offline) |
| 3. | Cho phép nhiều nhân viên (Admin, Nhân viên bán hàng, Nhân viên kho) đồng thời quản lý đơn hàng, cập nhật sách mà không xung đột dữ liệu |
| 4. | Hỗ trợ upload và lưu trữ tối thiểu 100,000 hình ảnh sách (bìa sách, ảnh chi tiết, ảnh đọc thử) và 50,000 ảnh/video từ đánh giá người dùng |
| 5. | Kiến trúc hệ thống phải cho phép mở rộng horizontal scaling khi lượng truy cập tăng |
| 6. | Hỗ trợ đồng bộ dữ liệu thời gian thực giữa kênh online và offline |

## Security

| No. | Requirement |
|-----|-------------|
| 1. | Backend sử dụng Node.js phiên bản 20.0 trở lên để đảm bảo các bản vá bảo mật mới nhất |
| 2. | Xác thực người dùng bắt buộc sử dụng JWT (JSON Web Token) với thời gian hết hạn 24 giờ |
| 3. | Mật khẩu người dùng phải được mã hóa bằng Bcrypt với salt rounds tối thiểu là 10 |
| 4. | Phân quyền rõ ràng giữa 4 vai trò: Admin, Nhân viên bán hàng, Nhân viên kho và Khách hàng - mỗi vai trò chỉ truy cập được các chức năng được phép |
| 5. | Tích hợp các cổng thanh toán (VNPay, MoMo, ZaloPay, Viettel Money) phải tuân thủ chuẩn bảo mật PCI DSS |
| 6. | Dữ liệu hệ thống (thông tin sách, đơn hàng, khách hàng, tồn kho) được sao lưu tự động hàng ngày và lưu trữ tại server backup riêng biệt |
| 7. | Tất cả API endpoints phải được bảo vệ bởi middleware xác thực (Passport.js) |
| 8. | Sử dụng HTTPS/SSL cho mọi kết nối giữa client và server |
| 9. | Implement CORS policy để chỉ cho phép các domain được phê duyệt truy cập API |
| 10. | Chống tấn công XSS, SQL Injection, CSRF thông qua validation (Zod) và sanitization dữ liệu đầu vào |
| 11. | Bảo mật thông tin khách hàng (họ tên, số điện thoại, địa chỉ, lịch sử mua hàng) tuân thủ quy định bảo vệ dữ liệu cá nhân |
| 12. | Khôi phục mật khẩu thông qua email/SMS phải có cơ chế xác thực OTP với thời gian hết hạn 5 phút |

## Browser

| No. | Requirement |
|-----|-------------|
| 1. | Hỗ trợ các trình duyệt hiện đại: Chrome (3 phiên bản gần nhất), Firefox (3 phiên bản gần nhất) |
| 2. | Hỗ trợ Microsoft Edge (phiên bản dựa trên Chromium) |
| 3. | Hỗ trợ Safari 14 trở lên (cho người dùng macOS và iOS) |
| 4. | Responsive design tương thích với các thiết bị mobile (iOS, Android) cho cả khách hàng và nhân viên |
| 5. | Không hỗ trợ Internet Explorer (đã ngừng hỗ trợ từ Microsoft) |
| 6. | Giao diện tối ưu cho màn hình tablet để nhân viên bán hàng dễ dàng xử lý đơn hàng tại quầy |

## Reliability

| No. | Requirement |
|-----|-------------|
| 1. | Uptime hệ thống đạt tối thiểu 99.5% trong tháng (cho phép downtime không quá 3.6 giờ/tháng) |
| 2. | Thời gian phục hồi hệ thống từ dữ liệu backup trong trường hợp sự cố không quá 6 giờ |
| 3. | Cơ chế retry tự động cho các giao dịch thanh toán thất bại |
| 4. | Đồng bộ dữ liệu tồn kho giữa online và offline phải chính xác 100% để tránh bán quá số lượng có sẵn |
| 5. | Thông báo trạng thái đơn hàng cho khách hàng phải được gửi kịp thời (độ trễ tối đa 30 giây) |
| 6. | Hệ thống báo cáo phải luôn sẵn sàng cho Admin và nhân viên truy cập mọi lúc |

## Interfaces

| No. | Requirement |
|-----|-------------|
| 1. | Sử dụng Framework Next.js để tạo giao diện người dùng |
| 2. | Styling sử dụng Tailwind CSS kết hợp shadcn/ui components |
| 3. | Hỗ trợ đa ngôn ngữ (Tiếng Việt, Tiếng Anh) thông qua next-intl |
| 4. | Responsive design tương thích mọi kích thước màn hình (desktop, tablet, mobile) |
| 5. | Giao diện riêng biệt cho từng vai trò: Admin, Nhân viên bán hàng, Nhân viên kho, Khách hàng |
| 6. | Dashboard trực quan cho Admin để theo dõi doanh thu, tồn kho, đơn hàng theo thời gian thực |
| 7. | Giao diện POS (Point of Sale) đơn giản, nhanh cho nhân viên bán hàng tại quầy |
| 8. | Tích hợp API đơn vị vận chuyển (GHTK, GHN, J&T) để theo dõi đơn hàng |

## Assumptions

| No. | Requirement |
|-----|-------------|
| 1. | Có thể tạm ngưng hệ thống nếu cần phải nâng cấp (thời gian bảo trì: 2-4h sáng, thông báo trước 24h) |
| 2. | Người dùng (khách hàng và nhân viên) có kết nối internet ổn định tối thiểu 5 Mbps |
| 3. | Admin và nhân viên (bán hàng, kho) được đào tạo cơ bản trước khi vận hành hệ thống |
| 4. | Môi trường dev, staging, production được tách biệt hoàn toàn |
| 5. | Nhà sách có sẵn thiết bị (máy tính, máy quét mã vạch, máy in hóa đơn) để vận hành hệ thống |
| 6. | Khách hàng có tài khoản ngân hàng hoặc ví điện tử để thanh toán online |
| 7. | Thông tin sách (tên, tác giả, NXB, giá) được nhập chính xác bởi nhân viên kho |
| 8. | Hệ thống xếp hạng (ranking) khách hàng được cập nhật tự động dựa trên tổng giá trị chi tiêu |
