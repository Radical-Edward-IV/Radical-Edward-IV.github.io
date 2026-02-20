---
layout: article
title: 6. SQL의 기본
permalink: /notes/kr/info-processing-technician/chapter-07
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - SQL의 개념과 분류, DDL(데이터 정의어), DCL(데이터 제어어), DML(데이터 조작어)을 학습합니다.
keywords: "프로그래밍기능사, SQL, DDL, DML, DCL, CREATE, SELECT, INSERT, DELETE, UPDATE, GRANT, REVOKE, COMMIT, ROLLBACK"
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

# PART 1. SQL의 개념

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">전문가의 조언</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
SQL은 데이터 정의(DDL), 데이터 조작(DML), 데이터 제어(DCL) 기능을 모두 갖추고 있습니다. SQL의 개념과 각 분류별 명령어를 정확히 구분할 수 있어야 합니다.
</p>
</div>

## 1.1 SQL(Structured Query Language)의 개요

<span class="blue-text">SQL</span>은 관계형 데이터베이스(RDB)에서 데이터를 정의하고, 조작하고, 제어하기 위한 표준 언어입니다.

- 1974년 IBM 연구소에서 개발된 <span class="yellow-code">SEQUEL</span>이 시초이다.
- IBM뿐 아니라 다수의 기업에서 관계형 데이터베이스를 지원하는 언어로 채택하고 있다.
- 관계대수와 관계해석을 기초로 한 <span class="blue-text">혼합 데이터 언어</span>이다.
- 질의어라는 명칭이지만 질의 기능만 있는 것이 아니라 <span class="green-text">데이터 구조의 정의, 데이터 조작, 데이터 제어 기능</span>을 모두 갖추고 있다.

---

## 1.2 SQL의 분류

SQL은 사용 목적에 따라 <span class="blue-text">DDL</span>(데이터 정의어), <span class="blue-text">DML</span>(데이터 조작어), <span class="blue-text">DCL</span>(데이터 제어어)로 구분된다.

### DDL(Data Definition Language, 데이터 정의어)

- SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의하거나 변경 또는 삭제할 때 사용한다.
- 주로 데이터베이스 관리자나 설계자가 사용한다.

| 명령어 | 기능 |
|--------|------|
| **CREATE** | SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의한다. |
| **ALTER** | TABLE에 대한 정의를 변경할 때 사용한다. |
| **DROP** | SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 삭제한다. |

### DML(Data Manipulation Language, 데이터 조작어)

- 데이터베이스에 저장된 데이터를 실질적으로 처리하는 데 사용한다.
- 데이터베이스 사용자와 DBMS 간의 인터페이스를 제공한다.

| 명령어 | 기능 |
|--------|------|
| **SELECT** | 테이블에서 조건에 맞는 튜플을 검색한다. |
| **INSERT** | 테이블에 새로운 튜플을 삽입한다. |
| **DELETE** | 테이블에서 조건에 맞는 튜플을 삭제한다. |
| **UPDATE** | 테이블에서 조건에 맞는 튜플의 내용을 변경한다. |

### DCL(Data Control Language, 데이터 제어어)

- 데이터의 보안, 무결성, 회복, 병행 수행 제어 등을 정의한다.
- 주로 데이터베이스 관리자가 데이터 관리 목적으로 사용한다.

| 명령어 | 기능 |
|--------|------|
| **COMMIT** | 수행된 결과를 실제 물리적 디스크에 저장하고, 작업의 정상 완료를 알린다. |
| **ROLLBACK** | 작업이 비정상적으로 종료되었을 때 원래 상태로 복구한다. |
| **GRANT** | 데이터베이스 사용자에게 사용 권한을 부여한다. |
| **REVOKE** | 데이터베이스 사용자의 사용 권한을 취소한다. |

---

# PART 2. DDL

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
DDL의 각 명령어(CREATE, ALTER, DROP)의 문법을 정확히 이해하세요. 특히 CREATE TABLE의 제약 조건과 ALTER TABLE의 세부 옵션이 자주 출제됩니다.
</p>
</div>

## 2.1 DDL의 개념

<span class="blue-text">DDL(Data Definition Language)</span>은 DB 구조, 데이터 형식, 접근 방식 등 데이터베이스를 구축하거나 수정할 목적으로 사용하는 언어이다.

- DDL을 번역한 결과는 <span class="yellow-code">데이터 사전(Data Dictionary)</span>이라는 특별한 파일에 여러 테이블로 저장된다.
- CREATE SCHEMA, CREATE DOMAIN, CREATE TABLE, CREATE VIEW, CREATE INDEX, ALTER TABLE, DROP 등이 있다.

---

## 2.2 CREATE SCHEMA

스키마를 정의하는 명령문으로, 스키마 이름과 소유권자를 지정한다.

