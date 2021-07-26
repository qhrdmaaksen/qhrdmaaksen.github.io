---
layout: single
title: "The TCP socket Use The Server and Client Communication!"
---
####출처 : 한양사이버대학교 민병석 교수님 자료
### 1)자바와 네트워킹
### 2)URL 클래스와 URLConnection 클래스
### 3)TCP 소켓을 이용한 서버/클라이언트 통신
### 4)UDP 소켓을 이용한 서버/클라이언트 통신

###1-1) TCP 통신 방식
<li>자바는 서버/클라이언트 응용 프로그램을 위한 ServerSocket 클래스와 Socket 클래스를 제공</li>
<dl>
TCP 소켓의 특징
<li>연결성 통신 방법이므로, 전송 전에 연결이 성립되어야 한다.</li>
</dl>

<p>TCP 소켓의 동작</p>
<ol>
  <li>클라이언트는 소켓을 생성하여 서버에 연결 요청을 하며, 서버는 accept()메소드로 연결 요청을 수락</li>
  <li>클라이언트 연결 요청에 서버가 응답(수락)하지 못한다면 접속 거부 에러 발생</li>
  <li>서버가 먼저 실행되어 클라이언트의 접속 요청을 대기</li>
  <li>클라이언트의 접속 요청이 발생하면 서버는 요청을 처리, 데이터를 클라이언트에 전송</li>
</ol>

![TCPsocketMovement.png](../img/TCPsocketMovement.png)
####1-2) ServerSocket class 주요 메소드
```java
ServerSocket(int port)//생성자,port == 포트번호
throws IOException
-----------------------------------------------
Socket accept()//클라이언트의 요청을 받아들인다음 Socket 클래스 객체 반환
throws IOExcetption 
---------------------------------------------------------------------
void close()//서버 소켓을 닫는다.
throws IOException 
```
![socket_important_method.png](../img/socket_important_method.png)
####3-1) TCP Socket 을 이용한 서버/클라이언트 간 통신 순서
<p>서버</p>
<ol>
  <li>ServerSocket class 로 부터 서버 소켓 오브젝트를 생성 후 클라이언트의 접속 요청을 기다림</li>
  <li>클라이언트 접속 요청이 발생하면 요청을 수락하여 Socket object 생성</li>
  <li>Socket 오브젝트를 이용하여 입출력을 위한 스트림을 생성</li>
  <li>통신을 진행</li>
  <li>소켓 닫음</li>
</ol>
<p>클라이언트</p>
<ol>
  <li>연결하고자하는 서버의 주소와 포트번호로 Socket 을 생성</li>
  <li>Socket 오브젝트를 이용해 입출력을 위한 스트림 생성</li>
  <li>통신을 진행</li>
  <li>소켓 닫음</li>
</ol>
<p>예제 프로그램 순서</p>
<ol>
  <li>서버에서 클라이언트로 데이터 전송</li>
  <li>클라이언트에서는 수신한 데이터를 출력</li>
  <li>명령창에서 서버 프로그램 실행</li>
  <li>다른 명령창에서 클라이언트 프로그램 실행</li>
  <li>서버는 무한 루프 수행중이므로 종료하려면 컨트롤 + c 입력</li>
</ol>