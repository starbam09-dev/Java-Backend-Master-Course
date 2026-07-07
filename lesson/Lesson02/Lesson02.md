# Lesson02: Class와 Object를 이용한 실제 객체 생성

이 Lesson은 Java의 객체지향 이론을 깊게 설명하는 시간이 아니다.

목표는 IntelliJ에서 `Book`, `Member`, `Product` 클래스를 직접 만들고, `main()`에서 객체를 생성하고 출력하면서 잊어버린 객체지향 감각을 빠르게 복구하는 것이다.

수업 비율:

- 이론: 약 20분
- 실습: 약 100분

## 1. 학습 목표

이 Lesson을 마치면 다음을 할 수 있다.

- 클래스가 객체를 만들기 위한 설계도라는 것을 설명할 수 있다.
- `new` 키워드로 객체를 생성할 수 있다.
- 객체의 필드에 값을 저장하고 출력할 수 있다.
- getter와 setter를 직접 작성할 수 있다.
- IntelliJ 자동 생성 기능으로 getter와 setter를 만들 수 있다.
- 기본 생성자와 값을 받는 생성자를 직접 작성할 수 있다.
- `Book`에서 시작해 `Member`, `Product` 객체까지 직접 만들 수 있다.
- Spring Boot의 VO, DTO가 왜 클래스인지 이해할 수 있다.
- ERP의 `ProductVO`가 어떤 역할을 하는지 감을 잡을 수 있다.

## 2. 선수지식

Lesson01에서 다음 내용을 경험했다고 가정한다.

- IntelliJ에서 Java 클래스를 만들고 실행했다.
- `main()` 메서드에서 코드를 실행했다.
- `String`, `int`, `boolean` 변수를 사용했다.
- `if`, `else`로 간단한 판단을 했다.
- 메서드를 만들고 호출했다.

이번 Lesson에서 필요한 마음가짐은 하나다.

문법 이름을 완벽히 외우기보다, "클래스를 만들고 객체를 생성해서 값을 넣고 꺼낸다"는 흐름을 손으로 익힌다.

## 3. 왜 배우는가

Lesson01에서는 도서 정보를 변수로 따로 저장했다.

```java
String bookTitle = "Java Start";
String author = "JBMC";
int price = 25000;
int stock = 3;
```

도서가 한 권이면 괜찮다.

하지만 도서가 10권, 상품이 100개, 직원이 1,000명이 되면 변수만으로 관리하기 어렵다.

그래서 Java는 관련 있는 값을 하나의 객체로 묶는다.

```java
Book book = new Book();
```

ERP 시스템에서는 거의 모든 데이터가 객체로 움직인다.

- 도서 정보는 `Book`
- 회원 정보는 `Member`
- 상품 정보는 `Product`
- 직원 정보는 `Employee`
- 주문 정보는 `Order`

Spring Boot에서도 요청 데이터, 응답 데이터, DB 조회 결과를 클래스로 표현한다. 그래서 객체 생성 감각은 백엔드 개발의 출발점이다.

## 4. 핵심 개념

이번 Lesson에서는 필요한 개념만 짧게 정리한다.

| 개념 | 오늘의 이해 |
| --- | --- |
| 클래스 | 객체를 만들기 위한 설계도 |
| 객체 | 클래스로부터 만들어진 실제 데이터 묶음 |
| 필드 | 객체가 가지는 값 |
| `new` | 객체를 생성하는 키워드 |
| getter | 필드 값을 꺼내는 메서드 |
| setter | 필드 값을 넣거나 바꾸는 메서드 |
| 생성자 | 객체가 만들어질 때 실행되는 특별한 메서드 |
| VO | 값을 담아 전달하는 객체 |
| DTO | 계층 사이에서 데이터를 전달하는 객체 |

오늘은 캡슐화, 상속, 다형성을 깊게 다루지 않는다.

오늘 반드시 할 일은 세 가지다.

