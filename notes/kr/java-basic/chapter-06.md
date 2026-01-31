---
layout: article
title: 6. 클래스와 객체
permalink: /notes/kr/java-basic/chapter-06
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: Java 기초 과정 강의 노트, 클래스와 객체 개념, 접근 제어자, 메서드 정의 및 호출, 생성자 및 생성자 오버로딩, 상속 및 super 키워드를 다룹니다.
keywords: "Java, 클래스, 객체, OOP, 객체지향, 접근제어자, public, private, 메서드, 생성자, 오버로딩, 상속, extends, super"
---

<script src="/assets/js/quiz.js"></script>

<style>
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
    .quiz-container {
        margin: 20px 0;
        padding: 15px;
        border: 1px solid #e5e7eb;
        border-radius: 12px;
        background-color: #ffffff;
        box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);
    }
    .quiz-container:hover {
        box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);
    }
    .quiz-number {
        display: inline-block;
        background-color: #203BB0;
        color: white;
        padding: 5px 12px;
        border-radius: 15px;
        margin-right: 10px;
        font-size: 0.9em;
    }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=Java%20Basic&reversal=false&textBg=false)

---

## 객체지향 프로그래밍 (OOP)

Java는 <span class="blue-text">객체지향 프로그래밍(Object-Oriented Programming)</span> 언어입니다. 객체지향이란 현실 세계의 사물을 프로그램 속 **객체**로 표현하는 방식입니다.

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">일상 속 객체</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
자동차를 생각해보세요. 자동차는 색상, 속도, 연료량 같은 <strong>속성(데이터)</strong>과 출발하기, 멈추기, 가속하기 같은 <strong>기능(메서드)</strong>을 가지고 있습니다. 이처럼 속성과 기능을 하나로 묶어 표현한 것이 객체입니다.
</p>
</div>

### 객체지향의 4대 특징

| 특징 | 설명 |
|------|------|
| 캡슐화 (Encapsulation) | 데이터와 메서드를 하나로 묶고, 외부에서 직접 접근을 제한 |
| 상속 (Inheritance) | 기존 클래스의 속성과 메서드를 물려받아 새로운 클래스 생성 |
| 다형성 (Polymorphism) | 같은 이름의 메서드가 상황에 따라 다르게 동작 |
| 추상화 (Abstraction) | 복잡한 내부 구현을 숨기고 핵심 기능만 노출 |

---

## 클래스와 객체

### 클래스란?

<span class="blue-text">클래스(Class)</span>는 객체를 만들기 위한 **설계도(틀)**입니다. 클래스에는 객체가 가질 속성(변수)과 기능(메서드)이 정의됩니다.

```java
// 클래스 정의 (설계도)
public class Car {
    // 속성 (필드, 멤버 변수)
    String color;
    int speed;

    // 기능 (메서드)
    void accelerate() {
        speed += 10;
    }

    void brake() {
        speed -= 10;
    }
}
```

### 객체란?

<span class="blue-text">객체(Object)</span>는 클래스를 바탕으로 실제로 생성된 **인스턴스(Instance)**입니다. 하나의 클래스로 여러 객체를 만들 수 있습니다.

```
클래스 (설계도)              객체 (실체)
┌─────────────┐            ┌─────────────┐
│    Car      │  ───→      │ myCar       │
│ - color     │            │ color="빨강" │
│ - speed     │            │ speed=60    │
│ + accelerate│            └─────────────┘
│ + brake     │            ┌─────────────┐
└─────────────┘  ───→      │ yourCar     │
                           │ color="파랑" │
                           │ speed=80    │
                           └─────────────┘
```

### 객체 생성

`new` 키워드를 사용하여 객체를 생성합니다.

```java
public class CarTest {
    public static void main(String[] args) {
        // 객체 생성
        Car myCar = new Car();

        // 속성 설정
        myCar.color = "빨강";
        myCar.speed = 0;

        // 메서드 호출
        myCar.accelerate();
        System.out.println("속도: " + myCar.speed);  // 속도: 10

        myCar.accelerate();
        System.out.println("속도: " + myCar.speed);  // 속도: 20

        myCar.brake();
        System.out.println("속도: " + myCar.speed);  // 속도: 10
    }
}
```

### 여러 객체 생성

