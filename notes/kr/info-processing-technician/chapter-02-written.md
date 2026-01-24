---
layout: article
title: 2. 프로그래밍 언어 활용
permalink: /notes/kr/info-processing-technician/chapter-02
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 강의 노트, 프로그래밍 언어 활용 - 라이브러리, 구조적/객체지향/스크립트 프로그래밍 언어의 개념과 특징을 다룹니다.
keywords: "프로그래밍기능사, 라이브러리, 구조적 프로그래밍, 객체지향, 스크립트 언어, Java, Python"
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

<style>
    /* 색상 활용 규칙
      빨강: 주의, 경고, 위험 (오답, 금지사항 등)
      파랑: 핵심 개념, 주요 기능 (라이브러리, 객체지향 특징 등)
      초록: 안전한 대안, 긍정적 결과 (정답, 장점 등)
      노랑: 코드 요소 (패키지명, 메소드명 등)
    */
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%20%EC%96%B8%EC%96%B4%20%ED%99%9C%EC%9A%A9&reversal=false&textBg=false)

---

## SECTION 001. 라이브러리

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 포인트 (중요도: ★★★★★)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Java와 Python의 표준 라이브러리를 패키지 단위로 이해하고, 대표적인 라이브러리의 종류와 주요 기능을 숙지해야 합니다. 특히 자주 사용되는 메소드들의 기능을 정확히 암기하세요.
</p>
</div>

### 1.1 라이브러리의 개념

<span class="blue-text">라이브러리(Library)</span>는 프로그램 개발 시 자주 필요한 기능들을 미리 구현하여 모아놓은 <span class="blue-text">코드의 집합</span>입니다.

**라이브러리의 특징**
- 반복적으로 사용되는 함수와 데이터를 재사용 가능한 형태로 제공
- 개발 시간 단축 및 코드의 신뢰성 향상
- 필요한 시점에 호출(import)하여 사용

**라이브러리의 구성**

| 용어 | 설명 |
|------|------|
| 모듈 | 특정 기능을 수행하는 함수나 클래스들이 하나의 파일로 구현된 형태 |
| 패키지 | 관련된 여러 모듈을 하나의 디렉터리(폴더)에 모아 놓은 형태 |

**라이브러리의 분류**

- **표준 라이브러리(Standard Library)**
  - 프로그래밍 언어 설치 시 기본으로 포함되어 제공
  - 별도의 설치 과정 없이 바로 사용 가능

- **외부 라이브러리(External Library)**
  - 개발자 커뮤니티에서 제작하여 공유하는 라이브러리
  - 별도의 다운로드 및 설치 과정 필요

---

### 1.2 Java의 주요 표준 라이브러리

Java에서는 관련 기능을 <span class="blue-text">패키지(Package)</span> 단위로 제공합니다. 각 패키지에는 클래스들이 포함되어 있으며, 클래스 안에 메소드(Method)가 정의되어 있습니다.

**패키지 사용 방법**
```java
// 패키지 전체를 import
import java.util.*;

// 특정 클래스만 import
import java.util.Date;

// 사용 예시
Math.abs(-10);  // 클래스명.메소드명()
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">참고</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Java에서 함수를 메소드(Method)라고 부릅니다. 메소드는 특정 기능을 수행하는 코드 블록입니다.
</p>
</div>

**Java 주요 표준 라이브러리**

| 패키지 | 주요 기능 | 대표 클래스 |
|--------|-----------|-------------|
| java.lang | Java 프로그래밍의 기본 기능 제공<br>import 없이 사용 가능 | String, Math, System, Integer, Double, Object |
| java.util | 유틸리티 기능 제공<br>날짜, 시간, 난수, 컬렉션 등 | Date, Calendar, Random, ArrayList, HashMap |
| java.io | 입출력 관련 기능 제공<br>파일 읽기/쓰기 등 | File, InputStream, OutputStream, BufferedReader |
| java.net | 네트워크 프로그래밍 기능 제공 | Socket, URL, ServerSocket, InetAddress |
| java.awt | 그래픽 사용자 인터페이스(GUI) 제공 | Button, Label, TextField, Frame, Panel |

---

### 1.3 Java의 주요 메소드

**String 클래스의 주요 메소드**

| 메소드 | 기능 설명 |
|--------|-----------|
|length() | 문자열의 길이를 반환 |
|charAt(index) | 지정한 인덱스 위치의 문자를 반환 |
|substring(start) | start 위치부터 끝까지의 문자열 반환 |
|substring(start, end) | start부터 end-1까지의 문자열 반환 |
|toUpperCase() | 문자열을 모두 대문자로 변환 |
|toLowerCase() | 문자열을 모두 소문자로 변환 |
|trim() | 문자열 앞뒤의 공백 제거 |
|replace(old, new) | old 문자열을 new 문자열로 치환 |
|split(delimiter) | delimiter 기준으로 문자열을 분리하여 배열로 반환 |
|equals(str) | 문자열이 같은지 비교 (대소문자 구분) |
|equalsIgnoreCase(str) | 문자열이 같은지 비교 (대소문자 구분 안함) |
|compareTo(str) | 문자열을 사전순으로 비교<br>같으면 0, 이전이면 음수, 이후면 양수 |
|indexOf(str) | str이 처음 나타나는 위치 반환, 없으면 -1 |

**Math 클래스의 주요 메소드**

| 메소드 | 기능 설명 |
|--------|-----------|
|abs(x) | x의 절댓값 반환 |
|pow(x, y) | x의 y제곱 반환 |
|sqrt(x) | x의 제곱근 반환 |
|ceil(x) | x보다 크거나 같은 최소 정수 (올림) |
|floor(x) | x보다 작거나 같은 최대 정수 (내림) |
|round(x) | x를 반올림한 정수 |
|max(x, y) | x와 y 중 큰 값 반환 |
|min(x, y) | x와 y 중 작은 값 반환 |
|random() | 0.0 이상 1.0 미만의 난수 반환 |

---

### 1.4 Python의 주요 표준 라이브러리

Python도 Java와 유사하게 모듈과 패키지 형태로 라이브러리를 제공합니다.

**모듈 사용 방법**
```python
# 모듈 전체를 import
import random

