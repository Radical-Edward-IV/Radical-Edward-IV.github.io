---
layout: article
title: 9. 예상문제은행 (SELECT & JOIN)
permalink: /notes/kr/info-processing-technician/chapter-10
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - SELECT문과 JOIN 예상문제은행 (16문제)
keywords: "프로그래밍기능사, SQL, SELECT, JOIN, 하위 질의, GROUP BY, HAVING, ORDER BY, 예상문제, 실기"
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

# 예상문제은행 Part 1

<div class="quiz-number">문제 1</div><strong>다음 &lt;교재&gt;, &lt;교재가격&gt; 테이블을 참고하여 SQL문의 실행 결과를 쓰시오.</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;교재&gt;

교재번호 | 교재명
---------|----------
T101     | 운영체제
T102     | 자료구조
T103     | 네트워크

&lt;교재가격&gt;

교재번호 | 가격
---------|------
T101     | 25000
T102     | 15000
T103     | 20000
T104     | 12000

SELECT 가격
FROM 교재가격
WHERE 교재번호 = (
  SELECT 교재번호
  FROM 교재
  WHERE 교재명 = '자료구조'
);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_sel_bank"
   code_html=code_block1
   answer="15000"
   tags="SELECT, 하위 질의"
%}

---

<div class="quiz-number">문제 2</div><strong>다음 &lt;팀원&gt;, &lt;연락정보&gt; 테이블을 참고하여 SQL문의 실행 결과에서 ①~③에 해당하는 값을 쓰시오.</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;팀원&gt;

사번   | 유저명 | 나이 | 직급
-------|--------|------|------
P001   | 김현우 | 35   | 대리
P002   | 이수민 | 29   | 사원
P003   | 박지영 | 42   | 과장
P004   | 최민호 | 31   | 주임
P005   | 장서윤 | 27   | 사원

&lt;연락정보&gt;

사번   | 전화번호     | 이메일
-------|-------------|------------------
P001   | 010-1111    | kim@work.co.kr
P002   | 010-2222    | lee@work.co.kr
P003   | 010-3333    | park@work.co.kr
P005   | 010-5555    | jang@work.co.kr

SELECT 팀원.유저명, 팀원.나이, 팀원.직급
FROM 팀원, 연락정보
WHERE 팀원.사번 = 연락정보.사번
  AND 팀원.나이 < 30;

&lt;결과&gt;
유저명 | 나이 | 직급
-------|------|------
( ① ) | ( ② ) | ( ③ )</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_sel_bank"
   code_html=code_block2
   answer="장서윤, 27, 사원|장서윤,27,사원"
   tags="SELECT, 복수 테이블"
%}

---

<div class="quiz-number">문제 3</div><strong>다음은 &lt;수강생&gt; 테이블과 &lt;과정&gt; 테이블을 같은 속성으로 JOIN하는 3가지 방법이다. 괄호(①~③)에 알맞은 예약어를 쓰시오.</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>-- 방법 1: 조건절 사용
SELECT 번호, 이름, 과정코드, 과정명
FROM 수강생, 과정
( ① ) 수강생.과정코드 = 과정.과정코드;

-- 방법 2: 동일 속성명 자동 매칭
SELECT 번호, 이름, 과정코드, 과정명
FROM 수강생 ( ② ) 과정;

-- 방법 3: 공통 속성 명시
SELECT 번호, 이름, 과정코드, 과정명
FROM 수강생 JOIN 과정 ( ③ )(과정코드);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_sel_bank"
   code_html=code_block3
   answer="WHERE, NATURAL JOIN, USING|WHERE,NATURAL JOIN,USING"
   tags="JOIN, EQUI JOIN"
%}

---

<div class="quiz-number">문제 4</div><strong>다음은 &lt;수강생&gt; 테이블과 &lt;시험&gt; 테이블을 INNER JOIN하여 점수가 80 이상인 수강생의 이름과 점수를 조회하는 SQL문이다. 괄호에 들어갈 알맞은 예약어를 쓰시오.</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT 수강생.이름, 시험.점수
FROM 수강생 INNER JOIN 시험
(        ) 수강생.번호 = 시험.수강번호
WHERE 시험.점수 >= 80;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_sel_bank"
   code_html=code_block4
   answer="ON"
   tags="JOIN, INNER JOIN"
%}

---

# 예상문제은행 Part 2

<div class="quiz-number">문제 5</div><strong>다음 SQL문에서 유저명이 '이'로 시작하는 모든 직원을 검색하고자 한다. 괄호에 들어갈 알맞은 대표 문자를 쓰시오.</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT *
FROM 직원
WHERE 유저명 LIKE '이(      )';</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_sel_bank"
   code_html=code_block5
   answer="%"
   tags="SELECT, LIKE"
%}

---

<div class="quiz-number">문제 6</div><strong>다음 &lt;T1&gt;, &lt;T2&gt; 테이블을 참고하여 SQL문의 실행 결과를 쓰시오.</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;T1&gt;

