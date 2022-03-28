---
layout: post
title: "BufferedReader와 Scanner 차이점!"
---

### 문득 궁금해진 BufferedReader 클래스와 Scanner 클래스 차이점!  

우리가 공부를 하다보면 문득 같은 기능을 가졌지만 어떤 차이점이있을까?  
라는 궁금증을 가져볼 수 있습니다.  
그럴때 우리는 그 궁금증을 그냥 지나가지말고 한번 쯤 검색을 해서 궁금증을  
해소하는 습관을 갖춘다면 조금씩 한발자국 발전해 나갈 수 있다고 생각합니다.  

먼저 많이 사용해보셨을 Scanner scan = new Scanner (System.in);

```java
package curious;

import java.util.Scanner;

public class study {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);

		System.out.println("원하는 숫자를 입력하세요");
		String input = scanner.nextLine();
		int num = Integer.parseInt(input);

		System.out.println(num);
	}
}
```

<br>
자바 수업을 듣거나 공부하다보면 BufferedReader 보다는 Scanner를 먼저
<br>   
배우게되는 경우가 많으실거고 저또한 그랬었습니다.
<br>  
위와같이 input 에 scanner.nextLine 으로 입력받은 값을 담아  
<br>
parseInt로 String 으로 입력받은 문자열 값을 정수로 변환시켜 num에 저장하고  
<br>
System 클래스에 out 객체에 println 메소드로 num 을 출력해 보여주는 로직이며,  
<br>
Scanner 클래스는 예를들어 hello 라는 단어를 키보드로 입력 시  
<br>
h , e , l , l , o 로 h 입력시 바로 즉시 프로그램에 전달, 다음으로  
<br>
e 입력시 바로 즉시 프로그램에 전달, l 입
력시 바로 즉시 프로그램에 전달  
<br>
l o 도 마찬가지로 키보드로 한번 입력할때마다 전달이되는 형식으로 사용하기 편리하지만  
<br>
속도가 느리다는 단점이있습니다.(보통 버벅거린다고하죠??이렇게 얘기하면 이해하기쉬우실거에요!)<br>  
<br>
반면 BufferedReader 클래스는 어떻게 진행되는지 한번 볼까요 ?  

```java
package curious;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class study {
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in)); // 선언
		String s = br.readLine(); 
		int i = Integer.parseInt(br.readLine()); 
		
		System.out.println("String : " + s);
		System.out.println("Int : " + i);
		
	}
}
```

<br> 
BufferedReader 는 라인단위로 입력받기에 공백또한 String 으로 인식하며 입력받은 데이터 타입이
<br>
String 타입이기때문에 다른 타입의 데이터라면 이후 형변환이 필요합니다.
<br>
Scanner 는 공백과 줄바꿈 모두 입력값의 경계로 인식하기때문에 쉽게 데이터를 입력받을 수 있도록해주며,
<br>
데이터 타입이 입력받는 시점에서 결정되므로 별도의 Casting 이 필요하지 않습니다. 
<br>
<table>
  <div>
    <tr align="center">
      <td>&nbsp;</td><td>BufferedReader</td><td>Scanner</td>
    </tr>
    <tr align="center">
      <td>Buffer Size</td><td>8192</td><td>1024</td>
    </tr>
    <tr align="center">
      <td>동기화됨</td><td>O</td><td>X</td>
    </tr>
    <tr align="center">
      <td>문자열 파싱</td><td>단순히 읽어들임</td><td>문자열 파싱가능</td>
    </tr>
    <tr align="center">
      <td>Exception</td><td>IOException 던짐</td><td>IOException 숨김</td>
    </tr>
  </div>
</table>