# 모듈에서 특정 함수만 import
from random import choice

# 별칭을 사용하여 import
import datetime as dt

# 사용 예시
random.randint(1, 10)  # 모듈명.함수명()
```

**Python 주요 표준 라이브러리**

| 모듈 | 주요 기능 | 대표 함수/메소드 |
|------|-----------|------------------|
|내장 함수 | import 없이 사용 가능한 기본 함수 | print(), len(), type(), int(), str(), input() |
|math | 수학 연산 관련 기능 | sqrt(), pow(), ceil(), floor(), sin(), cos() |
|random | 난수 생성 및 무작위 선택 | random(), randint(), choice(), shuffle() |
|datetime | 날짜와 시간 처리 | now(), today(), strftime(), timedelta() |
|os | 운영체제와 상호작용 | getcwd(), listdir(), mkdir(), remove() |
|sys | 시스템 관련 기능 | argv, exit(), path |
|re | 정규표현식을 이용한 문자열 처리 | search(), findall(), sub(), split() |

---

### 1.5 Python의 주요 메소드

**문자열(String) 관련 메소드**

| 메소드 | 기능 설명 |
|--------|-----------|
|upper() | 모든 문자를 대문자로 변환 |
|lower() | 모든 문자를 소문자로 변환 |
|capitalize() | 첫 번째 문자만 대문자로 변환 |
|title() | 각 단어의 첫 글자를 대문자로 변환 |
|strip() | 양쪽 공백 제거 |
|replace(old, new) | old를 new로 치환 |
|split(sep) | sep을 기준으로 문자열 분리 (기본값: 공백) |
|join(list) | 리스트의 요소들을 연결하여 문자열 생성 |
|find(sub) | sub가 처음 나타나는 위치 반환, 없으면 -1 |
|index(sub) | sub가 처음 나타나는 위치 반환, 없으면 오류 발생 |
|count(sub) | sub가 나타나는 횟수 반환 |

**리스트(List) 관련 메소드**

| 메소드 | 기능 설명 |
|--------|-----------|
|append(item) | 리스트 끝에 item 추가 |
|insert(index, item) | index 위치에 item 삽입 |
|remove(item) | 첫 번째로 나타나는 item 삭제 |
|pop() | 마지막 요소를 반환하고 삭제 |
|pop(index) | index 위치의 요소를 반환하고 삭제 |
|sort() | 리스트를 오름차순으로 정렬 |
|sort(reverse=True) | 리스트를 내림차순으로 정렬 |
|reverse() | 리스트의 순서를 반대로 뒤집기 |
|count(item) | item이 나타나는 횟수 반환 |
|index(item) | item이 처음 나타나는 위치 반환 |
|extend(list) | 다른 리스트의 요소를 추가 |
|clear() | 모든 요소 삭제 |

---

### 🎯 기출문제 따라잡기

<div class="quiz-number">문제 1</div><strong>라이브러리에 관한 설명 중 올바르지 않은 것은?</strong>

{% capture choices1 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 자주 사용하는 기능을 미리 구현하여 제공하는 코드 집합이다<br>
② 모듈과 패키지를 포괄하는 개념이다<br>
③ 표준 라이브러리는 언어 설치 시 기본으로 제공된다<br>
④ 외부 라이브러리는 모든 프로그래밍 언어에 기본 포함되어 있다
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_lib"
   code_html=choices1
   answer="4|④"
   tags="라이브러리"
%}

---

<div class="quiz-number">문제 2</div><strong>다음 Java 코드의 출력 결과는?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>String text = "Programming";
System.out.println(text.substring(3, 7));</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
① Pro<br>
② gram<br>
③ gramm<br>
④ rammi
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_lib"
   code_html=code_block2
   answer="2|②|gram"
   tags="라이브러리"
%}

---

<div class="quiz-number">문제 3</div><strong>다음 Python 코드의 실행 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>text = "Python Programming"
print(text.replace("o", "0").count("0"))</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
① 1<br>
② 2<br>
③ 3<br>
④ 4
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_lib"
   code_html=code_block3
   answer="3|③"
   tags="라이브러리"
%}

---

<div class="quiz-number">문제 4</div><strong>Java에서 import 없이 사용할 수 있는 패키지는?</strong>

{% capture choices4 %}
<div style="margin: 15px 0; line-height: 1.8;">
① java.util<br>
② java.lang<br>
③ java.io<br>
④ java.net
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_lib"
   code_html=choices4
   answer="2|②|java.lang"
   tags="라이브러리"
%}

---

<div class="quiz-number">문제 5</div><strong>Python 리스트 메소드 중 리스트의 순서를 반대로 뒤집는 것은?</strong>

{% capture choices5 %}
<div style="margin: 15px 0; line-height: 1.8;">
① sort()<br>
② reverse()<br>
③ remove()<br>
④ pop()
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_lib"
   code_html=choices5
   answer="2|②|reverse()|reverse"
   tags="라이브러리"
%}

---

## SECTION 002. 구조적 프로그래밍 언어

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 포인트 (중요도: ★★★★☆)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
구조적 프로그래밍의 핵심은 <span class="red-text">세 가지 기본 구조(순차, 선택, 반복)</span>와 <span class="red-text">GOTO문 사용 금지</span>입니다. 이 두 가지 핵심 개념을 반드시 기억하세요.
</p>
</div>

### 2.1 구조적 프로그래밍의 개념

<span class="blue-text">구조적 프로그래밍(Structured Programming)</span>은 네덜란드의 컴퓨터 과학자 <span class="blue-text">에츠허르 데이크스트라(Edsger Dijkstra)</span>가 제안한 프로그래밍 방법론입니다.

**등장 배경**
- 1960년대 후반, 프로그램의 복잡도 증가로 유지보수가 어려워짐
- GOTO문의 무분별한 사용으로 프로그램 흐름 파악이 어려워짐
- 프로그램의 신뢰성과 생산성 향상 필요성 대두

**구조적 프로그래밍의 목적**
- 프로그램의 복잡도를 낮추어 이해하기 쉽게 만듦
- 코드의 신뢰성과 품질 향상
- 유지보수와 디버깅 용이
- 프로그래밍 표준화를 통한 생산성 증대

---

### 2.2 구조적 프로그래밍의 원칙

**1. 단일 입구와 단일 출구**
- 각 프로그램 모듈은 하나의 시작점과 하나의 종료점을 가져야 함
- 프로그램의 흐름을 예측 가능하게 만듦

**2. GOTO문 사용 금지**
- 무분별한 분기(GOTO)를 사용하지 않음
- 프로그램의 논리적 흐름을 명확하게 유지

**3. 세 가지 기본 제어 구조만 사용**

<table>
<tr>
<th style="width: 25%;">구조</th>
<th>설명</th>
<th>예시</th>
</tr>
<tr>
<td><span class="blue-text">순차(Sequence)</span></td>
<td>명령문이 위에서 아래로 순차적으로 실행되는 구조</td>
<td>
<pre>
int a = 10;
int b = 20;
int sum = a + b;
</pre>
</td>
</tr>
<tr>
<td><span class="blue-text">선택(Selection)</span></td>
<td>조건에 따라 실행할 명령을 선택하는 구조<br>(if, if-else, switch 등)</td>
<td>
<pre>
if (score >= 60) {
    System.out.println("합격");
} else {
    System.out.println("불합격");
}
</pre>
</td>
</tr>
<tr>
<td><span class="blue-text">반복(Iteration)</span></td>
<td>조건이 만족하는 동안 명령을 반복 실행하는 구조<br>(for, while, do-while 등)</td>
<td>
<pre>
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
</pre>
</td>
</tr>
</table>

---

### 2.3 구조적 프로그래밍의 장점

| 장점 | 설명 |
|------|------|
| **가독성 향상** | 프로그램의 논리적 흐름이 명확하여 읽기 쉬움 |
| **유지보수 용이** | 구조화된 코드로 수정과 확장이 쉬움 |
| **디버깅 효율** | 오류 발생 시 원인을 빠르게 파악 가능 |
| **생산성 증대** | 표준화된 구조로 개발 시간 단축 |
| **신뢰성 향상** | 논리적 오류 감소로 프로그램 품질 향상 |
| **재사용성** | 모듈화를 통한 코드 재사용 가능 |

---

### 2.4 구조적 프로그래밍 vs 비구조적 프로그래밍

**비구조적 프로그래밍 (GOTO 사용)**
```c
// 나쁜 예: GOTO를 사용한 코드
int i = 1;
loop:
    if (i <= 10) {
        printf("%d ", i);
        i++;
        goto loop;  // GOTO문 사용
    }
