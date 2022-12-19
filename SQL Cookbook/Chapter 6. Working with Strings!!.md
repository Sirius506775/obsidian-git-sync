##### 내가 만든 문제

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

----------------------------------------------------------------------

- Solution
```sql

/* 문자열 하나 하나 살펴보면서 숫자 유무를 확인해봅시다.*/
select x.data, iter.idx, substr(x.data,iter.idx,1) as a
 from x,
( select id idx from t10 ) iter
 where iter.idx <= length(x.data) 
order by 1,2

 /* 하나 이상의 숫자를 포함하는 행을 반환 */
 select cast(group_concat(a order by pos separator '') as unsigned)
 as result
 from ( 
select x.data, iter.pos, substr(x.data,iter.pos,1) as a 
 from x, 
 ( select id pos from t10 ) iter 
 where iter.pos <= length(x.data) 
 and ascii(substr(x.data,iter.pos,1)) between 48 and 57
 ) y
 group by data
 order BY 1

```

---
퀴즈로 푼 문제 
![[Pasted image 20221219133938.png]]

- Solution
```sql

/* 
	Chapter.6 문제 : dept 테이블의 dname(사원 이름)에서 각각의 개별 문자를 알파벳순으로 지정해라. 
*/

select dname AS OLD_NAME, group_concat(c order by c SEPARATOR '') AS NEW_NAME
from (
select dname, substr(a.dname,iter.pos,1) c /* substr()으로 DNAME의 문자들을 하나씩 추출*/
from dept a,
( select id pos from t10 ) iter /* 문자열을 순서대로 이동하기 위해 t10 테이블을 사용해서 iter 뷰 생성 */
where iter.pos <= length(a.dname)
) x
group by dname;

/* GROUP_CONCAT 함수를 사용 */
/* inline view X는 DNAME의 각 문자를 행으로 반환*/
```


