# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý tài khoản của Nhân viên kho_

## MỤC LỤC

1. [Chức năng quản lý tài khoản](#1-chức-năng-quản-lý-tài-khoản)
   - 1.1 [Đăng nhập hệ thống](#11-đăng-nhập-hệ-thống)
   - 1.2 [Quản lý thông tin cá nhân](#12-quản-lý-thông-tin-cá-nhân)
   - 1.3 [Thay đổi mật khẩu](#13-thay-đổi-mật-khẩu)
   - 1.4 [Đăng xuất hệ thống](#14-đăng-xuất-hệ-thống)

---

## 1. CHỨC NĂNG QUẢN LÝ TÀI KHOẢN

### 1.1 ĐĂNG NHẬP HỆ THỐNG

#### 1.1.1 Thông tin màn hình:

| Screen        | Đăng nhập hệ thống                                                                 |
| ------------- | ---------------------------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho đăng nhập vào hệ thống quản lý bằng tài khoản được cấp phát |
| Screen Access | Truy cập trang đăng nhập từ URL chính của hệ thống                                 |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                     | Type         | Data                                   | Description                                       |
| ------------------------ | ------------ | -------------------------------------- | ------------------------------------------------- |
| **Tiêu đề trang**        | Text         | Đăng nhập - Nhân viên kho              | Tiêu đề chính của trang đăng nhập                 |
| **Logo hệ thống**        | Image        | Logo nhà sách                          | Logo của hệ thống quản lý nhà sách                |
| **Tên đăng nhập**        | Input (Text) |                                        | Ô nhập tên đăng nhập hoặc email của nhân viên kho |
| **Mật khẩu**             | Input (Pass) |                                        | Ô nhập mật khẩu đăng nhập                         |
| **Ghi nhớ đăng nhập**    | Checkbox     |                                        | Tùy chọn ghi nhớ thông tin đăng nhập              |
| **Nút đăng nhập**        | Button       |                                        | Nút thực hiện đăng nhập vào hệ thống              |
| **Quên mật khẩu**        | Link         |                                        | Liên kết để khôi phục mật khẩu                    |
| **Thông báo lỗi**        | Alert        | Tên đăng nhập hoặc mật khẩu không đúng | Hiển thị thông báo khi đăng nhập thất bại         |
| **Thông báo thành công** | Alert        | Đăng nhập thành công                   | Hiển thị thông báo khi đăng nhập thành công       |

#### 1.1.3 Hành động và xử lý:

| Action Name            | Description                                                                                                                                                                                                                                                                                                                                                                                                                     | Success                                                                                                                   | Failure                                                                                                                              |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **Đăng nhập hệ thống** | Cho phép nhân viên kho đăng nhập vào hệ thống quản lý bằng tài khoản được cấp phát. Hệ thống xác thực thông tin đăng nhập (tên đăng nhập/email và mật khẩu). Kiểm tra quyền truy cập của nhân viên kho. Ghi nhận thời gian đăng nhập và địa chỉ IP. Tự động chuyển hướng đến trang dashboard của nhân viên kho sau khi đăng nhập thành công. Hỗ trợ tính năng "Ghi nhớ đăng nhập" để tự động đăng nhập trong các lần tiếp theo. | Đăng nhập thành công và chuyển hướng đến trang dashboard nhân viên kho. Thông tin đăng nhập được ghi nhận trong hệ thống. | Tên đăng nhập hoặc mật khẩu không đúng. Tài khoản bị khóa hoặc vô hiệu hóa. Lỗi kết nối hệ thống. Tài khoản không có quyền truy cập. |

### 1.2 QUẢN LÝ THÔNG TIN CÁ NHÂN

#### 1.2.1 Thông tin màn hình:

| Screen        | Quản lý thông tin cá nhân                                                        |
| ------------- | -------------------------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho xem và cập nhật thông tin cá nhân của mình trong hệ thống |
| Screen Access | Nhân viên kho chọn **Thông tin cá nhân** từ menu tài khoản                       |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                     | Type          | Data                            | Description                                       |
| ------------------------ | ------------- | ------------------------------- | ------------------------------------------------- |
| **Tiêu đề trang**        | Text          | Thông tin cá nhân               | Tiêu đề chính của trang quản lý thông tin cá nhân |
| **Ảnh đại diện**         | Image         | Ảnh profile của nhân viên       | Hiển thị ảnh đại diện hiện tại của nhân viên      |
| **Tải lên ảnh mới**      | Button        |                                 | Nút để tải lên ảnh đại diện mới                   |
| **Họ và tên**            | Input (Text)  | Nguyễn Văn A                    | Ô nhập họ và tên đầy đủ của nhân viên             |
| **Số điện thoại**        | Input (Text)  | 0901234567                      | Ô nhập số điện thoại liên lạc                     |
| **Email**                | Input (Email) | nhanvien@example.com            | Ô nhập địa chỉ email liên lạc                     |
| **Địa chỉ**              | Textarea      | 123 Đường ABC, Quận XYZ, TP.HCM | Ô nhập địa chỉ nơi ở hiện tại                     |
| **Ngày sinh**            | Input (Date)  | 1990-01-01                      | Ô nhập ngày sinh                                  |
| **Giới tính**            | Select        | Nam<br>Nữ<br>Khác               | Lựa chọn giới tính                                |
| **Chức vụ**              | Text          | Nhân viên kho                   | Hiển thị chức vụ hiện tại (chỉ đọc)               |
| **Ngày vào làm**         | Text          | 2023-01-15                      | Hiển thị ngày bắt đầu làm việc (chỉ đọc)          |
| **Trạng thái tài khoản** | Badge         | Hoạt động                       | Hiển thị trạng thái tài khoản hiện tại            |
| **Nút lưu thay đổi**     | Button        |                                 | Nút để lưu các thay đổi thông tin cá nhân         |
| **Nút hủy**              | Button        |                                 | Nút để hủy các thay đổi chưa lưu                  |

#### 1.2.3 Hành động và xử lý:

| Action Name                    | Description                                                                                                                                                                                                                                                                      | Success                                                                                   | Failure                                                                                                 |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Xem thông tin cá nhân**      | Hiển thị thông tin cá nhân hiện tại của nhân viên kho bao gồm họ tên, số điện thoại, email, địa chỉ, ngày sinh, giới tính. Hiển thị thông tin chức vụ và ngày vào làm (chỉ đọc). Hiển thị trạng thái tài khoản hiện tại. Cho phép xem ảnh đại diện hiện tại.                     | Hiển thị đầy đủ thông tin cá nhân của nhân viên kho. Giao diện thân thiện và dễ sử dụng.  | Không thể tải thông tin cá nhân do lỗi hệ thống. Thông tin hiển thị không chính xác hoặc không đầy đủ.  |
| **Cập nhật thông tin cá nhân** | Cho phép nhân viên kho cập nhật các thông tin cá nhân có thể thay đổi như họ tên, số điện thoại, email, địa chỉ, ngày sinh, giới tính. Tải lên ảnh đại diện mới. Xác thực tính hợp lệ của dữ liệu nhập vào. Lưu thay đổi vào cơ sở dữ liệu. Ghi nhận lịch sử thay đổi thông tin. | Thông tin cá nhân được cập nhật thành công. Lịch sử thay đổi được ghi nhận.               | Dữ liệu nhập vào không hợp lệ. Lỗi khi lưu thông tin vào cơ sở dữ liệu. Không thể tải lên ảnh đại diện. |
| **Tải lên ảnh đại diện**       | Cho phép nhân viên kho tải lên ảnh đại diện mới. Hỗ trợ các định dạng ảnh phổ biến (JPG, PNG, GIF). Tự động resize ảnh về kích thước chuẩn. Kiểm tra kích thước file ảnh. Lưu ảnh vào hệ thống và cập nhật thông tin cá nhân.                                                    | Ảnh đại diện được tải lên và cập nhật thành công. Ảnh hiển thị chính xác trong giao diện. | File ảnh không đúng định dạng. Kích thước file quá lớn. Lỗi khi tải lên hoặc lưu ảnh.                   |

### 1.3 THAY ĐỔI MẬT KHẨU

#### 1.3.1 Thông tin màn hình:

| Screen        | Thay đổi mật khẩu                                                                        |
| ------------- | ---------------------------------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho thay đổi mật khẩu đăng nhập của mình để đảm bảo bảo mật tài khoản |
| Screen Access | Nhân viên kho chọn **Đổi mật khẩu** từ menu tài khoản                                    |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                     | Type         | Data                                                                                       | Description                                          |
| ------------------------ | ------------ | ------------------------------------------------------------------------------------------ | ---------------------------------------------------- |
| **Tiêu đề trang**        | Text         | Đổi mật khẩu                                                                               | Tiêu đề chính của trang đổi mật khẩu                 |
| **Mật khẩu hiện tại**    | Input (Pass) |                                                                                            | Ô nhập mật khẩu hiện tại để xác thực                 |
| **Mật khẩu mới**         | Input (Pass) |                                                                                            | Ô nhập mật khẩu mới                                  |
| **Xác nhận mật khẩu**    | Input (Pass) |                                                                                            | Ô nhập lại mật khẩu mới để xác nhận                  |
| **Hiển thị mật khẩu**    | Checkbox     |                                                                                            | Tùy chọn hiển thị/ẩn mật khẩu                        |
| **Yêu cầu mật khẩu**     | Text         | Mật khẩu phải có ít nhất 8 ký tự, bao gồm chữ hoa, chữ thường, số và ký tự đặc biệt        | Hiển thị yêu cầu về độ mạnh của mật khẩu mới         |
| **Nút đổi mật khẩu**     | Button       |                                                                                            | Nút thực hiện thay đổi mật khẩu                      |
| **Nút hủy**              | Button       |                                                                                            | Nút hủy thao tác đổi mật khẩu                        |
| **Thông báo lỗi**        | Alert        | Mật khẩu hiện tại không đúng<br>Mật khẩu mới không đủ mạnh<br>Xác nhận mật khẩu không khớp | Hiển thị các thông báo lỗi khi đổi mật khẩu thất bại |
| **Thông báo thành công** | Alert        | Đổi mật khẩu thành công                                                                    | Hiển thị thông báo khi đổi mật khẩu thành công       |

#### 1.3.3 Hành động và xử lý:

| Action Name                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                        | Success                                                                                                     | Failure                                                                                                                                |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Thay đổi mật khẩu**          | Cho phép nhân viên kho thay đổi mật khẩu đăng nhập của mình. Yêu cầu nhập mật khẩu hiện tại để xác thực. Nhập mật khẩu mới và xác nhận mật khẩu mới. Kiểm tra độ mạnh của mật khẩu mới (ít nhất 8 ký tự, bao gồm chữ hoa, chữ thường, số và ký tự đặc biệt). Xác thực mật khẩu hiện tại có đúng không. Kiểm tra mật khẩu mới và xác nhận mật khẩu có khớp nhau không. Cập nhật mật khẩu mới vào cơ sở dữ liệu. Ghi nhận lịch sử thay đổi mật khẩu. | Mật khẩu được thay đổi thành công. Tài khoản được bảo mật với mật khẩu mới. Lịch sử thay đổi được ghi nhận. | Mật khẩu hiện tại không đúng. Mật khẩu mới không đủ mạnh. Xác nhận mật khẩu không khớp. Lỗi khi cập nhật mật khẩu trong cơ sở dữ liệu. |
| **Xác thực mật khẩu hiện tại** | Kiểm tra mật khẩu hiện tại mà nhân viên nhập vào có đúng với mật khẩu đang lưu trong hệ thống không. Sử dụng mã hóa bảo mật để so sánh mật khẩu. Chỉ cho phép tiếp tục thay đổi mật khẩu khi xác thực thành công.                                                                                                                                                                                                                                  | Mật khẩu hiện tại được xác thực chính xác. Cho phép tiếp tục thay đổi mật khẩu.                             | Mật khẩu hiện tại không đúng. Yêu cầu nhập lại mật khẩu hiện tại.                                                                      |
| **Kiểm tra độ mạnh mật khẩu**  | Kiểm tra mật khẩu mới có đáp ứng các yêu cầu bảo mật không. Kiểm tra độ dài tối thiểu (8 ký tự). Kiểm tra có chứa chữ hoa, chữ thường, số và ký tự đặc biệt. Hiển thị thông báo lỗi nếu mật khẩu không đủ mạnh. Chỉ cho phép lưu mật khẩu khi đáp ứng tất cả yêu cầu.                                                                                                                                                                              | Mật khẩu mới đáp ứng tất cả yêu cầu bảo mật. Cho phép lưu mật khẩu mới.                                     | Mật khẩu mới không đủ mạnh. Hiển thị thông báo yêu cầu cải thiện mật khẩu.                                                             |

### 1.4 ĐĂNG XUẤT HỆ THỐNG

#### 1.4.1 Thông tin màn hình:

| Screen        | Đăng xuất hệ thống                                                              |
| ------------- | ------------------------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho đăng xuất khỏi hệ thống một cách an toàn                 |
| Screen Access | Nhân viên kho chọn **Đăng xuất** từ menu tài khoản hoặc click vào nút đăng xuất |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                     | Type     | Data                             | Description                                         |
| ------------------------ | -------- | -------------------------------- | --------------------------------------------------- |
| **Xác nhận đăng xuất**   | Modal    | Bạn có chắc chắn muốn đăng xuất? | Modal xác nhận trước khi đăng xuất                  |
| **Nút xác nhận**         | Button   | Có, đăng xuất                    | Nút xác nhận đăng xuất                              |
| **Nút hủy**              | Button   | Hủy                              | Nút hủy thao tác đăng xuất                          |
| **Thông báo thành công** | Alert    | Đăng xuất thành công             | Hiển thị thông báo khi đăng xuất thành công         |
| **Chuyển hướng**         | Redirect | Chuyển về trang đăng nhập        | Tự động chuyển về trang đăng nhập sau khi đăng xuất |

#### 1.4.3 Hành động và xử lý:

| Action Name             | Description                                                                                                                                                                                                                                                                                       | Success                                                                              | Failure                                                                 |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ----------------------------------------------------------------------- |
| **Đăng xuất hệ thống**  | Cho phép nhân viên kho đăng xuất khỏi hệ thống một cách an toàn. Hiển thị modal xác nhận trước khi đăng xuất. Hủy phiên đăng nhập hiện tại. Xóa thông tin xác thực khỏi trình duyệt. Ghi nhận thời gian đăng xuất và địa chỉ IP. Chuyển hướng về trang đăng nhập. Thông báo đăng xuất thành công. | Đăng xuất thành công và chuyển về trang đăng nhập. Phiên đăng nhập được hủy an toàn. | Lỗi khi hủy phiên đăng nhập. Không thể chuyển hướng về trang đăng nhập. |
| **Xác nhận đăng xuất**  | Hiển thị modal xác nhận trước khi thực hiện đăng xuất để tránh đăng xuất nhầm. Cho phép nhân viên hủy thao tác đăng xuất nếu không muốn. Chỉ thực hiện đăng xuất khi có xác nhận rõ ràng từ người dùng.                                                                                           | Modal xác nhận hiển thị chính xác. Người dùng có thể xác nhận hoặc hủy đăng xuất.    | Modal xác nhận không hiển thị. Không thể hủy thao tác đăng xuất.        |
| **Hủy phiên đăng nhập** | Hủy phiên đăng nhập hiện tại của nhân viên kho một cách an toàn. Xóa token xác thực khỏi hệ thống. Xóa thông tin phiên đăng nhập khỏi cơ sở dữ liệu. Đảm bảo không thể truy cập vào hệ thống sau khi đăng xuất.                                                                                   | Phiên đăng nhập được hủy thành công. Token xác thực được xóa khỏi hệ thống.          | Không thể hủy phiên đăng nhập. Token xác thực vẫn còn tồn tại.          |
