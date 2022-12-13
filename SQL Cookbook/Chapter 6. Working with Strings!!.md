
```sql
create view x as
select concat(
substr(ename,1,2),
replace(cast(deptno as char(4)),' ',''),
 substr(ename,3,2)
 ) as data
 from emp
 where sal <= 1000
 union all
select replace(cast(empno as char(4)), ' ', '')
 from emp where sal <= 2000
 union all
select ename from emp where sal <= 3000

```

1. 위 쿼리문으로 view X를 생성합니다. 
![[Pasted image 20221214001453.png]]
2. 아래와 같이 문자열 하나 하나 살펴보면서 숫자 유무를 판단해보세요. 
![[Pasted image 20221214003553.png]]
3. 다음과 같이 하나 이상의 숫자를 포함하는 10개의 행을 반환해봅시다.(group_concat을 사용해봅시다. )
![[Pasted image 20221214003456.png]]

