# Command

## Cấu trúc lệnh chính

```console
docker OBJECT OPTION COMMAND <ID or name>
```

## Container:

- Các command:
  - start, stop
  - dettach
- Các option
  - `-p <HOST_POST>:<CONTAINERPORT>`
  - `--help` để mà đọc doc luôn
- Docker ps thực ra là process để biết cái nào đang chạy. Có thể viết docker container ls thì kết quả cũng tương tự
- Khi mà start lại thì có thể gắn lại các tag khi chạy lại
- Có thể run với option `--rm` để khi mà cái container chạy xong thì tự xóa
- Copy một file bỏ vào container
  - `docker cp a/. <ImageID/name>:/anc` (Lựa chọn /. để mà lấy tất cả trong thư mục a) Sau đó copy vào thư mục anc của cái container, vice versa để mà copy qua lại test.
  - Hoặc có thể exec vào rồi thực hiện bash, ls để lấy các thư mục.
  - Có thể export cái container ra thành file tar rồi share
  - `docker exec -it <ImageID/name> bash` sau đó có thể thực hiện các lệnh ls cd .. gì để mà xem cái cây thư mục. Nói chung việc tương tác lấy file ra cũng khá dễ. Nó là linux, tương tác với bash thay đổi cái file rồi thực hiện với máy host cũng ok. Khi container stop vẫn có thể thực hiện các thao tác copy

-> Do vậy nên có thể extract code từ image

## Image:

- inspect: `docker image inspect <ImageID/name>` để xem các layer của image đó và các thông tin khác
- tag
- rm
- có thể ngắn gọn rmi chứ ko cần `docker image rm`
- Tên `name:tag` -> Nên sử dụng để specify version
- push
- Đổi tên = docker tag
- pull thì có thể chỉ gõ build với tên image thôi, nếu ko có local nó tự động lên docker nó down
