# 第一部分 基础知识
## 第一章 起步


## 第二章 变量和简单数据类型
### 变量
```Python
 message = "yang yang is a silly baby, sb in short"
 print(message)
```

### 字符串
```Python
first_name = "ada"
last_name = "lovelace"
full_name = f"{first_name} {last_name}"
message = f"Hello,{full_name.title()}!"
print(message)
# 输出：Hello, Ada Lovelace!

print("Languages:\n\tPython\n\tC\n\tJavaScript")

favorite_language = ' python '
print(favorite_language+"hhhh")
print(favorite_language.rstrip()+"hhhh")
favorite_language = favorite_language.rstrip()
print(favorite_language)
favorite_language = favorite_language.lstrip()
print(favorite_language)
```

### 数
```Python
print(4/2)

universe_age = 14_000_000_000
print(universe_age)

x, y, z = 0, 0, 0
print(x)
print(y)
print(z)

MAX_CONNECTIONS = 5000

#practice:
print(3 + 5)
print(10 - 2)
print(2 * 4)
print(80 / 10)

favorite_number = 2 ** 3
message = f"my favorite number is {favorite_number}."
print(message)
```

### Python之禅
The Zen of Python, by Tim Peters

Beautiful is better than ugly.

Explicit is better than implicit.

Simple is better than complex.

Complex is better than complicated.

Flat is better than nested.

Sparse is better than dense.

Readability counts.

Now is better than never.

Although never is often better than *right* now.

If the implementation is hard to explain, it's a bad idea.

If the implementation is easy to explain, it may be a good idea.

Namespaces are one honking great idea -- let's do more of those!

## 第三章 列表简介
### 列表是什么
在Python中，用方括号（[]）表示列表，并用逗号分隔其中的元素。下面是一个简单的列表示例，其中包含几种自行车：
bicycles = ['trek', 'cannondale', 'redline', 'specialized']

要访问列表元素，可指出列表的名称，再指出元素的索引，并将后者放在方括号内。
（索引从0开始，可使用负数）

### 修改、添加和删除元素
- 修改
- 添加
	1. append()
	2. insert()
```Python
bicycles.append('honda')
bicycles.insert(1,'ducati')
```
- 删除
	1. 删除语句：del
	2. pop()：默认为删除最后一个元素，也可删除指定位置的元素，元素删除后可再利用
	3. remove()：删除确定的值，不知道位置
```
del bicycles[1]
popped_bicycles = bicycles.pop()
popped_bicycles = bicycles.pop(2)
bicycles.remove('trek')
```

练习：
```Python
name_list = ['yy', 'yxl', 'rbt']  
print(name_list)  
message = f"I will invite {name_list[0]}, {name_list[1]}, and {name_list[2]} to join dinner"print(message)  
  
print("rbt can not join the dinner")  
name_list.remove('rbt')  
name_list.append('marco')  
message = f"I will invite {name_list[0]}, {name_list[1]}, and {name_list[2]} to join dinner"print(message)  
  
print("You have find a bigger table, so you can invite more person")  
name_list.insert(0,'mats')  
name_list.insert(2,'julia')  
name_list.append('nico')  
message = f"I will invite {name_list[0]}, {name_list[1]}, {name_list[2]}, {name_list[3]}, {name_list[4]} and {name_list[5]} to join dinner"print(message)  
  
print("Sorry to tell you that your table can not be get on time, so you can only invite two people")  
while len(name_list) > 2 :  
    message0 = f"Sorry {name_list.pop()}, the dinner is canceled."  
    print(message0)  
  
message = f"I will invite {name_list[0]}, and {name_list[1]} to join dinner"print(message)  
  
del name_list[1]  
del name_list[0]  
  
print(name_list)
```
### 组织列表
- sort()方法永久排序：默认按字母排序，无法恢复
```Python
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort()
cars.sort(reverse = True)
```
- sorted()方法临时排序：保留原来顺序，以特定顺序呈现
```Python
print(sorted(cars))
print(sorted(cars,reverse = True))
```
- 倒着打印列表：reverse()
```Python
print(cars.reverse())
```
- 确定列表长度：len()
```Python
print(len(cars))
```

练习：
```Python
location = ['North Pole', 'German', 'England', 'West of SC', 'QingCheng Mount']  
print(location)  
  
print(sorted(location))  
print(sorted(location, reverse=True))  
  
location.sort()  
print(location)  
location.sort(reverse=True)  
print(location)
```
### 使用列表时避免索引错误
索引错误意味着Python在指定索引处找不到元素。


## 第四章 操作列表
### 遍历整个列表
```Python
magicians = ['alica', 'david', 'carolina']
for magician in magicians:
	print(magician)
```
使用单数和复数式名称，可帮助你判断代码段处理的是单个列表元素还是整个列表

```Python
magicians = ['alica', 'david', 'carolina']
for magician in magicians:
	print(f"{magician.title(), that was a great trick!")
```

### 避免缩进错误
- 忘记缩进
- 不必要的缩进
- 循环后不必要的缩进
- 遗漏冒号

### 创建数值列表
函数range() 
```Python
for value in range(1,5):
	print(value)

## range()可作为list()的参数
numbers = list(range(1,6))

## 从2开始，不断加2
even_numbers = list(range(2,11,2))
```

使用函数range() 几乎能够创建任何需要的数集
 ```Python
 ## 将前10个数的平方数加入列表中
squares = []
for value in range(1, 11):
     square = value ** 2
    squares.append(square)
print(squares)

## 更简洁版
squares = []
for value in range(1,11):
	squares.append(value**2)
	print(squares)

## 处理数字列表的函数
digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
min(digits)
max(digits)
sum(digits)
```

- 列表解析
将for循环和创建新元素的代码合并成一行，并自动附加新元素
```Python
squares = [value**2 for value in range(1,11)]
```




### 使用列表的一部分





### 元组





### 设置代码格式







## 第五章 if语句

## 第六章 字典


## 第七章 用户输入和while循环


## 第八章 函数



## 第九章 类



## 第十章 文件和异常


## 第十一章 测试代码



# 第二部分 项目







