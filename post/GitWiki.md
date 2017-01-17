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

git clone [URL]
# 克隆一个远程仓库
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
# 对每个文件的修改会要求手动确认
```

### 删除文件

```
git rm [file]
# 删除工作区的文件，并将此操作放入暂存区

git rm --cached [file]
# 停止追踪指定文件，但该文件会保留在工作区
```

## 提交

```
git commit -m "[description]"
# 提交暂存区的所有文件到仓库区

git commit -m "[description]" [file] [file]
# 提交暂存区的指定文件到仓库区
```

## 撤销

```
git checkout [file]
# 恢复暂存区的指定文件到工作区

git checkout [commit_id] [file]
# 恢复某个 commit 的指定文件到暂存区和工作区

git checkout .
# 恢复暂存区的所有文件到工作区

git reset --hard
# 重置暂存区与工作区，与上一次 commit 保持一致​

git reset [commit_id]
# 重置当前分支的 HEAD 为指定 commit，同时重置暂存区，但工作区不变

git reset --hard [commit_id]
# 重置当前分支的 HEAD 为 指定commit，同时重置暂存区和工作区，与指定 commit 一致

git stash
# 暂时将未提交的变化移除​

git stash pop
# 将未提交的变化移入
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

git branch [branch] [commit]
# 新建一个分支，指向指定commit

git --orphan gh-pages
3 新建一个空白分支​

git merge [branch]
# 使用快速合并，合并指定分支到当前分支

git merge --no-ff [branch]
# 使用正常合并，合并指定分支到当前分支​

git push origin --delete [branch]
git branch -dr [remote/branch]
# 删除远程分支
```

## 标签

```
git tag
# 列出所有tag
```

## 查看


## 远程仓库


## 补充

```
git checkout -b，b其实是browse的abbr.
git branch -r, r -> remote
git branch -a, a -> all
git config -l, l -> list
git commit -m, m -> message
```