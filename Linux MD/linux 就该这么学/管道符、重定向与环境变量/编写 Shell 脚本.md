	可以将 Shell 终端解释器当作人与计算机硬件之间的“翻译官”，它作为用户与 Linux 系 统内部的通信媒介，除了能够支持各种变量与参数外，还提供了诸如循环、分支等高级编程 语言才有的控制结构特性。要想正确使用 Shell 中的这些功能特性，准确下达命令尤为重要。 Shell 脚本命令的工作方式有两种：交互式和批处理。
	
- 交互式（Interactive）：用户每输入一条命令就立即执行。 
- 批处理（Batch）：由用户事先编写好一个完整的 Shell 脚本，Shell 会一次性执行脚本 中诸多的命令。
`查看 SHELL 变量可以发现当前系统已经默认使用 Bash 作为命令行终端解释器了： 
```shell
[root@linuxprobe ~]# echo $SHELL 
/bin/bash
```
# 编写简单的脚本
其实使用 Vim 编辑器把 Linux 命令按照顺序依次写入到一 个文件中，这就是一个简单的脚本了。 例如，如果想查看当前所在工作路径并列出当前目录下所有的文件及属性信息，实现这 个功能的脚本应该类似于下面这样：
```shell
 [root@linuxprobe ~]# vim example.sh 
 #!/bin/bash 
 #For Example BY linuxprobe.com 
 pwd 
 ls -al
```
Shell 脚本文件的名称可以任意，但为了避免被误以为是普通文件，建议将.sh 后缀加上，
以 表示是一个脚本文件。
在上面的这个 example.sh 脚本中实际上出现了三种不同的元素：
	第一行的 脚本声明（#!）用来告诉系统使用哪种 Shell 解释器来执行该脚本；
	第二行的注释信息（#）是对 脚本功能和某些命令的介绍信息，
	使得自己或他人在日后看到这个脚本内容时，可以快速知道该 脚本的作用或一些警告信息；
	第三、四行的可执行语句也就是我们平时执行的 Linux 命令了。
	什 么？！你们不相信这么简单就编写出来了一个脚本程序，那我们来执行一下看看结果：
```shell
[root@linuxprobe ~]# bash example.sh 
/root/Desktop 
total 8 
drwxr-xr-x. 2 root root 23 Jul 23 17:31 . 
dr-xr-x---. 14 root root 4096 Jul 23 17:31 ..
-rwxr--r--. 1 root root 55 Jul 23 17:31 example.sh
```

    除了上面用 bash 解释器命令直接运行 Shell 脚本文件外，第二种运行脚本程序的方法是 通过输入完整路径的方式来执行。但默认会因为权限不足而提示报错信息，此时只需要为脚 本文件增加执行权限即可。
```shell
[root@linuxprobe ~]# ./example.sh 
bash: ./Example.sh: Permission denied 
[root@linuxprobe ~]# chmod u+x example.sh 
[root@linuxprobe ~]# ./example.sh 
/root/Desktop total 8 
drwxr-xr-x. 2 root root 23 Jul 23 17:31 . 
dr-xr-x---. 14 root root 4096 Jul 23 17:31 .. 
-rwxr--r--. 1 root root 55 Jul 23 17:31 example.sh
```
# 接收用户的参数
	但是，像上面这样的脚本程序只能执行一些预先定义好的功能，未免太过死板了。为了 让 Shell 脚本程序更好地满足用户的一些实时需求，以便灵活完成工作，必须要让脚本程序能 够像之前执行命令时那样，接收用户输入的参数。
	其实，Linux 系统中的 Shell 脚本语言早就考虑到了这些，已经内设了用于接收参数的变 量，变量之间可以使用空格间隔。
-  例如$0 对应的是当前 Shell 脚本程序的名称，
-   $#对应的是总共 有几个参数，
-   $\ * 对应的是所有位置的参数值，
-  $?对应的是显示上一次命令的执行返回值，
-  而$1、 $2、$3……则分别对应着第 N 个位置的参数值
```shell
[root@linuxprobe ~]# vim example.sh 
#!/bin/bash 
echo "当前脚本名称为$0" 
echo "总共有$#个参数，分别是$*。" 
echo "第 1 个参数为$1，第 5 个为$5。"
:wq

