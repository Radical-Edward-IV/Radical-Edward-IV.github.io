---
layout: article
title: 1. 라이브러리 및 객체지향
permalink: /notes/kr/info-processing-technician/chapter-02
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - 라이브러리의 개념과 Java/Python 표준 라이브러리, 객체지향 프로그래밍 언어의 특징과 종류를 학습합니다.
keywords: "프로그래밍기능사, 라이브러리, Java, Python, 객체지향, OOP, 표준 라이브러리"
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

## SECTION 01. 라이브러리

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Java와 Python은 패키지 형태로 라이브러리를 제공합니다. 주요 표준 라이브러리의 종류와 대표적인 메소드의 기능을 꼼꼼히 정리해 두세요.
</p>
</div>

### 1.1 라이브러리의 개념

<span class="blue-text">라이브러리(Library)</span>는 개발 효율성을 높이기 위해 빈번하게 사용되는 함수나 데이터를 미리 구현해 모아둔 집합체입니다.

**핵심 개념**
- **모듈(Module)**: 특정 기능을 하나의 파일로 구현한 형태
- **패키지(Package)**: 여러 모듈을 하나의 폴더에 묶어놓은 형태

**라이브러리의 구분**

| 구분 | 설명 |
|------|------|
| 표준 라이브러리 | 프로그래밍 언어에 기본 내장된 라이브러리로, 모듈이나 패키지 형태로 제공됨 |
| 외부 라이브러리 | 개발자들이 직접 만들어 인터넷에 공유한 것으로, 별도 설치 후 사용 가능 |

---

### 1.2 Java의 표준 라이브러리

Java는 패키지 단위로 라이브러리를 제공하며, 각 패키지 안에 클래스로 정리된 메소드들이 포함되어 있습니다.

**패키지 사용 방법**
```java
// import문으로 패키지 선언 후 사용
import java.util.*;

// 클래스.메소드() 형식으로 호출
Math.abs(-10);
```

**주요 표준 라이브러리**

| 패키지 | 주요 기능 | 대표 클래스 |
|--------|-----------|-------------|
| java.util | 날짜, 난수, 복잡한 문자열 처리 기능 | Date, Calendar, Random, StringTokenizer |
| java.lang | 기본 인터페이스, 자료형, 예외 처리 (import 없이 사용 가능) | String, System, Math, Error, Process |
| java.io | 파일 입출력 및 프로토콜 관련 기능 | InputStream, OutputStream, Reader, Writer |
| java.net | 네트워크 관련 기능 | Socket, URL, InetAddress |
| java.awt | 사용자 인터페이스(UI) 관련 기능 | Frame, Panel, Button, Dialog, Checkbox |

---

### 1.3 Java의 주요 메소드

**String 클래스**

| 메소드 | 기능 |
|--------|------|
| A.length() | 문자열 A의 길이 반환 |
| A.charAt(위치) | 문자열 A에서 해당 위치의 문자 반환 |
| A.substring(위치) | 지정 위치부터 끝까지의 문자열 반환 |
| A.trim() | 문자열 A의 양쪽 공백 제거 |
| A.equals(B) | 대소문자 구분하여 A와 B 비교 (같으면 true) |
| A.equalsIgnoreCase(B) | 대소문자 무시하고 A와 B 비교 |
| A.compareTo(B) | 숫자 문자열 A와 B 비교 (같으면 0, A가 크면 1, B가 크면 -1) |
| toLowerCase(문자열) | 모두 소문자로 변환 |
| toUpperCase(문자열) | 모두 대문자로 변환 |
| replace(대상, 변환문자) | 대상을 변환문자로 치환 |
| split(구분자) | 구분자 기준으로 문자열 분리 |
| getNumericValue() | 숫자 형태의 문자를 정수로 변환 ('a'~'z'는 10~35 반환, 특수문자는 -1) |

**Math 클래스**

