---
layout: article
title: 8. 파일 입출력
permalink: /notes/kr/c-deep-dive/chapter-08
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C DeepDive 강의 노트, 파일 입출력 기본, 텍스트 파일과 바이너리 파일 처리, fopen/fclose/fprintf/fscanf/fwrite/fread 함수를 다룹니다.
keywords: "C언어, 파일입출력, fopen, fclose, fprintf, fscanf, fwrite, fread, 바이너리파일, 텍스트파일"
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

## 1. 파일 입출력의 이해

파일 입출력은 <span class="blue-text">프로그램 실행 후에도 데이터를 보존</span>하기 위한 방법입니다. 메모리의 데이터는 프로그램 종료 시 사라지지만, 파일에 저장하면 영구적으로 보관할 수 있습니다.

### 파일이란?

파일은 <span class="blue-text">보조 기억장치에 저장된 데이터의 집합</span>입니다.

| 구분 | 메모리 | 파일 |
|------|--------|------|
| **저장 위치** | RAM (주기억장치) | HDD/SSD (보조기억장치) |
| **데이터 보존** | 프로그램 종료 시 소멸 | 영구 보존 |
| **접근 속도** | 빠름 | 상대적으로 느림 |
| **용량** | 제한적 | 대용량 |
| **용도** | 실행 중 데이터 처리 | 데이터 저장 및 공유 |

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>파일 입출력의 필요성</strong><br>
• 프로그램 종료 후에도 데이터 유지<br>
• 대용량 데이터 처리<br>
• 프로그램 간 데이터 공유<br>
• 설정 정보 저장
</div>

### 텍스트 파일 vs 바이너리 파일

C 언어는 두 가지 방식으로 파일을 처리합니다.

| 구분 | 텍스트 파일 | 바이너리 파일 |
|------|-----------|-------------|
| **저장 형식** | 문자 형태 (ASCII/UTF-8) | 이진 형태 (바이트) |
| **가독성** | 텍스트 에디터로 확인 가능 | 전용 프로그램 필요 |
| **크기** | 상대적으로 큼 | 상대적으로 작음 |
| **예시** | .txt, .csv, .log | .exe, .bin, .dat |
| **변환** | 숫자 ↔ 문자열 변환 발생 | 메모리 그대로 저장 |

```c
// 숫자 100을 저장할 때의 차이

// 텍스트 파일: '1', '0', '0' (3바이트)
fprintf(fp, "%d", 100);

// 바이너리 파일: 0x00000064 (4바이트, int 크기)
int num = 100;
fwrite(&num, sizeof(int), 1, fp);
```

---

## 2. 파일 열기와 닫기

파일 입출력의 기본은 <span class="blue-text">파일을 열고 작업 후 닫는 것</span>입니다.

### fopen 함수

<span class="yellow-code">fopen</span> 함수는 <span class="blue-text">파일을 열고 FILE 포인터를 반환</span>합니다.

```c
#include <stdio.h>

FILE *fopen(const char *filename, const char *mode);
```

- **매개변수 1**: 파일 경로 및 이름
- **매개변수 2**: 파일 열기 모드
- **반환값**: 파일 포인터 (FILE *), 실패 시 NULL

### 파일 열기 모드

| 모드 | 설명 | 파일 없을 때 | 파일 있을 때 |
|------|------|------------|------------|
| **"r"** | 읽기 전용 | 실패 (NULL) | 처음부터 읽기 |
| **"w"** | 쓰기 전용 | 새로 생성 | <span class="red-text">기존 내용 삭제</span> |
| **"a"** | 추가 쓰기 | 새로 생성 | 끝에 추가 |
| **"r+"** | 읽기/쓰기 | 실패 (NULL) | 처음부터 읽기/쓰기 |
| **"w+"** | 읽기/쓰기 | 새로 생성 | <span class="red-text">기존 내용 삭제</span> |
| **"a+"** | 읽기/추가 | 새로 생성 | 끝에 추가 |