root@localhost ~# sh a.sh  -a -b -c -d -e -f
当前脚本名称为a.sh
总共有6个参数，分别是-a -b -c -d -e -f。
第 1 个参数为-a，第 5 个为-e。
```
# 判断用户的参数
Shell 脚本中的条 件测试语法可以判断表达式是否成立，
	若条件成立则返回数字 0，
	否则便返回其他随机数值。
	
`按照测试对象来划分，条件测试语句可以分为 4 种：

 - 文件测试语句； 
 - 逻辑测试语句； 
 - 整数值比较语句；
 - 字符串比较语句。
 ---------
`文件测试所用的参数
	-d 测试文件是否为**目录**类型 
	-e 测试文件是否**存在**
	-f 判断是否为一般文件 
	-r 测试当前用户是否有权限**读取** 
	-w 测试当前用户是否有权限**写入** 
	-x 测试当前用户是否有权限**执行**

下面使用文件测试语句来判断/etc/fstab 是否为一个目录类型的文件，
然后通过 Shell 解释 器的内设$?变量显示上一条命令执行后的返回值。
如果返回值为 0，则目录存在；
如果返回值 为非零的值，则意味着目录不存在：
```shell
[root@linuxprobe ~]# [ -d /etc/fstab ] 
[root@linuxprobe ~]# echo $? 
1
再使用文件测试语句来判断/etc/fstab 是否为一般文件，如果返回值为 0，则代表文件存 在，且为一般文件：
[root@linuxprobe ~]# [ -f /etc/fstab ] 
[root@linuxprobe ~]# echo $? 
0
逻辑语句用于对测试结果进行逻辑分析，根据测试结果可实现不同的效果。例如在 Shell 终端中逻辑“与”的运算符号是&&，它表示当前面的命令执行成功后才会执行它后面的命令， 因此可以用来判断/dev/cdrom 文件是否存在，若存在则输出 Exist 字样。
[root@localhost ~]# [ -e /dev/cdrom ] && echo "Exist"
Exist
除了逻辑“与”外，还有逻辑“或”，它在 Linux 系统中的运算符号为||，表示当前面的命 令执行失败后才会执行它后面的命令，因此可以用来结合系统环境变量 USER 来判断当前登 录的用户是否为非管理员身份：
root@linuxprobe ~]# echo $USER 
root
[root@linuxprobe ~]# [ $USER = root ] || echo "user" 
[root@linuxprobe ~]# su - linuxprobe 
[linuxprobe@linuxprobe ~]$ [ $USER = root ] || echo "user" 
user
第三种逻辑语句是“非”，在 Linux 系统中的运算符号是一个叹号（！），
它表示把条件测 试中的判断结果取相反值。
也就是说，如果原本测试的结果是正确的，则将其变成错误的；
原 本测试错误的结果则将其变成正确的。 
我们现在切换到一个普通用户的身份，再判断当前用户是否为一个非管理员的用户。
由 于判断结果因为两次否定而变成正确，因此会正常地输出预设信息：
[linuxprobe@linuxprobe ~]$ exit 
logout 
[root@linuxprobe root]# [ ! $USER = root ] || echo "administrator" 
administrator
```
整数比较运算符仅是对数字的操作，不能将数字与字符串、文件等内容一起操作，
	而且 不能想当然地使用日常生活中的等号、大于号、小于号等来判断。
因为等号与赋值命令符冲 突，
	大于号和小于号分别与输出重定向命令符和输入重定向命令符冲突。
		因此一定要使用规 范的整数比较运算符来进行操作。
- -eq 是否等于
- -ne 是否不等于 
- -gt 是否大于 
- -lt 是否小于 
- -le 是否等于或小于 
- -ge 是否大于或等于
```shell
我们先测试一下 10 是否大于 10 以及 10 是否等于 10
[root@localhost ~]# [ 10 -gt 9 ]
[root@localhost ~]# echo $?
0
当然，我自己试了一下这样也可以的
[root@localhost ~]# [ 10 -gt 9 ] && echo "10 > 9"
10 > 9
```
曾经讲过 free 命令，它可以用来获取当前系统正在使用及可用的内存量信息。
接下来先使用 free -m 命令查看内存使用量情况（单位为 MB），然后通过 grep Mem:命令过滤 出剩余内存量的行，再用 awk '{print $4}'命令只保留第四列，最后用 FreeMem=`语句`的方式 把语句内执行的结果赋值给变量。
```shell
[root@linuxprobe ~]# free -m 
total used free shared buffers cached 
Mem: 1826 1244 582 9 1 413 
-/+ buffers/cache: 830 996 
Swap: 2047 0 2047 
[root@linuxprobe ~]# free -m | grep Mem: 
Mem: 1826 1244 582 9 
[root@linuxprobe ~]# free -m | grep Mem: | awk '{print $4}' 
582 
[root@linuxprobe ~]# FreeMem=`free -m | grep Mem: | awk '{print $4}'` [root@linuxprobe ~]# echo $FreeMem 
582
```
我们使用整数运算符来判断内存可用量的值是否小于 1024，若小 于则会提示“Insufficient Memory”（内存不足）的字样：
```shell
[root@linuxprobe ~]# [ $FreeMem -lt 1024 ] && echo "Insufficient Memory" Insufficient Memory
```
字符串比较语句用于判断测试字符串是否为空值，或两个字符串是否相同。它经常用来 判断某个变量是否未被定义（即内容为空值）.
= 比较字符串内容是否相同 
!= 比较字符串内容是否不同
-z 判断字符串内容是否为空
接下来通过判断 String 变量是否为空值，进而判断是否定义了这个变量：
```shell
 [root@linuxprobe ~]# [ -z $String] 
 [root@linuxprobe ~]# echo $? 
 0
 挺好玩的
 [root@localhost ~]# String="hello"
 [root@localhost ~]# [ -z $String ] && echo "null" || echo "$String is Exist"
