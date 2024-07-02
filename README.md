# SSL
## SSL là gì ?
SSL được viết tắt từ Secure Sockets Layer, đây là một tiêu chuẩn của công nghệ bảo mật, truyền thông mã hóa giữa trình duyệt và máy chủ web server. SSL hoạt động và đảm bảo rằng những dữ liệu được truyền tải giữa máy chủ và trình duyệt của bạn đều được toàn vẹn, riêng tư và bảo mật.  
## Có bao nhiêu cách chứng thực SSL ?
Có 5 cách chứng thực SSL
- Domain Validation – DV SSL: là chứng chỉ xác thực tên miền dành cho các website cá nhân với khả năng mã hóa cơ bản.  
- Organization Validation – OV SSL: là chứng chỉ xác thực dành cho các tổ chức và doanh nghiệp có độ tin cậy cao.  
- Extended Validation – EV SSL: là loại chứng chỉ xác thực mở rộng, có độ tin cậy cao nhất thường được sử dụng cho các doanh nghiệp và tổ chức đang hoạt động.   
- Wildcard SSL: dành cho các website có nhu cầu sử dụng SSL cho nhiều subdomain khác nhau. Đặc biệt, Wildcard SSL Certificate khác với các loại SSL thông thường là có thể chạy cho nhiều subdomain khác nhau và không bị giới hạn và chỉ cần một chứng chỉ SSL duy nhất.  
- Subject Alternative Names – SANs SSL: Đây là loại chứng chỉ được thiết kế cho các ứng dụng Communication của Microsoft Exchange server, Microsoft Office Communications, Lync và cũng là giải pháp tiết kiệm cho Web Hosting và QA Testing.
## CSR file dùng làm gì trong quá trình tạo SSL
CSR là từ viết tắt của cụm từ Certificate Signing Request là một văn bản chứa thông tin của chủ sở hữu tên miền được mã hóa từ máy chủ. Bạn cần phải tạo CSR trước khi gửi yêu cầu chứng thực tới nhà cung cấp CA (Certificate Authority) để tạo ra một chứng thực SSL.
## Sử dụng OpenSSL để gen file CSR sau đó request SSL cho domain tech.training.vietnix.tech  
```
openssl req -new -newkey rsa:2048 -nodes -keyout tech.training.vietnix.tech.key -out tech.training.vietnix.tech.csr  
.+...+..+......+..........+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*...+......+...+....+...+........+....+......+.....+.+.....+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*.......+.............+...+............+..+.+..+.........+..........+...+........+...+......+.+...+......+..............+.+........+.......+...+..+......+.......+..+.............+......+.....+.+........+......................+.........+..............+......+....+..+......+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
..........+...+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*.....+......+....+..............+.+..+............+.+......+......+.....+....+...+.....+......+.+.........+..+...+....+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++*.+...............+.........................+...+..+....+........+.....................+....+...+..+............+.+........+............+....+.........+...............+.........+..+...+.+......+...+...+..+......+....+..+.+..+......+.......+..+...+...+....+...+..+.............+........+......+......+.......+..+..................+.+..+....+......+...+......+........+.+......+...+.....+...+....+...+.................+.+..+...+...................+...........+....+...+......+............+.....+...+......+.........+.+.........+...............+..+....+........+................+.....+....+..+.........+.+.....+...+......+....+.....+............+.+...+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
-----  
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.  
-----  
Country Name (2 letter code) [AU]:VN   
State or Province Name (full name) [Some-State]:Vietnam  
Locality Name (eg, city) []:Ho Chi Minh City  
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Vietnix  
Organizational Unit Name (eg, section) []:Tech  
Common Name (e.g. server FQDN or YOUR name) []:Training  
Email Address []:p**tin@gmail.com  

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:           
An optional company name []:  
```  
Output:
```
:~$ ls -l 
total 12   
-rw-rw-r-- 1 tpaityubun tpaityubun 1017 Jul  1 10:04 tech.training.vietnix.tech.csr  
-rw------- 1 tpaityubun tpaityubun 1704 Jul  1 09:57 tech.training.vietnix.tech.key
```     
### Kiểm tra lại file .csr  
```:~$ openssl req -text -noout -verify -in tech.training.vietnix.tech.csr  
Certificate request self-signature verify OK  
Certificate Request:  
    Data:  
        Version: 1 (0x0)   
        Subject: C = VN, ST = Some-State, L = Ho Chi Minh city, O = Vietnix, OU = Tech, CN = Training  
        Subject Public Key Info:  
           Public Key Algorithm: rsaEncryption  
                Public-Key: (2048 bit)  
                Modulus:  
                    00:a9:08:a0:c4:ab:25:d1:fe:af:ab:35:05:33:58:  
                    69:2c:e5:03:ac:9d:d2:e2:d6:23:f6:1e:a5:28:41:  
                    ea:d9:2c:09:36:b9:69:a1:46:c0:f7:ae:4b:a0:8e:  
                    2b:f0:2f:2e:c8:5b:89:ad:6d:18:3c:9b:f7:75:9d:  
                    dc:66:63:f9:88:98:de:95:61:5f:81:43:c9:06:c1:  
                    5f:60:51:4a:56:5d:ad:10:d4:0c:42:23:d1:cb:c0:  
                    eb:24:07:89:3c:05:5e:77:00:41:97:08:a5:3b:e3:  
                    4b:70:d4:d3:d4:2c:e1:1e:ad:a0:bf:9f:5b:4d:97:  
                    7a:6e:a5:de:72:dd:a3:de:2e:7c:c9:1c:ea:7f:20:  
                    af:00:95:c5:20:5d:03:3c:3b:c5:f7:95:47:3d:14:  
                    0e:03:77:ee:ef:e6:c5:15:9c:3a:dc:7a:dc:ba:cd:  
                    19:37:ee:74:cf:23:0d:6c:55:e2:79:c1:4e:ec:1b:   
                    12:43:c5:8e:08:b6:73:bd:79:bc:dd:4d:ae:78:f5:  
                    9b:d4:95:ef:05:90:32:5b:ec:3d:36:18:c7:12:3c:  
                    93:2b:8e:d7:f7:3f:40:7b:8f:29:4d:a2:16:4a:8a:  
                    92:66:16:c4:f3:5d:d1:4a:d0:c8:3c:ce:4f:62:a4:  
                    e2:2f:29:dc:10:91:f9:d9:23:d6:4e:c8:f5:eb:8c:  
                    be:6b  
                Exponent: 65537 (0x10001)  
        Attributes:  
            (none)  
            Requested Extensions:  
    Signature Algorithm: sha256WithRSAEncryption  
    Signature Value:  
        68:9d:3b:45:b3:20:8b:a1:98:ad:ce:d1:56:13:40:28:3e:c2:  
        e1:43:b5:0b:22:de:56:ad:59:da:e9:1f:4c:15:f5:35:a6:1e:  
        0d:98:2d:19:e1:1e:dc:11:70:f3:41:5e:ca:80:80:5a:05:ab:  
        90:44:7f:ba:da:cc:2d:ac:07:d8:ad:1b:71:47:74:c0:ef:2f:  
        d2:18:8a:13:a6:26:18:00:85:24:33:ae:27:2b:73:d5:60:19:  
        73:b2:32:92:03:64:20:7f:a9:d3:41:9e:c8:d1:8a:ad:e8:1b:  
        5e:29:c0:bb:81:c8:3c:86:75:da:12:0e:7b:50:68:fa:9a:bc:  
        bb:ed:a0:56:4c:30:6d:76:52:4d:22:bb:f3:e1:59:5e:e2:09:  
        c1:37:78:f6:a1:c9:7b:ef:a3:03:38:4a:35:31:7a:ae:a8:6f:  
        f8:66:d1:c1:ba:a0:c0:74:90:46:ee:a9:8d:30:cd:ec:32:d1:  
        58:f3:6b:e4:5b:82:80:f1:fd:a9:45:dc:5b:71:a3:63:d5:af:  
        4c:30:40:dd:9b:3b:df:28:2b:bd:a7:7d:0d:5e:72:73:5f:73:  
        ec:f1:b4:69:03:24:ee:7b:5a:14:74:0d:9e:c3:c0:4f:8a:1b:  
        05:f3:cd:0b:03:62:2b:c0:c2:97:3f:d5:33:6a:ec:d1:12:85:  
        3a:04:ef:ea
```  
## Pem file là gì ?
PEM (Privacy Enhanced Mail) là tệp chứng chỉ bảo mật được sử dụng để thiết lập kênh liên lạc an toàn giữa máy chủ web và trình duyệt. Nó được mã hóa Base64 và có thể chứa khóa riêng, chứng chỉ máy chủ và/hoặc kết hợp các chứng chỉ khác. Các tệp PEM tương tự như các tệp chứng chỉ .der về cách sử dụng nhưng được lưu trữ dưới dạng văn bản được mã hóa Base64 thay vì dữ liệu nhị phân. Các định dạng tệp chứng chỉ tương tự khác bao gồm các tệp .cer và .crt.  
Tạo file .pem bằng file .csr và .key  
```openssl x509 -req -sha256 -days 365 -in tech.training.vietnix.tech.csr -signkey tech.training.vietnix.tech.key -out tech.training.vietnix.tech.pem
Certificate request self-signature ok  
subject=C = VN, ST = Some-State, L = Ho Chi Minh city, O = Vietnix, OU = Tech, CN = Training
```  
## Private key ssl là gì ?
Là file mã hoá được sinh ra cùng lúc khi tạo CSR. Để đơn giản, hãy hình dung CRT là phần mã hoá công khai được trình duyệt sử dụng để truy cập đến website của bạn. Vậy khi dữ liệu đến được website sẽ cần chìa khoá để mở khoá thông tin được mã hoá ở CRT.   
## PFX file là gì ? Cách chuyển từ file crt file sang PFX file.
PFX là định dạng nhị phân thường được sử dụng để lưu trữ tất cả các phần tử của chuỗi tin cậy, chẳng hạn như chứng chỉ máy chủ, bất kỳ chứng chỉ trung gian nào và khóa riêng tư vào một tệp có thể mã hóa duy nhất.   
PFX chứa chứng chỉ số (SSL/TLS certificate), chứng chỉ được phát hành bởi một cơ quan chứng thực (Certificate Authority), cùng với khóa riêng tư tương ứng. Thông thường, tệp .pfx được sử dụng để cung cấp thông tin bảo mật cho các kết nối an toàn như HTTPS (HTTP Secure), SMTPS (SMTP Secure), và các dịch vụ khác.  
Cách tạo file PFX:  
- Đầu tiên chuyển đổi 2 file .csr và .key sang .crt : `openssl x509 -req -in tech.training.vietnix.tech.csr -signkey tech.training.vietnix.tech.key -out tech.training.vietnix.tech.crt`
- Chuyển file crt sang pfx: `openssl pkcs12 -export -out tech.training.vietnix.tech.pfx -inkey tech.training.vietnix.tech.key -in tech.training.vietnix.tech.crt`
- Hoặc chuyển file .pem sang pfx:
```openssl pkcs12 -export -out tech.training.vietnix.tech.pfx -inkey tech.training.vietnix.tech.key -in tech.training.vietnix.tech.pem  
Enter Export Password:
Verifying - Enter Export Password:
```
# Domain
## Domain là gì ?
Domain (hay tên miền) là địa chỉ độc nhất của một website trên Internet, hoạt động giống như một “ngôi nhà ảo” chứa đựng toàn bộ nội dung và thông tin của trang web. Thay vì phải ghi nhớ dãy số phức tạp của địa chỉ IP, người dùng có thể dễ dàng truy cập website bằng cách nhập tên miền vào trình duyệt.  
Các thành phần của tên miền:
<pre>
  .----------------------------------- protocal (ftps, http, https)
  |        .-------------------------- subdomain (tên miền phụ)
  |        |       .------------------ Second level Domain
  |        |       |    .------------- Top level Domain
  |        |       |    |     .------- page-path
  |        |       |    |     | 
