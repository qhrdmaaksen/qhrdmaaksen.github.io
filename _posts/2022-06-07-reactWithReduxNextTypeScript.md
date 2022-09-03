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
* -리액트에게 이 함수가 커스텀 훅임을 알려주며 리액트가 해당 함수를 훅의 규칙에 따라 사용하겠다고 보장해줌(내장 훅과 같은 방식으로 쓰겠다는)*/
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

/*커스텀 훅을 사용하는 컴포넌트에서, counter 의 상태를 사용 가능하게 하려면, 간단히 이를 반환만 하면 됨
-커스텀 훅에서는 필요한 무엇이든간에 반환이 가능함,배열도 가능하고, 객체나 숫자 등*/
return counter;
};
export default useCounter ;

업그레이드된 ForwardCounter.js 와 BackwardCounter 동시 사용 가능 커스텀 훅
/*커스텀 훅은 무조건 use 로 시작해야함(룰)
* -리액트에게 이 함수가 커스텀 훅임을 알려주며 리액트가 해당 함수를 훅의 규칙에 따라 사용하겠다고 보장해줌(내장 훅과 같은 방식으로 쓰겠다는)*/
/*const useCounter = (counterUpdateFn) => {/!*counter 갱신 fn 을 매개변수로 넣어주며 이 갱신함수를 실행해주면됨*!/*/
const useCounter = (forwards = true) => { /*전달할 값을 true 로 지정하여 setCounter 로 더할지 뺄지 조건문 넣어줘서 ForwardCounter,BackwardCounter 로직 사용*/
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
    /*setCounter(counterUpdateFn());/!*여기에서 받게 될 인자는 실행 가능한 함수이며 이는 이전의 카운터를 받고 새로운 카운터를 받아들임*!/*/
  }, 1000);

  return () => clearInterval(interval);
}, [forwards]);/*매개변수로서 받게 되는 값이기 때문에 이를 의존성으로 추가해야 함*/

/*커스텀 훅을 사용하는 컴포넌트에서, counter 의 상태를 사용 가능하게 하려면, 간단히 이를 반환만 하면 됨
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
ref로 구현하는 것도 불가능하진 않지만 이렇게 깔끔하진 않음 ref로도 할 수는 있다 nameInputRef.current.value =’’로 ref에 저장된 input 요소에 접근해 빈 문자열로 만들 수 있는데 바람직한 방법은 아님, 이 부분을 주석처리하고 실행하면 보시다시피 작동은 하지만 바람직하진 않음 이는 DOM을 직접 조작하는 
것으로 바닐라 자바스크립트 코드를 이용해 DOM에 접근해 무언가 변경하는 
것인데 보통 지양해야 하는 방법임, 리액트로만 DOM을 조작해야 함

-event.preventDefault()
--브라우저에서 작동하는 js 를 다루고있기 때문에 기본적으로 브라우저는 이 폼 안에 있는 버튼을 통해서 폼이 제출되면
웹사이트를 제공하는 서버로 HTTP 요청을 보내게 되며, 이 과정은 자동적으로 일어나며 브라우저가 자동적으로
웹사이트를 제공하는 서버로 HTTP 요청을 보냅니다 이 과정에서 문제는 실제로 요청을 처리할 서버가 없고
HTML과 자바스크립트만 전송하는 정적 서버만 있다는 점에따라 따라서 이 요청이 보내지지 않도록 해야합니다
따라서 이 event 객체는 onSubmit 속성에있는 함수와 바로 연결이 되어있는데 onSubmit으로 연결된 이 event 객체에서
브라우저의 기본 행동인 HTTP 요청을 보내지않고 아무것도 하지 않도록 명령 함(event.preventDefault()) 이것이 필요한 이유는
HTTP 요청이 보내진다면 결국 페이지가 새로고침될텐데 이 경우에는 리액트 앱들이 전부 재시작되면서 모든 상태가
없어지게되고 원하는 대로 작동하지 않게 되기 때문, 따라서 이 부분이 매우 중요함
따라서 그 다음에 페이지가 새로고침 되지 않아서 앱이 재시작되지 않도록 하는것

바닐라 자바스크립트 
-바닐라 자바스크립트(Vanila Javascript)란, 라이브러리나 프레임워크를 사용하지 않는 순수한 형태의 자바스크립트를 의미
-바닐라 자바스크립트는 프로그래밍 문제를 해결하기 위해 어떤 도우미 라이브러리나 프레임워크를 사용하는 것보다 코어 API나 유틸리티를 사용하여 코딩하는 방식을 의미
-오늘날 대부분의 자바스크립트 프로그램은 제이쿼리, 리액트, 앵귤러 등 다양한  프레임워크 및 라이브러리에 의해 구현된 기능을 사용하고 있는데, 사실 이러한 라이브러리의 기능들은 모두 자바스크립트 언어를 기반으로 구현이 되어 있기에, 바닐라 자바스크립트 만으로도 구현이 가능한 것들임


blur
-input 요소가 포커스를 잃었다는 의미

================================================================
&& 논리 연산자 잘 생각해보기
const [enteredName, setEnteredName] = useState('')
/*enteredName 이 빈 문자열이아니라면 true*/
/*.trim()을 이용해 입력 값의 처음부터 끝 사이에 있는 공백문자를 없앨 수 있음*/
const enteredNameIsValid = enteredName.trim() !== ''
/*바로 위에 코드 에서 빈 문자열이라면 enteredNmaIsValid 에는 false,
!enteredNameIsValid 는 true 로되고 enteredNameTouched 도 true 라면 nameInputIsInValid 는 true 가되며 nameInputIsInvalid 는 true*/
const nameInputIsInvalid = !enteredNameIsValid && enteredNameTouched
 

