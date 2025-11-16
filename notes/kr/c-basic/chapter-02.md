---
layout: article
title: 2. 변수와 자료형
permalink: /notes/kr/c-basic/chapter-02
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C 기초 과정 강의 노트, 변수의 선언과 초기화, 기본 자료형, 형 변환, printf 함수 활용 방법을 다룹니다.
keywords: "C언어, 변수, 자료형, int, float, double, char, printf, 형변환"
---

<script src="/assets/js/quiz.js"></script>

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
    .quiz-container {
        margin: 20px 0;
        padding: 15px;
        border: 1px solid #e0e0e0;
        border-radius: 8px;
        background-color: #f9f9f9;
    }
    .quiz-container:hover {
        box-shadow: 0 2px 8px rgba(0,0,0,0.1);
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

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=C%20Programming%20Basic&reversal=false&textBg=false)

---

## 1. 변수란?

변수는 데이터를 저장하는 <span class="blue-text">메모리 공간</span>입니다. 값을 담는 상자라고 생각하면 쉽습니다.

```c
int number = 3;  // 정수형 변수 number를 선언하고 3을 저장
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>변수 = 값을 저장하는 메모리 공간</strong><br>
변수를 선언하면 메모리에 공간이 할당되고, 그 공간에 값을 저장할 수 있습니다.
</div>

---

## 2. 변수명 규칙

변수명을 지을 때는 다음 규칙을 따라야 합니다:

- **문자, 숫자, 언더바(_)만** 사용 가능 (특수문자 ✕)
- **숫자로 시작 불가** (✕ `3number`, ✓ `number3`)
- **키워드 사용 불가** (✕ `int`, `return`, `if` 등)
- **대소문자 구분** (`Number`와 `number`는 다른 변수)

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 좋은 변수명 짓기</strong><br>
의미있는 이름을 사용하세요: <span class="green-text">age</span>, <span class="green-text">studentCount</span> (✓)<br>
무의미한 이름은 피하세요: <span class="red-text">a</span>, <span class="red-text">x123</span> (✕)
</div>

```c
// 올바른 변수명
int age = 25;
int student_count = 30;
int number1 = 10;

// 잘못된 변수명
int 3number = 10;    // 숫자로 시작 (에러!)
int hello boy = 3;   // 공백 포함 (에러!)
int int = 5;         // 키워드 사용 (에러!)
```

---

## 3. 변수 선언과 초기화

### 선언

```c
int number;        // 변수 선언만 (값 없음)
```

### 초기화

```c
int number = 10;   // 선언과 동시에 초기화
```

### 다양한 초기화 방법

```c
// 한 번에 여러 변수 선언
int number1, number2;

// 선언과 초기화를 동시에
int number3 = 3, number4 = 4;
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 초기화하지 않은 변수</strong><br>
선언만 하고 초기화하지 않으면 <span class="red-text">쓰레기 값(garbage value)</span>이 들어있습니다. 반드시 초기화 후 사용하세요!
</div>

### 실습 1

다음 코드의 실행 결과를 확인해보세요:

```c
#include <stdio.h>

int main() {
    int number1, number2;
    number1 = 1;
    number2 = 2;
    int number3 = 3, number4 = 4;
    
    printf("%d\n", number1);
    printf("%d\n", number2);
    printf("%d\n", number3);
    printf("%d\n", number4);
    
    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
1
2
3
4
</pre>

</details>

---

## 4. C언어 기본 자료형

| 자료형 | 의미 | 크기 | 값의 범위 |
|--------|------|------|-----------|
| `char` | 문자 | 1바이트 | -128 ~ 127 |
| `short` | 정수 | 2바이트 | -32,768 ~ 32,767 |
| `int` | 정수 | 4바이트 | 약 -21억 ~ 21억 |
| `long` | 정수 | 4/8바이트 | 약 -21억 ~ 21억 |
| `float` | 실수 | 4바이트 | 소수점 7자리 |
| `double` | 실수 | 8바이트 | 소수점 15자리 |

### 정수형

```c
int age = 25;
short temperature = -10;
long population = 5000000;
```

### 실수형

```c
float pi = 3.14f;        // f를 붙여 float 표시
double e = 2.718281828;
```

### 문자형

```c
char grade = 'A';        // 단일 문자는 작은따옴표
```

### 실습 2

다음 프로그램을 작성하고 실행해보세요:

```c
#include <stdio.h>

