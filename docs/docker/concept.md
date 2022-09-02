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
  ARG DEFAULT_PORT=80
  ##Có thể viết dockerignore để đá bớt cái node_modules ra
  COPY . ./
  ## Hoặc copy kiểu
  COPY . /app
  ## Set các biến môi trường
  ENV PORT 5000
  Hoặc là ENV PORT=$DEFAULT_PORT
  ##Copy xong thì thực hiện lấy các dependency
  RUN npm install
  ##EXPOSE cái port của app chạy, thường backend mình để 5000 thì expose 5000
  ##Có thể không có cũng được, làm vầy thì dễ document hơn
  EXPOSE 5000
  # Hoặc là EXPOSE $PORT
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

- Bind Mounts(Tự quản lý): Tự set một cái volume ở máy host của mình. Giúp cho persistent data và editable data. Chỉ ảnh hưởng container, ko ảnh hưởng đến image
  - Vấn đề với `COPY . ./` là mình có thể xóa nó nếu mình binding nhưng mà nếu như mình chạy product thì cũng phải dùng cái này do lúc đó ko binding volumes

## Argument và Environment

- Arg: chỉ có trong Dockerfile, ko lấy được từ cmd hoặc application code. Có thể set trong lệnh run của image
  - Vẫn có thể đọc được giá trị các tham số qua lệnh `docker history`
- Env: có trong Dockerfile, và application code, có thể set trong docker run
  - Nói chung nếu set = env hay viết bằng dockerfile thì ngta vẫn có thể lấy ra đọc được. Chú ý đến vấn đề bảo mật thì ko set ở đây
  - Xem các lệnh cấu thành nên các layer của image: `docker history <imageName/ID>`

## Network

- Kiểu giúp container tương tác với nhau
- Có thể định nghĩa các driver với network

## Docker compose

- Thay vì phải nhớ các lệnh, gắn port, tạo volume thì có thể dùng docker compose để tự động hóa các việc đó, nó tiện lợi nhất là đối với những cái với nhiều micro service, mỗi container là 1 service.
- Nó không thay đổi image gốc hay gì mà chỉ là guideline các lệnh thôi
- Cách viết:

File docker-compose.yaml

- Ví dụ 1:

```yaml
# Version của docker
version: "3.0"
# Các container
services:
  # 2 dấu cách để xác định là con
  back-end:
  front-end:
  mongodb:
    environment:
```

- Nói chung là set environment có thể tạo 1 file rồi --env-file các kiểu
- Đối với docker-compose thì nó tự tạo cho tất cả các cái trong nó một network luôn, nên ko cần set network

- Ví dụ 2:

```yaml
version: "3.8"
services:
  mongodb:
    image: "mongo"
    volumes:
      - data:/data/db
    environment:
      - MONGO_INITDB_ROOT_USERNAME=root
      - MONGO_INITDB_ROOT_PASSWORD=secret
  backend:
    build: ./backend
    container_name: backend
    ports:
      - "5000:5000"

  frontend:
    build: ./frontend
    container_name: frontend
    ports:
      - "3000:3000"
    stdin_open: true
    tty: true
volumes:
  data:
```

- Phần build mặc định là context nhưng mà còn có thể viết kỹ hơn nếu như dockerfile mình tên là dockerfile-dev

```yaml
build:
  context: ./backend
  dockerfile: dockerfile-dev
```

- Nếu muốn chạy kiểu tương tác -it thì có thể thêm

```yaml
stdin_open: true
tty: true
```

- Bên docker file thì đối với volume có thể kiểu dùng:
  - `./backend` chứ ko cần nguyên cái absolute path dài ngoằng
- Có thể thêm:
  - Giá trị `depends_on:` là child của các container để biết là khi nào reload cái nào thì cái này sẽ tự reload
- Viết xong để chạy: `docker-compose up`
- `docker-compose down` để mà khi chạy xong có thể xóa hết container
  - Mặc định là nếu ko có -v thì các volume sẽ không được remove
- `docker-compose build` dùng khi mà muốn build thôi ko muốn chạy
