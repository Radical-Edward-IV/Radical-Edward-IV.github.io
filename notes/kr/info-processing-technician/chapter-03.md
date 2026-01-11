---
layout: article
title: 3. 프로그래밍 언어 응용 - 01
permalink: /notes/kr/info-processing-technician/chapter-03
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 강의 노트, 프로그래밍 언어 응용 - 데이터 타입, 변수, 연산자, 입출력, 제어문, 반복문의 개념과 활용을 다룹니다.
keywords: "프로그래밍기능사, 데이터 타입, 변수, 연산자, 입출력, 제어문, 반복문, Java, Python, C"
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

<style>
    /* 색상 활용 규칙
      빨강: 주의, 경고, 위험 (오답, 금지사항 등)
      파랑: 핵심 개념, 주요 기능 (자료형, 연산자 등)
      초록: 안전한 대안, 긍정적 결과 (정답, 올바른 예시 등)
      노랑: 코드 요소 (변수명, 메소드명 등)
    */
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }

</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%20%EC%96%B8%EC%96%B4%20%EC%9D%91%EC%9A%A9&reversal=false&textBg=false)

---

## SECTION 005. 데이터 타입


<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 포인트 (중요도: ★★★★★)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
프로그래밍 언어별 <span class="blue-text">기본 자료형(Primitive Type)</span>과 <span class="blue-text">참조 자료형(Reference Type)</span>의 차이를 명확히 이해하고, 각 자료형의 크기와 범위를 숙지해야 합니다.
</p>
</div>

### 5.1 데이터 타입의 개념

<span class="blue-text">데이터 타입(Data Type)</span>은 프로그램에서 사용하는 데이터의 종류를 정의하는 것으로, 변수가 저장할 수 있는 <span class="blue-text">값의 종류와 크기</span>를 결정합니다.

**데이터 타입의 필요성**
- 메모리 공간의 효율적 사용
- 데이터 연산의 안정성 확보
- 프로그램 오류 방지
- 적절한 연산 수행

---

### 5.2 기본 자료형 (Primitive Type)

기본 자료형은 프로그래밍 언어에서 기본적으로 제공하는 자료형으로, <span class="blue-text">값 자체를 메모리에 저장</span>합니다.

#### Java의 기본 자료형

<table>
<tr>
<th style="width: 15%;">분류</th>
<th style="width: 15%;">타입</th>
<th style="width: 12%;">크기</th>
<th style="width: 28%;">범위</th>
<th>기본값</th>
</tr>
<tr>
<td rowspan="4"><span class="blue-text">정수형</span></td>
<td><span class="yellow-code">byte</span></td>
<td>1 byte</td>
<td>-128 ~ 127</td>
<td>0</td>
</tr>
<tr>
<td><span class="yellow-code">short</span></td>
<td>2 bytes</td>
<td>-32,768 ~ 32,767</td>
<td>0</td>
</tr>
<tr>
<td><span class="yellow-code">int</span></td>
<td>4 bytes</td>
<td>-2,147,483,648 ~ 2,147,483,647</td>
<td>0</td>
</tr>
<tr>
<td><span class="yellow-code">long</span></td>
<td>8 bytes</td>
<td>-9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807</td>
<td>0L</td>
</tr>
<tr>
<td rowspan="2"><span class="blue-text">실수형</span></td>
<td><span class="yellow-code">float</span></td>
<td>4 bytes</td>
<td>약 ±3.4 × 10<sup>38</sup> (소수점 7자리)</td>
<td>0.0f</td>
</tr>
<tr>
<td><span class="yellow-code">double</span></td>
<td>8 bytes</td>
<td>약 ±1.7 × 10<sup>308</sup> (소수점 15자리)</td>
<td>0.0</td>
</tr>
<tr>
<td><span class="blue-text">문자형</span></td>
<td><span class="yellow-code">char</span></td>
<td>2 bytes</td>
<td>0 ~ 65,535 (유니코드 문자)</td>
<td>'\u0000'</td>
</tr>
<tr>
<td><span class="blue-text">논리형</span></td>
<td><span class="yellow-code">boolean</span></td>
<td>1 bit</td>
<td>true, false</td>
<td>false</td>
</tr>
</table>

**Java 자료형 선언 예시**
```java
// 정수형
byte age = 25;
short year = 2024;
int population = 50000000;
long distance = 384400000L;  // L 접미사 필수

// 실수형
float pi = 3.14f;  // f 접미사 필수
double e = 2.718281828;

// 문자형
char grade = 'A';
char unicode = '\uAC00';  // '가'

// 논리형
boolean isPassed = true;
boolean isFinished = false;
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">참고</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <span class="yellow-code">long</span> 타입 리터럴은 끝에 <span class="red-text">L</span> 또는 l을 붙여야 합니다.<br>
• <span class="yellow-code">float</span> 타입 리터럴은 끝에 <span class="red-text">F</span> 또는 f를 붙여야 합니다.<br>
• <span class="yellow-code">char</span> 타입은 작은따옴표('')로 표현합니다.
</p>
</div>

---

#### C 언어의 기본 자료형

<table>
<tr>
<th style="width: 20%;">타입</th>
<th style="width: 15%;">크기</th>
<th style="width: 35%;">범위</th>
<th>설명</th>
</tr>
<tr>
<td><span class="yellow-code">char</span></td>
<td>1 byte</td>
<td>-128 ~ 127</td>
<td>문자 또는 작은 정수</td>
</tr>
<tr>
<td><span class="yellow-code">unsigned char</span></td>
<td>1 byte</td>
<td>0 ~ 255</td>
<td>양수만 저장하는 문자형</td>
</tr>
<tr>
<td><span class="yellow-code">short</span></td>
<td>2 bytes</td>
<td>-32,768 ~ 32,767</td>
<td>짧은 정수</td>
</tr>
<tr>
<td><span class="yellow-code">int</span></td>
<td>4 bytes</td>
<td>-2,147,483,648 ~ 2,147,483,647</td>
<td>일반 정수 (가장 많이 사용)</td>
</tr>
<tr>
<td><span class="yellow-code">long</span></td>
<td>4/8 bytes</td>
<td>시스템에 따라 다름</td>
<td>긴 정수</td>
</tr>
<tr>
<td><span class="yellow-code">float</span></td>
<td>4 bytes</td>
<td>±3.4 × 10<sup>38</sup></td>
<td>단정밀도 실수</td>
</tr>
<tr>
<td><span class="yellow-code">double</span></td>
<td>8 bytes</td>
<td>±1.7 × 10<sup>308</sup></td>
<td>배정밀도 실수</td>
</tr>
</table>

**C 언어 자료형 선언 예시**
```c
char grade = 'A';
unsigned char age = 25;
int count = 100;
long population = 5000000L;
float height = 175.5f;
double pi = 3.141592653589793;
```

---

#### Python의 기본 자료형

Python은 동적 타이핑 언어로, 변수 선언 시 자료형을 명시하지 않습니다. 하지만 내부적으로는 다음과 같은 기본 자료형을 가집니다.

<table>
<tr>
<th style="width: 20%;">타입</th>
<th style="width: 30%;">예시</th>
<th>설명</th>
</tr>
<tr>
<td><span class="yellow-code">int</span></td>
<td>10, -5, 1000000</td>
<td>정수 (크기 제한 없음)</td>
</tr>
<tr>
<td><span class="yellow-code">float</span></td>
<td>3.14, -0.5, 2.0</td>
<td>실수 (부동소수점)</td>
</tr>
<tr>
<td><span class="yellow-code">complex</span></td>
<td>3+4j, 1-2j</td>
<td>복소수</td>
</tr>
<tr>
<td><span class="yellow-code">bool</span></td>
<td>True, False</td>
<td>논리값</td>
</tr>
<tr>
<td><span class="yellow-code">str</span></td>
<td>"Hello", 'Python'</td>
<td>문자열</td>
</tr>
</table>

**Python 자료형 선언 예시**
```python
# 정수형
age = 25
count = 100

