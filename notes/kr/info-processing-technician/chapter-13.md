---
layout: article
title: 12. 연습문제 (프로그래밍기능사 실기)
permalink: /notes/kr/info-processing-technician/chapter-13
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - 연습문제 (25문제)
keywords: "프로그래밍기능사, 실기, 연습문제, Python, Java, SQL, Linux, 경로, 모의고사"
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

# 연습문제 Part 1

<div class="quiz-number">문제 1</div><strong>다음 &lt;Product_A&gt;, &lt;Product_B&gt; 테이블을 참고하여 SQL문의 실행 결과를 쓰시오.</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;Product_A&gt;

ID   | NAME
-----|----------
S1   | Monitor
S2   | Mouse
S3   | Keyboard

&lt;Product_B&gt;

ID   | PRICE
-----|------
S1   | 200
S2   | 15
S4   | 50
S5   | 80

SELECT SUM(PRICE) AS total_sum
FROM Product_B
WHERE ID NOT IN (SELECT ID FROM Product_A);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_mock2"
   code_html=code_block1
   answer="130"
   tags="SQL, NOT IN, SUM"
%}

---

<div class="quiz-number">문제 2</div><strong>다음 JAVA 프로그램의 실행 결과를 쓰시오.</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Polymorphism {
    public static class Base {
        public int calc(int n) { return n * 2; }
        public static String getName() { return "Base"; }
    }
    public static class Derived extends Base {
        public int calc(int n) { return n * 3; }
        public String calc(String s) { return s + "!"; }
        public static String getName() { return "Derived"; }
    }
    public static void main(String[] args) {
        Base obj = new Derived();
        System.out.println(obj.calc(5) + obj.getName());
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_mock2"
   code_html=code_block2
   answer="15Base"
   tags="Java, static, 다형성"
%}

---

<div class="quiz-number">문제 3</div><strong>현재 작업 디렉터리가 다음과 같을 때, 제시된 상대 경로를 절대 경로로 변환하여 쓰시오.</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>[현재 디렉터리]
/usr/local/bin

[상대 경로]
../../etc/config</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_mock2"
   code_html=code_block3
   answer="/usr/etc/config"
   tags="경로, 상대 경로"
%}

---

<div class="quiz-number">문제 4</div><strong>다음 설명에 해당하는 리눅스 명령어를 &lt;보기&gt;에서 골라 쓰시오.</strong>

{% capture code_block4 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;보기&gt;</strong><br>
cat &nbsp; rm &nbsp; rmdir &nbsp; mkdir &nbsp; cp &nbsp; mv &nbsp; tail &nbsp; head &nbsp; more &nbsp; who
</div>
<div style="margin: 15px 0; line-height: 1.8;">
① 파일의 내용을 화면에 출력하는 명령어이다.<br>
② 디렉터리를 삭제할 때 사용하는 명령어이다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_mock2"
   code_html=code_block4
   answer="cat, rmdir|cat,rmdir"
   tags="Linux, 명령어"
%}

---

<div class="quiz-number">문제 5</div><strong>다음 Python 프로그램의 실행 결과를 쓰시오.</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>items = ['apple', 'banana', 'cherry', 'date', 'apple']
target = items.count('apple')
items.pop(target)
last_one = items.pop()
new_items = ['egg', 'flour']
items.extend(new_items)
items.reverse()
print(items)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_mock2"
   code_html=code_block5
   answer="['flour', 'egg', 'date', 'banana', 'apple']"
   tags="Python, 리스트"
%}

---

# 연습문제 Part 2

<div class="quiz-number">문제 6</div><strong>다음은 '사용자A'에게 &lt;STAFF&gt; 테이블에 대한 SELECT 권한을 부여하고, 해당 사용자가 다른 사람에게도 권한을 부여할 수 있도록 하는 SQL문이다. 괄호(①, ②)에 알맞은 항목을 쓰시오.</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>( ① ) SELECT ON STAFF TO 사용자A ( ② );</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_mock2"
   code_html=code_block6
   answer="GRANT, WITH GRANT OPTION|GRANT,WITH GRANT OPTION"
   tags="SQL, GRANT, DCL"
