# PBT_01
# Phiếu Bài Tập CHương 1
## Phần A
---
### Câu A1
1. Các bước của tiến trình:
   - Bước 1(Dns Lookup): Trình duyệt kiểm tra cache đệm của chính nó, của hệ điều hành, rounter và của máy chủ rồi gửi yêu cầu đến máy chủ DNS của nhà cung cấp dịch vụ Internet.
   - Bước 2(TCP): Sau khi có địa chỉ IP, trình duyệt cần thiết lập một "đường truyền" để trao đổi dữ liệu với máy chủ Shopee.
   - Bước 3(TLS/SSL): Vì sử dụng giao thức https (có chữ 's' - secure), trình duyệt và máy chủ phải thiết lập một kết nối mã hóa để bảo mật thông tin (như mật khẩu, số thẻ tín dụng).
   - Bước 4(HTTP Request):Sau khi đường truyền bảo mật đã sẵn sàng, trình duyệt sẽ gửi một yêu cầu HTTP (thường là phương thức GET) đến máy chủ Shopee.
   - Bước 5(HTTP Response & Rendering):
     + Response: Máy chủ Shopee gửi về mã phản hồi kèm theo dữ liệu thô của trang web (thường là các tệp HTML, CSS, JavaScript).
     + Render: Phân tích mã HTML để tạo cấu trúc trang -> Phân tích các tệp CSS để biết màu sắc, font chữ, bố cục -> trình duyệt vẽ các điểm ảnh lên màn hình để bạn thấy giao diện Shopee hoàn chỉnh.

2. Trong devtools, tab Network cho thấy:
    + Name: Tên của yêu cầu.
    + Status: Kết quả của yêu cầu.
    + Type: Phân loại đó là HTML (document), CSS (stylesheet), JavaScript (script) hay hình ảnh.
    + Size : File nặng bao nhiêu. File càng nặng thì thời gian chạy qua cáp quang càng lâu.
    + Time : Tổng số mili giây để hoàn thành việc gửi yêu cầu và nhận phản hồi.
    + Waterfall: Biểu đồ thời gian cho thấy file nào được tải trước, file nào tải sau và có bị nghẽn ở đâu không.

<img width="1439" height="517" alt="Screenshot 2026-04-22 114141" src="https://github.com/user-attachments/assets/b09518b5-2c9e-4839-baad-fe0d739ab5c2" />

    + Màu đỏ: Mã status của request đầu tiên.
    + Màu xanh dương: tổng thời gian load trang.
    + Màu xanh lá: request trả về file CSS.
---
### Câu A2
**Các lỗi trong đoạn code:**
1. Thay vì dùng `<div>` để chia ô sẽ khiến google không hiểu bố cục thì nên thay bằng các thẻ `<head>,<main>,<footer>`.
2. Thanh menu dùng các thẻ `<div>` lồng nhau. Máy tìm kiếm sẽ không hiểu đây là một danh sách các liên kết điều hướng quan trọng của trang, thay vào đó sử dụng thẻ `<nav>` bao quanh một danh sách không thứ tự `<ul>` và các mục `<li>`.
3. Tên sản phẩm được đặt trong `<div class="title">`. Google sẽ không biết đây là từ khóa chính của trang này, nên sử dụng các thẻ từ `<h1>` đến `<h6>`. Tên sản phẩm chính nên nằm trong thẻ `<h1>` hoặc `<h2>`.
4. Thẻ `<img>` của bạn không có thuộc tính alt. Nếu ảnh không load được hoặc đối với người dùng sử dụng trình đọc màn hình, họ sẽ không biết ảnh đó là gì. Đây là một điểm trừ lớn về khả năng tiếp cận (Accessibility) và SEO alt="iPhone 16 Pro màu Titan" vào thẻ ảnh.
**Phần code đã sửa:**
```html
<header>
    <div class="logo">ShopTLU</div>
    <nav>
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/products">Sản phẩm</a></li>
        </ul>
    </nav>
</header>

<main>
    <article class="product">
        <h2>iPhone 16 Pro</h2>
        <p class="price">25.990.000đ</p>
        <figure class="image">
            <img src="iphone.jpg" alt="Điện thoại iPhone 16 Pro chính hãng">
        </figure>
    </article>
</main>

<footer>
    <p>© 2026 ShopTLU</p>
</footer>
```
---
### Câu A3:
<img width="2560" height="1184" alt="image" src="https://github.com/user-attachments/assets/cd289d73-9682-4f32-8ccf-33244ad4473f" />

