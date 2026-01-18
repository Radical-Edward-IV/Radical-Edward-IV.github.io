---
layout: article
title: 3. 조건문과 제어 흐름
permalink: /notes/kr/java-basic/chapter-03
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: Java 기초 과정 강의 노트, 조건문(if, if-else, if-else if-else, switch), 중첩 조건문, 삼항 연산자를 통한 제어 흐름을 다룹니다.
keywords: "Java, 조건문, if, else, else if, switch, 삼항연산자, 제어문, 분기문, case, break, default"
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

## 조건문이란?

프로그램은 **조건에 따라 다른 동작**을 수행해야 할 때가 많습니다. 조건문은 프로그램의 실행 흐름을 제어하는 가장 기본적인 도구입니다.

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">일상 속 조건문</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
"<strong>만약</strong> 비가 오면 우산을 챙긴다, <strong>그렇지 않으면</strong> 우산을 챙기지 않는다"<br>
이런 일상의 논리를 프로그램으로 표현한 것이 바로 조건문입니다.
</p>
</div>

### 조건문의 종류

Java에서 제공하는 조건문은 다음과 같습니다:

| 조건문 | 용도 |
|--------|------|
| `if` | 조건이 참일 때만 실행 |
| `if-else` | 조건이 참/거짓일 때 각각 다른 코드 실행 |
| `if-else if-else` | 여러 조건을 순차적으로 검사 |
| `switch` | 값에 따라 여러 경우의 수 중 하나 선택 |
| 삼항 연산자 | 간단한 조건문을 한 줄로 표현 |

---

## if 문

<span class="blue-text">if 문</span>은 가장 기본적인 조건문으로, 조건이 참(true)일 때만 코드를 실행합니다.

### 기본 문법

```java
if (조건식) {
    // 조건이 true일 때 실행되는 코드
}
```

### 단일 if 문 예제

```java
int age = 20;

if (age >= 18) {
    System.out.println("성인입니다.");
}
// 출력: 성인입니다.
```

```java
int score = 85;

if (score >= 90) {
    System.out.println("A학점입니다.");
}
// 출력 없음 (조건이 false)
```

### 중괄호 생략

조건문 안에 **문장이 하나만** 있으면 중괄호를 생략할 수 있습니다.

```java
int num = 10;

// 중괄호 있음
if (num > 0) {
    System.out.println("양수입니다.");
}

// 중괄호 생략 (권장하지 않음)
if (num > 0)
    System.out.println("양수입니다.");
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">중괄호 생략 주의</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
문장이 하나만 있어도 <span class="green-text">중괄호를 사용하는 것을 권장</span>합니다. 나중에 코드를 추가할 때 실수를 방지할 수 있습니다.
</p>
</div>

---

## if-else 문

<span class="blue-text">if-else 문</span>은 조건이 참일 때와 거짓일 때 각각 다른 코드를 실행합니다.

### 기본 문법

```java
if (조건식) {
    // 조건이 true일 때 실행
} else {
    // 조건이 false일 때 실행
}
```

### if-else 예제

```java
int age = 15;

if (age >= 18) {
    System.out.println("성인입니다.");
} else {
    System.out.println("미성년자입니다.");
}
// 출력: 미성년자입니다.
```

```java
int number = -5;

if (number >= 0) {
    System.out.println("양수입니다.");
} else {
    System.out.println("음수입니다.");
}
// 출력: 음수입니다.
```

### 실습: 짝수/홀수 판별

```java
public class EvenOddTest {
    public static void main(String[] args) {
        int number = 17;

        if (number % 2 == 0) {
            System.out.println(number + "는 짝수입니다.");
        } else {
            System.out.println(number + "는 홀수입니다.");
        }
    }
}
// 출력: 17는 홀수입니다.
```

---

## if-else if-else 문

여러 조건을 순차적으로 검사할 때 사용합니다.

### 기본 문법

```java
if (조건1) {
    // 조건1이 true일 때 실행
} else if (조건2) {
    // 조건1이 false이고 조건2가 true일 때 실행
} else if (조건3) {
    // 조건1, 조건2가 false이고 조건3이 true일 때 실행
} else {
    // 모든 조건이 false일 때 실행
}
```

### 성적 등급 판별

```java
int score = 85;
String grade;

