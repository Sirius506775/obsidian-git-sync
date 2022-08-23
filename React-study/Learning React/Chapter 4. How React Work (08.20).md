#### React의 작동 원리

리액트는 브라우저 DOM을 갱신해주기 위해서 만들어진 라이브러리입니다. 

리액트를 사용하면서 우리는 코드로 DOM API를 직접 조작하지 않게 되었습니다. 그렇기 때문에 더이상 Single Page Application을 만들면서 효율적으로 처리를 하기 위해 복잡한 코드를 작성할 일이 없습니다. 

리액트에서 어떤 UI를 생성할지 지시하면, 명령에 맞춰 원소 렌더링을 조절해준다.

브라우저에서 리액트를 사용하려면 2가지의 라이브러리가 필요하다 .

React Element  is more faster than DOM elements use DOM API.


virtual DOM that was JavaScript object
> React : 뷰를 만들기 위한 라이브러리
> ReactDOM은 UI를 실제로 브라우저에 렌더링할 때 사용하는 라이브러리

----


- `React.createElement` 
```js
React.createElement("h1", { id: "recipe-0" }, "Baked Salmon");
```

The first argument of defines the type of element we want to create. 

The seconde argument represents the element's properties. 

The third argument represents the element's children: any nodes that are inserted between the opening tag and closing tag.

During rendering, React will convert this elements to an actual DOM element.

``` js
<h1 id="recipe-0">Baked Salmon</h1>
```

** A React element is just a JavaScript literal that tells React how to construct the DOM element. **

If we were to log this element, it would look like this:

```js
{
	$$typeof: Symbol(React.element),
	"type": "h1",
	"key": null,
	"ref": null,
	"props": {id: "recipe-0", children: "Baked Salmon"},
	"_owner": null,
	"_store": {}
	}
```
{

##### ReactDOM