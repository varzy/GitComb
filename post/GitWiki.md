# Git Wiki

<!-- TOC -->

- [Git Wiki](#git-wiki)
  - [配置](#配置)
  - [新建仓库](#新建仓库)
  - [添加文件](#添加文件)
  - [删除文件](#删除文件)
  - [提交](#提交)
  - [查看](#查看)
  - [撤销](#撤销)
  - [分支](#分支)
  - [标签](#标签)
  - [SSH Key](#ssh-key)
  - [克隆](#克隆)
  - [拉取](#拉取)
  - [推送](#推送)
  - [修改远程仓库](#修改远程仓库)
  - [子模块](#子模块)
  - [配置命令别名](#配置命令别名)

<!-- /TOC -->

## 配置

``` shell
git config --global user.name "{user_name}"
# 添加 git 使用者的名字

git config --global user.email "{user_email}"
# 添加 git 使用者的邮箱
```

## 新建仓库

``` shell
git init [floder] [--bare]
# 初始化一个 Git 仓库
# `floder`: 新建一个名为 [floder] 的 Git 仓库
# `--bare`: 新建一个裸仓库
```

## 添加文件

``` shell
git add .
# 添加所有文件到暂存区​

git add {dir}/{file}
# 添加指定文件或指定文件夹到暂存区

git add *.{type}
# 添加某个类型的所有文件到暂存区

git add -p
# 将文件添加到暂存区时，需要依次手动确认
```

## 删除文件

``` shell
git rm {file} [--cached]
# 删除工作区的文件，并记录下此次删除操作
# `--cached`: 停止追踪指定文件，但该文件仍会保留在工作区
```

## 提交

``` shell
git commit -m "[description]" [file1 file2 ...]
# 提交暂存区的所有文件到版本库，并添加提交信息
# `files1 file2 ...`: 仅提交指定的文件到版本库
```

## 查看

``` shell
git status
# 显示各个文件当前的变更情况

git log [-num] [--pretty=oneline] [--graph]
# 显示当前分支的版本历史，默认显示三次。可以在后面跟 -[num] 参数自定义显示次数
# `--pretty=oneline`: 参数可以显示简略信息，每条信息只占一行
# `--graph`: 显示分支合并图

git reflog
# 查看 HEAD 的每一次变化历史。可用于将已经回退到过去版本的 HEAD 再次移动到更新的版本

git diff [-- {file}]
# 显示所有文件的暂存区和工作区的差异
# `-- file`: 仅显示某个文件的暂存区和工作区的差异

git diff HEAD [-- {file}]
# 显示所有文件的工作区与当前分支最新 commit 之间的差异
# `-- file`: # 仅显示某个文件的工作区与当前分支最新 commit 之间的差异
```

## 撤销

``` shell
git checkout {file} [commit]
# 将某个文件回到最近一次 git commit 或 git add 时的状态
# `commit`: 将某个文件恢复到该次 commit 时的状态

git checkout .
# 恢复目前暂存区的所有文件到工作区

git reset --hard
# 重置暂存区与工作区，与上一次 commit 保持一致​

git reset --hard HEAD^
# 将文件版本快速回退至上一个版本。在 Git 中，HEAD 表示当前版本，上一个版本是 HEAD^，上上一个版本是 HEAD^^。也可以用数字表示，比如上 100 个版本是 HEAD~100

git reset [{--hard}/{--mixed}/{--soft}] [commit]
# 重置当前分支的 HEAD 为 指定commit
# `--hard`: 重置 HEAD 的同时重置暂存区和工作区
# `--mixed`: 重置 HEAD 的同时将当前修改存放到工作区
# `--soft`: 重置 HEAD 的同时将当前修改存放到暂存区

git stash
# 将未提交的变化暂时保存起来并清空暂存区和工作区

git stash pop
# 将未提交的变化再次移入，工作区和暂存区将再次出现之前的修改
```

## 分支

``` shell
git branch [-r] [-a] [branch]
# 列出所有本地分支
# `-r`: 列出所有远程分支
# `-a`: 列出所有本地分支和远程分支
# `branch`: 新建一个分支，但版本库依然停留在当前分支

git branch {branch} {commit}
# 新建一个指向指定 commit 的分支

git checkout -b {branch}
# 新建一个分支，并切换到该分支

git checkout -b {branch} origin/{branch}
# 在本地新建一个分支，并使其与远程分支保持同步

git checkout --orphan {branch}
# 新建一个空白分支​。可用于创建 gh-pages 分支

git branch -d {branch}
# 删除本地分支

git push origin -d {branch}
git branch -dr {remote/branch}
# 删除远程分支

git merge [--no-ff] {branch}
# 使用快速合并，合并指定分支到当前分支
# `--no-ff`: 使用正常合并，合并指定分支到当前分支​

git rebase {branch}
# 在一个分支里提交的改变移到另一个分支里重放一遍
```

## 标签

``` shell
git tag
# 列出所有标签

git tag {tag} [commit]
# 在当前 commit 新建一个标签
# `commit`: 在指定 commit 上新建一个标签

git show {tag}
# 查看标签信息

git push origin {tag}
# 提交指定标签到远程仓库

git push origin --tags
# 提交所有标签到远程仓库

git tag -d {tag}
# 删除本地标签

git push origin :refs/tags/{tag}
# 删除远程仓库的某个标签。前提是必须先删除本地标签

git checkout -b {branch} {tag}
# 新建一个指向某个标签的分支
```

## SSH Key

``` shell
ssh-keygen -t rsa -C "{user_email}"
# 创建 SSH 密钥

ssh -T git@github.com
# 测试是否顺利连接到 Github

ssh -T git@git.coding.net
# 测试是否顺利连接到 Coding.net
```

## 克隆

``` shell
git clone {URL} [--depth {num}]
# 克隆远程仓库
# `--depth num`: 克隆深度。--depth 10 就表示仅克隆最近 10 次的 commit
```

## 拉取

``` shell
git remote -v
# 显示所有远程仓库

git remote show [remote]
# 显示某个远程仓库的信息
# `remote`: 当只有一个远程仓库时可省略

git pull [remote] [remote_branch]:[local_branch]
# 拉取远程仓库相应追踪分支的更改并直接合并到本地当前分支。如果当前分支只有一个追踪分支，连远程主机名都可以省略

git pull origin [branch]
# 取回远程仓库的变化，并直接与本地分支合并
# `branch`: 当本地分支与远程分支建立追踪关系后可以省略

git fetch [remote] [-p]
# 下载远程仓库的所有变动
# `remote`: 当只有一个远程仓库时可省略
# `-p`: 获取远程仓库对远程分支的删除操作
```

## 推送

``` shell
git push [remote] [local_branch]:[remote_branch]
# 推送本地当前分支的修改到远程仓库相应追踪分支。如果当前分支只有一个追踪分支，连远程主机名都可以省略
# 如果该远程分支不存在，则会被新建
# 注意，分支推送顺序的写法是 <来源地>:<目的地>，所以 git pull 是 <远程分支>:<本地分支>，而 git push 是 <本地分支>:<远程分支>

git push -u origin {branch}
# 把一个本地分支推送到远程并建立追踪关系，一般用于将本地提交首次推送到远程仓库

git push origin {branch} [-a]
# 上传本地指定分支到远程仓库
# `-a`: 推送当前所有分支到远程仓库
```

## 修改远程仓库

``` shell
git remote add origin [name] {URL}
# 添加一个名为 origin 的远程仓库

git remote add {name} {URL}
# 添加一个名为 name 的新远程仓库

git remote set-url [--add] origin {URL}
# 修改当前仓库的远程仓库地址
# `--add`: 添加一个新的远程仓库，但其名字仍为 origin。此时推送至远程时，可以实现一键推荐至多个仓库；但拉取时，仅能拉取 .git/config 中列出的第一个远程仓库
```

## 子模块

``` shell
git submodule add {URL}
# 添加子模块

git submodule init
# 初始化本地的子模块配置

git submodule update
# 更新子模块
```

## 配置命令别名

``` shell
git config --global alias.{alias} {origin}
# 配置命令别名。比如用 cl 代替 clone
# --global 参数是全局参数，也就是这些命令在这台电脑的所有 Git 仓库下都有用
# 此修改将保存至 .gitconfig 文件中，也可以直接进入 .gitconfig 文件批量修改
```
