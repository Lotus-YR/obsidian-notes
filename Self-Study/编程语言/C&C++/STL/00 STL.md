### STL
Standard Template Library，即即标准模板库，是一个具有工业强度的，高效的C++程序库。

STL中六大组件：容器、迭代器、算法、仿函数、迭代适配器、空间配制器


**容器类模板**
容器用于存储**序列化的**数据，如：向量 (vector)、队列 (queue) 、栈 (stack)、集合 (set) 等。

**算法（函数）模板**
算法用于对容器中的数据元素进行一些常用**操作**，如：排序、统计等。

**迭代器类模板**
- 迭代器实现了*抽象的指针*功能，它们指向容器中的数据元素，用于对容器中的数据元素进行遍历和访问。
- *迭代器是容器和算法之间的桥梁*：传给算法的不是容器，而是指向容器中元素的迭代器，算法通过迭代器实现对容器中数据元素的访问。这样使得算法与容器保持独立，从而提高算法的通用性。

例子：
```C++
#include <iostream>
#include <vector>
#include <algorithm>
#include <numeric>
using namespace std;

void display(int x) { cout << ' ' << x; return; }
int main()
{
    vector<int> v; //创建容器对象v，元素类型为int
    int x;
    cin >> x;
    while (x > 0) //生成容器v中的元素
    {
        v.push_back(x); //往容器v中增加一个元素
        cin >> x;
    }
    //利用算法max_element计算并输出容器v中的最大元素
    cout << "Max = " << *max_element(v.begin(),v.end()) << endl;
    //利用算法accumulate计算并输出容器v中所有元素的和
    cout << "Sum = " << accumulate(v.begin(),v.end(),0) << endl;
    //利用算法sort对容器v中的元素进行排序
    sort(v.begin(),v.end()); 
    //利用算法for_each输出排序结果
    cout << "Sorted result is:\n";
    for_each(v.begin(),v.end(),display);
    cout << '\n';
    return 0;
}
```