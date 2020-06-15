## 基本语法
- `#` 单行注释，`'''` 和 `"""` 多行注释
- 缩进表示代码块，少用`TAB`？
- `\` 语句换行，括号中不需要使用
## 变量
- isinstance 和 type 的区别：
  type()不会认为子类是一种父类类型；
  isinstance()会认为子类是一种父类类型。
 - / 返回一个浮点数，// 返回一个整数
 - 可为多个变量赋值，可连续赋值
 - 在 python 中，类型属于对象，变量是没有类型的
 - 在 python 中，strings, tuples, 和 numbers 是不可更改的对象，而 list,dict 等则是可以修改的对象。
  不可变类型：变量赋值 a=5 后再赋值 a=10，这里实际是新生成一个 int 值对象 10，再让 a 指向它，而 5 被丢弃，不是改变a的值，相当于新生成了a。
  可变类型：变量赋值 la=[1,2,3,4] 后再赋值 la[2]=5 则是将 list la 的第三个元素值更改，本身la没有动，只是其内部的一部分值被修改了。
## 标准数据类型
- Number(数字)
- - int (整数), 只有一种int长整型，没有 python2 中的 Long
- - bool (布尔), 如 True
- - float (浮点数), 如 1.23、3E-2
- - complex (复数), 如 1.1 + 2.2j
- String（字符串）
- - 单双引号完全相同
- - 使用r可以让反斜杠不发生转义。 如 r"this is a line with \n" 则\n会显示，并不是换行。
- - 没有单独的字符类型，一个字符就是长度为1的字符串
- - 字符串不能改变。向一个索引位置赋值，比如word[0] = 'm'会导致错误。
- - spilt()分割函数
```
txt = "Google#Runoob#Taobao#Facebook"
# 第二个参数为 1，返回两个参数List
txtList = txt.split("#", 1)
#输出
txtList = ['Google', 'Runoob#Taobao#Facebook']

```
- List（列表）
- - del 删除
- - 截取与拼接
- - 嵌套
- - 函数
![](https://www.runoob.com/wp-content/uploads/2013/11/list_slicing1.png)
- Set（集合）
- - 创建空集合必须用 set() 而不是 { }，因为 { } 是用来创建一个空字典。
- Tuple（元组）
```
tup1 = ()    # 空元组
tup2 = (20,) # 一个元素，需要在元素后添加逗号
```
- Dictionary（字典）
- - 字典是一种映射类型，字典用 { } 标识，它是一个无序的 键(key) : 值(value) 的集合。
- - 键(key)必须使用不可变类型。在同一个字典中，键必须是唯一的。
- - 列表是有序的对象集合，字典是无序的对象集合。两者的区别：字典当中的元素通过`键`来存取，而不是偏移。
- 数据类型转换
## 运算符
- 算数
- - `/` 浮点除
- - `//` 取整除
- - `**` 幂
- 逻辑
- - and
- 比较
- - `==` 相等
- 赋值
- - `**=` 	幂赋值运算符
- 位运算符
- 成员
- - in
- - not in
- 身份
- - is
- - not is
- 优先级
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
- __name__属性
  一个模块被另一个程序第一次引入时，其主程序将运行。如果想在模块被引入时，模块中的某一程序块不执行，可以用__name__属性来使该程序块仅在该模块自身运行时执行。每个模块都有一个__name__属性，当其值是'__main__'时，表明该模块自身在运行，否则是被引入。
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
## 文件
```
os.path.abspath(path)	返回绝对路径（包含路径和文件名）
os.path.basename(path)	返回纯文件名
os.path.dirname(path)	返回纯文件路径
```
#读文件
f1 = open(prj_path, 'r+')
1. f1.read()
2. f1.readline()
3. f1.readlines()
#字符串匹配
re.compile(pattern[, flags])  #用于编译生成一个正则表达式对象
1. re.match(pattern, string, flags=0) #从字符串的起始位置开始
2. re.search(pattern, string, flags=0)  #扫描整个字符串并返回第一个成功的匹配
3. re.findall(string[, pos[, endpos]])
4. re.sub(pattern, repl, string, count=0, flags=0)  #

## 面向对象
## 其他
- `-h`参数查看各参数帮助信息
- 有两种退出方式：
os._exit() 会直接将python程序终止，之后的所有代码都不执行。
sys.exit() 会抛出SystemExit异常，如果没有被捕获，python解释器将会退出，否则还会执行，可以捕获这个异常做些清理工作。比较优雅
##爬虫
- 爬取（requests）、分析（re）、存储


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
