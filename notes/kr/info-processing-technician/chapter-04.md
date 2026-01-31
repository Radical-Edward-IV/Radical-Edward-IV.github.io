---
layout: article
title: 3. Java 프로그래밍
permalink: /notes/kr/info-processing-technician/chapter-04
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - Java의 입·출력, 제어문, 클래스, 추상 클래스, 인터페이스를 학습합니다.
keywords: "프로그래밍기능사, Java, 입출력, 제어문, 클래스, 추상 클래스, 인터페이스, 상속, 다형성"
---

<script src="/assets/js/quiz.js"></script>

<style>
    .quiz-container {
        margin: 20px 0;
        padding: 15px;
        border: 1px solid #e5e7eb;
        border-radius: 12px;
        background-color: #ffffff;
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
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EA%B8%B0%EB%8A%A5%EC%82%AC&reversal=false&textBg=false)

---

# PART 1. 데이터 입·출력

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Java의 기본 프로그램 구조와 입·출력 함수, 연산자 우선순위를 이해하세요. 코드를 읽고 실행 결과를 정확히 예측하는 것이 핵심입니다.
</p>
</div>

## 1.1 프로그램의 기본 구조

다음은 입력받은 정수를 가지고 여러 연산을 수행한 후 출력하는 프로그램입니다.

```java
import java.util.Scanner;
public class Test {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        int a = scan.nextInt();
        System.out.printf("a * 3 = %d\n", a * 3);
        System.out.println("a / 2 = " + (a / 2));
        System.out.print("a - 1 = " + (a - 1));
        scan.close();
    }
}
```

| 코드 | 설명 |
|------|------|
| `import java.util.Scanner;` | Scanner 클래스를 java.util 패키지에서 가져옴 |
| `public class Test` | 클래스 정의. 클래스 이름은 첫 글자를 대문자로 |
| `public static void main(String[] args)` | 프로그램 실행 진입점(Entry Point) |
| `Scanner scan = new Scanner(System.in);` | 키보드로부터 입력받을 객체 생성 |
| `int a = scan.nextInt();` | 정수형 값을 입력받아 a에 저장 |
| `System.out.printf()` | 서식 문자열을 사용하여 출력 |
| `System.out.println()` | 출력 후 줄바꿈 |
| `System.out.print()` | 출력 (줄바꿈 없음) |

---

## 1.2 헝가리안 표기법

<span class="blue-text">헝가리안 표기법(Hungarian Notation)</span>이란 변수명에 자료형을 의미하는 문자를 포함하여 작성하는 방법입니다.

```java
int i_InputA;      // 정수형 변수
double d_Result;   // 실수형 변수
```

---

## 1.3 주요 자료형

| 종류 | 자료형 | 크기(Java) |
|------|--------|------------|
| 정수형 | `int` | 4Byte |
| 문자형 | `char` | 2Byte |
| 실수형 | `float` | 4Byte |
| 실수형 | `double` | 8Byte |

---

## 1.4 서식 지정자와 제어 문자

### 주요 서식 지정자

| 서식 지정자 | 의미 |
|-------------|------|
| `%d` | 정수형 10진수 |
| `%o` | 정수형 8진수 |
| `%x` | 정수형 16진수 |
| `%c` | 문자 |
| `%s` | 문자열 |
| `%f` | 실수형 (기본 소수점 6자리) |
| `%b` | boolean 값 |

### 주요 제어 문자

| 제어 문자 | 기능 |
|-----------|------|
| `\n` | 줄바꿈 |
| `\t` | 탭 |
| `\0` | 널(Null) 문자 |

---

## 1.5 연산자 우선순위

| 대분류 | 중분류 | 연산자 | 우선순위 |
|--------|--------|--------|----------|
| 단항 연산자 | 단항 | `++` `--` `!` `~` | 높음 ↑ |
| 이항 연산자 | 산술 | `*` `/` `%` | |
| | 산술 | `+` `-` | |
| | 시프트 | `<<` `>>` | |
| | 관계 | `<` `<=` `>` `>=` | |
| | 관계 | `==` `!=` | |
| | 비트 | `&` `^` `|` | |
| | 논리 | `&&` `||` | |
| 삼항 연산자 | 조건 | `? :` | |
| 대입 연산자 | 대입 | `=` `+=` `-=` 등 | 낮음 ↓ |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">진법 표기법</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <strong>8진수</strong>: 숫자 앞에 <code>0</code>을 붙임 (예: <code>024</code> = 10진수 20)<br>
• <strong>16진수</strong>: 숫자 앞에 <code>0x</code>를 붙임 (예: <code>0x24</code> = 10진수 36)
</p>
</div>

---

# PART 2. 제어문

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
제어문은 프로그램의 흐름을 제어하는 핵심 구문입니다. 코드 추적 능력이 시험의 핵심입니다.
</p>
</div>

## 2.1 조건문

### if문

```java
if (조건식) {
    // 조건식이 참일 때 실행
} else if (조건식2) {
    // 조건식2가 참일 때 실행
} else {
    // 모든 조건이 거짓일 때 실행
}
```

### switch문

