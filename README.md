# 我的 2021 日程记录

2020 年的日程记录见：[DailySchedule\_2020](https://github.com/wfly1998/DailySchedule_2020)

## 已完成内容

* (Day 4) YuLang 编译成功，可以正常使用
* (Day 4) GeeOS 编译成功
* (Day 5) GeeOS 在 QEMU 中运行成功
* (Day 22) Fuxi SoC without DDR3 在 Vivado 中仿真成功
* (Day 23) Fuxi SoC without DDR3 在 FPGA 中启动成功
* (Day 29) Fuxi SoC 在 Vivado 中仿真成功、在 FPGA 中启动成功
* (Day 31) 在运行 Fuxi SoC 的 FPGA 上通过 UART 启动 GeeOS 成功
* (Day 36) 在运行 Fuxi SoC 的 FPGA 上启动 `fw_jump` 模式的 OpenSBI 成功
* (Day 55) Fuxi SoC 可以读取 Flash 了，但仍有 bug
* (Day 81) Fuxi SoC 在 FPGA 上运行，一切正常
* (Day 85) 在 QEMU 环境下，GeeOS 中实现 Buddy System 成功
* (Day 110) 在 QEMU 环境下，GeeOS 中实现 `sys_fork` 成功
* (Day 129) ICPC 省赛金牌
* (Day 167) 毕业论文通过。万事具备，只欠毕业证 (x)
* (Day 171) 成功晋级 OSCOMP 决赛

## [Before 2021](2021-0.md)

### 上半年计划

1. 报名参加 OSCOMP 比赛，选题 proj5
2. 学习 Chisel、YuLang，学习编译原理、网络原理，深入学习操作系统
3. 以 RVM 代码为基础，学习 CPU 虚拟化技术
4. 跟 ICPC 队友备战上半年的区域赛
5. 多读书，多运动，写[读书笔记](NOTE.md)

### 2021-01 计划

* 学习 Scala 及 Chisel
* 学习数字电路设计
* 学习编译原理、网络原理
* 完成 OSCOMP proj5 的第一题

## [January](2021-1.md)

### 2021-01 收获

* 学会了 Vivado 的基本操作以及 SoC 构建的基本过程
* 学会了基本的数字电路设计以及简单的调试
* 学习了部分编译原理（学习几章之后有事搁置，之后就忘记了）
* 让 Fuxi SoC 和 GeeOS 在我的板子上启动起来了

### 2021-01 不足

* 学了一点 Scala 和 Chisel 但是没用上，月底已经基本忘光了
* 编译原理只学了一点，没有坚持下去
* 在买设备和选择开发环境和配置开发环境上浪费了太多时间
* 在开发上不够细心，犯了太多低级错误
* 跟 ICPC 队友做题不够认真，也不太上心，摸鱼比较多
* 本月计划完成情况也不够理想，只勉强完成了移植

### 2021-02 计划

* 多读书，写读书笔记
* 多运动，减重减脂
* 深入学习操作系统知识
* 继续学习编译原理
* 完成 OSCOMP proj5 的前两题

## [Feburary](2021-2.md)

### 2021-02 收获

* 读书不多，但是也有收获
* 解决了部分 Fuxi SoC 中 Flash 的问题
* 跟 ICPC 队友更好地磨合了

### 2021-02 不足

* 读书太少
* 减肥失败
* 没学编译原理

### 2021-03 计划

* 在家身不由己，返校后正式开始减重减脂
* 认真做毕业论文，尽量这个月做出点成果
* 准备 ICPC 区域赛昆明站
* 空余时间读书，学编译原理

## [March](2021-3.md)

### 2021-03 收获

* 读书不多，但是也有收获（说人话：跟上个月一样懒）
* 完全解决了 Fuxi SoC 中 Flash 的问题
* 为 GeeOS 实现了 Buddy System
* 跟 ICPC 队友更好地磨合了
* 毕业论文所需实验进展过半
* 体重减轻数公斤

### 2021-03 不足

* 读书太少
* OSCOMP 没怎么进行
* 没学编译原理（我好懒 qwq）

### 2021-04 计划

* 尽量肝完毕业论文(?)
* ICPC 区域赛昆明站争取拿铜
* 为 GeeOS 实现基于优先级的线程调度
* 为 GeeOS 实现 `sys_mmap`, `sys_fork`, `sys_execve` 系统调用
* 尝试为 Fuxi SoC 移植 xv6-rv32
* 尝试为 GeeOS 移植一些程序，如 `bash`

## [April](2021-4.md)

### 2021-04 收获

* 为 GeeOS 实现了 `sys_fork`
* 修复了一些 `sys_fork` 相关的 bug
* 解决了一些开启 O2 优化后导致的问题
* 开始学编译原理，顺便做 minidecaf 实验了，感觉良好

### 2021-04 不足

* 基本没读书
* 毕业论文刚开始，实验进展过慢
* ICPC 区域赛打铁，而且还是接近铁首...
* 在 `sys_fork` 上浪费了太多时间，没有实现线程调度和 `sys_mmap` 以及 `sys_execve`
* 没有给 Fuxi SoC 移植 `xv6-rv32`
* 没有给 GeeOS 移植 `bash`
* （总结一下就是基本啥也没错 orz）

### 2021-05 计划

* 必须写完毕业论文了
* ICPC 省赛保银冲金
* 战术放弃 GeeOS 部分题目，转战 YuLang 和 Fuxi：
  * 五一假期做完 minidecaf 实验
  * 使用 Python 和 antlr4 以及 LLVM 完成 YuLang 的编译器
  * 时间允许的话，争取实现一下 Fuxi 处理器的 RVC 扩展
* 多读书！读 Unix 代码，读 KVM 代码

## [May](2021-5.md)

### 2021-05 收获

* ICPC 省赛金牌
* 完成 minidecaf 实验

### 2021-05 不足

* 没完成 YuLang 编译器
* 勉强完成毕业论文
* 没读书

### 2021-06 计划

* 完成答辩
* 去上海租房子
* 读书，读代码，准备入职

## [June](2021-6.md)

### 2021-06 收获

* 成功在单位附近租到房子
* 毕业论文通过

