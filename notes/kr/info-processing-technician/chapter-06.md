---
layout: article
title: 5. 예상문제은행
permalink: /notes/kr/info-processing-technician/chapter-06
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - Java와 Python 예상문제은행 (52문제)
keywords: "프로그래밍기능사, Java, Python, 예상문제, 실기"
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

<div class="quiz-number">문제 1</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int x = 15, y = 6, z = 3, w = 2;
        x /= y++ - z * w;
        System.out.printf("%d", x);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_bank"
   code_html=code_block1
   answer="15"
   tags="Java, 연산자"
%}

---

<div class="quiz-number">문제 2</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    static final int ODD = 1;
    static final int EVEN = 0;

    public static void main(String[] args) {
        int value = 42;
        if (value % 2 == EVEN)
            System.out.printf("APPLE");
        else if (value % 2 == ODD)
            System.out.printf("BANANA");
        else
            System.out.printf("CHERRY");
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_bank"
   code_html=code_block2
   answer="APPLE"
   tags="Java, 조건문"
%}

---

<div class="quiz-number">문제 3</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int arr[] = {7, 6, 5, 4, 3};
        int k = 4, total = 0;

        do {
            arr[k] = arr[k] % 4;
            total = total + arr[k];
            k--;
        } while (k > 0);

        System.out.printf("%d", total);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_bank"
   code_html=code_block3
   answer="6"
   tags="Java, 반복문"
%}

---

<div class="quiz-number">문제 4</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    static void countdown(int n) {
        if (n <= 0)
            return;
        System.out.printf("%d ", n);
        countdown(n - 1);
    }

    public static void main(String[] args) {
        countdown(4);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_bank"
   code_html=code_block4
   answer="4 3 2 1"
   tags="Java, 재귀"
%}

---

<div class="quiz-number">문제 5</div><strong>다음은 피보나치 수를 구하는 Java 프로그램이다. 괄호 ①, ②에 들어갈 알맞은 코드를 쉼표로 구분하여 작성하시오.</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    static int Fibo(int n) {
        if (n == 0)
            return 0;
        else if (n == 1)
            return ( ① );
        else
            return Fibo(( ② )) + Fibo(n - 1);
    }

    public static void main(String[] args) {
        for (int i = 0; i < 8; i++)
            System.out.printf("%d ", Fibo(i));
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_bank"
   code_html=code_block5
   answer="1, n - 2|1,n-2|1, n-2"
   tags="Java, 재귀"
%}

---

<div class="quiz-number">문제 6</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        for (int k = 7; k > 0; k--) {
            switch (k % 2) {
            case 1:
                System.out.printf("%d", k);
                break;
            default:
                System.out.printf("#");
                break;
            }
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_bank"
   code_html=code_block6
   answer="7#5#3#1"
   tags="Java, switch"
%}

---

<div class="quiz-number">문제 7</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int x, y = 15;
        for (x = 0; x < 4; ++x, y -= x);
        System.out.printf("%d, %d", x, y);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7_bank"
   code_html=code_block7
   answer="4, 5"
   tags="Java, 반복문"
%}

---

<div class="quiz-number">문제 8</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>data = [0, 0, 0, 0, 5]

for m in range(4, -1, -1):
    for n in range(4, m, -1):
        data[m] += data[n]

for m in range(5):
    print(data[m], end=" ")</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8_bank"
   code_html=code_block8
   answer="25 15 10 5 5"
   tags="Python, 리스트"
%}

---

<div class="quiz-number">문제 9</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def remove_char(text):
    return text.replace('-', '')

s = "A-B-C-D-E-F"
s = remove_char(s)
print(s)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_bank"
   code_html=code_block9
   answer="ABCDEF"
   tags="Python, 문자열"
%}

---

<div class="quiz-number">문제 10</div><strong>다음은 50 이하의 소수 개수를 구하는 Python 프로그램이다. 괄호에 들어갈 알맞은 조건식을 작성하시오.</strong>

{% capture code_block10 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def is_prime(num):
    for k in range(2, num):
        if (        ):
            return 0
    return 1

limit = 50
count = 0

for k in range(2, limit + 1):
    count += is_prime(k)

print(f"{limit} 이하의 소수는 {count}개입니다.")</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz10_bank"
   code_html=code_block10
   answer="num % k == 0"
   tags="Python, 소수"
%}

