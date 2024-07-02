# Control Panel
## 1.DirectAdmin
Cây thư mục nằm ở:  
/usr/local/directadmin  
/usr/local/directadmin/conf/directadmin.conf - file config chính cho dịch vụ directadmin    
/usr/local/directadmin/custombuild/ - thư mục cho dịch vụ custombuild    
/usr/local/directadmin/conf/my.cnf - chi tiết kế nối mysql mặc định cho dịch vụ directadmin    
/usr/local/directadmin/data/user/[username] - cấu hình cho một user  
/var/log/directadmin - vị trí file log của directadmin  
CLI: không có
## 2.aaPanel
Cây thư mục nằm ở:    
/www/wwwroot - chứa domains folder và source web  
/www/wwwlogs - chứa file log  
/www/server - chứa config các service  
/www/backup - chứa các backup  
CLI : bt  
## 3.Cyber Panel
Cây thư mục nằm ở:  
/usr/local/CyberCP/CyberCP/settings.py - File cấu hình chính  
/usr/local/CyberCP/ - chứa các file data của Cyberpanel  
/home/cyberpanel - một số cấu hình nằm ở đây  
/etc/cyberpanl - tool hỗ trợ  
/home/cyberpanel/error-logs.txt - file log của cyberpanel  
CLI : cyberpanel  
## 4.VestaCP
Cây thư mục nằm ở:
/home/[user]/conf - file config cho mỗi user/domain
/usr/local/vestacp/conf/vesta.conf - file config chính
/usr/local/vesta/data - thư mục data chính
/home/[user]/web - docroot của web
CLI : v-*
## 5.So sánh 3 control panel
| STT | Tiêu chí | DirectAdmin | aaPanel | CyberPanel | VestaCP |
| --- | --- | --- | --- | --- | --- |
| 1 | Có CLI | Không | Có | Có | Có |
