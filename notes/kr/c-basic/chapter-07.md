---
layout: article
title: 7. 1차원 배열
permalink: /notes/kr/c-basic/chapter-07
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C 기초 과정 강의 노트, 1차원 배열의 선언, 초기화, 접근 방법, 문자 배열과 문자열 처리를 다룹니다.
keywords: "C언어, 배열, 1차원배열, 문자배열, 문자열, 배열초기화"
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

## 1. 배열이란?

배열은 <span class="blue-text">같은 자료형의 데이터를 여러 개 저장</span>할 수 있는 데이터 구조입니다.

### 배열이 필요한 이유

학생 5명의 점수를 저장하려면 어떻게 해야 할까요?

**배열을 사용하지 않는 경우:**

```c
int score1 = 85;
int score2 = 90;
int score3 = 78;
int score4 = 92;
int score5 = 88;
```

변수가 너무 많아서 관리하기 어렵습니다!

**배열을 사용하는 경우:**

```c
int scores[5] = {85, 90, 78, 92, 88};
```

하나의 변수로 여러 개의 값을 관리할 수 있습니다!

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>배열 = 같은 자료형 데이터의 집합</strong><br>
배열을 사용하면 많은 데이터를 효율적으로 관리할 수 있습니다.
</div>

---

## 2. 배열의 선언과 초기화

### 배열 선언 방법

배열을 선언하려면 세 가지 요소가 필요합니다:

1. **자료형**: 배열에 저장할 데이터의 타입
2. **배열 이름**: 배열을 식별하는 이름
3. **배열 크기**: 저장할 수 있는 데이터의 개수

```c
자료형 배열이름[배열크기];
```

**예시:**

```c
int numbers[5];     // 정수 5개를 저장할 수 있는 배열
double values[10];  // 실수 10개를 저장할 수 있는 배열
char letters[26];   // 문자 26개를 저장할 수 있는 배열
```

### 배열의 메모리 구조

```c
int arr[3];
```

위 배열을 선언하면 메모리에는 다음과 같이 공간이 할당됩니다:

| arr[0] | arr[1] | arr[2] |
|--------|--------|--------|
| 4바이트 | 4바이트 | 4바이트 |

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 메모리 할당</strong><br>
int형은 4바이트이므로 <code>int arr[3]</code>은 총 12바이트(4×3)의 메모리를 차지합니다.
</div>

### 배열 초기화 방법

**방법 1: 선언과 동시에 초기화**

```c
int arr[5] = {10, 20, 30, 40, 50};
```

**방법 2: 크기 생략 (컴파일러가 자동으로 크기 결정)**

```c
int arr[] = {10, 20, 30, 40, 50};  // 크기는 자동으로 5
```

**방법 3: 일부만 초기화 (나머지는 0으로 자동 초기화)**

```c
int arr[5] = {10, 20};  // arr[0]=10, arr[1]=20, arr[2]=0, arr[3]=0, arr[4]=0
```

**방법 4: 모두 0으로 초기화**

```c
int arr[5] = {0};  // 모든 요소가 0
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 주의</strong><br>
배열을 선언만 하고 초기화하지 않으면 <span class="red-text">쓰레기 값</span>이 들어있습니다!
</div>

### 실습 1

다음 코드의 실행 결과를 확인해보세요:

```c
#include <stdio.h>

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};
    int values[] = {1, 2, 3};
    int zeros[5] = {0};

    printf("numbers 배열의 크기: %d바이트\n", sizeof(numbers));
    printf("values 배열의 크기: %d바이트\n", sizeof(values));
    printf("zeros[0] = %d\n", zeros[0]);
    printf("zeros[4] = %d\n", zeros[4]);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
numbers 배열의 크기: 20바이트
values 배열의 크기: 12바이트
zeros[0] = 0
zeros[4] = 0
</pre>

<ul style="margin-top: 10px;">
<li><code>numbers</code>: int 5개 × 4바이트 = 20바이트</li>
<li><code>values</code>: int 3개 × 4바이트 = 12바이트</li>
<li><code>zeros</code>: {0}으로 초기화하면 모든 요소가 0</li>
</ul>

</details>

---

## 3. 배열 요소 접근하기

### 인덱스(Index)

