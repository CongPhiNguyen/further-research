# Main

## Khái niệm:

- JavaScript Superset, phải build ra JS mới chạy được
- Kiểu nó kỹ về loại nên tránh lỗi, check string hay số là báo lỗi luôn

## Syntax:

- `a as HTMLElement` dùng để cast
- const a: `<Type>`
- `function ABC(a: number){}`

### Sử dụng type:

- Các type: number(các số), string(các chuỗi), boolean(chỉ true, false, không có truthy, falsy), object(object của JS), array, tuple, enum. (Những type này không có viết hoa, viết hoa là sai)
- Cái này nó sẽ giúp mình check type trong quá trình phát triển thôi, còn chạy thì logic các kiểu vẫn là JS
- Bình thường nếu bên JS thì có khi phải check type (typeof) để chắc chắn còn bên này thì không

```ts
const a: number = 10
const b: string = "Blue"
const person: {
  name: string
  abc: {
    diff: number
  }
} = {
  name: "King kai",
  abc: {
    diff: 0
  }
}
let c: string[]
const d = [number, string] // Đây là kiểu Tuple
```

- Có vài dạng khá lạ:

  - Tuple: Kiểu mảng mà fix loại với length
  - Enum: Kiểu hay thường gặp, build ra JS thì có vẻ code hơi quằn, có thể gán thêm giá trị cụ thể cho nó

- Có thể dùng union type:
  - `const a: string | number;`
- Có thể đặt type là undefined, biến bt undefined ok nhưng nếu hàm thì phải return;
  - `const b: Function`: check để lỡ gán thì ko gán được cho cái khác
  - Specify hàm và cái return của nó
    - `const b = () => number`
  - Kiểu như đối với hàm callback được pass vô thì nó ko specify được cái giá trị trả về, chỉ khi nào dùng để gán thì nó mới có.

```ts
const cal = (
  a: number | string,
  b: number | string,
  flag: "King" | "Queen"
) => {}
```

Này kiểu chỉ cho phép 2 giá trị "King" và "Queen" được truyền vào

- Khai báo type:
  - `type Combination = number` này là type alias
  - Kiểu unknown khác với any ntn: unknown là gán gì cũng được, nhưng mà ghi nhận type ở lần gán cuối cùng để test còn any thì không
  - Kiểu never hay dùng cho hàm khi hàm nó chỉ dùng để throw error và không có giá trị trả về, hoặc hàm chỉ tạo infinite loop
  -

## Tính năng:

- Những tính năng mà TS thêm:
  - Thêm generic, enum
  - Compile ra chạy được nhiều phiên bản JS
  - Có decorator và có thể kiểu config thêm
- Cụ thể:

  - Check type, check số lượng argument
  - Vẫn cộng các string và số được nhưng mà phải specify loại để biết mình thực sự làm gì
  - Let, const, var vẫn bình thường
  - Có thể ban đầu không gắn type nhưng có gán giá trị type đó, sau này thì ko assign type khác vô được
  - Check các proper của Object có tồn tại không và thông báo nếu như object đó tường minh trong code
  - Specify các object có thể có của object, nest các thứ vẫn oke
  - Vẫn có thể khai báo type không check type bình thường
  - Có thể switch value giữa các union

- TSC:
  - Chạy `tsc app.ts -w` để vừa build file js vừa có thể save để nó build lại chứ ko cần gõ lệnh lại
  - `tsc --init` với `tsc -w` để build file lại trong thư mục hiện tại và chạy
  - Trong file config có thể exclude hoặc include
  - Tùy config mình build được es5 es6 là const let var các kiểu
  - Dấu `!` để nói với ts biết là oke, giá trị này có tồn tại(thường dùng với document querySelection các kiểu)
  - Typescript nó check xem mấy cái route if else của mình để biết null hay không luôn, nghĩa là `a?.vb = 19` còn có thể viết là `if(a) {a.vb=19}`
- Nên đọc thêm 1 số tài liệu:

  - [Config typescript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)
  - [Compiler config](https://www.typescriptlang.org/docs/handbook/compiler-options.html)
  - [Typescript debug](https://code.visualstudio.com/docs/typescript/typescript-debugging)

- Typescript thực chất vẫn build ra JS nên nó có scope các kiểu. Vẫn arrow function, set default bình thường, rest, spread operator cũng oke
- Dùng rest kiểu
  - `const add(...number: number[]){}`
- Object, array destructuring thì vẫn hoạt động bt, khi lấy ra thì nó có cho check nữa
- Từ class, mình build ra object nên kiểu class là blueprint rồi từ đó build ra các instance
- Đối với object đó là key và value còn class thì đó gọi là các field

```ts
class Department {
  name: string
  constructor(n: string) {
    this.name = n
  }
}
const a = new Department("acc")
```

- Nếu mình viết như vầy thì khi in a ra sẽ được 1 Object Department có name là acc
-
