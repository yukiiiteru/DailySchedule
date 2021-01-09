# 我的 2021 日程记录

## 已完成内容

* (Day 4) YuLang 编译成功，可以正常使用
* (Day 4) GeeOS 编译成功
* (Day 5) GeeOS 在 QEMU 中运行成功

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

* 发现自己电脑硬盘不够用，没有进展

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

## Day 3 2021-01-03

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

### Day 3 进展

* 知道了 Fuxi SoC 的使用方法，也知道了我的板子不适合拿来搞这个...

### Day 4 计划

1. 买板子，然后等收货
2. 编译 YuLang
3. 用 YuLang 编译 GeeOS，并在 QEMU 里跑起来

## Day 4 2021-01-04

昨晚下单了新板子，Artix-7 系的，没想到今天上午就发货了，意想不到的快。那么趁新主机和新板子都还没到的时间，先折腾下 YuLang 好了

此外，装 VS Code 的时候有点新发现，MaxXing 大佬已经制作了 YuLang 的 VS Code 高亮插件，可以用 VS Code 搞开发了

但是，编译 YuLang 的过程中也遇到了一些问题，YuLang 的 README 里写需要用 `llvm 8.0 or later`，但是我用的 LLVM 11，遇到了一些小问题，比如：

1. `src/back/llvm/objgen.cpp` 需要再 `#include "llvm/Support/Host.h"`；
2. `src/back/llvm/generator.cpp` 调用的 `CreateCall` 函数参数更新了，需要把 `llvm::Value *` 改成 `llvm::Callee *`，把 `std::Vector` 改成 `llvm::ArrayRef`；

20210104 下午补充：换成 LLVM 10 就没有问题了，看来是 LLVM 11 的新 feature，但是又遇到一些新的问题：

1. `make[3]: /usr/local/opt/llvm/bin/llc: 没有那个文件或目录`，解决方法：修改 `toolchain.mk`，把 `export LLC := $(LLVM_HOME)/llc $(LLCFLAGS)` 改成 `export LLC := llc $(LLCFLAGS)`
2. `clang` 没装会报个错，小问题
3. 装上 `clang` 之后会报：
   ```
   making example "array\_test"...
   /usr/bin/ld: /home/yukiteru/github/YuLang/build/obj/examples/array\_test.yu.o: relocation R\_X86\_64\_32 against symbol `out' can not be used when making a PIE object; recompile with -fPIE
   /usr/bin/ld: /home/yukiteru/github/YuLang/build/libyu.a(io.yu.o): warning: relocation in read-only section `.text'
   clang-11: error: linker command failed with exit code 1 (use -v to see invocation)
   ```
   是用 `clang` 编译时出现的链接问题，解决方法：在 `toolchain.mk` 里，给 `LDFLAGS` 加上 `-no-pie`

解决掉这些问题后，`yuc` 就成功被编译出来了～然后顺手 `ln -s` 到 `~/.local/bin` 里面，运行起来也方便

但是——GeeOS 的编译又出了不少问题：

1. `mkfs` 工具使用了 C++17 的类 `string_view`，并将 `string_view` 隐式传入需要 `string` 参数的函数，然而编译器报了错
   解决方法：将 `string_view` 变量套上 `string()` 或者在其后面添加 `.data()`，推荐后者
2. LLVM 工具链的路径问题，改 `toolchain.mk` 即可，还有找不到 `ld.lld`，装一个 `lld` 就好了
3. `objdump` 识别不了 RV32 的 elf 文件，给 `objdump` 加上 prefix 即可
4. `bin2coe.py` 无法直接运行，可能是我终端的问题，在 `src/Makefile` 里给加上 `python3` 就好了

经过以上改动，`geeos.elf` 就编译出来了，但是运行又出了问题。`cd` 进 `build`，然后照 README 写的命令运行，会报：

```
rom: requested regions overlap (rom phdr #0: build/geeos.elf. free=0x000000008000f2c0, addr=0x0000000080000000)
qemu-system-riscv32: rom check and register reset failed
```

