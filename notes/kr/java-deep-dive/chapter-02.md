---
layout: article
title: 2. 자바 인터페이스 완전 정복
permalink: /notes/kr/java-deep-dive/chapter-02
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: Java 심화 과정 강의 노트, 인터페이스 개념과 활용 방법을 다룹니다.
keywords: "Java, 인터페이스, 심화 과정, 데이터 처리, 프로그래밍"
---

<style>
    /* 색상 활용 규칙
      빨강: 주의, 경고, 위험 (덮어쓰기, 에러 등)
      파랑: 핵심 개념, 주요 기능 (모드, with 구문 등)
      초록: 안전한 대안, 긍정적 결과 (추가 모드, 정답 보기 등)
      노랑: 코드 요소 (함수명, 메서드명 등)
    */
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=Java%20DeepDive&reversal=false&textBg=false)

>앞 장에서 **상속**과 **다형성**을 배웠습니다.
>이번 장에서는 다형성을 더욱 유연하게 만들어주는 **추상 클래스**와 **인터페이스**를 알아봅니다.

## 1. 추상 클래스(Abstract Class)

### 추상 클래스란?
<span class="blue-text">미완성 설계도</span>라고 생각하면 쉽습니다. 직접 객체를 만들 수 없고, <span class="blue-text">자식 클래스가 반드시 완성해야 하는 메서드</span>를 포함하는 클래스입니다.

* <code class="yellow-code">abstract</code> 키워드를 사용하여 선언
* <span class="red-text">직접 객체 생성 불가</span> (`new 추상클래스()` 불가능)
* 일반 메서드와 추상 메서드를 함께 가질 수 있음

### 추상 메서드
<span class="blue-text">본문(중괄호 `{}`)이 없는 메서드</span>입니다. 자식 클래스에서 <span class="red-text">반드시 오버라이딩</span>해야 합니다.

```java
// 추상 클래스 선언
abstract class Animal {
    String name;

    // 일반 메서드 - 본문이 있음
    void breathe() {
        System.out.println(name + "이(가) 숨을 쉽니다.");
    }

    // 추상 메서드 - 본문이 없음!
    abstract void sound();
}
```

왜 `sound()`에 본문이 없을까요? 동물마다 소리가 다르기 때문입니다. 강아지는 "멍멍", 고양이는 "야옹"처럼요. 그래서 **자식 클래스가 각자 구현**하도록 비워둔 것입니다.

```java
class Dog extends Animal {
    Dog(String name) { this.name = name; }

    @Override
    void sound() {  // 반드시 구현해야 함!
        System.out.println("멍멍!");
    }
}

class Cat extends Animal {
    Cat(String name) { this.name = name; }

    @Override
    void sound() {  // 반드시 구현해야 함!
        System.out.println("야옹~");
    }
}

public class Main {
    public static void main(String[] args) {
        // Animal a = new Animal();  // 추상 클래스는 객체 생성 불가!
        Animal dog = new Dog("바둑이");
        Animal cat = new Cat("나비");

        dog.sound();    // 멍멍!
        cat.sound();    // 야옹~
        dog.breathe();  // 바둑이이(가) 숨을 쉽니다.
    }
}
```

### 문제 1: 추상 클래스 기초 연습
> `Shape`(도형) 추상 클래스를 만들고, `Circle`과 `Rectangle` 클래스에서 넓이를 계산하는 메서드를 구현하세요.
>
> **조건 및 힌트**
> 1. `Shape` 클래스에 추상 메서드 `area()`를 선언하세요.
> 2. `Circle`은 반지름, `Rectangle`은 가로와 세로를 필드로 갖습니다.
> 3. 각 클래스에서 `area()`를 오버라이딩하여 넓이를 출력하세요.

