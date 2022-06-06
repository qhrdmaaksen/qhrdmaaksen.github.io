---
layout: post
title: "Next.js nodeBird Front summary"
---

## 민우의 블로그 테스트중입니다

```js
===============install 설정===========
node 설치 후
node version check
  in terminal command : node -v

npm 초기화 : npm init

next 설치
  npm i next@9     (@9는 version 을 의미)

package.json 에서 대략적인거 설정하고, test 를 "dev": "next" 변경

react and react-dom 설치가안되어있다면 npm i react react-dom 으로 설치

pages folder create (반드시 폴더명은 pages 여야한다. 넥스트가 인식한다)
  pages folder 안에 file 들은 pages 가 파일들을 개별적인 page 로 만들어준다 (page component)
    code splitting 으로 만들어준다

pages folder in create index.js file

npm i antd styled-component @ant-design/icons

npm i styles-components

npm i babel-preset-next

npm i babel-plugin-styled-components

npm i nex-redux-wrapper@6

npm i redux

npm i react-redux           (리액트랑 리덕스를 연결시켜줌)

npm i redux-devtools-extension      (브라우저 개발자 도구와 연동이됨)

npm i pm2 (server state check)
------------------
npm i react-slick         (이미지를 넘겨서 볼 수 있게 지원해주는 컴포넌트)
npm i redux-thunk
npm rm redux-thunk  (rm 을 붙이면 지울 수 있다.)
npm i redux-saga      ( redux-saga 설치)
----------------------------------------------------------------
npm i -D shortid            (id 를 랜덤하게 적용, 라이브러리)
npm i -D faker@5       (단점은 영어로나옴, 각종 더미데이터 랜덤 적용 라이브러리)
npm i immer     (불변성엔 필수! )
----------------------------------------------------------------
npm i -D babel-eslint  
npm i -D eslint-config-airbnb
npm i -D eslint-plugin-import
npm i -D eslint-plugin-react-hooks
npm i -D eslint-plugin-jsx-a11y   (스크린 리더가 화면을 잘 이해할수있는지)
------------------
코드 통합 ( 깨끗한 코드 및 문법 검사 )
npm i eslint -D
npm i eslint-plugin-import -D
npm i eslint-plugin-react -D
npm i eslint-plugin-react-hooks -D
npm install prettier --save-dev --save-exact

.eslintrc 폴더에 추가 및 셋팅
{
	"parserOptions": {
		"ecmaVersion": 2020, // 버젼
		"sourceType": "module", // 모듈 시스템
		"ecmaFeatures": {
			"jsx": true
		}
	},
	"env": { // 환경
		"browser": true,
		"node": true,
		"es6": true
	},
	"extends": [
		"eslint:recommended", // 규칙을 따른다
		"plugin:react/recommended"
	],
	"plugins": [
		"import",
		"react-hooks"
	],
	"rules": {
	}
}


prettier settings
module.exports =  {
	semi:  true,
	trailingComma:  'all',
	singleQuote:  true,
	printWidth:  100,
	tabWidth:  2,
};
=========================================
1) next.js 역할, settings, page & layout, Link & eslint
브라우저 : 백엔드간에 요청에 CORS 설정이 필요하다

CSR : 브라우저 프론트 브라우저  백엔드 브라우저
SSR (서버사이드렌더링) : 브라우저 프론트 백엔드 프론트 브라우저
  로딩을 없애는 이유로 ssr 을 사용하는것도 좋다 (캐싱까지 활용되면 최고)

몽고 db 추천안하는 이유 : 대부분 서비스에는 관계가있다, sql을 사용하는게 좋다.
  하지만, 관계가없고 데이터가 다른데 하나의 테이블에 들어가야할때엔 사용하기좋다.

next 가 ssr 을 쉽게 해준다.

리액트사용 이유: 고객이 웹 사이트가아니라 모바일 웹을 사용하는것 같은 느낌을 받음
  검색엔진에 나와야한다면, SSR
    그렇지않다면 REACT


react-router 에서 했던 맵핑을 next 는 자동으로 해준다

pages 하위 folder 를 생성할수있으며, 생성된 폴더(about)에 file 에 접근하려면
  localhost:3000/about/vitamin777

prop-Types 사용 시 설치 :  npm i prop-types

next.js 는 react 를 사용한 framework 다
  갖춰진건 많지만 코딩의 자유도는 줄어든다
    next 가 해주는 것중 제일 큰 장점은 server side rendering

크게 3 개의 주체
브라우저;
프론트서버;
백엔드서버;데이터베이스;

전통적인 구동방식
browser -> frontend server -> backend server -> data base ->
- backend server -> frontend server -> browser

SPA 구동방식 ( 사용자가 빠르게 인터렉션을 원할때 )
  (data 없이 화면만 받음)js, html, css, img 등을 browser에 뿌려주며, data는 다시 backend server
  - 에서 db -> backend server -> browser

검색엔진을 위해 서버 사이드 렌더링
  코드 스플릿팅
    첫 방문은 전통적인 구동방식으로 하되, 그 다음 페이지 전환일땐 react 방식으로

next를 사용 유무를 고려해야할것
무 - 어드민 페이지 ( 코드 스플릿팅, 서버사이드 렌더링이 필요없는 경우)
유 - 검색엔진이 필요하고 고객들이 접근하는 페이지

return 안에 들어가는 모든 것들은 node

next 에는 react 의 hot loader 가 적용이되어있다. (실시간 자동 업데이트 반영)

웹팩은 여러개의 파일을 하나의 js로 합쳐주는 툴임
  next도 webpack을 쓰고 있는데 내부적으로 쓰고 있어서 따로 설정이 없는 것
=================================================
2) antd(css framework) & styled-components, _app.js & Head,
    use the response grid, create login form
      rerendering understand, use dummy data to login, chrome extension,
        create profile page, signup page

next 에는 기본적으로 webpack 이 들어가있다.
  css file 은 import 를 못하며, import 는 js 만 가능하다
    웹팩이 css 를 보는 순간 스타일 태그로 바꿔서 html 에 넣어준다 .

공통된것들은 pages 에 _app.js 에 설정해둔다
  _app.js 는 pages 들의 완전한 공통 부분이다.

_app.js 가 모든 pages 들의 부모 역할

Head 수정: next 에서 Head component 제공함
  import Head from 'next/head';

next page structure
_document         <DOCUMENT>
_app              <App>
pages             <Page>

node는 elementType, number, string, null 등 모든 것을 넣을 수 있고,
  elementType에는 컴포넌트만 넣을 수 있다.
    _app.js in code : PropTypes.elementType.isRequired,

antd design 은 직접 site 들어가서 code 보고 적합한걸로 사용하자

반응형: 화면이 처음엔 모바일 페이지였다가 점점 늘어나면서 컴포넌트가 재배치되면서 화면이 바뀐다,
  테블릿 페이지 -> 데스크탑 페이지
적응형: 모바일 페이지 따로 데스크탑 페이지 따로 테블릿 페이지따로

반응형을 할 수 있게 antd design 에서 지원을 해준다.

반응형으로 만든다면 모바일 디자인부터 만들어가자 (데스크탑부터하면 브레이크포인트 설정이 머리아프다?)
  효율성을 위해서는 모바일부터 다음 테블릿 다음 데스크탑으로 넓혀가야한다

가로부터해서 세로를 만들자
  <Row>
    <Col xs={24} md={6} />
    <Col xs={24} md={12} />
    <Col xs={24} md={6} />
  </Row>
    xs mobile, sm tablet, md small desktop, lg middle screen, xl full screen

{/*컬럼 사이의 간격 gutter*/}

타겟 블랭크를 사용할때엔 보안의 위험때문에 아래와같이 설정해두자
  target={'_blank'} rel="noreferrer noopener" // 새창을 누가열었는지 알 수 없게만듬

dummy data : 의미없는 data 이지만, 빈 공간을 채워야할 때 사용? db가 없을때 test 로 채워쓰기

보통 component file 들은 component folder 에 정리해놓고 pages 에서 꺼내사용한다

components = presenters :
  전에는 화면 보여주는것은 component 에 넣어두고 data 들어가는 것은 컨테이너에 넣었었다.

form 은 수작업말고 리액트 라이브러리를 활용하는게 좋다.
link 에는 href 넣고 a tag 에는 안넣는게 좋다.

label 사용시 input tag 에 id 가있으면 라벨 클릭시에 인풋이 포커스가된다.

Link 태그는 내부 next/router로 내부 페이지 라우팅 용

class였을때는 객체 state를 많이 썼지만 hooks일 때는 보통 속성별로 따로 선언,
  불변성 지키기가 귀찮, class의 setState는 최상위객체는
    알아서 shallow compare를 해주지만 hooks는 그런게 없음

보통 리액트 컴포넌트는 대문자로 시작.
  또는 클래스, 인터페이스, 그 외에는 소문자로 하고, next에서는 page는 소문자

code inline style 로 <div style={{ marginTop: '10px'}}> 와 같이 사용하면안된다.
  객체 === 객체는 false

-----------------------------

### inline style 을 넣으면 렌더링 최적화가 되지않기에 아래와같이한다

import styled from 'styled-components';
// 디브 컴포넌트이면서 css 가 적용된 ButtonWrapper component 생성됨
const ButtonWrapper = styled.div` // div tag 가 된다.
  margin-top: 10px;
