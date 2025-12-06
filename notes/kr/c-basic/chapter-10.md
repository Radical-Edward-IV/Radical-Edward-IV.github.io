---
layout: article
title: 10. 다차원 배열
permalink: /notes/kr/c-basic/chapter-10
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C 기초 과정 강의 노트, 2차원 배열, 3차원 배열의 선언과 초기화, 배열 포인터를 다룹니다.
keywords: "C언어, 2차원배열, 3차원배열, 다차원배열, 배열포인터"
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

## 1. 2차원 배열

2차원 배열은 <span class="blue-text">행(row)과 열(column)</span>로 구성된 평면 구조의 배열입니다.

### 2차원 배열의 개념

1차원 배열이 선형 구조라면, 2차원 배열은 표(table) 구조입니다.

**실생활 예시:**
- 교실의 좌석 배치
- 체스판
- 엑셀 스프레드시트

```c
int arr[3][4];  // 3행 4열의 2차원 배열
```

**배열 구조 시각화:**

|      | 0열 | 1열 | 2열 | 3열 |
|------|-----|-----|-----|-----|
| **0행** | arr[0][0] | arr[0][1] | arr[0][2] | arr[0][3] |
| **1행** | arr[1][0] | arr[1][1] | arr[1][2] | arr[1][3] |
| **2행** | arr[2][0] | arr[2][1] | arr[2][2] | arr[2][3] |

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>2차원 배열의 구조</strong><br>
• 첫 번째 인덱스: 행 번호 (세로)<br>
• 두 번째 인덱스: 열 번호 (가로)<br>
• 총 요소 개수 = 행 × 열
</div>

### 2차원 배열 선언

```c
자료형 배열이름[행크기][열크기];
```

**예시:**

```c
int scores[3][4];    // 3행 4열 (총 12개 요소)
double data[2][5];   // 2행 5열 (총 10개 요소)
char table[4][3];    // 4행 3열 (총 12개 요소)
```

### 2차원 배열의 메모리 크기

```c
int arr[3][4];
```

- int형: 4바이트
- 요소 개수: 3 × 4 = 12개
- 총 크기: 4 × 12 = **48바이트**

### 실습 1