```

**구조적 프로그래밍 (반복문 사용)**
```c
// 좋은 예: 구조적 프로그래밍
for (int i = 1; i <= 10; i++) {
    printf("%d ", i);
}
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">주의</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
GOTO문을 사용하면 프로그램의 실행 흐름이 복잡해져 <span class="red-text">"스파게티 코드(Spaghetti Code)"</span>가 됩니다. 이는 유지보수와 디버깅을 매우 어렵게 만듭니다.
</p>
</div>

---

### 🎯 기출문제 따라잡기

<div class="quiz-number">문제 1</div><strong>구조적 프로그래밍의 기본 제어 구조가 아닌 것은?</strong>

{% capture choices_struct1 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 순차(Sequence)<br>
② 선택(Selection)<br>
③ 반복(Iteration)<br>
④ 분기(Branch)
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_struct"
   code_html=choices_struct1
   answer="4|④|분기"
   tags="구조적 프로그래밍"
%}

---

<div class="quiz-number">문제 2</div><strong>구조적 프로그래밍에 관한 설명으로 올바르지 않은 것은?</strong>

{% capture choices_struct2 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 다익스트라(Dijkstra)가 제안한 프로그래밍 방법론이다<br>
② 프로그램의 복잡도를 낮추어 이해하기 쉽게 만든다<br>
③ GOTO문을 적극 활용하여 프로그램 흐름을 자유롭게 제어한다<br>
④ 순차, 선택, 반복의 세 가지 기본 구조를 사용한다
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_struct"
   code_html=choices_struct2
   answer="3|③"
   tags="구조적 프로그래밍"
%}

