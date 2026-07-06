# Lesson01: Java 다시 떠올리기

이 Lesson은 Java를 한 번 배웠지만 기억이 흐려진 학습자를 위한 복구 수업이다.

목표는 모든 문법을 새로 외우는 것이 아니다. IntelliJ에서 Java 파일을 만들고, `main` 메서드를 실행하고, 변수, 조건문, 반복문, 메서드를 다시 손에 익히는 것이다.

예상 수업 시간은 약 2시간이다.

- 이론: 약 30%
- 실습: 약 70%

## 1. 학습 목표

이 Lesson을 마치면 다음을 할 수 있다.

- IntelliJ에서 Java 프로젝트와 클래스를 만들 수 있다.
- `main` 메서드가 Java 프로그램의 시작점임을 설명할 수 있다.
- 변수, 자료형, 문자열, 숫자, boolean 값을 다시 사용할 수 있다.
- `if`, `for`를 사용해서 간단한 업무 규칙을 표현할 수 있다.
- 메서드로 반복되는 코드를 분리할 수 있다.
- `Book`, `Product` 같은 업무 객체를 코드로 표현하는 첫 감각을 되찾을 수 있다.

## 2. 선수지식

이 Lesson은 완전한 입문자를 위한 수업이 아니다. 다음 내용을 예전에 한 번이라도 본 적이 있다고 가정한다.

- Java 파일은 `.java` 확장자를 가진다.
- Java 코드는 클래스 안에 작성한다.
- 프로그램은 보통 `main` 메서드에서 시작한다.
- 변수에는 값을 저장한다.
- 조건문과 반복문으로 실행 흐름을 제어한다.

기억이 정확하지 않아도 괜찮다. 이번 Lesson의 목적은 "아, 이거였지"라는 감각을 되살리는 것이다.

## 3. 왜 배우는가

백엔드 개발자는 결국 데이터를 다룬다.

ERP 시스템을 예로 들면 다음과 같은 질문을 코드로 표현해야 한다.

- 이 상품의 가격은 얼마인가?
- 재고가 0보다 큰가?
- 주문 수량이 재고보다 많은가?
- 직원의 부서가 어떤 곳인가?
- 도서 대여가 가능한 상태인가?

이 질문들은 거창해 보이지만 시작점은 단순하다.

- 값을 저장한다.
- 값을 비교한다.
- 조건에 따라 다른 메시지를 출력한다.
- 여러 데이터를 반복해서 처리한다.
- 반복되는 로직을 메서드로 분리한다.

Java 기본 문법은 Spring Boot나 ERP 프로젝트와 분리된 것이 아니다. 나중에 Controller, Service, Repository를 만들 때도 결국 변수, 조건문, 반복문, 메서드를 계속 사용한다.

## 4. 핵심 개념

### 클래스

Java 코드는 클래스 단위로 작성한다.

```java
public class Lesson01App {
}
```

지금은 클래스를 "코드를 담는 상자" 정도로 이해해도 충분하다. 객체지향을 깊게 다루는 것은 Lesson11 이후에 진행한다.

### main 메서드

`main` 메서드는 Java 프로그램의 시작점이다.

```java
public static void main(String[] args) {
    System.out.println("Hello Java");
}
```

IntelliJ에서 실행 버튼을 누르면 이 메서드 안의 코드가 위에서 아래로 실행된다.

### 변수와 자료형

변수는 값을 저장하는 이름이다.

```java
String bookTitle = "Java Backend";
int price = 30000;
boolean available = true;
```

자주 사용하는 기본 형태는 다음과 같다.

| 자료형 | 의미 | 예시 |
| --- | --- | --- |
| `String` | 문자열 | `"Java Backend"` |
| `int` | 정수 | `30000` |
| `double` | 실수 | `4.5` |
| `boolean` | 참 또는 거짓 | `true`, `false` |

### 조건문

조건문은 업무 규칙을 표현한다.

```java
if (stock > 0) {
    System.out.println("주문 가능");
} else {
    System.out.println("품절");
}
```

ERP에서는 조건문이 자주 등장한다.

- 재고가 있으면 주문 가능
- 재고가 부족하면 주문 불가
- 권한이 관리자이면 관리 메뉴 접근 가능
- 결제 상태가 완료이면 배송 준비

### 반복문

반복문은 여러 데이터를 같은 방식으로 처리할 때 사용한다.

