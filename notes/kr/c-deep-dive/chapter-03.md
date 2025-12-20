---
layout: article
title: 3. 메모리 구조와 변수의 생명주기
permalink: /notes/kr/c-deep-dive/chapter-03
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C DeepDive 강의 노트, 프로그램 메모리 구조(코드, 데이터, 스택, 힙 영역), 전역 변수와 지역 변수의 차이를 다룹니다.
keywords: "C언어, 메모리구조, 코드영역, 데이터영역, 스택영역, 힙영역, 전역변수, 지역변수"
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

## 1. 프로그램의 메모리 구조

C 언어 프로그램이 실행될 때 운영체제는 메모리 공간을 할당합니다. 이 메모리는 <span class="blue-text">효율적인 관리</span>를 위해 네 가지 영역으로 나뉩니다.

### 메모리의 4가지 영역

프로그램 실행 시 메모리는 다음과 같이 구분됩니다.

```
┌─────────────┐ ← 높은 주소
│  스택 영역   │
│   (Stack)   │
├─────────────┤
│             │
│    (여유)    │
│             │
├─────────────┤
│  힙 영역     │
│   (Heap)    │
├─────────────┤
│ 데이터 영역  │
│   (Data)    │
├─────────────┤
│  코드 영역   │
│   (Code)    │
└─────────────┘ ← 낮은 주소
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>왜 메모리를 구분할까?</strong><br>
도서관에서 책을 분야별로 나누어 관리하듯이, C 언어도 메모리를 목적별로 구분하여 효율적으로 관리합니다.
</div>

### 각 영역의 역할

| 영역 | 저장 대상 | 생명주기 |
|------|----------|----------|
| **코드 영역** | 실행할 프로그램 코드(명령어) | 프로그램 시작~종료 |
| **데이터 영역** | 전역 변수, static 변수 | 프로그램 시작~종료 |
| **스택 영역** | 지역 변수, 매개변수 | 함수 시작~종료 |
| **힙 영역** | 동적 할당 메모리 | 사용자가 관리 |

---

## 2. 코드 영역 (Code Area)

코드 영역은 <span class="blue-text">프로그램의 실행 명령어</span>를 저장하는 공간입니다.

### 코드 영역의 특징

```c
#include <stdio.h>

int main(void) {
    printf("Hello World\n");
    return 0;
}
```

위 코드가 실행되면:
- 모든 실행 명령어가 코드 영역에 저장됨
- CPU가 이 영역의 명령어를 순서대로 실행
- <span class="red-text">읽기 전용</span> 메모리 (수정 불가)

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 코드 영역의 특징</strong><br>
• 프로그램이 실행되는 동안 변하지 않음<br>
• 읽기 전용으로 보호됨<br>
• 함수의 코드도 이 영역에 저장됨
</div>

---

## 3. 데이터 영역 (Data Area)

데이터 영역은 <span class="blue-text">전역 변수</span>와 <span class="blue-text">static 변수</span>를 저장하는 공간입니다.

### 전역 변수

전역 변수는 함수 밖에서 선언된 변수로, 프로그램 전체에서 사용 가능합니다.

```c
#include <stdio.h>

int globalVar = 100;  // 전역 변수 (데이터 영역에 저장)

void printGlobal(void) {
    printf("전역 변수: %d\n", globalVar);
}

