---
layout: single
title: "자바스크립트 기초02!"
---

# 기초에대해 필요한 것들을 정리해두자

<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>js객체</title>
  <script>
    //객체 상수(리터럴방식)로부터 객체 생성
    //간단하지만 객체를 하나만 생성할수있고 추가로 객체 생성시,
    //동일한 코드 반복해야해서 싱글톤(객체가 하나만생성)이라부른다.
    let myCarEx01 = {
      modelCar: `moning`,//객체의 속성
      speedCar: 150,
      colorCar: `black`,
      brakeCar: function () { this.speedCar -= 10 },//객체의 메서드
      accelCar: function () { this.speedCar += 10 },
    }
    myCarEx01.colorCar = `white`;//객체 속성 변경
    console.log(myCarEx01.colorCar);
    myCarEx01.brakeCar()//브레이크 함수 실행
    console.log(myCarEx01);//speed 150에서 10줄어든 140으로 변경확인
    myCarEx01.accelCar()//엑셀 함수 실행
    console.log(myCarEx01);//speed 140에서 10 늘어난 150으로 변경확인
  </script>
  <script>
    //생성자 함수를 이용한 객체 생성
    //장점 : 개발자가 원하는 개수만큼 객체를 쉽게 만들 수 있다.
    //개발 도중, 필요하지만 자바스크립트에서 지원하지않는 객체를 생성하고 싶을때 사용
    function MyCarEx02(model, speed, color) {//생성자 이름은 대문자로한다.
      this.model = model//this 키워드로 일반 변수와 객체 속성을 구별
      this.speed = speed
      this.color = color
      this.brake = function () { this.speed -= 10 }//객체의 메서드
      this.accel = function () { this.speed += 10 }
    }
    let myCarEx02 = new MyCarEx02(`avante`, `170`, `white`);
    console.log(myCarEx02);
    myCarEx02.color = `black`
    console.log(myCarEx02);
    myCarEx02.brake()
    console.log(myCarEx02);
    myCarEx02.accel()
    console.log(myCarEx02);
    myCarEx02.turbo = true //객체에 새로운 속성 추가 
    console.log(myCarEx02);
    myCarEx02.showModel = function () { //객체에 새로운 메서드 추가
      document.write(`<hr>`)
      document.write(`해당 자동차는 아반테입니다.`)
    }
    myCarEx02.showModel()
    //객체 멤버 - 객체 안의 속성과 메서드를 객체 멤버라고 함
  </script>
  <script>
    //자바스크립트에는 클래스가없다. 입력되는 즉시 실행해야하는 인터프리터 언어이기때문이다.
    //하지만 클래스의 역할을 하는 프로토 타입이있다. 이것을 클래스처럼 사용할 수 있다.
    //프로토타입 체인 - 자바스크립트에서 속성,메서드를 참조하게되면 다음과같다.
    //1) 객체 안에 속성이나 메서드가 정의되어있는지 체크
    //2) 객체 안에 정의되어있지 않으면 객체의 prototype이 속성이나 메서드를 가지고있는지 체크
    //3) 원하는 속성/메서드를 찾을때까지 프로토타입 체인을 따라 올라간다.
    //프로토타입 객체는 개별 객체에서 시작해 생성자의 프로토타입을 통해 object의 프로토타입까지 연결되어있다.
    function Point(xpos, ypos) {
      this.x = xpos;
      this.y = ypos;
    }
    Point.prototype.getDistance = function (p) { //모든 포인트 객체가 공유하는 메서드
      return Math.sqrt(this.x * this.x + this.y * this.y)
    }
    let p1 = new Point(10, 20)
    let d1 = p1.getDistance()
    let p2 = new Point(10, 30)
    let d2 = p2.getDistance()
    document.write(`<br>`)
    document.write(`<hr>`)
    document.write(d1 + `<br>`)
    document.write(d2 + `<br>`)
    //Object 객체 - 자바스크립트 객체의 부모가 되는 객체.
    //constructor 속성 - 속성으로 생성자 함수를 가리킨다.
    document.write(`<hr>`)
    document.write(p1.constructor)
    document.write(`<hr>`)
    //valueOf() 메서드 - 메서드로서 객체를 숫자로 변환한다.
    //toString() 메서드 - // 객체의 값을 문자열로 변환
    //hasOwnProperty() - 전달 인수로 주어진 속성을 가지고있다면 true 반환
    //isPrototype() - 현재 객체가 전달 인수로 주어진 객체의 프로토타입이면 true 반환
    //Object 객체의 메서드는 하위 객체에서 재정의해서 아래와같이 사용 할 수 있다.
    Point.toString = function () {
      return `새로 정의된 객체입니다.`
    }
    document.write(`<br>`)
    document.write(Point.toString())
  </script>
  <script>
    //자바스크립트 내장 객체
    //1 - Date() : 날짜와 시간 작업을 하는데 사용되는 가장 기본적인 객체
    // Date 객체 생성자 4가지
    //1-1 : 현재 날짜와 시간 date
    let nowDateTime = new Date()
    document.write(`<hr>`)
    document.write(`<br>`)
    document.write(nowDateTime)
    //1-2 : Date(milliseconds) - 1999/01/01 이후의 밀리초 
    //let DateTimeMilli = new Date(milliseconds)
    document.write(`<br>`)
    //document.write(DateTimeMilli)
    //1-3 : Date(dateString) - 다양한 문자열
    //let DateString = new Date(dateString)
    document.write(`<br>`)
    //document.write(DateString)
    //1-4 : Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])
    //Date() 주의 할 점은 월은 0부터 시작, 1월은 0으로 입력해줘야함 12월은 11 입력
    //Date 는 아주많은 메서드를 가지고있기에 작업할때 검색해서 필요한것을 사용하자
    //쇼핑몰에 구입한지 30일 지난물건은 교환이 안된다. 검사하는 프로그램을 만들어보자
    function cheackDate() {
      let userBuyDate = document.getElementById(`productDate`).value
      let pDate = new Date(userBuyDate)
      let today = new Date()
      let diff = today.getTime() - pDate.getTime() //날짜 간격 밀리초 단위 계산
      let days = Math.floor(diff / (1000 * 60 * 60 * 24)) // 밀리초 차이값 나눠서 날짜 간격 구하기
      if (days > 30) {
        confirm(`교환 기간이 지났습니다.`)
      } else {
        confirm(`교환 가능한 기간입니다`)
      }
    }
  </script>
  <script>
    //Number 객체 - Number객체는 수치형 값을 감싸서 객체로 만들어주는 랩퍼(wrapper) 객체다.
    //랩퍼 객체 - 수치값을 직접 사용할 수는 없고 , 반드시 객체가 필요한 경우에 사용
    let num = new Number()
    num = 1.234
    console.log(num.toString()); //이와 같이 1.234를 감싸는 랩퍼 객체 생성가능
    //Number 객체의 속성 중 일부 3가지
    //1) MAX VALUE - 표현 할 수 있는 가장큰값
    //2) MIN VALUE - 표현 할 수 있는 가장작은값
    //3) NaN - Not a Number 
    //Number 객체의 메서드 4가지
    //1) toExponential() - 지수형으로 반환 , 인수는 소수점 이하 숫자의 개수
    document.write(`<hr>`)
    let numProperty = 123.4567
    document.write(`1) toExponential() - 지수형으로 반환 , 인수는 소수점 이하 숫자의 개수` + `<br>`)
    document.write(numProperty.toExponential() + `<br>`)
    document.write(numProperty.toExponential(1) + `<br>`)
    //2) toFixed() - 고정소수점 방식으로 반환, 인수는 소수점 이하 숫자의 개수
    let numProperty2 = 123.4567
    document.write(`2) toFixed() - 고정소수점 방식으로 반환, 인수는 소수점 이하 숫자의 개수` + `<br>`)
    document.write(numProperty2.toFixed() + `<br>`)
    document.write(numProperty2.toFixed(1) + `<br>`)
    //3) toPrecision() - 유효숫자 수를 지정
    let numProperty3 = 123.4567
    document.write(`3) toPrecision() - 유효숫자 수를 지정` + `<br>`)
    document.write(numProperty2.toPrecision(1) + `<br>`)
    document.write(numProperty2.toPrecision(2) + `<br>`)
    //4) toString() - 주어진 진법으로 숫자를 반환
    let numProperty4 = 123.4567
    document.write(`4) toString() - 주어진 진법으로 숫자를 반환` + `<br>`)
    document.write(numProperty2.toString() + `<br>`)
    document.write(numProperty2.toString(2) + `<br>`)
    document.write(numProperty2.toString(8) + `<br>`)
    document.write(numProperty2.toString(16) + `<br>`)
    document.write(`<hr>`)
  </script>
