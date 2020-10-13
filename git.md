**pwd显示当前目录**

1. **git init   新建一个空的仓库**
2. **git status  查看状态**
3. git branch 查看所有分支
4. git branch newname 创建一个叫newname的分支
5. git checkout newname 切换到叫newname的分支上
6. **git add . 添加文件**
7. git rm -r xxx.txt  删除文件
8. **git commit -m '注释' 提交添加的文件并备注说明**
9. **git remote add origin git@github.com:gyctl/LeetCode.git 连接远程仓库**
10. **git push origin master 将本地仓库文件推送到远程仓库**
11. **git pull origin master 将远程仓库文件更新到本地仓库**
12. **git remote -v  查看远程仓库**
13. git fetch origin master:newname  本地新建一个newname分支，并将远程origin仓库的master分支代码下载到本地newname分支
    git diff newname 比较本地代码与刚刚从远程下载下来的代码的区别
14. git merge newname 把newname分支合并到当前分支上
15. git branch -d newname  删除newname分支
16. git log 查看变更日志
17. **git reset --hard 版本号前六位 回归到指定版本**
18. **git pull origin master 将master分支上的内容拉到本地上**
19. **git reset --hard HEAD^：把当前的版本回退到上一个版本；hard HEAD^：上一个版本、hard HEAD^^：上上一个版本、hard HEAD~100：前100个版本**

# 远程仓库

1、本地创建SSH key 

```
ssh-keygen -t rsa -C "youremail@example.com"
```

2.1、Github创建一个仓库和本地的Git仓库同步。GitHub仓库作为本地Git仓库备份，与远程仓库建立链接

```
$ git remote add origin 仓库地址
```

2.2 获取最新远程仓库分支 

```
$ git pull origin 分支名
```

2.3 、将本地Git仓库指定分支推送到GitHub，**-u参数**：将origin仓库中的master分支设置为本地仓库当前分支的upstream（上游），一般选择本地的master分支！本地仓库当前分支可以直接从origin仓库的master分支获取内容，省去添加参数的麻烦。

```
$ git push -u origin master
```

2.4 将远程的仓库（GitHub中的仓库）克隆到本地，建立一个一致的本地仓库。执行完成默认在master分支。

```
$ git clone 地址
```

2.5 将远程的仓库（origin仓库）中的一个分支复制到本地，建立一个一致的本地分支。-b参数后面是本地分支名称

```
$ git checkout -b 分支名 origin/分支名
```



# 删除本地文件后重新拉取最新
1. git fetch --all   
2. git reset --hard origin/master 
3. git pull或git checkout file(文件名)
   #将已提交的文件忽略
4. git rm -r --cached node_modules
   git add . -A
5. git commit -m "remove xxx"
6. git push

# 添加新功能时
1. git checkout -b login 创建一个新的login分支并进入此分支
2. git status
3. git add .
4. git commit -m "xxx"
5. git branch
6. git checkout master
7. git branch
8. git merge login
9. git push

# 把新分支添加到云端
1. git checkout login
2. git branch
3. git push -u origin login

### 分支：

##### 分支：用户创建仓库的时候，master是默认分支，用户可以在其他分支上进行开发，经过审核再将他们合并到主分支上。

1. **git branch 分支名（创建分支）**
2. **git checkout 分支名（切换分支）**
3. **git checkout -b 分支名（创建加切换分支）**
4. **git branch（查看当前分支，带星号为当前分支）**
5. **git checkout master（切换回master分支）**
6. **git merge 分支名（合并指定分支到当前分支，只是将master指针指向此分支）**
7. **git branch -d 分支名（删除分支）**

**二、入门操作常见错误**
1、输入：git remote add origin 仓库链接地址 时
报错：fatal: Not a git repository (or any of the parent directories): .git
解决办法：输入 git init ，初始化一个本地仓库
2、输入：git remote add origin 仓库链接地址 时
报错：fatal: remote origin already exists.
解决办法：
**删除Git仓库中的origin信息：git remote rm origin**
重新添加Git仓库中的origin信息
3、输入：git push origin master 时
报错：fatal: 'origin' does not appear to be a git repository
fatal: Could not read from remote repository.Please make sure you have the correct access rights and the repository exists.
解决办法：重新输入一次 git remote add origin 仓库链接地址
4、输入：git push origin master 时
报错：fatal: remote error:
XXXXXX@qq.com/myarea is not a valid repository name Email support@github.com for help
解决办法：使用git remote rm origin 然后再使用上传命令
5、输入：git push origin master 时
报错：To git@git.oschina.net:yangzhi/hello.git
! [rejected] master -> master (fetch first)
error:faled push some refs to ‘仓库地址’
解决办法：出现这个问题是因为github中的README.md文件不在本地代码目录中。先进行代码合并 git pull --rebase origin master 再执行 git push origin master
6、输入：git add ./ 时
报错：fatal: Not a git repository (or any of the parent directories): .git
解决办法：先输入git init，再git add ./
7、输入：git push origin master 时
报错：error:failed to push some refs to...
解决办法：先输入git pull origin master（先把远程服务器github上面的文件拉下来），再输入git push origin master



