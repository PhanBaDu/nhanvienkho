# Non-Functional Requirements

## Performance

| No. | Requirement |
|-----|-------------|
| 1. | Hệ thống phải hỗ trợ tối thiểu 1000 người dùng truy cập đồng thời mà không ảnh hưởng đến hiệu suất |
| 2. | Thời gian phản hồi API trung bình phải dưới 200ms cho các thao tác đơn giản (xem sản phẩm, giỏ hàng) |
| 3. | Thời gian tải trang không vượt quá 3 giây với kết nối internet tốc độ trung bình |
| 4. | Thời gian xử lý thanh toán và đặt hàng không vượt quá 5 giây |
| 5. | Real-time chat hỗ trợ khách hàng có độ trễ tối đa 1 giây (sử dụng Socket.IO) |

## Scalability

| No. | Requirement |
|-----|-------------|
| 1. | Database PostgreSQL phải có khả năng lưu trữ tối thiểu 100,000 sản phẩm và 500,000 người dùng |
| 2. | Hệ thống phải xử lý được ít nhất 10,000 đơn hàng mỗi ngày |
| 3. | Cho phép nhiều admin đồng thời quản lý đơn hàng, cập nhật sản phẩm mà không xung đột dữ liệu |
| 4. | Hỗ trợ upload và lưu trữ tối thiểu 50,000 hình ảnh sản phẩm và 20,000 ảnh/video từ bài viết người dùng |
| 5. | Kiến trúc hệ thống phải cho phép mở rộng horizontal scaling khi lượng truy cập tăng |

## Security

| No. | Requirement |
|-----|-------------|
| 1. | Backend sử dụng Node.js phiên bản 20.0 trở lên để đảm bảo các bản vá bảo mật mới nhất |
| 2. | Xác thực người dùng bắt buộc sử dụng JWT (JSON Web Token) với thời gian hết hạn 24 giờ |
| 3. | Mật khẩu người dùng phải được mã hóa bằng Bcrypt với salt rounds tối thiểu là 10 |
| 4. | Phân quyền rõ ràng giữa User và Admin - mỗi vai trò chỉ truy cập được các chức năng được phép |
| 5. | Tích hợp các cổng thanh toán (VNPay, MoMo, ZaloPay, Viettel Money) phải tuân thủ chuẩn bảo mật PCI DSS |
| 6. | Dữ liệu hệ thống được sao lưu tự động hàng ngày và lưu trữ tại server backup riêng biệt |
| 7. | Tất cả API endpoints phải được bảo vệ bởi middleware xác thực (Passport.js) |
| 8. | Sử dụng HTTPS/SSL cho mọi kết nối giữa client và server |
| 9. | Implement CORS policy để chỉ cho phép các domain được phê duyệt truy cập API |
| 10. | Chống tấn công XSS, SQL Injection, CSRF thông qua validation (Zod) và sanitization dữ liệu đầu vào |

## Browser Compatibility

| No. | Requirement |
|-----|-------------|
| 1. | Hỗ trợ các trình duyệt hiện đại: Chrome (3 phiên bản gần nhất), Firefox (3 phiên bản gần nhất) |
| 2. | Hỗ trợ Microsoft Edge (phiên bản dựa trên Chromium) |
| 3. | Hỗ trợ Safari 14 trở lên (cho người dùng macOS và iOS) |
| 4. | Responsive design tương thích với các thiết bị mobile (iOS, Android) |
| 5. | Không hỗ trợ Internet Explorer (đã ngừng hỗ trợ từ Microsoft) |

## Reliability

| No. | Requirement |
|-----|-------------|
| 1. | Uptime hệ thống đạt tối thiểu 99.5% trong tháng (cho phép downtime không quá 3.6 giờ/tháng) |
| 2. | Thời gian phục hồi hệ thống từ dữ liệu backup trong trường hợp sự cố không quá 6 giờ |
| 3. | Cơ chế retry tự động cho các giao dịch thanh toán thất bại |
| 4. | Logging đầy đủ các lỗi hệ thống để hỗ trợ debugging và maintenance |
| 5. | Monitoring real-time các chỉ số quan trọng (CPU, RAM, Database connection, API response time) |

## Usability

| No. | Requirement |
|-----|-------------|
| 1. | Giao diện người dùng phải trực quan, dễ sử dụng theo nguyên tắc UX/UI hiện đại |
| 2. | Hỗ trợ đa ngôn ngữ (tiếng Việt và tiếng Anh) thông qua next-intl |
| 3. | Các form nhập liệu phải có validation real-time và hiển thị lỗi rõ ràng (React Hook Form + Zod) |
| 4. | Thời gian học cách sử dụng hệ thống cho người dùng mới không quá 15 phút |
| 5. | Giao diện phải tối ưu cho cả desktop và mobile (responsive design với Tailwind CSS) |
| 6. | Sử dụng shadcn/ui components để đảm bảo tính nhất quán trong thiết kế |

## Maintainability

| No. | Requirement |
|-----|-------------|
| 1. | Code phải tuân thủ coding standards và best practices của TypeScript |
| 2. | Sử dụng Prisma ORM để quản lý database schema và migrations dễ dàng |
| 3. | API phải được document đầy đủ (sử dụng Swagger hoặc tương tự) |
| 4. | Tách biệt rõ ràng giữa business logic, data access layer và presentation layer |
| 5. | Version control sử dụng Git với commit messages có cấu trúc |

## Data Management

| No. | Requirement |
|-----|-------------|
| 1. | Sử dụng TanStack Query (React Query) cho state management và caching dữ liệu phía client |
| 2. | Implement pagination cho các danh sách lớn (sản phẩm, đơn hàng, thông báo) - tối đa 20-50 items mỗi trang |
| 3. | Database indexing cho các trường thường xuyên query (tên sản phẩm, thương hiệu, giá, trạng thái đơn hàng) |
| 4. | File uploads (ảnh, video) sử dụng Multer middleware với giới hạn kích thước hợp lý (ảnh: 5MB, video: 50MB) |

## Third-party Integration

| No. | Requirement |
|-----|-------------|
| 1. | Tích hợp API các đơn vị vận chuyển (GHTK, GHN, J&T) để tính phí và tracking đơn hàng |
| 2. | Tích hợp các cổng thanh toán phải đảm bảo độ tin cậy 99.9% |
| 3. | Có cơ chế fallback khi third-party service gặp sự cố |

## Assumptions & Constraints

| No. | Requirement |
|-----|-------------|
| 1. | Hệ thống có thể tạm ngưng hoạt động từ 2-4 giờ sáng để bảo trì và nâng cấp (thông báo trước 24h) |
| 2. | Môi trường development, staging và production phải được tách biệt |
| 3. | Yêu cầu internet ổn định tối thiểu 5 Mbps cho trải nghiệm tốt |
| 4. | Admin cần được đào tạo cơ bản về quản trị hệ thống trước khi sử dụng |

---

## Technical Stack Summary

### Backend
- **Ngôn ngữ chính:** TypeScript
- **Runtime:** Node.js (>= 20.0)
- **Framework:** Express.js (RESTful API)
- **Upload file:** Multer middleware
- **ORM:** Prisma
- **Database:** PostgreSQL
- **Real-time:** Socket.IO
- **Hỗ trợ khác:** DOTENV, CORS, JWT, Bcrypt, Cookie, Passport

### Frontend
- **Framework:** Next.js
- **Styling:** Tailwind CSS + shadcn/ui
- **Internationalization:** next-intl
- **Data Management:** TanStack Query
- **Form Management:** React Hook Form + Zod validation
