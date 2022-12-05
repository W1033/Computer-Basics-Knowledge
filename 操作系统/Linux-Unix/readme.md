# Linux-Unix



## ▲ ps -ef|grep tomcat是啥意思呢？

`ps -ef` 是用标准的格式显示进程

显示的项目有：`UID , PID , PPID , C , STIME , TTY , TIME , CMD` ，如下图所示：

![img](readme.assets/20200221141148508.png)

grep 命令是查找

中间的 `|` 是管道命令(/符)，是指 ps 命令与 grep 同时执行，

所以 `ps -ef|grep tomcat` 是显示有关 tomcat 的命令，

`ps -ef|grep xxx` 该命令用于查看进程 xxx 的相关信息。