```java
public class CarTest {
    public static void main(String[] args) {
        Car car1 = new Car();
        Car car2 = new Car();

        car1.color = "빨강";
        car1.speed = 100;

        car2.color = "파랑";
        car2.speed = 80;

        System.out.println("car1: " + car1.color + ", " + car1.speed + "km/h");
        System.out.println("car2: " + car2.color + ", " + car2.speed + "km/h");
    }
}
```

**출력:**

```
car1: 빨강, 100km/h
car2: 파랑, 80km/h
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">클래스 vs 객체</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <strong>클래스</strong>: 붕어빵 틀 (설계도)<br>
• <strong>객체</strong>: 붕어빵 틀로 만든 각각의 붕어빵 (실체)<br>
하나의 틀(클래스)로 여러 개의 붕어빵(객체)을 만들 수 있습니다.
</p>
</div>

---

## 인스턴스 변수와 클래스 변수

### 인스턴스 변수

<span class="blue-text">인스턴스 변수</span>는 각 객체마다 **독립적으로** 가지는 변수입니다.

```java
public class Student {
    String name;      // 인스턴스 변수
    int score;        // 인스턴스 변수
}
```

```java
Student s1 = new Student();
Student s2 = new Student();

s1.name = "홍길동";
s1.score = 90;

s2.name = "김철수";
s2.score = 85;

// s1과 s2는 각자의 name, score를 가짐
```

### 클래스 변수 (static)

<span class="blue-text">클래스 변수</span>는 모든 객체가 **공유**하는 변수입니다. `static` 키워드를 사용합니다.

```java
public class Student {
    String name;              // 인스턴스 변수
    int score;                // 인스턴스 변수
    static int studentCount;  // 클래스 변수 (공유)
}
```

```java
Student s1 = new Student();
Student.studentCount++;  // 클래스 이름으로 접근

Student s2 = new Student();
Student.studentCount++;

System.out.println(Student.studentCount);  // 2
```

### 인스턴스 변수 vs 클래스 변수

| 구분 | 인스턴스 변수 | 클래스 변수 (static) |
|------|--------------|---------------------|
| 선언 | `int num;` | `static int num;` |
| 생성 시점 | 객체 생성 시 | 클래스 로드 시 |
| 메모리 위치 | 힙(Heap) | 메서드 영역 |
| 공유 여부 | 객체마다 개별 | 모든 객체가 공유 |
| 접근 방법 | `객체명.변수` | `클래스명.변수` |

---

## 접근 제어자

<span class="blue-text">접근 제어자(Access Modifier)</span>는 클래스, 변수, 메서드에 대한 접근 범위를 제한합니다.

### 접근 제어자 종류

| 접근 제어자 | 같은 클래스 | 같은 패키지 | 자식 클래스 | 전체 |
|------------|:----------:|:----------:|:----------:|:----:|
| `public` | O | O | O | O |
| `protected` | O | O | O | X |
| `(default)` | O | O | X | X |
| `private` | O | X | X | X |

```java
public class Person {
    public String name;       // 어디서든 접근 가능
    protected int age;        // 같은 패키지 + 자식 클래스
    String address;           // 같은 패키지만 (default)
    private String password;  // 같은 클래스만
}
```

### 캡슐화와 정보 은닉

<span class="blue-text">캡슐화</span>는 데이터를 `private`으로 숨기고, `public` 메서드(getter/setter)를 통해 접근하는 것입니다.

```java
public class BankAccount {
    private int balance;  // 외부에서 직접 접근 불가

    // Getter: 값을 반환
    public int getBalance() {
        return balance;
    }

    // Setter: 값을 설정 (유효성 검사 가능)
    public void setBalance(int balance) {
        if (balance >= 0) {
            this.balance = balance;
        }
    }

    // 입금
    public void deposit(int amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    // 출금
    public void withdraw(int amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
        }
    }
}
```

```java
public class BankTest {
    public static void main(String[] args) {
        BankAccount account = new BankAccount();

        // account.balance = 1000;  // 오류! private 접근 불가

        account.setBalance(1000);   // setter로 접근
        account.deposit(500);
        account.withdraw(200);

        System.out.println("잔액: " + account.getBalance());  // 1300
    }
}
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">왜 캡슐화를 할까?</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <strong>데이터 보호</strong>: 잘못된 값이 들어가는 것을 방지<br>
• <strong>유지보수</strong>: 내부 구현 변경 시 외부 코드에 영향 없음<br>
• <strong>유효성 검사</strong>: setter에서 값을 검증할 수 있음
</p>
</div>

