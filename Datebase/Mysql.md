# Mysql

SQL分类：结构化的查询语言（Structured Query Language）

- `DQL`:查询语言---》select
  - data query language
- `DMl`：操作语言增、删、改 ---》insert 、update 、delete
  - data mainipulation language
- TPL：事务处理语言，对事物进行处理---》begin transaction 、 commit 、 rollback
  - transaction processing language
- DCL：数据控制语言，进行授权与权限回收---》grant 、revoke
  - data control language
- DDL：数据定义语言，进行数据库、表的管理等---》create 、drop
  - data definition language 
- CCL：指针控制语言，通过控制指针完成表的操作---》declare cursor
  - cursor control language

---

## 1. 连接

- 命令连接Mysql

  - 前置

    - 确定mysql的IP地址

      - 通过ifconfig确认

    - 确认mysql服务是否开启

      - ```shell
        sudo netstat -anptu ｜ grep 3306
        ```

- 连接命令

  ```shell
  mysql -h数据库IP -P端口号 -u数据库登陆用户名 -p数据库登陆密码
  ```

  - -h 不加时表示本机
  - -P 不加时表示默认3306端口

---

|    时间     |       周日        |  周一、二、三、四   |   周五    |      周六      |
| :---------: | :---------------: | :-----------------: | :-------: | :------------: |
|  8:00-8:20  |                   |      起床+洗漱      |           |                |
|  8:25-9:40  |                   |  学习技术之外+英语  |           |                |
| 9:40-10:10  |     起+洗+吃      |      通勤+早饭      |           |    起+洗+吃    |
| 10:20-11:52 |     许倩+学习     |     技术或工作      |           |   许倩+学习    |
| 12:00-13:20 |  许倩+学习+吃饭   |    吃饭+自由安排    |           | 许倩+学习+吃饭 |
| 13:25-14:00 |     许倩+午觉     |        午觉         |           |   许倩+午觉    |
| 14:05-17:52 |  许倩+午觉+学习   |   工作或技术+摸鱼   |           |    自由安排    |
| 18:00-19:00 |  许倩+溜达+吃饭   |    吃饭+自由安排    |           |    自由安排    |
| 19:05-20:20 |  许倩+溜达+学习   |     技术或工作      |           |    自由安排    |
| 20:30-21:30 | 许倩+学习技术之外 |  健身房+技术或工作  |           |    自由安排    |
| 21:40-22:30 |     英语学习      |  技术或工作-->许倩  | 自由安排  | 许倩+洗漱+学习 |
| 23:30-00:30 |       许倩        | 许倩+洗漱+收拾+娱乐 | 自由安排  |    英语学习    |
| 00:30-1:00  |       许倩        |      总结+学习      | 自由安排  |      许倩      |
|    1:00     |     许倩+睡觉     |      许倩+睡觉      | 许倩+睡觉 |   许倩+睡觉    |

目标规划

---

## 2. 数据约束

## 3. sql备份和还原

## 4. 命令操作数据库和表

- 查看所有数据库：show databases;
- 使用数据库：use 数据库名;
- 查看当前使用的数据库：select database();
- 创建数据库：create database 数据库名 charset=utf8;
- 删除数据库：drop database 数据库名;





- 查看当前数据库中所有的表：show tables;
- 查看表结构：desc 表名;
  - 查看表的创建与聚：show create table 表名;

---

- 增
  - 主键自增的字段可以用0或者null代替
    - values(0,value)
    - values(null, value)
  - insert into 表名 values(value,value,value);---->全部字段
  - insert into 表名(字段1，字段2) values(value,value);---->部分字段
  - insert into 表名 values(value,value,value),(value1,value1,value1);---->插入多行数据，全部字段
  - insert into 表名(字段1,字段2) values(value,value),(value1,value1);---->插入多行数据，部分字段

- 查
  - select * from 表名
  - select 字段1，字段2 from 表名



