# JAVA 기본 요약 
## JDK (Java Development Kit)
- 자바에 필요한 클래스(class), 컴파일(compile), 실행(execution), 배포(deployment) 등 개발에 필요한 환경도구를 JDK라 칭함
 1) JDK : 개발도구
 2) JRE : 실행환경
 3) JVM : 가상머신(실제 실행영역)

## 자바 표기법
 1) 파스칼 표기법 : 첫 단어에 대문자, 클래스명이나 인터페이스 명에 사용됨 (예) class Car() , class Support() 등 
 2) 카멜 표기법 : 단어 사이에 대문자, 메소드 이름이나 변수명에 사용됨 (예) void speedUp()

(ex) 이 밖에도 많은 표기법이 있으나 대표적으로 위 두 가지가 있다.

## 자바의 기본적인 객체 모델
 1) 클래스 (예) 자동차
 2) 변수 (예) 자동차 색깔, 부품 이름
 3) 매소드 (예) 가속, 감속, 브레이크 등 동적 행위

## 기타 설명
1. main : JVM이 객체를 호출할 때에 진입점 역할을 수행함
2. JVM 영역
   
    (1) Method 영역
    
    (2) Heap 영역
    
    (3) Stack 영역
    -    여기서, Static 선언을 하게 되면 Heap 영역이 아닌 Methon, Stack 영역으로 메소드가 형성이 되면서 정상 실행이 된다. 만약 main 에 static 이 선언되어 있지 않다면 JVM 과 메모리 상의 구조적인 문제가 발생될 가능성이 크다.

3. Package / Import
       
    (1) Package
        
    - 모든 클래스는 패키지라는 고유 주소를 가지고 있음 , 일반적으로 클래스의 고유 주소를 나타내기 위해서 "패키지명+클래스명" 형태로 표기함
        
    (2) Import
    - 클래스 내부에서 다른 클래스의 위치를 표현하기 위해 사용함. 다만, java.lang. 내부에 속해져 있는 클래스의 경우엔 import 가 생략될 수 있다.

# 객체지향
## 기본 속성
1) 상속성
- 상위 클래스(부모 클래스)의 특징을 하위 클래스(자식 클래스)가 모두 물려받는 것을 말함
- 이때, 자식 클래스는 부모가 가지고 있는 멤버 변수와 메소드를 모두 물려받아 사용이 가능함
- 쉬운 용어로 상속관계 혹은 계층구조로 불림

2) 캡슐화
- 세부 구조는 숨기고 접근할 필요가 있는 부분만 노출하는 것, 대표적인 예로 라이브러리가 있다.
- 프로그램의 복잡도를 줄이는 데에 큰 역할을 함
- private 에서 public 으로 갈수록 접근 가능 범위가 커짐 (private > default > protected > public)
- private : 외부 객체 접근 불가, default : 같은 패키지의 객체만 접근 가능, protected : 상속 관계의 객체만 접근 가능, public : 모든 객체에서 접근 가능

3) 추상화
- 객체의 공통적인 특징을 추출하는 과정으로 다음과 같다.
    
    (1) 객체들의 공통적으로 가지고 있는 개념을 추출함

    (2) 공통 개념이 추출되면, 추출한 개념을 이용한 최소한의 기능을 가진 상위 개념 객체를 생성함

    (3) 상위 개념의 객체를 상속받아 구현을 함


4) 다양성
- 객체 간의 결합도를 줄이기 위해 OOP(객체 지향 프로그래밍, Object-Oriented Programming)에 도입된 개념
```java
public class MainRun{

    public void inCome(Animal a){
        a.sound();
    }

    public static void main(String args[]){

        MainRun run = new MainRun();

        Animal cat = new Cat(); // 부모클래스 타입으로 레퍼런스 생성
        Animal dog = new Dog(); // 부모클래스 타입으로 레퍼런스 생성

        run.inCome(cat);
        run.inCome(dog)
    }
}
```
- 하위 클래스인 Doc, Cat 은 각각 상위 클래스인 Animal 클래스를 상속 받아 구현됨
- 실행 시 cat 변수는 상위 클래스 타입인 Animal 타입의 레퍼런스로 Cat 타입의 객체를 연결함, Dog 도 마찬가지다.
- 실제 데이터를 처리하는 inCome() 메소드를 살펴보면 인자 값으로 Animal 타입의 객체를 받아서 처리함
- 위 코드가 정상 작동하는 이유는 상위 클래스인 Animal 타입의 변수로 선언하였기 때문이다.
- 이와 같이 설명하는 이유는 객체 간의 결합도를 줄이기 위하여 사용되는 다양성을 설명하기 위함이다.


