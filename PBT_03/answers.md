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

---

    
