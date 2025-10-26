---
layout: article
title: 실전 문제 연습
permalink: /notes/kr/info-processing-technician/quiz-practice
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기능사 실기 실전 문제 연습 - 다양한 유형의 문제를 풀어보세요.
keywords: "정보처리기능사, 실기, 문제풀이, 연습문제, C언어, 네트워크, 데이터베이스, 운영체제, 애플리케이션 테스트"
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
    .tag-filter-container {
        background-color: #f0f4f8;
        padding: 20px;
        border-radius: 10px;
        margin: 20px 0;
    }
    .tag-filter-btn {
        display: inline-block;
        padding: 8px 16px;
        margin: 5px;
        border: 2px solid #203BB0;
        background-color: white;
        color: #203BB0;
        border-radius: 20px;
        cursor: pointer;
        font-weight: bold;
        transition: all 0.3s;
    }
    .tag-filter-btn:hover {
        background-color: #e8f4f8;
        transform: translateY(-2px);
    }
    .tag-filter-btn.active {
        background-color: #203BB0;
        color: white;
    }
    #filter-stats {
        margin-top: 15px;
        font-size: 1.1em;
        color: #203BB0;
    }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%EC%8B%A4%EC%A0%84%20%EB%AC%B8%EC%A0%9C%20%EC%97%B0%EC%8A%B5&reversal=false&textBg=false)

정보처리기능사 실기 시험에 나올 수 있는 다양한 유형의 문제들을 연습해보세요! 💪

## 과목별 필터링

<div class="tag-filter-container">
    <div style="margin-bottom: 10px; font-weight: bold; color: #203BB0;">📚 과목 선택:</div>
    <button class="tag-filter-btn active" data-tag="" onclick="filterQuizByTag('')">전체</button>
    <button class="tag-filter-btn" data-tag="C언어" onclick="filterQuizByTag('C언어')">C언어</button>
    <button class="tag-filter-btn" data-tag="네트워크 기초 활용" onclick="filterQuizByTag('네트워크 기초 활용')">네트워크 기초 활용</button>
    <button class="tag-filter-btn" data-tag="데이터베이스 기초 활용" onclick="filterQuizByTag('데이터베이스 기초 활용')">데이터베이스 기초 활용</button>
    <button class="tag-filter-btn" data-tag="운영체제 기초 활용" onclick="filterQuizByTag('운영체제 기초 활용')">운영체제 기초 활용</button>
    <button class="tag-filter-btn" data-tag="애플리케이션 테스트" onclick="filterQuizByTag('애플리케이션 테스트')">애플리케이션 테스트</button>
    <div id="filter-stats"></div>
</div>

## 문제 풀이

<div class="quiz-number">문제 1</div><strong>C언어: 실행 결과를 쓰시오.</strong>

{% capture code_block %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int a = 8;
    int b = 12;
    int c = 25;
    int total = 0;
    a += b;
    b -= a;
    c %= b;
    total = a + b + c;
    printf("%d", total);
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-1"
   question=""
   code_html=code_block
   answer="13"
   tags="C언어"
%}

---

<div class="quiz-number">문제 2</div><strong>네트워크 토폴로지</strong>

{% capture choices_block %}
<div class="quiz-choices" style="margin-bottom: 15px; padding: 10px; background-color: #fff; border-left: 3px solid #203BB0;">
    <strong>보기</strong><br>
    ㉠ 버스(Bus)형<br>
    ㉡ 스타(Star)형<br>
    ㉢ 링(Ring)형<br>
    ㉣ 트리(Tree)형<br>
    ㉤ 메시(Mesh)형
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-2"
   question="모든 노드가 서로 직접 연결된 네트워크 구조로, 초기 구축 비용이 높지만 통신 신뢰도가 매우 우수하며, 대용량 데이터 전송에 적합한 토폴로지는?"
   choices_html=choices_block
   answer="㉤|메시|Mesh"
   tags="네트워크 기초 활용"
%}

---

<div class="quiz-number">문제 3</div><strong>데이터베이스 용어</strong>

{% capture choices_block3 %}
<div class="quiz-choices" style="margin-bottom: 15px; padding: 10px; background-color: #fff; border-left: 3px solid #203BB0;">
    <strong>보기</strong><br>
    ㉠ 도메인<br>
    ㉡ 차수<br>
    ㉢ 카디널리티<br>
    ㉣ 튜플<br>
    ㉤ 속성<br>
    ㉥ 릴레이션<br>
    ㉦ 관계<br>
    ㉧ 스키마
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-3-1"
   question="관계형 데이터베이스의 기본 구성 요소 중 하나로, 개체의 특성을 표현하며 테이블의 컬럼(Column)에 해당하는 것을 무엇이라고 하는가?"
   choices_html=choices_block3
   answer="㉤|속성"
   tags="데이터베이스 기초 활용"
