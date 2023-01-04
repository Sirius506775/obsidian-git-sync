- IDE : InteliJ

1.  jdk download
2. new project할 때 version은 javaEE로 한다.  
jakarta에 맞춘 폴더구조가 아직 익숙치않음.
3. 동적 정적 데이터 송수신을 위한 웹서버가 필요함
was가 필요한데 우리는 tomcat server를 설치 
4. 프로젝트 생성
	1. templet은 web Application 선택
	2. application server는 기존에 다운 받은 tomcat 파일을 압축 푼 path로 설정
	3. build 도구는 gradle 

4. UTF-8 설정
- help-vmOptions에 들어가서 아래 코드 추가
```
-Xmx2011m
-Dfile.encoding=UTF-8
-Dconsole.encoding=UTF-8
```

5. 서버 구동 설정
	1. run configuration에 들어가서 .war로도 배포가 export가 가능하게끔 deployment에서 exploded 버젼으로 변경
	2. Application context도 가장 기본적인 '/'로 변경
	3. 서버가 자동으로 update 되기 위해 update classes and resources 설정으로 모두 변경

