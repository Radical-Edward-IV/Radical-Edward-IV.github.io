---
layout: article
title: 2. 함수 심화
permalink: /notes/kr/c-deep-dive/chapter-02
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C DeepDive 과정 강의 노트, 배열을 전달받는 함수, Call-by-value와 Call-by-reference, 재귀 호출 함수를 다룹니다.
keywords: "C언어, 함수, 배열전달, Call-by-value, Call-by-reference, 재귀함수, 포인터"
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

## 1. 배열을 전달받는 함수

변수를 함수의 인자로 전달하는 방식과 배열을 함수의 인자로 전달하는 방식을 살펴봅니다. <span class="blue-text">배열의 이름은 배열의 시작 주소값을 나타내는 포인터</span>라는 것을 이해하고 있어야 합니다.

### 함수 호출 시 인자 전달 방식

함수에 매개 변수가 지정되어 있다면 사용자는 함수를 호출할 때 인자를 전달하여 지역 변수의 성격을 가진 매개 변수에 값을 저장할 수 있습니다.

**정수형 데이터를 전달받는 함수의 예:**

```c
int number = 10;
numberFunc(number);     // 함수 호출
printf("%d", number);   // 출력되는 number의 값은?
```

위 코드에서 변수 `number`를 함수의 인자로 전달하고 있습니다. 함수가 전달받은 값을 증가시킨 후에도 변수 `number`의 값은 변하지 않고 유지됩니다.

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>💡 값 복사 전달 (Call-by-value)</strong><br>
함수 호출 시 인자로 변수를 전달한다는 것은 변수가 가진 <span class="blue-text">값을 복사하여 전달</span>하기 때문입니다. 따라서 함수가 전달받은 값을 가지고 기능을 수행한다고 해도 그 값을 복사해 준 실제 변수에는 아무런 영향을 끼치지 않습니다.
</div>

### 함수 호출 시 배열의 전달

배열을 함수의 인자로 전달할 때는 <span class="blue-text">배열의 이름이 포인터 변수</span>이고, 배열의 이름이 저장하고 있는 데이터는 포인터(주소값)라는 것을 이해하고 있어야 합니다.

**잘못된 예:**

```c
int numberFunc(int arr) { ... }

int main(void)
{
    int number[3] = {1, 2, 3};
    numberFunc(number); // number는 포인터 변수
}
```

위 코드는 정수형으로 선언된 매개 변수 `arr`에 배열의 이름인 `number`를 전달하고 있습니다. 즉, int형 변수에 포인터(주소값)를 전달하고 있는데, 이후 연산을 진행하면 자료형 불일치로 인해 문제가 생길 수 있습니다.

### 올바른 배열 전달 방법

배열을 전달받아 연산을 진행하는 함수를 만들기 위해서는 <span class="blue-text">매개 변수를 포인터 변수로 선언</span>해야 합니다.

**방법 1: 포인터 변수로 선언**

```c
#include <stdio.h>

// 배열을 전달받을 수 있는 int형 포인터 변수 arr
int readArray(int *arr, int length)
{
    int i;
    printf("배열의 요소 읽어보기: [ ");
    for(i = 0; i < length; i++)
    {
        // arr[i] == *(arr + i)
        printf("%d", arr[i]);
        if(i + 1 < length)
        {
            printf(", ");
        }
        else
        {
            printf(" ");
        }
    }
    printf("]\n");
}

int main(void)
{
    int arr[3] = {3, 6, 9};
    readArray(arr, 3); // 배열의 이름 arr를 포인터 변수에 대입

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
배열의 요소 읽어보기: [ 3, 6, 9 ]
</pre>

<p style="margin-top: 10px;">
<strong>해설:</strong><br>
• 매개 변수를 포인터 변수로 선언하여 배열의 이름을 전달받을 수 있도록 함<br>
• 배열의 주소값만으로는 배열의 길이를 알 수 없으므로 길이 정보를 함께 인자로 전달
</p>

</details>

**방법 2: 대괄호를 사용한 선언**

```c
#include <stdio.h>

