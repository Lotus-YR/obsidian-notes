# 1 Overview of the SQL Query Language
SQL(structured query language)

The SQL language has several parts:
- **Data-definition language(DDL)**
	定义创建关系模式
- **Data-manipulation language(DML)**
	查、插、删、改，操作关系模式
- Integrity完整性
	语义约束
- View definition
	DDL
- Embedded SQL and dynamic SQL
- Authorization

# 2 SQL Data Definition
DDL allows specification of information about relation, including:
- The **schema** for each relation
- The **types of values** associated with each attribute
- The integrity **constraints**
- The set of indices to be maintained for each relation
- The security and authorization information for each relation
- The physical storage structure of each relation on disk

##### Basic Types
- char(n)
- varchar(n): cahracter varying
- int: integer
- smallint
- numeric(p,d): 格式化十进制数 ？？
- real, double, precision
- float

##### Basic Schema Definition
integrity constraints:
- primary key
- foreign key references
- not null

```sql
create table course
	(course_id    varchar(7),
	 title         varchar(50),
	 dept_name     varchar(20),
	 primary key(course_id),
	 foreign key(dept_name) references department);
```

insert: insert into
update
delete: delete from
drop
alter: alter r add A , alter r drop D

# 3 Basic Structure of SQL Queries
### Queries on a Single Relation
select xxxx from xxxx;
select xxxx from xxxx where xxxxx;

大小写不敏感

SQL命名规则：
全部小写，用下划线分割
dept_name
user_id
（Java使用驼峰式 DeptName UserId）

### Querise on Multiple Relations
first from
then where
and then select

![[Pasted image 20240918083952.png|400]]

等值连接

# 4 Additional Basic Operations
### Natural Join
```sql
select name, title
from instructor natural join teachers natural join course
```

危险：同名异义
```sql
select name, title
from instructor natural join teaches, course
where teachers.course_id = courese.course_id;

select name. titile;
from (instructor natural join teaches) join course using (course_id);
//?????
```


### The Rename Operation
无名列
select xxxx as xxxx from xxxxx where xxxx

from后通常省略（有些数据库不支持）

```sql
select name as instructor_name, course_id
from insturctor, teacher
where instructor.ID = teacher.ID;

select T.name, S.course_id
from instructor as T, teache as S
where T.ID = S.ID;
```

主码？外码？

### String Operations
like运算符实现模式匹配
- %： %字符匹配任意子串
-  _ ： _ 字符匹配任意一个字符

转义字符“\\”,”&“

```sql
select dept_name
from department
where building like '%Waston%';
```

### Attribute Specification in the Select Clause
select * from .... where ....

### Ordering the Display of Tuples
```sql
select name
from instructor
where dept_name = 'Physics'
order by name;
```

### Where-Clause Predicates
```sql
select name
from instructor
where salary between 9000 and 10000;

select name, course_id
from instructor, teaches
where (instructor.ID, dept_name) = (teaches.ID, 'Biology');
```

# 5 Set Operations




# 6 Null Values


# 7 Aggregate Functions
average: avg
minimum: min
maximun: max
total: sum
count: count

### Basic Aggregation


### Aggregation with Grouping


### The Having Clause


### Aggregation with Null and Boolean Values


# 8 Nested Subquerise
### Set Membership


### Set Comparison


### With Clause
????

### Complex Queries using "With Clause"


### Scalar Subquery


### Scalar without From


# Modification of the Database
