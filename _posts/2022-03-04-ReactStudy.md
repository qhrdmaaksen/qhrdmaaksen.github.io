---
layout: single
title: "리액트를 배워보자(웹게임) 01"
---

# 민우의 블로그 테스트중입니다.

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
-  html 에서 속성에 class 를 사용하지않으며 className 을 사용한다
-  html 에서 속성 for 를 사용하지 않으며 htmlFor 를 사용한다

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
        test: /\.jsx?/, // js & jsx 파일을 룰에 적용
        loader: 'babel-loader', // js & jsx 에 바벨을 적용해서 예전 문법에도 적용돼 돌아갈수있도록 해준다
        options: {
          presets: ['@babel/preset-env', '@babel/preset-react'],
          plugins: ['@babel/plugin-proposal-class-properties', `react-refresh/babel`],
        }
      }
    ]
  }, // modules - 엔트리에있는 파일을 읽고 거기에 모듈을 적용 후 아웃풋에 출력
  plugins: [new RefreshWebpackPlugin()],
  output: {
    path: path.join(__dirname, 'dist'), // dist 폴더 경로 설정
    filename: 'app.js', // 원하는 파일
  },
  devServer: {
    devMiddleware: { publicPath: '/dist'}, // 버전 업 되면서 변경됨 (웹팩 명령어 실행할때 dist 폴더안에 생성해줌)
    static: { directory: path.resolve(__dirname)}, // 버전 업 되면서 변경됨 ( 실제로 존재하는 정적 파일의 경로를 적어주면 됨)
    hot: true // 소스코드의 변경점을 감지하여 dist폴더의 결과물을 수정을 해줌 ? (기존 데이터를 유지하며 리로딩)
  }
}
-------------------------------------------------------------
  다음으로 client.jsx 파일 생성 후
  const React = require('react');
  const ReactDOM = require('react-dom'); // (리액트와 리액트돔 불러오기)
  const GuGuDan = require('./GuGuDan') // const 변수 = require('파일경로및이름')
  ReactDOM.render(<component />, document.querySelector('#root'))
  이렇게 하면 더이상 위에 파일들을 더이상 html에 표기하지 않아도된다 babel 포함

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

```