%}

{% include quiz-text.html
   id="quiz-3-2"
   question="데이터베이스에서 여러 개체 간의 연관성을 표현하는 요소를 무엇이라고 하는가?"
   choices_html=choices_block3
   answer="㉦|관계"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 4</div><strong>UNIX 명령어</strong>

{% include quiz-text.html
   id="quiz-4"
   question="UNIX/Linux에서 현재 작업 중인 디렉토리의 파일 목록을 표시하는 명령어는?"
   answer="ls"
   tags="운영체제 기초 활용"
%}

---

<div class="quiz-number">문제 5</div><strong>IPv4 주소 체계</strong>

{% include quiz-text.html
   id="quiz-5"
   question="IPv4 주소 체계는 몇 비트(bit)로 이루어져 있는가?"
   answer="32"
   placeholder="숫자만 입력하세요"
   tags="네트워크 기초 활용"
%}

---

<div class="quiz-number">문제 6</div><strong>데이터베이스 모델</strong>

{% include quiz-text.html
   id="quiz-6"
   question="계층형 구조를 확장한 형태로, 하나의 자식 노드가 여러 개의 부모 노드를 가질 수 있는 네트워크 구조의 데이터베이스 모델은?"
   answer="NDBMS|Network DBMS|네트워크형 DBMS|망형 DBMS"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 7</div><strong>운영체제 시스템</strong>

{% capture choices_block7 %}
<div class="quiz-choices" style="margin-bottom: 15px; padding: 10px; background-color: #fff; border-left: 3px solid #203BB0;">
    <strong>보기</strong><br>
    ㉠ 일괄처리 시스템<br>
    ㉡ 다중 처리 시스템<br>
    ㉢ 실시간 처리 시스템<br>
    ㉣ 시분할 시스템<br>
    ㉤ 분산 처리 시스템
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-7"
   question="CPU를 일정 시간 단위로 분할하여 여러 사용자가 동시에 사용하는 것처럼 느끼게 하는 시스템으로, 멀티태스킹을 지원하는 시스템은?"
   choices_html=choices_block7
   answer="㉣|시분할|시분할 시스템"
   tags="운영체제 기초 활용"
%}

---

<div class="quiz-number">문제 8</div><strong>전송 계층 프로토콜</strong>

{% capture choices_block8 %}
<div class="quiz-choices" style="margin-bottom: 15px; padding: 10px; background-color: #fff; border-left: 3px solid #203BB0;">
    <strong>프로토콜 설명</strong><br><br>
    <strong>1.</strong> 연결 지향형 프로토콜로 신뢰성 있는 데이터 전송을 보장한다. 흐름 제어와 오류 제어를 수행하며, 3-way handshake 방식으로 연결을 수립한다. 웹(HTTP), 파일 전송(FTP) 등에 사용된다.<br><br>
    <strong>2.</strong> 비연결형 프로토콜로 빠른 데이터 전송이 특징이다. 신뢰성보다는 속도를 중시하며, 실시간 스트리밍이나 DNS 조회 등에 적합하다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-8"
   question="위 설명에 해당하는 프로토콜을 순서대로 작성하시오."
   choices_html=choices_block8
   answer="1. TCP, 2. UDP|TCP, UDP"
   placeholder="예: 1. TCP, 2. UDP"
   tags="네트워크 기초 활용"
%}

---

<div class="quiz-number">문제 9</div><strong>C언어: 출력 결과를 쓰시오.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    int i=0, j=0;
    int count=0;
    for (i=0; j&lt;5; j++) {
        if (i==j || (i+j)==4) {
            count++;
        }
    }
    printf("%d", count);
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-9"
   question=""
   code_html=code_block9
   answer="9"
   tags="C언어"
%}

---

<div class="quiz-number">문제 10</div><strong>Windows 단축키</strong>

{% capture choices_block10 %}
<div class="quiz-choices" style="margin-bottom: 15px; padding: 10px; background-color: #fff; border-left: 3px solid #203BB0;">
    <strong>단축키</strong><br>
    [Windows Key] + ( )<br><br>
    <strong>보기</strong><br>
    A   B   D   E   R   T   U   V
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-10"
   question="Windows에서 '실행' 대화상자를 여는 단축키는?"
   choices_html=choices_block10
   answer="R|r"
   placeholder="알파벳 한 글자 입력"
   tags="운영체제 기초 활용"
%}

---

<div class="quiz-number">문제 11</div><strong>데이터베이스 용어</strong>

