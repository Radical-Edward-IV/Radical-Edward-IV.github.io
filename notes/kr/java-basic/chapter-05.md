---
layout: article
title: 5. 배열
permalink: /notes/kr/java-basic/chapter-05
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: Java 기초 과정 강의 노트, 배열의 선언과 초기화, 1차원/다차원 배열, 향상된 for문, Arrays 클래스를 다룹니다.
keywords: "Java, 배열, Array, 1차원 배열, 2차원 배열, 다차원 배열, for-each, Arrays, 인덱스"
---

<script src="/assets/js/quiz.js"></script>

<style>
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
    .quiz-container {
        margin: 20px 0;
        padding: 15px;
        border: 1px solid #e5e7eb;
        border-radius: 12px;
        background-color: #ffffff;
        box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);
    }
    .quiz-container:hover {
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
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=Java%20Basic&reversal=false&textBg=false)

---

## 배열이란?

<span class="blue-text">배열(Array)</span>은 **같은 타입의 데이터를 연속된 메모리 공간에 저장**하는 자료구조입니다. 여러 개의 값을 하나의 변수로 관리할 수 있습니다.

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">배열이 필요한 이유</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
학생 100명의 성적을 저장한다면? 변수 100개를 만드는 것보다 배열 하나로 관리하는 것이 훨씬 효율적입니다.
</p>
</div>

### 배열의 특징

| 특징 | 설명 |
|------|------|
| 같은 타입 | 배열의 모든 요소는 동일한 자료형 |
| 고정 크기 | 생성 시 크기가 결정되며, 변경 불가 |
| 인덱스 접근 | 0부터 시작하는 인덱스로 요소에 접근 |
| 연속 메모리 | 메모리에 연속적으로 저장 |

```
배열 scores (크기 5)
┌───────┬───────┬───────┬───────┬───────┐
│  85   │  90   │  78   │  92   │  88   │
├───────┼───────┼───────┼───────┼───────┤
│ [0]   │ [1]   │ [2]   │ [3]   │ [4]   │
└───────┴───────┴───────┴───────┴───────┘
  인덱스 0부터 시작, 마지막 인덱스는 (크기-1)
```

---

## 1차원 배열

### 배열 선언

```java
// 방법 1: 타입[] 배열명;
int[] scores;
String[] names;

// 방법 2: 타입 배열명[];  (C 스타일, 권장하지 않음)
int numbers[];
```

### 배열 생성

```java
// 선언과 생성을 따로
int[] scores;
scores = new int[5];  // 크기가 5인 int 배열 생성

// 선언과 생성을 동시에
int[] numbers = new int[10];  // 크기가 10인 int 배열
String[] names = new String[3];  // 크기가 3인 String 배열
```

### 배열 초기화

```java
// 방법 1: 선언, 생성, 초기화를 한 번에
int[] scores = {85, 90, 78, 92, 88};

// 방법 2: new 키워드와 함께 초기화
int[] scores = new int[]{85, 90, 78, 92, 88};

// 방법 3: 생성 후 개별 초기화
int[] scores = new int[5];
scores[0] = 85;
scores[1] = 90;
scores[2] = 78;
scores[3] = 92;
scores[4] = 88;
```

### 배열의 기본값

배열 생성 시 요소들은 자료형에 따라 기본값으로 초기화됩니다.

| 자료형 | 기본값 |
|--------|--------|
| `int`, `short`, `byte`, `long` | 0 |
| `float`, `double` | 0.0 |
| `char` | '\u0000' (널 문자) |
| `boolean` | false |
| 참조 타입 (String 등) | null |

```java
int[] numbers = new int[3];
System.out.println(numbers[0]);  // 0

String[] names = new String[3];
System.out.println(names[0]);    // null
```

### 배열 요소 접근

```java
int[] scores = {85, 90, 78, 92, 88};

// 읽기
System.out.println(scores[0]);  // 85
System.out.println(scores[2]);  // 78

// 쓰기
scores[1] = 95;  // 90 → 95로 변경
System.out.println(scores[1]);  // 95
```

### 배열 길이

<span class="yellow-code">length</span> 속성으로 배열의 크기를 확인합니다.

