---
layout: article
title: 4. 포인터의 심화
permalink: /notes/kr/c-deep-dive/chapter-04
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C DeepDive 강의 노트, 더블 포인터(이중 포인터), 다중 포인터, 함수 포인터, void 포인터를 다룹니다.
keywords: "C언어, 더블포인터, 이중포인터, 다중포인터, 함수포인터, void포인터, 포인터배열"
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

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=C%20Deep%20Dive&reversal=false&textBg=false)

---

## 1. 더블 포인터 (이중 포인터)

더블 포인터는 <span class="blue-text">포인터 변수를 가리키는 포인터</span>입니다. 포인터도 변수이므로 주소를 가지며, 이 주소를 저장할 수 있습니다.

### 더블 포인터의 개념

일반 포인터가 변수의 주소를 저장한다면, 더블 포인터는 포인터 변수의 주소를 저장합니다.

```c
int num = 10;
int *ptr = &num;       // 싱글 포인터: num의 주소 저장
int **dptr = &ptr;     // 더블 포인터: ptr의 주소 저장
```

**메모리 구조:**

```
num의 값   ptr의 값      dptr의 값
  10   ←   num의 주소  ←  ptr의 주소
 num        ptr          dptr
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>더블 포인터 선언</strong><br>
<code>int **dptr;</code><br>
• 애스터리스크(*) 2개 사용<br>
• "포인터의 포인터"를 의미
</div>

### 더블 포인터의 사용

```c
#include <stdio.h>

