# News Web — Đề 19: Website Tin tức / Cổng thông tin

## Mục tiêu
Triển khai website tin tức bằng Docker Compose, có reverse proxy,
monitoring, logging và hardening có kiểm chứng.

## Môi trường
- Windows 11, Docker Desktop, Linux containers trên WSL 2.
- Terminal PowerShell.
- Demo trên localhost.

## Trạng thái đã kiểm thử
- WordPress kết nối MySQL thành công.
- Admin đăng nhập, tạo danh mục, đăng và sửa bài.
- Khách đọc được ba bài mẫu.
- Bài thử được đưa vào thùng rác và không còn công khai.
- MySQL và phpMyAdmin truy vấn được dữ liệu WordPress.
- Dữ liệu vẫn tồn tại sau khi restart MySQL.

Nginx, monitoring và logging chưa được triển khai tại mốc này.

## Cách chạy
Mở PowerShell trong thư mục chứa docker-compose.yml.
Yêu cầu Docker Desktop đang chạy Linux containers.

Chỉ trên lần chuẩn bị đầu tiên, khi chưa có .env:
```powershell
Copy-Item .env.example .env
notepad .env
```

Thay các giá trị CHANGE_ME bằng hai mật khẩu mạnh, khác nhau.
Không ghi đè .env hiện có.

Khởi động:
```powershell
docker compose up -d
docker compose ps
```

Truy cập tại mốc hiện tại:
- WordPress: http://localhost:8080
- Admin: http://localhost:8080/wp-admin/
- phpMyAdmin: http://localhost:8081

Trên volume trống, hoàn tất cài đặt WordPress qua trình duyệt.
Đăng nhập phpMyAdmin bằng MYSQL_USER và MYSQL_PASSWORD trong .env.
Bài viết và tài khoản thực hành nằm trong database, không nằm trong Git.

Dừng:
```powershell
docker compose stop
```

## Lưu trữ và bảo mật
- Named volume mysql_data lưu database.
- Named volume wordpress_data lưu file WordPress.
- MySQL không publish cổng ra Windows.
- WordPress và phpMyAdmin chỉ publish trên 127.0.0.1.
- Network database được cấu hình internal.
- Tài khoản ứng dụng chỉ được cấp quyền trên database news_db.
- Không commit .env, mật khẩu thật, private key hoặc backup database.
- Thay .env không tự đổi mật khẩu MySQL đã khởi tạo.
- Không xóa volume khi chưa có backup và chưa xác định dữ liệu sẽ mất.

## Các mốc tiếp theo
1. Nginx Reverse Proxy và security headers.
2. Prometheus, Grafana và exporters.
3. Loki, Promtail và ba truy vấn LogQL.
4. Kiểm thử tổng thể, lưu minh chứng và hoàn thiện báo cáo.
