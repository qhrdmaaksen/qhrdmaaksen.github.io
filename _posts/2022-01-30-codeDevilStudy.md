---
layout: post
title: "자바스크립트 기초00"
---

## 자바스크립트 기초00

<div>
    <p>
        자바 스크립트에서 변수는 let 선언<br>
        변하지 않은 값은 const 선언
    </p>
    <p>
        <ol>
            <li>
                변수는 문자, 숫자 , $ , _ 사용 가능
            </li>
            <li>
                첫글자는 숫자가 될 수 없다.
            </li>
            <li>
                예약어는 사용 할 수 없다.    
            </li>
            <li>
                가급적 상수는 대문자로 알려주는게 좋다.
            </li>
            <li>
                변수명은 읽기 쉽고 이해할 수 있게 선언해주자.
            </li>
        </ol>
        <br>
        <ul>
            문자형 String
            <li>
                const name = "minwoo"; //쌍따옴표
            </li>
            <li>
                const name = 'minwoo'; //따옴표
            </li>
            <li>
                const name = `minwoo`; //벡틱(${ }표현식 사용가능)
            </li>
            <li>
                const message = "I'm minwoo";
            </li>
            <li>
                const message2 = 'I/'m minwoo'; (벡터안에 / 는 ' 를 특수문자로 인식)
            </li>
            <li>
                const message3 = "I'm ${name}";
            </li>
            <li>
                const message4 = "나는 ${30+5}세 입니다.";
            </li>
        </ul>
    </p>
    
</div>

```js
//문자열 String
let name = "minwoo";
let age = 35;
//console.log(age);
//alert(name);
let name_massage = `내 이름은 ${name}입니다.`;
let age_message = `내 나이는 ${age}입니다.`;
let age2_message = `내 나이는 ${30 + 5}세 입니다.`;
console.log(name_massage);
console.log(age_message);
console.log(age2_message);
```

```js
//숫자형 number
let age2 = 35;
console.log(1 + 2); //더하기
console.log(5 - 2); //빼기
console.log(4 * 2); //곱하기
console.log(4 / 2); //나누기
console.log(7 % 2); //나머지

let x = 1 / 0;
console.log(x); //infinity 무한대
let hello = "hello";
let y = hello / 2;
console.log(y); //NaN (not a number)출력
```

```js
//참 거짓 boolean
let name_bool = "minwoo";
let age_bool = 35;
console.log(name_bool == `minwoo`);
console.log(age_bool < 40);

//null , undefine
let age_unde;
console.log(age_unde);
let name_null = null;
console.log(name_null);

//typeof 연산자
//내가 만든 코드라면 알아보기 쉽겠지만 다른 개발자가 작성한 코드 변수타입을 알아야하거나
//api 통신등을 통해 받아온 데이터를 타입에따라 다른방식으로 처리해야할때 많이사용함
console.log(typeof 3);
console.log(typeof name);
console.log(typeof true);
console.log(typeof "xxx");
console.log(typeof null);
console.log(typeof undefined);

//문자열 짜집기
const appli_im = "나는 ";
const aplli_im2 = " 입니다.";
const aplli_age = 35;
console.log(appli_im + name + aplli_im2);
console.log(appli_im + aplli_age + " 세 " + aplli_im2);
```

```js
//대화 상자 응용
//alert 알려줌 , prompt 입력받음 , confirm 확인받음
let alert_greetings = "HelloWorld";
//alert(`alert_greetings`);
//let prom_name = prompt("이름을 입력해주세요.");
//let prom_date = prompt("예약일을 입력해주세요.","2022-1-");
//alert("안녕하세요,"+prom_name+"님 환영합니다.");
//벡틱 응용
//alert(`안녕하세요. ${prom_name} 님 환영합니다.`);
//alert(`${prom_date} 날짜로 예약이 완료되었습니다.`);

//alert 는 대화상자 명시 팝업
//prompt 는 입력받을 대화상자 팝업, 취소누르면 null 반환
//confirm 은 확인 취소 대화상자 true,false 반환

//단점으로는
//1.기본 대화상자를 사용하면 스크립트가 일시 정지된다(대화상자 창이 없어져야 다른 활동 가능)
//2.스타일링을 설정할 수 없다. (그래서 html 과 css로 만드는 모달창을 많이 활용함)
//장점으로 기본 대화상자는 빠르고 간단하게 적용가능해 활용을 많이함
```

