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

- Nên nhớ sự kỳ diệu của cái phép xor:
  - Tìm số còn thiếu trong mảng từ 1 - > n

```js
var missingNumber = function (nums) {
  let xorRes = 0
  for (let i = 1; i <= nums.length; i++) {
    xorRes ^= i
  }
  for (let i = 0; i < nums.length; i++) {
    xorRes ^= nums[i]
  }
  return xorRes
}
```

- Cố gắng đưa mọi thứ về công thức và sử dụng công thức tính toán sẽ nhanh hơn
- Có nhiều bài phức tạp nếu quy về tính toán dùng công thức thì chỉ mất vài hàm
  - Nên nhớ số ước của 1 chỉ lẻ khi nó là số bình phương
  - Số số bình phương trong khoảng 1 đến n là floor(sqrt(n))
- Đối với một số bài toán kiểu lan truyền bằng cái ma trận thì có thể dùng queue
- Bài toán tìm điểm khác biệt khá phổ biến, có thể dùng sort hoặc objectSearch, cái object đó dùng hashMap thì phải

  - Đây là kỹ thuật mà mình hay sử dụng
  - Iterate qua các key của nó hoặc dùng nó như set

- Phải bắt hết các edge case:
  - Mảng rỗng, mảng 1 phần tử
  - Chia cho 0
- Đối với bài toán Linkedlist thì có thể dùng kỹ thuật 3 node:
  - prev, next, current
    - current để iterate
    - next để lưu tạm cái tiếp theo, lúc cuối cái current sẽ được gán bằng next
    - prev để lưu cái node đã iterate được
  - Có thể dùng bài toán rùa và thỏ để check vòng, một cái iterator chạy nhanh hơn gấp đôi cái còn lại
- Chú ý lúc chia thì nó có ra số không nguyên không, bên JS nó ra số không nguyên
- Khúc tìm một chuỗi có form thành 1 chuỗi khác hoàn toàn được không thì phải dùng objectSearch

1 số hàm utils nên viết

- make object search from array, string
- 1 chuỗi có được form từ chuỗi có sẵn hay không
