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











```