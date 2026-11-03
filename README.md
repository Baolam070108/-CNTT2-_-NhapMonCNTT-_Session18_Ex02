1. VẤN ĐỀ LÀ GÌ?

- **Shipper thường xuyên bị đăng xuất và mất giỏ hàng khi đóng hoặc tải lại trình duyệt do cơ chế lưu trạng thái đăng nhập chưa phù hợp.**

3. YÊU CẦU LÀ GÌ?

- **Chức năng 1 (Duy trì trạng thái):** Vận dụng kiến thức về Persistent Cookies để thiết lập cơ chế ghi nhớ phiên làm việc thay vì sử dụng Session Cookies.

- **Chức năng 2 (Bảo mật):** Thiết lập các cờ bảo mật HttpOnly và Secure để ngăn chặn hành vi đánh cắp Session (Session Hijacking).

3. CÁCH LÀM:

- Phần 1. Phân tích:

Cache có dung lượng lớn (MB/GB), dùng để lưu hình ảnh, CSS, JavaScript giúp trang web tải nhanh. Cookies có dung lượng nhỏ (khoảng 4KB), dùng để lưu Token và thông tin phiên đăng nhập. Vì vậy, nên dùng Persistent Cookies để ghi nhớ đăng nhập lâu hơn.

- Phần 2. Triển khai:

Sử dụng Cookie với cấu trúc:
Set-Cookie: session_token=abc123; Max-Age=604800; HttpOnly; Secure; SameSite=Lax

Trong đó:

+ Token: Mã xác thực đăng nhập.
+ Max-Age=604800: Cookie tồn tại trong 7 ngày.
+ HttpOnly: Ngăn JavaScript truy cập Cookie.
+ Secure: Chỉ gửi Cookie qua HTTPS.
+ SameSite=Lax: Hạn chế gửi Cookie trong một số yêu cầu từ trang web khác.

- Phần 3. Kiểm thử:

Khi giao diện vẫn hiển thị màu cũ, thực hiện Hard Reload:
+ Mở trang web và nhấn F12.
+ Nhấn chuột phải vào nút Reload.
+ Chọn Empty Cache and Hard Reload.

