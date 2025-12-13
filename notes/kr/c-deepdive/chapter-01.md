---
layout: article
title: 1. 함수의 정의와 선언
permalink: /notes/kr/c-deepdive/chapter-01
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C DeepDive 과정 강의 노트, 사용자 정의 함수, 함수 선언과 정의, 함수의 형태, 변수의 생명주기를 다룹니다.
keywords: "C언어, 함수, 사용자정의함수, 함수선언, 함수정의, 지역변수, 전역변수, static변수"
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

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=C%20DeepDive&reversal=false&textBg=false)

---

## 1. 사용자 정의 함수

이전까지는 C 언어가 제공하는 표준 함수만 사용했습니다. 지금부터는 사용자가 직접 함수를 만들고, 이를 사용하는 방법에 대해 학습합니다.

### 함수란?

C 언어에서 함수란 <span class="blue-text">'만들어진 기능'</span>을 의미합니다. 다음은 우리에게 가장 익숙한 main 함수의 형태입니다.

```c
int main(void)
{
    // main 함수의 몸체(실행문)
}
```

main 함수를 자세히 보면 몸체 외에도 다른 구성 요소들이 있는 것을 알 수 있습니다.

**함수의 구성 요소:**

```c
반환형    함수의 이름    입력 데이터 표현
int         main          (void)
{
    // 함수의 몸체(함수의 기능)
    return 0;
}
```

각 구성 요소의 역할은 다음과 같습니다:

| 구성 요소 | 역할 |
|----------|------|
| **반환형** | 함수로부터 반환될 데이터의 자료형 |
| **함수의 이름** | 함수를 호출할 때 사용하는 함수의 이름 |
| **입력 데이터 표현** | 함수에 전달할 인자의 형태 (매개 변수) |
| **함수의 몸체** | 함수가 호출되었을 때 실행할 기능을 정의하는 부분 |

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>💡 사용자 정의 함수</strong><br>
main 함수처럼 구성 요소를 갖춘 함수를 만들어 원하는 시점마다 호출하여 사용할 수 있으며, 이를 <span class="blue-text">사용자 정의 함수</span>라고 부릅니다.
</div>

### 실습 1 - 사용자 정의 함수 만들기

다음은 사용자 정의 함수를 만들어 원하는 시점에 사용하는 예제입니다.

```c
#include <stdio.h>

// 사용자 정의 함수의 정의
int add(int a, int b)
{
    // 입력받은 두 개의 값을 더하여 반환
    return a + b;
}

int main(void)
{
    int result;

    // 사용자 정의 함수 호출
    result = add(3, 5);
    printf("함수가 반환한 값: %d\n", result);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
함수가 반환한 값: 8
</pre>

</details>

### 함수의 동작 원리

add 함수가 호출되면 다음과 같이 동작합니다:

1. 두 개의 int형 변수 a, b에 데이터를 전달받습니다
2. 두 변수에 저장된 전달 데이터를 더한 값을 반환합니다
3. 반환되는 값은 int형 정수입니다

```c
result = add(3, 5);
```

- 함수 호출 시 인자로 3과 5를 전달
- 매개 변수 a에 3, b에 5가 저장됨
- 함수는 3 + 5 = 8을 반환
- <span class="blue-text">함수의 호출문은 해당 함수의 반환값으로 대체됩니다</span>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 함수의 장점</strong><br>
• 코드의 중복을 줄일 수 있음<br>
• main 함수의 코드가 간결해짐<br>
• 유지 관리가 쉬워짐<br>
• 기능을 지속적으로 개선 가능
</div>

---

## 2. 함수 선언과 정의 분리하기

함수를 정의할 때는 반환형, 함수의 이름, 매개 변수, 함수의 몸체를 각각 정의해야 합니다. 사용자는 필요에 따라 자신이 정의한 함수를 <span class="blue-text">선언부와 정의부로 나누어 작성</span>할 수 있습니다.

### 선언부와 정의부

**선언부 (함수의 원형, Prototype):**
- 함수의 형태를 선언
- 반환형, 함수의 이름, 매개 변수를 포함

**정의부:**
- 함수의 기능을 정의
- 반환형, 함수의 이름, 매개 변수, 몸체를 포함

```c
// 선언부 (함수의 원형)
int add(int a, int b);

// 정의부
int add(int a, int b)
{
    return a + b;
}
```

### 실습 2 - 선언과 정의 분리

```c
#include <stdio.h>

// add 함수의 원형(선언부)
int add(int a, int b);