```sql
CREATE SCHEMA 스키마명 AUTHORIZATION 사용자_id;
```

**예제)** 소유권자가 '이순신'인 스키마 '온라인도서관'을 정의하시오.

```sql
CREATE SCHEMA 온라인도서관 AUTHORIZATION 이순신;
```

---

## 2.3 CREATE DOMAIN

도메인을 정의하는 명령문으로, 속성이 취할 수 있는 값의 범위를 지정한다.

```sql
CREATE DOMAIN 도메인명 [AS] 데이터_타입
    [DEFAULT 기본값]
    [CONSTRAINT 제약조건명 CHECK (범위값)];
```

**예제)** '직급'이 '사원', '대리', '과장' 중 하나의 값만 가질 수 있도록 도메인 POSITION_TYPE을 정의하시오.

```sql
CREATE DOMAIN POSITION_TYPE CHAR(2)
    DEFAULT '사원'
    CONSTRAINT VALID-POSITION CHECK(VALUE IN ('사원', '대리', '과장'));
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">SQL의 기본 데이터 타입</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <strong>정수</strong> : INTEGER(4Byte), SMALLINT(2Byte)<br>
• <strong>실수</strong> : FLOAT, REAL, DOUBLE PRECISION<br>
• <strong>형식화된 숫자</strong> : DEC(i, j) — i: 전체 자릿수, j: 소수부 자릿수<br>
• <strong>고정길이 문자</strong> : CHAR(n), CHARACTER(n)<br>
• <strong>가변길이 문자</strong> : VARCHAR(n), CHARACTER VARYING(n)<br>
• <strong>날짜</strong> : DATE &nbsp; • <strong>시간</strong> : TIME
</p>
</div>

---

## 2.4 CREATE TABLE

테이블을 정의하는 명령문이다.

```sql
CREATE TABLE 테이블명
(속성명 데이터_타입 [DEFAULT 기본값] [NOT NULL], ...
[, PRIMARY KEY(기본키_속성명, ...)]
[, UNIQUE(대체키_속성명, ...)]
[, FOREIGN KEY(외래키_속성명, ...)]
    REFERENCES 참조테이블(기본키_속성명, ...)]
[, CONSTRAINT 제약조건명 CHECK (조건식)]);
```

- **PRIMARY KEY** : 기본키로 사용할 속성을 지정한다.
- **UNIQUE** : 대체키로 지정하며, 중복된 값을 가질 수 없다.
- **FOREIGN KEY ~ REFERENCES ~** : 참조할 다른 테이블과 외래키 속성을 지정한다.
- **CONSTRAINT** : 제약 조건의 이름을 지정한다.
- **CHECK** : 속성 값에 대한 제약 조건을 정의한다.

**예제)** '성명', '사번', '부서코드', '직급', '입사일'로 구성된 &lt;직원&gt; 테이블을 정의하시오.

```sql
CREATE TABLE 직원
(성명 VARCHAR(15) NOT NULL,
 사번 CHAR(8),
 부서코드 CHAR(5),
 직급 POSITION_TYPE,
 입사일 DATE,
 PRIMARY KEY(사번),
 FOREIGN KEY(부서코드)
     REFERENCES 부서(부서코드),
 CHECK(직급 = '사원'));
```

---

## 2.5 CREATE VIEW

뷰(View)를 정의하는 명령문이다.

```sql
CREATE VIEW 뷰명[(속성명, 속성명, ...)]
AS SELECT문;
```

- SELECT문을 서브 쿼리로 사용하여 뷰를 생성한다.
- 서브 쿼리인 SELECT문에는 <span class="red-text">UNION이나 ORDER BY절을 사용할 수 없다</span>.
- 속성명을 기술하지 않으면 SELECT문의 속성명이 자동으로 사용된다.

**예제)** &lt;회원&gt; 테이블에서 '지역'이 '서울'인 회원들의 '이름'과 '연락처'를 '서울회원'이라는 뷰로 정의하시오.

```sql
CREATE VIEW 서울회원(이름, 연락처)
AS SELECT 이름, 연락처
   FROM 회원
   WHERE 지역 = '서울';
```

---

## 2.6 CREATE INDEX

인덱스를 정의하는 명령문이다.

```sql
CREATE [UNIQUE] INDEX 인덱스명
ON 테이블명(속성명 [ASC | DESC], ...)
[CLUSTER];
```

- **UNIQUE** 사용 시 : 중복 값이 없는 고유한 인덱스를 생성한다.
- **ASC** : 오름차순 정렬 / **DESC** : 내림차순 정렬 (생략 시 오름차순)
- **CLUSTER** : 클러스터드 인덱스로 설정한다.

**예제)** &lt;직원&gt; 테이블에서 UNIQUE한 특성을 갖는 '사번' 속성에 대해 내림차순으로 '사번_idx'라는 인덱스를 정의하시오.

```sql
CREATE UNIQUE INDEX 사번_idx
ON 직원(사번 DESC);
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">인덱스 재구성(INDEX REBUILD)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
데이터의 반복적인 INSERT, UPDATE, DELETE로 인해 <span class="red-text">단편화(Fragmentation)</span>가 발생하면 인덱스 성능이 저하됩니다. 이때 인덱스 재구성을 통해 구조를 다시 정렬하여 효율적인 상태로 복원합니다.
</p>
</div>

