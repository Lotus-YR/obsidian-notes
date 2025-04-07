# 1 Structure of Relational Databases
### Relation Schema and Instance
- attributes 属性
- relation schema  关系模式 
	instructor = (ID, name, dept_name, salary)
- tuple 元组
- domain 域（属性的取值集合）
- null 空值

### Relations are Unordered
order of tuples is irrelevant

# 2 Database Schema
database schema: the logical design of the database
database instance: a snapshot of the data in the database at a given instant in time

relation -- a variable
relation schema -- type definition


# 3 Key
- **superkey**: a set of one or more attributes that, taken collectively, allow us to identify uniquely a tuple in the relation
	if K is a superkey, then so is any superset of K
- **candidate keys**: minimal superkeys
	{ID, name} ×
	{name, dept_name} {ID} √
- **primary key**: chosen by the database designer as the principal means of identifying tuples within a relation
	referred to as **primary key constraints**
- **foreign-key constraint**: 一个关系中的值必须出现在另一个关系中
	被参照表中的值必须是主码
	参照表属性集被称为**外码（foreign key）**，可以取空值
	e.g. instructor中的dept_name属性就是从instructor引用（参照）department的外码
- referential integrity constraint（引用完整性约束）

# 4 Schema Diagrams
![[Pasted image 20240911090040.png|400]]

实体表 联系表
双箭头：引用完整性约束
	被参照的值（time_slot_id）不是主码，但是外码（section的time_slot_id）取值和它有关，可能对应多个取值（多个时间片） 触发器解决......

# 5 Relational Query Languages
##### Pure Language
- 关系代数！（掌握）
- 元组关系演算
- 域关系演算
(they are equivalent in computing power)

##### 关系代数基本运算
- 选择select
- 投影project
- 并union
- 差set difference
- 笛卡尔积Cartesian product
- 更名rename

# The Relational Algebra
### The Select Operation
![[Pasted image 20240911094734.png|300]]

选择操作逐行进行 单目运算
not 单次查询...... 

### The Project Operation
![[Pasted image 20240911101637.png|300]]
投影操作逐列进行
降维

### Composition of Relational Operations
$Π_{name}(σ_{dept_name=“Physics”} (instructor))$

### The Cartesian-Product Operation
![[Pasted image 20240911103227.png|300]]

### The Join Operation
$σ_{instructor.ID=teaches.ID}(instructor × teaches)$
The **join** operation is defined as:
![[Pasted image 20240911103620.png|120]]
### Set Operations
并交叉
整体上进行

![[Pasted image 20240911105402.png|300]]


### The Assignment Operation
赋值
![[Pasted image 20240911105731.png|300]]

### The Rename Operation
自表连接 通过更名实现


### Equivalent Queries



