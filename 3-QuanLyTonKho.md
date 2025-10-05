# TỔNG HỢP CHỨC NĂNG

_Dựa trên tài liệu yêu cầu KH-19_RO.MD - Chức năng quản lý tồn kho của Nhân viên kho_

## MỤC LỤC

1. [Chức năng quản lý tồn kho](#1-chức-năng-quản-lý-tồn-kho)
   - 1.1 [Cập nhật số lượng tồn kho](#11-cập-nhật-số-lượng-tồn-kho)
   - 1.2 [Nhập hàng](#12-nhập-hàng)
   - 1.3 [Xuất hàng](#13-xuất-hàng)
   - 1.4 [Kiểm kê kho](#14-kiểm-kê-kho)

---

## 1. CHỨC NĂNG QUẢN LÝ TỒN KHO

### 1.1 CẬP NHẬT SỐ LƯỢNG TỒN KHO

#### 1.1.1 Thông tin màn hình:

| Screen        | Cập nhật số lượng tồn kho                                      |
| ------------- | -------------------------------------------------------------- |
| Description   | Cho phép nhân viên kho thay đổi số lượng sách có sẵn trong kho |
| Screen Access | Nhân viên kho chọn **Quản lý tồn kho** từ menu chính           |

#### 1.1.2 Chi tiết thành phần màn hình:

| Item                       | Type           | Data                                                                            | Description                                              |
| -------------------------- | -------------- | ------------------------------------------------------------------------------- | -------------------------------------------------------- |
| **Tiêu đề trang**          | Text           | Quản lý tồn kho                                                                 | Tiêu đề chính của trang quản lý tồn kho                  |
| **Thống kê tổng quan**     | Card Group     | Tổng sách: 1,250<br>Sách có sẵn: 1,180<br>Sách hết hàng: 45<br>Sách sắp hết: 25 | Hiển thị các chỉ số thống kê nhanh về tình hình tồn kho  |
| **Tìm kiếm sách**          | Input (Text)   |                                                                                 | Ô nhập liệu để tìm kiếm sách cần cập nhật tồn kho        |
| **Bộ lọc trạng thái**      | Dropdown       | Tất cả<br>Có sẵn<br>Hết hàng<br>Sắp hết<br>Ẩn                                   | Lọc danh sách sách theo trạng thái tồn kho               |
| **Danh sách sách**         | Table          | Mã sách<br>Tên sách<br>Số lượng hiện tại<br>Số lượng mới<br>Thao tác            | Hiển thị các sách cần cập nhật tồn kho dưới dạng bảng    |
| **Mã sách**                | Text + Badge   | BK001                                                                           | Mã định danh của sách, kèm theo badge trạng thái tồn kho |
| **Tên sách**               | Text           | Đắc Nhân Tâm                                                                    | Tên của cuốn sách                                        |
| **Số lượng hiện tại**      | Text           | 15                                                                              | Số lượng sách hiện có trong kho                          |
| **Số lượng mới**           | Input (Number) |                                                                                 | Ô nhập số lượng mới cho sách                             |
| **Thao tác**               | Button Group   | Cập nhật<br>Xem lịch sử                                                         | Các nút chức năng để thao tác trên tồn kho               |
| **Lý do cập nhật**         | Textarea       |                                                                                 | Ô nhập lý do cập nhật số lượng (bắt buộc)                |
| **Nút cập nhật hàng loạt** | Button         |                                                                                 | Nút cập nhật tồn kho cho nhiều sách cùng lúc             |
| **Phân trang**             | Pagination     | Trang 1/50                                                                      | Điều hướng giữa các trang                                |

#### 1.1.3 Hành động và xử lý:

| Action Name                   | Description                                                                                                                                                                                                                                                                                                                                                                                             | Success                                                                                                           | Failure                                                                              |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| **Cập nhật số lượng tồn kho** | Cho phép nhân viên kho thay đổi số lượng sách có sẵn trong kho. Hiển thị danh sách sách với số lượng hiện tại. Cho phép nhập số lượng mới cho từng sách. Yêu cầu nhập lý do cập nhật để đảm bảo tính minh bạch. Xác thực số lượng mới phải là số dương. Cập nhật số lượng tồn kho trong cơ sở dữ liệu. Ghi nhận lịch sử cập nhật tồn kho. Tự động cập nhật trạng thái sách (có sẵn, hết hàng, sắp hết). | Số lượng tồn kho được cập nhật thành công. Lịch sử cập nhật được ghi nhận. Trạng thái sách được cập nhật tự động. | Số lượng mới không hợp lệ. Lỗi khi cập nhật cơ sở dữ liệu. Chưa nhập lý do cập nhật. |
| **Cập nhật hàng loạt**        | Cho phép nhân viên kho cập nhật tồn kho cho nhiều sách cùng lúc. Chọn nhiều sách cần cập nhật. Nhập số lượng mới cho tất cả sách đã chọn. Nhập lý do cập nhật chung. Xác thực tất cả số lượng mới đều hợp lệ. Cập nhật hàng loạt vào cơ sở dữ liệu. Ghi nhận lịch sử cập nhật cho từng sách.                                                                                                            | Tất cả sách được cập nhật tồn kho thành công. Lịch sử được ghi nhận đầy đủ.                                       | Một số sách không được cập nhật do lỗi. Số lượng của một số sách không hợp lệ.       |
| **Xem lịch sử cập nhật**      | Hiển thị lịch sử chi tiết các lần cập nhật tồn kho của sách. Bao gồm thông tin về ngày cập nhật, số lượng cũ, số lượng mới, lý do cập nhật và người thực hiện. Hiển thị theo dòng thời gian từ cũ đến mới nhất. Cho phép xem chi tiết từng lần cập nhật.                                                                                                                                                | Hiển thị đầy đủ lịch sử cập nhật tồn kho. Thông tin chi tiết được hiển thị chính xác.                             | Không thể tải lịch sử cập nhật do lỗi hệ thống. Lịch sử hiển thị không đầy đủ.       |

### 1.2 NHẬP HÀNG

#### 1.2.1 Thông tin màn hình:

| Screen        | Nhập hàng                                                |
| ------------- | -------------------------------------------------------- |
| Description   | Ghi nhận việc nhập sách mới từ nhà cung cấp vào kho      |
| Screen Access | Nhân viên kho chọn **Nhập hàng** từ menu quản lý tồn kho |

#### 1.2.2 Chi tiết thành phần màn hình:

| Item                     | Type           | Data                                                                      | Description                                            |
| ------------------------ | -------------- | ------------------------------------------------------------------------- | ------------------------------------------------------ |
| **Tiêu đề trang**        | Text           | Nhập hàng                                                                 | Tiêu đề chính của trang nhập hàng                      |
| **Thông tin đơn nhập**   | Form           | Mã đơn nhập<br>Nhà cung cấp<br>Ngày nhập<br>Ghi chú                       | Form nhập thông tin cơ bản về đơn nhập hàng            |
| **Mã đơn nhập**          | Text           | IMP001                                                                    | Mã định danh duy nhất của đơn nhập (tự động tạo)       |
| **Nhà cung cấp**         | Select         | Nhà xuất bản Trẻ<br>NXB Kim Đồng<br>NXB Giáo dục<br>NXB Hội nhà văn       | Lựa chọn nhà cung cấp sách                             |
| **Ngày nhập**            | Input (Date)   | 2023-11-20                                                                | Ngày thực hiện nhập hàng                               |
| **Ghi chú**              | Textarea       |                                                                           | Ghi chú về đơn nhập hàng                               |
| **Danh sách sách nhập**  | Table          | Mã sách<br>Tên sách<br>Số lượng nhập<br>Giá nhập<br>Tổng tiền<br>Thao tác | Bảng danh sách sách trong đơn nhập                     |
| **Mã sách**              | Select         | BK001, BK002, BK003...                                                    | Lựa chọn sách cần nhập từ danh sách có sẵn             |
| **Tên sách**             | Text           | Đắc Nhân Tâm                                                              | Tên sách được chọn (tự động hiển thị)                  |
| **Số lượng nhập**        | Input (Number) |                                                                           | Ô nhập số lượng sách nhập                              |
| **Giá nhập**             | Input (Number) |                                                                           | Ô nhập giá nhập của sách                               |
| **Tổng tiền**            | Text           | 1.350.000 VNĐ                                                             | Tổng tiền của sách (tự động tính)                      |
| **Thao tác**             | Button         | Xóa                                                                       | Nút xóa sách khỏi danh sách nhập                       |
| **Nút thêm sách**        | Button         | Thêm sách                                                                 | Nút thêm sách mới vào danh sách nhập                   |
| **Tổng đơn nhập**        | Card           | Tổng số sách: 15<br>Tổng tiền: 15.000.000 VNĐ                             | Hiển thị tổng kết đơn nhập hàng                        |
| **Nút lưu đơn nhập**     | Button         |                                                                           | Nút lưu đơn nhập hàng                                  |
| **Nút hủy**              | Button         |                                                                           | Nút hủy đơn nhập hàng                                  |
| **Thông báo lỗi**        | Alert          | Vui lòng chọn ít nhất một sách<br>Số lượng phải lớn hơn 0                 | Hiển thị thông báo lỗi khi nhập thông tin không hợp lệ |
| **Thông báo thành công** | Alert          | Nhập hàng thành công                                                      | Hiển thị thông báo khi nhập hàng thành công            |

#### 1.2.3 Hành động và xử lý:

| Action Name                | Description                                                                                                                                                                                                                                                                                                       | Success                                                                                         | Failure                                                                                         |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| **Tạo đơn nhập hàng**      | Cho phép nhân viên kho tạo đơn nhập hàng mới. Tự động tạo mã đơn nhập duy nhất. Chọn nhà cung cấp từ danh sách có sẵn. Nhập ngày nhập hàng và ghi chú. Thêm các sách cần nhập vào danh sách. Nhập số lượng và giá nhập cho từng sách. Tự động tính tổng tiền đơn nhập. Xác thực thông tin đơn nhập trước khi lưu. | Đơn nhập hàng được tạo thành công. Mã đơn nhập được tạo tự động. Tổng tiền được tính chính xác. | Thông tin đơn nhập không hợp lệ. Lỗi khi tạo mã đơn nhập. Không thể tính tổng tiền.             |
| **Thêm sách vào đơn nhập** | Cho phép nhân viên kho thêm sách vào danh sách đơn nhập. Chọn sách từ danh sách có sẵn trong hệ thống. Nhập số lượng sách cần nhập. Nhập giá nhập của sách. Tự động tính tổng tiền cho sách đó. Cập nhật tổng tiền đơn nhập. Xác thực số lượng và giá nhập phải là số dương.                                      | Sách được thêm vào đơn nhập thành công. Tổng tiền được cập nhật chính xác.                      | Sách đã tồn tại trong đơn nhập. Số lượng hoặc giá nhập không hợp lệ.                            |
| **Lưu đơn nhập hàng**      | Lưu đơn nhập hàng vào cơ sở dữ liệu. Cập nhật số lượng tồn kho cho tất cả sách trong đơn nhập. Ghi nhận lịch sử nhập hàng. Cập nhật thông tin nhà cung cấp nếu cần. Tạo phiếu nhập kho. Gửi thông báo cho bộ phận liên quan.                                                                                      | Đơn nhập hàng được lưu thành công. Tồn kho được cập nhật. Lịch sử được ghi nhận.                | Lỗi khi lưu đơn nhập vào cơ sở dữ liệu. Không thể cập nhật tồn kho. Lỗi khi tạo phiếu nhập kho. |

### 1.3 XUẤT HÀNG

#### 1.3.1 Thông tin màn hình:

| Screen        | Xuất hàng                                                      |
| ------------- | -------------------------------------------------------------- |
| Description   | Ghi nhận việc xuất sách khi bán (tự động từ hệ thống bán hàng) |
| Screen Access | Nhân viên kho chọn **Xuất hàng** từ menu quản lý tồn kho       |

#### 1.3.2 Chi tiết thành phần màn hình:

| Item                    | Type         | Data                                                                                        | Description                                          |
| ----------------------- | ------------ | ------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| **Tiêu đề trang**       | Text         | Xuất hàng                                                                                   | Tiêu đề chính của trang xuất hàng                    |
| **Thống kê xuất hàng**  | Card Group   | Xuất hôm nay: 45<br>Xuất tuần này: 320<br>Xuất tháng này: 1,250                             | Hiển thị thống kê xuất hàng theo thời gian           |
| **Bộ lọc thời gian**    | Select       | Hôm nay<br>Tuần này<br>Tháng này<br>Tùy chọn                                                | Lọc danh sách xuất hàng theo thời gian               |
| **Khoảng thời gian**    | Date Range   | Từ 2023-11-01 đến 2023-11-30                                                                | Chọn khoảng thời gian tùy chỉnh                      |
| **Danh sách xuất hàng** | Table        | Mã đơn xuất<br>Mã đơn hàng<br>Khách hàng<br>Ngày xuất<br>Số lượng<br>Trạng thái<br>Thao tác | Hiển thị danh sách xuất hàng dưới dạng bảng          |
| **Mã đơn xuất**         | Text + Badge | EXP001                                                                                      | Mã định danh của đơn xuất, kèm theo badge trạng thái |
| **Mã đơn hàng**         | Text         | ORD001                                                                                      | Mã đơn hàng liên kết                                 |
| **Khách hàng**          | Text         | Nguyễn Văn A                                                                                | Tên khách hàng                                       |
| **Ngày xuất**           | Text         | 2023-11-20 14:30                                                                            | Thời gian xuất hàng                                  |
| **Số lượng**            | Text         | 3                                                                                           | Tổng số lượng sách xuất                              |
| **Trạng thái**          | Badge        | Đã xuất<br>Đang xuất<br>Chờ xác nhận                                                        | Trạng thái hiện tại của đơn xuất                     |
| **Thao tác**            | Button Group | Xem chi tiết<br>Xác nhận xuất<br>In phiếu xuất                                              | Các nút chức năng để thao tác trên đơn xuất          |
| **Chi tiết đơn xuất**   | Modal        | Danh sách sách xuất<br>Số lượng từng sách<br>Ghi chú                                        | Modal hiển thị chi tiết đơn xuất hàng                |
| **Phân trang**          | Pagination   | Trang 1/25                                                                                  | Điều hướng giữa các trang                            |

#### 1.3.3 Hành động và xử lý:

| Action Name                 | Description                                                                                                                                                                                                                                                                                                                                   | Success                                                                                                       | Failure                                                                                                       |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| **Xem danh sách xuất hàng** | Hiển thị danh sách các đơn xuất hàng đã được tạo từ hệ thống bán hàng. Bao gồm thông tin về mã đơn xuất, mã đơn hàng liên kết, khách hàng, ngày xuất, số lượng và trạng thái. Cung cấp bộ lọc theo thời gian để xem xuất hàng theo ngày, tuần hoặc tháng. Cho phép xem chi tiết từng đơn xuất hàng. Hiển thị thống kê tổng quan về xuất hàng. | Hiển thị danh sách xuất hàng đầy đủ với đầy đủ thông tin. Bộ lọc hoạt động chính xác. Thống kê hiển thị đúng. | Không thể tải danh sách xuất hàng do lỗi hệ thống. Bộ lọc không hoạt động. Thống kê hiển thị không chính xác. |
| **Xem chi tiết đơn xuất**   | Hiển thị chi tiết đơn xuất hàng được chọn. Bao gồm danh sách sách xuất với số lượng từng sách. Thông tin khách hàng và địa chỉ giao hàng. Ghi chú về đơn xuất. Trạng thái xử lý đơn xuất. Cho phép xác nhận xuất hàng hoặc in phiếu xuất.                                                                                                     | Hiển thị đầy đủ chi tiết đơn xuất hàng. Thông tin sách xuất chính xác.                                        | Không thể tải chi tiết đơn xuất. Thông tin hiển thị không đầy đủ.                                             |
| **Xác nhận xuất hàng**      | Cho phép nhân viên kho xác nhận việc xuất hàng. Cập nhật trạng thái đơn xuất thành "Đã xuất". Giảm số lượng tồn kho cho các sách đã xuất. Ghi nhận lịch sử xuất hàng. Cập nhật trạng thái đơn hàng liên kết. Gửi thông báo cho khách hàng về việc xuất hàng.                                                                                  | Đơn xuất hàng được xác nhận thành công. Tồn kho được cập nhật. Khách hàng được thông báo.                     | Không thể xác nhận xuất hàng do lỗi hệ thống. Không thể cập nhật tồn kho. Lỗi khi gửi thông báo.              |
| **In phiếu xuất**           | Tạo và in phiếu xuất hàng cho đơn xuất được chọn. Bao gồm thông tin đơn xuất, danh sách sách xuất, thông tin khách hàng và thời gian xuất. Định dạng phiếu xuất theo chuẩn của công ty. Cho phép in nhiều bản copy nếu cần. Lưu bản mềm phiếu xuất vào hệ thống.                                                                              | Phiếu xuất hàng được tạo và in thành công. Bản mềm được lưu vào hệ thống.                                     | Không thể tạo phiếu xuất. Lỗi khi in phiếu xuất. Không thể lưu bản mềm.                                       |

### 1.4 KIỂM KÊ KHO

#### 1.4.1 Thông tin màn hình:

| Screen        | Kiểm kê kho                                                                  |
| ------------- | ---------------------------------------------------------------------------- |
| Description   | Thực hiện kiểm đếm số lượng sách thực tế trong kho để đối chiếu với hệ thống |
| Screen Access | Nhân viên kho chọn **Kiểm kê kho** từ menu quản lý tồn kho                   |

#### 1.4.2 Chi tiết thành phần màn hình:

| Item                       | Type           | Data                                                                                  | Description                                           |
| -------------------------- | -------------- | ------------------------------------------------------------------------------------- | ----------------------------------------------------- |
| **Tiêu đề trang**          | Text           | Kiểm kê kho                                                                           | Tiêu đề chính của trang kiểm kê kho                   |
| **Thông tin đợt kiểm kê**  | Form           | Mã đợt kiểm kê<br>Ngày kiểm kê<br>Người thực hiện<br>Ghi chú                          | Form nhập thông tin cơ bản về đợt kiểm kê             |
| **Mã đợt kiểm kê**         | Text           | INV001                                                                                | Mã định danh duy nhất của đợt kiểm kê (tự động tạo)   |
| **Ngày kiểm kê**           | Input (Date)   | 2023-11-20                                                                            | Ngày thực hiện kiểm kê                                |
| **Người thực hiện**        | Text           | Nguyễn Văn A                                                                          | Tên nhân viên thực hiện kiểm kê (tự động điền)        |
| **Ghi chú**                | Textarea       |                                                                                       | Ghi chú về đợt kiểm kê                                |
| **Danh sách sách kiểm kê** | Table          | Mã sách<br>Tên sách<br>Số lượng hệ thống<br>Số lượng thực tế<br>Chênh lệch<br>Ghi chú | Bảng danh sách sách cần kiểm kê                       |
| **Mã sách**                | Text           | BK001                                                                                 | Mã định danh của sách                                 |
| **Tên sách**               | Text           | Đắc Nhân Tâm                                                                          | Tên của cuốn sách                                     |
| **Số lượng hệ thống**      | Text           | 15                                                                                    | Số lượng sách theo hệ thống                           |
| **Số lượng thực tế**       | Input (Number) |                                                                                       | Ô nhập số lượng sách thực tế kiểm đếm được            |
| **Chênh lệch**             | Text + Badge   | +2<br>0<br>-1                                                                         | Hiển thị chênh lệch giữa hệ thống và thực tế          |
| **Ghi chú**                | Textarea       |                                                                                       | Ghi chú về sách kiểm kê                               |
| **Tổng kết kiểm kê**       | Card           | Tổng sách kiểm kê: 1,250<br>Chênh lệch dương: 15<br>Chênh lệch âm: 8                  | Hiển thị tổng kết kết quả kiểm kê                     |
| **Nút bắt đầu kiểm kê**    | Button         |                                                                                       | Nút bắt đầu quá trình kiểm kê                         |
| **Nút lưu kết quả**        | Button         |                                                                                       | Nút lưu kết quả kiểm kê                               |
| **Nút hoàn thành**         | Button         |                                                                                       | Nút hoàn thành đợt kiểm kê                            |
| **Thông báo lỗi**          | Alert          | Vui lòng nhập số lượng thực tế cho tất cả sách                                        | Hiển thị thông báo lỗi khi chưa nhập đầy đủ thông tin |
| **Thông báo thành công**   | Alert          | Kiểm kê kho hoàn thành thành công                                                     | Hiển thị thông báo khi kiểm kê thành công             |

#### 1.4.3 Hành động và xử lý:

| Action Name               | Description                                                                                                                                                                                                                                                                                        | Success                                                                          | Failure                                                                    |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **Bắt đầu kiểm kê kho**   | Cho phép nhân viên kho bắt đầu quá trình kiểm kê kho. Tạo mã đợt kiểm kê duy nhất. Hiển thị danh sách tất cả sách cần kiểm kê với số lượng theo hệ thống. Cho phép nhập số lượng thực tế cho từng sách. Tự động tính chênh lệch giữa hệ thống và thực tế. Hiển thị tổng kết kết quả kiểm kê.       | Đợt kiểm kê được tạo thành công. Danh sách sách được hiển thị đầy đủ.            | Không thể tạo đợt kiểm kê. Lỗi khi tải danh sách sách.                     |
| **Nhập số lượng thực tế** | Cho phép nhân viên kho nhập số lượng sách thực tế kiểm đếm được. Tự động tính chênh lệch giữa số lượng hệ thống và số lượng thực tế. Hiển thị chênh lệch với màu sắc khác nhau (dương: xanh, âm: đỏ, bằng: xám). Cho phép nhập ghi chú cho từng sách. Cập nhật tổng kết kết quả kiểm kê real-time. | Số lượng thực tế được nhập chính xác. Chênh lệch được tính toán đúng.            | Số lượng thực tế không hợp lệ. Lỗi khi tính chênh lệch.                    |
| **Lưu kết quả kiểm kê**   | Lưu kết quả kiểm kê vào cơ sở dữ liệu. Ghi nhận tất cả số lượng thực tế và chênh lệch. Lưu ghi chú cho từng sách. Tạo báo cáo kiểm kê chi tiết. Gửi thông báo cho quản lý về kết quả kiểm kê.                                                                                                      | Kết quả kiểm kê được lưu thành công. Báo cáo được tạo. Quản lý được thông báo.   | Lỗi khi lưu kết quả kiểm kê. Không thể tạo báo cáo. Lỗi khi gửi thông báo. |
| **Hoàn thành kiểm kê**    | Hoàn thành đợt kiểm kê và cập nhật tồn kho theo kết quả thực tế. Cập nhật số lượng tồn kho cho các sách có chênh lệch. Ghi nhận lịch sử điều chỉnh tồn kho. Tạo báo cáo tổng kết đợt kiểm kê. Đóng đợt kiểm kê và không cho phép chỉnh sửa.                                                        | Đợt kiểm kê được hoàn thành thành công. Tồn kho được cập nhật theo thực tế.      | Không thể hoàn thành kiểm kê. Lỗi khi cập nhật tồn kho.                    |
| **Tạo báo cáo kiểm kê**   | Tạo báo cáo chi tiết về kết quả kiểm kê kho. Bao gồm thông tin đợt kiểm kê, danh sách sách có chênh lệch, tổng kết kết quả. Định dạng báo cáo theo chuẩn của công ty. Cho phép xuất báo cáo dưới dạng PDF hoặc Excel. Gửi báo cáo cho quản lý và các bộ phận liên quan.                            | Báo cáo kiểm kê được tạo thành công. Báo cáo được gửi đến các bộ phận liên quan. | Không thể tạo báo cáo. Lỗi khi xuất báo cáo. Lỗi khi gửi báo cáo.          |
