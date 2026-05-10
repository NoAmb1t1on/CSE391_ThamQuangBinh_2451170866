# PBT_02
---
## Phần A:
### Câu A1 (07_forms_interactive.md-3.Core Technical Truth):
    1.type="email" → Ô nhập văn bản, tự kiểm tra định dạng @ → Đăng ký tài khoản khách hàng.
    2.type="password" → Ẩn ký tự bằng dấu chấm/sao, bảo mật → Nhập mật khẩu khi thanh toán.
    3.type="number" → Chỉ nhập số, có nút tăng/giảm, kiểm tra min/max → Chọn số lượng sản phẩm.
    4.type="tel" → Hiển thị bàn phím số trên mobile, hỗ trợ pattern → Nhập số điện thoại giao hàng.
    5.type="url" → Tự kiểm tra định dạng đường dẫn http:// → Nhập link website của đối tác/nhà cung cấp.
    6.type="date" → Hiển thị bảng lịch (DatePicker) chọn ngày → Chọn ngày dự kiến nhận hàng.
    7.type="range" → Thanh trượt chọn giá trị trong khoảng định sẵn → Bộ lọc tìm kiếm theo giá sản phẩm.
    8.type="color" → Bảng chọn màu sắc, trả về mã Hex → Chọn màu sắc tùy chỉnh cho sản phẩm.
    9.type="search" → Ô nhập văn bản kèm nút "X" để xóa nhanh nội dung → Tìm kiếm tên sản phẩm trên store.
    10.type="file" → Nút chọn tệp từ thiết bị, kiểm tra định dạng qua accept → Tải ảnh thực tế khi đánh giá sản phẩm.

### Câu A2 (07_forms_interactive.md-3.Core Technical Truth):
- Trường hợp 1: Form không được gửi đi. Trình duyệt hiển thị thông báo lỗi. Thuộc tính required bắt buộc trường này không được phép để trống.
- Trường hợp 2: Form không được gửi đi. Trình duyệt báo lỗi sai định dạng. type="email" kích hoạt bộ lọc tự động, yêu cầu nội dung phải có cấu trúc của một email.
- Trường hợp 3: Form không được gửi đi. Trình duyệt báo lỗi giá trị không hợp lệ. Thuộc tính max="10" giới hạn giá trị cao nhất là 10, trong khi giá trị nhập vào là 15.
- Trường hợp 4: Form không được gửi đi. Trình duyệt báo dữ liệu không khớp với định dạng yêu cầu. Thuộc tính pattern yêu cầu dữ liệu phải khớp với biểu thức chính quy (Regex) [0-9]{10},"abc123" vi phạm cả về ký tự lẫn độ dài.
- Trường hợp 5: Form không được gửi đi. Trình duyệt báo lỗi chuỗi quá ngắn. Thuộc tính minlength="8" yêu cầu độ dài tối thiểu của chuỗi là 8 ký tự, trong khi "123" chỉ có 3 ký tự.

### Câu A3 ():
1. `<label for="email">` quan trọng cho người dùng Screen Reader là vì:
    - Liên kết dữ liệu: Thuộc tính for liên kết trực tiếp với id của ô input. Khi người dùng khiếm thị dùng Screen Reader (trình đọc màn hình) tab vào ô nhập liệu, thiết bị sẽ đọc to nội dung bên trong thẻ <label> lên. Nếu không có <label>, người dùng sẽ chỉ nghe thấy "Edit text, empty", khiến họ không biết phải nhập thông tin gì.
    - Mở rộng vùng tương tác: Giúp người dùng dễ dàng click vào vùng nhãn để kích hoạt ô nhập liệu, cực kỳ hữu ích cho những người có vấn đề về vận động tinh.
2. Dùng `<fieldset>` + `<legend>` khi cần nhóm các thẻ input có liên quan chặt chẽ với nhau về mặt nội dung để tạo ngữ cảnh rõ ràng. VÍ dụ:
```html
<fieldset>
  <legend>Phương thức vận chuyển</legend>
  <input type="radio" id="fast" name="ship">
  <label for="fast">Giao hàng hỏa tốc</label><br>
  <input type="radio" id="standard" name="ship">
  <label for="standard">Giao hàng tiêu chuẩn</label>
</fieldset>
```
3. `arial-label`:
    - Dùng khi giao diện thiết kế không cho phép hiển thị văn bản nhãn (để đảm bảo thẩm mỹ) nhưng vẫn cần cung cấp thông tin cho Screen Reader.
    - Không dùng chung với `label` vì:
        - `aria-label` sẽ ghi đè nội dung của `<label>`. Screen Reader sẽ chỉ đọc `aria-label` và bỏ qua `<label>`.
        - Quy tắc cốt lõi của Accessibility là "Sử dụng HTML thuần trước khi dùng ARIA". `<label>` là cách chuẩn nhất, hỗ trợ tốt nhất cho mọi trình duyệt và thiết bị; `aria-label` chỉ là phương án thay thế khi không thể dùng nhãn hiển thị.

