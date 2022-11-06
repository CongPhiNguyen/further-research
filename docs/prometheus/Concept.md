# Concept

- Một chương trình kiểu hỗ trợ việc tracking quản lý các service, công cụ monitor server mã nguồn mở, với time series database
- How it works:
  - pull các thông số(metrics) từ các job hay là exporter. Sau đó lưu về database, chạy các rules để xử lý nhu cầu hoặc hiện cảnh báo. Sau 1 thời gian kiểu các thông số sẽ được retrieve. Có thể mình tự đặt
- Download:
  - https://prometheus.io/download/
    - Ở đây nó hiện nhiều exporter thì có thể vô xem, tải về, hoặc kiếm mấy cái ở bên thứ 3 viết ra
    - Phổ biến: snmp exporter
- Chú ý file yaml, có thể copy paste lại nó thiếu dấu cách dấu chấm cái nó không chạy