---

<div class="quiz-number">문제 3</div><strong>다음 중 구조적 프로그래밍의 장점이 아닌 것은?</strong>

{% capture choices_struct3 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 프로그램의 가독성이 향상된다<br>
② 유지보수가 용이하다<br>
③ 디버깅이 쉬워진다<br>
④ 프로그램 실행 속도가 항상 빠르다
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_struct"
   code_html=choices_struct3
   answer="4|④"
   tags="구조적 프로그래밍"
%}

---

## SECTION 003. 객체지향 프로그래밍 언어

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 포인트 (중요도: ★★★★★)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
객체지향 프로그래밍의 핵심 특징인 <span class="blue-text">캡슐화, 상속, 다형성, 추상화</span>를 정확히 이해하고, 객체/클래스/메시지의 개념을 명확히 구분할 수 있어야 합니다.
</p>
</div>

### 3.1 객체지향 프로그래밍의 개념

<span class="blue-text">객체지향 프로그래밍(Object-Oriented Programming, OOP)</span>은 현실 세계의 사물(객체)을 프로그래밍에 반영하는 기법으로, 프로그램을 <span class="blue-text">객체들의 집합</span>으로 구성하여 개발하는 방법론입니다.

**객체지향 프로그래밍의 특징**
- 데이터와 데이터를 처리하는 함수를 하나의 객체로 묶어서 관리
- 현실 세계를 모델링하기 쉬움
- 코드의 재사용성이 높음
- 유지보수와 확장이 용이

**대표적인 객체지향 언어**
- Java, C++, C#, Python, Ruby, JavaScript 등

---

### 3.2 객체지향 프로그래밍의 구성 요소

<table>
<tr>
<th style="width: 20%;">구성 요소</th>
<th>설명</th>
<th>예시</th>
</tr>
<tr>
<td><span class="blue-text">객체<br>(Object)</span></td>
<td>
• 현실 세계의 사물을 프로그래밍으로 표현한 것<br>
• 속성(데이터)과 메소드(기능)를 가짐<br>
• 클래스로부터 생성됨
</td>
<td>
자동차, 학생, 계좌 등<br><br>
예: '내 차'는 Car 클래스의 객체
</td>
</tr>
<tr>
<td><span class="blue-text">클래스<br>(Class)</span></td>
<td>
• 객체를 생성하기 위한 설계도 또는 틀<br>
• 공통된 속성과 메소드를 정의<br>
• 동일한 클래스로 여러 객체 생성 가능
</td>
<td>
Car 클래스:<br>
- 속성: 색상, 속도, 크기<br>
- 메소드: 가속(), 정지(), 회전()
</td>
</tr>
<tr>
<td><span class="blue-text">메시지<br>(Message)</span></td>
<td>
• 객체 간 상호작용을 위한 수단<br>
• 한 객체가 다른 객체의 메소드를 호출하는 것<br>
• 메시지를 받은 객체는 해당 메소드를 실행
</td>
<td>
myCar.start();<br>
→ myCar 객체에게 "시동을 걸어라"는 메시지 전달
</td>
</tr>
<tr>
<td><span class="blue-text">속성<br>(Attribute)</span></td>
<td>
• 객체가 가지는 데이터 또는 상태<br>
• 변수의 형태로 표현<br>
• 객체의 특징을 나타냄
</td>
<td>
자동차의 색상, 속도, 연료량<br>
학생의 이름, 학번, 성적
</td>
</tr>
<tr>
<td><span class="blue-text">메소드<br>(Method)</span></td>
<td>
• 객체의 동작 또는 기능<br>
• 함수의 형태로 표현<br>
• 속성 값을 변경하거나 특정 작업 수행
</td>
<td>
자동차의 가속(), 감속(), 정지()<br>
학생의 공부하다(), 시험보다()
</td>
</tr>
</table>