1. 클래스를 만든다.
2. 객체를 생성한다.
3. 객체에 값을 넣고 출력한다.

## 5. IntelliJ 실습

전체 실습은 약 100분을 기준으로 진행한다. 설명을 오래 듣기보다 코드를 직접 작성하면서 진행한다.

### 실습 1: Lesson02 프로젝트 준비

예상 시간: 5분

1. IntelliJ IDEA를 실행한다.
2. `Lesson01-Java-Recovery` 프로젝트를 그대로 사용하거나 새 Java 프로젝트를 만든다.
3. 새 프로젝트를 만든다면 이름은 `Lesson02-Class-Object`로 한다.
4. `src` 폴더 아래에 `Lesson02App` 클래스를 만든다.

```java
public class Lesson02App {
    public static void main(String[] args) {
        System.out.println("Lesson02: Class and Object");
    }
}
```

실행해서 콘솔에 문장이 출력되는지 확인한다.

### 실습 2: Book 클래스 만들기

예상 시간: 15분

`src` 폴더 아래에 `Book` 클래스를 만든다.

```java
public class Book {
    String title;
    String author;
    int price;
    int stock;
}
```

`Lesson02App`의 `main()`에서 객체를 생성한다.

```java
Book book = new Book();

book.title = "Java Start";
book.author = "JBMC";
book.price = 25000;
book.stock = 3;

System.out.println("도서명: " + book.title);
System.out.println("저자: " + book.author);
System.out.println("가격: " + book.price);
System.out.println("재고: " + book.stock);
```

확인:

- [ ] `Book` 클래스를 만들었다.
- [ ] `new Book()`으로 객체를 만들었다.
- [ ] 객체의 필드에 값을 넣었다.
- [ ] 객체의 필드 값을 출력했다.

여기까지가 객체 생성의 첫 감각이다.

### 실습 3: Book에 getter와 setter 직접 작성하기

예상 시간: 20분

이번에는 필드를 `private`으로 바꾸고 getter와 setter를 직접 작성한다.

```java
public class Book {
    private String title;
    private String author;
    private int price;
    private int stock;

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getAuthor() {
        return author;
    }

    public void setAuthor(String author) {
        this.author = author;
    }

    public int getPrice() {
        return price;
    }

    public void setPrice(int price) {
        this.price = price;
    }

    public int getStock() {
        return stock;
    }

    public void setStock(int stock) {
        this.stock = stock;
    }
}
```

`main()` 코드를 setter와 getter 방식으로 바꾼다.

```java
Book book = new Book();

book.setTitle("Java Start");
book.setAuthor("JBMC");
book.setPrice(25000);
book.setStock(3);

System.out.println("도서명: " + book.getTitle());
System.out.println("저자: " + book.getAuthor());
System.out.println("가격: " + book.getPrice());
System.out.println("재고: " + book.getStock());
```

기억할 것:

- setter는 값을 넣는다.
- getter는 값을 꺼낸다.
- `this.title`은 현재 객체의 `title` 필드를 의미한다.

### 실습 4: IntelliJ로 getter/setter 자동 생성하기

예상 시간: 10분

직접 한 번 작성했으니 이제 IntelliJ 자동 생성 기능을 사용한다.

1. `Book` 클래스에서 필드 아래 빈 줄을 클릭한다.
2. 마우스 오른쪽 버튼을 누른다.
3. `Generate`를 선택한다.
4. `Getter and Setter`를 선택한다.
5. 필요한 필드를 선택한다.
6. `OK`를 누른다.

단축키:

- Windows: `Alt + Insert`

주의:

자동 생성 기능은 편하지만, 처음에는 반드시 직접 한 번 써봐야 한다. 그래야 자동 생성된 코드가 무엇을 하는지 읽을 수 있다.

### 실습 5: Book 생성자 만들기

예상 시간: 20분

객체를 만든 뒤 setter를 여러 번 호출하는 방식은 길다.

