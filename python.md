## 基本语法
- `#` 单行注释，`'''` 和 `"""` 多行注释
- 缩进表示代码块，少用`TAB`？
- `\` 语句换行，括号中不需要使用
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
![](https://www.runoob.com/wp-content/uploads/2013/11/o99aU.png)
- Tuple（元组）
```
tup1 = ()    # 空元组
tup2 = (20,) # 一个元素，需要在元素后添加逗号
```
- List（列表）
- - del 删除
- - 截取与拼接
- - 嵌套
- - 函数
![](https://www.runoob.com/wp-content/uploads/2013/11/list_slicing1.png)
- Set（集合）
- - 创建空集合必须用 set() 而不是 { }，因为 { } 是用来创建一个空字典。
- Dictionary（字典）
- - 字典是一种映射类型，字典用 { } 标识，它是一个无序的 键(key) : 值(value) 的集合。
- - 键(key)必须使用不可变类型。在同一个字典中，键必须是唯一的。
- - 列表是有序的对象集合，字典是无序的对象集合。两者的区别：字典当中的元素通过`键`来存取，而不是偏移。
- 数据类型转换
## 变量
- isinstance 和 type 的区别：
  type()不会认为子类是一种父类类型；
  isinstance()会认为子类是一种父类类型。
 - / 返回一个浮点数，// 返回一个整数
 - 可为多个变量赋值，可连续赋值
## 运算符
- 算数
- - `/` 浮点除
- - `//` 取整除
- - `**` 幂
- 逻辑
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
## 其他
- `-h`参数查看各参数帮助信息
## 参考文献
1. [Python3菜鸟教程](https://www.runoob.com/python3/python3-tutorial.html)