```java
int[] numbers = {10, 20, 30, 40, 50};
System.out.println(numbers.length);  // 5

// 마지막 요소 접근
System.out.println(numbers[numbers.length - 1]);  // 50
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">ArrayIndexOutOfBoundsException</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
배열의 범위를 벗어난 인덱스에 접근하면 <span class="red-text">ArrayIndexOutOfBoundsException</span> 오류가 발생합니다.<br>
유효한 인덱스 범위: <code>0</code> ~ <code>length - 1</code>
</p>
</div>

```java
int[] arr = {1, 2, 3};
System.out.println(arr[3]);  // 오류! 유효 인덱스는 0, 1, 2
```

---

## 배열과 반복문

배열은 반복문과 함께 사용할 때 가장 강력합니다.

### for 문으로 배열 순회

```java
int[] scores = {85, 90, 78, 92, 88};

// 모든 요소 출력
for (int i = 0; i < scores.length; i++) {
    System.out.println("scores[" + i + "] = " + scores[i]);
}
```

**출력:**

```
scores[0] = 85
scores[1] = 90
scores[2] = 78
scores[3] = 92
scores[4] = 88
```

### 배열 합계와 평균

```java
int[] scores = {85, 90, 78, 92, 88};
int sum = 0;

for (int i = 0; i < scores.length; i++) {
    sum += scores[i];
}

double average = (double) sum / scores.length;

System.out.println("합계: " + sum);        // 합계: 433
System.out.println("평균: " + average);    // 평균: 86.6
```

### 최댓값과 최솟값

```java
int[] numbers = {45, 78, 23, 91, 56};

int max = numbers[0];
int min = numbers[0];

for (int i = 1; i < numbers.length; i++) {
    if (numbers[i] > max) {
        max = numbers[i];
    }
    if (numbers[i] < min) {
        min = numbers[i];
    }
}

System.out.println("최댓값: " + max);  // 91
System.out.println("최솟값: " + min);  // 23
```

### while 문으로 배열 순회

```java
String[] fruits = {"사과", "바나나", "오렌지"};
int i = 0;

while (i < fruits.length) {
    System.out.println(fruits[i]);
    i++;
}
```

---

## 향상된 for 문 (for-each)

<span class="blue-text">향상된 for 문</span>은 배열의 모든 요소를 순차적으로 접근할 때 사용합니다. 인덱스 없이 요소에 직접 접근합니다.

### 기본 문법

```java
for (자료형 변수명 : 배열명) {
    // 변수명을 통해 요소에 접근
}
```

### 기본 예제

```java
int[] scores = {85, 90, 78, 92, 88};

// 기존 for 문
for (int i = 0; i < scores.length; i++) {
    System.out.println(scores[i]);
}

// 향상된 for 문 (for-each)
for (int score : scores) {
    System.out.println(score);
}
```

### 합계 계산 (for-each)

```java
int[] numbers = {10, 20, 30, 40, 50};
int sum = 0;

for (int num : numbers) {
    sum += num;
}

System.out.println("합계: " + sum);  // 합계: 150
```

### for 문 vs for-each 비교

| 구분 | for 문 | for-each 문 |
|------|--------|-------------|
| 인덱스 사용 | O | X |
| 요소 수정 | O | X (원본 수정 불가) |
| 가독성 | 보통 | 좋음 |
| 역순 순회 | O | X |
| 사용 시점 | 인덱스 필요, 요소 수정 | 단순 읽기 |

```java
int[] arr = {1, 2, 3, 4, 5};

// for-each로 요소 수정 시도 (원본 변경 안 됨)
for (int num : arr) {
    num = num * 2;  // 지역 변수만 변경됨
}
System.out.println(arr[0]);  // 1 (변경 안 됨)

// for 문으로 요소 수정 (원본 변경됨)
for (int i = 0; i < arr.length; i++) {
    arr[i] = arr[i] * 2;
}
System.out.println(arr[0]);  // 2 (변경됨)
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">for-each 사용 권장</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
단순히 배열의 모든 요소를 읽기만 한다면 <span class="green-text">for-each 문</span>을 사용하세요. 코드가 간결해지고 실수를 줄일 수 있습니다.
</p>
</div>

---

## 다차원 배열

### 2차원 배열

2차원 배열은 <span class="blue-text">배열의 배열</span>입니다. 행(row)과 열(column)로 구성된 표 형태의 데이터를 저장합니다.

