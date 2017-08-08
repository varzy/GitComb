# SSH Config

Set the proxy for ssh connection.

Create a new text document named `config` in your ".ssh" folder, add the following content. Enjoy~

```
Host github.com
  Hostname github.com
  ProxyCommand connect -S 127.0.0.1:1080 %h %p
  PreferredAuthentications publickey
  IdentityFile [path]/.ssh/id_rsa
```
