# 01 -- 起步
介绍版本控制系统 (VCSs) 和 Git 的基本概念

## Catalog
1. 起步(Getting Started)
    + 1.1 关于版本控制
        - 1.1.1 本地版本控制系统
        - 1.1.2 集中化的版本控制系统
        - 1.1.3 分布式版本控制系统
    + 1.2 Git 简史
    + 1.3 Git 基础
        + 1.3.1 直接记录快照, 而非差异比较
        + 1.3.2 近乎所有操作都是本地执行
        + 1.3.3 Git 保证完整性
        + 1.3.4 Git 一般只添加数据
        + 1.3.5 三种状态
    + 1.4 命令行
    + 1.5 安装 Git
        + 1.5.1 在 Linux 上安装
        + 1.5.1 在 Mac 上安装
        + 1.5.1 在 Windows 上安装
        + 1.5.1 从源代码安装
    + 1.6 初次运行 Git 前的配置
        + 1.6.1 ⽤用户信息
        + 1.6.2 本编辑器器
        + 1.6.3 检查配置信息
    + 1.7 获取帮助
    + 1.8 总结



## New Words
- centralize `/ˈsentrəˌlaɪz/` --vt.(使)集中; 使集权.  --vi.集中, 中央集权
- perforce `/pə'fɔːs/` --adv.必然地；不得已
- database `/'deitəbeis/` --n.数据库,资料库.
- stage `/steɪdʒ/` --n.阶段, 舞台, 期. --v.表演
- perforce `/pɚ'fɔrs/` --adv.强制地,强迫地; 必然地; 一定地
- efficient `/ɪ'fɪʃ(ə)nt/` --adj.有效率的, 能胜任的
- basically `/ˈbeisikəli/` --adv.基本上,根本上,本质上 
- identical `/aɪ'dentɪk(ə)l/` --adj.相同的, 一致的 


## Content
### 1. 起步
本章关于开始学习 Git.  我们从介绍有关版本控制工具的一些背景知识开始, 
然后讲解如何在你的系统运行 Git, 最后是关于如何设置 Git 开始你的工作. 
通过本章的学习, 你应该了解为什么你应该使用 Git 以及你应该如何设置以便使用 Git. 

#### 1.1 关于版本控制
什么是 "版本控制 (version control)"? 版本控制是一种记录一个或若干文件内容变化, 
以便将来查阅特定版本修订情况的系统. 在本书所展示的例子中, 
我们对保存着软件源代码的文件作版本控制, 但实际上, 
你可以对**任何类型**的文件进行版本控制.

如果你是位 图形(a graphic) 或 网页设计师(web designer),
可能会需要保存某一幅图片或页面布局文件的所有修订版本
(这或许是你非常渴望拥有的功能), 采用
`版本控制系统(VCS: Version Control System)`是个明智的选择.
有了它你就可以将某个文件回溯到之前的状态, 甚至将整个项目都回退到过去某个时间点的状态,
你可以比较文件的变化细节, 查出最后是谁修改了哪个地方,
从而找出导致怪异问题出现的原因, 又是谁在何时报告了某个功能缺陷等等. 
使用版本控制系统通常还意味着, 就算你乱来一气把整个项目中的文件改的改删的删, 
你也照样可以轻松恢复到原先的样子. 但额外增加的工作量却微乎其微. 

##### 1.1.1 本地版本控制系统
许多人习惯用复制整个项目目录的方式来保存不同的版本, 或许还会改名加上备份时间以示区别. 
这么做唯一的好处就是简单, 但是特别容易犯错. 为了解决这个问题, 
人们很久以前就开发了许多种本地版本控制系统, 
大多都是采用某种简单的数据库来记录文件的历次更新差异. 

<img src="./pro-git-images/01-images/local.png"
    style="margin-left: 0; border-radius: 4px; width: 66%;
        box-shadow: 1px 1px 3px 2px #e5e5e5">

