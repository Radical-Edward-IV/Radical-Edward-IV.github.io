---
layout: article
title: 11. 문자열과 함수
permalink: /notes/kr/c-basic/chapter-11
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C 기초 과정 강의 노트, 문자열과 포인터, 문자/문자열 입출력 함수, 문자열 처리 함수를 다룹니다.
keywords: "C언어, 문자열, 포인터, 문자열함수, strlen, strcpy, strcat, strcmp, getchar, putchar, gets, puts"
---

<script src="/assets/js/quiz.js"></script>

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
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=C%20Programming%20Basic&reversal=false&textBg=false)

---

## 1. 문자열과 포인터

### 문자열의 두 가지 표현 방법

C 언어에서 문자열은 <span class="blue-text">널 문자(\0)로 끝나는 문자 배열</span>입니다. 문자열을 선언하는 방법은 크게 두 가지가 있습니다.

**방법 1: 배열 기반 문자열**

```c
char str[] = "Hello";
```

이 방법은 문자 배열을 선언하고 문자열로 초기화합니다. 배열의 크기는 자동으로 6이 됩니다(Hello 5글자 + 널 문자 1개).

| H | e | l | l | o | \0 |
|---|---|---|---|---|-----|
| [0] | [1] | [2] | [3] | [4] | [5] |

**방법 2: 포인터 기반 문자열**

```c
char *str = "Hello";
```

이 방법은 문자열 상수 "Hello"를 메모리에 저장하고, 그 시작 주소를 포인터 변수 str에 저장합니다.

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>두 방법 모두 같은 방식으로 출력 가능</strong><br>
printf("%s", str); 형태로 문자열을 출력할 수 있습니다.
</div>

### 배열 기반 vs 포인터 기반 차이점

두 방법은 출력은 동일하지만, **수정 가능 여부**에서 중요한 차이가 있습니다.

| 구분 | 배열 기반 | 포인터 기반 |
|------|-----------|-------------|
| **문자 변경** | ✅ 가능 | ❌ 불가능 |
| **주소 변경** | ❌ 불가능 | ✅ 가능 |
| **특징** | 변수 형태의 문자열 | 상수 형태의 문자열 |

**배열 기반 문자열:**

```c
char str1[] = "Good";
str1[0] = 'F';      // ✅ 가능: "Food"로 변경
str1 = "New";       // ❌ 불가능: 배열 이름은 상수
```

**포인터 기반 문자열:**

```c
char *str2 = "Bad";
str2[0] = 'S';      // ❌ 불가능: 문자열 상수 영역 (실행 시 오류 가능)
str2 = "New Bad";   // ✅ 가능: 포인터가 다른 문자열을 가리킴
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 중요</strong><br>
• 배열 기반: <span class="green-text">문자 변경 O</span>, <span class="red-text">주소 변경 X</span><br>
• 포인터 기반: <span class="red-text">문자 변경 X</span>, <span class="green-text">주소 변경 O</span>
</div>

### 실습 1

다음 코드의 실행 결과를 확인해보세요:

```c
#include <stdio.h>

