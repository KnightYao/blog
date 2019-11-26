# GIT http模式保存账号和密码

https 方式每次都要输入密码，按照如下设置即可输入一次就不用再手输入密码的困扰而且又享受 https 带来的极速

```shell
# 设置记住密码（默认15分钟）：
$ git config --global credential.helper cache

# 如果想自己设置时间，可以这样做：
$ git config credential.helper 'cache --timeout=3600'

# 长期存储密码：
$ git config --global credential.helper store

# 增加远程地址的时候带上密码也是可以的。(推荐)
$ http://yourname:password@gitee.com/name/project.git

```