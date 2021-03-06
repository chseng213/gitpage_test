# cup-structure

> cup 的简单构成

## **架构构成:控制单元,存储器,运算单元**

> CPU的根本任务就是执行指令，对计算机来说最终都是一串由“0”和“1”组成的序列。CPU从逻辑上可以划分成3个模块，分别是控制单元、运算单元和存储单元，这三部分由CPU内部总线连接起来

![](https://img2018.cnblogs.com/blog/1251433/201906/1251433-20190609113803427-1944099013.png)

**1.1、控制单元**

控制单元是整个CPU的指挥控制中心，包括指令寄存器IR\(Instruction Register\)、指令译码器ID\(Instruction Decoder\)和操作控制器OC\(Operation Controller\)、时序发生器和程序计数器等部件，对协调整个电脑有序工作极为重要。它根据用户预先编好的程序，依次从存储器中取出各条指令，放在指令寄存器IR中，通过指令译码\(分析\)确定应该进行什么操作，然后通过操作控制器OC，按确定的时序，向相应的部件发出微操作控制信号。操作控制器OC中主要包括节拍脉冲发生器、控制矩阵、时钟脉冲发生器、复位电路和启停电路等控制逻辑。

* **程序计数器（PC）**又称指令计数器，用来确定下一条指令的地址。在程序开始执行前，必须将它的起始地址，即程序的一条指令所在的内存的那样地址送入PC,因此PC的内容及是从内存提取的第一条指令的地址。当执行指令时，CPU将自动修改PC内容，以便使其保持的总是将要执行的下一条指令的地址。由于大多数指令是顺序执行，所以修改的过程通才只是简单的对PC加一个1，但是遇到跳转指令时，那么后续的指令地址必须从指令的地址段取得，由跳转指定来规定。
* **指令寄存器** 用来保存当前正在执行的指令。当执行一条指令时，先把他从内存取到缓冲寄存器中，然后在传送到指令寄存器。
* **指令译码器**

  分析和执行当前指令的部件。为了执行给定的指令，必须对操作码进行测试，以便识别所要求的操作。操作码一经译码后，即可向操作控制器发出具体的操作的信号。

* **操作控制器\(OC\)**用来产生各种操作[控制信号](https://baike.baidu.com/item/%E6%8E%A7%E5%88%B6%E4%BF%A1%E5%8F%B7/10329713)。CPU内的每个功能部件都完成一定的特定功能。然而信息怎样才能在各部件之间传送呢?也就是说，数据的流动是由什么部件控制的呢? 通常把许多数字部件之间传送信息的通路称为“[数据通路](https://baike.baidu.com/item/%E6%95%B0%E6%8D%AE%E9%80%9A%E8%B7%AF)”。信息从什么地方开始，中间经过哪个寄存器或多路开关，最后传到哪个寄存器，都要加以控制。在各寄存器之间建立数据通路的任务，是由称为“操作控制器”的部件来完成的。操作控制器的功能就是根据指令[操作码](https://baike.baidu.com/item/%E6%93%8D%E4%BD%9C%E7%A0%81)和[时序信号](https://baike.baidu.com/item/%E6%97%B6%E5%BA%8F%E4%BF%A1%E5%8F%B7)，产生各种操作[控制信号](https://baike.baidu.com/item/%E6%8E%A7%E5%88%B6%E4%BF%A1%E5%8F%B7)，以便正确地建立[数据通路](https://baike.baidu.com/item/%E6%95%B0%E6%8D%AE%E9%80%9A%E8%B7%AF)，从而完成取指令和执行指令的控制。
* **时序发生器**CPU中一个类似“作息时间”的[东西](https://baike.baidu.com/item/%E4%B8%9C%E8%A5%BF/26739)，使计算机可以准确、迅速、有条不紊地工作。机器一旦被启动，即CPU开始取指令并执行指令时，[操作控制器](https://baike.baidu.com/item/%E6%93%8D%E4%BD%9C%E6%8E%A7%E5%88%B6%E5%99%A8)就利用定时脉冲的顺序和不同的脉冲间隔，有条理、有节奏地指挥机器的动作，规定在这个脉冲到来时做什么，在那个脉冲到来时又做什么，给计算机各部分提供工作所需的时间标志。为此，需要采用多级时序体制。从时间上来说，取指令事件发生在[指令周期](https://baike.baidu.com/item/%E6%8C%87%E4%BB%A4%E5%91%A8%E6%9C%9F)的第一个CPU周期中，即发生在“取指令”阶段，而取数据事件发生在指令周期的后面几个CPU周期中，即发生在“执行指令”阶段。从空间上来说，如果取出的代码是指令，那么一定送往[指令寄存器](https://baike.baidu.com/item/%E6%8C%87%E4%BB%A4%E5%AF%84%E5%AD%98%E5%99%A8)，如果取出的代码是数据，那么一定送往[运算器](https://baike.baidu.com/item/%E8%BF%90%E7%AE%97%E5%99%A8)。由此可见，时间控制对计算机来说是太重要了。

**1.2、运算单元**

是运算器的核心。可以执行算术运算\(包括加减乘数等基本运算及其附加运算\)和逻辑运算\(包括移位、逻辑测试或两个值比较\)。相对控制单元而言，运算器接受控制单元的命令而进行动作，即运算单元所进行的全部操作都是由控制单元发出的控制信号来指挥的，所以它是执行部件。由算术运算逻辑单元\(ALU\)、累加器、数据缓冲寄存器、状态寄存器和通用寄存器组组成，它是数据加工处理部件。

* **算术运算逻辑单元（ALU）**实现多组算术运算和逻辑运算的组合逻辑电路，简称ALU。由"And Gate"（[与门](https://baike.baidu.com/item/%E4%B8%8E%E9%97%A8)） 和"Or Gate"（[或门](https://baike.baidu.com/item/%E6%88%96%E9%97%A8)）构成的算术逻辑单元，主要功能是进行整数的二位元的算术运算，如加减乘\(不包括整数除法\)。
* **累加器（AC\)** 当运算器的算术逻辑单元执行算术或逻辑运算时，为ALU提供一个工作区。暂时存放运算结果信息。目前CPU中的有多达16个、32个、甚至更多的累加器。
* **数据缓冲寄存器\(DR\)** 用来暂时存放由内存读出的指令或数据，反之，当向内存存入指令或数据时，也暂时将它们存放在DR中。作为CPU和内存及外部设备间信息传送的中专站。
* **状态寄存器（PSW）** 保存由算术指令和逻辑指令运行或测试的结果建立的各种条件码内容，如运算结果进位标志、溢出标志，为零标志、为负标志等。
* 通用寄存器组

  通用寄存器

  可用于

  传送

  和暂存数据，也可参与算术逻辑运算，并保存运算结果。除此之外，它们还各自具有一些特殊功能。通用寄存器的长度取决于

  机器字长

  ，汇编语言程序员必须熟悉每个寄存器的一般用途和特殊用途，只有这样，才能在程序中做到正确、合理地使用它们。

**1.3、存储单元**

包括CPU片内缓存和寄存器组，是CPU中暂时存放数据的地方，里面保存着那些等待处理的数据，或已经处理过的数据，CPU访问寄存器所用的时间要比访问内存的时间短。采用寄存器，可以减少CPU访问内存的次数，从而提高了CPU的工作速度。但因为受到芯片面积和集成度所限，寄存器组的容量不可能很大。寄存器组可分为专用寄存器和通用寄存器。专用寄存器的作用是固定的，分别寄存相应的数据。而通用寄存器用途广泛并可由程序员规定其用途，通用寄存器的数目因微处理器而异。

## 重要元件构成:ALU,PC,Register

