# mysql-final-test

2019-2020 mysql final test

姓名：```陈宗豪```

学号：```17061507```

说明1：考试为开卷，可以上网，自觉不要相互电话和QQ；

说明2：考试时间为：2020 年 4 月 10 日 8:10分-9:40分。

说明3：试题比较多，抓紧时间，超时提交的github commit不被接受。未避免完全超时提交，可以在做题过程中多 commit 几次。

说明4：结束后发邮件给 42225@hdu.edu.cn 标题为“MySQL期末考试,姓名+学号”，内容为github链接。


1 打印当前时间（例如 2020-04-07 13:41:42），写出SQL语句和结果
```sql
select now();
+---------------------+
| now()               |
+---------------------+
| 2020-04-10 08:00:30 |
+---------------------+
1 row in set (0.00 sec)
```
2 组合打印自己的姓名和学号

(例如 张三+123456 或者 zhangsan+123456 显示需包含加号)，写出SQL语句和结果
```sql
select concat('陈宗豪','+','17061507')'姓名+学号';
+-----------------+
| 姓名+学号       |
+-----------------+
| 陈宗豪+17061507 |
+-----------------+
1 row in set (0.00 sec)
```

3 建立如下表1和表2，写出建表语句和插入语句。

表1：其中deptno为主键
```
deptno, deptno,    loc
(10, "ACCOUNTING", "NEW YORK"),
(20, "RESEARCH", "DALLAS"),
(30, "SALES", "CHICAGO"),
(40, "OPERATIONS", "BOSTON")
```

表2：其中empno字段为主键
```
        empno, ename,    job,    MGR,   Hiredate,    sal,   comm, deptno
        (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
	(7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
	(7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
	(7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
	(7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
	(7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
	(7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
	(7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
	(7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
	(7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
	(7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
	(7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
``` 
```sql
create table biao1(
    -> deptno int primary key,
    -> dname varchar(20),
    -> loc varchar(40));
Query OK, 0 rows affected (0.05 sec)
desc biao1;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| deptno | int(11)     | NO   | PRI | NULL    |       |
| dname  | varchar(20) | YES  |     | NULL    |       |
| loc    | varchar(40) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
3 rows in set (0.01 sec)
insert into biao1 values
    -> (10, "ACCOUNTING", "NEW YORK"),
    -> (20, "RESEARCH", "DALLAS"),
    -> (30, "SALES", "CHICAGO"),
    -> (40, "OPERATIONS", "BOSTON");
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> select *from biao1;
+--------+------------+----------+
| deptno | dname      | loc      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+

create table biao2(
    -> empno int primary key,
    -> ename varchar(20),
    -> job varchar(40),
    -> MGR int,
    -> Hiredate varchar(40),
    -> sal float,
    -> comm float,
    -> deptno int);
Query OK, 0 rows affected (0.04 sec)

mysql> desc biao2;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| empno    | int(11)     | NO   | PRI | NULL    |       |
| ename    | varchar(20) | YES  |     | NULL    |       |
| job      | varchar(40) | YES  |     | NULL    |       |
| MGR      | int(11)     | YES  |     | NULL    |       |
| Hiredate | varchar(40) | YES  |     | NULL    |       |
| sal      | float       | YES  |     | NULL    |       |
| comm     | float       | YES  |     | NULL    |       |
| deptno   | int(11)     | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
8 rows in set (0.01 sec)

mysql> insert into biao2 values
    -> (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
    -> (7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
    ->  (7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
    -> (7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
    -> (7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
    -> (7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
    -> (7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
    -> (7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
    -> (7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
    -> (7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
    -> (7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10);
Query OK, 13 rows affected (0.01 sec)
Records: 13  Duplicates: 0  Warnings: 0

mysql>  select*from biao2;
+-------+--------+-----------+------+------------+------+------+--------+
| empno | ename  | job       | MGR  | Hiredate   | sal  | comm | deptno |
+-------+--------+-----------+------+------------+------+------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|  7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
+-------+--------+-----------+------+------------+------+------+--------+
13 rows in set (0.00 sec)
```
3.1 表2 中再插入一条记录：

`(你的学号，你的姓名或者拼音， “CLERK”, 7782, 你的生日,  NULL, NULL, 10)`
 
