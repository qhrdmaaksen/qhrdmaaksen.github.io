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
```
