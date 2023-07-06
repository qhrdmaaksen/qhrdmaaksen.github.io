---
layout: post
title: "naver-clone(feat: ZeroCho)"
---

## 코드는 재산이다, 나중에 도움된다, 정리잘하자

```js

- 처음 일을 맡아 진행할 때 바로 키보드에 손을 대지말고 먼저 생각하고 정리하자
- 가로 세로 법칙을 적용 시켜 구역을 나누어보자

- head 는 html 문서 설명 (meta data)
- favicon 가져오고 싶을때 (ex: naver.com/favicon.ico)

- div tag 특징 : block 요소 (width 100% 다 차지함), 줄바꿈이 일어난다
- display: inline 은 width, height 너비 높이가 적용되지 않는다

- 폴더에서 파일 확장명 및 숨긴 파일 표시는 항상 켜놓자

- 이미지 스프라이트 : 이미지를 하나로 합쳐서 사용하는 것(예전 브라우저를 위해 사용)
-- 이미지 스프라이트에서 이미지 설정 시 background-position: x축 y축; 으로 설정하고 
background-repeat: no-repeat; 으로 설정하면 이미지가 반복되지 않는다

- 브라우저 개발자 모드에서 force state 를 통해 hover 상태 및 여러 상태를 확인할 수 있다

position
- 기본적으로 tag 의 position 은 static 이다
- relative 는 static 처럼 취급되지만 top, left, right, bottom 을 사용할 수 있다
-- relative 는 자기 자신을 기준으로 움직인다
-- relative 는 자기 자신을 기준으로 움직이기 때문에 다른 요소들에게 영향을 주지 않는다
- absolute 는 static 이 아닌 가장 가까운 부모를 기준으로 움직인다
- fixed 는 스크롤을 내려도 항상 화면에 고정되어 있다 (뷰포트 기준으로 배치)
- sticky 는 스크롤 영역 기준으로 배치 (fixed 처럼 동작하지만 스크롤 영역 기준으로 배치)

z-index
- z-index 는 형제 요소들끼리만 비교한다

display: none; 은 스크린 리더기에 읽히지 않는다


border-box 는 width, height 를 포함한다
- content-box 는 width, height 를 포함하지 않는다
- box-sizing: border-box; 를 사용하면 width, height 를 포함한다


css 는 위에서 아래로 읽는다
- 같은 요소에 같은 속성이 있을 경우 아래에 있는 속성이 적용된다


svg
- svg 는 이미지를 확대해도 깨지지 않는다










```