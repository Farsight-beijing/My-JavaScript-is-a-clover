**git 帮助**

These are common Git commands used in various situations:|| 这些都是常见的Git命令用于在各种情况下：

# start a working area (see also: git help tutorial)
-    clone      Clone a repository into a new directory
-    init       Create an empty Git repository or reinitialize an existing one

# work on the current change (see also: git help everyday)
-    add        Add file contents to the index
-    mv         Move or rename a file, a directory, or a symlink
-    reset      Reset current HEAD to the specified state
-    rm         Remove files from the working tree and from the index

# examine the history and state (see also: git help revisions)
-    bisect     Find by binary search the change that introduced a bug
-    grep       Print lines matching a pattern
-    log        Show commit logs
-    show       Show various types of objects
-    status     Show the working tree status

# grow, mark and tweak your common history
-    branch     List, create, or delete branches
-    checkout   Switch branches or restore working tree files
-    commit     Record changes to the repository
-    diff       Show changes between commits, commit and working tree, etc
-    merge      Join two or more development histories together
-    rebase     Forward-port local commits to the updated upstream head
-    tag        Create, list, delete or verify a tag object signed with GPG

# collaborate (see also: git help workflows)
-    fetch      Download objects and refs from another repository
-    pull       Fetch from and integrate with another repository or a local branch
-    push       Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.


# git简介
1、历史记录
2、多人协作
3、代码共享--github

#特点
svn集中式，有中央服务器管理代码，离开网络不能工作，不能提交代码；

分布式的版本管理工具；分为四步；

#为什么用
- 简单 易用
- 对操作系统和IDE支持良好
- 可以将大多数操作系统编程离线；
- 分支和TAG非常易用；
- 很方便的撤销更改，修改版本；
- 速度更快，效率更高，不受网络影响
- 开发开源项目；

# 查看帮助
    git help
# 配置git
git config
global 全局的
system 整个用户生效的

# 基本流程
工作区+暂存区+历史区
git init -> git add -> git commit

# 创建仓库
git init
#添加文件
touch index.html
# 添加到暂存区
- git add
- git add . 加个点代表添加所有文件
# 添加到历史区
- git commit -m 'zhushi' 添加到历史区并且加注释；
- git commit -a -m"zhushi" 把工作区的内容直接加到历史区，仅限于已经add的文件；用在修改文件的时候；

# 查看工作区和暂存区的区别
git diff

# 查看暂存区和历史区的区别
git diff --staged

# 重命名
git mv index.html index.htm

# 删除文件
git rm index.css
# 恢复删除的文件
git checkout HEAD --index.html (HEAD代表当前最新一次提交)
# 恢复删除之前的文件
git checkout HEAD ^^
git checkout HEAD ^^ --index.html 把index.index恢复到上上次的版本
# 恢复服务器删除的文件
git reset HEAD index.css
#把服务器上恢复删除的文件，同步到工作区
git checkout index.css

#创建文件夹
mkdir css
#移动文件到另外一个文件夹
git mv index.css css/
#撤掉提交(git的时候不要轻易改变历史)
git revert f7fd17d 这样不仅可以撤掉提交，而且还可以在历史记录里有反应；
#恢复历史版本，撤掉提交，毁尸灭迹
git reset -- f7fd17d  1/改变历史区指针指向的位置；2/改变了暂存区 ;不改变工作区；以后加东西，就在指针指向的位置后添加；
git reset --mixed f7fd17d
git reset --hard f7fd17d 工作区 暂存区 历史区全部修改了，毁尸灭迹，相当于没有提交过一样；



git的时候不要轻易改变历史；
cat index.html 查看index.html文件有什么内容；
vi index.html 进入编辑器写index.html
增删改查都需要提交的
ls 回到项目首页
git status  查看当前的状态,跟踪文件，只跟踪文件，不跟踪文件夹；
【ESC】+【:】+【X】 +【回车】  是退出；
git log  查看往历史区提交的记录
git log --oneline  以一行做简洁显示
git log -graph --all
git log -graph     以图形化的方式显示
git log -graph --oneline    一行显示
git log -graph --oneline --all   显示所有分支
git log -graph --oneline --all --decorate //decorate是加上指针的位置；

# 建立分支
git branch one 新建分支
git branch 查看现在在哪个支或者主干上
git checkout one 切换到one的分支；
touch team.txt 新建一个txt
vi team.txt 修改team.txt文件内容
git add . 添加
git commit -m "+add team.txt"

git merge one 把one分支合并到主干


# git配置

## 1、全局配置
   用户名配置：
   git config –global user.name “Your Name Here”


   邮箱配置：
   git config –global user.email your_email@youremail.com
   查看配置：
   git config –list
## 2、产生rsa密钥对
   ssh-keygen.exe -t rsa
   一路回车，会在下面路径生成你的公私钥
   [windows] : C:\Users\XXX\.ssh
   [linux]   : ~/.ssh/
   私钥：id_rsa
   公钥：id_rsa.pub
## 3、将公钥加入到服务端配置中
   用自己用户登录gitweb服务，profile setting中有ssh keys一项
   将自己的公钥复制添加进来

## 4、克隆git的代码到当前路径
   修改下面ip为git服务器地址
   git clone git@127.0.0.1:master/linux_filter.git

## 5、创建本地develop分支
   查看本地分支：
   git branch –list
   查看远程分支：
   git branch -r 
   创建本地分支：
   git branch develop
   删除本地分支
   git branch -d develop

## 6、切换分支
   git checkout develop
   切换到develop分支

## 7、从远程服务器更新文件到本地
   git  pull

## 8、添加/删除一个文件
   添加一个新文件:
   git add  newfile
   添加修改和新建的文件：
   git add .
   添加修改和删除的文件：
   git add -u

   添加所有修改：
   git add -A

   删除一个文件
   git rm  file

## 9、提交修改
   git commit -m “message modify”
   注意：
   此时的提交只是修改了本地缓存，并没有提交到远程服务器

## 10、提交修改到远程服务器
   git push origin master
   此时可以去git web上查看文件更新








