[Licensed under the CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh)

文档不定时更新，如有疑问请及时联系本文作者，当前文档版本1.0.0

[阿里云](https://developer.aliyun.com/mirror/) [清华](https://mirrors.tuna.tsinghua.edu.cn/) [科大](https://mirrors.ustc.edu.cn/) [腾讯](https://mirrors.cloud.tencent.com/) [网易](http://mirrors.163.com/)

## 挂在光盘/镜像
~~~
// 查看光盘或镜像挂载完整路径
[root@oa ~]# ls -l /dev | grep cdrom
lrwxrwxrwx 1 root root 3 11月 8 21:54 cdrom -> sr0
crw-rw---- 1 root cdrom 21, 1 11月 8 21:54 sg1
brw-rw----+ 1 root cdrom 11, 0 11月 8 21:54 sr0
// 挂载
[root@oa ~]# mount /dev/cdrom /media/
mount: block device /dev/sr0 is write-protected, mounting read-only
// 配置本地yum(Red Hat)
[root@oa ~]# vi /etc/yum.repos.d/rhel-source.repo    
baseurl=file:///media/Server
enabled=1
// 配置本地yum(CentOS)
[root@oa ~]# vi /etc/yum.repos.d/CentOS-Media.repo
baseurl=file:///media/
enabled=1

// 注意：将   /etc/yum.repos.d/   其他文件重命名

// 检查本地或者网上yum
[root@oa ~]# yum list
// 清除yum缓存
[root@oa ~]# yum clean all 
// 缓存本地yum
[root@oa ~]# yum makecache
~~~