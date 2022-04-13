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

```