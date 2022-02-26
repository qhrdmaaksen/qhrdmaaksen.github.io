---
layout: single
title: "반응형 웹 basic"
---

# 반응형 웹

<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="../css/mystyle.css" />
    <title>반응형 웹</title>
  </head>

  <body>
    <div>
      <dl>
        <dt>반응형 웹 디자인</dt>
        <dd>responsive web design = RWD</dd>
        <dd>
          - css 미디어 쿼리를 통해 브라우저 상태값을 읽어 브라우저 창의
          크기,화면방향,화면 비율 등을 파악
        </dd>
        <dd>-- 절대값 대신 상대적인 값을 이용해 페이지 레이아웃을 설정</dd>
        <dd>
          --- 부모 요소의 크기에따라 이미지와 미디어의 크기가 자동으로 조절됨
        </dd>
        <dt>미디어 타입</dt>
        <dd>미디어의 종류뿐만 아니라 장치의 물리적인 특성을 알수있음</dd>
        <dd>미디어 쿼리는 2개의 요소를 포함함</dd>
        <dd>
          - &lt;link rel="stylesheet" type="text/css" media="screen and
          (max-device-width: 480px)" href="small.css"&gt; 에서 미디어의 타입은
          screen이며 원하는 장치의 수평 해상도가 480px 이고 해당된다면
          작은화면이라 인식해 small.css 를 로드한다는 의미이며 해당되지않는다면
          link 는 무시됨
        </dd>
        <dd>
          미디어쿼리는 화면의 해상도보다 많은 미디어 특징을 제공하며 원한다면
          and 키워드를 이용해 여러 특징값을 검사할수있음
        </dd>
        <dd>@media 규칙을 이용해서 내 css로 직접 포함 시킬수도있음</dd>
        <dd>
          <pre>
        @media screen adn (max-device-width: 480px) {
          .colum {
            float: none;
          }
        }
      </pre
          >
        </dd>
        <dd>또는 @import 지시어의 일부로 사용 가능</dd>
        <dd>
          <code>
            @import url("small.css") screen and (max-device-width: 480px)
          </code>
        </dd>
      </dl>
      <div id="page">
        <div id="header">
          <h3>반응형 웹 ex_01</h3>
        </div>
        <div id="main">
          <h3>Main</h3>
          BufferedReader와 Scanner 차이점! 1 minute read 문득 궁금해진
          BufferedReader 클래스와 Scanner 클래스 차이점!Permalink 우리가 공부를
          하다보면 문득 같은 기능을 가졌지만 어떤 차이점이있을까? 라는 궁금증을
          가져볼 수 있습니다. 그럴때 우리는 그 궁금증을 그냥 지나가지말고 한번
          쯤 검색을 해서 궁금증을 해소하는 습관을 갖춘다면 조금씩 한발자국
          발전해 나갈 수 있다고 생각합니다. 먼저 많이 사용해보셨을 Scanner scan
          = new Scanner (System.in); package curious; import java.util.Scanner;
          public class study { public static void main(String[] args) { Scanner
          scanner = new Scanner(System.in); System.out.println("원하는 숫자를
          입력하세요"); String input = scanner.nextLine(); int num =
          Integer.parseInt(input); System.out.println(num); } } 자바 수업을
          듣거나 공부하다보면 BufferedReader 보다는 Scanner를 먼저 배우게되는
          경우가 많으실거고 저또한 그랬었습니다. 위와같이 input 에
          scanner.nextLine 으로 입력받은 값을 담아 parseInt로 String 으로
          입력받은 문자열 값을 정수로 변환시켜 num에 저장하고 System 클래스에
          out 객체에 println 메소드로 num 을 출력해 보여주는 로직이며, Scanner
          클래스는 예를들어 hello 라는 단어를 키보드로 입력 시 h , e , l , l , o
          로 h 입력시 바로 즉시 프로그램에 전달, 다음으로 e 입력시 바로 즉시
          프로그램에 전달, l 입 력시 바로 즉시 프로그램에 전달 l o 도 마찬가지로
          키보드로 한번 입력할때마다 전달이되는 형식으로 사용하기 편리하지만
          속도가 느리다는 단점이있습니다.(보통 버벅거린다고하죠??이렇게 얘기하면
          이해하기쉬우실거에요!) 반면 BufferedReader 클래스는 어떻게 진행되는지
          한번 볼까요 ? package curious; import java.io.BufferedReader; import
          java.io.IOException; import java.io.InputStreamReader; public class
          study { public static void main(String[] args) throws IOException {
          BufferedReader br = new BufferedReader(new
          InputStreamReader(System.in)); // 선언 String s = br.readLine(); int i
          = Integer.parseInt(br.readLine()); System.out.println("String : " +
          s); System.out.println("Int : " + i); } } BufferedReader 는 라인단위로
          입력받기에 공백또한 String 으로 인식하며 입력받은 데이터 타입이 String
          타입이기때문에 다른 타입의 데이터라면 이후 형변환이 필요합니다.
          Scanner 는 공백과 줄바꿈 모두 입력값의 경계로 인식하기때문에 쉽게
          데이터를 입력받을 수 있도록해주며, 데이터 타입이 입력받는 시점에서
          결정되므로 별도의 Casting 이 필요하지 않습니다.
        </div>
        <div id="sidebar">
          <h3>Sidebar</h3>
          <ul>
            <li>Fluid Grides</li>
            <li>Media Queries</li>
          </ul>
        </div>
        <div id="footer">
          <h3>Footer</h3>
        </div>
      </div>
      <hr />
      <h3>CSS Code</h3>
      <pre>
      body {
        background-color: rgb(214, 230, 240);
      }
      h4 {
        color: red;
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
    </pre
      >
    </div>
  </body>
</html>