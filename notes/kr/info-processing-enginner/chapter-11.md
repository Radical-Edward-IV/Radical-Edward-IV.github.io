---
layout: article
title: 11. 응용 SW 기초 기술 활용
permalink: /notes/kr/info-processing-engineer/chapter-11
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기사 필기와 실기에 대한 요약, 특히 응용 소프트웨어 기초 기술 활용 부분에 대한 자세한 설명입니다.
keywords: "정보처리기사, 요약, 커널, 스케줄링, 교착상태, 클라우드, OSI, 프로토콜, IPv4, IPv6, 전송계층, TCP, UDP, 패킷, 애드 훅, 네트워크, 운영체제, 개발도구, IDE"
---

`정보처리기사`{:.info} `정보처리기사요약`{:.info} `커널`{:.info} `스케줄링`{:.info} `교착상태`{:.info} `클라우드`{:.info} `OSI 7계층`{:.info} `프로토콜`{:.info} `IP`{:.info} `전송계층`{:.info} `TCP`{:.info} `패킷`{:.info} `애드 혹 네트워크`{:.info} `운영체제`{:.info} `개발도구`{:.info}

## 운영체제 특징
### 운영체제 종류 :star::star::star:

* **운영체제**

    - **개념:** <u>사용자</u>가 컴퓨터 하드웨어를 <u>쉽게 사용</u>할 수 있도록 <u>인터페이스</u>를 <u>제공</u>해주는 <u>소프트웨어</u>이다.

    - **특징**

        + **일반적:** 사용자 편리성 제공, 인터페이스 기능을 담당, 스케줄링 담당, 자원 관리, 제어 기능

        + **커널:** 프로세스 관리, 기억장치 관리, 주변장치 관리, 파일 관리

* **운영체제의 종류**

    - **윈도즈:** **G**UI 제공, **선**점형 멀티태스킹 방식 제공, PnP, **O**LE `#지선피 오`{:.success}

    - **유닉스 계열:** **대**화식 운영체제 기능 제공, **다**중 작업 기능 제공, 다중 **사**용자 기능 제공, **이**식성 제공, **계**층적 트리 구조 파일 시스템 제공 `#대다 사이계`{:.success}

    - **맥**

    - **안드로이드:** 리눅스 기반, 자바와 코틀린 언어, 런타임 라이브러리, 안드로이드 소프트웨어 개발 키트

### 운영체제 기본 명령어 활용 :star::star::star:

* **기본 명령어**

    - **윈도즈:** ATTRIB, CALL, CD, CHKDSK, CLS, CMD, COMP, DISKPART, ECHO, ERASE, EXIT

    - **리눅스:** uname -a, uname -r, cat, uptime, id, last, who, ls, pwd, rm, cp, mv, ps, pmap, kill, chmod, chown, ifconfig, host, tar, gzip, grep, find, cp, rsync, cd

        + **파일 접근 제어 명령어**<br>

        👉 **기호로 기술:** `chmod o-w yoom.c` , `chmod u+r g=rwx o+x yoom.c`   

        👉 **숫자로 기술:** `chmod 664 yoom.c`

### 운영체제 핵심 기능 파악 :star::star::star:

* **운영체제 핵심 기능:** 메모리 관리, 프로세스 관리

    - **메모리 관리 기법** `#반배할교`{:.success}

        + **반입 기법**

        + **배치 기법:** 최초 적합, 최적 적합, 최악 적합

        + **할당 기법**

        + **교체 기법**

    - **프로세스 관리**

        + **상태:** **생**성 상태, **준**비 상태, **실**행 상태, **대**기 상태, **완**료 상대 `#생준 실대완`{:.success}<br>

        👉 **상태 전이:** **디**스패치, **타**이머 런 아웃, **블**록, **웨**이크 업 `#디타 블웨`{:.success}

        + **스케줄링**<br>

        👉 **주요 용어:** 서비스 시간, 응답시간, 반환시간, 대기시간, 평균 대기시간, 종료시간, 시간 할당량, 응답률   

        👉 **선점형 스케줄링:** 라운드 로빈, SRT, 다단계 큐, 다단계 피드백 큐   

        👉 **비선점형 스케줄링:** 우선순위, 기한부, FCFS, HRN( $(대기시간 + 서비스 시간) / 서비스 시간$ ), SJF

        + **교착상태:** 다중프로세싱 환경에서 두 개 이상의 프로세스가 특정 자원할당을 <u>무한정 대기</u>하는 <u>상태</u>이다.

        👉 **발생 조건:** **상**호 배제, **점**유와 대기, **비**선점, **환**형 대기 `#상점비환`{:.success}

        👉 **해결 방법:** 예방, 회피(은행가 알고리즘), 발견, 복구

