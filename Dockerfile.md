# [Thực hành với Dockerfile](google.com)

 1. Chỉ định image gốc tạo ra image bằng `Dockerfile`:
 ```sh
 FROM ubuntu:18.10
 ```
 2. Bổ sung thông tin về người tao ra `Dockerfile`:
 ```sh
 MAINTAINER GekiRin
 ```
 3. Chạy các lệnh cài đặt bổ sung gói cho image, giả sử ở đây muốn tạo image `ping`:
 ```sh
 RUN apt-get update && apt-get install -y net-tools iputils-ping && mkdir /script
 ```
 *Trong thư mục script, tạo 1 file script đơn giản `ping.sh`:
 ```sh
 #!/bin/bash
 ping 8.8.8.8
 ```
 4. Copy script `ping.sh` từ thư mục script:
 ```sh
 COPY ping.sh /script/
 ```
 5. Phân quyền:
 ```sh
 RUN chmod +x /script/ping.sh
 ```
 6. Đặt thư mục làm việc cho các chỉ thị trên:
 ```sh
 WORKDIR /script
 ```
  Tổng hợp các phần trên hoàn chỉnh tạo ra 1 file `Dockerfile` như sau:
  ```sh
   FROM ubuntu:18.10
   MAINTAINER GekiRin
   RUN apt-get update && apt-get install -y net-tools iputils-ping && mkdir /script
   COPY ping.sh /script/
   RUN chmod +x /script/ping.sh
   WORKDIR /script
   ```
 7. Thực hiện lệnh sau trên host để tạo 1 image có tên `dockerfile_test`:
 ```sh
 docker build -t dockerfile_test .
 ```
 8. Kiểm tra image vừa tạo:
 ```sh
 docker images
 ```
 9. Tạo container mới từ image vừa tạo:
 ```sh
 docker run -it dockerfile_test
 ```
 10. Chạy script `ping.sh`:
 ```sh
 ./ping.sh
 ```
