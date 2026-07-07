# Lesson03: Method를 이용하여 객체를 스스로 동작하게 만들기

이 Lesson은 객체 안에 메서드를 작성하고, `main()`에서 객체를 생성한 뒤 메서드를 호출하는 흐름을 익히는 수업이다.

Lesson02에서는 객체가 값을 담는 방법을 연습했다. Lesson03에서는 객체가 자기 값을 이용해 스스로 동작하게 만든다.

수업 비율:

- 이론: 약 20분
- 실습: 약 100분

## 1. 학습 목표

이 Lesson을 마치면 다음을 할 수 있다.

- 클래스 안에 메서드를 직접 작성할 수 있다.
- 객체를 생성한 뒤 객체의 메서드를 호출할 수 있다.
- `Book` 객체에 `printInfo()`, `isAvailable()` 메서드를 만들 수 있다.
- `Product` 객체에 `printInfo()`, `changePrice()`, `changeStock()` 메서드를 만들 수 있다.
- getter로 값을 꺼내 처리하는 방식과 객체 내부 메서드가 처리하는 방식의 차이를 설명할 수 있다.
- Spring Boot의 Service 메서드가 객체의 동작을 모아놓은 것이라는 감을 잡을 수 있다.
- ERP의 `ProductService`가 여러 업무 메서드를 가진 객체라는 점을 이해할 수 있다.

## 2. 선수지식

Lesson02에서 다음 내용을 경험했다고 가정한다.

- `Book`, `Member`, `Product` 클래스를 만들었다.
- `new Book()`으로 객체를 생성했다.
- 필드, getter, setter를 작성했다.
- 생성자로 객체에 초기값을 넣었다.
- `main()`에서 객체 값을 출력했다.

이번 Lesson에서는 조건문을 깊게 설명하지 않는다. `stock > 0`처럼 필요한 정도만 사용한다.

## 3. 왜 배우는가

객체는 값만 담는 상자가 아니다.

Lesson02의 `Book` 객체는 값을 담았다.

```java
Book book = new Book("Java Start", "JBMC", 25000, 3);
```

하지만 실제 업무에서는 객체가 자기 상태를 이용해 행동해야 한다.

- 도서가 대여 가능한지 판단한다.
- 상품 정보를 출력한다.
- 상품 가격을 변경한다.
- 상품 재고를 변경한다.
- 주문 가능 여부를 판단한다.

이런 행동을 메서드로 만든다.

```java
book.printInfo();
book.isAvailable();
product.changeStock(5);
```

Spring Boot와 ERP에서도 마찬가지다. `ProductService`는 상품 등록, 상품 수정, 재고 변경 같은 메서드를 모아놓은 객체다.

## 4. 핵심 개념

이번 Lesson에서 필요한 개념만 짧게 정리한다.

| 개념 | 오늘의 이해 |
| --- | --- |
| 메서드 | 객체가 할 수 있는 동작 |
| 메서드 호출 | 객체에게 일을 시키는 것 |
| 반환값 | 메서드가 실행 후 돌려주는 값 |
| `void` | 돌려주는 값이 없다는 뜻 |
| `boolean` 반환 | 참/거짓 판단 결과를 돌려주는 방식 |
| 상태 변경 | 객체 안의 필드 값이 바뀌는 것 |
| Service 메서드 | Spring Boot에서 업무 동작을 표현하는 메서드 |

오늘은 메서드 문법을 길게 설명하지 않는다.

오늘의 핵심 흐름은 이것이다.

1. 객체를 만든다.
2. 객체 안에 메서드를 만든다.
3. `main()`에서 객체의 메서드를 호출한다.
4. 객체의 상태가 바뀌는지 출력으로 확인한다.

## 5. IntelliJ 실습

전체 실습은 약 100분을 기준으로 진행한다. 각 실습은 반드시 직접 입력하고 실행한다.

### 실습 1: Lesson03App 만들기

예상 시간: 5분

IntelliJ에서 `Lesson03App` 클래스를 만든다.