例如：`(12345,  "Zhangsan", "sTUDENT", 7782, "2000-03-12", NULL, NULL, 10)`
```sql
insert into biao2 values(17061507,'陈宗豪','sTUDENT',7782,'2000-03-12',null,null,10);
Query OK, 1 row affected (0.00 sec)
select*from biao2;
+----------+--------+-----------+------+------------+------+------+--------+
| empno    | ename  | job       | MGR  | Hiredate   | sal  | comm | deptno |
+----------+--------+-----------+------+------------+------+------+--------+
|     7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |     20 |
|     7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |     30 |
|     7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |     30 |
|     7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |     20 |
|     7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |     30 |
|     7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |     10 |
|     7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |     10 |
|     7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |     30 |
|     7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |     20 |
|     7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |     30 |
|     7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |     20 |
|     7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |     10 |
| 17061507 | 陈宗豪 | sTUDENT   | 7782 | 2000-03-12 | NULL | NULL |     10 |
+----------+--------+-----------+------+------------+------+------+--------+
14 rows in set (0.00 sec)
```

3.2 表中入职时间（Hiredate字段）最短的人。
```sql
 select ename from biao2 where Hiredate=(select max(hiredate) from biao2);
+--------+
| ename  |
+--------+
| 陈宗豪 |
+--------+
1 row in set (0.00 sec)
```

