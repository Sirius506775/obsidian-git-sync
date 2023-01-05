Fetch 와 axios는 모두 promise 기반의 HTTP 클라이언트입니다. 즉 이 클라이언트를 이용해 네트워크 요청을 하면 이행(resolve) 혹은 거부(reject)할 수 있는 promise가 반환됩니다.

- fetch 요청은 필요한 JSON 데이터의 포맷을 얻기 위해 일반적으로 두 개의 .then() 호출을 갖는 반면, Axios는 응답 데이터를 기본적으로 JSON 타입으로 사용할 수 있다. 

-   fetch로 post 요청을 할 경우에는 `JSON.stringify()`를 사용하여 객체를 문자열로 변환한 뒤 본문에 할당해야하는 반면, Axios는 자동으로 데이터를 문자열로 변환해줍니다.
    
-   fetch는 HTTP 에러 응답을 받았다고 해서 프로미스를 거부하지 않고 네트워크 장애가 발생한 경우에만 거부하는 반면, Axios는 상태코드가 2xx의 범위를 넘어가면 거부합니다.
    
-   두 클라이언트 모두 비동기이기 때문에 크게 중요하지 않을 수 있지만 fetch 가 Axios 보다 살짝 더 빠릅니다.

```js
fetch(url, {
  method: "GET", //(POST, PUT, DELETE, etc.)
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify({}),
});
```

```js
axios(url, {
  method: "get", 
  headers: {},
  data: {},
});
```


### 에러 처리

Fetch와 axios는 모두 이행(resolve) 되거나 거부(reject)된 promise를 반환합니다. Promise가 거부(reject)되면 `.catch()`를 사용하여 에러를 처리할 수 있습니다. Axios로 에러를 처리하는 방법은 Fetch에 비해 더 간결합니다.

Axios부터 살펴보면, `.catch()`를 사용한 일반적인 에러 처리는 다음과 같습니다.

```js
const url = "https://jsonplaceholder.typicode.com/todos";

axios
  .get(url)
  .then((response) => console.log(response.data))
  .catch((err) => {
    console.log(err.message);
  });
```

Axios의 promise는 상태코드가 2xx의 범위를 넘어가면 거부(reject)합니다. 에러 객체에 응답(response) 또는 요청(request) 프로퍼티가 포함되어 있는지 확인하여 에러에 대한 자세한 정보를 확인할 수 있습니다.

```js
.catch((err) => {
// 에러 처리
if (err.response) {
// 요청이 이루어졌고 서버가 응답했을 경우

    const { status, config } = err.response;

    if (status === 404) {
      console.log(`${config.url} not found`);
    }
    if (status === 500) {
      console.log("Server error");
    }

  } else if (err.request) {
    // 요청이 이루어졌으나 서버에서 응답이 없었을 경우
    console.log("Error", err.message);
  } else {
    // 그 외 다른 에러
    console.log("Error", err.message);
  }
});
```

에러 객체의 `response` 프로퍼티는 클라이언트가 2xx 범위를 벗어나는 상태 코드를 가진 에러 응답을 받았음을 나타냅니다. 에러 객체의 `request` 프로퍼티는 요청이 수행되었지만 클라이언트가 응답을 받지 못했음을 나타냅니다. 요청 또는 응답 속성이 모두 없는 경우는 네트워크 요청을 설정하는 동안 오류가 발생한 경우입니다.


### 응답 시간 초과 / 요청 취소

각각의 HTTP 클라이언트에서 HTTP 요청이 시간 초과될 경우 어떻게 처리하는지 살펴봅시다. Axios에서는 `timeout` 속성을 설정 객체에 추가하여 요청이 종료될 때까지의 시간을 밀리초로 지정할 수 있습니다.

다음 코드 스니펫에서는 만약 요청이 4초 이상 걸릴 경우에 종료하고 console창에 error를 로깅하고 있습니다.

```js
const url = "https://jsonplaceholder.typicode.com/todos";

axios
  .get(url, {
    timeout: 4000, // 기본 설정은 '0'입니다 (타임아웃 없음)
  })
  .then((response) => console.log(response.data))
  .catch((err) => {
    console.log(err.message);
  });
```

Fetch를 통한 요청을 취소하기 위해서는 [AbortController 인터페이스](https://developer.mozilla.org/en-US/docs/Web/API/AbortController)를 사용할 수 있습니다. 다음과 같이 사용할 수 있습니다.

```js
const url = "https://jsonplaceholder.typicode.com/todos";

const controller = new AbortController();
const signal = controller.signal;
setTimeout(() => controller.abort(), 4000);

fetch(url, {
  signal: signal,
})
  .then((response) => response.json())
  .then(console.log)
  .catch((err) => {
    console.error(err.message);
  });
```

`controller` 객체를 생성하고나서 `signal` 객체와 `abort()` 메서드에 접근했습니다. 이 `signal`객체를 설정 옵션을 통해 `fetch()`에 넘깁니다. 이렇게 하면 abort 메서드가 호출될 때마다 fetch 요청이 종료됩니다. 보시다시피 `setTimeout` 기능을 사용하여 서버가 4초 이내에 응답하지 않으면 작업이 종료됩니다.

**참고**
- https://meticulous.ai/blog/fetch-vs-axios/