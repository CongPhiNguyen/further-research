---
sidebar_position: 3
---

# Image

## Khái niệm

> Là blueprint, template để mà build cái container

Chứa code và các công cụ bắt buộc

## Layer của image

Mỗi lệnh trong dockerfile khi chạy sẽ tạo ra 1 layer. Nếu ko có gì thay đổi hay mình ignore nó ra thì nó sẽ không chạy lại lệnh tạo layer đó mà dùng cache để tái sử dụng layer đó để run tiếp.