```java
for (int i = 1; i <= 3; i++) {
    System.out.println(i);
}
```

지금은 배열과 컬렉션을 깊게 다루지 않는다. 이번 Lesson에서는 반복문의 감각만 되살린다.

### 메서드

메서드는 이름이 붙은 코드 묶음이다.

```java
public static void printProduct(String name, int price) {
    System.out.println(name + " / " + price + "원");
}
```

메서드를 사용하면 같은 코드를 여러 번 복사하지 않아도 된다.

## 5. IntelliJ 실습

### 실습 1: Java 프로젝트 만들기

1. IntelliJ IDEA를 실행한다.
2. `New Project`를 선택한다.
3. `Java`를 선택한다.
4. JDK는 Java 17을 선택한다.
5. 프로젝트 이름을 `Lesson01-Java-Recovery`로 입력한다.
6. 프로젝트를 생성한다.

이번 Lesson에서는 Gradle을 반드시 사용할 필요는 없다. 목표는 Java 실행 감각을 회복하는 것이다. Gradle과 프로젝트 구조는 이후 Lesson에서 자연스럽게 확장한다.

### 실습 2: 클래스 만들기

1. `src` 폴더를 찾는다.
2. `src`에서 마우스 오른쪽 버튼을 누른다.
3. `New` > `Java Class`를 선택한다.
4. 클래스 이름을 `Lesson01App`으로 입력한다.

생성된 파일에 다음 코드를 작성한다.

```java
public class Lesson01App {
    public static void main(String[] args) {
        System.out.println("JBMC Lesson01");
        System.out.println("Java 기억을 다시 깨웁니다.");
    }
}
```

실행 버튼을 눌러 콘솔에 문장이 출력되는지 확인한다.

### 실습 3: Book 정보 출력하기

`main` 메서드 안에 다음 코드를 추가한다.

```java
String bookTitle = "Java Backend Master";
String author = "JBMC";
int price = 30000;
boolean available = true;

System.out.println("도서명: " + bookTitle);
System.out.println("저자: " + author);
System.out.println("가격: " + price + "원");
System.out.println("대여 가능 여부: " + available);
```

여기서 중요한 것은 문법을 완벽하게 외우는 것이 아니다. 값을 이름 붙여 저장하고, 그 값을 출력하는 감각을 되찾는 것이다.

### 실습 4: 재고 조건 판단하기

아래 코드를 추가한다.

```java
int stock = 5;

if (stock > 0) {
    System.out.println("현재 대여 가능합니다.");
} else {
    System.out.println("현재 대여할 수 없습니다.");
}
```

`stock` 값을 `0`으로 바꾸고 다시 실행해 본다.

### 실습 5: Product 3개 출력하기

이번에는 반복문으로 상품 번호를 출력한다.

```java
for (int i = 1; i <= 3; i++) {
    System.out.println("상품 번호: P-" + i);
}
```

반복문은 나중에 여러 상품, 여러 주문, 여러 직원을 처리할 때 다시 등장한다.

### 실습 6: 메서드로 분리하기

`main` 메서드 아래에 다음 메서드를 추가한다.

```java
public static void printProduct(String name, int price, int stock) {
    System.out.println("상품명: " + name);
    System.out.println("가격: " + price + "원");
    System.out.println("재고: " + stock + "개");

    if (stock > 0) {
        System.out.println("판매 가능");
    } else {
        System.out.println("품절");
    }

    System.out.println("--------------------");
}
```

그리고 `main` 메서드에서 호출한다.

```java
printProduct("키보드", 45000, 10);
printProduct("마우스", 25000, 0);
printProduct("모니터", 180000, 3);
```

이제 상품 출력 규칙을 한 곳에 모아두고 여러 번 사용할 수 있다.

## 6. 예제 코드

아래 코드는 Lesson01의 전체 예제다.