```java
switch (변수) {
    case 값1:
        // 값1일 때 실행
        break;
    case 값2:
        // 값2일 때 실행
        break;
    default:
        // 어떤 case에도 해당하지 않을 때 실행
}
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">switch문 주의사항</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <strong>break 누락</strong>: break가 없으면 다음 case로 <span class="red-text">fall-through</span>(연속 실행)됩니다.
</p>
</div>

---

## 2.2 반복문

### for문

```java
for (초기식; 조건식; 증감식) {
    // 반복 실행할 명령문
}
```

### while문

```java
while (조건식) {
    // 조건식이 참인 동안 반복 실행
}
```

### do-while문

```java
do {
    // 최소 1회 실행 후 조건 검사
} while (조건식);
```

---

## 2.3 분기문

| 분기문 | 설명 |
|--------|------|
| `break` | 반복문을 <span class="red-text">완전히 종료</span> |
| `continue` | 현재 반복만 <span class="blue-text">건너뛰고</span> 다음 반복 진행 |

---

## 2.4 종합 예제

### 예제 1: for + if + continue (3의 배수 제외 합계)

```java
public class Main {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 1; i <= 10; i++) {
            if (i % 3 == 0)
                continue;  // 3의 배수는 건너뛰기
            sum += i;
        }
        System.out.println("합계: " + sum);
    }
}
```

**실행 결과:**
```
합계: 37
```

**해설:** 1~10 중 3, 6, 9를 제외한 나머지 합계 (1+2+4+5+7+8+10 = 37)

---

### 예제 2: while + if + break (누적 합이 100 이상이면 종료)

```java
public class Main {
    public static void main(String[] args) {
        int i = 0, sum = 0;
        while (i <= 100) {
            i++;
            sum += i;
            if (sum >= 100)
                break;  // 합이 100 이상이면 종료
        }
        System.out.println("i=" + i + ", sum=" + sum);
    }
}
```

**실행 결과:**
```
i=14, sum=105
```

**해설:** 1+2+3+...+14 = 105 (처음으로 100 이상이 되는 시점)

---

### 예제 3: for + switch (요일별 메시지)

```java
public class Main {
    public static void main(String[] args) {
        for (int day = 1; day <= 3; day++) {
            switch (day) {
                case 1:
                    System.out.print("월 ");
                    break;
                case 2:
                    System.out.print("화 ");
                    break;
                case 3:
                    System.out.print("수 ");
                    break;
            }
        }
    }
}
```

**실행 결과:**
```
월 화 수
```

---

### 예제 4: do-while + if (입력값 검증 시뮬레이션)

```java
public class Main {
    public static void main(String[] args) {
        int[] inputs = {-1, 0, 5};  // 시뮬레이션용 입력값
        int idx = 0, value;

        do {
            value = inputs[idx++];
            if (value <= 0) {
                System.out.println("유효하지 않은 값: " + value);
            } else {
                System.out.println("유효한 값: " + value);
            }
        } while (value <= 0 && idx < inputs.length);
    }
}
```

**실행 결과:**
```
유효하지 않은 값: -1
유효하지 않은 값: 0
유효한 값: 5
```

**해설:** do-while은 조건과 관계없이 최소 1회 실행됨

---

## 2.5 코드 해석 연습

### 예제 문제 1: switch + for (점수별 등급 분류)

```java
public class Solution {
    public static void main(String[] args) {
        int[] points = { 72, 88, 45, 91, 67 };
        char level;
        String msg = "Grade";

        for (int k = 0; k < 5; k++) {
            switch (points[k] / 10) {
                case 10:
                case 9:
                    level = 'A';
                    break;
                case 8:
                    level = 'B';
                    break;
                case 7:
                    level = 'C';
                    break;
                default:
                    level = 'F';
            }

            if (level != 'F')
                System.out.printf("%d is %c %s\n",
                    k + 1, level, msg);
        }
    }
}
```

**코드 해설:**
- `points[k] / 10`: 점수를 10으로 나눈 몫으로 등급 판별
- case 10, 9: 90점 이상 → 'A'
- case 8: 80점대 → 'B'
- case 7: 70점대 → 'C'
- default: 그 외 → 'F'
- level이 'F'가 아닐 때만 출력

| k | points[k] | points[k]/10 | level | 출력 |
|---|-----------|--------------|-------|------|
| 0 | 72 | 7 | 'C' | 1 is C Grade |
| 1 | 88 | 8 | 'B' | 2 is B Grade |
| 2 | 45 | 4 | 'F' | (출력 없음) |
| 3 | 91 | 9 | 'A' | 4 is A Grade |
| 4 | 67 | 6 | 'F' | (출력 없음) |

**실행 결과:**
```
1 is C Grade
2 is B Grade
4 is A Grade
```

---

### 예제 문제 2: while + for (문자열 역순 출력)

```java
public class Solution {
    public static void main(String[] args) {
        String word = "hello";
        int nums[] = { 5, 4, 3, 2, 1 };
        char chars[] = new char[5];
        int idx = 0;

        while (idx < word.length()) {
            chars[idx] = word.charAt(idx);
            idx++;
        }

        for (int n : nums) {
            idx--;
            System.out.print(chars[idx]);
            System.out.print(n + " ");
        }
    }
}
```

**코드 해설:**
- `word.charAt(idx)`: 문자열의 idx번째 문자 반환
- while문: 문자열을 문자 배열로 복사 (chars[] = {'h','e','l','l','o'})
- 향상된 for문: nums 배열의 값을 n에 순서대로 대입
- idx를 감소시키며 chars 배열을 역순으로 출력

| n | idx (감소 후) | chars[idx] | 출력 |
|---|---------------|------------|------|
| 5 | 4 | 'o' | o5 |
| 4 | 3 | 'l' | l4 |
| 3 | 2 | 'l' | l3 |
| 2 | 1 | 'e' | e2 |
| 1 | 0 | 'h' | h1 |

**실행 결과:**
```
o5 l4 l3 e2 h1
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">charAt() 메소드</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
<code>charAt(index)</code>는 문자열에서 index 위치의 문자를 반환합니다. 인덱스는 0부터 시작합니다.
</p>
</div>

