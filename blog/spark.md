---
slug: spark-learn
title: Spark
authors: CongPhiNguyen
tags: [spark]
---

# Spark

- Khái niệm: là một cái engine xử lý data nhanh và phổ biến
- Sử dụng kiểu divide and conquered
- Có thể kiểu scale được
- 100x nhanh hơn map reduce ở memory, ở disk thì 10 lần? quảng cáo hơi phóng đại, nhưng mà nhanh hơn thật
- DAG Engine(directed acyclic graph) tối ưu hóa cái workflows
- RDD (Resilient Distributed Dataset): dữ liệu phân tán linh hoạt
  - Nói chung công việc của mình là load data vô cái RDD sau đó sử dụng nó để call các method để mà tính toán
  - Từ cái RDD đó mình sẽ tiến hành transform
    - map, flatmap, filter, distinct, sample,
    - Các phương thức tương tác RDD: union, intersection, substract, cartesian
- Data Warehouse: Kho dữ liệu để làm cho cái BI
- Spark streaming các kiểu
- Maven??
- Hive??
- HDFS??
- JDBC??
- Pandas??
-

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

## Fact

- Spark 3 nhanh hơn 17 lần so với Spark 2
- GPU instance support, mất cái thư viện ML nhưng mà mình có thể cài thêm
- Kết hợp với tensorflow
- SparkGraph?? Có cần RedisGraph không?
- Cypher?
- Morpheus?
- Delta Lake?
- ACID
