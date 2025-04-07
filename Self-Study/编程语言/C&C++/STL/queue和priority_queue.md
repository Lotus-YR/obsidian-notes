#### 初始化
```C++
# include<queue>

queue <int> q;                //定义一个名为q队列

priority_queue <int> q;       //默认是大根堆
priority_queue <int, vector <int>, greater<int>> q;    //小根堆
```

#### 方法
```C++
//共同函数
q.size()
q.empty()
q.push()       //队尾插入元素
q.pop()        //队列：从队头弹出    优先队列：弹出堆顶元素

//区别
//队列：
q.front()          //返回队头元素
q.back()           //返回队尾元素
//优先队列：
q.top()            //返回堆顶元素

//没有clear函数 清空方法就是重新初始化
q = queue <int> ();
```




