

```shell
npm init gatsby
```

- Start by going to the directory with
```shell
cd my-gatsby-site
```

- Start the local development server 
```shell
npm run develop
```

생성이 완료되면 해당 폴더로 이동하고 실행을 시켜본다. 만약 gatsby-cli가 global로 설정되었다면 gatsby develop을 하고 아니면 npm run develop을 한다.


>***11903 error 발생 시 해결방법
>https://stackoverflow.com/questions/71552122/error-11903-when-developing-first-gatsby-project


locallhost 8080으로 접속하면 sample 확인 


![[Pasted image 20221123162159.png]]

원하는 gatsby theme의 주소를 import한 repo를 만들고 해당 repo를 local에 clone한다

**1. 블로그를 동작시킬 패키지 다운

```bash
cd [Repository 주소]
npm install
```

**2. Blog 배포 준비

그리고 이제 Gatsby 테마를 GitHub 페이지에 올리기 위해 gh-pages 패키지 설치 

```bash
npm install gh-pages --save-dev
```

이후 package.json에 다음을 추가

```json
{
  "scripts": {
    "deploy": "gatsby build && gh-pages -d public" // 추가
  }
}
```

**3. github page에 배포

```bash
npm run deploy
```

조금 기다리신 후에 다음과 같이 `Published`라는 메시지 확인



>**deploy 시 publish가 되지않는 에러 발생! 
>![[Pasted image 20221123202535.png]]
>
>

터미널에 명령어 입력
```shell
git config --global core.longpaths true
```
> https://stackoverflow.com/questions/44307590/how-to-enable-using-git-repository-with-files-with-long-paths-for-all-users

위 에러는 특정 파일 이름이 너무 길 경우에 발생한다.
이와 같은 경우 git의 문제가 아닌 windows의 문제이다. 
windows 파일 이름의 제한이 255자 이기 때문이다. 

위와 같이 파일 이름의 제한을 커널에서 풀어버리는 방법은 권장하는 방법은 아니다.
많은 어플리케이션들이 260자 이상의 파일 경로로 핸들링이 안되는 어플리케이션이 많기 때문이다.

repo 안의 path를 줄이는 것이 best

---


**4. Repository Source Branch 변경하기

마지막으로 GitHub 페이지가 작동하려면 GitHub의 Repository 설정에서 배포 할 Branch를 선택해야 합니다. 이를 위해서 Repository에 있는 Settings를 클릭하고 죄측 메뉴에서 Pages를 클릭하여 Github Pages 설정 페이지로 이동합니다.

deploy가 완료되었다면 
해당 repo의 setting에서 branch를 gh-pages로 변경한다. 

![[Pasted image 20221123203210.png]]

5. 지정된 git path 접속 시 배포된 페이지를 확인할 수 있다. 
![[Pasted image 20221123203557.png]]


---
```shell
  git add *
```

```shell
  git commit -m '[commit message]' *
```

```shell
  git push origin main
```

```shell
  npm run deploy
```

```shell
  
Pages

┌ src/templates/blog-post.js
│ ├   /hello-world/
│ └   ...3 more pages available
├ src/pages/404.js
│ ├   /404/
│ └   /404.html
├ src/pages/index.js
│ └   /
└ src/pages/using-typescript.tsx
  └   /using-typescript/

  ╭────────────────────────────────────────────────────────────────╮
  │                                                                │
  │   (SSG) Generated at build time                                │
  │ D (DSG) Deferred static generation - page generated at runtime │
  │ ∞ (SSR) Server-side renders at runtime (uses getServerData)    │
  │ λ (Function) Gatsby function                                   │
  │                                                                │
  ╰────────────────────────────────────────────────────────────────╯

Published

```