---

## 2.7 ALTER TABLE

테이블의 정의를 변경하는 명령문이다.

```sql
ALTER TABLE 테이블명 ADD 속성명 데이터_타입;
ALTER TABLE 테이블명 ALTER 속성명 데이터_타입;
ALTER TABLE 테이블명 DROP COLUMN 속성명 [CASCADE];
```

- **ADD** : 새로운 속성(열)을 추가한다.
- **ALTER** : 특정 속성의 데이터 타입이나 크기를 변경한다.
- **DROP COLUMN** : 특정 속성을 삭제한다.

**예제1)** &lt;직원&gt; 테이블에 최대 30글자로 구성되는 '주소' 속성을 추가하시오.

```sql
ALTER TABLE 직원 ADD 주소 VARCHAR(30);
```

**예제2)** &lt;직원&gt; 테이블의 '사번' 필드를 VARCHAR(12)으로 변경하고 NULL 값이 입력되지 않도록 변경하시오.

```sql
ALTER TABLE 직원 ALTER 사번 VARCHAR(12) NOT NULL;
```

---

## 2.8 DROP

스키마, 도메인, 테이블, 뷰, 인덱스, 제약 조건 등을 제거하는 명령문이다.

```sql
DROP SCHEMA 스키마명 [CASCADE | RESTRICT];
DROP DOMAIN 도메인명 [CASCADE | RESTRICT];
DROP TABLE 테이블명 [CASCADE | RESTRICT];
DROP VIEW 뷰명 [CASCADE | RESTRICT];
DROP INDEX 인덱스명 [CASCADE | RESTRICT];
DROP CONSTRAINT 제약조건명;
```

- **CASCADE** : 제거할 요소를 참조하는 다른 모든 개체를 <span class="red-text">함께 제거</span>한다.
- **RESTRICT** : 다른 개체가 참조 중이면 <span class="green-text">제거를 취소</span>한다.

**예제)** &lt;직원&gt; 테이블을 제거하되, 참조하는 모든 데이터를 함께 제거하시오.

```sql
DROP TABLE 직원 CASCADE;
```

---

# PART 3. DCL

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
GRANT/REVOKE의 권한 부여·취소 문법과 COMMIT/ROLLBACK/SAVEPOINT의 트랜잭션 제어 흐름을 정확히 파악하세요.
</p>
</div>

## 3.1 DCL의 개념

<span class="blue-text">DCL(Data Control Language)</span>은 데이터의 보안, 무결성, 회복, 병행 제어 등을 정의하는 언어이다.

- 데이터베이스 관리자(DBA)가 데이터 관리를 목적으로 사용한다.
- GRANT, REVOKE, COMMIT, ROLLBACK, SAVEPOINT 등이 있다.

---

## 3.2 GRANT / REVOKE

데이터베이스 사용자에게 권한을 부여하거나 취소하기 위한 명령어이다.

**사용자등급 지정 및 해제**

```sql
GRANT 사용자등급 TO 사용자_ID_리스트 [IDENTIFIED BY 암호];
REVOKE 사용자등급 FROM 사용자_ID_리스트;
```

**예제1)** 사용자 ID가 'PARK'인 사람에게 데이터베이스 및 테이블을 생성할 수 있는 권한을 부여하시오.

```sql
GRANT RESOURCE TO PARK;
```

**예제2)** 사용자 ID가 'CHOI'인 사람에게 데이터베이스의 정보를 검색할 수 있는 권한을 부여하시오.

```sql
GRANT CONNECT TO CHOI;
```

**테이블 및 속성에 대한 권한 부여 및 취소**

```sql
GRANT 권한_리스트 ON 객체 TO 사용자 [WITH GRANT OPTION];
REVOKE [GRANT OPTION FOR] 권한_리스트 ON 객체 FROM 사용자 [CASCADE];
```

- **WITH GRANT OPTION** : 부여받은 권한을 다른 사용자에게 다시 부여할 수 있는 권한까지 부여
- **GRANT OPTION FOR** : 다른 사용자에게 권한을 부여할 수 있는 권한만 취소
- **CASCADE** : 연쇄적으로 권한 취소

**예제3)** 사용자 'PARK'에게 &lt;주문&gt; 테이블에 대한 모든 권한과 다른 사람에게 권한을 부여할 수 있는 권한까지 부여하시오.