배열의 각 요소는 <span class="blue-text">인덱스(색인)</span>를 통해 접근합니다.

**중요:** 인덱스는 <span class="red-text">0부터 시작</span>합니다!

```c
int arr[5] = {10, 20, 30, 40, 50};
```

| 인덱스 | 0 | 1 | 2 | 3 | 4 |
|--------|---|---|---|---|---|
| 값 | 10 | 20 | 30 | 40 | 50 |

### 배열 요소 읽기와 쓰기

**읽기:**

```c
printf("%d\n", arr[0]);  // 10 출력
printf("%d\n", arr[2]);  // 30 출력
```

**쓰기:**

```c
arr[1] = 100;   // 두 번째 요소를 100으로 변경
arr[4] = 200;   // 다섯 번째 요소를 200으로 변경
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 배열 범위 초과 주의</strong><br>
크기가 5인 배열의 유효한 인덱스는 0~4입니다.<br>
<code>arr[5]</code>, <code>arr[10]</code> 같은 접근은 <span class="red-text">오류</span>를 발생시킵니다!
</div>

### 실습 2

```c
#include <stdio.h>

int main() {
    int scores[3];

    // 배열 요소에 값 저장
    scores[0] = 85;
    scores[1] = 90;
    scores[2] = 78;

    // 배열 요소 출력
    printf("첫 번째 점수: %d\n", scores[0]);
    printf("두 번째 점수: %d\n", scores[1]);
    printf("세 번째 점수: %d\n", scores[2]);

    // 평균 계산
    double average = (scores[0] + scores[1] + scores[2]) / 3.0;
    printf("평균: %.2f\n", average);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
첫 번째 점수: 85
두 번째 점수: 90
세 번째 점수: 78
평균: 84.33
</pre>

</details>

---

## 4. 배열과 반복문

배열은 <span class="blue-text">for 반복문</span>과 함께 사용하면 매우 효율적입니다.

### for문으로 배열 순회하기

```c
#include <stdio.h>

int main() {
    int numbers[5] = {10, 20, 30, 40, 50};
    int i;

    // 배열의 모든 요소 출력
    for (i = 0; i < 5; i++) {
        printf("numbers[%d] = %d\n", i, numbers[i]);
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
numbers[0] = 10
numbers[1] = 20
numbers[2] = 30
numbers[3] = 40
numbers[4] = 50
</pre>

</details>

### 실습 3 - 배열의 합과 평균 구하기

```c
#include <stdio.h>

int main() {
    int scores[5] = {85, 90, 78, 92, 88};
    int sum = 0;
    int i;

    // 합계 계산
    for (i = 0; i < 5; i++) {
        sum += scores[i];
    }

    // 평균 계산
    double average = sum / 5.0;

    printf("총점: %d\n", sum);
    printf("평균: %.2f\n", average);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
총점: 433
평균: 86.60
</pre>

</details>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 배열 크기 자동 계산</strong><br>
배열의 크기를 코드에 직접 쓰지 않고 계산할 수 있습니다:<br>
<code>int size = sizeof(scores) / sizeof(scores[0]);</code>
</div>

---

## 5. 문자 배열과 문자열

### 문자 배열

문자를 저장하는 배열은 <span class="blue-text">char형 배열</span>을 사용합니다.

```c
char letters[5] = {'H', 'e', 'l', 'l', 'o'};
```

### 문자열

C 언어에서 문자열은 <span class="blue-text">널 문자(\0)로 끝나는 문자 배열</span>입니다.

```c
char greeting[6] = "Hello";  // 자동으로 '\0' 추가
```

| H | e | l | l | o | \0 |
|---|---|---|---|---|----|
| [0] | [1] | [2] | [3] | [4] | [5] |

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>널 문자(\0)란?</strong><br>
• 문자열의 끝을 나타내는 특수 문자<br>
• 문자열을 저장할 때 자동으로 추가됨<br>
• 실제 문자열보다 <span class="blue-text">1바이트 더 큰 배열</span>이 필요
</div>

### 문자열 선언과 초기화

**방법 1: 큰따옴표 사용 (권장)**

```c
char str1[6] = "Hello";  // 널 문자 포함 6바이트
```

**방법 2: 문자 배열로 초기화**

```c
char str2[6] = {'H', 'e', 'l', 'l', 'o', '\0'};  // 수동으로 널 문자 추가
```

**방법 3: 크기 생략**

```c
char str3[] = "Hello";  // 컴파일러가 자동으로 크기 6으로 설정
```

### 문자열 입출력

**출력:**

```c
char name[] = "Kim";
printf("%s\n", name);  // %s: 문자열 출력
```

**입력:**

```c
char name[50];
scanf("%s", name);  // & 연산자 없이 사용!
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ scanf의 문자열 입력 제한</strong><br>
• <code>scanf("%s", ...)</code>는 <span class="red-text">공백에서 입력이 끝남</span><br>
• "Hello World" 입력 시 "Hello"만 저장됨<br>
• 공백 포함 입력은 <code>fgets()</code> 함수 사용
</div>

### 실습 4

```c
#include <stdio.h>

int main() {
    char str1[20] = "Good";
    char str2[20];

    printf("문자열 입력: ");
    scanf("%s", str2);

    printf("str1: %s\n", str1);
    printf("str2: %s\n", str2);

    // 문자열 길이 확인 (널 문자 포함)
    printf("str1 크기: %d바이트\n", sizeof(str1));

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
문자열 입력: Morning
str1: Good
str2: Morning
str1 크기: 20바이트
</pre>

</details>

---

## 6. 종합 실습

### 문제 1 - 배열 크기 (기초)

<div class="quiz-number">문제 1</div><strong>int형 배열 arr[10]의 전체 크기는 몇 바이트입니까?</strong>

{% include quiz-text.html
   id="quiz1"
   answer="40"
   tags="1차원 배열"
%}

---

### 문제 2 - 배열 인덱스 (기초)

<div class="quiz-number">문제 2</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[5] = {2, 4, 6, 8, 10};

    printf("%d", arr[2] + arr[4]);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="16"
   tags="1차원 배열"
%}

---

### 문제 3 - 배열 초기화 (기초)

<div class="quiz-number">문제 3</div><strong>다음 코드에서 arr[3]의 값은?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[5] = {10, 20};

    printf("%d", arr[3]);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="0"
   tags="1차원 배열"
%}

---

### 문제 4 - 배열과 반복문 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    int i, sum = 0;

    for (i = 0; i < 5; i++) {
        if (arr[i] % 2 == 0) {
            sum += arr[i];
        }
    }

    printf("%d", sum);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="6"
   tags="1차원 배열"
%}