// 대괄호를 사용하여 배열을 전달받음 (길이 정보는 생략)
int readArray(int arr[], int length)
{
    int i;
    printf("배열의 요소 읽어보기: [ ");
    for(i = 0; i < length; i++)
    {
        printf("%d", arr[i]);
        if(i + 1 < length)
        {
            printf(", ");
        }
        else
        {
            printf(" ");
        }
    }
    printf("]\n");
}

int main(void)
{
    int arr[3] = {3, 6, 9};
    readArray(arr, 3);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
배열의 요소 읽어보기: [ 3, 6, 9 ]
</pre>

</details>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 두 방법의 동일성</strong><br>
매개 변수를 포인터 변수로 선언하는 것(<code>int *arr</code>)과 대괄호를 사용해 배열을 매개 변수가 전달받는 것(<code>int arr[]</code>)은 <span class="blue-text">완전히 동일한 매개 변수 선언</span>입니다.
</div>

---

## 2. Call-by-value와 Call-by-reference

값을 전달하여 함수를 호출하는 Call-by-value 방식과 주소값을 전달하여 함수를 호출하는 Call-by-reference 방식에 대해 알아봅니다.

### Call-by-value (값에 의한 호출)

함수를 정의할 때 매개 변수를 기본 형태의 변수로 지정하면 함수를 호출할 때 단순히 <span class="blue-text">값만 전달</span>합니다.

**특징:**
- 값을 복사하여 전달
- 함수 내에서 매개 변수 값을 변경해도 원본 변수에는 영향 없음
- 함수 종료 시 복사된 값은 소멸

**예제: 값 교환 함수 (실패)**

```c
#include <stdio.h>

void swapNumber(int num1, int num2)
{
    int temp = num1;
    num1 = num2;
    num2 = temp;
    printf("함수 안에서 확인한 결과, num1: %d num2: %d\n", num1, num2);
}

int main(void)
{
    int number1 = 33, number2 = 99;
    swapNumber(number1, number2);
    printf("함수 호출 완료 후 확인한 결과, number1: %d number2: %d\n", number1, number2);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
함수 안에서 확인한 결과, num1: 99 num2: 33
함수 호출 완료 후 확인한 결과, number1: 33 number2: 99
</pre>

<p style="margin-top: 10px;">
<strong>해설:</strong><br>
• main 함수에서 swapNumber 함수를 호출하면서 값을 복사하는 방식으로 전달<br>
• swapNumber 함수는 복사된 값을 이용해 기능을 수행하고, 함수 종료와 함께 복사한 값은 소멸<br>
• main 함수의 지역 변수 number1과 number2에는 아무 일도 일어나지 않음
</p>

</details>

### Call-by-reference (참조에 의한 호출)

실제 값의 변경이 이루어지게 하려면 <span class="blue-text">메모리 공간의 주소값을 전달</span>해야 합니다. 주소값을 전달받아 실제 메모리에 접근하는 방식을 Call-by-reference라고 합니다.

**예제: 값 교환 함수 (성공)**

```c
#include <stdio.h>

// 매개 변수로 포인터 변수 ptr1과 ptr2 선언
void swapNumber(int *ptr1, int *ptr2)
{
    // 실제 주소에 저장된 값을 서로 교환
    int temp = *ptr1;
    *ptr1 = *ptr2;
    *ptr2 = temp;
    printf("함수 안에서 확인한 결과, num1: %d num2: %d\n", *ptr1, *ptr2);
}

int main(void)
{
    int number1 = 33, number2 = 99;
    swapNumber(&number1, &number2); // 각 변수의 '주소'를 인자로 전달
    printf("함수 호출 후 확인한 결과, number1: %d number2: %d\n", number1, number2);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
함수 안에서 확인한 결과, num1: 99 num2: 33
함수 호출 후 확인한 결과, number1: 99 number2: 33
</pre>

<p style="margin-top: 10px;">
<strong>해설:</strong><br>
• 실제 주소값을 전달하여 해당 주소 안에 들어있는 값에 접근<br>
• 포인터 연산을 통해 실제 메모리 공간의 값을 변경<br>
• 함수 종료 후에도 원본 변수의 값이 변경됨
</p>

</details>

### 동작 흐름 비교

**Call-by-value:**
```
main 함수               numberFunc 함수
number = 10    ----복사---->  num = 10
                             num = 11
원본 변수 유지 <----종료----  복사본 소멸
number = 10 (변경 없음)
```

**Call-by-reference:**
```
main 함수               swapNumber 함수
number1 = 33           ptr1 → number1의 주소
number2 = 99           ptr2 → number2의 주소
                       *ptr1과 *ptr2 값 교환
number1 = 99 (변경됨!)
number2 = 33 (변경됨!)
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 핵심 차이</strong><br>
• <span class="blue-text">Call-by-value</span>: 값의 복사본 전달, 원본 변수 변경 불가<br>
• <span class="blue-text">Call-by-reference</span>: 주소값 전달, 원본 변수 변경 가능
</div>

---

## 3. 재귀 호출 함수

재귀(Recursion)의 사전적 의미는 <span class="blue-text">원래 자리로 되돌아가거나 되돌아온다</span>는 뜻입니다. 재귀 호출 함수의 의미와 사용법에 대해 알아봅니다.

### 재귀 호출 함수란?

재귀 호출 함수란 <span class="blue-text">함수가 몸체 내에서 자기 자신을 호출</span>하는 것을 말합니다.

**기본 예제 (무한 반복):**

```c
#include <stdio.h>

void sayHello()
{
    printf("Hello!\n");
    sayHello(); // 자기 자신을 다시 호출
}

int main(void)
{
    sayHello(); // 재귀 호출 함수 호출

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
Hello!
Hello!
Hello!
(무한 반복)
</pre>

<p style="margin-top: 10px;">
<strong>해설:</strong><br>
• sayHello 함수는 printf 실행 후 자기 자신을 다시 호출<br>
• 함수가 종료되기 전에 자기 자신을 다시 호출하면 몸체 안의 기능을 처음부터 다시 시작<br>
• 종료 조건이 없어 무한 반복 발생 (Ctrl + C로 강제 종료 필요)
</p>

</details>

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 재귀 호출의 위험</strong><br>
재귀 호출이 끝없이 반복되면 메모리 공간을 더 이상 사용할 수 없어 시스템적으로 강제 종료될 수 있습니다. <span class="red-text">반드시 종료 조건이 필요</span>합니다.
</div>

### 종료 조건이 있는 재귀 호출

재귀 호출 함수를 올바르게 사용하기 위해서는 <span class="blue-text">재귀 호출의 종료 조건</span>이 반드시 필요합니다.

**예제: 3번만 호출하는 재귀 함수**

```c
#include <stdio.h>

// count는 종료 조건을 위한 매개 변수
int sayHello(int count)
{
    printf("Hello!\n");

    // count가 3이 되면 더 이상 재귀 호출을 하지 않음
    if(count != 3){
        sayHello(count + 1);
    }

    return 0;
}

int main(void)
{
    sayHello(1); // 재귀 호출 함수 호출

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
Hello!
Hello!
Hello!
</pre>

<p style="margin-top: 10px;">
<strong>해설:</strong><br>
• 매개 변수 count가 재귀 호출의 종료 조건을 만듦<br>
• 함수 호출 시 count에 1을 전달하고, 재귀 호출마다 count + 1을 전달<br>
• count가 3이 되면 재귀 호출을 멈추고 함수가 종료됨
</p>

</details>

### 재귀 함수 활용 예제: 팩토리얼

재귀 함수는 수학적 정의가 재귀적인 경우에 매우 유용합니다.

**팩토리얼 공식:**
- n! = n × (n-1) × (n-2) × ... × 2 × 1
- n! = n × (n-1)!
- 0! = 1 (종료 조건)

```c
#include <stdio.h>

int factorial(int n)
{
    if(n == 0)
        return 1;           // 종료 조건
    else
        return n * factorial(n - 1); // 재귀 호출
}

int main(void)
{
    printf("5! = %d\n", factorial(5));
    printf("10! = %d\n", factorial(10));

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
5! = 120
10! = 3628800
</pre>

<p style="margin-top: 10px;">
<strong>동작 과정 (factorial(5)):</strong><br>
1. factorial(5) → 5 × factorial(4)<br>
2. factorial(4) → 4 × factorial(3)<br>
3. factorial(3) → 3 × factorial(2)<br>
4. factorial(2) → 2 × factorial(1)<br>
5. factorial(1) → 1 × factorial(0)<br>
6. factorial(0) → 1 (종료)<br>
7. 역순으로 계산: 1 × 1 × 2 × 3 × 4 × 5 = 120
</p>

</details>

### 재귀 함수 활용 예제: 피보나치 수열

피보나치 수열: 0, 1, 1, 2, 3, 5, 8, 13, 21, ...

**수학적 정의:**
- F(0) = 0
- F(1) = 1
- F(n) = F(n-1) + F(n-2) (n ≥ 2)

```c
#include <stdio.h>

int fibonacci(int n)
{
    if(n == 0)
        return 0;
    else if(n == 1)
        return 1;
    else
        return fibonacci(n - 1) + fibonacci(n - 2);
}

int main(void)
{
    int i;
    printf("피보나치 수열 (처음 10개): ");
    for(i = 0; i < 10; i++)
    {
        printf("%d ", fibonacci(i));
    }
    printf("\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
피보나치 수열 (처음 10개): 0 1 1 2 3 5 8 13 21 34
</pre>

</details>

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>💡 재귀 함수의 장단점</strong><br>
<strong>장점:</strong><br>
• 코드가 간결하고 이해하기 쉬움<br>
• 수학적 정의를 그대로 코드로 표현 가능<br>
• 복잡한 알고리즘을 단순하게 표현<br><br>
<strong>단점:</strong><br>
• 함수 호출이 반복되어 성능이 떨어질 수 있음<br>
• 메모리 사용량이 많을 수 있음<br>
• 잘못 작성하면 무한 재귀로 스택 오버플로우 발생 가능
</div>

---

## 4. 종합 실습

### 문제 1 - 배열 전달 (기초)

<div class="quiz-number">문제 1</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int sumArray(int arr[], int length)
{
    int sum = 0;
    int i;
    for(i = 0; i &lt; length; i++)
    {
        sum += arr[i];
    }
    return sum;
}

int main(void)
{
    int numbers[4] = {10, 20, 30, 40};
    printf("%d", sumArray(numbers, 4));

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="100"
   tags="함수 심화"
%}

---

### 문제 2 - Call-by-value (기초)

<div class="quiz-number">문제 2</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

void changeValue(int num)
{
    num = 100;
}

int main(void)
{
    int value = 50;
    changeValue(value);
    printf("%d", value);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint2 %}
Call-by-value 방식은 값을 복사하여 전달하므로 원본 변수는 변경되지 않습니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   question=hint2
   code_html=code_block2
   answer="50"
   tags="함수 심화"
%}

---

### 문제 3 - Call-by-reference (중급)

<div class="quiz-number">문제 3</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

void changeValue(int *ptr)
{
    *ptr = 100;
}

int main(void)
{
    int value = 50;
    changeValue(&value);
    printf("%d", value);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint3 %}
Call-by-reference 방식은 주소값을 전달하여 원본 변수를 직접 변경할 수 있습니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   question=hint3
   code_html=code_block3
   answer="100"
   tags="함수 심화"
%}

---

### 문제 4 - 재귀 함수 (중급)

<div class="quiz-number">문제 4</div><strong>다음 재귀 함수의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int mystery(int n)
{
    if(n == 1)
        return 1;
    else
        return n + mystery(n - 1);
}

int main(void)
{
    printf("%d", mystery(5));

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint4 %}
mystery(5) = 5 + mystery(4) = 5 + 4 + 3 + 2 + 1
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   question=hint4
   code_html=code_block4
   answer="15"
   tags="함수 심화"
%}

---

### 문제 5 - 배열과 포인터 (중급)

<div class="quiz-number">문제 5</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

void doubleArray(int *arr, int length)
{
    int i;
    for(i = 0; i &lt; length; i++)
    {
        arr[i] = arr[i] * 2;
    }
}

int main(void)
{
    int numbers[3] = {1, 2, 3};
    doubleArray(numbers, 3);
    printf("%d", numbers[1]);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint5 %}
배열을 전달하는 것은 주소값을 전달하는 것이므로 원본 배열이 변경됩니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=hint5
   code_html=code_block5
   answer="4"
   tags="함수 심화"
%}

---

### 문제 6 - 팩토리얼 (고급)

<div class="quiz-number">문제 6</div><strong>다음 재귀 함수의 실행 결과는?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int factorial(int n)
{
    if(n &lt;= 1)
        return 1;
    else
        return n * factorial(n - 1);
}

int main(void)
{
    printf("%d", factorial(4));

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint6 %}
4! = 4 × 3 × 2 × 1
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   question=hint6
   code_html=code_block6
   answer="24"
   tags="함수 심화"
%}

---

### 문제 7 - 값 교환 (고급)

<div class="quiz-number">문제 7</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

void swap(int *a, int *b)
{
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main(void)
{
    int x = 10, y = 20;
    swap(&x, &y);
    printf("%d %d", x, y);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7"
   code_html=code_block7
   answer="20 10"
   tags="함수 심화"
%}

---

### 문제 8 - 피보나치 (고급)

<div class="quiz-number">문제 8</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int fibonacci(int n)
{
    if(n == 0)
        return 0;
    else if(n == 1)
        return 1;
    else
        return fibonacci(n - 1) + fibonacci(n - 2);
}

int main(void)
{
    printf("%d", fibonacci(6));

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint8 %}
피보나치 수열: 0, 1, 1, 2, 3, 5, 8, 13...
{% endcapture %}

{% include quiz-text.html
   id="quiz8"
   question=hint8
   code_html=code_block8
   answer="8"
   tags="함수 심화"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 배열을 전달받는 함수</strong><br>
• 배열의 이름은 포인터(주소값)<br>
• 매개 변수: <code>int *arr</code> 또는 <code>int arr[]</code><br>
• 배열의 길이 정보는 별도로 전달 필요<br>
• 배열 전달은 주소값 전달 (원본 수정 가능)<br><br>

<strong>2. Call-by-value</strong><br>
• 값을 복사하여 전달<br>
• 원본 변수는 변경되지 않음<br>
• 함수 종료 시 복사본은 소멸<br>
• 일반 변수를 매개 변수로 사용<br><br>

<strong>3. Call-by-reference</strong><br>
• 주소값을 전달<br>
• 원본 변수를 직접 변경 가능<br>
• 포인터 변수를 매개 변수로 사용<br>
• 주소 연산자 <code>&</code>와 역참조 연산자 <code>*</code> 사용<br><br>

<strong>4. 재귀 호출 함수</strong><br>
• 함수가 자기 자신을 호출하는 함수<br>
• <span class="red-text">반드시 종료 조건 필요</span> (무한 재귀 방지)<br>
• 수학적 정의가 재귀적인 경우 유용<br>
• 예: 팩토리얼, 피보나치 수열<br><br>

<strong>5. 주요 차이점 정리</strong><br>
• 일반 변수 전달: Call-by-value (값 복사)<br>
• 포인터/배열 전달: Call-by-reference (주소 전달)<br>
• 재귀 함수: 종료 조건 + 자기 호출<br><br>

<strong>6. 주의사항</strong><br>
• 배열 전달 시 길이 정보 함께 전달<br>
• Call-by-reference 시 원본 변경됨에 유의<br>
• 재귀 함수는 종료 조건 반드시 명시<br>
• 재귀 깊이가 깊으면 스택 오버플로우 주의

</div>

---