Kết quả này được quyết định bởi thuộc tính display mặc định của các thẻ:
  - Thẻ Block `<div>`: Luôn bắt đầu trên một dòng mới và chiếm trọn bộ chiều ngang của trình duyệt. Do đó, "Hộp 1", "Hộp 2" và "Hộp 3" nằm riêng biệt trên từng dòng.
  - Thẻ Inline `<span>, <strong>`: Chỉ chiếm không gian vừa đủ với nội dung của nó và không tạo dòng mới, thẻ `<strong>` để in đậm chữ.
  - Text A và Text B là thẻ inline đứng cạnh nhau nên chúng nằm trên cùng một dòng ngay sau "Hộp 1".
  - Text C và Text D cũng là inline nên nằm cùng nhau trên một dòng sau "Hộp 2".

---
### Câu A4:
1. Sự khác nhau:
    - `<thead>`: Dùng để chứa các tiêu đề cột (thường nằm ở hàng đầu tiên), giúp người dùng và máy tìm kiếm biết được các cột đang nói về chủ đề gì.
    - `<tbody>`: hứa toàn bộ dữ liệu thực tế của danh sách. Một bảng có thể có nhiều hàng dữ liệu trong phần này.
    - `<tfoot>`: Dùng để tóm tắt dữ liệu bên trên (thường nằm ở hàng cuối cùng). Được dùng để hiển thị tổng cộng, trung bình cộng hoặc các ghi chú cuối bảng.
2. Lý do không nên dùng table để tạo layout cho trang web:
    - Table chỉ dành cho dữ liệu (như bảng giá), không phải để chia khung trang web. Máy tìm kiếm và trình đọc màn hình sẽ không hiểu được bố cục.
    - Table rất cứng nhắc, khó hiển thị đẹp trên điện thoại so với Flexbox hay CSS Grid.
    - Code table phức tạp làm chậm tốc độ render của trình duyệt và bị Google đánh giá thấp về cấu trúc.

---

# PBT_01
# Phiếu Bài Tập CHương 1
## Phần A
---
### Câu A1
1. Các bước của tiến trình:
   - Bước 1(Dns Lookup): Trình duyệt kiểm tra cache đệm của chính nó, của hệ điều hành, rounter và của máy chủ rồi gửi yêu cầu đến máy chủ DNS của nhà cung cấp dịch vụ Internet.
   - Bước 2(TCP): Sau khi có địa chỉ IP, trình duyệt cần thiết lập một "đường truyền" để trao đổi dữ liệu với máy chủ Shopee.
   - Bước 3(TLS/SSL): Vì sử dụng giao thức https (có chữ 's' - secure), trình duyệt và máy chủ phải thiết lập một kết nối mã hóa để bảo mật thông tin (như mật khẩu, số thẻ tín dụng).
   - Bước 4(HTTP Request):Sau khi đường truyền bảo mật đã sẵn sàng, trình duyệt sẽ gửi một yêu cầu HTTP (thường là phương thức GET) đến máy chủ Shopee.
   - Bước 5(HTTP Response & Rendering):
     + Response: Máy chủ Shopee gửi về mã phản hồi kèm theo dữ liệu thô của trang web (thường là các tệp HTML, CSS, JavaScript).
     + Render: Phân tích mã HTML để tạo cấu trúc trang -> Phân tích các tệp CSS để biết màu sắc, font chữ, bố cục -> trình duyệt vẽ các điểm ảnh lên màn hình để bạn thấy giao diện Shopee hoàn chỉnh.

2. Trong devtools, tab Network cho thấy:
    + Name: Tên của yêu cầu.
    + Status: Kết quả của yêu cầu.
    + Type: Phân loại đó là HTML (document), CSS (stylesheet), JavaScript (script) hay hình ảnh.
    + Size : File nặng bao nhiêu. File càng nặng thì thời gian chạy qua cáp quang càng lâu.
    + Time : Tổng số mili giây để hoàn thành việc gửi yêu cầu và nhận phản hồi.
    + Waterfall: Biểu đồ thời gian cho thấy file nào được tải trước, file nào tải sau và có bị nghẽn ở đâu không.

