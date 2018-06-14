# **TÌM HIỂU CƠ BẢN VỀ NETWORKING**
## **Khái niệm:** 
*	Mạng máy tính là tập hợp các máy tính kết nối với nhau dựa trên một kiến trúc nào đó để trao đổi dữ liệu. VD: mạng Internet, mang Ethernet, mạng Lan, mạng không dây….
*	Giúp nhiều người có thể dùng chung 1 phần mềm tiện ích.
*	Chia sẻ tài nguyên với nhau 1 cách dễ dàng.
*	Kết nối với các thành phần, thiết bị khác mà không cần kết nối thủ công.

## **Mô hình xử lý:**
*	Mô hình tập trung (Centralized computing) là toàn bộ các tiến trình xử lý diễn ra ở máy tính trung tâm. Còn các máy khác sẽ kết nối với máy tính trung tâm đóng vai trò như nới nhập xuất dữ liệu.
	**	Ưu điểm: Dễ bảo mật an toàn, dễ sao lưu, dễ diệt virus và chi phí cài đặt thấp vì mọi xử lý hay dữ liệu đều tập trung ở máy  tính trung tâm.
	**	Nhược điểm: Khó đáp ứng được yêu cầu của nhiều ứng dụng, tốc độ truy xuất chậm.
*	Mô hình phân tán (Distributed computing): các máy tính có khả năng hoạt động độc lập, các công việc được tách nhỏ và giao cho nhiều máy tính khác nhau trong mạng thay vì tập trung ở 1 máy tính như mô hình tập trung. Dữ liệu được xử lý cục bộ nhưng có kết nối mạng với nau nên có thể trao đổi dữ liệu và dịch vụ.
	**	Ưu điểm: Truy xuất nhanh, không giới hạn các ưng dụng và chức năng.
	**	Khuyết điểm: Dữ liệu lưu trữ ở nhiều máy khó đồng bộ và sao lưu, rất dễ nhiễm virus.
*	Mô hình cộng tác (Collaborative computing): mô hình gồm nhiều máy tính có thể hợp tác để thực hiện một công việc. Một máy tính có thể mượn năng lực tính toán xử lý của máy tính khác bằng cách chay các chương trình trên các  máy tính nằm trong mạng.
	**	Ưu điểm: Xử lý nhanh và manh, có thể dùng để chạy các ứng dụng đòi hỏi tốc độ xử lý lớn.
	**	Khuyết điểm: giống như mô hình phân tán là dữ liệu khó đồng bộ và sao lưu, khả năng nhiễm virus rất cao.

## **Kiến trúc mạng:** 
	Bao gồm hình trạng(topology) và giao thức (protocol)
*	Hình trạng (topology)
	**	Trục(Bus): dùng một kênh chung để truyền dữ liệu, mỗi máy tính và các thiết bị đầu cuối sẽ được gắn vào đó, mô hình hoạt động theo các liên kết Point-to-Multipoint or Broadcast (quảng bá đến các nút con or nút ngang hàng).
		***	Ưu điểm: Dễ thiết kế và chi phí thấp
		***	Khuyết điểm: tính ổn định kém, 1 nút bị hỏng thì toàn bộ mạng bị ngừng

	**	Vòng(Ring): tín hiệu được truyền đi trên vòng theo một chiều duy nhất. Mỗi trạm của mạng được nối với nhau qua một bộ chuyển tiếp - repeater (bộ kết nối, khuếch đại tín hiệu) có nhiệm vụ nhận tín hiệu rồi chuyển tiếp đến trạm kế tiếp trên vòng - kiểu liên kết point to point giữa các repeater.
		***	Ưu điểm: thiết lập đơn giản, dễ dàng cấu hình, dễ dàng kiểm soát và khắc phục sự cố, tận dụng được tối đa tốc độ đường truyền vật lý.
		***	Khuyết điểm: một trạm hoặc cáp hỏng có thể khiến toàn bộ mạng bị ngừng hoạt động, giao thức truy cập phức tạp.
	**	Sao(Star): gồm 1 máy tính trung tâm và các máy kết nối tới máy tính đó.
		***	Ưu điểm: thiết lập đơn giản, dễ dàng cấu hình, dễ dàng kiểm soát và khắc phục sự cố, tận dụng được tối đa tốc độ đường truyền vật lý.
		***	Khuyết điểm: độ dài đường truyền nối mỗi trạm với thiết bị trung tâm bị hạn chế.

*	Giao thức(protocol): Quy tắc truyền thông( Gửi-Nhận các thông tin)  định nghĩa khuân dạng dữ liệu, thông điệp. VD: TCP,UDP, IP, HTTP,....

## **Mô hình truyền thông tin:** 
	Bao gồm 3 giai đoạn: thiết lập kênh truyền, truyền dữ liệu và giải phóng kênh truyền.
