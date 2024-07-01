# ping/hping3 ping đến domain vietnix.vn sau đó giải thích
`root@lpcomp:~# hping3 -1 vietnix.vn`  
`HPING vietnix.vn (wlp0s20f3 103.90.224.90): icmp mode set, 28 headers + 0 data bytes`  
`len=28 ip=103.90.224.90 ttl=53 id=3956 icmp_seq=0 rtt=109.0 ms`  
`len=28 ip=103.90.224.90 ttl=53 id=4134 icmp_seq=1 rtt=6.7 ms`  
`len=28 ip=103.90.224.90 ttl=53 id=4369 icmp_seq=2 rtt=5.4 ms`  
`len=28 ip=103.90.224.90 ttl=53 id=4452 icmp_seq=3 rtt=8.1 ms`  
`len=28 ip=103.90.224.90 ttl=53 id=4625 icmp_seq=4 rtt=7.0 ms`  
`len=28 ip=103.90.224.90 ttl=53 id=4661 icmp_seq=5 rtt=6.6 ms`  
## ttl= là gì
## time= là gì
ttl = 53  
round-trip min/avg/max = 5.2/6.9/9.0 ms  
# ssh command
## Dùng password
`ssh [username]@[ip]`
Sao đó nhập password của user
## Dùng key
`ssh -i [đường đẫn đến key] [username]@[ip]`
## Dùng port custom
`ssh -p [port] [username]@[ip]`
## scp command
`scp A@ip:[đường dẫn đến tệp] B@ip:[đường dẫn đích đến]`
## scp 1 file
`scp A@ip:[đường dẫn đến file]/file B@ip:[đường dẫn đích đến]`
## scp 1 folder
`scp A@ip:[đường dẫn đến thư mục]/[thư mục] B@ip:[đường dẫn đích đến]`
# rsync command
## rsync file
`rsync -av source/file dest/`
## rsync folder
`rsync -av source/folder dest`
## rsync increamental
`rsync -av source/oldfolder remote:source/folder source/newfolder`
# cat command
## cat nội dung 1 file
`cat file`
## cat dòng thứ <n> trong file
`cat -n file`
## cat nhiều dòng vào 1 file bằng EOF
`cat <<EOF`  
`dòng 1`  
`dòng 2`  
`EOF`  
## echo command
`echo "hello"`
## Dùng echo để chèn thêm 1 dòng vào cuối file
`echo "dong moi" >> file`  
## Dùng echo để overwirte nội dung của file
`echo "overwrite" > file`
# tail/head command
tail: In ra 10 dòng cuối ở file
head: In ra 10 dòng đầu tiên ở file
# tail và tailf
tailf giống như tail -f : xem 10 dòng cuối ở file và cập nhật ở thời gian thực
# sed command
## Dùng sed để find and replace một string trong file
`sed -i 's\old\new\g' file`
# traceroute/tracert command
Sau khi traceroute xong giải thích chi tiết kết quả trả về
`root@lpcomp:~# traceroute vietnix.vn`  
`traceroute to vietnix.vn (14.225.253.240), 30 hops max, 60 byte packets`  
` 1  192.168.0.1 (192.168.0.1)  1.796 ms  1.754 ms  3.757 ms`  
` 2  localhost (27.71.251.149)  4.712 ms  4.687 ms  4.662 ms`  
` 3  10.255.39.243 (10.255.39.243)  4.628 ms 10.255.39.241 (10.255.39.241)  4.517 ms  4.492 ms`  
` 4  * * *`  
` 5  localhost (27.68.236.46)  7.373 ms localhost (27.68.236.240)  7.370 ms localhost (27.68.236.242)  5.706 ms`  
` 6  static.vnpt.vn (113.171.45.66)  7.369 ms 203.113.187.98 (203.113.187.98)  5.162 ms *`  
` 7  static.vnpt.vn (113.171.45.66)  4.971 ms  4.619 ms static.vnpt.vn (113.171.45.38)  5.632 ms`  
` 8  static.vnpt.vn (113.171.45.38)  5.590 ms static.vnpt.vn (113.171.46.226)  5.575 ms  5.552 ms`  
` 9  172.16.34.46 (172.16.34.46)  5.538 ms static.vnpt.vn (113.171.48.190)  5.510 ms 172.16.34.46 (172.16.34.46)  5.507 ms`  
`10  172.16.34.46 (172.16.34.46)  5.492 ms  5.477 ms *`  
`11  static.vnpt.vn (14.225.253.240)  4.121 ms  3.974 ms  4.128 ms`  

Bước nhảy 1 ra 192.168.0.1 (gatewate)  
Bước nhảy 6 - 10 ra gateway bên vnpt   
Bước nhảy 11 đến Website vietnix.vn  
# netstat command
## hiển thị các socket đang listen
`netstat -l`
## don't resolve hostname
`netstat --numeric-hosts`
## don't resolve portname
`netstat --numeric-ports`
## display process name/PID
`netstat -p`
## only show tcp socket
`netstat -t`
## only show udp socket
`netstat -u`