-입력이 많을때는 전체 양식이 유효하도록하면 좋다
--ex 10 개중 1 개라도 유효하지않다면 전체가 유효하지않도록
/*formIsValid state 를 지우고 아래와 같이 하면 useEffect 가 필요없어지며 코드 간결화, enteredNameIsValid 가 true 일경우 form 전체 유효성을 true 설정*/
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

-앱 와이드: 다수의 컴포넌트가 아니라 애플리케이션의 모든 컴포넌트에 영향을 미치는 상태도 있는데
그런 경우를 우리는 앱 와이드 상태라고 부를 수 있음,예를 하나 들자면 사용자 인증

-크로스컴포넌트:모달안에 버튼을 통해 뭔가 표시하고 감추면 다수의 컴포넌트가 협력하는것이며 
useState or useReducer 를 이용하는데 이럴땐 props 를 주변에 넣어 props 체인을 구축한상태

-리액트 컨텍스트:리액트의 내장 기능이며, 크로스 컴포넌트 상태나 앱 와이드 상태를
쉽게 관리하도록 해줌, 그렇게 크로스 컴포넌트와 앱 와이드 상태 관리를 단순화 할수있음
--단점:컨텍스트를 사용하면 설정이 아주 복잡해질 수 있고 리액트 컨텍스트를 이용한 상태 관리가
상당히 복잡해질 수 있다는 점 (복잡한 경우 여러개의 컨텍스트프로바이더를 중첩사용)
---단점02:성능에대한 문제(데이터가 자주 변경되면 성능에 좋지않음)

-리덕스는 컨텍스트와같이 크로스 컴포넌트 상태나 앱 와이드 상태를 관리하도록 도와줌,리덕스는 컨텍스트의 대안

-리덕스로 작업할때는 절대 기존의 state 를 변형해서는 안되며 대신 새로운
state 객체를 반환하여 재정의 하면된다

-식별자는 절대적으로 오타를 내면 안되기때문에 보통 
export const 상수명 = 'type 명' 으로 보내고 사용하는쪽에 import 하여사용

-리덕스는 중앙 저장소를 갖게되며 데이터를 저장해서 컴포넌트 안에서 사용가능
--컴포넌트는 중앙저장소를 구독하게되며 데이터가 변경될때마다 저장소가 
컴포넌트에 알려주게됨

-컴포넌트는 저장소에 있는 데이터를 직접 조작하지 않음,대신 리듀서 개념을 이용(리듀서는 변형을 담당하여,useReducer hook 과는 다름)
--리듀서 함수는 입력을 받아 입력을 변환하고 줄이는 함수임
---예를 들면 숫자로 된 리스트를 그 숫자들의 합으로 줄일 수 있음
----리듀서 함수는 입력을 변환해서 새로운 출력, 새로운 결과를 뱉어냄
-----useReducer는 훅이 사용하고 리듀서 함수는 리덕스도 사용함,리듀서 함수가 있고 그게 저장소 데이터의 업데이트를 담당함, 그리고 그 데이터를 
구독하는 컴포넌트가 있음

