---
layout: article
title: 3. 네트워크 기초 활용 
permalink: /notes/kr/info-processing-technician/chapter-03
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기능사 실기 강의 노트, 네트워크 기초 활용 개념과 활용 방법을 다룹니다.
keywords: "정보처리기능사, 실기, 네트워크 기초 활용, 데이터 처리, 프로그래밍"
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

## 1. 네트워크 / 인터넷 :star::star::star:

### 네트워크(Network)의 개념
네트워크는 <span class="blue-text">두 대 이상의 컴퓨터를 전화선이나 케이블 등으로 연결하여 자원을 공유</span>하는 것을 말한다.

#### 네트워크의 분류 `근광`{:.success}
* <span class="blue-text">근거리 통신망(LAN; Local Area Network)</span>: 제한된 지역 내에서 고속 데이터 전송
* <span class="blue-text">광대역 통신망(WAN; Wide Area Network)</span>: 넓은 지역에 걸친 네트워크 연결

### 인터넷(Internet)의 개요
인터넷이란 <span class="blue-text">TCP/IP 프로토콜을 기반으로 하여 전 세계 수많은 컴퓨터와 네트워크들이 연결된 광범위한 통신망</span>이다.

<summary> 🌟 TCP/IP </summary>

+ 컴퓨터끼리 데이터를 주고받기 위한 **통신 규칙(Protocol)** 들의 **모음(집합)**


| 구분 | TCP (Transmission Control Protocol) | IP (Internet Protocol) |
|------|--------------------------------------|-------------------------|
| **역할** | 데이터를 안전하게 전송하도록 관리 | 데이터를 어디로 보낼지 경로를 결정 |
| **방식** | 연결형(연결 후 데이터 전송) | 비연결형(패킷 단위로 독립 전송) |
| **주요 기능** | 오류 제어, 흐름 제어, 순서 제어 | 주소 지정, 경로 설정, 패킷 전달 |
| **특징** | 신뢰성 ↑ 속도 ↓ | 신뢰성 ↓ 속도는 ↑ |
| **계층** | OSI 4계층(전송계층)| OSI 3계층(네트워크 계층) |
| **관계** | IP 위에서 작동(TCP는 IP의 서비스를 이용) | TCP의 하위계층, 데이터 운반 담당|




#### 인터넷의 특징 `미유모네백`{:.success}
* <span class="blue-text">미국 국방성의 ARPANET</span>에서 시작
* <span class="blue-text">유닉스 운영체제</span> 기반
* <span class="blue-text">모든 컴퓨터는 고유한 IP 주소</span>를 가짐
* <span class="blue-text">네트워크 장비</span>: 브리지, 라우터, 게이트웨이
* <span class="blue-text">백본(Backbone)</span>: 인터넷의 주가 되는 기간망

## 2. IP 주소 체계 :star::star::star:

### IP 주소(Internet Protocol Address)
IP 주소는 <span class="blue-text">인터넷에 연결된 모든 컴퓨터 자원을 구분하기 위한 고유 주소</span>이다.

#### IPv4 주소 구조
* <span class="blue-text">32비트</span>로 구성 (8비트씩 4부분)
* <span class="blue-text">숫자로 표현</span> (예: 192.168.1.1)
* <span class="blue-text">네트워크 부분과 호스트 부분</span>으로 구분

#### IP 주소 클래스 `ABCDE`{:.success}

| 클래스 | 사용 용도 | 시작 주소 | 서브넷 마스크 | 설명 |
|--------|-----------|-----------|---------------|------|
| <span class="blue-text">A Class</span> | 국가나 대형 통신망 | 0 ~ 127 | 255.0.0.0 | 대규모 네트워크 |
| <span class="blue-text">B Class</span> | 중대형 통신망 | 128 ~ 191 | 255.255.0.0 | 중규모 네트워크 |
| <span class="blue-text">C Class</span> | 소규모 통신망 | 192 ~ 223 | 255.255.255.0 | 소규모 네트워크 |
| <span class="blue-text">D Class</span> | 멀티캐스트 | 224 ~ 239 | - | 멀티캐스트 용도 |
| <span class="blue-text">E Class</span> | 실험적 주소 | 240 ~ 255 | - | 실험용, 공용되지 않음 |

