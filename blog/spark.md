---
slug: spark-learn
title: Spark
authors: CongPhiNguyen
tags: [spark]
---

# Spark

## Overal

- Khái niệm: là một cái engine xử lý data nhanh và phổ biến
- Sử dụng kiểu divide and conquered
- Có thể kiểu scale được
- 100x nhanh hơn map reduce ở memory, ở disk thì 10 lần? quảng cáo hơi phóng đại, nhưng mà nhanh hơn thật
- DAG Engine(directed acyclic graph) tối ưu hóa cái workflows
- Data Warehouse: Kho dữ liệu để làm cho cái BI
- Spark streaming các kiểu
- Maven??
- Hive??
- HDFS??
- JDBC??
- Pandas??
  - Spark có sẵn 1 số api của cái này
- Về xử lý từ ngữ thì có thể xài regex.
-

## RDD (Resilient Distributed Dataset): dữ liệu phân tán linh hoạt

- Nói chung công việc của mình là load data vô cái RDD sau đó sử dụng nó để call các method để mà tính toán
- Từ cái RDD đó mình sẽ tiến hành transform
  - map, flatmap, filter, distinct, sample,
  - Các phương thức tương tác RDD: union, intersection, substract, cartesian
- Một số RDD action:
  - collect, count, countByValue, take, top, reduce,...
- Spark core có RDD
- Từ dataframe có thể xử lý các hàm của rdd theo kiểu này:
  - `newDf.select('_id').rdd.flatMap(lambda x: x).collect()`
- Giải thích 1 số câu lệnh
  - setMaster("local") để biết là chỉ chạy trên local chứ chưa có cluster
- Key value RDD: có giống Redis không?
  - Kiểu nó giống dictionary trong python?
  - Các hàm: reduceByKey, groupByKey, sortByKey, keys, values
- RDD và DataFrame thì cái nào oke hơn?
  - Map và filter, kiểu xử lý dữ liệu khá giống với kiểu JS
  - collect?
  - Map và Flatmap
- Bên kia group thì bên này reduceByKey các kiểu

## Install

- Cài đặt với môi trường trên anaconda
  - [Chi tiết cài đặt](https://sparkbyexamples.com/pyspark/install-pyspark-in-anaconda-jupyter-notebook/)
  -

## RDD ?

## DataFrame

## Khóa học

- Lấy data từ đâu:
  - [Grouplens](https://grouplens.org/)
- Một vài trang web tham khảo
  - [Movielens](https://movielens.org/) - Này giúp mình chọn phim để xem. Rate càng nhiều thì độ tin cậy càng lớn. Kiểu có thể như là
- Word count, Add các data cùng group vào cùng với nhau

## Fact

- Spark 3 nhanh hơn 17 lần so với Spark 2
- GPU instance support, mất cái thư viện ML nhưng mà mình có thể cài thêm
- Kết hợp với tensorflow
- SparkGraph?? Có cần RedisGraph không?
- Cypher?
- Morpheus?
- Delta Lake?
- ACID

## Job

- Chú ý về việc sử dụng spark với mongoObjectID
  - Cách upsert với mongo

```python
schema1 = StructType([
    StructField("_id",  StructType([StructField("oid", StringType(), True)]), True),
    StructField("name", StringType(), True),
    StructField("subject", StringType(), True),
    StructField("mark", IntegerType(), True)
])

dataAdd = [
    (("6375bbb3cdd46274caae6a32",),"A", "Toán", 110),
]
currentDataAdd = spark.createDataFrame(data = dataAdd, schema = schema1)

currentDataAdd.write\
    .option("uri", "mongodb+srv://phiroud:1@tracking-service.cp1dn0g.mongodb.net")\
    .option("database", "test-spark")\
    .option("collection", "user-mark-12")\
    .format("mongo").mode("append")\
    .save()
```

- Khi tạo dataframe hầu như chỉ lưu schema với cái mongo-spark connector
- Chú ý về cách sử dụng limit trong spark
- Các chuẩn thời gian:
  - iso 8601 và rfc 3339
- Repartition:
  - Khái niệm: increase or decrease the RDD/DataFrame partitions

## Background job

- Spark mongo connector 10

  - Có cái data streaming khác với mongo connector 3
  - Có thể sử dụng cái connect chung như cách mình hay dùng, có thể dụng cả bản 3 và 10
  - [Full doc](https://www.mongodb.com/developer/languages/python/streaming-data-apache-spark-mongodb/)
  -

- Đối với mongo spark connector thì khi mà convert thành schema thì:
  - Lấy 1000 collection đầu tiên để render ra schema
  - Nếu có 1 cái trường có 2 dạng dữ liệu là struct với string thì nó sẽ ưu tiên lấy string
  - Kiểu nó ưu tiên dạng không lỗi

## Reference

- [Document của pyspark](https://sparkbyexamples.com/pyspark/)
