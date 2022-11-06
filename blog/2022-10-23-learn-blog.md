---
slug: first-learn-blog-post
title: First Learn Blog Post
authors: CongPhiNguyen
tags: [ttl]
---

## Time to live (TTL)

- Khái niệm: là Time To Live, là thời gian để một data có thể tồn tại trong database, nó giúp mình tự remove 1 số data khi mà data đã quá hạn. Nó là minimum time guaranteed to live.
- Đối với Oracle thì sẽ có boundaries chứ không phải là realtime, có thể mongo vẫn vậy, để mà giảm được thay vì việc lúc nào cũng listen để xóa. Nghĩa là nếu TTL là 1 tiếng thì những data sẽ thêm vào từ 0h đến 0h59p59.999s sẽ được expired ở cột mốc 2h. Nếu cột mốc 1h thì vẫn chưa đủ.
- Nó thay thế cho việc mình phải viết log hay script đồ, hay xóa bằng tay
- Có set và update TTL. Đối với mongo như từng test thì có thể thay = Robot3T khá dễ, thêm xóa sửa oke luôn
- Data expired vẫn còn ở trong database, không query và tính vào static thôi. Sau 1 khoảng thời gian nó sẽ được purge thì lúc đó mới xóa hẳn.
- Mongo xem cái này như 1 cái TTL Index
  - Có thể tạo Index với option expiredAfterSeconds trong eventlog của mongodb
  - Có thể thêm vào các trường chưa có db
  - Hầu hết thường đụng đến đối tượng db
  - Hành vi thực hiện:
    - Xét field expired thì nếu field đó là ngày thì bình thường, còn nếu là mảng thì lấy giá trị ngày nhỏ nhất trong mảng đó
      - Còn nếu trường đó không có ngày thì nó sẽ không expired
    - Khi xóa: Background `mongod` sẽ giải quyết vấn đề này. Khi TTL Thread chạy thì sẽ xóa, nó sẽ chạy trong index build, nên sẽ có delay trong thời gian expired. Này là khi build index chứ không phải timebound
      - Background này chạy sau 60s, chứ ko realtime theo giây, trễ tầm 60s là max
  - Hạn chế trong TTL của mongodb:
    - Ko áp dụng với compound index
    - Trường \_id không xài được TTL
    - Ko xài được trong capped collection vì mongodb ko xóa từ cái này được
    - Ko xài bình thường trong Timeseries được mà phải dùng hàm của nó
    - Để thay đổi time expired phải dùng hàm của nó chứ ko createIndex lại bt được
    - Nếu trường có index mà ko phải TTL thì ko tạo index cho nó được, mình phải thay đổi nó thành index TTL.
- Những platform hỗ trợ
  - Mongo hỗ trợ tốt
  - Có thể là Redis hay trên doc của Oracle cũng có nói

## WiredTiger Cache

- WiredTiger là 1 cái storage Engine mặc định từ mongo 3.2 trở đi. Kiểu như nó cũng tạo checkpoint sau 60s. During checkpoint thì có thể tạo index các thứ
- Language: C, mã nguồn mở
- Memory:
- Journaling:
-

## Xử lý form
- Có nhiều cách như Reactform, formilk

## Tham khảo

- TTL
  - [Oracle Time To Live](<https://docs.oracle.com/cd/E17277_02/html/GettingStartedGuide/timetolive.html#:~:text=Time%20to%20Live%20(TTL)%20is,appear%20in%20any%20database%20statistics>)
  - [MongoDB TTL](https://www.mongodb.com/docs/manual/core/index-ttl/)
- WiredTiger
  - [WiredTiger in MongoDB](https://www.mongodb.com/docs/manual/core/wiredtiger/)
  - [WiredTiger Source](https://source.wiredtiger.com/develop/ex_access_8c-example.html)
