# CommandLine

## Command:

Một số lệnh:

- ls
- cd
- mkdir
- `find <directory to find> <filter>`
  - Một số filter:
    - `-type`: Thiết lập file type: d(directory) f(file)
    - `-name`: Lọc theo name. Có thể nhập đúng còn ko thì a\* nếu chỉ biết ký tự đầu là a
    -
- `cat a.txt`: đọc file bằng command line
- `$(pwd)`: với linux và macOS dùng cái này để mà lấy path hiện tại còn
- `"%cd%"`: lấy path hiện tại với window
- sudo: để mà kích hoạt thì có thể su -
- `apt-get install <package-name>`
- vim:
  - i để bắt đầu insert
  - Esc để thoát insert
  - gõ :qw để thoát vim
- Khi thực hiện các cmd với linux ở trong container thì nên

```console
  su -
  apt-get update
  apt-get install <package>
```

- Mở explorer:

  - `explore.exe <path>`

- Cài wsl thì có thể gõ nó trước rồi thực hiện các lệnh bên linux ok