*	Chuyển mạch dữ liệu theo kênh: khi hai trạm cần trao đổi thông tin với nhau thì giữa chúng sẽ thiết lâp một “kênh” cố định và duy trì tới lúc một bên ngắt kết nối. Dữ liệu chỉ được truyền theo con đường cố định này.
*	Kỹ thuật này thường được sử dụng trong các kết nối ATM(Asynchronous Transfer Mode-chế độ truyền không đồng bộ-truyền dữ liệu, âm thanh và hình ảnh số hóa) và Dial-up ISDN(Integrated Services Digital Networks-chỉ truyền dịch vụ thoại và chuyển mạch gói tốc độ thấp).
	**	Ưu điểm: tốc độ truyền được đảm bảo do kênh truyền được dành riêng trong suốt quá trình giao tiếp phù hợp với những ứng dụng đòi hỏi thời gian thực như audio và video.
	**	Nhược điểm: tốn thời gian để thiết lập kênh truyền, hiệu suất sử dụng đường truyền không cao vì không phải lúc nào 2 trạm cũng truyền liên tục.

*	Mạng chuyển mạch thông báo (Message Switching Network): không giống như chuyển mạch kênh, chuyển mạch thông báo không thiết lập kênh truyền mà sử dụng mỗi thông báo là một khối độc lập gồm địa chỉ nguồn và địa chỉ đích. Nó được truyền qua các trạm trong mạng cho đến khi đến được địa chỉ đích, mỗi trạm trung gian sẽ nhận và lưu trữa thông báo cho đến khi trạm kế tiếp sẵn sang để nhận. Ví dụ như dịch vụ thư điện tử (email).
	**	Ưu điểm: quản lý hiệu quả, tăng hiệu quả sử dụng  lưu lượng của kênh truyền bằng cách gán thứ tự ưu tiên cho các thông báo.
	**	Khuyết điểm: Không phù hợp với những ứng dụng thời gian thực và các trạm trung gian đòi hỏi bộ nhớ lớn để lưu trữ các thông báo.

*	Chuyển mạch dữ liệu theo gói: chia các thông báo thành các gói tin có kích thước thay đổi, mỗi gói bao gồm dữ liệu, địa chỉ nguồn, địa chỉ đích và thông tin về các trạm trung gian. Các gói tin đi theo nhiều đường khác nhau.
	**	Ưu điểm: do việc chia nhỏ thành các gói và truyền đi theo nhiều đường khác nhau, các gói tin bị giới hạn độ dài tối đa nên các trạm trung gian có thể lưu thông báo ở bộ nhớ trong mà không phải đưa ra bộ nhớ ngoài nên có thể tận dụng, tăng hiệu quả truyền tin
	**	Khuyết điểm: khó khăn trong việc tập hợp các gói tin tại nơi nhận.

*	Truyền thông hướng liên kết (thiết lập liên kết-truyền dữ liệu-hủy bỏ liên kết)  - TCP và không liên kết (chỉ truyền dữ liệu)-UDP

## **Mô hình phân tâng OSI:**

![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/OSI.PNG)

*	Physical: điều khiển việc truyền tải các bit trên đường truyền vật lý. Nó định nghĩa các đặc tính vật lý như tín hiệu điện, trạng thái đường truyền, phương pháp mã hóa dữ liệu và các loại đầu nối được sử dụng gồm hữu tuyến ( Twisted Pair-Coaxial Cable-Fiber Optics) và vô tuyến không dây (Radio, hồng ngoại, ánh sáng)
*	Sử dụng các tín hiệu rời rạc, điện áp khác nhau để biểu diễn các bit 0 và 1.
*	Data link layer:  Truyền dữ liệu giữa các thành phần kết nối trong mạng bằng cách thêm một header chứa các địa chỉ phần cứng nơi nhận và địa chỉ nguồn của nó.	Bao gồm: đóng gói và địa chỉ hóa,truy cập đường truyền, đưa dữ liệu vào mạng phát hiện và sửa lỗi, kiểm suốt luồng và kiểm soát truy cập đường truyền. Dữ liệu dưới dạng các Frame.
*	Network layer:  Chọn đường, định tuyến gói tin từ nguồn đến đích. Dữ liệu dưới dạng thành nhiều gói Package.
*	Transport layer:  Xử lý việc truyền nhận dữ liệu cho các ứng dụng ( dữ liệu được chia nhỏ thành nhiều Segment bổ sung các thông tin về phương thức vận chuyển để đảm bảo tính bảo mật, tin cậy)
*	Sesion layer: đồng bộ hóa phiên làm việc, check-poit, khôi phục quá trình trao đổi.
*	Presentation layer: cho phép các ứng dụng biểu diễn dữ liệu, mã hóa, nén, chuyển đổi dữ liệu từ tâng ứng dụng về một dạng chung.
*	Application layer: Hỗ trợ các ứng dụng trên mạng, làm việc trực tiếp với người dùng: hình ảnh, văn bản, âm thanh, data….