3.3 有几种职位（job字段）？在关系代数中，本操作是什么运算？
```sql
 select count(distinct(job)) from biao2;
+----------------------+
| count(distinct(job)) |
+----------------------+
|                    6 |
+----------------------+
1 row in set (0.00 sec)
简单数据查询运算
``` 
3.4 将 MILLER 的 comm 增加 100； 然后，找到 comm 比 MILLER 低的人；
```sql
update biao2
    -> set comm=100
    -> where ename='miller';
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> select*from biao2;
+----------+--------+-----------+------+------------+--------+------+--------+
| empno    | ename  | job       | MGR  | Hiredate   | salary | comm | deptno |
+----------+--------+-----------+------+------------+--------+------+--------+
|     7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |    800 | NULL |     20 |
|     7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 |   1600 |  300 |     30 |
|     7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 |   1250 |  500 |     30 |
|     7566 | JONES  | MANAGER   | 7839 | 1981-03-12 |   2975 | NULL |     20 |
|     7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 |   1250 | 1400 |     30 |
|     7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 |   2450 | NULL |     10 |
|     7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 |   3000 | NULL |     20 |
|     7839 | KING   | PRESIDENT | NULL | 1981-03-12 |   5000 | NULL |     10 |
|     7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 |   1500 |    0 |     30 |
|     7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 |   1100 | NULL |     20 |
|     7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |    950 | NULL |     30 |
|     7902 | FORD   | ANALYST   | 7566 | 1981-03-12 |   3000 | NULL |     20 |
|     7934 | MILLER | CLERK     | 7782 | 1981-03-12 |   1300 |  100 |     10 |
| 17061507 | 陈宗豪 | sTUDENT   | 7782 | 2000-03-12 |   NULL | NULL |     10 |
+----------+--------+-----------+------+------------+--------+------+--------+
14 rows in set (0.00 sec)

mysql> select ename from biao2 where comm<100;
+--------+
| ename  |
+--------+
| TURNER |
+--------+
1 row in set (0.00 sec)
```
3.5 计算每个人的收入(ename, sal + comm)；计算总共有多少人；计算所有人的平均收入。 提示：计算时 NULL 要当做 0 处理； 
```sql
 select ename,salary+comm,count(ename) '人数',AVG(salary+comm) '平均收入' from biao2;
+-------+-------------+------+----------+
| ename | salary+comm | 人数 | 平均收入 |
+-------+-------------+------+----------+
| SMITH |        NULL |   14 |     1840 |
+-------+-------------+------+----------+
```
3.6 显示每个人的下属, 没有下属的显示 NULL。本操作使用关系代数中哪几种运算？
```sql
select t1.ename '大老板',t2.ename '老板' ,t3.ename '下属'
    -> from (biao2 t1 inner join biao2 t2 on t1. empno= t2. mgr)  inner join biao2 t3
    -> on t2.empno=t3.mgr;
+--------+-------+--------+
| 大老板 | 老板  | 下属   |
+--------+-------+--------+
| JONES  | FORD  | SMITH  |
| KING   | BLAKE | ALLEN  |
| KING   | BLAKE | WARD   |
| KING   | BLAKE | MARTIN |
| KING   | JONES | SCOTT  |
| JONES  | SCOTT | ADAMS  |
| KING   | BLAKE | JAMES  |
| KING   | JONES | FORD   |
+--------+-------+--------+
8 rows in set (0.01 sec)
```
3.7 建立一个视图：每个人的empno, ename, job 和 loc。简述为什么要建立本视图。
```sql
create view v_kaoshi
    -> as
    -> select empno ,ename ,job
    -> from biao2;
Query OK, 0 rows affected (0.02 sec)

mysql> select*from v_kaoshi;
+----------+--------+-----------+
| empno    | ename  | job       |
+----------+--------+-----------+
|     7369 | SMITH  | CLERK     |
|     7499 | ALLEN  | SALESMAN  |
|     7521 | WARD   | SALESMAN  |
|     7566 | JONES  | MANAGER   |
|     7654 | MARTIN | SALESMAN  |
|     7698 | BLAKE  | MANAGER   |
|     7788 | SCOTT  | ANALYST   |
|     7839 | KING   | PRESIDENT |
|     7844 | TURNER | SALESMAN  |
|     7878 | ADAMS  | CLERK     |
|     7900 | JAMES  | CLERK     |
|     7902 | FORD   | ANALYST   |
|     7934 | MILLER | CLERK     |
| 17061507 | 陈宗豪 | sTUDENT   |
+----------+--------+-----------+
14 rows in set (0.00 sec)
为了保护隐私不被侵犯
```
3.8 为表2增加一个约束：deptno字段需要在表1中存在；这称做什么完整性？
```sql
alter table biao2
    -> change column deptno
    -> int not null;
    实体完整性
```
3.9 为表2增加一个索引：ename 字段。简述为什么要在 ename 字段建立索引
```sql
create index index_ename
    -> on biao2(ename);
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> show create table biao2\G
*************************** 1. row ***************************
       Table: biao2
Create Table: CREATE TABLE `biao2` (
  `empno` int(11) NOT NULL,
  `ename` varchar(20) DEFAULT NULL,
  `job` varchar(40) DEFAULT NULL,
  `MGR` int(11) DEFAULT NULL,
  `Hiredate` varchar(40) DEFAULT NULL,
  `sal` float DEFAULT NULL,
  `comm` float DEFAULT NULL,
  `deptno` int(11) DEFAULT NULL,
  PRIMARY KEY (`empno`),
  KEY `index_ename` (`ename`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8
1 row in set (0.00 sec)
为了提高从表中检索数据的速度
```
3.10 将表2的 sal 字段改名为 salary
```sql
alter table biao2
    -> change sal salary float;
Query OK, 0 rows affected (0.02 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> desc biao2;
+----------+-------------+------+-----+---------+-------+
| Field    | Type        | Null | Key | Default | Extra |
+----------+-------------+------+-----+---------+-------+
| empno    | int(11)     | NO   | PRI | NULL    |       |
| ename    | varchar(20) | YES  | MUL | NULL    |       |
| job      | varchar(40) | YES  |     | NULL    |       |
| MGR      | int(11)     | YES  |     | NULL    |       |
| Hiredate | varchar(40) | YES  |     | NULL    |       |
| salary   | float       | YES  |     | NULL    |       |
| comm     | float       | YES  |     | NULL    |       |
| deptno   | int(11)     | YES  |     | NULL    |       |
+----------+-------------+------+-----+---------+-------+
8 rows in set (0.00 sec)
```
3.11 撰写一个函数 get_deptno_from_empno，输入 empno，输出对应的 deptno。 简述函数和存储过程有什么不同。
```sql
DELIMITER $$
mysql> CREATE FUNCTION func_get_deptno_from_empno (empno INT)
    -> RETURNS int
    -> BEGIN
    -> RETURN (SELECT deptno FROM biao2 WHERE biao2.empno = empno);
    -> end$$
Query OK, 0 rows affected (0.00 sec)

mysql> delimiter ;
mysql> select func_get_deptno_from_empno(7369);
+----------------------------------+
| func_get_deptno_from_empno(7369) |
+----------------------------------+
|                               20 |
+----------------------------------+
1 row in set (0.01 sec)
于存储过程来说可以返回参数，如记录集，而函数只能返回值或者表对象。
```
4 建立一个新用户，账号为自己的姓名拼音，密码为自己的学号；

4.1 将表1的SELECT, INSERT, UPDATE(ename)权限赋给该账号。

