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
-이 함수의 첫번째 파라미터에는 페이지에 렌더링할 내용을 jsx 형태로 작성/ 두번째 파라미터에는 해당 jsx 를 렌더링할 document 내부 요소를 설정함
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
--------------------------------------------------------




```