---
layout: article
title: 9. 소프트웨어 개발 보안 구축
permalink: /notes/kr/info-processing-engineer/chapter-09
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기사 필기와 실기에 대한 요약, 특히 소프트웨어 개발 보안 구축 부분에 대한 자세한 설명입니다.
keywords: "정보처리기사, 요약, 소프트웨어 개발 보안, DOS, DDOS, 세션 하이재킹, 백도어, IPSec, SSL, TLS, https, XSS, CSRF, SQL injection"
---

`정보처리기사`{:.info} `정보처리기사요약`{:.info} `소프트웨어개발보안`{:.info} `서버인증`{:.info} `접근통제`{:.info} `암호화`{:.info}

## 소프트웨어 개발 보안 설계
### 소프트웨어 개발 보안 설계 :star::star::star:

* **SW 개발 보안**

    - **개념:** 소스 코드 등에 존재하는 <u>취약점 제거</u>, 일련의 <u>보안 활동</u>을 의미

    - **구성 요소**

        + **3대 요소:** **기**밀성, **무**결성, **가**용성 `#기무가`{:.success}

        + **보안 용어:** **자**산, **위**협, **취**약점, **위**험 `#자위취위`{:.success}
    
* **SW 개발 보안을 위한 공격기법의 이해**

    - **DOS 공격:** <u>자원을 부족</u>하게 만들어 원래 의도대로 사용이 불가하게 만듦.

        + **종류:** SYN 플러딩, UDP 플러딩, 스머핑(ICMP Echo), 죽음의 핑(커다란 ICMP), 랜드 어택(출발지가 목적지), 티어 드롭(Fragment Offset), 보잉크(패킷 재조립 과부하)

    - **DDOS 공격:** 여러 대의 공격자를 분산 배치, 동시 동작 공격

        + **구성요소:** **H**andler, **A**gent, **M**aster, **A**ttacker, **D**eamon `#HAMAD`{:.success}

        + **공격 도구:** Trinoo(UDP flood), Tribe Flood Network(다양한 공격), Stacheldraht

        + **공격 종류**<br>

            👉 **대역폭 소진 공격:** UDP/ICMP Traffic Flooding, TCP Traffic Flooding, IP Flooding

            👉 **서비스 마비 공격:** HTTP Traffic Flooding, HTTP Header/Option Spoofing, Other L7 Service Flooding

            👉 **공격 대응 방안:** 차단 정책 업데이트, 좀비PC IP 확보, 보안 솔루션 운영, 홈페이지 보안 관리, 시스템 패치

    - **DRDoS 공격:** 공격자는 <u>출발지 IP를 공격대상 IP로 위조</u>하여 <u>다수의 반사 서버</u>로 <u>요청</u> 정보를 전송, <u>공격 대상자</u>는 <u>다량의 응답</u>을 받아서 <u>서비스</u>가 <u>거부</u>됨.

        + **공격 절차:** 출발지 IP 변조, 공격 대상자 서버로 응답, 서비스 거부

    - **세션 하이재킹:** <u>TCP</u>의 <u>세션 관리</u> <u>취약점</u>을 <u>이용한 공격기법</u>이다.

    - **애플리케이션 공격:** HTTP GET 플러딩, Slowloris(한 번의 CR+LF), RUDY(Content-Length), Slow HTTP Read DoS, Hulk DoS(URL 변경), Hash DoS

    - **네트워크 공격:** 스니핑, 네트워크 스캐너, 패스워드 크래킹(사전 크래킹, 무차별 크래킹, 패스워드 하이브리드 공격, 레인보우 테이블 공격), IP 스푸핑, ARP 스푸핑, ICMP Redirect 공격, 트로이 목마

    - **시스템 보안 위협:** 포맷 스트링 공격, 레이스 컨디션 공격, 키로거 공격, 루트킷

        + **- 버퍼 오버플로우 공격:** 스택 버퍼 오버플로우 공격, 힙 버퍼 오버플로우 공격<br>

        👉 **대응 방안:** 스택가드(카나리), 스택쉴드, ASLR, 안전한 함수 활용

        + **백도어**<br>

        👉 **탐지기법:** 프로세스 및 열린 포트 확인, Setuid 파일 검사, 백신 및 백도어 탐지 툴 활용, 무결성 검사, 로그 분석

    - **보안 관련 용어:** 스피어피싱, 스미싱, 큐싱, 봇넷, APT 공격, 공급망 공격, 제로데이 공격, 웜, 악성 봇, 사이버 킬체인, 랜섬웨어, 이블 트윈

* **서버 인증 및 접근 통제**

    - **서버 인증**

        + **개념:** <u>다중 사용자 시스템</u>과 <u>망 운영 시스템</u>에서 접속자의 <u>로그인 정보</u>를 <u>확인</u>하는 <u>보안 절차</u>이다.

        + **기능:** 스니핑 방지, 피싱 방지, 데이터 변조 방지, 기업 신뢰도 향상

        + **기술의 유형:** **지**식기반 인증, **소**지기반 인증, **생**체기반 인증, **특**징기반 인증 `#지소생특`{:.success}

    - **서버 접근 통제**

        + **용어:** 주체, 객체, 접근

        + **기법:** 식별, 인증, 인가, 책임추적성

        + **유형:** 임의적 접근 통제, 강제적 접근 통제, 역할 기반 접근 통제

        + **3A:** 인증(Authentication), 권한 부여(Authorization), 계정 관리(Accounting)

    - **접근 통제 보호 모델:** **벨**-라파듈라(**기**밀성), **비**바 모델(**무**결성) `#벨기비무`{:.success}

