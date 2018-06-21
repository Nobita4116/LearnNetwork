# Tìm hiểu về Software-defined Networking (SDN) và OpenFlow

## 1. Software-defined Networking (SDN)

### 1.1 Định nghĩa SDN.
Software-Defined Networking (SDN) là kiến trúc mạng linh động, dễ dàng quản lý, hiệu quả về chi phí, có khả năng đáp ứng cao, lý tưởng cho các ứng dụng đòi hỏi băng thông lớn và có tính năng động cao. Kiến trúc này tách biệt hai cơ chế đang tồn tại trong kiến trúc mạng hiện tại là cơ chế điều khiển (control plane) và cơ chế chuyển tiếp (dataplane), cho phép phần điều khiển có khả năng lập trình được và hạ tầng bên dưới trở nên trừu tượng với các ứng dụng và các dịch vụ mạng. Các đặc tính trong kiến trúc của SDN:
* Khả năng lập trình trực tiếp: Việc điều khiển network được lập trình trực tiếp bởi nó đã được tách biệt với các chức năng chuyển tiếp
* Nhanh chóng: Việc tách biệt các chức năng điều khiển và chức năng chuyển tiếp cho phép các nhà quản trị linh hoạt trong việc điều chỉnh luồng lưu lượng của network khi có yêu cầu thay đổi
* Quản lý tập trung: Việc điều khiển tập trung được thực hiện bởi SDN Controller(một phần mềm) duy trì khung nhìn toàn cục về mạng
* Việc cấu hình lập trình được: SDN cho phép người quản lý mạng cấu hình, quản lý, thiết lập bảo mật, tối ưu hóa tài nguyên mạng nhanh chóng nhờ có các chương trình hỗ trợ SDN đã tự động hóa, những chương trình đó hoàn toàn có thể tự lập trình được mà không phụ thuộc vào phần mềm.
* ung cấp các tiêu chuẩn mở: Khi triển khai thông qua các tiêu chuân mở, SDN đã đơn gian hóa việc thiết kế mạng và vận hành bởi vì các chỉ dẫn được cung cấp bởi SDN controller thay vì các giao thức hay các thiết bị chuyên biệt của các nhà cung cấp.

### 1.2 Kiến trúc.

![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/OpenSwitch/sdn.jpg)

SDN dựa trên giao thức luồng mở (Open Flow) và là kết quả nghiên cứu của Đại học Stanford và California Berkeley. SDN tách định tuyến và chuyển các luồng dữ liệu riêng rẽ và chuyển kiểm soát luồng sang thành phần mạng riêng có tên gọi là thiết bị kiểm soát luồng (Flow Controller). Điều này cho phép luồng các gói dữ liệu đi qua mạng được kiểm soát theo lập trình. Trong SDN, control plane được tách ra từ các thiết bị vật lý và chuyển đến các bộ điều khiển. Bộ điều khiển này có thể nhìn thấy toàn bộ mạng lưới, và do đó cho phép các kỹ sư mạng làm cho chính sách chuyển tiếp tối ưu dựa trên toàn bộ mạng. Các bộ điều khiển tương tác với các thiết bị mạng vật lý thông qua một giao thức chuẩn OpenFlow. Kiến trúc của SDN gồm 3 lớp riêng biệt: lớp ứng dụng, lớp điều khiển, và lớp cơ sở hạ tầng (lớp chuyển tiếp).
* Lớp ứng dụng: Là các ứng dụng kinh doanh được triển khai trên mạng, được kết nối tới lớp điều khiển thông qua các API, cung cấp khả năng cho phép lớp ứng dụng lập trình lại (cấu hình lại) mạng (điều chỉnh các tham số trễ, băng thông, định tuyến, …) thông qua lớp điều khiển.
* Lớp điều khiển: Là nơi tập trung các bộ điều khiển thực hiện việc điều khiển cấu hình mạng theo các yêu cầu từ lớp ứng dụng và khả năng của mạng. Các bộ điều khiển này có thể là các phần mềm được lập trình.
* Lớp cơ sở hạ tầng: Là các thiết bị mạng thực tế (vật lý hay ảo hóa) thực hiện việc chuyển tiếp gói tin theo sự điều khiển của lớp điểu khiển. Một thiết bị mạng có thể hoạt động theo sự điều khiển của nhiều bộ điều khiển khác nhau, điều này giúp tăng cường khả năng ảo hóa của mạng.

## 2. OpenFlow

Khái niệm SDN đặt ra 2 vấn đề khi triển khai thực tế:
* Cần phần có một kiến trúc logic chung cho tất cả các switch, router và các thiết bị mạng khác được quản lý bởi SDN Controller. Kiến trúc này có thể được triển khai bằng nhiều cách khác nhau trên các thiết bị của các nhà cung cấp khác nhau và phụ thuộc vào nhiều loại thiết bị mạng, miễn là SDN controller thấy được chức năng chuyển mạch thống nhất
* Một giao thức chuẩn, bảo mật để giao tiếp giữa SDN controller và các thiết bị mạng

OpenFlow là tiêu chuẩn đầu tiên, cung cấp khả năng truyền thông giữa các giao diện của lớp điều khiển và lớp chuyển tiếp trong kiến trúc SDN. OpenFlow cho phép truy cập trực tiếp và điều khiển mặt phẳng chuyển tiếp của các thiết bị mạng như switch và router, cả thiết bị vật lý và thiết bị ảo, do đó giúp di chuyển phần điều khiển mạng ra khỏi các thiết bị chuyển mạch thực tế tới phần mềm điều khiển trung tâm. Các quyết định về các luồng traffic sẽ được quyết định tập trung tại OpenFlow Controller giúp đơn giản trong việc quản trị cấu hình trong toàn hệ thống. Một thiết bị OpenFlow bao gồm ít nhất 3 thành phần:

* Secure Channel: kênh kết nối thiết bị tới bộ điều khiển (controller), cho phép các lệnh và các gói tin được gửi giữa bộ điều khiển và thiết bị.
* OpenFlow Protocol: giao thức cung cấp phương thức tiêu chuẩn và mở cho một bộ điều khiển truyền thông với thiết bị.
* Flow Table: một liên kết hành động với mỗi luồng, giúp thiết bị xử lý các luồng thế nào. 

![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/OpenSwitch/open_flow.jpg)