[Nguồn tham khảo](https://www.digistar.vn/quy-trinh-truyen-goi-tin-trong-mo-hinh-osi/
)

## **Mô hình TCP/IP:**

![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/TCP1.PNG)

** Quá trình đóng gói: **
đi qua mỗi tầng thì gói tin đều được thêm 1 phần header

![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/TCP2.PNG)

![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/TCP3.PNG)

## **Định danh trên Internet:**

![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/dinhdanh.PNG)

*	**Địa chỉ vật lý/ địa chỉ MAC:** sử dụng trong tầng liên kết dữ liệu và để địa chỉ hóa trong các mạng quảng bá.

![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/adresseMac.PNG)

*	**Địa chỉ Ip:** dùng trong giao thức IP - tầng mạng.

## **DNS (Domain Name Sever):**

*	WHAT: là một giao thức của mạng máy tính. Nhiệm vụ cơ bản là biến tên miền thân thiện với người dùng thành địa chỉ IP mà các máy tính có thể nhận dạng lẫn nhau trên hệ thống mạng
![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/DNS.PNG)

*	WHY: giúp thể hiện địa chỉ của những trang web về dạng mà người dùng dễ nhớ và thân thiện hơn

*	**HOW**
![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/DNS2.PNG)

*	WHEN: khi một cá nhân đăng ký một địa chỉ web mới thì các nhà cung cấp dịch vụ sẽ tạo mới 1 địa chỉ IP tương ứng với tên trang web.

## **DHCP( Dynamic Host Configuration Protocol):**

*	What: là giao thức cấu hình động máy chủ cho phép cấp phát tự động cùng với các cấu hình liên quan khác như subnet mask và gateway  mặc định. Nó cung cấp  một databse trung tâm để theo dõi tất cả các máy tính trong cùng hệ thống mạng. Hiện nay DHCP có 2 version: IPv4 và IPv6.
*	WHY: Mỗi thiết bị trên mạng dựa trên TCP / IP phải có một địa chỉ IP unicast duy nhất để truy cập vào mạng và các tài nguyên của nó. Nếu không có DHCP, các địa chỉ IP cho các máy tính hoặc máy tính mới được chuyển từ một mạng con này sang mạng khác phải được cấu hình bằng tay; Địa chỉ IP cho máy tính bị xóa khỏi mạng phải được lấy lại theo cách thủ công.
	Với DHCP, toàn bộ quá trình này được tự động hóa và được quản lý tập trung. Máy chủ DHCP duy trì một tập hợp các địa chỉ IP và thuê một địa chỉ cho bất kỳ máy khách có hỗ trợ DHCP nào khi nó khởi động trên mạng. Bởi vì các địa chỉ IP là động (thuê) thay vì tĩnh (được gán vĩnh viễn), các địa chỉ không còn sử dụng sẽ tự động được trả về pool để tái phân bổ.
*	HOW: DHCP tự động quản lý các địa chỉ IP và loại bỏ được các lỗi có thể làm mất liên lạc. Nó tự động gán lại các địa chỉ chưa được sử dụng. DHCP cho thuê địa chỉ trong một khoảng thời gian, có nghĩa là những địa chỉ này sẽ còn dùng được cho các hệ thống khác.

![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/IP4vsIPv6.PNG)

![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/IP4vsIPv6.2.PNG)

## **IPSEC**

*	Thực hiện mã hóa và xác thực ở lớp mạng. Nó cung cấp một giải pháp an toàn dữ liệu từ đầu cuối đến đầu cuối trong bản thân cấu trúc mạng.

*	Bao gồm  bốn chức năng sau:
	**	Bảo mật ( mã hóa)- Confidentiality: Người gửi có thể mã hóa dữ liệu trước khi truyền chúng qua mạng. Bằng cách đó, không ai có thể nghe trộm trên đường truyền. Nếu giao tiếp bị ngăn chặn, dữ liệu không thể đọc được.
	**	Toàn vẹn dữ liệu - Data integrity: Người nhận có thể xác minh các dữ liệu được truyền qua mạng Internet mà không bị thay đổi. IPSec đảm bảo toàn vẹn dữ liệu bằng các sử dụng checksums.
	**	Xác thực -Authentication: xác thực đảm bảo kết nối được thực hiện và đúng đối tượng. Người nhận có thể xác thực nguồn gốc của gói tin, bảo đảm, xác thực nguồn gốc của thông tin.
	**	Antireplay protection: xác nhận mỗi gói tin là duy nhất và không trùng lặp.

