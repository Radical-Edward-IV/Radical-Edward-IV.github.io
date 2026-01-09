---
layout: article
title: 2. 변수와 자료형, 연산자
permalink: /notes/kr/java-basic/chapter-02
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: Java 기초 과정 강의 노트, 변수 선언, 기본/참조 자료형, 형변환, 연산자(산술, 비교, 논리, 비트), 연산자 우선순위를 다룹니다.
keywords: "Java, 변수, 자료형, int, double, boolean, String, 형변환, 연산자, 산술연산자, 비교연산자, 논리연산자, 비트연산자"
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

## 변수 선언 및 초기화

### 변수란?

변수는 데이터를 저장하는 <span class="blue-text">메모리 공간</span>입니다. 값을 담는 상자라고 생각하면 쉽습니다.

```java
int age = 25;
//  ↑   ↑   ↑
// 자료형 변수명 값
```

- <span class="blue-text">자료형</span>: 변수에 저장될 데이터의 종류
- <span class="blue-text">변수명</span>: 변수를 식별하는 이름
- <span class="blue-text">값</span>: 변수에 저장되는 실제 데이터

### 변수명 규칙

**필수 규칙 (지키지 않으면 오류):**
- 문자, 숫자, 언더바(_), 달러($)만 사용 가능
- 숫자로 시작 불가
- 키워드(예약어) 사용 불가
- 대소문자 구분
- 공백 사용 불가

**권장 규칙 (관례):**
- 카멜 케이스(camelCase) 사용
- 의미있는 이름 사용

```java
// 올바른 변수명
int studentAge = 20;
double totalPrice = 15000.0;

// 잘못된 변수명
int 3number = 10;      // 숫자로 시작 (오류)
int my number = 5;     // 공백 포함 (오류)
int class = 100;       // 키워드 사용 (오류)
```

### 선언과 초기화

**선언 (Declaration):**

```java
int number;           // 변수 선언만
double price;
```

**초기화 (Initialization):**

```java
int number = 10;      // 선언과 동시에 초기화
double price = 5000.0;
```

**선언 후 초기화:**

```java
int number;
number = 10;          // 나중에 초기화
```

**여러 변수 선언:**

```java
int a, b, c;                    // 여러 변수 선언
int x = 10, y = 20, z = 30;     // 선언과 초기화
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">초기화하지 않은 지역 변수</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Java에서는 <span class="red-text">초기화하지 않은 지역 변수를 사용하면 컴파일 오류</span>가 발생합니다.
</p>
</div>

---

## 기본 자료형 (Primitive Types)

Java의 기본 자료형은 총 **8가지**입니다.

### 정수형

| 자료형 | 크기 | 값의 범위 |
|--------|------|-----------|
| `byte` | 1바이트 | -128 ~ 127 |
| `short` | 2바이트 | -32,768 ~ 32,767 |
| `int` | 4바이트 | 약 -21억 ~ 21억 |
| `long` | 8바이트 | 약 -9경 ~ 9경 |

```java
byte smallNumber = 100;
short temperature = -10;
int population = 50000000;
long distance = 384400000L;  // long은 L 붙이기
```

### 실수형

| 자료형 | 크기 | 정밀도 |
|--------|------|--------|
| `float` | 4바이트 | 소수점 7자리 |
| `double` | 8바이트 | 소수점 15자리 |

```java
float pi = 3.14f;              // float은 f 붙이기
double e = 2.718281828;
```

### 문자형

| 자료형 | 크기 | 값의 범위 |
|--------|------|-----------|
| `char` | 2바이트 | 유니코드 문자 |

```java
char grade = 'A';              // 작은따옴표
char koreanChar = '가';
```

### 논리형

| 자료형 | 크기 | 값의 범위 |
|--------|------|-----------|
| `boolean` | 1비트 | true, false |

```java
boolean isStudent = true;
boolean hasLicense = false;
```

---

## 참조 자료형 (Reference Types)

### String (문자열)

<span class="blue-text">String</span>은 문자열을 다루는 참조 자료형입니다.

```java
String name = "홍길동";
String greeting = "Hello, Java!";
String empty = "";              // 빈 문자열
```

### 기본 자료형 vs 참조 자료형

| 구분 | 기본 자료형 | 참조 자료형 |
|------|-------------|-------------|
| 종류 | byte, short, int, long, float, double, char, boolean | String, Array, Class 등 |
| 저장 위치 | 스택(Stack) | 힙(Heap) |
| 기본값 | 0, 0.0, false 등 | null |
| 크기 | 고정 | 가변 |

```java
// 기본 자료형
int num = 10;          // 값 자체를 저장

