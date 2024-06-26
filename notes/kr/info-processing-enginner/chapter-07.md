---
layout: article
title: 7. SQL 응용
permalink: /notes/kr/info-processing-engineer/chapter-07
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기사 필기와 실기에 대한 요약, 특히 SQL 응용 부분에 대한 자세한 설명입니다.
keywords: "정보처리기사, 요약, SQL, ORACLE, 트랜잭션, ACID, 데이터베이스 고립화, DDL, DML, DCL, 프로시저, 옵티마이저"
---

`정보처리기사`{:.info} `정보처리기사요약`{:.info} `SQL`{:.info} `ORACLE`{:.info} `트랜잭션`{:.info} `ACID`{:.info} `데이터베이스고립화`{:.info} `DDL`{:.info} `DML`{:.info} `DCL`{:.info} `프로시저`{:.info} `옵티마이저`{:.info}

## 데이터베이스 기본
### 트랜잭션 :star::star::star:

* **트랜잭션**

    - **개념:** 인가받지 않은 사용자로부터 <u>데이터</u>를 <u>보장</u>하기 위해 DBMS가 가져야하는 <u>특성</u>, <u>작업의 기본 단위</u>

    - **특징:** 원자성(**A**tomicity), 일관성(**C**onsistency), 격리성(**I**solation), 영속성(**D**urability) `ACID`{:.success}

    - **상태 변화:** **활**동 상태, **부**분 완료 상태, **완**료 상태, **실**패 상태, **철**회 상태 `활부완실철`{:.success}   
    <img src="/notes/assets/transaction-status.png" width="500px" title="Transaction Status"/>

    - **제어:** **커**밋, **롤**백, **체**크포인트 `커롤체`{:.success}

    - **병행 제어**

		+ **개념:** <u>다수 사용자 환경</u>에서 <u>여러 트랜잭션</u>을 <u>수행</u>, 데이터베이스 <u>일관성 유지</u>를 위한 상호 작용 <u>제어 기법</u>.

		+ **미보장 시 문제점:** **갱**신 손실, **현**황 파악오류, **모**순성, **연**쇄복귀 `갱현모연`{:.success}

		+ **기법의 종류:** **로**킹, **낙**관적 검증, **타**임 스탬프 순서, **다**중버전 동시성 제어 `로 낙타다`{:.success}

    - **데이터베이스 고립화 수준(격리성 주요 기법)**

		+ **개념:** 다른 트랜잭션이 현재의 <u>데이터</u>에 대한 무결성을 해치지 않기 위해 <u>잠금을 설정하는 정도</u>이다.

		+ **종류:** Read Uncommitted, Read Committed, Repeatable Read, Serializable Read

    - **회복 기법**

		+ **개념:** <u>트랜잭션</u>을 수행하는 <u>도중 장애</u>로 인해 손상된 데이터베이스를 손상되기 이전의 <u>정상</u>적인 <u>상태</u>로 <u>복구시키는 작업</u>이다.

		+ **종류:** **로**그 기반 회복 기법(지연 갱신 회복 기법, 즉각 갱신 회복 기법), **체**크 포인트 회복 기법, **그**림자 페이징 회복 기법 `회로 체크`{:.success} *( **회**복 기법: **로**그, **체**크 포인트, **그**림자 )*

