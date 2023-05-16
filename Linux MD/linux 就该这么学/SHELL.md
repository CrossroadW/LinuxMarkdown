
# man 命令帮助信息的结构以及意义
|结构的名称|代表意义|
|:-----|------|
|NAME |命令的名称 |
|SYNOPSIS|参数的大致使用方法 |
|DESCRIPTION |介绍说明|
|EXAMPLES|演示（附带简单说明）|
|OVERVIEW |概述 |
|DEFAULTS| 默认的功能|
|OPTIONS| 具体的可用选项（带介绍）|
|ENVIRONMENT| 环境变量|
|FILES| 用到的文件|
|SEE ALSO| 相关的资料 |
|HISTORY| 维护历史与联系方式|
## 1.echo命令
echo 命令用于在终端输出字符串或变量提取后的值，
格式为“echo [字符串 | $变量]”。 例如，把指定字符串“Linuxprobe.com”输出到终端屏幕的命令为：

```shell
[root@linuxprobe ~]# echo Linuxprobe.Com
```
该命令会在终端屏幕上显示如下信息：
```shell
Linuxprobe.Com 
```
下面，我们使用$变量的方式提取变量 SHELL 的值，并将其输出到屏幕上：
```shell
[root@linuxprobe ~]# echo $SHELL 
/bin/bash
```

## 2.data命令
date 命令用于显示及设置系统的时间或日期，
格式为“date [选项] [+指定的格式]”。 只需在强大的 date 命令中输入以“+”号开头的参数，即可按照指定格式来输出系统的时 间或日期。
例如，把打包后的文件自动按照“年-月-日”的格式打包成“backup-2017-9-1.tar.gz”
date 命令中的参数以及作用 
|参数|作用|
|----|----|
|%t |跳格[Tab 键]|
|%H |小时（00～23）|
|%I |小时（00～12）|
|%M |分钟（00～59）|
|%S |秒（00～59）| 
|%j |今年中的第几|
默认格式：
```shell
[root@linuxprobe ~]# date 
Mon Aug 24 16:11:23 CST 2017
```

按照“年-月-日 小时:分钟:秒”的格式查看当前系统时间的 date 命令如下所示：
```shell
[root@linuxprobe ~]# date "+%Y-%m-%d %H:%M:%S" 
2017-08-24 16:29:12
```
将系统的当前时间设置为 2017 年 9 月 1 日 8 点 30 分的 date 命令如下所示： 
```shell
[root@linuxprobe ~]# date -s "20170901 8:30:00" 
Fri Sep 1 08:30:00 CST 2017 
```
再次使用 date 命令并按照默认的格式查看当前的系统时间，如下所示：
```bash
[root@linuxprobe ~]# date 
Fri Sep 1 08:30:01 CST 2017
```

## reboot命令

reboot 命令用于重启系统，其格式为 reboot。 
由于重启计算机这种操作会涉及硬件资源的管理权限，因此默认只能使用 root 管理员来 重启，其命令如下：
```shell
[root@linuxprobe ~]# reboot 
```
## poweroff命令

poweroff 命令用于关闭系统，其格式为 poweroff。 该命令与 reboot 命令相同，都会涉及硬件资源的管理权限，因此默认只有 root 管理员才 可以关闭电脑，其命令如下： 
```shell
[root@linuxprobe ~]# poweroff 
```
## wget命令

wget 命令用于在终端中下载网络文件，格式为“wget [参数] 下载地址”。
`wget 命令的参数以及作用`
|参数|作用|
|---|----|
|-b| 后台下载模式 |
|-P |下载到指定目录| 
|-t |最大尝试次数| 
|-c| 断点续传 |
|-p| 下载页面内所有资源，包括图片、视频等| 
|-r |递归下载|
## evince命令

