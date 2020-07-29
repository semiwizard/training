## 简介
有动态类型系统和垃圾回收功能，能自动管理内存使用，且支持面向对象、命令式、函数式和过程式编程等。
## 基本语法
- `#` 单行注释，`'''` 和 `"""` 多行注释
- `\` 用于语句换行，括号中不需要使用
## 代码风格
- 官方文档：https://www.python.org/dev/peps/pep-0008/
- 可读性：代码的读取次数比编写的次数多
- import this #The Zen of Python
[空格]
用 4 个空格缩进，对空格敏感，用空格来划分代码块和区分代码层次
不要用制表符，可设置编辑器自动将Tab展开为空格
不要混用制表符和空格
用 字典(dict)、 列表(list)、元组(tuple)、 参数(argument)列表时， 应在尾随逗号 "," 后添加一个空格，并且使用字典(dict)时，在 ":" 号后添加空格，而不是在前面添加。
在括号/参数前、文档注释前后不加空格。
当用-t选项调用Python 2命令行解释器时，会发出有关非法混用制表符和空格的代码的警告。当使用-tt时，这些警告变为错误。

续行
1. 与打开定界符对齐
2. 悬挂式缩进:
- 元素垂直对齐;
- 第一行不应包含任何参数;
- 添加4（个数可选）个额外的空格以区分参数和其余语句.

[空行]
Class间用两个空行，函数间用一个空行

[命名]
用驼峰命名法命名类名，用下划线分隔方式命名方法或者函数

[标识符]
_foo（单下划线开头）：弱“内部使用”标识。对于from M import *，将不导入所有以下划线开头的对象，包括包、模块、成员。
foo_（单下划线结尾）：为了避免与python关键字的命名冲突
__foobar（双下划线开头）：模块内的成员，表示私有成员，外部无法直接调用。
__foobar__（双下划线开头双下划线结尾）：指那些包含在用户无法控制的名字空间中的“魔术”对象或属性，如类成员的__name__、__doc__、__init__、__import__、__file__等。建议永远不要将这样的命名方式应用于自己的变量或函数

## 变量
- isinstance 和 type 的区别：
  type()不会认为子类是一种父类类型；
  isinstance()会认为子类是一种父类类型。
 - 可为多个变量赋值，可连续赋值
 - 动态语言：变量本身类型不固定
 - 类型属于对象，变量没有类型
 - strings, tuples, 和 numbers 是不可更改的对象，而 list, dict 等则是可以修改的对象。
  不可变类型（对象）：变量赋值 a=5 后再赋值 a=10，这里实际是新生成一个 int 值对象 10，再让 a 指向它，而 5 被丢弃，不是改变a的值，相当于新生成了a。
  可变类型：变量赋值 la=[1,2,3,4] 后再赋值 la[2]=5 则是将 list la 的第三个元素值更改，本身la没有动，只是其内部的一部分值被修改了。
## 标准数据类型
- None  #空对象
- Number(数字)
- - int (整数), 只有一种int长整型，没有 python2 中的 Long
- - - bool (布尔), 如 True
- - float (浮点数), 如 1.23、3E-2
- - complex (复数), 如 1.1 + 2.2j
- String（字符串）
- - 索引和截取，截取按[)计算，[0：n]可简写为[:n]
- - 单双引号完全相同
- - 字符串前加r表示不转义反斜杠。 如 r"this is a line with \n" 则\n会显示，并不是换行。
- - 没有单独的字符类型，一个字符就是长度为1的字符串
- - 字符串不能改变。向一个索引位置赋值，比如word[0] = 'm'会导致错误。
- - spilt()分割函数
```
txt = "Google#Runoob#Taobao#Facebook"
# 第二个参数表示分隔次数，返回两个参数List
txtList = txt.split("#", 1)
#输出
txtList = ['Google', 'Runoob#Taobao#Facebook']
```
- List（列表）
- - 与字符串不同，列表元素可以改变
- - del 删除
- - 截取[0：-1：步长)
- - 拼接+操作符
- - 嵌套
- - 函数

![](https://www.runoob.com/wp-content/uploads/2013/11/list_slicing1.png)
- Set（集合）
- - 创建空集合必须用 set() 而不是 { }，因为 { } 是用来创建一个空字典。
- - set(list) 传入list创建set
- - add()/remove()
- - s1&s2 s1|s2   交集/并集
- Tuple（元组）：和list相似的数据结构，初始化后不可变，速度比list快，没有增删改，安全，元素为list等时list的内容可变（不可变指tuple指向的元素不可变，但是元素再指向的元素不受约束）
```
tup1 = ()    # 空元组
tup2 = (20,) # 一个元素，需要在元素后添加逗号
```
- Dictionary（字典）
- - 字典是一种映射类型，字典用 { } 标识，它是一个无序的 键(key) : 值(value) 的集合。
- - 键(key)必须使用不可变类型。在同一个字典中，键必须是唯一的。
- - 列表是有序的对象集合，字典是无序的对象集合。两者的区别：字典当中的元素通过`键`来存取，而不是偏移。
```
#1.  ~in~
if'name' in people:
    value = people['name']