网上查了下，看到了 openEuler 那边的 [issue](https://bugs.launchpad.net/qemu/+bug/1429841)，这可能是最新版 QEMU 才会出的问题，好像 4.x 版本的 QEMU 不会有问题

我是不是不该用 ArchLinux 的，LLVM 版本太新了，QEMU 版本也太新了...

唉，明天再重装系统吧，换成 Ubuntu 20.04，或者 18.04 也行，毕竟比赛最终编译是在这上面进行的

### Day 4 进展

* YuLang 编译成功，看起来一切正常
* GeeOS 编译成功，但是运行不起来

### Day 5 计划

1. 重装系统，把 ArchLinux 换成 Windows 10 + Ubuntu 18.04 (?)
2. 编译 YuLang + GeeOS，然后在 QEMU 上跑起来
3. fork 一份 YuLang 和 GeeOS，把一些跟比赛无关的内容，比如 `Makefile` 啥的改改，提交一份 PR，比赛有关的就先放自己仓库里，等结束了再提交
4. 把 GeeOS 在 QEMU 里运行起来好像也不是什么难事，那就先学下 YuLang，在 FPGA 板子到货之前先写着线程调度

## Day 5 2021-01-05

今天的时间都用在装系统上了。装了 Ubuntu 18.04，发现 `cmake` 版本太旧、`vim` 版本太旧、`g++` 默认版本太旧，受不了折腾这些东西，我就换了 Ubuntu 20.04

Ubuntu 20.04 基本一切正常，除了`apt` 里面的 QEMU 没有 RISCV 版本，我又自己从源码编译了一份 `qemu-system-riscv32`，4.2.1 的版本，运行一切正常，唯一的问题是我忘记该怎么退出 QEMU 了...

然后我又装上了 Windows，又在 Windows 下挂机装 Vivado，顺便学一下 YuLang。直到现在 Vivado 都还没装完，先睡觉！

明天估计我的板子就能到了，但是电脑还要大概一周才能到。就先用我的电脑凑合整吧，熟悉一下 Vivado 先，等新电脑到了就全部在 Linux 上开发了，还是 Linux 搞开发舒服啊

（另外，有机会可以学一下 Vim 插件怎么写，我整一个 Vim 的 YuLang 高亮插件也不错，不过自动补全可能有点难

### Day 5 进展

* GeeOS 运行成功
* fork 了 YuLang 和 GeeOS，并改了下 `Makefile` 啥的，先不 PR 了，感觉没啥必要(?)

### Day 6 计划

1. 熟悉 Vivado 的使用
2. 生成 Fuxi SoC 和 OpenSBI 的 SVF 文件
3. 板子收货之后把 SVF 文件烧进去，进度快的话就先调试着

线程调度之后再说吧，昨天的计划就先推迟一下(x

此外我仔细想了一下，移植 RustSBI 也不是不行，照 QEMU 版本编译然后烧进去理论上是可以的，但是可能有点小问题

Rust 的 RISC-V 32 环境似乎只有 RV32imac 和 RV32gc，而 Fuxi 处理器目前只支持 RV32ima，并不支持 C 扩展，所以暂时是没办法使用的，等写完了 C 扩展再移植 RustSBI 也不迟

OpenSBI 必须自己编译了，在编译参数里声明一下用 RV32ima 指令编译，这样应该就可以勉强运行起来，如果 `mstatus` 寄存器不出什么问题的话

## Day 6 2021-01-06

根据 Xilinx 官网的推荐，我装好了最新版本的 Vivado 2020.2，然后熟练地用 Vivado 打开 `Fuxi/soc/soc.xpr`，综合，还是之前一样的错误

这次我仔细看了一下，是文件的缺失，是找不到 `Fuxi\soc\soc.srcs\sources_1\bd\soc\ipshared` 的问题，我到上层目录看了下 `.gitignore`，发现一堆目录被 ignore 掉了

结合文件名以及 `.gitignore`，我觉得这个目录应该是由 Vivado 自动生成的，IP Core 相关的功能，但是我的 Vivado 的 IP INTEGRATOR 板块只能选择 Create 和 Open，还有一个 Generate Block Design 的按钮是灰色的，不能点，然后我就去网上查，并没有查到什么

这时我突然想起 Fuxi 的 README 里有提到，作者用的是 Vivado 2018.3，要不我也装一个试试？

装完之后，打开 `soc.xpr`，发现 Generate Block Design 是可以点的，解决了一个大问题，但是综合的时候又闪退了...就很难受

经过了一番折腾，我发现 Vivado 2020.2 不能 Generate Block Design 是因为调用的 Vivado 的 IP Core 版本太旧了(?)，需要 Upgrade，更新一下就又可以 Generate 了

为了保持稳定，我没有改设置里的 Project Device，综合、布线，一切正常，但是改成我的板子型号之后，报错了：

```
[xilinx.com:ip:mig_7series:4.2-0] soc_mig_7series_0_0: Target FPGA device 'xc7a200t' provided in the mig project did not match with the selected FPGA device 'xc7a35t' in project settings. Please cross check the mig project loaded or review the project settings
```

看起来是换板子型号产生的问题了，根据字面意思需要修改 mig project，也算是一切正常。不过我觉得改 SoC 应该没有我想象的那么简单，毕竟板子端口什么的布置就很不一样

搜索 `mig`，然后用记事本打开 `mig.prj` 文件，我发现第四行写着：

```xml
<!-- IMPORTANT: This is an internal file that has been generated by the MIG software. Any direct editing or changes made to this file may result in unpredictable behavior or data corruption. It is strongly advised that users do not edit the contents of this file. Re-run the MIG GUI with the required settings if any of the options provided below need to be altered. -->
```

看来这个是自动生成的了，查了一下需要在 Vivado 的 IP Catalog 里选择 Memory Interface Generator 生成 mig，但是照默认配置生成 mig 之后再选 Upgrade，会报 `Selected IPs can't be upgraded`，选择需要升级的 IP Core 时不全选，只选择必须升级的 IP Core，这时候升级会闪退

换成 Vivado 2018.3，改完 Project Device 之后，Generate Block Design 也变成灰色，不能点了，怪不得我之前没注意到这个问题

然后我问某宝店家要到了我现在板子的配套资料，里面有 MicroBlaze 处理器的构建教程，可以参考这个来整一遍

此外，我也查了一下 IP Core 的定义，感觉跟我经过以上操作之后的理解差不多：

> IP (Intellectual Property) 在嵌入式 FPGA 设计中，指的是某些设计好的模块，分为软件模块和硬件模块。这些模块，一般都是已经测试好，所有功能完善的，由一些用户自己设计的。有些模块是免费的，也有收费的模块。所有用户都可以将这些 IP 核 (IP Core) 导入到自己的工程中，同样，所有用户也都可以定制自己的IP核。

20210106 晚上补充：我照开发板的手册重新设置了一遍 mig 的管脚号 (Pin Number)，完成之后意外的没问题了，我还以为要把所有 IPC 的管脚号都要设置一遍的

现在已经全部 Upgrade 了，SoC 也可以在我的板子配置下正常综合了，今天就先到这，早睡早起身体好

### Day 6 进度

* 对 Vivado 的基本使用相对熟悉一些了
* Fuxi SoC 综合成功，布线成功，其实最后生成 Bitstream 也成功了，但是不知道给生成到哪去了，这个明天再说x

### Day 7 计划

1. 前面的步骤都完成了，明天真的该把 SoC 烧到板子上了
2. 在 Linux 下编译 RV32ima 的 OpenSBI，烧到板子上
3. debug

## Day 7 2021-01-07

参考 MicroBlaze 的文档，找到了生成 BIT 文件并烧写到 FPGA 上的步骤，但是奇了个怪了，综合、布线都不报错，生成 BIT 文件报没有布线：

```
ERROR: [Common 17-70] Application Exception: Unable to get BIT file from implementation run. Please ensure implementation has been run all the way through Bitstream generation. Aborting write_hw_platform..
```

20210107 下午补充：布线没报错，但是也没成功，其实要等很久之后才会报错，报错内容看不懂，也查不出来

有没有必要把 SoC 重新做一遍呢...

20210107 傍晚补充：有必要，毕竟板子不同，板子上的硬件不同，硬件对应的管脚号也不同。就算不重做，也要把 `xdc` 文件重新写一遍

20210107 晚上补充：开始重做！

20210107 深夜补充：放弃重做！先照 MicroBlaze 的教程熟悉一下 SoC 的构建方法！

### Day 7 进展

* 对 SoC 构建的基本操作相对熟悉一些了

综合没有问题，布线还是有问题，或许一些约束和一些模块需要针对特定板子重写

### Day 8 计划

1. 完成 Fuxi SoC 在我的板子上的构建

## Day 8 2021-01-08

今天开始参考 Fuxi SoC 在龙芯 FPGA 上的配置以及 MicroBlaze SoC 在我的 FPGA 上的配置

我觉得大部分配置都是可以参考的，按键、LED 还有最麻烦的 HDMI 需要重写，因为龙芯是用 VGA 的，ALINX 是用 HDMI 的，这里接口和协议都不一样，不过好像不是必须的，先跳过这部分也行

按键和 LED 先给用 wire 连上，HDMI 先略过，之后再参考板子给的 demo 和 Fuxi 的 VGA 写 HDMI

进行到现在，一个小问题是：大部分 IP Core 的功能我看一眼就知道是做什么的，但是我很难理解 AXI Interconnect 这个 IP Core 的使用方法，大体查了一下，是使用 AXI4 总线协议进行总线仲裁的，这就涉及到我的知识盲区了，因为我学的组成原理对总线仲裁只是停留在原理，并没有深入到具体的硬件、协议层面

AXI Interconnect 参考资料：

1. [AXI Interconnect](https://www.xilinx.com/products/intellectual-property/axi_interconnect.html)
2. [总线仲裁 - 百度百科](https://baike.baidu.com/item/%E6%80%BB%E7%BA%BF%E4%BB%B2%E8%A3%81)

算了，就强行连吧...

此外，我在万能的 bilibili 上找到了用 MicroBlaze 连 HDMI 输出视频的一个小教程：[Nexys Video 基于 Microblaze 的 OV5640 视频输出](https://www.bilibili.com/read/cv5242447/)，但是这个似乎用了几个我找不到的 IP Core；还有，我也在板子附送的 demo 里找到了 HDMI 输出的样例，但是先不折腾了吧，先老老实实折腾 SoC

20210108 傍晚补充：经过了一天的折(连)腾(线)，虽然连生成 Wrapper 都没有完成，但是我了解了 SoC 的构造，这简直是太妙了，一个 SoC 就是一个完整的主板，总线`sys_bus`、南北桥(`peri_bus`, `mem_bus`)、中断发生器、内存、显卡、网卡，一应俱全，虽然这里不应该称作显卡、网卡，因为并没有实际的卡存在，只是嵌入到板子上的电路

此外我也庆幸自己没有选择使用古老的 Spartan-6 系 FPGA 配合 ISE 自己写 SoC，每个 IP Core 都够我写半天的（除了 `Constant`）

经过这么久的折腾，我也知道如何移植 SoC 了：把板子上没有的模块（如 VGA）剔除掉、把板子上有的模块（如 HDMI）加上、把板子上都有的但不同模块（如晶振、内存）进行修改、适配

虽然上面都是废话，但是也确实是我走了一天的弯路所得出来的结论

今天也是失败的一天呢

### Day 8 进展

* 对 SoC 的基本结构相对熟悉一些了

但是我也发现前几天我的 repo 里 commit 的代码不能生成 Block Design，打算最近再整一份可以生成 bd 的，适配我板子的 project

20210108 深夜补充：重新 commit 了一遍，好像跟之前一样，还是不能生成 bd...

### Day 9 计划

1. 让 SoC 可以生成 Block Design
2. 完成 Fuxi SoC 在我板子上的构建

（题外话：我的计划从一个远大的目标变得越来越...嗯...不那么远大了，但是这也说明我的进展在不断深入，我的工作在不断细化，这也是好事）

## Day 9 2021-01-09

偶然在 GitHub 发现了 [基于龙芯 FPGA 开发板的计算机系统综合实验](https://github.com/oscourse-tsinghua/LoongsonCsprj2020)，感觉可能有一些参考价值

然后，又经过了一天的连线，在 CPU 没有连接外设的情况下，可以生成 BD 并综合了，但是布线还是有一些问题，会报错：`DRC PDRC-34` 和 `DRC PDRC-43`，有两个时钟频率不匹配，应该不难解决

然而，Google 出的结果没有参考价值，龙芯板子上的 Fuxi SoC 参考了并没有起作用，板子附送的 demo 参考价值也不大

报错内容主要说的是，计算出的 MMCM 和 PLL 的 VCO 频率（`CLKIN1_PERIOD`）不在其要求的周期范围内

计算公式为：`CLKIN1_PERIOD = (CLKFBOUT_MULT_F * 1000 / (CLKINx_PERIOD * DIVCLK_DIVIDE))`

需要调整 MMCM 和 PLL 配置中的 输入周期(`CLKINx_PERIOD`)、乘法因子(`CLKBOUT_MULT_F`) 或者 除法因子(`DIVCLK_DIVIDE`)，使得两者的 VCO 频率落在设备的范围内

一晚上过去了，并没有解决，因为不知道该调整什么地方...

20210109 深夜补充：应该调整 Clocking Wizard 的配置，改 Output Clocks 部分让 MMCM 变化，应该就能解决了

今晚大部分时间都用在生成输出(Generate Block Design)、综合和布线上了，在跑程序的过程中顺便了刷了一下哈工大的编译原理，毕竟还是要折腾 YuLang 的

### Day 9 进展

* 半成品 SoC 生成输出、综合成功，卡在布线上
* 学习了编译原理的绪论部分以及词法分析的前半部分

### Day 10 计划

1. 解决 Error，让半成品 SoC 可以布线
2. 完善 SoC，尽量让完整的 SoC 可以生成 Bitstream
