---
layout: post
title: "푸드 레시피 앱 문서 정리"
---

## 코드는 재산이다, 나중에 도움된다, 정리잘하자

```js

목적
- 자신의 레시피를 등록하고 불러올 수 있도록 함
- 플랫폼의 모든 사람이 만든 레시피를 키워드 검색으로 해당 레시피를 찾을 수 있도록 함
- 레시피 및 사용자 정보를 데이터 베이스에 저장하여 관리


Food Recipe App Skill set
-Server- NodeJs, Express, MongoDB, Cloudinary(이미지 설치)
-Client- ReactJs, React Context, SWR (data fetching library), React Router dom v6

진행 및 설치
-1- yarn init -y
-2- yarn add express (express는 nodejs에서 사용할 수 있는 웹 프레임워크)
-2-02- helmet (helmet은 보안을 위한 패키지)
-2-03 cors (cors는 다른 도메인에서 요청을 보낼 수 있게 해주는 패키지)

-3- yarn add -D @types/node 
-3-02- @types/express
-3-03- @types/helmet
-3-04- @types/cors

-4- yarn add -D typescript
-4-02- ts-node (typescript를 nodejs로 실행시켜주는 패키지)

-5- npx tsc --init (tsconfig.json 생성)

-6- tsconfig setting

-7- yarn add -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin eslint-config-prettier

-8- npx eslint --init
-8-02- eslint.json setting

-9- package.json script setting
ex code
"scripts": {
    "dev": "npx nodemon",
    "start": "yarn run build && node ./build/index.js",
    "build": "rimraf ./build && tsc", // build folder delete
    "lint": "npx eslint --ignore-path .gitignore --ext .js,.ts --fix", // 파일 무시
    "format": "npx prettier --ignore-path .gitignore --write \"**/*.+(js|ts|json)\""
  }

-9- yarn add -D nodemon (nodemon은 서버를 자동으로 재시작해주는 패키지)
-9-02- nodemon.json 생성 후 setting

-10- yarn add rimraf (rimraf는 윈도우에서 rm -rf 명령어를 사용할 수 있게 해주는 패키지)
-10-02- yarn build 로 build 폴더 생성 확인 후 삭제 (rimraf ./build)

-11- yarn add -D dotenv (dotenv는 환경변수를 사용할 수 있게 해주는 패키지)
-11-02- .env 생성 후 setting (PORT number)

-12- index.ts 에 express server 설정 및 생성 후 실행 (yarn dev)

-13- mongoDB 데이터 베이스 생성 후 연결 (DB_URL)
-13-02- .env 파일에 DB_URL 추가

-14- yarn add mongoose (mongoose는 mongoDB를 사용하기 위한 패키지)

-15- src/models 폴더 생성 후 User.ts, Recipe.ts 생성 후 user,recipe 인터페이스 type 정의 후 스키마 작성
-15-02- src/index.ts 에서 import { User, Recipe } from './models' 추가
-15-03- src/models/index.ts 파일에  export { User, Recipe } 추가해 User, Recipe 내보내기 설정

-16- routes 폴더 생성 후 auth.ts, recipe.ts 생성 후 라우터 작성해서 내보내고 routes 폴더내에 index.ts 에서 모든 라우터를 import 해서 내보냄
-16-02- src/index.ts 에서 import authRouter, recipeRouter from './routes' 추가
-16-03- src/index.ts 에서 app.use() 로 /auth, /recipe 경로 추가

-17- src/controllers 폴더 생성 후 auth.ts, recipe.ts 생성 후 컨트롤러 작성해서 내보내고 controllers 폴더내에 index.ts 에서 모든 컨트롤러를 import 해서 내보냄
-17-02- src/routes 폴더내에 auth.ts 에 import {registerOrLogin} from '../controllers' 추가해 , controllers 에서 내보낸 별칭 registerOrLogin 을 url 경로 localhost:4000/auth/join 입력 시 registerOrLogin 에서 보낸 함수 실행결과 리턴 값 출력 확인 완료(postman 으로 확인)

-18- yarn add yup (yup은 데이터 유효성 검사를 위한 패키지)
-18-02- yarn add -D @types/yup (yup의 타입스크립트 타입을 사용하기 위한 패키지)

-19- src/schema-validations 폴더 생성 후 index.ts 에 다운로드 받은 yup 활용해 레시피 등록 시 필요한 데이터 유효성 검사 스키마 작성 후 내보내기(레시피 등록 유효성 검사 스키마, 단일 레시피 조회 유효성 검사 스키마, 레시피 검색 유효성 검사 스키마, 사용자 레시피 조회 유효성 검사 스키마)

-20- 비밀번호 암호화를 위해 yarn add bcrypt (bcrypt는 비밀번호 암호화를 위한 패키지), yarn add -D @types/bcrypt (bcrypt의 타입스크립트 타입을 사용하기 위한 패키지)
-20-02- 데이터 베이스에 등록된 유저 비번과 클라이언트에게 전달받은 비번이 일치 하지 않을 경우 에러 메세지 출력 (비밀번호 암호화를 위해 bcrypt.compare() 사용)

-21- yarn add jsonwebtoken (jsonwebtoken은 토큰을 생성하고 검증하는 패키지)
-21-02- yarn add passport(passport는 인증을 위한 패키지), yarn add -D @types/passport (passport의 타입스크립트 타입을 사용하기 위한 패키지)
-21-03- yarn add passport-jwt (passport-jwt는 jwt를 사용한 인증을 위한 패키지), yarn add -D @types/passport-jwt (passport-jwt의 타입스크립트 타입을 사용하기 위한 패키지)

-22- yarn add express-fileupload (express-fileupload는 파일 업로드를 위한 패키지)
- yarn add -D @types/express-fileupload (express-fileupload의 타입스크립트 타입을 사용하기 위한 패키지)
-22-02- yarn add sharp (sharp는 이미지 리사이징을 위한 패키지)
- yarn add -D @types/sharp (sharp의 타입스크립트 타입을 사용하기 위한 패키지)
-22-03- yarn add cloudinary (cloudinary는 이미지 업로드를 위한 패키지)
-yarn add -D @types/cloudinary (cloudinary의 타입스크립트 타입을 사용하기 위한 패키지)

----------------------------------------------------------------
frontend
-23- yarn create vite ./ (vite는 리액트 프로젝트를 위한 번들러)
-24- yarn add -D tailwindcss postcss autoprefixer (tailwindcss는 css 프레임워크, postcss는 css 전처리기, autoprefixer는 css 벤더프리픽스 자동으로 붙여주는 패키지)
-25- yarn add react-router-dom (react-router-dom은 리액트 라우터 패키지)
-25-02- yarn add -D @types/react-router-dom (react-router-dom의 타입스크립트 타입을 사용하기 위한 패키지)


- 공부하며 알게된 내용들
================================================================
fork()와 exec()의 차이
OS 2016. 4. 21. 16:50
fork()와 exec()는 모두 한 프로세스가 다른 프로세스를 실행시키기 위해 사용하게 됩니다.

exec에는 execl, execv등 여러가지 함수군을 가지고 있습니다. exec의 함수군에 대해서는 아래쪽에서 차이를 간단히 정리하고자 합니다.

우선 fork()와 exec()의 차이점은 fork() 시스템 호출은 새로운 프로세스를 위한 메모리를 할당합니다. 그리고 fork()를 호출한 프로세스를 새로운 공간으로 전부 복사하게 되고, 원래 프로세스는 원래 프로세스대로 작업을 실행하고 fork()를 이용해서 생성된 프로세스도 그 나름대로 fork() 시스템 콜이 수행된 라인의 다음 라인부터 실행이 됩니다. (새로 생성된 프로세스는 원래의 프로세스와 똑같은 코드를 가지고 있습니다.)

반면, exec()는 fork()처럼 새로운 프로세스를 위한 메모리를 할당하지 않고, exec()를 호출한 프로세스가 아닌 exec()에 의해 호출된 프로세스만 메모리에 남게됩니다.

간단히 정리하면, fork()의 결과는 프로세스가 하나 더 생기는 것입니다.( = 프로세스 id- PID 가 완전히 다른 또 하나의 프로세스가 생기는 것)

반면 exec()실행의 결과로 생성되는 새로운 프로세스는 없고, exec()를 호출한 프로세스의 PID가 그대로 새로운 프로세스에 적용이 되며, exec()를 호출한 프로세스는 새로운 프로세스에 의해 덮어 쓰여지게 됩니다.



이제, exec()관련 함수들에 대해 조금 간단히 다뤄볼까 합니다. exec는 execl, execv, execlp, execvp 등이 있습니다.

이들에 대하여 본 4가지만 간단히 구분하는 방법을 정리해보았습니다.



exec를 먼저 l계열(execl, execlp)과 v계열(execv, execvp)로 나누어 설명하겠습니다.

l계열 : 인자를 열거하는 방식이 나열형

v계열 : 인자를 열거하는 방식이 배열형



다음으로 p가 붙은 계열(execlp, execvp), 안붙은 계열(execl, execv)로 나누어 정리하면,

p가 안붙은 계열 : 경로를 지정해주면 ,현재/절대경로를 기준으로 찾게 됩니다.(경로로 실행파일을 지정)

p가 붙은 계열(path) : path에 잡혀있으면 실행됩니다.(실행파일의 이름만 지정)



exec계열은 첫번째 인자의 코드가 들어오고 나머지 기존에 exec아래에서 실행해야할 코드는 전부 잃어버리게 된다는 점을 가지고 있다고 보시면 됩니다.
자료 출처 (https://jwprogramming.tistory.com/55)

================================================================








```