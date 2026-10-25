# Monitoring va logging

## Monitoring
- Prometheus: http://localhost:9090
- Grafana: http://localhost:3000
- Exporters: cAdvisor, Nginx Exporter, MySQL Exporter.
- Metrics container thuoc moi truong Linux Docker Desktop, khong phai toan Windows.
- Kiem tra Targets UP va nginx_up/mysql_up bang 1.
- Dashboard Grafana duoc luu trong volume grafana_data.

## MySQL Exporter tren may moi
Truoc khi khoi dong mysql-exporter:
1. Tao thu muc secrets va file mysql-exporter.cnf:
   [client]
   user=exporter
   password=MAT_KHAU_RIENG_CAN_THAY
   host=mysql
   port=3306
2. Khoi dong MySQL va dang nhap bang root.
3. Tao tai khoan voi cung mat khau:
   CREATE USER 'exporter'@'%' IDENTIFIED BY 'MAT_KHAU_RIENG_CAN_THAY'
     WITH MAX_USER_CONNECTIONS 3;
   GRANT PROCESS, REPLICATION CLIENT, SELECT ON *.* TO 'exporter'@'%';
4. Khoi dong cac dich vu con lai.

Tai khoan exporter co quyen doc rong, khong phai tai khoan WordPress.
Khong commit file secrets thuc te.

## Logging
- Promtail doc log qua Docker API, gui toi Loki.
- Grafana dung datasource Loki tai http://loki:3100.
- Khong can doc duong dan log Docker truc tiep tu Windows.
- Loki luu du lieu trong volume loki_data.
- Promtail luu vi tri doc trong volume promtail_positions.
- Promtail da EOL ngay 2026-03-02; chi giu theo yeu cau bai thuc hanh.
- Docker socket va containerd socket la cac giao dien nhay cam.
  Mount read-only khong dam bao API chi doc.

## LogQL
1. {job="docker",service="nginx"}
   Xem log Nginx.
2. {job="docker",service="nginx"} |= "demo-log-not-found-2026"
   Loc request thu nghiem, kiem tra ma HTTP 404 trong dong log.
3. sum by (service) (count_over_time({job="docker"}[5m]))
   Dem dong log theo service trong cua so 5 phut.

## Minh chung
Luu anh Targets, dashboard va ket qua tung truy van vao docs/evidence.
Khong dua mat khau, token hoac noi dung file secrets vao anh.