<details>
  <summary><span class="green-bold">정답 보기</span></summary>

  <pre><code class="language-java">
    abstract class Shape {
        abstract void area();
    }

    class Circle extends Shape {
        double radius;

        Circle(double radius) {
            this.radius = radius;
        }

        @Override
        void area() {
            double result = Math.PI * radius * radius;
            System.out.println("원의 넓이: " + result);
        }
    }

    class Rectangle extends Shape {
        double width, height;

        Rectangle(double width, double height) {
            this.width = width;
            this.height = height;
        }

        @Override
        void area() {
            System.out.println("사각형의 넓이: " + (width * height));
        }
    }

    public class Main {
        public static void main(String[] args) {
            Shape c = new Circle(5);
            Shape r = new Rectangle(3, 4);

            c.area();  // 원의 넓이: 78.539...
            r.area();  // 사각형의 넓이: 12.0
        }
    }
  </code></pre>
</details>

## 2. 인터페이스(Interface)란?

### 인터페이스 개념
인터페이스는 <span class="blue-text">클래스가 지켜야 할 약속(규약)</span>입니다.

추상 클래스보다 더 엄격한 규칙을 가지며, <span class="blue-text">"무엇을 할 수 있는가"</span>를 정의합니다.

쉽게 비유하면 이렇습니다.
* **추상 클래스** = 미완성 설계도 (일부는 완성, 일부는 미완성)
* **인터페이스** = 자격증 (이 자격이 있으면 이것을 할 수 있다!)

예를 들어, "수영 자격증"이 있으면 수영을 할 수 있습니다. 사람이든 로봇이든 상관없이, 수영 자격증(인터페이스)을 가지면 `swim()` 능력을 보장하는 것입니다.

### 인터페이스 선언

```java
interface Swimmable {
    void swim();  // 추상 메서드 (abstract 생략 가능)
}
```

인터페이스의 특징을 정리하면 다음과 같습니다.

* <code class="yellow-code">interface</code> 키워드로 선언
* 모든 메서드는 기본적으로 <span class="blue-text">public abstract</span> (생략 가능)
* 모든 필드는 기본적으로 <span class="blue-text">public static final</span> (상수만 가능)
* <span class="red-text">생성자를 가질 수 없음</span> → 직접 객체 생성 불가

## 3. 인터페이스 구현

### implements 키워드
클래스가 인터페이스를 구현할 때 <code class="yellow-code">implements</code> 키워드를 사용합니다.

```java
interface Flyable {
    void fly();
}

interface Swimmable {
    void swim();
}

class Duck implements Flyable, Swimmable {
    @Override
    public void fly() {
        System.out.println("오리가 날아갑니다!");
    }

    @Override
    public void swim() {
        System.out.println("오리가 수영합니다!");
    }
}
```

여기서 중요한 점이 있습니다. 자바는 <span class="red-text">클래스의 다중 상속을 허용하지 않습니다.</span>

```java
// 불가능! 자바는 클래스 다중 상속을 지원하지 않는다.
class Duck extends Bird, Fish { }
```

하지만 <span class="green-text">인터페이스는 여러 개를 동시에 구현</span>할 수 있습니다!

```java
// 가능! 인터페이스는 여러 개 구현 가능!
class Duck implements Flyable, Swimmable { }
```

이것이 인터페이스의 큰 장점 중 하나입니다.

### 상속과 인터페이스 동시 사용
<code class="yellow-code">extends</code>와 <code class="yellow-code">implements</code>를 함께 사용할 수도 있습니다.

```java
abstract class Animal {
    String name;
    void breathe() {
        System.out.println(name + "이(가) 숨을 쉽니다.");
    }
}

interface Swimmable {
    void swim();
}

class Dolphin extends Animal implements Swimmable {
    Dolphin(String name) { this.name = name; }

    @Override
    public void swim() {
        System.out.println(name + "이(가) 수영합니다!");
    }
}
```

### 문제 2: 인터페이스 구현 연습
> `Playable` 인터페이스를 만들고, `Guitar`와 `Piano` 클래스에서 구현하세요.
>
> **조건 및 힌트**
> 1. `Playable` 인터페이스에 `play()` 메서드를 선언하세요.
> 2. `Guitar`는 "기타를 연주합니다!", `Piano`는 "피아노를 연주합니다!"를 출력하세요.
> 3. `Playable` 타입 배열에 두 객체를 넣고 반복문으로 `play()`를 호출하세요.

