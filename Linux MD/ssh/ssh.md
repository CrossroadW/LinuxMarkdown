# 如果不想在ssh连接时每次输入主机ip该怎么办

可以将主机IP地址添加到Windows 11的SSH配置文件中：

打开Windows PowerShell或命令提示符。

输入以下命令来创建SSH配置文件：


1. New-Item -ItemType File -Path $HOME\.ssh\config
打开SSH配置文件，您可以使用任何文本编辑器，例如记事本：

2. notepad $HOME\.ssh\config
3. 在打开的文件中添加以下内容，将主机IP地址替换为您要连接的实际IP地址：

```console
Host myserver
  HostName 192.168.1.100
  User myusername
```
    'myserver'是您为主机设置的别名，
    '192.168.1.100'是主机的IP地址，
    'myusername'是您在主机上的用户名。

保存文件并关闭文本编辑器。

现在，可以使用以下命令来连接到主机，而无需再输入IP地址：


```console
 ssh myserver
```
Windows 11会自动使用SSH配置文件中的IP地址和用户名来连接到主机。

请注意，如果您的主机使用非标准SSH端口（默认为22），您可以在配置文件中添加'Port'行来指定端口号。例如：


```console
Host myserver
  HostName 192.168.1.100
  Port 2222
  User myusername
```
在上面的示例中，'2222'是非标准端口号。