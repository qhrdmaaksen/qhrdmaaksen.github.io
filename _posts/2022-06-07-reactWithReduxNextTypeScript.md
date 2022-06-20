---
layout: post
title: "리액트-리덕스-넥스트-타입스크립트"
---

## 유데미 리액트 강좌 공부 정리

```js

리액트
  리액트는 js 라이브러리로 사용자 인터페이스를 만드는데 사용됨

전통적인 웹사이트
  링크를 클릭하면 서버로 요청이진행되며, 새로운 html 페이지가 브라우저로
    보내져서 화면에 보여준다. 

리액트는 응용프로그램을 작은 빌딩 블록과 작은 컴포넌트들로 분할하는 것에
  관한 것으로 모든 빌딩 블록, 모든 컴포넌트들은 명확한 task 들을 갖고있으며
    코드는 유지 보수와 관리가 용이하도록 유지된다 
  리액트에서 라이브러리는 코드를 조합해 화면에 무언가를 렌더링하는 중요한
    작업을 하게된다

앵귤러는 완벽하게 컴포넌트 기반의 UI 프레임워크, 컴포넌트에 집중됨
  처음부터 타입스크립트 적용됐음

뷰 역시 컴포넌트 기반의 UI 프레임워크

var 와 let 과 const 의 차이
  es6 이전에는 변수 선언 var 만 사용가능
    let 은 값을 수정할 수 있는 변수를 선언할 때 사용
  이후에는 let 과 const 사용
    const 는 한번 지정하면 절대 변하지 않은 값인 상수 선언
      만약 const 로 변수 선언했음에도 불구하고 새로운 값을 대입하면 error
  
화살표 함수
  기존 js function
    function myName(){    }
  화살표 함수
    const myName = () => {}
  차이점: 기존 함수보다 짧아졌으며, 키워드 this 로 인해 생겼던 문제들을 해결

  인수가 딱 한개인 경우 사용할 수 있는 방법
  const myName = name => {}

모듈
  person.js 와 utility.js 파일의 내용을 가지고 오고싶을때
    app.js 에서 import 문으로 가져올 수 있으며 person.js 에서 export 
      default person 이라면 import person from 'person.js file 경로'
      (export default person 지정했을때만 import person from 가져옴)
        utility.js 에서는 export const clean = () => {} 함수를 가져오고
          싶다면 import {clean} from 'utility.js file 경로'
            만약 utility.js 에 export const name = () => {} 함수가있다면
              import {name} from 'utility.js file 경로' 로 가져올 수있다
                 import {clean, name} from 'utility.js file 경로' 가능
  별칭을 줘서 사용도 가능하다 ex) import * as bundle from 'utility 경로'
    이렇게 하면 bundle.clean bundle.name 으로 utility.js 의 clean 과
      name 의 함수에 접근 할 수 있다. 일반적으론 import {name} from '경로'

클래스
  프로퍼티는 클래스와 객체에 추가되는 변수와 같은 것
  메소드는 클래스와 객체에 추가되는 함수 같은 것
  메소드는 값으로 함수를 저장하는 프로퍼티

화살표 함수에서는 프로퍼티의 값으로 화살표 함수를 사용하기때문에
  this 를 생략 할 수 있다 
  
스프레드 연산자
  배열의 원소나 객체의 프로퍼티를 나누는데 사용
레스트 연산자
  함수의 인수 목록을 배열로 합치는데 사용
ex) const numbers = [1,2,3]
const newNumbers = [...numbers,4]
console.log(newNumbers)
  [1,2,3,4] 확인

ex02)
// spread object
const people = {
  name : 'seok',
}
const newPeople = {
  ...people,
  name : 'min',
  age : 35
}
console.log(newPeople)
name: 'min', age: 35 확인
===========================
구조 분할
  배열의 원소나 객체의 프로퍼티를 추출해서 변수에 저장할수 있도록해줌
(스프레드는 모든 원소와 프로퍼티를 가져와 새 배열에 객체 등에 전달)
  디스트럭쳐링은 원소나 프로퍼티를 하나만 가져와서 변수에 저장함

  배열 구조 분해
ex)
// 구조 분해
const numbers02 = [1,2,3];
[num1, ,num3] = numbers02;
console.log(num1,num3);
// 1,3 출력  
======================
참조형 및 원시형 데이터 타입
ex)
// 참조형 및 원시형 데이터 타입
const person02 = {
  name : 'min',
}
const person03 = person02; //포인터가 복사된것
person.name = 'woo'
console.log(person03);
// name 은 woo 로 변경됨
const person03 = {
			...person02,
		}; 로 변경해주면 주소가아닌 진짜 복사본이기때문에 min 으로 출력됌
/*객체 pserson02 는 메모리에 저장되어있고 상수 person02 엔 메모리에있는 주소를 가리키는 포인터를 저장함*/
객체와 배열은 참조형 자료 타입임
======================
Refreshing array function 배열 함수 새로고침
  map() 은 내장된 배열 메소드 (배열의 각 원소에서 map 이 실행)
    맵 함수는 예전 값을 새 값으로 반환한다 
ex)
//map 활용 배열의 2 배수 출력
const mapNumber = [1,2,3,4,5];
const doubleNumber = mapNumber.map((num) => {
  return num*2 ;
})
console.log(mapNumber); // [1,2,3,4,5]
console.log(doubleNumber); // [2,4,6,8,10]
======================
배열 기능 참고 자료
코스에서 특히 중요한 사항
map()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map
  (map()메서드 는 호출 배열의 모든 요소에 대해 제공된 함수를 호출한 결과로 채워진 새 배열을 만듬)

ex)
const array1 = [1, 4, 9, 16];
// pass a function to map
const map1 = array1.map(x => x * 2);
console.log(map1);
// expected output: Array [2, 8, 18, 32]
=======================================================
find()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find
  (find()메서드는 제공된 테스트 기능을 충족하는 제공된 배열의 첫 번째 요소를 반환)
  (테스트 기능을 만족하는 값이 없으면 undefined반환됩니다.)

ex)
const array1 = [5, 12, 8, 130, 44];
const found = array1.find(element => element > 10);
console.log(found);
// expected output: 12
=======================================================
findIndex()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex
  (findIndex()메서드는 제공된 테스트 기능을 충족하는 배열의 첫 번째 요소 인덱스 를 반환합니다 . 그렇지 않으면 테스트를 통과한 요소가 없음을 나타내는 를 반환합니다. -1)

ex)
const array1 = [5, 12, 8, 130, 44];
const isLargeNumber = (element) => element > 13;
console.log(array1.findIndex(isLargeNumber));
// expected output: 3
=======================================================
filter()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter
  (filter()메서드 는 제공된 함수로 구현된 테스트를 통과하는 모든 요소가 포함 된 새 배열을 만듭니다 .)

ex)
const words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];
const result = words.filter(word => word.length > 6);
console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
=======================================================
reduce()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce?v=b
  (reduce()는 배열에 있는 모든 요소의 합을 반환)

ex)
const array1 = [1, 2, 3, 4];
// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (previousValue, currentValue) => previousValue + currentValue,
  initialValue
);
console.log(sumWithInitial);
// expected output: 10
=======================================================
concat()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat?v=b
  (concat()방법은 둘 이상의 배열을 병합하는 데 사용됩니다. 이 메서드는 기존 배열을 변경하지 않고 대신 새 배열을 반환합니다.)

ex)
const array1 = ['a', 'b', 'c'];
const array2 = ['d', 'e', 'f'];
const array3 = array1.concat(array2);
console.log(array3);
// expected output: Array ["a", "b", "c", "d", "e", "f"]
=======================================================
slice()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice
  (slice()메서드는 배열의 일부에 대한 얕은 복사본 을 에서 선택한 새 배열 개체로 반환 start합니다 end ( end포함되지 않음). 여기서 start및 end해당 배열의 항목 인덱스를 나타냅니다. 원래 배열은 수정되지 않습니다.)

ex)
const animals = ['ant', 'bison', 'camel', 'duck', 'elephant'];
console.log(animals.slice(2));
// expected output: Array ["camel", "duck", "elephant"]
console.log(animals.slice(2, 4));
// expected output: Array ["camel", "duck"]
console.log(animals.slice(1, 5));
// expected output: Array ["bison", "camel", "duck", "elephant"]
console.log(animals.slice(-2));
// expected output: Array ["duck", "elephant"]
console.log(animals.slice(2, -1));
// expected output: Array ["camel", "duck"]
console.log(animals.slice());
// expected output: Array ["ant", "bison", "camel", "duck", "elephant"]
=======================================================
splice()  => https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice
  (splice()메서드는 기존 요소를 제거하거나 교체하고 새 요소 를 제자리에 추가하여 배열의 내용을 변경합니다 . 배열을 수정하지 않고 배열의 일부에 액세스하려면 을 참조하십시오 slice())

ex)
const months = ['Jan', 'March', 'April', 'June'];
months.splice(1, 0, 'Feb');
// inserts at index 1
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "June"]
months.splice(4, 1, 'May');
// replaces 1 element at index 4
console.log(months);
// expected output: Array ["Jan", "Feb", "March", "April", "May"]
=======================================================
컴포넌트
  사용자 인터페이스에서 재사용 할 수 있는 빌딩 블록
  스타일을 만드는 html 코드와 css 코드 자바스크립트의 결합
  컴포넌트들을 만들기 위해서 리액트는 선언적 접근 방식을 사용
  리액트나 리액트 컴포넌트로 작업할 때는 최종 상태와 어떤 상황에서 어떤 
    상태가 사용되어야하는지 정의(리액트는 이 작업들을 숨어서 처리하게한다)
=======================================================
React Create app (리액트 프로젝트에 필요한 구성요소들을 담고있다)  
실행 하기위해선 node.js 가 필요하며 최신버전을 다운받는다
터미널에서 파일 생성 경로로 이동한다음 npx create-react-app (폴더명)
설치완료 후 터미널에서 생성된 폴더명으로 이동 후 npm start

package.json 파일은 프로젝트에서 어떤 패키지들을 사용하고있는지 보여줌

구축중인 응용프로그램이 업데이트되면 자동으로 미리 볼 수 있도록 개발 서버를
  다시 구동시키는 방법 터미널에서 npm install
====================================================
npm start 프로세스
  개발 서버를 구동하고 코드를 감시하며 코드를 가져가서 브라우저에 전달한다
    (전달하기전에 코드를 변환함)

public 폴더의 index.html 
  한개의 html 파일만이 브라우저에 전달되며, 브라우저에 관리되어
    브라우저에 의하여 렌더링된다
      이 한개의 파일에서 완성된 리액트 응용프로그램 코드를 임포트하고 
        그 코드는 화면에서 보는것들을 업데이트한다

JSX 는 JS 의 XML 을 의미 HTML 은 XML 이라고 할 수 있기 때문

리액트는 화면에 보이는것을 업데이트하는 DOM 지시사항들을 생성하고 실행하는 역할을 함
====================================
컴포넌트
  최상위 컴포넌트는 React.DOM.render 의 지시로 html 페이지에 직접 렌더링됨
  모든 다른 컴포넌트들은 이 지침으로 렌더링되지는 않고, 대신 컴포넌트의 
    html코드 안에 있는 보통의 html요소들을 사용해서 렌더링될 것임

리액트 프로그램에서 이름을 지을땐 대문자로 시작하는 한 단어로 시작해서
  단어들이 결합될때 중간에 시작하는 서브 단어는 대문자로 시작하면됌

리액트에 있는 컴포넌트는 JSX코드를 반환하지만, 단지 자바스크립트 함수일 뿐임

사용자 지정 컴포넌트는 반드시 JSX코드를 사용할 때 대문자로 시작해야한다
  그래야 리액트는 사용자 지정 컴포넌트를 감지할 수 있다

리액트 컴포넌트에는 컴포넌트 안에 반환하는 이 html 파일 즉 JSX코드 안에
  중요한 규칙이 하나 있다 반환하는 문장마다 또는 JSX코드 조각마다 반드시 
    한 개의 루트 요소를 갖는다는 것
여러 div 를 사용하고 싶다면 또다른 <div>태그로 div 부분을 감싸주는 것
  <div>으로 열고 </div> 로 닫는 것

속성 class 는 리액트에서는 className 으로 사용한다 꼭 기억 잘 하자!

보통 css file 은 해당 컴포넌트 파일과 같은 위치에 생성한다 
  컴포넌트 파일에서 import 할땐 import 'css file 경로' 로 사용한다
==============================================
JSX 에서 동적 데이터 출력 및 표현식 작업

동적인 출력 데이터를 위해 JSX코드 안에서 특별한 리액트 구문을 사용합니다
  고정 코드는 중괄호를 열고 닫는 것으로 대체할 수 있습니다 하나의 중괄호를 
    열고 닫습니다 JSX코드의 안에 있는 중괄호에서 특별한 점은 중괄호 안에서 
      기본적인 자바스크립트 코드를 실행할 수 있다는 것
========================================
props 

다른 컴포넌트에서 일부 컴포넌트를 가지고 html 코드의 결과값에 직접 접근할 
  수 없고 저장된 데이터를 거기로 보낼 수 없습니다 하지만 대신 props라는 
    개념을 이용할 수 있습니다 속성을 추가해서 사용자 지정 컴포넌트에 
      데이터를 전달할 수 있습니다

기본적으로 사용자 지정 html 요소를 구축하고 있습니다 그리고 html 
  요소처럼 속성을 가질 수 있는데 리액트로도 우리만의 사용자 지정 컴포넌트도 
    속성을 가질 수 있습니다 리액트에서 이 개념은 속성 대신 props라고불립니다
  
매개변수 한 개를 사용합니다 리액트는 사용하는 모든 컴포넌트에서 한 개의 
  매개변수만을 사용할 것
그 한 개의 매개변수는 프로퍼티로서 모든 속성을 받는 객체가 될 것임 그래서   
  전체적인 개념에 대해 props라는 이름이 붙었습니다
props객체에서 키와 밸류로 이루어진 파일 포맷을 얻는데 그것은 리액트에 의해 
  자동으로 전달
props객체에서 접근하는 키는 선택한 속성 이름이어야 합니다
props는 아주 중요한 개념,왜냐하면 재사용 가능한 컴포넌트를 만들 수 있게 
  해주고 다른 컴포넌트에서 이 컴포넌트로 데이터를 전달할 수 있게 해주기 때문
=========================================
고정 코드화된 값을 가질 수도 있다 props는 동적으로 설정된 값에만 국한되지 
  않습니다
=========================================
toLocaleString()
number.toLocaleString([locales[, options]])
매개 변수
Stringlocales선택
생략하면 웹브라우저의 기본 Locale 값을 사용하지만 직접 지정할 수도 있다. Locale Codes를 참조한다.

Objectoptions선택
다음의 속성들을 전부 또는 일부 포함한 객체로 지정할 수 있다.(실험적인 API 제외)

localeMatcher
지역화 일치 알고리즘을 'lookup' 또는 'best fit'로 지정한다. 기본 값은 'best fit'이다.
style
사용할 서식 스타일이며 기본 값은 'decimal'이다.
다음 아래의 값으로 지정
'deciam': 일반 숫자
'currency': 통화 형식
'percent': 백분율 형식
currency
통화 형식에 사용할 통화이며 가능한 값은 미국 달러 'USD', 유로화 'EUR', 중국 위안화 'CNY' 등과 같은 ISO 4217 통화 코드이다. 기본 값은 없으며 style 속성에서 'currency'를 설정해야 한다.
currencyDisplay
통화를 통화 형식으로 표시하는 방법이며 가능한 값은 €와 같이 현지 통화 기호를 사용하는 'symbol', ISO 통화 코드를 사용하는 'code', dollar와 같이 현지 통화 이름을 사용하는 'name'이 있다. 기본 값은 'symbol'이다.
useGrouping
천 단위 또는 lakh, crore 구분 기호를 사용할지 여부를 boolean 값으로 지정한다. 기본 값은 true이다.
minimumIntegerDigits
사용할 최소 정수 자릿수이며 가능한 값은 1~21사이의 값이다. 기본 값은 1이다.
minimumFractionDigits
사용할 최소 소수 자릿수이며 가능한 값은 0~20사이의 값이다. 일반 숫자와 퍼센트 형식의 기본 값은 0이다. 통화 형식의 기본 값은 ISO 4217 통화 코드 목록에서 참고한다.
maximumFractionDigits
사용할 최대 소수 자릿수이며 가능한 값은 0~20사이의 값이다. 일반 숫자 형식의 기본 값은 minimumFractionDigits와 3보다 크다. 통화 형식의 기본 값은 minimumFractionDigits 보다 크고 ISO 4217 통화 코드 목록에서 제공하는 부 단위의 숫자의 수이다.
minimumSignificantDigits
사용할 유효 숫자의 최소 수이며 가능한 값은 1~21이다. 기본 값은 1이다.
maximumSignificantDigits
사용할 최대 유효 자릿수이며 가능한 값은 1~21이다. 기본 값은 21이다.
반환
Stringstr
숫자의 사용 언어에 따른 표현을 포함한 문자열을 반환
const n1 = 12345.6789;
const n2 = -12345.6789;
const option = {
  maximumFractionDigits: 4
};
const cn1 = 
      n1.toLocaleString('ko-KR', option);
const cn2 = 
      n2.toLocaleString('ko-KR', option);
document.writeln(cn1);
document.writeln('<br>');
document.writeln(cn2);
12,345.6789
-12,345.6789
=========================================
<ExpenseItem title={props.expenses[0].title}
										 amount={props.expenses[0].amount.toLocaleString('ko-KR', option)}
										 date={props.expenses[0].date}/>
                     컴포넌트 분할 시 item 활용
<ExpenseItem title={props.item[0].title}
										 amount={props.item[0].amount.toLocaleString('ko-KR', option)}
										 date={props.item[0].date}/>
====================================
박스 밖에 있는 모든 디폴드 Html 컴포넌트들은 렌더링된 html 요소들에게 
  CSS클래스를 추가하는 className을 지원합니다

합성에서 특히 중요한 부분은 props.children인데 래퍼 컴포넌트를 생성하게 
  하며 특별한 컴포넌트라고 할 수 있다

박스 밖에 있는 모든 디폴드 Html 컴포넌트들은 렌더링된 html 요소들에게 
  CSS클래스를 추가하는 className을 지원함

사용자 정의 컴포넌트들은 내가 지원하라고 지시한 것만 지원함
================================================================
props
0. props가 없을 때
//App.js
import React from 'react';
import First from './First';
					
function App() {
  return <First />;
}
// First.js
import React from 'react';

function First() {
  return <div>첫 째입니다</div>;
}
export default First;
결과 = 첫 째 입니다
-----------------------------
. props (properties)의 역할
//App.js
import React from 'react';
import Second from './Second';
					
function App() {
  return <Second name="동2" />;
}
// Second.js
import React from 'react';

function Second({ name }) {
  return <div> 둘 째 {name} 입니다</div>;
}
export default Second;
'0. props가 없을 때'와의 차이점을 아시겠나요?
props는 부모(App.js)가 자식(Secnond.js)에게 전달해주는 값, 파라미터입니다. <Second name= "동2" />는 Second에서 name을 '동2'라고 지정는 것이죠.

참고로 props는 javascript 객체 형태로 전달됩니다. 자바스크립트의 Destructing 문법이 적용된 이유입니다. 참고로 return <div> 둘 째 {name} 입니다</div>;에서 name을 중괄호({})로 감싼 이유는 html 태그에서 자바스크립트를 사용하기 위함입니다.
--------------------------------------------------------
2. children
First.js, Second.js를 모두 포함하는 컴포넌트(House.js)가 필요한 상황이라고 가정하겠습니다. 아래처럼 , 를 감싸는 <House/> 컴포넌트가 있습니다.
// App.js
import React from 'react';
import First from './First';
import Second from './Second';
import House from './House';

function App() {
  return (
    <House>
      <First />
      <Second name="동2" color="blue" />
    </House>
  );
}
export default App;
// House.js
import React from 'react';
function House() {
  const style = {
    border: '4px solid green',
    padding: '16px',
  };
  return <div style={style}></div>;
}
export default House;
서버를 켜보면 House는 정상적으로 초록색 박스가 그려지는데, 내부의 컴포넌트인 First, Second는 작동하지 않는 것을 볼 수 있습니다.
컴포넌트 태그(House) 사이의 컴포넌트(First, Second)의 값을 조회하고 싶을 때 props.children을 사용해야 합니다.
// House.js
import React from 'react';

function House({ children }) {
  const style = {
    border: '4px solid green',
    padding: '16px',
  };
  return <div style={style}>{children}</div>;
}
export default House;
3. props, children 정리
props: 어떤 컴포넌트를 import해와서 사용하는 부모(상위) 컴포넌트 (ex. App.js)에서 정하는 값입니다. 부모 컴포넌트에서 설정해서 자식 컴포넌트로 전달하여, 자식 컴포넌트에서 쓰입니다.
children: A 컴포넌트 사이에 B 컴포넌트가 있을 때, A 컴포넌트에서 B 컴포넌트 내용을 보여주려고 사용하는 props입니다.
================================================================
임포트된 리액트 객체에는 호출할 수 있는 createElement 메소드가 있기 
  때문인데요JSX를 사용할 때, 그것은 호출되는 이 메소드에 가깝습니다
    createElement메소드는 세 개의 인자를 취합니다
  첫 번째 인자는 생성해야 하는 요소인데요 예를 들면, div 같은 것이죠
    만약 이것이 내장된 html요소라면 ‘div’처럼 요소의 이름으로 문자열을 
      전달합니다 
  두 번째 인자는 이런 요소를 설정하는 객체입니다
    요소의 모든 속성을 설정하는 객체를 말하는데 이 div는 속성을 갖지 않기 
      때문에 여기서는 빈 객체를 전달할 수 있습니다
    세 번째 인자는 이 여닫는 <div>태그 사이에 있는 컨텐츠입니다 사실 이것은 
      단지 세 번째 인자가 아니라 여닫는 태그 사이에 있는 다양한 컨텐츠 
        조각들인 무한대의 긴 목록의 인자를 가질 수도 있습니다 그래서 여기 
         2개의 요소가 있고 2개의 추가적인인수를 갖게 됩니다
================================================================
import React from 'react';를 모두 적어주자 
  JSX코드를 사용할 때 리액트가 사실은 내부에서 사용되고 있다는 것을
    강조하기 위해

React.js 를 사용할땐 선언적 js code 사용
  
JSX 
  React project 에서 사용하는 비표준 구문
  뒤에서 표준 js code 로 컴파일됨


















```
