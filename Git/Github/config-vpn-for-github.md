# Github



## 生词(New Words)
- **stylish ['staɪlɪʃ] --adj.时尚的; 优雅的; 潇洒的.**
    + She always faced stylish and elegant. 他总是时尚和优雅相伴.
    + Most of the clothes aren't that stylish. 大部分衣服都不太时髦.








## 解决 Mac 下使用 V2ray 提交代码报 `Failed to connect to github.com port 443: Operation timed out` 的问题.
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



## 把蓝灯的代理添加到 `/Users/WANG/.gitconfig` 中:
- (1) 每次启动蓝灯，它会自动修改操作系统的网络代理指向它自己。不需要我们手动配置，很是方便。
  需要网络代理的地方其实不止是浏览器，很多命令行工具也会访问网络。比如，我们通过
  homebrew 安装 dart 的时候，brew 命令会从 Google 的服务器上下载安装文件。
  然后你就会看到网络连接错误的提示信息。

  要解决这类问题，只需要为 Shell 设置两个环境变量 HTTP_PROXY 和 HTTPS_PROXY 即可。
  我们直接利用蓝灯在本地启动好的代理端口。

  我们首先找到蓝灯在本地启动的具体端口号。打开蓝灯，依次选择 
  `Settings -> ADVANCED SETTINGS` 即可看到蓝灯在本地选择的端口号。
- (2) 打开 `iTerm`, 通过如下代码设置 proxy:
  ```base
    git config --global http.proxy 127.0.0.1:49374
    git config --global https.proxy 127.0.0.1:49374
  ```
- (3) 通过第 (2) 步设置的代码可以在 `.gitConfig` 文件中查看, 路径为
  `/Users/WANG/.gitconfig` (tip: 可以修改本地仓库代码, 提交代码到 github 便可测试.)



##  把 `V2RayU` 客户端的代理 IP 添加到 `/Users/WANG/.gitconfig` 中
- 查看电脑顶部的 `V2RayU` 客户端, 右键点击 `查看 config.json`, 在浏览器中打开后会看到
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
- (2) 其中 `"protocol": "http"` 即为要设置的 http 代理, 打开 `iTerm` 输入以下命令:
  ```base
    git config --global http.proxy 127.0.0.1:1087
    git config --global https.proxy 127.0.0.1:1087
  ```
- Tip: 关于 `V2Ray` 使用的更多教程, 去 google 搜索即可.



## Mac 下在 Chrome/ Firefox 中自定义 github 网站样式. (下面以 Chrome 为例)
1. 在 Chrome 应用商店中安装 `Stylish` 插件.
    + `Stylish`--为任意网站自定义主题: 利用用户样式管理器 Stylish
      来重新编辑网站的样式. 您可利用 Stylish 为许多网站安装主题和皮肤,
      也可创建自己的注意和皮肤.
2. 打开 `github.com` 网站, 然后点击右上角的 `Stylish` 插件图标,
   在下拉图标中点击 `为此网站查找更多样式`, 进入到 Stylish 的主页后, 
   搜索 `Github-font-size`, 打开主题后, 点击 `Install Style`,
   然后回到 `github.com` 网站, 再次点击右上角的 `Stylish` 插件图标,
   在 `已安装样式` 中显示的就是你已安装的样式,  看到 `Github-font-size`
   样式后(Tip: 服务器应该在国外, 如果没有显示请稍作等待. 如果一直没有展示, 点击
   `Stylish on` 后面竖排的 `三个小圆点`, 点击 `管理样式`,
   在打开的窗口中找到安装的样式, 点击下面的 `修改`.), 点击 `编辑`
   按钮(像铅笔一样的图标), 在打开的页面中, 把下面第 3 步自定义的 `CSS`
   代码站粘贴到右侧的框内. <br/>
   **Note**: 如果英文好, 可以不用搜索 `Github-font-size` 插件来做更改,
   你可以直接在 `Stylish` 中自己 `Create One Style` 即可.
3. 自定义的 `CSS` 样式, 这些样式会覆盖 `github` 网站中的样式.
   ```css
    body {
        color: #333333;
    }
    .line-data, #gist-form .file .input textarea, .blob-code-inner {
        font-size: 14px !important;
    }
    code, pre {
        font-size: 14px !important;
    }
    .markdown-body {
        font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Oxygen, Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
        font-size: 15px;
        line-height: 1.6;
        word-wrap: break-word;
    }
    .markdown-body .highlight pre, .markdown-body pre {
        background-color: #f6f6f6;
        border-radius: 3px;
    }
    .markdown-body code, .markdown-body tt {
        background-color: #f6f6f6;
        border-radius: 4px;
        color: #e96900;
    }
    .pl-c {
        color: #aa6633;
    }
   ```
