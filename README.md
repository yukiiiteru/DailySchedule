# 我的 2021 日程记录

## 已完成内容

* 暂无

## Before 2021

在 2020 年的最后一天，提前给将要到来的 2021 年制定一下计划，并尽量按计划每天记录下来，希望自己能达到想要的目标。

### 上半年计划

战线拉太长了不好，就先定半年的计划吧

1. 报名参加 OSCOMP 比赛，选题 [proj5-fuxi-full-system-with-cpu-compiler-os](https://github.com/oscomp/proj5-fuxi-full-system-with-cpu-compiler-os)
2. 学习 Chisel、YuLang，学习编译原理、网络原理，深入学习操作系统
3. 以 [RVM](https://github.com/rcore-os/RVM) 代码为基础，学习 CPU 虚拟化技术
4. 学有余力的情况下，跟 ICPC 的队友准备明年的区域赛，多用真题训练，提升自己的代码能力

大概先这样(?)，更具体的内容之后再补充吧

### Day 1 计划

1. 学习 Scala 及 Chisel
2. 配置 Linux 下的 FPGA 开发板的开发环境
3. 尝试写一些简单的 Chisel 小程序，然后烧到 FPGA 板子上并调试

#### 学习资料

* [Chisel 教程汇总 - csdn](https://blog.csdn.net/qq_34291505/article/details/86744581)
* [Chisel-Bootcamp](https://github.com/freechipsproject/chisel-bootcamp)
* FPGA 开发板文档（某宝店送的资料，在某度网盘里）

### 扯点别的

今天就是 2020 年的最后一天了，我也是刚从学校回到家，挺累的

所以——就先放纵一下吧，打打游戏看看跨年晚会啥的，明天正式开始学 Chisel（虽然之前已经接触过一丢丢了）

总结一下我的这一年吧，上半年摸鱼上网课，暑假爆肝做项目，下半年放弃考研找工作，年底事业爱情双丰收

在此还是要感谢一下陈老师和向老师给了我参加暑期活动的机会，凭我之前的经历写出的简历只能在济南勉强找到月入 5.5k 的工作，但有了暑假的项目后我成功拿到了字节跳动的 offer，我的感激之情无以言表

我选择记录我的 2021 日程，并参加 OSCOMP 的比赛，也是受到陈老师和向老师的影响，希望我也可以为开源社区贡献一份力量

2020 年唯一的遗憾可能就是放弃考研了吧，因为焦虑被迫放弃。虽然最后找工作的结果也还不错，但是我还是更向往能去贵系读研究生的生活

说得有点多了，嗯...就先这样吧

2021，我来了

## Day 1 2021-01-01

Chisel 基础学习完成，还没开始上手敲代码。今天完成的主要工作是配置 Chisel 环境并编译 Fuxi 处理器

`sbt` 第一次编译好慢，下载 Xilinx ISE DS 好慢，好多时间都用在这上面了，我应该一边配环境一边学习的

我之前有买过 FPGA 的板子，也参考一些书籍写过 MIPS 的 CPU，但是只在电脑上仿真过，并没有烧到板子上调试，所以这方面我也不是很懂，要从头开始学起

根据我参考的书，应该做的事情如下：

1. 完成 CPU 的代码（废话）
2. 为 CPU 编写 SoC 代码（不然只有处理器没有内存没有 ROM 什么的也用不成）（个人理解）
3. 安装 Xilinx ISE WebPACK 和 UrJTAG 软件
   * 其中，ISE WebPACK 包括 ISE Project Navigator 和 iMPACT，作用分别为：将 Verilog 源程序转换为 BIT 文件、将 BIT 文件转换成 SVF 文件，及将 BIT 文件转换为 MCS 文件再转换为 SVF 文件
   * UrJTAG 的作用为，将 BIT 直接生成的 SVF 文件写入 FPGA，并将 MCS 文件生成的 SVF 文件写入 ROM
4. 这样似乎就可以运行了(?)

但是我又在考虑要不要先在本地仿真来完善功能，比如编译一下 OpenSBI 或者 RustSBI，用之前写 CPU 的小工具把 SBI 的可执行文件转化成可以导入 Fuxi 处理器运行的（存着十六进制指令的）文本文件

思考了一下，也看了下这个 Project 中导师的预期目标，还是决定烧到 FPGA 里面会比较好一些

本来想第一个移植 luojia 大佬的 RustSBI，结果发现 release 里面只有 QEMU 和 K210 的版本，所以我先用 OpenSBI 试试 Fuxi SoC 的基本功能，等 OpenSBI 适配好了再尝试移植 RustSBI 试试～

然而...安装 Xilinx ISE WebPACK 的时候发现，我的 Linux 空间不够用了，这软件需要 23G，但是我的系统只有 1G 了，所以被迫去用 Windows 了，而且 Scala 和 Chisel 的环境还需要再重新配一遍...

先 push 一下，今晚还有些事情，定一下明天的计划就先撤了，虽然今天的计划没怎么完成...

### Day 2 计划

1. 在 Windows 下配置 Chisel 以及 FPGA 所需环境
2. 将 Fuxi SoC 及 OpenSBI 烧录到 FPGA 板子上
3. 调试运行 OpenSBI

前两条估计很快就能解决，第三条战线可能会比较长了

