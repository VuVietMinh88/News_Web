# News Web — Đề 19: Website Tin tức / Cổng thông tin

## Mục tiêu

Triển khai website tin tức WordPress bằng Docker Compose, có database,
reverse proxy, monitoring, logging và các biện pháp hardening có kiểm chứng.

## Môi trường thực hành

- Windows 11.
- Docker Desktop sử dụng Linux containers trên WSL 2.
- Terminal: PowerShell.
- Quản lý dịch vụ bằng lệnh docker compose.
- Demo bằng trình duyệt trên chính máy triển khai.

## Các thành phần dự kiến

- Website: WordPress.
- Database: MySQL.
- Quản trị database: phpMyAdmin.
- Reverse proxy: Nginx.
- Monitoring: Prometheus, Grafana và các exporter phù hợp.
- Logging: Loki và Promtail; sẽ xác minh phiên bản và khả năng tương thích.

## Trạng thái

- Đã kiểm tra kết nối Docker CLI với Docker Engine.
- Đã kiểm tra lệnh Docker Compose và Git.
- Đã khởi tạo repository và kiểm tra quy tắc .gitignore.
- Chưa tạo cấu hình hoặc triển khai các dịch vụ của đề tài.

## Cách chạy

Chưa có hướng dẫn chạy ứng dụng vì cấu hình triển khai chưa được tạo
và kiểm thử. Mục này sẽ được cập nhật theo từng mốc thực hành.

## Quản lý thông tin nhạy cảm

Không commit file .env thực tế, mật khẩu, private key, dữ liệu runtime
hoặc bản sao lưu database. File .env.example chỉ chứa cấu hình mẫu,
không chứa thông tin bí mật thật.

## Các mốc triển khai dự kiến

1. WordPress, MySQL, phpMyAdmin và Nginx Reverse Proxy.
2. Prometheus, Grafana và metrics thực tế.
3. Loki, Promtail và truy vấn LogQL.
4. Hoàn thiện hardening, kiểm thử, minh chứng và báo cáo.