```java
Book book = new Book();
book.setTitle("Java Start");
book.setAuthor("JBMC");
book.setPrice(25000);
book.setStock(3);
```

생성자를 만들면 객체를 만들 때 값을 한 번에 넣을 수 있다.

`Book` 클래스에 기본 생성자와 값을 받는 생성자를 추가한다.

```java
public Book() {
}

public Book(String title, String author, int price, int stock) {
    this.title = title;
    this.author = author;
    this.price = price;
    this.stock = stock;
}
```

`main()`에서 두 가지 방식으로 객체를 만들어본다.

```java
Book book1 = new Book();
book1.setTitle("Java Start");
book1.setAuthor("JBMC");
book1.setPrice(25000);
book1.setStock(3);

Book book2 = new Book("Spring Boot Basic", "JBMC", 35000, 0);
```

그리고 출력한다.

```java
System.out.println(book1.getTitle() + " / " + book1.getPrice());
System.out.println(book2.getTitle() + " / " + book2.getPrice());
```

오늘 반드시 기억해야 하는 생성자 감각:

- `new Book()`은 기본 생성자를 사용한다.
- `new Book("Spring Boot Basic", "JBMC", 35000, 0)`은 값을 받는 생성자를 사용한다.
- 생성자는 객체를 만들 때 초기값을 넣는 통로다.

### 실습 6: Member 클래스 만들기

예상 시간: 15분

이번에는 `Member` 클래스를 직접 만든다.

필드:

- `name`
- `email`
- `age`

```java
public class Member {
    private String name;
    private String email;
    private int age;

    public Member() {
    }

    public Member(String name, String email, int age) {
        this.name = name;
        this.email = email;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getEmail() {
        return email;
    }

    public void setEmail(String email) {
        this.email = email;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}
```

`main()`에서 객체를 생성한다.

```java
Member member = new Member("kim", "kim@example.com", 30);

System.out.println("회원명: " + member.getName());
System.out.println("이메일: " + member.getEmail());
System.out.println("나이: " + member.getAge());
```

직접 바꿔보기:

- 다른 회원을 하나 더 만든다.
- 기본 생성자와 setter 방식으로도 만들어본다.

### 실습 7: Product 클래스 만들기

예상 시간: 15분

마지막으로 ERP와 직접 연결되는 `Product` 클래스를 만든다.

필드:

- `productName`
- `price`
- `stock`
- `active`

```java
public class Product {
    private String productName;
    private int price;
    private int stock;
    private boolean active;

    public Product() {
    }

    public Product(String productName, int price, int stock, boolean active) {
        this.productName = productName;
        this.price = price;
        this.stock = stock;
        this.active = active;
    }

    public String getProductName() {
        return productName;
    }

    public void setProductName(String productName) {
        this.productName = productName;
    }

    public int getPrice() {
        return price;
    }

    public void setPrice(int price) {
        this.price = price;
    }

    public int getStock() {
        return stock;
    }

    public void setStock(int stock) {
        this.stock = stock;
    }

    public boolean isActive() {
        return active;
    }

    public void setActive(boolean active) {
        this.active = active;
    }
}
```

`main()`에서 객체를 만든다.

```java
Product product = new Product("키보드", 45000, 10, true);

System.out.println("상품명: " + product.getProductName());
System.out.println("가격: " + product.getPrice());
System.out.println("재고: " + product.getStock());
System.out.println("판매 여부: " + product.isActive());
```

중요:

`boolean` 필드의 getter는 보통 `getActive()`가 아니라 `isActive()` 형태로 만들 수 있다.

## 6. 예제 코드

