---
layout: post
title: "자바스크립트 기초!"
---

## 기초에대해 필요한 것들을 정리해두자

```js

함수,객체 특성

비동기 개념 - 이벤트 드리븐(상호작용) 프로그래밍
  콜백,프로미스,async/await
    호출스택, 이벤트루프, 실행 컨텍스트( this )

프로토타입(자바와 가장 큰 차이점)  class 는 class 가 아니다 

DOM 외우지말자, 자주 사용하다보면 외워진다
디자인패턴 -> 코딩하다가 코드정리하다보면 알아서 디자인패턴 모양이된다 (관련책 한번읽자)
함수형 프로그래밍 -> 선택
  map, filter, reduce -> 필수

배열-> 객체, 실무에서는 이차원 배열 많이사용 

//안녕하세요 거꾸로 출력해보기
let a = "안녕하세요";
//a.charAt() 활용 인덱스로 안녕하세요 거꾸로 , 요세하녕안 출력
//a의 5번째 인덱스는 아무것도 없기때문에 공백으로 출력
console.log(
  a.charAt(5),
  a.charAt(4),
  a.charAt(3),
  a.charAt(2),
  a.charAt(1),
  a.charAt(0)
);
//replace 활용 안녕하세요 거꾸로 , 요세하녕안 으로 변경 출력
console.log(a.replace("안녕하세요", "요세하녕안"));
//for 문 활용 안녕하세요 거꾸로 , 요세하녕안 으로 변경 출력
let b = ["안", "녕", "하", "세", "요"];
for (let i = b.length - 1; i >= 0; i--) {
  let result = b[i];
  document.write(result);
  console.log(result);
}
document.write(`<br>`);
//현재 시간 출력해보기
let time = new Date();
console.log(time);
document.write(`<br>` + time + `<br>`);
//Hello World 출력해보기
document.write(`<br>` + "Hello World");
//Hello World h1 으로 출력해보기
document.write(`<h1>` + `Hello World` + `</h1>`);
//"legend"를 변수에 담아 출력하되 대문자로 출력해보자
let legend = "legend";
document.write(`<br>` + legend.toUpperCase());
//typeOf메소드를 사용해 타입을 알아보자
let x = "y" + 1;
document.write(`<br>` + `<br>` + x);
document.write(`<br>` + `<br>` + typeof x);
// ===  !=== 연산자 알아보기
// === 연산자는 값과 타입이 모두 같으면 true 둘중하나라도 다르다면 false
// !=== 연산자는 값이나 타입이 다르면 참 (false(값도 같고 타입도 같다)(true(값은 같지만 타입이 다르다)))

// 예제 나이가 30세 미만이면 변수에 청년부 대입 , 아니면 장년부 대입
let age = 15;
let group = age < 30 ? "청년부" : "장년부";
console.log(group);

//parseInt() - 문자열을 숫자로 변환
//String() - 숫자를 문자열로 변환

// 사용자로부터 2개의숫자를 받고 덧셈을해서 그 결과를 돌려주자
/* let num01 = prompt("1번 사람의 나이를 입력해주세요");
    let num02 = prompt("2번 사람의 나이를 입력해주세요");
    num01 = parseInt(num01);
    num02 = parseInt(num01);
    let numEx_parseInt = num01+num02;
    confirm(numEx_parseInt); */
```