其中最流行的一种叫做 RCS, 现今许多计算机系统上都还看得到它的踪影. 
甚至在流行的 Mac OS X 系统上安装了开发者工具包之后, 也可以使用 rcs 命令. 
它的工作原理是在硬盘上保存补丁集（补丁是指文件修订前后的变化）；通过应用所有的补丁, 
可以重新计算出各个版本的文件内容. 

##### 1.1.2 集中化的版本控制系统
接下来人们又遇到一个问题, 如何让在不同系统上的开发者协同工作？于是, 
`集中化的版本控制系统（Centralized Version Control Systems, 简称 CVCS)`
应运而生.这类系统, 诸如 CVS、Subversion 以及 Perforce 等, 
都有一个单一的集中管理的服务器, 保存所有文件的修订版本, 
而协同工作的人们都通过客户端连到这台服务器, 取出最新的文件或者提交更新. 
多年以来, 这已成为版本控制系统的标准做法. 

<img src="./pro-git-images/01-images/centralized.png"
    style="margin-left: 0; border-radius: 4px; width: 66%;
        box-shadow: 1px 1px 3px 2px #e5e5e5">

这种做法带来了许多好处, 特别是相较于老式的本地 VCS 来说. 现在, 
每个人都可以在一定程度上看到项目中的其他人正在做些什么.
而管理员也可以轻松掌控每个开发者的权限, 并且管理一个 CVCS 
要远比在各个客户端上维护本地数据库来得轻松容易. 

事分两面, 有好有坏. 这么做最显而易见的缺点是中央服务器的单点故障. 
如果宕机一小时, 那么在这一小时内, 谁都无法提交更新, 也就无法协同工作. 
如果中心数据库所在的磁盘发生损坏, 又没有做恰当备份, 
毫无疑问你将丢失所有数据——包括项目的整个变更历史, 
只剩下人们在各自机器上保留的单独快照. 本地版本控制系统也存在类似问题, 
只要整个项目的历史记录被保存在单一位置, 就有丢失所有历史更新记录的风险. 

##### 1.1.3 分布式版本控制系统
于是分布式版本控制系统（Distributed Version Control System, 简称 DVCS）
面世了. 在这类系统中, 像 Git、Mercurial、Bazaar 以及 Darcs 等, 
**客户端并不只提取最新版本的文件快照, 而是把代码仓库完整地镜像下来**. 这么一来, 
任何一处协同工作用的服务器发生故障, 事后都可以用任何一个镜像出来的本地仓库恢复. 
因为每一次的克隆操作, 实际上都是一次对代码仓库的完整备份. 

<img src="./pro-git-images/01-images/distributed.png"
    style="margin-left: 0; border-radius: 4px; width: 66%;
        box-shadow: 1px 1px 3px 2px #e5e5e5">

更进一步, 许多这类系统都可以指定和若干不同的远端代码仓库进行交互. 籍此,
你就可以在同一个项目中, 分别和不同工作小组的人相互协作. 
你可以根据需要设定不同的协作流程, 比如层次模型式的工作流,
而这在以前的集中式系统中是无法实现的. 

#### 1.2 Git 简史
同生活中的许多伟大事物一样, Git 诞生于一个极富纷争大举创新的年代. 

Linux 内核开源项目有着为数众广的参与者. 绝大多数的 Linux
内核维护工作都花在了提交补丁和保存归档的繁琐事务上（1991－2002年间）. 
到 2002 年, 整个项目组开始启用一个专有的分布式版本控制系统 BitKeeper
来管理和维护代码. 

到了 2005 年, 开发 BitKeeper 的商业公司同 Linux 内核开源社区的合作关系结束, 
他们收回了 Linux 内核社区免费使用 BitKeeper 的权力. 这就迫使 Linux 开源社区
(特别是 Linux 的缔造者 Linus Torvalds) 基于使用 BitKeeper 时的经验教训, 
开发出自己的版本系统.他们对新的系统制订了若干目标: 
+ 速度
+ 简单的设计
+ 对非线性开发模式的强力支持（允许成千上万个并行开发的分支）
+ 完全分布式
+ 有能力高效管理类似 Linux 内核一样的超大规模项目（速度和数据量）
  