---

# PART 3. Java의 클래스

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
클래스는 객체를 만들기 위한 설계도입니다. 클래스의 구성 요소와 객체 생성 과정을 정확히 이해하세요.
</p>
</div>

## 3.1 클래스와 객체

<span class="blue-text">클래스(Class)</span>는 객체를 정의하는 틀입니다. <span class="blue-text">객체(Object)</span>는 클래스로부터 생성된 실체입니다.

```java
public class Person {
    String name;  // 멤버 변수
    int age;

    void introduce() {  // 메서드
        System.out.println("이름: " + name);
    }
}

// 객체 생성
Person p1 = new Person();
p1.name = "홍길동";
```

---

## 3.2 생성자(Constructor)

<span class="blue-text">생성자</span>는 객체가 생성될 때 자동으로 호출되는 특수한 메서드입니다.

- 클래스 이름과 동일
- 반환형이 없음 (void도 쓰지 않음)

```java
public class Person {
    String name;

    public Person(String name) {
        this.name = name;  // this: 현재 객체 참조
    }
}
```

### 생성자 오버로딩

매개변수의 개수나 타입이 다른 여러 생성자를 정의할 수 있습니다.

---

## 3.3 접근 제어자

| 접근 제어자 | 같은 클래스 | 같은 패키지 | 자식 클래스 | 전체 |
|------------|:----------:|:----------:|:----------:|:----:|
| `public` | ✓ | ✓ | ✓ | ✓ |
| `protected` | ✓ | ✓ | ✓ | ✗ |
| `(default)` | ✓ | ✓ | ✗ | ✗ |
| `private` | ✓ | ✗ | ✗ | ✗ |

---

## 3.4 상속(Inheritance)

<span class="blue-text">상속</span>은 기존 클래스의 속성과 기능을 새로운 클래스가 물려받는 것입니다.

```java
class Animal {
    void eat() { System.out.println("먹습니다."); }
}

class Dog extends Animal {
    void bark() { System.out.println("멍멍"); }
}
```

### super 키워드

<span class="yellow-code">super</span>는 부모 클래스를 가리키는 참조 변수입니다.

### 메서드 오버라이딩

부모 클래스의 메서드를 자식 클래스에서 재정의합니다.

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">오버로딩 vs 오버라이딩</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <strong>오버로딩(Overloading)</strong>: 같은 클래스에서 <span class="blue-text">같은 이름</span>의 메서드를 매개변수를 다르게 하여 여러 개 정의<br>
• <strong>오버라이딩(Overriding)</strong>: 상속 관계에서 부모 메서드를 자식이 <span class="green-text">재정의</span>
</p>
</div>

---

## 3.5 코드 해석 연습

### 예제 문제 1: 클래스와 메서드 호출

```java
class Calculator {
    int base = 5;
    int compute(int x, int y) {
        return x + y + base;
    }
}

public class Solution {
    public static void main(String[] args) {
        int a = 7, b = 3, result;
        Calculator calc = new Calculator();
        result = calc.compute(a, b);
        System.out.print(result);
    }
}
```

**코드 해설:**
1. Calculator 클래스에 base=5와 compute 메서드 정의
2. main에서 Calculator 객체 생성
3. compute(7, 3) 호출 → 7 + 3 + 5 = 15

**실행 결과:**
```
15
```

---

### 예제 문제 2: 상속과 오버라이딩

```java
class Base {
    Base() {
        System.out.print('X');
        this.show();
    }
    void show() {
        System.out.print('Y');
    }
}

class Derived extends Base {
    Derived() {
        super();
        System.out.print('Z');
    }
    void show() {
        System.out.print('W');
    }
    void show(int n) {
        System.out.print(n);
    }
}

public class Solution {
    public static void main(String[] args) {
        int n = 5;
        Derived obj = new Derived();
        obj.show(n);
    }
}
```

**실행 흐름:**
1. `Derived obj = new Derived()` → Derived 생성자 호출
2. `super()` → Base 생성자 호출
3. Base 생성자에서 'X' 출력
4. `this.show()` → 오버라이딩된 Derived의 show() 실행 → 'W' 출력
5. Base 생성자 종료 → Derived 생성자로 복귀
6. 'Z' 출력
7. main으로 복귀 → `obj.show(5)` → 5 출력

