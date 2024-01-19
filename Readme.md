# God of Java
## 클래스
### 정의
- 각각의 객체를 나타내는 청사진.
- 자바에서 하나의 객체를 나타내기 위한 가장 작은 단위.
- 상태와 행동을 가진다.

### 메소드
- 클래스의 행동 제공.

### 객체와의 차이
- 틀과 실체로써의 차이.
- 클래스로 객체를 생성할 수 있음.
- 객체 참조 변수는 stack에 들어감.

## 변수
### 변수의 종류
1. local variable
1. parameter
1. instance variable
1. class variable

### 자료형
1. Reference Type: new를 사용한 타입
1. Primitive Type: new 안쓴 것
1. 단, string은 예외.

### char
1. 16 bit / (c++은 8bit)
1. 음수 없음


## 객체 
### switch
- 비교 구문에 객체가 들어갈 수 있음.
    - equals로 비교
    - char, byte, short, int, enum, string
    - long이 안되는 이유: 메모리 사용효율, 필요성이 부족

### for
```Java
for (A a : list) {
    
}
```

## 객체
### 2차원 배열
- 배열의 크기 다르게 생성 가능
    ```java
    int[][] a = new int[4][];
    a[1] = new int[4];
    a[0] = new int[5];
    ```
- length 시간복잡도
    - O(1)

### 객체의 생성 과정

1. member변수, 메소드의 메모리 할당
1. this참조 초기화
1. 필드 초기화: 타입 기본값
1. 필드의 명시적 초기화: 기본값
1. 초기화 블록 실행: 이름 없이 블록 쓴것
1. 생성자의 실행

### static 
1. 객체 생성 없이 method/변수 접근이 가능
1. 클래스로 전역 참조

## package
### 제약
1. 이름에 예약어를 사용할 수 없음
1. root에서 실행하는게 관례
    - class path로 실행 위치 찾음
    - 프로젝트 구조의 통일로 편의성 + 상대경로 표현 가능
1. java.lang은 import 없이 가능
1. 자식 패키지는 명시 없이 import 불가
1. static 변수,메서드는 import static으로 가능

### 접근 제어자