---

## 메서드 정의 및 호출

### 메서드란?

<span class="blue-text">메서드(Method)</span>는 특정 작업을 수행하는 코드 블록입니다. 재사용 가능하고, 코드를 구조화하는 데 도움이 됩니다.

### 메서드 정의

```java
접근제어자 반환타입 메서드명(매개변수) {
    // 실행할 코드
    return 반환값;  // 반환타입이 void가 아닌 경우
}
```

### 메서드 예제

```java
public class Calculator {

    // 반환값이 없는 메서드
    public void printHello() {
        System.out.println("Hello!");
    }

    // 매개변수와 반환값이 있는 메서드
    public int add(int a, int b) {
        return a + b;
    }

    // 여러 매개변수
    public int multiply(int a, int b) {
        return a * b;
    }

    // 조건에 따른 반환
    public String getGrade(int score) {
        if (score >= 90) return "A";
        else if (score >= 80) return "B";
        else if (score >= 70) return "C";
        else return "F";
    }
}
```

### 메서드 호출

```java
public class CalculatorTest {
    public static void main(String[] args) {
        Calculator calc = new Calculator();

        calc.printHello();  // Hello!

        int sum = calc.add(10, 20);
        System.out.println("합계: " + sum);  // 합계: 30

        int product = calc.multiply(5, 4);
        System.out.println("곱: " + product);  // 곱: 20

        String grade = calc.getGrade(85);
        System.out.println("학점: " + grade);  // 학점: B
    }
}
```

### 메서드 오버로딩

<span class="blue-text">메서드 오버로딩(Overloading)</span>은 같은 이름의 메서드를 **매개변수의 타입이나 개수**를 다르게 하여 여러 개 정의하는 것입니다.

```java
public class Calculator {

    // 정수 2개 덧셈
    public int add(int a, int b) {
        return a + b;
    }

    // 정수 3개 덧셈
    public int add(int a, int b, int c) {
        return a + b + c;
    }

    // 실수 덧셈
    public double add(double a, double b) {
        return a + b;
    }
}
```

```java
Calculator calc = new Calculator();

System.out.println(calc.add(10, 20));         // 30 (int, int)
System.out.println(calc.add(10, 20, 30));     // 60 (int, int, int)
System.out.println(calc.add(1.5, 2.5));       // 4.0 (double, double)
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">오버로딩 조건</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• 메서드 이름이 같아야 함<br>
• <span class="blue-text">매개변수의 타입, 개수, 순서</span> 중 하나 이상이 달라야 함<br>
• <span class="red-text">반환 타입만 다른 것은 오버로딩이 아님</span>
</p>
</div>

---

## 생성자

### 생성자란?

<span class="blue-text">생성자(Constructor)</span>는 객체가 생성될 때 **자동으로 호출**되는 특별한 메서드입니다. 객체의 초기화를 담당합니다.

### 생성자의 특징

- 클래스 이름과 동일
- 반환 타입이 없음 (void도 쓰지 않음)
- 객체 생성 시 `new` 키워드와 함께 호출

### 기본 생성자

매개변수가 없는 생성자입니다. 클래스에 생성자가 하나도 없으면 컴파일러가 자동으로 기본 생성자를 추가합니다.

```java
public class Person {
    String name;
    int age;

    // 기본 생성자
    public Person() {
        name = "이름 없음";
        age = 0;
    }
}
```

```java
Person p = new Person();  // 기본 생성자 호출
System.out.println(p.name);  // 이름 없음
System.out.println(p.age);   // 0
```

### 매개변수가 있는 생성자

```java
public class Person {
    String name;
    int age;

    // 매개변수가 있는 생성자
    public Person(String name, int age) {
        this.name = name;  // this: 현재 객체
        this.age = age;
    }
}
```

```java
Person p = new Person("홍길동", 25);
System.out.println(p.name);  // 홍길동
System.out.println(p.age);   // 25
```

### this 키워드

<span class="yellow-code">this</span>는 현재 객체 자신을 가리킵니다. 매개변수와 인스턴스 변수의 이름이 같을 때 구분하기 위해 사용합니다.

```java
public class Student {
    String name;
    int score;