<img width="1439" height="517" alt="Screenshot 2026-04-22 114141" src="https://github.com/user-attachments/assets/b09518b5-2c9e-4839-baad-fe0d739ab5c2" />

    + Màu đỏ: Mã status của request đầu tiên.
    + Màu xanh dương: tổng thời gian load trang.
    + Màu xanh lá: request trả về file CSS.
---
### Câu A2
**Các lỗi trong đoạn code:**
1. Thay vì dùng `<div>` để chia ô sẽ khiến google không hiểu bố cục thì nên thay bằng các thẻ `<head>,<main>,<footer>`.
2. Thanh menu dùng các thẻ `<div>` lồng nhau. Máy tìm kiếm sẽ không hiểu đây là một danh sách các liên kết điều hướng quan trọng của trang, thay vào đó sử dụng thẻ `<nav>` bao quanh một danh sách không thứ tự `<ul>` và các mục `<li>`.
3. Tên sản phẩm được đặt trong `<div class="title">`. Google sẽ không biết đây là từ khóa chính của trang này, nên sử dụng các thẻ từ `<h1>` đến `<h6>`. Tên sản phẩm chính nên nằm trong thẻ `<h1>` hoặc `<h2>`.
4. Thẻ `<img>` của bạn không có thuộc tính alt. Nếu ảnh không load được hoặc đối với người dùng sử dụng trình đọc màn hình, họ sẽ không biết ảnh đó là gì. Đây là một điểm trừ lớn về khả năng tiếp cận (Accessibility) và SEO alt="iPhone 16 Pro màu Titan" vào thẻ ảnh.
**Phần code đã sửa:**
```html
<header>
    <div class="logo">ShopTLU</div>
    <nav>
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/products">Sản phẩm</a></li>
        </ul>
    </nav>
</header>

<main>
    <article class="product">
        <h2>iPhone 16 Pro</h2>
        <p class="price">25.990.000đ</p>
        <figure class="image">
            <img src="iphone.jpg" alt="Điện thoại iPhone 16 Pro chính hãng">
        </figure>
    </article>
</main>

<footer>
    <p>© 2026 ShopTLU</p>
</footer>
```
---
### Câu A3:
<img width="2560" height="1184" alt="image" src="https://github.com/user-attachments/assets/cd289d73-9682-4f32-8ccf-33244ad4473f" />

Kết quả này được quyết định bởi thuộc tính display mặc định của các thẻ:
  - Thẻ Block `<div>`: Luôn bắt đầu trên một dòng mới và chiếm trọn bộ chiều ngang của trình duyệt. Do đó, "Hộp 1", "Hộp 2" và "Hộp 3" nằm riêng biệt trên từng dòng.
  - Thẻ Inline `<span>, <strong>`: Chỉ chiếm không gian vừa đủ với nội dung của nó và không tạo dòng mới, thẻ `<strong>` để in đậm chữ.
  - Text A và Text B là thẻ inline đứng cạnh nhau nên chúng nằm trên cùng một dòng ngay sau "Hộp 1".
  - Text C và Text D cũng là inline nên nằm cùng nhau trên một dòng sau "Hộp 2".

---
### Câu A4:
1. Sự khác nhau:
    - `<thead>`: Dùng để chứa các tiêu đề cột (thường nằm ở hàng đầu tiên), giúp người dùng và máy tìm kiếm biết được các cột đang nói về chủ đề gì.
    - `<tbody>`: hứa toàn bộ dữ liệu thực tế của danh sách. Một bảng có thể có nhiều hàng dữ liệu trong phần này.
    - `<tfoot>`: Dùng để tóm tắt dữ liệu bên trên (thường nằm ở hàng cuối cùng). Được dùng để hiển thị tổng cộng, trung bình cộng hoặc các ghi chú cuối bảng.
2. Lý do không nên dùng table để tạo layout cho trang web:
    - Table chỉ dành cho dữ liệu (như bảng giá), không phải để chia khung trang web. Máy tìm kiếm và trình đọc màn hình sẽ không hiểu được bố cục.
    - Table rất cứng nhắc, khó hiển thị đẹp trên điện thoại so với Flexbox hay CSS Grid.
    - Code table phức tạp làm chậm tốc độ render của trình duyệt và bị Google đánh giá thấp về cấu trúc.