---

# 예상문제은행 Part 2

<div class="quiz-number">문제 11</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block11 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        String msg = "CODE" + 20 + 25;
        System.out.println(msg);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_bank"
   code_html=code_block11
   answer="CODE2025"
   tags="Java, 문자열"
%}

---

<div class="quiz-number">문제 12</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block12 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        char val = 0x05;
        System.out.printf("%04x", val << 3);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz12_bank"
   code_html=code_block12
   answer="0028"
   tags="Java, 비트연산"
%}

---

<div class="quiz-number">문제 13</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block13 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int m = 13;
        int n = 7;
        int result = m ^ n;
        System.out.println(result);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz13_bank"
   code_html=code_block13
   answer="10"
   tags="Java, 비트연산"
%}

---

<div class="quiz-number">문제 14</div><strong>다음은 홀수의 합을 구하는 Java 프로그램이다. 괄호에 들어갈 알맞은 코드를 작성하시오.</strong>

{% capture code_block14 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int total = 0;
        for (int k = 1; k <= 10; k++) {
            if (k % 2 == 1)
                (                     );
        }
        System.out.println("홀수의 합 = " + total);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz14_bank"
   code_html=code_block14
   answer="total += k|total = total + k"
   tags="Java, 반복문"
%}

---

<div class="quiz-number">문제 15</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block15 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int result = multiply(5, 3);
        System.out.println(result);
    }

    public static int multiply(int x, int y) {
        int product;
        return product = x * y;
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz15_bank"
   code_html=code_block15
   answer="15"
   tags="Java, 함수"
%}

---

<div class="quiz-number">문제 16</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block16 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int p, q, r, answer;
        p = 15;
        q = 25;
        r = 35;
        answer = p < q ? q++ : --r;
        System.out.printf("%d %d %d\n", answer, q, r);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz16_bank"
   code_html=code_block16
   answer="25 26 35"
   tags="Java, 삼항연산자"
%}

---

<div class="quiz-number">문제 17</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block17 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        StringBuffer sb = new StringBuffer();
        sb.append("JAVA");
        sb.insert(2, "TEST");
        System.out.print(sb.toString());
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz17_bank"
   code_html=code_block17
   answer="JATESTVA"
   tags="Java, StringBuffer"
%}

---

<div class="quiz-number">문제 18</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block18 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Main {
    public static void main(String[] args) {
        int[] nums = {2, 7, 4, 9, 3, 6};
        Filter f = new Filter();
        f.process(nums, 3);
    }
}

class Filter {
    void process(int[] arr, int mod) {
        int k;
        if (mod > 1) {
            for (k = 0; k < arr.length; k++) {
                if ((k + 1) % mod == 0)
                    System.out.printf("%d", arr[k]);
            }
        } else {
            for (k = 0; k < arr.length; k++) {
                System.out.printf("%d", arr[k]);
            }
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz18_bank"
   code_html=code_block18
   answer="46"
   tags="Java, 배열"
%}

---

<div class="quiz-number">문제 19</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block19 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int val;
        val = 25;
        modify(val);
        System.out.printf("%d", val);
    }

    static void modify(int val) {
        val = val + 5;
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz19_bank"
   code_html=code_block19
   answer="25"
   tags="Java, 매개변수"
%}

---

<div class="quiz-number">문제 20</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block20 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        String text = "#hello#";
        int len = text.length();
        char[] chars = new char[len];
        len--;
        for (int i = len; i >= 0; i--)
            chars[len - i] = text.charAt(i);
        for (char c : chars)
            System.out.printf("%c", c);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz20_bank"
   code_html=code_block20
   answer="#olleh#"
   tags="Java, 문자열"
%}

---

# 예상문제은행 Part 3

<div class="quiz-number">문제 21</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block21 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int k, total = 0;
        for (k = 1; k <= 8; ++k, total += k);
        System.out.printf("%d, %d\n", k, total);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz21_bank"
   code_html=code_block21
   answer="9, 44"
   tags="Java, 반복문"
%}

---

