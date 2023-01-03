## BOJ codeKata repo

####  vscode 환경 설정

- JavaScript로 백준 풀이를 하려면 입력 환경을 설정해야하기 때문에 사용언어로 node.js를 선택하면 아래와 같은 코드가 필요합니다.

```js
const fs = require("fs");

const filePath = process.platform === "linux" ? "/dev/stdin" : "input.txt";

let stdin = fs.readFileSync(filePath).toString().split("\n");
```

 1. fs 모듈을 추출하여 readFileSync 메소드로 파일을 읽어들입니다. 
 2. 읽어들인 input을 변수로 선언 및 할당하여 toString()과 split() 함수를 사용하여 배열로 저장합니다.

> - Node.js의 built-in file system module fs 
> https://www.w3schools.com/nodejs/ref_fs.asp

```js
const filePath = process.platform === "linux" ? "/dev/stdin" : "input.txt";
```
- 유닉스 기반인 Mac OS와 Linux에는 /dev/stdin를 읽어주면 터미널 상에서 예제를 입력 가능하지만, windows에는 불가능하기 때문에 로컬에서 테스트할 때는 상대경로를 입력해주어야 합니다. 참고로 BOJ 채점환경은 리눅스입니다.