// 참조 자료형
String str = "Hello";  // 객체의 주소를 저장
```

### String 연결

```java
String firstName = "Gil-dong";
String lastName = "Hong";
String fullName = lastName + " " + firstName;

System.out.println(fullName);  // Hong Gil-dong
```

### String과 숫자의 결합

```java
int age = 25;
String message = "나이: " + age;  // "나이: 25"

String result = "10" + 20;        // "1020" (문자열 연결)
```

---

## 형변환 및 타입 캐스팅

### 자동 형변환 (Implicit Casting)

작은 타입에서 큰 타입으로 변환할 때는 자동으로 형변환됩니다.

```
byte → short → int → long → float → double
         char →
```

```java
int intValue = 100;
long longValue = intValue;       // int → long (자동)
double doubleValue = intValue;   // int → double (자동)
```

### 강제 형변환 (Explicit Casting)

큰 타입에서 작은 타입으로 변환할 때는 명시적으로 형변환해야 합니다.

```java
double pi = 3.14159;
int intPi = (int) pi;            // 3 (소수점 이하 버림)

long longValue = 1000L;
int intValue = (int) longValue;
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">데이터 손실 주의</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
강제 형변환 시 데이터 손실이 발생할 수 있습니다.<br>
• 실수 → 정수: 소수점 이하 버림<br>
• 큰 정수 → 작은 정수: 오버플로우 가능
</p>
</div>

### 연산 시 자동 형변환

```java
int a = 10;
double b = 3.0;
double result = a / b;      // int가 double로 자동 변환
System.out.println(result);  // 3.3333...

// 정수 나눗셈 주의!
int c = 10;
int d = 3;
double result2 = c / d;      // 3.0 (정수 나눗셈)
double result3 = (double) c / d;  // 3.333... (실수 나눗셈)
```

### 실습: 형변환

```java
public class CastingTest {
    public static void main(String[] args) {
        // 자동 형변환
        int num = 100;
        double dNum = num;
        System.out.println("자동 형변환: " + dNum);  // 100.0

        // 강제 형변환
        double pi = 3.14159;
        int intPi = (int) pi;
        System.out.println("강제 형변환: " + intPi);  // 3

        // 연산 시 형변환
        int a = 10, b = 3;
        System.out.println("정수 나눗셈: " + (a / b));        // 3
        System.out.println("실수 나눗셈: " + ((double)a / b));  // 3.333...
    }
}
```

---

## 산술 연산자

산술 연산자는 수학적 계산을 수행합니다.

| 연산자 | 의미 | 예시 | 결과 |
|--------|------|------|------|
| `+` | 덧셈 | `5 + 3` | 8 |
| `-` | 뺄셈 | `5 - 3` | 2 |
| `*` | 곱셈 | `5 * 3` | 15 |
| `/` | 나눗셈 | `5 / 3` | 1 (정수 나눗셈) |
| `%` | 나머지 | `5 % 3` | 2 |

### 기본 산술 연산

```java
int a = 10, b = 3;

System.out.println(a + b);  // 13
System.out.println(a - b);  // 7
System.out.println(a * b);  // 30
System.out.println(a / b);  // 3 (정수 나눗셈)
System.out.println(a % b);  // 1 (나머지)
```

### 정수 나눗셈 vs 실수 나눗셈

```java
int x = 10, y = 3;
System.out.println(x / y);           // 3 (정수 나눗셈)
System.out.println((double)x / y);   // 3.333... (실수 나눗셈)
```

### 증감 연산자

| 연산자 | 의미 | 설명 |
|--------|------|------|
| `++` | 증가 | 1 증가 |
| `--` | 감소 | 1 감소 |

