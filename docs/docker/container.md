---
sidebar_position: 2
---

# Container

## Khái niệm

## Quá trình chạy

Khi mà chạy thì nó sẽ không copy code như quá trình build image mà nó sẽ tạo thêm 1 layer với môi trường, phân bố tài nguyên, bộ nhớ để chạy từ code đó.

Khi chạy thì có thể chạy dạng dettach hoặc attach. Attach thì bình thường, nếu không thích thì -d để dettach

Có thể list ra rồi attach thêm 1 cái đang chạy

Có thể lấy tất cả các log bằng cách

```console
docker logs <container ID>
```

có thể thêm option f là follow để mà attach vào luôn

## Ultility Container

- Container bình thường có environment và App, còn ultility container chỉ chứa enviroment thôi. Từ đó mình chạy các lệnh nào đó.
- Kiểu như có thể override lại các lệnh:
  - `docker run -it node` thành `docker run -it node npm init`
- Kiểu mình có thể bind mount các kiểu vào thì khi mình chạy các lệnh bên container có thay đổi file thì bên mình vẫn thay đổi, app vẫn chạy được mà không cần môi trường trên máy host
- Có thể set trước entripoint là npm để mà gõ init với install sau docker run là nó chạy luôn
- Đối với docker-compose thì có thể dùng `docker-compose run` để chạy từng image trong cái docker-compose.yaml. `docker-compose run` nó cũng có các option bt như `docker run`.
- Đối với node thì đơn giản còn với Lavarel và PHP thì nó thật sự hữu dụng
