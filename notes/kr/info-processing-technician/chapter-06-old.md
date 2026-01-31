---
layout: article
title: 6. Java, Python 프로그래밍 언어
permalink: /notes/kr/info-processing-technician/chapter-06
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기능사 실기 강의 노트, Java, Python 프로그래밍 언어 개념과 활용 방법을 다룹니다.
keywords: "정보처리기능사, 실기, 라이브러리, 프로그래밍 언어, 데이터 처리, 프로그래밍, Java, Python"
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

Java와 Python은 <span class="blue-text">객체지향 프로그래밍 언어</span>로 현대 소프트웨어 개발에서 널리 사용되는 언어다.  
<span class="blue-text">클래스, 객체, 메서드</span> 개념을 이해하면 더 효율적인 프로그램을 작성할 수 있다!

## 1. Java의 기초 :star::star::star:

> 💡 **전문가의 조언**: Java 프로그램의 범위는 정보처리기능사 실기 시험의 출제 범위에 맞춰 C언어와의 차이점에만 집중한다. C언어와 순서도를 먼저 학습한 후, C언어와의 차이점만 설명한다. C언어와 순서도에서 학습한 개념(알고리즘 등)은 재설명하지 않는다. 적절한 사전 지식 없이는 어려울 수 있다.

Java 프로그램은 C와 C++ 언어를 기반으로 하므로 문법이 거의 동일하다.  
정보처리기능사 실기 시험 범위 내에서 C 프로그램과의 차이점만 설명한다.

### 주요 차이점
- **배열**: 객체로 처리
- **문자열**: 클래스 제공
- **향상된 FOR문**: 객체용 반복문
- **클래스 사용**: 객체지향 프로그래밍

#### 예제: C와 Java 프로그램 비교

