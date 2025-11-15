---
layout: article
title: 모의고사 2
permalink: /notes/kr/info-processing-technician/mock-exam-02
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기능사 실기 모의고사 2 - 실전 대비 20문제
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

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%EB%AA%A8%EC%9D%98%EA%B3%A0%EC%82%AC%202&reversal=false&textBg=false)

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

<div class="quiz-number">문제 1</div><strong>데이터베이스 용어에 대한 설명입니다. 괄호(①, ②)에 들어갈 용어를 보기에서 찾아 기호로 작성하세요.</strong>

{% capture question1 %}
1. 테이블의 열은 ( ① )로 이루어집니다.<br>
2. ( ① )은 데이터베이스의 가장 작은 논리 단위이며, 필드 또는 컬럼에 해당합니다.<br>
3. ( ① )의 개수를 ( ② )라고 부릅니다.<br><br>
<strong>보기</strong><br>
ㄱ. 속성(Attribute)<br>
ㄴ. 기수(Cardinality)<br>
ㄷ. 차수(Degree)<br>
ㄹ. 도메인(Domain)<br>
ㅁ. 튜플(Tuple)<br>
ㅂ. 스키마(Schema)
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   question=question1
   answer="ㄱ, ㄷ|ㄱ,ㄷ"
   placeholder="예: ㄱ, ㄴ"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 2</div><strong>&lt;회원&gt; 테이블을 정의하는 SQL문입니다. 요구사항을 만족하도록 괄호에 적합한 예약어를 영문 대문자로 작성하세요.</strong>

{% capture question2 %}
<strong>요구사항</strong><br>
• 'user_id(문자 10)', 'username(문자 20)', 'gender(문자 1)', 'email(문자 30)' 속성을 가집니다.<br>
• 'user_id' 속성은 기본키입니다.<br>
• 'gender' 속성은 'M' 또는 'F' 값만 갖도록 합니다(제약조건명: gender_ck).<br>
• 'user_id'는 &lt;member&gt; 테이블의 'mem_id'를 참조합니다(제약조건명: user_fk).
{% endcapture %}

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE TABLE 회원 (
    user_id CHAR(10) (         ),
    username CHAR(20),
    gender CHAR(1),
    email CHAR(30),
    CONSTRAINT gender_ck CHECK (gender='M' OR gender='F'),
    CONSTRAINT user_fk FOREIGN KEY(user_id) REFERENCES member(mem_id)
);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   question=question2
   code_html=code_block2
   answer="PRIMARY KEY"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 3</div><strong>운영체제의 발달 과정을 올바른 순서대로 기호로 나열하세요.</strong>

{% capture question3 %}
① 분산 처리 시스템<br>
② 시분할 시스템<br>
③ 다중 프로그래밍 시스템<br>
④ 일괄 처리 시스템
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   question=question3
   answer="④, ③, ②, ①|4, 3, 2, 1"
   placeholder="예: ①, ②, ③, ④"
   tags="운영체제 기초 활용"
%}

---

<div class="quiz-number">문제 4</div><strong>다음 두 릴레이션에서 외래키를 찾아 작성하세요. (밑줄은 기본키를 의미합니다)</strong>

{% capture question4 %}
상품(<u>상품번호</u>, 상품명, 단가, 공급업체)<br>
주문(<u>주문번호</u>, 주문처, 상품번호, 수량)
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   question=question4
   answer="상품번호"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 5</div><strong>OSI 7계층 중 응용 계층에서 동작하는 프로토콜을 모두 골라 기호로 작성하세요.</strong>

{% capture question5 %}
① HTTP<br>
② SMTP<br>
③ FTP<br>
④ TCP<br>
⑤ ICMP<br>
⑥ IP<br>
⑦ UDP<br>
⑧ ARP
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=question5
   answer="①, ②, ③|1, 2, 3"
   placeholder="예: ①, ②, ③"
   tags="네트워크 기초 활용"
%}

---

<div class="quiz-number">문제 6</div><strong>관계형 데이터베이스에서 하나의 속성이 가질 수 있는 동일한 타입의 원자값들의 집합을 의미하는 용어를 작성하세요.</strong>

