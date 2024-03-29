---
layout: post
title: "처음만난리액트 정리"
---

## 코드는 재산이다, 나중에 도움된다, 정리잘하자

```js

----------------------------------------------------------------
mini blog project 사용된 라이브러리
react-router-dom v6
styled-components v5
----------------------------------------------------------------
프로젝트 시작시
(프로젝트 설계시 탑 다운 형식으로 큰 틀에서 작은 틀 방향으로 설계)
-구조 설계
-필요 기능 구성
-필요한 컴포넌트 구성
-폴더 경로 구성


프로젝트 구현시
(작은 부분(ui component 부터)을 모아 큰 컴포넌트로 구현)
----------------------------------------------------------------
html : 웹 사이트의 뼈대를 구성하는 마크업 언어
<head> : 여러가지 속성을 가지고있으며 헤드 태그 살펴봐도 대략적으로 어떤 사이트인지 알아볼 수 있도록한다
<body> : 실제로 웹사이트에 보이는 컨텐츠가 들어간다

----------------------------------------------------------------
기존: 전통적인 웹 에플리케이션 여러개의 페이지가 존재하며 멀티 페이지 어플리케이션이라고도 함, 요청할때마다 새로운 페이지가 로딩되어 화면에 나타남,
각자의 html file 을 가지고있다 

SPA : single page application (html file 은 하나이며, 해당 페이지에 접속할때 그 페이지에 해당하는 컨텐츠가 필요할때 동적으로 바디 태그 내부를 채워넣는다)

----------------------------------------------------------------
javascript : 프로그래밍 언어, ecmaScript (정식 명칭), 웹 사이트가 살아 움직이도록 생명을 넣어주는 역할,
스크립트 언어의 특징: 프로그램이 실행되는 런타임에 코드가 해석되고 실행된다

자료형 data type : 프로그래밍 언어에서 데이터를 다루기위해 미리 정해놓은 데이터의 유형 integer, array 등

dynamic typing : 동적으로 자료형이 결정 (동적 타이핑)

undefined : 값이 아직 정의되지 않은 상태
null : 값이 정의되었지만 정의된 그 값이 null 임

----------------------------------------------------------------
객체 : js 에서 객체는 키와 값으로 구성된 쌍의 집합을 의미, 키는 문자열이여야 한다 값은 어떤 자료형이든 다 들어감

함수 : 입력을 받아 정해진 출력을 하는 것(입력:파라미터or인자)
----------------------------------------------------------------
ui : user interface (사용자와 컴퓨터가 상호작용을 하기위해 중간에서 입력과 출력을 제어해주는 것)

ui library : 사용자 인터페이스를 만들기 위한 기능 모음집

lts mode : 단기간에 버전업을 하지 않으며 안정적인 버전을 장기간 유지 방식
----------------------------------------------------------------
앵귤러js : google 에서 만든 open source 로 js 기반 웹 개발 프레임워크

리액트js : face book 에서 만든 오픈소스 js 라이브러리, 사용자와 웹사이트의 상호작용을 돕는 인터페이스를 만들기 위한 js 기능 모음집

뷰js : 에반 뉴라는 중국인이 만듬 리액트와 항상 언급되는 js 기반 프레임워크

프레임워크 : 흐름의 제어 권한을 개발자가아닌 프레임워크가 가짐
라이브러리: 흐름의 제어를 하지 않고 개발자가 필요한 부분만 필요할 때 가져가 사용, 제어 권한이 개발자에게 있음

----------------------------------------------------------------
리액트의 장점 : 빠른 업데이트(웹사이트 탐색 시 화면에 나타나는 컨텐츠가 바뀌는 것)와 렌더링 속도,
빠른 업데이트를 위해 virtual dom 을 사용함,

virtual dom : 가상의 dom(dom:웹페이지를 정의하는 하나의 객체),
화면이 업데이트 된다는 얘기는 곧 dom 이 수정된다는 의미,
기존의 방식: 돔을 직접 수정하는데 성능에 영향을 크게 끼치며 비용도 많이든다(수정할 부분을 돔의 데이터에서 모두 찾아야하기 때문),

가상 돔: 업데이트할 최소한의 부분만을 찾아 업데이트함,
어떤 상태의 변경이 일어나면 버츄얼돔에서 업데이트해야할 최소한의 부분을 검색하고 검색된 부분만을 업데이트하고 
다시 렌더링하며 변경된 부분을 빠르게 사용자에게 보여줌

component : 리액트는 모든 페이지가 컴포넌트로 구성되어있다.

재사용성: 다시 사용이 가능한 성질을 의미, 재사용성이 높게 개발해야한다는건 해당 모듈이 다른곳에서도 쉽게 곧바로 사용할수있도록 개발하는것을 의미, 호환성 문제가 발생하지 않도록하며 의존성을 낮춤,
개발 기간이 단축됨, 유지보수가 용이함(재사용이 높다면 버그의 원일을 찾기 쉬쉽다 (재사용이 높다 == 의존성이 낮다))

리액트는 메타라는 든든한 지원군이있기 때문에 계속해서 발전해 나갈 것임

활발한 지식공유 및 커뮤니티 : 리액트 프로젝트는 아주 많은 개발자가 사용하고 관심을 많이 가지고있다. 도움을 요청할 커뮤니티가 많다.

리액트 네이티브 : 모바일 웹을 개발할 수 있다. 


리액트 단점 : 방대한 학습량, 계속해서 뭔가 바뀜, 새로운 내용이 계속 추가, 
높은 상태관리 복잡도
----------------------------------------------------------------
createElement : jsx code 를 js 로 변환해주는 함수, 파라미터로 type,props(엘리먼트의 속성),[...children] 이 들어감

jsx : js+xml
장점 : 간결한 코드, 가독성 향상, 버그를 발견하기 쉽다, injection attacks (입력창에 문자 숫자 일반적인 값이 아닌 소스코드를 입력하여 해당코드 실행되도록함)방어 
, 중괄호를 사용해서 js 변수나 함수를 사용할 수 있다,

----------------------------------------------------------------
리액트에서 엘리먼트 : 리액트 앱을 구성하는 가장 작은 블록들, 화면에서 보이는것들을 기술,
자바스크립트 객체 형태로 존재하며 마음대로 변경할 수 없는 불변성을 갖고있음,
모든 컴포넌트가 크레이에이트 엘리먼트를 통해 엘리먼트로 변환된다.

리액트 엘리먼트 렌더링 과정 : 버츄얼돔에서 실제 돔으로 이동되는 과정

리액트 엘리먼트의 특징 : 불변성(한번 생성된 후에는 변경될 수 없다), 새로운 엘리먼트를 만들어 앞선 엘리먼트들을 바꿔서 변경 가능

렌더링된 엘리먼트 업데이트 : 

root dom node : 모든 리액트 앱에 필수적으로 들어가며, div 안에 리액트 엘리먼트들이 렌더링되며 root dom node 라 함, 
단 하나의 루트 돔 노드를 가짐, 기존의 웹사이트에 추가적으로 리액트를 연동하게되면 여러개의 루트 돔 노드를 가질 수 있다

돔 엘리먼트 : HTML 요소를 나타냄 

리액트 컴포넌트 : 리액트는 모든 컴포넌트로 구성되었으며 하나의 컴포넌트는 여러 컴포넌트의 조합으로 구성될 수 있다, 
리액트 컴포넌트를 하나의 함수로 생각하면 이해하기 쉽다(입력은 Props, 출력은 React element),

----------------------------------------------------------------
Props : property(속성)(리액트 컴포넌트의 속성), 컴포넌트의 속 재료라고 생각하면됨,
props 는 컴포넌트에 전달할 다양한 정보를 담고있는 js 객체

Props 의 특징 : Read-Only(읽기 전용, 값 변경 불가(엘리먼트 생성 중 바뀌면 제대로된 엘리먼트가 생성될 수 없다)),
다른 props 의 값으로 엘리먼트 생성(새로운 값을 컴포넌트에 전달해 새로 엘리먼트 생성), 
모든 리액트 컴포넌트는 props 를 직접 바꿀수없고 같은 props 에 대해서 항상 같은 결과를 보여줄 것(결과 == 엘리먼트)

props 사용법 : 전달된 props 는 js 객체가 됨, 

----------------------------------------------------------------
클래스 컴포넌트 : es6 의 class 사용해서 만들어진 형태의 컴포넌트,
리액트의 모든 클래스 컴포넌트는 React.Component 를 상속받아 새로운 자식 클래스를 만드는 방법,

컴포넌트 이름 : 항상 대문자로 시작해야한다(리액트는 소문자로 시작하는 컴포넌트를 돔 태그로 인식하기 때문)

컴포넌트 렌더링 : 컴포넌트로부터 엘리먼트를 생성해 최종적으로 리액트 돔을 통해 실제 돔에 효과적으로 업데이트가되고 브라우저를 통해볼 수 있게된다.

컴포넌트 합성 : 컴포넌트 안에 또다른 컴포넌트를 사용할수 있으며, 복잡한 화면을 여러개의 컴포넌트로 나눠서 구현 가능하다.

컴포넌트 추출 : 복잡한 컴포넌트를 나누며 잘활용하면 컴포넌트의 재사용성이 높아진다(컴포넌트가 작아질 수록 기능과 목적이 명확해지고 재사용성이 높아진다 프롭스가 단순 명확해지기때문에
다른곳에서 사용할 수 있다. 개발속도도 향상된다.),
어느정도까지 나눠할지 정해진것은 없지만 보통 기능별로 나눈다, 재사용 가능한 컴포넌트가 많을수록 개발속도 향상된다.
----------------------------------------------------------------
State and LifeCycle
-state : 리액트에서 상태는 리액트 컴포넌트의 상태이며 리액트 컴포넌트의 변경 가능한 데이터를 state 라고하며 state 는 개발자가 정의한다,
렌더링이나 데이터 흐름에 사용되는 값만 state 에 포함시켜야하며 그렇지 않은 값은 컴포넌트의 인스턴스 필드로 정의하면된다,
state 는 자바스크립트의 객체라고 생각하면됨, state 는 직접 수정할 수 있지만 그렇게하면 안됨

-lifecycle : (생명주기) 리액트 컴포넌트의 생명주기를 가지고있으며 생성되는 시점과 사라지는 시점이 정해져있다. 
Mounting (componentDidMount) 출생, updating (componentDidUpdate):인생 Unmounting (componentWillUnmount): 사망
----------------------------------------------------------------
Hooks (react version 16.8 이후로 생김)

함수 컴포넌트와 클래스 컴포넌트 차이
함수컴포에서는 state 사용 불가, 라이프사이클에따른 기능 구현 불가
클래스컴포에서는 생성자에서 state 정의, setState() 함수를 통해 state 업데이트,
라이프 사이클 메소드 제공
위와 같기에 대체할 수 있게 함수 컴포넌트에서도 사용할 수 있게 hooks 가 나옴

-Function component 에서 사용함
-앞에 use 를 사용함
-useState hooks : state 를 사용하기위한 hook, 
const [변수명, set함수형] = useState(초기값)

-useEffect : 사이드 이펙트를 사용수행하기 위한 hook, 리액트에서 사이드 이펙트는 효과/영향을 의미함,
이펙트라고 불리는 이유 : 다른 컴포넌트에 영향을 미칠수있으며 렌더링 중에는 작업이 완료될 수 없기때문(렌더링이 끝난 이후에 실행되어야하는 작업들)
--리액트의 함수 컴포넌트에서 사이드이펙트를 실행할수있게해주는 훅(생명주기 사용)
--ex code useEffect(이펙트 함수, 의존성 배열) : 의존성 배열은 이펙트가 의존하고있는 배열이며 배열안에있는 변수중에 값이 하나라도 변경되었을때 이펙트함수가 실행됨,
기본적으로 이펙트함수는 처음 컴포넌트가 렌더링된 이후와 업데이트로 인한 재 렌더링 이후에 실행됨,
만약 한번씩만 실행되게하고 싶다면 빈배열로 두면 됨,
의존성 배열을 생략하면 컴포넌트가 업데이트될때마다 호출됨

--componentDidMount , componentDidUpdate 와 비슷하게 작동함
	useEffect(() => {
		document.title = `my count ${count} times`
	})

--componentWillUnmount 와 비슷하게 작동하도록 함
	useEffect(() => {
		// 컴포넌트가 마운트 된 이후,
		// 의존성 배열에있는 변수들 중 하나라도 값이 변경되었을 때 실행
		// 의존성 배열에 아무것도 넣지 않으면, 컴포넌트가 마운트와 언마운트시에 한번만 실행
		// 의존성 배열 생략 시 컴포넌트 업데이트 시마다 실행됨
		ServerAPI.subscribeUserStatus(props.user.id, handleStatusChange)

		// 컴포넌트가 마운트 해제되기 전에 실행됨
		return () =>{
			ServerAPI.unsubscribeUserStatus(props.user.id, handleStatusChange)
		}
	}, [의존성 배열1, 의존성 배열2])
----------------------------------------------------------------
useMemo : Memoized value 를 리턴하는 훅 

--Memoized 는 최적화를 위해 사용하는 개념, 비용이 높은 연산량이 많이드는 함수의 호출결과를 저장해두었다가 
같은 입력값으로 함수를 호출하면 새로 함수를 호출하지 않고 이전에 저장해놨던 호출결과를 바로 반환함 이 반환한 값을 memoized value 라고 함

--의존성 배열에 들어있는 변수가 변했을 경우에만 결과 값을 반환하며 변수가 변하지않앗을 경우 기존 함수의 결과 값을 그대로 반환함

--컴포넌트가 다시 렌더링될때마다 연산량이 높은 작업을 반복하는것을 피할 수 있기에 빠른 렌더링 속도를 얻을 수 있다.

--일반적으로 렌더링이 일어나는 동안 실행되면안될 작업을 useMemo 함수에 넣으면안된다. (ex 수동으로 돔을 작업하는 경우 or 서버에서 데이터를 받아오는 경우) 이럴땐 useEffect 함수를 사용해야함

--의존성 배열을 넣지 않을 경우 매 렌더링마다 함수가 실행됨
--의존성 배열이 빈 배열일 경우 컴포넌트 마운트 시에만 호출됨
----------------------------------------------------------------
useCallback
-useMemo() 훅과 유사하지만 값이 아닌 함수를 반환함
-컴포넌트가 렌더링될때마다 매번 함수를 새로정의하는것이아닌 의존성 배열의 값이 바뀐 경우에만 함수를 새로 리턴해줌
--useMemo 와 마찬가지로 함수와 의존성 배열을 파라미터로 받음
----------------------------------------------------------------
useRef

-reference(특정 컴포넌트에 접근할 수 있는 객체 ) 를 사용하기 위한 훅,
useRef 는 reference 를 반환함

-useRef 는 변경가능한 current 라는 하나의 상자라고 생각하면됨

-useRef 는 일반적인 자바스크립트 객체를 반환함

-useRef 는 매번 렌더링될때마다 항상 같은 레퍼런스 객체를 반환함

-useRef 는 내부의 데이터가 변경되었을 때 별도로 알리지 않는다.
(current) 가 변경되었을때 재렌더링되지않음

-Callback ref : useRef 는 따로 변경되었을때 알리지 않기에 useCallback 을 사용하면 자식 컴포넌트가 변경되었을 때 알림을 받을 수 있고 이를 통해 다른 정보들을 업데이트할 수 있다.
----------------------------------------------------------------
hook 규칙

-훅은 무조건 최상위 레벨에서만 호출해야 함

-훅은 컴포넌트가 렌더링될 때마다 매번 같은 순서로 호출되어야함

-리액트 함수 컴포넌트에서만 훅을 호출해야함

eslint-plugin-react-hooks 훅의 규칙을 따르게하는 강제해주는 플러그인
----------------------------------------------------------------
Custom hook 만들기

-이름이 use 로 시작하고 내부에서 다른 훅을 호출하는 하나의 자바스크립트 함수

-여러개의 컴포넌트에서 하나의 커스텀 훅을 사용할 때 컴포넌트 내부에 있는 모든 state 와 effects 는 전부 분리되어있다.
-각 커스텀훅 호출에 대해 분리된 state 를 얻게 됨

-각 커스텀 훅의 호출 또한 완전히 독립적임

-훅들 사이에서 데이터를 공유하는 방법 : ex code
const [userId, setUserId] = useState(1)
const isUserOnline = useUserStatus(useId)
----------------------------------------------------------------
useEffect 의 의존성 배열이 없는 경우엔 마운트된 직후 호출되며 컴포넌트가 업데이트될 때마다 호출됨
useEffect 의 의존성 배열이 있는 경우엔 컴포넌트가 마운트된 직후 호출되며 의존성 배열의 변수가 변동될때마다 호출됨
----------------------------------------------------------------
컴퓨터에서 event == 사건

DOM 에서의 EVENT 는 버튼이 눌리면 온클릭을 통해서 함수 호출

callback 에서 this 를 사용하기 위해선 바인딩을 필수적으로 해줘야함

----------------------------------------------------------------
conditional rendering : 조건부 렌더링/어떠한 조건에 따라 렌더링이 달라지는것

true 이면 보여주고 false 이면 안보여주는 방식

truthy : true 는 아니지만 true 로 여겨지는 값
ex
{} empty object /
[] empty array /
42 number, not zero /
"0", "false" string, not empty /

falsy : false 는 아니지만 false 로 여겨지는 값
ex
0, -0 zero, minus zero /
0n bigInt zero /
'',"",`` empty string /
null /
undefined /
NaN not a number /
----------------------------------------------------------------
element variable : element 를 변수 처럼 사용하는 것

component rendering 원하지 않은 경우 : null return 하면 됨 
----------------------------------------------------------------
List : 목록/리스트를 위해 사용하는 자료구조 :배열(js 의 변수나 객체들을 하나의 변수로 묶어 놓은 것)

key :  각 객체나 아이템을 구분할 수 있는 고유한 값/ react 에서 키는 아이템들을 구분하기 위한 고유한 문자열/ 키 값은 같은 list 에 있는 element 사이에서만 고유한 값이면 됨/ 키로 인덱스를 사용할 수 있다 (아이템들의 고유한 id 가 없을 경우에만 사용하도록함)/ react 에서는 key 값을 넣어주지않으면 기본적으로 index 를 키로 사용함
----------------------------------------------------------------
map : 배열의 첫 번째 아이템부터 순서대로 각 아이템의 어떤 연산을 수행한 뒤 최종 결과를 배열로 리턴해줌 / 맵 함수 안에있는 element 는 꼭 key 가 필요함
ex code
const todoItems = todo.map((todo, index) => 
  <li key={index}>{todo.text}</li>
)
----------------------------------------------------------------
Form : 양식/ 사용자로부터 입력을 받기 위해 사용함/ 

HTML form : 자체적으로 state 를 관리

Controlled Component : 사용자가 입력한 값에 접근하고 제어할 수 있도록 해주는 컴포넌트 / 값이 리액트의 통제를 받는 input form element / 입력값이 리액트의 state 를 통해 관리되며 원하는 입력 양식의 값을 원하는대로 넣어줄 수 있으며 양식의 값이 변경되었을 때 또 다른 양식의 값을 변경시킬 수 있다
----------------------------------------------------------------
textarea tag : 여러 줄에 걸쳐 긴 텍스트를 입력받기 위한 html tag
select tag : option tag 에 value 를 사용해서 값을 선택 할 수 있다
-- 여러개 옵션 선택을 원한다면 
ex code
<select multiple={true} value={['a','c']}> 와 같이 사용 가능

HTML file Input tag : 값이 읽기 전용임(값이 리액트의 통제를 받지 않음)/ 
----------------------------------------------------------------
Share State : State 에 있는 data 를 여러 개의 하위 컴포넌트에서 공통적으로 사용하는 경우
----------------------------------------------------------------
composition : 구성/여러개의 컴포넌트를 합쳐 새로운 컴포넌트를 만드는것, 리액트에서는 합성이라는 뜻

containment : 방지or견제/컨테인(담다) / 리액트에서는 하위컴포넌트를 포함하는 형태의 합성 방법/ 사이드나 다이얼로그 같은 박스 형태의 컴포넌트는 자신의 하위 컴포넌트를 미리 알 수 없다. / children 이라는 prop 를 사용해서 조합

specialization : 전문화/특수화/ 웰컴 다이얼로그는 다이얼로그의 특별한 케이스임/ 범용적인 개념을 구별이 되게 구체화 하는것/ 기존의 객체지향 언어에서는 상속을 사용해서 specialization 을 구현함 / 리액트에서는 합성을 사용해서 specialization 을 사용

inheritance : 상속/부모 클래스를 상속받아 새로운 자식 클래스를 만든다는 개념으로 자식 클래스는 부모클래스가 가진 변수나 함수 속성을 모두 갖게 된다/리액트는 다른 컴포넌트로부터 상속을 받아 새로운 컴포넌트를 만드는것(자주 사용하지 않음)

복잡한 컴포넌트를 쪼개서 여러 개의 컴포넌트로 만들고 만든 컴포넌트들을 조합해 새로운 컴포넌트를 만들자
----------------------------------------------------------------
Context : 컨텍스트를 사용하면 props 를 전달할 필요 없이 데이터를 필요로 하는 컴포넌트에 데이터를 전달할 수 있다. 코드도 깔끔해지며 데이터를 한곳에서 관리하기때문에 디버깅에도 유리하다/ 여러개의 컴포넌트들이 접근해야하는 데이터(로그인 여부 로그인정보 ui 테마 현재 언어 등)


Context.Provider : 데이터를 제공해주는 프로바이더 <MyContext.Provider value={'some value'}> / Provider component 가 rerendering 될때마다 모든 하위 consumer 컴포넌트가 재렌더링됨(state 를 사용해 불필요한 재렌더링을 막을 수 있다 ex code
const [value, setValue] = useState({something: 'something'})
return (
  <MyContext.Provider value={value}>
  <Component />
  </MyContext.Provider>
)
)


Context.Consumer : 컨텍스트의 데이터를 구독하는 컴포넌트/
ex code
<MyContext.Consumer>
/* 만약 상위 컴포넌트의 provider 가 없다면 value 는 createContext 를 호출할때 넣는 기본값과 동일한 역할을 함 */
  {value => /* 컨텍스트의 값에 따라 컴포넌트들을 렌더링*/}
</MyContext.Consumer>


Function as a child : 컴포넌트의 자식으로 함수를 사용하는 방법
ex code
// children 이라는 prop 을 직접 선언 방식
<Profile children={name => <p>이름: {name}</p>}>
// Profile 컴포넌트로 감싸서 children  으로 만드는 방식
<Profile>{name => <p>이름: {name}</p></Profile>


Context.displayName : 컨텍스트 객체는 displayName 이라는 문자열 속성을 가지며 크롬의 리액트 개발자 도구에서는 컨텍스트의 프로바이더나 컨슈머를 표시할때 displayName 을 함께 표시해준다 
ex code
const MyContext = React.createContext('some value')
MyContext.displayName = "MyDisplayName"
// 개발자 도구에서 MyDisplayName.Provider 로 표시됨
<MyContext.Provider>
// 개발자 도구에서 MyDisplayName.Consumer 로 표시됨
<MyContext.Consumer>


useContext() :
ex code 
function MyComponent(props) {
  const value = useContext(MyContext)
  return (
    ...
  )
}


Context API : MyContext = React.createContext(기본값) context 생성/ 만약 상위 레벨에 매칭되는 Provider 가 없다면 기본값이 사용됨 

----------------------------------------------------------------
Styling 
css : cascading style sheets 스타일링이라는 언어

Class selector 사용 예시
<p class='medium'></p>
p.medium { font-size: 16px}

Universal selector 사용 예시
* {
  font-size: 16px;
  color: black;
}

Grouping selector 사용 예시
h1, h2, p {
  color: black;
  text-align: center;
}


:hover : 마우스 커서가 element 위에 올라왔을때
button:hover {
  font-weight: bold;
}
:active : 주로 a tag 에 사용되며 element 가 클릭됐을때를 의미
a:active {
  color: red;
}
:focus : 주로 input tag 사용되며 element 가 초점을 갖고있을 경우 의미
input:focus {
  color: #000000;
}
:checked : radio button 이나 checkbox 같은 유형의 input tag 가 체크되어있는 경우 의미
option:checked {
  background: #00ff00;
}
:first-child :last-child :: 상위 element 기준으로 각각 첫 번째 child 마지막 child 일 경우 의미
p:first-child {
  background: #00ff00;
}
p:last-child {
  background: #00ff00;
}


----------------------------------------------------------------
layout
화면에 element 들을 어떻게 배치할지

display 속성 : 엘리먼트를 어떻게 표시할지 방법에대한 속성/ none|block|inline|flex
--none : element 를 화면에 숨기기 위해 사용/ script tag 의 display 속성 기본값은 display: none;
--block : 블록 단위로 element 를 배치/ p,div,h1~6 tag 의 display 속성 기본값이 display:block
--inline : element 를 라인 안에 넣는것/ span tag 의 display 속성 기본값이 display: inline;
--flex: element 를 블록 레벨의 flex container 로 표시 / container 이기 때문에 내부에 다른 element 들을 포함 

visibility : 가시성 / 보여주거나 감추기 위해 사용하는 속성
--visible : element 를 화면에 보이게하는것
--hidden : 화면에서 안보이게 감추는것이며 화면에서의 영역은 그대로 차지함


position : 엘리먼트를 어떻게 위치시킬것인지 
-- static : 기본값으로 element 를 원래의 순서대로 위치시킴
-- fixed : element 를 브라우저 window 에 상대적으로 위치시킴
-- relative : element 를 보통의 위치에 상대적으로 위치시킴
-- absolute : element 를 절대 위치에 위치시킴 (기준은 상위 element 가 됨)
----------------------------------------------------------------
Flexbox : 기존 css 의 layout 사용이 불편하기에 개선하기위해 등장함
container 와 item 으로 구분됨/ 컨테이너에는 여러개의 엘리먼트를 포함할 수 있으며 이게 플렉스 아이템임 
속성
display: flex;
flex-direction 속성의 대표적인 값들
row: 기본값이며 아이템을 row 행을 따라 가로 순서대로 왼쪽부터 배치
column:아이템을 column 열을 따라 세로 순서대로 위쪽부터 배치
row-reverse: 아이템을 row 행의 역 방향으로 오른쪽부터 배치
column-reverse: 아이템을 column 의 역 방향으로 아래쪽부터 배치


align-items 속성의 대표적인 값들
stretch:기본값으로써 아이템을 늘려서 컨테이너를 가득 채움
flex-start: cross axis 의 시작 지점으로 아이템을 정렬
center: cross axis 의 중앙으로 아이템을 정렬
flex-end:cross axis 의 끝 지점으로 아이템을 정렬
baseline: 아이템을 baseline 기준으로 정렬


justify-content 속성의 대표적인 값들
flex-start: main axis 의 시작 지점으로 아이템을 맞춤
center: main axis 의 중앙으로 아이템을 맞춤
flex-end: main axis 의 끝 지점으로 아이템을 맞춤
space-between: main axis 를 기준으로 첫 아이템은 시작 지점에 맞추고 마지막 아이템은 끝 지점에 맞추며 중간에 있는 아이템들 사이의 간격이 일정하게 되도록 맞춤
space-around: main axis 를 기준으로 각 아이템의 주변 간격을 동일하게 맞춤
----------------------------------------------------------------
Font
font-family : 어떤 글꼴을 사용할지 결정하는 속성/ 글꼴의 이름에 띄워쓰기가 들어갈경우 쌍따옴표로 묶어줘야함
font-family 의 대표적인 글꼴
일반적인 글꼴 분류
serif : 각 글자의 모서리에 작은 테두리를 갖고있는 형태의 글꼴
sans-serif : 모서리에 테두리가 없는 갈끔한 선을 가진 글꼴/ 컴퓨터 모니터에서는 serif 보다 가독성이 좋음
monospace: 모든 글자가 같은 가로 길이를 가지는 글꼴/ 코딩할때 주로 사용
cursive: 사람이 쓴 손글씨 모양의 글꼴
fantasy: 장식이 들어간 형태의 글꼴


font-size 의 대표적인 값들
PX: 고정된 값이며 브라우저를 통해 크기를 바꿀수없다
EM: 사용자가 브라우저의 글꼴의 크기를 변경할 수 있게해준다
16*em == pixels
REM / VW


font-weight: 글꼴의 투께와 관련 속성이며 값으로는 노멀 볼드 사용하며 숫자가 클수록 글자가 두꺼워진다


font-style: 글꼴의 스타일을 지정하기 위한 속성
-normal: 일반적인 글자의 형태 의미
-italic: 글자가 기울어진 형태로 나타남/별도로 기울어진 형태의 글자들을 직접 디자인해서 만든것이므로 브라우저가 이태릭을 지원하는지 확인해야함
-oblique: 글자가 비스듬한 형태로 italic 과 같지만 그냥 글자를 기울인 것임
----------------------------------------------------------------
styled-component : css 문법을 그대로 사용하며 결과물을 스타일링된 컴포넌트 형태로 만들어주는 오픈소스 라이브러리

tagged template literal : js 에서 제공하는 문법중 하나/ literal : 소스 코드의 고정된 값을 의미하며 상수와 다른 개념 /


styled-component 확장 
ex code 
// 버튼 컴포넌트
const Button = styled.div`
  color: grey;
  border : 1px solid red;
