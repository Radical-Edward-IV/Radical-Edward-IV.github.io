---
layout: article
title: 10. 기본 SQL 작성하기
permalink: /notes/kr/info-processing-technician/chapter-10
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기능사 실기 강의 노트, SQL의 개념과 분류, DDL/DML/DCL 명령어 및 데이터 정의와 조작 방법을 다룹니다.
keywords: "정보처리기능사, 실기, SQL, DDL, DML, DCL, 데이터베이스, CREATE, SELECT, INSERT, UPDATE, DELETE"
---

<style>
    /* 색상 활용 규칙
      빨강: 주의, 경고, 위험 (삭제, 제약 등)
      파랑: 핵심 개념, 주요 기능 (SQL 명령어, 키워드 등)
      초록: 안전한 대안, 긍정적 결과 (성공, 완료 등)
      노랑: 코드 요소 (명령어, 속성명 등)
    */
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%EC%A0%95%EB%B3%B4%EC%B2%98%EB%A6%AC%EA%B8%B0%EB%8A%A5%EC%82%AC&reversal=false&textBg=false)

SQL은 관계형 데이터베이스의 표준 질의 언어로, <span class="blue-text">데이터 정의(DDL)</span>, <span class="blue-text">데이터 조작(DML)</span>, <span class="blue-text">데이터 제어(DCL)</span> 기능을 모두 갖추고 있습니다.
각 명령어의 역할과 구문을 정확히 이해하여 데이터베이스를 효과적으로 관리할 수 있어야 합니다!

## 1. SQL의 개념 :star::star:

> 💡 **전문가의 조언**: SQL은 데이터 정의, 조작, 제어 기능을 모두 갖춘 관계형 데이터베이스의 표준 언어입니다. 각 분류(DDL, DML, DCL)의 명령어와 기능을 명확히 구분하여 암기해야 합니다.

### SQL(Structured Query Language)의 개요

SQL은 관계형 데이터베이스를 관리하기 위한 표준 질의 언어입니다.

- **1974년 IBM 연구소**에서 개발한 **SEQUEL**에서 유래
- IBM 외 많은 회사에서 관계형 데이터베이스(RDB)를 지원하는 언어로 채택
- **관계대수**와 **관계해석**을 기초로 한 혼합 데이터 언어
- 질의의 효율성과 가능성뿐만 아니라 <span class="blue-text">데이터 구조의 정의, 데이터 조작, 데이터 제어 기능</span>을 모두 제공

### SQL의 분류

SQL은 사용 용도에 따라 다음과 같이 <span class="blue-text">DDL(데이터 정의어)</span>, <span class="blue-text">DML(데이터 조작어)</span>, <span class="blue-text">DCL(데이터 제어어)</span>로 구분됩니다.

#### DDL(Data Definition Language, 데이터 정의어)

DDL은 SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의하거나 변경 또는 삭제할 때 사용하는 언어입니다.

- <span class="green-text">데이터베이스 관리자</span>나 <span class="green-text">데이터베이스 설계자</span>가 사용

| 명령어 | 기능 |
|--------|------|
| <span class="yellow-code">CREATE</span> | SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 정의한다. |
| <span class="yellow-code">ALTER</span> | TABLE에 대한 정의를 변경하는 데 사용한다. |
| <span class="yellow-code">DROP</span> | SCHEMA, DOMAIN, TABLE, VIEW, INDEX를 삭제한다. |

#### DML(Data Manipulation Language, 데이터 조작어)

DML은 데이터베이스 사용자가 응용 프로그램이나 질의어를 통하여 저장된 데이터를 실질적으로 처리하는 데 사용하는 언어입니다.

- 데이터베이스 사용자와 데이터베이스 관리 시스템 간의 <span class="blue-text">인터페이스를 제공</span>

| 명령어 | 기능 |
|--------|------|
| <span class="yellow-code">SELECT</span> | 테이블에서 조건에 맞는 튜플을 검색한다. |
| <span class="yellow-code">INSERT</span> | 테이블에 새로운 튜플을 삽입한다. |
| <span class="yellow-code">DELETE</span> | 테이블에서 조건에 맞는 튜플을 삭제한다. |
| <span class="yellow-code">UPDATE</span> | 테이블에서 조건에 맞는 튜플의 내용을 변경한다. |

#### DCL(Data Control Language, 데이터 제어어)

DCL은 데이터의 보안, 무결성, 회복, 병행 수행 제어 등을 정의하는 데 사용되는 언어입니다.

- <span class="green-text">데이터베이스 관리자</span>가 데이터 관리를 목적으로 사용

| 명령어 | 기능 |
|--------|------|
| <span class="yellow-code">COMMIT</span> | 명령에 의해 수행된 결과를 실제 물리적 디스크로 저장하고, 데이터베이스 조작 작업이 정상적으로 완료되었음을 관리자에게 알려준다. |
| <span class="yellow-code">ROLLBACK</span> | 데이터베이스 조작 작업이 비정상적으로 종료되었을 때 원래의 상태로 복구한다. |
| <span class="yellow-code">GRANT</span> | 데이터베이스 사용자에게 사용 권한을 부여한다. |
| <span class="yellow-code">REVOKE</span> | 데이터베이스 사용자의 사용 권한을 취소한다. |

