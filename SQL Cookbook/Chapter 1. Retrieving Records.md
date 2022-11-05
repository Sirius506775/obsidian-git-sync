
1.1 Retrieving All Rows and Columns from a Table



* AS 키워드를 사용하여 query에서 반환된 column에 새 이름을 지정하는 것을 해당 열의 aliasing이라고 하며, 지정한 새 이름을 alias라고 한다. 
* 좋은 별칭을 만들면 쿼리와 그 결과를 다른 사람이 이해하는 데큰 도움이 될 수 있다. 


Alias가 있는 쿼리를 인라인 뷰에 배치하면 외부 쿼리에서 alias column을 참조할 수 있다. 



> where 절은 select 절을 시행하기 전에 판단된다..!
> from절은 where절보다 먼저 평가됩니다. 

---

### 1.7 Concatenating Column Values

열 값을 이어붙여서 하나 열로 반환하려면 DBMS에서 제공하는 내장함수(built-in function)를 사용한다. 

##### DB2, Oracle, PostgreSQL 
These databases use the double vertical bar as the concatenation operator
```sql
1 select ename||' WORKS AS A '||job as msg 
2 from emp 
3 where deptno=10
```
``
##### MySQL 
This database supports a function called CONCAT
```sql
1 select concat(ename, ' WORKS AS A ',job) as msg 
2 from emp 
3 where deptno=10
```

##### SQL Server 
Use the + operator for concatenation: 
``` sql
1 select ename + ' WORKS AS A ' + job as msg 
2 from emp 
3 where deptno=10
```

---

### 1.8 Using Conditional Logic in a SELECT Statement

select문에서 조건문을 사용하려면 CASE식을 사용한다. 

```sql
1 select ename,sal, 
2        case when sal <= 2000 then 'UNDERPAID' 
3        when sal >= 4000 then 'OVERPAID' 
4        else 'OK' 
5        end as status 
6 from emp
```

else절은 선택사항이며, 생략할 시에는 case식은 조건에 부합하지 않은 행에 대해 NULL을 반환한다.

---

### 1.9 Limiting the Number of Rows Returned

반환되는 행 수를 제한하려면 내장 함수를 사용해야한다. 

##### DB2 
In DB2 use the FETCH FIRST clause:
```sql
1 select * 
2   from emp fetch first 5 rows only
```

##### MySQL and PostgreSQL 
Do the same thing in MySQL and PostgreSQL using LIMIT:
```sql
1 select * 
2   from emp limit
```

##### Oracle 
In Oracle, place a restriction on the number of rows returned by restricting ROW‐ NUM in the WHERE clause:
```sql
1 select * 
2   from emp 
3 where rownum <= 5
```

>**오라클에서 사용하는 rownum이라는 함수는 반환되는 각 행에 대해 숫자를 반환한다는 점이 다른 sql과 다르다. (1에서 증가하는 증갓값이다.)


##### SQL Server 
Use the TOP keyword to restrict the number of rows returned
```sql
1 select top 5 * 
2   from emp
```
---


```sql

```