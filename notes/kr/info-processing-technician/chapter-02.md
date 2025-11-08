---
layout: article
title: 1. 데이터베이스 기초 활용 
permalink: /notes/kr/info-processing-technician/chapter-02
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기능사 실기 강의 노트, 데이터베이스 기초 활용 개념과 활용 방법을 다룹니다.
keywords: "정보처리기능사, 실기, 데이터베이스 기초 활용, 데이터 처리, 프로그래밍"
---

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
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%EC%A0%95%EB%B3%B4%EC%B2%98%EB%A6%AC%EA%B8%B0%EB%8A%A5%EC%82%AC&reversal=false&textBg=false)


## 1. 데이터베이스의 개념 :star::star::star:
### 데이터베이스(Database) `통저운공`{:.success}
* <span class="blue-text">통합된 데이터(Integrated Data)</span>: 중복이 최소화된 데이터의 집합
* <span class="blue-text">저장된 데이터(Stored Data)</span>: 컴퓨터가 접근할 수 있는 매체에 저장된 데이터
* <span class="blue-text">운영 데이터(Operational Data)</span>: 현재 운영 중인 데이터
* <span class="blue-text">공용 데이터(Common Data)</span>: 여러 사용자 또는 응용 시스템들이 공유하는 데이터

### 데이터베이스 설계 `요개논물구`{:.success}
1. <span class="blue-text">요구</span> 조건 분석: 어떤 데이터가 필요한지, 무엇을 해야 하는지 정리
2. <span class="blue-text">개념</span>적 설계: 필요한 정보를 그림(도식)으로 쉽게 표현
3. <span class="blue-text">논리</span>적 설계: 사용할 데이터베이스에 맞게 구조를 구체적으로 설계
4. <span class="blue-text">물리</span>적 설계: 실제 저장 방식과 성능을 고려해 데이터 저장 방법 결정
5. <span class="blue-text">구현</span>: 데이터베이스를 실제로 만들고 사용할 수 있게 준비

### 스키마(Schema)
* __외부__ 스키마(External Schema): 사용자 관점, 각 사용자가 보는 스키마
* __개념__ 스키마(Conceptual Schema): 통합 관점, 조직 전체의 데이터베이스
* __내부__ 스키마(Internal Schema): 물리적 관점, 실질적인 데이터의 저장 구조

### 데이터베이스 사용자
* <span class="blue-text">데이터베이스 관리자(DBA : DataBase Administrator)</span>
    - 스키마를 정의, 생성, 삭제
    - 저장 구조 및 접근 방법 정의
    - 보안 및 접근 권한 정책 관리
    - 장애 예비 조치와 회복에 대한 전략 수립
    - 무결성을 위한 제약조건
    - 데이터 사전 구성
    - 성능 향상을 위해 데이터베이스 재구성
* <span class="blue-text">응용 프로그래머(Application Programmer)</span>: 데이터베이스에 접근하여 일반 사용자가 사용할 수 있는 인터페이스 제공
* <span class="blue-text">일반 사용자(End User)</span>: 터미널을 통해 데이터베이스에 접근하여 자원을 활용
<br>

<summary>🌟 데이터베이스 3단계 스키마 & 사용자 구분 보기</summary>

| 스키마 종류 | 담당 사용자 | 주요 역할 |
|------------|------------|---------|
| **외부 스키마** (External) | **일반 사용자, 응용 프로그램 사용자** | 필요한 **부분 데이터만 조회**<br/>사용자 뷰(View) 제공 |
| **개념 스키마** (Conceptual) | **DBA (데이터베이스 관리자)** | **전체 DB 통합 구조** 관리<br/>데이터 독립성 확보 |
| **내부 스키마** (Internal) | **시스템 프로그래머** | **물리적 저장 구조** 관리<br/>인덱스, 파일 구조, 최적화 |

---

## 2. 데이터 모델 :star::star::star:
### 데이터 모델의 정의
데이터 모델은 <span class="blue-text">실제 세계의 정보를 컴퓨터가 표현할 수 있도록 단순화, 추상화, 체계화</span>한 개념적 모델이다.

