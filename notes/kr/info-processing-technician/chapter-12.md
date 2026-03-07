---
layout: article
title: 11. 모의고사 1회 (프로그래밍기능사 실기)
permalink: /notes/kr/info-processing-technician/chapter-12
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - 모의고사 1회 (12문제)
keywords: "프로그래밍기능사, 실기, 모의고사, Python, Java, SQL, Linux, 경로"
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

# 모의고사 1회 Part 1

<div class="quiz-number">문제 1</div><strong>현재 작업 디렉터리의 절대 경로가 다음과 같을 때, 상대 경로로 제시된 디렉터리의 절대 경로를 쓰시오.</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>[작업폴더]
/srv/app/api/v2

[상대 경로]
../../../static/css</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_mock1"
   code_html=code_block1
   answer="/srv/static/css"
   tags="경로, 상대 경로"
%}

---

<div class="quiz-number">문제 2</div><strong>다음 각 기능에 해당하는 Linux 터미널 명령어를 &lt;보기&gt;에서 골라 쓰시오.</strong>

{% capture code_block2 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;보기&gt;</strong><br>
grep &nbsp; cp &nbsp; cat &nbsp; rmdir &nbsp; chmod &nbsp; ls &nbsp; mv &nbsp; pwd &nbsp; diff &nbsp; find
</div>
<div style="margin: 15px 0; line-height: 1.8;">
① 텍스트 파일에서 특정 문자열 패턴을 검색하는 명령어입니다.<br>
② 파일이나 디렉터리를 복사할 때 사용하는 명령어입니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_mock1"
   code_html=code_block2
   answer="grep, cp|grep,cp"
   tags="Linux, 명령어"
%}

---

<div class="quiz-number">문제 3</div><strong>&lt;ORDERS&gt; 테이블에 100자의 가변길이를 가진 'memo'라는 속성을 추가하는 SQL문을 작성하시오.</strong>

{% include quiz-text.html
   id="quiz3_mock1"
   answer="ALTER TABLE ORDERS ADD memo VARCHAR(100)"
   tags="SQL, DDL, ALTER"
%}

---

# 모의고사 1회 Part 2

<div class="quiz-number">문제 4</div><strong>다음은 &lt;교수&gt; 테이블과 &lt;강의&gt; 테이블을 조인(JOIN)한 결과이다. SQL의 괄호(①, ②)에 알맞은 항목을 적어 SQL문을 완성하시오.</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;교수&gt;

교번 | 이름   | 전공   | 직급
-----|--------|--------|------
201  | 강태호 | 컴퓨터 | 교수
202  | 박지수 | 수학   | 조교수
203  | 윤민준 | 영어   | 강사
204  | 이하나 | 물리   |

&lt;강의&gt;

교번 | 이름   | 과목명   | 학점
-----|--------|----------|------
201  | 강태호 | 자료구조 | 3
202  |        | 선형대수 | 3
203  | 윤민준 |          |
203  | 윤민준 | 영어회화 | 2

SELECT a.교번, 이름, 과목명, 학점
FROM 교수 a LEFT JOIN 강의 b
( ① ) a.교번 = b.( ② )</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_mock1"
   code_html=code_block4
   answer="ON, 교번|ON,교번"
   tags="SQL, JOIN, LEFT JOIN"
%}

---

<div class="quiz-number">문제 5</div><strong>다음 &lt;INVENTORY&gt; 테이블에서 품목별(item) 입고량(quantity)의 합계가 500 이상인 '품목명', '최소입고량', '최대입고량'을 조회하는 SQL문을 완성하시오. 괄호(①, ②)에 알맞은 항목을 쓰시오.</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT item, MIN(quantity) ( ① ) 최소입고량, MAX(quantity) ( ① ) 최대입고량
FROM INVENTORY
GROUP BY item
( ② ) SUM(quantity) >= 500</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_mock1"
   code_html=code_block5
   answer="AS, HAVING|AS,HAVING"
   tags="SQL, AS, HAVING"
%}

---

<div class="quiz-number">문제 6</div><strong>다음 Y1과 Y2 테이블에 대해 SQL문을 실행했을 때 출력되는 결과를 쓰시오.</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;Y1&gt;

 P  | Q
----|----
 B  | 12
 D  |  7
 F  |  3
 H  |  9

&lt;Y2&gt;

 P  | Q
----|----
 A  |  5
 D  | 14
 E  |  8
 H  |  6

SELECT AVG(Q) AS result
FROM Y2
WHERE P IN (SELECT P FROM Y1);</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: Y1의 P 값은 {B, D, F, H}이므로, Y2에서 이에 포함되는 행만 선택됩니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_mock1"
   code_html=code_block6
   answer="10"
   tags="SQL, IN, AVG"
%}

---

# 모의고사 1회 Part 3

<div class="quiz-number">문제 7</div><strong>다음 JAVA로 구현한 프로그램을 분석하여 그 실행 결과를 쓰시오.</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        int ans = (int)Math.pow(3, Math.floor(Math.PI));
        System.out.printf("%d", ans);
    }
}</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: <code>Math.PI</code> ≈ 3.14159..., <code>Math.floor()</code>는 소수점 이하를 버리며, <code>Math.pow(a, b)</code>는 a<sup>b</sup>를 반환합니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7_mock1"
   code_html=code_block7
   answer="27"
   tags="Java, Math"
%}

---

<div class="quiz-number">문제 8</div><strong>다음은 문자열에 숫자가 하나라도 포함되어 있는지, 문자열의 길이가 8 이상인지 검사하기 위한 Python 프로그램이다. 괄호(①, ②)에 들어갈 알맞은 코드를 쓰시오.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def is_valid_pw(pw):
    return (
        any(c.( ① )() for c in pw)
        and len(pw).( ② )(8)
    )

