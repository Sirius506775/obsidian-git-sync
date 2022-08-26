##### React에서 input태그를 사용하는 방법
- input태그는 사용자가 입력을 해도 컴포넌트가 변하지 않습니다. re-rendering이 일어나지 않습니다. 


##### 1. useRef를 사용하는 방법 (권장하지 않음)
- id를 사용하지 않고 대신 ref를 사용하는 방법입니다. 
- ref를 만드는 이유는 DOM 요소를 사용해야할 경우에 사용하기 위함입니다. ( 빈도 수는 적음)
- input 태그는 빈 곳에 입력을 하거나, 이미 있던 내용을 보여주기 위함의 2가지 목적이 있다는 것을 기억해보면 이 방법은 추천하지 않습니다.


##### 2. state를 사용하는 방법
- value는 re-rendering이 안되기 때문에 일반적으로 input태그를 쓸때는 ref가 아니라 state로 빼라고 말하곤 합니다.
- 사용자가 입력을 하면 그 입력값을 가지고 state를 변경해서 다시 렌더링을 하며 이떄 `onChange` 함수를 사용합니다.
```js
import React, {useState} from 'react'; 

const InputEx2 = () => { 
	const [text,setText] = useState('A') 
	
	return ( 
		<div> 
			<input type='text' value={text} onChange={(e) => {setText(e.target.value)}}/>  
			//onChange() method를 사용해서 setText으로 state를 변경할 수 있다
			</div> 
		); 
}; 
	
export default InputEx2;
```


=> 하지만 실제로 외부에서 작업할 때에는 React의 input를 효과적으로 하기위해 만든 수많은 플러그인을 사용한다는 것을 기억하자...!