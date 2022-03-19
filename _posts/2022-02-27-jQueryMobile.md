---
layout: single
title: "제이쿼리 모바일 basic"
---

# 제이쿼리 모바일 html , css

```js
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="http://code.jquery.com/mobile/1.3.1/jquery.mobile-1.3.1.min.css">
  <script src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
  <script src="http://code.jquery.com/mobile/1.3.1/jquery.mobile-1.3.1.min.js"></script>
  <link rel="stylesheet" href="../css/mystyle.css">
  <style>
    body {
      background-color: rgb(214, 230, 240);
    }
  </style>
  <title>Document</title>
</head>

<body>
  <!--- data-role 속성으로 UI를 구성한다. - JQM에서는 기본적으로 div 태그에 data-role 속성이 아래와 같은 값을 가진 구조를 가진다. data-role="header" : 문서의 상단영역. 툴바형태로 제공되며 보통 h1 태그와 함께 쓰인다.-->
  <div data-role="page">
    <div data-role="header">
      <h1>jQuery mobile Web</h1>
    </div>
    <div data-role="content">
      <div>
        <p>안녕하세요, 제이쿼리 기본 구조에 오신것을 환영합니다.</p>
        <h3>제이쿼리 모바일</h3>
        <ul>
          <li>웹 앱은 앱처럼 보이는 웹 페이지이며 앱처럼 사용자와 상호작용하며 모바일 화면에 적절한 레이아웃을 사용하고 매번 전체 페이지를 다시 로드하지않고도 필요한 부분만을 로드한다.</li>
          <li>제이쿼리 모바일은 모바일 프레임워크중에 하나임</li>
          <li>제이쿼리 모바일은 터치-기반의 HTML5 UI 프레임워크</li>
          <li>제이쿼리 모바일로 작성한 웹 앱은 모든 종류의 스마트폰,테블릿,데스크탑에서 소스 변경 없이도 동일한 모습으로 실행될 수 있음</li>
        </ul>
        <ol>
          <legend>모바일 프레임워크를 사용하는 이유</legend>
          <li>- 터치 기반의 사용자 인터페이스를 쉽고 빠르게 작성할 수 있다.</li>
          <li>- 모바일에 어울리는 인터페이스를 구현하고 있기때문에 네이티브 웹과 같은 느낌을 준다</li>
          <li>- 모바일 플랫폼의 특성을 파악해 처리하고있기때문에 개발자가 신경을 쓸 필요가 없다는 점이 중요하다</li>
        </ol>
        <ol>
          <legend>제이쿼리 모바일을 사용하는 애플리케이션의 기본 구조</legend>
          <li>1개의 css 파일과 2개의 자바스크립트 라이브러리를 포함시키면 됨</li>
          <li>특징 - 기본적으로 div 요소를 만들고 data-role 속성으로 요소의 역할을 지정한다는 점</li>
          <li>-- 다음 단계로 콘텐츠 컨테이너 안에 콘텐츠를 추가하는 것 ex_ div data-role="content"</li>
          <li>어떤 표준 HTML 요소라도 추가할수있으며 헤딩,리스트,단락 등 어떤 요소라도 추가할수있다 .</li>
          <li>개발자 자신만의 커스텀 스타일을 작성해 커스텀 레이아웃을 생성해도 됨</li>
        </ol>
        <p>제이쿼리 모바일을 사용하려면 아래와 같이 추가해주면된다.</p>
        <pre>
      &lt;link rel="stylesheet" href="http://code.jquery.com/mobile/1.3.1/jquery.mobile-1.3.1.min.css"&gt;
      &lt;script src="http://code.jquery.com/jquery-1.9.1.min.js"&gt;&lt;/script&gt;
      &lt;script src="http://code.jquery.com/mobile/1.3.1/jquery.mobile-1.3.1.min.js"&gt;&lt;/script&gt;
    </pre>
      </div>
      <div>
        <dl>
          <dt>리스트 뷰</dt>
          <dd>제이쿼리 모바일은 여러가지 종류의 리스트 뷰를 제공하며 모바일 앱에서는 특히 중요하다.</dd>
          <dd>리스트에서 data-role="listview" 를 추가해주면되며, data0inset="true" 속성은 리스트 뷰를 inset 모듈처럼 보이게한다</dd>
          <dd>data-filter="true" 는 동적 검색 필터를 추가해준다</dd>
        </dl>
        <div data-role="content">
          <ul data-role="listview" data-inset="true" data-filter="true">
            <li><a href="">배틀그라운드</a></li>
            <li><a href="">서든어택</a></li>
            <li><a href="">리니지</a></li>
            <li><a href="">오딘</a></li>
          </ul>
        </div>
      </div>
      <div data-role="content">
        <ol>
          <legend>슬라이더</legend>
          <li>제이쿼리 모바일은 자동적으로 터치-친화적인 스타일 위젯으로 향상되는 폼 요소를 가지고있다</li>
          <li>HTML5 에서 제공되는 슬라이더도 변형되어 그대로 제공됨</li>
          <li>여기선 data-role 이 필요없다</li>
          <li>모든 폼 요소는 label 속성을 가지고있어야하며 폼 요소의 그룹은 form 태그로 둘러쌓여야 한다.</li>
        </ol>
      </div>
      <div data-role="content">
        <p>여기는 슬라이드 컨텐츠 공간입니다.</p>
        <form>
          <label for="slider-0">인풋 슬라이더</label>
          <input type="range" name="slider" id="slider-0" value="25" min="0" max="100">
        </form>
      </div>
      <div data-role="content">
        <ul>
          <legend>버튼</legend>
          <li>가장 흔한것으로 링크를 버튼으로 변경하는것이다</li>
          <li>링크보다 버튼이 클릭하기 쉬우며 링크로 시작해서 링크에 data-role="button" 속성만 추가해주면 된다.</li>
          <li>data-icon 속성을 이용해 아이콘을 추가할수있으며 아이콘 위치는 data-iconpos 속성으로 설정된다.</li>
        </ul>
      </div>
      <div data-role="content">
        <script>
          $(document).ready(function () {
            $(`#clickMe`).click(function () {
              alert(`클릭해주셔서 감사합니다`)
            })
          })
        </script>
        <p>여기는 버튼 콘텐츠 공간입니다.</p>
        <a href="#" data-role="button" data-icon="star" id="clickMe">클릭 미!!!</a>
      </div>
      <div data-role="content">
        <ul>
          <legend>기타 UI 컴포넌트</legend>
          <li>제이쿼리 모바일은 다양한 컴포넌트가 있으며 제이쿼리 모바일 홈페이지를 참고해서 사용하면 좋다</li>
          <li>http://jquerymobile.com/demos</li>
        </ul>
      </div>
      <div data-role="content">
        <ul>
          <legend>테마 swatch(견본,샘플?) 선택</legend>
          <li>제이쿼리모바일은 스와치라고 불리는 테마 프레임워크를 가지고있으며 부트스트랩과 비슷하게 다양하게 많이있기에 찾아보자</li>
          <li>툴바,콘텐츠,버튼 색상의 집합 등 등 지원함</li>
        </ul>
      </div>
      <div data-role="content">
        <ul>
          <legend>UI Build</legend>
          <li>제이쿼리모바일은 홈페이지에가보면 codiqa 라는 UI 빌더를 소개하며 필요한만큼 요소를 마우스로 끌어와 사용자 인터페이스를 작성할수도있다</li>
          <li>작성된 HTML 코드를 확인할수도있다</li>
          <li>제이쿼리모바일 시멘틱 마크업을 사용하고 앞으로 향상이 가능하도록 설계되있다</li>
          <li>내가 원하는대로 간단하고 빠르게 이것 저것 디자인해서 코드를 뽑아 사용하면된다. 템플릿 같은 느낌이다</li>
        </ul>
      </div>
      <div data-role="content">
        <ul>
          <legend>페이지 링크</legend>
          <li>제이쿼리모바일은 페이지 링크 규칙을 사용하며 기본적으로 개발자는 이전과 동일하게 페이지를 요소에 링크할수있다 .</li>
          <li>제이쿼리모바일은 Ajax 를 이용해 자동적으로 페이지 요청처리를 한다 .</li>
          <li>Ajax 가 가능하지 않다면 기본적인 http 요청이 사용됨</li>
          <li>Ajax 를 사용하기 싫다면 rel="external" or data-ajax="false" 속성을 사용하면 전체 페이지 다시 읽기가 되고 애니메이션을 사용하는 페이지 전환도 이뤄지지 않는다.</li>
          <li>제이쿼리모바일은 다양한 페이지 전환을 지원하며 설정하려면 ex_ &lt;a href="index.html" data-transition="pop"&gt; 와 같이 사용</li>
          <li>페이지 전환은 플랫폼에 따라 지원되지 않으며 안드로이드에서는 ex_ .ui-page { -webkit-backface-visibility: hidden; } 코드를 추가해야함</li>
        </ul>
      </div>
      <div data-role="content">
        <ul>
          <legend>대화 상자</legend>
          <li>페이지를 링크할때 data-rel="dialog" 속성을 추가하면 페이지가 model 대화 상자가 됨</li>
          <li>dialog 속성이 추가되면 프레임워크는 둥근 코너 스타일을 만들며 페이지 마진을 크게하고 배경을 어두운 색으로해서 대화 상자가 페이지 앞에 매달려 있는 듯한 효과를 냄</li>
          <li>- &lt;a href="foo.html" data-rel="dialog"&gt; Open 대화창 &lt;/a&gt;</li>
        </ul>
      </div>
    </div>
    <div data-role="footer">
      <h4>Thank You!</h4>
    </div>
  </div>