```js
//String() 문자열 변환
//Number() 숫자형 변환
//Boolean() 불린형 변환
console.log(
  String(3),
  String(name),
  String(true),
  String("xxx"),
  String(null),
  String(undefined)
);
console.log(
  Number(123),
  //Number(123asd),
  Number(true), //true 1반환
  Number(false), //false 0반환
  Number(0), // 0반환
  Number(`0`), // true반환
  Number(undefined), // 0반환
  Number(``), // false반환
  Number(` `) // true 반환
);
//Boolean() 의 false
//숫자 0 , 빈 문자열 `` , null , undefined , NaN
console.log(
  Boolean(0),
  Boolean(``),
  Boolean(null),
  Boolean(undefined),
  Boolean(NaN)
);
//수능 당사자 19세에게 인사말
let exam_age = 19;
if (exam_age > 20) {
  console.log(`성인입니다, 시험 대상자가 아닙니다.`);
} else if (exam_age === 19) {
  console.log(`시험 대상자입니다. 수능 대박나세요`);
} else {
  console.log(`안녕히가세요`);
}
// OR _ 이름이 MINWOO 이거나 , 성인이면 통과
// AND _ 이름이 MINWOO 이며 , 성인이면 통과
let or_name = `minwoo`;
let or_age = 21;
if (or_name === `minwoo` && or_age === 21) {
  console.log(`이름이 MINWOO 이며 , 성인`);
} else {
  console.log(`해당되는 조건이 없습니다.`);
}
// NOT
// 나이를 입력받아 성인이 아니면 통과안됨
//let age_adult = prompt(`나이를 입력해주세요.`);
//let age_adult2 = age_adult >= 20;
// if (age_adult2) {
//     console.log(`성인입니다.`);
// } else if(!age_adult2){
//     console.log(`성인이아닙니다. 돌아가세요.`);
// }
//1부터 10까지 로그
for (let i = 1; i <= 10; i++) {
  console.log(i);
}
console.log(`--------------------`);
let i = 0;
while (i < 10) {
  console.log(i + 1);
  i++;
}
//continue,짝수만
for (let i = 0; i < 10; i++) {
  if (i % 2) {
    continue;
  }
  console.log(i);
}
//사고 싶은 과일을 물어보고 가격 알려주기
//사과 : 100원
//바나나 : 200원
//키위 : 300원
//멜론 : 400원
//수박 : 400원
let fruits = prompt(`사고 싶은 과일을 입력해주시면 가격을 알 수 있습니다.`);
switch (fruits) {
  case `사과`:
    console.log(`사과는 100원 입니다.`);
    break;
  case `바나나`:
    console.log(`바나나는 200원 입니다.`);
    break;
  case `키위`:
    console.log(`키위는 300원 입니다.`);
    break;
  //break; 를 넣어주지 않았기에 break 를 만나기전까지 수행한다.
  case `멜론`:
  case `수박`:
    console.log(`400원 입니다.`);
    break;
  case ``:
    console.log(`과일 이름을 입력하지 않았습니다.`);
    break;
  case null:
    console.log(`과일 이름을 입력하지 않았습니다.`);
    break;
  default:
    console.log(`목록에 해당 과일 이름은 없습니다. 목록을 확인해주세요.`);
    break;
}
```

```js
//함수
function sayHello(name) {
  console.log(`Hello,${name}`);
}
sayHello(`minwoo`);
console.log(`--------------------`);

//전역 변수
let msg = `hello`;
console.log(`함수 호출 전`);
console.log(msg);

function myName(name) {
  //지역 변수
  if (name) {
    msg += `, ${name}`;
    console.log(`함수 내부 호출`);
    console.log(msg);
  }
}
myName(`MINWOO`);
console.log(`함수 호출 후`);
console.log(msg);

//or
let newName = `min`;

function say2Hello(name) {
  let newName = name || `friend`;
  let msg = `hello, ${newName}`;
  console.log(msg);
}
say2Hello();
say2Hello(`joon`);
console.log(`--------------------------`);
//default value
function say3Hello(name = `friend`) {
  let msg = `hello, ${name}`;
  console.log(msg);
}
say3Hello();
say3Hello(`min`);
console.log(`---------------------`);
//return 값 반환
function returntest(num1, num2) {
  return num1 + num2;
}
let return_result = returntest(3, 3);
console.log(return_result);
console.log(`--------------`);
//함수 표현식
let fun_expression = function () {
  console.log(`error`);
};
fun_expression();
console.log(`------------`);
//화살표 함수
let arrow_fun = () => {
  console.log(`arrow`);
};
arrow_fun();
console.log(`--------------`);
//화살표 함수, 리턴 문
let arrow_fun_re = (num3, num4) => num3 + num4;
let result_arrow = arrow_fun_re(5, 5);
console.log(result_arrow);
```

