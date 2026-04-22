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