### IPv6 (Internet Protocol version 6)
IPv6은 <span class="blue-text">IPv4의 주소 부족 문제를 해결하기 위해 개발</span>된 차세대 IP 주소 체계이다.

#### IPv6의 특징 `빠호인주융실`{:.success}
* <span class="blue-text">빠른 자료 전송</span>: IPv4에 비해 전송 속도 향상
* <span class="blue-text">호환성</span>: IPv4와의 호환성 뛰어남
* <span class="blue-text">인증성, 기밀성, 데이터 무결성</span> 지원
* <span class="blue-text">주소의 확장성, 융통성, 연동성</span> 뛰어남
* <span class="blue-text">실시간 흐름 제어</span>로 향상된 멀티미디어 기능
* <span class="blue-text">Traffic Class, Flow Label</span>을 이용한 등급별 서비스

#### IPv6 주소 구조
* <span class="blue-text">128비트</span>로 구성 (16비트씩 8부분)
* <span class="blue-text">16진수로 표현</span>하고 콜론으로 구분
* 예: 2001:0db8:85a3:0000:0000:8a2e:0370:7334

#### IPv6 주소 체계 `유멀애`{:.success}
<!--암기에 도움이 될 것 같아 사용예시를 추가해 보았습니다. -->

| 주소 유형 | 설명 | 특징 | 사용 예시 | 
|-----------|------|------|
| <span class="blue-text">유니캐스트(Unicast)</span> | 단일 송신자와 단일 수신자 간의 통신 | 1:1 통신 | 웹서버 → 클라이언트 HTML 페이지 전송 |
| <span class="blue-text">멀티캐스트(Multicast)</span> | 단일 송신자와 다중 수신자 간의 통신 | 1:N 통신 | 실시간 방송, IPTV |
| <span class="blue-text">애니캐스트(Anycast)</span> | 단일 송신자와 가장 가까이 있는 단일 수신자 간의 통신 | 최단 경로 통신 | DNS서버, 클라우드 서비스 |

### 도메인 네임(Domain Name)
* 도메인 네임은 <span class="blue-text">숫자로 된 IP 주소를 사람이 이해하기 쉬운 문자 형태로 표현</span>한 것이다.

#### 도메인 네임 구조
```
www.my-company.co.kr
│   │          │  │
│   │          │  └─ 국가 도메인 (.kr)
│   │          └──── 기관 종류 (.co)
│   └─────────────── 기관 이름 (my-company)
└─────────────────── 호스트 이름 (www)
```

| 구성 요소 | 설명 | 예시 |
|-----------|------|------|
| <span class="blue-text">호스트 컴퓨터 이름</span> | 서버의 역할을 나타냄 | www, ftp, mail |
| <span class="blue-text">소속 기관 이름</span> | 조직이나 회사명 | my-company, google |
| <span class="blue-text">소속 기관 종류</span> | 조직의 성격 | .com, .org, .edu, .co |
| <span class="blue-text">소속 국가</span> | 국가 코드 | .kr, .us, .jp |

> 💡 **팁**: <span class="blue-text">우측으로 갈수록 상위 도메인</span>을 의미하며, DNS(Domain Name System)를 통해 IP 주소로 변환됩니다! 🌐

## 3. OSI 참조 모델 :star::star::star:

### OSI(Open System Interconnection) 참조 모델의 개요
OSI 참조 모델은 <span class="blue-text">다른 시스템 간의 원활한 통신을 위해 ISO(국제표준화기구)에서 제안한 통신 규약(Protocol)</span>이다.

<figure>
<img src="/notes/assets/info-processing-technician/chapter-03-01.webp" width="80%" alt="OSI 참조 모델 7계층">
<figcaption>https://www.geeksforgeeks.org/computer-networks/tcp-ip-model/</figcaption>
</figure>


<summary> 🌟 OSI vs TCP/IP 비교 </summary>