您可以使用命令行工具"evince"来查看pdf文件。在终端中运行以下命令：
`evince <PDF文件路径>`
例如，如果您的pdf文档名为example.pdf，并且存储在用户的“文档”目录下，可以使用以下命令来查看它
`evince ~/Documents/example.pdf`
## ps命令
`-a 显示所有进程（包括其他用户的进程） `
``-u 用户以及其他详细信息 
``-x 显示没有控制终端的进程
Linux 系统中，有 5 种常见的进程状态，
分别为运行、中断、不可中断、僵死与停止，其各自 含义如下所示。
``➢ R运行  进程正在运行或在运行队列中等待。 
``➢ S中断 进程处于休眠中，当某个条件形成后或者接收到信号时，则脱离该 状态。 
``➢ D不可中断 进程不响应系统异步信号，即便用 kill 命令也不能将其中断。
``➢ Z僵死 进程已经终止，但进程描述符依然存在, 直到父进程调用 wait4()系统函数 后将进程释放。 《Linux 就该这么学》 - 必读的 Linux 系统与红帽 RHCE 认证免费自学书籍 56 
``➢ T停止 进程收到停止信号后停止运行。
**进程状态**
![[Pasted image 20230403151856.png]]
![[Pasted image 20230403151949.png]]

## top命令
top 命令用于动态地监视进程活动与系统负载等信息，其格式为 top。 top 命令相当强大，能够动态地查看系统运维状态，完全将它看作 Linux 中的“强化版的 Windows 任务管理器”。
![[Pasted image 20230403152503.png]]
top 命令执行结果的前 5 行为系统整体的统计信息，其所代表的含义如下。
➢ 第 1 行：系统时间、运行时间、登录终端数、系统负载（三个数值分别为 1 分钟、5 分钟、15 分钟内的平均值，数值越小意味着负载越低）。
➢ 第 2 行：进程总数、运行中的进程数、睡眠中的进程数、停止的进程数、僵死的进程 数。 ➢ 第 3 行：用户占用资源百分比、系统内核占用资源百分比、改变过优先级的进程资源 百分比、空闲的资源百分比等。
![[Pasted image 20230403152731.png]]
## pidof命令
pidof 命令用于查询某个指定服务进程的 PID 值，格式为“pidof [参数] [服务名称]”。
每个进程的进程号码值（PID）是唯一的，因此可以通过 PID 来区分不同的进程。
例如， 可以使用如下命令来查询本机上 sshd 服务程序的 PID： 
```shell
	[root@linuxprobe ~]# pidof sshd 
	2156
```

## pidof命令
kill 命令用于终止某个指定 PID 的服务进程，格式为“kill [参数] [进程 PID]”。 
接下来，我们使用 kill 命令把上面用 pidof 命令查询到的 PID 所代表的进程终止掉，
其命 令如下所示。这种操作的效果等同于强制停止 sshd 服务。
```shell
[root@linuxprobe ~]# kill 2156
```
## uname命令
uname 命令用于查看系统内核与系统版本等信息，格式为“uname [-a]”。 
在使用 uname 命令时，一般会固定搭配上-a 参数来完整地查看当前系统的内核名称、主 机名、内核发行版本、节点名、系统时间、硬件名称、硬件平台、处理器类型以及操作系统名 称等信息。
```shell
[root@linuxprobe ~]# uname -a
Linux localhost.localdomain 3.10.0-1160.88.1.el7.x86_64 #1 SMP Tue Mar 7 15:41:52 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
```
`如果要查看当前系统版本的详细信息，则需要查看 redhat-release 文件.
```shell
root@localhost ~# cat /etc/redhat-release
	CentOS Linux release 7.9.2009 (Core)
	root@localhost ~# cat /etc/os-release
	NAME="CentOS Linux"
	VERSION="7 (Core)"
	ID="centos"
	ID_LIKE="rhel fedora"
	VERSION_ID="7"
	PRETTY_NAME="CentOS Linux 7 (Core)"
	ANSI_COLOR="0;31"
	CPE_NAME="cpe:/o:centos:centos:7"
	HOME_URL="https://www.centos.org/"
	BUG_REPORT_URL="https://bugs.centos.org/"

