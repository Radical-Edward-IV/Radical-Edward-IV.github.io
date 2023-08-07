---
title: 🏦 금융권 IT 시스템의 구조 정리
key: 20230801
tags: IT시스템
---

## 금융 IT 시스템 구조 정리

메타 데이터 관리 솔루션을 제공하는 회사에 취업한 후 금융팀에 배치되었다.   
금융권 IT에서 사용되는 🤔뜻 모를 단어들을 많이 접하게 되었다.   
금융권 IT 관계자들 사이에서 사용되는 용어들을 모른다고 해서 개발을 못하는 건 아니지만,   
전체적인 시스템을 파악하고 싶다면 알아두는 편이 좋겠다.   

<figure>
<img src="/images/financial-it-system-01.png" width="650px;" alt="메리츠 종금 증권 차세대 시스템">
<figcaption>메리츠 종금 증권 차세대 시스템</figcaption>
</figure>

<img src="/images/financial-it-system-02.png" width="650px;" alt="인터넷 전문 은행">



### 1. 계정계
통장을 계좌 또는 계정이라 부르는데, **본연의 금융 거래를 처리하는 시스템**이다. 개인/법인/기타 고객들의 거래 데이터를 가지고 있다. **가장 핵심적인 시스템**이며, 장애 발생 시 큰 타격을 받기 때문에 **보수적(삼중백업)으로 운영**된다.

* **시스템:** 공통, 수신, 여신, 신탁, 보험, 카드, 외환, 대행업무 등으로 구성되어 있다. 기본 데이터만 N억 건 이상이다. 일반적으로 원장(마스터테이블, 근원이 되는 장부)에 트랜잭션이 집중되기 때문에 안정적인 트랜잭션 처리를 위한 미들웨어가 발달해 있다.

* **업무:** 계좌 개설/폐쇄, 입출금, 계좌이체, 지로, 외환 등 전반적인 금융 업무를 담당한다.

​

### 2. 정보계
**고객 정보, 분석 정보를 처리하는 시스템**이다. 해당 정보를 처리하는 목적은 거래 활동 및 성과 분석에 있다. 기본적으로 정보연계, 통합조회, 통계분석 등을 많이 하기에 **관계형 데이터베이스 사용이 필수**이다.

* **시스템:** 계정계 데이터를 기반으로 영업점 및 부서의 업무 처리를 위해 필요한 고객의 거래 데이터에 대한 "기록" 및 기록의 "통계"를 관리하는 시스템이다. 주요 시스템으로는 데이터웨어하우스를 기반으로 하는 수익관리, 고객관계관리, 성과관리, 위험관리 시스템이 있다.

* **업무:** 신용평가, 여신승인, 리스크 관리, 수익관리, 고객관계관리, 성과관리, 위험관리, 마케팅 업무를 담당한다.

​

### 3. 대외계
**은행 외부 기관과 연계되는 업무를 처리하기 위한 대외(금융공동망 등)연결 시스템**이다. 해당 시스템은 네트워가 꼭 필요했기에 70년대에 처음 생겨났다. 지로 공과금 처리 등을 위해 금융 동공망이 생겨나며 대외계가 시작되었다. 거래내역 검증, 네트워크 오류 관리 등 매우 복잡한 구조로 운영되며, 대용량 처리보다는 정확성과 안정성이 중심이 된다.

* **업무:** 인터넷 뱅킹, 텔레뱅킹, CD 공동망, 타행이체, 카드결제, 주식 주문 등이 있다.

​

### 4. 채널계
대외계 시스템을 비롯하여 다양한 **비대면 채널들을 관리하는 시스템**을 아울러 채널계라고 부르기도 합니다.

* **시스템:** End User(최종 사용자)에 따른 다양한 접속 채널에서 발생하는 데이터를 관리하는 시스템이다.

* **업무:** 모바일 뱅킹, 인터넷 뱅킹, 현업의 단말기 데이터, 콜센터, 제휴 업체 정보 연계 등이 있다.

​

### 5. 운영계
IT 시스템의 **안정적인 운영을 위한 시스템**이다.

* **시스템:** 통합 관제, 네트워크 모니터링, 유지보수 등을 담당하는 시스템이다.

​

### 6. 기간계
새로운 시스템(TO-BE) 도입 시점에서, 고객이 **기존에 사용하던 시스템(AS-IS, Legacy)**을 말한다.

​

## 기타 용어 정리

* **U2L(Unix to Linux):** **유닉스 플랫폼 환경에서 리눅스 환경으로 Migration**하는 방법이다. 최근 증권사, 카드사, 인터넷 은행 등에서 U2L이 확산하고 있다.

<img src="/images/financial-it-system-03.png" width="500px;" alt="티맥스 U2L 전환">

* **DW(Data Warehouse):** 방대한 조직 내에서 분산 운영되는 각각의 데이터 베이스 관리 시스템들을 효율적으로 통합하여 조정ㆍ관리한다. 그렇기 때문에 효율적인 의사 결정 시스템을 위한 기초를 제공하는 실무적인 활용 방법론이 제공되고 있다.

* **RDW(Real-Time Data Warehouse):** 점점 더 많은 고객이 요구하는 기능인 라이브 데이터, 최근 데이터, 과거 데이터에 대한 분석 기능들을 다루는 실시간 데이터 웨어하우스이다.

* **ADW(Analytical Data Warehouse):** 유용한 정보를 발굴하고 정보를 바탕으로 결과를 만들고, 의사결정을 지원하는 것을 목표로 데이터를 정리, 변환, 모델링하는 데이터 웨어하우스이다.

* **ETL(Extract, Transform, Load):** ETL 시스템은 소스 데이터 시스템과 데이터 웨어하우스 간의 데이터 이동과 데이터 웨어하우스에서 데이터 마트로의 이동을 관리한다.

* **CDC(Change Data Capture):** https://blog.naver.com/blacksocks93/223116039736

* **EXP:** 간편 결제

* **방카슈랑스:** 좁은 의미로는 은행창구에서 보험상품을 판매하는 것이고, 넓은 의미로는 은행과 보험사간의 업무제휴를 뜻한다.

* **ITSM(IT service management):** IT 시스템보다는 엔드 포인트 사용자의 요구 및 IT 서비스(고객 우선)에 중점을 두는 솔루션이다. SR(서비스 요청) 정보를 제공받아 모델 및 DDL에 해당 정보를 추가하는 개발을 수행했었다 (CSR: Custom Service Request, CHA: 형상관리 요구사항).

* **FDS(이상거래탐지시스템, Fraud Detection System):** 전자금융거래 시 단말기 정보와 접속 정보, 거래 정보 등을 수집 및 분석하여 이상 금융 거래를 차단하는 기술이다.

<br>
<br>
<span style="color: grey; font-weight: 700;">References</span>   
[https://it-ist.tistory.com/m/171](https://it-ist.tistory.com/m/171)   
[https://tyrionlife.tistory.com/m/40](https://tyrionlife.tistory.com/m/40)   
[https://velog.io/@hitobi1014/IT-개발-금융권-이해](https://velog.io/@hitobi1014/IT-개발-금융권-이해)   
[https://newsroom.koscom.co.kr/17371](https://newsroom.koscom.co.kr/17371)   
[https://simroot.tistory.com/25](https://simroot.tistory.com/25) 