### Câu A4 (06_graphics_multimedia.md-3.Core Technical Truth):
- Dùng cách 1 khi ảnh chỉ để minh họa hoặc là một phần nhỏ trong giao diện, không cần chú thích chữ bên dưới. Ví dụ:
    - Ảnh Avatar nhỏ bên cạnh tên khách hàng trong mục Review.
    - Các icon tiện ích trong phần mô tả ngắn.
- Dùng cách 2 khi ảnh là một nội dung quan trọng, đứng độc lập và cần có tiêu đề/chú thích đi kèm để người dùng dễ hiểu. Ví dụ:
    - Ảnh sản phẩm chính trong giỏ hàng.
    - Biểu đồ so sánh kích thước các dòng máy trong bài viết tư vấn chọn mua.
---

## Phần C:
### Câu C1:
1. Lỗi 1: Dòng 2 — Input "Tên" thiếu `<label for="...">` và thuộc tính id, vi phạm accessibility. Sửa: `<label for="name">Tên:</label> <input type="text" id="name" name="name" required>`.
2. Lỗi 2: Dòng 4 — Input `"Email"` dùng placeholder thay thế nhãn, thiếu required và name. Sửa: `<label for="email">Email:</label> <input type="email" id="email" name="email" placeholder="Email của bạn" required>`.
3. Lỗi 3: Dòng 6 — Input "Mật khẩu" thiếu minlength để bảo mật và thiếu nhãn. Sửa: `<label for="pwd">Mật khẩu:</label> <input type="password" id="pwd" name="password" minlength="8" required>`.
4. Lỗi 4: Dòng 7 — Input "Nhập lại mật khẩu" không có nhãn và id riêng biệt. Sửa: `<label for="re-pwd">Nhập lại mật khẩu:</label> <input type="password" id="re-pwd" name="re_password" required>`.
5. Lỗi 5: Dòng 9 — Input "Phone" dùng `type="text"`, không tối ưu bàn phím số trên mobile. Sửa: `<label for="tel">Phone:</label> <input type="tel" id="tel" name="phone" pattern="[0-9]{10}">`.
6. Lỗi 6: Dòng 11 — Thẻ `<select>` thiếu nhãn mô tả và thuộc tính name để gửi dữ liệu. Sửa: `<label for="city">Thành phố:</label> <select id="city" name="city"><option value="hn">Hà Nội</option>...</select>`.
7. Lỗi 7: Dòng 16 — Thẻ `<label>` điều khoản không chứa hoặc không liên kết với input `type="checkbox"`. Sửa: `<input type="checkbox" id="terms" name="terms" required> <label for="terms">Tôi đồng ý điều khoản</label>`.
8. Lỗi 8: Tổng thể — Thiếu thẻ `<button type="submit">` và không có thuộc tính action/method cho form. Sửa: Thay thế bằng `<button type="submit">Gửi</button> bên trong <form action="/submit" method="POST">`.

### Câu C2:
1. Regex Pattern cho CMND/CCCD và Số tài khoản
    - CMND/CCCD (Đúng 12 chữ số): `pattern="[0-9]{12}"`.
    - Số tài khoản (10 đến 15 chữ số): `pattern="[0-9]{10,15}"`.
2. HTML5 Validation không đủ an toàn. Vì:
    - Dễ bị vượt qua: Người dùng có thể dùng DevTools để xóa thuộc tính `required` hoặc `pattern`, hoặc dùng các công cụ như Postman để gửi dữ liệu trực tiếp lên server mà không thông qua trình duyệt.
    - Mục đích chính: HTML5 validation chỉ phục vụ UX để báo lỗi nhanh, chứ không phải một rào cản bảo mật vững chắc.
3. 3 loại validation HTML5 KHÔNG THỂ làm được (Cần JavaScript):
    - Kiểm tra trùng lặp dữ liệu: Ví dụ kiểm tra email này đã được đăng ký trong Database hay chưa.
    - So khớp hai trường : Ví dụ kiểm tra ô "Nhập lại PIN" có khớp với ô "PIN" đã nhập trước đó hay không.
    - Thuật toán logic phức tạp: Ví dụ thuật toán Luhn để kiểm tra tính hợp lệ của số thẻ ngân hàng hoặc kiểm tra độ mạnh mật khẩu theo thời gian thực.
4. 2 rủi ro bảo mật nếu chỉ validate trên Frontend:
    - Tấn công Injection: Nếu không validate ở Backend, kẻ tấn công có thể gửi các đoạn mã độc vào Database để đánh cắp dữ liệu hoặc phá hoại hệ thống.
    - Sai lệch dữ liệu tài chính: Kẻ xấu có thể gửi số tiền âm hoặc số lượng sản phẩm không hợp lệ, gây thất thoát tài sản nghiêm trọng cho ngân hàng.





