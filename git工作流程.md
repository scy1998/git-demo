## git工作流程

工作流程：

1. 从远程仓库中克隆代码到本地仓库
2. 从本地仓库中checkout代码，然后修改代码
3. 在提交前先将 代码提交到暂存区
4. 提交本地仓库，本地仓库中保存修改的各个历史版本
5. 修改完成之后，将代码push到远程仓库，与团队成员贡献代码。

## git基础

git管理下，程序员操作的目录是工作树

在数据库和工作树之间有索引，索引是为了向数据库提交做准备的区域

**文件提交到远程数据库中必须添加索引**，通过索引，可以避免不必要的文件的提交，还可以将文件修改内容的一部分加入到索引区并提交

git clone(克隆) 将远程仓库复制到本地

git push (推送)将本地仓库代码上传到远程仓库

git pull(拉取) 将远程仓库代码下载到本地仓库



git clone 和git pull的区别：

git clone：从远程服务器克隆一个一模一样的版本库到本地，复制的是整个版本库

git pull : 相当于相当于从远程获取最新版本合并到本地，获取远程主机某个分支的更新，再与本地的指定分支进行合并。 git pull = git fetch + git merge

## 初步工作

1.git bash 进入到你想建立本地仓库的文件夹

git init 初始化本地仓库



2.~/.ssh判断是否已经配置ssh，只有仓库的主任才能使用ssh链接，如果只是某个项目的成员，只能使用HTTPS链接

如果没有配置ssh,需要配置ssh key



3.添加远程仓库，git remote add + 名字 + github的远程仓库的链接地址

改名字用于向远程仓库推送时使用，因为以后一个本地仓库会链接多个远程仓库，应当使用名字加以区分 git remote add origin  + ssh url

git remote -v  用来查看已经添加的远程仓库的名字



## 文件上传

git add 将修改的文件添加进暂存区，也就是将要添加的文件信息添加进索引库中。

git add -A 提交所有变化

git add . 把所有文件添加进索引



git commit 将当当前暂存区的文件实际保存到仓库的历史记录

git commit -m "修改备注" ： 就是给git add的文件添加一个备注，之后上传到远程仓库中，修改的文件会显示这个备注。

git push 远程仓库名称 远程仓库分支名

注：仓库名称：刚才添加链接时，给仓库起名origin

​		分支：多人合作项目时可以创建多个分支

***注意：如果当前本地仓库不是从远程仓库克隆，而是本地创建的仓库，并且仓库中存在文件，此时再从远程仓库拉取文件的时候会报错（fatal: refusing to merge unrelated histories ），解决此问题可以在git pull命令后加入参数–allow-unrelated-histories\*** ***当执行git中的“git pull origin master –allow-unrelated-histories”命令时，会出现“ couldn’t find remote ref –allow-unrelated-histories”的错误，\*** ***输入如下命令即可解决：\*** ***git pull --rebase origin master\*****