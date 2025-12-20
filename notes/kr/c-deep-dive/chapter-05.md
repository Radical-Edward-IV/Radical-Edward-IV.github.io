---
layout: article
title: 5. 동적 메모리 할당
permalink: /notes/kr/c-deep-dive/chapter-05
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C DeepDive 강의 노트, 힙 영역의 활용, malloc/calloc/realloc/free 함수, 메모리 누수 방지 방법을 다룹니다.
keywords: "C언어, 동적메모리할당, malloc, calloc, realloc, free, 힙영역, 메모리누수"
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

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=C%20Deep%20Dive&reversal=false&textBg=false)

---

## 1. 동적 메모리 할당이란?

동적 메모리 할당은 <span class="blue-text">프로그램 실행 중에 필요한 만큼 메모리를 할당</span>하는 기법입니다.

### 정적 메모리 vs 동적 메모리

| 구분 | 정적 메모리 | 동적 메모리 |
|------|-----------|-----------|
| **할당 영역** | 데이터/스택 영역 | 힙 영역 |
| **할당 시점** | 컴파일 타임 | 런타임 |
| **크기 결정** | 선언 시 고정 | 실행 중 결정 |
| **생명주기** | 자동 관리 | 수동 관리 |
| **예시** | `int arr[100];` | `malloc(100);` |

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>동적 메모리의 장점</strong><br>
• 필요한 만큼만 메모리 사용 (효율적)<br>
• 실행 중 크기 변경 가능<br>
• 큰 데이터 구조 생성 가능
</div>

### 동적 메모리가 필요한 이유

다음 코드는 문제가 발생할 수 있습니다.

```c
#include <stdio.h>
#include <string.h>

char *createString(void) {
    char str[100];  // 지역 변수 (스택 영역)

    printf("문자열 입력: ");
    scanf("%s", str);

    return str;  // ⚠️ 위험! 함수 종료 후 str은 소멸됨
}

int main(void) {
    char *result = createString();
    printf("결과: %s\n", result);  // 예측 불가능한 동작

    return 0;
}
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 문제점</strong><br>
지역 변수 <code>str</code>은 함수가 끝나면 스택에서 사라집니다.<br>
반환된 주소는 이미 해제된 메모리를 가리키므로 <span class="red-text">위험</span>합니다!
</div>

**해결책: 동적 메모리 할당**

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char *createString(void) {
    char *str = (char *)malloc(100);  // 힙 영역에 할당

    if (str == NULL) {
        printf("메모리 할당 실패\n");
        return NULL;
    }

    printf("문자열 입력: ");
    scanf("%s", str);

    return str;  // ✅ 안전! 힙 메모리는 유지됨
}

int main(void) {
    char *result = createString();

    if (result != NULL) {
        printf("결과: %s\n", result);
        free(result);  // 사용 후 메모리 해제
    }

    return 0;
}
```

---

## 2. malloc 함수

<span class="yellow-code">malloc</span> 함수는 <span class="blue-text">지정한 크기만큼 힙 메모리를 할당</span>합니다.

### malloc 함수의 사용법

```c
#include <stdlib.h>

void *malloc(size_t size);
```

- **매개변수**: 할당할 바이트 수
- **반환값**: 할당된 메모리의 주소 (void *)
- **실패 시**: NULL 반환

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 malloc 사용 패턴</strong><br>
<code>자료형 *포인터 = (자료형 *)malloc(sizeof(자료형) * 개수);</code>
</div>

### 기본 사용 예제

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int *ptr;

    // int 하나 크기만큼 메모리 할당
    ptr = (int *)malloc(sizeof(int));

    if (ptr == NULL) {
        printf("메모리 할당 실패\n");
        return 1;
    }

    *ptr = 100;
    printf("값: %d\n", *ptr);

    free(ptr);  // 메모리 해제

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
값: 100
</pre>

</details>