---

### 3.3 객체지향 프로그래밍의 특징

#### 1. 캡슐화 (Encapsulation)

<span class="blue-text">캡슐화</span>는 데이터(속성)와 데이터를 처리하는 함수(메소드)를 하나로 묶고, 외부에서 직접 접근하지 못하도록 <span class="blue-text">정보 은닉(Information Hiding)</span>하는 것입니다.

**캡슐화의 장점**
- 외부로부터 데이터를 보호
- 내부 구현을 숨기고 인터페이스만 제공
- 변경에 따른 오류의 파급 효과 최소화
- 코드의 재사용성 향상

```java
// 캡슐화 예시
public class Account {
    private int balance;  // private: 외부 접근 차단

    public void deposit(int amount) {  // public 메소드로만 접근 허용
        if (amount > 0) {
            balance += amount;
        }
    }

    public int getBalance() {
        return balance;
    }
}
```

---

#### 2. 상속 (Inheritance)

<span class="blue-text">상속</span>은 기존 클래스(부모 클래스)의 속성과 메소드를 새로운 클래스(자식 클래스)가 물려받아 사용하는 것입니다.

**상속의 장점**
- 코드의 재사용성 증대
- 계층적 분류 및 관리 가능
- 유지보수 용이
- 확장성 향상

```java
// 상속 예시
class Vehicle {  // 부모 클래스
    String brand;
    void start() {
        System.out.println("시동을 겁니다");
    }
}

class Car extends Vehicle {  // 자식 클래스
    int seats;
    void drive() {
        System.out.println("운전합니다");
    }
}

// Car 클래스는 Vehicle의 brand와 start()를 물려받음
```

---

#### 3. 다형성 (Polymorphism)

<span class="blue-text">다형성</span>은 하나의 메시지에 대해 각 객체가 자신만의 방식으로 응답할 수 있는 능력입니다.

**다형성의 구현 방법**

| 방법 | 설명 | 예시 |
|------|------|------|
|오버로딩<br>(Overloading) | 같은 이름의 메소드를 매개변수의 개수나 타입을 다르게 하여 여러 개 정의 | add(int a, int b)<br>add(double a, double b) |
|오버라이딩<br>(Overriding) | 부모 클래스의 메소드를 자식 클래스에서 재정의 | 부모의 start()를<br>자식에서 다르게 재정의 |

```java
// 오버로딩 예시
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }
}

// 오버라이딩 예시
class Animal {
    void sound() {
        System.out.println("동물 소리");
    }
}

class Dog extends Animal {
    @Override
    void sound() {  // 메소드 재정의
        System.out.println("멍멍");
    }
}
```

---

#### 4. 추상화 (Abstraction)

<span class="blue-text">추상화</span>는 복잡한 내부 구현을 숨기고 핵심적인 정보나 기능만을 외부에 제공하는 것입니다.

**추상화의 특징**
- 불필요한 세부사항을 감춤
- 공통적인 속성이나 기능을 추출
- 복잡도를 낮춰 이해하기 쉽게 만듦

```java
// 추상화 예시
abstract class Shape {  // 추상 클래스
    abstract double getArea();  // 추상 메소드 (구현 없음)
}

class Circle extends Shape {
    double radius;

    @Override
    double getArea() {  // 구체적인 구현
        return 3.14 * radius * radius;
    }
}
```

---

### 3.4 객체지향 프로그래밍의 장단점

**장점**

| 장점 | 설명 |
|------|------|
| **재사용성** | 상속과 모듈화를 통해 코드 재사용이 용이 |
| **확장성** | 새로운 기능 추가가 쉬움 |
| **유지보수성** | 모듈화로 인해 수정과 관리가 편리 |
| **직관성** | 현실 세계를 모델링하여 이해하기 쉬움 |
| **생산성** | 라이브러리 활용으로 개발 시간 단축 |

**단점**

| 단점 | 설명 |
|------|------|
| **학습 곡선** | 개념 이해와 설계가 복잡함 |
| **실행 속도** | 절차지향에 비해 상대적으로 느림 |
| **설계 시간** | 초기 설계에 많은 시간 소요 |

---

### 🎯 기출문제 따라잡기

<div class="quiz-number">문제 1</div><strong>객체지향 프로그래밍의 구성 요소가 아닌 것은?</strong>

{% capture choices_oop1 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 객체(Object)<br>
② 클래스(Class)<br>
③ 메시지(Message)<br>
④ 반복문(Loop)
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_oop"
   code_html=choices_oop1
   answer="4|④|반복문"
   tags="객체지향"
%}

