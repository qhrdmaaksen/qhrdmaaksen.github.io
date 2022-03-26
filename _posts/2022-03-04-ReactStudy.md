---
layout: post
title: "리액트를 배워보자(웹게임) 01"
---

# 민우의 블로그 테스트중입니다

```js

리액트 =
- 사용자 인터페이스를 만들기 위한 js 라이브러리
- 데이터 처리를 쉽게 함
- 데이터와 화면의 싱크를 맞춰준다 ? 화면일치
- 재사용 컴포넌트 (중복되는 요소들을 하나로 묶어주기에 유지보수하기 좋다)

webPack 은 쪼개어진 자바스크립트 파일을 html 이 실행 할 수 있는 js 로 합쳐준다
----------------------------------------------------------------------------------------------------------------------------------
<!--리액트를 사용하려면 필수 파일 두개-->
  <!--개발 단계이기때문에 development.js 로 사용하며 실제 배포할때엔 production.js 로 변환-->
  <!--첫번째 파일은 리액트의 핵심적인 요소가 담긴 자바스크립트 파일-->
  <script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
  <!--react-dom 은 리액트를 웹에다가 붙여주는 역할-->
  <script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
  <!--최신 문법들을 js 에서 사용할 수 있도록 해주는 babel-->
  <script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>

  <script type="text/babel">//사용될 script 에 type babel 지정해주면 적용됨</script>
----------------------------------------------------------------------------------------------------------------------------------
  기본적으로 리액트에는 컴포넌트들을 렌더링할곳인 root 가 필요하다

  state 상태가 들어간다는건 바뀔수있다는 뜻

  클래스 하나당 컴포넌트 하나다?


  컴포넌트 장점 = 원하는 개수만큼 늘릴 수 있음

  대문자로 시작하는 태그는 리액트 컴포넌트
  소문자로 시작하는 태그는 html 태그
----------------------------------------------------------------------------------------------------------------------------------
  <script type="text/babel">
    //ReactDOM 은 만들것을 웹에 랜더링을 하겠다 (화면에 실제로 반영) (ReactDOM 에 DOM 은 모두 대문자다... 조심하자)
    //ReactDOM.render(e(LikeButton), document.querySelector(`#root`));//위에 id= root 에 그린다.

    ReactDOM.render(<LikeButton />, document.querySelector(`#root`));
  </script>
----------------------------------------------------------------------------------------------------------------------------------
  //JSX와 HTML 을 섞어서 쓰지 않기위해 함수로 따로 만들어서 사용하자

  return 할때 div 태그로 감싸줘야하지만 신경쓰인다면 <> </> 로 해두면된다. (빈태그) 혹시 에러가 발생한다면 <React.fragment> </React.Fragment> 사용

  직접 내가 만든 함수는 화살표 함수를 꼭 사용해야한다 . function 을 사용하게됐을 경우 this 가 달라진다.

Hooks - 함수컴포넌트에서도 ref 랑 state 를 사용 할 수 있게 해줌
- ref를 사용하면 current 를 같이 넣어줘야한다
-  html 에서 속성에 class 를 사용하지않으며 className 을 사용한다
-  html 에서 속성 for 를 사용하지 않으며 htmlFor 를 사용한다

  state 와 ref 의 차이점 (값을 바꾸고싶다는 의미는 같음)
  - setState 를 사용하면 리턴부분이 다시 실행된다.(렌더링)
  - ref 가 사용될땐 리턴부분이 다시실행되지않는다.
  리턴 부분이 렌더링되지않게(화면에 영향을 끼치고싶지않다면) 하고싶다면 ref 를 사용하면된다. 

  hooks 가 아닌 class 사용시 render 함수만 재실행되지만 함수 컴포넌트 사용시엔 전체가 재실행된다 ?