### 배열처럼 사용하기

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int *arr;
    int i;

    // int 5개 크기만큼 메모리 할당
    arr = (int *)malloc(sizeof(int) * 5);

    if (arr == NULL) {
        printf("메모리 할당 실패\n");
        return 1;
    }

    // 배열처럼 사용
    for (i = 0; i < 5; i++) {
        arr[i] = (i + 1) * 10;
    }

    printf("할당된 배열: ");
    for (i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    free(arr);  // 메모리 해제

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
할당된 배열: 10 20 30 40 50
</pre>

</details>

### malloc의 특징

- 할당된 메모리는 <span class="red-text">초기화되지 않음</span> (쓰레기 값 포함)
- 반드시 형 변환 필요: `(자료형 *)`
- NULL 체크 필수

---

## 3. calloc 함수

<span class="yellow-code">calloc</span> 함수는 malloc과 유사하지만 <span class="blue-text">메모리를 0으로 초기화</span>합니다.

### calloc 함수의 사용법

```c
#include <stdlib.h>

void *calloc(size_t count, size_t size);
```

- **매개변수 1**: 요소 개수
- **매개변수 2**: 각 요소의 크기
- **반환값**: 할당된 메모리의 주소 (void *)

### malloc vs calloc 비교

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int *arr1, *arr2;
    int i;

    // malloc: 초기화 안 됨
    arr1 = (int *)malloc(sizeof(int) * 5);

    // calloc: 0으로 초기화됨
    arr2 = (int *)calloc(5, sizeof(int));

    printf("malloc 결과: ");
    for (i = 0; i < 5; i++) {
        printf("%d ", arr1[i]);  // 쓰레기 값
    }

    printf("\ncalloc 결과: ");
    for (i = 0; i < 5; i++) {
        printf("%d ", arr2[i]);  // 모두 0
    }
    printf("\n");

    free(arr1);
    free(arr2);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기 (예시)</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
malloc 결과: -858993460 -858993460 -858993460 -858993460 -858993460
calloc 결과: 0 0 0 0 0
</pre>

<p style="margin-top: 10px;">
malloc은 쓰레기 값, calloc은 0으로 초기화됩니다.
</p>

</details>

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>calloc의 장점</strong><br>
• 자동으로 0 초기화<br>
• 배열 생성 시 안전<br>
• malloc보다 약간 느릴 수 있음
</div>

---

## 4. realloc 함수

<span class="yellow-code">realloc</span> 함수는 <span class="blue-text">이미 할당된 메모리 크기를 변경</span>합니다.

### realloc 함수의 사용법

```c
#include <stdlib.h>

void *realloc(void *ptr, size_t new_size);
```

- **매개변수 1**: 기존 메모리 주소
- **매개변수 2**: 새로운 크기 (바이트)
- **반환값**: 재할당된 메모리 주소

### realloc 동작 방식

1. 기존 위치에 충분한 공간이 있으면 → 같은 주소 반환
2. 공간이 부족하면 → 새 위치에 할당 후 데이터 복사, 새 주소 반환

### 기본 사용 예제

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int *arr;
    int i;

    // 초기 할당: int 3개
    arr = (int *)calloc(3, sizeof(int));
    arr[0] = 10;
    arr[1] = 20;
    arr[2] = 30;

    printf("초기 배열: ");
    for (i = 0; i < 3; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    // 크기 확장: int 5개로
    arr = (int *)realloc(arr, sizeof(int) * 5);

    if (arr == NULL) {
        printf("재할당 실패\n");
        return 1;
    }

    arr[3] = 40;
    arr[4] = 50;

    printf("확장 후 배열: ");
    for (i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    free(arr);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
초기 배열: 10 20 30
확장 후 배열: 10 20 30 40 50
</pre>

</details>

### 동적 배열 구현

실행 중에 크기를 조절하는 배열을 만들 수 있습니다.

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int *arr = NULL;
    int size = 0;
    int capacity = 2;
    int input;

    arr = (int *)calloc(capacity, sizeof(int));

    printf("정수를 입력하세요 (-1 종료):\n");

    while (1) {
        scanf("%d", &input);
        if (input == -1) break;

        // 용량 초과 시 2배로 확장
        if (size == capacity) {
            capacity *= 2;
            arr = (int *)realloc(arr, sizeof(int) * capacity);
            printf("[배열 확장: %d개]\n", capacity);
        }

        arr[size++] = input;
    }

    printf("\n입력한 숫자: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    free(arr);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기 (예시)</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
정수를 입력하세요 (-1 종료):
10
20
30
[배열 확장: 4개]
40
50
[배열 확장: 8개]
-1

입력한 숫자: 10 20 30 40 50
</pre>

</details>

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ realloc 주의사항</strong><br>
• 실패 시 NULL 반환, 기존 메모리는 유지됨<br>
• <code>arr = realloc(arr, ...);</code>는 위험! (실패 시 주소 손실)<br>
• 임시 포인터 사용 권장: <code>temp = realloc(arr, ...); if (temp) arr = temp;</code>
</div>

---

## 5. free 함수

<span class="yellow-code">free</span> 함수는 <span class="blue-text">할당된 메모리를 해제</span>합니다.

### free 함수의 사용법

```c
#include <stdlib.h>

void free(void *ptr);
```

- **매개변수**: 해제할 메모리 주소
- **반환값**: 없음

### free의 중요성

```c
#include <stdio.h>
#include <stdlib.h>

void memoryLeak(void) {
    int *ptr = (int *)malloc(sizeof(int) * 1000000);
    // free(ptr); 없음! → 메모리 누수
}

int main(void) {
    int i;

    for (i = 0; i < 10000; i++) {
        memoryLeak();  // 계속 메모리 할당만 함
    }

    printf("프로그램 종료\n");
    // 프로그램이 종료되어야 메모리 해제됨

    return 0;
}
```

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 메모리 누수 (Memory Leak)</strong><br>
할당한 메모리를 해제하지 않으면:<br>
• 프로그램이 사용하는 메모리 증가<br>
• 시스템 성능 저하<br>
• 최악의 경우 프로그램/시스템 다운
</div>

### 올바른 메모리 관리

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int *ptr;

    // 1. 메모리 할당
    ptr = (int *)malloc(sizeof(int) * 5);

    if (ptr == NULL) {
        printf("할당 실패\n");
        return 1;
    }

    // 2. 메모리 사용
    for (int i = 0; i < 5; i++) {
        ptr[i] = i * 10;
    }

    // 3. 메모리 해제
    free(ptr);

    // 4. 포인터 초기화 (선택사항, 권장)
    ptr = NULL;

    return 0;
}
```

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>메모리 관리 원칙</strong><br>
• malloc/calloc으로 할당 → free로 해제<br>
• 할당과 해제는 <strong>1:1 대응</strong><br>
• 해제 후 포인터에 NULL 대입 권장<br>
• 같은 메모리를 두 번 해제 금지
</div>

---

## 6. 메모리 관리 실전 예제

### 예제 1: 동적 문자열 처리

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char *getString(void) {
    char temp[100];
    char *str;

    printf("문자열 입력: ");
    scanf("%s", temp);

    // 실제 길이만큼 메모리 할당
    str = (char *)malloc(strlen(temp) + 1);

    if (str != NULL) {
        strcpy(str, temp);
    }

    return str;
}

int main(void) {
    char *result = getString();

    if (result != NULL) {
        printf("입력한 문자열: %s\n", result);
        printf("길이: %d 바이트\n", (int)strlen(result));
        free(result);
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
문자열 입력: Programming
입력한 문자열: Programming
길이: 11 바이트
</pre>

</details>

### 예제 2: 성적 관리 프로그램

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int n, i;
    int *scores;
    int sum = 0;
    double avg;

    printf("학생 수 입력: ");
    scanf("%d", &n);

    // 학생 수만큼 동적 할당
    scores = (int *)calloc(n, sizeof(int));

    if (scores == NULL) {
        printf("메모리 할당 실패\n");
        return 1;
    }

    // 성적 입력
    for (i = 0; i < n; i++) {
        printf("%d번 학생 점수: ", i + 1);
        scanf("%d", &scores[i]);
        sum += scores[i];
    }

    // 평균 계산
    avg = (double)sum / n;

    // 결과 출력
    printf("\n=== 결과 ===\n");
    printf("전체 점수: ");
    for (i = 0; i < n; i++) {
        printf("%d ", scores[i]);
    }
    printf("\n평균: %.2f점\n", avg);

    free(scores);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
학생 수 입력: 3
1번 학생 점수: 85
2번 학생 점수: 90
3번 학생 점수: 78

=== 결과 ===
전체 점수: 85 90 78
평균: 84.33점
</pre>

</details>

### 예제 3: 2차원 배열 동적 할당

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    int **matrix;
    int rows = 3, cols = 4;
    int i, j;

    // 행 포인터 배열 할당
    matrix = (int **)malloc(sizeof(int *) * rows);

    // 각 행에 대한 열 할당
    for (i = 0; i < rows; i++) {
        matrix[i] = (int *)malloc(sizeof(int) * cols);
    }

    // 값 초기화
    for (i = 0; i < rows; i++) {
        for (j = 0; j < cols; j++) {
            matrix[i][j] = i * cols + j + 1;
        }
    }

    // 출력
    printf("=== 행렬 출력 ===\n");
    for (i = 0; i < rows; i++) {
        for (j = 0; j < cols; j++) {
            printf("%3d ", matrix[i][j]);
        }
        printf("\n");
    }

    // 메모리 해제 (역순)
    for (i = 0; i < rows; i++) {
        free(matrix[i]);
    }
    free(matrix);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 행렬 출력 ===
  1   2   3   4
  5   6   7   8
  9  10  11  12
</pre>

</details>

---

## 7. 종합 실습

### 문제 1 - malloc 기초 (기초)

<div class="quiz-number">문제 1</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;

int main(void) {
    int *ptr = (int *)malloc(sizeof(int));

    *ptr = 777;

    printf("%d", *ptr);

    free(ptr);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="777"
   tags="동적 메모리 할당"
%}

---

### 문제 2 - calloc vs malloc (기초)

<div class="quiz-number">문제 2</div><strong>calloc과 malloc의 차이점은?</strong>

```
A. calloc은 메모리를 0으로 초기화한다.
B. malloc은 더 빠르다.
C. calloc은 매개변수가 2개다.
D. 위의 모든 설명이 맞다.
```

{% include quiz-text.html
   id="quiz2"
   answer="D"
   tags="동적 메모리 할당"
%}

---

### 문제 3 - 배열 크기 계산 (중급)

<div class="quiz-number">문제 3</div><strong>다음 코드에서 할당되는 총 바이트 수는?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdlib.h&gt;

int main(void) {
    double *arr = (double *)malloc(sizeof(double) * 10);

    // 총 몇 바이트?

    free(arr);
    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint3 %}
double은 8바이트, 10개이므로 8 × 10 = 80바이트
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   question=hint3
   code_html=code_block3
   answer="80"
   tags="동적 메모리 할당"
%}

---

### 문제 4 - realloc 이해 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;

int main(void) {
    int *arr = (int *)calloc(3, sizeof(int));

    arr[0] = 10;
    arr[1] = 20;
    arr[2] = 30;

    arr = (int *)realloc(arr, sizeof(int) * 5);

    arr[3] = 40;
    arr[4] = 50;

    printf("%d", arr[2] + arr[4]);

    free(arr);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="80"
   tags="동적 메모리 할당"
%}

---

### 문제 5 - 메모리 누수 (고급)

<div class="quiz-number">문제 5</div><strong>다음 코드에서 메모리 누수가 발생하는 줄은?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdlib.h&gt;

int main(void) {
    int *ptr1 = (int *)malloc(sizeof(int));  // 3행
    int *ptr2 = (int *)malloc(sizeof(int));  // 4행

    *ptr1 = 100;
    *ptr2 = 200;

    ptr1 = ptr2;  // 9행

    free(ptr1);  // 11행

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint5 %}
9행에서 ptr1이 가리키던 메모리 주소를 잃어버려 해제할 수 없게 됩니다.
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=hint5
   code_html=code_block5
   answer="9"
   tags="동적 메모리 할당"
%}

---

### 문제 6 - 동적 할당 종합 (고급)

<div class="quiz-number">문제 6</div><strong>다음 코드의 실행 결과는?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;
#include &lt;stdlib.h&gt;

int main(void) {
    int *arr = (int *)calloc(4, sizeof(int));
    int i, sum = 0;

    for (i = 0; i < 4; i++) {
        arr[i] = (i + 1) * 5;
    }

    arr = (int *)realloc(arr, sizeof(int) * 6);
    arr[4] = 25;
    arr[5] = 30;

    for (i = 0; i < 6; i++) {
        sum += arr[i];
    }

    printf("%d", sum);

    free(arr);

    return 0;
}</code></pre>
</div>
{% endcapture %}

{% capture hint6 %}
5 + 10 + 15 + 20 + 25 + 30 = 105
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   question=hint6
   code_html=code_block6
   answer="105"
   tags="동적 메모리 할당"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 동적 메모리 할당 함수</strong><br>
• <code>malloc(size)</code>: 지정한 크기만큼 할당 (초기화 안 됨)<br>
• <code>calloc(count, size)</code>: 할당 + 0으로 초기화<br>
• <code>realloc(ptr, new_size)</code>: 크기 재조정<br>
• <code>free(ptr)</code>: 메모리 해제<br><br>

<strong>2. 사용 패턴</strong><br>
• 할당: <code>ptr = (type *)malloc(sizeof(type) * n);</code><br>
• NULL 체크: <code>if (ptr == NULL) { ... }</code><br>
• 사용 후 해제: <code>free(ptr);</code><br>
• 해제 후 초기화: <code>ptr = NULL;</code><br><br>

<strong>3. 메모리 누수 방지</strong><br>
• 모든 malloc/calloc에 대응하는 free 호출<br>
• 포인터 덮어쓰기 전 기존 메모리 해제<br>
• 함수 반환 전 로컬 동적 메모리 해제<br><br>

<strong>4. 주의사항</strong><br>
• 같은 메모리 두 번 해제 금지<br>
• 해제된 메모리 접근 금지 (댕글링 포인터)<br>
• realloc 실패 시 임시 포인터 사용<br><br>

<strong>5. 활용 예시</strong><br>
• 크기를 모르는 데이터 처리<br>
• 런타임에 결정되는 배열<br>
• 큰 데이터 구조 (연결 리스트, 트리 등)

</div>

---
