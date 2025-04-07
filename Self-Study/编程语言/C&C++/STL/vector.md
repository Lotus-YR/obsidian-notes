#### 初始化：
```C++
#include<iostream>
#include<vector>                   //头文件
using namespace std;
int main () {
	//几种初始化的方法
    vector<int> a;//定义一个vector  未初始化 输出》 0
    
    vector<int> a(3);//定义一个长度为3的vector  未初始化 输出》0 0 0
    
    vector<int> a(10, 3); //定义一个长度为10，且每个数赋值为3
    
	//将向量b中从下标0 1 2（共三个）的元素赋值给a，a的类型为int型
	//它的初始化不和数组一样 
	vector<int>a(b.begin(),b.begin+3);

	//从数组中获得初值
	int b[7]={1,2,3,4,5,6,7};
	vector<int> a(b,b+7）;
	
    for(auto x : a) {//遍历输出 
        cout << x << " ";
    }
    return 0;
}

```

#### 方法：
```C++
a.size()           //返回元素个数
a.resize()         //改变大小
a.empty()          //判断a是否为空，空则返回true
a.front()          //当a存在时返回a的第一个元素
a.back()           //返回a的最后一个元素
a.clear()          //清空a中的元素
a.pop_back()       //删除a向量的最后一个元素
a.push_back()      //在a的最后一个向量中插入一个元素
a.begin()          //vector的第0个数
a.end()            //vector的最后一个数的后面一个数
a.erase(p)         //从a中删除迭代器p指定的元素，p必须指向c中的一个真实元素，不能是最后一个元素
a.reverse(a.begin(),a.end())  //倒置
```

#### 支持比较运算：
按字典序比较

#### 遍历方法：
```C++
int main () {
    vector<int> a;
    for (int i = 0; i < 10; i ++) {
        a.push_back(i);
    }
    
    //三种遍历vector的方法
    for (int i = 0; i < a.size(); i ++) {
        cout << a[i] << ' ';
    }
    cout << endl;

    for (auto i = a.begin(); i != a.end(); i ++) {
        cout << *i << ' ';
    }
    cout << endl;

    //C++11的新语法
    for (auto x : a) {
        cout << x << ' ';
    }
    cout << endl;  
    return 0;
}

```