```js
<body>
  <div>
    <hr />
    <br />
    <p>자바 스크립트는 이벤트에 반응할 수 있습니다.</p>
    <button type="button" onclick="alert(`반갑습니다`)">버튼을 누르세요</button>
    <br />
  </div>
  <br />
  <hr />
  <!--덧셈 계산기 함수-->
  <script>
    function calc_total_func() {
      let calc01 = document.getElementById(`calc_int01`).value;
      let calc02 = document.getElementById(`calc_int02`).value;
      let calcTotal;
      calcTotal = parseInt(calc01) + parseInt(calc02);
      document.getElementById(`calc_total`).value = calcTotal;
    }
  </script>
  <div style="display: inline-block;">
    <!--덧셈 계산기-->
    <fieldset>
      <legend>덧셈 계산기</legend>
      <form>
        첫번째 정수 : <input id="calc_int01" type="number" value="" />
        <br />
        두번째 정수 : <input id="calc_int02" type="number" value="" />
        <br />
        합계 : <input id="calc_total" type="number" value="" />
      </form>
      <input type="button" value="계산" onclick="calc_total_func()" />
    </fieldset>
  </div>
  <br />
  <hr />
  <!--요소에 접근해 요소의 색상을 변경 함수-->
  <script>
    function color_changeEx() {
      let wri_p = document.getElementById(`color_change_writhing`);
      wri_p.style.color = `red`;
    }
    function color_changeEx2() {
      let wri_p = document.getElementById(`color_change_writhing`);
      wri_p.style.color = `black`;
    }
  </script>
  <!--요소에 접근해 요소의 색상을 변경해보자-->
  <div>
    <p id="color_change_writhing">내 글씨의 색상을 변경해볼까나?</p>
    <button type="button" onclick="color_changeEx()">
      클릭하면 빨강색상으로 변경
    </button>
    <button type="button" onclick="color_changeEx2()">
      클릭하면 검정색상으로 변경
    </button>
  </div>
  <br />
  <hr />
  <!--아침엔 좋은아침,오후엔 좋은오후, 저녁엔 좋은저녁 출력-->
  <script>
    let now_time = new Date().getHours;
    if (now_time < 12) {
      document.write(`좋은 아침입니다.!`);
    } else if (now_time < 18) {
      document.write(`좋은 오후입니다.!`);
    } else {
      document.write(`좋은 저녘입니다.!`);
    }
    //학점으로 메시지 출력하기
    function score_msgPrint() {
      let input_score = document.getElementById(`example_SC`).value;
      switch (input_score) {
        case "A":
          let A_MSG = `A 학점이군요, 자랑하세요!`;
          document.getElementById(`example_SC_msg`).value = A_MSG;
          break;
        case "B":
          let B_MSG = `B 학점이군요, 좀 더 공부하세요!`;
          document.getElementById(`example_SC_msg`).value = B_MSG;
          break;
        case "C":
          let C_MSG = `C 학점이군요, 남아서 공부하세요!!`;
          document.getElementById(`example_SC_msg`).value = C_MSG;
          break;
        default:
          let default_score = `알 수 없는 학점입니다. 확인해주세요!`;
          document.getElementById(`example_SC_msg`).value = default_score;
          break;
      }
    }
  </script>
  <hr />
  <div>
    <p>학점(A~C)을 대문자로 입력해주세요.</p>
    학점 : <input id="example_SC" type="text" value="" style="width: 30px;" />
    <br />
    <input
      type="button"
      value="학점 입력 후 클릭!"
      onclick="score_msgPrint()"
    />
    <br />
    메세지 :
    <input id="example_SC_msg" type="text" value="" style="width: 300px;" />
  </div>
  <hr />
  <script>
    let opportunity = 0; //현재 게임 한 횟수
    let computer_result = Math.floor(Math.random() * 10) + 1; //컴퓨터 가지고있는 숫자
    function game_check() {
      let user_input = 0; //유저가 입력한 숫자
      let game_msg = ""; //힌트 메세지
      user_input = document.getElementById(`user_num`).value;
      opportunity++;
      if (user_input == computer_result) {
        game_msg = `축하합니다.성공!`;
      } else if (user_input < computer_result) {
        game_msg = `낮습니다!`;
      } else {
        game_msg = `높습니다!`;
      }
      document.getElementById(`opportunity_num`).value = opportunity;
      document.getElementById(`game_hint`).value = game_msg;
    }
  </script>
  <div style="display: inline-block;">
    <form>
      <fieldset>
        <legend>숫자 맞추기 게임!</legend>
        <p>
          이 게임은 컴퓨터가 생성한 숫자를 맞추는 게임입니다. 숫자는 1부터
          10사이에있어요.
        </p>
        숫자 : <input id="user_num" type="number" value="" size="3" />
        <button type="button" onclick="game_check()">확인</button>
        <br />
        횟수 :
        <input id="opportunity_num" type="number" value="" size="5" /> 힌트 :
        <input id="game_hint" type="text" value="" />
        <input
          type="button"
          value="게임 새로 시작"
          onClick="window.location.href=window.location.href"
        />
      </fieldset>
    </form>
  </div>
  <hr />
  <!--hello 5번 출력 loof 문활용-->
  <script>
    for (let i = 0; i <= 4; i++) {
      document.write(`Hello for 5` + `<br>`);
    }
    let j = 0;
    while (j <= 4) {
      document.write(`Hello while 5` + `<br>`);
      j++;
    }
  </script>
  <hr />
  <!--count 0~10 출력-->
  <script>
    let k = 0;
    while (k <= 10) {
      document.write(`count : ` + k + `<br>`);
      k++;
    }
  </script>
  <hr />
  <!--온도 변환기-->
  <div>
    <table border="3">
      <tr>
        <td>섭씨 온도</td>
        <td>화씨 온도</td>
      </tr>
      <script>
        for (let celsius = 0; celsius <= 10; celsius++) {
          document.write(
            `<tr><td>` + celsius + `</td><td>` + ((celsius * 9.0) / 5 + 32)
          ) + `</td></tr>`;
        }
      </script>
    </table>
  </div>
  <hr />
  <!--구구단 표 작성해보기-->
  <script>
    document.write(`<h3>` + `구구단 표` + `</h3>`);
    document.write(`<br>` + `<table border=2 width=20%>`);
    for (let i = 1; i <= 9; i++) {
      document.write(`<tr>`);
      document.write(`<td>` + i + `</td>`);
      for (let j = 2; j <= 9; j++) {
        document.write(`<td>` + i * j + `</td>`);
      }
      document.write(`</tr>`);
    }
    document.write(`</table>`);
  </script>
  <hr />
  <!--do/while 문으로 카운터 1부터 10까지 출력-->
  <script>
    let i = 1;
    do {
      document.write(`카운터 : ` + i + `<br>`);
      ++i;
    } while (i <= 10);
  </script>
  <hr />
  <!--for..in 문으로 객체 속성 출력-->
  <script>
    let min = {
      name: `minwoo`,
      age: 35,
      hobby: `coding`,
    };
    let text = ``;
    for (const output in min) {
      text += output + ` : ` + min[output] + `<br>`;
    }
    document.write(text);
  </script>
  <hr />
  <!--break 문장-->
  <script>
    for (let i = 0; i < 10; i++) {
      if (i == 3) {
        break;
      }
      document.write(i + `<br>`);
    }
  </script>
  <hr />
  <!--continue 문장-->
  <script>
    for (let i = 0; i <= 5; i++) {
      if (i == 3) {
        continue;
      }
      document.write(i + `<br>`);
    }
  </script>
  <hr />
  <!--리터럴(문자그대로)로 배열 생성-->
  <script>
    let fruits = [`바나나`, `딸기`, `멜론`];
    for (let i = 0; i < fruits.length; i++) {
      document.write(fruits[i] + `<br>`);
    }
  </script>
  <hr />
  <!--Array 객체로 배열 생성-->
  <script>
    let family = new Array(`민우`, `민지`, `민석`);
    for (let i = 0; i < family.length; i++) {
      document.write(family[i] + `<br>`);
    }
  </script>
  <hr />
  <!--연관배열(키,값)으로 호출-->
  <script>
    function get_info() {
      for (let i = 0; i < 3; i++) {
        document.min_info[`user_` + i].value = i;
      }
    }
  </script>
  <div>
    <form name="min_info">
      숫자0 : <input name="user_0" type="text" value="" />
      <br />
      숫자1 : <input name="user_1" type="text" value="" />
      <br />
      숫자2 : <input name="user_2" type="text" value="" />
      <br />
      <button type="button" onclick="get_info()">받기</button>
    </form>
  </div>
  <hr />
  <!--매개 변수 활용 onclick 이벤트 함수로 인사말 팝업-->
  <script>
    function hello(name, bank) {
      confirm(name + ` 님 ` + bank + `을 방문해주셔서 감사합니다.`);
    }
  </script>
  <button type="button" onclick="hello(`민우`,`땡땡은행`)">인사말</button>
  <hr />
  <!--무명함수-->
  <script>
    let greeting_func = function (name) {
      document.write(`무명함수 동작 ` + name);
    };
    greeting_func(`김민우`);
    document.write(`<br>`);
    greeting_func();
  </script>
  <hr />
  <!--100보다 작은 정수만을 입력받는 자바스크립트 프로그램 작성-->
  <script>
    function ex_pop_int() {
      let val = prompt("100미만의 정수 입력");
      if (val > 100) {
        confirm(`정수 ` + val + ` 은 100보다 작지 않습니다.`);
      }
    }
  </script>
  <button type="button" onclick="ex_pop_int()">정수 입력창 팝업</button>
  <hr />
  <!--1부터100까지 합 구하는 프로그램-->
  <script>
    let total = 0;
    for (let i = 1; i <= 100; i++) {
      total += i;
    }
    document.write(total);
  </script>
  <hr />
  <!--요일 순서 팝업-->
  <script>
    function day_of_the_week() {
      let day = new Array(
        `월요일`,
        `화요일`,
        `수요일`,
        `목요일`,
        `금요일`,
        `토요일`,
        `일요일`
      );
      for (let i = 0; i < day.length; i++) {
        confirm(day[i]);
      }
    }
  </script>
  <div>
    <button type="button" onclick="day_of_the_week()">
      요일 순서 팝업창 보기
    </button>
  </div>
  <hr />
  <!--게임 시작 팝업창 프로그램-->
  <script>
    function game_start() {
      let game_start_check = confirm(`게임을 시작하시겠습니까?`);
      if (game_start_check) {
        alert(`좋습니다.게임시작!`);
      } else {
        alert(`다음 기회엔 꼭 참여해주세요!`);
      }
    }
  </script>
  <div>
    <button type="button" onclick="game_start()">
      게임 시작 알림 프로그램
    </button>
  </div>
  <hr />
  <!--유저가 좋아하는 음악 정보를 담은 객체와 속성을 출력하는 프로그램-->
  <script>
    let user01_like_music = {
      singer: `아이유`,
      title: `좋은날`,
      sing_time: 90 + `초`,
    };
    for (const user_music_info in user01_like_music) {
      document.write(
        user_music_info + ` : ` + user01_like_music[user_music_info] + `<br>`
      );
    }
  </script>
</body>
arr.fill('A', 1, 3) /*A:Value,1:start index,3end index*/
 
 fill() 함수는 
배열의 start index부터 end index 전까지(end index는 미포함) value값으로 채워주는 함수입니다.
 
 파라미터 
value
배열에 채울 값을 지정합니다.
 
start
value 값을 채울 배열의 시작 index입니다.
입력하지 않으면 기본값은 0입니다.
 
end
value 값을 채울 배열의 종료 index입니다.
입력하지 않으면 기본값은 배열의 길이(arr.length)입니다.
 
 리턴값 
지정한 값으로 채워진 배열을 리턴합니다.

const arr1 = ['a', 'b', 'c', 'd'];
arr1.fill('A'); // ['A', 'A', 'A', 'A']
document.write(arr1 + '<br>');

const arr2 = ['a', 'b', 'c', 'd'];
arr2.fill('A', 1); // ['a', 'A', 'A', 'A']
document.write(arr2 + '<br>');

const arr3 = ['a', 'b', 'c', 'd'];
arr3.fill('A', 1, 3); // ['a', 'A', 'A', 'd']
document.write(arr3 + '<br>');

배열 초기화
const arr = new Array(4).fill('A');

document.write(arr); //[A,A,A,A]
출처: https://hianna.tistory.com/399 [어제 오늘 내일:티스토리]
=======================================================
slice() 함수
slice() 함수는 배열로 부터 특정 범위를 복사한 값들을 담고 있는 새로운 배열을 만드는데 사용합니다. 첫번째 인자로 시작 인덱스(index), 두번째 인자로 종료 인덱스를 받으며, 시작 인덱스부터 종료 인덱스까지 값을 복사하여 반환합니다.

간단한 실습을 위해 숫자 0부터 19까지를 담고있는 배열을 생성하여 nums라는 변수에 할당해보겠습니다. (브라우저의 콘솔에서 따라서 코딩해보시기를 추천드립니다.)

> nums = Array(20).fill().map((_, i) => i)
< [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
이 숫자 배열에서 5부터 9까지를 복사한 값을 담고 있는 새로운 배열을 만들어 보겠습니다.

> nums.slice(5, 10)
< [5, 6, 7, 8, 9]
여기서 주의할 점은 첫번째 인자로 넘어온 시작 인덱스가 가리키는 값은 포함하지만, 두번째 인자로 넘어온 종료 인덱스가 가리키는 값은 포함하지 않는다는 것입니다.

두번째 인자를 넘기지 않으면, 시작 인덱스가 가리키는 값부터 배열의 마지막 값까지 모두 복사해줍니다.

> nums.slice(10)
< [10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
첫번째 인자도 넘기지 않으면, 배열의 처음 값부터 마지막 값까지 전체를 복제해버리는 효과를 낼 수 있습니다.

> nums.slice()
< [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
slice() 함수는 밑에서 다룰 splice() 함수와 달리 아무리 많이 호출해도 원본 배열의 값은 절대 건드리지 않습니다. 따라서 원본 배열이 그대로 보존되야 하는 상황에서 매우 유용하게 사용됩니다.

> nums
< [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
=======================================================
splice() 함수
slice() 함수의 이름에서 알파벳 p가 하나 더 있는 splice() 함수는 다목적으로 사용할 수 있는 함수인데요. 이 함수로는 배열로 부터 특정 범위를 삭제하거나 새로운 값을 추가 또는 기존 값을 대체할 수 있습니다. 첫번째 인자로 시작 인덱스(index), 두번째 인자로 몇개의 값을 삭제할지, 그리고 세번째 인자부터는 추가할 값을 가변 인자로 넘길 수 있으며, 삭제된 값을 담고 있는 배열을 반환합니다.

역시 위와 동일한 방법으로 nums라는 숫자 배열을 생성해놓고 실습을 시작하겠습니다.

> nums = Array(20).fill().map((_, i) => i)
< [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
이 숫자 배열에서 인덱스 5가 기리키는 값부터 3개의 값을 삭제해보겠습니다.

> nums.splice(5, 3)
< [5, 6, 7]
> nums
< [0, 1, 2, 3, 4, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
삭제된 3개의 값을 담고 있는 배열이 반환되며, 원본 배열로 부터 3개의 값이 빠져나간 것을 알 수 있습니다.

이번에는 인덱스 5가 기리키는 값부터 아무 값도 삭제하지 않고, -5, -6, -7을 추가해보겠습니다.

> nums.splice(5, 0, -5, -6, -7)
< []
> nums
< [0, 1, 2, 3, 4, -5, -6, -7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
삭제된 값이 없으므로 빈 배열이 반환되고, 이전에 값이 삭제된 자리에 -5, -6, -7을 들어간 것을 알 수 있습니다.

이번에는 인덱스 10이 가리키는 값부터 2개의 값을 -10, -11로 대체해보겠습니다.

> nums.splice(10, 2, -10, -11)
< [10, 11]
> nums
< [0, 1, 2, 3, 4, -5, -6, -7, 8, 9, -10, -11, 12, 13, 14, 15, 16, 17, 18, 19]
삭제된 2개의 값을 담고 있는 배열이 반환되며, 원본 배열의 10, 11이 있던 자리에 -10, -11에 들어가 앉아있는 것을 볼 수 있습니다.

splice() 함수에 첫번째 인자만 넘기면 해당 인덱스가 가리키는 값을 포함해서 배열의 마지막 값까지 삭제가 됩니다.

> nums.splice(15)
< [15, 16, 17, 18, 19]
> nums
< [0, 1, 2, 3, 4, -5, -6, -7, 8, 9, -10, -11, 12, 13, 14]
splice() 함수를 사용할 때 가장 주의할 부분은 삭제된 값을 담고 있는 새로운 배열이 반환될 뿐만 아니라 원본 배열에도 변경이 가해진다는 점입니다. 따라서 의도치 않은 데이터 유실이나 변경으로 이어질 수 있으니 특히 데이터의 불변성(immutability)이 보장되어야 하는 프로그램을 작성할 때 주의하셔야 합니다.

slice() vs. splice()
많은 자바스크립트 개발자들이 slice() 함수와 splice() 함수를 햇갈려하는 이유는 비단 이름이 비슷해서 뿐만 아니라 실제로 동일한 목적을 위해서 두 함수 중에 아무거나 사용해도 무방한 경우가 있기 때문입니다.

예를 들어, nums 배열에서 5부터 7까지를 복사한 값을 담고 있는 새로운 배열을 얻고 싶을 때 다음 두 가지 방법을 다 쓸 수가 있습니다.

> nums = Array(20).fill().map((_, i) => i)
< [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
> nums.slice(5, 8)
< [5, 6, 7]
> nums.splice(5, 3)
< [5, 6, 7]
차이점이라고 하면 두번째 인자로 slice() 함수는 종료 인덱스, splice() 함수는 몇개의 값을 때어낼지를 넘긴다는 것 뿐인데요.

하지만 이 두 함수를 동일한 배열을 대상으로 여러 번 호출할 수 있는 상황이라면 얘기가 좀 틀려집니다.

> nums = Array(20).fill().map((_, i) => i)
< [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
> nums.slice(5, 8) // slice() 1회 호출
< [5, 6, 7]
> nums.slice(5, 8) // slice() 2회 호출
< [5, 6, 7]
> nums.slice(5, 8) // slice() 3회 호출
< [5, 6, 7]
> nums.slice(5, 3) // splice() 1회 호출
< [5, 6, 7]
> nums.splice(5, 3) // splice() 2회 호출
< [8, 9, 10]
> nums.splice(5, 3) // splice() 3회 호출
< [11, 12, 13]
항상 같은 배열을 반환한는 slice() 함수와 달리 splice() 함수는 계속해서 원본 배열를 깍아 먹기 때문에 동일한 인자로 여러 번 함수를 호출했을 때 매번 다른 배열이 반환되게 됩니다.
=======================================================
reduce() 메서드
-배열의 각 요소에 대해 주어진 reducer 함수를 실행하고 하나의 결과 값을 반환함
ex code
const array1 = [1, 2, 3, 4];
// 0 + 1 + 2 + 3 + 4
const initialValue = 0;
const sumWithInitial = array1.reduce(
  (accumulator, currentValue) => accumulator + currentValue,
  initialValue
);
console.log(sumWithInitial);
// expected output: 10
(리듀서 함수는 제개의 인자를 가짐(누산기,현재값,현재인덱스원본 배열))
리듀서 함수의 반환 값은 누산기에 할당되고 누산기는 순회중 유지되므로 결국 최종 결과는 하나의 값이 됨 

-reduce 함수 호출에서 initialValue 를 제공한 경우 accumulator 는 initialValue 와 같고 currentValue 는 배열의 첫 번째 값과 같다/ initialValue 를 제공하지 않았다면 accumulator 는 배열의 첫 번째 값과 같고 currentValue 는 두 번째와 같다
-배열이 비어있는데 initialValue 도 제공하지 않으면 타입 에러 발생함
-배열의 요소가 하나 뿐이면서 initialValue 를 제공되지않은 경우 or initialValue 는 주어졌으나 배열이 빈 경우엔 그 단독 값을 callback 호출 없이 반환함
=======================================================
connect 함수
-connect 함수는 컨테이너 컴포넌트를 만드는 또 다른 방법
-사용할 일은 별로 없음 useSelector, useDispatch 로 대체됨
-클래스형 컴포넌트로 작성되어있다면 connect 함수를 사용된 경우를 보게될 것임
-HOC (higher-order-component) 임 / 리액트 컴포넌트를 개발하는 하나의 패턴이며 컴포넌트의 로직을 재활용할때 유용한 패턴임
-특정 함수 또는 값을 props 로 받아와 사용하고 싶은 경우에 이런 패턴을 사용함
-리액트에 hooks 가 도입되기 전에 HOC 패턴이 자주사용됐고 지금은 HOC 를 만들이유가 없어짐
-용도는 컴포넌트를 특정 함수로 감싸서 특정 값 또는 함수를 PROPS 로 받아와 사용할수있게 해주는 패턴임
=======================================================
=======================================================
=======================================================
=======================================================
=======================================================
=======================================================
=======================================================
=======================================================
=======================================================
=======================================================

```
