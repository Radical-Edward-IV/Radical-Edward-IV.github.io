---
layout: article
title: 6. 구조체 기본
permalink: /notes/kr/c-deep-dive/chapter-06
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C DeepDive 강의 노트, 구조체의 정의와 선언, 구조체 배열, typedef 선언을 다룹니다.
keywords: "C언어, 구조체, struct, 구조체배열, typedef, 사용자정의자료형"
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

## 1. 구조체의 이해

구조체(Structure)는 <span class="blue-text">다양한 데이터형을 갖는 변수들의 집합</span>입니다. 하나 이상의 변수를 묶어서 새로운 사용자 정의 자료형을 만들 수 있습니다.

### 구조체란?

구조체는 사용자가 임의로 정의하는 새로운 유형의 자료형이라는 의미로 <span class="blue-text">사용자 정의 자료형</span>이라고도 불립니다.

```c
struct person
{
    char name[30];
    int age;
};
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>구조체의 특징</strong><br>
• <code>struct</code> 키워드로 정의<br>
• 여러 자료형을 하나로 묶을 수 있음<br>
• 각 멤버 변수는 독립적인 메모리 공간 할당<br>
• 사용자 정의 자료형으로 활용
</div>

### 구조체 변수의 선언

구조체 정의가 완료되면 구조체 변수를 선언할 수 있습니다.

```c
struct person boy;
struct person girl;
```

**메모리 할당:**

```
boy 구조체 변수
┌────────────────┬────┐
│ name[30]       │age │
└────────────────┴────┘

girl 구조체 변수
┌────────────────┬────┐
│ name[30]       │age │
└────────────────┴────┘
```

### 구조체 멤버 변수 접근

멤버 변수에 접근할 때는 <span class="yellow-code">. 연산자</span>(도트 연산자)를 사용합니다.

```c
#include <stdio.h>
#include <string.h>

struct person
{
    char name[30];
    int age;
};

