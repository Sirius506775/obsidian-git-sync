
#### 호출부

this는 Call-Site에서 함수를 호출할 때 바인딩된다.

호출부를 파악하려면 먼저 호출 스택을 확인하는 곳이 용이하다. 

this 바인딩은 오직 호출부와 연관되기 때문에 코드를 유심히 살펴봐야한다.

** 브라우저 혹은 개발환경의 디버깅 콘솔로 Call-Stack을 추적해보자 ** 


#### 2.2 Binding Rules
1. Default Binding
첫 번째 규칙은 Standalone Function Invocation(단독 함수 실행)이다. 가장 기본적인 this의 규칙이다. 
```javascript
function foo(){

    console.log(this.a)

}

var a = 2; //전역 스코프에 변수를 선언하면 변수명과 같은 이름의 전역 객체 프로퍼티가 생성된다. (! 사본이 아니다.)

  

foo() //호출 시 this.a는 전역객체 a
//기본 바인딩이 되어 this는 전역객체를 참조한다.
```

But, strict mode에서는 전역 객체가 기본 바인딩 대상에서 제외된다.
이때 this는 undefinded가 된다. 
```
-   "error"
    
-   "TypeError: Cannot read properties of undefined (reading 'a')
```
(! Non-strict-Mode에서는 위 예제에서는 전역 객체만이 기본 바인딩의 유일한 대상이 된다. )

2. Implicitly Binding(암시적 바인딩)

객체는 함수 호출 시점에 함수의 레퍼런스를 소유하거나 포함한다고 말할 수 있다.
콘텍스트 객체가 함수 호출 시 this에 바인딩 된다. 
```javascript
function foo(){

    console.log(this.a)

}

var obj ={

    a:2,

    foo:foo //foo()함수를 property로 참조하고 있으나, 정말로 갖고 있는 것은 x
    

}

obj.foo() //obj 콘텍스트로 foo()를 참조하기 때문에
//호출 시점에서 foo()의 레퍼런스를 owning/containing한다고 볼 수 있다.
```

3. 명시적 바인딩

