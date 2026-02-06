---
layout: article
title: 4. Python과 예외처리
permalink: /notes/kr/info-processing-technician/chapter-05
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - Python의 기본 문법, 리스트/세트/슬라이스/람다 식 활용과 Java/Python의 예외처리를 학습합니다.
keywords: "프로그래밍기능사, Python, 리스트, 세트, 슬라이스, Range, 람다, 예외처리, try-catch"
---

<script src="/assets/js/quiz.js"></script>

<style>
    .quiz-container {
        margin: 20px 0;
        padding: 15px;
        border: 1px solid #e5e7eb;
        border-radius: 12px;
        background-color: #ffffff;
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
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EA%B8%B0%EB%8A%A5%EC%82%AC&reversal=false&textBg=false)

---

# PART 1. Python의 활용 1

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">전문가의 조언</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Python에서도 Java와 마찬가지로 기본적인 문법은 생략하고 바로 소스코드를 통해 코드를 읽고 해석하는 방법을 학습합니다. 본문에 수록된 내용은 Java를 충분히 학습하였다는 전제하에 진행되므로, 어려움을 느끼는 수험생들은 앞의 Java 섹션을 먼저 공부한 후 학습을 진행하는 것이 좋습니다.
</p>
</div>

## 1.1 Python의 개요

Python은 객체지향 기능을 지원하는 스크립트 언어로, 다른 언어에 비해 문법이 간단하다는 장점이 있습니다.

**Java와의 기본 작성법 차이점**

| 구분 | Python | Java |
|------|--------|------|
| 자료형 선언 | 불필요 | 필요 |
| 문자/문자열 | `''`, `""`, `'''`, `"""` 모두 사용 가능 | 문자: `''`, 문자열: `""` |
| 문장 끝 | 세미콜론(;) 불필요 | 세미콜론(;) 필수 |
| 코드 블록 | 콜론(`:`)과 들여쓰기로 구분 | 중괄호(`{}`)로 구분 |

**이번 섹션에서 배울 내용**
- 자료형: 리스트(List), 세트(Set)
- 입출력 함수: `input`, `print`
- 슬라이스(Slice)
- Range

---

## 1.2 Range와 슬라이스 정리

### Range

연속된 숫자를 생성하는 함수로, 리스트 반복문에서 자주 사용됩니다.

| 형식 | 설명 | 예시 |
|------|------|------|
| `range(최종값)` | 0부터 최종값-1까지 | `range(5)` → 0, 1, 2, 3, 4 |
| `range(초기값, 최종값)` | 초기값부터 최종값-1까지 | `range(2, 5)` → 2, 3, 4 |
| `range(초기값, 최종값, 증가값)` | 증가값만큼 증감 | `range(1, 10, 2)` → 1, 3, 5, 7, 9 |

### 슬라이스(Slice)

문자열이나 리스트와 같은 순차형 객체에서 일부를 잘라 반환합니다.

| 형식 | 설명 |
|------|------|
| `객체명[:]` | 전체 |
| `객체명[:3]` | 처음부터 인덱스 2까지 |
| `객체명[3:]` | 인덱스 3부터 끝까지 |
| `객체명[1:5]` | 인덱스 1부터 4까지 |
| `객체명[::-1]` | 역순 |
| `객체명[::2]` | 2칸씩 건너뛰며 |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">슬라이스 핵심 포인트</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• 최종위치는 <span class="red-text">포함되지 않음</span><br>
• 음수 인덱스 사용 가능 (-1은 마지막 요소)<br>
• 인덱스 생략 가능
</p>
</div>

---

# PART 2. Python의 활용 2

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
람다 식과 클래스를 활용한 Python 프로그램의 코드 해석 능력을 기릅니다.
</p>
</div>

## 2.1 람다 식 (Lambda Expression)

<span class="blue-text">람다 식</span>은 어떤 문제를 해결하기 위한 과정을 수학식으로 표현한 것입니다. 프로그래밍에서는 수학적 연산을 수행하는 함수를 간소화할 때 사용합니다.

**기본 형식:**
```python
lambda 변수명 : 수학식
```

**일반 함수와 람다 식 비교:**

