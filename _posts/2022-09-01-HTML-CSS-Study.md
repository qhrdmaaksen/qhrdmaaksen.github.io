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






















```