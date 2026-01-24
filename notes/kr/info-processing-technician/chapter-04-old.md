---
layout: article
title: 4. 라이브러리와 프로그래밍 언어
permalink: /notes/kr/info-processing-technician/chapter-04
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기능사 실기 강의 노트, 라이브러리와 프로그래밍 언어의 종류 개념과 활용 방법을 다룹니다.
keywords: "정보처리기능사, 실기, 라이브러리, 프로그래밍 언어, 데이터 처리, 프로그래밍"
---

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
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%EC%A0%95%EB%B3%B4%EC%B2%98%EB%A6%AC%EA%B8%B0%EB%8A%A5%EC%82%AC&reversal=false&textBg=false)

## 1. 라이브러리 :star::star::star:

### 라이브러리의 개념

라이브러리는 <span class="blue-text">프로그램을 효율적으로 개발할 수 있도록 자주 사용하는 함수나 데이터들을 미리 만들어 모아 놓은 집합체</span>이다.
<small style="color: #203BB0;"> = 🧰도구상자</small>

#### 라이브러리의 분류
* <span class="blue-text">표준 라이브러리</span>: 프로그래밍 언어에 기본적으로 포함되어 있는 라이브러리로 여러 종류의 모듈이나 패키지 형태
* <span class="blue-text">외부 라이브러리</span>: 개발자들이 필요한 기능들을 만들어 인터넷 등에 공유해 놓은 것으로, 외부 라이브러리를 다운받아 설치한 후 사용

#### 라이브러리의 특징
* <span class="blue-text">효율적인 개발</span>: 자주 사용하는 함수들의 반복적인 코드 작성을 피하기 위함
* <span class="blue-text">재사용성</span>: 필요할 때는 언제든지 호출 가능
* <span class="blue-text">공유성</span>: 여러 개발자들이 공통으로 사용할 수 있는 기능 제공

#### 모듈과 패키지의 개념
* <span class="blue-text">모듈(Module)</span>: 관련된 함수나 클래스들을 하나의 파일로 묶어 놓은 것
* <span class="blue-text">패키지(Package)</span>: 여러 모듈들을 디렉토리 구조로 묶어 놓은 것

> 💡 **팁**: <span class="blue-text">라이브러리를 활용하면 개발 시간을 단축</span>하고 <span class="blue-text">코드의 품질을 향상</span>시킬 수 있습니다! 🚀

### C언어의 주요 표준 라이브러리

C언어는 <span class="blue-text">라이브러리를 헤더 파일로 제공</span>한다.  
각 헤더 파일에는 <span class="blue-text">응용 프로그램 개발에 필요한 함수들이 정리</span>되어 있다.

C언어에서 헤더 파일을 사용하려면 <span class="yellow-code">#include < stdio.h > </span>와 같이 <span class="yellow-code">include문</span>을 이용해 선언한 후 사용해야 한다.

#### C언어 주요 헤더 파일

| 헤더 파일 | 기능 | 주요 함수 |
|-----------|------|-----------|
| <span class="blue-text">stdio.h</span> | 데이터의 입출력에 사용되는 기능들 | <span class="yellow-code">printf()</span>, <span class="yellow-code">scanf()</span>, <span class="yellow-code">fprintf()</span>, <span class="yellow-code">fclose()</span>, <span class="yellow-code">fopen()</span> 등 |
| <span class="blue-text">math.h</span> | 수학 함수들을 제공 | <span class="yellow-code">sqrt()</span>, <span class="yellow-code">pow()</span>, <span class="yellow-code">log()</span>, <span class="yellow-code">fabs()</span> 등 |
| <span class="blue-text">string.h</span> | 문자열 처리에 사용되는 기능들을 제공 | <span class="yellow-code">strlen()</span>, <span class="yellow-code">strcpy()</span>, <span class="yellow-code">strcmp()</span> 등 |
| <span class="blue-text">stdlib.h</span> | 자료형 변환, 난수 발생, 메모리 할당 및 정수 수학 함수 제공 | <span class="yellow-code">atoi()</span>, <span class="yellow-code">atof()</span>, <span class="yellow-code">srand()</span>, <span class="yellow-code">rand()</span>, <span class="yellow-code">malloc()</span>, <span class="yellow-code">free()</span>,<span class="yellow-code">abs()</span> 등 |
| <span class="blue-text">time.h</span> | 시간 처리에 사용되는 기능 | <span class="yellow-code">time()</span>, <span class="yellow-code">clock()</span> 등 |