`;
-----------------------------
import { Menu, Input, Row, Col } from 'antd'; // antd 에 Menu 사용
import styled from 'styled-components';

const SearchInput = styled(Input.Search)` // antd 에서 사용한 Input.Search 를 styled component 로 바꿔 넣어줌
  verticalAlign: middle;
`;
-----------------------------
const style = useMemo(()=>({ // styled component 를 사용원치 않을때 useMemo 사용
    marginTop: 10
  }), []);

<ButtonWrapper style={style}>
-----------------------------
useMemo : 값 캐싱, useCallback: 함수 캐싱(잠시저장)
useCallback의 경우는 [] 내부에 넣은 값이 바뀌면 함수를 재생성하고,
useEffect의 경우는 [] 내부에 넣은 값이 바뀌면 함수를 재실행
-----------------------------
버츄얼 돔
  return 부분이 버츄얼 돔이라고 생각하면된다.
    리액트에서 한번은 return 을 그려주고 리렌더링을 됐을때
    - 버츄얼 돔으로된게 이전 컴포넌트의 버츄얼돔과,
     --지금 컴포넌트의 버츄얼돔 중 바뀐게있으면,
     ---버츄얼 돔에서 달라진 부분을 리액트에 알려주기때문에 바뀐 부분만 다시그린다.
-----------------------------
css 관련, 공식문서 참고하자-----
전역 스타일시트 추가
  pages 폴더에 _app.js 에 import '../styles.css' 파일명
    아마도 next 10 버전 이후로는 각 폴더마다 따로 줄수있다고도하는듯?

타사 구성요소에 필요한 css 가져오는방법
  pages 폴더에 _app.js 에 import 'bootstrap/dist/css/bootstrap.css'
    이후 원하는 컴포넌트 js 에서 <button className="close-button" onClick={close}>
      위 와 같이 사용하면됨

스타일시트 및 전역 css 파일
  CSS 모듈은 선택적 기능 이며.module.css 확장자 가 . 일반 <link>스타일시트 및 전역 CSS 파일은 계속 지원됩니다.
    ex: components/Button.module.css먼저 다음 내용 으로 만듬
 .error {
  color: white;
  background-color: red;
}
그런 다음 components/Button.js위의 CSS 파일을 가져와서 사용합니다.
  import styles from './Button.module.css'
    export function Button() {
  return (
    <button
      type="button"
      // Note how the "error" class is accessed as a property on the imported
      // `styles` object.
      className={styles.error}
    >
      Destroy
    </button>
  )
}
---------------------
sass 지원함 사용원한다면 공식문서 다시보자
====================================
<Form onFinish={onSubmitFrom}> {/*onFinish 는 이미 e.preventDefault() 가 적용되어있다. antd 전용, 대체제로는 onSubmit*/}
  그러므로 antd 에서는 onSubmitFrom 함수에 별도의 preventDefault 를 지정하면안된다.
-----------------------------
dummy data (가상의 useState) 를 활용해서 백엔드 없이 테스트 가능하다
-----------------------------
next 는 세미콜론을 사용하지 않는다,
  문장의 길이는 100 을 넘기지않도록한다
    싱글 쿼트를 사용한다

<div key="twit">짹짹<br />0</div>,  /*리액트에서 배열로 jsx 사용할땐 key 붙여줘야함*/

padding: 10px !important 같이 우선순위를 올릴수있다.

next 는 react 에 기능이 추가된것이지만 폴더 구조(pages, public 등)를
  next 가 제안하는대로 따라야하며,
    next 에서 react + @(next 제공기능) 을 사용

{ }로 객체를 감쌀 때 주의할 점은 화살표 함수 사용 시입니다.
  const a = () => {} 이렇게 되면 마지막 {}가 객체인지 함수의 몸통인지 헷갈립니다.
     a = ()  => {} 이런 경우 함수의 몸통이고 () => ({}) 이런 경우 {}
       객체를 return하는 겁니다.

Hooks 는 조건이있다, 반복문 조건문 함수안에서는 안되며, 컴포넌트안에서 가능하다,
  뎁스 한단계일때 가능
    2개이상의 hooks 서로 관련있을때는 커스텀 훅 만들어 간추려주자

<></>는 자식 태그가 2개 이상일 때만 감싸는것,
  자식 태그가 2개 이상일 때 묶어주는 역할 이외에는 아무런 역할이 없음

리덕스는 코드량이많아 생산성 측면에선 좋지않지만, 초보가 사용하기좋다(에러가 덜남)
  넥스트에서 리덕스를 붙일때 복잡하지만 간편하게해주는 라이브러리가있다.
    next-redux-wrapper
      설치 npm i nex-redux-wrapper@6                (@6은 6버전)
mobx 는 생산성을 중요시한다면 mobx 사용,
----------------------------------------
const wrapper = createWrapper(configureStore,
		// 옵션객체 디버그가 트루이면 리덕스에관해서 자세한 설명이나오기때문에 개발할땐 true 로 놓자
		{ debug: process.env.NODE_ENV === 'development'})

next 에서는 react-redux 와 달리 Provider 를 사용하지않음
  6버전 이후로는 알아서 감싸줌

redux 는 중앙 데이터 저장소라고 생각하자, 흩뿌려져있는 component 들을 모아서
  필요한곳에 뿌려주는 역할
    (react-context 와 비슷한 역할)

리덕스는 원리가 간단하기때문에 에러가 날 일이 많이 적고 나더라도 해결하기 쉽다.
  추적이 잘 되기때문에, 단점으로는 코드량이 많아진다. 하지만 앱은 안정적으로됨

모빅스는 코드량은 많이 줄지만, 실수하는 경우 추적하기 어렵다.

서버에서 데이터를 받아온다는것은 비동기다 (비동기를 다룰땐 실패에 대비해야한다)

비동기는 보통 3단계
  처음 데이터를 보내달라고 요청
    성공해서 받는것
      실패하는것

context api 는 직접 다 구현해줘야한다.
  단점은 useEffext 같은곳에 요청을 보내는데
    컴포넌트는 화면에 그리는것에 집중하면좋다.
      데이터까지 다루는것은 컴포넌트 역할이 아니다.
        비동기 요청이 많다면 어차피 리덕스나 모빅스와 비슷하게 코드가 변한다
          그렇기에 그냥 처음부터 리덕스나 모빅스를 사용하자

데이터 요청은 별도의 모듈이나 라이브러리를 사용하자

화면을 비즈니스 로직과 분리 데이터 요청과 분리
  데이터는 중앙 데이터 저장소에서 관리하는게 좋다.
    데이터의 양이많다면 쪼개주는 작업이 필요하다
      리덕스는 리듀서들을 쪼갤수있따

하나의 컴포넌트에만 쓰이는 비동기 요청은 컴포넌트내에서 작성하자, 코드가 훨씬 적어진다.

next redux wrapper가 없으면 리덕스가 ssr되지 않는다,
  서버에서 데이터가 없이 화면만 그려주게되는데 그러면 ssr하는 의미가 없어진다.

redux 는 reduce 에서 따온것?

redux 에서 데이터를 수정하려할때 액션을 꼭 필수로 만들어줘야한다.
중앙 state 저장소
ex { name: 'vitamin',
      age: '35',
      password: 'hello'
    }
    액션을 dispatch 하면 중앙 저장소에 state 가 바뀜(자동으로바뀌는게아닌 reducer 활용)
   { type: 'CHANGE_NICKNAME',
       data: 'hanaro'}
reducer 는 어떻게 바꿔줘야할지 직접 적어줘야함
ex switch (action.type){
    case 'CHANGE_NICKNAME':
    return {
      ...state,
      name: action.data
    }
}
...state를 사용하는이유:
  전체 객체의 속성들을 적어주지 않고
    ...state 이전 상태들은 내비두고 name: action.data 로 이름만 바꾸는것은
      메모리를 아끼기 위해서 및 타자가 길어져서
        모든것이 기록으로 남아있는데 액션을 하나 실행할때마다 새로운 객체들이 생기기에
          메모리를 많이 잡아먹는다.
바뀌는 애들만 바꾸고, 참조관계 유지되도 괜찮은 애들은 계속 참조관계 유지시키자
  (메모리 관리)
개발 모드일때는 히스토리를 계속 가지고있다.
  배포모드로 바꾸면 히스토리를 중간 중간에 계속 버린다.(그래서 메모리 문제가일어나지않는다)

좋은점은 액션하나 하나가 리덕스에 기록이되기때문에 지금까지 데이터를 어덯게 바꿔왔는지
  추적이되기때문에 데이터가 잘못되서 에러나는부분을 쉽게 찾을수있다.
액션을 만드는이유중 하나로 기록이 남기때문이다.


js 에서 항상 염두하고 조심해야할것 {} === {} // false
  객체를 새로만든것은 false 이지만 객체를 참조를 대입하면 true 가 나옴

객체를 새로 만들어줘야 추적이 가능하다.
  직접적으로 객체 참조에 대입을 해버리면 이전 기록과 현재 기록이 동일해진다.
    추적할수없다.

const nest = { b: 'c'}
const prev = { a: nest }
const next = { ...prev }
prev.a === next.a
  -> true
prev === next
  ->false
{ a: 'b'} === { a: 'b'}
  -> false
===============================================
store = state, reducer

configureStore 에서는 import reducer from '../reducers' 폴더까지만 경로지정

액션 함수의 형식이 중복되는 경우 동적액션or 액션생성기를 만들어주자

원리 :
액션 만들어서 디스패치 해주면 리듀서에따라 다음상태가나오며
  이전상태와 다음상태가 바뀌었다는게 확인되면 알아서 연결된 컴포넌트들에게 데이터가 뿌려짐

wrapper.withRedux가 react-redux의 Provider 역할을 하는 게 맞습니다.
  Provider는 context-api를 내부에 쓰고 있어서 어떤 컴포넌트에서든
   스토어의 값을 쓸 수 있게 해줍니다. 스토어의 값을 state라고 합니다.
    useSelector는 커스텀훅으로 훅 내부에서 useContext같은
      context-api 값 불러오는   기능을 사용하고 있습니다.
        거기에 있는 state에서 state.user.isLoggedIn 값을 가져오라고
          지시하는 게 저기 useSelector 훅의 역할입니다.

state를 return 안하면 undefined를 return하게된다. switch 문에서 default 빼먹지말자

store는 그냥 리덕스 전체라고 보시면 되고요.
  그 안에 state들과, action이 dispatch됐을 때 state를
    어떻게 바꿀지 적어놓은 파일이 reducer입니다.
      리덕스는 크게 state, reducer, action 세 가지

객체에서는 키와 값 변수가 같으면 생략가능하다.
  { data : data }를 { data } 로 줄일 수 있습니다.

.js나  index.js는 생략 가능합니다.
  ../reducers는 ../reducers/index 또는 ../reducers/index.js랑 같고요.

export default A 한 애는 다른 곳에서 import B from '경로'로 가져올 수 있습니다.
  이름이 달라도 됩니다.
export { a } 한 애는 import { a } 로 이름이 같게 가져와야 합니다.

액션에는 데이터만 담고, reducer 에서 데이터를 가공하자

리덕스 툴킷 에는 redux app 을 만들기에 필수적으로 여기는 패키지와 함수들을 포함함

액션을 기록하고 싶다면 미들웨어를 붙여야한다.

HYDRATE 가 새로 생겼으며, 겟이니셜프롭스가 요즘 거의 안쓰이며, 겟스텍틱프롭스와
  겟서버사이드프롭스 두개로 바뀌어서 서버사이드 렌더링이 기존과 많이 달라졌기에 새로생김
HYDRATE는 next-redux-wrapper를 쓸 때 필요한 액션인데요.
  서버쪽에서 실행된 리덕스의 결과물이 프론트에서는 HYDRATE라는
    액션 이름 아래에 데이터로 전달됩니다.

composeWithDevTools 히스토리가 쌓이면 메모리도 많이 잡아먹으며, 중앙 데이터들이
  어떻게 변화하는지 다 보이기때문에 보안에 취약하기에 배포용일때엔 데브툴을 연결하지않으며
    개발중일땐 데브툴을 연결해서 사용

만약 포트를 바꾸고싶다면 (기본은 3000)
  package.json 에 "dev": "next -p 3060" <- 왼쪽과 같이 바꾸면 포트 바뀜

브라우저에 redux 에서 히스토리를 볼수있으며, state or diff 로 상태변환 히스토리 상세보기
  그리고 돌아가고싶다면 마우스 올려놓고 jump 누르면서 debug check
    이게 가능한 이유가 모든 히스토리를 남겨놨기에 가능하다. 리덕스 ...짱짱
반드시 불변성을 지키자!

재사용 가능한 컴포넌트를 만들려면 여전히 디스패치같은 게 없는 컴포넌트를 작성하는 게 좋습니다.

middleware : 액션이 리듀서로 전달되기 전 후로 추가 작업을 실행해주는 함수

리듀서는 스토어에 연결될때 초기화된다.

리듀서는 이전 스테이트와 액션을 받아 다음 스테이트를 돌려주는 함수다

아래는 리듀서의 기본 꼬리 코드
const initialState = {

}
const reducer = (state = initialState, action) => {
	switch (action.type) {
		default:
			return state;
	}
}
export default reducer ;
--------------------------
import { combineReducers } from 'redux'
const rootReducer = combineReducers => {
리듀서와 합쳐주는 메서드

HYDRATE
  를 넣어주려면 인덱스를 하나 넣어주고 하이드레이트를 위해
    인덱스 리듀서를 추가해줌 (SSR 을 위해서)

switch문을 쓴다면 break;를 걸거나 return

리덕스와 모빅스를 리액트에서만 사용하는것이라 착각하지말자
  하지만 대부분 리액트에서 리덕스나 모빅스를 많이사용한다.

리덕스는 상태관리도구(뷰 or 앵귤러에서도 사용할수도있음)

컨텍스트 api 를 안쓰는 이유가 이미 리덕스나 모빅스에 다 만들어줘서,

리덕스는 컴포넌트사이의 스테이트 문제를 해결하려고 사용
  컴포넌트들과의 관계가있다면 리덕스를 사용하는게 편하다.
    하지만 관계가없다면 그냥 component 에서 state 사용하면된다.

모빅스 구조

  스테이트가 액션을 통해 상태가 바뀌면 감싸고있던 객체 옵저버블이,
    스테이트의 상태가 바뀔때마다 옵저버블이 옵저버한테 바뀐 상태를 알려줌

require 와 import 는 기능은 비슷하지만, default 가 다르다.

리덕스와 리듀스를 연결하기위해 필요한
const store = createStore(reducer, enhancer)
	store.dispatch({ // 디스패치하는 순간 타입과 데이터가 리듀서로 보내진다.
		type: 'CHANGE_NICKNAME',
		data: 'vitamin777',
	})
	return store;

모빅스 ex
const { observable, autorun, runInAction } = require('mobx')
const state = observable({ // state를 감싸고있는 observable
  compA: 'a',
  compB: 12,
  compC: null,
})
autorun(() => { // 상태가 바뀔때마다 autorun 콜백함수를 실행함
  console.log('change, state.compA');
  // 여러개의 함수에서 각각의 상태가 여러번 콘솔찍힘
})
// state.compA = 'b'
// state.compB = 'd'
// state.compC = 'c'
// console.log('change') // 한번만찍힘 여러개의 상태변화를 한번의 액션으로 침
runInAction = () => {
  state.compA = 'b'
  state.compC = 'c'
}
runInAction = () => {
  state.compB = 'd'
}
----------------------------------------------------------------
모빅스는 너무 자유롭기때문에 프로젝트 시작떄 어느정도 구조를 정하고 들어가야함

리덕스 툴킷에는 사가 성크 이머 createReducer 등등이 내장이되어있다.

리액트 핫로더가 사라지고 리엑트 리프레쉬,리엑트 리프레쉬 플러그인이 생김

id,content 는 게시글 자체의 속성이며,
유저 이미지스 커맨츠스는 다른정보들과 합쳐서 주기때문에 대문자로,
프론트 개발자라면 서버쪽과 리덕스 데이터구조를 어떻게 보낼건지 물어보는게 좋다.

{/*뭔가 묶일 수 있는 단위가있을 것 같으면 먼저 컴포넌트 이름을 정해주자*/}

맵을 사용하면 키를 사용해야하며, 키는 인덱스로하면안된다, 특히
  게시글이 지워질 가능성이있을 경우에는 인덱스로 사용하면안된다,
    중간에 뭔가 추가될때도 사용하면안되며, 다만 바뀌지 않을것이며
      반복문이 바뀌지 않을경우에는 키를 인덱스로 사용하면안된다.
        키에는 고유한 값이 들어갈 수 있도록하자.

큰 뭉텅이로 포스트 폼 포스트카드 나누거나, 반복문안에 맵안에 들어있는것도 컴포넌트로
  따로 나누면 좋다.

액션은 객체다.
  동적으로 액션이 필요할때는 액션 크리에이터라는 함수를 만들어줌
디스패치 자리에는 객체가 들어가는것이 맞다

ref
  실제 돔에 접근하기위해서 사용

보통 프로퍼티들은 api백엔드개발자가 정의한다.

서버사이드렌더링에서 렌더링은 브라우저에서 하는 렌더링이 아니라
  서버쪽에서 데이터와 css태그 헤드 태그등을 다 포함한 html 코드를 완성한다는 의미

()도 연산자라서 함부로 감싸면 안됨

컨테이너 컴포넌트, 프리젠터 컴포넌트는 hooks로 오면서 구분할 필요가 없어졌습니다.

mainPosts.map에서 key값을 지정할때,
왜 {index}이렇게 { 이게 왜 들어가는걸가요?
  jsx에서 변수를 사용하는 문법

styled-components는 서버사이드렌더링을 적용해야
  페이지 로딩 시 경고가 안 나고 CSS가 적용됨

배열안에 jsx 들을 넣을때는 key 를 넣어줘야한다.

PropTypes.object.isRequired, 오브젝트는 속성들이 많이있지만,
  상세하게 표기해주고싶다면 shape 를 사용하자

setLiked((prev) => !prev)
  항상 false 는 true , true 는 false 로 바뀜

중괄호는 jsx태그 안에서 js문법을 쓰고 싶을 때 쓰는 것

남이 누른 걸 보여지게 하려면 Post 불러올 때 Likers 목록도\
  include해서 불러오셔야 합니다.

하나의 폼을 두 가지로 사용하려면 미묘하게 다른점들 때문에
 구현이 어려울 수 있습니다.
  또 하나의 컴포넌트는 하나의 기능만 하는 게 좋습니다

&&는 앞에 것이 truthy면 뒤에 것 실행/return하기이고
  ||는 앞에 것이 falsy면 뒤에 것 실행/return하기입니다.
    ?? 는 null, undefined 아니면 앞에것
      null,undefined 라면 뒤에것
ex
앞에가 false 면 뒤에꺼
앞에서 true면 앞에꺼
(5 > 3) || (2<0)
= true
(5 < 3) || (2<0)
= false
(5 < 3) || (2 > 0)
= true
앞에서 false 라면 앞에것
앞에서 true 라면 뒤에것
(5 > 3) && (2 < 0)
= false
(5 > 3) && (2 > 0)
= true
(5 < 3) && (2 > 0)
= false

이게 컴포넌트를 재사용하다보면 리덕스에서 각각 다른 데이터를
 전달해줘야할 때도 있습니다. 그럴 때는 props를 씁니다.
어떤 PostCard는 리트윗을 보여주고, 어떤 PostCard는
  일반 게시글을 보여줘야하는데 PostCard가 내부에서 useSelector를 통해
    고정된 데이터를 가져오면 자유도가 떨어져버립니다.
      그럴 때 props로 부모로부터 각기 다른 데이터를 받아오는 겁니다.

대부분의 경우는 (prev) => !prev 대신 !liked처럼 해도 됩니다만

setState를 연달아 할 때 완전 결과가 달라집니다.
  연달아 setState할 때는 반드시 콜백함수 방식으로 하셔야 합니다.
    react batched state로 검색해보시면 관련 이유를 알 수 있습니다.

빈배열은 그 자체로 데이터가 없다는 것을 나타내기 때문입니다.
  length를 쓸 때도 바로 0이 나오니 편리합니다.

폼은 일일이 다 만들지말고 라이브러리를 활용하자, 리액트 폼 리덕스 폼 라이브러리 등
  react-hook-form 추천드립니다.

리액트에서는 진짜 특수한 경우를 제외하고 직접 DOM에 접근하시면 안 됩니다.
  리렌더링될 때 DOM에 직접 변경했던 내용이 전부 초기화됩니다.
    item.content같은 데이터를 수정하셔야 합니다.
      content에는 리액트 컴포넌트를 넣을 수 있습니다.
        글자를 클릭할 때 그 글자의 색이 바뀌는 컴포넌트를
          item.content 데이터와 함께 넣으시면 됩니다.
content={<ChangeColorComment data={item.content} />}

next는 module.css 처음부터 지원하고있다

이미지의 alt 는 최대한 적합하게 적어주자, 시각장애인들에게 큰 도움이된다.

버튼이나 인풋이아니라면 presentation 을 넣어주자,시각장애인들이 버튼이아니라는걸
  알게된다고한다. 스크린리더에서 클릭할 필요있다 정도 알려줘야할때 아래와같이
    <img role="presentation" 를 넣어주자

JSX의 style 속성은 객체입니다. 따라서 객체 형식인 :를 사용해야 합니다.

폴더는 자동으로 index 를 가져온다.
  import ImagesZoom from "./ImagesZoom";

func()
 func`` 로도 호출 할 수 있다
--------------------------------
const Header = styled.header`
	header: 44px;
	background: white;
	position: relative;
	padding: 0;
	text-align: center;

	& h1 {
		margin: 0;
		font-size: 17px;
		color: #333;
		line-height: 44px;
	}

	& button {
		position: absolute;
		right: 0;
		top: 0;
		padding: 15px;
		line-height: 14px;
		cursor: pointer;
	}
