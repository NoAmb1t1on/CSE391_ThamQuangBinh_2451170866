# PBT_03
## Phần A:
### Câu A1 (08_introduction_css.md - 3. ⚙️ Core Technical Truth):
1. Inline CSS: Phương pháp này sử dụng thuộc tính style ngay bên trong thẻ mở của phần tử HTML.
    - VÍ dụ:

          <h1 style="color: blue; font-size: 20px;">Chào mừng bạn!</h1>
    - Uư điểm: Nhanh chóng, có độ ưu tiên cao nhất, hữu ích khi muốn kiểm tra nhanh một thuộc tính hoặc thay đổi duy nhất một phần tử cụ thể mà không làm ảnh hưởng đến các phần tử khác.
    - Nhược điểm: Khó bảo trì, làm mã HTML trở nên lộn xộn, không thể tái sử dụng mã CSS cho các phần tử khác.
    - Nên dùng khi: cần ghi đè khẩn cấp.
2. Internal CSS: Phương pháp này đặt các quy tắc CSS bên trong thẻ `<style>`, thường nằm trong phần `<head>` của tệp HTML.
    - Ví dụ:

           <head>
              <style>
                p {
                  color: red;
                  line-height: 1.5;
                }
              </style>
            </head>

    - Ưu điểm: Tất cả CSS cho một trang nằm tập trung tại một chỗ, không cần tạo thêm tệp tin mới, dễ dàng quản lý kiểu dáng cho một trang đơn lẻ.
    - Nhược điểm: Chỉ áp dụng được cho trang hiện tại, nếu website có nhiều trang sẽ dẫn đến việc lặp lại code, làm tăng kích thước tệp HTML.
    - Khi nào nên dùng: Dùng cho các trang web đơn hoặc khi bạn chỉ muốn định dạng riêng biệt cho một trang duy nhất mà không muốn ảnh hưởng đến toàn bộ hệ thống.
3. External CSS: Đây là cách phổ biến nhất, sử dụng một tệp tin `.css` riêng biệt và liên kết vào HTML thông qua thẻ `<link>`.
    - Ví dụ:

          <head>
                <link rel="stylesheet" href="style.css">
              </head>
          
              /* Trong tệp style.css */
              body {
                background-color: #f0f0f0;
              }
### Câu A2 (09_css_selectors.md - 3. ⚙️ Core Technical Truth):
1. h1 -> Chọn: ShopTLU
2. .price -> Chọn: 25.990.000đ và 45.990.000đ
3. #app header -> Chọn: Toàn bộ nội dung bên trong thẻ `<header>`.
4. nav a:first-child: -> Chọn: `Home`.
5. .product.featured h2 -> Chọn: `MacBook Pro`.
6. article > p -> Chọn:
      - 25.990.000đ và Mô tả sản phẩm... (của iPhone 16).
      - 45.990.000đ và Mô tả sản phẩm... (của MacBook Pro).
7. a[href="/"] -> Chọn: `Home`.
8. .top-bar.dark h1 -> Chọn: `ShopTLU`. 

### Câu A3 (11_box_model.md - 3. ⚙️ Core Technical Truth):
- Trường hợp 1: content-box(Mặc định)
  - Chiều rộng hiển thị: width + padding-left + padding-right + border-left + border-right = 450px.
  - Không gian chiếm trên trang: Chiều rộng hiển thị + margin-left + margin-right = 470px.
- Trường hợp 2: border-box
  - Chiều rộng hiển thị: 400px.
  - Kích thước content thực tế: width - (padding + border) = 350px.
  - Không gian chiếm trên trang: width + margin-left + margin-right = 420px.
- Trường hợp 3: Margin collapse
  - Khoảng cách giữa box-a và box-b: 40px.
  - Đây là hiện tượng Margin Collapse trong CSS. Khi hai lề dọc của hai khối tiếp xúc với nhau, chúng không cộng dồn lại mà sẽ "nhập" vào nhau.
    - Trình duyệt sẽ so sánh hai giá trị lề và giữ lại giá trị lớn nhất.
    - Trong trường hợp này: $Max(25px, 40px) = 40px$.
### Câu A4 (09_css_selectors.md - 3. ⚙️ Core Technical Truth):
1. Specificity Score:
    | **Rule** | **Selector** | **A** | **B** | **C** | **Score** |
    |---|---|---|---|---|---|
    | Rule A | `P` | 0 | 0 | 1 | (0,0,1) |
    | Rule B | `.price` | 0 | 1 | 0 | (0,1,0) |
    | Rule C | `#main-price` | 1 | 0 | 0 | (1,0,0) |
    | Rule D | `p.price` | 0 | 1 | 1 | (0,1,1) |
2. Element hiển thị màu Đỏ. Vì Trình duyệt so sánh các trọng số từ trái sang phải. Rule C có 1 ID $(1, 0, 0)$, đây là trọng số cao nhất so với các Rule còn lại (chỉ có Class hoặc Element). Dù Rule D có cả Element và Class cộng lại $(0, 1, 1)$, nó vẫn "thua" hoàn toàn trước 1 ID.
3. Nếu thêm `<p class="price" id="main-price" style="color: orange;">`, element có màu Cam.
4. Nếu Rule A thêm `!important`, element có màu Đen. Vì `!important` không phải là một phần của Specificity nhưng nó là một "lệnh cưỡng chế" phá vỡ mọi quy tắc Cascade thông thường. Nó sẽ ghi đè lên cả ID và cả Inline Style.
---
## Phần C:
### Câu C1:
1. Theo mặc định, trình duyệt sử dụng box-sizing: content-box. Kích thước thực tế sẽ được tính theo công thức:

        Total Width = width + padding-left + padding-right + border-left + border-right

    - SideBar: 300px(width) + 40px(padding) + 2px(border) = 342px
    - Content: 660px(width) + 60px(padding) + 2px(border) = 722px
