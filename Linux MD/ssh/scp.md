# 实例 
    打开cmd,
    输入scp root@192.168.0.1:/root/a.java C:\project_practice

# Linux通过ssh传输文件

## scp(secure copy)是什么?

scp是linux系统下基于ssh登陆进行安全的远程文件拷贝命令。
用于在Linux下进行远程拷贝文件的命令，和它类似的命令有cp，
不过cp只是在本机进行拷贝不能跨服务器，
而且scp传输是加密的。可能会稍微影响一下速度。
## 二、scp有什么用?

1、我们需要获得远程服务器上的某个文件，远程服务器既没有配置ftp服务器，没有开启web服务器，也没有做共享.
2、我们需要将本机上的文件上传到远程服务器上，
## 三、scp使用方法

# 获取远程服务器上的文件

scp -P 2222 root@www.vpser.net:/root/lnmp0.4.tar /home/lnmp0.4.tar

    上端口大写P 为参数，2222 表示更改SSH端口后的端口，
    如果没有更改SSH端口可以不用添加该参数。 
    root@www.vpser.net 表示使用root用户登录远程服务器www.vpser.net，
    :/root/lnmp0.4.tar 表示远程服务器上的文件，
    最后面的/home/lnmp0.4.tar表示保存在本地上的路径和文件名。

## 获取远程服务器上的目录

    scp -P 2222 -r root@www.vpser.net:/root/lnmp0.4/ /home/lnmp0.4/
    上端口大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数。
    -r 参数表示递归复制(即复制该目录下面的文件和目录);
    root@www.vpser.net 
    表示使用root用户登录远程服务器www.vpser.net，
    :/root/lnmp0.4/ 表示远程服务器上的目录，
    最后面的/home/lnmp0.4/表示保存在本地上的路径。
## 将本地文件上传到服务器上

scp -P 2222 /home/lnmp0.4.tar.gz root@www.vpser.net:/root/lnmp0.4.tar
    上端口大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数。 
    /home/lnmp0.4.tar表示本地上准备上传文件的路径和文件名。
    root@www.vpser.net 表示使用root用户登录远程服务器www.vpser.net，
    :/root/lnmp0.4.tar表示保存在远程服务器上目录和文件名。

## 将本地目录上传到服务器上

    scp -P 2222 -r /home/lnmp0.4/ root@www.vpser.net:/root/lnmp0.4/
    上 端口大写P 为参数，2222 表示更改SSH端口后的端口，如果没有更改SSH端口可以不用添加该参数。
    -r 参数表示递归复制(即复制该目录下面的文件和目录);
    /home/lnmp0.4/表示准备要上传的目录，
    root@www.vpser.net 表示使用root用户登录远程服务器www.vpser.net，
    :/root/lnmp0.4/ 表示保存在远程服务器上的目录位置。

## 可能有用的几个参数 :

    -v 和大多数 linux 命令中的 -v 意思一样 , 用来显示进度 . 可以用来查看连接 , 认证 , 或是配置错误 .
    -C 使能压缩选项 .
    -4 强行使用 IPV4 地址 .
    -6 强行使用 IPV6 地址 .



