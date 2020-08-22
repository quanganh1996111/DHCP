# Tổng quan về DHCP

## Mục lục

[1. Giới thiệu](https://github.com/quanganh1996111/DHCP#1-gi%E1%BB%9Bi-thi%E1%BB%87u)

[2. Khái niệm](https://github.com/quanganh1996111/DHCP#2-kh%C3%A1i-ni%E1%BB%87m)

[3. Nguyên lý hoạt động của DHCP](https://github.com/quanganh1996111/DHCP#3-nguy%C3%AAn-l%C3%BD-ho%E1%BA%A1t-%C4%91%E1%BB%99ng-c%E1%BB%A7a-dhcp)

[Tài liệu tham khảo](https://github.com/quanganh1996111/DHCP#t%C3%A0i-li%E1%BB%87u-tham-kh%E1%BA%A3o)

## 1. Giới thiệu

DHCP là một giao thức khá là một giao thức phổ biến mà chúng ta hay sử dụng đến để truy cập internet. Hôm nay tôi sẽ giúp mọi người hiểu rõ hơn về DHCP và nguyên lý làm việc của nó ở trong mạng internet.

## 2. Khái niệm

DHCP (Dynamic Host Configuration Protocol) là giao thức cấu hình host động. Nó cung cấp cho máy tính địa chỉ ip ; subnet mask; default gateway. Và nó thường được cấp phát bởi DHPC server được tích hợp sẵn trên router.

DHCP giao tiếp bằng UDP và sử dụng port 67 và 68. DHCP server sử dụng port 67 để nghe thông tin từ các client và sử dụng port 68 để reply thông tin

Ưu điểm khi sử dụng DHCP:

- Tập trung quản trị thông tin cấu hình host.

- Cấu hình động các máy.

- Cấu hình IP cho các máy một cách liền mạch.

- Sự linh hoạt.

- Đơn giản hóa vài trò quản trị của việc cauas hình địa chỉ IP của client.

- Sự linh hoạt.

DHCP làm việc theo mô hình client server và thành phần chính của DHCP là:

- DHCP client: Là thiết bị dùng để kết nối vào mạng.

- DHCP server: Là thiết bị dùng để cấp phát địa chỉ cho client.

<img src="https://imgur.com/u0XlsRr.png">

## 3. Nguyên lý hoạt động của DHCP

Thành phần chính của DHCP bao gồm 4 bản tin:

- DISCOVERY

- OFFER

- REQUEST

- ACK

<img src="https://imgur.com/egy85Ud.png">

Quá trình cấp phát địa chỉ IP trong giao thức DHCP bao gồm các bước sau:

- Bước 1: Khi muốn có địa chỉ IP để truy cập vào internet thì client sẽ tạo ra bản tin DISCOVERY để yêu cầu cấp phát địa chỉ IP

- Bước 2: Client chưa biết địa chỉ chính xác của Server cấp phát địa chỉ cho mình do đó nó sẽ gửi bản tin này dưới dạng broadcast.

- Bước 3: Server sẽ nhận bản tin DISCOVERY của client. Sau khi biết client muốn được cấp địa chỉ IP nó sẽ kiểm tra xem địa chỉ IP nào phù hợp để cấp cho client sử dụng

- Bước 4: Server tạo bản tin OFFER. Gói tin này sẽ lưu trữ thông tin về IP và các thông số cấu hình khác mà client yêu cầu để có thể sử dụng để truy cập internet

- Bước 5: Tất cả các server sẽ gửi bản OFFER dưới dạng broadcast

- Bước 6: Client nhận gói OFFER và nó sẽ chọn ra bản OFFER đầu tiên mà nó nhận được. Nếu không nhận được OFFER nào trong một khoảng thời gian nào đó thì nó sẽ gửi lại DISCOVERY một lần nữa

- Bước 7: Client tạo ra gói REQUEST. Và gửi dưới dạng broadcast tới tất cả các server. Server nào được nhận OFFER sẽ mang ý nghĩa là nó đồng ý nhận IP. Server nào không được nhận OFFER thì thông báo là không nhận OFFER đó

- Bước 8: Server nhận bản tin REQEST. Các server không được nhận OFFER sẽ bỏ qua gói tin này. Gói tin nào được nhận OFFER sẽ nhận và xử lý nó. Nó sẽ kiểm tra sem IP này còn sử dụng được hay không. Nếu còn sử dụng được thì nó sẽ ghi lại thông tin và gửi lại gói tin PACK cho client. Còn nếu không thì nó sẽ gửi lại PNAK để quay lại bước 1.

## Tài liệu tham khảo

https://blog.cloud365.vn/ccna/dhcp-tong-quan/