## 2. DDL :star::star::star:

> 💡 **전문가의 조언**: DDL 구문을 모두 외울 필요는 없습니다. 각 명령어의 역할을 숙지하고, 구문을 보면 무엇을 의미하는지 이해할 수 있을 정도로 학습하세요.

### DDL(Data Definition Language, 데이터 정의어)의 개념

- DDL은 <span class="blue-text">DB 구조, 데이터 형식, 접근 방식</span> 등 DB를 구축하거나 수정할 목적으로 사용하는 언어
- DDL 번역 결과는 <span class="blue-text">데이터 사전(Data Dictionary)</span>이라는 특별한 파일에 여러 개의 테이블로 저장됨
- DDL에는 CREATE SCHEMA, CREATE DOMAIN, CREATE TABLE, CREATE VIEW, CREATE INDEX, ALTER TABLE, DROP 등이 있음

### CREATE SCHEMA

CREATE SCHEMA는 스키마를 정의하는 명령문입니다.

#### 표기 형식

```sql
CREATE SCHEMA 스키마명 AUTHORIZATION 사용자_id;
```

- 스키마의 식별을 위해 스키마 이름과 소유권자나 허가권자를 정의

#### 예제

*소유권자의 사용자 ID가 '홍길동'인 스키마 '대학교'를 정의하는 SQL문*

```sql
CREATE SCHEMA 대학교 AUTHORIZATION 홍길동;
```

### CREATE DOMAIN

CREATE DOMAIN은 도메인을 정의하는 명령문입니다.

#### 표기 형식

```sql
CREATE DOMAIN 도메인명 [AS] 데이터_타입
    [DEFAULT 기본값]
    [CONSTRAINT 제약조건명 CHECK (범위값)];
```

- **데이터 타입**: SQL에서 지원하는 데이터 타입
- **기본값**: 데이터를 입력하지 않았을 때 자동으로 입력되는 값
- 임의의 속성에서 취할 수 있는 값의 범위가 SQL에서 지원하는 전체 데이터 값의 일부일 때 도메인으로 정의
- 정의된 도메인명은 일반적인 데이터 타입처럼 사용 가능

#### 예제

*'성별'을 '남' 또는 '여'와 같이 정해진 1개의 문자로 표현되는 도메인 SEX를 정의하는 SQL문*

```sql
CREATE DOMAIN SEX CHAR(1)
    DEFAULT '남'
    CONSTRAINT VALID-SEX CHECK(VALUE IN ('남','여'));
```

### SQL에서 지원하는 기본 데이터 타입

| 데이터 타입 | 설명 |
|------------|------|
| <span class="blue-text">정수(Integer)</span> | • INTEGER (4Byte 정수)<br/>• SMALLINT (2Byte 정수) |
| <span class="blue-text">실수(Float)</span> | • FLOAT<br/>• REAL<br/>• DOUBLE PRECISION |
| <span class="blue-text">형식화 숫자</span> | DEC(길이, 소수) - 전체 자리수, 소수부 자리수 지정 |
| <span class="blue-text">고정길이 문자</span> | • CHAR(n)<br/>• CHARACTER(n)<br/>※ n: 문자수 |
| <span class="blue-text">가변길이 문자</span> | • VARCHAR(n)<br/>• CHARACTER VARYING(n)<br/>※ n: 최대 문자수 |
| <span class="blue-text">고정길이 비트열</span> | BIT(n) |
| <span class="blue-text">가변길이 비트열</span> | VARBIT(n) |
| <span class="blue-text">날짜</span> | DATE |
| <span class="blue-text">시간</span> | TIME |

### CREATE TABLE

CREATE TABLE은 테이블을 정의하는 명령문입니다.

#### 표기 형식

```sql
CREATE TABLE 테이블명
(속성명 데이터_타입 [DEFAULT 기본값] [NOT NULL], …
 [, PRIMARY KEY(기본키_속성명, …)]
 [, UNIQUE(대체키_속성명, …)]
 [, FOREIGN KEY(외래키_속성명, …)
     REFERENCES 참조테이블명(기본키_속성명, …)]
 [, CONSTRAINT 제약조건명 [CHECK (조건식) …]]);
```

#### 구성 요소 설명

| 요소 | 설명 |
|------|------|
| **속성 정의** | 기본 테이블에 포함될 모든 속성에 대하여 속성명과 데이터 타입, 기본값, NOT NULL 여부를 지정 |
| <span class="yellow-code">PRIMARY KEY</span> | 기본키로 사용할 속성 또는 속성의 집합을 지정 |
| <span class="yellow-code">UNIQUE</span> | 대체키로 사용할 속성 또는 속성의 집합을 지정<br/>중복된 값을 가질 수 없음 |
| <span class="yellow-code">FOREIGN KEY ~ REFERENCES</span> | 참조할 다른 테이블과 그 테이블을 참조할 때 사용할 외래키 속성을 지정<br/>외래키 지정 시 참조 무결성의 CASCADE 법칙이 적용됨 |
| <span class="yellow-code">CONSTRAINT</span> | 제약 조건의 이름을 지정<br/>이름이 필요 없으면 CHECK절만 사용 |
| <span class="yellow-code">CHECK</span> | 속성 값에 대한 제약 조건을 정의 |