| 구분 | OSI 7계층 | TCP/IP 4계층 |
|------|------------|---------------|
| 제정 기관 | ISO (국제표준화기구) | 미국 국방성(DARPA) |
| 계층 수 | 7계층 | 4계층 |
| 계층 구조(송신) | 응용 → 표현 → 세션 → 전송 → 네트워크 → 데이터링크 → 물리 | 응용 → 전송 → 인터넷 → 네트워크 액세스 |
| 계층 구조(수신) | 물리 → 데이터링크 → 네트워크 → 전송 → 세션 → 표현 → 응용 | 네트워크 액세스 → 인터넷 → 전송 → 응용 |
| 표준 목적 | 통신의 이론적 구조 제시 | 인터넷의 실제 구현 중심 |
| 전송 방식 | 연결형(TCP), 비연결형(UDP) 모두 포함(이론적 설계) | TCP/UDP 직접 구현 (실제 동작) |


#### 🌟 계층 대응 구조

| OSI 7계층 | TCP/IP 4계층 | 예시 프로토콜 |
|------------|----------------|----------------|
| **응용** (Application) | 응용 계층 | HTTP, FTP, SMTP, DNS |
| 표현 (Presentation) | ↑ 통합됨 | JPEG, ASCII, SSL |
| 세션 (Session) | ↑ 통합됨 | NetBIOS, RPC |
| **전송** (Transport) | 전송 계층 | TCP, UDP |
| **네트워크** (Network) | 인터넷 계층 | IP, ICMP, ARP |
| **데이터링크** (Data Link) | 네트워크 액세스 계층 | Ethernet, PPP |
| 물리 (Physical) | ↑ 통합됨 | RS-232C, X.21 |



#### OSI 모델의 특징 `개개`{:.success}
* <span class="blue-text">개방형 시스템</span> 간의 데이터 통신 시 필요한 장비 및 처리 방법을 7단계로 표준화
* <span class="blue-text">계층별 분리</span>: 1~3계층(하위), 4~7계층(상위)

### OSI 참조 모델 계층별 특징 `응표세전네데물`{:.success}

| 계층 | 계층명 | 주요 기능 | 표준 예시 | PDU |
|------|--------|-----------|-----------|-----|
| <span class="blue-text">7</span> | <span class="blue-text">응용 계층</span> | 사용자가 OS 환경에 접근할 수 있도록 서비스 제공 | HTTP, SMTP, POP3, FTP, TELNET | 데이터 |
| <span class="blue-text">6</span> | <span class="blue-text">표현 계층</span> | 데이터를 통신에 적당한 형태로 변환 | ASCII, EBCDIC, JPEG, MPEG | 데이터 |
| <span class="blue-text">5</span> | <span class="blue-text">세션 계층</span> | 통신 세션의 설정, 유지, 해제 | NetBIOS, RPC, SQL | 데이터 |
| <span class="blue-text">4</span> | <span class="blue-text">전송 계층</span> | 종단 시스템 간 투명한 데이터 전송 | TCP, UDP | 세그먼트 |
| <span class="blue-text">3</span> | <span class="blue-text">네트워크 계층</span> | 네트워크 연결 관리 및 데이터 교환 | IP, ARP, ICMP, IPX | 패킷 |
| <span class="blue-text">2</span> | <span class="blue-text">데이터 링크 계층</span> | 인접한 시스템 간 신뢰성 있는 정보 전송 | HDLC, LLC, LAPB | 프레임 |
| <span class="blue-text">1</span> | <span class="blue-text">물리 계층</span> | 전송에 필요한 기계적, 전기적 특성 규칙 | RS-232C, X.21 | 비트 |

#### 계층별 상세 설명

##### 물리 계층 (Physical Layer)
* <span class="blue-text">전송에 필요한 두 장치 간의 실제 접속과 절단</span> 등 기계적, 전기적, 기능적, 절차적 특성에 대한 규칙
* <span class="yellow-code">표준</span>: RS-232C, X.21 등
* <span class="yellow-code">PDU</span>: 비트(Bit)

##### 데이터 링크 계층 (Data Link Layer) <!-- line.196  개발 시스템 > 개방 시스템 으로 수정하였습니다. OS를 말씀하신 것 같아 수정했습니다.-->
* <span class="blue-text">두 개의 인접한 개방 시스템들 간에 신뢰성 있고 효율적인 정보 전송</span>
* <span class="yellow-code">표준</span>: HDLC, ADCCP, LLC, LAPB, LAPD 등
* <span class="yellow-code">PDU</span>: 프레임(Frame)

