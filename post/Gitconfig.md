# Gitignore

自用的 .gitconfig 文件配置。

```
[user]
  name = zy
  email = i@zyis.me

[alias]
# basic
  i = init
  a = add
  c = commit
  cl = clone
  st = status

# push
  p = push
  po = push origin
  pom = push origin master
  pot = push origin --tags

# pull
  pl = pull
  fe = fetch

# branch
  b = branch
  bd  = branch -d
  bD  = branch -D

# tag
  t = tag
  td = tag -d

# merge
  mg = merge
  mgn = merge --no-ff

# checkout
  co = checkout
  cob = checkout -b

# reset
  rs = reset --hard
  rsl = reset --hard HEAD^

# remote
  rm = remote

# log
  lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
  
[http]
  proxy = socks5://127.0.0.1:1080

[https]
  proxy = socks5://127.0.0.1:1080

[credential]
  helper = wincred
```
