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
Đây là 1 đoạn text chứa thông tin của chủ sở hữu tên miền được mã hóa. Thông tin này được gửi đến nhà cung cấp dịch vụ SSL để xác nhận.  
## Sử dụng OpenSSL để gen file CSR sau đó request SSL cho domain tech.training.vietnix.tech  
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
  
Output:
`:~$ ls -l`  
`total 12`  
`-rw-rw-r-- 1 tpaityubun tpaityubun 1017 Jul  1 10:04 tech.training.vietnix.tech.csr`  
`-rw------- 1 tpaityubun tpaityubun 1704 Jul  1 09:57 tech.training.vietnix.tech.key`  
`-rw-rw-r-- 1 tpaityubun tpaityubun  447 Jul  1 10:11 tinphong.md`  
## Pem file là gì ?
PEM (Privacy Enhanced Mail) là tệp chứng chỉ bảo mật được sử dụng để thiết lập kênh liên lạc an toàn giữa máy chủ web và trình duyệt. Nó được mã hóa Base64 và có thể chứa khóa riêng, chứng chỉ máy chủ và/hoặc kết hợp các chứng chỉ khác. Các tệp PEM tương tự như các tệp chứng chỉ .der về cách sử dụng nhưng được lưu trữ dưới dạng văn bản được mã hóa Base64 thay vì dữ liệu nhị phân. Các định dạng tệp chứng chỉ tương tự khác bao gồm các tệp .cer và .crt.  
## Private key ssl là gì ?
Là file mã hoá được sinh ra cùng lúc khi tạo CSR. Để đơn giản, hãy hình dung CRT là phần mã hoá công khai được trình duyệt sử dụng để truy cập đến website của bạn. Vậy khi dữ liệu đến được website sẽ cần chìa khoá để mở khoá thông tin được mã hoá ở CRT.  

## PFX file là gì ? Cách chuyển từ file crt file sang PFX file.
Định dạng PKCS # 12 hoặc PFX là định dạng nhị phân thường được sử dụng để lưu trữ tất cả các phần tử của chuỗi tin cậy, chẳng hạn như chứng chỉ máy chủ, bất kỳ chứng chỉ trung gian nào và khóa riêng tư vào một tệp có thể mã hóa duy nhất.   
PFX chứa một chứng chỉ số ký số (SSL/TLS certificate), chứng chỉ được phát hành bởi một cơ quan chứng thực (Certificate Authority), cùng với khóa riêng tư tương ứng. Thông thường, tệp .pfx được sử dụng để cung cấp thông tin bảo mật cho các kết nối an toàn như HTTPS (HTTP Secure), SMTPS (SMTP Secure), và các dịch vụ khác.  
- Đầu tiên chuyển đổi 2 file .csr và .key sang .crt : `openssl x509 -req -in tech.training.vietnix.tech.csr -signkey tech.training.vietnix.tech.key -out tech.training.vietnix.tech.crt`
- Chuyển file crt sang pfx: `openssl pkcs12 -export -out tech.training.vietnix.tech.pfx -inkey tech.training.vietnix.tech.key -in tech.training.vietnix.tech.crt`  
- 
