---
layout: article
title: 4. 반복문
permalink: /notes/kr/java-basic/chapter-04
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: Java 기초 과정 강의 노트, 반복문(for, while, do-while), 중첩 반복문, break와 continue를 다룹니다.
keywords: "Java, 반복문, for, while, do-while, 중첩 반복문, break, continue, 무한루프"
---

<script src="/assets/js/quiz.js"></script>

<style>
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
    .quiz-container {
        margin: 20px 0;
        padding: 15px;
        border: 1px solid #e5e7eb;
        border-radius: 12px;
        background-color: #ffffff;
        box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);
    }
    .quiz-container:hover {
        box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);
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

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=Java%20Basic&reversal=false&textBg=false)

---

## 반복문이란?

프로그램에서 **같은 작업을 여러 번 반복**해야 할 때가 많습니다. 반복문은 특정 코드 블록을 조건에 따라 반복 실행하는 제어문입니다.

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">일상 속 반복문</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
"1부터 100까지 모두 더해라"라는 문제가 있다면, 100줄의 코드를 작성하는 대신 반복문을 사용하면 몇 줄로 해결할 수 있습니다.
</p>
</div>

### 반복문의 종류

Java에서 제공하는 반복문은 다음과 같습니다:

| 반복문 | 용도 |
|--------|------|
| `for` | 반복 횟수가 정해진 경우 |
| `while` | 조건이 참인 동안 반복 |
| `do-while` | 최소 1회 실행 후 조건 검사 |

---

## for 문

<span class="blue-text">for 문</span>은 반복 횟수가 명확할 때 가장 많이 사용하는 반복문입니다.

### 기본 문법

```java
for (초기화; 조건식; 증감식) {
    // 반복 실행할 코드
}
```

### 실행 흐름

```
1. 초기화 (한 번만 실행)
        ↓
2. 조건식 검사 ──(false)──→ 반복문 종료
        ↓ (true)
3. 반복 코드 실행
        ↓
4. 증감식 실행
        ↓
   2번으로 돌아감
```

### 기본 예제: 1부터 5까지 출력

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
// 출력:
// 1
// 2
// 3
// 4
// 5
```

**실행 과정:**

| 단계 | i 값 | 조건(i <= 5) | 출력 | i++ 후 |
|------|------|--------------|------|--------|
| 1 | 1 | true | 1 | 2 |
| 2 | 2 | true | 2 | 3 |
| 3 | 3 | true | 3 | 4 |
| 4 | 4 | true | 4 | 5 |
| 5 | 5 | true | 5 | 6 |
| 6 | 6 | false | - | 종료 |

### 합계 계산

```java
int sum = 0;

for (int i = 1; i <= 100; i++) {
    sum += i;
}

System.out.println("1부터 100까지의 합: " + sum);
// 출력: 1부터 100까지의 합: 5050
```

### 역순 반복

```java
for (int i = 5; i >= 1; i--) {
    System.out.println(i);
}
// 출력:
// 5
// 4
// 3
// 2
// 1
```

### 다양한 증감식

```java
// 2씩 증가 (짝수 출력)
for (int i = 2; i <= 10; i += 2) {
    System.out.print(i + " ");
}
// 출력: 2 4 6 8 10

// 3씩 증가
for (int i = 0; i < 15; i += 3) {
    System.out.print(i + " ");
}
// 출력: 0 3 6 9 12
```

### for 문 변형

```java
// 초기화 생략
int i = 0;
for (; i < 5; i++) {
    System.out.print(i + " ");
}

// 조건식 생략 (무한 루프 - break 필요)
for (int j = 0; ; j++) {
    if (j >= 5) break;
    System.out.print(j + " ");
}

// 증감식 생략
for (int k = 0; k < 5; ) {
    System.out.print(k + " ");
    k++;
}
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">변수 범위 주의</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
for 문 내에서 선언한 변수(예: <code>int i</code>)는 for 문 블록 내에서만 사용 가능합니다. 반복문 밖에서 사용하려면 반복문 전에 선언해야 합니다.
</p>
</div>

---

## while 문

<span class="blue-text">while 문</span>은 조건이 참인 동안 반복을 계속합니다. 반복 횟수가 정해지지 않은 경우에 유용합니다.