### 데이터 모델의 구성 요소 `개속관`{:.success}
* <span class="blue-text">개체(Entity)</span>: 데이터베이스에 표현하려는 대상, 실세계의 객체나 개념
* <span class="blue-text">속성(Attribute)</span>: 개체의 특성을 나타내는 가장 작은 논리적 단위
* <span class="blue-text">관계(Relationship)</span>: 개체들 간의 의미 있는 연관성

### 개체(Entity)의 구성 요소
* <span class="blue-text">개체 타입(Entity Type)</span>: 속성들로만 정의된 개체의 정의
* <span class="blue-text">개체 인스턴스(Entity Instance)</span>: 각 속성에 값을 가진 개별 개체
* <span class="blue-text">개체 세트(Entity Set)</span>: 개체 인스턴스들의 집합

### 관계(Relationship)의 형태 `일일다다`{:.success}
* <span class="blue-text">일대일(1:1)</span>: A의 각 원소가 B의 정확히 하나의 원소와 대응
* <span class="blue-text">일대다(1:N)</span>: A의 각 원소가 B의 여러 원소와 대응, B의 각 원소는 A의 하나의 원소와 대응
* <span class="blue-text">다대다(N:M)</span>: A의 각 원소가 B의 여러 원소와 대응, B의 각 원소도 A의 여러 원소와 대응

## 3. ER(Entity Relationship) 모델 :star::star::star:
### ER 모델의 정의
<span class="blue-text">Peter Chen</span>이 1976년에 제안한 가장 대표적인 개념적 데이터 모델로, <span class="blue-text">ERD(Entity Relationship Diagram)</span>를 통해 개체, 속성, 관계를 쉽게 표현할 수 있다.

### ER 도형의 종류

<figure>
<img src="/notes/assets/info-processing-technician/chapter-02-01.png" width="700px;" alt="ER 도형의 종류">
<figcaption>https://en.wikipedia.org/wiki/Entity-relationship_model</figcaption>
</figure>

| 도형 | 의미 | 모양 |
|------|------|:----:|
| <span class="blue-text">사각형</span> | 개체 타입(Entity Type) | <svg width="48" height="24" viewBox="0 0 48 24"><rect x="4" y="4" width="40" height="16" fill="none" stroke="black" stroke-width="2"/></svg> |
| <span class="blue-text">마름모</span> | 관계 타입(Relationship Type) | <svg width="48" height="24" viewBox="0 0 48 24"><rect x="16" y="4" width="16" height="16" fill="none" stroke="black" stroke-width="2" transform="rotate(45 24 12)"/></svg> |
| <span class="blue-text">타원</span> | 속성(Attribute) | <svg width="48" height="24" viewBox="0 0 48 24"><ellipse cx="24" cy="12" rx="18" ry="8" fill="none" stroke="black" stroke-width="2"/></svg> |
| <span class="blue-text">밑줄 친 타원</span> | 기본키(Primary Key) 속성 | <svg width="60" height="28" viewBox="0 0 60 28"><ellipse cx="30" cy="12" rx="22" ry="9" fill="none" stroke="black" stroke-width="2"/><line x1="12" y1="15" x2="48" y2="15" stroke="black" stroke-width="2"/></svg> |
| <span class="blue-text">이중 타원</span> | 다중값 속성(Multivalued Attribute) | <svg width="60" height="28" viewBox="0 0 60 28"><ellipse cx="30" cy="14" rx="20" ry="9" fill="none" stroke="black" stroke-width="2"/><ellipse cx="30" cy="14" rx="24" ry="12" fill="none" stroke="black" stroke-width="2"/></svg> |
| <span class="blue-text">점선 타원</span> | 유도 속성(Derived Attribute) | <svg width="60" height="28" viewBox="0 0 60 28"><ellipse cx="30" cy="14" rx="22" ry="10" fill="none" stroke="black" stroke-width="2" stroke-dasharray="4 4"/></svg> |
| <span class="blue-text">삼각형(ISA)</span> | ISA 관계 | <svg width="48" height="28" viewBox="0 0 48 28"><polygon points="24,4 40,24 8,24" fill="none" stroke="black" stroke-width="2"/></svg> |
| <span class="blue-text">선</span> | 개체 타입과 속성 연결 | <svg width="60" height="16" viewBox="0 0 60 16"><line x1="6" y1="8" x2="54" y2="8" stroke="black" stroke-width="2"/></svg> |
| <span class="blue-text">겹치는 타원</span> | 복합 속성(Composite Attribute) | <svg width="64" height="28" viewBox="0 0 64 28"><ellipse cx="28" cy="14" rx="18" ry="9" fill="none" stroke="black" stroke-width="2"/><ellipse cx="36" cy="14" rx="18" ry="9" fill="none" stroke="black" stroke-width="2"/></svg> |




