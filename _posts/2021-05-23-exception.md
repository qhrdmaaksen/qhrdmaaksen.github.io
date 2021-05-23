---
layout: post
title: "예외와 예외 처리의 개념!"
---

### 예외 : 프로그램을 실행했을 때 발생하는 에러  
  
정의 : 수치를 0 으로 나누거나, 배열의 범위 밖을 이요하려 할 때 예외가 발생
  
1/ 에러, 예외에 대응하는것을 **예외 처리**라고 함
  
2/ 자바는 예외가 발생하면 자동적으로 전용클래스(예외 클래스)의 오브젝트가 생성됨
  
예외 클래스에는 exception 클래스와 그 서브 클래스가 있다.
  
**예외 처리**  
예외가 발생할 것 같은 처리를 수행할 경우에 try 문 , catch 문, finally문 사용
```java
try {
    //예외가 일어날 것 같은 처리를 기술함
  }
  catch(//예외 클래스명 변수명 ex: Exception e) {
    //예외 발생 시 수행할 처리
  }
  //예외가 생기든 안생기든 실행됨 finally 문은 생략 할 수 있다.
  finally {
    //처리
  }
```  
예외 발생 예상 메소드는 **throw**를 사용, 메소드에서 생길수 있는 예외 클래스를 지정해 둠  
but 메소드를 호출한 곳에 예외를 받아 줄 catch 문이 없으면 , 컴파일 에러 발생
```java
class Args {
    public static void main(String[] args){
      try {
        //같은 클래스내의 static 멤버이므로 오브젝트 생성없이 back() 직접 호출가능
        back(args[0]); //인수가 없으면 예외 발생
      } catch (Exception e) {
        System.out.println("커맨드라인 인수가 없음");
      } finally {
        System.out.println("종료");
      }
    }
      static void back(String a) throws Exception {
        System.out.println("커맨드라인 인수는 " +  a + "입니다.");
      }        
}
```
3/**사용자 정의 예외 만들기**  
1)기존 정의된 예외 클래스외에 필요에 따라 새로운 예외 클래스를 정의하여 사용할 수 있음  
2)보통 exception 클래스로부터 상속받는 클래스를 만들지만,예외 클래스를 선택할수있음
```java
class MyException1 extends Exception{
  //noting
}
class MyException2 extends Exception{
  //noting
}
class MyException {
  public static void main(String[] args) {
    try {
      //같은 클래스내의 static 멤버이므로 오브젝트 생성없이 MyMethod메소드 직접 호출가능
      MyMethod(args[0]); //인수가 없으면 예외 발생
    } catch (MyException1 e1) {
      System.out.println("예외 1");
    } catch (MyException2 e2){
      System.out.println("예외 2");
    } finally{
      System.out.println("종료");
    }
  }
  static void MyMethod(String str) throws MyException1,MyException2 {
    System.out.println("입력값은 " + str + "입니다.");
    int x = Integer.parseInt(str); // 문자열을 정수로 변환
    switch ( x ){
      case 1:
        throw new MyException1();//예외 발생 시킴
      case 2:
        throw new MyException2();//예외 발생 시킴
      default:
        System.out.println("예외 없음");
    }
  }
}
```


