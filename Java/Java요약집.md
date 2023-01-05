# JDK (Java Development Kit)
- 자바에 필요한 클래스(class), 컴파일(compile), 실행(execution), 배포(deployment) 등 개발에 필요한 환경도구를 JDK라 칭함
- JDK : 개발
- JRE : 실행
- JVM : 이식(이관 등)

# 자바 표기법
- 파스칼 표기법 : 첫 단어에 대문자, 클래스명이나 인터페이스 명에 사용됨 (예) class Car() , class Support() 등 
- 카멜 표기법 : 단어 사이에 대문자, 메소드 이름이나 변수명에 사용됨 (예) void speedUp()

# 자바의 기본적인 객체 모델
- 1) 클래스 (예) 자동차
- 2) 변수 (예) 자동차 색깔, 부품 이름
- 3) 매소드 (예) 가속, 감속, 브레이크 등 동적 행위

# main, static 
- main : JVM이 객체를 호출할 때에 진입점 역할을 수행함
- JVM 영역
- 1) Method 영역
- 2) Heap 영역
- 3) Stack 영역
- 여기서, Static 선언을 하게 되면 Heap 영역이 아닌 Methon, Stack 영역으로 메소드가 형성이 되면서 정상 실행이 된다.
- 만약 main 에 static 이 선언되어 있지 않다면 JVM 과 메모리 상의 구조적인 문제가 발생될 가능성이 크다.

# Package / Import
- 1) Package
- > 모든 클래스는 패키지라는 고유 주소를 가지고 있음
- > 일반적으로 클래스의 고유 주소를 나타내기 위해서 "패키지명+클래스명" 형태로 표기함

- 2) Import
- > 클래스 내부에서 다른 클래스의 위치를 표현하기 위해 사용함
- > 다만, java.lang. 내부에 속해져 있는 클래스의 경우엔 import 가 생략될 수 있다.

# 