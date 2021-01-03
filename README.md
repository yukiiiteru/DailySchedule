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

### Day 1 进展

发现自己电脑硬盘不够用，没有进展

### Day 2 计划

1. 在 Windows 下配置 Chisel 以及 FPGA 所需环境
2. 将 Fuxi SoC 及 OpenSBI 烧录到 FPGA 板子上
3. 调试运行 OpenSBI

前两条估计很快就能解决，第三条战线可能会比较长了

## Day 2 2021-01-02

在 Windows 下折腾了大半天 `sbt` 和 ISE WebPACK，最终发现 Windows 的 ISE WebPACK 极其不稳定，打开文件都闪退

考虑了一番换硬盘还是换电脑的问题后，我决定换电脑，然后当即在某宝下单一台 ITX 整机，但是发货还要一段时间

这段时间我先把自己电脑重装掉，只留 Linux，先凑合用着，计划还是要进行的嘛，等主机到货之后就把现在用的电脑再格式化回 Windows，然后就这么用着吧，毕竟开学后还是要写毕业论文的，Windows 必不可少

### Day 2 进展

几乎没有进展

* 发现 Windows 下的 ISE 不好用
* 发现 32 位的 OpenSBI 编译很麻烦，而 release 里的二进制不知道能不能直接使用

### Day 3 计划

1. 把电脑全盘格式化成 Linux，为开发让路
2. 将 Fuxi SoC 及 OpenSBI 烧录到 FPGA 板子上
3. 有必要的话，将 OpenSBI 编译到 RV32ima 平台
4. 调试运行 OpenSBI

### Day 3 2021-01-03

配环境越来越熟练了，只用了一个小时就装好了 Linux 和 `sbt` 以及 ISE WebPACK，然后把 Fuxi SoC 编译成 Verilog 代码，综合没有问题，布线过程出了些错误，具体报错如下：

```
ERROR:Pack:2309 - Too many bonded comps of type "IOB" found to fit this device.
ERROR:Map:237 - The design is too large to fit the device.  Please check the Design Summary section to see which resource requirement for
   your design exceeds the resources available in the device. Note that the number of slices reported may not be reflected accurately as
   their packing might not have been completed.
```

查了下 Design Summary，发现：

```
IO Utilization:
  Number of bonded IOBs:                       664 out of     160  415% (OVERMAPPED)
```

由内容并结合 Google 查询，我认为报错的意思是，代码中的 IO 端口数量超过了 FPGA 板子可以设置的数量，但是如何解决，我一点头绪也没有...

最终经过了半个小时的 Google，找到了这样一个帖子：[Using Xilinx ISE 14.7, PCIe core implementation problem](https://www.edaboard.com/threads/using-xilinx-ise-14-7-pcie-core-implementation-problem.356126/)

4 楼有解释可能的原因，可能是因为一些需要写在内部的 IO 端口，都给放外边去了

经过一阵思考，我认为，整个 CPU 需要被 SoC 封装起来，目前不需要有对外的接口，但是 SoC 代码我看不懂，也不知道怎么用...就很尴尬

我还是去翻书吧，一些自制 CPU 的书籍，参考一下最上层的代码应该怎么封装

有必要的话，也可以参考一下 Rocket 或者 BOOM 的代码，如果里面有可以参考的内容的话...

20210103 傍晚补充：我觉得应该装一个 Vivado，而不是 ISE，然而 Vivado 用 Windows 就可以，没必要把电脑重装，也没必要买新电脑...

罢了罢了，Linux 开发更舒服，而且新电脑也可以玩赛博朋克，计划通(x

20210103 晚上补充：Vivado 装完了，可以直接打开 `soc` 目录里的工程文件，解决了大部分问题，但是综合报了一大堆错，而且我发现最新版 Vivado 并不支持我 Spartan-6 的板子...

查了下，原话是这样的：

```
The Vivado tool has been created for the 7 Series devices (Virtex-7, Kintex-7, Artix-7, and Zynq-7000). 

To support the Spartan-6 devices (or any non 7 Series devices), you will need to use the latest ISE design tools, which work best regardless of the complexity of the design.
```

好了，买新板子还是折腾 ISE 二选一吧