```sql
GRANT ALL ON 주문 TO PARK WITH GRANT OPTION;
```

**예제4)** 사용자 'CHOI'에게 부여한 &lt;주문&gt; 테이블에 대한 UPDATE 권한을 다른 사람에게 부여할 수 있는 권한만 취소하시오.

```sql
REVOKE GRANT OPTION FOR UPDATE ON 주문 FROM CHOI;
```

---

## 3.3 COMMIT

트랜잭션이 성공적으로 완료되면 변경된 모든 내용을 데이터베이스에 반영하기 위해 사용한다.

- DML문이 성공적으로 완료되면 자동으로 COMMIT되도록 <span class="yellow-code">Auto Commit</span> 기능을 설정할 수 있다.

---

## 3.4 ROLLBACK

아직 COMMIT되지 않은 변경 내용을 모두 취소하고 데이터베이스를 이전 상태로 되돌린다.

- 일부만 완료된 트랜잭션은 비일관성(Inconsistency) 상태를 방지하기 위해 롤백되어야 한다.

---

## 3.5 SAVEPOINT

트랜잭션 내에 ROLLBACK할 위치인 저장점을 지정하는 명령어이다.

- 저장점에 이름을 부여하며, ROLLBACK 시 지정된 저장점까지의 처리 내용만 취소된다.

**SAVEPOINT 예제 시나리오**

&lt;도서&gt; 테이블 (초기 상태)

| 도서번호 | 제목 | 분류 |
|---------|------|------|
| B01 | 자바의 정석 | 프로그래밍 |
| B02 | 파이썬 입문 | 프로그래밍 |
| B03 | 네트워크 개론 | 네트워크 |
| B04 | DB 설계 실무 | 데이터베이스 |

**예제1)** 도서번호가 'B04'인 도서를 삭제한 후 COMMIT을 수행하시오.

```sql
DELETE FROM 도서 WHERE 도서번호 = 'B04';
COMMIT;
```

→ COMMIT 이후에는 ROLLBACK으로 되돌릴 수 없다.

| 도서번호 | 제목 | 분류 |
|---------|------|------|
| B01 | 자바의 정석 | 프로그래밍 |
| B02 | 파이썬 입문 | 프로그래밍 |
| B03 | 네트워크 개론 | 네트워크 |

**예제2)** 도서번호가 'B03'인 도서를 삭제하시오.

```sql
DELETE FROM 도서 WHERE 도서번호 = 'B03';
```

→ COMMIT하지 않았으므로 ROLLBACK으로 되돌릴 수 있다.

| 도서번호 | 제목 | 분류 |
|---------|------|------|
| B01 | 자바의 정석 | 프로그래밍 |
| B02 | 파이썬 입문 | 프로그래밍 |

**예제3)** SAVEPOINT 'SP1'을 설정하고 도서번호 'B02'를 삭제하시오.

```sql
SAVEPOINT SP1;
DELETE FROM 도서 WHERE 도서번호 = 'B02';
```

| 도서번호 | 제목 | 분류 |
|---------|------|------|
| B01 | 자바의 정석 | 프로그래밍 |

**예제4)** SAVEPOINT 'SP2'를 설정하고 도서번호 'B01'을 삭제하시오.

```sql
SAVEPOINT SP2;
DELETE FROM 도서 WHERE 도서번호 = 'B01';
```

| 도서번호 | 제목 | 분류 |
|---------|------|------|
| (비어 있음) | | |

**예제5)** SAVEPOINT 'SP2'까지 ROLLBACK을 수행하시오.

```sql
ROLLBACK TO SP2;
```

→ 예제4의 작업이 취소된다.

| 도서번호 | 제목 | 분류 |
|---------|------|------|
| B01 | 자바의 정석 | 프로그래밍 |

**예제6)** SAVEPOINT 'SP1'까지 ROLLBACK을 수행하시오.

```sql
ROLLBACK TO SP1;
```

→ 예제3의 작업이 취소된다.

| 도서번호 | 제목 | 분류 |
|---------|------|------|
| B01 | 자바의 정석 | 프로그래밍 |
| B02 | 파이썬 입문 | 프로그래밍 |

**예제7)** SAVEPOINT 없이 ROLLBACK을 수행하시오.

```sql
ROLLBACK;
```

→ 예제1에서 COMMIT한 시점 이후의 모든 작업이 취소된다.

| 도서번호 | 제목 | 분류 |
|---------|------|------|
| B01 | 자바의 정석 | 프로그래밍 |
| B02 | 파이썬 입문 | 프로그래밍 |
| B03 | 네트워크 개론 | 네트워크 |

---

# PART 4. DML

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
INSERT, DELETE, UPDATE의 문법 구조를 정확히 구분하세요. 특히 각 명령문의 기본 키워드(<code>INTO</code>, <code>FROM</code>, <code>SET</code>)를 빈칸으로 출제하는 문제가 자주 나옵니다.
</p>
</div>