<details>
  <summary><span class="green-bold">정답 보기</span></summary>

  <pre><code class="language-java">
    interface Playable {
        void play();
    }

    class Guitar implements Playable {
        @Override
        public void play() {
            System.out.println("기타를 연주합니다!");
        }
    }

    class Piano implements Playable {
        @Override
        public void play() {
            System.out.println("피아노를 연주합니다!");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Playable[] instruments = { new Guitar(), new Piano() };

            for (Playable p : instruments) {
                p.play();
            }
        }
    }
  </code></pre>
</details>

## 4. 인터페이스와 다형성

앞 장에서 배운 **다형성**을 인터페이스에서도 동일하게 활용할 수 있습니다. <span class="blue-text">인터페이스 타입으로 다양한 구현 객체를 다룰 수 있습니다.</span>

```java
interface Payment {
    void pay(int amount);
}

class CardPayment implements Payment {
    @Override
    public void pay(int amount) {
        System.out.println("카드로 " + amount + "원 결제");
    }
}

class CashPayment implements Payment {
    @Override
    public void pay(int amount) {
        System.out.println("현금으로 " + amount + "원 결제");
    }
}

class MobilePayment implements Payment {
    @Override
    public void pay(int amount) {
        System.out.println("모바일로 " + amount + "원 결제");
    }
}

public class Main {
    public static void main(String[] args) {
        // 인터페이스 타입 하나로 다양한 결제 수단을 다룰 수 있다!
        Payment p1 = new CardPayment();
        Payment p2 = new CashPayment();
        Payment p3 = new MobilePayment();

        p1.pay(10000);  // 카드로 10000원 결제
        p2.pay(5000);   // 현금으로 5000원 결제
        p3.pay(3000);   // 모바일로 3000원 결제
    }
}
```

이처럼 `Payment`라는 인터페이스 타입 하나로 카드, 현금, 모바일 등 <span class="green-text">다양한 결제 방식을 유연하게 처리</span>할 수 있습니다. 새로운 결제 수단이 추가되더라도 `Payment` 인터페이스를 구현하기만 하면 기존 코드를 수정할 필요가 없습니다.

### 문제 3: 인터페이스와 다형성 활용
> 알림 시스템을 만드세요. `Notifiable` 인터페이스를 정의하고, `EmailNotification`, `SmsNotification` 클래스에서 구현하세요.
>
> **조건 및 힌트**
> 1. `Notifiable` 인터페이스에 `send(String message)` 메서드를 선언하세요.
> 2. 각 클래스에서 알림 방식에 맞게 메시지를 출력하세요.
> 3. `Notifiable` 타입 배열로 두 객체를 관리하고, 반복문으로 알림을 보내세요.

<details>
  <summary><span class="green-bold">정답 보기</span></summary>

  <pre><code class="language-java">
    interface Notifiable {
        void send(String message);
    }

    class EmailNotification implements Notifiable {
        @Override
        public void send(String message) {
            System.out.println("[이메일] " + message);
        }
    }

    class SmsNotification implements Notifiable {
        @Override
        public void send(String message) {
            System.out.println("[SMS] " + message);
        }
    }

    public class Main {
        public static void main(String[] args) {
            Notifiable[] channels = {
                new EmailNotification(),
                new SmsNotification()
            };

            for (Notifiable n : channels) {
                n.send("주문이 완료되었습니다!");
            }
        }
    }
  </code></pre>
</details>

## 5. 디폴트 메서드와 정적 메서드

Java 8부터 인터페이스에도 <span class="blue-text">본문이 있는 메서드</span>를 작성할 수 있게 되었습니다.

### 디폴트 메서드 (default method)
<code class="yellow-code">default</code> 키워드를 붙이면, 인터페이스 안에서 메서드의 <span class="blue-text">기본 구현을 제공</span>할 수 있습니다. 구현 클래스에서 오버라이딩하지 않으면 기본 구현이 그대로 사용됩니다.

```java
interface Greeting {
    void greet();  // 추상 메서드 (반드시 구현)

    // 디폴트 메서드 (구현하지 않아도 됨)
    default void sayBye() {
        System.out.println("안녕히 가세요!");
    }
}

class KoreanGreeting implements Greeting {
    @Override
    public void greet() {
        System.out.println("안녕하세요!");
    }
    // sayBye()를 오버라이딩하지 않으면 기본 구현 사용
}

class EnglishGreeting implements Greeting {
    @Override
    public void greet() {
        System.out.println("Hello!");
    }

    @Override
    public void sayBye() {
        System.out.println("Goodbye!");  // 기본 구현을 재정의
    }
}
```

