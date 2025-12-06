---
layout: article
title: 6. 반복문
permalink: /notes/kr/c-basic/chapter-06
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C 기초 과정 강의 노트, while문, do-while문, for문을 활용한 반복 제어, break와 continue를 다룹니다.
keywords: "C언어, 반복문, while문, do-while문, for문, break, continue, 루프, 무한루프"
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

## 1. 반복문이란?

반복문은 특정 코드를 <span class="blue-text">여러 번 반복 실행</span>할 때 사용하는 제어문입니다.

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>반복문 = 같은 코드를 여러 번 실행</strong><br>
반복문을 사용하면 코드의 양을 줄이고 효율적인 프로그램을 작성할 수 있습니다.
</div>

**반복문의 필요성:**

반복문이 없다면?

```c
printf("Hello\n");
printf("Hello\n");
printf("Hello\n");
printf("Hello\n");
printf("Hello\n");
// 100번 출력하려면...?
```

반복문을 사용하면?

```c
int i;
for (i = 0; i < 100; i++) {
    printf("Hello\n");
}
```

**C 언어의 반복문 종류:**

| 반복문 | 특징 | 주요 용도 |
|--------|------|-----------|
| `while` | 조건이 참인 동안 반복 | 반복 횟수가 정해지지 않은 경우 |
| `do-while` | 최소 1회 실행 후 조건 검사 | 한 번은 반드시 실행해야 하는 경우 |
| `for` | 반복 횟수가 명확한 경우 | 반복 횟수를 알고 있는 경우 |

---

## 2. while문

while문은 조건이 참인 동안 코드를 반복 실행합니다.

### 기본 형태

```c
while (조건식)
{
    // 조건이 참일 때 반복 실행할 코드
}
```

**실행 흐름:**

```
시작 → 조건 검사 → 참? → 코드 실행 → 조건 검사 반복
                 ↓ 거짓
               종료
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>while문의 동작 원리</strong><br>
1. 조건식을 먼저 검사<br>
2. 조건이 참이면 코드 실행<br>
3. 다시 조건식으로 돌아가 검사<br>
4. 조건이 거짓이면 반복 종료
</div>

### 실습 1

```c
#include <stdio.h>