**바이너리 모드**: 위 모드에 `b`를 추가 (예: `"rb"`, `"wb"`, `"ab"`)

<div style="background-color: #ffe8e8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #D53C41;">
<strong>⚠️ 주의사항</strong><br>
• <code>"w"</code> 모드는 기존 파일 내용을 <span class="red-text">모두 삭제</span>합니다!<br>
• 파일 열기 실패 시 반드시 NULL 체크 필요<br>
• 파일 경로는 절대 경로 또는 상대 경로 사용
</div>

### fclose 함수

<span class="yellow-code">fclose</span> 함수는 <span class="blue-text">열린 파일을 닫고 버퍼를 비움</span>니다.

```c
#include <stdio.h>

int fclose(FILE *stream);
```

- **매개변수**: 닫을 파일 포인터
- **반환값**: 성공 시 0, 실패 시 EOF

### 기본 사용 예제

```c
#include <stdio.h>

int main(void) {
    FILE *fp;

    // 파일 열기
    fp = fopen("example.txt", "w");

    if (fp == NULL) {
        printf("파일을 열 수 없습니다.\n");
        return 1;
    }

    printf("파일이 성공적으로 열렸습니다.\n");

    // 파일 닫기
    fclose(fp);

    printf("파일이 닫혔습니다.\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
파일이 성공적으로 열렸습니다.
파일이 닫혔습니다.
</pre>

<p style="margin-top: 10px;">
실행 후 현재 디렉터리에 빈 파일 <code>example.txt</code>가 생성됩니다.
</p>

</details>

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>파일 입출력 기본 패턴</strong><br>
1. <code>fopen()</code>으로 파일 열기<br>
2. NULL 체크로 오류 확인<br>
3. 파일 읽기/쓰기 작업<br>
4. <code>fclose()</code>로 파일 닫기
</div>

---

## 3. 텍스트 파일 입출력

텍스트 파일은 <span class="blue-text">사람이 읽을 수 있는 문자 형태</span>로 데이터를 저장합니다.

### fprintf 함수

<span class="yellow-code">fprintf</span> 함수는 <span class="blue-text">형식화된 데이터를 파일에 쓰기</span>합니다.

```c
#include <stdio.h>

int fprintf(FILE *stream, const char *format, ...);
```

- **매개변수 1**: 파일 포인터
- **매개변수 2**: 형식 문자열 (printf와 동일)
- **매개변수 3~**: 출력할 데이터
- **반환값**: 출력한 문자 수, 실패 시 음수

```c
#include <stdio.h>

