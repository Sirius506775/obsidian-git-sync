### Components

Reusabiliity building block

각각의 컴포넌트를 구축하고 리액트에게 최종 UI에서 어떻게 구성할 것인지 명령

Main Topic => Reusabiliity + Separation of Concerns

![[Pasted image 20220820123512.png]]

##### How is a Component Built
- React allows you to create re-useable and reactive components consisting of HTML and JavaScript(and CSS)
- React uses somthing which is call a Declarative Approach for building components

```js
const para = document.createElement('p')

  para.textContent = 'This is also visible!'

  document.getElementById('root').append(para)
```

=>

```js
function App() {

  

  return (

    <div>

      <h2>Let's get started!</h2>

      <p>This is also visible!</p>

    </div>

  );

}

export default App;
```

![[Pasted image 20220820130958.png]]

App.js is Root components.