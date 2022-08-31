# Command

## Cấu trúc lệnh chính

```console
docker OBJECT OPTION COMMAND <ID or name>
```

## Container

- Các command:
  - start, stop
  - dettach: Nếu đang chạy trong attach thì `Ctrl P` + `Ctrl Q`
- Các option
  - `-p <HOST_POST>:<CONTAINERPORT>`
  - `--help` để mà đọc doc luôn
- Docker ps thực ra là process để biết cái nào đang chạy. Có thể viết docker container ls thì kết quả cũng tương tự
- Khi mà start lại thì có thể gắn lại các tag khi chạy lại
- Có thể run với option `--rm` để khi mà cái container chạy xong thì tự xóa
- Copy một file bỏ vào container
  - `docker cp a/. <ContainerID/name>:/anc` (Lựa chọn /. để mà lấy tất cả trong thư mục a) Sau đó copy vào thư mục anc của cái container, vice versa để mà copy qua lại test.
  - Hoặc có thể exec vào rồi thực hiện bash, ls để lấy các thư mục.
  - Có thể export cái container ra thành file tar rồi share
  - `docker exec -it <ContainerID/name> bash` sau đó có thể thực hiện các lệnh ls cd .. gì để mà xem cái cây thư mục. Nói chung việc tương tác lấy file ra cũng khá dễ. Nó là linux, tương tác với bash thay đổi cái file rồi thực hiện với máy host cũng ok. Khi container stop vẫn có thể thực hiện các thao tác copy

-> Do vậy nên có thể extract code từ image

- Đối với trường hợp dotnet lúc trước thì do mình tạo file dll để dotnet run luôn nên là không thể lấy được code

## Image

- inspect: `docker image inspect <ImageID/name>` để xem các layer của image đó và các thông tin khác
- tag
- rm
- có thể ngắn gọn rmi chứ ko cần `docker image rm`
- Tên `name:tag` -> Nên sử dụng để specify version
- push
- Đổi tên = docker tag
- pull thì có thể chỉ gõ build với tên image thôi, nếu ko có local nó tự động lên docker nó down
- Có thể set các biến enviroment với --env

## Volume

- Command shell như sau:

```console
docker run -it -p 5000:5000 -v "C:\CongPhi\CODE\test-docker\controllers:/app/controllers" d70
```

- Thực hiện lệnh trên để mà tạo cái volume `C:\CongPhi\CODE\test-docker\controllers` map với `/app/controllers` từ đó có thể thay đổi cái này mà bên cái container cũng thay đổi luôn
- Kiểm tra đã map được volume hay chưa có thể gõ `docker inspect <containerID/name>` sẽ hiện ra các thông tin, trong đó có thông tin mount

```json
"HostConfig": {
  "Binds": [
      "C:\\CongPhi\\CODE\\test-docker\\controllers:/app/controllers"
  ],
  // ...
}
// ...
"Mounts": [
  {
    "Type": "bind",
    "Source": "C:\\CongPhi\\CODE\\test-docker\\controllers",
    "Destination": "/app/controllers",
    "Mode": "",
    "RW": true,
    "Propagation": "rprivate"
  }
],
```

- Việc mình binding như thế này thì kiểu như nó sẽ override một số folder mà mình đã thực hiện copy bên dockerfile.
- Đối với việc binding thì để tránh bị override như đã nói ở trên có thể tạo anonymous volume. Có thể tạo trong dockerfile hoặc với cmd như `-v 'abc/acc'`. Nói chung tên volume càng dài, tức là nó đi sâu hơn thì nó sẽ lấy cái đó.
- Cái nodemon nó không catch sự kiện save ở host mà nó sẽ catch sự kiện save khi dùng cái vim để mà thay đổi ở bên trong cái container luôn. Khi thay đổi như vậy thì cái mình binding bên ngoài cũng thay đổi.
  -> Để fix cái này thì có thể dùng wsl filesystem để fix tình trạng này, máy mac thì không bị
- Để thực hiện với read-only volume thì có thể

```console
docker run -it -p 5000:5000 -v "C:\CongPhi\CODE\test-docker\controllers:/app/controllers:ro" d70
```

- Thêm :ro để specify là cái volume trong container nó thay đổi thì không ảnh hưởng đến cái file của host
