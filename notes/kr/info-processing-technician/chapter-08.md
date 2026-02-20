---
layout: article
title: 7. 예상문제은행 (SQL)
permalink: /notes/kr/info-processing-technician/chapter-08
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - SQL(DDL, DML, DCL) 예상문제은행 (19문제)
keywords: "프로그래밍기능사, SQL, DDL, DML, DCL, 예상문제, 실기"
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

<div class="quiz-number">문제 1</div><strong>다음은 SELECT 권한을 취소하는 SQL문이다. 괄호에 들어갈 가장 적합한 SQL 명령어를 쓰시오.</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>(      ) SELECT ON course FROM HONG;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_sql_bank"
   code_html=code_block1
   answer="REVOKE"
   tags="DCL, REVOKE"
%}

---

<div class="quiz-number">문제 2</div><strong>다음은 &lt;수강생&gt; 테이블에 가변적인 20자리 문자가 저장되는 '연락처' 속성을 추가하는 SQL문이다. 괄호에 들어갈 알맞은 데이터 타입을 쓰시오.</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>ALTER TABLE 수강생 ADD 연락처 (        );</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_sql_bank"
   code_html=code_block2
   answer="VARCHAR(20)"
   tags="DDL, ALTER"
%}

---

<div class="quiz-number">문제 3</div><strong>인덱스 운영 중 데이터의 Insert, Update, Delete 등의 반복 작업으로 단편화가 발생하여 인덱스 성능이 저하될 수 있다. 다음은 idx_P 인덱스를 재구성하기 위한 SQL문이다. 괄호에 들어갈 알맞은 명령어를 쓰시오.</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>ALTER INDEX idx_P (        );</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_sql_bank"
   code_html=code_block3
   answer="REBUILD"
   tags="DDL, INDEX"
%}

---

<div class="quiz-number">문제 4</div><strong>다음은 기존 테이블과 동일한 구조의 테이블을 복사하여 생성하는 SQL문이다. 괄호에 알맞은 명령어를 쓰시오.</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>(      ) TABLE order_backup SELECT * FROM order_main;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_sql_bank"
   code_html=code_block4
   answer="CREATE"
   tags="DDL, CREATE"
%}

---

<div class="quiz-number">문제 5</div><strong>다음은 이순신에게 &lt;수강생&gt; 테이블에 대한 모든 권한을 부여하고, 해당 권한을 다른 사용자에게도 부여할 수 있도록 하는 SQL문이다. 괄호에 들어갈 가장 적합한 명령어를 쓰시오.</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>GRANT ALL ON 수강생 TO 이순신 (        );</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_sql_bank"
   code_html=code_block5
   answer="WITH GRANT OPTION"
   tags="DCL, GRANT"
%}

---

<div class="quiz-number">문제 6</div><strong>다음은 &lt;member&gt; 테이블의 email 속성을 제거하면서 연계된 모든 제약 조건도 함께 제거하는 SQL문이다. 괄호에 적합한 예약어를 쓰시오.</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>ALTER TABLE member DROP COLUMN email (        );</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_sql_bank"
   code_html=code_block6
   answer="CASCADE"
   tags="DDL, ALTER"
%}

---

# 예상문제은행 Part 2

<div class="quiz-number">문제 7</div><strong>다음은 &lt;Inventory&gt; 테이블에서 quantity가 50 미만인 제품들의 item_id, item_name, quantity를 가져와 &lt;low_stock&gt; 뷰를 생성하는 SQL문이다. 괄호(①, ②)에 적절한 예약어를 쓰시오.</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE VIEW low_stock ( ① )
SELECT item_id, item_name, quantity
FROM Inventory
( ② ) quantity < 50;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7_sql_bank"
   code_html=code_block7
   answer="AS, WHERE|AS,WHERE"
   tags="DDL, VIEW"
%}

---

<div class="quiz-number">문제 8</div><strong>다음 &lt;처리 조건&gt;을 준수하여 인덱스를 생성하는 SQL문의 괄호(①, ②)에 들어갈 알맞은 명령어를 쓰시오.</strong>