# 실수형
pi = 3.14
temperature = -15.5

# 복소수형
complex_num = 3 + 4j

# 논리형
is_student = True
is_passed = False

# 문자열
name = "홍길동"
greeting = 'Hello, World!'
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">Python의 특징</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• Python의 <span class="yellow-code">int</span>는 크기 제한이 없어 매우 큰 정수도 표현 가능합니다.<br>
• <span class="yellow-code">type()</span> 함수로 변수의 자료형을 확인할 수 있습니다.<br>
• 문자열은 큰따옴표("")와 작은따옴표('') 모두 사용 가능합니다.
</p>
</div>

---

### 5.3 참조 자료형 (Reference Type)

참조 자료형은 <span class="blue-text">값이 아닌 메모리 주소(참조)</span>를 저장하는 자료형입니다.

**Java의 주요 참조 자료형**

| 타입 | 설명 | 예시 |
|------|------|------|
| <span class="yellow-code">String</span> | 문자열을 저장 | "Hello World" |
| <span class="yellow-code">Array</span> | 같은 타입의 데이터를 연속적으로 저장 | int[] arr = {1, 2, 3} |
| <span class="yellow-code">Class</span> | 사용자 정의 자료형 | Person, Car 등 |

**Python의 주요 참조 자료형**

| 타입 | 설명 | 예시 |
|------|------|------|
| <span class="yellow-code">list</span> | 순서가 있는 변경 가능한 컬렉션 | [1, 2, 3, 4] |
| <span class="yellow-code">tuple</span> | 순서가 있는 변경 불가능한 컬렉션 | (1, 2, 3, 4) |
| <span class="yellow-code">dict</span> | 키-값 쌍의 컬렉션 | {"name": "홍길동"} |
| <span class="yellow-code">set</span> | 중복을 허용하지 않는 집합 | {1, 2, 3, 4} |

---

### 🎯 기출문제 따라잡기

<div class="quiz-container">

**문제 1.** Java에서 정수를 저장하는 기본 자료형이 아닌 것은?

① byte
② short
③ int
④ <span class="red-text">double</span>

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ④</strong><br><br>
double은 실수를 저장하는 자료형입니다. byte, short, int, long이 정수형 자료형입니다.
</div>
</details>

---

**문제 2.** Java에서 다음 변수 선언 중 올바르지 않은 것은?

① int age = 25;
② float pi = 3.14;
③ char grade = 'A';
④ boolean isTrue = true;

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ②</strong><br><br>
float 타입 리터럴은 끝에 f 또는 F를 붙여야 합니다. 올바른 선언: <span class="yellow-code">float pi = 3.14f;</span>
</div>
</details>

---

**문제 3.** Python에서 다음 코드의 출력 결과는?

```python
x = 10
y = 3.14
z = "Hello"
print(type(y))
```

① &lt;class 'int'&gt;
② <span class="green-text">&lt;class 'float'&gt;</span>
③ &lt;class 'str'&gt;
④ &lt;class 'bool'&gt;

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ②</strong><br><br>
type(y)는 변수 y의 자료형을 반환합니다. y = 3.14는 실수이므로 float 타입입니다.
</div>
</details>

</div>

---

## SECTION 006. 변수


<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 포인트 (중요도: ★★★★★)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
변수의 <span class="blue-text">선언, 초기화, 할당</span>의 차이를 명확히 이해하고, 각 프로그래밍 언어의 <span class="blue-text">변수 명명 규칙</span>을 숙지해야 합니다.
</p>
</div>

### 6.1 변수의 개념

<span class="blue-text">변수(Variable)</span>는 프로그램에서 데이터를 저장하기 위한 <span class="blue-text">메모리 공간의 이름</span>입니다.

**변수의 특징**
- 값을 저장하고 참조할 수 있는 저장 공간
- 프로그램 실행 중에 값이 변경될 수 있음
- 의미 있는 이름을 부여하여 가독성 향상
- 자료형에 따라 저장 가능한 데이터의 종류가 결정됨

---

### 6.2 변수의 선언과 초기화

#### 변수 선언 (Declaration)
변수를 사용하기 위해 메모리 공간을 할당하고 이름을 부여하는 것

#### 초기화 (Initialization)
변수 선언과 동시에 초기값을 할당하는 것

#### 할당 (Assignment)
이미 선언된 변수에 값을 저장하는 것

**Java 예시**
```java
// 변수 선언
int age;

// 변수 할당
age = 25;

// 변수 선언과 초기화
int count = 100;
String name = "홍길동";

// 여러 변수 동시 선언
int x, y, z;
x = 10;
y = 20;
z = 30;

// 여러 변수 동시 선언 및 초기화
int a = 1, b = 2, c = 3;
```

**Python 예시**
```python
# 변수 선언과 초기화 (동시에 이루어짐)
age = 25
name = "홍길동"
pi = 3.14

# 여러 변수 동시 할당
x, y, z = 10, 20, 30

# 같은 값을 여러 변수에 할당
a = b = c = 100
```

**C 언어 예시**
```c
// 변수 선언
int age;
char grade;
float height;

// 변수 초기화
int count = 100;
double pi = 3.14159;

// 여러 변수 동시 선언
int x, y, z;

// 여러 변수 동시 선언 및 초기화
int a = 1, b = 2, c = 3;
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">주의사항</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• Java와 C에서는 변수를 선언만 하고 초기화하지 않으면 쓰레기 값(Garbage Value)이 저장될 수 있습니다.<br>
• 변수를 사용하기 전에 반드시 초기화해야 합니다.<br>
• Python은 선언과 초기화가 동시에 이루어지므로 이러한 문제가 발생하지 않습니다.
</p>
</div>

---

### 6.3 변수 명명 규칙

**공통 규칙 (Java, C, Python)**

<table>
<tr>
<th style="width: 30%;">규칙</th>
<th>설명</th>
<th>예시</th>
</tr>
<tr>
<td><span class="blue-text">알파벳, 숫자, 밑줄 사용</span></td>
<td>변수명은 영문자, 숫자, 밑줄(_)로 구성</td>
<td><span class="green-text">age</span>, <span class="green-text">user_name</span>, <span class="green-text">count2</span></td>
</tr>
<tr>
<td><span class="blue-text">숫자로 시작 불가</span></td>
<td>변수명의 첫 글자는 숫자가 될 수 없음</td>
<td><span class="red-text">2name</span> (X), <span class="green-text">name2</span> (O)</td>
</tr>
<tr>
<td><span class="blue-text">예약어 사용 불가</span></td>
<td>프로그래밍 언어의 키워드는 변수명으로 사용 불가</td>
<td><span class="red-text">if</span>, <span class="red-text">for</span>, <span class="red-text">class</span> (X)</td>
</tr>
<tr>
<td><span class="blue-text">대소문자 구분</span></td>
<td>age와 Age는 서로 다른 변수</td>
<td>name ≠ Name ≠ NAME</td>
</tr>
<tr>
<td><span class="blue-text">공백 사용 불가</span></td>
<td>변수명에 공백을 포함할 수 없음</td>
<td><span class="red-text">user name</span> (X), <span class="green-text">user_name</span> (O)</td>
</tr>
</table>

**명명 규칙 권장사항**

| 규칙 | 설명 | 예시 |
|------|------|------|
| <span class="blue-text">카멜 케이스<br>(camelCase)</span> | Java에서 주로 사용<br>첫 단어는 소문자, 이후 단어의 첫 글자는 대문자 | userName, firstName, totalCount |
| <span class="blue-text">스네이크 케이스<br>(snake_case)</span> | Python과 C에서 주로 사용<br>단어를 밑줄(_)로 연결 | user_name, first_name, total_count |
| <span class="blue-text">의미 있는 이름</span> | 변수의 목적을 명확히 표현 | age (O), a (X)<br>studentCount (O), sc (X) |

**좋은 변수명 vs 나쁜 변수명**

```java
// 나쁜 예
int a = 25;
String s = "홍길동";
double x = 180.5;

