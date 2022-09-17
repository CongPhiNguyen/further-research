# Deploy

- Kiểu có thể dùng các dịch vụ của Amazone, Google, Microsoft để deploy
- Có thể dùng AWS EC2 để thực hiện các thao tác
- Expose các port đến WWW, connect SSH, tải docker và run container
- Ko cần dùng đến bind mount và volume

VPC ?

- Kiểu như các bước bắt đầu với
  - Tạo server
  - SSH đến server với key được tạo khi mà tạo server
  - Thực hiện các lệnh:
    - `sudo yum update -y`: Update gói update như đã làm với apt-get update
    - `sudo amazon-linux-extras install docker`: Chạy install với cái amazon 1 cách xịn hơn
    - `sudo service docker start`: Chạy docker
    - Tạo image, có thể up lên docker hub rồi sau đó down xuống từ server
    - Chạy
    - Lấy IP
    - Mở Security group, trong cái inbound rules thêm http với port 80 vào
- Nếu build bằng cạch này thì đòi hỏi mình cũng phải có kiến thức để mà build server sao cho sercurity, firewall và performance ổn nhất.
- Có thể lựa chọn cách build = dịch vụ hỗ trợ sẵn như EC5 để ko phải config quá nhiều.
  - Chọn elastic container service
  - Chọn cái tùy chọn, next next là xong
  - Để update thì up lên dockerhub nếu ban đầu mình chọn link dockerhub
  - Sau đó mình sẽ chọn run new task các kiểu
- Việc run nhiều container:

  - Lấy cảm hứng từ docker-compose chứ không dùng nó được, nghĩa là network đồ các kiểu chỉ cho dùng local
  - Đối với AWS thì có thể deploy cho mỗi cái task khác nhau mỗi cái khác nhau, tất cả nó cùng nằm trên 1 machine nên có thể sử dụng localhost, nhưng mà mấy path đồ thì nên dùng biến môi trường
  - Load balancer?: Tự reload lại khi thấy service chạy ko ổn. Có 1 cái health check path, nếu cái route đó chạy ko ổn thì reload
  - Trên ECS nó cũng có cho thêm volume để có data persit
  - Khi tạo task mới force deployment thì nó sẽ có 2 task giống nhau chạy,cái mới chạy healthy thì cái kia mới stop, chú ý để tránh conflict

- Đối với database container thì:

  - Vấn đề scaling với managing, xử lý performance và đặc biệt là backup, security có thể khá khó khăn
  - Do đó nên xài mongo Atlas các kiểu

- Có nhiều lựa chọn build:

  - Từ repo có dockerfile
  - Từ docker images

- Đối với React thì:

  - Cần bước build khác với chạy bình thường. Do development server không tối ưu và ko dùng để chạy production
  - React dùng node để tạo development server(Kiểu như 1 cái browser) nên nếu ko có dev server mình có thể ko dùng cái image của node, nhưng thực ra vẫn dùng npm install nên không bỏ được
  - Thay `CMD["npm", "start"]` thành `CMD["npm", "run", "build"]` và build theo kiểu multi-stage

- Build kiểu multi-stage là mỗi stage sẽ copy result từ stage trước, hoặc chạy nhiều stage cùng lúc các kiểu. Mỗi lệnh `FROM` sẽ tạo 1 stage, mỗi stage kiểu nó cũng độc lập với nhau, cái đầu xài node để npm còn cái sau xài nginx cũng ok
- `FROM node as build` sau đó ở stage tiếp theo mình sẽ `COPY --from=build /app/build /usr/share/nginx/html`(Này riêng của React, copy cái build vào để mà lấy stage trước chạy tiếp), `EXPOSE 80`, `CMD ["nginx", "-g", "daemon off;"]`
- Thử copy cái code build của React ra và chạy = cái live server thì nó vẫn sống bình thường, chạy ổn luôn
- Nginx chỉ dùng để host thì cũng khá dễ map volume các kiểu cái host cái html đơn giản:
  - Tham khảo ở `https://hub.docker.com/_/nginx`
  - Kết nối front và back thì mỗi cái load balancer có 1 cái thì mình có thể lấy link của nó
  - Có thể build từng stage với option target

## Với Azure:

- Có thể làm theo link này [Docker deploy Azure Tutorial](https://docs.docker.com/cloud/aci-integration/)

- Làm quen với context để mà chạy các kiểu