{% capture code_block8 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;처리 조건&gt;</strong><br>
• 기본 테이블 S의 열(A, B, C)에 관한 조합으로 Y 인덱스를 생성한다.<br>
• 인덱스 정렬은 A(오름차순), B(내림차순), C(오름차순)이다.<br>
• UNIQUE와 CLUSTER는 생략한다.
</div>
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE ( ① ) Y ( ② ) S(A, B DESC, C);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8_sql_bank"
   code_html=code_block8
   answer="INDEX, ON|INDEX,ON"
   tags="DDL, INDEX"
%}

---

<div class="quiz-number">문제 9</div><strong>&lt;환자&gt; 테이블을 정의하는 SQL문이다. 아래의 &lt;요구사항&gt;을 만족하도록 괄호에 적합한 예약어를 쓰시오.</strong>

{% capture code_block9 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;요구사항&gt;</strong><br>
• 'pid(문자 5)', 'pname(문자 10)', 'gender(문자 1)', 'contact(문자 20)' 속성을 가진다.<br>
• 'pid' 속성은 기본키이다.<br>
• 'gender' 속성은 'M' 또는 'F' 값만 갖도록 한다(제약조건명 : gender_ck).<br>
• 'pid'는 &lt;physician&gt; 테이블에 있는 'phy_id'를 참조한다(제약조건명 : pid_fk).
</div>
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE TABLE patient (
    pid CHAR(5) (        ),
    pname CHAR(10),
    gender CHAR(1),
    contact CHAR(20),
    CONSTRAINT gender_ck CHECK (gender='M' or gender='F'),
    CONSTRAINT pid_fk FOREIGN KEY(pid) REFERENCES physician(phy_id)
);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_sql_bank"
   code_html=code_block9
   answer="PRIMARY KEY"
   tags="DDL, CREATE TABLE"
%}

---

<div class="quiz-number">문제 10</div><strong>SQL에 대한 다음 설명에서 괄호(①~③)에 들어갈 알맞은 DDL 명령어를 쓰시오.</strong>

{% capture code_block10 %}
<div style="margin: 15px 0; line-height: 1.8;">
DDL(Data Definition Language)은 DB 구조, 데이터 형식, 접근 방식 등을 정의하는 언어로, 다음 3가지 명령어로 표현한다.<br><br>
• ( ① ) : 스키마, 도메인, 테이블 등의 객체를 정의하는 명령어<br>
• ( ② ) : 객체에 대한 정의를 변경하는 명령어<br>
• ( ③ ) : 스키마, 도메인, 테이블 등의 객체를 삭제하는 명령어
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz10_sql_bank"
   code_html=code_block10
   answer="CREATE, ALTER, DROP|CREATE,ALTER,DROP"
   tags="DDL"
%}

---

# 예상문제은행 Part 3

<div class="quiz-number">문제 11</div><strong>데이터 제어어(DCL)에 대한 다음 설명에서 괄호(①, ②)에 들어갈 알맞은 답을 &lt;보기&gt;에서 찾아 쓰시오.</strong>

{% capture code_block11 %}
<div style="margin: 15px 0; line-height: 1.8;">
• ( ① ) : 수행 결과를 실제 물리적 디스크에 저장하고, 데이터베이스 조작 작업이 정상 완료되었음을 관리자에게 알려주는 명령어<br>
• ( ② ) : 작업이 비정상적으로 종료되었을 때 원래 상태로 복구할 때 사용하는 명령어<br><br>
<strong>&lt;보기&gt;</strong><br>
GRANT &nbsp; ROLLBACK &nbsp; SAVEPOINT &nbsp; COMMIT &nbsp; REVOKE &nbsp; UNDO &nbsp; REDO
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_sql_bank"
   code_html=code_block11
   answer="COMMIT, ROLLBACK|COMMIT,ROLLBACK"
   tags="DCL"
%}

---

<div class="quiz-number">문제 12</div><strong>다음 &lt;보기&gt;에 나열된 SQL 명령어를 DDL, DML, DCL로 구분하시오. (각 분류별로 쉼표로 구분하여 작성)</strong>

