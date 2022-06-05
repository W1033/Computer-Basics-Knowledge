# Structured Computer Organization, Sixth Edition

计算机组成：结构化方法 （第 6 版）


(荷) Andrew S. Tanenbaum

(美) Todd Austin 

刘卫东 宋伟兴译



## I 前言

 Structured Computer Organization, Sixth Edition

本书的前 5 个版本都是建立在计算机由层次结构组成、每层完成规定的功能这一思想上的。今天，这一基本思想依旧和第 1 版刚出版时一样正确，它依然是第 6 版的基础。和前 5 版一样，我们将详细讨论 **数字逻辑层**、**微体系结构层**、**指令系统层**、**操作系统层** 和 **汇编语言层**。

尽管保留了基本的结构，但第 6 版还是包含了或大或小的许多变动，以跟上飞速更新的计算机产业的步伐。例如，本版的示例计算机均已改成当前的主流计算机系统，即 Intel 公司的 Core i7、德州仪器的 OMAP 4430 和 Atmel(爱特梅尔) 的 ATmega168。其中， Core i7 是广泛应用于笔记本、台式机和服务器的 CPU，而 OMAP 4430 是一款基于 ARM 的主流 CPU,被很多智能手机和平板电脑釆用。

许多人可能从未听说过 ATmega 168 微控制器，但也许每天都会和它打交道。由于极其低廉的成本（几美分）、高附加值的软件和外部设备，以及数量众多的程序员，基于 AVR 的 ATmega168 广泛用于从定时收音机到微波炉的许多嵌入式系统中，世界上 ATmega168 的数量要比 Pentium 以及 Core i3、 i5 和 i7 CPU 多出许多个数量级。同时， ATmega168 也是 Arduino 单片嵌入式系统中使用的处理器， Arduino 是一个基于开源代码的软硬件平台，最初由意大利一所大学设计，价格低廉，比在比萨店吃顿晚饭还便宜。

近年来，许多讲授本课程的教授多次询问关于汇编语言程序设计的内容，第 6 版把这些材料放在了本书的网站中（地址见后），这样做可以方便更新这些材料，以保持它们的时新性。我们选择的是 8088 汇编语言，主要原因在于它是当前流行的 Core i7 处理器使用的 IA32 指令集的先前版本，我们当然也可以选择 ARM 或者 AVR 指令集，甚至其他没人听说过的指令系统作为例子，但作为目的性很强的教学工具，由于大多数同学家里都有一台兼容 8088 的计算机， 8088显然是一个更好的选择。 Core i7 的全集太复杂，不适宜让学生了解全部细节, 8088 则要简单得多。

另外，本版使用 Core i7 作为例子，讲解了不少该 CPU 的细节， Core i7 本身就能运行 8088汇编语言程序。尽管如此，调试汇编语言代码依然比较困难，我们提供了一系列工具来帮助大家学习汇编语言编程，包括 8088 的汇编器、模拟程序和跟踪程序。这些工具可在 Windows、 Unix和 Linux 环境下运行，都可在本书的网站上下载。

这些年来，本书也变得越来越厚（第 1 版有 443 页，而本版有 769 页^*）。由于学科本身的发展和对它的了解的加深，这也是不可避免的。因此，当用作教材时，可能就无法在一门课（一个学期）中讲述完所有内容。一种可行的方法是讲述第 1、第 2 和第 3 章的全部内容， 第 4 章的前 4 节，以及第 5 章的少量内容。其余的时间可根据教师和学生的兴趣介绍第 4 章剩余部分和第 6、第 7、第 8 章的部分内容。

* `*` 这里的页数均指原版书。一译者注

下面逐章介绍一下各章纲要及对第 5 版的主要改动。第 1 章依然是对计算机体系结构发展的历史回顾，指出我们是如何走过来的，目前的位置和发展道路上的主要里程碑。当了解到 20 世纪 60 年代世界上最强大的计算机的成本高达数百万美元，而计算能力还不及现在智能手机的 1%时，许多同学可能会十分惊讶。我们还要介绍广义上的计算机系列，包括 FPGA、智能手机、平板电脑和游戏控制器。当然，本版新的 3 种示例处理器(Corei7、 OMAP4430和 ATmega168 )的体系结构也在本章中有简单说明。

第 2 章在处理方式方面，增加了数据并行处理器也就是图形处理器(Graphics Processing Unit, GPU)的相关材料。存储技术领域引入了当前正趋于流行的基于 Flash 的存储设备。而 2. 4 节中，加入了对现代游戏控制器(如 Wiimote, Kinect)和智能手机、平板电脑上使用的触摸屏等的介绍。

