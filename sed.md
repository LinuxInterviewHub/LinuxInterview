## Sed

* [1.删除centos7系统/etc/grub2.cfg⽂件中所有以空⽩开头的⾏⾏⾸的空⽩字符](#1删除centos7系统etcgrub2cfg件中所有以空开头的的空字符)
* [2.在/tmp/file.txt文件中不以#开头的行的行首增加#号](#2在tmpfiletxt文件中不以开头的行的行首增加号)
* [3.用命令行更改/tmp/file.txt文件，把里面所有的“name”更改为“address”](#3用命令行更改tmpfiletxt文件把里面所有的name更改为address)
* [4.使用sed命令打印出/tmp/file.txt文件的第一行到第三行](#4使用sed命令打印出tmpfiletxt文件的第一行到第三行)
* [5.删除/etc/fstab⽂件中所有以#开头，后⾯⾄少跟⼀个空⽩字符的⾏的⾏⾸的# 和空⽩字符](#5删除etcfstab件中所有以开头后少跟个空字符的的的-和空字符)
* [6.在/etc/fstab⽂件中不以#开头的⾏的⾏⾸增加#号](#6在etcfstab件中不以开头的的增加号)
* [7.处理/etc/fstab路径,使⽤sed命令取出其⽬录名和基名](#7处理etcfstab路径使sed命令取出其录名和基名)
* [8.利⽤sed 取出ifconﬁg命令中本机的IPv4地址](#8利sed-取出ifconﬁg命令中本机的ipv4地址)
* [9.将⽂本⽂件的n和n+1⾏合并为⼀⾏， n为奇数⾏](#9将本件的n和n1合并为-n为奇数)
* [10.在每一行后增加一空行？](#10在每一行后增加一空行)
* [11.将/tmp/file.txt文件中第2到第8行之间所有大写字母替换成小写字母](#11将tmpfiletxt文件中第2到第8行之间所有大写字母替换成小写字母)
* [12.使用sed找出/tmp/file.txt文件中包含oldboy的行](#12使用sed找出tmpfiletxt文件中包含oldboy的行)
* [13.将/tmp/file.txt文件中以；结尾的行，行首插入#](#13将tmpfiletxt文件中以结尾的行行首插入)
* [14.删除file.txt文件中的空行](#14删除filetxt文件中的空行)
* [15.使用sed将selinux彻底关闭](#15使用sed将selinux彻底关闭)
* [参考链接](#参考链接)

#### 1.删除centos7系统/etc/grub2.cfg⽂件中所有以空⽩开头的⾏⾏⾸的空⽩字符

``` linux 
sed -r 's/^[[:blank:]]+//' /etc/grub2.cfg
```

#### 2.在/tmp/file.txt文件中不以#开头的行的行首增加#号

``` linux
[root@web01 shell]# sed -n '/^[ a-Z]/p' /tmp/file.txt | sed 's/^/#/g'
```

#### 3.用命令行更改/tmp/file.txt文件，把里面所有的“name”更改为“address”

```linux
 [root@web01 shell]# sed 's/name/address/g' /tmp/file.txt  
```

#### 4.使用sed命令打印出/tmp/file.txt文件的第一行到第三行

```linux
[root@web01 sed]# sed -n '2,3p' /tmp/file.txt 

```

#### 5.删除/etc/fstab⽂件中所有以#开头，后⾯⾄少跟⼀个空⽩字符的⾏的⾏⾸的# 和空⽩字符

```linux 
[root@centos7 ~]# sed -r 's/^#[[:space:]]+//g' /etc/fstab
```

#### 6.在/etc/fstab⽂件中不以#开头的⾏的⾏⾸增加#号

```linux
[root@centos7 ~]# sed -r 's/^[^#]/#&/g' /etc/fstab

[root@centos7 ~]# sed -r '/^[^#]/s@^@#@' /etc/fstab
```

#### 7.处理/etc/fstab路径,使⽤sed命令取出其⽬录名和基名

```linux
[root@centos7 ~]# echo "etc/fstab/dd/" | sed -r 's@^(.*)/(.+)$@\1@'
[root@centos7 ~]# echo "etc/fstab/dd/" | sed -r 's@^(.*)/(.+)$@\2@'
dd/
```

#### 8.利⽤sed 取出ifconﬁg命令中本机的IPv4地址

```linux
[root@centos7 ~]# ifconfig eth0 | sed -rn '/netmask/s#.*net (.*)  net.*#\1#p'
192.168.38.128
```

#### 9.将⽂本⽂件的n和n+1⾏合并为⼀⾏， n为奇数⾏

```linux
[root@centos7 ~]#  seq 10 | sed "1~2N;s/\n/ /" 
1 2
3 4
5 6
7 8
9 10
```

#### 10.在每一行后增加一空行？

```linux
[root@centos7 ~]# sed G /etc/fstab

[root@qqq tmp]# sed -r 's/$/\n/' /etc/passwd
```

#### 11.将/tmp/file.txt文件中第2到第8行之间所有大写字母替换成小写字母

```linux
[root@web01 sed]# sed 's#[a-z]#\u&#g' /tmp/file.txt | sed '2,8s/[A-Z]/\l&/g'

```

#### 12.使用sed找出/tmp/file.txt文件中包含oldboy的行

```linux
[root@web01 sed]# sed -n '/oldboy/p' /tmp/file.txt 
```

#### 13.将/tmp/file.txt文件中以；结尾的行，行首插入#

```linux
[root@web01 sed]# sed -n '/;$/p' /tmp/file.txt | sed 's@^@#@g'
#i like linux;
```

#### 14.删除file.txt文件中的空行

```linux
[root@web01 sed]# sed -r '/^$/d' /tmp/file.txt 
```

#### 15.使用sed将selinux彻底关闭

```linux
[root@web01 sed]# sed '/^SELINUX=/c SELINUX=disabled' /etclinux/config
disabled  enforcing
```

#### 参考链接

http://www.bubuko.com/infodetail-3275744.html

https://blog.51cto.com/14012942/2427099