**실행 결과:**
```
XWZ5
```

---

# PART 4. Java의 활용

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
추상 클래스와 인터페이스의 차이점과 사용 목적을 명확히 이해하세요.
</p>
</div>

## 4.1 추상 클래스 (Abstract Class)

<span class="blue-text">추상 클래스</span>는 하나 이상의 추상 메서드를 포함하는 클래스입니다.

```java
abstract class Animal {
    abstract void sound();  // 추상 메서드
    void eat() { System.out.println("먹습니다."); }  // 일반 메서드
}

class Dog extends Animal {
    void sound() { System.out.println("멍멍"); }
}
```

**특징:**
- <span class="yellow-code">abstract</span> 키워드 사용
- <span class="red-text">직접 객체 생성 불가</span>
- 추상 메서드는 자식 클래스에서 반드시 구현

---

## 4.2 인터페이스 (Interface)

<span class="blue-text">인터페이스</span>는 모든 메서드가 추상 메서드인 일종의 추상 클래스입니다.

```java
interface Flyable {
    void fly();
}

interface Swimmable {
    void swim();
}

class Duck implements Flyable, Swimmable {
    public void fly() { System.out.println("날아갑니다."); }
    public void swim() { System.out.println("수영합니다."); }
}
```

**특징:**
- <span class="yellow-code">interface</span> 키워드로 선언
- <span class="yellow-code">implements</span> 키워드로 구현
- <span class="green-text">다중 구현 가능</span>

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">추상 클래스 vs 인터페이스</strong>
</div>
<table style="width: 100%; border-collapse: collapse; font-size: 0.9rem;">
<tr style="background-color: #f9fafb;">
<th style="border: 1px solid #e5e7eb; padding: 8px;">구분</th>
<th style="border: 1px solid #e5e7eb; padding: 8px;">추상 클래스</th>
<th style="border: 1px solid #e5e7eb; padding: 8px;">인터페이스</th>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">키워드</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">abstract class</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">interface</td>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">구현 키워드</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">extends</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">implements</td>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">다중 상속</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;"><span class="red-text">불가</span></td>
<td style="border: 1px solid #e5e7eb; padding: 8px;"><span class="green-text">가능</span></td>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">일반 메서드</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">가능</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">불가</td>
</tr>
</table>
</div>

---

## 4.3 배열의 활용

### 1차원 배열

```java
int[] arr = new int[5];
int[] arr2 = {1, 2, 3, 4, 5};
```

### 2차원 배열

```java
int[][] matrix = new int[3][4];
int[][] matrix2 = { {1, 2, 3}, {4, 5, 6} };
```

---

## 4.4 코드 해석 연습

### 예제 문제 1: 추상 클래스와 형 변환

```java
abstract class Pet {
    String desc = " is pet";
    abstract void greet();
    void info() {
        System.out.println("Pet Info");
    }
}

class Cat extends Pet {
    Cat() {
        greet();
    }
    void greet() {
        System.out.println("Cat" + desc);
    }
    void meow() {
        System.out.println("meow~");
    }
}

public class Solution {
    public static void main(String[] args) {
        Pet p = new Cat();
        p.info();
    }
}
```

**실행 흐름:**
1. `Pet p = new Cat()` → Cat 생성자 호출
2. Cat 생성자에서 `greet()` 호출 → "Cat is pet" 출력
3. main으로 복귀 → `p.info()` 호출 → "Pet Info" 출력

**실행 결과:**
```
Cat is pet
Pet Info
```

---

### 예제 문제 2: 인터페이스와 다형성

```java
interface Calculator {
    int compute(int x, int y);
}

class Plus implements Calculator {
    public int compute(int x, int y) {
        return x + y;
    }
}

class Minus implements Calculator {
    public int compute(int x, int y) {
        return x - y;
    }
}

class Multi implements Calculator {
    public int compute(int x, int y) {
        return x * y;
    }
}

public class Solution {
    public static void main(String[] args) {
        int a = 8, b = 3;
        Calculator plus = new Plus();
        Calculator minus = new Minus();
        Calculator multi = new Multi();
        System.out.print(plus.compute(a, b) + ", ");
        System.out.print(minus.compute(a, b) + ", ");
        System.out.print(multi.compute(a, b));
    }
}
```

**연산 결과:**
- plus.compute(8, 3) → 11
- minus.compute(8, 3) → 5
- multi.compute(8, 3) → 24

**실행 결과:**
```
11, 5, 24
```

---

# 연습문제

## Part 1 - 데이터 입·출력

