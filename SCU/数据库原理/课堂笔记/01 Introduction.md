SQL 30分+
数据库设计 20分+
事务管理

40(期末考试) : 60(30平时成绩，30课程设计)

小组设计 两次汇报（国庆之后简单介绍项目内容和设计路线5min 学期末报告总结） 期末之前交设计报告

---

# Database-System Applications
- enterprise information
- manufacturing
- banking and finance
- universities
- airlines
- telecommunication
- web-based services
- document databases
- navigation systems

# Purpose of Database Systems
to solve those problems:
- data redundancy(冗余) and inconsistency(不一致)
- difficulty in accessing data
- data isolation
- integrity problems
- atomicity of updates(更新原子性) 
- concurrent access by multiple users(多用户并发访问) 关中断
- security problems


# View of Data
### Data Models
 a collection of tools for describing:
- data
- data relationships
- data semantics
- data constraints
##### model
- ==Relational model== 关系模型
- ==Entity-Relationship data model== (mainly for database design) 实体联系模型
- Object-base data models (Object-oriented and Object-relational)
- Semi-structured data model (XML)
- other older models
	Network model 网状模型
	Hierarchical model 层次模型

### Relational Model
![[Pasted image 20240904101925.png|300]]

堆存储
散列存储？？？

### Data Abstraction
- Physical level
- Logical level
- View level
![[Pasted image 20240904102149.png|300]]

### Instances and Schemas
- Logical Schema
- Physical Schema
- Instance
##### Physical Data Independence
物理数据独立性（软件和数据物理独立）
the ability to modify the physical schema without changing the logical schema

逻辑数据独立性？？？
# Database Languages
### Data Definition Language(DDL)
对模式进行操作

Specification notation for defining the database schema
```DDL
create table instructor (
		ID        char(5),
		name      varchar(20),  //变长串
		dept_name varchar(20),
		salary    numeric(8,2)
)
```

DDL compiler generates a set of table templates stored in a ==data dictionary==(数据字典)(用数据库来管理数据库)

Data dictionary contains metadata(元数据)
- database schema
- integrity constraints 完整性约束
- authorization 授权

### Data Manipulation Language(DML)
对实例进行操作

Language for *accessing and updating* the data organized by the appropriate data model, also known as ==query language==

##### two types of DML
- Procedural DML 过程化（顺序循环分支）what data are needed and how to get those data
- Declarative DML 申明式 what data are needed *without specifying how to get those data* (non-procedural DMLs)

### SQL
nonprocedural

图灵机等效语言？？？

### Database Access from Application Program


# Database Design



# Database Engine
### Storage Manager


### Query Processing Component
优化：
代数优化（启发式规则）
物理优化


### Transaction Management Component

# Database Architecture


# Database Users and Administractors


# History of Database Systems
啊吧啊吧