https://host247.vietnix.vn/webmail
</pre>
## Các trạng thái của domain
| Trạng thái | Ý nghĩa |
| :--- | :--- |
| OK / active | Tên miền hoạt động |
| addPeriod | Vừa đăng ký tên miền |
| autoRenewPeriod | Thời gian tự động gia hạn tên miền |
| inactive | Tên miền đã được đăng ký nhưng Nameserver chưa được liên kết với tên miền |
| pendingCreate | Tên miền chờ được đăng ký |
| pendingDelete | Tên miền hết hạn hoặc chờ được xóa |
| pendingRenew | Tên miền chờ gia hạn |
| pendingRestore | Tên miền hết hạn và chờ gia hạn |
| pendingTransfer | Tên miền chờ chuyển đổi nhà đăng ký |
| pendingUpdate | Tên miền đang chờ cập nhật. |
| redemptionPeriod | Tên miền đã hết hạn và rơi vào trạng thái cần thanh toán phí gia hạn nếu muốn tiếp tục sử dụng. |
| renewPeriod | Tên miền được gia hạn |
| serverDeleteProhibited | Ngăn tên miền bị xóa |
| serverHold | Tên miền không được kích hoạt trong DNS |
| serverRenewProhibited | Tên miền không thể được gia hạn |
| serverTransferProhibited | Trạng thái không cho phép transfer tên miền. |
| serverUpdateProhibited | Trạng thái không cho phép cập nhật tên miền. |
| transferPeriod | Đây là trạng thái cho phép sau khi transfer tên miền thành thông thì nhà đăng ký mới có thể yêu cầu nhà cung cấp xóa tên miền. |  
## Subdomain là gì?
Subdomain là tên miền phụ của tên miền chính (Domain).
Tên miền phụ có thể được sử dụng để tạo trang web mới mà không cần phải mua thêm tên miền mới.  
Mối tên miền phụ có thể được quản lý riêng biệt và điều chỉnh độc lập, cho phép bạn có thể tùy chỉnh cấu hình, thiết lập quyền truy cập và theo dõi hiệu suất của từng phần riêng biệt của trang web  
## Virtual Hosts là gì?
Virtual Host là một dạng lưu trữ mà bạn lưu được nhiều domain khác nhau trên cùng một máy chủ sever.   
# Mail Server
## Tìm hiểu MX Record
MX Record được viết tắt của từ Mail Exchange Record, có nghĩa là record giúp xác định được địa chỉ của một hoặc nhiều mail server đang chịu trách nhiệm xử lý mail cho chính tên miền đó.   
## Tìm hiểu DKIM, SPF, PTR
- DKIM là viết tắt của DomainKeys Identified Mail – một phương thức giúp xác nhận Email thông qua chữ ký số giúp tránh email giả mạo. Một kỹ thuật thường được sử dụng trong lừa đảo và spam email.  
- Sender Policy Framework (SPF) là một kỹ thuật xác thực email được sử dụng để chống lại việc giả mạo email (email spoofing). Việc thiết lập SPF record giúp ngăn chặn những kẻ có mục đích xấu sử dụng domain của bạn để gửi email xấu. Những email này còn được gọi là giả mạo email (email spoofing).  
- Bản ghi PTR (Pointer Record) là một loại bản ghi trong hệ thống DNS được sử dụng để ánh xạ một địa chỉ IP (IPv4 hoặc IPv6) thành một tên miền. Bản ghi PTR hoạt động theo chiều ngược lại so với các bản ghi DNS thông thường: thay vì ánh xạ tên miền thành địa chỉ IP (như trong bản ghi A hoặc AAAA), nó ánh xạ địa chỉ IP thành tên miền.  
# DNS
## DNS là gì ?
DNS hay còn được gọi là Domain Name System là hệ thống phân giải tên miền. DNS là hệ thống cho phép thiết lập tương ứng giữa địa chỉ IP và tên miền trên Internet.  
## Các loại recored DNS
- CNAME Record
- TXT Record
- A Record
- AAAA Record
- MX Record
- SRV Record
- NS Record  
## Nguyên tắc làm việc của DNS
- Khi người dùng truy cập một website, máy tính sẽ gửi yêu cầu đến máy chủ DNS cục bộ để tìm địa chỉ IP của website đó. Máy chủ DNS cục bộ sẽ kiểm tra cơ sở dữ liệu của mình xem có chứa địa chỉ IP của website hay không. Nếu có, sẽ trả về địa chỉ IP cho máy tính của người dùng.
- Quá trình phân giải DNS bao gồm chuyển đổi tên máy chủ (chẳng hạn như www.example.com) thành địa chỉ IP thân thiện với máy tính (chẳng hạn như 192.168.1.1). Một địa chỉ IP được cung cấp cho mỗi thiết bị trên Internet và địa chỉ đó là cần thiết để tìm thiết bị Internet phù hợp. Giống như một địa chỉ đường phố được sử dụng để tìm một ngôi nhà cụ thể.
- Khi người dùng muốn tải một trang web, một bản dịch phải xảy ra giữa những gì người dùng nhập vào trình duyệt web của họ (example.com) và địa chỉ thân thiện với máy cần thiết để định vị trang web example.com.
- Nếu máy chủ DNS cục bộ không có địa chỉ IP của website, nó sẽ hỏi máy chủ DNS gốc. Máy chủ DNS gốc sẽ trả về địa chỉ IP của máy chủ DNS cấp cao nhất cho website.
- Máy chủ DNS cấp cao nhất sẽ trả về địa chỉ IP của máy chủ DNS quản lý website. Máy chủ DNS quản lý sẽ trả về địa chỉ IP của trang web cho máy chủ DNS cục bộ.
- Cuối cùng, máy chủ DNS cục bộ sẽ trả về địa chỉ IP của trang web cho máy tính của người dùng. Máy tính của người dùng sẽ sử dụng địa chỉ IP này để kết nối với website.
## Cách phân giải địa chỉ DNS
- Bước 1: Một người dùng nhập “example.com” vào trình duyệt web và truy vấn trên Internet. Và được nhận bởi DNS Recursive Resolver.
- Bước 2: Resolver sau đó truy vấn một root nameserver DNS (.).
- Bước 3: Sau đó, Root Nameserver phản hồi resolver bằng địa chỉ của máy chủ DNS tên miền cấp cao (TLD) (chẳng hạn như .com hoặc .net), nơi lưu trữ thông tin cho các tên miền của nó. Khi tìm kiếm example.com, yêu cầu ban đầu là hướng tới TLD.com.
- Bước 4: Resovler sau đó thực hiện một yêu cầu tới TLD.com.
- Bước 5: Sau đó, máy chủ TLD phản hồi với địa chỉ IP nameserver của domain example.com.
- Bước 6: Cuối cùng, recursive resolver gửi một truy vấn đến nameserver của tên miền.
- Bước 7: Địa chỉ IP cho example.com sau đó được trả về từ nameserver.
- Bước 8: DNS Resovler sau đó trả lời trình duyệt web bằng địa chỉ IP của tên miền được yêu cầu ban đầu.
- Bước 9: Khi 8 bước tra cứu DNS đã trả về địa chỉ IP cho example.com. Trình duyệt có thể đưa ra yêu cầu cho trang web. Trình duyệt tạo một yêu cầu HTTP đến địa chỉ IP.
- Bước 10: Máy chủ tại IP đó trả về trang web sẽ được hiển thị trong trình duyệt (bước 10).

01/07/2024.