{% include quiz-text.html
   id="quiz6"
   question=""
   answer="도메인|Domain"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 7</div><strong>&lt;Item&gt; 테이블로부터 cost가 50000 미만인 항목들의 ID, NAME, cost를 가져와 &lt;discount&gt; 뷰를 생성하는 SQL문입니다. 괄호에 적합한 예약어를 영문 대문자로 작성하세요.</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE VIEW discount ( ① )
SELECT ID, NAME, cost
FROM Item
( ② ) cost &lt; 50000;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7"
   question=""
   code_html=code_block7
   answer="AS, WHERE"
   placeholder="예: KEYWORD, KEYWORD"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 8</div><strong>&lt;목표&gt; 테이블의 판매액이 3000 초과인 상품에 대해 &lt;판매&gt; 테이블의 재고를 &lt;목표&gt; 테이블의 재고로 변경하는 SQL문입니다. 괄호에 적합한 예약어를 영문 대문자로 작성하세요.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>UPDATE 판매 x INNER JOIN 목표 y
(     ) x.ID = y.ID
SET x.재고 = y.재고
WHERE y.판매액 &gt; 3000;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8"
   question=""
   code_html=code_block8
   answer="ON"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 9</div><strong>다음 C 프로그램의 실행 결과를 작성하세요.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
int main()
{
    int result, m = 30, n = 50, p = 70;
    result = m &lt; n ? n++ : --p;
    printf("%d/%d/%d", result, n, p);
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9"
   question=""
   code_html=code_block9
   answer="50/51/70"
   tags="C언어"
%}

---

<div class="quiz-number">문제 10</div><strong>다음 C 프로그램의 실행 결과를 작성하세요.</strong>

{% capture code_block10 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
int main()
{
    char arr[] = {'5', 'X', 'Y', 'Z', 'A'};
    char *ptr;
    ptr = &amp;arr[3];
    printf("%c%c", *ptr, *(ptr-2));
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz10"
   question=""
   code_html=code_block10
   answer="ZX"
   tags="C언어"
%}

---

<div class="quiz-number">문제 11</div><strong>홍길동에게 부여된 &lt;학생&gt; 테이블에 대한 INSERT와 DELETE 권한을 취소하는 SQL문을 작성하려고 합니다. 괄호에 적합한 예약어를 영문 대문자로 작성하세요.</strong>

{% capture code_block11 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>(     ) INSERT, DELETE ON 학생 FROM 홍길동;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11"
   question=""
   code_html=code_block11
   answer="REVOKE"
   tags="데이터베이스 기초 활용"
%}

---

<div class="quiz-number">문제 12</div><strong>다음 설명에 해당하는 용어를 영문 대문자 4글자로 작성하세요.</strong>

{% capture question12 %}
IP 주소 부족 문제를 해결하기 위한 프로토콜로, 동적 호스트 설정 프로토콜이라 불립니다. 네트워크 관리자가 IP 주소를 중앙에서 관리하고 할당할 수 있게 하며, IP 주소의 '임대' 개념을 사용하여 제한된 IP 주소를 효율적으로 관리할 수 있습니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz12"
   question=question12
   answer="DHCP"
   tags="네트워크 기초 활용"
%}

---

<div class="quiz-number">문제 13</div><strong>다음 설명에 해당하는 용어를 작성하세요.</strong>

{% capture question13 %}
네트워크에서 서로 다른 컴퓨터들이 정보를 교환할 수 있도록 하는 통신 규약으로, 흐름 제어, 동기화, 오류 검출 기능을 수행합니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz13"
   question=question13
   answer="프로토콜|Protocol"
   tags="네트워크 기초 활용"
%}

---

<div class="quiz-number">문제 14</div><strong>리눅스에서 사용하는 명령어 중 다음 기능에 해당하는 명령을 보기에서 찾아 작성하세요.</strong>

{% capture question14 %}
1. 파일을 삭제합니다.<br>
2. 파일의 권한 모드를 설정하여 접근 권한을 지정합니다.<br><br>
<strong>보기</strong><br>
cat, cd, chmod, find, rm, kill, ls, chown
{% endcapture %}

{% include quiz-text.html
   id="quiz14"
   question=question14
   answer="rm, chmod"
   placeholder="예: command1, command2"
   tags="운영체제 기초 활용"
%}

---

<div class="quiz-number">문제 15</div><strong>소프트웨어 개발에서 진행되는 테스트를 올바른 순서대로 기호로 나열하세요.</strong>