| 메소드 | 기능 |
|--------|------|
| Math.abs() | 절댓값 반환 |
| Math.sqrt() | 제곱근 반환 |
| Math.pow() | 거듭제곱 반환 |
| Math.max(), Math.min() | 최댓값, 최솟값 반환 |
| Math.round() | 소수점 첫째 자리에서 반올림 |
| Math.ceil() | 소수점 올림 |
| Math.log10() | 상용 로그 값 계산 |

**StringTokenizer 클래스**

| 메소드 | 기능 |
|--------|------|
| countTokens() | 토큰 개수 반환 |
| hasMoreTokens() | 반환할 토큰이 있으면 true, 없으면 false |
| nextToken() | 다음 토큰을 순서대로 반환 |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">Math 클래스 상수</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <code>Math.PI</code> : 원주율 3.1415...<br>
• <code>Math.E</code> : 자연상수 2.7182...
</p>
</div>

---

### 1.4 Python의 표준 라이브러리

Python 역시 패키지 형태로 라이브러리를 제공하며, `import` 선언 후 `모듈명.메소드()` 형식으로 사용합니다.

**주요 표준 라이브러리**

| 모듈 | 주요 기능 | 대표 메소드 |
|------|-----------|-------------|
| 내장 함수 | 기본 인터페이스 (import 없이 사용 가능) | abs(), print(), slice(), pow() |
| random | 무작위 선택 기능 | choice(), sample(), random(), randrange() |
| math | 복잡한 수학 연산 | cos(), log() |
| os | 운영체제 상호작용 | getcwd(), chdir(), system() |
| re | 고급 문자열 처리 | findall(), sub() |
| datetime | 날짜 및 시간 조작 | today(), date(), strftime() |
| statistics | 통계값 산출 | mean(), median(), variance() |

---

### 1.5 Python의 주요 메소드

**문자열 관련**

| 메소드 | 기능 |
|--------|------|
| upper() | 대문자로 변경 |
| lower() | 소문자로 변경 |
| capitalize() | 첫 글자만 대문자, 나머지 소문자 |
| title() | 각 단어의 첫 글자를 대문자로 |
| replace(값1, 값2) | 값1을 값2로 교체 |
| split(값) | 값 기준으로 분리하여 리스트 반환 (기본값: 공백) |
| count(값) | 문자열에서 값의 개수 반환 |
| find(값) | 처음 검색되는 위치 반환 (못 찾으면 -1) |
| index(값) | 처음 검색되는 위치 반환 (못 찾으면 오류 발생) |
| len() | 문자열 길이 반환 |

**리스트 관련**

| 메소드 | 기능 |
|--------|------|
| list() | 반복 가능한 객체를 리스트로 변환하거나 빈 리스트 생성 |
| len() | 요소의 개수 반환 |
| pop(위치) | 해당 위치의 값을 출력하고 삭제 (생략 시 마지막 요소) |
| remove(값) | 해당 값을 찾아 삭제 |
| count(값) | 값이 저장된 요소 개수 반환 |
| extend(리스트) | 리스트 끝에 새 리스트 추가 |
| reverse() | 리스트 순서를 역순으로 뒤집음 |
| copy() | 리스트 복사 |
| index(값) | 값이 저장된 요소의 위치 반환 |
| sort() | 정렬 (기본: 오름차순, reverse=True: 내림차순) |
| sum(리스트) | 모든 요소의 합계 반환 |

**딕셔너리 관련**

| 메소드 | 기능 |
|--------|------|
| get(key, default) | key에 해당하는 값 반환 (없으면 None 또는 default 반환) |
| keys() | 모든 키 반환 |
| values() | 모든 값 반환 |
| items() | 모든 (키, 값) 쌍 반환 |
| update() | 키-값 쌍을 갱신하거나 없으면 추가 |
| setdefault() | 키-값 쌍 추가 |
| pop() | key에 해당하는 항목 제거 후 값 반환 |
| clear() | 모든 항목 제거 |

