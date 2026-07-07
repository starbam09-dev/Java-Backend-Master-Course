# Lesson04: 객체의 상태(State)를 메서드로 변경하기

이 Lesson은 객체 내부의 필드가 메서드 호출에 의해 실제로 변경되는 과정을 이해하는 수업이다.

Lesson03에서는 객체 안에 메서드를 만들고 호출했다. Lesson04에서는 한 걸음 더 들어가서, 메서드가 객체의 상태를 어떻게 바꾸는지 직접 확인한다.

수업 비율:

- 이론: 약 20분
- 실습: 약 100분

## 1. 학습 목표

이 Lesson을 마치면 다음을 할 수 있다.

- 객체의 상태가 필드 값이라는 것을 설명할 수 있다.
- 메서드 호출 전과 후의 객체 상태를 출력할 수 있다.
- `Product` 객체의 재고를 `increaseStock(int quantity)`로 증가시킬 수 있다.
- `Product` 객체의 재고를 `decreaseStock(int quantity)`로 감소시킬 수 있다.
- `Product` 객체의 가격을 `changePrice(int price)`로 변경할 수 있다.
- `activate()`, `deactivate()`로 판매 상태를 변경할 수 있다.
- getter와 setter를 남용하지 않는 이유를 간단히 설명할 수 있다.
- 객체가 자신의 데이터를 스스로 변경하는 것이 객체지향의 핵심임을 이해할 수 있다.
- Spring Boot의 Entity, VO, DTO, Service가 어떻게 연결되는지 큰 흐름을 잡을 수 있다.
- ERP의 재고 증가, 재고 감소, 판매 중지, 가격 변경 기능이 객체 메서드에서 출발한다는 것을 이해할 수 있다.

## 2. 선수지식

Lesson03에서 다음 내용을 경험했다고 가정한다.

- 객체 안에 메서드를 작성했다.
- `main()`에서 객체를 생성했다.
- `product.printInfo()`처럼 객체의 메서드를 호출했다.
- `changePrice()`, `changeStock()`처럼 메서드가 필드 값을 바꿀 수 있다는 것을 보았다.

이번 Lesson에서는 조건문을 깊게 설명하지 않는다. 재고가 음수가 되지 않게 막는 정도만 사용한다.

## 3. 왜 배우는가

ERP에서 상품은 단순한 데이터 묶음이 아니다.

상품은 계속 상태가 바뀐다.

- 입고되면 재고가 증가한다.
- 판매되면 재고가 감소한다.
- 행사 기간에는 가격이 바뀐다.
- 품절이나 단종이면 판매가 중지된다.
- 다시 판매하면 판매 상태가 활성화된다.

이런 변화는 결국 객체의 필드 값이 바뀌는 것이다.

```java
product.increaseStock(10);
product.decreaseStock(2);
product.changePrice(39000);
product.deactivate();
```

중요한 점은 외부에서 값을 마음대로 바꾸는 것이 아니라, 객체가 자신의 메서드를 통해 자기 상태를 관리하게 만드는 것이다.

이 감각이 나중에 Spring Boot의 Service, Entity, VO, DTO를 이해하는 바닥이 된다.

## 4. 핵심 개념

이번 Lesson에서 필요한 개념만 짧게 정리한다.

| 개념 | 오늘의 이해 |
| --- | --- |
| 상태 | 객체가 현재 가지고 있는 필드 값 |
| 상태 변경 | 메서드 호출로 필드 값이 바뀌는 것 |
| `increaseStock()` | 재고를 증가시키는 메서드 |
| `decreaseStock()` | 재고를 감소시키는 메서드 |
| `changePrice()` | 가격을 변경하는 메서드 |
| `activate()` | 판매 상태를 켜는 메서드 |
| `deactivate()` | 판매 상태를 끄는 메서드 |
| getter 남용 | 외부에서 값을 꺼내 모든 판단을 처리하는 습관 |
| setter 남용 | 외부에서 필드 값을 아무 규칙 없이 바꾸는 습관 |

오늘의 핵심 문장:

객체는 자신의 데이터를 스스로 관리해야 한다.

## 5. IntelliJ 실습

전체 실습은 약 100분을 기준으로 진행한다. 설명보다 직접 작성하고 실행하는 시간이 더 중요하다.

### 실습 1: Lesson04App 만들기

예상 시간: 5분

IntelliJ에서 `Lesson04App` 클래스를 만든다.

```java
public class Lesson04App {
    public static void main(String[] args) {
        System.out.println("Lesson04: Object State");
    }
}
```

실행해서 콘솔에 문장이 출력되는지 확인한다.

### 실습 2: Product 클래스 기본 형태 만들기

예상 시간: 15분

`Product` 클래스를 만든다.

```java
public class Product {
    private String productName;
    private int price;
    private int stock;
    private boolean active;

    public Product(String productName, int price, int stock, boolean active) {
        this.productName = productName;
        this.price = price;
        this.stock = stock;
        this.active = active;
    }

    public void printInfo() {
        System.out.println("상품명: " + productName);
        System.out.println("가격: " + price + "원");
        System.out.println("재고: " + stock + "개");
        System.out.println("판매 상태: " + active);
        System.out.println("--------------------");
    }
}
```

`Lesson04App`에서 객체를 생성하고 출력한다.

```java
Product product = new Product("키보드", 45000, 10, true);

product.printInfo();
```

확인:

- [ ] `Product` 클래스를 만들었다.
- [ ] 생성자로 객체를 만들었다.
- [ ] `printInfo()`로 현재 상태를 출력했다.

### 실습 3: increaseStock(int quantity) 만들기

예상 시간: 15분

`Product` 클래스에 재고 증가 메서드를 추가한다.

```java
public void increaseStock(int quantity) {
    stock = stock + quantity;
}
```

호출 전과 후를 출력한다.

```java
Product product = new Product("키보드", 45000, 10, true);

System.out.println("입고 전");
product.printInfo();

product.increaseStock(5);

System.out.println("입고 후");
product.printInfo();
```

확인:

- [ ] 처음 재고는 10개다.
- [ ] `increaseStock(5)` 호출 후 재고는 15개다.
- [ ] 메서드 호출 전과 후를 모두 출력했다.

### 실습 4: decreaseStock(int quantity) 만들기

예상 시간: 20분

`Product` 클래스에 재고 감소 메서드를 추가한다.

```java
public void decreaseStock(int quantity) {
    if (stock >= quantity) {
        stock = stock - quantity;
    } else {
        System.out.println("재고가 부족합니다.");
    }
}
```

호출 전과 후를 출력한다.

```java
Product product = new Product("키보드", 45000, 10, true);

System.out.println("판매 전");
product.printInfo();

product.decreaseStock(3);

System.out.println("판매 후");
product.printInfo();
```

재고 부족도 확인한다.

```java
product.decreaseStock(100);
product.printInfo();
```

이번 Lesson에서는 `if` 문법을 깊게 설명하지 않는다.

여기서는 "재고보다 큰 수량은 뺄 수 없다"는 업무 규칙을 표현하기 위해 필요한 만큼만 사용한다.

### 실습 5: changePrice(int price) 만들기

예상 시간: 10분

`Product` 클래스에 가격 변경 메서드를 추가한다.

```java
public void changePrice(int price) {
    this.price = price;
}
```

호출 전과 후를 출력한다.

```java
Product product = new Product("키보드", 45000, 10, true);

System.out.println("가격 변경 전");
product.printInfo();

product.changePrice(39000);

System.out.println("가격 변경 후");
product.printInfo();
```

중요:

`this.price`는 객체 내부의 필드다.

`price`는 메서드로 전달받은 새 가격이다.

### 실습 6: activate(), deactivate() 만들기

예상 시간: 15분

`Product` 클래스에 판매 상태 변경 메서드를 추가한다.

```java
public void activate() {
    active = true;
}

public void deactivate() {
    active = false;
}
```

호출 전과 후를 출력한다.

