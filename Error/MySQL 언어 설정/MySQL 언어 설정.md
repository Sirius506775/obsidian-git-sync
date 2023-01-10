
## 문제

세션을 통한 로그인 기능을 구현 하던 중에 insert 쿼리 실행 시 아래와 같은 오류가 발생했다. 

```sql
[22007][1366] (conn=76) Incorrect string value: '\xEC\x82\xAC\xEC\x9A\xA9...' for column `webdb`.`tbl_member`.`mname` at row 1
```


## 추론 

컬럼에 맞지 않는 데이터라는데  `for column `webdb`.`tbl_member`.`mname` at row 1` 라는 걸 보니 해당 에러는 mname의 값이 문제가 되는 것 같다. 

mname에 한글로 된 문자열이 들어간 

```sql
insert into tbl_member (mid, mpw, mname) values ('user00', '1111','사용자0');
```


## 해결방법 

이 에러는 MySQL 언어 설정이 UTF-8이 되어 있지 않아서 생기는 문제이다. 

```sql
ALTER TABLE tbl_member CONVERT TO CHARSET utf8;
```

쿼리 탭에 해당 테이블의 기본 설정을 UTF-8로 바꾸어주고 다시 쿼리를 날리면 정상적으로 데이터가 테이블에 insert 되는 것을 확인할 수 있다. 

![[Pasted image 20230106145828.png]]
