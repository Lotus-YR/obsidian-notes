# 第1章 概述
### 1.1 CSS世界的”世界观“
层叠天星，幻化有形，50%，变！
类名之石，test为名，为我选择，出！

CSS世界 平行世界
Windows、OS、iOS、Android

### 1.2 世界都是创造出来的
CSS(Cascading Style Sheets, 层叠样式表)
CSS世界的诞生就是为图文信息展示服务的

### 1.3 CSS完胜SVG的武器——流
##### 何为”流“
文档流
流实际是CSS世界中的一种基本的定位和布局机制（类似”水流“，HTML的两个基石< div>< span>类似容器）
可以实现自动换行

##### 流是如何影响整个CSS世界的
1. 擒贼先擒王。HTML默认的表现符合流，则可以控制。
2. 特殊布局与流的破坏。
3. 流向的改变。


##### 什么是流体布局
指利用元素“流”的特性实现的各类布局效果

### 1.4 CSS世界的开启从IE8开始
本书指CSS2.1

### 1.5 table自己的世界
table出现的比CSS早


### 1.6 CSS新世界——CSS3
1. 布局更为丰富
2. 视觉表现长足进步

# 第2章 需提前了解的术语和概念
### 2.1 务必了解的CSS世界的专业术语
```css
.vocabulary {
	height: 99px;
	color: transparent;
}
```
1. 属性
	height、color
2. 值
	99px
3. 关键字
	transparent
4. 变量
5. 长度单位
	< lnumber>+长度单位 = < length>
	分为：相对长度单位（em, ex, vh, vw...）、绝对长度单位（px, pt, cm, mm, pc...）
6. 功能符
	值以函数的形式指定 rgba(0, 0, 0, .5)
7. 属性值
	值+关键字+功能符
8. 声明
	属性名+属性值
9. 声明块
	{ }包裹的一系列声明
10. 规则或规则集
	选择器+声明块
11. 选择器
	- 类选择器 “.”
	- ID选择器 ”#“
	- 属性选择器 ”[ ]”  e.g. [title="xxxx"]{ }
	- 伪类选择器 “:“
	- 伪元素选择器 ”::“
12. 关系选择器
	- 后代选择器
	- 相邻后代选择器 子选择器 ”>“
	- 兄弟选择器 ”~“
	- 相邻兄弟选择器 ”+“
13. @规则

### 2.2 了解CSS世界中的”未定义行为“
规范顾及不到的细枝末节的实现


# 第3章 流、元素与基本尺寸
标签分为块级元素和内联元素

### 3.1 块级元素
block-level element
常见的有：< div>, < li>, < table>等

块级元素 != display为block的元素 ？？？

块级元素可以配合clear属性来清除浮动带来的影响
```css
.clear:after {
	content: '';
	display: table; //或block, list-item
	clear: both;
}
```

使用block、table，不使用list-item：
1. 字符数量
2. 会出现不需要的项目符号
3. IE浏览器不支持伪元素的display值为list-item

##### 为什么list-item元素会出现项目符号
生成了一个附加的盒子，学名”标记盒子“，专门用来放圆点、数字这些项目符号

每个元素都有两个盒子，外在盒子和内在盒子
外在盒子负责元素是可以一行显示还是只能换行显示
内在盒子（**容器盒子**）负责宽高、内容呈现
	值为block的元素的盒子由外在的块级盒子和内在的块级容器盒子组成

##### display：inline-table的盒子是怎样组成的
和文字在一行中显示的表格
```css
.inline-table {
	display: inline-table;
	width: 128px;
	margin-left: 10px;
	border: 1px solid #cad5ed;
}
```

##### width/height作用在哪个盒子上
内在盒子，也就是容器盒子

### 3.2 width/height作用的具体细节
##### 深藏不露的width: auto
