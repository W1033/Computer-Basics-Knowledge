# Git LFS

## ▲ 详解 Git LFS（arge file storage 大文件存储）

关于 GitHub 上的大文件：https://docs.github.com/zh/repositories/working-with-files/managing-large-files/about-large-files-on-github

MacOS 安装文档：https://docs.github.com/zh/repositories/working-with-files/managing-large-files/installing-git-large-file-storage

使用文档：https://docs.github.com/zh/repositories/working-with-files/managing-large-files/configuring-git-large-file-storage

> 1. 打开终端。
>
> 2. 将当前工作目录更改为要用于 Git LFS 的现有仓库。
>
> 3. 要将存储库中的文件类型与 Git LFS 相关联，请输入 `git lfs track`，后跟要自动上传到 Git LFS 的文件扩展名的名称。
>
>     例如，要关联 .psd 文件，请输入以下命令：
>
>     ```shell
>     $ git lfs track "*.psd"
>     > Adding path *.psd
>     ```
>
>     需要将每种要与 Git LFS 关联的文件类型和 `git lfs track` 一起添加。 此命令将修改存储库的 .gitattributes 文件，并将大文件与 Git LFS 相关联。
>
>     注意：强烈建议将本地 .gitattributes 文件提交到存储库中。
>
>     - 如果依赖与 Git LFS 关联的全局 .gitattributes 文件，可能会导致在参与其他 Git 项目时发生冲突。
>     - 在存储库中包含 .gitattributes 文件允许创建分支或新克隆的人员更轻松地使用 Git LFS 进行协作。
>     - 在存储库中包含 .gitattributes 文件允许将 Git LFS 对象选择性地包含在 ZIP 文件和 tarball 存档中。
>
> 4. 将文件添加到与关联的扩展名相匹配的仓库：
>
>     ```shell
>     $ git add path/to/file.psd
>     ```
>
> 5. 提交文件并将其推送到 GitHub：
>
>     ```shell
>     $ git commit -m "add file.psd"
>     $ git push
>     ```
>
>     您会看到一些有关文件上传的诊断信息：
>
>     ```shell
>     > Sending file.psd
>     > 44.74 MB / 81.04 MB  55.21 % 14s
>     > 64.74 MB / 81.04 MB  79.21 % 3s
>     ```



## ▲  Remove Git LFS

由于静态网站自动化部署和 GitHub API 自身的原因不能托管使用了**Git LFS**的 Repository。一番 Google 后没有获得有用的操作步骤。此后无意间操作成功 remove 了这个高级操作……

1. 先对你的 Repository 执行 `git lfs pull` 或者 `git lfs fetch`，确保本地的指针文件替换成你的文件
2. 删除目录下所有 **.gitattributes** 跟踪文件
3. **关键**：执行 `git rm --cached *`，其中 —cached 属性必不可少，该命令会刷新所有 Git 记录的文件缓存
4. 这时你会发现你刷新了整个 Git 记录，提示需要 add 所有的 change，不要惊慌，此时直接`git add .`并 commit 记录就可以了，到这里就已经移除了 Git LFS

注：笔记来源：https://redblue.fun/articles/remove-git-lfs/