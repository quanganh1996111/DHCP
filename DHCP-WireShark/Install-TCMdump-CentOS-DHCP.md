# Cài đặt Tcpdump trên CentOS 7 và phân tích gói tin DHCP

## Chuẩn bị

- Hai máy CentOS 7.

- Một máy cài tcpdump, một máy đặt dhcp để test.

## Cài đặt Tcpdump

### Bước 1: Cập nhật hệ thống CentOS 7

`yum -y update`

### Bước 2: Cài đặt tcpdump

`yum -y install tcpdump`

## Phân tích gói tin DHCP bằng tcpdump

### Bước 1: Thiết lập giao thức DHCP trên máy Test

<img src="https://imgur.com/QFKyfnr.png">

### Bước 2: Chạy lệnh tcpdump với lựa chọn giao thức DHCP

Ta có thể thêm lựa chọn lưu lại file `dhcpens33.pacp` để lưu lại và phân tách được qua WireShark.

```
[root@localhost ~]# tcpdump -i ens33 -n port 67 and port 68 -w dhcpens33.pcap
tcpdump: listening on ens33, link-type EN10MB (Ethernet), capture size 262144 bytes
```

### Bước 3: Bật lại card mạng cho máy test để nhận DHCP

Card mạng ens33 đã nhận IP 172.16.2.74/20.

<img src="https://imgur.com/zPh33BR.png">

### Bước 4: Kiểm tra file PCAP mà ta vừa lưu

Bản ghi DHCP đầy đủ 4 bản ghi: Discover, Offer, Request, ACK và địa chỉ IP 172.16.2.74

<img src="https://imgur.com/KD3wYmW.png">

Bạn có thể tìm hiểu về cách phân tích gói tin DHCP [tại đây](https://github.com/quanganh1996111/DHCP/blob/master/DHCP_WireShark/Ph%C3%A2n%20t%C3%ADch%20g%C3%B3i%20tin%20DHCP%20v%E1%BB%9Bi%20WireShark.md)

## Tại liệu tham khảo

https://www.hugeserver.com/kb/install-use-tcpdump-capture-packets/

https://news.cloud365.vn/huong-dan-su-dung-wireshark-co-ban/