> 💡 **팁**: <span class="blue-text">C언어는 헤더 파일을 통해 라이브러리를 제공</span>하며, <span class="yellow-code">#include < 헤더 파일 ></span>로 선언 후 사용합니다! 📚 <br>
> 🌟<span class="yellow-code">abs()</span>는 정수 절댓값, <span class="yellow-code">fabs()</span>는 실수 절댓값을 계산.

### Java의 주요 표준 라이브러리

Java는 <span class="blue-text">라이브러리를 패키지에 포함하여 제공</span>한다.  
각 패키지에는 <span class="blue-text">Java 응용 프로그램 개발에 필요한 모든 메소드들이 클래스로 정리</span>되어 있다.

Java에서 패키지 사용하려면 <span class="yellow-code">import java.util</span>과 같이 <span class="yellow-code">import 문</span>을 이용한다.  
import로 선언된 패키지 안에 있는 클래스의 메소드를 사용할 때는 클래스와 메소드를 마침표로 구분하여 <span class="yellow-code">Math.sqrt()</span>와 같이 사용한다.

#### Java 주요 패키지

| 패키지 | 기능 | 주요 클래스 |
|--------|------|-------------|
| <span class="blue-text">java.lang</span> | 기본적으로 필요한 인터페이스, 자료형, 예외 처리 등에 관련된 기능 제공, import문 없이 사용 가능 | <span class="yellow-code">String</span>, <span class="yellow-code">System</span>, <span class="yellow-code">Process</span>, <span class="yellow-code">Runtime</span>, <span class="yellow-code">Math</span>, <span class="yellow-code">Error</span> 등 |
| <span class="blue-text">java.util</span> | 날짜 처리, 난수 발생, 복잡한 문자열 처리 등에 관련된 기능 제공 | <span class="yellow-code">Date</span>, <span class="yellow-code">Calendar</span>, <span class="yellow-code">Random</span>, <span class="yellow-code">StringTokenizer</span> 등 |
| <span class="blue-text">java.io</span> | 파일 입출력과 관련된 기능 및 프로토콜을 제공 | <span class="yellow-code">InputStream</span>, <span class="yellow-code">OutputStream</span>, <span class="yellow-code">Writer</span> 등 |
| <span class="blue-text">java.net</span> | 네트워크 관련된 기능 제공 | <span class="yellow-code">Socket</span>, <span class="yellow-code">URL</span>, <span class="yellow-code">InetAddress</span> 등 |
| <span class="blue-text">java.awt</span> | 사용자 인터페이스(UI)와 관련된 기능 제공 | <span class="yellow-code">Frame</span>, <span class="yellow-code">Panel</span>, <span class="yellow-code">Dialog</span>, <span class="yellow-code">Button</span>, <span class="yellow-code">Checkbox</span> 등 |
| <span class="blue-text">java.sql</span> | 데이터베이스 연동 | <span class="yellow-code">Connection</span>, <span class="yellow-code">Statement</span>, <span class="yellow-code">ResultSet</span> |
| <span class="blue-text">java.text</span> | 형식화/파싱 | <span class="yellow-code">SimpleDateFormat</span>, <span class="yellow-code">DecimalFormat</span> |


#### Java 주요 메소드