컴포넌트와 리듀서 함수 연결
-액션이 있고 컴포넌트가 액션을 발송하면 컴포넌트가 어떤 액션을 트리거한다고 말할 수도 있으며 액션은 사실 단순한 자바스크립트 객체이고
그게 리듀서가 수행해야 할 작업을 설명하게 됨,그래서 리덕스는 그 액션을 리듀서로 전달하고 원하는 작업에 대한 설명을 읽게 되며 리덕스가 그걸 직접 하지는 않지만 액션들을 리듀서로 전달해서 그 액션이 원하는 걸 리듀서가 하게 
됨, 그리고 나서 리듀서는 새로운 상태를 뱉어내고 그게 실제로 그 중앙 데이터 저장소의 기존 상태를 대체하게 됨,데이터 저장소의 상태가 업데이트되면
구독 중인 컴포넌트가 알림을 받게 되고 컴포넌트는 UI를 업데이트할 수 있게 되는 작동방식임

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
* -구독 함수는 state 가 update 될때마다 trigger 되면 getState 를 통해 최신 상태 스냅샷을 얻음*/
const latestStore = store.getState()
console.log(latestStore)
}
/*subscribe 를 호출해서 리덕스가 구독함수를 인식하고 state 가 update 될때마다 함수를 실행하도록함함
* -subscribe 메소드는 counterSubscriber 함수를 취함
* -리덕스는 데이터와 저장소가 변경될때마다 counterSubscriber 함수를 실행하게해줌*/
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
  /*reducers 가 아닌 reducer, 이유는 createStore 와 configureStore 둘 중에서 무엇을 사용하든,
  리덕스에는 전역 상태를 담당하는 단 하나의주요 리듀서 함수만 있어야 해서
  * -모든 리듀서 메서드를 갖추고있는 counterSlice.reducer 는 전역 state 를 담당하는 주요 리듀서로 사용가능
  * --만약 규모가 큰 앱에 slice 가 여러개라면 리듀서 key value 대신 객체를 설정해서 그 객체 안에 원하는 대로 속성 이름을 정하며
  * ---key value 를 설정해서 프로퍼티들의 값이 또다른 리듀서 함수가 됨, 결국 리듀서 맵을 생성하는 것이며 맵은 주요 리듀서의 값이되고
  * ----보이진 않지만 configureStore 의 모든 리듀서를 하나의 큰 리듀서로 병합함
  */
  reducer: counterSlice.reducer,
});
/*createSlice 함수의 리듀서 영역에 있는 메서드 이름과 매칭
* -actions 의 객체에서 이런 key 에 접근할 수 있으며 그러면 리듀서 메서드에 접근할 필요가 없어짐, 대신에 Redux toolkit 에 의해
* --자동으로 생성된 메서드가 생기고 그 메서드가 호출되면 액션 객체가 생성될 것이며 이런 메스드는 액션 생성자라고 불림
* ---액션 객체를 생성해주며 이런 객체는 이미 액션마다 다른 고유 식별자와 함께 type 프로퍼티를 가지고 있음, 안 보이게 뒤에서 자동으로 생성됨
그래서 액션 식별자에 대해 신경 쓸 필요 없어짐 직접 액션 객체를 생성할 필요가 없음 단지 createSlice 의 actions key 및 객체를 사용하면 됨
* 액션 생성자 매서드를 실행해서 리듀서 메서드와 이름이 같으면 액션을 전달하며 그러면 최종적으로 서로 다른 매서드를 작동키는 원리*/
export const counterActions = counterSlice.actions
export default store;


 /* -state.counter.counter 의 앞 counter 는 리액트 리덕스에게 slice 에 접근한다는 걸 알려주기 위함이고
   * --slice 의 리듀서가 만든 state 를 말함, 그리고 그 상태 slice 에서 가지고 있는 프로퍼티 이름이 counter
   * --- 만약에 counter 가 아닌 다른 이름이었다면, 가령 value 라면, Counter 컴포넌트에서 state.counter.value 가 됨*/
  const counter = useSelector(state => state.counter.counter);