```java
public class Lesson01App {
    public static void main(String[] args) {
        System.out.println("JBMC Lesson01");
        System.out.println("Java 기억을 다시 깨웁니다.");
        System.out.println("--------------------");

        String bookTitle = "Java Backend Master";
        String author = "JBMC";
        int price = 30000;
        boolean available = true;

        System.out.println("도서명: " + bookTitle);
        System.out.println("저자: " + author);
        System.out.println("가격: " + price + "원");
        System.out.println("대여 가능 여부: " + available);
        System.out.println("--------------------");

        int stock = 5;

        if (stock > 0) {
            System.out.println("현재 대여 가능합니다.");
        } else {
            System.out.println("현재 대여할 수 없습니다.");
        }

        System.out.println("--------------------");

        for (int i = 1; i <= 3; i++) {
            System.out.println("상품 번호: P-" + i);
        }

        System.out.println("--------------------");

        printProduct("키보드", 45000, 10);
        printProduct("마우스", 25000, 0);
        printProduct("모니터", 180000, 3);
    }

    public static void printProduct(String name, int price, int stock) {
        System.out.println("상품명: " + name);
        System.out.println("가격: " + price + "원");
        System.out.println("재고: " + stock + "개");

        if (stock > 0) {
            System.out.println("판매 가능");
        } else {
            System.out.println("품절");
        }

        System.out.println("--------------------");
    }
}
```

예상 출력은 다음과 비슷하다.

```text
JBMC Lesson01
Java 기억을 다시 깨웁니다.
--------------------
도서명: Java Backend Master
저자: JBMC
가격: 30000원
대여 가능 여부: true
--------------------
현재 대여 가능합니다.
--------------------
상품 번호: P-1
상품 번호: P-2
상품 번호: P-3
--------------------
상품명: 키보드
가격: 45000원
재고: 10개
판매 가능
--------------------
상품명: 마우스
가격: 25000원
재고: 0개
품절
--------------------
상품명: 모니터
가격: 180000원
재고: 3개
판매 가능
--------------------
```

## 7. 코드 설명

### 실행 흐름

프로그램은 `main` 메서드의 첫 줄부터 실행된다.

```java
public static void main(String[] args) {
}
```

지금은 `public`, `static`, `void`, `String[] args`를 모두 깊게 이해하지 않아도 된다. 이번 Lesson에서는 "`main`이 시작점이다"만 확실히 기억한다.

### 변수

```java
String bookTitle = "Java Backend Master";
int price = 30000;
boolean available = true;
```

변수는 값에 이름을 붙인다.

이름이 없으면 코드는 금방 읽기 어려워진다. `30000`이라는 숫자만 보면 의미를 알기 어렵지만, `price`라는 이름이 붙으면 가격이라는 뜻이 생긴다.

### 조건문

```java
if (stock > 0) {
    System.out.println("판매 가능");
} else {
    System.out.println("품절");
}
```

조건문은 업무 규칙을 코드로 표현한다.

`stock > 0`은 "재고가 0보다 큰가?"라는 질문이다. 이 질문의 결과가 참이면 판매 가능, 거짓이면 품절을 출력한다.

### 반복문

```java
for (int i = 1; i <= 3; i++) {
    System.out.println("상품 번호: P-" + i);
}
```

반복문은 같은 패턴을 여러 번 실행한다.

나중에는 상품 3개를 직접 출력하는 대신 상품 목록을 반복하면서 처리하게 된다. 그 단계는 Collection 파트에서 본격적으로 다룬다.

### 메서드

```java
public static void printProduct(String name, int price, int stock) {
}
```

메서드는 반복되는 코드를 이름 붙여 묶는다.

`printProduct`는 상품명, 가격, 재고를 받아서 상품 정보를 출력한다. 이처럼 메서드를 만들면 같은 출력 규칙을 여러 상품에 재사용할 수 있다.

## 8. Spring Boot 연결

Spring Boot를 배우면 코드는 더 많은 파일로 나뉜다.

하지만 기본 감각은 같다.

```java
if (stock > 0) {
    return "판매 가능";
}
return "품절";
```

이런 판단은 나중에 Service 계층에서 자주 사용된다.

예를 들어 상품 주문 API를 만든다면 다음 흐름이 필요하다.

1. 요청으로 상품 번호와 주문 수량이 들어온다.
2. Service에서 현재 재고를 확인한다.
3. 재고가 충분하면 주문을 진행한다.
4. 재고가 부족하면 주문을 거절한다.

즉, 오늘 배운 변수, 조건문, 메서드는 Spring Boot에서 Controller와 Service를 이해하기 위한 바닥이다.

## 9. ERP 연결

ERP는 회사의 업무를 관리하는 시스템이다.

ERP에서는 다음과 같은 데이터를 계속 다룬다.

- 직원
- 상품
- 재고
- 거래처
- 주문
- 결제
- 입고와 출고

오늘 작성한 `Product` 예제는 아주 작지만 ERP의 출발점이다.