`
<Header>
<h1> </h1>
<button> </button>
</Header>
------------------------------------
styled component 가 Slick class 로 정의되어있는것을 덮어씌게 할 수 있다.
  const Global = createGlobalStyle`
	.slick-slide {
		display: inline-block;
	}
  `
    그리고 Global 은 아무곳이나 넣어줘도된다.
      <Overlay>
				<Global/>
				<Header>
					<h1>상세 이미지</h1>
					<button onClick={onClose}>X</button>
				</Header>
------------------------------------
transform 안에 fixed 가 들어가면 fixed 를 제대로 잡지못하는 버그가있음
  const Global = createGlobalStyle`
	.slick-slide {
		display: inline-block;
	}
	.ant-card-cover {  // 넣어주면 됨
		transform: none !important;
	}
  `
--------------------------------------------------------
antd 에 발생하는 버그중 사이트 하단 가로 스크롤 바 없애기
const Global = createGlobalStyle`
	.ant-row {
		margin-right: 0 !important;
		margin-left: 0 !important;
	}

	.ant-col:first-child {
		padding-left: 0 !important;
	}

	.ant-col:last-child {
		padding-right: 0 !important;
	}
`
이후 글로벌은 아무곳이나 넣어주면됨
--------------------------------------------------------
스타일드 컴포넌트 사용하려면 바벨 설정 필수

styled component 를 많이 사용할 수록 코드량이 늘기때문에
  따로 styled.js 와 같이 빼놔서 import 로 사용하자
    export 로 설정해놓으면 다른 component 에서 사용 할 수 있기에
      export const Global = createGlobalStyle`
	    .slick-slide {
      display: inline-block;
	    }
