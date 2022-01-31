---
layout: single
title: "자바스크립트 기초00"
---

# 자바스크립트 기초00
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
        let age2_message = `내 나이는 ${30+5}세 입니다.`;
        console.log(name_massage);
        console.log(age_message);
        console.log(age2_message);
```

```js
//숫자형 number
        let age2 = 35;
        console.log(1+2);//더하기
        console.log(5-2);//빼기
        console.log(4*2);//곱하기
        console.log(4/2);//나누기
        console.log(7%2);//나머지
        
        let x = 1/0;
        console.log(x);//infinity 무한대
        let hello = "hello";
        let y = hello/2;
        console.log(y);//NaN (not a number)출력
```
```js
//참 거짓 boolean
        let name_bool = "minwoo";
        let age_bool = 35;
        console.log(name_bool==`minwoo`);
        console.log(age_bool<40);

        //null , undefine
        let age_unde ;
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
