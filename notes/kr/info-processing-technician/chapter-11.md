---
layout: article
title: 10. 예시문제 (프로그래밍기능사 실기)
permalink: /notes/kr/info-processing-technician/chapter-11
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - 예시문제 (11문제)
keywords: "프로그래밍기능사, 실기, 예시문제, Python, Java, SQL, Linux, 경로"
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

# 예시문제 Part 1

<div class="quiz-number">문제 1</div><strong>현재 작업 디렉터리의 절대 경로가 다음과 같을 때, 상대 경로로 제시된 디렉터리의 절대 경로를 쓰시오.</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>[작업폴더]
/home/dev/projects/backend

[상대 경로]
../../config/env</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_sample"
   code_html=code_block1
   answer="/home/dev/config/env"
   tags="경로, 상대 경로"
%}

---

<div class="quiz-number">문제 2</div><strong>다음 각 기능에 해당하는 Linux 터미널 명령어를 &lt;보기&gt;에서 골라 쓰시오.</strong>

{% capture code_block2 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;보기&gt;</strong><br>
ls &nbsp; mv &nbsp; cat &nbsp; grep &nbsp; pwd &nbsp; echo &nbsp; find &nbsp; chmod &nbsp; rm &nbsp; cp &nbsp; cd &nbsp; export
</div>
<div style="margin: 15px 0; line-height: 1.8;">
① 파일이나 디렉터리를 다른 위치로 이동하거나 이름을 변경하는 명령어를 쓰시오.<br>
② 특정 파일이나 디렉터리를 검색할 때 사용하는 명령어를 쓰시오.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_sample"
   code_html=code_block2
   answer="mv, find|mv,find"
   tags="Linux, 명령어"
%}

---

<div class="quiz-number">문제 3</div><strong>다음 Python 프로그램에 대하여 실행 결과를 쓰시오.</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Vertex:
    def __init__(self, val):
        self.left = None
        self.right = None
        self.val = val

def traverse(node):
    if node:
        traverse(node.left)
        traverse(node.right)
        print(node.val, end = ' ')

root = Vertex(9)
root.left = Vertex(3)
root.right = Vertex(6)
root.left.left = Vertex(1)
root.left.right = Vertex(4)
root.right.left = Vertex(7)
root.right.right = Vertex(2)

traverse(root)</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: 재귀 호출 순서(왼쪽 → 오른쪽 → 현재 노드)를 따라 트리를 순회합니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_sample"
   code_html=code_block3
   answer="1 4 3 7 2 6 9"
   tags="Python, 트리, 후위순회"
%}

---

# 예시문제 Part 2

<div class="quiz-number">문제 4</div><strong>다음은 dictionary 변수에 어떤 값의 key를 포함하고 있다면 해당 key의 value 값을 모두 찾아 반환하는 Python 프로그램이다. 괄호(①)에 들어갈 알맞은 코드를 쓰시오.</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def lookup(data, k) :
    return [v for k2, v in data.( ① )() if k2 == k]</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_sample"
   code_html=code_block4
   answer="items"
   tags="Python, dictionary"
%}

---

<div class="quiz-number">문제 5</div><strong>다음 Python 프로그램에 대하여 다음 각 물음에 답하시오.</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code> 1 | def make_series(count):
 2 |     result = []
 3 |     x, y = 0, 1
 4 |     for _ in range(count):
 5 |         result.append(x)
 6 |         x, y = y, x+y
 7 |     return result
 8 |
 9 | num = 7
10 | print(make_series(num)[0])</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
① 오류가 발생하는 Line의 번호를 쓰시오.<br>
② 오류를 정상적으로 수정하여 프로그램이 실행되었을 경우의 실행 결과를 쓰시오.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_sample"
   code_html=code_block5
   answer="없음, 0|없음,0"
   tags="Python, 피보나치"
%}

---

<div class="quiz-number">문제 6</div><strong>다음 JAVA 프로그램의 실행 결과가 30이 나오도록 괄호(①)에 들어갈 알맞은 키워드를 한 단어로 쓰시오.</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>interface Calc {
    int operate(int x, int y);
}

class Multiply ( ① ) Calc {
    public int operate(int x, int y) {
        return x*y;
    }
}

public class Solution {
    public static void main(String[] args) {
        int p = 5, q = 6;
        Calc mul = new Multiply();
        System.out.print(mul.operate(p, q));
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_sample"
   code_html=code_block6
   answer="implements"
   tags="Java, interface"
%}

---

# 예시문제 Part 3

<div class="quiz-number">문제 7</div><strong>다음 JAVA 프로그램의 실행 결과를 쓰시오.</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Solution {
    public static void main(String[] args) {
        String s1 = new String("JAVA");
        String s2 = new String("JAVA");
        if(s1.equals(s2)) System.out.print(s1);
        else System.out.print(s1+s2);
    }
}</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: <code>equals()</code>는 문자열의 <strong>내용</strong>을 비교하고, <code>==</code>는 <strong>참조(주소)</strong>를 비교합니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7_sample"
   code_html=code_block7
   answer="JAVA"
   tags="Java, String"
%}

