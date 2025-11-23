---
layout: article
title: 2. 데이터 표현 방식
permalink: /notes/kr/c-basic/chapter-02
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C 기초 과정 강의 노트, 2진수, 비트와 바이트, 정수와 실수의 표현 방식, unsigned 자료형을 다룹니다.
keywords: "C언어, 2진수, 비트, 바이트, 정수표현, 실수표현, unsigned, 2의보수, 부동소수점"
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

## 1. 2진수의 이해

"컴퓨터는 1과 0밖에 모르는 바보다"라는 말을 들어보셨나요? 컴퓨터는 모든 데이터를 <span class="blue-text">2진수</span>로 표현하고 처리합니다.

### 10진수와 2진수

**10진수**는 우리가 일상에서 사용하는 수 체계로, 0부터 9까지 열 가지 기호를 사용합니다.

**2진수**는 0과 1, 두 가지 기호만을 사용하여 값을 표현합니다.

### 10진수와 2진수 변환표

| 10진수 | 2진수 | 설명 |
|--------|-------|------|
| 0 | 0 | 0은 그대로 0 |
| 1 | 1 | 1은 그대로 1 |
| 2 | 10 | 1보다 큰 수부터 자릿수를 올림 |
| 3 | 11 | |
| 4 | 100 | |
| 5 | 101 | |
| 6 | 110 | |
| 7 | 111 | |
| 8 | 1000 | |
| 9 | 1001 | |
| 10 | 1010 | |
| 15 | 1111 | |
| 16 | 10000 | |

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>2진수의 특징</strong><br>
2진수에는 0과 1 외의 다른 기호가 없습니다. 10진수에서 9보다 큰 수를 표현할 때 자릿수를 올리듯, 2진수는 1보다 큰 수부터 자릿수를 올립니다.
</div>

### 2진수 → 10진수 변환

2진수를 10진수로 변환하려면 각 자리의 값에 2의 거듭제곱을 곱합니다.

**예시: 2진수 1011을 10진수로 변환**

```
1011(2) = 1×2³ + 0×2² + 1×2¹ + 1×2⁰
        = 1×8 + 0×4 + 1×2 + 1×1
        = 8 + 0 + 2 + 1
        = 11(10)
```

---

## 2. 비트와 바이트

컴퓨터 메모리의 기본 단위는 <span class="blue-text">비트(bit)</span>와 <span class="blue-text">바이트(byte)</span>입니다.

### 비트 (bit)

- 컴퓨터 메모리의 가장 작은 단위
- 0 또는 1의 값만 저장 가능
- binary digit의 약자

### 바이트 (byte)

- 비트 8개가 모여 이루어진 단위
- 1바이트 = 8비트
- 대부분의 자료형 크기는 바이트 단위로 표현

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>1바이트로 표현 가능한 값의 개수</strong><br>
8비트 = 2⁸ = 256가지 (0~255 또는 -128~127)
</div>

### char형 데이터 표현 예시

```c
char ch = 0;   // 00000000 (8비트 모두 0)
ch = 1;        // 00000001
ch = 2;        // 00000010
ch = 7;        // 00000111
```

**비트 구조:**

| 비트 위치 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|---------|---|---|---|---|---|---|---|---|
| 값 (ch=7) | 0 | 0 | 0 | 0 | 0 | 1 | 1 | 1 |
| 설명 | MSB | | | | | | | LSB |

- **MSB** (Most Significant Bit): 가장 왼쪽 비트, 가장 큰 자릿수
- **LSB** (Least Significant Bit): 가장 오른쪽 비트, 가장 작은 자릿수

---

## 3. 정수의 표현

정수형 데이터는 2진수로 표현되며, 음수 표현을 위해 <span class="blue-text">2의 보수</span> 방식을 사용합니다.

### 정수 표현 구조 (1바이트 기준)

| 비트 | 7 | 6 | 5 | 4 | 3 | 2 | 1 | 0 |
|------|---|---|---|---|---|---|---|---|
| 역할 | 부호 비트 | 값 | 값 | 값 | 값 | 값 | 값 | 값 |

- **부호 비트 (7번 비트)**
  - 0: 양수
  - 1: 음수

### 양수 표현

양수는 2진수를 그대로 사용합니다.

| 10진수 | 2진수 (1바이트) | 설명 |
|--------|----------------|------|
| 0 | 00000000 | 모든 비트 0 |
| 1 | 00000001 | |
| 127 | 01111111 | 1바이트 최댓값 |

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 1바이트 signed 정수 범위</strong><br>
최솟값: -128<br>
최댓값: +127<br>
총 256가지 값 표현 가능
</div>

### 음수 표현 - 2의 보수

음수를 표현하려면 단순히 부호 비트만 바꾸면 안 됩니다. <span class="blue-text">2의 보수</span>를 사용해야 합니다.

**2의 보수 구하는 방법:**

1. 모든 비트를 반전 (0→1, 1→0)
2. 결과에 1을 더함

**예시: -5를 2진수로 표현**

```
1단계: +5의 2진수
00000101

2단계: 모든 비트 반전
11111010

3단계: 1을 더함
11111010
+      1
--------
11111011  ← -5의 2진수 표현
```

### 왜 2의 보수를 사용하나요?

2의 보수를 사용하면 덧셈 연산만으로 뺄셈을 수행할 수 있습니다.

```
예: 5 + (-5) = 0인지 확인

  00000101  (+5)
+ 11111011  (-5)
----------
1 00000000  (캐리는 버려지고 0이 됨)
```

<div style="background-color: #e8f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #448F52;">
<strong>✓ 2의 보수의 장점</strong><br>
• 덧셈 회로만으로 뺄셈 가능<br>
• 하드웨어 설계가 간단해짐<br>
• 0의 표현이 하나만 존재 (00000000)
</div>

---

## 4. 실수의 표현

실수는 정수보다 복잡한 방식으로 표현됩니다. <span class="blue-text">부동소수점(floating point)</span> 방식을 사용합니다.

### 부동소수점 표현 구조

실수는 다음 세 부분으로 나뉩니다:

| 구성 요소 | 설명 | float (32비트) | double (64비트) |
|----------|------|----------------|----------------|
| 부호 비트 (S) | 양수/음수 구분 | 1비트 | 1비트 |
| 지수부 (E) | 소수점 위치 | 8비트 | 11비트 |
| 가수부 (M) | 실제 값 | 23비트 | 52비트 |

### 부동소수점 표현 공식

```
값 = ±(1.M) × 2^(E - 127)
```

- **S**: 부호 (0: 양수, 1: 음수)
- **M**: 가수부 (소수점 이하 값)
- **E**: 지수부 (127을 기준으로 한 지수)

**예시: 5.75를 표현**

```
1. 5.75를 2진수로 변환
   5.75 = 101.11(2) = 1.0111 × 2²

2. 정규화된 형태
   1.0111 × 2²

3. 각 부분 추출
   부호(S): 0 (양수)
   지수(E): 2 + 127 = 129 = 10000001(2)
   가수(M): 0111 (1.0111에서 소수점 이하만)
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 부동소수점 오차</strong><br>
실수는 제한된 비트로 표현되므로 <span class="red-text">작은 오차</span>가 발생할 수 있습니다.<br>
<code>0.1 + 0.2 ≠ 0.3</code> (정확히 0.30000000000000004)
</div>

### float vs double

| 자료형 | 크기 | 유효 자릿수 | 범위 |
|--------|------|------------|------|
| `float` | 4바이트 (32비트) | 약 7자리 | ±3.4 × 10³⁸ |
| `double` | 8바이트 (64비트) | 약 15자리 | ±1.7 × 10³⁰⁸ |

---

## 5. unsigned 자료형

`unsigned`는 "부호가 없다"는 의미로, 음수를 표현하지 않고 0 이상의 값만 표현합니다.

### signed vs unsigned

| 자료형 | 크기 | 범위 |
|--------|------|------|
| `char` (signed) | 1바이트 | -128 ~ 127 |
| `unsigned char` | 1바이트 | 0 ~ 255 |
| `short` (signed) | 2바이트 | -32,768 ~ 32,767 |
| `unsigned short` | 2바이트 | 0 ~ 65,535 |
| `int` (signed) | 4바이트 | 약 -21억 ~ 21억 |
| `unsigned int` | 4바이트 | 0 ~ 약 42억 |

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>unsigned의 특징</strong><br>
• 부호 비트를 값 표현에 사용<br>
• 표현 가능한 값의 범위가 2배로 증가<br>
• 음수 표현 불가능
</div>

### unsigned 선언 예시

```c
unsigned char age = 25;       // 0~255
unsigned short count = 1000;  // 0~65535
unsigned int population = 5000000;  // 0~약 42억
unsigned long big_number = 4000000000UL;
```

### 실습 1

```c
#include <stdio.h>

int main() {
    char cnum = 128;           // signed char: -128~127
    unsigned char u_cnum = 128;

    short snum = 32768;        // signed short: -32768~32767
    unsigned short u_snum = 32768;

    printf("char: %d\n", cnum);
    printf("unsigned char: %u\n", u_cnum);
    printf("short: %d\n", snum);
    printf("unsigned short: %u\n", u_snum);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
char: -128
unsigned char: 128
short: -32768
unsigned short: 32768
</pre>

<ul style="margin-top: 10px;">
<li><span class="blue-text">signed char:</span> 128은 범위를 초과하여 오버플로우 발생 → -128</li>
<li><span class="blue-text">unsigned char:</span> 128은 범위 내 → 그대로 128</li>
<li><span class="blue-text">short:</span> 32768은 범위 초과 → -32768</li>
<li><span class="blue-text">unsigned short:</span> 32768은 범위 내 → 그대로 32768</li>
</ul>

</details>

---

## 6. 리터럴 접미사

C 언어에서는 숫자 리터럴에 접미사를 붙여 자료형을 명시할 수 있습니다.

### unsigned 접미사

| 접미사 | 의미 | 사용 예 |
|--------|------|---------|
| `U` 또는 `u` | unsigned int | `1000U` |
| `UL` 또는 `ul` | unsigned long | `100000UL` |
| `ULL` 또는 `ull` | unsigned long long | `10000000000ULL` |

### 실수 접미사

| 접미사 | 의미 | 사용 예 |
|--------|------|---------|
| `F` 또는 `f` | float | `3.14F` |
| 없음 | double (기본) | `3.14` |
| `L` 또는 `l` | long double | `3.14L` |

### 사용 예시

```c
unsigned int a = 1000U;
unsigned long b = 100000UL;
unsigned long long c = 10000000000ULL;

float pi = 3.14F;
double e = 2.718;
long double big = 3.14159265358979L;
```

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 접미사를 사용하는 이유</strong><br>
• 컴파일러에게 명확한 자료형 전달<br>
• 경고 메시지 방지<br>
• 의도하지 않은 형변환 방지
</div>

---

## 7. 종합 실습

### 문제 1 - 2진수 변환 (기초)

<div class="quiz-number">문제 1</div><strong>10진수 13을 2진수로 변환하면?</strong>

{% capture hint1 %}
13 = 8 + 4 + 1 = 2³ + 2² + 2⁰ = 1101(2)
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   question=hint1
   answer="1101"
   tags="데이터 표현 방식"
%}

---

### 문제 2 - 바이트 단위 (기초)

<div class="quiz-number">문제 2</div><strong>1바이트는 몇 비트인가?</strong>

{% capture hint2 %}
1바이트 = 8비트
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   question=hint2
   answer="8|8비트"
   tags="데이터 표현 방식"
%}

---

### 문제 3 - unsigned 범위 (중급)

<div class="quiz-number">문제 3</div><strong>unsigned char의 최댓값은?</strong>

{% capture hint3 %}
8비트를 모두 값 표현에 사용: 2⁸ - 1 = 255
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   question=hint3
   answer="255"
   tags="데이터 표현 방식"
%}

---

### 문제 4 - 2의 보수 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    char num = 127;
    num = num + 1;

    printf("%d", num);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint4 %}
char의 최댓값은 127입니다. 1을 더하면 오버플로우가 발생하여 -128이 됩니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   question=hint4
   code_html=code_block4
   answer="-128"
   tags="데이터 표현 방식"
%}

---

### 문제 5 - 접미사 (기초)

<div class="quiz-number">문제 5</div><strong>다음 중 올바른 unsigned long 리터럴은?</strong>

{% capture hint5 %}
unsigned long은 UL 또는 ul 접미사를 사용합니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=hint5
   answer="100000UL|100000ul"
   tags="데이터 표현 방식"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 2진수</strong><br>
• 0과 1만 사용하여 값을 표현<br>
• 1보다 큰 수부터 자릿수를 올림<br><br>

<strong>2. 비트와 바이트</strong><br>
• 비트(bit): 0 또는 1을 저장하는 최소 단위<br>
• 바이트(byte): 8비트 = 256가지 값 표현 가능<br><br>

<strong>3. 정수 표현</strong><br>
• 양수: 2진수 그대로 사용<br>
• 음수: 2의 보수 방식 사용<br>
• 2의 보수 = 비트 반전 + 1<br><br>

<strong>4. 실수 표현</strong><br>
• 부동소수점 방식: 부호 + 지수 + 가수<br>
• <code>float</code>: 32비트 (정밀도 낮음)<br>
• <code>double</code>: 64비트 (정밀도 높음)<br><br>

<strong>5. unsigned 자료형</strong><br>
• 부호 비트를 값 표현에 사용<br>
• 0 이상의 값만 표현 가능<br>
• 표현 범위가 2배로 증가<br><br>

<strong>6. 리터럴 접미사</strong><br>
• unsigned: <code>U</code>, <code>UL</code>, <code>ULL</code><br>
• 실수: <code>F</code>(float), 기본(double), <code>L</code>(long double)

</div>

---