```java
Product product = new Product("키보드", 45000, 10, true);

System.out.println("판매 중지 전");
product.printInfo();

product.deactivate();

System.out.println("판매 중지 후");
product.printInfo();

product.activate();

System.out.println("판매 재개 후");
product.printInfo();
```

확인:

- [ ] `deactivate()` 호출 후 판매 상태가 `false`로 바뀐다.
- [ ] `activate()` 호출 후 판매 상태가 `true`로 바뀐다.

### 실습 7: getter/setter를 남용하지 않는 이유 보기

예상 시간: 10분

setter만 사용하면 외부에서 값을 마음대로 바꿀 수 있다.

```java
product.setStock(-100);
product.setPrice(-5000);
```

이 코드는 업무적으로 이상하다.

재고가 음수이거나 가격이 음수인 상품은 정상적인 상품이 아니다.

그래서 무조건 setter로 값을 바꾸기보다, 의미 있는 메서드를 만든다.

```java
product.increaseStock(10);
product.decreaseStock(3);
product.changePrice(39000);
product.deactivate();
```

차이:

- setter는 단순히 값을 바꾼다.
- 업무 메서드는 "왜 바꾸는지"를 이름으로 드러낸다.

객체가 자신의 데이터를 스스로 변경하게 만드는 것이 객체지향의 핵심이다.

### 실습 8: Book 보조 예제 만들기

예상 시간: 10분

이번에는 `Book` 객체로 같은 흐름을 짧게 확인한다.

```java
public class Book {
    private String title;
    private int stock;

    public Book(String title, int stock) {
        this.title = title;
        this.stock = stock;
    }

    public void printInfo() {
        System.out.println("도서명: " + title);
        System.out.println("재고: " + stock + "권");
        System.out.println("--------------------");
    }

    public void increaseStock(int quantity) {
        stock = stock + quantity;
    }

    public void decreaseStock(int quantity) {
        if (stock >= quantity) {
            stock = stock - quantity;
        } else {
            System.out.println("도서 재고가 부족합니다.");
        }
    }
}
```

`main()`에서 호출한다.

```java
Book book = new Book("Java Start", 2);

book.printInfo();
book.decreaseStock(1);
book.printInfo();
book.increaseStock(3);
book.printInfo();
```

Product와 Book은 다르지만 핵심은 같다.

객체가 자기 상태를 메서드로 바꾼다.

### 실습 9: 전체 흐름 한 번에 실행하기

예상 시간: 10분

마지막으로 `Product` 객체의 상태 변경 흐름을 한 번에 실행한다.

```java
Product product = new Product("키보드", 45000, 10, true);

product.printInfo();
product.increaseStock(5);
product.printInfo();
product.decreaseStock(3);
product.printInfo();
product.changePrice(39000);
product.printInfo();
product.deactivate();
product.printInfo();
product.activate();
product.printInfo();
```

출력 결과에서 가격, 재고, 판매 상태가 실제로 바뀌는지 확인한다.

## 6. 예제 코드

Lesson04의 핵심 예제는 `Product` 객체가 자신의 상태를 직접 변경하는 코드다.

```java
public class Product {
    private String productName;
    private int price;
    private int stock;
    private boolean active;

    public Product(String productName, int price, int stock, boolean active) {
        this.productName = productName;
        this.price = price;
        this.stock = stock;
        this.active = active;
    }

    public void printInfo() {
        System.out.println("상품명: " + productName);
        System.out.println("가격: " + price + "원");
        System.out.println("재고: " + stock + "개");
        System.out.println("판매 상태: " + active);
        System.out.println("--------------------");
    }

    public void increaseStock(int quantity) {
        stock = stock + quantity;
    }

    public void decreaseStock(int quantity) {
        if (stock >= quantity) {
            stock = stock - quantity;
        } else {
            System.out.println("재고가 부족합니다.");
        }
    }

    public void changePrice(int price) {
        this.price = price;
    }

    public void activate() {
        active = true;
    }

    public void deactivate() {
        active = false;
    }
}
```

`main()`에서 호출한다.