```java
int num = 10;

// 후위 증감 (사용 후 증가)
System.out.println(num++);  // 10 출력, 그 후 11로 증가
System.out.println(num);    // 11

// 전위 증감 (증가 후 사용)
System.out.println(++num);  // 12로 증가, 그 후 12 출력
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">증감 연산자 차이</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <code>num++</code>: 현재 값 사용 후 증가<br>
• <code>++num</code>: 먼저 증가 후 사용
</p>
</div>

### 복합 대입 연산자

| 연산자 | 의미 | 예시 | 동일한 표현 |
|--------|------|------|-------------|
| `+=` | 덧셈 후 대입 | `a += 3` | `a = a + 3` |
| `-=` | 뺄셈 후 대입 | `a -= 3` | `a = a - 3` |
| `*=` | 곱셈 후 대입 | `a *= 3` | `a = a * 3` |
| `/=` | 나눗셈 후 대입 | `a /= 3` | `a = a / 3` |
| `%=` | 나머지 후 대입 | `a %= 3` | `a = a % 3` |

```java
int num = 10;
num += 5;   // num = num + 5;  → 15
num *= 2;   // num = num * 2;  → 30
num -= 8;   // num = num - 8;  → 22
```

---

## 비교 연산자

비교 연산자는 두 값을 비교하여 <span class="blue-text">boolean</span> 값(true/false)을 반환합니다.

| 연산자 | 의미 | 예시 | 결과 |
|--------|------|------|------|
| `==` | 같다 | `5 == 5` | true |
| `!=` | 같지 않다 | `5 != 3` | true |
| `>` | 크다 | `5 > 3` | true |
| `<` | 작다 | `5 < 3` | false |
| `>=` | 크거나 같다 | `5 >= 5` | true |
| `<=` | 작거나 같다 | `5 <= 3` | false |

### 비교 연산 예제

```java
int a = 10, b = 20;

System.out.println(a == b);  // false
System.out.println(a != b);  // true
System.out.println(a > b);   // false
System.out.println(a < b);   // true
System.out.println(a >= 10); // true
System.out.println(a <= 5);  // false
```

### 문자열 비교 주의

```java
String str1 = "Hello";
String str2 = "Hello";
String str3 = new String("Hello");

System.out.println(str1 == str2);        // true
System.out.println(str1 == str3);        // false (주소 비교)
System.out.println(str1.equals(str3));   // true (내용 비교)
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">문자열 비교</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
문자열은 <code>==</code> 대신 <span class="green-text">.equals()</span> 메서드를 사용하세요!
</p>
</div>

---

## 논리 연산자

논리 연산자는 boolean 값을 연산합니다.

| 연산자 | 의미 | 설명 |
|--------|------|------|
| `&&` | AND (그리고) | 둘 다 true일 때 true |
| `||` | OR (또는) | 하나라도 true면 true |
| `!` | NOT (부정) | true ↔ false 반전 |

### AND 연산자 (&&)

```java
int age = 25;
boolean hasLicense = true;

boolean canDrive = (age >= 18) && hasLicense;
System.out.println(canDrive);  // true
```

**진리표:**

| A | B | A && B |
|---|---|--------|
| true | true | true |
| true | false | false |
| false | true | false |
| false | false | false |

### OR 연산자 (||)

```java
boolean isWeekend = true;
boolean isHoliday = false;

boolean canRest = isWeekend || isHoliday;
System.out.println(canRest);  // true
```

**진리표:**

| A | B | A \|\| B |
|---|---|--------|
| true | true | true |
| true | false | true |
| false | true | true |
| false | false | false |

### NOT 연산자 (!)

```java
boolean isRaining = false;
boolean isSunny = !isRaining;
System.out.println(isSunny);  // true
```

### 단축 평가 (Short-Circuit Evaluation)

```java
int x = 0;

// && 연산: 왼쪽이 false면 오른쪽은 평가하지 않음
if (x != 0 && 10 / x > 1) {  // x != 0이 false이므로 10/x는 실행 안 됨
    System.out.println("조건 만족");
}

// || 연산: 왼쪽이 true면 오른쪽은 평가하지 않음
if (x == 0 || 10 / x > 1) {  // x == 0이 true이므로 10/x는 실행 안 됨
    System.out.println("조건 만족");  // 출력됨
}
```

---

## 비트 연산자

비트 연산자는 비트 단위로 연산을 수행합니다.

| 연산자 | 의미 | 설명 |
|--------|------|------|
| `&` | AND | 둘 다 1이면 1 |
| `|` | OR | 하나라도 1이면 1 |
| `^` | XOR | 다르면 1, 같으면 0 |
| `~` | NOT | 비트 반전 |
| `<<` | 왼쪽 시프트 | 비트를 왼쪽으로 이동 |
| `>>` | 오른쪽 시프트 | 비트를 오른쪽으로 이동 (부호 유지) |
| `>>>` | 부호 없는 오른쪽 시프트 | 비트를 오른쪽으로 이동 (0으로 채움) |

### 비트 AND, OR, XOR

```java
int a = 12;  // 1100 (2진수)
int b = 10;  // 1010 (2진수)

System.out.println(a & b);  // 8  (1000)
System.out.println(a | b);  // 14 (1110)
System.out.println(a ^ b);  // 6  (0110)
```

### 비트 NOT

```java
int num = 5;        // 00000101
System.out.println(~num);  // -6 (11111010, 2의 보수)
```

### 비트 시프트