<table>
<tr>
<th>클래스</th>
<th>주요 메소드</th>
<th>기능</th>
</tr>
<tr>
<td rowspan="7"><span class="blue-text">String</span></td>
<td><span class="yellow-code">A.compareTo(B)</span></td>
<td>숫자로된 문자열 A와 B를 비교하여 같으면 0, A가 크면 1, B가 크면 -1을 반환</td>
</tr>
<tr>
<td><span class="yellow-code">A.equals(B)</span></td>
<td>문자열 A와 B가 같은지 비교 (대소문자 구분)</td>
</tr>
<tr>
<td><span class="yellow-code">A.equalsIgnoreCase(B)</span></td>
<td>문자열 A와 B가 같은지 비교 (대소문자 무시)</td>
</tr>
<tr>
<td><span class="yellow-code">toLowerCase(문자열)</span></td>
<td>문자열을 소문자로 변환</td>
</tr>
<tr>
<td><span class="yellow-code">toUpperCase(문자열)</span></td>
<td>문자열을 대문자로 변환</td>
</tr>
<tr>
<td><span class="yellow-code">split(구분자)</span></td>
<td>문자열을 구분자로 분리</td>
</tr>
<tr>
<td><span class="yellow-code">replaceAll(변환 대상, 변환할 문자)</span></td>
<td>문자열에서 특정 문자를 다른 문자로 변환</td>
</tr>
<tr>
<td rowspan="3"><span class="blue-text">StringTokenizer</span></td>
<td><span class="yellow-code">countTokens()</span></td>
<td>토큰의 개수를 반환</td>
</tr>
<tr>
<td><span class="yellow-code">hasMoreTokens()</span></td>
<td>다음 토큰이 있는지 확인</td>
</tr>
<tr>
<td><span class="yellow-code">nextToken()</span></td>
<td>다음 토큰을 반환</td>
</tr>
</table>

> 💡 **팁**: <span class="blue-text">Java는 패키지 단위로 라이브러리를 제공</span>하며, <span class="yellow-code">import</span>로 선언 후 클래스.메소드() 형태로 사용합니다! ☕

### Python의 주요 표준 라이브러리

Python은 <span class="blue-text">Java와 동일하게 라이브러리를 패키지로 제공</span>한다.  
Python에서 라이브러리를 사용하려면 <span class="yellow-code">import random</span>과 같이 선언한다.  
사용할 때는 마침표로 구분하여 <span class="yellow-code">random.choice()</span>와 같이 사용한다.

#### Python 주요 모듈

| 모듈 | 기능 | 주요 함수 |
|------|------|-----------|
| <span class="blue-text">내장 함수</span> | Python에 기본적인 인터페이스로, import문이나 클래스명 없이도 사용 | <span class="yellow-code">abs()</span>, <span class="yellow-code">slice()</span>, <span class="yellow-code">pow()</span>, <span class="yellow-code">print()</span> 등 |
| <span class="blue-text">os</span> | 운영체제와 상호 작용하기 위한 기능 제공 | <span class="yellow-code">getcwd()</span>, <span class="yellow-code">chdir()</span>, <span class="yellow-code">system()</span> 등 |
| <span class="blue-text">re</span> | 고급 문자열 처리를 위한 기능 제공 | <span class="yellow-code">findall()</span>, <span class="yellow-code">sub()</span> 등 |
| <span class="blue-text">math</span> | 복잡한 수학 연산을 위한 기능 제공 | <span class="yellow-code">cos()</span>, <span class="yellow-code">log()</span> 등 |
| <span class="blue-text">random</span> | 무작위 선택을 위한 기능을 제공 | <span class="yellow-code">choice()</span>, <span class="yellow-code">sample()</span>, <span class="yellow-code">random()</span>, <span class="yellow-code">randrange()</span> 등 |
| <span class="blue-text">statistics</span> | 통계값 산출을 위한 기능을 제공 | <span class="yellow-code">mean()</span>, <span class="yellow-code">median()</span>, <span class="yellow-code">variance()</span> 등 |
| <span class="blue-text">datetime</span> | 날짜와 시간 조작을 위한 기능을 제공 | <span class="yellow-code">today()</span>, <span class="yellow-code">date()</span>, <span class="yellow-code">strftime()</span> 등 |

> 💡 **팁**: <span class="blue-text">Python은 모듈 단위로 라이브러리를 제공</span>하며, <span class="yellow-code">import</span>로 선언 후 모듈.함수() 형태로 사용합니다! 🐍

### 주요 수학 함수 (C, Java, Python 공통)

