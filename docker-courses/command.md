# Docker Commands

## Quản lý Image

```bash
docker pull ubuntu              # Kéo image Ubuntu về máy
docker images                   # Liệt kê tất cả images
docker rmi <image_id>           # Xóa một image
docker build -t <name> .        # Build image từ Dockerfile
docker tag <image> <new_tag>    # Đặt tag cho image
docker push <username>/<image>  # Push image lên Docker Hub
```

## Quản lý Container

```bash
docker run -it ubuntu           # Chạy container ở chế độ interactive
docker run -d ubuntu            # Chạy container ở chế độ background (detached)
docker run -p 8080:80 nginx     # Map port 8080 (host) -> 80 (container)
docker run -v /host:/container ubuntu  # Mount volume
docker run --name myapp ubuntu  # Đặt tên cho container
docker run -p 5173:5173 -v "$(pwd):/app" -v /app/node_modules react-docker  # Chạy container với bind mount + anonymous volume (giữ node_modules trong container)
docker ps                       # Liệt kê containers đang chạy
docker ps -a                    # Liệt kê tất cả containers (kể cả đã dừng)
docker stop <container_id>      # Dừng container
docker start <container_id>     # Khởi động lại container đã dừng
docker restart <container_id>   # Restart container
docker rm <container_id>        # Xóa container
docker exec -it <container_id> bash  # Truy cập vào container đang chạy
docker logs <container_id>      # Xem logs của container
docker inspect <container_id>   # Xem thông tin chi tiết container
```

## Docker Compose

```bash
docker compose up               # Khởi động tất cả services (CLI plugin mới)
docker compose up -d            # Khởi động ở chế độ background
docker compose down             # Dừng và xóa tất cả services
docker compose ps               # Liệt kê services đang chạy
docker compose logs             # Xem logs tất cả services
docker compose build            # Build lại images
docker-compose up               # Khởi động tất cả services (standalone cũ)
docker-compose up -d            # Khởi động ở chế độ background (standalone cũ)
docker-compose down             # Dừng và xóa tất cả services (standalone cũ)
docker-compose ps               # Liệt kê services đang chạy (standalone cũ)
docker-compose logs             # Xem logs tất cả services (standalone cũ)
docker-compose build            # Build lại images (standalone cũ)
```

## Quản lý Network & Volume

```bash
docker network ls               # Liệt kê networks
docker network create <name>    # Tạo network mới
docker volume ls                # Liệt kê volumes
docker volume create <name>     # Tạo volume mới
```

## Dọn dẹp

```bash
docker system prune             # Xóa tất cả containers, images, networks không dùng
docker container prune          # Xóa tất cả containers đã dừng
docker image prune              # Xóa images không dùng
```

---

# Ubuntu Commands

## Quản lý File & Thư mục

```bash
ls                              # Liệt kê file/thư mục
ls -la                          # Liệt kê chi tiết (bao gồm file ẩn)
cd /path/to/dir                 # Di chuyển đến thư mục
pwd                             # Hiển thị thư mục hiện tại
mkdir <dir_name>                # Tạo thư mục mới
mkdir -p a/b/c                  # Tạo thư mục lồng nhau
rm <file>                       # Xóa file
rm -rf <dir>                    # Xóa thư mục và nội dung bên trong
cp <source> <dest>              # Copy file
cp -r <source> <dest>           # Copy thư mục
mv <source> <dest>              # Di chuyển hoặc đổi tên
touch <file>                    # Tạo file mới (rỗng)
cat <file>                      # Xem nội dung file
head -n 10 <file>               # Xem 10 dòng đầu
tail -n 10 <file>               # Xem 10 dòng cuối
find / -name "*.log"            # Tìm file theo tên
```

## Quản lý Package (APT)

```bash
apt update                      # Cập nhật danh sách packages
apt upgrade                     # Nâng cấp tất cả packages
apt install <package>           # Cài đặt package
apt remove <package>            # Gỡ package
apt search <keyword>            # Tìm kiếm package
apt list --installed            # Liệt kê packages đã cài
```

## Quản lý User & Permission

```bash
whoami                          # Xem user hiện tại
sudo <command>                  # Chạy lệnh với quyền root
chmod 755 <file>                # Thay đổi quyền file
chown user:group <file>         # Thay đổi chủ sở hữu file
adduser <username>              # Tạo user mới
passwd <username>               # Đổi mật khẩu user
```

## Quản lý Process

```bash
ps aux                          # Liệt kê tất cả process
top                             # Monitor process realtime
htop                            # Monitor process (giao diện đẹp hơn)
kill <pid>                      # Dừng process theo PID
killall <name>                  # Dừng tất cả process theo tên
```

## Mạng (Network)

```bash
ifconfig                        # Xem thông tin mạng
ip addr                         # Xem địa chỉ IP
ping <host>                     # Kiểm tra kết nối
curl <url>                      # Gửi HTTP request
wget <url>                      # Tải file từ URL
netstat -tlnp                   # Xem các port đang mở
ss -tlnp                        # Xem các port đang mở (thay thế netstat)
```

## Hệ thống

```bash
df -h                           # Xem dung lượng ổ đĩa
du -sh <dir>                    # Xem dung lượng thư mục
free -h                         # Xem RAM
uname -a                        # Thông tin hệ thống
uptime                          # Thời gian hoạt động
reboot                          # Khởi động lại
shutdown -h now                 # Tắt máy ngay
```

## Nén & Giải nén

```bash
tar -czvf archive.tar.gz <dir>  # Nén thư mục
tar -xzvf archive.tar.gz       # Giải nén
zip -r archive.zip <dir>       # Nén thành .zip
unzip archive.zip               # Giải nén .zip
```