* **가상화, 클라우드**

    - **가상화:** 물리적인 리소스들을 사용자에게 하나 또는 여러 개로 보이게 하는 기술이다.

        + **종류:** 플랫폼 가상화, 리소스 가상화

        + **기술 요소:** 컴퓨팅 가상화, 스토리지 가상화, I/O 가상화, 컨테이너, 분산처리 기술, 네트워크 가상화 기술

* **클라우드 컴퓨팅:** 인터넷을 통해 가상화된 리소스를 제공하고, 정보를 자신의 컴퓨터가 아닌 연결된 다른 컴퓨터로 처리하는 기술이다.

    - **분류:** **사**설 클라우드, **공**용 클라우드, **하**이브리드 클라우드 `#사공하`{:.success}

    - **유형:** **인**프라형 서비스, **플**랫폼형 서비스, **소**프트웨어형 서비스 `#인플소`{:.success}

## 네트워크 기초 활용하기
### 네트워크 계층 구조 파악 :star::star::star:

* **네트워크**

    - **개념:** 원하는 <u>정보</u>를 원하는 수신자 또는 기기에 <u>전송</u>하기 위한 <u>인프라</u>이다.

    - **거리에 따른 분류:** WAN, LAN

* **OSI 7계층   `#아파서 티내다, 피나다`{:.success}**

    - **응용 계층**

        + **프로토콜:** HTTP, FTP, SMTP, POP3, IMAP, Telnet, SSH, SNMP

    - **표현 계층:** JPEG, MPEG

    - **세션 계층**

    - **전송 계층**

        + **프로토콜:** TCP, UDP

        + **장비:** L4 스위치

    - **네트워크 계층**

        + **프로토콜:** IP, ARP, RARP, ICMP, IGMP, 라우팅 프로토콜

        + **장비:** 라우터, 게이트웨이, L3 스위치, 유무선 인터넷 공유기, 백본 스위치 허브

    - **데이터링크 계층**

        + **개념:** 회선 제어, 흐름 제어, 오류 제어

        + **장비:** 브리지, L2 스위치, NIC, 스위칭 허브

    - **물리 계층**

        + **장비:** 허브, 리피터

### 네트워크 프로토콜 파악 :star::star::star:

* **프로토콜**

    - **개념:** 서로 다른 시스템이나 기기들 간의 <u>데이터</u> <u>교환</u>을 위한 <u>표준화된</u> <u>통신규약</u>이다.

    - **기본 3요소:** **구**문, **의**미, **타**이밍 `#구의타`{:.success}

* **네트워크 프로토콜**

    - **개념:** 컴퓨터나 <u>원거리 통신 장비 사이</u>에서 <u>메시지</u>를 주고받는 <u>양식</u>과 <u>규칙</u>의 <u>체계</u>이다.

    - **특징:** 단편화, 재조립, 캡슐화, 연결 제어, 오류 제어, 동기화, 다중화, 주소 지정

* **IPv6**

    - **특징:** IP 주소의 확장, 이동성, 인증 및 보안 기능, 개선된 QoS 지원, Plug&Play 지원, Ad-hoc 네트워크 지원, 단순 헤더 적용, 실시간 패킷 추적 가능

    - **IPv4 → IPv6 전환 방법:** 듀얼 스택, 터널링, 주소 변환

    - **프로토콜:** 멀티캐스트, 유니캐스트, 애니캐스트