    public Student(String name, int score) {
        this.name = name;    // this.name: 인스턴스 변수
        this.score = score;  // name: 매개변수
    }
}
```

### 생성자 오버로딩

생성자도 오버로딩할 수 있습니다. 다양한 방법으로 객체를 초기화할 수 있습니다.

```java
public class Book {
    String title;
    String author;
    int price;

    // 기본 생성자
    public Book() {
        this.title = "제목 없음";
        this.author = "저자 미상";
        this.price = 0;
    }

    // 제목만 받는 생성자
    public Book(String title) {
        this.title = title;
        this.author = "저자 미상";
        this.price = 0;
    }

    // 모든 값을 받는 생성자
    public Book(String title, String author, int price) {
        this.title = title;
        this.author = author;
        this.price = price;
    }

    public void showInfo() {
        System.out.println(title + " / " + author + " / " + price + "원");
    }
}
```

```java
Book book1 = new Book();
Book book2 = new Book("Java 입문");
Book book3 = new Book("Java 마스터", "홍길동", 25000);

book1.showInfo();  // 제목 없음 / 저자 미상 / 0원
book2.showInfo();  // Java 입문 / 저자 미상 / 0원
book3.showInfo();  // Java 마스터 / 홍길동 / 25000원
```

### this()를 이용한 생성자 호출

한 생성자에서 다른 생성자를 호출할 때 `this()`를 사용합니다. **첫 줄에서만** 사용 가능합니다.

```java
public class Book {
    String title;
    String author;
    int price;

    public Book() {
        this("제목 없음", "저자 미상", 0);  // 다른 생성자 호출
    }

    public Book(String title) {
        this(title, "저자 미상", 0);
    }

    public Book(String title, String author, int price) {
        this.title = title;
        this.author = author;
        this.price = price;
    }
}
```

---

## 상속

### 상속이란?

<span class="blue-text">상속(Inheritance)</span>은 기존 클래스의 속성과 메서드를 물려받아 새로운 클래스를 만드는 것입니다.

- **부모 클래스 (Super Class)**: 상속을 해주는 클래스
- **자식 클래스 (Sub Class)**: 상속을 받는 클래스

### extends 키워드

```java
// 부모 클래스
public class Animal {
    String name;

    public void eat() {
        System.out.println(name + "이(가) 먹습니다.");
    }

    public void sleep() {
        System.out.println(name + "이(가) 잡니다.");
    }
}
```

```java
// 자식 클래스
public class Dog extends Animal {

    // 자식 클래스만의 메서드
    public void bark() {
        System.out.println(name + "이(가) 멍멍 짖습니다.");
    }
}
```

```java
// 자식 클래스
public class Cat extends Animal {

    public void meow() {
        System.out.println(name + "이(가) 야옹 웁니다.");
    }
}
```

```java
public class AnimalTest {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.name = "바둑이";
        dog.eat();    // 바둑이이(가) 먹습니다.
        dog.sleep();  // 바둑이이(가) 잡니다.
        dog.bark();   // 바둑이이(가) 멍멍 짖습니다.

        Cat cat = new Cat();
        cat.name = "나비";
        cat.eat();    // 나비이(가) 먹습니다.
        cat.meow();   // 나비이(가) 야옹 웁니다.
    }
}
```

### 상속의 장점

```
           Animal
         /        \
       Dog        Cat
```

- **코드 재사용**: 공통 코드를 부모 클래스에 작성
- **유지보수 용이**: 공통 기능 수정 시 부모 클래스만 수정
- **확장성**: 새로운 자식 클래스 추가 용이

### 메서드 오버라이딩

<span class="blue-text">오버라이딩(Overriding)</span>은 부모 클래스의 메서드를 자식 클래스에서 **재정의**하는 것입니다.

```java
public class Animal {
    String name;

    public void sound() {
        System.out.println("동물 소리");
    }
}
```

```java
public class Dog extends Animal {

    @Override  // 오버라이딩 어노테이션 (권장)
    public void sound() {
        System.out.println("멍멍!");
    }
}
```

```java
public class Cat extends Animal {

    @Override
    public void sound() {
        System.out.println("야옹!");
    }
}
```

```java
Animal dog = new Dog();
Animal cat = new Cat();

