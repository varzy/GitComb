# gitconfig

自用的 .gitconfig 文件配置。

```
[user]
  name = 
  email = 

[alias]
# basic
  i = init
  a = add
  c = commit
  o = origin
  cl = clone
  st = status
  cm = commit -m

# push
  ps = push
  pso = push origin
  psc = push coding
  psom = push origin master
  psot = push origin --tags

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

# remote
  rmt = remote

# log
  lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
  
[http]
  proxy = socks5://127.0.0.1:1080

[https]
  proxy = socks5://127.0.0.1:1080

[credential]
  helper = wincred
```
