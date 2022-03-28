---
layout: single
title: "제이쿼리 및 이벤트 활용 01"
---

## 제이쿼리 및 이벤트 활용 01

```js

<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>jQuery</title>
  <script src="http://code.jquery.com/jquery-3.6.0.min.js"></script>
  <link rel="stylesheet" href="../css/jquery_ajax_jsonEx.css">
</head>

<body style="background-color: lightgreen;">
  <script>
    $(document).ready(function () {
      $(`#hideWriting`).click(function () {
        $(this).hide()
      })
    })
    $(document).ready(function () {
      $(`p`).show()
    })
  </script>
  <div>
    <p>제이쿼리는 Ajax호출이나 dom 조작도 훨씬 간단하게 할 수 있다.</p>
    <p>HTML 문서에서 특정 요소를 쉽게 찾을 수 있다.</p>
    <p>HTML 콘텐츠를 쉽게 변경할 수 있다.</p>
    <p>이벤트를 쉽게 처리할 수 있다.</p>
    <p>페이지 상의 콘텐츠를 쉽게 애니메이트 할 수 있다.</p>
    <p>네트워크를 통해 새로운 컨텐츠를 쉽게 가져올 수 있다 ( Ajax,JSON</p>
    <p>브라우저의 종류나 브라우저의 버전을 따질 필요가 없다. 모든 차이점은 제이쿼리 안에서 해결한다.</p>
    <p>제이쿼리를 웹 페이지에서 사용하는 두가지 방법
      <br>
      첫번째로 jQuery.com 에서 다운받아 사용하기
      <br>
      두번째로 실행 시 구글이나 마이크로소프트에서 제이쿼리 파일을 포함하는 방법
    </p>
  </div>
  <hr>
  <div>
    <h3 id="hideWriting">클릭하면 글씨가 사라집니다.</h3>
  </div>
  <hr>
  <div>
    <p>div태그로 사각형을 만들고 마우스 커서가 사각형 안으로 넘어오면 변수의 값을 증가시키는 시켜 화면에 출력하는 프로그램</p>
    <div id="mouseExRactangl">
      <p>마우스를 올려주세요</p>
      <p id="Pvalue">0</p>
    </div>
  </div>
  <script>
    //마우스 이벤트 - 마우스가 요소안으로 진입하면 mouseenter 이벤트 발생
    //반대로 마우스 요소를 빠져나가면 mouseleave 이벤트 발생
    //위에서 배웠던 mousedown은 마우스가 클릭되있는 순간 발생
    //mouseup 은 마우스가 클릭되었다가 떼지는 순간 이벤트 발생
    //mouseover는 마우스가 특정 요소 위에있을때 이벤트 발생
    let i = 0;
    $(`#mouseExRactangl`).mouseover(function () {//id 에서 마우스가 올라가면 동작
      $(`p:first`, this).text(`mouseover`)//첫번째 p의 요소의 텍스트 변환
      $(`p:last`, this).text(++i)//p의 마지막의 텍스트에 1씩 더한다
    })

  </script>
  <hr>
  <script>
    //focus와 blur 이벤트
    $(document).ready(function () {
      $(`#focusInputEx`).focus(function () {
        $(this).css(`background-color`, `yellow`)
      })
      $(`#focusInputEx`).blur(function () {
        $(this).css(`background-color`, `white`)
      })
    })
  </script>
  <div>
    <p>입력 필드를 만들고 포커스를 얻으면 입력필드의 배경색을 노랑색으로 변경, 포커스를 잃으면 흰색으로 변경</p>
    아이디 : <input type="text" id="focusInputEx">
  </div>
  <hr>
  <p>이벤트 처리기 함수 안에서 사용 가능한 정보</p>
  <p>pageX,pageY - 이벤트가 발생했을 당시의 마우스 위치
    <br>
    type - 이벤트의 종류 ex_ `click`
    <br>
    which - 눌려진 마우스 버튼이나 키
  </p>
  <div id="log"></div>
  <script>
    $(document).mouseover(function (e) {
      $(`#log`).text(`e.pageX : ` + e.pageX + `, e.pageY : ` + e.pageY + `, e.type : ` + e.type + `, e.which : ` + e.which)
    })
  </script>
  <hr>
  <script>
    //jQuery 를 이용한 애니메이션 효과
    $(document).ready(function () {
      $(`#showButton`).click(function () {
        //$(선택자).show(duration,complete)duration-slow,fast,밀리초단위 입력가능,complete-콜백함수로서 show()완료된 후 호출되는 메서드 지정
        $(`#coffeeImg`).show(`slow`)
      })
    })
  </script>
  <div>
    <img id="coffeeImg" src="../image/etc/coffee_painting.jpg" width="200" height="100" style="display: none;">
    <button id="showButton" type="button">Show it</button>
  </div>
  <hr>
  <script>
    $(document).ready(function () {
      $(`#showButton02`).click(function () {
        $(`#coffeeImg02`).toggle(`fast`)
      })
    })
  </script>
  <div>
    <p>toggle() - 요소가 감추어져 있으면 표시,표시되어있으면 감춤</p>
    <img id="coffeeImg02" src="../image/etc/coffee_painting.jpg" width="200" height="100" style="display: none;">
    <button id="showButton02" type="button">Show it</button>
  </div>
  <hr>
  <script>
    $(document).ready(function () {
      $(`#imgButton03`).click(function () {
        $(`#spaceImg`).animate({
          left: `100px`,
          width: `200px`,
          height: `100px`,
          opacity: `0.5`,
        })
      })
    })
  </script>
  <div>
    <p>animate() - 가장 일반적인 애니메이션을 작성할 때 사용하는 함수, 어디로나 이동이 가능하고 어떤 효과도 가능
      <br>
      css 속성을 변경해서 애니메이션을 만듦
      <br>
      $(selector).animate(properties, duration, easing,complete)
      <br>
      properties - 애니메이트될 css 속성, 목표값을 여기에 적음
      <br>
      duration - speed 는 slow , fast or 밀리초 단위 지정
    </p>
    <img id="spaceImg" src="../image/thumnails/spaceView.png" style="position: relative;" width="100" height="50">
    <button type="button" id="imgButton03">animate()</button>
  </div>
  <hr>
  <p>stop() - 모든 애니메이션을 중간에 중단할때 사용 ex_ $(`#id`).stop()</p>
  <hr>
  <script>
    $(document).ready(function () {
      $(`#fadeInBT`).click(function () {
        $(`#spaceFade`).fadeIn()
      })
      $(`#fadeOutBT`).click(function () {
        $(`#spaceFade`).fadeOut()
      })
    })
  </script>
  <div>
    <p>fadeIn(),fadeOut() - 요소를 표시할때 영화처럼 천천히 등장 or 빠르게 등장
      <br>
      ex_ $(selector).fadeIn(duration,complete)
    </p>
    <img src="../image/thumnails/spaceView.png" id="spaceFade" width="300" height="200" style="display: none;">
    <br>
    <button type="button" id="fadeInBT">fadeIn</button>
    <button type="button" id="fadeOutBT">fadeOut</button>
  </div>
  <hr>
  <script>
    $(document).ready(function () {
      $(`#slideUpBT`).click(function () {
        $(`#spaceFade02`).slideUp()
      })
      $(`#slideDownBT`).click(function () {
        $(`#spaceFade02`).slideDown()
      })
    })
  </script>
  <div>
    <p>slideUp(),slideDown() - 요소를 밀어올리거나 밀어내린다</p>
    <img src="../image/thumnails/spaceView.png" id="spaceFade02" width="300" height="200" style="display: none;">
    <br>
    <button type="button" id="slideUpBT">slideUp</button>
    <button type="button" id="slideDownBT">slideDown</button>
  </div>
  <hr>
  <script>
    $(document).ready(function () {
      $(`#methodChaining`).click(function () {
        $(`#chainingImg`).show(`slow`).fadeOut(`slow`).slideDown(`slow`)
      })
    })
  </script>
  <div>
    <p>이미지 요소를 화면에 나타내고 이어서 페이드아웃 슬라이드 다운으로 한 요소에대해 여러개의 메소드를 적용해보자(메소드체이닝)</p>
    <img id="chainingImg" src="../image/thumnails/blackHole.png" width="300" height="200" style="display: none;">
    <br>
    <button type="button" id="methodChaining">메소드 체이닝</button>
  </div>
  <hr>
  <script>
    $(document).ready(function () {
      $(`#textBT`).click(function () {
        confirm($(`#valWriting`).text())
      })
      $(`#htmlBT`).click(function () {
        confirm($(`#valWriting`).html())
      })
      $(`#textBT02`).click(function () {
        $(`#valWriting`).text(`텍스트 메서드로 변경됨`)
      })
      $(`#htmlBT02`).click(function () {
        $(`#valWriting`).html(`<b>HTML 메서드로 변경됨</b>`)
      })
    })
  </script>
  <div>
    <p>제이쿼리를 이용한 DOM 변경
      <br>
      제이쿼리에서는 돔 트리에 접근해 노드의 내용을 가져오거나 or 변경할수있고 동적으로 노드를 추가하거나 or 삭제할수도있다.
    </p>
    <ol>
      <li>요소의 내용을 가져오거나 변경할수있다 - text() - 선택된 요소의 텍스트 반환</li>
      <li>html() - 선택된 요소의 HTML 태그가 포함된 컨텐츠 반환</li>
      <li id="valWriting">val() - <span>입력</span> 필드의 값을 반환한다.</li>
      <li style="display: none;" id="valWriting02">val() - <span>입력</span> 필드의 값을 반환한다.</li>
      <li>요소의 속성을 가져오거나 변경할 수 있다. - attr()</li>
      <li>요소의 스타일 속성을 가져오거나 변경할수있다 - css() </li>
      <li>요소를 추가하거나 삭제할 수 있다 - append() , remove()</li>
      <li>position() - 요소의 위치를 반환한다.</li>
    </ol>
    <button type="button" id="textBT">text()</button>
    <button type="button" id="htmlBT">html()</button>
    <hr>
    <button type="button" id="textBT02">textChange()</button>
    <button type="button" id="htmlBT02">htmlChange()</button>
  </div>
  <hr>
  <p>attr() - 선택된 요소의 속성 값을 가져온다</p>
  <hr>
  <script>
    $(document).ready(function () {
      $(`#val`).click(function () {
        confirm($(`#inputVal`).val())
      })
    })
  </script>
  <div>
    <p>입력필드의 값 읽어오기</p>
    이름 : <input type="text" value="" id="inputVal">
    <br>
    <button type="button" id="val">val()</button>
  </div>
  <hr>
  <script>
    $(document).ready(function () {
      $(`#apEx`).click(function () {
        $(`#insertP`).append("<b style=`color:red`>아무개야</b>")
      })
      $(`#ppEx`).click(function () {
        $(`#insertP`).prepend("<b style=`color:red`>개똥이야  </b>")
      })
    })
  </script>
  <div>
    <p>DOM 에 요소 추가하기 - 제이쿼리를 사용하면 돔 트리의 기존 요소 아래에 새로운 컨텐츠를 추가할 수 있다. 대표적으로 append() 많이 사용</p>
    <ol>
      <li>append() - 선택된 요소의 끝에 새로운 컨텐츠를 추가</li>
      <li>prepend() - 선택된 요소의 처음에 새로운 컨텐츠를 추가</li>
      <li>after() - 선택된 요소의 뒤에 컨텐츠를 삽입</li>
      <li>before() - 선택된 요소의 앞에 컨텐츠 삽입</li>
    </ol>
    <p id="insertP">안녕 내 이름은 , </p>
    <button type="button" id="apEx">append()</button>
    <button type="button" id="ppEx">prepend()</button>
  </div>
  <hr>
  <div>
    <p>콘텐츠 삭제하기 - remove() - 선택된 요소와 그 자식 요소를 삭제한다.
      <br>
      empty() - 선택된 요소의 자식 요소를 삭제한다.
    </p>
  </div>
  <hr>
  <script>
    $(document).ready(function () {
      $(`#getCss`).click(function () {
        let valueCss = $(`#racBlue`).css(`background-color`)
        $(`#resultRac`).text(`css background-color 속성 : ` + valueCss)
      })
      $(`#cssChange`).click(function () {
        $(`#racBlue`).css(`background-color`, `red`)
      })
    })
  </script>
  <div>
    <p>제이쿼리를 이용한 css 조작</p>
    <ul>
      <li>css() - 선택된 요소의 스타일 속성을 설정하거나 반환</li>
      <li>addClass() - 선택된 요소에 하나 이상의 클래스를 추가</li>
      <li>removeClass() - 선택된 요소에 하나 이상의 클래스를 삭제</li>
    </ul>
    <br>
    <div id="racBlue"></div>
    <p id="resultRac"></p>
    <button type="button" id="getCss">css속성가져오기</button>
    <button type="button" id="cssChange">css속성 변경하기</button>
  </div>
  <hr>
  <script>
    $(document).ready(function () {
      $(`#adCla`).click(function () {
        //$(`#exCssP`).addClass(`exAddCla`)
        $(`#exCssP`).toggleClass(`exAddCla`)
      })
    })
  </script>
  <div>
    <p>addClass() - 선택된 요소에 css 클래스를 적용하는 것, 따라서 기존 요소의 스타일을 어떤
      클래스 스타일로 순식간에 변경 할 수 있다.
      <br>
      removeClass() - 선택된 요소로부터 css 클래스를 삭제하는 것
      toggleClass() - 선택된 요소로부터 css 클래스를 껏다 켰다 할 수 있는 기능
    </p>
    <p id="exCssP">예제 단락입니다.</p>
    <button type="button" id="adCla">addClass</button>
  </div>
  <hr>
  <script></script>
  <div>
    <p>요소의 크기 알아보기
      <br>
      width() - 요소의 가로 크기 반환(패딩,경계,마진은 들어가지 않음)
      <br>
      height() - 요소의 세로 크기 반환
      <br>
      ex_ $(`#id`).width()
      ex_ $(`#id`).height()
      <br>
      브라우저의 폭이나 HTML 문서 전체의 폭도 알수 있음
      <br>
      ex_ $(window).width() - 브라우저 뷰포트의 폭
      <br>
      ex_ $(document).width() - HTML 문서의 폭
    </p>
  </div>
</body>

</html>

```