#### 예제

*'이름', '학번', '전공', '성별', '생년월일'로 구성된 '학생' 테이블을 정의하시오.*

```sql
CREATE TABLE 학생
(이름 VARCHAR(15) NOT NULL,
 학번 CHAR(8),
 전공 CHAR(5),
 성별 SEX,
 생년월일 DATE,
 PRIMARY KEY(학번),
 FOREIGN KEY(전공)
   REFERENCES 학과(학과코드),
 CHECK(성별 = '남'));
```

### CREATE VIEW

CREATE VIEW는 뷰(View)를 정의하는 명령문입니다.

#### 표기 형식

```sql
CREATE VIEW 뷰명[(속성명, 속성명, …)]
AS SELECT문;
```

#### 특징

- SELECT문을 서브 쿼리로 사용하여 SELECT문의 결과로서 뷰를 생성
- 서브 쿼리인 SELECT문에는 <span class="red-text">UNION이나 ORDER BY절을 사용할 수 없음</span>
- 속성명을 기술하지 않으면 SELECT문의 속성명이 자동으로 사용됨

#### 예제

*(고객) 테이블에서 '주소'가 '안산시'인 고객들의 '성명'과 '전화번호'를 '안산고객'이라는 뷰로 정의하시오.*

```sql
CREATE VIEW 안산고객(성명, 전화번호)
AS SELECT 성명, 전화번호
FROM 고객
WHERE 주소 = '안산시';
```

### CREATE INDEX

CREATE INDEX는 인덱스를 정의하는 명령문입니다.

#### 표기 형식

```sql
CREATE [UNIQUE] INDEX 인덱스명
ON 테이블명(속성명 [ASC | DESC] [, 속성명 [ASC | DESC]])
[CLUSTER];
```

#### 옵션 설명

| 옵션 | 설명 |
|------|------|
| <span class="yellow-code">UNIQUE</span> | • 사용된 경우: 중복 값이 없는 고유한 특성을 갖는 인덱스 생성<br/>• 생략된 경우: 중복 값을 허용하는 인덱스 생성 |
| <span class="yellow-code">ASC / DESC</span> | • ASC: 오름차순 정렬<br/>• DESC: 내림차순 정렬<br/>• 생략 시: 오름차순으로 정렬 |
| <span class="yellow-code">CLUSTER</span> | 사용하면 인덱스가 클러스터드 인덱스로 설정됨 |

#### 예제

*(고객) 테이블에서 UNIQUE한 특성을 갖는 '고객번호' 속성에 대해 내림차순으로 정렬하여 '고객번호_idx'라는 이름으로 인덱스를 정의하시오.*

```sql
CREATE UNIQUE INDEX 고객번호_idx
ON 고객(고객번호 DESC);
```

### ALTER TABLE

ALTER TABLE은 테이블에 대한 정의를 변경하는 명령문입니다.

#### 표기 형식

```sql
ALTER TABLE 테이블명 ADD 속성명 데이터_타입;
ALTER TABLE 테이블명 ALTER 속성명 데이터_타입;
ALTER TABLE 테이블명 DROP COLUMN 속성명 [CASCADE];
```

#### 명령어 설명

| 명령어 | 기능 |
|--------|------|
| <span class="yellow-code">ADD</span> | 새로운 속성(열)을 추가할 때 사용 |
| <span class="yellow-code">ALTER</span> | 특정 속성의 데이터 타입이나 크기를 변경할 때 사용 |
| <span class="yellow-code">DROP COLUMN</span> | 특정 속성을 삭제할 때 사용 |

### DROP

DROP은 스키마, 도메인, 기본 테이블, 뷰 테이블, 인덱스, 제약 조건 등을 제거하는 명령문입니다.

#### 표기 형식

```sql
DROP SCHEMA 스키마명 [CASCADE | RESTRICT];
DROP DOMAIN 도메인명 [CASCADE | RESTRICT];
DROP TABLE 테이블명 [CASCADE | RESTRICT];
DROP VIEW 뷰명 [CASCADE | RESTRICT];
DROP INDEX 인덱스명 [CASCADE | RESTRICT];
DROP CONSTRAINT 제약조건명;
```

#### 옵션 설명

| 옵션 | 설명 |
|------|------|
| <span class="yellow-code">CASCADE</span> | 제거할 요소를 참조하는 다른 모든 개체를 함께 제거<br/>주 테이블의 데이터 제거 시 각 외래키와 관계를 맺고 있는 모든 데이터를 제거하는 참조 무결성 제약 조건 설정 |
| <span class="yellow-code">RESTRICT</span> | 다른 개체가 제거할 요소를 참조 중일 때는 제거를 취소 |

#### 예제

*(학생) 테이블을 제거하고, (학생) 테이블을 참조하는 모든 데이터를 함께 제거하시오.*

```sql
DROP TABLE 학생 CASCADE;
```

## 3. DCL :star::star:

> 💡 **전문가의 조언**: DCL은 트랜잭션 제어와 권한 관리를 담당합니다. 특히 COMMIT과 ROLLBACK의 차이, 그리고 SAVEPOINT의 활용을 명확히 이해해야 합니다.

