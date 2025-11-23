---
layout: article
title: 4. 조건문
permalink: /notes/kr/c-basic/chapter-04
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C 기초 과정 강의 노트, if문, if-else문, 중첩 if문, switch문을 활용한 조건 분기를 다룹니다.
keywords: "C언어, 조건문, if문, else문, switch문, 분기문, 제어문"
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

## 1. 조건문이란?

프로그램은 기본적으로 위에서 아래로 순차적으로 실행됩니다. 하지만 특정 조건에 따라 실행 흐름을 바꾸고 싶을 때가 있습니다. 이때 사용하는 것이 <span class="blue-text">조건문</span>입니다.

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>조건문 = 실행 흐름을 제어하는 문장</strong><br>
조건이 참(True)이면 실행하고, 거짓(False)이면 건너뜁니다.
</div>

**조건문의 종류:**
- `if`문: 조건이 참일 때만 실행
- `if-else`문: 조건에 따라 두 갈래로 분기
- `if-else if-else`문: 여러 조건을 순차적으로 검사
- `switch`문: 값에 따라 여러 갈래로 분기

---

## 2. if문

if문은 가장 기본적인 조건문으로, 조건이 참일 때만 코드를 실행합니다.

### 기본 형태

```c
if (조건)
{
    // 조건이 참일 때 실행할 코드
}
```

**조건**이 참(1)이면 중괄호 안의 코드를 실행하고, 거짓(0)이면 건너뜁니다.

### 실습 1

```c
#include <stdio.h>

int main() {
    int age = 20;

    if (age >= 18) {
        printf("성인입니다.\n");
    }

    if (age < 18) {
        printf("미성년자입니다.\n");
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
성인입니다.
</pre>

<ul style="margin-top: 10px;">
<li><span class="blue-text">06행:</span> age >= 18이 참이므로 실행됩니다.</li>
<li><span class="blue-text">10행:</span> age < 18이 거짓이므로 실행되지 않습니다.</li>
</ul>

</details>

### 중괄호 생략

실행할 문장이 하나뿐이면 중괄호를 생략할 수 있습니다.

```c
if (score >= 60)
    printf("합격\n");  // 한 줄이면 중괄호 생략 가능
```

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 권장사항</strong><br>
중괄호를 생략할 수 있지만, 가독성과 유지보수를 위해 항상 중괄호를 사용하는 것이 좋습니다.
</div>

---

## 3. if-else문

if-else문은 조건이 참일 때와 거짓일 때 각각 다른 코드를 실행합니다.

### 기본 형태

```c
if (조건)
{
    // 조건이 참일 때 실행
}
else
{
    // 조건이 거짓일 때 실행
}
```

### 실습 2

```c
#include <stdio.h>