int main(void) {
    int num = 100;
    int *ptr = &num;      // num의 주소
    int **dptr = &ptr;    // ptr의 주소

    printf("=== 값 출력 ===\n");
    printf("num: %d\n", num);
    printf("*ptr: %d\n", *ptr);
    printf("**dptr: %d\n", **dptr);

    printf("\n=== 주소 출력 ===\n");
    printf("&num: %p\n", &num);
    printf("ptr: %p\n", ptr);
    printf("*dptr: %p\n", *dptr);

    printf("\n&ptr: %p\n", &ptr);
    printf("dptr: %p\n", dptr);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기 (예시)</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 값 출력 ===
num: 100
*ptr: 100
**dptr: 100

=== 주소 출력 ===
&num: 00B3FA14
ptr: 00B3FA14
*dptr: 00B3FA14

&ptr: 00B3FA08
dptr: 00B3FA08
</pre>

<ul style="margin-top: 10px;">
<li><code>**dptr</code>은 최종적으로 num의 값(100)에 접근</li>
<li><code>*dptr</code>은 ptr이 저장한 주소(num의 주소)</li>
<li><code>dptr</code>은 ptr의 주소</li>
</ul>

</details>

### 더블 포인터로 값 변경하기

```c
#include <stdio.h>

int main(void) {
    int num = 50;
    int *ptr = &num;
    int **dptr = &ptr;

    printf("변경 전: %d\n", num);

    **dptr = 999;  // num = 999와 동일

    printf("변경 후: %d\n", num);
    printf("*ptr: %d\n", *ptr);
    printf("**dptr: %d\n", **dptr);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
변경 전: 50
변경 후: 999
*ptr: 999
**dptr: 999
</pre>

</details>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 더블 포인터 접근 방식</strong><br>
• <code>dptr</code>: ptr의 주소<br>
• <code>*dptr</code>: ptr이 저장한 값 (num의 주소)<br>
• <code>**dptr</code>: num의 값
</div>

---

## 2. 더블 포인터와 함수

더블 포인터는 함수에서 <span class="blue-text">포인터 자체를 변경</span>할 때 유용합니다.

### 포인터 교환 함수

싱글 포인터만 사용하면 포인터가 가리키는 값만 교환할 수 있지만, 더블 포인터를 사용하면 포인터 자체를 교환할 수 있습니다.

```c
#include <stdio.h>

void swapPointer(int **dptr1, int **dptr2) {
    int *temp = *dptr1;
    *dptr1 = *dptr2;
    *dptr2 = temp;
}

int main(void) {
    int num1 = 10, num2 = 20;
    int *ptr1 = &num1;
    int *ptr2 = &num2;

    printf("=== 교환 전 ===\n");
    printf("*ptr1: %d, *ptr2: %d\n", *ptr1, *ptr2);

    swapPointer(&ptr1, &ptr2);  // 포인터 자체를 교환

    printf("\n=== 교환 후 ===\n");
    printf("*ptr1: %d, *ptr2: %d\n", *ptr1, *ptr2);
    printf("num1: %d, num2: %d\n", num1, num2);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 교환 전 ===
*ptr1: 10, *ptr2: 20

=== 교환 후 ===
*ptr1: 20, *ptr2: 10
num1: 10, num2: 20
</pre>

<p style="margin-top: 10px;">
num1과 num2의 값은 그대로지만, ptr1과 ptr2가 가리키는 대상이 바뀌었습니다.
</p>

</details>

**메모리 상태 변화:**

```
[교환 전]
ptr1 → num1(10)
ptr2 → num2(20)

[교환 후]
ptr1 → num2(20)
ptr2 → num1(10)
```

### 더블 포인터로 배열 접근

```c
#include <stdio.h>

void printArray(int **dptr, int size) {
    int i;
    for (i = 0; i < size; i++) {
        printf("%d ", *(*dptr + i));
    }
    printf("\n");
}

int main(void) {
    int arr[5] = {10, 20, 30, 40, 50};
    int *ptr = arr;
    int **dptr = &ptr;

    printf("배열 출력: ");
    printArray(dptr, 5);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
배열 출력: 10 20 30 40 50
</pre>

</details>

---

## 3. 다중 포인터 (삼중 포인터)

포인터는 이론적으로 무한대로 중첩할 수 있습니다. 실무에서는 드물지만, 개념 이해를 위해 삼중 포인터를 살펴보겠습니다.

### 삼중 포인터의 선언

```c
int num = 100;
int *ptr = &num;        // 싱글 포인터
int **dptr = &ptr;      // 더블 포인터
int ***tptr = &dptr;    // 삼중 포인터
```

**관계도:**

```
num의 값  ptr의 값     dptr의 값    tptr의 값
  100  ← num의 주소 ← ptr의 주소 ← dptr의 주소
  num      ptr         dptr         tptr
```

### 삼중 포인터 예제

```c
#include <stdio.h>

int main(void) {
    int num = 777;
    int *ptr = &num;
    int **dptr = &ptr;
    int ***tptr = &dptr;

    printf("=== 값 출력 ===\n");
    printf("num: %d\n", num);
    printf("*ptr: %d\n", *ptr);
    printf("**dptr: %d\n", **dptr);
    printf("***tptr: %d\n", ***tptr);

    // 삼중 포인터로 값 변경
    ***tptr = 999;

    printf("\n=== 변경 후 ===\n");
    printf("num: %d\n", num);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 값 출력 ===
num: 777
*ptr: 777
**dptr: 777
***tptr: 777

=== 변경 후 ===
num: 999
</pre>

</details>

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 다중 포인터 주의사항</strong><br>
• 실무에서는 삼중 포인터 이상은 거의 사용하지 않음<br>
• 코드 가독성이 크게 떨어짐<br>
• 더블 포인터까지만 이해해도 충분
</div>

---

## 4. 함수 포인터

함수도 메모리에 저장되므로 주소를 가집니다. <span class="blue-text">함수 포인터</span>는 함수의 주소를 저장하는 포인터입니다.

### 함수 포인터의 필요성

함수를 변수처럼 다루어 동적으로 호출하거나, 함수를 다른 함수에 전달할 수 있습니다.

### 함수 포인터 선언

```c
// 함수 정의
int add(int a, int b) {
    return a + b;
}

// 함수 포인터 선언
int (*funcPtr)(int, int);

// 함수 주소 저장
funcPtr = add;
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>함수 포인터 선언 형식</strong><br>
<code>반환형 (*포인터이름)(매개변수타입1, 매개변수타입2, ...);</code><br><br>
• 반환형과 매개변수 타입이 일치해야 함<br>
• 괄호 <code>(*포인터이름)</code> 필수
</div>

### 함수 포인터 사용 예제

```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int subtract(int a, int b) {
    return a - b;
}

int multiply(int a, int b) {
    return a * b;
}

int main(void) {
    int (*funcPtr)(int, int);  // 함수 포인터 선언

    // 덧셈 함수 호출
    funcPtr = add;
    printf("10 + 5 = %d\n", funcPtr(10, 5));

    // 뺄셈 함수 호출
    funcPtr = subtract;
    printf("10 - 5 = %d\n", funcPtr(10, 5));

    // 곱셈 함수 호출
    funcPtr = multiply;
    printf("10 × 5 = %d\n", funcPtr(10, 5));

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
10 + 5 = 15
10 - 5 = 5
10 × 5 = 50
</pre>

</details>

### 함수 포인터 배열

여러 함수를 배열로 관리할 수 있습니다.

```c
#include <stdio.h>

int add(int a, int b) { return a + b; }
int sub(int a, int b) { return a - b; }
int mul(int a, int b) { return a * b; }
int div(int a, int b) { return a / b; }

int main(void) {
    int (*calc[4])(int, int) = {add, sub, mul, div};
    char *op[4] = {"+", "-", "×", "÷"};
    int i;

    printf("=== 계산기 ===\n");
    for (i = 0; i < 4; i++) {
        printf("20 %s 4 = %d\n", op[i], calc[i](20, 4));
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 계산기 ===
20 + 4 = 24
20 - 4 = 16
20 × 4 = 80
20 ÷ 4 = 5
</pre>

</details>

### 함수 포인터를 매개변수로 전달

콜백 함수(Callback Function) 패턴에 활용됩니다.

```c
#include <stdio.h>

void processArray(int arr[], int size, int (*func)(int)) {
    int i;
    for (i = 0; i < size; i++) {
        arr[i] = func(arr[i]);
    }
}

int square(int n) {
    return n * n;
}

int triple(int n) {
    return n * 3;
}

int main(void) {
    int arr1[5] = {1, 2, 3, 4, 5};
    int arr2[5] = {1, 2, 3, 4, 5};
    int i;

    processArray(arr1, 5, square);
    processArray(arr2, 5, triple);

    printf("제곱: ");
    for (i = 0; i < 5; i++) printf("%d ", arr1[i]);

    printf("\n3배: ");
    for (i = 0; i < 5; i++) printf("%d ", arr2[i]);
    printf("\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
제곱: 1 4 9 16 25
3배: 3 6 9 12 15
</pre>

</details>

---

## 5. void 포인터

void 포인터는 <span class="blue-text">자료형이 정해지지 않은 포인터</span>입니다. 어떤 타입의 주소든 저장할 수 있습니다.

### void 포인터의 특징

```c
void *ptr;  // void 포인터 선언
```

- 모든 타입의 주소를 저장 가능
- <span class="red-text">포인터 연산 불가</span>
- <span class="red-text">역참조 전에 형 변환 필요</span>

### void 포인터 사용 예제

```c
#include <stdio.h>

int main(void) {
    int num = 100;
    double pi = 3.14;
    char ch = 'A';

    void *ptr;  // void 포인터 선언

    // int형 주소 저장
    ptr = &num;
    printf("int: %d\n", *(int *)ptr);

    // double형 주소 저장
    ptr = &pi;
    printf("double: %.2f\n", *(double *)ptr);

    // char형 주소 저장
    ptr = &ch;
    printf("char: %c\n", *(char *)ptr);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
int: 100
double: 3.14
char: A
</pre>

</details>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 void 포인터의 활용</strong><br>
• 범용 함수 구현 (예: qsort, memcpy)<br>
• 동적 메모리 할당 (malloc의 반환 타입)<br>
• 다양한 타입을 처리하는 구조체
</div>

---

## 6. 종합 실습

### 문제 1 - 더블 포인터 기초 (기초)

<div class="quiz-number">문제 1</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main(void) {
    int num = 50;
    int *ptr = &num;
    int **dptr = &ptr;

    **dptr += 10;

    printf("%d", num);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="60"
   tags="포인터의 심화"
%}

---

### 문제 2 - 포인터 교환 (중급)

<div class="quiz-number">문제 2</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

void swap(int **a, int **b) {
    int *temp = *a;
    *a = *b;
    *b = temp;
}

int main(void) {
    int x = 10, y = 20;
    int *p1 = &x;
    int *p2 = &y;

    swap(&p1, &p2);

    printf("%d %d", *p1, *p2);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="20 10"
   tags="포인터의 심화"
%}

---

### 문제 3 - 함수 포인터 (기초)

<div class="quiz-number">문제 3</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int calc(int a, int b) {
    return a * b + 5;
}

int main(void) {
    int (*fp)(int, int);

    fp = calc;

    printf("%d", fp(3, 4));

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="17"
   tags="포인터의 심화"
%}

---

### 문제 4 - 삼중 포인터 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main(void) {
    int num = 100;
    int *p = &num;
    int **dp = &p;
    int ***tp = &dp;

    ***tp = 500;

    printf("%d", num);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="500"
   tags="포인터의 심화"
%}

---

### 문제 5 - 함수 포인터 배열 (고급)

<div class="quiz-number">문제 5</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int add(int a, int b) { return a + b; }
int mul(int a, int b) { return a * b; }

int main(void) {
    int (*func[2])(int, int) = {add, mul};

    int result = func[0](5, 3) + func[1](4, 2);

    printf("%d", result);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint5 %}
func[0](5, 3)은 add(5, 3) = 8, func[1](4, 2)는 mul(4, 2) = 8
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=hint5
   code_html=code_block5
   answer="16"
   tags="포인터의 심화"
%}

---

### 문제 6 - void 포인터 (중급)

<div class="quiz-number">문제 6</div><strong>void 포인터에 대한 설명으로 올바른 것은?</strong>

```
A. void 포인터는 포인터 연산이 가능하다.
B. void 포인터는 역참조할 때 형 변환이 필요하다.
C. void 포인터는 int형 주소만 저장할 수 있다.
D. void 포인터는 함수 포인터로 사용할 수 없다.
```

{% include quiz-text.html
   id="quiz6"
   answer="B"
   tags="포인터의 심화"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 더블 포인터</strong><br>
• 선언: <code>int **dptr;</code><br>
• 포인터 변수의 주소를 저장<br>
• <code>**dptr</code>로 최종 값에 접근<br>
• 포인터 자체를 변경할 때 유용<br><br>

<strong>2. 다중 포인터</strong><br>
• 삼중 포인터: <code>int ***tptr;</code><br>
• 실무에서는 거의 사용 안 함<br>
• 개념 이해 목적으로 학습<br><br>

<strong>3. 함수 포인터</strong><br>
• 선언: <code>반환형 (*이름)(매개변수...);</code><br>
• 함수의 주소를 저장<br>
• 함수를 동적으로 호출 가능<br>
• 콜백 함수 구현에 활용<br><br>

<strong>4. void 포인터</strong><br>
• 선언: <code>void *ptr;</code><br>
• 모든 타입의 주소 저장 가능<br>
• 역참조 시 형 변환 필수<br>
• 포인터 연산 불가<br><br>

<strong>5. 활용 패턴</strong><br>
• 더블 포인터: Call-by-reference로 포인터 변경<br>
• 함수 포인터: 범용 함수, 콜백 구현<br>
• void 포인터: malloc, 범용 자료구조

</div>

---
