---
layout: single
title: "Method 모음집"
---

## 검색하거나 공부할때마다 적어두자

```js
자바 CONCAT () 메소드
-설명
문자열로 연결 문자열의 매개 변수를 지정하는데 사용됨
ex(public String concat(String s))

ex info =

public class Test {
	public static void main(String args[]) {
		String s = "本教程：";
		s = s.concat("www.w3big.com");
		System.out.println(s);
	}
}
위의 프로그램 실행 결과 :
本教程：www.w3big.com
```

```js
filter()
JavaScript - 배열 filter() 사용법 및 예제
-설명
자바스크립트의 filter함수는 배열의 각 요소를 순회하며 callback함수를 실행하며 조건에 맞는 요소만을 갖는 배열을 반환합니다.

arr.filter(callback(element[, index[, array]])[, thisArg])
--------------------------------------------------------------
파라미터

callback function
각 요소의 조건을 판단할 함수로 true를 반환하면 요소를 유지하고 false를 반환하면 제외합니다.
다음 3가지의 인수를 가집니다.
element - 배열의 현재 요소
index(Optional) - 배열의 현재 요소의 인덱스
array(Optional) - 호출한 배열
thisArg(Optional)
callback함수를 실행할때 this로 사용되는 값
반환 값
배열을 순서대로 불러 각 요소에 대해 callback 함수을 실행하고 결과가 true인 요소들만으로 이루어진 새로운 배열을 반환합니다.

예제
1. 배열 속 숫자 중 홀수만 갖는 배열 만들기

const numbers = [1, 2, 3, 4, 5]; // 기존 배열

// filter1 - callback함수를 직접 작성
// 현재 요소를 2로 나눈 나머지가 1일 경우 홀수
const filter1 = numbers.filter(currentNumber => currentNumber % 2 === 1);

console.log('filter1 =', filter1);
또는

// filter2 - callback함수 선언 후 이용
function isOdd(currentNumber) {
  return currentNumber % 2 === 1;
}

const filter2 = numbers.filter(isOdd);

console.log('filter2 =', filter2);

Result :
filter1= [1, 3, 5]
filter2= [1, 3, 5]
```
