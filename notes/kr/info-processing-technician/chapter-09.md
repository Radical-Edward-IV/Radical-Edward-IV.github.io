---
layout: article
title: 8. DML - SELECT와 JOIN
permalink: /notes/kr/info-processing-technician/chapter-09
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - SELECT문의 기본 구조와 조건 검색, 정렬, 그룹 함수, 하위 질의, JOIN(INNER/OUTER)을 학습합니다.
keywords: "프로그래밍기능사, SQL, SELECT, JOIN, INNER JOIN, OUTER JOIN, GROUP BY, HAVING, ORDER BY, 하위 질의"
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

# PART 1. SELECT문의 기본

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
SELECT문은 SQL에서 가장 빈번하게 출제되는 영역입니다. WHERE, GROUP BY, HAVING, ORDER BY 절의 역할과 실행 순서를 반드시 암기하세요.
</p>
</div>

## 1.1 SELECT문의 개요

<span class="blue-text">SELECT문</span>은 테이블의 튜플(행) 중에서 전체 또는 조건을 만족하는 튜플을 검색하여 주기억장치 상에 임시 테이블로 구성하는 명령문이다.

```sql
SELECT [PREDICATE] [테이블명.]속성명1, [테이블명.]속성명2, ...
FROM 테이블명1, 테이블명2, ...
[WHERE 조건]
[GROUP BY 속성명1, 속성명2, ...]
[HAVING 조건]
[ORDER BY 속성명 [ASC | DESC]];
```

**각 절의 역할**

| 절 | 설명 |
|------|------|
| **SELECT** | 검색할 속성(열) 또는 수식을 지정한다. 모든 속성을 검색할 때는 `*`를 사용한다. |
| **FROM** | 검색할 데이터를 포함하는 테이블명을 지정한다. |
| **WHERE** | 검색 조건을 기술한다. |
| **GROUP BY** | 특정 속성을 기준으로 그룹화하여 검색할 때 사용한다. 그룹 함수와 함께 쓰인다. |
| **HAVING** | GROUP BY로 그룹화한 결과에 대한 조건을 지정한다. |
| **ORDER BY** | 특정 속성 기준으로 정렬한다. ASC(오름차순, 기본값), DESC(내림차순) |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">PREDICATE 옵션</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <strong>ALL</strong> : 모든 튜플을 검색 (주로 생략)<br>
• <strong>DISTINCT</strong> : 중복된 튜플이 있으면 그 중 첫 번째 것만 검색<br>
• <strong>DISTINCTROW</strong> : 선택된 속성이 아닌 튜플 전체를 대상으로 중복 제거
</p>
</div>

**SELECT문의 실행 순서**

```
FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY
```

---

## 1.2 조건 연산자와 주요 함수

### 비교 연산자

| 연산자 | 의미 |
|--------|------|
| `=` | 같다 |
| `<>` | 같지 않다 |
| `>` | 크다 |
| `<` | 작다 |
| `>=` | 크거나 같다 |
| `<=` | 작거나 같다 |

### 논리 연산자

| 연산자 | 의미 |
|--------|------|
| `NOT` | 조건을 만족하지 않는 데이터 추출 |
| `AND` | 두 조건을 모두 만족하는 데이터 추출 |
| `OR` | 두 조건 중 하나라도 만족하는 데이터 추출 |

### LIKE 연산자와 대표 문자

| 대표 문자 | 의미 |
|-----------|------|
| `%` | 모든 문자를 대표 |
| `_` | 문자 하나를 대표 |
| `#` | 숫자 하나를 대표 |

### 연산자 우선순위

```
(1) 산술 연산자 : *, /, +, -
(2) 관계 연산자 : =, <>, >, <, >=, <=
(3) 논리 연산자 : NOT → AND → OR
```

### 주요 함수

| 함수 | 기능 |
|------|------|
| `AVG(필드명)` | 평균 |
| `SUM(필드명)` | 합계 |
| `COUNT(필드명)` | 개수 |
| `MIN(필드명)` | 최솟값 |
| `MAX(필드명)` | 최댓값 |
| `UPPER(문자열)` | 대문자 변환 |
| `LOWER(문자열)` | 소문자 변환 |
| `LEN(문자열)` | 문자열 길이 |
| `TRIM(문자열)` | 양쪽 공백 제거 |

---

## 1.3 기본 검색

