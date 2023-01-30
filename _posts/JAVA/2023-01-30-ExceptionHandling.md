---
layout: post
title: "[Java/자바] 오류의 종류와 예외 처리"
categories: [JAVA]
tag: [Java, Error, Exception, ExceptionHandling]
date: 2023-01-30 00:00:00 +0300
---

# 오류
## - 에러 Error : 수습 불가능한 심각한 오류.
StackOverflow, OutofMemory 등 예측하여 방지 불가능.
## - 예외 Exception : 예외 처리를 통해 수습 가능한 오류.
프로그래머 부주의 / 프로그램 사용 상 실수로 발생.
<br><br>

---

<br><br>

## 1. 오류의 종류
### 1) 구문 오류, 문법 오류 (Syntax Error, Compile Error)
 : 문법을 잘못 작성해 나타나는 오류로 컴파일러가 오류난 코드를 알려줘 쉽게 수정할 수 있다.<br> 컴파일 되는 시간에 일어나는 오류이다. <br><br>
`Compile: 각 언어로 작성된 코드를 기계어로 변환하는 작업.`<br>`컴파일러가 소스코드 .java를 검사하면 클래스 파일 .class이 생성되고 실행을 도와준다.`<br>`이를 시행하는 것이 JVM의 역할이다.`
<br><br>

### 2) 실행 오류 (Runtime Error)
 : 컴파일을 마치고 프로그램이 실제로 수행되는 Runtime에 일어나는 오류.<br>프로그램 실행 도중에 오류를 발견한 것이다.<br><br>
 Ⅰ. 예외 Exception: 프로그래머 부주의 / 프로그램 사용 상 실수로 발생. → 예외처리를 통해 해결.<br>
 Ⅱ. 논리 오류 Logical Error: 잘못된 알고리즘이나 프로그램 설계로 의도와 다르게 동작. → 프로그램 재작성 필요.<br>
 Ⅲ. 시스템 오류 System Error: 하드웨어나 운영체제 문제로 나타나는 오류. → 관리하여 미리 예방.<br>
 <br><br><br><br>
 
 ## 2. Throwable
 - 모든 클래스의 조상은 Object이다. 오류와 예외를 처리하는 것은 Throwable 클래스에서 상속받는다.<br>
 Object - Throwable - Exception, Error - ...
 <br><br><br><br>

 ## 3. Exception Handling
 - 프로그램 실행 시 발생할 수 있는 예외에 대비해 코드를 작성하는 것이다.<br>
 - 예외를 처리하지 못할 시 프로그램은 비정상 종료 된다. 정상적인 실행 상태를 유지하고자 할 때 예외처리를 사용한다.<br>
 처리되지 못한 예외는 JVM의 예외처리기 UncaughtExceptionHandler가 받아서 처리한다.<br><br>

 < 예외 처리 방법><br>
① 예외가 발생할 가능성이 잇는 곳을 try<br>
② 예외가 발생한 메세지를 던짐<br>
③ catch로 try가 던진 예외를 받아서 처리함<br>
④ 예외 발생과 상관없이 무조건 실행하고 싶다면 finally<br>
<br><br>
예외가 일치하는 catch블럭이 있어야 catch 안의 문장이 수행된다. 일치하는 catch블럭이 없으면 예외 처리를 할 수 없다. 만약 try 블럭 안에서 예외가 발생한 문장이 있으면, 바로 예외로 넘겨서 다음 문장은 실행되지 않고 catch로 넘어간다. 예외 처리를 어디서 해야 하는지 위치를 잘 잡아야 사용자가 원하는 코드를 작성할 수 있다.<br><br>모든 예외 클래스는 Exception의 자손으로 Exception 타입의 참조변수 선언 시, 어떤 예외가 발생하더라도 해당 catch 블럭에 의해 처리할 수 있다.<br><br>catch블럭은 try 아래에 위치해야 가독성 향상과 유지 보수에 도움이 된다.<br>finally 사용 시, try~catch 가 종료된 후에 실행되는 것으로 catch 다음에 위치해야 한다.<br><br><br>