* **라우팅 프로토콜**

    - **RIP(거리):** 벨만-포드 알고리즘 사용, 15홉 제한, UDP 사용

    - **OSFP(링크):** 다익스트라 알고리즘 사용, 라우팅 메트릭 지정, AS 분할 사용, 홉 카운트 무제한

    - **BGP(경로):** 거리 백터 알고리즘, 링크 상태 알고리즘

* **전송 계층**

    - **TCP 특징:** **신**뢰성 보장, **연**결 지향적 특징, **흐**름 제어, **혼**잡 제어 `#신연흐혼`{:.success}

        + **헤더 구조:** **So**urce/**De**stination Port Number, **Se**quence Number, **Ack**nowledgement Number, **HLE**N, **Fl**ag Bit, **Win**dow Size, **Che**cksum, **Ur**gent Pointer, **Opt**ions and **Pa**dding `#소데씨엑 헤리플윈 체어옵패`{:.success}

    - **UDP 특징:** 비신뢰성, 순서화되지 않은 데이터그램 서비스 제공, 실시간 응용 및 멀티캐스팅 가능, 단순 헤더

        + **헤더 구조:** **So**urce Port Number, **De**stination Port Number, UDP **Leng**th, UDP **Che**cksum, **Da**ta `#소데 랭체다`{:.success}

### 네트워크 전달 방식 :star:

* **패킷 교환 방식과 서핏 교환 방식의 차이**

    | 패킷 교환 방식 (X.25) | 서킷 교환 방식 |
    | --- | --- |
    | 데이터를 패킷 단위로 보내는 방식 | 전송 경로를 설정한 뒤 데이터를 송수신하는 방식 |
    | 회선 효율이 우수, 비동기 전송이 가능 | 전송 제어 절차와 형식에 제약을 받지 않음 |
    | 실시간 전송에 부적합, 네트워크 지연이 발생 | 송수식 측 모두 데이터 교환 준비가 완료되어야 함, 회선이 독점되어 있음 |
    | 이메일, 메시지 | 영상, 비디오 |
    | 데이터그램 방식, 가상 회선 방식 |  |

* **애드 혹 네트워크**

    - **개념:** 노드들에 의해 자율적으로 구성되는 기반 구조가 없는 네트워크이다.

## 기본 개발환경 구축하기
### 운영체제 설치 및 운용 :star::star:

* **운영체제 선택**

    - **윈도즈 계열 운영체제 선택:** Windows Home, Window Pro, Windows Pro for Workstation

    - **리눅스 계열 운영체제 선택:** 데비안 계열(Ubuntu), Redhat(Fedora) 계열, 기타

### 개발 도구 설치 및 운용 :star::star:

* **프로그래밍 언어**

    - **선택 시 고려사항:** 언어의 타입, 시스템의 특징, 언어 특징, 지원

    | 종류 | 타입 | 목적 | 언어 특징 |
    | --- | --- | --- | --- |
    | JAVA | 정적 | 일반 | 객체 지향, 명령형 |
    | C# | 정적 | 일반 | 객체 지향, 명령형 |
    | C++ | 정적 | 일반 | 순차적, 명령형 |
    | Perl | 동적 | 일반 | 순차적, 명령형 |
    | SQL | 동적 | 데이터 처리 | 선언형 |
    | PHP | 동적 | 일반 | 순차적, 명령형 |
    | Python | 동적 | 일반 | 순차적, 명령형 |

* **개발 지원 도구:** 요구사항 관리, 설계, 구현, 테스트, 빌드, 형상 관리, 품질 관리, 이슈 관리, 프로젝트 관리

### 응용 시스템 개발 인프로 구축 :star:

* **방식:** 온프레미스 방식, 클라우드 방식, 하이브리드 방식