#配置多个ssh_key

##1 公司gitlab 的配置
```
http://git.corp.kuaishou.com/help/ssh/README 

. ssh-keygen -t rsa -C "your.email@example.com" -b 4096
. copy id_rsa.pub 到远端服务器
```

##2 github的配置
```
. ssh-keygen -t rsa -C "your.email@example.com"
. cd /.ssh/config进行配置
# 文件内容如下：
# gitlab
Host gitlab.com
    HostName git.corp.kuaishou.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_rsa (此处是私钥文件)
# github
Host github.com
    HostName github.com
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/github_id-rsa
```