4.2 显示该账号权限
```sql
 USE MYSQL;
Database changed
mysql> SELECT *FROM USER\G
*************************** 1. row ***************************
                  Host: localhost
                  User: root
           Select_priv: Y
           Insert_priv: Y
           Update_priv: Y
           Delete_priv: Y
           Create_priv: Y
             Drop_priv: Y
           Reload_priv: Y
         Shutdown_priv: Y
          Process_priv: Y
             File_priv: Y
            Grant_priv: Y
       References_priv: Y
            Index_priv: Y
            Alter_priv: Y
          Show_db_priv: Y
            Super_priv: Y
 Create_tmp_table_priv: Y
      Lock_tables_priv: Y
          Execute_priv: Y
       Repl_slave_priv: Y
      Repl_client_priv: Y
      Create_view_priv: Y
        Show_view_priv: Y
   Create_routine_priv: Y
    Alter_routine_priv: Y
      Create_user_priv: Y
            Event_priv: Y
          Trigger_priv: Y
Create_tablespace_priv: Y
              ssl_type:
            ssl_cipher:
           x509_issuer:
          x509_subject:
         max_questions: 0
           max_updates: 0
       max_connections: 0
  max_user_connections: 0
                plugin: mysql_native_password
 authentication_string: *7997D5F206D3AC56D4844272ECB338F2BE30F517
      password_expired: N
 password_last_changed: 2020-02-20 10:44:39
     password_lifetime: NULL
        account_locked: N
*************************** 2. row ***************************
                  Host: localhost
                  User: mysql.sys
           Select_priv: N
           Insert_priv: N
           Update_priv: N
           Delete_priv: N
           Create_priv: N
             Drop_priv: N
           Reload_priv: N
         Shutdown_priv: N
          Process_priv: N
             File_priv: N
            Grant_priv: N
       References_priv: N
            Index_priv: N
            Alter_priv: N
          Show_db_priv: N
            Super_priv: N
 Create_tmp_table_priv: N
      Lock_tables_priv: N
          Execute_priv: N
       Repl_slave_priv: N
      Repl_client_priv: N
      Create_view_priv: N
        Show_view_priv: N
   Create_routine_priv: N
    Alter_routine_priv: N
      Create_user_priv: N
            Event_priv: N
          Trigger_priv: N
Create_tablespace_priv: N
              ssl_type:
            ssl_cipher:
           x509_issuer:
          x509_subject:
         max_questions: 0
           max_updates: 0
       max_connections: 0
  max_user_connections: 0
                plugin: mysql_native_password
 authentication_string: *THISISNOTAVALIDPASSWORDTHATCANBEUSEDHERE
      password_expired: N
 password_last_changed: 2020-02-20 10:44:26
     password_lifetime: NULL
        account_locked: Y
2 rows in set (0.00 sec)
```
4.3 `with grant option` 是什么意思。
```sql
传递权限
```
5 表 1 和表 2 这样设计是否符合第一范式，是否符合第二范式，为什么？

6 画出表 1 和表 2 所对应的 E-R 图

7 什么是外模式，什么是内模式。为什么要分成这几层？
```外模式又称子模式或用户模式，对应于用户级。它是某个或某几个用户所看到的数据库的数据视图，是与某一来应用有关的数据的逻辑表示。内模式又称存储模式，百对应于物理级，它是数据库中全体数据的内部表示或底层描述，是数据库最低一级的逻辑描述，它描述了数据在存度储问介质上的存储方式和物理结构，对应着实际存储在外存储介质上的数据库。内模式由内模式描述语言来描述、定义，它是数据库的存储观。
在一个数据库系统中，只有唯一的数据库， 因而作为定义 、描述数据库存储结构的内模式和定义、描述数据库逻辑结答构的模式，也是唯一的，但建立在数据库系统之上的应用则是非常广泛、多样的，所以对应的外模式不是唯一的，也不可能是唯一的。
```
8 什么是ACID？
```sql
ACID是衡量事务的四个特性：原子性、一致性、隔离性、持久性。
```
8.1 编写一个事务，“将 MILLER 的 comm 增加 100，如果增加后的 comm 大于 1000 则回滚”；

8.2 如何查看 MySQL 当前的隔离级别？
```sql
show variables like 'tx_isolation';
+---------------+-----------------+
| Variable_name | Value           |
+---------------+-----------------+
| tx_isolation  | REPEATABLE-READ |
+---------------+-----------------+
1 row in set, 1 warning (0.01 sec)
```
8.3 如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到的结果有哪些，原因是什么？

9 有哪些场景不适合用关系型数据库？为什么？
```sql
搜索 推荐 商品分类 高频交易 用户和权限acl 日志分析 媒体库 email 分类广告 时间系列
```
