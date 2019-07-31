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
![](https://www.runoob.com/wp-content/uploads/2013/11/list_slicing1.png)
- Set（集合）
- Dictionary（字典）
## 变量
- isinstance 和 type 的区别：
  type()不会认为子类是一种父类类型；
  isinstance()会认为子类是一种父类类型。
 - / 返回一个浮点数，// 返回一个整数
 - 可为多个变量赋值，可连续赋值
 - 
## 其他
- `-h`参数查看各参数帮助信息
## 参考文献
1. [Python3菜鸟教程](https://www.runoob.com/python3/python3-tutorial.html)