```java
int num = 8;  // 1000 (2진수)

System.out.println(num << 1);  // 16  (10000) - 왼쪽으로 1비트
System.out.println(num >> 1);  // 4   (100) - 오른쪽으로 1비트
System.out.println(num << 2);  // 32  (100000) - 왼쪽으로 2비트
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">✓</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">비트 시프트 활용</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <code>n << 1</code>은 <code>n * 2</code>와 같음<br>
• <code>n >> 1</code>은 <code>n / 2</code>와 같음
</p>
</div>

---

## 연산자 우선순위

연산자는 실행 순서가 정해져 있습니다.

| 우선순위 | 연산자 | 설명 |
|----------|--------|------|
| 1 | `()` | 괄호 |
| 2 | `!`, `~`, `++`, `--` | 단항 연산자 |
| 3 | `*`, `/`, `%` | 곱셈, 나눗셈, 나머지 |
| 4 | `+`, `-` | 덧셈, 뺄셈 |
| 5 | `<<`, `>>`, `>>>` | 시프트 |
| 6 | `<`, `<=`, `>`, `>=` | 비교 |
| 7 | `==`, `!=` | 같음, 다름 |
| 8 | `&` | 비트 AND |
| 9 | `^` | 비트 XOR |
| 10 | `|` | 비트 OR |
| 11 | `&&` | 논리 AND |
| 12 | `||` | 논리 OR |
| 13 | `?:` | 삼항 연산자 |
| 14 | `=`, `+=`, `-=`, `*=`, `/=`, `%=` | 대입 |

### 우선순위 예제

```java
int result1 = 5 + 3 * 2;        // 11 (곱셈 먼저)
int result2 = (5 + 3) * 2;      // 16 (괄호 먼저)

boolean result3 = 10 > 5 && 3 < 7;  // true
boolean result4 = 10 > 5 || 3 > 7;  // true

int result5 = 10 + 5 * 2 - 3;   // 17 (곱셈 → 덧셈 → 뺄셈)
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">가독성을 위해 괄호 사용</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
복잡한 연산식에서는 우선순위에 의존하기보다 <span class="green-text">괄호를 사용</span>하여 명확하게 표현하는 것이 좋습니다.
</p>
</div>

---

## 종합 실습

### 문제 1 - 산술 연산 (기초)

<div class="quiz-number">문제 1</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int a = 17;
        int b = 5;
        System.out.println(a % b);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="2"
   tags="연산자"
%}

---

### 문제 2 - 증감 연산자 (기초)

<div class="quiz-number">문제 2</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int num = 10;
        System.out.println(num++);
        System.out.println(num);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="10\n11|10 11"
   tags="연산자"
%}

---

### 문제 3 - 비교 연산자 (기초)

<div class="quiz-number">문제 3</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int age = 18;
        System.out.println(age >= 18);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="true"
   tags="연산자"
%}

---

### 문제 4 - 논리 연산자 (중급)

<div class="quiz-number">문제 4</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        boolean a = true;
        boolean b = false;
        System.out.println(a && b || !b);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="true"
   tags="연산자"
%}

---

### 문제 5 - 형변환과 연산 (중급)

<div class="quiz-number">문제 5</div><strong>다음 Java 프로그램의 실행 결과를 소수점 첫째 자리까지 작성하세요. (예: 3.3)</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int total = 250;
        int count = 3;
        double average = (double) total / count;
        System.out.printf("%.1f", average);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   code_html=code_block5
   answer="83.3"
   tags="연산자"
%}

---

### 문제 6 - 비트 연산자 (중급)

<div class="quiz-number">문제 6</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int num = 4;
        System.out.println(num << 2);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   code_html=code_block6
   answer="16"
   tags="연산자"
%}

---

### 문제 7 - 연산자 우선순위 (고급)

<div class="quiz-number">문제 7</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int result = 10 + 5 * 2 - 8 / 4;
        System.out.println(result);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7"
   code_html=code_block7
   answer="18"
   tags="연산자"
%}

---

### 문제 8 - 복합 문제 (고급)

<div class="quiz-number">문제 8</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int x = 10;
        int y = ++x + x++;
        System.out.println(y);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8"
   code_html=code_block8
   answer="22"
   tags="연산자"
%}

---

## 실전 프로그래밍

### 과제 1: 온도 변환기

화씨 온도를 섭씨로 변환하는 프로그램을 작성하세요.