```java
public class Lesson03App {
    public static void main(String[] args) {
        System.out.println("Lesson03: Object Method");
    }
}
```

실행해서 콘솔에 문장이 출력되는지 확인한다.

### 실습 2: Book 클래스 준비하기

예상 시간: 15분

`Book` 클래스를 만든다.

```java
public class Book {
    private String title;
    private String author;
    private int price;
    private int stock;

    public Book() {
    }

    public Book(String title, String author, int price, int stock) {
        this.title = title;
        this.author = author;
        this.price = price;
        this.stock = stock;
    }

    public String getTitle() {
        return title;
    }

    public int getStock() {
        return stock;
    }
}
```

오늘은 getter/setter 전체를 반복해서 작성하지 않는다. 메서드 호출 감각에 집중한다.

`Lesson03App`에서 객체를 생성한다.

```java
Book book = new Book("Java Start", "JBMC", 25000, 3);

System.out.println(book.getTitle());
System.out.println(book.getStock());
```

확인:

- [ ] `Book` 클래스를 만들었다.
- [ ] 생성자로 객체를 만들었다.
- [ ] getter로 값을 출력했다.

### 실습 3: Book에 printInfo() 만들기

예상 시간: 15분

`Book` 클래스 안에 `printInfo()` 메서드를 추가한다.

```java
public void printInfo() {
    System.out.println("도서명: " + title);
    System.out.println("저자: " + author);
    System.out.println("가격: " + price + "원");
    System.out.println("재고: " + stock + "권");
    System.out.println("--------------------");
}
```

`main()`에서 호출한다.

```java
Book book = new Book("Java Start", "JBMC", 25000, 3);

book.printInfo();
```

중요한 변화:

이전에는 `main()`에서 getter를 여러 번 호출했다.

```java
System.out.println(book.getTitle());
System.out.println(book.getStock());
```

이제는 객체에게 직접 출력하라고 시킨다.

```java
book.printInfo();
```

객체가 자기 정보를 스스로 출력하는 첫 번째 경험이다.

### 실습 4: Book에 isAvailable() 만들기

예상 시간: 15분

`Book` 클래스에 대여 가능 여부를 판단하는 메서드를 추가한다.

```java
public boolean isAvailable() {
    return stock > 0;
}
```

`main()`에서 호출한다.

```java
Book book = new Book("Java Start", "JBMC", 25000, 3);

book.printInfo();
System.out.println("대여 가능 여부: " + book.isAvailable());
```

재고가 0인 도서도 만들어본다.

```java
Book emptyBook = new Book("Spring Boot Basic", "JBMC", 35000, 0);

emptyBook.printInfo();
System.out.println("대여 가능 여부: " + emptyBook.isAvailable());
```

조건문 설명은 여기서 깊게 하지 않는다.

`stock > 0`은 "재고가 있으면 true, 없으면 false" 정도로 이해하고 넘어간다.

### 실습 5: getter 방식과 객체 내부 메서드 방식 비교

예상 시간: 10분

getter를 사용하는 방식:

```java
if (book.getStock() > 0) {
    System.out.println("대여 가능");
} else {
    System.out.println("대여 불가");
}
```

객체 내부 메서드를 사용하는 방식:

```java
if (book.isAvailable()) {
    System.out.println("대여 가능");
} else {
    System.out.println("대여 불가");
}
```

차이:

- getter 방식은 `main()`이 객체의 값을 꺼내서 판단한다.
- 메서드 방식은 객체가 자기 상태를 이용해 판단 결과를 알려준다.

오늘은 두 방식을 모두 써본다. 하지만 ERP 코드가 커질수록 "객체가 자기 일을 하게 만드는 방식"이 더 읽기 쉬워진다.

### 실습 6: Product 클래스 만들기

예상 시간: 15분

`Product` 클래스를 만든다.

```java
public class Product {
    private String productName;
    private int price;
    private int stock;

    public Product(String productName, int price, int stock) {
        this.productName = productName;
        this.price = price;
        this.stock = stock;
    }

    public void printInfo() {
        System.out.println("상품명: " + productName);
        System.out.println("가격: " + price + "원");
        System.out.println("재고: " + stock + "개");
        System.out.println("--------------------");
    }
}
```

