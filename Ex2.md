# EX 2 Data Manipulation Language (DML) Commands and built in functions in SQL
## DATE:
## AIM:
To create a manager database and execute DML queries using SQL.


## DML(Data Manipulation Language)
<div align="justify">
The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.
</div>

## List of DML commands: 
<div align="justify">
INSERT: It is used to insert data into a table.<br>
UPDATE: It is used to update existing data within a table.<br>
DELETE: It is used to delete records from a database table.<br>
</div>

## Create the table as given below:
```sql
create table manager(enumber number(6),ename char(15),salary number(5),commission number(4),annualsalary number(7),Hiredate date,designation char(10),deptno number(2),reporting char(10));
```
## insert the following values into the table
```sql
insert into manager values(7369,'Dharsan',2500,500,30000,'30-June-81','clerk',10,'John');
insert into manager values(7839,'Subu',3000,400,36000,'1-Jul-82','manager',null,'James');
insert into manager values(7934,'Aadhi',3500,300,42000,'1-May-82','manager',30,NULL);
insert into manager values(7788,'Vikash',4000,0,48000,'12-Aug-82','clerk',50,'Bond');
```

### Q1) Update all the records of manager table by increasing 10% of their salary as bonus.

### QUERY:
```sql
UPDATE manager
SET salary = salary + (salary * 0.10),
annualsalary = annualsalary + (annualsalary * 0.10);
```

### OUTPUT:

![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/5d6d1541-9fa9-476a-9490-8a64bc5d2b9c)


### Q2) Delete the records from manager table where the salary less than 2750.


### QUERY:
```sql
DELETE FROM manager WHERE salary < 2750;
```

### OUTPUT:


![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/748af6b1-3b2e-4afa-a7ef-c9804383e550)



### Q3) Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)


### QUERY:
```sql
SELECT ename AS "Name", salary * 12 AS "Annual Salary"
FROM manager;
```

### OUTPUT:

![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/b6f975bb-bff3-4fc8-a836-8a5d714b6495)



### Q5)	List the names of Clerks from emp table.


### QUERY:
```sql
SELECT ename from manager where designation='clerk';
```
### OUTPUT:

![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/e88b1fac-1721-4566-8e98-95d557531519)



### Q6)	List the names of employee who are not Managers.


### QUERY:
```sql
SELECT ename from manager where designation!='manager';
```
### OUTPUT:

![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/763e9332-8769-4b0e-a30c-62e44a424e6e)



### Q7)	List the names of employees not eligible for commission.


### QUERY:
```sql
SELECT ename from manager where commission=0;
```
### OUTPUT:

![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/12ca2927-b243-4d02-a82f-7abdd44ef9c2)



### Q8)	List employees whose name either start or end with ‘s’.


### QUERY:
```sql
SELECT ename
FROM manager
WHERE ename LIKE 'S%' OR ename LIKE '%s';
```
### OUTPUT:


![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/c5471199-9c1b-47e0-acdd-3fac1e3cbafa)



### Q9) Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.


### QUERY:
```sql
select ename,designation,deptno,Hiredate from manager
order by Hiredate asc;
```
### OUTPUT:

![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/145a0840-9577-4500-937a-35a7d85fbf16)



### Q10) List the Details of Employees who have joined before 30 Sept 81.


### QUERY:
```sql
SELECT *
FROM manager
WHERE Hiredate < TO_DATE('1981-09-30', 'YYYY-MM-DD');
```
### OUTPUT:

![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/af2ca59d-5def-4976-9ce4-b804c776d83d)



### Q11)	List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.


### QUERY:
```sql

select ename,deptno,salary from manager order by deptno asc;
select ename,deptno,salary from manager order by salary desc;
```
### OUTPUT:


![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/8c87ecdc-3bd2-49ec-a7bd-16a4a5ecc2a6)



### Q12) List the names of employees not belonging to dept no 30,40 & 10


### QUERY:
```sql
select ename from manager where deptno not in (10,30,40);
```

### OUTPUT:


![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/742ed824-d207-4ea0-b528-4ec41301ca39)



### Q13) Find number of rows in the table EMP

### QUERY:
```sql
select count(*) from manager;
```
### OUTPUT:


![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/1c8df334-5413-4b9f-9b6a-643c67502532)



### Q14) Find maximum, minimum and average salary in EMP table.

### QUERY:
```sql
select ename ,salary,annualsalary from manager
where salary = (select max(salary) from manager);

select ename ,salary,annualsalary from manager
where salary = (select min(salary) from manager);

select avg(salary) from manager;
```

### OUTPUT:

![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/5a781034-9006-4a88-a0b3-8cf933f7e552)



### Q15) List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.

### QUERY:
```sql
SELECT designation, COUNT(*) AS "Number of Employees"
FROM manager
GROUP BY designation
ORDER BY COUNT(*) DESC;
```
### OUTPUT:

![image](https://github.com/vinushcv/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/113975318/8fc27c46-59ba-40fc-b80a-5e237b74676a)


### RESULT:
Thus, Manager database is created and DML queries such as insertion, updation, deletion are executed using SQL.


