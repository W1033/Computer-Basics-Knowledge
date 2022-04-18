# MacOS 包管理器 Homebrew

> Homebrew 官网：https://brew.sh/index_zh-cn


## New Words
### homebrew `/'həum'bru:/`
```css
├── noun
│   ├── 家酿啤酒(beer made at home), 自酿（啤）酒
```

### cask `/kæsk/`
```css
├── noun [countable]
│   ├── 〔装酒或其他液体的〕小木桶﹔一桶之量 (a round wooden container used for 
│   │    storing wine or other liquids, or the amount of liquid that it contains)
│   │   ├── a cask of rum. 一桶朗姆酒 
```

 



## Content

macOS 和 Linux 缺失软件包的管理器.(The Missing Package Manager for macOS (or Linux)) -- Homebrew 官网

**Homebrew**是一款[自由](https://zh.wikipedia.org/wiki/自由软件)及[开放源代码](https://zh.wikipedia.org/wiki/开源软件)的[软件包管理系统](https://zh.wikipedia.org/wiki/软件包管理系统)，用以简化[macOS](https://zh.wikipedia.org/wiki/MacOS)系统上的软件安装过程，最初由马克斯·霍威尔（Max Howell）写成。因其[可扩展性](https://zh.wikipedia.org/wiki/可扩展性)得到了一致好评[[3\]](https://zh.wikipedia.org/wiki/Homebrew#cite_note-3)，而在[Ruby on Rails](https://zh.wikipedia.org/wiki/Ruby_on_Rails)社区广为人知。 -- WikiPedia

### 1. 安装和卸载方式
#### 1.1 安装 
一般情况下如果网络没有受到限制，通过 Homebrew 官网里如下的命令行就可以正常安装，

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

但是在国内你懂的。。。下面这种镜像版本更快让你成功安装，下面的安装方式来源终于知乎的这篇文章 [Homebrew国内如何自动安装（国内地址）（Mac & Linux）](https://zhuanlan.zhihu.com/p/111014448)，但是为了预防原文丢失，我就备份了 Mac 下的安装方式：

**苹果电脑 常规安装脚本（推荐 完全体 几分钟安装完成）：**

```bash
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```

**苹果电脑 极速安装脚本（精简版 几秒钟安装完成）：**

```bash
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)" speed
```


#### 1.2 卸载
把上面的安装方式命令里的 `install.sh` 换成 `uninstall.sh` 即可。 

卸载完成后进入 `/usr/local` 目录下再把 Homebrew 文件夹删除就算清除干净了。



### 2. Homebrew 常用命令

Homebrew 会将软件包安装到独立目录，并将其文件软链接至 `/usr/local` 。

Homebrew 不会将文件安装到它本身目录之外，所以您可将 Homebrew 安装到任意位置。

```sh
# 查看 brew 版本
brew --version

# 搜索包
brew search xxx     

# 安装包 
brew install xxx    

# 查看包信息, 比如目前的版本, 依赖, 安装后注意事项等
brew info xxx       

# 卸载包
brew uninstall xxx  

# 显示已安装的包
brew list          

# 查看 brew 的帮助
brew --help          

# 更新, 这会更新 Homebrew 自己
brew update 

# 检查过时（是否有新版本）, 这会列出所有安装的包里, 哪些可以升级
brew outdated xxx   
# 例如: brew outdated mysql

# 升级所有可以升级的软件
brew upgrade xxx    
# 例如：brew upgrade mysql

# 清理不需要的版本极其安装包缓存
brew cleanup xxx    
# 例如：brew cleanup mysql
```
Homebrew 安装软件的存放目录: 通过 brew install 安装的所有软件存放在 `/usr/local/Cellar/` 目录下. 

可以使用 `brew list` 查看所有通过 brew 安装的软件, 然后通过显示的软件名通过 `brew list 软件名` 确定软件安装的路径..


### 3. 安装 Cask
安装命令: `brew install cask`

brew 是下载源码解压然后 `./configure`(配置) 和 make install (安装) ，同时会安装包含的相关依存库。并自动配置好各种环境变量，而且易于卸载。

这个对程序员来说简直是福音，简单的指令，就能快速安装和升级本地的各种开发环境。

而 brew cask 是已经编译好了的应用包（.dmg/.pkg），仅仅是下载解压，放在统一的目录中（/opt/homebrew-cask/Caskroom），就省掉了自己去下载、解压、拖拽（安装）等蛋疼步骤，同样，卸载相当容易与干净。这个对一般用户来说会比较方便，包含很多在 AppStore 里没有的常用软件。

