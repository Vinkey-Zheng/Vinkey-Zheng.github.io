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


## 查找文件命令

find是根据文件的属性来查找，grep是根据文件的类型来查找
文件属性：文件名、文件大小、修改时间、所有者、所属组、是否为空、访问时间


1.  `find . //列举该文件夹下面的所有命令` 
2.  `find [完整的路径] -name  “#.t x t" //查找该路径下面以.txt结尾的文件` 
3. ```
find 组合查找
​
基本语法：-a 与（去交集）
​
• &nbsp; &nbsp; &nbsp; &nbsp;-o 或（去并集）
​
         -not 非(同-！）
​
•        -！非（同-not)
find . -name 'file1*' -a -name 'file2*'
```
4. 根基文件类型来查找


 `find -type f` 

1. 查找关键词


 `find . -name &nbsp;'*srm*' # 在当前目录下查找文件名含有srm的` 


1. 查找文件的后缀


```
grep 'test' d* # 显示所有以d开头的文件中包含test的行
​
grep 'test' aa bb cc # 显示aa, bb , cc的文件中包含test的行
​
grep '[a-z]\{5\}' aa # 显示aa的文件中所有包含每行字符串至少有5个连续小写字符的字符串的行
grep magic /usr/src # 显示/usr/src目录下的文件（不含子目录）中包含magic的行
grep -r magic /usr/src # 显示/usr/src目录下的文件（包含子目录）中包含magic的行
```
## tail命令


- f 循环读取
- -q 不显示处理信息
- -v 显示详细的处理信息
- -c<数目> 显示的字节数
- -n<行数> 显示文件的尾部 n 行内容
- --pid=PID 与-f合用,表示在进程ID,PID死掉之后结束
- -q, --quiet, --silent 从不输出给出文件名的首部


默认显示最后10行
显示文件 notes.log 的内容，从第 20 行至文件末尾:
 `tail -n +20 notes.log` 显示文件 notes.log 的最后 10 个字符:
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
相关链接：https://zhuanlan.zhihu.com/p/101478169
