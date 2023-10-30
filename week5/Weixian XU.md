# 图灵机 Turing Machine
**A Turing machine is a mathematical model of computation describing an abstract machine[1] that manipulates symbols on a strip of tape according to a table of rules.**
图灵机，又称图灵计算机指一个抽象的机器，是，英国数学家艾伦・麦席森・图灵(1912―-1954年)于1936年提出的一种抽象的计算模型，即将人们使用纸笔进行数学运算的过程进行抽象，由一个虚拟的机器替代人类进行数学运算。
![Turing Machine](https://img2.baidu.com/it/u=3330725666,318716883&fm=253&fmt=auto&app=138&f=JPEG?w=563&h=500 "Turing Machine")
组成：
* **无限长的纸带**，上面有无数个小格子，“当前位置”每次只能是其中的某一个格子
* **读写头**，能从带子上读取符号或将符号写到带子上
* **状态储存器**：储存将使用到的心灵状态的集合，需要指定其中的初始状态以及停机状态集合，当前状态属于停机状态集合时，机器停止运行
* **控制规则集**：基于当前读入的内容、当前的心灵状态找到控制规则集中对应的控制规则，然后写下（或擦除）符号、改变当前位置（左移或者右移）、改变当前的心灵状态。
* **符号集**：可能出现在纸带上或者可能被写入纸带的符号的整体
## 一组规则（程序）就是一个机器
X Y Z
1 2 3
* 1位置：改变当前位置值为X
* 2位置：左移（Y=L）右移（Y=R）
* 3位置：进入程序指令Z

例 ：1L2：改变当前位置值为1，左移，进入2状态
![输入输出简图](https://pic2.zhimg.com/80/v2-1267235001d0786d3ca06c4eb22e6b7d_1440w.webp "输入输出简图")
### 简单的程序
#### M(+3)     
输入0在左，输入1在右
**1**  1L2     1L1
**2**  1L3
**3**  1R3     1L0
#### M(2x+3)   
输入0在左，输入1在右
**1**  0R7     0R2
**2**  0R3     1R2
**3**  1R4     1R3
**4**  1L5
**5**  0L6     1L5
**6**  0R1     1L6
**7**  1L8     1L7
**8**  1L9
**9**  1R9     1L0
*** 第二个程序把*2程序的0状态(停止态)改为7状态，实现了与+3程序的组合 ***
通过此类程序组合*可以实现大量组合运算
---
由此发问
## Turing Machine的功能局限
*邱奇-图灵论题告诉我们一切可计算过程都可以用图灵机模拟*
可计算过程是指可以通过某种计算模型进行描述和规范化的过程或问题
### 丘奇论题：
λ可定义函数类与直观可计算函数类相同
### 图灵论题：
图灵机可计算函数类与直观可计算函数类相同
### 证明？
直观可计算函数不是一个精确的数学概念，因此丘奇-图灵论题是不能加以证明的。30年代以来，人们提出了许多不同的计算模型来精确刻划可计算性，并且证明了这些模型都与图灵机等价。这表明图灵机和其他等价的模型确实合理地定义了可计算性，因此丘奇-图灵论题得到了计算机科学界和数学界的公认。
#### More Information ####
<https://baike.baidu.com/item/%E9%82%B1%E5%A5%87%E5%9B%BE%E7%81%B5%E8%AE%BA%E9%A2%98/10364106?fr=ge_ala>

## Busy Beaver Problem
(数学方面的问题)
***寻找在给定规则下，具有最大步骤数（繁忙度）的停机状态的图灵机***
#### Four values of BB(n):
**BB(1)=1**
**BB(2)=6**
**BB(3)=21**
**BB(4)=107**
*It is Known that BB(5)>=47176870*
#### More infomation ####
<https://www.docin.com/p-940970823.html>

# 生命游戏
## 康威生命游戏
**生存定律**
游戏开始时，每个细胞随机地设定为**“生”或“死”**之一的某个状态。然后，根据某种规则，计算出下一代每个细胞的状态，画出下一代细胞的生死分布图。
应该规定什么样的迭代规则呢?需要一个简单的，但又反映生命之间既协同又竞争的生存定律。为简单起见，最基本的考虑是假设每一个细胞都遵循完全一样的生存定律；再进一步，把细胞之间的相互影响只限制在最靠近该细胞的8个邻居中。
也就是说，每个细胞迭代后的状态由该细胞及周围8个细胞状态所决定。作了这些限制后，仍然还有很多方法来规定“生存定律”的具体细节。例如，在康威的生命游戏中，规定了如下**生存定律**。
* 当前细胞为**死亡状态**时，当周围有3个存活细胞时，则迭代后该细胞变成存活状态(模拟繁殖)；若原先为生，则保持不变。
* 当前细胞为**存活状态**时，当周围的邻居细胞低于两个(不包含两个)存活时，该细胞变成死亡状态(模拟生命数量稀少)。
* 当前细胞为**存活状态**时，当周围有两个或3个存活细胞时，该细胞保持原样。
* 当前细胞为**存活状态**时，当周围有3个以上的存活细胞时，该细胞变成死亡状态(模拟生命数量过多)。
可以把最初的细胞结构定义为种子，当所有种子细胞按以上规则处理后，可以得到第1代细胞图。按规则继续处理当前的细胞图，可以得到下一代的细胞图，周而复始。
上面的生存定律当然可以任意改动，发明出不同的“生命游戏”。
*游戏体验：*
<https://conwaylife.com/>
## 生命游戏的图灵完备
### 图灵完备
图灵完备是指在可计算性理论里，如果一系列操作数据的规则（如指令集、编程语言、细胞自动机）可以用来模拟单带图灵机。这个词源于引入图灵机概念的数学家艾伦·图灵。
### 康威游戏中实现计算机功能
主体思路：
1. 在导线世界游戏里做原型验证
2. 在多规则生命游戏里搭建高层级的通用计算机
3. 使用OTCA metapixel单元细胞转译第二步的结果，得到低层级实现

先根据规则初步实现：系统时钟、二极管
从而根据电路知识可以构建：与门、或门、非门、异或门
后续可以构建触发器等部件。
![导线世界的游戏计算机](https://pic3.zhimg.com/80/v2-5e298ebf27e771af8f3c72c1024a5f92_1440w.webp "导线世界游戏计算机")
后略
<https://zhuanlan.zhihu.com/p/144162012>
---
附上生命游戏C++实现
<https://blog.csdn.net/myRealization/article/details/102181103?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-0-102181103-blog-128881032.235^v38^pc_relevant_anti_t3_base&spm=1001.2101.3001.4242.1&utm_relevant_index=3>