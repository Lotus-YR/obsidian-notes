# Join Expressions



# View
### View Definition
create view v（视图名称） as <查询表达式>

可用视图定义视图
视图和积分表在使用时没区别
视图，虚积分表（就像函数....用的时候调用 计算出结果

物化视图（存储视图关系，让使用该视图的查询可以通过使用预计算的视图结果来更快的运行，不用重新计算
数据改变需要更新

视图更新

JBC

# Transaction
事务，由查询或更新语句的序列组成

begin;
....
commit; / rollback;


# Integrity Constraint
not null
primary key
unique
check(谓词)

foreign key

check单表约束

assertion断言


# Built-in Data Types in SQL
date 年月日
time 时分秒
timestamp
interval

### Large-Object Types
clob
blob

### User-Defined Types


# Index Creation



# Authorization
读取数据
插入数据
更新数据
插入数据

### Grant & Revoke


### Roles