## 4.1 DML의 개념

<span class="blue-text">DML(Data Manipulation Language)</span>은 데이터베이스에 저장된 데이터를 실질적으로 관리하는 언어이다.

| 명령문 | 기본 형식 |
|--------|----------|
| SELECT(검색) | SELECT ~ FROM ~ WHERE ~ |
| INSERT(삽입) | INSERT INTO ~ VALUES ~ |
| DELETE(삭제) | DELETE FROM ~ WHERE ~ |
| UPDATE(변경) | UPDATE ~ SET ~ WHERE ~ |

---

## 4.2 삽입문(INSERT INTO~)

기본 테이블에 새로운 튜플을 삽입할 때 사용한다.

```sql
INSERT INTO 테이블명[(속성명1, 속성명2, ...)]
VALUES (데이터1, 데이터2, ...);
```

- 속성과 데이터는 개수와 데이터 유형이 일치해야 한다.
- 모든 속성을 사용할 때는 속성명을 생략할 수 있다.
- SELECT문을 사용하여 다른 테이블의 검색 결과를 삽입할 수 있다.

&lt;상품&gt; 테이블

| 상품명 | 카테고리 | 등록일 | 제조사 | 가격 |
|--------|---------|--------|--------|------|
| 노트북A | 전자제품 | 03/15/24 | 삼성 | 150 |
| 태블릿B | 전자제품 | 06/20/23 | LG | 80 |
| 키보드C | 주변기기 | 01/10/24 | 로지텍 | 10 |
| 마우스D | 주변기기 | 09/05/23 | 로지텍 | 5 |
| 모니터E | 전자제품 | 02/28/24 | 삼성 | 45 |
| 스피커F | 주변기기 | 11/12/23 | 보스 | 30 |
| 카메라G | 전자제품 | 04/18/24 | 소니 | 120 |
| 이어폰H | 주변기기 | 07/22/24 | | 2 |

**예제1)** &lt;상품&gt; 테이블에 (상품명 – 프린터I, 카테고리 – 주변기기)를 삽입하시오.

```sql
INSERT INTO 상품(상품명, 카테고리) VALUES ('프린터I', '주변기기');
```

**예제2)** &lt;상품&gt; 테이블에 (충전기J, 주변기기, 08/01/24, 애플, 3)을 삽입하시오.

```sql
INSERT INTO 상품 VALUES ('충전기J', '주변기기', #08/01/24#, '애플', 3);
```

**예제3)** &lt;상품&gt; 테이블에서 주변기기의 모든 튜플을 주변기기목록(상품명, 등록일, 제조사, 가격) 테이블에 삽입하시오.

```sql
INSERT INTO 주변기기목록(상품명, 등록일, 제조사, 가격)
SELECT 상품명, 등록일, 제조사, 가격
FROM 상품
WHERE 카테고리 = '주변기기';
```

---

## 4.3 삭제문(DELETE FROM~)

특정 튜플(행)을 삭제할 때 사용한다.

```sql
DELETE
FROM 테이블명
[WHERE 조건];
```

- 모든 레코드를 삭제할 때는 WHERE절을 생략한다.
- 모든 레코드를 삭제하더라도 테이블 구조는 남아 있어 <span class="red-text">DROP과 다르다</span>.

**예제1)** &lt;상품&gt; 테이블에서 '키보드C'에 대한 튜플을 삭제하시오.

```sql
DELETE FROM 상품 WHERE 상품명 = '키보드C';
```

**예제2)** &lt;상품&gt; 테이블에서 '주변기기' 카테고리의 모든 튜플을 삭제하시오.

```sql
DELETE FROM 상품 WHERE 카테고리 = '주변기기';
```

**예제3)** &lt;상품&gt; 테이블의 모든 레코드를 삭제하시오.

```sql
DELETE FROM 상품;
```

---

## 4.4 갱신문(UPDATE ~ SET ~)

특정 튜플의 내용을 변경할 때 사용한다.

```sql
UPDATE 테이블명
SET 속성명 = 데이터, 속성명 = 데이터, ...
[WHERE 조건];
```

**예제1)** &lt;상품&gt; 테이블에서 '노트북A'의 제조사를 '애플'로 수정하시오.

```sql
UPDATE 상품 SET 제조사 = '애플' WHERE 상품명 = '노트북A';
```

**예제2)** &lt;상품&gt; 테이블에서 '태블릿B'의 카테고리를 '모바일'로 변경하고 가격을 10만 원 인상시키시오.

```sql
UPDATE 상품
SET 카테고리 = '모바일', 가격 = 가격 + 10
WHERE 상품명 = '태블릿B';
```

---

# 연습문제

## Part 1 - SQL의 개념