### 기본 문법

```java
while (조건식) {
    // 조건이 true인 동안 반복 실행
}
```

### 실행 흐름

```
1. 조건식 검사 ──(false)──→ 반복문 종료
        ↓ (true)
2. 반복 코드 실행
        ↓
   1번으로 돌아감
```

### 기본 예제

```java
int i = 1;

while (i <= 5) {
    System.out.println(i);
    i++;
}
// 출력:
// 1
// 2
// 3
// 4
// 5
```

### for 문과 while 문 비교

**for 문:**

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

**while 문:**

```java
int i = 1;
while (i <= 5) {
    System.out.println(i);
    i++;
}
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">for vs while 선택 기준</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <strong>for 문</strong>: 반복 횟수가 명확할 때 (배열 순회, 정해진 횟수 반복)<br>
• <strong>while 문</strong>: 조건에 따라 반복할 때 (파일 읽기, 사용자 입력 대기)
</p>
</div>

### 조건에 따른 반복

```java
int number = 1234;
int digitCount = 0;

while (number > 0) {
    number /= 10;  // 10으로 나눠 자릿수 줄이기
    digitCount++;
}

System.out.println("자릿수: " + digitCount);
// 출력: 자릿수: 4
```

### 합계 계산 (while 버전)

```java
int sum = 0;
int i = 1;

while (i <= 100) {
    sum += i;
    i++;
}

System.out.println("합계: " + sum);
// 출력: 합계: 5050
```

---

## do-while 문

<span class="blue-text">do-while 문</span>은 <span class="red-text">최소 1회 실행을 보장</span>하는 반복문입니다. 조건 검사를 반복 코드 실행 후에 수행합니다.

### 기본 문법

```java
do {
    // 최소 1회 실행, 이후 조건이 true인 동안 반복
} while (조건식);
```

### 실행 흐름

```
1. 반복 코드 실행 (무조건 1회)
        ↓
2. 조건식 검사 ──(false)──→ 반복문 종료
        ↓ (true)
   1번으로 돌아감
```

### while 문과 do-while 문 비교

```java
// while: 조건이 처음부터 false면 한 번도 실행 안 됨
int i = 10;
while (i < 5) {
    System.out.println("while: " + i);
    i++;
}
// 출력 없음

// do-while: 조건이 false여도 최소 1회 실행
int j = 10;
do {
    System.out.println("do-while: " + j);
    j++;
} while (j < 5);
// 출력: do-while: 10
```

### do-while 기본 예제

```java
int count = 1;

do {
    System.out.println("반복 " + count);
    count++;
} while (count <= 3);
// 출력:
// 반복 1
// 반복 2
// 반복 3
```

### do-while 사용 케이스

메뉴 선택과 같이 최소 1회 실행이 필요한 경우에 유용합니다.

```java
int choice;

do {
    System.out.println("===== 메뉴 =====");
    System.out.println("1. 시작");
    System.out.println("2. 설정");
    System.out.println("0. 종료");
    System.out.print("선택: ");

    choice = 0;  // 실제로는 Scanner로 입력받음

    switch (choice) {
        case 1:
            System.out.println("시작합니다.");
            break;
        case 2:
            System.out.println("설정 화면입니다.");
            break;
        case 0:
            System.out.println("종료합니다.");
            break;
        default:
            System.out.println("잘못된 선택입니다.");
    }
} while (choice != 0);
```

---

## 중첩 반복문

반복문 안에 또 다른 반복문을 넣을 수 있습니다. 이를 <span class="blue-text">중첩 반복문</span>이라고 합니다.

### 기본 구조

```java
for (int i = 0; i < 외부횟수; i++) {
    for (int j = 0; j < 내부횟수; j++) {
        // 외부횟수 × 내부횟수 만큼 실행
    }
}
```

### 구구단 출력

```java
for (int dan = 2; dan <= 9; dan++) {
    System.out.println("===== " + dan + "단 =====");
    for (int i = 1; i <= 9; i++) {
        System.out.println(dan + " × " + i + " = " + (dan * i));
    }
    System.out.println();
}
```

**출력 (일부):**

```
===== 2단 =====
2 × 1 = 2
2 × 2 = 4
...
2 × 9 = 18