다음 예제들은 아래의 <span class="blue-text">&lt;직원&gt;</span> 테이블을 기준으로 합니다.

**&lt;직원&gt; 테이블**

| 성명 | 팀 | 입사일 | 지역 | 급여 |
|------|------|--------|------|------|
| 김태현 | 개발 | 03/15/95 | 강남구 | 130 |
| 박수진 | 마케팅 | 09/22/98 | 마포구 | 85 |
| 이준혁 | 디자인 | 05/10/92 | 서초구 | 110 |
| 정미래 | 디자인 | 11/03/96 | 강남구 | 95 |
| 오세영 | 개발 | 06/18/90 | 송파구 | 105 |
| 한지우 | 디자인 | 08/25/94 | 용산구 | 130 |
| 최동현 | 개발 | 02/14/99 | 성동구 | 115 |
| 송예린 | 마케팅 | 07/30/01 | NULL | 95 |

**예제 1)** &lt;직원&gt; 테이블의 모든 튜플 검색

```sql
SELECT * FROM 직원;
```

**예제 2)** 지역 중복 제거 후 검색

```sql
SELECT DISTINCT 지역 FROM 직원;
```

**예제 3)** 급여에 10을 더한 결과 검색

```sql
SELECT 팀 + '팀' AS 소속,
       성명 + '의 급여' AS 급여정보,
       급여 + 10 AS 실급여
FROM 직원;
```

---

## 1.4 조건 지정 검색

**예제 1)** 팀이 '개발'인 직원 검색

```sql
SELECT * FROM 직원
WHERE 팀 = '개발';
```

**예제 2)** 팀이 '개발'이고 급여가 110 초과인 직원 검색

```sql
SELECT * FROM 직원
WHERE 팀 = '개발' AND 급여 > 110;
```

**예제 3)** 팀이 '개발'이거나 '마케팅'인 직원 검색

```sql
SELECT * FROM 직원
WHERE 팀 = '개발' OR 팀 = '마케팅';
```

**예제 4)** 성명이 '김'으로 시작하는 직원 검색

```sql
SELECT * FROM 직원
WHERE 성명 LIKE '김%';
```

**예제 5)** 입사일이 1994~1998 사이인 직원 검색

```sql
SELECT * FROM 직원
WHERE 입사일 BETWEEN #01/01/94# AND #12/31/98#;
```

**예제 6)** 지역이 NULL인 직원 검색

```sql
SELECT * FROM 직원
WHERE 지역 IS NULL;
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">IS NULL vs IS NOT NULL</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• NULL 값을 비교할 때는 <code>=</code> 연산자를 사용할 수 없으며, 반드시 <code>IS NULL</code> 또는 <code>IS NOT NULL</code>을 사용해야 합니다.
</p>
</div>

---

## 1.5 정렬 검색

**예제 1)** 지역을 내림차순으로 정렬하여 상위 2건 검색

```sql
SELECT TOP 2 *
FROM 직원
ORDER BY 지역 DESC;
```

**예제 2)** 팀 오름차순, 같은 팀은 성명 내림차순 정렬

```sql
SELECT *
FROM 직원
ORDER BY 팀 ASC, 성명 DESC;
```

---

## 1.6 그룹 지정 검색

**예제 1)** 팀별 평균 급여

```sql
SELECT 팀, AVG(급여) AS 평균
FROM 직원
GROUP BY 팀;
```

**예제 2)** 팀별 직원 수

```sql
SELECT 팀, COUNT(*) AS 직원수
FROM 직원
GROUP BY 팀;
```

**예제 3)** 급여가 100 이상인 직원이 2명 이상인 팀 검색

```sql
SELECT 팀, COUNT(*) AS 직원수
FROM 직원
WHERE 급여 >= 100
GROUP BY 팀
HAVING COUNT(*) >= 2;
```

**해설:**
- 급여 >= 100인 직원: 김태현(130), 이준혁(110), 오세영(105), 한지우(130), 최동현(115)
- 개발팀: 3명, 디자인팀: 2명 → 둘 다 HAVING 조건 충족

---

## 1.7 하위 질의

하위 질의(서브쿼리)는 SELECT문 안에 또 다른 SELECT문을 포함하는 방식이다.

**&lt;동호회&gt; 테이블**

| 성명 | 활동 | 년수 |
|------|------|------|
| 김태현 | 축구 | 12 |
| 이준혁 | 독서 | 8 |
| 정미래 | 등산 | 5 |
| 한지우 | 요리 | 15 |
| 최동현 | 축구 | 3 |

**예제 1)** 활동이 '요리'인 직원의 성명과 지역 검색

```sql
SELECT 성명, 지역
FROM 직원
WHERE 성명 = (
  SELECT 성명
  FROM 동호회
  WHERE 활동 = '요리'
);
```

**결과:** 한지우, 용산구

**예제 2)** 동호회 활동을 하지 않는 직원 검색

```sql
SELECT *
FROM 직원
WHERE 성명 NOT IN (
  SELECT 성명 FROM 동호회
);
```

**결과:** 박수진, 오세영, 송예린 (동호회 테이블에 없는 직원)

---

## 1.8 복수 테이블 검색

**예제)** 활동 년수가 10 이상인 직원의 성명, 팀, 활동, 년수 검색

```sql
SELECT 직원.성명, 직원.팀,
       동호회.활동, 동호회.년수
