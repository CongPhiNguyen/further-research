---
sidebar_position: 1
---

## ForEach

Kiểu như có thể thay đổi giá trị của phần tử mảng luôn.

Dường như là ít được sử dụng trong Modern JS. Hầu hết chỉ sử dụng các hàm builtin để làm như map, filter, reduce các kiểu, hoặc for (const/let/var of) hoặc đơn giản là for bình thường

Nó ko có đợi cái index trước hoàn thành xong mới làm index sau nên là có thể khi gọi API theo id có thể bị random vị trí các giá trị

Ngay cả nó cũng kiểu ko async, nghĩa là gọi hàm sau đó thì hàm đó thực hiện xong trước thì nó in trước. Ngay cả khi dùng await trước nó thì nó vẫn ko block bản thân nó lại

## For (const/let/var of)

Chỉ lấy giá trị ra, không thể thay đổi giá trị phần tử mảng. Ủa alo
Có thể lấy index theo cách này:

```js
for (const [index, value] of [1, 2, 3, 4, 5].entries()) {
  console.log(index, value);
}
```

## Một số hàm for khác dùng để fetch dữ liệu

```js
const posts = await Promise.all(ids.map(async (id) => getPost(id)));
// await Promise.allSettled(ids.map(async (id) => getPost(id))); // Thêm trạng thái
console.log(posts);
```