### COMMIT

트랜잭션이 성공적으로 끝나면 데이터베이스가 새로운 일관성(Consistency) 상태를 가지기 위해 변경된 모든 내용을 데이터베이스에 반영해야 하는데, 이때 사용하는 명령이 <span class="blue-text">COMMIT</span>입니다.

#### 특징

- <span class="green-text">COMMIT 명령을 실행하지 않아도</span> DML문이 성공적으로 완료되면 자동으로 COMMIT됨
- DML이 실패하면 자동으로 ROLLBACK되도록 <span class="blue-text">Auto Commit 기능</span>을 설정할 수 있음

### ROLLBACK

ROLLBACK은 아직 COMMIT되지 않은 변경된 모든 내용들을 취소하고 데이터베이스를 이전 상태로 되돌리는 명령입니다.

#### 목적

- 트랜잭션 전체가 성공적으로 끝나지 못하면 일부 변경된 내용만 데이터베이스에 반영되는 <span class="red-text">비일관성(Inconsistency) 상태</span>를 가질 수 있음
- 일부만 완료된 트랜잭션은 롤백(Rollback)되어야 함

### SAVEPOINT

SAVEPOINT는 트랜잭션 내에 ROLLBACK 할 위치인 저장점을 지정하는 명령입니다.

#### 특징

- 저장점을 지정할 때는 이름을 부여
- ROLLBACK 시 지정된 저장점까지의 트랜잭션 처리 내용이 취소됨

## 4. DML :star::star::star:

> 💡 **전문가의 조언**: DML은 실제 데이터를 다루는 가장 중요한 명령어입니다. INSERT, SELECT, UPDATE, DELETE의 구문과 사용법을 정확히 숙지해야 합니다.

### DML(Data Manipulation Language, 데이터 조작어)의 개념

DML(데이터 조작어)은 데이터베이스 사용자가 응용 프로그램이나 질의어를 통해 저장된 데이터를 실질적으로 관리하는 데 사용되는 언어입니다.

- 데이터베이스 사용자와 데이터베이스 관리 시스템 간의 <span class="blue-text">인터페이스를 제공</span>

| 명령문 | 기능 |
|--------|------|
| <span class="yellow-code">SELECT</span> | 테이블에서 튜플을 검색한다. |
| <span class="yellow-code">INSERT</span> | 테이블에 새로운 튜플을 삽입한다. |
| <span class="yellow-code">DELETE</span> | 테이블에서 튜플을 삭제한다. |
| <span class="yellow-code">UPDATE</span> | 테이블에서 튜플의 내용을 갱신한다. |

### 삽입문(INSERT INTO~)

삽입문은 기본 테이블에 새로운 튜플을 삽입할 때 사용합니다.

#### 표기 형식

```sql
INSERT INTO 테이블명(속성명1, 속성명2, …)
VALUES (데이터1, 데이터2, …);
```

#### 특징

- 대응하는 속성과 데이터는 <span class="blue-text">개수와 데이터 유형이 일치</span>해야 함
- 기본 테이블의 모든 속성을 사용할 때는 속성명을 생략할 수 있음
- SELECT문을 사용하여 다른 테이블의 검색 결과를 삽입할 수 있음

#### 예제 테이블: (사원)

| 이름 | 부서 | 생일 | 주소 | 기본급 |
|------|------|------|------|--------|
| 홍길동 | 기획 | 04/05/61 | 망원동 | 120 |
| 황진이 | 인터넷 | 01/09/69 | 성산동 | 80 |
| 김선달 | 편집 | 07/21/75 | 연희동 | 90 |
| 성춘향 | 편집 | 10/22/73 | 망원동 | 100 |
| 장길산 | 편집 | 03/11/67 | 상암동 | 120 |
| 일지매 | 기획 | 04/12/79 | 합정동 | 110 |
| 강호동 | 인터넷 | 12/11/80 | 망원동 | 90 |

#### 예제 1

*(사원) 테이블에 (이름 = 홍승현, 부서 = 인터넷)을 삽입하시오.*

```sql
INSERT INTO 사원(이름, 부서) VALUES ('홍승현', '인터넷');
```

#### 예제 2

*(사원) 테이블에 (장보고, 기획, 05/03/73, 홍제동, 90)을 삽입하시오.*

```sql
INSERT INTO 사원 VALUES ('장보고', '기획', '05/03/73', '홍제동', 90);
```

#### 예제 3

*(사원) 테이블에 있는 편집부의 모든 튜플을 편집부원(이름, 생일, 주소, 기본급) 테이블에 삽입하시오.*

```sql
INSERT INTO 편집부원(이름, 생일, 주소, 기본급)
SELECT 이름, 생일, 주소, 기본급
FROM 사원
WHERE 부서 = '편집';
```

### 삭제문(DELETE FROM~)

삭제문은 기본 테이블에 있는 튜플들 중에서 특정 튜플(행)을 삭제할 때 사용합니다.

#### 표기 형식

```sql
DELETE
FROM 테이블명
[WHERE 조건];
```

#### 특징

- 모든 레코드를 삭제할 때는 WHERE절을 생략
- 모든 레코드를 삭제하더라도 <span class="green-text">테이블 구조는 남아 있음</span>
- 디스크에서 테이블을 완전히 제거하는 <span class="red-text">DROP과는 다름</span>

