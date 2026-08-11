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
- Tìm kiếm và lọc sản phẩm theo từ khóa / danh mục.
- Giao diện responsive (hỗ trợ thiết bị di động).
- Nhập liệu/ứng dụng báo cáo đơn giản (báo cáo doanh thu theo đơn hàng).

## Tech Stack
- Back-end: PHP (thuần hoặc framework nhẹ tuỳ triển khai)
- Front-end: HTML5, CSS3, JavaScript, Bootstrap
- Database: MySQL / MariaDB
- Công cụ bổ trợ: Composer (nếu dùng thư viện), jQuery (tùy chọn)
- Môi trường phát triển: Apache/Nginx hoặc PHP built-in server

## Architecture
Áp dụng mô hình MVC (Model - View - Controller)
- public/                : Thư mục gốc (entry point, assets: css/js/images)
  - index.php            : Front controller
  - assets/              : CSS, JS, hình ảnh
- app/
  - Controllers/         : Các controller xử lý request
  - Models/              : Các lớp tương tác DB (ORM hoặc query builder)
  - Views/               : Template/HTML (header, footer, pages)
  - Helpers/             : Hàm tiện ích chung
- config/
  - config.php           : Cấu hình kết nối DB, base URL, hằng số
- database/
  - migrations/          : (Tùy) file migration / schema
  - seeds/               : dữ liệu mẫu
- storage/ (hoặc uploads/) : Lưu trữ ảnh sản phẩm, file tạm
- vendor/ (nếu dùng Composer)

Luồng xử lý cơ bản:
1. Request tới public/index.php (Front controller).
2. Router định tuyến tới Controller tương ứng.
3. Controller gọi Model để lấy/ghi dữ liệu.
4. Controller truyền dữ liệu sang View để render HTML.

## Installation
Yêu cầu cơ bản:
- PHP >= 7.2 (hoặc phiên bản bạn đã phát triển)
- MySQL / MariaDB
- Composer (nếu dùng thư viện)

Cài đặt:
1. Clone repo:
   git clone https://github.com/khoinong/website-b-n-n-ng-s-n.git
2. Vào thư mục dự án:
   cd website-b-n-n-ng-s-n
3. Cài thư viện (nếu dùng Composer):
   composer install
4. Sao chép file cấu hình môi trường:
   cp config/config.example.php config/config.php
   - Sửa `config/config.php` hoặc `.env` để đặt thông tin DB, base URL, v.v.
5. Tạo database và import schema (nếu có file SQL):
   - Tạo database trên MySQL, ví dụ tên `vegetables_db`
   - Import (nếu có dump):
     mysql -u root -p vegetables_db < database/dump.sql
6. Thiết lập quyền ghi cho thư mục lưu trữ/uploads:
   chmod -R 755 storage/
   chown -R www-data:www-data storage/  # trên Linux với Apache/Nginx

## How to run
- Chạy bằng PHP built-in server (phù hợp phát triển):
  php -S localhost:8000 -t public
  Truy cập http://localhost:8000

- Hoặc cấu hình Virtual Host trong Apache/Nginx:
  - DocumentRoot trỏ tới đường dẫn .../website-b-n-n-ng-s-n/public
  - Thiết lập rewrite rules nếu dùng pretty URL (mod_rewrite cho Apache)

- Tài khoản admin mặc định (nếu có):
  - Sử dụng dữ liệu seed hoặc tạo thủ công trong DB. (Thông tin tài khoản mẫu có thể được thêm vào database/seeds/)

Ghi chú:
- Nếu có file .htaccess trong public/, đảm bảo mod_rewrite đã bật (Apache).
- Kiểm tra cấu hình DB trong config/config.php, đảm bảo kết nối thành công.
- Với môi trường production, tắt hiển thị lỗi PHP và bật caching phù hợp.

