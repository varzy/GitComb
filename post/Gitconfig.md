# .gitconfig

My own ".gitconfig" file.

```
[user]
  name = 
  email = 

[alias]
# basic
  i = init
  a = add
  aa = add .
  c = commit
  cm = commit -m
  cl = clone
  st = status
  re = remote
  # sm = submodule

# push
  ps = push
  pso = push origin
  psom = push origin master
  psot = push origin --tags
  psou = push origin -u

# pull
  pl = pull
  plo = pull origin
  plom = pull origin master

# fetch
  fe = fetch
  feo = fetch origin

# branch
  b = branch
  bd = branch -d
  bD = branch -D

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

# log
  lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
  rlg = reflog
  
[http "https://github.com"]
  proxy = socks5://127.0.0.1:1080

[https "https://github.com"]
  proxy = socks5://127.0.0.1:1080

# encoding
[core]
  quotepath = false

[gui]
  encoding = utf-8

[i18n "commit"]
  encoding = utf-8

[i18n]
  logoutputencoding = utf-8
```