int main(void) {
    FILE *fp;

    fp = fopen("data.txt", "w");

    if (fp == NULL) {
        printf("파일 열기 실패\n");
        return 1;
    }

    // 파일에 데이터 쓰기
    fprintf(fp, "이름: %s\n", "홍길동");
    fprintf(fp, "나이: %d세\n", 25);
    fprintf(fp, "점수: %.2f점\n", 95.5);

    fclose(fp);

    printf("파일에 데이터를 저장했습니다.\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 및 파일 내용</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
파일에 데이터를 저장했습니다.
</pre>

<p style="margin-top: 10px;"><strong>data.txt 파일 내용:</strong></p>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px;">
이름: 홍길동
나이: 25세
점수: 95.50점
</pre>

</details>

### fscanf 함수

<span class="yellow-code">fscanf</span> 함수는 <span class="blue-text">파일에서 형식화된 데이터를 읽기</span>합니다.

```c
#include <stdio.h>

int fscanf(FILE *stream, const char *format, ...);
```

- **매개변수 1**: 파일 포인터
- **매개변수 2**: 형식 문자열 (scanf와 동일)
- **매개변수 3~**: 데이터를 저장할 변수의 주소
- **반환값**: 읽은 항목 수, 파일 끝이면 EOF

```c
#include <stdio.h>

int main(void) {
    FILE *fp;
    char name[50];
    int age;
    double score;

    fp = fopen("data.txt", "r");

    if (fp == NULL) {
        printf("파일 열기 실패\n");
        return 1;
    }

    // 파일에서 데이터 읽기
    fscanf(fp, "이름: %s\n", name);
    fscanf(fp, "나이: %d세\n", &age);
    fscanf(fp, "점수: %lf점\n", &score);

    printf("=== 파일에서 읽은 데이터 ===\n");
    printf("이름: %s\n", name);
    printf("나이: %d세\n", age);
    printf("점수: %.2f점\n", score);

    fclose(fp);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 파일에서 읽은 데이터 ===
이름: 홍길동
나이: 25세
점수: 95.50점
</pre>

</details>

### fgets와 fputs 함수

**fputs**: 문자열을 파일에 쓰기

```c
int fputs(const char *str, FILE *stream);
```

**fgets**: 파일에서 문자열 읽기

```c
char *fgets(char *str, int size, FILE *stream);
```

```c
#include <stdio.h>
#include <string.h>

int main(void) {
    FILE *fp;
    char buffer[100];

    // 파일 쓰기
    fp = fopen("memo.txt", "w");
    if (fp == NULL) {
        printf("파일 열기 실패\n");
        return 1;
    }

    fputs("첫 번째 줄\n", fp);
    fputs("두 번째 줄\n", fp);
    fputs("세 번째 줄\n", fp);

    fclose(fp);

    // 파일 읽기
    fp = fopen("memo.txt", "r");
    if (fp == NULL) {
        printf("파일 열기 실패\n");
        return 1;
    }

    printf("=== 파일 내용 ===\n");
    while (fgets(buffer, sizeof(buffer), fp) != NULL) {
        printf("%s", buffer);
    }

    fclose(fp);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
=== 파일 내용 ===
첫 번째 줄
두 번째 줄
세 번째 줄
</pre>

</details>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 텍스트 파일 함수 선택</strong><br>
• 형식화된 데이터: <code>fprintf</code>, <code>fscanf</code><br>
• 문자열 단위: <code>fputs</code>, <code>fgets</code><br>
• 문자 단위: <code>fputc</code>, <code>fgetc</code><br>
• <code>fgets</code>는 개행 문자(\n)까지 읽음
</div>

---

## 4. 바이너리 파일 입출력

바이너리 파일은 <span class="blue-text">메모리의 데이터를 그대로 저장</span>하여 효율적입니다.

### fwrite 함수

<span class="yellow-code">fwrite</span> 함수는 <span class="blue-text">메모리 블록을 파일에 쓰기</span>합니다.

```c
#include <stdio.h>

size_t fwrite(const void *ptr, size_t size, size_t count, FILE *stream);
```

- **매개변수 1**: 쓸 데이터의 주소
- **매개변수 2**: 각 항목의 크기 (바이트)
- **매개변수 3**: 항목 개수
- **매개변수 4**: 파일 포인터
- **반환값**: 쓴 항목 개수

### fread 함수

<span class="yellow-code">fread</span> 함수는 <span class="blue-text">파일에서 메모리 블록으로 읽기</span>합니다.

```c
#include <stdio.h>

size_t fread(void *ptr, size_t size, size_t count, FILE *stream);
```

- **매개변수 1**: 읽은 데이터를 저장할 주소
- **매개변수 2**: 각 항목의 크기 (바이트)
- **매개변수 3**: 항목 개수
- **매개변수 4**: 파일 포인터
- **반환값**: 읽은 항목 개수

### 기본 사용 예제

```c
#include <stdio.h>

int main(void) {
    FILE *fp;
    int numbers[5] = {10, 20, 30, 40, 50};
    int read_numbers[5];
    int i;

    // 바이너리 쓰기
    fp = fopen("numbers.dat", "wb");
    if (fp == NULL) {
        printf("파일 열기 실패\n");
        return 1;
    }

    fwrite(numbers, sizeof(int), 5, fp);
    fclose(fp);

    printf("데이터를 바이너리 파일에 저장했습니다.\n");

    // 바이너리 읽기
    fp = fopen("numbers.dat", "rb");
    if (fp == NULL) {
        printf("파일 열기 실패\n");
        return 1;
    }

    fread(read_numbers, sizeof(int), 5, fp);
    fclose(fp);

    printf("읽은 데이터: ");
    for (i = 0; i < 5; i++) {
        printf("%d ", read_numbers[i]);
    }
    printf("\n");

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
데이터를 바이너리 파일에 저장했습니다.
읽은 데이터: 10 20 30 40 50
</pre>

</details>

### 구조체 저장하기

바이너리 파일은 구조체를 통째로 저장하기에 매우 유용합니다.

```c
#include <stdio.h>
#include <string.h>

typedef struct {
    char name[30];
    int age;
    double score;
} Student;

int main(void) {
    FILE *fp;
    Student students[3] = {
        {"김철수", 20, 85.5},
        {"이영희", 22, 90.0},
        {"박민수", 21, 88.3}
    };
    Student read_students[3];
    int i;

    // 구조체 배열 저장
    fp = fopen("students.dat", "wb");
    if (fp == NULL) {
        printf("파일 열기 실패\n");
        return 1;
    }

    fwrite(students, sizeof(Student), 3, fp);
    fclose(fp);

    printf("학생 데이터를 저장했습니다.\n\n");

    // 구조체 배열 읽기
    fp = fopen("students.dat", "rb");
    if (fp == NULL) {
        printf("파일 열기 실패\n");
        return 1;
    }

    fread(read_students, sizeof(Student), 3, fp);
    fclose(fp);

    printf("=== 읽은 학생 데이터 ===\n");
    for (i = 0; i < 3; i++) {
        printf("이름: %s, 나이: %d세, 점수: %.1f점\n",
               read_students[i].name,
               read_students[i].age,
               read_students[i].score);
    }

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
학생 데이터를 저장했습니다.

=== 읽은 학생 데이터 ===
이름: 김철수, 나이: 20세, 점수: 85.5점
이름: 이영희, 나이: 22세, 점수: 90.0점
이름: 박민수, 나이: 21세, 점수: 88.3점
</pre>

</details>

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>바이너리 파일의 장점</strong><br>
• 메모리 구조 그대로 저장 (빠름)<br>
• 텍스트 변환 없이 효율적<br>
• 구조체, 배열 등 복잡한 데이터 저장에 유리<br>
• 파일 크기가 작음
</div>

---

## 5. 파일 위치 제어

파일의 특정 위치로 이동하여 읽기/쓰기를 할 수 있습니다.

### fseek 함수

<span class="yellow-code">fseek</span> 함수는 <span class="blue-text">파일 위치 지시자를 이동</span>합니다.

```c
#include <stdio.h>

int fseek(FILE *stream, long offset, int origin);
```

- **매개변수 1**: 파일 포인터
- **매개변수 2**: 이동할 바이트 수 (offset)
- **매개변수 3**: 기준 위치
  - `SEEK_SET`: 파일 시작 (0)
  - `SEEK_CUR`: 현재 위치
  - `SEEK_END`: 파일 끝
- **반환값**: 성공 시 0, 실패 시 -1

### ftell 함수

<span class="yellow-code">ftell</span> 함수는 <span class="blue-text">현재 파일 위치를 반환</span>합니다.

```c
#include <stdio.h>

long ftell(FILE *stream);
```

- **반환값**: 파일 시작부터의 바이트 수

### rewind 함수

<span class="yellow-code">rewind</span> 함수는 <span class="blue-text">파일 위치를 처음으로 이동</span>합니다.

```c
#include <stdio.h>

void rewind(FILE *stream);
```

### 사용 예제

```c
#include <stdio.h>

int main(void) {
    FILE *fp;
    int numbers[5] = {10, 20, 30, 40, 50};
    int value;

    fp = fopen("position.dat", "wb");
    fwrite(numbers, sizeof(int), 5, fp);
    fclose(fp);

    fp = fopen("position.dat", "rb");

    // 세 번째 요소로 이동 (0부터 시작하므로 인덱스 2)
    fseek(fp, sizeof(int) * 2, SEEK_SET);
    fread(&value, sizeof(int), 1, fp);
    printf("세 번째 값: %d\n", value);

    // 현재 위치 확인
    printf("현재 파일 위치: %ld 바이트\n", ftell(fp));

    // 파일 끝에서 두 번째 요소로 이동
    fseek(fp, -sizeof(int) * 2, SEEK_END);
    fread(&value, sizeof(int), 1, fp);
    printf("끝에서 두 번째 값: %d\n", value);

    // 처음으로 이동
    rewind(fp);
    fread(&value, sizeof(int), 1, fp);
    printf("첫 번째 값: %d\n", value);

    fclose(fp);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
세 번째 값: 30
현재 파일 위치: 12 바이트
끝에서 두 번째 값: 40
첫 번째 값: 10
</pre>

</details>

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #BD8739;">
<strong>💡 파일 위치 제어 활용</strong><br>
• 대용량 파일에서 특정 부분만 읽기<br>
• 파일 크기 계산: <code>fseek(fp, 0, SEEK_END); size = ftell(fp);</code><br>
• 랜덤 접근이 필요한 데이터베이스 구현<br>
• 파일 수정 시 특정 위치만 업데이트
</div>

---

## 6. 실전 예제

### 예제 1: 성적 관리 프로그램

```c
#include <stdio.h>
#include <string.h>

typedef struct {
    char name[30];
    int math;
    int english;
    int science;
} Student;

void saveStudents(Student students[], int count) {
    FILE *fp = fopen("students.dat", "wb");
    if (fp == NULL) {
        printf("파일 저장 실패\n");
        return;
    }

    fwrite(students, sizeof(Student), count, fp);
    fclose(fp);
    printf("학생 데이터를 저장했습니다.\n");
}

void loadStudents(Student students[], int *count) {
    FILE *fp = fopen("students.dat", "rb");
    if (fp == NULL) {
        printf("파일이 없습니다.\n");
        *count = 0;
        return;
    }

    *count = fread(students, sizeof(Student), 100, fp);
    fclose(fp);
    printf("%d명의 학생 데이터를 불러왔습니다.\n", *count);
}

void printStudents(Student students[], int count) {
    int i;
    printf("\n=== 학생 성적표 ===\n");
    printf("이름\t\t수학\t영어\t과학\t평균\n");
    printf("==========================================\n");

    for (i = 0; i < count; i++) {
        double avg = (students[i].math + students[i].english + students[i].science) / 3.0;
        printf("%s\t\t%d\t%d\t%d\t%.1f\n",
               students[i].name,
               students[i].math,
               students[i].english,
               students[i].science,
               avg);
    }
}

int main(void) {
    Student students[3] = {
        {"김철수", 85, 90, 88},
        {"이영희", 92, 88, 95},
        {"박민수", 78, 85, 82}
    };
    Student loaded_students[100];
    int count;

    // 데이터 저장
    saveStudents(students, 3);

    // 데이터 불러오기
    loadStudents(loaded_students, &count);

    // 출력
    printStudents(loaded_students, count);

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
학생 데이터를 저장했습니다.
3명의 학생 데이터를 불러왔습니다.

=== 학생 성적표 ===
이름		수학	영어	과학	평균
==========================================
김철수		85	90	88	87.7
이영희		92	88	95	91.7
박민수		78	85	82	81.7
</pre>

</details>

### 예제 2: 로그 파일 작성

```c
#include <stdio.h>
#include <time.h>

void writeLog(const char *message) {
    FILE *fp;
    time_t now;
    struct tm *timeinfo;

    fp = fopen("system.log", "a");  // 추가 모드
    if (fp == NULL) {
        printf("로그 파일 열기 실패\n");
        return;
    }

    // 현재 시각 가져오기
    time(&now);
    timeinfo = localtime(&now);

    // 시각과 메시지 기록
    fprintf(fp, "[%04d-%02d-%02d %02d:%02d:%02d] %s\n",
            timeinfo->tm_year + 1900,
            timeinfo->tm_mon + 1,
            timeinfo->tm_mday,
            timeinfo->tm_hour,
            timeinfo->tm_min,
            timeinfo->tm_sec,
            message);

    fclose(fp);
}

void readLog(void) {
    FILE *fp;
    char buffer[200];

    fp = fopen("system.log", "r");
    if (fp == NULL) {
        printf("로그 파일이 없습니다.\n");
        return;
    }

    printf("=== 시스템 로그 ===\n");
    while (fgets(buffer, sizeof(buffer), fp) != NULL) {
        printf("%s", buffer);
    }

    fclose(fp);
}

int main(void) {
    writeLog("시스템 시작");
    writeLog("사용자 로그인");
    writeLog("파일 업로드 완료");
    writeLog("시스템 종료");

    printf("로그를 기록했습니다.\n\n");

    readLog();

    return 0;
}
```

<details>
<summary><span class="green-text">실행 결과 보기 (예시)</span></summary>

<pre style="background-color: #f5f5f5; padding: 10px; border-radius: 5px; margin-top: 10px;">
로그를 기록했습니다.

=== 시스템 로그 ===
[2024-01-15 14:30:25] 시스템 시작
[2024-01-15 14:30:25] 사용자 로그인
[2024-01-15 14:30:25] 파일 업로드 완료
[2024-01-15 14:30:25] 시스템 종료
</pre>

</details>

---

## 7. 종합 실습

### 문제 1 - fopen 모드 (기초)

<div class="quiz-number">문제 1</div><strong>기존 파일 내용을 지우고 새로 쓰는 모드는?</strong>

```
A. "r"
B. "w"
C. "a"
D. "r+"
```

{% include quiz-text.html
   id="quiz1"
   answer="B"
   tags="파일 입출력"
%}

---

### 문제 2 - fprintf 사용 (기초)

<div class="quiz-number">문제 2</div><strong>다음 코드 실행 후 파일에 저장되는 내용은?</strong>

{% raw %}
{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main(void) {
    FILE *fp = fopen("test.txt", "w");

    fprintf(fp, "%d + %d = %d", 10, 20, 30);

    fclose(fp);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% include quiz-text.html
   id="quiz2"
   code_html=code_block2
   answer="10 + 20 = 30"
   tags="파일 입출력"
%}

---

### 문제 3 - fwrite 바이트 수 (중급)

<div class="quiz-number">문제 3</div><strong>다음 코드에서 파일에 쓰인 총 바이트 수는?</strong>

{% raw %}
{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main(void) {
    FILE *fp = fopen("data.bin", "wb");
    int arr[4] = {1, 2, 3, 4};

    fwrite(arr, sizeof(int), 4, fp);

    fclose(fp);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% capture hint3 %}
int는 4바이트, 4개이므로 4 × 4 = 16바이트
{% endcapture %}

{% include quiz-text.html
   id="quiz3"
   question=hint3
   code_html=code_block3
   answer="16"
   tags="파일 입출력"
%}

---

### 문제 4 - fscanf 사용 (중급)

<div class="quiz-number">문제 4</div><strong>다음 코드의 실행 결과는? (파일 내용: "100 200")</strong>

{% raw %}
{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main(void) {
    FILE *fp = fopen("numbers.txt", "r");
    int a, b;

    fscanf(fp, "%d %d", &a, &b);

    printf("%d", a + b);

    fclose(fp);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% include quiz-text.html
   id="quiz4"
   code_html=code_block4
   answer="300"
   tags="파일 입출력"
%}

---

### 문제 5 - fseek 활용 (고급)

<div class="quiz-number">문제 5</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block5 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

int main(void) {
    FILE *fp = fopen("test.bin", "wb");
    int arr[5] = {10, 20, 30, 40, 50};
    int value;

    fwrite(arr, sizeof(int), 5, fp);
    fclose(fp);

    fp = fopen("test.bin", "rb");
    fseek(fp, sizeof(int) * 3, SEEK_SET);
    fread(&value, sizeof(int), 1, fp);

    printf("%d", value);

    fclose(fp);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% capture hint5 %}
인덱스 3 위치(네 번째 요소)로 이동하여 읽음
{% endcapture %}

{% include quiz-text.html
   id="quiz5"
   question=hint5
   code_html=code_block5
   answer="40"
   tags="파일 입출력"
%}

---

### 문제 6 - 구조체 바이너리 저장 (고급)

<div class="quiz-number">문제 6</div><strong>다음 코드의 실행 결과는?</strong>

{% raw %}
{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
    <pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>#include &lt;stdio.h&gt;

typedef struct {
    int x;
    int y;
} Point;

int main(void) {
    FILE *fp = fopen("point.bin", "wb");
    Point p1 = {5, 10};
    Point p2;

    fwrite(&p1, sizeof(Point), 1, fp);
    fclose(fp);

    fp = fopen("point.bin", "rb");
    fread(&p2, sizeof(Point), 1, fp);
    fclose(fp);

    printf("%d", p2.x + p2.y);

    return 0;
}</code></pre>
</div>
{% endcapture %}
{% endraw %}

{% capture hint6 %}
구조체 {5, 10}을 저장 후 읽어서 5 + 10 = 15
{% endcapture %}

{% include quiz-text.html
   id="quiz6"
   question=hint6
   code_html=code_block6
   answer="15"
   tags="파일 입출력"
%}

---

## 핵심 요약

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">

<strong>1. 파일 열기/닫기</strong><br>
• <code>fopen(filename, mode)</code>: 파일 열기, FILE * 반환<br>
• <code>fclose(fp)</code>: 파일 닫기<br>
• 주요 모드: <code>"r"</code>(읽기), <code>"w"</code>(쓰기), <code>"a"</code>(추가)<br>
• 바이너리: <code>"rb"</code>, <code>"wb"</code>, <code>"ab"</code><br><br>

<strong>2. 텍스트 파일 입출력</strong><br>
• <code>fprintf(fp, format, ...)</code>: 형식화된 쓰기<br>
• <code>fscanf(fp, format, ...)</code>: 형식화된 읽기<br>
• <code>fputs(str, fp)</code>: 문자열 쓰기<br>
• <code>fgets(str, size, fp)</code>: 문자열 읽기<br><br>

<strong>3. 바이너리 파일 입출력</strong><br>
• <code>fwrite(ptr, size, count, fp)</code>: 메모리 블록 쓰기<br>
• <code>fread(ptr, size, count, fp)</code>: 메모리 블록 읽기<br>
• 구조체, 배열 저장에 효율적<br>
• 변환 없이 원본 데이터 그대로 저장<br><br>

<strong>4. 파일 위치 제어</strong><br>
• <code>fseek(fp, offset, origin)</code>: 위치 이동<br>
• <code>ftell(fp)</code>: 현재 위치 반환<br>
• <code>rewind(fp)</code>: 처음으로 이동<br>
• origin: <code>SEEK_SET</code>, <code>SEEK_CUR</code>, <code>SEEK_END</code><br><br>

<strong>5. 주의사항</strong><br>
• 파일 열기 후 반드시 NULL 체크<br>
• 사용 후 반드시 <code>fclose()</code> 호출<br>
• <code>"w"</code> 모드는 기존 내용 삭제<br>
• 바이너리 모드에서는 반드시 "b" 추가<br><br>

<strong>6. 활용 예시</strong><br>
• 데이터 영구 저장 (설정, 게임 저장)<br>
• 로그 파일 작성<br>
• 대용량 데이터 처리<br>
• 프로그램 간 데이터 공유

</div>

---