hello is Exist
```

再尝试引入逻辑运算符来试一下。当用于保存当前语系的环境变量值 LANG 不是英语 （en.US）时，则会满足逻辑测试条件并输出“Not en.US”（非英语）的字样： 
```shell
[root@linuxprobe ~]# echo $LANG 
en_US.UTF-8 
[root@linuxprobe ~]# [ $LANG != "en.US" ] && echo "Not en.US" 
Not en.US
# 这是我自己的 也是utf-8
[root@localhost ~]# echo $LANG
en_US.UTF-8
```

# 流程控制语句
## if 条件测试语句
	下面使用单分支的 if 条件语句来判断/media/cdrom 文件是否存在，
	若存在就结束条件判 断和整个 Shell 脚本，反之则去创建这个目录：
```shell
[root@linuxprobe ~]# vim mkcdrom.sh 
#!/bin/bash 
DIR="/media/cdrom" 
if [ ! -e $DIR ] 
then 
mkdir -p $DIR 
fi
[root@linuxprobe ~]# bash mkcdrom.sh 
[root@linuxprobe ~]# ls -d /media/cdrom 
/media/cdrom
```

Linux 系统中的 ping 命令不像 Windows 一样尝试 4 次就结束，因此为 了避免用户等待时间过长，需要通过-c 参数来规定尝试的次数，
并使用-i 参数定义每个数据 包的发送间隔，
以及使用-W 参数定义等待超时时间。
```shell
[root@linuxprobe ~]# vim chkhost.sh 
#!/bin/bash 
ping -c 3 -i 0.2 -W 3 $1 &> /dev/null 
if [ $? -eq 0 ] 
then echo "Host $1 is On-line." 
else echo "Host $1 is Off-line." 
fi
```

```shell
接下来编写 Shell 脚本 Example.sh。
在脚本中使用 read 命令读取用户输入的密码值，
然 后赋值给 PASSWD 变量，并通过-p 参数向用户显示一段提示信息，
告诉用户正在输入的内容 即将作为账户密码。
在执行该脚本后，会自动使用从列表文件 users.txt 中获取到所有的用户 名称，
然后逐一使用“id 用户名”命令查看用户的信息，
并使用$?判断这条命令是否执行成 功，也就是判断该用户是否已经存在。
需要多说一句，/dev/null 是一个被称作 Linux 黑洞的文件，
把输出信息重定向到这个文件等 同于删除数据（类似于没有回收功能的垃圾箱），
可以让用户的屏幕窗口保持简洁
[root@linuxprobe ~]# vim Example.sh 
#!/bin/bash 
read -p "Enter The Users Password : " PASSWD 
for UNAME in `cat users.txt` 
do 
id $UNAME &> /dev/null 
if [ $? -eq 0 ] 
then 
echo "Already exists" 
else useradd $UNAME &> /dev/null 
echo "$PASSWD" | passwd --stdin $UNAME &> /dev/null 
if [ $? -eq 0 ] 
then 
echo "$UNAME , Create success"
else 
echo "$UNAME , Create failure" 
fi 
fi 
done
这是我自己写的，可以遍历当前目录的文件显示wc命令的统计信息
[root@localhost ~]# cat forwc.sh
#!/bin/bash
for user in `ls | cat`
do
wc $user
done
[root@localhost ~]# bash forwc.sh
  89  272 2666 anaconda-ks.cfg
 5 11 54 forwc.sh
 2  2 12 users.txt
