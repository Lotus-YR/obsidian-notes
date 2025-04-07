#### 初始化
```C++
#include <string>

string a = "ac";
```

#### 方法
```C++
a.substr(m, n)                //求子串 下标从m到n的子串
a.substr(m)                   //下标m到最后一个字符

a.c_str()                                //返回字符串组的头指针
a.push_back(char)                        //尾插一个字符
a.insert(pos, char)                      //插入字符串
a.insert(pos, str, m, n)                 //字符串str从下标m开始的3个字符，插入原串下标pos前

a.empty()         //判断a是否为空，为空返回true

a.size()
a.length()         //返回字符个数 !!注意他们的类型都是 注：std::string 的成员函数 length() 的返回值类型为 unsigned 类型，因此当 s.length() < t.length() 时，二者相减会得到一个很大的数产生运行时错误，所以相减之前需要先将二者强制类型转换为 int 类型

a.clear()          //清空字符串
```

#### 支持比较运算



