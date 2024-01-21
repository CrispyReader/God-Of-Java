
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

### 접근 제어자
| 접근제어자 | 클래스 내 | 같은 페키지내 | 상속 | 외부 |
|---|---|---|---|---|
| public | O | O | O | O |
| protected | O | O | O | X |
| default | O | O | X | X |
| private | O | X | X | X |

### 상속
- 다중 상속 X, 상속시 매개 변수 없는 것부터 찾음
#### 메소드 오버라이딩
1. 동일 시그니처
2. 리턴 타입 유지
3. 접근 제어자는 확장되는 쪽으로
#### instanceOf
- JVM 구현에 의존해 객체가 클래스 인지 구분
- 접근
    1. 객체의 타입 정보 확인 - 메타 정보(class 객체) 접근
    2. 클래스/인터페이스 계층 구조 비교
    3. 비교 결과 반환
        - true: 지정된 클래스의 인스턴스, 부모 클래스, 인터페이스의 구현체
        - false: null, else
- 다형성
    - 하나의 객체가 여러 타입을 가질 수 있다는 특성
    - 상속 등의 상황에서 부모 타입 변수에 자식 타입을 할당하는 등의 예시가 있다.
 
### Nested class
- innerClass
    - outer.new Inerclass
    - outer의 모든 변수 참조 가능
- StaticInnerClass
    - outer.StaticInnerClass
    - outer의 static만 참조 가능
      
## 동등
### equals
- 조건
    1. 재귀: a => a
    2. 대칭: a => b, b => a
    3. 타동적: a => b, b => c, a => c
    4. 일관: equals결과는 항상 동일
    5. NULL: false
### hashCode
- 16진수, Java 실행 중엔 같은 값
- equals
    - true => hashCode 같아야 함.
    - false => hashCode 다를 필요는 없는데, 다르면 hashtable 등의 성능에 악영향

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


## 접근 제어
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

## Enum
- java.lang.Enum
- 메서드는 finalize

## 예외
### 상속 관계
- Throwable
    - Error: process에 치명, 시스템 등 외부 사유로 발생하는 오류
    - Exception: thread에 치명, 내부 원인으로 발생하는 오류
        - checked Exception: 컴파일러 등에 의해 발생하는 오류
        - unchecked/runtime exception: 실행 중 발생하는 예외
### 메소드
- getMessage, toString, printStackTrace

### 직접 예외 생성 Tip
- Runtime exception상속받아 던지기 (꼭 try catch로 감싸기)

## String
### 특징
- object 상속
- final로 선언됨
- Sequential, Comparable<String>, CharSequence 구현
- immutable, constant pool에서 재활용
### 주의 사항
- 메서드 중 intern 메서드 사용하지 않기
    - constant pool에 문자열 저장하는 메서드로 gc를 트리거 할 수 있음
### Builder와 Buffer
- StringBuffer: thread safe
- StringBuilder: thread unsafe
    - String의 +연산시 컴파일러가 builder로 바꿔줌
    - valueOf로 객체 출력함
 
## Annotation
### 패키지
- java.lang.annotation

### 기본
- Override, Deprecated, SupressWarning, Document

### 선언시 활용하는 것
- Target: 적용 대상
- Retention: 정보 유지 시기
- Inherited
- Interface

## Java.lang
### 특징
- import 없이 사용 가능

### System
- 출력
    - in: InputStream
    - out/err: PrintStream
        - valueOf 값을 이용해 객체 출력

### 기타
- 숫자: MIN_VALUE/MAX_VALUE
- 진수 변환: to진수String()
- 형변환: parse타입명
- property는 수정 가능
- Env는 수정 불가
- gc 등의 메서드는 호출해서는 안됨 <- 성능에 영향

## Generic
### 관례
- E: element, collection 등
- K: 키
- V: 값
- N: 숫자
- T: 타입
- S,U,V: 2,3,4번째 타입
### 만들어진 이유
- 형변환에서의 오류를 줄이고 확장 가능한 코드를 타입안전하게 짜기 위해 만들어 졌다.

### wild card
- bounded: ? extends T
- unbounded: ?

### 함수 선언시
- <T> 리턴타입 함수명(T)

