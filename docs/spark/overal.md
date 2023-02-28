# Overal

- Có 1 số api bên pandas
  - Dùng với dataset nhỏ. Nó sẽ không bị chia file và chạy trên 1 node duy nhất
- Khái niệm:
  - Là 1 thư viện chạy python để dùng nó tương tác với spark
  - Chạy với Py4J
- Các tính năng:
  - Tính toán in-memory
  - Phân phối tiến trình dựa trên parallelize
  - Sử dụng với nhiều cái cluster manager như Spark, Yarn, Mesos
  - Fault-tolerant?
  - Immutable
  - Lazy Evaluation
  - Cache & Persistence
  - Tối ưu với DataFrames
  - Có thể sử dụng ANSI SQL
- Lợi ích:
  - Có thể sử dụng realtime với streaming và Kafka nhưng với dữ liệu rất lớn thì thôi, không dùng
  - Có vài thư viện graph đồ nhưng mình cũng không dùng
- Chạy:
  - Trước h chạy standalone chứ không có chạy kiểu cluster
  - Slave - master thì phải cài các thư viện từng con node như từng cái docker mới chạy oke được
  - Dùng chạy cluster thì phải config Mesos, Hadoop Yarn, Kubernetes
- So sánh với Panda thì nó nhanh hơn do nó chạy trên nhiều tiến trình và tối ưu hơn.

## RDD:

- Các operations:
  - Transformations: Trả về 1 RDD khác chứ ko update cái hiện tại, này là lazy operation
    - Ví dụ:
      - flatMap(), map(), reduceByKey(),
      - filter()
      - sortByKey()
  - Actions: Thực hiện tính toán trả giá trị RDD về cho driver
    - Nghĩa là nếu nó trả về giá tị non RDD thì nó là một action
    - Ví dụ:
      - count(), collect(), first(), max(), reduce()

## DataFrames

- Sử dụng với databrick?
- Là một cái collection được phân phối thành các column, tương tự với table trong các database quan hệ và dataFrame trong R, python. Nhưng nó có tối ưu hơn. Có thể được tạo từ các file structured, database, table từ Hive hoặc từ các bảng RDDs
- Để tạo dataFrame thì có thể tạo từ 1 list, có các option Schema các kiểu
  - Tạo bằng createDataFrame()
- df.show() thì nó kiểu tạo Stage? với Job?(under the hood)
- Nó cũng có các operation kiểu transform và actions
- Có thể tạo bằng cách đọc mongo, json, các file csv từ nhiều nguồn

## Sử dụng với Sql

- Được sử dụng nhiều để xử lý với structured columnar data format.
- Nói chung là nó cho phép xài SQL trong cái pyspark(tận dụng những cái đã có từ BigQuery)

```py
df.createOrReplaceTempView("PERSON_DATA")
df2 = spark.sql("SELECT * from PERSON_DATA")
```

- Tạo cái tempView từ nó

## Streaming

- Có thể ko dùng
- Nhưng nó kết nối với socket hay nhiều cái khác để mà có thể sử dụng với realtime

## Partition

- Đối với mongo spark connector có các option:
  - `partitioner.options.partition.field`, field dùng để partition, mặc định là ID
  - `partitioner.options.partition.size`, đơn vị là MB mặc định là 64MB. Là size của các partition
  - `partitioner.options.samples.per.partition`, số sample để tạo sample của partition.
    - `samples per partition \* ( count / number of documents per partition)`

## Others

- DataFrame and SQL
- Streaming?
- MLib?
  - Là 1 cái thư viện
- Hive?
- GraphFrames?
  - Nó là các Api dùng cho GraphX, tận dụng các điểm mạnh của DataFrames
- Resource?
- Parallelize:
  - Dùng với SparkContext
- Stage, Job?
- structured columnar data format?

- Nghiên cứu kỹ:
  - [Github của Spark](https://github.com/spark-examples/pyspark-examples/)
  - Đã đọc: [Trang mở đầu làm quen với spark](https://sparkbyexamples.com/pyspark-tutorial/)
- Ref:
  - https://spark.apache.org/docs/latest/api/python/
  - https://spark.apache.org/docs/latest/rdd-programming-guide.html
