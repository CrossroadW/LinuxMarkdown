	Yum 软件仓库的作用是为了进一步简化 RPM 管理软件的难度以及自动分析 所需软件包及其依赖关系的技术。可以把 Yum 想象成是一个硕大的软件仓库，里面保存有几乎所 有常用的工具，而且只需要说出所需的软件包名称，系统就会自动为您搞定一切。
	/etc/yum.repos.d/  yum配置文件
➢ ：Yum 软件仓库唯一标识符，避免与其他仓库冲突。 
➢ ：Yum 软件仓库的名称描述，易于识别仓库用处。 
➢ ：提供的方式包括 FTP（ftp://..）、HTTP（http://..）、本地 （file:///..）。 《Linux 就该这么学》 - 必读的 Linux 系统与红帽 RHCE 认证免费自学书籍 99 
➢ ：设置此源是否可用；1 为可用，0 为禁用。 
➢ ：设置此源是否校验文件；1 为校验，0 为不校验。 
➢ ：若上面参数开启校验， 那么请指定公钥文件地址。