#### 예제 1

*(사원) 테이블에서 "임꺽정"에 대한 튜플을 삭제하시오.*

```sql
DELETE
FROM 사원
WHERE 이름 = '임꺽정';
```

#### 예제 2

*(사원) 테이블에서 "인터넷" 부서에 대한 모든 튜플을 삭제하시오.*

```sql
DELETE
FROM 사원
WHERE 부서 = '인터넷';
```

#### 예제 3

*(사원) 테이블의 모든 레코드를 삭제하시오.*

```sql
DELETE
FROM 사원;
```

### 갱신문(UPDATE~ SET~)

갱신문은 기본 테이블에 있는 튜플들 중에서 특정 튜플의 내용을 변경할 때 사용합니다.

#### 표기 형식

```sql
UPDATE 테이블명
SET 속성명 = 데이터, 속성명 = 데이터, ...
[WHERE 조건];
```

#### 예제 1

*(사원) 테이블에서 "홍길동"의 '주소'를 "수색동"으로 수정하시오.*

```sql
UPDATE 사원
SET 주소 = '수색동'
WHERE 이름 = '홍길동';
```

#### 예제 2

*(사원) 테이블에서 "황진이"의 '부서'를 '기획부'로 변경하고 '기본급'을 5만 원 인상시키시오.*

```sql
UPDATE 사원
SET 부서 = '기획', 기본급 = 기본급 + 5
WHERE 이름 = '황진이';
```

---

## 핵심 요약 정리

### SQL의 3가지 분류

| 분류 | 명령어 | 사용자 |
|------|--------|--------|
| <span class="blue-text">DDL</span><br/>(데이터 정의어) | CREATE, ALTER, DROP | DB 관리자, DB 설계자 |
| <span class="blue-text">DML</span><br/>(데이터 조작어) | SELECT, INSERT, DELETE, UPDATE | DB 사용자 |
| <span class="blue-text">DCL</span><br/>(데이터 제어어) | COMMIT, ROLLBACK, GRANT, REVOKE | DB 관리자 |

### DDL 주요 명령어

```
CREATE: 생성
    ↓
ALTER: 변경
    ↓
DROP: 삭제
```

### DML 주요 명령어

```
INSERT: 삽입
    ↓
SELECT: 검색
    ↓
UPDATE: 갱신
    ↓
DELETE: 삭제
```

### DROP vs DELETE 비교

| 구분 | DROP | DELETE |
|------|------|--------|
| **분류** | DDL | DML |
| **기능** | 테이블 구조 자체를 삭제 | 테이블의 데이터만 삭제 |
| **결과** | 테이블이 완전히 제거됨 | 테이블 구조는 유지됨 |
| **ROLLBACK** | 불가능 | 가능 (COMMIT 전) |

> 💡 **전문가의 조언**: SQL은 데이터베이스 관리의 핵심 도구입니다. DDL로 구조를 정의하고, DML로 데이터를 조작하며, DCL로 보안과 무결성을 제어하는 전체 흐름을 이해하는 것이 중요합니다!

## 5. DML - SELECT :star::star::star:

> 💡 **전문가의 조언**: SELECT문은 실무에서 가장 많이 사용되는 SQL 명령입니다. 명령어의 위치와 순서 및 옵션을 명확히 구분 지어 암기해 두는 것이 중요합니다.

SELECT문은 테이블을 구성하는 튜플(행)들 중에서 전체 또는 조건을 만족하는 튜플(행)을 검색하여 주기억장치 상에 임시 테이블로 구성하는 명령문입니다.

### 일반 형식

```sql
SELECT PREDICATE [테이블명.속성명1, 테이블명.속성명2, ...]
FROM 테이블명, 테이블명, ...
[WHERE 조건]
[GROUP BY 속성명1, 속성명2, ...]
[HAVING 조건]
[ORDER BY 속성명 [ASC | DESC]];
```

#### SELECT문의 실행 순서

<span class="blue-text">SELECT문의 실행 순서는 FROM → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY 순입니다.</span>

#### SELECT절

- **속성명**: 검색하여 보여줄 속성(열) 또는 속성을 이용한 수식을 지정한다.
  - 기본 테이블을 구성하는 모든 속성을 지정할 때는 `*`를 기술한다.
  - 두 개 이상의 테이블을 이용할 경우 테이블명과 함께 `테이블명.속성명`으로 기술한다.
- **PREDICATE**: 불러올 튜플 수를 제한할 명령어를 기술한다.

| PREDICATE 옵션 | 설명 |
|----------------|------|
| <span class="yellow-code">ALL</span> | 모든 튜플을 검색할 때 지정하는 것으로, 주로 생략된다. |
| <span class="yellow-code">DISTINCT</span> | 중복된 튜플이 있으면 그 중 첫 번째 튜플만 검색된다. |
| <span class="yellow-code">DISTINCTROW</span> | 중복된 튜플을 제거하되 한 개의 속성이 아닌 튜플 전체를 대상으로 한다. |

#### FROM절

- 질의에 의해 검색될 데이터들을 포함하는 테이블명을 기술한다.

#### WHERE절

