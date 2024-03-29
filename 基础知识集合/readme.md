# 基础知识集合



## New Words
- **bit `/bɪt/` --n.(二进制) 位, 比特; 少量. --adj.很小的; 微不足道的.**
  **--vt.控制. --adv.相当; 有点儿. --v.咬(bite 的过去式和过去分词)**
    + 1Byte = 8 bit. 1字节 = 8 比特(位)
    + a bit(n) of paper. 纸片
    + come to bits(n) 破成碎片
    + a bit of land. 一小块土地.
    + He knows a little bit of everything. 他什么都知道一点点.
- **byte `/baɪt/` --n.[计]字节; 8位元组**
    + That is the address in memory in the heap of the first byte that
      the user typed in. 那是用户输入的第一个字节在内存中堆的地址.
    + Every byte in memory has to have an "address" for a process to
      be able to locate it. 内存中的每一个字节都必须有一个 "地址",
      以便让进程可以找到它.







## 1. 计算机上常用的单位

### 1.1 数据单位
计算机中数据单位是 `bit/bɪt/(比特/位)`. 在计算机内部, 数据都是以二进制的形式存储和运行的.

> 二进制数据中的一个位(bit)简写为 b, 音译为比特, 是计算机存储数据的最小单位. 一个二进制位只能表示 0 或 1 两种状态, 要表示更多的信息, 就要把多个位组合成一个整体, 一般以 8 位二进制组成一个基本单位. 

> 字节：计算机数据处理的最基本单位, 主要以字节为单位解释信息. 字节(Byte)简记为 B, 规定一个字节为 8 位, 即 1B = 8bit。每个字节由 8 个二进制位组成. 一般情况下, 一个 ASCII 码占用一个字节, 一个汉字国际码占用两个字节. 

> 字：一个字通常由一个或若干个字节组成. 字(Word)是计算机进行数据处理时, 一次存取、加工和传送的数据长度. 由于字长是计算机一次所能处理信息的实际位数, 所以, 它决定了计算机数据处理的速度, 是衡量计算机性能的一个重要指标, 字长越长, 性能越好. 

> 数据的换算关系
`1Byte = 8bit，1KB = 1024B，1MB = 1024KB，1GB = 1024MB`. 
计算机型号不同, 其字长是不同的, 常用的字长有 8、16、32 和 64 位. 一般情况下, IBM PC/XT的字长为 8 位, 80286 微机字长为 16 位, 80386/80486 微机字长为 32 位, Pentium 系列微机字长为 64 位. 

### 1.2 速度单位

CPU 的运算速度使用的是 `MHz` 或者是 `GHz` 之类的单位。而在网络传输上使用的是 bit 单位, 因此常使用的是Mbit/s.

举例: 大家常听到的 `8M/1M` 网速, 如果转换为文件容量的 `byte` 时，其实理论上最大传输值为: 1MB/s / 125KB/s 的上传或下载速度. (tip: 下面
`### 2. xxx` 中有详细讲解.) 


## 2. `MB/S` 与 `Mbit/S` 的区别
内存的最小单位是`位 (bit)`(或称: 比特), 将 8 个位组合为一组,
称为字节(`byte`) (tip: 1byte(字节) = 8bit(比特)); 
每个字节都有唯一的地址, 字节地址从 0 开始, 第一位只能是 0 或 1.

计算机内存的常用单位是 
+ **千字节(KB)**: 1KB = 1024byte
+ **兆字节(MB)**: 1MB == 1024KB
+ **千兆字节(GB)**: 1GB = 1024MB
+ 大型磁盘驱动器使用 **兆兆字节(TB)**: 1TB = 1024GB

数据传输率的单位一般采用 `MB/S` 或 `Mbit/S`,
尤其在内部数据传输率上官方数据中更多的采用 `Mbit/S` 为单位.
此处有必要讲解一下两个单位二者之间的差异:
+ `MB/S`(mega byte 兆位) 的含义是**兆字节每秒**, `Mbit/S`
的含义是**兆比特每秒**, 前者是指每秒传输的字节数量, 后者是指每秒传输的比特位数.
`MB/S` 中的 `B` 字母是 `Byte` 的含义, Byte 是字节数, bit 是位数,
在计算机中每 **1Byte ＝ 8bit**, 是 1 : 8 的对应关系.
因此 **1MB/S = 8Mbit/S**. 

(1) 计算光纤传输的真实速度 
+ 使用光纤连接网络具有传输速度快. 衰减少等特点. 因此很多公司的网络出口都使用光纤.
  一般网络服务商声称光纤的速度为 "5M", 那么他的下载真实速度是多少那？
  
  我们来计算一下, 一般情况下, "5M" 实际上就是 5000Kbit/s(按千进位计算这就存在一个换算的问题. 因此电信所说的 "5M" 经过换算后就成为了 (5000 / 8)KByte/s = 625KByte/s 这样我们平时下载速度最高就是 625KByte/s 常常表示 625KB/S。在实际的情况中. 理论值最高为 625KB/S.
  
  那么还要排除网络损耗以及线路衰减等原因因此真正的下载速度可能还不到600KB/S 不过只要是550KB/S以上都算正常 

(2) 计算ADSL的真实速度ADSL是大家经常使用的上网方式. 那么电信和网通声称的“512K” ADSL 下载速度是多少那？ 

+ 换算方法为 512Kbit/s = (512/8)KByte/s = 64KByte/s, 考虑线路等损耗实际的下载速度在 50KB/S 以上就算正常了 那么 "1MB" 呢?
  大家算算吧答案是 125KByte/s 

(3) 计算内网的传输速度 
+ 1000MBPS 网卡的速度为: 1000MB/S＝1000000KByte/s = (1000000/8)KByte/s = 125000KByte/s; 理论上 1 秒钟可以传输 125MB 的速度, 考虑到干扰的因素每秒传输只要超过 100MB 就是正常了.
