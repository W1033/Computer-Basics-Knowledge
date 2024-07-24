# KB / KiB，MB / MiB，GB / GiB，… 的区别是什么？

[知乎问答链接](https://www.zhihu.com/question/24601215)


> K 单独出现时，代表 1000 或 1024
>
> K 与 Ki 一起出现时，K 代表1000，K 代表 1024
>
> K 与 k 一起出现时，K 代表1024，k 代表 1000







## Calude 3.5 Sonnet 

Add: 2024.07.24

让我解释一下原因:

1. 在计算机存储中,有两种不同的计量系统: 
    - (a) 十进制(SI)系统: 1 GB = 1000 MB 
    - (b) 二进制系统: 1 GiB = 1024 MiB
2. 如果我们使用常见的十进制系统: 10 GB = 10 * 1000 MB = 10000 MB
3. 如果我们使用二进制系统: 10 GiB = 10 * 1024 MiB = 10240 MiB

所以,正确的表述应该是:

- 10 GB = 10000 MB (使用十进制系统)
- 10 GiB = 10240 MiB (使用二进制系统)




> 1KB = 1,000 Byte
>
> 1MB = 1,000 KB
>
> 1GB = 1,000,000 KB
>
> 1TB = 1,000,000,000 KB

> 1KiB = 1,024Byte
> 
> 1MiB = 1,024KiB
> 
> 1GiB = 1,024MiB = 1,048,576 KiB
> 
> 1TiB = 1,024GiB = 1,073,741,824 KiB






## KiB = "Kibi-" + "Byte" = Kibibyte （千字节）

**1 KiB = $2^{10}$ Byte = 1024 Byte**

- TIP：bit 和 byte 的详细关系见仓库 `Learning-C-CPP\Learning-C-Language\Beginning C--Fifth Edition\1st-2nd_笔记.md`

## KB/kB = "Kilo-" + "Byte" = Kilobyte（千字节）

**1KB/kB = $10^{3}$ Byte = 1000 Byte**