### 정적 메서드 (static method)
인터페이스에 <code class="yellow-code">static</code> 메서드를 정의하면, <span class="blue-text">인터페이스 이름으로 직접 호출</span>할 수 있습니다.

```java
interface MathHelper {
    static int add(int a, int b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        // 인터페이스 이름으로 직접 호출
        int result = MathHelper.add(3, 5);
        System.out.println(result);  // 8
    }
}
```

## 6. 인터페이스 상속

인터페이스끼리도 상속이 가능합니다. 이때 <code class="yellow-code">extends</code> 키워드를 사용하며, <span class="green-text">다중 상속도 허용</span>됩니다.

```java
interface Readable {
    void read();
}

interface Writable {
    void write();
}

// 인터페이스끼리 다중 상속 가능!
interface ReadWritable extends Readable, Writable {
    void readWrite();
}

// ReadWritable을 구현하면 read(), write(), readWrite() 모두 구현해야 함
class File implements ReadWritable {
    @Override
    public void read() {
        System.out.println("파일을 읽습니다.");
    }

    @Override
    public void write() {
        System.out.println("파일에 씁니다.");
    }

    @Override
    public void readWrite() {
        System.out.println("파일을 읽고 씁니다.");
    }
}
```

## 7. 추상 클래스 vs 인터페이스

<table>
  <colgroup>
    <col width="30%" />
    <col width="35%" />
    <col width="35%" />
  </colgroup>
  <tr align="center" style="background-color: #ddd;">
    <th>구분</th>
    <th>추상 클래스</th>
    <th>인터페이스</th>
  </tr>
  <tr>
    <td>키워드</td>
    <td><code class="yellow-code">abstract class</code></td>
    <td><code class="yellow-code">interface</code></td>
  </tr>
  <tr>
    <td>상속/구현</td>
    <td><code class="yellow-code">extends</code> (단일 상속만)</td>
    <td><code class="yellow-code">implements</code> (다중 구현 가능)</td>
  </tr>
  <tr>
    <td>필드</td>
    <td>일반 변수 가능</td>
    <td><span class="blue-text">상수(static final)만</span> 가능</td>
  </tr>
  <tr>
    <td>메서드</td>
    <td>일반 메서드 + 추상 메서드</td>
    <td>추상 메서드 + default/static 메서드</td>
  </tr>
  <tr>
    <td>생성자</td>
    <td><span class="green-text">있음</span></td>
    <td><span class="red-text">없음</span></td>
  </tr>
  <tr>
    <td>목적</td>
    <td>"~이다" (is-a 관계)</td>
    <td>"~할 수 있다" (has-a 능력)</td>
  </tr>
</table>

**언제 무엇을 사용할까?**
* <span class="blue-text">추상 클래스</span>: 공통된 필드나 기본 동작을 물려주고 싶을 때 → "강아지**는** 동물**이다**"
* <span class="blue-text">인터페이스</span>: 서로 관련 없는 클래스에 공통 능력을 부여하고 싶을 때 → "오리**는** 수영**할 수 있다**"

### 문제 4: 추상 클래스와 인터페이스 함께 사용하기
> 추상 클래스 `Vehicle`(탈것)을 만들고, 인터페이스 `Electric`(전기 충전 가능)을 정의하세요. `ElectricCar`는 `Vehicle`을 상속하고 `Electric`을 구현하세요.
>
> **조건 및 힌트**
> 1. `Vehicle`에는 추상 메서드 `drive()`와 일반 메서드 `stop()`을 정의하세요.
> 2. `Electric` 인터페이스에는 `charge()` 메서드를 선언하세요.
> 3. `ElectricCar`에서 `drive()`와 `charge()`를 구현하세요.