FROM 직원, 동호회
WHERE 동호회.년수 >= 10
  AND 직원.성명 = 동호회.성명;
```

**결과:**

| 성명 | 팀 | 활동 | 년수 |
|------|------|------|------|
| 김태현 | 개발 | 축구 | 12 |
| 한지우 | 디자인 | 요리 | 15 |

---

## 1.9 집합 연산자를 이용한 통합 질의

```sql
SELECT 속성명1, 속성명2, ...
FROM 테이블명
UNION | UNION ALL | INTERSECT | EXCEPT
SELECT 속성명1, 속성명2, ...
FROM 테이블명
[ORDER BY 속성명 [ASC | DESC]];
```

| 집합 연산자 | 설명 |
|-------------|------|
| **UNION** | 두 SELECT 결과를 통합 (중복 행 <span class="red-text">제거</span>) |
| **UNION ALL** | 두 SELECT 결과를 통합 (중복 행 <span class="green-text">포함</span>) |
| **INTERSECT** | 두 결과의 공통된 행만 출력 (교집합) |
| **EXCEPT** | 첫 번째 결과에서 두 번째 결과를 제외 (차집합) |

**예제 1)** 직원 ∪ 계약직 (중복 제거)

```sql
SELECT * FROM 직원
UNION
SELECT * FROM 계약직;
```

**예제 2)** 직원 ∩ 계약직 (공통 행만)

```sql
SELECT * FROM 직원
INTERSECT
SELECT * FROM 계약직;
```

---

# PART 2. JOIN

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
JOIN은 두 개 이상의 테이블을 연결하여 데이터를 검색하는 핵심 기법입니다. INNER JOIN과 OUTER JOIN의 차이, 그리고 다양한 표기 형식을 반드시 구분하세요.
</p>
</div>

## 2.1 JOIN의 개념

<span class="blue-text">JOIN</span>은 2개의 릴레이션에서 연관된 튜플들을 결합하여 하나의 새로운 릴레이션을 반환한다.

- 일반적으로 FROM절에 기술하지만, 릴레이션이 사용되는 곳 어디에서나 사용 가능하다.
- JOIN은 크게 <span class="blue-text">INNER JOIN</span>과 <span class="blue-text">OUTER JOIN</span>으로 구분된다.

| 분류 | 종류 |
|------|------|
| INNER JOIN | EQUI JOIN, NON-EQUI JOIN, NATURAL JOIN |
| OUTER JOIN | LEFT OUTER JOIN, RIGHT OUTER JOIN, FULL OUTER JOIN |

다음 예제들은 아래의 테이블을 기준으로 합니다.

**&lt;수강생&gt; 테이블**

| 번호 | 이름 | 과정코드 | 멘토 | 점수 |
|------|------|----------|------|------|
| 101 | 김도윤 | dev | | 88 |
| 102 | 이서연 | des | | 92 |
| 103 | 박준서 | dev | 101 | 97 |
| 104 | 최하윤 | des | 102 | 70 |
| 105 | 정우진 | | 103 | 58 |

**&lt;과정&gt; 테이블**

| 과정코드 | 과정명 |
|----------|--------|
| dev | 개발 |
| des | 디자인 |
| mkt | 마케팅 |

**&lt;점수등급&gt; 테이블**

| 등급 | 하한 | 상한 |
|------|------|------|
| S | 90 | 100 |
| A | 80 | 89 |
| B | 60 | 79 |
| C | 0 | 59 |

---

## 2.2 INNER JOIN

### EQUI JOIN (동등 조인)

<span class="blue-text">EQUI JOIN</span>은 `=` 비교에 의해 같은 값을 가지는 행을 연결하여 결과를 생성하는 방법이다.

- 중복된 속성을 제거하여 한 번만 표기하는 방법을 <span class="yellow-code">NATURAL JOIN</span>이라 한다.
- 연결 고리가 되는 공통 속성을 <span class="green-text">JOIN 속성</span>이라 한다.

**표기 형식 1 - WHERE절 사용**

```sql
SELECT [테이블명1.]속성명, [테이블명2.]속성명, ...
FROM 테이블명1, 테이블명2
WHERE 테이블명1.속성명 = 테이블명2.속성명;
```

**표기 형식 2 - NATURAL JOIN 사용**

```sql
SELECT [테이블명1.]속성명, [테이블명2.]속성명, ...
FROM 테이블명1 NATURAL JOIN 테이블명2;
```

**표기 형식 3 - USING절 사용**

```sql
SELECT [테이블명1.]속성명, [테이블명2.]속성명, ...
FROM 테이블명1 JOIN 테이블명2 USING(속성명);
```

**표기 형식 4 - ON절 사용**

```sql
SELECT [테이블명1.]속성명, [테이블명2.]속성명, ...
FROM 테이블명1 INNER JOIN 테이블명2
ON 테이블명1.속성명 = 테이블명2.속성명;
```

**예제 1)** &lt;수강생&gt;과 &lt;과정&gt;에서 '과정코드'가 같은 튜플을 JOIN하여 '번호', '이름', '과정코드', '과정명'을 출력하시오.

```sql
-- WHERE절 사용
SELECT 번호, 이름, 수강생.과정코드, 과정명
FROM 수강생, 과정
WHERE 수강생.과정코드 = 과정.과정코드;

