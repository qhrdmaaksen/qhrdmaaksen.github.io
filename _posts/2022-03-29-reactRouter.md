---
layout: post
title: "reactRouter 개념 및 정리"
---

## 개념 및 참고 코드 정리

react-router 설치 (설치원하는 경로 설정 후)
  npm i react-router
  npm i react-router-dom (use web)
  npm i react-router-native (use app)

```js

import React from 'react';
import { BrowserRouter, HashRouter } from 'react-router-dom';

const Games = () => {
  return (
      <BrowserRouter>
        <div>
          <Link to="/number-baseball">숫자 야구</Link>                    // 레이아웃
          &nbsp;
          <Link to="/rock-scissors-paper">가위바위보</Link>
          &nbsp;
          <Link to="/lotto-generator">로또추첨기</Link>
          &nbsp;
        </div>
        <div>
          <Routes path="/number-baseball" component={NumberBaseBall} />                 // route
          <Routes path="/rock-scissors-paper" component={RSP} />
          <Routes path="/lotto-generator" component={Lotto} />
        </div>
      </BrowserRouter>
  );
};

export default Games;
```

리액트는 native 가 있기때문에 ? 웹에서도 앱에서도 사용할 수 있다.
router 

hashRouter 의 장점은 새로고침을 해도 동작은 한다 (검색엔진이 중요하기때문에 실무에서는 잘안쓴다?)
- 검색엔진에 뜨지않는다 ?
BrowserRouter 는 새로고침을 하면 동작안한다
- BrowserRouter 를 사용해도 SEO 에 맞는 설정을 따로 해줘야한다 
--- 서버는 모르고 브라우저는 안다

<Routes path='/game/:name' component={GameMatcher} /> 
- :name 은 파라미터로 무엇으로든 변할수있다. ( 동적 라우트 매칭 )
- 대신 게임매쳐의 코드가 길어진다 ?

history
- 페이지를 넘어다니는 내역을 간직하고있다 .
- 리액트 라우터는 눈속임이기때문에 페이지를 넘어다니는 api 도 browser 가 제공하는 api 를 사용하면안되며, 
-- history 를 사용해서 확인한다


location 
- 주소 해쉬 서치 등 정보 담겨있다.

매치
- 동적 주소 라우팅할때 파람스 부분에 대한 정보가 담겨있음

api 의 관계를 파악해놓는게 좋다 ? 의존관계, 역할

query 부분은 location 의 search 부분에 있다 . 

서버도 페이지가 여러개인지 모르기때문에 따로 알려줘야 검색엔진 로봇이 긁어갈수있다


let urlSearchParams = new URLSearchParams(this.props.location.search.slice(1))
- 리액트 라우트에서는 쿼리스트링을 해석하는걸 제공하지 않기때문에 urlSearchParams 를 사용하는게좋다

{/*<Routes path='/game/:name' render={(props) => <GameMatcher {...props}/>} /> props 를 게임매쳐에넘기고싶을때*/}

<Routes exact path='/game/number-baseball/' render={(props) => <GameMatcher {...props} />} />
- exact 를 붙이면 path 의 경로가 조금이라도 다르면 렌더링되지않는다. 
-- 붙이지않을때 path='/' 경로가 왼쪽과같이만 되있어도 /game/number-baseball/ 경로와 같다고 인식한다
-- 이럴때 exact 를 사용해주면좋다?

// 스위치는 반드시 칠드런중에 하나만 실행된다, 스위치를 사용하지않으면 하위 경로 모두 실행된다
 <Switch>
          <Routes exact path="/" render={() => <GameMatcher />} />
          <Routes
            path="/game/:name/"
            render={(props) => <GameMatcher {...props} />}
          />
        </Switch>

=================================================

import React, { Component } from "react";
import { withRouter } from "react-router-dom";
import NumberBaseBall from "../BaseBallGameFolder/baseBallGame";
import RSP from "../scissorsRockPaperGame/RSPgameClass";
import Lotto from "../LottoGameFolder/lottoGameClass";

class GameMatcher extends Component {
  render() {
		let urlSearchParams = new URLSearchParams(this.props.location.search.slice(1))
		console.log(urlSearchParams.get('hello'))
    if (this.props.match.params.name === 'number-baseball') {
			return <NumberBaseBall />
		} else if (this.props.match.params.name === 'rock-scissors-paper') {
			return <RSP />
		} else if (this.props.match.params.name === 'lotto-scissors-paper') {
			return <Lotto />
		}
    return (
      <>
        <div>일치하는 게임이 없습니다.</div>
      </>
    );
  }
}

export default GameMatcher;

==================================================

react-router v6 에서는 <Switch> 가 없어졌으며, <Routes> 로 바뀌었다.

버전은 공식문서에서 changeLog or migration , release check

v6 버전에서는 render(), component 가 사라지고 element 로 통합?
<Routes>
          <Route path="/" element={<GameMatcher />} />
          <Route path="/game/:name/" element={<GameMatcher />} />
        </Routes>


codemod 라이브러리 버전에따라 전체 코드 수정해준다 ?

어우어렵당.... 다시공부하자;;