##### 네트워크 계층 (Network Layer)
* <span class="blue-text">개방 시스템들 간의 네트워크 연결을 관리하는 기능과 데이터의 교환 및 중계 기능</span> 수행
* <span class="yellow-code">표준</span>: X.25, ARP, IPX, IP, ICMP 등
* <span class="yellow-code">PDU</span>: 패킷(Packet)

##### 전송 계층 (Transport Layer)
* <span class="blue-text">논리적 안정과 균일한 데이터 전송 서비스 제공</span>으로써 종단 시스템(End-to-End) 간에 투명한 데이터 전송 기능
* <span class="yellow-code">표준</span>: TCP, UDP 등
* <span class="yellow-code">PDU</span>: 세그먼트(Segment)

##### 세션 계층 (Session Layer)
* <span class="blue-text">통신 세션의 설정, 유지, 해제</span>를 담당
* <span class="yellow-code">표준</span>: NetBIOS, RPC, SQL 등
* <span class="yellow-code">PDU</span>: 데이터(Data)

##### 표현 계층 (Presentation Layer)
* <span class="blue-text">응용 계층으로부터 받은 데이터를 세션 계층에 보내기 전에 통신에 적당한 형태로 변환</span>
* <span class="blue-text">서로 다른 데이터 표현 형태를 갖는 시스템 간의 상호 접속</span>을 위해 필요
* <span class="yellow-code">표준</span>: ASCII, EBCDIC, JPEG, MPEG 등
* <span class="yellow-code">PDU</span>: 데이터(Data)

##### 응용 계층 (Application Layer)
* <span class="blue-text">사용자가 OS 환경에 접근할 수 있도록 서비스 제공</span>
* <span class="yellow-code">서비스</span>: HTTP, 전자 사서함(SMTP, POP3), 파일 전송(FTP), 원격 접속(TELNET) 등
* <span class="yellow-code">PDU</span>: 데이터(Data)

> 💡 **팁**: <span class="blue-text">PDU(Protocol Data Unit)</span>는 각 계층에서 처리하는 데이터의 단위를 의미합니다! 각 계층마다 다른 형태의 데이터를 다룹니다! 🔄

## 4. 네트워크 관련 장비 :star::star:

### 네트워크 인터페이스 카드(NIC)
네트워크 인터페이스 카드는 <span class="blue-text">컴퓨터와 컴퓨터 또는 컴퓨터와 네트워크를 연결하는 장치</span>이다.
* <span class="blue-text">정보 전송 시 정보가 케이블을 통해 전송될 수 있도록 정보 형태 변환</span>
* <span class="yellow-code">이더넷 카드</span> 혹은 <span class="yellow-code">네트워크 어댑터</span>라고도 함

### 허브(Hub)
허브는 <span class="blue-text">한 사무실이나 가까운 거리의 컴퓨터들을 연결하는 장치</span>이다.
* 각 회선을 통합적으로 관리하며, 신호 증폭 기능을 하는 리피터 역할도 포함

#### 허브의 종류 `더스`{:.success}

##### 더미 허브(Dummy Hub)
* <span class="blue-text">네트워크에 흐르는 모든 데이터를 단순히 연결만 함</span>
* LAN이 보유한 대역폭을 컴퓨터 수만큼 나누어 제공
* 네트워크에 연결된 각 노드를 물리적인 성형 구조로 연결

##### 스위칭 허브(Switching Hub)
* <span class="blue-text">네트워크상에 흐르는 데이터의 유무 및 흐름을 제어</span>하여 각각의 노드가 허브의 최대 대역폭을 사용할 수 있는 지능형 허브
* 최근에 사용되는 허브는 대부분 스위칭 허브

### 리피터(Repeater)
리피터는 <span class="blue-text">전송되는 신호가 전송 선로의 특성 및 외부 충격 등의 요인으로 인해 원래의 형태와 다르게 왜곡되거나 약해질 경우 원래의 신호 형태로 재생하여 다시 전송</span>하는 장치이다.
* <span class="blue-text">OSI 참조 모델의 물리 계층</span>에서 동작
* <span class="blue-text">근접한 네트워크 사이에 신호 전송</span>