3. layout bị vỡ vì tổng chiều rộng thực tế của hai khối là: 342px + 722px =1064px. Trong khi đó, Container của bạn chỉ rộng 960px. Vì 1064px > 960px, không gian không đủ để hai khối nằm cùng một hàng, nên theo cơ chế của float, khối thứ hai (.content) sẽ bị đẩy xuống dòng mới.
4. Sửa:
    - Cách 1: Sử dụng `border-box`: Đặt box-sizing: border-box. Lúc này 300px + 660px = 960px (vừa khít).
    - Cách 2: không dùng `border-box`(tính toán lại width thủ công): Trừ đi phần padding và border khỏi giá trị width để tổng cuối cùng đạt đúng con số mong muốn:
        - Content width: 660 - 60 - 2 = 598px.
        - Sidebar width: 300 - 40 - 2 = 258px.
### Câu C2:
1. "Sản phẩm A" (h2) có `font-size = 20px` và `color = green`.Quá trình
    - font-size: Selector `.card` `.title` có độ ưu tiên (0, 2, 0) trực tiếp nhắm vào phần tử này, giá trị là 20px.
    - color:
        - featured .title có độ ưu tiên (1, 1, 0) muốn màu red.
        - `.highlight` có độ ưu tiên thấp hơn (0, 1, 0) nhưng lại có `!important`.
        - Kết quả: `!important` phá vỡ mọi quy tắc Specificity thông thường, màu green thắng.
2. "Mô tả sản phẩm" (p trong card featured) có `color = blue`. Quá trình:
    - color:
        - Selector `.card p` (0, 1, 1) áp dụng giá trị inherit.
        - Nó sẽ ép thẻ p lấy màu từ cha trực tiếp của nó là `.card (có màu blue)`.
        - Kết quả: Màu blue.
3. "Sản phẩm B" (h2) có `font-size = 20px` và `color = blue`. Quá trình:
    - font-size: Giống sản phẩm A, selector .card .title (0, 2, 0) áp dụng giá trị 20px.
    - color:
        - Không có selector nào trực tiếp quy định màu cho h2 này (ngo trừ `.highlight` không có ở đây).
        - Nó sẽ thừa kế màu từ cha trực tiếp là `.card (color: blue)`.
        - Kết quả: Màu blue.
4. "Mô tả sản phẩm B" (p.highlight) có `color = green`. Quá trình:
    - color:
        - `.card` p (0, 1, 1) yêu cầu inherit (lấy màu blue từ cha).
        - `.highlight` (0, 1, 0) yêu cầu màu green kèm theo `!important`.
        - Kết quả: `!important` thắng, màu green.
---
## Phần B:
### Câu B2:
- Hộp 1 (content-box): chiều rộng thực tế = 348.73px.
- Hộp 2 (border-box): chiều rộng thực tế = 300px.
- Giải thích sự khác biệt:
    - Với content-box, thuộc tính width chỉ định nghĩa kích thước của vùng chứa nội dung (content). Mọi giá trị padding và border sẽ được cộng dồn vào bên ngoài khiến hộp phình to ra.
    - Với border-box, trình duyệt sẽ ép toàn bộ nội dung, padding và border nằm gọn trong con số width đã định sẵn. Nếu bạn tăng padding, phần content sẽ tự động thu nhỏ lại để tổng kích thước không đổi.
### Câu B3:
1. 10 rule + specificity score:

| **Selector** | **Specificity Score (a, b, c)** | **Color** |
|---|---|---|
| p | (0, 0, 1) | Gray |
| .text | (0, 1, 0) | Silver |
| p[class*="text"] | (0, 1, 1) | Lime |
| .text.highlight | (0, 2, 0) | Pink |
| p.text.highlight | (0, 2, 1) | Brown |
| #demo | (1, 0, 0) | Blue |
| p#demo | (1, 0, 1) | Purple |
| #demo.text | (1, 1, 0) | Orange |
| #demo.text.highlight | (1, 2, 0) | Cyan |
| .highlight { color: red !important; } | Phá vỡ thang điểm | Red |

2. Element cuối cùng hiển thị màu Đỏ. Vì mặc dù quy tắc số 9 có điểm Specificity rất cao (1, 2, 0), nhưng quy tắc số 10 sử dụng từ khóa `!important`. Trong CSS Cascade, `!important` là một lệnh cưỡng chế có quyền ưu tiên cao hơn bất kỳ Selector ID hay Class nào. Nếu bỏ `!important`, màu hiển thị sẽ là Cyan (quy tắc số 9) vì nó có điểm Specificity cao nhất.
4. Thay đổi thứ tự rules trong CSS file kết quả không đổi. Vì trình duyệt luôn ưu tiên quy tắc có Specificity cao hơn bất kể nó nằm ở vị trí nào trong file CSS. Thứ tự viết code chỉ có tác dụng khi hai Selector có cùng điểm Specificity.