```c
#include <stdio.h>

int main() {
    int arr[2][3];

    printf("배열 크기: %d바이트\n", sizeof(arr));
    printf("행 개수: %d\n", sizeof(arr) / sizeof(arr[0]));
    printf("열 개수: %d\n", sizeof(arr[0]) / sizeof(arr[0][0]));

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
배열 크기: 24바이트
행 개수: 2
열 개수: 3
</pre>

<ul style="margin-top: 10px;">
<li>총 크기: 2행 × 3열 × 4바이트(int) = 24바이트</li>
<li>행 개수: 전체 크기 / 1행의 크기 = 24 / 12 = 2</li>
<li>열 개수: 1행의 크기 / 1개 요소 크기 = 12 / 4 = 3</li>
</ul>

</details>

---

## 2. 2차원 배열의 초기화

2차원 배열은 여러 방법으로 초기화할 수 있습니다.

### 방법 1: 중괄호로 행 구분

```c
int arr[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```

| 0열 | 1열 | 2열 |
|-----|-----|-----|
| **0행** 1 | 2 | 3 |
| **1행** 4 | 5 | 6 |

### 방법 2: 일렬로 나열 (비권장)

```c
int arr[2][3] = {1, 2, 3, 4, 5, 6};
```

순서대로 채워집니다. 하지만 가독성이 떨어지므로 방법 1을 권장합니다.

### 방법 3: 일부만 초기화

```c
int arr[2][3] = {
    {1, 2},
    {4}
};
```

| 0열 | 1열 | 2열 |
|-----|-----|-----|
| **0행** 1 | 2 | 0 |
| **1행** 4 | 0 | 0 |

나머지는 0으로 자동 초기화됩니다.

### 방법 4: 행 크기 생략

```c
int arr[][3] = {
    {1, 2, 3},
    {4, 5, 6}
};
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 중요</strong><br>
• 행 크기는 생략 가능<br>
• <span class="red-text">열 크기는 반드시 명시</span>해야 함
</div>

### 실습 2

```c
#include <stdio.h>

int main() {
    int arr[3][2] = {
        {10, 20},
        {30, 40},
        {50, 60}
    };
    int i, j;

    printf("=== 2차원 배열 출력 ===\n");
    for (i = 0; i < 3; i++) {
        for (j = 0; j < 2; j++) {
            printf("arr[%d][%d] = %d\n", i, j, arr[i][j]);
        }
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 2차원 배열 출력 ===
arr[0][0] = 10
arr[0][1] = 20
arr[1][0] = 30
arr[1][1] = 40
arr[2][0] = 50
arr[2][1] = 60
</pre>

</details>

---

## 3. 2차원 배열과 반복문

2차원 배열은 <span class="blue-text">중첩 for문</span>을 사용하여 처리합니다.

### 기본 패턴

```c
for (i = 0; i < 행크기; i++) {
    for (j = 0; j < 열크기; j++) {
        // arr[i][j] 처리
    }
}
```

- 외부 루프: 행을 반복
- 내부 루프: 열을 반복

### 실습 3 - 표 형태로 출력

```c
#include <stdio.h>

int main() {
    int scores[3][4] = {
        {90, 85, 88, 92},
        {78, 95, 82, 88},
        {85, 90, 93, 87}
    };
    int i, j;

    printf("학생 | 국어 영어 수학 과학\n");
    printf("------|-------------------\n");

    for (i = 0; i < 3; i++) {
        printf(" %d번  |", i+1);
        for (j = 0; j < 4; j++) {
            printf(" %3d", scores[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
학생 | 국어 영어 수학 과학
------|-------------------
 1번  |  90  85  88  92
 2번  |  78  95  82  88
 3번  |  85  90  93  87
</pre>

</details>

### 실습 4 - 학생별 평균 계산

```c
#include <stdio.h>

int main() {
    int scores[3][4] = {
        {90, 85, 88, 92},
        {78, 95, 82, 88},
        {85, 90, 93, 87}
    };
    int i, j;
    double sum, average;

    for (i = 0; i < 3; i++) {
        sum = 0;
        for (j = 0; j < 4; j++) {
            sum += scores[i][j];
        }
        average = sum / 4;
        printf("학생 %d 평균: %.2f\n", i+1, average);
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
학생 1 평균: 88.75
학생 2 평균: 85.75
학생 3 평균: 88.75
</pre>

</details>

---

## 4. 3차원 배열

3차원 배열은 <span class="blue-text">높이(depth), 행, 열</span>의 3차원 구조를 가집니다.

### 3차원 배열의 개념

```c
int arr[2][3][4];
```

- **높이(depth)**: 2 (2개의 2차원 배열)
- **행(row)**: 3
- **열(column)**: 4
- **총 요소**: 2 × 3 × 4 = 24개

**3차원 배열 시각화:**

```
[0층]               [1층]
┌─────────┐        ┌─────────┐
│ 3 x 4   │        │ 3 x 4   │
│ 배열    │        │ 배열    │
└─────────┘        └─────────┘
```

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 3차원 배열 이해하기</strong><br>
3차원 배열은 "2차원 배열을 여러 개 쌓아놓은 구조"로 생각하면 쉽습니다.
</div>

### 3차원 배열 선언과 초기화

```c
int arr[2][3][4] = {
    {   // 0층
        {1, 2, 3, 4},
        {5, 6, 7, 8},
        {9, 10, 11, 12}
    },
    {   // 1층
        {13, 14, 15, 16},
        {17, 18, 19, 20},
        {21, 22, 23, 24}
    }
};
```

### 3차원 배열 접근

```c
arr[0][1][2] = 7;   // 0층, 1행, 2열
arr[1][2][3] = 24;  // 1층, 2행, 3열
```

### 실습 5

```c
#include <stdio.h>

int main() {
    int arr[2][2][3] = {
        {
            {1, 2, 3},
            {4, 5, 6}
        },
        {
            {7, 8, 9},
            {10, 11, 12}
        }
    };
    int i, j, k;

    printf("=== 3차원 배열 출력 ===\n");
    for (i = 0; i < 2; i++) {
        printf("[%d층]\n", i);
        for (j = 0; j < 2; j++) {
            for (k = 0; k < 3; k++) {
                printf("%3d ", arr[i][j][k]);
            }
            printf("\n");
        }
        printf("\n");
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 3차원 배열 출력 ===
[0층]
  1   2   3
  4   5   6

[1층]
  7   8   9
 10  11  12
</pre>

</details>

### 3차원 배열의 메모리 크기

```c
#include <stdio.h>

int main() {
    int arr[2][3][4];

    printf("전체 크기: %d바이트\n", sizeof(arr));
    printf("층 개수: %d\n", sizeof(arr) / sizeof(arr[0]));
    printf("행 개수: %d\n", sizeof(arr[0]) / sizeof(arr[0][0]));
    printf("열 개수: %d\n", sizeof(arr[0][0]) / sizeof(arr[0][0][0]));

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
전체 크기: 96바이트
층 개수: 2
행 개수: 3
열 개수: 4
</pre>

<p style="margin-top: 10px;">
2 × 3 × 4 × 4바이트(int) = 96바이트
</p>

</details>

---

## 5. 배열 포인터

배열 포인터는 <span class="blue-text">배열 전체를 가리키는 포인터</span>입니다.

### 포인터 배열 vs 배열 포인터

두 개념을 혼동하지 마세요!

**포인터 배열:**

```c
int *arr[3];  // int형 포인터 3개를 가지는 배열
```

**배열 포인터:**

```c
int (*ptr)[3];  // int형 배열(크기 3)을 가리키는 포인터
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>구분 방법</strong><br>
• <code>int *arr[3]</code> → 배열이 먼저 (포인터 배열)<br>
• <code>int (*ptr)[3]</code> → 괄호로 포인터가 먼저 (배열 포인터)
</div>

### 배열 포인터의 사용

배열 포인터는 <span class="blue-text">2차원 배열을 가리킬 때</span> 주로 사용합니다.

```c
int arr[2][3] = {
    {1, 2, 3},
    {4, 5, 6}
};

int (*ptr)[3];  // 크기 3인 int 배열을 가리키는 포인터
ptr = arr;      // arr의 첫 번째 행을 가리킴
```

### 실습 6

```c
#include <stdio.h>

int main() {
    int arr[2][3] = {
        {10, 20, 30},
        {40, 50, 60}
    };

    int (*ptr)[3];  // 배열 포인터 선언
    ptr = arr;      // arr의 첫 번째 행을 가리킴
    int i, j;

    printf("=== 배열 포인터로 접근 ===\n");
    for (i = 0; i < 2; i++) {
        for (j = 0; j < 3; j++) {
            printf("%d ", ptr[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 배열 포인터로 접근 ===
10 20 30
40 50 60
</pre>

</details>

### 배열 포인터의 연산

```c
int arr[3][4];
int (*ptr)[4] = arr;

ptr;      // arr[0]을 가리킴 (0행)
ptr + 1;  // arr[1]을 가리킴 (1행)
ptr + 2;  // arr[2]를 가리킴 (2행)
```

배열 포인터를 1 증가시키면 <span class="blue-text">다음 행</span>을 가리킵니다.

---

## 6. 종합 실습

### 문제 1 - 2차원 배열 크기 (기초)

<div class="quiz-number">문제 1</div><strong>int arr[4][5]의 전체 크기는 몇 바이트입니까?</strong>

{% include quiz-text.html
   id="quiz1"
   answer="80"
   tags="다차원 배열"
%}

---

### 문제 2 - 2차원 배열 접근 (기초)

<div class="quiz-number">문제 2</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[2][3] = {
        {1, 2, 3},
        {4, 5, 6}
    };

    printf("%d", arr[1][2]);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="6"
   tags="다차원 배열"
%}

---

### 문제 3 - 2차원 배열 초기화 (기초)

<div class="quiz-number">문제 3</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[2][3] = {
        {10, 20},
        {30}
    };

    printf("%d", arr[0][2] + arr[1][1]);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="0"
   tags="다차원 배열"
%}

---

### 문제 4 - 2차원 배열 합계 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[2][2] = {
        {5, 10},
        {15, 20}
    };
    int i, j, sum = 0;

    for (i = 0; i < 2; i++) {
        for (j = 0; j < 2; j++) {
            sum += arr[i][j];
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
   answer="50"
   tags="다차원 배열"
%}

---

### 문제 5 - 3차원 배열 (중급)

<div class="quiz-number">문제 5</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[2][2][2] = {
        &#123;&#123;1, 2&#125;, &#123;3, 4&#125;&#125;,
        &#123;&#123;5, 6&#125;, &#123;7, 8&#125;&#125;
    };

    printf("%d", arr[1][0][1] + arr[0][1][1]);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   code_html=code_block5
   answer="10"
   tags="다차원 배열"
%}

---

### 문제 6 - 대각선 합 (고급)

<div class="quiz-number">문제 6</div><strong>다음 코드에서 3×3 배열의 대각선 합은?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int arr[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };
    int i, sum = 0;

    for (i = 0; i < 3; i++) {
        sum += arr[i][i];
    }

    printf("%d", sum);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   code_html=code_block6
   answer="15"
   tags="다차원 배열"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 2차원 배열</strong><br>
• 선언: <code>int arr[행][열];</code><br>
• 행과 열로 구성된 표 구조<br>
• 접근: <code>arr[i][j]</code><br>
• 초기화: 중괄호로 행 구분<br><br>

<strong>2. 2차원 배열 순회</strong><br>
• 중첩 for문 사용<br>
• 외부 루프: 행 반복<br>
• 내부 루프: 열 반복<br><br>

<strong>3. 3차원 배열</strong><br>
• 선언: <code>int arr[높이][행][열];</code><br>
• 2차원 배열을 쌓아놓은 구조<br>
• 3중 중첩 for문으로 순회<br><br>

<strong>4. 배열 포인터</strong><br>
• 선언: <code>int (*ptr)[열크기];</code><br>
• 배열 전체를 가리키는 포인터<br>
• 2차원 배열 접근에 활용<br>
• 포인터 배열과 구분 필수<br><br>

<strong>5. 메모리 크기</strong><br>
• 2차원: 행 × 열 × 자료형 크기<br>
• 3차원: 높이 × 행 × 열 × 자료형 크기<br>
• <code>sizeof()</code>로 계산 가능

</div>

---