--------------------------------------------------------
더미 데이터 구조를 제대로 잡아놔야한다.
  처음 부터 백엔드 개발자와 데이터 구조를 정확하게 협의를해서 문서화를 해놓자

package.json에 ^4.2로 쓰여있어서 그럽니다. ^가 붙으면 4버전 중에 가장 최신으로 하겠다는 뜻

useSWR을 이용해서 비동기 데이터 외에도 전역상태 관리가 필요한 다른 데이터도 활용가능한지
 useSWR이 Redux와 ContextAPI를 대체할수 있는건지 궁금합니다.
 :전역 상태관리도 가능합니다. 키를 설정하고 mutate로 값을 저장하면 그게 전역 값이 됩니다.

CRNA 는 기본적으로 웹팩을 안 쓸겁니다. 바벨쪽에서 설정하는 걸로 알고 있습니다.

스크롤 생기는 끝부분에 마우스 댄 뒤 ctr+shift+c 누르고 쭉 훑어보면 됩니다.

스타일 분리는 바로바로 하는 것이 좋습니다. 나중되면 너무 많아지고 중복도 심해집니다. 
  하지만 전부 다 하지는 않고 성능에 문제되는 것이 발생할 때 수정하는 용도로만 하기도 합니다.

Pages 안에 있는 컴포넌트들도 styled-component 따로 분리하고 싶을때도 폴더를 만들어서 작업을 해야 할까요?
  Pages 폴더 안에는 라우팅 잡힐거 같아서 파일 관리를 어떤식으로 해야할지 궁금합니다.
  :css 폴더를 pages 폴더와 동등한 위치에 새로 만들어서 styled-components를 모아둔 뒤 import 해서 쓰면 될 것 같습니다.

