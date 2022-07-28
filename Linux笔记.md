# Shell
1. Shell是Linux系统的***用户界面***，提供了用户与Linux系统内核进行交互操作的一种接口，它接收用户输入的命令并把它送入内核去执行。
2. 当我们在Linux系统中打开一个终端（**Ctrl+Alt+T**）时，就进入了Shell命令提示符状态，在里面输入的用户命令，都会被送入Linux内核去执行。
3. 每个Linux系统的用户可以拥有自己的Shell，用以满足他们自己专门的Shell需要。

Shell也有多种不同的版本，主要有下列版本的Shell：
+ Bourne Shell：由贝尔实验室开发；
+ BASH：是GNU的Bourne Again Shell，是GNU操作系统上默认的Shell；
+ Korn Shell：是对Bourne Shell的发展，在大部分内容上与Bourne Shell兼容；
+ C Shell：是SUN公司Shell的BSD版本；
+ Z Shell：Z是最后一个字母，也就是终极Shell，集成了BASH、ksh的重要特性，同时又增加了自己独有的特性。

# root用户
1. 对于Linux系统而言，超级用户一般命名为root，相当于Windows系统中的Administrator用户。
2. root是系统中唯一的超级用户，具有系统中所有的权限，如启动或停止一个进程、删除或增加用户、增加或者禁用硬件等等。

# sudo授权
sudo是Linux系统管理指令，管理员可以授权给一些普通用户去执行一些需要root权限执行的操作。这样不仅减少了root用户的登录和管理时间，同样也提高了安全性。本教程后面在执行软件安装时，都是采用hadoop用户登录，而不是root用户登录，因此，使用hadoop用户登录Linux系统以后，当需要执行只有root用户有权限执行的命令时，都要在命令前面加上sudo，才能够顺利执行，如果不加上sudo，就会被拒绝执行。

当使用sudo命令时，会要求输入当前用户的密码。需要注意的是，Windows系统中，用户输入密码，都会在屏幕上显示“*”号作为反馈，但是，在Linux系统中，当输入密码时，不会在屏幕上显示“*”号作为反馈，这时，不要误以为系统死机或者键盘出了问题，只要输完密码后回车即可。

# 创建普通用户
```
# 创建一个用户hadoop
sudo useradd -m hadoop -s /bin/bash
# 为hadoop设置密码
sudo passwd hadoop
# 为hadoop用户增加管理员权限
sudo adduser hadoop sudo
```
# 常用命令
```
# 查看Linux系统内核版本信息
cat /proc/version
# 进入当前Linux系统登陆用户的主目录（或主文件夹）
cd ~
# 即“/home/用户名”,若登录用户名为Hadoop，则~代表/home/Hadoop

# 把当前目录下的file1和file2文件合并到生成file3
cat file1 file2 > file3
# 把当前目录下的word.txt文件中的前5行内容显示到屏幕上
head -5 word.txt
# 把/home/hadoop/word.txt文件复制到/usr/local目录下
cp /home/hadoop/word.txt /usr/local
# 查看本机IP地址
ifconfig
```
# 常用的目录
1. Linux系统的根目录“/”下，存在很多个目录，其中有两个目录，是本教程学习过程中经常用到的，一个是“/home”目录，一个是“/usr”目录。“/home”目录包含了各个用户的用户目录，每当在Linux系统中新建一个普通用户时，系统就会自动为这个用户创建用户主目录（主文件夹）

2. “/usr”目录是“Unix Software Resource”的简写，表示这里是各种软件安装的目录。对于“/usr”目录而言，只需要关注它下面的子目录“/usr/local”，一般由用户安装的软件都建议安装到该目录下

# 更新APT
APT是一个非常优秀的软件管理工具，Linux系统采用APT来安装和管理各种软件。
```
sudo apt-get update
```
# 目录的权限
sudo chown [权限] 用户名 文件（目录）
