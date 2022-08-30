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