- 검색할 조건을 기술한다.

#### GROUP BY절

- 특정 속성을 기준으로 그룹화하여 검색할 때 그룹화할 속성을 지정한다.
- 일반적으로 GROUP BY절은 그룹 함수와 함께 사용된다.

#### HAVING절

- GROUP BY와 함께 사용되며, 그룹에 대한 조건을 지정한다.

#### ORDER BY절

- 특정 속성을 기준으로 정렬하여 검색할 때 사용한다.
- 속성명: 기준이 되는 속성명을 기술한다.
- `[ASC|DESC]`: 정렬 방식으로서 `ASC`는 오름차순, `DESC`는 내림차순이다.
  단, 생략하면 오름차순으로 지정된다.

### 그룹 함수(집단 함수)

집합으로 묶은 값을 요약하거나 집계하는 함수로, 그룹 함수에는 <span class="yellow-code">COUNT</span>, <span class="yellow-code">MAX</span>, <span class="yellow-code">MIN</span>, <span class="yellow-code">SUM</span>, <span class="yellow-code">AVG</span> 등이 있습니다.

### 조건 연산자 / 연산자 우선순위 / 주요 함수

#### 조건 연산자

**비교 연산자**

| 연산자 | = | > | < | >= | <= |
|--------|---|---|---|----|-----|
| 의미 | 같다 | 크다 | 작다 | 크거나 같다 | 작거나 같다 |

**논리 연산자: NOT, AND, OR**

| 연산자 | 의미 |
|--------|------|
| <span class="yellow-code">NOT</span> | 조건을 만족하지 않을 경우에만 데이터를 추출한다. |
| <span class="yellow-code">AND</span> | 두 조건을 모두 만족할 경우에만 데이터를 추출한다. |
| <span class="yellow-code">OR</span> | 두 조건식 중 하나라도 만족할 경우 데이터를 추출한다. |

**LIKE 연산자**

가장 일반적으로 사용되는 문자열에 대한 연산으로, 대표 문자를 이용해 지정된 속성의 문자 패턴을 검색하기 위해 사용됩니다.

| 대표 문자 | 의미 |
|-----------|------|
| <span class="yellow-code">%</span> | 모든 문자를 대표한다. |
| <span class="yellow-code">_</span> | 문자 하나를 대표한다. |
| <span class="yellow-code">#</span> | 숫자 하나를 대표한다. |

#### 연산자 우선순위

| 종류 | 연산자 | 우선순위 |
|------|---------|----------|
| 산술 연산자 | +, -, *, / | 왼쪽에서 오른쪽으로 계산. 우선순위 높다. |
| 비교 연산자 | =, <>, <, <=, >, >= | 왼쪽에서 오른쪽으로 계산. 우선순위 낮다. |
| 논리 연산자 | NOT, AND, OR | NOT → AND → OR 순으로 우선순위가 낮아진다. |

> <span class="blue-text">산술 > 관계 > 논리 연산자 순서로 우선순위가 정해진다.</span>

#### 주요 함수

| 함수 | 설명 |
|------|------|
| <span class="yellow-code">NOW()</span> | 현재 날짜와 시간을 표시한다. |
| <span class="yellow-code">DATE()</span> | 현재 날짜를 표시한다. |
| <span class="yellow-code">LEFT(문자열, 자릿수)</span> | 문자열의 왼쪽에서 주어진 자릿수만큼 추출한다. |
| <span class="yellow-code">MID(문자열, 시작값, 자릿수)</span> | 문자열의 시작 위치에서 주어진 자릿수만큼 추출한다. |
| <span class="yellow-code">RIGHT(문자열, 자릿수)</span> | 문자열의 오른쪽에서 주어진 자릿수만큼 추출한다. |
| <span class="yellow-code">TRIM(문자열)</span> | 문자열의 좌우 공백을 제거한다. |
| <span class="yellow-code">LEN(문자열)</span> | 문자열의 길이를 반환한다. |
| <span class="yellow-code">UPPER(문자열)</span> | 문자열을 모두 대문자로 변환한다. |
| <span class="yellow-code">LOWER(문자열)</span> | 문자열을 모두 소문자로 변환한다. |
| <span class="yellow-code">AVG(필드명)</span> | 필드의 평균을 구한다. |
| <span class="yellow-code">SUM(필드명)</span> | 필드의 합계를 구한다. |
| <span class="yellow-code">COUNT(필드명)</span> | 레코드 수를 구한다. |
| <span class="yellow-code">MIN(필드명)</span> | 필드에서 최소값을 구한다. |
| <span class="yellow-code">MAX(필드명)</span> | 필드에서 최대값을 구한다. |

### 기본 검색

SELECT절에 원하는 속성을 지정하여 검색합니다.

#### 예제 테이블: (사원)

| 이름 | 부서 | 생일 | 주소 | 기본급 |
|------|------|------|------|--------|
| 홍길동 | 기획 | 04/05/61 | 망원동 | 120 |
| 임꺽정 | 인터넷 | 01/09/69 | 서교동 | 80 |
| 황진이 | 편집 | 07/21/75 | 합정동 | 100 |
| 김선달 | 기획 | 02/20/64 | 대흥동 | 110 |
| 성춘향 | 편집 | 07/22/63 | 당인동 | 100 |
| 장길산 | 편집 | 03/11/67 | 상암동 | 120 |
| 일지매 | 기획 | 04/29/78 | 연남동 | 110 |
| 강감찬 | 인터넷 | 12/11/80 | 망원동 | 90 |

