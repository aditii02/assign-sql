1.1) select staff_name,design_code from staff_master where hiredate<'01-jan-2003' and staff_sal between 12000 and 25000;

1.2) select staff_code ,staff_name , dept_code from staff_master where ( sysdate-hiredate)/365 >= 18 order by hiredate desc;

1.3) select * from staff_master where mgr_code is null;

1.4) select * from book_master where book_pub_year between 2001 and 2004 and book_name like '%"&"%';

1.5) select staff_name from staff_master where staff_name like '%\%' escape '\';

2.1.1) select staff_name, lpad(staff_sal,15,'$') from staff_master;

2.1.2) select student_name,to_char(student_dob,'month dd yyyy') as student_dob from student_master where to_char(student_dob,'day') like ('%saturday%') or to_char(student_dob,'day') like ('%sunday%');

2.1.3) select staff_name, round ((months_between(sysdate,hiredate)),0) as Months_Worked from staff_master order by Months_Worked;

2.1.4) select * from book_master where book_pub_year between 2001 and 2004 and book_name like '%&%';

2.1.5)alter table staff_master add grade varchar2(20);
  update staff_master set grade='A' where staff_sal>50000;
  update staff_master set grade='B' where staff_sal>25000 and staff_sal<50000;
  update staff_master set grade='C' where staff_sal>10000 and staff_sal<25000;
  update staff_master set grade='D' where staff_sal<10000;
  select staff_name,staff_sal,grade from staff_master;

2.1.6) select staff_name,hiredate from staff_master;

2.1.7)select instr('Mississippi', 'i',2,3) from dual;

2.1.8) select to_char(next_day(last_day(sysdate)-7,'friday','dd month,yyyy') as payday from dual;

2.1.9) select student_code, student_name, decode(dept_code, 20, 'electronics', 30, 'electricals', 'others') department_name from student_master;
 
2.2.1) select round(MAX(staff_sal),0)"Maximum", round(MIN(staff_sal),0)"minimun",round(SUM(staff_sal),0)"sum",round(avg(staff_sal),0)"average", dept_code from staff_master group by dept_code

2.2.2) select deptno,count(*) from emp where mgr=7839 group by deptno;

2.2.3) select staff_sal, department_master.dept_code, department_master.dept_name from staff_master, department-master where staff_sal >20000 and mgr_code=null;

3.1) select staff_name,staff_salary,d.deptcode,d.deptname from staff_master,dept_master d where staff_salary>20000;

3.2) select staff code,staff name,staff sal from staff master where staff sal>(select avg(staff sal)from staff master);
 

3.3) select s.student_code,s.student_name,b.book_code,m.book_name from student_master s, book_transactions b, book_master m where s.student_code=b.student_code and b.book_code=m.book_code and book_expected_return_date='09-feb-2011'; 

3.4) select s.staff_code, s.staff_name, b.book_code, b.book_name, bb.book_issue_date, d.design_name, dm.dept_name from staff_master s, book_master b, book_transactions bb, designation_master d, department_master dm whee s.staff_code=bb.staff_code and b.book_code=bb.book_code and sysdate-30<= bb.ook_issue_date;

3.5) select staff_code, s.staff_name, d.design_name, dd.dept_name, b.book_code, bb.book_name, (trunc(sysdate)-trunc(b.book_expected_return_date))*5 as fine from staff_master s, designation_master d, department_master dd, book_transactions b, book_master bb where s.dept_code=dd.dept_code and s.design_code=d.design_code and s.staff_code=b.staff_code;

3.6) select staff code,staff name,staff sal from staff master where staff sal>(select avg(staff sal)from staff master);

3.7) select book_pub_author, book_name fro book_master where book_pub_author in(select book_pub_author from book_master group by book_pub_author having count(book_pub_author)>1);

3.8) select s.staff_name, dm.dept_name, s.staff_name, bt.book_code from staff_master s, book_transactions bt, department_master dm where bt.staff_code = s.staff_code and dm.dept_code = s.dept_code;

3.9) create table accountdetails as select *from accountmaster;

3.10) select staff_code, staff_name, dept_name, design_name from staff_master sm, department_master depm, designation_master desm where sm.dept_code = depm.dept_code and (months_between(sysdate,hiredate))<=3;

3.11) select b.ename, count(*) from emp e join emp b on b.empno = e.mgr group by b.empno,b.ename;

3.12) select book_name from book_master where book_code in (select book_code from book_transactions where book_actual_return_date is null);

3.13) select sm.dept_code, dm.dept_name, count(sm.staff_name) as number_of_people from staff master sm inner join department_master dm where sm.dept_code = dm.dept_code;

4.1) create table customer(Customerid, number(5), cust_name varchar2(20), Address1 varchar2(30), Address2 varchar2(30));

4.2) alter table cust
    modify custname varchar2(30);
    alter table cust rename column custname to customername;

4.3) a) 
       alter customer add age number(3);
       alter customer add gende varchar2(10);
       alter customer add mobno number(10);
    
    b)
       alter customer rename to cust_table;

4.4) insert into cust values(1000,'Allen', '#115 Chicago', '#115 Chicago', 'M','25','7878776');
    insert into cust values(1001,'George', '#116 France', '#116 France', 'M','25','434524');
    insert into cust values(1002,'Becker', '#114 New York', '#114 New York', 'M','45','431525');
     