{% capture code_block12 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;보기&gt;</strong><br>
SELECT &nbsp; REVOKE &nbsp; ALTER &nbsp; CREATE &nbsp; DELETE &nbsp; DROP &nbsp; INSERT &nbsp; GRANT &nbsp; UPDATE
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz12_sql_bank"
   code_html=code_block12
   answer="DDL: CREATE, ALTER, DROP / DML: SELECT, INSERT, DELETE, UPDATE / DCL: GRANT, REVOKE"
   tags="SQL"
%}

---

<div class="quiz-number">문제 13</div><strong>&lt;고객&gt; 테이블에 가변 길이 25자의 '이메일' 속성을 추가하는 SQL문을 완성하시오. 괄호(①, ②)에 들어갈 알맞은 예약어를 쓰시오.</strong>

{% capture code_block13 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>( ① ) TABLE 고객 ( ② ) 이메일 VARCHAR(25);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz13_sql_bank"
   code_html=code_block13
   answer="ALTER, ADD|ALTER,ADD"
   tags="DDL, ALTER"
%}

---

<div class="quiz-number">문제 14</div><strong>&lt;직원&gt; 테이블에서 '성명'이 '김철수'인 튜플을 삭제하고자 한다. 다음 &lt;처리 조건&gt;을 참고하여 SQL문을 작성하시오.</strong>

