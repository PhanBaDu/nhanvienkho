# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng hỗ trợ bán hàng của Nhân viên kho_

## MỤC LỤC

1. [Chức năng hỗ trợ bán hàng](#1-chức-năng-hỗ-trợ-bán-hàng)
   - 1.1 [Kiểm tra tồn kho cho đơn hàng](#11-kiểm-tra-tồn-kho-cho-đơn-hàng)
   - 1.2 [Xác nhận khả năng giao hàng](#12-xác-nhận-khả-năng-giao-hàng)
   - 1.3 [Cập nhật trạng thái đơn hàng](#13-cập-nhật-trạng-thái-đơn-hàng)
   - 1.4 [Hỗ trợ xử lý đơn hàng đặc biệt](#14-hỗ-trợ-xử-lý-đơn-hàng-đặc-biệt)

---

## 1. CHỨC NĂNG HỖ TRỢ BÁN HÀNG

### 1.1 KIỂM TRA TỒN KHO CHO ĐƠN HÀNG

#### 1.1.1 Thông tin màn hình:

| Screen        | Kiểm tra tồn kho cho đơn hàng                                       |
| ------------- | ------------------------------------------------------------------- |
| Description   | Kiểm tra tình trạng tồn kho để xác nhận khả năng thực hiện đơn hàng |
| Screen Access | Nhân viên kho chọn **Hỗ trợ bán hàng** từ menu chính                |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                        | Type         | Data                                                                                                | Description                                 |
| --------------------------- | ------------ | --------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| **Tiêu đề trang**           | Text         | Kiểm tra tồn kho cho đơn hàng                                                                       | Tiêu đề chính của trang kiểm tra tồn kho    |
| **Tìm kiếm đơn hàng**       | Form         | Mã đơn hàng<br>Mã khách hàng<br>Ngày tạo đơn                                                        | Form tìm kiếm đơn hàng cần kiểm tra         |
| **Mã đơn hàng**             | Input (Text) | ORD001                                                                                              | Ô nhập mã đơn hàng cần kiểm tra             |
| **Mã khách hàng**           | Input (Text) | CUS001                                                                                              | Ô nhập mã khách hàng để lọc đơn hàng        |
| **Ngày tạo đơn**            | Input (Date) | 2023-11-20                                                                                          | Ô nhập ngày tạo đơn hàng                    |
| **Nút tìm kiếm**            | Button       |                                                                                                     | Nút thực hiện tìm kiếm đơn hàng             |
| **Thông tin đơn hàng**      | Card         | Mã đơn hàng: ORD001<br>Khách hàng: Nguyễn Văn A<br>Ngày tạo: 2023-11-20<br>Tổng tiền: 1.500.000 VNĐ | Hiển thị thông tin cơ bản về đơn hàng       |
| **Danh sách sách đơn hàng** | Table        | Mã sách<br>Tên sách<br>Số lượng yêu cầu<br>Số lượng có sẵn<br>Trạng thái<br>Ghi chú                 | Bảng danh sách sách trong đơn hàng          |
| **Mã sách**                 | Text         | BK001                                                                                               | Mã định danh của sách                       |
| **Tên sách**                | Text         | Đắc Nhân Tâm                                                                                        | Tên của cuốn sách                           |
| **Số lượng yêu cầu**        | Text         | 3                                                                                                   | Số lượng sách khách hàng yêu cầu            |
| **Số lượng có sẵn**         | Text         | 15                                                                                                  | Số lượng sách hiện có trong kho             |
| **Trạng thái**              | Badge        | Có sẵn<br>Hết hàng<br>Sắp hết<br>Không có                                                           | Trạng thái tồn kho của sách                 |
| **Ghi chú**                 | Text         | Sách có sẵn đủ số lượng                                                                             | Ghi chú về tình trạng sách                  |
| **Tổng kết kiểm tra**       | Card         | Tổng sách: 5<br>Có sẵn: 4<br>Hết hàng: 1<br>Trạng thái: Có thể giao hàng                            | Hiển thị tổng kết kết quả kiểm tra tồn kho  |
| **Nút xác nhận giao hàng**  | Button       |                                                                                                     | Nút xác nhận có thể giao hàng cho đơn hàng  |
| **Nút từ chối giao hàng**   | Button       |                                                                                                     | Nút từ chối giao hàng do không đủ tồn kho   |
| **Nút đề xuất thay thế**    | Button       |                                                                                                     | Nút đề xuất sách thay thế cho sách hết hàng |
| **Thông báo kết quả**       | Alert        | Đơn hàng có thể giao hàng được                                                                      | Hiển thị thông báo kết quả kiểm tra         |

#### 1.1.3 Hành động và xử lý:

| Action Name                   | Description                                                                                                                                                                                                                                                    | Success                                                                       | Failure                                                                         |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Tìm kiếm đơn hàng**         | Cho phép nhân viên kho tìm kiếm đơn hàng cần kiểm tra tồn kho. Nhập mã đơn hàng, mã khách hàng hoặc ngày tạo đơn để tìm kiếm. Hiển thị danh sách đơn hàng phù hợp với tiêu chí tìm kiếm. Cho phép chọn đơn hàng cần kiểm tra từ danh sách kết quả.             | Danh sách đơn hàng được hiển thị chính xác theo tiêu chí tìm kiếm.            | Không tìm thấy đơn hàng phù hợp. Lỗi khi tải danh sách đơn hàng.                |
| **Kiểm tra tồn kho đơn hàng** | Kiểm tra tình trạng tồn kho cho tất cả sách trong đơn hàng. So sánh số lượng yêu cầu với số lượng có sẵn trong kho. Xác định trạng thái từng sách (có sẵn, hết hàng, sắp hết). Tính toán tổng kết khả năng giao hàng. Hiển thị ghi chú chi tiết cho từng sách. | Tình trạng tồn kho được kiểm tra chính xác. Tổng kết hiển thị đúng.           | Không thể kiểm tra tồn kho do lỗi hệ thống. Thông tin hiển thị không chính xác. |
| **Xác nhận giao hàng**        | Cho phép nhân viên kho xác nhận có thể giao hàng cho đơn hàng. Cập nhật trạng thái đơn hàng thành "Xác nhận giao hàng". Ghi nhận thời gian xác nhận và người thực hiện. Gửi thông báo cho bộ phận bán hàng về việc xác nhận. Tạo lịch sử xác nhận giao hàng.   | Đơn hàng được xác nhận giao hàng thành công. Bộ phận bán hàng được thông báo. | Không thể xác nhận giao hàng do lỗi hệ thống. Lỗi khi gửi thông báo.            |
| **Từ chối giao hàng**         | Cho phép nhân viên kho từ chối giao hàng nếu không đủ tồn kho. Chọn lý do từ chối từ danh sách có sẵn hoặc nhập lý do tùy chỉnh. Cập nhật trạng thái đơn hàng thành "Từ chối giao hàng". Gửi thông báo cho bộ phận bán hàng về việc từ chối.                   | Đơn hàng được từ chối giao hàng thành công. Bộ phận bán hàng được thông báo.  | Không thể từ chối giao hàng do lỗi hệ thống. Lỗi khi gửi thông báo.             |
| **Đề xuất sách thay thế**     | Cho phép nhân viên kho đề xuất sách thay thế cho sách hết hàng. Tìm kiếm sách tương tự về thể loại và tác giả. So sánh giá và đánh giá mức độ phù hợp. Thêm ghi chú về sách thay thế. Gửi đề xuất cho bộ phận bán hàng để xem xét.                             | Sách thay thế được đề xuất thành công. Bộ phận bán hàng nhận được đề xuất.    | Không tìm thấy sách thay thế phù hợp. Lỗi khi gửi đề xuất.                      |

### 1.2 XÁC NHẬN KHẢ NĂNG GIAO HÀNG

#### 1.2.1 Thông tin màn hình:

| Screen        | Xác nhận khả năng giao hàng                                       |
| ------------- | ----------------------------------------------------------------- |
| Description   | Xác nhận khả năng giao hàng cho các đơn hàng đã được kiểm tra     |
| Screen Access | Nhân viên kho chọn **Xác nhận giao hàng** từ menu hỗ trợ bán hàng |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                       | Type         | Data                                                                                    | Description                                             |
| -------------------------- | ------------ | --------------------------------------------------------------------------------------- | ------------------------------------------------------- |
| **Tiêu đề trang**          | Text         | Xác nhận khả năng giao hàng                                                             | Tiêu đề chính của trang xác nhận giao hàng              |
| **Bộ lọc đơn hàng**        | Form         | Trạng thái<br>Ngày tạo<br>Mã khách hàng<br>Mức độ ưu tiên                               | Form lọc đơn hàng cần xác nhận                          |
| **Trạng thái**             | Dropdown     | Tất cả<br>Chờ xác nhận<br>Đã xác nhận<br>Từ chối<br>Đang xử lý                          | Lọc đơn hàng theo trạng thái                            |
| **Ngày tạo**               | Input (Date) | 2023-11-20                                                                              | Ô nhập ngày tạo đơn hàng                                |
| **Mã khách hàng**          | Input (Text) | CUS001                                                                                  | Ô nhập mã khách hàng                                    |
| **Mức độ ưu tiên**         | Dropdown     | Tất cả<br>Cao<br>Trung bình<br>Thấp                                                     | Lọc đơn hàng theo mức độ ưu tiên                        |
| **Danh sách đơn hàng**     | Table        | Mã đơn hàng<br>Khách hàng<br>Ngày tạo<br>Tổng tiền<br>Trạng thái<br>Ưu tiên<br>Thao tác | Hiển thị danh sách đơn hàng cần xác nhận dưới dạng bảng |
| **Mã đơn hàng**            | Text + Badge | ORD001                                                                                  | Mã định danh của đơn hàng, kèm theo badge ưu tiên       |
| **Khách hàng**             | Text         | Nguyễn Văn A                                                                            | Tên khách hàng                                          |
| **Ngày tạo**               | Text         | 2023-11-20                                                                              | Ngày tạo đơn hàng                                       |
| **Tổng tiền**              | Text         | 1.500.000 VNĐ                                                                           | Tổng giá trị đơn hàng                                   |
| **Trạng thái**             | Badge        | Chờ xác nhận<br>Đã xác nhận<br>Từ chối<br>Đang xử lý                                    | Trạng thái hiện tại của đơn hàng                        |
| **Ưu tiên**                | Badge        | Cao<br>Trung bình<br>Thấp                                                               | Mức độ ưu tiên của đơn hàng                             |
| **Thao tác**               | Button Group | Xem chi tiết<br>Xác nhận<br>Từ chối<br>Đề xuất thay thế                                 | Các nút chức năng để thao tác trên đơn hàng             |
| **Nút xác nhận hàng loạt** | Button       |                                                                                         | Nút xác nhận nhiều đơn hàng cùng lúc                    |
| **Nút xuất báo cáo**       | Button       |                                                                                         | Nút xuất báo cáo xác nhận giao hàng                     |
| **Phân trang**             | Pagination   | Trang 1/20                                                                              | Điều hướng giữa các trang                               |

#### 1.2.3 Hành động và xử lý:

| Action Name                | Description                                                                                                                                                                                                                                                                                           | Success                                                                                   | Failure                                                                      |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| **Xem danh sách đơn hàng** | Hiển thị danh sách các đơn hàng cần xác nhận khả năng giao hàng. Bao gồm thông tin về mã đơn hàng, khách hàng, ngày tạo, tổng tiền, trạng thái và mức độ ưu tiên. Cung cấp bộ lọc theo trạng thái, ngày tạo, mã khách hàng và mức độ ưu tiên. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. | Danh sách đơn hàng được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. | Không thể tải danh sách đơn hàng do lỗi hệ thống. Bộ lọc không hoạt động.    |
| **Xem chi tiết đơn hàng**  | Hiển thị chi tiết đơn hàng được chọn. Bao gồm thông tin đầy đủ về đơn hàng, danh sách sách, thông tin khách hàng và địa chỉ giao hàng. Hiển thị kết quả kiểm tra tồn kho cho từng sách. Cho phép xem lịch sử xử lý đơn hàng.                                                                          | Chi tiết đơn hàng được hiển thị đầy đủ và chính xác.                                      | Không thể tải chi tiết đơn hàng. Thông tin hiển thị không đầy đủ.            |
| **Xác nhận giao hàng**     | Cho phép nhân viên kho xác nhận khả năng giao hàng cho đơn hàng. Cập nhật trạng thái đơn hàng thành "Đã xác nhận giao hàng". Ghi nhận thời gian xác nhận và người thực hiện. Gửi thông báo cho bộ phận bán hàng và khách hàng. Tạo lịch sử xác nhận giao hàng.                                        | Đơn hàng được xác nhận giao hàng thành công. Các bộ phận liên quan được thông báo.        | Không thể xác nhận giao hàng do lỗi hệ thống. Lỗi khi gửi thông báo.         |
| **Từ chối giao hàng**      | Cho phép nhân viên kho từ chối giao hàng nếu không đủ tồn kho hoặc không phù hợp. Chọn lý do từ chối từ danh sách có sẵn hoặc nhập lý do tùy chỉnh. Cập nhật trạng thái đơn hàng thành "Từ chối giao hàng". Gửi thông báo cho bộ phận bán hàng và khách hàng.                                         | Đơn hàng được từ chối giao hàng thành công. Các bộ phận liên quan được thông báo.         | Không thể từ chối giao hàng do lỗi hệ thống. Lỗi khi gửi thông báo.          |
| **Xác nhận hàng loạt**     | Cho phép nhân viên kho xác nhận giao hàng cho nhiều đơn hàng cùng lúc. Chọn các đơn hàng cần xác nhận. Xác nhận tất cả đơn hàng đã chọn. Ghi nhận thời gian xác nhận và người thực hiện. Gửi thông báo hàng loạt cho các bộ phận liên quan.                                                           | Tất cả đơn hàng được xác nhận thành công. Thông báo được gửi đến các bộ phận liên quan.   | Một số đơn hàng không được xác nhận do lỗi. Lỗi khi gửi thông báo hàng loạt. |

### 1.3 CẬP NHẬT TRẠNG THÁI ĐƠN HÀNG

#### 1.3.1 Thông tin màn hình:

| Screen        | Cập nhật trạng thái đơn hàng                                         |
| ------------- | -------------------------------------------------------------------- |
| Description   | Cập nhật trạng thái xử lý của các đơn hàng trong quá trình giao hàng |
| Screen Access | Nhân viên kho chọn **Cập nhật trạng thái** từ menu hỗ trợ bán hàng   |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                         | Type         | Data                                                                                     | Description                                                        |
| ---------------------------- | ------------ | ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------ |
| **Tiêu đề trang**            | Text         | Cập nhật trạng thái đơn hàng                                                             | Tiêu đề chính của trang cập nhật trạng thái                        |
| **Bộ lọc đơn hàng**          | Form         | Mã đơn hàng<br>Trạng thái hiện tại<br>Ngày cập nhật<br>Mã khách hàng                     | Form lọc đơn hàng cần cập nhật trạng thái                          |
| **Mã đơn hàng**              | Input (Text) | ORD001                                                                                   | Ô nhập mã đơn hàng cần cập nhật                                    |
| **Trạng thái hiện tại**      | Dropdown     | Tất cả<br>Đã xác nhận<br>Đang chuẩn bị<br>Đang giao<br>Đã giao<br>Hoàn thành             | Lọc đơn hàng theo trạng thái hiện tại                              |
| **Ngày cập nhật**            | Input (Date) | 2023-11-20                                                                               | Ô nhập ngày cập nhật trạng thái                                    |
| **Mã khách hàng**            | Input (Text) | CUS001                                                                                   | Ô nhập mã khách hàng                                               |
| **Danh sách đơn hàng**       | Table        | Mã đơn hàng<br>Khách hàng<br>Trạng thái hiện tại<br>Ngày cập nhật<br>Ghi chú<br>Thao tác | Hiển thị danh sách đơn hàng cần cập nhật trạng thái dưới dạng bảng |
| **Mã đơn hàng**              | Text         | ORD001                                                                                   | Mã định danh của đơn hàng                                          |
| **Khách hàng**               | Text         | Nguyễn Văn A                                                                             | Tên khách hàng                                                     |
| **Trạng thái hiện tại**      | Badge        | Đã xác nhận<br>Đang chuẩn bị<br>Đang giao<br>Đã giao<br>Hoàn thành                       | Trạng thái hiện tại của đơn hàng                                   |
| **Ngày cập nhật**            | Text         | 2023-11-20 14:30                                                                         | Ngày cập nhật trạng thái lần cuối                                  |
| **Ghi chú**                  | Text         | Đơn hàng đã được chuẩn bị xong                                                           | Ghi chú về trạng thái đơn hàng                                     |
| **Thao tác**                 | Button Group | Xem chi tiết<br>Cập nhật trạng thái<br>Xem lịch sử                                       | Các nút chức năng để thao tác trên đơn hàng                        |
| **Form cập nhật trạng thái** | Modal        | Trạng thái mới<br>Ghi chú<br>Ngày cập nhật<br>Người thực hiện                            | Modal form cập nhật trạng thái đơn hàng                            |
| **Trạng thái mới**           | Select       | Đang chuẩn bị<br>Đang giao<br>Đã giao<br>Hoàn thành<br>Hủy bỏ                            | Lựa chọn trạng thái mới cho đơn hàng                               |
| **Ghi chú**                  | Textarea     |                                                                                          | Ô nhập ghi chú về việc cập nhật trạng thái                         |
| **Ngày cập nhật**            | Input (Date) | 2023-11-20                                                                               | Ngày cập nhật trạng thái                                           |
| **Người thực hiện**          | Text         | Nguyễn Văn A                                                                             | Tên người thực hiện cập nhật (tự động điền)                        |
| **Nút lưu cập nhật**         | Button       |                                                                                          | Nút lưu cập nhật trạng thái đơn hàng                               |
| **Nút hủy**                  | Button       |                                                                                          | Nút hủy cập nhật trạng thái                                        |
| **Phân trang**               | Pagination   | Trang 1/15                                                                               | Điều hướng giữa các trang                                          |

#### 1.3.3 Hành động và xử lý:

| Action Name                      | Description                                                                                                                                                                                                                                                                                                 | Success                                                                                               | Failure                                                                   |
| -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| **Xem danh sách đơn hàng**       | Hiển thị danh sách các đơn hàng cần cập nhật trạng thái. Bao gồm thông tin về mã đơn hàng, khách hàng, trạng thái hiện tại, ngày cập nhật và ghi chú. Cung cấp bộ lọc theo mã đơn hàng, trạng thái hiện tại, ngày cập nhật và mã khách hàng. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau.        | Danh sách đơn hàng được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác.             | Không thể tải danh sách đơn hàng do lỗi hệ thống. Bộ lọc không hoạt động. |
| **Cập nhật trạng thái đơn hàng** | Cho phép nhân viên kho cập nhật trạng thái xử lý của đơn hàng. Chọn trạng thái mới từ danh sách có sẵn (đang chuẩn bị, đang giao, đã giao, hoàn thành, hủy bỏ). Thêm ghi chú về việc cập nhật trạng thái. Ghi nhận thời gian cập nhật và người thực hiện. Gửi thông báo cho bộ phận bán hàng và khách hàng. | Trạng thái đơn hàng được cập nhật thành công. Các bộ phận liên quan được thông báo.                   | Không thể cập nhật trạng thái do lỗi hệ thống. Lỗi khi gửi thông báo.     |
| **Xem lịch sử cập nhật**         | Hiển thị lịch sử chi tiết các lần cập nhật trạng thái đơn hàng. Bao gồm thông tin về trạng thái cũ, trạng thái mới, thời gian cập nhật, người thực hiện và ghi chú. Hiển thị theo dòng thời gian từ cũ đến mới nhất. Cho phép xem chi tiết từng lần cập nhật.                                               | Lịch sử cập nhật được hiển thị đầy đủ và chính xác.                                                   | Không thể tải lịch sử cập nhật. Thông tin hiển thị không đầy đủ.          |
| **Lưu cập nhật trạng thái**      | Lưu cập nhật trạng thái đơn hàng vào cơ sở dữ liệu. Ghi nhận tất cả thông tin về trạng thái mới, ghi chú và thời gian cập nhật. Tạo lịch sử cập nhật trạng thái. Gửi thông báo cho các bộ phận liên quan. Cập nhật trạng thái đơn hàng trong hệ thống.                                                      | Cập nhật trạng thái được lưu thành công. Lịch sử được ghi nhận. Các bộ phận liên quan được thông báo. | Lỗi khi lưu cập nhật trạng thái. Lỗi khi gửi thông báo.                   |

### 1.4 HỖ TRỢ XỬ LÝ ĐƠN HÀNG ĐẶC BIỆT

#### 1.4.1 Thông tin màn hình:

| Screen        | Hỗ trợ xử lý đơn hàng đặc biệt                                   |
| ------------- | ---------------------------------------------------------------- |
| Description   | Xử lý các đơn hàng có yêu cầu đặc biệt hoặc phức tạp             |
| Screen Access | Nhân viên kho chọn **Đơn hàng đặc biệt** từ menu hỗ trợ bán hàng |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                    | Type         | Data                                                                                             | Description                                             |
| ----------------------- | ------------ | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------- |
| **Tiêu đề trang**       | Text         | Hỗ trợ xử lý đơn hàng đặc biệt                                                                   | Tiêu đề chính của trang xử lý đơn hàng đặc biệt         |
| **Bộ lọc đơn hàng**     | Form         | Loại đặc biệt<br>Mức độ ưu tiên<br>Trạng thái<br>Ngày tạo                                        | Form lọc đơn hàng đặc biệt                              |
| **Loại đặc biệt**       | Dropdown     | Tất cả<br>Giao hàng nhanh<br>Đơn hàng lớn<br>Đơn hàng quốc tế<br>Đơn hàng VIP                    | Lọc đơn hàng theo loại đặc biệt                         |
| **Mức độ ưu tiên**      | Dropdown     | Tất cả<br>Cao<br>Trung bình<br>Thấp                                                              | Lọc đơn hàng theo mức độ ưu tiên                        |
| **Trạng thái**          | Dropdown     | Tất cả<br>Chờ xử lý<br>Đang xử lý<br>Hoàn thành<br>Từ chối                                       | Lọc đơn hàng theo trạng thái                            |
| **Ngày tạo**            | Input (Date) | 2023-11-20                                                                                       | Ô nhập ngày tạo đơn hàng                                |
| **Danh sách đơn hàng**  | Table        | Mã đơn hàng<br>Loại đặc biệt<br>Khách hàng<br>Mô tả yêu cầu<br>Ưu tiên<br>Trạng thái<br>Thao tác | Hiển thị danh sách đơn hàng đặc biệt dưới dạng bảng     |
| **Mã đơn hàng**         | Text + Badge | ORD001                                                                                           | Mã định danh của đơn hàng, kèm theo badge loại đặc biệt |
| **Loại đặc biệt**       | Badge        | Giao hàng nhanh<br>Đơn hàng lớn<br>Đơn hàng quốc tế<br>Đơn hàng VIP                              | Loại đặc biệt của đơn hàng                              |
| **Khách hàng**          | Text         | Nguyễn Văn A                                                                                     | Tên khách hàng                                          |
| **Mô tả yêu cầu**       | Text         | Giao hàng trong 2 giờ                                                                            | Mô tả yêu cầu đặc biệt của đơn hàng                     |
| **Ưu tiên**             | Badge        | Cao<br>Trung bình<br>Thấp                                                                        | Mức độ ưu tiên của đơn hàng                             |
| **Trạng thái**          | Badge        | Chờ xử lý<br>Đang xử lý<br>Hoàn thành<br>Từ chối                                                 | Trạng thái hiện tại của đơn hàng                        |
| **Thao tác**            | Button Group | Xem chi tiết<br>Xử lý<br>Chuyển tiếp<br>Ghi chú                                                  | Các nút chức năng để thao tác trên đơn hàng đặc biệt    |
| **Form xử lý đặc biệt** | Modal        | Phương án xử lý<br>Thời gian dự kiến<br>Ghi chú<br>Người phụ trách                               | Modal form xử lý đơn hàng đặc biệt                      |
| **Phương án xử lý**     | Textarea     |                                                                                                  | Ô nhập phương án xử lý đơn hàng đặc biệt                |
| **Thời gian dự kiến**   | Input (Date) | 2023-11-21 10:00                                                                                 | Thời gian dự kiến hoàn thành xử lý                      |
| **Ghi chú**             | Textarea     |                                                                                                  | Ô nhập ghi chú về việc xử lý đơn hàng đặc biệt          |
| **Người phụ trách**     | Select       | Nguyễn Văn A<br>Trần Thị B<br>Lê Văn C                                                           | Lựa chọn người phụ trách xử lý đơn hàng                 |
| **Nút lưu xử lý**       | Button       |                                                                                                  | Nút lưu phương án xử lý đơn hàng đặc biệt               |
| **Nút chuyển tiếp**     | Button       |                                                                                                  | Nút chuyển tiếp đơn hàng cho bộ phận khác               |
| **Phân trang**          | Pagination   | Trang 1/10                                                                                       | Điều hướng giữa các trang                               |

#### 1.4.3 Hành động và xử lý:

| Action Name                         | Description                                                                                                                                                                                                                                                                                                      | Success                                                                                            | Failure                                                                            |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Xem danh sách đơn hàng đặc biệt** | Hiển thị danh sách các đơn hàng có yêu cầu đặc biệt hoặc phức tạp. Bao gồm thông tin về mã đơn hàng, loại đặc biệt, khách hàng, mô tả yêu cầu, mức độ ưu tiên và trạng thái. Cung cấp bộ lọc theo loại đặc biệt, mức độ ưu tiên, trạng thái và ngày tạo. Cho phép sắp xếp danh sách theo các tiêu chí khác nhau. | Danh sách đơn hàng đặc biệt được hiển thị đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. | Không thể tải danh sách đơn hàng đặc biệt do lỗi hệ thống. Bộ lọc không hoạt động. |
| **Xem chi tiết đơn hàng đặc biệt**  | Hiển thị chi tiết đơn hàng đặc biệt được chọn. Bao gồm thông tin đầy đủ về đơn hàng, yêu cầu đặc biệt, danh sách sách, thông tin khách hàng và lịch sử xử lý. Cho phép xem tài liệu đính kèm và ghi chú chi tiết.                                                                                                | Chi tiết đơn hàng đặc biệt được hiển thị đầy đủ và chính xác.                                      | Không thể tải chi tiết đơn hàng đặc biệt. Thông tin hiển thị không đầy đủ.         |
| **Xử lý đơn hàng đặc biệt**         | Cho phép nhân viên kho xử lý đơn hàng đặc biệt theo yêu cầu cụ thể. Tạo phương án xử lý chi tiết cho đơn hàng. Ước tính thời gian hoàn thành xử lý. Chỉ định người phụ trách xử lý đơn hàng. Thêm ghi chú về quá trình xử lý. Cập nhật trạng thái đơn hàng thành "Đang xử lý".                                   | Đơn hàng đặc biệt được xử lý thành công. Phương án xử lý được lưu.                                 | Không thể xử lý đơn hàng đặc biệt do lỗi hệ thống. Phương án xử lý không được lưu. |
| **Chuyển tiếp đơn hàng**            | Cho phép nhân viên kho chuyển tiếp đơn hàng đặc biệt cho bộ phận khác nếu cần thiết. Chọn bộ phận nhận đơn hàng từ danh sách có sẵn. Thêm ghi chú về lý do chuyển tiếp. Gửi thông báo cho bộ phận nhận đơn hàng. Cập nhật trạng thái đơn hàng thành "Đã chuyển tiếp".                                            | Đơn hàng được chuyển tiếp thành công. Bộ phận nhận được thông báo.                                 | Không thể chuyển tiếp đơn hàng do lỗi hệ thống. Lỗi khi gửi thông báo.             |
| **Lưu phương án xử lý**             | Lưu phương án xử lý đơn hàng đặc biệt vào cơ sở dữ liệu. Ghi nhận tất cả thông tin về phương án xử lý, thời gian dự kiến, ghi chú và người phụ trách. Tạo lịch sử xử lý đơn hàng đặc biệt. Gửi thông báo cho các bộ phận liên quan.                                                                              | Phương án xử lý được lưu thành công. Lịch sử được ghi nhận. Các bộ phận liên quan được thông báo.  | Lỗi khi lưu phương án xử lý. Lỗi khi gửi thông báo.                                |
