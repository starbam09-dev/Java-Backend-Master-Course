# Lesson01: Java 기억 되살리기

이 Lesson은 Java를 한 번 배웠지만 기억이 흐려진 학습자를 위한 2시간 복구 수업이다.

목표는 문법을 많이 설명하는 것이 아니라 IntelliJ를 열고 직접 실행하면서 Java의 기본 감각을 되찾는 것이다.

수업 비율:

- 이론: 약 30분
- 실습: 약 90분

## 1. 학습 목표

이 Lesson을 마치면 다음을 할 수 있다.

- IntelliJ에서 Java 프로젝트와 클래스를 만들 수 있다.
- `main` 메서드에서 Java 프로그램을 실행할 수 있다.
- `String`, `int`, `boolean` 변수를 만들고 출력할 수 있다.
- `if`, `else`로 재고 상태를 판단할 수 있다.
- `for`로 반복 출력을 할 수 있다.
- 메서드를 만들어 반복되는 출력 코드를 줄일 수 있다.
- `Book`, `Product` 예제를 통해 Java 기본 문법이 Spring Boot와 ERP로 이어지는 흐름을 설명할 수 있다.

## 2. 선수지식

다음 내용을 예전에 한 번이라도 본 적이 있으면 충분하다.

- Java 코드는 클래스 안에 작성한다.
- 프로그램은 보통 `main` 메서드에서 시작한다.
- 변수는 값을 저장한다.
- 조건문은 상황에 따라 다른 코드를 실행한다.
- 반복문은 같은 작업을 여러 번 실행한다.

정확히 기억하지 못해도 괜찮다. 이번 Lesson은 새 내용을 많이 배우는 시간이 아니라, 손으로 다시 떠올리는 시간이다.

## 3. 왜 배우는가

ERP 백엔드는 결국 업무 데이터를 코드로 처리하는 일이다.

예를 들어 도서, 상품, 재고를 다룰 때 이런 판단이 필요하다.

- 도서명이 무엇인가?
- 상품 가격이 얼마인가?
- 재고가 남아 있는가?
- 재고가 없으면 어떤 메시지를 보여줄 것인가?
- 같은 출력 규칙을 여러 상품에 어떻게 적용할 것인가?

이 질문을 해결하는 출발점이 변수, 조건문, 반복문, 메서드다.

Spring Boot를 배울 때도 갑자기 완전히 다른 문법을 쓰는 것이 아니다. Controller와 Service 안에서도 결국 값을 받고, 조건을 판단하고, 메서드로 로직을 나눈다.

## 4. 핵심 개념

이번 Lesson에서 필요한 개념만 짧게 정리한다.

| 개념 | 오늘의 이해 |
| --- | --- |
| 클래스 | Java 코드를 담는 파일 단위 |
| `main` 메서드 | 프로그램이 시작되는 위치 |
| 변수 | 값에 이름을 붙여 저장하는 방법 |
| `String` | 도서명, 상품명 같은 문자열 |
| `int` | 가격, 수량 같은 정수 |
| `boolean` | 판매 가능 여부 같은 참/거짓 |
| `if`, `else` | 재고 상태 같은 업무 규칙 판단 |
| `for` | 같은 작업을 여러 번 반복 |
| 메서드 | 반복되는 코드를 이름 붙여 묶는 방법 |

오늘은 객체지향 이론을 깊게 설명하지 않는다. 클래스와 객체는 뒤의 OOP 파트에서 다시 다룬다.

## 5. IntelliJ 실습

전체 실습은 약 90분을 기준으로 진행한다. 각 단계마다 반드시 실행해보고 다음 단계로 넘어간다.

### 실습 1: 프로젝트 만들기

예상 시간: 10분

1. IntelliJ IDEA를 실행한다.
2. `New Project`를 선택한다.
3. `Java`를 선택한다.
4. JDK는 `17`을 선택한다.
5. 프로젝트 이름을 `Lesson01-Java-Recovery`로 입력한다.
6. 프로젝트를 생성한다.

이번 Lesson에서는 Gradle을 사용하지 않아도 된다. 목표는 Java 실행 감각을 되찾는 것이다.

### 실습 2: 첫 클래스 실행하기

예상 시간: 10분

`src` 폴더 아래에 `Lesson01App` 클래스를 만든다.

```java
public class Lesson01App {
    public static void main(String[] args) {
        System.out.println("JBMC Lesson01");
        System.out.println("Java 기억을 다시 깨웁니다.");
    }
}
```

실행 후 콘솔에 두 줄이 보이면 성공이다.

확인:

- [ ] 실행 버튼을 눌렀다.
- [ ] 콘솔에 `JBMC Lesson01`이 출력됐다.
- [ ] 문자열을 바꾼 뒤 다시 실행해봤다.

