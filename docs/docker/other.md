# Other

## Các trường hợp cần sự tương tác

- Tương tác với API HTTP: tương tác bình thường
- Tương tác với host machine:
  - Nghĩa là tương tác với các port local của máy host
    - Đối với mongo chạy local:
      - Thay thế `mongodb://mongodb:27017/swfavorites` thành `mongodb://host.docker.internal:27017/swfavorites`
    - Hoặc đối với khi chạy 1 số localhost bình thường khác `http://localhost:5000` cũng chỉ cần thay thành `http://host.docker.internal:5000`
    - `host.docker.internal` nó tự động trỏ đến localhost
- Tương tác giữa các container:
  - Có thể tương tác bằng ip do mỗi container sẽ có một ip được assign, có thể inspect container để biết ip đó và truy cập bằng cách thay đổi code kết nối