%}

---

<div class="quiz-number">문제 7</div><strong>다음 JAVA 프로그램의 실행 결과를 쓰시오.</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static class Node {
        public int value;
        public Node(int value) {
            this.value = value;
        }
    }
    public static void main(String[] args) {
        Node n1 = new Node(10);
        Node n2 = new Node(20);
        Node n3 = new Node(30);
        Node[] nodes = {n1, n2, n3};
        Node temp = nodes[0];
        nodes[0] = nodes[2];
        nodes[2] = temp;
        nodes[1].value = nodes[0].value;
        System.out.println(n1.value + "x" + n2.value + "y" + n3.value);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7_mock2"
   code_html=code_block7
   answer="10x30y30"
   tags="Java, 배열, 참조"
%}

---

<div class="quiz-number">문제 8</div><strong>다음 Python 프로그램의 실행 결과를 쓰시오.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>scores = [
    [10, 20],
    [30, 40],
    [50, 60]
]
db = {}
idx = 1
for row in scores:
    sum_val = 0
    for val in row:
        sum_val += val
    db[idx] = sum_val
    idx += 1

result = db.get(2)
print(result)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8_mock2"
   code_html=code_block8
   answer="70"
   tags="Python, dictionary"
%}

---

<div class="quiz-number">문제 9</div><strong>다음은 &lt;BOOK_LIST&gt; 테이블에서 '도서명'이 "데이터"로 시작하는 항목들을 '출판일' 기준 내림차순으로 정렬하는 SQL문이다. 괄호(①, ②)에 알맞은 항목을 쓰시오.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT * FROM BOOK_LIST
WHERE 도서명 LIKE ( ① )
ORDER BY 출판일 ( ② );</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_mock2"
   code_html=code_block9
   answer="'데이터%', DESC|'데이터%',DESC|데이터%, DESC|데이터%,DESC"
   tags="SQL, LIKE, ORDER BY"
%}

---

<div class="quiz-number">문제 10</div><strong>'setup.sh' 파일에 대해 다음과 같은 권한을 8진법 숫자를 사용하여 한 줄의 명령어로 부여하시오.</strong>

{% capture code_block10 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>권한 설정 조건</strong><br>
소유자(User): 읽기, 실행<br>
그룹(Group): 읽기<br>
기타(Others): 실행
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz10_mock2"
   code_html=code_block10
   answer="chmod 541 setup.sh"
   tags="Linux, chmod"
%}

---

# 연습문제 Part 3

<div class="quiz-number">문제 11</div><strong>다음 Python 프로그램의 실행 결과를 쓰시오.</strong>

{% capture code_block11 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def func(n):
    if n <= 1:
        return 1
    else:
        return n + func(n - 1)

print(func(4))</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_mock2"
   code_html=code_block11
   answer="10"
   tags="Python, 재귀 함수"
%}

---

<div class="quiz-number">문제 12</div><strong>&lt;STUDENT(STU_ID, STU_NAME, MAJOR)&gt; 테이블에 학번 '202601', 이름 '홍길동', 전공 'AI'인 데이터를 삽입하는 SQL문을 작성하시오.</strong>

{% include quiz-text.html
   id="quiz12_mock2"
   answer="INSERT INTO STUDENT VALUES('202601', '홍길동', 'AI')|INSERT INTO STUDENT VALUES ('202601', '홍길동', 'AI')|INSERT INTO STUDENT(STU_ID, STU_NAME, MAJOR) VALUES('202601', '홍길동', 'AI')|INSERT INTO STUDENT(STU_ID, STU_NAME, MAJOR) VALUES ('202601', '홍길동', 'AI')"
   tags="SQL, INSERT, DML"
%}

---

<div class="quiz-number">문제 13</div><strong>다음 Java 코드를 분석하여 각 물음에 답하시오.</strong>