<div class="quiz-number">문제 1</div><strong>다음 중 DML(데이터 조작어) 명령어를 모두 쓰시오.</strong>

{% capture code_block1 %}
<div style="margin: 15px 0; line-height: 1.8;">
REVOKE, INSERT, DROP, UPDATE, CREATE, DELETE, ALTER, SELECT, ROLLBACK
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz1_sql_concept"
   code_html=code_block1
   answer="SELECT, INSERT, DELETE, UPDATE|INSERT, DELETE, UPDATE, SELECT"
   tags="SQL, DML"
%}

---

<div class="quiz-number">문제 2</div><strong>데이터의 보안, 무결성, 회복, 병행 제어 등을 정의하며 GRANT, REVOKE, COMMIT 등의 명령어를 포함하는 SQL의 종류를 쓰시오.</strong>

{% include quiz-text.html
   id="quiz2_sql_concept"
   answer="DCL|데이터 제어어"
   tags="SQL, DCL"
%}

---

<div class="quiz-number">문제 3</div><strong>다음 설명에서 괄호 ①, ②에 들어갈 알맞은 DDL 명령어를 &lt;보기&gt;에서 찾아 쓰시오.</strong>

{% capture code_block3 %}
<div style="margin: 15px 0; line-height: 1.8;">
• ( ① ) : SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 삭제한다.<br>
• ( ② ) : TABLE에 대한 정의를 변경하는 데 사용한다.<br><br>
<strong>&lt;보기&gt;</strong><br>
CREATE &nbsp; ALTER &nbsp; INSERT &nbsp; DELETE &nbsp; DROP &nbsp; SELECT
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_sql_concept"
   code_html=code_block3
   answer="DROP, ALTER|DROP,ALTER"
   tags="SQL, DDL"
%}

---

<div class="quiz-number">문제 4</div><strong>데이터베이스 구조를 정의하거나 변경 또는 삭제하기 위해 사용되며, CREATE, ALTER, DROP 등의 명령어를 포함하는 SQL의 종류를 쓰시오.</strong>

{% include quiz-text.html
   id="quiz4_sql_concept"
   answer="DDL|데이터 정의어"
   tags="SQL, DDL"
%}

---

<div class="quiz-number">문제 5</div><strong>트랜잭션이 성공적으로 완료된 후, 수행 결과를 실제 물리적 디스크에 저장하고 작업이 정상 완료되었음을 알려주는 SQL 명령어를 쓰시오.</strong>

{% include quiz-text.html
   id="quiz5_sql_concept"
   answer="COMMIT"
   tags="SQL, DCL"
%}

---

<div class="quiz-number">문제 6</div><strong>데이터베이스 관리자가 사용자에게 부여했던 사용 권한을 취소할 때 사용하는 SQL 명령어를 쓰시오.</strong>

{% include quiz-text.html
   id="quiz6_sql_concept"
   answer="REVOKE"
   tags="SQL, DCL"
%}

---

## Part 2 - DDL

<div class="quiz-number">문제 7</div><strong>다음은 &lt;product&gt; 테이블에서 고유한 특성을 갖는 'prd_idx'라는 이름의 인덱스를 정의하며, 'prd_id' 속성에 대해 오름차순으로 정렬하는 SQL문이다. 괄호에 들어갈 알맞은 명령어를 쓰시오.</strong>

{% capture code_block7 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE (     ) INDEX prd_idx ON product(prd_id ASC);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz7_ddl"
   code_html=code_block7
   answer="UNIQUE"
   tags="DDL, INDEX"
%}

---

<div class="quiz-number">문제 8</div><strong>다음은 뷰(View)를 생성하는 SQL문이다. 이를 올바르게 설명한 것을 &lt;보기&gt;에서 고르시오.</strong>

{% capture code_block8 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE VIEW vi_manager
AS
SELECT * FROM STAFF WHERE ROLE LIKE '%팀장%';</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;보기&gt;</strong><br>
ㄱ. STAFF 테이블에서 ROLE이 '팀장'을 포함하는 레코드로 vi_manager 뷰를 생성한다.<br>
ㄴ. STAFF 테이블에서 ROLE이 '개발팀장'인 레코드는 vi_manager 뷰에 포함되지 않는다.<br>
ㄷ. vi_manager 뷰에서 ROLE 외의 다른 속성은 조회할 수 없다.<br>
ㄹ. vi_manager 뷰와 STAFF 테이블의 차수(Degree)는 항상 같다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz8_ddl"
   code_html=code_block8
   answer="ㄱ"
   tags="DDL, VIEW"
%}

---

<div class="quiz-number">문제 9</div><strong>DBA는 &lt;고객&gt; 테이블을 생성한 이후 '이메일' 속성이 누락된 것을 발견하였다. 다음 SQL문의 괄호에 들어갈 알맞은 명령어를 쓰시오.</strong>

