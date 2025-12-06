---
layout: article
title: 9. 포인터와 배열의 관계
permalink: /notes/kr/c-basic/chapter-09
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C 기초 과정 강의 노트, 배열 이름과 포인터의 관계, 포인터 연산, 포인터로 배열 접근하는 방법을 다룹니다.
keywords: "C언어, 포인터, 배열, 포인터연산, 포인터배열, 배열포인터"
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

## 1. 배열 이름의 정체

배열과 포인터는 매우 밀접한 관계를 가지고 있습니다. 사실 <span class="blue-text">배열의 이름은 포인터</span>입니다!

### 배열 이름은 첫 번째 요소의 주소

```c
int arr[3] = {10, 20, 30};
```

| arr[0] | arr[1] | arr[2] |
|--------|--------|--------|
| 10 | 20 | 30 |
| 주소: 0x100 | 주소: 0x104 | 주소: 0x108 |

배열 이름 `arr`은 배열의 첫 번째 요소 `arr[0]`의 주소를 의미합니다.

```c
arr == &arr[0]  // 참
```

### 실습 1

```c
#include <stdio.h>

int main() {
    int arr[3] = {10, 20, 30};

    printf("배열 이름 arr: %p\n", arr);
    printf("첫 번째 요소의 주소 &arr[0]: %p\n", &arr[0]);
    printf("두 번째 요소의 주소 &arr[1]: %p\n", &arr[1]);
    printf("세 번째 요소의 주소 &arr[2]: %p\n", &arr[2]);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기 (예시)</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
배열 이름 arr: 000000D5BCDFF6E8
첫 번째 요소의 주소 &arr[0]: 000000D5BCDFF6E8
두 번째 요소의 주소 &arr[1]: 000000D5BCDFF6EC
세 번째 요소의 주소 &arr[2]: 000000D5BCDFF6F0
</pre>

<ul style="margin-top: 10px;">
<li><code>arr</code>과 <code>&arr[0]</code>이 같은 주소</li>
<li>int형은 4바이트이므로 주소가 4씩 증가</li>
</ul>

</details>

### 배열 이름과 포인터의 차이

배열 이름은 포인터처럼 동작하지만 중요한 차이점이 있습니다:

```c
int arr[3] = {10, 20, 30};
int *ptr = arr;  // 가능

ptr = ptr + 1;   // 가능 (포인터는 값 변경 가능)
arr = arr + 1;   // 불가능! (배열 이름은 상수)
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 중요한 차이점</strong><br>
• <span class="blue-text">포인터 변수</span>: 값을 변경할 수 있음<br>
• <span class="red-text">배열 이름</span>: 상수 포인터, 값 변경 불가
</div>

---

## 2. 포인터 연산

포인터는 특별한 방식으로 산술 연산을 수행합니다.

### 포인터 증가 연산

포인터를 1 증가시키면, 가리키는 자료형의 크기만큼 주소가 증가합니다.

```c
int arr[3] = {10, 20, 30};
int *ptr = arr;  // ptr은 arr[0]을 가리킴
```

| 연산 | 가리키는 요소 | 주소 증가량 |
|------|--------------|------------|
| `ptr` | arr[0] | - |
| `ptr + 1` | arr[1] | +4 (int 크기) |
| `ptr + 2` | arr[2] | +8 (int 크기) |

### 자료형별 포인터 증가

```c
char *cptr;   // char는 1바이트
cptr + 1;     // 주소 +1

int *iptr;    // int는 4바이트
iptr + 1;     // 주소 +4

double *dptr; // double은 8바이트
dptr + 1;     // 주소 +8
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>포인터 연산의 핵심</strong><br>
포인터 + 1 = 주소 + (자료형 크기 × 1)<br>
포인터 + n = 주소 + (자료형 크기 × n)
</div>

### 실습 2

```c
#include <stdio.h>

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int *ptr = arr;

    printf("=== 포인터 연산 ===\n");
    printf("ptr: %p, 값: %d\n", ptr, *ptr);
    printf("ptr+1: %p, 값: %d\n", ptr+1, *(ptr+1));
    printf("ptr+2: %p, 값: %d\n", ptr+2, *(ptr+2));
    printf("ptr+3: %p, 값: %d\n", ptr+3, *(ptr+3));
    printf("ptr+4: %p, 값: %d\n", ptr+4, *(ptr+4));

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기 (예시)</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 포인터 연산 ===
ptr: 000000C8FFDFF700, 값: 10
ptr+1: 000000C8FFDFF704, 값: 20
ptr+2: 000000C8FFDFF708, 값: 30
ptr+3: 000000C8FFDFF70C, 값: 40
ptr+4: 000000C8FFDFF710, 값: 50
</pre>