[root@localhost ~]# ls
anaconda-ks.cfg  forwc.sh  users.txt
```
## while 条件循环语句
	编写一个用来猜测数值大 小的脚本 Guess.sh。
	该脚本使用$RANDOM 变量来调取出一个随机的数值（范围为 0～32767）， 
	将这个随机数对 1000 进行取余操作，并使用 expr 命令取得其结果，
	再用这个数值与用户通过 read 命令输入的数值进行比较判断。这个判断语句分为三种情况，分别是判断用户输入的数值是等于、 大于还是小于使用 expr 命令取得的数值。当前，现在这些内容不是重点，我们当前要关注的是 while 条件循环语句中的条件测试始终为 true，因此判断语句会无限执行下去，直到用户输入的数 值等于 expr 命令取得的数值后，这两者相等之后才运行 exit 0 命令，终止脚本的执行。
```shell
[root@linuxprobe ~]# vim Guess.sh 
#!/bin/bash 
PRICE=$(expr $RANDOM % 1000) 
TIMES=0 
echo "商品实际价格为 0-999 之间，猜猜看是多少？" 
while true 
	do
		read -p "请输入您猜测的价格数目：" INT 
		let TIMES++ 
		if [ $INT -eq $PRICE ] ; then 
			echo "恭喜您答对了，实际价格是 $PRICE" 
			echo "您总共猜测了 $TIMES 次" 
			exit 0 
		elif [ $INT -gt $PRICE ] ; then 
			echo "太高了！" 
		else 
			echo "太低了！" 
		fi 
	done
```

## case 条件测试语句
case 条件测试语句和 switch 语句的功能非常相似！
case 语句是在多个范围内匹配 数据，若匹配成功则执行相关命令并结束整个条件测试；
而如果数据不在所列出的范围内， 则会去执行星号（\*）中所定义的默认命令。
>		在前文介绍的 Guess.sh 脚本中有一个致命的弱点—只能接受数字！您可以尝试输入一 个字母，会发现脚本立即就崩溃了。原因是字母无法与数字进行大小比较，例如，“a 是否大 于等于 3”这样的命题是完全错误的。我们必须有一定的措施来判断用户的输入内容，当用户 输入的内容不是数字时，脚本能予以提示，从而免于崩溃。
接下来我们编写脚本 Checkkeys.sh，提示用户输入一个字符并将其赋值给变量 KEY， 然后根据变量 KEY 的值向用户显示其值是字母、数字还是其他字符。
```shell
自己实现了一个
[root@localhost ~]# cat Ckey.sh
#!/bin/bash
read -p "请输入一个字符，按enter确认" KEY

case "$KEY" in
[a-z]|[A-Z])
echo "you input value is letter"
;;
[0-9])
echo "you input value is number"
;;
*)
echo "you input is space or other"
esac

