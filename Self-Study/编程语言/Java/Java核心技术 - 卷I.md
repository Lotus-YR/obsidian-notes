### 第1章 Java程序设计概述




### 第2章 Java程序设计环境


### 第3章 Java的基本程序设计结构
#### 一个简单的Java应用程序
```java
public class FirstSample{
	public static void main(String[] args)
	{
		System.out.println("We will not use 'Hello,Wordl!");
	}
}
```

public 访问修饰符 控制程序的其他部分对这段代码的访问级别
class 表面Java程序中的全部内容都包含在类中
类名 必须以字母开头
源代码的文件名必须与公共类的名字相同

Java虚拟机将从指定类中的main方法开始执行
main方法必须声明为public
每个Java应用程序都必须有一个main方法



#### 数组
for each 循环
```java
for (int element : a)
	System.out.println(element);
```

### 第4章 对象与类
#### 面向对象程序设计概述
类之间常见的关系：
- 依赖 (uses-a)
- 聚合 (has-a)
- 继承 (is-a)

#### 使用预定义类
？？


#### 用户自定义类
```java
class Employee {
	public Employee (String n, double s, int year, int month, int day){
		name = n;
		salary = s;
		hireDay = LocalDate.of(year,month,day);
	}

	public String getName(){
		return name;
	}

	public double getSalary(){
		return salary;
	}

	public LocalDate getHireDay(){
		return hireDay;
	}

	public void raiseSalary(double byPercent){
		double raise = salary * byPercent / 100;
		salary += raise;
	}
}
```

构造器
- 与类同名
- 每个类可以有一个以上的构造器
- 构造器没有返回值
- 构造器伴随着new操作符的执行被调用

隐式参数
显式参数




final实例域

#### 静态域与静态方法


工厂方法


#### 方法参数


#### 对象构造




#### 包




#### 类路径




#### 文档注释



#### 类设计技巧


### 第5章 继承


### 第6章 接口、lambda表达式与内部类
#### 接口
###### 接口的概念
接口代码：
```java
public interface Comparable{
	int compareTo(Object other);
}
```

让类实现接口，步骤：
1. 将类声明为实现给定的接口，使用关键字 implements
2. 对接口中的所有方法进行定义
```java
class Empliyee implements Comparable<Employee>{
	public int compareTo(Employee other){
		return Double.compare(salary, other.salary);
	}
	......
}
```

```java
//EmployeeSortTest.java
package interfaces;

import java.util.*;

public class EmployeeSortTest{
	publc static void main (String[] args){
		Employee[] staff = new Employee[3];

		staff[0] = new Employee("Harry Hacker", 35000);
		staff[1] = new Employee("Carl Cracker", 75000);

		Arrays.sort(staff);
	}
}

//Employee.java
package interfaces;

public class Employee implements Comparable<Employee>{
	private String name;
	private double salary;

	public Employee(String name, double salary){
		this.name = name;
		this.salary = salary;
	}
	......

	public int compareTo(Employee other){
		return Double.compare(salary, other.salary);
	}
}
```

###### 接口的特性
接口变量必须引用实现了接口的类对象
```kotlin
Comparable x;
x = new Employee(...);
```

###### 接口与抽象类
Java不支持多重继承

###### 静态方法


###### 默认方法


#### 接口示例
###### 接口与回调



#### lambda表达式


#### 内部类



#### 代理



### 第8章 泛型程序设计
#### 为什么要使用泛型程序设计




#### 定义简单泛型类


#### 泛型方法



#### 类型变量的限定



#### 泛型代码和虚拟机






### 第12章 Swing用户界面组件
#### Swing和MVC设计模式

几种模式：
- 容器和组件是组合模式
- 带滚动条的面板是装饰器模式
- 布局管理器是策略模式


MVC模式
- 模型model：存储内容
- 视图view：显示内容
- 控制器controller：处理用户输入