CENTOS_MANTISBT_PROJECT="CentOS-7"
CENTOS_MANTISBT_PROJECT_VERSION="7"
REDHAT_SUPPORT_PRODUCT="centos"
REDHAT_SUPPORT_PRODUCT_VERSION="7"
```
## uptime命令
uptime 用于查看系统的负载信息，格式为 uptime。 
它可以显示当前系统时间、系统已运行时间、启用终端数量以 及平均负载值等信息。
平均负载值指的是系统在最近 
	1 分钟、5 分钟、15 分钟内的压力情 况（下面加粗的信息部分）；
	负载值越低越好，尽量不要长期超过 1，在生产环境中不要超 过 5。
```shell
[root@linuxprobe ~]# uptime 
22:49:55 up 10 min, 2 users, load average: 0.01, 0.19, 0.18
```

## free命令
free 用于显示当前系统中内存的使用量信息，格式为“free [-h]”。
为了保证 Linux 系统不会因资源耗尽而突然宕机，运维人员需要时刻关注内存的使用量。 
在使用 free 命令时，可以结合使用-h 参数以更人性化的方式输出当前内存的实时使用量信息。
```shell
root@localhost ~# free -h
              total        used        free      shared  buff/cache   available
Mem:           1.8G        395M        257M        9.6M        1.1G        1.2G
Swap:          2.0G        1.3M        2.0G
```
## who命令
who 用于查看当前登入主机的用户终端信息，格式为“who [参数]”。 
这三个简单的字母可以快速显示出所有正在登录本机的用户的名称以及他们正在开启的 终端信息。
```shell
root@localhost ~# who
root     tty1         2023-04-02 13:14
root     pts/0        2023-04-03 21:22 (192.168.75.1)
```

```
$ who
user1    tty1         2023-04-02 09:00
user2    pts/0        2023-04-02 09:30 (10.0.0.1)
user3    pts/1        2023-04-02 11:45 (10.0.0.2)
其中，第一列是用户名，第二列是使用的终端设备名称
（tty 表示本地终端，pts 表示远程终端），
第三列是登录时间，
第四列是登录来源（可能为 IP 地址或主机名）。
```
## last命令
last 命令用于查看所有系统的登录记录，格式为“last [参数]”。 
使用 last 命令可以查看本机的登录记录。
```shell
root@localhost ~# last
root     pts/0        192.168.75.1     Mon Apr  3 21:22   still logged in
root     tty1                          Mon Mar  6 17:39 - 13:42 (6+20:03)
reboot   system boot  3.10.0-1160.83.1 Mon Mar  6 17:39 - 16:44 (9+23:04)
root     tty1                          Fri Mar  3 21:55 - 17:38 (2+19:43)
reboot   system boot  3.10.0-1160.el7. Fri Mar  3 21:52 - 17:38 (2+19:46)

