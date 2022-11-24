# Method

## Repartition và Coalesce

- Repartition là để tăng giảm số RDD và DataFrame partitions còn cái Coalesce chỉ để giảm số partition theo một cách hiệu quả hơn
- Nó phải Shuffle data nên rất tốn kém(thời gian chạy, tài nguyên, bộ nhớ)