// 좋은 예
int studentAge = 25;
String studentName = "홍길동";
double studentHeight = 180.5;
```

---

### 6.4 변수의 스코프 (Scope)

변수의 스코프는 변수가 유효한 범위를 의미합니다.

**Java의 변수 스코프**

| 변수 종류 | 선언 위치 | 유효 범위 | 생명 주기 |
|-----------|----------|-----------|-----------|
| <span class="blue-text">지역 변수</span> | 메소드 내부 | 선언된 블록 내부 | 블록 실행 시 생성, 종료 시 소멸 |
| <span class="blue-text">인스턴스 변수</span> | 클래스 내부 | 객체 내부 전체 | 객체 생성 시 생성, 소멸 시 소멸 |
| <span class="blue-text">클래스 변수</span> | 클래스 내부 (static) | 클래스 전체 | 프로그램 시작 시 생성, 종료 시 소멸 |

```java
public class Example {
    // 인스턴스 변수 (객체마다 다른 값을 가짐)
    int instanceVar = 10;

    // 클래스 변수 (모든 객체가 공유)
    static int classVar = 20;

    public void method() {
        // 지역 변수 (메소드 내에서만 유효)
        int localVar = 30;
        System.out.println(localVar);
    }  // localVar는 여기서 소멸
}
```

---

### 🎯 기출문제 따라잡기

<div class="quiz-container">

**문제 1.** 다음 중 올바른 변수명이 아닌 것은?

① userName
② _count
③ <span class="red-text">2number</span>
④ total_score

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ③</strong><br><br>
변수명은 숫자로 시작할 수 없습니다. number2는 가능하지만 2number는 불가능합니다.
</div>
</details>

---

**문제 2.** Python에서 다음 코드의 실행 결과는?

```python
x, y, z = 10, 20, 30
print(y)
```

① 10
② <span class="green-text">20</span>
③ 30
④ 60

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ②</strong><br><br>
Python의 다중 할당에서 x=10, y=20, z=30이 됩니다. print(y)는 20을 출력합니다.
</div>
</details>

---

**문제 3.** Java에서 변수 명명 규칙으로 올바르지 않은 것은?

① 변수명은 대소문자를 구분한다
② 변수명에 공백을 포함할 수 없다
③ <span class="red-text">예약어를 변수명으로 사용할 수 있다</span>
④ 변수명은 숫자로 시작할 수 없다

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ③</strong><br><br>
if, for, class 등의 예약어는 변수명으로 사용할 수 없습니다.
</div>
</details>

</div>

---

## SECTION 007. 연산자


<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 포인트 (중요도: ★★★★★)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
<span class="blue-text">산술, 비교, 논리, 비트, 대입 연산자</span>의 종류와 사용법을 정확히 이해하고, <span class="blue-text">연산자 우선순위</span>를 숙지해야 합니다.
</p>
</div>

### 7.1 연산자의 개념

<span class="blue-text">연산자(Operator)</span>는 데이터를 처리하여 결과를 산출하는 기호입니다.

**연산자의 구성 요소**
- <span class="blue-text">연산자(Operator)</span>: 연산을 수행하는 기호 (+, -, *, / 등)
- <span class="blue-text">피연산자(Operand)</span>: 연산의 대상이 되는 값이나 변수

```java
int result = 10 + 5;
//           ↑  ↑ ↑
//       피연산자 연산자 피연산자
```

---

### 7.2 산술 연산자

산술 연산자는 사칙연산과 나머지 연산을 수행합니다.

<table>
<tr>
<th style="width: 15%;">연산자</th>
<th style="width: 20%;">의미</th>
<th>예시</th>
<th style="width: 15%;">결과</th>
</tr>
<tr>
<td><span class="yellow-code">+</span></td>
<td>덧셈</td>
<td>10 + 5</td>
<td>15</td>
</tr>
<tr>
<td><span class="yellow-code">-</span></td>
<td>뺄셈</td>
<td>10 - 5</td>
<td>5</td>
</tr>
<tr>
<td><span class="yellow-code">*</span></td>
<td>곱셈</td>
<td>10 * 5</td>
<td>50</td>
</tr>
<tr>
<td><span class="yellow-code">/</span></td>
<td>나눗셈 (몫)</td>
<td>10 / 3</td>
<td>3 (정수 나눗셈)</td>
</tr>
<tr>
<td><span class="yellow-code">%</span></td>
<td>나머지 (modulo)</td>
<td>10 % 3</td>
<td>1</td>
</tr>
<tr>
<td><span class="yellow-code">**</span></td>
<td>거듭제곱 (Python)</td>
<td>2 ** 3</td>
<td>8</td>
</tr>
</table>

**산술 연산자 예시**

```java
// Java
int a = 10, b = 3;
System.out.println(a + b);  // 13
System.out.println(a - b);  // 7
System.out.println(a * b);  // 30
System.out.println(a / b);  // 3 (정수 나눗셈)
System.out.println(a % b);  // 1

