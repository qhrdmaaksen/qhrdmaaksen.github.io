---
layout: post
title: "리액트를 다루는 기술 정리"
---

## 코드는 재산이다, 나중에 도움된다, 정리잘하자

```js
--------------------------------------------------------
리액트는 구조가 mvc, mvw 등의 프레임워크와 달리 오직 view 만 싱경쓰는 라이브러리임
--------------------------------------------------------
컴포넌트: 재사용이 가능한 api 로 수많은 기능을 내장하고 있으며 컴포넌트 하나에 해당 컴포넌트의 생김새와 작동을 정의함
--------------------------------------------------------
render : 이 함수는 컴포넌트가 어떻게 생겼는지 정의하는 역할을 함/html 형식의 문자열을 반환하지않으며 뷰가 어떻게 생겼고 어떻게 작동하는지에대한 정보를 지닌 객체를 반환함/컴포넌트 내부에 또다른 컴포넌트들이 들어갈 수 있으며 이때 render 함수를 실행 시 내부에있는 컴포넌트들도 재귀적으로 렌더링함/최상위 컴포넌트의 렌더링이 끝나면 지니고있는 정보들을 사용해 html 마크업을 만들고 이를 우리가 정하는 실제 페이지의 돔 요소 안에 주입함/ 컴포넌트를 실제 페이지에 렌더링할땐 분리된 두가지 절차가 따르며 문자열 형태의 html 코드를 생성한 후 특정 dom 에 해당 내용을 주입하면 이벤트가 적용됨
--------------------------------------------------------
Virtual DOM
-실제 돔에 접근해 조작하는대신 추상화한 js 객체를 구성해 사용한다 예를들면 실제 돔의 가벼운 사본과 비슷함

-리액트에서 데이터가 변하면 웹 브라우저에 실제 돔을 업데이트할땐 3가지 절차를 밟음
--1.데이터를 업데이트하면 전체 ui 를 버츄얼 돔에 리렌더링함
--2.이전 버츄얼 돔에있던 내용과 현재 내용을 비교함
--3.바뀐 부분만 실제 돔에 적용함
--------------------------------------------------------
DOM
-document object model 객체로 문서 구조를 표현하는 방법으로 xml 이나 html 로 작성함

-웹 브라우저는 dom 을 활용해 객체에 자바스크립트와 css 를 적용함/ 돔은 트리 형태라 특정 노드를 찾거나 수정하거나 제거하거나 원하는 곳에 삽입할수있음

-돔의 치명적인 한가지 문제점은 동적 ui 에 최적화되어있지 않다/ html 은 자체적으로는 정적이며 js 를 사용해 이를 동적으로 만든다

-돔 자체는 빠르며 돔 자체를 읽고 쓸때의 성능은 js 객체 처리할때 성능과 비교하면 다르지않다

-웹 브라우저 단에서 돔에 변화가 일어나면 웹 브라우저가 css 를 다시 연산하고 레이아웃을 구성하고 페이지를 리 페인트하는데 이 과정에서 시간이 허비되는것임
--------------------------------------------------------
설치

node.js
-react app 은 웹 브라우저에서 실행되는 코드이므로 직접적인 연관은없지만 프로젝트를 개발하는데 필요한 주요도구들(ecmascript 를 호환시켜주는 바벨/ 모듈화된 코드를 한파일로 합치고(번들링) 코드를 수정할때마다 웹 브라우저를 리로딩하는 등의 여러기능을 가진 웹펩 등)

yarn
- npm 을 대체할 수 있는 도구이며  npm 보다 더 빠르고 효율적인 캐시 시스템 및 기타 부가 기능을 제공
--------------------------------------------------------
대표적인 번들러로 웹팩, 파셀 브라우저ify 도구들이있으며 리액트에서는 주로 웹팩을 사용

번들러 도구를 사용하면 import or require 로 모듈을 불러왔을때 불러온 모듈을 모두 합쳐서 하나의 파일을 생성해줌/ 최적화 과정에서 여러개의 파일로 분리될 수수도있음
--------------------------------------------------------
jsx
-js 확장 문법이며 xml 과 비슷하게 생김/브라우저에서 실행되기 전에 코드가 번들링되는 과정에서 바벨을 사용해 일반 js 형태의 코드로 변환됨

-컴포넌트에 여러 요소가 있다면 반드시 부모 요소 하나로 감싸야 함
--버츄얼 돔에서 컴포넌트 변화를 감지해 낼 때 효율적으로 비교할수있도록 컴포넌트 내부는 하나의 돔트리 구조로 이루어져야한다는 규칙때문임

jsx 는 공식적인 js 문법이 아님

jsx 장점
-가독성이 높고 작성하기 쉽다

-js 요소들을 일일이 만들어야하면 불편하기때문에 사용

-jsx 는 html tag 를 사용할수 있으며 컴포넌트도 jsx 안에서 작성가능


리액트 컴포넌트에서는 함수에서 undefined 만 반환하여 렌더링하는 상황을 만들면안된다. 만약 어떤 값이 undefined 일 수 있다면 or 연산자를 사용해 해당 값이 undefined 일 때 사용할 값을 지정할 수 있고 이로인해 오류를 방지 할 수 있다
-jsx 내부에서 undefined 를 렌더링하는것은 괜찮음
--------------------------------------------------------
ReactDOM.render
-컴포넌트를 페이지에 렌더링하는 역할을 함

-react-dom module 을 불러와 사용할 수 있음

-이 함수의 첫번째 파라미터에는 페이지에 렌더링할 내용을 jsx 형태로 작성/ 두번째 
파라미터에는 해당 jsx 를 렌더링할 document 내부 요소를 설정함
--------------------------------------------------------
화살표 함수
-화살표 함수는 주로 함수를 파라미터로 전달할 때 유용함

-기존 function 을 대체 할수없는것은 용도가 다르기때문임 서로 가르키고있는 this 값이 다름
--일반 함수는 자신이 종속된 객체를 this 로 가리키며 화살표 함수는 자신이 종속된 인스턴스를 가리킴

-화살표 함수는 값을 연산하여 바로 반환해야할때 사용하면 가독성을 높일 수 있음
--------------------------------------------------------
props
-컴포넌트 속성을 설정할때 사용하는 요소 / 프롭스 값은 해당 컴포넌트를 불러와 사용하는 부모 컴포넌트에서 설정할 수있음

default props setting
ex code
MyComponent.defaultProps ={
  name: 'vitamin'
}


비구조화 할당 문법 통해 props 내부 값 추출
ex code
const {name, children} = props;

/** 프롭 타입 세팅 및 타입 오류 시 경고 메시지 출력토록 isRequired 설정*/
MyPropsTypeComponent.propTypes = {
	name: PropTypes.string,
  myNumber: PropsTypes.number.isRequired,
}

-props 는 컴포넌트가 사용되는 과정에서 부모 컴포넌트가 설정하는 값이며 컴포넌트 자신은 해당 props 를 읽기 전용으로만 사용할수있고/ props 를 바꾸려면 부모컴포넌트에서 바꿔줘야한다

PropTypes 종류
-array: 배열
-arrayOf: 특정 PropType 으로 이루어진 배열을 의미, ex arrayOf(PropTypes.number)는 숫자로 이루어진 배열
-bool: true or false value 
-fuc: 함수
-number: 숫자
-object: 객체
-string: 문자열
-symbol: es6 의 Symbol
-node: 렌더링할 수 있는 모든 것
-instanceOf:특정 클래스의 인스턴스
-oneOf(['dog','cat']): 주어진 배열 요소 중 값 하나
-oneOfType([React.PropTypes.string, PropTypes.number]): 주어진 배열안에 종류중 하나
-objectOf(React.PropTypes.number):객체의 모든 키 값이 인자로 주어진 PropType 인 객체 
-shape({name:PropTypes.string, num:PropTypes.number}): 주어진 스키마를 가진 객체
-any: 아무 종류


defaultProps & PropTypes 는 사용해도되고 안해도되지만 큰 규모에 협업 프로젝트에서는 개발자들끼리 헷갈리지않도록 사용해주는게 좋다.
--------------------------------------------------------
state
-컴포넌트 내부에서 바뀔수 있는 값을 의미

state 사용시 주의사항
-배열이나 객체를 업데이트해야할땐 배열 or 객체 사본을 만들어 사본의 값을 업데이트 한 후에 그 사본의 상태를 setState 혹은 세터 함수를 통해 업데이트함

-객체 사본을 만들땐 스프레드 연산자라 불리는 ... 을 사용/ 배열에 대한 사본을 만들땐 배열의 내장함수들을 활용함
ex code
객체
const object = {a: 1, b: 2, c: 3}
const nextObject = {...object, b: 3} // 사본을 만들어 b 에 값만 덮어씌움

배열
const array = [
  {
    id:1, value: true
  },
  {
    id:2, value: true
  },
  {
    id:3, value: false
  },
]
let nextArray = array.concat({id:4}) // 새 항목 추가
nextArray.filter(item => item.id !==2) // id 2번 제외
// 아디가 1인 항목에는 value 값을 false 로 변경
nextArray.map(item => item.id === 1 ? {...item, value: false} : item)
--------------------------------------------------------
class component

-클래스형 컴포넌트에서 constructor 를 작성시 반드시 super(props) 를 호출해줘야함 이 함수가 호출되면 현재 클래스 컴포넌트가 상속받고있는 리액트의 component 클래스가 지닌 생성자 함수를 호출해줌


-ref 사용시 createRef 함수를 사용함/ React.createRef() 를 멤버 변수에 담아사용
--------------------------------------------------------
배열 비구조화 할당
ex code
const array = [1, 2]
const one = array[0]
const tow = array[1]
을
const [one, tow] = array
--------------------------------------------------------
이벤트
-리액트에서 이벤트 이름은 카멜 표기법으로 작성

-이벤트에 실행할 js 코드를 전달하는것이아닌 함수 형태의 값을 전달함

-돔 요소에만 이벤트를 설정할 수 있음


SyntheticEvent : 웹 브라우저의 네이티브 이벤트를 감싸는 객체/ 네이티브 이벤트와 달리 이벤트가 끝나고 나면 이벤트가 초기화되고 정보를 참조할수 없음/ex 0.5초 뒤에 e 객체를 참조하면 e 객체 내부의 모든값이 비워지게됨
-만약 비동기적으로 이벤트 객체 참조할땐 e.persist() 함수를 호출해주면됨


객체 안에서 key 를 []로 감싸면 그안에 넣은 레퍼런스가 가리키는 실제 값이 키 값으로 사용됨
ex code
const name = 'vitamin'
const object = {
  [name: 'value']
}
결과 : {'vitamin':'value'}


리액트에서 지원하는 이벤트 종류
Clipboard/Composition/Touch/UI/Keyboard/Wheel/Focus/Media/Form/Image/Mouse/Animation/Selection/Transition
--------------------------------------------------------
ref

-ref 는 특정 dom 에 작업을 해야할때 ref 를 사용함/ dom 을 꼭 직접적으로 건드려야할때 사용
--특정 input 에 포커스 주기 
--스크롤 박스 조작하기
--Canvas 요소에 그림 그리기 등


-ref 를 만드는 가장 기본적인 방법은 콜백 함수를 사용하는 것

-ref 를 달고자하는 요소에 ref 라는 콜백 함수를 props 로 전달해주면됨 그러면 콜백 함수는 ref 값을 파라미터로 전달받음 그리고 함수 내부에서 파라미터로 받은 ref 를 컴포넌트의 멤버 변수로 설정해주면됨


-리액트 컴포넌트안에서 id 를 사용할수 있지만 jsx 안에서 dom 에 id 를 달면 해당 dom을 렌더링할때 그대로 전달됨 하지만 특수한 경우가아니면 사용을 권장하지 않음/ ex 같은 컴포넌트를 여러번 사용한다고 가정시 html 에서 dom 의 id 는 유일해야하지만 이런 상황에선 중복 id 를 가진 dom 이 여러개 생기니 잘못된 사용임
--ref 는 전역적으로 작동하지 않고 컴포넌트 내부에서만 작동하기때문에 이런 문제가 생기지 않음/대부분 id 를 사용하지 않고도 원하는 기능을 구현할수있지만 다른 라이브러리나 프레임워크와 함께 id 를 사용해야하는 상황발생할수있음 이런 상황에선 컴포넌트를 만들때마다 id 뒷부분에 추가 텍스트를 붙여 중복 id 가 발생하는것을 방지해야함 ex id="button01",id="button02",id="button03"
--------------------------------------------------------
맵 map 함수

-js 배열 객체의 내장 함수인 map 함수를 사용해 반복되는 컴포넌트를 렌더링할수있음

-map 함수는 파라미터로 전달된 함수를 사용해 배열 내 각 요소를 원하는 규칙에 따라 변환한 후 그 결과로 새로운 배열을 생성함

맵 파라미터
ex code arr.map(callback, [thisArg])
-callback : 새로운 배열의 요소를 생성하는 함수로 파라미터는 다음 세가지 임
--currentValue : 현재 처리하고있는 요소
--index : 현재 처리하고있는 요소의 index 값
--array : 현재 처리하고있는 원본 배열
-thisArg(선택항목) : callback 함수 내부에서 사용할 this 레퍼런스

ex code
const number = [1,2,3,4]

const process = number.map(item => {
  return item * item ;
})
console.log(process) // [1,4,9,16]
--------------------------------------------------------
키 key

-react 에서 key 는 컴포넌트 배열을 렌더링했을 때 어떤 원소에 변동이있었는지 알아내려고 사용함

-키가 없다면 버츄얼 돔을 비교하는 과정에서 리스트를 순차적으로 비교하면서 변화를 감지함

-키가 있다면 이 값을 사용해 어떤 변화가 일어났는지 더욱 빠르게 알아낼 수 있음

-키 값을 설정할땐 map 함수의 인자로 전달되는 함수 내부에서 컴포넌트 props 를 설정하듯이 설정하면 됨

-키 값을 언제나 유일해야함/따라서 데이터가 가진 고유값을 키 값으로 설정해야함

ex code 
const articleList = article.map(article => (
  <Article
    title={article.title}
    write={article.write}
    key={article.id}
  />
))

-만약 고유번호가 없을 시 map 함수에 전달된 콜백 함수의 인수인 index 값을 사용하면됨
--------------------------------------------------------
데이터 추가

-배열에 새 항목을 추가할때 배열의 push/ concat 사용
--push : 기존 배열 자체를 변경해줌
--concat :  기존 상태를 그대로 두며 새로운 값을 상태로 설정해야함/ 불변성 유지라고하며 불변 성 유지해줘야 리액트 컴포넌트의 성능을 최적화 할수 있음


데이터 삭제
-불변성을 유지하면서 배열의 특정 항목을 삭제시 배열의 내장 함수 filter 사용

-filter 함수를 사용하면 특정 조건을 만족하는 원소들만 쉽게 분류 가능
ex code
const number = [1,2,3,4,5]
const filterNumber = number.filter(num => num > 3)
console.log(filterNumber) // [4,5]

-filter 함수 으용해 특정 배열에서 특정 원소만 제외시킬 수 있음
ex code
const number = [1,2,3,4,5]
const filterNumber = number.filter(num => num !== 3)
console.log(filterNumber) // [1,2,4,5]
--------------------------------------------------------
컴포넌트의 라이프 사이클 메서드

-모든 리액트 컴포넌트에는 라이프사이클이 존재함

-컴포넌트의 수명은 페이지에 렌더링되기 전인 준비 과정에서 시작해 페이지에서 사라질때 끝남

-리액트 컴포넌트 진행시 컴포넌트를 처음으로 렌더링할때 어떤 작업을 처리하거나/컴포넌트를 업데이트하기 전후로 어떤 작업을 처리하거나 / 불필요한 업데이트를 방지해야할때가 있음 그때 컴포넌트의 라이프사이클 메서드를 사용함

-라이프 사이클 메서드는 클래스 컴포넌트에서만 사용가능함

-함수 컴포넌트에서는 라이프 사이클 메서드 대신해 Hooks 기능을 사용해 비슷한 작업 처리 가능


라이프 사이클 메서드의 종류는 총 아홉 가지임
-Will 접두사가 붙은 메서드는 어떤 작업을 작동하기 전에 실행되는 메서드임

-Did 접두가사 붙은 메서드는 어떤 작업을 작동한 후에 실행하는 메서드임
-- 위 두가지 Will/Did 는 컴포넌트 클래스에서 덮어 써서 선언함으로써 사용할수있음

라이프 사이클은 총 세가지 마운트/업데이트/언마운트 카테고리로 나눔
마운트: DOM 이 생성되고 웹 브라우저상에 나타나는 것을 마운트라고하며 이때 호출하는 메서드의 종류

마운트
--constructor:z컴포넌트를 새로 만들때마다 호출되는 클래스 생성자 메서드
--getDerivedStateFromProps: props 에 있는 값을 state 에 넣을때 사용하는 메서드
--render: 준비한 UI 를 렌더링하는 메서드 
--componentDidMount: 컴포넌트가 웹 브라우저상에 나타난 후 호출하는 메서드

업데이트
컴포넌트는 다음과 같은 총 네가지 경우에 업데이트함
-props 가 바뀔때
-state 가 바뀔때
-부모 컴포넌트가 리렌더링될 때
-this.forceUpdate 로 강제로 렌더링을 트리거할때

언마운트
마운트의 반대과정이며 즉 컴포넌트를 DOM 에서 제거하는 것을 언마운트라고 함
-componentWillUnmount: 컴포넌트가 웹 브라우저상에서 사라지기전에 호출하는 메서드임


라이프사이클 메서드 상세히 살펴보기
-render: 이 메서드는 컴포넌트 모양새를 정의함/컴포넌트에서 가장 중요한 메서드임/라이프사이클 메서드중 유일한 필수 메서드임
--이 메서드 안에서 this.props 와 this.state 에 접근할수있고 리액트 요소를 반환함
--아무것도 보여주고 싶지 않다면 null 값이나 false 값을 반환하면됨
--주의사항으로는 해당 메서드 안에서는 이벤트 설정이아닌곳에서 setState 를 사용하면안되고 브라우저의 DOM 에 접근해서도 안됨/DOM 정보를 가져오거나 state 에 변화를 줄때는 componentDidMount 에서 처리해야함

constructor method : 이것은 컴포넌트의 생성자 메서드로 컴포넌트를 만들때 처음으로 실행됨/ 이 메서드에서는 초기 state 를 정할수 있음

getDerivedStateFromProps method : 리액트 v16.3 이후에 새로만든 라이프사이클 메서드이며 props 로 받아 온 값을 state 에 동기화시키는 요도로 사용하고 컴포넌트가 마운트될때와 업데이트될때 호출됨

componentDidMount method : 이것은 컴포넌트를 만들고 첫 렌더링을 다 마친후 실행하며 이 안에서 다른 js 라이브러리 또는 프레임워크의 함수를 호출하거나 이벤트 등록 setTimeout, setInterval, 네트워크 요청 같은 비동기 작업을 처리하면됨

shouldComponentUpdate method : props or state 를 변경했을때 리렌더링을 시작할지 여부를 지정하는 메서드이며 이 메서드에서 반드시 true 값 또는 false 값을 반환해야함/컴포넌트를 만들때 이 메서드를 따로 생성하지 않으면 기본적으로 언제나 true 값을 반환함/이 메서드가 false 값을 반환한다면 업데이트 과정은 여기서 중지됨/ 이 메서드 안에서 현재 props 와 state 는 this.props 와 this.state 로 접근하고 새로 설정될 props 또는 state 는 nextPorps 와 nextState 로 접근할수있음/ 프로젝트 성능을 최적화할때 상황에 맞는 알고리즘을 작성해 리렌더링을 방지할땐 false 값을 반환하게 함 

getSnapshotBeforeUpdate method : 리액트 16.3 버전 이후 만든 메서드임/ 이 메서드는 render 에서 만들어진 결과물이 브라우저에서 실제로 반영되기 직전에 호출됨/ 이메서드에서 반환하는 값은 componentDidUpdate 에서 세번째 파라미터인 snapshot 값으로 전달받을 수 있으며 주로 업데이트하기 직전의 값을 참고할 일이 있을때 활용됨

componentDidUpdate method : 리렌더링을 완료한 후 실행함/ 업데이트가 끝난 직후이므로 DOM 관련 처리를해도 무방함/ 여기서는 prevProps or preveState 를 사용해 컴포넌트가 이전에 가졌던 데이터에 접근할수있음/ getSnapshotBeforeUpdate 에서 반환한 값이 있다면 여기서 snapshot 값을 전달받을 수 있음

componentWillUnmount method: 컴포넌트를 DOM 에서 제거할때 실행함/ componentDidMount 에서 등록한 이벤트,타이머 직접 생상한 DOM 이있다면 여기서 제거작업을 해야함

componentDidCatch method : componentDidCatch method 는 리액트 v16 에서 새롭게 도입되었으며 컴포넌트 렌더링 도중에 에러가 발생했을 시 애플리케이션이 먹통되지 않고 오류 UI 를 보여줄수있도록 해줌
ex code
componentDidCatch(error, info) {
  this.setState({error: true})
  console.log({error, info})
}
여기서 error 는 파라미터에 어떤 에러가 발생했는지 알려줌/ info 는 어디에 있는 코드에서 오류가 발생했는지에대한 정보를 줌/ 실제로 사용할땐 오류가 발생하면 서버 api 를 호출해 따로 수집할수있음/그러나 이 메서드를 사용할때 컴포넌트 자신에게 발생하는 에러를 잡아낼수없고 자신의 this.props.children 으로 전달되는 컴포넌트에서 발생하는 에러만 잡아낼수있다는 점을 알아두어야함

--------------------------------------------------------
Hooks 훅스
-리액트 16.8 버전에 새로 도입된 기능이며 함수 컴포넌트에서도 상태관리를 할수있는 useState, 렌더링 직후 작업을 설정하는 useEffect 등의 기능을 제공해 기존의 함수 컴포넌트에서 할수 없었던 다양한 작업을 할 수 있게해줌
--------------------------------------------------------
useState
-가장 기본적인 훅이며 함수 컴포넌트에서도 가변적인 상태를 지닐 수 있게해줌

-useState 에는 상태의 기본값을 넣어줌

-이 함수가 호출되면 배열을 반환하며 그 배열의 첫 번째 원소는 상태 값/ 두번째 원소는 상태를 설정하는 함수임

-이 함수에 파라미터를 넣어 호출하면 전달받은 파라미터로 값이 바뀌고 컴포넌트가 정상적으로 리렌더링됨
--------------------------------------------------------
useEffect
-리액트 컴포넌트가 렌더링될때마다 특정 작업을 수행하도록 설정할수있는 훅임

-클래스형 컴포넌트의 componentDidMount 와 componentDidUpdate 를 합친 형태로 보아도 무방함

-기본적으로 렌더링되고 난 직후마다 실행되며 두번째 파라미터 배열에 무엇을 넣는지에따라 실행되는 조건이 달라짐

-컴포넌트가 언마운트되기 전이나 업데이트되기 직전에 어떤 작업을 수행하고싶다면 useEffect 에서 cleanup 함수를 반환해 줘야함
ex code
useEffect(() => {
    console.log("마운트 될 때만 실행됩니다.");
    console.log({
      name,
      nickName,
    });
    return () => {
      console.log("clean up");
      console.log({
        name,
        nickName,
      });
    };
    // 빈 배열을 넣어주면 마운트 될 때만 실행됩니다.
    // 배열 안에 요소를 넣어주면 해당 요소가 변경될 때만 실행됩니다.
  }, [name, nickName]);

-오직 언마운트될때만 뒷정리함수를 호출하고 싶다면 useEffect 함수의 두번째 파라미터에 비어있는 배열을 넣으면됨
useEffect(() => {
  console.log('effect');
  return () => {
    console.log('unmount')
  }
},[])


마운트 될때만 실행하고 싶을때
-useEffect 에서 설정한 함수를 컴포넌트가 화면에 맨 처음 렌더링 될때만 실행하고 업데이트 될땐 실행하지 않으려면 함수의 두번째 파라미터로 비어있는 배열을 넣어주면됨


특정 값이 업데이트될때만 실행하고 싶을때
-useEffect 를 사용할때 특정 값이 변경될때만 호출하고 싶은 경우
ex code class component
componentDidUpdate(prevProps, prevState) {
  if(prevProps.value !== this.props.value) {
    doSomething()
  }
}
--------------------------------------------------------
useReducer 리듀서
-useState 보다 더 다양한 컴포넌트 상황에따라 다양한 상태를 다른 값으로 업데이트해주고 싶을때 사용하는 훅임

-리듀서는 현재상태 그리고 업데이트를 위해 필요한 정보를 담은 액션 값을 전달받아 새로운 상태를 반환하는 함수임

-리덕스에서 사용하는 액션 객체에는 어떤 액션인지 알려주는 타입 필드가 꼭있어야하지만 리듀서에서 사용하는 액션 객체는 반드시 타입을 지니고 있을 필요가 없음/심지어 객체가 아닌 문자열이나 숫자여도 상관없음

-리듀서 사용시 가장 장점은 컴포넌트 밖에서 업데이트 로직을 컴포넌트 바깥으로 빼낼수 있다


-리듀서 함수에서 새로운 상태를 만들땐 반드시 불변성을 지켜줘야함
ex code
function reducer (state, action) {
  return { ... } // 불변성을 지키면서 업데이트한 새로운 상태를 반환함
}
-- 액션값은 주로 다음과 같은 형태로 이뤄져있음
{type: 'INCREMENT'} // 필요하다면 추가로 들어갈 수 잇음


useReducer ex code
const [state, dispatch] = useReducer(리듀서함수, {value: 초기값})
--------------------------------------------------------
useMemo 
-useMemo 를 사용하면 함수컴포넌트 내부에서 발생하는 연산을 최적화할수 있음

-렌더링하는 과정에서 특정 값이 바뀌었을때만 연산을하고 원하는 값이 바뀌지 않았다면 이전에 연산했던 결과를 다시 사용하는 방식임
ex code
/** useMemo 를 사용하여 getAverage 함수를 호출할 때 list 가 바뀔 때만 호출되도록 함*/
	const avg = useMemo(()=> getAverage(list), [list])
--------------------------------------------------------
useCallback 

-useMemo 와 상당히 비슷한 함수임

-주로 렌더링 성능을 최적화해야하는 상황에서 사용함

-이 훅을 사용하면 만들어놨던 함수를 재사용할수있음

-컴포넌트의 렌더링이 자주 발생하거나 렌더링해야할 컴포넌트의 개수가 많아지면 최적화 해주는것이 좋음

-useCallback 의 첫 번째 파라미터에는 생성하고싶은 함수를 넣고 두번째 파라미터에는 배열을 넣어서 사용함
-- 의존성 배열에는 어떤 값이 바뀌었을 때 함수를 새로 생성해야하는지 명시해야함

-빈배열을 넣게되면 컴포넌트가 렌더링될때 만들었던 함수를 계속해서 재사용하게됨
ex code

-함수 내부에서 상태 값에 의존해야할땐 그 값을 반드시 두번째 파라미터 안에 포함시켜줘야함

--------------------------------------------------------
useRef

-함수 컴포넌트에서 ref 를 쉽게 사용할수 있도록해줌

-useRef 를 사용해 ref 를 설정하면 useRef 를 통해 만든 객체 안의 current 값이 실제 엘리먼트를 가리킴

-로컬 변수를 사용해야할때도 useRef 를 활용할 수 있음
--로컬변수 : 렌더링과 상관없이 바뀔수 있는 값을 의미함
---ref 안의 값이 바뀌어도 컴포넌트가 렌더링되지 않는다는 점을 주의해야함 / 렌더링과 관련되지 않은 값을 관리할때만 로컬 변수를 사용해 코드를 작성함
--------------------------------------------------------
커스텀 훅 customHooks
-여러 컴포넌트에서 비슷한 기능을 공유할 경우 커스텀 훅을 작성해 로직을 재 사용할수 있음
--------------------------------------------------------
컴포넌트 스타일링
-일반 css : 컴포넌트를 스타일링하는 가장 기본적인 방식

-Sass : 자주 사용되는 CSS 전처리기 중 하나로 확장된 css 문법을 사용해 css 코드를 더욱 쉽게 작성할수 있도록해줌

-CSS Module: 스타일을 작성할 때 css 클래스가 다른 css 클래스의 이름과 절대 충돌하지 않도록 파일마다 고유한 이름을 자동으로 생성해주는 옵션임

-styled-components: 스타일을 js 파일에  내장시키는 방식으로 스타일을 작성함과 동시에 해당 스타일이 적용된 컴포넌트를 만들 수 있게 해줌


BEM naming : css 방법론 중 하나로 이름을 지을때 일종의 규칙을 준수해 해당 클래스가 어디에서 어떤 용도로 사용되는지 명확하게 작성하는 방식임
ex code 
useInfo__nickname-color


CSS Selector : css 클래스가 특정 클래스 내부에있는 경우에만 스타일을 적용할 수 있음
 / 컴포넌트의 최상위 html 요소에 컴포넌트의 이름으로 클래스 이름을 짓고 그 내부에서 소문자를 입력하거나 태그를 사용해 클래스 이름이 불필요한 경우엔 아예 생략할수있음


 Sass (Syntactically Awesome Style Sheet (문법적으로 매우 멋진 스타일 시트) )::: css 전처리기로 복잡한 작업을 쉽게 할 수 있도록 해주며 스타일 코드의 재활용성을 높여주고 코드의 가독성을 높여 유지 보수를 더욱 쉽게 해줌
-Sass 에서는 두가지 확장자 .scss 와 .sass 를 지원함

-Sass 가 처음 나왔을땐 .sass 확장자만 지원됐으며 나중에 .scss 확장자도 지원하게되었음

ex code .sass 문법
$font-stack: Helvetica, sans-serif
$primary-color: #333
body 
  font: 100% $font-stack
  color: $primary-color

ex code .scss 문법
$font-stack: Helvetica, sans-serif;
$primary-color: #333;
body {
  font: 100% $font-stack;
  color: $primary-color;
}
위 sass 와 scss 의 차이점은 sass 확장자는 중괄호 및 세미콜론을 사용하지 않음 / 보통 scss 문법을 더 많이 사용함


utils 함수 분리하기
-여러 파일에서 사용될 수 있는 Sass 변수 및 믹스인은 다른 파일로 따로 분리해 작성한뒤 필요한곳에서 쉽게 불러와 사용할 수 있음

-다른 scss 파일을 불러올땐 @import 구문을 사용함


sass-loader 설정 커스터마이징
-Sass 를 사용할때 반드시해야하는건 아니며 해두면 유용함 / SassComponent 에서 utils 를 불러올때 프로젝트 디렉터리를 많이 만들어 구조가 깊어졌다면 웹팩에서 Sass 를 처리하는 sass-loader 의 설정을 커스터마이징해서 해결할수있음 
--create-react-app 으로 만든 프로젝트는 프로젝트 구조의 복잡도를 낮추기위해 세부설정이 모두 숨겨져있기때문에 커스터마이징하려면 프로젝트 디렉터리에서 yarn eject 명령어를 통해 세부 설정을 밖으로 꺼내줘야함
--create-react-app 에선 기본적으로 git 설정이되어있으며 yarn eject 는 아직 git 에 커밋되지않은 변화가있다면 진행되지않으니 커밋을 먼저해줘야함 / 만약 개발 서버 시작되지않는다면 프로젝트 디렉터리 노드모듈즈 디렉터리를 삭제 후 yarn install 명령어를 실행하고 yarn start 를 해보자 / 정상적으로 진행됐다면 프로젝트 디렉터리에 config 라는 디렉터리가 생성되었을 것이며 디렉터리 안에 들어있는 webpack.config.js 를 열면 sassRegex 키워드를 찾아 use 에 sass-loader 를 지우고 concat 을 통해 커스터마이징된 sass-loader 설정을 넣어주면 됨
ex code
{
  test: sassRegex,
  exclude: sassModuleRegex,
  use: getStyleLoaders(
    {
      importLoaders: 3,
      sourceMap: isEnvProduction
        ? shouldUseSourceMap
        : isEnvDevelopment,
      modules: {
        mode: 'icss',
      },
    }).concat({
      loader: require.resolve("sass-loader"),
      options: {
        sassOptions: {
          includePaths: [paths.appSrc + "/styles"],
        },
      },
    }),
  // Don't consider CSS imports dead code even if the
  // containing package claims to have no side effects.
  // Remove this when webpack adds a warning or an error for this.
  // See https://github.com/webpack/webpack/issues/6571
  sideEffects: true,
},
위와 같이 설정하며 매번 utils.scss 를 포함시키는게 귀찮다면 해결방법으로 sass-loader 의 additionalData 옵션을 설정해주면됨 설정하면 Sass file 을 불러올때마다 코드의 맨 윗부분에 특정 코드를 포함시켜줌
ex code
}).concat({
  loader: require.resolve("sass-loader"),
  options: {
    sassOptions: {
      includePaths: [paths.appSrc + "/styles"],
    },
    additionalData: "@import 'utils';",
  },
}),
위와 같이 작성하고 개발 서버 재시작시 모든 scss file 에서 utils.scss 를 자동으로 불러오며 맨 윗줄에 있는 import 구문을 지워도 정상적으로 작동함



--------------------------------------------------------
node_modules 에서 라이브러리 불러오기

-Sass 의 장점중 하나로 라이브러리를 쉽게 불러와서 사용할수있다는 점임 / yarn 을 통해 설치한 라이브러리를 사용하는 가장 기본적인 방법으로 상대 경로를 사용해 node_modules 까지 들어가서 불러오는 방법임 하지만 이런구조는 스타일 파일이 깊숙한 디렉터리에 위치할경우 ../ 을 많이 적어야해서 번거롭기에 물결 문자를 사용하는 방법이있음 
ex code 
@import '~library/styles';

--물결 문자를 사용하면 자동으로 node_modules 에서 라이브러리 디렉터리를 탐지해 스타일을 불러올수있음

-반응형 디자인을 쉽게 만들어주는 include-media 와 편리한 색상 팔레트 open-color 사용 $ yarn add open-color include-media 

-Sass 라이브러리를 불러올땐 node_modules 내부 라이브러리 경로안에 들어있는 scss file 을 불러와야함 / 보통 scss file directory 가 어디에위치하고있는지를 라이브러리 공식 메뉴얼에서 알려주지않을때가 많아서 직접 경로로 들어가서 확인하는게 좋음
--------------------------------------------------------
Scss @Mixin @include 사용방법 및 예제
@mixin @include 알아보기
먼저 두 가지 @mixin와 @include는 항상 함께 사용되며 @mixin을 사용하면 그룹단위의 스타일을 변수처럼 적용할 수 있습니다. 즉 여러개의 스타일을 설정해두었다가 한번에 적용하는 것이 가능합니다. 이때 설정에는 @mixin을 그리고 사용할 때는 @include를 사용하면 됩니다. 아래 코드를 봐주세요.
@mixin box-default {
  padding: 20px 30px;
  margin-bottom: 20px;
}

위에서는 @mixin을 사용해 box-default라는 이름을 가진 스타일 그룹을 설정했습니다. 이제 원하는 곳에 box-default를 사용하면 padding과 margin값을 동시에 적용하게 됩니다. 이제 위 스타일을 div 태그에 적용해보겠습니다.
div {
  @include box-default
}

이처럼 div태그에 적용하면 아래와 같이 box-default의 모든 스타일 속성을 가지게 됩니다.
div {
  padding: 20px 30px;
  margin-bottom: 20px;
}

이처럼 @mixin을 사용하여 미리 선언해두면 동일한 레이아웃 등의 스타일 지정에 매우 편리합니다. 만약 스크롤바의 스타일을 항상 정해진 스타일로 보이고 싶은 경우에도 위와 같이 @mixin을 사용해 선언할 수 있을 것입니다.
@mixin scrollbar-default {
  ::-webkit-scrollbar {
    width: 10px;
    height: 20px
  }
  ::-webkit-scrollbar-track {
    background-color: darkblue;
  }
  ::-webkit-scrollbar-thumb {
    border-radius: 8px;
    background-color: black;
  }
}

위 스크롤바를 적용하려면 아래와 같이 간단하게 @include를 사용하면 됩니다.
div {
  @include scrollbar-default
}

이처럼 @mixin과 @include를 잘 사용하면 매우 편리합니다.


! mixin에 조건문 사용하는 방법 if, else
mixin은 전달 받은 인자를 사용하여 조건문 @if, @else를 사용할 수 있습니다. 예를들어 폰트 사이즈를 키우거나 줄이기 위해 아래와 같이 각각 다른 mixin을 구현할 수 있죠.
mixin fontSize($size) {
  @if $size == 'small' {
    font-size: 10px;
  }
  @else if $size == 'large' {
    font-size: 14px;
  }
  @else {
    font-size: 12px;
  }
}

이제 각각 큰 폰트, 기본 폰트, 작은 폰트를 구현하기 위해서 아래와 같이 사용할 수 있습니다.
div {
  @include fontSize('small');
  @include fontSize;
  @include fontSize('large');
}

이처럼 mixin과 if 조건문을 조합해 사용하면 다양한 스타일을 간단하게 얻는 것이 가능합니다.


! @content 블럭 사용하는 방법
만약 기존의 @mixin 내부의 스타일을 추가하거나 변경하려면? 이때 @content를 사용할 수 있습니다. @content를 사용하면 @include 내부에 선언된 블럭을 함께 사용할 수 있습니다.
@mixin box-default {
  padding: 20px 30px;
  margin-bottom: 20px;
  @content;
}

이제 @include에 스타일 블럭을 추가해봅니다.
div {
  @include box-default {
    padding: 40px 60px;
  }
}

이처럼 간단하게 추가 스타일을 선언해 사용할 수 있습니다.


! @mixin에 인자 arguments를 사용하는 방법
여기서 @mixin의 특징으로 인자를 사용하여 함수처럼 사용할 수 있다는 점입니다. 만약 위의 box-default의 padding 값을 상황에 따라 다르게 주고 싶다면? 아래와 같이 사용할 수 있습니다.
@mixin box-default($padding, $margin) {
  padding: $padding;
  margin-bottom: $margin;
}

이제 box-default에 padding과 margin 값으로 각각 20px, 30px을 주려면 아래처럼 선언합니다.
div {
  @include box-default(20px, 30px);
}

이제 div 태그는 padding과 margin-bottom 값이 각각 20px, 30px으로 선언될 것입니다. 이처럼 코드를 @mixin에 인자를 사용하여 선언해두면 코드의 재사용성을 높일 수 있을 것입니다.

참고로, 인자가 없는 경우... 즉 기본값을 설정할 수 있습니다. 이 방법은 아래에서 확인해보세요.


! 기본값 선언하여 사용하기
추가로 인자의 기본값을 선언하는 것도 가능합니다. 아무 값도 입력되지 않은 경우 각각 10px, 20px로 선언해보겠습니다.
@mixin box-default($padding: 10px, $margin: 20px) {
  padding: $padding;
  margin-bottom: $margin;
}

이제 값이 없어도 기본값이 적용되어 나타납니다.
(https://webisfree.com/2019-10-08/[scss]-mixin-include-%EC%82%AC%EC%9A%A9%EB%B0%A9%EB%B2%95-%EB%B0%8F-%EC%98%88%EC%A0%9C%EB%B3%B4%EA%B8%B0)
--------------------------------------------------------
CSS Module 

-css 를 불러와서 사용할때 클래스 이름을 고유한 값 파일이름_클래스이름_해시값 형태로 자동으로 만들어서 컴포넌트 스타일 클래스 이름이 중첩되는 현상을 방지해주는 기술임

-css module 을 사용하기 위해 구버전의 create-react-app 에서는 웹팩에서 css-loader 설정을 별도로 해줘야했지만 v2 버전이상부터는 따로 설정할 필요없이 .module.css 확장자로 파일을 저장하기만하면 css module 이 적용됨

-클래스 이름을 지을때 고유성에대해 고민하지 않아도되며 흔히 사용하는 단어로 이름을 짓는다고해도 문제가될게 없다. / 해당 클래스는 내가 만든 스타일을 직접 불러온 컴포넌트 내부에서만 작동하기 때문임

-특정 클래스가 웹페이지에서 전역적으로 사용되는 경우라면 :global 을 앞에 입력해 전역 css 임을 명시할수있음

-css module 이 적용된 스타일 파일을 불러오면 객체를 전달받으며 css module 에서 사용한 클래스 이름과 해당 이름을 고유화한 값이 키-값 형태로 들어있음
--이 고유한 클래스 이름을 사용하면 클래스를 적용하고 싶은 jsx 엘리먼트에 ex className={styles.className} 형태로 전달해주면됨
--:global 을 사용해 전역적으로 선언한 클래스의 경우 평상시처럼 문자열로 넣어주면됨

-css module 을 사용한 클래스 이름을 두개 이상 적용할땐 백틱으로 className={`${styles.wrapper} ${styles.inverted}`} 와 같이 작성하면됨 / 만약 템플릿 리터럴 문법을 사용하고 싶지 않다면 ex className={[styles.wrapper, styles.inverted].join(' ')} 과 같이 사용할 수 있다
--------------------------------------------------------
classnames 

-css class 를 조건부로 설정할때 유용한 라이브러리임
-css module 을 사용할때 이 라이브러리를 사용하면 여러 클래스를 적용할때 매우 편리함

-설치방법
-- $ yarn add classnames

-css module 과 함께 사용하면 classnames 에 내장되어있는 bind 함수를 사용해서 클래스를 넣어줄때마다 styles.클래스이름 형태를 사용할 필요가 없고 사전에 미리 styles 에서 받아온 후 사용하게 설정해두고 클래스이름,클래스이름2 형태로 사용할 수 있음
ex code
const cx = classNames.bind(styles) // 미리 styles 에서 클래스를 받아오도록 설정함
	return (
			/*classNames 와 css module 같이 사용한 경우*/
			<div className={cx('wrapper', 'inverted')}>
				안녕하세요, 저는 <span className="something">CSS Module!</span>
			</div>
	/* css module 만 사용했을 경우
	<div className={`${styles.wrapper} ${styles.inverted}`}>
				안녕하세요, 저는 <span className="something">CSS Module!</span>
			</div>*/
--------------------------------------------------------
CssModule 을 Sass 와 함께 사용

-Sass 를 사용할때 파일 이름 뒤에 .module.scss 확장자를 사용해주면 css module 로 사용할 수 있음 
-CSSModule.module.css file 의 이름을 CSSModule.module.scss 로 변경해서 사용함
--------------------------------------------------------
CSS Module 이 아닌 파일에서 CSS Module 사용하기

- css/scss 에서도 :local 을 사용해 CSS Module 을 사용할수있음
ex code
:local .wrapper {
  /* 스타일 */
}
:local {
  .wrapper {
    /* 스타일 */
  }
}
--------------------------------------------------------
Styled-components

-설치 $ yarn add styled-components

-js file 안에 스타일을 선언하는 방식임 해당 방식을 CSS-in-JS 라고 부름

-styledComponent 와 일반 classNames 를 사용하는 CSS/Sass 를 비교하면 가장 큰 장점은 props 값으로 전달해 주는 값을 쉽게 스타일에 적용할수있다는것임

-vs code 에서는 styled-components 를 위해 컴포넌트 내부에 작성한 스타일이 그냥 문자열로 간주되어 코드 신택스 하이라이팅(문법에따라 에디터 폰트 색상을 입히는작업) 이 제대로 이뤄지지않기때문에 마켓플레이스에서 따로 vscode-styled-components 를 검색해 설치하면 색상이 정상적으로 입혀짐


Tagged template literal 
-템플릿 사이사이에 들어가는 자바스크립트 객체나 함수의 원본 값을 그대로 추출할 수있다
ex code
function tagged(...args) {
  console.log(args)
}
tagged`hello ${{foo: 'bar'}} ${() => 'world'}!`
-styled-components 는 이런 속성을 사용해서만든 컴포넌트의 props 를 스타일 쪽에서 쉽게 조회할수있도록 해준다

-컴포넌트를 styled 의 파라미터에 넣는 경우 해당 컴포넌트에 className props 를 최상위 dom 의 className value 로 설정하는 작업이 내부적으로 되어있어야함
ex code 예시 코드
const Sample = ({className}) => {
  return <div className={className}>Sample</div>
}
const StyledSample = styled(Sample)`
  font-size: 2rem;
