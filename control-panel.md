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

