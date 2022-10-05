---
layout: post
title: "리액트-리덕스-넥스트-타입스크립트"
---

## 유데미 리액트 강좌 공부 정리

```js

리액트
-리액트는 js 라이브러리로 사용자 인터페이스를 만드는데 사용됨
-React :client side javascript library 모든 렌더링은 클라이언트서 일어남
-사용자 브라우저에 보이는 것은 서버에서 나온 것이 아니며 결과적으로 
사용자가 페이지를 방문할 때 서버에서 클라이언트로 전송되는 실제 HTML 코드는 
상당히 비어 있음

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
. props 의 역할
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

버튼의 입력 타입이 submit이라면 폼 대신에 클릭된다면 전체 폼 요소는 수신할
  수 있는 이벤트를 생략할 것입니다 이것이 바로 submit 이벤트
    버튼을 클릭할때마다 새로고침됨 (브라우저는 사실 폼이 제출될 때마다 이
      웹페이지를 호스팅하고 있는 서버에 요청을 보내기 때문)
        그래서 form 자체에 onSubmit 으로 함수생성해서 preventDefault 처리
          (preventDefault,기본 요청이 보내지는것을 막아줌)

state를 사용하면 장점이 있습니다 양방향 바인딩이라는 것을 구현할 수 있습니다
  변경되는 입력값만 수신하는 것이 아니라 입력에 새로운 값을 다시 전달할
    수도 있다는 것 프로그램에 따라 입력값을 재설정하거나 입력할 수 있습니다
      기본 속성인 value를 입력 요소에 추가하면 됨

속성은 오로지 부모에서 자식으로만 전달될 수 있습니다

무상태, dumb, 프리젠테이션 컴포넌트 : 상태를 가지고있지않으며 데이터 출력만

Smart, 상태 유지 컴포넌트 : 상태를 가지고있다

key 는 고유한 값을 넣어주자, ex 아이디, 아이디가 없다면 중복되지않는 고유값
  인덱스를 사용할 수 있지만 특정한 아이템에 대한 인덱스가 항상 똑같으며,
    아이템 컨텐츠에 직접적으로 첨부된게 아님, (함수가 자동으로 인덱스관리)

따로 데이터가있는경우 ex props.items , state 를 사용하지않고 그대로
  props.items 로 사용하면된다

css module : css file 에 ex(ex.css)를 ex.module.css 로 변경하여
  참조하는 js 에서 import 로(import styles from `ex.module.css`) 해당 file 을 임포트해주고 속성에서
    className={styles[해당 css class]} 로 사용

label에는 보통 속성으로 for를 추가하는데 for는 class와 마찬가지로 JSX에서
  사용할 수 없습니다 자바스크립트 예약어이기 때문입니다 그래서 htmlFor라고
    설정하는데 그것은 label에 for의 속성을 할당하는 props 이름입니다

jsx 는 컴포넌트에서 반환하는 코드임, 리액트는 이 코드를 실제 돔으로 렌더링함
jsx 코드는 리액트 createElement 로 변환됨

fragment 사용시 불필요한 html 요소들이 줄어듬
  <>
    로 사용하거나
  </>

  <React.Fragment>
    로 사용하지만 이 방법은 항상 작동하므로 권장
  <React.Fragment/>

createPortal
  (Portal은 부모 컴포넌트의 DOM 계층 구조 바깥에 있는 DOM 노드로 자식을 렌더링하는 최고의 방법을 제공)
  (https://ko.reactjs.org/docs/portals.html)
  이 메소드는 두개의 인수를 취한다
    첫 번째는 렌더링되어야하는 리액트 노드, 두 번째 인수는 포인터

ref
  ref는 객체가 출력되며 current 속성이있다 ref 값은 항상 객체이며 항상
    current 프롭을 가지고있다 current 프롭은 그 ref가 연결된 실제 값을
      습니다  기본값은 정의되지 않음이지만 이 코드가 실행되자마자 이 ref
        프롭 때문에 nameInputRef는 인풋에 연결됩니다 current 프롭에
          값으로 저장된 인풋이죠 여기에 저장된 것은 실제 DOM 노드입니다
            그래서 어떤 이론적인 값 같은 게 아니라 실제 DOM 노드입니다
  값을 빠르게 읽고 싶거나 값만 읽거나 아무것도 바꿀계획이 없을때 사용

useEffect 이펙트
-useEffect 에 입력한 함수는 promise 를 반환하면안됨
--useEffect 에서는 async 를 사용하면 안됨
---사용하고 싶다면 useEffect 함수 내부에 중첩 함수로 새 함수를 만들어사용
  예를 들면 http 리퀘스트를 보내는 것 또는 브라우저 저장소에 무언가를
    장하는 것입니다 예를 들어 로컬 저장소에요 또한 코드에서 타이머나 간격을
      설정할 수도 있습니다
  useEffect 훅은 그냥 내장 훅입니다 여러분의 컴포넌트 함수 내부에서 실행할
    수 있는 또다른 함수입니다
  두 개의 매개변수, 두 개의 인수와 같이 호출됨
    첫 번째 인수는 함수
      모든 컴포넌트 평가 후에 실행되어야하는 함수 (지정된 의존성이 변경된 경우)
    두 번째 인수
      지정된 의존성을 두 번째 인수로 넣어줘야 함
        의존성으로 구성된 배열임
    의존성으로 구성된 배열이며 의존성이 변경될 때마다 첫 번째 함수가 다시
      실행되며 첫 번째 함수에 어떠한 사이드 이펙트 코드라도 넣을 수 잇음
        그러면 지정한 의존성이 변경된 경우에만 실행됨
          컴포넌트가 다시 렌더링될때는 실행되지 않음
            의존성이 변경된 경우에만 실행됨
    데이터 가져오기는 사이드이펙트입니다 UI와 직접적인 관련이 없습니다
-항상, 참조하는 모든 항목을 의존성으로 useEffect 내부에 추가해야 한다는
 겁니다 그렇게 하지 않을 합당한 이유가 없다면
-useReducer 또는 useState에 의해 노출된 state 업데이트 함수는변경되지
않도록 리액트가 보장됩니다 따라서 의존성으로 추가할 필요가 없습니다
변하지 않으니까요
ex code (
    function App() {
const [isLoggedIn, setIsLoggedIn] = useState(false);
useEffect(() => {
  const storedUserLoggedInInfomation = localStorage.getItem('isLoggedIn');
  if (storedUserLoggedInInfomation === 'login') {
    setIsLoggedIn(true);
  }
}, [])
const loginHandler = (email, password) => {
  // We should of course check email and password
  // But it's just a dummy/ demo anyways
  localStorage.setItem('isLoggedIn', 'login');
  setIsLoggedIn(true);
};
const logoutHandler = () => {
  localStorage.setItem('isLogout', 'logout');
  setIsLoggedIn(false);
};
  )
  의존성 배열에 추가하게되면 추가된 배열을 마지막 컴포넌트 렌더링 주기에서
    변경된 경우에만 실행하라고 하는것임
  이메일 또는 비번 필드의 키 입력에대한 응답으로 해당 폼의 유효성을 확인 및
    업데이트하는것에 사용될 수 있고 무언가에대한 응답으로 실행되는 코드를
      다루는데 도움이되며 무언가는 로드되는 컴포넌트일수도있고 업데이트되는
        이메일 주소일수도있고 무엇이든 될 수 있다 어떤 액션에대한 응답으로
          실행되는 액션이있다면 그건 사이드 이펙트이다
  effect 함수에서 사용하는 모든 "것들"을 추가해야 합니다. 구성 요소(또는 
    일부 상위 구성 요소)가 다시 렌더링 되어 이러한 "것들"이 변경될 수 있는 
      경우.그렇기 때문에 컴포넌트 함수에 정의된 변수나 상태, 컴포넌트 수에 
        정의된 props 또는 함수는 종속성으로 추가되어야 합니다!
  기간을, 타이머를 두고 싶을때 (디바운싱)
    사용자가 타이핑을 일시 중지했을때 시간을 걸어두고 작업 수행
  클린 업 함수
    useEffect 함수가 실행될 때마다 처음 실행되는 경우를 제외하고 이 클린업 
      함수가 실행됩니다 또한 이 클린업 함수는 이펙트를 특정한 컴포넌트가
        DOM에서 마운트 해제될 때마다 실행됩니다 즉 컴포넌트가 재사용될 
          때마다죠 즉 클린업 함수는 모든 새로운 사이드이펙트 함수가 
            실행되기 전에, 그리고 컴포넌트가 제거되기 전에 실행됩니다 그리고
              첫 번째 사이드이펙트 함수가 실행되기 전에는 실행되지 않습니다
                그러나 그 이후에는 실행됩니다 모든 다음 사이드이펙트 
                  함수들이 실행되기 전에요 
  useEffect(()=>{
  console.log('effect running')
})
  현재 의존성에 대한 정보는 없는 상태이며 이 경우 컴포넌트가 처음 
    마운트되었을때 실행되며 state 가 업뎃될때마다 실행됨
      빈 배열을 추가하게되면 이 컴포넌트가 처음으로 마운트되고 렌더링될 
        때만 실행됩니다 그러나 그 이후에는, 이후의 렌더링 주기에는 실행되지 
          않습니다 만약 의존성을 추가하게된다면 해당 컴포넌트가 재평가 
            될때마다 재실행됨 state 가 변경될때마다 실행됨
useEffect(()=>{
  console.log('effect running')
  return ()=> {
    console.log('effect cleanup');
  }
}, [enteredPassword])
위 경우 비밀번호 입력시작시 effect cleanup 이 트리거됨
useEffect(()=>{
  console.log('effect running')
  return ()=> {
    console.log('effect cleanup');
  }
}, [])
  위 경우 의존성이 없으며 effect cleanup 은 한번만 표시됨
    이 경우 클린업 함수는 컴포넌트가 제거되면 실행됩니다 따라서 이 경우에는 
      예를 들어 로그인하고 컴포넌트가 DOM에서 제거되면 "이펙트 클린업"이 
        표시됩니다


브라우저 저장소 일반적인 저장소 : 쿠키 또는 로컬 저장소


useReducer 리듀서
-내장된 훅임 state 관리를 도와줌 그래서 useState와 약간 비슷함 하지만 더 
많은 기능이 있으며 복잡한 state에 특히 유용함 가끔 복잡한 state가 
있을때 예를 들어 여러 state들이 함께 속해 있는 경우에 같은 것을 
관리하는데 관리하는 측면이 다를 경우 또는 여러 state가 같이 바뀌거나
서로 관련된 경우가 있을거임 그런 경우에는 useState나 거기에서 얻은 state는
종종 사용 및 관리가 어려워지거나 오류가 발생하기 쉽다 나쁘거나 비효율적이거나
버그가 생길 수 있는 코드가 되기 쉬운데 이런 경우 useReducer를 useState 
대신 쓸 수 있다 더 강력한 state 관리가 필요한 경우, 대체할 수 있음 하지만 
그렇다고 해서 항상 useReducer를 사용해야 한다는 건 아니지만 사용하기 조금 
더 복잡하기 때문에 조금 더 설정이 필요함 따라서 대부분의 경우에는 seState를 
사용하는 것이 좋음 그러나 useReducer 가 작동하도록 추가 작업을 할 만한 
가치가 있는 경우가 있음
/*초기 입력 상태*/
const initialInputState = {
value: '',
isTouched: false,
}
/*reducer 에는 2 개의 인자 필요, 이전 state 와 리액트에 의해 전달되는 action
* -action 은 code 에 전달되어 최종적으로 새로운 state 반환*/
const inputStateReducer = (state, action) => {
if (action.type === 'INPUT') {
  return {value: action.value, isTouched: state.isTouched}
}
/*focus 를 잃은 경우 사용자가 입력칸을 건드렸단 의미로 true 로 새로운 객체 설정*/
if (action.type === 'BLUR') {
  return {isTouched: true, value: state.value}
}
if (action.type === 'RESET') {
  return {isTouched: false, value: ''}
}
return {
  value: '',
  isTouched: false,
}
}
-(공식문서)
다수의 하윗값을 포함하는 복잡한 정적 로직을 만드는 경우나 다음 state가 이전 
state에 의존적인 경우에 보통 useState보다 useReducer를 선호

useReducer는 자세한 업데이트를 트리거 하는 컴포넌트의 성능을 최적화할 수 
있게 하는데, 이것은 콜백 대신 dispatch를 전달 할 수 있기 때문

초기 state의 구체화
useReducer state의 초기화에는 두 가지 방법이 있습니다. 유스케이스에 따라서 
한 가지를 선택하세요. 가장 간단한 방법은 초기 state를 두 번째 인자로 
전달하는 것

초기화 지연
초기 state를 조금 지연해서 생성할 수도 있습니다. 이를 위해서는 init 함수를 
세 번째 인자로 전달합니다. 초기 state는 init(initialArg)에 설정될 
것입니다.
이것은 reducer 외부에서 초기 state를 계산하는 로직을 추출할 수 있도록 
합니다. 또한, 어떤 행동에 대한 대응으로 나중에 state를 재설정하는 데에도 
유용합니다.



-useState처럼, useReducer도 항상 두 개의 값이 있는 배열을 반환합니다
따라서 배열 디스트럭처링을 사용할 수 있습니다 반환되는 두 가지 값은
최신 state 스냅샷입니다 (state 관리 메커니즘이기때문)
ex code(
  const [state, dispatchFn] = useReducer(reducerFn, initialState, initFn)
)
-action 을 dispatch 하면 reducerFn 함수가 소비한다 (최신 스냅샷을 자동으로 가져오는 함수)
-리액트는 새 액션이 디스패치될때마다 리듀서 함수를 호출함
-리듀서 함수는 새로운 업데이트된 state 를 반환함
-초기 state나 초기 함수를 설정할 수도 있습니다 초기 state를 설정하기 위해 실행해야 하는 함수죠
초기 state가 좀 더 복잡한 경우라면요 예를 들어 http 리퀘스트의 결과나
또는 그와 비슷한 경우
-컴포넌트 함수 내부에서 정의된 어떤 것과도 상호 작용필요 없다면 
컴포넌트 함수 밖에 리듀서 함수를 만들어도됨
-리듀서 함수는 최신 state 스냅샷 과 디스패치된 action 두 개의 인수를 갖음


-emailIsvalid state와 다른 state입니다 물론 관련은 있죠두 가지 모두 
사용자가 입력한 내용에 따라 바뀝니다 하지만 엄밀히 말하자면 이 두 가지는 
서로 다른 state입니다 두 개의 다른 변수죠 그리고 다른 state를 보고 새로운 
emailIsvalid state를 도출하는 건 해서는 안 되는 일입니다 대부분의 경우에는 
잘 작동하지만 그러나 어떤 경우에는 작동하지 않을 수 있습니다 왜냐하면 
enteredEmail에 대한 어떤 state 업데이트는 제 시간에 처리되지 않을 수도 
있기 때문입니다 그 경우에는 emailIsValid를 어떤 오래된 enteredEmail 
state를 기반으로 업데이트하게 되는 거죠 따라서 여기서는 함수 폼을 사용해야 
합니다

객체 디스트럭쳐링
ex code)
// 객체 디스럭쳐링으로 emailState 에서 isValid 속성을 가져왔고 유효성 검사를 하지않을땐 useEffect 가 실행되지않음
const {isValid: emailIsValid } = emailState;
const {isValid: passwordIsValid} = passwordState;

useEffect(() => { // 다른 state 를 기준으로 state 를 update 하는 좋은 방법
  const identifier = setTimeout(() => {
    console.log('유효성 식별 검사')
    //이메일에 @ 가 포함되어야하며 입력된 비밀번호가 정확한지 체크 및 입력 이메일또는 비번이 변경될때 업데이트
    setFormIsValid( // setFormIsValid 가 useEffect 안에있기때문에 여전히 state 스냅샷을 참조한다
        emailState.isValid && passwordState.isValid)
  }, 500) // 0.5초 딜레이
  return () => {
    console.log('clean up')
    clearTimeout(identifier) // 타이머 초기화

  }
}, [emailIsValid, passwordIsValid])

useReducer 을 언제 사용해야하나
-useState 는 주요 state 관리 도구이며 개별 state 및 data 다루기에 적합
하지만 복잡한 state 또는 state 로서 객체가 존재하는 경우엔 useReducer 의
사용을 생각해볼만함 복잡한 state 업데이트 로직을 포함하는 리듀서함수를
사용할수있기때문, 컴포넌트 함수 바디에서 별도의 리듀서 함수로 이동도 가능,
-연관된 state 조각들로 구성된 state 관련 데이터를 다루는 경우
-useReducer 를 사용해서 폼 state 를 전체적으로 관리 할 수 있음,
폼 유효성을 위해서 useState 를 사용하는 대신 가능

state 관리는 끌어올린 최종 컴포넌트 파일에서 관리한다?

react Context consumer
-react 내부적으로 state 를 관리할수있도록 해줌
- 컴포넌트 전체 state 저장소에서 액션을 트리거할 수 있으며, 관련된 
컴포넌트에 직접 전달 할 수 있다
-앱의 어떤 컴포넌트에서라도 직접 변경해서 앱의 다른 컴포넌트에 
직접 전달할수있게해줌(프롭체인을 구축하지않아도됨)
--소비자방법
-기본값이 있으면 공급자는 필요없다
-소비자는 자식을 가지고 함수여야한다

useContext Hook
-context consumer 와 세팅은 거의 비슷
다른점은 useContext 를 사용한다는 것과 심플?
-언제 프롭을 사용하고 언제 컨텍스트를 사용할지 알 수 있습니다 대부분의 
경우에는 프롭을 사용하여 컴포넌트에 데이터를 전달합니다 프롭은 컴포넌트를 
구성하고 그것들을 재사용할 수 있도록 하는 매커니즘이기 때문입니다 따라서 
많은 컴포넌트를 통해 전달하고자 하는 것이 있는 경우에만, 그리고 예를 들어 
네비게이션처럼 매우 특정적인 일을 하는 컴포넌트, 예를 들어 항상 사용자를 
로그아웃시키는 버튼이 있죠, 그런 컴포넌트로 전달하는 경우에만 컨텍스트를 
사용하는 게 좋다
-공식문서
const value = useContext(MyContext);
context 객체(React.createContext에서 반환된 값)을 받아 그 context의 현재 
값을 반환합니다. context의 현재 값은 트리 안에서 이 Hook을 호출하는 
컴포넌트에 가장 가까이에 있는 <MyContext.Provider>의 value prop에 의해 
결정됩니다.
컴포넌트에서 가장 가까운 <MyContext.Provider>가 갱신되면 이 Hook은 그 
MyContext provider에게 전달된 가장 최신의 context value를 사용하여 
렌더러를 트리거 합니다. 상위 컴포넌트에서 React.memo 또는 
shouldComponentUpdate를 사용하더라도 useContext를 사용하고 있는 컴포넌트 
자체에서부터 다시 렌더링됨
useContext를 호출한 컴포넌트는 context 값이 변경되면 항상 리렌더링 될 
것입니다. 컴포넌트를 리렌더링 하는 것에 비용이 많이 든다면, 메모이제이션을 
사용하여 최적화할 수 있습니다
-팁
여러분이 Hook 보다 context API에 친숙하다면 useContext(MyContext)는 
클래스에서의 static contextType = MyContext 또는 <MyContext.Consumer>와 
같다고 보면 됩니다.
useContext(MyContext)는 context를 읽고 context의 변경을 구독하는 것만 
가능합니다. context의 값을 설정하기 위해서는 여전히 트리의 윗 
계층에서의<MyContext.Provider>가 필요합니다.
-프롭체인을 교체하기위해선 사용하기괜찮음

Context 의 한계
-앱 전체 또는 컴포넌트 전체 state에는 적합할 수 있습니다 즉 기본적으로 
여러 컴포넌트에 영향을 미치는 state들에는요 하지만 컴포넌트 구성을
대체할 수는 없습니다
(재사용 가능한 버튼 같은 경우 컨텍스트를 사용해 사용자가 클릭시 
항상 로그아웃을 시키면 다른곳에서 이 컴포넌트를 재활용하는 한계가 존재
이런 경우는 context 를 사용하지않고 prop 을 사용해서 구성)
-변경이 잦은 경우에는, 리액트 컨텍스트는 그다지 적합하지 않습니다
예를 들어, 매초 또는 1초에 여러 번 state가 변경되는 경우
-이러한 Input 컴포넌트는 보시다시피 재사용할 수 있어야 합니다
따라서 구성할 수 있도록 프롭으로 합니다 그들을 사용하는 부모 내부에서요
인풋 내부에서 컨텍스트를 사용한다면,모든 인풋은 동일한 작업을 수행합니다
동일한 컨텍스트에 바운딩되겠죠그러면 재사용하기 어려울 수 있습니다

redux
-state가 자주 변경되는 경우 사용
-프롭의 모든 컴포넌트 커뮤니케이션을 대체하기 위해 사용하면 안됨

리액트 훅 작업할 때 지켜야할 규칙
-리액트 훅은 리액트 함수안에서만 호출해야함
-사용자 정의 훅에서도 사용가능
-리액트 훅은 리액트 컴포넌트 함수 또는 사용자 정의 훅 함수의 최상위
수준에서만 호출해야함 훅 중첩 함수에서 훅을 호출하면안됨
-리액트 훅 useContext는 콜백 내부에서호출할 수 없습니다, 리액트 훅은
리액트 함수 컴포넌트 또는 사용자 정의 리액트 훅 함수 안에서 호출되어야
합니다,그리고 최상위 수준에서 직접 호출되어야 함
-if 문에서도 불가능

useImperativeHandle hook
- 이 훅을 사용하면 컴포넌트나 컴포넌트 내부에서 오는 기능들을
명령적으로 사용할 수 있게 해줍니다 즉 일반적인 state 프롭 관리를 
통하지 않고 부모 컴포넌트의 state를 통해 컴포넌트를 제어하지 않고
프로그래밍적으로 컴포넌트에서 무언가를 직접 호출하거나 조작해서 
사용하게 해주는 거죠 다시 말씀드리지만, 이건 거의 사용하지
않을 거임
- 두 번째 매개변수는 함수입니다 객체를 반환해야 하는 함수죠
그 객체는 외부에서 사용할 수 있는 모든 데이터를 포함할 것입니다
예를 들어 여기에 activate 필드나 focus 필드를 추가할 수 있습니다
-useImperativeHandle 및 forwardRef를 사용하면 리액트 컴포넌트에서 온 
기능을 노출하여 부모 컴포넌트에 연결한 다음, 부모 컴포넌트 안에서
참조를 통해 그 컴포넌트를 사용하고 기능을 트리거할 수 있습니다

img 이미지 사용
-import 로 해당 폴더에서 직접 사용
(단순히 이미지를 임포트하면 됩니다 css 파일을 가져오는 것과 비슷)
-내부에서는 임포트하면 완성된 애플리케이션에 이미지가 포함하도록 변환됩니다
애플리케이션은 서버에 배포하여해당 이미지에 대한 링크를 만들 수 있습니다
그 링크는 만들어진 코드에 동적으로 삽입됨
-어떤 서버에 있는 이미지라면 그 이미지에 대한 URL을 쓰면 됨
(local 에있는 img 라면 그냥 import 이름 사용하면됨 ex src={import name})

className 속성 입력 시
ex01 code
header 는 className={classes.header}
ex02 code
header-list 는 className={['header-list']} 로 사용해야함 점 표기법 안됨

렌더링 하는곳에서 useState 로 관리를 하자
또는 상위 컴포넌트에서 프롭으로 state 데이터를 전달해주자
하지만 App 에서 렌더링하는 컴포넌트는 상위는 index 밖에없기에 App 에서 진행

modal backdrop 설정할때 createPortal 사용하여 index 에 루트 생성 및
백드롭 활성화는 속성 프롭 ex onClose={props.onClose} 도 같이 넣어줘야함
{ReactDOM.createPortal(
          <Backdrop onClose={props.onClose}/>,
          portalElement)}

모달창 안에 장바구니 데이터 출력
-{ReactDOM.createPortal(
          <ModalOverlay>
            {props.children}
          </ModalOverlay>,
          portalElement)}

리액트에서는 관습적으로 애플리케이션 전체 state 관리는 이름을 store 라고함

컨텍스트는 시간에 따라 변경되게, 애플리케이션의 일부도 시간에 따라 업데이트
되도록 설정 할 수 있다

사용자 정의 컴포넌트에는 ref 프롭 작동하지 않음
-하지만 사용하려면 ref 를 받고 싶은 컴포넌트로 가서 컴포넌트 함수를 
React.forwardRef 로 감싸주면 해당 컴포넌트 함수는 forwardRef 의
인수가 되며 ref 를 얻을 수 있다
ex code
const Input = React.forwardRef((prop, ref) => {

bind method 는 함수를 사전에 구성함 향후 실행을 위해서 기본적으로 인수를 
미리 구성할 수 있음 함수가 실행될때 받을 인수
* -컴포넌트와 이벤트 함수를 연결하는것
* -바인딩하지않아도 이벤트 함수는 실행되지만 어떤 컴포넌트가 호출했는지 
알수없음
* -바인딩하지않으면 이벤트 함수에서 this.state or this.props 사용할경우 
undefined 로 처리됨

리액트
-사용자 인터페이스 구축을 위한 js 라이브러리

-리액트는 가상 dom 과 비교를 통해서 최종 스냅샷과 현재의 스냅샷을 
실제 DOM 에 전달하는 구조는 갖음

-리액트의 핵심은 컴포넌트

-리액트 dom 은 웹에대한 인터페이스

-리액트 DOM 은 컴포넌트에 HTML 요소들이 포함되있는지 고려함

-리액트는 컴포넌트를 관리하고 상태 객체를 관리하고 다른 객체의 상태와
컴포넌트가 바뀌어야하느지 확인하고 컴포넌트의 변경 전후 상태를 확인함

-리액트는 변경된 내용과 어떤 화면이든간에 화면에 표시되야할 정보 모두를 
현재 인터페이스에 전달함

-리액트 DOM 은 브라우저의 일부인 실제 DOM 에 대한 작업을 하기에
무언가를 표시하는 역할은 리액트 DOM 임

-리액트는 props 를 관리함 props 는 컴포넌트에 전달하는 데이터로 
컴포넌트 구성을 가능하게 해주며 부모-자식 컴포넌트간의 통신을 연결해줌

-리액트는 컴포넌트 내부 데이터인 state 를 다룸

-리액트는 컴포넌트 전체의 데이터인 컨텍스트도 다룸

-props,state,context 가 변경되면 사용하는 컴포넌트도 리액트를 통해 변경되며
화면에 새로운것을 표시하는지 확인하며 화면에 무언가 그릴려하면 리액트는
리액트 dom 에게 알려줘서 리액트 dom 이 새로운 화면과 새로운 컴포넌트,
새 출력을 표시할 수 있게 해줌
(상태나 props, 컨텍스트, 컴포넌트에 변경이 발생하면 컴포넌트 함수가 재실행되어
리액트가 이를 재평가함, 이 재평가는 dom 을 다시 렌더링하는것은 아님,
리액트에의해 컴포넌트 함수가 재실행 된다해서 실제 dom 각 부분들이 다시 
렌더링되거나 재평가되는건 아님)

-리액트는 컴포넌트를 다루며 최종적으론 가상 dom 이라는 개념을 사용하며
가상 dom 은 앱이 마지막에 만들어내는 컴포넌트 트리를 결정함,
각 하위 트리를 갖고있는 컴포넌트들은 jsx 코드를 반환하며 가상 dom 은
컴포넌트 트리의 현재 모양과 최종 모양을 정함

-상태가 업데이트되면 업데이트 된 정보는 리액트 dom 으로 전달되어
갱신 전 후 의 상태 차이를 인식해 리액트가 컴포넌트 트리를 통해 구성한
가상 스냅샷이 가상 dom 과 일치하도록 실제 dom 을 조작하는 방법을 알수 있게함

-state,props,context 가 변경되면 재평가되며 리액트는 컴포넌트 함수를 다시 실행함
반면 실제 DOM 은 리액트가 구성한 컴포넌트의 이전 상태와 트리, 현재의 상태간에
차이점을 기반으로 변경이 필요할때만 업데이트됨, 실제 DOM 은 필요한 경우에만 변경됨

-이전상태와 현재 상태를 가상으로 비교하면 간편하고 자원도 적게 듬
(작업이 메모리 안에서만 발생)
실제 DOM 을 사용하면 (브라우저에 직접 렌더링하는것) 은 성능 측면에서
자원이 많이 필요하게 됨, 성능 부하 발생할 수 있음

-변경된 내용이있다면 리액트 DOM 은 실제 DOM 을 업데이트하고 추가된 문장을 넣는다
리액트 DOM 은 전체 DOM 을 재렌더링하지않고 오로지 변경된 내용만을 추가함

-props 는 부모에서 자식 컴포넌트로 향하는 것

-모든 jsx 요소들은 컴포넌트 함수에 대한 함수 호출과 같다

-부모 컴포넌트 함수가 재실행되면 자식 컴포넌트 함수도 재실행된다

React.memo()
-props 가 바뀔때만 재실행 되도록 할 수 있다

-React.memo 에 인자로 들어간 컴포넌트에 어떤 props 가 입력되는지 확인하고 입력되는
모든 props 의 신규 값을 확인한 후에 이를 기존의 props 의 값과 비교하도록 
리액트에게 전달하며 props 의 값이 바뀐 경우에만 컴포넌트를 재실행 및 재평가함,
부모 컴포넌트가 변경되었지만 컴포넌트의 props 값이 바뀌지않았다면 컴포넌트 실행은 건너뜀

-memo 는 함수형 컴포넌트를 최적화 할 수 있다

-모든 컴포넌트에 적용하지 않는건 최적화에는 비용이 따르기때문, 그 비용이란 것은
부모 컴포넌트에서 변경이 발생할때마다 memo 는 랩핑되어있는 컴포넌트로 이동해 기존의
props 값과 새로운 값을 비교하게되며 리액트가 두가지 작업을 할 수 있어야하는데
기존의 props 값을 저장할 공간이 필요하며 비교하는 작업도 해야하기때문에
각각의 작업에대한 개별적인 성능 비용이 필요하게되기에 성능 효율은 어떤 컴포넌트를 
최적화하느냐에따라 달라지게된다(컴포넌트를 재평가하는데 필요한 성능 비용과 
props 를 비교하는 성능 비용을 서로 맞바꾸는것) 컴포넌트의 복잡도에 따라 자식컴포넌트의
숫자에따라 달라지며 자식 컴포넌트가 많거나 컴포넌트 트리가 매우 크다면 memo 는
유용하게 쓰인다

-컴포넌트 트리의 상위에 위치해있다면 전체 컴포넌트 트리에대한 필요없는 리렌더링을 막을수있다
(트리중 상단에있다면 memo 로 랩핑한 컴포넌트의 하위 컴포넌트들에대한 리렌더링을 막을수있음)

-부모 컴포넌트를 항상 재평가된다던지 컴포넌트의 변화가있거나 props 의 값이
변화할수있는 경우라면 memo 는 큰 의미를 갖지 못한다 컴포넌트의 리렌더링이 어떻게든 필요하기때문,
이런 경우 props 값에 추가적인 비교에대한 비용을 아낄순있지만 오버헤드로 발생하는 코스트는
아낄만한 가치가 없다

-useMemo 로 함수를 랩핑할경우 2개의 인자를 필요로 하며 의존성 배열임

-useMemo 로는 정렬을 하는 경우에 업데이트될 경우를 제외하곤 불필요한 정렬을 막아줄 수 도있다



useCallback
-기본적으로 컴포넌트 실행 전반에 걸쳐 함수를 저장할 수 있게 하는 훅

-선택한 함수를 리액트의 내부 저장 공간에 저장해서 함수 객체가 실행될 때마다 이를 재사용할 수 있게 됨

useCallback 로 함수를 첫번째 인자로전달하면 useCallback 은 저장된 함수를 반환해줌
* -App 함수가 다시 실행되면 useCallback 이 리액트의 저장한 함수를 찾아 같은 함수 객체를 재사용함
* -어떤 함수가 절대 변경되선안된다면 useCallback 을 사용해 함수를 저장하면됨
* -두번째 인자는 useCallback 호출에 대한 의존성 배열이며 함수를 감싼 컴포넌트로부터 전달받은 모든것을 사용할 수 있음
* -- state or props or context 를 지정할 수 있음
* ---두 번째 인자를 비워두면 해당 setShowParagraph 배열은 변경되지않을 것이라는것을 명시
const [showParagraph, setShowParagraph] = useState(false);

const toggleShowParagraphBTN = useCallback(() => {
  setShowParagraph(prevParagraph => !prevParagraph)
}, [])
전달한 모든 props 값이 비교가 가능하게끔 전달했기 때문에 React.memo가 역할을 수행할 수 있음
이 toggleParagraphHandler 객체가 useCallback 덕분에 메모리 안에서 항상 같은 객체임을 보증하기 때문




Closure
-클로저는 함수와 함수가 선언된 어휘적 환경의 조합

function init() {
      var name = "Mozilla"; // name은 init에 의해 생성된 지역 변수이다.
      function displayName() { // displayName() 은 내부 함수이며, 클로저다.
        alert(name); // 부모 함수에서 선언된 변수를 사용한다.
      }
      displayName();
    }
    init();
-init()은 지역 변수 name과 함수 displayName()을 생성한다. displayName()은 
init() 안에 정의된 내부 함수이며 init() 함수 본문에서만 사용할 수 있다. 
여기서 주의할 점은 displayName() 내부엔 자신만의 지역 변수가 없다는 점이다. 
그런데 함수 내부에서 외부 함수의 변수에 접근할 수 있기 때문에 displayName() 역시
부모 함수 init()에서 선언된 변수 name에 접근할 수 있다. 만약 displayName()가
자신만의 name변수를 가지고 있었다면, name대신 this.name을 사용했을 것

-클로저는 어떤 데이터(어휘적 환경)와 그 데이터를 조작하는 함수를 연관시켜주기 때문에 유용하다.
이것은 객체가 어떤 데이터와(그 객체의 속성) 하나 혹은 그 이상의 메소드들을 
연관시킨다는 점에서 객체지향 프로그래밍과 분명히 같은 맥락에 있다
const [showParagraph, setShowParagraph] = useState(false);
	const [allowToggle, setAllowToggle] = useState(false)
const toggleShowParagraphBTN = useCallback(() => {
  /*allowToggle 은 useCallback 안에 함수로 지정해놨기에 최신 스냅샷이아닌 이전 함수 생성 시점의 state 의 값을 저장중이다
  * -하지만 의존성 주입으로 allowToggle 을 설정하게되면 최신의 값만을 사용하게 된다 */
  /*ShowParagraph 는 true 일 경우에만 이 함수가 실행되도록한다*/
  if (allowToggle){
  setShowParagraph(prevParagraph => !prevParagraph)
  }
}, [allowToggle])

const allowToggleHandler = () => {
  setAllowToggle(true)
}

useState
-useState 는 초기값에 대해서는 한번만 고려되도록 처리됨
(App 컴포넌트가 최초 실행될때)
-useState가 실행ㄷ괴면 리액트가 관리하는 새로운 상태 변수를 만든다,
리액트는 이 변수가 어느 컴포넌트에 속하지는지 기억하며 기본값을 사용해서
상태값을 초기화한다, 이후 컴포넌트 재평가하는 과정에서 useState 가 호출되면
새로운 상태는 생성되지않음

-DOM 에 컴포넌트가 연결되고 유지되는 동안엔 state 는 최초의 초기화 이후에는 갱신만됨

-state 가 update 되면 react 는 component 를 재평가하고 컴포넌트 함수를 재실행한다


클래스형 컴포넌트 or 함수형 컴포넌트
-클래스는 리액트의 기능이 아니며 모던 js 에 존재하는 기능임

-훅은 클래스 기반 컴포넌트에서는 사용이 불가능함

-클래스형 컴포넌트는 로직을 컴포넌트 내에서 구현하기 때문에 더 복잡한 UI를 갖게 됨,
반면에, 함수형 컴포넌트는 props로 데이터를 받아서 UI에 뿌려주기 때문에 상대적으로 
단순한 형태를 갖게 되며 재사용성이 높다는 장점이 있다.

클래스형 컴포넌트
-class 키워드 필요
-Component로 상속 받음
-render() 메소드 필요
-state, lifeCycle 사용 가능
-this.state 초기값 설정, 변경 가능
-this.props로 데이터 불러옴
-메모리 자원의 많은 사용
-임의 메소드 정의 가능

함수형 컴포넌트
-state, lifeCycle 사용 불가 (Hook으로 해결)
-useState 함수로 state 사용
-props 불러올 필요 없이 바로 호출
-메모리 자원 덜 사용
-컴포넌트 선언이 편리함

-함수형 컴포넌트와 클래스형 컴포넌트를 함께 작업이 가능함
필요하다면 섞어서 사용이 가능하다


오버라이드
-부모 클래스가 정의한 함수를 덮어씌워 다시 정의하여 사용하는 것

-자식이 오버라이드를 한다고 부모 클래스의 기능이 사라지는 것이 아님

-부모 클래스의 메소드를 사용할 수 있어도 자식 클래스에서 변경해야 할 상황이 발생한다면
오버라이드를 통해 자식 클래스에서만 새로운 기능으로 재정의할 수 있음

조건:
-부모 클래스와 자식 클래스 사이에서만 성립됨

-static 메소드는 클래스에 속하는 메소드이기 때문에 상속되지 않고 오버라이드 되지도 않음

- private의 접근제어자를 가진 메소드는 상속 자체가 되지 않아 오버라이드도 성립되지 않음

- interface를 구현하여 오버라이드할 때는 반드시 public 접근 제어자를 사용해야 함

- 오버로드와 달리 리턴 타입, 메소드 명, 매개변수 패턴이 모두 같아야 함

- 부모 클래스의 메소드의 접근 제한자 범위보다 작아질 수 없고 확장은 가능함

- 부모 클래스의 메소드보다 더 많은 예외를 던질 수 없음

- final이 지정된 메소드는 오버라이드할 수 없음

장점:
오버라이드는 메소드 하나로 여러 객체를 다루고 객체마다 다른 기능을 사용할 수 있다는 장점


오버로딩
-오버로딩을 사용한다면 메소드 명이 같아도 전달되는 매개변수의 개수에 따라 정의된 메소드가 호출

-오버로딩은 메소드 이름, 반환 타입과는 상관없이 메소드 이름이 같다면 매개변수의 타입과 개수에 의해 호출되는 메소드가 결정

-생성자 오버로딩은 메소드 오버로딩과 같습니다. 생성자도 하나의 메소드처럼 생각하면 되는데 
객체를 생성하면서 초깃값으로 설정해주는 생성자에도 오버로딩이 가능

조건

- 오버로딩은 메소드 이름이 같아야 함

- 매개변수의 개수 또는 타입이 달라야 합니다. 당연히 매개변수로 전달되는 인자의 순서도 같아야 함

- 매개변수는 같고 반환 타입이 다른 경우는 오버로딩이 성립되지 않음


장점:

- 가독성이 증가

- 하나의 이름만 기억하면 되므로 오류의 가능성을 많이 줄일 수 있음

- 메서드의 이름만 보고 이름이 같으니, 같은 기능이라고 예측할 수 있음

- 메서드 이름을 절약할 수 있음

ex:대표적인 예로 우리가 자주 사용하는 println() 메소드가 있습니다. 우리는 메소드 이름은 
println 하나만 사용하지만 int형을 출력할 때와 String 형을 출력할 때 등 모두 같은 기능으로 출력됨
이는 메소드 이름은 같으나 매개변수로 전달되는 인자 타입이 다르기 때문에 오버로딩을 통한 메소드 호출임
만약 오버로딩없이 printlnInt(), printlnString() 이런 식으로 구현되었다면 사용하는 입장에서 
오류의 가능성이 엄청나게 늘어날 것이고, 메소드 사용에도 굉장한 불편함

-class component 에서 state 를 정의할땐 constructor 을 사용
* -class component 에서 state 는 object 형식임
* -함수형 컴포넌트에서는 여러 상태 조각이있으면 useState 를 여러번 호출할수있다
* --하나의 state object 를 만들어 그룹화 할수있지만 이건 함수형 컴포넌트에서만 가능한 선택사항임
* ---class component 에서는 무조건적으로 컴포넌트를 구성하는 모든 상태를 하나의 객체로 만들어야함

-class component 에서는 한번에 하나의 context 만 연결 할 수 있다

js 에서 super 는 부모클래스 생성자의 참조임, 그리고 js 는 언어적 제약사항으로서 생성자에서 
uper 를 호출하기 전에는 this 를 사용할 수 없음
constructor(props) {
  super(props);
}

toggleUsersHandler() {
  /*새로운 상태를 갖는 객체 대신에 이 갱신 함수를 setState 에 전달합니다 만약 새로운 상태가 이전 상태에 의존한다면 그 역시 이런 방법을 사용*/
  this.setState((curState)=> {
    return {showUsers: curState.showUsers}
  })
}


useEffect === lifeCycle
-모든 컴포넌트는 생명 주기를 가집니다 예를 들어서, DOM에 렌더링되거나 DOM에서 삭제될 때 말이죠, 
하지만 특정 메소드를 통해 생명 주기가 다른 2개의 클래스 컴포넌트를 서로 다른 시점에서 추가할 수 있음

-클래스 컴포넌트에 추가할 수 있는 생명 주기 메소드는 componentDidMount() 메소드
컴포넌트가 마운트되면 호출됨, 컴포넌트가 평가되고 DOM 에 렌더링 될때이며 이건 useEffect 를 사용한것과 같음
모든 effect 함수는 컴포넌트가 처음 마운트 될때 실행되며 의존성 배열이 비어있다면 최초 한번만 실행됨,
effect 를 비어있는 의존성 배열과 함께 추가하면 componentDidMount() 와 같은 역할을 수행함

-다른 생명 주기 메소드는 componentDidUpdate()와 componentWillUnmount()
componentDidUpdate() 는 컴포넌트가 갱신되면 호출됨, state 가 update 되거나 컴포넌트가 재평가,리렌더링되면 그때 호출됨
이것은 useEffect 와 동일함
componentWillUnmount() 는 컴포넌트가 DOM 에서 삭제되기 직전에 호출되며 useEffect() 에 있는 clean up 함수와 같음
clean up func 는 effect func 가 다시 실행되기 직전에 호출되며 항상 컴포넌트가 DOM 으로부터 삭제되기 전에 다시 호출됨


리액트에 의해 state 변화로 인해 컴포넌트가 재평가되게 되면 자동적으로 호출
componentDidUpdate(prevState) {
  /* setState 를 호출하여 갱신되는 filteredUsers 가 바뀌었다면, componentDidUpdate() 메소드는 재실행됩니다만, 이 if 구문은 실행되지 않음
  따라서 상태 갱신이 이루어지지 않으니무한 루프 역시 발생하지 않음
  -함수형 컴포넌트는 의존성 배열을 명시 해주므로 아래와 같이 조건문을 넣어줄 필요가 없다 */
  if(prevState.searchTerm !== this.state.searchTerm){ /*이전 상태와 현재 상태가 달라지면 실행
  this.state({filteredUsers: DUMMY_USERS.filter((user) => user.name.includes(this.state.searchTerm))})
  }
}


/*컴포넌트가 처음 렌더링 될때만 실행
* -HTTP 요청을 보내고 다룰 수 있음*/
componentDidMount() {
  /*SERVER 에서 가져온 유저들 정보 설정*/
  this.state({
    filteredUsers: DUMMY_USERS,
  })
}


오류 경계
class ErrorBoundary extends Component {
constructor(props){
  super(props)
  this.state({
    hasError: false,
  })
}
/*어느 클래스 컴포넌트에도 추가할 수 있으며 컴포넌트에 이를 추가하게 되면 클래스 컴포넌트를 오류 경계로 만들게 됨,이 ‘오류 경계’란 단어는
이런 생명 주기 메소드를 갖는 컴포넌트를 지칭하는 용어임,2개의 함수형 컴포넌트를 편집할 수 없음
-오류 경계를 빌드하려면 클래스 컴포넌트여야 하고 동시에 생명 주기 메소드를 갖는 컴포넌트여야 함
-생명 주기 메소드는 하위 컴포넌트 중 하나가 오류를 만들거나 전달할 때 발동
-오류 경계는 class component 에서만 사용가능하며 아직 함수형 component 에서는 사용 불가*/
componentDidCatch(error, errorInfo) {
  console.log('componentDidCatch Error ::: ', error) /*분석을 위해서 서버로 전송작업*/
  this.setState({
    hasError: true,
  })
}
render(){
  if (this.state.hasError){
    return <p>무언가 잘못되었음 에러 발생</p>
  }
  return (
      this.props.children /*오류 경계 컴포넌트를 보호하려고하는 컴포넌트로 둘러싸아야하기때문,*/
  )
}
}
export default ErrorBoundary ;


리액트가 dataBase 와 소통하는 방법
-db 와 js code 가 직접 통신하면 절대 안된다, App 으로 직접 데이터를 가져오거나 
저장하고 연결을 하는 것은 외부 환경에서는 절대 해서는 안되는 일중 하나임
(code 를 통해 db 의 인증 정보를 노출시키는 행위이기 때문)
(브라우저에서 실행되는 js code 는 웹 사이트의 사용자들도 접근하고 읽을 수 있기때문)

-데이터베이스와 통신하는 백엔드 어플리케이션은 사용자가 이 백엔드 코드를 확인할 수 없기 때문에
데이터베이스의 인증 정보를 안전하게 저장할 수 있으며  다른 서버에 있으므로
웹사이트 사용자는 이 코드를 절대 볼 수 없다

-리액트 앱은 일반적으로 해당 백엔드 서버, 또는 백엔드 API라고 불리는 서로 다른 URL로의 요청을 전송하는
서버와 통신하게 됨
-인증 정보는 백엔드 앱에 저장되었고 백엔드 앱과의 통신은 보안에 관련된 세부 사항이 필요 없으므로
데이터베이스와 안전하게 통신을 주고 받을 수 있음


Axios
js 솔루션을 통해 워하는 어떤 http 요청을 전달할수있는데 패키지중 axios 가있으며 github 를 방문해 받을 수 있음
(HTTP 요청 전송을하고 이에대한 반응을 간단하게 할수있는 패키지임,라이브러리가없어도 사용가능)
-최근엔 JS 내에 HTTP 요청을 전송하는 내장메커니즘 Fetch api 가있으며 브라우저 내장형이고 
데이터를 불러오고 이름과는 다르게 데이터 전송도 가능하며 api 를 통해 http 요청을 전송하고
응답을 처리할 수 있음

-요청 전송에 성공한다면 오류 상태 코드에 맞는 오류를 만들어서 전달함


JSON
-데이터 교환에 사용하는 간단하지만 유명한 형식

-key 와 value 로 나뉘어있음
-js 로 변환 작업이 필요하지만 파일에서 js 객체로의 변환이 매우 쉬움
-프론트 엔드와 백엔드간에 데이터 교환에 사용되는 유형

리액트 앱 내에서 백엔드로 HTTP 요청을 전송하는 방법
const App = () => {
const [movies, setMovies] = useState([])

/*이 함수가 호출될때마다 매번 http 요청이 전송됨*/
const fetchMoviesHandler = () => {

  /*fetch func 는 browser 가 사용할수있게해준 func
  * -첫번째 인자는 요청을 전송하려는 URL, 두 번째인자는 다양한 선택사항 지정 가능(object,request method change 기타등등)
  * -fetch func 는 promise 객체를 반환하며 발생할수있는 오류 및 호출에 대한 응답에 반응할수있게해줌
  * -http request 전송은 async 작업 이며 밀리초 및 몇초가 걸리는 작업이고 실패할 가능성도있음
  * --따라서 코드 다음줄로 작업을 계속하고 코드의 결과를 바로 사용할수없지만 코드 실행의 결과는 미래의 어느 시점에서 확인가능(js 에 Promise 객체가있는 이유)
  * -then 을 추가해주면 최종함수는 응답을 받을때 호출됨
  * -그 뒤에 .catch() 문을 추가하면 잠재적 오류 처리 가능*/
  fetch('https://swapi.dev/api/films').then(response => {
    /*응답을 받은뒤 여기서 응답을 사용할수있다
    * -then 에 들어온 response 는 객체이며 요청 응답에 대한 데이터를 가지고있음(응답 헤더를 읽거나 상태 코드를 얻을 수도있다)
    * -response.ok 는 모든것이 정상이면 true , 아니면 false 반환
    * -response.json() 은 response 의 본문을 code 에서 사용 할수있는 js object 로 자동 변환해줌*/
    return response.json()
  /*}).then(data => {
    data.results /!*API 에있는 result 배열에 접근*!/*/
  }).then((data)=>{
    /*넘겨받은 배열의 모든 객체를 새로운 객체로 변환함, 새로운 객체는 새로운 객체로 채워진 배열임*/
    const transformedMovies = data.results.map(movieData => {
      return {
        id: movieData.episode_id,
        title: movieData.title,
        openingText: movieData.opening_crawl,
        releaseDate: movieData.releaseDate,
      }
    })
    setMovies(transformedMovies) /*API 의 results 의 배열이 movies 에대한 새로운 state 가 됨*/
    /*setMovies(data.results) /!*API 의 results 의 배열이 movies 에대한 새로운 state 가 됨*!/*/
  })
}

return (
    <React.Fragment>
      <section>
        <button onClick={fetchMoviesHandler}>Fetch Movies</button>
      </section>
      <section>
        <MoviesList movies={movies}/>
      </section>
    </React.Fragment>
);
}
export default App;

위 코드를 async 와 await 을 사용한 비동기화 코드로 변환
function App() {
	const [movies, setMovies] = useState([])

	/*이 함수가 호출될때마다 매번 http 요청이 전송됨*/
	async function fetchMoviesHandler() {

		/*fetch func 는 browser 가 사용할수있게해준 func
		* -첫번째 인자는 요청을 전송하려는 URL, 두 번째인자는 다양한 선택사항 지정 가능(object,request method change 기타등등)
		* -fetch func 는 promise 객체를 반환하며 발생할수있는 오류 및 호출에 대한 응답에 반응할수있게해줌
		* -http request 전송은 async 작업 이며 밀리초 및 몇초가 걸리는 작업이고 실패할 가능성도있음
		* --따라서 코드 다음줄로 작업을 계속하고 코드의 결과를 바로 사용할수없지만 코드 실행의 결과는 미래의 어느 시점에서 확인가능(js 에 Promise 객체가있는 이유)
		* -then 을 추가해주면 최종함수는 응답을 받을때 호출됨
		* -그 뒤에 .catch() 문을 추가하면 잠재적 오류 처리 가능*/
		const response = await fetch('https://swapi.dev/api/films');
		const data = await response.json();
		/*.then(response => {
			/!*응답을 받은뒤 여기서 응답을 사용할수있다
			* -then 에 들어온 response 는 객체이며 요청 응답에 대한 데이터를 가지고있음(응답 헤더를 읽거나 상태 코드를 얻을 수도있다)
			* -response.ok 는 모든것이 정상이면 true , 아니면 false 반환
			* -response.json() 은 response 의 본문을 code 에서 사용 할수있는 js object 로 자동 변환해줌*!/
			return response.json()
			/!*}).then(data => {
				data.results /!*API 에있는 result 배열에 접근*!/!*!/
		})
		.then((data) => {*/
		/*넘겨받은 배열의 모든 객체를 새로운 객체로 변환함, 새로운 객체는 새로운 객체로 채워진 배열임*/
		const transformedMovies = data.results.map(movieData => {
			return {
				id: movieData.episode_id,
				title: movieData.title,
				openingText: movieData.opening_crawl,
				releaseDate: movieData.releaseDate,
			}
		})
		setMovies(transformedMovies) /*API 의 results 의 배열이 movies 에대한 새로운 state 가 됨*/
		/*setMovies(data.results) /!*API 의 results 의 배열이 movies 에대한 새로운 state 가 됨*!/*/
	}



-fetch 는 Promise object 를 반환하므로 then 구문을 호출한것

-async 와 await 문법은 함수 앞에 async 예약어를 추가하고 프로미스를 반환하는 작업 앞에
await 예약어를 사용함, 이 것은 단순히 코드 변환이며 백그라운드에서는 then 블록을 사용한 것과
같은 일을 합니다

-오류 발생시 then 을 사용하면 cache() 추가하여 오류 확인 가능
fetch('https://swapi.dev/api/films').cache()


데이터를 즉시 fetch하려면useEffect 훅이 있음 이게 가능한 이유는 HTTP 요청 전송은 일종의 사이드 이펙트로
컴포넌트의 상태를 바꿔버리기 때문, 그리고 이런 사이드 이펙트는 useEffect 에 들어가야함,
그 함수를 메인 컴포넌트의 함수 일부분으로 호출하지만 않는다면 함수로 집어넣어도됨, 
만약 그렇게 하면 함수 호출이 되는 순간 상태의 갱신이 발생하고 컴포넌트 함수가 재 렌더링, 재평가되면서
함수가 다시 호출되는 무한 루프가 발생하여 문제가 되기 때문 이를 피하기 위해 useEffect를 사용함

-useEffect 는 렌더링되는 주기안에서 사용되어야하는 코드가있을때 유용함

-const fetchMoviesHandler = useCallback(async() =>{ /*useCallback 사용시, async 예약어 삭제 시 화살표함수 앞에 추가해주자*/

-useEffect 로 인한 무한 루프 발생 시 useCallback 으로 useEffect 에 사용되는 함수를 감싸주며
의존성 배열을 추가해주자, 외부 의존성이 없다면 빈 배열로 놔두면됨

-fetch 는 기본적으로 GET 요청을 보냄

-Firebase 에서는 POST 요청을 보내면 리소스를 만들어줌

-method: 'POST',
    /*body 는 js 의 객체가아닌 JSON 데이터를 필요로함
    * -stringify  는 객체나 배열을 JSON 형식으로 바꿔줌*/
body: JSON.stringify(movie),

-/*헤더가 없어도 요청은 정상적으로 처리해주지만, 요청을 받는 대다수 API 들은 헤더를 필요로함, 헤더를 통해 어떤 컨텐츠가 전달되는지 알수있기때문*/
    headers: {
      'Content-Type': 'application/json'
    }


js 의 속성에 대한 동적 접근 방법
function App() {
const [movies, setMovies] = useState([]);
const [isLoading, setIsLoading] = useState(false);
const [error, setError] = useState(null);

const fetchMoviesHandler = useCallback(async () => {
  setIsLoading(true);
  setError(null);
  try {
    /*동적 REST API 로 서로 다른 구획으로 db 의 서로 다른 노드들에 data 를 저장할수있게해주는 설정
    * -.json 을 붙인건 Firebase 필수 요구사항*/
    const response = await fetch('https://react-http-d5583-default-rtdb.firebaseio.com/movies.json');
    if (!response.ok) {
      throw new Error('데이터를 가져오는데 실패하였습니다.!');
    }

    const data = await response.json();
    console.log('fetchMoviesHandler data :::', data)
/*for roof 통해 data 안에 모든 key 확인*/
    const loadedMovies = [];
    for (const key in data) {
      /*loadedMovies 에 전달받은 data 의 key 와 value 들의 조합에대해 새로운 객체 푸쉬
      * -아래와같이하면 response 로 받은 중첩 객체를 타고 들어가게됨
      * --js 의 속성에 대한 동적 접근 방법*/
      loadedMovies.push({
        id: key,
        title: data[key].title,
        opening: data[key].openingText,
        releaseDate: data[key].releaseDate,
      })
    }
setMovies(loadedMovies);
  } catch (error) {
    setError(error.message);
  }
  setIsLoading(false);
}, []);


커스텀 훅
-리액트 훅은 리액트 컴포넌트 함수, 또는 커스텀 훅에서만 사용가능하다

-정규 함수이며 내장 훅이나 useState 와 같지만
state 를 설정 할수있는 로직을 포함한 함수이다
--커스텀 훅을 만들어서, 재사용 가능한 함수에 상태를 설정하는 로직을 
아웃소싱할 수 있음,정규 함수와는 다르게, 커스텀 훅은 다른 커스텀 훅을
포함한 다른 리액트 훅을 사용할 수 있음(useEffect 등에 접근가능)

ex.code useCounter custom hook
/*커스텀 훅은 무조건 use 로 시작해야함(룰)
* -리액트에게 이 함수가 커스텀 훅임을 알려주며 리액트가 해당 함수를 훅의 규칙에
 따라 사용하겠다고 보장해줌(내장 훅과 같은 방식으로 쓰겠다는)*/
const useCounter = () => {
/*ForwardCounter.js 에서 가져온 code*/
const [counter, setCounter] = useState(0);

useEffect(() => {
  /*앞으로 1초 마다 이전 카운터보다 + 1 씩 추가*/
  const interval = setInterval(() => {
    setCounter((prevCounter) => prevCounter + 1);
  }, 1000);

  return () => clearInterval(interval);
}, []);

/*커스텀 훅을 사용하는 컴포넌트에서, counter 의 상태를 사용 가능하게 하려면, 
간단히 이를 반환만 하면 됨
-커스텀 훅에서는 필요한 무엇이든간에 반환이 가능함,배열도 가능하고, 객체나 숫자 등*/
return counter;
};
export default useCounter ;

업그레이드된 ForwardCounter.js 와 BackwardCounter 동시 사용 가능 커스텀 훅
/*커스텀 훅은 무조건 use 로 시작해야함(룰)
* -리액트에게 이 함수가 커스텀 훅임을 알려주며 리액트가 해당 함수를 훅의 규칙에 
따라 사용하겠다고 보장해줌(내장 훅과 같은 방식으로 쓰겠다는)*/
/*const useCounter = (counterUpdateFn) => {/!*counter 갱신 fn 을 매개변수로 
넣어주며 이 갱신함수를 실행해주면됨*!/*/
const useCounter = (forwards = true) => { /*전달할 값을 true 로 지정하여 
setCounter 로 더할지 뺄지 조건문 넣어줘서 ForwardCounter,BackwardCounter 로직 사용*/
/*ForwardCounter.js 에서 가져온 code*/
const [counter, setCounter] = useState(0);

useEffect(() => {
  /*앞으로 1초 마다 이전 카운터보다 + 1 씩 추가*/
  const interval = setInterval(() => {
    if (forwards) {
    setCounter((prevCounter) => prevCounter + 1);
    } else{
    setCounter((prevCounter)=> prevCounter - 1)	;
    }
    /*setCounter(counterUpdateFn());/!*여기에서 받게 될 인자는 실행 가능한
    함수이며 이는 이전의 카운터를 받고 새로운 카운터를 받아들임*!/*/
  }, 1000);

  return () => clearInterval(interval);
}, [forwards]);/*매개변수로서 받게 되는 값이기 때문에 이를 의존성으로 추가해야 함*/

/*커스텀 훅을 사용하는 컴포넌트에서, counter 의 상태를 사용 가능하게 하려면,
 간단히 이를 반환만 하면 됨
* -의존성 변경이 발생할 때마다 useEffect 함수가 재실행하게 함*/
return counter;
};

css module 화
-컴포넌트 스타일 클래스 이름이 중첩되는 현상을 방지해 주는 기술, CSS 
Module을 이용하면 클래스명이 충돌하는 단점을 극복할 수 있음, CSS Module은 
컴포넌트 단위로 스타일을 적용할 때 유용


bind()
-bind 는 Fn 를 사전에 구성할수있게해주며 호출 즉시 함수가 실행되지 않음

-bind에 보내는 첫 번째 인자는 실행이 예정된 함수에서 this 예약어를 
사용하게 하는 것 (사용하지 않을땐 null 입력)

-두번째 인자는 호출 예정인 함수가 받는 첫 번째 인자가 됨


input form valid test
-입력 값에 대한 유효성을 검증하고 필요한 경우 사용자에게 error message popup

-사용자 입력을 가져오는 방법은 두가지 방법
--1) 모든 키 입력마다 확인하며 키 입력 값들을 state 변수에 저장
--2) ref 를 이용해 사용자가 입력 값을 모두 입력했을 때 입력 값을 가져옴
(input 을 ref 로 설정함으로써 필요할 때 input 요소로부터 값을 읽음)
-둘중에 어떤 것을 사용할지 어떻게 결정할까?
이는 입력된 값으로 하고자 하는 일에 따라 다름, 만일 이 값이 폼이 
제출되었을 때 한번만 필요하다면 모든 키 입력마다 state 값을 업데이트 하기엔
조금 지나치고 불필요하므로 ref가 낫다, 반면 즉각적인 유효성 검증을 위해
키 입력마다 입력 값이 필요하다면 ref로는 이 작업이 불가하므로 state 를 
사용하는 것이 좋다, ref보다 state 를 사용하는 것이 좋은 또 다른 경우는
입력된 값을 초기화 하고 싶은 경우임, 이 formSubmissionHandler 마지막에
setEnteredName(‘’)으로 빈 문자열로 설정해준 뒤에 여기 아래로 내려가서
value={enteredValue}로 input의 값을 연결해주면 초기화 시켜줄 수 있음
이렇게 enteredName이 input의 value prop과 연결되어서 enteredName을 
업데이트 된 뒤에는 이 부분에 반영됩니다 이는 상태를 사용하면 잘 작동하고
ref로 구현하는 것도 불가능하진 않지만 이렇게 깔끔하진 않음 ref로도 할 수는 있다 
nameInputRef.current.value =’’로 ref에 저장된 input 요소에 접근해 빈 문자열로
 만들 수 있는데 바람직한 방법은 아님, 이 부분을 주석처리하고 실행하면 
 보시다시피 작동은 하지만 바람직하진 않음 이는 DOM을 직접 조작하는 
것으로 바닐라 자바스크립트 코드를 이용해 DOM에 접근해 무언가 변경하는 
것인데 보통 지양해야 하는 방법임, 리액트로만 DOM을 조작해야 함

-event.preventDefault()
--브라우저에서 작동하는 js 를 다루고있기 때문에 기본적으로 브라우저는 
이 폼 안에 있는 버튼을 통해서 폼이 제출되면
웹사이트를 제공하는 서버로 HTTP 요청을 보내게 되며, 이 과정은 자동적으로 
일어나며 브라우저가 자동적으로
웹사이트를 제공하는 서버로 HTTP 요청을 보냅니다 이 과정에서 문제는 실제로 
요청을 처리할 서버가 없고
HTML과 자바스크립트만 전송하는 정적 서버만 있다는 점에따라 따라서 이 요청이 
보내지지 않도록 해야합니다
따라서 이 event 객체는 onSubmit 속성에있는 함수와 바로 연결이 되어있는데
 onSubmit으로 연결된 이 event 객체에서
브라우저의 기본 행동인 HTTP 요청을 보내지않고 아무것도 하지 않도록 
명령 함(event.preventDefault()) 이것이 필요한 이유는
HTTP 요청이 보내진다면 결국 페이지가 새로고침될텐데 이 경우에는 리액트 앱들이
 전부 재시작되면서 모든 상태가
없어지게되고 원하는 대로 작동하지 않게 되기 때문, 따라서 이 부분이 매우 중요함
따라서 그 다음에 페이지가 새로고침 되지 않아서 앱이 재시작되지 않도록 하는것

바닐라 자바스크립트 
-바닐라 자바스크립트(Vanila Javascript)란, 라이브러리나 프레임워크를 사용하지 
않는 순수한 형태의 자바스크립트를 의미
-바닐라 자바스크립트는 프로그래밍 문제를 해결하기 위해 어떤 도우미 라이브러리나 
프레임워크를 사용하는 것보다 코어 API나 유틸리티를 사용하여 코딩하는 방식을 의미
-오늘날 대부분의 자바스크립트 프로그램은 제이쿼리, 리액트, 앵귤러 등 다양한  
프레임워크 및 라이브러리에 의해 구현된 기능을 사용하고 있는데, 사실 이러한 
라이브러리의 기능들은 모두 자바스크립트 언어를 기반으로 구현이 되어 있기에,
 바닐라 자바스크립트 만으로도 구현이 가능한 것들임


blur
-input 요소가 포커스를 잃었다는 의미

================================================================
&& 논리 연산자 잘 생각해보기
const [enteredName, setEnteredName] = useState('')
/*enteredName 이 빈 문자열이아니라면 true*/
/*.trim()을 이용해 입력 값의 처음부터 끝 사이에 있는 공백문자를 없앨 수 있음*/
const enteredNameIsValid = enteredName.trim() !== ''
/*바로 위에 코드 에서 빈 문자열이라면 enteredNmaIsValid 에는 false,
!enteredNameIsValid 는 true 로되고 enteredNameTouched 도 true 라면 
nameInputIsInValid 는 true 가되며 nameInputIsInvalid 는 true*/
const nameInputIsInvalid = !enteredNameIsValid && enteredNameTouched
 

-입력이 많을때는 전체 양식이 유효하도록하면 좋다
--ex 10 개중 1 개라도 유효하지않다면 전체가 유효하지않도록
/*formIsValid state 를 지우고 아래와 같이 하면 useEffect 가 필요없어지며 
코드 간결화, enteredNameIsValid 가 true 일경우 form 전체 유효성을 true 설정*/
let formIsValid = false;
if (enteredNameIsValid) {
    formIsValid = true
}


-jsx 에서 false, undefined, null 은 tag 없음을 의미함

-async 함수에서는 항상 promise를 반환하며 promise 대신 오류를 가져오는 
경우 그 오류로 인해 해당 promise가 거부하게되기에 따라서 try/catch를 
사용해서 그것을 래핑 할 수 없음 단, await를 적용하여 useEffect 함수를
async 함수로 전환하면 가능하지만 effect 함수 내에서 promise 를 반환해야
해서 사용할수 없을땐 catch() 메소드를 사용하여 promise 를 반환하게할수있음


================================================================
리덕스
-크로스 컴포넌트 또는 앱 와이드 상태를 위한 상태 관리 시스템

-로컬 상태:데이터가 변경되어서 하나의 컴포넌트에 속하는 UI에 영향을 미치는 상태

-앱 와이드: 다수의 컴포넌트가 아니라 애플리케이션의 모든 컴포넌트에 영향을 
미치는 상태도 있는데
그런 경우를 우리는 앱 와이드 상태라고 부를 수 있음,예를 하나 들자면 사용자 인증

-크로스컴포넌트:모달안에 버튼을 통해 뭔가 표시하고 감추면 다수의 컴포넌트가 협력하는것이며 
useState or useReducer 를 이용하는데 이럴땐 props 를 주변에 넣어 props 체인을 구축한상태

-리액트 컨텍스트:리액트의 내장 기능이며, 크로스 컴포넌트 상태나 앱 와이드 상태를
쉽게 관리하도록 해줌, 그렇게 크로스 컴포넌트와 앱 와이드 상태 관리를 단순화 할수있음
--단점:컨텍스트를 사용하면 설정이 아주 복잡해질 수 있고 리액트 컨텍스트를 이용한 상태 관리가
상당히 복잡해질 수 있다는 점 (복잡한 경우 여러개의 컨텍스트프로바이더를 중첩사용)
---단점02:성능에대한 문제(데이터가 자주 변경되면 성능에 좋지않음)

-리덕스는 컨텍스트와같이 크로스 컴포넌트 상태나 앱 와이드 상태를 관리하도록 
도와줌,리덕스는 컨텍스트의 대안

-리덕스로 작업할때는 절대 기존의 state 를 변형해서는 안되며 대신 새로운
state 객체를 반환하여 재정의 하면된다

-식별자는 절대적으로 오타를 내면 안되기때문에 보통 
export const 상수명 = 'type 명' 으로 보내고 사용하는쪽에 import 하여사용

-리덕스는 중앙 저장소를 갖게되며 데이터를 저장해서 컴포넌트 안에서 사용가능
--컴포넌트는 중앙저장소를 구독하게되며 데이터가 변경될때마다 저장소가 
컴포넌트에 알려주게됨

-컴포넌트는 저장소에 있는 데이터를 직접 조작하지 않음,대신 리듀서 
개념을 이용(리듀서는 변형을 담당하여,useReducer hook 과는 다름)
--리듀서 함수는 입력을 받아 입력을 변환하고 줄이는 함수임
---예를 들면 숫자로 된 리스트를 그 숫자들의 합으로 줄일 수 있음
----리듀서 함수는 입력을 변환해서 새로운 출력, 새로운 결과를 뱉어냄
-----useReducer는 훅이 사용하고 리듀서 함수는 리덕스도 사용함,리듀서 함수가
 있고 그게 저장소 데이터의 업데이트를 담당함, 그리고 그 데이터를 
구독하는 컴포넌트가 있음

컴포넌트와 리듀서 함수 연결
-액션이 있고 컴포넌트가 액션을 발송하면 컴포넌트가 어떤 액션을 트리거한다고 
말할 수도 있으며 액션은 사실 단순한 자바스크립트 객체이고
그게 리듀서가 수행해야 할 작업을 설명하게 됨,그래서 리덕스는 그 액션을 리듀서로 
전달하고 원하는 작업에 대한 설명을 읽게 되며 리덕스가 그걸 직접 하지는 
않지만 액션들을 리듀서로 전달해서 그 액션이 원하는 걸 리듀서가 하게 
됨, 그리고 나서 리듀서는 새로운 상태를 뱉어내고 그게 실제로 그 중앙 데이터 
저장소의 기존 상태를 대체하게 됨,데이터 저장소의 상태가 업데이트되면
구독 중인 컴포넌트가 알림을 받게 되고 컴포넌트는 UI를 업데이트할 수 있게 
되는 작동방식임

-redux 사용시 npm install redux, npm install redux react-redux

-임포트한 리덕스 객체를 이용해서 그 저장소를 만들 수 있음,그리고 그 객체에 
createStore()를 호출할 수 있음
const redux = require('redux')

-저장소는 데이터를 관리해야 하며 관리하는 데이터는 결국 리듀서 함수에 의해 
결정됨, 리듀서 함수가 새로운 상태 스냅샷을 생성할 것이며 리듀서는 액션이 
도착할 때마다 새로운 상태 스냅샷을 뱉어내야 함

-리듀서 함수는 표준 자바스크립트 함수지만 리덕스 라이브러리에 의해 호출될 
것이며, 항상 2개의 입력, 즉 2개의 파라미터를 받을 것임 바로 기존의 상태와
발송된 액션임,리듀서 함수는 어떤 출력을 리턴해야만 함,항상 새로운 상태 
객체를 리턴해야하며 리듀서 함수는 순수한 함수가 되어야 함, 그건 동일한 
입력, 즉 동일한 입력 값을 넣으면 항상 정확히 같은 출력이 산출되어야
한다는 것,그 함수 안에서는 어떠한 부수적인 효과도 없어야 함,예를 들면 HTTP 
요청을 전송한다거나 뭔가를 로컬 저장소에 기록한다거나 로컬 저장소에서 
뭔가를 가져오지 말아야 함,리듀서는 리덕스가 제공하는 입력을 취하고 예상된 
출력물인 새로운 상태 객체를 생성하는 순수한 함수가 되어야 함

-리덕스 개념 정리 code
const redux = require('redux')
/*현재의 state 와 action 을 받게될 리듀서 함수*/
const counterReducer = (state = {counter: 0}, action) => {
if (action.type === 'increment') {
  return {
    counter: state.counter + 1,
  };
}
if (action.type === 'decrement'){
  return {
    counter: state.counter - 1,
  }
}
return state;/*다른 action 이라면 변하지 않은 state return*/
}
/*리덕스 라이브러리에서 온것이며 저장소 생성함
* -counterReducer 가 store 의 저장소를 변경할 것임을 명시*/
const store = redux.createStore(counterReducer)
console.log(store.getState())
/*reducer 가 저장소 구독*/
const counterSubscriber = () => {
/*getState 는 createStore 로 생성된 저장소에서 사용할 수 있는 method
* -getState 는 업데이트 된 후 최신 상태 스냅샷을 제공할 것임
* -구독 함수는 state 가 update 될때마다 trigger 되면 getState 를 통해 
최신 상태 스냅샷을 얻음*/
const latestStore = store.getState()
console.log(latestStore)
}
/*subscribe 를 호출해서 리덕스가 구독함수를 인식하고 state 가 update
 될때마다함수를 실행하도록함함
* -subscribe 메소드는 counterSubscriber 함수를 취함
* -리덕스는 데이터와 저장소가 변경될때마다 counterSubscriber 함수를 
실행하게해줌*/
store.subscribe(counterSubscriber)
/*증가 action 발송*/
store.dispatch({
type: 'increment', /*type 은 고유한 문자열이여야함*/
})
/*감소 action 발송*/
store.dispatch({
type: 'decrement',
})

-리덕스 스토어를 리액트 앱에 제공하기위해선 index.js 에서 Provider import
import {Provider} from  'react-redux'
import './index.css';
import App from './App';
import store from './store/index'
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<Provider store={store}><App /></Provider>);
-리액트 리덕스 제공자에 리덕스 스토어의 값 store 설정, 그럼 제공자의 
자식 컴포넌트는 제공자의 스토어에 데이터를 가져올 수 있다

-useSelector : 자동으로 state 의 일부를 선택하게해줌, class component 
에서는 connect 를 사용
--useSelector 를 사용하면 자동으로 subscription 을 컴포넌트를 위해서 
리덕스 스토어에 설정함, 따라서 컴포넌트가 업데이트되며 자동으로 가장 
리덕스 스토어에서 데이터가 바뀔 때마다 최신의 카운터를 받음, 자동으로 
리덕스 스토어가 바뀐다면 컴포넌트 함수가 다시 실행됨, 항상 최신의 카운터를 
가지게 됨

-node.js 를 사용하면 브라우저 밖에서 js 를 실행 할 수 있따
(npm install 로 이미 설치되어있다고보면됨)


-eslint : $ npm i -D eslint-plugin-import eslint-plugin-react
-prettier : $ npm install --save-dev --save-exact prettier 

================================================================
리덕스 툴킷
-리덕스 툴킷 사용 : npm install @reduxjs/toolkit
(리덕스가 만약 설치되어있다면 리덕스 툴킷안에 모든기능있기에 기존리덕스삭제)

-Redux toolkit 과 createSlice 같은 함수를 사용하면 기존 상태를 바꿀 수 
없음, 왜냐하면 Redux toolkit 은 내부적으로 immer 라는 다른 패키지를 
사용하는데 이런 코드를 감지하고 자동으로 원래 있는 상태를 복제함, 그리고 
새로운 상태 객체를 생성하고 모든 상태를 변경할 수 없게 유지하고, 변경한 
상태는 변하지 않도록 오버라이드함,직접 코드를 복사할 필요도 없고 더 이상 
불변성을 신경 쓸 필요도 없어짐

-configureStore : createStore처럼 store를 만들며 다른 점은 여러 개의 
리듀서를 하나의 리듀서로 쉽게 합칠 수 있다

-createSlice 는 서로 다른 리듀서에 해당하는 고유 액션 식별자를 자동으로 
생성하며 액션 식별자 값을 얻으려면 counterSlice.actions를 사용하면 됨

-slice 가 여러개더라도 리덕스 스토어는 하나밖에 없으며 한번만
configureStore 를 호출해야한다, 스토어 또한 루트 리듀서 하나만가지고있음


const store = configureStore({
  /*reducers 가 아닌 reducer, 이유는 createStore 와 configureStore
   둘 중에서 무엇을 사용하든,
  리덕스에는 전역 상태를 담당하는 단 하나의주요 리듀서 함수만 있어야 해서
  * -모든 리듀서 메서드를 갖추고있는 counterSlice.reducer 는 전역 state 를
   담당하는 주요 리듀서로 사용가능
  * --만약 규모가 큰 앱에 slice 가 여러개라면 리듀서 key value 대신 객체를 
  설정해서 그 객체 안에 원하는 대로 속성 이름을 정하며
  * ---key value 를 설정해서 프로퍼티들의 값이 또다른 리듀서 함수가 됨, 
  결국 리듀서 맵을 생성하는 것이며 맵은 주요 리듀서의 값이되고
  * ----보이진 않지만 configureStore 의 모든 리듀서를 하나의 큰 리듀서로 
  병합함
  */
  reducer: counterSlice.reducer,
});
/*createSlice 함수의 리듀서 영역에 있는 메서드 이름과 매칭
* -actions 의 객체에서 이런 key 에 접근할 수 있으며 그러면 리듀서 메서드에
 접근할 필요가 없어짐, 대신에 Redux toolkit 에 의해
* --자동으로 생성된 메서드가 생기고 그 메서드가 호출되면 액션 객체가 생성될
 것이며 이런 메스드는 액션 생성자라고 불림
* ---액션 객체를 생성해주며 이런 객체는 이미 액션마다 다른 고유 식별자와 
함께 type 프로퍼티를 가지고 있음, 안 보이게 뒤에서 자동으로 생성됨
그래서 액션 식별자에 대해 신경 쓸 필요 없어짐 직접 액션 객체를 생성할 필요가
 없음 단지 createSlice 의 actions key 및 객체를 사용하면 됨
* 액션 생성자 매서드를 실행해서 리듀서 메서드와 이름이 같으면 액션을 
전달하며 그러면 최종적으로 서로 다른 매서드를 작동키는 원리*/
export const counterActions = counterSlice.actions
export default store;


 /* -state.counter.counter 의 앞 counter 는 리액트 리덕스에게 slice 
 에 접근한다는 걸 알려주기 위함이고
   * --slice 의 리듀서가 만든 state 를 말함, 그리고 그 상태 slice 에서
    가지고 있는 프로퍼티 이름이 counter
   * --- 만약에 counter 가 아닌 다른 이름이었다면, 가령 value 라면, 
   Counter 컴포넌트에서 state.counter.value 가 됨*/
  const counter = useSelector(state => state.counter.counter);

================================================================
동기 비동기 차이
-비동기는 동시에 일어나지 않는다를 의미합니다. 요청과 결과가 동시에 
일어나지 않을거라는 약속입니다. 
-동기는 말 그대로 동시에 일어난다는 뜻입니다. 요청과 그 결과가 동시에 
일어난다는 약속인데요. 바로 요청을 하면 시간이 얼마가 걸리던지 요청한 
자리에서 결과가 주어져야 합니다.
요청과 결과가 한 자리에서 동시에 일어남
A노드와 B노드 사이의 작업 처리 단위(transaction)를 동시에 맞추겠다
요청한 그 자리에서 결과가 주어지지 않음
노드 사이의 작업 처리 단위를 동시에 맞추지 않아도 된다.
-동기와 비동기는 상황에 따라서 각각의 장단점이 있습니다. 
 동기방식은 설계가 매우 간단하고 직관적이지만 결과가 주어질 때까지 
아무것도 못하고 대기해야 하는 단점이 있고, 
 비동기방식은 동기보다 복잡하지만 결과가 주어지는데 시간이 걸리더라도 그 
시간 동안 다른 작업을 할 수 있으므로 자원을 효율적으로 사용할 수 있는 
장점이 있습니다.
-동기는 추구하는 같은 행위(목적)가 동시에 이루어지며, 비동기는 추구하는 
행위(목적)가 다를 수도 있고, 동시에 이루어지지도 않습니다
비동기 방식 예제를 통해서 블록과 논블록의 차이를 간략하게 설명하자면, 
학생이 시험지를 선생에게 건넨 후 가만히 앉아 채점이 끝나서 시험지를 
돌려받기만을 기다린다면 학생은 블록 상태입니다. 하지만 학생이 시험지를 
건넨 후 선생에게 채점이 완료되었다는 전송을 받기 전까지 다른 과목을 
공부한다거나 게임을 한다거나 다른 일을 하게 되면 학생의 상태는 논블록 
상태라고 합니다.
출처: https://private.tistory.com/24 [오토봇팩토리:티스토리]
================================================================

-/*스토어 제공하여 컴포넌트 내에서 리덕스 활용 가능케 함*/
root.render(<Provider store={store}><App /></Provider>);

-/*기존 배열에 들어있지 않은 item 일 경우
       * -redux toolkit 이아닌 redux 만 사용할 경우 push 는 기존 state 의
        기존 배열을 조작하기에 사용하면안됨
       * --redux toolkit 에는 내부적으로 immer 가 기존 state 를 조작하지
        않도록 불변성 유지되기에 문제되지않음*/


리덕스의 부수효과 및 비동식 코드

-리듀서는 순수함수이며 부수효과도 없으며 동기식이어야한다

-리듀서에서 fetch 를 사용해서 백엔드로 요청을 보낼수 없다

-리듀서에서 부수효과 및 동기 or 비동기는 수행면안된다

put 과 post 의 차이 

-새 데이터가 데이터 목록에 추가되지 않고 기존의 데이터를 오버라이드 함
-put 요청을 보낼때 장바구니를 수신 데이터로 오버라이드함

================================================================
멱등성
-동일한 요청을 한 번 보내는 것과 여러 번 연속으로 보내는 것이 같은 효과를 지니고, 
서버의 상태도 동일하게 남을 때, 해당 HTTP 메서드가 멱등성을 가졌다고 말합니다. 
다른 말로는, 멱등성 메서드에는 통계 기록 등을 제외하면 어떠한 
부수 효과(side effect)도 존재해서는 안됩니다. 올바르게 구현한 경우 
GET, HEAD, PUT, DELETE 메서드는 멱등성을 가지며, POST 메서드는 그렇지 않습니다. 
모든 안전한 메서드는 멱등성도 가집니다.

-멱등성을 따질 땐 실제 서버의 백엔드 상태만 보면 되며, 각 요청에서 반환하는 
응답 코드는 다를 수 있습니다. 첫 번째 DELETE 요청이 200을 반환한다면, 그 이후는 
아마 404를 반환할 것입니다. DELETE가 멱등성을 가진다는 것은, REST API에서 
개발자는 DELETE 메서드를 사용해 "목록의 마지막 항목 제거" 기능을 구현해서는 
안된다는 것입니다.
다만, 서버는 멱등성을 보장하지 않으며, 일부 애플리케이션은 잘못된 구현으로 
멱등성 제약을 어길 수도 있습니다.

-GET /pageX HTTP/1.1는 멱등성을 가집니다. 여러 번 연속해서 호출해도 클라이언트가
 받는 응답은 동일합니다.

    GET /pageX HTTP/1.1
    GET /pageX HTTP/1.1
    GET /pageX HTTP/1.1
    GET /pageX HTTP/1.1
-POST /add_row HTTP/1.1는 멱등성을 갖지 않습니다. 여러 번 호출할 경우, 
여러 열을 추가합니다.

    POST /add_row HTTP/1.1
    POST /add_row HTTP/1.1   -> Adds a 2nd row
    POST /add_row HTTP/1.1   -> Adds a 3rd row
-DELETE /idX/delete HTTP/1.1의 상태 코드는 응답마다 달라질 수 있지만, 
그럼에도 멱등성을 가집니다.

    DELETE /idX/delete HTTP/1.1   -> Returns 200 if idX exists
    DELETE /idX/delete HTTP/1.1   -> Returns 404 as it just got deleted
    DELETE /idX/delete HTTP/1.1   -> Returns 404

-PUT
HTTP PUT 메서드는 요청 페이로드를 사용해 새로운 리소스를 생성하거나, 대상 
리소스를 나타내는 데이터를 대체합니다.
PUT과 POST의 차이는 멱등성으로, PUT은 멱등성을 가집니다. PUT은 한 번을 보내도,
 여러 번을 연속으로 보내도 같은 효과를 보입니다. 즉, 부수 효과가 없습니다.
EX)

요청
PUT /new.html HTTP/1.1
Host: example.com
Content-type: text/html
Content-length: 16

<p>New File</p>

응답
대상 리소스를 나타내는 데이터가 없고, PUT 요청이 성공적으로 하나를 새로 생성한 경우,
 출처 서버는 반드시 사용자 에이전트에게 201 (Created) 응답을 보내 해당 사항을 알려줘야 합니다.

HTTP/1.1 201 Created
Content-Location: /new.html
대상 리소스를 나타내는 데이터가 있고, 이를 요청에 포함된 자료에 준하여 성공적으로
 수정했다면, 출처 서버는 반드시 200 (OK) 또는 204 (No Content) 응답을 보내 성공을 알려줘야 합니다.

HTTP/1.1 204 No Content
Content-Location: /existing.html

RESTful API
GET:조회할떄, POST:생성할때, PUT: 전체를 수정하려할때, 
PATCH: 일부를 수정하려할때, DELETE: 삭제하려할때
================================================================

썽크 thunks
-다른 작업이 완료될때까지 지연 시키기 위한 함수
-작업 객체를 즉시 반환하지 않는 작업 크리에이터를 작성하기 위해
--썽크로 작업 크리에이터를 작성할 수 있음
================================================================
RESTful API 와 REST API
RESTful API:RESTful은 REST의 설계 규칙을 잘 지켜서 설계된 API를 
RESTful한 API라고 합니다.
즉, REST의 원리를 잘 따르는 시스템을 RESTful이란 용어로 지칭됩니다.
 
REST API:"REpresentational State Transfer" 의 약자로, 
자원을 이름(자원의 표현)으로 구분해 해당 자원의 상태(정보)를 주고 받는 
모든 것을 의미합니다.
즉, 자원(resource)의 표현(representation)에 의한 상태 전달을 뜻합니다.

자원 : 해당 소프트웨어가 관리하는 모든 것 ( 문서, 그림, 데이터, 해당 
소프트웨어 자체 등 )
표현 : 그 자원을 표현하기 위한 이름 ( DB의 학생 정보가 자원이면, 'students'를 
자원의 표현으로 정함 )
상태 전달 : 데이터가 요청되는 시점에 자원의 상태를 전달한다. ( JSON 혹은 XML을 
통해 데이터를 주고 받는 것이 일반적 )

REST는 기본적으로 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에,
웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일입니다.
REST는 네트워크 상에서 Client와 Server 사이의 통신 방식 중 하나입니다.
RESTful하게 만든 API는 요청을 보내는 주소만으로도 어떤 것을 요청 하는지 파악이 
가능합니다.REST API를 간단히 요약하면
URI는 정보의 자원만 표현해야 하며, 자원의 행위는 HTTP Method에 명시한다는 것입니다.
출처: https://dev-coco.tistory.com/97 [슬기로운 개발생활:티스토리]

================================================================
URI 와 URL 차이
URI는 식별하고, URL은 위치를 가르킨다. 실세계에 빗대어 예시를 들어보자면 다음과 같다. 
“Charles” 는 내 이름이며 식별자(Identifier)다. 이는 URI와 비슷하지만 내 위치나 연락처에 대한 정보가 없으므로 URL은 될 수 없다
======================================================================
side effect는 React 컴포넌트가 화면에 렌더링된 이후에 비동기로 처리되어야 하는 
부수적인 효과들을 흔히 Side Effect라고 말함
======================================================================
라우터 npm install react-router-dom@5 (5버전 download)
-여러 페이지를 추가할 수 있음

-동일한 단일 페이지 응용 프로그램에 URL 이 다른 여러 페이지가 있는것처럼 
보이게 할 수 있음

-처음 로드되는 HTML 페이지는 하나이며 JavaScript가 이를 이어받게되는데
좋은 점은 URL을 통해 JavaScript를 사용하여 도메인 뒤의 URL과 해당 경로를
조작할 수도 있다, 또한 URL을 제어하고 해당 URL이 변경되거나 새 HTML 
파일을 가져오지 않고 링크를 클릭할 때 화면에 표시되는 내용을 변경하는 일부 
클라이언트 사이트 그리고 일부 React 코드를 작성하거나 사용할 수도 있음,
그래서 도메인 뒤의 해당 경로와 작동하는 URL과 작동하는 일부 코드가 필요함
그런 다음 페이지의 링크 클릭을 수신하여 해당 경로를 URL로 업데이트함
하지만 실제로 새 HTML 파일에 대한 요청을 서버에 보내지 않고 대신 우리가 
작성하거나 차단해야 하는 패키지를 수행하는 이 코드가 브라우저 기본값을 
수행하게 되는데, 대신 리액트가 포함된 클라이언트 사이드 JavaScript로
화면에 표시되는 내용을 업데이트하도록 하며 모든 라우팅을 수행하고 URL을 확인하고 
URL 변경을 기반으로 화면에 다른 컴포넌트를 가져오는 패키지를 원한다고 볼 수 
있는데 브라우저에서 이 모든 작업을 수행하려면 해당 작업을 
수행하는 코드를 작성하거나 해당 작업을 수행하는 써드(third) 파티 패키지를
사용해야하며 그것은 react-router 임

-react-router-dom 을 사용하면 다른 경로를 등록할수 있음, url 의 다른 경로
--와 이러한 경로에대해 컴포넌트가 매우 간편하게 로드됨

-import {Route} from 'react-router-dom'라고 명시하고 사용하면 Route 
라는 컴포넌트가 하나 생긴거라고 생각하자
import Welcome from "./components/Welcome";
function App() {
  return (
    <div>
      <Route path="/Welcome">{/*url 뒤에 /Welcome 의 경로가 붙을 경우에만 Welcome 표시*/}
        <Welcome />
      </Route>
      <Route path="/Products">
        <Products />
      </Route>
    </div>

-앱을 문서 요소로 렌더링하는 루트 파일로 이동해서 react-router-dom 에서
제공하는 BrowserRouter 컴포넌트를 가져와서 전체 앱을 래핑해줘하며 래핑하면
리액트 라우터가 활성화 되며 경로 정의와 같은 리액트 라우터 기능 잠금해제됨
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<BrowserRouter><App /></BrowserRouter>);

-Link component 는 link 를 생성하는 역할을 함,링크 컴포넌트에 의해
렌더링 된 앵커 태그이며, 내부적으로 라우터에 반응함, 사용하는 패키지는 
실제로 해당 링크의 클릭을 수신하고 브라우저 기본값을 유지하는 대신
URL을 수동으로 업데이트함,페이지를 전환하면 화면에 표시되는 내용도 바뀐 
것처럼 보임, 페이지 사이를 탐색할 수 있도록 하려면 이젠 표준 앵커 태그 대신
링크 컴포넌트를 사용하면 됨

-NavLink component 는 navigation 역할을 해주며 표준 링크를 대체할수있음
--여전히 앵커 태그를 생성하여 클릭이 새 요청을 보내는 브라우저 기본값을 
방지활성함, 앵커 항목에 CSS 클래스를 설정가능 activeClassName attr 로 하면됨

-동적 라우트
path /example/:productId 로 :동적경로 세그먼트로 이페이지가 
로드되어야하는 전체 경로는 다음과 같을거라고 라우터에게 알려주는것

-파람스 useParams 특수 훅 : useParams를 호출하면 훅은 상수에 저장할 수 
있는 params 객체를 반환함,키값 쌍을 가지게 되는데 페이지로 연결되는 동적 
세그먼트인 키를 의미하며 필요한 경우 여러 세그먼트를 가질 수 있음

-스위치 Switch compo : 라우트 컴포넌트 주위에 래핑 될 수 있음, 이러한 
모든 라우트 주위에 열기 및 닫기 태그를 추가하면 되며 그러면 경로 중 하나만
동시에 활성화됨 아마 가장 먼저 매칭되는 라우트가 될것임,또한
exact prop 를 추가하면 리액트 라우터에 정확히 일치하는 경우에만
일치 여부를 알려 주며 다음 경로의 시작 부분과 일치하는 이 경로를
전체 경로와 일치하게끔 전환해줌
<Switch>
  <Route path="/" exact> {/*사이트 방문 시 */}
    <Redirect to="/welcome"/>
  </Route>
</Switch>
--Switch 는 v6 이후로 Routes 로 대체되었음

-중첩 라우트
다른 컴포넌트에서 라우트를 정의할 수 있으므로 다른 라우트에서도 정의할 수 
있다, 그런 다음 더 구체적인 경로 일치가 있는 경우, 더 많은 콘텐츠를 로드할 
수 있으며  기능은 더 복잡한 사용자 인터페이스를 구축하는 데 사용할 수도 
있다, 그리고 빌드하는 모든 애플리케이션에 필요한 것은 아니지만 몇 가지
애플리케이션에서는 도움이 됨

리다이렉트 Redirect
--v6 이후 더이상 Redirect component 는 사용되지않음 Navigate 로 대체되었음
-react-router-dom 에 Redirect component
<Switch>
  <Route path="/" exact> {/*사이트 방문 시 redirect 로 to props 로 
  /welcome 으로 연결 */}
    <Redirect to="/welcome"/>
  </Route>
</Switch>  
exact 가 매우 중요, 그게 없다면 모든 라우트가 여기에서 일치하게 되고
항상 리디렉션을 하게 되며 여기 무한한 루프를 생성하게 됨

-useHistory 불러오기를 할 수 있는 react-router-dom hook
--v6 부턴 더이상 useHistory 는 사용되지않으며 useNavigate 로 대체되었음
--브라우저 기록을 변경 할 수 있다
--기록 페이지를 변경하는 것은 예를 들어 새 페이지를 추가하거나 새 페이지로 
이동하면 페이지 스택에 새 페이지를 푸시하는 push 메소드를 사용하여 탐색이 
가능하므로, 페이지 기록에 새 페이지가 표시되며, 현재 페이지를 대체하는 
replace 메소드로 탐색할 수도 있음, 차이점은 푸시를 사용하면 백(back) 
버튼을 사용하여 원래 페이지로 돌아갈 수 있고 replace 버튼을 사용하면
그럴 수 없다는 점임, replace는 발생한 페이지를 변경하는 리디렉션과 같고 
push는 새 페이지를 추가하는 것이라 볼 수 있다,사용자가 돌아가기를 원한다면 
스택에서 푸시를 사용하여 사용자가 뒤로 돌아갈 수 있게 한 다음 
history.push('/quotes') 이처럼 로 이동할 수 있다
-useHistory는 history 객체에 접속하게 하고, history 객체는 URL을 바꿀 수 
있게 해 줌
-페이지를 push 할때 현재 보고있는 페이지라도 페이지 컴포넌트는 재평가됨
(react router 가 history 를 변경했다고 보고 리렌더링함)

-Prompt Component (react-router-dom)
--when={state} message={(location)=> 'message'} 어떤 조건에 메시지 
출력할지 설정

쿼리 매개 변수
-물음표가 route 매칭을 바꾸지 않으며 route 매칭에 미치는 영향이 없지만,
어떤 route가 연결되든 쿼리 매개 변수 데이터에 접속해서 로드된 페이지의 
'행동'을 바꾼다 

useLocation
-location 객체에 접속하게 하고, location 객체엔 최근 로드된 페이지와
URL 의 정보가 있으며 useLocation 을 호출해서 location 객체를 받을수있음
-const queryParams = new URLSearchParams(location.search) 로 
queryParams 에 search 에있는 쿼리 매개변수 key,value 를 추출할 수 있음

useRouteMatch
-URL Pattern Match 을 통한 처리를 하고자 하는 경우에 사용할 수 있다
-useRouteMatch 는 match 객체의 값에 접근할 수 있게 해주는 hook
-방법 1)Route 컴포넌트의 프로퍼티들(path, strict, sensitive, exact)을 
가진 객체를 인자로 받는 방법으로, 만약 path 프로퍼티와 현재 페이지 URL이 
일치할 경우 해당 path의 match객체를 반환하고 일치 하지 않으면 null을 반환
-방법 2)아무 인자도 넘겨주지 않고 hook을 호출하는 방법이다. 이는 
withRouter HoC로 match객체에 접근했을 때처럼 제일 가까운 부모 Route 
컴포넌트의 match 값을 리턴
-Context API를 사용하기 때문에 <Route> 의 하위에서만 값을 받을 수 있다

ReactRouterVersion6
-6 버전에선 더이상 Switch Component 를 사용하지 않으며 Routes Component
로 대체되어 사용된다.
<Routes>
  <Route path='/welcome' element={<Welcome />}></Route>
  <Route path='/products' exact element={<Products />}></Route>
  <Route path='/products/:productId' element={<ProductDetail />}></Route>
</Routes>
--Route 에서 element attr 이 생겼으며 이안에 구성요소를 설정해야함
-더이상 exact 를 사용하지 않으며 v6 에선 알아서 exact 가 적용되어있음
--이전 버전처럼 사용하고 싶다면 path='/products/*' 로 url 이 /products 로
시작하는 경로일때만 활성화됨
-더이상 동적 세그먼트가 먼저 정의되어야할 필요가 없어졌음(라우팅이 특정
경로에 대해 가장 적합한지 판단함)
-더이상 activeClassName 를 v6 에선 사용하지 않음
{/*className, style 속성을 사용하면된다*/}
{/*<NavLink activeClassName={classes.active} to='/welcome'>*/}
<NavLink 
  className={(navData)= navData.isActive ? classes.active : ''} 
  to='/welcome'
>
  Welcome
</NavLink>
-더이상 Redirect component 는 사용되지않음 Navigate 로 대체되었음
만약 지정하길 원한다면 replace attr 을 추가해주면됨
-더이상 중첩 라우트를 사용할때 단 하나뿐이더라도 Routes 로 랩핑해줘야함
-더이상 중첩 라우팅시 path 의 경로를 상위 라우팅의 경로를
<Route path='/welcome/*' element={<Welcome />}></Route>로 지정시
웰컴 컴포넌트의 중첩 라우팅시
<Route path='/new-user' element={<Welcome />}></Route>로 사용하면됨
웰컴 컴포넌트안이라면 Link 도 new-user 로만 path 지정하면됨
기존에는 <Route path='/welcome/new-user' element={<Welcome />}></Route>
--이젠 중첩 라우팅을 상위에 지정할수 있으며 welcome compo 에는 <Outlet/>표현
<Route path='/welcome/*' element={<Welcome />}>
  <Route path='/new-user' element={<Welcome />}></Route>
</Route>
-더이상 useHistory 는 사용되지않으며 useNavigate 로 대체되었음
const navigate = useNavigate()
navigate('/welcome') 지정하거나 navigate('/welcome',{replace: true})
와 같이 stack 지정 가능하며 navigate(-1) 과 같이 숫자넣으면 이전 페이지로
돌아가는것을 뜻하며 -2 는 이전 페이지보다 전의 페이지로 1은 다시 앞으로간다는뜻
-더이상 Prompt 는 사용되지 않으며 아직 대체 컴포넌트가 생기지 않았음
================================================================
Layout
-nav 같은 경우 Layout compo 를 따로 만들어 Navigation compo 를 import
해와서 사용한다 (card 같은 느낌으로 적용하기 위해)
/*이 컴포넌트의 목표는 MainNavigation 을 실제 페이지 콘텐츠와 나란히 렌더링하는 것*/
const Layout = props => {
  return (
    <Fragment>
      <MainNavigation />
      <main className={classes.main}>{props.children}</main>
    </Fragment>
=======================================================================
사용자가 지원되지 않는 경로 입력 할 경우
-루트 라우트로 이동해서 들어오는 모든 요청과 일치 여부를 확인해야함, 모든 
URL과 일치되는 경우를 확인해야하며 그리고 * 에 경로를 설정함으로써 이 
작업을 할 수 있음,와일드카드 문자는 리액트 라우터에 모든 경로, 모든 URL이
라우트와 일치해야 한다는 신호를 보내며 경로는 실제 라우트 중 하나에 대한 
요청을 소비하지 않도록 마지막에 위치해야 함, 제일 마지막 지점점까지 
일치하는 항목이 없으면 모든 URL과 이 라우트가 일치되며 Not Found 페이지를 
렌더링 하도록함
================================================================
배포
1)test code
-deploy 할땐 코드를 쓰고 테스트하는걸로 시작

2)Optimize code
--최적화에 대해 살펴본다 (레이지 로딩 등)
---최적화되었고 잘 작동된다면 프로덕션용 앱을 빌드한다

3)빌드 App for Production
--스크립트를 실행하며 스크립트가 프로덕션 준비가된 코드를 출력할것이며 
코드들은 최대한 작게 축소되고 자동으로 최적화되면서 출력 값을 얻어 서버로 
옮길수 있게되면 자동적으로 사용자에게 최적화된 코드 패키지를 제공하게됨
-build folder : 최종적으로 deploy 하는데 필요한 모든 code 가 들어있음
(빌드 폴더의 코드는 절대로 변경하면안됨 npm run build 할때마다 파일이
자동으로 덮어씌워지기 때문)

4)Upload Production code to server
-디플로이할 준비가 된 최적화된 코드가 생성되면 그 패키지를 디플로이할건데
작성한 코드를 바탕으로 생성된 코드를 서버로 업로드하며 이때 옵션이 다양한 
호스팅 프로바이더가 있다

5)Configure Server
-서버 또는 호스팅 프로바이더의 제품을 설정

-리액트 싱글 페이지 앱을 배열하고 싶을때 정적 사이드 호스트가 필요함

레이지 로딩
-해당 코드가 필요할 때만 그 특정 코드를 로딩하는 것
--예를 들어 쿼트 추가와 관련된 코드 등 특정한 코드는 진짜로 해당 페이지에 
들어올 때만 다운로드되도록 해야 함, low close free thousand 에 들어와서
초기 화면만 보고 새 쿼트를 추가하지 않을 수도 있기 때문, 그렇다면 쿼트 
추가 기능과 관련된 모든 코드를 다운로드할 필요가 없다, 초기 다운로드가 
불필요하게 커질 뿐이기때문에 해당 코드가 필요하지 않으니까요.이것이 바로 
레이지 로딩의 개념
-코드를 여러 덩어리로, 여러 번들로 나누고 각각 필요할 때만 다운로드하는 것
-라우팅을 사용하는 경우 레이지 로딩을 구현하기 쉽다,라우트별로 코드를 
분할해서 특정 라우트에 대한 코드가 해당 라우트를 방문할 때만 다운로드되도록 
할 수 있기 때문

페이지 url 입력 시 출력까지 과정
-페이지를 방문하면, local host free thousand를 여기 입력해서 페이지에 
들어오면, React가 이 모든 유저 인터페이스를 화면에 띄우고 이 애플케이션이 
반응하게 하기 위해 다운로드되어야 하는 모든 React 코드 말입니다. 즉, 
여기에서 볼 수 있는 모든 것과 여기에서 사용하는 모든 것은 모든 코드가 
다운로드된 후에만 작동합니다. 사용자가,화면에 뭐가 보이고 웹 애플리케이션을 
사용할 수 있을 때까지 우리 웹사이트 방문자가 코드가 다운로드될 때까지 
기다려야 한다
-초기 코드 번들,다운로드되는 이 최초의 첫 번째 코드 번들을 가능한 한 
작게 만들어야 함

================================================================
React.lazy()
-코드 분할에 도움이 되는 기본 메서드
ex)
/*React.lazy 에 전달하는 이 함수는 이 새 쿼트 컴포넌트가 필요할 때 React 
에 의해 실행됨
이것이 일반적으로 import 할때와의 핵심적인 차이점임 코드를 미리 다운로드하기 
위해 미리 실행하지 않고 필요할 때만 실행*/
const NewQuote = React.lazy(()=> import('./pages/NewQuote'))

대체 UI 를 정의 해야하는 이유
-코드를 필요할 때만 다운로드한다는 것이 레이지 로딩의 개념인데 문제는, 이 
다운로드가 몇 밀리초 또는 몇 초가 걸릴 수 있다는 것이며 코드를 다운로드하는 
동안 React는 당연히 중단되고, 다운로드가 완료될 때까지 이 컴포넌트를 로드할 
수 없게되기에 대체 UI를 정의해야 한다
--이때 필요한게 React 의 Suspense component 이며 React.lazy를 사용하는 
코드에 래핑한다 
ex)
function App() {
  return (
    <Layout>
      <Suspense
        fallback={
          <div className="centered">
            <LoadingSpinner />
          </div>
        }>
fallback attr 을 넣어줘서 다운로드되는 동안 로딩스피너가 보이도록함
================================================================
파이어 베이스 호스트 사용
-파이어 베이스 도구 설치
npm install -g firebase-tools
-npm config get prefix (NPM 경로 확인)
-firebase login
questions
-yes
-firebase init (프로젝트 경로)
-yes
-디렉토리 build 입력
-hosting config 선택
-yes no no
-firebase deploy
-firebase hosting:disable 
-싱글 페이지 앱을 호스트 할때 경로 무시 하고 싶을때
서버에 있는, 도메인 뒤의 부분은 항상 같은 응답을 리턴할 것임 같은 HTML 
파일, 같은 자바스크립트 파일을 응답함 사용자가 어떤 경로를 타겟하는지 
관계없음 그렇게 하면 리액트 앱이 시작되며 그럼 리액트 앱과 앱의 일부인 
리액트 라우터는 다른 URL을 찾을 것임 그리고 알맞은 콘텐츠를 스크린에 
렌더함 따라서 서버는 /some-route라는 경로를 무시해야 함 하지만 디폴트로는 
서버가 그렇게 하지 않음 따라서 여러분이 직접 무시하도록 서버를 설정해야함
그리고 특정 호스트 제공자의 문서화를 살펴야 함 거기서 설정이 어떻게 
되어있나 봄 파이어베이스에서는, 아주 쉬움 파이어베이스가 무시할 건지는 
물음 모든 URL이 인덱스 HTML로 다시 쓰여야 한다면, 어떤 종류의 URL이 
보내졌는지와는 관계없이, 우리는 항상 같은 HTML 파일을 리턴해야 함 그럼 항상
같은 자바스크립트 코드를 요청할 것임 URL이 뭔지와 상관없이, 따라서 여기에 
예스라는 의미로 y를 입력하면, 파이어베이스가 설정함 이게 서버를 설정하는 
과정임 ,항상 서버를 설정해야한다 URL과 URL에 있는 경로가 서버에서 
무시되도록, 그렇게 하면 싱글 페이지 앱 코드를 항상 리턴할 것임URL이 뭔지와 
관계없이, 여기서 y를 치고 엔터를 누른 뒤에, 자동 빌드와 배열은 필요 없으므로
'노'라는 의미로 n을 입력하면 됩니다.그리고인덱스 HTML 파일이 다시 쓰여야 
하느냐는 질문에도n을 입력해야 함 왜냐하면 우리는 HTML 파일을 이용할 것이기 
때문, npm 런 빌드 명령어로 만들어진 HTML 파일임 이렇게 해서 파이어베이스 
배열이 설정됨

URL 을 직접 쓰고 엔터를 누르면 일어나는 상황
-서버와 클라이언트가 있으며 클라이언트는 브라우저를 사용하는 사용자임
서버는 원격 머신이며 프로덕션 레디 리액트 코드를 호스트함 따라서 코드를 
배열함 로컬 머신이 아니라 어떤 서버에 있을 것이며 사용자를 위한 머신에는 
없음 어떤 서버에 있다 만약 사용자가 페이지를 방문한다면, 도메인을 입력하고
그 위에 경로를 입력해야 할텐데 사용자는 서버에 요청을 보낸다 웹사이트에 
관한 요청이며 요청에는 전체 URL이 입력됨 그다음에 요청이 서버로 갈 것임
그리고 서버가 다시 응답을 보내며 응답에는 CSS와 HTML 코드가 포함됨 그리고 
JS 리액트 코드도 있음 리액트 코드가 만들어지고 업로드됨 리액트 코드는 
리액트 라우터 코드를 포함함 이게 경로를 탐색하고 도메인 뒤의 URL 부분이
평가한 뒤에 알맞은 컴포넌트를 스크린에 가져옴 경로를 정의한 컴포넌트를 
렌더함 하지만 이건 응답받았을 때만 일어나는 일임
사용자가 입력한 URL은, 사용자가 특정 경로와 입력한 URL은, /some-route 같은 
건, 요청의 일부임 따라서 서버에 도달한 요청은 경로를 포함함 전체 URL을 
포함함 그리고 디폴트로, 서버는 다른 파일을 찾음 다른 URL의 응답으로 리턴될 
것임 그런 식으로 서버가 작동함 다른 URL은 다른 액션을 트리거 함 따라서 다른 
응답을 도출함
================================================================
인증, 로그인, 로그아웃, 가입 , 보호된 리소스 접근, 로그인 유지, 일정시간 후
자동 로그아웃, 인증 작동 원리

-모든 사이트 이용자나 방문자가 모든 정보에 접근 권한을 가져선 안 되니인증이 
필요
-사이트의 특정 페이지 같은 경우 미인증 사용자의 접근을 제한
-데모 웹사이트로 작업은 시작 페이지도 있고 신규 사용자 생성이 가능한 로그인 
페이지가있고, 프로필 페이지에서는 사용자가 비밀번호를 변경할 수 있음 이 
프로필 페이지는 로그인한 사용자만 접근가능, 로그인 상태가 아니면 이 
페이지에 들어올 수 없어야 함 따라서 접근 제한을 걸어야 함 로그인하지 않은 
사용자는 접근할 수 없게, 이런 페이지뿐 아니라 데이터베이스에 저장된 데이터도
보호된 정보일 수 있음 미인증 사용자의 접근이 제한된 페이지에 리액트 앱이 
요청을 보낼 때 그 요청을 받는 API 엔드포인트가 그런 데이터에 속함, 프로필 
페이지는 우리가 Change Password 버튼을 누르면 비밀번호 변경 요청이 전송됨
버튼을 누르는 순간 데이터베이스 내의 사용자 비밀번호를 업데이트하겠다는 
요청이 서버로 전송됨 프로필 페이지 자체에도 접근 제한을 걸어야겠지만 
로그인한 사용자가 보낸 게 아니라면 API 엔드포인트로 전송된 요청이 성공할 수 
없게끔 API 엔드포인트에도 접근 제한을 걸어야 함 API 엔드포인트에 접근 
제한을 걸지 않으면 엔드포인트의 URL을 아는 아무 사용자나 비밀번호 변경 
요청을 보내 다른 사람의 비밀번호를 바꿀 수 있어 보안이 취약해지기 때문,
그러니 사이트의 페이지뿐 아니라 리액트 앱에서 보낸 요청을 받는 API
엔드포인트에도 접근 제한을 걸어야 함, 인증이 필요한 이유임 일반적으로 
인증은 2단계 절차를 거칩니다 1단계는 사용자가 접근 허가를 받는 것이며
로그인으로 자격 증명을 제공해 접근 허가를 받을 수 있음 그러려면 계정부터 
생성해야하며 일단 계정을 만들고 로그인 시에 자격 증명을 제공하면 데이터가 
서버로 전송됨 그러면 서버에서 데이터베이스를 살펴 사용자의 이메일/비밀번호 
조합을 확인함 유효성이 검증되면 요청을 받은 백엔드 서버가 접근을 허가함 
일단 허가를 받으면 사이트의 특정 페이지에 접근할 수 있고 필요에 따라서는
접근 허가를 활용해 API 엔드포인트의 다른 보호된 리소스에 후속 요청을 보낼 
수도 있음 허가를 받고 나서 허가 정보를 첨부해 다른 엔드포인트에 더 많은 
요청을 보낼 수 있는 음 인증은 보통 이런 식으로 작동함 브라우저에서 리액트 
앱이 실행 중인 클라이언트와 백엔드 서버가 있음 서버 사이드 코드는 우리가 
직접 작성해도 되고 타인이 작성해도 됨 우리가 강의에서 사용하는 것처럼
서드파티 API, 즉 외부 API일 수도 있고 우리 자체 API일 수도 있음 우선 
이메일/비밀번호 조합을 입력해 서버에 요청을 보내면 서버가 유효성을 확인하고
자격 증명을 검증해 후속 요청을 허가하거나 거절함 그러고 나면 조금 전에 
설명했듯 받은 허가를 활용할 수 있음 단순한 ‘예, 아니오’만으로는 API 
엔드포인트 같은 보호된 리소스에 접근할 수 없음 ‘예, 아니오’ 같은 응답은
위조하기 쉽기때문 자격 증명을 받는 서버가 ‘예, 아니오’로만 응답한다면
아예 허가를 받는 절차를 생략하고 보호된 리소스에 우리가 직접 ‘예, 아니오’ 
요청을 보낼 수도 음 그러므로 인증은 단순한 ‘예, 아니오’보다 더 정교해야 
함 자격 증명을 보내고 확인하는 과정은 반드시 필요하지만, 서버가 클라이언트에
보내는 응답은 ‘예, 아니오’보다는 복잡해야 함 그럴 때 쓰는 기법은 크게 
2가지임 서버 사이드 세션을 활용하거나 인증 토큰을 활용함 서버 사이드 세션은
무척 전통적이면서도 훌륭한 인증 처리 기법임 서버 사이드 세션 기법에서는
사용자 접근을 허가한 서버가 허가를 받은 클라이언트, 즉 특정 사용자의 고유 
ID를 저장하며 서버가 특정 클라이언트의 고유 ID를 생성하고 저장함 따라서 
인증을 거치는 모든 사이트 방문자의 고유 ID가 서버에 저장됨 이 ID는 서버에만 
저장되지 않고 클라이언트에게도 전송됨 덕분에 서버의 응답은 단순한 ‘예, 
아니오’가 아니라 고유 ID까지 포함하게 됨 서버와 클라이언트 모두 이 ID를 
알고 있으며 이 ID는 서버에 후속 요청을 보낼 때 함께 첨부됨 서버가 ID를 알고 
있으므로 ID를 위조할 수 없음 임의로 만든 ID는 서버가 못 알아보니 접근이 
거부되고 후속 요청도 불가함 그러나 이 방식에는 단점이 하나 있음 백엔드와 
프론트엔드의 결합이 긴밀하면 아무 이상 없지만 분리돼 있다면 이야기가 달라져요
가령, 싱글 페이지 앱은 서버 A로, 백엔드 앱의 REST API는 서버 B로 운영 
중이라면 결합이 느슨해서 백엔드 API와 프론트엔드의 싱글 페이지 앱은 서로 
독립적으로 작동함 또는 구글 맵스 API처럼 여러 사이트에서 이용할 수 있는
API를 만드는 중이라면, 이 역시 특정 프론트엔드에 긴밀하게 결합하지 못하고
유동적인 상태로 있음 따라서 이런 경우에는 서버에 ID를 저장하면 안 됨
서버는 이른바 무상태여야함 접속한 클라이언트의 데이터를 저장해선 안 됨
백엔드와 프론트엔드 분리 상태는 특히 싱글 페이지 앱 개발에서 자주 맞닥뜨릴 
것이기 때문에 그런 상황에서는 인증 토큰을 사용하면 됨 기본 개념은 얼추 
슷함 다만 중요한 차이가 있으며 사용자가 이메일과 비밀번호로 서버에 자격 
증명을 보내면 서버가 그걸 데이터베이스에 저장된 이메일/비밀번호 조합과 
비교해 유효성을 확인하는 것까지는 같음 그런데 자격이 증명되면 서버가 허가 
토큰이라는 걸 생성함 안에 데이터가 인코딩된 아주 긴 문자열임 서버가 특정 
알고리즘을 사용해 사용자의 이메일 주소를 비롯한 각종 데이터를 한 문자열로
인코딩하면 나중에 다시 개별 데이터로 디코딩할 수 있음 각기 다른 데이터를 
이어붙이는 작업임 토큰은 서버가 특정 알고리즘에 따라 생성하는데, 이때 
중요한 건 서버만 아는 키를 사용해 데이터를 문자열로 해싱함 사용되는 키는
클라이언트는 모르고 서버만 압니다 토큰은 서버에 저장되지 않고 클라이언트에게 
다시 전송되지만 토큰을 생성하는 법은 서버만 알고 있음 그 과정에 키가
쓰이기때문, 리액트 앱 같은 클라이언트는 이 토큰을 후속 요청에 첨부해 
서버의 보호된 리소스에 보냄 서버는 세션 기반 기법과 달리 ID를 저장하지 
않고도 자신이 생성한 토큰인지 확인할 수 있음 토큰 생성에 사용된 개인키를 
아는 건 서버뿐이기때문 그래서 보호된 리소스에 접근 요청을 보낼 때 첨부된
토큰의 유효성을 서버가 확인함 자신이 생성한 토큰인지 확인할 수 있기 때문,
토큰이 위조됐거나 다른 키로 생성됐으면 서버가 이를 감지하고 접근을 거부함
서버가 클라이언트를 식별하는 또 다른 보안 방식이자 프론트엔드와 백엔드 분리를
허용하는 기법임
-"인증 토큰"을 작업할 때, 이러한 토큰은 일반적으로 "JSON 웹 토큰" 형식(JWT)
으로 생성됨
================================================================
- 로그인과 같이 전역 상태 관리 (앱 와이드 상태)는 2가지 옵션이 존재
1) context api
2) redux
================================================================
네비게이션 가드
-로그인 여부에따라 라우트 설정을 동적으로 바꿈
========================================
NextJS
-React 를 기반으로하는 프레임워크
-nextJS 는 FULL STACK FRAMEWORK 라고 한다
-프레임워크가 라이브러리보다 더 크고 더 많은 기능이 있다
-코드를 작성하는 방법이나 파일을 구성하는 방법에대한 명확한 규칙과 지침있음
-ServerSideRendering 을 내장하고있다
-Next 앱을 만들면 추가 설정을 안해도 페이지에 방문했을때 서버에서 
기본적으로 사전 렌더링을 하기에 검색 엔진 최적화에 좋음
-사용자가 후속 탐색을 할 수있음, 사용자가 페이지를 열어서 탐색할 때
이런 활동들은 모두 브라우저에서 React가 관리하여 사용자에게 빠른 대화형 
인터페이스를 제공할 수 있음
-NextJS 는 public folder 에 index.html 이없음,왜냐하면 NextJS는 사전 
렌더링 기능을 내장하기 때문에 NextJS는 싱글 페이지 애플리케이션을 제공하여
서버에 요청이 오면 이 싱글 페이지에 동적으로 사전 렌더링을 거쳐
콘텐츠를 포함한 초기 페이지를 보여주게 되기때문
-npm un dev 로 개발서버를 시작함
-pages folder 의 파일 명으로 경로 설정
-폴더명으로 파일이름을 정해서 index.js file 에 컴포넌트를 작서애놓으면
폴더명으로 경로를 탐색해서 index.js 에있는 component 를 출력한다
-중첩 경로가 필요하면 하위 폴더를 만들어야한다
-NextJS 가 자동으로 생성하는 사전 렌더링된 페이지는 useEffect 와 같이 
두 번째 사이클을 기다리지 않으며 첫 번째 렌더링 사이클의 결과를 가져와서
사전 렌더링한 HTML 코드를 반환함
-getStaticeProps 및 거기서 반환할 수 있는 항목에 대한 더 많은 구성 옵션이 
있음, 그리고 내장된 Next Image 컴포넌트를 사용하여 이미지를 최적화할 수 
있는 방법도 있음 NextJS로 간편하게 인증을 추가하고 사용자 가입, 로그인, 
로그아웃 추가 및 세션 관리를 할 수 있음 이 모든 것이 가능함
----------------------------------------------------------------
파일 기반 라우팅
-pages folder 를 구성하고있으며 페이지가 지원하는 라우트와 경로를 정의함
----------------------------------------------------------------
라우팅: 사용자에게 여러 페이지가 있는것처럼 착각하게 하는것
-탐색하고 다른 페이지를 로딩하는것이 라우터의 역할
-라우터는 기본적으로 URL을 감시하다가 URL이 바뀌면 백엔드 서버에 요청을 
보내는 브라우저의 기본 동작을 막고 대신 React를 사용하여 페이지에 다른 
콘텐츠를 렌더링함 다른 컴포넌트를 보여주는 거임 이런 과정이 바로 라우팅
-서버에 추가로 요청을 보내지 않고 URL을 기반으로 화면에 보이는 것을 바꿈
----------------------------------------------------------------
풀스택 프레임워크
-React 프로젝트에 백엔드 코드를 쉽게 추가할 수 있다
-풀스택 React 프로젝트를 구축하려면 클라이언트 쪽 코드만 있어서도 안 되고
서버 사이드 사전 렌더링을 해야 할 뿐만 아니라 독립형 백엔드 코드도 있어야 함
-React 프로젝트에 백엔드 API를 쉽게 추가할 수 있음 즉, NextJS를 이용하면 
Next / React 애플리케이션에 코드를 쉽게 추가할 수 있다, 이런 방식으로 
코드를 추가해서 데이터베이스나 파일에 데이터를 저장하거나 거기에서 데이터를 
받아오거나, 인증을 추가하는 등 모든 작업을 할 수 있음. NextJS로 쉽게 추가할 
수 있다,프로젝트 하나로 작업할 수 있음,그러면 독립적으로 REST API 프로젝트를
구축하지 않아도 됌
----------------------------------------------------------------
SSR
-페이지 콘텐츠를 클라이언트가 아니라 전적으로 서버에서 준비함
-검색 엔진 최적화(서버에서 해당 페이지를 사전 렌더링한 상태에서 서버에 
요청이 들어왔을때 해당 데이터를 서버에서 가져오면 완성된 페이지가 사용자와 
검색 엔진 크롤러에게 제공됨)
--사용자는 깜빡이는 로딩 상태를 보지 않아도 되고 검색 엔진도 해당 페이지 
콘텐츠를 보게 됨
--서버에서 리액트 컴포넌트를 사전 렌더링할수있다는말
-ReactJS 에서도 SSR 을 추가할수있는 기능이 내장되어있지만 구현하기까다로움
----------------------------------------------------------------
-동적 경로 설정
pages folder 에 file name 을 [].js 로 사용하면 동적 페이지로 인식해서 
경로에 여러 값을 불러오며 괄호 안에 식별자를 추가하면 된다
----------------------------------------------------------------
useRouter
-라우터는 페이지를 처음 렌더링할때 즉시 실행됨
-컴포넌트 함수에서만 사용 가능
----------------------------------------------------------------
싱글 페이지 어플리케이션 SPA single page application
-새 html page 를 요청하는게 아닌 화면을 업데이트하는것
-싱글 페이지 어플리케이션으로 유지하려면 a tag 가 아닌 Link component 사용
(import Link from 'next/link')
Link가 앵커 태그를 렌더링하고 이 앵커 태그에 하는 클릭을 감지해서 클릭을 
하면 브라우저가 기본 동작으로 새 HTML 페이지를 받는 요청을 보내지 못하도록 
함 대신에 불러올 컴포넌트를 읽어 들이고 URL을 변경하여 페이지가 바뀐 것처럼 
보이게 함, 실제로는 싱글 페이지 애플리케이션에 있는 것임 따라서 NextJS 
애플리케이션의 사이트 내부 링크에는 앵커 태그 컴포넌트 대신에 Link 
컴포넌트를 쓰는 것이 좋음
----------------------------------------------------------------
_app.js 
-이 특수 컴포넌트는 NextJS가 렌더링하는 최상위 컴포넌트처럼 작동
-모든 페이지에 적용할 컴포넌트나 설정이 있다면 이 _app.js 파일을 활용해서 
추가하면됨, 수십 개의 파일에 하나씩 들어갈 필요가 없음
----------------------------------------------------------------
NextJS는 페이지 렌더링 방법을 제어하는 데 사용할 수 있는 두 가지 형태의 
사전 렌더링을 제공
-정적 생성
--정적 생성에서 페이지 컴포넌트가 사전 렌더링 되는 시점은 애플리케이션을 
빌드하거나 Next 프로젝트를 빌드하는 시점 즉 프로덕션용으로 빌드하는 시점임
--정적 생성에서는 기본적으로 요청이 서버에 도달했을 때 서버에서 즉각적으로
페이지를 사전 렌더링하지 않는다,대신에 개발자가 프로덕션용 사이트를 빌드할 
때 사전 렌더링함, 즉 사이트가 배포되고 나면 사전 렌더링한 페이지는 변경되지 
않는다는 뜻이며 데이터를 업데이트했는데 사전 렌더링한 페이지를 변경해야 
한다면 해당 빌드 프로세스를 다시 시작하고 다시 배포해야 한다.
----------------------------------------------------------------
getStaticProps
-이 함수들은 프리 렌더링 페이지에 데이터를 패치하도록 합니다.
데이터를 기다려야 한다면 즉 페이지 컴포넌트에 데이터를 가져와서 추가해야 
한다면 페이지 컴포넌트 파일 안에서 특수 함수를 export로 내보내면 된다
아주 중요함 이건 페이지 컴포넌트 파일에서만 작동함, 다른 컴포넌트 파일은 안됨 
pages 폴더 안에 있는 컴포넌트 파일들에서만 가능 getStaticProps()
을 nextJS 가 발견하면 사전 렌더링 프로세스 중에 이 함수를 실행함, 컴포넌트
함수를 바로 호출하지 않고 반환된 JSX 스냅샷을 html 컨텐츠로 사용함
getStaticProps 는 비동기적으로 설정될수있어서 유용하며 promise 를 반환 할
수 있다, nextJS 는 PROMISE 가 해결될때까지 기다린다, 데이터를 읽어 들일때
까지 기다린다, 그 다음에 페이지 컴포넌트 함수에서 사용할 props 를 반환함
이렇게되면 페이지 컴포넌트 함수가 실행되기 전에 데이터를 읽어들일수있어서 
페이지 컴포넌트를 필요한 데이터와 함께 렌더링 할수있다
---getStaticProps 함수 안에서는 일반적으로 서버에서만 돌아가는 어떤 
코드든지 전부 실행할 수 있다, 파일 시스템에 접근가능하며 데이터 베이스에도
안전하게 연결 가능
--여기에 작성하는 모든 코드는 클라이언트 측에 들어가지 않기 때문에클라이언트 
측에서 절대 실행되지 않음 이 코드는 빌드 프로세스 중에
실행되기 때문임 서버에서도, 특히 방문자인 클라이언트 측에서도 실행되지 
않음 따라서 여기에 쓴 코드는 절대 방문자의 컴퓨터에 도달하지 못함
방문자 컴퓨터에서 실행될 수가 없습, 예를 들어 API나 데이터베이스에서
데이터를 가져오거나 파일 시스템의 일부 파일에서 데이터를 읽어올 수도 있음
필요한 데이터를 얻는 작업을 모두 완료했으면 여기 getStaticProps에서 객체를 
반환해야 함 항상 여기에서 객체를 반환해야 함
--가장 중요한 것은 일반적으로 getStaticProps 함수의 props 프로퍼티를 
설정한다는 것임 이름은 반드시 props여야 하며 여기에 다른 객체를 저장하는데  
이건 이 페이지 컴포넌트 함수에서 받는 props 객체가 될 것임 props 객체를 
받으면 이 객체는 여기 getStaticProps에서 props로 설정한 객체임
--초기에 이 페이지를 사전 렌더링하기 전에 빌드 프로세스에서 데이터를 받기에
클라이언트 측 컴포넌트의 두 번째 렌더링 사이클에서 데이터를 받는 것이 
아니게됨 이는 사전 렌더링으로 데이터 가져오기는 굉장한 장점이자 NextJS의 
주요 기능 중 하나임
--revalidate property
---점진적 정적 생성이라는 기능을 추가 할 수 있음
---숫자가 필요하며 숫자는 요청이 들어올때 이 페이지를 다시 생성할때까지 
NextJS 가 대기하는 시간을 초단위로 표시하는것임
---revalidate: 3600 과 같이 하면 1시간마다 이전 페이지를 대체하게됨
---페이지가 배열 다음에 규칙적으로 업데이트되게 할 수 있음
하지만 주기적인 업데이트로도 부족할 수 있다 요청이 들어올 때마다 페이지를 
다시 만들어야 할 때가 있기때문, 페이지를 동적으로 프리 제너레이트해야 한다
--페이지가 빌드 프로세스 중에 프리 제너레이트 됐다는건 말은 넥스트 JS가 동적 페이지의 
모든 버전의 프리 제너레이트가 필요하다는 말임 지원되는 모든 ID에서요. 동적이기 때문에 
넥스트 JS는 어떤 ID 밸류가 프리 제너레이트 페이지가 되어야 하는지 알아야 함 프리 
제너레이트 페이지가 아니면 ID는 여기 있는 URL에서 얻을 수 있지만 사용자가 URL의 특정 
밸류로 페이지에 방문했을 때 프리 제너레이트되는 게 아님 빌드 프로세스에서 되는 거임
따라서 모든 미트 업 ID 밸류에서 모든 URL에서 프리 제너레이트해야 함 만약 프리 
제너레이트 하지 않은 페이지인 ID로 입장하면 404 에러를 보게 될 것임 
하지만 그런 식으로 작동하기 때문에 getStaticPaths를 추가해야 함
----------------------------------------------------------------
서버 사이드 렌더링 getServerSideProps()
-이 함수들은 프리 렌더링 페이지에 데이터를 패치하도록 합니다.
-이 함수는 빌드 프로세스 중에는 실행되지 않음,하지만 대신 배열 다음에 
서버에서 실행됨
-api 에서 data 를 패치할 수 있고 파일 시스템이 될 수 도있음, 코드는
서버에서만 실행됨, 자격증을 이용하는 운영을 실행 할 수 있음
-매개변수 context 넣어주면 context 매개 변수에서 요청 객체에 접속 가능
const req = context.req
const res = context.res
-단점
모든 요청을 실행하기에 단점이 될 수 있다, 요청이 들어올 때까지 페이지가 
만들어지기 기다려야 한다는 뜻임 항상 바뀌는 데이터가 없는데 매초 여러 번 
바뀌게됨 그리고 인증 처럼 요청 객체에 접속할 필요가 없다면 
getStaticProps이 좀 더 낫다, 여기서는 HTML 파일을 프리 제너레이트하기 
때문임 그 파일은 CDN에 저장되고 서브 된다 그리고 요청이 들어올 때마다
데이터를 다시 만들고 패치하는 것보다 빠르다 따라서 페이지는 
getStaticProps일 때 더 빠르다 캐시하고 다시 사용하기때문, 따라서 
콘크리트 요청 객체에 접속해야 한다면 getServerSideProps을 사용해야 한다 
getStaticProps에서는 요청과 응답에 접속하지 않기때문, 매초 여러 번 바뀌는 
데이터를 가지고 있다면 revalidate도 도움이 안 됨 이때는 
getServerSideProps이 좋은 선택임 그리고 여기 meetups 에서는 좋은 선택이 
아님, 주기적으로 바뀌는 데이터가 아니기때문, 그리고 여기서는 들어오는 요청에
작업할 필요없기때문,그럼 캐시를 이용할 수 있으니까 getStaticProps 
사용하는게 좋다 그리고 페이지를 여러 번 프리 제너레이트할 필요 없기때문
불필요한 일일뿐이다
----------------------------------------------------------------
npm run build
-npm run build를 실행하면 프로덕션 빌드를 구축하고 프로덕션 빌드를 만들고
결과가 나옴 출력된 결과를 보면 무엇을 했는지 볼 수 있음 
info  - Creating an optimized production build  
info  - Compiled successfully                   
info  - Collecting page data
info  - Generating static pages (4/4)
info  - Finalizing page optimization

Page                                                           Size     First Load JS
┌ ● /                                                          703 B          65.1 kB
├   └ css/a328f70f1500a47f59a4.css                             409 B
├   /_app                                                      0 B            64.4 kB
├ ○ /[meetupId]                                                4.88 kB        69.3 kB
├   └ css/3b26cd1d59fa637b4c12.css                             81 B
├ ○ /404                                                       3.46 kB        67.8 kB
└ ○ /new-meetup                                                770 B          65.1 kB
    └ css/60f9e9f292a28db77853.css                             360 B
+ First Load JS shared by all                                  64.4 kB
  ├ chunks/3ef630e34cd10ba68f9d468ac363ff81c534e1e9.f8990c.js  13.1 kB
  ├ chunks/framework.d886aa.js                                 41.8 kB
  ├ chunks/main.fa70c4.js                                      6.63 kB
  ├ chunks/pages/_app.ee2c13.js                                2.13 kB
  ├ chunks/webpack.50bee0.js                                   751 B
  └ css/022ca2af15273adee313.css                               494 B

λ  (Server)  server-side renders at runtime (uses getInitialProps or getServerSideProps)
○  (Static)  automatically rendered as static HTML (uses no initial props)
●  (SSG)     automatically generated as static HTML + JSON (uses getStaticProps)
   (ISR)     incremental static regeneration (uses revalidate in getStaticProps)
예를 들어서 정적 페이지 몇 개를 생성한걸 볼 수있고, 정확히는 네 페이지,
어떤 페이지를 만들었는지도 볼 수 있음 이걸 보면 루트 페이지를 만들었다는 걸 
알 수 있음 슬래시 뒤에 아무것도 없습니다 이 /[meetupId]는 동적 페이지이며
여기 404 페이지는 기본값으로 자동으로 만들어지는 것, 유효하지 않은 URL을 
입력한 경우에 사용함 여기 new-meetup 페이지도 있음 그리고 여기 페이지 옆에 
아이콘들이 있는데, 하나는 채워진 원이고 나머지는 비어있는 원으로 보이고 
밑으로 내려보면 여기 범례가 나와 있음 보시면 채워진 원은 정적으로 생성된 ;
사이트를 의미함 이 SSG는 정적 사이트 생성(Static Site Generation)의 
약자임 HTML로 자동 생성된 것임, JSON은 페이지가 싱글 페이지 
애플리케이션으로 전환되면 데이터를 미리 가져오는 데 사용됨 이 비어있는 원은 
정적 생성을 의미함 유일한 차이점은 여기엔 초기 props가 없다는 것임 따라서 
가져온 초기 데이터가 없고 실제로 루트 페이지에서만 데이터를 가져옴
getStaticProps를 추가한 페이지라서그럼, 예를 들어 new-meetup 페이지에는
아무 데이터도 가져올 필요가 없음 여기에서는 양식을 렌더링할 뿐이기때문,
아무 데이터도 필요 없고 서버에서 어떤 데이터도 받아오지 않음 그래서 
new-meetup 페이지는 늘 아무 콘텐츠가 없는 정적 페이지로 남아 있음
이 meetupId 페이지는 나중에 SSG 페이지로 바꿈

-이 명령을 실행하면 최적화된 파일 일부를 포함하는 .next 폴더를 얻게 됨
예를 들어, 이 .next 폴더는 미리 생성된 모든 페이지 파일과 시작 페이지 또는
개별 meetup 세부 정보 페이지와 같은 해당 HTML 파일을 포함함 즉, npm이 
구축을 실행하고 Vercel이 서버를 대신하여 명령을 실행하기 때문에 작업을 따로 
할 필요가 없음,하지만 직접 관리하는 다른 서버에서 프로젝트를 호스트하려면
npm run build 를 실행해야 npm start로 프로덕션 서버를 시작할 수 있음
다시 말해, 실행 중인 서버가 있지만 이것은 원격 기기에서 시작할 수 있는
프로덕션 서버이며 다음 애플리케이션을 위해 실행하는 사용자가 직접 관리하는 
서버임 따라서 애플리케이션을 외부에 공개하려는 경우 애플리케이션을 배포한 
기기에서 해당 서버는 계속 실행되고 있어야 함 여기에서 작업을 하고 있지만
이제 모든 작업을 Vercel이 수행함
vercel site 에서 github account login 하고 git repository import 하고
mongoDB 에서 networkAccess 에서 add ip address 에서 어디에서 엑세스가능

----------------------------------------------------------------
getStaticPaths
-이 함수들은 프리 렌더링 페이지에 데이터를 패치하도록 합니다.
-pages component file 에서 export 
-프리 제너레이트 하지 않은 페이지인 ID로 입장하면 404 에러를 보게 되기때문에 사용
-객체(모든 동적 세그먼트 벨류가 있는 객체)를 리턴하는 일을 함
-객체는 paths 키가 있어야 함 배열이죠. 그리고 배열에는 객체가 여러 개 있어야 함
동적 페이지 버전당 객체가 하나여야 함 이 객체는 params 키를 가짐 꼭 필요한 것임
이건 모든 키 밸류 쌍을 가진 객체임 동적 페이지로 이끔 따라서, 동적 페이지 세그먼트가 
여러 개 있다면 네스트 객체에 키가 여러 개 있는 것임
-fallback
--특정 paths 를 정의함
--fallback:false 로 하면 일부가 아닌 모든 meetupId value 를 포함
즉, 사용자가 지원되지 않는 걸 입력하면, 예를 들어 m3 같은 것이라면 404 에러가 뜸
--fallback:true 로 하면 넥스트 JS가 페이지를 만들 것임  들어오는 요청에 관해서, 
서버에서 미트 업 ID로 동적으로 만들 것임
--동적 페이지에서 필요한 함수고, 넥스트 JS에게 어떤 동적 매개변수 밸류의 어떤 페이지가 
프리 제너레이트되어야 하는지 설정 할 수 있음
--fallback을 true나 blocking으로 설정하면 여기서 지정한 경로 목록이
완전하지 않을 수 있고 더 유효한 페이지가 있을 수 있음을 NextJS에 알려줌
따라서 fallback을 true 또는 blocking으로 설정하면 NextJS가 바로 페이지를 
찾을 수 없는 경우 404페이지로 응답하지는 않음 대신에 fallback을 true나 
blocking으로 설정하면 요청 시 페이지를 생성한 후에 캐시에 저장하여
필요할 때 이것을 미리 생성함 true와 blocking의 차이점은 true로 설정하면 빈 
페이지가 즉시 반환되고 동적으로 생성된 콘텐츠를 풀다운함 따라서 페이지에
데이터가 아직 없는 경우를 처리해야함 blocking으로 설정할 경우는 페이지가 
미리 생성될 때까지 사용자는 아무것도 볼 수 없고 완성된 페이지가 제공됨
----------------------------------------------------------------
API Route
-HTML CODE 를 리턴하지 않고 HTTP request 를 받으며 fetch 를 post 하고 request 를 삭제
하며 JSON data 가 부착되어있다,예를 들어 데이터베이스에 데이터를 저장하고 JSON 
데이터를 리턴하게된다,따라서 넥스트 프로젝트의 일부로 API 라우트가 API 엔드 포인트를 
만들게 한다,  그리고 넥스트 앱과 같은 서버로 서브 된다
-pages folder 안에 api folder 생성하면 넥스트 JS가 여기에 저장되어 있는
자바스크립트를 골라낼 것이고  그리고 그 파일들을 API 라우트로 보내게되며 엔드 
포인트에서 요청에 의해 타겟될 수 있게된다 그리고 JSON을 받고 JSON을 리턴해야 한다
-API 라우트는 리액트 컴포넌트를 정의하고, 렌더링하거나 리턴하지 않는다 대신에 서버 
사이드 코드를 포함하는 함수를 정의하며 API 라우트는 서버에서만 돌아간다 
클라이언트에서는 아니며 디코드해도 클라이언트에게 노출되지 않는다 따라서 API 라우트에서
인증서를 사용할 수 있게되며 그리고 이 함수들은 라우트에 요청이 들어올 때마다 트리거 된다
----------------------------------------------------------------
deploy
-디플로이 하기 전에 메타데이터를 페이지에 추가해야한다
title, meta tags 를 추가 설정하여 검색엔진에 노출될 수 있도록하자
--import Head from 'next/head' 는 head section 에 head elements 를 추가
하는 구성 요소임
<Head>
  <title>{props.meetupData.title}</title>
  <meta name='description' content={props.meetupData.description} />
</Head>

vercel
-nextJS app 을 위한 호스팅 제공 업체
-배포를 시작하려면 Git repository 공급 서비스에 등록을 해야 함
Vercel을 사용하면 바로 소스 코드가 저장된 GitHub repository에 연결하여
해당 저장소에서 소스 코드를 가져와 배포할 수 있음

redeploy 할때 변경된 코드를 git 에 add . & commit & push 하면 
자동으로 push 한 main 브렌치가 주시하여 변화가 감지될때마다 자동으로 
building 과 redeploying 을 시작함
================================================================
리액트 앱 애니메이션
-정적인 스타일과 컴포넌트 동적인 스타일과 컴포넌트
----------------------------------------------------------------
-join(' ') method 를 사용 할땐 공백을 넣어줘야한다
----------------------------------------------------------------
-@keyframes
----------------------------------------------------------------
-Transition component
트랜지션 컴포넌트로 랩핑하면 랩핑된 요소를 제어 할 수 있음 특히 애니메이션,
--in attr : 트랜지션 컴포넌트로 감싸진 요소들을 보일지 말지 결정함
--네가지 내부 state를 관리합니다, entering, entered, exiting, exited
--transition 컴포넌트에서 설정하는 timeout 에 따라 확인하는 입장하고 
퇴장하는 상태가 지속되는 시간의 길이가 결정됨, state가 얼마동안 지속될지
사용하는 시간의 길이 말이죠 만약에 timeout 을 재생하는 애니메이션 보다 훨씬 
짧게 설정하게 된다면 그러면 애니메이션을 선제적으로 종료하게됨, state를 
너무 일찍 전환했기 때문임 ‘exited’으로 전환해버림 그렇다는 것은 요소가 
제거된다는 의미고, 이것이 원하는 동작이 아닐 수 있음 그렇지만 이렇게 
설정한다고 해서 반드시 문제가 되는 것은 아님 하지만 염두에 둘 수 있는, 
경우에 따라서 설정해줄 수 있는 한가지가 timeout 임 현재 timeout은 밀리초 
밖에 안되는 숫자로 정의된 값이지만 하지만 입장과 퇴장에 대해서 다른 
타이밍을 원한다면요,이것을 설정해 줄 수 있음
-애니 메이션이 시작하거나 진행중이거나 끝날때 활용할 수 있는 attrs
/* Entering mode 에 들어가기 직전 실행됨 */
onEnter={()=> console.log('onEnter')}
/* Entering mode 에 들어가고 나서 실행됨 */
onEntering={()=> console.log('onEntering')}
/* Entered mode 에 들어가고 나서 실행 */
onEntered={()=> console.log('onEntered')}
/* Exiting 들어가기 직전 실행 */
onExit={()=> console.log('onExit')}
/* Exiting mode 에 들어가고 나서 실행 */
onExiting={()=> console.log('onExiting')}
/* Exited mode 들어가고 나서 실행 */
onExited={()=> console.log('onExited')}
----------------------------------------------------------------
CSSTransition
-CSSTransition은 태그 사이에 어떠한 함수도 사용하지 않음
-classNames attr 
다른 속성에서 사용 했었던 className이 아님 classNames 임, 왜냐하면 여기서 
래핑된 요소에 대해서 추가해야 하는 cssClasses 를 정의하기 때문임 따라서 이 
div 부분에 대해서, 전환의 상태에 따라 말이죠 이 요소에 있는 클래스는 항상 
유지됨, 이 경우엔 “Modal” 이겠죠, 그렇지만 이것과 새로운 클래스들을
병합함 이러한 클래스들의 몸통이라 할 수 있는 것을 정의할 수 있음, 예를 들어 
변수명을 “fade-slide”라고 하면 이러면 이제, CSSTransition 컴포넌트가 
자동으로 몇 개의 css 클래스들을 순회 하면서 클래스들을 여기 div에 
병합함, 물론 래핑된 div 또는 래핑된 모든 요소에 병합함 CSSTranstiion 또는 
일반 Transition의 상태에 따라서 말이죠 컴포넌트가 순회하는 클래스들이 
몸통임 따라서 이 경우는 fade-slide가 됨, 그리고 -enter 클래스 경우 
들어가기 시작하는 시점에 바로 연결됨 그 다음, enter-active 클래스 경우 
entering 모드에 있는 동안은 연결된 상태로 유지됨 따라서 이 400 밀리초 동안 
지속되는 동안 말이죠, 한편 -enter 클래스는 한 프레임이 직후에 제거됨, 또 
-exit 클래스 또한 연결됨 나가기 시작하는 시점에 말이죠, 그리고 exit-activ 
클래스
--classNames={{
        enter: 
        enterActive:
          exit:
          exitActive:
          appear: /* appear & appearActive 는 무언가 처음으로 DOM 에 
          렌더링될때 사용됨 예를 들면 버튼을 클릭 여부에 따르는 것*/
          appearActive:
      }}
----------------------------------------------------------------
--timeout attr timeout은 단순히 entering에서 entered로 그리고 
exiting 에서 exited로 전환할 때 시간이 얼마나 걸리는지를 결정하는것임
(그래서 이들 사이에서 애니메이션을 적용함)
timeout을 300이라고 하면 이것은 밀리초로 해석된다 이렇게 해주면, 이 
Transition 컴포넌트 안에서 중괄호로 동적인 무언가를 렌더링할 수 있다
왜냐하면 이 안에 실제로 함수를 렌더링해야하기 때문, 이것이 결국에는 
Transition 컴포넌트가 반환하는 것이 됨, 이 함수 안에 사용할 수 있는 값들 
또는 정확히 말하자면 단 하나의 값은 state 임 따라서 가장 간단한 형태로 
할 수 있는 것은, 단순히 => 함수를 사용하는 것, 이것이 중괄호가 필요한 이유
----------------------------------------------------------------
TransitionGroup Component
import TransitionGroup from 'react-transition-group/TransitionGroup'
-List 에 아이템 추가 및 제거에대한 애니메이션 적용하기에 좋음
-리스트를 반환하는 곳에서 사용할 수 있습니다, 동적 리스트 요소가 있는 곳
(순서 없는 리스트에서 처럼)
-TransitionGroup이 특별한 점 이자 유일하게 이것이 하는 일은 여러 아이템을 
취급할 수 있다는 것, 이것이 리스트의 변경된 요소를 알아냄, 제거 되었는지 
추가 되었는지, 그리고는 일일이 in 속성을 설정 해줌, 감싸 놓은 Transition 
또는 CSSTransition 컴포넌트에,  우리가 in 속성을 제어하지 않아도
되도록 함, 왜냐하면 당연히 in 속성을 제어 할 수 없기 때문임 끝내 취급하게 
되는 것이 동적 리스트이기 때문이죠 그런 점에서, in 속성에 대한 관리가 주요 
차이점이라고 할 수 있음
-이 패키지는 리액트에서 애니메이션 효과를 적용하는데 사용하는 모든 
컴포넌트들을 제공함, DOM에서 요소를 제거하거나 추가할 때 있어서 시간과 
관련된 것들임 이 패키지에 대한 대안이 존재함 인기있는 대안 중 하나는 React 
Motion입니다
----------------------------------------------------------------
ReactMotion
-애니메이션 효과가 걸리는 시간을 수동으로 정의하지 않음 대신 React 
Motion 은 현실의 물리학을 모방해서 애니메이션 효과가 걸리는 최적의 시간을 
구하려고 함 단순히 종료 및 시작 상태만을 정의할 수 있게 하고, 현실의 
물리학을 최대한 이용해서 그 종료와 시작 사이의 상태를 모방하거나 보간하기를 
시도함

ReactMove
-React Move는 제공하는 두가지 기본 컴포넌트가 있으며 단일 아이템 및 그룹 
아이템과 노드 그룹에 애니메이션을 적용할 수 있음 React Move에서는 항상 
객체로 작업을 하게 되고, 이 객체는 애니메이션의 상태를 설명함
-몇몇의 애니메이션은 이것으로는 하기가 좀 어려울 수있음, 하지만 다른 많은 
경우에는 굉장할 수 있고 더 자연스러워 보이는 애니메이션을 효과를 줄 수도 
있음 특정한 종류의 애니메이션을 원할 경우에 말이죠 또 다른 대안 중 하나는 
React Move 임

ReactRouteTransition
-route 전환을 쉽게 생성할 수 있도록 해줌, 서로 다른 route 간의 애니메이션 
효과인것임
-React Motion을 기본으로 하고, 기본적으로 이 AnimationSwitch라는 
컴포넌트를 제공함, 이것으로 일반 RouteSwitch를 대체함, 이것은 React 
Router 버전 4와 작동할 수 있도록 만들어 졌음, AnimatedSwitch는 일반 
switch가 하는 모든 것을 동일하게 함 하지만 atEnter, atLeave, atActive 
그리고 className을 정의할 수 있도록 설정되어 있음,페이지 전환 애니메이션 
같이 route에 대한 애니메이션  효과를 줄 수 있도록함
================================================================
리덕스를 리액트 훅으로 바꾸기
-Redux 는 애플리케이션 상의 상태 관리 시스템

리액트 17 에서 18 버전으로 업데이트 내용
React 18로 업데이트
1) npm install --save react@latest react-dom@latest
2) index.js 업데이트 하기
다음 부분을
ReactDOM.render(<App />, document.getElementById('root'));
아래와 같이 변경해 주세요.
const root = ReactDOM.createRoot(document.getElementById('root'));root.render(<App />);
이렇게만 하면, 모든 사항이 최신 버전의 React로 업데이트됨

-컴포넌트가 커스텀 훅을 사용하고, 그 커스텀 훅이 useState를 사용하면, 그 
커스텀 훅을 사용하는 컴포넌트는 그 커스텀 훅을 입력해 주었을 때 재렌더링 
하게 됨,  그 커스텀 훅이 재렌더링을 유발하기 때문임


-
/*훅 밖에서 데이터를 관리, 훅 안에서는공유되지 않기 때문, 각 컴포넌트에 국한됨
각 컴포넌트는 각각의 데이터를 갖음 그렇지만 훅 밖에서 관리함으로써 이 파일을 import 하는
모든 파일 또는 그 파일 중 어떤 파일은 똑같은 공유된 데이터를 가짐*/
/*여기서 가지는 몇개의 변수는 전역적이지 않음 window 객체에 등록되지 않았습니다
하지만 이 파일에서는 존재함, 그리고 앱이 구동되는 동안에 한번만 존재하고 전체 프로그램에서 공유됨*/
let globalState = {};
let listeners = [];
let actions = {};
export const useStore = () => {}
store.js 파일을 불러오는 모든 모듈 혹은 모든 파일은 여기에 저장된 같은 값을 
사용하게됩니다 그리고 같은 파일에서 우리만의 커스텀 훅을 생성합니다
그렇지만 이 변수들은 훅 밖에서 정의 되었죠 이점이 아주 중요합니다
만약 훅 안에서 정의 되었다면 이 훅을 사용하는 모든 컴포넌트가
각각의 값을 사용하게 됐을 겁니다 그렇지만 훅 밖에서 변수들이 정의 되었기 
때문에 커스텀 훅을 사용하는 모든 컴포넌트가 같은 값을 사용하게 되었습니다
따라서 이제 훅의 로직 뿐만 아니라 데이터도 공유합니다 때로는 이것을 원치 
않을 수 있습니다만 여기서는 절대적으로 이것을 원합니다왜냐하면 이것을 통해 
전역적으로 state와 actions 그리고 listeners를 관리할 수 있기 때문입니다
listeners는 state의 변경사항이 관심거리이고 이 state의 변화는 actions에 
의해 유발됩니다 useStore 훅에서 우리는 이 모든 것을 관리합니다
useStore에서 dispatch 함수도 가집니다 이 dispatch를 호출했을 때
globalState가 업데이트되고 listeners를 호출합니다 그리고 listeners는 결국 
setState 호출을 하게 되죠 말하자면 속성을 남용하는 건데요, 술수는 아닙니다
단지 속성을 활용하는 것이죠 state를 업데이트하는 함수를 호출 했을 때
useState가 이 훅을 사용하는 모든 컴포넌트를 재렌더링하게 한다는 사실
--store.js
한 컴포넌트당 하나의 listeners를 등록했습니다, useEffect를 이용해서요
그리고 해당 컴포넌트가 파괴되면 등록도 해제되도록 했습니다 그런 다음 
store를 초기화하는 작업을 해주었습니다 여러번 호출 할 수 있도록 해주었습니다
globalState를 대체하고 actions를 대체하는 것이 아니라 항상 현재의 
globalState와 현재의 actions map를 새 데이터에 병합해줌
--products-store.js
이렇게 해주는 것은 구체적인 store의 슬라이스를 생성할 수 있도록 하기 
위해섭니다 리덕스에서 여러개의 Reducers로 하는 것과 동일하게 말이죠
한 슬라이스에서 상품을 관리하고 다른 슬라이스에서 사용자의 인증 상태를
관리하는 것과 같이요 물론 이름이 충돌하지 않도록해야합니다만, 그것이 다입니다
그래서 여기서는 actions를 설정해주었습니다 물론 여기선 actions 한개입니다
그런 다음 initStore를 호출해서 actions와 초기 state를 전달해주었습니다, 
이 globalState의 슬라이스에 대해서 말이죠 따라서 globalState와 전역적 
actions맵에 병합되게 됩니다 그러면 이 프로젝트의 아무 곳에서나 이 store를 
사용할 수 있습니다 state에 접근하거나 dispatch 함수를 사용해서 액션을 
날려서 사용
----------------------------------------------------------------
커스텀 스토어 최적화
-메인에 상품 리스트 갯수에따른 렌더링 횟수 최적화하기
ProductItem.js 에서 React.memo() 로 감싸주는 방법이있지만 이렇게해도 
횟수가 상품 갯수에따라 렌더링이 된다면 커스텀 훅에서 상태관리 훅을
사용하는 경우일 수 있다, 이럴때 커스텀 훅의 인자를 두고 value 를 true 로
넣어주고 ProductsItem.js 에서 dispatch 와 같이 action 을 날리기위해
useStore (커스텀훅) 을 사용하는 컴포넌트가있다면 ProductItem component
안에 변화를 따라갈 필요가 없다 state 의 변화가아닌 action 을 날리도록 
훅을 사용하기때문임, useEffect를 사용할 수 있는데요 shouldListen이 
참이라면 오직 참일 때만 listener를 추가하도록 확인 해줍니다
그리고 물론 우리가 변화를 따라가고 있을 때만 정리하도록 해줍니다
따라서 shouldListen이 참이라면 오직 참일 때만 이것을 정리하도록 합니다
그렇다는 것은 shouldListen은 이제 useEffect에 종속되기 때문에 추가해줌
,ProductItem으로 가서 여기 useStore에 false를 전달할 수 있습니다
이제 shouldListen의 인자값은 false입니다 그렇다는 것은 ProductItem에서 
listener를 설정해주지 않는 다는 겁니다 따라서 여기 이 아이템 이 컴포넌트는 
listener를 등록하지 않습니다 전역적 listeners 배열에 말이죠
따라서 store가 변했을때 다시 빌드 되면 안됩니다 store의 변화에는 별로 
관심이 없기 때문임,단일 상품에 대한 store의 변화는 좋아요로 설정한
것이죠, 이 좋아요는 어쨌든 이 ProductItem에 접근하게 되기 때문에
왜냐하면 이것이 우리가 Products.js 파일에서 따라가고 있는 것이죠
state.product.map() 으로 상품 리스트를 다시 빌드 합니다 어떤 상품에 좋아요 
표시를 하면 말이죠 렇기 때문에 이 특정 ProductItem은 어쨌든 새로운 prop을 
가지게 되고 이것은 React.memo를 통과해서 이 단일 상품이 다시 빌드 됩니다
하지만 다른 상품들은 그렇지 않음, 이로써 처음 화면에 렌더링할때는 상품 목록
에대한 갯수만 큼 렌더링되지만 단일 좋아요 버튼을 누른 상태는 한번만 렌더링됨
================================================================
리액트 앱 테스트 react app test
-자동화된 테스팅은 추가적인 코드를 작성해서 이 코드가 실행되면서 다른 
애플리케이션의 메인 코드를 테스트합니다 
-자동화된 테스팅의 장점은 전제 애플리케이션을 자동으로 테스트하는 코드를 
작성하기 때문에 항상 모든 것을 테스트할 수 있다는 것이죠, 어떤 것을 
바꾸더라도요 자동적으로 전체 애플리케이션을 테스트 할테니까요, 많은 시간이 
걸리지도 않습니다, 이러한 테스트를 작성하고 자동화 테스트요, 이것은 앱의
서로 다른 개별 구성요소에 대한 테스트를 합니다 그런 다음 이 모든 개별 
구성요소들을 다같이 테스트합니다 코드를 변경할 때마다 말이죠 가끔씩 앱의 
일부만을 테스트하는 것이 아니라요 매우 기술적이지만 모든 것을 상시 테스트할 
수 있습니다 수동 테스팅과 함께하면 오류들을 훨씬 더 일찍 잡을 수 있고
더 나은 코드를 작성해서 애플리케이션에 제공할 수 있음

테스트 유형
-단위 테스트 Unit test
단위 테스트는 애플리케이션의 가장 작은 단위에 대한 테스트를 작성하는 겁니다
따라서 함수들이요, 애플리케이션에서 사용하는 개별 함수들을 테스팅 하는 겁니다
또는 리액트 앱의 경우엔 애플리케이션의 다른 컴포넌트와 독립적으로 일부 
컴포넌트를 테스팅 하는 것이죠, 따라서 프로젝트에는 일반적으로 많은 단위 
테스트가 포함됩니다, 애플리케이션을 구성하는 모든 단위, 모든 함수 및 
컴포넌트를 테스트 하기를 원하기 때문입니다 그렇기 때문에 단위 테스트는 가장 
일반적이고 중요한 종류의 테스트입니다 아이디어는 단순히 모든 개별 단위를 
자체적으로 테스트 하면 전체 애플리케이션도 작동
-통합 테스트 integration Tests
통합테스트는 여러개의 구성 요소의 조합을 테스트합니다 예를 들어 여러 
구성요소가 함께 작동 되는지를요 프로젝트에는 일반적으로 몇가지 통합테스트가 
포함됩니다 하지만 단위테스트 만큼 많지는 않습니다 이번 섹션을 통해서 
보시겠지만 리액트 앱을 태스팅 할 때 단위테스트와 통합테스트를 구별하는 것이 
항상 쉬운 것은 아닙니다 흔히 컴포넌트를 테스트할 때 한 컴포넌트가 다른 
컴포넌트들도 사용하기 때문,일반적으로 통합테스트도 매우 중요합니다
하지만 단위테스트 보다는 통합테스트의 수가 적죠
--통합테스트는 하나 이상의 유닛, 하나이상의 컴포넌트가 관여돼면 조건 성립
하지만 자체적 논리가 없는 wrapper 컴포넌트를 다루는 상황엔 정확한 표현아님
-전체 테스트 End-to-End (e2e) Tests
전체 애플리케이션도 실제로 작동 하는지 확인하기 위해서 이 모든 단위들을 
모아서 통합테스트를 해볼 수 있음, 
애플리케이션의 전체 워크플로우를 테스트하는 것이라 할 수 있습니다
전체 시나리오를 말이죠, 사용자가 로그인하고 특정 페이지로 이동하는 것과 
같이 말이죠 실제로 사람이 여러분의 웹사이트에서 수행하는 작업을 재현하는 것을
목표로 합니다 수동 테스트로도 하는 것을 단지 자동화하는 것이죠 전 구간 
테스트가 가장 중요한 테스트처럼 들릴지 모르지만 확실히 중요하긴 합니다
그렇기 때문에 전 구간 테스트를 실제로 작성하기도 하고요 그렇지만 
단위테스트와 통합테스트 만큼 많지는 않습니다 단위 및 통합 테스트가 잘 
작동한다면 전제적으로 앱이 잘 작동한다고 꽤 확신할 수 있기 때문이죠
단위 및 통합 테스트가 단순히 더 테스트 하기도 쉽고요 보통 더 빠르고 
집중적입니다, 그리고 가능한 모든 시나리오를 테스트하는 것이 훨씬 쉽습니다
모든 단위에 대해서 서로 다른 시나리오를 테스트해서 말이죠, 앱을 전체로 보고 
가능한 모든 시나리오를 제시하는 것 보다 말이죠 보통 이것이 전 구간 
테스트에서 하는 것이죠 이것들도 중요합니다 그러나 기본적으로 수동으로 
수행하는 작업이기도 하므로 전 구간 테스트 수가 더 적습니다

테스트할때 생각해야할 것들 두가지
-어떤것을 어떻게 테스트 할지

테스트 도구
두가지 도구는 모두 이미 설치 및 설정이 되어 있습니다 create-react-app으로
생성한 프로젝트에서 작업할 경우
-jest :테스팅 코드를 실행하고 결과를 확인
-react testing library : 리액트 앱에서 컴포넌트를 렌더링하고 시뮬레이팅

test.js
-app component test file setting 
--ex App.js test, App.test.js 로 테스팅 파일과 컴포넌트 파일의 이름 일치

테스트 진행
-개발 서버를 실행하는 스크립트가 있었듯, 스크립트가 필요
-테스트 스크립트 진행은 터미널창에 npm test 로 실행
세 가지 A를 사용해 테스트를 작성하는 거죠.첫 번째 A는 '준비'를 의미합니다.
우리는 테스트를 설정하고자 하는 건데 예를 들면, 테스트하고자 하는 컴포넌트를
렌더링하길 원하는 거죠. 요구된다면 추가적인 설정도 할 수 있습니다.
두 번째는 '실행'입니다. 실제로 테스트하고자 하는 걸 하는 겁니다.
예를 들면, 버튼 클릭을 시뮬레이션 해보고 싶다면 두 번째 단계로 테스트를 
실행하는 거죠. 지금 여기서 할 건 아니지만 여러분이 나중에 테스트에서 자주 
하게 될 겁니다. 나중에 우리도 할 거예요. 마지막 단계이지만 중요한 세 번째는
결과를 '단언'하는 것입니다. 예를 들면, 브라우저상에서 보이는 아웃풋을 
검토하는 거죠. 그런 다음에 우리의 예상과 같은지 보는 겁니다.

index.js
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
인덱스 파일은 새 createRoot API 를 사용해 애플리케이션을 렌더링해야함

/* 렌더링 된 가상 DOM 또는 가상 화면에 액세스할 수 있게 해주는 screen */
import {render, screen} from '@testing-library/react'
/*첫 번째 인자는 테스트에대한 설명
* 두 번째 인자는 함수(실제 테스트 및 코드를 포함하는 포인트인 익명함수)*/
test('renders learn react link', () => {
  render(<App />);/*App.js 에 테스트*/
  const linkElement = screen.getByText(/learn react/i);/*내부에서 렌더링된 텍스트를 사용해 엘리먼트를 식별함*/
  /*문서에서 learn react 가 있다면 테스트는 성공함*/
  expect(linkElement).toBeInTheDocument();/*문서에있는지 확인*/

import Greeting from "./Greeting";
import {render, screen} from '@testing-library/react'
test('greeting component test', () => {
	render(<Greeting />)
	const helloWorldElement = screen.getByText('Hello World!', {exact: false})	/*엘리먼트 존재유무, 정밀하지않고 포함되어있어도 검색가능*/
	/*테스트 결괏값을 전달할 수 있는 expect 함수
	* 이 함수는 숫자든 문자열이든 뭐든 될 수 있음*/
	expect(helloWorldElement).toBeInTheDocument()
	/*여러 가지 matcher 함수가 있는데 여기 toBeInTheDocument 함수는 여기에 있을 것으로 예상하는
	HTML 엘리먼트가 문서 안에 있는지 확인하는 함수임 matcher 함수인 toBeInTheDocument에 .not을 추가해
	반대로 확인할 수도 있음, 만약 이 엘리먼트가 문서 안에 없기를 바란다면 그런 경우에는 텍스트로 된
	query 함수를 사용하면 됨, 엘리먼트가 발견되지 않으면 getByText는 실패할 테니까요*/
	/*expect(helloWorldElement).not.toBeInTheDocument()*/
})

tests 와 Test Suites
-다수의 다른 테스트를 서로 다른 테스트 suite에 넣어서 그룹화하고 정리함
-예를 들어, 애플리케이션 내의 하나의 특징 또는 하나의 컴포넌트에 속하는 
모든 테스트는 한 테스트 suite 그룹에 들어갑니다. 그리고 글로벌한 describe 
함수를 사용해 그러한 테스트 suite를 생성하는데요. test 함수처럼 이것 또한 
글로벌하게 사용할 수 있는 함수임, 
-describe
describe Fn 에는 두 매개변수 중 첫 번째 매개변수에는 설명이 옵니다. 서로 
다른 테스트들이 어디에 속할지에 관한 카테고리 설명에 해당하죠. 그래서 
여기에는 이렇게 'Greeting'이나 'Greeting component'라고 쓰는데 확실히 
말씀드리면 'Greeting component'에 속하는 테스트들을 얘기하는 거예요. 그런 
다음 두 번째 매개변수에도 익명의  함수가 오는데 이 함수에는 자체 테스트 
코드를 쓰지 않고 다른 테스트들을 넣습니다
-
/*이 테스트를 이 describe 에 추가해줍니다. 이렇게 하나의 suite에 한 테스트가 옵니다. suite를 여러 개 가질 수도 있으며
suite마다 테스트도 여러 개 가질 수 있습니다. 이제 이걸 저장하면 이 설명 텍스트가 아직도 있는 게 보이실 텐데
이건 이제 테스트 그룹 이름... 그러니까 테스트 suite 이름 하에 들어가 있으며 이제 하나의 테스트 suite와
하나의 테스트가 있는 게 보이실 겁니다. 전처럼 분명한 세트 suite가 없다면 자동으로 suite 하나를 갖게 될 테지만
지금은 명확하게 이름 붙여진 suite가 있죠. 이게 괜찮은 방법인 게 여러분의 애플리케이션이 점점 커질수록 아마 테스트들을 이렇게 그룹화함*/
describe('Greeting component', () => {
  test('greeting component test', () => {
    render(<Greeting />);


it - 개별 테스트를 수행합니다. test 메서드와 동일합니다.

userEvent
-import {userEvent} from '@testing-library/user-event'
-실제 화면에서 사용자 이벤트를 작동시키도록 돕는 객체입니다.
단순히 userEvent를 사용해서 전형적인 이벤트들을 사용할 수가 있는데
클릭, 더블 클릭, 호버링, 인풋에 타이핑하기와 같은 것들이 이에 해당함
-click은 적어도 하나의 매개변수가 필요한데요. 클릭을 시뮬레이션 해볼 수 있는
엘리먼트가 필요함

getByRole()
-element 가져올때 사용
-특정된 역할에대해 하나를 초과하는 아이템이있다면 작동하지 않음이럴때
getAllByRole() 사용함 ex List 와 같이 하나이상의 아이템있을때 사용
findAllByRole()와 차이점은 getAllByRole 은 비동기로 요소를 즉시 찾으려함
findAllByRole 은 get 쿼리 대신 사용하는 find query 들은 프로미스를 반환함
findAllByRole에 대한 세 번째 인자도 특정할 수 있습니다.두 번째 인자는 
exact 등을 설정할 수 있게 해줍니다.세 번째 인자는 또 다른 객체로서
여기서 timeout 기간을 정할 수 있습니다.디폴트는 1초입니다.1초 후에도 
아이템이 존재하지 않는다면여전히 실패하는 겁니다.여기서는 디폴트 1초도 
충분할 겁니다.늦어도 1초 안에는 아이템들을 가져올 수 있을 겁니다.그리고 
가장 중요하게는렌더링 된 컴포넌트를 즉시 찾는 게 아니라일정한 시간이 지난 
후에 찾을 수 있는지를 따집니다.
getByText()
- text 가 찾아지지 않는다면 에러 발생
toBeInTheDocument()
-문서에서 찾을때 사용
toBeNull()
-NUll value 인지 확인할때 사용
queryByText()
-element 가 찾아지지 않으면 null 반환

-
일반적으로는 서버에 HTTP 요청을 전송하지는 않습니다. 요청을 전송하지 않는 
이유는 첫째, 많은 네트워크 트래픽을 일으켜서 서버가 요청들로 인해 과부하될 
것이기 때문입니다. 특히 많은 요청에 대한 많은 테스트가 존재한다면요.
둘째, 데이터를 가져오지는 않지만, 일부 컴포넌트가 서버로 포스트 요청을 
전송한다면 테스트로 인해 데이터베이스에 데이터가 삽입될 겁니다.혹은 서버의 
내용이 변경될 수도 있습니다. 왜냐하면 그러한 종류의 요청이 전송되는
컴포넌트와 시나리오도 테스트해야 할 테니까요. 물론 테스트하면서
그런 일이 생겨서는 안 되겠죠. 서버의 내용을 변경시키는 요청을 보내서는 안 
될 겁니다. 그러므로 테스트를 작성할 때 보통 취하는 방식은 진짜 요청을 
전송하지 않거나 혹은 일종의 테스팅 서버로 요청을 전송하는 겁니다. 둘 다 
가능한 방식임

-
테스트를 작성할 때는 내가 작성하지 않은 코드를 테스트해서는 안 됨

-
fetch가 성공적으로 요청을 전송하는지를 테스트해서는 안 됩니다. 대신 전송된 
요청의 서로 다른 결과에 따라서 컴포넌트가 올바로 작동하는지 테스트해야죠.
즉, 응답 데이터를 받았을 때 컴포넌트가 올바로 작동하는지 테스트해야 합니다.
또한 에러가 발생했을 때도 제대로 작동하는지 확인해야겠죠. 하지만
요청 전송에 성공하는지는 테스트하지않음 그러므로 브라우저에 내장된 이 fetch 
함수를 소위 mock 함수로 대체해야 합니다. 내장 함수를 덮어쓰는 더미 함수를 
사용하는 겁니다. 우리가 원하는 바를 수행하면서도 진짜 요청을 전송하지 않는 
더미 함수를 쓰는 거죠. 그러면 테스트 중에 컴포넌트가 실행될 때 mock 더미 
함수가 사용될 겁니다. 내장된 진짜 함수가 아님

















```