// 실수 나눗셈
double result = 10.0 / 3.0;  // 3.333...
```

```python
# Python
a, b = 10, 3
print(a + b)   # 13
print(a - b)   # 7
print(a * b)   # 30
print(a / b)   # 3.3333... (실수 나눗셈)
print(a // b)  # 3 (정수 나눗셈, floor division)
print(a % b)   # 1
print(a ** b)  # 1000 (거듭제곱)
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">참고</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• Java/C에서 정수끼리 나누면 결과도 정수입니다. (10 / 3 = 3)<br>
• Python에서 <span class="yellow-code">/</span>는 항상 실수 나눗셈, <span class="yellow-code">//</span>는 정수 나눗셈입니다.<br>
• 나머지 연산자 <span class="yellow-code">%</span>는 홀수/짝수 판별, 배수 확인 등에 유용합니다.
</p>
</div>

---

### 7.3 증감 연산자

증감 연산자는 변수의 값을 1 증가 또는 감소시킵니다.

<table>
<tr>
<th style="width: 15%;">연산자</th>
<th style="width: 20%;">의미</th>
<th>예시</th>
<th>설명</th>
</tr>
<tr>
<td><span class="yellow-code">++</span></td>
<td>1 증가</td>
<td>++a (전위)<br>a++ (후위)</td>
<td>전위: 증가 후 사용<br>후위: 사용 후 증가</td>
</tr>
<tr>
<td><span class="yellow-code">--</span></td>
<td>1 감소</td>
<td>--a (전위)<br>a-- (후위)</td>
<td>전위: 감소 후 사용<br>후위: 사용 후 감소</td>
</tr>
</table>

**증감 연산자 예시**

```java
// Java
int a = 5;
System.out.println(++a);  // 6 (먼저 증가, 그 다음 출력)
System.out.println(a);    // 6

int b = 5;
System.out.println(b++);  // 5 (먼저 출력, 그 다음 증가)
System.out.println(b);    // 6
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">주의</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Python에는 증감 연산자(++, --)가 없습니다. <span class="yellow-code">x += 1</span> 또는 <span class="yellow-code">x -= 1</span>을 사용해야 합니다.
</p>
</div>

---

### 7.4 비교 연산자 (관계 연산자)

비교 연산자는 두 값을 비교하여 참(true) 또는 거짓(false)을 반환합니다.

<table>
<tr>
<th style="width: 15%;">연산자</th>
<th style="width: 25%;">의미</th>
<th>예시 (a=10, b=5)</th>
<th>결과</th>
</tr>
<tr>
<td><span class="yellow-code">==</span></td>
<td>같다</td>
<td>a == b</td>
<td>false</td>
</tr>
<tr>
<td><span class="yellow-code">!=</span></td>
<td>같지 않다</td>
<td>a != b</td>
<td>true</td>
</tr>
<tr>
<td><span class="yellow-code">&gt;</span></td>
<td>크다</td>
<td>a &gt; b</td>
<td>true</td>
</tr>
<tr>
<td><span class="yellow-code">&lt;</span></td>
<td>작다</td>
<td>a &lt; b</td>
<td>false</td>
</tr>
<tr>
<td><span class="yellow-code">&gt;=</span></td>
<td>크거나 같다</td>
<td>a &gt;= 10</td>
<td>true</td>
</tr>
<tr>
<td><span class="yellow-code">&lt;=</span></td>
<td>작거나 같다</td>
<td>b &lt;= 5</td>
<td>true</td>
</tr>
</table>

**비교 연산자 예시**

```java
// Java
int score = 85;
boolean isPassed = score >= 60;  // true
boolean isA = score >= 90;       // false

// 문자열 비교 (주의!)
String str1 = "Hello";
String str2 = "Hello";
System.out.println(str1 == str2);       // 참조 비교
System.out.println(str1.equals(str2));  // 값 비교 (권장)
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">중요</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• Java에서 문자열 비교는 <span class="red-text">==</span>이 아닌 <span class="green-text">.equals()</span> 메소드를 사용해야 합니다!<br>
• == 연산자는 참조(주소)를 비교하고, equals()는 값을 비교합니다.<br>
• Python에서는 == 연산자로 문자열 값을 비교할 수 있습니다.
</p>
</div>

---

### 7.5 논리 연산자

논리 연산자는 논리값(true/false)을 연산합니다.

<table>
<tr>
<th style="width: 15%;">연산자</th>
<th style="width: 20%;">의미</th>
<th>설명</th>
<th>예시</th>
</tr>
<tr>
<td><span class="yellow-code">&&</span><br>(and)</td>
<td>논리곱 (AND)</td>
<td>모두 true일 때만 true</td>
<td>true && false → false</td>
</tr>
<tr>
<td><span class="yellow-code">||</span><br>(or)</td>
<td>논리합 (OR)</td>
<td>하나라도 true면 true</td>
<td>true || false → true</td>
</tr>
<tr>
<td><span class="yellow-code">!</span><br>(not)</td>
<td>논리 부정 (NOT)</td>
<td>true ↔ false 반전</td>
<td>!true → false</td>
</tr>
</table>

**논리 연산 진리표**

<div class="code-compare">
<div>
<strong>AND (&&) 연산</strong>

| A | B | A && B |
|---|---|--------|
| T | T | T |
| T | F | F |
| F | T | F |
| F | F | F |

</div>
<div>
<strong>OR (||) 연산</strong>

| A | B | A \|\| B |
|---|---|----------|
| T | T | T |
| T | F | T |
| F | T | T |
| F | F | F |

</div>
</div>

**논리 연산자 예시**

```java
// Java
int age = 25;
boolean hasLicense = true;

// AND 연산
boolean canDrive = (age >= 18) && hasLicense;  // true

// OR 연산
boolean needsTraining = (age < 18) || !hasLicense;  // false

// NOT 연산
boolean isMinor = !(age >= 18);  // false
```

```python
# Python (and, or, not 키워드 사용)
age = 25
has_license = True

# AND 연산
can_drive = (age >= 18) and has_license  # True

# OR 연산
needs_training = (age < 18) or not has_license  # False

# NOT 연산
is_minor = not (age >= 18)  # False
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">단락 평가 (Short-Circuit Evaluation)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <span class="yellow-code">&&</span> 연산: 첫 번째 조건이 false면 두 번째 조건을 평가하지 않음<br>
• <span class="yellow-code">||</span> 연산: 첫 번째 조건이 true면 두 번째 조건을 평가하지 않음<br>
• 이를 활용하면 효율적이고 안전한 코드를 작성할 수 있습니다.
</p>
</div>

---

### 7.6 비트 연산자

비트 연산자는 정수의 이진수 비트 단위로 연산합니다.

<table>
<tr>
<th style="width: 15%;">연산자</th>
<th style="width: 20%;">의미</th>
<th>설명</th>
<th>예시 (2진수)</th>
</tr>
<tr>
<td><span class="yellow-code">&</span></td>
<td>비트 AND</td>
<td>대응 비트가 모두 1이면 1</td>
<td>1010 & 1100 = 1000</td>
</tr>
<tr>
<td><span class="yellow-code">|</span></td>
<td>비트 OR</td>
<td>대응 비트 중 하나라도 1이면 1</td>
<td>1010 | 1100 = 1110</td>
</tr>
<tr>
<td><span class="yellow-code">^</span></td>
<td>비트 XOR</td>
<td>대응 비트가 다르면 1</td>
<td>1010 ^ 1100 = 0110</td>
</tr>
<tr>
<td><span class="yellow-code">~</span></td>
<td>비트 NOT</td>
<td>모든 비트 반전</td>
<td>~1010 = 0101</td>
</tr>
<tr>
<td><span class="yellow-code">&lt;&lt;</span></td>
<td>왼쪽 시프트</td>
<td>비트를 왼쪽으로 이동 (2배씩 증가)</td>
<td>5 &lt;&lt; 2 = 20</td>
</tr>
<tr>
<td><span class="yellow-code">&gt;&gt;</span></td>
<td>오른쪽 시프트</td>
<td>비트를 오른쪽으로 이동 (2로 나눔)</td>
<td>20 &gt;&gt; 2 = 5</td>
</tr>
</table>

**비트 연산자 예시**

```java
// Java
int a = 5;   // 0101 (2진수)
int b = 3;   // 0011 (2진수)

System.out.println(a & b);   // 1 (0001)
System.out.println(a | b);   // 7 (0111)
System.out.println(a ^ b);   // 6 (0110)
System.out.println(~a);      // -6
System.out.println(a << 1);  // 10 (0101 → 1010)
System.out.println(a >> 1);  // 2 (0101 → 0010)
```

---

### 7.7 대입 연산자

대입 연산자는 오른쪽 값을 왼쪽 변수에 저장합니다.

<table>
<tr>
<th style="width: 15%;">연산자</th>
<th style="width: 25%;">의미</th>
<th>예시</th>
<th>동일 표현</th>
</tr>
<tr>
<td><span class="yellow-code">=</span></td>
<td>대입</td>
<td>a = 10</td>
<td>-</td>
</tr>
<tr>
<td><span class="yellow-code">+=</span></td>
<td>덧셈 후 대입</td>
<td>a += 5</td>
<td>a = a + 5</td>
</tr>
<tr>
<td><span class="yellow-code">-=</span></td>
<td>뺄셈 후 대입</td>
<td>a -= 5</td>
<td>a = a - 5</td>
</tr>
<tr>
<td><span class="yellow-code">*=</span></td>
<td>곱셈 후 대입</td>
<td>a *= 5</td>
<td>a = a * 5</td>
</tr>
<tr>
<td><span class="yellow-code">/=</span></td>
<td>나눗셈 후 대입</td>
<td>a /= 5</td>
<td>a = a / 5</td>
</tr>
<tr>
<td><span class="yellow-code">%=</span></td>
<td>나머지 후 대입</td>
<td>a %= 5</td>
<td>a = a % 5</td>
</tr>
</table>

---

### 7.8 연산자 우선순위

연산자 우선순위는 여러 연산자가 함께 사용될 때 어떤 연산을 먼저 수행할지 결정합니다.

<table>
<tr>
<th style="width: 10%;">우선순위</th>
<th style="width: 30%;">연산자</th>
<th>설명</th>
</tr>
<tr>
<td>1</td>
<td><span class="yellow-code">()</span></td>
<td>괄호</td>
</tr>
<tr>
<td>2</td>
<td><span class="yellow-code">++, --</span></td>
<td>증감 연산자</td>
</tr>
<tr>
<td>3</td>
<td><span class="yellow-code">!, ~</span></td>
<td>논리/비트 부정</td>
</tr>
<tr>
<td>4</td>
<td><span class="yellow-code">*, /, %</span></td>
<td>곱셈, 나눗셈, 나머지</td>
</tr>
<tr>
<td>5</td>
<td><span class="yellow-code">+, -</span></td>
<td>덧셈, 뺄셈</td>
</tr>
<tr>
<td>6</td>
<td><span class="yellow-code">&lt;&lt;, &gt;&gt;</span></td>
<td>비트 시프트</td>
</tr>
<tr>
<td>7</td>
<td><span class="yellow-code">&lt;, &lt;=, &gt;, &gt;=</span></td>
<td>비교 연산자</td>
</tr>
<tr>
<td>8</td>
<td><span class="yellow-code">==, !=</span></td>
<td>동등 비교</td>
</tr>
<tr>
<td>9</td>
<td><span class="yellow-code">&</span></td>
<td>비트 AND</td>
</tr>
<tr>
<td>10</td>
<td><span class="yellow-code">^</span></td>
<td>비트 XOR</td>
</tr>
<tr>
<td>11</td>
<td><span class="yellow-code">|</span></td>
<td>비트 OR</td>
</tr>
<tr>
<td>12</td>
<td><span class="yellow-code">&&</span></td>
<td>논리 AND</td>
</tr>
<tr>
<td>13</td>
<td><span class="yellow-code">||</span></td>
<td>논리 OR</td>
</tr>
<tr>
<td>14</td>
<td><span class="yellow-code">=, +=, -=, 등</span></td>
<td>대입 연산자</td>
</tr>
</table>

**연산자 우선순위 예시**

```java
int result = 10 + 5 * 2;  // 20 (곱셈이 먼저)
int result2 = (10 + 5) * 2;  // 30 (괄호가 최우선)

boolean b = 10 > 5 && 3 < 7;  // true (비교 → 논리)
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">권장사항</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
연산자 우선순위를 모두 외우기보다는, <span class="blue-text">괄호()</span>를 사용하여 명확하게 표현하는 것이 좋습니다. 코드의 가독성이 향상되고 오류를 줄일 수 있습니다.
</p>
</div>

---

### 🎯 기출문제 따라잡기

<div class="quiz-container">

**문제 1.** 다음 Java 코드의 출력 결과는?

```java
int x = 5;
System.out.println(x++);
System.out.println(++x);
```

① 5, 6
② 6, 7
③ <span class="green-text">5, 7</span>
④ 6, 6

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ③</strong><br><br>
x++는 출력 후 증가 → 5 출력, x는 6이 됨<br>
++x는 증가 후 출력 → x가 7이 되고, 7 출력
</div>
</details>

---

**문제 2.** 다음 중 비트 연산자가 아닌 것은?

① &
② |
③ ^
④ <span class="red-text">&&</span>

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ④</strong><br><br>
&&는 논리 AND 연산자입니다. &는 비트 AND 연산자입니다.
</div>
</details>

---

**문제 3.** 다음 연산의 결과는?

```java
int result = 10 + 3 * 2;
```

① 26
② <span class="green-text">16</span>
③ 13
④ 15

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ②</strong><br><br>
곱셈이 덧셈보다 우선순위가 높으므로: 10 + (3 * 2) = 10 + 6 = 16
</div>
</details>

---

**문제 4.** Python에서 다음 코드의 출력 결과는?

```python
print(17 // 5)
print(17 % 5)
```

① 3.4, 2
② <span class="green-text">3, 2</span>
③ 3, 5
④ 4, 2

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ②</strong><br><br>
//는 정수 나눗셈(몫): 17 // 5 = 3<br>
%는 나머지 연산: 17 % 5 = 2
</div>
</details>

---

**문제 5.** 다음 논리 연산의 결과로 true인 것은?

① true && false
② false || false
③ <span class="green-text">!(false)</span>
④ false && true

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ③</strong><br><br>
!(false)는 NOT 연산으로 false를 true로 반전시킵니다.
</div>
</details>

</div>

---

**(계속 - Chapter 3는 너무 길어서 두 개의 파일로 나누어야 할 것 같습니다. 나머지 Section 008, 009, 010도 작성해야 합니다.)**

실제로 Chapter 3 파일이 매우 길어질 것으로 예상됩니다. 파일을 완성하겠습니다.

## SECTION 008. 데이터 입·출력


<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 포인트 (중요도: ★★★★★)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
각 프로그래밍 언어의 <span class="blue-text">표준 입출력 방법</span>과 <span class="blue-text">형식화된 출력</span>을 이해하고 활용할 수 있어야 합니다.
</p>
</div>

### 8.1 출력 (Output)

#### Java의 출력

**System.out의 주요 메소드**

<table>
<tr>
<th style="width: 30%;">메소드</th>
<th>기능</th>
<th>예시</th>
</tr>
<tr>
<td><span class="yellow-code">print()</span></td>
<td>출력 후 줄바꿈 없음</td>
<td>System.out.print("Hello");</td>
</tr>
<tr>
<td><span class="yellow-code">println()</span></td>
<td>출력 후 줄바꿈</td>
<td>System.out.println("Hello");</td>
</tr>
<tr>
<td><span class="yellow-code">printf()</span></td>
<td>형식화된 출력</td>
<td>System.out.printf("%d", 10);</td>
</tr>
</table>

**Java 출력 예시**
```java
// 기본 출력
System.out.println("Hello, World!");
System.out.print("안녕");
System.out.print("하세요");  // 안녕하세요 (같은 줄)

// 변수 출력
int age = 25;
String name = "홍길동";
System.out.println("이름: " + name + ", 나이: " + age);

// 형식화된 출력 (printf)
System.out.printf("이름: %s, 나이: %d%n", name, age);
System.out.printf("%.2f", 3.14159);  // 3.14 (소수점 2자리)
```

**Java printf 형식 지정자**

| 지정자 | 의미 | 예시 |
|--------|------|------|
| <span class="yellow-code">%d</span> | 10진수 정수 | printf("%d", 10) → 10 |
| <span class="yellow-code">%f</span> | 실수 | printf("%.2f", 3.14) → 3.14 |
| <span class="yellow-code">%s</span> | 문자열 | printf("%s", "Hello") → Hello |
| <span class="yellow-code">%c</span> | 문자 | printf("%c", 'A') → A |
| <span class="yellow-code">%b</span> | boolean | printf("%b", true) → true |
| <span class="yellow-code">%n</span> | 줄바꿈 | printf("Line1%nLine2") |

---

#### Python의 출력

**print() 함수**

```python
# 기본 출력
print("Hello, World!")

# 여러 값 출력 (쉼표로 구분)
print("이름:", "홍길동", "나이:", 25)  # 이름: 홍길동 나이: 25

# 줄바꿈 제어
print("Hello", end=" ")  # 줄바꿈 대신 공백
print("World")  # Hello World (같은 줄)

# 구분자 변경
print("사과", "바나나", "오렌지", sep=", ")  # 사과, 바나나, 오렌지

# 형식화된 출력 (f-string)
name = "홍길동"
age = 25
print(f"이름: {name}, 나이: {age}")

# format() 메소드
print("이름: {}, 나이: {}".format(name, age))

# % 연산자 (구식)
print("이름: %s, 나이: %d" % (name, age))
```

---

#### C 언어의 출력

**printf() 함수**

```c
#include <stdio.h>

int main() {
    // 기본 출력
    printf("Hello, World!\n");

    // 변수 출력
    int age = 25;
    char name[] = "홍길동";
    printf("이름: %s, 나이: %d\n", name, age);

    // 형식화된 출력
    printf("%5d\n", 10);      // "   10" (5자리, 오른쪽 정렬)
    printf("%-5d\n", 10);     // "10   " (5자리, 왼쪽 정렬)
    printf("%.2f\n", 3.14159);  // "3.14" (소수점 2자리)

    return 0;
}
```

---

### 8.2 입력 (Input)

#### Java의 입력

**Scanner 클래스 사용**

```java
import java.util.Scanner;

public class InputExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // 정수 입력
        System.out.print("나이를 입력하세요: ");
        int age = sc.nextInt();

        // 실수 입력
        System.out.print("키를 입력하세요: ");
        double height = sc.nextDouble();

        // 문자열 입력 (한 단어)
        System.out.print("이름을 입력하세요: ");
        String name = sc.next();

        // 문자열 입력 (한 줄)
        sc.nextLine();  // 버퍼 비우기
        System.out.print("주소를 입력하세요: ");
        String address = sc.nextLine();

        sc.close();  // Scanner 닫기
    }
}
```

**Scanner의 주요 메소드**

| 메소드 | 기능 | 반환 타입 |
|--------|------|-----------|
| <span class="yellow-code">nextInt()</span> | 정수 입력 | int |
| <span class="yellow-code">nextDouble()</span> | 실수 입력 | double |
| <span class="yellow-code">next()</span> | 문자열 입력 (공백 전까지) | String |
| <span class="yellow-code">nextLine()</span> | 한 줄 입력 | String |
| <span class="yellow-code">nextBoolean()</span> | 논리값 입력 | boolean |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">Scanner 사용 시 주의사항</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
<span class="yellow-code">nextInt()</span> 등을 사용한 후 <span class="yellow-code">nextLine()</span>을 사용하면 버퍼에 남아있는 엔터가 입력되어 문제가 발생할 수 있습니다. 이 경우 <span class="yellow-code">sc.nextLine()</span>을 한 번 더 호출하여 버퍼를 비워야 합니다.
</p>
</div>

---

#### Python의 입력

**input() 함수**

```python
# 문자열 입력 (기본)
name = input("이름을 입력하세요: ")
print("입력한 이름:", name)

# 정수 입력 (형 변환 필요)
age = int(input("나이를 입력하세요: "))
print("10년 후 나이:", age + 10)

# 실수 입력
height = float(input("키를 입력하세요: "))
print("키:", height, "cm")

# 여러 값 입력 (공백으로 구분)
a, b = input("두 수를 입력하세요: ").split()
print(a, b)

# 여러 정수 입력
numbers = list(map(int, input("숫자들을 입력하세요: ").split()))
print("입력한 숫자:", numbers)
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">Python input()의 특징</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <span class="yellow-code">input()</span>은 항상 문자열을 반환합니다.<br>
• 숫자를 입력받으려면 <span class="yellow-code">int()</span> 또는 <span class="yellow-code">float()</span>로 형 변환해야 합니다.<br>
• <span class="yellow-code">split()</span>을 사용하면 여러 값을 한 번에 입력받을 수 있습니다.
</p>
</div>

---

#### C 언어의 입력

**scanf() 함수**

```c
#include <stdio.h>

int main() {
    int age;
    double height;
    char name[50];

    // 정수 입력
    printf("나이를 입력하세요: ");
    scanf("%d", &age);

    // 실수 입력
    printf("키를 입력하세요: ");
    scanf("%lf", &height);

    // 문자열 입력 (공백 전까지)
    printf("이름을 입력하세요: ");
    scanf("%s", name);  // 배열은 & 불필요

    // 여러 값 입력
    int a, b;
    printf("두 수를 입력하세요: ");
    scanf("%d %d", &a, &b);

    return 0;
}
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">scanf() 사용 시 주의사항</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• 변수 앞에 <span class="red-text">&</span>(주소 연산자)를 붙여야 합니다. (배열 제외)<br>
• %s는 공백을 만나면 입력이 종료됩니다.<br>
• 버퍼 오버플로우 방지를 위해 <span class="yellow-code">fgets()</span> 사용을 권장합니다.
</p>
</div>

---

### 🎯 기출문제 따라잡기

<div class="quiz-container">

**문제 1.** Java에서 형식화된 출력을 위해 사용하는 메소드는?

① print()
② println()
③ <span class="green-text">printf()</span>
④ format()

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ③</strong><br><br>
printf()는 C 언어 스타일의 형식화된 출력을 지원합니다.
</div>
</details>

---

**문제 2.** Python에서 다음 코드의 출력 결과는?

```python
print("Hello", "World", sep="-")
```

① Hello World
② <span class="green-text">Hello-World</span>
③ Hello, World
④ HelloWorld

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ②</strong><br><br>
sep 매개변수는 값들 사이의 구분자를 지정합니다. sep="-"는 하이픈으로 구분합니다.
</div>
</details>

---

**문제 3.** Java Scanner의 메소드 중 한 줄 전체를 입력받는 것은?

① next()
② nextInt()
③ <span class="green-text">nextLine()</span>
④ nextDouble()

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ③</strong><br><br>
nextLine()은 줄바꿈 문자까지 포함한 한 줄 전체를 입력받습니다. next()는 공백 전까지만 입력받습니다.
</div>
</details>

</div>

---

## SECTION 009. 제어문


<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 포인트 (중요도: ★★★★★)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
<span class="blue-text">조건문(if, switch)</span>의 문법과 사용 방법을 정확히 이해하고, 각 언어별 차이점을 숙지해야 합니다.
</p>
</div>

### 9.1 제어문의 개념

<span class="blue-text">제어문(Control Statement)</span>은 프로그램의 실행 흐름을 제어하는 명령문입니다.

**제어문의 종류**
- <span class="blue-text">조건문</span>: 조건에 따라 다른 코드를 실행 (if, switch)
- <span class="blue-text">반복문</span>: 특정 코드를 반복 실행 (for, while, do-while)

---

### 9.2 if 문

if 문은 조건식의 결과가 참(true)일 때 특정 코드를 실행합니다.

**기본 형식**

```java
// Java
if (조건식) {
    // 조건이 참일 때 실행할 코드
}
```

```python
# Python
if 조건식:
    # 조건이 참일 때 실행할 코드
```

**예시**

```java
// Java
int score = 85;

if (score >= 60) {
    System.out.println("합격입니다!");
}
```

```python
# Python
score = 85

if score >= 60:
    print("합격입니다!")
```

---

### 9.3 if-else 문

조건이 참일 때와 거짓일 때 각각 다른 코드를 실행합니다.

**기본 형식**

```java
// Java
if (조건식) {
    // 조건이 참일 때 실행
} else {
    // 조건이 거짓일 때 실행
}
```

**예시**

```java
// Java
int age = 15;

if (age >= 18) {
    System.out.println("성인입니다.");
} else {
    System.out.println("미성년자입니다.");
}
```

```python
# Python
age = 15

if age >= 18:
    print("성인입니다.")
else:
    print("미성년자입니다.")
```

---

### 9.4 if-else if-else 문

여러 조건을 순차적으로 검사합니다.

**기본 형식**

```java
// Java
if (조건식1) {
    // 조건식1이 참일 때
} else if (조건식2) {
    // 조건식2가 참일 때
} else if (조건식3) {
    // 조건식3이 참일 때
} else {
    // 모든 조건이 거짓일 때
}
```

**예시: 학점 계산**

```java
// Java
int score = 85;
char grade;

if (score >= 90) {
    grade = 'A';
} else if (score >= 80) {
    grade = 'B';
} else if (score >= 70) {
    grade = 'C';
} else if (score >= 60) {
    grade = 'D';
} else {
    grade = 'F';
}

System.out.println("학점: " + grade);
```

```python
# Python
score = 85

if score >= 90:
    grade = 'A'
elif score >= 80:
    grade = 'B'
elif score >= 70:
    grade = 'C'
elif score >= 60:
    grade = 'D'
else:
    grade = 'F'

print(f"학점: {grade}")
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">참고</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• Python에서는 <span class="yellow-code">else if</span> 대신 <span class="yellow-code">elif</span>를 사용합니다.<br>
• 조건은 위에서부터 순차적으로 검사되며, 참인 조건을 만나면 나머지는 검사하지 않습니다.
</p>
</div>

---

### 9.5 중첩 if 문

if 문 안에 또 다른 if 문을 포함할 수 있습니다.

```java
// Java
int age = 25;
boolean hasLicense = true;

if (age >= 18) {
    if (hasLicense) {
        System.out.println("운전 가능합니다.");
    } else {
        System.out.println("면허가 필요합니다.");
    }
} else {
    System.out.println("나이가 부족합니다.");
}
```

---

### 9.6 switch 문

하나의 변수 값에 따라 여러 경우 중 하나를 선택합니다.

**기본 형식**

```java
// Java
switch (변수) {
    case 값1:
        // 값1일 때 실행
        break;
    case 값2:
        // 값2일 때 실행
        break;
    default:
        // 어느 case에도 해당하지 않을 때 실행
        break;
}
```

**예시: 요일 판별**

```java
// Java
int day = 3;
String dayName;

switch (day) {
    case 1:
        dayName = "월요일";
        break;
    case 2:
        dayName = "화요일";
        break;
    case 3:
        dayName = "수요일";
        break;
    case 4:
        dayName = "목요일";
        break;
    case 5:
        dayName = "금요일";
        break;
    case 6:
        dayName = "토요일";
        break;
    case 7:
        dayName = "일요일";
        break;
    default:
        dayName = "잘못된 입력";
        break;
}

System.out.println(dayName);  // 수요일
```

```c
// C 언어
int month = 12;

switch (month) {
    case 12:
    case 1:
    case 2:
        printf("겨울\n");
        break;
    case 3:
    case 4:
    case 5:
        printf("봄\n");
        break;
    case 6:
    case 7:
    case 8:
        printf("여름\n");
        break;
    case 9:
    case 10:
    case 11:
        printf("가을\n");
        break;
    default:
        printf("잘못된 월\n");
        break;
}
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">break 문의 중요성</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <span class="yellow-code">break</span> 문을 생략하면 다음 case로 넘어가는 <span class="red-text">Fall-through</span> 현상이 발생합니다.<br>
• 의도적으로 사용하는 경우가 아니면 반드시 break를 작성해야 합니다.<br>
• Python에는 switch 문이 없습니다. (Python 3.10부터 match-case 지원)
</p>
</div>

---

### 9.7 삼항 연산자

간단한 조건문을 한 줄로 표현할 수 있습니다.

**기본 형식**

```java
// Java
변수 = (조건식) ? 참일_때_값 : 거짓일_때_값;
```

**예시**

```java
// Java
int age = 20;
String result = (age >= 18) ? "성인" : "미성년자";
System.out.println(result);  // 성인

// 중첩 삼항 연산자
int score = 85;
String grade = (score >= 90) ? "A" :
               (score >= 80) ? "B" :
               (score >= 70) ? "C" : "F";
```

```python
# Python
age = 20
result = "성인" if age >= 18 else "미성년자"
print(result)  # 성인
```

---

### 🎯 기출문제 따라잡기

<div class="quiz-container">

**문제 1.** 다음 Java 코드의 출력 결과는?

```java
int x = 10;
if (x > 5) {
    if (x < 15) {
        System.out.println("A");
    } else {
        System.out.println("B");
    }
} else {
    System.out.println("C");
}
```

① <span class="green-text">A</span>
② B
③ C
④ 출력 없음

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ①</strong><br><br>
x=10은 5보다 크고(참) 15보다 작으므로(참) "A"가 출력됩니다.
</div>
</details>

---

**문제 2.** switch 문에서 break를 생략하면 발생하는 현상은?

① 컴파일 오류
② 런타임 오류
③ <span class="green-text">Fall-through (다음 case 실행)</span>
④ 프로그램 종료

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ③</strong><br><br>
break를 생략하면 다음 case로 넘어가는 Fall-through 현상이 발생합니다. 의도적으로 사용하는 경우가 아니면 반드시 break를 작성해야 합니다.
</div>
</details>

---

**문제 3.** Python에서 다중 조건을 검사하는 키워드는?

① else if
② <span class="green-text">elif</span>
③ elseif
④ elsif

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ②</strong><br><br>
Python에서는 else if 대신 elif를 사용합니다.
</div>
</details>

</div>

---

## SECTION 010. 반복문


<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 포인트 (중요도: ★★★★★)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
<span class="blue-text">for, while, do-while</span> 반복문의 차이점을 이해하고, <span class="blue-text">break와 continue</span>의 사용법을 숙지해야 합니다.
</p>
</div>

### 10.1 반복문의 개념

<span class="blue-text">반복문(Loop Statement)</span>은 특정 조건이 만족하는 동안 코드를 반복 실행하는 제어문입니다.

**반복문의 종류**
- <span class="blue-text">for 문</span>: 정해진 횟수만큼 반복
- <span class="blue-text">while 문</span>: 조건이 참인 동안 반복
- <span class="blue-text">do-while 문</span>: 최소 한 번은 실행하고 조건 검사

---

### 10.2 for 문

반복 횟수가 정해져 있을 때 주로 사용합니다.

**기본 형식**

```java
// Java, C
for (초기식; 조건식; 증감식) {
    // 반복 실행할 코드
}
```

```python
# Python
for 변수 in 범위:
    # 반복 실행할 코드
```

**실행 순서**
1. 초기식 실행 (최초 한 번만)
2. 조건식 검사 (참이면 3번, 거짓이면 종료)
3. 반복 코드 실행
4. 증감식 실행
5. 2번으로 돌아감

**예시**

```java
// Java: 1부터 10까지 출력
for (int i = 1; i <= 10; i++) {
    System.out.println(i);
}

// 짝수만 출력
for (int i = 2; i <= 10; i += 2) {
    System.out.println(i);
}

// 역순 출력
for (int i = 10; i >= 1; i--) {
    System.out.println(i);
}
```

```python
# Python: range() 함수 사용
for i in range(1, 11):  # 1부터 10까지
    print(i)

# 짝수만 출력
for i in range(2, 11, 2):  # 시작, 끝, 증가값
    print(i)

# 역순 출력
for i in range(10, 0, -1):  # 10부터 1까지
    print(i)

# 리스트 순회
fruits = ["사과", "바나나", "오렌지"]
for fruit in fruits:
    print(fruit)
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">Python range() 함수</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <span class="yellow-code">range(n)</span>: 0부터 n-1까지<br>
• <span class="yellow-code">range(start, end)</span>: start부터 end-1까지<br>
• <span class="yellow-code">range(start, end, step)</span>: start부터 end-1까지 step 간격으로
</p>
</div>

---

### 10.3 중첩 for 문

for 문 안에 또 다른 for 문을 포함할 수 있습니다.

**구구단 출력**

```java
// Java
for (int dan = 2; dan <= 9; dan++) {
    System.out.println(dan + "단:");
    for (int i = 1; i <= 9; i++) {
        System.out.println(dan + " × " + i + " = " + (dan * i));
    }
    System.out.println();
}
```

**별 찍기 (직각삼각형)**

```java
// Java
for (int i = 1; i <= 5; i++) {
    for (int j = 1; j <= i; j++) {
        System.out.print("*");
    }
    System.out.println();
}

// 출력:
// *
// **
// ***
// ****
// *****
```

---

### 10.4 while 문

조건이 참인 동안 반복 실행합니다. 반복 횟수를 모를 때 주로 사용합니다.

**기본 형식**

```java
// Java, C
while (조건식) {
    // 반복 실행할 코드
}
```

```python
# Python
while 조건식:
    # 반복 실행할 코드
```

**예시**

```java
// Java: 1부터 10까지 출력
int i = 1;
while (i <= 10) {
    System.out.println(i);
    i++;
}

// 사용자 입력 받기 (특정 값 입력 시 종료)
Scanner sc = new Scanner(System.in);
int num = 0;
while (num != -1) {
    System.out.print("숫자 입력 (-1: 종료): ");
    num = sc.nextInt();
    System.out.println("입력한 숫자: " + num);
}
```

```python
# Python
i = 1
while i <= 10:
    print(i)
    i += 1

# 무한 루프 (조건 만족 시 break로 탈출)
while True:
    num = int(input("숫자 입력 (-1: 종료): "))
    if num == -1:
        break
    print(f"입력한 숫자: {num}")
```

---

### 10.5 do-while 문

조건을 검사하기 전에 먼저 한 번 실행합니다. (Python에는 없음)

**기본 형식**

```java
// Java, C
do {
    // 반복 실행할 코드
} while (조건식);
```

**특징**
- 조건과 관계없이 최소 한 번은 실행됨
- 루프 끝에서 조건을 검사

**예시**

```java
// Java
int i = 1;
do {
    System.out.println(i);
    i++;
} while (i <= 5);

// 최소 한 번은 실행 (조건이 거짓이어도)
int j = 10;
do {
    System.out.println("한 번은 실행됩니다");
} while (j < 5);  // 조건은 거짓이지만 위 코드는 실행됨
```

**while vs do-while 비교**

```java
// while: 조건이 거짓이면 한 번도 실행 안 됨
int x = 10;
while (x < 5) {
    System.out.println("실행 안 됨");
}

// do-while: 조건이 거짓이어도 한 번은 실행됨
int y = 10;
do {
    System.out.println("한 번은 실행됨");
} while (y < 5);
```

---

### 10.6 break와 continue

**break 문**
- 반복문을 즉시 종료하고 빠져나옴
- switch 문에서도 사용

```java
// Java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break;  // i가 5이면 반복 종료
    }
    System.out.println(i);
}
// 출력: 1 2 3 4
```

**continue 문**
- 현재 반복을 건너뛰고 다음 반복으로 이동
- 반복문을 종료하지는 않음

```java
// Java
for (int i = 1; i <= 10; i++) {
    if (i % 2 == 0) {
        continue;  // 짝수면 건너뛰기
    }
    System.out.println(i);
}
// 출력: 1 3 5 7 9 (홀수만)
```

**중첩 반복문에서의 break**

```java
// Java
outer:  // 레이블 지정
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        if (i * j == 4) {
            break outer;  // 외부 반복문까지 종료
        }
        System.out.println(i + " * " + j + " = " + (i * j));
    }
}
```

---

### 10.7 향상된 for 문 (Enhanced for loop)

배열이나 컬렉션의 모든 요소를 순회할 때 사용합니다.

**Java**
```java
// 배열 순회
int[] numbers = {1, 2, 3, 4, 5};
for (int num : numbers) {
    System.out.println(num);
}