wtmp begins Fri Mar  3 21:52:10 2023
```

## history命令
history 命令用于显示历史执行过的命令，格式为“history [-c]”。
>		执行 history 命令能显示出当前用户在本地计算机 中执行过的最近 1000 条命令记录。
		如果觉得 1000 不够用，还可以自定义/etc/profile 文件中的 HISTSIZE 变量值。
		在使用 history 命令时，如果使用-c 参数则会清空所有的命令历史记录。
		还可以使用“!编码数字”的方式来重复执行某一次的命令。

`历史命令会被保存到用户家目录中的.bash_history 文件中。
`Linux 系统中以点（.）开 头的文件均代表隐藏文件，这些文件大多数为系统服务文件，
`可以用 cat 命令查看其文件 内容。
```shell
[root@linuxprobe ~]# cat ~/.bash_history 
```
要清空当前用户在本机上执行的 Linux 命令历史记录信息，可执行如下命令： 
```shell
[root@linuxprobe ~]# history -c
```
`查看history文件的行数可以使用：`
```shell
root@localhost ~# cat ~/.bash_history | wc -l
887
```
## sosreport命令
sosreport（System Overview Snapshot Report） 命令用于收集系统配置及架构信息并输出诊断文档，格式为 sosreport。 
当 Linux 系统出现故障需要联系技术支持人员时，大多数时候都要先使用这个命令来简 单收集系统的运行状态和服务配置信息，
以便让技术支持人员能够远程解决一些小问题，亦 或让他们能提前了解某些复杂问题。
## head&tail&more&less -cat
-   `head` 命令显示文件的前几行，默认为前 10 行。
-   `tail` 命令显示文件的末尾几行，默认为最后 10 行。
-   `more` 命令以一页一页的方式显示文件内容，用户可以使用空格键翻页、回车键滚动一行或者输入 q 键退出查看。
-   `less` 命令和 `more` 类似，但提供了更多的功能和选项，例如向前翻页、搜索、跳转等。
## tr命令
tr 命令用于替换文本文件中的字符，格式为“tr [原始字符] [目标字符]”。
在很多时候，我们想要快速地替换文本中的一些词汇，又或者把整个文本内容都进行替 换，如果进行手工替换，难免工作量太大，尤其是需要处理大批量的内容时，
进行手工替换更 是不现实。
这时，就可以先使用 cat 命令读取待处理的文本，
然后通过管道符（详见第 3 章） 把这些文本内容传递给 tr 命令进行替换操作即可。
例如，把某个文本内容中的英文全部替换 为大写：
```shell
root@localhost ~/p/ConsoleApplication2# cat main.cpp | tr [a-z] [A-Z]
﻿#INCLUDE <CSTDIO>

INT MAIN()
{
    PRINTF("%S 向你问好!\N", "CONSOLEAPPLICATION2");
    RETURN 0;
}
root@localhost ~/p/ConsoleApplication2#
```
## wc命令
wc 命令用于统计指定文本的行数、字数、字节数，格式为“wc [参数] 文本”。
``-l 只显示行数 
``-w 只显示单词数 
``-c 只显示字节数
```shell
root@localhost ~/p/ConsoleApplication2# wc -lwc main.cpp
  7  11 115 main.cpp
  # lines words chars
```
## passwd文件
passwd 是用于保存系统账户信息的文件，
要统计当前系统中有多少个 用户，可以使用下面的命令来进行查询。
## stat
stat 命令用于查看文件的具体存储信息和时间等信息，格式为“stat 文件名称”。
stat 命令可以用于查看文件的存储信息和时间等信息，
命令 stat anaconda-ks.cfg 会显示出 文件的三种时间状态（已加粗）：
Access、Modify、Change。
```shell
root@localhost ~/p/ConsoleApplication2# stat main.cpp
  File: ‘main.cpp’
  Size: 115             Blocks: 8          IO Block: 4096   regular file
Device: 803h/2051d      Inode: 50565280    Links: 1
Access: (0644/-rw-r--r--)  Uid: (    0/    root)   Gid: (    0/    root)
Context: unconfined_u:object_r:admin_home_t:s0
Access: 2023-04-04 13:00:50.971509745 +0800
Modify: 2023-04-02 12:14:43.912704661 +0800
Change: 2023-04-02 12:14:43.914704613 +0800
 Birth: -
```
## cut命令
cut 命令用于按“列”提取文本字符，格式为“cut [参数] 文本”。 
在 Linux 系统中，如何准确地提取出最想要的数据，这也是我们应该重点学习的内容。
一般 而言，按基于“行”的方式来提取数据是比较简单的，
只需要设置好要搜索的关键词即可。
但是 如果按列搜索，不仅要使用-f 参数来设置需要看的列数，
还需要使用-d 参数来设置间隔符号。
passwd 在保存用户数据信息时，
用户信息的每一项值之间是采用冒号来间隔的，
接下来我们使用 下述命令尝试提取出 passwd 文件中的用户名信息，
即提取以冒号（：）为间隔符号的第一列内容：
```shell
root@localhost ~/p/ConsoleApplication2# cut -d: -f1 /etc/passwd
root
bin
daemon
adm
lp
sync
...
```
## diff命令
diff 命令用于比较多个文本文件的差异，格式为“diff [参数] 文件”。 
在使用 diff 命令时，不仅可以使用--brief 参数来确认两个文件是否不同，
还可以使用-c 参 数来详细比较出多个文件的差异之处，
这绝对是判断文件是否被篡改的有力神器。
例如，先 使用 cat 命令分别查看 diff_A.txt 和 diff_B.txt 文件的内容，然后进行比较：
## touch命令
touch 命令用于创建空白文件或设置文件的时间，格式为“touch [选项] [文件]”。 在创建空白的文本文件方面，这个 touch 命令相当简捷，简捷到没有必要铺开去讲。 比如，touch linuxprobe 命令可以创建出一个名为 linuxprobe 的空白文本文件。对 touch 命 令来讲，有难度的操作主要是体现在设置文件内容的修改时间（mtime）、文件权限或属性 的更改时间（ctime）与文件的读取时间（atime）上面。
- -a 仅修改“读取时间”（atime） 
- -m 仅修改“修改时间”（mtime） 
- -d 同时修改 atime 与 mtime
## mkdir命令
mkdir 命令用于创建空白的目录，格式为“mkdir [选项] 目录”。 
文件夹是最常见的文件类型之一。除了能创建单个空白目录外，
mkdir 命令还可以结合-p 参数来递归创建出具有嵌套叠层关系的文件目录
```shell
[root@localhost ConsoleApplication2]# mkdir -p A/B/C/D
[root@localhost ConsoleApplication2]# tree
.
├── A
│   └── B
│       └── C
│           └── D
```
## cp命令
cp 命令用于复制文件或目录，格式为“cp [选项] 源文件 目标文件”。 
大家对文件复制操作应该不陌生，在 Linux 系统中，复制操作具体分为 3 种情况： 
`➢ 如果目标文件是目录，则会把源文件复制到该目录中；`
`➢ 如果目标文件也是普通文件，则会询问是否要覆盖它； `
`➢ 如果目标文件不存在，则执行正常的复制操作。`
- -r 递归持续复制（用于目录）
```shell
[root@localhost ConsoleApplication2]# ls
bin  b.txt  main.cpp  obj
[root@localhost ConsoleApplication2]# echo "hello b.txt" > b.txt
[root@localhost ConsoleApplication2]# cat b.txt
hello b.txt
[root@localhost ConsoleApplication2]# cp main.cpp b.txt
cp: overwrite ‘b.txt’? y
[root@localhost ConsoleApplication2]# cat b.txt
﻿#include <cstdio>

int main()
{
    printf("%s 向你问好!\n", "ConsoleApplication2");
    return 0;
}
```
## mv命令
mv 命令用于剪切文件或将文件重命名，
格式为“mv [选项] 源文件 [目标路径|目标文件名]”。 
剪切操作不同于复制操作，因为它会默认把源文件删除掉，只保留剪切后的文件。
如果 在同一个目录中对一个文件进行剪切操作，其实也就是对其进行重命名：
```shell
[root@localhost ConsoleApplication2]# ls
bin  main.cpp  obj
[root@localhost ConsoleApplication2]# mv main.cpp a.txt
[root@localhost ConsoleApplication2]# head -n 3 a.txt
﻿#include <cstdio>

int main()
```

