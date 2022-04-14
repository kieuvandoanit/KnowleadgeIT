# Docker
### Liệt kê các images
1) Liệt kê các image
```sh
docker images
```
2) Tải về image từ docker hub
```sh
docker pull <image>:<tag>
```
3) Xóa 1 image
```sh
docker image rm <image>:<tag>
```

### Chạy 1 container
1) Chạy container
- Cú pháp chung: `docker run thamso IMAGE command thamsolenh`
```sh
docker run -it ubuntu:lastest   
```
- Đặt tên cho container: `--name <container_name>`
- Đặt hostname cho container: ` -h <host_name>`

2) Liệt kê các container đang chạy
```sh
docker ps
```
3) Liệt kê tất cả các docker
```sh
docker ps -a
```
4) Resart container
```sh
docker start <container_name>
# docker start <container_id>

docker stop <container_name>
# docker stop <container_id>
```
5) Truy cập vào terminal của container
```sh
docker attach <container_id>
# docker attach <container_name>
```
- Trường hợp muốn thoát terminal của container, mà vẫn muốn container chạy: `CTRL + P + Q`
- Trường hợp muốn thoát terminal của container và stop container: `exit`
6) Xóa 1 container 
- Xóa container đã tắt
```sh
docker rm <container_id>
```
- Xóa container đang chạy
```sh
docker rm -f <container_id>
```
7) Thực hiện command trên container
- Truy cập vào container, gõ command như bình thường
- Đứng ở máy host, muốn thực hiện command của 1 container:
```sh
docker exec container command
```
8) Lưu container thành image, xuất ra image file
- Xuất ra 1 image từ 1 container (container phải đang stop)
```sh
docker commit <container> <image>:<tag>
```
- Lưu image ra file
```sh
docker save --output filename.tar <image_id>
```
- Nạp image vào docker từ 1 file
```sh
docker load -i filename.tar
# Đặt tên và tag cho image
docker tag <image_id> <name>:<tag>
```
### Chia sẻ dữ liệu giữa máy host với container, container vs container
1) Chia sẻ dữ liệu máy host với container
```sh
docker run -it -v pathHost:pathContainer <imageID>
# docker run -it -v "D:\vandoan\KnowleadgeIT":/hom/dulieu ff85
```
2) Tạo 1 container khác có chung thư mục chia sẻ dữ liệu với 1 container đã tồn tại
```sh
docker run -it --volumes-from <OtherContainer> <imageID>
```
3) Tạo và quản lý ổ đĩa docker volume
- Kiểm tra xem có ổ đĩa nào đang chạy
```sh
docker volume ls
```
- Tạo 1 ổ đĩa
```sh
docker volume create <NameDisk>
```
- Kiểm tra thông tin ổ đĩa
```sh
docker volume inspect <NameDisk>
```
- Xóa 1 ổ đĩa
```sh
docker volume rm <NameDisk>
```
- Tạo 1 container gắn ổ đĩa volume vào container
```sh
# docker run -it --mount source=DISK, targe=pathContainer imageID
docker run -it -name C1 --mount source=D2, target=/home/disk2 ubuntu:latest
```
- Tạo ổ đĩa ánh xạ vào thư mục máy host
```sh
docker volume create --opt device="D:\vandoan\KnowleadgeIT" --opt type=none --opt o=bind DISK1
```
- Tạo container gắn volume ánh xạ vào máy host
```sh
docker run -it -v DISK1:/home/disk ubuntu:lastest
```

## Networking trong Docker, tạo và quản lý network
- Kiểm tra xem trong docker đang có những mạng nào
```sh
docker network ls
```
- Kiểm tra thông tin network
```sh
docker network inspect <network_name>
```
- Ánh xạ cổng từ container vào máy host
```sh
docker run -it --name B2 -p 8888:80 <imageName>
```
- Tạo ra 1 network
```sh
docker network create --driver bridge <networkName>
```
- Xóa 1 network
```sh
docker network rm <networkName>
```
- Tạo container kết nối tới network
```sh
docker run -it --name B3 --network <networkName> <imageName>
```
- Gắn network cho 1 container đang chạy
```sh
docker network connect <networkName> <containerName>
```
Hihi