### 브리지(Bridge)
브리지는 <span class="blue-text">LAN과 LAN을 연결하거나 LAN 안의 컴퓨터 그룹을 연결</span>하는 장치이다.

#### 브리지의 특징 `데네트보`{:.success} <!-- MAC을 찾아보다 저와 같은 수강생이 있을 것 같아 간단한 비유를 작게 달아봤습니다. -->
* <span class="blue-text">데이터 링크 계층 중 MAC 계층</span>에서 사용    <small style="margin-left:5px; color:gray">MAC : 네트워크 장치 고유 식별자</small>
* <span class="blue-text">네트워크 상의 많은 단말기들에 의해 발생되는 트래픽 병목 현상</span> 줄임
* <span class="blue-text">네트워크를 분산적으로 구성하여 보안</span> 향상
* <span class="blue-text">브리지를 이용한 서브넷 구성 시 전송 가능한 회선 수</span>: n개일 때 n(n-1)/2개

### 스위치(Switch)
스위치는 <span class="blue-text">브리지와 같이 LAN과 LAN을 연결하여 훨씬 더 큰 LAN을 만드는 장치</span>이다.

#### 스위치의 특징 `하포수데`{:.success}
* <span class="blue-text">하드웨어를 기반으로 처리</span>해 빠름
* <span class="blue-text">포트마다 각기 다른 전송 속도</span>를 지원하도록 제어 가능
* <span class="blue-text">수십에서 수백개의 포트</span> 제공
* <span class="blue-text">OSI 참조 모델의 데이터 링크 계층</span>에서 사용

#### 스위치의 종류 `L2L3L4L7`{:.success}

| 스위치 종류 | OSI 계층 | 설명 | 주요 기능 | 연결 범위 |
|-------------|----------|------|-----------|-----------|
| <span class="blue-text">L2 스위치</span> | 2계층 | 일반적인 스위치 | MAC주소를 기반으로 프레임 전송 | 동일 네트워크 간의 연결 |
| <span class="blue-text">L3 스위치</span> | 3계층 | L2 스위치에 라우터 기능 추가 | IP 주소를 기반으로 패킷 전송 | 서로 다른 네트워크 간 연결 |
| <span class="blue-text">L4 스위치</span> | 4계층 | 로드밸런서가 달린 L3 스위치 | IP 주소 및 TCP/UDP를 기반으로 로드밸런싱 | 부하 분산 |
| <span class="blue-text">L7 스위치</span> | 7계층 | 세밀한 로드 밸런싱 | 애플리케이션 계층에서 로드 밸런싱 | 고급 부하 분산 |

### 라우터(Router)
라우터는 <span class="blue-text">브리지와 같이 LAN과 LAN의 연결 기능에 데이터 전송의 최적 경로를 선택할 수 있는 기능이 추가된 것</span>이다.

#### 라우터의 특징 `네접프`{:.success}
* <span class="blue-text">네트워크 계층</span>에서 동작하는 장비
* <span class="blue-text">접속 가능한 경로에 대한 정보를 라우팅 제어표에 저장</span>하여 보관
* <span class="blue-text">프로토콜 변환</span> 수행 (3계층까지의 프로토콜 구조가 다른 네트워크 간의 연결)

### 게이트웨이(Gateway)
게이트웨이는 <span class="blue-text">전 계층의 프로토콜 구조가 다른 네트워크의 연결을 수행</span>하는 장치이다.

#### 게이트웨이의 기능 `세표응출`{:.success}
* <span class="blue-text">세션, 표현, 응용 계층</span> 간을 연결
* <span class="blue-text">데이터 형식 변환, 주소 변환, 프로토콜 변환</span> 등을 수행
* <span class="blue-text">출입구 역할</span>: LAN에서 다른 네트워크에 데이터를 보내거나 받아들이는 역할

## 5. TCP/IP 프로토콜 :star::star::star:

### 프로토콜(Protocol)의 개념
프로토콜은 <span class="blue-text">서로 다른 기기들 간의 데이터 교환을 원활하게 수행할 수 있도록 표준화시켜 놓은 통신 규약</span>이다.

#### 프로토콜의 기본 요소 `구의시`{:.success}