===== 3단 =====
3 × 1 = 3
...
```

### 별 찍기: 직각 삼각형

```java
for (int i = 1; i <= 5; i++) {
    for (int j = 1; j <= i; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

**출력:**

```
*
**
***
****
*****
```

### 별 찍기: 역삼각형

```java
for (int i = 5; i >= 1; i--) {
    for (int j = 1; j <= i; j++) {
        System.out.print("*");
    }
    System.out.println();
}
```

**출력:**

```
*****
****
***
**
*
```

### 별 찍기: 피라미드

```java
int height = 5;

for (int i = 1; i <= height; i++) {
    // 공백 출력
    for (int j = 1; j <= height - i; j++) {
        System.out.print(" ");
    }
    // 별 출력
    for (int k = 1; k <= 2 * i - 1; k++) {
        System.out.print("*");
    }
    System.out.println();
}
```

**출력:**

```
    *
   ***
  *****
 *******
*********
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">중첩 반복문 실행 횟수</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
외부 반복이 n번, 내부 반복이 m번이면 총 <span class="blue-text">n × m번</span> 실행됩니다. 중첩이 깊어지면 실행 횟수가 기하급수적으로 증가하므로 주의하세요.
</p>
</div>

---

## break와 continue

### break

<span class="yellow-code">break</span>는 반복문을 <span class="red-text">즉시 종료</span>합니다.

```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break;  // i가 5일 때 반복문 종료
    }
    System.out.print(i + " ");
}
// 출력: 1 2 3 4
```

### continue

<span class="yellow-code">continue</span>는 현재 반복을 <span class="green-text">건너뛰고</span> 다음 반복으로 넘어갑니다.

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue;  // i가 3일 때 건너뛰기
    }
    System.out.print(i + " ");
}
// 출력: 1 2 4 5
```

### break vs continue 비교

```java
System.out.println("=== break ===");
for (int i = 1; i <= 5; i++) {
    if (i == 3) break;
    System.out.print(i + " ");
}
// 출력: 1 2

System.out.println("\n=== continue ===");
for (int i = 1; i <= 5; i++) {
    if (i == 3) continue;
    System.out.print(i + " ");
}
// 출력: 1 2 4 5
```

### 특정 값 찾기 (break 활용)

```java
int[] numbers = {10, 25, 30, 45, 50};
int target = 30;
boolean found = false;

for (int i = 0; i < numbers.length; i++) {
    if (numbers[i] == target) {
        System.out.println(target + "을 인덱스 " + i + "에서 찾았습니다.");
        found = true;
        break;
    }
}

if (!found) {
    System.out.println(target + "을 찾지 못했습니다.");
}
// 출력: 30을 인덱스 2에서 찾았습니다.
```

### 홀수만 출력 (continue 활용)

```java
for (int i = 1; i <= 10; i++) {
    if (i % 2 == 0) {
        continue;  // 짝수는 건너뛰기
    }
    System.out.print(i + " ");
}
// 출력: 1 3 5 7 9
```

### 레이블을 이용한 중첩 반복문 제어

중첩 반복문에서 외부 반복문을 제어하려면 <span class="blue-text">레이블(label)</span>을 사용합니다.

```java
outer:  // 레이블 선언
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        if (i == 2 && j == 2) {
            break outer;  // 외부 반복문까지 종료
        }
        System.out.println("i=" + i + ", j=" + j);
    }
}
```

**출력:**

```
i=1, j=1
i=1, j=2
i=1, j=3
i=2, j=1
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">레이블 사용 주의</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
레이블은 코드의 가독성을 떨어뜨릴 수 있으므로, 꼭 필요한 경우에만 사용하세요. 대부분의 경우 메서드 분리나 플래그 변수로 대체할 수 있습니다.
</p>
</div>

---

## 무한 루프

조건이 항상 참이면 반복문이 끝나지 않는 <span class="red-text">무한 루프</span>가 됩니다.

### for 무한 루프

```java
for (;;) {
    System.out.println("무한 반복");
    // break 없으면 영원히 반복
}
```

### while 무한 루프

```java
while (true) {
    System.out.println("무한 반복");
    // break 없으면 영원히 반복
}
```

### 무한 루프 활용 예제

```java
int count = 0;