{% capture code_block13 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code> 1 | public class ExceptionTest {
 2 |     public static void main(String[] args) {
 3 |         int x = 100, y = 0, z = 5;
 4 |         int res1, res2;
 5 |         try {
 6 |             res1 = x / y;
 7 |             System.out.print(x);
 8 |         }
 9 |         catch (NumberFormatException e) {
10 |             res2 = x / z;
11 |             System.out.print(res2);
12 |         }
13 |         finally {
14 |             System.out.print(" done" + z);
15 |         }
16 |     }
17 | }</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
① 런타임 오류가 발생하는 행(Line) 번호를 쓰시오.<br>
② catch문의 예외 타입을 'ArithmeticException'으로 수정했을 때의 출력 결과를 쓰시오.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz13_mock2"
   code_html=code_block13
   answer="6, 20 done5|6,20 done5"
   tags="Java, 예외 처리, try-catch-finally"
%}

---

<div class="quiz-number">문제 14</div><strong>다음 작업 환경에서 제시된 상대 경로의 절대 경로를 쓰시오.</strong>

{% capture code_block14 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>[작업 폴더]
D:/Work/Project/Source

[상대 경로]
../Include/header.h</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz14_mock2"
   code_html=code_block14
   answer="D:/Work/Project/Include/header.h"
   tags="경로, Windows"
%}

---

<div class="quiz-number">문제 15</div><strong>다음 설명에 해당하는 리눅스 명령어를 &lt;보기&gt;에서 골라 쓰시오.</strong>

{% capture code_block15 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;보기&gt;</strong><br>
pwd &nbsp; chmod &nbsp; fsck &nbsp; rm &nbsp; cp &nbsp; mv &nbsp; ls &nbsp; touch &nbsp; grep &nbsp; man
</div>
<div style="margin: 15px 0; line-height: 1.8;">
① 현재 작업 디렉터리의 절대 경로를 출력하는 명령어이다.<br>
② 파일 시스템의 무결성을 점검하고 오류를 수정하는 명령어이다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz15_mock2"
   code_html=code_block15
   answer="pwd, fsck|pwd,fsck"
   tags="Linux, 명령어"
%}

---

# 연습문제 Part 4

<div class="quiz-number">문제 16</div><strong>다음 &lt;Stock&gt; 테이블을 보고 SQL문의 실행 결과(행의 개수)를 쓰시오.</strong>

{% capture code_block16 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;Stock&gt;

CODE | QTY | PRICE
-----|-----|------
A1   | 50  | 1000
A2   | 10  | 5000
A3   | 100 | 2000
A4   | 5   | 8000
A5   | 80  | 1500

SELECT COUNT(*) FROM Stock
WHERE QTY > 40 AND PRICE >= 1500 OR QTY <= 5;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz16_mock2"
   code_html=code_block16
   answer="3"
   tags="SQL, AND, OR, COUNT"
%}

---

<div class="quiz-number">문제 17</div><strong>문자 형태의 숫자를 정수로 변환하여 계산하는 다음 Java 코드의 괄호(①)에 들어갈 공통 메소드와 최종 출력 결과를 쓰시오.</strong>