----------------------------------------------------------------------------------------------------------------------------------
  노드는 자바스크립트 실행기 그 이상 이하도 아니다

  webPack 을 사용하기 전에 npm 과 node 를 준비해야한다
  터미널로 사용될 폴더지정이 되있다면 npm init 해주고
  필요한 정보를 입력해준 후 yes 엔터
  터미널에 npm i react react-dom 입력  (리액트랑 리액트 돔을 설치하겠다)
  다음으로  npm i webpack webpack-cli 리액트할때 필요한 웹팩을 설치해줘야함
  다음으로 webpack5번전으로시작한다면 npm i react-refresh @pmmmwh/react-refresh-webpack-plugin -D
  다음으로 서버- npm i -D webpack-dev-server
  //바벨 설치 -D 는 개발자 모드
npm i -D @babel/core //core 에는 바벨의 기본적인것이 들어있음
npm i -D @babel/preset-env // 사용하고있는 브라우저에 맞게 최신문법을 옛날 문법을 지원하는것으로 바꿔줌
npm i -- @babel/preset-react // jsx 도 지원해줌
npm i -D babel-loader //바벨과 웹팩을 연결해줌
npm i -D @babel/plugin-proposal-class-properties //필요하다면 설치

  다음으로 폴더에 webpack.config.js 파일 생성후 아래와 같이 작성
const path = require('path')
const RefreshWebpackPlugin = require('@pmmmwh/react-refresh-webpack-plugin') // 핫 로드? 리로딩

module.exports = {
  name: 'wordrelay-setting',
  mode: 'development', // 실서비스 사용할땐 : production 으로 변경
  devtool: 'eval', // 빠르게
  resolve: {
    extensions: ['.js', '.json', '.jsx', '.css']
  },
  entry: {
    app: ['./client'] // 입력 할 파일 설정 ( WordRelay.jsx 파일을 client.jsx 에서 불러오고있기때문에 적어줄 필요없다), resolve 에서 확장자를 설정해줬기에 따로 확장자를 안붙여줘도된다
  }, // 입력

  module: {
    rules: [
      {
        test: /\.jsx?$/, // js & jsx 파일을 룰에 적용
        loader: 'babel-loader', // js & jsx 에 바벨을 적용해서 예전 문법에도 적용돼 돌아갈수있도록 해준다
        options: {
          presets: ['@babel/preset-env', '@babel/preset-react'],
          plugins: [`react-refresh/babel`],
        },
        exclude: path.join(__dirname, 'node_modules'),
      }
    ]
  }, // modules - 엔트리에있는 파일을 읽고 거기에 모듈을 적용 후 아웃풋에 출력
  plugins: [new RefreshWebpackPlugin()],
  output: {
    path: path.join(__dirname, 'dist'), // dist 폴더 경로 설정
    filename: 'app.js', // 원하는 파일
    publicPath: './dist',
  },
  devServer: {
    devMiddleware: { publicPath: '/dist'}, // 버전 업 되면서 변경됨 (웹팩 명령어 실행할때 dist 폴더안에 생성해줌)
    static: { directory: path.resolve(__dirname)}, // 버전 업 되면서 변경됨 ( 실제로 존재하는 정적 파일의 경로를 적어주면 됨)
    hot: true // 소스코드의 변경점을 감지하여 dist폴더의 결과물을 수정을 해줌 ? (기존 데이터를 유지하며 리로딩)
  }
}
-------------------------------------------------------------
  다음으로 client.jsx 파일 생성 후
import React from 'react';
import ReactDOM from 'react-dom';
import TicTacToe from './TicTacToeClass';
ReactDOM.render(<TicTacToe />, document.querySelector('#root'));