```
2차원 배열 (3행 4열)
         열0   열1   열2   열3
      ┌─────┬─────┬─────┬─────┐
행0   │  1  │  2  │  3  │  4  │
      ├─────┼─────┼─────┼─────┤
행1   │  5  │  6  │  7  │  8  │
      ├─────┼─────┼─────┼─────┤
행2   │  9  │ 10  │ 11  │ 12  │
      └─────┴─────┴─────┴─────┘
```

### 2차원 배열 선언과 생성

```java
// 선언
int[][] matrix;

// 생성 (3행 4열)
matrix = new int[3][4];

// 선언과 생성 동시에
int[][] table = new int[2][3];
```

### 2차원 배열 초기화

```java
// 방법 1: 선언과 동시에 초기화
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// 방법 2: 개별 요소 초기화
int[][] table = new int[2][3];
table[0][0] = 1;
table[0][1] = 2;
table[0][2] = 3;
table[1][0] = 4;
table[1][1] = 5;
table[1][2] = 6;
```

### 2차원 배열 요소 접근

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// 읽기
System.out.println(matrix[0][0]);  // 1 (0행 0열)
System.out.println(matrix[1][2]);  // 6 (1행 2열)
System.out.println(matrix[2][1]);  // 8 (2행 1열)

// 쓰기
matrix[1][1] = 100;  // 5 → 100으로 변경
```

### 2차원 배열 길이

```java
int[][] matrix = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12}
};

System.out.println(matrix.length);       // 3 (행의 개수)
System.out.println(matrix[0].length);    // 4 (0번 행의 열 개수)
System.out.println(matrix[1].length);    // 4 (1번 행의 열 개수)
```

### 2차원 배열 순회

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// 중첩 for 문
for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix[i].length; j++) {
        System.out.print(matrix[i][j] + " ");
    }
    System.out.println();
}
```

**출력:**

```
1 2 3
4 5 6
7 8 9
```

### 2차원 배열과 for-each

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};

for (int[] row : matrix) {        // 각 행
    for (int value : row) {       // 각 요소
        System.out.print(value + " ");
    }
    System.out.println();
}
```

### 가변 배열 (Jagged Array)

Java의 2차원 배열은 각 행의 열 개수가 다를 수 있습니다.

```java
// 가변 배열 생성
int[][] jagged = new int[3][];
jagged[0] = new int[2];  // 0행: 2열
jagged[1] = new int[4];  // 1행: 4열
jagged[2] = new int[3];  // 2행: 3열

// 가변 배열 초기화
int[][] jagged2 = {
    {1, 2},
    {3, 4, 5, 6},
    {7, 8, 9}
};

// 순회
for (int i = 0; i < jagged2.length; i++) {
    for (int j = 0; j < jagged2[i].length; j++) {
        System.out.print(jagged2[i][j] + " ");
    }
    System.out.println();
}
```

**출력:**

```
1 2
3 4 5 6
7 8 9
```

---

## Arrays 클래스

<span class="blue-text">java.util.Arrays</span> 클래스는 배열을 다루는 유용한 메서드를 제공합니다.

```java
import java.util.Arrays;
```

### toString() - 배열 출력

```java
int[] arr = {3, 1, 4, 1, 5};
System.out.println(arr);              // [I@hashcode (주소값)
System.out.println(Arrays.toString(arr));  // [3, 1, 4, 1, 5]
```

### sort() - 정렬

```java
int[] numbers = {5, 2, 8, 1, 9};
Arrays.sort(numbers);
System.out.println(Arrays.toString(numbers));  // [1, 2, 5, 8, 9]

// 부분 정렬 (인덱스 1부터 4 이전까지)
int[] arr = {5, 3, 1, 4, 2};
Arrays.sort(arr, 1, 4);  // 인덱스 1, 2, 3만 정렬
System.out.println(Arrays.toString(arr));  // [5, 1, 3, 4, 2]
```

### fill() - 값 채우기

```java
int[] arr = new int[5];
Arrays.fill(arr, 7);
System.out.println(Arrays.toString(arr));  // [7, 7, 7, 7, 7]

// 부분 채우기
int[] arr2 = new int[5];
Arrays.fill(arr2, 1, 4, 9);  // 인덱스 1~3만 9로 채움
System.out.println(Arrays.toString(arr2));  // [0, 9, 9, 9, 0]
```

### copyOf() - 배열 복사

```java
int[] original = {1, 2, 3, 4, 5};

// 같은 크기로 복사
int[] copy1 = Arrays.copyOf(original, original.length);
System.out.println(Arrays.toString(copy1));  // [1, 2, 3, 4, 5]