<div class="quiz-number">문제 22</div><strong>다음은 입력받은 숫자의 홀짝 여부를 판단하는 Java 프로그램이다. 괄호에 들어갈 알맞은 조건식을 작성하시오.</strong>

{% capture code_block22 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>import java.util.Scanner;

public class Test {
    public static void main(String[] args) {
        int number;
        Scanner sc = new Scanner(System.in);
        number = sc.nextInt();
        if ( (        ) == 0 )
            System.out.printf("%d는 짝수\n", number);
        else
            System.out.printf("%d는 홀수\n", number);
        sc.close();
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz22_bank"
   code_html=code_block22
   answer="number % 2"
   tags="Java, 조건문"
%}

---

<div class="quiz-number">문제 23</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오. (줄바꿈은 /로 구분)</strong>

{% capture code_block23 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int n = 0, acc = 0;
        for (n = 1; n <= 4; ++n, acc += n)
            System.out.printf("n=%d acc=%d\n", n, acc);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz23_bank"
   code_html=code_block23
   answer="n=1 acc=0/n=2 acc=2/n=3 acc=5/n=4 acc=9"
   tags="Java, 반복문"
%}

---

<div class="quiz-number">문제 24</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block24 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int m, n, result;
        m = 15;
        n = 25;
        result = calc(m, n);
        System.out.printf("m=%d, n=%d, result=%d\n", m, n, result);
    }

    static int calc(int x, int y) {
        int z;
        if (x == y) z = x + y;
        else z = x - y;
        return(z);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz24_bank"
   code_html=code_block24
   answer="m=15, n=25, result=-10"
   tags="Java, 함수"
%}

---

<div class="quiz-number">문제 25</div><strong>다음 Java 프로그램의 괄호에 들어갈 알맞은 예약어를 &lt;보기&gt;에서 찾아 기호로 작성하시오.</strong>

{% capture code_block25 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>interface Calculator {
    public void compute(int n);
}

class Doubler (      ) Calculator {
    public void compute(int n) {
        System.out.print(n * 2);
    }
}

public class Test {
    public static void main(String[] args) {
        Calculator c = new Doubler();
        c.compute(25);
    }
}

// 실행결과: 50

&lt;보기&gt;
ㄱ new
ㄴ abstract
ㄷ super
ㄹ extends
ㅁ implements</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz25_bank"
   code_html=code_block25
   answer="ㅁ"
   tags="Java, 인터페이스"
%}

---

<div class="quiz-number">문제 26</div><strong>다음 Python 프로그램의 괄호에 들어갈 예약어를 작성하시오.</strong>

{% capture code_block26 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>(      ) Product:
    name = '노트북'
    code = 'A1001'
    price = 1500000
    available = True

item = Product()
print(item.name)
print(item.code)
print(item.price)
print(item.available)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz26_bank"
   code_html=code_block26
   answer="class"
   tags="Python, 클래스"
%}

---

<div class="quiz-number">문제 27</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block27 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>n = total = 0

while n < 12:
    n += 1
    if n % 3 != 0:
        continue
    total += n

print(total)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz27_bank"
   code_html=code_block27
   answer="30"
   tags="Python, 반복문"
%}

---

<div class="quiz-number">문제 28</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block28 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>x, y = 5, 6
z = x | y
print(z)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz28_bank"
   code_html=code_block28
   answer="7"
   tags="Python, 비트연산"
%}

---

<div class="quiz-number">문제 29</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block29 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>total = 0
for k in range(1, 8):
    total += k
print(k, total)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz29_bank"
   code_html=code_block29
   answer="7 28"
   tags="Python, 반복문"
%}

---

<div class="quiz-number">문제 30</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오. (줄바꿈은 /로 구분)</strong>

{% capture code_block30 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>s = "Hello World"
print("%-12.5s" % s)
print("%12.5s" % s)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz30_bank"
   code_html=code_block30
   answer="Hello       /       Hello"
   tags="Python, 서식"
%}

---

<div class="quiz-number">문제 31</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block31 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>val1 = 15 + 15 % 6 - 15 % 7
val2 = 15 * 15 % 6 - 15 % 7 + 3
print("%d, %d" % (val1, val2))</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz31_bank"
   code_html=code_block31
   answer="17, 5"
   tags="Python, 연산자"
%}

---

# 예상문제은행 Part 4