#2. get()方法
value = people.get('name', None)
if None == value:
  print 'not find'
```
- 数据类型转换
## 运算符
~, |, ^, &, <<, >>必须应用于整数
- 算数
- - `/` 浮点除
- - `//` 取整除
- - `**` 幂
- 逻辑： and
- 比较： `==` 
- 幂赋值运算： `**=`
- 位运算
- 成员：in、not in
- 身份：is、not is
- 优先级
- 生成器表达式
- lamda匿名函数
- 条件表达式：y if do else x
- Python允许像数学的常用写法那样连着写两个比较运行符。比如a < b < c与a < b and b < c等价。
## 解释器
- 脚本式编程
  在Linux/Unix系统中，可以在脚本顶部添加`#! /usr/bin/env python3`命令，让Python脚本可以像SHELL脚本一样可直接执行
  然后修改脚本权限，使其有执行权限，命令如下：
  $ chmod +x hello.py
  执行以下命令：
  ./hello.py
## 函数
- python 函数的参数传递：
  不可变类型：类似 c++ 的值传递，如 整数、字符串、元组。如fun（a），传递的只是a的值，没有影响a对象本身。比如在 fun（a）内部修改 a 的值，只是修改另一个复制的对象，不会影响 a 本身。
  可变类型：类似 c++ 的引用传递，如 列表，字典。如 fun（la），则是将 la 真正的传过去，修改后fun外部的la也会受影响
- 参数
> 可变参数用*args或**dictargs表示，即在形式参数名字前加一个*号，表示这是由多个实参组成的可变参数，该形参视作tuple数据类型；在形式参数名字前加**号，表示这是由多个实参组成的可变参数，该形参视作dict数据类型。实际上，在一个"集合(collection)类型"（包括set、list、tuple甚至bytes、str等）的变量前加一个*号，获得了其中所有元素作为多个对象。
- - 必需参数
- - 关键字参数
- - 默认参数
- - 不定长参数
- 匿名函数
  lambda 只是一个表达式，函数体比 def 简单很多。
  lambda的主体是一个表达式，而不是一个代码块。仅仅能在lambda表达式中封装有限的逻辑进去。
  lambda 函数拥有自己的命名空间，且不能访问自己参数列表之外或全局命名空间里的参数。
  虽然lambda函数看起来只能写一行，却不等同于C或C++的内联函数，后者的目的是调用小函数时不占用栈内存从而增加运行效率。
- 变量作用域
- - L （Local） 局部作用域
- - E （Enclosing） 闭包函数外的函数中
- - G （Global） 全局作用域
- - B （Built-in） 内置作用域（内置函数所在模块的范围）
- - 以 L –> E –> G –>B 的规则查找，即：在局部找不到，便会去局部外的局部找（例如闭包），再找不到就会去全局找，再者去内置中找。
## 模块 
- pip list：查看已安装的模块
- yolk -l
- pydoc modules
- __name__属性
  一个模块被另一个程序第一次引入时，其主程序将运行。如果想在模块被引入时，模块中的某一程序块不执行，可以用__name__属性来使该程序块仅在该模块自身运行时执行。每个模块都有一个__name__属性，当其值是'__main__'时，表明该模块自身在运行，否则是被引入。
```
>>> from datetime import datetime
>>> now = datetime.now() # 获取当前datetime
>>> print(now)
2015-05-18 16:28:07.198690
>>> print(type(now))
<class 'datetime.datetime
```
注意到datetime是模块，datetime模块还包含一个datetime类，通过from datetime import datetime导入的才是datetime这个类。

如果仅导入import datetime，则必须引用全名datetime.datetime。
## 输入和输出

### 传参
- ~sys.argv~
- ~optparse~ (被弃用)
- ~getopt~ 
- argparse （输入参数解析）+ configparser （解析配置文件）