{% include quiz-text.html
   id="quiz-11"
   question="속성(Attribute)이 가질 수 있는 값들의 집합으로, 각 속성값의 유효성을 검사하는 데 사용되는 것은 무엇인가?"
   answer="도메인|Domain"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 12</div><strong>OSI 7계층</strong>

{% capture choices_block12 %}
<div class="quiz-choices" style="margin-bottom: 15px; padding: 10px; background-color: #fff; border-left: 3px solid #203BB0;">
    <strong>계층의 주요 기능</strong><br><br>
    • 인접한 시스템 간 신뢰성 있는 데이터 전송을 담당한다.<br>
    • 프레임 단위로 데이터를 전송하며, MAC 주소를 사용한다.<br>
    • 흐름 제어, 오류 제어, 접근 제어 기능을 수행한다.<br>
    • 프레임의 시작과 끝을 구분하는 동기화 기능을 제공한다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-12"
   question="위 설명에 해당하는 OSI 7계층을 쓰시오."
   choices_html=choices_block12
   answer="데이터 링크 계층|Data Link Layer|데이터링크계층"
   tags="네트워크 기초 활용"
%}

---

<div class="quiz-number">문제 13</div><strong>사용자 인터페이스</strong>

{% include quiz-text.html
   id="quiz-13"
   question="마우스를 이용하여 아이콘, 메뉴, 버튼 등을 클릭하여 작업을 수행하는 그래픽 기반 인터페이스를 영문 약어로 쓰시오."
   answer="GUI"
   placeholder="영문 약어 입력"
   tags="운영체제 기초 활용"
%}

---

<div class="quiz-number">문제 14</div><strong>Java: 출력 결과를 쓰시오.</strong>

{% capture code_block14 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        MyClass mc = new MyClass();
        mc.print();
        mc.print("Hello");
    }
}

class MyClass {
    void print() {
        System.out.print("5678");
    }

    void print(int num) {
        System.out.print(++num);
    }

    void print(String str) {
        System.out.print("World");
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-14"
   question=""
   code_html=code_block14
   answer="5678World"
   tags="C언어"
%}

---

<div class="quiz-number">문제 15</div><strong>네트워크 관리 프로토콜</strong>

{% capture choices_block15 %}
<div class="quiz-choices" style="margin-bottom: 15px; padding: 10px; background-color: #fff; border-left: 3px solid #203BB0;">
    <strong>보기</strong><br>
    ㉠ TCP<br>
    ㉡ HTTP<br>
    ㉢ SGMP<br>
    ㉣ SNMP<br>
    ㉤ UDP
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-15"
   question="네트워크 장비를 관리하고 모니터링하기 위한 프로토콜로, 라우터, 스위치 등의 네트워크 정보를 수집하는데 사용되는 표준 프로토콜을 보기에서 찾아 기호로 쓰시오."
   choices_html=choices_block15
   answer="㉣|SNMP"
   tags="네트워크 기초 활용"
%}

---

<div class="quiz-number">문제 16</div><strong>C언어: 출력 결과를 쓰시오.</strong>

