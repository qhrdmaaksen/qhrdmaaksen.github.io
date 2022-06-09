---
layout: post
title: "리액트-리덕스-넥스트-타입스크립트"
---

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

  


















```