```
## 计划任务服务程序

	经验丰富的系统运维工程师可以使得 Linux 在无需人为介入的情况下，在指定的时间段自动 启用或停止某些服务或命令，从而实现运维的自动化。尽管我们现在已经有了功能彪悍的脚本程 序来执行一些批处理工作，但是，如果仍然需要在每天凌晨两点敲击键盘回车键来执行这个脚本 程序，这简直太痛苦了（当然，也可以训练您的小猫在半夜按下回车键）。接下来，刘遄老师将向 大家讲解如何设置服务器的计划任务服务，把周期性、规律性的工作交给系统自动完成。
	计划任务分为一次性计划任务与长期性计划任务，大家可以按照如下方式理解。 
		➢ 一次性计划任务：今晚 11 点 30 分开启网站服务。 
		➢ 长期性计划任务：每周一的凌晨 3 点 25 分把/home/wwwroot 目录打包备份为 backup.tar.gz。 
	顾名思义，一次性计划任务只执行一次，一般用于满足临时的工作需求。我们可以用 at 命令实现这种功能，只需要写成“at 时间”的形式就可以。如果想要查看已设置好但还未执 行的一次性计划任务，可以使用“at -l”命令；要想将其删除，可以用“atrm 任务序号”。在 使用 at 命令来设置一次性计划任务时，默认采用的是交互式方法。例如，使用下述命令将系 统设置为在今晚 23:30 分自动重启网站服务。
```shell
[root@linuxprobe ~]# at 23:30 
at > systemctl restart httpd 
at > 此处请同时按下 Ctrl + D 组合键来结束编写计划任务 
job 3 at Mon Apr 27 23:30:00 2017 
[root@linuxprobe ~]# at -l
```
如果读者想挑战一下难度更大但简捷性更高的方式，可以把前面学习的管道符（任意门） 放到两条命令之间，让 at 命令接收前面 echo 命令的输出信息，以达到通过非交互式的方式创 建计划一次性任务的目的。 
```shell
[root@linuxprobe ~]# echo "systemctl restart httpd" | at 23:30 
job 4 at Mon Apr 27 23:30:00 2017
[root@linuxprobe ~]# at -l 
3 Mon Apr 27 23:30:00 2017 a root 
4 Mon Apr 27 23:30:00 2017 a root 如果我们不小心设置了两个一次性计划任务，可以使用下面的命令轻松删除其中一个： 
[root@linuxprobe ~]# atrm 3 
[root@linuxprobe ~]# at -l 
4 Mon Apr 27 23:30:00 2017 a root
```

如果我们希望 Linux 系统能够周期性地、有规律地执行某些具体的任务，那么 Linux 系统 中默认启用的 crond 服务简直再适合不过了。
创建、编辑计划任务的命令为“crontab -e”，
查看 当前计划任务的命令为“crontab -l”，
删除某条计划任务的命令为“crontab -r”。
另外，如果您是 以管理员的身份登录的系统，
还可以在 crontab 命令中加上-u 参数来编辑他人的计划任务。 
在正式部署计划任务前，请先跟刘遄老师念一下口诀“分、时、日、月、星期 命令”。 这是使用 crond 服务设置任务的参数格式（其格式见表 4-6）。需要注意的是，如果有些字段 没有设置，则需要使用星号（\*）占位，
![[Pasted image 20230413133620.png]]
分 取值为 0～59 的整数 
时 取值为 0～23 的任意整数 
日 取值为 1～31 的任意整数 
月 取值为 1～12 的任意整数 
星期 取值为 0～7 的任意整数，
其中 0 与 7 均为星期日 
命令 要执行的命令或程序脚本
假设在每周一、三、五的凌晨 3 点 25 分，
都需要使用 tar 命令把某个网站的数据目录进 行打包处理，
使其作为一个备份文件。
我们可以使用 crontab -e 命令来创建计划任务。
为自己 创建计划任务无需使用-u 参数，
具体的实现效果的参数如 crontab -l 命令结果所示：
```shell
[root@linuxprobe ~]# crontab -e 
no crontab for root - using an empty one 
crontab: installing new crontab 
[root@linuxprobe ~]# crontab -l
25 3 * * 1,3,5 /usr/bin/tar -czvf backup.tar.gz /home/wwwroot
```

需要说明的是，除了用逗号（,）来分别表示多个时间段，
例如“8,9,12”表示 8 月、9 月 和 12 月。
还可以用减号（-）来表示一段连续的时间周期（例如字段“日”的取值为“12-15”， 则表示每月的 12～15 日）。以及用除号（/）表示执行任务的间隔时间（例如“ \*/2”表示每隔 2 分钟执行一次任务）。 
**如果在 crond 服务中需要同时包含多条计划任务的命令语句，应每行仅写一条。**
例如我们再 添加一条计划任务，它的功能是每周一至周五的凌晨 1 点钟自动清空/tmp 目录内的所有文件。尤 其需要注意的是，在 crond 服务的计划任务参数中，所有命令一定要用**绝对路径的方式**来写，如 果不知道绝对路径，请用 whereis 命令进行查询，rm 命令路径为下面输出信息中加粗部分。
```shell
[root@linuxprobe ~]# whereis rm 
rm: /usr/bin/rm /usr/share/man/man1/rm.1.gz /usr/share/man/man1p/rm.1p.gz [root@linuxprobe ~]# crontab -e 
crontab: installing new crontab 
[root@linuxprobe ~]# crontab -l 
25 3 * * 1,3,5 /usr/bin/tar -czvf backup.tar.gz /home/wwwroot 
0 1 * * 1-5 /usr/bin/rm -rf /tmp/*
```
注意事项。
➢ 在 crond 服务的配置参数中，可以像 Shell 脚本那样以#号开头写上注释信息，
这样 在日后回顾这段命令代码时可以快速了解其功能、需求以及编写人员等重要信息。 
➢ 计划任务中的“分”字段必须有数值，绝对不能为空或是\*号，而“日”和“星期”字 段不能同时使用，否则就会发生冲突。
