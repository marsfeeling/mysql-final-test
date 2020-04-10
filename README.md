# mysql-final-test

2019-2020 mysql final test

姓名： 郭剑

学号： 17061816

说明1：考试为开卷，可以上网，自觉不要相互电话和QQ；

说明2：考试时间为：2020 年 4 月 10 日 8:10分-9:40分。

说明3：试题比较多，抓紧时间，超时提交的github commit不被接受。未避免完全超时提交，可以在做题过程中多 commit 几次。

说明4：结束后发邮件给 42225@hdu.edu.cn 标题为“MySQL期末考试,姓名+学号”，内容为github链接。


1 打印当前时间（例如 2020-04-07 13:41:42），写出SQL语句和结果

2 组合打印自己的姓名和学号

(例如 张三+123456 或者 zhangsan+123456 显示需包含加号)，写出SQL语句和结果

3 建立如下表1和表2，写出建表语句和插入语句。

表1：其中deptno为主键
```
deptno, deptno,    loc
(10, "ACCOUNTING", "NEW YORK"),
(20, "RESEARCH", "DALLAS"),
(30, "SALES", "CHICAGO"),
(40, "OPERATIONS", "BOSTON")
```
代码
```
create table t_dept2(
    -> depton int,
    -> dname varchar(20),
    -> loc varchar(40)
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql> describe t_dept2;
+--------+-------------+------+-----+---------+-------+
| Field  | Type        | Null | Key | Default | Extra |
+--------+-------------+------+-----+---------+-------+
| depton | int(11)     | YES  |     | NULL    |       |
| dname  | varchar(20) | YES  |     | NULL    |       |
| loc    | varchar(40) | YES  |     | NULL    |       |
+--------+-------------+------+-----+---------+-------+
3 rows in set (0.01 sec)
insert into t_dept2(depton,dname,loc)
    -> values(10,'ACCOUNING','NEW YORK'),
    -> (20,'RESEARCH','DALLAS'),
    -> (30,'SALES','CHICAGO'),
    -> (40,'OPERATIONS','BOSTON');
Query OK, 4 rows affected (0.00 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM t_dept2;
+--------+------------+----------+
| depton | dname      | loc      |
+--------+------------+----------+
|     10 | ACCOUNING  | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+
4 rows in set (0.00 sec)

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
代码：
```
 CREATE TABLE t_employee2 (
    ->     deptno INT NOT NULL,
    -> empno INT PRIMARY KEY,
    -> ename VARCHAR(20),
    -> job VARCHAR(20),
    ->     MGR INT,
    -> Hiredate Date,
    -> sal float,
    -> comm float
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql> INSERT INTO t_employee2 (empno, ename, job, MGR, Hiredate, sal, comm, deptno)
    -> VALUES (7369, "SMITH", "CLERK", 7902, "1981-03-12", 800.00, NULL, 20),
    -> (7499, "ALLEN", "SALESMAN", 7698, "1982-03-12", 1600, 300, 30),
    -> (7521, "WARD", "SALESMAN", 7698, "1838-03-12", 1250, 500, 30),
    -> (7566, "JONES", "MANAGER", 7839, "1981-03-12", 2975, NULL, 20),
    -> (7654, "MARTIN", "SALESMAN", 7698, "1981-01-12", 1250, 1400, 30),
    -> (7698, "BLAKE", "MANAGER", 7839, "1985-03-12", 2450, NULL, 10),
    -> (7788, "SCOTT", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7839, "KING", "PRESIDENT", NULL, "1981-03-12", 5000, NULL, 10),
    -> (7844, "TURNER", "SALESMAN", 7689, "1981-03-12", 1500, 0, 30),
    -> (7878, "ADAMS", "CLERK", 7788, "1981-03-12", 1100, NULL,20),
    -> (7900, "JAMES", "CLERK", 7698,"1981-03-12",  950, NULL, 30),
    -> (7902, "FORD", "ANALYST", 7566, "1981-03-12", 3000, NULL, 20),
    -> (7934, "MILLER", "CLERK", 7782, "1981-03-12", 1300, NULL, 10)
    -> ;
Query OK, 13 rows affected (0.01 sec)
Records: 13  Duplicates: 0  Warnings: 0

mysql> select * from t_employee2;
+--------+-------+--------+-----------+------+------------+------+------+
| deptno | empno | ename  | job       | MGR  | Hiredate   | sal  | comm |
+--------+-------+--------+-----------+------+------------+------+------+
|     20 |  7369 | SMITH  | CLERK     | 7902 | 1981-03-12 |  800 | NULL |
|     30 |  7499 | ALLEN  | SALESMAN  | 7698 | 1982-03-12 | 1600 |  300 |
|     30 |  7521 | WARD   | SALESMAN  | 7698 | 1838-03-12 | 1250 |  500 |
|     20 |  7566 | JONES  | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |
|     30 |  7654 | MARTIN | SALESMAN  | 7698 | 1981-01-12 | 1250 | 1400 |
|     10 |  7698 | BLAKE  | MANAGER   | 7839 | 1985-03-12 | 2450 | NULL |
|     20 |  7788 | SCOTT  | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7839 | KING   | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     30 |  7844 | TURNER | SALESMAN  | 7689 | 1981-03-12 | 1500 |    0 |
|     20 |  7878 | ADAMS  | CLERK     | 7788 | 1981-03-12 | 1100 | NULL |
|     30 |  7900 | JAMES  | CLERK     | 7698 | 1981-03-12 |  950 | NULL |
|     20 |  7902 | FORD   | ANALYST   | 7566 | 1981-03-12 | 3000 | NULL |
|     10 |  7934 | MILLER | CLERK     | 7782 | 1981-03-12 | 1300 | NULL |
+--------+-------+--------+-----------+------+------------+------+------+
13 rows in set (0.00 sec)

mysql> select *
    -> from (t_employee2 t1 inner join t_employee2 t2 on t1. mgr= t2.empno )  inner join t_employee2 t3
    -> on t2. mgr= t3.empno;
+--------+-------+--------+----------+------+------------+------+------+--------+-------+-------+---------+------+------------+------+------+--------+-------+-------+-----------+------+------------+------+------+
| deptno | empno | ename  | job      | MGR  | Hiredate   | sal  | comm | deptno | empno | ename | job     | MGR  | Hiredate   | sal  | comm | deptno | empno | ename | job       | MGR  | Hiredate   | sal  | comm |
+--------+-------+--------+----------+------+------------+------+------+--------+-------+-------+---------+------+------------+------+------+--------+-------+-------+-----------+------+------------+------+------+
|     20 |  7369 | SMITH  | CLERK    | 7902 | 1981-03-12 |  800 | NULL |     20 |  7902 | FORD  | ANALYST | 7566 | 1981-03-12 | 3000 | NULL |     20 |  7566 | JONES | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |
|     30 |  7499 | ALLEN  | SALESMAN | 7698 | 1982-03-12 | 1600 |  300 |     10 |  7698 | BLAKE | MANAGER | 7839 | 1985-03-12 | 2450 | NULL |     10 |  7839 | KING  | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     30 |  7521 | WARD   | SALESMAN | 7698 | 1838-03-12 | 1250 |  500 |     10 |  7698 | BLAKE | MANAGER | 7839 | 1985-03-12 | 2450 | NULL |     10 |  7839 | KING  | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     30 |  7654 | MARTIN | SALESMAN | 7698 | 1981-01-12 | 1250 | 1400 |     10 |  7698 | BLAKE | MANAGER | 7839 | 1985-03-12 | 2450 | NULL |     10 |  7839 | KING  | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     20 |  7788 | SCOTT  | ANALYST  | 7566 | 1981-03-12 | 3000 | NULL |     20 |  7566 | JONES | MANAGER | 7839 | 1981-03-12 | 2975 | NULL |     10 |  7839 | KING  | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     20 |  7878 | ADAMS  | CLERK    | 7788 | 1981-03-12 | 1100 | NULL |     20 |  7788 | SCOTT | ANALYST | 7566 | 1981-03-12 | 3000 | NULL |     20 |  7566 | JONES | MANAGER   | 7839 | 1981-03-12 | 2975 | NULL |
|     30 |  7900 | JAMES  | CLERK    | 7698 | 1981-03-12 |  950 | NULL |     10 |  7698 | BLAKE | MANAGER | 7839 | 1985-03-12 | 2450 | NULL |     10 |  7839 | KING  | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
|     20 |  7902 | FORD   | ANALYST  | 7566 | 1981-03-12 | 3000 | NULL |     20 |  7566 | JONES | MANAGER | 7839 | 1981-03-12 | 2975 | NULL |     10 |  7839 | KING  | PRESIDENT | NULL | 1981-03-12 | 5000 | NULL |
+--------+-------+--------+----------+------+------------+------+------+--------+-------+-------+---------+------+------------+------+------+--------+-------+-------+-----------+------+------------+------+------+
8 rows in set (0.01 sec)

mysql>
mysql> select t1.ename My_name,t2.ename My_b_name ,t3.ename My_b_b_name
    -> from (t_employee2 t1 inner join t_employee2 t2 on t1. mgr= t2.empno )  inner join t_employee2 t3
    -> on t2. mgr= t3.empno;
+---------+-----------+-------------+
| My_name | My_b_name | My_b_b_name |
+---------+-----------+-------------+
| SMITH   | FORD      | JONES       |
| ALLEN   | BLAKE     | KING        |
| WARD    | BLAKE     | KING        |
| MARTIN  | BLAKE     | KING        |
| SCOTT   | JONES     | KING        |
| ADAMS   | SCOTT     | JONES       |
| JAMES   | BLAKE     | KING        |
| FORD    | JONES     | KING        |
+---------+-----------+-------------+
8 rows in set (0.00 sec)
```

3.1 表2 中再插入一条记录：

`(你的学号，你的姓名或者拼音， “CLERK”, 7782, 你的生日,  NULL, NULL, 10)`
 
例如：`(12345,  "Zhangsan", "sTUDENT", 7782, "2000-03-12", NULL, NULL, 10)`

3.2 表中入职时间（Hiredate字段）最短的人。

3.3 有几种职位（job字段）？在关系代数中，本操作是什么运算？

3.4 将 MILLER 的 comm 增加 100； 然后，找到 comm 比 MILLER 低的人；

3.5 计算每个人的收入(ename, sal + comm)；计算总共有多少人；计算所有人的平均收入。 提示：计算时 NULL 要当做 0 处理； 

3.6 显示每个人的下属, 没有下属的显示 NULL。本操作使用关系代数中哪几种运算？

3.7 建立一个视图：每个人的empno, ename, job 和 loc。简述为什么要建立本视图。

3.8 为表2增加一个约束：deptno字段需要在表1中存在；这称做什么完整性？

3.9 为表2增加一个索引：ename 字段。简述为什么要在 ename 字段建立索引

3.10 将表2的 sal 字段改名为 salary

3.11 撰写一个函数 get_deptno_from_empno，输入 empno，输出对应的 deptno。 简述函数和存储过程有什么不同。

4 建立一个新用户，账号为自己的姓名拼音，密码为自己的学号；

4.1 将表1的SELECT, INSERT, UPDATE(ename)权限赋给该账号。

4.2 显示该账号权限

4.3 `with grant option` 是什么意思。

对象的owner将权限赋予某个用户

5 表 1 和表 2 这样设计是否符合第一范式，是否符合第二范式，为什么？

6 画出表 1 和表 2 所对应的 E-R 图

7 什么是外模式，什么是内模式。为什么要分成这几层？

8 什么是ACID？

8.1 编写一个事务，“将 MILLER 的 comm 增加 100，如果增加后的 comm 大于 1000 则回滚”；

8.2 如何查看 MySQL 当前的隔离级别？

8.3 如果隔离级别为 READ-UNCOMMITED, 完成 “MILLER 的 comm 增加 100” 事务操作完成后，可能读到的结果有哪些，原因是什么？

9 有哪些场景不适合用关系型数据库？为什么？