// 더 큰 크기로 복사 (나머지는 기본값)
int[] copy2 = Arrays.copyOf(original, 7);
System.out.println(Arrays.toString(copy2));  // [1, 2, 3, 4, 5, 0, 0]

// 더 작은 크기로 복사
int[] copy3 = Arrays.copyOf(original, 3);
System.out.println(Arrays.toString(copy3));  // [1, 2, 3]
```

### copyOfRange() - 범위 복사

```java
int[] arr = {1, 2, 3, 4, 5};
int[] part = Arrays.copyOfRange(arr, 1, 4);  // 인덱스 1~3 복사
System.out.println(Arrays.toString(part));    // [2, 3, 4]
```

### equals() - 배열 비교

```java
int[] arr1 = {1, 2, 3};
int[] arr2 = {1, 2, 3};
int[] arr3 = {1, 2, 4};

System.out.println(arr1 == arr2);              // false (주소 비교)
System.out.println(Arrays.equals(arr1, arr2)); // true (값 비교)
System.out.println(Arrays.equals(arr1, arr3)); // false
```

### binarySearch() - 이진 검색

```java
int[] arr = {1, 3, 5, 7, 9};  // 정렬된 상태여야 함

int index = Arrays.binarySearch(arr, 5);
System.out.println(index);  // 2 (찾은 위치)

int notFound = Arrays.binarySearch(arr, 4);
System.out.println(notFound);  // -3 (없으면 음수)
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">binarySearch 주의</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
<code>binarySearch()</code>는 <span class="red-text">반드시 정렬된 배열</span>에서만 사용해야 합니다. 정렬되지 않은 배열에서 사용하면 잘못된 결과가 나올 수 있습니다.
</p>
</div>

### Arrays 메서드 요약

| 메서드 | 설명 |
|--------|------|
| `toString(arr)` | 배열을 문자열로 변환 |
| `sort(arr)` | 오름차순 정렬 |
| `fill(arr, value)` | 모든 요소를 지정 값으로 채움 |
| `copyOf(arr, length)` | 배열 복사 (새 크기 지정 가능) |
| `copyOfRange(arr, from, to)` | 범위 지정 복사 |
| `equals(arr1, arr2)` | 두 배열 내용 비교 |
| `binarySearch(arr, key)` | 이진 검색 (정렬 필수) |

---

## 배열 활용 예제

### 배열 역순 출력

```java
int[] numbers = {1, 2, 3, 4, 5};

System.out.print("원본: ");
for (int num : numbers) {
    System.out.print(num + " ");
}

System.out.print("\n역순: ");
for (int i = numbers.length - 1; i >= 0; i--) {
    System.out.print(numbers[i] + " ");
}
```

**출력:**

```
원본: 1 2 3 4 5
역순: 5 4 3 2 1
```

### 배열 요소 검색

```java
int[] numbers = {45, 78, 23, 91, 56};
int target = 23;
int foundIndex = -1;

for (int i = 0; i < numbers.length; i++) {
    if (numbers[i] == target) {
        foundIndex = i;
        break;
    }
}

if (foundIndex != -1) {
    System.out.println(target + "을 인덱스 " + foundIndex + "에서 찾았습니다.");
} else {
    System.out.println(target + "을 찾지 못했습니다.");
}
// 출력: 23을 인덱스 2에서 찾았습니다.
```

### 배열 요소 개수 세기

```java
int[] scores = {85, 90, 78, 92, 88, 95, 72, 90};
int target = 90;
int count = 0;

for (int score : scores) {
    if (score == target) {
        count++;
    }
}

System.out.println(target + "점을 받은 학생: " + count + "명");
// 출력: 90점을 받은 학생: 2명
```

### 2차원 배열 합계

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

int total = 0;
for (int[] row : matrix) {
    for (int value : row) {
        total += value;
    }
}