styled-component를 사용하여서 글로벌 스타일을 변경하는 것이 antd만 가능한건가요 ?
  :리액트 컴포넌트면 다 됩니다. 다만 !important로 덮어쓰는 게 있다면 안 됩니다.

postData 가 변하지 않는다는 조건 (반복문이 바뀔일 없는 조건)
   바뀔일이 없는 상황에는 key에 i (index) 를 넣어도된다.

react에서 map을 쓸 경우에는 배열말고 안에 내용물만 return 하도록 
  그렇게 라이브러리 적으로 설정이 되어있는 걸까요?
  :네 배열이 들어있으면 그 내용물만 렌더링합니다.

middleware 는 redux 의 기능을 향상 시켜주는 역할을 한다.
  리덕스에 없던 기능을 추가해주는 역할

리덕스 성크(thunk)는 리덕스가 비동기 액션을 
  디스패치할 수 있도록 도와주는 역할을한다.
    지연의 의미를 가지고있다
      ex 디스패치를 좀 나중에 보낼 수 있게

성크는 비동기 액션 하나에 동기 액션 여러개를 디스패치 할 수있다

미들웨어는 항상 화살표 3 개의 고차 함수를 가진다.

미들웨어를 사용해 리덕스 데브툴즈를 대체해도되긴한다.

로그인에는 로그인 요청, 성공, 실패 세단계가있다

성크에서는 로그인 클릭을 두번하면 서버에 요청 두번이 다 간다

스로틀이나 디바운스로 1초에 몇번 액션이 들어오는지 컨트롤이 가능하다

1. 검색엔진 노출이 필요하면 ssr 씁니다
  그러나 대부분의 서비스는 ssr과 csr를 섞어서 씁니다
2. SEO만 판단해서 Nextjs를 쓸지 아니면 그냥 react만 쓸지 결정하는편
3. 로딩은 ssr이 전체적으로는 더 빠르나, csr이 체감상으로는 
    더 빨라보이는 효과를 줄 수 있습니다. 결과적으로는 더 느릴 수 있습니다.

기존 connect 와 mapStateToProps대신 useSelector를 쓴다고 보시면 됩니다.
  mapStateToProps나 useSelector모두 필요한 것만 가져오는 것은 공통입니다.

리듀서에서 처리하기 전에 다른 일을 하고자 미들웨어를 씁니다. 
  리듀서는 무조건 동기 작업만 수행할 수 있습니다(태생적으로 그렇습니다)
   그래서 비동기 작업을 수행하기 위해서 thunk같은 미들웨어를 
    액션과 리듀서 사이에 끼어넣습니다

컴포넌트에서 axios를 호출하는 것은 지양하시는 게 좋습니다. 
  그렇게 하다보면 모양이 thunk나 saga처럼 됩니다. 
    그래서 그냥 처음부터 thunk나 saga를 쓰게됩니다

(store) => (next) => (action)은 액션 실행 시 자동으로 넣어집니다.
  next는 다음 미들웨어를 호출하는 역할입니다. 
    다음 미들웨어가 없으면 dispatch됩니다.

제너레이터
  function* 
    yield(yield 에서 멈춤, 중단점이있는 함수, generator 에선 yield넣으면 멈춤)
    suspended