# JVM 메모리 구조

## JVM 영역

![](2023-01-05-18-57-00.png)

### 1.메소드(Method) 영역
- 런타임 시 생성된 모든 스레드가 공유하는 영역
- 기본적으로 할당받는 메소드 영역의 메모리 사이즈는 일정하게 정해져 있다.
- 기본 구성은 아래와 같다.
1) 클래스로더에서 읽어들인 바이트 코드를 저장해 두고 바이트 코드를 이용해 모든 클래스를 분석함
2) 클래스 분석이 완료되면 클래스 정보, 메소드 정보 등을 생성하고 생성된 정보를 이용하여 Static 변수를 생성함

### 2.스택(Stack) 영역
- JVM 스택, 호출 스택 등의 다양한 이름으로 불림
- JVM 스택은 프로세스 내부에 생성된 스레드 마다 생성되며 메소드 동작을 위한 메모리 공간을 제공함
- 해당 스택(Stack) 영역에 메소드 정보, 지역 변수 정보 파라미터 값 등이 저장됨
- 호출된 메소드가 실행되면 스택 프레임이라는 자료 구조가 생성되고, 실행 순서에 따라 스택 동작을 수행하다가 모든 동작이 완료되면 메모리에서 사라진다.

### 3.힙(Heap) 영역
- 새로운 키워드로 객체를 생성하면 생성된 객체는 힙(Heap) 영역에 저장됨
- 런타임 시 생성되는 객체를 저장하는 공간
- 메모리상의 쓰레기를 제거하는 작업, 불필요한 메모리 공간을 정리하는 역할을 수행함


# Java 플랫폼

## Java SE 
- 가장 기본적인 환경(사용자 PC)에서 동작하는 프로그램을 개발하기 위한 자바 플랫폼
- 기본적인 API와 컴파일러, 실행 환경 등을 포함함
- Java SE에 포함된 API는 가장 기본적인 것으로 모든 API의 근간이 되는  Base API이다.
- Java SE 는 JDK 와 JRE 로 구성되어 있다.

## Java EE
- 대량의 리소스를 사용하는 기업용 프로그램을 제작하는데 적합한 API로 구성되어 있다.
- 자바 기반의 웹 프로그램을 작성하기 위한 Servlet이나 JSP, 대량의 트랜잭션 처리를 위한 EJB 같은 API가 제공됨
- JDK와 같은 API를 제공하지 않기 때문에 Java EE API를 사용하려면 Java EE 명세를 실제 구현한 구현체를 함께 사용해야 된다.
- WAS 제품들이 Java EE 명세를 모두 구현하고 있기 때문에 Java EE 가 제공하는 API는 WAS 환경에서만 실행이 가능하다.

## Java ME
- 모바일 환경에서 자바 기반의 프로그램을 제작하는 데 적합한 API로 구성되어 있음
- 오라클에서 모바일용 SDK를 별도로 지원하고 있음

# Java Development Kit (JDK)

## 기본 툴 종류
- java : 실제 자바 프로그램을 실행시키는 도구
- javac : 자바 소스 코드를 컴파일하는 도구
- javadoc : API 문서를 생성해주는 APJ 문서 생성 도구
- jdb : 자바 소스 디버깅 도구
- jar : 자바 Archive(JAR) 파일 생성 도구
- appletviewer : 애플릿을 간단하게 실행해주는 도구

## Java API
   - 프로그램을 위한 기본적인 API들로 구성되어 있음 ,API 라는 것은 라이브러리로 생각하면 됨
   - 대표적인 API는 다음과 같다.

1. java.lang 패키지
    - 프로그래밍하는데 필요한 기본 클래스를 제공함
    - import 키워드를 이용하지 않더라도 자동으로 컴파일됨
    - Object 클래스도 해당 패키지 내에 존재함