{% capture question15 %}
① 시스템 테스트<br>
② 단위 테스트<br>
③ 통합 테스트<br>
④ 인수 테스트
{% endcapture %}

{% include quiz-text.html
   id="quiz15"
   question=question15
   answer="②, ③, ①, ④|2, 3, 1, 4"
   placeholder="예: ①, ②, ③, ④"
   tags="애플리케이션 테스트"
%}

---

<div class="quiz-number">문제 16</div><strong>운영체제의 커널을 보조기억장치에서 주기억장치로 적재하여 시스템을 초기화하는 기능을 수행하는 것을 찾아 기호로 작성하세요.</strong>

{% capture question16 %}
① BIOS<br>
② CMOS<br>
③ Bootstrap Loader<br>
④ RAM<br>
⑤ ROM<br>
⑥ MBR
{% endcapture %}

{% include quiz-text.html
   id="quiz16"
   question=question16
   answer="③|3"
   tags="운영체제 기초 활용"
%}

---

<div class="quiz-number">문제 17</div><strong>다음 C 프로그램의 실행 결과를 작성하세요.</strong>

{% capture code_block17 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
int main()
{
    int grid[5][5] = {
        2, 4, 8, 3, 7,
        3, 6, 5, 2, 9,
        1, 3, 4, 8, 6,
        5, 7, 2, 1, 4,
        3, 9, 6, 5, 2
    };

    int i = 0, j = 0;
    int total = grid[i][j];

    while(1)
    {
        if (i==4 &amp;&amp; j==4) break;
        else if (i==4) j++;
        else if (j==4) i++;
        else if (grid[i+1][j] &gt;= grid[i][j+1]) j++;
        else i++;

        total += grid[i][j];
    }

    printf("result : %d", total);
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz17"
   question=""
   code_html=code_block17
   answer="result : 23"
   tags="C언어"
%}

---

<div class="quiz-number">문제 18</div><strong>다음 Java 프로그램의 실행 결과를 작성하세요.</strong>

{% capture code_block18 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>import java.lang.*;
public class Main
{
    public static void main(String[] args) {
        switch((int)Math.signum(-50)) {
            case -1:
                System.out.print("A");
                break;
            case 0:
                System.out.print("B");
                break;
            case 1:
                System.out.print("C");
                break;
            default:
                System.out.print("D");
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz18"
   question=""
   code_html=code_block18
   answer="A"
   tags="C언어"
%}

---

<div class="quiz-number">문제 19</div><strong>다음 Java 프로그램에서 괄호에 들어갈 알맞은 예약어를 보기에서 찾아 기호로 작성하세요.</strong>

{% capture question19 %}
결과로 20을 출력하는 프로그램입니다.
{% endcapture %}

{% capture code_block19 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>interface Calculate {
    public void compute(int v);
}

class Processor (     ) Calculate {
    public void compute(int v) {
        System.out.print(v+v);
    }
}

public class Main {
    public static void main(String[] args) {
        Calculate calc = new Processor();
        calc.compute(10);
    }
}</code></pre>
</div>
<div class="quiz-choices" style="margin-bottom: 15px; padding: 10px; background-color: #fff; border-left: 3px solid #203BB0;">
    <strong>보기</strong><br>
    ① new<br>
    ② abstract<br>
    ③ super<br>
    ④ extends<br>
    ⑤ implements
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz19"
   question=question19
   code_html=code_block19
   answer="⑤|5"
   tags="C언어"
%}

---

<div class="quiz-number">문제 20</div><strong>다음 Java 프로그램의 실행 결과를 작성하세요.</strong>

{% capture code_block20 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class ParentClass {
    int x = 2;
    int y = 3;
}

class ChildClass extends ParentClass {
    void method1() {
        System.out.println(this.x * this.y);
    }
    void method1(int num) {
        System.out.println(this.x - this.y);
    }
    void method1(char ch) {
        System.out.println(this.x / this.y);
    }
    void method1(float f) {
        System.out.println(this.x + this.y);
    }
}

public class Main
{
    public static void main(String[] args) {
        int x = 15;
        int y = 4;

        ChildClass obj = new ChildClass();
        obj.method1(x/y);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz20"
   question=""
   code_html=code_block20
   answer="-1"
   tags="C언어"
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
