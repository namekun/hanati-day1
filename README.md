# 20180816 hanati-class-day1

## JAVA?

- 95년 5월에 JAVA라는 이름으로 공식발표, JDK 지원, 지원클래스는 250개로 시작
- 자바는 인터넷의 발달로 인해 인기가 많아짐(웹에 바로 적용가능한 언어)

---
## 특징

* **객체지향 프로그래밍 언어(Object Oriented Programming)**

* **문법이 매우 Simple**

  * C++기반의 언어지만, C++보단 간단하다.

* **플랫폼(OS)에 독립적이다.**

  * 자바는 운영체제에 상관없이 JRE가 설치되어 있으면 어디에서든지 가능하다.(이식성이 뛰어남)

  * JAVA Platform = 모든 자바어플리케이션이 동작할 수 있는 환경(Java SE, EE, ME)

* **메모리 자동관리(Garbage Collection)**

* **보안성**

* **쉬운 예외처리, 멀티스레드, 네트워킹, 분산시스템 구축 등...**

---

## 구조

Hardware Platform(os) - Java SE, EE, ME platform(JRE) & Java APIs - Java Program

---

## JAVA로 작성할 수 있는 프로그램 종류

* Desktop Application
* Applet
* Servlet/JSP
* Java Beans
* Enterprise Java Beans (EJB)
  * 분산 컴포넌트 기술 (Spring이 대체하기 위해 나옴)
* Mobile Application

---

## 개발하는 과정이 어떻게 이루어지는가?

OS(1층) / Java SE Platform(2층) / Application(3층) 

* 상호작용하기 위해 필요한 라이브러리 = 표준API( 클래스 라이브러리 )

*.java -> 컴파일(javac.exe) -> * .class로 변환( byte code ) 로 변환

* JDK 설치하면 개발환경과 실행환경이 모두 설치된다.

---

## 설치

1. JDK 1.8 버전 설치

2. path 설정 후 잘 설치가 되어있는지 확인

   ```
   C:\Users\KOSTA>set path
   Path=C:\Program Files (x86)\Common Files\Oracle\Java\javapath;C:\Program Files (x86)\Intel\iCLS Client\;C:\Program Files\Intel\iCLS Client\;C:\windows\system32;C:\windows;C:\windows\System32\Wbem;C:\windows\System32\WindowsPowerShell\v1.0\;C:\Program Files (x86)\Intel\Intel(R) Management Engine Components\DAL;C:\Program Files\Intel\Intel(R) Management Engine Components\DAL;C:\Program Files (x86)\Intel\Intel(R) Management Engine Components\IPT;C:\Program Files\Intel\Intel(R) Management Engine Components\IPT;C:\Program Files (x86)\NVIDIA Corporation\PhysX\Common;C:\Program Files\Samsung\SamsungLink\AllShare Framework DMS\bin\;C:\Program Files\Java\jdk1.8.0_181; \bin;C:\Program Files\Bandizip\
   PATHEXT=.COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC
   
   C:\Users\KOSTA>set classpath
   CLASSPATH=.
   
   C:\Users\KOSTA>set java_home
   JAVA_HOME=C:\Program Files\Java\jdk1.8.0_181;
   
   C:\Users\KOSTA>java -version
   java version "1.8.0_181"
   Java(TM) SE Runtime Environment (build 1.8.0_181-b13)
   Java HotSpot(TM) 64-Bit Server VM (build 25.181-b13, mixed mode)
   ```

3. 잘 설치되었음을 확인한다.