| 요소 | 설명 | 내용 |
|------|------|------|
| <span class="blue-text">구문(Syntax)</span> | 전송하고자 하는 데이터의 형식 | 부호화, 신호 레벨 등을 규정 |
| <span class="blue-text">의미(Semantics)</span> | 두 기기 간의 효율적이고 정확한 정보 전송을 위한 협조 사항 | 오류 관리를 위한 제어 정보 규정 |
| <span class="blue-text">시간(Timing)</span> | 두 기기 간의 통신 속도, 메시지의 순서 제어 | 통신 속도, 순서 제어 등을 규정 |

#### 프로토콜의 기능 `단캡흐오동순주다경전`{:.success}
단편화와 재결합, 캡슐화, 흐름 제어, 오류 제어, 동기화, 순서 제어, 주소 지정, 다중화, 경로 제어, 전송 서비스 등

### TCP/IP의 개요
TCP/IP는 <span class="blue-text">인터넷에 연결된 서로 다른 기종의 컴퓨터들이 데이터를 주고받을 수 있도록 하는 표준 프로토콜</span>이다.

#### TCP와 UDP 비교 `신연패`{:.success}

| 프로토콜 | OSI 계층 | 서비스 유형 | 주요 특징 |
|----------|----------|-------------|-----------|
| <span class="blue-text">TCP</span> | 전송 계층 | <span class="blue-text">신뢰성 있는 연결형</span> 서비스 | 3-way-handshake, 패킷의 다중화, 순서 제어, 오류 제어, 흐름 제어 |
| <span class="blue-text">UDP</span> | 전송 계층 | <span class="blue-text">비연결형</span> 서비스 | 데이터그램 기반, 패킷의 분해/조립, 주소 지정, 경로 선택 |

### TCP/IP의 구조 `응전인네`{:.success}

| OSI 모델 | TCP/IP 계층 | 주요 기능 | 프로토콜 예시 |
|----------|-------------|-----------|---------------|
| <span class="blue-text">응용, 표현, 세션</span> | <span class="blue-text">응용 계층</span> | 응용 프로그램 간의 데이터 송수신 제공 | TELNET, FTP, SMTP, SNMP, DNS, HTTP |
| <span class="blue-text">전송 계층</span> | <span class="blue-text">전송 계층</span> | 호스트들 간의 신뢰성 있는 통신 제공 | TCP, UDP, RTCP |
| <span class="blue-text">네트워크 계층</span> | <span class="blue-text">인터넷 계층</span> | 데이터 전송을 위한 주소 지정, 경로 설정 제공 | IP, IPX, ICMP, ARP, RARP, OSPF |
| <span class="blue-text">데이터 링크, 물리</span> | <span class="blue-text">네트워크 액세스 계층</span> | 실제 데이터를 송수신하는 역할 | Ethernet, IEEE 802, HDLC, X.25, RS-232C, ARQ |

> 💡 **팁**: <span class="blue-text">TCP/IP는 4계층 구조</span>로 OSI 7계층보다 단순화되어 있으며, 실제 인터넷에서 가장 널리 사용되는 프로토콜입니다! 🌐

### 주요 프로토콜

#### 응용 계층 프로토콜 `HTTPTELFTP`{:.success}

##### HTTP (HyperText Transfer Protocol)
* <span class="blue-text">웹(WWW)에서 HTML로 작성된 하이퍼텍스트 문서를 전송하기 위한 표준 프로토콜</span>
* 1989년 <span class="yellow-code">버너스리(Berners-Lee)</span>가 WWW를 고안하면서 설계
* <span class="blue-text">HTTPS (HyperText Transfer Protocol Secure)</span>: HTTP의 단점을 보완하고, 안전한 통신을 위해 SSL/TLS의 인증, 암호화 기능을 지원

##### TELNET
* <span class="blue-text">멀리 떨어져 있는 컴퓨터에 접속하여 자신의 컴퓨터처럼 사용할 수 있도록 해주는 서비스</span>
* 프로그램을 실행하는 등 시스템 관리 작업을 할 수 있는 <span class="blue-text">가상의 터미널(Virtual Terminal)</span> 기능을 수행

##### FTP (File Transfer Protocol)
* <span class="blue-text">컴퓨터와 컴퓨터 또는 컴퓨터와 인터넷 사이에서 파일을 주고받을 수 있도록 하는 원격 파일 전송 프로토콜</span>