*	Các giao thức sử dụng trong IPSec:

	**	IIP Security Protocol (IPSec)
		***	Authentication Header (AH): cung cấp tính toàn vẹn phi kết nối và chứng thực nguồn gốc dữ liệu cho các  gói dữ liệu IP và bảo vệ chống lại các cuộc tấn công replay.
		***	Encapsulation Security Protocol (ESP): cung cấp tính năng bảo mật, chứng thực nguồn gốc dữ liệu, tính toàn vẹn phi kết nối và dịch vụ chống replay.

	**	Message Encryption
		***	Data Encryption Standard (DES): Được phát triển bởi IBM. DES sử dụng 1 khóa 56-bít, đảm bảo hiệu năng mã hóa cao. DES là một hệ thống mã hóa khóa đối xứng.
		***	Triple DES (3DES): là một biến thể của DES 56-bít. Hoạt động tương tự như DES, trong đó dữ liệu được chia thành các khối 64 bít. 3DES thực thi mỗi khối ba lần, mỗi lần với một khóa 56 bít độc lập. 3DES cung cấp sức mạnh khóa đáng kể so với DES.

	**	Message Integrity (Hash) Functions
		***	Hash-based Message Authentication Code (HMAC) : là một thuật toán toàn vẹn dữ liệu đảm bảo tính toàn vẹn của bản tin. Tại đầu cuối, bản tin và một khóa chia sẻ bí mật được gửi thông qua một thuật toán băm, trong đó tạo ra một giá trị băm. Bản tin và giá trị băm được gửi qua mạng. Hai dạng phổ biến của thuật toán HMAC như sau:
		***	Message Digest 5 (MD5): là một hàm băm để mã hóa với giá trị băm là 128 bít. MD5 biến đổi một thông điệp có chiều dài bất kỳ thành một khối có kích thước cố định 128 bít. Thông điệp đưa vào sẽ được cắt thành các khối 512 bít, thông điệp sau đó được độn sao cho chiều dài của nó chia chẵn cho 512.
		***	Secure Hash Algorithm-1,2 (SHA-1,2): Sử dụng một khóa 160 bít, 224 bít….

	**	Peer Authentication
		***	Rivest, Shamir, and Adelman (RSA) Digital Signutures: là một hệ thống mật mã khóa bất đối xứng. Nó sử dụng một chiều dài khóa là 512 bít, 768 bít, 1024 bít hoặc lớn hơn. IPsec không sử dụng RSA để mã hóa dữ liệu. Chỉ sử dụng RSA để mã hóa trong giai đoạn xác thực ngang hàng.
		***	RSA Encrypted Nonces

	**	Key Management
		***	Diffie-Hellman (D-H)
		***	Certificate Authority (CA)

	**	Security Association
		***	Internet Exchange Key (IKE): IPSec dùng một giao thức thứ ba, Internet Key Exchange (IKE), để thỏa thuận các giao thức bảo mật và các thuật toán mã hóa trước và trong suốt phiên giao dịch.
		***	Internet Security Association and Key Management Protocol (ISAKMP)