### ISA 관계
특정 개체를 여러 하위 개체로 나눌 수 있을 때, 상위 개체와 하위 개체 간의 관계를 나타낸다.
> 예: 학생 → 재학생, 휴학생, 졸업생


## 4. 관계형 데이터베이스의 구조 :star::star::star:
### 관계형 데이터베이스의 개요
* 1970년 <span class="blue-text">IBM의 E. F. Codd</span>에 의해 처음 제안
* 개체와 관계를 모두 <span class="blue-text">릴레이션(Relation)</span>이라는 표로 표현
* <span class="blue-text">개체 릴레이션</span>과 <span class="blue-text">관계 릴레이션</span>으로 구분

### 릴레이션의 구조
* <span class="blue-text">릴레이션 스키마</span>: 릴레이션의 구조를 나타냄 (속성들의 집합)
* <span class="blue-text">릴레이션 인스턴스</span>: 실제 값들 (튜플들의 집합)
<img src="/notes/assets/info-processing-technician/chapter-02-06.png" width="100%;" alt="릴레이션 구조">
<figcaption>출처 : https://tragramming.tistory.com/48</figcaption>

### 릴레이션의 구성 요소
* <span class="blue-text">속성(Attribute)</span>: 릴레이션을 구성하는 가장 작은 논리적 단위
  - <span class="blue-text">디그리(Degree)</span>: 속성의 개수
* <span class="blue-text">튜플(Tuple)</span>: 릴레이션을 구성하는 각각의 행
  - <span class="blue-text">카디널리티(Cardinality)</span>: 튜플의 개수
<img src="/notes/assets/info-processing-technician/chapter-02-07.PNG" width="80%;" alt="디그리와 카디널리티의 차이">
<figcaption>출처 : https://tragramming.tistory.com/48</figcaption>

### 릴레이션의 특징 `유순변중원키`{:.success}
* <span class="blue-text">유일성</span>: 동일한 튜플이 존재할 수 없음
* <span class="blue-text">순서 무관</span>: 튜플들 간의 순서는 중요하지 않음
* <span class="blue-text">변화성</span>: 시간에 따라 변함 (삽입, 삭제 등)
* <span class="blue-text">중복 배제</span>: 속성명은 유일해야 함
* <span class="blue-text">원자값</span>: 속성값은 더 이상 분할할 수 없는 원자값
* <span class="blue-text">키 설정</span>: 튜플을 유일하게 식별하기 위한 키 설정

### 도메인(Domain)
하나의 속성이 취할 수 있는 <span class="blue-text">같은 타입의 원자값들의 집합</span>
> 예: 성별 속성의 도메인 = {'남', '여'}

## 5. 키(Key)의 개념 및 종류 :star::star::star:
### 키의 정의
데이터베이스에서 조건에 만족하는 튜플을 찾거나 순서대로 정렬할 때 <span class="blue-text">기준이 되는 속성</span>

### 키의 종류 `슈후기대외`{:.success}

#### 슈퍼키(Super Key)
* 릴레이션 내 속성들의 집합으로 구성된 키
* <span class="blue-text">유일성</span>은 만족하지만 <span class="blue-text">최소성</span>은 만족하지 않음
> 예: (학번, 주민등록번호), (학번, 주민등록번호, 성명)

#### 후보키(Candidate Key)
* 튜플을 유일하게 식별하기 위한 속성들의 부분집합
* <span class="blue-text">유일성</span>과 <span class="blue-text">최소성</span>을 모두 만족
> 예: 학번, 주민등록번호

#### 기본키(Primary Key)
* 후보키 중에서 <span class="blue-text">특별히 선택된 키</span>
* <span class="blue-text">NULL 값을 가질 수 없음</span>
* <span class="blue-text">중복값을 가질 수 없음</span>