```java
printProduct("키보드", 45000, 10);
```

이 한 줄은 나중에 다음 구조로 발전한다.

- 상품 테이블
- 상품 등록 화면
- 상품 조회 API
- 재고 확인 로직
- 주문 가능 여부 판단
- Oracle DB 저장
- Spring Boot Service 로직

따라서 Lesson01은 단순한 복습이 아니라 ERP 백엔드로 가기 위한 첫 번째 회복 훈련이다.

## 10. 미션

### 미션: 도서 대여 가능 여부 출력 프로그램 만들기

IntelliJ에서 `BookRentalApp` 클래스를 만들고 직접 구현한다.

요구사항:

- 도서명, 저자, 가격, 재고 수량을 변수로 만든다.
- 도서 정보를 출력한다.
- 재고가 1권 이상이면 `대여 가능`을 출력한다.
- 재고가 0권이면 `대여 불가`를 출력한다.
- `printBook` 메서드를 만들어 도서 정보를 출력한다.
- 서로 다른 도서 3권을 `printBook` 메서드로 출력한다.

예시 도서:

- `Java Start`, `JBMC`, `25000`, `3`
- `Spring Boot Basic`, `JBMC`, `35000`, `0`
- `ERP Backend`, `JBMC`, `45000`, `5`

추가 도전:

- 가격이 30000원 이상이면 `전문 서적`을 출력한다.
- 가격이 30000원 미만이면 `입문 서적`을 출력한다.

## 11. 체크리스트

- [ ] IntelliJ에서 Java 프로젝트를 만들 수 있다.
- [ ] Java 클래스를 만들 수 있다.
- [ ] `main` 메서드에서 프로그램을 실행할 수 있다.
- [ ] `System.out.println`으로 값을 출력할 수 있다.
- [ ] `String`, `int`, `boolean` 변수를 사용할 수 있다.
- [ ] `if`, `else`로 재고 상태를 판단할 수 있다.
- [ ] `for` 반복문을 실행할 수 있다.
- [ ] 메서드를 만들고 호출할 수 있다.
- [ ] `Book` 또는 `Product` 예제를 직접 수정할 수 있다.
- [ ] Java 기본 문법이 Spring Boot와 ERP 로직의 기초임을 설명할 수 있다.

## 12. 면접 질문

1. Java에서 `main` 메서드는 어떤 역할을 하는가?
2. 변수에 이름을 붙이는 이유는 무엇인가?
3. `String`, `int`, `boolean`은 각각 어떤 값을 표현하는가?
4. `if`, `else`는 어떤 상황에서 사용하는가?
5. 반복문은 왜 필요한가?
6. 메서드를 사용하면 어떤 장점이 있는가?
7. 재고가 0보다 큰지 판단하는 코드는 ERP에서 어떤 업무와 연결될 수 있는가?
8. Java 기본 문법이 Spring Boot Service 로직과 연결되는 이유는 무엇인가?

## 13. 복습 문제

1. `System.out.println("Hello Java");`를 실행하면 어떤 일이 일어나는가?
2. 도서 가격을 저장하기 위한 변수 선언 코드를 작성하라.
3. 재고 수량이 0이면 `품절`, 0보다 크면 `판매 가능`을 출력하는 조건문을 작성하라.
4. 1부터 5까지 출력하는 `for` 반복문을 작성하라.
5. 상품명과 가격을 받아 출력하는 `printProduct` 메서드를 작성하라.
6. 오늘 만든 `BookRentalApp`에서 메서드를 사용하지 않으면 어떤 불편함이 생기는가?

## 14. 다음 Lesson

다음 Lesson에서는 Java의 값과 타입을 더 분명하게 정리한다.

Lesson01에서는 변수, 조건문, 반복문, 메서드를 한 번에 다시 떠올렸다. Lesson02에서는 이 중에서 변수와 자료형을 더 자세히 다룬다.

특히 ERP에서 자주 등장하는 상품명, 가격, 수량, 할인율, 판매 가능 여부 같은 값을 어떤 자료형으로 표현해야 하는지 연습한다.

Lesson02로 넘어가기 전, 다음 질문에 답해보자.

- 상품명은 왜 숫자가 아니라 문자열인가?
- 재고 수량은 왜 `int`로 표현할 수 있는가?
- 판매 가능 여부는 왜 `boolean`으로 표현할 수 있는가?