**C 프로그램**
{% include code-with-image.html 
   image="/notes/assets/info-processing-technician/chapter-06-01.png" 
   image_alt="C 프로그램 예제"
   code_id="c-program-example" 
   code_content="#include &lt;stdio.h&gt;

int main() {
    int i, j = 0;

    for (i = 1; i &lt; 5; i++) {
        j = j + i;
    }

    printf(&quot;%d %d&quot;, i, j);

    return 0;
}" %}

**Java 프로그램**
{% include code-with-image.html 
   image="/notes/assets/info-processing-technician/chapter-06-02.png" 
   image_alt="Java 프로그램 예제"
   code_id="java-program-example" 
   code_content="public class Problem {
    public static void main (String[] args) {
        int i, j = 0;

        for (i = 1; i &lt; 5; i++) {
            j = j + i;
        }

        System.out.printf(&quot;%d %d&quot;, i, j);
    }
}" %}

<script src="/assets/js/code-copy.js"></script>

> 💡 **참고**: 일단은 Java에서는 이렇게 시작하는구나? 정도로만 알아두기 바란다. 새로운 내용이 나올 때마다 그때그때 빼놓지 않고 자세히 설명할 것이다.

### 배열과 반복문

Java는 향상된 `for`문을 지원하며, 이는 객체를 위해 설계되었다.  
Java는 배열을 객체로 취급하며, 배열 작업에 필요한 기능들이 API로 제공된다.

#### 예제: 배열과 향상된 반복문

{% include code-with-image.html 
   image="/notes/assets/info-processing-technician/chapter-06-03.png" 
   image_alt="배열과 향상된 반복문"
   code_id="java-array-example" 
   code_content="public class Example {
    public static void main(String[] args) {
        int a[] = new int[5];
        int i;
        for (i = 0; i &lt; 5; i++) {
            a[i] = i + 10;
        }
        
        // 향상된 for문 사용
        for (int num : a) {
            System.out.printf(&quot;%4d&quot;, num);
        }
    }
}"%}

> 💡 **객체 변수**: 정확히는 힙 영역에 생성된 객체의 주소를 저장한다. Java에서는 주소를 직접 제어할 수 없으므로 객체 변수를 생성한다고 이해하면 된다.

### 문자열

C언어에서는 배열이나 포인터 변수를 이용해 문자열을 처리하지만, Java에서는 직접적인 주소 제어(포인터)가 불가능하다.  
대신 문자열 처리를 위한 클래스가 제공되며, 필요한 속성과 메서드들이 포함되어 있다.

#### 예제: 문자열을 거꾸로 출력하는 Java 프로그램

{% include code-with-image.html 
   image="/notes/assets/info-processing-technician/chapter-06-04.png" 
   image_alt="문자열을 거꾸로 출력하는 Java 프로그램"
   code_id="java-string-example" 
   code_content="public class Example {
    public static void main(String[] args) {
        String str = &quot;Information!&quot;
        int n = str.length();
        char[] st = new char [n];
        n--;

        for (int k = n; k &gt;= 0; k--) {
            st[n-k] = str.charAt(k);
        }

        for (char k : st) {
            System.out.printf(&quot;%c&quot;, k);
        }
    }
}"%}

## 2. Java의 활용 :star::star::star:

### 클래스와 함수

> 💡 **전문가의 조언**: Java는 객체지향 언어이므로 클래스가 중요하다. 이 책에서는 클래스를 간단히 다루지만, 클래스를 이해하는 것이 중요하다. 또한 Java와 C의 중요한 차이점은 반환값과 주소를 처리하는 방식이다. Java는 직접적인 주소 처리가 불가능하므로 여러 반환값을 처리하려면 클래스가 필수적이다.

클래스는 객체를 만들기 위한 설계도로, 필드(속성)와 함수(메서드)를 정의한다.  
아무리 작은 Java 프로그램이라도 클래스가 필요하다.

#### 클래스 사용 과정

1. **클래스명, 필드, 메서드 정의** (자동차 설계도 작성) → `class` 명령어 사용
2. **클래스로부터 객체 생성** (설계도로 자동차 제작) → `new` 명령어 사용하여 프로그램에서 사용 가능하게 함
3. **생성된 객체를 이용해 프로그램 코딩**

#### 예제 1: 클래스 생성과 객체 사용

```java
class ClassA {                    // A: 클래스 정의
    int a = 10;                   // B: 필드 정의
    int funcAdd(int x, int y) {   // C: 메서드 정의
        return x + y + a;         // 5: 메서드 내용
    }
}

public class Test {               // D: 실행 클래스
    public static void main(String[] args) { // E: main 메서드
        int x = 3, y = 6, r;     // 1: 변수 선언
        ClassA cal = new ClassA(); // 2: 객체 생성
        r = cal.funcAdd(x, y);    // 3: 메서드 호출
        System.out.print(r);      // 7: 결과 출력
    }
}
```

#### 실행 과정

**컴파일 과정 (A~C)**: 클래스/메서드 정의
**실행 과정 (1~7)**: 실제 프로그램 실행

> 💡 **전문가의 조언**: 컴파일은 컴퓨터 내부 과정이므로 사용자는 정의와 실행 흐름을 이해하는 데 집중하자. Java의 '메서드'와 C의 '함수'는 개념적으로 동일하며, 언어에 따른 용어 차이일 뿐이다.

### 클래스 구성 요소

| 구성 요소 | 설명 | 예시 |
|-----------|------|------|
| <span class="blue-text">클래스명</span> | 클래스의 이름 | `ClassA`, `Test` |
| <span class="blue-text">필드</span> | 클래스의 속성(변수) | `int a = 10;` |
| <span class="blue-text">메서드</span> | 클래스의 기능(함수) | `funcAdd(int x, int y)` |
| <span class="blue-text">객체</span> | 클래스의 인스턴스 | `ClassA cal = new ClassA();` |

### 메서드 호출

```java
// 객체 생성
ClassA cal = new ClassA();

// 메서드 호출
int result = cal.funcAdd(3, 6);
```

- **객체 생성**: `new` 키워드로 클래스의 인스턴스 생성
- **메서드 호출**: 객체명.메서드명(매개변수) 형태로 호출
- **반환값**: 메서드에서 `return`으로 값을 반환

> 💡 **팁**: Java는 <span class="blue-text">객체지향 프로그래밍</span>이므로 모든 것이 클래스와 객체를 중심으로 동작한다! C언어의 함수 개념을 Java에서는 메서드라고 부른다! 🎯

## 3. Python의 기초

### Python의 기본 문법

- 변수의 자료형에 대한 선언이 없다.
- 문장의 끝을 의미하는 세미콜론(;)을 사용할 필요가 없다.
- 변수에 연속하여 값을 저장하는 것이 가능하다.
    ```python
    x, y, z = 10, 20, 30
    ```
- `if`나 `for`와 같이 코드 블록을 포함하는 명령문을 작성할 때 코드 블록은 콜론 (:)과 여백으로 구분한다.
- 여백은 일반적으로 4칸 또는 한 개의 탭만큼 띄워야하며, 같은 수준의 코드들은 반드시 동일한 여백을 가져야 한다.

### Python의 데이터 입·출력 함수

#### input() 함수

- `input()` 함수는 Python의 표준 입력 함수로, 키보드로 입력받아 변수에 저장하는 함수이다.
- 입력되는 값은 문자열로 취급되어 저장된다.

**형식1**
```
변수 = input(출력문자)
```
- `'출력문자'`는 생략이 가능하며, `'변수'`는 사용자가 임의로 지정할 수 있다.
- 값을 입력하고 Enter를 누르면, 입력한 값이 `'변수'`에 저장된다.

**예제:**
```python
a = input("입력하세요.")
```
- 화면에 "입력하세요."가 출력되고 그 뒤에서 커서가 깜빡거리며 입력을 기다린다. 키보드로 값을 입력하면 변수 `a`에 저장된다.

**형식2**
```
변수1, 변수2,... = input(출력문자).split(분리문자)
```
- 화면에 '출력문자'가 표시되고 입력받은 값을 '분리문자'로 구분하여 각각 변수1, 변수2,-에 저장한다.
- '분리문자'를 생략하면 공백으로 값들을 구분한다.

**예제:**
```python
x, y = input().split('-')
```
- "gilbut-sinagong"을 입력할 경우, 분리문자 '-'를 기준으로 "gilbut"은 변수 `x`에 저장되고, "sinagong"은 변수 `y`에 저장된다.

#### print() 함수

**형식1: 기본 출력 및 sep, end 인자**
```python
print(출력값1, 출력값2, ..., sep = 분리문자, end = 종료문자)
```
- `'출력값'`에는 숫자, 문자, 문자열, 변수 등 다양한 값이나 식이 올 수 있습니다.
- `'sep'`는 여러 값을 출력할 때 값과 값 사이를 구분하기 위해 출력하는 문자로, 생략할 경우 기본값은 공백 한 칸(' ')입니다.
- `'end'`는 맨 마지막에 표시할 문자로, 생략할 경우 기본값은 줄 나눔입니다.

**예제:**
```python
print(82, 24, sep = '-', end = '')
```
**결과:** `82-24,`

**형식2: 서식 문자열을 이용한 출력**
```python
print(서식 문자열 % (출력값1, 출력값2, ...))
```
- C와 Java에서 사용했던 서식 문자열이 동일하게 적용됩니다.
- 출력값이 한 개일 경우 출력값에 대한 괄호를 생략할 수 있습니다.

**예제:**
```python
print("%-8.2f" % 200.20)
```
- `%`: 서식 문자열임을 지정
- `-`: 왼쪽부터 출력
- `8`: 출력 자릿수를 8자리로 지정
- `.2`: 소수점 이하를 2자리로 지정
- `f`: 실수로 출력

**결과:** `200.20  ` (8자리 폭에 왼쪽 정렬, 소수점 이하 2자리)

#### print() 함수 활용 예제

| 번호 | 코드 | 결과 |
|------|------|------|
| ① | `print(12, 34, 56)` | `12 34 56` |
| ② | `print('gilbut', 'sinagong', sep = '-')` | `gilbut-sinagong` |
| ③ | `print('help')`<br>`print('me')` | `help`<br>`me` |
| ④ | `print('help', end = '')`<br>`print('me')` | `help me` |
| ⑤ | `print('%3d' % 15)` | ` 15` |
| ⑥ | `print('%.3s%8.2f' % ('help me', 245.2555))` | `hel   245.26` |

### Python의 문자열

#### 문자열 메서드

| 형식 | 내용 |
|------|------|
| `upper()` | 대문자로 변경한다. |
| `lower()` | 소문자로 변경한다. |
| `capitalize()` | 문자열 첫 글자는 대문자, 나머지는 모두 소문자로 변경한다. |
| `title()` | 각 단어의 첫 글자만 대문자로 변경한다. |
| `replace(값1, 값2)` | 문자열에서 '값1'을 찾아 '값2'로 교체한다. |
| `split(값)` | '값'을 기준으로 문자열을 분리하여 리스트로 반환한다. '값'을 생략하면 공백으로 문자열을 분리한다. |
| `count(값)` | 문자열에서 '값'을 검색하여 '값'의 개수를 반환한다. |
| `find(값)` | 문자열에서 처음 검색되는 '값'의 위치를 반환한다. 찾지 못한 경우 -1을 반환한다. |
| `index(값)` | 문자열에서 처음 검색되는 '값'의 위치를 반환한다. 찾지 못한 경우 오류가 발생한다. |

**예제:**
- `'abc'.upper() → ABC`
- `'ABC'.lower() → abc`
- `'abc EFG'.capitalize() → Abc efg`
- `'abc efg'.title() → Abc Efg`
- `'abcde'.replace('c', 'o') → abode`
- `'ab-cd'.split('-') → ['ab', 'cd']`
- `'aababc'.count('b') → 2`
- `'abcd'.find('b') → 1`
- `'abcd'.index('b') → 1`

> 💡 **전문가의 조언**: Python에서 위치는 0부터 시작합니다. 그러므로 문자열 'abcd'에서 a의 위치는 0, b는 1, c는 2, d는 3 입니다.

### 리스트(List)

C와 Java에서는 여러 요소들을 한 개의 이름으로 처리할 때 배열을 사용했는데 Python에서는 리스트를 사용한다.
- 리스트는 필요에 따라 개수를 늘이거나 줄일 수 있기 때문에 리스트를 선언할 때 크기를 적지 않는다.
- 배열과 달리 하나의 리스트에 정수, 실수, 문자열 등 다양한 자료형을 섞어서 저장할 수 있다.
- Python에서 리스트의 위치는 0부터 시작한다.

#### 1차원 리스트

**형식**
- `리스트명 = [값1, 값2, ...]`
- `리스트명 = list([값1, 값2, ...])`

**예제 1: 리스트 생성 및 초기화**
- `방법1: a = [10, 'mike', 23.45]`
- `방법2: a = list([10, 'mike', 23.45])`

| | a[0] | a[1] | a[2] |
|---|---|---|---|
| 결과 리스트 a | 10 | mike | 23.45 |

**예제 2: 리스트 요소 값 변경**
- `a[0] = 1` (a[0]에 1을 저장한다.)

| | a[0] | a[1] | a[2] |
|---|---|---|---|
| 결과 리스트 a | 1 | mike | 23.45 |

**예제 3: 리스트에 요소 추가 (append)**
- `a.append('B Class')` (a 리스트의 마지막에 'B Class'를 추가한다.)

| | a[0] | a[1] | a[2] | a[3] |
|---|---|---|---|---|
| 결과 리스트 a | 1 | mike | 23.45 | B Class |

**예제 4: 리스트에 요소 삽입 (insert)**
- `a.insert(1, 'Brown')` (a 리스트의 두 번째(a[1]) 자리에 요소를 하나 삽입하여 "Brown"을 저장하고 그 이후의 요소들을 하나씩 뒤로 이동시킨다.)

| | a[0] | a[1] | a[2] | a[3] | a[4] |
|---|---|---|---|---|---|
| 결과 리스트 a | 1 | Brown | mike | 23.45 | B Class |

**예제 5: 리스트에서 요소 삭제 (del, remove)**
- `del a[3]` (a 리스트의 네 번째 요소(23.45)를 삭제하고, 그 이후의 요소들을 하나씩 앞으로 이동시킨다.)

| | a[0] | a[1] | a[2] | a[3] |
|---|---|---|---|---|
| 결과 리스트 a | 1 | Brown | mike | B Class |

- `a.remove('mike')` (a 리스트에서 "mike"를 찾아 해당 요소를 삭제하고, 이후의 요소들을 하나씩 앞으로 이동시킨다.)

| | a[0] | a[1] | a[2] |
|---|---|---|---|
| 결과 리스트 a | 1 | Brown | B Class |

#### 2차원 리스트

2차원 리스트는 리스트 안에 리스트가 저장된 형태이다.

**형식1**
```
리스트명 = [[값1, 값2, 값3 ], [값4. 값5, 값6]]
```

**형식2**
```
리스트A = [값1, 값2, 값3]
리스트B = [값4, 값5, 값6]
리스트명 = [리스트A, 리스트B]
```

**예제 1:**
```python
b = [[1,2,3], ['a','b','c']]
```

| | b[0][0] | b[0][1] | b[0][2] | b[1][0] | b[1][1] | b[1][2] |
|---|---|---|---|---|---|---|
| 결과 리스트 b | 1 | 2 | 3 | a | b | c |

**예제 2:**
```python
b[1][1] = 'f'
```

| | b[0][0] | b[0][1] | b[0][2] | b[1][0] | b[1][1] | b[1][2] |
|---|---|---|---|---|---|---|
| 결과 리스트 b | 1 | 2 | 3 | a | f | c |

#### 리스트 관련 주요 메서드

| 형식 | 내용 |
|------|------|
| `pop(위치)` | 지정된 '위치'의 값을 출력하고 해당 요소를 삭제한다. |
| `index(값)` | 리스트에서 지정된 '값'이 처음 나타나는 위치를 반환한다. |
| `count(값)` | 리스트에서 지정된 '값'과 같은 요소의 개수를 반환한다. |
| `extend(리스트)` | 리스트의 끝에 다른 '리스트'의 모든 요소를 추가한다. |
| `reverse()` | 리스트의 요소 순서를 뒤바꾼다. |
| `sort()` | 리스트를 정렬한다. 기본은 오름차순이며, 정렬 순서는 reverse 속성으로 지정할 수 있다. True는 내림차순, False는 오름차순이다. |
| `copy()` | 리스트의 얕은 복사본을 만든다. |

**예제:**
- `[10, 11, 12].pop(1) → 11 출력 → [10, 12]`
- `[10, 11, 12].index(12) → 2`
- `[1, 0, 1, 0, 0].count(0) → 3`
- `['a', 'b'].extend(['c', 'd']) → ['a', 'b', 'c', 'd']`
- `[1, 2, 3].reverse() → [3, 2, 1]`
- `[2, 1, 3].sort() → [1, 2, 3]`
- `[2, 1, 3].sort(reverse = True) → [3, 2, 1]`

### Range

Range는 연속된 숫자를 생성하는 것으로, 리스트, 반복문 등에서 많이 사용된다.

**형식**
- `range(최종값)`: 0에서 '최종값'-1까지 연속된 숫자를 생성한다.
- `range(초기값, 최종값)`: '초기값'에서 '최종값'-1까지 연속된 숫자를 생성한다.
- `range(초기값, 최종값, 증가값)`: '초기값'에서 '최종값'-1까지 '증가값'만큼 증가하면서 숫자를 생성한다. 증가값이 음수인 경우 '초기값'에서 '최종값'+1까지 '증가값'만큼 감소하면서 숫자를 생성한다.

**예제:**
- `a = list(range(5))` → `0, 1, 2, 3, 4`
- `a = list(range(4, 9))` → `4, 5, 6, 7, 8`
- `a = list(range(1, 15, 3))` → `1, 4, 7, 10, 13`
- `a = list(range(9, 4, -1))` → `9, 8, 7, 6, 5`

### 슬라이스(Slice)

슬라이스는 문자열이나 리스트와 같은 순차형 객체에서 일부를 잘라(slicing) 반환하는 기능이다.

**형식**
- `객체명[초기위치:최종위치]`: '초기위치'에서 '최종위치'-1까지의 요소들을 가져온다.
- `객체명[초기위치:최종위치:증가값]`: '초기위치'에서 '최종위치'-1까지 '증가값'만큼 증가하면서 해당 위치의 요소들을 가져온다. '증가값'이 음수인 경우 '초기위치'에서 '최종위치'+1까지 '증가값'만큼 감소하면서 해당 위치의 요소들을 가져온다.

**슬라이스 인수 생략**
- `객체명[:]` 또는 `객체명[::]`: 객체의 모든 요소를 반환한다.
- `객체명[초기위치:]`: 객체의 '초기위치'에서 마지막 위치까지의 요소들을 반환한다.
- `객체명[:최종위치]`: 객체의 0번째 위치에서 '최종위치'-1까지의 요소들을 반환한다.
- `객체명[::증가값]`: 객체의 0번째 위치에서 마지막 위치까지 '증가값'만큼 증가하면서 해당 위치의 요소들을 반환한다.

**예제:**
- `a=['a', 'b', 'c', 'd', 'e']`일 때
- `a[1:3] → ['b', 'c']`
- `a[0:5:2] → ['a', 'c', 'e']`
- `a[3:] → ['d', 'e']`
- `a[:3] → ['a', 'b', 'c']`
- `a[3] → ['a', 'd']`

**슬라이스 및 문자열 연산 예제**

| 번호 | 객체 | 코드 | 결과 |
|------|------|------|------|
| ① | `a = 'sinagong'` | `print(a[3:7])` | `agon` |
| ② | `a = list(range(10))` | `print(a[:7:2])` | `[0, 2, 4, 6]` |
| ③ | `a = 'hello, world'` | `print(a[7:])` | `world` |
| ④ | `a = list(range(5, 22, 2))` | `print(a[::3])` | `[5, 11, 17]` |
| ⑤ | `a = list(range(8))` | `print(a[2::2])` | `[2, 4, 6]` |
| ⑥ | `a = list(range(8, 3, -1))` | `print(a[:3])` | `[8, 7, 6]` |

> 💡 **전문가의 조언**: 각 객체의 첫 번째 요소는 위치가 0이고, `range`와 `slice`의 최종값이나 최종위치는 증가값에 따라 1 감소하거나 1 증가한 후 계산해야 한다는 것을 잊지 마세요.

### 조건문 (if문)

#### 형식1: 조건이 참일 때만 실행한다.
```python
if 조건:
    실행할 문장
```

**예제 1:**
```python
a = 15
if a > 10:
    a = a - 10
    print(a)
```
**결과:** 5

#### 형식2: 조건이 참일 때와 거짓일 때 실행할 문장이 다르다.
```python
if 조건:
    실행할 문장
else:
    실행할 문장
```

**예제 2:**
```python
a, b = 10, 20
if a > b:
    cha = a - b
    print(cha)
else:
    cha = b - a
    print(cha)
```
**결과:** 10

#### 형식3: 여러 조건 처리
```python
if 조건1:
    실행할 문장
elif 조건2:
    실행할 문장
else:
    실행할 문장
```

#### 형식4: if문 안에 if문이 포함된다.
```python
if 조건1:
    if 조건2:
        실행할 문장1
    else:
        실행할 문장2
else:
    실행할 문장3
```

**예제 4:**
```python
a, b = 21, 10
if a % 2 == 0:
    if b % 2 == 0:
        print('모두 짝수')
    else:
        print('a: 짝수, b: 홀수')
else:
    if b % 2 == 0:
        print('a: 홀수, b: 짝수')
    else:
        print('모두 홀수')
```
**결과:** `a: 홀수, b: 짝수`

### 반복문

#### for문

**형식1: range를 이용하는 방식**
```python
for 변수 in range(최종값):
    실행할 문장
```
- 0에서 '최종값'-1까지 연속된 숫자를 순서대로 변수에 저장하며 '실행할 문장'을 반복 수행합니다.

**예제 1:**
```python
for i in range(10):
    sum += i
```

**예제 2:**
```python
for i in range(11, 20):
    sum += i
```

**예제 3:**
```python
for i in range(-10, 20, 2):
    sum += i
```

**형식2: 리스트(List)를 이용하는 방식**
```python
for 변수 in 리스트:
    실행할 문장
```
- 리스트의 0번째 요소에서 마지막 요소까지 순서대로 변수에 저장하며 실행할 문장을 반복 수행합니다.

**예제:**
```python
a = [35, 55, 65, 84, 45]
hap = 0
for i in a:
    hap += i
avg = hap / len(a)
print(hap, avg)
```

#### while문

**형식**
```python
while 조건:
    실행할 문장
```

**예제:**
```python
i, hap = 0, 0
while i < 5:
    i += 1
    hap += i
print(hap)
```
**결과:** 15

**디버깅**

| i | hap |
|---|---|
| 0 | 0 |
| 1 | 1 |
| 2 | 3 |
| 3 | 6 |
| 4 | 10 |
| 5 | 15 |

### 클래스 (Class)

#### 정의 형식
```python
class 클래스명:
    실행할 문장
    def 메소드명(self, 인수):
        실행할 문장
        return 값
```

- `class`는 예약어로, 그대로 입력하고 클래스명은 사용자가 임의로 지정한다.
- `def`는 메소드를 정의하는 예약어로, 그대로 입력하고, 메소드명은 사용자가 임의로 지정한다.
- `self`는 클래스에 속한 메소드에 반드시 포함되어야 하는 예약어로, 그대로 적는다.
- `인수`는 메소드를 호출하는 곳에서 보낸 값을 저장할 변수로, 사용자가 임의로 지정한다.
- `return`은 메소드를 호출한 위치로 값을 돌려주기 위해 사용하는 예약어로, 그대로 입력한다. return 값이 없는 경우에는 생략할 수 있다.

#### 객체의 선언 형식
```python
변수명 = 클래스명()
```
- `변수명`은 사용자가 임의로 지정하고, 사전에 정의한 클래스명과 괄호()를 적는다.

**예제 1: 두 수를 교환하는 프로그램**
```python
class Cls:
    x, y = 10, 20
    def chg(self):
        temp = self.x
        self.x = self.y
        self.y = temp

a = Cls()
print(a.x, a.y)
a.chg()
print(a.x, a.y)
```

**예제 2: 0부터 10까지 더하는 프로그램**
```python
class Cls:
    def rep(self, r):
        hap = 0
        for i in range(r + 1):
            hap += i
        return hap

a = Cls()
b = a.rep(10)
print(b)
```
**결과:** 55

**디버깅**

| i | hap |
|---|---|
| 0 | 0 |
| 1 | 1 |
| 2 | 3 |
| 3 | 6 |
| ... | ... |
| 8 | 36 |
| 9 | 45 |
| 10 | 55 |

### 기출 따라잡기: Python 프로그램 분석

다음 Python으로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오.

```python
class CharClass:
    a = ["Seoul", "Incheon", "Kyonggi", "Daejun", "Daegu","Pusan"]
myVar = CharClass()
str01 = ''
for i in myVar.a:
    str01 = str01 + i[0]
print(str01)
```

## 4. Python의 활용

### if문

#### 형식1: 조건이 참일 때만 실행한다.
```python
if 조건:
    실행할 문장
```

**예제 1:**
```python
a = 15
if a > 10:
    a = a - 10
    print(a)
```
**결과:** 5

#### 형식2: 조건이 참일 때와 거짓일 때 실행할 문장이 다르다.
```python
if 조건:
    실행할 문장
else:
    실행할 문장
```

**예제 2:**
```python
a, b = 10, 20
if a > b:
    cha = a - b
    print(cha)
else:
    cha = b - a
    print(cha)
```
**결과:** 10

#### 형식3: 여러 조건 처리
```python
if 조건1:
    실행할 문장
elif 조건2:
    실행할 문장
else:
    실행할 문장
```

#### 형식4: if문 안에 if문이 포함된다.
```python
if 조건1:
    if 조건2:
        실행할 문장1
    else:
        실행할 문장2
else:
    실행할 문장3
```

**예제 4:**
```python
a, b = 21, 10
if a % 2 == 0:
    if b % 2 == 0:
        print('모두 짝수')
    else:
        print('a: 짝수, b: 홀수')
else:
    if b % 2 == 0:
        print('a: 홀수, b: 짝수')
    else:
        print('모두 홀수')
```
**결과:** `a: 홀수, b: 짝수`

### for문

#### 형식1: range를 이용하는 방식
```python
for 변수 in range(최종값):
    실행할 문장
```
- 0에서 '최종값'-1까지 연속된 숫자를 순서대로 변수에 저장하며 '실행할 문장'을 반복 수행합니다.

**예제 1:**
```python
for i in range(10):
    sum += i
```

**예제 2:**
```python
for i in range(11, 20):
    sum += i
```

**예제 3:**
```python
for i in range(-10, 20, 2):
    sum += i
```

#### 형식2: 리스트(List)를 이용하는 방식
```python
for 변수 in 리스트:
    실행할 문장
```
- 리스트의 0번째 요소에서 마지막 요소까지 순서대로 변수에 저장하며 실행할 문장을 반복 수행합니다.

**예제:**
```python
a = [35, 55, 65, 84, 45]
hap = 0
for i in a:
    hap += i
avg = hap / len(a)
print(hap, avg)
```

### while문

**형식**
```python
while 조건:
    실행할 문장
```

**예제:**
```python
i, hap = 0, 0
while i < 5:
    i += 1
    hap += i
print(hap)
```
**결과:** 15

**디버깅**

| i | hap |
|---|---|
| 0 | 0 |
| 1 | 1 |
| 2 | 3 |
| 3 | 6 |
| 4 | 10 |
| 5 | 15 |

### 클래스

#### 정의 형식
```python
class 클래스명:
    실행할 문장
    def 메소드명(self, 인수):
        실행할 문장
        return 값
```

- `class`는 예약어로, 그대로 입력하고 클래스명은 사용자가 임의로 지정한다.
- `def`는 메소드를 정의하는 예약어로, 그대로 입력하고, 메소드명은 사용자가 임의로 지정한다.
- `self`는 클래스에 속한 메소드에 반드시 포함되어야 하는 예약어로, 그대로 적는다.
- `인수`는 메소드를 호출하는 곳에서 보낸 값을 저장할 변수로, 사용자가 임의로 지정한다.
- `return`은 메소드를 호출한 위치로 값을 돌려주기 위해 사용하는 예약어로, 그대로 입력한다. return 값이 없는 경우에는 생략할 수 있다.

#### 객체의 선언 형식
```python
변수명 = 클래스명()
```
- `변수명`은 사용자가 임의로 지정하고, 사전에 정의한 클래스명과 괄호()를 적는다.

**예제 1: 두 수를 교환하는 프로그램**
```python
class Cls:
    x, y = 10, 20
    def chg(self):
        temp = self.x
        self.x = self.y
        self.y = temp

a = Cls()
print(a.x, a.y)
a.chg()
print(a.x, a.y)
```

**예제 2: 0부터 10까지 더하는 프로그램**
```python
class Cls:
    def rep(self, r):
        hap = 0
        for i in range(r + 1):
            hap += i
        return hap

a = Cls()
b = a.rep(10)
print(b)
```
**결과:** 55

**디버깅**

| i | hap |
|---|---|
| 0 | 0 |
| 1 | 1 |
| 2 | 3 |
| 3 | 6 |
| ... | ... |
| 8 | 36 |
| 9 | 45 |
| 10 | 55 |

### 기출 따라잡기: Python 프로그램 분석

다음 Python으로 구현된 프로그램을 분석하여 그 실행 결과를 쓰시오.

```python
class CharClass:
    a = ["Seoul", "Incheon", "Kyonggi", "Daejun", "Daegu","Pusan"]
myVar = CharClass()
str01 = ''
for i in myVar.a:
    str01 = str01 + i[0]
print(str01)
```

> 💡 **전문가의 조언**: Python에서의 클래스는 Java의 클래스와 동일한 개념입니다. 클래스에 대한 자세한 내용은 Section 028을 참조하세요.