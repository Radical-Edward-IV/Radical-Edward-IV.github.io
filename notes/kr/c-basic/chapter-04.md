---
layout: article
title: 4. 연산자
permalink: /notes/kr/c-basic/chapter-04
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C 기초 과정 강의 노트, 산술/대입/비교/증감/논리 연산자 및 연산자 우선순위를 다룹니다.
keywords: "C언어, 연산자, 산술연산자, 비교연산자, 논리연산자, 증감연산자, 삼항연산자"
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

## 1. 산술 연산자

산술 연산자는 덧셈, 뺄셈, 곱셈, 나눗셈 등 수학적 연산을 수행하는 연산자입니다.

### 기본 산술 연산자

| 연산자 | 기능 | 사용 예 |
|--------|------|---------|
| `+` | 두 값을 더합니다 | `5 + 3` → `8` |
| `-` | 왼쪽 값에서 오른쪽 값을 뺍니다 | `10 - 4` → `6` |
| `*` | 두 값을 곱합니다 | `6 * 8` → `48` |
| `/` | 왼쪽 값을 오른쪽 값으로 나눕니다 | `9 / 3` → `3` |
| `%` | 나눗셈의 나머지를 구합니다 | `9 % 2` → `1` |

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 나머지 연산자 %</strong><br>
나머지 연산자는 정수 나눗셈에서만 사용 가능합니다. 홀수/짝수 판별, 배수 확인 등에 유용합니다.
</div>

### 실습 1

다음 코드를 실행해보세요:

```c
#include <stdio.h>

int main() {
    int num1 = 7, num2 = 3;

    printf("%d + %d = %d\n", num1, num2, num1 + num2);
    printf("%d - %d = %d\n", num1, num2, num1 - num2);
    printf("%d * %d = %d\n", num1, num2, num1 * num2);
    printf("%d / %d = %d\n", num1, num2, num1 / num2);
    printf("%d %% %d = %d\n", num1, num2, num1 % num2);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
7 + 3 = 10
7 - 3 = 4
7 * 3 = 21
7 / 3 = 2
7 % 3 = 1
</pre>

<ul style="margin-top: 10px;">
<li><span class="blue-text">정수 나눗셈:</span> 7 / 3 = 2 (소수점 이하 버림)</li>
<li><span class="blue-text">나머지:</span> 7을 3으로 나눈 나머지는 1</li>
</ul>

</details>

### 연산 결과의 자료형

산술 연산의 결과는 두 피연산자의 자료형에 따라 결정됩니다.

| 피연산자 자료형 | 결과 자료형 |
|----------------|------------|
| `int` + `int` | `int` |
| `int` + `float` | `float` |
| `double` + `int` | `double` |
| `char` + `char` | `int` |

```c
int result1 = 7 / 3;      // 2 (정수 나눗셈)
double result2 = 7 / 3;   // 2.0 (여전히 정수 나눗셈 후 double로 변환)
double result3 = 7.0 / 3; // 2.333... (실수 나눗셈)
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 정수 나눗셈 주의</strong><br>
정수끼리 나누면 결과도 정수입니다. 실수 결과를 얻으려면 최소 하나를 실수로 만드세요.
</div>

---

## 2. 대입 연산자

대입 연산자는 값을 변수에 저장하는 연산자입니다.

### 기본 대입 연산자

```c
int num = 10;   // 변수 num에 10을 대입
```

### 복합 대입 연산자

| 연산자 | 사용 예 | 의미 |
|--------|---------|------|
| `+=` | `num += 3` | `num = num + 3` |
| `-=` | `num -= 5` | `num = num - 5` |
| `*=` | `num *= 7` | `num = num * 7` |
| `/=` | `num /= 9` | `num = num / 9` |
| `%=` | `num %= 2` | `num = num % 2` |

### 실습 2

```c
#include <stdio.h>

int main() {
    int num1 = 10, num2 = 20;

    num1 += 5;   // num1 = num1 + 5;
    num2 *= 2;   // num2 = num2 * 2;

    printf("num1 = %d\n", num1);  // 15
    printf("num2 = %d\n", num2);  // 40

    return 0;
}
```

---

## 3. 비교 연산자

