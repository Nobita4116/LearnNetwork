# Tìm hiểu về Open vSwitch

## ** 1. Open vSwitch là gì ? **
	OpenVSwitch là phần mềm cung cấp các giải pháp ảo hóa network
	- Open vSwitch là phần mềm switch mã nguồn mở hỗ trợ giao thức OpenFlow, sử dụng cho ảo hóa vswitch trong môi trường ảo hóa của server
	- Open vSwitch được sử dụng với các hypervisors để kết nối giữa các máy ảo trên một host vật lý và các máy ảo giữa các host vật lý khác nhau qua mạng.
	- Open vSwitch cũng được sử dụng trên một số thiết bị chuyển mạch vật lý (Ví dụ: switch Pica8)
	- Open vSwitch là một trong những thành phần quan trọng hỗ trợ SDN (Software Defined Networking - Công nghệ mạng điều khiển bằng phần mềm)
	- OpenVSwitch có thể chạy trên các Linux-based virtualization platform (KVM,VirtualBox, Xen, Xen Cloud Platform, XenServer)
	- Tính năng:
		- Hỗ trợ VLAN tagging và chuẩn 802.1q trunking
		- Hỗ trợ STP (spanning tree protocol 802.1D)
		- Hỗ trợ LACP (Link Aggregation Control Protocol)
		- Hỗ trợ port mirroring (SPAN/RSPAN)
		- Hỗ trợ Flow export (sử dụng các giao thức sflow, netflow)
		- Hỗ trợ các giao thức đường hầm (GRE, VXLAN, IPSEC tunneling)
		- Hỗ trợ kiểm soát QoS

## ** 2. Kiến trúc của Open vSwitch **
	
	### ** 2.1 Kiến trúc tổng quan **
	
	![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/OpenSwitch/ovs_arch.jpg)
	- Open vSwitch thường được sử dụng để kết nối các VMs/containers trong một host. Ví dụ như trên OpenStack compute node, nó được sử dụng với vai trò là integration bridge để kết nối các VMs chạy trên Compute node đó. Nó quản lý cả các port vật lý (eth0, eth1) và các port ảo (ví dụ như tap port của các VMs).
	- Ba khối thành phần chính của Open vSwitch được mô tả như trên hình:
		- vswitchd:
			- Là ovs daemon chạy trên user space
			- Công cụ tương tác: ovs-dpctl, ovs-appctl, ovs-ofctl, sFlowTrend
		- ovsdb-server:
			- Là database server của Open vSwitch chạy trên user space
			- Công cụ tương tác: ovs-vsctl, ovsdb-client
		- kernel module (datapath):
			- Là module thuộc kernel space, thực hiện công việc chuyển tiếp gói tin
	
	### ** 2.2 Kiến trúc chi tiết **
	
	![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/OpenSwitch/ovs_detail.png)
	
## ** 3. Các thành phân của Open vSwitch **
	
	### ** 3.1 ovs-vswitchd **
	
		- ovs-vswitchd là daemon của Open vSwitch chạy trên userspace. Nó đọc cấu hình của Open vSwitch từ ovsdb-server thông qua kênh IPC (Inter Process Communication) và đẩy cấu hình xuống ovs bridge (là các instance của thư viện ofproto). Nó cũng đẩy trạng thái và thông tin thống kê từ các ovs bridges vào trong database.
		- ovs-vswitchd giao tiếp với:
			- outside world sử dụng OpenFlow
			- ovsdb-server sử dụng giao thức OVSDB protocol
			- kernel thông qua netlink (tương tự như Unix socket domain)
			- system thông qua abstract interface là netdev
		- ovs-vswitchd triển khai mirroring, bonding và VLANs
		
		![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/OpenSwitch/vswitchd_ovsdb_ofproto.png)
		
	### ** 3.2 ovsdb-server **
		- Là một deamon quản lý và điều khiển bất kỳ số lượng công tắc Open vSwitch nào trên máy tính vật lý.
		- Đối với cơ sở dữ liệu xác định cách mà ovs-vswitchd kết nối với ovsdb-server là đọc file máy (mặc định là unix:/usr/ local/ var/ run / open-vswitch / db.sock. Ovs-switch sẽ truy xuất cẫu hình của  nó từ cơ sở dữ liệu lúc khởi động. Nó sẽ thiết lập các bảng dữ liệu Open vSwitch và sau đó chuyển hoạt động trên mỗi cầu được mô tả trong tập tin đó. Khi cơ sở dữ liệu được cập nhật thì ovs-vswitch tự động cập nhật cấu hình của nó cho phù hợp
		- Sử dụng giao thức quản lý OVSDB để quản lý
		
	### ** 3.3 ovsdb **
		- Nếu như những cấu hình tạm thời ví dụ như flows được lưu trong datapath và vswitchd thì các cấu hình bền vững sẽ được lưu trữ trong ovsdb và vẫn lưu giữ khi sau khi khởi động lại hệ thống. Các cấu hình này bao gồm cấu hình về bridge, port, interface, địa chỉ của OpenFlow controller ()nếu sử dụng),...
		- ovsdb-server cung cấp giao diện RPC(remote procedure call) tới ovsdb. Nó hỗ trợ trình khách JSON-RPC kết nối tới thông qua passive TCP/IP hoặc Unix domain sockets.
		- ovsdb-server chạy hoặc như một backup server hoặc như một active server. Tuy nhiên chỉ có active server mới xử lý giao dịch làm thay đổi ovsdb.
		
		![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/OpenSwitch/ovsdb_tables.jpg)
	
	### ** 3.4 datapath **
		- Module chính chịu trách nhiệm chuyển tiếp gói tin trong Open vswitch, triển khai trong kernelspace nhằm mục đích đạt hiệu năng cao. Nó caches lại OpenFlow flows và thực thi các action trên các gói tin nhận được nếu các gói tin nó match với một flow đã tồn tại. Nếu gói tin không khớp với bất kì flow nào thì gói tin sẽ được chuyển lên ovs-vswitchd. Nếu flow matching tại vswitchd thành công thì nó sẽ gửi gói tin lại cho kernel datapath kèm theo các action tương ứng để xử lý gói tin đồng thời thực hiện cache lại flow đó vào datapath để datapath xử lý những gói tin cùng loại đến tiếp sau. Hiệu năng cao đạt được ở đây là vì thực tế hầu hết các gói tin sẽ match flows thành công tại datapath và do đó sẽ được xử lý trực tiếp tại kernelspace.
		- Phân loại datapath mà Open vSwitch hỗ trợ:
			- Linux upstream: là datapath triển khai bởi module của nhân đi cùng với bản phát hành Linux.
			- Linux OVS tree: là datapath triển khai bởi module của nhân phát hành cùng với cây mã nguồn của Open vSwitch. Một số tính năng của module này có thể không hỗ trợ với các kernel phiên bản cũ, trong trường hợp này, Linux kernel version tối thiểu sẽ được đưa ra để tránh bị biên dịch lỗi
			- Userpace datapath: datapath cho phép xử lý và chuyển tiếp gói tin ở userspace, điển hình là DPDK.
			- Hyper-V: hay còn gọi là Windows datapath

