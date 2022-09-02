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
  - Ngoài ra thì có thể dùng network, các container trong cùng network kiểu như có thể tương tác với nhau
  - Chỉ cần gán tên của container khác là được:
    - `mongodb://<mongodbOfMine>:27017/swfavorites`
    - `<mongodbOfMine>` là tên container đó
    - Gán network khi run với option --network
  - Ko tương tác trực tiếp mà tương tác qua network

## Notes

- Khi mà chạy 1 cái reactapp thì cần phải có -it để mà ko bị stop ngay lập tức
- Đối với React thì nó chạy trong JS runtime nhưng mà nó sẽ chạy 1 cái development server kiểu như browser chứ nó ko hẳn chạy trên node. Nên nhiều khi mình dockerize nó lại thì nó ko resolve được cái port để get dữ liệu.
- Nghĩa là phải bắt buộc dùng port liên kết với máy như hiện tại chứ ko gán network được.
- Về phần mongodb có thể tham khảo: https://hub.docker.com/_/mongo để kiếm tra volume các kiểu. Ngoài ra còn set username, password khi mà access và mongo. Kiểu mình có thể set với processEnv và dockerfile với việc set biến ENV

## MONGODB

- Các lệnh tương tác với mongo

```powershell
# // ssh into the running container
# // Change container name if necessary
$ docker exec -it mongo /bin/bash
# // Enter into mongo shell
$ mongo
# // Caret will change when you enter successfully
# // Switch to admin database. Dùng admin mới có thể auth được
$> use admin
# admin là tên user, sau đó nhập password
$> db.auth("admin", passwordPrompt())
# // Show available databases
$> show dbs
```