---

<div class="quiz-number">문제 2</div><strong>부모 클래스의 속성과 메소드를 자식 클래스가 물려받는 것은?</strong>

{% capture choices_oop2 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 캡슐화<br>
② 상속<br>
③ 다형성<br>
④ 추상화
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_oop"
   code_html=choices_oop2
   answer="2|②|상속"
   tags="객체지향"
%}

---

<div class="quiz-number">문제 3</div><strong>객체지향의 특징 설명 중 올바르지 않은 것은?</strong>

{% capture choices_oop3 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 캡슐화는 데이터와 메소드를 하나로 묶는 것이다<br>
② 상속은 하나의 메시지에 여러 형태로 응답하는 것이다<br>
③ 다형성은 오버로딩과 오버라이딩으로 구현된다<br>
④ 추상화는 핵심적인 정보만을 외부에 제공하는 것이다
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_oop"
   code_html=choices_oop3
   answer="2|②"
   tags="객체지향"
%}

---

<div class="quiz-number">문제 4</div><strong>같은 이름의 메소드를 매개변수를 다르게 하여 여러 개 정의하는 것은?</strong>

{% capture choices_oop4 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 오버라이딩<br>
② 오버로딩<br>
③ 캡슐화<br>
④ 상속
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_oop"
   code_html=choices_oop4
   answer="2|②|오버로딩"
   tags="객체지향"
%}

---

<div class="quiz-number">문제 5</div><strong>객체의 동작이나 기능을 정의한 것은?</strong>

{% capture choices_oop5 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 속성(Attribute)<br>
② 메소드(Method)<br>
③ 클래스(Class)<br>
④ 메시지(Message)
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_oop"
   code_html=choices_oop5
   answer="2|②|메소드"
   tags="객체지향"
%}

---

<div class="quiz-number">문제 6</div><strong>여러 유사한 객체들을 묶어 공통 특성을 표현한 것은?</strong>

{% capture choices_oop6 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 객체<br>
② 클래스<br>
③ 메시지<br>
④ 메소드
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_oop"
   code_html=choices_oop6
   answer="2|②|클래스"
   tags="객체지향"
%}

---

## SECTION 004. 스크립트 언어

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 포인트 (중요도: ★★★★☆)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
스크립트 언어를 <span class="blue-text">서버용</span>과 <span class="blue-text">클라이언트용</span>으로 구분하여 정리하고, 각 언어의 특징과 실행 환경을 명확히 이해해야 합니다.
</p>
</div>

### 4.1 스크립트 언어의 개념

<span class="blue-text">스크립트 언어(Script Language)</span>는 프로그램을 <span class="blue-text">컴파일 과정 없이</span> 인터프리터를 통해 한 줄씩 해석하여 즉시 실행하는 프로그래밍 언어입니다.

**스크립트 언어의 특징**
- HTML 문서 내에 직접 삽입하여 사용 가능
- 컴파일 없이 바로 실행 (인터프리터 방식)
- 간결한 문법으로 배우기 쉬움
- 빠른 개발과 프로토타이핑에 유리

**주요 사용 분야**
- 웹 프로그래밍 (동적 웹 페이지 생성)
- 시스템 관리 및 자동화
- 데이터 처리 및 분석
- 게임 스크립팅

---

### 4.2 스크립트 언어의 분류

<table>
<tr>
<th style="width: 25%;">분류</th>
<th>실행 위치</th>
<th>대표 언어</th>
</tr>
<tr>
<td><span class="blue-text">서버 사이드<br>스크립트</span></td>
<td>
• 서버에서 실행<br>
• 실행 결과만 클라이언트로 전송<br>
• 소스 코드가 노출되지 않음<br>
• 데이터베이스 연동 가능
</td>
<td>
<span class="yellow-code">JSP</span><br>
<span class="yellow-code">ASP</span><br>
<span class="yellow-code">PHP</span><br>
<span class="yellow-code">Python</span>
</td>
</tr>
<tr>
<td><span class="blue-text">클라이언트 사이드<br>스크립트</span></td>
<td>
• 클라이언트(웹 브라우저)에서 실행<br>
• 소스 코드가 노출됨<br>
• 서버 부하 감소<br>
• 빠른 응답 속도
</td>
<td>
<span class="yellow-code">JavaScript</span><br>
<span class="yellow-code">VBScript</span>
</td>
</tr>
</table>

---

### 4.3 스크립트 언어의 장단점

**장점**

| 장점 | 설명 |
|------|------|
| **빠른 개발** | 컴파일 없이 바로 실행하여 결과 확인 |
| **간단한 문법** | 배우기 쉽고 코딩이 간편 |
| **빠른 수정** | 소스 수정 후 즉시 반영 가능 |
| **프로토타이핑** | 아이디어를 빠르게 구현하고 테스트 |

**단점**

