

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







## ▲解决 Mac 下使用 V2ray 

提交代码报 `Failed to connect to github.com port 443: Operation timed out` 的问题.

- `V2ray`客户端的代理导致的, webstorm 无法提交代码到 github, 从 `iTerm` 中也可以测试, 测试代码如下:

    ```shell
      git clone https://chromium.googlesource.com/v8/v8.git
    ```

    提示错误为: 

    ```base
      fatal: unable to access 'https://chromium.googlesource.com/v8/v8.git/':
      Failed to connect to chromium.googlesource.com port 443: Operation timed out
    ```

- 同时也不知道到底是下面哪一行代码起的作用: 
    (参考文章为: https://www.zhihu.com/question/26954892)

    ```shell
      # 查看有没有设置代理的代码(本机上没效果, 但是评论里说这 2 行代码是有效果的.)
      git config --global http.proxy
      # 取消代理
      git config --global --unset http.proxy
      git config --global --unset https.proxy
    
      # 文章里另外一种说:使用以下命令确认系统是否使用了代理
      env | grep -i proxy (这个为粘贴文章中的: env | grep -i proxy)
      / - 如果有设置 https 代理, 可以使用命令去除
      unset https_proxy
    ```

- 可能需要重启电脑.  



##  ▲ 把 V2Ray 客户端的代理 IP 添加到 `/Users/WANG/.gitconfig` 中

<p style="border-left:4px solid red; padding:10px 15px; font-style:italic; background-color:#feeeee;">Added: 2023.05.02  Mac 下推荐使用 ClashX，不推荐使用 v2ray 了。</p>

查看电脑顶部的 `V2RayU` 客户端, 右键点击 `查看 config.json`, 在浏览器中打开后会看到

```js
  inbounds": [
  {
    "listen": "127.0.0.1",
    "protocol": "socks",
    "settings": {
      "udp": false,
      "auth": "noauth"
    },
    "port": "1080"
  },
  {
    "listen": "127.0.0.1",
    "protocol": "http",
    "settings": {
      "timeout": 360
    },
    "port": "1087"
  }
],
```

(2) 其中 `"protocol": "http"` 即为要设置的 http 代理, 打开 `iTerm` 输入以下命令:

```base
  git config --global http.proxy 127.0.0.1:1087
  git config --global https.proxy 127.0.0.1:1087
```

- Tip: 关于 `V2Ray` 使用的更多教程, 去 google 搜索即可.