// 리스트 순회
ArrayList<String> names = new ArrayList<>();
names.add("홍길동");
names.add("김철수");
for (String name : names) {
    System.out.println(name);
}
```

**Python**
```python
# 리스트 순회
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    print(num)

# 인덱스와 값을 함께 가져오기
fruits = ["사과", "바나나", "오렌지"]
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")
```

---

### 🎯 기출문제 따라잡기

<div class="quiz-container">

**문제 1.** 다음 Java 코드의 출력 결과는?

```java
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 2; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

① * * *
② **<br>**<br>**
③ <span class="green-text">**<br>**<br>**</span>
④ * * * * * *

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ③</strong><br><br>
외부 루프 3번 × 내부 루프 2번 = 각 줄에 별 2개씩 3줄 출력
</div>
</details>

---

**문제 2.** Python에서 1부터 10까지의 숫자 중 홀수만 출력하는 코드는?

① for i in range(1, 10):<br>&nbsp;&nbsp;&nbsp;&nbsp;if i % 2 == 1: print(i)
② <span class="green-text">for i in range(1, 11, 2):<br>&nbsp;&nbsp;&nbsp;&nbsp;print(i)</span>
③ for i in range(10):<br>&nbsp;&nbsp;&nbsp;&nbsp;if i % 2 == 0: print(i)
④ for i in range(2, 11, 2):<br>&nbsp;&nbsp;&nbsp;&nbsp;print(i)

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ②</strong><br><br>
range(1, 11, 2)는 1부터 10까지 2씩 증가 → 1, 3, 5, 7, 9 (홀수)
</div>
</details>

