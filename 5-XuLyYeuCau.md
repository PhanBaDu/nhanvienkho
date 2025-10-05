# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng xử lý yêu cầu của Nhân viên kho_

## MỤC LỤC

1. [Chức năng xử lý yêu cầu](#1-chức-năng-xử-lý-yêu-cầu)
   - 1.1 [Xem danh sách yêu cầu](#11-xem-danh-sách-yêu-cầu)
   - 1.2 [Xử lý yêu cầu nhập hàng](#12-xử-lý-yêu-cầu-nhập-hàng)
   - 1.3 [Xử lý yêu cầu xuất hàng](#13-xử-lý-yêu-cầu-xuất-hàng)
   - 1.4 [Theo dõi trạng thái yêu cầu](#14-theo-dõi-trạng-thái-yêu-cầu)

---

## 1. CHỨC NĂNG XỬ LÝ YÊU CẦU

### 1.1 XEM DANH SÁCH YÊU CẦU

#### 1.1.1 Thông tin màn hình:

| Screen        | Danh sách yêu cầu                                                       |
| ------------- | ----------------------------------------------------------------------- |
| Description   | Hiển thị danh sách các yêu cầu cần xử lý từ bộ phận bán hàng và quản lý |
| Screen Access | Nhân viên kho chọn **Xử lý yêu cầu** từ menu chính                      |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                    | Type         | Data                                                                                       | Description                                       |
| ----------------------- | ------------ | ------------------------------------------------------------------------------------------ | ------------------------------------------------- |
| **Tiêu đề trang**       | Text         | Danh sách yêu cầu                                                                          | Tiêu đề chính của trang xử lý yêu cầu             |
| **Thống kê yêu cầu**    | Card Group   | Yêu cầu mới: 15<br>Đang xử lý: 8<br>Hoàn thành: 45<br>Chờ phê duyệt: 3                     | Hiển thị các chỉ số thống kê về tình hình yêu cầu |
| **Bộ lọc loại yêu cầu** | Dropdown     | Tất cả<br>Nhập hàng<br>Xuất hàng<br>Kiểm kê<br>Điều chỉnh                                  | Lọc danh sách yêu cầu theo loại                   |
| **Bộ lọc trạng thái**   | Dropdown     | Tất cả<br>Mới<br>Đang xử lý<br>Hoàn thành<br>Chờ phê duyệt<br>Từ chối                      | Lọc danh sách yêu cầu theo trạng thái             |
| **Bộ lọc ưu tiên**      | Dropdown     | Tất cả<br>Cao<br>Trung bình<br>Thấp                                                        | Lọc danh sách yêu cầu theo mức độ ưu tiên         |
| **Sắp xếp**             | Dropdown     | Thời gian tạo mới nhất<br>Thời gian tạo cũ nhất<br>Ưu tiên cao nhất<br>Mã yêu cầu          | Sắp xếp danh sách yêu cầu theo tiêu chí           |
| **Danh sách yêu cầu**   | Table        | Mã yêu cầu<br>Loại<br>Mô tả<br>Người tạo<br>Thời gian<br>Ưu tiên<br>Trạng thái<br>Thao tác | Hiển thị các yêu cầu cần xử lý dưới dạng bảng     |
| **Mã yêu cầu**          | Text + Badge | REQ001                                                                                     | Mã định danh của yêu cầu, kèm theo badge ưu tiên  |
| **Loại**                | Badge        | Nhập hàng<br>Xuất hàng<br>Kiểm kê<br>Điều chỉnh                                            | Loại yêu cầu                                      |
| **Mô tả**               | Text         | Yêu cầu nhập 100 cuốn sách mới                                                             | Mô tả ngắn gọn về yêu cầu                         |
| **Người tạo**           | Text         | Nguyễn Văn A                                                                               | Tên người tạo yêu cầu                             |
| **Thời gian**           | Text         | 2023-11-20 14:30                                                                           | Thời gian tạo yêu cầu                             |
| **Ưu tiên**             | Badge        | Cao<br>Trung bình<br>Thấp                                                                  | Mức độ ưu tiên của yêu cầu                        |
| **Trạng thái**          | Badge        | Mới<br>Đang xử lý<br>Hoàn thành<br>Chờ phê duyệt<br>Từ chối                                | Trạng thái hiện tại của yêu cầu                   |
| **Thao tác**            | Button Group | Xem chi tiết<br>Xử lý<br>Ghi chú                                                           | Các nút chức năng để thao tác trên yêu cầu        |
| **Nút xử lý hàng loạt** | Button       |                                                                                            | Nút xử lý nhiều yêu cầu cùng lúc                  |
| **Nút xuất báo cáo**    | Button       |                                                                                            | Nút xuất báo cáo yêu cầu                          |
| **Phân trang**          | Pagination   | Trang 1/25                                                                                 | Điều hướng giữa các trang                         |

#### 1.1.3 Hành động và xử lý:

| Action Name                   | Description                                                                                                                                                                                                                                                                                                                                    | Success                                                                                                                | Failure                                                                                                                |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Xem danh sách yêu cầu**     | Hiển thị danh sách các yêu cầu cần xử lý từ bộ phận bán hàng và quản lý. Bao gồm thông tin về mã yêu cầu, loại, mô tả, người tạo, thời gian, ưu tiên và trạng thái. Cung cấp bộ lọc theo loại yêu cầu, trạng thái và mức độ ưu tiên. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. Hiển thị thống kê tổng quan về tình hình yêu cầu. | Hiển thị danh sách yêu cầu đầy đủ với đầy đủ thông tin. Bộ lọc và sắp xếp hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách yêu cầu do lỗi hệ thống. Bộ lọc và sắp xếp không hoạt động. Thống kê hiển thị không chính xác. |
| **Xem chi tiết yêu cầu**      | Hiển thị chi tiết yêu cầu được chọn. Bao gồm thông tin đầy đủ về yêu cầu, danh sách sách liên quan, ghi chú và lịch sử xử lý. Cho phép xem tài liệu đính kèm nếu có. Hiển thị thông tin người tạo và người xử lý.                                                                                                                              | Chi tiết yêu cầu được hiển thị đầy đủ và chính xác.                                                                    | Không thể tải chi tiết yêu cầu. Thông tin hiển thị không đầy đủ.                                                       |
| **Lọc yêu cầu theo tiêu chí** | Cho phép nhân viên kho lọc danh sách yêu cầu theo các tiêu chí khác nhau. Lọc theo loại yêu cầu (nhập hàng, xuất hàng, kiểm kê, điều chỉnh). Lọc theo trạng thái (mới, đang xử lý, hoàn thành, chờ phê duyệt, từ chối). Lọc theo mức độ ưu tiên (cao, trung bình, thấp). Cập nhật danh sách theo tiêu chí đã chọn.                             | Danh sách yêu cầu được lọc chính xác theo tiêu chí đã chọn.                                                            | Bộ lọc không hoạt động. Kết quả lọc không chính xác.                                                                   |
| **Sắp xếp danh sách yêu cầu** | Cho phép nhân viên kho sắp xếp danh sách yêu cầu theo các tiêu chí khác nhau. Sắp xếp theo thời gian tạo (mới nhất, cũ nhất). Sắp xếp theo mức độ ưu tiên (cao nhất). Sắp xếp theo mã yêu cầu. Cập nhật thứ tự hiển thị danh sách.                                                                                                             | Danh sách yêu cầu được sắp xếp chính xác theo tiêu chí đã chọn.                                                        | Sắp xếp không hoạt động. Thứ tự hiển thị không đúng.                                                                   |

### 1.2 XỬ LÝ YÊU CẦU NHẬP HÀNG

#### 1.2.1 Thông tin màn hình:

| Screen        | Xử lý yêu cầu nhập hàng                                             |
| ------------- | ------------------------------------------------------------------- |
| Description   | Xử lý các yêu cầu nhập hàng từ bộ phận bán hàng và quản lý          |
| Screen Access | Nhân viên kho chọn **Xử lý yêu cầu nhập hàng** từ danh sách yêu cầu |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                       | Type         | Data                                                                                                                  | Description                                     |
| -------------------------- | ------------ | --------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| **Tiêu đề trang**          | Text         | Xử lý yêu cầu nhập hàng                                                                                               | Tiêu đề chính của trang xử lý yêu cầu nhập hàng |
| **Thông tin yêu cầu**      | Card         | Mã yêu cầu: REQ001<br>Người tạo: Nguyễn Văn A<br>Thời gian: 2023-11-20 14:30<br>Mô tả: Yêu cầu nhập 100 cuốn sách mới | Hiển thị thông tin cơ bản về yêu cầu nhập hàng  |
| **Danh sách sách yêu cầu** | Table        | Mã sách<br>Tên sách<br>Số lượng yêu cầu<br>Số lượng có sẵn<br>Trạng thái<br>Thao tác                                  | Bảng danh sách sách trong yêu cầu nhập hàng     |
| **Mã sách**                | Text         | BK001                                                                                                                 | Mã định danh của sách                           |
| **Tên sách**               | Text         | Đắc Nhân Tâm                                                                                                          | Tên của cuốn sách                               |
| **Số lượng yêu cầu**       | Text         | 50                                                                                                                    | Số lượng sách được yêu cầu nhập                 |
| **Số lượng có sẵn**        | Text         | 15                                                                                                                    | Số lượng sách hiện có trong kho                 |
| **Trạng thái**             | Badge        | Có sẵn<br>Hết hàng<br>Sắp hết                                                                                         | Trạng thái tồn kho của sách                     |
| **Thao tác**               | Button Group | Xác nhận<br>Từ chối<br>Điều chỉnh                                                                                     | Các nút chức năng để xử lý sách trong yêu cầu   |
| **Ghi chú xử lý**          | Textarea     |                                                                                                                       | Ô nhập ghi chú về việc xử lý yêu cầu            |
| **Nút xác nhận tất cả**    | Button       |                                                                                                                       | Nút xác nhận tất cả sách trong yêu cầu          |
| **Nút từ chối yêu cầu**    | Button       |                                                                                                                       | Nút từ chối toàn bộ yêu cầu nhập hàng           |
| **Nút lưu xử lý**          | Button       |                                                                                                                       | Nút lưu kết quả xử lý yêu cầu                   |
| **Thông báo xử lý**        | Alert        | Yêu cầu đã được xử lý thành công                                                                                      | Hiển thị thông báo kết quả xử lý yêu cầu        |

#### 1.2.3 Hành động và xử lý:

| Action Name                      | Description                                                                                                                                                                                                                                                                                                                      | Success                                                                         | Failure                                                                             |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **Xác nhận yêu cầu nhập hàng**   | Cho phép nhân viên kho xác nhận yêu cầu nhập hàng từ bộ phận bán hàng. Xem danh sách sách được yêu cầu nhập với số lượng và thông tin chi tiết. Kiểm tra tình trạng tồn kho hiện tại của các sách. Xác nhận từng sách hoặc toàn bộ yêu cầu. Thêm ghi chú về việc xử lý yêu cầu. Cập nhật trạng thái yêu cầu thành "Đã xác nhận". | Yêu cầu nhập hàng được xác nhận thành công. Trạng thái yêu cầu được cập nhật.   | Không thể xác nhận yêu cầu do lỗi hệ thống. Trạng thái yêu cầu không được cập nhật. |
| **Từ chối yêu cầu nhập hàng**    | Cho phép nhân viên kho từ chối yêu cầu nhập hàng nếu không phù hợp. Chọn lý do từ chối từ danh sách có sẵn hoặc nhập lý do tùy chỉnh. Thêm ghi chú chi tiết về việc từ chối. Cập nhật trạng thái yêu cầu thành "Từ chối". Gửi thông báo cho người tạo yêu cầu về việc từ chối.                                                   | Yêu cầu nhập hàng được từ chối thành công. Người tạo yêu cầu được thông báo.    | Không thể từ chối yêu cầu do lỗi hệ thống. Lỗi khi gửi thông báo.                   |
| **Điều chỉnh yêu cầu nhập hàng** | Cho phép nhân viên kho điều chỉnh yêu cầu nhập hàng theo tình hình thực tế. Thay đổi số lượng sách được yêu cầu nhập. Thêm hoặc bớt sách khỏi danh sách yêu cầu. Thêm ghi chú về việc điều chỉnh. Cập nhật trạng thái yêu cầu thành "Đã điều chỉnh". Gửi thông báo cho người tạo yêu cầu về việc điều chỉnh.                     | Yêu cầu nhập hàng được điều chỉnh thành công. Người tạo yêu cầu được thông báo. | Không thể điều chỉnh yêu cầu do lỗi hệ thống. Lỗi khi gửi thông báo.                |
| **Lưu kết quả xử lý**            | Lưu kết quả xử lý yêu cầu nhập hàng vào cơ sở dữ liệu. Ghi nhận tất cả các thay đổi về số lượng và danh sách sách. Lưu ghi chú và lý do xử lý. Cập nhật trạng thái yêu cầu cuối cùng. Gửi thông báo cho các bộ phận liên quan. Tạo lịch sử xử lý yêu cầu.                                                                        | Kết quả xử lý được lưu thành công. Các bộ phận liên quan được thông báo.        | Lỗi khi lưu kết quả xử lý. Lỗi khi gửi thông báo.                                   |

### 1.3 XỬ LÝ YÊU CẦU XUẤT HÀNG

#### 1.3.1 Thông tin màn hình:

| Screen        | Xử lý yêu cầu xuất hàng                                             |
| ------------- | ------------------------------------------------------------------- |
| Description   | Xử lý các yêu cầu xuất hàng từ bộ phận bán hàng                     |
| Screen Access | Nhân viên kho chọn **Xử lý yêu cầu xuất hàng** từ danh sách yêu cầu |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                    | Type         | Data                                                                                                                       | Description                                     |
| ----------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------- |
| **Tiêu đề trang**       | Text         | Xử lý yêu cầu xuất hàng                                                                                                    | Tiêu đề chính của trang xử lý yêu cầu xuất hàng |
| **Thông tin yêu cầu**   | Card         | Mã yêu cầu: REQ002<br>Người tạo: Trần Thị B<br>Thời gian: 2023-11-20 15:30<br>Mô tả: Yêu cầu xuất sách cho đơn hàng ORD001 | Hiển thị thông tin cơ bản về yêu cầu xuất hàng  |
| **Thông tin đơn hàng**  | Card         | Mã đơn hàng: ORD001<br>Khách hàng: Nguyễn Văn C<br>Địa chỉ: 123 Đường ABC<br>Thời gian giao: 2023-11-21 09:00              | Hiển thị thông tin đơn hàng liên quan           |
| **Danh sách sách xuất** | Table        | Mã sách<br>Tên sách<br>Số lượng yêu cầu<br>Số lượng có sẵn<br>Trạng thái<br>Thao tác                                       | Bảng danh sách sách trong yêu cầu xuất hàng     |
| **Mã sách**             | Text         | BK001                                                                                                                      | Mã định danh của sách                           |
| **Tên sách**            | Text         | Đắc Nhân Tâm                                                                                                               | Tên của cuốn sách                               |
| **Số lượng yêu cầu**    | Text         | 3                                                                                                                          | Số lượng sách được yêu cầu xuất                 |
| **Số lượng có sẵn**     | Text         | 15                                                                                                                         | Số lượng sách hiện có trong kho                 |
| **Trạng thái**          | Badge        | Có sẵn<br>Hết hàng<br>Sắp hết                                                                                              | Trạng thái tồn kho của sách                     |
| **Thao tác**            | Button Group | Xác nhận<br>Từ chối<br>Điều chỉnh                                                                                          | Các nút chức năng để xử lý sách trong yêu cầu   |
| **Ghi chú xử lý**       | Textarea     |                                                                                                                            | Ô nhập ghi chú về việc xử lý yêu cầu            |
| **Nút xác nhận tất cả** | Button       |                                                                                                                            | Nút xác nhận tất cả sách trong yêu cầu          |
| **Nút từ chối yêu cầu** | Button       |                                                                                                                            | Nút từ chối toàn bộ yêu cầu xuất hàng           |
| **Nút lưu xử lý**       | Button       |                                                                                                                            | Nút lưu kết quả xử lý yêu cầu                   |
| **Thông báo xử lý**     | Alert        | Yêu cầu đã được xử lý thành công                                                                                           | Hiển thị thông báo kết quả xử lý yêu cầu        |

#### 1.3.3 Hành động và xử lý:

| Action Name                      | Description                                                                                                                                                                                                                                                                                                                      | Success                                                                         | Failure                                                                             |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| **Xác nhận yêu cầu xuất hàng**   | Cho phép nhân viên kho xác nhận yêu cầu xuất hàng từ bộ phận bán hàng. Xem danh sách sách được yêu cầu xuất với số lượng và thông tin chi tiết. Kiểm tra tình trạng tồn kho hiện tại của các sách. Xác nhận từng sách hoặc toàn bộ yêu cầu. Thêm ghi chú về việc xử lý yêu cầu. Cập nhật trạng thái yêu cầu thành "Đã xác nhận". | Yêu cầu xuất hàng được xác nhận thành công. Trạng thái yêu cầu được cập nhật.   | Không thể xác nhận yêu cầu do lỗi hệ thống. Trạng thái yêu cầu không được cập nhật. |
| **Từ chối yêu cầu xuất hàng**    | Cho phép nhân viên kho từ chối yêu cầu xuất hàng nếu không đủ hàng hoặc không phù hợp. Chọn lý do từ chối từ danh sách có sẵn hoặc nhập lý do tùy chỉnh. Thêm ghi chú chi tiết về việc từ chối. Cập nhật trạng thái yêu cầu thành "Từ chối". Gửi thông báo cho người tạo yêu cầu về việc từ chối.                                | Yêu cầu xuất hàng được từ chối thành công. Người tạo yêu cầu được thông báo.    | Không thể từ chối yêu cầu do lỗi hệ thống. Lỗi khi gửi thông báo.                   |
| **Điều chỉnh yêu cầu xuất hàng** | Cho phép nhân viên kho điều chỉnh yêu cầu xuất hàng theo tình hình tồn kho thực tế. Thay đổi số lượng sách được yêu cầu xuất. Thay thế sách không có sẵn bằng sách tương tự. Thêm ghi chú về việc điều chỉnh. Cập nhật trạng thái yêu cầu thành "Đã điều chỉnh". Gửi thông báo cho người tạo yêu cầu về việc điều chỉnh.         | Yêu cầu xuất hàng được điều chỉnh thành công. Người tạo yêu cầu được thông báo. | Không thể điều chỉnh yêu cầu do lỗi hệ thống. Lỗi khi gửi thông báo.                |
| **Lưu kết quả xử lý**            | Lưu kết quả xử lý yêu cầu xuất hàng vào cơ sở dữ liệu. Ghi nhận tất cả các thay đổi về số lượng và danh sách sách. Lưu ghi chú và lý do xử lý. Cập nhật trạng thái yêu cầu cuối cùng. Gửi thông báo cho các bộ phận liên quan. Tạo lịch sử xử lý yêu cầu.                                                                        | Kết quả xử lý được lưu thành công. Các bộ phận liên quan được thông báo.        | Lỗi khi lưu kết quả xử lý. Lỗi khi gửi thông báo.                                   |

### 1.4 THEO DÕI TRẠNG THÁI YÊU CẦU

#### 1.4.1 Thông tin màn hình:

| Screen        | Theo dõi trạng thái yêu cầu                                   |
| ------------- | ------------------------------------------------------------- |
| Description   | Theo dõi trạng thái xử lý của các yêu cầu đã gửi              |
| Screen Access | Nhân viên kho chọn **Theo dõi yêu cầu** từ menu xử lý yêu cầu |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                    | Type         | Data                                                                                                     | Description                                |
| ----------------------- | ------------ | -------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| **Tiêu đề trang**       | Text         | Theo dõi trạng thái yêu cầu                                                                              | Tiêu đề chính của trang theo dõi yêu cầu   |
| **Bộ lọc thời gian**    | Form         | Từ ngày<br>Đến ngày<br>Khoảng thời gian                                                                  | Form lọc yêu cầu theo thời gian            |
| **Từ ngày**             | Input (Date) | 2023-11-01                                                                                               | Ngày bắt đầu theo dõi                      |
| **Đến ngày**            | Input (Date) | 2023-11-30                                                                                               | Ngày kết thúc theo dõi                     |
| **Khoảng thời gian**    | Select       | Hôm nay<br>Tuần này<br>Tháng này<br>Quý này<br>Tùy chọn                                                  | Lựa chọn khoảng thời gian có sẵn           |
| **Bộ lọc trạng thái**   | Dropdown     | Tất cả<br>Mới<br>Đang xử lý<br>Hoàn thành<br>Chờ phê duyệt<br>Từ chối                                    | Lọc yêu cầu theo trạng thái                |
| **Bộ lọc loại yêu cầu** | Dropdown     | Tất cả<br>Nhập hàng<br>Xuất hàng<br>Kiểm kê<br>Điều chỉnh                                                | Lọc yêu cầu theo loại                      |
| **Thống kê yêu cầu**    | Card Group   | Tổng yêu cầu: 150<br>Hoàn thành: 120<br>Đang xử lý: 20<br>Từ chối: 10                                    | Hiển thị thống kê tổng quan về yêu cầu     |
| **Biểu đồ trạng thái**  | Chart        | Biểu đồ tròn thể hiện tỷ lệ các trạng thái yêu cầu                                                       | Biểu đồ trực quan hóa trạng thái yêu cầu   |
| **Danh sách yêu cầu**   | Table        | Mã yêu cầu<br>Loại<br>Mô tả<br>Trạng thái<br>Thời gian tạo<br>Thời gian xử lý<br>Người xử lý<br>Thao tác | Hiển thị danh sách yêu cầu dưới dạng bảng  |
| **Mã yêu cầu**          | Text         | REQ001                                                                                                   | Mã định danh của yêu cầu                   |
| **Loại**                | Badge        | Nhập hàng<br>Xuất hàng<br>Kiểm kê<br>Điều chỉnh                                                          | Loại yêu cầu                               |
| **Mô tả**               | Text         | Yêu cầu nhập 100 cuốn sách mới                                                                           | Mô tả ngắn gọn về yêu cầu                  |
| **Trạng thái**          | Badge        | Mới<br>Đang xử lý<br>Hoàn thành<br>Chờ phê duyệt<br>Từ chối                                              | Trạng thái hiện tại của yêu cầu            |
| **Thời gian tạo**       | Text         | 2023-11-20 14:30                                                                                         | Thời gian tạo yêu cầu                      |
| **Thời gian xử lý**     | Text         | 2023-11-20 16:45                                                                                         | Thời gian xử lý yêu cầu                    |
| **Người xử lý**         | Text         | Nguyễn Văn A                                                                                             | Tên người xử lý yêu cầu                    |
| **Thao tác**            | Button Group | Xem chi tiết<br>Xem lịch sử<br>Cập nhật trạng thái                                                       | Các nút chức năng để thao tác trên yêu cầu |
| **Nút xuất báo cáo**    | Button       |                                                                                                          | Nút xuất báo cáo theo dõi yêu cầu          |
| **Phân trang**          | Pagination   | Trang 1/30                                                                                               | Điều hướng giữa các trang                  |

#### 1.4.3 Hành động và xử lý:

| Action Name                     | Description                                                                                                                                                                                                                                                                                                                               | Success                                                                                                                    | Failure                                                                                                                |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Theo dõi trạng thái yêu cầu** | Hiển thị danh sách các yêu cầu đã gửi với trạng thái xử lý hiện tại. Bao gồm thông tin về mã yêu cầu, loại, mô tả, trạng thái, thời gian tạo, thời gian xử lý và người xử lý. Cung cấp bộ lọc theo thời gian, trạng thái và loại yêu cầu. Hiển thị thống kê tổng quan về tình hình yêu cầu. Tạo biểu đồ trực quan hóa trạng thái yêu cầu. | Hiển thị danh sách yêu cầu đầy đủ với trạng thái chính xác. Bộ lọc hoạt động chính xác. Thống kê và biểu đồ hiển thị đúng. | Không thể tải danh sách yêu cầu do lỗi hệ thống. Bộ lọc không hoạt động. Thống kê và biểu đồ hiển thị không chính xác. |
| **Xem chi tiết yêu cầu**        | Hiển thị chi tiết yêu cầu được chọn. Bao gồm thông tin đầy đủ về yêu cầu, danh sách sách liên quan, ghi chú và lịch sử xử lý. Cho phép xem tài liệu đính kèm nếu có. Hiển thị thông tin người tạo và người xử lý.                                                                                                                         | Chi tiết yêu cầu được hiển thị đầy đủ và chính xác.                                                                        | Không thể tải chi tiết yêu cầu. Thông tin hiển thị không đầy đủ.                                                       |
| **Xem lịch sử xử lý**           | Hiển thị lịch sử chi tiết quá trình xử lý yêu cầu. Bao gồm thông tin về các bước xử lý, thời gian thực hiện, người thực hiện và ghi chú. Hiển thị theo dòng thời gian từ cũ đến mới nhất. Cho phép xem chi tiết từng bước xử lý.                                                                                                          | Lịch sử xử lý được hiển thị đầy đủ và chính xác.                                                                           | Không thể tải lịch sử xử lý. Thông tin hiển thị không đầy đủ.                                                          |
| **Cập nhật trạng thái yêu cầu** | Cho phép nhân viên kho cập nhật trạng thái yêu cầu nếu cần thiết. Thay đổi trạng thái yêu cầu (mới, đang xử lý, hoàn thành, chờ phê duyệt, từ chối). Thêm ghi chú về việc cập nhật trạng thái. Gửi thông báo cho người tạo yêu cầu về việc thay đổi trạng thái.                                                                           | Trạng thái yêu cầu được cập nhật thành công. Người tạo yêu cầu được thông báo.                                             | Không thể cập nhật trạng thái do lỗi hệ thống. Lỗi khi gửi thông báo.                                                  |
| **Xuất báo cáo theo dõi**       | Tạo báo cáo chi tiết về tình hình theo dõi yêu cầu. Bao gồm danh sách yêu cầu với trạng thái, thống kê tổng quan và biểu đồ trạng thái. Định dạng báo cáo theo chuẩn của công ty. Cho phép xuất báo cáo dưới dạng PDF hoặc Excel. Gửi báo cáo cho quản lý và các bộ phận liên quan.                                                       | Báo cáo theo dõi yêu cầu được tạo thành công. Báo cáo được gửi đến các bộ phận liên quan.                                  | Không thể tạo báo cáo. Lỗi khi xuất báo cáo. Lỗi khi gửi báo cáo.                                                      |
