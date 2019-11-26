# Linux 下无法删除的字符

```shell
# 在linux下使用zsh时出现tab补全时多出字符且无法删除，如下：
$ cd ->  ccd ->  backspace  ->  c

# 修改.zshrc
$ export LC_ALL="en_US.UTF-8"
```