# Concept

## Cài đặt:

- Gõ lệnh: `yarn global add @nestjs/cli` hoặc `npm i -g @nestjs/cli`
- Tạo project với `nest new project-name`
- Check thành công `nest -v`
- Chạy: `yarn start:dev`

## Khái niệm:

- Modules trong NestJS:
  - Mỗi ứng dụng phải có ít nhất 1 modules, đó là modules root, nó giúp cho tổ chức các component ok hơn, mỗi modules nên xếp ra 1 folder
  - Các property của Module Decorator:
    - providers: mảng của các provider khả dụng trong 1 modules
    - controllers: mảng của các controller tạo ra ở trong modules
    - exports: Những gì được export để có thể chạy ở modules khác
    - imports: Những modules nào được dùng ở modules này
    - (ý tưởng cũng giống với component trong React)
- Concept của 1 số thành phần quan trọng trong nestjs:
  - Controller:
    - Quản lý việc handle request và trả về response
    - Quản lý các path
    - Route các endpoint: delete, post, get
    - Có thể sử dụng dependency injection

## Command:

- `nest g module tasks` thì nó sẽ tạo 1 cái modules tên là "TasksModule" ở trong thư mục và import vô cái chính luôn,
- `nest g controller tasks` thì nó sẽ tạo 1 cái controller cho task, có thể gắn thêm flag `--no-spec` để nó ko tạo các file test