================================================================
동기 비동기 차이
-비동기는 동시에 일어나지 않는다를 의미합니다. 요청과 결과가 동시에 
일어나지 않을거라는 약속입니다. 
-동기는 말 그대로 동시에 일어난다는 뜻입니다. 요청과 그 결과가 동시에 일어난다는 약속인데요. 바로 요청을 하면 시간이 얼마가 걸리던지 요청한 자리에서 결과가 주어져야 합니다.
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
       * -redux toolkit 이아닌 redux 만 사용할 경우 push 는 기존 state 의 기존 배열을 조작하기에 사용하면안됨
       * --redux toolkit 에는 내부적으로 immer 가 기존 state 를 조작하지 않도록 불변성 유지되기에 문제되지않음*/


리덕스의 부수효과 및 비동식 코드

-리듀서는 순수함수이며 부수효과도 없으며 동기식이어야한다

-리듀서에서 fetch 를 사용해서 백엔드로 요청을 보낼수 없다

-리듀서에서 부수효과 및 동기 or 비동기는 수행면안된다

put 과 post 의 차이 

-새 데이터가 데이터 목록에 추가되지 않고 기존의 데이터를 오버라이드 함
-put 요청을 보낼때 장바구니를 수신 데이터로 오버라이드함

================================================================
멱등성
-동일한 요청을 한 번 보내는 것과 여러 번 연속으로 보내는 것이 같은 효과를 지니고, 서버의 상태도 동일하게 남을 때, 해당 HTTP 메서드가 멱등성을 가졌다고 말합니다. 다른 말로는, 멱등성 메서드에는 통계 기록 등을 제외하면 어떠한 부수 효과(side effect)도 존재해서는 안됩니다. 올바르게 구현한 경우 GET, HEAD, PUT, DELETE 메서드는 멱등성을 가지며, POST 메서드는 그렇지 않습니다. 모든 안전한 메서드는 멱등성도 가집니다.

-멱등성을 따질 땐 실제 서버의 백엔드 상태만 보면 되며, 각 요청에서 반환하는 응답 코드는 다를 수 있습니다. 첫 번째 DELETE 요청이 200을 반환한다면, 그 이후는 아마 404를 반환할 것입니다. DELETE가 멱등성을 가진다는 것은, REST API에서 개발자는 DELETE 메서드를 사용해 "목록의 마지막 항목 제거" 기능을 구현해서는 안된다는 것입니다.
다만, 서버는 멱등성을 보장하지 않으며, 일부 애플리케이션은 잘못된 구현으로 멱등성 제약을 어길 수도 있습니다.

-GET /pageX HTTP/1.1는 멱등성을 가집니다. 여러 번 연속해서 호출해도 클라이언트가 받는 응답은 동일합니다.

    GET /pageX HTTP/1.1
    GET /pageX HTTP/1.1
    GET /pageX HTTP/1.1
    GET /pageX HTTP/1.1
-POST /add_row HTTP/1.1는 멱등성을 갖지 않습니다. 여러 번 호출할 경우, 여러 열을 추가합니다.

    POST /add_row HTTP/1.1
    POST /add_row HTTP/1.1   -> Adds a 2nd row
    POST /add_row HTTP/1.1   -> Adds a 3rd row
-DELETE /idX/delete HTTP/1.1의 상태 코드는 응답마다 달라질 수 있지만, 그럼에도 멱등성을 가집니다.

    DELETE /idX/delete HTTP/1.1   -> Returns 200 if idX exists
    DELETE /idX/delete HTTP/1.1   -> Returns 404 as it just got deleted
    DELETE /idX/delete HTTP/1.1   -> Returns 404

-PUT
HTTP PUT 메서드는 요청 페이로드를 사용해 새로운 리소스를 생성하거나, 대상 리소스를 나타내는 데이터를 대체합니다.
PUT과 POST의 차이는 멱등성으로, PUT은 멱등성을 가집니다. PUT은 한 번을 보내도, 여러 번을 연속으로 보내도 같은 효과를 보입니다. 즉, 부수 효과가 없습니다.
EX)

요청
PUT /new.html HTTP/1.1
Host: example.com
Content-type: text/html
Content-length: 16

<p>New File</p>

응답
대상 리소스를 나타내는 데이터가 없고, PUT 요청이 성공적으로 하나를 새로 생성한 경우, 출처 서버는 반드시 사용자 에이전트에게 201 (Created) 응답을 보내 해당 사항을 알려줘야 합니다.

