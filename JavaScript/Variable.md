

## Variable ( memory address + value)

##### What is the Variable
It's Assignment that save value in variable. and Reference(참조) is reading value in variable 


##### Identifier
Identifier is Variable's name and it remember memory address. not value.


##### Variable declaration
It's Variable Declaration that create variable.
> To additional
> - 1. To allocate memory context 
> - 2. To name binding for save value 

** Variable declaration에 의해 allocate된 memory context는 allocate가 release 되기 전까지는 누구도 사용할 수 없도록 보호된다. **

Var keyword의 단점은 대표적인 것은 block-level scope가 아닌 function-level scope를 지원한다는 것이다. 

ES6 is a superset to ES5

All of the Indentifier register on execution context.

var keyword는 Declaration와 intialization은 동시에 진행된다. undefined라는 primitive value가 기본적으로 저장되기 때문이다. 

JS code는 인터프리터에 의해서 순차적으로 읽어내지만, 변수 선언은 런타임이 아닌 그 이전 단계에서 먼저 실행되기 때문에 참조 에러가 발생하지 않는다. 


##### Variable declaration의 실행 시점과 Hoisting
자바스크립트 엔진은 런타임 이전에 소스코드의 평가 과정을 거친다. 
그떄, 변수 선언을 포함한 모든 선언문을 소스코드에서 찾아내 먼저 실행한다.
그리고 평가과정이 끝나면 선언문을 제외한 소스코드를 순차적으로 실행한다. 

Variable declaration statement가 코드의 선두로 끌어 올려지는 것처럼 동작하는 JS 고유의 특징을 Variable Hoisting이라고 한다. 

모든 식별자는 호이스팅된다. 

##### Assignment
```javascript
var score // 변수 선언
score = 90; //값의 할당


var score = 80; //변수 선언과 값의 할당
```
하나의 문으로 단축시켜도 JS 엔진은 선언과 할당을 2개의 문으로 나누어 실행한다. 
undefined에서 80으로 재할당됌

** variable의 declaration과 assignment의 시점은 다르다. **

선언은 런타임 이전에 실행되지만, 할당은 런타임에 발생한다. 

> ! 변수에 값을 할당할 때 이전 메모리 공간을 지우는 것이 아니라 새로운 메모리 공간을 확보하고 저장한다는 것을 주의하자.

> ** garbage collector ** 
> - 어플리케이션이 allocate한 memory context를 주기적으로 검사하여 더이상 사용하지 않는 memory(어떤 indentifier도 참조하지않는 공간)를 release하는 기능이다. JavaScript 또한 managed language이기 때문에 가비지 콜렉터를 통해 memory leak을 방지한다. 

##### Identifier Naming Convention

특수기호를 포함한 문자 , _ , $ 시작가능 / 숫자로 시작 불가능 

- ,로 구분해 한 statement에서 여러 개를 declaration 할 수 있으나, 가독성이 나빠지므로 권장하지 않음. ex ) ` var person, $elem, _name, dirl_; `


변수 선언에 별도의 주석이 필요하다면 변수의 존재 목적을 명확히 드러내지 못하는 것이다. 

JS에서는 일반적으로 variable이나 function의 이름은 카멜케이스를 사용하고, 생성자 함수, 클래스 이름에는 파스칼 케이스를 사용하고 있다. 

=> ** 코드 가독성을 높이려면 카멜 케이스와 파스칼 케이스를 따르는 것이 유리하다. ** 