# Verilog语言
- 实例调用
- 命名端口连接
```
module tester;
reg [1:0] SELECT;
reg IN0;
wire OUT;
// 实例调用mux模块方法一
mux my_mux1 (OUT, SELECT, IN0); 
//使用命名端口调用实例，括号外面是模块声明时的端口，括号内是实际的端口连接
mux my_mux2 (.out(OUT), .select(SELECT), .in0(IN0)); //.形参(实参)
// 需要仿真的激励代码
initial
  begin
  end
endmodule
```
## 数据类型
```
module test(out, in);
  output [wire] out;
  input reg in;
endmodule
```
- 连线型（Net）
- - wire，默认初始值为高阻态“Z”，端口隐含声明
- 寄存器型（Register）
- - reg：常用的寄存器型变量，默认初始值为不定态“X”，如触发器、寄存器等。reg 指一个储存数值的变量，寄存器类型变量与真实的硬件寄存器不同。
- - integer：32位带符号整数型变量
- - real：64位带符号实数型变量
- - time：无符号时间变量
- 向量
- 数组
- 参数
- 强度
## 流程控制
- 选择结构
- - casex，将条件数值中的x、z均作为无关值
- - casez，仅将z作为无关值
- 循环结构
- - forever，用于无限循环
- - repeat，用于指定次数循环
## 运算符
- 缩减：`&(4'b1011) = 0`
- 求幂：`2**4 = 16`
- 拼接：`{2'b10,2'b11} = a'b1011`
- 重复：`{2{2'b01}} = 4'b0101`
## 赋值
|  | 持续赋值 | 过程赋值 | 过程持续赋值 |
| -------- | ------- | ------- | ------ |
| 语法/关键字 | assign | -- |  |
| 符号 | `=` | 阻塞赋值用`=`/非阻塞赋值用`<=` |  |
| 位置 | 不可出现在 always 或 initial 语句块 | 只能出现在 always 或 initial 过程块 |  |
| 执行条件 | 表示直通，总是处于激活状态，右值一旦变化，立即重新计算并反馈到左侧 | 只有赋值语句被执行才赋值，即必须满足过程块中敏感信号表，还有过程块中的各种条件语句才会执行；且执行完之后，即使右值发生变化，也不影响左侧 |  |
| 用途 | 用来对组合逻辑电路进行建模及对wire数据间的连接进行描述；用于驱动 wire（对 wire 赋值），等价于门级描述 | 用来对时序逻辑电路进行行为描述；用于对 reg 等变量赋值 |  |

1. 对wire型数据赋值时，只能在**结构体外**进行**连续赋值**，只能使用`=`。
2. 对变量赋值时，只能在**结构体内**进行**过程赋值**，可用`=`或`<=`，根据需求是阻塞式还是非阻塞式。
3. 如果一定要将wire型数据在**过程块内**使用，只能使用**过程连续赋值语句**（只有在testbench中用过），只能用`=`。

### 持续赋值

### 过程赋值
- 阻塞赋值：顺序执行。
- 非阻塞赋值：在同一个always过程块中，语句并发执行，在过程块结束时才执行赋值。
- initial过程
- always过程
### 过程持续赋值
- assign/deassign
- - 只能用于对 ==reg== 型变量的连续赋值，而不能用于对 wire 数据连续赋值
- force/release
- - 两者都可以进行连续赋值
## 时序控制
### 延迟时序控制 #
- 常规延迟
- 内嵌延迟
### 事件延迟控制 @
- 常规事件
- 命名事件
### 电平敏感时序控制 wait(a)
## 代码块
- 顺序代码块：begin-end
- 并行代码块：fork-join，并发执行