* **DDL (데이터 정의어)**

	- **대상:** **도**메인, **스**키마, **테**이블, **뷰**, **인**덱스 `도스테뷰인`{:.success}

		+ **스키마 3계층:** 외부 스키마, 개념 스키마, 내부 스키마

		+ **테이블 관련 용어:** 튜플/행, 애트리뷰트/열, 식별자, 카디널리티, 차수, 도메인

		+ **뷰의 특징:** 논리적 데이터 독립성 제공, 데이터 조작 연산 간소화, 보안 기능 제공, 뷰 변경 불가

		+ **인덱스:** 검색 연산의 최적화를 위해 데이터베이스 내 <u>값에 대한 주소 정보로 구성된 데이터 구조</u>이다.<br>

			👉 **종류:** **순**서 인덱스, **해**시 인덱스, **비**트맵 인덱스, **함**수기반 인덱스, **단**일 인덱스, **결**합 인덱스, **클**러스터드 인덱스 `순해비함 단결클`{:.success}

    - **명령어:** CREATE, ALTER, DROP, TRUNCATE

		+ **테이블 관련 DDL**

		``` sql
		CREATE TABLE emp
		(
			empno NUMBER(10) PRIMARY KEY
			,ename VARCHAR2(10) UNIQUE
			,egender CHAR(1) CHECK (egender = 'M' OR egender = 'F')
			,job VARCHAR2(20) NOT NULL
			,hiredate DATE DEFAULT SYSDATE
			,deptno VARCHAR2(20) FOREIGN KEY REFERENCES dept(deptno)
		);
		
		ALTER TABLE emp ADD tel VARCHAR2(15) UNIQUE;
		
		ALTER TABLE emp MODIFY tel NUMBER(15) NOT NULL;
		
		ALTER TABLE emp DROP tel;
		
		DROP TABLE emp [CASCADE | RESTRICT];
		
		TRUNCATE TABLE emp;
		```

		+ **뷰 관련 DDL**

		``` sql
		CREATE VIEW view_emp AS
		SELECT empno, ename
		FROM emp
		WHERE egender = 'F';
		-- UNION, ORDER BY 절 사용 불가
		
		-- 뷰 교체 명령어
		CREATE OR REPLACE VIEW view_emp AS
		조회쿼리;
		
		DROP VIEW view_emp;
		```
		+ **인덱스 관련 DDL**
		
		``` sql
		CREATE INDEX emp_idx ON emp(empno);
		
		ALTER INDEX emp_idx ON emp(empno);
		
		DROP INDEX emp_idx;
		```

* **DML**

    - **명령어:** SELECT, INSERT, UPDATE, DELETE

		+ **SELECT 명령어**<br>

			👉 **조인:** Inner Join, Outer Join(Left Outer Join, Right Outer Join, Full Outer Join), Cross Join, Self Join   

			👉 **집합 연산자:** UNION, UNION ALL, INTERSECTION, MINUS

			``` sql
			SELECT [ALL | DISTINCT] 속성명1, 속성명2 ...
			FROM 테이블명1, 테이블명2...
			-- BETWEEN 값1 AND 값2
			-- IN(값1, 값2, ...)
			-- NOT IN(값1, ...)
			-- LIKE 패턴
			-- IS NULL | IS NOT NULL
			-- AND, OR, NOT, !
			[WHERE 조건]
			[GROUP BY 속성명1, ...]
			[HAVING 그룹조건]
			[ORDER BY 속성 [ASC | DESC]];
			```

		+ **INSERT 명령어:** `INSERT INTO 테이블명(속성명1, ...) VALUES (데이터1, ...);`

		+ **UPDATE 명령어:** `UPDATE 테이블명 SET 속성명 = 데이터, ... WHERE 조건;`

		+ **DELETE 명령어:** `DELETE FROM 테이블명 WHERE 조건;`

* **DCL**

    - **명령어:** GRANT, REVOKE

		+ **GRANT 명령어:** `GRANT 권한 ON 테이블 TO 사용자`

		+ **REVOKE 명령어:** `REVOKE 권한 ON 테이블 FROM 사용자`

## 응용 SQL 작성하기
### 집계성 SQL 작성 :star::star::star:

* **데이터 분석 함수**

    - **개념:** 총합, 평균 등의 <u>데이터 분석</u>을 위한 <u>다중 행 함수</u>이다.

    - **종류:** 집계 함수(전체 행), 그룹 함수(소그룹), 윈도 함수(온라인 분석)

* **집계 함수**

    - **종류:** COUNT, SUM, AVG, MAX, MIN, STDDEV, VARIAN

* **그룹 함수**

    - **종류:** ROLLUP, CUBE, GROUPING SETS