```java
catch (참조변수) {
    예외처리할 문장; }
```
예외가 일어난 것과 같은 타입의 참조변수가 필요하다. 해당 타입의 예외를 catch가 잡아 괄호 안의 문장을 처리한다.<br><br><br>

< 자주 사용하는 예외의 종류 ><br>
- ArithmeticException: 어떤 수를 0으로 나눌 때 발생
- NullPointException: null 참조 시 발생
- IncompatibleCalsschangeException: 변수 선언이 static ↔ non-static 변경 시, 다른 클래스에서 참조할 때 발생
- ClassCastException: 변환할 수 없는 타임으로 객체를 변환할 때 발생
- OutOfMemoryException: 메모리가 부족한 경우 발생
- ArrayIndexoutOfBoundException: 배열 범위를 벗어나 접근할 때 발생
- IllegalArgumentException: 잘못된 인자 전달 시 발생
- IOException: 입출력 동작 실패 or 인터럽트 시 발생
- NumberFormatException: 숫자 형태 문자가 아닌 문자 입력 시 발생
<br><br><br><br>

## 4. 예외 정보
만약 예외 발생의 원인을 알고 싶다면 아래를 활용하면 된다.<br>
Ⅰ. printStackTrace(): 예외 발생 당시 호출 스택에 있던 메서드 정보와 예외 메세지가 출력 된다. <br>
Ⅱ. getMessage(): 해당 예외 클래스의 인스턴스에 저장된 메세지를 얻을 수 있다. <br>
<br><br>
```java
class ExceptionEx{
    public static void main(String args[]){
        System.out.println(1);
        System.out.println(2);
        try{
            System.out.println(3);
            System.out.println(0/0);
            System.out.println(4);
        } catch (ArithmeticException ae){
            ae.printStackTrace();
            System.out.println("예외메시지: "+ae.getMessage());
        }
        System.out.println(6);
    }
}
```
<br>
ArithmeticException는 0으로 나눌 때 발생하는 예외이다. 0을 0으로 나누면서 예외를 발생시켰다. catch에서 해당 예외 타입을 잡아 printStackTrace()로 예외 발생 시 나오는 정보와 메시지가 출력된다. <br><br>그리고 `예외메시지: / by zero`라는 문장도 함께 출력된다. zero(0) 으로 나누기를 진행해서 예외가 발생되었다고 알려준다. 해당 메서드를 통해 사용자가 예외의 정보를 알 수 있다.<br><br>

```java
1
2
3
예외메시지: / by zero
6
java.lang.ArithmeticException: / by zero
	at day_01.ExceptionEx.main(ExceptionEx.java:9)
```
<br>인텔리제이에서 해당 코드 실행 시 위처럼 나오고 정상 종료된다.<br><br><br><br>

## 5. throw
- 프로그래머가 고의로 예외를 발생시킨다.<br>예외 클래스를 throw로 넘기면 강제로 예외가 발생한다.<br><br>
```java
class ExceptionEx2{
    public static void main(String args[]){
        try{
            throw new Exception("고의 발생");
            // 예외 클래스의 객체를 생성하여 객체를 throw해도 된다.
        } catch (Exception e){
            System.out.println("에러 메세지: "+e.getMessage());
            e.printStackTrace();
        }
        System.out.println("프로그램 정상 종료");
    }
}
```
<br> < 결과 화면 >

```java
에러 메세지: 고의 발생
프로그램 정상 종료
java.lang.Exception: 고의 발생
	at day_01.ExceptionEx2.main(ExceptionEx.java:6)
```
<br> Exception을 인스턴스 한 뒤 throw로 넘겨주고, catch에서 Exception을 잡아 예외처리를 진행했다.<br><br><br>
메서드에서도 예외처리를 할 수 있다.
```java
void method() throw Exception{

}
```
해당 메서드에서 해당 예외가 발생할 수 있다는 것을 알려준다. `예외 처리가 이루어진 것이 아니고, 발생할 가능성이 있는 것을 알려주는 용도`임을 기억해야 한다.<br><br> [스트림 포스팅](https://euuns.github.io/2023-01/Stream)에서 입출력 관련 예외가 발생할 가능성이 있어 throw IOException을 추가해준 것이 이 예이다.