int main(void) {
    printf("main에서: %d\n", globalVar);
    printGlobal();

    globalVar = 200;
    printGlobal();

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
main에서: 100
전역 변수: 100
전역 변수: 200
</pre>

<p style="margin-top: 10px;">
전역 변수는 모든 함수에서 접근 가능합니다.
</p>

</details>

### static 변수

static 변수는 지역 변수이지만 데이터 영역에 저장되어 <span class="blue-text">값이 유지</span>됩니다.

```c
#include <stdio.h>

void counter(void) {
    int normalVar = 0;      // 지역 변수 (스택 영역)
    static int staticVar = 0;  // static 변수 (데이터 영역)

    normalVar++;
    staticVar++;

    printf("일반 변수: %d, static 변수: %d\n", normalVar, staticVar);
}

int main(void) {
    counter();  // 1번 호출
    counter();  // 2번 호출
    counter();  // 3번 호출

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
일반 변수: 1, static 변수: 1
일반 변수: 1, static 변수: 2
일반 변수: 1, static 변수: 3
</pre>

<p style="margin-top: 10px;">
static 변수는 함수가 끝나도 값이 유지됩니다.
</p>

</details>

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>데이터 영역의 특징</strong><br>
• 프로그램 시작 시 메모리 할당<br>
• 프로그램 종료 시까지 유지<br>
• 초기화하지 않으면 자동으로 0으로 초기화
</div>

---

## 4. 스택 영역 (Stack Area)

스택 영역은 <span class="blue-text">지역 변수</span>와 <span class="blue-text">함수 매개변수</span>를 저장하는 공간입니다.

### 지역 변수의 생명주기

```c
#include <stdio.h>

void myFunc(void) {
    int localVar = 10;  // 지역 변수 (스택 영역에 저장)
    printf("함수 내부: %d\n", localVar);
}  // localVar 소멸

int main(void) {
    int num = 5;  // 지역 변수 (스택 영역에 저장)

    printf("main 시작: %d\n", num);
    myFunc();
    printf("main 종료: %d\n", num);

    return 0;
}  // num 소멸
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
main 시작: 5
함수 내부: 10
main 종료: 5
</pre>

</details>

### 스택의 동작 원리

함수가 호출될 때마다 스택에 메모리가 쌓이고, 함수가 종료되면 제거됩니다.

```c
#include <stdio.h>

void func2(int c) {
    printf("func2: %d\n", c);
}

void func1(int b) {
    printf("func1: %d\n", b);
    func2(b + 10);
}

int main(void) {
    int a = 5;
    printf("main: %d\n", a);
    func1(a + 5);
    printf("main 다시: %d\n", a);

    return 0;
}
```

**메모리 상태 변화:**

```
[Step 1] main 실행
┌──────────┐
│ a = 5    │ ← main의 지역변수
└──────────┘

[Step 2] func1 호출
┌──────────┐
│ b = 10   │ ← func1의 매개변수
├──────────┤
│ a = 5    │ ← main의 지역변수
└──────────┘

[Step 3] func2 호출
┌──────────┐
│ c = 20   │ ← func2의 매개변수
├──────────┤
│ b = 10   │ ← func1의 매개변수
├──────────┤
│ a = 5    │ ← main의 지역변수
└──────────┘

[Step 4] func2 종료
┌──────────┐
│ b = 10   │ ← func1의 매개변수
├──────────┤
│ a = 5    │ ← main의 지역변수
└──────────┘

[Step 5] func1 종료
┌──────────┐
│ a = 5    │ ← main의 지역변수
└──────────┘
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 스택 영역 주의사항</strong><br>
• 함수 종료 시 자동으로 메모리 해제<br>
• <span class="red-text">지역 변수의 주소를 반환하면 위험!</span><br>
• 스택 크기는 제한적 (너무 많은 재귀 호출 시 오버플로우)
</div>

---

## 5. 힙 영역 (Heap Area)

힙 영역은 <span class="blue-text">프로그래머가 직접 관리</span>하는 메모리 공간입니다.

### 힙 영역의 필요성

지역 변수는 함수가 끝나면 사라지므로, 다음과 같은 코드는 문제가 발생할 수 있습니다.

```c
#include <stdio.h>

char *getString(void) {
    char str[100];  // 지역 변수
    printf("문자열 입력: ");
    scanf("%s", str);

    return str;  // ⚠️ 위험! 함수 종료 후 str은 소멸됨
}

int main(void) {
    char *result = getString();
    printf("입력한 문자열: %s\n", result);  // 예측 불가능한 결과

    return 0;
}
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>힙 영역의 특징</strong><br>
• 프로그래머가 직접 할당하고 해제<br>
• malloc, calloc 등의 함수로 할당<br>
• free 함수로 해제<br>
• 함수가 끝나도 메모리 유지
</div>

**힙 영역은 다음 챕터에서 자세히 다룹니다.**

---

## 6. 메모리 영역 종합 예제

모든 메모리 영역을 사용하는 예제를 살펴보겠습니다.

```c
#include <stdio.h>

int globalNum = 100;  // 전역 변수 (데이터 영역)

void printStatic(void) {
    static int count = 0;  // static 변수 (데이터 영역)
    count++;
    printf("호출 횟수: %d\n", count);
}

void localExample(int param) {  // 매개변수 (스택 영역)
    int local = 10;  // 지역 변수 (스택 영역)
    printf("지역 변수: %d, 매개변수: %d\n", local, param);
}

int main(void) {
    int mainLocal = 5;  // 지역 변수 (스택 영역)

    printf("전역 변수: %d\n", globalNum);

    printStatic();
    printStatic();

    localExample(mainLocal);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
전역 변수: 100
호출 횟수: 1
호출 횟수: 2
지역 변수: 10, 매개변수: 5
</pre>

</details>

**메모리 구조:**

```
[코드 영역]
- main 함수 코드
- printStatic 함수 코드
- localExample 함수 코드

[데이터 영역]
- globalNum = 100
- count = 2 (static)

[스택 영역] (실행 중)
- mainLocal = 5
- param = 5 (localExample 호출 시)
- local = 10 (localExample 호출 시)

[힙 영역]
- (이 예제에서는 미사용)
```

---

## 7. 종합 실습

### 문제 1 - 변수의 저장 위치 (기초)

<div class="quiz-number">문제 1</div><strong>다음 중 데이터 영역에 저장되는 변수는?</strong>

```c
#include <stdio.h>

int a = 10;

int main(void) {
    int b = 20;
    static int c = 30;

    return 0;
}
```

**선택지:**
- A. a만
- B. a와 c
- C. b와 c
- D. 모두

{% include quiz-text.html
   id="quiz1"
   answer="B"
   tags="메모리 구조"
%}

---

### 문제 2 - static 변수 (기초)

<div class="quiz-number">문제 2</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

void test(void) {
    static int num = 0;
    num += 5;
    printf("%d ", num);
}

int main(void) {
    test();
    test();
    test();

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="5 10 15"
   tags="메모리 구조"
%}

---

### 문제 3 - 지역 변수의 생명주기 (중급)

<div class="quiz-number">문제 3</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

void func(void) {
    int x = 100;
    x++;
    printf("%d ", x);
}

int main(void) {
    func();
    func();

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="101 101"
   tags="메모리 구조"
%}

---

### 문제 4 - 전역 변수와 지역 변수 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int num = 50;

void change(void) {
    int num = 100;
    num += 10;
    printf("%d ", num);
}

int main(void) {
    change();
    printf("%d", num);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="110 50"
   tags="메모리 구조"
%}

---

### 문제 5 - static과 일반 변수 비교 (고급)

<div class="quiz-number">문제 5</div><strong>다음 코드의 마지막 출력 결과는?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

void counter(void) {
    int a = 0;
    static int b = 0;

    a += 3;
    b += 3;
}

int main(void) {
    int i;
    for (i = 0; i < 5; i++) {
        counter();
    }

    // counter 함수의 static 변수 b의 최종 값은?
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint5 %}
static 변수 b는 5번 호출되면서 매번 3씩 증가합니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=hint5
   code_html=code_block5
   answer="15"
   tags="메모리 구조"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 메모리의 4가지 영역</strong><br>
• <strong>코드 영역</strong>: 프로그램 실행 명령어 저장<br>
• <strong>데이터 영역</strong>: 전역 변수, static 변수 저장<br>
• <strong>스택 영역</strong>: 지역 변수, 매개변수 저장<br>
• <strong>힙 영역</strong>: 동적 할당 메모리 저장<br><br>

<strong>2. 전역 변수 vs 지역 변수</strong><br>
• 전역 변수: 데이터 영역, 프로그램 전체에서 사용<br>
• 지역 변수: 스택 영역, 함수 내에서만 사용<br><br>

<strong>3. static 변수</strong><br>
• 데이터 영역에 저장<br>
• 함수가 끝나도 값이 유지됨<br>
• 초기화는 단 한 번만 수행<br><br>

<strong>4. 스택 영역의 특징</strong><br>
• 함수 호출 시 자동 할당<br>
• 함수 종료 시 자동 해제<br>
• LIFO(Last In First Out) 구조<br><br>

<strong>5. 메모리 관리 원칙</strong><br>
• 데이터/스택 영역: 자동 관리<br>
• 힙 영역: 수동 관리 (malloc/free)<br>
• 지역 변수 주소 반환 금지

</div>

---