<p style="margin-top: 10px;">
주소가 4바이트(int 크기)씩 증가합니다.
</p>

</details>

### 포인터 증감 연산자

```c
int arr[3] = {10, 20, 30};
int *ptr = arr;

printf("%d\n", *ptr);    // 10
ptr++;                    // 다음 요소로 이동
printf("%d\n", *ptr);    // 20
ptr++;                    // 다음 요소로 이동
printf("%d\n", *ptr);    // 30
```

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 포인터 연산 활용</strong><br>
• <code>ptr++</code>: 다음 요소로 이동<br>
• <code>ptr--</code>: 이전 요소로 이동<br>
• <code>ptr += 2</code>: 2칸 앞으로 이동
</div>

---

## 3. 포인터로 배열 접근하기

포인터를 사용하면 배열을 두 가지 방법으로 접근할 수 있습니다.

### 배열 표기법 vs 포인터 표기법

```c
int arr[3] = {10, 20, 30};
int *ptr = arr;
```

**같은 의미의 표현들:**

| 의미 | 배열 표기법 | 포인터 표기법 |
|------|------------|--------------|
| 첫 번째 요소 값 | `arr[0]` | `*arr` 또는 `*ptr` |
| 두 번째 요소 값 | `arr[1]` | `*(arr+1)` 또는 `*(ptr+1)` |
| 세 번째 요소 값 | `arr[2]` | `*(arr+2)` 또는 `*(ptr+2)` |

### 실습 3

```c
#include <stdio.h>

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    int i;

    printf("=== 배열 표기법 ===\n");
    for (i = 0; i < 5; i++) {
        printf("arr[%d] = %d\n", i, arr[i]);
    }

    printf("\n=== 포인터 표기법 ===\n");
    for (i = 0; i < 5; i++) {
        printf("*(arr+%d) = %d\n", i, *(arr+i));
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 배열 표기법 ===
arr[0] = 1
arr[1] = 2
arr[2] = 3
arr[3] = 4
arr[4] = 5

=== 포인터 표기법 ===
*(arr+0) = 1
*(arr+1) = 2
*(arr+2) = 3
*(arr+3) = 4
*(arr+4) = 5
</pre>

</details>

### 포인터로 배열 순회하기

```c
#include <stdio.h>

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int *ptr = arr;
    int i;

    // 방법 1: 인덱스 사용
    for (i = 0; i < 5; i++) {
        printf("%d ", ptr[i]);
    }
    printf("\n");

    // 방법 2: 포인터 연산
    for (i = 0; i < 5; i++) {
        printf("%d ", *(ptr + i));
    }
    printf("\n");

    // 방법 3: 포인터 증가
    ptr = arr;  // 포인터 초기화
    for (i = 0; i < 5; i++) {
        printf("%d ", *ptr);
        ptr++;
    }
    printf("\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
10 20 30 40 50
10 20 30 40 50
10 20 30 40 50
</pre>

</details>

---

## 4. 포인터 배열

포인터 배열은 <span class="blue-text">포인터를 요소로 가지는 배열</span>입니다.

### 포인터 배열 선언

```c
int *parr[3];  // int형 포인터 3개를 저장하는 배열
```

**구조:**

```
parr[0] → int형 변수의 주소
parr[1] → int형 변수의 주소
parr[2] → int형 변수의 주소
```

### 포인터 배열 사용 예

```c
#include <stdio.h>

int main() {
    int a = 10, b = 20, c = 30;

    // 포인터 배열 선언 및 초기화
    int *parr[3] = {&a, &b, &c};

    // 포인터 배열을 통한 접근
    printf("첫 번째 값: %d\n", *parr[0]);  // 10
    printf("두 번째 값: %d\n", *parr[1]);  // 20
    printf("세 번째 값: %d\n", *parr[2]);  // 30

    // 값 변경
    *parr[0] = 100;
    printf("변경된 a: %d\n", a);  // 100

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
첫 번째 값: 10
두 번째 값: 20
세 번째 값: 30
변경된 a: 100
</pre>

</details>

### 문자열 배열

포인터 배열은 여러 문자열을 저장할 때 유용합니다.

```c
#include <stdio.h>

int main() {
    char *fruits[3] = {"Apple", "Banana", "Cherry"};
    int i;

    printf("=== 과일 목록 ===\n");
    for (i = 0; i < 3; i++) {
        printf("%d. %s\n", i+1, fruits[i]);
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 과일 목록 ===
1. Apple
2. Banana
3. Cherry
</pre>

</details>

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>포인터 배열의 활용</strong><br>
• 여러 변수의 주소를 한 번에 관리<br>
• 문자열 배열 구현<br>
• 가변 길이 데이터 처리
</div>

---

## 5. 종합 실습

### 문제 1 - 배열과 포인터 (기초)

<div class="quiz-number">문제 1</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[3] = {5, 10, 15};

    printf("%d", *arr);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="5"
   tags="포인터와 배열"
%}

---

### 문제 2 - 포인터 연산 (기초)

<div class="quiz-number">문제 2</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[4] = {2, 4, 6, 8};

    printf("%d", *(arr + 2));

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="6"
   tags="포인터와 배열"
%}

---

### 문제 3 - 포인터 표기법 (중급)

<div class="quiz-number">문제 3</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int *ptr = arr + 2;

    printf("%d", *ptr + *(ptr + 1));

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="70"
   tags="포인터와 배열"
%}

