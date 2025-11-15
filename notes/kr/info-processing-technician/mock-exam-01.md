---
layout: article
title: 모의고사 1
permalink: /notes/kr/info-processing-technician/mock-exam-01
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기능사 실기 모의고사 1 - 실전 대비 20문제
keywords: "정보처리기능사, 실기, 모의고사, 기출문제, C언어, Java, SQL, 데이터베이스, 네트워크, 운영체제"
---

<script src="/assets/js/quiz.js"></script>

<style>
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
    .note-box {
        background-color: #fff3cd;
        border-left: 4px solid #BD8739;
        padding: 15px;
        margin: 20px 0;
    }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%EB%AA%A8%EC%9D%98%EA%B3%A0%EC%82%AC%201&reversal=false&textBg=false)

## 📝 시험 안내

- **총 문항 수**: 20문제
- **배점**: 각 5점 (총 100점)
- **합격 기준**: 60점 이상
- **시험 시간**: 60분

<div class="note-box">
⚠️ <strong>답안 작성 시 주의사항</strong>
<ul>
<li>문제에서 <strong>영문 대문자로 작성</strong>하라는 지시가 있으면 반드시 대문자로 작성하세요</li>
<li>공백과 개행에 유의하여 정확히 작성하세요</li>
<li>프로그래밍 문제는 실행 결과를 정확히 작성하세요</li>
</ul>
</div>

---

## 문제

<div class="quiz-number">문제 1</div><strong>다음 C 프로그램의 실행 결과를 작성하세요.</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#include &lt;string.h&gt;
#include &lt;stdlib.h&gt;

int main()
{
    char str[] = "A C d  G h  K ! ";
    removeSpaces(str);
    printf("%s", str);
    return 0;
}

void removeSpaces(char str[])
{
    int len = strlen(str);
    char* result = (char*)malloc(sizeof(char) * len);
    int i, k = 0;

    for(i = 0; i &lt; len; i++)
    {
        if (str[i] != ' ')
            result[k++] = str[i];
    }

    result[k] = '\0';
    strcpy(str, result);
    free(result);
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   question=""
   code_html=code_block1
   answer="ACdGhK!"
   tags="C언어"
%}

---

<div class="quiz-number">문제 2</div><strong>다음 설명에 해당하는 용어를 영문 대문자로 작성하세요.</strong>

{% capture question2 %}
• 원격 서버에서 프로그램을 이용하여 이메일을 확인하기 위한 표준 프로토콜입니다.<br>
• 다중 기기 접속을 지원하기 때문에 여러 위치에서 이메일을 확인하고 관리할 수 있습니다.<br>
• 메일 서버에서 제목이나 발신자를 먼저 확인한 후 선택적으로 다운로드할 수 있습니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   question=question2
   answer="IMAP"
   tags="네트워크 기초 활용"
%}

---

<div class="quiz-number">문제 3</div><strong>Windows 10에서 컴퓨터를 잠그거나 사용자를 전환할 때 사용하는 단축키를 작성하세요.</strong>

{% include quiz-text.html
   id="quiz3"
   question=""
   answer="Win + L|Window + L|Winkey + L|윈도우 + L|win + l|window + l"
   tags="운영체제 기초 활용"
%}

---

<div class="quiz-number">문제 4</div><strong>OSI 7계층 중 네트워크 연결 관리, 데이터 교환 및 중계를 담당하며, ARP, IPX, IP 프로토콜과 관련된 계층을 작성하세요.</strong>

{% include quiz-text.html
   id="quiz4"
   question=""
   answer="네트워크계층|네트워크|네트워크 계층"
   tags="네트워크 기초 활용"
%}

---

<div class="quiz-number">문제 5</div><strong>다음 Java 프로그램의 실행 결과를 작성하세요. (공백과 개행에 주의)</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args){
        String text1 = "HELLOworld!";
        String text2 = "helloWORLD!";

        if (text1.equals(text2))
            System.out.print(text1.toUpperCase());
        else if (text1.equalsIgnoreCase(text2))
            System.out.print(text1.toLowerCase());
        else
            System.out.print(text2);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=""
   code_html=code_block5
   answer="helloworld!"
   tags="C언어"
%}

---