dog.sound();  // 멍멍!
cat.sound();  // 야옹!
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">오버라이딩 vs 오버로딩</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <strong>오버라이딩(Overriding)</strong>: 부모의 메서드를 자식이 <span class="blue-text">재정의</span> (같은 이름, 같은 매개변수)<br>
• <strong>오버로딩(Overloading)</strong>: 같은 이름의 메서드를 <span class="blue-text">여러 개 정의</span> (다른 매개변수)
</p>
</div>

### super 키워드

<span class="yellow-code">super</span>는 부모 클래스를 가리킵니다.

**1. 부모의 변수나 메서드 접근:**

```java
public class Parent {
    String name = "부모";

    public void show() {
        System.out.println("Parent의 show()");
    }
}

public class Child extends Parent {
    String name = "자식";

    @Override
    public void show() {
        System.out.println("Child의 show()");
    }

    public void display() {
        System.out.println(name);        // 자식
        System.out.println(super.name);  // 부모

        show();        // Child의 show()
        super.show();  // Parent의 show()
    }
}
```

**2. 부모의 생성자 호출 (super()):**

자식 클래스의 생성자에서 `super()`를 사용하여 부모 생성자를 호출합니다.

```java
public class Person {
    String name;
    int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

public class Student extends Person {
    String school;

    public Student(String name, int age, String school) {
        super(name, age);  // 부모 생성자 호출 (첫 줄에서!)
        this.school = school;
    }

    public void showInfo() {
        System.out.println("이름: " + name);
        System.out.println("나이: " + age);
        System.out.println("학교: " + school);
    }
}
```

```java
Student student = new Student("홍길동", 20, "서울대학교");
student.showInfo();
```

**출력:**

