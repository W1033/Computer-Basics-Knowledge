# 操作系统



## ▲ Windows 系统快捷键

```md
Add: 2025.01.09
Source: https://sspai.com/post/53173
Edit: ChatGPT 4o
```

Xander: gpt, 帮我总结一下这个网站(上面)说的 快捷键好吗？以表格的形式呈现，谢谢

根据您提供的链接，以下是文章中提到的常用 Windows 快捷键汇总：

| 快捷键组合        | 功能描述                                                                 |
|---------------------|--------------------------------------------------------------------------|
| `Win + A`           | 打开操作中心（通知栏），查看通知和快速设置。                              |
| `Win + I`           | 打开 Windows 设置应用，进行系统配置。                                    |
| `Win + E`           | 打开文件资源管理器，浏览文件和文件夹。                                    |
| `Win + S`           | 打开搜索界面，快速查找应用、文件或设置。                                  |
| `Win + K`           | 打开“连接”面板，快速连接蓝牙设备或无线显示器。                            |
| `Win + D`           | 显示桌面，最小化所有打开的窗口。                                          |
| `Win + ,`           | 临时预览桌面，松开键后恢复之前的窗口状态。                                 |
| `Win + L`           | 锁定计算机，返回登录界面。                                                |
| `Win + V`           | 打开云剪贴板，查看剪贴板历史记录并进行选择。                               |
| `Win + Shift + S`   | 截图工具，选择屏幕区域进行截图。                                          |
| `Win + ;` 或 `Win + .` | 打开表情符号面板，插入 Emoji、颜文字或符号。                             |
| `Win + Ctrl + D`    | 创建新的虚拟桌面。                                                        |
| `Win + Ctrl + F4`   | 关闭当前虚拟桌面。                                                        |
| `Win + Ctrl + ←`    | 切换到左侧的虚拟桌面。                                                    |
| `Win + Ctrl + →`    | 切换到右侧的虚拟桌面。                                                    |

Xander: 这些快捷键，对应的 A、I 、E 等这些字母，在设计的时候有对应的英文单词吗？

是的，Windows 快捷键的设计通常与相应功能的英文单词首字母相关联，这样便于记忆和理解。以下是一些常见快捷键字母的含义：

| 快捷键组合       | 字母含义                                      |
|------------------|----------------------------------------------|
| **Win + A**      | **Action**，代表“操作中心”功能（Action Center）。 |
| **Win + I**      | **Settings**，与“设置”（Settings）的首字母对应。   |
| **Win + E**      | **Explorer**，对应“文件资源管理器”（File Explorer）。 |
| **Win + S**      | **Search**，代表“搜索”功能（Search）。             |
| **Win + K**      | **Connect**，与“连接”（Connect）功能对应。        |
| **Win + D**      | **Desktop**，用于快速显示“桌面”（Desktop）。      |
| **Win + L**      | **Lock**，对应“锁定”（Lock）功能。               |
| **Win + V**      | **Clipboard Viewer**，查看剪贴板历史记录。        |
| **Win + Shift + S** | **Snip**，截取屏幕的功能（Snipping Tool）。      |
| **Win + ;** 或 **Win + .** | 表情面板没有明确的单词关联，可能是设计时未特别指定。 |
| **Win + Ctrl + D** | **Desktop**，创建新虚拟桌面（Virtual Desktop）。 |
| **Win + Ctrl + F4** | 关闭当前窗口，F4 是传统关闭快捷键的延续。         |

### 设计逻辑总结：
1. **功能关联性**：快捷键大多数基于功能名称的首字母或常见缩写。
2. **直观易记**：通过直观的字母关联，方便用户快速记住功能。
3. **历史延续**：某些快捷键沿用早期 Windows 或通用快捷键设计（如 `F4` 关闭窗口）。

某些字母组合未必完全严格对应英文单词，但整体设计逻辑非常有助于用户理解和记忆。





## ▲ windows 系统如何查看电脑的型号？

> [!Note]
>
> Added: 2025.02.26
>
> Source: Perplexity

在Windows系统中，可通过多种方式快速查看电脑型号。以下是经过验证的常用方法，适用于Win10/Win11系统：

### 一、图形界面操作

