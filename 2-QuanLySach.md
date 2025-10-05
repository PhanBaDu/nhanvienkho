# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý sách của Nhân viên kho_

## MỤC LỤC

1. [Chức năng quản lý sách](#1-chức-năng-quản-lý-sách)
   - 1.1 [Hiển thị danh sách sách](#11-hiển-thị-danh-sách-sách)
   - 1.2 [Xem chi tiết sách](#12-xem-chi-tiết-sách)
   - 1.3 [Thêm sách mới](#13-thêm-sách-mới)
   - 1.4 [Chỉnh sửa thông tin sách](#14-chỉnh-sửa-thông-tin-sách)
   - 1.5 [Ẩn sách](#15-ẩn-sách)
   - 1.6 [Tìm kiếm sách](#16-tìm-kiếm-sách)

---

## 1. CHỨC NĂNG QUẢN LÝ SÁCH

### 1.1 HIỂN THỊ DANH SÁCH SÁCH

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách sách trong kho                                             |
| ------------- | -------------------------------------------------------------------- |
| Description   | Hiển thị danh sách tất cả sách có trong kho để nhân viên kho quản lý |
| Screen Access | Nhân viên kho chọn **Quản lý sách** từ menu chính                    |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                   | Type         | Data                                                                                    | Description                                                    |
| ---------------------- | ------------ | --------------------------------------------------------------------------------------- | -------------------------------------------------------------- |
| **Tiêu đề trang**      | Text         | Quản lý sách                                                                            | Tiêu đề chính của trang quản lý sách                           |
| **Thống kê tổng quan** | Card Group   | Tổng số sách: 1,250<br>Sách có sẵn: 1,180<br>Sách hết hàng: 45<br>Sách ẩn: 25           | Hiển thị các chỉ số thống kê nhanh về tình hình sách trong kho |
| **Tìm kiếm sách**      | Input (Text) |                                                                                         | Ô nhập liệu để tìm kiếm sách theo tên, tác giả, mã sách        |
| **Bộ lọc thể loại**    | Dropdown     | Tất cả<br>Văn học<br>Khoa học<br>Lịch sử<br>Kinh tế<br>Giáo dục                         | Lọc danh sách sách theo thể loại                               |
| **Bộ lọc trạng thái**  | Dropdown     | Tất cả<br>Có sẵn<br>Hết hàng<br>Ẩn<br>Ngừng kinh doanh                                  | Lọc danh sách sách theo trạng thái                             |
| **Sắp xếp**            | Dropdown     | Tên A-Z<br>Tên Z-A<br>Giá tăng dần<br>Giá giảm dần<br>Ngày nhập mới nhất                | Sắp xếp danh sách sách theo tiêu chí                           |
| **Danh sách sách**     | Table        | Mã sách<br>Tên sách<br>Tác giả<br>Thể loại<br>Giá<br>Số lượng<br>Trạng thái<br>Thao tác | Hiển thị các sách dưới dạng bảng                               |
| **Mã sách**            | Text + Badge | BK001                                                                                   | Mã định danh của sách, kèm theo badge trạng thái               |
| **Tên sách**           | Text         | Đắc Nhân Tâm                                                                            | Tên của cuốn sách                                              |
| **Tác giả**            | Text         | Dale Carnegie                                                                           | Tên tác giả của sách                                           |
| **Thể loại**           | Badge        | Văn học                                                                                 | Thể loại của sách                                              |
| **Giá**                | Text         | 89.000 VNĐ                                                                              | Giá bán của sách                                               |
| **Số lượng**           | Text         | 15                                                                                      | Số lượng sách còn trong kho                                    |
| **Trạng thái**         | Badge        | Có sẵn<br>Hết hàng<br>Ẩn<br>Ngừng kinh doanh                                            | Trạng thái hiện tại của sách                                   |
| **Thao tác**           | Button Group | Xem chi tiết<br>Chỉnh sửa<br>Ẩn sách                                                    | Các nút chức năng để thao tác trên sách                        |
| **Phân trang**         | Pagination   | Trang 1/50                                                                              | Điều hướng giữa các trang                                      |

#### 1.1.3 Hành động và xử lý:

| Action Name            | Description                                                                                                                                                                                                                                                                                                                                                                                                      | Success                                                                                                           | Failure                                                                                                           |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Xem danh sách sách** | Hiển thị danh sách tất cả sách có trong kho để nhân viên kho quản lý. Bao gồm thông tin cơ bản như mã sách, tên sách, tác giả, thể loại, giá, số lượng tồn kho và trạng thái. Cung cấp các bộ lọc để lọc sách theo thể loại và trạng thái. Hỗ trợ tìm kiếm sách theo tên, tác giả hoặc mã sách. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. Hiển thị thống kê tổng quan về tình hình sách trong kho. | Hiển thị danh sách sách đầy đủ với đầy đủ thông tin. Tìm kiếm và lọc hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách sách do lỗi hệ thống. Tìm kiếm và lọc không hoạt động. Thống kê hiển thị không chính xác. |
| **Tìm kiếm sách**      | Cho phép nhân viên kho tìm kiếm sách theo các tiêu chí khác nhau. Hỗ trợ tìm kiếm theo tên sách, tên tác giả, mã sách. Tìm kiếm real-time khi người dùng nhập từ khóa. Hiển thị kết quả tìm kiếm ngay lập tức và cập nhật danh sách sách. Làm nổi bật các từ khóa tìm kiếm trong kết quả.                                                                                                                        | Hiển thị kết quả tìm kiếm chính xác và nhanh chóng. Từ khóa được làm nổi bật trong kết quả.                       | Không tìm thấy sách nào phù hợp với từ khóa tìm kiếm. Lỗi khi thực hiện tìm kiếm.                                 |
| **Lọc sách**           | Cung cấp các bộ lọc để nhân viên kho có thể lọc danh sách sách theo nhu cầu. Bao gồm bộ lọc theo thể loại (Văn học, Khoa học, Lịch sử, Kinh tế, Giáo dục). Bộ lọc theo trạng thái (Có sẵn, Hết hàng, Ẩn, Ngừng kinh doanh). Bộ lọc theo khoảng giá. Bộ lọc theo nhà xuất bản.                                                                                                                                    | Hiển thị danh sách sách đã được lọc theo tiêu chí đã chọn. Bộ lọc hoạt động chính xác.                            | Bộ lọc không hoạt động hoặc hiển thị kết quả không chính xác. Lỗi khi áp dụng bộ lọc.                             |

### 1.2 XEM CHI TIẾT SÁCH

#### 1.2.1 Thông tin màn hình:

| Screen        | Chi tiết sách                                                  |
| ------------- | -------------------------------------------------------------- |
| Description   | Hiển thị thông tin chi tiết của một cuốn sách cụ thể trong kho |
| Screen Access | Nhân viên kho click vào nút **Xem chi tiết** từ danh sách sách |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                   | Type         | Data                                                                       | Description                                |
| ---------------------- | ------------ | -------------------------------------------------------------------------- | ------------------------------------------ |
| **Tiêu đề trang**      | Text         | Chi tiết sách - BK001                                                      | Tiêu đề trang hiển thị mã sách đang xem    |
| **Thông tin cơ bản**   | Card         | Mã sách<br>Tên sách<br>Tác giả<br>Thể loại<br>Nhà xuất bản<br>Năm xuất bản | Hiển thị các thông tin cơ bản về sách      |
| **Mã sách**            | Text         | BK001                                                                      | Mã định danh duy nhất của sách             |
| **Tên sách**           | Text         | Đắc Nhân Tâm                                                               | Tên đầy đủ của cuốn sách                   |
| **Tác giả**            | Text         | Dale Carnegie                                                              | Tên tác giả của sách                       |
| **Thể loại**           | Badge        | Văn học                                                                    | Thể loại của sách                          |
| **Nhà xuất bản**       | Text         | Nhà xuất bản Trẻ                                                           | Tên nhà xuất bản                           |
| **Năm xuất bản**       | Text         | 2020                                                                       | Năm xuất bản của sách                      |
| **Thông tin bán hàng** | Card         | Giá bán<br>Số lượng tồn kho<br>Trạng thái<br>Ngày nhập<br>Ngày cập nhật    | Hiển thị thông tin liên quan đến bán hàng  |
| **Giá bán**            | Text         | 89.000 VNĐ                                                                 | Giá bán hiện tại của sách                  |
| **Số lượng tồn kho**   | Text         | 15                                                                         | Số lượng sách còn trong kho                |
| **Trạng thái**         | Badge        | Có sẵn                                                                     | Trạng thái hiện tại của sách               |
| **Ngày nhập**          | Text         | 2023-10-15                                                                 | Ngày sách được nhập vào kho                |
| **Ngày cập nhật**      | Text         | 2023-11-20                                                                 | Ngày thông tin sách được cập nhật lần cuối |
| **Mô tả sách**         | Textarea     | Cuốn sách nổi tiếng về nghệ thuật giao tiếp và ứng xử...                   | Mô tả chi tiết về nội dung sách            |
| **Hình ảnh sách**      | Image        | Ảnh bìa sách                                                               | Hiển thị hình ảnh bìa sách                 |
| **Lịch sử nhập xuất**  | Table        | Ngày<br>Loại<br>Số lượng<br>Ghi chú<br>Người thực hiện                     | Bảng ghi lại lịch sử nhập xuất sách        |
| **Hành động**          | Button Group | Chỉnh sửa<br>Ẩn sách<br>Cập nhật tồn kho<br>Quay lại                       | Các nút chức năng để thao tác trên sách    |

#### 1.2.3 Hành động và xử lý:

| Action Name               | Description                                                                                                                                                                                                                                                                                                                                                                                                              | Success                                                                                                                   | Failure                                                                                                        |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **Xem chi tiết sách**     | Hiển thị thông tin chi tiết của một cuốn sách cụ thể trong kho. Bao gồm thông tin cơ bản (mã sách, tên sách, tác giả, thể loại, nhà xuất bản, năm xuất bản). Thông tin bán hàng (giá bán, số lượng tồn kho, trạng thái, ngày nhập, ngày cập nhật). Mô tả chi tiết về nội dung sách. Hình ảnh bìa sách. Lịch sử nhập xuất sách theo dòng thời gian. Cung cấp các nút hành động để chỉnh sửa, ẩn sách và cập nhật tồn kho. | Hiển thị đầy đủ thông tin chi tiết của sách được chọn. Lịch sử nhập xuất được hiển thị chính xác.                         | Không tìm thấy sách với mã đã cung cấp. Lỗi khi tải thông tin chi tiết sách. Lịch sử nhập xuất không hiển thị. |
| **Xem lịch sử nhập xuất** | Hiển thị lịch sử chi tiết các lần nhập và xuất sách. Bao gồm thông tin về ngày thực hiện, loại giao dịch (nhập/xuất), số lượng, ghi chú và người thực hiện. Hiển thị theo dòng thời gian từ cũ đến mới nhất. Cho phép xem chi tiết từng giao dịch.                                                                                                                                                                       | Hiển thị đầy đủ lịch sử nhập xuất sách theo dòng thời gian. Thông tin chi tiết về từng giao dịch được hiển thị chính xác. | Không thể tải lịch sử nhập xuất do lỗi hệ thống. Lịch sử hiển thị không đầy đủ hoặc không chính xác.           |

### 1.3 THÊM SÁCH MỚI

#### 1.3.1 Thông tin màn hình:

| Screen        | Thêm sách mới                                                       |
| ------------- | ------------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho thêm sách mới vào hệ thống quản lý kho       |
| Screen Access | Nhân viên kho click vào nút **Thêm sách mới** từ trang quản lý sách |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                     | Type           | Data                                                                    | Description                                            |
| ------------------------ | -------------- | ----------------------------------------------------------------------- | ------------------------------------------------------ |
| **Tiêu đề trang**        | Text           | Thêm sách mới                                                           | Tiêu đề chính của trang thêm sách                      |
| **Thông tin cơ bản**     | Form           | Tên sách<br>Tác giả<br>Thể loại<br>Nhà xuất bản<br>Năm xuất bản<br>ISBN | Form nhập thông tin cơ bản về sách                     |
| **Tên sách**             | Input (Text)   |                                                                         | Ô nhập tên đầy đủ của sách (bắt buộc)                  |
| **Tác giả**              | Input (Text)   |                                                                         | Ô nhập tên tác giả (bắt buộc)                          |
| **Thể loại**             | Select         | Văn học<br>Khoa học<br>Lịch sử<br>Kinh tế<br>Giáo dục<br>Khác           | Lựa chọn thể loại sách (bắt buộc)                      |
| **Nhà xuất bản**         | Input (Text)   |                                                                         | Ô nhập tên nhà xuất bản (bắt buộc)                     |
| **Năm xuất bản**         | Input (Number) |                                                                         | Ô nhập năm xuất bản (bắt buộc)                         |
| **ISBN**                 | Input (Text)   |                                                                         | Ô nhập mã ISBN của sách                                |
| **Thông tin bán hàng**   | Form           | Giá bán<br>Số lượng nhập<br>Mô tả sách                                  | Form nhập thông tin liên quan đến bán hàng             |
| **Giá bán**              | Input (Number) |                                                                         | Ô nhập giá bán của sách (bắt buộc)                     |
| **Số lượng nhập**        | Input (Number) |                                                                         | Ô nhập số lượng sách nhập vào kho (bắt buộc)           |
| **Mô tả sách**           | Textarea       |                                                                         | Ô nhập mô tả chi tiết về nội dung sách                 |
| **Hình ảnh sách**        | File Upload    |                                                                         | Tải lên hình ảnh bìa sách                              |
| **Nút lưu**              | Button         |                                                                         | Nút lưu thông tin sách mới                             |
| **Nút hủy**              | Button         |                                                                         | Nút hủy thao tác thêm sách                             |
| **Thông báo lỗi**        | Alert          | Vui lòng nhập đầy đủ thông tin bắt buộc<br>Giá bán phải lớn hơn 0       | Hiển thị thông báo lỗi khi nhập thông tin không hợp lệ |
| **Thông báo thành công** | Alert          | Thêm sách mới thành công                                                | Hiển thị thông báo khi thêm sách thành công            |

#### 1.3.3 Hành động và xử lý:

| Action Name               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                    | Success                                                                                                                  | Failure                                                                                                                        |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| **Thêm sách mới**         | Cho phép nhân viên kho thêm sách mới vào hệ thống quản lý kho. Yêu cầu nhập đầy đủ thông tin cơ bản về sách (tên sách, tác giả, thể loại, nhà xuất bản, năm xuất bản). Nhập thông tin bán hàng (giá bán, số lượng nhập, mô tả sách). Tải lên hình ảnh bìa sách. Tự động tạo mã sách duy nhất. Xác thực tính hợp lệ của dữ liệu nhập vào. Lưu thông tin sách vào cơ sở dữ liệu. Cập nhật tồn kho với số lượng nhập. Ghi nhận lịch sử nhập sách. | Sách mới được thêm thành công vào hệ thống. Mã sách được tạo tự động. Tồn kho được cập nhật. Lịch sử nhập được ghi nhận. | Dữ liệu nhập vào không hợp lệ. Lỗi khi lưu thông tin sách vào cơ sở dữ liệu. Không thể tải lên hình ảnh. Mã sách bị trùng lặp. |
| **Xác thực dữ liệu sách** | Kiểm tra tính hợp lệ của dữ liệu sách trước khi lưu. Kiểm tra các trường bắt buộc đã được nhập đầy đủ. Kiểm tra giá bán phải lớn hơn 0. Kiểm tra số lượng nhập phải lớn hơn 0. Kiểm tra năm xuất bản phải hợp lệ. Kiểm tra định dạng ISBN nếu có. Hiển thị thông báo lỗi chi tiết cho từng trường không hợp lệ.                                                                                                                                | Tất cả dữ liệu sách được xác thực hợp lệ. Cho phép lưu sách mới.                                                         | Dữ liệu sách không hợp lệ. Hiển thị thông báo lỗi chi tiết cho từng trường.                                                    |
| **Tạo mã sách tự động**   | Tự động tạo mã sách duy nhất cho sách mới. Sử dụng quy tắc đặt tên nhất quán (ví dụ: BK + số thứ tự). Kiểm tra mã sách không bị trùng lặp với các sách hiện có. Đảm bảo mã sách dễ đọc và quản lý. Lưu mã sách vào cơ sở dữ liệu cùng với thông tin sách.                                                                                                                                                                                      | Mã sách duy nhất được tạo thành công. Mã sách không bị trùng lặp.                                                        | Không thể tạo mã sách do lỗi hệ thống. Mã sách bị trùng lặp với sách hiện có.                                                  |

### 1.4 CHỈNH SỬA THÔNG TIN SÁCH

#### 1.4.1 Thông tin màn hình:

| Screen        | Chỉnh sửa thông tin sách                                                 |
| ------------- | ------------------------------------------------------------------------ |
| Description   | Cho phép nhân viên kho chỉnh sửa thông tin của sách đã có trong hệ thống |
| Screen Access | Nhân viên kho click vào nút **Chỉnh sửa** từ trang chi tiết sách         |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                     | Type           | Data                                                                    | Description                                               |
| ------------------------ | -------------- | ----------------------------------------------------------------------- | --------------------------------------------------------- |
| **Tiêu đề trang**        | Text           | Chỉnh sửa sách - BK001                                                  | Tiêu đề trang hiển thị mã sách đang chỉnh sửa             |
| **Thông tin cơ bản**     | Form           | Tên sách<br>Tác giả<br>Thể loại<br>Nhà xuất bản<br>Năm xuất bản<br>ISBN | Form chỉnh sửa thông tin cơ bản về sách                   |
| **Tên sách**             | Input (Text)   | Đắc Nhân Tâm                                                            | Ô nhập tên đầy đủ của sách (có thể chỉnh sửa)             |
| **Tác giả**              | Input (Text)   | Dale Carnegie                                                           | Ô nhập tên tác giả (có thể chỉnh sửa)                     |
| **Thể loại**             | Select         | Văn học<br>Khoa học<br>Lịch sử<br>Kinh tế<br>Giáo dục<br>Khác           | Lựa chọn thể loại sách (có thể thay đổi)                  |
| **Nhà xuất bản**         | Input (Text)   | Nhà xuất bản Trẻ                                                        | Ô nhập tên nhà xuất bản (có thể chỉnh sửa)                |
| **Năm xuất bản**         | Input (Number) | 2020                                                                    | Ô nhập năm xuất bản (có thể chỉnh sửa)                    |
| **ISBN**                 | Input (Text)   | 978-604-1-12345-6                                                       | Ô nhập mã ISBN của sách (có thể chỉnh sửa)                |
| **Thông tin bán hàng**   | Form           | Giá bán<br>Mô tả sách<br>Trạng thái                                     | Form chỉnh sửa thông tin liên quan đến bán hàng           |
| **Giá bán**              | Input (Number) | 89.000                                                                  | Ô nhập giá bán của sách (có thể chỉnh sửa)                |
| **Mô tả sách**           | Textarea       | Cuốn sách nổi tiếng về nghệ thuật giao tiếp...                          | Ô nhập mô tả chi tiết về nội dung sách (có thể chỉnh sửa) |
| **Trạng thái**           | Select         | Có sẵn<br>Hết hàng<br>Ẩn<br>Ngừng kinh doanh                            | Lựa chọn trạng thái sách (có thể thay đổi)                |
| **Hình ảnh sách**        | File Upload    |                                                                         | Tải lên hình ảnh bìa sách mới (tùy chọn)                  |
| **Nút lưu thay đổi**     | Button         |                                                                         | Nút lưu các thay đổi thông tin sách                       |
| **Nút hủy**              | Button         |                                                                         | Nút hủy các thay đổi chưa lưu                             |
| **Thông báo lỗi**        | Alert          | Vui lòng nhập đầy đủ thông tin bắt buộc<br>Giá bán phải lớn hơn 0       | Hiển thị thông báo lỗi khi nhập thông tin không hợp lệ    |
| **Thông báo thành công** | Alert          | Cập nhật thông tin sách thành công                                      | Hiển thị thông báo khi cập nhật thành công                |

#### 1.4.3 Hành động và xử lý:

| Action Name                    | Description                                                                                                                                                                                                                                                                                                                                                                                     | Success                                                                                                 | Failure                                                                                             |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **Chỉnh sửa thông tin sách**   | Cho phép nhân viên kho chỉnh sửa thông tin của sách đã có trong hệ thống. Cập nhật thông tin cơ bản (tên sách, tác giả, thể loại, nhà xuất bản, năm xuất bản, ISBN). Cập nhật thông tin bán hàng (giá bán, mô tả sách, trạng thái). Tải lên hình ảnh bìa sách mới nếu cần. Xác thực tính hợp lệ của dữ liệu nhập vào. Lưu thay đổi vào cơ sở dữ liệu. Ghi nhận lịch sử thay đổi thông tin sách. | Thông tin sách được cập nhật thành công. Lịch sử thay đổi được ghi nhận. Hình ảnh được cập nhật nếu có. | Dữ liệu nhập vào không hợp lệ. Lỗi khi lưu thay đổi vào cơ sở dữ liệu. Không thể cập nhật hình ảnh. |
| **Xác thực dữ liệu chỉnh sửa** | Kiểm tra tính hợp lệ của dữ liệu sách sau khi chỉnh sửa. Kiểm tra các trường bắt buộc vẫn được nhập đầy đủ. Kiểm tra giá bán phải lớn hơn 0. Kiểm tra năm xuất bản phải hợp lệ. Kiểm tra định dạng ISBN nếu có. So sánh với dữ liệu cũ để phát hiện thay đổi. Hiển thị thông báo lỗi chi tiết cho từng trường không hợp lệ.                                                                     | Tất cả dữ liệu sách sau chỉnh sửa được xác thực hợp lệ. Cho phép lưu thay đổi.                          | Dữ liệu sách sau chỉnh sửa không hợp lệ. Hiển thị thông báo lỗi chi tiết.                           |
| **Ghi nhận lịch sử thay đổi**  | Ghi nhận lịch sử tất cả các thay đổi thông tin sách. Bao gồm thông tin về trường thay đổi, giá trị cũ, giá trị mới, thời gian thay đổi và người thực hiện. Lưu lịch sử thay đổi vào cơ sở dữ liệu. Cho phép xem lại lịch sử thay đổi trong tương lai. Đảm bảo tính minh bạch và có thể truy vết được các thay đổi.                                                                              | Lịch sử thay đổi được ghi nhận đầy đủ và chính xác. Có thể xem lại lịch sử thay đổi.                    | Không thể ghi nhận lịch sử thay đổi do lỗi hệ thống. Lịch sử thay đổi không đầy đủ.                 |

### 1.5 ẨN SÁCH

#### 1.5.1 Thông tin màn hình:

| Screen        | Ẩn sách                                                           |
| ------------- | ----------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho ẩn sách không còn kinh doanh khỏi hệ thống |
| Screen Access | Nhân viên kho click vào nút **Ẩn sách** từ trang chi tiết sách    |

#### 1.5.2 Chi tiết thành phần màn hình:

| Item                     | Type     | Data                                                                             | Description                                |
| ------------------------ | -------- | -------------------------------------------------------------------------------- | ------------------------------------------ |
| **Xác nhận ẩn sách**     | Modal    | Bạn có chắc chắn muốn ẩn sách này?<br>Sách sẽ không hiển thị trong danh sách bán | Modal xác nhận trước khi ẩn sách           |
| **Lý do ẩn sách**        | Textarea |                                                                                  | Ô nhập lý do ẩn sách (bắt buộc)            |
| **Nút xác nhận**         | Button   | Có, ẩn sách                                                                      | Nút xác nhận ẩn sách                       |
| **Nút hủy**              | Button   | Hủy                                                                              | Nút hủy thao tác ẩn sách                   |
| **Thông báo thành công** | Alert    | Ẩn sách thành công                                                               | Hiển thị thông báo khi ẩn sách thành công  |
| **Thông báo lỗi**        | Alert    | Vui lòng nhập lý do ẩn sách                                                      | Hiển thị thông báo lỗi khi chưa nhập lý do |

#### 1.5.3 Hành động và xử lý:

| Action Name                  | Description                                                                                                                                                                                                                                                                                                                                                          | Success                                                                                                                 | Failure                                                                                       |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **Ẩn sách**                  | Cho phép nhân viên kho ẩn sách không còn kinh doanh khỏi hệ thống. Hiển thị modal xác nhận trước khi ẩn sách. Yêu cầu nhập lý do ẩn sách. Thay đổi trạng thái sách thành "Ẩn". Cập nhật thông tin sách trong cơ sở dữ liệu. Ghi nhận lịch sử ẩn sách với lý do và thời gian. Sách sẽ không hiển thị trong danh sách bán hàng nhưng vẫn có thể xem trong quản lý kho. | Sách được ẩn thành công khỏi hệ thống bán hàng. Lịch sử ẩn sách được ghi nhận. Sách không hiển thị trong danh sách bán. | Không thể ẩn sách do lỗi hệ thống. Chưa nhập lý do ẩn sách. Lỗi khi cập nhật trạng thái sách. |
| **Xác nhận ẩn sách**         | Hiển thị modal xác nhận trước khi thực hiện ẩn sách để tránh ẩn nhầm. Yêu cầu nhập lý do ẩn sách để đảm bảo tính minh bạch. Cho phép nhân viên hủy thao tác ẩn sách nếu không muốn. Chỉ thực hiện ẩn sách khi có xác nhận rõ ràng và lý do hợp lệ.                                                                                                                   | Modal xác nhận hiển thị chính xác. Người dùng có thể xác nhận hoặc hủy ẩn sách.                                         | Modal xác nhận không hiển thị. Không thể hủy thao tác ẩn sách.                                |
| **Ghi nhận lịch sử ẩn sách** | Ghi nhận lịch sử ẩn sách với đầy đủ thông tin. Bao gồm mã sách, tên sách, lý do ẩn, thời gian ẩn và người thực hiện. Lưu lịch sử ẩn sách vào cơ sở dữ liệu. Cho phép xem lại lịch sử ẩn sách trong tương lai. Đảm bảo có thể truy vết được lý do và thời gian ẩn sách.                                                                                               | Lịch sử ẩn sách được ghi nhận đầy đủ và chính xác. Có thể xem lại lịch sử ẩn sách.                                      | Không thể ghi nhận lịch sử ẩn sách do lỗi hệ thống. Lịch sử ẩn sách không đầy đủ.             |

### 1.6 TÌM KIẾM SÁCH

#### 1.6.1 Thông tin màn hình:

| Screen        | Tìm kiếm sách                                                              |
| ------------- | -------------------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho tìm kiếm sách theo tên, tác giả, mã sách để quản lý |
| Screen Access | Nhân viên kho sử dụng ô tìm kiếm trên trang quản lý sách                   |

#### 1.6.2 Chi tiết thành phần màn hình:

| Item                 | Type         | Data                                                                        | Description                              |
| -------------------- | ------------ | --------------------------------------------------------------------------- | ---------------------------------------- |
| **Ô tìm kiếm**       | Input (Text) |                                                                             | Ô nhập từ khóa tìm kiếm sách             |
| **Gợi ý tìm kiếm**   | Dropdown     | Tên sách gợi ý<br>Tác giả gợi ý<br>Mã sách gợi ý                            | Danh sách gợi ý khi nhập từ khóa         |
| **Bộ lọc nâng cao**  | Panel        | Tìm theo<br>Thể loại<br>Nhà xuất bản<br>Khoảng giá<br>Trạng thái            | Panel bộ lọc nâng cao cho tìm kiếm       |
| **Tìm theo**         | Radio        | Tên sách<br>Tác giả<br>Mã sách<br>ISBN<br>Tất cả                            | Lựa chọn tiêu chí tìm kiếm chính         |
| **Thể loại**         | Checkbox     | Văn học<br>Khoa học<br>Lịch sử<br>Kinh tế<br>Giáo dục                       | Lọc kết quả theo thể loại sách           |
| **Nhà xuất bản**     | Checkbox     | Nhà xuất bản Trẻ<br>NXB Kim Đồng<br>NXB Giáo dục<br>NXB Hội nhà văn         | Lọc kết quả theo nhà xuất bản            |
| **Khoảng giá**       | Range        | Từ 0 VNĐ đến 1.000.000 VNĐ                                                  | Lọc kết quả theo khoảng giá              |
| **Trạng thái**       | Checkbox     | Có sẵn<br>Hết hàng<br>Ẩn<br>Ngừng kinh doanh                                | Lọc kết quả theo trạng thái sách         |
| **Kết quả tìm kiếm** | Table        | Mã sách<br>Tên sách<br>Tác giả<br>Thể loại<br>Giá<br>Số lượng<br>Trạng thái | Hiển thị kết quả tìm kiếm dưới dạng bảng |
| **Thống kê kết quả** | Text         | Tìm thấy 15 kết quả                                                         | Hiển thị số lượng kết quả tìm kiếm       |
| **Nút xóa bộ lọc**   | Button       | Xóa bộ lọc                                                                  | Nút xóa tất cả bộ lọc đã áp dụng         |

#### 1.6.3 Hành động và xử lý:

| Action Name           | Description                                                                                                                                                                                                                                                                                                                                                                                           | Success                                                                                                             | Failure                                                                                                          |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Tìm kiếm sách**     | Cho phép nhân viên kho tìm kiếm sách theo tên, tác giả, mã sách để quản lý. Hỗ trợ tìm kiếm real-time khi người dùng nhập từ khóa. Cung cấp gợi ý tìm kiếm dựa trên dữ liệu hiện có. Hỗ trợ tìm kiếm nâng cao với nhiều tiêu chí lọc. Hiển thị kết quả tìm kiếm ngay lập tức và cập nhật danh sách sách. Làm nổi bật các từ khóa tìm kiếm trong kết quả. Hiển thị thống kê số lượng kết quả tìm kiếm. | Hiển thị kết quả tìm kiếm chính xác và nhanh chóng. Gợi ý tìm kiếm hữu ích. Từ khóa được làm nổi bật trong kết quả. | Không tìm thấy sách nào phù hợp với từ khóa tìm kiếm. Lỗi khi thực hiện tìm kiếm. Gợi ý tìm kiếm không hiển thị. |
| **Tìm kiếm nâng cao** | Cung cấp tính năng tìm kiếm nâng cao với nhiều tiêu chí lọc. Cho phép tìm kiếm theo tên sách, tác giả, mã sách hoặc ISBN. Lọc kết quả theo thể loại, nhà xuất bản, khoảng giá và trạng thái sách. Kết hợp nhiều tiêu chí lọc để thu hẹp kết quả tìm kiếm. Hiển thị kết quả tìm kiếm chính xác theo các tiêu chí đã chọn.                                                                              | Kết quả tìm kiếm nâng cao chính xác và phù hợp với các tiêu chí đã chọn.                                            | Bộ lọc nâng cao không hoạt động. Kết quả tìm kiếm không chính xác.                                               |
| **Gợi ý tìm kiếm**    | Cung cấp gợi ý tìm kiếm dựa trên dữ liệu sách hiện có. Hiển thị gợi ý tên sách, tác giả và mã sách khi người dùng nhập từ khóa. Gợi ý được cập nhật real-time theo từ khóa nhập vào. Cho phép chọn gợi ý để tự động điền vào ô tìm kiếm. Giúp người dùng tìm kiếm nhanh chóng và chính xác hơn.                                                                                                       | Gợi ý tìm kiếm hiển thị chính xác và hữu ích. Người dùng có thể chọn gợi ý dễ dàng.                                 | Gợi ý tìm kiếm không hiển thị. Gợi ý không chính xác hoặc không hữu ích.                                         |
