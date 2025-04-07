# 第1章 JavaScript简史
### 1.1 JavaScript的起源
JavaScript是一种脚本语言，通常只能通过Web浏览器去完成一些操作而不能像普通意义上的程序那样独立运行。

### 1.2 DOM
DOM是一套对文档的内容进行抽象和概念化的方法。

JavaScript的早期版本向程序员提供了查询和操控Web文档某些实际内容（主要是图像和表单）的手段。

### 1.3 浏览器战争
DHTML是“Dynamic HTML”（动态HTML）的简称。DHTML并不是一项新技术，而是描述HTML、CSS和JavaScript技术组合的术语。

### 1.4 制定标准
W3C推出的标准化DOM却可以让**任何一种** 程序设计语言对使用**任何一种** 标记语言编写出来的**任何一份** 文档进行操控。

DOM是一种API（应用编程接口）。
W3C对DOM的定义是：“一个与系统平台和编程语言无关的接口，程序和脚本可以通过这个接口动态地访问和修改文档的内容、结构和样式。”


# 第2章 JavaScript语法
### 2.1 准备工作
用JavaScript编写的代码必须通HTML/XHTML文档才能执行

方法：
- JavaScript代码放到 < head > 的< script >中
- 单独把JavaScript代码存为.js文件

程序设计语言分为解释型和编译型两大类。Java或C++等语言需要一个**编译器**（compiler）。
解释型程序设计语言不需要编译器——它们仅需要解释器。

### 2.2 语法
##### 语句
用JavaScript编写的脚本，与其他语言编写出来的脚本一样，都由一系列指令构成，这些指令叫做**语句** （statement）。

各条语句放在不同行或用分号分隔开
（建议都加分号）

##### 注释
```JavaScript
//       单行

/*  多行内容
	可以使用   */
	
<!--     “-->”视为注释的一部分
```

##### 变量
变量：会变化的量，变量名中不允许包含空格或标点符号（$例外）
赋值：把值存入变量的操作
声明：赋值操作自动声明（提前声明变量是好习惯）

```JavaScript
var my_mood = "happy";
var myMood = "sad";
```

##### 数据类型
JavaScript不需要进行类型声明，因此它是一种**弱类型** （weakly typed）语言。

1. 字符串
	字符串必须包在引号里
	可以用反斜线对引号进行转义
2. 数值
	不用限定整数还是浮点数
3. 布尔值

##### 数组
可以用Array声明数组（同时指定个数）
```JavaScript
	var beatles = Array(4);
	/* var beatles = Array(); 
	     不确定个数也可以声明   */

	//填充
	beatles[0] = "John";

	//声明同时填充
	var beatles = Array("John", "Paul", "George", "Ringo")
    var beatles = [ "John", "Paul", "George", "Ringo" ];

	//关联数组：用字符串代替下标数字
	var lennon = Array();
	lennon["name"] = "John";
	lennon["year"] = 1940;
	lennon["living"] = false;
	```

##### 对象
```JavaScript
var lennon = Object();
lennon.name = "John";
lennon.year = 1940;
lennon.living = false;
```

创建对象：
```JavaScript
var lennon = { name:"John", year:1940, living:false };
```

### 2.3 操作
##### 算术操作符
如果把字符串和数值拼接在一起，其结果将是一个更长的字符串；但如果用同样的操作符来“拼接”两个数值，其结果将是那两个数值的算术和

### 2.4 条件语句
同C
```JavaScript
if () {
	...
} else {
	...
}
```

### 2.5 循环语句
```JavaScript
while ( ) {
	...
};

do {
	...
}while ( );

for( ; ; ) {
	...
};
```

### 2.6 函数
定义函数：
```JavaScript
function name(arguments) {
  statements;
}
```

##### 变量的作用域
全局变量
局部变量

### 2.7 对象
对象是自包含的数据集合，包含在对象里的数据可以通过两种形式访问——**属性** （property）和**方法** （method）

为了使用`Person` 对象来描述一个特定的人，需要创建一个`Person` 对象的**实例** （instance）。实例是对象的具体个体。
```JavaScript
var jeremy = new Person;
```

用户定义对象

##### 内建对象
- Array
```JavaScript
var beatles = new Array();
```
- Math
- Date

##### 宿主对象
由浏览器提供的预定义对象
- Form
- Image
- Element


# 第3章 DOM
### 3.1 文档：DOM中的“D”
document
网页文档

### 3.2 对象：DOM中的“O”
对象是一种自足的数据集合

可分为三种类型：
- 用户定义对象
- 内建对象（native object）
	内建在JavaScript语言里的对象，如Array、Math和Date等
- 宿主对象（host object）
	浏览器提供的对象

**window对象**对应着浏览器窗口本身，这个对象的属性和方法通常称为BOM，提供了window.open和window.blur等方法
**document对象**的主要功能就是处理网页内容

### 3.3 模型：DOM中的“M”
model map
某种事物的表现形式

DOM把一份文档表示为一棵树，家谱树（节点树）
![[Pasted image 20240912110436.png|300]]

### 3.4 节点
节点（node）表示网络中的一个连接点

##### 元素节点
DOM的原子是元素节点（element node）

< body> < p> < ul>....

标签的名字就是元素的名字
< html > 根元素， 没有被包含在其他元素里

##### 文本节点
元素包含着的文本就是一个文本节点
文本节点总是被包含在元素节点的内部

##### 属性节点
属性节点用来对元素做出更具体的描述
所有的属性都被元素包含

![[Pasted image 20240912111330.png|300]]

##### CSS
通过CSS告诉浏览器如何显示一份文档的内容

声明可以嵌入文档< head>的< style>之间，也可以放在另外一个文件里

继承（inheritance），CSS技术中强大的功能
CSS也把文档内容看作一棵树，节点树上的各个元素将继承其父元素的样式属性

1. class属性
2. id属性

##### 获取元素
三种DOM方法可获取元素节点（id, tag, class）：
1. getElementById
	document对象特有的函数
	document.getElementById("purchases")
2. getElementsByTagName
	返回一个对象数组
	element.getElementsByTagName(tag)
	```JavaScript
	var items = document.getElementsByTagName("li");
	for (var i=0; i < items.length; i++) {
	    alert(typeof items[i]);
	}

//id属性值为purchase的元素包含着多少列表项
	var shopping = document.getElementById("purchases");
	var items = shopping.getElementsByTagName("*");
	```
3. bgetElementsByClassName
	getElementsByClassName(class)