第 3 章的许多地方都进行了修改。该章依然从晶体管开始论述，这样做的好处是没有任何硬件基础的同学也能理解现代计算机的运行原理。新增加的内容主要是现场可编程门阵列(Field- Programmable Gate Array, FPGA )的相关内容，现场可编程芯片价格降低到可以在教学中广泛使用，使得真正的大规模门级设计可以引入课堂。对用作示例的三种新的处理器体系结构做了芯片级的介绍。

第 4 章讲解计算机是如何运行的。这章一直就颇受好评，因此从第 5 版开始就没做大的改变。当然，用作示例的 Corei7、 OMAP4430 和 ATmega168 的微体系结构层的内容是新的。

第 5、 6 章仅就新的示例体系结构所涉及的部分做了改写，尤其是增加了对 ARM 和 AVR 指令系统的描述。第 6 章用 Windows 7 取代 Windows XP 作为例子。

第 7 章的内容是关于汇编语言编程的，和前一版比基本没有变化。

第 8 章做了许多修改，以反映在并行计算机领域各方面的新的研究动向。增加了 Core i7 多处理器体系结构的一些新的特征，并详细介绍了 NVIDIA Fremi 的通用 GPU 体系结构。最后，对 BlueGene 和 Red Storm 超级计算机的内容进行了更新，以跟上这些巨型机最近的升级。

参考文献也做了修改。将推荐读物放在了网站上，因此，这一版中引岀的仅仅是本书引用过的参考文献，许多都是全新的。计算机组成是一个快速发展的领域。

附录 A 和附录 B 从上一版本开始就没有修改，这些年以来，二进制数和浮点数的表示没有什么变化。附录 C 是关于汇编语言程序设计的，由阿姆斯特丹 Vrije 大学的 Evert Wattel 博士编写， Wattel 博士拥有多年使用这些工具进行教学的经验。我们十分感谢他写的这个附录， 主要内容没有做调整，但将工具放到了网站上。

除汇编语言的工具之外，本书网站还包含一个配合第 4 章使用的图形模拟器。它是由 Oberlin学院的 Richard Salter 教授编制的，可用于帮助同学们掌握第 4 章讨论的基本原理。十分感谢 Richard Salter 教授提供该软件。

包含这些工具以及其他内容的本书网站的网址是： http:// www. pearsonhighered. com/ tanenbaum

从网页上点击本书的链接，并从菜单项中选择你所找寻的页面。其中的学生资源包括：

- 汇编器/追踪器软件。
- 图形模拟器。
- 推荐读物。

教师资源包括：

- 课程的 PowerPoint 幻灯片。
- 每章习题的解答。

教师资源需要通过密码访问。使用本书作为教材的教师可通过联系当地的 Pearson 教育代表获得密码。

许多人读过本书的(部分)手稿，并提岀了有益的建议或以其他方式对本书提供了帮助。我 VII们要特别感谢 Anna Austinx Mark Austin、 Livio Bertacco, Valeria BertaccoDebapriya ChatterjeexJason Clemons、 Andrew DeOrio> Joseph Greathouse 和 Andrea Pellegrini。

下列人士审阅了手稿并提出了修改意见： Jason D. Bakos (University of South Carolina ), BobBrown (Southern Polytechnic State University ) 、 Andrew Chen (Minnesota State University, Moorhead )、 J. Archer Harris (James Madison University )、 Susan Krucke (James Madison University )、 A. Yauvz Oruc (University of Maryland )、 France Marsh (Jamestown Community College )和 KrisSchindler (University at Buffalo ) o 十分感谢他们。

还有几位帮助我们提供了新的习题。他们是： Byron A. Jeff (Clayton University ) Xaura W. McFall (Depaul University )、 Taghi M. Mostafavi (University of North Carolina at Charlotte )和 JamesNystrom (Ferri State University ) o 我们再次感谢他们的帮助。

我们的编辑 Tracy Johnson 给了我们全方位的帮助，十分感谢他的耐心。 Carole Snyder 在协调参与本书写作工作的各类人士方面提供了十分专业的帮助。 Bob Englehardt 对本书的最后出品做了很好的贡献。

我(Andrew S. Tanenbaum )要再次感谢 Suzanne 的爱和耐心，她一直陪伴我完成了 21 本著作的写作。 Barbara 和 Marvin 永远是开心果，他们现在也知道了教授是如何谋生的。 Aron 属于新生的一代：上幼儿园之前就已经是资深的计算机用户了。 Nathan 还没有达到这个程度， 但他学会走路后， iPad 将会是他的下一个学习目标。

最后，我(Todd Austin )要趁此机会感谢我的岳母 Roberta,她为我写作本书提供了许多黄金时间。她在意大利 Bassano Del Grappa 的餐桌上刚好有足够的幽静、舒适和葡萄酒，供我完成这项重要的工作。

 Andrew S. TanenbaumTodd Austin