---
layout: post
title: "CSS 방법론 정리!"
---

## 코드는 재산이다, 나중에 도움된다, 정리잘하자

```js

CSS 방법론 : WEB 에서 css 의 영향이 높아지며 css 사용시 class name 을 어떻게 작성할지 어떤 방식으로 
style 을 write 하는지 등 css 를 효율적으로 작성하기위해 정의된 일종의 규칙

크게 OOCSS, BEM, SMACSS 로 나뉘어져있으며 상황에따라 다르게 적용됨
---------------------------OOCSS-----------------------------------
OOCSS : (Object Oriented CSS) 객체 지향 css 는 css 를 module 방식으로 작성해 중복을 줄이는 방법론
- 가장 많이 사용되며 structure 와 style 을 분리해 작성함
- 중복되는 design element 를 따로 빼서 작성하기 때문에 반복적으로 사용가능함,
코드의 재사용성이 높아져 적은 코드량으로 최적의 성능을 보임
-공통된 부분을 찾아 어디서나 재활용 할 수 있다는 장점이있으며 다중 클래스 사용으로 코드의 가독성이 떨어질 수 있는 단점 존재함

구조와 모양을 분리하거나 결합시킴
ex code
기존 방식
class="menu_btn menu_skin"
OOCSS 방식
class="btn skin menu"
//.btn 은 공통 버튼 스타일 정의
//.skin 은 공통 스킨 스타일 정의
---------------------------BEM-----------------------------------
BEM : (Block Element Modifier) 블록 요소 상태로 구분해 class name 을 작성하는 방식의 방법론
- BEM 은 블록, 요소, 상태 세가지로 구성되며 각 부분을 __ 와 -- 로 구분 짓게됨,
어떻게 보일지가 아닌 어떤 목적인지에 초점을 두어 이름을 작성함
- 엄격한 네이밍 규칙을 따르며 클래스명이 용도, 형태를 잘 표현해주며 직관적으로 알 수 있는 것이 장점,
단점은 클래스명이 길고 복잡해 질 수 있다는 단점 존재

블록 : 재사용성이 가능하며 기능적으로 독립이 가능한 컴포넌트, 일반적으로 하나의 단어를 사용하며 길어질 경우 - 사용
ex code
.header
.block
.main

요소 : 블록을 구성하는 단위 __ 를 사용
ex code
.header
.header__tap
.header__content
.header__logo__button

상태 : 블록이나 요소의 속성으로 -- 사용
ex code
.header--hide
.header__tap--big
.header__content--disabled
---------------------------SMACSS-----------------------------------
SMACSS : (Scalable and Modular Architecture for CSS) 확장 가능한 모듈 식 아키텍쳐, CSS 를 범주화로 패턴화 하고자하는 방법론
- 작성할 CSS 를 비슷한 종류끼리 모아 다섯가지 스타일로 나눠 각 유형에 맞는 선택자와 작명법, 코딩 기법 제시,
5 가지 (기본base, 레이아웃layout, 모듈module, 상태state, 테마theme) 의 범주를 제시함

기본base : Reset, Variable 등을 포함하며 !important 를 쓰지 않음
ex code
body, form, p, table, button, fieldset, input {
  margin: 0;
  padding: 0;
}

레이아웃layout : 주요 요소 id 와 하위 요소 class 로 구분하며 접두사를 사용
ex code
// layout => l-
// 주요 요소 작성
#header {
  width: 400px;
}
#aside {
  width: 40px;
}
// 하위 요소 작성
.l-width #header {
  width: 650px;
  padding: 10px;
}
.l-width #aside {
  width: 100px;
}

모듈module : 재사용성이 높은 구성 요소를 정의
ex code
.stick
.stick-name
.stick-number

상태state : 요소의 상태 변화를 표현하고 접두사 is- 또는 s- 를 사용
ex code
.is-error
.is-hidden
.is-disabled

테마theme : 사용자가 선택 가능 하도록 스타일을 재선언하여 사용
ex code
// base.css
.heder {
  background-color : red;
}
// theme.css
.header {
  background-color : orange;
}

SMACSS 사용시 지켜야할 유의사항 4 가지
1. 파생된 CSS 선택자 사용 금지
2. ID 셀렉터 사용금지
3. !important 사용금지
4. 다른 개발자들이 이해할 수 있도록 class name 을 의미있게 작성
----------------------------------------------------------------
CSS 방법론 사용 이유
1. 원활한 유지보수 위함
2. 코드의 재사용성 높임
3. 클래스명만으로도 무슨 내용인지 예측 할 수 있게 함

CSS 를 사용 할 때 상황에 알맞은 CSS 방법론을 선택해 작성하자




```