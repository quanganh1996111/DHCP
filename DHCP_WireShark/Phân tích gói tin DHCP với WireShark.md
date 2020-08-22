# Sử dụng WireShark để phân tích gói tin DHCP

## Mục lục

[1. Bắt gói tin DHCP bằng WireShark](https://github.com/quanganh1996111/DHCP/blob/master/DHCP_WireShark/Ph%C3%A2n%20t%C3%ADch%20g%C3%B3i%20tin%20DHCP%20v%E1%BB%9Bi%20WireShark.md#1-b%E1%BA%AFt-g%C3%B3i-tin-dhcp-b%E1%BA%B1ng-wireshark)

[2. Phân tích gói tin DHCP](https://github.com/quanganh1996111/DHCP/blob/master/DHCP_WireShark/Ph%C3%A2n%20t%C3%ADch%20g%C3%B3i%20tin%20DHCP%20v%E1%BB%9Bi%20WireShark.md#2-ph%C3%A2n-t%C3%ADch-g%C3%B3i-tin-dhcp)

- [DHCP DISCOVER](https://github.com/quanganh1996111/DHCP/blob/master/DHCP_WireShark/Ph%C3%A2n%20t%C3%ADch%20g%C3%B3i%20tin%20DHCP%20v%E1%BB%9Bi%20WireShark.md#dhcp-discover)

- [DHCP OFFER](https://github.com/quanganh1996111/DHCP/blob/master/DHCP_WireShark/Ph%C3%A2n%20t%C3%ADch%20g%C3%B3i%20tin%20DHCP%20v%E1%BB%9Bi%20WireShark.md#dhcp-offer)

- [DHCP REQUEST](https://github.com/quanganh1996111/DHCP/blob/master/DHCP_WireShark/Ph%C3%A2n%20t%C3%ADch%20g%C3%B3i%20tin%20DHCP%20v%E1%BB%9Bi%20WireShark.md#dhcp-request)

- [DHCP ACK](https://github.com/quanganh1996111/DHCP/blob/master/DHCP_WireShark/Ph%C3%A2n%20t%C3%ADch%20g%C3%B3i%20tin%20DHCP%20v%E1%BB%9Bi%20WireShark.md#dhcp-ack)

## 1. Bắt gói tin DHCP bằng WireShark

Để bắt gói tin DHCP bằng WireShark, trước hết ta tiến hành giải phóng IP

`ipconfig /release`

Sau đó ta tiến hành khởi động WireShark quét mạng `Ethernet`, sử dụng filter `bootp` để lọc ra các gói tin DHCP. Để cho WireShark tự động quét, ta tiến hành cấp lại địa chỉ IP mới cho máy

`ipconfig /renew`

Kết quả nhận được:

<img src="https://imgur.com/Gc2Z9Nt.png">

## 2. Phân tích gói tin DHCP

### DHCP DISCOVER

<img src="https://imgur.com/nUawyV9.png">

- Client gửi thông điệp Discover theo hình thức Broadcast.

- IP nguồn 0.0.0.0, IP đích 255.255.255.255.

- Cổng nguồn 68, cổng đích 67.

- Message Type: 1 - Thông điệp yêu cầu.

- Hardware type = 1 : Ethernet.

- Transaction ID : 0xf084c8ea.

- Flags==0 => đều tắt.

- Các địa chỉ IP (Client IP Address, Your IP Address ) đặt mặc định là 0.0.0.0.

- Các option : Type (discover), ClientID, Requested IP Address, host name, vendor classID, parameter request list.

### DHCP OFFER

<img src="https://imgur.com/V4zgVZz.png">

- Message type : 2 - thông điệp phản hồi.

- Địa chỉ IP cấp cho Client: 172.16.2.179

- Địa chỉ IP Server: 172.16.10.5

- Các option : Type(offer), ID server, IP address Lease Time, Subnet Mark, Router, DNS

### DHCP REQUEST

<img src="https://imgur.com/kwPCMGX.png">

- Client gửi thông điệp Discover theo hình thức Broadcast.

- Cổng nguồn 68, cổng đích 67.

- Message Type: 1 - Thông điệp yêu cầu.

- Client IP, Your IP, Next server IP, relay agent IP : đặt về 0.0.0.0

- Các option : Type (resquest), ClientID, Requested IP Address, DHCP serverID, host name, Client fully qualified domain name, vendor classID, parameter request list.

### DHCP ACK

<img src="https://imgur.com/0iCz8Vv.png">

- IP nguồn: 172.16.10.5, IP đích: 255.255.255.255

- Message type : 2 - thông điệp phản hồi.

- Các option : Type (ACK), DHCP serverID, IP address Lease Time, Subnet Mark, Router, DNS.

## Tài liệu tham khảo

https://blog.cloud365.vn/ccna/dhcp-tong-quan/

https://github.com/locvx1234/wireshark_DHCP