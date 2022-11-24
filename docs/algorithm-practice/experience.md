# Experience

- Nên tìm giới hạn của bài toán để có thể phân tích ra được giải pháp
  - Bài toán với chuỗi: a-z và A-Z tất cả có 26 ký tự. Từ đó có thể dùng kiểu biến lưu với 26 giá trị để mà kiểm tra
- Sort ở js thì hàm sort phải trả về 1, -1 để so sánh chứ ko trả về true false
- Nim:
  - win: at least 1 move to lose
  - lose: all move to win
- `log_b(a) = log_x(a) / log_x(b)`

- Nên nhớ là js thì sort nó compare các số theo kiểu string, nên là nhiều khi kết quả sort sẽ sai khi 4 được xác định lớn hơn 10
  - Sort số thì phải như này

```js
numArray.sort(function (a, b) {
  return a - b
})

// Hay đơn giản là
nums2.sort((a, b) => a - b)
```

- Nếu check mã tăng dần có thể dùng map để mà lưu giá trị lại, sau đó check giá trị min max(đã lưu lại, sau đó check tất cả các giá trị trong chuỗi, có tăng = (max - min) / n-1 không)
- Xor 2 số bằng nhau thì nó sẽ ra 0, hoặc n cặp số giống nhau vị trí nào cđ xor cũng 0
- Kiểu khi mình tính toán, specify 1 giá trị nào đó thì ko nên if trong vòng lặp
