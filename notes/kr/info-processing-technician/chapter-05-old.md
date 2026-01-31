---
layout: article
title: 5. C 언어
permalink: /notes/kr/info-processing-technician/chapter-05
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기능사 실기 강의 노트, C 언어 개념과 활용 방법을 다룹니다.
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

<script>
    function checkVariableAnswer() {
        answer = [true, false, false, true, false, true, true, true]
        userAnswer = []

        data = document.getElementsByClassName("variable-answer");

        for (let i = 0; i < data.length; i++) {
            userAnswer.push(data[i].checked);
        }

        const button = document.getElementById("variableAnswerButton");
        const resultDiv = document.getElementById("variableAnswerResult");
        
        if (userAnswer.every((value, index) => {
            return value === answer[index];
        })) {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #448F52; font-weight: bold;">정답입니다.</span>';
        } else {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #D53C41; font-weight: bold;">오답입니다.</span>';
        }
    }

    function checkIfAnswer() {
        const answer = document.getElementById("if-answer").value.trim();

        const button = document.getElementById("if-answerButton");
        const resultDiv = document.getElementById("if-answerResult");

        if (answer === "a % 2 != 0") {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #448F52; font-weight: bold;">정답입니다.</span>';
        } else {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #D53C41; font-weight: bold;">오답입니다.</span>';
        }
    }

    function checkConditionAnswer() {
        const userAnswer = document.getElementById("condition-answer").value.trim();
        const correctAnswer = "1";
        
        const button = document.getElementById("condition-answerButton");
        const resultDiv = document.getElementById("condition-answerResult");
        
        if (userAnswer === correctAnswer) {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #448F52; font-weight: bold;">정답입니다.</span>';
        } else {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #D53C41; font-weight: bold;">오답입니다.</span>';
        }
    }

    function checkIncrementAnswer() {
        const userAnswer = document.getElementById("increment-answer").value.trim();
        const correctAnswer = "15";
        
        const button = document.getElementById("increment-answerButton");
        const resultDiv = document.getElementById("increment-answerResult");
        
        if (userAnswer === correctAnswer) {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #448F52; font-weight: bold;">정답입니다.</span>';
        } else {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #D53C41; font-weight: bold;">오답입니다.</span>';
        }
    }

    function checkBitwiseAnswer() {
        const userAnswer = document.getElementById("bitwise-answer").value.trim();
        const correctAnswer = "4";
        
        const button = document.getElementById("bitwise-answerButton");
        const resultDiv = document.getElementById("bitwise-answerResult");
        
        if (userAnswer === correctAnswer) {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #448F52; font-weight: bold;">정답입니다.</span>';
        } else {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #D53C41; font-weight: bold;">오답입니다.</span>';
        }
    }

    function checkRandAnswer() {
        const userAnswer = document.getElementById("rand-answer").value.trim().toLowerCase();
        const correctAnswer = "rand()";
        
        const button = document.getElementById("rand-answerButton");
        const resultDiv = document.getElementById("rand-answerResult");
        
        if (userAnswer === "rand()" || userAnswer === "rand") {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #448F52; font-weight: bold;">정답입니다.</span>';
        } else {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #D53C41; font-weight: bold;">오답입니다.</span>';
        }
    }

    function checkPriorityAnswer() {
        const userAnswer = document.getElementById("priority-answer").value.trim();
        const correctAnswer = "*, +, =";
        
        const button = document.getElementById("priority-answerButton");
        const resultDiv = document.getElementById("priority-answerResult");
        
        if (userAnswer === correctAnswer) {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #448F52; font-weight: bold;">정답입니다.</span>';
        } else {
            button.style.display = "none";
            resultDiv.innerHTML = '<span style="color: #D53C41; font-weight: bold;">오답입니다.</span>';
        }
    }
</script>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%EC%A0%95%EB%B3%B4%EC%B2%98%EB%A6%AC%EA%B8%B0%EB%8A%A5%EC%82%AC&reversal=false&textBg=false)

C언어는 <span class="blue-text">시스템 프로그래밍의 기초</span>가 되는 중요한 언어다.  
<span class="blue-text">변수, 자료형, 연산자, 제어문</span>을 잘 이해하면 더 복잡한 프로그램을 작성할 수 있다! 🚀

## 1. 순서도와 C언어의 기호 :star::star::star:

<div class="responsive-image-layout">
    <!-- 첫 번째 이미지 -->
    <figure class="image-item">
        <img src="/notes/assets/info-processing-technician/chapter-05-01.png" width="300px" alt="순서도와 C언어의 기본" class="image-style">
    </figure>
    
    <!-- 두 번째 이미지와 코드 블록 -->
    <div class="image-item">
        {% include code-with-image.html 
           image="/notes/assets/info-processing-technician/chapter-05-13.png" 
           image_alt="C언어 코드 예시"
           code_id="c-example-1" 
           code_content="#include &lt;stdio.h&gt;

int main() {
    int num;

    scanf(&quot;%d&quot;, &amp;num);

    if (num &gt; 0) {
        printf(&quot;양수&quot;);
    } else if (num &lt; 0) {
        printf(&quot;음수&quot;);
    } else {
        printf(&quot;0&quot;);
    }
    
    return 0;
}" %}
    </div>
</div>

<script src="/assets/js/code-copy.js"></script>

<style>
/* 이미지 스타일 */
.image-style {
    display: block;
    margin: 0 auto;
}

/* 반응형 이미지 레이아웃 */
.responsive-image-layout {
    display: flex;
    flex-direction: column;
    gap: 20px;
    margin: 20px 0;
}

.responsive-image-layout .image-item {
    text-align: center;
}

/* 데스크톱 레이아웃 (768px 이상) */
@media (min-width: 768px) {
    .responsive-image-layout {
        flex-direction: row;
        align-items: stretch;
    }
    
    .responsive-image-layout .image-item:first-child {
        flex-shrink: 0;
        display: flex;
        align-items: center;
        text-align: left;
    }
    
    .responsive-image-layout .image-item:last-child {
        flex: 1;
        min-width: 0;
        text-align: left;
    }
}
</style>

> 💡 **팁**: C언어 프로그램은 <span class="blue-text">main()</span> 함수부터 시작된다! 모든 실행문은 중괄호 {} 안에 작성한다! 🎯

### 주요 순서도 기호

<table>
    <tr style="text-align: center; background-color: #d9e6ff;">
        <th>기호</th>
        <th>의미</th>
        <th>용도</th>
    </tr>
    <tr>
        <td>
            <img src="/notes/assets/info-processing-technician/chapter-05-02.svg" width="50px" alt="흐름선">
        </td>
        <td>흐름선(Flowline)</td>
        <td>흐름의 방향을 표시</td>
    </tr>
    <tr>
        <td>
            <img src="/notes/assets/info-processing-technician/chapter-05-03.svg" width="50px" alt="단자">
        </td>
        <td>단자(Terminal)</td>
        <td>순서도의 시작과 끝 표시</td>
    </tr>
    <tr>
        <td>
            <img src="/notes/assets/info-processing-technician/chapter-05-04.svg" width="50px" alt="처리">
        </td>
        <td>처리(Process)</td>
        <td>연산이나 데이터 등의 처리 작업</td>
    </tr>
    <tr>
        <td>
            <img src="/notes/assets/info-processing-technician/chapter-05-05.svg" width="50px" alt="판단">
        </td>
        <td>판단(Decision)</td>
        <td>조건을 비교하여 조건에 맞는 경로 선택</td>
    </tr>
    <tr>
        <td>
            <img src="/notes/assets/info-processing-technician/chapter-05-06.svg" width="50px" alt="수동 입력">
        </td>
        <td>수동 입력(Manual Input)</td>
        <td>키보드를 이용한 수동 입력</td>
    </tr>
    <tr>
        <td>
            <img src="/notes/assets/info-processing-technician/chapter-05-07.svg" width="50px" alt="입∙출력">
        </td>
        <td>입∙출력(I/O)</td>
        <td>데이터의 입∙출력</td>
    </tr>
    <tr>
        <td>
            <img src="/notes/assets/info-processing-technician/chapter-05-08.svg" width="50px" alt="준비">
        </td>
        <td>준비(Preparation)</td>
        <td>변수 및 변수의 초기 값 선언</td>
    </tr>
    <tr>
        <td>
            <img src="/notes/assets/info-processing-technician/chapter-05-09.svg" width="50px" alt="연결">
        </td>
        <td>연결(Connector)</td>
        <td>순서도 내 흐름의 연결</td>
    </tr>
    <tr>
        <td>
            <img src="/notes/assets/info-processing-technician/chapter-05-10.svg" width="50px" alt="서류">
        </td>
        <td>서류(Document)</td>
        <td>서류를 이용한 출력</td>
    </tr>
    <tr>
        <td>
            <img src="/notes/assets/info-processing-technician/chapter-05-11.svg" width="50px" alt="서브루틴 호출">
        </td>
        <td>서브루틴 호출(Subroutine Call)</td>
        <td>서브루틴을 호출</td>
    </tr>
</table>

### C언어의 변수(Variable)

#### 실습 예제 2: 변수 선언과 사용

```c
#include <stdio.h>

int main()
{
    int age = 20;           // 나이
    float height = 175.5;   // 키
    char grade = 'A';       // 성적
    
    printf("나이: %d세\n", age);
    printf("키: %.1fcm\n", height);
    printf("성적: %c등급\n", grade);
    
    return 0;
}
```

#### 변수명 규칙
- 변수명에는 영문자, 숫자, _(언더바)만 사용할 수 있으며, 글자 수에는 제한이 없습니다.
- 변수명 중간에 공백(띄어쓰기)은 사용할 수 없습니다.
- 변수명은 대문자와 소문자를 구분합니다.
- 변수명의 첫 글자는 반드시 영문자 또는 _(언더바)로 시작해야 하며, 숫자로 시작할 수 없습니다.
- C언어의 예약어(예: int, if, for 등)는 변수명으로 사용할 수 없습니다.
- 변수 선언문 끝에는 반드시 세미콜론(;)을 붙여야 합니다.

#### 다음 중 사용 가능한 변수명을 모두 선택하세요:

- <input type="checkbox" class="variable-answer"> `my_var`
- <input type="checkbox" class="variable-answer"> `2nd_value`
- <input type="checkbox" class="variable-answer"> `user@home`
- <input type="checkbox" class="variable-answer"> `_count`
- <input type="checkbox" class="variable-answer"> `int`
- <input type="checkbox" class="variable-answer"> `total_score`
- <input type="checkbox" class="variable-answer"> `user_name`
- <input type="checkbox" class="variable-answer"> `MAX_VALUE`

<input type="button" id="variableAnswerButton" value="정답 보기" onclick="checkVariableAnswer()" style="background-color: #448F52; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; font-weight: bold;">
<div id="variableAnswerResult"></div>

> 💡 **팁**: C언어 예약어️   
> 자료형: char, int, float, double, long, short, unsigned, const, signed, auto, static, extern, register, typedef, struct, union, enum, void   
> 제어문: if, else, switch, case, default, for, while, do, break, continue, return, goto, try, catch, throw, finally   
> 연산자: sizeof

### C언어의 자료형(Data Type)

#### 실습 예제 3: 자료형별 사용법

```c
#include <stdio.h>

int main()
{
    char name = 'A';        // 문자형
    int age = 25;           // 정수형
    float height = 175.5;   // 실수형
    double weight = 70.8;   // 더블형
    
    printf("이름: %c\n", name);
    printf("나이: %d세\n", age);
    printf("키: %.1fcm\n", height);
    printf("몸무게: %.1fkg\n", weight);
    
    return 0;
}
```

#### C언어 자료형 전체 목록

<table>
    <tr style="text-align: center; background-color: #d9e6ff;">
        <th>종류</th>
        <th>자료형</th>
        <th>크기</th>
        <th>기억 범위</th>
    </tr>
    <tr>
        <td>문자</td>
        <td>char</td>
        <td>1 byte</td>
        <td>-128 ~ 127</td>
    </tr>
    <tr>
        <td>부호없는 문자</td>
        <td>unsigned char</td>
        <td>1 byte</td>
        <td>0 ~ 255</td>
    </tr>
    <tr>
        <td rowspan="4">정수</td>
        <td>short</td>
        <td>2 byte</td>
        <td>-32,768 ~ 32,767</td>
    </tr>
    <tr>
        <td>int</td>
        <td>4 byte</td>
        <td>-2,147,483,648 ~ 2,147,483,647</td>
    </tr>
    <tr>
        <td>long</td>
        <td>8 byte</td>
        <td>-9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807</td>
    </tr>
    <tr>
        <td>long long</td>
        <td>8 byte</td>
        <td>-9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807</td>
    </tr>
    <tr>
        <td rowspan="3">부호없는 정수</td>
        <td>unsigned short</td>
        <td>2 byte</td>
        <td>0 ~ 65,535</td>
    </tr>
    <tr>
        <td>unsigned int</td>
        <td>4 byte</td>
        <td>0 ~ 4,294,967,295</td>
    </tr>
    <tr>
        <td>unsigned long</td>
        <td>8 byte</td>
        <td>0 ~ 18,446,744,073,709,551,615</td>
    </tr>
    <tr>
        <td rowspan="3">실수</td>
        <td>float</td>
        <td>4 byte</td>
        <td>-3.402823466E+38 ~ 3.402823466E+38</td>
    </tr>
    <tr>
        <td>double</td>
        <td>8 byte</td>
        <td>-1.7976931348623157E+308 ~ 1.7976931348623157E+308</td>
    </tr>
    <tr>
        <td>long double</td>
        <td>16 byte</td>
        <td>-1.7976931348623157E+308 ~ 1.7976931348623157E+308</td>
    </tr>
</table>

### C언어의 표준 입출력 함수

#### 실습 예제 4: 입출력 함수 사용하기

```c
#include <stdio.h>

int main()
{
    char name[20];
    int age;
    float height;
    
    printf("이름을 입력하세요: ");
    scanf("%s", name);
    
    printf("나이를 입력하세요: ");
    scanf("%d", &age);
    
    printf("키를 입력하세요: ");
    scanf("%f", &height);
    
    printf("\n=== 입력된 정보 ===\n");
    printf("이름: %s\n", name);
    printf("나이: %d세\n", age);
    printf("키: %.1fcm\n", height);
    
    return 0;
}
```

#### scanf() 함수

**서식 문자열**

| 서식 문자열 | 의미 |
| --- | --- |
| %d | 정수형 10진수 |
| %u | 부호없는 정수형 10진수 |
| %o | 정수형 8진수 |
| %x | 정수형 16진수 |
| %c | 문자 |
| %s | 문자열 |
| %f | 실수 |
| %e | 지수형 실수 |
| %ld | 긴 정수형 10진수 |

> 💡 **팁**: 기타 입출력 함수   
> getchar(): 키보드로 한 문자를 입력받아 변수에 저장하는 함수   
> gets(): 키보드로 문자열을 입력받아 변수에 저장하는 함수   
> putchar(): 인수로 주어진 한 문자를 화면에 출력하는 함수   
> puts(): 인수로 주어진 문자열을 화면에 출력하는 함수

#### printf() 함수

| 제어문자 | 의미 | 예시 |
|----------|------|------|
| <span class="yellow-code">\n</span> | 줄바꿈 | `printf("안녕\n하세요")` |
| <span class="yellow-code">\t</span> | 탭 | `printf("이름\t나이")` |
| <span class="yellow-code">\r</span> | 캐리지 리턴 | `printf("진행률: 50%\r")` |

> 💡 **팁**: <span class="red-text">scanf()</span>에서는 변수 앞에 <span class="yellow-code">&</span>를 붙여야 한다! <span class="blue-text">printf()</span>에서는 &가 필요 없다! 🎯

### C언어의 연산자와 식

#### 실습 예제 5: 연산자 활용하기

```c
#include <stdio.h>

int main()
{
    int a = 10, b = 3;
    
    printf("=== 산술 연산자 ===\n");
    printf("%d + %d = %d\n", a, b, a + b);
    printf("%d - %d = %d\n", a, b, a - b);
    printf("%d * %d = %d\n", a, b, a * b);
    printf("%d / %d = %d\n", a, b, a / b);
    printf("%d %% %d = %d\n", a, b, a % b);
    
    printf("\n=== 관계 연산자 ===\n");
    printf("%d > %d = %d\n", a, b, a > b);
    printf("%d == %d = %d\n", a, b, a == b);
    printf("%d != %d = %d\n", a, b, a != b);
    
    printf("\n=== 논리 연산자 ===\n");
    printf("(%d > 5) && (%d < 20) = %d\n", a, a, (a > 5) && (a < 20));
    printf("(%d < 5) || (%d > 20) = %d\n", a, a, (a < 5) || (a > 20));
    
    return 0;
}
```

#### 산술 연산자

| 산술 연산자 | 의미 |
| --- | --- |
| + | 덧셈 |
| - | 뺄셈 |
| * | 곱셈 |
| / | 나눗셈 |
| % | 나머지 |
| ++ | 증가 |
| -- | 감소 |

#### 기출문제 - 증가/감소 연산자 사용하기

```c
#include <stdio.h>

void main(void)
{
    int x=7;int y=7;int a;
    a=++x + y--;
    printf("%d\n",a);
}
```

답: <input type="text" id="increment-answer" placeholder="정답을 입력하세요">
<input type="button" id="increment-answerButton" value="정답 보기" onclick="checkIncrementAnswer()" style="background-color: #448F52; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; font-weight: bold;">
<div id="increment-answerResult"></div>

#### 관계 연산자

| 관계 연산자 | 의미 |
| --- | --- |
| == | 같음 |
| != | 다름 |
| > | 보다 큼 |
| >= | 보다 크거나 같음 |
| < | 보다 작음 |
| <= | 보다 작거나 같음 |

#### 비트 연산자

| 비트 연산자 | 의미 |
| --- | --- |
| & | 비트 AND |
| \| | 비트 OR |
| ^ | 비트 XOR |
| ~ | 비트 NOT |
| << | 비트 왼쪽 시프트 |
| >> | 비트 오른쪽 시프트 |

#### 기출문제 - 비트 연산자 사용하기

```c
int main()
{
    int a,b,result;
    a=7;b=4;
    result=a&b;
    printf("%d",result);
}
```

답: <input type="text" id="bitwise-answer" placeholder="정답을 입력하세요">
<input type="button" id="bitwise-answerButton" value="정답 보기" onclick="checkBitwiseAnswer()" style="background-color: #448F52; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; font-weight: bold;">
<div id="bitwise-answerResult"></div>

#### 논리 연산자

| 논리 연산자 | 의미 |
| --- | --- |
| && | 모두 참이면 참 |
| \|\| | 하나라도 참이면 참 |
| ! | 참이면 거짓, 거짓이면 참 |

#### 대입 연산자

| 대입 연산자 | 의미 |
| --- | --- |
| = | 대입 |

#### 조건 연산자

```c
조건 ? 참일 때 실행할 코드 : 거짓일 때 실행할 코드
```

#### 기출문제 - 조건 연산자 사용하기

```c
int main(void)
{
    ina a = 15;

    printf("%d", a > 10 ? 1 : 0);

    return 0;
}
```

답: <input type="text" id="condition-answer" placeholder="정답을 입력하세요">
<input type="button" id="condition-answerButton" value="정답 보기" onclick="checkConditionAnswer()" style="background-color: #448F52; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; font-weight: bold;">
<div id="condition-answerResult"></div>

#### 기타 연산자

| 기타 연산자 | 의미 |
| --- | --- |
| sizeof | 변수의 크기를 반환 |
| ,(콤마) | 콤마로 구분된 식을 순차적으로 실행 |

#### 연산자 우선순위

<table>
    <tr style="text-align: center; background-color: #d9e6ff;">
        <th>대분류</th>
        <th>중분류</th>
        <th>연산자</th>
        <th>결합규칙</th>
    </tr>
    <tr>
        <td>단항 연산자</td>
        <td>단항 연산자</td>
        <td>!(논리 not) ~(비트 not) ++(증가) --(감소)</td>
        <td>←</td>
    </tr>
    <tr>
        <td rowspan="7">이항 연산자</td>
        <td rowspan="2">산술 연산자</td>
        <td>*(곱셈) /(나눗셈) %(나머지)</td>
        <td rowspan="8">→</td>
    </tr>
    <tr>
        <td>+(덧셈) -(뺄셈)</td>
    </tr>
    <tr>
        <td>시프트 연산자</td>
        <td>&gt;&gt; (오른쪽 시프트) &lt;&lt; (왼쪽 시프트)</td>
    </tr>
    <tr>
        <td rowspan="2">관계 연산자</td>
        <td>&gt; (보다 큼) &lt; (보다 작음) &gt;= (보다 크거나 같음) &lt;= (보다 작거나 같음)</td>
    </tr>
    <tr>
        <td>== (같음) != (다름)</td>
    </tr>
    <tr>
        <td>비트 연산자</td>
        <td>&amp; (비트 AND) | (비트 OR) ^ (비트 XOR)</td>
    </tr>
    <tr>
        <td>논리 연산자</td>
        <td>&amp;&amp; (논리 AND) || (논리 OR) ! (논리 NOT)</td>
    </tr>
    <tr>
        <td>삼항 연산자</td>
        <td>조건 연산자</td>
        <td>? : (조건 연산자)</td>
    </tr>
    <tr>
        <td>대입 연산자</td>
        <td>대입 연산자</td>
        <td>
            = (대입) <br>
            += (더한 후 대입) <br>
            -= (뺀 후 대입) <br>
            *= (곱한 후 대입) <br>
            /= (나눈 후 대입) <br>
            %= (나머지 대입) <br>
            <<= (왼쪽 시프트 후 대입) <br>
            >>= (오른쪽 시프트 후 대입) <br>
        </td>
        <td>←</td>
    </tr>
    <tr>
        <td>순서 연산자</td>
        <td>순서 연산자</td>
        <td>, (콤마)</td>
        <td>→</td>
    </tr>
</table>

> 💡 **팁**: 연산자 우선순위는 <span class="blue-text">수학의 연산 순서</span>와 유사합니다! 괄호를 사용하면 명확하게 표현할 수 있습니다! 🧮

#### 기출문제 - 연산자 우선순위

다음 연산자들을 우선순위가 높은 순서대로 나열하세요: `*`, `+`, `=`

답: <input type="text" id="priority-answer" placeholder="예: *, +, =">
<input type="button" id="priority-answerButton" value="정답 보기" onclick="checkPriorityAnswer()" style="background-color: #448F52; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; font-weight: bold;">
<div id="priority-answerResult"></div>

> 💡 **해설**: 
> - `*` (곱셈): 산술 연산자로 우선순위 높음
> - `+` (덧셈): 산술 연산자로 곱셈보다 낮음
> - `=` (대입): 대입 연산자로 가장 낮음

## 2. C언어의 제어문 :star::star::star:

### if문 - 조건문

#### 실습 예제 6: 성적 등급 판정

```c
#include <stdio.h>

int main()
{
    int score;
    
    printf("점수를 입력하세요: ");
    scanf("%d", &score);
    
    if (score >= 90) {
        printf("A등급 - 우수!\n");
    } else if (score >= 80) {
        printf("B등급 - 양호\n");
    } else if (score >= 70) {
        printf("C등급 - 보통\n");
    } else if (score >= 60) {
        printf("D등급 - 미흡\n");
    } else {
        printf("F등급 - 재시험\n");
    }
    
    return 0;
}
```

#### if문 종류

| 종류 | 구조 | 용도 |
|------|------|------|
| <span class="blue-text">단순 if</span> | `if (조건) { 실행; }` | 조건이 참일 때만 실행 |
| <span class="blue-text">if-else</span> | `if (조건) { 실행1; } else { 실행2; }` | 참/거짓에 따라 분기 |
| <span class="blue-text">중첩 if</span> | `if (조건1) { if (조건2) { 실행; } }` | 조건 안에 조건 |
| <span class="blue-text">다중 if</span> | `if-else if-else` | 여러 조건 중 하나 선택 |

#### 기출문제 - if문 사용하기

<figure>
    <img src="/notes/assets/info-processing-technician/chapter-05-12.png" width="300px" alt="기출문제 - if문 사용하기">
</figure>

```c
#include <stdio.h>

int main()
{
    int a;

    scanf("%d", &a);

    if (__1__) {
        printf("짝수");
    } else {
        printf("홀수");
    }
}
```

<input type="text" id="if-answer" placeholder="정답을 입력하세요">
<input type="button" id="if-answerButton" value="정답 보기" onclick="checkIfAnswer()" style="background-color: #448F52; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; font-weight: bold;">
<div id="if-answerResult"></div>

### switch문 - 다중 선택

#### 실습 예제 7: 메뉴 선택 시스템

```c
#include <stdio.h>

int main()
{
    int choice;
    
    printf("=== 음식 메뉴 ===\n");
    printf("1. 햄버거\n");
    printf("2. 피자\n");
    printf("3. 치킨\n");
    printf("4. 파스타\n");
    printf("선택하세요 (1-4): ");
    scanf("%d", &choice);
    
    switch (choice) {
        case 1:
            printf("햄버거를 선택했습니다! 🍔\n");
            break;
        case 2:
            printf("피자를 선택했습니다! 🍕\n");
            break;
        case 3:
            printf("치킨을 선택했습니다! 🍗\n");
            break;
        case 4:
            printf("파스타를 선택했습니다! 🍝\n");
            break;
        default:
            printf("잘못된 선택입니다! 😅\n");
    }
    
    return 0;
}
```

### 반복문

#### 실습 예제 8: 구구단 출력기

```c
#include <stdio.h>

int main()
{
    int dan;
    
    printf("구구단을 출력할 단을 입력하세요: ");
    scanf("%d", &dan);
    
    printf("\n=== %d단 ===\n", dan);
    
    // for문 사용
    for (int i = 1; i <= 9; i++) {
        printf("%d × %d = %d\n", dan, i, dan * i);
    }
    
    return 0;
}
```

#### 반복문 종류

| 종류 | 구조 | 특징 |
|------|------|------|
| <span class="blue-text">for문</span> | `for (초기식; 조건식; 증감식)` | 횟수를 정확히 알 때 |
| <span class="blue-text">while문</span> | `while (조건)` | 조건이 참인 동안 반복 |
| <span class="blue-text">do-while문</span> | `do { 실행; } while (조건)` | 최소 한 번은 실행 |

#### break와 continue

```c
// break: 반복문을 즉시 종료
for (int i = 1; i <= 10; i++) {
    if (i == 5) break;  // 5에서 반복 종료
    printf("%d ", i);   // 1 2 3 4
}

// continue: 다음 반복으로 건너뛰기
for (int i = 1; i <= 5; i++) {
    if (i == 3) continue;  // 3을 건너뛰고 다음으로
    printf("%d ", i);      // 1 2 4 5
}
```

> 💡 **팁**: <span class="blue-text">break</span>는 반복문을 완전히 종료하고, <span class="blue-text">continue</span>는 현재 반복만 건너뛴다! 🎯

## 3. C언어의 포인터, 배열 :star::star::star:

### 포인터

변수는 기억 장소의 어느 위치에 대한 이름이다. 그 위치는 주소로도 표현 가능하다.  
C언어는 변수의 위치, 즉 주소를 제어할 수 있는 기능을 제공한다.

#### 실습 예제 9: 포인터 기본 사용법

```c
#include <stdio.h>

int main()
{
    int num = 100;        // 일반 변수
    int *ptr;             // 포인터 변수 선언
    
    ptr = &num;           // 포인터에 변수의 주소 저장
    
    printf("변수 num의 값: %d\n", num);
    printf("변수 num의 주소: %p\n", &num);
    printf("포인터 ptr이 가리키는 주소: %p\n", ptr);
    printf("포인터 ptr이 가리키는 값: %d\n", *ptr);
    
    // 포인터를 통한 값 변경
    *ptr = 200;
    printf("포인터로 변경한 후 num의 값: %d\n", num);
    
    return 0;
}
```

#### 포인터 사용법

| 단계 | 설명 | 예시 |
|------|------|------|
| <span class="blue-text">선언</span> | 포인터 변수 선언 | `int *ptr;` |
| <span class="blue-text">저장</span> | 주소를 포인터에 저장 | `ptr = &num;` |
| <span class="blue-text">참조</span> | *를 붙여 값 참조 | `*ptr = 100;` |

> 💡 **팁**: <span class="yellow-code">*</span>는 포인터 선언과 값 참조에 사용된다! <span class="yellow-code">&</span>는 주소를 가져올 때 사용한다! 🎯

### 배열

배열은 동일한 데이터 유형을 여러 개 사용하는 경우 이를 손쉽게 처리하기 위해 여러 개의 변수들을 조합해서 하나의 변수명으로 정의해 사용하는 것이다.

#### 1차원 배열

##### 실습 예제 10: 1차원 배열 사용법

```c
#include <stdio.h>

int main()
{
    int scores[5] = {85, 92, 78, 96, 88};  // 배열 선언과 초기화
    int sum = 0;
    
    printf("=== 학생 점수 ===\n");
    
    // 배열 출력
    for (int i = 0; i < 5; i++) {
        printf("학생 %d: %d점\n", i + 1, scores[i]);
        sum += scores[i];
    }
    
    printf("평균: %.1f점\n", (float)sum / 5);
    
    return 0;
}
```

##### 1차원 배열 형식

```c
자료형 배열명[크기];
자료형 배열명[크기] = {값1, 값2, 값3, ...};
```

#### 2차원 배열

##### 실습 예제 11: 2차원 배열 사용법

```c
#include <stdio.h>

int main()
{
    int matrix[3][4] = {
        {1, 2, 3, 4},
        {5, 6, 7, 8},
        {9, 10, 11, 12}
    };
    
    printf("=== 3x4 행렬 ===\n");
    
    // 2차원 배열 출력
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 4; j++) {
            printf("%3d ", matrix[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

##### 2차원 배열 형식

```c
자료형 배열명[행크기][열크기];
자료형 배열명[행크기][열크기] = { {값1, 값2}, {값3, 값4} };
```

#### 배열과 포인터의 관계

```c
#include <stdio.h>

int main()
{
    int arr[5] = {10, 20, 30, 40, 50};
    
    printf("배열 이름 arr: %p\n", arr);
    printf("첫 번째 요소 주소: %p\n", &arr[0]);
    printf("첫 번째 요소 값: %d\n", arr[0]);
    printf("포인터로 접근: %d\n", *arr);
    
    return 0;
}
```

> 💡 **팁**: 배열 이름은 첫 번째 요소의 주소를 가리키는 포인터다! <span class="blue-text">arr[i]</span>와 <span class="blue-text">*(arr + i)</span>는 같다! 🎯

## 4. C언어의 사용자 정의 함수 :star::star::star:

C언어는 함수 지향 언어로 처음 시작할 때 입력하는 main()도 함수다.  
함수에는 C언어에 내장되어 있는 내장 함수와 사용자가 만들어 사용하는 사용자 정의 함수가 있다.

### 사용자 정의 함수

사용자 정의 함수는 사용자가 필요한 기능을 취향대로 만들어 쓰는 함수다.

#### 실습 예제 12: 사용자 정의 함수 만들기

```c
#include <stdio.h>

// 함수 선언
int add(int a, int b);
void printMessage(char* message);

int main()
{
    int result = add(10, 20);
    printf("10 + 20 = %d\n", result);
    
    printMessage("안녕하세요! 사용자 정의 함수입니다.");
    
    return 0;
}

// 함수 정의
int add(int a, int b)
{
    return a + b;
}

void printMessage(char* message)
{
    printf("메시지: %s\n", message);
}
```

**함수 구조**

| 구성 요소 | 설명 | 예시 |
|-----------|------|------|
| <span class="blue-text">반환형</span> | 함수가 반환하는 데이터 타입 | `int`, `void`, `float` |
| <span class="blue-text">자료형</span> | 함수 이름 | `add`, `printMessage` |
| <span class="blue-text">매개변수</span> | 함수에 전달되는 값들 | `(int a, int b)` |
| <span class="blue-text">실행문</span> | 함수가 수행하는 작업 | `return a + b;` |

**재귀 함수**

재귀 함수는 함수가 자기 자신을 호출하는 함수다.

#### 실습 예제 13: 재귀 함수로 팩토리얼 계산

```c
#include <stdio.h>

int factorial(int n);

int main()
{
    int num;
    
    printf("팩토리얼을 계산할 숫자를 입력하세요: ");
    scanf("%d", &num);
    
    printf("%d! = %d\n", num, factorial(num));
    
    return 0;
}

int factorial(int n)
{
    if (n <= 1) {
        return 1;  // 기본 조건
    } else {
        return n * factorial(n - 1);  // 재귀 호출
    }
}
```

**재귀 함수의 특징**

- **기본 조건**: 재귀를 멈추는 조건 (n <= 1)
- **재귀 호출**: 자기 자신을 다시 호출 (factorial(n - 1))
- **스택 사용**: 함수 호출이 스택에 쌓임

> 💡 **팁**: 재귀 함수는 <span class="red-text">기본 조건</span>이 없으면 무한 반복에 빠진다! 반드시 종료 조건을 설정해야 한다! ⚠️

## 5. C언어의 라이브러리 함수

### rand() 함수 - 난수 생성

C언어에서 난수를 생성할 때 사용하는 함수입니다.

#### rand() 함수 사용법

```c
#include <stdio.h>
#include <stdlib.h>  // rand() 함수를 사용하기 위해 필요

int main()
{
    // 0부터 99까지의 난수 생성
    int random_num = rand() % 100;
    printf("난수: %d\n", random_num);
    
    return 0;
}
```

#### 특정 범위의 난수 생성

```c
// 1부터 70까지의 난수 생성
int random_num = 1 + (rand() % 70);
```

#### 기출문제 - rand() 함수 사용하기

다음은 C언어로 구현된 1~70까지의 난수를 구하는 프로그램이다. 빈 칸에 알맞은 라이브러리 함수를 입력하시오.

```c
int main()
{
    for(int i=0;i<10;i++)
        printf("%d\n",1+(       )%70);
}
```

답: <input type="text" id="rand-answer" placeholder="정답을 입력하세요">
<input type="button" id="rand-answerButton" value="정답 보기" onclick="checkRandAnswer()" style="background-color: #448F52; color: white; border: none; padding: 10px 20px; border-radius: 5px; cursor: pointer; font-weight: bold;">
<div id="rand-answerResult"></div>