```java
public class Lesson04App {
    public static void main(String[] args) {
        Product product = new Product("키보드", 45000, 10, true);

        product.printInfo();

        product.increaseStock(5);
        product.printInfo();

        product.decreaseStock(3);
        product.printInfo();

        product.changePrice(39000);
        product.printInfo();

        product.deactivate();
        product.printInfo();

        product.activate();
        product.printInfo();
    }
}
```

## 7. 코드 설명

`stock = stock + quantity;`는 현재 재고에 전달받은 수량을 더한다.

`stock = stock - quantity;`는 현재 재고에서 전달받은 수량을 뺀다.

`this.price = price;`는 새 가격을 객체 내부의 `price` 필드에 저장한다.

`active = false;`는 판매 상태를 중지 상태로 바꾼다.

`active = true;`는 판매 상태를 다시 활성 상태로 바꾼다.

중요한 것은 메서드 이름이다.

`setStock(15)`보다 `increaseStock(5)`가 더 업무적으로 읽기 쉽다.

`setActive(false)`보다 `deactivate()`가 더 명확하다.

메서드 이름이 업무 의도를 드러내면 코드를 읽는 사람이 "왜 값이 바뀌는지"를 더 쉽게 이해한다.

## 8. Spring Boot 연결

Spring Boot에서는 객체 역할이 더 분리된다.

아주 단순하게 보면 다음과 같다.

- Entity: DB에 저장되는 핵심 데이터 객체
- VO: 값을 표현하거나 전달하는 객체
- DTO: 요청과 응답 데이터를 전달하는 객체
- Service: 업무 메서드를 모아놓은 객체

예를 들어 상품 재고를 늘리는 기능은 나중에 이런 흐름으로 커진다.

```java
public class ProductService {
    public void increaseStock(Long productId, int quantity) {
        // 상품 조회
        // 재고 증가
        // 저장
    }
}
```

오늘은 DB도 없고 Spring Boot도 없다.

하지만 핵심은 같다.

상품 상태를 바꾸는 업무는 결국 메서드로 표현된다.

## 9. ERP 연결

ERP에서 상품 관리는 상태 변경의 연속이다.

오늘 만든 메서드는 ERP 기능의 작은 형태다.

| 오늘의 메서드 | ERP 기능 |
| --- | --- |
| `increaseStock()` | 입고 처리 |
| `decreaseStock()` | 판매 또는 출고 처리 |
| `changePrice()` | 가격 변경 |
| `deactivate()` | 판매 중지 |
| `activate()` | 판매 재개 |

나중에 ERP 프로젝트에서는 이 기능들이 더 복잡해진다.

- 입고 이력 저장
- 출고 이력 저장
- 재고 부족 검증
- 판매 중지 상품 주문 차단
- 가격 변경 이력 관리

하지만 시작점은 지금과 같다.

객체의 상태를 메서드로 변경한다.

## 10. 미션

### 미션: Product 상태 변경 기능 직접 구현하기

예상 시간: 30분

다음 기능을 `Product` 객체에 직접 구현한다.

- 입고: `receive(int quantity)`
- 판매: `sell(int quantity)`
- 가격 할인: `discount(int amount)`
- 판매 종료: `stopSelling()`
- 판매 재개: `startSelling()`

요구사항:

- `Product` 클래스에 `productName`, `price`, `stock`, `active` 필드를 만든다.
- 생성자로 초기값을 넣는다.
- `printInfo()`로 현재 상태를 출력한다.
- `receive()`는 재고를 증가시킨다.
- `sell()`은 재고를 감소시킨다.
- `discount()`는 가격을 감소시킨다.
- `stopSelling()`은 `active`를 `false`로 바꾼다.
- `startSelling()`은 `active`를 `true`로 바꾼다.
- 각 메서드 호출 전과 후에 `printInfo()`를 호출한다.

예상 호출 흐름:

```java
Product product = new Product("모니터", 180000, 5, true);

product.printInfo();
product.receive(10);
product.printInfo();
product.sell(3);
product.printInfo();
product.discount(20000);
product.printInfo();
product.stopSelling();
product.printInfo();
product.startSelling();
product.printInfo();
```