<br/>
<br/>

    #### 1) Class 클래스 (java.lang.Class)

    - 객체의 클래스 타입에 관한 정보
    - new 키워드를 사용하지 않고 Object 클래스의 getClass() 메소드를 이용하여 얻을 수 있음
    - Object 클래스는 모든 클래스의 최상위 클래스이므로 모든 객체는 getClass()를 가지고 있음
    - 예시)

        static Class forName(String className) <br> - static 메소드 내에 넘어온 클래스명의 객체에 대한 Class를 리턴함

        String getName() <br> - 객체의 클래스명을 리턴함

        Object newInstance <br> - 객체의 클래스 인스턴스를 생성하여 리턴함


    #### 2) String 클래스 (java.lang.String)
    - 문자열 처리를 위해 자바에서 제공하는 가장 기본적인 클래스
    - 한 번 생성된 문자열의 내용을 변경할 수 없음
    - 이 때문에 Primitive 데이터 타입처럼 사용이 가능함

        int length <br> - 문자열의 길이를 리턴함

        char charAt(int index) <br> - index로 지정된 위치의 문자열을 리턴함

        boolean equals(Object  anObject) <br> - 같은 값을 가진 문자열은 true가 리턴되도록 오버라이딩됨

        String substring(int beginIndex) <br> - beginIndex 에 해당되는 문자열까지 잘러서 리턴함

        String replace(char oldChar, char newChar) <br> -
        문자열에서 oldChar 로부터 되어 있는 문자를 newChar로 변환 리턴함

    
    #### 3) Object Wrapper 클래스
    - 자바에서 기본형으로 사용하는 Primitive 데이터 타입은 여덟가지
    - 자바 기본형을 객체로 변환할 수 있도록 도와주는 역할을 함
    논리형 - boolean - java.lang.Boolean <br>
    문자형 - char - java.lang.Charactor <br>
    수치형 <br>
    &nbsp; 1) 정수 <br>
    &nbsp;&nbsp;&nbsp;&nbsp; (1) byte - java.lang.Byte <br>
    &nbsp;&nbsp;&nbsp;&nbsp; (2) short - java.lang.Short <br>
    &nbsp;&nbsp;&nbsp;&nbsp; (3) int - java.lang.Integer <br>
    &nbsp;&nbsp;&nbsp;&nbsp; (4) long - java.lang.Long <br>
    &nbsp; 2) 정수 <br>
    &nbsp;&nbsp;&nbsp;&nbsp; (1) float - java.long.Floct
    &nbsp;&nbsp;&nbsp;&nbsp; (2) double - java.lang.Double

    
    




### 참고사항
- 기본 API : Java 에서 기본적으로 제공하는 API, (사용 형식) java.aaa.bbb 
- 확장 API : 기본 API 기반으로 작성하며 확장된 의미로 javax.aaa.bbb 형태로 표현함

- Example
    
    (1) 기본 API : java.lang.Object,  java.util.List 등

    (2) 확장 API : javax.swing.JButton, org.xml.sax, kr.or.javacate 등




# Object 클래스

## 클래스 유틸리티

- protected Object clone() - 객체 자신을 복사하여 똑같은 복사본을 리턴함
- protected void finalize() - 가비지 컬렉터에 의해 객체가 메모리에서 삭제 대상으로 결정될 경우, 제거 전에 호출되는 메소드
- Class getClass() - 객체의 클래스 정보를 리턴함
- boolean quals(Object obj) - 객체가 같은지 비교하는 메소드, 모든 클래스에서 오버라이딩해야 함
- String toString() - 객체 정보를 문자열로 리턴함
- int hashCode() - 객체의 고유값을 해시 코드로 리턴함

## 동기화 유틸리티

- void notify() - 객체를 사용하려고 대기하고 있는 스레드 중 하나를 깨움
- void notifyAll() - 객체를 사용하려고 대기하고 있는 모든 스레드를 깨움
- void wait() - 다른 객체가 깨워줄 때까지 대기 상태
- void wait(long timeout) - 다른 객체가 깨워주거나 "TimeOver"까지 대기상태
- void wait(long timeout, int nanos) - 다른 객체가 깨워주거나 "TimeOver" 시간의 나노초까지 지정하여 대기상태로 만듬

> Object 클래스에는 객체의 정보를 제공하는 특수한 메소드가 있음, 자주 사용되는 메소드는 toString(), equals(), hashCode()