int main(void)
{
    struct person boy, girl;

    // name 멤버 변수에 대한 접근
    strcpy(boy.name, "김선호");
    strcpy(girl.name, "이소녀");

    // age 멤버 변수에 대한 접근
    boy.age = 12;
    girl.age = 9;

    printf("소년의 이름은 %s, 나이는 %d세\n", boy.name, boy.age);
    printf("소녀의 이름은 %s, 나이는 %d세\n", girl.name, girl.age);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
소년의 이름은 김선호, 나이는 12세
소녀의 이름은 이소녀, 나이는 9세
</pre>

</details>

### 구조체 변수의 초기화

구조체 변수는 선언과 동시에 초기화할 수 있으며, 배열과 유사한 문법을 사용합니다.

```c
struct person boy = {"김선호", 12};
```

```c
#include <stdio.h>

struct person
{
    char name[30];
    int age;
};

int main(void)
{
    // 구조체 변수 선언과 동시에 초기화
    struct person boy = {"김선호", 12};
    struct person girl = {"이소녀", 9};

    printf("소년의 이름은 %s, 나이는 %d세\n", boy.name, boy.age);
    printf("소녀의 이름은 %s, 나이는 %d세\n", girl.name, girl.age);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
소년의 이름은 김선호, 나이는 12세
소녀의 이름은 이소녀, 나이는 9세
</pre>

</details>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 구조체를 사용하는 이유</strong><br>
• 관련된 데이터를 논리적으로 묶어 관리<br>
• 코드의 가독성과 유지보수성 향상<br>
• 복잡한 데이터 구조를 효율적으로 표현
</div>

---

## 2. 구조체와 배열

구조체는 사용자 정의 자료형이므로 <span class="blue-text">구조체 배열</span>을 선언할 수 있습니다.

### 구조체 배열의 선언

```c
int iarr[3];              // 일반 배열
struct person parr[3];    // 구조체 배열
```

**메모리 구조:**

```
int형 배열 iarr
┌─────┬─────┬─────┐
│ int │ int │ int │
└─────┴─────┴─────┘

person 구조체 배열 parr
┌──────────────┬──────────────┬──────────────┐
│   name  age  │   name  age  │   name  age  │
│ [30]    int  │ [30]    int  │ [30]    int  │
└──────────────┴──────────────┴──────────────┘
```

### 구조체 배열의 초기화

```c
#include <stdio.h>
#include <string.h>

struct person
{
    char name[30];
    int age;
};

int main(void)
{
    // 구조체 배열의 선언 및 초기화
    struct person boy[3] = {
        {"김소년", 12},
        {"유소년", 14},
        {"청소년", 16}
    };

    struct person girl[3];
    int i;

    // 개별 변수에 대한 초기화
    strcpy(girl[0].name, "이소녀");
    strcpy(girl[1].name, "오소녀");
    strcpy(girl[2].name, "하소녀");
    girl[0].age = 9;
    girl[1].age = 13;
    girl[2].age = 7;

    for(i = 0; i < 3; i++)
    {
        printf("소년의 이름은 %s, 나이는 %d세\n", boy[i].name, boy[i].age);
        printf("소녀의 이름은 %s, 나이는 %d세\n", girl[i].name, girl[i].age);
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
소년의 이름은 김소년, 나이는 12세
소녀의 이름은 이소녀, 나이는 9세
소년의 이름은 유소년, 나이는 14세
소녀의 이름은 오소녀, 나이는 13세
소년의 이름은 청소년, 나이는 16세
소녀의 이름은 하소녀, 나이는 7세
</pre>

</details>

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>구조체 배열 초기화 방법</strong><br>
• 선언 시 초기화 리스트 사용: <code>{% raw %}{{"값1", 값2}, {"값3", 값4}, ...}{% endraw %}</code><br>
• 각 배열 요소에 개별 접근하여 초기화<br>
• 배열의 인덱스와 . 연산자 함께 사용: <code>arr[i].member</code>
</div>

---

## 3. typedef 선언

<span class="yellow-code">typedef</span>는 <span class="blue-text">기존 자료형에 새 이름을 부여</span>하는 선언입니다. 복잡한 자료형을 간결하게 사용할 수 있습니다.

### typedef 기본 사용법

```c
typedef int INTEGER;
```

위와 같이 선언하면 `INTEGER`는 `int`와 동일한 역할을 수행합니다.

```c
#include <stdio.h>

// int형 정수, int형 정수 포인터, 부호 없는 int형 정수에 각각 별칭 부여
typedef int INT;
typedef int * PINT;
typedef unsigned int UINT;

int main(void)
{
    // 지역 내에서 사용할 자료형 이름에 대한 선언
    typedef char CHAR;
    typedef char * STR;

    // typedef 선언 이후 자료형은 기존 자료형과 동일한 역할을 수행
    INT num = 3;
    PINT ptr = &num;
    UINT unum = 5;

    CHAR ch = 'c';
    STR str = "Hello!";

    printf("%d %d %d\n", num, *ptr, unum);
    printf("%c %s\n", ch, str);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
3 3 5
c Hello!
</pre>

</details>

| 기존 자료형 | 별칭 |
|------------|------|
| int | INT |
| int * | PINT |
| unsigned int | UINT |
| char | CHAR |
| char * | STR |

### 구조체와 typedef

구조체를 typedef로 선언하면 `struct` 키워드를 생략할 수 있어 편리합니다.

```c
struct point
{
    int x;
    int y;
};

typedef struct point POINT;
```

이제 구조체 변수 선언 시 다음과 같이 사용할 수 있습니다.

```c
POINT position = {30, 60};
```

### 구조체 정의와 동시에 typedef 선언

더 간결하게 구조체를 정의하면서 동시에 typedef 선언을 할 수 있습니다.

```c
typedef struct
{
    int x;
    int y;
} POINT;
```

```c
#include <stdio.h>

// 구조체 선언과 동시에 typedef 선언
typedef struct
{
    int x;
    int y;
} POINT;

struct person
{
    char name[30];
    int age;
};

// 정의된 구조체에 대한 typedef 선언
typedef struct person PERSON;

int main(void)
{
    POINT position = {30, 60};
    PERSON saram = {"김사람", 10};

    printf("%d %d\n", position.x, position.y);
    printf("%s %d\n", saram.name, saram.age);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
30 60
김사람 10
</pre>

</details>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 typedef 사용의 장점</strong><br>
• 코드 간결성 향상 (<code>struct</code> 키워드 생략)<br>
• 자료형 이름의 직관성 증가<br>
• 코드 유지보수 용이<br>
• 플랫폼 독립적 코드 작성에 유리
</div>

---

## 4. 종합 실습

### 문제 1 - 구조체 기본 (기초)

<div class="quiz-number">문제 1</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

struct student {
    int id;
    int score;
};

int main(void) {
    struct student s = {20230101, 95};

    printf("%d", s.score);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="95"
   tags="구조체 기본"
%}

---

### 문제 2 - 구조체 배열 (기초)

<div class="quiz-number">문제 2</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

struct point {
    int x;
    int y;
};

int main(void) {
    struct point arr[3] = {{1, 2}, {3, 4}, {5, 6}};

    printf("%d", arr[1].x + arr[2].y);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="9"
   tags="구조체 기본"
%}

---

### 문제 3 - typedef 선언 (기초)

<div class="quiz-number">문제 3</div><strong>다음 중 올바른 typedef 선언은?</strong>

```
A. typedef int INTEGER;
B. typedef struct point POINT;
C. typedef char * STRING;
D. 위의 모든 선언이 올바르다.
```

{% include quiz-text.html
   id="quiz3"
   answer="D"
   tags="구조체 기본"
%}

---

### 문제 4 - 구조체 초기화 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

typedef struct {
    int num;
    int score;
} Student;

int main(void) {
    Student s1 = {1, 80};
    Student s2 = {2, 90};

    int total = s1.score + s2.score;

    printf("%d", total);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="170"
   tags="구조체 기본"
%}

---

### 문제 5 - 구조체 배열과 반복문 (중급)

<div class="quiz-number">문제 5</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

typedef struct {
    int value;
} Data;

int main(void) {
    Data arr[4] = {{10}, {20}, {30}, {40}};
    int sum = 0;
    int i;

    for(i = 0; i < 4; i++) {
        sum += arr[i].value;
    }

    printf("%d", sum);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% include quiz-text.html
   id="quiz5"
   code_html=code_block5
   answer="100"
   tags="구조체 기본"
%}

---

### 문제 6 - 구조체 멤버 접근 (고급)

<div class="quiz-number">문제 6</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

typedef struct {
    int a;
    int b;
} Pair;

int main(void) {
    Pair p1 = {5, 10};
    Pair p2 = {3, 7};

    int result = (p1.a + p2.a) * (p1.b - p2.b);

    printf("%d", result);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% capture hint6 %}
(5 + 3) * (10 - 7) = 8 * 3 = 24
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   question=hint6
   code_html=code_block6
   answer="24"
   tags="구조체 기본"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 구조체의 정의</strong><br>
• 선언: <code>struct 구조체이름 { 멤버변수들; };</code><br>
• 여러 자료형을 하나로 묶는 사용자 정의 자료형<br>
• 멤버 변수는 개수 제한 없음<br>
• 각 멤버는 독립적인 메모리 공간 할당<br><br>

<strong>2. 구조체 변수 선언 및 접근</strong><br>
• 선언: <code>struct 구조체이름 변수이름;</code><br>
• 멤버 접근: <code>변수이름.멤버이름</code> (도트 연산자 사용)<br>
• 초기화: <code>{% raw %}struct 구조체이름 변수 = {값1, 값2, ...};{% endraw %}</code><br><br>

<strong>3. 구조체 배열</strong><br>
• 선언: <code>struct 구조체이름 배열이름[크기];</code><br>
• 초기화: <code>{% raw %}{{값1, 값2}, {값3, 값4}, ...}{% endraw %}</code><br>
• 접근: <code>배열이름[인덱스].멤버이름</code><br><br>

<strong>4. typedef 선언</strong><br>
• 기본 형식: <code>typedef 기존자료형 새이름;</code><br>
• 구조체: <code>typedef struct 구조체이름 새이름;</code><br>
• 정의와 동시 선언: <code>typedef struct { ... } 새이름;</code><br>
• struct 키워드 생략 가능<br><br>

<strong>5. 사용 시 주의사항</strong><br>
• 구조체 멤버 접근 시 . 연산자 필수<br>
• 배열 초기화는 선언 시에만 리스트 사용 가능<br>
• typedef 사용 시 코드 간결성 향상<br>
• 구조체는 논리적으로 관련된 데이터를 묶을 때 사용

</div>

---