int main() {
    int number = 7;

    if (number % 2 == 0) {
        printf("%d는 짝수입니다.\n", number);
    }
    else {
        printf("%d는 홀수입니다.\n", number);
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
7는 홀수입니다.
</pre>

<p style="margin-top: 10px;">
7을 2로 나눈 나머지는 1이므로 조건이 거짓입니다. 따라서 else 블록이 실행됩니다.
</p>

</details>

---

## 4. if-else if-else문

여러 조건을 순차적으로 검사할 때 사용합니다.

### 기본 형태

```c
if (조건1)
{
    // 조건1이 참일 때 실행
}
else if (조건2)
{
    // 조건1은 거짓, 조건2가 참일 때 실행
}
else if (조건3)
{
    // 조건1, 2는 거짓, 조건3이 참일 때 실행
}
else
{
    // 모든 조건이 거짓일 때 실행
}
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 중요</strong><br>
조건을 위에서부터 순차적으로 검사하며, <span class="red-text">첫 번째로 참인 조건만 실행</span>됩니다. 나머지 조건은 검사하지 않습니다.
</div>

### 실습 3

```c
#include <stdio.h>

int main() {
    int score = 85;

    if (score >= 90) {
        printf("학점: A\n");
    }
    else if (score >= 80) {
        printf("학점: B\n");
    }
    else if (score >= 70) {
        printf("학점: C\n");
    }
    else if (score >= 60) {
        printf("학점: D\n");
    }
    else {
        printf("학점: F\n");
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
학점: B
</pre>

<ul style="margin-top: 10px;">
<li>score >= 90 → 거짓 → 다음 조건으로</li>
<li>score >= 80 → 참 → "학점: B" 출력 후 조건문 종료</li>
<li>나머지 조건은 검사하지 않음</li>
</ul>

</details>

### else 생략 가능

모든 조건이 거짓일 때 아무것도 실행하지 않으려면 else를 생략할 수 있습니다.

```c
if (num == 1)
    printf("일\n");
else if (num == 2)
    printf("이\n");
else if (num == 3)
    printf("삼\n");
// else 생략: 1, 2, 3이 아니면 아무것도 출력 안 함
```

---

## 5. 중첩 if문

if문 안에 또 다른 if문을 포함할 수 있습니다. 이를 <span class="blue-text">중첩 if문</span>이라고 합니다.

### 기본 형태

```c
if (조건1)
{
    if (조건2)
    {
        // 조건1과 조건2가 모두 참일 때 실행
    }
}
```

### 실습 4

```c
#include <stdio.h>

int main() {
    int age = 25;
    int hasLicense = 1;  // 1: 면허 있음, 0: 면허 없음

    if (age >= 18) {
        printf("성인입니다.\n");

        if (hasLicense == 1) {
            printf("운전 가능합니다.\n");
        }
        else {
            printf("면허가 필요합니다.\n");
        }
    }
    else {
        printf("미성년자는 운전할 수 없습니다.\n");
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
성인입니다.
운전 가능합니다.
</pre>

<ul style="margin-top: 10px;">
<li>첫 번째 if: age >= 18 → 참</li>
<li>중첩된 if: hasLicense == 1 → 참</li>
<li>두 조건을 모두 만족하므로 "운전 가능합니다." 출력</li>
</ul>

</details>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 팁</strong><br>
중첩이 깊어질수록 코드가 복잡해집니다. 가능하면 논리 연산자(<code>&&</code>, <code>||</code>)로 조건을 합치는 것이 좋습니다.
</div>

**논리 연산자로 개선:**

```c
// 중첩 if문
if (age >= 18) {
    if (hasLicense == 1) {
        printf("운전 가능\n");
    }
}

// 논리 연산자 사용 (더 간결)
if (age >= 18 && hasLicense == 1) {
    printf("운전 가능\n");
}
```

---

## 6. switch문

switch문은 하나의 변수나 식의 값에 따라 여러 갈래로 분기할 때 사용합니다.

### 기본 형태

```c
switch (변수 또는 식)
{
    case 값1:
        // 변수가 값1과 같을 때 실행
        break;

    case 값2:
        // 변수가 값2와 같을 때 실행
        break;

    case 값3:
        // 변수가 값3과 같을 때 실행
        break;

    default:
        // 어떤 case에도 해당하지 않을 때 실행
        break;
}
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>switch문의 특징</strong><br>
• 정수형 값(int, char 등)만 사용 가능<br>
• 각 case는 <span class="blue-text">break</span>로 구분<br>
• default는 생략 가능 (선택사항)
</div>

### 실습 5

```c
#include <stdio.h>

int main() {
    int menu;

    printf("메뉴를 선택하세요 (1-3): ");
    scanf("%d", &menu);

    switch (menu) {
        case 1:
            printf("아메리카노를 주문하셨습니다.\n");
            break;

        case 2:
            printf("카페라떼를 주문하셨습니다.\n");
            break;

        case 3:
            printf("카푸치노를 주문하셨습니다.\n");
            break;

        default:
            printf("잘못된 선택입니다.\n");
            break;
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
메뉴를 선택하세요 (1-3): 2
카페라떼를 주문하셨습니다.
</pre>

</details>

---

## 7. break의 역할

break는 switch문을 즉시 종료합니다. break가 없으면 다음 case도 계속 실행됩니다.

### break가 있을 때

```c
int num = 2;

switch (num) {
    case 1:
        printf("일\n");
        break;  // switch 종료
    case 2:
        printf("이\n");
        break;  // switch 종료
    case 3:
        printf("삼\n");
        break;  // switch 종료
}
// 출력: 이
```

### break가 없을 때 (Fall-through)

```c
int num = 2;

switch (num) {
    case 1:
        printf("일\n");
        // break 없음
    case 2:
        printf("이\n");
        // break 없음
    case 3:
        printf("삼\n");
        // break 없음
}
// 출력: 이
//       삼
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 주의</strong><br>
break를 빼먹으면 의도하지 않은 동작이 발생합니다. <span class="red-text">각 case 끝에 break를 잊지 마세요!</span>
</div>

### break 생략을 활용하기

때로는 의도적으로 break를 생략하여 여러 case를 묶을 수 있습니다.

```c
#include <stdio.h>

int main() {
    int day;

    printf("요일을 숫자로 입력 (1-7): ");
    scanf("%d", &day);

    switch (day) {
        case 1:
        case 2:
        case 3:
        case 4:
        case 5:
            printf("평일입니다.\n");
            break;

        case 6:
        case 7:
            printf("주말입니다.\n");
            break;

        default:
            printf("잘못된 입력입니다.\n");
            break;
    }

    return 0;
}
```

---

## 8. if문 vs switch문

### 언제 if문을 사용하나요?

- 범위 조건을 검사할 때 (`score >= 90`)
- 비교 연산자가 필요할 때 (`age < 18`)
- 복잡한 조건식이 필요할 때 (`age >= 18 && hasLicense`)
- 실수형 값을 비교할 때

### 언제 switch문을 사용하나요?

- 하나의 변수가 여러 고정된 값과 비교될 때
- 정수형 또는 문자형 값만 다룰 때
- 메뉴 선택, 요일 구분 등 명확한 경우의 수가 있을 때

**비교 예시:**

```c
// if문으로 메뉴 선택
if (menu == 1)
    printf("아메리카노\n");
else if (menu == 2)
    printf("카페라떼\n");
else if (menu == 3)
    printf("카푸치노\n");

// switch문으로 메뉴 선택 (더 깔끔)
switch (menu) {
    case 1: printf("아메리카노\n"); break;
    case 2: printf("카페라떼\n"); break;
    case 3: printf("카푸치노\n"); break;
}
```

---

## 9. 종합 실습

### 문제 1 - 절댓값 구하기 (기초)

<div class="quiz-number">문제 1</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int num = -15;

    if (num < 0) {
        num = -num;
    }

    printf("%d", num);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint1 %}
num이 음수이므로 부호를 반전시킵니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   question=hint1
   code_html=code_block1
   answer="15"
   tags="조건문"
%}

---

### 문제 2 - 학점 계산 (기초)

<div class="quiz-number">문제 2</div><strong>점수가 75일 때 출력되는 학점은?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int score = 75;

    if (score >= 90)
        printf("A");
    else if (score >= 80)
        printf("B");
    else if (score >= 70)
        printf("C");
    else
        printf("D");

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint2 %}
75는 70 이상이므로 세 번째 조건에 해당합니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   question=hint2
   code_html=code_block2
   answer="C"
   tags="조건문"
%}