또는 

  const React = require('react');
  const ReactDOM = require('react-dom'); // (리액트와 리액트돔 불러오기)
  const GuGuDan = require('./GuGuDan') // const 변수 = require('파일경로및이름')
  ReactDOM.render(<component />, document.querySelector('#root'))
  이렇게 하면 더이상 위에 파일들을 더이상 html에 표기하지 않아도된다(script, link 등) babel 포함

  <body>
  <div id="root"></div>
  <script src="./dist/app.js"></script>
  </body>
  바디에 이렇게 적어주면 리액트 기본 세팅 끝

  위와 같이 수동으로 직접 다 해줬지만 create react app 이 따로있으며 이것은 위와같은 설정들을 자동으로 해준다 ?

  확장자를 리액트를 사용할땐 jsx 로 설정해주는게 다른사람이 파일을 볼때도 이것은 리액트가 들어가있겠구나라고 인지시켜주기에 jsx로 확장자를 설정해주자

  파일을 쪼개서 사용할때에 위에는 아래와 같이 적어주고
  const React = require(`react`); //npm 에서 react 를 불러옴

  <p>class 사용시엔</p>
  const { Component } = React; //React.Component 를 줄일 수 있다

  제일 아래에는 아래와 같이 작성해놓으면된다
  module.exports = componentName ; //쪼갠 파일의 컴포넌트를 밖에서도 사용할 수 있도록 설정

----------------------------------------------------------------------------------------------------------------------------------
module 시스템이 생기면서 몇만개의 클래스중에서 몇개만 사용하고싶다면
const WordRelay = require(`./WordRelay`); 와 같이 필요한것만 불러서 사용할수 있게됐다
----------------------------------------------------------------------------------------------------------------------------------

터미널에 첫번째로 터미널에 npx webpack 을 입력해 dist 폴더 생성 후

두번째로
package.json 에 scripts 에 따로
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "webpack serve --env development"
  },
  와 같이 ex_ "dev": "" 설정해주고 npm run dev 를 해주면 실행된다 webpack.config.js 에 mode: "development" 를 넣어줬지만 만약 안넣었다면 package.json 에서 따로 넣어줄수도있다


정말...오타조심하자 ㅠㅠ
npx webpack .. or 무언가를 설치할때.. 다시한번 꼭 터미널 경로 확인하자 정말정말 !

콘솔창에 HMR ( HOT MODULE RELOAD) , WDS (WEBPACK DEV SERVER)

inputRef.current.focus() // Hooks 에는 input 에 Ref와 current 를 항상 붙여줘야함

