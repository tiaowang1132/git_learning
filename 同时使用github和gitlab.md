# 同时使用github和gitlab
## 生成密钥：
ssh-keygen -t rsa "邮箱地址"
ssh-keygen -t rsa "邮箱地址" -f ~/.ssh/id_github_rsa
图略<br>
会生成一对私钥和公钥
## 新建一个config
```
# gitlab
Host git.XXX.com
  HostName git.XXX.com
  IdentityFile ~/.ssh/id_rsa
  
# github
Host github.com
  HostName ssh.github.com
  User XXXXX@XXX.com
  PreferredAuthentications publickey
  IdentityFile ~/.ssh/id_github_rsa
  Port 443
```
## 添加公钥（github）
图略<br>
## 测试
ssh -T git@github.com
图略<br>