4.5) alter table cust_table add constraint custid_prim primary key(customerid);

4.6) insert into cust_tables values(1002, 'John', '#114 chicago', '#114 Chicago', 'M' , 45, 439525);
    error at line 1:
    ora:00001 : unique constraint <system.custid_prim> violated
4.7) alter table cust_table disabe constraint custid_prim;
    table altered
    insert into cust_table values (1022,'beckar', '#114 New york' , '# 114 New york", 'M',45,431525);
    insert into cust_table values (1003,'Nanapateker', '#115 India' , '# 114 India", 'M',45,431525);

4.8) Alter table cust_table add constraints Custid_prim PRIMARY KEY (customerid);

4.9) alter table customer drop constraint custid_prim;
 
4.10) truncate table customer ; 
      
4.11) alter table customer add email varchar2(20);  

4.12) alter table customer drop column email;  

4.13) create table suppliers(suppid number(5), sname varchar2(20), addr1 varchar2(30), addr2 varchar2(30), contact no number);

4.14) create table customerMaster(customerId number(5) primary key, customername varchar2(20) not null, address1 varchar2(20) not null, address2 varchar2(20), gender varchar2(1), age number(3), phoneNo number(10));

4.15) Create table Accoutnmaster(customerid number(5),Accountnumber number(10) primary key ,accounttype char(3),ledgerbalance number(10) Not Null);
    Create sequence seq_ano
    MINVALUE 101
    MAXVALUE 10000
    START WITH 101
    INCREMENT BY 1
    CACHE 101;

4.16) Alter table Accountmaster ADD constraint ass_fk FOREIGN KEY(customerid) REFERENCES customermaster(customerid);      


4.17) insert into CustomerMaster values(1000,Allen,#115Chicago,#115Chicago,M,25,7878776);
    insert into CustomerMaster values(1001,George,#116France,#116France,M,25,434524);
    insert into CustomerMaster values(1002,Becker,#114New York,#114New York,M,45,4315250);

4.18) Alter table accountmaster and constraint ck_ac check(accounttype = 'NRI' or accounttype = 'IND');

4.19) Alter table accountmaster and constraint balance_check(ledger balance > 5000);

4.20) Delete from accountmaster,customertable wherecustomer id=1001;

4.21) Create table accountdetails as select * from Accountmaster;
 

4.22) create view acc_view as select (customer_id,customer_name,accountnumber,accounttype,ledgerbalance) from accountmaster;

4.23) create view vAccs_Dtls as select Accounttype,ledgerbalance from Accountmaster where where accounttype 'IND' and ledgerbalance < 10000;

4.24) create view accsvw10 as select * from employee with READ ONLY;

4.25) create sequence seq_dept minvalue 40 start with 40 increment by 10 maxvalue 200 cache 40;

4.26) create table department_masters(dept_no number, dept_name varchar2(20)) ;
    insert into department_masters values (seq_dept.NEXTVAL, 'cse');
    insert into department_masters values (seq_dept.NEXTVAL, 'it');
    insert into department_masters values (seq_dept.NEXTVAL, 'ece');

4.27) DROP sequence seq_dept;

4.28) create index no_name on emp(empno);

4.29) create  synonym syn_emp for emp;

4.30) select * from user_synonyms where SYNONYM_NAME='SYNEMP';

4.31) CREATE INDEX IDX_EMP_HIREDATE on emp(HIREDATE);

4.32) create sequence Seq_Emp start with 1000 increment by 1;
    create table employee(empno number, ename varchar2(30));
    insert into employee values(Seq_Emp.nextval, '&ename');

5.1) create table employee as select * from emp where 1=3;
    desc employee;

5.2) select * from employee;
EMPNO	ENAME	JOB    MGR   HIREDATE 	SAL 	COMM 	DEPTNO
7369	SMITH	  	  	  	800 	  	20
7499	ALLEN	  	  	  	1600 	  	30
7521	WARD	  	  	  	1250 	  	30
7566	JONES	  	  	  	2975 	  	20
7654	MARTIN	  	  	  	1250 	  	30
7698	BLAKE	  	  	  	2850 	  	30
7782	CLARK	  	  	  	2450 	  	10
7788	SCOTT	  	  	  	3000 	  	20
7839	KING	  	  	  	5000 	  	10
7844	TURNER	  	  	  	1500 	  	30
7876	ADAMS	  	  	  	1100 	  	20
7900	JAMES	  	  	  	950 	  	30
7902	FORD	  	  	  	3000 	  	20
7934	MILLER	  	  	  	1300 	  	10

5.3) update table employee set job = (select job from employee where empno = 7788), dept no = (select detno from employee where empno = 7788) where empno = 7698;

5.4) alter table employee drop column "sales";

5.5) update employee set deptno =(select deptno from employee where empno = 7698)where empno= 7788;

5.6) insert into employee values(&empno,'&ename','&job',&mgr,'&hiredate',&salary,&comm,&deptno);

6.1) insert into customermaster value(&customerid, &customername, &gender, &age, &phoneno);

6.2) savepoint SP1;

6.3) insert into customer_table values(6003, 'John', '#114 Chicago', '#114 Chicago ', 'M',45, 439525,1900.60'; 

6.4) rollback p1;
