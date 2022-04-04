# Github 搜索小技巧

## (1) 限定词
- `in:name` : name 为仓库名
    + `in:name javascript` 查出仓库名中有 javascript 的项目 
      (javascript in:name 也可以)
- `in:description`: description 为仓库项目描述
    + `in:description ES6` 查找仓库项目描述中有 ES6 关键词 的项目
- `in:readme`: 查找仓库的 readme.md 文件
    + `in:readme python` 查找仓库的 readme.md 文件 含有 python 关键词 的项目

## (2) 辅助限定词
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
  来筛选项目, 辅助限定词可以多个并用, 用空格隔开就行, 可以搭配限定词使用, 也可单独使用.
- 下面给出一些使用示例: 
    + 名字(name)里有 python 的并且 stars 大于 3000 的  
      `in:name python starts:>3000`
    + 名字(name)里有 python 的并且 stars 大于 3000 、forks 大于 200 的  
      `in:name python starts:>3000 forks:>200`
    + 详情(readme)里面有 python 的并且 stars 大于 3000 的  
      `in:readme python starts:>3000`
    + 描述(description)里面有 python 的并且 stars 大于 3000 的  
      `in:description python starts:>3000`
    + 描述(description)里面有 python 的并且是 python 语言的  
      `in:description python language:python`
    + 描述(description)里面有 python 的并且 2019-12-20 号之后有更新过的  
      `in:description python pushed:>2019-12-20`