while (true) {
    count++;
    System.out.println("반복 " + count);

    if (count >= 5) {
        System.out.println("종료!");
        break;
    }
}
// 출력:
// 반복 1
// 반복 2
// 반복 3
// 반복 4
// 반복 5
// 종료!
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">무한 루프 주의사항</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
무한 루프는 반드시 <span class="green-text">탈출 조건(break)</span>이 있어야 합니다. 탈출 조건이 없으면 프로그램이 멈추지 않으므로 강제 종료(Ctrl+C)가 필요합니다.
</p>
</div>

---

## 종합 실습

### 문제 1 - for 문 기초 (기초)

<div class="quiz-number">문제 1</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 1; i <= 5; i++) {
            sum += i;
        }
        System.out.println(sum);
    }
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

### 문제 2 - while 문 기초 (기초)

<div class="quiz-number">문제 2</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int i = 3;
        while (i > 0) {
            System.out.print(i + " ");
            i--;
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="3 2 1 |3 2 1"
   tags="반복문"
%}

---

### 문제 3 - do-while 문 (기초)

<div class="quiz-number">문제 3</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int num = 5;
        do {
            System.out.print(num + " ");
            num--;
        } while (num > 2);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="5 4 3 |5 4 3"
   tags="반복문"
%}

---

### 문제 4 - 중첩 for 문 (중급)

<div class="quiz-number">문제 4</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int count = 0;
        for (int i = 1; i <= 3; i++) {
            for (int j = 1; j <= 2; j++) {
                count++;
            }
        }
        System.out.println(count);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="6"
   tags="반복문"
%}

---

### 문제 5 - break 활용 (중급)

<div class="quiz-number">문제 5</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 1; i <= 10; i++) {
            sum += i;
            if (sum > 10) {
                break;
            }
        }
        System.out.println(sum);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   code_html=code_block5
   answer="15"
   tags="반복문"
%}

---

### 문제 6 - continue 활용 (중급)

<div class="quiz-number">문제 6</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 1; i <= 10; i++) {
            if (i % 2 == 0) {
                continue;
            }
            sum += i;
        }
        System.out.println(sum);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   code_html=code_block6
   answer="25"
   tags="반복문"
%}

---

### 문제 7 - 복합 반복문 (고급)

<div class="quiz-number">문제 7</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int result = 1;
        for (int i = 1; i <= 4; i++) {
            result *= i;
        }
        System.out.println(result);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7"
   code_html=code_block7
   answer="24"
   tags="반복문"
%}

---

### 문제 8 - 중첩 반복문과 break (고급)

<div class="quiz-number">문제 8</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까? (공백으로 구분하여 답하세요)</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        for (int i = 1; i <= 3; i++) {
            for (int j = 1; j <= 3; j++) {
                if (j == 2) break;
                System.out.print(i + "" + j + " ");
            }
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8"
   code_html=code_block8
   answer="11 21 31 |11 21 31"
   tags="반복문"
%}

---

## 실전 프로그래밍

### 과제 1: 팩토리얼 계산기

주어진 숫자의 팩토리얼을 계산하는 프로그램을 작성하세요.

