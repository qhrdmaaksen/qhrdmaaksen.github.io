---
layout: post
title: "기타 등등"
---

## 필요한 기타 등등

```js
================================================================
항상 dependencies 에 추가되도록 install --save 를 사용습관을 기르자
================================================================
prettier setting (.prettierrc.js)
-prettier : $ npm install --save-dev --save-exact prettier
module.exports =  {
	//한 줄이 이 글자수를 넘게 되면 들여쓰기되어 코드가 세로로 정리된다. (default: 80)
	"printWidth": 80,
	//탭 너비 (default: 2)
	"tabWidth": 2,
	//탭 사용 여부. 참이면 탭이있는 줄을 들여 쓰기 한다. (default: false)
	"useTabs": false,
	//세미클론 강제 여부 (default: true)
	"semi": true,
	//홑따옴표를 쓸건지 설정. 기본값은 쌍따옴표. 코딩을 하면서 홑따옴표를 썼다면 강제로 쌍따옴표로 변경. (default: false)
	"singleQuote": true,
	/*객체, 배열, 함수 등의 후행에 쉼표를 찍을지 제어
	"none" - 쉼표를 붙히지 않음
	"es5" - ES5에서 유효한 후행 쉼표 붙힘 (객체, 배열 등)
	"all" - 가능하면 후행 쉼표를 붙힘 (함수 인수)*/
	"trailingComma": "all",
	//객체 리터럴 사용시 괄호에 공백 삽입 여부 (default: true)
	"bracketSpacing": true,
	// JSX 의 마지막 `>`를 다음 줄로 내릴지 여부
	"jsxBracketSameLine": false,
	//단독 화살표 함수의 매개 변수 주위에 괄호를 자동으로 붙힘 (default: 'avoid')
	"arrowParens": "always",
	//vue 파일의 script와 style태그 들여쓰기 여부
	"vueIndentScriptAndStyle": false,
	//맨마지막 줄 넣는지 여부
	"endOfLine": "auto",

	// .gitignore 처럼 prettier 이 적용되지 않게 하려면 .prettierignore 에 파일명을 기록하면 그 파일은 무시
	// 또한 파일 뿐만 아니고 코드내에서 주석으로 // prettier-ignore 라고 작성하면 해당 코드만 무시
	//ignorePath
	// 이 확장 기능을 비활성화 할 언어 ID 목록
	//disableLanguages: ["vue"]
};
================================================================
-eslint : $ npm i -D eslint-plugin-import eslint-plugin-react
-리덕스 툴킷 사용 : npm install @reduxjs/toolkit
(리덕스가 만약 설치되어있다면 리덕스 툴킷안에 모든기능있기에 기존리덕스삭제)
-redux 사용시 npm install redux, npm install redux react-redux
===============================
라우터 설치 npm install react-router-dom@5 (5버전 download)
============================
파이어 베이스 도구 설치
npm install -g firebase-tools
================================================================
NextJS
nodejs.org 접속 후 최신 버전 받은 후 터미널에서 해당 프로젝트 경로에서 
cpx create-next-app
================================================================
mongodb package install
-npm install mongodb
================================================================
React Transition Group install
-npm install react-transition-group --save
================================================================
TypeScript install
-npm install -g typescript

TypeScript 로 새로운 Create React App 프로젝트를 시작
-npx create-react-app my-app --template typescript
또는
-yarn create react-app my-app --template typescript

기존 Create React App 프로젝트에 TypeScript 를 추가
-npm install --save typescript @types/node @types/react @types/react-dom @types/jest
또는
-yarn add typescript @types/node @types/react @types/react-dom @types/jest
================================================================
실시간 브라우저 연동 lite-server
npm install lite-server
================================================================
styled-component 설치 
// npm 사용
--save : 지금 설치하는 패키지들을 package.json 파일이 관리하는 의존성 목록에 저장하겠다는 의미
npm install --save styled-components
// yarn 사용
yarn add styled-components
================================================================
(window) powershell 생성할 경로
npx create-react-app {폴더명}
================================================================
serve install (serve 는 static file 을 서빙해주는 역할의 패키지)
(-g 로 글로벌로 설치하면 현재 사용하는 컴퓨터의 다른 경로 어디에서든지 사용할수있게됨)
npm install -g serve
================================================================
yarn install
npm install --global yarn 
================================================================
sass install
-yarn add sass
================================================================
반응형 디자인을 쉽게 만들어주는 include-media 와 편리한 색상 팔레트 open-color 사용 
- $ yarn add open-color include-media 
================================================================
className 
- $ yarn add className
================================================================
styled-components
- $ yarn add styled-components
================================================================
react-icons (리액트에서 다양하고 예쁜 아이콘을 사용할수있는 라이브러리)
-해당 라이브러리의 장점으로 SVG 형태로 이뤄진 아이콘을 리액트 컴포넌트처럼 쉽게 사용할수있음
-아이콘의 크기나 색상은 props or CSS style 로 변경해 사용할수있음
설치
yarn add react-icons
================================================================
react-virtualized 최적화 라이브러리 
$ yarn add react-virtualized
================================================================
Parcel
-이 도구를 사용하면 쉽고 빠르게 웹 앱 프로젝트를 구성할 수 있음
yarn global add parcel-bundler
npm install -g parcel-bundler

프로젝트 디렉터리 생성 후 package.json 파일 생성
================================================================
리덕스 데브툴즈 설치
yarn add redux-devtools-extension
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================






















```