<div class="quiz-number">문제 1</div><strong>다음 Java 코드를 분석하여 출력되는 값을 쓰시오.</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Exam01 {
    public static void main(String[] args) {
        int m = 15, n = 5, o = 28;
        m /= n;
        n -= m;
        o %= n;
        System.out.printf("%d, %d, %d\n", m, n, o);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_io"
   code_html=code_block1
   answer="3, 2, 0"
   tags="데이터 입출력"
%}

---

<div class="quiz-number">문제 2</div><strong>다음은 두 정수를 입력받아 차를 출력하는 Java 코드이다. 빈칸에 공통으로 들어갈 적합한 클래스명을 쓰시오.</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>import java.util.(      );

public class Exam02 {
    public static void main(String args[]) {
        (      ) input = new (      )(System.in);
        int first = input.nextInt();
        int second = input.nextInt();
        System.out.printf("%d", first - second);
        input.close();
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_io"
   code_html=code_block2
   answer="Scanner"
   tags="데이터 입출력"
%}

---

<div class="quiz-number">문제 3</div><strong>다음 Java 코드를 분석하여 출력되는 값을 쓰시오.</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Exam03 {
    public static void main(String[] args) {
        int oct = 023;
        int dec = 23;
        int hex = 0x23;
        int sum = oct + dec + hex;
        System.out.printf("%d, %d, %d, %d\n", oct, dec, hex, sum);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_io"
   code_html=code_block3
   answer="19, 23, 35, 77"
   tags="데이터 입출력"
%}

---

<div class="quiz-number">문제 4</div><strong>다음 Java 코드를 분석하여 출력되는 값을 쓰시오.</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Exam04 {
    public static void main(String[] args) {
        int out, low = 30, high = 60, mid = 50;
        out = low > high ? high++ : --mid;
        System.out.printf("%d, %d, %d\n", out, high, mid);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_io"
   code_html=code_block4
   answer="49, 60, 49"
   tags="데이터 입출력"
%}

---

<div class="quiz-number">문제 5</div><strong>다음 Java 코드를 분석하여 출력되는 값을 쓰시오.</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Exam05 {
    public static void main(String[] args) {
        int p = 9, q = 4, r = 3;
        boolean check1, check2;

        check1 = p > 8 && q != 0;
        check2 = q < 4 || r > 6;

        System.out.printf("%b, %b\n", check1, check2);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_io"
   code_html=code_block5
   answer="true, false"
   tags="데이터 입출력"
%}

---

<div class="quiz-number">문제 6</div><strong>다음 Java 코드를 분석하여 출력되는 값을 쓰시오.</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Exam06 {
    public static void main(String[] args) {
        int w = 5, x = 6, y = 5, z = 7;

        if ((w == 4 | w == y) & !(y > z) & (3 == x ^ y != z)) {
            w = x + y;
            if (10 == x ^ y != w)
                System.out.println(w);
            else
                System.out.println(x);
        } else {
            w = y + z;
            if (10 == y ^ z != w)
                System.out.println(w);
            else
                System.out.println(z);
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_io"
   code_html=code_block6
   answer="11"
   tags="데이터 입출력"
%}

---

## Part 2 - 제어문

<div class="quiz-number">문제 7</div><strong>다음 Java 코드를 분석하여 출력되는 값을 쓰시오.</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Exam07 {
    public static void main(String[] args) {
        int acc = 0;
        for (int i = 1; i <= 15; i++) {
            if (i % 5 == 0)
                continue;
            acc += i;
        }
        System.out.println(acc);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7_control"
   code_html=code_block7
   answer="90"
   tags="제어문"
%}

---

<div class="quiz-number">문제 8</div><strong>다음 Java 코드를 분석하여 출력되는 값을 쓰시오.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Exam08 {
    public static void main(String[] args) {
        int level = 2;
        switch (level) {
            case 1:
                System.out.print("A");
            case 2:
                System.out.print("B");
            case 3:
                System.out.print("C");
            case 4:
                System.out.print("D");
                break;
            default:
                System.out.print("F");
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8_control"
   code_html=code_block8
   answer="BCD"
   tags="제어문"
%}

---

<div class="quiz-number">문제 9</div><strong>다음 Java 코드를 분석하여 출력되는 값을 쓰시오.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Exam09 {
    public static void main(String[] args) {
        int acc = 0;
        for (int i = 1; i <= 30; i++) {
            acc += i;
            if (acc >= 40)
                break;
        }
        System.out.println(acc);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_control"
   code_html=code_block9
   answer="45"
   tags="제어문"
%}

---

<div class="quiz-number">문제 10</div><strong>다음은 변수 val에 저장된 10진수를 2진수로 변환하는 Java 코드이다. 코드를 분석하여 빈칸 ①, ②에 들어갈 알맞은 답을 쓰시오. (①, ②를 쉼표로 구분하여 작성)</strong>

{% capture code_block10 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Exam10 {
    public static void main(String[] args) {
        int bits[] = new int[8];
        int pos = 0;
        int val = 11;

        while (( ① )) {
            bits[pos++] = ( ② );
            val /= 2;
        }

        for (pos = 7; pos >= 0; pos--)
            System.out.print(bits[pos]);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz10_control"
   code_html=code_block10
   answer="val > 0, val % 2"
   tags="제어문"
%}

---

<div class="quiz-number">문제 11</div><strong>다음 Java 프로그램을 분석하여 괄호 ①, ②에 들어갈 알맞은 값을 쓰시오. (①, ②를 쉼표로 구분하여 작성)</strong>

{% capture code_block11 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int matrix[][] = new int[( ① )][( ② )];

        for (int r = 0; r < 4; r++) {
            for (int c = 0; c < 3; c++) {
                matrix[r][c] = c * 4 + r + 1;
                System.out.print(matrix[r][c] + " ");
            }
            System.out.println();
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_control"
   code_html=code_block11
   answer="4, 3"
   tags="제어문"
%}

---

<div class="quiz-number">문제 12</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block12 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int x = 0;
        int y = 40;
        int z = 25;

        if ((x > y ? y : x) != 0)
            y = y << 2;
        else
            z = z << 2;

        System.out.printf("%d", y + z);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz12_control"
   code_html=code_block12
   answer="140"
   tags="제어문"
%}

---

<div class="quiz-number">문제 13</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block13 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int cnt = 0, total = 0;
        while (cnt < 8) {
            cnt++;
            if (cnt % 2 == 1)
                continue;
            total += cnt;
        }
        System.out.println(total);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz13_control"
   code_html=code_block13
   answer="20"
   tags="제어문"
%}

---

<div class="quiz-number">문제 14</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block14 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int val = 5;
        switch (2) {
            case 1: val += 2;
            case 2: val = 0;
            case 3: val += 5;
            case 4: val -= 8;
            default: val--;
        }
        System.out.printf("%d", val);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz14_control"
   code_html=code_block14
   answer="-4"
   tags="제어문"
%}

---

<div class="quiz-number">문제 15</div><strong>다음은 2진수 110101을 10진수로 변환하는 Java 프로그램이다. 프로그램을 분석하여 괄호 ①, ②에 들어갈 알맞은 답을 쓰시오. (①, ②를 쉼표로 구분하여 작성)</strong>

{% capture code_block15 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int binary = 110101;
        int weight = 1;
        int decimal = 0;

        while (true) {
            if (binary == 0) break;
            decimal = decimal + (binary ( ① ) ( ② )) * weight;
            weight = weight * 2;
            binary = binary / 10;
        }

        System.out.printf("%d", decimal);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz15_control"
   code_html=code_block15
   answer="%, 10"
   tags="제어문"
%}

---

<div class="quiz-number">문제 16</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block16 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int sum, count = 0;
        for (int n = 2; n <= 10; n++) {
            sum = 0;
            for (int d = 1; d <= n / 2; d++)
                if (n % d == 0)
                    sum = sum + d;

            if (sum == n)
                count++;
        }
        System.out.printf("%d", count);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz16_control"
   code_html=code_block16
   answer="1"
   tags="제어문"
%}

---

<div class="quiz-number">문제 17</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block17 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int rank[] = new int[5];
        int score[] = { 85, 45, 90, 65, 30 };

        for (int i = 0; i < 5; i++) {
            rank[i] = 1;
            for (int j = 0; j < 5; j++)
                if (score[i] < score[j])
                    rank[i]++;
        }

        for (int k = 0; k < 5; k++)
            System.out.print(rank[k]);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz17_control"
   code_html=code_block17
   answer="21345"
   tags="제어문"
%}

---

<div class="quiz-number">문제 18</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block18 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int max = 0;
        for (int n = 1; n < 500; n++) {
            if (n % 4 == 0 && n % 5 == 0)
                max = n;
        }
        System.out.print(max);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz18_control"
   code_html=code_block18
   answer="480"
   tags="제어문"
%}

---

<div class="quiz-number">문제 19</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block19 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int sum, num;
        for (sum = 0, num = 1; num <= 4; num++) {
            sum += num;
            System.out.print(num);
            if (num == 4) {
                System.out.print("=");
                System.out.print(sum);
            }
            else
                System.out.print("+");
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz19_control"
   code_html=code_block19
   answer="1+2+3+4=10"
   tags="제어문"
%}

---

<div class="quiz-number">문제 20</div><strong>다음 Java 프로그램을 실행시킨 결과가 "32145"일 때, &lt;처리조건&gt;을 참고하여 괄호에 들어갈 알맞은 식을 쓰시오.</strong>

{% capture code_block20 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int[] arr = { 5, 4, 1, 2, 3 };
        for (int i = 0; i < 5; i++)
            System.out.printf("%d", (          ));
    }
}

&lt;처리조건&gt;
괄호의 식에 사용할 문자는 다음으로 제한한다.
· arr, i
· +, -, /, *, %
· 0~9, (, ), [, ]</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz20_control"
   code_html=code_block20
   answer="arr[(i+2)%5] 또는 arr[4-i]"
   tags="제어문"
%}

---

<div class="quiz-number">문제 21</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오. (출력 결과를 줄바꿈 없이 공백으로 구분하여 작성)</strong>

{% capture code_block21 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int data[][] = {% raw %}{ { 10, 20 },
                         { 30, 40, 50 } }{% endraw %};

        System.out.println(data[0].length);
        System.out.println(data[1].length);
        System.out.println(data[0][0]);
        System.out.println(data[1][1]);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz21_control"
   code_html=code_block21
   answer="2 3 10 40"
   tags="제어문"
%}

---

<div class="quiz-number">문제 22</div><strong>다음은 정수를 뒤집어 출력하는 Java 프로그램이다. 예를 들어 5678의 역순은 8765이다. 단, 5670처럼 0으로 끝나는 정수는 고려하지 않는다. 프로그램을 분석하여 괄호(①~③)에 들어갈 알맞은 연산자를 쓰시오. (①, ②, ③을 쉼표로 구분하여 작성)</strong>

{% capture code_block22 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int num = 5678;
        int base = 10, rev = 0;

        while (num ( ① ) 0) {
            rev = rev * base;
            rev = rev + num ( ② ) base;
            num = num ( ③ ) base;
        }

        System.out.printf("%d", rev);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz22_control"
   code_html=code_block22
   answer=">, %, /"
   tags="제어문"
%}

---

## Part 3 - Java의 클래스

<div class="quiz-number">문제 23</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block23 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Parent {
    int value;
    public Parent(int v) {
        value = v;
    }
    public void display() {
        System.out.println("value=" + value);
    }
}

class Child extends Parent {
    public Child(int v) {
        super(v);
        value = value + 5;
    }
}

public class Solution {
    public static void main(String[] args) {
        Parent obj = new Child(15);
        obj.display();
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz23_class"
   code_html=code_block23
   answer="value=20"
   tags="클래스"
%}

---

<div class="quiz-number">문제 24</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block24 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Vehicle {
    void run() {
        System.out.print("Vehicle ");
    }
}

class Bike extends Vehicle {
    void run() {
        System.out.print("Bike ");
    }
}

public class Solution {
    public static void main(String[] args) {
        Vehicle v1 = new Vehicle();
        Vehicle v2 = new Bike();
        v1.run();
        v2.run();
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz24_class"
   code_html=code_block24
   answer="Vehicle Bike"
   tags="클래스"
%}

---

<div class="quiz-number">문제 25</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block25 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Rectangle {
    int w, h;

    Rectangle() {
        this(5, 10);
    }
    Rectangle(int w, int h) {
        this.w = w;
        this.h = h;
    }
    int getArea() {
        return w * h;
    }
}

public class Solution {
    public static void main(String[] args) {
        Rectangle r1 = new Rectangle();
        Rectangle r2 = new Rectangle(4, 6);
        System.out.println(r1.getArea() + r2.getArea());
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz25_class"
   code_html=code_block25
   answer="74"
   tags="클래스"
%}

---

<div class="quiz-number">문제 26</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block26 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Base {
    int val;
    public Base(int val) { this.val = val; }
    void show() { System.out.println("val=" + val); }
}

class Sub extends Base {
    public Sub(int val) {
        super(val);
        super.show();
    }
}

public class Solution {
    public static void main(String[] args) {
        Sub obj = new Sub(25);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz26_class"
   code_html=code_block26
   answer="val=25"
   tags="클래스"
%}

---

<div class="quiz-number">문제 27</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block27 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    static int[] makeArray() {
        int arr[] = new int[4];
        int size = arr.length;
        for(int i = 0; i < size; i++)
            arr[i] = i * 2;
        return arr;
    }

    public static void main(String[] args) {
        int data[] = makeArray();
        for(int i = 0; i < data.length; i++)
            System.out.print(data[i] + " ");
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz27_class"
   code_html=code_block27
   answer="0 2 4 6"
   tags="클래스"
%}

---

<div class="quiz-number">문제 28</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block28 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Counter {
    int num;
    public Counter(int num) {
        this.num = num;
    }

    public int calc() {
        int sum = 1;
        for(int i = 1; i < num; i++)
            sum += num * i;
        return num + sum;
    }
}

public class Solution {
    public static void main(String args[]) {
        Counter obj = new Counter(4);
        obj.num = 3;
        int result = obj.calc();
        System.out.print(obj.num + result);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz28_class"
   code_html=code_block28
   answer="15"
   tags="클래스"
%}

---

<div class="quiz-number">문제 29</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block29 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Data {
    int x;
    int y;
}

public class Solution {
    static void modify1(Data d) {
        d.x += 5;
    }

    static void modify2(Data d) {
        d.x += d.y;
    }

    public static void main(String args[]) {
        Data d = new Data();
        d.x = 50;
        modify1(d);
        d.y = d.x;
        modify2(d);
        System.out.printf("%d", d.x);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz29_class"
   code_html=code_block29
   answer="110"
   tags="클래스"
%}

---

<div class="quiz-number">문제 30</div><strong>다음 Java 프로그램의 실행 순서를 번호로 나열하시오. (쉼표로 구분하여 작성, 중복 번호 제외)</strong>

{% capture code_block30 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Super {
    int a, b;

① Super(int a, int b) {
        this.a = a;
        this.b = b;
    }

② int getSum() {
        return a + b;
    }
}

class Derived extends Super {
    int a;

③ Derived(int a) {
        super(a + 2, a);
        this.a = a;
    }

④ int getSum(int n) {
        return super.getSum() + n;
    }
}

public class Solution {
⑤ public static void main(String[] args) {
⑥ Super s = new Derived(5);
⑦ System.out.println(s.getSum());
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz30_class"
   code_html=code_block30
   answer="5, 6, 3, 1, 7, 2"
   tags="클래스"
%}

---

## Part 4 - Java의 활용

<div class="quiz-number">문제 31</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block31 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>abstract class Figure {
    abstract void render();
}

class Triangle extends Figure {
    void render() {
        System.out.print("Triangle ");
    }
}

class Rect extends Figure {
    void render() {
        System.out.print("Rect ");
    }
}

public class Solution {
    public static void main(String[] args) {
        Figure[] figs = new Figure[2];
        figs[0] = new Triangle();
        figs[1] = new Rect();
        for (Figure f : figs) {
            f.render();
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz31_java"
   code_html=code_block31
   answer="Triangle Rect"
   tags="Java 활용"
%}

---

<div class="quiz-number">문제 32</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block32 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>interface Executable {
    void run();
}

interface Displayable {
    void show();
}

class Worker implements Executable, Displayable {
    public void run() {
        System.out.print("R");
    }
    public void show() {
        System.out.print("S");
    }
}

public class Solution {
    public static void main(String[] args) {
        Worker w = new Worker();
        w.run();
        w.show();
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz32_java"
   code_html=code_block32
   answer="RS"
   tags="Java 활용"
%}

---

<div class="quiz-number">문제 33</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block33 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int[][] grid = {% raw %}{{3, 6, 9}, {12, 15, 18}, {21, 24, 27}}{% endraw %};
        int sum = 0;
        for (int i = 0; i < 3; i++) {
            sum += grid[i][i];
        }
        System.out.println(sum);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz33_java"
   code_html=code_block33
   answer="45"
   tags="Java 활용"
%}

---

<div class="quiz-number">문제 34</div><strong>다음 Java 프로그램을 분석하여 괄호에 들어갈 알맞은 키워드를 쓰시오.</strong>

{% capture code_block34 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Super {
    void display() { System.out.println("super"); }
}

class Sub extends Super {
    void display() { System.out.println("sub"); }
}

public class Solution {
    public static void main(String[] args) {
        Super s = (     ) Sub();
        s.display();
    }
}

// 출력: sub</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz34_java"
   code_html=code_block34
   answer="new"
   tags="Java 활용"
%}

---

<div class="quiz-number">문제 35</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block35 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Alpha {
    int calc(int n) {
        if(n <= 1) return n;
        return calc(n - 1) + calc(n - 2);
    }
}

class Beta extends Alpha {
    int calc(int n) {
        if(n <= 1) return n;
        return calc(n - 1) + calc(n - 3);
    }
}

public class Solution {
    public static void main(String[] args) {
        Alpha obj = new Beta();
        System.out.print(obj.calc(5));
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz35_java"
   code_html=code_block35
   answer="2"
   tags="Java 활용"
%}

---

<div class="quiz-number">문제 36</div><strong>다음 Java 프로그램을 분석하여 실행 결과를 쓰시오.</strong>

{% capture code_block36 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>abstract class Product {
    String type;
    abstract public String getType(String val);
    public String getType() {
        return "Product type : " + type;
    }
}

class Phone extends Product {
    private String type;

    public Phone(String val) {
        type = super.type = val;
    }

    public String getType(String val) {
        return "Phone type : " + val;
    }

    public String getType(byte[] val) {
        return "Phone type : " + val;
    }
}

public class Solution {
    public static void main(String[] args) {
        Product obj = new Phone("Galaxy");
        System.out.print(obj.getType());
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz36_java"
   code_html=code_block36
   answer="Product type : Galaxy"
   tags="Java 활용"
%}

---

<div class="quiz-number">문제 37</div><strong>다음 Java 프로그램의 실행 결과가 20이 나오도록 괄호에 들어갈 알맞은 키워드를 쓰시오.</strong>

{% capture code_block37 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>interface Calc {
    int add(int x, int y);
    default void greet() {
        System.out.print("Hello");
    }
}

class Adder (      ) Calc {
    public int add(int x, int y) {
        return x + y;
    }

    public void greet() {
        System.out.print("Hi");
    }
}

public class Solution {
    public static void main(String[] args) {
        int a = 12, b = 8;
        Calc c = new Adder();
        System.out.println(c.add(a, b));
        c.greet();
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz37_java"
   code_html=code_block37
   answer="implements"
   tags="Java 활용"
%}

---

# 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Part 1 - 데이터 입·출력</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>Scanner</strong>: 입력용 클래스, <code>nextInt()</code>로 정수 입력</li>
<li><strong>print/println/printf</strong>: 출력 함수들</li>
<li>8진수: 0으로 시작, 16진수: 0x로 시작</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Part 2 - 제어문</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>if/switch</strong>: 조건문 (switch의 break 주의!)</li>
<li><strong>for/while/do-while</strong>: 반복문</li>
<li><strong>break</strong>: 종료, <strong>continue</strong>: 건너뛰기</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Part 3 - 클래스</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>this</strong>: 현재 객체 참조</li>
<li><strong>super</strong>: 부모 클래스 참조</li>
<li><strong>오버로딩</strong>: 같은 이름, 다른 매개변수</li>
<li><strong>오버라이딩</strong>: 부모 메서드 재정의</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Part 4 - 추상 클래스/인터페이스</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>abstract class</strong>: 추상 클래스 (extends로 상속)</li>
<li><strong>interface</strong>: 인터페이스 (implements로 구현, 다중 구현 가능)</li>
</ul>

</div>

---
