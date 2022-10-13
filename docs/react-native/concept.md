---
sidebar_position: 1
---

# Concept

## Cần kiến thức gì

- Nói chung là cần những kiến thức cơ bản về React
- React là 1 cái library để build UI, dùng cho web, là reactDOM có web support
- Còn ReactNative là 1 collection của ReactComponent, Có nhiều cái APi để tương tác với camera điện thoại các kiểu
- Khi cái ReactNative này nó compile thì nó chỉ compile cái view thôi còn code JS vẫn còn nguyên.
  - Nghĩa là từ cái `<div>` là cái `<View>` thì mình sẽ compile nó sang android.View hay UIView các kiểu
  - Còn cái code JS chứa logic thì nó sẽ chạy trên một cái thread khác được quản lý bởi ReactNative App

## Install

- Có thể dùng ExpoCLI Hoặc ReactNative CLI

  - Nên dùng expo vì nó cung cấp service cho phép chạy đồ các kiểu luôn khá ổn, có app di động đồ để chạy luôn. Đổi qua ReactNative CLI cũng dễ
  - Còn cái kia phải config, ít tính năng, xài camera đồ các kiểu cũng khó hơn cái kia, được cái dễ dàng hơn khi chuyển từ native source

- Các lệnh để chạy show ở đây:
  - [Document](https://reactnative.dev/docs/environment-setup)
  - Lệnh: `yarn create expo-app AwesomeProject` để chạy thì `yarn start` thôi
  - Điện thoại tải expo rồi quét QR là xong
