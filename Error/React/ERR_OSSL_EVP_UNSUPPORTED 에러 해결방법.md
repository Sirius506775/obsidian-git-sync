```shell
  -loader\lib\index.js:59:103 {
  opensslErrorStack: [ 'error:03000086:digital envelope routines::initialization er  library: 'digital envelope routines',
  code: 'ERR_OSSL_EVP_UNSUPPORTED'
}
```

서버 구동 시 잘되던

사용 중이던 모듈 중 하나 혹은 일부가 OpeenSSL 버젼 규격에 맞지 않을 때 발생한다. 

node 업그레이드 했을 때 보통 발생한다..

```shell
npm audit fix --force
```

++ <base href=“URL

		<base> 태그의 href 속성은 페이지 내의 모든 상대 주소(relative URL)들의 기본 URL을 명시합니다.
<base href=“URL”>