---

### 문제 4 - 포인터 증가 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[4] = {1, 3, 5, 7};
    int *ptr = arr;

    ptr++;
    ptr++;

    printf("%d", *ptr);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="5"
   tags="포인터와 배열"
%}

---

### 문제 5 - 포인터 배열 (중급)

<div class="quiz-number">문제 5</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int a = 100, b = 200, c = 300;
    int *parr[3] = {&a, &b, &c};

    *parr[1] = 500;

    printf("%d", b);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   code_html=code_block5
   answer="500"
   tags="포인터와 배열"
%}

---

### 문제 6 - 배열 합계 (고급)

<div class="quiz-number">문제 6</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[5] = {2, 4, 6, 8, 10};
    int *ptr = arr;
    int sum = 0;
    int i;

    for (i = 0; i < 5; i++) {
        sum += *(ptr + i);
    }

    printf("%d", sum);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   code_html=code_block6
   answer="30"
   tags="포인터와 배열"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 배열 이름과 포인터</strong><br>
• 배열 이름 = 첫 번째 요소의 주소<br>
• <code>arr == &arr[0]</code><br>
• 배열 이름은 상수 포인터 (값 변경 불가)<br><br>

<strong>2. 포인터 연산</strong><br>
• <code>ptr + 1</code> = 다음 요소의 주소<br>
• 주소 증가량 = 자료형 크기<br>
• <code>ptr++</code>, <code>ptr--</code> 사용 가능<br><br>

<strong>3. 배열 접근</strong><br>
• 배열 표기법: <code>arr[i]</code><br>
• 포인터 표기법: <code>*(arr + i)</code><br>
• 두 방법은 완전히 동일<br><br>

<strong>4. 포인터 배열</strong><br>
• 선언: <code>int *parr[크기];</code><br>
• 포인터를 요소로 가지는 배열<br>
• 문자열 배열 구현에 활용<br><br>

<strong>5. 핵심 공식</strong><br>
• <code>arr[i]</code> = <code>*(arr + i)</code><br>
• <code>&arr[i]</code> = <code>arr + i</code><br>
• <code>ptr[i]</code> = <code>*(ptr + i)</code>

</div>

---