int main() {
    char arr[] = "Hello";
    char *ptr = "World";

    printf("배열 기반: %s\n", arr);
    printf("포인터 기반: %s\n", ptr);

    // 배열 기반: 문자 변경 가능
    arr[0] = 'h';
    printf("변경 후 배열: %s\n", arr);

    // 포인터 기반: 다른 문자열을 가리킬 수 있음
    ptr = "New World";
    printf("변경 후 포인터: %s\n", ptr);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
배열 기반: Hello
포인터 기반: World
변경 후 배열: hello
변경 후 포인터: New World
</pre>

</details>

---

## 2. 문자 단위 입출력 함수

### putchar와 getchar 함수

C 언어는 **한 글자씩** 입출력하는 함수를 제공합니다.

| 함수 | 기능 | 사용 예 |
|------|------|---------|
| `putchar(문자)` | 문자 하나 출력 | `putchar('A');` |
| `getchar()` | 문자 하나 입력 | `ch = getchar();` |

### 기본 사용법

```c
#include <stdio.h>

int main() {
    int ch;

    printf("문자 입력: ");
    ch = getchar();    // 문자 하나 입력

    printf("입력한 문자: ");
    putchar(ch);       // 문자 하나 출력
    putchar('\n');

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
문자 입력: A
입력한 문자: A
</pre>

</details>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 getchar의 반환 타입</strong><br>
getchar()는 int형을 반환합니다. 이는 EOF(-1) 값을 구분하기 위함입니다.
</div>

### EOF (End Of File)

EOF는 <span class="blue-text">파일의 끝</span> 또는 <span class="blue-text">입력 종료</span>를 나타내는 상수입니다.

**EOF가 반환되는 경우:**
- 읽어 들일 데이터가 더 이상 없을 때
- Windows: `Ctrl + Z` 입력
- macOS/Linux: `Ctrl + D` 입력

### 실습 2 - EOF를 이용한 입력 종료

```c
#include <stdio.h>

int main() {
    int ch;

    printf("문자를 입력하세요 (종료: Ctrl+Z 또는 Ctrl+D):\n");

    while (1) {
        ch = getchar();

        if (ch == EOF)  // 입력 종료
            break;

        putchar(ch);
    }

    printf("\n입력이 종료되었습니다.\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
문자를 입력하세요 (종료: Ctrl+Z 또는 Ctrl+D):
Hello
Hello
World
World
^Z
입력이 종료되었습니다.
</pre>

</details>

---

## 3. 문자열 단위 입출력 함수

### puts와 gets 함수

<span class="blue-text">문자열 전체</span>를 한 번에 입출력하는 함수입니다.

| 함수 | 기능 | 사용 예 |
|------|------|---------|
| `puts(문자열)` | 문자열 출력 후 **자동 줄바꿈** | `puts("Hello");` |
| `gets(배열)` | 문자열 입력 (공백 포함) | `gets(str);` |

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ gets 함수의 위험성</strong><br>
gets() 함수는 <span class="red-text">버퍼 오버플로우</span> 위험이 있어 최신 컴파일러에서는 사용이 권장되지 않습니다.<br>
대신 <span class="green-text">fgets()</span> 함수 사용을 권장합니다.
</div>

### 실습 3

```c
#include <stdio.h>

int main() {
    char str[100];

    printf("문자열 입력: ");
    gets(str);

    printf("입력한 문자열:\n");
    puts(str);  // 자동으로 줄바꿈

    printf("이 문장은 다음 줄에 출력됩니다.\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
문자열 입력: Hello World
입력한 문자열:
Hello World
이 문장은 다음 줄에 출력됩니다.
</pre>

<p style="margin-top: 10px;">
<strong>puts vs printf:</strong><br>
• puts("Hello")는 자동으로 줄바꿈<br>
• printf("Hello")는 줄바꿈 없음 (명시적으로 \n 필요)
</p>

</details>

---

## 4. 문자열 처리 함수

C 언어는 문자열을 다루기 위한 다양한 표준 함수를 제공합니다. 이 함수들은 <span class="yellow-code">string.h</span> 헤더 파일에 선언되어 있습니다.

```c
#include <string.h>
```

### 주요 문자열 함수

| 함수 | 기능 | 반환값 |
|------|------|--------|
| `strlen(str)` | 문자열 길이 | 정수 |
| `strcpy(dest, src)` | 문자열 복사 | dest 주소 |
| `strncpy(dest, src, n)` | n개 문자 복사 | dest 주소 |
| `strcat(dest, src)` | 문자열 이어붙이기 | dest 주소 |
| `strncat(dest, src, n)` | n개 문자 이어붙이기 | dest 주소 |
| `strcmp(str1, str2)` | 문자열 비교 | 0, 양수, 음수 |
| `strncmp(str1, str2, n)` | n개 문자 비교 | 0, 양수, 음수 |

---

### strlen - 문자열 길이

문자열의 <span class="blue-text">널 문자를 제외한</span> 길이를 반환합니다.

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[] = "Hello";
    char str2[] = "C Programming";

    printf("str1의 길이: %d\n", strlen(str1));  // 5
    printf("str2의 길이: %d\n", strlen(str2));  // 13

    return 0;
}
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>strlen vs sizeof</strong><br>
• <code>strlen("Hello")</code> → 5 (문자 개수)<br>
• <code>sizeof("Hello")</code> → 6 (널 문자 포함 바이트 수)
</div>

---

### strcpy와 strncpy - 문자열 복사

**strcpy(dest, src)**: 전체 문자열 복사

```c
char src[] = "Hello";
char dest[20];

strcpy(dest, src);  // "Hello"가 dest에 복사됨
```

**strncpy(dest, src, n)**: n개 문자만 복사

```c
char src[] = "Hello World";
char dest[20];

strncpy(dest, src, 5);  // "Hello"만 복사
dest[5] = '\0';         // 수동으로 널 문자 추가 필요!
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ strncpy 주의사항</strong><br>
strncpy는 n개 문자만 복사하므로 <span class="red-text">자동으로 널 문자를 추가하지 않을 수 있습니다</span>.<br>
반드시 수동으로 널 문자를 추가해야 합니다!
</div>

### 실습 4

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[50] = "apple is good";
    char str2[50] = "berry is good";
    char str3[50];

    printf("원본 문자열:\n");
    printf("str1: %s\n", str1);
    printf("str2: %s\n", str2);

    // str1 전체를 str3에 복사
    strcpy(str3, str1);
    printf("\nstrcpy 후 str3: %s\n", str3);

    // str1의 5개 문자를 str2에 복사
    strncpy(str2, str1, 5);
    str2[5] = ' ';  // 기존 문자 유지
    printf("strncpy 후 str2: %s\n", str2);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
원본 문자열:
str1: apple is good
str2: berry is good

strcpy 후 str3: apple is good
strncpy 후 str2: apple is good
</pre>

</details>

---

### strcat과 strncat - 문자열 이어붙이기

**strcat(dest, src)**: src를 dest 뒤에 이어붙이기

```c
char str[50] = "Hello ";
strcat(str, "World");  // "Hello World"
```

**strncat(dest, src, n)**: src의 n개 문자만 이어붙이기

```c
char str[50] = "Hello ";
strncat(str, "World!", 5);  // "Hello World"
```

### 실습 5

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[50] = "Michael ";
    char str2[50] = "Michael ";

    // str1에 "Bolton" 이어붙이기
    strcat(str1, "Bolton");
    printf("strcat 결과: %s\n", str1);

    // str2에 "Jackson Five"의 7글자만 이어붙이기
    strncat(str2, "Jackson Five", 7);
    printf("strncat 결과: %s\n", str2);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
strcat 결과: Michael Bolton
strncat 결과: Michael Jackson
</pre>

</details>

---

### strcmp와 strncmp - 문자열 비교

**strcmp(str1, str2)**: 두 문자열 비교

| 조건 | 반환값 |
|------|--------|
| str1 == str2 | `0` |
| str1 < str2 (사전순 앞) | `음수` |
| str1 > str2 (사전순 뒤) | `양수` |

**strncmp(str1, str2, n)**: 앞 n개 문자만 비교

```c
strcmp("apple", "apple")    // 0 (같음)
strcmp("apple", "banana")   // 음수 (apple이 앞)
strcmp("zebra", "apple")    // 양수 (zebra가 뒤)

strncmp("apple", "application", 3)  // 0 ("app"까지 같음)
```

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 문자열 비교 주의</strong><br>
<code>==</code> 연산자로는 문자열을 비교할 수 없습니다!<br>
<code>if (str1 == str2)</code> ❌ 주소 비교<br>
<code>if (strcmp(str1, str2) == 0)</code> ✅ 내용 비교
</div>

### 실습 6

```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[] = "apple";
    char str2[] = "banana";
    char str3[] = "apple";

    // strcmp 예제
    printf("strcmp(str1, str2) = %d\n", strcmp(str1, str2));  // 음수
    printf("strcmp(str1, str3) = %d\n", strcmp(str1, str3));  // 0
    printf("strcmp(str2, str1) = %d\n", strcmp(str2, str1));  // 양수

    // 문자열 같은지 확인
    if (strcmp(str1, str3) == 0) {
        printf("\nstr1과 str3는 같은 문자열입니다.\n");
    }

    // strncmp 예제
    printf("\nstrncmp(\"apple\", \"application\", 3) = %d\n",
           strncmp("apple", "application", 3));  // 0

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
strcmp(str1, str2) = -1
strcmp(str1, str3) = 0
strcmp(str2, str1) = 1

str1과 str3는 같은 문자열입니다.

strncmp("apple", "application", 3) = 0
</pre>

<p style="margin-top: 10px;">
strcmp의 정확한 반환값은 컴파일러마다 다를 수 있지만, 음수/0/양수의 의미는 동일합니다.
</p>

</details>

---

## 5. 종합 실습

### 문제 1 - 문자열 길이 (기초)

<div class="quiz-number">문제 1</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#include &lt;string.h&gt;

int main() {
    char str[] = "C Language";

    printf("%d", strlen(str));

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint1 %}
공백도 문자로 계산됩니다. 널 문자는 제외합니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   question=hint1
   code_html=code_block1
   answer="10"
   tags="문자열과 함수"
%}

---

### 문제 2 - 문자열 복사 (기초)

<div class="quiz-number">문제 2</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#include &lt;string.h&gt;

int main() {
    char src[] = "Hello";
    char dest[20];

    strcpy(dest, src);
    dest[0] = 'h';

    printf("%s %s", src, dest);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint2 %}
strcpy는 복사본을 만들므로 dest 변경이 src에 영향을 주지 않습니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   question=hint2
   code_html=code_block2
   answer="Hello hello"
   tags="문자열과 함수"
%}

---

### 문제 3 - 문자열 이어붙이기 (기초)

<div class="quiz-number">문제 3</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#include &lt;string.h&gt;

int main() {
    char str[50] = "Good";

    strcat(str, " Morning");

    printf("%s", str);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="Good Morning"
   tags="문자열과 함수"
%}

---

### 문제 4 - 문자열 비교 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는? (0, 양수, 음수 중 하나)</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#include &lt;string.h&gt;

int main() {
    char str1[] = "Apple";
    char str2[] = "Banana";

    int result = strcmp(str1, str2);

    if (result < 0)
        printf("음수");
    else if (result > 0)
        printf("양수");
    else
        printf("0");

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint4 %}
"Apple"은 "Banana"보다 사전순으로 앞에 있습니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   question=hint4
   code_html=code_block4
   answer="음수"
   tags="문자열과 함수"
%}

---

### 문제 5 - strncpy (중급)

<div class="quiz-number">문제 5</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#include &lt;string.h&gt;

int main() {
    char src[] = "Programming";
    char dest[20] = "XXXXXXXXXXXX";

    strncpy(dest, src, 4);
    dest[4] = '\0';

    printf("%s", dest);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint5 %}
strncpy는 4개 문자만 복사하고, 수동으로 널 문자를 추가했습니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=hint5
   code_html=code_block5
   answer="Prog"
   tags="문자열과 함수"
%}

---

### 문제 6 - 배열 vs 포인터 (중급)

<div class="quiz-number">문제 6</div><strong>다음 코드에서 컴파일 에러가 발생하는 줄 번호는?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main() {
    char arr[] = "Hello";
    char *ptr = "World";

    // 6행
    arr[0] = 'h';

    // 9행
    arr = "New Hello";

    // 12행
    ptr[0] = 'w';

    // 15행
    ptr = "New World";

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint6 %}
배열 이름은 상수이므로 다른 주소를 할당할 수 없습니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   question=hint6
   code_html=code_block6
   answer="9"
   tags="문자열과 함수"
%}

---

### 문제 7 - EOF (중급)

<div class="quiz-number">문제 7</div><strong>다음 중 EOF에 대한 설명으로 올바른 것은?</strong>

```
A. EOF는 파일의 끝을 나타내는 상수이다.
B. getchar()는 EOF를 반환할 수 있다.
C. Windows에서는 Ctrl+Z로 EOF를 입력한다.
D. 위의 모든 설명이 맞다.
```

{% capture hint7 %}
EOF는 End Of File의 약자로, 입력 종료를 나타냅니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz7"
   question=hint7
   answer="D"
   tags="문자열과 함수"
%}

---

### 문제 8 - 문자열 처리 종합 (고급)

<div class="quiz-number">문제 8</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#include &lt;string.h&gt;

int main() {
    char str1[50] = "Hello";
    char str2[50] = "Hello";
    char str3[50];

    strcpy(str3, str1);
    strcat(str3, " World");

    if (strcmp(str1, str2) == 0 && strcmp(str1, str3) != 0) {
        printf("%d", strlen(str3));
    }

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint8 %}
str3은 "Hello World"가 되며, 공백을 포함한 길이는 11입니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz8"
   question=hint8
   code_html=code_block8
   answer="11"
   tags="문자열과 함수"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 문자열과 포인터</strong><br>
• 배열 기반: <code>char str[] = "Hello";</code> (문자 변경 O, 주소 변경 X)<br>
• 포인터 기반: <code>char *str = "Hello";</code> (문자 변경 X, 주소 변경 O)<br><br>

<strong>2. 문자 단위 입출력</strong><br>
• <code>getchar()</code>: 문자 하나 입력<br>
• <code>putchar(ch)</code>: 문자 하나 출력<br>
• <code>EOF</code>: 입력 종료 (Ctrl+Z 또는 Ctrl+D)<br><br>

<strong>3. 문자열 단위 입출력</strong><br>
• <code>gets(str)</code>: 문자열 입력 (위험, fgets 권장)<br>
• <code>puts(str)</code>: 문자열 출력 (자동 줄바꿈)<br><br>

<strong>4. 문자열 처리 함수 (string.h)</strong><br>
• <code>strlen(str)</code>: 문자열 길이 (널 문자 제외)<br>
• <code>strcpy(dest, src)</code>: 문자열 복사<br>
• <code>strncpy(dest, src, n)</code>: n개 문자 복사<br>
• <code>strcat(dest, src)</code>: 문자열 이어붙이기<br>
• <code>strncat(dest, src, n)</code>: n개 문자 이어붙이기<br>
• <code>strcmp(str1, str2)</code>: 문자열 비교 (같으면 0)<br>
• <code>strncmp(str1, str2, n)</code>: n개 문자 비교<br><br>

<strong>5. 문자열 비교</strong><br>
• <code>strcmp</code> 반환값: 0(같음), 음수(str1이 앞), 양수(str1이 뒤)<br>
• <code>==</code> 연산자는 주소 비교, <code>strcmp</code>로 내용 비교<br><br>

<strong>6. 주의사항</strong><br>
• <code>strncpy</code>는 널 문자 자동 추가 안 될 수 있음<br>
• <code>gets</code>는 버퍼 오버플로우 위험 (fgets 권장)<br>
• 문자열 함수 사용 시 <code>#include &lt;string.h&gt;</code> 필수

</div>

---