비교 연산자는 두 값을 비교하여 참(1) 또는 거짓(0)을 반환합니다.

### 비교 연산자 종류

| 연산자 | 의미 | 사용 예 |
|--------|------|---------|
| `==` | 같은가? | `a == b` |
| `!=` | 다른가? | `a != b` |
| `<` | 작은가? | `a < b` |
| `>` | 큰가? | `a > b` |
| `<=` | 작거나 같은가? | `a <= b` |
| `>=` | 크거나 같은가? | `a >= b` |

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 주의</strong><br>
대입 연산자 <span class="red-text">=</span>와 비교 연산자 <span class="blue-text">==</span>를 혼동하지 마세요!<br>
<code>if (num = 5)</code> ❌ 대입<br>
<code>if (num == 5)</code> ✅ 비교
</div>

### 실습 3

```c
#include <stdio.h>

int main() {
    int a = 10, b = 20;

    printf("a == b : %d\n", a == b);  // 0 (거짓)
    printf("a != b : %d\n", a != b);  // 1 (참)
    printf("a < b  : %d\n", a < b);   // 1 (참)
    printf("a > b  : %d\n", a > b);   // 0 (거짓)

    return 0;
}
```

---

## 4. 증감 연산자

증감 연산자는 변수의 값을 1만큼 증가 또는 감소시킵니다.

### 증감 연산자 종류

| 연산자 | 의미 | 사용 예 |
|--------|------|---------|
| `++` | 1 증가 | `num++`, `++num` |
| `--` | 1 감소 | `num--`, `--num` |

### 전위와 후위의 차이

**전위(Prefix)**: 먼저 증가/감소 후 사용
```c
int num = 5;
printf("%d\n", ++num);  // 6 출력 (먼저 증가)
```

**후위(Postfix)**: 먼저 사용 후 증가/감소
```c
int num = 5;
printf("%d\n", num++);  // 5 출력 (나중에 증가)
printf("%d\n", num);    // 6 출력
```

### 실습 4

<div class="quiz-number">실습 1</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int a = 10;
    int b = ++a;
    int c = a++;

    printf("%d, %d, %d", a, b, c);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint1 %}
전위는 먼저 증가, 후위는 나중에 증가합니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   question=hint1
   code_html=code_block1
   answer="12, 11, 11"
   tags="연산자"
%}

---

## 5. 논리 연산자

논리 연산자는 참(1)과 거짓(0)을 다루는 연산자입니다.

### 논리 연산자 종류

| 연산자 | 의미 | 설명 |
|--------|------|------|
| `&&` | AND | 모두 참이면 참 |
| `||` | OR | 하나라도 참이면 참 |
| `!` | NOT | 참↔거짓 반전 |

### 진리표

**AND (&&)**
- `1 && 1` → `1`
- `1 && 0` → `0`
- `0 && 0` → `0`

**OR (||)**
- `1 || 1` → `1`
- `1 || 0` → `1`
- `0 || 0` → `0`

**NOT (!)**
- `!1` → `0`
- `!0` → `1`

### 실습 5

```c
#include <stdio.h>

int main() {
    int age = 20;
    int score = 85;

    // AND: 나이가 18 이상이고 점수가 80 이상
    if (age >= 18 && score >= 80) {
        printf("합격!\n");
    }

    // OR: 나이가 60 이상이거나 학생
    if (age >= 60 || score >= 90) {
        printf("할인 대상\n");
    }

    // NOT: 성인이 아님
    if (!(age >= 18)) {
        printf("미성년자\n");
    }

    return 0;
}
```

---

## 6. 삼항 조건 연산자

삼항 조건 연산자는 조건에 따라 다른 값을 반환하는 연산자입니다.

### 기본 형태

```c
조건 ? 참일_때_값 : 거짓일_때_값
```

### 사용 예

```c
int num = 10;
int result = (num > 5) ? 100 : 200;  // result = 100

// 절댓값 구하기
int value = -15;
int absolute = (value >= 0) ? value : -value;  // absolute = 15
```

### 실습 6

<div class="quiz-number">실습 2</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int a = 15, b = 20;
    int max = (a > b) ? a : b;

    printf("최댓값: %d", max);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint2 %}
a(15)가 b(20)보다 크지 않으므로 b가 선택됩니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   question=hint2
   code_html=code_block2
   answer="최댓값: 20"
   tags="연산자"
%}

---

## 7. 연산자 우선순위

여러 연산자가 함께 사용될 때는 우선순위에 따라 계산됩니다.

### 주요 연산자 우선순위

| 우선순위 | 연산자 | 의미 | 결합 방향 |
|---------|--------|------|-----------|
| 1 | `++`, `--` (전위) | 증감 | → |
| 2 | `!` | 논리 NOT | → |
| 3 | `*`, `/`, `%` | 곱셈, 나눗셈 | ← |
| 4 | `+`, `-` | 덧셈, 뺄셈 | ← |
| 5 | `<`, `>`, `<=`, `>=` | 비교 | ← |
| 6 | `==`, `!=` | 동등 | ← |
| 7 | `&&` | 논리 AND | ← |
| 8 | `||` | 논리 OR | ← |
| 9 | `?:` | 삼항 연산자 | → |
| 10 | `=`, `+=`, `-=` | 대입 | → |

### 연산 순서 예제

```c
int result = 3 + 4 * 5;  // 23 (곱셈 먼저)
// 4 * 5 = 20
// 3 + 20 = 23

int value = 10 > 5 && 20 < 30;  // 1 (참)
// 10 > 5 = 1 (참)
// 20 < 30 = 1 (참)
// 1 && 1 = 1
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>💡 팁</strong><br>
복잡한 연산식에서는 괄호 <code>()</code>를 사용하면 가독성이 높아지고 의도가 명확해집니다.
</div>

---

## 8. 종합 실습

### 문제 1 - 나머지 연산 (기초)

<div class="quiz-number">문제 1</div><strong>17 % 5의 결과는?</strong>

{% capture hint3 %}
17을 5로 나눈 나머지를 구하세요.
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   question=hint3
   answer="2"
   tags="연산자"
%}

---

### 문제 2 - 증감 연산자 (중급)

<div class="quiz-number">문제 2</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int x = 5;
    int y = ++x + x++;

    printf("%d, %d", x, y);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint4 %}
전위 ++x는 먼저 증가(6), 그 다음 x++(6 사용 후 7로 증가)
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   question=hint4
   code_html=code_block3
   answer="7, 12"
   tags="연산자"
%}

---

### 문제 3 - 논리 연산 (중급)

<div class="quiz-number">문제 3</div><strong>다음 조건의 결과는 참(1) 또는 거짓(0)?</strong>

```c
int a = 10, b = 20, c = 30;
(a < b) && (b < c) && (a + b > c)
```

{% capture hint5 %}
각 조건을 순서대로 확인: (10 < 20) && (20 < 30) && (30 > 30)
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=hint5
   answer="0"
   tags="연산자"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 산술 연산자</strong><br>
• <code>+</code>, <code>-</code>, <code>*</code>, <code>/</code>, <code>%</code><br>
• 정수 나눗셈은 소수점 이하 버림<br><br>

<strong>2. 대입 연산자</strong><br>
• 기본: <code>=</code><br>
• 복합: <code>+=</code>, <code>-=</code>, <code>*=</code>, <code>/=</code>, <code>%=</code><br><br>

<strong>3. 비교 연산자</strong><br>
• <code>==</code>, <code>!=</code>, <code>&lt;</code>, <code>&gt;</code>, <code>&lt;=</code>, <code>&gt;=</code><br>
• 결과는 참(1) 또는 거짓(0)<br><br>

<strong>4. 증감 연산자</strong><br>
• 전위(prefix): <code>++num</code> (먼저 증가)<br>
• 후위(postfix): <code>num++</code> (나중에 증가)<br><br>

<strong>5. 논리 연산자</strong><br>
• AND(<code>&&</code>): 모두 참<br>
• OR(<code>||</code>): 하나라도 참<br>
• NOT(<code>!</code>): 반전<br><br>

<strong>6. 우선순위</strong><br>
• 산술 → 비교 → 논리 → 대입 순서<br>
• 괄호로 우선순위 명시 가능

</div>

---
