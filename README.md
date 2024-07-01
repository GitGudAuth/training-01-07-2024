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
Email Address []:phongdattin@gmail.com  

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:           
An optional company name []:  