| 단점 | 설명 |
|------|------|
| **실행 속도** | 인터프리터 방식으로 컴파일 언어보다 느림 |
| **런타임 오류** | 실행 중에 오류 발견 (컴파일 타임 체크 없음) |
| **보안** | 클라이언트 스크립트는 소스 코드 노출 |

---

### 4.4 주요 스크립트 언어

#### 1. JavaScript

<span class="blue-text">JavaScript</span>는 웹 페이지에 동적인 기능을 추가하기 위한 <span class="blue-text">클라이언트 사이드 스크립트 언어</span>입니다.

**JavaScript의 특징**
- 웹 브라우저에서 실행
- HTML/CSS와 함께 웹 개발의 핵심 기술
- 이벤트 기반 프로그래밍
- 객체 기반 언어 (프로토타입 기반)
- Node.js를 통해 서버 사이드 개발도 가능

**JavaScript 활용 예시**
```javascript
// 버튼 클릭 이벤트 처리
document.getElementById("myButton").onclick = function() {
    alert("버튼이 클릭되었습니다!");
};

// 폼 유효성 검사
function validateForm() {
    let name = document.forms["myForm"]["name"].value;
    if (name == "") {
        alert("이름을 입력하세요");
        return false;
    }
}
```

---

#### 2. JSP (Java Server Pages)

<span class="blue-text">JSP</span>는 Java 기반의 <span class="blue-text">서버 사이드 스크립트 언어</span>로, 동적 웹 페이지를 생성합니다.

**JSP의 특징**
- 서버에서 실행되는 Java 코드
- 다양한 운영체제에서 실행 가능 (플랫폼 독립적)
- Java의 강력한 기능 활용 가능
- 데이터베이스 연동 용이

---

#### 3. ASP (Active Server Pages)

<span class="blue-text">ASP</span>는 마이크로소프트에서 개발한 <span class="blue-text">서버 사이드 스크립트 언어</span>입니다.

**ASP의 특징**
- Windows 서버 환경에서 주로 사용
- IIS (Internet Information Services)에서 실행
- VBScript 또는 JScript 사용
- .NET 기반의 ASP.NET으로 발전

---

#### 4. PHP

<span class="blue-text">PHP (Hypertext Preprocessor)</span>는 웹 개발에 특화된 <span class="blue-text">서버 사이드 스크립트 언어</span>입니다.

**PHP의 특징**
- Linux, Unix, Windows 등 다양한 OS 지원
- C, Java와 유사한 문법으로 배우기 쉬움
- 웹 호스팅 업체들이 널리 지원
- WordPress, Laravel 등 유명 프레임워크 존재
- MySQL 등 데이터베이스와의 연동이 용이

**PHP 활용 예시**
```php
<?php
    // 변수 선언 및 출력
    $name = "홍길동";
    echo "안녕하세요, " . $name . "님!";

    // 데이터베이스 연결
    $conn = mysqli_connect("localhost", "user", "password", "database");
?>
```

---

#### 5. Python

<span class="blue-text">Python</span>은 귀도 반 로섬(Guido van Rossum)이 개발한 <span class="blue-text">고수준 프로그래밍 언어</span>로, 스크립트 언어로도 널리 사용됩니다.

**Python의 특징**
- 간결하고 읽기 쉬운 문법
- 들여쓰기로 코드 블록 구분
- 객체지향, 함수형, 절차지향 모두 지원
- 다양한 분야에서 활용 (웹, 데이터 분석, AI 등)
- 풍부한 라이브러리와 프레임워크
- 플랫폼 독립적

**Python 활용 분야**
- 웹 개발 (Django, Flask)
- 데이터 분석 및 시각화
- 인공지능 및 머신러닝
- 자동화 스크립트
- 과학 및 수학 연산

---

#### 6. Shell Script

<span class="blue-text">쉘 스크립트(Shell Script)</span>는 Unix/Linux 시스템에서 사용되는 <span class="blue-text">명령어 기반 스크립트</span>입니다.

**Shell Script의 특징**
- 운영체제 명령어를 조합하여 작성
- 파일 확장자: `.sh`
- 시스템 관리 및 자동화에 유용
- 컴파일 불필요로 실행 속도 빠름

**주요 Shell 종류**
- Bash Shell (가장 널리 사용)
- Bourne Shell
- C Shell
- Korn Shell

**Shell Script의 제어문**

| 분류 | 제어문 |
|------|--------|
| <span class="blue-text">선택형 | if, case |
| <span class="blue-text">반복형 | for, while, until |

---

#### 7. VBScript

<span class="blue-text">VBScript</span>는 마이크로소프트에서 개발한 <span class="blue-text">클라이언트 사이드 스크립트 언어</span>입니다.

**VBScript의 특징**
- Visual Basic을 기반으로 함
- Internet Explorer에서만 지원 (현재는 거의 사용 안 함)
- Active X 컨트롤 사용 가능
- JavaScript에 비해 사용 빈도 낮음

---

### 🎯 기출문제 따라잡기

<div class="quiz-number">문제 1</div><strong>다음 중 스크립트 언어가 아닌 것은?</strong>