<div class="quiz-number">문제 32</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block32 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>x, z = 16, -2
y = x << 3
x >>= 2
z = z << 3
print(x, y, z)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz32_bank"
   code_html=code_block32
   answer="4 128 -16"
   tags="Python, 비트연산"
%}

---

<div class="quiz-number">문제 33</div><strong>다음은 1부터 50까지의 합을 구하는 Python 프로그램이다. 괄호에 들어갈 알맞은 조건식을 작성하시오.</strong>

{% capture code_block33 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>n, total = 0, 0
while (        ):
    n += 1
    total += n
    if n >= 50:
        break
print(total)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz33_bank"
   code_html=code_block33
   answer="True|n < 51|n <= 50"
   tags="Python, 반복문"
%}

---

<div class="quiz-number">문제 34</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block34 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def swap():
    global a, b
    temp = a
    a = b
    b = temp

a, b = 30, 50
swap()
print(f"a={a}, b={b}")</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz34_bank"
   code_html=code_block34
   answer="a=50, b=30"
   tags="Python, 함수"
%}

---

<div class="quiz-number">문제 35</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block35 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>word = 'Python'
length = len(word)
chars = list()

for idx in range(length):
    chars.append(word[idx])

for idx in range(length-1, -1, -1):
    print(chars[idx], end='')</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz35_bank"
   code_html=code_block35
   answer="nohtyP"
   tags="Python, 리스트"
%}

---

<div class="quiz-number">문제 36</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block36 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>n, acc = 1, 0
while n <= 8:
    acc += n
    n += 3

print(f"n={n}, acc={acc}")</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz36_bank"
   code_html=code_block36
   answer="n=10, acc=12"
   tags="Python, 반복문"
%}

---

<div class="quiz-number">문제 37</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block37 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>matrix = [[1, 0, 1, 0, 1],
          [0, 1, 0, 1]]

total, count = 0, 0

for row in matrix:
    for val in row:
        total += val
    count = count + len(row)

print(count, total)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz37_bank"
   code_html=code_block37
   answer="9 5"
   tags="Python, 2차원 리스트"
%}

---

<div class="quiz-number">문제 38</div><strong>다음은 피보나치 수열의 합을 구하는 Python 프로그램이다. 괄호 ①, ②에 들어갈 알맞은 답을 쉼표로 구분하여 작성하시오.</strong>

{% capture code_block38 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>first, second = 1, 1
total = first + second
count = int(input())

for k in range(3, count + 1):
    third = first + second
    total = ( ① )
    first = second
    ( ② )

print(total)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz38_bank"
   code_html=code_block38
   answer="total + third, second = third|y + c, b = c"
   tags="Python, 피보나치"
%}

---

<div class="quiz-number">문제 39</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block39 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def display(val1, val2 = 5):
    print('x =', val1, ', y =', val2)

display(15)</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz39_bank"
   code_html=code_block39
   answer="x = 15 , y = 5"
   tags="Python, 함수"
%}

---

<div class="quiz-number">문제 40</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block40 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        String text = "AAXAAYAAZAA";
        String[] parts = text.split("A");
        System.out.print(parts[2]);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz40_bank"
   code_html=code_block40
   answer="X"
   tags="Java, 문자열"
%}

---

# 예상문제은행 Part 5

