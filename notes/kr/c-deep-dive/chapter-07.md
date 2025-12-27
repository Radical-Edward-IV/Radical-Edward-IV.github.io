---
layout: article
title: 7. 구조체 심화
permalink: /notes/kr/c-deep-dive/chapter-07
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C DeepDive 강의 노트, 구조체 포인터, 구조체 중첩, 구조체와 함수의 관계를 다룹니다.
keywords: "C언어, 구조체포인터, 화살표연산자, 구조체중첩, 구조체함수, Call-by-reference"
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

## 1. 구조체와 포인터

구조체 포인터는 <span class="blue-text">구조체 변수의 주소를 저장하는 포인터</span>입니다. 일반 포인터와 사용법이 유사하지만, 멤버 접근 방법이 다릅니다.

### 구조체 포인터 변수의 선언

일반 자료형 포인터와 동일한 방식으로 선언합니다.

```c
// int형 포인터
int num;
int * ptr = &num;

// Person 구조체 포인터
typedef struct
{
    char name[30];
    int age;
} Person;

Person boy;
Person * ptr = &boy;
```

### 구조체 포인터를 통한 멤버 접근

구조체 포인터로 멤버에 접근하는 방법은 두 가지가 있습니다.

**방법 1: * 연산자와 . 연산자 사용**

```c
(*ptr).age = 10;
```

**방법 2: -> 연산자 사용 (화살표 연산자)**

```c
ptr->age = 10;
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>화살표 연산자 (->)</strong><br>
• 구조체 포인터 전용 연산자<br>
• <code>(*ptr).멤버</code>와 <code>ptr->멤버</code>는 동일<br>
• 가독성이 좋아 많이 사용됨<br>
• 직관적인 표현
</div>

```c
#include <stdio.h>

typedef struct
{
    char name[30];
    int age;
} Person;