{% capture code_block16 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#define MAX 100

main() {
    int num = 1;
    int result = 0;
    while (num &lt;= MAX) {
        if ((num % 3) == 0 &amp;&amp; (num % 7) == 0) {
            result++;
            printf("%d#%d#", result, num);
        }
        num++;
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-16"
   question=""
   code_html=code_block16
   answer="1#21#2#42#3#63#4#84#"
   tags="C언어"
%}

---

<div class="quiz-number">문제 17</div><strong>Windows 화면 잠금</strong>

{% include quiz-text.html
   id="quiz-17"
   question="Windows 운영체제에서 컴퓨터 화면을 즉시 잠그는 단축키를 쓰시오."
   answer="Window Key + L|Win + L|Windows + L|window + l|win + l|windows + l"
   placeholder="예: Win + L"
   tags="운영체제 기초 활용"
%}

---

<div class="quiz-number">문제 18</div><strong>애플리케이션 테스트 원칙</strong>

{% include quiz-text.html
   id="quiz-18"
   question="소프트웨어에서 모든 결함을 제거하였다 하더라도 사용자의 요구를 만족시키지 못한다면 품질이 높다고 볼 수 없다는 테스트 원칙을 무엇이라고 하는가?"
   answer="오류-부재의 궤변"
   tags="애플리케이션 테스트"
%}

---

<div class="quiz-number">문제 19</div><strong>테스트 기본 원리</strong>

{% include quiz-text.html
   id="quiz-19"
   question="애플리케이션 결함의 80%가 전체 코드의 20%에서 발견된다는 경험적 법칙을 무엇이라고 하는가?"
   answer="파레토 법칙|파레토의 법칙"
   tags="애플리케이션 테스트"
%}

---

<div class="quiz-number">문제 20</div><strong>테스트 현상</strong>

{% include quiz-text.html
   id="quiz-20"
   question="다음 괄호에 들어갈 용어를 쓰시오.<br><br>동일한 테스트 케이스로 반복 테스트를 수행하면 더 이상 새로운 결함이 발견되지 않는 현상을 ( )라고 한다. 이를 방지하려면 테스트 케이스를 지속적으로 개선하고 업데이트해야 한다."
   answer="살충제 패러독스|살충제 페러독스"
   tags="애플리케이션 테스트"
%}

---

<div class="quiz-number">문제 21</div><strong>테스트 환경 요인</strong>

{% include quiz-text.html
   id="quiz-21"
   question="애플리케이션 테스트는 소프트웨어 특성, 테스트 환경, 테스터의 역량 등 ( )에 따라 결과가 달라질 수 있다. 괄호에 들어갈 용어를 쓰시오."
   answer="정황"
   tags="애플리케이션 테스트"
%}

---

<div class="quiz-number">문제 22</div><strong>목적별 테스트 분류</strong>

{% capture choices_block22 %}
<div class="quiz-choices" style="margin-bottom: 15px; padding: 10px; background-color: #fff; border-left: 3px solid #203BB0;">
    <strong>보기</strong><br>
    ㉠ 회복 테스트<br>
    ㉡ 안전 테스트<br>
    ㉢ 강도 테스트<br>
    ㉣ 성능 테스트<br>
    ㉤ 구조 테스트<br>
    ㉥ 회귀 테스트<br>
    ㉦ 병행 테스트
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-22"
   question="소프트웨어 내부의 논리적 경로와 소스 코드의 복잡도를 측정하고 평가하는 테스트를 보기에서 찾아 기호로 쓰시오."
   choices_html=choices_block22
   answer="㉤|구조 테스트"
   tags="애플리케이션 테스트"
%}

---

<div class="quiz-number">문제 23</div><strong>테스트 실행 방식</strong>

{% include quiz-text.html
   id="quiz-23"
   question="다음 괄호(①, ②)에 들어갈 테스트 용어를 순서대로 쓰시오.<br><br>프로그램 실행 여부에 따라 테스트는 ( ① )와 ( ② )로 구분된다. ( ① )는 프로그램을 실행하지 않고 명세서나 소스 코드를 검토하는 방식이며, ( ② )는 프로그램을 직접 실행하여 결함을 찾는 방식이다."
   answer="①정적 테스트 ②동적 테스트|①정적테스트 ②동적테스트"
   placeholder="예: ①정적 테스트 ②동적 테스트"
   tags="애플리케이션 테스트"
%}

---

<div class="quiz-number">문제 24</div><strong>화이트박스 테스트 기법</strong>

{% capture choices_block24 %}
<div class="quiz-choices" style="margin-bottom: 15px; padding: 10px; background-color: #fff; border-left: 3px solid #203BB0;">
    <strong>보기</strong><br>
    ∙ 제어 흐름 테스트<br>
    ∙ 분기(Branch) 테스트<br>
    ∙ 경계값 분석<br>
    ∙ 경로 테스트<br>
    ∙ 데이터 흐름 테스트<br>
    ∙ 동등 분할 테스트<br>
    ∙ 비교 테스트
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz-24"
   question="다음 보기에서 화이트박스 테스트 기법이 '아닌' 것을 모두 고르시오."
   choices_html=choices_block24
   answer="경계값 분석, 동등 분할 테스트, 비교 테스트"
   tags="애플리케이션 테스트"
%}

{% include quiz-text.html
   id="quiz-25"
   question="다음 보기에서 화이트박스 테스트 기법이 '아닌' 것을 모두 고르시오."
   choices_html=choices_block24
   answer="경계값 분석, 동등 분할 테스트, 비교 테스트"
   tags="애플리케이션 테스트"
%}

---

## 학습 팁 💡

<div style="background-color: #e8f4f8; padding: 15px; border-radius: 8px; margin: 20px 0;">
    <strong>📚 효과적인 문제 풀이 방법</strong>
    <ul>
        <li><strong>코드 문제</strong>: 한 줄씩 실행 흐름을 따라가며 변수 값의 변화를 추적하세요</li>
        <li><strong>용어 문제</strong>: 키워드를 중심으로 개념의 핵심 특징을 파악하세요</li>
        <li><strong>선택형 문제</strong>: 각 보기의 특징을 비교하며 소거법을 활용하세요</li>
        <li><strong>명령어 문제</strong>: 자주 사용되는 명령어는 반복 학습으로 암기하세요</li>
        <li><strong>애플리케이션 테스트</strong>: 테스트 원칙과 기법의 차이점을 명확히 구분하세요</li>
    </ul>
</div>

> 💪 **연습이 실력을 만듭니다!** 틀린 문제는 다시 한 번 복습하고, 관련 개념을 정리해보세요.
