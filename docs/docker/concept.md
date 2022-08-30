---
sidebar_position: 1
---

# Concept

## Khái niệm

Docker là một công nghệ container để tạo và quản lý các container

Nó là môi trường thuận lợi để mà test với kiểm thử chứ không thể để kiểu máy này chạy được, máy kia không chạy được. Tạo một môi trường giống nhau giữa các máy luôn. Kiểu những người khác công ti khác hệ thống máy đều có thể sử dụng được.

## Cài đặt

Máy yếu quá thì có thể xài Docker Toolbox còn không xài bình thường. Cài cái toolbox phải tự cài máy ảo đồ khá lằng nhằng.

## Container

Container là kiểu như một cái package đã có code và môi trường code của nó luôn, quản lý bởi server chứ ko phải bởi máy ảo nên nhanh với nhẹ hơn. Image cũng có thể tạo và chia sẻ được, không giống virtual machine là không thể chia sẻ được dễ như vậy.

## Image

Image nơi chứa code, logic,.. còn container là 1 running instance của image. Image giống class, có thể có nhiều instance là các container, mỗi cái độc lập với nhau

## Dockerfile

```dockerfile
  ##Chọn base images
  FROM node
  ##Chọn thư mục root (Nơi mà để mình có thể thực hiện các lệnh chạy)
  WORKDIR /app
  ##Copy file từ thư mục hiện tại là . (build context) sang images(/app) do đã set workdir phía trên
  ##Có thể viết dockerignore để đá bớt cái node_modules ra
  COPY . ./
  ## Hoặc copy kiểu
  COPY . /app
  ##Copy xong thì thực hiện lấy các dependency
  RUN npm install
  ##EXPOSE cái port của app chạy, thường backend mình để 5000 thì expose 5000
  ##Có thể không có cũng được, làm vầy thì dễ document hơn
  EXPOSE 5000
  ##Tạo volume
  VOLUME ["app/abc"]
  ##RUN thì nó chạy liền luôn còn cái này khi chạy container nó mới chạy
  CMD ["node","server.js"]
```

Ở đây để tránh thay đổi và build lại nhiều lần tốn thời gian khi các file ko quan trọng thay đổi thì

- Có thể dùng dockerignore
- Copy package.json và run npm install trước rồi mới copy để lần sau thay đổi code 1 xíu thì ko phải install lại

## Các loại data

- Application(Code + enviroment): **Read**
- Temporary Appdata(Enter user input, store in memory or temporary file, kiểu nó thay đổi trong quá trình thực thi chương trình, bộ nhớ đc cấp, mình stop là đi luôn) **Read and write** chỉ lưu ở container
- Permanant Appdata: Kiểu như 1 số dữ liệu mà nó lưu lại, stop đồ không mất **Read and write** lưu ở container và volume

## Volume

Để mà có thể thay đổi code trong quá trình chạy, run các thứ = docker thì cũng phải có cách giữ lại các data, chứ ko phải mỗi lần thay đổi là mất hết data luôn

> Volume là folder trong host machine mà được map tới container

Volumes có nhiều loại

- Volumes(quản lý bởi docker)
  - Anonymous Volumes: Tạo kiểu `VOLUME ["app/abc"]` trong dockerfile là anonymous, kiểu như `rm` là mất luôn
  - Named Volumes: Tạo trong command `docker run -it -v <imagename>:/<folderpath> <imagename>`. Cái file đó cũng có thể truy cập = port của cái container cũ dù container cũ đã bị xóa

Docker sẽ kiểu tạo 1 cái folder trong host machine, dev ko bk rõ địa chỉ quản lý ở `docker volume`

- Bind Mounts(Tự quản lý)
