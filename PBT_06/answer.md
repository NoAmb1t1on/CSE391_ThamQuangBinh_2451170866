# PBT_06:
---
## TRACK A - BOOTSTRAP 5
### Phần A:
#### Câu A1(tuan_4_css_frameworks - bootstrap - 02_grid_system - 3. Cú pháp cơ bản):

| Kích thước | Số cột | Box layout|
|------------|--------|-----------|
| <768px | 1 cột | 4 hàng (Box 1-4 xếp dọc) |
| 768px - 991px | 2 cột | 2 hàng (Mỗi hàng 2 box) |
| ≥992px | 4 cột | 1 hàng (4 box nằm ngang) |

#### Câu A2(tuan_4_css_frameworks - bootstrap - 04_utilities - 3. Display, Spacing):
1. Giải thích `d-none d-md-block`:
    - `d-none`: Ẩn element trên mọi màn hình (display: none).
    - `d-md-block`: Hiện element dạng block từ kích thước màn hình md (≥ 768px) trở lên.
    - Kết luận: Element này chỉ hiển thị trên tablet và desktop, ẩn trên mobile.
2. 5 Spacing utilities:
    - `mt-3`: Margin-top: 1rem (16px).
    - `px-4`: Padding-left và Padding-right: 1.5rem (24px).
    - `mb-auto`: Margin-bottom: auto (đẩy element lên trên).
    - `p-5`: Padding 3rem (48px) cho cả 4 phía.
    - `ms-2`: Margin-start (trái): 0.5rem (8px).
3. Sự khác nhau về Container:
    - `.container`: Có `max-width` thay đổi theo từng breakpoint, tự động căn giữa.
    - `.container-fluid`: Luôn `full-width` (100% màn hình) ở mọi kích thước.
    - `.container-md`: `Full0-width` dưới `md` (< 768px), từ `md` trở lên sẽ có `max-width` cố định.
### Phần C:
#### Câu C1:
1. Để đổi màu `$primary` từ xanh mặc định sang `#E63946`, bạn không nên can thiệp trực tiếp vào file CSS đã biên dịch (`bootstrap.min.css`). Thay vào đó, quy trình chuẩn là sử dụng SASS (SCSS).
    - Quy trình:
      - Công cụ cần thiết: * Node.js (để cài đặt gói Bootstrap).
      - Trình biên dịch SASS (thường tích hợp trong các build tool như Vite, Webpack hoặc Gulp).
      - File cần modify:
        - Tạo một file SCSS riêng (ví dụ: `custom.scss`).
        - Trong file `custom.scss`, bạn khai báo lại giá trị biến trước khi import file Bootstrap:
          ```scss
          $primary: #E63946; 
          @import "node_modules/bootstrap/scss/bootstrap";
          ```
          - Sử dụng file `custom.scss` này thay cho file CSS mặc định.
2. Không nên override trực tiếp (`.btn-primary { background: red; }`) vì:
  - Khả năng bảo trì: Khi bạn update phiên bản Bootstrap, các ghi đè thủ công có thể bị lỗi hoặc xung đột. Dùng SASS giúp biến đổi toàn bộ hệ thống (buttons, links, badges, alerts) sử dụng màu primary một cách đồng bộ.
  - Tính kế thừa: Khi thay đổi biến $primary, Bootstrap tự động tính toán các màu sắc liên quan (như màu hover, màu active, màu chữ tương phản) để đảm bảo tính thẩm mỹ và dễ đọc. Việc viết CSS thủ công khiến bạn mất đi sự hỗ trợ thông minh này.
#### Câu C2:
