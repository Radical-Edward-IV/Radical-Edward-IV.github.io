---
layout: article
title: 7. 포인터 소개
permalink: /notes/kr/c-basic/chapter-07
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C 기초 과정 강의 노트, 포인터의 개념, 포인터 변수 선언, 주소 연산자와 간접 참조 연산자를 다룹니다.
keywords: "C언어, 포인터, 주소, 메모리, 포인터변수, 주소연산자, 간접참조연산자"
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

## 1. 포인터란?

포인터는 C 언어의 가장 강력하면서도 어려운 개념입니다. 포인터를 이해하면 메모리를 직접 제어할 수 있습니다.

### 메모리 주소의 이해

변수를 선언하면 메모리 공간이 할당되고, 각 메모리 공간에는 <span class="blue-text">주소(Address)</span>가 있습니다.

```c
int num = 100;
```

이 변수는 메모리 어딘가에 저장되며, 그 위치를 나타내는 주소값이 있습니다.

**메모리 구조 예시:**

```
주소          값
0x0012FF44   ...
0x0012FF48   100  ← num이 저장된 위치
0x0012FF4C   ...
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>포인터 = 메모리 주소를 저장하는 변수</strong><br>
포인터는 다른 변수의 메모리 주소를 값으로 가지는 특별한 변수입니다.
</div>

### 포인터가 필요한 이유

1. **동적 메모리 할당**: 프로그램 실행 중 필요한 만큼 메모리를 할당
2. **함수에서 값 변경**: 함수에서 원본 변수를 직접 수정
3. **효율적인 데이터 전달**: 큰 데이터를 복사하지 않고 주소만 전달
4. **배열과 문자열 처리**: 배열을 효율적으로 다룸
5. **하드웨어 제어**: 임베디드 시스템에서 메모리 직접 접근

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 실생활 비유</strong><br>
포인터는 '주소록'과 같습니다. 친구의 집에 가려면 주소를 알아야 하듯이, 변수에 접근하려면 메모리 주소를 알아야 합니다.
</div>

---

## 2. 포인터 변수의 선언

포인터 변수는 메모리 주소를 저장하기 위한 특별한 변수입니다.

### 포인터 변수 선언 방법

```c
자료형 *포인터이름;
```

**예시:**

```c
int *ptr;      // int형 데이터를 가리키는 포인터
double *dptr;  // double형 데이터를 가리키는 포인터
char *cptr;    // char형 데이터를 가리키는 포인터
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 주의</strong><br>
• 포인터 변수 선언 시 <span class="red-text">*</span> 기호를 붙입니다<br>
• 자료형은 포인터가 가리킬 데이터의 타입을 의미<br>
• 포인터 자체의 크기는 시스템에 따라 다름 (32비트: 4바이트, 64비트: 8바이트)
</div>

### 포인터 선언 스타일

C 언어에서는 여러 스타일로 포인터를 선언할 수 있습니다:

```c
int *ptr1;   // 일반적인 방법 (권장)
int* ptr2;   // 자료형 강조
int * ptr3;  // 중간 공백
```

모두 동일하지만, `int *ptr` 스타일이 가장 많이 사용됩니다.

**여러 포인터 선언 시 주의:**

```c
int *ptr1, *ptr2;  // ptr1, ptr2 모두 포인터 (정확)
int* ptr1, ptr2;   // ptr1만 포인터, ptr2는 일반 변수 (혼동 주의!)
```

### 실습 1

```c
#include <stdio.h>

int main() {
    int *iptr;
    double *dptr;
    char *cptr;

    printf("int 포인터 크기: %d바이트\n", sizeof(iptr));
    printf("double 포인터 크기: %d바이트\n", sizeof(dptr));
    printf("char 포인터 크기: %d바이트\n", sizeof(cptr));

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기 (64비트 시스템 예시)</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
int 포인터 크기: 8바이트
double 포인터 크기: 8바이트
char 포인터 크기: 8바이트
</pre>

<p style="margin-top: 10px;">
모든 포인터의 크기가 동일합니다. 포인터는 주소를 저장하므로, 가리키는 자료형과 관계없이 크기가 같습니다.
</p>

</details>

---

## 3. 주소 연산자 (&)

주소 연산자 `&`는 변수의 메모리 주소를 알아내는 연산자입니다.

### & 연산자의 사용

```c
int num = 10;
printf("num의 주소: %p\n", &num);  // %p: 주소 출력 형식
```

### 포인터 변수 초기화

포인터 변수에 주소를 저장하려면 `&` 연산자를 사용합니다.

```c
int num = 10;
int *ptr;

ptr = &num;  // num의 주소를 ptr에 저장
```

**메모리 구조:**

```
변수   주소          값
num    0x0012FF48   10
ptr    0x0012FF44   0x0012FF48  (num의 주소)
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>포인터 초기화 규칙</strong><br>
• 포인터는 반드시 같은 자료형의 변수 주소를 저장해야 합니다<br>
• <code>int *ptr = &num;</code> ← num은 int형이어야 함<br>
• 자료형이 다르면 경고 또는 오류 발생
</div>

### 실습 2

```c
#include <stdio.h>

int main() {
    int num = 100;
    double value = 3.14;
    char ch = 'A';

    printf("=== 변수의 값 ===\n");
    printf("num = %d\n", num);
    printf("value = %.2f\n", value);
    printf("ch = %c\n", ch);

    printf("\n=== 변수의 주소 ===\n");
    printf("num의 주소: %p\n", &num);
    printf("value의 주소: %p\n", &value);
    printf("ch의 주소: %p\n", &ch);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기 (예시)</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 변수의 값 ===
num = 100
value = 3.14
ch = A

=== 변수의 주소 ===
num의 주소: 0000006DFFDFF754
value의 주소: 0000006DFFDFF748
ch의 주소: 0000006DFFDFF747
</pre>

<p style="margin-top: 10px;">
주소값은 실행할 때마다 달라질 수 있습니다.
</p>

</details>

### & 연산자 사용 시 주의사항

**가능:**

```c
int num = 10;
int *ptr = &num;  // OK
```

**불가능:**

```c
int *ptr = &100;      // 에러! 상수는 주소가 없음
int *ptr = &(num+5);  // 에러! 수식은 주소가 없음
```

---

## 4. 간접 참조 연산자 (*)

간접 참조 연산자 `*`는 포인터가 가리키는 메모리의 값을 읽거나 쓸 때 사용합니다.

### * 연산자의 역할

```c
int num = 10;
int *ptr = &num;

printf("%d\n", *ptr);  // 10 출력 (num의 값)
```

`*ptr`은 "ptr이 가리키는 곳의 값"을 의미합니다.

### 포인터로 값 읽기

```c
#include <stdio.h>

int main() {
    int num = 100;
    int *ptr = &num;

    printf("num의 값: %d\n", num);
    printf("*ptr의 값: %d\n", *ptr);  // num과 동일

    printf("num의 주소: %p\n", &num);
    printf("ptr의 값: %p\n", ptr);    // &num과 동일

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
num의 값: 100
*ptr의 값: 100
num의 주소: 0000006DFFDFF754
ptr의 값: 0000006DFFDFF754
</pre>

</details>

### 포인터로 값 변경하기

포인터를 통해 원본 변수의 값을 직접 수정할 수 있습니다!

```c
#include <stdio.h>

int main() {
    int num = 10;
    int *ptr = &num;

    printf("변경 전 num: %d\n", num);

    *ptr = 20;  // 포인터를 통해 num의 값 변경

    printf("변경 후 num: %d\n", num);
    printf("변경 후 *ptr: %d\n", *ptr);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
변경 전 num: 10
변경 후 num: 20
변경 후 *ptr: 20
</pre>

</details>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 핵심 개념</strong><br>
• <code>ptr</code> = num의 주소<br>
• <code>*ptr</code> = num의 값<br>
• <code>*ptr = 20</code> ⇒ num의 값이 20으로 변경됨
</div>

### 실습 3

```c
#include <stdio.h>

int main() {
    int a = 5;
    int *ptr = &a;

    printf("초기값 a: %d\n", a);

    (*ptr)++;  // a를 1 증가
    printf("1증가 후 a: %d\n", a);

    *ptr = *ptr * 2;  // a를 2배로
    printf("2배 후 a: %d\n", a);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
초기값 a: 5
1증가 후 a: 6
2배 후 a: 12
</pre>

</details>

---

## 5. 포인터의 활용

### 두 변수 값 교환하기

포인터를 사용하면 두 변수의 값을 효율적으로 교환할 수 있습니다.

```c
#include <stdio.h>

int main() {
    int a = 10, b = 20;
    int *pa = &a;
    int *pb = &b;
    int temp;

    printf("교환 전: a=%d, b=%d\n", a, b);

    // 포인터를 이용한 값 교환
    temp = *pa;
    *pa = *pb;
    *pb = temp;

    printf("교환 후: a=%d, b=%d\n", a, b);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
교환 전: a=10, b=20
교환 후: a=20, b=10
</pre>

</details>

### 포인터 연산

포인터는 여러 연산자와 함께 사용할 수 있습니다.

```c
#include <stdio.h>

int main() {
    int num = 100;
    int *ptr = &num;

    printf("원래 값: %d\n", *ptr);

    *ptr += 50;
    printf("50 더한 후: %d\n", *ptr);

    *ptr -= 30;
    printf("30 뺀 후: %d\n", *ptr);

    *ptr *= 2;
    printf("2배 후: %d\n", *ptr);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
원래 값: 100
50 더한 후: 150
30 뺀 후: 120
2배 후: 240
</pre>

</details>

---

## 6. 종합 실습

### 문제 1 - 포인터 크기 (기초)

<div class="quiz-number">문제 1</div><strong>64비트 시스템에서 char *ptr의 크기는 몇 바이트입니까?</strong>

{% include quiz-text.html
   id="quiz1"
   answer="8"
   tags="포인터"
%}

---

### 문제 2 - 주소 연산자 (기초)

<div class="quiz-number">문제 2</div><strong>다음 코드의 실행 결과로 올바른 것은?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int num = 50;
    int *ptr = &num;

    printf("%d", *ptr);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="50"
   tags="포인터"
%}

---

### 문제 3 - 간접 참조 연산자 (중급)

<div class="quiz-number">문제 3</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int a = 10;
    int *ptr = &a;

    *ptr = 30;
    a += 5;

    printf("%d", *ptr);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="35"
   tags="포인터"
%}

---

### 문제 4 - 포인터 연산 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int num = 100;
    int *ptr = &num;

    (*ptr)++;
    (*ptr) *= 2;

    printf("%d", num);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="202"
   tags="포인터"
%}

---

### 문제 5 - 두 변수 교환 (중급)

<div class="quiz-number">문제 5</div><strong>다음 코드 실행 후 a와 b의 값은? (형식: a, b)</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int a = 7, b = 3;
    int *pa = &a, *pb = &b;
    int temp;

    temp = *pa;
    *pa = *pb;
    *pb = temp;

    printf("%d, %d", a, b);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   code_html=code_block5
   answer="3, 7"
   tags="포인터"
%}

---

### 문제 6 - 포인터와 자료형 (고급)

<div class="quiz-number">문제 6</div><strong>다음 중 올바르지 않은 포인터 사용은?</strong>

```c
int num = 10;
double value = 3.14;

// A
int *ptr1 = &num;

// B
double *ptr2 = &value;

// C
int *ptr3 = &value;

// D
double *ptr4 = &num;
```

{% include quiz-text.html
   id="quiz6"
   answer="C|D|C, D|C와 D"
   tags="포인터"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 포인터 기본</strong><br>
• 메모리 주소를 저장하는 변수<br>
• 선언: <code>자료형 *포인터이름;</code><br>
• 포인터 크기는 시스템에 따라 결정<br><br>

<strong>2. 주소 연산자 (&)</strong><br>
• 변수의 메모리 주소를 반환<br>
• <code>ptr = &num;</code><br>
• 출력 형식: <code>%p</code><br><br>

<strong>3. 간접 참조 연산자 (*)</strong><br>
• 포인터가 가리키는 값을 읽거나 쓰기<br>
• <code>*ptr</code> = ptr이 가리키는 곳의 값<br>
• <code>*ptr = 20;</code>으로 값 변경 가능<br><br>

<strong>4. 포인터와 변수</strong><br>
• <code>ptr</code> = 주소<br>
• <code>*ptr</code> = 값<br>
• <code>&변수</code> = 변수의 주소<br><br>

<strong>5. 자료형 일치</strong><br>
• 포인터 자료형 = 가리키는 변수 자료형<br>
• <code>int *ptr = &int변수;</code> (O)<br>
• <code>int *ptr = &double변수;</code> (X)

</div>

---
