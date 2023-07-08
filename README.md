# SQL_pratices_Query
create database employee7;
create table employeetable(EMPLOYEE_ID INT,FIRST_NAME varchar(255),LAST_NAME varchar(255),SALARY int,JOINING_DATE date,DEPARTMENT varchar(255));

select *from employeetable;
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(1,"Venkatesh","S",100000,20150828,"BANKING");
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(2,"Ragavi","P",75000,20150828,"BUSINESS");
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(3,"Gopinath","C",50000,20160302,"PHARMA");
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(4,"Dinesh","G",50000,20160302,"INSURANCE");
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(5,"Saibabu","E",40000,20170708,"SOFTWARE");
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(6,"Hasan","S",29000,20170708,"MANUFACTURING");
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(7,"Divya","P",33000,20170708,"HEALTHCARE");
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(8,"Aravindan","R",40000,20170708,"HEALTHCARE");
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(9,"Sathish","MD",45000,20160302,"AUTOMOBILE");
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(10,"Prasanth","PKP",34000,20160302,"INSURANCE");
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(11,"Vijay","R",25684,20160302,"BUSINESS");
insert into employeetable(EMPLOYEE_ID,FIRST_NAME,LAST_NAME,SALARY,JOINING_DATE,DEPARTMENT) values(12,"Sivakumar","K",54789,20160302,"SOFTWARE");

/*alter table employee add primary key(EMPLOYEE_ID);
delete from employee where EMPLOYEE_ID=12;*/
select * from employeetable;
select FIRST_NAME,LAST_NAME from employeetable;
select FIRST_NAME as Employee_Name from employeetable;
select UPPER(FIRST_NAME) from employeetable;
select distinct DEPARTMENT from employeetable;
select SUBSTRING(FIRST_NAME,1,3)from employeetable;
select position('a' in "ragavi") as position_value;
select Rtrim(FIRST_NAME) from employeetable;
select Ltrim(FIRST_NAME) from employeetable;

select length(FIRST_NAME) from employeetable;
select concat(FIRST_NAME,"-",LAST_NAME) FROM employeetable;
select JOINING_DATE from employeetable;
select * from employeetable order by (FIRST_NAME);
select * from employeetable order by (FIRST_NAME)desc;
select * from employeetable order by  FIRST_NAME asc,SALARY desc;
select * from employeetable order by(SALARY)desc;
select * from employeetable where (FIRST_NAME="dinesh");
select * from employeetable where FIRST_NAME in("dinesh","roy");

Select * from employeetable where FIRST_NAME not in ('dinesh','Roy');
select * from employeetable where FIRST_NAME like 'd%';
select * from employeetable where FIRST_NAME like '%v%';
select * from employeetable where FIRST_NAME like '%n';
select * from employeetable where FIRST_NAME like 'j____';
select* from employeetable where salary>60000;
select* from employeetable where salary<80000;
select *from employeetable where FIRST_NAME in ("venkatesh","ragavi");
select *from employeetable where extract(year from JOINING_DATE)=2015;
select *from employeetable where extract(month from JOINING_DATE)=01;
select * from employeetable where JOINING_DATE > '2017/01/01';
select * from employeetable where JOINING_DATE < '2016/01/31';
Select CONVERT(DATE_FORMAT(joining_date,'%Y-%m-%d-%H:%i:00'),DATETIME) from employeetable;
select microsecond(JOINING_DATE) FROM employeetable;


select count(DEPARTMENT),DEPARTMENT from employeetable group by DEPARTMENT having DEPARTMENT="BUSINESS";
select count(JOINING_DATE),JOINING_DATE from employeetable group by JOINING_DATE having JOINING_DATE=20170708;

select EMPLOYEE_ID,concat(First_name," ",last_name),joining_date from employeetable having JOINING_DATE=20170708 order by concat(First_name,last_name);

create table Incentive (EMPLOYEE_REF_ID int ,INCENTIVE_DATE date,INCENTIVE_AMOUNT int);
select *from Incentive;

insert into incentive(EMPLOYEE_REF_ID,INCENTIVE_DATE,INCENTIVE_AMOUNT) values(1,20160201,5000);
insert into incentive(EMPLOYEE_REF_ID,INCENTIVE_DATE,INCENTIVE_AMOUNT) values(2,20160201,3000);
insert into incentive(EMPLOYEE_REF_ID,INCENTIVE_DATE,INCENTIVE_AMOUNT) values(3,20170217,4000);
insert into incentive(EMPLOYEE_REF_ID,INCENTIVE_DATE,INCENTIVE_AMOUNT) values(1,20170117,4500);
insert into incentive(EMPLOYEE_REF_ID,INCENTIVE_DATE,INCENTIVE_AMOUNT) values(2,20170117,3500);
select (employeetable.SALARY+sum(incentive_amount)) from incentive inner join employeetable where  employeetable.employee_id=1 and incentive.employee_ref_id=1;
