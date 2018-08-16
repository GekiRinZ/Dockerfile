# Docker-Compose

Sử dụng Docker Compose để chạy Wordpress trong một môi trường độc lập được build bởi Docker container.

1. Cài đặt `docker-compose`: 
```sh
pip install docker-compose
```
2. Tạo `docker-compose-wordpress` thư mục để thực hiện project:
```sh
cat > docker-compose-wordpress
cd docker-compose-wordpress
```
3. Tạo file `docker-compose.yml` dùng để khởi tạo Wordpress Blog và database MySQL:
```sh
version: '3.3'

services:
   db:
     image: mysql:8.0
     volumes:
       - db_data:/var/lib/mysql
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     ports:
       - "8000:80"    //hoặc 8000:443
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress
volumes:
    db_data:
```
4. Tiến hành build trong thư mục project:
```sh
docker-compose up -d
```
Ta được kết quả:
```sh
Pulling db (mysql:8.0)...
8.0: Pulling from library/mysql
Digest: sha256:d39a8ab7679df309e7eff6ddba434ad5747cc2a2acee2d7c60d8221c9acedcad
Status: Downloaded newer image for mysql:8.0
Pulling wordpress (wordpress:latest)...
latest: Pulling from library/wordpress
Digest: sha256:d92a0d4e9aae885789af8538bb8afe8624c23cb5d763dcc1d3a2e4ac57531d21
Status: Downloaded newer image for wordpress:latest
docker-compose-wordpress_db_1 is up-to-date
docker-compose-wordpress_wordpress_1 is up-to-date
```
5. Tại thời điểm này, Wordpress sẽ chạy tại cổng 8000 của Docker Host và ta có thể truy cập vào địa chỉ http://localhost:8000 và tiến hành các thao tác với Wordpress:
![](/Screenshot%20from%202018-08-16%2017-36-54.png)

6. Tắt và dọn dẹp docker-compose:
- Sử dụng lệnh `docker-compose down` để xóa containers và default network nhưng sẽ bảo toàn database của Wordpress.
- Sử dụng lệnh `docker-compose down` để xóa toàn bộ containers, default network và database của Wordpress.