- 改
  - update 表名 set 字段名1=值1,字段2=值2...where 条件
    - update student set name = "无敌",age = 12 where id = 5
- 删
  - delete from 表名 where 条件(物理删除对应的数据)
    - 工作中一般使用逻辑删除，即不删除数据行，隐藏改变数据状态
  - other ways
    - truncate table 表名 ---》清楚表里面所有数据，但是保留表结构，自增字段的值从1开始
    - drop table 表名 ---〉删除表，包括数据和结构
  - delete from student where id = 6;







- 分页

  - select * from 表名 limit 起点（从0开始，代表第几页），每一页显示几行

    - select * from student limt 0，5-->取从第1到第5条数据

    - select * from student limt 1，5-->取从2-6条数据

    - select * from student limt 10，5-->取从11-15条数据

  - select * from student limit (n-1)*m,m

    - n-->表示显示第几页的数据
    -  
    - m-->表示每页显示多少条数据
    - m = 3，每页显示3条数据

```sql
creat table grade(
  name varchar(10),
  `class` varchar(8),
  `st` varchar(56),
  `grade` decimal(4,1)
);
drop table grade;
insert into student values
("zhangsan","yiban","yuwen",89.5),
("zhangsan","yiban","yuwen",89.5)
update from student set grade = 97 where name = "lisi"
delete from student where name = "wangwu"
select * from student where name like "__"
select * from student where name like "百%" and age > 20
select * from student where id like %1
select count(name) /count(*) from student
select max(age) from student 
select min(age) from student where class = "1ban"
select sum(age) from student where hometown = "beijing"
select avg(age) from student where sex = "女"
```

---

## 5. 连接查询

### 5.1 内连接

- 连接表时，取的是两个表中都存在的数据（取交集）

- 语法格式：

  - ```sql
    select * from 表1
    	inner join 表2 on 表1.列 = 表2.列
    ```

  - ```sql
    select * from 表1,表2 where 表1.列 = 表2.列
    ```
  
  - ```sql
    select * from 表1
    	inner join 表2 on 表1.列 = 表2.列
    	inner join 表3 on 表1.列 = 表3.列 where 表3.name = '张三'
    ```
  
  - 

### 5.2 左连接

- 连接两表时，取的是左表中特有的数据，对于右表中不存在的数据，用null来填充

- 语法格式：

  - ```sql
    select * from 表1
    left join 表2 on 表1.列 = 表2.列
    ```

  - ```sql
    select * from 表1 
    left join 表2 on 表1.列 = 表2.列
    left join 表3 on 表3.列 = 表2.列
    ```

### 5.3 右连接



## 6. 自关联

```sql
select * from table t1 inner join table t2 on t1.列 = t2.列
inner join table t3 on  t3.列 = t2.列 where 条件
```



## 7. 子查询

- 子查询辅助主查询，要么充当条件，要么充当数据源

- 子查询是一条完整的 、可单独执行的select查询语句

- 标量子查询：where = 

- 列子查询：where in

- 行子查询：where（值1，值2）= 

- =any和in等价

- ```sql
  select score from scores where studentno = any(子)
  ```

- some：是any的别称，很少用

- ```sql
  select score from scores where studentno = some(子)
  ```

- !\=all 和not in 等价

- ```sql
  select score from scores where studentno not in (子)
  
  select score from scores where studentno ! =  all(子)
  ```



- 充当数据源

- ```sql
  select * from scores as sc inner join (
  select studentno from students where age bwteen 18 and 20
  ) as st on st.studentno = sc.studentno;
  
  
  
  select studentno from students where age between 18 and 20 ;
  select score from scores where studentno = (select studentno from students where age between 18 and 20 );
  ```

- 

## 8. 查询演练

```sql
select stu.name,sc.courseno,sc.scoure from students stu inner join scores sc on sc.studentno = stu.studentno where stu.name = '王昭君'
```









