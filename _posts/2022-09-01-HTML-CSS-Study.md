---
layout: post
title: "HTML CSS Study!"
---

## HTML CSS Study 정리 모음

```js

================================================================
한사대
웹 기술

웹 클라이언트 -> http 요청(url) -> 웹 서버 -> 웹 문서 -> db -> 웹 문서 -> 웹 서버 -> http 응답(HTML 문서) -> 웹 브라우저

근거리통신망 LAN
광역통신망 WAN
통신 프로토콜(규격) 웹에서 사용 TCP/IP

동적 웹 애플리케이션
-CGI, 서블릿, JSP 통해 동적 웹 어플리케이션

네이티브 어플리케이션
-워드,스프레드시트,이메일 같이 컴퓨터에서 동작되는 소프트웨어
특징
-주된처리:해당 기기에서 처리
-화면출력:각 기기에서 출력
-어플설치:컴퓨터에 설치

웹 어플의 특징
주된처리: 사용자 컴퓨터가아니라 웹 서버상에서 진행
화면출력: html 로 표현된 문서가 공통의 웹 브라우저 상에 출력
어플설치:사용자 컴퓨터에 설치할 필요가없음

하이브리드 어플리케이션: 어플 설치 후 웹에서 진행

www 표현 형식 : html 형식 사용 (하이퍼 텍스트)

웹 서버 : 네트워크 상에 공개하는 html 을 저장하고 웹 클라이언트의 요청에 따라 필요한것을 전송해줌
웹 클라이언트: 웹 서버에 요청하여 html 파일을 받아 출력해줌

웹 서버용 소프트웨어: 오픈소스로 공개된 아파치, 마이크로소프트사의 IIS
웹 클라이언트 소프트웨어: ie,크롬,파폭,사파리

URL : 인터넷 상의 컨텐츠를 고유하게 지정하기 위한 구조
-웹브라우저가 웹 서버에서 원하는 자료ㅗ를 얻는 방법
-클라이언트가 서버에 어디있는 자료를 읽고싶다라고 지정해줘야함
-웹 브라우저로 사이트를 열람할때 주소창에 입력하는 문자열

URL 의 구성
-스킴 호스트명 경로명
-스킴:통신 프로토콜

https:암호화된 http 통신을 나타내는 스킴
mailto:이메일의 수취인을 나타내는 스킴
ftp:ftp 프로토콜을 통해 파일 획득을 나타냄
file:파일 시스템 속의 파일이나 디렉터리를 참조하기 위한 스킴

http:tcp/ip 통신 프로토콜 중에 하나
-웹 서버와 웹 클라이언트 간에 하이퍼텍스트 전송 프로토콜

통신프로토콜:통신을 위한 규약

RFC: URL 이나 HTTP 등 인터넷상에서 이용되는 규격이나 규약이 인터넷상에 공개되고있는것

CGI 웹 서버에 요청하고 응답받는 시스템
-동적 컨텐츠: 컴퓨터 프로그램을 이용해 컨텐츠에 작은 변화를 준 것
--웹 서버상에서 작동하는 프로그램이 html 을 생성해서 돌려줌
-정적 컨텐츠: 미리 준비된 html 을 돌려줌
CGI:웹 서버 상에서 동적 컨텐츠를 생성하는 프로그램을 동작시키기 위한 조합
-웹 서버와 컨텐츠를 생성하는 프로그램의 연동하는 구조
CGI 프로그램: C언어,파이썬,루비 등등
CGI 기술: 동적컨텐츠 생성,웹 브라우저에서 입력받아 처리하는 앱 제작 가능
-검색사이트,게시판시스템,인터넷쇼핑 등
서블릿:자바언어로 만들어짐
-JAVAEE 의 일부로 서블릿이라는 웹 앱 개발을 지원하기 위한 기능을 제공
--HTML 등의 동적 웹 컨텐츠를 생성하기 위해 자바로 만들어진 프로그램
---기본적으로 CGI 와 같은 개념에서 동작함
----웹 서버와 같은 프로세스 속에서 컨텐츠 생성 프로그램이 동작함
-----웹 컨테이너의 내부에서 서블릿을 진행

자바의 장점
-javaVM 사용: 가상 컴퓨터에서 동작하는 언어로 컴파일해서 실행함
C언어:플랫폼별로 앱을 개발해야함
자바:같은 앱을 여러 플랫폼에서 실행할수있음

자바 애플릿: 웹 브라우저의 화면 속에서 자바 프로그램을 실행할수있게 한것임
-HTML 로는 표현할수없는 그래픽적인 애플리케이션을 구현할수있음

서블릿 문제점
-화면 디자인 변경 어려움
-서블릿을 통해 출력되는 html 을 상상하기 어려움

JSP 자바 서버 페이지
-서블릿의 단점을 개선하기 위해 고안된 기술
-출력되는 HTML 에 거의 근접한 형태
-JSP 에서 동적으로 출력하고 싶은 부분을 <%%> 로 묶고 그안에 자바 프로그램 기술가능(스크립틀릿)
-페이지를 구성하는 HTML 을 기본으로 삼고 변경되는 부분만 자바로 작성

서블릿과 JSP 의 문제점
-대규모 웹 앱 개발이 어려워짐

웹 앱 프레임워크의 탄생
-재사용할수있는 부분을 확장해서 앱 개발을 더욱 쉽게하기 위해 만들어짐
-앱의 기반이 되는것으로 프레임워크를 토대로 필요한 부분을 만들어 나가면 원하는 앱을 단기간에 개발할수있음
-재사용은 복사와 라이브러리를 이용해 이뤄짐

웹 서버 프로그램 <-> 웹 문서 <-> db 

html 문서는 브라우저에 의해 해석되고 실행됨
html 문서는 일반 텍스트 편집기로 작성가능
html 문서는 웹 서버에 탑재되지 않더라도 브라우저가 설치된 환경에선 모두 실행이 가능

html 기본 구조
-인터넷 웹 브라우저에 글자나 그림을 표시해주는 프로그램 언어중 가장 기초가 되는언어
-웹에서 정보를 쉽게 찾아볼수있도록 고안된 언어
마크업: 정보를 쉽게 찾기위해 제목 본문 등에 따라 글시나 폰트 색상들을 다르게 지정

확장자는 .htm , .html 파일로 저장됨
html 태그 : 문서 html 문서임을 알려줌
head 태그 : 본문의 내용 조정 문서의 제목 사용언어 등을 나타냄
body 태그 : 웹 브라우저의 본문에 출력되는 부분
title 태그 : 웹 페이지의 제목 설정
<meta> : 웹 페이지의 사용언어 지정,
-검색엔진에서 검색을 하기위한 키워드 지정
-검색 엔진에서 웹 페이지의 설명 지정
-자동으로 웹 페이지의 내용 갱신 지정
-웹 페이지의 제작자 알려줌
-각종 스크립트 설정

<meta> attr http-equiv="refresh" content = 2; (2초 후 이동) http="경로"

body tag
bgcolor 웹 페이지 배경색을 설정
background 웹 페이지 이미지를 설정
bgproperties 배경 이미지의 속성 설정(스크롤 시 고정 여부)
vlink 링크된 텍스트 중 클릭하여 한번이라도 방문 경우의 색상 지정 기본색은 보라색
alink 링크된 텍스트를 누르는 순간에 나타나는 색상 지정 기본색 빨강

<H> 제목입력
<U> 텍스트에 밑줄치기
<S> 텍스트에 삭제라인 표시 

<MARQUEE> 태그 : 텍스트를 움직이게함
속성
-BEHAVIOR : 어떤 형태로 될건지
-DERECTION : 어느 방향으로
-LOOP : 텍스트의움직이는 횟수 지정
-SCROLLAMOUNT : 텍스트의 움직이는 간격 지정 픽셀단위
-SCROLLDELAY : 텍스트의 움직이는 속도 지정 밀리초 단위

목록태그
<UL> TAG : 원이나 사각형 등의 도형 목록
-속성
--circle, square, disc
<OL> TAG : 번호 순서대로의 목록
--1, A, a , L/i 번호를 어떻게 표현할건지
--start 속성 : 시작 숫자 (1부터 시작할건지 5부터할건지등)
dl tag : 용어에대한 정의 목록

기타 텍스트 태그
pre tag : 텍스트 모양 그대로 웹 페이지에 출력
blockquote tag : 텍스트 들여쓰기
<center> : 컨텐츠 문서 중앙 배치
hr tag : 가로 선 attr : width, size, align, noshade
웹 페이지에 특수문자 넣기 : ㄱ -> 한자키 

IMG TAG : 이미지 삽입
ATTR
-width, height : 크기
-border : 테두리
-align : 이미지 주변 텍스트 정렬
alt : 이미지 설명
hspace, vspace : 이미지 와 텍스트 간격
clear : float 기능 을 취소

a tag : 텍스트나 이미지에 링크 설정
attr
-href 경로 지정
-target 링크된 웹 페이지 표시 방법
--_self : 현재 브라우저 창에 출력
--_blank : 새로운 브라우저의 부모 창에 출력
--_parent : 현재 브라우저의 부모 창에 출력
--_top : 현재 브라우저의 최상위 창에 출력
name : web page 내에서 지정 위치로 이동시킴, 다른 a tag 의 속성 href='#red' 을 눌렀을 시 name='red' 속성이있는 페이지로 이동
map : 이미지 일부분 영역에 하이퍼 링크 설정 , name='Map' usemap='#Map' 사용
<img src ='경로' usemap='#Map'>
<map name='Map'>
	<area shape='circle' coords='100,100,30' href='경로'> 는 이미지에 100,100,30 위치에 동그라미 버튼 누르면 img 경로 이동

table tag 
caption tag : 테이블 위에 테이블 제목을 만듦
attr
-border, bordercolor : table line setting
-frame : 테이블의 외곽 선 설정
width,height : 테이블과 셀의 크기 설정
cellspacing, cellpadding : 셀 간 간격과 셀 안의 텍스트와의 간격 설정
rules : 테이블 내부에 선을 그려줌
rowspan cellspan : 셀 합치기

PHP : 웹 서버에서 실행됨
-웹 브라우저에서 HTTP 요청하면 웹 서버 프로그램에서 PHP 웹 문서에서
DBMS DATA 필요하다면 DB DATA 및 웹 문서를 가지고 HTTP 응답해줌
-fileName.php 확장자 사용
-PHP 해석기가 필요함
-운영체제가 달라도 호환성이 높음
----------------------------------------------------------------
PHP 웹 애플리케이션 개발 환경 구축
-웹 브라우저와 웹 서버, 웹 서버 언어,PHP 웹 서버와 웹 클라이언트의 동작원리
PHP 웹 개발 환경
-동작원리
웹->서버>PHP해석기>웹문서>DB>PHP해석기>서버>웹

APM:웹 서버를 구성하는 주요 도구인 아파치+PHP+MYSQL 의미
XAMPP: PHP TOTAL PACKAGE

-<?code?> tag 사용
-변수는 $ 붙여서 사용
-변수선언할때 데이터형을 따로 지정하지않음
-gettype() 함수는 사용된 변수의 데이터형을 보여줌
-echo : printf 와 같은 기능, 큰따옴표 안에 내용 출력, 기호 출력시 \ 사용
-문자열안에 변수사용시 변수명 앞뒤에 공백을 두거나 중괄호로 표시해야 출력됨

---------------------------------------

멀티미디어와 프레임의 활용
-웹 문서에 사용되는 사운드와 동영상 파일의 종류, 태그를 통해 멀티미디어와 프레임의 활용
<BGSOUND>:웹 문서가 실행되면 바로 사운드 실행(src,loop,balance,volume attr)
<EMBED>:웹 문서에 사운드를 비롯해 동영상이나 플래시 파일을 삽입할 때 사용
(autostart,hidden,width,height,loop,showStatusbar attr)
<FRAME>:두 개 이상의 웹 페이지를 하나의 화면에 표시하는 기능
각각의 웹 페이지를 각각 프레임이라 부름,각각의 프레임에는 프레임 고유의 이름이 설정됨
,프레임셋은 각각의 프레임을 관리해주는 파일로 문서 전체에대한 정보를 가지고있음
,프레임셋 문서는 바디 태그를 사용하지 않음
<IFRAME>:인라인 프레임의 약자로 HTML 문서를 프레임으로 나누는것이아니라 
원하는 위치에 프레임을 만들어 다른 HTML 문서를 불러들임

HTML 입력 양식 태그를 통해 HTML 입력 양식 활용
-<FORM>:웹 서버와 웹 클라이언트간의 양방향 상호작용을 위한 방법 제공
<INPUT>:사용자가 웹 페이지에 직접 데이터를 입력할수있도록 입력 상자를 만들어줌
<TEXTAREA>:여러줄의 텍스트 입력 형식
<SELECT><OPTION>:: 라디오 버튼과 비슷한 기능 여러개 선택 가능함


플러그인 프로그램
-영화나 음악을 웹 상에서 실행 할 수 있게하는 실행 프로그램
EX) 윈도우 미디어플레이어, 리얼 플레이어 등

사운드 파일 종류
-AU : 유닉스 시스템에서 사용되는 표준 오디오 파일
-MIDI:디지털 음악 규격에 사용되는 음악파일
-WAV: 아날로그로 녹음한 파일
-RA:멀티미디어 스트리밍 데이터 파일
-MP3:MPEG-1 의 오디오 압축 기술을 이용한 오디오 파일 압축률 우수
-WMA:MS 사에서 개발한 새로운 암축방식을 이용한 오디오파일, 실시간 스트리밍 가능
사운드 재생에 필요한 프로그램의 종류
-윈도우 미디어 플레이어, 리얼플레이어,윈엠프

동영상 파일의 종류
-AVI:MS 윈도우 RIFF 규격을 따르는 사운드와 동영상 파일
-Mov:애플사의 퀵타임에서 재생되는 동영상 파일
-MPG:표준 동영상 파일 형식, 압축률 높음
-RM/RAM:리얼네트워크사의 스트리밍 데이터 파일
-ASF:스트리밍 데이터 파일

---------------------------------------

CSS
-HTML 로 표현하기 힘든것을 도와주는 스크립트
-CASCADING
우선순위 HTML 태그속성-인라인스타일-임베디드스타일-링크드스타일-사용자의스타일 설정-브라우저의 기본설정

태그선택자
문맥 선택자:html 태그가 설정된 순서에 맞으면 css 가 적용됨
속성 선택자:html 태그가 가지고있는 class 와 id 속성값으로 css 를 설정할때 사용

가상요소:가상요소 선택자로 첫행과 첫 문자가있음,대부분 웹 브라우저와 호환성이 작음
가상클래스:가상클래스 선택자로 링크가 설정된 텍스트에 css 를 적용함

text 의 속성
-text-indent: 문단 첫 번째 줄 들여쓰기 길이 설정

---------------------------------------

js
-내장객체
screen:화면 정보 출력
navigator:브라우저 정보

DOM:문서 객체모델
-웹 문서를 작성할때 자유롭게 불러서 사용할수있는 객체 모델임
-웹 브라우저 안에있으며 웹 프로그래밍의 필수 도구임

이벤트:사용자나 시스템이 일으키는 작업
-이벤트 핸들러:이벤트를 처리하는 코드


================================================================


HTML 
-hyperText Markup language
--hyperText:하이퍼링크를 통해 어떤 문서에서 다른 문서로 접근할수있는 텍스트
---Markup: 표시하다
----요약: HTML 은 웹 브라우저를 통해 표시되는 웹페이지의 컨텐츠를 정의하기 위해 사용하는 언어

-html 문서는 파일의 확장자가 html or htm
-html 문서가 웹 브라우저를 통해 해석되고 표현되는 과정을 렌더링이라고함

<!DOCTYPE html> : HTML 최신 표준 문법으로 작성 문서라는 표시
<html></html> : html code 의 시작과 끝을 의미
<head></head> : html 문서에대한 설정 태그
<title></title> :html 문서에대한 제목으로 탭 표시
<hr> : 수평선 태그
<p></p> : 태그는 하나의 문단을 나타내며 자기만의 영역을 가진다 (블록레벨요소)
<h1></h1> : 블록레벨요소
&nbsp; : spaceBar 역할
<mark></mark> : 감싸고있는 컨텐츠에 형광펜 표시를 더해주는 태그
<strong></strong> :강조 태그
<em></em> : 기울기
<u></u> : 언더 라인 밑줄 표시
<ul></ul> : 블록레벨, 순서가 없는 기호로 목록 
<ol></ol> : 블록레벨, 순서가 있는 기호로 목록
<li></li> : 블록레벨, ol, ul 부모 태그에 항목 요소 표시 사용될 자식 태그
-ol>li*10 + tab 은 ol tag 안에 li tag 10 개 생성
<img> : 이미지 태그, 너비 높이 설정 px 로 가능
-title 속성 : 마우스 hover 시 title 튤팁 제공
<div></div> : 블록레벨 컨테이너
<span></span> : 인라인 컨테이너
<a href="#"></a> : href 속성을 통해 다른 페이지,전화번호,이메일 주소와 그 외
다른 url 로 연결할수있는 링크를 만든다, 인라인 요소 이며 주로 링크의 목적지나타냄
--href="tel:010-1234-1234" : 전화
--href="mailto:rlaalsdn8@gamil.com" " 이메일 연결
-target 속성 : "_self"= 현재 탭에서 열기, "_blank" 새탭에서 열기

블록레벨요소: 자기가 속한 영역의 너비를 모두 차지하여 블록을 형성
인라인요소:자기가 필요한 공간만큼만 차지함

전역 속성
-id : 요소에 고유한 이름을 부여하는 식별자 역할 속성
-class : 요소를 그룹 별로 묶을 수 있는 식별자 역할 속성
-style : 요소에 적용한 css 스타일을 선언하는 속성
-title : 요소에 추가 정보를 제공하는 텍스트 속성, 사용자에게 튤팁 제공

<main></main> : <main> 태그는 해당 문서의 <body> 요소의 주 콘텐츠(main content)를 정의할 때 사용,<main> 요소의 콘텐츠는 해당 문서의 중심 주제 
또는 주요 기능과 직접적으로 관련되어 있거나 확장되는 콘텐츠로 구성되어야 
하며, 문서 전반에 걸쳐 반복되는 내용을 포함해서는 안 됨,하나의 문서에는 단 
하나의 <main> 요소만이 존재해야 하며, <main> 요소는 <article>, <aside>, 
<footer>, <header>, <nav> 요소의 자손 요소가 되어서는 안 됨

<nav></nav> : 태그는 다른 페이지 또는 현재 페이지의 다른 부분과 연결되는 네비게이션 링크(navigation links)들의 집합을 정의할 때 사용
<nav> 요소를 사용하는 일반적인 예로는 메뉴, 목차, 인덱스 등이 있음
글을 읽지 못하는 사용자를 위한 스크린 리더기와 같은 브라우저는 <nav> 요소를 
사용하여 해당 콘텐츠의 초기 렌더링을 생략할지 여부를 결정

<section></section> : 태그는 HTML 문서에 포함된 독립적인 섹션(section)을 정의할 때 사용,<section> 요소는 보통 제목 요소(h1~h6)를 자식 요소로 
포함하고 있는 경우가 많음

<canvas></canvas> :태그는 주로 자바스크립트와 같은 스크립트를 이용하여 그래픽 콘텐츠를 그릴 때 사용, <canvas> 요소는 그래픽 콘텐츠를 위한 
컨테이너일 뿐 실제로 그림을 그리는 동작은 스크립트를 사용하여 구현함
<canvas> 요소 내부에 존재하는 텍스트는 해당 브라우저가 <canvas> 요소를 지원하지 않을 경우 브라우저 화면에 대신 나타나게 됨

<table><thead><tr><td><tbody><tfoot> : table 관련 tag

<figure></figure> : 독립적인 콘텐츠를 표현합니다. <figcaption> 요소를 
사용해 설명을 붙일 수 있습니다. 피규어, 설명, 콘텐츠는 하나의 단위로 참조함
, 개인적으로 액자처럼? 플로라이드 사진에 figcaption 그림 설명있는듯함

<cite> 요소는 저작물의 출처를 표기할 때 사용하며, 제목을 반드시 포함해야 
합니다. 적절한 맥락 아래에서는 출처를 축약해서 표기

<blockquote> 요소는 안쪽의 텍스트가 긴 인용문임을 나타냅니다. 주로 
들여쓰기를 한 것으로 그려집니다. (외형을 바꾸는 법은 사용 일람을 참고하세요) 
인용문의 출처 URL은 cite 특성으로, 출처 텍스트는 <cite> 요소로 제공할 수 
있음

<address> 요소의 콘텐츠에서 제공하는 연락처 정보 <address>는 컨텍스트에 
적합한 모든 형식을 취할 수 있으며 물리적 주소, URL, 이메일 주소, 전화번호, 
소셜 미디어 핸들, 지리적 좌표와 같이 필요한 모든 유형의 연락처 정보를 포함할 
수 있음
================================================================
react-router-dom
-{NavLink} compo : navigation 역할 css add 가능 activeClassName prop
-{Link} compo: <a> 역할 href 대신 to 사용
================================================================
100vw 100vh 100%

viewport
-웹브라우저에서 viewport 는 현재 창에서 문서를 볼 수 있는 부분임
-viewport 밖의 콘텐츠는 스크롤하기전엔 보이지 않음
viewport 단위는 viewport 의 치수를 기준으로 하기때문에 요소의 폭 높이 크기를 viewport 에 맞게 설정해야하는 상황에서 좋음
-상대 길이 단위 (em, rem, lh, vw, vh 등등 )
--상대단위 사용시 텍스트나 다른 요소의 크기가 페이지의 다른 모든것에 비례하여 조정됨
-절대 길이 단위 (px, cm mm 등등)

vw/vh
- vw 는 viewport 너비의 1%임 vh 는 높이의 1%
ex 1024 px 너비/ 600px 높이 === 1vw 는 10.24px / 1vh 는 6px 임

100% 와 100vw 차이점
-모든 기기에서 웹페이지 전체 화면 너비 기준은 100vw 임
-% 단위의 크기는 부모 요소 영향을 받음
--container 클래스는 부모인 body 크기에서 몇% 를 차지하느냐가 되는것임
================================================================
UI 디자인 가이드 공통 규칙 - 네이밍
공통 : 네이밍 순서
- 형태_의미_상태 OR 대분류_중분류_소분류 순서의 형식으로 작성
ex code 
btn_login_off (3단계 이상을 넘지 않는다)

이미지
-허용 문자: 영문 소문자, 숫자 등 사용가능
-숫자 규칙: 숫자는 단어의 시작으로서 사용하지 않는다

CSS
-폴더 규칙: 공통 사항은 공통 폴더로 분류하고 서비스 분류에 따라서 서비스명_대분류명 으로 구성한다
ex
공통 css : common.css
분류별 css : member_layout.css
-CSS 네이밍: 간결하고 스타일의 작동 바식이 드러나도록 작성한다
ex code
.move_btn {
  width: 108px;background:#ddddddd;
}
================================================================
반드시 기억해야하는 css 선택자 30 개

1. *
* {
 margin: 0;
 padding: 0;
}
고급 선택자로 이동하기 전에 초보자를 위해 쉬운 선택자부터 알아보죠.

별표는 페이지에 있는 전체 요소를 대상으로 합니다. 많은 개발자가 margin과 padding 값을 0으로 세팅하려고 이 선택자를 사용합니다. 간단한 테스트 용도로서는 괜찮습니다. 그러나, 저는 여러분에게 이 별표를 실전에서 사용하지 말라고 권합니다. 브라우저에 과부하가 걸리고, 사용하기에 적절하지 않습니다.

*를 자식 선택자에도 사용할 수 있습니다.

#container * {
 border: 1px solid black;
}
이 코드는 #container div의 자식 요소 전체를 대상으로 합니다. 한 번 더 말하지만, 이 선택자를 과다하게 사용하지 마세요.

데모 보기

호환성
IE6+
파이어폭스
크롬
사파리
오페라


2. #X
#container {
   width: 960px;
   margin: auto;
}
선택자 앞에 해시(#) 기호를 붙여서 id를 대상으로 삼습니다. 가장 흔하고 쉽게 사용됩니다. 하지만, id 선택자를 사용할 때는 조심스러워야 합니다.

자문해 보세요. 이 요소를 대상으로 하기 위해 id를 필히 적용해야 할까요?

id 선택자는 유연성이 없고 재활용할 수 없습니다. 가능한 처음에 태그 명이나 새로운 HTML 요소 중 하나, 아니면 가상 클래스라도 적어 보세요.

데모 보기

호환성
IE6+
파이어폭스
크롬
사파리
오페라

AD
Advertisement


3. .X
.error {
  color: red;
}
class 선택자입니다. id와 class의 차이점이라면, 후자는 여러 개의 요소를 대상으로 정할 수 있습니다. 스타일을 한 그룹의 요소에 적용할 때는 class를 사용하세요. 찾을 가망성이 거의 없는 요소에 id를 사용하고 그 유일한 요소에만 스타일을 적용하세요.

데모 보기

호환성
IE6+
파이어폭스
크롬
사파리
오페라


4. X Y
li a {
  text-decoration: none;
}
다음으로 가장 많이 언급하는 선택자는 descendant입니다. 선택자를 이용해 더 상세히 작업해야 할 때, 이 선택자를 사용합니다. 가령, 전체 앵커 태그를 대상으로 하기보다 순서를 매기지 않는 목록(unordered list)에 있는 앵커만 대상으로 한다면 어떨까요? 하위 선택자를 사용하면 상세해집니다.

꿀팁 - 선택자가 X Y Z A B.error처럼 보이면 여러분은 작업을 잘못하고 있습니다. 모든 요소에 꼭 가중치를 둬야 하는지를 늘 자문하세요.

데모 보기


AD
Advertisement
호환성
IE6+
파이어폭스
크롬
사파리
오페라


5. X
a { color: red; }
ul { margin-left: 0; }
만일 여러분이 id나 class가 아닌 type에 따라 한 페이지에 있는 모든 요소를 대상으로 삼고 싶다면 어떨까요? 간단히 type 선택자를 이용하세요. 순서가 정해지지 않은 목록 전부를 대상으로 해야 한다면 ul {}를 쓰세요.

데모 보기

호환성
IE6+
파이어폭스
크롬
사파리
오페라


6. X:visited와 X:link
a:link { color: red; }
a:visted { color: purple; }
클릭하기 전 상태의 앵커 태그 전체를 대상으로 하려고 :link 가상 클래스를 사용합니다.

:visited 가상 클래스로 하기도 합니다. 예상하듯이 이는 클릭했었거나 방문했던 페이지에 있는 앵커 태그에만 특정한 스타일을 적용할 수 있습니다.

데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


7. X + Y
ul + p {
   color: red;
}
인접 선택자로 부르는 선택자입니다. 앞의 요소 바로 뒤에 있는 요소만 선택합니다. 위 코드에서 각 ul 뒤에 오는 첫 번째 단락의 텍스트만 빨간색이 됩니다.

데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


8. X > Y
div#container > ul {
  border: 1px solid black;
}
일반 X Y와 X > Y의 차이점은 후자가 직계 자식만을 선택한다는 것입니다. 가령, 아래 마크업을 생각해 보세요.

   <div id="container">
      <ul>
         <li> List Item
           <ul>
              <li> Child </li>
           </ul>
         </li>
         <li> List Item </li>
         <li> List Item </li>
         <li> List Item </li>
      </ul>
   </div>
#container > ul 선택자는 id가 container인 div의 직계 자손인 ul만 대상으로 삼습니다. 예를 들어 첫 번째 li의 자식인 ul은 대상이 되지 않습니다.

이런 이유로 자식 선택자를 이용해 성능을 향상할 수 있습니다. 사실, 자바스크립트를 기반으로 하는 CSS 선택자 엔진으로 작업할 때 추천합니다.

데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


9. X ~ Y
ul ~ p {
   color: red;
}
이 형제 선택자는 X + Y와 유사하지만 덜 엄격합니다. 인접 선택자(ul + p)는 앞의 선택자 바로 뒤에 오는 첫 번째 요소만을 선택하지만, 이 선택자는 좀 더 관대합니다. 위의 예를 보면, ul 아래 있는 모든 p 요소를 선택할 것입니다.

데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


10. X[title]
a[title] {
   color: green;
}
속성 선택자(attributes selector)라고 말하며, 앞의 예에서 title 속성이 있는 앵커 태그만을 선택합니다. title이 없는 앵커 태그에는 특정한 스타일이 적용되지 않습니다. 그런데 더 상세히 작업해야 한다면 어떨까요? 음...

데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


11. X[href="foo"]
a[href="https://net.tutsplus.com"] {
  color: #1f6053; /* nettuts green */
}
위의 코드는 https://net.tutsplus.com;로 연결된 전체 앵커 태그에 스타일을 적용할 것입니다. 우리 브랜드 컬러인 녹색이 적용되겠지요. 그 외의 앵커 태그는 스타일의 영향을 받지 않습니다.

값을 큰따옴표로 감쌌음을 기억하세요. 자바스크립트 CSS 선택자 엔진을 사용할 때 활용하는 것도 잊지 마세요. 가능하면, 비공식적인 선택자보다 CSS3 선택자를 항상 사용하세요.

동작은 잘하겠지만, 융통성은 낮습니다. 만약 링크가 Nettuts+로 직접 이어지지만, 경로를 전체 url이 아닌 nettuts.com으로 한다면 어떨까요? 그 경우에 우리는 정규식 표현 문장을 약간 사용할 수 있습니다.

데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


12. X[href*="nettuts"]
a[href*="tuts"] {
  color: #1f6053; /* nettuts green */
}
야아. 우리에게 필요한 선택자네요. 별표는 입력값이 속성값 안 어딘가에 보여야 한다는 것을 표시합니다. 그렇게 이 구문은 nettuts.com, net.tutsplus.com 그리고 tutsplus.com까지도 적용하고 있습니다.

폭넓은 표현이라는 것을 알아 두세요. 만약 앵커 태그의 url에 tuts 문자열이 일부 Evato가 아닌 사이트로 연결되어 있다면 어떨까요? 더 자세히 작성해야 한다면, 문자열의 앞과 뒤에 ^와 $를 붙이세요.

데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


13. X[href^="http"]
a[href^="http"] {
   background: url(path/to/external/icon.png) no-repeat;
   padding-left: 10px;
}
웹사이트에서 외부로 연결된 링크 옆에 작은 아이콘을 어떻게 보이게 했는지 궁금해한 적이 있나요? 틀림없이 전에 본 적이 있을 것입니다. 링크를 클릭하면 전혀 다른 웹사이트로 이동하리라는 것을 알게 해주니까요.

캐럿 기호를 이용하는 쉬운 작업입니다. 문자열의 시작을 표기하는 정규 표현식에서 흔히 사용됩니다. 만약 http로 시작하는 href 값을 가진 앵커 태그를 대상으로 하고 싶다면, 위의 코드와 유사한 선택자를 사용하면 됩니다.

https://로는 찾아지지 않습니다. 이 표현은 부적절하고 https://로 시작하는 url도 마찬가지입니다.

여러분이 사진으로 링크 걸린 앵커 전체에 스타일을 적용하고 싶다면 어떨까요? 그 경우에는 문자열의 끝을 찾아봅시다.

데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


14. X[href$=".jpg"]
a[href$=".jpg"] {
   color: red;
}
문자열 끝에 적용하도록 정규 표현식 기호인 $를 한번 더 사용하겠습니다. 이번 경우에는 이미지(나 최소한 .jpg로 끝나는 url)로 링크가 걸린 앵커 전체를 찾을 것입니다. gif와 png는 영향받지 않습니다.

데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


15. X[data-*="foo"]
a[data-filetype="image"] {
   color: red;
}
8번 내용을 다시 참조합시다. 여러 가지 이미지 형식(png, jpeg, jpg, gif)은 어떻게 적용할 수 있을까요? 다음과 같이 우리는 선택자를 여러 개 만들 수 있습니다.

a[href$=".jpg"],
a[href$=".jpeg"],
a[href$=".png"],
a[href$=".gif"] {
   color: red;
}
그런데, 이 방식은 골치 아프고 비효율적입니다. 커스텀 속성을 사용하는 다른 해결 방식이 있습니다. 이미지로 링크 걸린 앵커마다 data-filetype 속성을 넣으면 어떨까요?

<a href="path/to/image.jpg" data-filetype="image"> Image Link </a>
그러면 갈고리(hook) 역할을 이용해 해당 앵커만 대상으로 삼는 일반 속성 선택자를 사용할 수 있습니다.

a[data-filetype="image"] {
   color: red;
}
데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


16. X[foo~="bar"]
 a[data-info~="external"] {
   color: red;
}

a[data-info~="image"] {
   border: 1px solid black;
}
친구에게 깊은 인상을 남겨줄 특별한 선택자가 있습니다. 이 요령을 알고 있는 사람은 그리 많지 않습니다. 물결표(~)를 이용하면 띄어쓰기로 구분되는 값이 있는 속성을 대상으로 할 수 있습니다.

15번에 있는 커스텀 속성 방식으로 data-info 속성을 만들면 됩니다. 이 속성은 우리가 메모하는 무엇이든지 띄어쓰기로 구분한 목록을 받을 수 있습니다. 이 경우, 외부 링크와 이미지 링크를 메모할 수 있습니다. 단지 예를 들면 말이죠.

"<a href="path/to/image.jpg" data-info="external image"> Click Me, Fool </a>
위의 마크업을 적당한 위치에 쓰면 ~ 속성 선택자 방식을 이용해 두 개의 값 중 하나라도 있는 태그를 대상으로 삼을 수 있습니다.

/* Target data-info attr that contains the value "external" */
a[data-info~="external"] {
   color: red;
}

/* And which contain the value "image" */
a[data-info~="image"] {
  border: 1px solid black;
}
꽤 훌륭하지요?

데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


17. X:checked
input[type=radio]:checked {
   border: 1px solid black;
}
이 가상 클래스는 라디오 버튼이나 체크박스처럼 체크되는 사용자 인터페이스 요소만을 대상으로 합니다. 아래 코드처럼 간단합니다.

데모 보기

호환성
IE9+
파이어폭스
크롬
사파리
오페라


18. X:after
before과 after 가상 클래스는 매우 효과적입니다. 사람들이 늘 이 두 클래스를 효과적으로 사용하는 새롭고 창의적인 방법을 찾고 있는 듯합니다. 이 클래스는 선택된 요소 주변에 콘텐츠를 생성합니다.

많은 사람이 clear-fix 핵을 접했을 때 이 클래스를 맨 먼저 도입했었습니다.

.clearfix:after {
    content: "";
    display: block;
    clear: both;
    visibility: hidden;
    font-size: 0;
    height: 0;
    }

.clearfix { 
   *display: inline-block; 
   _height: 1%;
}
이 핵은 요소 뒤에 공간을 덧붙이고 float 효과를 제거하는데 :after 가상 클래스를 사용했습니다. 특히 overflow: hidden; 방법이 불가능한 경우 여러분이 사용할 방법 중에 가장 훌륭한 방법입니다.

다른 창의적 방식은 그림자 제작에 관한 간단한 팁을 참조해 보세요.

CSS3 선택자 명세서를 보면, 가상 요소는 엄밀히 말해 두 개의 콜론(::)으로 표현되어야 합니다. 그렇지만, 일관성을 위해 유저 에이전트는 콜론을 하나 사용한 경우도 허용합니다. 사실 현재, 프로젝트에서 콜론이 한 개인 버전을 사용하는 게 더 현명합니다.

호환성
IE8+
파이어폭스
크롬
사파리
오페라


19. X:hover
div:hover {
  background: #e3e3e3;
}
에이. 이 선택자는 알고 있겠죠. 공식 용어는 사용자 동작(user action) 가상 클래스랍니다. 혼란스럽겠지만 그렇지는 않습니다. 사용자가 요소 위에 커서를 올릴 때 특정한 스타일을 적용하고 싶나요? 이 선택자로 처리하세요!

알아두세요. 앵커 태그가 아닌 태그에 :hover 가상 클래스를 적용했을 때 인터넷 익스플로러의 하위 버전에서는 반응하지 않습니다.

대부분 hover 상태에서, 가령 앵커 태그에 border-bottom을 적용할 때 이 선택자를 사용합니다.

a:hover {
 border-bottom: 1px solid black;
}
꿀팁 - border-bottom: 1px solid black;이 text-decoration: underline;보다 보기 더 좋습니다.

호환성
IE6+ (IE6에서 :hover는 반드시 앵커 요소에 적용해야 합니다.)
파이어폭스
크롬
사파리
오페라


20. X:not(선택자)
div:not(#container) {
   color: blue;
}
negation 가상 클래스는 특히 유용합니다. 제가 모든 div를 선택하고 싶은데, 그중에서 id가 container인 것만 빼고 싶다고 합시다. 위의 코드가 그 작업을 완벽하게 수행합니다.

혹은, (권장하지 않지만) 제가 단락 태그만 제외하고 요소 전체를 선택하고 싶다고 한다면 아래처럼 하면 됩니다.

*:not(p) {
  color: green;
}
데모 보기

호환성
IE9+
파이어폭스
크롬
사파리
오페라


21. X::가상 요소
p::first-line {
   font-weight: bold;
   font-size: 1.2em;
}
첫 번째 줄이나 첫 글자와 같이 요소 일부분에 스타일을 적용하는데 가상 요소(::로 표기되는)를 사용할 수 있습니다. 효과를 보려면 이 요소를 반드시 블록 레벨 요소에 적용해야 합니다.

가상 요소는 두 개의 콜론(::)으로 표시됩니다.

단락의 첫 글자
p::first-letter {
   float: left;
   font-size: 2em;
   font-weight: bold;
   font-family: cursive;
   padding-right: 2px;
}
이 코드는 페이지에 있는 단락을 모두 찾은 다음 해당 요소의 첫 글자만을 대상으로 하는 추상 개념입니다.

신문처럼 글의 첫 글자를 스타일로 꾸미는 데 자주 사용됩니다.

단락의 첫 줄
p::first-line {
   font-weight: bold;
   font-size: 1.2em;
}
마찬가지로 ::first-line 가상 요소는 요소의 첫 번째 줄에만 스타일을 적용합니다.

기존 스타일 시트와 일관되도록 유저 에이전트는 CSS 레벨 1과 2 (즉 :first-line, :first-letter, :after)에서 도입한 가상 요소의 이전 표기인 하나의 콜론도 수용해야 합니다. 이 명세서에서 도입된 새 가상 요소에는 호환성이 부족합니다. - 출처

데모 보기

호환성
IE6+
파이어폭스
크롬
사파리
오페라


22. X:nth-child(n)
li:nth-child(3) {
   color: red;
}
여러 요소 중에서 특정 요소를 지목하는 방법이 없었던 시절이 기억나나요? 그 문제를 풀어줄 nth-child 가상 클래스가 있답니다!

nth-child는 변숫값을 정수(integer)로 받습니다. 0부터 시작하지는 않습니다. 두 번째 항목을 대상으로 하고 싶다면 li:nth-child(2)로 작성합니다.

자식 요소의 변수 집합을 선택하는 데에도 이 방식을 활용할 수 있습니다. 가령, 항목의 4번째마다 선택하려면 li:nth-child(4n)로 작성하면 됩니다.

데모 보기

호환성
IE9+
파이어폭스 3.5+
크롬
사파리


23. X:nth-last-child(n)
li:nth-last-child(2) {
   color: red;
}
만약 ul에 항목이 엄청 많고, 여러분은 끝에서 세 번째 항목만 필요하다고 한다면 어떨까요? li:nth-child(397)로 작성하지 말고 nth-last-child 가상 클래스를 쓰면 됩니다.

이 선택자는 16번과 거의 동일합니다. 다만 집합의 끝에서부터 출발하면서 동작한다는 게 다릅니다.

데모 보기

호환성
IE9+
파이어폭스 3.5+
크롬
사파리
오페라


24. X:nth-of-type(n)
ul:nth-of-type(3) {
   border: 1px solid black;
}
child를 선택하지 않고 요소의 type을 선택해야 하는 날이 있을 것입니다.

순서를 정하지 않은 목록 5개가 있는 마크업을 상상해 보세요. 세 번째 ul에만 스타일을 지정하고 싶은데 그것을 지정할 유일한 id가 없다면, nth-of-type(n) 가상 클래스를 이용할 수 있습니다. 위의 코드에서 세 번째 ul에만 테두리 선이 둘려집니다.

데모 보기

호환성
IE9+
파이어폭스 3.5+
크롬
사파리


25. X:nth-last-of-type(n)
ul:nth-last-of-type(3) {
   border: 1px solid black;
}
일관성을 유지하도록 목록 선택자의 끝부터 출발해 지정한 요소를 대상으로 하는 nth-last-of-type을 사용할 수도 있습니다.

호환성
IE9+
파이어폭스 3.5+
크롬
사파리
오페라


26. X:first-child
ul li:first-child {
   border-top: none;
}
이 구조적 가상 클래스를 이용해 부모 요소의 첫 번째 자식만 대상으로 삼을 수 있습니다. 목록에서 맨 처음과 맨 나중 항목에서 테두리 선을 제거하는데 이 방식을 흔히 사용합니다.

예를 들면, 가로 행 목록이 있다고 합시다. 행마다 border-top과 border-bottom이 적용되어 있습니다. 글쎄요. 그 정렬에서 맨 처음과 마지막 항목이 약간 어색해 보이겠네요.

많은 디자이너가 이를 보완하려고 first와 last 클래스를 적용합니다. 그 대신에 여러분은 이 가상 클래스를 사용하면 됩니다.

데모 보기

호환성
IE7+
파이어폭스
크롬
사파리
오페라


27. X:last-child
ul > li:last-child {
   color: green;
}
first-child와 반대로 last-child는 부모 요소의 마지막 항목을 대상으로 합니다.

예제
이 클래스 중에 활용 가능한 사례를 보여주는 간단한 예제를 만들어 봅시다. 스타일이 적용된 항목을 제작하겠습니다.

마크업
  <ul>
     <li> List Item </li>
     <li> List Item </li>
     <li> List Item </li>
  </ul>
그냥 코드입니다. 단순한 목록일 뿐이지요.

CSS
ul {
 width: 200px;
 background: #292929;
 color: white;
 list-style: none;
 padding-left: 0;
}

li {
 padding: 10px;
 border-bottom: 1px solid black;
 border-top: 1px solid #3c3c3c;
}
이 스타일에 배경을 입히고, 브라우저상에서 ul 기본값을 제거하며, 깊이를 약간 주려고 li마다 테두리 선을 주겠습니다.

Styled List
목록에 깊이를 더하기 위해 각각의 li에 border-bottom을 적용합니다. 이는 그림자가 되거나 li 배경보다 어두운색이 될 것입니다. 다음에 배경보다 더 밝은 값을 border-top에 적용합니다.

단 한 가지 문제점은, 위의 이미지에서 보이듯, 순서에 정해지지 않은 목록의 맨 위와 맨 아래에도 테두리 선이 적용된다는 것입니다. 자연스럽게 보이지 않죠. :first-child와 :last-child 가상 클래스를 사용해 이 문제를 고쳐봅시다.

li:first-child {
    border-top: none;
}

li:last-child {
   border-bottom: none;
}
Fixed
야아. 고쳐졌군요!

데모 보기

호환성
IE9+
파이어폭스
크롬
사파리
오페라
맞아요. IE8은 :first-child를 지원하지만 :last-child를 지원하지 않습니다. 말도 안 되죠.


28. X:only-child
div p:only-child {
   color: red;
}
솔직히 여러분은 아마 only-child 가상 클래스를 거의 사용하지 않을 것입니다. 그렇더라도 쓸 수 있으니 써봐야 하겠죠.

이 선택자는 부모의 단 하나의 자식 요소를 지정할 수 있습니다. 위의 코드를 참조하면, 가령, div의 단 하나의 자식인 문단만 빨간색으로 칠해질 것입니다.

아래의 마크업을 생각해 봅시다.

<div><p> My paragraph here. </p></div>

<div>
   <p> Two paragraphs total. </p>
   <p> Two paragraphs total. </p>
</div>
이 경우, 두 번째 div의 문단은 대상이 되지 않고 오직 첫 번째 div가 대상이 됩니다. 하나 이상의 자식을 요소에 적용하는 순간에 only-child 가상 클래스의 효과는 사라지게 됩니다.

데모 보기

호환성
IE9+
파이어폭스
크롬
사파리
오페라


29. X:only-of-type
li:only-of-type {
   font-weight: bold;
}
이 구조상의 가상 클래스는 기발한 방식으로 사용될 수 있습니다. 부모 컨테이너에 형제 요소가 없는 요소를 대상으로 합니다. 예로, 단 하나의 목록 아이템인 ul 전부를 대상으로 삼습니다.

우선, 이 작업을 어떻게 완료할지 자신에게 질문해 보세요. 여러분은 ul li로 하겠지만, 목록 아이템 전체가 대상이 됩니다. 유일한 해결 방법은 only-of-type을 사용하는 것입니다.

ul > li:only-of-type {
   font-weight: bold;
}
데모 보기

호환성
IE9+
파이어폭스 3.5+
크롬
사파리
오페라


30. X:first-of-type
first-of-type 가상 클래스로 해당 type의 첫 번째 형제 선택자를 선택할 수 있습니다.

테스트
이해를 돕도록 테스트를 해봅시다. 아래 마크업을 코드 편집기에 복사해 넣으세요.

<div>
   <p> My paragraph here. </p>
   <ul>
      <li> List Item 1 </li>
      <li> List Item 2 </li>
   </ul>

   <ul>
      <li> List Item 3 </li>
      <li> List Item 4 </li>
   </ul>   
</div>
다음 내용을 읽기 전에 "List Item 2"만 대상으로 하는 방법을 생각해 보세요. 생각났다면 (혹은 포기했더라도) 다음으로 넘어갑니다.

해결 방법 1
이 테스트를 푸는 방법은 여러 가지입니다. 이 중에서 몇 가지를 살펴보겠습니다. first-of-type을 사용해서 시작해 보지요.

ul:first-of-type > li:nth-child(2) {
   font-weight: bold;
}
이 코드는 기본적으로 "페이지에서 순서를 중요시하지 않는 첫 번째 목록을 찾고 나서 목록 아이템인 직계 자식만 찾아라."라고 이야기합니다. 그다음, 그 결과 세트에서 두 번째 목록 아이템만 걸러냅니다.

해결 방법 2
다른 방법은 인접 선택자를 사용하는 것입니다.

p + ul li:last-child {
   font-weight: bold;
}
이 시나리오에서는 p 태그 바로 뒤에 있는 ul을 찾고 나서 그 요소의 가장 마지막 자식을 찾습니다.

해결 방법 3
이 선택자를 써서 원하는 대로 불쾌해하거나 쾌활해 할 수 있습니다.

ul:first-of-type li:nth-last-child(1) {
   font-weight: bold;   
}
이번에는 페이지에 있는 첫 번째 ul을 잡고 나서 가장 첫 번째 목록 아이템을 찾습니다. 바로 아래부터 시작해서요! :)
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================
================================================================






















```