## List
### 구현
- Serializable, Clonable, Iterable<E>, Collection<E>, List<E>, RandomAccess
### 함수
- indexOf, get, set, add, addAll, remove, removeAll, toArray, trimToSize, clear
### 종류
- ArrayList, ArrayDeque: thread unsafe
- vector, stack: thread safe
### ArrayList
- 빈생성자 사용시: 10개 공간 생성

## Set
### HashSet 
#### 구현
- Serializable, Clonable, Set<E>, Iterable<E>, Collection<E>
#### 빈생성자 사용시
- 16개 저장 공간 생성, 0.75의 loadFactor 설정
### 함수
- clear, add, remove, contains, isEmpty, size, iterator
### 사용 목적
- 중복 제거 등
### 종류
- hashtable: thread safe, Enumerable, 순환 처리 불가, null 안됨
- HashSet: thread unsafe, 초기 size 설정 가능
- TreeSet: RB tree로 만들어진 정렬 되는 set
### loadFactor
- 저장된 데이터 / 저장공간

## Queue
### LinkedList
#### implements
- Serializable, Cloneable, Iterable<E>, Collection<E>, Queue, Deque<E>, List<E>
### 함수
- addFirst, addLast, getFirst, getLast, removeLast, removeFirst, indexOf

## Map
### 종류
- hashMap, TreeMap, LinkedHashMap
### implements
- Serializable, Clonable, Map<E>

### HashMap
- 기본 생성자: 16개 저장공간
- size 생성자: size에 해당하는 저장공간만 생성
#### 함수
- put, putAll, get, remove, keySet, values, entrySet, size, clear, containsKey, containsValue

## Thread
### 사용 방법
- Runnable 구현
- Thread 확장

### 함수
#### static
- sleep (InterruptedError 던질 수 있음), start, activeCount, currentThread, interrupted, dumpStack
#### instance
- isAlive, isInterrupted, notify, notifyAll, run, getId, getName, getPriority, isDeamon, setDeamon, getState, getThreadGroup, wait, join, interrupt, checkAccess
#### 데몬 스레드
- 모니터링 처럼 다른 스레드가 떠있을때 동작해야 하는 작업을 띄워든 쓰레드
- 실행 여부 관계 없이 JVM 종료 가능6
#### 상태
- NEW, RUNNABLE, BLOCKED, WAITING, TIMED_WAITING, TERMINATED
##### 우선순위
- MAX_PRIORITY: 10
- NORM_PRIORITY: 5
- MIN_PRIORITY: 1
### Syncronized
- Thread의 access를 막는다.
    - monitor/intrinsic lock
- 메소드에서 리턴타입 앞에 붙여 사용
- syncronized block은 object lock 걸듯이 사용
    ```java
    syncronized(obj) {
      // logic
    }
    ```
### ThreadGroup
#### 함수
- activeCount, enumerate, getName, getParent, list, setDemon

## File
- Java6 쪽의 파일 처리 도구
### 함수
- list, listRows, listFiles
### 필터
- FileFiler
    - accept
- FilenameFilter
    - accept(dir, name)
### file을 연거 역순으로 닫아야하는 이유
1. 의존성 관리
3. 데이터 무결성
4. 예외처리 용이성
#### 예시
1. File -> Buffer
2. Buffer -> File

## I/O stream
### 특징
- byteStream 다룸
### InputStream
#### 특징
- abstract class
- closable 구현
#### 함수
- read, mark, reset, markSepperated, skip, close
### OutStream
#### 특징
- abstract
- Closable, Flushable 구현
#### 함수
- write, flush, close

## Reader/Writer
### 특징
- charStream 다룸
### Reader
#### 특징
- abstract class
- Readable, Closable 구현
#### 함수
- read, mark, reset, markSupported, Skip, Close, Ready
### Writer
#### 특징
- abstract class
- Appendable, Flushable, Closeable 구현
#### 함수
- append, write, flush, close
### Scanner
- java.util
- text 기반 기본 자료형 or 문자열 데이터 처리 클래스

## Serializable
- 있어야지 JVM에서 저장 혹은 네트워크 전송 해줌
- (static final long)SerialVersionUID라는 변수로 변경을 탐지
- transient
    - 저장, 전송에 포함하지 않는 변수에 사용하는 키워드

## NIO
- NEW io
- 속도 때문에 탄생
- Buffer와 Channel로 데이터 전송
### Buffer
#### 변수
- capacity (>=1), limit(>=1), position(>=0)
#### 함수
- flip, mark, reset, rewind, remaining, hashRemaining, clear
