Dfingo의 구성: Eclicpse plugin + web application library

#### web application 관점

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

디핑고는 라이브러리 + 오토메이션 model 클래스로 동작
같은 어플리케이션 내에서 디핑고는 스프링에서 호출 가능

같은 인스턴스 내에서 자바로 되어 있으면 jsp든 헬퍼클래스이든 호출가능

---
![[Pasted image 20220817093915.png]]

넥사크로 화면에서 넘어온 파라미터를 data셋을 포함하는 자바 객체로 전환

객체화된 입력 파라미터를 가지고 오토메이션 모델을 호출

![[Pasted image 20220817094041.png]]
최초 모델 생성 시 xam과 java파일 2개가 생성
xam은 flow차트 기반의 업무구현을 수행, 자동생성되는 코드는 BaseAutoMationLogic 자동 생성된다.

xam파일 수정시 baseAuto는 새로 생성되며, 만약 개발자가 BaseAutoMationLogic에 자바 코딩을 하면 사라지게 된다. 
![[Pasted image 20220817094446.png]]
![[Pasted image 20220817094606.png]]
![[Pasted image 20220817094618.png]]
---
## Automation Model
1. 단일유형
	1. start와 end 사이에 하나의 invoke가 놓여지는 형태
	2. Select Invoke
	
![[Pasted image 20220817095506.png]]

2. 복합유형
	1. start와 end 사이에 2개 이상의 인보커가 놓여지는 형태
	2. SAP RFC Function을 호출
	3. DB 테이블을 조회
	4. Select Invokef
	5. 라인을 연결
	
![[Pasted image 20220817095446.png]]

> Example 2 )
첫번째 호출의 결과를 두번째 호출의 입력으로 사용하는 모델 ![[Pasted image 20220817100102.png]]
>1. DB Sequence 값 가져오기 
>2. Select 결과는 dataset 형태로 반환 -> variable로 변환
>3. D to V는 dataSet을 variable list로 변환
>4. Modify invoke 배치
>5. seq 컬럼 값으로 nextval을 설정
>![[Pasted image 20220817100130.png]]

3. 분기 (if구문)
	if구문은 decision 버튼을 이용해 구현 가능


4. Loop 구문
	dataset loop button
	event 추가
	

5. usermethod
6. errorcode / errorMessge ![[Pasted image 20220817101550.png]]
Dfingo는 exception이나 error가 음수인 경우, 롤백을 자동수행

7. Session Object
- UserSession은 HTTPSettion 객체를 wreapping하고 있다.
- invalidate()를 통해 session 객체 파기 가능

![[Pasted image 20220817101821.png]]


** x-up생성한 Autmation Model의 url을 가져와서 nexacro에서 dataset으로 사용가능하다. 
