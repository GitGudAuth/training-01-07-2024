# ping/hping3 ping đến domain vietnix.vn sau đó giải thích
```
root@lpcomp:~# hping3 -1 vietnix.vn  
HPING vietnix.vn (wlp0s20f3 103.90.224.90): icmp mode set, 28 headers + 0 data bytes
len=28 ip=103.90.224.90 ttl=53 id=3956 icmp_seq=0 rtt=109.0 ms
len=28 ip=103.90.224.90 ttl=53 id=4134 icmp_seq=1 rtt=6.7 ms 
len=28 ip=103.90.224.90 ttl=53 id=4369 icmp_seq=2 rtt=5.4 ms  
len=28 ip=103.90.224.90 ttl=53 id=4452 icmp_seq=3 rtt=8.1 ms  
len=28 ip=103.90.224.90 ttl=53 id=4625 icmp_seq=4 rtt=7.0 ms  
len=28 ip=103.90.224.90 ttl=53 id=4661 icmp_seq=5 rtt=6.6 ms
```  
## ttl= là gì
## time= là gì
ttl là time to live, là thời gian sống của một gói tin  
time là thời gian gói tin trả về, tính bằng ms, thời gian trả về càng thấp mạng càng nhanh.  
ttl = 53  
round-trip min/avg/max = 5.2/6.9/9.0 ms  
# ssh command
SSH (Secure Shell) là một giao thức mạng giúp người dùng truy cập an toàn vào một thiết bị qua một mạng không được bảo mật.
Cú pháp:  
```
usage: ssh [-46AaCfGgKkMNnqsTtVvXxYy] [-B bind_interface] [-b bind_address]
           [-c cipher_spec] [-D [bind_address:]port] [-E log_file]
           [-e escape_char] [-F configfile] [-I pkcs11] [-i identity_file]
           [-J destination] [-L address] [-l login_name] [-m mac_spec]
           [-O ctl_cmd] [-o option] [-P tag] [-p port] [-R address]
           [-S ctl_path] [-W host:port] [-w local_tun[:remote_tun]]
           destination [command [argument ...]]
       ssh [-Q query_option]
```
## Dùng password
```ssh [username]@[ip]```  
Sau đó nhập password của user
## Dùng key
```ssh -i [đường đẫn đến key]/private-key [username]@[ip]```  
## Dùng port custom
```ssh -p [port] [username]@[ip]```  
## scp command
SCP (Secure Copy) là giao thức dùng để truyền tải file an toan giữa các máy tính.   
Cú pháp:  
```scp [options] [source] [destination]```  
## scp 1 file
```scp [đường dẫn đến file]/file remote@ip:[đường dẫn đích đến]```  
## scp 1 folder
```scp [đường dẫn đến thư mục]/[thư mục] remote@ip:[đường dẫn đích đến]```   
# rsync command
Rsync là một công cụ command line rất nhanh và linh hoạt, được dùng để đồng bộ hoá file và thư mục giữa hai vị trí khác nhau.     
Cú pháp:   
```
Usage: rsync [OPTION]... SRC [SRC]... DEST
  or   rsync [OPTION]... SRC [SRC]... [USER@]HOST:DEST
  or   rsync [OPTION]... SRC [SRC]... [USER@]HOST::DEST
  or   rsync [OPTION]... SRC [SRC]... rsync://[USER@]HOST[:PORT]/DEST
  or   rsync [OPTION]... [USER@]HOST:SRC [DEST]
  or   rsync [OPTION]... [USER@]HOST::SRC [DEST]
  or   rsync [OPTION]... rsync://[USER@]HOST[:PORT]/SRC [DEST]
```
## rsync file
```rsync -a file-old file-new```  
## rsync folder
```rsync -a source/ dest/```  
## rsync increamental
```rsync -aAXPzv folder1 folder2```  
# cat command
CAT (concatenate) là câu lệnh cơ bản trong linux, dùng để hiển thị nội đụng của file, nối nội dung các file với nhau,...
Cú pháp:  
```
Usage: cat [OPTION]... [FILE]...
Concatenate FILE(s) to standard output.
```
## cat nội dung 1 file
```cat file```
## cat dòng thứ <n> trong file
```cat -n file```
## cat nhiều dòng vào 1 file bằng EOF
```
cat <<EOF  > FILE
dòng 1  
dòng 2  
EOF
```
# echo command
Echo là lệnh cơ bản trong linux, mục đích để hiển thị văn bản ra màn hình hoặc ghi đè vào tệp.  
Cú pháp:  
```
echo [OPTIONS] [ARGUMENTS]
```
## Dùng echo để chèn thêm 1 dòng vào cuối file
```echo "dong moi" >> file```  
## Dùng echo để overwirte nội dung của file
```echo "overwrite" > file```  
# tail/head command
tail: In ra 10 dòng cuối ở file  
head: In ra 10 dòng đầu tiên ở file
Cú pháp:  
```
tail [OPTIONS] [FILE]
head [OPTIONS] [FILE]
```
# tail và tailf
tailf giống như tail -f : xem 10 dòng cuối ở file và cập nhật ở thời gian thực  
# sed command
sed (Stream Editor) được sử dụng để tìm, thay thế, xóa, thêm, trích xuất và thao tác với dữ liệu văn bản một cách hiệu quả.  
cú pháp:  
```
Usage: sed [OPTION]... {script-only-if-no-other-script} [input-file]...
```
## Dùng sed để find and replace một string trong file
```sed -i 's\old\new\g' file```
# traceroute/tracert command
Sau khi traceroute xong giải thích chi tiết kết quả trả về  
```
root@lpcomp:~# traceroute vietnix.vn  
traceroute to vietnix.vn (14.225.253.240), 30 hops max, 60 byte packets 
 1  192.168.0.1 (192.168.0.1)  1.796 ms  1.754 ms  3.757 ms
 2  localhost (27.71.251.149)  4.712 ms  4.687 ms  4.662 ms
 3  10.255.39.243 (10.255.39.243)  4.628 ms 10.255.39.241 (10.255.39.241)  4.517 ms  4.492 ms
 4  * * *
 5  localhost (27.68.236.46)  7.373 ms localhost (27.68.236.240)  7.370 ms localhost (27.68.236.242)  5.706 ms
 6  static.vnpt.vn (113.171.45.66)  7.369 ms 203.113.187.98 (203.113.187.98)  5.162 ms *
 7  static.vnpt.vn (113.171.45.66)  4.971 ms  4.619 ms static.vnpt.vn (113.171.45.38)  5.632 ms
 8  static.vnpt.vn (113.171.45.38)  5.590 ms static.vnpt.vn (113.171.46.226)  5.575 ms  5.552 ms
 9  172.16.34.46 (172.16.34.46)  5.538 ms static.vnpt.vn (113.171.48.190)  5.510 ms 172.16.34.46 (172.16.34.46)  5.507 ms
10  172.16.34.46 (172.16.34.46)  5.492 ms  5.477 ms *
11  static.vnpt.vn (14.225.253.240)  4.121 ms  3.974 ms  4.128 ms
```
Bước nhảy 1 ra 192.168.0.1 (gatewate)  
Bước nhảy 6 - 10 ra gateway bên vnpt   
Bước nhảy 11 đến Website vietnix.vn  
# netstat command
netstat dùng dể thực hiện tra cứu, thống kê thông tin về tình trạng kết nối mạng, như thông tin về router, thông tin các cổng và thông tin các dịch vụ chạy trên cổng, IP ,...  
Cú pháp:  
```
usage: netstat [-vWeenNcCF] [<Af>] -r         netstat {-V|--version|-h|--help}
       netstat [-vWnNcaeol] [<Socket> ...]
       netstat { [-vWeenNac] -i | [-cnNe] -M | -s [-6tuw] }
```
## hiển thị các socket đang listen
```netstat -l```
## don't resolve hostname
```netstat --numeric-hosts```
## don't resolve portname
```netstat --numeric-ports```
## display process name/PID
```netstat -p```
## only show tcp socket
```netstat -t```
## only show udp socket
```netstat -u```

