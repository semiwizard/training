## 组成结构
- 容器
> 封装常用数据结构的模板类
- - 序列容器
 - `<array>`: array<T, N>
- - - <vector>: vector<T>
- - - <deque>: deque<T>
- - - - stack<T> 容器适配器
- - - - queue<T>
- - - <list>: list<T>
- - - <forward_list>: forward_list<T>
- - 关联式容器/排序容器
> <utility> pair类模板
- - - <map>: map
- - - <map>:multmap
- - - <set>: set
- - - <set>: multset
- - 无序关联式容器/哈希容器
- - - <map>: unordered_map
- - - <map>: unordered_multmap
- - - <set>: unordered_set
- - - <set>: unordered_multset
- 算法
- - <algorithm>
- - <numberic> 少部分
后面4部分为前面两部分服务
- 迭代器 <iterator>
- 函数对象/仿函数 <functional>	?
- 适配器
- - stack<T> 容器适配器
- - queue<T>
- 内存分配器