`
// Button 에 style 이 추가된 RoundedButton 컴포넌트
const RoundedButton = styled(Button)`
border-radius: 16px;
`
----------------------------------------------------------------
라우터 router
BrowserRouter : 웹 브라우저에서 리액트 라우터를 사용해 라우팅을 할 수 있게해주는 컴포넌트/ 웹 브라우저에는 히스토리라는 기능이 내장되어있으며 사용자가 탐색한 페이지들에 방문 기록이 저장되며 웹브라우저의 뒤로가기를 누르면 히스토리를 이용해 이전 페이지가 어딘지 찾고 해당 페이지로 이동하게되는것임/ 히스토리를 이용해 경로를 탐색할수있게해주는 컴포넌트라고 이해하자

Routes : 실제로 라우팅 경로를 구성할수있게해주는 컴포넌트 / Routes 는 여러개의 Route 를 children 으로 가질 수 있다.

Route : 라우츠 컴포넌트의 하위 컴포넌트로써 패스와 엘리먼트 프롭스를 가지고있고 path 는 경로를 의미하고 element 는 경로가 일치할 경우 렌더링할 리액트 엘리먼트를 의미함

ex code
<BrowserRouter>
  <Routes>
    <Route index element={<MainPage />} />
    <Route path="place" element={<PlacePage />} />
    <Route path="games" element={<GamePage/>} />
  </Routes>
</BrowserRouter>
----------------------------------------------------------------
빌드 : 코드와 애플리케이션이 사용하는 이미지/css file 등의 파일을 모두 모아 패키징하는 과정 

배포 : 빌드를 통해 생성된 정적인 파일들을 배포하려는 서버에 올리는 과정
----------------------------------------------------------------
----------------------------------------------------------------
























```
