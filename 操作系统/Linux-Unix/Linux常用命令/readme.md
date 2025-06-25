# Linux 常用命令

> [!Tip]
>
> Created: 2025.06.25
>
> Source: [Linux 命令参考](https://i.linuxtoy.org/docs/guide/ch02s02.html)
>
> Edited: Gemini 2.5 pro



## ▲ Linux 常用命令表格

| index | 命令 (Command) | 英文释义 (Description)                          | 中文说明与备注 (Notes)                                       |
| ----- | -------------- | ----------------------------------------------- | ------------------------------------------------------------ |
| 1     | `ls`           | **L**i**s**t directory contents                 | 列出当前目录下的文件和文件夹。                               |
| 2     | `pwd`          | **P**rint **W**orking **D**irectory             | 显示当前所在的目录路径。                                     |
| 3     | `cd`           | **C**hange **D**irectory                        | 切换目录。用法如下：  • `cd ..`：返回上层目录。<br> • `cd /`：返回到根目录。<br> • `cd ~`：进入当前用户的家目录。<br> • `cd -`：返回到上次所在的目录。<br> • `cd <路径>`：切换到指定路径，如 `cd /Applications`。 |
| 4     | `mkdir`        | **M**a**k**e **Dir**ectory                      | 创建一个新目录。                                             |
| 5     | `rm`           | **R**e**m**ove                                  | 删除一个或多个文件。                                         |
| 6     | `rmdir`        | **R**e**m**ove **Dir**ectory                    | 删除一个 **空** 目录。                                       |
| 7     | `cp`           | **C**o**p**y                                    | 复制文件或目录。                                             |
| 8     | `mv`           | **M**o**v**e                                    | 移动或重命名文件 / 目录。                                    |
| 9     | `ps`           | **P**rocess **S**tatus                          | 显示当前正在运行的进程列表。                                 |
| 10    | `grep`         | **G**lobal **R**egular **E**xpression **P**rint | 在文件或输出中搜索匹配的文本行（支持正则表达式）。           |
| 11    | `find`         | **Find** a file                                 | 在文件系统中实时查找文件（精确，但速度较慢）。               |
| 12    | `locate`       | **Locate** a file                               | 从系统数据库缓存中查找文件（速度快，但可能不是最新的）。     |
| 13    | `man`          | **Man**ual                                      | 显示命令的帮助手册，是 Linux 下的 " 说明书 "。               |
| 14    | `clear`        | **Clear** the screen                            | 清空终端屏幕。                                               |
| 15    | `less`         | **Less** is more                                | 分页查看文件内容，比 `more` 命令功能更强大。                 |
| 16    | `nano`         | **N**ano's **ANO**ther editor                   | 一个简单易用的命令行文本编辑器。                             |
| 17    | `view`         | **View** a file                                 | 以只读模式启动 `vim` 编辑器，防止意外修改文件。              |
| 18    | `sudo`         | **S**uper **U**ser **Do**                       | 以超级用户（root）的权限执行指定的命令。                     |
| 19    | `su`           | **S**witch **U**ser                             | 切换用户账号（若不指定用户名，则默认为 root）。              |



## ▲ `mkdir -p` 中的 `-p` 是什么意思

> [!Note]
>
> Added: 2025.06.25
>
> Source: Gemini 2.5 pro

不客气！这是一个非常实用的问题。

`mkdir -p` 命令中的 `-p` 是 **`--parents`** 的缩写，它的核心作用是 **“递归创建目录”**。

简单来说，当你需要创建一个深层次的、其父目录可能还不存在的目录时，`-p` 选项会自动帮你创建所有缺失的父级目录。


### 对比说明

为了让你更直观地理解，我们来看一个有无 `-p` 的对比：

假设你当前在一个空目录下，想创建一个路径为 `project/src/components` 的文件夹。

#### 1. **不使用 `-p`**

如果你直接运行：

```bash
mkdir project/src/components
```

系统会返回一个错误：

```
mkdir: cannot create directory ‘project/src/components’: No such file or directory
```

**原因**：因为 `project` 目录和 `project/src` 目录都不存在，`mkdir` 无法直接在不存在的路径下创建子目录 `components`。你必须一步一步地创建：

```bash
mkdir project
mkdir project/src
mkdir project/src/components
```

#### 2. **使用 `-p`**

如果你使用 `-p` 选项：

```bash
mkdir -p project/src/components
```

命令会成功执行，没有任何报错。它会自动完成以下操作：

1.  检查 `project` 目录是否存在，如果不存在，就创建它。
2.  接着检查 `project/src` 目录是否存在，如果不存在，就创建它。
3.  最后创建 `project/src/components` 目录。


### 一个额外的好处

`-p` 还有一个非常方便的特性：**如果目录已经存在，它不会报错**。

这个特性让它在编写自动化脚本时特别有用，因为你可以反复执行 `mkdir -p <目录名>` 来确保某个目录一定存在，而不用担心脚本因为目录已存在而中断。

### 总结

记住这个关键点：

> 当你想一次性创建多层嵌套的目录，或者想确保一个目录存在而不关心它是否已经被创建时，就使用 `mkdir -p`。

这是 Linux/macOS 系统中一个使用频率非常高的命令选项。



## ▲ 高频实用命令 和 Linux 学习书籍推荐

> [!Note]
>
> Added: 2025.06.25
>
> Source: Gemini 2.5 pro

### 一、再介绍一个高频实用命令：`find`

如果说 `mkdir -p` 是创建文件的“神器”，那么 `find` 就是查找文件的“核武器”。它功能极其强大，是每个 Linux 用户都必须掌握的命令。

`find` 命令用于在指定的目录树中递归地搜索文件，并可以根据各种条件（如名称、类型、大小、修改时间等）进行筛选，然后对找到的文件执行操作。

**基本语法**：`find [搜索路径] [表达式选项] [操作]`

我们通过几个实用场景来理解它。



#### 场景 1：按名称查找

这是最常见的用法。比如，你想在当前目录（`.`）及其所有子目录下查找一个名为 `config.yaml` 的文件。

Bash

```
# -name 表示按名称查找，支持通配符 *
find . -name "config.yaml"
```

如果想进行模糊查找，比如查找所有 `.log` 结尾的日志文件：

Bash

```
find . -name "*.log"
```

> **Tip**: 如果想忽略大小写，可以使用 `-iname` (ignore case name)。



#### 场景 2：按类型查找

有时候你只想找目录或者文件。比如，查找所有名为 `project` 的 **目录**：

Bash

```
# -type d 表示只查找目录 (directory)
find . -type d -name "project"
```

反之，如果只想查找 **普通文件** (file)，可以使用 `-type f`。

#### 场景 3：按时间和大小查找（系统管理利器）

这是 `find` 非常强大的地方，尤其适合系统维护。

- **查找最近 7 天内被修改过的所有文件**：

    Bash

    ```
    # -mtime -7 表示修改时间 (modification time) 在7天之内
    find . -mtime -7
    ```

- **查找所有大于 100MB 的文件**：

    Bash

    ```
    # -size +100M 表示大小 (size) 超过 100 Megabytes
    # 这个命令常用于查找占用磁盘空间的大文件
    find / -type f -size +100M
    ```



#### 场景 4：`find` 的“超能力”：结合 `-exec` 执行命令

这是 `find` 最强大的功能，没有之一！它允许你对 **每一个搜索结果** 执行一个指定的命令。

它的语法是 `-exec command {} \;`

- `command` 是你要执行的命令，比如 `rm`, `cp`, `ls -l`。
- `{}` 是一个占位符，代表 `find` 命令找到的每一个文件。
- `\;` 表示 `-exec` 命令的结束。

**实战举例：**

1. **找到并删除所有临时文件**：查找当前目录下所有 `.tmp` 后缀的文件，并直接删除它们。

    Bash

    ```
    # 找到所有名为 *.tmp 的文件，并执行 rm 命令删除它
    find . -type f -name "*.tmp" -exec rm {} \;
    ```

    ( 更现代的写法是使用 `-delete` 选项 : `find . -type f -name "*.tmp" -delete`)

2. **批量修改文件权限**：找到所有 `.sh` 脚本文件，并赋予它们可执行权限。

    Bash

    ```
    find . -type f -name "*.sh" -exec chmod +x {} \;
    ```

**总结**：`find` 命令的强大之处在于其精细的筛选能力和 `-exec` 提供的批量处理能力。一旦掌握，它将成为你管理文件系统不可或缺的工具。

### 二、关于 Linux 系统学习的书籍推荐

选择合适的书籍是系统学习的关键。这里为你推荐几本从入门到精通的经典著作，它们各有侧重，口碑极佳。

#### 1. 入门首选（专注于命令行）

- **《The Linux Command Line: A Complete Introduction》** ( 中文名：《Linux 命令行大全》) by William Shotts
    - **推荐理由**：**公认的最佳入门书，没有之一**。作者的网站（[linuxcommand.org](https://linuxcommand.org/)）上甚至提供免费的 PDF 版本。这本书从零开始，以非常友好和易于理解的方式讲解了 Shell 和常用命令，并穿插了大量实践练习。它只专注于“命令行”这一件事，并做到了极致。
    - **适合人群**：所有 Linux 初学者。
- **《鸟哥的 Linux 私房菜 — 基础学习篇》** by 鸟哥（VBird）
    - **推荐理由**：**华语世界最经典的 Linux 入门“圣经”**。内容极其详尽，像字典一样全面，不仅教你“怎么做”，还深入讲解“为什么”。虽然篇幅很长，但如果你能静下心来啃完，你的 Linux 基础将无比扎实。
    - **适合人群**：愿意投入时间，希望构建系统、深入、全面知识体系的初学者。

#### 2. 进阶读物（理解系统原理）

- **《How Linux Works: What Every Superuser Should Know》** ( 中文名：《Linux 是如何工作的》) by Brian Ward
    - **推荐理由**：当你掌握了基本命令后，这本书将带你深入理解 Linux 的“内脏”。它会讲解系统启动流程、内核、设备、网络、文件系统等核心概念。读完这本书，你将从一个命令的“使用者”变成一个真正理解系统的“管理者”。
    - **适合人群**：已经熟悉基本命令，希望了解系统底层工作原理的进阶用户。

#### 3. 权威参考（系统管理员必备）

- **《UNIX and Linux System Administration Handbook》** ( 中文名：《UNIX & Linux 系统管理技术手册》)
    - **推荐理由**：**这本是系统管理员领域的“红宝书”**，被誉为该领域的权威指南。它覆盖了作为一名系统管理员需要知道的几乎所有知识点，从系统安装、网络服务到安全和性能调优。它更像是一本案头参考书，当你遇到具体问题时，随时可以查阅。
    - **适合人群**：专业的系统管理员、运维工程师或希望往这个方向发展的资深用户。

**学习建议**：

1. 从 **《The Linux Command Line》** 或 **《鸟哥的 Linux 私房菜 — 基础学习篇》** 开始，动手实践，打好命令行基础。
2. 然后阅读 **《How Linux Works》**，建立起对系统全局的认知。
3. 最后，将 **《UNIX and Linux System Administration Handbook》** 作为你职业生涯中长期的参考手册。

希望这些推荐能对你有所帮助！祝你在 Linux 的世界里探索愉快！