추가 도전:

- `sell()`에서 재고가 부족하면 재고를 줄이지 않는다.
- `discount()`에서 가격이 0보다 작아지지 않도록 한다.
- 판매 중지 상태에서는 `sell()`이 실행되지 않도록 한다.

## 11. 체크리스트

- [ ] `Product` 클래스를 만들었다.
- [ ] `printInfo()`로 객체 상태를 출력했다.
- [ ] `increaseStock(int quantity)`를 구현했다.
- [ ] `decreaseStock(int quantity)`를 구현했다.
- [ ] `changePrice(int price)`를 구현했다.
- [ ] `activate()`를 구현했다.
- [ ] `deactivate()`를 구현했다.
- [ ] 메서드 호출 전과 후의 상태를 출력했다.
- [ ] setter보다 업무 메서드가 더 명확한 이유를 설명할 수 있다.
- [ ] 객체가 자신의 상태를 스스로 관리한다는 말을 설명할 수 있다.
- [ ] ERP의 입고, 판매, 가격 변경, 판매 중지가 오늘의 메서드와 연결된다는 것을 이해했다.

## 12. 면접 질문

1. 객체의 상태란 무엇인가?
2. 메서드 호출로 객체의 상태가 바뀐다는 말은 무엇인가?
3. `increaseStock(int quantity)`는 어떤 필드를 변경하는가?
4. `decreaseStock(int quantity)`에서 재고 부족을 확인하는 이유는 무엇인가?
5. `changePrice(int price)`에서 `this.price = price;`는 어떤 의미인가?
6. `activate()`와 `deactivate()`는 어떤 상태를 변경하는가?
7. setter를 남용하면 어떤 문제가 생길 수 있는가?
8. Spring Boot에서 Service는 어떤 역할을 하는가?
9. ERP에서 재고 증가와 재고 감소는 어떤 업무와 연결되는가?

## 13. 복습 문제

1. `Product` 클래스에 `productName`, `price`, `stock`, `active` 필드를 작성하라.
2. `printInfo()` 메서드를 작성하라.
3. `increaseStock(int quantity)` 메서드를 작성하라.
4. `decreaseStock(int quantity)` 메서드를 작성하라.
5. `changePrice(int price)` 메서드를 작성하라.
6. `activate()`, `deactivate()` 메서드를 작성하라.
7. `main()`에서 각 메서드 호출 전과 후의 상태를 출력하라.
8. `setStock()`보다 `increaseStock()`이 더 읽기 좋은 이유를 설명하라.

## 14. 다음 Lesson

오늘 반드시 기억해야 하는 것:

- 객체의 상태는 객체 내부의 필드 값이다.
- 메서드는 객체의 상태를 변경할 수 있다.
- 메서드 호출 전과 후를 출력하면 상태 변화를 확인할 수 있다.
- 객체가 자신의 데이터를 스스로 변경하는 것이 객체지향의 핵심이다.
- setter를 아무 곳에서나 사용하면 업무 규칙이 흩어진다.
- `increaseStock()`, `decreaseStock()`, `changePrice()` 같은 이름은 업무 의도를 드러낸다.

오늘 실무에서 사용되는 부분:

- 입고 처리는 재고 증가 메서드와 연결된다.
- 판매 또는 출고 처리는 재고 감소 메서드와 연결된다.
- 판매 중지는 상태 변경 메서드와 연결된다.
- 가격 변경은 가격 변경 메서드와 연결된다.
- Spring Boot의 Service는 이런 업무 메서드를 모아놓는 객체다.

다음 Lesson에서 사용할 개념:

- 객체 상태를 변경하는 메서드
- 상태 변경 전후를 확인하는 출력 흐름
- 재고 부족 같은 간단한 업무 규칙
- Product 객체를 중심으로 여러 업무 동작을 분리하는 감각

다음 Lesson에서는 여러 객체를 만들고, 같은 메서드를 여러 객체에 호출하면서 객체마다 상태가 따로 관리된다는 점을 확인한다.