#### 대체키(Alternate Key)
* 기본키로 선택되지 않은 <span class="blue-text">나머지 후보키</span>

#### 외래키(Foreign Key)
* <span class="blue-text">다른 릴레이션의 기본키를 참조</span>하는 속성 또는 속성들의 집합
* 릴레이션 간의 관계를 표현하는 데 사용

### 키의 특성
* <span class="blue-text">유일성(Uniqueness)</span>: 하나의 키 값으로 단일 튜플을 유일하게 식별
* <span class="blue-text">최소성(Minimality)</span>: 최소한의 필요 속성으로 구성되어 하나의 속성을 제거하면 유일성을 잃음

## 6. 무결성(Integrity) :star::star::star:
### 무결성의 정의
데이터베이스에 저장된 데이터 값과 그것이 표현하는 <span class="blue-text">현실 세계의 실제값이 일치하는 정확성</span>

### 무결성 제약 조건
데이터베이스에 들어 있는 데이터의 정확성을 보장하기 위해 <span class="blue-text">부정확한 자료가 저장되는 것을 방지</span>하는 제약 조건

### 무결성의 종류 `개도참사NULL고키관`{:.success}

#### 개체 무결성(Entity Integrity)
* 기본키를 구성하는 어떤 속성도 <span class="blue-text">NULL 값이나 중복값을 가질 수 없음</span>
> 예: <학생> 릴레이션에서 '학번'이 기본키면 반드시 값을 입력해야 하고 중복 불가

#### 도메인 무결성(Domain Integrity)
* 주어진 속성 값이 <span class="blue-text">정의된 도메인에 속한 값</span>이어야 함
> 예: <수강> 릴레이션의 '과목명'이 '영어', '수학', '전산'만 허용되면 이 값들만 입력 가능

#### 참조 무결성(Referential Integrity)
* 외래키 값은 <span class="blue-text">NULL이거나 참조 릴레이션의 기본키 값과 동일</span>해야 함
* 외래키와 참조하는 테이블의 기본키는 <span class="blue-text">도메인과 속성 개수가 같아야 함</span>

#### 사용자 정의 무결성(User-Defined Integrity)
* 속성 값들이 <span class="blue-text">사용자가 정의한 제약조건에 만족</span>해야 함

#### NULL 무결성
* 릴레이션의 특정 속성 값이 <span class="blue-text">NULL이 될 수 없도록</span> 하는 규정

#### 고유 무결성(Unique Integrity)
* 릴레이션의 특정 속성에 대해 <span class="blue-text">각 튜플이 갖는 속성값들이 서로 달라야 함</span>

#### 키 무결성(Key Integrity)
* 하나의 릴레이션에는 <span class="blue-text">적어도 하나의 키가 존재</span>해야 함

#### 관계 무결성(Relationship Integrity)
* 릴레이션에 튜플의 삽입 가능 여부 또는 릴레이션 간 튜플들의 관계에 대한 <span class="blue-text">적절성 여부</span>를 지정

## 7. 정규화(Normalization) :star::star::star:
### 정규화의 정의
<span class="blue-text">함수적 종속성</span> 등의 종속성 이론을 이용하여 잘못 설계된 관계형 스키마를 더 작은 속성의 세트로 쪼개어 <span class="blue-text">바람직한 스키마로 만들어 가는 과정</span>

### 정규화의 목적 `효중삽저무`{:.success}
* <span class="blue-text">효과적인 검색 알고리즘</span> 생성
* <span class="blue-text">중복을 배제</span>하여 삽입, 삭제, 갱신 이상의 발생 방지
* <span class="blue-text">삽입 시 릴레이션 재구성</span> 필요성 감소
* <span class="blue-text">저장공간 최소화</span> 및 데이터 구조의 안정성 극대화
* <span class="blue-text">무결성 유지</span> 극대화