{% capture choices_script1 %}
<div style="margin: 15px 0; line-height: 1.8;">
① PHP<br>
② Python<br>
③ JavaScript<br>
④ FORTRAN
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_script"
   code_html=choices_script1
   answer="4|④|FORTRAN"
   tags="스크립트 언어"
%}

---

<div class="quiz-number">문제 2</div><strong>서버 사이드 스크립트 언어가 아닌 것은?</strong>

{% capture choices_script2 %}
<div style="margin: 15px 0; line-height: 1.8;">
① JSP<br>
② ASP<br>
③ PHP<br>
④ JavaScript
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_script"
   code_html=choices_script2
   answer="4|④|JavaScript"
   tags="스크립트 언어"
%}

---

<div class="quiz-number">문제 3</div><strong>귀도 반 로섬이 개발한 언어로, 간결한 문법과 높은 가독성을 특징으로 하는 스크립트 언어는?</strong>

{% capture choices_script3 %}
<div style="margin: 15px 0; line-height: 1.8;">
① Java<br>
② C++<br>
③ Python<br>
④ Ruby
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_script"
   code_html=choices_script3
   answer="3|③|Python"
   tags="스크립트 언어"
%}

---

<div class="quiz-number">문제 4</div><strong>Shell Script에서 사용할 수 없는 제어문은?</strong>

{% capture choices_script4 %}
<div style="margin: 15px 0; line-height: 1.8;">
① if<br>
② for<br>
③ while<br>
④ switch
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_script"
   code_html=choices_script4
   answer="4|④|switch"
   tags="스크립트 언어"
%}

---

<div class="quiz-number">문제 5</div><strong>스크립트 언어의 특징으로 올바르지 않은 것은?</strong>

{% capture choices_script5 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 컴파일 없이 바로 실행 가능하다<br>
② 실행 속도가 컴파일 언어보다 항상 빠르다<br>
③ 소스 코드 수정 후 즉시 반영된다<br>
④ 문법이 간결하여 배우기 쉽다
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_script"
   code_html=choices_script5
   answer="2|②"
   tags="스크립트 언어"
%}

---

## 📝 1장 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">001. 라이브러리</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>개념</strong>: 자주 사용하는 함수와 데이터를 모아놓은 코드 집합</li>
<li><strong>분류</strong>: 표준 라이브러리(기본 제공) / 외부 라이브러리(별도 설치)</li>
<li><strong>구성</strong>: 모듈(파일 단위) / 패키지(디렉터리 단위)</li>
<li><strong>Java 주요 패키지</strong>: java.lang, java.util, java.io, java.net, java.awt</li>
<li><strong>Python 주요 모듈</strong>: math, random, datetime, os, sys, re</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">002. 구조적 프로그래밍 언어</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>제안자</strong>: 에츠허르 데이크스트라(Edsger Dijkstra)</li>
<li><strong>핵심 원칙</strong>: GOTO문 사용 금지</li>
<li><strong>3가지 기본 구조</strong>: 순차(Sequence), 선택(Selection), 반복(Iteration)</li>
<li><strong>목적</strong>: 코드 복잡도 감소, 가독성 향상, 유지보수 용이</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">003. 객체지향 프로그래밍 언어</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>구성 요소</strong>: 객체(Object), 클래스(Class), 메시지(Message)</li>
<li><strong>4대 특징</strong>: 캡슐화, 상속, 다형성, 추상화</li>
<li><strong>다형성 구현</strong>: 오버로딩(매개변수 다르게), 오버라이딩(메소드 재정의)</li>
<li><strong>대표 언어</strong>: Java, C++, C#, Python</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">004. 스크립트 언어</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>특징</strong>: 컴파일 없이 인터프리터로 실행</li>
<li><strong>서버 사이드</strong>: JSP, ASP, PHP, Python</li>
<li><strong>클라이언트 사이드</strong>: JavaScript, VBScript</li>
<li><strong>장점</strong>: 빠른 개발, 간단한 문법, 즉시 실행</li>
<li><strong>단점</strong>: 느린 실행 속도, 런타임 오류 발생</li>
</ul>

</div>

---

## 📚 다음 학습 내용

<p>다음 장에서는 <span class="blue-text">프로그래밍 언어 응용</span>에 대해 학습합니다.</p>

<ul>
<li><strong>Section 005</strong>: 데이터 타입</li>
<li><strong>Section 006</strong>: 변수</li>
<li><strong>Section 007</strong>: 연산자</li>
<li><strong>Section 008</strong>: 데이터 입·출력</li>
<li><strong>Section 009</strong>: 제어문</li>
<li><strong>Section 010</strong>: 반복문</li>
</ul>

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💪</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
이번 장에서 학습한 내용은 프로그래밍의 기본 개념입니다. 각 언어의 특징과 차이점을 명확히 이해하고, 실제 코드 예제를 통해 개념을 확실히 익히세요!
</p>
</div>

---
