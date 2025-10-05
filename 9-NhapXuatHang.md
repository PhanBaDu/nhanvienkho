# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng nhập xuất hàng của Nhân viên kho_

## MỤC LỤC

1. [Chức năng nhập xuất hàng](#1-chức-năng-nhập-xuất-hàng)
   - 1.1 [Quản lý nhập hàng](#11-quản-lý-nhập-hàng)
   - 1.2 [Quản lý xuất hàng](#12-quản-lý-xuất-hàng)
   - 1.3 [Theo dõi vận chuyển](#13-theo-dõi-vận-chuyển)
   - 1.4 [Quản lý nhà cung cấp](#14-quản-lý-nhà-cung-cấp)

---

## 1. CHỨC NĂNG NHẬP XUẤT HÀNG

### 1.1 QUẢN LÝ NHẬP HÀNG

#### 1.1.1 Thông tin màn hình:

| Screen        | Quản lý nhập hàng                                   |
| ------------- | --------------------------------------------------- |
| Description   | Quản lý việc nhập hàng mới vào kho từ nhà cung cấp  |
| Screen Access | Nhân viên kho chọn **Nhập xuất hàng** từ menu chính |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                   | Type         | Data                                                                                      | Description                                          |
| ---------------------- | ------------ | ----------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **Tiêu đề trang**      | Text         | Quản lý nhập hàng                                                                         | Tiêu đề chính của trang quản lý nhập hàng            |
| **Thống kê nhập hàng** | Card Group   | Tổng đơn nhập: 15<br>Đang xử lý: 3<br>Hoàn thành: 12<br>Giá trị: 2.5M VNĐ                 | Hiển thị thống kê tổng quan về nhập hàng             |
| **Bộ lọc đơn nhập**    | Form         | Trạng thái<br>Nhà cung cấp<br>Khoảng thời gian<br>Tìm kiếm                                | Form lọc đơn nhập hàng theo tiêu chí                 |
| **Trạng thái**         | Dropdown     | Tất cả<br>Chờ xử lý<br>Đang xử lý<br>Hoàn thành<br>Hủy bỏ                                 | Lọc đơn nhập theo trạng thái                         |
| **Nhà cung cấp**       | Dropdown     | Tất cả<br>NXB Kim Đồng<br>NXB Trẻ<br>NXB Giáo dục<br>NXB Văn học                          | Lọc đơn nhập theo nhà cung cấp                       |
| **Khoảng thời gian**   | Select       | Hôm nay<br>Tuần này<br>Tháng này<br>Quý này<br>Tùy chọn                                   | Lựa chọn khoảng thời gian có sẵn                     |
| **Tìm kiếm**           | Input (Text) |                                                                                           | Ô nhập mã đơn nhập hoặc tên sách để tìm kiếm         |
| **Danh sách đơn nhập** | Table        | Mã đơn nhập<br>Nhà cung cấp<br>Ngày nhập<br>Số lượng<br>Giá trị<br>Trạng thái<br>Thao tác | Hiển thị danh sách đơn nhập hàng dưới dạng bảng      |
| **Mã đơn nhập**        | Text + Badge | NH001                                                                                     | Mã định danh của đơn nhập, kèm theo badge trạng thái |
| **Nhà cung cấp**       | Text         | NXB Kim Đồng                                                                              | Tên nhà cung cấp                                     |
| **Ngày nhập**          | Text         | 2023-11-20                                                                                | Ngày nhập hàng                                       |
| **Số lượng**           | Text         | 500 cuốn                                                                                  | Tổng số lượng sách nhập                              |
| **Giá trị**            | Text         | 150,000,000 VNĐ                                                                           | Tổng giá trị đơn nhập                                |
| **Trạng thái**         | Badge        | Chờ xử lý<br>Đang xử lý<br>Hoàn thành<br>Hủy bỏ                                           | Trạng thái hiện tại của đơn nhập                     |
| **Thao tác**           | Button Group | Xem chi tiết<br>Xử lý<br>Chỉnh sửa<br>Hủy bỏ                                              | Các nút chức năng để thao tác trên đơn nhập          |
| **Nút tạo đơn nhập**   | Button       |                                                                                           | Nút tạo đơn nhập hàng mới                            |
| **Nút xuất báo cáo**   | Button       |                                                                                           | Nút xuất báo cáo nhập hàng                           |
| **Phân trang**         | Pagination   | Trang 1/8                                                                                 | Điều hướng giữa các trang                            |

#### 1.1.3 Hành động và xử lý:

| Action Name                | Description                                                                                                                                                                                                                                                                                                      | Success                                                                                                           | Failure                                                                                                      |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Xem danh sách đơn nhập** | Hiển thị danh sách các đơn nhập hàng. Bao gồm thông tin về mã đơn nhập, nhà cung cấp, ngày nhập, số lượng, giá trị và trạng thái. Cung cấp bộ lọc theo trạng thái, nhà cung cấp, khoảng thời gian và tìm kiếm. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. Hiển thị thống kê tổng quan về nhập hàng. | Danh sách đơn nhập được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách đơn nhập do lỗi hệ thống. Bộ lọc không hoạt động. Thống kê hiển thị không chính xác. |
| **Xem chi tiết đơn nhập**  | Hiển thị chi tiết đơn nhập hàng được chọn. Bao gồm thông tin đầy đủ về đơn nhập, danh sách sách nhập, thông tin nhà cung cấp và lịch sử xử lý. Cho phép xem hóa đơn và chứng từ liên quan.                                                                                                                       | Chi tiết đơn nhập được hiển thị đầy đủ và chính xác.                                                              | Không thể tải chi tiết đơn nhập. Thông tin hiển thị không đầy đủ.                                            |
| **Tạo đơn nhập mới**       | Cho phép nhân viên kho tạo đơn nhập hàng mới. Chọn nhà cung cấp. Thêm danh sách sách cần nhập với số lượng và giá. Thiết lập thông tin vận chuyển và thanh toán. Lưu đơn nhập vào hệ thống.                                                                                                                      | Đơn nhập mới được tạo thành công. Thông tin được lưu vào hệ thống.                                                | Không thể tạo đơn nhập mới do lỗi hệ thống. Thông tin không được lưu.                                        |
| **Xử lý đơn nhập**         | Cho phép nhân viên kho xử lý đơn nhập hàng. Cập nhật trạng thái đơn nhập (đang xử lý, hoàn thành, hủy bỏ). Thêm ghi chú về việc xử lý. Ghi nhận thời gian và người thực hiện. Gửi thông báo cho các bộ phận liên quan.                                                                                           | Đơn nhập được xử lý thành công. Các bộ phận liên quan được thông báo.                                             | Không thể xử lý đơn nhập do lỗi hệ thống. Lỗi khi gửi thông báo.                                             |
| **Chỉnh sửa đơn nhập**     | Cho phép nhân viên kho chỉnh sửa thông tin đơn nhập hàng. Cập nhật danh sách sách nhập, số lượng và giá. Thay đổi thông tin vận chuyển và thanh toán. Cập nhật ghi chú về đơn nhập. Lưu thay đổi vào hệ thống.                                                                                                   | Thông tin đơn nhập được cập nhật thành công. Thay đổi được lưu vào hệ thống.                                      | Không thể cập nhật thông tin đơn nhập do lỗi hệ thống. Thay đổi không được lưu.                              |
| **Hủy bỏ đơn nhập**        | Cho phép nhân viên kho hủy bỏ đơn nhập hàng. Chọn đơn nhập cần hủy. Nhập lý do hủy bỏ. Cập nhật trạng thái đơn nhập thành hủy bỏ. Gửi thông báo cho nhà cung cấp và các bộ phận liên quan.                                                                                                                       | Đơn nhập được hủy bỏ thành công. Các bộ phận liên quan được thông báo.                                            | Không thể hủy bỏ đơn nhập do lỗi hệ thống. Lỗi khi gửi thông báo.                                            |

### 1.2 QUẢN LÝ XUẤT HÀNG

#### 1.2.1 Thông tin màn hình:

| Screen        | Quản lý xuất hàng                                    |
| ------------- | ---------------------------------------------------- |
| Description   | Quản lý việc xuất hàng từ kho để bán hoặc chuyển kho |
| Screen Access | Nhân viên kho chọn **Xuất hàng** từ menu nhập xuất   |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                   | Type         | Data                                                                                   | Description                                          |
| ---------------------- | ------------ | -------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **Tiêu đề trang**      | Text         | Quản lý xuất hàng                                                                      | Tiêu đề chính của trang quản lý xuất hàng            |
| **Thống kê xuất hàng** | Card Group   | Tổng đơn xuất: 25<br>Đang xử lý: 5<br>Hoàn thành: 20<br>Giá trị: 3.2M VNĐ              | Hiển thị thống kê tổng quan về xuất hàng             |
| **Bộ lọc đơn xuất**    | Form         | Trạng thái<br>Loại xuất<br>Khoảng thời gian<br>Tìm kiếm                                | Form lọc đơn xuất hàng theo tiêu chí                 |
| **Trạng thái**         | Dropdown     | Tất cả<br>Chờ xử lý<br>Đang xử lý<br>Hoàn thành<br>Hủy bỏ                              | Lọc đơn xuất theo trạng thái                         |
| **Loại xuất**          | Dropdown     | Tất cả<br>Bán hàng<br>Chuyển kho<br>Trả hàng<br>Hủy bỏ                                 | Lọc đơn xuất theo loại                               |
| **Khoảng thời gian**   | Select       | Hôm nay<br>Tuần này<br>Tháng này<br>Quý này<br>Tùy chọn                                | Lựa chọn khoảng thời gian có sẵn                     |
| **Tìm kiếm**           | Input (Text) |                                                                                        | Ô nhập mã đơn xuất hoặc tên sách để tìm kiếm         |
| **Danh sách đơn xuất** | Table        | Mã đơn xuất<br>Loại xuất<br>Ngày xuất<br>Số lượng<br>Giá trị<br>Trạng thái<br>Thao tác | Hiển thị danh sách đơn xuất hàng dưới dạng bảng      |
| **Mã đơn xuất**        | Text + Badge | XH001                                                                                  | Mã định danh của đơn xuất, kèm theo badge trạng thái |
| **Loại xuất**          | Badge        | Bán hàng<br>Chuyển kho<br>Trả hàng<br>Hủy bỏ                                           | Loại xuất hàng                                       |
| **Ngày xuất**          | Text         | 2023-11-20                                                                             | Ngày xuất hàng                                       |
| **Số lượng**           | Text         | 200 cuốn                                                                               | Tổng số lượng sách xuất                              |
| **Giá trị**            | Text         | 120,000,000 VNĐ                                                                        | Tổng giá trị đơn xuất                                |
| **Trạng thái**         | Badge        | Chờ xử lý<br>Đang xử lý<br>Hoàn thành<br>Hủy bỏ                                        | Trạng thái hiện tại của đơn xuất                     |
| **Thao tác**           | Button Group | Xem chi tiết<br>Xử lý<br>Chỉnh sửa<br>Hủy bỏ                                           | Các nút chức năng để thao tác trên đơn xuất          |
| **Nút tạo đơn xuất**   | Button       |                                                                                        | Nút tạo đơn xuất hàng mới                            |
| **Nút xuất báo cáo**   | Button       |                                                                                        | Nút xuất báo cáo xuất hàng                           |
| **Phân trang**         | Pagination   | Trang 1/10                                                                             | Điều hướng giữa các trang                            |

#### 1.2.3 Hành động và xử lý:

| Action Name                | Description                                                                                                                                                                                                                                                                                                | Success                                                                                                           | Failure                                                                                                      |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Xem danh sách đơn xuất** | Hiển thị danh sách các đơn xuất hàng. Bao gồm thông tin về mã đơn xuất, loại xuất, ngày xuất, số lượng, giá trị và trạng thái. Cung cấp bộ lọc theo trạng thái, loại xuất, khoảng thời gian và tìm kiếm. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. Hiển thị thống kê tổng quan về xuất hàng. | Danh sách đơn xuất được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách đơn xuất do lỗi hệ thống. Bộ lọc không hoạt động. Thống kê hiển thị không chính xác. |
| **Xem chi tiết đơn xuất**  | Hiển thị chi tiết đơn xuất hàng được chọn. Bao gồm thông tin đầy đủ về đơn xuất, danh sách sách xuất, thông tin khách hàng và lịch sử xử lý. Cho phép xem hóa đơn và chứng từ liên quan.                                                                                                                   | Chi tiết đơn xuất được hiển thị đầy đủ và chính xác.                                                              | Không thể tải chi tiết đơn xuất. Thông tin hiển thị không đầy đủ.                                            |
| **Tạo đơn xuất mới**       | Cho phép nhân viên kho tạo đơn xuất hàng mới. Chọn loại xuất (bán hàng, chuyển kho, trả hàng). Thêm danh sách sách cần xuất với số lượng. Thiết lập thông tin vận chuyển và thanh toán. Lưu đơn xuất vào hệ thống.                                                                                         | Đơn xuất mới được tạo thành công. Thông tin được lưu vào hệ thống.                                                | Không thể tạo đơn xuất mới do lỗi hệ thống. Thông tin không được lưu.                                        |
| **Xử lý đơn xuất**         | Cho phép nhân viên kho xử lý đơn xuất hàng. Cập nhật trạng thái đơn xuất (đang xử lý, hoàn thành, hủy bỏ). Thêm ghi chú về việc xử lý. Ghi nhận thời gian và người thực hiện. Gửi thông báo cho các bộ phận liên quan.                                                                                     | Đơn xuất được xử lý thành công. Các bộ phận liên quan được thông báo.                                             | Không thể xử lý đơn xuất do lỗi hệ thống. Lỗi khi gửi thông báo.                                             |
| **Chỉnh sửa đơn xuất**     | Cho phép nhân viên kho chỉnh sửa thông tin đơn xuất hàng. Cập nhật danh sách sách xuất, số lượng. Thay đổi thông tin vận chuyển và thanh toán. Cập nhật ghi chú về đơn xuất. Lưu thay đổi vào hệ thống.                                                                                                    | Thông tin đơn xuất được cập nhật thành công. Thay đổi được lưu vào hệ thống.                                      | Không thể cập nhật thông tin đơn xuất do lỗi hệ thống. Thay đổi không được lưu.                              |
| **Hủy bỏ đơn xuất**        | Cho phép nhân viên kho hủy bỏ đơn xuất hàng. Chọn đơn xuất cần hủy. Nhập lý do hủy bỏ. Cập nhật trạng thái đơn xuất thành hủy bỏ. Gửi thông báo cho khách hàng và các bộ phận liên quan.                                                                                                                   | Đơn xuất được hủy bỏ thành công. Các bộ phận liên quan được thông báo.                                            | Không thể hủy bỏ đơn xuất do lỗi hệ thống. Lỗi khi gửi thông báo.                                            |

### 1.3 THEO DÕI VẬN CHUYỂN

#### 1.3.1 Thông tin màn hình:

| Screen        | Theo dõi vận chuyển                                |
| ------------- | -------------------------------------------------- |
| Description   | Theo dõi tình trạng vận chuyển hàng hóa            |
| Screen Access | Nhân viên kho chọn **Theo dõi vận chuyển** từ menu |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                     | Type         | Data                                                                         | Description                                            |
| ------------------------ | ------------ | ---------------------------------------------------------------------------- | ------------------------------------------------------ |
| **Tiêu đề trang**        | Text         | Theo dõi vận chuyển                                                          | Tiêu đề chính của trang theo dõi vận chuyển            |
| **Thống kê vận chuyển**  | Card Group   | Tổng đơn vận chuyển: 30<br>Đang vận chuyển: 8<br>Đã giao: 22<br>Trễ hạn: 2   | Hiển thị thống kê tổng quan về vận chuyển              |
| **Bộ lọc vận chuyển**    | Form         | Trạng thái<br>Đơn vị vận chuyển<br>Khoảng thời gian<br>Tìm kiếm              | Form lọc vận chuyển theo tiêu chí                      |
| **Trạng thái**           | Dropdown     | Tất cả<br>Chờ lấy hàng<br>Đang vận chuyển<br>Đã giao<br>Trễ hạn<br>Hủy bỏ    | Lọc vận chuyển theo trạng thái                         |
| **Đơn vị vận chuyển**    | Dropdown     | Tất cả<br>Viettel Post<br>Giao Hàng Nhanh<br>J&T Express<br>Ninja Van        | Lọc vận chuyển theo đơn vị                             |
| **Khoảng thời gian**     | Select       | Hôm nay<br>Tuần này<br>Tháng này<br>Quý này<br>Tùy chọn                      | Lựa chọn khoảng thời gian có sẵn                       |
| **Tìm kiếm**             | Input (Text) |                                                                              | Ô nhập mã vận chuyển hoặc tên khách hàng để tìm kiếm   |
| **Danh sách vận chuyển** | Table        | Mã vận chuyển<br>Đơn vị<br>Khách hàng<br>Trạng thái<br>Ngày giao<br>Thao tác | Hiển thị danh sách vận chuyển dưới dạng bảng           |
| **Mã vận chuyển**        | Text + Badge | VC001                                                                        | Mã định danh của vận chuyển, kèm theo badge trạng thái |
| **Đơn vị**               | Text         | Viettel Post                                                                 | Tên đơn vị vận chuyển                                  |
| **Khách hàng**           | Text         | Nguyễn Văn A                                                                 | Tên khách hàng                                         |
| **Trạng thái**           | Badge        | Chờ lấy hàng<br>Đang vận chuyển<br>Đã giao<br>Trễ hạn<br>Hủy bỏ              | Trạng thái hiện tại của vận chuyển                     |
| **Ngày giao**            | Text         | 2023-11-25                                                                   | Ngày dự kiến giao hàng                                 |
| **Thao tác**             | Button Group | Xem chi tiết<br>Cập nhật trạng thái<br>Theo dõi<br>Liên hệ                   | Các nút chức năng để thao tác trên vận chuyển          |
| **Nút tạo vận chuyển**   | Button       |                                                                              | Nút tạo vận chuyển mới                                 |
| **Nút xuất báo cáo**     | Button       |                                                                              | Nút xuất báo cáo vận chuyển                            |
| **Phân trang**           | Pagination   | Trang 1/15                                                                   | Điều hướng giữa các trang                              |

#### 1.3.3 Hành động và xử lý:

| Action Name                        | Description                                                                                                                                                                                                                                                                                                                  | Success                                                                                                             | Failure                                                                                                        |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| **Xem danh sách vận chuyển**       | Hiển thị danh sách các vận chuyển hàng hóa. Bao gồm thông tin về mã vận chuyển, đơn vị vận chuyển, khách hàng, trạng thái và ngày giao. Cung cấp bộ lọc theo trạng thái, đơn vị vận chuyển, khoảng thời gian và tìm kiếm. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. Hiển thị thống kê tổng quan về vận chuyển. | Danh sách vận chuyển được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách vận chuyển do lỗi hệ thống. Bộ lọc không hoạt động. Thống kê hiển thị không chính xác. |
| **Xem chi tiết vận chuyển**        | Hiển thị chi tiết vận chuyển hàng hóa được chọn. Bao gồm thông tin đầy đủ về vận chuyển, lịch sử trạng thái, thông tin khách hàng và đơn vị vận chuyển. Cho phép xem lộ trình vận chuyển và thời gian dự kiến.                                                                                                               | Chi tiết vận chuyển được hiển thị đầy đủ và chính xác.                                                              | Không thể tải chi tiết vận chuyển. Thông tin hiển thị không đầy đủ.                                            |
| **Tạo vận chuyển mới**             | Cho phép nhân viên kho tạo vận chuyển hàng hóa mới. Chọn đơn vị vận chuyển. Nhập thông tin khách hàng và địa chỉ giao hàng. Thiết lập thông tin hàng hóa và thời gian giao hàng. Lưu thông tin vận chuyển vào hệ thống.                                                                                                      | Vận chuyển mới được tạo thành công. Thông tin được lưu vào hệ thống.                                                | Không thể tạo vận chuyển mới do lỗi hệ thống. Thông tin không được lưu.                                        |
| **Cập nhật trạng thái vận chuyển** | Cho phép nhân viên kho cập nhật trạng thái vận chuyển hàng hóa. Thay đổi trạng thái (chờ lấy hàng, đang vận chuyển, đã giao, trễ hạn, hủy bỏ). Thêm ghi chú về việc thay đổi trạng thái. Ghi nhận thời gian và người thực hiện. Gửi thông báo cho khách hàng và các bộ phận liên quan.                                       | Trạng thái vận chuyển được cập nhật thành công. Khách hàng và các bộ phận liên quan được thông báo.                 | Không thể cập nhật trạng thái vận chuyển do lỗi hệ thống. Lỗi khi gửi thông báo.                               |
| **Theo dõi vận chuyển**            | Cho phép nhân viên kho theo dõi tình trạng vận chuyển hàng hóa. Xem lộ trình vận chuyển và thời gian dự kiến. Cập nhật thông tin vận chuyển từ đơn vị vận chuyển. Gửi thông báo cho khách hàng về tình trạng vận chuyển.                                                                                                     | Tình trạng vận chuyển được cập nhật thành công. Khách hàng được thông báo.                                          | Không thể cập nhật tình trạng vận chuyển do lỗi hệ thống. Lỗi khi gửi thông báo.                               |
| **Liên hệ vận chuyển**             | Cho phép nhân viên kho liên hệ với đơn vị vận chuyển. Gửi yêu cầu hỗ trợ hoặc thông tin bổ sung. Theo dõi phản hồi từ đơn vị vận chuyển. Cập nhật thông tin vận chuyển dựa trên phản hồi.                                                                                                                                    | Liên hệ vận chuyển được thực hiện thành công. Thông tin được cập nhật.                                              | Không thể liên hệ vận chuyển do lỗi hệ thống. Thông tin không được cập nhật.                                   |

### 1.4 QUẢN LÝ NHÀ CUNG CẤP

#### 1.4.1 Thông tin màn hình:

| Screen        | Quản lý nhà cung cấp                                |
| ------------- | --------------------------------------------------- |
| Description   | Quản lý thông tin và quan hệ với nhà cung cấp       |
| Screen Access | Nhân viên kho chọn **Quản lý nhà cung cấp** từ menu |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                       | Type         | Data                                                                                   | Description                                              |
| -------------------------- | ------------ | -------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| **Tiêu đề trang**          | Text         | Quản lý nhà cung cấp                                                                   | Tiêu đề chính của trang quản lý nhà cung cấp             |
| **Thống kê nhà cung cấp**  | Card Group   | Tổng nhà cung cấp: 12<br>Hoạt động: 10<br>Tạm dừng: 2<br>Hợp đồng: 8                   | Hiển thị thống kê tổng quan về nhà cung cấp              |
| **Bộ lọc nhà cung cấp**    | Form         | Trạng thái<br>Loại sách<br>Khu vực<br>Tìm kiếm                                         | Form lọc nhà cung cấp theo tiêu chí                      |
| **Trạng thái**             | Dropdown     | Tất cả<br>Hoạt động<br>Tạm dừng<br>Ngừng hợp tác<br>Chờ duyệt                          | Lọc nhà cung cấp theo trạng thái                         |
| **Loại sách**              | Dropdown     | Tất cả<br>Văn học<br>Khoa học<br>Lịch sử<br>Kinh tế<br>Giáo dục                        | Lọc nhà cung cấp theo loại sách                          |
| **Khu vực**                | Dropdown     | Tất cả<br>Hà Nội<br>TP.HCM<br>Đà Nẵng<br>Khác                                          | Lọc nhà cung cấp theo khu vực                            |
| **Tìm kiếm**               | Input (Text) |                                                                                        | Ô nhập tên nhà cung cấp hoặc mã nhà cung cấp để tìm kiếm |
| **Danh sách nhà cung cấp** | Table        | Mã nhà cung cấp<br>Tên nhà cung cấp<br>Loại sách<br>Trạng thái<br>Hợp đồng<br>Thao tác | Hiển thị danh sách nhà cung cấp dưới dạng bảng           |
| **Mã nhà cung cấp**        | Text + Badge | NCC001                                                                                 | Mã định danh của nhà cung cấp, kèm theo badge trạng thái |
| **Tên nhà cung cấp**       | Text         | NXB Kim Đồng                                                                           | Tên nhà cung cấp                                         |
| **Loại sách**              | Badge        | Văn học<br>Khoa học<br>Lịch sử<br>Kinh tế<br>Giáo dục                                  | Loại sách cung cấp                                       |
| **Trạng thái**             | Badge        | Hoạt động<br>Tạm dừng<br>Ngừng hợp tác<br>Chờ duyệt                                    | Trạng thái hiện tại của nhà cung cấp                     |
| **Hợp đồng**               | Text         | HĐ001 - 2023/2024                                                                      | Mã hợp đồng và thời hạn                                  |
| **Thao tác**               | Button Group | Xem chi tiết<br>Chỉnh sửa<br>Cập nhật trạng thái<br>Xem hợp đồng                       | Các nút chức năng để thao tác trên nhà cung cấp          |
| **Nút thêm nhà cung cấp**  | Button       |                                                                                        | Nút thêm nhà cung cấp mới                                |
| **Nút xuất báo cáo**       | Button       |                                                                                        | Nút xuất báo cáo nhà cung cấp                            |
| **Phân trang**             | Pagination   | Trang 1/6                                                                              | Điều hướng giữa các trang                                |

#### 1.4.3 Hành động và xử lý:

| Action Name                          | Description                                                                                                                                                                                                                                                                                           | Success                                                                                                               | Failure                                                                                                          |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Xem danh sách nhà cung cấp**       | Hiển thị danh sách các nhà cung cấp. Bao gồm thông tin về mã nhà cung cấp, tên nhà cung cấp, loại sách, trạng thái và hợp đồng. Cung cấp bộ lọc theo trạng thái, loại sách, khu vực và tìm kiếm. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. Hiển thị thống kê tổng quan về nhà cung cấp. | Danh sách nhà cung cấp được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách nhà cung cấp do lỗi hệ thống. Bộ lọc không hoạt động. Thống kê hiển thị không chính xác. |
| **Xem chi tiết nhà cung cấp**        | Hiển thị chi tiết nhà cung cấp được chọn. Bao gồm thông tin đầy đủ về nhà cung cấp, lịch sử hợp tác, danh sách sách cung cấp và thông tin liên hệ. Cho phép xem hợp đồng và tài liệu liên quan.                                                                                                       | Chi tiết nhà cung cấp được hiển thị đầy đủ và chính xác.                                                              | Không thể tải chi tiết nhà cung cấp. Thông tin hiển thị không đầy đủ.                                            |
| **Thêm nhà cung cấp mới**            | Cho phép nhân viên kho thêm nhà cung cấp mới. Nhập thông tin cơ bản về nhà cung cấp (tên, địa chỉ, liên hệ). Thiết lập loại sách cung cấp và điều kiện hợp tác. Tạo hợp đồng mới với nhà cung cấp. Lưu thông tin nhà cung cấp vào hệ thống.                                                           | Nhà cung cấp mới được tạo thành công. Thông tin được lưu vào hệ thống.                                                | Không thể tạo nhà cung cấp mới do lỗi hệ thống. Thông tin không được lưu.                                        |
| **Chỉnh sửa nhà cung cấp**           | Cho phép nhân viên kho chỉnh sửa thông tin nhà cung cấp. Cập nhật thông tin liên hệ và địa chỉ. Thay đổi loại sách cung cấp và điều kiện hợp tác. Cập nhật thông tin hợp đồng. Lưu thay đổi vào hệ thống.                                                                                             | Thông tin nhà cung cấp được cập nhật thành công. Thay đổi được lưu vào hệ thống.                                      | Không thể cập nhật thông tin nhà cung cấp do lỗi hệ thống. Thay đổi không được lưu.                              |
| **Cập nhật trạng thái nhà cung cấp** | Cho phép nhân viên kho cập nhật trạng thái nhà cung cấp. Thay đổi trạng thái (hoạt động, tạm dừng, ngừng hợp tác, chờ duyệt). Thêm ghi chú về việc thay đổi trạng thái. Ghi nhận thời gian và người thực hiện. Gửi thông báo cho các bộ phận liên quan.                                               | Trạng thái nhà cung cấp được cập nhật thành công. Các bộ phận liên quan được thông báo.                               | Không thể cập nhật trạng thái nhà cung cấp do lỗi hệ thống. Lỗi khi gửi thông báo.                               |
| **Xem hợp đồng nhà cung cấp**        | Hiển thị hợp đồng của nhà cung cấp. Bao gồm thông tin về hợp đồng, điều khoản, thời hạn và giá trị. Cho phép xem lịch sử hợp đồng và tài liệu liên quan. Hiển thị thông báo về thời hạn hợp đồng sắp hết hạn.                                                                                         | Hợp đồng nhà cung cấp được hiển thị đầy đủ và chính xác.                                                              | Không thể tải hợp đồng nhà cung cấp. Thông tin hiển thị không đầy đủ.                                            |
