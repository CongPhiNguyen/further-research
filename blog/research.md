---
slug: spark-research
title: Research
authors: CongPhiNguyen
tags: [spark]
---

# Research

## Dùng cả hai có sao không

- The new Connector uses a different namespace with a short name, “mongodb” (full path is “com.mongodb.spark.sql.connector.MongoTableProvider”), versus “mongo” (full path of “com.mongodb.spark.DefaultSource”). Having a different namespace makes it possible to use both versions of the connector within the same Spark application! This is helpful in unit testing your application with the new Connector and making the transition on your timeline.
  - [Source](https://www.mongodb.com/developer/languages/python/streaming-data-apache-spark-mongodb/)
  - (Docs) -> Kết nối kafka, cast
- (Coi các log, sẽ thấy các package được add)
-