if (score >= 90) {
    grade = "A";
} else if (score >= 80) {
    grade = "B";
} else if (score >= 70) {
    grade = "C";
} else if (score >= 60) {
    grade = "D";
} else {
    grade = "F";
}

System.out.println("학점: " + grade);
// 출력: 학점: B
```

### 시간대에 따른 인사말

```java
int hour = 14;  // 오후 2시
String greeting;

if (hour < 12) {
    greeting = "좋은 아침입니다!";
} else if (hour < 18) {
    greeting = "좋은 오후입니다!";
} else {
    greeting = "좋은 저녁입니다!";
}

System.out.println(greeting);
// 출력: 좋은 오후입니다!
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">조건 검사 순서</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
if-else if-else 문은 <span class="blue-text">위에서 아래로 순차적으로 검사</span>하며, 조건이 참인 블록을 실행한 후 나머지는 건너뜁니다.
</p>
</div>

---

## 중첩 if 문

if 문 안에 또 다른 if 문을 넣을 수 있습니다.

### 기본 문법

```java
if (조건1) {
    if (조건2) {
        // 조건1과 조건2 모두 true일 때 실행
    }
}
```

### 중첩 if 예제

```java
int age = 25;
boolean hasLicense = true;

if (age >= 18) {
    if (hasLicense) {
        System.out.println("운전할 수 있습니다.");
    } else {
        System.out.println("면허증이 필요합니다.");
    }
} else {
    System.out.println("나이가 부족합니다.");
}
// 출력: 운전할 수 있습니다.
```

### 학점 세부 판정

```java
int score = 95;
String grade;

if (score >= 90) {
    if (score >= 95) {
        grade = "A+";
    } else {
        grade = "A";
    }
} else if (score >= 80) {
    if (score >= 85) {
        grade = "B+";
    } else {
        grade = "B";
    }
} else {
    grade = "C";
}

System.out.println("학점: " + grade);
// 출력: 학점: A+
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">중첩 if 문 대안</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
중첩이 깊어지면 코드가 복잡해집니다. 논리 연산자(<code>&&</code>)를 사용하면 더 간결하게 표현할 수 있습니다.
</p>
</div>

**논리 연산자로 개선:**

```java
int age = 25;
boolean hasLicense = true;

if (age >= 18 && hasLicense) {
    System.out.println("운전할 수 있습니다.");
} else if (age >= 18) {
    System.out.println("면허증이 필요합니다.");
} else {
    System.out.println("나이가 부족합니다.");
}
```

---

## switch 문

<span class="blue-text">switch 문</span>은 변수의 값에 따라 여러 경우 중 하나를 선택하여 실행합니다.

### 기본 문법

```java
switch (변수) {
    case 값1:
        // 변수가 값1과 같을 때 실행
        break;
    case 값2:
        // 변수가 값2와 같을 때 실행
        break;
    default:
        // 모든 case에 해당하지 않을 때 실행
        break;
}
```

### switch 문 기본 예제

```java
int day = 3;
String dayName;

switch (day) {
    case 1:
        dayName = "월요일";
        break;
    case 2:
        dayName = "화요일";
        break;
    case 3:
        dayName = "수요일";
        break;
    case 4:
        dayName = "목요일";
        break;
    case 5:
        dayName = "금요일";
        break;
    case 6:
        dayName = "토요일";
        break;
    case 7:
        dayName = "일요일";
        break;
    default:
        dayName = "잘못된 요일";
        break;
}

System.out.println(dayName);
// 출력: 수요일
```

### break의 중요성

<span class="yellow-code">break</span>를 생략하면 다음 case로 계속 실행됩니다 (Fall-through).

```java
int month = 3;
String season;