{% capture code_block17 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Main {
    public static void main(String[] args) {
        char c1 = '4';
        int v1 = Character.( ① )(c1);
        char c2 = '+';
        int v2 = Character.( ① )(c2);
        char c3 = '8';
        int v3 = Character.( ① )(c3);
        System.out.print(v1 * v2 + v3);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz17_mock2"
   code_html=code_block17
   answer="getNumericValue, 4|getNumericValue,4"
   tags="Java, Character, 형변환"
%}

---

<div class="quiz-number">문제 18</div><strong>다음 Python 프로그램의 실행 결과를 쓰시오.</strong>

{% capture code_block18 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def process(a, b, res):
    if a >= b:
        return res
    a += 2
    res += a
    return process(a, b, res)

x, y, z = 0, 4, 0
z = process(x, y, z)
print('x=', x, 'z=', z)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz18_mock2"
   code_html=code_block18
   answer="x= 0 z= 6"
   tags="Python, 재귀, 함수"
%}

---

<div class="quiz-number">문제 19</div><strong>&lt;MEMBER&gt; 테이블에서 '거주지' 컬럼의 값을 중복 없이 한 번씩만 출력하는 SQL문을 작성하시오.</strong>

{% include quiz-text.html
   id="quiz19_mock2"
   answer="SELECT DISTINCT 거주지 FROM MEMBER|SELECT DISTINCT 거주지 FROM MEMBER;"
   tags="SQL, DISTINCT"
%}

---

<div class="quiz-number">문제 20</div><strong>다음 Java 프로그램의 실행 결과를 쓰시오.</strong>

{% capture code_block20 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class FormatTest {
    public static void main(String[] args) {
        double val = 12.5678;
        System.out.printf("%.1f", val);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz20_mock2"
   code_html=code_block20
   answer="12.6"
   tags="Java, printf, 포맷"
%}

---

# 연습문제 Part 5

<div class="quiz-number">문제 21</div><strong>다음 Python 프로그램의 실행 결과를 쓰시오.</strong>

{% capture code_block21 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def sort_logic(data):
    data = list(data)
    n = len(data)
    for i in range(n):
        for j in range(i + 1, n):
            if data[i].upper() < data[j].upper():
                data[i], data[j] = data[j], data[i]
    return "".join(data)

word = "pAsSCal"
print(sort_logic(word))</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz21_mock2"
   code_html=code_block21
   answer="sSplCaA"
   tags="Python, 정렬, 문자열"
%}

---

<div class="quiz-number">문제 22</div><strong>다음 조건에 맞는 SQL문을 완성하기 위해 괄호(①~③)에 들어갈 키워드를 쓰시오.</strong>

{% capture code_block22 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>조건</strong><br>
• &lt;MEMBER&gt; 테이블에서 나이가 20세 이상( ① ) 30세 이하인 회원을 검색한다.<br>
• 이름을 기준으로 오름차순( ② ) 정렬한다.<br>
• 주소가 "서울"로 시작하지 않는( ③ ) 회원을 필터링한다.
</div>
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT * FROM MEMBER
WHERE AGE BETWEEN 20 ( ① ) 30
  AND ADDRESS ( ③ ) '서울%'
ORDER BY NAME ( ② );</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz22_mock2"
   code_html=code_block22
   answer="AND, ASC, NOT LIKE|AND,ASC,NOT LIKE"
   tags="SQL, BETWEEN, NOT LIKE, ORDER BY"
%}

---

<div class="quiz-number">문제 23</div><strong>다음은 &lt;EMPLOYEE&gt; 테이블에서 SALARY가 5000 이상인 직원의 ID, NAME을 추출하여 &lt;HIGH_PAY&gt;라는 이름의 뷰를 생성하는 SQL문이다. 괄호(①~③)에 알맞은 키워드를 쓰시오.</strong>

{% capture code_block23 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE VIEW HIGH_PAY
( ① ) ( ② ) ID, NAME
FROM EMPLOYEE
( ③ ) SALARY >= 5000;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz23_mock2"
   code_html=code_block23
   answer="AS, SELECT, WHERE|AS,SELECT,WHERE"
   tags="SQL, VIEW, CREATE"
%}

---

<div class="quiz-number">문제 24</div><strong>다음 Java 코드의 실행 순서를 Line 번호로 나열하시오. (예: 1, 2, 3...)</strong>

{% capture code_block24 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code> 1 | public class OrderTest {
 2 |     public static void main(String[] args) {
 3 |         int[] arr = {1, 2};
 4 |         try {
 5 |             int n = 5 / 0;
 6 |             System.out.println(arr[5]);
 7 |         }
 8 |         catch (ArithmeticException e) {
 9 |             System.out.println("Error 1");
10 |         }
11 |         catch (ArrayIndexOutOfBoundsException e) {
12 |             System.out.println("Error 2");
13 |         }
14 |         finally {
15 |             System.out.println("End");
16 |         }
17 |     }
18 | }</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz24_mock2"
   code_html=code_block24
   answer="3, 5, 8, 9, 14, 15|3,5,8,9,14,15"
   tags="Java, 예외 처리, 실행 순서"
%}

---

<div class="quiz-number">문제 25</div><strong>다음 Python 프로그램의 실행 결과를 쓰시오.</strong>

{% capture code_block25 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>text_list = "python-is-easy".split("-")
limit = 10
val_list = list(range(1, limit, 3))
val_list.remove(4)
print(text_list[0].find('y') + val_list[1])</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz25_mock2"
   code_html=code_block25
   answer="8"
   tags="Python, 문자열, 리스트"
%}

---

# 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">SQL 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>NOT IN (서브쿼리)</strong> : 서브쿼리 결과에 포함되지 않는 행 검색, SUM/AVG 등 집계 함수와 결합 가능</li>
<li><strong>GRANT ~ WITH GRANT OPTION</strong> : 권한 부여 시 재부여 권한까지 함께 부여</li>
<li><strong>LIKE</strong> : <code>%</code>(0개 이상 문자), <code>_</code>(정확히 1개 문자), NOT LIKE로 부정 검색</li>
<li><strong>INSERT INTO ~ VALUES</strong> : 테이블에 새로운 튜플 삽입</li>
<li><strong>AND/OR 우선순위</strong> : AND가 OR보다 먼저 평가, 필요 시 괄호로 명시</li>
<li><strong>DISTINCT</strong> : 중복 행 제거하여 고유 값만 출력</li>
<li><strong>CREATE VIEW ~ AS SELECT</strong> : 가상 테이블(뷰) 생성, WHERE로 조건 지정</li>
<li><strong>BETWEEN A AND B</strong> : A 이상 B 이하 (경계값 포함)</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Java 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>static 메서드 vs 인스턴스 메서드</strong> : static은 참조 타입(하이딩), 인스턴스는 실제 객체 타입(오버라이딩)</li>
<li><strong>배열 참조 교환</strong> : 배열 요소의 참조를 교환해도 원본 객체(n1, n2, n3) 자체는 변하지 않음</li>
<li><strong>try-catch-finally</strong> : 예외 타입이 일치해야 catch 실행, finally는 항상 실행</li>
<li><strong>Character.getNumericValue()</strong> : 숫자 문자는 해당 정수 반환, 비숫자 문자는 -1 반환</li>
<li><strong>printf("%.nf")</strong> : 소수점 이하 n자리까지 반올림 출력</li>
<li><strong>예외 처리 실행 순서</strong> : try → 예외 발생 → 일치하는 catch → finally 순으로 실행</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Python 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>리스트 메서드</strong> : <code>count()</code>(개수), <code>pop(i)</code>(제거·반환), <code>extend()</code>(확장), <code>reverse()</code>(역순)</li>
<li><strong>dict.get(key)</strong> : 딕셔너리에서 key에 해당하는 value 반환 (없으면 None)</li>
<li><strong>재귀 함수</strong> : 종료 조건과 반환값 누적 패턴 이해, 매개변수 전달 시 원본 불변 (정수)</li>
<li><strong>문자열 정렬</strong> : <code>.upper()</code>로 비교 기준 통일, 교환 시 원래 대소문자 유지</li>
<li><strong>split() / find()</strong> : 구분자 기준 분리, 문자열 내 첫 번째 인덱스 반환</li>
<li><strong>range(start, stop, step)</strong> : start부터 stop 미만까지 step 간격의 수열 생성</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">경로 & Linux 핵심 포인트</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>상대 경로 → 절대 경로</strong> : <code>..</code>를 만나면 한 단계 위로 이동, 남은 경로를 이어 붙임</li>
<li><strong>Windows 경로</strong> : 드라이브 문자(D:)로 시작, 구분자는 <code>/</code> 또는 <code>\</code> 사용</li>
<li><strong>pwd</strong> : 현재 작업 디렉터리 출력, <strong>fsck</strong> : 파일 시스템 무결성 점검</li>
<li><strong>cat</strong> : 파일 내용 출력, <strong>rmdir</strong> : 빈 디렉터리 삭제</li>
<li><strong>chmod (8진법)</strong> : 읽기(4)+쓰기(2)+실행(1)을 소유자/그룹/기타 순으로 지정</li>
</ul>

</div>

---
