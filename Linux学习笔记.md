# Linux学习笔记

### 常用命令

#### ls

+ 隐藏文件以 . 开头

+ ls  -a全部显示  

+ ls  -l 完整显示

+ ls  -d显示目录信息

+ ls   -h 友善显示

+ ls  -i 查看文件i结点号

+ ls  /根目录

+ 所有者U  ：只能有一个，文件所有者

+ 所有组 G：只能有一个，文件所有组，一类用户

+ 其他人O：

#### mkdir

+ mkdir 创建目录
+ mkdir -p递归创建多级目录
#### cd
+ 进入指定目录
+ cd ..返回上级目录
#### pwd
+ 显示绝对路径
#### rmdir
+ 删除空目录
#### cp
+ cp    [复制的目录] [复制的文件] ...[目标目录]  将多个文件复制到目标文件
+ cp  -r 复制目录
+ cp  -p保留文件属性
#### mv
+ mv [原文件或目录]....[目标文件或目录]   改名或者剪切
#### rm
+ rm -rf 强制删除目录
+ rm -r 删除目录
+ rm -f 强制删除
#### touch
+ touch 创建文件
#### cat
+ cat 显示文件内容
+ cat -n 标记行号
+ tac 反向查看，不支持-n
#### more（less）
+ 分页显示（空格翻页回车换行）
+ less 可以往回翻页，可查找。pgup上翻    pgon下翻    n遍历关键词     q退出
#### head tail
+ head tail -n 数目 指定行数从头或者尾部查看
+ tail -f 动态显示末尾文件
#### ln
+ ln -s [原文件] [目标文件]

+ ln 硬链接（相当于拷贝，i节点跟原文件相同，跟原文件同步更新）

+ ln -s 创建软链接   软链接类似于window的快捷方式
#### umask
+ umask 查看默认目录创建权限

#### man
+ man 命令或者配置文件 查看文件或者配置文件介绍
#### whatis  
+ whatis 命令  查看命令简短信息
#### apropos
+ apropos 配置文件  查看配置文件信息
#### help
+ help 查看shell内置命令，此类命令通过whereis跟which无法找到
#### useradd
+ useradd 管理员权限下增加用户
#### 压缩命令
文件格式       压缩命令        解压缩命令
+ .gz              gzip                 gunzip
+ .tar          tar  -cf                   -xf
+ .tar.gz      tar -zcf                -zxf
+ .zip           zip -r                  unzip
+ .bz2         bzip2                bunzip2
+ .tar.bz2   tar -cjf                  -xjf
#### 网络命令
+ write

+ wall

+ ping

+ ifconfig

+ mail 

+ netstat
      -tlun  查看本机监听的端口
      -an  查看本机所有的网络连接
      -rn  查看本机路由表
  
+ mount
  
  mount    设备文件名(默认/dev/sr0)   挂载点(也就是自己建立的目录）
  
  umount  挂在点   卸载挂载点

### 文件类型（-rwxrwxrwx）

+ -开头  代表是一个文件  

+ d开头  代表是一个目录

+ l开头   代表一个软链接

rwx                rwx              rwx  ：第一个r，第二个w，第三个x。-代表没有这个权限
u                    g                   o
u所有者     g所属组       o其他人 ：所有者有读写权限；所属组有读权限；其他人有读权限
r读         w写        x执行

