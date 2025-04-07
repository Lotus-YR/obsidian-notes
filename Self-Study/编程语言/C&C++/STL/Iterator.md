迭代器实现了抽象的指针（智能指针）功能，它们用于指向容器中的元素，对容器中的元素进行访问和遍历

在STL中，迭代器是作为类模板来实现的（在头文件`iterator`中定义），它们可分为以下几种类型：
**根据访问修改权限分类**
- 输出迭代器（output iterator，记为：**OutIt**）
    - 可以修改它所指向的容器元素
    - 间接访问操作（`*`）
    - `++`操作
- 输入迭代器（input iterator，记为：**InIt**）
    - 只能读取它所指向的容器元素
    - 间接访问操作（`*`）和元素成员间接访问（`->`)
    - `++` 、 ` == ` 、 `!=`操作

**根据迭代方式分类**
- 前向迭代器（forward iterator，记为：**FwdIt**）
    - 可以读取/修改它所指向的容器元素   
    - 元素间接访问操作（`*`）和元素成员间接访问操作（`->`）
    - `++` 、` == ` 、`!=`操作
- 双向迭代器（bidirectional iterator，记为：**BidIt**）
    - 可以读取/修改它所指向的容器元素
    - 元素间接访问操作（`*`）和元素成员间接访问操作（`->`）
    - `++`、`--`、` == `、`!=`操作
- 随机访问迭代器（random-access iterator，记为：**RanIt**）
    - 可以读取/修改它所指向的容器元素
    - 元素间接访问操作（`*`）、元素成员间接访问操作（`->`）和下标访问元素操作（`[]`）
    - `++`、`--`、`+`、`-`、`+=`、`-=`、` == `、`!=`、`<`、`>`、`<=`、`>=`操作


#### 各容器的迭代器类型
- 对于`vector`、`deque`以及`basic_string`容器类，与它们关联的迭代器类型为*随机访问迭代器（RanIt）*
- 对于`list`、`map/multimap`以及`set/multiset`容器类，与它们关联的迭代器类型为*双向迭代器（BidIt）*

| CONTAINER                 | ITERATOR CATEGORY        |
| ------------------------- | ------------------------ |
| vector                    | Randon access            |
| deque                     | Randon access            |
| list                      | Bidirectional            |
| map/multimap/set/multiset | Bidirectional(const key) |
| unorder_set/unordered_map | Forward(const key)       |
| stack                     | Not supported            |
| queue                     | Not supported            |
| priority_queue            | Not supported            |

