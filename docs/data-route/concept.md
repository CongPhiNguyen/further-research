# Data và các vấn đề liên quan
## Hadoop là gì

- Tham khảo:
  - [TopDev Hadoop](https://topdev.vn/blog/hadoop-la-gi/)
- Một apache framework dùng để thực hiện việc phát triển ứng dụng phân tán, lưu trữ, quản lý các tập dữ liệu lớn. Chạy bằng Mapreduce(ứng dụng chia nhỏ thành nhiều phân đoạn và chạy song song trên nhiều node)
- Tính chất:
  - Xử lý dữ liệu khổng lồ, phân tán, băng thông giới hạn?
- Chạy trên yarn
- HDFS: Hadoop distributed file system
  - Hệ thống phân mảnh, tập tin được chia thành nhiều mảng nhỏ
- MapReduce:
  - Sử dụng YARN xử lý dữ liệu lớn

## YARN và NPM khác nhau như thế nào

- Đều là cái dùng để quản lý các package
  - Yarn được tạo bởi Facebook, google, exponent,...
  - Npm được tạo ra trước và dùng để cài yarn, nó có giải quyết vấn đề về internet, package theo 1 kiểu khác.
    - Nó có vấn đề về security, perfomance và consistent
  - yarn giải quyết được cái peer dependence và có offline mode
- Npm được cái có cộng đồng lớn hơn với nhẹ về space hơn so với yarn
- yarn sẽ có vấn đề về native module và node ver5 trở lên có thể không chạy với Yarn?
- Berry??
