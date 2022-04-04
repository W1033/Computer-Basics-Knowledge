

# MAC下安装win 10单系统的最快+最好方法



31 人赞同了该文章

发布于 2017-10-02，编辑于 2017-12-28

先上结论：

一、为啥装win 10单系统，因为OS X不适合我。

二、MAC下安装win 10单系统的最快+最好的办法是：GHOST+EFI！

\------------------------------------------------------------------------------------------------------------------------

方法：

一、前期准备

1、制作WIN PE启动盘，很多PE苹果启动不了，用此版本“[U盘PE装机必备 — IT天空优启通 v3.3.2017.0411](https://www.itsk.com/forum.php?mod=viewthread&tid=415848)”；

2、下载Bootcamp，注意选对的版本（百度“Bootcamp对应表”）；

3、下载Win 10 Ghost文件，我们喜欢的各种版本。

二、正式开始

1、如果OS X能用，在“磁盘工具”下进行分区，随意分，注意要选Mac os扩展模式；如果像我一样OS X不能用，那么开机command+r网络修复进入“磁盘工具”分区。

2、关机、插上U盘、开机按option，选择EFI boot进入win PE。

3、win PE下打开DiskGenius（GD 硬盘分区）进行分区。

（1）删除所有分区；

（2）菜单栏“硬盘”——>转换分区表类型为GUID格式；

（3）保存更改；

（4）新建分区。注意新建分区的时候勾选ESP！

![img](https://pic4.zhimg.com/v2-c3bbc331aa35e736675617a7c846278b_r.jpg)

4、Ghost恢复系统：win——>程序——>备份还原——>Ghost 11.5.1（熟悉的面孔）。

5、修复UEFI引导（这一步非常关键！！！）

（1）win——>程序——>系统安装——>UEfix（UEFI引导修复）；

（2）ESP分区选刚才在DiskGenius自动生成的ESP分区，如上图是F；

（3）开始修复选择win安装的根目录，即选Ghost出来系统盘里那个Windows文件夹；

（4）开始修复。

![img](https://pic1.zhimg.com/v2-991b08d2a196327a3914a90ec0829f2c_r.jpg)

6、重启安装bootcamp驱动，大功告成！



## 14 条评论

- [satyru](https://www.zhihu.com/people/satyru)2017-12-10

    您把mac系统整个都删掉了，只保留win系统，如果以后想装回mac系统，还能做到吗？

    3回复踩 举报

- [维拉蒂哦取消](https://www.zhihu.com/people/weiladiaoquxiao) (作者) 回复[satyru](https://www.zhihu.com/people/satyru)2017-12-13

    可以，command+r网络修复。

    