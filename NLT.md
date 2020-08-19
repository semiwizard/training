## 组成结构
- 标准容器
> 封装常用数据结构的模板类
- - 序列容器
- - - `<array>`: array<T, N>，随机迭代器
- - - `<vector>`: vector<T>，随机迭代器
- - - `<deque>`: deque<T>，随机迭代器
- - - - stack<T> 容器适配器，不支持迭代器
- - - - queue<T>，不支持迭代器
- - - `<list>`: list<T>，双向迭代器
- - - `<list>`?: forward_list<T>，前向迭代器
- - 有序关联式容器/排序容器
> `<utility>` pair 类模板
- - - `<map>`: map / multmap，双向迭代器
- - - `<set>`: set / multset，双向迭代器
- - 无序关联式容器/哈希容器
> C++ 11 加入
- - - `<map>`: unordered_map / unordered_multmap，前向迭代器
- - - `<set>`: unordered_set / unordered_multset，前向迭代器
- 算法
- - `<algorithm>`
- - `<numberic>` 少部分
后面4部分为前面两部分服务
- 迭代器 `<iterator>`
> 泛型思维，每一种容器对应一种迭代器
- - 输入迭代器
- - 输出迭代器
- - 前向迭代器：++p p++ *p == !=
- - 双向迭代器：++p p++ *p == != --p p--
- - 随机迭代器：p+i/p+=i p-i/p-=i p[i] >/>= </=< p2-p1
- 函数对象/仿函数 `<functional>`	?
- 适配器
- - stack<T> 容器适配器
- - queue<T>
- 内存分配器