**세트 관련**

| 메소드 | 기능 |
|--------|------|
| set() | 반복 가능한 객체를 세트로 변환하거나 빈 세트 생성 |
| len() | 요소의 개수 반환 |
| pop() | 임의 요소를 추출하고 삭제 |
| add(값) | 세트에 값 추가 (이미 존재하면 추가 안 함) |
| update(세트) | 세트에 새 세트 추가하여 확장 |
| remove(값) | 값을 찾아 삭제 |

---

### 1.6 난수 발생 함수

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Java와 Python의 random() 함수는 <span class="red-text">실수 난수</span>를 반환하므로 정수로 사용하려면 자료형 변환이 필요합니다.
</p>
</div>

| 언어 | 함수 | 사용 예 (1~10 사이 정수 난수) |
|------|------|-------------------------------|
| Java | random() | `a = (int)(Math.random() * 10 + 1);` |
| Python | random() | `a = int(random.random() * 10 + 1)` |

---

## SECTION 02. 객체지향 프로그래밍 언어

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
객체지향 프로그래밍의 정의와 대표 언어들의 특징을 파악해 두세요.
</p>
</div>

### 2.1 객체지향 프로그래밍의 개념

<span class="blue-text">객체지향 프로그래밍(OOP)</span>은 현실 세계의 사물을 객체로 모델링하고, 이 객체들을 조립하듯 결합하여 프로그램을 작성하는 기법입니다.

**핵심 특징**
- 프로시저(절차)보다 **명령과 데이터로 구성된 객체**를 중심으로 함
- 한 프로그램을 다른 프로그램에서 재사용 가능

---

### 2.2 대표적인 객체지향 언어

| 언어 | 주요 특징 |
|------|-----------|
| **C++** | C언어에 객체지향 개념을 적용한 언어로, 모든 문제를 객체로 모델링하여 표현함 |
| **JAVA** | 분산 네트워크 환경에 적합하고, 멀티스레드 기능으로 여러 작업을 동시 처리 가능하며, OS와 하드웨어에 독립적이어서 이식성이 우수함 |
| **Smalltalk** | 1세대 객체지향 언어로, 순수한 객체지향 언어이며 <span class="blue-text">최초로 GUI를 제공</span>함 |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">GUI (Graphical User Interface)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
아이콘이나 메뉴를 마우스로 선택하여 작업을 수행하는 그래픽 환경의 인터페이스
</p>
</div>

---

## 연습문제

<div class="quiz-number">문제 1</div><strong>아래 Java 코드의 실행 결과를 작성하시오.</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int a = (int)Math.sqrt(25);
        int b = (int)Math.log10(1000);
        int result = a + b;
        System.out.println(result);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_lib"
   code_html=code_block1
   answer="8"
   tags="라이브러리, Math"
%}

---

<div class="quiz-number">문제 2</div><strong>아래 Python 코드의 실행 결과를 작성하시오.</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>numbers = [8, 3, 1, 6, 2, 9, 4]
numbers.sort()
numbers.reverse()
print(numbers)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_lib"
   code_html=code_block2
   answer="[9, 8, 6, 4, 3, 2, 1]"
   tags="라이브러리, List"
%}

---

<div class="quiz-number">문제 3</div><strong>아래는 1부터 50까지의 난수를 생성하는 Python 코드입니다. 세 개의 괄호에 공통으로 들어갈 라이브러리명을 작성하시오.</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>import (   ①   )

for i in range(10):
    print(int((   ②   ).(   ③   )() * 50 + 1))</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
정답은 쉼표(,)로 구분하여 작성하시오.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_lib"
   code_html=code_block3
   answer="random, random, random|random,random,random"
   tags="라이브러리, Python"
%}

---

