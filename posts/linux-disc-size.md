# Linux 查看磁盘空间大小命令

```shell
# Df命令是linux系统以磁盘分区为单位查看文件系统，可以加上参数查看磁盘剩余空间信息，命令格式：
$ df -hl
显示格式为：　
文件系统               容量   已用   可用 已用%  挂载点　
Filesystem            Size  Used  Avail  Use%  Mounted on
/dev/hda2              45G   19G    24G   44%  /
/dev/hda1             494M   19M   450M    4%  /boot
/dev/hda6             4.9G  2.2G   2.5G   47%  /home
/dev/hda5             9.7G  2.9G   6.4G   31%  /opt
none                 1009M     0  1009M    0%  /dev/shm
/dev/hda3             9.7G  7.2G   2.1G   78%  /usr/local
/dev/hdb2              75G   75G      0  100%  /
/dev/hdb2              75G   75G      0  100%  /

# 以上面的输出为例，表示的意思为：
# HD硬盘接口的第二个硬盘（b），第二个分区（2），容量是75G，用了75G，可用是0，因此利用率是100%， 被挂载到根分区目录上（/）。
# 下面是相关命令的解释：
$ df -hl 查看磁盘剩余空间
$ df -h  查看每个根路径的分区大小
$ du -sh [目录名] 返回该目录的大小
$ du -sm [文件夹] 返回该文件夹总M数
$ du -h  [目录名] 查看指定文件夹下的所有文件大小（包含子文件夹）

# 更多功能可以输入一下命令查看：
$ df --help
$ du --help

# 查看硬盘的分区 
$ sudo fdisk -l

# 查看IDE硬盘信息 
$ sudo hdparm -i /dev/hda

# 查看STAT硬盘信息 
$ sudo hdparm -I /dev/sda

# 查看硬盘剩余空间 
$ df -h 
$ df -H

# 查看目录占用空间 
$ du -hs 目录名

# 优盘没法卸载  
$ sync fuser -km /media/usbdisk
```