集合与映射也是两个常用的容器,`set`类似于数学上的集合
#### 初始化
```C++
# include <set>
set<string> s;
```

set不允许元素重复，有重复就会被忽略，但multiset允许
#### 方法
```C++
s.size()           // 返回元素个数
s.empty()          //返回set是否是空的
s.clear()          //清空
s.begin()          //第0个数，支持++或--，返回前驱和后继
s.end()            //最后一个的数的后面一个数，支持++或--，返回前驱和后继
s.insert()        //插入一个数
s.find()          //查找一个数
s.count()         //返回某一个数的个数
s.erase(x)        //删除所以x  时间复杂度 O(k + logn)
s.erase(s.begin(),s.end())//删除一个迭代器

//核心函数
s.lower_bound(x)        //返回大于等于x的最小的数的迭代器 核心操作
s.upper_bound(x)        //返回大于x的最小的数的迭代器 不存在返回end()
```