```python
# 일반 함수
def func(x):
    return x * x - 3
print(func(10))  # 결과: 97

# 람다 식
func = lambda x : x * x - 3
print(func(10))  # 결과: 97
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">Python의 매개변수 전달</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Python에서 함수에 전달된 매개변수는 함수 내부에서만 유효합니다. 따라서 함수 내에서 매개변수를 변경해도 원본 변수는 영향받지 않습니다.
</p>
</div>

---

# PART 3. 예외 처리

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
예외 처리는 프로그램 실행 중 발생할 수 있는 오류에 대비하는 중요한 기법입니다. Java의 try-catch 구문과 주요 예외 객체를 정확히 이해하세요.
</p>
</div>

## 3.1 예외 처리의 개념

<span class="blue-text">예외 처리(Exception Handling)</span>는 예외가 발생했을 때 프로그램에 해당 문제에 대비해 작성해 놓은 처리 루틴이 수행되도록 하는 것입니다.

**예외 처리의 일반적인 동작:**
- 프로그램을 종료시키거나
- 로그(Log)를 남기는 것

**대표적인 예외 발생 원인:**

| 원인 | 설명 |
|------|------|
| 컴퓨터 하드웨어 문제 | 메모리 부족, 디스크 오류 등 |
| 운영체제 설정 실수 | 잘못된 환경 변수 등 |
| 라이브러리 손상 | 의존성 파일 손상 |
| 사용자 입력 실수 | 잘못된 형식의 입력 |
| 받아들일 수 없는 연산 | 0으로 나누기 등 |
| 할당하지 못하는 기억장치 접근 | null 참조 등 |

---

## 3.2 Java의 예외 처리

Java는 예외를 <span class="blue-text">객체로 취급</span>하며, 예외와 관련된 클래스를 `java.lang` 패키지에서 제공합니다.

### try-catch 문의 기본 형식

```java
try {
    예외가 발생할 가능성이 있는 코드;
}
catch (예외객체1 매개변수) {
    예외객체1에 해당하는 예외 발생 시 처리 코드;
}
catch (예외객체2 매개변수) {
    예외객체2에 해당하는 예외 발생 시 처리 코드;
}
catch (Exception 매개변수) {
    위 예외에 해당하지 않는 예외 발생 시 처리 코드;
}
finally {
    예외 발생 여부와 관계없이 무조건 실행되는 코드;
}
```

### try-catch 문의 특징

- try 블록에서 예외 발생 시 catch 블록으로 이동
- 예외 발생 이후의 코드는 <span class="red-text">실행되지 않음</span>
- catch 블록의 변수는 해당 블록에서만 유효
- try-catch 문 중첩 가능
- 실행 코드가 한 줄이라도 <span class="red-text">중괄호 생략 불가</span>
- finally 블록은 <span class="green-text">항상 실행</span>됨

---

## 3.3 Java의 주요 예외 객체

| 예외 객체 | 발생 원인 |
|----------|----------|
| `ClassNotFoundException` | 클래스를 찾지 못한 경우 |
| `NoSuchMethodException` | 메소드를 찾지 못한 경우 |
| `FileNotFoundException` | 파일을 찾지 못한 경우 |
| `InterruptedIOException` | 입출력 처리가 중단된 경우 |
| `ArithmeticException` | 0으로 나누는 등의 산술 연산 예외 |
| `IllegalArgumentException` | 잘못된 인자를 전달한 경우 |
| `NumberFormatException` | 숫자로 변환할 수 없는 문자열을 숫자로 변환 |
| `ArrayIndexOutOfBoundsException` | 배열의 범위를 벗어난 접근 |
| `NegativeArraySizeException` | 0보다 작은 값으로 배열 크기 지정 |
| `NullPointerException` | 존재하지 않는 객체 참조 |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">예외 처리 실행 흐름</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
1. try 블록 실행<br>
2. 예외 발생 시 → 해당 catch 블록으로 이동<br>
3. finally 블록 실행 (예외 발생 여부와 무관)<br>
4. try-catch 문 이후 코드 계속 실행
</p>
</div>

---

# 연습문제

## Part 1 - Python의 활용 1

<div class="quiz-number">문제 1</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>animals = {'고양이', '강아지', '토끼'}
animals.add('햄스터')
animals.add('고양이')
animals.remove('토끼')
animals.update(('강아지', '앵무새', '거북이'))
print(animals)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_python"
   code_html=code_block1
   answer="{'고양이', '강아지', '햄스터', '앵무새', '거북이'}|{'햄스터', '거북이', '고양이', '앵무새', '강아지'}"
   tags="Python, Set"
%}

---

<div class="quiz-number">문제 2</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>m, n = 50, 75
print(m >= n)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_python"
   code_html=code_block2
   answer="False"
   tags="Python, 비교연산"
%}

---

<div class="quiz-number">문제 3</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오. (줄바꿈은 /로 구분)</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>matrix = [[10, 20], [30, 40, 50], [60]]

print(matrix[1])
print(matrix[1][2])

for row in matrix:
    for val in row:
        print(val, end=' ')
    print()</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_python"
   code_html=code_block3
   answer="[30, 40, 50]/50/10 20 /30 40 50 /60 |[30, 40, 50]/50/10 20/30 40 50/60"
   tags="Python, 2차원 리스트"
%}

---

<div class="quiz-number">문제 4</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>num = 64
output = 0

for k in range(1, 4):
    output = num >> k
    output = output + 2

print(output)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_python"
   code_html=code_block4
   answer="10"
   tags="Python, 비트연산"
%}

---

<div class="quiz-number">문제 5</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class DataHolder:
    items = ['Apple', 'Banana', 'Cherry',
             'Date', 'Elderberry']

obj = DataHolder()
result = ''

for fruit in obj.items:
    result = result + fruit[-1]

print(result)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_python"
   code_html=code_block5
   answer="eayey"
   tags="Python, 클래스"
%}

---

<div class="quiz-number">문제 6</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>msg = 'HELLO WORLD PYTHON'
part1 = msg[0:5] + msg[11:17]
part2 = ' IS %s' % 'FUN'
print(part1 + part2)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_python"
   code_html=code_block6
   answer="HELLO PYTHON IS FUN"
   tags="Python, 슬라이스"
%}

---

<div class="quiz-number">문제 7</div><strong>다음 Python 프로그램의 괄호에 들어갈 알맞은 메소드명을 작성하시오.</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>a, b = input('두 수를 쉼표로 구분하여 입력 : ').(      )(',')
print('첫 번째 값 :', a)
print('두 번째 값 :', b)

# 실행결과
# 두 수를 쉼표로 구분하여 입력 : 15,25
# 첫 번째 값 : 15
# 두 번째 값 : 25</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7_python"
   code_html=code_block7
   answer="split"
   tags="Python, 입력"
%}

---

## Part 2 - Python의 활용 2

<div class="quiz-number">문제 8</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def process(arr):
    for idx in range(len(arr) // 2):
        arr[idx], arr[-idx-1] = arr[-idx-1], arr[idx]

data = [10, 20, 30, 40, 50, 60, 70, 80]
process(data)
print(sum(data[::2]) - sum(data[1::2]))</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8_python"
   code_html=code_block8
   answer="40"
   tags="Python, 리스트"
%}

---

<div class="quiz-number">문제 9</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def check(item):
    if type(item) == type(50):
        return 50
    elif type(item) == type("hello"):
        return len(item)
    else:
        return 10

x = "python"
y = 3.14
z = [1, 2, 3]

print(check(x) + check(y) + check(z))</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_python"
   code_html=code_block9
   answer="26"
   tags="Python, 함수"
%}

---

## Part 3 - 예외 처리

<div class="quiz-number">문제 10</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block10 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int result = 0;
        try {
            execute();
        }
        catch (ArithmeticException e) {
            result = result + 5;
        }
        catch (Exception e) {
            result = result + 50;
        }
        finally {
            result = result + 200;
        }
        System.out.print(result);
    }

    static void execute() throws Exception {
        throw new ArithmeticException();
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz10_exception"
   code_html=code_block10
   answer="205"
   tags="예외처리, Java"
%}

---

<div class="quiz-number">문제 11</div><strong>다음 상황에 가장 적합한 Java 예외 객체를 &lt;보기&gt;에서 찾아 기호로 작성하시오. (①, ②, ③, ④ 순서대로 쉼표로 구분)</strong>

{% capture code_block11 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 정수를 0으로 나누려고 시도한 경우<br>
② 문자열 "ABC"를 정수로 변환하려고 시도한 경우<br>
③ 배열을 arr[5]로 선언한 후 arr[7]에 접근한 경우<br>
④ 초기화되지 않은 객체의 메소드를 호출한 경우<br><br>
<strong>&lt;보기&gt;</strong><br>
ㄱ ClassNotFoundException<br>
ㄴ NoSuchMethodException<br>
ㄷ FileNotFoundException<br>
ㄹ InterruptedIOException<br>
ㅁ ArithmeticException<br>
ㅂ IllegalArgumentException<br>
ㅅ NumberFormatException<br>
ㅇ ArrayIndexOutOfBoundsException<br>
ㅈ NegativeArraySizeException<br>
ㅋ NullPointerException
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_exception"
   code_html=code_block11
   answer="ㅁ, ㅅ, ㅇ, ㅋ|ㅁ,ㅅ,ㅇ,ㅋ"
   tags="예외처리, Java"
%}

---

# 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Part 1 - Python 기본</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>리스트</strong>: <code>append()</code>(추가), <code>remove()</code>(삭제), 인덱싱/슬라이싱</li>
<li><strong>세트</strong>: 중복 불허, <code>add()</code>(단일 추가), <code>update()</code>(여러 개 추가)</li>
<li><strong>Range</strong>: <code>range(최종)</code>, <code>range(초기, 최종)</code>, <code>range(초기, 최종, 증가)</code></li>
<li><strong>슬라이스</strong>: <code>[시작:끝]</code>, <code>[::-1]</code>(역순), 끝 인덱스는 포함 안 됨</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Part 2 - Python 활용</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>람다 식</strong>: <code>lambda 변수 : 수학식</code></li>
<li><strong>map 함수</strong>: <code>map(함수, 반복가능객체)</code> - 각 요소에 함수 적용</li>
<li><strong>클래스</strong>: <code>self</code>는 객체 자신을 참조</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Part 3 - 예외 처리</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>try-catch-finally</strong>: try에서 예외 발생 시 catch로 이동, finally는 항상 실행</li>
<li><strong>주요 예외</strong>: NullPointerException(null 참조), ArrayIndexOutOfBoundsException(배열 범위 초과), ArithmeticException(산술 오류)</li>
<li><strong>예외 던지기</strong>: <code>throw new 예외객체()</code></li>
</ul>

</div>

---
