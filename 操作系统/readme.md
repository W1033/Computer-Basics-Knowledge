# 操作系统





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