# sort command
Lệnh sort giúp người dùng sắp xếp nội dung của tệp văn bản theo một thứ tự nhất định. Lệnh này có thể sắp xếp một tệp văn bản theo thứ tự bảng chữ cái, số, theo cột và hơn thế nữa, theo thứ tự bình thường hoặc ngược lại.     
Cú pháp:  
```
       sort [OPTION]... [FILE]...
       sort [OPTION]... --files0-from=F
```
## sort theo thứ tự tăng dần
```sort```
## sort theo thứ tự giảm dần
```sort -r```
## sort theo column
```sort -k```
# uniq command
uniq là lệnh dòng dể báo cáo số dòng lập lại trong một file
Cú pháp:
```
       uniq [OPTION]... [INPUT [OUTPUT]]
```
## lọc ra các dòng lặp lại trong một file
```uniq file```
## lọc ra các dòng lặp lại trong file và đếm số lượng các dòng lặp lại
```uniq -c file```
# wc command
wc là câu lệnh để đếm số lượng câu, chữ, dòng trong một file, hoặc có thể dùng để tìm số lượng thư mục trong một cây thư mục.   
Cú pháp:
```
Usage: wc [OPTION]... [FILE]...
  or:  wc [OPTION]... --files0-from=F

```
## Đếm số dòng trong file
```wc -l file```
## Đếm số kí tự trong file
```wc -m file```
# chmod, chown, chattr command
chmod là lệnh dùng để thay đổi quyền trên thư mục hoặc tệp tin  
Cú pháp :  
```
Usage: chmod [OPTION]... MODE[,MODE]... FILE...
  or:  chmod [OPTION]... OCTAL-MODE FILE...
  or:  chmod [OPTION]... --reference=RFILE FILE...
```
chown là lệnh dùng dể thay đổi chủ sỡ hữu file, hay group sở hữu file  
Cú pháp:  
```
Usage: chown [OPTION]... [OWNER][:[GROUP]] FILE...
  or:  chown [OPTION]... --reference=RFILE FILE...
```
chattr là lệnh dùng để thay đổi tính chất của file, thay đổi sticky bit  
Cú pháp:  
```
Usage: chattr [-RVf] [-+=aAcCdDeijPsStTuFx] [-p project] [-v version] files..
```
## Phân quyền bằng số, phân quyền bằng chữ
1 = execute = x
2 = write = w
4 = read = r
----------  1 root root 2274 Mar  5 18:44 filedemo  
"-" đầu tiên cho biết loại file là gì (tệp hoặc thư mục)  
"---" 3 gạch đầu tiên cho biết quyền thực thi của owner  
"---" 3 gạch tiếp theo cho biết quyền thực thi của group  
"---" 3 gạch cuối cho biết quyền thực thi của other  
```
chmod 777 filedemo (full quyền)  
chmod g+w filedemo (chỉ cho group quyền write)  
chmod u+x filedemo (cho quyền user/owner quyền execute file)
```  
## Đổi owner user/group
chown user:group [file hoặc directory]
## Set Immutable Attribute
```chattr file```
# find command
find là câu lệnh dùng để tìm các file và thư mục trong cây thư mục.  
Cú pháp:  
```
find  [-H]  [-L] [-P] [-D debugopts] [-Olevel] [starting-point...] [ex‐pression]
```
## find các file có đuôi .log
```find / -type f -name "*.log"```
## find các folder có tên abc
```find / -type d -name "abc"```
## find các file có tên abc
```find / -type f -name "abc"```
## find các file có tên abc và thực hiện phần quyền read only cho file
```find / -type f -name "abc" -exec chmod 444 {} \;```
# cp command
cp là lệnh cơ bản trong linux, dùng để sao chép tệp và thư mục trong hệ thống  
Cú pháp:  
```
Usage: cp [OPTION]... [-T] SOURCE DEST
  or:  cp [OPTION]... SOURCE... DIRECTORY
  or:  cp [OPTION]... -t DIRECTORY SOURCE...
```
## cp file
```cp src/file dest/```
## cp folder
```cp src/ dest/```
# mv command
mv là lệnh dùng để di chuyển tệp tin và thư mục trong hệ thống.  
Cú pháp:  
```
Usage: mv [OPTION]... [-T] SOURCE DEST
  or:  mv [OPTION]... SOURCE... DIRECTORY
  or:  mv [OPTION]... -t DIRECTORY SOURCE...
```
# mv file, folder
```
mv src/file dest/  
mv src/ dest/
```
# cut command
Lệnh cut được dùng để in ra màn hình một phần của dòng từ trong file được đưa vào câu lệnh.  
Cú pháp:  
```
Usage: cut OPTION... [FILE]...

```
## cut kí tự thứ <n> trong string
```cut -c <n> filedemo```
## cut từ kí tự thứ <n> trở về sau
```cut -c <n>- filedemo```
## cut từ kí tự thứ <n> trở về trước
```cut -c -<n> filedemo```
# dig command
Dig là câu lệnh dùng để tra cứu thông tin Domain Name Server (DNS) về một máy chủ từ xa cụ thể.  
Cú pháp:  
```
Usage:  dig [@global-server] [domain] [q-type] [q-class] {q-opt}
            {global-d-opt} host [@local-server] {local-d-opt}
            [ host [@local-server] {local-d-opt} [...]]
```
## Dùng Dig command để kiểm tra resolv record A, MX, NS
```dig A vietnix.vn MX vietnix.vn NS vietnix.vn```
## Dùng Dig command để kiểm tra resolv record A, MX, NS với custom DNS
```dig @CustomDNS A vietnix.vn MX vietnix.vn NS vietnix.vn```
# tar/zip/unzip command
tar dùng để giải nén hoặc nén file .tar, .tar.gz  
zip dùng để nén file thành định dạng .zip  
unzip dùng để giái nén file có định dạng .zip  
## - Nén/Giải nén file tar.gz - Nén/Giải nén file .zip
Nén với tar: ```tar -cvf file.tar filesrc```  
Nén với gunzip: ```tar -cvzf file.tar.gz filesrc```  
Nén với zip: ```zip -rv file.zip filedemo```  
Giải nén tar: ```tar -xvf file.tar```  
Giải nén gunzip: ```tar -xvf file.tar.gz```  
Giải nén unzip: ```unzip file.zip```  