---

<div class="quiz-number">문제 8</div><strong>다음 JAVA 프로그램의 실행 결과를 쓰시오.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Animal {
    Animal() {
        System.out.print('A');
    }
    Animal(char c) {
        this();
        System.out.print(c);
    }
}
class Dog extends Animal {
    Dog() {
        super();
        System.out.print('B');
    }
    Dog(char c) {
        this();
        System.out.print(c);
    }
}
public class Solution {
    public static void main(String[] args) {
        Animal a = new Dog('W');
    }
}</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: 생성자 체이닝에서 <code>this()</code>는 같은 클래스의 다른 생성자를, <code>super()</code>는 부모 클래스의 생성자를 호출합니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8_sample"
   code_html=code_block8
   answer="ABW"
   tags="Java, 생성자, 상속"
%}

---

<div class="quiz-number">문제 9</div><strong>member 테이블에는 nickname(닉네임), uid(아이디), dept(부서) 컬럼이 있다. 닉네임이 '김'으로 시작하면서 이름이 2글자인 사람의 정보를 찾는 SQL 코드에 대하여 괄호(①)에 들어갈 알맞은 와일드카드 문자를 쓰시오.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT * FROM member WHERE nickname LIKE '김( ① )'</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: LIKE에서 <code>%</code>는 0개 이상의 문자, <code>_</code>는 정확히 1개의 문자를 의미합니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_sample"
   code_html=code_block9
   answer="_"
   tags="SQL, LIKE"
%}

---

# 예시문제 Part 4

<div class="quiz-number">문제 10</div><strong>log 테이블의 구조와 데이터를 모두 삭제하고, 연관 제약 조건까지 모두 제거하는 SQL 쿼리를 3개의 키워드와 테이블 이름(log)만 사용하여 쓰시오.</strong>

{% include quiz-text.html
   id="quiz10_sample"
   answer="DROP TABLE log CASCADE"
   tags="SQL, DROP, CASCADE"
%}

---

<div class="quiz-number">문제 11</div><strong>다음 테이블 a1, a2에 대한 SQL 쿼리 수행 결과를 쓰시오.</strong>

{% capture code_block11 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;a1&gt;

 k  | v
----|----
 B  | 4
 D  | 7
 E  | 1
 G  | 5

&lt;a2&gt;

 k  | v
----|----
 A  | 9
 D  | 3
 F  | 6
 G  | 8

SELECT SUM(v) AS total
FROM a2
WHERE k NOT IN (SELECT k FROM a1);</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>힌트</strong>: a1의 k 값은 {B, D, E, G}이므로, a2에서 이에 포함되지 않는 행만 선택됩니다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_sample"
   code_html=code_block11
   answer="15"
   tags="SQL, NOT IN, SUM"
%}

---

# 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">경로 & Linux 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>절대 경로</strong> : 루트(/)부터 시작하는 전체 경로</li>
<li><strong>상대 경로</strong> : <code>..</code>(상위 디렉터리), <code>.</code>(현재 디렉터리) 기준으로 이동</li>
<li><strong>mv</strong> : 파일/디렉터리 이동 또는 이름 변경</li>
<li><strong>find</strong> : 파일/디렉터리 검색, <strong>grep</strong> : 파일 내 문자열 패턴 검색</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Python 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>후위순회(Postorder)</strong> : 왼쪽 → 오른쪽 → 루트 순서로 트리 탐색</li>
<li><strong>dict.items()</strong> : 딕셔너리의 (key, value) 쌍을 반환</li>
<li><strong>피보나치 수열</strong> : <code>x, y = y, x+y</code> 패턴으로 동시 할당</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Java 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>implements</strong> : 인터페이스 구현 시 사용하는 키워드</li>
<li><strong>equals()</strong> : 문자열 내용 비교 (==는 참조 비교)</li>
<li><strong>생성자 체이닝</strong> : <code>this()</code>로 같은 클래스, <code>super()</code>로 부모 클래스 생성자 호출</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">SQL 핵심 포인트</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>LIKE</strong> : <code>%</code>(0개 이상 문자), <code>_</code>(정확히 1개 문자)</li>
<li><strong>DROP TABLE ~ CASCADE</strong> : 테이블과 연관 제약 조건 모두 삭제</li>
<li><strong>NOT IN (서브쿼리)</strong> : 서브쿼리 결과에 포함되지 않는 행 검색</li>
</ul>

</div>

---
