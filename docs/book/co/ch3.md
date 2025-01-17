# 第三章:系统总线

## 3.1 总线的基本概念

总线将计算机的五大部分连接起来了。

如果两两连接，不仅线组织起来复杂，修改也复杂。

总线连接各个部件的信息传输线，是各个部件共享的**传输介质**。

总线分为**串行**和**并行**两种传输方式。

* 单总线结构。（优点缺点待补充！！！）
* 面向 CPU 的双总线结构。
* 以存储器位中心的双总线设计。

## 3.2 总线的分类

1. 片内总线：芯片内部的总线。
2. 系统总线：计算机各部件之间的信息传输。
   1. 数据总线：双向
   2. 地址总线：单向
   3. 控制总线：双向

## 3.3 总线特性及性能指标

1. 总线的物理实现
2. 总线特性
   1. 机械特性：尺寸，形状，管脚数及排列顺序。
   2. 电气特性：传输方向和有效的电平范围。
   3. 功能特性：每根传输线的功能：地址，数据，控制。
   4. 时间特性：信号的时序关系。
3. 总线的性能指标
   1. 总线的宽度，数据线的根数
   2. 标准传输率，每秒传输的最大字节数（MBps）
   3. 时钟同步/异步，同步，异步
   4. 总线复用，地址线与数据线的复用
   5. 信号线数，地址线，数据线和控制线的总和
   6. 总线控制方式，突发，自动，仲裁，逻辑，计数。
   7. 其他指标，负载能力。

4. 总线的标准

总线是在不断的发展，在发展的过程中不断的形成了多种标准。

![](https://cdn.jsdelivr.net/gh/weijiew/pic@master/images/20200821214544.png)

## 3.4 总线结构

1. 单总线结构

计算机的所有部分都和总线**直接相连**，但是每一部分使用总线的频率各不相同导致总线成为了性能的**瓶颈**。

![](https://cdn.jsdelivr.net/gh/weijiew/pic@master/images/20200821214740.png)

2. 多总线结构

针对单总线的缺点，多总线结构出现了。

多总线结构又分多种，例如双总线结构：

![](https://cdn.jsdelivr.net/gh/weijiew/pic@master/images/20200821215154.png)

通道是由操作系统管理的一种特殊功能的处理器，由通道对 I/O 统一管理。

三总线结构：

![](https://cdn.jsdelivr.net/gh/weijiew/pic@master/images/20200821215648.png)

三总线结构的又一形式：

![](https://cdn.jsdelivr.net/gh/weijiew/pic@master/images/20200821215708.png)

四总线结构：（高速缓存的引入）

![](https://cdn.jsdelivr.net/gh/weijiew/pic@master/images/20200821215809.png)

## 3.5 总线控制

1. 总线判优控制

* 主设备 对总线有**控制权**。
* 从设置 响应从主设备发来的总线命令。
* 总线判优控制：集中式，分布式。
  * 集中式:链式查询，计数器定时查询，独立请求方式。
  * 分布式。

### 链式查询

![](https://cdn.jsdelivr.net/gh/weijiew/pic@master/images/20200821220558.png)

### 计数器定时查询

![](https://cdn.jsdelivr.net/gh/weijiew/pic@master/images/20200821220906.png)

总线控制部件里面有一个计数器，当某个设备向总线提出了 BR （总线请求）时。总线控制部件会逐个查询 I/O 接口，查询是谁发出的 BR 请求。

I/O 接口的顺序是固定了，优先级按顺序逐个递减。也可以通过软件的方式来设置优先级的顺序。

与链式查询相比，少了 BG ，但是多个设备地址线，设备地址线与设备地址的个数相关。

### 独立请求方式

每个 I/O 接口都存在 BG 和 BR 。都可以独立的和总线控制部件相连。

优先级顺序按照排队器的设定来确定。

![](https://cdn.jsdelivr.net/gh/weijiew/pic@master/images/20200821220836.png)

2. 总线通信控制

* 目的： 解决双方协调配合问题。
* 总线传输周期：
  * 申请分配阶段
  * 寻址阶段
  * 传输阶段
  * 结束阶段


3. 总线通信的四种方式

* 同步通信：由**统一时标**控制数据传送。
* 异步通信：采用**应答方式**，没有公共时钟标准。
* 半同步通信：同步异步相结合。不互锁，半互锁，全互锁。
* 分离式通信：充分挖掘系统总线每个瞬间的潜力。

