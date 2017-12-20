#配置多个ssh_key

##1 公司gitlab 的配置
```

. git config user.name " " 
. git config user.email " "
. ssh-keygen -t rsa -C "your.email@example.com" -b 4096
. copy id_rsa.pub 到远端服务器

参考地址：http://git.corp.kuaishou.com/help/ssh/README 
⚠️ git config配置user name/email时，是否使用global。如不使用，需进入一个仓库中进行后续操作
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
    
 参考地址：http://blog.csdn.net/birdben/article/details/51824788
 ⚠️ 多个ssh-key时，注意不要覆盖以前的rsa
 
```