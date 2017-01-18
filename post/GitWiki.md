# GitWiki

## 配置

```
git config --global user.name "[user_name]"
git config --global user.email "[user_email]"
```

## 新建

```
git init
# 在当前目录创建 Git 仓库

git init [floder_name]
# 新建一个目录，并将其初始化为 Git 仓库

git init --bare
# 创建一个 Git 裸仓库​​
```

## 增删文件

### 添加文件

```
git add [file]/[dir]
# 添加指定文件或指定文件夹到暂存区

git add *.[file_type]
# 添加某个类型的所有文件到暂存区

git add .
# 添加当前目录所有文件到暂存区​

git add -p
# 将文件添加到暂存区时，要求逐次手动确认
```

### 删除文件

```
git rm [file]
# 删除工作区的文件，并将此操作放入暂存区。等同于在文件资源管理器中手动删除

git rm --cached [file]
# 停止追踪指定文件，但该文件会保留在工作区
```

## 提交

```
git commit -m "[description]"
# 提交暂存区的所有文件到仓库

git commit -m "[description]" [file] [file]
# 提交暂存区的指定文件到仓库
```

## 查看

```
git status
# 显示有过变更的文件

git log
# 显示当前分支的版本历史。默认显示三次，可以在后面跟 -[num] 参数自定义显示次数

git log -[num] --pretty=oneline
# 如果不加 -[num] 参数，则默认显示过去 30 次提交信息。提交信息一条仅占一行

git log --graph
# 查看分支合并图

git reflog
# 查看之前进行操作的每一次命令

git diff
# 显示所有文件的暂存区和工作区的差异

git diff -- [file]
# 显示某个文件的暂存区和工作区的差异

git diff HEAD
# 显示所有文件的工作区与当前分支最新 commit 之间的差异

git diff HEAD -- [file]
# 显示某个文件的工作区与当前分支最新 commit 之间的差异
```

## 撤销

```
git checkout [file]
# 让某个文件回到最近一次 git commit 或 git add 时的状态

git checkout [commit] [file]
# 恢复某个 commit 的指定文件到暂存区和工作区

git checkout .
# 恢复目前暂存区的所有文件到工作区

git reset --hard
# 重置暂存区与工作区，与上一次 commit 保持一致​

git reset --hard HEAD^
# 将文件版本快速回退至上一个版本。在 Git 中，HEAD 表示当前版本，上一个版本是 HEAD^，上上一个版本是 HEAD^^。也可以用数字表示，比如上 100 个版本是 HEAD~100

git reset [commit]
# 重置当前分支的 HEAD 为指定 commit，同时重置暂存区，但工作区不变

git reset --hard [commit]
# 重置当前分支的 HEAD 为 指定commit，同时重置暂存区和工作区，与指定 commit 一致

git stash
# 将未提交的变化暂时移除​

git stash pop
# 将未提交的变化再次移入
```

## 分支

```
git branch
# 列出所有本地分支

git branch -r
# 列出所有远程分支

git branch -a
# 列出所有本地分支和远程分支

git branch [branch]
# 新建一个分支，但依然停留在当前分支

git checkout -b [branch]
# 新建一个分支，并切换到该分支

git checkout --orphan [branch]
# 新建一个空白分支​。常用于创建 gh-pages 分支

git merge [branch]
# 使用快速合并，合并指定分支到当前分支

git merge --no-ff [branch]
# 使用正常合并，合并指定分支到当前分支​

git rebase [branch]
# 在一个分支里提交的改变移到另一个分支里重放一遍

git push origin --delete [branch]
git branch -dr [remote/branch]
# 删除远程分支

git branch [branch] [commit]
# 新建一个分支，指向指定 commit
```

## 标签

```
git tag
# 列出所有标签

git tag [tag]
# 在当前 commit 新建一个标签

git tag [tag] [commit]
# 在指定 commit 新建一个标签

git show [tag]
# 查看标签信息

git push origin [tag]
# 提交指定标签

git push origin --tags
# 提交所有标签

git tag -d [tag]
# 删除本地标签

git push origin :refs/tags/[tag]
# 删除远程标签。要想删除远程标签，必须先删除本地标签

git checkout -b [branch] [tag]
# 新建一个分支，指向某个标签
```

## 远程仓库

### SSH Key

```
ssh-keygen -t rsa -C "i@zyis.me"
# 创建 SSH 密钥

ssh -T git@github.com
# 测试是否顺利连接到 Github
```

### 克隆

```
git clone [URL] ( --depth [num] )
# 如果添加 --depth [num] 参数可以指定克隆深度。比如 --depth 1 表示仅克隆最近的一次 commit
```

### 拉取

```
git fetch ( [remote] )
# 下载远程仓库的所有变动

git remote -v
# 显示所有远程仓库

git remote show [remote]
# 显示某个远程仓库的信息

git pull origin [branch]
# 取回远程仓库的变化，并直接与本地分支合并
```

### 推送

```
git push -u origin master
# 把当前 master 分支首次推送到远程

git push origin [branch]
# 上传本地指定分支到远程仓库

git push origin --all
# 推送所有分支到远程仓库
```

### 修改

```
git remote add origin [URL]
# 添加远程仓库

git remote set-url origin [URL]
# 修改远程仓库
```

## 其他

### 配置 .gitconfig

```
git config --global alias.[st] status
# 配置别名，用 st 代替 status。--global 参数是全局参数，也就是这些命令在这台电脑的所有 Git 仓库下都有用。此修改将保存至 .gitconfig 文件中。也可以直接进入 .gitconfig 文件批量修改。
```

### 命令简写意义

来自 [阮一峰：常用 Git 命令清单](http://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html) 一文中 AnnabellChan 的评论

```
git checkout -b，b 其实是 browse 的 abbr
git branch -r, r -> remote
git branch -a, a -> all
git config -l, l -> list
git commit -m, m -> message
```