</body>

</html>
```

```css
body {
  background-color: rgb(214, 230, 240);
}
h4 {
  color: red;
}

legend  {
  font-weight: bold;
}

dt {
  font-weight: bold;
}
p {
  color: rgb(34, 72, 77);
}

#clock {
  font: 2em sans-serif;
}

#page {
  padding: 5px;
  width: 960px;
  margin: 20px auto;
}

#header {
  height: 50px;
}

#main {
  width: 600px;
  float: left;
}

#sidebar {
  width: 300px;
  float: right;
}

#footer {
  clear: both;
}

@media screen and (max-width: 980px) {
  #page {
    width: 94%;
  }

  #main {
    width: 65%;
  }

  #sidebar {
    width: 30%;
  }
}

@media screen and (max-width: 700px) {
  /*media 타입이 screen이며 최대너비가 980픽셀이라면*/
  #main {
    width: auto;
    float: none;
  }

  #sidebar {
    width: auto;
    float: none;
  }
}

@media screen and (max-width: 480px) {
  #header {
    height: auto;
  }

  #h2 {
    font-size: 24px;
  }

  #sidebar {
    display: none;
  }
}

#header,
#main,
#sidebar,
#footer {
  border: solid 1px red;
}

#header {
  background-color: yellow;
}

#sidebar {
  background-color: aliceblue;
}

#main {
  background-color: aqua;
}

#footer {
  background-color: coral;
}

```