1. **系统信息工具**
    - 按下 `Win + R` 打开运行窗口，输入 `msinfo32` 后回车
    - 在「系统摘要」中找到 **系统型号** 字段[1](https://blog.csdn.net/xitongzhijianet/article/details/124455784)[2](https://www.sohu.com/a/823935805_267471)[5](https://www.160.com/article/7373.html)[6](https://blog.csdn.net/wyxtx/article/details/130826163)
2. **DirectX 诊断工具**
    
    - 按下 `Win + R` 输入 `dxdiag` 回车
    - 进入 DirectX 诊断工具，在「系统」选项卡查看 **系统型号**[4](https://jingyan.baidu.com/article/22a299b5f0957adf18376a7d.html)[7](https://jingyan.baidu.com/article/f25ef2543ce932082d1b8225.html)
    
    > **设备ID是指硬件设备的唯一标识符，用于区分不同的设备。**
    >
    > **而产品ID则是指特定产品的唯一标识符，用于区分不同的型号或版本**。 
    >
    > 设备ID通常由厂商自行分配，并且是硬件设备的固有属性。 产品ID则由厂商自行确定，并且可能因不同型号或版本而不同。
3. **设置界面**
    
    - `Win + i` 打开设置 →「系统」→「关于」
    - 在「设备规格」中查看型号信息[2](https://www.sohu.com/a/823935805_267471)[5](https://www.160.com/article/7373.html)[8](https://www.160.com/article/5361.html)

### 二、命令行工具

1. **命令提示符**

    ```
    bash
    wmic csproduct get name
    ```

    （同时获取序列号可执行 `wmic csproduct get name, identifyingnumber`）[1](https://blog.csdn.net/xitongzhijianet/article/details/124455784)[3](https://www.51cto.com/article/644821.html)[6](https://blog.csdn.net/wyxtx/article/details/130826163)

2. **Windows PowerShell**

    ```powershell
    Get-CimInstance -ClassName Win32_ComputerSystem
    ```

    或

    ```powershell
    Get-CimInstance -ClassName Win32_bios
    ```

### 三、其他方式

- **设备标签**：查看笔记本底部的型号标签（部分台式机在机箱侧面）
- **BIOS界面**：开机时按F2/Del键进入BIOS查看硬件信息[8](https://www.160.com/article/5361.html)

> 提示：带管理员权限运行命令提示符/PowerShell可获得更完整信息。若需导出配置报告，在系统信息工具中使用「文件→导出」功能[5](https://www.160.com/article/7373.html)[6](https://blog.csdn.net/wyxtx/article/details/130826163)。

### Citations:

1. https://blog.csdn.net/xitongzhijianet/article/details/124455784
2. https://www.sohu.com/a/823935805_267471
3. https://www.51cto.com/article/644821.html
4. https://jingyan.baidu.com/article/22a299b5f0957adf18376a7d.html
5. https://www.160.com/article/7373.html
6. https://blog.csdn.net/wyxtx/article/details/130826163
7. https://jingyan.baidu.com/article/f25ef2543ce932082d1b8225.html
8. https://www.160.com/article/5361.html
9. https://www.crucial.tw/articles/pc-users/how-to-check-computer-specs
10. https://ofeyhong.pixnet.net/blog/post/205817446
11. https://www.160.com/article/7711.html
12. https://jingyan.baidu.com/article/e73e26c0e8ed3465acb6a701.html
13. [https://support.microsoft.com/zh-cn/windows/%E6%9F%A5%E6%89%BE%E6%9C%89%E5%85%B3%E8%AE%BE%E5%A4%87%E7%9A%84%E4%BF%A1%E6%81%AF-a66d52c8-3323-44fd-8f34-a9497bb935e1](https://support.microsoft.com/zh-cn/windows/查找有关设备的信息-a66d52c8-3323-44fd-8f34-a9497bb935e1)
14. https://www.asus.com/tw/support/faq/1030673/
15. https://jingyan.baidu.com/article/4d58d54167ddf1dcd5e9c064.html
16. https://www.honor.com/cn/support/content/zh-cn15838269/

------

来自 Perplexity 的回答: [pplx.ai/share](https://www.perplexity.ai/search/pplx.ai/share)










## ▲ 命令行快捷键

### `Ctrl+C`
通常用于停止或中断当前运行的程序或操作。当您在终端中运行长时间执行的命令或脚本时，按下 `Ctrl+C` 快捷键会立即停止该进程并返回到终端提示符。例如，您可以在使用 `ping` 命令时按下 `Ctrl+C` 来停止对远程主机的 ping 测试：
```
Copy Code$ ping example.com
PING example.com (93.184.216.34) 56(84) bytes of data.
^C
--- example.com ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2004ms
```

### `Ctrl+D`
通常用于表示结束输入或退出 Shell。当您在终端中运行某些需要输入的命令或程序时（如 Python、Groovy、Bash 等），按下 `Ctrl+D` 快捷键可以告诉程序已经到达输入结束的位置。如果您正在交互式地使用终端，并且希望退出当前 Shell 会话，则可以输入 `exit` 或按下 `Ctrl+D`。

### `Ctrl+Z`
通常用于将进程放入后台并挂起。如果您在运行一个长时间的命令或程序，而不希望在等待它完成时保持终端窗口打开，可以按下 `Ctrl+Z` 将该进程挂起，并将其放入后台执行。您可以使用 `jobs` 命令查看所有正在后台运行的进程。