#### 예제 테이블: (여가활동)

| 이름 | 취미 | 경력 |
|------|------|------|
| 김선달 | 당구 | 10 |
| 성춘향 | 나이트댄스 | 5 |
| 일지매 | 태권도 | 15 |
| 임꺽정 | 씨름 | 8 |

#### 예제 1

*(사원) 테이블의 모든 튜플을 검색하시오.*

```sql
SELECT * FROM 사원;
```

#### 예제 2

*(사원) 테이블에서 주소만 검색하되 같은 주소는 한 번만 출력하시오.*

```sql
SELECT DISTINCT 주소 FROM 사원;
```

**결과**: 대흥동, 망원동, 상암동, 서교동, 연남동, 합정동, 당인동

#### 예제 3

*(사원) 테이블에서 '기본급'에 10을 더한 형태로 출력하시오.*

```sql
SELECT 부서 AS 부서2, 이름 AS 이름, 기본급+10 AS 기본급2 FROM 사원;
```

### 조건 지정 검색

WHERE절에 조건을 지정하여 조건에 만족하는 튜플을 검색합니다.

#### 예제 1

*(사원) 테이블에서 '기획' 부서에 근무하는 사원을 검색하시오.*

```sql
SELECT * FROM 사원 WHERE 부서='기획';
```

#### 예제 2

*(사원) 테이블에서 '기획' 부서에 근무하면서 '기본급'이 110 이상인 사원을 검색하시오.*

```sql
SELECT * FROM 사원 WHERE 부서='기획' AND 기본급>=110;
```

#### 예제 3

*(사원) 테이블에서 '기획' 부서 또는 '인터넷' 부서에 근무하는 사원을 검색하시오.*

```sql
SELECT * FROM 사원 WHERE 부서='기획' OR 부서='인터넷';
```

#### 예제 4

*'김'으로 시작하는 이름을 검색하시오.*

```sql
SELECT * FROM 사원 WHERE 이름 LIKE '김%';
```

#### 예제 5

*생일이 '01/01/69' ~ '12/31/73' 사이인 튜플을 검색하시오.*

```sql
SELECT * FROM 사원 WHERE 생일 BETWEEN #01/01/69# AND #12/31/73#;
```

#### 예제 6

*주소가 NULL인 튜플을 검색하시오.*

```sql
SELECT * FROM 사원 WHERE 주소 IS NULL;
```

### 정렬 검색

ORDER BY절에 특정 속성을 지정하여 정렬합니다.

#### 예제 1

*(사원) 테이블에서 '주소'를 기준으로 내림차순 정렬시켜 상위 2개의 튜플만 검색하시오.*

```sql
SELECT TOP 2 * FROM 사원 ORDER BY 주소 DESC;
```

#### 예제 2

*(사원) 테이블에서 '부서'를 기준으로 오름차순 정렬하고, 같은 '부서'는 '이름'을 기준으로 내림차순 정렬하시오.*

```sql
SELECT * FROM 사원 ORDER BY 부서 ASC, 이름 DESC;
```

### 그룹 지정 검색

GROUP BY절에 지정한 속성을 기준으로 그룹화합니다.

#### 예제 1

*(사원) 테이블에서 '부서'별 '기본급'의 평균을 구하시오.*

```sql
SELECT 부서, AVG(기본급) AS 평균 FROM 사원 GROUP BY 부서;
```

#### 예제 2

*(사원) 테이블에서 '부서'별 튜플의 개수를 검색하시오.*

```sql
SELECT 부서, COUNT(*) AS 사원수 FROM 사원 GROUP BY 부서;
```

#### 예제 3

*(사원) 테이블에서 '기본급'이 100 이상인 사원에 대하여 '부서'별 튜플 개수를 구하되, 튜플 개수가 2 이상인 '부서'만 검색하시오.*

```sql
SELECT 부서, COUNT(*) AS 사원수
FROM 사원
WHERE 기본급>=100
GROUP BY 부서
HAVING COUNT(*)>=2;
```

### 하위 질의(Subquery)

하위 질의는 SELECT문 안에 있는 SELECT문입니다.

#### 예제 1

*(여가활동) 테이블에서 '취미'가 '나이트댄스'인 사원의 '이름'과 '주소'를 (사원) 테이블에서 검색하시오.*

```sql
SELECT 이름, 주소
FROM 사원
WHERE 이름=(SELECT 이름 FROM 여가활동 WHERE 취미='나이트댄스');
```

#### 예제 2

*(여가활동) 테이블에 없는 사원의 정보를 (사원) 테이블에서 검색하시오.*

```sql
SELECT *
FROM 사원
WHERE 이름 NOT IN (SELECT 이름 FROM 여가활동);
```

### 통합(UNION) 질의

두 SELECT문의 결과를 통합합니다.

#### 예제 테이블: (사원)

| 사원 | 직급 |
|------|------|
| 김형석 | 대리 |
| 홍영섭 | 과장 |
| 류기선 | 부장 |
| 김현진 | 이사 |