## ** 4. Xử lý gói tin trong Open vSwitch **
	
	![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/OpenSwitch/ovs_packet_flow.jpg)
	
	- Open vSwitch là một phần mềm switch hỗ trợ OpenFlow
	- OpenFlow controller chịu trách nhiệm hướng dẫn cho datapath biết làm sao xử lý các loại gói khác nhau, hay còn gọi là flows. Một flow mô tả hành động mà datapath thực hiện để xử lý các gói tin của cùng một loại như thế nào, hay còn được gọi là action. Các kiểu hành động bao gồm chuyển tiếp tới port khác, thay đổi vlan tag,... Quá trình tìm kiếm flow khớp với gói tin nhận được gọi là flow matching.
	- Nhằm mục đích đạt hiệu năng tốt, một phần của flows được cache trong datapath, và phần còn lại ở vswitchd.
	- Một gói tin đi vào Open vSwitch datapath sau khi nó được nhận trên một card mạng. Nếu gói tin khớp với flow nào đó trong datapath thì datapath sẽ thực thi các actions tương ứng mô tả trong flow entry. Nếu không (flow missing), datapath sẽ gửi gói tin lên ovs-vswitchd và tiến trình flow-matching khác được xử lý tại đây. Sau khi ovs-vswitchd xác định làm sao để xử lý gói tin, nó gửi trả gói tin lại cho datapath cùng với yêu cầu xử lý. Đồng thời, vswitchd cũng yêu cầu datapath cache lại flow để xử lý các gói tin tương tự sau đó.

## ** 5. Các công cụ chính tương tác với Open vSwitch **

	- ovs-vsctl: tiện ích chính sử dụng để quản lý các switch, nó tương tác với ovsdb-server để lưu cấu hình vào database của Open vSwitch. ovs-vsctl thực hiện truy vấn và áp dụng các thay đổi vào database tùy thuộc vào lệnh ta thực hiện. ovsdb-server sẽ nói chuyện với ovs-vswitchd qua giao thức OVSDB. Sau đó, nếu ovs-vsctl áp dụng bất kì thay đổi nào thì mặc định nó sẽ đợi ovs-vswitchd kết thúc việc tái cấu hình lại switch.
	- ovs-appctl: cũng là công cụ để quản lý ovs-vswitchd bênh cạnh ovs-vsctl, nó gửi một số command nội bộ tới ovs-vswitchd để thay đổi một số cấu hình và in ra phản hồi từ ovs-vswitchd. ovs-vswitchd đồng thời cũng lưu lại các cấu hình này vào database bằng việc tương tác với ovsdb-server thông qua Unix domain socket.
	- ovs-dpctl: đôi khi ta cần quản lý dapapath trong kernel trực tiếp mà thậm chí ovsdb-server không chạy, ta có thể sử dụng ovs-dpctl tương tác với ovs-vswitchd để quản lý datapath trong kernelspace trực tiếp mà không cần database.
	- ovsdb-client và ovsdb-tool: khi cần nói chuyện với ovsdb-server để thực hiện một số thao tác với database, ta sử dụng ovsdb-client, hoặc nếu muốn xử lý database trực tiếp không thông qua ovsdb-server thì sử dụng ovsdb-tool.
	- ovs-ofctl và sFlowTrend: Open vSwitch có thể được quản trị và giám sát bởi một remote controller. Điều này lý giải tại sao ta có thể định nghĩa mạng bằng phần mềm (hay Open vSwitch hỗ trợ SDN). Cụ thể hơn, sFlow là giao thức dể lấy mẫu gói tin và giám sát, trong khi OpenFlow là giao thức để quản lý flow table của switch, bridge hoặc device. Open vSwitch hỗ trợ cả OpenFlow và sFlow. Với ovs-ofctl, ta có thể sử dụng OpenFlow để kết nối với switch và thực hiện giám sát và quản trị từ xa. Trong khi đó sFlowTrend không phải là thành phần trong Open vSwitch packet mà là phần mềm độc lập hỗ trợ giám sát sử dụng sFlow.
