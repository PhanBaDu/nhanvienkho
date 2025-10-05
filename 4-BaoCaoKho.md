# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng báo cáo kho của Nhân viên kho_

## MỤC LỤC

1. [Chức năng báo cáo kho](#1-chức-năng-báo-cáo-kho)
   - 1.1 [Xem sách sắp hết hàng](#11-xem-sách-sắp-hết-hàng)
   - 1.2 [Báo cáo tồn kho](#12-báo-cáo-tồn-kho)
   - 1.3 [Lịch sử nhập xuất](#13-lịch-sử-nhập-xuất)

---

## 1. CHỨC NĂNG BÁO CÁO KHO

### 1.1 XEM SÁCH SẮP HẾT HÀNG

#### 1.1.1 Thông tin màn hình:

| Screen        | Sách sắp hết hàng                                                       |
| ------------- | ----------------------------------------------------------------------- |
| Description   | Hiển thị danh sách sách có số lượng dưới ngưỡng tối thiểu cần nhập thêm |
| Screen Access | Nhân viên kho chọn **Báo cáo kho** từ menu chính                        |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                          | Type         | Data                                                                                           | Description                                           |
| ----------------------------- | ------------ | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| **Tiêu đề trang**             | Text         | Sách sắp hết hàng                                                                              | Tiêu đề chính của trang báo cáo sách sắp hết hàng     |
| **Thống kê cảnh báo**         | Card Group   | Sách sắp hết: 25<br>Sách hết hàng: 8<br>Sách cần nhập gấp: 5                                   | Hiển thị các chỉ số cảnh báo về tình hình tồn kho     |
| **Bộ lọc mức độ**             | Dropdown     | Tất cả<br>Sắp hết<br>Hết hàng<br>Cần nhập gấp                                                  | Lọc danh sách sách theo mức độ cảnh báo               |
| **Bộ lọc thể loại**           | Dropdown     | Tất cả<br>Văn học<br>Khoa học<br>Lịch sử<br>Kinh tế<br>Giáo dục                                | Lọc danh sách sách theo thể loại                      |
| **Sắp xếp**                   | Dropdown     | Số lượng tăng dần<br>Số lượng giảm dần<br>Tên A-Z<br>Ngày cập nhật mới nhất                    | Sắp xếp danh sách sách theo tiêu chí                  |
| **Danh sách sách**            | Table        | Mã sách<br>Tên sách<br>Thể loại<br>Số lượng hiện tại<br>Ngưỡng tối thiểu<br>Mức độ<br>Thao tác | Hiển thị các sách sắp hết hàng dưới dạng bảng         |
| **Mã sách**                   | Text + Badge | BK001                                                                                          | Mã định danh của sách, kèm theo badge mức độ cảnh báo |
| **Tên sách**                  | Text         | Đắc Nhân Tâm                                                                                   | Tên của cuốn sách                                     |
| **Thể loại**                  | Badge        | Văn học                                                                                        | Thể loại của sách                                     |
| **Số lượng hiện tại**         | Text         | 3                                                                                              | Số lượng sách hiện có trong kho                       |
| **Ngưỡng tối thiểu**          | Text         | 10                                                                                             | Số lượng tối thiểu cần duy trì trong kho              |
| **Mức độ**                    | Badge        | Sắp hết<br>Hết hàng<br>Cần nhập gấp                                                            | Mức độ cảnh báo dựa trên số lượng hiện tại            |
| **Thao tác**                  | Button Group | Tạo yêu cầu nhập<br>Xem chi tiết<br>Cập nhật ngưỡng                                            | Các nút chức năng để thao tác trên sách sắp hết hàng  |
| **Nút tạo yêu cầu hàng loạt** | Button       |                                                                                                | Nút tạo yêu cầu nhập hàng cho nhiều sách cùng lúc     |
| **Nút xuất báo cáo**          | Button       |                                                                                                | Nút xuất báo cáo sách sắp hết hàng                    |
| **Phân trang**                | Pagination   | Trang 1/10                                                                                     | Điều hướng giữa các trang                             |

#### 1.1.3 Hành động và xử lý:

| Action Name                   | Description                                                                                                                                                                                                                                                                                                                                                  | Success                                                                                                                          | Failure                                                                                                                          |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| **Xem sách sắp hết hàng**     | Hiển thị danh sách sách có số lượng dưới ngưỡng tối thiểu cần nhập thêm. Bao gồm thông tin về mã sách, tên sách, thể loại, số lượng hiện tại, ngưỡng tối thiểu và mức độ cảnh báo. Cung cấp bộ lọc theo mức độ cảnh báo và thể loại sách. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. Hiển thị thống kê tổng quan về tình hình cảnh báo tồn kho. | Hiển thị danh sách sách sắp hết hàng đầy đủ với đầy đủ thông tin. Bộ lọc và sắp xếp hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách sách sắp hết hàng do lỗi hệ thống. Bộ lọc và sắp xếp không hoạt động. Thống kê hiển thị không chính xác. |
| **Tạo yêu cầu nhập hàng**     | Cho phép nhân viên kho tạo yêu cầu nhập hàng cho sách sắp hết. Chọn sách cần nhập thêm. Nhập số lượng đề xuất nhập. Nhập lý do yêu cầu nhập hàng. Gửi yêu cầu đến quản lý để phê duyệt. Tự động tính toán số lượng cần nhập dựa trên ngưỡng tối thiểu.                                                                                                       | Yêu cầu nhập hàng được tạo thành công. Yêu cầu được gửi đến quản lý.                                                             | Không thể tạo yêu cầu nhập hàng. Lỗi khi gửi yêu cầu đến quản lý.                                                                |
| **Cập nhật ngưỡng tối thiểu** | Cho phép nhân viên kho cập nhật ngưỡng tối thiểu cho sách. Nhập ngưỡng tối thiểu mới. Xác thực ngưỡng mới phải là số dương. Cập nhật ngưỡng trong cơ sở dữ liệu. Ghi nhận lịch sử thay đổi ngưỡng. Tự động cập nhật mức độ cảnh báo cho sách.                                                                                                                | Ngưỡng tối thiểu được cập nhật thành công. Mức độ cảnh báo được cập nhật tự động.                                                | Ngưỡng mới không hợp lệ. Lỗi khi cập nhật cơ sở dữ liệu.                                                                         |
| **Tạo yêu cầu hàng loạt**     | Cho phép nhân viên kho tạo yêu cầu nhập hàng cho nhiều sách cùng lúc. Chọn nhiều sách sắp hết hàng. Nhập số lượng đề xuất nhập cho từng sách. Nhập lý do yêu cầu chung. Gửi yêu cầu hàng loạt đến quản lý. Tự động tính toán số lượng cần nhập cho tất cả sách.                                                                                              | Tất cả yêu cầu nhập hàng được tạo thành công. Yêu cầu hàng loạt được gửi đến quản lý.                                            | Một số yêu cầu không được tạo do lỗi. Lỗi khi gửi yêu cầu hàng loạt.                                                             |
| **Xuất báo cáo sách sắp hết** | Tạo báo cáo chi tiết về sách sắp hết hàng. Bao gồm danh sách sách sắp hết với đầy đủ thông tin. Thống kê tổng quan về tình hình cảnh báo tồn kho. Định dạng báo cáo theo chuẩn của công ty. Cho phép xuất báo cáo dưới dạng PDF hoặc Excel. Gửi báo cáo cho quản lý và các bộ phận liên quan.                                                                | Báo cáo sách sắp hết hàng được tạo thành công. Báo cáo được gửi đến các bộ phận liên quan.                                       | Không thể tạo báo cáo. Lỗi khi xuất báo cáo. Lỗi khi gửi báo cáo.                                                                |

### 1.2 BÁO CÁO TỒN KHO

#### 1.2.1 Thông tin màn hình:

| Screen        | Báo cáo tồn kho                                            |
| ------------- | ---------------------------------------------------------- |
| Description   | Tạo báo cáo tình trạng kho hàng theo thời gian             |
| Screen Access | Nhân viên kho chọn **Báo cáo tồn kho** từ menu báo cáo kho |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                   | Type         | Data                                                                                     | Description                                          |
| ---------------------- | ------------ | ---------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **Tiêu đề trang**      | Text         | Báo cáo tồn kho                                                                          | Tiêu đề chính của trang báo cáo tồn kho              |
| **Bộ lọc thời gian**   | Form         | Từ ngày<br>Đến ngày<br>Khoảng thời gian<br>Thể loại                                      | Form lọc báo cáo theo thời gian và tiêu chí          |
| **Từ ngày**            | Input (Date) | 2023-11-01                                                                               | Ngày bắt đầu tạo báo cáo                             |
| **Đến ngày**           | Input (Date) | 2023-11-30                                                                               | Ngày kết thúc tạo báo cáo                            |
| **Khoảng thời gian**   | Select       | Hôm nay<br>Tuần này<br>Tháng này<br>Quý này<br>Năm này<br>Tùy chọn                       | Lựa chọn khoảng thời gian có sẵn                     |
| **Thể loại**           | Multi-Select | Văn học<br>Khoa học<br>Lịch sử<br>Kinh tế<br>Giáo dục<br>Tất cả                          | Lọc báo cáo theo thể loại sách                       |
| **Thống kê tổng quan** | Card Group   | Tổng sách: 1,250<br>Giá trị tồn kho: 125M VNĐ<br>Sách có sẵn: 1,180<br>Sách hết hàng: 45 | Hiển thị các chỉ số thống kê tổng quan về tồn kho    |
| **Biểu đồ tồn kho**    | Chart        | Biểu đồ cột thể hiện số lượng sách theo thể loại                                         | Biểu đồ trực quan hóa tình hình tồn kho              |
| **Danh sách sách**     | Table        | Mã sách<br>Tên sách<br>Thể loại<br>Số lượng<br>Giá trị<br>Trạng thái<br>Ngày cập nhật    | Hiển thị danh sách sách trong kho dưới dạng bảng     |
| **Mã sách**            | Text         | BK001                                                                                    | Mã định danh của sách                                |
| **Tên sách**           | Text         | Đắc Nhân Tâm                                                                             | Tên của cuốn sách                                    |
| **Thể loại**           | Badge        | Văn học                                                                                  | Thể loại của sách                                    |
| **Số lượng**           | Text         | 15                                                                                       | Số lượng sách hiện có trong kho                      |
| **Giá trị**            | Text         | 1.350.000 VNĐ                                                                            | Giá trị tồn kho của sách (Số lượng x Giá bán)        |
| **Trạng thái**         | Badge        | Có sẵn<br>Hết hàng<br>Sắp hết<br>Ẩn                                                      | Trạng thái hiện tại của sách                         |
| **Ngày cập nhật**      | Text         | 2023-11-20                                                                               | Ngày cập nhật thông tin sách lần cuối                |
| **Nút tạo báo cáo**    | Button       |                                                                                          | Nút tạo báo cáo tồn kho theo tiêu chí đã chọn        |
| **Nút xuất báo cáo**   | Button       |                                                                                          | Nút xuất báo cáo dưới dạng PDF hoặc Excel            |
| **Nút gửi báo cáo**    | Button       |                                                                                          | Nút gửi báo cáo cho quản lý và các bộ phận liên quan |
| **Phân trang**         | Pagination   | Trang 1/50                                                                               | Điều hướng giữa các trang                            |

#### 1.2.3 Hành động và xử lý:

| Action Name                   | Description                                                                                                                                                                                                                                                                                                                                                          | Success                                                                                                             | Failure                                                                                     |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| **Tạo báo cáo tồn kho**       | Cho phép nhân viên kho tạo báo cáo tình trạng kho hàng theo thời gian. Chọn khoảng thời gian và thể loại sách cần báo cáo. Hiển thị thống kê tổng quan về tồn kho bao gồm tổng số sách, giá trị tồn kho, số sách có sẵn và hết hàng. Tạo biểu đồ trực quan hóa tình hình tồn kho theo thể loại. Hiển thị danh sách chi tiết các sách trong kho với đầy đủ thông tin. | Báo cáo tồn kho được tạo thành công với đầy đủ thông tin. Biểu đồ hiển thị chính xác. Thống kê được tính toán đúng. | Không thể tạo báo cáo do lỗi hệ thống. Biểu đồ không hiển thị. Thống kê được tính toán sai. |
| **Lọc báo cáo theo tiêu chí** | Cho phép nhân viên kho lọc báo cáo tồn kho theo các tiêu chí khác nhau. Lọc theo khoảng thời gian (hôm nay, tuần này, tháng này, quý này, năm này hoặc tùy chọn). Lọc theo thể loại sách (văn học, khoa học, lịch sử, kinh tế, giáo dục). Cập nhật báo cáo theo tiêu chí đã chọn. Hiển thị kết quả lọc ngay lập tức.                                                 | Báo cáo được lọc chính xác theo tiêu chí đã chọn. Kết quả lọc hiển thị đúng.                                        | Bộ lọc không hoạt động. Kết quả lọc không chính xác.                                        |
| **Xuất báo cáo tồn kho**      | Cho phép nhân viên kho xuất báo cáo tồn kho dưới dạng PDF hoặc Excel. Bao gồm thống kê tổng quan, biểu đồ và danh sách chi tiết sách. Định dạng báo cáo theo chuẩn của công ty. Cho phép tùy chỉnh nội dung báo cáo trước khi xuất. Lưu bản mềm báo cáo vào hệ thống.                                                                                                | Báo cáo được xuất thành công dưới định dạng đã chọn. Bản mềm được lưu vào hệ thống.                                 | Không thể xuất báo cáo. Lỗi khi lưu bản mềm.                                                |
| **Gửi báo cáo tồn kho**       | Cho phép nhân viên kho gửi báo cáo tồn kho cho quản lý và các bộ phận liên quan. Chọn người nhận báo cáo. Thêm ghi chú hoặc lời nhắn kèm theo báo cáo. Gửi báo cáo qua email hoặc hệ thống nội bộ. Lưu lịch sử gửi báo cáo.                                                                                                                                          | Báo cáo được gửi thành công đến các bộ phận liên quan. Lịch sử gửi được lưu.                                        | Không thể gửi báo cáo. Lỗi khi lưu lịch sử gửi.                                             |

### 1.3 LỊCH SỬ NHẬP XUẤT

#### 1.3.1 Thông tin màn hình:

| Screen        | Lịch sử nhập xuất                                            |
| ------------- | ------------------------------------------------------------ |
| Description   | Xem lịch sử các lần nhập và xuất hàng                        |
| Screen Access | Nhân viên kho chọn **Lịch sử nhập xuất** từ menu báo cáo kho |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                    | Type         | Data                                                                                         | Description                                           |
| ----------------------- | ------------ | -------------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| **Tiêu đề trang**       | Text         | Lịch sử nhập xuất                                                                            | Tiêu đề chính của trang lịch sử nhập xuất             |
| **Bộ lọc thời gian**    | Form         | Từ ngày<br>Đến ngày<br>Loại giao dịch<br>Mã sách                                             | Form lọc lịch sử theo thời gian và tiêu chí           |
| **Từ ngày**             | Input (Date) | 2023-11-01                                                                                   | Ngày bắt đầu xem lịch sử                              |
| **Đến ngày**            | Input (Date) | 2023-11-30                                                                                   | Ngày kết thúc xem lịch sử                             |
| **Loại giao dịch**      | Select       | Tất cả<br>Nhập hàng<br>Xuất hàng<br>Điều chỉnh                                               | Lọc lịch sử theo loại giao dịch                       |
| **Mã sách**             | Input (Text) |                                                                                              | Ô nhập mã sách để lọc lịch sử cụ thể                  |
| **Thống kê nhập xuất**  | Card Group   | Tổng nhập: 1,250<br>Tổng xuất: 980<br>Chênh lệch: +270<br>Giá trị nhập: 125M VNĐ             | Hiển thị thống kê tổng quan về nhập xuất hàng         |
| **Biểu đồ nhập xuất**   | Chart        | Biểu đồ đường thể hiện xu hướng nhập xuất theo thời gian                                     | Biểu đồ trực quan hóa xu hướng nhập xuất hàng         |
| **Danh sách giao dịch** | Table        | Ngày giờ<br>Loại<br>Mã sách<br>Tên sách<br>Số lượng<br>Giá trị<br>Người thực hiện<br>Ghi chú | Hiển thị danh sách giao dịch nhập xuất dưới dạng bảng |
| **Ngày giờ**            | Text         | 2023-11-20 14:30                                                                             | Thời gian thực hiện giao dịch                         |
| **Loại**                | Badge        | Nhập hàng<br>Xuất hàng<br>Điều chỉnh                                                         | Loại giao dịch được thực hiện                         |
| **Mã sách**             | Text         | BK001                                                                                        | Mã sách liên quan đến giao dịch                       |
| **Tên sách**            | Text         | Đắc Nhân Tâm                                                                                 | Tên sách liên quan đến giao dịch                      |
| **Số lượng**            | Text         | +15<br>-3<br>+5                                                                              | Số lượng thay đổi (dương: nhập, âm: xuất)             |
| **Giá trị**             | Text         | 1.350.000 VNĐ                                                                                | Giá trị giao dịch                                     |
| **Người thực hiện**     | Text         | Nguyễn Văn A                                                                                 | Tên nhân viên thực hiện giao dịch                     |
| **Ghi chú**             | Text         | Nhập hàng từ NXB Trẻ                                                                         | Ghi chú về giao dịch                                  |
| **Nút xuất lịch sử**    | Button       |                                                                                              | Nút xuất lịch sử nhập xuất dưới dạng PDF hoặc Excel   |
| **Nút gửi báo cáo**     | Button       |                                                                                              | Nút gửi báo cáo lịch sử nhập xuất cho quản lý         |
| **Phân trang**          | Pagination   | Trang 1/100                                                                                  | Điều hướng giữa các trang                             |

#### 1.3.3 Hành động và xử lý:

| Action Name                   | Description                                                                                                                                                                                                                                                                                                                                   | Success                                                                                                                | Failure                                                                                                                |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Xem lịch sử nhập xuất**     | Hiển thị lịch sử các lần nhập và xuất hàng trong kho. Bao gồm thông tin về ngày giờ, loại giao dịch, mã sách, tên sách, số lượng, giá trị, người thực hiện và ghi chú. Cung cấp bộ lọc theo thời gian, loại giao dịch và mã sách. Hiển thị thống kê tổng quan về nhập xuất hàng. Tạo biểu đồ trực quan hóa xu hướng nhập xuất theo thời gian. | Hiển thị lịch sử nhập xuất đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. Thống kê và biểu đồ hiển thị đúng. | Không thể tải lịch sử nhập xuất do lỗi hệ thống. Bộ lọc không hoạt động. Thống kê và biểu đồ hiển thị không chính xác. |
| **Lọc lịch sử theo tiêu chí** | Cho phép nhân viên kho lọc lịch sử nhập xuất theo các tiêu chí khác nhau. Lọc theo khoảng thời gian (từ ngày đến ngày). Lọc theo loại giao dịch (nhập hàng, xuất hàng, điều chỉnh). Lọc theo mã sách cụ thể. Cập nhật danh sách lịch sử theo tiêu chí đã chọn. Hiển thị kết quả lọc ngay lập tức.                                             | Lịch sử được lọc chính xác theo tiêu chí đã chọn. Kết quả lọc hiển thị đúng.                                           | Bộ lọc không hoạt động. Kết quả lọc không chính xác.                                                                   |
| **Xuất lịch sử nhập xuất**    | Cho phép nhân viên kho xuất lịch sử nhập xuất dưới dạng PDF hoặc Excel. Bao gồm danh sách chi tiết các giao dịch, thống kê tổng quan và biểu đồ xu hướng. Định dạng báo cáo theo chuẩn của công ty. Cho phép tùy chỉnh nội dung báo cáo trước khi xuất. Lưu bản mềm báo cáo vào hệ thống.                                                     | Lịch sử nhập xuất được xuất thành công dưới định dạng đã chọn. Bản mềm được lưu vào hệ thống.                          | Không thể xuất lịch sử. Lỗi khi lưu bản mềm.                                                                           |
| **Gửi báo cáo lịch sử**       | Cho phép nhân viên kho gửi báo cáo lịch sử nhập xuất cho quản lý. Chọn người nhận báo cáo. Thêm ghi chú hoặc lời nhắn kèm theo báo cáo. Gửi báo cáo qua email hoặc hệ thống nội bộ. Lưu lịch sử gửi báo cáo.                                                                                                                                  | Báo cáo lịch sử được gửi thành công đến quản lý. Lịch sử gửi được lưu.                                                 | Không thể gửi báo cáo. Lỗi khi lưu lịch sử gửi.                                                                        |
| **Xem chi tiết giao dịch**    | Cho phép nhân viên kho xem chi tiết một giao dịch nhập xuất cụ thể. Hiển thị đầy đủ thông tin về giao dịch bao gồm thời gian, loại, sách liên quan, số lượng, giá trị, người thực hiện và ghi chú. Cho phép xem thông tin bổ sung về giao dịch nếu có.                                                                                        | Chi tiết giao dịch được hiển thị đầy đủ và chính xác.                                                                  | Không thể tải chi tiết giao dịch. Thông tin hiển thị không đầy đủ.                                                     |