## 参考文献
1. [Verilog学习笔记基本语法篇（一）·········数据类型](https://www.cnblogs.com/SYoong/p/5849168.html)
2. [Verilog基础语法](https://blog.csdn.net/zhangshuaiisme/article/details/78993582)
3. [Verilog赋值语句](https://blog.csdn.net/firstlai/article/details/52712042)
4. [关于Verilog中的几种赋值语句](https://www.cnblogs.com/nanoty/archive/2012/10/21/2733017.html)
5. [Verilog 初级入门概念讲解](https://blog.csdn.net/Born_/article/details/52903920)
6. [Verilog中的数据类型](https://blog.csdn.net/wordwarwordwar/article/details/53731372)
7.[Verilog数据类型](http://blog.sina.com.cn/s/blog_615047920100ih0k.html)
8.[附录 20Verilog 硬件描述语言参考4](http://read.pudn.com/downloads70/ebook/251634/%E9%99%84%E5%BD%95%20Verilog%20%E7%A1%AC%E4%BB%B6%E6%8F%8F%E8%BF%B0%E8%AF%AD%E8%A8%80%E5%8F%82%E8%80%834.pdf)
9.[第5章 门级建模](http://gr.xjtu.edu.cn/c/document_library/get_file?p_l_id=1736655&folderId=1736675&name=DLFE-18899.pdf)

# VHDL语言

- VHDL描述的目的是给出数字电路（Digital Electronics）和系统的模型；
- VHDL语言的基本结构 = 实体 + 结构体1 + ... + 结构体n；

## 1、参数部分：库（Liberary），包集合（Package）

```
# 库
LIBERARY IEEE;
# 定义标准逻辑数据类型
USE IEEE.STD_LOGIC_1164.ALL;
# 调用无符号数、标准逻辑与整数间的算术、比较函数
USE STD_LOGIC_UNSIGNED.ALL;
# 定义标准逻辑的算术运算函数
USESTD_LOGIC_ARITH.ALL
```

## 2、实体（Entity）~~接口~~说明部分：可视

- 功能：规定设计单元的I/O接口和引脚；用于描述外部接口信号；
- 可以表示一个系统，芯片，单元，门电路
- 实体名必须=文件名，!=保留字，符合标识符规范

```
# 全加器的实体说明
Entity full_adder is
port(a, b, sin: IN, BIT;
    s, cout: OUT, BIT);
END full_adder;
```

### 端口模式

> 用来说明数据、信号通过该端口的方向

- IN：
- OUT：
- BUFFER：
- INOUT：
- LINKAGE：

### 端口数据类型

- BOOLEAN
- BIT
- BIT_VECTOR
- INTEGER
- STD_LOGIC：~~U、X~~、0、1、Z、~~W~~、L、H、_
- STD_LOGIC_VECTOR

## 3、构造体（Architecture）~~描述~~部分：功能

> 功能：定义设计单元的具体构造和操作（行为）；具体说明系统内部的结构和行为，定义实体功能，规定实体的数据流程，指明实体内部元件的连接关系；

### 分类

- 行为描述法：用进程语句顺序描述，process
- 数据流描述法：逻辑方程
- 结构描述法：并行，component（模板元件说明）
- 混合描述法

### 子结构描述

- 多进程描述
- 多模块描述
- 多子程序描述

### 数据声明

- 数据对象类型 数据名称:数据类型 约束条件:=表达式；

### 标识符 

- 大小写不敏感

### 数据对象

|          | CONSTANT（常量）                           | VARIABLE（变量）                             | SIGNAL（信号）                               | FILE（文件） |
| -------- | ------------------------------------------ | -------------------------------------------- | -------------------------------------------- | ------------ |
| 用法     | 固定值（电源、地等）                       | 暂时数据的局部存储（算法描述）               | 代表实际连线                                 |              |
| 作用域   | 全局量                                     | 局部量                                       | 全局量                                       |              |
| 说明场合 | 可用于其他两种场合                         | 只能在process说明区中（begin前）说明，只能用于process中 | 在ARCHITECTURE说明区中申明                   |              |
| 赋值     | `:=`，在程序中不能被赋值，声明的时候初始化 | `:=`，赋值后立即变化为新值，无延迟           | `<=`，先改变驱动值，但不立即更新赋值，有延迟 |              |

> 赋值原则：相同位宽，相同数据类型。

### 数据类型

- 标量型
- 复合型
- 寻址型
- 文件型

### 属性

### 运算符：算数，关系，逻辑

## 4、配置（Configuation）

## 语句

### 并行语句

> 用于描述模块间的关系；结构体内并行执行；

- 变量赋值：`<=`
- process 进程语句：敏感变量列表
- when-else 并行信号赋值语句
- with-select-when 选择信号赋值语句
- 并行断句
- 块语句
- 元件例化语句
- 生成语句：for方案，if方案

### 顺序语句：一般用来实现算法；

- 变量赋值：`:=`
- if-then-elseif 语句
- case-when 语句
- loop 语句
- next 语句
- exit 语句
- return 语句
- null 语句
- wait 语句
- 过程调用和断言语句
- report 语句

|          | when-else                                                   | with-select-when          | if-then-else               | case-when                      |
| -------- | ----------------------------------------------------------- | ------------------------- | -------------------------- | ------------------------------ |
| 语句属性 | 只能在 process 外并行执行，是 with-select-when 更一般的形式 | 只能在 process 外并行执行 | 只能在 process 里顺序执行  | 只能在 process 里顺序执行      |
| 优先级   | 有                                                          | 无                        | 有                         | 无                             |
| 选择条件 | 多个信号多种组合，不必互斥                                  | 一个信号的不同值，互斥    | 多个信号多种组合，不必互斥 | 一个信号的不同值，互斥         |
| 用途     | 优先编码器，地址译码器                                      | 编码，译码，多路选择器    | 优先编码器，地址译码器     | 编码，译码，多路选择器，状态机 |

## 用VHDL设计基本的逻辑电路

- 组合逻辑电路
- - 门电路
- - 编码器（Encoder）
- - 译码器（Decoder）n:1
- - 多路选择器（Multiplexer）
- - 加法器
- 时序逻辑电路
- - 触发器（Flip Flop）
- - 寄存器和移位寄存器
- - 计数器（Counter）

## 部件定义（Component）和部件映像（Port Map）
## 逻辑综合（logic synthesis）
> 定义：用HDL进行电路的高级抽象（通常是数字电路寄存器传输级的数据、行为）描述数字电路的逻辑功能，经过布尔函数化简、优化后，转换到的逻辑门级别的实际电路连线网表的过程。简单来说，综合就是把Verilog/HDL语言/原理图转换为（门级）综合网表的过程。
## 参考文献
1. [VHDL 语法总结](https://allansheng.wordpress.com/2018/07/11/vhdl-%E8%AF%AD%E6%B3%95%E6%80%BB%E7%BB%93/)
2. [VHDL 语言的常用语法 ](http://www.go-gddq.com/down/2011-07/11071222382580.pdf)
3. [从Verilog到VHDL：基本语法](https://www.cnblogs.com/ifys/archive/2010/09/10/1860615.html)
4. [vhdl入门(一)-vhdl的代码结构](https://blog.csdn.net/weixin_38071135/article/details/82357023)
5. [Verilog/VHDL语法学习是掌握基本代码设计的技能以及经验总结](http://m.elecfans.com/article/605163.html)
6. [逻辑综合 - 维基百科](https://zh.wikipedia.org/zh-hans/%E9%80%BB%E8%BE%91%E7%BB%BC%E5%90%88)
7. [介绍FPGA的综合](https://blog.csdn.net/jeakon/article/details/9493835)
8. [fpga开发的疑问？（关于高层次综合）](https://www.zhihu.com/question/24898211/answer/29791473)
9. [VHDL中信号与变量的区别及赋值的讨论](https://blog.csdn.net/oier_xcj/article/details/78244474)
10. [VHDL - 维基百科](https://zh.wikipedia.org/zh-hans/VHDL)
# FPGA相关术语

| 逻辑电路 | 组合（逻辑）电路                                             | 时序（逻辑）电路                                             |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 决定因素 | 当前输入                                                     | 当前输入和原状态，由边沿信号切换                             |
| 分析方法 | 根据逻辑电路图，写出各输出端的逻辑表达式；化简与变换；列真值表；逻辑功能评述。 | 驱动方程：按组合逻辑电路的分析方法，写出触发器输入的逻辑关系；状态方程：按触发器的特性表或特性方程分析输入与触发器的输出（触发器的状态）的逻辑关系；输出方程：按组合逻辑电路的分析方法，将触发器输出（触发器的状态）与时序逻辑电路输出间的组合逻辑关系表示出来； |

- 二者最本质的区别是时序电路有记忆功能；

![时序逻辑电路](https://wikipedia.tk.gugeeseo.com/baike-File:Sxdl.jpg)

###
- 逻辑仿真
- 逻辑综合
## 时序波形图
- GND   在电子电路理论里，接地通常被理想化为一个无穷电荷电源或电荷吸收槽，可以无限制的吸收电流，同时保持电位不变。
- VCC   接入电路的电压
## 封装
- Quad Flat Pack 塑料方形扁平封装
- - Low profile QFP 100 144 薄型QFP
- Quad Flat Non-leaded Package 32 42 88 四侧（方形）无引脚扁平封装
- Ball Grid Array 球栅阵列封装
- - Micro BGA 160 微型BGA
- - Ultra BGA 增强型BGA
- - Plastic BGA 256 256M 塑料BGA
- Wafer-Level Chip Scale Package 晶圆级芯片尺寸封装
- Dual In-Line Package 双侧直插封装
## 参考文献
1. [时序逻辑电路 - 维基百科](https:/zh.wikipedia.org/zh-hans/%E6%97%B6%E5%BA%8F%E9%80%BB%E8%BE%91%E7%94%B5%E8%B7%AF)
2. [串行 - 维基百科](https://zh.wikipedia.org/zh-hans/%E4%B8%B2%E8%A1%8C)
3. [数字电路学不好？是因为你不懂时序！ ](http://www.sohu.com/a/120944023_488169)
4. [半导体IP核 - 维基百科](https://zh.wikipedia.org/zh-hans/%E5%8D%8A%E5%AF%BC%E4%BD%93IP%E6%A0%B8)
5. [数字电路 - 维基百科](https://zh.wikipedia.org/zh-hans/%E6%95%B0%E5%AD%97%E7%94%B5%E8%B7%AF)
6. [集成电路 - 维基百科](https://zh.wikipedia.org/zh-hans/%E6%95%B8%E4%BD%8D%E9%9B%BB%E8%B7%AF)
7. [真值表 - 维基百科](https://zh.wikipedia.org/zh-hans/%E7%9C%9F%E5%80%BC%E8%A1%A8)
8. [逻辑门 - 维基百科](https://zh.wikipedia.org/zh-hans/%E9%80%BB%E8%BE%91%E
