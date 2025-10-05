# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý kho của Nhân viên kho_

## MỤC LỤC

1. [Chức năng quản lý kho](#1-chức-năng-quản-lý-kho)
   - 1.1 [Quản lý khu vực kho](#11-quản-lý-khu-vực-kho)
   - 1.2 [Quản lý vị trí sách](#12-quản-lý-vị-trí-sách)
   - 1.3 [Theo dõi tình trạng kho](#13-theo-dõi-tình-trạng-kho)
   - 1.4 [Quản lý thiết bị kho](#14-quản-lý-thiết-bị-kho)

---

## 1. CHỨC NĂNG QUẢN LÝ KHO

### 1.1 QUẢN LÝ KHU VỰC KHO

#### 1.1.1 Thông tin màn hình:

| Screen        | Quản lý khu vực kho                              |
| ------------- | ------------------------------------------------ |
| Description   | Quản lý các khu vực và phân khu trong kho hàng   |
| Screen Access | Nhân viên kho chọn **Quản lý kho** từ menu chính |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                  | Type            | Data                                                                                | Description                                         |
| --------------------- | --------------- | ----------------------------------------------------------------------------------- | --------------------------------------------------- |
| **Tiêu đề trang**     | Text            | Quản lý khu vực kho                                                                 | Tiêu đề chính của trang quản lý khu vực kho         |
| **Thống kê khu vực**  | Card Group      | Tổng khu vực: 8<br>Khu vực hoạt động: 7<br>Khu vực bảo trì: 1<br>Sức chứa: 85%      | Hiển thị thống kê tổng quan về khu vực kho          |
| **Bộ lọc khu vực**    | Form            | Trạng thái<br>Loại khu vực<br>Mức độ sử dụng<br>Tìm kiếm                            | Form lọc khu vực kho theo tiêu chí                  |
| **Trạng thái**        | Dropdown        | Tất cả<br>Hoạt động<br>Bảo trì<br>Ngừng hoạt động<br>Đầy                            | Lọc khu vực theo trạng thái                         |
| **Loại khu vực**      | Dropdown        | Tất cả<br>Khu A (Văn học)<br>Khu B (Khoa học)<br>Khu C (Lịch sử)<br>Khu D (Kinh tế) | Lọc khu vực theo loại                               |
| **Mức độ sử dụng**    | Dropdown        | Tất cả<br>Dưới 50%<br>50-80%<br>Trên 80%<br>Đầy                                     | Lọc khu vực theo mức độ sử dụng                     |
| **Tìm kiếm**          | Input (Text)    |                                                                                     | Ô nhập từ khóa tìm kiếm khu vực                     |
| **Danh sách khu vực** | Table           | Mã khu vực<br>Tên khu vực<br>Loại<br>Sức chứa<br>Sử dụng<br>Trạng thái<br>Thao tác  | Hiển thị danh sách khu vực kho dưới dạng bảng       |
| **Mã khu vực**        | Text + Badge    | KHU001                                                                              | Mã định danh của khu vực, kèm theo badge trạng thái |
| **Tên khu vực**       | Text            | Khu A - Văn học                                                                     | Tên khu vực kho                                     |
| **Loại**              | Badge           | Văn học<br>Khoa học<br>Lịch sử<br>Kinh tế<br>Giáo dục                               | Loại sách được lưu trữ trong khu vực                |
| **Sức chứa**          | Text            | 1,000 cuốn                                                                          | Sức chứa tối đa của khu vực                         |
| **Sử dụng**           | Text + Progress | 850 cuốn (85%)                                                                      | Số lượng sách hiện có và tỷ lệ sử dụng              |
| **Trạng thái**        | Badge           | Hoạt động<br>Bảo trì<br>Ngừng hoạt động<br>Đầy                                      | Trạng thái hiện tại của khu vực                     |
| **Thao tác**          | Button Group    | Xem chi tiết<br>Chỉnh sửa<br>Cập nhật trạng thái<br>Xem báo cáo                     | Các nút chức năng để thao tác trên khu vực kho      |
| **Nút thêm khu vực**  | Button          |                                                                                     | Nút thêm khu vực kho mới                            |
| **Nút xuất báo cáo**  | Button          |                                                                                     | Nút xuất báo cáo khu vực kho                        |
| **Phân trang**        | Pagination      | Trang 1/5                                                                           | Điều hướng giữa các trang                           |

#### 1.1.3 Hành động và xử lý:

| Action Name                     | Description                                                                                                                                                                                                                                                                                                               | Success                                                                                                          | Failure                                                                                                     |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| **Xem danh sách khu vực**       | Hiển thị danh sách các khu vực trong kho hàng. Bao gồm thông tin về mã khu vực, tên khu vực, loại, sức chứa, mức độ sử dụng và trạng thái. Cung cấp bộ lọc theo trạng thái, loại khu vực, mức độ sử dụng và tìm kiếm. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. Hiển thị thống kê tổng quan về khu vực kho. | Danh sách khu vực được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách khu vực do lỗi hệ thống. Bộ lọc không hoạt động. Thống kê hiển thị không chính xác. |
| **Xem chi tiết khu vực**        | Hiển thị chi tiết khu vực kho được chọn. Bao gồm thông tin đầy đủ về khu vực, danh sách sách lưu trữ, lịch sử hoạt động và báo cáo sử dụng. Cho phép xem sơ đồ bố trí khu vực.                                                                                                                                            | Chi tiết khu vực được hiển thị đầy đủ và chính xác.                                                              | Không thể tải chi tiết khu vực. Thông tin hiển thị không đầy đủ.                                            |
| **Thêm khu vực mới**            | Cho phép nhân viên kho thêm khu vực kho mới. Nhập thông tin cơ bản về khu vực (tên, loại, sức chứa). Thiết lập vị trí và kích thước khu vực. Cấu hình các quy tắc quản lý khu vực. Lưu thông tin khu vực vào hệ thống.                                                                                                    | Khu vực mới được tạo thành công. Thông tin được lưu vào hệ thống.                                                | Không thể tạo khu vực mới do lỗi hệ thống. Thông tin không được lưu.                                        |
| **Chỉnh sửa khu vực**           | Cho phép nhân viên kho chỉnh sửa thông tin khu vực kho. Cập nhật tên, loại và sức chứa khu vực. Thay đổi vị trí và kích thước khu vực. Cập nhật các quy tắc quản lý khu vực. Lưu thay đổi vào hệ thống.                                                                                                                   | Thông tin khu vực được cập nhật thành công. Thay đổi được lưu vào hệ thống.                                      | Không thể cập nhật thông tin khu vực do lỗi hệ thống. Thay đổi không được lưu.                              |
| **Cập nhật trạng thái khu vực** | Cho phép nhân viên kho cập nhật trạng thái khu vực kho. Thay đổi trạng thái (hoạt động, bảo trì, ngừng hoạt động, đầy). Thêm ghi chú về việc thay đổi trạng thái. Ghi nhận thời gian và người thực hiện. Gửi thông báo cho các bộ phận liên quan.                                                                         | Trạng thái khu vực được cập nhật thành công. Các bộ phận liên quan được thông báo.                               | Không thể cập nhật trạng thái khu vực do lỗi hệ thống. Lỗi khi gửi thông báo.                               |

### 1.2 QUẢN LÝ VỊ TRÍ SÁCH

#### 1.2.1 Thông tin màn hình:

| Screen        | Quản lý vị trí sách                                       |
| ------------- | --------------------------------------------------------- |
| Description   | Quản lý vị trí lưu trữ và sắp xếp sách trong kho          |
| Screen Access | Nhân viên kho chọn **Quản lý vị trí** từ menu quản lý kho |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                        | Type         | Data                                                                                | Description                                    |
| --------------------------- | ------------ | ----------------------------------------------------------------------------------- | ---------------------------------------------- |
| **Tiêu đề trang**           | Text         | Quản lý vị trí sách                                                                 | Tiêu đề chính của trang quản lý vị trí sách    |
| **Bộ lọc vị trí**           | Form         | Khu vực<br>Kệ sách<br>Trạng thái<br>Tìm kiếm sách                                   | Form lọc vị trí sách theo tiêu chí             |
| **Khu vực**                 | Dropdown     | Tất cả<br>Khu A (Văn học)<br>Khu B (Khoa học)<br>Khu C (Lịch sử)<br>Khu D (Kinh tế) | Lọc vị trí theo khu vực                        |
| **Kệ sách**                 | Dropdown     | Tất cả<br>Kệ 1<br>Kệ 2<br>Kệ 3<br>Kệ 4<br>Kệ 5                                      | Lọc vị trí theo kệ sách                        |
| **Trạng thái**              | Dropdown     | Tất cả<br>Có sách<br>Trống<br>Bảo trì<br>Không sử dụng                              | Lọc vị trí theo trạng thái                     |
| **Tìm kiếm sách**           | Input (Text) |                                                                                     | Ô nhập tên sách hoặc mã sách để tìm vị trí     |
| **Sơ đồ khu vực**           | Chart        | Sơ đồ trực quan hiển thị bố trí kệ sách và vị trí sách                              | Sơ đồ trực quan hóa vị trí sách trong kho      |
| **Danh sách vị trí**        | Table        | Vị trí<br>Kệ sách<br>Sách<br>Số lượng<br>Trạng thái<br>Ghi chú<br>Thao tác          | Hiển thị danh sách vị trí sách dưới dạng bảng  |
| **Vị trí**                  | Text + Badge | A1-01                                                                               | Mã vị trí sách, kèm theo badge trạng thái      |
| **Kệ sách**                 | Text         | Kệ 1 - Tầng A                                                                       | Thông tin kệ sách                              |
| **Sách**                    | Text         | Đắc Nhân Tâm                                                                        | Tên sách được lưu trữ tại vị trí               |
| **Số lượng**                | Text         | 15 cuốn                                                                             | Số lượng sách tại vị trí                       |
| **Trạng thái**              | Badge        | Có sách<br>Trống<br>Bảo trì<br>Không sử dụng                                        | Trạng thái hiện tại của vị trí                 |
| **Ghi chú**                 | Text         | Sách mới nhập                                                                       | Ghi chú về vị trí sách                         |
| **Thao tác**                | Button Group | Xem chi tiết<br>Chỉnh sửa<br>Di chuyển sách<br>Cập nhật trạng thái                  | Các nút chức năng để thao tác trên vị trí sách |
| **Nút thêm vị trí**         | Button       |                                                                                     | Nút thêm vị trí sách mới                       |
| **Nút di chuyển hàng loạt** | Button       |                                                                                     | Nút di chuyển nhiều sách cùng lúc              |
| **Nút xuất báo cáo**        | Button       |                                                                                     | Nút xuất báo cáo vị trí sách                   |
| **Phân trang**              | Pagination   | Trang 1/50                                                                          | Điều hướng giữa các trang                      |

#### 1.2.3 Hành động và xử lý:

| Action Name                   | Description                                                                                                                                                                                                                                            | Success                                                                                                                | Failure                                                                                            |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **Xem danh sách vị trí sách** | Hiển thị danh sách các vị trí sách trong kho. Bao gồm thông tin về vị trí, kệ sách, sách, số lượng, trạng thái và ghi chú. Cung cấp bộ lọc theo khu vực, kệ sách, trạng thái và tìm kiếm sách. Hiển thị sơ đồ trực quan bố trí kệ sách và vị trí sách. | Danh sách vị trí sách được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. Sơ đồ hiển thị chính xác. | Không thể tải danh sách vị trí sách do lỗi hệ thống. Bộ lọc không hoạt động. Sơ đồ không hiển thị. |
| **Xem chi tiết vị trí**       | Hiển thị chi tiết vị trí sách được chọn. Bao gồm thông tin đầy đủ về vị trí, lịch sử sử dụng, sách hiện tại và lịch sử di chuyển. Cho phép xem sơ đồ vị trí trong khu vực.                                                                             | Chi tiết vị trí được hiển thị đầy đủ và chính xác.                                                                     | Không thể tải chi tiết vị trí. Thông tin hiển thị không đầy đủ.                                    |
| **Thêm vị trí mới**           | Cho phép nhân viên kho thêm vị trí sách mới. Nhập thông tin vị trí (mã vị trí, kệ sách, tầng). Thiết lập trạng thái ban đầu của vị trí. Thêm ghi chú về vị trí. Lưu thông tin vị trí vào hệ thống.                                                     | Vị trí mới được tạo thành công. Thông tin được lưu vào hệ thống.                                                       | Không thể tạo vị trí mới do lỗi hệ thống. Thông tin không được lưu.                                |
| **Chỉnh sửa vị trí**          | Cho phép nhân viên kho chỉnh sửa thông tin vị trí sách. Cập nhật thông tin vị trí (mã vị trí, kệ sách, tầng). Thay đổi trạng thái vị trí. Cập nhật ghi chú về vị trí. Lưu thay đổi vào hệ thống.                                                       | Thông tin vị trí được cập nhật thành công. Thay đổi được lưu vào hệ thống.                                             | Không thể cập nhật thông tin vị trí do lỗi hệ thống. Thay đổi không được lưu.                      |
| **Di chuyển sách**            | Cho phép nhân viên kho di chuyển sách giữa các vị trí. Chọn sách cần di chuyển. Chọn vị trí đích. Xác nhận việc di chuyển sách. Cập nhật thông tin vị trí sách. Ghi nhận lịch sử di chuyển.                                                            | Sách được di chuyển thành công. Lịch sử di chuyển được ghi nhận.                                                       | Không thể di chuyển sách do lỗi hệ thống. Lịch sử di chuyển không được ghi nhận.                   |
| **Di chuyển hàng loạt**       | Cho phép nhân viên kho di chuyển nhiều sách cùng lúc. Chọn các sách cần di chuyển. Chọn vị trí đích cho từng sách. Xác nhận việc di chuyển hàng loạt. Cập nhật thông tin vị trí cho tất cả sách. Ghi nhận lịch sử di chuyển hàng loạt.                 | Tất cả sách được di chuyển thành công. Lịch sử di chuyển hàng loạt được ghi nhận.                                      | Một số sách không được di chuyển do lỗi. Lịch sử di chuyển hàng loạt không được ghi nhận đầy đủ.   |

### 1.3 THEO DÕI TÌNH TRẠNG KHO

#### 1.3.1 Thông tin màn hình:

| Screen        | Theo dõi tình trạng kho                                        |
| ------------- | -------------------------------------------------------------- |
| Description   | Theo dõi tình trạng hoạt động và hiệu suất của kho hàng        |
| Screen Access | Nhân viên kho chọn **Theo dõi tình trạng** từ menu quản lý kho |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                    | Type         | Data                                                                                       | Description                                     |
| ----------------------- | ------------ | ------------------------------------------------------------------------------------------ | ----------------------------------------------- |
| **Tiêu đề trang**       | Text         | Theo dõi tình trạng kho                                                                    | Tiêu đề chính của trang theo dõi tình trạng kho |
| **Thống kê tổng quan**  | Card Group   | Tổng sức chứa: 10,000<br>Đã sử dụng: 8,500<br>Tỷ lệ sử dụng: 85%<br>Khu vực hoạt động: 7/8 | Hiển thị thống kê tổng quan về tình trạng kho   |
| **Bộ lọc thời gian**    | Form         | Từ ngày<br>Đến ngày<br>Khoảng thời gian<br>Loại báo cáo                                    | Form lọc báo cáo tình trạng kho theo thời gian  |
| **Từ ngày**             | Input (Date) | 2023-11-01                                                                                 | Ngày bắt đầu theo dõi                           |
| **Đến ngày**            | Input (Date) | 2023-11-30                                                                                 | Ngày kết thúc theo dõi                          |
| **Khoảng thời gian**    | Select       | Hôm nay<br>Tuần này<br>Tháng này<br>Quý này<br>Tùy chọn                                    | Lựa chọn khoảng thời gian có sẵn                |
| **Loại báo cáo**        | Dropdown     | Tất cả<br>Sử dụng kho<br>Hiệu suất<br>Bảo trì<br>Sự cố                                     | Lọc báo cáo theo loại                           |
| **Biểu đồ sử dụng kho** | Chart        | Biểu đồ cột thể hiện tỷ lệ sử dụng kho theo thời gian                                      | Biểu đồ trực quan hóa tình trạng sử dụng kho    |
| **Biểu đồ hiệu suất**   | Chart        | Biểu đồ đường thể hiện hiệu suất hoạt động kho theo thời gian                              | Biểu đồ trực quan hóa hiệu suất kho             |
| **Danh sách sự kiện**   | Table        | Thời gian<br>Loại<br>Mô tả<br>Khu vực<br>Mức độ<br>Trạng thái<br>Thao tác                  | Hiển thị danh sách sự kiện kho dưới dạng bảng   |
| **Thời gian**           | Text         | 2023-11-20 14:30                                                                           | Thời gian xảy ra sự kiện                        |
| **Loại**                | Badge        | Sử dụng kho<br>Hiệu suất<br>Bảo trì<br>Sự cố                                               | Loại sự kiện kho                                |
| **Mô tả**               | Text         | Khu A đạt 90% sức chứa                                                                     | Mô tả chi tiết về sự kiện                       |
| **Khu vực**             | Text         | Khu A - Văn học                                                                            | Khu vực liên quan đến sự kiện                   |
| **Mức độ**              | Badge        | Thông tin<br>Cảnh báo<br>Quan trọng<br>Nghiêm trọng                                        | Mức độ quan trọng của sự kiện                   |
| **Trạng thái**          | Badge        | Đã xử lý<br>Đang xử lý<br>Chờ xử lý<br>Bỏ qua                                              | Trạng thái xử lý sự kiện                        |
| **Thao tác**            | Button Group | Xem chi tiết<br>Xử lý<br>Báo cáo<br>Xuất log                                               | Các nút chức năng để thao tác trên sự kiện kho  |
| **Nút tạo báo cáo**     | Button       |                                                                                            | Nút tạo báo cáo tình trạng kho                  |
| **Nút xuất báo cáo**    | Button       |                                                                                            | Nút xuất báo cáo tình trạng kho                 |
| **Phân trang**          | Pagination   | Trang 1/25                                                                                 | Điều hướng giữa các trang                       |

#### 1.3.3 Hành động và xử lý:

| Action Name                 | Description                                                                                                                                                                                                                                                        | Success                                                                                                           | Failure                                                                                       |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **Xem tình trạng kho**      | Hiển thị tình trạng hoạt động và hiệu suất của kho hàng. Bao gồm thống kê tổng quan về sức chứa, tỷ lệ sử dụng và khu vực hoạt động. Hiển thị biểu đồ trực quan hóa tình trạng sử dụng kho và hiệu suất hoạt động. Cung cấp bộ lọc theo thời gian và loại báo cáo. | Tình trạng kho được hiển thị đầy đủ với đầy đủ thông tin. Biểu đồ hiển thị chính xác. Bộ lọc hoạt động chính xác. | Không thể tải tình trạng kho do lỗi hệ thống. Biểu đồ không hiển thị. Bộ lọc không hoạt động. |
| **Xem danh sách sự kiện**   | Hiển thị danh sách các sự kiện liên quan đến kho hàng. Bao gồm thông tin về thời gian, loại, mô tả, khu vực, mức độ và trạng thái. Cho phép xem chi tiết từng sự kiện.                                                                                             | Danh sách sự kiện được hiển thị đầy đủ với đầy đủ thông tin.                                                      | Không thể tải danh sách sự kiện do lỗi hệ thống.                                              |
| **Xử lý sự kiện kho**       | Cho phép nhân viên kho xử lý các sự kiện liên quan đến kho hàng. Chọn sự kiện cần xử lý. Cập nhật trạng thái sự kiện (đã xử lý, đang xử lý, chờ xử lý, bỏ qua). Thêm ghi chú về việc xử lý sự kiện. Gửi thông báo cho các bộ phận liên quan nếu cần.               | Sự kiện kho được xử lý thành công. Các bộ phận liên quan được thông báo nếu cần.                                  | Không thể xử lý sự kiện kho do lỗi hệ thống. Lỗi khi gửi thông báo.                           |
| **Tạo báo cáo tình trạng**  | Cho phép nhân viên kho tạo báo cáo về tình trạng kho hàng. Chọn khoảng thời gian và loại báo cáo cần tạo. Hiển thị thống kê tổng quan và biểu đồ trực quan. Bao gồm danh sách chi tiết các sự kiện kho.                                                            | Báo cáo tình trạng kho được tạo thành công với đầy đủ thông tin.                                                  | Không thể tạo báo cáo tình trạng kho do lỗi hệ thống.                                         |
| **Xuất báo cáo tình trạng** | Cho phép nhân viên kho xuất báo cáo tình trạng kho dưới dạng PDF hoặc Excel. Bao gồm thống kê tổng quan, biểu đồ và danh sách chi tiết sự kiện. Định dạng báo cáo theo chuẩn của công ty.                                                                          | Báo cáo tình trạng kho được xuất thành công dưới định dạng đã chọn.                                               | Không thể xuất báo cáo tình trạng kho. Lỗi khi tạo file báo cáo.                              |

### 1.4 QUẢN LÝ THIẾT BỊ KHO

#### 1.4.1 Thông tin màn hình:

| Screen        | Quản lý thiết bị kho                                        |
| ------------- | ----------------------------------------------------------- |
| Description   | Quản lý các thiết bị và công cụ trong kho hàng              |
| Screen Access | Nhân viên kho chọn **Quản lý thiết bị** từ menu quản lý kho |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                     | Type         | Data                                                                                     | Description                                          |
| ------------------------ | ------------ | ---------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **Tiêu đề trang**        | Text         | Quản lý thiết bị kho                                                                     | Tiêu đề chính của trang quản lý thiết bị kho         |
| **Thống kê thiết bị**    | Card Group   | Tổng thiết bị: 25<br>Hoạt động: 22<br>Bảo trì: 2<br>Hỏng: 1                              | Hiển thị thống kê tổng quan về thiết bị kho          |
| **Bộ lọc thiết bị**      | Form         | Loại thiết bị<br>Trạng thái<br>Khu vực<br>Tìm kiếm                                       | Form lọc thiết bị kho theo tiêu chí                  |
| **Loại thiết bị**        | Dropdown     | Tất cả<br>Xe nâng<br>Băng tải<br>Máy quét<br>Máy in<br>Thiết bị khác                     | Lọc thiết bị theo loại                               |
| **Trạng thái**           | Dropdown     | Tất cả<br>Hoạt động<br>Bảo trì<br>Hỏng<br>Ngừng sử dụng                                  | Lọc thiết bị theo trạng thái                         |
| **Khu vực**              | Dropdown     | Tất cả<br>Khu A<br>Khu B<br>Khu C<br>Khu D<br>Khu chung                                  | Lọc thiết bị theo khu vực                            |
| **Tìm kiếm**             | Input (Text) |                                                                                          | Ô nhập tên thiết bị hoặc mã thiết bị để tìm kiếm     |
| **Danh sách thiết bị**   | Table        | Mã thiết bị<br>Tên thiết bị<br>Loại<br>Khu vực<br>Trạng thái<br>Ngày bảo trì<br>Thao tác | Hiển thị danh sách thiết bị kho dưới dạng bảng       |
| **Mã thiết bị**          | Text + Badge | TB001                                                                                    | Mã định danh của thiết bị, kèm theo badge trạng thái |
| **Tên thiết bị**         | Text         | Xe nâng điện Toyota                                                                      | Tên thiết bị kho                                     |
| **Loại**                 | Badge        | Xe nâng<br>Băng tải<br>Máy quét<br>Máy in<br>Thiết bị khác                               | Loại thiết bị                                        |
| **Khu vực**              | Text         | Khu A - Văn học                                                                          | Khu vực sử dụng thiết bị                             |
| **Trạng thái**           | Badge        | Hoạt động<br>Bảo trì<br>Hỏng<br>Ngừng sử dụng                                            | Trạng thái hiện tại của thiết bị                     |
| **Ngày bảo trì**         | Text         | 2023-11-25                                                                               | Ngày bảo trì gần nhất                                |
| **Thao tác**             | Button Group | Xem chi tiết<br>Chỉnh sửa<br>Cập nhật trạng thái<br>Lịch sử bảo trì                      | Các nút chức năng để thao tác trên thiết bị kho      |
| **Nút thêm thiết bị**    | Button       |                                                                                          | Nút thêm thiết bị kho mới                            |
| **Nút lập lịch bảo trì** | Button       |                                                                                          | Nút lập lịch bảo trì thiết bị                        |
| **Nút xuất báo cáo**     | Button       |                                                                                          | Nút xuất báo cáo thiết bị kho                        |
| **Phân trang**           | Pagination   | Trang 1/10                                                                               | Điều hướng giữa các trang                            |

#### 1.4.3 Hành động và xử lý:

| Action Name                      | Description                                                                                                                                                                                                                                                                                                          | Success                                                                                                           | Failure                                                                                                      |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Xem danh sách thiết bị**       | Hiển thị danh sách các thiết bị trong kho hàng. Bao gồm thông tin về mã thiết bị, tên thiết bị, loại, khu vực, trạng thái và ngày bảo trì. Cung cấp bộ lọc theo loại thiết bị, trạng thái, khu vực và tìm kiếm. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. Hiển thị thống kê tổng quan về thiết bị kho. | Danh sách thiết bị được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách thiết bị do lỗi hệ thống. Bộ lọc không hoạt động. Thống kê hiển thị không chính xác. |
| **Xem chi tiết thiết bị**        | Hiển thị chi tiết thiết bị kho được chọn. Bao gồm thông tin đầy đủ về thiết bị, lịch sử sử dụng, lịch sử bảo trì và tài liệu hướng dẫn. Cho phép xem lịch sử hoạt động của thiết bị.                                                                                                                                 | Chi tiết thiết bị được hiển thị đầy đủ và chính xác.                                                              | Không thể tải chi tiết thiết bị. Thông tin hiển thị không đầy đủ.                                            |
| **Thêm thiết bị mới**            | Cho phép nhân viên kho thêm thiết bị kho mới. Nhập thông tin cơ bản về thiết bị (tên, loại, khu vực). Thiết lập trạng thái ban đầu của thiết bị. Thêm thông tin bảo trì và hướng dẫn sử dụng. Lưu thông tin thiết bị vào hệ thống.                                                                                   | Thiết bị mới được tạo thành công. Thông tin được lưu vào hệ thống.                                                | Không thể tạo thiết bị mới do lỗi hệ thống. Thông tin không được lưu.                                        |
| **Chỉnh sửa thiết bị**           | Cho phép nhân viên kho chỉnh sửa thông tin thiết bị kho. Cập nhật tên, loại và khu vực thiết bị. Thay đổi trạng thái thiết bị. Cập nhật thông tin bảo trì và hướng dẫn sử dụng. Lưu thay đổi vào hệ thống.                                                                                                           | Thông tin thiết bị được cập nhật thành công. Thay đổi được lưu vào hệ thống.                                      | Không thể cập nhật thông tin thiết bị do lỗi hệ thống. Thay đổi không được lưu.                              |
| **Cập nhật trạng thái thiết bị** | Cho phép nhân viên kho cập nhật trạng thái thiết bị kho. Thay đổi trạng thái (hoạt động, bảo trì, hỏng, ngừng sử dụng). Thêm ghi chú về việc thay đổi trạng thái. Ghi nhận thời gian và người thực hiện. Gửi thông báo cho các bộ phận liên quan.                                                                    | Trạng thái thiết bị được cập nhật thành công. Các bộ phận liên quan được thông báo.                               | Không thể cập nhật trạng thái thiết bị do lỗi hệ thống. Lỗi khi gửi thông báo.                               |
| **Lập lịch bảo trì thiết bị**    | Cho phép nhân viên kho lập lịch bảo trì cho thiết bị kho. Chọn thiết bị cần bảo trì. Thiết lập thời gian bảo trì. Thêm ghi chú về nội dung bảo trì. Gửi thông báo cho bộ phận bảo trì. Tạo lịch sử bảo trì thiết bị.                                                                                                 | Lịch bảo trì thiết bị được tạo thành công. Bộ phận bảo trì được thông báo.                                        | Không thể tạo lịch bảo trì thiết bị do lỗi hệ thống. Lỗi khi gửi thông báo.                                  |
| **Xem lịch sử bảo trì**          | Hiển thị lịch sử bảo trì của thiết bị kho. Bao gồm thông tin về các lần bảo trì, nội dung bảo trì, người thực hiện và kết quả bảo trì. Hiển thị theo dòng thời gian từ cũ đến mới nhất.                                                                                                                              | Lịch sử bảo trì được hiển thị đầy đủ và chính xác.                                                                | Không thể tải lịch sử bảo trì. Thông tin hiển thị không đầy đủ.                                              |