ex 
const gen = function* () {
	console.log(1)
	yield;
	console.log(2)
	yield;
	console.log(3)
	yield 4;
}
const generator = gen()
generator.next()
(1)
generator.next()
(2)
generator.next()
(3) value 4 
----------------------
let i = 0 ; 
const gen = function* (){ // saga 에서 사용 예
  while (true) {
    yield i++;
  }
}
const g = gen()
g.next()
(value:0 (중단점 i 출력 후 종료))
g.next() (재 호출 시 i++ 숫자 한번찍히고 yield 중단점에서 종료)
(value:1 (중단점 i 출력 후 종료))
.
.
.
g.next() (재 호출 시 i++ 숫자 한번찍히고 yield 중단점에서 종료)
(value:9999 (중단점 i 출력 후 종료))

무한의 개념은 제너레이터로 많이 표현한다.

제너레이터는 이벤트 리스너 처럼 사용 가능
  제너레이터를 활용한 이벤트 리스너


function* watchLogin () {// 로그인 액션이 실행될때까지 기다리겠다는 뜻
	yield take('LOG_IN_REQUEST', logIn) 
  //LOG_IN_REQUEST 액션이 실행되면 logIn 함수 실행
}
-------------------------------
function* logIn() {
	try { // 요청 실패 대비
		const result = yield call(logInAPI) // 서버에서 받은 결과 값을 받음
		yield put({
			type: 'LOG_IN_SUCCESS',
			data: result.data // (성공 결과 담김)
		})
	} catch (err) {
		yield put({ // put 은 dispatch 라고 생각하자 
			type: 'LOG_IN_FAILURE',
			data: err.response.data // (실패 결과 담김)
		})
	}
}
saga effect 앞에는 yield 를 붙여주자
  saga 는 test 할때 엄청편하게된다 
    generator 를 사용하면 테스트를 한 줄 한 줄 돌려볼 수 있어서 엄청편하다.

fork 와 call 의 명확한 차이점
  fork 는 비동기 함수 호출 , 요청보내고 논블록킹 후 바로 실행
  ( 결과 값을 받아 올떄까지 안 기다려주며 다음 줄로 진행)
  call 은 동기 함수 호출 로그인 api 가 리턴할때까지 기다려서 result 에 넣어줌
    ( 결과 값을 받아 올떄까지 기다려준다)
ex basic pattern
function logInAPI() { // gererator 아님
	return axios.post('/api/login') // 실제 서버에 로그인 요청을 보냄
}
function* logIn() {
	try { // 요청 실패 대비
		const result = yield call(logInAPI) // 서버에서 받은 결과 값을 받음
		yield put({
			type: 'LOG_IN_SUCCESS',
			data: result.data // (성공 결과 담김)
		})
	} catch (err) {
		yield put({ // put 은 dispatch 라고 생각하자
			type: 'LOG_IN_FAILURE',
			data: err.response.data // (실패 결과 담김)
		})
	}
}
function* watchLogIn() {	// 로그인 액션이 실행될때까지 기다리겠다는 뜻
//LOG_IN_REQUEST 액션이 실행되면 logIn 함수 실행
	yield take('LOG_IN_REQUEST', logIn) 
}
//  fork or call 로 generator 함수를 실행 해준다.
export default function* rootSaga() {
	yield all([ // ALL 배열안에 한방에 실행해줌
			fork(watchLogin), // fork 는 (함수)실행
			fork(watchLogOut),	// call 이랑은 다르다.
			fork(watchAddPost),
	])
}
----------------------------------------------------------------
const result = yield call(logInAPI, action.data) 
// 서버에서 받은 결과 값을 받음
(logInAPI, action.data, a,b,c)  첫번째 자리 함수, 그 이후로는 매개변수
----------------------------------------------------------------
take는 (문자열,함수)같은 인수를 허용하지 않습니다

태그안에 인라인으로 css 을 적용하면 성능최적화에 안좋다고 하셨는데,
  그럼 태그별로 클래스명을 주고 css파일을 따로만들어서 css을 정의하는 방식은  
    성능최적화에 좋은지안좋은지 여부와 , 또다른 단점이 있다면 알고싶습니다
  :css로 하는 것이 성능에는 더 좋습니다. 인라인스타일은 리렌더링을 유발하거든요.
    단점은 리액트 측면에서는 없는 것 같긴 합니다.

next는 saga가 내부적으로 실행하므로 result 값도 saga가 알아서 할당합니다
  그래서 원래 제너레이터를 쓸 때는 yield에서 멈추지만 saga가 next를 
    계속 순서대로 호출하므로 우리의 눈에는 중단되는 것처럼 보이지 않습니다. 
      next를 호출하면서 Promise는 resolve 해서 next를 호출하므로 
        async/await 같은 효과를 낼 수 있습니다

제너레이터는 yield call이 await이라고 보시면 됩니다. 
  yield fork를 쓰면 await 없이 promise를 호출하는 것이고요. 
    둘 다 논블럭/비동기입니다

{type: `액션타입`} 형태여야만 takeLatest('액션타입')이 인식이되는지 궁금합니다.
  :네 이게 맞습니다. 둘이 같으면 takeLatest가 반응합니다. 
    이벤트리스너같은 것과 유사하다고 보시면 됩니다

yield take 치명적인 단점 : 일회용이다.
  단점 보완 : while 문으로 감싸주면된다
  // 로그인 액션이 실행될때까지 기다리겠다는 뜻
function* watchLogOut() {	
	while (true) {
    //LOG_IN_REQUEST 액션이 실행되면 logIn 함수 실행
		yield take('LOG_OUT_REQUEST', logOut) 
	}
}
while take 는 동기적으로 동작하지만, takeEvery 는 비동기로 동작한다는 차이가있음
function* watchAddPost() {
	yield takeEvery('ADD_POST_REQUEST', addPost)
}

takeLatest 
  100 번을 동시에 눌러도 99개 무시되고 마지막 것만 알아서 실행 해준다.
    완료된것은 그냥 냅두고 동시에 로딩중인것을 취소해준다.
      만약 서버에 두번 요청이 들어가게되면 요청은 두번들어가게되지만
        응답은 하나만 돌아온다. (서버에서 요청이 남아있는지 확인해줘야한다.)
takeLatest는 이전 요청이 끝나기도 전에 다시 요청을 보낼 때 적용됩니다
takeLeading
  여러번 빠르게누르더라도 첫 번째 것만 알아서 실행 해준다.
  function* watchAddPost() {
	yield takeLatest('ADD_POST_REQUEST', addPost)
}
throttle 
 function* watchAddPost() {
	yield throttle('ADD_POST_REQUEST', addPost, 3000)
} // 3 초 동안 요청이 한번만 갈 수 있게한다.
throttle(밀리초, 이름, 액션)에서 액션이 한번만 실행됩니다

서버를 구현하기 전까지는 딜레이로 비동기적인 효과를 주자
구현하면 딜레이를 지우고 실제 서버로 요청을 보내는데

쓰로틀링:마지막 함수가 호출된 후 일정 시간이 지나기 전에 다시 호출되지 않도록
디바운싱:연이어 호출되는 함수들 중 마지막 함수(또는 제일 처음)만 호출하도록 하는것
  debounce는 호출되고 일정 시간이 지나야만 실제로 실행되고 시간이 
    지나기전에 재호출되면 이전게 취소됩니다
여려번의 요청으로 중복 저장이 발생되는것을 막는방법
  loading을 사용해서 막는 게 좋습니다. 
    reducer의 state보다는 컴포넌트에 useState로 만들어야 좀 간단합니다