[Nguồn tham khảo](https://www.vnnic.vn/ipv6/congnghe/giao-th%E1%BB%A9c-b%E1%BA%A3o-m%E1%BA%ADt-ipsec-trong-ipv6)

## **DNSSec:**

*	Là công nghệ an toàn mở rộng cho hệ thống DNS. Trong đó DNSSEC sẽ cung cấp một cơ chế xác thực giữa các máy chủ DNS với nhau và xác thực cho từng zone dữ liệu để đảm bảo toàn vẹn dữ liệu.
*	Trong khi giao thức DNS thông thường không có công cụ để xác thực nguồn dữ liệu. Trước nguy cơ dữ liệu DNS bị giả mạo và bị làm sai lệch trong các tương tác giữa máy chủ DNS với các máy trạm (resolver) hoặc máy chủ chuyển tiếp (forwarder), công nghệ bảo mật mới DNSSEC đã được nghiên cứu, triển khai áp dụng để hỗ trợ cho DNS bảo vệ chống lại các nguy cơ giả mạo làm sai lệch nguồn dữ liệu. Trong đó DNSSEC sẽ cung cấp một cơ chế xác thực giữa các máy chủ DNS với nhau và xác thực cho từng zone dữ liệu để đảm bảo toàn vẹn dữ liệu.
*	DNSSEC đưa ra 4 loại bản ghi mới:
	**	Bản ghi khóa công cộng DNS (DNSKEY - DNS Public Key): sử dụng để chứng thực zone dữ liệu.
	**	Bản ghi chữ ký tài nguyên (RRSIG - Resource Record Signature): sử dụng để chứng thực cho các bản ghi tài nguyên trong zone dữ liệu.
	**	Bản ghi bảo mật kế tiếp (NSEC - Next Secure): sử dụng trong quá trình xác thực đối với các bản ghi có cùng sở hữu tập các bản ghi tài nguyên hoặc bản ghi CNAME. Kết hợp với bản ghi RRSIG để xác thực cho zone dữ liệu.
	**	Bản ghi ký ủy quyền (DS - Delegation Signer): thiết lập chứng thực giữa các zone dữ liệu, sử dụng trong việc ký xác thực trong quá trình chuyển giao DNS.

*	Ứng dụng DNSSec cho bảo mật hệ thống DNS:
	**	DNSSEC đưa ra khái niệm ký zone (Zone Signing): một zone được ký bao gồm khóa công cộng DNS (DNS Public Key), chữ ký bản ghi tài nguyên (RRSIG), bảo mật tiếp theo (NSEC), và ký chuyển giao (Delegation Signer). Một zone mà không thêm những bản ghi này vào là một zone chưa được ký. Đồng thời DNSSEC đòi hỏi thay đổi định nghĩa của bản ghi tài nguyên CNAME bằng 2 bản ghi chứng thực là bản ghi RRSIG và bản ghi NSEC.

**Thêm bản ghi DNSKEY vào một zone**
*	Để ký một zone, người quản trị zone sẽ tạo một hay nhiều cặp khóa công cộng/dành riêng (public/private), cặp khóa công cộng dùng cho zone chính và khóa riêng để ký cho những bản ghi cần xác thực trong zone. Mỗi zone phải thêm một bản ghi DNSKEY (zone DNSKEY RR) chứa đựng khóa công cộng tương ứng, và mỗi khóa riêng được dùng để tạo bản ghi RRSIG trong zone.
*	Bản ghi chứng thực DNSKEY cho zone phải có bit Zone Key của trường dữ liệu cờ đặt giá trị là 1.  Nếu quản trị zone có ý định ký một zone để chứng thực thì zone chính phải chứa đựng ít nhất một bản ghi DNSKEY để hoạt động như một điểm bảo mật ở trong zone. Điểm bảo mật được dùng cùng với bản ghi DS tương ứng ở zone cha trong hoạt động chuyển giao DNS.

**Thêm các bản ghi RRSIG vào một zone**
*	Với một zone đã được ký bởi bản ghi DNSKEY, thì các bản ghi tài nguyên trong zone đó cần có một bản ghi RRSIG ký xác thực. Một bản ghi tài nguyên có thể có nhiều bản ghi RRSIG kết hợp với nó. Các bản ghi RRSIG chứa chữ ký điện tử kết hợp chặt chẽ với các bản ghi tài nguyên để xác thực cho các bản ghi tài nguyên đó. Đặc biệt, giá trị TTL trong các bản ghi RRSIG với một tên miền sở hữu không giống với giá trị TTL của bản ghi tài nguyên.
*	Trong trường hợp các bản ghi tài nguyên cùng sở hữu một tên miền thì cần kết hợp bản ghi RRSIG với bản ghi NSEC để xác thực, trường hợp này cũng tương tự đối với bản ghi CNAME.
*	Tập bản ghi tài nguyên NS trong zone phải được ký xác thực, khi bản ghi NS là bản ghi chuyển giao từ máy chủ tên miền cha xuống máy chủ tên miền con thì cần kết hợp bản ghi RRSIG với bản ghi xác thực DS. Bản ghi glue cũng cần xác thực bằng RRSIG.

**Thêm bản ghi NSEC vào một zone**
*	Mỗi tên miền sở hữu nhiều hơn 1 bản ghi tài nguyên cùng loại trong một zone hoặc một tập bản ghi NS chuyển giao thì phải có một bản ghi NSEC để xác thực. Trong đó, giá trị TTL nhỏ nhất cho một bản ghi NSEC phải bằng với giá trị TTL trong bản ghi SOA của zone đó.
*	Một bản ghi NSEC và bản ghi RRSIG kết hợp với nó không nhất thiết là bản ghi duy nhất cho bất cứ tên miền sở hữu bản ghi bảo mật nào. Vì thế, qui trình ký không phải tạo bất cứ bản ghi RRSIG hoặc NSEC nào cho những tên miền sở hữu bản ghi mà không sở hữu bất cứ tập bản ghi nào trước khi vùng được ký. Lý do chính là muốn ổn định giữa không gian đã ký và không gian chưa ký của một zone và mong giảm rủi ro đối với những mâu thuẫn trong phản hồi những máy chủ truy vấn đệ qui không được cấu hình bảo mật.
*	Các bản ghi RRSIG hiện diện tại tên miền sở hữu các tập bản ghi mà nó nắm giữ. Các bản ghi NSEC hiện diện tại tên miền sở hữu và còn hiện diện tại điểm chuyển giao của các tên miền con của chúng. Vì thế, bất cứ tên miền nào có một tập bản ghi NSEC sẽ có các bản ghi RRSIG trong vùng được ký.

**Thêm bản ghi DS vào trong một zone**
*	Bản ghi DS thiết lập chứng thực giữa những zone DNS. Một bản ghi DS được biểu diễn cho bản ghi chuyển giao khi vùng con được ký. Bản ghi DS kết hợp với bản ghi RRSIG để chứng thực cho zone được chuyển giao tại máy chủ tên miền cha. Bản ghi DS được khai báo trước , và bản ghi RRSIG khai báo sau giống như khai báo để xác thực cho một bản ghi tài nguyên thông thường.
*	Trường TTL của tập bản ghi DS phải ứng với trường TTL của tập bản ghi NS ủy quyền (có nghĩa là tập bản ghi NS trong cùng vùng chứa tập bản ghi DS). Việc xây dựng một bản ghi DS đòi hỏi phải có hiểu biết của bản ghi DNSKEY tương ứng trong vùng con để đưa ra được các giao tiếp giữa vùng con và vùng cha.

**Những thay đổi đối với bản ghi CNAME**
*	Nếu một tập bản ghi CNAME hiện diện tại một tên miền trong một vùng được ký, sẽ thay thế bằng tập bản ghi RRSIG và NSEC tương ứng trong tên miền đó. Đây là một phiên bản đã được chỉnh sửa của định nghĩa CNAME nguyên gốc. Định nghĩa nguyên gốc của bản ghi CNAME không cho phép bất cứ kiểu nào khác cùng tồn tại với bản ghi CNAME, nhưng một vùng được ký đòi hỏi những bản ghi NSEC và bản ghi RRSIG cho mọi tên miền. Để giải quyết xung đột này, định nghĩa của bản ghi CNAME của hệ thống DNS đã được chỉnh sửa lại để cho phép nó cùng tồn tại với các bản ghi NSEC và bản ghi RRSIG.
*	DNSKEY được thiết lập để tạo khóa công cộng nhằm thực hiện xác thực với các máy chủ DNS khác có cùng khóa công cộng này. Các bản ghi chứng thực RRSIG sử dụng để ký xác thực cho các bản ghi tài nguyên SOA, A, MX… Đối với các bản ghi NS khai báo quyền sở hữu tên miền đối với tên miền gốc thì sử dụng bản ghi NSEC kết hợp với bản ghi RRSIG để xác thực. Đối với các bản ghi chuyển giao từ DNS cha xuống các máy chủ tên miền DNS con thì kết hợp với bản ghi DS với bản ghi RRSIG để xác thực.

*	Mô hình triển khai thực tế:
![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/CNAME.PNG)

## **IGMP**
*	là giao thức truyền thông được sử dụng bởi host và các router liền kề trên mạng IPv4 để thành lập nhóm multicast.
*	IGMP thường được sử dụng trong các ứng dụng mạng tự một đến nhiều điểm như video trực tuyến, trò chơi trực tuyến.
*	Mô hình: 

![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/IGMP.PNG)

*	IGMP hoạt động giữa máy chủ và bộ định tuyến multicast cục bộ . Các Local Multicast Router sẽ thu thập thông tin hữu ích bằng cách quan sát các giao dịch IGMP con. Sau đó các Protocol Independent Multicast (PIM) được sử dụng giữa các bộ định tuyến multicast cục bộ để hướng multicast từ các máy chủ tới cá host đã được đăng ký.
*	Giao thức IGMP được thực hiện trên một máy chủ cụ hể và trọng 1 bộ router. Một máy chủ yêu cầu tới các thành viên trong một nhóm thông qua bộ router cục bộ bằng các router sẽ lắng nghe và định kì gửi các truy vấn thuê bao.
*	Các version:Các trạm con sử dụng IGMP để thông báo việc tham gia vào nhóm multicast với router kết nối trực tiếp với nó. Ðịnh dạng thông điệp IGMP như hình sau:
	**	IGMPv1:
		***	Trường Version dài 4bit mang giá trị 0x1.
		***	Trường Type dài 4 bit xác định loại thông điệp truy vấn.
		***	Type=0x1: thông điệp truy vấn thành viên Membership Query.
		***	Type = 0x2: thông điệp báo cáo thành viên Membership Report.
		***	Trường Unused dài 8 bit không sử dụng nên mang giá trị 0x00.
		***	Trường Checksum dài 16bit dùng để kiểm tra lỗi header.
		***	Trường Group Address dài 32 bit chứa địa chỉ nhóm multicast.

	**	IGMPv2:	
		***	Trường Type dài 8 bit, mỗi giá trị trường Type ứng với mỗi lại thông điệp:
		***	Type = 0x11: thông điệp truy vấn thành viên Membership Query. Nó dùng để xác định nhóm nào trên mạng có thành viên hoạt động và cụ thể là những thành viên nào.
		***	Type = 0x12 thông điệp báo cáo thành viên Membership Report Version 1.
		***	Type = 0x16 thông điệp báo cáo thành viên Membership Report Version 2.
		***	Type = 0x17 thông điệp rời khỏi nhóm Leave Group.
		***	Trường Maximum Response Time áp dụng cho thông điêp Membership Query. Nó chỉ ra thời gian lớn nhất mà trạm con phải chờ trước khi nhận thông điệp hồi đáp Membership Query.
		***	Trường Checksum dài 16bit dùng để kiểm tra lỗi header.
		***	Trường Group Address chứa địa chỉ nhóm. 

## **Proxy**

*	What: có thể hiểu nôm na là một chiếc máy tính đóng vài trò trung gian giữa chiếc máy tính bạn đang sử dụng với toàn bộ môi trường internet bên ngoài. Bên cạnh đó Proxy còn được dùng để lọc, ngăn chặn các website hoặc chính xác hơn là những nội dung website tùy theo nhu cầu.
*	Why:
![alt](https://github.com/Nobita4116/LearnNetwork/blob/master/Network/Proxy.PNG)

## **Firewall: - tầng vận chuyển**

*	What: là một kỹ thuật tích hợp vào hệ thống mạng để chống sự truy cập trái phép nhằm bảo vệ các nguồn thông tin nội bộ và hạn chế sự xâm nhập không mong muốn từ bên ngoài hệ thống. Nó phải được đặt nằm giữa hệ thống mạng LAN local và mạng Internet bên ngoài, đồng thời được yêu cầu luôn chạy nền để có thể bảo vệ hệ thống. Firewall sẽ giám sát dữ liệu trao đổi  giữa máy tính, máy chủ và các thiết bị định tuyến trong hệ thống mạng để kiểm tra xem chúng có an toàn không. Firewal có thể là phần cứng (router) hoặc phần mềm.
	**	Phân loại: 
		***	Dùng để lọc gói tin: khi một gói tin đi qua một tưởng lửa lọc gói thì địa chỉ nguồn và đích của nó, giao thức và số cổng đích sẽ được kiểm tra. Nếu nó không tuân theo tập luật quy tắc tường lửa thì gói này sẽ bị bỏ đi và không được chuyển tới đích.
		***	Firewall kiểm tra trạng thái: cơ chế cũng giống lọc gói tin. Khác ở chỗ là nó duy trì một bảng theo dõi tất cả các kết nối mở. Khi một gói tin mới đến, nó sẽ so sánh thông tin tiêu đề gói tin với bảng trạng thái và xác định xem nó là một phần của một kết nối đã được thiết lập rồi hay chưa. Nếu okie thì gói tin sẽ được thông qua.
		***	Tưởng lửa ứng dụng và proxy: nó cung cấp khả năng kiểm tra kích thước gói tin và phân biệt chúng là yêu cầu , dữ liêu và mã đọc hợp lệ được nguy trang dưới dang yêu cầu hoặc dữ liệu hợp lệ.

*	When: áp dụng với tất cả máy tính. Càng quan trọng thì mức độ bảo mật càng cao.

## **Flat:** 
là một phương pháp thiết kế mạng máy tính nhằm giảm chi phí, bảo trì và quản lý. Nó được thiết kế để giảm số lượng bộ định tuyến và chuyển mạch trên mạng máy tính bằng cách kết nối các thiết bị này với một bộ chuyển mạch duy nhất( Hub mạng or switch) thay vì các công tắc riêng biệt.

## **Overlay:**
là mạng máy tính được xây dựng trên một mạng khác. Các nút trong mạng có thể được coi là kết nối bằng các liên kết ảo hoặc logic, mỗi liên kết tương ứng với một đường dẫn, có thể qua nhiều liên kết vật lý. Ví dụ các hệ thống phân tán như peer to peer hoặc các ứng dụng client-server.

## **Repeater:**
Trong cùng mạng LAN, khoảng các truyền dẫn tín hiệu tối đa là 100m. Do đó khi khách hàng muốn truyền tín hiệu ở một khoảng các xa hơn thì cần một bộ khuếch đại và định thời tín hiệu, giúp tín hiệu có thể truyền dẫn đi xa hơn giới hạn 100m này. Repeater là một thiết bị như trên.

## **Hub:**
có thể được xem là Repeater có nhiều cổng. Khi cấu hình mạng là hình sao thì nó sẽ đóng vài trò là trung tâm của mạng, thông tin vào từ một cổng và sẽ được đưa đến tất cả các cổng khác. Hub có 2 loại là Active Hub (cần nguồn khi hoạt động, dùng để khuếch đại tín hiệu) và Smart Hub( Active Hub + chip có khả năng tự động dò lỗi).

## **Bridge:**
là một thiết bị dùng để ghép nối 2 hoặc nhiều mạng mạng khác nhau để tạo thành một mạng lớn duy nhất. 

## **SWITCH:**
là một Bridge có nhiều cổng. Switch có thể liên kết được nhiều Segment lại với nhau. Ngoài ra Switch còn có một khả năng khác là tạo mạng Lan ảo (VLAN) nhằm tăng hiệu quả của việc sử dụng hệ thống mạng LAN thông qua việc tăng tính bảo mật, khai thác tối đa lợi ích sử dụng của các cổng.


## **GATEWAY:** 
*	What: là bộ có thể chuyển đổi giao thức của một mạng máy tính thành một giao thức khác thông qua đó kết nối các mạng có giao thức khác nhau lại với nhau.
*	When: các mạng có giao thức kết nối khác nhau thì không thể  kết nối với nhau.
*	Where: tầng 4 hoặc cao hơn ở mô hình OSI- tích hợp ở router.

## **NAT:**
*	What: làm việc như một router, công việc là chuyển tiếp các gói tin giữa những lớp mạng khác nhau trên nhưng mạng lớn (subnet).
	**	Phân loại: 
		***	Static NAT ( chuyển từ một private sang public ip),
		***	Dynamic ( chuyển toàn bộ từ private sang public Ip) 
		***	Overload NAT (bảo gồm cả 2 loại trên.

*	How: NAT sử dụng IP của chính nó làm IP công cộng cho mỗi máy con (client) với IP riêng. Khi một máy con thực hiện kết nối hoặc gởi dữ liệu tới một máy tính nào đó trên internet, dữ liệu sẽ được gởi tới NAT, sau đó NAT sẽ thay thế địa chỉ IP gốc của máy con đó rồi gửi gói dữ liệu đi với địa chỉ IP của NAT. Máy tính từ xa hoặc máy tính nào đó trên internet khi nhận được tín hiệu sẽ gởi gói tin trở về cho NAT computer bởi vì chúng nghĩ rằng NAT computer là máy đã gởi những gói dữ liệu đi. NAT ghi lại bảng thông tin của những máy tính đã gởi những gói tin đi ra ngoài trên mỗi cổng dịch vụ và gởi những gói tin nhận được về đúng máy tính đó (client).

*	When: với những máy tính mà không cùng trên một lớp mạng thì sẽ không có kết nối trức tiếp với nhau vì vậy sẽ không thể trao đổi thông tin với nhau. Vì vậy cần có một router để chuyển tiếp qua lại giữa những router này.

*	Where: tầng Network.

## **QoS: ( Quality of Service)**

*	What: là khả năng giúp cho việc truyền dữ liệu với thời gian tối thiểu và những ứng dụng truyền thông đa phương tiền thời gian.Ví dụ QoS trên router Draytek cho phép người dùng điều khiển được sự lưu thông qua cổng hay máy chủ. Sự lưu thông xuyên qua router sẽ được phân loại vào trong bốn lớp truyền thông, mỗi lớp có độ ưu tiên riêng.

*	When: áp dụng với những vấn đề đòi hỏi thời gian thực, tốc độ lớn và độ chính xác.

*	Where: thực hiện ở 2 tầng Datalink và Network

*	How: 
	**	Cấu trúc Best-Effort: dữ liệu đi vào mạng đều tuân theo quy tắc FIFO.Không có sự đối xử nào của QoS đối với dữ liệu
	**	Cấu trúc Guaranteed Services: dữ liệu đi qua mạng được dành riêng 1 băng thông chắc chắn cho dữ liệu. Thực hiện thông qua cơ chế RSVP và CBWFQ của QoS.
	**	Cấu trúc Differentiated Services: dữ liệu đi vào mạng được phân loại thành các lớp khác nhau để phân loại cách đối xử của mạng đối với dữ liệu. Thực hiện thông qua các tool QoS là PQ, CQ, WFQ và WRED.


Routing:
What: (định tuyến) là cách mà hệ thống tìm đường đi từ mạng này tới mạng khác. Thông tin về định tuyến có thể được cập nhật tự động từ các router khác hoặc do người quản trị chỉ định cho router. Như vậy router là thiết bị có vai trò kết nối, định tuyến và vận chuyển dữ liệu từ mạng này sang mạng khác. Gồm có 2 loại: hardwave router và softwave router.
How: Sử dụng các thuật toán định tuyến.
		Thuật toán vector khoảng cách: Distance vector routing protocol
		Thuật toán liên kết trạng thái: Link state routing protocols
		Thuật toán định tuyến State state tối ưu hóa: OLSR
		Giao thức vector đường dẫn: sử dụng để định tuyến giữa các miền.
Phân loại:
		Định tuyến tĩnh: sử dụng ở các mạng nhỏ có thể sử dụng bảng định tuyến thử công được cấu hình- mạng di động công cộng.
		Định tuyến động: xây dựng bảng định tuyến dựa trên thông tin được thiện bằng các giao thức định tuyến ở mô hình mạng lớn và topo mạng phức tạp.
Where: sử dụng ở tầng Network.






