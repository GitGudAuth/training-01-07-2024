# Control Panel
## 1.DirectAdmin
Cây thư mục:  
/home/admin/domains/[example.com]/public_html  
Cây thư mục chính và cấu hìnhnằm ở:  
/usr/local/directadmin  
/usr/local/directadmin/conf/directadmin.conf - file config chính cho dịch vụ directadmin    
/usr/local/directadmin/custombuild/ - thư mục cho dịch vụ custombuild    
/usr/local/directadmin/conf/my.cnf - chi tiết kế nối mysql mặc định cho dịch vụ directadmin    
/usr/local/directadmin/data/user/[username] - cấu hình cho một user  
/var/log/directadmin - vị trí file log của directadmin  
**Port: 2222**  
CLI: không có
## 2.aaPanel
Cây thư mục nằm ở:    
/www/wwwroot - chứa domains folder và source web  
/www/wwwlogs - chứa file log  
/www/server - chứa config các service  
/www/backup - chứa các backup  
**Port: 8888**  
CLI : bt  
## 3.Cyber Panel
Cây thư mục cấu hình nằm ở:  
/usr/local/CyberCP/CyberCP/settings.py - File cấu hình chính  
/usr/local/CyberCP/ - chứa các file data của Cyberpanel  
/home/cyberpanel - một số cấu hình nằm ở đây  
/etc/cyberpanl - tool hỗ trợ  
/home/cyberpanel/error-logs.txt - file log của cyberpanel  
/home/[example.com] - doc root  
**Port: 8090**  
CLI : cyberpanel  
## 4.VestaCP
Cây thư mục nằm ở:  
/home/[user]/conf - file config cho mỗi user/domain  
/usr/local/vestacp/conf/vesta.conf - file config chính  
/usr/local/vesta/data - thư mục data chính  
/home/[user]/web - docroot của web  
**Port: 8083**  
CLI : v-*
## 5.Cpanel
Cây thư mục:  
/var/cpanel/cpanel.conf hoặc /usr/local/cpanel/etc/cpanel.conf  
**Port: 2082,2083(Cpanel); 2086,2087(WHM); 2095,2096(Webmail); 2089(License)**  
  
Cách xem log IP truy cập vào Domain ở user trên Hosting cPanel >> Login user cPanel -> Metrics -> Visitors  
cPanel Vietnix hỗ trợ chạy web source code nào >> PHP, NodeJS, HTML/CSS/Javascript  
Cách hiện file ẩn trong File Manager. >> Login user cPanel -> File Manager -> Settings > Show hidden files  
Phát biểu sai về ưu điểm Jetbackup so với cPanel Backup >>  
Cách chặn truy cập quốc tế đến 1 domain ở user cPanel >> .htaccess  
Cấu hình trỏ domain về NS host179.vietnix.vn ? >> ns1.host179.vietnix.vn ns2.host179.vietnix.vn  
cPanel Vietnix hỗ trợ chạy web source code nào (perl, python, nodejs,...) >> Php, NodeJS, Python  
Cách reload hosting cPanel khi full Number Of Processes tại Vietnix >> cagefs -m <user>  
Cách truy cập giao diện quản lý cPanel WHM ? >> IP:2087  
PHP X-ray là gì ? >> php x-ray dùng để trace cụ thể thời gian thực thi các function php, giúp phát hiện các func nào gây chậm website khách hàng  
Vị trí access log mặc định trên hosting cPanel >> /usr/local/cpanel/logs/access_log  
Cách tìm add-on domain thuộc user nào trong WHM >> WHM -> List Subdomains -> nhập vào domain cần tìm  
Các file nào dưới đây mặc định không nhìn thấy được trong File Manager cPanel >> .htaccess  
Cách tạo thêm một trang web của user trong Hosting cPanel ? >> Login cPanel -> Domain -> Addon Domain -> Cấu hình database -> Kiểm tra website  
Select PHP Version là gì ? >> (Cloudlinux) Có thể tùy chọn các phiên bản PHP khác nhau cho từng website.
Cách kiểm tra số lượng của Number Of Processes đang chạy trong user cPanel ? » ps aux | grep <user>  
Tính năng Mailing List trong cPanel là gì ? >> Mailing Lists trên cPanel là một công cụ giúp bạn gửi email đến một nhóm lớn người một cách dễ dàng và hiệu quả. 
File manager ở user cPanel hỗ trợ giao thức nào ? >> http  
Khác nhau giữa MultiPHP Manager và Select PHP Version >>  
```
MultiPHP Manager (hỗ trợ bởi cPanel): Có thể tùy chọn các phiên bản PHP khác nhau cho từng website.
Select PHP Version (hỗ trợ bởi cloudlinux): Có thể tùy chọn các phiên bản PHP khác nhau cho từng website.
```
## 6.So sánh 3 control panel
| STT | Tiêu chí | DirectAdmin | aaPanel | CyberPanel | VestaCP |
| :---: | :--- | :---: | :---: | :---: | :---: |
| 1 | Có CLI | Không | Có | Có | Có |
| 2 | Giới hạn users/domains | Theo gói | 1 | Nhiều users/domains | Nhiều users/domains |
| 3 | Webpanel Miễn phí | Không | Miễn phí/Có phí | Miễn phí/Có phí | Miễn phí |
| 4 | Webpanel mặc định | Apache | Apache/Nginx | OpenLiteSpeed | Apache/Nginx |
| 5 | Hỗ trợ SSL | Có | Có | Có | Có - không ổn định |
| 6 | File manager | Có | Có | Có | Không - phải active thủ công |
| 7 | Hỗ trợ FTP | Có | Có | Có | Có |
| 8 | Hỗ trọ PHPMyAdmin | Có | Có | Có | Có |
| 9 | DNS server | Có | Có | Có | Có |
| 10 | Email server | Có | Không | Có | Có
| 11 | Backup - Restore | Thủ công | Thủ công | Thủ công | Có predefined - có thể custom |
| 12 | Hỗ trợ docker | Không | Có | Có | Không |
| 13 | Hỗ trợ multi PHP | Có - build thêm | Có - build thêm | Có - mặc định | Có - build thêm |
| 14 | Reseller | Có | Không | Có | Không |
| 15 | Hỗ trợ NodeJS/Python | Có trong pro pack | Có | Không | Không
| 16 | Thao tác cài đặt, sửa đổi gói/plugins | Dễ | Dễ | Khó | Khó |
| 17 | Firewall CSF/LFD | Firewall có GUI | Cơ bản | Không | Không |
| 18 | Terminal in GUI | Không | Có | Không | Không
| 19 | Hỗ trợ packages - Chia gói Hosting | Có | Không | Có | Có |
| 20 | Hỗ trợ chuyển qua sử dụng LiteSpeed | Có | Không - Chỉ OpenLiteSpeed | Có | Không
| 21 | Các chức năng trả phí nâng cao | Theo gói | Mua plugin | Mua plugin | Mua plugin |
| 22 | Hỗ trợ cấu hình qua API | Có | Có | Có | Chỉ có Github |