{% capture code_block14 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;처리조건&gt;</strong><br>
• 최소한의 코드로 SQL문을 구성한다.<br>
• 마지막 세미콜론(;)은 생략 가능하다.<br>
• 인용 부호가 필요한 경우 작은따옴표(')를 사용한다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz14_sql_bank"
   code_html=code_block14
   answer="DELETE FROM 직원 WHERE 성명 = '김철수'"
   tags="DML, DELETE"
%}

---

<div class="quiz-number">문제 15</div><strong>다음은 &lt;Employee&gt; 테이블의 'emp_no' 속성에 대해 중복을 허용하지 않는 'Emp_idx'라는 이름의 인덱스를 정의하는 SQL문이다. 괄호(①, ②)에 알맞은 예약어를 쓰시오.</strong>

{% capture code_block15 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE ( ① ) ( ② ) Emp_idx ON Employee (emp_no);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz15_sql_bank"
   code_html=code_block15
   answer="UNIQUE, INDEX|UNIQUE,INDEX"
   tags="DDL, INDEX"
%}

---

# 예상문제은행 Part 4

<div class="quiz-number">문제 16</div><strong>&lt;PRODUCT&gt; 테이블의 구조와 데이터를 모두 삭제하되, 외래키 제약 등 다른 테이블이 참조하고 있다면 삭제되지 않도록 제한하는 SQL문을 작성하시오.</strong>

{% include quiz-text.html
   id="quiz16_sql_bank"
   answer="DROP TABLE PRODUCT RESTRICT"
   tags="DDL, DROP"
%}

---

<div class="quiz-number">문제 17</div><strong>다음 &lt;직원&gt; 테이블의 정의문과 &lt;조건&gt;을 참고하여 괄호(①, ②)에 들어갈 알맞은 답을 쓰시오.</strong>

{% capture code_block17 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE TABLE 직원
(
    사번 NUMBER NOT NULL,
    성명 CHAR(10) UNIQUE,
    부서 CHAR(10) ( ① ) (부서 ( ② ) ('개발', '기획', '인사', '영업')),
    급여 NUMBER
);</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;조건&gt;</strong><br>
• '사번' 속성은 NULL을 갖지 않는다.<br>
• '성명' 속성은 중복 값을 허용하지 않는다.<br>
• '부서' 속성에는 '개발', '기획', '인사', '영업' 중 하나의 값만 저장할 수 있다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz17_sql_bank"
   code_html=code_block17
   answer="CHECK, IN|CHECK,IN"
   tags="DDL, CREATE TABLE"
%}

---

<div class="quiz-number">문제 18</div><strong>다음 &lt;employees&gt; 테이블에서 사번(emp_id)이 E1035인 직원의 급여(salary)를 3200으로 갱신하는 SQL문을 작성하시오.</strong>

{% capture code_block18 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;employees&gt;</strong>
</div>
<table style="width: 100%; border-collapse: collapse; font-size: 0.9rem; margin-bottom: 15px;">
<tr style="background-color: #f9fafb;">
<th style="border: 1px solid #e5e7eb; padding: 8px;">emp_id</th>
<th style="border: 1px solid #e5e7eb; padding: 8px;">name</th>
<th style="border: 1px solid #e5e7eb; padding: 8px;">salary</th>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">E1031</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">Kim</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">2800</td>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">E1032</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">Lee</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">2500</td>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">E1035</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">Park</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">2900</td>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">E1038</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">Choi</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">3500</td>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">E1041</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">Jung</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">4100</td>
</tr>
</table>
{% endcapture %}

{% include quiz-text.html
   id="quiz18_sql_bank"
   code_html=code_block18
   answer="UPDATE employees SET salary = 3200 WHERE emp_id = 'E1035'"
   tags="DML, UPDATE"
%}

---

<div class="quiz-number">문제 19</div><strong>다음 &lt;처리조건&gt;에 부합하는 SQL문이 완성되도록 괄호(①~③)에 적합한 명령어를 쓰시오.</strong>

{% capture code_block19 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;처리조건&gt;</strong><br>
• &lt;상품&gt; 테이블에 상품명이 '무선마우스', 카테고리가 '주변기기', 가격이 '25000'인 상품 정보를 입력하시오.<br>
• &lt;상품&gt; 테이블에서 상품명이 '유선키보드'인 상품의 가격을 '18000'으로 변경하시오.
</div>
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>• INSERT ( ① ) 상품 (상품명, 카테고리, 가격) ( ② ) ('무선마우스', '주변기기', 25000);
• UPDATE 상품 ( ③ ) 가격 = 18000 WHERE 상품명 = '유선키보드';</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz19_sql_bank"
   code_html=code_block19
   answer="INTO, VALUES, SET|INTO,VALUES,SET"
   tags="DML, INSERT, UPDATE"
%}

---

# 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">DDL 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>CREATE TABLE</strong> : PRIMARY KEY, FOREIGN KEY, UNIQUE, CHECK, NOT NULL 제약 조건</li>
<li><strong>CREATE VIEW</strong> : <code>AS SELECT</code>문 사용, UNION/ORDER BY 사용 불가</li>
<li><strong>CREATE INDEX</strong> : UNIQUE(고유 인덱스), ASC/DESC(정렬), CLUSTER</li>
<li><strong>ALTER TABLE</strong> : ADD(추가), ALTER(변경), DROP COLUMN(삭제, CASCADE 옵션)</li>
<li><strong>DROP</strong> : CASCADE(연쇄 삭제) vs RESTRICT(참조 시 삭제 취소)</li>
<li><strong>INDEX REBUILD</strong> : 단편화 발생 시 인덱스 재구성</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">DML 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>INSERT INTO ~ VALUES</strong> : 속성명 생략 시 모든 속성에 대응하는 데이터 필요</li>
<li><strong>DELETE FROM ~ WHERE</strong> : WHERE 생략 시 전체 삭제 (구조는 유지)</li>
<li><strong>UPDATE ~ SET ~ WHERE</strong> : SET 절에서 산술 연산 가능 (예: 가격 = 가격 * 1.1)</li>
<li><strong>SELECT ~ FROM ~ WHERE</strong> : 데이터 검색의 기본 구문</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">DCL 핵심 포인트</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>GRANT ~ ON ~ TO</strong> : 권한 부여, <code>WITH GRANT OPTION</code>으로 재부여 가능</li>
<li><strong>REVOKE ~ ON ~ FROM</strong> : 권한 취소, <code>GRANT OPTION FOR</code>로 재부여 권한만 취소 가능</li>
<li><strong>COMMIT</strong> : 트랜잭션 결과를 영구적으로 반영</li>
<li><strong>ROLLBACK</strong> : COMMIT 이전 상태로 복원, <code>ROLLBACK TO 저장점</code>으로 특정 지점까지 복원</li>
<li><strong>SAVEPOINT</strong> : 트랜잭션 내 롤백 지점 설정</li>
</ul>

</div>

---
