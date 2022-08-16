
**Chapter2 : JavaScript for React.js**
--

### 2.1 Assignment variable

#### 2.1.1 const

```JavaScript
const pizza = true

pizza = false


console.log(pizza) 
//Assignment to constant variable.
```

#### 2.1.2 let

Now, JavaScirpt provide lexical variable scoping.

```JavaScript 
      const container = document.getElementById('container')

        let div;

        for (let i = 0; i < 5; i++) {

            div = document.createElement('div')

            div.onclick = function(){

                alert('이것은 박스 #' + i + '입니다.')

            }

            container.appendChild(div)
			// var와 달리 let을 사용하면 i의 영역을 제한할 수 있다.
			// 
        }
```

#### 2.1.3 Templete String

```javascript
   let html5 = 'Html5'

   let article = 'article'

   let footer = 'footer'
   
   
   document.body.innerHTML = `

        <section>

            <header>

                <h1>The ${html5} Blog</h1>

            </header>

            <article>

                <h2>${article} body</h2>

            </article>

            <footer>

                <h2>${footer}ter</h2>

                <p>copyrigth</p>

            </footer>

        </section>

        `
```

### 2.2 Creating Functions

#### 2.2.1 Function Declarations and Expressions
```javascript
     today() //enable hosting

  

        //기본 함수 선언

        function today (){

            console.log("Today is 2022 Aug 14")

        }

  

        tomorrow() //disable hosting

  

        //함수 표현식

        const tomorrow = function() { //변수에 값을 대입

            console.log("Tomorrow is 2022 Aug 15")

        }
```

This example is obviously a small example. But, It occurr 'TypeError' when importing files and functions and in a project. So, you should refactor from function to assignment always.

If you see it, you can always refactor as a declaration

#### 2.2.2 Returns, PASSING Arguments
```javascript

        const createCompliment = function(name, message) {

            return `${name}: ${message}`;

        }

  

        console.log(createCompliment('James', 'Hello World!'))
```


#### 2.2.3 Arrow Functions

With arrow functions, you can create functions without using the `function`keyword. You also often do not have to use the `return` keyword. 

```javascript
  

        const lordify = (firstname, land) => {

            if(!firstname){

                throw new Error('lordify에게 name을 넘겨야합니다.')

            }

  

            if(!land){

                throw new Error('land가 없습니다. ')

            }

  

            return `${firstname} is Lord of the ${land} `

        }

  

        console.log(lordify('Eden', 'england'))
```

**Returning Object**

객체를 반환하려면 괄호로 둘러싸면 된다.
To fix this, just wrap the object you’re returning with parentheses


JavaScrit나 React에서 괄호를 빼먹어서 오류가 생기는 경우가 많다..! 꼭 기억할 것..


These missing parentheses are the source of countless bugs in JavaScript and React apps, so it’s important to remember this one!

```javascript
 const person = (firstname, lastname) =>

        ({

            first: firstname,

            last: lastname

        })

  

        console.log('Gerrard', 'Steven')
```

**Arrow Functions and Scope**


화살표 함수와 영역에서
this가 windows 객체라는 것에 대해
자바스크립트의 설계오류라고 지적한 부분이라는 것을 알게되었다.
this 바인딩에 대해서 더 파헤쳐보자


### 2.4 Objects and Arrays
#### 2.4.1 Destructuring Objects

.

```javascript
const lordify = ({ firstname }) => { 
	console.log(`${firstname} of Canterbury`);
}; 
	
const regularPerson = { 
	firstname: "Bill", 
	lastname: "Wilson" 
}; 

lordify(regularPerson); // Bill of Canterbury
```
curly braces : 중괄호 

Using the colon and nested curly braces, we can destructure the firstname from the spouse object

#### 2.4.2 Destructuring Arrays
```javascript
        //Destructring Arrays

        const regularperson =

            {

                firstname: 'dongheon',

                lastname: 'lee'

        }

  

        const [,,secondanimal] = ["캥거루", "코끼리","사자"]

        console.log(secondanimal)
```


#### 2.4.3 Object Literal Enhancement
Object literal enhancement is the opposite of destructuring.


### 2.5 Async JavaScript

#### 2.5.1 단순한 프로미스와 fetch

대기 중인`promise`는 데이터가 도착하기 전의 상태를 표현한다. 
`then()`이라는 함수를 대기 중인 `promise`에 연쇄 호출해야한다.

`then()`은 `promise`가 정상적으로 완료되면 callback function을 한 번만 호출한다. 
	이때 callback 함수가 반환하는 값은 그 다음에 오는 `then()`함수의 콜백에 전달되는 인자가 된다. 
	이말은 즉슨 

Allow Function은 그동안 Js가 
this로 인한 문제들을 해결해주는 장점을 갖고 있다.

this가 항상 원하는 객체를 참조하지 않았던 문제를 
항상 정의한 객체를 나타내고, 실행 중에 갑자기 바뀔 일이 없어진다. 


## Spread & Rest Operators

```javascript
// spread operator

//ex1
const numbers = [1,2,3,4]
const newNumbers = [...numbers, 4, 5,]
console.log(newNumbers) 
//[1, 2, 3, 4, 4, 5]

//ex2
const person = {
  name : 'Max'
};
const newPerson = {
  ...person, //person 객체를 newPerson 객체에 전달
  age: 28
};

console.log(newPerson)
//[object Object] {  age: 28,  name: "Max" }

//Rest operator
const filter = (...args) => {
  return args.filter(el => el > 2)
}

console.log(filter(1,2,3,4,5))
//[3, 4, 5]

```