## dd命令
dd 命令用于按照指定大小和个数的数据块来复制文件或转换文件，格式为“dd [参数]”。 
`dd 让用户按照指定大小和个数 的数据块来复制文件的内容`
`当然如果愿意的话，还可以在复制过程中转换其中的数据。`
`Linux 系统中有一个名为/dev/zero 的设备文件，`
`这个文件不会占用系统存储空间，但却可以提供无穷无尽的数据，`
`因此可以使用它作为 dd 命令的输入文件，来生成一个指定大小的文件。`
 
	 命令的功能也绝不仅限于复制文件这么简单。
	 如果您想把光驱设备中的光盘制作成 iso 格 式的镜像文件，
	 在 Windows 系统中需要借助于第三方软件才能做到，
	 但在 Linux 系统中可以直接 使用 dd 命令来压制出光盘镜像文件，
	 将它变成一个可立即使用的 iso 镜像： 
```shell
 [root@linuxprobe ~]# dd if=/dev/cdrom of=RHEL-server-7.0-x86_64-LinuxProbe.Com.iso      
 7311360+0 records in 
 7311360+0 records out 
 3743416320 bytes (3.7 GB) copied, 370.758 s, 10.1 MB/s 
```
 `考虑到有些读者会纠结 bs 块大小与 count 块个数的关系，下面举一个吃货的例子进行 解释。假设小明的饭量（即需求）是一个固定的值，用来盛饭的勺子的大小即 bs 块大小， 而用勺子盛饭的次数即 count 块个数。小明要想吃饱（满足需求），则需要在勺子大小（bs 块 大小）与用勺子盛饭的次数（count 块个数）之间进行平衡。勺子越大，用勺子盛饭的次数就越少，由上可见，bs 与 count 都是用来指定容量的大小，只要能满足需求，可随意组合搭配方 式。
## file命令 
 file 命令用于查看文件的类型，格式为“file 文件名”。
  在 Linux 系统中，由于文本、目录、设备等所有这些一切都统称为文件，而我们又不能 单凭后缀就知道具体的文件类型，这时就需要使用 file 命令来查看文件类型了。
```shell
[root@localhost projects]# file a.txt b.txt
	a.txt: ASCII text
	b.txt: ASCII text