<div class="quiz-number">문제 6</div><strong>&lt;수강생&gt; 테이블에는 '수강생번호', '성명', '성적', '전공코드' 필드가 있고 &lt;전공&gt; 테이블에는 '전공코드', '전공명' 필드가 있으며, &lt;성적범위&gt; 테이블에는 '하한'과 '상한' 필드가 있을 때 '성적' 필드의 값이 &lt;성적범위&gt; 테이블의 '하한' 필드 값 이상이고 '상한' 필드 값 이하인 자료를 추출하려고 합니다. 다음 SQL문의 괄호에 알맞은 연산자를 영문 대문자로 작성하세요.</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT 수강생번호, 성명, 전공명
FROM 수강생, 전공, 성적범위
WHERE 수강생.전공코드 = 전공.전공코드
  AND 수강생.성적 (     ) 성적범위.하한 AND 성적범위.상한;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   question=""
   code_html=code_block6
   answer="BETWEEN"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 7</div><strong>다음 설명에 해당하는 용어를 작성하세요.</strong>

{% capture question7 %}
• UNIX 시스템에서 사용자 명령어를 인식하여 프로그램을 호출하고 명령을 실행하는 명령어 해석기입니다.<br>
• 명령을 해석하여 처리할 수 있도록 커널로 전달하는 명령 인터프리터로, 터미널을 통해 사용자로부터 명령어를 입력받습니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz7"
   question=question7
   answer="쉘|Shell|shell|SHELL"
   tags="운영체제 기초 활용"
%}

---

<div class="quiz-number">문제 8</div><strong>다음 C 프로그램의 실행 결과를 작성하세요.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
int main()
{
    int num = 25;
    printf("%o", num);
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8"
   question=""
   code_html=code_block8
   answer="31"
   tags="C언어"
%}

---

<div class="quiz-number">문제 9</div><strong>다음 C 프로그램의 실행 결과를 작성하세요.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int convertToBinary(int n)
{
    if (n == 0 || n == 1) printf("%d", n);
    else
    {
        convertToBinary(n/2);
        printf("%d", n%2);
    }
}

int main()
{
    int value = 15;
    convertToBinary(value);
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9"
   question=""
   code_html=code_block9
   answer="1111"
   tags="C언어"
%}

---

<div class="quiz-number">문제 10</div><strong>&lt;수강생&gt; 테이블에서 '전공' 별로 '수강료'의 평균을 구한 후 '평균수강료'라는 이름으로 표시하되, 전공을 기준으로 오름차순 정렬하려고 합니다. 다음 SQL문의 괄호에 알맞은 예약어를 영문 대문자로 작성하세요.</strong>