```
이름: 홍길동
나이: 20
학교: 서울대학교
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">super() 규칙</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <code>super()</code>는 생성자의 <span class="red-text">첫 줄에서만</span> 호출 가능<br>
• 명시하지 않으면 컴파일러가 자동으로 <code>super()</code> 삽입<br>
• 부모에 기본 생성자가 없으면 반드시 <code>super(매개변수)</code> 호출 필요
</p>
</div>

---

## 종합 실습

### 문제 1 - 객체 생성 (기초)

<div class="quiz-number">문제 1</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Counter {
    int count = 0;
    void increase() { count++; }
}

public class Test {
    public static void main(String[] args) {
        Counter c = new Counter();
        c.increase();
        c.increase();
        c.increase();
        System.out.println(c.count);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="3"
   tags="클래스와 객체"
%}

---

### 문제 2 - 생성자 (기초)

<div class="quiz-number">문제 2</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Person {
    String name;
    Person(String name) {
        this.name = name;
    }
}

public class Test {
    public static void main(String[] args) {
        Person p = new Person("홍길동");
        System.out.println(p.name);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="홍길동"
   tags="클래스와 객체"
%}

---

### 문제 3 - 메서드 오버로딩 (기초)

<div class="quiz-number">문제 3</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Calculator {
    int add(int a, int b) { return a + b; }
    int add(int a, int b, int c) { return a + b + c; }
}

public class Test {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(1, 2, 3));
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="6"
   tags="클래스와 객체"
%}

---

### 문제 4 - static 변수 (중급)

<div class="quiz-number">문제 4</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Item {
    static int count = 0;
    Item() { count++; }
}

public class Test {
    public static void main(String[] args) {
        Item i1 = new Item();
        Item i2 = new Item();
        Item i3 = new Item();
        System.out.println(Item.count);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="3"
   tags="클래스와 객체"
%}

---

### 문제 5 - 상속 기본 (중급)

<div class="quiz-number">문제 5</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Animal {
    void sound() { System.out.print("동물"); }
}

class Dog extends Animal {
    void sound() { System.out.print("멍멍"); }
}

public class Test {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound();
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   code_html=code_block5
   answer="멍멍"
   tags="클래스와 객체"
%}

---

### 문제 6 - super 키워드 (중급)

<div class="quiz-number">문제 6</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Parent {
    int num = 10;
}

class Child extends Parent {
    int num = 20;
    void show() {
        System.out.println(super.num + this.num);
    }
}

public class Test {
    public static void main(String[] args) {
        Child c = new Child();
        c.show();
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   code_html=code_block6
   answer="30"
   tags="클래스와 객체"
%}

---

### 문제 7 - 생성자 체이닝 (고급)

<div class="quiz-number">문제 7</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class A {
    A() { System.out.print("A"); }
}

class B extends A {
    B() { System.out.print("B"); }
}

class C extends B {
    C() { System.out.print("C"); }
}

public class Test {
    public static void main(String[] args) {
        C c = new C();
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7"
   code_html=code_block7
   answer="ABC"
   tags="클래스와 객체"
%}

---

### 문제 8 - 복합 문제 (고급)

<div class="quiz-number">문제 8</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Shape {
    int getArea() { return 0; }
}

class Rectangle extends Shape {
    int width, height;
    Rectangle(int w, int h) {
        width = w;
        height = h;
    }
    int getArea() { return width * height; }
}

public class Test {
    public static void main(String[] args) {
        Shape s = new Rectangle(5, 4);
        System.out.println(s.getArea());
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8"
   code_html=code_block8
   answer="20"
   tags="클래스와 객체"
%}

---

## 실전 프로그래밍

### 과제 1: 학생 관리 클래스

학생 정보를 관리하는 Student 클래스를 작성하세요.

**요구사항:**
- 필드: 이름(name), 학번(studentId), 점수(score)
- 생성자: 이름과 학번을 받는 생성자
- 메서드: setScore(점수 설정), getGrade(학점 반환)
- 학점 기준: 90이상 A, 80이상 B, 70이상 C, 60이상 D, 미만 F

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">public class Student {
    private String name;
    private String studentId;
    private int score;

    public Student(String name, String studentId) {
        this.name = name;
        this.studentId = studentId;
        this.score = 0;
    }

    public void setScore(int score) {
        if (score >= 0 && score <= 100) {
            this.score = score;
        }
    }

    public String getGrade() {
        if (score >= 90) return "A";
        else if (score >= 80) return "B";
        else if (score >= 70) return "C";
        else if (score >= 60) return "D";
        else return "F";
    }

    public void showInfo() {
        System.out.println("이름: " + name);
        System.out.println("학번: " + studentId);
        System.out.println("점수: " + score);
        System.out.println("학점: " + getGrade());
    }

    public static void main(String[] args) {
        Student s = new Student("홍길동", "2024001");
        s.setScore(85);
        s.showInfo();
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>이름: 홍길동
학번: 2024001
점수: 85
학점: B
</code></pre>

</details>

---

### 과제 2: 도형 상속 구조

Shape 클래스를 상속받아 Rectangle과 Circle 클래스를 작성하세요.

**요구사항:**
- Shape: 추상 클래스가 아닌 일반 클래스, getArea() 메서드 (0 반환)
- Rectangle: width, height 필드, getArea() 오버라이딩
- Circle: radius 필드, getArea() 오버라이딩 (π = 3.14)
- 각 클래스에 적절한 생성자 추가

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">class Shape {
    public double getArea() {
        return 0;
    }
}

class Rectangle extends Shape {
    private int width;
    private int height;

    public Rectangle(int width, int height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double getArea() {
        return width * height;
    }
}

class Circle extends Shape {
    private int radius;

    public Circle(int radius) {
        this.radius = radius;
    }

    @Override
    public double getArea() {
        return 3.14 * radius * radius;
    }
}

public class ShapeTest {
    public static void main(String[] args) {
        Shape rect = new Rectangle(5, 4);
        Shape circle = new Circle(3);

        System.out.println("사각형 넓이: " + rect.getArea());
        System.out.println("원 넓이: " + circle.getArea());
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>사각형 넓이: 20.0
원 넓이: 28.26
</code></pre>

</details>

---

### 과제 3: 은행 계좌 시스템

BankAccount 클래스를 작성하고, SavingsAccount(저축 계좌)를 상속받아 구현하세요.

**요구사항:**
- BankAccount: 계좌번호, 잔액, 입금(deposit), 출금(withdraw) 메서드
- SavingsAccount: 이자율(interestRate) 추가, addInterest() 메서드
- 출금 시 잔액 부족하면 출금 불가
- super()를 사용하여 부모 생성자 호출

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">class BankAccount {
    protected String accountNumber;
    protected int balance;

    public BankAccount(String accountNumber, int initialBalance) {
        this.accountNumber = accountNumber;
        this.balance = initialBalance;
    }

    public void deposit(int amount) {
        if (amount > 0) {
            balance += amount;
            System.out.println(amount + "원 입금. 잔액: " + balance + "원");
        }
    }

    public void withdraw(int amount) {
        if (amount > 0 && balance >= amount) {
            balance -= amount;
            System.out.println(amount + "원 출금. 잔액: " + balance + "원");
        } else {
            System.out.println("출금 불가. 잔액 부족.");
        }
    }

    public int getBalance() {
        return balance;
    }
}

class SavingsAccount extends BankAccount {
    private double interestRate;

    public SavingsAccount(String accountNumber, int initialBalance, double interestRate) {
        super(accountNumber, initialBalance);
        this.interestRate = interestRate;
    }

    public void addInterest() {
        int interest = (int)(balance * interestRate);
        balance += interest;
        System.out.println("이자 " + interest + "원 추가. 잔액: " + balance + "원");
    }
}

public class BankTest {
    public static void main(String[] args) {
        SavingsAccount account = new SavingsAccount("123-456", 100000, 0.05);

        account.deposit(50000);
        account.withdraw(30000);
        account.addInterest();

        System.out.println("최종 잔액: " + account.getBalance() + "원");
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>50000원 입금. 잔액: 150000원
30000원 출금. 잔액: 120000원
이자 6000원 추가. 잔액: 126000원
최종 잔액: 126000원
</code></pre>

</details>

---

## 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 16px;">
<span style="font-size: 1.25rem;">✅</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">이번 챕터에서 배운 내용</h3>
</div>

<ol style="margin: 0; padding-left: 20px; color: #4b5563;">
<li style="margin-bottom: 12px;"><strong>클래스와 객체</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">class Car { }           // 클래스 (설계도)
Car myCar = new Car();  // 객체 (인스턴스)
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>접근 제어자</strong>
   <table style="margin-top: 8px; margin-bottom: 0; width: 100%; border-collapse: collapse;">
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <th style="padding: 8px; text-align: left;">제어자</th>
   <th style="padding: 8px; text-align: left;">접근 범위</th>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;"><code>public</code></td>
   <td style="padding: 8px;">모든 곳</td>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;"><code>protected</code></td>
   <td style="padding: 8px;">같은 패키지 + 자식 클래스</td>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;">(default)</td>
   <td style="padding: 8px;">같은 패키지</td>
   </tr>
   <tr>
   <td style="padding: 8px;"><code>private</code></td>
   <td style="padding: 8px;">같은 클래스</td>
   </tr>
   </table>
</li>
<li style="margin-bottom: 12px;"><strong>메서드 정의</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">public int add(int a, int b) {
    return a + b;
}
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>생성자</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">public Person(String name) {
    this.name = name;
}
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>상속</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">class Child extends Parent {
    // 부모의 속성과 메서드 상속
}
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>super 키워드</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">super.변수      // 부모의 변수
super.메서드()  // 부모의 메서드
super()        // 부모의 생성자
</code></pre>
</li>
<li style="margin-bottom: 0;"><strong>주요 포인트</strong>
   <ul style="margin-top: 8px; margin-bottom: 0;">
   <li>클래스는 설계도, 객체는 실체</li>
   <li>캡슐화: private + getter/setter</li>
   <li>오버로딩: 같은 이름, 다른 매개변수</li>
   <li>오버라이딩: 부모 메서드 재정의 (@Override)</li>
   <li>super()는 생성자 첫 줄에서만 호출</li>
   <li>생성자 호출 순서: 부모 → 자식</li>
   </ul>
</li>
</ol>

</div>

---

## 다음 챕터 예고

다음 챕터에서는 **추상 클래스와 인터페이스**를 배웁니다.

- 추상 클래스 (abstract class)
- 추상 메서드
- 인터페이스 (interface)
- 인터페이스 구현 (implements)
- 다중 상속과 인터페이스
- 디폴트 메서드

---

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04); text-align: center;">
<div style="display: flex; align-items: center; justify-content: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">🎯</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">클래스와 객체 학습 완료!</h3>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
객체지향 프로그래밍의 핵심인 클래스, 객체, 상속을 배웠습니다.<br>
이제 추상 클래스와 인터페이스를 배우면 더욱 유연한 설계가 가능합니다!
</p>
</div>