switch (month) {
    case 12:
    case 1:
    case 2:
        season = "겨울";
        break;
    case 3:
    case 4:
    case 5:
        season = "봄";
        break;
    case 6:
    case 7:
    case 8:
        season = "여름";
        break;
    case 9:
    case 10:
    case 11:
        season = "가을";
        break;
    default:
        season = "잘못된 월";
        break;
}

System.out.println(season);
// 출력: 봄
```

### switch 문 vs if-else

**switch 문 사용 가능 조건:**
- 변수가 정수형(`byte`, `short`, `int`, `char`)
- 문자열(`String`) - Java 7 이상
- 열거형(`enum`)

**사용할 수 없는 경우:**
- 실수형(`float`, `double`)
- 범위 비교(`>=`, `<=` 등)

```java
// ✅ switch 사용 가능
String grade = "A";
switch (grade) {
    case "A":
        System.out.println("우수");
        break;
    case "B":
        System.out.println("양호");
        break;
    default:
        System.out.println("보통");
        break;
}

// ❌ switch 사용 불가 (범위 비교)
int score = 85;
// switch (score >= 90) { ... }  // 오류!

// ✅ if-else 사용
if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");
}
```

### Java 14+ Enhanced Switch (참고)

Java 14 이후에는 화살표(`->`) 문법을 사용할 수 있습니다.

```java
int day = 3;
String dayName = switch (day) {
    case 1 -> "월요일";
    case 2 -> "화요일";
    case 3 -> "수요일";
    case 4 -> "목요일";
    case 5 -> "금요일";
    case 6 -> "토요일";
    case 7 -> "일요일";
    default -> "잘못된 요일";
};

System.out.println(dayName);
// 출력: 수요일
```

---

## 삼항 연산자

<span class="blue-text">삼항 연산자</span>는 간단한 if-else 문을 한 줄로 표현할 수 있는 연산자입니다.

### 기본 문법

```java
조건식 ? 값1 : 값2
```

- 조건식이 `true`이면 `값1` 반환
- 조건식이 `false`이면 `값2` 반환

### 삼항 연산자 예제

```java
int age = 20;
String result = (age >= 18) ? "성인" : "미성년자";
System.out.println(result);
// 출력: 성인
```

```java
int a = 10, b = 20;
int max = (a > b) ? a : b;
System.out.println("최댓값: " + max);
// 출력: 최댓값: 20
```

### if-else 문과 비교

**if-else 문:**

```java
int score = 85;
String result;

if (score >= 60) {
    result = "합격";
} else {
    result = "불합격";
}
```

**삼항 연산자:**

```java
int score = 85;
String result = (score >= 60) ? "합격" : "불합격";
```

### 중첩 삼항 연산자

삼항 연산자를 중첩해서 사용할 수 있지만, 가독성이 떨어질 수 있습니다.

```java
int score = 85;
String grade = (score >= 90) ? "A" :
               (score >= 80) ? "B" :
               (score >= 70) ? "C" : "F";
System.out.println(grade);
// 출력: B
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">삼항 연산자 사용 팁</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• 간단한 조건문은 삼항 연산자로 표현하면 코드가 간결해집니다.<br>
• 복잡한 조건이나 여러 문장이 필요한 경우 if-else 문을 사용하세요.<br>
• 중첩 삼항 연산자는 가독성이 떨어지므로 주의하세요.
</p>
</div>

---

## 종합 실습

### 문제 1 - if 문 기초 (기초)

<div class="quiz-number">문제 1</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int number = 15;
        if (number > 10) {
            System.out.println("10보다 큽니다.");
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="10보다 큽니다."
   tags="조건문"
%}

---

### 문제 2 - if-else 문 (기초)

<div class="quiz-number">문제 2</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int age = 16;
        if (age >= 18) {
            System.out.println("성인");
        } else {
            System.out.println("미성년자");
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="미성년자"
   tags="조건문"
%}