**요구사항:**
- 화씨 온도를 변수에 저장 (예: 100.0)
- 공식: 섭씨 = (화씨 - 32) * 5 / 9
- 결과를 소수점 둘째 자리까지 출력

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">public class TemperatureConverter {
    public static void main(String[] args) {
        double fahrenheit = 100.0;
        double celsius = (fahrenheit - 32) * 5 / 9;

        System.out.printf("화씨 %.1f도는 섭씨 %.2f도입니다.", fahrenheit, celsius);
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>화씨 100.0도는 섭씨 37.78도입니다.
</code></pre>

</details>

---

### 과제 2: 짝수/홀수 판별

주어진 숫자가 짝수인지 홀수인지 판별하는 프로그램을 작성하세요.

**요구사항:**
- 정수를 변수에 저장 (예: 17)
- 나머지 연산자(%)를 사용하여 짝수/홀수 판별
- boolean 변수에 짝수 여부 저장
- 결과 출력

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">public class EvenOddChecker {
    public static void main(String[] args) {
        int number = 17;
        boolean isEven = (number % 2 == 0);

        System.out.println("숫자: " + number);
        System.out.println("짝수입니까? " + isEven);
        System.out.println(isEven ? "짝수입니다." : "홀수입니다.");
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>숫자: 17
짝수입니까? false
홀수입니다.
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
<li style="margin-bottom: 12px;"><strong>변수 선언 및 초기화</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">int number = 10;          // 선언과 초기화
int a, b, c;              // 여러 변수 선언
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>기본 자료형 (8가지)</strong>
   <table style="margin-top: 8px; margin-bottom: 0; width: 100%; border-collapse: collapse;">
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <th style="padding: 8px; text-align: left;">분류</th>
   <th style="padding: 8px; text-align: left;">자료형</th>
   <th style="padding: 8px; text-align: left;">크기</th>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;">정수</td>
   <td style="padding: 8px;">byte, short, int, long</td>
   <td style="padding: 8px;">1, 2, 4, 8바이트</td>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;">실수</td>
   <td style="padding: 8px;">float, double</td>
   <td style="padding: 8px;">4, 8바이트</td>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;">문자</td>
   <td style="padding: 8px;">char</td>
   <td style="padding: 8px;">2바이트</td>
   </tr>
   <tr>
   <td style="padding: 8px;">논리</td>
   <td style="padding: 8px;">boolean</td>
   <td style="padding: 8px;">1비트</td>
   </tr>
   </table>
</li>
<li style="margin-bottom: 12px;"><strong>참조 자료형</strong>
   <ul style="margin-top: 8px; margin-bottom: 0;">
   <li>String: 문자열</li>
   <li>기본값: null</li>
   <li>힙(Heap) 메모리에 저장</li>
   </ul>
</li>
<li style="margin-bottom: 12px;"><strong>형변환</strong>
   <ul style="margin-top: 8px; margin-bottom: 0;">
   <li>자동 형변환: 작은 타입 → 큰 타입</li>
   <li>강제 형변환: <code>(타입)변수</code></li>
   </ul>
</li>
<li style="margin-bottom: 12px;"><strong>산술 연산자</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">+  -  *  /  %     // 기본 연산
++  --            // 증감
+=  -=  *=  /=    // 복합 대입
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>비교 연산자</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">==  !=  >  <  >=  <=
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>논리 연산자</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">&&  ||  !         // AND, OR, NOT
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>비트 연산자</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">&  |  ^  ~        // AND, OR, XOR, NOT
<<  >>  >>>       // 시프트
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>연산자 우선순위</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code>괄호 → 단항 → 산술 → 시프트 → 비교 → 논리 → 대입
</code></pre>
</li>
<li style="margin-bottom: 0;"><strong>주요 포인트</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">// 정수 나눗셈 주의
10 / 3              // 3 (정수)
(double)10 / 3      // 3.333... (실수)

// 증감 연산자
num++               // 후위: 사용 후 증가
++num               // 전위: 증가 후 사용

// 문자열 비교
str1 == str2        // 주소 비교 (X)
str1.equals(str2)   // 내용 비교 (O)

// 비트 시프트
n << 1              // n * 2
n >> 1              // n / 2
</code></pre>
</li>
</ol>

</div>

---

## 다음 챕터 예고

다음 챕터에서는 **조건문**을 배웁니다.

- if 문
- if-else 문
- if-else if-else 문
- 중첩 if 문
- switch 문
- 삼항 연산자

---

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04); text-align: center;">
<div style="display: flex; align-items: center; justify-content: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">🎯</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">변수, 자료형, 연산자 학습 완료!</h3>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Java의 기본 데이터 타입과 다양한 연산자를 배웠습니다.<br>
이제 조건문을 배우면 프로그램의 흐름을 제어할 수 있습니다!
</p>
</div>