自诞生于 2005 年以来, Git 日臻成熟完善, 在高度易用的同时, 仍然保留着初期设定的目标.
它的速度飞快, 极其适合管理大项目, 有着令人难以置信的非线性分支管理系统
(参见 `Git 分支`(第 3 章)）

#### 1.3 Git 基础
那么, 简单地说, Git 究竟是怎样一个系统呢? 请注意接下来的内容非常重要, 若你理解了
Git 的思想和基本工作原理, 用起来就会知其所以然, 游刃有余. 在开始学习 Git 的时候,
请努力分清你对其他版本管理系统的已有认知, 如 Subversion 和 Perforce 等;
这么做能帮助你使用工具时避免发生混淆. Git
在保存和对待各种信息的时候与其他版本控制系统有很大差异,
尽管操作起来的命令形式非常相近, 理解这些差异将有助于防止你使用中的困惑.

##### 1.3.1 直接记录快照, 而非差异比较
Git 和其它版本控制系统(包括 Subversion 和近似工具)的主要差别在于 Git
对待数据的方法. 概念上来区分, 其它大部分系统**以文件变更列表的方式存储信息**. 
这类系统(CVS、Subversion、Perforce、Bazaar 等等)
将它们保存的信息看作是一组基本文件和每个文件随时间逐步累积的差异. 

Checkins Over Time(随着时间的推移签入). 

<img src="./pro-git-images/01-images/deltas.png"
    style="margin-left: 0; border-radius: 4px; width: 66%;
        box-shadow: 1px 1px 3px 2px #e5e5e5">

Figure 4. Storing data as changes to a base version of each file.
(存储数据作为对每个文件基本版本的更该.)

Git doesn't think of or store its data this way. Instead, Git thinks
of its data more like a set of snapshots of a miniature filesystem.
Every time you commit, or save the state of your project in Git, it
basically takes a picture of what all you files look like at that
moment and stores a reference to that snapshot. To be efficient. if
files have not changed, Git doesn't store the file again, just a link
to the previous identical file it has already stored. Git thinks about
its data more like a **stream of snapshots**.

(Git 不按照以上方式对待或保存数据. 反之, Git 认为数据更像是一组微型文件系统的快照.
每次你提交或将项目状态保存在 Git 中时, 它基本上都会拍下当前所有文件的样子,
并存储对该快照的引用. 为了高效, 如果文件没有修改, Git 不再重新存储该文件,
而是只保留一个链接指向之前已经存储的相同文件. Git 对待数据更像是一个**快照流**.)

<img src="./pro-git-images/01-images/snapshots.png"
    style="margin-left: 0; border-radius: 4px; width: 66%;
        box-shadow: 1px 1px 3px 2px #e5e5e5">

Figure 5. Storing data as snapshots of the project over time.
(随着时间的推移将数据存储为项目的快照).

**Additional Info:** 此处添加一下对上图的解说, 比如当前的项目里有 `File A`,
`File B`, `File C` 几个文件, 它们在被提交到 Git 数据库中时,
会按照当前的样子存储一张快照, 这就是上图中的 `Version 1`; 当你第二次修改了 `B` 文件,
再次提交到 Git 仓库时, Git 仍然会把当前所有文件的样子存储为一张快照, 这就是
`Version 2`, 当然 Git 内部还是做了处理的, 那些没有做修改的文件,
只会保留一个链接指向之前已经存储的相同文件.

##### 1.3.2 近乎所有操作都是本地执行
在 Git 中的绝大多数操作都只需要访问本地文件和资源，一般不需要来自网络上其它计算机的信息. 
如果你习惯于所有操作都有网络延时开销的集中式版本控制系统，Git 在这方面会让你感到速度超凡. 因为你在本地磁盘上就有项目的完整历史，所以大部分操作看起来瞬间完成. 

举个例子, 要浏览项目的历史, Git 不需外连到服务器去获取历史, 
然后再显示出来——它只需直接从本地数据库中读取. 你能立即看到项目历史. 
如果你想查看当前版本与一个月前的版本之间引入的修改, Git
会查找到一个月前的文件做一次本地的差异计算, 
而不是由远程服务器处理或从远程服务器拉回旧版本文件再来本地处理. 

##### 1.3.3 Git 保证完整性
Git 中所有数据在存储前都计算校验和, 然后以校验和来引用. 这意味着不可能在 Git
不知情时更改任何文件内容或目录内容. 这个功能建构在 Git 底层, 是构成 Git
哲学不可或缺的部分. 若你在传送过程中丢失信息或损坏文件, Git 就能发现. 

Git 用以计算校验和的机制叫做 `SHA-1 散列(hash 哈希)`. 这是一个由 40
个十六进制字符(0-9 和 a-f)组成的字符串, 基于 Git 中文件的内容或目录结构计算出来.
SHA-1 哈希看起来是这样:

`24b9da6552252987aa493b52f8696cd6d3b00373`

Git 中使用这种哈希值的情况很多, 你将经常看到这种哈希值. 实际上,
Git 数据库中保存的信息都是以文件内容的哈希值来索引, 而不是文件名. 

##### 1.3.4 Git 一般只添加数据
你执行的 Git 操作, 几乎只往 Git 数据库中增加数据. 很难让 Git 执行任何不可逆操作,
或者让它以任何方式清除数据. 同别的 VCS 一样,
未提交更新时有可能丢失或弄乱修改的内容; 但是一旦你提交快照到 Git 中,
就难以再丢失数据, 特别是如果你定期的推送数据库到其它仓库的话. 

这使得我们使用 Git 成为一个安心愉悦的过程. 更深度探讨 Git
如何保存数据及恢复丢失数据的话题, 请参考 [撤消操作]()
(见: `02-Git基础.md` -- `撤销操作).

##### 1.3.5 三种状态
请注意, 如果你希望后面的学习更顺利, 请记住下面这些 Git 的改变.
Git 有三种状态, 你的文件可能处于其中之一:
+ (1) `已提交(committed)`: 已提交表示数据已经安全的 保存在本地数据库中.  
+ (2) `已修改(modified)`: 已修改表示修改了文件, 但还没保存到数据库中.  
+ (3) `已暂存(staged)`: 已暂存表示对一个已修改文件的当前 版本做了标记,
  使之包含在下次提交的快照中. 
  

由此引入 Git 项目的 3 个工作区域的概念: `Git 仓库`、`工作目录` 以及 `暂存区域`. 

<img src="./pro-git-images/01-images/areas.png"
    style="margin-left: 0; border-radius: 4px; width: 66%;
        box-shadow: 1px 1px 3px 2px #e5e5e5">

Figure 6. 工作目录, 暂存区域 以及 Git 仓库.
+ (1) `Git 仓库目录(.git directory)`: 是 Git
  用来保存项目的元数据和对象数据库的地方. 这是 Git 中最重要的部分, 
  从其它计算机克隆仓库时, 拷贝的就是这里的数据.    
+ (2) `工作目录(Working Directory)`: 是对项目的某个版本独立提取出来的内容.
  这些从 Git 仓库的压缩数据库中提取出来的文件, 放在磁盘上供你使用或修改. 
+ (3) `暂存区域(staging area)`是一个文件, 保存了下次将提交的文件列表信息,
  一般在 Git 仓库目录中. 有时候也被称作“索引”, 不过一般说法还是叫暂存区域.   
  基本的 Git 工作流程如下:
    + 1. 在工作目录中修改文件. 
    + 2. 暂存文件, 将文件的快照放入暂存区域. 
    + 3. 提交更新, 找到暂存区域的文件, 将快照永久性存储到 Git 仓库目录. 
  

如果 Git 目录中保存着特定版本的文件, 就属于已提交状态. 如果作了修改并已放入暂存区域,
就属于已暂存状态. 如果自上次取出后, 作了修改但还没有放到暂存区域, 就是已修改状态.
在 Git 基础一章, 你会进一步了解这些状态的细节, 并学会如何根据文件状态实施后续操作,
以及怎样跳过暂存直接提交.       


#### 1.4 命令行
Git 有多种使用方式.  你可以使用原生的命令行模式, 也可以使用 GUI 模式, 这些 GUI
软件也能提供多种功能.在本书中, 我们将使用命令行模式. 这是因为首先,
只有在命令行模式下你才能执行 Git 的 所有 命令, 而大多数的 GUI 软件只实现了 Git
所有功能的一个子集以降低操作难度. 如果你学会了在命令行下如何操作, 那么你在操作
GUI 软件时应该也不会遇到什么困难, 但是, 反之则不成立. 
此外由于每个人的想法与侧重点不同, 不同的人常常会安装不同的 GUI 软件,
但所有人一定会有命令行工具. 

假如你是 Mac 用户, 我们希望你懂得如何使用终端(Terminal); 假如你是 Windows 用户,
我们希望你懂得如何使用命令窗口（Command Prompt）或 PowerShell.
如果你尚未掌握以上技能, 我们建议你先停下来快速学习一下,
本书中的讲述和举例将用到这些技能. 

#### 1.5 安装 Git
在你开始使用 Git 前, 需要将它安装在你的计算机上. 即便已经安装, 
最好将它升级到最新的版本. 你可以通过软件包或者其它安装程序来安装, 
或者下载源码编译安装. 

**NOTE:** 本书写作时使用的 Git 版本为 2.0.0. 
我们使用的大部分命令仍然可以在很古老的 Git 版本上使用, 
但也有少部分命令不好用或者在旧版本中的行为有差异. 因为 Git 
在保持向后兼容方面表现很好, 本书使用的这些命令在 2.0 之后的版本应该有效. 
##### 1.5.1 在 Linux 上安装
见[在线文档](https://www.progit.cn/#_%E5%AE%89%E8%A3%85_git), 此处省略
##### 1.5.1 在 Mac 上安装
同上
##### 1.5.1 在 Windows 上安装
同上
##### 1.5.4 从源代码安装
同上


#### 1.6 初次运行 Git 前的配置
安装了 Git, 后来定制你的 Git 环境. 每台计算机上只需要配置一次,
程序升级时会保留配置信息. 你可以在任何时候再次通过运行命令来修改它们.

Git 自带一个 `git config` 的工具来帮助设置控制 Git 外观和行为的配置变量.
这些变量存储在 3 个不同的位置:
+ (1) `/ect/gitconfig` 文件: 包含系统上每一个用户及他们仓库的通用配置.
  如果使用带有 `--system` 选项的 `git config` 时, 它会从此文件读写配置变量.
+ (2) `~/.gitconfig` 或 `~/.config/git/config` 文件:只针对当前用户.
  可以传递 `--global` 选项让 Git 读写此文件.
    - 例如, 我使用下面 shell 脚本打开本机的 `.gitconfig` 文件: 
      ```shell
        open ~/.gitconfig
      ```
      里面的内容如下:
      ```base
        [user]
            name = Watermelon1033
            email = forownwang@gmail.com
        [core]
            autocrlf = input
            excludesfile = /Users/WANG/.gitignore_global
        [difftool "sourcetree"]
            cmd = opendiff \"$LOCAL\" \"$REMOTE\"
            path = 
        [mergetool "sourcetree"]
            cmd = /Applications/Sourcetree.app/Contents/Resources/opendiff-w.sh \"$LOCAL\" \"$REMOTE\" -ancestor \"$BASE\" -merge \"$MERGED\"
            trustExitCode = true
        [commit]
            template = /Users/WANG/.stCommitMsg
        [filter "lfs"]
            smudge = git-lfs smudge -- %f
            process = git-lfs filter-process
            required = true
            clean = git-lfs clean -- %f
        [https]
            proxy = 127.0.0.1:1087
        [http]
            proxy = 127.0.0.1:1087
      ```
+ (3) 当前使用仓库的 Git 目录中的 `config` 文件(就是 `.git/config`): 针对该仓库.

每一个级别覆盖上一级别的配置, 所以 `.git/config` 的配置变量会覆盖
`/etc/gitconfig` 中的配置变量. 

在 Windows 系统中, Git 会查找 `$HOME` 目录下(一般情况下是 `C:\Users\$USER`)
的 `.gitconfig` 文件. Git 同样也会寻找 `/etc/gitconfig` 文件, 但只限于
MSys 的根目录下, 即安装 Git 时所选的目标位置. 

##### 1.6.1 用户信息
当安装完 Git 应该做的第一件事就是设置你的用户名称与邮件地址. 这样做很重要,
因为每一次 Git 的提交都会使用这些信息, 并且它会写入到你的每一次提交中, 不可更改:

```shell
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```
再次强调, 如果使用了 `--global` 选项, 那么该命令只需要运行一次, 
因为之后无论你在该系统上做任何事情, Git 都会使用那些信息. 
当你想针对特定项目使用不同的用户名称与邮件地址时, 
可以在那个项目目录下运行没有 `--global` 选项的命令来配置. 

很多 GUI 工具都会在第一次运行时帮助你配置这些信息. 

##### 1.6.2 文本编辑器 
既然用户信息已经设置完毕, 你可以配置默认文本编辑器了, 当 Git
需要你输入信息时会调用它.  如果未配置, Git 会使用操作系统默认的文本编辑器, 
通常是 Vim.  如果你想使用不同的文本编辑器, 例如 Emacs, 可以这样做:
```shell
git config --global core.editor emacs
```
**WARNING**: Vim 和 Emacs 是像 Linux 与 Mac 等基于 Unix
的系统上开发者经常使用的流行的文本编辑器.
如果你对这些编辑器都不是很了解或者你使用的是 Windows 系统,
那么可能需要搜索如何在 Git 中配置你最常用的编辑器. 如果你不设置编辑器并且不知道
Vim 或 Emacs 是什么, 当它们运行起来后你可能会被弄糊涂、不知所措. 

##### 1.6.3 检查配置信息
如果想要检查你的配置, 可以使用 `git config --list` 命令来列出所有 Git
当时能找到的配置. 
```shell
$ git config --list
user.name=John Doe
user.email=johndoe@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
...
```
你可能会看到重复的变量名, 因为 Git 会从不同的文件中读取同一个配置(例如:
`/etc/gitconfig` 与 `~/.gitconfig`). 这种情况下, 
Git 会使用它找到的每一个变量的最后一个配置. 

你可以通过输入 `git config <key>`: 来检查 Git 的某一项配置 
```shell
git config user.name
```
输出 `John Doe`

#### 1.7 获取帮助
若你使用 Git 时需要获取帮助, 有三种方法可以找到 Git 命令的使用手册:
```shell
git help <verb>
git <verb> --help
man git-<verb>
```
例如, 要想获得 config 命令的手册, 执行
```shell
git help config
```
这些命令很棒, 因为你随时随地可以使用而无需联网.
如果你觉得手册或者本书的内容还不够用, 你可以尝试在 Freenode IRC 服务器
(irc.freenode.net)的 #git 或 #github 频道寻求帮助.  这些频道经常有上百人在线,
他们都精通 Git 并且乐于助人. 

#### 1.8 总结
你应该已经对 Git 是什么、Git 与你可能正在使用的集中式版本控制系统有何区别等问题有了基本的了解. 现在,  在你的个人系统中应该也有了一份能够工作的 Git 版本.
是时候开始学习有关 Git 的基础知识了. 