<details>
  <summary><span class="green-bold">정답 보기</span></summary>

  <pre><code class="language-java">
    abstract class Vehicle {
        abstract void drive();

        void stop() {
            System.out.println("정지합니다.");
        }
    }

    interface Electric {
        void charge();
    }

    class ElectricCar extends Vehicle implements Electric {
        @Override
        void drive() {
            System.out.println("전기차가 조용히 달립니다.");
        }

        @Override
        public void charge() {
            System.out.println("전기차를 충전합니다.");
        }
    }

    public class Main {
        public static void main(String[] args) {
            ElectricCar car = new ElectricCar();
            car.drive();   // 전기차가 조용히 달립니다.
            car.stop();    // 정지합니다.
            car.charge();  // 전기차를 충전합니다.
        }
    }
  </code></pre>
</details>

### 문제 5: 다중 인터페이스 구현
> 스마트폰 클래스를 만드세요. 스마트폰은 전화(`Callable`), 인터넷(`Browsable`), 카메라(`Photographable`) 기능을 모두 가지고 있습니다.
>
> **조건 및 힌트**
> 1. 세 개의 인터페이스를 각각 선언하세요.
> 2. `Callable`에는 `call(String number)`, `Browsable`에는 `browse(String url)`, `Photographable`에는 `takePhoto()` 메서드를 선언하세요.
> 3. `SmartPhone` 클래스에서 세 인터페이스를 모두 구현하세요.

<details>
  <summary><span class="green-bold">정답 보기</span></summary>

  <pre><code class="language-java">
    interface Callable {
        void call(String number);
    }

    interface Browsable {
        void browse(String url);
    }

    interface Photographable {
        void takePhoto();
    }

    class SmartPhone implements Callable, Browsable, Photographable {
        @Override
        public void call(String number) {
            System.out.println(number + "에 전화를 겁니다.");
        }

        @Override
        public void browse(String url) {
            System.out.println(url + "에 접속합니다.");
        }

        @Override
        public void takePhoto() {
            System.out.println("사진을 촬영합니다.");
        }
    }

    public class Main {
        public static void main(String[] args) {
            SmartPhone phone = new SmartPhone();
            phone.call("010-1234-5678");
            phone.browse("www.google.com");
            phone.takePhoto();

            // 인터페이스 타입으로도 사용 가능 (다형성!)
            Callable c = phone;
            c.call("010-9876-5432");
        }
    }
  </code></pre>
</details>

### 문제 6: 인터페이스 기반 정렬 시스템 설계
> 학생 성적 관리 프로그램을 만드세요. `Sortable` 인터페이스를 정의하고 `Student` 클래스에서 구현하여, 학생 배열을 점수 기준으로 정렬하세요.
>
> **조건 및 힌트**
> 1. `Sortable` 인터페이스에 `int compareTo(Student other)` 메서드를 선언하세요.
> 2. `Student` 클래스는 `name`과 `score` 필드를 갖습니다.
> 3. `compareTo`는 점수가 높으면 양수, 같으면 0, 낮으면 음수를 반환하세요.
> 4. 버블 정렬을 사용하여 학생 배열을 점수 내림차순으로 정렬하세요.

<details>
  <summary><span class="green-bold">정답 보기</span></summary>

  <pre><code class="language-java">
    interface Sortable {
        int compareTo(Student other);
    }

    class Student implements Sortable {
        String name;
        int score;

        Student(String name, int score) {
            this.name = name;
            this.score = score;
        }

        @Override
        public int compareTo(Student other) {
            return this.score - other.score;
        }

        void showInfo() {
            System.out.println(name + ": " + score + "점");
        }
    }

    public class Main {
        public static void main(String[] args) {
            Student[] students = {
                new Student("철수", 85),
                new Student("영희", 92),
                new Student("민수", 78)
            };

            // 버블 정렬 (점수 내림차순)
            for (int i = 0; i < students.length - 1; i++) {
                for (int j = 0; j < students.length - 1 - i; j++) {
                    if (students[j].compareTo(students[j + 1]) < 0) {
                        Student temp = students[j];
                        students[j] = students[j + 1];
                        students[j + 1] = temp;
                    }
                }
            }

            for (Student s : students) {
                s.showInfo();
            }
            // 영희: 92점
            // 철수: 85점
            // 민수: 78점
        }
    }
  </code></pre>
</details>