```js
//객체
const superman = {
  ob_name: `vitamin`,
  ob_age: 35,
};
console.log(superman.ob_name);
console.log(superman.ob_age);
//객체에 추가
superman.skin = `yellow`;
console.log(superman.skin);
superman.hair = `black`;
console.log(superman.hair);
console.log("superman: ", superman);
//객체에서 삭제
delete superman.skin;
console.log("superman: ", superman);
//함수를 하나 만들어서 이름과 나이를 받아서 객체를 반환하는 함수
function get_name_age(name, age) {
  return {
    name: name,
    age: age,
    hobby: `game`,
  };
}
let minwoo = get_name_age(`minwoo`, 35);

console.log(minwoo);
//위 함수를 축약형으로 변환
let get_name_age1 = (name, age) => {
  return {
    name,
    age,
    hobby: `game`,
  };
};
let minwoo1 = get_name_age1(`minwoo`, 35);
console.log(minwoo);
//minwoo 1 에 age 가 있는지 여부 확인
console.log(`age` in minwoo1);
console.log(`============`);
//성인 미성년자 판별
let minjee = {
  name: `minjee`,
  age: 33,
};
let minseok = {
  name: `minseok`,
  age: 19,
};
let minwoo00 = {
  name: `minwoo`,
};

function judgment_adult(user) {
  if (user.age < 20 || !(`age` in user)) {
    return false;
  }
  return true;
}
console.log(`성인 판별 코드`);
console.log(`성인 판별 : `, judgment_adult(minjee));
console.log(`성인 판별 : `, judgment_adult(minseok));
console.log(`성인 판별 : `, judgment_adult(minwoo00));
console.log(`===========`);
//객체 for.......in
let minwoo01 = {
  name: `min`,
  age: 35,
};
for (i in minwoo01) {
  console.log(minwoo01[i]);
}
```

```js
//method:객체 프로퍼티로 할당 된 함수
let superman2 = {
  name: `minwoo`,
  age: 35,
  fly: function () {
    console.log(`날아가유`);
  },
};
superman2.fly();
let user = {
  name: `minwoo`,
  say4Hello: function () {
    console.log(`hello, ${this.name}`);
  },
};
user.say4Hello();
console.log(`==============`);
//method
let boy = {
  name: `vita777`,
  showName: function () {
    // <-- method 에서는 객체를 직접 써주기 보다는 this 를 사용해주는게 좋다.
    console.log(`hello, i'm ${this.name}`); //console 에 ${boy.name}으로 입력해주면 아래 boy=null이 적용돼 찾을 수 없고 ,
    //this.name 은 오로지 객체안에 name 을 가르키기때문에 man.showName(); 은 vita777을 출력하게된다.
  },
};
let man = boy;
boy = null;
man.showName();
// let boy = {
//     name: `minmin`,
//     sayThis: () => { //화살표 함수로 method를 작성하면 this 는 boy 를 가리키는게아니라 window 전역 객체를 가리킴
//         console.log(this); // this 는 boy 객체를 가리킴
//     }
// };
// boy.sayThis();
//method 를 사용해서this 를 사용한다면 화살표함수는 사용하지 않는게 좋다.
console.log(`================`);
//배열(문자,숫자,객체,함수,불린 등도 포함될 수 있다.)
//배열은 몇개의 method 를 가지고있다.
//push(): 배열 끝에 추가
//pop(): 배열 끝 요소 제거
//unshift(): 배열 앞에 추가
//shift(): 배열 앞 제거
let days = [`화`, `수`, `목`, `금`, `토`];
console.log(`현재 배열`);
console.log(days);
console.log('배열 제일 앞에 "월"추가');
days.unshift(`월`);
console.log(days);
console.log('배열 제일 끝에 "일"추가');
days.push(`일`);
console.log(days);
console.log('배열 제일 끝에 "일" 제거');
days.pop(`일`);
console.log(days);
console.log('배열 제일 앞에 "월" 제거');
days.shift(`월`);
console.log(days);
console.log("배열의 0 번째 '월' 로 변경");
days[0] = `월`;
console.log(days);
console.log(`배열 전체 길이 보기`);
console.log(days.length);
console.log("for 문 사용해서 차례로 출력");
for (let index = 0; index < days.length; index++) {
  console.log("days[index]: ", days[index]);
}
console.log("for ..of 문 사용해서 차례로 출력");
for (const iterator of days) {
  console.log(iterator);
}
```