| 함수명 | 기능 | 사용 예시 |
|--------|------|-----------|
| <span class="yellow-code">pow(x, y)</span> | x의 y제곱을 계산 | pow(2, 3) = 8 |
| <span class="yellow-code">sqrt(x)</span> | x의 제곱근을 계산 | sqrt(16) = 4 |
| <span class="yellow-code">abs(x)</span> | x의 절댓값을 계산 | abs(-5) = 5 |
| <span class="yellow-code">log(x)</span> | x의 자연로그를 계산 | log(e) = 1 |
| <span class="yellow-code">log10(x)</span> | x의 상용로그를 계산 | log10(100) = 2 |
| <span class="yellow-code">ceil(x)</span> | x보다 크거나 같은 가장 작은 정수 | ceil(3.2) = 4 |

> 💡 **팁**: <span class="blue-text">수학 함수는 대부분의 프로그래밍 언어에서 공통으로 제공</span>되며, <span class="blue-text">수학적 계산에 필수적</span>입니다! 🧮

### 난수 발생 함수

| 언어 | 함수명 | 기능 | 사용 예시 |
|------|--------|------|-----------|
| <span class="blue-text">C</span> | <span class="yellow-code">rand()</span> | 0부터 RAND_MAX까지의 난수 생성 | rand() % 100 (0~99) |
| <span class="blue-text">Java</span> | <span class="yellow-code">random()</span> | 0.0부터 1.0까지의 실수 난수 생성 | Math.random() * 100 |
| <span class="blue-text">Python</span> | <span class="yellow-code">random()</span> | 0.0부터 1.0까지의 실수 난수 생성 | random.random() * 100 |

#### 언어별 난수 발생 특징
* <span class="blue-text">C</span>: 정수형 난수 생성, 시드 설정 필요 (<span class="yellow-code">srand()</span>)
* <span class="blue-text">Java</span>: 실수형 난수 생성, <span class="yellow-code">Random</span> 클래스 사용
* <span class="blue-text">Python</span>: 실수형 난수 생성, 다양한 난수 함수 제공

> 💡 **팁**: <span class="blue-text">난수 발생 함수는 게임, 시뮬레이션, 암호화</span> 등에서 많이 사용되며, <span class="blue-text">언어별로 사용법이 다릅니다</span>! 🎲

## 2. 객체지향 프로그래밍 언어 :star:

### 객체지향 프로그래밍 언어의 개념

객체지향 프로그래밍 언어는 <span class="blue-text">현실 세계의 개체를 기계의 부품처럼 하나의 객체로 만들어 조립하여 제품을 만들 듯 소프트웨어를 개발할 때도 객체들을 조립해서 프로그램 작성</span>하는 언어이다.

**객체지향 프로그래밍의 특징**
* <span class="blue-text">프로시저보다는 명령과 데이터로 구성된 객체를 중심으로 하는 프로그래밍 기법</span>
* <span class="blue-text">명령과 데이터로 구성된 객체를 중심으로 하는 프로그래밍 기법</span>
* <span class="blue-text">한 프로그램을 다른 프로그램에서 이용 가능</span>

> 💡 **팁:**  객체지향의 4대 핵심 개념 : <span class="blue-text">추상화, 캡슐화, 상속, 다형성</span>

### 객체지향 프로그래밍 언어의 종류
<!-- 객체지향 프로그래밍 언어의 종류 (HTML Table) -->
<table>
  <thead>
    <tr>
      <th>언어</th>
      <th>특징</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><span class="blue-text">Java</span></td>
      <td>분산 네트워크 환경에 적용 가능, 멀티스레드 기능을 제공하여 여러 작업을 동시에 처리 가능, 운영체제 및 하드웨어에 독립적이며, 이식성이 강함</td>
    </tr>
    <tr>
      <td><span class="blue-text">C++</span></td>
      <td>C언어에 객체지향 개념을 도입, 모든 문제를 객체로 모델링하여 표현</td>
    </tr>
    <tr>
      <td><span class="blue-text">Smalltalk</span></td>
      <td>1세대 객체지향 프로그래밍 언어, 최초의 GUI 제공</td>
    </tr>
  </tbody>
</table>
- <small> 객체지향 언어 : Java, C++, Python, C#, Ruby, Kotlin, JavaScript </small> <br>