Lesson02의 핵심 예제는 `Book` 클래스다.

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

    public void setTitle(String title) {
        this.title = title;
    }

    public String getAuthor() {
        return author;
    }

    public void setAuthor(String author) {
        this.author = author;
    }

    public int getPrice() {
        return price;
    }

    public void setPrice(int price) {
        this.price = price;
    }

    public int getStock() {
        return stock;
    }

    public void setStock(int stock) {
        this.stock = stock;
    }
}
```

`main()`에서 객체를 생성한다.

```java
public class Lesson02App {
    public static void main(String[] args) {
        Book book1 = new Book();
        book1.setTitle("Java Start");
        book1.setAuthor("JBMC");
        book1.setPrice(25000);
        book1.setStock(3);

        Book book2 = new Book("Spring Boot Basic", "JBMC", 35000, 0);

        System.out.println("도서명: " + book1.getTitle());
        System.out.println("가격: " + book1.getPrice());
        System.out.println("--------------------");
        System.out.println("도서명: " + book2.getTitle());
        System.out.println("가격: " + book2.getPrice());
    }
}
```

## 7. 코드 설명

`private String title;`은 외부에서 필드에 바로 접근하지 못하게 한다.

`setTitle("Java Start")`는 객체 안에 값을 넣는다.

`getTitle()`은 객체 안에 들어 있는 값을 꺼낸다.

`new Book()`은 기본 생성자로 객체를 만든다.

`new Book("Spring Boot Basic", "JBMC", 35000, 0)`은 값을 받는 생성자로 객체를 만든다.

`this.title = title;`은 매개변수로 받은 `title` 값을 현재 객체의 `title` 필드에 넣는 코드다.

오늘은 이 문장을 완벽히 설명하는 것보다 많이 보고 직접 작성하는 것이 더 중요하다.

## 8. Spring Boot 연결

Spring Boot에서는 데이터를 클래스로 자주 표현한다.

예를 들어 도서 등록 요청을 받는다면 이런 DTO를 만들 수 있다.

```java
public class BookCreateRequest {
    private String title;
    private String author;
    private int price;
}
```

상품 정보를 화면에 보내야 한다면 이런 DTO를 만들 수 있다.

```java
public class ProductResponse {
    private String productName;
    private int price;
    private int stock;
}
```

VO와 DTO가 어려운 특별한 문법은 아니다.

기본은 오늘 만든 `Book`, `Member`, `Product`와 같다.

- 필드가 있다.
- 생성자가 있다.
- getter와 setter가 있다.
- 객체를 생성해서 값을 담는다.

그래서 Class와 Object를 손으로 익히는 것이 Spring Boot를 배우기 전 꼭 필요하다.

## 9. ERP 연결

ERP 프로젝트에서는 상품 데이터를 자주 다룬다.

나중에 `ProductVO`는 다음과 비슷한 형태가 된다.

```java
public class ProductVO {
    private Long productId;
    private String productName;
    private int price;
    private int stock;
    private boolean active;
}
```

오늘 만든 `Product`는 `ProductVO`의 아주 초기 형태다.

```java
Product product = new Product("키보드", 45000, 10, true);
```

이 객체는 나중에 다음 흐름으로 이어진다.

- 상품 등록 화면
- 상품 등록 API
- `ProductVO`
- MyBatis Mapper
- Oracle `PRODUCT` 테이블
- 재고 관리
- 주문 가능 여부 판단

ERP에서는 데이터를 흩어진 변수로 관리하지 않는다. 업무 단위로 묶인 객체로 다룬다.

## 10. 미션

### 미션: Employee와 Product 객체 직접 만들기

예상 시간: 30분

이번 미션은 설명을 보지 않고 혼자 작성한다.

### 미션 1: Employee 클래스 작성

`Employee` 클래스를 만든다.

필드:

- `employeeName`
- `department`
- `salary`
- `active`

요구사항:

- 모든 필드는 `private`으로 만든다.
- 기본 생성자를 만든다.
- 모든 값을 받는 생성자를 만든다.
- getter와 setter를 만든다.
- `main()`에서 객체를 2개 만든다.
- 하나는 기본 생성자와 setter로 만든다.
- 하나는 값을 받는 생성자로 만든다.
- 두 객체의 값을 출력한다.

### 미션 2: Product 클래스 혼자 다시 작성

`Product` 클래스를 다시 작성한다.

필드:

- `productName`
- `price`
- `stock`
- `active`

요구사항:

- 기본 생성자를 만든다.
- 값을 받는 생성자를 만든다.
- getter와 setter를 만든다.
- 상품 객체를 2개 만든다.
- 객체 값을 출력한다.
- `stock`이 0보다 크면 `판매 가능`, 아니면 `품절`을 출력한다.

추가 도전:

- `price`가 100000원 이상이면 `고가 상품`을 출력한다.
- `active`가 `false`이면 `판매 중지 상품`을 출력한다.

## 11. 체크리스트

- [ ] `Book` 클래스를 직접 만들었다.
- [ ] `new Book()`으로 객체를 생성했다.
- [ ] 객체의 필드에 값을 저장했다.
- [ ] getter와 setter를 직접 작성했다.
- [ ] IntelliJ 자동 생성 기능으로 getter와 setter를 만들었다.
- [ ] 기본 생성자를 작성했다.
- [ ] 값을 받는 생성자를 작성했다.
- [ ] `Member` 객체를 만들고 출력했다.
- [ ] `Product` 객체를 만들고 출력했다.
- [ ] `Employee` 미션을 혼자 작성했다.
- [ ] `ProductVO`가 오늘 만든 `Product`와 연결된다는 것을 이해했다.

## 12. 면접 질문

1. 클래스와 객체의 차이는 무엇인가?
2. `new Book()`은 어떤 일을 하는가?
3. 필드를 `private`으로 만드는 이유는 무엇인가?
4. getter와 setter는 각각 어떤 역할을 하는가?
5. 생성자는 언제 실행되는가?
6. 기본 생성자와 값을 받는 생성자는 어떻게 다른가?
7. `this.title = title;`은 어떤 의미인가?
8. Spring Boot에서 DTO가 클래스인 이유는 무엇인가?
9. ERP에서 `ProductVO`는 어떤 데이터를 담을 수 있는가?

## 13. 복습 문제

1. `Book` 클래스에 `title`, `author`, `price`, `stock` 필드를 작성하라.
2. `Book book = new Book();` 코드의 의미를 설명하라.
3. `title` 필드의 getter와 setter를 직접 작성하라.
4. `Book(String title, String author, int price, int stock)` 생성자를 작성하라.
5. `Member` 객체를 생성하고 이름과 이메일을 출력하는 코드를 작성하라.
6. `Product` 객체를 생성하고 재고가 있으면 `판매 가능`을 출력하는 코드를 작성하라.
7. `ProductVO`가 ERP 프로젝트에서 필요한 이유를 한 문장으로 설명하라.

## 14. 다음 Lesson

오늘 반드시 기억해야 하는 것:

- 클래스는 객체를 만들기 위한 설계도다.
- 객체는 `new`로 생성한다.
- 필드는 객체가 가지는 값이다.
- getter는 값을 꺼낸다.
- setter는 값을 넣거나 바꾼다.
- 생성자는 객체가 만들어질 때 초기값을 넣는 통로다.
- Spring Boot의 VO, DTO도 결국 데이터를 담기 위한 클래스다.
- ERP의 `ProductVO`는 상품 업무 데이터를 담는 객체다.

다음 Lesson에서 사용할 것:

- `Book`, `Member`, `Product`처럼 여러 값을 하나로 묶는 감각
- getter와 setter를 통해 값을 넣고 꺼내는 감각
- 생성자로 객체를 초기화하는 감각
- `Product` 객체를 기준으로 재고와 가격을 판단하는 흐름

다음 Lesson에서는 객체 안에 메서드를 작성하고, 객체가 자기 상태를 이용해 스스로 동작하게 만든다.

특히 `Book`과 `Product` 객체에 `printInfo()`, `isAvailable()`, `changePrice()`, `changeStock()` 같은 메서드를 만들고 `main()`에서 직접 호출하는 연습으로 이어진다.