# mount/umount command

## - Add thêm một ổ cứng sdb ~ 5gb
```fdisk /dev/sdb``` 
n : tạo phân vùng mới    
p : primary    
1: phân vùng 1  
+5G : thêm ổ cứng 5gb  
w: save lại  
## - Kiểm tra được có bao nhiêu ổ cứng trên máy chủ
```lsblk```  
## - Mount ổ cứng vào /mnt/test
```mount /dev/sdb /mnt/test```  
## - Umount /mnt/test
```umount /mnt/test```  
# Symbolic Links, Hard Links command
## Định nghĩa Sym Link
Liên kết mềm có thể xem như các shortcut trong Windows, tức là trỏ gián tiếp đến một file hoặc thư mục nào đó. Loại liên kết này có thể trỏ đến một file hay thư mục trên một filesystem hoặc phân vùng khác.  
## Định nghĩa Hard Link
Có thể hiểu như một tên bổ sung cho file hiện có. Các liên kết này liên kết hai hay nhiều tên file với nhau trong cùng một inode. Người dùng có thể tạo một hay nhiều liên kết cứng cho một file duy nhất, tuy nhiên không thể tạo cho thư mục và file trên một filesystem hoặc phân vùng khác. Các liên kết cứng chủ yếu được dùng để lưu trữ nội dung file ở một vị trí cố định, thường để tránh việc nhân bản lượng dữ liệu quá lớn.  
## Ví dụ về Sym Link và Hard Link
Tạo Sym Link : ```ln -s sourcefile symlinkfile```   
Tạo Hard Link : ```ln sourcefile hardlinkfile```  
# ls command
## Liệt kê danh sách file/thư mục
```ls```
## Liệt kê danh sách file/thư mục và thuộc tính
```ls -l```
## Show file ẩn
```ls -a```
# ps command
## show tiến trình
```ps aux```
## kill tiến trình
```
pkill tientrinh  
kill -9 PID
```  
# top command
## Kiểm tra tài nguyên cpu đang sử dụng của một vài process đang chạy
```top ```
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
zombie process:   
sleeping process:   
# free command 
## Giải thích ram used, free, shared, buff/cache, free
used: số lượng bộ nhớ đang được sử dụng      
free: số lượng bộ nhớ còn trống    
shared: số lượng bộ nhớ được sử dụng bỏi tmpfs  
buff/cache: số lượng bộ nhớ được sử dụng bởi kernel  
# df command
## Xem dung lượng disk
```df ```
## Phân vùng / là gì
Là gốc của cây thư mục filesystem, chứa toàn bộ các file và thư mục của hệ điều hành  