<div class="quiz-number">문제 4</div><strong>아래 Java 코드의 실행 결과를 작성하시오.</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        String str1 = "PROGRAMtest";
        String str2 = "programTEST";

        if (str1.equalsIgnoreCase(str2))
            System.out.print(str1.toUpperCase());
        else if (str1.equals(str2))
            System.out.print(str1.toLowerCase());
        else
            System.out.print(str2);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_lib"
   code_html=code_block4
   answer="PROGRAMTEST"
   tags="라이브러리, String"
%}

---

<div class="quiz-number">문제 5</div><strong>아래 Python 코드의 실행 결과를 작성하시오.</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>data = "software-engineering"
result = data.split('e')
print(result[2])</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_lib"
   code_html=code_block5
   answer="ring"
   tags="라이브러리, String"
%}

---

<div class="quiz-number">문제 6</div><strong>아래 Java 코드의 실행 결과를 작성하시오.</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Main {
    public static void main(String[] args) {
        String teststr = "   SampleText   ";
        System.out.println(teststr.trim().length());
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_lib"
   code_html=code_block6
   answer="10"
   tags="라이브러리, String"
%}

---

<div class="quiz-number">문제 7</div><strong>아래 Python 코드에서 딕셔너리의 모든 (키, 값) 쌍을 순회하기 위해 사용되는 메소드명을 작성하시오.</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def find_keys(dict, x):
    return [k for k, v in dict.(   ) if v == x]</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7_lib"
   code_html=code_block7
   answer="items()|items"
   tags="라이브러리, Dictionary"
%}

---

<div class="quiz-number">문제 8</div><strong>아래 Python 코드의 실행 결과를 작성하시오.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>d1 = {'a': 5}
d2 = {'b': 10, 'a': 15}
d1.update(d2)
print(d1)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8_lib"
   code_html=code_block8
   answer="{'a': 15, 'b': 10}"
   tags="라이브러리, Dictionary"
%}

---

<div class="quiz-number">문제 9</div><strong>아래 Java 코드의 실행 결과를 작성하시오.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        String str = "LEARN*!@CODE#%";
        String res = str.replaceAll("[^a-zA-Z0-9,. ]", "*");
        System.out.print(res);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_lib"
   code_html=code_block9
   answer="LEARN***CODE**"
   tags="라이브러리, String, 정규식"
%}

---

<div class="quiz-number">문제 10</div><strong>아래 Python 코드의 실행 결과를 두 줄로 작성하시오. (줄바꿈은 슬래시(/)로 구분)</strong>

{% capture code_block10 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>d = {'x': 10, 'y': 20}
print(d.get('x'))
print(d.get('z', 0))</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz10_lib"
   code_html=code_block10
   answer="10/0|10 / 0"
   tags="라이브러리, Dictionary"
%}

---

<div class="quiz-number">문제 11</div><strong>아래 Python 코드의 실행 결과를 작성하시오.</strong>

{% capture code_block11 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>numbers = [2, 4, 6, 8, 10]
even_set = {2, 4, 6}
new_set = {12, 14}
last_num = numbers.pop()
even_set.add(last_num)
numbers.remove(6)
even_set.update(new_set)
print(even_set)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_lib"
   code_html=code_block11
   answer="{2, 4, 6, 10, 12, 14}"
   tags="라이브러리, Set"
%}

---

<div class="quiz-number">문제 12</div><strong>현실 세계의 사물을 객체로 만들고, 이 객체들을 조립하여 프로그램을 작성하는 프로그래밍 기법의 명칭을 작성하시오.</strong>

{% include quiz-text.html
   id="quiz12_oop"
   answer="객체지향 프로그래밍|객체지향 프로그래밍 언어|OOP"
   tags="객체지향"
%}

---

<div class="quiz-number">문제 13</div><strong>아래 Java 코드의 실행 결과를 작성하시오.</strong>