![헬로월드](http://www.zentut.com/wp-content/uploads/2013/01/javahelloworldcode.png)

* public class ~~ {} = 클래스
* public static void main(String[] args){} = 메인메서드(실행진입점)

---

## 실습

*C:\kosta187\workspace\Fundamental*

```java
class HelloWorld{ // 클래스
	public static void main(String[] args){ //메인 메서드 (실행 진입점)
		System.out.println("안녕 오랜만이야");
		System.out.println(50);
		System.out.println('김');
	}
}
```

* 저장 될 이름과 class의 이름은 똑같아야한다.

*컴파일 해보자*

```
C:\Windows\system32>cd C:\kosta187\workspace\Fundamental

C:\kosta187\workspace\Fundamental>dir
 C 드라이브의 볼륨에는 이름이 없습니다.
 볼륨 일련 번호: F453-BF50

 C:\kosta187\workspace\Fundamental 디렉터리

2018-08-16  오후 02:54    <DIR>          .
2018-08-16  오후 02:54    <DIR>          ..
2018-08-16  오후 02:53               172 HelloWorld.java
               1개 파일                 172 바이트
               2개 디렉터리  941,298,438,144 바이트 남음
```

* 만약 인코딩이 UTF-8이면 다음과 같은 인코딩오류가 나온다.

```java
C:\kosta187\workspace\Fundamental>javac HelloWorld.java
HelloWorld.java:3: error: unmappable character for encoding MS949
                System.out.println("?븞?뀞 ?삤?옖留뚯씠?빞");
                                    ^
HelloWorld.java:3: error: unmappable character for encoding MS949
                System.out.println("?븞?뀞 ?삤?옖留뚯씠?빞");
                                      ^
HelloWorld.java:3: error: unmappable character for encoding MS949
                System.out.println("?븞?뀞 ?삤?옖留뚯씠?빞");
                                         ^
HelloWorld.java:3: error: unmappable character for encoding MS949
                System.out.println("?븞?뀞 ?삤?옖留뚯씠?빞");
                                           ^
HelloWorld.java:3: error: unmappable character for encoding MS949
                System.out.println("?븞?뀞 ?삤?옖留뚯씠?빞");
                                                ^
HelloWorld.java:5: error: unmappable character for encoding MS949
                System.out.println('源?');
                                     ^
HelloWorld.java:5: error: unclosed character literal
                System.out.println('源?');
                                   ^
HelloWorld.java:5: error: unclosed character literal
                System.out.println('源?');
                                      ^
8 errors
```

* 그러니까 인코딩을 ANSI로 바꿔주자

```
C:\kosta187\workspace\Fundamental>javac HelloWorld.java //컴파일해준다.

C:\kosta187\workspace\Fundamental>java HelloWorld
안녕 오랜만이야
50
김
```

---

##  클래스?

* 애플리케이션을 구성하는 기본단위.
* 클래스의 첫 문자는 대문자로 시작한다.
* 클래스의 구성요소(속성, 메소드 등...) 들은 블록 ({}) 안에 위치한다.
* 소스파일 저장 시 파일명이 클래스명과 반드시 일치해야한다.

---

## main(String[] args) 메서드 정의

* Desktop Application이 실행되려면 최소 1개 존재하여야한다.
* 프로그램의 실행 진입점으로 JVM에 의해 최초 실행되며
* 메인 메서드 블록({}) 내부에 기술된 실행구문(명령문)들을 순차적으로 실행한다.
* 하나의 실행 구문은 세미콜론(;)으로 마무리한다.

---

## 자바 응용프로그램 동작원리(중요!)

![자바실행과정](https://t1.daumcdn.net/cfile/tistory/25616D45576B854C3F)

* 소스코드를 컴파일러를 통해 바이트 코드로 바꿔준다. 
* 클래스 로더로 바이트 코드를 가져와서, 바이트 코드에서 검증, 그리고 인터프리터로 해석해서 실행결과를 보여준다.

---

## 자바 기본 구문

### 주석  - 말 그대로 주석

* Singleline Comment
  * // 뒤에 한 라인에 대하여 주석 처리
* Multiline Comment
  * /* … */ 범위의 모든 라인에 대하여 주석 처리
* Document Comment
  * /** … */ 범위의 모든 라인에 대하여 주석 처리
* 클래스나 메소드 앞에 사용되어지며, javadoc.exe(도큐먼트 생성툴)를 이용하여 HTML Document 생성시 주석내용이 문서에 포함된다
* 주석 내용에 HTML 태그 사용 가능

*C:\kosta187\workspace\Fundamental*

```java
/** 
  * 이 주석은 document에 들어간다라고 알려주는 것입니다.<br>
  * <p>클래스 설명</p>
  * 작성자 : 김남혁<br>
  * 작성일자 : 2018-08-16<br>
*/

public class CommentExample { // public = 누구나 사용할 수 있다.
	public static void main(String[] args){
		
		//System.out.println('주석테스트입니다');
		
		/*
		System.out.println('주석테스트입니다');
		System.out.println('주석테스트입니다');
		System.out.println('주석테스트입니다');
		*/
		
		System.out.println("주석테스트입니다");
		
	}
}
```

* javadoc.exe를 통해서 html 문서를 더 만들 수 있다.

```
C:\kosta187\workspace\Fundamental>javadoc CommentExample.java
Loading source file CommentExample.java...
Constructing Javadoc information...
Standard Doclet version 1.8.0_181
Building tree for all the packages and classes...
Generating .\CommentExample.html...
Generating .\package-frame.html...
Generating .\package-summary.html...
Generating .\package-tree.html...
Generating .\constant-values.html...
Building index for all the packages and classes...
Generating .\overview-tree.html...
Generating .\index-all.html...
Generating .\deprecated-list.html...
Building index for all classes...
Generating .\allclasses-frame.html...
Generating .\allclasses-noframe.html...
Generating .\index.html...
Generating .\help-doc.html...
```



---

### 예약어

* JVM에 사전에 등록되어 의미가 약속되어져있는 명령어(단어) 들을 의미한다.
* ex > abstract, const, finally, int, public, throw, boolean, continue, float, interface, return, throwsm, break, default, for, long, short, transient.....

---

### 식별자

* 프로그램을 구성하는 변수, 상수, 배열, 메서드, 클래스 등을 구분하기 위해 사용자가 정의하는 이름을 의미한다.
* 대소문자를 구분하고, 첫 글자는 영문자나 특수문자로 시작되어야한다.
* 첫 글자를 숫자로 사용 불가. 
* 예약어는 식별자로 사용 불가
* 16비트 유니코드를 지원하므로 한글도 식별자로 사용 가능은 하다. 그러나 권장하진 않는다.
  * JAVA는 아스키 코드를 쓰는게 아니라 유니코드를 지원하는 것이다.
    * 아스키코드 : ANSI(American National Standards Institute: 미국규격협회)에서 제정한 8비트 문자코드로  256개의 문자를 코드화 
    * 유니코드 : 유니코드(Apple, IBM, MS등의 컨소시엄)에서 제정한 16비트로 확장한  문자코드로 전세계의 모든 문자를 표현하기 위한 표준 문자 코드이다. 
* 식별자 관례 
  * 클래스 이름은 대문자로 시작하고, 변수, 메소드 등의 이름은 소문자로 시작하는 것이 관례
  * 두 단어를 조합하여 이름을 정할때는 조합하는 문자의 첫글자는 대문자로 한다.
  * Camel 표기법을 권장
    * Camel표기법 : 각 단어의 첫문자를 대문자로 표기하고 붙여쓰되, 맨처음 문자는 소문자로 표기 , 띄어쓰기 대신에 대문자로 단어를 구분하는 표기 방식  ( _도 되도록 사용하지 않습니다.)
* 올바른 식별자의 예시
  * id
  * userName, user_name
  * _userName
  * $userName
* 틀린 식별자의 예
  * user name // 빈 공백이 오면 안된다.
  * 3d_studio // 숫자로 시작할 수 없다.
  * this // 키워드는 사용할 수없다.
  * #arg // #을 사용할 수 없다.

---

### 변수 

* 데이터를 넣고 필요할 때 마다 계속 사용하기위해서 쓰는 것, 즉 데이터 재사용을 위해 쓰는 것이다.
  * 기능의 재사용을 위해 만든건 JAVA에서는 메소드, C에선 Function
  * 설계의 재사용 = 개발방법론
* 코드적으로 말하자면, 상수는 변하지 않는 **변수**를 뜻한다.
* 데이터타입 변수이름 ; -> 변수 선언
* 변수이름 = 값; -> 변수에 값을 할당, 변수 초기화라고 한다.

```java
int age; // 변수 선언
age = 50; // 변수 값 할당, 변수 초기화
age = 500; // 변수에 할당된 값을 바꾼다, 변수 수정
```

* 프로그램 언어는 자체적인 데이터타입을 제공하는데, 변수의 메모리 크기는 선언되는 데이터타입에 따라 결정된다. 
* ex) int a;   long b, c;   String name; 8
* 초기화가 안된 변수를 불러오면 오류납니다.

```java
class VariableExample{
	public static void main(String[] args) {
		
		// 숫자를 3개 저장할 수 있는 변수를 만든다.
		//int a, b, c; // C와 달리 아무것도 담기지 않습니다.
		/*
		a = 10;
		b = 20;
		c = 30;
		*/
		// a = 10, b = 20, c = 30;
	
		int a = 10, b = 20, c = 30;
		System.out.println(a);
		System.out.println(b);
		System.out.println(c);

		String name = "kalid";
		String 메세지 = "이것은 한글로 된 변수입니다.";
		
		System.out.println(name);
		System.out.println(메세지);
        
        //int x;
       	//System.out.println(x);  <- 에러!
		}
}
```



---

### 리터럴

* 리터럴은 데이터 그 자체를 뜻 한다. 변수에 넣는 변하지 않는 **데이터**를 의미하는 것 (상수)
* 변수에 리터럴(상수) 할당

```java
int a = 3;
//[데이터타입] [변수] = [리터럴]; 
```
---

### 데이터타입 

* 데이터를 구별하기 위해서 쓰는 것.

![datatype](https://t1.daumcdn.net/cfile/tistory/1860543F4DEE241C0A)

* 기본 자료형(primitive DataType) 

  * char, byte, short, int, long, float, double, boolean
  * 기본 자료형으로 선언된 변수에는 실제 값이 저장된다.
  * Pass by Value
    * 값에 의한 전달이다. 즉 매개 변수로 넘어갈 때 값이 넘어가는 형태.

  |  구분  |                           자료형                            |             크기(처리범위)              |
  | :----: | :---------------------------------------------------------: | :-------------------------------------: |
  | 논리형 |                           boolean                           |          1bit (true or false)           |
  | 문자형 |                            char                             |          16bit (\u0000-\uFFFF)          |
  | 정수형 |                            byte                             |      8bit (-2의 7승 ~ 2의   7승-1)      |
  | short  |              16 bit (-2의 15승 ~ 2의 15승 –1)               |                                         |
  |  Int   |              32 bit (-2의 31승 ~ 2의 31승 –1)               |                                         |
  |  long  |              64 bit (-2의 63승 ~ 2의 63승 –1)               |                                         |
  | 실수형 |                            float                            | 32bit (-3.40292347E38 ~ +3. 40292347E38 |
  | double | 64 bit (-1.79769313486231570308 ~ +1. 79769313486231570308) |                                         |

  1. 논리형(boolean)

     * True or False 값만 가질 수 있다.

     ```java
     /**
      * 자바 데이터 유형 테스트  
     */
     
     class DataTypeExample{
     	public static void main(String[] args){
     		boolean flag = true; //false
     		
              System.out.println(flag);
     		
              //boolean flag2 = 10; // error
     		
     	}
     }
     ```

     

  2. 문자형(char)

     * 비 영어권 문자를 처리할 수 있도록 유니코드를 지원
     * 문자 상수는 작은 따옴표(' ')안에 넣어야 한다.
     * char 형에는 모니터, 프린터 같은 주변기기를 제어하는데 사용하는 제어 문자와 인용부호(“”) 안에서 표현될 수 없는 특수한 문자(“, ‘, \)를 표현하는데 사용되는 이스케이프(Escape) 문자가 있다 

* 참조 자료형 (Reference DataType)

  * 클래스, 인터페이스, 배열
  * 참조 자료형으로 선언된 변수에는 인스턴스에 대한 주소값이 저장된다.
  * Pass by Reference
    * 참조 자료형 안에 있는 변수들은 매개 변수로 넘어갈 때 참조 주소가 넘어간다.

---

### 클래스 

* 모듈의 재사용을 위해 만든 것이다.

