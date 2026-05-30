# PBT_04:
---
## Phần A:
### Câu A1(12_css_positioning - 3. ⚙️ Core Technical Truth):
| Position | Vẫn chiếm chỗ trong flow? | Tham chiếu vị trí | Cuộn theo trang? | Use case |
|----------|---------------------------|-------------------|------------------|----------|
| `static` | Có | Theo luồng tài liệu tự nhiên (Normal flow) | Có | Là giá trị mặc định cho mọi phần tử, dùng khi muốn reset lại định vị |
| `relative` | Có (Vẫn giữ nguyên khoảng trống ban đầu) | Chính vị trí gốc ban đầu của nó | Có | Làm điểm tựa (gốc tọa độ) cho các phần tử con dùng absolute, hoặc dịch chuyển nhẹ mà không làm vỡ layout xung quanh |
| `absolute` | Không (Bị tách khỏi normal flow) | Phần tử tổ tiên gần nhất có định vị | Có | Làm các thành phần đè lên nhau như: dropdown menu, icon thông báo trên góc avatar, nút close của modal |
| `fixed` | Không (Bị tách khỏi normal flow) | Cửa sổ trình duyệt | Không (Đứng yên khi cuộn trang) | Thanh điều hướng (Navbar) luôn dính ở đỉnh màn hình, nút "Back to top", hoặc cửa sổ chat hỗ trợ trực tuyến |
| `sticky` | Có (Khi ở trạng thái bình thường) | Cuộn theo flow cho đến khi chạm ngưỡng xác định (bởi top, bottom,...) thì tham chiếu theo viewport | đến khi chạm ngưỡng xác định (bởi top, bottom,...) thì tham chiếu theo viewport.	Có (Nhưng sẽ dính lại tại một vị trí khi cuộn qua) | Tiêu đề danh mục trong danh sách dài, hoặc thanh sidebar cuốn theo màn hình nhưng dừng lại khi hết container |

- `absolute` tham chiếu `body` khi:
  - `absolute` sẽ tham chiếu đến `body` (chính xác hơn là thẻ `<html> - viewport` ban đầu) khi tất cả các phần tử cha, ông, tổ tiên bao bọc bên ngoài nó đều có `position: static` (mặc định).
  - `absolute` sẽ tham chiếu đến `parent` (hoặc một tổ tiên bất kỳ) khi phần tử đó được thiết lập một giá trị position khác với `static` (thường dùng nhất là `position: relative`).
- Khái niệm "nearest positioned ancestor": là "phần tử tổ tiên gần nhất có định vị". Khi bạn duyệt ngược từ phần tử hiện tại lên các cấp cha, ông, cố, cụ... phần tử đầu tiên nào mà bạn gặp có thuộc tính `position` mang giá trị khác `static` (như `relative, absolute, fixed, sticky`) thì đó chính là gốc tọa độ để tính toán các khoảng cách top, bottom, left, right cho phần tử `absolute`.

### Câu A2(13_creating_responsive_layouts - 3. ⚙️ Core Technical Truth):
- Trường hợp 1:
  - Dự đoán layout: 4 items sẽ nằm trên cùng 1 hàng ngang. Do có thuộc tính flex: 1, không gian hàng ngang của `.container` sẽ được chia đều 4 phần bằng nhau cho cả 4 items.
  - Sơ đồ bố cục:

        +-----------------------------------------------------------+
        |                      .container (Flex)                    |
        | +------------+ +------------+ +------------+ +------------+ |
        | |   Item 1   | |   Item 2   | |   Item 3   | |   Item 4   | |
        | | (Width 25%)| | (Width 25%)| | (Width 25%)| | (Width 25%)| |
        | +------------+ +------------+ +------------+ +------------+ |
        +-----------------------------------------------------------+