번호 | 이름   | 점수
-----|--------|------
1    | 김도윤 | 5
2    | 이서연 | 3
3    | 박준서 | 8
4    | 최하윤 | 6
5    | 정우진 | 2

&lt;T2&gt;

번호 | 이름   | 점수
-----|--------|------
3    | 박준서 | 8
4    | 최하윤 | 6

SELECT SUM(점수)
FROM T1
WHERE 번호 NOT IN (
  SELECT 번호 FROM T2
);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_sel_bank"
   code_html=code_block6
   answer="10"
   tags="SELECT, NOT IN, SUM"
%}

---

<div class="quiz-number">문제 7</div><strong>&lt;TRAINEE&gt; 테이블에는 180개의 튜플이 존재하며, &lt;TRAINEE&gt; 테이블의 '소속' 속성에는 3개의 서로 다른 값이 들어가 있다. 다음 SQL문의 실행 결과에서 ①~③에 해당하는 값을 쓰시오.</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT COUNT(*) FROM TRAINEE;              -- 결과: ( ① )
SELECT COUNT(DISTINCT 소속) FROM TRAINEE;  -- 결과: ( ② )
SELECT COUNT(DISTINCT 소속)
FROM TRAINEE
WHERE 소속 = '운영팀';                     -- 결과: ( ③ )</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7_sel_bank"
   code_html=code_block7
   answer="180, 3, 1|180,3,1"
   tags="SELECT, COUNT, DISTINCT"
%}

---

<div class="quiz-number">문제 8</div><strong>다음은 &lt;회원&gt; 테이블에서 가입일이 2023년 1월 1일부터 2024년 12월 31일 사이인 회원을 검색하는 SQL문이다. 괄호에 들어갈 알맞은 예약어를 쓰시오.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT *
FROM 회원
WHERE 가입일 (        ) '2023-01-01' AND '2024-12-31';</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8_sel_bank"
   code_html=code_block8
   answer="BETWEEN"
   tags="SELECT, BETWEEN"
%}

---

# 예상문제은행 Part 3

<div class="quiz-number">문제 9</div><strong>다음 SQL문은 &lt;성적&gt; 테이블에서 전체 수강생의 점수 평균을 구하는 문장이다. 괄호에 들어갈 알맞은 함수를 쓰시오.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT (        )(점수) AS 평균점수
FROM 성적;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_sel_bank"
   code_html=code_block9
   answer="AVG"
   tags="SELECT, 집계 함수"
%}

---

<div class="quiz-number">문제 10</div><strong>다음은 &lt;직원&gt; 테이블에서 유저명을 내림차순으로 정렬하여 조회하는 SQL문이다. 괄호에 들어갈 알맞은 명령어를 쓰시오.</strong>

{% capture code_block10 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT *
FROM 직원
(                          );</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz10_sel_bank"
   code_html=code_block10
   answer="ORDER BY 유저명 DESC"
   tags="SELECT, ORDER BY"
%}

---

<div class="quiz-number">문제 11</div><strong>다음 SQL문은 &lt;주문&gt; 테이블에서 고객별 주문 총액을 구하되, 총액이 50000 이상인 고객만 출력하는 문장이다. 괄호에 들어갈 알맞은 예약어를 쓰시오.</strong>

{% capture code_block11 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT 고객명, SUM(금액) AS 총액
FROM 주문
GROUP BY 고객명
(        ) SUM(금액) >= 50000;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_sel_bank"
   code_html=code_block11
   answer="HAVING"
   tags="SELECT, HAVING"
%}

---

<div class="quiz-number">문제 12</div><strong>다음 SQL문에서 '직원수'라는 별칭을 부여하기 위해 사용된 예약어를 쓰시오.</strong>

{% capture code_block12 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT 팀, COUNT(*) (        ) 직원수
FROM 직원
GROUP BY 팀;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz12_sel_bank"
   code_html=code_block12
   answer="AS"
   tags="SELECT, AS"
%}

---

# 예상문제은행 Part 4

<div class="quiz-number">문제 13</div><strong>다음은 &lt;상품&gt; 테이블에서 상품명에 '프로'가 포함된 상품을 검색하는 SQL문이다. 괄호에 들어갈 알맞은 예약어를 쓰시오.</strong>

{% capture code_block13 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT *
FROM 상품
WHERE 상품명 (        ) '%프로%';</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz13_sel_bank"
   code_html=code_block13
   answer="LIKE"
   tags="SELECT, LIKE"
%}

---

<div class="quiz-number">문제 14</div><strong>다음 &lt;지원자&gt; 테이블을 참고하여 SQL문의 실행 결과에서 ①에 해당하는 값을 쓰고, ②에 들어갈 알맞은 ORDER BY 절을 완성하시오.</strong>