---

### 문제 3 - if-else if-else (기초)

<div class="quiz-number">문제 3</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int score = 75;
        if (score >= 90) {
            System.out.println("A");
        } else if (score >= 80) {
            System.out.println("B");
        } else if (score >= 70) {
            System.out.println("C");
        } else {
            System.out.println("D");
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="C"
   tags="조건문"
%}

---

### 문제 4 - switch 문 (중급)

<div class="quiz-number">문제 4</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int month = 8;
        String season;
        switch (month) {
            case 3: case 4: case 5:
                season = "봄";
                break;
            case 6: case 7: case 8:
                season = "여름";
                break;
            case 9: case 10: case 11:
                season = "가을";
                break;
            default:
                season = "겨울";
                break;
        }
        System.out.println(season);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="여름"
   tags="조건문"
%}

---

### 문제 5 - 삼항 연산자 (중급)

<div class="quiz-number">문제 5</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int num = 7;
        String result = (num % 2 == 0) ? "짝수" : "홀수";
        System.out.println(result);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   code_html=code_block5
   answer="홀수"
   tags="조건문"
%}

---

### 문제 6 - 중첩 if 문 (중급)

<div class="quiz-number">문제 6</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int score = 92;
        if (score >= 90) {
            if (score >= 95) {
                System.out.println("A+");
            } else {
                System.out.println("A");
            }
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   code_html=code_block6
   answer="A"
   tags="조건문"
%}

---

### 문제 7 - break 없는 switch (고급)

<div class="quiz-number">문제 7</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까? (줄바꿈 포함)</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int num = 2;
        switch (num) {
            case 1:
                System.out.println("one");
            case 2:
                System.out.println("two");
            case 3:
                System.out.println("three");
                break;
            default:
                System.out.println("other");
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7"
   code_html=code_block7
   answer="two\nthree|two three"
   tags="조건문"
%}

---

### 문제 8 - 복합 조건 (고급)

<div class="quiz-number">문제 8</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int x = 10;
        int y = 20;
        String result = (x > 5 && y < 30) ? "조건1" :
                        (x > 15 || y > 15) ? "조건2" : "조건3";
        System.out.println(result);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8"
   code_html=code_block8
   answer="조건1"
   tags="조건문"
%}

---

## 실전 프로그래밍

### 과제 1: BMI 계산기

체질량 지수(BMI)를 계산하고 비만도를 판정하는 프로그램을 작성하세요.

