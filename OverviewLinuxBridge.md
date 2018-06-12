#**Tìm hiểu cơ bản về Linux Bridge**
##Khái niệm.
Linux Bridge là một phần mềm được tích hợp vào trong nhân Linux để giải quyết vấn đề ảo hóa phần network trong các máy vật lý. Về mặt logic Linux Bridge sẽ tạo ra một con switcch ảo để cho các VM kết nối đưuọc vào và có thể nói chuyện được với nhau cũng như sử dụng ra mạng bên ngoài.
Mô hình kiến trúc máy tính khi có và không có bridge:
![alt](image/BridgeAndNobridge.png)
Khi không có bridge: hệ điều hành máy tính đươc kết nối trực tiếp với card mạng vật lý (eth0) qua đó kết nối với internet bên ngoài.
Khi có bridge: bridge sẽ đóng vài trò làm 1 con switch ảo ở trong máy tính. Bridge sẽ cần đầu vào là card mạng vật lý (eth0) và tạo ra các port ảo để cung cấp mạng cho hệ điều hành của máy tính (br0) và các máy ảo (eth1).
Một số thuật ngữ đi kèm:
*Port: tương tự cổng của một con switch thật.
*Bridge: tương đương switch layer 2.

## Kiến trúc
![alt](image/Architecture1.png)
![alt](image/Architecture2.png)

Một số thuật ngữ đi kèm:
*Tab/Turn : là các thiết bị hạt nhân mạng ảo, được hỗ trợ hoàn toàn nằm trong phần mềm
*Turn mô phỏng thiết bị tầng network (tầng IP) còn Tab mô phỏng thiết bị tầng Data Link (tầng Ethernet). Như vậy Tun được sử dụng như một bộ định tuyến còn Tab được sử dụng để tạo cầu nối mạng
*VFS (File System Virtual) : là hệ thống chuyển đổi hệ thống tập tin ảo. Nó cho phép các ứng dụng khác truy cập vào các thiết bị lưu trữ cục bộ một cách thống nhất.
*FD (forward data) : giúp chuyển tiếp dữ liệu từ máy ảo tới bridge.

## Một số tính năng khác
STP ( Spanning Tree Protocol) : giao thức chống lặp gói tin trong mạng.
*Tổng quan về IEEE 802.1D:
**Một mạng mạnh mẽ được thiết kế không chỉ đem lại tính hiệu quả cho việc truyền các gói hoặc frame, mà còn phải xem xét thế nào để khôi phục hoạt động của mạng một cách nhanh chóng khi mạng xảy ra lỗi. Trong tầng thứ 3 (network layer), các giao thức định tuyến sử dụng con đường dự phòng đến mạng đích để khi con đường chính bị lỗi thì sẽ nhanh cóng tận dụng con đường thứ 2. Định tuyến tầng 2 cho phép nhiều con đường đến đích để giữ nguyên tình trạng hoạt động của mạng và cũng cho phép cân bằng tải qua nhều con đường.
**Trong tầng thứ 2 ( Datalink layer) - switching hoặc bridging thì không sử dụng giao thức định tuyến và cũng không cho phép các con đường dự phòng, thay vì bridge cung cấp việc truyền dữ liệu giữa các mạng hoặc các port của switch. Giao thức Spanning Tree cung cấp liên kết dự phòng để mạng chuyển mạng lớp 2 có thể khắc phục từ lỗi mà không cần có sự can thiệp kịp thời. STP được định nghĩa trong chuẩn IEEE 802.1D.

*Spannning Tree Protocol là gì và tại sao lại sử dụng nó:
**STP là một giao thức ngăn chặn sự lặp vòng, cho phép các bridge truyền thông với nhau để phát hiện vòng lặp vật lý trong mạng. Sau đó giao thức này sẽ định rõ một thuật toán mà bridge có thể tạo ra một topology luận lý chứa loop-free. Nói cách khác STP sẽ tạo ra một cấu trúc cây của free-loop gồm các lá và các nhánh nối toàn bộ mạng lớp 2.
**Vòng lặp xảy ra trong mạng với nhiều nguyên nhân. Hầu hết các nguyên nhân thông thường là kết quả của việc cố gắng tính toán để cung cấp khả năng dự phòng mà ở đây là một link hỏng or switch bị hỏng trong khi các link và các switch vẫn tiếp tục hoạt động

![alt](image/switch.png)

**Có 2 nguyên nhân chính dẫn đến hiện tượng lặp vòng:
***Do switch gửi Broadcast.
***Do sự sai lệch trong bảng Bridge.
***Multiple Frame copies.

* Các trạng thái của STP
**Mỗi port phải trải qua những trạng thái:
***Disable: port bị shutdown bởi người quản trị.
***Blocking: sau khi port khởi tạo, nó sẽ bắt đầu ở trạng thái block và không thể nhận hay truyền dữ liệu hay thêm địa chỉ Mac vào trong table của nó. Nó chỉ có thể nhận được gói BPDU hay các port khác trong chế độ standby để tránh bridge loop.
***Listen: port chuyển từ trạng thái block sang trạng thái listen. Lúc này port vẫn chưa nhận và chuyển data nhưng có nhận và chuyển BPDU để tham gia quá trình STP. Nếu port đó trở thành root port hay designed port thì nó có thể gửi BPDU sang những switch khác nhưng nếu nó không thành root port hay designed port thì nó trở về trạng thái block.
***Learning: sau khoảng thời gian Forward Delay trong trạng thái listen, port sẽ chuyển sang trạng thái learning. Port có thể gửi và nhận BPDU và có thể học địa chỉ MAC mưới và ghi nó vào trong table của mình.
***Forrwarding: sau khoảng thời gian forward delay ở trạng thái learning, port có thể chuyển sang trạng thái forwarding. Ở trạng thái này, port cso thể nhận và gửi data và gói BPDU, thu thập địa chỉ MAC trong bảng table của nó. Đây là trạng thái với chắc năng đầy đủ của port trong STP.

*Bộ đếm thời gian của STP
**STP có ba bộ đếm thời gian để đảm bảo rằng network hội tụ trước khi bridge loop hình thành:
***Hello time: là khoảng thời gian Configuration BPDU được gửi bởi root bridge. Mặc định là 2 giây.
***Forward delay: là khoảng thời gian switch port chuyển từ trạng thái listening sang trạng thái learning.
***Max( maximum) Age: là khoảng thời gian switch lưu lại BPDP trước khi loại bỏ nó. Trong khi thực hiện STP, mỗi cổng của switch giữ một bản sao của “tốt nhất” BPDU mà nó đã nghe. Nếu các cổng của switch mất liên lạc với nguồn của BPDU, switch các giả sử rằng một sự thay đổi cấu trúc liên kết đã xảy ra sau khi Max Age thời gian trôi qua và do đó, các BPDU được loại bỏ. Mặc định Max Age là 20 giây.

**VLAN: chia switch (do linux bridge tạo ra) thành các mạng LAN ảo, cô lập traffic giữa các VM trên các VLAN khác nhau của cùng một switch.
**FDB (forwarding database): chuyển tiếp các gói tin theo database để nâng cao hiệu năng switch. Database lưu các địa chỉ MAC mà nó học được. Khi gói tin Ethernet đến, bridge sẽ tìm kiếm trong database có chứa MAC address không. Nếu không, nó sẽ gửi gói tin đến tất cả các cổng






