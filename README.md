# Website bán rau củ - Đồ án ngành

## Description
Website bán rau củ được xây dựng theo mô hình MVC sử dụng PHP. Mục tiêu là triển khai một hệ thống thương mại điện tử nhỏ phục vụ mô hình kinh doanh vừa và nhỏ, tách biệt rõ ràng giữa xử lý dữ liệu (Model), logic nghiệp vụ (Controller) và giao diện (View).

## Features
- Quản lý danh mục sản phẩm (thêm, sửa, xóa, phân loại).
- Danh mục và trang chi tiết sản phẩm.
- Giỏ hàng (thêm/xóa/cập nhật số lượng).
- Thanh toán đơn giản (mô phỏng) và quản lý đơn hàng.
- Đăng nhập/Đăng ký người dùng, xác thực cơ bản.
- Trang quản trị (Admin) để quản lý sản phẩm, đơn hàng, người dùng.
- Tìm kiếm sản phẩm theo từ khóa.
- Nhập liệu.

## Tech Stack
- Back-end: PHP 
- Front-end: HTML5, CSS3, JavaScript, Bootstrap
- Database: MySQL / MariaDB
- Môi trường phát triển: Apache/Nginx hoặc PHP built-in server

## Architecture
Áp dụng mô hình MVC (Model - View - Controller)
```text
vegetablestore/
│
├── index.php                     # File khởi tạo ứng dụng
├── vegetablestore.sql            # Cơ sở dữ liệu
│
├── mvc/
│   ├── Bridge.php                # Khởi tạo các class core
│   ├── controllers/             # Chứa controller
│   ├── core/                    # Router, controller cha, DB
│   │   ├── App.php
│   │   ├── Controller.php
│   │   └── DB.php
│   ├── models/                  # Chứa model
│   └── views/                   # Giao diện admin + user
│       ├── admin/
│       └── user/
│
└── public/
    ├── admin/                   # CSS/JS/Admin assets
    └── user/                    # CSS/JS/User assets
```
## Cấu trúc core của hệ thống

### App.php
File App.php là router chính của ứng dụng.

Chức năng:
- Đọc URL từ browser
- Tìm controller tương ứng
- Xác định action cần gọi
- Truyền tham số cho action
- Gọi phương thức tương ứng

### Controller.php
File này định nghĩa lớp Controller cha.

Chức năng:
- Nạp model: model("ModelName")
- Nạp view: viewuser("template", $data)
- Nạp view admin: viewadmin("template", $data)

### DB.php
File DB.php đảm nhiệm việc kết nối database theo PDO.

Thông tin kết nối cơ bản:
- Host: localhost
- Username: root
- Password: empty
- Database: vegetablestore
Luồng xử lý cơ bản:
1. Người dùng truy cập URL
2. App.php phân tích URL
3. Chọn controller phù hợp
4. Gọi đúng action
5. Controller gọi Model để lấy dữ liệu
6. Model truy vấn database
7. Controller truyền dữ liệu vào View
8. View render ra giao diện HTML

## Installation
Yêu cầu cơ bản:
- PHP >= 7.2 (hoặc phiên bản bạn đã phát triển)
- MySQL / MariaDB
- Composer (nếu dùng thư viện)
- git clone https://github.com/khoinong/website_ban_nong_san.git
### Yêu cầu
- PHP 7.4+
- Apache hoặc XAMPP/WAMP
- MySQL

### Cài đặt
1. Copy thư mục dự án vào thư mục web server, ví dụ: `htdocs` hoặc `www`.
2. Tạo database MySQL tên `vegetablestore`.
3. Import file `vegetablestore.sql` vào database.
4. Khởi động Apache và MySQL.
5. Truy cập địa chỉ: `http://localhost/vegetablestore/`

- Tài khoản admin mặc định (nếu có):
  - Sử dụng dữ liệu seed hoặc tạo thủ công trong DB. (Thông tin tài khoản mẫu có thể được thêm vào database/seeds/)