int main() {
    double number1 = 10;
    int number2 = 1.2345;
    short number3 = 70000;
    
    printf("%f\n%d\n%d", number1, number2, number3);
    
    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 및 설명 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
10.000000
1
4464
</pre>

<ul style="margin-top: 10px;">
<li><span class="blue-text">05번:</span> 정수를 double에 저장하면 실수형으로 변환됩니다.</li>
<li><span class="blue-text">06번:</span> 실수를 int에 저장하면 소수점 이하가 잘립니다.</li>
<li><span class="blue-text">07번:</span> short 범위를 초과하면 오버플로우가 발생합니다.</li>
</ul>

</details>

---

## 5. printf 함수로 출력하기

`printf` 함수는 화면에 데이터를 출력하는 함수입니다.

### 형식 지정자

| 지정자 | 의미 |
|--------|------|
| `%d` | 정수 (int) |
| `%ld` | 정수 (long) |
| `%f` | 실수 (float, double) |
| `%c` | 문자 (char) |
| `%s` | 문자열 |

### 기본 사용법

```c
#include <stdio.h>

int main() {
    int number1 = 3;
    int number2 = 5;
    
    printf("%d\n%d\n", number1, number2);
    
    return 0;
}
```

출력:
```
3
5
```

### 실습 3

다음 프로그램의 실행 결과를 확인해보세요:

```c
#include <stdio.h>

int main() {
    int number1 = 8;
    int number2 = 10;
    
    printf("%d", number1 + number2);
    
    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
18
</pre>

</details>

---

## 6. 형 변환 (Type Casting)

### 명시적 형 변환

자료형을 강제로 변환하는 것을 <span class="blue-text">형 변환(Type Casting)</span>이라고 합니다.

```c
double number = 10;    // 10.0으로 변환
int result = 5.4321;   // 5로 변환 (소수점 이하 버림)
short number = 200;    // 200으로 변환
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 주의</strong><br>
정수를 실수로 변환하면 소수점 이하 손실이 발생합니다.<br>
자료형 범위를 초과하면 <span class="red-text">오버플로우</span>가 발생합니다.
</div>

### 실습 4

<div class="quiz-number">실습 1</div><strong>다음 C 프로그램에서 sizeof(100)의 결과는 무엇입니까?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    printf("%d, %d", sizeof(100), sizeof(3.14));
    
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint4 %}
정수 100은 int형으로 처리되어 4바이트입니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   question=hint4
   code_html=code_block4
   answer="4, 8"
   tags="변수와 자료형"
%}

---

## 7. 문자 다루기

문자는 <span class="blue-text">char</span> 자료형을 사용하며, **작은따옴표**로 표현합니다.

```c
char ch1 = 'A';   // 문자 'A' 저장
```

### ASCII 코드

모든 문자는 숫자로 표현됩니다. 이를 <span class="blue-text">ASCII 코드</span>라고 합니다.

```c
char ch1 = 66;     // 숫자 66 저장 (ASCII 코드로 'B')
char ch2 = 'B';    // 문자 'B' 저장 (내부적으로는 66)
```

### 실습 5

<div class="quiz-number">실습 2</div><strong>다음 C 프로그램에서 printf("%c\n", ch1)의 실행 결과는 무엇입니까?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    char ch1 = 66;
    
    printf("%c", ch1);
    
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint5 %}
<code>%c</code>는 숫자를 문자로 출력하며, ASCII 코드 66은 'B'입니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   question=hint5
   code_html=code_block5
   answer="B"
   tags="변수와 자료형"
%}

---

## 8. 상수 (Constant)

### 리터럴 상수

코드에 직접 작성한 값을 말합니다.

```c
int number = 10;   // 10이 리터럴 상수
```

### 심볼릭 상수 (const)

변경할 수 없는 변수를 만들 때 사용합니다.

```c
const int LENGTH = 10;
// LENGTH = 20;  // 에러! const 변수는 변경 불가
```

<div style="background-color: #e8f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #448F52;">
<strong>✓ const를 사용하는 이유</strong><br>
실수로 값을 변경하는 것을 방지하고, 코드의 의도를 명확히 전달할 수 있습니다.
</div>

### 매크로 상수 (#define)