passwords = ['hello123', 'ab', 'secure99pass']
for pw in passwords:
    print(is_valid_pw(pw))</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: ①은 문자가 숫자인지 판별하는 메서드이며, ②는 <code>>=</code> 연산을 메서드로 표현한 것입니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8_mock1"
   code_html=code_block8
   answer="isdigit, __ge__|isdigit,__ge__"
   tags="Python, 문자열, 매직 메서드"
%}

---

<div class="quiz-number">문제 9</div><strong>다음 JAVA로 구현한 프로그램을 분석하여 그 실행 결과를 쓰시오.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    int value = 0;
    int run() {
        try {
            return 10;
        } finally {
            value = 20;
        }
    }
    public static void main(String[] args) {
        Solution obj = new Solution();
        System.out.print(obj.run());
    }
}</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: <code>try</code> 블록에서 <code>return</code>을 만나면, <code>finally</code> 블록이 실행된 후 반환값이 전달됩니다. 단, <code>finally</code>에서 반환값을 변경하지 않으면 원래 값이 반환됩니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_mock1"
   code_html=code_block9
   answer="10"
   tags="Java, try-finally"
%}

---

# 모의고사 1회 Part 4

<div class="quiz-number">문제 10</div><strong>다음 JAVA로 구현한 프로그램을 분석하여 그 실행 결과를 쓰시오.</strong>

{% capture code_block10 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    static class Shape {
        static String type() { return "Shape"; }
        String color() { return "white"; }
    }
    static class Circle extends Shape {
        static String type() { return "Circle"; }
        String color() { return "red"; }
    }
    public static void main(String[] args) {
        Shape obj = new Circle();
        System.out.println(obj.type() + obj.color());
    }
}</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: <code>static</code> 메서드는 참조 타입(Shape)에 바인딩되고, 인스턴스 메서드는 실제 객체 타입(Circle)에 바인딩됩니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz10_mock1"
   code_html=code_block10
   answer="Shapered"
   tags="Java, static, 다형성"
%}

---

<div class="quiz-number">문제 11</div><strong>다음 Python으로 구현한 프로그램을 분석하여 그 실행 결과를 쓰시오.</strong>

{% capture code_block11 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>nums = [2, 4, 6]
dct = {i: i * 3 for i in nums}
s = set(dct.values())
nums[0] = 10
dct[4] = 5
s.add(10)
print(len(s & set(dct.values())))</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: <code>&</code>는 두 집합의 교집합 연산입니다. 딕셔너리 값 변경이 기존 set에 영향을 주는지 주의하세요.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_mock1"
   code_html=code_block11
   answer="2"
   tags="Python, set, dictionary"
%}

---

<div class="quiz-number">문제 12</div><strong>다음 Python 프로그램에 대하여 다음 각 물음에 답하시오.</strong>

{% capture code_block12 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code> 1 | def filter_data(data_list):
 2 |     trimmed = data_list[0:3]
 3 |     output = []
 4 |     for item in trimmed:
 5 |         output.append(item + '-Done')
 6 |     return output
 7 | items = ['x', 'y', 'z', 'w', 'v']
 8 | result1 = filter_data(items)
 9 | result2 = result1[2].split('o')
10 | print(result2[1])</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
① 오류가 발생하는 Line의 번호를 쓰시오.<br>
② 오류를 정상적으로 수정하여 프로그램이 실행되었을 경우의 실행 결과를 쓰시오.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz12_mock1"
   code_html=code_block12
   answer="없음, ne|없음,ne"
   tags="Python, 문자열, split"
%}

---

# 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">경로 & Linux 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>상대 경로 계산</strong> : <code>..</code>를 만나면 현재 경로에서 한 단계 위로 이동</li>
<li><strong>grep</strong> : 파일 내 문자열 패턴 검색, <strong>cp</strong> : 파일/디렉터리 복사</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">SQL 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>ALTER TABLE ~ ADD</strong> : 테이블에 새 속성 추가, <code>VARCHAR(n)</code>은 가변길이 문자</li>
<li><strong>LEFT JOIN ~ ON</strong> : 왼쪽 테이블의 모든 행을 포함하는 조인</li>
<li><strong>AS</strong> : 별칭 부여, <strong>HAVING</strong> : 그룹화 결과에 조건 지정 (GROUP BY 이후)</li>
<li><strong>IN (서브쿼리)</strong> : 서브쿼리 결과에 포함되는 행 검색</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Java 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>Math.floor(Math.PI)</strong> : 3.14... → 3.0 (소수점 이하 버림)</li>
<li><strong>try-finally</strong> : finally는 반드시 실행되지만, try의 return 값을 변경하지 않음</li>
<li><strong>static 메서드</strong> : 참조 타입에 바인딩 (오버라이딩 X, 하이딩 O)</li>
<li><strong>인스턴스 메서드</strong> : 실제 객체 타입에 바인딩 (다형성 적용)</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Python 핵심 포인트</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>isdigit()</strong> : 문자가 숫자인지 판별하는 문자열 메서드</li>
<li><strong>__ge__(n)</strong> : <code>>=</code> 연산의 매직 메서드 표현 (예: <code>len(s).__ge__(8)</code>은 <code>len(s) >= 8</code>)</li>
<li><strong>set 교집합</strong> : <code>s1 & s2</code>로 두 집합의 공통 원소 추출</li>
<li><strong>split()</strong> : 문자열을 구분자 기준으로 분리하여 리스트 반환</li>
</ul>

</div>

---
