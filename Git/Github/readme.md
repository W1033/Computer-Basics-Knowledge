

# Github



## ▲ 解决 VSCode 从 github 拉取代码后，中文路径乱码的问题

### 解决办法

```bash
# 命令行模式输入
git config --global core.quotepath false
```

### 原理分析
`core.quotepath` 设为 `false` 的话，就不会对 `0x80` 以上的字符进行 quote, 故中文可以正常显示，此时，如果你查看 git 的配置文件，就会发现在 [core] 的分类下多处一条 `quotepath = false` 的选项.

### 怎么查看 git 的配置文件
```
# win 系统中，此命令需在仓库的文件夹下使用 git bash 命令行窗口查看才行，不知道为啥 vscode 不支持。
vi ~/.gitconfig
```

————————————————
原文链接：https://blog.csdn.net/qfeung/article/details/106067094





## ▲ 终端命令行打开 vscode

在指定文件夹内，使用终端命令行打开 vscode

(1) 在当前目录打开 vscode 的命令：`code .`

如果 code 命令无法使用，需要配路径，如下：

打开 bash 或者 zsh 配置文件

```bash
# bash 用户请使用
vi ~/.bash_profile 

# zsh 用户请使用
vi ~/.zshrc
```

(2) 按 **i** 键 开始输入

```ini
# 设置 vscode 启动命令别名
alias code="/Applications/Visual\Studio\Code.app/Contents/Resources/app/bin/code"
```

上面命令中双引号内容是我的 vscode 中的 code 命令路径，应换成你自己的。

**Tips**：如果路径里有空格，如 “Visual Studio Code.app” 请在每个空格前加一个反斜杠 '\'。

(3) **Esc** 退出编辑模式

(4)  输入 `:wq` 键 保存退出 vi 模式


**赠如下常用 vi 命令:**

- `:wq`  保存后退出 vi，若为 :wq! 则为强制储存后退出（常用）
- `:w`  保存但不退出（常用）
- `:w!`  若文件属性为『只读』时，强制写入该档案 
- `:q `  离开 vi （常用）
- `:q!`  若曾修改过档案，又不想储存，使用！为强制离开不储存档案。
- `:e!`  将档案还原到最原始的状态！






##  ▲ Github 搜索小技巧

### (1) 限定词

- `in:name` : name 为仓库名
    + `in:name javascript` 查出仓库名中有 javascript 的项目 
      (javascript in:name 也可以)
- `in:description`: description 为仓库项目描述
    + `in:description ES6` 查找仓库项目描述中有 ES6 关键词 的项目
- `in:readme`: 查找仓库的 readme.md 文件
    + `in:readme python` 查找仓库的 readme.md 文件 含有 python 关键词 的项目

### (2) 辅助限定词

- 可以通过限制: 
    + `size`: 项目大小
    + `followers`: 拥护者数
    + `forks`: fork 数
    + `stars`: star 数
    + `created`: 创建时间
    + `pushed`: 更新时间
    + `language`: 项目所用语言
    + `topic`: topic 标签
    + `topics`: top 标签数  
  来筛选项目，辅助限定词可以多个并用，用空格隔开就行，可以搭配限定词使用，也可单独使用.
- 下面给出一些使用示例: 
    + 名字 (name) 里有 python 的并且 stars 大于 3000 的  
      `in:name python starts:>3000`
    + 名字 (name) 里有 python 的并且 stars 大于 3000 、forks 大于 200 的  
      `in:name python starts:>3000 forks:>200`
    + 详情 (readme) 里面有 python 的并且 stars 大于 3000 的  
      `in:readme python starts:>3000`
    + 描述 (description) 里面有 python 的并且 stars 大于 3000 的  
      `in:description python starts:>3000`
    + 描述 (description) 里面有 python 的并且是 python 语言的  
      `in:description python language:python`
    + 描述 (description) 里面有 python 的并且 2019-12-20 号之后有更新过的  
      `in:description python pushed:>2019-12-20`
