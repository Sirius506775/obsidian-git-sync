
`Uncaught ReferenceError: daum is not defined… `

=> js 파일 맨처음에 /_global daum_/를 넣으면 컴파일이 된다. 


---

지도 호출 시 geocoder() 호출 에러
`Cannot read property ‘Geocoder’ of undefined`


https://devtalk.kakao.com/t/react-kakao-maps-cannot-read-property-geocoder-of-undefined/115215

=> import 된 스크립트 안에 공백이 있거나 오타가 있다면 라이브러리를 못불러오기 때문에 발생하는 에러였다. 아래와 같이 첨부해여함.

작성 시 코드샘플을 붙여넣기하다가 발생할 수도 있음

```js
<script type="text/javascript" src="//dapi.kakao.com/v2/maps/sdk.js?appkey=Javascript Key&libraries=services&autoload=false"></script>
```

https://postcode.map.daum.net/guide#attributes