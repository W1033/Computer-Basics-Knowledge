# Mac 中 Git 忽略 .DS_Store 文件

> 文章来源：https://orianna-zzo.github.io/sci-tech/2018-01/mac%E4%B8%ADgit%E5%BF%BD%E7%95%A5.ds_store%E6%96%87%E4%BB%B6/

## Git 中多出来的 .DS_Store

虽然不是第一次使用 mac，也不是第一次在 mac 上使用 git，但对 mac 实际上非常不熟悉。每次 git 上传时多出来的 .DS_Store 文件虽然不清楚具体做什么，但看上去并没什么问题 .git 一般也是自己一个人单机使用，就算换机也一般是直接换，没有遇到过两个同时使用的时候，上传 .DS_Store 也就默认都上传了。

但这次用两个 mac，一个 mac 提交了修改，第二个 mac 想要拉下来时居然遇到了 .DS_Store 文件被修改过需要提交再 merge。什么？我没改过内容呀？所以这个 .DS_Store 是什么鬼？

.DS_Store 是 Mac OS 用来存储这个文件夹的显示属性的，被作为一种通用的有关显示设置的元数据（比如图标位置等设置）为 Finder、Spotlight 用。所以在不经意间就会修改这个文件。而文件共享时为了隐私关系将 .DS_Store 文件删除比较好，因为其中有一些信息在不经意间泄露出去。

## Git 中处理方案

### 方案一：项目设置 .gitignore

仅针对 git 的处理最 naive 的想法就是设置 .gitignore 文件。

.gitignore 文件用于忽略文件，官网介绍在 [这里](https://git-scm.com/docs/gitignore)，规范如下：

- 所有空行或者以注释符号 `＃` 开头的行都会被 git 忽略，空行可以为了可读性分隔段落，`#` 表明注释。
- 第一个 `/` 会**匹配路径的根目录**，举个栗子，`/*.html` 会匹配 `index.html`，而不是 ~~`d/index.html`~~。
- 通配符 `*` 匹配一到多个任意意字符（匹配前面的 元字符(子表达式) 0次 或 多次），`?` 匹配一个任意字符（匹配前面元字符0次或1次）。需要注意的是通配符不会匹配文件路径中的 `/`，举个栗子，`d/*.html` 会匹配 `d/index.html`，但不会匹配 ~~`d/a/b/c/index.html`~~。
- 两个连续的星号 `**`有特殊含义：
    - 以 `**/` 开头表示匹配所有的文件夹，例如 `**/test.md` 匹配所有的 `test.md` 文件。
    - 以 `/**` 结尾表示匹配文件夹内所有内容，例如 `a/**` 匹配文件夹 a 中所有内容。
    - 连续星号 `**` 前后分别被 `/` 夹住表示匹配 0 或者多层文件夹，例如 `a/**/b` 匹配到 `a/b` 、`a/x/b` 、`a/x/y/b` 等。
- 前缀 `!` 的模式表示如果前面匹配到被忽略，则重新添加回来。如果匹配到的父文件夹还是忽略状态，该文件还是保持忽略状态。如果路径名第一个字符为 `!` ，则需要在前面增加 `\` 进行转义。

对于一些常用的系统、工程文件的 .gitignore 文件可以参考 [这个网站](https://www.gitignore.io/) 进行设置，这里有很多模板。

针对 .DS_Store 文件，在 git 工程文件夹中新建 .gitignore 文件，在文件中设置：

```
.gitignore
**/.DS_Store
```

对于已经提交的内容，希望 git 能够忽略，但同时并不会删除本地文件，需要在 terminal 输入以下命令：

```Shell
$ git rm -r --cached $file_path
```

这个方案的优点就是方便、快捷、最容易想到，缺点就是每个 git 项目都要重复一遍。

### 方案二：全局设置忽略

虽然每个项目配 .gitignore 文件可以成功，但是每个项目都需要配，嗯，有点烦。我们可以在 git 的全局进行配置来忽略 .DS_Store 文件。

设置之前我们先看下现在的 git config 配置情况（[git config 官方文档说明](https://git-scm.com/docs/git-config)）：

```shell
$ git config --list
```

实际上 git 配置情况可以在 `~/.gitconfig` 文件中查看。

```shell
$ vi ~/.gitconfig
```

通过 `:q!` 退出后，我们需要建立一个文件，把需要全局忽略的文件路径写入其中。该文件起名为 .gitignore_global：

```shell
$ touch ~/.gitignore_global
```

然后对这个文件进行修改。

```
# Mac OS
**/.DS_Store
```

然后对 git 进行全局设置，让 git 忽略 .gitignore_global 中的所有文件：

```shell
$ git config --global core.excludesfile ~/.gitignore_global
```

这样就不用每个 git 目录都设置忽略 .DS_Store 文件了！

## Resource 资源链接汇总

[gitignore 官方文档说明](https://git-scm.com/docs/gitignore)、[gitignore 文件模板参考](https://www.gitignore.io/)、[git config 官方文档说明](https://git-scm.com/docs/git-config)