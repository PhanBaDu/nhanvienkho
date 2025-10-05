# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng bảo mật của Nhân viên kho_

## MỤC LỤC

1. [Chức năng bảo mật](#1-chức-năng-bảo-mật)
   - 1.1 [Quản lý phiên đăng nhập](#11-quản-lý-phiên-đăng-nhập)
   - 1.2 [Theo dõi hoạt động hệ thống](#12-theo-dõi-hoạt-động-hệ-thống)
   - 1.3 [Báo cáo bảo mật](#13-báo-cáo-bảo-mật)
   - 1.4 [Cảnh báo bảo mật](#14-cảnh-báo-bảo-mật)

---

## 1. CHỨC NĂNG BẢO MẬT

### 1.1 QUẢN LÝ PHIÊN ĐĂNG NHẬP

#### 1.1.1 Thông tin màn hình:

| Screen        | Quản lý phiên đăng nhập                                    |
| ------------- | ---------------------------------------------------------- |
| Description   | Quản lý các phiên đăng nhập và kiểm soát truy cập hệ thống |
| Screen Access | Nhân viên kho chọn **Bảo mật** từ menu chính               |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                          | Type         | Data                                                                                                            | Description                                        |
| ----------------------------- | ------------ | --------------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| **Tiêu đề trang**             | Text         | Quản lý phiên đăng nhập                                                                                         | Tiêu đề chính của trang quản lý phiên đăng nhập    |
| **Thông tin phiên hiện tại**  | Card         | Phiên đăng nhập: SESS001<br>Thời gian đăng nhập: 2023-11-20 08:30<br>IP: 192.168.1.100<br>Trạng thái: Hoạt động | Hiển thị thông tin phiên đăng nhập hiện tại        |
| **Bộ lọc phiên đăng nhập**    | Form         | Từ ngày<br>Đến ngày<br>Trạng thái<br>Địa chỉ IP                                                                 | Form lọc phiên đăng nhập theo tiêu chí             |
| **Từ ngày**                   | Input (Date) | 2023-11-01                                                                                                      | Ngày bắt đầu xem phiên đăng nhập                   |
| **Đến ngày**                  | Input (Date) | 2023-11-30                                                                                                      | Ngày kết thúc xem phiên đăng nhập                  |
| **Trạng thái**                | Dropdown     | Tất cả<br>Hoạt động<br>Đã kết thúc<br>Bị khóa<br>Bất thường                                                     | Lọc phiên đăng nhập theo trạng thái                |
| **Địa chỉ IP**                | Input (Text) | 192.168.1.100                                                                                                   | Ô nhập địa chỉ IP để lọc phiên đăng nhập           |
| **Danh sách phiên đăng nhập** | Table        | Mã phiên<br>Thời gian đăng nhập<br>Địa chỉ IP<br>Thiết bị<br>Trạng thái<br>Thao tác                             | Hiển thị danh sách phiên đăng nhập dưới dạng bảng  |
| **Mã phiên**                  | Text         | SESS001                                                                                                         | Mã định danh của phiên đăng nhập                   |
| **Thời gian đăng nhập**       | Text         | 2023-11-20 08:30                                                                                                | Thời gian bắt đầu phiên đăng nhập                  |
| **Địa chỉ IP**                | Text         | 192.168.1.100                                                                                                   | Địa chỉ IP của thiết bị đăng nhập                  |
| **Thiết bị**                  | Text         | Windows 10 - Chrome 119.0                                                                                       | Thông tin thiết bị và trình duyệt                  |
| **Trạng thái**                | Badge        | Hoạt động<br>Đã kết thúc<br>Bị khóa<br>Bất thường                                                               | Trạng thái hiện tại của phiên đăng nhập            |
| **Thao tác**                  | Button Group | Xem chi tiết<br>Kết thúc phiên<br>Khóa phiên<br>Xóa lịch sử                                                     | Các nút chức năng để thao tác trên phiên đăng nhập |
| **Nút kết thúc tất cả**       | Button       |                                                                                                                 | Nút kết thúc tất cả phiên đăng nhập khác           |
| **Nút xuất báo cáo**          | Button       |                                                                                                                 | Nút xuất báo cáo phiên đăng nhập                   |
| **Phân trang**                | Pagination   | Trang 1/20                                                                                                      | Điều hướng giữa các trang                          |

#### 1.1.3 Hành động và xử lý:

| Action Name                       | Description                                                                                                                                                                                                                                                         | Success                                                                                          | Failure                                                                          |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| **Xem danh sách phiên đăng nhập** | Hiển thị danh sách các phiên đăng nhập của nhân viên kho. Bao gồm thông tin về mã phiên, thời gian đăng nhập, địa chỉ IP, thiết bị và trạng thái. Cung cấp bộ lọc theo thời gian, trạng thái và địa chỉ IP. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. | Danh sách phiên đăng nhập được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. | Không thể tải danh sách phiên đăng nhập do lỗi hệ thống. Bộ lọc không hoạt động. |
| **Xem chi tiết phiên đăng nhập**  | Hiển thị chi tiết phiên đăng nhập được chọn. Bao gồm thông tin đầy đủ về phiên đăng nhập, hoạt động trong phiên, thời gian kết thúc và lý do kết thúc. Cho phép xem lịch sử hoạt động trong phiên.                                                                  | Chi tiết phiên đăng nhập được hiển thị đầy đủ và chính xác.                                      | Không thể tải chi tiết phiên đăng nhập. Thông tin hiển thị không đầy đủ.         |
| **Kết thúc phiên đăng nhập**      | Cho phép nhân viên kho kết thúc phiên đăng nhập đang hoạt động. Chọn phiên đăng nhập cần kết thúc. Xác nhận việc kết thúc phiên. Ghi nhận thời gian kết thúc và lý do kết thúc. Gửi thông báo cho người dùng về việc kết thúc phiên.                                | Phiên đăng nhập được kết thúc thành công. Người dùng được thông báo.                             | Không thể kết thúc phiên đăng nhập do lỗi hệ thống. Lỗi khi gửi thông báo.       |
| **Khóa phiên đăng nhập**          | Cho phép nhân viên kho khóa phiên đăng nhập nếu phát hiện hoạt động bất thường. Chọn phiên đăng nhập cần khóa. Nhập lý do khóa phiên. Cập nhật trạng thái phiên thành "Bị khóa". Gửi thông báo cho người dùng về việc khóa phiên.                                   | Phiên đăng nhập được khóa thành công. Người dùng được thông báo.                                 | Không thể khóa phiên đăng nhập do lỗi hệ thống. Lỗi khi gửi thông báo.           |
| **Xóa lịch sử phiên đăng nhập**   | Cho phép nhân viên kho xóa lịch sử phiên đăng nhập cũ. Chọn phiên đăng nhập cần xóa. Xác nhận việc xóa lịch sử. Ghi nhận thời gian xóa và người thực hiện. Lưu ý: Chỉ có thể xóa phiên đã kết thúc.                                                                 | Lịch sử phiên đăng nhập được xóa thành công.                                                     | Không thể xóa lịch sử phiên đăng nhập do lỗi hệ thống.                           |

### 1.2 THEO DÕI HOẠT ĐỘNG HỆ THỐNG

#### 1.2.1 Thông tin màn hình:

| Screen        | Theo dõi hoạt động hệ thống                                   |
| ------------- | ------------------------------------------------------------- |
| Description   | Theo dõi và ghi nhận các hoạt động trong hệ thống quản lý kho |
| Screen Access | Nhân viên kho chọn **Theo dõi hoạt động** từ menu bảo mật     |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                    | Type         | Data                                                                                 | Description                                          |
| ----------------------- | ------------ | ------------------------------------------------------------------------------------ | ---------------------------------------------------- |
| **Tiêu đề trang**       | Text         | Theo dõi hoạt động hệ thống                                                          | Tiêu đề chính của trang theo dõi hoạt động           |
| **Bộ lọc hoạt động**    | Form         | Từ ngày<br>Đến ngày<br>Loại hoạt động<br>Người thực hiện<br>Mức độ                   | Form lọc hoạt động hệ thống theo tiêu chí            |
| **Từ ngày**             | Input (Date) | 2023-11-01                                                                           | Ngày bắt đầu theo dõi hoạt động                      |
| **Đến ngày**            | Input (Date) | 2023-11-30                                                                           | Ngày kết thúc theo dõi hoạt động                     |
| **Loại hoạt động**      | Dropdown     | Tất cả<br>Đăng nhập<br>Đăng xuất<br>Thao tác dữ liệu<br>Bảo mật<br>Hệ thống          | Lọc hoạt động theo loại                              |
| **Người thực hiện**     | Input (Text) | Nguyễn Văn A                                                                         | Ô nhập tên người thực hiện hoạt động                 |
| **Mức độ**              | Dropdown     | Tất cả<br>Thông tin<br>Cảnh báo<br>Lỗi<br>Nghiêm trọng                               | Lọc hoạt động theo mức độ                            |
| **Thống kê hoạt động**  | Card Group   | Tổng hoạt động: 1,250<br>Thành công: 1,180<br>Lỗi: 45<br>Cảnh báo: 25                | Hiển thị thống kê tổng quan về hoạt động hệ thống    |
| **Biểu đồ hoạt động**   | Chart        | Biểu đồ đường thể hiện xu hướng hoạt động theo thời gian                             | Biểu đồ trực quan hóa hoạt động hệ thống             |
| **Danh sách hoạt động** | Table        | Thời gian<br>Loại<br>Mô tả<br>Người thực hiện<br>IP<br>Mức độ<br>Kết quả<br>Thao tác | Hiển thị danh sách hoạt động hệ thống dưới dạng bảng |
| **Thời gian**           | Text         | 2023-11-20 14:30                                                                     | Thời gian thực hiện hoạt động                        |
| **Loại**                | Badge        | Đăng nhập<br>Đăng xuất<br>Thao tác dữ liệu<br>Bảo mật<br>Hệ thống                    | Loại hoạt động được thực hiện                        |
| **Mô tả**               | Text         | Đăng nhập thành công vào hệ thống                                                    | Mô tả chi tiết về hoạt động                          |
| **Người thực hiện**     | Text         | Nguyễn Văn A                                                                         | Tên người thực hiện hoạt động                        |
| **IP**                  | Text         | 192.168.1.100                                                                        | Địa chỉ IP của thiết bị thực hiện hoạt động          |
| **Mức độ**              | Badge        | Thông tin<br>Cảnh báo<br>Lỗi<br>Nghiêm trọng                                         | Mức độ quan trọng của hoạt động                      |
| **Kết quả**             | Badge        | Thành công<br>Thất bại<br>Lỗi                                                        | Kết quả thực hiện hoạt động                          |
| **Thao tác**            | Button Group | Xem chi tiết<br>Xuất log<br>Báo cáo lỗi                                              | Các nút chức năng để thao tác trên hoạt động         |
| **Nút xuất log**        | Button       |                                                                                      | Nút xuất log hoạt động hệ thống                      |
| **Nút báo cáo lỗi**     | Button       |                                                                                      | Nút báo cáo lỗi hệ thống cho quản trị viên           |
| **Phân trang**          | Pagination   | Trang 1/100                                                                          | Điều hướng giữa các trang                            |

#### 1.2.3 Hành động và xử lý:

| Action Name                     | Description                                                                                                                                                                                                                                                                                                                             | Success                                                                                                            | Failure                                                                                                       |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------- |
| **Xem danh sách hoạt động**     | Hiển thị danh sách các hoạt động trong hệ thống quản lý kho. Bao gồm thông tin về thời gian, loại, mô tả, người thực hiện, IP, mức độ và kết quả. Cung cấp bộ lọc theo thời gian, loại hoạt động, người thực hiện và mức độ. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. Hiển thị thống kê tổng quan về hoạt động hệ thống. | Danh sách hoạt động được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách hoạt động do lỗi hệ thống. Bộ lọc không hoạt động. Thống kê hiển thị không chính xác. |
| **Xem chi tiết hoạt động**      | Hiển thị chi tiết hoạt động được chọn. Bao gồm thông tin đầy đủ về hoạt động, dữ liệu liên quan, thông tin thiết bị và môi trường thực hiện. Cho phép xem log chi tiết của hoạt động.                                                                                                                                                   | Chi tiết hoạt động được hiển thị đầy đủ và chính xác.                                                              | Không thể tải chi tiết hoạt động. Thông tin hiển thị không đầy đủ.                                            |
| **Lọc hoạt động theo tiêu chí** | Cho phép nhân viên kho lọc hoạt động hệ thống theo các tiêu chí khác nhau. Lọc theo khoảng thời gian (từ ngày đến ngày). Lọc theo loại hoạt động (đăng nhập, đăng xuất, thao tác dữ liệu, bảo mật, hệ thống). Lọc theo người thực hiện. Lọc theo mức độ (thông tin, cảnh báo, lỗi, nghiêm trọng).                                       | Hoạt động được lọc chính xác theo tiêu chí đã chọn.                                                                | Bộ lọc không hoạt động. Kết quả lọc không chính xác.                                                          |
| **Xuất log hoạt động**          | Cho phép nhân viên kho xuất log hoạt động hệ thống dưới dạng file text hoặc CSV. Bao gồm danh sách chi tiết các hoạt động, thống kê tổng quan và biểu đồ xu hướng. Định dạng log theo chuẩn của hệ thống. Cho phép tùy chỉnh nội dung log trước khi xuất.                                                                               | Log hoạt động được xuất thành công dưới định dạng đã chọn.                                                         | Không thể xuất log hoạt động. Lỗi khi tạo file log.                                                           |
| **Báo cáo lỗi hệ thống**        | Cho phép nhân viên kho báo cáo lỗi hệ thống cho quản trị viên. Chọn loại lỗi từ danh sách có sẵn hoặc nhập mô tả lỗi tùy chỉnh. Thêm thông tin chi tiết về lỗi và cách tái hiện. Gửi báo cáo lỗi cho quản trị viên.                                                                                                                     | Báo cáo lỗi được gửi thành công cho quản trị viên.                                                                 | Không thể gửi báo cáo lỗi. Lỗi khi tạo báo cáo lỗi.                                                           |

### 1.3 BÁO CÁO BẢO MẬT

#### 1.3.1 Thông tin màn hình:

| Screen        | Báo cáo bảo mật                                        |
| ------------- | ------------------------------------------------------ |
| Description   | Tạo báo cáo về tình hình bảo mật và hoạt động hệ thống |
| Screen Access | Nhân viên kho chọn **Báo cáo bảo mật** từ menu bảo mật |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                          | Type         | Data                                                                                                      | Description                                        |
| ----------------------------- | ------------ | --------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| **Tiêu đề trang**             | Text         | Báo cáo bảo mật                                                                                           | Tiêu đề chính của trang báo cáo bảo mật            |
| **Bộ lọc báo cáo**            | Form         | Từ ngày<br>Đến ngày<br>Loại báo cáo<br>Mức độ ưu tiên                                                     | Form lọc báo cáo bảo mật theo tiêu chí             |
| **Từ ngày**                   | Input (Date) | 2023-11-01                                                                                                | Ngày bắt đầu tạo báo cáo                           |
| **Đến ngày**                  | Input (Date) | 2023-11-30                                                                                                | Ngày kết thúc tạo báo cáo                          |
| **Loại báo cáo**              | Dropdown     | Tất cả<br>Đăng nhập<br>Hoạt động hệ thống<br>Lỗi bảo mật<br>Vi phạm chính sách                            | Lọc báo cáo theo loại                              |
| **Mức độ ưu tiên**            | Dropdown     | Tất cả<br>Cao<br>Trung bình<br>Thấp                                                                       | Lọc báo cáo theo mức độ ưu tiên                    |
| **Thống kê bảo mật**          | Card Group   | Tổng đăng nhập: 1,250<br>Đăng nhập thành công: 1,180<br>Đăng nhập thất bại: 45<br>Hoạt động bất thường: 8 | Hiển thị thống kê tổng quan về bảo mật             |
| **Biểu đồ bảo mật**           | Chart        | Biểu đồ cột thể hiện số lượng sự kiện bảo mật theo loại                                                   | Biểu đồ trực quan hóa tình hình bảo mật            |
| **Danh sách sự kiện bảo mật** | Table        | Thời gian<br>Loại<br>Mô tả<br>Mức độ<br>Trạng thái<br>Người thực hiện<br>Thao tác                         | Hiển thị danh sách sự kiện bảo mật dưới dạng bảng  |
| **Thời gian**                 | Text         | 2023-11-20 14:30                                                                                          | Thời gian xảy ra sự kiện bảo mật                   |
| **Loại**                      | Badge        | Đăng nhập<br>Hoạt động hệ thống<br>Lỗi bảo mật<br>Vi phạm chính sách                                      | Loại sự kiện bảo mật                               |
| **Mô tả**                     | Text         | Đăng nhập thất bại từ IP không xác định                                                                   | Mô tả chi tiết về sự kiện bảo mật                  |
| **Mức độ**                    | Badge        | Cao<br>Trung bình<br>Thấp                                                                                 | Mức độ ưu tiên của sự kiện bảo mật                 |
| **Trạng thái**                | Badge        | Đã xử lý<br>Đang xử lý<br>Chờ xử lý<br>Bỏ qua                                                             | Trạng thái xử lý sự kiện bảo mật                   |
| **Người thực hiện**           | Text         | Nguyễn Văn A                                                                                              | Tên người thực hiện hoặc liên quan đến sự kiện     |
| **Thao tác**                  | Button Group | Xem chi tiết<br>Xử lý<br>Bỏ qua<br>Báo cáo                                                                | Các nút chức năng để thao tác trên sự kiện bảo mật |
| **Nút tạo báo cáo**           | Button       |                                                                                                           | Nút tạo báo cáo bảo mật theo tiêu chí đã chọn      |
| **Nút xuất báo cáo**          | Button       |                                                                                                           | Nút xuất báo cáo bảo mật dưới dạng PDF hoặc Excel  |
| **Nút gửi báo cáo**           | Button       |                                                                                                           | Nút gửi báo cáo bảo mật cho quản trị viên          |
| **Phân trang**                | Pagination   | Trang 1/50                                                                                                | Điều hướng giữa các trang                          |

#### 1.3.3 Hành động và xử lý:

| Action Name                   | Description                                                                                                                                                                                                                                                                                                            | Success                                                                                                             | Failure                                                                                             |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **Tạo báo cáo bảo mật**       | Cho phép nhân viên kho tạo báo cáo về tình hình bảo mật hệ thống. Chọn khoảng thời gian và loại báo cáo cần tạo. Hiển thị thống kê tổng quan về bảo mật bao gồm số lượng đăng nhập, hoạt động bất thường và lỗi bảo mật. Tạo biểu đồ trực quan hóa tình hình bảo mật. Hiển thị danh sách chi tiết các sự kiện bảo mật. | Báo cáo bảo mật được tạo thành công với đầy đủ thông tin. Biểu đồ hiển thị chính xác. Thống kê được tính toán đúng. | Không thể tạo báo cáo bảo mật do lỗi hệ thống. Biểu đồ không hiển thị. Thống kê được tính toán sai. |
| **Lọc báo cáo theo tiêu chí** | Cho phép nhân viên kho lọc báo cáo bảo mật theo các tiêu chí khác nhau. Lọc theo khoảng thời gian (từ ngày đến ngày). Lọc theo loại báo cáo (đăng nhập, hoạt động hệ thống, lỗi bảo mật, vi phạm chính sách). Lọc theo mức độ ưu tiên (cao, trung bình, thấp). Cập nhật báo cáo theo tiêu chí đã chọn.                 | Báo cáo được lọc chính xác theo tiêu chí đã chọn. Kết quả lọc hiển thị đúng.                                        | Bộ lọc không hoạt động. Kết quả lọc không chính xác.                                                |
| **Xử lý sự kiện bảo mật**     | Cho phép nhân viên kho xử lý các sự kiện bảo mật được phát hiện. Chọn sự kiện bảo mật cần xử lý. Cập nhật trạng thái sự kiện (đã xử lý, đang xử lý, chờ xử lý, bỏ qua). Thêm ghi chú về việc xử lý sự kiện. Gửi thông báo cho quản trị viên nếu cần.                                                                   | Sự kiện bảo mật được xử lý thành công. Quản trị viên được thông báo nếu cần.                                        | Không thể xử lý sự kiện bảo mật do lỗi hệ thống. Lỗi khi gửi thông báo.                             |
| **Xuất báo cáo bảo mật**      | Cho phép nhân viên kho xuất báo cáo bảo mật dưới dạng PDF hoặc Excel. Bao gồm thống kê tổng quan, biểu đồ và danh sách chi tiết sự kiện bảo mật. Định dạng báo cáo theo chuẩn của công ty. Cho phép tùy chỉnh nội dung báo cáo trước khi xuất.                                                                         | Báo cáo bảo mật được xuất thành công dưới định dạng đã chọn.                                                        | Không thể xuất báo cáo bảo mật. Lỗi khi tạo file báo cáo.                                           |
| **Gửi báo cáo bảo mật**       | Cho phép nhân viên kho gửi báo cáo bảo mật cho quản trị viên và các bộ phận liên quan. Chọn người nhận báo cáo. Thêm ghi chú hoặc lời nhắn kèm theo báo cáo. Gửi báo cáo qua email hoặc hệ thống nội bộ. Lưu lịch sử gửi báo cáo.                                                                                      | Báo cáo bảo mật được gửi thành công đến các bộ phận liên quan. Lịch sử gửi được lưu.                                | Không thể gửi báo cáo bảo mật. Lỗi khi lưu lịch sử gửi.                                             |

### 1.4 CẢNH BÁO BẢO MẬT

#### 1.4.1 Thông tin màn hình:

| Screen        | Cảnh báo bảo mật                                        |
| ------------- | ------------------------------------------------------- |
| Description   | Quản lý và xử lý các cảnh báo bảo mật hệ thống          |
| Screen Access | Nhân viên kho chọn **Cảnh báo bảo mật** từ menu bảo mật |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                    | Type         | Data                                                                                       | Description                                         |
| ----------------------- | ------------ | ------------------------------------------------------------------------------------------ | --------------------------------------------------- |
| **Tiêu đề trang**       | Text         | Cảnh báo bảo mật                                                                           | Tiêu đề chính của trang cảnh báo bảo mật            |
| **Thống kê cảnh báo**   | Card Group   | Cảnh báo mới: 5<br>Đang xử lý: 3<br>Đã xử lý: 45<br>Cảnh báo nghiêm trọng: 2               | Hiển thị thống kê tổng quan về cảnh báo bảo mật     |
| **Bộ lọc cảnh báo**     | Form         | Mức độ<br>Trạng thái<br>Loại cảnh báo<br>Thời gian                                         | Form lọc cảnh báo bảo mật theo tiêu chí             |
| **Mức độ**              | Dropdown     | Tất cả<br>Nghiêm trọng<br>Cao<br>Trung bình<br>Thấp                                        | Lọc cảnh báo theo mức độ                            |
| **Trạng thái**          | Dropdown     | Tất cả<br>Mới<br>Đang xử lý<br>Đã xử lý<br>Bỏ qua                                          | Lọc cảnh báo theo trạng thái                        |
| **Loại cảnh báo**       | Dropdown     | Tất cả<br>Đăng nhập bất thường<br>Hoạt động đáng ngờ<br>Lỗi hệ thống<br>Vi phạm chính sách | Lọc cảnh báo theo loại                              |
| **Thời gian**           | Input (Date) | 2023-11-20                                                                                 | Ô nhập thời gian xảy ra cảnh báo                    |
| **Danh sách cảnh báo**  | Table        | Thời gian<br>Loại<br>Mô tả<br>Mức độ<br>Trạng thái<br>Người xử lý<br>Thao tác              | Hiển thị danh sách cảnh báo bảo mật dưới dạng bảng  |
| **Thời gian**           | Text         | 2023-11-20 14:30                                                                           | Thời gian xảy ra cảnh báo                           |
| **Loại**                | Badge        | Đăng nhập bất thường<br>Hoạt động đáng ngờ<br>Lỗi hệ thống<br>Vi phạm chính sách           | Loại cảnh báo bảo mật                               |
| **Mô tả**               | Text         | Đăng nhập thất bại 5 lần liên tiếp từ IP 192.168.1.200                                     | Mô tả chi tiết về cảnh báo bảo mật                  |
| **Mức độ**              | Badge        | Nghiêm trọng<br>Cao<br>Trung bình<br>Thấp                                                  | Mức độ ưu tiên của cảnh báo                         |
| **Trạng thái**          | Badge        | Mới<br>Đang xử lý<br>Đã xử lý<br>Bỏ qua                                                    | Trạng thái xử lý cảnh báo                           |
| **Người xử lý**         | Text         | Nguyễn Văn A                                                                               | Tên người xử lý cảnh báo                            |
| **Thao tác**            | Button Group | Xem chi tiết<br>Xử lý<br>Bỏ qua<br>Báo cáo                                                 | Các nút chức năng để thao tác trên cảnh báo bảo mật |
| **Nút xử lý hàng loạt** | Button       |                                                                                            | Nút xử lý nhiều cảnh báo cùng lúc                   |
| **Nút xuất báo cáo**    | Button       |                                                                                            | Nút xuất báo cáo cảnh báo bảo mật                   |
| **Phân trang**          | Pagination   | Trang 1/25                                                                                 | Điều hướng giữa các trang                           |

#### 1.4.3 Hành động và xử lý:

| Action Name                  | Description                                                                                                                                                                                                                                                                                                     | Success                                                                                                           | Failure                                                                                                      |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Xem danh sách cảnh báo**   | Hiển thị danh sách các cảnh báo bảo mật hệ thống. Bao gồm thông tin về thời gian, loại, mô tả, mức độ, trạng thái và người xử lý. Cung cấp bộ lọc theo mức độ, trạng thái, loại cảnh báo và thời gian. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. Hiển thị thống kê tổng quan về cảnh báo bảo mật. | Danh sách cảnh báo được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách cảnh báo do lỗi hệ thống. Bộ lọc không hoạt động. Thống kê hiển thị không chính xác. |
| **Xem chi tiết cảnh báo**    | Hiển thị chi tiết cảnh báo bảo mật được chọn. Bao gồm thông tin đầy đủ về cảnh báo, dữ liệu liên quan, thông tin thiết bị và môi trường xảy ra cảnh báo. Cho phép xem log chi tiết của cảnh báo.                                                                                                                | Chi tiết cảnh báo được hiển thị đầy đủ và chính xác.                                                              | Không thể tải chi tiết cảnh báo. Thông tin hiển thị không đầy đủ.                                            |
| **Xử lý cảnh báo bảo mật**   | Cho phép nhân viên kho xử lý cảnh báo bảo mật được phát hiện. Chọn cảnh báo cần xử lý. Cập nhật trạng thái cảnh báo (đang xử lý, đã xử lý, bỏ qua). Thêm ghi chú về việc xử lý cảnh báo. Gửi thông báo cho quản trị viên nếu cần.                                                                               | Cảnh báo bảo mật được xử lý thành công. Quản trị viên được thông báo nếu cần.                                     | Không thể xử lý cảnh báo bảo mật do lỗi hệ thống. Lỗi khi gửi thông báo.                                     |
| **Bỏ qua cảnh báo**          | Cho phép nhân viên kho bỏ qua cảnh báo bảo mật nếu không cần thiết. Chọn cảnh báo cần bỏ qua. Nhập lý do bỏ qua cảnh báo. Cập nhật trạng thái cảnh báo thành "Bỏ qua". Ghi nhận thời gian bỏ qua và người thực hiện.                                                                                            | Cảnh báo được bỏ qua thành công. Lý do bỏ qua được ghi nhận.                                                      | Không thể bỏ qua cảnh báo do lỗi hệ thống.                                                                   |
| **Xử lý hàng loạt cảnh báo** | Cho phép nhân viên kho xử lý nhiều cảnh báo bảo mật cùng lúc. Chọn các cảnh báo cần xử lý. Chọn hành động xử lý (đã xử lý, bỏ qua). Thêm ghi chú chung cho tất cả cảnh báo. Thực hiện xử lý hàng loạt.                                                                                                          | Tất cả cảnh báo được xử lý thành công.                                                                            | Một số cảnh báo không được xử lý do lỗi.                                                                     |
| **Báo cáo cảnh báo**         | Cho phép nhân viên kho báo cáo cảnh báo bảo mật cho quản trị viên. Chọn cảnh báo cần báo cáo. Thêm thông tin chi tiết về cảnh báo. Gửi báo cáo cho quản trị viên. Tạo lịch sử báo cáo cảnh báo.                                                                                                                 | Báo cáo cảnh báo được gửi thành công cho quản trị viên. Lịch sử báo cáo được tạo.                                 | Không thể gửi báo cáo cảnh báo. Lỗi khi tạo lịch sử báo cáo.                                                 |