HTTP/1.1 201 Created
Content-Location: /new.html
대상 리소스를 나타내는 데이터가 있고, 이를 요청에 포함된 자료에 준하여 성공적으로 수정했다면, 출처 서버는 반드시 200 (OK) 또는 204 (No Content) 응답을 보내 성공을 알려줘야 합니다.

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
자원을 이름(자원의 표현)으로 구분해 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미합니다.
즉, 자원(resource)의 표현(representation)에 의한 상태 전달을 뜻합니다.

자원 : 해당 소프트웨어가 관리하는 모든 것 ( 문서, 그림, 데이터, 해당 소프트웨어 자체 등 )
표현 : 그 자원을 표현하기 위한 이름 ( DB의 학생 정보가 자원이면, 'students'를 자원의 표현으로 정함 )
상태 전달 : 데이터가 요청되는 시점에 자원의 상태를 전달한다. ( JSON 혹은 XML을 통해 데이터를 주고 받는 것이 일반적 )

REST는 기본적으로 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용하기 때문에,
웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일입니다.
REST는 네트워크 상에서 Client와 Server 사이의 통신 방식 중 하나입니다.
RESTful하게 만든 API는 요청을 보내는 주소만으로도 어떤 것을 요청 하는지 파악이 가능합니다.
REST API를 간단히 요약하면
URI는 정보의 자원만 표현해야 하며, 자원의 행위는 HTTP Method에 명시한다는 것입니다.
출처: https://dev-coco.tistory.com/97 [슬기로운 개발생활:티스토리]

================================================================
URI 와 URL 차이
URI는 식별하고, URL은 위치를 가르킨다. 실세계에 빗대어 예시를 들어보자면 다음과 같다. “Charles” 는 내 이름이며 식별자(Identifier)다. 이는 URI와 비슷하지만 내 위치나 연락처에 대한 정보가 없으므로 URL은 될 수 없다
======================================================================
side effect는 React 컴포넌트가 화면에 렌더링된 이후에 비동기로 처리되어야 하는 부수적인 효과들을 흔히 Side Effect라고 말함
======================================================================
라우터 npm install react-router-dom@5 (5버전 download)
-여러 페이지를 추가할 수 있음

-동일한 단일 페이지 응용 프로그램에 URL 이 다른 여러 페이지가 있는것처럼 보이게 할 수 있음

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
화면에 표시되는 내용을 업데이트하도록 하며 모든 라우팅을 수행하고 URL을 확인하고 URL 변경을 기반으로 화면에 다른 컴포넌트를 가져오는 패키지를 원한다고 볼 수 있는데 브라우저에서 이 모든 작업을 수행하려면 해당 작업을 
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
--여전히 앵커 태그를 생성하여 클릭이 브라우저 기본값을 방지활성함, 앵커 
항목에 CSS 클래스를 설정가능 activeClassName attr 로 하면됨

-동적 라우트
path /example/:productId 로 :동적경로 세그먼트로 이페이지가 
로드되어야하는 전체 경로는 다음과 같을거라고 라우터에게 알려주는것

-파람스 useParams 특수 훅 : UseParams를 호출하면 훅은 상수에 저장할 수 
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

-중첩 라우트
다른 컴포넌트에서 라우트를 정의할 수 있으므로 다른 라우트에서도 정의할 수 
있다, 그런 다음 더 구체적인 경로 일치가 있는 경우, 더 많은 콘텐츠를 로드할 
수 있으며  기능은 더 복잡한 사용자 인터페이스를 구축하는 데 사용할 수도 
있다, 그리고 빌드하는 모든 애플리케이션에 필요한 것은 아니지만 몇 가지
애플리케이션에서는 도움이 됨

리다이렉트 Redirect
-react-router-dom 에 Redirect component
<Switch>
  <Route path="/" exact> {/*사이트 방문 시 redirect 로 to props 로 
  /welcome 으로 연결 */}
    <Redirect to="/welcome"/>
  </Route>
</Switch>  
exact 가 매우 중요, 그게 없다면 모든 라우트가 여기에서 일치하게 되고
항상 리디렉션을 하게 되며 여기 무한한 루프를 생성하게 됨
================================================================








```