System.out.println("전체 합계: " + total);  // 전체 합계: 45
```

---

## 종합 실습

### 문제 1 - 배열 기초 (기초)

<div class="quiz-number">문제 1</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int[] arr = {10, 20, 30, 40, 50};
        System.out.println(arr[2]);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1"
   code_html=code_block1
   answer="30"
   tags="배열"
%}

---

### 문제 2 - 배열 길이 (기초)

<div class="quiz-number">문제 2</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        String[] fruits = {"사과", "바나나", "오렌지", "포도"};
        System.out.println(fruits.length);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="4"
   tags="배열"
%}

---

### 문제 3 - 배열 합계 (기초)

<div class="quiz-number">문제 3</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4, 5};
        int sum = 0;
        for (int n : nums) {
            sum += n;
        }
        System.out.println(sum);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   code_html=code_block3
   answer="15"
   tags="배열"
%}

---

### 문제 4 - 2차원 배열 (중급)

<div class="quiz-number">문제 4</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int[][] arr = {
            {1, 2, 3},
            {4, 5, 6}
        };
        System.out.println(arr[1][2]);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="6"
   tags="배열"
%}

---

### 문제 5 - 배열 기본값 (중급)

<div class="quiz-number">문제 5</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int[] arr = new int[3];
        arr[1] = 5;
        int sum = arr[0] + arr[1] + arr[2];
        System.out.println(sum);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   code_html=code_block5
   answer="5"
   tags="배열"
%}

---

### 문제 6 - 2차원 배열 길이 (중급)

<div class="quiz-number">문제 6</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int[][] matrix = new int[3][4];
        System.out.println(matrix.length + matrix[0].length);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   code_html=code_block6
   answer="7"
   tags="배열"
%}

---

### 문제 7 - Arrays 클래스 (고급)

<div class="quiz-number">문제 7</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>import java.util.Arrays;

public class Test {
    public static void main(String[] args) {
        int[] arr = {5, 2, 8, 1, 9};
        Arrays.sort(arr);
        System.out.println(arr[2]);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7"
   code_html=code_block7
   answer="5"
   tags="배열"
%}

---

### 문제 8 - 가변 배열 (고급)

<div class="quiz-number">문제 8</div><strong>다음 Java 프로그램의 실행 결과는 무엇입니까?</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>public class Test {
    public static void main(String[] args) {
        int[][] arr = {
            {1, 2},
            {3, 4, 5, 6},
            {7, 8, 9}
        };
        int sum = 0;
        for (int[] row : arr) {
            sum += row.length;
        }
        System.out.println(sum);
    }
}</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8"
   code_html=code_block8
   answer="9"
   tags="배열"
%}

---

## 실전 프로그래밍

### 과제 1: 성적 처리 프로그램

학생 5명의 성적을 배열에 저장하고 합계, 평균, 최고점, 최저점을 구하는 프로그램을 작성하세요.

**요구사항:**
- 5명의 성적을 배열에 저장 (예: 85, 92, 78, 96, 88)
- 합계, 평균, 최고점, 최저점 계산
- 결과 출력

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">public class GradeProcessor {
    public static void main(String[] args) {
        int[] scores = {85, 92, 78, 96, 88};

        int sum = 0;
        int max = scores[0];
        int min = scores[0];

        for (int score : scores) {
            sum += score;
            if (score > max) max = score;
            if (score < min) min = score;
        }

        double average = (double) sum / scores.length;

        System.out.println("===== 성적 처리 결과 =====");
        System.out.println("합계: " + sum);
        System.out.printf("평균: %.2f\n", average);
        System.out.println("최고점: " + max);
        System.out.println("최저점: " + min);
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>===== 성적 처리 결과 =====
합계: 439
평균: 87.80
최고점: 96
최저점: 78
</code></pre>

</details>

---

### 과제 2: 배열 정렬 (버블 정렬)

Arrays.sort()를 사용하지 않고 버블 정렬 알고리즘으로 배열을 오름차순 정렬하는 프로그램을 작성하세요.

**요구사항:**
- 정렬할 배열 선언 (예: {64, 34, 25, 12, 22, 11, 90})
- 버블 정렬: 인접한 두 요소를 비교하여 교환
- 정렬 전후 배열 출력

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">import java.util.Arrays;

public class BubbleSort {
    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};

        System.out.println("정렬 전: " + Arrays.toString(arr));

        // 버블 정렬
        for (int i = 0; i < arr.length - 1; i++) {
            for (int j = 0; j < arr.length - 1 - i; j++) {
                if (arr[j] > arr[j + 1]) {
                    // 교환
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }

        System.out.println("정렬 후: " + Arrays.toString(arr));
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>정렬 전: [64, 34, 25, 12, 22, 11, 90]
정렬 후: [11, 12, 22, 25, 34, 64, 90]
</code></pre>

</details>

---

### 과제 3: 행렬 덧셈

두 개의 2차원 배열(행렬)을 더하는 프로그램을 작성하세요.

**요구사항:**
- 같은 크기의 2×3 행렬 두 개 선언
- 두 행렬의 같은 위치 요소끼리 더하기
- 결과 행렬 출력

<details>
<summary><span class="green-text">예시 답안 보기</span></summary>

<pre><code class="language-java">public class MatrixAddition {
    public static void main(String[] args) {
        int[][] matrix1 = {
            {1, 2, 3},
            {4, 5, 6}
        };

        int[][] matrix2 = {
            {7, 8, 9},
            {10, 11, 12}
        };

        int[][] result = new int[2][3];

        // 행렬 덧셈
        for (int i = 0; i < matrix1.length; i++) {
            for (int j = 0; j < matrix1[i].length; j++) {
                result[i][j] = matrix1[i][j] + matrix2[i][j];
            }
        }

        // 결과 출력
        System.out.println("===== 행렬 덧셈 결과 =====");
        for (int[] row : result) {
            for (int value : row) {
                System.out.print(value + "\t");
            }
            System.out.println();
        }
    }
}
</code></pre>

<p><strong>출력:</strong></p>
<pre><code>===== 행렬 덧셈 결과 =====
8	10	12
14	16	18
</code></pre>

</details>

---

## 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 16px;">
<span style="font-size: 1.25rem;">✅</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">이번 챕터에서 배운 내용</h3>
</div>

<ol style="margin: 0; padding-left: 20px; color: #4b5563;">
<li style="margin-bottom: 12px;"><strong>배열 선언과 생성</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">int[] arr = new int[5];          // 생성
int[] arr = {1, 2, 3, 4, 5};     // 초기화
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>배열 접근</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">arr[0] = 10;              // 쓰기
int value = arr[0];       // 읽기
int size = arr.length;    // 길이
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>향상된 for 문</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">for (int num : arr) {
    // 요소 읽기 전용
}
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>2차원 배열</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">int[][] matrix = new int[3][4];  // 3행 4열
matrix[0][0] = 1;                // 요소 접근
matrix.length;                   // 행 개수
matrix[0].length;                // 열 개수
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>Arrays 클래스 주요 메서드</strong>
   <table style="margin-top: 8px; margin-bottom: 0; width: 100%; border-collapse: collapse;">
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <th style="padding: 8px; text-align: left;">메서드</th>
   <th style="padding: 8px; text-align: left;">기능</th>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;"><code>toString()</code></td>
   <td style="padding: 8px;">배열 → 문자열</td>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;"><code>sort()</code></td>
   <td style="padding: 8px;">정렬</td>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;"><code>fill()</code></td>
   <td style="padding: 8px;">값 채우기</td>
   </tr>
   <tr style="border-bottom: 1px solid #e5e7eb;">
   <td style="padding: 8px;"><code>copyOf()</code></td>
   <td style="padding: 8px;">배열 복사</td>
   </tr>
   <tr>
   <td style="padding: 8px;"><code>equals()</code></td>
   <td style="padding: 8px;">배열 비교</td>
   </tr>
   </table>
</li>
<li style="margin-bottom: 0;"><strong>주요 포인트</strong>
   <ul style="margin-top: 8px; margin-bottom: 0;">
   <li>인덱스는 <span class="blue-text">0부터 시작</span>, 마지막은 <code>length - 1</code></li>
   <li>범위 초과 시 <span class="red-text">ArrayIndexOutOfBoundsException</span></li>
   <li>배열 크기는 생성 후 <span class="red-text">변경 불가</span></li>
   <li>for-each는 읽기 전용, 요소 수정 불가</li>
   <li>2차원 배열은 행별로 다른 열 개수 가능 (가변 배열)</li>
   </ul>
</li>
</ol>

</div>

---

## 다음 챕터 예고

다음 챕터에서는 **메서드 (Method)**를 배웁니다.

- 메서드란?
- 메서드 선언과 호출
- 매개변수와 반환값
- 메서드 오버로딩
- 재귀 메서드
- 가변 인자 (Varargs)

---

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04); text-align: center;">
<div style="display: flex; align-items: center; justify-content: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">🎯</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">배열 학습 완료!</h3>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
여러 데이터를 효율적으로 관리하는 배열을 배웠습니다.<br>
이제 메서드를 배우면 코드를 재사용 가능한 단위로 구성할 수 있습니다!
</p>
</div>