### 실습 3: Book 변수 만들기

예상 시간: 15분

`main` 메서드 안에 도서 정보를 저장한다.

```java
String bookTitle = "Java Backend Master";
String author = "JBMC";
int price = 30000;
boolean available = true;

System.out.println("도서명: " + bookTitle);
System.out.println("저자: " + author);
System.out.println("가격: " + price + "원");
System.out.println("대여 가능: " + available);
```

직접 바꿔보기:

- `bookTitle`을 다른 책 이름으로 바꾼다.
- `price`를 다른 가격으로 바꾼다.
- `available`을 `false`로 바꾸고 다시 실행한다.

기억할 것:

- 도서명은 `String`
- 가격은 `int`
- 가능 여부는 `boolean`

### 실습 4: 재고 조건 판단하기

예상 시간: 15분

도서 재고를 변수로 만들고 대여 가능 여부를 판단한다.

```java
int stock = 5;

if (stock > 0) {
    System.out.println("대여 가능");
} else {
    System.out.println("대여 불가");
}
```

직접 바꿔보기:

- `stock`을 `0`으로 바꾸고 실행한다.
- `stock`을 `10`으로 바꾸고 실행한다.
- 출력 문장을 원하는 문장으로 바꾼다.

업무 관점:

`stock > 0`은 단순한 문법이 아니라 "재고가 남아 있는가?"라는 업무 질문이다.

### 실습 5: Product 번호 반복 출력하기

예상 시간: 10분

상품 번호를 1번부터 5번까지 출력한다.

```java
for (int i = 1; i <= 5; i++) {
    System.out.println("상품 번호: P-" + i);
}
```

직접 바꿔보기:

- 3개만 출력하도록 바꾼다.
- 10개까지 출력하도록 바꾼다.
- `P-` 대신 `BOOK-`이 붙도록 바꾼다.

반복문은 나중에 여러 상품, 여러 주문, 여러 직원을 처리할 때 다시 사용한다.

### 실습 6: Product 출력 메서드 만들기

예상 시간: 20분

`main` 메서드 아래에 `printProduct` 메서드를 만든다.

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

`main` 메서드 안에서 호출한다.

```java
printProduct("키보드", 45000, 10);
printProduct("마우스", 25000, 0);
printProduct("모니터", 180000, 3);
```

직접 바꿔보기:

- 상품을 하나 더 추가한다.
- 재고가 `0`인 상품과 `1` 이상인 상품을 모두 만들어본다.
- 가격이 100000원 이상이면 `고가 상품`을 출력하도록 조건문을 추가해본다.

### 실습 7: 전체 코드 정리하기

예상 시간: 10분