---

**문제 3.** while문과 do-while문의 차이점으로 올바른 것은?

① while문이 더 빠르다
② <span class="green-text">do-while문은 최소 한 번은 실행된다</span>
③ do-while문은 조건을 검사하지 않는다
④ while문은 무한루프를 만들 수 없다

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ②</strong><br><br>
do-while문은 조건 검사를 루프 끝에서 하므로 조건과 관계없이 최소 한 번은 실행됩니다.
</div>
</details>

---

**문제 4.** 다음 코드의 출력 결과는?

```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        continue;
    }
    if (i == 8) {
        break;
    }
    System.out.print(i + " ");
}
```

① 1 2 3 4 6 7
② 1 2 3 4 5 6 7
③ <span class="green-text">1 2 3 4 6 7</span>
④ 1 2 3 4

<details>
<summary><span class="green-text">정답 보기</span></summary>
<div style="background: #ffffff; padding: 15px; margin-top: 10px; border-radius: 8px; border: 1px solid #e5e7eb;">
<strong>정답: ③</strong><br><br>
i=5일 때 continue로 건너뛰고, i=8일 때 break로 종료. 따라서 1 2 3 4 6 7 출력
</div>
</details>

</div>

---

## 📝 2장 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">005. 데이터 타입</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>기본 자료형</strong>: 값 자체를 저장 (int, double, char, boolean 등)</li>
<li><strong>참조 자료형</strong>: 메모리 주소를 저장 (String, Array, Class 등)</li>
<li><strong>Java 정수형</strong>: byte(1), short(2), int(4), long(8)</li>
<li><strong>Java 실수형</strong>: float(4), double(8)</li>
</ul>

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">006. 변수</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>선언</strong>: 메모리 공간 할당, <strong>초기화</strong>: 초기값 할당</li>
<li><strong>명명 규칙</strong>: 문자/숫자/밑줄 사용, 숫자 시작 불가, 예약어 불가</li>
<li><strong>스코프</strong>: 지역 변수, 인스턴스 변수, 클래스 변수</li>
</ul>

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">007. 연산자</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>산술</strong>: +, -, *, /, % (나머지)</li>
<li><strong>비교</strong>: ==, !=, &gt;, &lt;, &gt;=, &lt;=</li>
<li><strong>논리</strong>: &amp;&amp;(AND), ||(OR), !(NOT)</li>
<li><strong>비트</strong>: &amp;, |, ^, ~, &lt;&lt;, &gt;&gt;</li>
<li><strong>우선순위</strong>: () → 단항 → 산술 → 비교 → 논리 → 대입</li>
</ul>

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">008. 데이터 입·출력</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>Java 출력</strong>: print(), println(), printf()</li>
<li><strong>Java 입력</strong>: Scanner 클래스 (nextInt, nextLine 등)</li>
<li><strong>Python 출력</strong>: print() (sep, end 매개변수)</li>
<li><strong>Python 입력</strong>: input() (항상 문자열 반환)</li>
</ul>

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">009. 제어문</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>if-else</strong>: 조건에 따른 분기</li>
<li><strong>switch-case</strong>: 값에 따른 분기 (break 필수)</li>
<li><strong>삼항 연산자</strong>: (조건) ? 참 : 거짓</li>
</ul>

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">010. 반복문</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>for</strong>: 정해진 횟수만큼 반복</li>
<li><strong>while</strong>: 조건이 참인 동안 반복</li>
<li><strong>do-while</strong>: 최소 한 번은 실행 (Java/C만)</li>
<li><strong>break</strong>: 반복 종료, <strong>continue</strong>: 다음 반복으로</li>
</ul>

</div>

---

## 📚 다음 학습 내용

다음 장에서는 <span class="blue-text">프로그래밍 언어 응용 - 02</span>에 대해 학습합니다.

- 배열과 문자열
- 함수와 메소드
- 파일 입출력
- 예외 처리

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💪</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
이번 장에서 학습한 제어문과 반복문은 프로그래밍의 핵심입니다. 다양한 예제를 직접 작성하고 실행해보면서 개념을 완전히 이해하세요!
</p>
</div>

---

<div style="text-align: center; margin-top: 50px; color: #888;">
<p>본 자료는 프로그래밍기능사 시험 대비용 학습 자료입니다.</p>
<p>© 2026 Programming Technician Study Notes</p>
</div>