* **SW 개발 보안을 위한 암호화 알고리즘**

    - **개념:** <u>데이터 무결성</u> 및 <u>기밀성 확보</u>를 위해 <u>정보</u>를 <u>변환</u>하는 <u>기법</u>이다.

    - **주요 용어:** 평문, 암호문, 암호화, 복호화, 키, 치환 암호, 전치 암호
    <img src="/notes/assets/decryption-methods.png" width="500px" title="Decryption Methods"/>

* **안전한 전송을 위한 데이터 암호화 전송**

    - **IPSec:** <u>3계층</u>에서 무결성과 인증을 보장하는 <u>인증 헤더</u>와 기밀성을 보장하는 <u>암호화</u>를 이용한 <u>IP 보안 프로토콜</u>이다.

        + **동작 모드:** 전송 모드, 터널 모드

    - **SSL/TSL:** <u>4계층과 7계층 사이</u>에서 클라이언트와 서버 간의 웹 데이터 암호화, 상호 인증 및 전송 시 데이터 무결성을 보장하는 <u>보안 프로토콜</u>이다.

    - **S-HTTP:** 웹상에서 <u>네트워크 트래픽</u>을 <u>암호화</u>하는 주요 <u>방법</u>이다.

* **자산에 대한 보안 항목식별**

    - **주요 용어:** 자산, 사용자, 소유자, 관리자

## 소프트웨어 개발 보안 구현
### SW 개발 보안 구현 :star::star::star:

* **시큐어 코딩 가이드 `입보시 에코캡아`{:.success}**

    - **입력데이터 검증 및 표현**

        + **취약점**<br>

            👉 **XSS:** Stored XSS, Reflected XSS, DOM   

            👉 **사이트 간 요청 위조(CSRF)**   

            👉  **SQL 삽입:** From SQL Injection, Union SQL Injection, Stored Procedure SQL Injection, Mass SQL Injection, Error-Based SQL Injection, Blind SQL Injection

    - **보안 기능**

    - **시간 및 상태**

    - **에러 처리**

        + **취약점:** 오류 메시지 통한 정보 노출, 오류 상황 대응 부재, 적절하지 않은 예외 처리

    - **코드 오류**

        + **취약점:** 널 포인터 역참조, 정수를 문자로 변환, 부적절한 자원 해제, 초기화되지 않은 변수 사용

    - **캡슐화**

    - **API 오용**

### 시스템 보안 구현 :star:

* **보안 솔루션**

    - **네트워크 보안 솔루션:** 방화벽, 웹 방화벽(WAF), 네트워크 접근 제어(NAC), 침입 탐지 시스템(IDS), 침입 방지 시스템(IPS), 무선 침입 방지 시스템(WIPS), 통합 보안 시스템(UTM), 가상사설망(VPN)

    - **시스템 보안 솔루션:** 스팸 차단 솔루션, 보안 운영체제

    - **콘텐츠 유출 방지 보안 솔루션:** 보안 USB, 데이터 유출 방지, DRM

### SW 개발 보안 테스트와 결함 관리 :star:

* **소프트웨어 개발 보안 테스트**

    - **개념:** 보안 요구사항이 반영되어 있음을 보증하고, 취약점을 발견하고 개선하여 안전한 소프트웨어를 개발하기 위한 활동이다.

    - **유형:** 정적 분석, 동적 분석

### 비즈니스 연속성 계획(BCP) :star::star:

* **개념:** 각종 재해, 장애 재난으로부터 <u>위기관리</u>를 <u>기반</u>으로 비즈니스 <u>연속성</u>을 <u>보장</u>하는 <u>체계</u>이다.

* **주요 용어:** BIA, RTO(목표 복구 시간), RPO(목표 복구 시점), DRP(재해 복구 계획), DRS(재해 복구 시스템)

    - **DRS 유형:** Mirror Site, Hot Site, Warm Site, Cold Site

### 보안 중요 용어

* **공격 관련 중요 용어**

    - 부 채널 공격
    - 드라이브 바이 다운로드
    - 워터링홀
    - 스캠 공격
    - 하트 블리드
    - 크라임웨어
    - 토르 네트워크
    - MITM 공격
    - DNS 스푸핑 공격
    - 포트 스캐닝
    - 디렉토리 리스팅
    - 리버스 쉘 공격
    - 익스플로잇
    - 스턱스넷 공격
    - 크리덴셜 스터핑
* **대응 관련 중요 용어**

    - 허니팟
    - OWASP Top 10
    - 핑커프린팅
    - 워터마킹
    - 이상금융거래탐지시스템
    - CC
    - 사이버 위협정보 분성 공유시스템
    - 장착형 인증 모듈
    - CVE
    - CWE