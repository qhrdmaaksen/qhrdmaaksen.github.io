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
redux-actions
-리덕스 액션즈를 사용하면 액션생성함수를 더 짧은 코드로 작성가능
-리듀서를 작성할때도 switch/case 가아닌 handleActions 함수를 사용해 각 액션마다 업데이트 함수를 설정하는 형식으로 작성해줄수있음
yarn add redux-actions
================================================================
redux-logger
-오픈 소스 커뮤니티에 올라와있는 미들웨어 설치(잘만들어진 미들웨어 라이브러리)
yarn add redux-logger
================================================================
서버를 위해 번들링할때 node_modules 에서 불러오는것을 제외하고 번들링하기 위한 라이브러리
yarn add webpack-node-externals
================================================================
고유 ID를 만들어주는 라이브러리
npm install uuid
================================================================

컴포넌트란
- component (요소를 구성)

웹 컴포넌트 (표준 등재)
- 라이브러리로 가져다 사용 가능
- 웹 페이지 및 웹 앱에서 커스텀 가능, 캡슐화하여 재사용 가능한 커스텀 엘리먼트를 생성하고 웹 앱에서 활용할 수 있도록 해주는 다양한 기술들의 모음

리액트 컴포넌트
- 데이터와 돔을 동기화하는 선언적 라이브러리 제공

headless component
- 기능만 제공하되 사용자가 직접 스타일링을 해야하는 컴포넌트

커스텀훅
- headless component 를 만들기 위한 패턴

contenteditable 속성
- 전역 특성은 사용자가 요소를 편집할 수 있는지 나타내는 열거형 특성입니다
- 어떤 컴포넌트든 해당 속성을 사용하면 텍스트 편집이 가능해집니다
ex code
<blockquote contenteditable="true">
    <p>Edit this content to add your own quote</p>
</blockquote>
<cite contenteditable="true">-- Write your own name here</cite>
- 가능한 값은 다음과 같습니다.
  true 또는 빈 문자열은 요소가 편집 가능함을 나타냅니다.
  false는 요소가 편집 불가능함을 나타냅니다.
  값 없이, <label contenteditable>예제</label>처럼 사용할 경우 빈 문자열 값으로 간주합니다.
  특성이 없거나, 값이 유효하지 않은 경우 부모 요소로부터 상속합니다. 즉, 부모 요소를 편집 가능한 경우 자신도 편집 가능합니다.
  가능한 값에 true와 false가 있긴 하지만, contenteditable 특성은 불리언 특성이 아닌 열거형 특성입니다.
  텍스트 삽입 시 표시되는 커서의 색은 CSS caret-color (en-US) 특성으로 바꿀 수 있습니다.

ServerLess
- 서버 개발자 없이 웹 서비스를 만들 수 있게 해주는 클라우드 서비스


유효성 검사는 제어 컴포넌트로 구현하는것이 좋음
- 제어 컴포넌트는 사용자가 입력한 값을 state 에 넣어주고 state 의 값을 이용해서 렌더링을 하는 컴포넌트

End to End Test
- 사용자의 시나리오대로 애플리케이션을 테스트하는 방법
- 처음 부터 끝까지 테스트를 하는것

Integration Test
- 여러 컴포넌트가 정상적으로 작동하는지 테스트하는 방법
- 컴포넌트를 렌더링하는것 까지만 테스트
- 실제 디비, 브라우저 없이 큰 규모의 기능이나 하나의 페이지가 잘 작동하는지 테스트

Unit test
- 기능의 개별적인 단위나 하나의 컴포넌트를 테스트

Static test
- 코드 작성 레벨에서 오타와 타입에러를 확인
- 구문 오류, 나쁜 코드 스타일, 잘못된 api 사용 등을 lint 라는 도구를 사용해서 확인


아토믹 디자인 패턴
Atom
- 인터페이스를 구성하는 가장 작은 단위 (조합이 없음)

Molecule
- Atom 을 여러개 묶어서 구성한 컴포넌트

Organism
- Molecule 을 여러개 묶어서 구성한 컴포넌트

Template
- Organism, Atom, Molecule 을 조합해 만든 레이아웃

Page
- 여러 Template, Organism 을 조합해 만든 페이지

리액트 스러운 컴포넌트 생각
- 리액트는 디자인을 바라보는 방식과 앱을 빌드하는 방식
리액트로 사용자 인터페이스를 빌드하는 방법 
1. 컴포넌트라고하는 조각으로 분해 
2. 각 컴포넌트에 대해 서로 생김새가 다른 상태 정의 
3. 컴포넌트를 서로 연결해 데이터가 흐르도록한다


TPO (Time(시간), Place(장소), Occasion(상황))

CDD (Component Driven Development) 상향식 컴포넌트 개발 Bottom Up
- 컴포넌트를 먼저 만들고 이를 조합해서 페이지를 만드는 방식
- 아토믹 디자인 패턴을 사용하면 CDD 방식으로 개발하기 쉬움
- 일반 사용자뿐아니라 개발자도 사용할수있는것을 고려해야함
- Atom -> Molecule -> Organism -> Template -> Page

하향식 컴포넌트 개발 Top Down
- 하향식 컴포넌트 개발은 전체 시스템의 큰 구성요소들을 먼저 개발
- 이후 중복되는 작은 컴포넌트 분리 및 공통 혹은 교차되는 컴포넌트 분리 
- 전체 시스템의 디자인과 구조를 먼저 구성하고, 이를 바탕으로 세부적인 요소들을 개발
- 르블랑의 법칙에 빠지기 쉽다
- Page -> Template -> Organism -> Molecule -> Atom



TDD (Test Driven Development) 테스트 주도 개발
- 테스트를 먼저 만들고 이를 통과하는 코드를 작성하는 방식
- 테스트를 먼저 만들어야하는 이유는 테스트를 먼저 만들면 테스트를 통과하는 코드를 작성하기 위해 무엇을 해야하는지 명확해지기 때문

BDD (Behavior Driven Development) 행위 주도 개발


제어 컴포넌트와 비제어 컴포넌트

제어 컴포넌트는 push 로 진행됨 & single source of truth
- 사용자가 입력한 값을 state 에 넣어주고 state 의 값을 이용해서 렌더링을 하는 컴포넌트
- 리액트에 값이 완전히 제어되는 input element
- state 를 값으로 넘기고 그 state 를 다룰수있는 핸들러를 콜백으로 넘긴다
- 항상 이벤트 핸들러를 통해서만 값을 변경할 수 있음
- 잦은 렌더링 문제가 발생할 수 있음
- 상태를 중심으로 개발하기에 상태 변경에 따른 핸들링이 필요
- 렌더링 시점마다 고유의 값을 가진다
- 유효성 검사에서 자동 업데이트로 인해 개발자가 별도의 업데이트 코드를 작성할 필요 없다

비제어 컴포넌트는 pull 로 진행됨 & get State
- 전통적인 HTML 처럼 DOM 에 제어되는 input element
- 오직 사용자만 값과 상호작용
- 필요한 시점에 트리거 하기때문에 사용자가 입력한 값을 얻어오기 위해서는 ref 를 사용해야함
- DOM 에 직접 접근하기 때문에 잦은 렌더링 문제가 발생하지 않음
- 돔을 직접 조작하기에 핸들링이 어렵고 값 비싼 비용 지불
- 렌더링시에 원하는 값을 볼 수 없다
- 개발자가 직접 트리거해야한다







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
