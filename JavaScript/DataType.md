##### 8 Type
---
- Primitive Type
	- number : 모든 수가 실수
	- string : 문자열
	- boolean : true or false
	- undefinded: var keyword로 선언된 변수에 암묵적으로 할당되는 값
	- null : 값이 없다는 것을 의도적으로 명시
	- symbol (ES6) 
	- Bigint (ES11) : 숫자값 표현 최대치보다 큰 정수를 표현
		- 정수 리터럴 뒤에 n을 붙이거나, Bigint함수 호출 
		- Example) 10n or Bigint(10)
- Object/reference Type
	- object, function, array


- NaN : 산술 연산 불가
- Infinity /-Infinity : 양/음의 무한대

##### String
- JS에서 string은 primitive type이며, immutable value이다. 
> '' / "" / ``
- 따옴표로 감싸지 않으면 keyword나 idenfier와 같은 token으로 인식함

##### Templete literal(ES6)

- 템플릿 리터럴은 런타임에 일반 문자열로 변환되어 처리된다. 
- multi-line string, expression interpolation, tagged templete 등이 가능하다. 

- 일반 문자열 내에서는 줄바꿈(개행)이 허용되지 않는다. 따라서 일반 문자열 내에서 줄바꿈 등의 공백(white space)을 표현하려면 백슬래시( \ )로 시작하는 escape sequence를 사용해야한다. 

1. Multi-line string(멀티라인 문자열)
```javascript
var templete = '<ul>\n\t<li><a href="#">Home</a></li>\n</ul>';

console.log(templete)

/* console : 

<ul>

    <li><a href="#">Home</a></li>

</ul>

*/
```

하지만 템플리 리터럴 내에서는 이스케이프 시퀀스를 사용하지 않아도 줄바꿈과 공백이 그대로 적용된다. 
```javascript
var templete = `<ul>

<li><a href="#">Home</a></li>

</ul>`;

  

console.log(templete)

  

/*

<ul>

    <li><a href="#">Home</a></li>

</ul>

*/
```

2.  Expression interpolation(표현식 삽입)
- 표현식 삽입은 ${ }으로 표현식을 감싼다. 이때 evaluate 결과가 string이 아니더라도 string으로 강제변환 되어 삽입된다. 

``` javascript
var first = 'dong-heon';

var last = 'lee';

  

console.log(`My name is ${first} ${last}.`);

  
  

/* console :

My name is dong-heon lee.

*/
```


#### Undefinded Type
- 개발자가 의도적으로 할당하기 위한 값이 아니라 JS 엔진이 변수를 초기화할 때 사용하는 값이다. 
- 의도적으로 변수에 할당한다면 undefinde의 본래 취지에 맞지 않을 뿐더러 혼란을 야기할 수 있기 때문에 지양한다. 

> ! C언어 같은 경우 선언과 정의의 개념이 명확하나, JavaScript에서는 declaration과 definition이 불명확하다. ECMAScript 사양에서는 변수는 '선언한다'라고 표현하고, 함수는 '정의한다'라고 표현한다.

#### null Type
- Intentional absence(의도적 부재)할 때 사용한다. 
- 변수에 null을 할당하겠다는 것은 변수가 이전에 참조하던 값을 더이상 참조하지 않겠다는 의미

#### symbol Type
- 변경 불가능한 primitive value. 
- 주로 이름이 충돌될 위험이 없는 객체의 유일한 property key를 만들기 위해 사용한다.
- 심벌 이외의 primitive value는 literal를 이용해 생성하지만, symbol은 Symbol 함수를 호출해 생성한다. -> 생성된 값은 외부에 노출되지 않는 중복되지 않는 유일무이한 값


##### 데이터 타입의 필요성
- 자바스크립트 엔진은 데이터 타입에 따라 정해진 크기의 메모리 공간을 allocate한다. => 변수에 할당되는 값의 타입에 따라 확보해야할 메모리 크기가 결정된다는 말이다. 

ECMAScript 사양은 숫자 타입은 배정밀도 64비트 부동소수점 형식(=8바이트)이다.

메모리 셀의 크기가 8바이트를 확보한다. 

- `typeof` 연산자는 피연산자의 데이터 타입을 문자열로 반환한다. 
	- 변수의 데이터 타입이 아니라 변수에 할당된 값의 데이터 타입


자바스크립트는 C나 JAVA와 같은 정적 타입 언어가 아니다. 
JS는 값을 할당하는 시점에 변수의 타입이 동적으로 결정되고 변수의 타입을 언제든 자유롭게 변경 가능하다. 


>- 자바스크립트의 변수는 선언이 아닌 할당에 의해 타입이 결정(타입 추론 type inference)된다. 
>- 재할당에 의해 변수의 타입은 언제든지 동적으로 변할 수 있다. 

이러한 특징을 동적 타이핑 (Dynamic typing)이라고 한다.
JavaScript는 dynamic / weak type 언어라고 한다. 


** 기본적으로 변수는 타입을 값지 않는다. 다만 변수에 할당된 값의 의해서 변수의 타입이 동적으로 결정된다고 보는 것이 적절하다. ** 


- 여기서 알아야할 점은 동적타입 언어는 유연성과 신뢰성이 떨어진다는 단점이 있는 것이다. 

=> 때문에 변수를 사용할 때 주의할 점
> - 변수의 무분별한 남발은 금물이다. 필요한 경우에 제한적으로 사용한다.
> - 변수의 스코프는 최대한 좁게 만들어서 부작용을 억제하라. [#스코프]
> - 전역변수는 최대한 사용하지 않도록 한다. [#전역변수]
> - 변수보다는 상수를 사용해 값의 변경을 억제한다. (const 사용)
> - 변수 이름은 명시적으로 네이밍하라. 존재 이유를 파악할 수 있는 이름으로 생성
> 	- 특히 식별자의 스코프가 넓을수록 명확한 이름을 명명 

** 가독성이 좋은 코드가 좋은 코드입니다. **