---

### 문제 5 - 문자열 길이 (중급)

<div class="quiz-number">문제 5</div><strong>문자열 "C Language"를 저장하려면 최소 몇 바이트의 char 배열이 필요합니까?</strong>

{% include quiz-text.html
   id="quiz5"
   answer="11"
   tags="1차원 배열"
%}

---

### 문제 6 - 최댓값 찾기 (중급)

<div class="quiz-number">문제 6</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[5] = {23, 67, 45, 89, 12};
    int max = arr[0];
    int i;

    for (i = 1; i < 5; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }

    printf("%d", max);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   code_html=code_block6
   answer="89"
   tags="1차원 배열"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 배열 기본</strong><br>
• 같은 자료형의 데이터를 여러 개 저장하는 구조<br>
• 선언: <code>자료형 배열이름[크기];</code><br>
• 인덱스는 0부터 시작<br><br>

<strong>2. 배열 초기화</strong><br>
• <code>int arr[5] = {10, 20, 30, 40, 50};</code><br>
• 크기 생략 가능: <code>int arr[] = {10, 20, 30};</code><br>
• 일부만 초기화하면 나머지는 0<br><br>

<strong>3. 배열 접근</strong><br>
• 읽기: <code>value = arr[0];</code><br>
• 쓰기: <code>arr[0] = 100;</code><br>
• 유효 인덱스: 0 ~ (크기-1)<br><br>

<strong>4. 배열과 반복문</strong><br>
• for문으로 효율적인 접근<br>
• <code>for (i = 0; i < 크기; i++)</code><br><br>

<strong>5. 문자열</strong><br>
• char 배열로 표현<br>
• 널 문자(\0)로 끝남<br>
• <code>char str[] = "Hello";</code><br>
• printf: <code>%s</code>, scanf: <code>%s</code> (& 없이)

</div>

---
