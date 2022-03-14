
---
layout: single
title: "배열 특정값 포함 여부 체크(사용할때 다시 공부하기좋다)js"
---

### 1. indexOf(), lastIndexOf()
2. includes()
3. findIndex()
4. some()
5. includes() vs some()

```html
# 자바스크립트 Object의 entries() 메소드는?
자바스크립트은 여러 타입이 있는데요 그 중에 객체 타입은 배열처럼 여러 개의 값을 가지고 있습니다. 만약 객체가 어떤 값들을 가지고 있는지 모두 확인할 수 있을까요?
이 경우 Object에 entries()를 사용하면 객체가 가지고 있는 모든 프로퍼티를 키와 값 쌍으로 배열 형태로 반환하여 줍니다. 그렇기 때문에 어떤 프로퍼티와 값으로 이루어졌는지 한 눈에 확인할 수 있겠죠.

- 모든 프로퍼티와 값을 배열로 반환함

프로퍼티뿐 아니라 가지고 있는 값도 모두 배열 형태로 변환하여 반환하게 됩니다. 

================================================================

1. indexOf(), lastIndexOf()
arr.indexOf(searchElement[, fromIndex])
arr.lastIndexOf(searchElement[, fromIndex])
 indexOf() 함수는 

배열 안에서 찾으려는 값(searchElement)과 정확하게 일치(===)하는'첫번째' element의 index를 리턴합니다. 

 lastIndexOf() 함수는 

배열 안에서 찾으려는 값(searchElement)과 정확하게 일치(===)하는 '마지막' element의 index 를 리턴합니다.

두 함수 모두 찾으려는 값이 배열에 없으면 -1을 리턴합니다.

이 특징을 이용해서 특정 값이 배열에 포함되어 있는지 확인할 수 있습니다.

================================================================

2. includes()
arr.includes(valueToFind[, fromIndex])
includes() 함수는 배열이 특정값을 포함하고 있는지의 여부를 boolean 값으로 반환합니다.

 파라미터 

valueToFind

찾으려는 값

fromIndex

검색을 시작할 index

기본값은 0

음수가 입력되면 arr.length+fromIndex로 계산

 리턴값 

배열이 valueToFind 값을 포함하고 있는지의 여부(boolean)

================================================================

3. findIndex()
arr.findIndex(callback(element[, index[, array]])[, thisArg])
 findIndex() 함수는 

배열에서 값을 찾는 조건을 callback 함수로 전달하고,

배열에서 조건에 맞는 값의 '첫번째 index'를 리턴하는 함수입니다.

만약, 조건에 맞는 값이 배열에 없으면 -1을 리턴합니다.

================================================================

4. some()
arr.some(callback(element[, index[, array]])[, thisArg])
 some() 함수는 

배열에서 값을 찾는 조건을 callback 함수로 전달하고,

배열에 조건에 맞는 값이 있는지 여부(boolean)를 리턴하는 하는 함수입니다.

조건에 맞는 값이 있으면 true, 조건에 맞는 값이 없으면 false를 리턴합니다.

 파라미터 

callback(element, index, array) 함수

조건을 비교할 callback 함수이고, 다음 3개의 파라미터가 전달됩니다.

callback 함수에서 사용자가 테스트할 조건을 정의하고,

만약 배열의 값이 조건에 부합하면 true를 리턴하면,

some() 함수는 true를 리턴합니다.

조건에 부합하는 값을 찾으면, 그 이후의 배열 값은 테스트 되지 않습니다.

element : 현재 처리 중인 배열의 element입니다.
index : 현재 처리 중인 배열의 index입니다. (optional)
array : some() 함수가 호출된 배열입니다. (optional)
thisArg (optional)

callback을 실행할 때 this로 사용할 객체입니다.

 리턴 값 

조건에 부합하는 값이 있으면 true, 없으면 false를 리턴합니다.

5. includes() vs some() 
includes()와 some() 함수는 모두 특정 값이 배열에 포함되어 있는지를 체크할 수 있습니다.

================================================================

 정리해 보면 

includes() 함수는 primitive type을 체크하는 적절하고,

some() 함수는 primitive type 외의 타입을 체크하는데 적절하고,

체크 로직을 다양하게 적용할 수 있는 장점이 있습니다.



출처: https://hianna.tistory.com/403 [어제 오늘 내일]
```