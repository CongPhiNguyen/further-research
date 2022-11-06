# Aggregate

- Kiểu cũng phải chú ý, nó kiểu như 1 cái chain of responsiblity, cố gắng giảm data phải lọc qua từng bước nhất có thể
- Kiểu mọi thứ nó giống 1 cái pipeline
- Mỗi bước group là một stage
- Nghiên cứu thêm về cursor, tại vì này nó có dùng cursor

- Dùng shell:

```mongosh
db
show collections
```

- Find hay aggregate nó cũng trả về 1 cursor
- Cách stageOperator:
  - `$match`: Tìm kiếm những cái thỏa điều kiện nào đó. Kiểu như tất cả cái document nếu muốn được trả ra thì phải match hết những cái property object mình truyền vào. Kiểu nó là 1 query and or các kiểu
  - `$`
