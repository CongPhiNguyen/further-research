---
slug: elastic-search
title: Elastic Search
authors: CongPhiNguyen
tags: [elastic-search]
---

## Khái niệm

- Thường dùng trong Linux, là một phần của Elastic Stack, bao gồm ElasticSearch, LogStash, X-pack và Kibana.
  - Kibana: Web UI để visual việc search, lấy data từ cái Log, nó có cả IP thời gian các kiểu
  - LogStash: Nơi lấy data thực hiện các mục đích của mình
  - X-pack: một tool monitor về hệ thống, bảo mật
- Tìm kiếm nhanh trong thời gian thực
- Mục đích sử dụng:
  - Ngoài tạo index và search thì nó còn có ứng dụng trong việc xử lý data, structured data hoặc aggregate data
  - Nhanh hơn cả Hadoop, Spark, Flink
  - Có graph để visual và các cái của Machine Learning
-

## Tech

- Công nghệ sử dụng là Java, với Apache Lucene.
- Về cấu trúc:

  - Nhiều node tạo thành 1 hệ thống, khi client truy vấn tới bằng giao thức http thì nó sẽ chạy trong cái node đó và trả về bằng http luôn
  - Mỗi node lưu phân tán data
  - Mỗi dữ liệu lưu ở 1 index, mỗi index có nhiều cái Shard

- Nó sẽ lưu data ko theo hàng cột mà theo một cấu trúc JSON, mỗi cluster gồm nhiều node

## Research

## ES8

- Mất đi document type
- DataStream ổn hơn
- Có mấy package hỗ trợ xử lý ngôn ngữ tự nhiên oke hơn
- Có agent cho azure
- Có vector similarit, knn các kiểu

## Phân tích data

- Có sử dụng kibana để tạo hoặc có thể custom một cái dashboard với ant design

## Get với các câu query

- Tạo index:
  - PUT: `http://localhost:9200/<index_name>?&pretty`
    - Có thể setting một số cái nữa ở trong body
- Khá giống với format của mongodb
- GET: `/<index>/_search`:
  - Ngang cấp với query có thể add `"_source": ["name"]` để mà select các trường cần lấy
  - Match query: Tìm giá trị bằng với mấy trường nhất định

```
  "query": {
    "match": {
      "title": "ABC"
    }
  }
```

- Term query: Tìm kiếm document có trường chứa 1 giá trị nào đó. Kiểu như hỗ trợ tìm kiếm text nhanh hơn

```
{
  "query": {
    "term": {
      "genre": "action"
    }
  }
}
```

- Bool query: Truy vấn kết hợp, giống $and trong mongo

```
{
  "query": {
    "bool": {
      "must": [
        {
          "match": {
            "title": "Naruto"
          }
        },
        {
          "term": {
            "genre": "action"
          }
        }
      ]
    }
  }
}
```

- Range: tìm trong khoảng, có thể dùng "gt", "eq"
- Regex:

```
{
    "query": {
      "regexp": {
        "phone": "[0-9]{11}" // [field name]: "regexp"
      }
    },
}
```

- Tìm với nhiều id:

  - GET `/<index name>/_search`

```
{
  "query": {
    "ids" : {
      "values" : ["1", "6"]
    }
  }
}
```

- Các query:

  - Match Query
  - Multi-Match Query
  - Common Terms Query
  - Query String Query
  - Term Query
  - Terms Query
  - Range Query
  - Exists Query
  - Wildcard Query
  - Regexp Query
  - Prefix Query
  - Fuzzy Query
  - Type Query
  - Ids Query
  - Bool Query
  - Boosting Query
  - Constant Score Query
  - Disjunction Max Query
  - Function Score Query
  - More Like This Query
  - Nested Query
  - Parent Id Query
  - Has Child Query
  - Has Parent Query
  - Match All Query
  - Geo Shape Query
  - Geo Bounding Box Query
  - Geo Distance Query
  - Geo Polygon Query

- Fuzzy search:

```

{
"query": {
"fuzzy": {
"nutshell": {
"value": "relate",
"fuzziness": "AUTO",
"prefix_length": 3
}
}
}
}

```

- Trả về kết quả tương tự như tìm kiếm term dựa trên việc sử dụng khoảng cách Levenshtein.
- Khoảng cách Levenshtein là số bước thay đổi cần thiết để biến một term (string) này thành một term khác. Những thay đổi này có thể gồm:
  - Thay đổi một ký tự.
  - Xóa một ký tự.
  - Chèn một ký tự.
  - Chuyển đổi hai ký tự liền kề.
- Để tìm các term tương tự, fuzzy tạo ra một tập hợp tất cả các biến thể hoặc mở rộng có thể của cụm từ cần tìm kiếm trong một khoảng cách được chỉ định. Truy vấn sau đó trả về kết quả khớp chính xác cho mỗi lần mở rộng.
- Chúng ta có thể config tham số fuzziness của truy vấn.

  - 0, 1, 2: khoảng cách Levenshtein lớn nhất được chấp thuận.
  - AUTO: tự động điều chỉnh kết quả dựa trên độ dài của term

- Này hỗ trợ tính năng tìm kiếm term khá ổn, có thể dùng làm công cụ search
- Có thể sử dụng multi-match với fuzzy search luôn

## Một số câu aggregate

## Xóa document

- DELETE `/<index name>/_doc/id`
- POST `/<index name>/_delete_by_query`

```

{
"query": {
"match": {
"field_name": "abc"
}
}
}

```

## Update document

- Thay đổi document: PUT `/<index name>/_doc/id`

```

{
"field": "data"
}

```

- Xóa và tạo lại document với các thông tin mới: document PUT `/<index name>/_doc/id`

```

{
"field": "data"
}

```

```

```

```

```