다른 이펙트들은 사라지지않나요??
  :사라집니다. 질문의 의도를 추측해보자면 take은 한 번 실행하고 더이상 
    실행이 안되는데 delay랑 Put은 왜 다음번에 되는지를 물어보시는 것 같은데요.
      watch 함수는 한 번만 실행되고 login* 함수같은 것은 매번 실행돼서
        그렇습니다. 하나의 함수 안에서 더이상 호출이 안 되는거지 
          새로운 함수가 또 실행되면 새 함수 안에서는 실행됩니다

REQUEST 일때엔 보통 ing 가 true 가 된다.

비동기 요청은 항상 셋쌍씩있다 :request, success, failure

// 로그인 동작 루트
로그인폼에서 로그인을 하고, 아이디 비번 적고 로그인 누르면
  로그인 리퀘스트 액션이 실행, 그러면 sagas user.js 에 'LOG_IN_REQUEST'가 뜨며
    로그인 실행되면서 리듀서스의 user.js 에 switch 동시에 실행된다
      1초 뒤에 'LOG_IN_SUCCESS' 가 되면서 디스패치되면 리듀서에 user.js 에
        'LOG_IN_SUCCESS' 가 실행되는 순간 me 에 data 가 들어가면
          isLoggedIn 이 true 가 되며 AppLayOut 에서 <UserProfile /> 로 바뀜

리액트 코드스플리팅에서는 필요한 데이터를 
  같이 불러오지 못하고 html js css만 불러옵니다
    컴포넌트가 마운트된 후 불러옵니다

nextjs는 프론트서버로 쓰고 스프링은 api서버로 쓰시면 됩니다
  nextjs가 제공하는 ssr 외의 검색엔진 최적화는 직접 하셔야 합니다

logInRequestAction 함수를 호출했으므로 
  dispatch({ type: LOG_IN_REQUEST, data })가 됩니다. 
    이러면 해당하는 타입의 reducer와 saga가 실행됩니다.

saga애서는 put이 dispatch입니다. 
  LOG_IN_SUCCESS 액션이 dispatch되어 그에 따른 reducer가 실행됩니다

로그아웃은 서버에서 처리해주어야 합니다. 
  안 그러면 당장은 로그인이 풀린 것 같더라도 새로고침하면 
    다시 로그인 되어 있게 됩니다

{}가 없는 것은 return이 생략된 것입니다.
  state => state.user 또는 state => (state.user)는
    state => { return state.user }와 같습니다

dispatch가 호출되면 reducer의 switch의 LOG_IN_REQUEST도 실행되고, 
  takeEvery(LOG_IN_REQUEST)의 콜백인 login도 실행됩니다. 
    저희가 configureStore.js에서 사가를 연결해줬는데 
      그 때 알아서 saga도 실행되는 것입니다

실제 서비스를 하다 보면 로딩창을 여러 개 사용하는 경우가 많습니다. 
  그래서 로딩을 각각 두었습니다. 로딩 모듈이 뭘 의미하시는지 잘 모르겠습니다만
    저도 시도해본 결과 로딩 부분을 공통적으로 쓰기는 조금 힘들었습니다

mysql db 를 사용 할때 id 값을 자동으로 하나씩 붙여주는게 있기에 헷갈릴 수 있어서
  id 를 email 로 사용 하는게 편한점이있따

postForm 에서도 submit comment 할때 dispatch 를 해주자

addPost 가 있고 실제로 axios 로 네트워크 요청하게하면 
  오류가 떠서 catch 로 갈수도 있는데 이때 보통 어떤식으로 처리하나요?
:ADD_POST_FAILURE 리듀서에서 받은 action.data(에러 내용)를 
  리덕스에 저장하고, 컴포넌트에서는 에러 데이터를 useEffect로 
    감시하고 있다가 에러 데이터가 발생하면 그에 따라 처리합니다

비동기가 아닌 것들은 reducer에서 처리하시면 됩니다

take의 경우는
  yield take(액션);
  함수();
    이런식으로 두줄에 걸쳐 적어주세요

불변성의 핵심은 바뀌는것만 새로운 객체로만들고 나머지 객체는 참조를 유지해야한다
  그래야만 바뀌는것만 바뀌고 안바뀌는것은 참조하는것을 유지하기때문에 메모리를
    절약할 수가있다.

const post = {...state.mainPosts[postIndex]}
  부분이 왜 {}로 감싸져 있는걸까요?? 대괄호인 []로 감싸져야 하는게 아닐까요??
      그 아래인 const mainPosts = [...state.mainPosts]로 
        []로 감싸져 있는데 왜그런걸까요 
:post는 일반 객체입니다. mainPosts는 배열이고요.
  일반 객체는 {...}고, 일반 배열은 [...]로 얕은 복사합니다

type이 일치하면 액션이 saga에 전달됩니다. type이 중요합니다

단순히 =는 쓰지 못하므로, 불변성 메서드를 사용해야 합니다. slice, concat 등

include라는 기능(SQL의 JOIN)을 써서 만든 속성은 대문자가 됩니다

