Dfingo의 구성: Eclicpse plugin + web application library

#### 

![[Pasted image 20220817093237.png]]

Spring과 Dfingo를 같이 쓰는 것을 권장

관리 포인트가 늘어나서
관리를 쉽게하려는 관점에서는 서블릿에서 디핑고를 바로 사용하는 것을 추천

AutomationModel
은 서비스의 단위

스프링에서는 업무를 서비스에서 구현하고, DB연동은 DAO

구현 내용 : 
비즈니스 로직, DB 

#### spring 관점

![[Pasted image 20220817093647.png]]