---

### 문제 3 - switch문 (중급)

<div class="quiz-number">문제 3</div><strong>다음 코드에서 num이 2일 때 출력 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int num = 2;

    switch (num) {
        case 1:
            printf("A");
        case 2:
            printf("B");
        case 3:
            printf("C");
            break;
        default:
            printf("D");
    }

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint3 %}
case 2에 break가 없으므로 case 3도 실행됩니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   question=hint3
   code_html=code_block3
   answer="BC"
   tags="조건문"
%}

---

### 문제 4 - 중첩 if문 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int x = 10, y = 20;

    if (x > 5) {
        if (y > 15) {
            printf("A");
        }
        else {
            printf("B");
        }
    }
    else {
        printf("C");
    }

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint4 %}
x > 5는 참, y > 15도 참입니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   question=hint4
   code_html=code_block4
   answer="A"
   tags="조건문"
%}

---

### 문제 5 - 윤년 판별 (고급)

<div class="quiz-number">문제 5</div><strong>2024년은 윤년인가요? (1: 윤년, 0: 평년)</strong>

```c
// 윤년 조건:
// 1. 4로 나누어떨어지고
// 2. 100으로 나누어떨어지지 않거나
// 3. 400으로 나누어떨어지면 윤년

int year = 2024;
int isLeap;

if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0))
    isLeap = 1;
else
    isLeap = 0;
```

{% capture hint5 %}
2024는 4로 나누어떨어지고, 100으로 나누어떨어지지 않습니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=hint5
   answer="1"
   tags="조건문"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. if문</strong><br>
• 조건이 참일 때만 실행<br>
• 형태: <code>if (조건) { 실행문 }</code><br><br>

<strong>2. if-else문</strong><br>
• 참/거짓에 따라 두 갈래 분기<br>
• 형태: <code>if (조건) { ... } else { ... }</code><br><br>

<strong>3. if-else if-else문</strong><br>
• 여러 조건을 순차 검사<br>
• 첫 번째로 참인 조건만 실행<br><br>

<strong>4. 중첩 if문</strong><br>
• if문 안에 if문 포함<br>
• 논리 연산자로 대체 가능<br><br>

<strong>5. switch문</strong><br>
• 값에 따라 여러 갈래 분기<br>
• 정수형/문자형만 사용 가능<br>
• 각 case 끝에 break 필요<br><br>

<strong>6. break</strong><br>
• switch문 즉시 종료<br>
• 빼먹으면 다음 case도 실행됨<br><br>

<strong>7. if vs switch</strong><br>
• 범위 비교 → if문<br>
• 고정된 값 비교 → switch문

</div>

---