int main() {
    int count = 0;

    while (count < 3) {
        printf("count = %d\n", count);
        count++;  // count 증가 (중요!)
    }

    printf("반복 종료\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
count = 0
count = 1
count = 2
반복 종료
</pre>

<ul style="margin-top: 10px;">
<li>count가 0, 1, 2일 때 조건(count < 3)이 참</li>
<li>count가 3이 되면 조건이 거짓이므로 반복 종료</li>
<li><span class="blue-text">count++가 없으면 무한루프 발생!</span></li>
</ul>

</details>

### 실습 2 - 사용자 입력 반복

```c
#include <stdio.h>

int main() {
    int num;

    printf("숫자를 입력하세요 (-1 입력 시 종료)\n");

    num = 0;  // 초기값 설정
    while (num != -1) {
        printf("입력: ");
        scanf("%d", &num);

        if (num == -1) {
            printf("프로그램을 종료합니다.\n");
        } else {
            printf("%d를 입력하셨습니다.\n", num);
        }
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
숫자를 입력하세요 (-1 입력 시 종료)
입력: 5
5를 입력하셨습니다.
입력: 10
10를 입력하셨습니다.
입력: -1
프로그램을 종료합니다.
</pre>

</details>

### 무한루프

조건이 항상 참이면 반복문이 <span class="red-text">영원히 실행</span>됩니다.

**의도하지 않은 무한루프 (주의!):**

```c
int num = 1;
while (num < 5) {
    printf("무한 반복!\n");
    // num이 변하지 않음 → 무한루프!
}
```

**의도적인 무한루프:**

```c
while (1) {  // 1은 항상 참
    printf("무한 반복 중...\n");
    // 특정 조건에서 break로 탈출
}
```

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 무한루프 탈출 방법</strong><br>
• 프로그램 강제 종료: <code>Ctrl + C</code><br>
• 코드 내에서 탈출: <code>break</code> 사용
</div>

---

## 3. do-while문

do-while문은 <span class="blue-text">최소 한 번은 실행</span>한 후 조건을 검사합니다.

### 기본 형태

```c
do {
    // 최소 1회는 실행되는 코드
} while (조건식);
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ while문과의 차이점</strong><br>
• <span class="blue-text">while문</span>: 조건 검사 → 실행<br>
• <span class="green-text">do-while문</span>: 실행 → 조건 검사<br>
• do-while문은 조건이 거짓이어도 <span class="red-text">최소 1회는 실행</span>됩니다!
</div>

**실행 흐름:**

```
시작 → 코드 실행 → 조건 검사 → 참? → 코드 실행 반복
                              ↓ 거짓
                            종료
```

### 실습 3

```c
#include <stdio.h>

int main() {
    int num;

    do {
        printf("숫자 입력 (-1 입력 시 종료): ");
        scanf("%d", &num);
    } while (num != -1);

    printf("종료되었습니다.\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
숫자 입력 (-1 입력 시 종료): 5
숫자 입력 (-1 입력 시 종료): 10
숫자 입력 (-1 입력 시 종료): -1
종료되었습니다.
</pre>

<p style="margin-top: 10px;">
do-while문은 입력을 최소 1회는 받아야 하는 경우에 적합합니다.
</p>

</details>

### 실습 4 - 1부터 10까지의 합

```c
#include <stdio.h>

int main() {
    int num = 1;
    int sum = 0;

    do {
        sum += num;  // sum = sum + num
        num++;
    } while (num <= 10);

    printf("1부터 10까지의 합: %d\n", sum);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
1부터 10까지의 합: 55
</pre>

<ul style="margin-top: 10px;">
<li>num이 1부터 10까지 증가하며 sum에 더해짐</li>
<li>1 + 2 + 3 + ... + 10 = 55</li>
</ul>

</details>

---

## 4. for문

for문은 <span class="blue-text">반복 횟수가 정해져 있을 때</span> 가장 많이 사용하는 반복문입니다.

### 기본 형태

```c
for (초기식; 조건식; 증감식)
{
    // 반복 실행할 코드
}
```

**각 요소의 역할:**

| 요소 | 역할 | 실행 시점 |
|------|------|-----------|
| **초기식** | 반복 변수 초기화 | 딱 한 번만 실행 |
| **조건식** | 반복 조건 검사 | 매 반복마다 검사 |
| **증감식** | 반복 변수 변경 | 매 반복 후 실행 |

**실행 순서:**

```
초기식 → 조건식 → 참? → 코드 실행 → 증감식 → 조건식 반복
                ↓ 거짓
              종료
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>for문의 실행 순서</strong><br>
1. <span class="blue-text">초기식</span> 실행 (딱 1번)<br>
2. <span class="blue-text">조건식</span> 검사<br>
3. 조건이 참이면 <span class="blue-text">코드 실행</span><br>
4. <span class="blue-text">증감식</span> 실행<br>
5. 2번으로 돌아가 반복
</div>

### 실습 5

```c
#include <stdio.h>

int main() {
    int i;

    for (i = 0; i < 5; i++) {
        printf("i = %d\n", i);
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
i = 0
i = 1
i = 2
i = 3
i = 4
</pre>

<ul style="margin-top: 10px;">
<li><code>i = 0</code>: 초기식, i를 0으로 초기화</li>
<li><code>i < 5</code>: 조건식, i가 5보다 작으면 반복</li>
<li><code>i++</code>: 증감식, i를 1씩 증가</li>
<li>총 5회 반복 (i = 0, 1, 2, 3, 4)</li>
</ul>

</details>

### 실습 6 - 1부터 100까지의 합

```c
#include <stdio.h>

int main() {
    int i;
    int sum = 0;

    for (i = 1; i <= 100; i++) {
        sum += i;
    }

    printf("1부터 100까지의 합: %d\n", sum);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
1부터 100까지의 합: 5050
</pre>

</details>

### for문의 다양한 형태

**증감식 변형:**

```c
// 2씩 증가
for (i = 0; i < 10; i += 2)
    printf("%d ", i);  // 0 2 4 6 8

// 1씩 감소
for (i = 5; i > 0; i--)
    printf("%d ", i);  // 5 4 3 2 1
```

**요소 생략 가능:**

```c
int i = 0;
for (; i < 3; i++) {  // 초기식 생략
    printf("%d ", i);
}
```

**무한루프:**

```c
for (;;) {  // 모든 요소 생략
    printf("무한 반복!\n");
    // Ctrl + C로 종료
}
```

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 for문 vs while문</strong><br>
• <span class="blue-text">for문</span>: 반복 횟수가 명확할 때 (카운팅)<br>
• <span class="green-text">while문</span>: 조건에 따라 반복할 때 (조건 기반)
</div>

---

## 5. 중첩 반복문

반복문 안에 또 다른 반복문을 넣을 수 있습니다.

### 기본 형태

```c
for (외부 초기식; 외부 조건식; 외부 증감식)
{
    for (내부 초기식; 내부 조건식; 내부 증감식)
    {
        // 외부 반복 1회당 내부 반복 전체가 실행됨
    }
}
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>중첩 반복문의 실행 횟수</strong><br>
외부 반복 N회 × 내부 반복 M회 = 총 N × M회 실행
</div>

### 실습 7 - 구구단 출력

```c
#include <stdio.h>

int main() {
    int dan, num;

    printf("=== 구구단 ===\n");

    for (dan = 2; dan <= 9; dan++) {
        printf("\n[%d단]\n", dan);
        for (num = 1; num <= 9; num++) {
            printf("%d × %d = %d\n", dan, num, dan * num);
        }
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 구구단 ===

[2단]
2 × 1 = 2
2 × 2 = 4
2 × 3 = 6
...
2 × 9 = 18

[3단]
3 × 1 = 3
3 × 2 = 6
...
[9단까지 계속]
</pre>

<p style="margin-top: 10px;">
외부 for문(dan)이 1회 실행될 때마다 내부 for문(num)이 9회 실행됩니다.
</p>

</details>

### 실습 8 - 별 찍기 패턴

```c
#include <stdio.h>

int main() {
    int i, j;

    printf("직각삼각형 패턴:\n");
    for (i = 1; i <= 5; i++) {
        for (j = 1; j <= i; j++) {
            printf("*");
        }
        printf("\n");
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
직각삼각형 패턴:
*
**
***
****
*****
</pre>

<ul style="margin-top: 10px;">
<li>i = 1일 때: j가 1번 반복 → * 1개</li>
<li>i = 2일 때: j가 2번 반복 → * 2개</li>
<li>i = 5일 때: j가 5번 반복 → * 5개</li>
</ul>

</details>

---

## 6. break와 continue

반복문의 흐름을 제어하는 두 가지 키워드입니다.

### break - 반복문 즉시 종료

break는 <span class="blue-text">반복문을 완전히 탈출</span>합니다.

```c
#include <stdio.h>

int main() {
    int i;

    for (i = 1; i <= 10; i++) {
        if (i == 5) {
            break;  // i가 5일 때 반복문 종료
        }
        printf("%d ", i);
    }

    printf("\n반복문 종료\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
1 2 3 4
반복문 종료
</pre>

<p style="margin-top: 10px;">
i가 5가 되면 break가 실행되어 반복문이 즉시 종료됩니다.
</p>

</details>

### continue - 다음 반복으로 건너뛰기

continue는 <span class="blue-text">현재 반복만 건너뛰고</span> 다음 반복을 계속합니다.

```c
#include <stdio.h>

int main() {
    int i;

    for (i = 1; i <= 5; i++) {
        if (i == 3) {
            continue;  // i가 3일 때 아래 코드 건너뛰기
        }
        printf("%d ", i);
    }

    printf("\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
1 2 4 5
</pre>

<p style="margin-top: 10px;">
i가 3일 때 continue가 실행되어 printf를 건너뛰고 다음 반복으로 넘어갑니다.
</p>

</details>

### 실습 9 - 짝수만 출력하기

```c
#include <stdio.h>

int main() {
    int i;

    printf("1부터 10까지 짝수만 출력:\n");

    for (i = 1; i <= 10; i++) {
        if (i % 2 != 0) {  // 홀수면
            continue;       // 건너뛰기
        }
        printf("%d ", i);
    }

    printf("\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
1부터 10까지 짝수만 출력:
2 4 6 8 10
</pre>

</details>

**break vs continue 비교:**

| 키워드 | 동작 | 사용 시점 |
|--------|------|-----------|
| `break` | 반복문 즉시 종료 | 더 이상 반복이 필요 없을 때 |
| `continue` | 현재 반복만 건너뛰기 | 특정 조건에서 일부 코드만 건너뛸 때 |

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>실행 흐름 비교</strong><br>
• <span class="blue-text">break</span>: 반복문 탈출 → 반복문 다음 코드 실행<br>
• <span class="green-text">continue</span>: 반복문의 처음(증감식)으로 이동 → 다음 반복 진행
</div>

---

## 7. 종합 실습

### 문제 1 - while문 (기초)

<div class="quiz-number">문제 1</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int i = 5;
    int sum = 0;

    while (i > 0) {
        sum += i;
        i--;
    }

    printf("%d", sum);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="15"
   tags="반복문"
%}

---

### 문제 2 - do-while문 (기초)

<div class="quiz-number">문제 2</div><strong>다음 코드는 몇 번 실행됩니까?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int num = 10;
    int count = 0;

    do {
        count++;
    } while (num < 5);

    printf("%d", count);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="1"
   tags="반복문"
%}

---

### 문제 3 - for문 (기초)

<div class="quiz-number">문제 3</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int i;

    for (i = 0; i < 4; i++) {
        printf("%d ", i * 2);
    }

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="0 2 4 6"
   tags="반복문"
%}

---

### 문제 4 - break (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int i;
    int sum = 0;

    for (i = 1; i <= 10; i++) {
        sum += i;
        if (sum > 10) {
            break;
        }
    }

    printf("%d", i);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="5"
   tags="반복문"
%}

---

### 문제 5 - continue (중급)

<div class="quiz-number">문제 5</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int i;
    int count = 0;

    for (i = 1; i <= 5; i++) {
        if (i == 2 || i == 4) {
            continue;
        }
        count++;
    }

    printf("%d", count);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   code_html=code_block5
   answer="3"
   tags="반복문"
%}

---

### 문제 6 - 중첩 반복문 (중급)

<div class="quiz-number">문제 6</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int i, j;
    int count = 0;

    for (i = 0; i < 3; i++) {
        for (j = 0; j < 2; j++) {
            count++;
        }
    }

    printf("%d", count);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   code_html=code_block6
   answer="6"
   tags="반복문"
%}

---

### 문제 7 - 팩토리얼 (고급)

<div class="quiz-number">문제 7</div><strong>5! (5 팩토리얼)의 값은?</strong>

```c
// 5! = 5 × 4 × 3 × 2 × 1

int n = 5;
int result = 1;
int i;

for (i = 1; i <= n; i++) {
    result *= i;
}

printf("%d", result);
```

{% include quiz-text.html
   id="quiz7"
   answer="120"
   tags="반복문"
%}

---

### 문제 8 - 무한루프 판별 (고급)

<div class="quiz-number">문제 8</div><strong>다음 중 무한루프가 발생하는 코드는? (여러 개 선택 가능)</strong>

```
A. while (1) { }

B. for (;;) { }

C. int i = 0;
   while (i < 5) {
       printf("%d ", i);
   }

D. do {
       printf("Hello");
   } while (1);
```

{% include quiz-text.html
   id="quiz8"
   answer="A|B|C|D|A, B, C, D|ABCD"
   tags="반복문"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. while문</strong><br>
• 조건이 참인 동안 반복<br>
• 형태: <code>while (조건) { 실행문 }</code><br>
• 조건을 먼저 검사<br><br>

<strong>2. do-while문</strong><br>
• 최소 1회는 실행 후 조건 검사<br>
• 형태: <code>do { 실행문 } while (조건);</code><br>
• 한 번은 반드시 실행해야 할 때 사용<br><br>

<strong>3. for문</strong><br>
• 반복 횟수가 정해져 있을 때 사용<br>
• 형태: <code>for (초기식; 조건식; 증감식) { 실행문 }</code><br>
• 가장 많이 사용되는 반복문<br><br>

<strong>4. 중첩 반복문</strong><br>
• 반복문 안에 반복문<br>
• 외부 N회 × 내부 M회 = 총 N×M회 실행<br>
• 2차원 패턴, 구구단 등에 활용<br><br>

<strong>5. break</strong><br>
• 반복문 즉시 종료<br>
• 더 이상 반복이 필요 없을 때 사용<br><br>

<strong>6. continue</strong><br>
• 현재 반복만 건너뛰고 다음 반복 진행<br>
• 특정 조건의 코드만 건너뛸 때 사용<br><br>

<strong>7. 무한루프</strong><br>
• <code>while (1)</code> 또는 <code>for (;;)</code><br>
• 강제 종료: <code>Ctrl + C</code><br>
• 의도적인 경우: break로 탈출

</div>

---
