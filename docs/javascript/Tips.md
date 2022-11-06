# Tips

- Có thể thêm + vào trước để convert chuỗi số thành 1 số
  Ví dụ `+'10' là 10`

- Convert Set cho JS thì có thể dùng spread operator `[...a]`
- Tránh closure đối với một số hàm thì có thể dùng đến tham số thứ 3:
  - Đối với hàm filter
    ```js
    filter(function (element, index, array) {
      /* … */
    })
    ```