```
#sys.argv示例
import sys

print sys.argv  #
print len(sys.argv) #参数个数
print sys.argv[0] #脚本名
print sys.argv[1:]  #参数列表

#输入：
$ python test.py 1212 232 3232

#输出：
['test.py', '1212', '232', '3232']  #
4
test.py
['1212', '232', '3232']

```
```
import argparse
parser = argparse.ArgumentParser()
# 短选项
parser.add_argument("-v", "--verbose", help="increase output verbosity",
                    action="store_true")
parser.parse_args()
```
```
#configparser
```
## 文件
```
os.path.abspath(path)	返回绝对路径（包含路径和文件名）
os.path.basename(path)	返回纯文件名
os.path.dirname(path)	返回纯文件路径
dirPath, fileName = os.path.split(os.path.realpath(__ file __)) #当前文件路径和文件名组成的元组
```
## 读文件
f1 = open(prj_path, 'r+')
1. f1.read() #读入到字符串
2. f1.readline()
3. f1.readlines()

## 正则匹配
pattern
- ^$
- \s
- \S
1. re.match(pattern, string, flags=0) #从字符串的起始位置开始
2. result = re.search(pattern, string, flags=0)  #扫描整个字符串，并返回第一个成功的匹配，失败返回None
  result.group()  #匹配的整个字符串
  result.group(1)  #第一个括号位置匹配的字符串
  result.groups() #返回一个包含所有小组字符串的元组，从 1 到 所含的小组号。
  result.start()  #匹配的字符串的起始下标
  result.end()
  result.span() #匹配的字符串的起始和结束下标（开区间）的元组
3. re.compile(pattern[, flags])  #用于编译生成一个正则表达式对象
  re.findall(string[, pos[, endpos]])  #返回list
4. re.sub(pattern, repl, string, count=0, flags=0)  #

## html解析
## 生成html
- pyh模块

## 面向对象
Python是完全面向对象的语言，函数、模块、数值、字符串都是对象；并且完全支持继承、重载、派生、多重继承。
当定义对象方法时，必须显式地定义第一个参数，一般该参数名都使用self，用于访问对象的内部数据。这里的self相当于C++, Java里面的this变量，但是我们还可以使用任何其它合法的参数名，比如this和mine等，self与C++,Java里面的this不完全一样，它可以被看作是一个习惯性的用法，我们传入任何其它的合法名称都行
## 其他
- `-h`参数查看各参数帮助信息
- 有两种退出方式：
os._exit() 会直接将python程序终止，之后的所有代码都不执行。
sys.exit() 会抛出SystemExit异常，如果没有被捕获，python解释器将会退出，否则还会执行，可以捕获这个异常做些清理工作。比较优雅
##爬虫
- 爬取（requests）、分析（re）、存储

## 模式
MVC被认为是一种架构模式而不是一种设计模式，区别在于前者比后者的范畴更广。
https://blog.csdn.net/Burgess_zheng/article/details/86762248#%C2%A0%20%C2%A0%20%E8%AE%BE%E8%AE%A1%E6%A8%A1%E5%BC%8F%E5%88%86%E7%B1%BB

## 参考文献
1. [Python3菜鸟教程](https://www.runoob.com/python3/python3-tutorial.html)
2. [向python脚本传递参数的方法](https://blog.csdn.net/BabyFish13/article/details/53769525)
3. [Python逐行读取文件内容的三种方法](https://www.cnblogs.com/dcc001/p/5705438.html)
4. [python逐行读写txt文件](https://blog.csdn.net/matrix_google/article/details/76861485)
5. [保存网页 TypeError: must be str, not bytes](https://blog.csdn.net/gdp12315_gu/article/details/47314175)
6. [保存网页 TypeError: must be str, not bytes - Python使用pyh生成HTML文档](https://www.jb51.net/article/136166.htm)
7. [Python PyH模块中文文档](http://hanxiaomax.github.io/trans/pyh-chinese-doc/)
8. [Pyh模块+Bootstrap框架](https://www.cnblogs.com/1fengchen1/p/9440881.html)
9. [os.path() 模块](https://www.runoob.com/python3/python3-os-path.html)
10. [argparse -- 命令行选项、参数和子命令解析器¶](https://docs.python.org/zh-cn/3/library/argparse.html)


## 回归测试
1. [回归测试总结](https://blog.csdn.net/caiqcong/article/details/4172128)
2. [软件测试 - 维基百科](https://zh.wikipedia.org/zh-hans/软件测试)
3. [回归测试 - 维基百科](https://zh.wikipedia.org/zh-hans/回归测试)
4. [自动化测试 - 维基百科](https://zh.wikipedia.org/zh-hans/自动化测试)