컴파일 전에 치환되는 상수입니다.

```c
#define LENGTH 10

int main() {
    printf("%d", LENGTH);
    return 0;
}
```

### 실습 6

<div class="quiz-number">실습 3</div><strong>다음 C 프로그램에서 NUMBER의 값은 무엇입니까?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#define LENGTH 10

int main() {
    int number = 3;
    const int NUMBER = 5;
    
    // 에러가 발생하는 코드는?
    number = 10;
    NUMBER = 10;
    
    printf("%d, %d, %d", LENGTH, number, NUMBER);
    
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint6 %}
const로 선언된 변수는 값을 변경할 수 없으므로 초기값인 5가 유지됩니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   question=hint6
   code_html=code_block6
   answer="10, 10, 5"
   tags="변수와 자료형"
%}

---

## 9. 종합 실습

### 문제 1 - sizeof 연산자 (기초)

<div class="quiz-number">문제 1</div><strong>다음 C 프로그램에서 sizeof(char)의 결과는 무엇입니까?</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    printf("%d", sizeof(char));
    
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint7 %}
char 자료형은 1바이트 크기를 가집니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   question=hint7
   code_html=code_block7
   answer="1"
   tags="변수와 자료형"
%}

---

### 문제 2 - 실수형 변환 (기초)

<div class="quiz-number">문제 2</div><strong>3.14는 기본적으로 double형입니다. float 변수 f에 3.14를 저장할 때 컴파일 경고가 발생하지 않도록 하려면 어떻게 작성해야 합니까? (f를 포함하여 작성)</strong>

{% capture hint8 %}
실수 리터럴 뒤에 특정 접미사를 붙여 float형임을 명시해야 합니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=hint8
   answer="3.14f|3.14F|float f = 3.14f;|float f = 3.14F;"
   tags="변수와 자료형"
%}

---

### 문제 3 - 문자형 출력 (기초)

<div class="quiz-number">문제 3</div><strong>다음 C 프로그램에서 printf("%d\n", ch2)의 실행 결과는 무엇입니까?</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    char ch2 = 'B';
    
    printf("%d\n", ch2);
    
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint9 %}
'B'는 ASCII 코드로 66이며, %d로 출력하면 숫자로 표시됩니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   question=hint9
   code_html=code_block9
   answer="66"
   tags="변수와 자료형"
%}

---

### 문제 4 - 변수 교환 (중급)

<div class="quiz-number">문제 4</div><strong>다음 C 프로그램에서 변수 교환 후 a의 값은 무엇입니까?</strong>

{% capture code_block10 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int a = 10, b = 20;
    int temp = a;
    a = b;
    b = temp;
    
    printf("a = %d, b = %d\n", a, b);
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint10 %}
temp 변수를 이용하여 a와 b의 값을 교환합니다. 교환 후 a는 b의 값인 20을 가집니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz7"
   question=hint10
   code_html=code_block10
   answer="a = 20, b = 10"
   tags="변수와 자료형"
%}

---

### 문제 5 - 평균 계산 (중급)

<div class="quiz-number">문제 5</div><strong>다음 C 프로그램에서 average의 값을 소수점 둘째 자리까지 작성하세요. (예: 87.67)</strong>

{% capture code_block11 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int korean = 90, english = 85, math = 88;
    double average = (korean + english + math) / 3.0;
    
    printf("평균: %.2f\n", average);
    
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint11 %}
(90 + 85 + 88) / 3.0 = 263 / 3.0 = 87.666...이며, 소수점 둘째 자리까지 표시하면 87.67입니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz8"
   question=hint11
   code_html=code_block11
   answer="87.67"
   tags="변수와 자료형"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

**1. 변수**
- 데이터를 저장하는 메모리 공간
- 선언 시 자료형을 반드시 지정

**2. 자료형**
- 정수: `char`, `short`, `int`, `long`
- 실수: `float`, `double`
- 문자: `char` (작은따옴표 사용)

**3. printf 형식 지정자**
- `%d`: 정수, `%f`: 실수, `%c`: 문자

**4. 상수**
- `const`: 변경 불가능한 변수
- `#define`: 매크로 상수 (컴파일 전 치환)

**5. 형 변환**
- 명시적 변환: `(자료형)변수`
- 자동 변환: 더 큰 자료형으로 자동 변환

</div>

---

