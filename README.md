# KnightYao's blog

在尝试了多种博客工具之后，我觉得博客应该要随心随性，易于编写和维护，所以决定使用比较有趣的方式来实现。工具栈是 grep+vim+fpp ，在每篇博客标题下为该文章打 Tags，便于搜索。

日常工作流

1. vim 编辑文档，markdown 文档可以使用 [grip](https://github.com/joeyespo/grip) 工具预览
2. grep 搜索文档，`grep -i <pattern> | fpp`
3. [fpp](https://github.com/facebook/PathPicker) 支持将 grep 搜索到后的结果输入到管道里面，可以从搜索结果中直接打开文件。

### 文章列表

* [B 站异步爬虫初体验](./posts/bilibili-asyncio-crawler.md)
* [CentOS 中搭建 nfs 服务](./posts/centos-nfs-server.md)
* [CentOS 时间同步](./posts/centos-sync-ntp.md)
* [Docker 解决拉取镜像被墙的问题](./posts/fix-docker-pull-images.md)
* [Git 常用命令整理](./posts/git-common-command.md)
* [Git 彻底删除大文件](./posts/git-remove-huge-object.md)
* [Git tag版本代码快速修复](./posts/git-tag-repair.md)
* [Git http模式保存账号和密码](./posts/git-save-http-password.md)
* [Kubernetes 访问 dashboard](./posts/k8s-dashboard.md)
* [Kubernetes 修改 kube-porxy ipvs 模式](./posts/k8s-ipvs-mode.md)
* [Kubernetes 中使用 nfs-storageclass 持久化数据](./posts/k8s-nfs-storageclass.md)
* [Kubernetes Tips](./posts/k8s-tips.md)
* [Python 并行与并发](./posts/python-concurrency-parallelism.md)
* [Python 的编码和解码](./posts/python-decode-encode.md)
* [Python 两个神奇的装饰器](./posts/python-lru-singledispatch.md)
* [Python 魔法方法](./posts/python-magic-function.md)
* [Python 从零开始写出简易版跳一跳外挂](./posts/python-wechat-jump-game.md)
* [Vim 实用技巧](./posts/vim-tips.md)
* [Linux 下无法删除的字符](./posts/linux-can-not-delete-char.md)
* [Linux 查看磁盘空间大小命令](./posts/linux-disc-size.md)
* [Linux 动态库的符号冲突问题](./posts/linux-dynamic-library-conflict.md)
* [InstanceNorm 反向梯度推导](./posts/instancenorm.md)