# sort command
## sort theo thứ tự tăng dần
`sort`
## sort theo thứ tự giảm dần
`sort -r`
## sort theo column
`sort -k`
# uniq command
## lọc ra các dòng lặp lại trong một file
`uniq file`
## lọc ra các dòng lặp lại trong file và đếm số lượng các dòng lặp lại
`uniq -c file`
# wc command
## Đếm số dòng trong file
`wc -l file`
## Đếm số kí tự trong file
`wc -m file`
# chmod, chown, chattr command
## Phân quyền bằng số, phân quyền bằng chữ
1 = execute = x
2 = write = w
4 = read = r
----------  1 root root 2274 Mar  5 18:44 filedemo  
"-" đầu tiên cho biết loại file là gì (tệp hoặc thư mục)  
"---" 3 gạch đầu tiên cho biết quyền thực thi của owner  
"---" 3 gạch tiếp theo cho biết quyền thực thi của group  
"---" 3 gạch cuối cho biết quyền thực thi của other  
`chmod 777 filedemo (full quyền)`  
`chmod g+w filedemo (chỉ cho group quyền write)`  
`chmod u+x filedemo (cho quyền user/owner quyền execute file)`  
## Đổi owner user/group
chown user:group [file hoặc directory]
## Set Immutable Attribute
`chattr file`
# find command
## find các file có đuôi .log
`find / -type f -name "*.log"`
## find các folder có tên abc
`find / -type d -name "abc"`
## find các file có tên abc
`find / -type f -name "abc"`
## find các file có tên abc và thực hiện phần quyền read only cho file
`find / -type f -name "abc" -exec chmod 444 {} \;`
# cp command
## cp file
`cp src/file dest/`
## cp folder
`cp src/ dest/`
# mv command
# mv file, folder
`mv src/file dest/`  
`mv src/ dest/`
# cut command
## cut kí tự thứ <n> trong string
`cut -c <n> filedemo`
## cut từ kí tự thứ <n> trở về sau
`cut -c <n>- filedemo`
## cut từ kí tự thứ <n> trở về trước
`cut -c -<n> filedemo`
# dig comman
## Dùng Dig command để kiểm tra resolv record A, MX, NS
`dig A vietnix.vn MX vietnix.vn NS vietnix.vn`
## Dùng Dig command để kiểm tra resolv record A, MX, NS với custom DNS
`dig @CustomDNS A vietnix.vn MX vietnix.vn NS vietnix.vn`
# tar/zip/unzip command
## - Nén/Giải nén file tar.gz - Nén/Giải nén file .zip
Nén với tar: `tar -cvf file.tar filesrc`  
Nén với gunzip: `tar -cvzf file.tar.gz filesrc`  
Nén với zip: `zip -rv file.zip filedemo`  
Giải nén tar: `tar -xvf file.tar`  
Giải nén gunzip: `tar -xvf file.tar.gz`  
Giải nén unzip: `unzip file.zip`  

# mount/umount command

## - Add thêm một ổ cứng sdb ~ 5gb
`fdisk /dev/sdb`  
n : tạo phân vùng mới    
p : primary    
1: phân vùng 1  
+5G : thêm ổ cứng 5gb  
w: save lại  
## - Kiểm tra được có bao nhiêu ổ cứng trên máy chủ
`lsblk`  
## - Mount ổ cứng vào /mnt/test
`mount /dev/sdb /mnt/test`  
## - Umount /mnt/test
`umount /mnt/test`  
# Symbolic Links, Hard Links command
## Định nghĩa Sym Link
Liên kết mềm có thể xem như các shortcut trong Windows, tức là trỏ gián tiếp đến một file hoặc thư mục nào đó. Loại liên kết này có thể trỏ đến một file hay thư mục trên một filesystem hoặc phân vùng khác.  
## Định nghĩa Hard Link
Có thể hiểu như một tên bổ sung cho file hiện có. Các liên kết này liên kết hai hay nhiều tên file với nhau trong cùng một inode. Người dùng có thể tạo một hay nhiều liên kết cứng cho một file duy nhất, tuy nhiên không thể tạo cho thư mục và file trên một filesystem hoặc phân vùng khác. Các liên kết cứng chủ yếu được dùng để lưu trữ nội dung file ở một vị trí cố định, thường để tránh việc nhân bản lượng dữ liệu quá lớn.  
## Ví dụ về Sym Link và Hard Link
Tạo Sym Link : `ln -s sourcefile symlinkfile`   
Tạo Hard Link : `ln sourcefile hardlinkfile`  
# ls command
## Liệt kê danh sách file/thư mục
`ls`
## Liệt kê danh sách file/thư mục và thuộc tính
`ls -l`
## Show file ẩn
`ls -a`
# ps command
## show tiến trình
`ps aux`
## kill tiến trình
`pkill tientrinh`  
`kill -9 PID`  
# top command
## Kiểm tra tài nguyên cpu đang sử dụng của một vài process đang chạy
`top`
## Giải thích về Load average, us, sy, ni, id, wa, hi, si, st, zombie process, sleeping process
Load average : Thời gian load trung bình của cpu trong thời gian nhất định  
us: phần trăm cpu dành để chạy tiến trình của user  
sy: phần trăm cpu dành để chạy tiến trình của system  
ni: phần trăm cpu dành để chạy các tiến trình không có độ ưu tiên cao
id: phần trăm cpu đang nhàn rỗi  
wa: phần trăm cpu đang chờ các I/O
hi: phần trăm cpu chờ gián đoạn phần cứng  
si: phần trăm cpu chờ gián đọan phần mềm  
st: phần trăm cpu ảo đợi cpu giải quyết các tiến trình  
# free command
## Giải thích ram used, free, shared, buff/cache, free
used: số lượng bộ nhớ đang được sử dụng      
free: số lượng bộ nhớ còn trống    
shared: số lượng bộ nhớ được sử dụng bỏi tmpfs  
buff/cache: số lượng bộ nhớ được sử dụng bởi kernel  
# df command
## Xem dung lượng disk
`df`
## Phân vùng / là gì
Là gốc của cây thư mục filesystem, chứa toàn bộ các file và thư mục của hệ điều hành  