마지막으로 전체 코드를 아래와 비슷한 형태로 정리한다.

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
        System.out.println("대여 가능: " + available);
        System.out.println("--------------------");

        int stock = 5;

        if (stock > 0) {
            System.out.println("대여 가능");
        } else {
            System.out.println("대여 불가");
        }

        System.out.println("--------------------");

        for (int i = 1; i <= 5; i++) {
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

## 6. 예제 코드

이번 Lesson의 핵심 예제는 `Book` 정보 출력과 `Product` 재고 판단이다.

가장 중요한 코드는 아래 세 부분이다.

```java
String bookTitle = "Java Backend Master";
int price = 30000;
boolean available = true;
```

```java
if (stock > 0) {
    System.out.println("판매 가능");
} else {
    System.out.println("품절");
}
```

```java
public static void printProduct(String name, int price, int stock) {
    System.out.println("상품명: " + name);
    System.out.println("가격: " + price + "원");
    System.out.println("재고: " + stock + "개");
}
```

이 세 가지를 직접 칠 수 있으면 Lesson01의 핵심은 통과다.

## 7. 코드 설명

설명은 필요한 만큼만 정리한다.

`String bookTitle`은 도서명을 저장한다.

`int price`는 가격처럼 정수로 표현할 수 있는 값을 저장한다.

`boolean available`은 가능 여부처럼 `true` 또는 `false`로 표현되는 값을 저장한다.

`if (stock > 0)`은 재고가 있는지 판단한다.

`printProduct`는 상품 출력 규칙을 하나의 메서드로 묶는다. 같은 출력 코드를 세 번 복사하지 않고, 상품명과 가격과 재고만 바꿔서 재사용할 수 있다.

이번 Lesson에서 `public`, `static`, `void`를 깊게 외울 필요는 없다. 지금은 메서드를 만들고 호출하는 흐름에 익숙해지는 것이 더 중요하다.

## 8. Spring Boot 연결

Spring Boot에서 상품 주문 API를 만들면 Service 안에서 이런 판단을 하게 된다.

```java
if (stock > 0) {
    return "주문 가능";
}

return "품절";
```

오늘은 콘솔에 출력했지만, Spring Boot에서는 같은 판단 결과를 API 응답으로 돌려준다.

연결 흐름:

1. Java 변수로 값을 담는다.
2. Java 조건문으로 업무 규칙을 판단한다.
3. Java 메서드로 로직을 분리한다.
4. Spring Boot Service에서 같은 방식으로 주문 가능 여부를 판단한다.

그래서 Lesson01은 Spring Boot 이전의 준비 운동이다.

## 9. ERP 연결

ERP에서는 재고, 상품, 주문 같은 업무 데이터를 계속 다룬다.

오늘의 예제는 작지만 ERP의 기본 흐름과 연결된다.

```java
printProduct("키보드", 45000, 10);
```

이 코드는 나중에 다음 흐름으로 커진다.

- 상품 등록
- 상품 조회
- 재고 확인
- 주문 가능 여부 판단
- Oracle DB 저장
- Spring Boot API 응답

즉, `stock > 0`은 단순 문법이 아니라 ERP에서 "주문할 수 있는가?"를 판단하는 첫 번째 형태다.

## 10. 미션

### 미션: 도서 대여 관리 프로그램 만들기

예상 시간: 25분

IntelliJ에서 `BookRentalApp` 클래스를 새로 만들고 직접 구현한다.

요구사항:

- `main` 메서드를 만든다.
- `printBook` 메서드를 만든다.
- `printBook`은 도서명, 저자, 가격, 재고를 전달받는다.
- 도서명, 저자, 가격, 재고를 출력한다.
- 재고가 1권 이상이면 `대여 가능`을 출력한다.
- 재고가 0권이면 `대여 불가`를 출력한다.
- 서로 다른 도서 3권을 출력한다.

사용할 예시 데이터:

| 도서명 | 저자 | 가격 | 재고 |
| --- | --- | --- | --- |
| Java Start | JBMC | 25000 | 3 |
| Spring Boot Basic | JBMC | 35000 | 0 |
| ERP Backend | JBMC | 45000 | 5 |

추가 도전:

- 가격이 30000원 이상이면 `전문 서적`을 출력한다.
- 가격이 30000원 미만이면 `입문 서적`을 출력한다.
- 출력 마지막에 `--------------------`를 출력한다.

완성 예시 형태:

```java
public static void printBook(String title, String author, int price, int stock) {
    // 직접 구현
}
```

## 11. 체크리스트

- [ ] IntelliJ에서 Java 프로젝트를 만들었다.
- [ ] Java 클래스를 만들고 실행했다.
- [ ] `main` 메서드가 시작점이라는 것을 설명할 수 있다.
- [ ] `String`, `int`, `boolean` 변수를 직접 작성했다.
- [ ] `if`, `else`로 재고를 판단했다.
- [ ] `for`로 반복 출력을 했다.
- [ ] `printProduct` 메서드를 만들고 호출했다.
- [ ] `BookRentalApp` 미션을 직접 구현했다.
- [ ] 재고 판단이 Spring Boot Service와 연결된다는 것을 이해했다.
- [ ] 재고 판단이 ERP 주문 가능 여부와 연결된다는 것을 이해했다.

## 12. 면접 질문

1. Java에서 `main` 메서드는 어떤 역할을 하는가?
2. `String`, `int`, `boolean`은 각각 어떤 값을 저장할 때 사용하는가?
3. `if`, `else`는 어떤 상황에서 사용하는가?
4. 반복문은 왜 필요한가?
5. 메서드를 사용하면 어떤 점이 좋아지는가?
6. `stock > 0` 같은 조건은 ERP에서 어떤 업무 판단과 연결될 수 있는가?

## 13. 복습 문제

1. `BookRentalApp` 클래스를 새로 만들고 `main` 메서드를 작성하라.
2. 도서명, 가격, 재고를 각각 변수로 선언하라.
3. 재고가 0이면 `대여 불가`, 1 이상이면 `대여 가능`을 출력하는 조건문을 작성하라.
4. 1부터 5까지 도서 번호를 출력하는 반복문을 작성하라.
5. 도서명, 저자, 가격, 재고를 받아 출력하는 `printBook` 메서드를 작성하라.

## 14. 다음 Lesson

다음 Lesson에서는 변수와 자료형을 더 자세히 정리한다.

Lesson01에서는 여러 문법을 한 번에 다시 움직여 보았다. Lesson02에서는 그중에서도 값을 저장하는 방법에 집중한다.

다음 질문을 생각해보고 넘어가자.

- 도서명은 왜 `String`인가?
- 가격과 재고는 왜 `int`로 표현할 수 있는가?
- 대여 가능 여부는 왜 `boolean`으로 표현할 수 있는가?