`main()`에서 객체를 만들고 메서드를 호출한다.

```java
Product product = new Product("키보드", 45000, 10);

product.printInfo();
```

### 실습 7: Product에 changePrice() 만들기

예상 시간: 10분

`Product` 클래스에 가격을 바꾸는 메서드를 추가한다.

```java
public void changePrice(int newPrice) {
    price = newPrice;
}
```

`main()`에서 호출한다.

```java
Product product = new Product("키보드", 45000, 10);

product.printInfo();
product.changePrice(40000);
product.printInfo();
```

확인:

- [ ] 첫 출력은 45000원이다.
- [ ] `changePrice(40000)` 호출 후 40000원으로 바뀐다.

### 실습 8: Product에 changeStock() 만들기

예상 시간: 15분

`Product` 클래스에 재고를 바꾸는 메서드를 추가한다.

```java
public void changeStock(int newStock) {
    stock = newStock;
}
```

재고가 있는지 확인하는 메서드도 추가한다.

```java
public boolean isAvailable() {
    return stock > 0;
}
```

`main()`에서 호출한다.

```java
Product product = new Product("키보드", 45000, 10);

product.printInfo();
System.out.println("판매 가능 여부: " + product.isAvailable());

product.changeStock(0);

product.printInfo();
System.out.println("판매 가능 여부: " + product.isAvailable());
```

여기서 중요한 것은 조건문이 아니다.

중요한 것은 메서드를 호출하면 객체의 상태가 바뀌고, 바뀐 상태를 다시 출력할 수 있다는 점이다.

### 실습 9: 객체 메서드 호출 흐름 정리

예상 시간: 5분

오늘 작성한 호출 흐름을 다시 읽어본다.

```java
product.printInfo();
product.changePrice(40000);
product.changeStock(0);
product.printInfo();
```

이 코드는 이렇게 읽는다.

1. 상품 정보를 출력한다.
2. 상품 가격을 변경한다.
3. 상품 재고를 변경한다.
4. 변경된 상품 정보를 다시 출력한다.

객체는 값을 담고, 메서드는 그 값을 이용해 동작한다.

## 6. 예제 코드

Lesson03의 핵심 예제는 `Book`과 `Product`에 메서드를 추가하는 것이다.

### Book

```java
public class Book {
    private String title;
    private String author;
    private int price;
    private int stock;

    public Book(String title, String author, int price, int stock) {
        this.title = title;
        this.author = author;
        this.price = price;
        this.stock = stock;
    }

    public void printInfo() {
        System.out.println("도서명: " + title);
        System.out.println("저자: " + author);
        System.out.println("가격: " + price + "원");
        System.out.println("재고: " + stock + "권");
        System.out.println("--------------------");
    }

    public boolean isAvailable() {
        return stock > 0;
    }
}
```

### Product

```java
public class Product {
    private String productName;
    private int price;
    private int stock;

    public Product(String productName, int price, int stock) {
        this.productName = productName;
        this.price = price;
        this.stock = stock;
    }

    public void printInfo() {
        System.out.println("상품명: " + productName);
        System.out.println("가격: " + price + "원");
        System.out.println("재고: " + stock + "개");
        System.out.println("--------------------");
    }

    public boolean isAvailable() {
        return stock > 0;
    }

    public void changePrice(int newPrice) {
        price = newPrice;
    }

    public void changeStock(int newStock) {
        stock = newStock;
    }
}
```

### Lesson03App

```java
public class Lesson03App {
    public static void main(String[] args) {
        Book book = new Book("Java Start", "JBMC", 25000, 3);
        book.printInfo();
        System.out.println("대여 가능 여부: " + book.isAvailable());

        Product product = new Product("키보드", 45000, 10);
        product.printInfo();
        System.out.println("판매 가능 여부: " + product.isAvailable());

        product.changePrice(40000);
        product.changeStock(0);

        product.printInfo();
        System.out.println("판매 가능 여부: " + product.isAvailable());
    }
}
```

