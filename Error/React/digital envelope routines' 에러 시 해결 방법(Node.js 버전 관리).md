서버가 켜지지 않는 이슈

https://velog.io/@hongihongi60/Error-error0308010Cdigital-envelope-routinesunsupported


node 버젼이 최신이라서 생기는 문제


해결방안
case 1: 
```js
"start": "react-scripts --openssl-legacy-provider start"
```
-> 일시적인 해결책일뿐 --openssl-legacy-provider를 사용하는 건 안전하지 않는 ssl이다. 근본적인 문제를 해결하지 못함

해결방법을 더 찾아보자