-- NATURAL JOIN 사용
SELECT 번호, 이름, 과정코드, 과정명
FROM 수강생 NATURAL JOIN 과정;

-- USING절 사용
SELECT 번호, 이름, 과정코드, 과정명
FROM 수강생 JOIN 과정 USING(과정코드);
```

**결과:**

| 번호 | 이름 | 과정코드 | 과정명 |
|------|------|----------|--------|
| 101 | 김도윤 | dev | 개발 |
| 102 | 이서연 | des | 디자인 |
| 103 | 박준서 | dev | 개발 |
| 104 | 최하윤 | des | 디자인 |

※ 정우진(105)은 과정코드가 NULL이므로 제외됨

---

### NON-EQUI JOIN

<span class="blue-text">NON-EQUI JOIN</span>은 `=` 이외의 비교 연산자(`>`, `<`, `>=`, `<=`, `BETWEEN` 등)를 사용하는 JOIN 방법이다.

**예제 2)** &lt;수강생&gt;과 &lt;점수등급&gt;을 JOIN하여 각 수강생의 '번호', '이름', '점수', '등급'을 출력하시오.

```sql
SELECT 번호, 이름, 점수, 등급
FROM 수강생, 점수등급
WHERE 수강생.점수 BETWEEN 점수등급.하한 AND 점수등급.상한;
```

**결과:**

| 번호 | 이름 | 점수 | 등급 |
|------|------|------|------|
| 101 | 김도윤 | 88 | A |
| 102 | 이서연 | 92 | S |
| 103 | 박준서 | 97 | S |
| 104 | 최하윤 | 70 | B |
| 105 | 정우진 | 58 | C |

---

## 2.3 OUTER JOIN

<span class="blue-text">OUTER JOIN</span>은 JOIN 조건에 만족하지 않는 튜플도 결과로 출력하기 위한 JOIN 방법이다.

### LEFT OUTER JOIN

INNER JOIN의 결과를 구한 후, 오른쪽 릴레이션의 어떤 튜플과도 맞지 않는 <span class="red-text">왼쪽 릴레이션</span>의 튜플들에 NULL 값을 붙여 결과에 추가한다.

```sql
SELECT [테이블명1.]속성명, [테이블명2.]속성명, ...
FROM 테이블명1 LEFT OUTER JOIN 테이블명2
ON 테이블명1.속성명 = 테이블명2.속성명;
```

**예제)** &lt;수강생&gt;과 &lt;과정&gt;에서 과정코드가 같은 튜플을 JOIN하되, 과정코드가 없는 수강생도 포함하여 출력하시오.

```sql
SELECT 번호, 이름, 수강생.과정코드, 과정명
FROM 수강생 LEFT OUTER JOIN 과정
ON 수강생.과정코드 = 과정.과정코드;
```

**결과:**

| 번호 | 이름 | 과정코드 | 과정명 |
|------|------|----------|--------|
| 101 | 김도윤 | dev | 개발 |
| 102 | 이서연 | des | 디자인 |
| 103 | 박준서 | dev | 개발 |
| 104 | 최하윤 | des | 디자인 |
| 105 | 정우진 | NULL | NULL |

---

### RIGHT OUTER JOIN

INNER JOIN의 결과를 구한 후, 왼쪽 릴레이션의 어떤 튜플과도 맞지 않는 <span class="red-text">오른쪽 릴레이션</span>의 튜플들에 NULL 값을 붙여 결과에 추가한다.

```sql
SELECT [테이블명1.]속성명, [테이블명2.]속성명, ...
FROM 테이블명1 RIGHT OUTER JOIN 테이블명2
ON 테이블명1.속성명 = 테이블명2.속성명;
```

---

### FULL OUTER JOIN

LEFT OUTER JOIN과 RIGHT OUTER JOIN을 합쳐 놓은 것으로, 양쪽 릴레이션에서 조건에 맞지 않는 <span class="red-text">모든 튜플</span>을 포함한다.

```sql
SELECT [테이블명1.]속성명, [테이블명2.]속성명, ...
FROM 테이블명1 FULL OUTER JOIN 테이블명2
ON 테이블명1.속성명 = 테이블명2.속성명;
```

**예제)** &lt;수강생&gt;과 &lt;과정&gt;에서 과정코드가 같은 튜플을 JOIN하되, 과정코드가 없는 수강생이나 수강생이 없는 과정도 모두 출력하시오.

```sql
SELECT 번호, 이름, 수강생.과정코드, 과정명
FROM 수강생 FULL OUTER JOIN 과정
ON 수강생.과정코드 = 과정.과정코드;
```

**결과:**

| 번호 | 이름 | 과정코드 | 과정명 |
|------|------|----------|--------|
| 101 | 김도윤 | dev | 개발 |
| 102 | 이서연 | des | 디자인 |
| 103 | 박준서 | dev | 개발 |
| 104 | 최하윤 | des | 디자인 |
| 105 | 정우진 | NULL | NULL |
| NULL | NULL | mkt | 마케팅 |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">OUTER JOIN 정리</strong>
</div>
<table style="width: 100%; border-collapse: collapse; font-size: 0.9rem;">
<tr style="background-color: #f9fafb;">
<th style="border: 1px solid #e5e7eb; padding: 8px;">종류</th>
<th style="border: 1px solid #e5e7eb; padding: 8px;">NULL이 추가되는 위치</th>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">LEFT OUTER JOIN</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">오른쪽 테이블에 NULL 추가 (왼쪽 테이블 기준)</td>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">RIGHT OUTER JOIN</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">왼쪽 테이블에 NULL 추가 (오른쪽 테이블 기준)</td>
</tr>
<tr>
<td style="border: 1px solid #e5e7eb; padding: 8px;">FULL OUTER JOIN</td>
<td style="border: 1px solid #e5e7eb; padding: 8px;">양쪽 모두에 NULL 추가</td>
</tr>
</table>
</div>

---

# 연습문제

## Part 1 - SELECT

<div class="quiz-number">문제 1</div><strong>&lt;수강생&gt; 테이블에서 학기가 2 이상인 레코드의 과정코드를 검색하되, 동일한 과정코드는 한 번만 출력되도록 하는 SQL문이다. 괄호에 들어갈 알맞은 명령어를 쓰시오.</strong>

{% capture code_block1 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;수강생&gt;

학번    | 이름   | 학기 | 과정코드
--------|--------|------|--------
S101    | 김도윤 | 1    | WE
S102    | 이서연 | 3    | DS
S103    | 박준서 | 2    | AI
S104    | 최하윤 | 1    | WE
S105    | 정우진 | 2    | DS
S106    | 한소율 | 4    | AI
S107    | 오지훈 | 1    | WE

SELECT (      ) 과정코드
FROM 수강생
WHERE 학기 >= 2;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_select"
   code_html=code_block1
   answer="DISTINCT"
   tags="SELECT, DISTINCT"
%}

---

<div class="quiz-number">문제 2</div><strong>&lt;직원&gt; 테이블에서 '성과급'이 500 이상인 데이터를 조회하는 SQL문이다. 괄호에 알맞은 조건을 쓰시오.</strong>

{% capture code_block2 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;직원&gt;

사번   | 유저명 | 성과급
-------|--------|------
E101   | 김태현 | 200
E102   | 박수진 | 350
E103   | 이준혁 | 520
E104   | 정미래 | 780
E105   | 오세영 | 490
E106   | 한지우 | 610

SELECT *
FROM 직원
WHERE (                 );</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz2_select"
   code_html=code_block2
   answer="성과급 >= 500"
   tags="SELECT, WHERE"
%}

---

<div class="quiz-number">문제 3</div><strong>&lt;수강생&gt; 테이블에서 3학기이거나 전공이 '소프트웨어'인 수강생의 이름을 조회하는 SQL문이다. 괄호에 들어갈 알맞은 연산자를 쓰시오.</strong>

{% capture code_block3 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;수강생&gt;

번호 | 이름   | 전공       | 학기 | 평점
-----|--------|------------|------|-----
1    | 김도윤 | 소프트웨어 | 1    | 3.5
2    | 이서연 | 건축       | 1    | 4.0
3    | 박준서 | 기계       | 3    | 2.8
4    | 최하윤 | 소프트웨어 | 3    | 4.2
5    | 정우진 | 기계       | 2    | 3.9

SELECT 이름
FROM 수강생
WHERE 학기 = 3 (      ) 전공 = '소프트웨어';</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_select"
   code_html=code_block3
   answer="OR"
   tags="SELECT, WHERE"
%}

---

<div class="quiz-number">문제 4</div><strong>&lt;직원&gt; 테이블에서 '팀'이 '개발'인 튜플의 사번과 유저명을 검색하고자 한다. 괄호(①~③)에 알맞은 명령어를 쓰시오.</strong>

{% capture code_block4 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT ( ① ), ( ② )
FROM 직원 ( ③ ) 팀 = '개발';</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz4_select"
   code_html=code_block4
   answer="사번, 유저명, WHERE|사번,유저명,WHERE"
   tags="SELECT, WHERE"
%}

---

<div class="quiz-number">문제 5</div><strong>다음은 SELECT문의 실행 순서를 나열한 것이다. 괄호(①~③)에 들어갈 알맞은 절을 &lt;보기&gt;에서 찾아 쓰시오.</strong>

{% capture code_block5 %}
<div style="margin: 15px 0; line-height: 1.8;">
FROM → ( ① ) → ( ② ) → ( ③ ) → SELECT → ORDER BY<br><br>
<strong>&lt;보기&gt;</strong><br>
HAVING, GROUP BY, WHERE
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz5_select"
   code_html=code_block5
   answer="WHERE, GROUP BY, HAVING|WHERE,GROUP BY,HAVING"
   tags="SELECT, 실행 순서"
%}

---

<div class="quiz-number">문제 6</div><strong>&lt;교재&gt;, &lt;교재가격&gt; 테이블을 참고하여 다음 SQL문의 실행 결과를 쓰시오.</strong>

{% capture code_block6 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;교재&gt;

교재번호 | 교재명
---------|----------
A111     | 네트워크개론
A222     | 알고리즘
A333     | 데이터분석

&lt;교재가격&gt;

교재번호 | 가격
---------|------
A111     | 22000
A222     | 18000
A333     | 15000
A444     | 9000

SELECT 가격
FROM 교재가격
WHERE 교재번호 = (
  SELECT 교재번호
  FROM 교재
  WHERE 교재명 = '알고리즘'
);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_select"
   code_html=code_block6
   answer="18000"
   tags="SELECT, 하위 질의"
%}

---

<div class="quiz-number">문제 7</div><strong>여러 개의 SQL문 결과에 대한 합집합을 구하되, 중복된 행은 한 번만 출력하는 집합 연산자를 쓰시오.</strong>

{% include quiz-text.html
   id="quiz7_select"
   answer="UNION"
   tags="SELECT, 집합 연산자"
%}

---

<div class="quiz-number">문제 8</div><strong>&lt;고객&gt; 테이블에서 '이메일' 필드가 비어있는 고객의 유저명을 검색하는 SQL문이다. 괄호에 들어갈 알맞은 명령어를 쓰시오.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;고객&gt;

고객번호 | 유저명 | 이메일
---------|--------|---------------
C1       | 김도윤 | kim@mail.com
C2       | 이서연 | lee@mail.com
C3       | 박준서 | park@mail.com
C4       | 최하윤 |
C5       | 정우진 | jung@mail.com

SELECT 유저명
FROM 고객
WHERE 이메일 (        );</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8_select"
   code_html=code_block8
   answer="IS NULL"
   tags="SELECT, NULL"
%}

---

<div class="quiz-number">문제 9</div><strong>다음은 &lt;dept&gt; 테이블의 'name' 필드와 &lt;team&gt; 테이블의 'name' 필드를 통합하되, 중복된 레코드도 모두 출력하는 SQL문이다. 괄호에 들어갈 알맞은 명령어를 쓰시오.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>SELECT name FROM dept
UNION (        )
SELECT name FROM team;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_select"
   code_html=code_block9
   answer="ALL"
   tags="SELECT, UNION ALL"
%}

---

<div class="quiz-number">문제 10</div><strong>다음 &lt;회원&gt;, &lt;도서&gt;, &lt;대출&gt; 테이블을 참고하여 SQL문의 실행 결과로 출력되는 유저명을 모두 쓰시오. (쉼표로 구분)</strong>

{% capture code_block10 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;회원&gt;
회원코드 | 유저명 | 연락처
---------|--------|----------
M1       | 김태현 | 010-1111
M2       | 박수진 | 010-2222
M3       | 이준혁 | 010-3333
M4       | 정미래 | 010-4444
M5       | 오세영 | 010-5555

&lt;대출&gt;
회원코드 | 유저명 | 도서코드
---------|--------|----------
M1       | 김태현 | B2
M1       | 김태현 | B3
M2       | 박수진 | B4
M2       | 박수진 | B5
M3       | 이준혁 | B1
M3       | 이준혁 | B3
M4       | 정미래 | B3
M4       | 정미래 | B4
M5       | 오세영 | B5
M5       | 오세영 | B1

SELECT 회원.유저명, 회원.연락처
FROM 회원, 대출
WHERE 회원.회원코드 = 대출.회원코드
  AND 대출.도서코드 = 'B3';</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz10_select"
   code_html=code_block10
   answer="김태현, 이준혁, 정미래|김태현,이준혁,정미래"
   tags="SELECT, 복수 테이블"
%}

---

## Part 2 - JOIN

<div class="quiz-number">문제 11</div><strong>다음 &lt;직원&gt;, &lt;평가&gt; 테이블과 결과를 참고하여 SQL문의 괄호에 들어갈 알맞은 연산자를 쓰시오.</strong>

{% capture code_block11 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;직원&gt;
사번   | 유저명 | 직책
-------|--------|------
3001   | 김현우 | 영업
3002   | 이수민 | 개발
3003   | 박지영 | 영업
3004   | 최민호 | 인사
3005   | 장서윤 | 개발
3006   | 한도현 | 개발
3007   | 윤채원 | 인사

&lt;평가&gt;
대상번호 | 등급
---------|------
3001     | B+
3002     | A
3004     | C
3006     | A-
3008     | B

&lt;결과&gt;
사번   | 유저명
-------|--------
3004   | 최민호

SELECT 사번, 유저명
FROM 직원, 평가
WHERE 사번 = 대상번호 (        ) 직책 = '인사';</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_join"
   code_html=code_block11
   answer="AND"
   tags="JOIN, WHERE"
%}

---

<div class="quiz-number">문제 12</div><strong>다음은 &lt;실적&gt; 테이블의 매출액이 3000 초과인 항목에 대해 &lt;주문&gt; 테이블의 수량을 &lt;실적&gt; 테이블의 수량으로 갱신하는 SQL문이다. 괄호에 적절한 예약어를 쓰시오.</strong>

{% capture code_block12 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>UPDATE 주문 a INNER JOIN 실적 b
(        ) a.코드 = b.코드
SET a.수량 = b.수량
WHERE b.매출액 > 3000;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz12_join"
   code_html=code_block12
   answer="ON"
   tags="JOIN, UPDATE"
%}

---

<div class="quiz-number">문제 13</div><strong>다음 &lt;수강생&gt;, &lt;성적&gt; 테이블과 결과를 분석하여 SQL문의 괄호에 들어갈 알맞은 명령어를 쓰시오. (mydb는 두 테이블이 속한 데이터베이스명)</strong>

{% capture code_block13 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;수강생&gt;
번호 | 이름   | 연락처     | 전공
-----|--------|------------|----------
1    | 김도윤 | 010-1111   | 컴퓨터공학
2    | 이서연 | 010-2222   | 전자공학
3    | 박준서 | 010-3333   | 생명공학
4    | 최하윤 | 010-4444   | 로봇공학
5    | 정우진 | 010-5555   | 유전공학

&lt;성적&gt;
번호 | 점수
-----|------
1    | 88
2    | 91
3    | 73
4    | 82
5    | 95

&lt;결과&gt;
번호 | 이름   | 전공       | 점수
-----|--------|------------|------
1    | 김도윤 | 컴퓨터공학 | 88
2    | 이서연 | 전자공학   | 91
3    | 박준서 | 생명공학   | 73
4    | 최하윤 | 로봇공학   | 82
5    | 정우진 | 유전공학   | 95

SELECT 번호, 이름, 전공, 점수
FROM mydb.수강생, mydb.성적
(        ) mydb.수강생.번호 = mydb.성적.번호;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz13_join"
   code_html=code_block13
   answer="WHERE"
   tags="JOIN, WHERE"
%}

---

<div class="quiz-number">문제 14</div><strong>다음은 &lt;게시판&gt; 테이블과 &lt;작성자&gt; 테이블을 결합하는 SQL문이다. 결과를 참고하여 괄호에 들어갈 알맞은 명령어를 쓰시오.</strong>

{% capture code_block14 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>&lt;게시판&gt;
글번호 | 제목   | 내용       | 작성자ID
-------|--------|------------|--------
1      | sql    | sql입문    | 1
2      | java   | java기초   | 1
3      | python | python심화 | 3
4      | react  | react개발  | 2
5      | linux  | linux명령  | 1

&lt;작성자&gt;
ID | 이름   | 역할
---|--------|--------
1  | 김도윤 | 강사
2  | 이서연 | DBA
3  | 박준서 | 연구원

SELECT * FROM 게시판
LEFT (        ) 작성자
ON 게시판.작성자ID = 작성자.ID;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz14_join"
   code_html=code_block14
   answer="JOIN|OUTER JOIN"
   tags="JOIN, LEFT JOIN"
%}

---

# 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">SELECT문</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>기본 형식</strong>: SELECT ~ FROM ~ WHERE ~ GROUP BY ~ HAVING ~ ORDER BY</li>
<li><strong>실행 순서</strong>: FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY</li>
<li><strong>DISTINCT</strong>: 중복 행 제거</li>
<li><strong>LIKE</strong>: 패턴 검색 (%, _, #)</li>
<li><strong>IS NULL / IS NOT NULL</strong>: NULL 값 비교</li>
<li><strong>집합 연산자</strong>: UNION(중복제거), UNION ALL(중복포함), INTERSECT(교집합), EXCEPT(차집합)</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">그룹 함수</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>AVG</strong>: 평균, <strong>SUM</strong>: 합계, <strong>COUNT</strong>: 개수</li>
<li><strong>MAX</strong>: 최댓값, <strong>MIN</strong>: 최솟값</li>
<li><strong>GROUP BY</strong>로 그룹화 후 <strong>HAVING</strong>으로 그룹 조건 지정</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">JOIN</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>EQUI JOIN</strong>: = 조건으로 같은 값의 행을 연결 (WHERE, NATURAL JOIN, USING, ON)</li>
<li><strong>NON-EQUI JOIN</strong>: &gt;, &lt;, BETWEEN 등 비교 연산자 사용</li>
<li><strong>LEFT OUTER JOIN</strong>: 왼쪽 테이블 기준, 매칭 안 되는 행에 NULL 추가</li>
<li><strong>RIGHT OUTER JOIN</strong>: 오른쪽 테이블 기준, 매칭 안 되는 행에 NULL 추가</li>
<li><strong>FULL OUTER JOIN</strong>: 양쪽 모두 매칭 안 되는 행에 NULL 추가</li>
</ul>

</div>

---
