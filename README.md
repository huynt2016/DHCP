#DHCP
##Khái niệm
- DHCP – Dynamic Host Configuration Protocol là một giao thức cho phép cấp phát tự động cấu hình IP cho các host trên một mạng LAN.

##Mô hình
- DHCP hoạt động theo mô hình client – server. Trong đó:
<ul>
  <li>DHCP server thực hiện cấp phát IP cho các client.</li>
  <li>DHCP client là các host yêu cầu các địa chỉ IP từ server./li>
  </ul>
  
##Các loại bản tin DHCP
- DHCP Discover: Gói tin Broadcast từ client để tìm kiếm server
- DHCP Offer: Gói tin server phản hồi client với các tham số cấu hình
- DHCP Request: Gói tin từ client đến server xác định, loại bỏ cái khác
- DHCP ACK: Server xác nhận gán 1 ip cho client
- DHCP NAK: Server từ chối yêu cầu từ client
- DHCP Decline: Client phát hiện có vấn đề với ip được server cấp
- DHCP Release: Client gửi một gói DHCP Release đến một server để giải phóng địa chỉ IP và xoá bất cứ thuê bao nào đang tồn tại.

##Cơ chế
http://i.imgur.com/qGxobnV.png

###Bước 1:
Khi client kết nối vào mạng và chưa có IP, nó sẽ gửi broadcast gói tin DHCP Discover (bao gồm địa chỉ MAC và tên client) để tìm kiếm DHCP server trong mạng nội bộ.

###Bước 2:
- Khi DHCP Server nhận được thông điệp Discover từ client, nó hồi đáp unicast về một gói DHCP Offer đến client.
- Gói Offer sẽ đưa ra một cấu hình IP mà server muốn gán xuống cho client. Trong thời gian này server không cấp địa chỉ IP vừa đề nghị cho một client nào khác.

###Bước 3:
- Đến lượt nó, client gửi lên gói broadcast cho DHCP server gói DHCP Request.
- Thông điệp Request của client sẽ cho biết yêu cầu của nó với những thông tin đã được server offer ở bước trước. Điều này giúp cho các gói tin không được chấp nhận sẽ được server thu hồi và cấp cho các client khác.

###Bước 4:
- Cuối cùng, server hồi đáp lại cho client gói DHCP ACK để xác nhận cấu hình IP mà client đã request.

###Lưu ý:
- Mỗi cấu hình IP được cấp phát sẽ chỉ có thời hạn trong một khoảng thời gian nhất định, sau khoảng thời gian này, client phải yêu cầu server cấp phát gia hạn lại cấu hình IP của mình. Trong những lần sau, các thông điệp DHCP được gửi unicast thay vì broadcast như lần cấp phát đầu tiên.
- Tất cả việc trao đổi thông tin giữa một DHCP server và client sẽ sử dụng giao thức UDP tại hai cổng 67 và 68.
- Tất cả các gói tin client gửi đều là broadcast.

##DHCP Header
