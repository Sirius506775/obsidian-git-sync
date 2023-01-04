# 1. JBDC 프로그램 구성
1. DataBase 설치 및 사용자 계정과 권한 추가
2. Java와 DB 간의 연동을 위해 JDBC 드라이버 설치 (**dependency**)
	- (+) DB 연결 확인을 위한 테스트 코드 작성
3. 신규 Table 생성[]
4. lombok 라이브러리 설정(**dependency**)
	- getter setter 등의 생성 혹은 생성자 함수를 자동으로 정의하기 위함 
	- (+) 테스트 환경에서도 사용하기 위해 testCompileOnly와 testAnnotationProcessor 설정 추가 
```java
testCompileOnly 'org.projectlombok:lombok:1.18.24'  
testAnnotationProcessor 'org.projectlombok:lombok:1.18.24'
```
6. VO 클래스 생성
	- DB에 있는 테이블의 데이터를 Java 객체로 처리하기 위한 VO 클래스(읽기 전용)  
7. HikariCP 설정(**dependency**)
	- (+) CP를 통해서  Connetion 객체가 생성되는지 확인 테스트 코드 작성 
8. DAO 클래스 생성 및 기능 구현

# 2. MVC와 JDBC 결합
JDBC를 이용해서 DAO를 구성했다면 서비스 객체와 컨트롤러 객체를 연동한다.
1. DTO 클래스 생성
2. modelMapper 라이브러리 설정(**dependency**)
	- DTO <-> VO 변환을 위해 modelMapper 사용
```java
// https://mvnrepository.com/artifact/org.modelmapper/modelmapper  
implementation group: 'org.modelmapper', name: 'modelmapper', version: '3.1.0'
```
3. Service 클래스 생성
	- (+) VO와 DTO를 사용하는 Service에서 modelMapper의 동작을 확인하는 테스트 코드 작성
4. 문제해결을 위한 로그를 확인하기 위해 Log4j2 라이브러리 설정(**dependency**)
	- (+) Lombok과 마찬가지로 테스트 환경에서 사용가능하게끔 설정 추가
5. resouse 폴더 내에 Log4j2.xml 설정파일 생성
6. Controller 클래스 생성
7. JSP에서 사용할 JTSL 라이브러리 설정(**dependency**)
8. 목록 기능
9. 등록 기능
10. 조회 기능
11. 수정 및 삭제 기능