```
## tar命令
tar 命令用于对文件进行打包压缩或解压，格式为“tar [选项] [文件]”。 
在 Linux 系统中，常见的文件格式比较多，其中主要使用的是.tar 或.tar.gz 或.tar.bz2 格式，我 们不用担心格式太多而记不住，其实这些格式大部分都是由 tar 命令来生成的。
-c 创建压缩文件 
-x 解开压缩文件 
-t 查看压缩包内有哪些文件 
-z 用 Gzip 压缩或解压 
-j 用 bzip2 压缩或解压 
-v 显示压缩或解压的过程 
-f 目标文件名 
-p 保留原始的权限与属性 
-P 使用绝对路径来压缩 
-C 指定解压到的目录
```shell
[root@linuxprobe ~]# tar -czvf etc.tar.gz /etc 
tar: Removing leading '/' from member names 
/etc/ 
/etc/fstab 
/etc/crypttab 
/etc/mtab 
/etc/fonts/
```
```shell
[root@linuxprobe ~]# mkdir /root/etc 
[root@linuxprobe ~]# tar xzvf etc.tar.gz -C /root/etc 
etc/ etc/fstab 
etc/crypttab 
etc/mtab 
etc/fonts/ 
etc/fonts/conf.d/
```

## grep命令
grep 命令用于在文本中执行关键词搜索，并显示匹配的结果，格式为“grep [选项] [文件]”。
-b 将可执行文件（binary）当作文本文件（text）来搜索 
-c 仅显示找到的行数 
-i 忽略大小写 
-n 显示行号 
-v 反向选择—仅列出没有“关键词”的行
```shell
[root@linuxprobe ~]# grep /sbin/nologin /etc/passwd bin:x:1:1:bin:/bin:/sbin/nologin daemon:x:2:2:daemon:/sbin:/sbin/nologin adm:x:3:4:adm:/var/adm:/sbin/nologin lp:x:4:7:lp:/var/spool/lpd:/sbin/nologin mail:x:8:12:mail:/var/spool/mail:/sbin/nologin operator:x:11:0:operator:/root:/sbin/nologin
```

## find命令
find 命令用于按照指定条件来查找文件，格式为“find [查找路径] 寻找条件 操作”。
本书中曾经多次提到“Linux 系统中的一切都是文件”，接下来就要见证这句话的分量了。 在 Linux 系统中，搜索工作一般都是通过 find 命令来完成的，它可以使用不同的文件特性作 为寻找条件（如文件名、大小、修改时间、权限等信息），一旦匹配成功则默认将信息显示到 屏幕上。
-name 匹配名称 
-perm 匹配权限（mode 为完全匹配，-mode 为包含即可） 
-user 匹配所有者 
-group 匹配所有组 
-mtime -n +n 匹配修改内容的时间（-n 指 n 天以内，+n 指 n 天以前） 
-atime -n +n 匹配访问文件的时间（-n 指 n 天以内，+n 指 n 天以前） 
-ctime -n +n 匹配修改文件权限的时间（-n 指 n 天以内，+n 指 n 天以前）
-exec …… {}\; 后面可跟用于进一步处理搜索结果的命令（下文会有演示）


