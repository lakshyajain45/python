# Q1

mysql> create database jp;

Query OK, 1 row affected (0.01 sec)



mysql> use jp;

Database changed

mysql> create table student(

&#x20;   -> id int(3),

&#x20;   -> name varchar(15),

&#x20;   -> city varchar(15),

&#x20;   -> marks int(3),

&#x20;   -> grade varchar(2)

&#x20;   -> );

Query OK, 0 rows affected (0.04 sec)



mysql> insert into student values(1,'rahul','delhi',72,'B');

Query OK, 1 row affected (0.01 sec)



mysql> insert into student values(2,'priya','mumbai',91,'A');

Query OK, 1 row affected (0.00 sec)



mysql> insert into student values(3,'arjun','delhi',38,'F');

Query OK, 1 row affected (0.00 sec)



mysql> insert into student values(4,'sneha','Pune',85,'A');

Query OK, 1 row affected (0.00 sec)



mysql> insert into student values(5,'vikram','Mumbai',55,'C');

Query OK, 1 row affected (0.00 sec)



mysql> insert into student values(6,'anita','Delhi',94,'A');

Query OK, 1 row affected (0.00 sec)



mysql> insert into student values(7,'rohan','Pune',43,'F');

Query OK, 1 row affected (0.00 sec)



mysql> select \* from student;

+------+--------+--------+-------+-------+

| id   | name   | city   | marks | grade |

+------+--------+--------+-------+-------+

|    1 | rahul  | delhi  |    72 | B     |

|    2 | priya  | mumbai |    91 | A     |

|    3 | arjun  | delhi  |    38 | F     |

|    4 | sneha  | Pune   |    85 | A     |

|    5 | vikram | Mumbai |    55 | C     |

|    6 | anita  | Delhi  |    94 | A     |

|    7 | rohan  | Pune   |    43 | F     |

+------+--------+--------+-------+-------+

7 rows in set (0.01 sec)



mysql> select name,marks from student;

+--------+-------+

| name   | marks |

+--------+-------+

| rahul  |    72 |

| priya  |    91 |

| arjun  |    38 |

| sneha  |    85 |

| vikram |    55 |

| anita  |    94 |

| rohan  |    43 |

+--------+-------+

7 rows in set (0.00 sec)



mysql> select \* from student where city in('Delhi','delhi');

+------+-------+-------+-------+-------+

| id   | name  | city  | marks | grade |

+------+-------+-------+-------+-------+

|    1 | rahul | delhi |    72 | B     |

|    3 | arjun | delhi |    38 | F     |

|    6 | anita | Delhi |    94 | A     |

+------+-------+-------+-------+-------+

3 rows in set (0.01 sec)



mysql> select \* from student where marks>80;

+------+-------+--------+-------+-------+

| id   | name  | city   | marks | grade |

+------+-------+--------+-------+-------+

|    2 | priya | mumbai |    91 | A     |

|    4 | sneha | Pune   |    85 | A     |

|    6 | anita | Delhi  |    94 | A     |

+------+-------+--------+-------+-------+

3 rows in set (0.00 sec)



mysql> select \* from student where grade='F';

+------+-------+-------+-------+-------+

| id   | name  | city  | marks | grade |

+------+-------+-------+-------+-------+

|    3 | arjun | delhi |    38 | F     |

|    7 | rohan | Pune  |    43 | F     |

+------+-------+-------+-------+-------+

2 rows in set (0.00 sec)



# Q2

mysql> select \* from student order by marks desc;

+------+--------+--------+-------+-------+

| id   | name   | city   | marks | grade |

+------+--------+--------+-------+-------+

|    6 | anita  | Delhi  |    94 | A     |

|    2 | priya  | mumbai |    91 | A     |

|    4 | sneha  | Pune   |    85 | A     |

|    1 | rahul  | delhi  |    72 | B     |

|    5 | vikram | Mumbai |    55 | C     |

|    7 | rohan  | Pune   |    43 | F     |

|    3 | arjun  | delhi  |    38 | F     |

+------+--------+--------+-------+-------+

7 rows in set (0.01 sec)



mysql> select \* from student order by marks desc and rows=3;

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'and rows=3' at line 1

mysql> select \* from student order by marks desc and limit=3 ;

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'and limit=3' at line 1

mysql> select \* from student order by marks desc limit 3 ;

+------+-------+--------+-------+-------+

| id   | name  | city   | marks | grade |

+------+-------+--------+-------+-------+

|    6 | anita | Delhi  |    94 | A     |

|    2 | priya | mumbai |    91 | A     |

|    4 | sneha | Pune   |    85 | A     |

+------+-------+--------+-------+-------+

3 rows in set (0.00 sec)



mysql> select \* from student order by name;

+------+--------+--------+-------+-------+

| id   | name   | city   | marks | grade |

+------+--------+--------+-------+-------+

|    6 | anita  | Delhi  |    94 | A     |

|    3 | arjun  | delhi  |    38 | F     |

|    2 | priya  | mumbai |    91 | A     |

|    1 | rahul  | delhi  |    72 | B     |

|    7 | rohan  | Pune   |    43 | F     |

|    4 | sneha  | Pune   |    85 | A     |

|    5 | vikram | Mumbai |    55 | C     |

+------+--------+--------+-------+-------+

7 rows in set (0.00 sec)



mysql> select \* from student order by marks limit 2 ;

+------+-------+-------+-------+-------+

| id   | name  | city  | marks | grade |

+------+-------+-------+-------+-------+

|    3 | arjun | delhi |    38 | F     |

|    7 | rohan | Pune  |    43 | F     |

+------+-------+-------+-------+-------+

2 rows in set (0.00 sec)



mysql> select \* from student where city in ('Delhi','delhi') order by marks desc ;

+------+-------+-------+-------+-------+

| id   | name  | city  | marks | grade |

+------+-------+-------+-------+-------+

|    6 | anita | Delhi |    94 | A     |

|    1 | rahul | delhi |    72 | B     |

|    3 | arjun | delhi |    38 | F     |

+------+-------+-------+-------+-------+

3 rows in set (0.03 sec)



# Q3

mysql> select count(\*) from student;

+----------+

| count(\*) |

+----------+

|        7 |

+----------+

1 row in set (0.01 sec)



mysql> select avg(marks) from student;

+------------+

| avg(marks) |

+------------+

|    68.2857 |

+------------+

1 row in set (0.00 sec)



mysql> select max(marks),min(marks) from student;

+------------+------------+

| max(marks) | min(marks) |

+------------+------------+

|         94 |         38 |

+------------+------------+

1 row in set (0.00 sec)



mysql> select count(\*) from student where city in ('delhi','Delhi');

+----------+

| count(\*) |

+----------+

|        3 |

+----------+

1 row in set (0.00 sec)



mysql> select avg(marks) from student where grade='A';

+------------+

| avg(marks) |

+------------+

|    90.0000 |

+------------+

1 row in set (0.00 sec)



# Q4

mysql> select count(\*),city from student group by city;

+----------+--------+

| count(\*) | city   |

+----------+--------+

|        3 | delhi  |

|        2 | mumbai |

|        2 | Pune   |

+----------+--------+

3 rows in set (0.00 sec)



mysql> select avg(marks),grade from student group by grade;

+------------+-------+

| avg(marks) | grade |

+------------+-------+

|    90.0000 | A     |

|    72.0000 | B     |

|    55.0000 | C     |

|    40.5000 | F     |

+------------+-------+

4 rows in set (0.00 sec)



mysql> select city from student group by city having count(\*)>2;

+-------+

| city  |

+-------+

| delhi |

+-------+

1 row in set (0.00 sec)



mysql> select max(marks),city from student group by city;

+------------+--------+

| max(marks) | city   |

+------------+--------+

|         94 | delhi  |

|         91 | mumbai |

|         85 | Pune   |

+------------+--------+

3 rows in set (0.00 sec)



# Q5

mysql> select \* from student;

+------+--------+--------+-------+-------+

| id   | name   | city   | marks | grade |

+------+--------+--------+-------+-------+

|    1 | rahul  | delhi  |    72 | B     |

|    2 | priya  | mumbai |    91 | A     |

|    3 | arjun  | delhi  |    38 | F     |

|    4 | sneha  | Pune   |    85 | A     |

|    5 | vikram | Mumbai |    55 | C     |

|    6 | anita  | Delhi  |    94 | A     |

|    7 | rohan  | Pune   |    43 | F     |

+------+--------+--------+-------+-------+

7 rows in set (0.00 sec)



mysql> insert into student(name,city,marks,grade) values('karan','banglore',78,'B');

Query OK, 1 row affected (0.03 sec)



mysql> select \* from student

&#x20;   -> ;

+------+--------+----------+-------+-------+

| id   | name   | city     | marks | grade |

+------+--------+----------+-------+-------+

|    1 | rahul  | delhi    |    72 | B     |

|    2 | priya  | mumbai   |    91 | A     |

|    3 | arjun  | delhi    |    38 | F     |

|    4 | sneha  | Pune     |    85 | A     |

|    5 | vikram | Mumbai   |    55 | C     |

|    6 | anita  | Delhi    |    94 | A     |

|    7 | rohan  | Pune     |    43 | F     |

| NULL | karan  | banglore |    78 | B     |

+------+--------+----------+-------+-------+

8 rows in set (0.00 sec)



mysql> update student set marks=65,grade='C' where name='arjun';

Query OK, 1 row affected (0.01 sec)

Rows matched: 1  Changed: 1  Warnings: 0



mysql> update student set id=8 where name='karan';

Query OK, 1 row affected (0.02 sec)

Rows matched: 1  Changed: 1  Warnings: 0



mysql> select \* from student;

+------+--------+----------+-------+-------+

| id   | name   | city     | marks | grade |

+------+--------+----------+-------+-------+

|    1 | rahul  | delhi    |    72 | B     |

|    2 | priya  | mumbai   |    91 | A     |

|    3 | arjun  | delhi    |    65 | C     |

|    4 | sneha  | Pune     |    85 | A     |

|    5 | vikram | Mumbai   |    55 | C     |

|    6 | anita  | Delhi    |    94 | A     |

|    7 | rohan  | Pune     |    43 | F     |

|    8 | karan  | banglore |    78 | B     |

+------+--------+----------+-------+-------+

8 rows in set (0.00 sec)



mysql> delete from student wher grade='F';

ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'wher grade='F'' at line 1

mysql> delete from student where grade='F';

Query OK, 1 row affected (0.01 sec)



mysql> select \* from student;

+------+--------+----------+-------+-------+

| id   | name   | city     | marks | grade |

+------+--------+----------+-------+-------+

|    1 | rahul  | delhi    |    72 | B     |

|    2 | priya  | mumbai   |    91 | A     |

|    3 | arjun  | delhi    |    65 | C     |

|    4 | sneha  | Pune     |    85 | A     |

|    5 | vikram | Mumbai   |    55 | C     |

|    6 | anita  | Delhi    |    94 | A     |

|    8 | karan  | banglore |    78 | B     |

+------+--------+----------+-------+-------+

7 rows in set (0.00 sec)



