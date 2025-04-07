`map`就是从键（key）到值（value）的映射。因为重载了[ ]运算符，map像是数组的“高级版”。例如可以用一个`map<string，int>month_name`来表示“月份名字到月份编号”的映射， 然后用`month_name["July"]=7`这样的方式来赋值

#### 初始化
```C++
# include <map>
map<string, int> m= {"A", 10}
```

#### 方法
```C++
m.insert()    //插入一个数，插入的数是一个pair
m.erase()     //（1）输入是pair
              //（2）输入一个迭代器，删除这个迭代器
s.find()      //查找一个数
s.lower_bound(x) //返回大于等于x的最小的数的迭代器
s.upper_bound(x) //返回大于x的最小的数的迭代器
```

#### 映射 [ ]







例子：
```C++
#include <iostream>
#include <map>
#include <string>
using namespace std;
int main()
{
    map<string,int> phone_book; // 创建一个map类容器，用于存储电话号码簿
    
    // 创建电话簿
    phone_book["wang"] = 12345678; // 通过[]操作和关键字往容器中加入元素
    phone_book["li"] = 87654321;
    phone_book["zhang"] = 56781234;
    // ......  还可以添加更多的信息
    // 输出电话号码簿
    cout << "电话号码簿的信息如下：\n";
    for (pair<string, int> item: phone_book) 
    // C++11中引入的enhanced-for loop
        cout << item.first << ": " << item.second << endl; 
    // 输出元素的姓名和电话号码

    // 查找某个人的电话号码
    string name;
    cout << "请输入要查询号码的姓名：";
    cin >> name;
    map<string,int>::const_iterator it; // 创建一个不能修改所指向的元素的迭代器
    it = phone_book.find(name); // 查找关键字为name的容器元素
    if (it == phone_book.end()) // 判断是否找到
        cout << name << ": not found\n"; // 未找到
    else
        cout << it->first << ": " << it->second << endl; // 找到
    return 0;
}
```