int main(void)
{
    int result;

    /*
    add 함수는 main 함수의 위에 이미 선언되어 있으므로
    컴파일러는 프로그램 내에서 add 함수를 찾아낼 수 있습니다.
    */
    result = add(3, 5);
    printf("함수가 반환한 값: %d\n", result);

    return 0;
}

// add 함수의 기능(정의부)
int add(int a, int b)
{
    return a + b;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
함수가 반환한 값: 8
</pre>

</details>

### 함수 선언의 필요성

사용자가 정의한 함수를 호출했을 때 정상적으로 동작하게 하려면 다음 두 가지 유형 중 하나를 선택해서 코드를 작성해야 합니다:

1. **선언부를 main 함수 위에 작성**하고, 정의부를 main 함수 아래에 작성 ✅ 권장
2. 선언부를 생략하고 main 함수 위에 정의부만 작성

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 권장 방식</strong><br>
선언부와 정의부를 분리하는 방식은 main 함수 위쪽에 작성되는 코드를 최소화하여 <span class="blue-text">main 함수가 코드의 상단에 위치</span>하게 할 수 있어 일반적으로 권장하는 방식입니다.
</div>

---

## 3. 함수의 4가지 형태

사용자 정의 함수는 <span class="blue-text">입력값과 반환값의 사용 여부</span>에 따라 네 가지 형태로 구분합니다.

### 함수 형태 분류

| 형태 | 입력값 | 반환값 |
|------|--------|--------|
| **형태 1** | ✅ 있음 | ✅ 있음 |
| **형태 2** | ✅ 있음 | ❌ 없음 |
| **형태 3** | ❌ 없음 | ✅ 있음 |
| **형태 4** | ❌ 없음 | ❌ 없음 |

---

### 형태 1: 입력값과 반환값이 모두 있는 경우

가장 일반적인 함수의 형태입니다.

**예제: 두 정수 중 큰 값을 반환하는 함수**

```c
#include <stdio.h>

// 정수형 데이터 두 개를 전달받아 정수형 데이터를 반환
int getBigger(int n1, int n2)
{
    if (n1 > n2)
    {
        return n1;
    }
    else if (n1 < n2)
    {
        return n2;
    }
    else
    {
        return 0;
    }
}

int main(void)
{
    int result; // 반환값을 저장하는 변수

    result = getBigger(3, 5); // 3과 5 중 큰 값을 반환
    printf("첫 번째 결과: %d\n", result);

    result = getBigger(8, 2); // 8과 2 중 큰 값을 반환
    printf("두 번째 결과: %d\n", result);

    result = getBigger(4, 4); // 4와 4는 같음
    printf("세 번째 결과: %d\n", result);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
첫 번째 결과: 5
두 번째 결과: 8
세 번째 결과: 0
</pre>

</details>

---

### 형태 2: 입력값만 존재하는 경우

반환값이 없는 경우 반환형을 <span class="yellow-code">void</span>로 선언합니다.

```c
void printNumber(int num)
{
    printf("당신이 입력한 정수는 %d입니다\n", num);
}
```

- void는 "반환하지 않는다"는 의미
- return 키워드가 없거나 `return;`만 사용
- 함수의 몸체에 정의된 기능만 수행

---

### 형태 3: 반환값만 존재하는 경우

입력값이 없는 경우 매개 변수 자리에 <span class="yellow-code">void</span>를 사용합니다.

```c
int inputNumber(void)
{
    int num;
    printf("정수를 입력해주세요: ");
    scanf("%d", &num);
    return num;
}
```

- void는 "인자를 입력받지 않는다"는 의미
- 함수 호출 시 괄호를 비워둠: `inputNumber();`

---

### 형태 4: 입력값과 반환값이 모두 없는 경우

입력값과 반환값이 모두 없는 경우 반환형과 매개 변수 모두 <span class="yellow-code">void</span>를 사용합니다.

```c
void guide(void)
{
    printf("inputNumber 함수를 통해 정수를 입력할 수 있습니다.\n");
    printf("또한 printNumber 함수를 통해 입력한 정수를 출력할 수도 있습니다.\n");
}
```

### 실습 3 - 네 가지 형태 종합

```c
#include <stdio.h>

// 입력값과 반환값이 모두 없는 함수
void guide(void)
{
    printf("inputNumber 함수를 통해 정수를 입력할 수 있습니다.\n");
    printf("또한 printNumber 함수를 통해 입력한 정수를 출력할 수도 있습니다.\n");
}

// 입력값만 존재하는 함수
void printNumber(int num)
{
    printf("당신이 입력한 정수는 %d입니다\n", num);
}

// 반환값만 존재하는 함수
int inputNumber(void)
{
    int num;
    printf("정수를 입력해주세요: ");
    scanf("%d", &num);

    return num;
}

int main(void)
{
    guide(); // 안내 함수 호출
    int num = inputNumber(); // 반환값을 저장
    printNumber(num);
    num = inputNumber();
    printNumber(num);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
inputNumber 함수를 통해 정수를 입력할 수 있습니다.
또한 printNumber 함수를 통해 입력한 정수를 출력할 수도 있습니다.
정수를 입력해주세요: 4
당신이 입력한 정수는 4입니다
정수를 입력해주세요: 6
당신이 입력한 정수는 6입니다
</pre>

</details>

---

## 4. 변수의 생명주기

변수는 선언되는 위치에 따라 <span class="blue-text">지역 변수</span>와 <span class="blue-text">전역 변수</span>로 구분할 수 있습니다.

### 지역 변수 (Local Variable)

지역 변수는 <span class="blue-text">특정 지역 내에서만 사용할 수 있는 변수</span>로, 여기에서 지역이란 중괄호 `{}`로 감싸고 있는 코드 블록을 의미합니다.

**지역 변수의 특성:**

- 중괄호 내에 선언된 모든 변수는 지역 변수
- 함수의 매개 변수도 지역 변수
- 자신이 선언된 지역 외 다른 영역에서는 사용할 수 없음
- 선언된 지역이 서로 다른 경우에는 이름이 중복되어도 문제없음

### 실습 4 - 지역 변수

```c
#include <stdio.h>

int localFunc(int num)
{
    int result = 0;
    return result + num;
}

int main(void)
{
    int num = 5;
    int result = localFunc(num);

    printf("결과: %d\n", result);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
결과: 5
</pre>

<p style="margin-top: 10px;">
<strong>해설:</strong><br>
• main 함수의 num과 localFunc 함수의 매개 변수 num은 이름은 같지만 서로 다른 변수<br>
• main 함수의 result와 localFunc 함수의 result도 영역이 다르므로 문제없음
</p>

</details>

---

### 전역 변수 (Global Variable)

전역 변수는 <span class="blue-text">모든 지역에서 접근이 가능한 변수</span>입니다. 전역 변수를 선언하려면 중괄호로 묶이지 않은 위치에 선언해야 합니다.

**전역 변수의 특성:**

- 프로그램의 시작과 함께 메모리 공간에 할당되어 종료할 때까지 존재
- 프로그램의 모든 영역에서 접근 가능
- 전역 변수와 동일한 이름의 지역 변수가 선언된 경우 해당 지역 내에서는 지역 변수가 우선

### 실습 5 - 전역 변수

```c
#include <stdio.h>

// 전역 변수 number
int number = 0;

void printNumber(void)
{
    printf("전역 변수 number는 %d를 저장하고 있다!\n", number);
}

int main(void)
{
    // 지역 변수 number
    int number = 3;
    printf("지역 변수 number는 %d를 저장하고 있다!\n", number);

    printNumber();

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
지역 변수 number는 3을 저장하고 있다!
전역 변수 number는 0을 저장하고 있다!
</pre>

<p style="margin-top: 10px;">
<strong>해설:</strong><br>
• 전역 변수 number는 모든 함수에서 접근 가능<br>
• main 함수 내에서는 지역 변수 number가 전역 변수보다 우선<br>
• printNumber 함수에서는 전역 변수 number에 접근
</p>

</details>

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 전역 변수 사용 주의</strong><br>
전역 변수는 어디에서나 접근할 수 있지만, 지나치게 많아질 경우 프로그램의 유지관리가 어려워질 수 있으니 <span class="red-text">남용하지 않는 것이 좋습니다</span>.
</div>

---

### static 변수

<span class="yellow-code">static</span> 키워드를 사용하여 static 변수를 선언할 수 있습니다. 특히 지역 변수가 가진 특성을 일부 보완해 주는 역할을 합니다.

**static 변수의 특성:**

| 구분 | static 미사용 | static 사용 |
|------|--------------|-------------|
| **생명주기** | 선언된 지역 내에서 생성과 소멸 반복 | 최초 생성 후 프로그램 종료까지 유지 |
| **초기화** | 함수 호출마다 초기화 | 최초 1회만 초기화 |
| **값 유지** | 함수 종료 시 소멸 | 이전 값 유지 |

### 실습 6 - static 변수

```c
#include <stdio.h>

void increaseNumber()
{
    static int number = 0; // static 지역 변수 number의 선언

    number++;
    printf("number: %d\n", number);
}

int main(void)
{
    increaseNumber();
    increaseNumber();
    increaseNumber();
    increaseNumber();
    increaseNumber();

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
number: 1
number: 2
number: 3
number: 4
number: 5
</pre>

<p style="margin-top: 10px;">
<strong>해설:</strong><br>
• static 변수 number는 최초 1회 초기화된 후 소멸되지 않고 메모리에 유지<br>
• 함수 호출마다 number가 0으로 초기화되지 않고 이전 값을 유지<br>
• 따라서 값이 계속 증가하는 것을 확인할 수 있음
</p>

</details>

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>💡 static 변수 활용</strong><br>
static 변수는 함수가 호출된 횟수를 세거나, 함수 내에서 이전 상태를 기억해야 할 때 유용합니다.
</div>

---

## 5. 종합 실습

### 문제 1 - 함수의 반환값 (기초)

<div class="quiz-number">문제 1</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int multiply(int a, int b)
{
    return a * b;
}

int main(void)
{
    int result = multiply(4, 5);
    printf("%d", result);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="20"
   tags="함수의 정의와 선언"
%}

---

### 문제 2 - void 함수 (기초)

<div class="quiz-number">문제 2</div><strong>다음 중 올바른 함수 선언은?</strong>

```
A. void printHello();
B. printHello(void);
C. void printHello(void);
D. printHello();
```

{% include quiz-text.html
   id="quiz2"
   answer="C"
   tags="함수의 정의와 선언"
%}

---

### 문제 3 - 지역 변수 (중급)

<div class="quiz-number">문제 3</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

void func()
{
    int x = 10;
    x = x + 5;
}

int main(void)
{
    int x = 0;
    func();
    printf("%d", x);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint3 %}
main 함수의 x와 func 함수의 x는 서로 다른 지역 변수입니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   question=hint3
   code_html=code_block3
   answer="0"
   tags="함수의 정의와 선언"
%}

---

### 문제 4 - 전역 변수 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int global = 100;

void changeGlobal()
{
    global = 200;
}

int main(void)
{
    changeGlobal();
    printf("%d", global);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="200"
   tags="함수의 정의와 선언"
%}

---

### 문제 5 - static 변수 (중급)

<div class="quiz-number">문제 5</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

void counter()
{
    static int count = 0;
    count = count + 10;
    printf("%d ", count);
}

int main(void)
{
    counter();
    counter();
    counter();

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint5 %}
static 변수는 최초 1회만 초기화되며, 이전 값을 유지합니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=hint5
   code_html=code_block5
   answer="10 20 30"
   tags="함수의 정의와 선언"
%}

---

### 문제 6 - 함수 호출과 반환 (고급)

<div class="quiz-number">문제 6</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int add(int a, int b)
{
    return a + b;
}

int calculate(int x)
{
    return add(x, 10) + add(x, 20);
}

int main(void)
{
    int result = calculate(5);
    printf("%d", result);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint6 %}
calculate(5)는 add(5, 10) + add(5, 20)을 계산합니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   question=hint6
   code_html=code_block6
   answer="40"
   tags="함수의 정의와 선언"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 사용자 정의 함수</strong><br>
• 구성 요소: 반환형, 함수 이름, 매개 변수, 함수 몸체<br>
• 함수는 호출될 때만 실행됨<br>
• 함수 호출문은 반환값으로 대체됨<br><br>

<strong>2. 함수 선언과 정의</strong><br>
• 선언부(원형): 반환형, 함수 이름, 매개 변수<br>
• 정의부: 선언부 + 함수 몸체<br>
• 권장: 선언부는 main 위, 정의부는 main 아래<br><br>

<strong>3. 함수의 4가지 형태</strong><br>
• 입력값 O, 반환값 O: <code>int func(int a)</code><br>
• 입력값 O, 반환값 X: <code>void func(int a)</code><br>
• 입력값 X, 반환값 O: <code>int func(void)</code><br>
• 입력값 X, 반환값 X: <code>void func(void)</code><br><br>

<strong>4. 변수의 생명주기</strong><br>
• 지역 변수: 중괄호 내에서만 유효, 함수 종료 시 소멸<br>
• 전역 변수: 모든 영역에서 접근 가능, 프로그램 종료까지 유지<br>
• static 변수: 최초 1회 초기화, 프로그램 종료까지 값 유지<br><br>

<strong>5. 주의사항</strong><br>
• 함수는 정의만으로는 실행되지 않음 (호출 필요)<br>
• 전역 변수 남용 주의<br>
• 지역이 다르면 같은 이름의 변수 사용 가능<br>
• 매개 변수도 지역 변수의 일종

</div>

---