### 정규화 단계 `도부이결다조`{:.success}
1. <span class="blue-text">도</span>메인이 원자값 (1NF)
2. <span class="blue-text">부</span>분적 함수 종속 제거 (2NF)
3. <span class="blue-text">이</span>행적 함수 종속 제거 (3NF)
4. <span class="blue-text">결</span>정자이면서 후보키가 아닌 것 제거 (BCNF)
5. <span class="blue-text">다</span>치 종속 제거 (4NF)
6. <span class="blue-text">조</span>인 종속성 이용 (5NF)

<figure>
<img src="/notes/assets/info-processing-technician/chapter-02-02.png" width="70%;" alt="정규화 단계">
</figure>

<figure>
<img src="/notes/assets/info-processing-technician/chapter-02-03.png" width="70%;" alt="정규화 단계">
<figcaption>1NF</figcaption>
</figure>

<figure>
<img src="/notes/assets/info-processing-technician/chapter-02-04.png" width="70%;" alt="정규화 단계">
<figcaption>2NF</figcaption>
</figure>

<figure>
<img src="/notes/assets/info-processing-technician/chapter-02-05.png" width="70%;" alt="정규화 단계">
<figcaption>3NF</figcaption>
</figure>

### 이상(Anomaly)의 종류 `삽삭갱`{:.success}
* <span class="blue-text">삽입 이상(Insertion Anomaly)</span>: 데이터 삽입 시 의도와 상관없이 원하지 않은 값들도 함께 삽입
* <span class="blue-text">삭제 이상(Deletion Anomaly)</span>: 한 튜플 삭제 시 의도와 상관없는 값들도 함께 삭제
* <span class="blue-text">갱신 이상(Update Anomaly)</span>: 일부 튜플의 정보만 갱신되어 정보에 모순 발생

### 함수적 종속성(Functional Dependency)
릴레이션의 어떤 속성의 값이 다른 속성의 값을 <span class="blue-text">고유하게 결정</span>하는 것
> 표기: X → Y (X가 Y를 함수적으로 결정)

### 다치 종속(Multi Valued Dependency)
A, B, C 3개의 속성을 가진 릴레이션 R에서 (A, C)에 대응하는 B 값의 집합이 <span class="blue-text">A 값에만 종속되고 C 값에는 무관</span>할 때
> 표기: A →→ B (B는 A에 다치 종속)

## 8. 고급 데이터베이스 기능 :star::star:
### 뷰(View)
* <span class="blue-text">하나 이상의 기본 테이블로부터 유도된 가상 테이블</span>
* 사용자에게 접근이 허용된 자료만을 제한적으로 보여줌
* <span class="blue-text">물리적으로 존재하지 않지만</span> 사용자에게는 있는 것처럼 간주
* <span class="blue-text">논리적 독립성</span> 제공

### 인덱스(Index)
* 데이터 레코드의 <span class="blue-text">검색 시간을 단축</span>시키기 위한 보조적인 데이터 구조
* <span class="blue-text">CREATE문</span>을 이용하여 생성
* <span class="blue-text">TABLE SCAN</span> 방지
* 삽입/삭제가 빈번한 경우 인덱스 개수 최소화 필요

### 시스템 카탈로그(System Catalog)
* 시스템 그 자체에 관련이 있는 <span class="blue-text">다양한 객체에 관한 정보를 포함</span>하는 시스템 데이터베이스
* <span class="blue-text">메타데이터(Meta-Data)</span> 저장
* <span class="blue-text">데이터 사전(Data Dictionary)</span>에 저장

## 9. 트랜잭션(Transaction) :star::star:
### 트랜잭션의 정의
데이터베이스에서 <span class="blue-text">하나의 논리적 기능을 수행하기 위한 작업 단위</span>로, 데이터베이스 관련 연산의 가장 기본적인 단위

### 트랜잭션의 특징
* 데이터베이스 시스템에서 <span class="blue-text">복구 및 병행 수행 시 처리되는 작업의 논리적 단위</span>
* 하나의 트랜잭션은 <span class="blue-text">하나의 질의문 또는 여러 질의문</span>으로 구성
* 일반적으로 <span class="blue-text">Commit 또는 Rollback</span>됨

