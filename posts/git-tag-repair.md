# git tag版本代码快速修复
实际生产开发中，遇到突发情况，需要紧急修复线上bug，但是灰度环境(或者其他预生产测试环境)已经存在多个新功能的代码了，这时候我们可能选择直接在生产tag版本的代码上进行修复并发布。

```shell
# local_branch : 本地分支名
# tag_name : 生产tag分支
# 修改已经存在的tag
# 基于指定tag版本创建一个分支
$ git checkout -b local_branch tag_name

# 添加新文件代码
$ git add .

# 提交变更
$ git commit -m “紧急修复说明”

# 删除本地tag
$ git tag -d tag_name

# 将本地最新代码发布成tag版本
$ git tag tag_name

# 将本地tag发布到远程
$ git push origin :tag_name

# 本地代码推送到新的远程tag
$ git push origin tag_name
$ git fetch origin
```