#### useState Hook
리액트의 컴포넌트가 re-rendering 하는 조건 중 하나는 컴포넌트 안에 있는 state가 변경되었을 경우입니다. 

- useState는 리액트가 컴포넌트들을 모니터링하기 위해 만들어진 개념입니다.
	- state로 데이터를 만들면 리액트가 모니터링을 할 수 있습니다. 
	- 리액트는 컴포넌트의 상태가 변경되었음을 알아야하기 때문에 리액트에서는 useState를 사용하여 상태를 관리합니다. 

- useState는 배열을 반환 하는 호출가능한 함수이다.
	- 함수 실행 시 컴포넌트에 있는 값을 쓰는 것이 아니라 useState를 통해 가져온 배열을 사용하는 것
	- 배열의 첫번째 요소는 초기화된 값이며, 두 번째 값은 초기값을 변경할 수 있는 함수로 구성되어 있습니다.


useState 훅은 실제로 react 패키지에 들어있기 때문에 임포트를 해야한다. 
```js
import React,{ useState } from 'react'
```
useState()에 전달하는 값은 상태 변수의 디폴트 값이다.
```js
const [title, setTitle] = useState(props.title);
```


##### setstate를 검사 하는 작동원리
- setState가 실행이 되면 React는 자기가 원래 가지고 있던 객체랑 setState로 들어온 객체랑 같은 건지 비교를 하는 작업을 거칩니다. ( 때문에 useState를 남발하는 것은 지양)
- 만약 이 2개가 같다면 re-render를 하지 않아도 된다고 판단하고 skip합니다.


> ** change와 change() **
> - change = 변수의 의미
> - change() = 실행한 결과의 의미


state를 다루는 진짜 이유는 Re-rendering을 하기 위해서입니다. 다시 컴포넌트를 뿌려주기 위함이 목적입니다.

##### re-render를 하는 3가지 상황

-   컴포넌트의 state가 변경이 되었을 때
-   props가 변경이 되었을 때
-   상위컴포넌트가 변경이 되어서 re-render가 되면, 하위 컴포넌트도 re-render를 한다.