{% capture code_block9 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>ALTER TABLE 고객 (      ) 이메일 VARCHAR(50);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_ddl"
   code_html=code_block9
   answer="ADD"
   tags="DDL, ALTER"
%}

---

<div class="quiz-number">문제 10</div><strong>테이블의 구조를 변경하는 DDL(Data Definition Language) 명령어를 쓰시오.</strong>

{% include quiz-text.html
   id="quiz10_ddl"
   answer="ALTER|ALTER TABLE"
   tags="DDL"
%}

---

<div class="quiz-number">문제 11</div><strong>다음은 &lt;수강생&gt; 테이블을 생성하는 SQL문이다. '수강번호'를 기본키, '과목코드'를 외래키로 처리하고자 할 때 괄호에 알맞은 예약어를 쓰시오.</strong>

{% capture code_block11 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE ( ① ) 수강생 (
 학년 INT NOT NULL,
 반 INT NOT NULL,
 성명 CHAR(8),
 수강번호 CHAR(16) UNIQUE,
 과목코드 CHAR(10),
 ( ② ) KEY(수강번호),
 ( ③ ) KEY(과목코드)
     REFERENCES 과목(과목코드));</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_ddl"
   code_html=code_block11
   answer="TABLE, PRIMARY, FOREIGN|TABLE,PRIMARY,FOREIGN"
   tags="DDL, CREATE TABLE"
%}

---

<div class="quiz-number">문제 12</div><strong>다음은 &lt;수강생&gt; 테이블에서 3학년 학생들의 성명, 연락처, 학년을 가져와 &lt;출결현황&gt; 뷰를 생성하는 SQL문이다. 괄호에 적합한 예약어를 쓰시오.</strong>

{% capture code_block12 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>CREATE VIEW 출결현황
(        ) 성명, 연락처, 학년
FROM 수강생
WHERE 학년 = 3;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz12_ddl"
   code_html=code_block12
   answer="AS SELECT"
   tags="DDL, VIEW"
%}

---

<div class="quiz-number">문제 13</div><strong>SQL의 데이터 정의어(DDL) 중 테이블 구조를 제거하는 명령어를 쓰시오.</strong>

{% include quiz-text.html
   id="quiz13_ddl"
   answer="DROP|DROP TABLE"
   tags="DDL"
%}

---

## Part 3 - DCL

<div class="quiz-number">문제 14</div><strong>다음은 사용자 "JUNG"에게 &lt;Order01&gt;의 검색 권한을 부여하기 위한 SQL문이다. &lt;보기&gt;를 참조하여 괄호에 들어갈 알맞은 기호를 쓰시오.</strong>

{% capture code_block14 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>(        ) SELECT ON Order01 TO JUNG;</code></pre>
</div>
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;보기&gt;</strong><br>
ㄱ CREATE &nbsp; ㄴ ALTER &nbsp; ㄷ DROP &nbsp; ㄹ INSERT &nbsp; ㅁ DELETE<br>
ㅂ UPDATE &nbsp; ㅅ GRANT &nbsp; ㅇ REVOKE &nbsp; ㅈ COMMIT &nbsp; ㅊ ROLLBACK
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz14_dcl"
   code_html=code_block14
   answer="ㅅ"
   tags="DCL, GRANT"
%}

---

<div class="quiz-number">문제 15</div><strong>데이터베이스 조작 중 이상이 발생하여 원래 상태로 되돌리고자 할 때 사용하는 DCL 명령어를 쓰시오.</strong>

{% include quiz-text.html
   id="quiz15_dcl"
   answer="ROLLBACK"
   tags="DCL"
%}

---

<div class="quiz-number">문제 16</div><strong>계정 ID가 '박문수'인 사용자에게 &lt;staff&gt; 테이블에 대한 삭제 권한을 부여하고, 해당 삭제 권한을 다른 계정에 부여할 수 있는 권한까지 부여하고자 한다. 괄호에 들어갈 알맞은 명령어를 쓰시오.</strong>

{% capture code_block16 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>GRANT DELETE ON staff TO 박문수 WITH (        ) OPTION;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz16_dcl"
   code_html=code_block16
   answer="GRANT"
   tags="DCL, GRANT"
%}

---

<div class="quiz-number">문제 17</div><strong>장영실에게 부여된 &lt;과목&gt; 테이블에 대한 INSERT와 DELETE 권한을 취소하는 SQL문을 완성하시오. 괄호에 적합한 예약어를 쓰시오.</strong>

{% capture code_block17 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>(        ) INSERT, DELETE ON 과목 FROM 장영실;</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz17_dcl"
   code_html=code_block17
   answer="REVOKE"
   tags="DCL, REVOKE"
%}

---

## Part 4 - DML