{% capture code_block13 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>import java.math.*;

public class Test {
    public static void main(String[] args) {
        BigInteger n = new BigInteger("54321");
        BigInteger m = new BigInteger("12345");
        System.out.print(n.compareTo(m));
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz13_lib"
   code_html=code_block13
   answer="1"
   tags="라이브러리, BigInteger"
%}

---

<div class="quiz-number">문제 14</div><strong>다음 객체지향 언어에 관한 설명에서 괄호에 들어갈 언어명을 쉼표(,)로 구분하여 작성하시오.</strong>

{% capture code_block14 %}
<div style="margin: 15px 0; line-height: 1.8;">
• (①) : C언어에 객체지향 개념을 적용하였으며, 모든 문제를 객체로 모델링하여 표현한다.<br>
• (②) : 최초로 GUI를 제공한 1세대 객체지향 언어이며, 순수한 객체지향 프로그래밍 언어이다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz14_oop"
   code_html=code_block14
   answer="C++, Smalltalk|C++,Smalltalk"
   tags="객체지향"
%}

---

<div class="quiz-number">문제 15</div><strong>아래 Python 코드의 실행 결과를 작성하시오.</strong>

{% capture code_block15 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>sentence = "Welcome to Programming."
print(sentence.find("g"))</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz15_lib"
   code_html=code_block15
   answer="14"
   tags="라이브러리, String"
%}

---

<div class="quiz-number">문제 16</div><strong>아래 Python 코드의 실행 결과를 두 줄로 작성하시오. (줄바꿈은 슬래시(/)로 구분)</strong>

{% capture code_block16 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>d = {'x': 10, 'y': 20}
value = d.pop('x')
print(value)
print(d)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz16_lib"
   code_html=code_block16
   answer="10/{'y': 20}|10 / {'y': 20}"
   tags="라이브러리, Dictionary"
%}

---

<div class="quiz-number">문제 17</div><strong>아래 Java 코드의 실행 결과를 작성하시오.</strong>

{% capture code_block17 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>import java.util.Arrays;
import java.util.StringTokenizer;

public class Test {
    public static int[] Add(int[] originalArr, int val) {
        int[] newArray = Arrays.copyOf(originalArr, originalArr.length + 1);
        newArray[newArray.length - 1] = val;
        return newArray;
    }

    public static void main(String[] args) {
        String test1 = "25, -31, 18, 52, -22, 7, 9";
        String test2 = test1.replaceAll("[^0-9,-]", "");
        StringTokenizer strtok = new StringTokenizer(test2, ",");
        int[] originalArr = new int[strtok.countTokens()];
        int index = 0;

        while (strtok.hasMoreTokens()) {
            originalArr[index] = Integer.parseInt(strtok.nextToken());
            index++;
        }

        int[] newArray = Add(originalArr, 88);
        int maxNumber = Integer.MIN_VALUE;

        for (int number : newArray) {
            if (number > maxNumber) {
                maxNumber = number;
            }
        }

        System.out.print(maxNumber);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz17_lib"
   code_html=code_block17
   answer="88"
   tags="라이브러리, StringTokenizer"
%}

---

## 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">라이브러리</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>개념</strong>: 자주 사용하는 함수와 데이터를 모아놓은 집합체</li>
<li><strong>구분</strong>: 표준 라이브러리(기본 제공) / 외부 라이브러리(별도 설치)</li>
<li><strong>Java 주요 패키지</strong>: java.lang(import 불필요), java.util, java.io, java.net, java.awt</li>
<li><strong>Python 주요 모듈</strong>: 내장 함수(import 불필요), random, math, os, re, datetime</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">객체지향 프로그래밍</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>정의</strong>: 현실 세계의 객체를 조립하여 프로그램을 작성하는 기법</li>
<li><strong>JAVA</strong>: 분산 네트워크, 멀티스레드, OS 독립적, 높은 이식성</li>
<li><strong>C++</strong>: C언어 + 객체지향, 모든 문제를 객체로 모델링</li>
<li><strong>Smalltalk</strong>: 1세대 객체지향, 순수 객체지향, 최초의 GUI 제공</li>
</ul>

</div>

---