__1. toString()__
- int, char 같이 기본형을 나타내는 primitive 데이터 타입을 제외한 모든 것이 객체로 이루어져 있음
- toString() 메소드는 이러한 객체 정보를 문자열로 리턴함
- 아래 예제 참조
```java
package kr.or.javacafe.sample6;

public class TV{
    
    int channel;
    int volume;

    public TV(int channel, int volume){
        this.channel = channel;
        this.volume = volume;
    }

    public String toString(){ // 숫자형을 문자형으로 변환하여 return
        return "TV Channel is " + this.channel + ", Volume is " + this.vloume;
    }

    public static void main(String args[]){
        TV objTV = new TV(11, 5);
        System.out.printIn(objTV);
    }
}

// 실행 결과 : TV Channel is 11, Volume is 5
```

__2. equals()__
- 자바에서 객체를 생성하면 객체 자체를 가져오는 것이 아니라 단순히 객체의 레퍼런스를 가져옴
    > TV objTV = new TV();
- 객체 레퍼런스란 일종의 포인터로 'new' 키워드를 이용하여 생성된 objTV 변수는 TV 객체가 생성된 곳의 주소값을 가지게 됨
- 실제 TV 객체 자체는 메모리 힙(Heap) 영역에 생성되고 TV 객체를 호출할 수 있도록 이 영역의 주소값만 제공함
- equals() 메소드는 객체간의 비교할 수 있도록 Object 클래스에서 기본으로 제공함
- 아래 예제 참조
```java

package kr.or.javacate.sample7;

public class TV{

    int channel;
    int volume;

    public TV(int channel, int volume){
        this.channel = channel;
        this.volume = volume;
    }

    public String toString(){ // 숫자형을 문자형으로 변환하여 return
        return "TV Channel is " + this.channel + ", Volume is " + this.vloume;
    }

    public static void main(String args[]){
        TV objTV1 = new TV(11, 5);
        TV objTV2 = new TV(11, 5);

        // 실행 결과는 두 객체가 다르다.
        if(objTV1.equals(objTV2)){
            System.out.printIn("두 객체는 같다.");
        } else {
            System.out.printIn("두 객체는 다르다.");
        }

        // 두 객체의 레퍼런스를 같게 만듬
        objTV1 = objTV2;
        
        // 레퍼런스 동일하게 맞추면 실행 결과는 두 객체가 같다.
        if(objTV1.equals(objTV2)){
            System.out.printIn("두 객체는 같다.");
        } else {
            System.out.printIn("두 객체는 다르다.");
        }

}


// 실행 결과 : 첫번째 if 문은 두 객체가 다르다, 두번째 if 문은 두 객체가 같다.
```
- objTV1, objTV2 변수가 가리키는 객체가 다른 메모리 공간에 있다면, 내용이 같더라도 equals() 메소드에선 False이 됨
- 클래스의 인스턴스가 프로세스 내에서 하나만 생성되는 경우라든지, 상속 관계의 부모 클래스에 이미 equals() 메소드가 구현되어 있는 경우라면 굳이 equals() 메소드를 오버라디이하지 않아도 됨

    > 오버라이딩(overriding) - 상속 관계에 있는 부모 클래스에서 이미 정의된 메소드를 자식 클래스에서 같은 시그니처를 갖는 메소드로 다시 정의하는 것 <br>
    > 오버로딩(Overloading) - 서로 다른 시그니처를 갖는 여러 메소드를 하나의 이름으로 정의하는 것 <br>


__3. hashCode()__
- hashCode() 메소드를 이용하여 객체의 고유값을 구함
- HashTable이나 HashMap 같은 해싱 알고리즘을 사용하는 자료구조에 주로 사용됨
- 해당 메소드를 호출하면 객체의 메모리 주소를 바탕으로 4바이트의 고유한 숫자 값으로 리턴함
- 메모리 주소가 다른 객체는 같은 hashCode(해시 코드값)을 가질 수 없음
- equals() 메소드를 오버라이딩할 경우 hashCode() 메소드도 같이 해야됨
- equals() 메소드만 오버라이딩할 경우 해시기반의 자료 구조를 사용할 때 올바르게 동작하지 않음
- 참고로 String 클래스는 문자열의 메모리 값이 달라도 문자열이 동일하면 같은 객체로 바라보기 때문에 hashCode() 메소드도 같은 해시값을 리턴하도록 오버라이딩 되어 있음