## 7. 코드 설명

`printInfo()`는 객체가 자기 정보를 출력하는 메서드다.

`isAvailable()`은 객체가 자기 재고를 보고 사용 가능 여부를 알려주는 메서드다.

`changePrice(int newPrice)`는 상품 가격을 바꾸는 메서드다.

`changeStock(int newStock)`은 상품 재고를 바꾸는 메서드다.

getter를 사용하면 외부 코드가 객체의 값을 꺼내서 판단한다.

```java
book.getStock() > 0
```

객체 내부 메서드를 사용하면 객체가 판단 결과를 알려준다.

```java
book.isAvailable()
```

이번 Lesson에서는 두 방식을 비교만 한다. 어느 방식이 항상 정답이라고 외우지 않는다. 중요한 것은 객체 안에 동작을 넣을 수 있다는 감각이다.

## 8. Spring Boot 연결

Spring Boot에서 Service는 메서드를 모아놓은 객체다.

예를 들어 상품 업무를 처리하는 `ProductService`는 다음과 같은 메서드를 가질 수 있다.

```java
public class ProductService {
    public void changePrice() {
    }

    public void changeStock() {
    }

    public boolean isAvailable() {
        return true;
    }
}
```

오늘은 `Product` 객체 안에 메서드를 만들었다.

나중에는 상품 업무가 커지면서 이런 동작들이 `ProductService`로 이동하거나, `Product`와 `ProductService`가 함께 역할을 나누게 된다.

즉, 오늘 배운 객체 메서드 호출 감각은 Spring Boot Service 메서드를 이해하기 위한 준비다.

## 9. ERP 연결

ERP의 상품 업무는 단순히 상품명을 저장하는 것으로 끝나지 않는다.

상품에는 행동이 필요하다.

- 가격 변경
- 재고 증가
- 재고 감소
- 판매 가능 여부 확인
- 판매 중지 처리

이런 업무 동작은 결국 메서드로 표현된다.

ERP 프로젝트에서 `ProductService`는 여러 메서드를 모아놓은 객체가 된다.

```java
public class ProductService {
    public void discount() {
    }

    public void increaseStock() {
    }

    public void decreaseStock() {
    }
}
```

오늘 만든 `Product.changeStock()`은 나중에 `ProductService.increaseStock()`, `ProductService.decreaseStock()` 같은 메서드를 이해하기 위한 작은 출발점이다.

## 10. 미션

### 미션: 객체의 상태가 바뀌는 것을 메서드로 확인하기

예상 시간: 30분

이번 미션은 `Book`과 `Product` 객체에 직접 메서드를 추가하고, `main()`에서 호출하여 객체 상태가 바뀌는 것을 출력으로 확인하는 것이다.

### 미션 1: Book 객체에 borrow(), returnBook() 만들기

`Book` 클래스에 다음 메서드를 추가한다.

- `borrow()`
- `returnBook()`

요구사항:

- `borrow()`는 재고를 1 줄인다.
- `returnBook()`은 재고를 1 늘린다.
- `stock`이 0이면 `borrow()`에서 재고를 줄이지 않는다.
- `printInfo()`로 변경 전과 변경 후를 출력한다.

예상 호출 흐름:

```java
Book book = new Book("Java Start", "JBMC", 25000, 1);

book.printInfo();
book.borrow();
book.printInfo();
book.borrow();
book.printInfo();
book.returnBook();
book.printInfo();
```

### 미션 2: Product 객체에 discount(), increaseStock(), decreaseStock() 만들기

`Product` 클래스에 다음 메서드를 추가한다.

- `discount(int amount)`
- `increaseStock(int amount)`
- `decreaseStock(int amount)`

요구사항:

- `discount()`는 가격을 전달받은 금액만큼 낮춘다.
- `increaseStock()`은 재고를 전달받은 수량만큼 늘린다.
- `decreaseStock()`은 재고를 전달받은 수량만큼 줄인다.
- 재고가 부족하면 `decreaseStock()`에서 재고를 음수로 만들지 않는다.
- `main()`에서 메서드를 호출하고 변경 전후를 출력한다.