> 💡 **팁**: <span class="blue-text">객체지향 프로그래밍은 코드의 재사용성과 유지보수성을 높여주는</span> 현대적인 프로그래밍 패러다임입니다! 🎯

## 3. 스크립트 언어 :star::star:

스크립트 언어는 <span class="blue-text">HTML 문서 안에 직접 프로그래밍 언어를 삽입하여 사용하는 언어</span>이다.

* <span class="blue-text">기계어로 컴파일되지 않고 별도의 번역기가 소스를 분석하여 동작</span> → 인터프리터 언어
* <span class="blue-text">게시판 입력, 상품 검색, 회원 가입 등과 같은 데이터베이스 처리 작업을 수행하기 위해 주로 사용</span>

### 스크립트 언어의 분류

| 분류 | 내용 | 종류 |
|------|------|------|
| <span class="blue-text">서버용</span> | 서버에서 해석되어 실행된 후 결과만 클라이언트로 보냄 | <span class="yellow-code">ASP</span>, <span class="yellow-code">JSP</span>, <span class="yellow-code">PHP</span>, <span class="yellow-code">파이썬</span> |
| <span class="blue-text">클라이언트용</span> | 클라이언트의 웹 브라우저에서 해석되어 실행됨 | <span class="yellow-code">자바 스크립트</span>, <span class="yellow-code">VB 스크립트</span> |

### 스크립트 언어의 종류

| 언어 | 특징 |
|------|------|
| <span class="blue-text">자바 스크립트</span> | 웹 페이지의 동작을 제어하는 데 사용되는 클라이언트용 스크립트 |
| <span class="blue-text">VB 스크립트</span> | 마이크로소프트 사에서 자바 스크립트에 대응하기 위해 제작한 언어, Active X를 사용하여 마이크로소프트 사의 애플리케이션 컨트롤 |
| <span class="blue-text">ASP</span> | 서버 측에서 동적으로 수행되는 페이지를 만들기 위한 언어, 마이크로소프트 사에서 제작, Windows 계열에서만 수행 가능 |
| <span class="blue-text">JSP</span> | Java로 만들어진 서버용 스크립트 언어, 다양한 운영체제에서 사용 가능 |
| <span class="blue-text">PHP</span> | Linux, Unix, Windows 운영체제에서 사용 가능한 서버용 스크립트 언어, C, Java 등과 문법이 유사하여 배우기 쉬움 |
| <span class="blue-text">파이썬</span> | 객체지향 기능을 지원하는 대화형 인터프리터 언어, 플랫폼 독립적이고 문법이 간단함 |
| <span class="blue-text">쉘 스크립트</span> | 유닉스/리눅스 계열의 쉘에서 사용되는 명령어들의 조합으로 구성 |
| <span class="blue-text">Basic</span> | 절차지향 기능을 지원하는 대화형 인터프리터 언어, 초보자도 쉽게 배움 |

### XML, JSON, AJAX

**XML (eXtensible Markup Language)**
* <span class="blue-text">특수한 목적을 갖는 마크업 언어를 만드는 데 사용되는 다목적 마크업 언어</span>
* 웹 페이지의 기본 형식인 HTML의 문법이 각 웹 브라우저에서 상호 호환적이지 못하다는 문제와 SGML의 복잡함을 해결하기 위하여 개발

**JSON (JavaScript Object Notation)**
* <span class="blue-text">속성-값 쌍으로 이루어진 데이터 객체를 전달하기 위해 사람이 읽을 수 있는 텍스트를 사용하는 개방형 표준 포맷</span>
* 비동기 처리에 사용되는 AJAX에서 XML을 대체하여 사용되고 있음

**AJAX (Asynchronous JavaScript and XML)**
* <span class="blue-text">자바 스크립트 등을 이용하여 클라이언트와 서버 간에 XML 데이터를 교환 및 제어함으로써 이용자가 웹 페이지와 자유롭게 상호 작용할 수 있도록 하는 비동기 통신 기술</span>

> 💡 **팁**: <span class="blue-text">스크립트 언어는 웹 개발의 핵심</span>이며, <span class="blue-text">서버용과 클라이언트용으로 구분</span>하여 사용됩니다! 🌐