</head>

<body>
  <div>
    <form>
      구입 날짜 : <input id="productDate" type="date" value="">
      <button type="button" onclick="cheackDate()">검사</button>
    </form>
  </div>
  <hr>
  <div id="remaining">
  </div>
  <script>
    //카운트 다운 타이머를 만들어보자
    function datesUntilNewYear() {
      let now = new Date()
      let newYear = new Date(`January 1, ` + (now.getFullYear() + 1))
      let diff = newYear - now
      let milliseconds = Math.floor(diff % 1000)
      diff = diff / 1000
      let seconds = Math.floor(diff % 60)
      diff = diff / 60
      let minutes = Math.floor(diff % 60)
      diff = diff / 60
      let hours = Math.floor(diff % 24)
      diff = diff / 24
      let days = Math.floor(diff)

      let outStr = `내년 1월 1일까지 ` + days + `일, ` + hours + `시간, ` + minutes
      outStr += `분, ` + seconds + `초` + ` 남았습니다.`

      document.getElementById(`remaining`).innerHTML = outStr
      //1초가 지나면 다시 함수를 호출한다.
      setTimeout(`datesUntilNewYear()`, 1000)
    }
    // 타이머를 시작한다.
    datesUntilNewYear()
  </script>
  <hr>
  <div id="clock">
  </div>
  <script>
    // 현재 시간 시계 만들기
    function setClock() {
      let now = new Date()
      let s = now.getHours() + `:` + now.getMinutes() + `:` + now.getSeconds()
      document.getElementById(`clock`).innerHTML = s
      setTimeout(`setClock()`, 1000) //두번째 인수의 시간(밀리초)만큼 지난 후에 첫번째 인수를 호출, 여기서는 1초가 지난 후에 setClock() 호출
    }
    setClock()
  </script>
  <hr>
  <!--String 객체-->
  <!--String 객체 속성은 다양하기에 필요에따라 검색해서 응용하자-->
  <!--1)length - 문자열의 길이-->
  <!--응용 - 아이디 길이 체크-->
  <script>
    function idLengthCheck() {
      let idValue = ``;
      idValue = document.getElementById(`lengthCheck`).value
      if (idValue.length < 6) {
        confirm(`아이디의 길이는 최소 6글자 이상이어야합니다.`)
      }
    }
  </script>
  <div>
    <form>
      <p>1)length - 문자열의 길이</p>
      아이디 : <input id="lengthCheck" type="text" size="10" value="">
      <button type="button" onclick="idLengthCheck()">검사</button>
    </form>
  </div>
  <!--2)indexOf() 메서드 - 문자열 안에서 주어진 텍스트가 처음 등장하는 위치를 반환-->
  <hr>
  <script>
    let indexOfTest01 = `자바스크립트에 오신 것을 환영합니다.`;
    let indexOfTest02 = indexOfTest01.indexOf(`환영`);
    document.write(`2)indexOf() 메서드 - 문자열 안에서 주어진 텍스트가 처음 등장하는 위치를 반환` + `<br>`)
    document.write(indexOfTest02);
  </script>
  <hr>
  <!--3)match() 메서드 - 문자열 안에서 일치하는 콘텐츠를 탐색하는데 사용,정규식 사용이 가능하다.-->
  <script>
    let str = `like game, Like dog`
    document.write(`3)match() 메서드 - 문자열 안에서 일치하는 콘텐츠를 탐색하는데 사용,정규식 사용이 가능하다.` + `<br>`)
    document.write(str.match(/like/ig))// ig 의 i 는 insensitive, g는 globally 옵션 의미 
  </script>
  <hr>
  <!--4)replace() 메서드 - 문자열 안에서 주어진 값을 다른 값으로 대체, 정규식 사용가능-->
  <script>
    let replaceTest01 = `우리 우미 안뇽 반가워 잘지내지 귀여운 강아지`;
    let replaceTest02 = replaceTest01.replace(`안뇽 반가워`, `안녕 안녕`);
    document.write(`4)replace() 메서드 - 문자열 안에서 주어진 값을 다른 값으로 대체, 정규식 사용가능` + `<br>`)
    document.write(replaceTest02)
  </script>
  <hr>
  <!--5)split() - 첫번째 인수를 분리자로 하여 주어진 문자열을 분리한 후에 각 항목을 가지고있는 배열을 반환,
    문자열을 배열로 변환할 수 있다.-->
  <script>
    let splitTest01 = `One, Two, Three, Four, Five`;
    let array = new Array();
    array = splitTest01.split(`,`);
    for (let i = 0; i < array.length; i++) {
      document.write(i + ` - ` + array[i] + `<br>`);
    }
  </script>
  <hr>
  <!--6)HTML 랩퍼 메서드 - 종류가 많다. 필요에따라 검색해서 사용하자-->
  <!--7)문자열 리터럴과 문자열 객체 - String 객체가 함수로 전달될 때 값만 전달된다.
    함수 안에서 전달받은 문자열을 변경하더라도 원본은 변경되지 않는다.-->
  <script>
    let sLiteral = `문자열 리터럴`;
    let sObject = new String(`문자열 객체`);
    function change(strlit, strobj) {
      strlit = `hello`;
      strobj = `hello`;
    }
    change(sLiteral, sObject);
    document.write(sLiteral + `<br>`);
    document.write(sObject + `<br>`);
  </script>
  <!--8)concat() - 문자열에선 문자열 합치기 , 배열출력에 사용하면 배열합치기-->
  <!--9)sort() - 정렬 메서드로 알파벳 순서로 정렬하기에 수치값으로 정렬하고자한다면 정렬기준 함수를 인수로 제공해야한다.-->
  <hr>
  <script>
    let sortTest01 = [8, 43, 3, 32, 6, 4, 2, 376];
    sortTest01.sort(function (a, b) { return a - b })
    document.write(`9)sort() - 정렬 메서드로 알파벳 순서로 정렬하기에 수치값으로 정렬하고자한다면 정렬기준 함수를 인수로 제공해야한다.` + `<br>`);
    document.write(sortTest01);
  </script>
  <!--10)Array.slice() 메서드 - 배열의 일부를 복사해 새로운 배열로 반환, 시작인덱스가없으면 0으로 가정, 종료인덱스가 없다면 배열의 끝까지 복사-->
  <hr>
  <script>
    let sliceNumber = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
    let sliceNumber2 = sliceNumber.slice(6);
    document.write(`10)Array.slice() 메서드 - 배열의 일부를 복사해 새로운 배열로 반환, 시작인덱스가없으면 0으로 가정, 종료인덱스가 없다면 배열의 끝까지 복사` + `<br>`);
    document.write(sliceNumber2 + `<br>`);
  </script>
  <hr>
  <!--11)join() - 배열의 요소들을 하나의 문자열로 출력, 이 기능은 배열을 서버로 보낼때 유용하며 분리자가 각 요소를 분리하게된다.-->
  <script>
    let joinTest01 = [`김민우`, `김민석`, `김민지`];
    let joinTest02 = joinTest01.join(` + `);
    document.write(`11)join() - 배열의 요소들을 하나의 문자열로 출력, 이 기능은 배열을 서버로 보낼때 유용하며 분리자가 각 요소를 분리하게된다.` + `<br>`);
    document.write(joinTest02)
  </script>
  <hr>
  <!--12)filter() - 어떤 조건에 부합하는 요소만을 선택해서 새로운 배열로 만들어서 반환, 요소를 선택하는 함수를 작성하여 인수로 전달한다.-->
  <script>
    let NumberTest = [10, 20, 30, 40, 50];
    function filterFunc(element, index, array) {
      return (element >= 30);
    }
    let numberRepogitory = NumberTest.filter(filterFunc)
    document.write(`12)filter() - 어떤 조건에 부합하는 요소만을 선택해서 새로운 배열로 만들어서 반환, 요소를 선택하는 함수를 작성하여 인수로 전달한다.` + `<br>`);
    document.write(numberRepogitory);
  </script>
  <hr>
  <!--2차원 배열-->
  <script>
    let x = [0, 1, 2, 3, 4]
    let y = [x]
    document.write(`2차원 배열` + `<br>`)
    document.write(y[0] + `<br>`)
    document.write(y[0][3] + `<br>`)
    document.write(`<hr>`)
  </script>
  <!--2차원 배열 리터럴 방식-->
  <script>
    let z = [
      [1, 2, 3],
      [4, 5, 6],
      [7, 8, 9],
    ]
    document.write(`2차원 배열 리터럴 방식` + `<br>`)
    document.write(z[1][1])
  </script>
  <hr>
  <!--try_catch-->
  <script>
    let msg = ``;
    function TCtest() {
      try {
        allert(`얼럿 에러`)
      } catch (error) {
        msg = `다음과 같은 오류 발생 : ` + error.message
        alert(msg)
      }
    }
  </script>
  <div>
    <button type="button" onclick="TCtest()">try_catch테스트</button>
  </div>
  <hr>
  <!--throw - 개발자가 오류를 생성할수 있도록한다. 어떤 기준을정하고 이 기준에 안맞다면 사용자에게 경고메시지 줄때도 사용된다.-->
  <script>
    let comNum = Math.floor(Math.random() * 100 + 1)
    console.log(comNum);
    function guessGame() {
      let userInput = parseInt(document.getElementById(`inputNum`).value)
      try {
        if (userInput > 100) throw `100 이하의 숫자를 입력하세요!`;
        if (comNum == userInput) throw `맞추셨습니다! 성공!`;
        if (comNum > userInput) throw `숫자가 낮습니다!`;
        if (comNum < userInput) throw `숫자가 높습니다!`;
        if (userInput == ``) throw `숫자를 입력해주세요!`;
        if (isNaN(userInput)) throw `숫자가 아닙니다!`;
      } catch (error) {
        let gameHint = document.getElementById(`numberHint`);
        gameHint.innerHTML = `힌트 : ` + error;
      }
    }
  </script>
  <div>
    <form>
      <h3>Number Game</h3>
      <p>1 부터 100 사이의 숫자를 입력해서 맞춰보세요!</p>
      <input type="number" id="inputNum" value="">
      <button type="button" onclick="guessGame()">숫자 추측</button>
      <p id="numberHint"></p>
    </form>
  </div>
  <hr>
  <!--문자열을 받아 문자열의 첫번째 글자를 대문자로 변환하는 프로그램을 만들어보자-->
  <script>
    function strChange() {
      let result = String(document.getElementById(`change0index`).value)
      console.log(result.charAt(0).toUpperCase());
      console.log(typeof result);
      document.getElementById(`change0index`).value = String(result.charAt(0).toUpperCase()) + String(result.slice(1))
      console.log(document.getElementById(`change0index`).value);
    }
  </script>
  <div>
    <p>문자열을 받아 문자열의 첫번째 글자를 대문자로 변환하는 프로그램을 만들어보자</p>
    <input id="change0index" type="button" value="changeWriting" onclick="strChange()">
  </div>
  <hr>
  <script>
    //1-movies배열 생성,2-터미네이터,트랜스포머 배열요소 추가,3-맨오브스틸 배열에추가,4-배열의 뒤에서2번째요소 스파이더맨으로 변경,5-배열의 마지막요소 꺼내서 경고박스표시
    let movies = new Array()
    movies[0] = `터미네이터`
    movies[1] = `트랜스포머`
    console.log(movies);
    movies[2] = `맨오브스틸`
    console.log(movies);
    console.log(movies.length);
    movies[1] = `스파이더맨`
    console.log(movies.length);
    console.log(movies);
    //alert(movies[2]);
  </script>
  <script>
    //배열에서 랜덤하게 하나의 요소 선택해서 출력하는 프로그램
    let fruits = [`바나나`, `사과`, `딸기`, `배`]
    let isPick = Math.floor(Math.random() * fruits.length)
    console.log(fruits[isPick]);
  </script>
  <script>
    let arrTest = ["hello", 10, 32.6, true]
    function find(item,value) {
      console.log(item.indexOf(value));
      return item.indexOf(value);
    }
    document.write(find(arrTest,"hello"))
    find(arrTest,"hello")
    document.write(find(arrTest,10))
    find(arrTest,10)
    document.write(find(arrTest,32.6))
    find(arrTest,32.6)
    document.write(find(arrTest,true))
    find(arrTest,true)
  </script>
  <script>
    function swear() {
      let userCheck = String(document.getElementById(`userChat`).value)
      let p_msg = document.getElementById(`pMSG`)
      let msg = `욕설은 옳지 않습니다.`
      if (userCheck == `XXX`) {
        p_msg.innerHTML = msg
      }
    }
  </script>
  <div>
    <form>
      <p>특정 단어(XXX) 입력시 메시지 출력</p>
      <input id="userChat" type="text" value="">
      <button type="button" onclick="swear()">확인</button>
      <p id="pMSG"></p>
    </form>
  </div>
</body>

</html>