<div class="quiz-number">문제 18</div><strong>&lt;Course&gt; 테이블에서 'C_NO'가 'CS2024A'인 과목의 레코드를 삭제하기 위한 SQL문의 괄호에 들어갈 알맞은 명령을 쓰시오.</strong>

{% capture code_block18 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>DELETE FROM Course (        ) C_NO = 'CS2024A';</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz18_dml"
   code_html=code_block18
   answer="WHERE"
   tags="DML, DELETE"
%}

---

<div class="quiz-number">문제 19</div><strong>&lt;Item01&gt;에서 'price' 속성의 값을 1.5배로 증가시키고자 할 때 사용해야 할 SQL문으로 알맞은 것을 &lt;보기&gt;에서 찾아 기호로 쓰시오.</strong>

{% capture code_block19 %}
<div style="margin: 15px 0; line-height: 1.8;">
<strong>&lt;보기&gt;</strong><br>
① ALTER Item01 COLUMN price = price * 1.5;<br>
② ALTER Item01 ADD price = price * 1.5;<br>
③ UPDATE Item01 SET = price = price * 1.5;<br>
④ UPDATE Item01 SET price = price * 1.5;
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz19_dml"
   code_html=code_block19
   answer="④"
   tags="DML, UPDATE"
%}

---

<div class="quiz-number">문제 20</div><strong>다음은 MEMBER(MNO, MNAME, MYEAR) 테이블에 회원번호가 200, 이름이 '이순신', 가입년도가 3인 자료를 삽입하려고 한다. 괄호에 적합한 명령어를 쓰시오.</strong>

{% capture code_block20 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>(        ) INTO MEMBER(MNO, MNAME, MYEAR) VALUES (200, '이순신', 3);</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz20_dml"
   code_html=code_block20
   answer="INSERT"
   tags="DML, INSERT"
%}

---

<div class="quiz-number">문제 21</div><strong>다음은 &lt;과목&gt; 테이블에서 '수강번호'가 'K20240101'인 수강생의 과목명을 '알고리즘'으로 변경하는 SQL문이다. 괄호에 가장 적합한 명령어를 쓰시오.</strong>

{% capture code_block21 %}
<div class="quiz-code" style="margin-bottom: 15px;">
<pre style="background-color: #2d2d2d; color: #f8f8f2; padding: 15px; border-radius: 5px; overflow-x: auto;"><code>UPDATE 과목 (        ) 과목명 = '알고리즘'
WHERE 수강번호 = 'K20240101';</code></pre>
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz21_dml"
   code_html=code_block21
   answer="SET"
   tags="DML, UPDATE"
%}

---

<div class="quiz-number">문제 22</div><strong>DML 중 데이터베이스의 데이터를 변경할 때 사용하는 명령어를 쓰시오.</strong>

{% include quiz-text.html
   id="quiz22_dml"
   answer="UPDATE"
   tags="DML"
%}

---

# 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">SQL의 개념</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>SQL</strong>: 관계형 DB를 위한 표준 언어 (1974년 IBM SEQUEL에서 유래)</li>
<li><strong>DDL</strong>: CREATE, ALTER, DROP (구조 정의·변경·삭제)</li>
<li><strong>DML</strong>: SELECT, INSERT, DELETE, UPDATE (데이터 조작)</li>
<li><strong>DCL</strong>: GRANT, REVOKE, COMMIT, ROLLBACK (권한·트랜잭션 제어)</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">DDL</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>CREATE TABLE</strong>: PRIMARY KEY, FOREIGN KEY, UNIQUE, CHECK 제약 조건</li>
<li><strong>CREATE VIEW</strong>: AS SELECT문 (UNION, ORDER BY 사용 불가)</li>
<li><strong>CREATE INDEX</strong>: UNIQUE, ASC/DESC, CLUSTER</li>
<li><strong>ALTER TABLE</strong>: ADD(추가), ALTER(변경), DROP COLUMN(삭제)</li>
<li><strong>DROP</strong>: CASCADE(연쇄 삭제), RESTRICT(참조 시 취소)</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">DCL</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>GRANT</strong>: 권한 부여 (WITH GRANT OPTION)</li>
<li><strong>REVOKE</strong>: 권한 취소 (GRANT OPTION FOR, CASCADE)</li>
<li><strong>COMMIT</strong>: 변경 내용 확정</li>
<li><strong>ROLLBACK</strong>: 변경 내용 취소, SAVEPOINT로 특정 지점까지 복원 가능</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">DML</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>INSERT INTO ~ VALUES</strong>: 새 튜플 삽입</li>
<li><strong>DELETE FROM ~ WHERE</strong>: 튜플 삭제 (DROP과 달리 구조 유지)</li>
<li><strong>UPDATE ~ SET ~ WHERE</strong>: 튜플 내용 변경</li>
<li><strong>SELECT ~ FROM ~ WHERE</strong>: 튜플 검색</li>
</ul>

</div>

---