클래스 사용과 함수 컴포넌트 차이
======= 클래스 사용 ========
class RelrayFunc extends Component {
  state = {
    word: '김민우',
    value: '',
    result: '',
  }
onSubmitForm = (e) => {
    e.preventDefault();
    if (this.state.word[this.state.word.length - 1] === this.state.value[0]) { // 워드의 -1번째(마지막번째) === 인풋에입력한 값의 첫번째
      this.setState({
        result: `딩동댕,다음 문제 고고고!`,
        word: this.state.value,
        value: ``,
      })
      this.input.focus()
    } else {
      this.setState({
        result: `땡!, 틀렸습니다.`,
        value: ``,
      })
      this.input.focus()
    }
  }
======= 함수컴포넌트 사용 ========
const { useState, useRef } = React;

const HooksRelay = () => {
  const [word, setWord] = useState(`김민우`);
  const [value, setValue] = useState(``);
  const [result, setResult] = useState(``);
  const inputRef = useRef(null);

  const onSubmitForm = (e) => {
    e.preventDefault();
    if (word[word.length - 1] === value[0]) { // 워드의 -1번째(마지막번째) === 인풋에입력한 값의 첫번째
      setResult(`딩동댕,다음 문제 고고고!`),
      setWord(value),
      setValue(``),
      inputRef.current.focus() // Hooks 에는 input 에 Ref와 current 를 항상 붙여줘야함
    } else {
      setResult(`땡!, 틀렸습니다.`),
      setValue(``)
      inputRef.current.focus()
    }
  }
---------------------------------------------------------------------------------------------------------------------------------
export const hello = 'hello'; // import { hello } 와 같다 (변수 ?) 한번에 변수명만다르게해서 여러개를 사용할수도있다
노드 모듈 시스템에서 exports.hello = 'a' 와 module.export = { hello: 'a'}; 와 같다
const React = require('react') 와 같이 require 는 노드에서 사용하고
react 에서는 import React, { Component } from 'react' 로 사용한다 ,  export 도 마찬가지 ? import 나 export const 를 보고 당황하지 말자
export default NumberBaseBall; // import NumberBaseBall 과 같다 (module.export = NumberBaseBall; 와 호환되지만 좀 다름)

---------------------------------------------------------------------------------------------------------------------------------
리액트에서 반복문 사용할때엔
<ul>
          {['사과','바나나','like','like','like','like','like','like','like'].map( (v) => {

            return (
              <li>{v}</li>
            )
          })}
        </ul>
      배열에 넣어 맵으로 사용
================================================================
 {[
            {fruit:'사과',taste:'맛있다'},
            {fruit:'바나나',taste:'맛없다'},
            {fruit:'포도',taste:'시다'},
            {fruit:'귤',taste:'달달하다'}
          ].map( (v) => {
            return (
              <li><b>{v.fruit}</b> - {v.taste}</li>
            )
          })}
          객체 키 값으로 사용
----------------------------------------------------------------
배열에 추가할땐
js 에서는 array.push(2) 과 같이 추가해줬지만 react 에서는 새로운 변수 variableNew = [...originVariable,2] 와같이 추가해줘야한다
originVariable === variableNew ( 예전 state 와 현재 state 가 false 가 되어야 렌더링을 해주기때문에 ?)
-----------------------------------
const { result, value, tries } = this.state // 구조분해
this.state.result 는 result 와 같아진다

<Try key={`${i + 1}차 시도 : `} tryInfo={v} /> // html 에서는 속성이라 부르지만 리액트에서는 props 라고 불림

예전 state 로 현재 state 를 만들때엔 함수형 state 를 사용
  this.setState((prevState) => { // 예전 상태를 나타냄
        return {
          result: '홈런',
          tries: [...prevState.tries, { try: value, result: '홈런' }], // 예전 상태의 배열에 추가

----------------------------------------------------------------
port 번호 지정해주고 터미널  링크 찍고 타서 작업하자 ( 데브서버 반영이 안될 경우 )
----------------------------------------------------------------
컴포넌트 최적화
class Test extends Component {
  state = {
    counter: 0,
  }

  shouldComponentUpdate(nextProps, nextState, nextContext) { // 컴포넌트 최적화 (필요할때만 렌더링?)
    if (this.state.counter !== nextState.counter) { // 현재 카운터와 미래의 카운터가 같지않으면 렌더링
      return true
    }
    return false
  }
    ----------------------------------------------------------------
  자식 컴포넌트에서 모두 PureComponent 를 사용하고있다면 부모 코드에도 PureComponent 를 넣어주자
  hooks 도 memo 를 넣어주자
  import React, { PureComponent, memo } from 'react'; // class 의 pure component 와 같이 hooks 에서는 memo 를 추가해준다

const TryHooks = memo(({ tryInfo }) => { // hooks 에서 props 구조 분해 사용 ,  memo 추가 ( state 나 props 가 바뀌었을때만 렌더링을 해줌)
    ----------------------------------------------------------------
class component 에서 ref 를 설정할때 import React, { Component, createRef } from 'react'; 
createRef 를 만들어주면된다 . 로직에 inputRef = createRef() 넣어주면 input에 ref 에서도 그냥 this.inputRef 만 넣어주면됨
대신 hooks component 와 같이 input.current.focus() 와 같이 current를 추가해줘야함 이렇게하면 hooks 와 class component 가 
ref 추가에대해 코드가 비슷해짐
    ----------------------------------------------------------------
    render(){
      렌더 안에는 setState() 를 사용하면안된다. 렌더와 setState 가 서로 실행되기때문에 ?
    }
      ----------------------------------------------------------------
props 는 부모쪽에서 바꿔줘야하지 자식 컴포넌트에 props 를 직접적으로 바꾸면 안된다. 
바꾸려면 아래와 같이 바꿀수있다 ( state 로 만들어서 바꾼다) 그래야 부모한테 영향을 안끼친다
import React, { PureComponent, memo, useState } from 'react'; // class 의 pure component 와 같이 hooks 에서는 memo 를 추가해준다

const TryHooks = memo(({ tryInfo }) => { // hooks 에서 props 구조 분해 사용 ,  memo 추가 ( state 나 props 가 바뀌었을때만 렌더링을 해줌)

  const [result, setResult] = useState(tryInfo.try) 

  const onClick = () => {
    setResult('1')
  }

  return (
    <li>
      <div>{tryInfo.try}</div>
      <div onClick={onClick}>{result}</div>
    </li> // key 는 고유해야한다
  )
})
export default TryHooks;
    ----------------------------------------------------------------
    props 는 자식에게만 넘길수있으며 만약 뛰어넘어 손주에게 바로 넘기려한다면 context api 를 사용한다
    ----------------------------------------------------------------
  react 는 항상 js 역할만 담당한다는것을 인지하자
  render( ) 안에서는 for 와 if 를 사용할 수 없기때문에 다른방식을 사용해야한다 . ( 부호 연산자, 삼항 연산자, 반복문은 map)

  false, undefined, null 은 jsx 에서 tag 없음을 의미한다

  class component 를 사용할땐 구조분해 하는걸 습관화하자 this.state 같이 너무 자주 사용하는 경우가 많기때문이다
  const { state } = this.state
  ex_ state = ({
    state: '',
  })
  state.current.focus()
====================================================================================================================
리턴안에서 if 조건문 사용하는 방법
  return (
    <>
      <div id="screen" className={state} onClick={onClickScreen}>
        {message}
      </div>
      {(() => {                    {/* 리턴문안에서 if 문 사용하기 */}
        if (result.length === 0) {
          return null
        } else {
          return <>
            <div>평균 시간 : {result.reduce((a, c) => a + c) / result.length}ms</div>
            <button onClick={onReset}>리셋</button>
          </>
        }
      })}
      {/*{renderAverage()}if 문 사용하려고 잠깐 막아놓음*/} 
    </>
  )
====================================================================================================================
배열안에 jsx 를 사용 할수 있다 , jsx 에서 배열을 리턴할 수 있다
====================================================================================================================

Hooks 는 라이프 사이클을 가지고있지 않다. 하지만 비슷하게 아래와 같이 사용할 수 있다

useEffect(() => { // componentDidMount , componentDidUpdate 역할 ( 1 대 1 대응은 아님 )

    return () => { // componentWillUnmount 역할

    }
  }, []) // 배열에는 계속 바뀌는 state 지정? ( componentDidUpdate ?) 
  // 배열에는 꼭 useEffect 를 다시 실행할 값만 넣자
-------------------
useEffect 는 여러번 사용할 수 있다 . 계속해서 바뀔 state 를 따로 지정해야 할 경우
- 화면이 바뀐 다음에 실행 
----------------------------------------------------------------
부모 컴포넌트가 렌더링 될때마다 자식 컴포넌트도 렌더링 된다 이럴때 따로 지정하고 싶다면 memo 사용
------------------------------------------------------------------------------------------------
useLayoutEffect 는 화면이 바뀌기전에 발생, 화면 바뀌는걸 감지하는 이펙트

/*hooks useEffect =
                                                              useEffect 는 세로 
                          result , imgCoords , score
componentDidMount
componentDidUpdate
componentWillUnmount

// class component
componentDidMount() {
  this.setState({
    imgCoords: 2,
    score: 1,
    result: 3
  })
}
// hooks component
useEffect(()=> {
  setImgCoords(2)
  setScore(1)
}[score, imgCoords])

useEffect(()=> {
  setResult(3)
}[result])
*/
================================================================================================================
/*라이프 사이클 = 클래스의 경우 -> constructor -> rendering -> ref 부분실행 -> componentDidMount -> (setState or props바뀔때 -> shouldComponentUpdate(true)
 -> render -> componentDidUpdate -> 부모가 나를 없앨을때 -> componentWillUnmount -> 소멸 */

componentDidMount () { // 렌더가 처음 성공적으로 실행되었다면 componentDidMount 가 실행됨, 하지만 setState로 리렌더링이 될때엔 실행되진않음

componentWillUnmount () { // 컴포넌트가 제거되기 직전에 실행됨 , 부모가 자식 컴포넌트를 없앴을때 실행됨

componentDidUpdate () { // 리렌더링 후에 실행됨

class component 경우 componentDidMount or componentDidUpdate 에서 모든 state를 조건문으로 분기 처리한다
----------------------------------------------------------------
비동기 함수가 지역변수를 참조하면 클로즈 에러 발생

useMemo - 복잡한 함수 결과 값을 기억  (함수 리턴값)
// useMemo 는 값을 기억한다 input [] 이 바뀌기 전까지
useRef - 일반 값을 기억
useCallback - 함수 자체를 기억

}, [timeouts.current]); // useEffect 는 로직을 실행하는데 input [] 이 바뀔때 실행 

useCallback 안에 state 는 항상 [] 인풋에다가도 넣어줘야한다 . (인풋값이 바뀌어야 새로 실행된다)
const onClickRedo = useCallback(() => { // useCallback 은 함수를 기억한다. input [winNumbers] 가 바뀌기 전까지만

hooks 는 순서가 중요하다

자식 컴포넌트의 함수를 넘길때 (프롭스) 이럴땐 useCallback 을 꼭 사용해주자, 사용하지 않으면 부모로부터 받은 프롭스가 바뀌었다 인식하기에 리렌더링을 하게된다

훅스들은 최상위에 두도록하자

훅스를 한번 선언하면 그 순서(실행순서)가 바뀌지않게해야하며 조건문 안에 훅스를 넣으면 안되고 함수나 반복문 안에도 웬만하면 넣지 말자

useEffect 안에서 훅스(useState)등을 넣지 말자
비동기 상태에 따라서 처리할땐 useEffect 를 사용한다 

useEffect 로직은 componentDidMount 에 쓰일 로직을 넣는다. input[] 은 componentDidUpdate 라고 생각하자 상태변환이 될 state 를 넣어주자

class는 함수 한 번 선언하면 다시 선언될 일이 없습니다.

useEffect(() => {
  // ajax 
}, [])

const mounted = useRef(false)
useEffect(()=>{
  if (!mounted.current) {
    mounted.current = true 
  } else {
    // ajax
  }
}, [바뀌는 값]) // componentDidUpdate 에서만 , componentDidMount 에서는 x

dispatch({ type: 'SET_WINNER', winner: '0'}) // 디스패치안에는 액션을 만들어주고 액션안에 타입을 만들어줘야한다

const reducer = (state, action) => { // 액션을 dispatch 할때마다 reducer 가 실행
	switch (action.type) {
		case 'SET_WINNER':
			// state.winner = action.winner ; 이렇게(초기 값을 직접 바꿈) 하면 안된다
			return {
				...state, // 새로운 객체를 만들어서 값을 바꿔줘야한다.
				winner: action.winner,

action 의 이름은 보통 모두 대문자로 하는게 규칙이다햣

프롭스로 넣어두는 데이터는 useCallback 에 넣어주는게 좋으며 , 계속해서 값이 바뀔것같은 것은 input[] 에 넣어주면된다

렌더링을 리팩토링할떄 memo 를 먼저 사용해보고 적용이안된다면 최후의 수단으로 useMemo 를 사용해보자
useMemo 사용시 기억을 해제할땐 input[] 에는 바뀔여지가있는 state 를 넣어주자

useReducer 는 useState 가 많을때 state 를 하나로 묶어주는 역할
useReducer 에서 state 를 바꿀때엔 action 을 통해 dispatch 해서 초기 state는 건들지 않으면서 새로만들어 바꾼다
Reducer와 useReducer 차이점은 Reducer 는 state 가 동기적으로 바뀌는데 useReducer는 비동기적으로 바뀐다

```
