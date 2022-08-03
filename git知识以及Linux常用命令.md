# 利用git管理分支、远程分支
```
1、在当前分支下（一般是master分支），创建iotTest的本地分支分,名为iot_vinkey
$ git checkout -b iot_vinkey
Switched to a new branch 'iot_vinkey'
​
2、将iot_vinkey分支推送到远程
$ git push origin iot_vinkey
$ git push origin master //直接推到master上面
Everything up-to-date
​
3、将本地分支iot_vinkey关联到远程分支iot_vinkey上 &nbsp;
$ git branch --set-upstream-to=origin/iot_vinkey
......
......
......
Branch 'iot_vinkey' set up to track remote branch 'iot_vinkey' from 'origin'
或者 
git branch --up-sstream-to iot_vinkey origin/iot_vinkey
4、查看本地分支和远程分支的映射关系
$ git branch -vv
muscleape &nbsp; &nbsp; &nbsp; &nbsp; f938a3d8e9 [origin/muscleape: gone] 测试test
​
## 5、查看远程分支
$ git branch -r
origin/iot_vinkey
​
## 6、查看本地各个分支目前最新的提交
$ git branch -v
muscleape &nbsp; &nbsp; &nbsp; &nbsp; f938a3d8e9 测试test
​
## 7、查看远程各个分支目前最新的提交
$ git branch -r -v
origin/iot_vinkey &nbsp; &nbsp; &nbsp; &nbsp; f938a3d8e9 测试test
## 8、查看远程分支
git branch -r
## 9、查看本地分支
git branch
## 10、拉取远程分支
git checkout -b 本地分支 origin/远程分支
## 11、拉取远程分支
git pull origin 远程分支
# 12、拉取分支
git pull
#遇到本地冲突，先删除本地分支，再重新拉取远程分支
git branch -D 本地分支名称
```
# git工作原理
**相关内容**
[git工作原理](https://juejin.cn/post/6844904053370159112)
**内容总结**
git内部一切皆对象，commit对象是git仓库的一个快照，包含了整个项目在某一次提交时所有的文件。
每个version就是一个commit，而虚线框的文件表示不同commit中该文件未做修改，git内部实际上对同一个文件（blob对象）的存储永远只有一份，不同commit中是用对象引用的形式来指向同一文件。
**相关git命令**

- cat：查看文件的内容
- git cat-file -p：查看转化后的内容（某一次commit中的一个文件的具体内容）
- git cat-file -t：查看文件的类型
【此节内容截取自余聪莹的分享】
# Linux中的符号的意义
1. ～：家目录
```
cd ~ #回到home目录
cd ~ user #直接在符号后加上某账户的名称
～/bin #路径的一部分
```
2. #: 注释作用
3. `:反引号，编程中调用shell命令
4. $：文件行结尾标识符，变量标识符
5. ～+当前的工作目录，这个符号代表当前的工作目录，和内建指令pwd的作用是相同的。
6. ～-上次的工作目录
7. ；连续指令
8. /:代表目录，单一的/代表root根目录的意思

# 常用命令
> **万能**：man [命令] 或者 [命令] --help, 遇事不决就用这个。
> 不过这两个罗列出来的命令比较多，所以没有耐心的话，还是要记一些常用的。

## 1. **显示当前路径pwd**
## 2. **切换目录命令**
```
cd ../(或者cd ..)切换到上级目录
cd /(cd [空格]) 切换到根目录
cd ~ (或者只有cd)切换到当前用户主目录(home底下以用户名命名的文件夹) /root目录mkdir 创建目录
cd file1 进入文件夹file1
```
## 3. 创建目录命令and创建文件命令
mkdir 目录名 -p 递归创建目录
```
 mkdir file1 新建目录
 mkdir -p /home/file1/file2/file3 一次性创建多级文件
```
创建文件命令
```
touch filename
```
## 4. 删除目录
```
`空目录
用法：rmdir 目录名
也可用：rm -rf 目录名`
例如：
rmdir fileempty
rm -rf fileempty
`非空目录
-f 强制删除
-r 删除目录
常用：rm -rf 文件或目录`
所以直接用 rm -rf就够了
```
```
删除文件： rm [filename]
```
## 5. ls 查看目录或文件信息
主要选项：
ls 单纯列出目录和文件的名称
-l 列出目录或者文件的详细信息。比如权限、修改时间等等
-a 列出当前目录下所有文件，包括隐藏文件（已点开头的都是隐藏文件）

## 6. vi 文本编辑器
```
键入i 进入编辑状态
退出编辑按ESC键
不保存退出： :q!
保存退出： :wq
输入/，进入搜索
输入:set nu，显示每一行的行数
按键盘G，可以直接定位到最末尾
```
## 7. 查找文件命令

find是根据文件的属性来查找，grep是根据文件的类型来查找
文件属性：文件名、文件大小、修改时间、所有者、所属组、是否为空、访问时间

```
`find . //列举该文件夹下面的所有命令` 
`find [完整的路径] -name  “*.txt" //查找该路径下面以.txt结尾的文件` 
find . -name *.gz //在当前目录查找以gz结尾的文件
find / -name vinkey在根目录查找以名称为vinkey的文件
```
+ 根基文件类型来查找
```
 `find -type f` 
查找关键词
 `find . -name &nbsp;'*srm*' # 在当前目录下查找文件名含有srm的` 
 ```
 + 查找文件的后缀
```
grep 'test' d* # 显示所有以d开头的文件中包含test的行
grep 'test' aa bb cc # 显示aa, bb , cc的文件中包含test的行
grep '[a-z]\{5\}' aa # 显示aa的文件中所有包含每行字符串至少有5个连续小写字符的字符串的行
grep magic /usr/src # 显示/usr/src目录下的文件（不含子目录）中包含magic的行
grep -r magic /usr/src # 显示/usr/src目录下的文件（包含子目录）中包含magic的行
```
## 8. cp 复制
用法：cp ［选项］文件名或目录 目标地址
-R 拷贝目录及目录下所有目录和文件
```
cp a.txt b.txt 将a文件复制，且另命名为b文件（目录名）
cp -R a.txt b.txt
```
## 9. mv 移动

用法：mv 文件名或目录 目标目录
mv a.txt ../ 将a文件移动到上级目录（将一个文件移动到另一个目录没有重命名）
mv a.txt ../b.txt 将a文件移动到上一级并改名为b文件（将一个文件移动到另一个目录并重命名）
## 10. head命令
用法： head -n 5 文件名

## 11. tail命令
- f 循环读取
- -q 不显示处理信息
- -v 显示详细的处理信息
- -c<数目> 显示的字节数
- -n<行数> 显示文件的尾部 n 行内容
- --pid=PID 与-f合用,表示在进程ID,PID死掉之后结束
- -q, --quiet, --silent 从不输出给出文件名的首部
```
tail -n 5 文件名 查看后几行
tail -f error.log 不断刷新，看到最新内容
```
默认显示最后10行
显示文件 notes.log 的内容，从第 20 行至文件末尾:
 `tail -n +20 notes.log` 
显示文件 notes.log 的最后 10 个字符:
 `tail -c 10 notes.log` 
```
tail -n 100 /etc/cron &nbsp;#显示最后100行数据
tail -n -100 /etc/cron #除了前99行不显示外，显示第100行到末尾行
```
```
tail -n -5 /test001/text001 与 tail -n 5 /test001/text001 
显示的结果相同，均是文件末尾最后 5 行内容。
​
tail -n +5 /test001/text001 
显示的内容为从第 5 行开始，直到末尾的内容。tail -n 后面的数字有效输入只有单个数字（5）或者加号连接数字（+5）两种。
```
## 12. netstat 查看网络状况 （net status的简写）
netstat -apn 查看所有端口
an，按一定顺序排列输出
p，表示显示哪个进程在调用

## 13. | 管道符 （竖线，英文输入法状态下shift+键盘上的的|\）
在命令之间建立管道，将前面命令的输出作为后面命令的输入
通过命令查找tomcat进程：ps -ef | grep tomcat
通过命令查找到占用此端口的进程编号：netstat -apn|grep 8080
# Docker的一些基本知识

http://www.dockerinfo.net/document 

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

