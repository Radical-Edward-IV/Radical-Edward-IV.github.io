---
layout: article
title: 3. 데이터 입출력 구현
permalink: /notes/kr/info-processing-engineer/chapter-03
key: notes
sidebar:
  nav: notes-kr
---

## 논리 데이터 저장소 확인
### 데이터 모델 :star::star::star:

* **개념:** **현실 세계**의 **정보**를 **인간과 컴퓨터**가 **이해**할 수 있도록 **추상화**한 것.

* **표시 요소:** 연산, 구조, 제약 조건

* **데이터 모델 절차:** **요**구사항 분석 → **개**념적 설계(개념적 데이터 모델, ERD) → **논**리적 설계(논리적 데이터 모델, 정규화) → **물**리적 설계(물리적 데이터 모델, 반정규화) `#요개논물`{:.info}

### 논리 데이터 모델 검증 :star::star::star:

* **논리 데이터 모델링 종류**

    - **관계 데이터 모델:** 2차원 테이블 형태로 구성

        + **구성 요소:** 릴레이션, 튜플, 속성, 카디널리티, 차수, 스키마, 인스턴스

        + **관계 대수:** 일반 집합 연산자(**합**집합, **교**집합, **차**집합, **카**티션 프로덕트   **#합교차카**), 순수 관계 연산자(**셀**렉트, **프**로젝트, **조**인, **디**비전 `#셀프조디`{:.info})

        + **관계 해석:** 관계 대수(절차적 정형 언어)와 반대로 비절차적 언어이다.

        + **속성:** **개**체(피터 챈 모델: 사각형 / 까마귀발 모델: 표), **속**성(피터 챈 모델: 원 / 까마귀발 모델: 표 내부), **관**계 `#개속관`{:.info}

    - **계층 데이터 모델**

    - **네트워크 데이터 모델**

* **개체-관계(E-R) 모델** 

    - **개념:** 현실 세계에 존재하는 **데이터와 관계**를 **이해**할 수 있는 형태로 **가장 널리 사용**되고 있는 모델이다.

    - **기호:** 개체(□), 관계(◇), 속성(○), 다중 값 속성(◎), 관계-속성 연결(─)

* **정규화**

    - **개념:** 데이터의 중복성 제거, 이상 현상을 방지, 데이터 일관성과 정확성 유지, 무손실 분해

        + **이상 현상:** **삽**입, **삭**제, **갱**신 이상 `#삽삭갱`{:.info}

    - **정규화 단계:** 1정규형(1NF, **원**자화) → 2정규형(2NF, **부**분 함수 종속 제거) → 3정규형(3NF, **이**행 함수 종속 제거) → 보이스-코드 정규형(BCNF, **결**정자 함수 종속 제거) → 4정규형(4NF, **다**치 종속 제거) → 5정규형(5NF, **조**인 종속 제거) `#원부이 결다조`{:.info}

* **반 정규화**

    - **개념:** **성능 향상**, **개발 운영의 단순화**를 위해 **중복**, **통합**, **분리 등**을 **수행**하는 기법

    - **기법:** **테이블**(테이블 **병**합, 테이블 **분**할, **중**복 테이블 추가(집계 테이블 추가, 진행 테이블 추가, 특정 부분만을 포함하는 테이블 추가)), **컬**럼(컬럼 **중**복화), **관**계(**중**복관계 추가) `#테병분중 컬중 관중`{:.info}

## 물리 데이터 저장소 설계
### 물리 데이터 저장소 설계 :star::star::star:

* **물리 데이터 모델링**

    - **개념:** 논리모델을 적용하고자 하는 **기술에 맞도록 상세화**해가는 **과정**이다.

    - **변환 절차:** 개체를 테이블로 변환 → 속성을 컬럼으로 변환 → UID를 기본키로 변환 →관계를 외래키로 변환 → 컬럼 유형과 길이 정의 → 반 정규화 수행

### 물리 데이터 저장소 구성 :star:

* **테이블 제약 조건 설계**

    - **참조무결성 제약 조건:** **참조하는 외래키의 값**은 항상 **참조되는 릴레이션에 기본키**로 존재해야 한다.

    - **옵션:** 제한(Restricted), 연쇄(Cascade), 널 값(Nullify)

* **인덱스 설계**

    - **개념:** **검색 연산의 최적화**를 위해 **열에 대한 정보**를 구성한 **데이터구조**이다.

* **뷰 설계**

    - **속성:** REPLACE, FORCE, NOFORCE, WITH CHECK OPTION, WITH READ ONLY

* **클러스터 설계**

    - **적용 기준:** **인덱스의 단점을 해결**한 기법으로 **분포도가 넓을수록** 오히려 **유리**하다.

* **파티션 설계**

    - **종류:** **레**인지 파티셔닝, **해**시 파티셔닝, **리**스트 파티셔닝, **컴**포지트 파티셔닝, **라**운드로빈 파티셔닝 `#레해리컴라`{:.info}

    - **장점:** **성**능 향상, **가**용성 향상, **백**업 가능, 경**합**감소 `#성가백합`{:.info}

## 데이터베이스 기초 활용하기
### 데이터베이스 종류 :star::star::star:

* **데이터베이스**

    - **개념:** **다수의 인원, 시스템**이 **사용**할 목적으로 **통합**하여 **관리**되는 **데이터**의 **집합**이다.

    - **정의:** **통**합된 데이터, **저**장된 데이터, **운**영 데이터, **공**용 데이터 `#통저운공`{:.info}

    - **특성:** 실시간 접근성, 계속적인 변화, 동시 공용, 내용 참조

    - **종류:** 파일 시스템(ISAM, VSAM), 관계형 데이터베이스 관리시스템(Oracle, SQL Server, MySQL, Maria DB), 계층형 데이터베이스 관리시스템(IMS, System2000), 네트워크 데이터베이스 관리시스템(IDS, IDMS, Database Manegement System)

* **DBMS**

    - **개념:** **데이터 관리**의 **복잡성**을 **해결**하는 동시에 데이터 추가, 보안 등 **추가 기능**을 **제공**하는 **소프트웨어**이다.

    - **유형:** Key-Value DBMS, Column Family Data Store DBMS, Document Store DBMS, Graph DBMS

    - **특징:** 데이터 무결성, 데이터 일관성, 데이터 회복성, 데이터 보안성, 데이터 효율성

* **데이터베이스 기술 트랜드**

    - **빅데이터**

        + **개념:** 주어진 비용, 시간 내에 처리 가능한 데이터 범위를 넘어서는 **수십 페타바이트 크기**의 **비정형 데이터**이다.

        + **특성:** 데이터의 양, 데이터의 다양성, 데이터의 속도

        + **수집, 저장, 처리 기술:** 비정형/반정형 데이터 수집, 정형 데이터 수집, 분산데이터 저장/처리(HDFS, 맵 리듀스), 분산데이터 베이스

        + **분석, 실시간 처리 및 시각화 주요 기술:** 빅데이터 분석, 빅데이터 실시간 처리, 분산 코디네이션, 분석 및 시각화

    - **NoSQL**

        + **개념:** 전통적인 **RDBMS와 다른 DBMS**를 지칭하기 위한 용어, 고정된 테이블 스키마가 필요없고 조인 연산을 사용하지 않고 **수평적으로 확장**이 가능하다.

        + **특성:** Basically Available, Soft-State, Eventually Consistency

        + **유형:** Key-Value Store, Column Family Data Store, Document Store, Graph Store `#키컬도그`{:.info}

    - **데이터 마이닝**

        + **개념:** **대규모 데이터** 안에서 체계적이고 자동적으로 **통계적 규칙**이나 **패턴**을 찾아내는 **기술**.

        + **절차:** 목적 설정 → 데이터 준비 → 가공 → 마이닝 기법 적용 → 정보 검증

        + **주요 기법:** **분**류 규칙, **연**관 규칙, **연**속 규칙, **데**이터 군집화 `#분연 연데`{:.info}