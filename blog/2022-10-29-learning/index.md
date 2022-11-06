---
slug: second-learn-blog-post
title: Second Learn Blog Post
authors: CongPhiNguyen
tags: [python, algo]
---

## Algo chạy nodejs

```js
process.stdin.addListener("data", (data) => {
  var n = data.toString()
  for (let i = 0; i < n; ++i) {
    console.log("Hello, World!!!")
  }
})
```

## Python

- In ra thì in các kiểu như js
- Có cộng trừ nhân chia như bình thường(+,-,\*,/,\*\*)
- Chú thích thì thường dùng ide là làm được. Nhưng chính xác là 3 dấu ' hoặc 1 dấu #
- Kiểu dữ liệu: ko cần khai báo kiểu var let const gì luôn, kiểu hosting mà không có đầu
  - Có nhiều kiểu: int, float, bool, str, list, set, dict, tuple, complex
  - Để kiểm tra kiểu: type(`tên biến hoặc value`)
  - Quy cách đặt tên biến cũng giống với JS
- là True và False, nhớ viết hoa
- Operator:
  - String: +,_, in, not in. Tính năng của những cái này cũng từ intituition thôi, + là nối chuỗi, _ là số lần cộng với chính nó. in với not in là toán tử membership, trả về true, false
    - 1 nháy hay 2 nháy cũng được giống với JS.
    - Có các hàm `len()`, `s.lower()`, `s.upper()`, `s.isalnum()`: check xem có toàn chữ và số đúng hay không, `s.isalpha()`: check xem chuỗi có toàn ký tự chữ hay không, `s.isalnum()`: check xem có toàn số hay không, `s.split(c)`: giống y như JS, `" ".join(lst)`: nối nhau cách nhau bởi dấu cách, hay gì tùy mình specify, `s.replace(x,y)`: đổi hết ký tự x thành y
    - Lấy các ký tự của chuỗi thì rất đơn giản:
      - `s[a:b]`: có thể để trông a và b.
        - Lấy 3 ký tự cuối `s[-3:]`, nếu có thêm số 0 đằng sau cùng thì lại khác
        - Lấy 3 ký tự đầu
  - Không thể nối chuỗi với số do không tự convert, ép về với hàm str(`int`)
  - convert từ string sang int thì cứ int() thôi nếu là float thì float()
  - Số:
    - +, -, \* , / (đây là chia bt, chia ra số thực luôn), `//` (đây là chia lấy phần nguyên), % chia lấy phần dư, `**` là lũy thừa, `^` , `|`, xor với or các kiểu
    - Cũng có nhiều cái viết tắt như `%=` hay `/=` các kiểu, một số phép khá lạ như `x>>=1` tương đương với `x=x>>1`
    - So sánh thì có ==, >= các kiểu
    - Toán tử logic: and, or, not chứ ko thể dùng &&, ||, !
    - So sánh có thể dùng is
- Input:
  - `name = input()`
- Print:
  - có thể tách ra, nó sẽ cách nhau = 1 khoảng cách
  - `print("abc", abc)`
  - Hàm so sánh bên này cũng y hệt
- If-else
  ```py
  if condition:
      #
  else:
      #
  ```
  - Các khối lệnh xác định = thụt lề nên không có dấu ngoặc
- Toán tử 3 ngôi:
  ```py
  print ("Both a and b are equal" if a == b else "a is greater than b"
  	if a > b else "b is greater than a")
  ```
  if, elif
- Vòng lặp:
  - `while condition:` Các lệnh được viết trong block ở dưới
  - `for i in range(1,5):`: Chỉ lặp cho một tập hợp cho trước, range trả về 1 tập hợp chứa số từ 1 đến 4
  - `for c in "Codelearn"`
  - Vòng for bên python không có đóng ngoặc
  - break, continue bình thường
- Một số function:
  - `round(a,b)` thì a là số, b là số chữ số thập phân
- List:

  - 1 trong 4 loại collection để mà lưu trữ(List, tuple, Set, Dictionary)
  - Các tính chất:
    - Ordered: Có thứ tự
    - Changable: Có thể thay đổi
    - Allow duplicated: Cho phép trùng
  - Built-in:
    - append: thêm vào cuối
    - `len(lst)`
    - max(lst), min(lst)
    - lst.insert(): thêm 1 phần từ, có index
    - lst.remove(): bỏ 1 phần tử
    - lst.append(): Thêm 1 hoặc nhiều phần tử ở cuối
    - lst.pop():
    - lst.sort():
    - lst.reverse():
    - lst.count(val): đếm số lần val xuất hiện trong list
    - lst.clear(): Xóa hết phần tử
    - Hàm print thì có sẵn như trong js
      - print 1 hàng, print("???", end="")
    - lst = filter(function, lst)
  - Đọc thêm ở: [Python W3School](https://www.w3schools.com/python/python_lists.asp)

- Ví dụ về hàm:
  ```py
  def sum_of_list(lst):
    res = 0
    for i in range(0, len(lst)):
        res+=lst[i]
    return res
  ```
- Về phần biến thì bên đây không có khái niệm scope nên khai báo đâu cũng được