int main(void)
{
    Person boy = {"호날두", 35};
    Person * ptr = &boy;   // Person형 포인터 변수는 구조체 변수 boy를 참조

    // 다음 두 코드는 동일한 결과를 출력
    printf("%s (%d)\n", (*ptr).name, (*ptr).age);
    printf("%s (%d)\n", ptr->name, ptr->age);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
호날두 (35)
호날두 (35)
</pre>

</details>

### 구조체의 멤버 변수로 선언된 포인터

포인터 변수도 구조체의 멤버로 선언될 수 있습니다.

```c
#include <stdio.h>

typedef struct
{
    int x;
    int y;
} Point;

typedef struct
{
    Point * start;   // 구조체 포인터 변수 start
    Point * end;     // 구조체 포인터 변수 end
} Line;

int main(void)
{
    Point p1 = {10, 8};
    Point p2 = {20, 40};

    Line line = {&p1, &p2};

    // line의 멤버 변수 start와 end는 각각 포인터 변수
    printf("선의 시작점: [%d, %d]\n", line.start->x, line.start->y);
    printf("선의 끝점: [%d, %d]\n", line.end->x, line.end->y);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
선의 시작점: [10, 8]
선의 끝점: [20, 40]
</pre>

</details>

**메모리 구조:**

```
Line 구조체 변수 line
┌────────────────────┐
│ start (Point *)    │──→ Point p1
│                    │    ┌────┬────┐
│                    │    │ x  │ y  │
│                    │    │ 10 │ 8  │
│                    │    └────┴────┘
│ end   (Point *)    │──→ Point p2
│                    │    ┌────┬────┐
└────────────────────┘    │ x  │ y  │
                          │ 20 │ 40 │
                          └────┴────┘
```

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 구조체 포인터 멤버의 활용</strong><br>
• 다른 구조체를 간접적으로 참조<br>
• 메모리 효율적인 데이터 구조 구현<br>
• 연결 리스트, 트리 등의 자료구조에 활용<br>
• <code>line.start->x</code>: 구조체 → 포인터 → 멤버 순서로 접근
</div>

---

## 2. 구조체의 중첩

구조체의 멤버로 <span class="blue-text">다른 구조체 변수</span>를 선언할 수 있으며, 이를 구조체의 중첩이라고 합니다.

### 구조체 중첩의 기본

```c
typedef struct
{
    char title[100];
    int published;
} Book;

typedef struct
{
    Book book;   // 멤버 변수로 구조체 변수 선언
} Bag;
```

### 중첩 구조체 초기화 및 접근

```c
#include <stdio.h>

typedef struct
{
    char title[100];
    int published;
} Book;

typedef struct
{
    Book book;   // 멤버 변수로 구조체 변수 선언
} Bag;

int main(void)
{
    /*
     구조체 변수 선언과 동시에 초기화
     이때 멤버 변수 또한 선언과 동시에 초기화
    */
    Bag myBag = {
        {"지금 하지 않으면 언제 하겠는가", 2018}
    };

    // 멤버 변수로서의 구조체 변수에 접근할 때에도 사용 연산자는 동일
    printf("책 제목: %s\n출간년도: %d년\n",
           myBag.book.title, myBag.book.published);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
책 제목: 지금 하지 않으면 언제 하겠는가
출간년도: 2018년
</pre>

</details>

**접근 방식:**

```
myBag.book.title

1. myBag 구조체 변수의 book 멤버에 접근
2. book 구조체 변수의 title 멤버에 접근
```

### 구조체 배열 멤버 변수

구조체 배열도 구조체의 멤버가 될 수 있습니다.

```c
#include <stdio.h>

typedef struct
{
    char title[100];
    int published;
} Book;

typedef struct
{
    Book books[3];   // 멤버 길이 3인 구조체 배열 선언
} Bag;

int main(void)
{
    // 선언과 동시에 초기화
    Bag myBag = {
        {
            {"지금 하지 않으면 언제 하겠는가", 2018},
            {"타이탄의 도구들", 2017},
            {"12가지 인생의 법칙", 2018}
        }
    };

    int i;

    // 배열 요소에 대한 순차적 접근
    for(i = 0; i < 3; i++)
    {
        printf("책 제목: %s\n출간년도: %d년\n",
               myBag.books[i].title,
               myBag.books[i].published);
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
책 제목: 지금 하지 않으면 언제 하겠는가
출간년도: 2018년
책 제목: 타이탄의 도구들
출간년도: 2017년
책 제목: 12가지 인생의 법칙
출간년도: 2018년
</pre>

</details>

**메모리 구조:**

```
Bag myBag
┌──────────────────────────────────────────┐
│ books[0]  │ books[1]  │ books[2]         │
├───────────┼───────────┼───────────       │
│ title     │ title     │ title            │
│ published │ published │ published        │
└──────────────────────────────────────────┘
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 구조체 중첩 주의사항</strong><br>
• 구조체 포인터 멤버 ≠ 구조체 멤버<br>
• 포인터: 주소만 저장 (4 또는 8바이트)<br>
• 직접 포함: 전체 구조체 크기만큼 메모리 할당<br>
• 초기화 시 중괄호 중첩 필요
</div>

---

## 3. 구조체와 함수

구조체 변수를 <span class="blue-text">함수의 인자로 전달</span>하고 <span class="blue-text">반환</span>할 수 있습니다.

### 구조체를 인자로 전달 (Call-by-value)

```c
#include <stdio.h>

typedef struct
{
    int s_id;
    int age;
} Student;

// 학번 및 나이를 인자로 받아 구조체 변수를 반환하는 함수
Student setStudent(int s_id, int age)
{
    Student s = {s_id, age};

    return s;
}

// 구조체를 전달받아 멤버 변수를 출력하는 함수
void printStudent(Student s)
{
    printf("학번: %d, 나이: %d\n", s.s_id, s.age);
}

int main(void)
{
    Student s = setStudent(20201212, 10);   // 반환된 구조체 변수를 대입
    printStudent(s);                        // 구조체 변수를 인자로 전달

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
학번: 20201212, 나이: 10
</pre>

</details>

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>Call-by-value 방식</strong><br>
• 구조체 변수 전체가 복사되어 전달<br>
• 원본 데이터에 영향을 주지 않음<br>
• 큰 구조체는 복사 비용이 클 수 있음<br>
• 함수 내부에서 값을 변경해도 원본은 그대로 유지
</div>

### 구조체와 Call-by-reference

구조체 포인터를 사용하면 원본 구조체를 직접 수정할 수 있습니다.

```c
#include <stdio.h>

typedef struct
{
    int xpos;
    int ypos;
} Point;

// 주소값을 참조하는 매개 변수
void setPosSameValue(Point * ptr)
{
    if(ptr->xpos > ptr->ypos)
        ptr->ypos = ptr->xpos;
    else
        ptr->xpos = ptr->ypos;
}

void printPoint(Point point)
{
    printf("x: %d, y: %d\n", point.xpos, point.ypos);
}

int main(void)
{
    Point position1 = {33, 66};
    Point position2 = {6, 3};

    // 주소값 전달
    setPosSameValue(&position1);
    setPosSameValue(&position2);

    // 구조체 출력
    printPoint(position1);
    printPoint(position2);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
x: 66, y: 66
x: 6, y: 6
</pre>

</details>

**동작 과정:**

```
[position1 = {33, 66}일 때]

setPosSameValue(&position1) 호출
→ ptr->xpos (33) < ptr->ypos (66)
→ ptr->xpos = ptr->ypos
→ position1 = {66, 66} (원본 변경됨)

[position2 = {6, 3}일 때]

setPosSameValue(&position2) 호출
→ ptr->xpos (6) > ptr->ypos (3)
→ ptr->ypos = ptr->xpos
→ position2 = {6, 6} (원본 변경됨)
```

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 Call-by-reference의 장점</strong><br>
• 원본 구조체를 직접 수정 가능<br>
• 큰 구조체도 주소만 전달 (효율적)<br>
• 메모리 복사 비용 절감<br>
• 함수에서 여러 값을 반환하는 효과<br><br>
<strong>사용 선택 기준</strong><br>
• 원본 수정 필요 → Call-by-reference<br>
• 원본 보존 필요 → Call-by-value<br>
• 큰 구조체 → Call-by-reference (효율성)
</div>

---

## 4. 종합 실습

### 문제 1 - 구조체 포인터 기본 (기초)

<div class="quiz-number">문제 1</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

typedef struct {
    int x;
    int y;
} Point;

int main(void) {
    Point p = {10, 20};
    Point * ptr = &p;

    ptr->x = 30;

    printf("%d", p.x);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="30"
   tags="구조체 심화"
%}

---

### 문제 2 - 화살표 연산자 (기초)

<div class="quiz-number">문제 2</div><strong>다음 중 올바른 구조체 포인터 접근 방법은?</strong>

```
A. ptr.member
B. ptr->member
C. (*ptr).member
D. B와 C 모두 올바르다.
```

{% include quiz-text.html
   id="quiz2"
   answer="D"
   tags="구조체 심화"
%}

---

### 문제 3 - 구조체 중첩 (중급)

<div class="quiz-number">문제 3</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

typedef struct {
    int score;
} Test;

typedef struct {
    Test math;
    Test english;
} Student;

int main(void) {
    Student s = {{90}, {85}};

    int total = s.math.score + s.english.score;

    printf("%d", total);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="175"
   tags="구조체 심화"
%}

---

### 문제 4 - 구조체 배열 멤버 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

typedef struct {
    int value;
} Data;

typedef struct {
    Data arr[3];
} Container;

int main(void) {
    Container c = {{{5}, {10}, {15}}};

    printf("%d", c.arr[1].value + c.arr[2].value);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="25"
   tags="구조체 심화"
%}

---

### 문제 5 - Call-by-reference (중급)

<div class="quiz-number">문제 5</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

typedef struct {
    int num;
} Data;

void modify(Data * ptr) {
    ptr->num *= 2;
}

int main(void) {
    Data d = {7};

    modify(&d);

    printf("%d", d.num);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% include quiz-text.html
   id="quiz5"
   code_html=code_block5
   answer="14"
   tags="구조체 심화"
%}

---

### 문제 6 - 구조체 함수 종합 (고급)

<div class="quiz-number">문제 6</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

typedef struct {
    int x;
    int y;
} Point;

Point createPoint(int x, int y) {
    Point p = {x, y};
    return p;
}

void doubleValues(Point * ptr) {
    ptr->x *= 2;
    ptr->y *= 2;
}

int main(void) {
    Point p = createPoint(3, 5);
    doubleValues(&p);

    printf("%d", p.x + p.y);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% raw %}
{% capture hint6 %}
createPoint(3, 5) → {3, 5}
doubleValues → {6, 10}
6 + 10 = 16
{% endcapture %}
{% endraw %}

{% include quiz-text.html
   id="quiz6"
   question=hint6
   code_html=code_block6
   answer="16"
   tags="구조체 심화"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 구조체 포인터</strong><br>
• 선언: <code>구조체타입 * 포인터이름;</code><br>
• 멤버 접근: <code>포인터->멤버</code> 또는 <code>(*포인터).멤버</code><br>
• -> 연산자(화살표 연산자)가 가독성이 좋음<br>
• 구조체 포인터 멤버 변수로 다른 구조체 참조 가능<br><br>

<strong>2. 구조체 중첩</strong><br>
• 구조체의 멤버로 다른 구조체 선언 가능<br>
• 접근: <code>외부구조체.내부구조체.멤버</code><br>
• 초기화 시 중괄호 중첩 사용<br>
• 구조체 배열도 멤버로 사용 가능<br>
• 포인터 멤버와 직접 포함 멤버는 다름<br><br>

<strong>3. 구조체와 함수</strong><br>
• Call-by-value: 구조체 전체 복사<br>
• Call-by-reference: 구조체 주소 전달<br>
• 함수 인자: <code>void func(구조체타입 변수)</code><br>
• 포인터 인자: <code>void func(구조체타입 * 포인터)</code><br>
• 구조체 반환: <code>구조체타입 func(...)</code><br><br>

<strong>4. Call-by-value vs Call-by-reference</strong><br>
• Call-by-value: 원본 보존, 복사 비용 발생<br>
• Call-by-reference: 원본 수정, 효율적<br>
• 큰 구조체는 포인터 전달 권장<br>
• 용도에 따라 적절히 선택<br><br>

<strong>5. 실무 팁</strong><br>
• -> 연산자 사용으로 코드 간결성 향상<br>
• 구조체 중첩으로 복잡한 데이터 구조 표현<br>
• 함수에서 구조체 수정 필요 시 포인터 사용<br>
• 연결 리스트, 트리 등에서 포인터 멤버 활용

</div>

---