`
--------------------------------------------------------
스타일에서 props 조회하기
-styled-components 를 사용하면 style 쪽에서 컴포넌트에게 전달된 props 값을 참조할수 있음

-일반 CSS 클래스를 사용해 조건부 스타일링을할땐 클라스네임을 사용해 조건부 스타일링을 작성하며 styled-components 에선 조건부 스타일링을 간단하게 props 로 처리할수있다

-스타일 코드 여러 줄을 props 에 따라 넣어주어야할땐 css 를 styled-components 에서 불러와야함 / css 를 사용하지 않고 바로 문자열을 넣어도 작동하긴 하지만 문자열로만 취급되기때문에 vs code 같은 확장프로그램에선 신택스 하이라이팅이 제대로 이뤄지지않아 단점이 따르고 치명적인 단점은 tagged template literal 이 아니기때문에 함수를 받아 사용하지 못하기때문에 props 값을 사용하지 못함
--만약 조건부 스타일링을할때 넣는 여러줄의 코드에서 props 를 참조하지 않는다면 굳이 css 를 불러와 사용하지 않아도 상관없음 하지만 props 를 참조한다면 반드시 css 로 감싸줘서 tagged template literal 을 사용해줘야함
--------------------------------------------------------
styled-components 를 사용해 반응형 디자인
-브라우저의 가로크기에따라 다른스타일을 적용하기 위해선 일반 css 를 사용할대와 같이 media 쿼리를 사용하면됨
--이런 작업을 여러 컴포넌트에서 반복해야할땐 함수화하여 간편하게 사용할수있으며 styled-components 메뉴얼에서 제공되는 유틸함수를 따라 사용하면된다
--------------------------------------------------------
컴포넌트가 다른 탭으로 열려있지않으면 자동완성이 되지않음
닫혀있는 파일에도 자동완성이 제대로 작동하려면 프로젝트 최상위 경로에 
jsconfig.json file 을 만들어주고
ex code
{
  "compilerOptions": {
    "target": "es6"
  }
}
작성하면 컴포넌트 파일이 열려있지않아도 자동완성을 통해 컴포넌트를 불러와서 사용 가능
--------------------------------------------------------
onSubmit event 는 브라우저를 새로고침 시키기때문에 e.preventDefault() 함수를 
호출해서 새로고침을 방지해줘야한다


onSubmit 과 onClick 의 차이
-onSubmit 이벤트의 경우 인풋에 enter 를 눌렀을때도 발생되고 버튼에 onClick 을 사용한다면 인풋에서 onKeyPress event 를 통해 enter 를 감지하는 로직을 따로 작성해줘야하는 차이점이있음
--------------------------------------------------------
지우기 기능 구현
-리액트 컴포넌트에서 배열의 불변성을 지키면서 배열 원소를 제거해야할 경우
배열 내장함수 filter 를 사용하면 간편함

-filter 함수는 기존의 배열은 그대로 둔 상태에서 특정 조건을 만족하는 원소들만 따로
추출해 새로운 배열을 만들어줌
ex code
const array = [1,2,3,4,5]
const biggerThanTwo = array.filter((number) => number > 2)
결과 : [3,4,5]
--filter 함수에는 조건을 확인해주는 함수를 파라미터로 넣어줘야함
--파라미터로 넣는 함수는 true or false 값을 반환해야하고 true 를 반환하는 경우에만 새로운 배열에 포함됨

-보통 지우기 기능에서는 배열에서 id 로 지움
--------------------------------------------------------
컴포넌트 리렌더링 조건
-자신이 전달받은 props 가 변경될 때

-자신의 state 가 바뀔때

-부모 컴포넌트가 리렌더링될 때

-forceUpdate 함수가 실행될때
--------------------------------------------------------
성능 최적화

React.memo 를 사용해 컴포넌트 성능 최적화
-컴포넌트 리렌더링 방지할때 shouldComponentUpdate 라이프 사이클 사용하면됨
-함수 컴포넌트에서는 React.memo 를 사용하면됨
-컴포넌트의 props 가 바뀌지 않았다면 리렌더링하지않도록 설정해 함수 컴포넌트의 리렌더링 성능을 최적화해줄수있음

React.memo 사용법 ex code
export default React.memo(component name)


useState 함수형 업데이트
-todos 배열이 업데이트되면 onRemove, onToggle 함수들도 새롭게 바뀌기때문에
onRemove, onToggle 함수는 배열상태를 업데이트하는 과정에서 최신 상태의 todos 를 참조하여 todos 배열이 바뀔때마다 함수가 새로 만들어지기때문에 함수가 계속 만들어지는 상황을 방지하는 방법으로 useState 의 함수형 업데이트 기능을 사용하거나 useReducer 를 사용하는 방법이있음

setTodos(직접 변경) 사용해 새로운 상태를 파라미터로 넣는 대신 상태 업데이트를 어떻게 할지 정의해주는 업데이트 함수를 넣을수있으며 함수형 업데이트라고 부름
ex code
const [number, setNumber] = useState(0)
// 기존 코드 
const onIncrease => useCallback(setNumber(prevNumber => prevNumber + 1),
[prevNumber]);
// 업데이트 함수를 넣어준 코드
const onIncrease => useCallback(() => setNumber(prevNumber => prevNumber + 1),
[]);
위 코드 처럼 어떻게 업데이트할지 정의해주는 업데이트함수를 넣어주면 useCallback 을 사용할때 두번째 파라미터로 넣는 배열에 넣지 않아도됨


useReducer 사용해 최적화하기
-useState 의 함수형 업데이트를 사용하는 대신 useReducer 를 사용해 onToggle, onRemove 가 계속 새로워지는 문제를 해결 할 수 있음
-useReducer 를 사용하면 기존 코드를 많이 고쳐야하는 단점이있고 상태를 업데이트하는
로직을 모아서 컴포넌트 바깥에 둘수있다는 장점이있음
-useReducer 의 두 번째 파라미터로 undefined 를 넣고 세 번째 파라미터에 초기값을 두면 컴포넌트가 맨 처음 렌더링될때만 createBulkTodos 함수가 호출됨
--------------------------------------------------------
불변성의 중요성

const onToggle = useCallback((id) => {
  setTodos((todo => todo.id === id ? {...todo, checked: !todo.checked} : todo))
}, [])
위 코드와 같이 기존 데이터를 수정할때 직접 수정하지않고 새로운 배열을 만든다음에 새로운 객체를 만들어 필요한 부분을 교체해주는 방식으로 구현했기때문에 React.memo 를 사용했을때 props 가 바뀌었는지 혹은 바뀌지 않았는지 알아내서 리렌더링 성능을 최적화해줄 수 있음
--기존의 값을 직접 수정하지 않으면서 새로운 값을 만들어내는 것을 불변성을 지킨다라고함
--리액트 컴포넌트에서 상태를 업데이트할때 불변성을 지키는 것을 매우 중요시함
ex code
배열 예제
const array = [1,2,3]
const nextArrayBad = array // 배열 복사가아닌 똑같은 array 배열을 가리킴
nextArrayBad[0] = 100
console.log(array === nextArrayBad) // 결과 true
// 배열 복사
nextArrayGood = [...array] // 배열 복사, 배열 내부의 값을 모두 복사함
nextArrayGood[0] = 100
console.log(array === nextArrayGood) // 복사한 다른 배열이기때문에 false

객체 예제
const object = {
  foo: 'bar',
  value: 1
}
const nextObjectBad = object // 객체가 복사되지않고 똑같은 객체를 가리킴
nextObjectBad.value = nextObjectBad.value + 1 ;
console.log(object === nextObjectBad) // 같은 객체이기 때문에 결과 : true
// 객체 복사
const nextObjectGood = {
  ...object, // 기존에 있던 내용을 모두 복사해서 넣음
  value: object + 1; // 새로운 값을 덮어 씌움
  } // 객체 값 복사
console.log(object === nextObjectGood) // 다른 객체이기때문에 결과 : false

-불변성이 지켜지지 않으면 객체 내부의 값이 새로워져도 바뀐것을 감지하지 못하며 React.memo 에서 서로 비교하여 최적화하는것이 불가능함
-전개 연산자 ... 문법을 사용해 객체나 배열 내부의 값을 복사할땐 얕은 복사를 하게되는데 내부의 값이 완전히 새로 복사되는것이아닌 가장 바깥쪽에있는 값만 복사됨
-- 내부의 값이 객체 혹은 배열이라면 내부의 값 또한 따로 복사해줘야함
ex code
const todos = [{id:1, checked: true}, {id:2, checked: true}]
const nextTodos = [...todos]
nextTodos.checked = false;
console.log(todos[0] === nextTodos[0])  // 아직까지 똑같은 객체를 가리키기때문에 true
// 새로운 객체 할당
nextTodos[0] = {
  ...nextTodos[0],
  checked: false
}
console.log(todos[0] === nextTodos[0]) // 새로운 객체를 할당해줬기에 false


-배열 혹은 객체의 구조가 정말 복잡해진다면 불변성을 유지하면서 업데이트하는 것도 까다로워짐
--이렇게 복잡한 상황일 경우 immer 라는 라이브러리의 도움을 받으면 편하게 작업할 수 있음

-리스트에 관련된 컴포넌트를 최적화할땐 리스트 내부에서 사용하는 컴포넌트도 최적화해야하고 리스트로 사용되는 컴포넌트 자체도 최적화해주는것이 좋음
--리스트 관련 컴포넌트 작성시 리스트 아이템과 리스트 두가지 컴포넌트를 최적화해주는것을 잊지 말자 / 하지만 내부 데이터가 100개를 넘지않거나 업데이트가 자주 발생하지 않는다면 이런 최적화 작업을 반드시 해줄 필요는 없음


react-virtualized 사용한 렌더링 최적화
-리스트 컴포넌트에서 스크롤 되기 전에 보이지 않는 컴포넌트는 렌더링하지않고 크기만 차지하게끔 할 수 있음
-만약 스크롤되면 해당 스크롤 위치에서 보여주어야할 컴포넌트를 자연스럽게 렌더링시킴
--이렇게 해주므로 라이브러리를 사용하면 낭비되는 자원을 쉽게 아낄 수 있음
설치
$ yarn add react-virtualized
-제공하는 List 컴포넌트를 사용해 list component 의 성넝을 최적화할 수 있음
-최적화를 수행하려면 사전에 각 항목의 실제 크기를 px 단위로 알아내야함
-- 이 값은 작성한 css 를 확인해서 직접 계산해도되지만 크롬 개발자 도구의 좌측 상단에있는 아이콘을 눌러서 크기를 알고싶은 항목에 커서를대서 알아 볼 수 있음

--------------------------------------------------------
immer 
ex code
import produce from 'immer'
const nextState = produce(originalState, draft => {
  // 바꾸고 싶은 값 바꾸기
  draft.somewhere.deep.inside = 5;
})
-produce 함수는 두가지 파라미터를 받았음 첫 번째 파라미터는 수정하고싶은 상태 / 두 번째 파라미터는 상태를 어떻게 업데이트할지 정의하는 함수
--두번째 파라미터로 전달되는 함수 내부에서 원하는 값을 변경하면 produce 함수가 불변성 유지를 대신해주면서 새로운 상태를 생성해줌


-immer 를 사용해 컴포넌트 상태를 작성할땐 객체안에있는 값을 직접 수정하거나 배열에 직접적인 변화를 일으키는 push, splice 등의 함수를 사용해도 무방함
-불변성에 익숙하지 않아도 js 에 익숙하다면 컴포넌트 상태에 원하는 변화를 쉽게 반영시킬수있음
-immer 를 사용한다고해서 코드가 간결해지는건아님
-onRemove 와 같이 배열 내장함수 filter 를 사용하는것이 더 깔끔함 / 이머는 불변성을 유지하는 코드가 복잡할때만 사용해도됨

-immer 에서 제공하는 produce 함수를 호출할때 첫번째 파라미터가 함수형태라면 업데이트함수를 반환함
ex code
const update = produce((draft => {
  draft.value = 2;
})
const originalState = {
  value: 1,
  foo: 'bar'
}
const nextState = update(originalState)
console.log(nextState) // 결과 : {value:2, foo: 'bar'}
)
--------------------------------------------------------
라우팅
-웹 앱에서 라우팅 개념은 사용자가 요청한 url 에 따라 알맞은 페이지를 보여주는 것을 의미
-웹앱을 만들때 프로젝트를 여러개의 페이지로 구성되게 만든다면 페이지 별로 컴포넌트들을 분리해가면서 프로젝트를 관리하기 위해 필요한것이 라우팅 시스템임


-리액트에서 라우트 시스템 구축위해 사용할수있는 선택지는 두 가지가있음
--리액트 라우터(react router): 해당 라이브러리는 리액트 라우팅 관련 라이브러리중 가장 오래되고 많이 사용되고있으며 컴포넌트 기반으로 라우팅 시스템 설정 할수있음
--Next.js : 리액트 프로젝트 프레임워크임 / create react app 처럼 리액트 프로젝트 설정을 하는 기능, 라우팅 시스템, 최적호, 다국어 시스템 지원, 서버서사이드 렌더링등 다양한 기능을 제공 / 해당 프레임워크의 라우팅 시스템은 파일 경로 기반으로 작동하며 리액트 라우터의 대안으로도 많이 사용됨


라우팅 관련 기능은 리액트 라이브러리에서 공식적으로 지원하는것이아닌 서드파티로 제공되기때문에 react-location, rakkas 등 프로젝트들이있음
--------------------------------------------------------
싱글 페이지 앱
-하나의 페이지로 이뤄진 앱이라는 의미
-리액트 라이브러리를사용해 뷰 렌더링을 사용자의 브라우저가 담당하고 웹 앱을 브라우저에서 불러와 실행시킨 후 사용자와의 인터랙션이 발생하면 필요한 부분만 js 를 사용해 업데이트하는 방식을 사용함 / 새로운 데이터가 필요하다면 서버 api 를 호출해 필요한 데이터만 새로 불러와 앱에서 사용할수있게됌
-html 은 한번만 받아와서 웹 앱을 실행시키고 이후에 필요한 데이터만 받아 화면을 업데이트하는것이 싱글 페이지 앱임 spa 
-spa 는 기술적으로 한페이지만 존재하지만 사용자가 경험할땐 여러 페이지가 존재하는것처럼 느낌
-리액트 라우터같은 라우팅 시스템은 사용자의 브라우저 주소창의 경로에 따라 알맞은 페이지를 보여줌
-이후 링크를 눌러 다른 페이지로 이동할때 서버에 다른 페이지의 html 을 새로 요청하는것이아닌 브라우저의 히스토리 api 를 사용해 브라우저의 주소창의 값만 변경하고 기존에 페이지에 띄웠던 웹 앱을 그대로 유지하면서 라우팅 설정에따라 또다른 페이지를 보여주게됨

-멀티 페이지 앱에선 사용자가 다른 페이지로 이동할때마다 새로운 html 을 받아오고 페이지를 로딩할때마다 서버에서 css,js img file 등의 리소스를 전달받아 브라우저 화면에 보여줌 / 각 페이지마다 다른 html file 을 만들어 제공해주거나 데이터에 따라서 유동적인 html 을 생성해주는 템플릿 엔진을 사용함
--사용자 인터렉션이 별로 없는 정적인 페이지들은 기존의 방식(멀티 페이지 앱) 사용자 인터랙션이 많고 다양한 정보를 제공하는 모던 웹 앱은 해당 방식이 적합하지 않음 / 새로운 페이지를 보여줘야할때마다 서버측에서 모든 준비를하면 그만큼 서버의 자원을 사용하고 트래픽도 더 많이 나올수 있기때문임


사용법
-프로젝트에 리액트 라우터를 적용할땐 src/index.js file 에서 react-router-dom 에 내장되어있는 BrowserRouter 컴포넌트를 사용해 감싸주면됨
--이 컴포넌트는 웹 앱에 html5 의 history api 를 사용해 페이지를 새로 불러오지 않고도 주소를 변경하고 현재 주소의 경로에 관련된 정보를 리액트 컴포넌트에서 사용할수있도록해줌
ex code src/index.js
<BrowserRouter>
  <App />
</BrowserRouter>

ex code src/App.js
<Routes>
  <Route path="/" element={<Home/>} />
</Routes>

-src/pages 로 꼭 pages 경로에 넣을 필요는 없음 다른이름을 써도되고 src 경로에 바로 생성해도 문제가되진않음
-사용자의 브라우저 주소 경로에따라서 원하는 컴포넌트를 보여주려면 Route 라는 컴포넌트를 통해 라우트 설정을 해줘야함
--------------------------------------------------------
Link 컴포넌트 사용
-리액트 라우터를 사용하는 프로젝트에선 a tag 를 바로 사용하면 안됨 / a tag 를 클릭해 페이지를 이동할때 브라우저에서는 페이지를 새로 불러오게 되기때문임
-Link 컴포넌트도 a tag 를 사용하지만 페이지를 새로 불러오는것을 막고 히스토리 api 를 통해 브라우저 주소의 경로만 바꾸는 기능이 내장되어있음
ex code
<Link to="경로">링크 이름</Link>
--------------------------------------------------------
URL 파라미터와 쿼리스트링
-페이지 주소를 정의할때 유동적인 값을 사용할때 사용
ex
URL 파라미터 : /profile/velopert
-URL 파라미터는 주소의 경로에 유동적인 값을 넣는 형태
-URL 파라미터는 useParams hook 을 사용해 객체 형태로 조회할수있음
-URL 파라미터의 이름은 라우트 설정할때 Route 컴포넌트의 path props 를 통해 설정함
-URL 파라미터는 /profile/:username 과 같이 경로에 : 를 사용해서 설정함
--만약 url 파라미터가 여러개인경우에 /profiles/:username/:field 와 같은 형태로 설정할수있음
-URL 파라미터는 주로 ID or 이름을 사용해 특정 데이터를 조회할때 사용


쿼리스트링 : /articles?page=1&keyword=react
-쿼리스트링은 주소의 뒷부분에 ? 문자열 이후 key=value 로 값을 정의하고 & 로 구분하는 형태
-쿼리스트링은 키워드검색,페이지네이션,정렬방식등 데이터조회에 필요한 옵션을 전달할때 사용
-URL 파라미터와 달리 Route 컴포넌트를 사용할때 별도로 설정해야함

--------------------------------------------------------
--------------------------------------------------------
--------------------------------------------------------




```