#### 예제 테이블: (직원)

| 사원 | 직급 |
|------|------|
| 신원철 | 대리 |
| 이상윤 | 대리 |
| 홍영섭 | 과장 |
| 류기선 | 부장 |

#### 예제

*(사원) 테이블과 (직원) 테이블을 통합하는 SQL문을 작성하시오.*

```sql
SELECT * FROM 사원
UNION
SELECT * FROM 직원;
```

**결과**: 김현진, 김형석, 류기선, 신원철, 이상윤, 홍영섭

### 집합 연산자의 종류

| 집합 연산자 | 설명 | 집합 종류 |
|-------------|------|-----------|
| <span class="yellow-code">UNION</span> | 두 SELECT문의 조회 결과를 통합하여 모두 출력한다. 중복된 행은 한 번만 출력한다. | 합집합 |
| <span class="yellow-code">UNION ALL</span> | 중복된 행을 그대로 출력한다. | 합집합 |
| <span class="yellow-code">INTERSECT</span> | 두 SELECT문의 공통 행만 출력한다. | 교집합 |
| <span class="yellow-code">EXCEPT</span> | 첫 번째 SELECT문의 결과에서 두 번째 SELECT문의 결과를 제외한다. | 차집합 |

## 6. SQL - JOIN :star::star::star:

> 💡 **전문가의 조언**: JOIN은 2개 이상의 테이블을 연결하여 데이터를 검색하는 매우 중요한 기능입니다. INNER JOIN과 OUTER JOIN의 차이를 명확히 이해해야 합니다.

JOIN(조인)은 2개 이상의 테이블에 대해 연관된 튜플들을 결합하여 하나의 새로운 테이블을 반환합니다.

JOIN은 <span class="blue-text">INNER JOIN</span>과 <span class="blue-text">OUTER JOIN</span>으로 구분됩니다.

### INNER JOIN

<span class="blue-text">가장 일반적인 조인</span>으로, 공통 속성을 기준으로 일치하는 튜플만 반환합니다.

#### WHERE절을 이용한 형식

```sql
SELECT 테이블명1.속성명, 테이블명2.속성명
FROM 테이블명1, 테이블명2
WHERE 테이블명1.속성명 = 테이블명2.속성명;
```

#### ON절 이용 형식

```sql
SELECT 테이블명1.속성명, 테이블명2.속성명
FROM 테이블명1 INNER JOIN 테이블명2
ON 테이블명1.속성명 = 테이블명2.속성명;
```

#### NATURAL JOIN 형식

```sql
SELECT 테이블명1.속성명, 테이블명2.속성명
FROM 테이블명1 NATURAL JOIN 테이블명2;
```

#### USING절 이용 형식

```sql
SELECT 테이블명1.속성명, 테이블명2.속성명
FROM 테이블명1 JOIN 테이블명2 USING(속성명);
```

### OUTER JOIN

릴레이션에서 JOIN 조건에 만족하지 않는 튜플도 결과에 포함시킵니다.

- <span class="blue-text">LEFT OUTER JOIN</span>: 왼쪽 릴레이션의 모든 튜플을 포함
- <span class="blue-text">RIGHT OUTER JOIN</span>: 오른쪽 릴레이션의 모든 튜플을 포함

#### LEFT OUTER JOIN

```sql
SELECT 테이블1.속성명, 테이블2.속성명
FROM 테이블1 LEFT OUTER JOIN 테이블2
ON 테이블1.속성명 = 테이블2.속성명;
```

#### RIGHT OUTER JOIN

```sql
SELECT 테이블1.속성명, 테이블2.속성명
FROM 테이블1 RIGHT OUTER JOIN 테이블2
ON 테이블1.속성명 = 테이블2.속성명;
```

---

## 최종 요약 정리

### SQL 명령어 전체 구조

```
DDL (데이터 정의어)
├─ CREATE: 생성
├─ ALTER: 변경
└─ DROP: 삭제

DML (데이터 조작어)
├─ SELECT: 검색
├─ INSERT: 삽입
├─ UPDATE: 갱신
└─ DELETE: 삭제

DCL (데이터 제어어)
├─ COMMIT: 확정
├─ ROLLBACK: 취소
├─ GRANT: 권한 부여
└─ REVOKE: 권한 취소
```

### SELECT문 실행 순서 (중요!)

```
FROM → WHERE → GROUP BY → HAVING → SELECT → DISTINCT → ORDER BY
```

### JOIN의 종류

| JOIN 종류 | 설명 |
|-----------|------|
| <span class="blue-text">INNER JOIN</span> | 두 테이블에서 일치하는 행만 반환 |
| <span class="blue-text">LEFT OUTER JOIN</span> | 왼쪽 테이블의 모든 행 + 일치하는 오른쪽 테이블 행 |
| <span class="blue-text">RIGHT OUTER JOIN</span> | 오른쪽 테이블의 모든 행 + 일치하는 왼쪽 테이블 행 |

> 💡 **전문가의 조언**: SQL 문법을 완벽하게 외우는 것보다는 각 명령어의 역할과 구조를 이해하고, 실제 문제를 풀어보며 익숙해지는 것이 중요합니다!