{% capture code_block10 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT 전공, (     )(수강료) AS 평균수강료
FROM 수강생
GROUP BY 전공
ORDER BY 전공 ASC;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz10"
   question=""
   code_html=code_block10
   answer="AVG"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 11</div><strong>도메인 이름을 IP 주소로 변환하는 시스템을 영문 대문자로 작성하세요.</strong>

{% include quiz-text.html
   id="quiz11"
   question=""
   answer="DNS|도메인 네임 시스템"
   tags="네트워크 기초 활용"
%}

---

<div class="quiz-number">문제 12</div><strong>다음 Java 프로그램의 실행 결과를 작성하세요. (공백과 개행에 주의)</strong>

{% capture code_block12 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test
{
    public static void main(String[] args) {
        String data = "a,b,c,d,,,e,f,g,,h,i";
        String[] parts = data.split(",");

        for(int i = 0; i &lt; parts.length; i++)
        {
            System.out.print(parts[i]);
            if ((i+1) % 3 == 0)
                System.out.println();
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz12"
   question=""
   code_html=code_block12
   answer="abc\nd\nefg\nhi"
   tags="C언어"
%}

---

<div class="quiz-number">문제 13</div><strong>다음 설명에 해당하는 용어를 영문으로 작성하세요.</strong>

{% capture question13 %}
• 후보키 중에서 특별히 선정된 키로 중복된 값을 가질 수 없습니다.<br>
• 유일성과 최소성을 가지며 튜플을 식별하기 위해 반드시 필요합니다.<br>
• NULL 값을 가질 수 없습니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz13"
   question=question13
   answer="Primary Key|primary key|기본키"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 14</div><strong>다음 Java 프로그램의 실행 결과를 작성하세요. (공백과 개행에 주의)</strong>

{% capture code_block14 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test
{
    public static void main(String[] args) {
        String text = "HELLO!@#2024/-";
        String output = text.replaceAll("[^ㄱ-ㅎㅏ-ㅣ가-힣a-zA-Z0-9,.]", "*");
        System.out.print(output);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz14"
   question=""
   code_html=code_block14
   answer="HELLO***2024**"
   tags="C언어"
%}

---

<div class="quiz-number">문제 15</div><strong>다음 설명에 해당하는 용어를 작성하세요.</strong>

{% capture question15 %}
• A, B, C 3개의 속성을 가진 릴레이션 R에서 어떤 복합 속성(A, C)에 대응하는 값의 집합이 A 값에만 종속되고 C 값에는 무관한 경우로, A ↠ B로 표기합니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz15"
   question=question15
   answer="다치종속|다중값종속"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 16</div><strong>다음 설명에 해당하는 용어를 작성하세요.</strong>

{% capture question16 %}
• 소프트웨어가 수행할 특정 작업을 알기 위해서 각 기능이 완전히 작동하는지 입증하는 테스트로, 기능 테스트라고도 합니다.<br>
• 프로그램의 구조를 고려하지 않기 때문에 테스트 케이스는 프로그램 또는 모듈의 요구사항이나 명세를 기초로 결정합니다.<br>
• 소프트웨어 인터페이스에서 실시되는 테스트입니다.<br>
• 부정확하거나 누락된 기능, 인터페이스 오류, 자료 구조나 외부 데이터베이스 접근에 따른 오류, 동작이나 성능 오류, 초기화와 종료 오류 등을 발견하기 위해 사용됩니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz16"
   question=question16
   answer="블랙박스|블랙박스테스트|블랙박스 테스트"
   tags="애플리케이션 테스트"
%}

---

<div class="quiz-number">문제 17</div><strong>Windows 10에서 화면 상단에 스크린샷 도구 바를 표시하는 단축키를 작성하세요.</strong>

{% include quiz-text.html
   id="quiz17"
   question=""
   answer="Win + Shift + S|Window + Shift + S|윈도우 + Shift + S"
   tags="운영체제 기초 활용"
%}

---

<div class="quiz-number">문제 18</div><strong>&lt;수강생&gt; 테이블을 대상으로 '전공코드' 값이 "IT"인 경우 "정보기술학과"라는 별칭으로 개수를 1씩 증가시키고, 전공코드 값이 "BZ"인 경우 "비즈니스학과"라는 별칭으로 개수를 1씩 증가시킨 후 출력하려고 합니다. 다음 SQL문의 괄호에 공통으로 들어갈 알맞은 명령을 영문 대문자로 작성하세요.</strong>

{% capture code_block18 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT
    COUNT((     ) WHEN 전공코드 = "IT" THEN 1 END) AS "정보기술학과",
    COUNT((     ) WHEN 전공코드 = "BZ" THEN 1 END) AS "비즈니스학과"
FROM 수강생;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz18"
   question=""
   code_html=code_block18
   answer="CASE"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 19</div><strong>다음 설명에 해당하는 스키마의 종류를 작성하세요.</strong>

{% capture question19 %}
물리적 저장 장치의 입장에서 본 데이터베이스 구조로서 실제로 데이터베이스에 저장될 레코드의 형식을 정의하고 저장 데이터 항목의 표현 방법, 내부 레코드의 물리적 순서 등을 나타냅니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz19"
   question=question19
   answer="내부스키마|내부 스키마"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 20</div><strong>다음 처리 조건을 준수하여 색인을 생성하는 SQL문의 괄호에 들어갈 알맞은 명령어를 영문 대문자로 작성하세요.</strong>

{% capture question20 %}
<strong>&lt;처리 조건&gt;</strong><br>
• 기본 테이블 S의 열(A, B, C)에 관한 조합으로 Y 색인을 생성합니다.<br>
• 색인 내용은 A(오름차순), B(내림차순), C(오름차순)입니다.<br>
• SQL 작성 시 UNIQUE, CLUSTER는 생략 가능합니다.
{% endcapture %}

{% capture code_block20 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE (      ) Y ON S(A, B DESC, C);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz20"
   question=question20
   code_html=code_block20
   answer="INDEX"
   tags="데이터베이스 기초 활용"
%}

---

## 💡 학습 팁

<div style="background-color: #e8f4f8; padding: 15px; border-radius: 8px; margin: 20px 0;">
<strong>📚 효과적인 모의고사 활용법</strong>
<ul>
<li><strong>실전처럼</strong>: 60분 제한 시간을 지켜 풀어보세요</li>
<li><strong>오답 노트</strong>: 틀린 문제는 반드시 개념을 다시 학습하세요</li>
<li><strong>반복 학습</strong>: 같은 유형의 문제를 여러 번 풀어보세요</li>
<li><strong>코드 실행</strong>: C언어와 Java 문제는 직접 컴파일하고 실행해보세요</li>
<li><strong>SQL 실습</strong>: 데이터베이스 문제는 실제 DB에서 실행해보세요</li>
</ul>
</div>

> 💪 **합격을 향한 첫걸음!** 모의고사를 통해 실전 감각을 익히고 약점을 보완하세요.