**요구사항:**
- 정수 n을 변수에 저장 (예: 5)
- n! = n × (n-1) × (n-2) × ... × 2 × 1 계산
- 결과 출력

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">public class Factorial {
    public static void main(String[] args) {
        int n = 5;
        long factorial = 1;

        for (int i = 1; i <= n; i++) {
            factorial *= i;
        }

        System.out.println(n + "! = " + factorial);
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>5! = 120
</code></pre>

</details>

---

### 과제 2: 소수 판별기

1부터 100까지의 숫자 중 소수(Prime Number)를 모두 출력하는 프로그램을 작성하세요.

**요구사항:**
- 소수: 1과 자기 자신으로만 나누어지는 수 (1 제외)
- 1부터 100까지 검사
- 소수만 출력

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">public class PrimeNumbers {
    public static void main(String[] args) {
        System.out.println("1부터 100까지의 소수:");

        for (int num = 2; num <= 100; num++) {
            boolean isPrime = true;

            for (int i = 2; i <= Math.sqrt(num); i++) {
                if (num % i == 0) {
                    isPrime = false;
                    break;
                }
            }

            if (isPrime) {
                System.out.print(num + " ");
            }
        }
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>1부터 100까지의 소수:
2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97
</code></pre>

</details>

---

### 과제 3: 별 다이아몬드 출력

높이가 주어졌을 때 다이아몬드 모양을 출력하는 프로그램을 작성하세요.

**요구사항:**
- 높이 변수 선언 (예: 5)
- 위쪽 삼각형과 아래쪽 역삼각형 결합
- 공백과 별을 적절히 배치

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">public class Diamond {
    public static void main(String[] args) {
        int height = 5;

        // 위쪽 삼각형
        for (int i = 1; i <= height; i++) {
            // 공백 출력
            for (int j = 1; j <= height - i; j++) {
                System.out.print(" ");
            }
            // 별 출력
            for (int k = 1; k <= 2 * i - 1; k++) {
                System.out.print("*");
            }
            System.out.println();
        }

        // 아래쪽 역삼각형
        for (int i = height - 1; i >= 1; i--) {
            // 공백 출력
            for (int j = 1; j <= height - i; j++) {
                System.out.print(" ");
            }
            // 별 출력
            for (int k = 1; k <= 2 * i - 1; k++) {
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>    *
   ***
  *****
 *******
*********
 *******
  *****
   ***
    *
</code></pre>

</details>

---

## 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 16px;">
<span style="font-size: 1.25rem;">✅</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">이번 챕터에서 배운 내용</h3>
</div>

<ol style="margin: 0; padding-left: 20px; color: #4b5563;">
<li style="margin-bottom: 12px;"><strong>for 문</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">for (초기화; 조건식; 증감식) {
    // 반복 코드
}
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>while 문</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">while (조건식) {
    // 조건이 true인 동안 반복
}
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>do-while 문</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">do {
    // 최소 1회 실행
} while (조건식);
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>반복문 비교</strong>
   <table style="margin-top: 8px; margin-bottom: 0; width: 100%; border-collapse: collapse;">
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <th style="padding: 8px; text-align: left;">구분</th>
   <th style="padding: 8px; text-align: left;">특징</th>
   <th style="padding: 8px; text-align: left;">사용 시점</th>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;">for</td>
   <td style="padding: 8px;">초기화/조건/증감 한 곳에</td>
   <td style="padding: 8px;">반복 횟수 명확</td>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;">while</td>
   <td style="padding: 8px;">조건만 검사</td>
   <td style="padding: 8px;">횟수 불명확</td>
   </tr>
   <tr>
   <td style="padding: 8px;">do-while</td>
   <td style="padding: 8px;">최소 1회 실행</td>
   <td style="padding: 8px;">1회 이상 보장</td>
   </tr>
   </table>
</li>
<li style="margin-bottom: 12px;"><strong>break와 continue</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">break;     // 반복문 즉시 종료
continue;  // 현재 반복 건너뛰기
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>중첩 반복문</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">for (외부) {
    for (내부) {
        // 외부 × 내부 횟수만큼 실행
    }
}
</code></pre>
</li>
<li style="margin-bottom: 0;"><strong>주요 포인트</strong>
   <ul style="margin-top: 8px; margin-bottom: 0;">
   <li>for 문 변수는 블록 내에서만 유효</li>
   <li>while 문은 조건 검사 후 실행</li>
   <li>do-while 문은 실행 후 조건 검사</li>
   <li>무한 루프는 반드시 탈출 조건 필요</li>
   <li>레이블은 가독성을 고려해 신중히 사용</li>
   </ul>
</li>
</ol>

</div>

---

## 다음 챕터 예고

다음 챕터에서는 **배열 (Array)**을 배웁니다.

- 배열이란?
- 1차원 배열
- 다차원 배열
- 배열과 반복문
- 향상된 for 문 (for-each)
- Arrays 클래스 활용

---

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04); text-align: center;">
<div style="display: flex; align-items: center; justify-content: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">🎯</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">반복문 학습 완료!</h3>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
반복문을 통해 같은 작업을 효율적으로 처리하는 방법을 배웠습니다.<br>
이제 배열을 배우면 여러 데이터를 체계적으로 관리할 수 있습니다!
</p>
</div>