**요구사항:**
- 몸무게(kg)와 키(m)를 변수에 저장
- BMI = 몸무게 / (키 * 키)
- BMI에 따른 판정:
  - 18.5 미만: 저체중
  - 18.5 이상 25 미만: 정상
  - 25 이상 30 미만: 과체중
  - 30 이상: 비만

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">public class BMICalculator {
    public static void main(String[] args) {
        double weight = 70.0;  // kg
        double height = 1.75;  // m

        double bmi = weight / (height * height);
        String status;

        if (bmi < 18.5) {
            status = "저체중";
        } else if (bmi < 25) {
            status = "정상";
        } else if (bmi < 30) {
            status = "과체중";
        } else {
            status = "비만";
        }

        System.out.printf("BMI: %.2f\n", bmi);
        System.out.println("판정: " + status);
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>BMI: 22.86
판정: 정상
</code></pre>

</details>

---

### 과제 2: 계산기 프로그램

두 숫자와 연산자를 입력받아 계산하는 간단한 계산기 프로그램을 작성하세요.

**요구사항:**
- 두 개의 정수 변수 선언 (예: 10, 5)
- 연산자 변수 선언 ('+', '-', '*', '/', '%')
- switch 문을 사용하여 연산 수행
- 결과 출력

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">public class Calculator {
    public static void main(String[] args) {
        int num1 = 10;
        int num2 = 5;
        char operator = '*';
        int result;

        switch (operator) {
            case '+':
                result = num1 + num2;
                break;
            case '-':
                result = num1 - num2;
                break;
            case '*':
                result = num1 * num2;
                break;
            case '/':
                result = num1 / num2;
                break;
            case '%':
                result = num1 % num2;
                break;
            default:
                System.out.println("잘못된 연산자입니다.");
                return;
        }

        System.out.printf("%d %c %d = %d\n", num1, operator, num2, result);
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>10 * 5 = 50
</code></pre>

</details>

---

### 과제 3: 학점 세부 판정 시스템

점수를 입력받아 학점과 세부 등급(+, 0)을 판정하는 프로그램을 작성하세요.

**요구사항:**
- 0~100 점수를 변수에 저장
- 학점 판정:
  - 90 이상: A
  - 80 이상: B
  - 70 이상: C
  - 60 이상: D
  - 60 미만: F
- 각 구간에서 상위 50%는 +, 하위 50%는 0 (F 제외)
  - 예: 95점 이상은 A+, 90~94는 A

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">public class GradeSystem {
    public static void main(String[] args) {
        int score = 87;
        String grade;

        if (score >= 90) {
            grade = (score >= 95) ? "A+" : "A";
        } else if (score >= 80) {
            grade = (score >= 85) ? "B+" : "B";
        } else if (score >= 70) {
            grade = (score >= 75) ? "C+" : "C";
        } else if (score >= 60) {
            grade = (score >= 65) ? "D+" : "D";
        } else {
            grade = "F";
        }

        System.out.println("점수: " + score);
        System.out.println("학점: " + grade);
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>점수: 87
학점: B+
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
<li style="margin-bottom: 12px;"><strong>if 문</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">if (조건) {
    // 조건이 true일 때 실행
}
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>if-else 문</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">if (조건) {
    // true일 때
} else {
    // false일 때
}
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>if-else if-else 문</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">if (조건1) {
    // 조건1 true
} else if (조건2) {
    // 조건2 true
} else {
    // 모두 false
}
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>switch 문</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">switch (변수) {
    case 값1:
        // 실행 코드
        break;
    case 값2:
        // 실행 코드
        break;
    default:
        // 기본 코드
        break;
}
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>삼항 연산자</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">조건 ? 값1 : 값2
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>주요 포인트</strong>
   <table style="margin-top: 8px; margin-bottom: 0; width: 100%; border-collapse: collapse;">
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <th style="padding: 8px; text-align: left;">구분</th>
   <th style="padding: 8px; text-align: left;">용도</th>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;">if 계열</td>
   <td style="padding: 8px;">범위 비교, 복잡한 조건</td>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;">switch</td>
   <td style="padding: 8px;">값의 일치 비교 (정수, 문자열, enum)</td>
   </tr>
   <tr>
   <td style="padding: 8px;">삼항 연산자</td>
   <td style="padding: 8px;">간단한 조건, 값 할당</td>
   </tr>
   </table>
</li>
<li style="margin-bottom: 0;"><strong>중요 사항</strong>
   <ul style="margin-top: 8px; margin-bottom: 0;">
   <li>switch 문에서 <code>break</code>를 빠뜨리면 Fall-through 발생</li>
   <li>중괄호 생략은 권장하지 않음</li>
   <li>중첩이 깊어지면 논리 연산자 사용 고려</li>
   <li>삼항 연산자는 간단한 경우에만 사용</li>
   </ul>
</li>
</ol>

</div>

---

## 다음 챕터 예고

다음 챕터에서는 **반복문**을 배웁니다.

- for 문
- while 문
- do-while 문
- 중첩 반복문
- break와 continue
- 무한 루프

---

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04); text-align: center;">
<div style="display: flex; align-items: center; justify-content: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">🎯</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">조건문 학습 완료!</h3>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
조건에 따라 프로그램의 흐름을 제어하는 방법을 배웠습니다.<br>
이제 반복문을 배우면 더욱 강력한 프로그램을 만들 수 있습니다!
</p>
</div>