<div class="quiz-number">문제 41</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block41 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {

    static class Item {
        int data;
        Item next;
        Item(int d) { this.data = d; }
    }

    static void process(Item item) {
        while (item != null && item.next != null) {
            int temp = item.data;
            item.data = item.next.data;
            item.next.data = temp;
            item = item.next.next;
        }
    }

    public static void main(String[] args) {
        Item i1 = new Item(5);
        Item i2 = new Item(10);
        Item i3 = new Item(15);

        i1.next = i3;
        i3.next = i2;

        process(i1);
        process(i1);

        Item cur = i1;
        while (cur != null) {
            System.out.printf("%d", cur.data);
            cur = cur.next;
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz41_bank"
   code_html=code_block41
   answer="51510"
   tags="Java, 연결리스트"
%}

---

<div class="quiz-number">문제 42</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오. (줄바꿈은 /로 구분)</strong>

{% capture code_block42 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Counter {
    public int x = 30;
    static int y = 0;
}

public class Test {
    public static void main(String[] args) {
        int x = 15;
        Counter.y = x;
        Counter c = new Counter();

        System.out.println(Counter.y++);
        System.out.println(c.y);
        System.out.println(x);
        System.out.print(c.x);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz42_bank"
   code_html=code_block42
   answer="15/16/15/30"
   tags="Java, static"
%}

---

<div class="quiz-number">문제 43</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오. (줄바꿈은 /로 구분)</strong>

{% capture code_block43 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {

        String s1 = "Hello";
        String s2 = "Hello";
        String s3 = new String("Hello");

        System.out.println(s1 == s2);
        System.out.println(s1 == s3);
        System.out.println(s1.equals(s3));
        System.out.println(s2.equals(s3));
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz43_bank"
   code_html=code_block43
   answer="true/false/true/true"
   tags="Java, 문자열비교"
%}

---

<div class="quiz-number">문제 44</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block44 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class DataBox {
    int p;
    int q;
    int r;
}

public class Test {
    public static void main(String[] args) {
        DataBox box = new DataBox();
        box.p = 20;
        box.q = 30;
        compute(box);

        System.out.printf("p=%d, q=%d, r=%d\n",
                          box.p, box.q, box.r);
    }

    static void compute(DataBox box) {
        box.p += 10;
        box.q -= 10;

        if (box.p <= box.q)
            box.r = box.p + box.q;
        else
            box.r = box.p - box.q;
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz44_bank"
   code_html=code_block44
   answer="p=30, q=20, r=10"
   tags="Java, 클래스"
%}

---

<div class="quiz-number">문제 45</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오. (줄바꿈은 /로 구분)</strong>

{% capture code_block45 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {

    static int[] data = new int[4];
    static int ptr = -1;

    public static void main(String[] args) {

        add(50);
        add(60);
        add(70);
        remove();
        add(80);
        add(90);
        remove();
    }

    static void add(int val) {
        ptr++;
        if (ptr >= 4)
            System.out.printf("overflow");
        else
            data[ptr] = val;
    }

    static void remove() {
        if (ptr < 0)
            System.out.printf("underflow");
        else
            System.out.printf("%d삭제\n", data[ptr--]);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz45_bank"
   code_html=code_block45
   answer="70삭제/90삭제"
   tags="Java, 스택"
%}

---

<div class="quiz-number">문제 46</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block46 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void compare(int[] m, int[] n) {
        if (m == n)
            System.out.print("Y");
        else
            System.out.print("X");
    }

    public static void main(String[] args) {
        int p[] = new int[] {5, 10, 15};
        int q[] = new int[] {5, 10, 15};
        int r[] = new int[] {5, 10};

        compare(p, q);
        compare(q, r);
        compare(p, r);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz46_bank"
   code_html=code_block46
   answer="XXX"
   tags="Java, 배열비교"
%}

---

<div class="quiz-number">문제 47</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block47 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static String unique(String s, int idx, boolean[] check) {
        if (idx < 0) return "";
        char ch = s.charAt(idx);
        String result = unique(s, idx - 1, check);

        if (!check[ch]) {
            check[ch] = true;
            return ch + result;
        }
        return result;
    }

    public static void main(String[] args) {
        String text = "xyzxyxz";
        int len = text.length();
        boolean[] check = new boolean[256];
        System.out.print(unique(text, len - 1, check));
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz47_bank"
   code_html=code_block47
   answer="xyz"
   tags="Java, 재귀"
%}

---

<div class="quiz-number">문제 48</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block48 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>interface Filter {
    int calculate(int[] arr, boolean positive);
}

public class Test {
    public static void main(String[] args) {
        int nums[] = {-3, -2, -1, 0, 1, 2, 3};
        SignFilter sf = new SignFilter();
        System.out.print(sf.calculate(nums, true) + ", " + sf.calculate(nums, false));
    }
}

class SignFilter implements Filter {
    public int calculate(int[] arr, boolean positive) {
        int sum = 0;
        for (int i = 0; i < arr.length; i++) {
            if ((positive && arr[i] > 0) || (!positive && arr[i] < 0)) {
                sum += arr[i];
            }
        }
        return sum;
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz48_bank"
   code_html=code_block48
   answer="6, -6"
   tags="Java, 인터페이스"
%}

---

<div class="quiz-number">문제 49</div><strong>다음 Python 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block49 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>def find(text, pattern):
    count = 0
    for idx in range(len(text)):
        part = text[idx:idx+len(pattern)]
        if part == pattern:
            count += 1
    return count

text = "abcabcabcabc"
p1 = "bc"
p2 = "ca"
print(f"bc{find(text, p1)} ca{find(text, p2)}")</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz49_bank"
   code_html=code_block49
   answer="bc4 ca3"
   tags="Python, 문자열"
%}

---

<div class="quiz-number">문제 50</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block50 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Output {
    void show(Integer x) {
        System.out.print("X" + x);
    }

    void show(Object x) {
        System.out.print("Y" + x);
    }

    void show(Number x) {
        System.out.print("Z" + x);
    }
}

public class Test {
    public static void main(String[] args) {
        new Container&lt;&gt;(5).display();
    }

    public static class Container&lt;T&gt; {
        T item;

        public Container(T t) {
            item = t;
        }

        public void display() {
            new Output().show(item);
        }
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz50_bank"
   code_html=code_block50
   answer="Y5"
   tags="Java, 제네릭"
%}

---

<div class="quiz-number">문제 51</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block51 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    static String[] arr = new String[3];

    static void check(String[] arr, int size) {
        for (int k = 1; k < size; k++) {
            if (arr[k - 1].equals(arr[k])) {
                System.out.print("Y");
            } else {
                System.out.print("X");
            }
        }

        for (String s : arr) {
            System.out.print(s);
        }
    }

    public static void main(String[] args) {
        arr[0] = "B";
        arr[1] = "B";
        arr[2] = new String("B");
        check(arr, 3);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz51_bank"
   code_html=code_block51
   answer="YYBBB"
   tags="Java, 문자열비교"
%}

---

<div class="quiz-number">문제 52</div><strong>다음 Java 프로그램의 실행 결과를 작성하시오.</strong>

{% capture code_block52 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>class Database {
    private static Database _instance = null;
    private int queries = 0;

    public static Database getInstance() {
        if (_instance == null) {
            _instance = new Database();
            return _instance;
        }
        return _instance;
    }

    public void query() {
        queries++;
    }

    public int getQueries() {
        return queries;
    }
}

public class Test {
    public static void main(String[] args) {
        Database db1 = Database.getInstance();
        db1.query();
        db1.query();

        Database db2 = Database.getInstance();
        db2.query();

        Database db3 = Database.getInstance();
        db3.query();
        db3.query();

        System.out.print(db1.getQueries());
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz52_bank"
   code_html=code_block52
   answer="5"
   tags="Java, 싱글톤"
%}

---

# 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Java 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>연산자 우선순위</strong>: 단항 > 산술 > 시프트 > 관계 > 비트 > 논리 > 삼항 > 대입</li>
<li><strong>증감연산자</strong>: <code>++x</code>(전위), <code>x++</code>(후위) 차이 주의</li>
<li><strong>문자열 비교</strong>: <code>==</code>는 주소 비교, <code>equals()</code>는 내용 비교</li>
<li><strong>static 변수</strong>: 클래스 변수로 모든 인스턴스가 공유</li>
<li><strong>인터페이스</strong>: <code>implements</code> 키워드로 구현</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">Python 핵심 포인트</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>비트연산</strong>: <code>&</code>(AND), <code>|</code>(OR), <code>^</code>(XOR), <code><<</code>(좌시프트), <code>>></code>(우시프트)</li>
<li><strong>슬라이싱</strong>: <code>[시작:끝:증가]</code>, 끝 인덱스 미포함</li>
<li><strong>global 키워드</strong>: 함수 내에서 전역변수 수정 시 필요</li>
<li><strong>기본 매개변수</strong>: 함수 정의 시 기본값 지정 가능</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">자료구조</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>스택</strong>: LIFO(후입선출), push/pop 연산</li>
<li><strong>연결리스트</strong>: 노드와 포인터로 구성</li>
<li><strong>싱글톤</strong>: 인스턴스를 하나만 생성하는 디자인 패턴</li>
</ul>

</div>

---