---
## Phần C
### Câu C1:
```html
<head>
    <meta charset="UTF-8">
    <title>Trang Chi Tiết Sản Phẩm</title>
</head>
<body>
    <header> <!-- thẻ tiêu đề --> 
        <nav aria-label="breadcrumb"> <!-- chứa link điều hướng -->
            <div class="breadcrumb"> <!-- tạo khối chứa nội dung bên trong, phân bố giao diện -->
                <a href="https://shopee.vn/">Trang chủ</a>
                <span> > </span> <!-- hiển thị kí hiệu nhưng không xuống dòng -->
                <a href="https://shopee.vn/%C4%90i%E1%BB%87n-Tho%E1%BA%A1i-Ph%E1%BB%A5-Ki%E1%BB%87n-cat.11036030">Điện Thoại</a>
                <span> > </span>
                <a href="https://shopee.vn/search?keyword=iphone%2016">Iphone 16</a>
            </div>
        </nav>
    </header>
    
    <hr> <!-- kẻ ngang ngăn cách hộp -->

    <main> <!-- thẻ nội dung chính -->
        
        <div class="Pics">
        <img src="Iphone16_1.png" alt="iphone 16's screen" width="100"> <!-- để chèn ảnh -->
        </div>
        <div class="Pics">
        <img src="Iphone16_2.png" alt="iphone 16's back" width="100">
        </div>
        <div class="Pics">
        <img src="Iphone16_3.png" alt="iphone 16's left/right sides" width="100">
        </div>
        <div class="Pics">
        <img src="Iphone16_4.png" alt="iphone 16's top/bottom sides" width="100">
        </div>
        <div class="Pics">
        <img src="Iphone16_5.png" alt="backs of 5 iphone 16 with 5 different colors" width="150">
        </div>

        <div class="product_in4">
            <h4>Thông tin sản phẩm</h4> <!-- headline cỡ chữ to thứ 4 -->
            <ul> <!-- danh sách không đánh số thứ tự -->
                <li>Tên: Iphone 16/Iphone16Plus/Iphone16Pro/16ProMax</li> <!-- thành phần trong danh sách -->
                <li>Giá: 20.000.000/21.000.000/22.000.000/24.000.000 VNĐ</li>
                <li>Đánh giá sao: 3,8/5</li>
                <li>Mô tả: *Mô tả*</li>
            </ul>
        </div>

        <div class="product_technical_in4">
            <h4>Bảng thông số kỹ thuật</h4>
            <table border="1" width="1000"> <!-- tạo bảng thông số kỹ thuật -->
                <colgroup> <!-- gộp cột theo nhóm để chỉnh sửa chung -->
                    <col width="120"> <!-- chỉnh sửa thông số của từng cột-->
                    <col width="120">
                    <col width="120">
                    <col width="120">
                    <col width="120">
                </colgroup>
                <tr> <!-- hàng ngang của bảng -->
                    <td style="text-align: center;"><strong>Tiêu chí</strong></td> <!-- ô chưa dữ liệu -->
                    <td style="text-align: center;">Iphone 16</td>
                    <td style="text-align: center;">Iphone 16 Plus</td>
                    <td style="text-align: center;">Iphone 16 Pro</td>
                    <td style="text-align: center;">Iphone 16 ProMax</td>
                </tr>
                <tr>
                    <td style="text-align: center;">Tiêu chí 1</td>
                    <td style="text-align: center;">a</td>
                    <td style="text-align: center;">b</td>
                    <td style="text-align: center;">c</td>
                    <td style="text-align: center;">d</td>
                </tr>
                <tr>
                    <td style="text-align: center;">Tiêu chí 2</td>
                    <td style="text-align: center;" colspan="4">e</td>
                </tr>
                <tr>
                    <td style="text-align: center;">Tiêu chí 3</td>
                    <td style="text-align: center;">a</td>
                    <td style="text-align: center;">b</td>
                    <td style="text-align: center;">c</td>
                    <td style="text-align: center;">d</td>
                </tr>
            </table>
        </div>

        <hr>
        <h3>Đánh giá & Bình luận</h3> <!-- headline với cỡ chữ to thứ 3-->
            <div class="Comments&Rating">
                <span >Tổng điểm đánh giá: 3.7/5</span>
                <ul>
                    <li>5 sao:
                        <ul>
                            <li>Bình luận 1</li>
                            <li>Bình luận 2</li>
                            <li>Bình luận 3</li>
                        </ul>
                    </li>
                    <li>4 sao:
                        <ul>
                            <li>Bình luận 1</li>
                            <li>Bình luận 2</li>
                            <li>Bình luận 3</li>
                        </ul>
                    </li>
                    <li>3 sao:
                        <ul>
                            <li>Bình luận 1</li>
                            <li>Bình luận 2</li>
                            <li>Bình luận 3</li>
                        </ul>
                    </li>
                    <li>2 sao:
                        <ul>
                            <li>Bình luận 1</li>
                            <li>Bình luận 2</li>
                            <li>Bình luận 3</li>
                        </ul>
                    </li>
                    <li>1 sao:
                        <ul>
                            <li>Bình luận 1</li>
                            <li>Bình luận 2</li>
                            <li>Bình luận 3</li>
                        </ul>
                    </li>
                </ul>
            </div>
    <hr>
    
    <aside> <h3>Sản phẩm tương tự</h3> 
        <div>
            <a href="#">
            <div class="similar-item">
                <img src="SamsungS24.png" alt="Samsung Galaxy S24" width="80">
                <p>Samsung Galaxy S24 Ultra</p> <!-- chèn đường dẫn tới sản phẩm khi click vào hình -->
                <span>28.000.000 VNĐ</span>
            </div>
            </a>

            <a href="#">
            <div class="similar-item">
                <a href="#">
                <img src="GooglePixel9.png" alt="Google Pixel 9" width="80">
                <p>Google Pixel 9 Pro</p>
                <span>22.500.000 VNĐ</span>
            </div>
            </a>

            <a href="#">
            <div class="similar-item">
                <img src="Xiaomi14.png" alt="Xiaomi 14" width="80">
                <p>Xiaomi 14 Ultra</p>
                <span>21.000.000 VNĐ</span>
            </div>
            </a>
        </div>
    </aside>
    </main>
    
    <footer> <!-- thẻ ghi chú cuối trang web --> 
        <p>&copy; 2026 Tên Cửa Hàng. All rights reserved.</p> <!-- đoạn văn nội dung -->
    </footer>

</body>
```
### Câu C2:
**Cách tiếp cận "div-only" thực chất là một cái bẫy về kỹ thuật (technical debt) mà bạn sẽ phải trả giá đắt sau này. Dưới đây là lý do tại sao nên đầu tư thêm vài giây để gõ đúng thẻ:**
1. Hai trụ cột kỹ thuật: SEO và Accessibility
   - SEO (Tối ưu hóa tìm kiếm): Bot của Google không đọc CSS để hiểu website. Nó dựa vào các thẻ như `<main>, <article>`, hay `<h1>` để biết nội dung nào là trọng tâm. Nếu toàn bộ trang chỉ là một rừng `<div>`, bot sẽ      mất phương hướng, dẫn đến việc xếp hạng nội dung kém chính xác và giảm lưu lượng truy cập tự nhiên.
   - Accessibility (Khả năng tiếp cận): Đối với người dùng khiếm thị sử dụng trình đọc màn hình (Screen Reader), thẻ semantic đóng vai trò như "biển báo giao thông". Một cái `<div>` vô hồn không thể báo hiệu đó là một          thanh điều hướng (`<nav>`) hay một nút bấm. Sử dụng đúng thẻ giúp mọi đối tượng người dùng đều có thể trải nghiệm sản phẩm.

2. Ví dụ thực tế: `<button>` vs `<div class="btn">`
   - Nếu bạn dùng <button>, trình duyệt mặc định hỗ trợ:
      - Tương tác bằng bàn phím (phím Enter/Space).
      - Trạng thái focus để người dùng biết mình đang ở đâu.
      - Các thuộc tính disabled.
   - Nếu dùng `<div>`, bạn sẽ phải tự viết thêm hàng chục dòng JavaScript chỉ để "giả lập" những hành vi mặc định đó. Vậy ai mới là người tốn thời gian hơn?

---

