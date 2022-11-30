---
layout: post
title: "내장 Method, Function 모음집"
---

## 검색하거나 공부할때마다 적어두자

```js

concat() 메소드
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

--------------------------------------------------------------
filter()
JavaScript - 배열 filter() 사용법 및 예제
-설명
자바스크립트의 filter함수는 배열의 각 요소를 순회하며 callback함수를 실행하며 조건에 맞는 요소만을 갖는 배열을 반환합니다.

arr.filter(callback(element[, index[, array]])[, thisArg])
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
--------------------------------------------------------------
setInterval() mdn 문서

-인터페이스에서 제공 되는 setInterval()메서드 는 각 호출 사이에 고정된 시간 지연으로 함수를 반복적으로 호출하거나 코드 스니펫을 실행합니다. WindowWorker
-이 메서드는 간격을 고유하게 식별하는 간격 ID를 반환하므로 나중에 를 호출하여 제거할 수 있습니다 clearInterval().

ex code
setInterval(code)
setInterval(code, delay)

setInterval(func)
setInterval(func, delay)
setInterval(func, delay, arg0)
setInterval(func, delay, arg0, arg1)
setInterval(func, delay, arg0, arg1, /* … ,*/ argN)

매개변수
func
A 는 밀리초 function마다 실행됩니다 . delay첫 번째 실행은 delay밀리초 후에 발생합니다.

code
delay선택적 구문을 사용하면 밀리초 마다 컴파일되고 실행되는 함수 대신 문자열을 포함할 수 있습니다 . 이 구문은 보안 위험 을 사용하는 것과 같은 이유로 권장되지 않습니다 .eval()

delay 선택 과목
밀리초(1/1000초) 단위의 타이머는 지정된 함수 또는 코드 실행 사이에 지연되어야 합니다. 지정하지 않으면 기본값은 0입니다. 허용되는 값 범위에 대한 자세한 내용은 아래의 지연 제한 을 참조하십시오 delay.

arg0, …, argN 선택 과목
타이머가 만료되면 func 에서 지정한 함수로 전달되는 추가 인수입니다 .

반환 값
반환 intervalID된 값은 에 대한 호출로 생성된 타이머를 식별하는 0이 아닌 숫자 값입니다 setInterval(). 이 값은 clearInterval()간격을 취소하기 위해 전달될 수 있습니다.

동일한 ID 풀을 공유하고 setInterval()기술적 으로 상호 교환하여 사용할 수 있음을 알고 있으면 도움이 될 수 있습니다 . 그러나 명확성을 위해 코드를 유지 관리할 때 혼동을 피하기 위해 항상 일치하도록 노력해야 합니다. setTimeout()clearInterval()clearTimeout()
--------------------------------------------------------------


```
