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
scp 1 folder
`scp A@ip:[đường dẫn đến thư mục]/[thư mục] B@ip:[đường dẫn đích đến]`
# rsync command
## rsync file
`rsync -av source/file dest/`
## rsync folder
`rsync -av source/folder dest`
## rsync increamental

# cat command
## cat nội dung 1 file
`cat file`
## cat dòng thứ <n> trong file

## cat nhiều dòng vào 1 file bằng EOF
`cat <<EOF`  
`dòng 1`  
`dòng 2`  
`EOF`  
echo command

Dùng echo để chèn thêm 1 dòng vào cuối file

Dùng echo để overwirte nội dung của file

tail/head command

tail và tailf

sed command

Dùng sed để find and replace một string trong file

traceroute/tracert command

Sau khi traceroute xong giải thích chi tiết kết quả trả về

netstat command

hiển thị các socket đang listen

don't resolve hostname

don't resolve portname

display process name/PID

only show tcp socket

only show udp socket

sort command

sort theo thứ tự tăng dần

sort theo thứ tự giảm dần

sort theo column

uniq command

lọc ra các dòng lặp lại trong một file

lọc ra các dòng lặp lại trong file và đếm số lượng các dòng lặp lại

wc command

Đếm số dòng trong file

Đếm số kí tự trong file

chmod, chown, chattr command

Phân quyền bằng số, phân quyền bằng chữ

Đổi owner user/group

Set Immutable Attribute

find command

find các file có đuôi .log

find các folder có tên abc

find các file có tên abc

find các file có tên abc và thực hiện phần quyền read only cho file

cp command

cp file

cp folder

mv command

mv file, folder

cut command

cut kí tự thứ <n> trong string

cut từ kí tự thứ <n> trở về sau

cut từ kí tự thứ <n> trở về trước

dig command

Dùng Dig command để kiểm tra resolv record A, MX, NS

Dùng Dig command để kiểm tra resolv record A, MX, NS với custom DNS

tar/zip/unzip command

- Nén/Giải nén file tar.gz - Nén/Giải nén file .zip

mount/umount command

- Add thêm một ổ cứng sdb ~ 5gb

- Kiểm tra được có bao nhiêu ổ cứng trên máy chủ

- Mount ổ cứng vào /mnt/test

- Umount /mnt/test

Symbolic Links, Hard Links command

Định nghĩ Sym Link

Định nghĩ Hard Link

Ví dụ về Sym Link và Hard Link

ls command

Liệt kê danh sách file/thư mục

Liệt kê danh sách file/thư mục và thuộc tính

Show file ẩn

ps command

show tiến trình

kill tiến trình

top command

Kiểm tra tài nguyên cpu đang sử dụng của một vài process đang chạy

Giải thích về Load average, us, sy, ni, id, wa, hi, si, st, zombie process, sleeping process

free command

Giải thích ram used, free, shared, buff/cache, free

df command

Xem dung lượng disk

Phân vùng / là gì