### ACID 특성 `원일독영`{:.success}
* <span class="blue-text">원자성(Atomicity)</span>: 트랜잭션의 연산은 모두 반영되거나 전혀 반영되지 않음
* <span class="blue-text">일관성(Consistency)</span>: 트랜잭션이 성공적으로 완료되면 일관성 있는 데이터베이스 상태로 변환
* <span class="blue-text">독립성(Isolation)</span>: 동시 실행되는 트랜잭션들이 서로 간섭하지 않음
* <span class="blue-text">영속성(Durability)</span>: 성공적으로 완료된 트랜잭션의 결과는 영구적으로 반영

### Commit과 Rollback
* <span class="blue-text">Commit</span>: 명령 수행 결과를 실제 물리적 디스크에 저장하고 정상 완료를 관리자에게 알림
* <span class="blue-text">Rollback</span>: Commit되지 않은 변경 내용을 취소하고 데이터베이스를 이전 상태로 복원

## 10. DBMS :star::star::star:
### DBMS의 정의 (Database Management System)
사용자와 데이터베이스 사이에서 <span class="blue-text">사용자의 요구에 따라 정보를 생성</span>해 주고, <span class="blue-text">데이터베이스를 관리</span>해 주는 소프트웨어

### DBMS의 필수 기능 `정조제`{:.success}
* <span class="blue-text">정의 기능(Definition)</span>: 데이터 구조, 형, 제약조건 등을 명시
* <span class="blue-text">조작 기능(Manipulation)</span>: 데이터 검색, 갱신, 삽입, 삭제 등의 인터페이스 제공
* <span class="blue-text">제어 기능(Control)</span>: 데이터 무결성 유지를 위한 제어

### DBMS의 종류 `계망관`{:.success}
* <span class="blue-text">계층형 DBMS</span>: 트리 구조, 1:N 관계만 지원 (IMS, System2000)
* <span class="blue-text">망형 DBMS</span>: 그래프 구조, 1:1, 1:N, N:M 관계 모두 지원 (IDS, TOTAL, IDMS)
* <span class="blue-text">관계형 DBMS</span>: 2차원 표 구조, 가장 널리 사용 (Oracle, SQL Server, MySQL)

### DBMS의 장단점

#### 장점 `논물공일무보표통최실`{:.success}
* <span class="blue-text">논리적, 물리적 독립성</span> 보장
* <span class="blue-text">물리적 중복</span> 피해 기억공간 절약
* <span class="blue-text">공동 이용</span> 가능
* <span class="blue-text">일관성</span> 유지
* <span class="blue-text">무결성</span> 유지
* <span class="blue-text">보안</span> 유지
* <span class="blue-text">표준화</span> 가능
* <span class="blue-text">통합 관리</span> 가능
* <span class="blue-text">최신 데이터</span> 유지
* <span class="blue-text">실시간 처리</span> 가능

#### 단점 `전전대백시`{:.success}
* <span class="blue-text">전문가</span> 부족
* <span class="blue-text">전산화 비용</span> 증가
* <span class="blue-text">대용량 디스크</span> 집중적 Access로 과부하 발생
* <span class="blue-text">백업과 회복</span> 어려움
* <span class="blue-text">시스템</span> 복잡

### 비관계형 DBMS(NoSQL)
* 데이터 간의 관계를 정의하지 않고 <span class="blue-text">비구조적 데이터를 저장</span>
* <span class="blue-text">빅데이터 처리</span>를 위한 시스템으로 각광
* <span class="blue-text">수평적 확장 및 분산 저장</span> 가능
* 데이터 구조에 따라 <span class="blue-text">Key-Value, Document, Graph DBMS</span> 등으로 분류


<summary><strong>🌟 Key-Value, Document, Graph DBMS ?</strong></summary>


| 구분 | Key-Value Store | Document Store | Graph DB |
|------|----------------|----------------|----------|
| 데이터 구조 | 키-값 한 쌍 | 문서(JSON/BSON) | 노드 + 관계 |
| 강점 | 빠른 속도 / 캐시 | 유연한 구조 / 검색 OK | 관계 탐색 최강  |
| 약점 | 검색·관계 약함 | 복잡한 관계 불리 | 단순조회엔 과함 |
| 대표 사례 | Redis, DynamoDB | MongoDB, CouchDB | Neo4j, ArangoDB |
| 사용 예 | 세션/캐시 | 사용자/게시글 | 추천/소셜 |