data 관련된것들은 reducer 에서 관리
--------------------------------------------------------
대문자로 된 애들은 서버에서 주는애들이며 아이디가 고유하게 붙어있어야한다.
	Comments: [
				{
					id: shortId.generate(),
					User: {
						id: shortId.generate(),
						nickname: 'nero',
					},
					content: '개정판이 나왔네요!?',
				},
--------------------------------------------------------
포스트 리듀서에 게시글이 추가되면 유저 리듀서에 자신이쓴 게시글이 아이디가 
  추가되어야 1에서 2로 오르고, 포스트 리듀서에있는 글 중 하나를 삭제했을때
    유저 리듀서에있는 자신의 포스트 데이터에서도 2에서 1로 빠져야 게시글이 
      1로 빠진다 
상태는 액션을 통해서만 바꿀수있기에 액션을 만들어주면된다.
포스트 사가에서 유저의 액션을 호출할수있다.

사가는 동시에 여러 액션을 디스패치할수있기때문에 어떤 액션이 여러 리듀서의
  데이터를 동시에 바꿔야한다면 액션을 여러번 호출해주면된다. 
    포스트 리듀서에서는 포스터 리듀서 액션으로 바꾸고 
      유저 리듀서에서는 유저 리듀서 액션으로 바꿔주면된다.

redux devtools 로 에러를 추적하는 습관을 들이자

propTypes 경고는 id 가 숫자가아닌 문자여서 뜨는거며, 백엔드가 완성되면
  id 가 숫자로 나오니까 백엔드 완성 전까지 떠있어도 상관없다.

react-query는 query에 관련된 것만 최적화하는 것이 주 목적입니다. 
  다만 그게 사실 전역상태관리의 대부분이라서 어쩌다보니 
    redux를 대체할 수는 있습니다. 저는 프로젝트에서 필요한 경우 둘 다 씁니다

saga는 api 통신 등 비동기적인 작업을 하는 역할입니다. 
  dispatch는 reducer 담당입니다. 그 중 REQUEST관련 액션들만 
    특별히 saga가 watch를 통해 관련 saga를 실행할 뿐입니다. 
      saga는 비동기작업 후 dispatch를 통해 다시 reducer를 조작합니다

saga를 쓰는 이유는 화면과 비동기 요청을 보내는 부분을 분리하기 위함입니다. 
  코드는 좀 더 길어지고 파일은 많아지더라도 나중에 관리하기는 더 편해집니다

POST 요청을 보내고 서버에서 DB를 갱신한 뒤 응답으로 새로운 데이터를 가져옵니다
  요청은 POST 요청 한 번만 보내면 됩니다. 응답을 받을 때 saga에서 dispatch를
    통해 리덕스를 갱신해줍니다. 요청-응답 모두를 saga에서 처리할 수 있습니다

immer
// 기본 꼴
return produce(state, (draft) => {
		
	})
state 는 draft 로 이름이 바뀐다.
  produce 를 사용하면 불변성을 신경쓰지않아도된다.
    immer 가 알아서 state 를 불변성을 지켜서 다음 상태(불변성있게)로 만들어준다.
      state 를 건들면안되며 draft 만 조작
        state 를 draft 로 교체 
          불변성에 관한건 immer 가 알아서 불변성 유지해줌
const reducer = (state = initialState, action) => {
	return produce(state, (draft) => {
		switch (action.type) {
			case ADD_POST_REQUEST:
				draft.addPostLoading = true;
				draft.addPostDone = false;
				draft.addPostError = null;
				break;
				return { // 을 위의 draft 로 모두 교체
					...state,
					addPostLoading: true,
					addPostDone: false,
					addPostError: null,
				}

draft.mainPosts = draft.mainPosts.filter((v) => v.id !== action.data) 
// 지울땐 보통 filter 가 편하다
아니면 splice 를 사용해야하는데 인덱스를 찾아야하며 인덱스를 찾으려면 한줄 늘어남
case ADD_COMMENT_SUCCESS: {
				//action.data.content, postId, userId
				const post = draft.mainPosts.find((v) => v.id === action.data.postId) // 게시글 찾기
				post.Comments.unshift(dummyComment(action.data.content))
				draft.addCommentLoading = false
				draft.addCommentDone = true
				break;

위아래와 같이 index 로 찾기 위한 코드 량 차이 

				const postIndex = state.mainPosts.findIndex((v) => v.id === action.data.postId)
				const post = {...state.mainPosts[postIndex]}
				post.Comments = [dummyComment(action.data.content), ...post.Comments]
				const mainPosts = [...state.mainPosts]
				mainPosts[postIndex] = post
				return {
					...state,
					mainPosts,
					//mainPosts: [dummyPost, ...state.mainPosts], // 불변성 지켜주며 앞에다가 추가해야 게시글 위에올라감
					addCommentLoading: false,
					addCommentDone: true,
				}

reducer
  이전 상태를 액션을 통해 다음 상태로 만들어내는 함수
    불변성은 지키면서! 단 produce 를 사용하면 불변성을 신경쓰지않아도된다.
    
findIndex 대신 find 써준 이유
:draft를 써서 굳이 불변성 유지를 신경써줄 필요가 없어졌기 때문에
  Index를 찾을 필요없이 그냥 바로 find를써서 
    v.id === action.data.postId인 객체를 찾아줌

draft를 mutable 하게 변경하면 내부적으로 변경점을 
  immutable 하게 state 에 반영하는 겁니다

// concat 을 할땐 항상 앞에 대입을 해줘야한다 그래야 합쳐짐
  initialState.mainPosts = initialState.mainPosts.concat(

프론트는 백엔드가 준비가 덜 되었더라도 더미데이터 리덕스, 사가 딜레이 같은걸로
  미리 프론트를 다 만들어놓으면된다, 나중에 사가에서 딜레이해놓은거 지우고 
    실제 서버 요청으로 바꾸면된다 이부분만 교체하면 백엔드 데이터로 교체할수있도록

deps 배열에객체를 넣는 것은 매우 안 좋은 습관입니다. 참조문제 때문에요

실제 개발시에 shortId, faker 같은 라이브러리는 실제 배포시에는 사용안하니까 
  설치시에 -D 옵션으로 devDependencies 로 빼주는게 맞다

useEffect 로 컴포넌트 디드마운트와 같은 효과 가능 , 뒤에 빈배열만 넣는다면

유즈 이펙트에서 윈도우 addEventListener 를 사용할땐 항상 리턴을 해줘야한다.
  스크롤했던거 해제해줘야한다, 안그러면 메모리에 쌓여있는다.

// (높이를 나타내는것중)scrollY,clientHeight,scrollHeight 를 많이사용
console.log(window.scrollY, document.documentElement.clientHeight,
  document.documentElement.scrollHeight)

scrollY
: 얼마나 내렸는지
clientHeight
: 화면 보이는 길이
scrollHeight
: 총 길이
끝까지 다 내렸는지 확인하는 방법은 scrollY + clientHeight = scrollHeight
끝까지 내렸을때 로딩 코드
window.scrollY + document.documentElement.clientHeight === 
  document.documentElement.scrollHeight

실무에서는 보통, 끝까지 다 내린다음에 더보기로 추가해주지않으며, 
  300 px 정도 남았을때 미리 로딩을 시켜놓는다
window.scrollY + document.documentElement.clientHeight > 
  document.documentElement.scrollHeight - 300

useEffect 로 초기에 불러오고 스크롤 위치를 파악해서 설정해주면된다

react virtualized 를 사용하면, 무한 스크롤링을 해도 메모리가 폭파되지않는다
  예를들어 화면에 2 개씩의 게시물이 보인다면 내릴때마다 제일 위의 게시물이
  사라지며, 올릴때마다 제일 아래의 게시물이 사라진다
    (사라진다 == 메모리에 저장)
프로젝트에 react virtualized 를 사용하면 좋다

시간순으로 10개씩 불러오고 있습니다. 최신게시물이 가장 위에 있게끔요

더이상 인피니트 스크롤링을 scroll 이벤트로 하지 않습니다. 
  너무 문제가 많아서요.intersectionObserver 사용합니다

addEventListener한 것은 반드시 컴포넌트가 끝나기 전에
  removeEventListener해야 메모리 문제가 발생하지 않습니다

extra 
  :  우측 상단에 추가의 공간을 줌

next 에서는 모두 js 로 사용해도된다, (react에서는 jsx 사용해야할때)
  node.js 를 이미 사용했다, next.js 에서 front server 를 사용할때
    node 를 사용한것이다.

게시글 수정하기
  게시글 수정누르면 textarea 로 바뀌면서 수정모드로 바꿀것임
    수정을했다 치면 saga 로 넘어가서 백엔드로 넘어갔다가 프론트로넘어와서
      성공했는지 실패했는지 보여줄것임
  1. reducer 에서 action 을 생성 해주자
  2. saga 에서 api 를 생성 해주자 
  3. route 에서 비즈니스 로직을 만들어주자 
  routes 에서 자신의 게시글 수정을 해주고 json 으로 보내주면
    saga 에서 data 가 들어가고 reducer 에서는 json 으로 받았던 
      PostId 와 content 로 업데이트가 된다 

  수정 누르면 textarea 로 바뀌게 해보자
  (editMode 는 true 면 textarea 를 보여주고 false 면 기존 게시글 보여줌)
    component post 에서 onClick 함수를 만들어주고 클릭하면 editMode true
      TextArea 안에 postData 가 들어가게 만들어주고 평소엔 false 로 
        useState 로 관리해주자, 게시글 수정 취소할때 editMode 를 false 로
          하려면 부모(PostCard.js)에서 설정을 해줘야한다
  propTypes isRequired 일때는 모든 사용처에 다 넣어줘야한다, 
  PostCardContent 의 editText 가 onChangePost 로 전달이되서, PostCard 에
  고차함수로들어가 dispatch 할때 사용 할 수있다

어드민 페이지 만들기
  어드민 페이지 만드는건 복잡하다
  forest-express-sequelize git search forestadmin.com 사이트에서
  회원가입 후 create a new project 에서 데이터베이스 설정 
  npm install -g forest-cli@latest -s 을 back 과 front 를 담은 폴더 
    경로에서 명령어 입력, 순서대로 쭉 명령어들 복붙해서 넣어주자
=============next.js nodeBird FrontEnd Finish===============

```