{% capture code_block14 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;지원자&gt;

접수번호 | 유저명 | 지원과정   | 점수
---------|--------|-----------|------
R001     | 김태현 | 개발      | 88
R002     | 박수진 | 디자인    | 92
R003     | 이준혁 | 개발      | 75
R004     | 정미래 | 마케팅    | 69
R005     | 오세영 | 디자인    | 85
R006     | 한지우 | 마케팅    | 91

-- SQL문 1
SELECT 점수
FROM 지원자
WHERE 유저명 = '정미래';
-- 결과: ( ① )

-- SQL문 2: 지원과정을 오름차순, 같은 과정 내에서 점수를 내림차순 정렬
SELECT *
FROM 지원자
( ② );</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz14_sel_bank"
   code_html=code_block14
   answer="69, ORDER BY 지원과정 ASC, 점수 DESC|69,ORDER BY 지원과정 ASC, 점수 DESC|69, ORDER BY 지원과정, 점수 DESC|69,ORDER BY 지원과정,점수 DESC"
   tags="SELECT, ORDER BY"
%}

---

<div class="quiz-number">문제 15</div><strong>&lt;개발팀&gt; 테이블에는 25명의 팀원이 있으며, 경력 속성에는 1년부터 25년까지 모두 다른 값이 저장되어 있다. 다음 SQL문의 실행 결과로 출력되는 튜플의 수를 쓰시오.</strong>

{% capture code_block15 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT *
FROM 개발팀
WHERE 경력 BETWEEN 5 AND 18
  OR 경력 >= 12;</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: BETWEEN은 경계값을 포함하며, OR은 두 조건 중 하나라도 만족하면 선택됩니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz15_sel_bank"
   code_html=code_block15
   answer="21|21명"
   tags="SELECT, BETWEEN, OR"
%}

---

<div class="quiz-number">문제 16</div><strong>다음 &lt;상품&gt;, &lt;매장&gt; 테이블을 참고하여 SQL문의 실행 결과를 쓰시오.</strong>

{% capture code_block16 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;상품&gt;

상품코드 | 상품명     | 카테고리
---------|-----------|----------
G01      | 모니터    | 전자
G02      | 키보드    | 전자
G03      | 노트      | 문구
G04      | 데스크    | 가구

&lt;매장&gt;

매장코드 | 상품코드 | 수량
---------|---------|------
S1       | G01     | 30
S1       | G02     | 50
S1       | G03     | 100
S2       | G01     | 25
S2       | G04     | 15
S3       | G02     | 40
S3       | G03     | 80

CREATE VIEW 전자상품현황 AS
SELECT 상품.상품코드, 상품명, COUNT(매장코드) AS 매장수
FROM 상품, 매장
WHERE 상품.상품코드 = 매장.상품코드
  AND 카테고리 = '전자'
GROUP BY 상품.상품코드, 상품명;

SELECT 매장수
FROM 전자상품현황
WHERE 상품코드 = 'G01';</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz16_sel_bank"
   code_html=code_block16
   answer="2"
   tags="SELECT, VIEW, COUNT"
%}

---

# 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">SELECT 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>DISTINCT</strong> : 중복 행 제거, <code>COUNT(DISTINCT 속성)</code>으로 고유 값 개수 확인</li>
<li><strong>LIKE</strong> : <code>%</code>(모든 문자), <code>_</code>(한 글자), <code>#</code>(숫자 하나)</li>
<li><strong>BETWEEN A AND B</strong> : A 이상 B 이하 (경계값 포함)</li>
<li><strong>IS NULL / IS NOT NULL</strong> : NULL 값 비교 (= 연산자 사용 불가)</li>
<li><strong>실행 순서</strong> : FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">집계 함수 & 그룹화</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>AVG / SUM / COUNT / MIN / MAX</strong> : GROUP BY와 함께 사용</li>
<li><strong>HAVING</strong> : 그룹화된 결과에 조건 지정 (WHERE는 그룹화 전 조건)</li>
<li><strong>AS</strong> : 속성명이나 테이블에 별칭(Alias) 부여</li>
<li><strong>ORDER BY</strong> : ASC(오름차순, 기본값), DESC(내림차순), 복수 정렬 가능</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">하위 질의 & 집합 연산자</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>하위 질의(서브쿼리)</strong> : SELECT 안에 SELECT 포함, WHERE절에서 많이 사용</li>
<li><strong>NOT IN</strong> : 하위 질의 결과에 포함되지 않는 행 검색</li>
<li><strong>UNION</strong> : 합집합 (중복 제거), <strong>UNION ALL</strong> : 합집합 (중복 포함)</li>
<li><strong>INTERSECT</strong> : 교집합, <strong>EXCEPT</strong> : 차집합</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">JOIN 핵심 포인트</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>EQUI JOIN</strong> : WHERE절, NATURAL JOIN, USING, ON 4가지 표기법</li>
<li><strong>INNER JOIN ~ ON</strong> : 표준 SQL 조인 표기, 조인 조건을 ON절에 명시</li>
<li><strong>LEFT/RIGHT/FULL OUTER JOIN</strong> : 매칭되지 않는 행도 NULL로 포함</li>
<li><strong>복수 테이블 검색</strong> : FROM에 여러 테이블, WHERE에서 연결 조건 지정</li>
</ul>

</div>

---
