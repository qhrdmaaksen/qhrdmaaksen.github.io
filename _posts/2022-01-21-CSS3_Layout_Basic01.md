---
layout: single
title: "css 레이아웃 기초"
---

<header>
  <p>블록 요소와 인라인 요소</p>
</header>
<section>
<dl>
  <dt>
    블록 요소
  </dt>
  <dd>
  h1,p,pre,form,table,blockquote,ul,li,div,header,nav
  </dd>
</dl>
</section>
<article>
  <dl>
    <dt>인라인 요소</dt>
    <dd>a,strong,em,img,input,span,br</dd>
  </dl>
</article>

<pre>
display 속성
  none = 없는 것으로 간주
  block = 블록 요소 정의
  inline = 인라인 요소로 정의
  hidden = 화면에 감춰짐
  * 주의 = 인라인 요소 안에 블록 요소를 넣으면 
    문제 발생 할 수 있음

css 기본적으로 4가지의 위치 설정 방법
  정적 위치 설정(static positioning)
    -정상적인 흐름에 따른 배치
    (디폴트 위치)
    -top/right/bottom/left 속성은 무시
  상대 위치 설정(relative positioning)
    -정상적인 위치가 기준점
    (정상적인 위치에서 오프셋만큼 떨어진 곳에 배치)
  절대 위치 설정(absolute positioning)
    -컨테이너의 원점이 기준
    (컨테이너 안에서 고정된 위치에 배치)
  고정 위치 설정(fixed positioning)
    -윈도우의 원점이 기준점
    (브라우저 윈도우 안에서 고정된 위치에 배치)

float 속성
  - 위 속성은 position:static 블록 요소에 사용됨
  - 위 속성이 사용되면 컨테이너 안 다른 요소가 
      이 요소를 감싸며 배치
  - 위 속성이 사용되면 position 이랑 
      offset 설정은 모두 무시
float 속성을 없애는 방법
  -clear 속성은 float 의 
    흐름을 제거하는 속성 (ex:clear:both;)

css offset
  -부모 박스의 좌측 상단으로부터 자식까지 x 및 y 거리
  (부모박스 position:static 이라면 부모로부터
     offset(거리)를 지정할 수 없으며, 
  relative,absolute,fixed 일때엔 offset 지정이 가능)

top/right/bottom/left 속성
  -요소의 위치를 결정 (포지션 static 에서는 무시됨)

z-index
  -요소가 겹쳐지는 순서를 제어할 때 사용 
  -주의 : z-index 는 요소의 포지션 속성이 절대 위치 or
     고정 위치 설정되어있어야 작동

요소의 크기 설정
  -width ,height : 요소의 가로 세로 크기
  min-width , min-height : 요소의 최소 크기
  max-width , max-height : 요소의 최대 크기

overflow 속성
  -hidden : 부모 영역을 벗어나는 부분을 
    보이지 않게 한다.
  -scroll : 부모 영역을 벗어나는 부분을 
    스크롤 할 수 있도록 한다.
  -auto : 자동으로 스크롤바가 나타난다 . 
  (overflow 속성을 설정하지 않으면,
     단순히 콘텐츠가 넘쳐버린다.)

display table 속성
    display 속성값 table, table-row, table-cell 등을
     사용해서 요소를 표(table)처럼 표현할 수 있습니다.
     표처럼 보이기 위해 
     사용할 수 있는 속성값들은 다음과 같습니다.

    table : table 요소처럼 표현합니다.
    table-caption : caption 요소처럼 표현합니다.
    table-column-group : colgroup 요소처럼 표현합니다.
    table-header-group : thead 요소처럼 표현합니다.
    table-footer-group : tfoot 요소처럼 표현합니다.
    table-row-group : tbody 요소처럼 표현합니다.
    table-cell : td 요소처럼 표현합니다.
    table-column : col 요소처럼 표현합니다.
    table-row : tr 요소처럼 표현합니다.
    위의 속성값으로 표처럼 표현되도록 만든 후에는,
    표를 꾸미는 것과 같은 방법으로,
    해당 요소를 꾸밀 수 있습니다. 주의할 점은,
    IE의 경우 8 이상에서 지원한다는 것입니다.

transition 속성
ex) transition:width 5s ; <--width 가 변경되면
  5초에 걸쳐서 서서히 변화하도록 전환 효과를 줌

<strong>css3 변환 transformation 기능</strong>
  -도형을 이동, 도형의 크기 변환, 도형 회전할 수 있다.
  -변환은 요소의 크기나 형태 위치를 변환하는 효과
  -요소는 2차원 또는 3차원적으로 변환될 수 있다
  transform 속성을 사용해서 좌표 공간을 변형해서 
  다른 요소에 영향을 미치지 않고 
  특정 요소의 위치를 바꿀 수 있다.
  
  transform : translate (10px,10px) x,y 축 10px씩 평행이동
  transform : rotate(45deg) 45도 회전
  transform : scale(2,1.2) x,y축 2배 1.2배 크기 변환
  transform : skew(20deg,10deg) x,y방향 비틀기 변환 [입체적으로보임]
  transform : matrix() 일반적인 변환

<strong>css3 3차원 변환</strong>
  translate3d(x,y,z) 3차원 평행 이동
  translateX(x) 3차원 평행 이동 x 축
  translateY(y) 3차원 평행 이동 y 축
  translateZ(z) 3차원 평행 이동 z 축
  scale3d(x,y,z) 3차원 크기 변환 
  scaleX(x) 3차원 크기 변환 x 축
  scaleY(y) 3차원 크기 변환 y 축
  scaleZ(z) 3차원 크기 변환 z 축
  rotate3d(angle) 3차원 회전 변환
  rotateX(angle) 3차원 회전 변환 x 축
  rotateY(angle) 3차원 회전 변환 y 축
  rotateZ(angle) 3차원 회전 변환 z 축
  perspective(n) 원근 변환
  backface-visibility 후면을 보이게하는 속성
  transform-origin 변환 원점을 설정
  -가장 대표적인 3차원 변환은 박스를 약간 옆으로 회전시키는 것 rotateY()를 사용하며,
    원근 변환을 주게 되면 입체적으로 회전한 것으로 보임

<strong>css3 애니메이션</strong>
  -키프레임(애니메이션 중간 중간에 객체의 위치와
  크기를 지정해주는 프레임)을 이용해서
   css 특성 값의 변화를 지정할 수 있음
  -css3 요소에 애니메이션을 적용할때
    속도 효과를 지정할 수 있다.
    linear,ease,ease-in(천천히 시작),
    ease-out(움직임이 멈출 때 쯤 
      변화의 정도가 서서히 감소), ease-in-out
  -커스텀 속도효과를 위해
    3차 베지어 곡선으로 지정할수 있다.

  <strong>@keyframes</strong>
  키프레임의 위치는 퍼센트로 지정
  각 키프레임에서 속성의 값을 지정
  (ex:
    @keyframes myani_test01 {
    0% {background-color: red; left: 0px; top: 0px;}
    25% {background-color: red; left: 100px; top: 0px;}
    50% {background-color: yellow; left: 200px; top: 0px;}
    75% {background-color: blue; left: 100px; top: 0px;}
    100% {background-color: blue; left: 0px; top: 0px;}
    }
  )
</pre>
