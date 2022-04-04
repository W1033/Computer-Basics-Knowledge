# 解决 Win10 新建文件夹卡顿的问题



我们在使用win10系统过程中，遇到右键鼠标打开右键菜单栏中的“新建”命令时，出现了响应速度非常缓慢的问题，怎么办？下面小编分享win10系统右键“新建”命令时响应速度非常缓慢解决方法：


## 方式一 ：改注册表（本人使用）

“win+R”打开运行，输入“regedit”打开注册表，然后定位到：计算机\HKEY_CLASSES_ROOT\Directory\Background\shellex\ContextMenuHandlers\igfxDTCM，然后右键“igfxDTCM”，选择【删除】

<img src="../readme.assets/3489393.jpg" style="border-radius: 4px; box-shadow: 1px 1px 3px 2px #e5e5e5">

**通过查询注册表信息，我的电脑内不存在igfxDTCM**
 那么，我们就需要执行下面的操作。计算机\HKEY_CLASSES_ROOT\Directory\Background\shellex\ContextMenuHandlers，这里仅保留“new”和“workfolders”两项，其余的全部删除

<img src="../readme.assets/970035.jpg" style="border-radius: 4px; box-shadow: 1px 1px 3px 2px #e5e5e5">


## 方式二 ：系统盘目录创建Intel项

这个比较简单，只要在系统盘下创建一个“Intel”文件就行。打开系统盘，右键【新建】>>【文件夹】，然后将名字改为“Intel”就行了


作者：比卡_没有丘
链接：https://www.jianshu.com/p/748ee297c007
来源：简书


## 方法三: 安装 BandZip 压软件，这样右键新建文件夹时可以使用 BandZip 的新建快捷键