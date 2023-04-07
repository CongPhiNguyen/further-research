---
slug: air-flow
title: Air flow
authors: CongPhiNguyen
tags: [air-flow]
---

## Khái niệm

- Một platform để quản lý schedule, monitor workflow và data pipeline
- Workflow: là một chuỗi các task. chạy khi mình schedule nó chạy hoặc trigger bằng một cách nào đó, thường dùng làm big data
- Trong cái ETL bình thường thì mình sẽ có 1 cái cron Script để thực hiện schedule các kiểu
  - Nếu như vậy thì fail retry như thế nào, xử lý bn lâu schedule hơi thủ công
  - Không check data được, ko check được trường hợp job này xong mà chạy luôn một job nữa
  - Khi chạy nhiều container cũng ko check được