- Trường hợp 2:
  - Dự đoán layout: Bố cục gồm 3 hàng, mỗi hàng 2 cột. Do mỗi item chiếm 45% chiều rộng và margin: 2.5% cho cả 4 phía (tổng chiều rộng ngang một item chiếm là $2.5% + 45% + 2.5% = 50%$). Một hàng ngang (100%) vừa đủ chứa đúng 2 items. Vì có `flex-wrap: wrap`, 6 items sẽ tự động ngắt dòng đều đặn thành 3 hàng.
  - Sơ đồ bố cục:

        +-----------------------------------------------------------+
        |                 .container (Flex - Wrap)                  |
        |  +-----------------------+     +-----------------------+  |
        |  |        Item 1         |     |        Item 2         |  |
        |  +-----------------------+     +-----------------------+  |
        |  +-----------------------+     +-----------------------+  |
        |  |        Item 3         |     |        Item 4         |  |
        |  +-----------------------+     +-----------------------+  |
        |  +-----------------------+     +-----------------------+  |
        |  |        Item 5         |     |        Item 6         |  |
        |  +-----------------------+     +-----------------------+  |
        +-----------------------------------------------------------+
- Trường hợp 3:
  - Dự đoán layout: 3 items nằm trên 1 hàng ngang. Thẻ `.container` căn giữa các item theo trục dọc (`align-items: center`). Theo trục ngang (`justify-space-between`), Item 1 dính sát lề trái, Item 3 dính sát lề phải, và Item 2 nằm chính giữa khoảng trống của dòng.
  - Sơ đồ bố cục:

        +-----------------------------------------------------------+
        |                     .container (Grid)                     |
        | <- 200px ->   <20px>    <----- 1fr ----->   <20px>   <- 200px -> |
        | +----------+            +---------------+            +----------+ |
        | |  Item 1  |            |     Item 2    |            |  Item 3  | |
        | +----------+            +---------------+            +----------+ |
        +-----------------------------------------------------------+
- Trường hợp 4:
  - Dự đoán layout: Bố cục 1 hàng, 3 cột. Cột đầu tiên cố định 200px, cột thứ ba cố định 200px. Cột thứ hai ở giữa sử dụng đơn vị 1fr nên sẽ tự động giãn nở chiếm trọn toàn bộ không gian còn lại ở giữa. Giữa các cột có một khoảng cách (gap) là 20px.
  - Sơ đồ bố cục:

        +-----------------------------------------------------------+
        |                     .container (Grid)                     |
        | <- 200px ->   <20px>    <----- 1fr ----->   <20px>   <- 200px -> |
        | +----------+            +---------------+            +----------+ |
        | |  Item 1  |            |     Item 2    |            |  Item 3  | |
        | +----------+            +---------------+            +----------+ |
        +-----------------------------------------------------------+
- Trường hợp 5:
  - Dự đoán layout: Bố cục chia đều làm 3 cột bằng nhau (repeat(3, 1fr)). Tổng cộng có 7 items nên hệ thống sẽ tự chia thành 3 hàng.
    - Hàng 1: chứa Item 1, Item 2, Item 3.
    - Hàng 2: chứa Item 4, Item 5, Item 6.
    - Hàng 3: Chỉ chứa duy nhất Item 7 nằm ở cột đầu tiên bên trái, bỏ trống hoàn toàn vị trí của cột 2 và cột 3. Khoảng cách giữa các ô là 10px.
  - Sơ đồ bố cục:

        +-----------------------------------------------------------+
        |                 .container (Grid - 3 Columns)             |
        | +---------------+   +---------------+   +---------------+ |
        | |    Item 1     |   |    Item 2     |   |    Item 3     | |
        | +---------------+   +---------------+   +---------------+ |
        |       gap                   gap                 gap       |
        | +---------------+   +---------------+   +---------------+ |
        | |    Item 4     |   |    Item 5     |   |    Item 6     | |
        | +---------------+   +---------------+   +---------------+ |
        |       gap                   gap                 gap       |
        | +---------------+                                         |
        | |    Item 7     |        (Ô Cột 2 và Cột 3 trống)         |
        | +---------------+                                         |
        +-----------------------------------------------------------+
---
## Phần C:
### Câu C1:
