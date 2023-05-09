# 03 -- 分支



## ▲ git branch

*注：添加笔记，以后看看能不能和下面的正文内容整合。*

**Q:** `git branch -M master` 是什么意思？

>  **ChatGPT:** 正在为您搜索：git branch -M master 是什么意思 
>
> 这是将当前分支重命名为 `master` 的 Git 命令。其中 `-M` 选项用于强制执行（即使有重名的分支存在），并且会更新任何其他参考（如其他分支和跟踪分支）来使用新名称。这个命令通常用于将默认分支从 `main` 改为 `master`。 

**Q:** git branch 后还常接哪些用法？

> **ChatGPT:** 正在为您搜索：git branch用法
>
> `git branch` 命令可以用来创建新的分支，列出已有的分支以及删除、重命名分支等。下面是 `git branch` 常用的一些子命令及其用法：
>
> - `git branch <branch-name>`: 创建一个新分支，并将其指向当前所在的提交对象。
> - `git branch -d <branch-name>`: 删除指定的分支。如果分支还没有被合并到当前分支，则会报错。
> - `git branch -D <branch-name>`: 强制删除指定的分支，即使该分支还没有被合并到当前分支。
> - `git branch -m <old-branch-name> <new-branch-name>`: 将旧分支重命名为新分支。
> - `git branch -a`: 列出所有本地和远程分支。
> - `git branch -r`: 列出所有远程分支。
> - `git branch -v`: 列出所有分支及其最后一次提交的 SHA-1 值和提交信息。
>
> 除了以上这些常用的子命令外，还有其他一些用法，例如：
>
> - `git branch -c <new-branch-name> <start-point>`: 创建一个新分支，并将其指向指定的起点（可以是任何提交对象）。
> - `git branch --no-merged`: 列出所有尚未被合并到当前分支的分支。
> - `git branch --merged`: 列出所有已经被合并到当前分支的分支。
> - `git branch --contains <commit>`: 列出包含指定提交对象的所有分支。
> - `git branch --edit-description <branch-name>`: 编辑指定分支的描述信息。






## ▲ 3. Git 分支

### 3.1 分支简介




### 3.2 分支的新建与合并




### 3.3 分支管理




### 3.4 分支开发工作流




### 3.5 远程分支




### 3.6 变基




### 3.7 总结