* **윈도 함수**

    - **순위 함수:** RANK, DENSE_RANKE, ROW_NUMBER

## 절차형 SQL 활용하기
### 절차형 SQL :star:

+ **개념:** SQL 언어에서도 <u>절차 지향적인 프로그램</u>이 <u>가능</u>하도록 하는 <u>트랜잭션 언어</u>이다.

+ **종류:** 프로시저, 사용자 정의 함수, 트리거

### 프로시저 :star::star:

* **개념:** 일련의 쿼리들을 마치 <u>하나의 함수처럼 실행</u>하기 위한 <u>쿼리의 집합</u>이다.

* **구성:** 선언부(**DE**CLARE), 시작/종료부(**BE**GIN/END), 제어부(**CON**TROLL), **S**QL, 예외부(**E**XCEPTION), 실행부(**T**RANSACTION) `디비컨 SET`{:.success}

```sql
CREATE [OR REPLACE] PROEDURE 프로시저_명
(파라미터_명, [IN | OUT | INOUT] 데이터_타입, ...)
IS
	변수 선언
BEGIN
	명령어;
[COMMIT | ROLLBACK]
END;
```

### 사용자 정의 함수 :star:

* **개념:** 일련의 SQL 처리를 수행하고, <u>수행 결과</u>를 <u>단일 값</u>으로 <u>반환</u>할 수 있는 <u>절차형 SQL</u>이다.

* **구성:** 선언부(**DE**CLARE), 시작/종료부(**BE**GIN/END), 제어부(**CON**TROLL), **S**QL, 예외부(**E**XCEPTION), 반환부(**R**ETURN) `디비컨 SER`{:.success}

```sql
CREATE [OR REPLACE] FUNCTION 함수명
(파라미터_명 IN 데이터_타입, ...)
RETURN 데이터_타입
IS
	변수 선언
BEGIN
	명령어;
	RETURN 변수;
END;
```

### 트리거 :star:

* **개념:** 삽입, 갱신, 삭제 등의 <u>이벤트</u>가 <u>발생</u>할 때마다 관련 작업이 <u>자동</u>으로 <u>수행</u>되는 <u>절차형 SQL</u>이다.

* **종류:** 행 트리거(여러 번), 문장 트리거(한 번)

* **구성:** 선언부(**DE**CLARE), 이벤트(**E**VENT), 시작/종료부(**BE**GIN/END), 제어부(**CON**TROLL), **S**QL, 예외부(**E**XCEPTION) `디이비컨 SE`{:.success}

```sql
CREATE [OR REPLACE] TRIGGER 트리거명
[BEFORE | AFTER] 유형 ON 테이블명
[FOR EACH ROW]
BEGIN
END;
```

* **접두어:** INSERT, UPDATE, DELETE

* **주의사항:** TCL 사용 불가, 오류에 주의

## 데이터 조작 프로시저 최적화

### 데이터 조작 프로시저 성능 개선 :star:

* **쿼리 성능 개선(튜닝)**

    - **개념:** 프로시저에 있는  <u>SQL 실행 계획</u>을 <u>분석</u>, <u>수정</u>을 <u>최소의 시간</u>으로 <u>원하는 결과</u>를 얻도록 하는 <u>작업</u>이다.

    - **절차:** 문제 있는 SQL 식별 → 옵티마이저 통계 확인 → SQL 문 재구성 → 인덱스 재구성 → 실행계획 유지관리

* **옵티마이저 통계 확인**

    - **개념:** SQL을 가장 빠르고 효율적으로 수행할 최적의 처리경로를 생성해주는 DBMS 내부의 핵심엔진이다.

    - **유형:** 규칙기반 옵티마이저(RBO), 비용기반 옵티마이저(CBO)

    - **역할:** 쿼리 변환, 비용 산정, 계획 생성

    - **힌트 사용:** 항상 최선의 실행 계획을 수립할 수 없어 명시적인 <u>힌트</u>를 통해 <u>실행계획을 변경</u>한다.