##### SMTP (Simple Mail Transfer Protocol)
* <span class="blue-text">전자 우편(E-Mail)을 전송하는 프로토콜</span> (보내기)

##### IMAP (Internet Messaging Access Protocol)
* <span class="blue-text">로컬 서버에서 프로그램을 이용하여 전자 우편을 액세스하기 위한 표준 프로토콜</span> (받기)

##### SNMP (Simple Network Management Protocol)
* <span class="blue-text">TCP/IP의 네트워크 관리 프로토콜</span>로, 라우터나 허브 등 네트워크 기기의 네트워크 정보를 네트워크 관리 시스템에 보내는 데 사용되는 표준 통신 규약

##### SSH (Secure Shell)
* <span class="blue-text">다른 네트워크상의 컴퓨터에 원격 접속하거나 파일을 복사할 수 있게 해주는 응용 프로토콜</span>
* <span class="yellow-code">22번 포트</span>를 사용
* rsh, rcp, rlogin, rexec 및 TELNET, FTP 서비스 등을 대체하기 위한 <span class="blue-text">네트워크 보안 도구</span> (TELNET 강화)

#### 전송 계층 프로토콜 `UDPRTCP`{:.success}

##### UDP (User Datagram Protocol)
* <span class="blue-text">비연결형 서비스</span>로 데이터 전송 전에 연결을 설정하지 않음
* TCP보다 <span class="blue-text">간단한 헤더 구조</span>로 오버헤드가 적음
* <span class="blue-text">흐름 제어나 순서 제어가 없어</span> 전송 속도가 빠름
* <span class="red-text">확인은 안함</span> (신뢰성 낮음)

##### RTCP (Real-Time Control Protocol)
* <span class="blue-text">RTP(Real-time Transport Protocol) 패킷의 전송 품질을 제어하기 위한 제어 프로토콜</span>
* 데이터 전송을 모니터링하고 최소한의 제어 및 인증 기능을 제공

#### 인터넷 계층 프로토콜 `ICMPIGMP`{:.success}

##### ICMP (Internet Control Message Protocol)
* <span class="blue-text">IP와 함께 동작하여 통신 중 오류의 처리와 전송 경로 변경을 위한 제어 메시지를 관리</span>
* <span class="yellow-code">헤더는 8바이트</span>
* <span class="blue-text">네트워크 상태 알림</span> 기능

##### IGMP (Internet Group Management Protocol)
* <span class="blue-text">멀티캐스트를 지원하는 호스트나 라우터 간에 멀티캐스트 그룹을 유지</span>하는 데 사용

#### 네트워크 진단 도구 `ping`{:.success}

##### ping
* <span class="blue-text">특정 호스트가 현재 네트워크에 연결되어 정상적으로 동작하는지 확인</span>하는 서비스
* <span class="blue-text">ICMP를 사용하여 특정 호스트에 대한 연결성을 확인</span>

#### 주소 변환 프로토콜 `ARPRARPDHCP`{:.success}

##### ARP (Address Resolution Protocol)
* <span class="blue-text">호스트의 IP 주소를 해당 호스트에 연결된 네트워크 액세스 장치의 물리 주소(MAC Address)로 변환</span>
* <span class="yellow-code">IP → MAC</span> 변환

##### RARP (Reverse Address Resolution Protocol)
* <span class="blue-text">물리 주소를 IP 주소로 변환하는 기능</span>으로, ARP와 반대
* <span class="yellow-code">MAC → IP</span> 변환

##### DHCP (Dynamic Host Configuration Protocol)
* <span class="blue-text">IP 주소 부족 문제를 해결하기 위해 만들어진 프로토콜</span>
* <span class="blue-text">일정 기간 동안 IP 주소를 임대</span>하여 사용 가능한 IP 주소 수보다 더 많은 컴퓨터가 IP 주소를 활용할 수 있게 함
* <span class="yellow-code">자동 IP 할당</span>

> 💡 **팁**: <span class="blue-text">각 프로토콜은 특정 계층에서 동작</span>하며, 서로 다른 목적과 기능을 가지고 있습니다! 네트워크 통신의 각 단계에서 적절한 프로토콜이 사용됩니다! 🌐