예상 호출 흐름:

```java
Product product = new Product("모니터", 180000, 5);

product.printInfo();
product.discount(30000);
product.increaseStock(2);
product.decreaseStock(4);
product.printInfo();
```

추가 도전:

- 가격이 0보다 작아지지 않도록 처리한다.
- 재고가 부족할 때 `재고 부족` 메시지를 출력한다.

## 11. 체크리스트

- [ ] `Book` 클래스 안에 `printInfo()`를 작성했다.
- [ ] `Book` 클래스 안에 `isAvailable()`을 작성했다.
- [ ] `Product` 클래스 안에 `printInfo()`를 작성했다.
- [ ] `Product` 클래스 안에 `changePrice()`를 작성했다.
- [ ] `Product` 클래스 안에 `changeStock()`을 작성했다.
- [ ] `main()`에서 객체를 생성했다.
- [ ] `main()`에서 객체의 메서드를 호출했다.
- [ ] 메서드 호출 후 객체 상태가 바뀌는 것을 출력으로 확인했다.
- [ ] getter 방식과 객체 내부 메서드 방식의 차이를 설명할 수 있다.
- [ ] `ProductService`가 여러 메서드를 가진 객체라는 점을 이해했다.

## 12. 면접 질문

1. 객체 안에 메서드를 작성하는 이유는 무엇인가?
2. `book.printInfo()`는 어떤 의미인가?
3. `isAvailable()`처럼 `boolean`을 반환하는 메서드는 언제 사용할 수 있는가?
4. getter를 사용해 외부에서 판단하는 방식과 객체 내부 메서드로 판단하는 방식은 어떻게 다른가?
5. `changePrice(int newPrice)`는 객체의 어떤 값을 바꾸는가?
6. 메서드를 호출하면 객체의 상태가 바뀔 수 있다는 말은 무슨 뜻인가?
7. Spring Boot의 Service 메서드는 오늘 배운 메서드와 어떻게 연결되는가?
8. ERP의 `ProductService`에는 어떤 메서드가 들어갈 수 있는가?

## 13. 복습 문제

1. `Book` 클래스에 `printInfo()` 메서드를 작성하라.
2. `Book` 클래스에 `isAvailable()` 메서드를 작성하라.
3. `Product` 클래스에 `changePrice(int newPrice)` 메서드를 작성하라.
4. `Product` 클래스에 `changeStock(int newStock)` 메서드를 작성하라.
5. `main()`에서 `Product` 객체를 만들고 `changePrice()` 호출 전후를 출력하라.
6. getter 방식과 객체 내부 메서드 방식의 차이를 한 문장으로 설명하라.
7. `ProductService`가 여러 메서드를 모아놓은 객체라는 말을 예시와 함께 설명하라.

## 14. 다음 Lesson

오늘 반드시 기억해야 하는 것:

- 객체는 값만 담는 상자가 아니다.
- 객체 안에는 메서드를 넣을 수 있다.
- 메서드는 객체가 할 수 있는 동작이다.
- `book.printInfo()`는 `book` 객체에게 정보를 출력하라고 시키는 코드다.
- `book.isAvailable()`은 `book` 객체에게 대여 가능 여부를 물어보는 코드다.
- 메서드를 호출하면 객체의 상태가 바뀔 수 있다.
- Spring Boot의 Service도 결국 여러 메서드를 가진 객체다.
- ERP의 `ProductService`는 상품 업무 메서드를 모아놓은 객체다.

다음 Lesson에서 사용할 것:

- 객체를 생성하는 흐름
- 객체의 메서드를 호출하는 흐름
- 메서드가 객체 상태를 바꾸는 흐름
- `Product`의 가격과 재고를 메서드로 다루는 감각

다음 Lesson에서는 `Product` 객체를 중심으로 메서드 호출 전과 후의 상태를 출력하면서, 객체 내부 필드가 실제로 변경되는 과정을 더 집중적으로 연습한다.
