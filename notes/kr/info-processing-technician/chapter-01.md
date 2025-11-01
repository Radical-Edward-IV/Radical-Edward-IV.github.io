---
layout: article
title: 1. 응용 SW 기초 기술 활용
permalink: /notes/kr/info-processing-technician/chapter-01
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기능사 실기 강의 노트, 응용 SW 기초 기술 활용 개념과 활용 방법을 다룹니다.
keywords: "정보처리기능사, 실기, 응용 SW 기초 기술 활용, 데이터 처리, 프로그래밍"
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

## 1. 운영체제의 개념 :star::star: 
### 운영체제(OS; Operating System)의 정의
운영체제는 컴퓨터 시스템의 <span class="blue-text">자원들을 효율적으로 관리</span>하는 여러 프로그램의 모임이다.   
<span class="blue-text">사용자와 하드웨어 간의 인터페이스</span>로 동작하는 <span class="blue-text">시스템 소프트웨어</span>의 일종이다.

### 운영체제의 목적 `처신반사`{:.success} 
<span class="blue-text">처리 능력</span>, <span class="blue-text">신뢰성</span>, <span class="blue-text">반환 시간</span>, <span class="blue-text">사용 가능도</span>
> 💡 **팁**: 운영체제의 성능을 평가하는 기준!


### 운영체제의 구성 `제작감자 처서문어`{:.success}
<span class="blue-text">제어 프로그램</span>(Control Program)
- <span class="blue-text">작업 제어 프로그램</span>, <span class="blue-text">감시 프로그램</span>, <span class="blue-text">자료 관리 프로그램</span>   


<span class="blue-text">처리 프로그램</span>(Processing Program)
- <span class="blue-text">서비스 프로그램</span>, <span class="blue-text">문제 프로그램</span>, <span class="blue-text">언어 번역 프로그램</span>


### 운영체제의 종류 `W U LI M A M I`{:.success}
<span class="blue-text">Windows</span>, <span class="blue-text">UNIX</span>, <span class="blue-text">LINUX</span>, <span class="blue-text">MacOS</span>, <span class="blue-text">MS_DOS</span>, <span class="blue-text">Android</span>, <span class="blue-text">iOS</span>

### 운영체제 운영 기법의 발달 과정 `일다시실범분`{:.success}
<span class="blue-text">일괄 처리 시스템</span> → <span class="blue-text">다중 프로그래밍 시스템</span> → <span class="blue-text">시분할 시스템</span> → <span class="blue-text">다중 처리 시스템</span> → <span class="blue-text">실시간 처리 시스템</span> → <span class="blue-text">범용 시스템</span> → <span class="blue-text">분산 처리 시스템</span>

<summary>🌟 각 과정 핵심 한눈에 보기</summary>

| 발달과정(시스템 명칭) | 핵심 특징 |
|----------------------|----------|
| 일괄처리(Batch) | 작업을 모아 한 번에 처리 |
| 다중 프로그래밍(Multiprogramming) | CPU 활용 극대화 |
| 시분할(Time-sharing) | 사용자 체감 동시 사용 |
| 다중 처리(Multiprocessing) | 여러 CPU 병렬 처리 |
| 실시간(Real-time) | 응답 기한 반드시 준수 |
| 범용(General-purpose) | 다양한 작업 가능 |
| 분산 처리(Distributed) | 여러 컴퓨터 공동 처리 |




## 2. Windows :star::star::star:
### 최신 Windows의 특징 `그32선플DO파기향`{:.success}
Windows는 컴퓨터 시스템의 <span class="blue-text">하드웨어를 효율적으로 관리</span>하고, 사용자가 컴퓨터를 쉽게 사용할 수 있도록 <span class="blue-text">인터페이스를 제공</span>하는 <span class="blue-text">운영체제</span>이다.

* <span class="blue-text">그래픽 사용자 인터페이스(GUI)</span> 사용
* <span class="blue-text">선점형 멀티태스킹</span>
* <span class="blue-text">32비트 또는 64비트</span> 데이터 처리
* <span class="blue-text">FAT32 파일 시스템</span>
* <span class="blue-text">플러그 앤 플레이(PnP)</span>
* <span class="blue-text">OLE(Object Linking and Embedding)</span>
* <span class="blue-text">255자의 긴 파일 이름</span>
* <span class="blue-text">향상된 네트워크 기능</span>
* <span class="blue-text">DOS와 호환</span>

### 바로 가기 키(단축키)

| 바로 가기 키         | 기능                      |
|----------------------|---------------------------|
| Alt + F4             | 현재 창 또는 프로그램 종료 |
| Shift + Delete       | 휴지통 거치지 않고 바로 삭제 |
| Win + 0 ~ 9          | 작업 표시줄의 해당 순서 앱 실행 |
| Win + D              | 바탕화면 보기/숨기기 토글 |
| Win + E              | 파일 탐색기 열기           |
| Win + L              | 화면 잠금                 |
| Win + P              | 화면 출력 모드 전환(프로젝터 등) |
| Win + Ctrl + D       | 새 가상 데스크톱 추가      |
| Win + Ctrl + F4      | 현재 가상 데스크톱 닫기    |
| Win + Shift + S      | 화면 캡처(스니핑 툴)       |
| Win + V              | 클립보드 기록 보기         |

## 3. UNIX / LINUX :star::star:
### UNIX의 개요 및 특징
UNIX는 1960년대 <span class="blue-text">AT&T 벨 연구소</span>, <span class="blue-text">MIT</span>, <span class="blue-text">General Electric</span>이 공동 개발한 운영체제
* <span class="blue-text">시분할 시스템</span>을 위해 설계된 <span class="blue-text">대화식 운영체제</span>
* <span class="blue-text">소스가 공개된 개방형 시스템</span>
* 대부분 <span class="blue-text">C 언어</span>로 작성
* <span class="blue-text">크기가 작아 가벼움</span>
* <span class="blue-text">Multi-User, Multi-Tasking</span> 지원
* <span class="blue-text">많은 네트워킹 기능</span> 제공
* <span class="blue-text">계층적 트리 구조의 파일 시스템</span>
* <span class="blue-text">표준 입/출력</span>을 통해 <span class="blue-text">명령어 파이프 라인</span> 구성

### UNIX 시스템의 구성 `커쉘유`{:.success}


| 요소 | 특징 |
|------|------| 
| <span class="blue-text">커널(Kernel)</span> | <span class="blue-text">UNIX의 가장 핵심</span>적인 부분<br/>컴퓨터 부팅될 때 주기억장치 적재 후 상주하면서 실행<br/>하드웨어 보호 및 프로그램과 하드웨어간 인터페이스<br/>프로세스 관리, 기억장치 관리, 파일 관리, 입/출력 관리, 데이터 전송 및 변환 등 여러 가지 기능 수행 |
| <span class="blue-text">쉘(Shell)</span> | <span class="blue-text">사용자와 커널 사이의 인터페이스</span> 역할<br/><span class="blue-text">명령어 해석 및 실행</span><br/>다양한 쉘 종류: <span class="blue-text">Bourne Shell</span>, <span class="blue-text">C Shell</span>, <span class="blue-text">Korn Shell</span>, <span class="blue-text">Bash</span> 등 |
| <span class="blue-text">유틸리티 프로그램</span> | <span class="blue-text">시스템 관리</span> 및 <span class="blue-text">사용자 작업</span>을 위한 <span class="blue-text">보조 프로그램</span><br/><span class="blue-text">파일 조작</span>, <span class="blue-text">텍스트 처리</span>, <span class="blue-text">네트워크 관리</span> 등<br/><span class="blue-text">ls</span>, <span class="blue-text">cp</span>, <span class="blue-text">mv</span>, <span class="blue-text">grep</span>, <span class="blue-text">awk</span>, <span class="blue-text">sed</span> 등 |



### LINUX의 개요 및 특징
LINUX는 1991년대 <span class="blue-text">리누스 토발즈</span>가 <span class="blue-text">UNIX를 기반</span>으로 개발한 운영체제
* <span class="blue-text">커널 재배포 허용</span>
* <span class="blue-text">커널 및 소스 공개</span>
* <span class="blue-text">UNIX와 완벽히 호환</span>
* 대부분의 특징이 <span class="blue-text">UNIX와 동일</span>

## 4. 운영체제의 기본 명령어 :star::star::star:

### 운영체제 기본 명령어 개요
운영체제는 CLI와 GUI로 제어할 수 있음
* <span class="blue-text">CLI</span>(Command Line Interface): 키보드로 명령어를 직접 입력하여 작업 수행
* <span class="blue-text">GUI</span>(Graphical User Interface): 마우스로 아이콘이나 메뉴를 선택하여 작업을 수행

### Windows 기본 명령어

#### CLI 기본 명령어
명령 프롬프트 창에 명령어를 입력하여 작업 수행

| 명령어 | 기능 | 예시 |
|--------|------|------|
| `dir` | 디렉토리 내용 보기 | `dir C:\` |
| `copy` | 파일 복사 | `copy file1.txt file2.txt` |
| `del` | 파일 삭제 | `del file.txt` |
| `md` | 디렉토리 생성 | `md newfolder` |
| `cd` | 디렉토리 이동 | `cd C:\Windows` |



<summary>🌟 Windows CLI 명령어 요약표 </summary>

| 파일/디렉토리 관리 | 설명 | 정보확인/네트워크 | 설명 | 시스템 제어/유틸 | 설명 |
|----------------|------|------------------|------|----------------|------|
| dir | 목록 출력 | ipconfig | IP 정보 확인 | tasklist | 프로세스 목록 |
| copy | 파일 복사 | ping | 네트워크 연결 테스트 | taskkill | 프로세스 종료 |
| move | 이동/이름 변경 | tracert | 경로 추적 | cls | 화면 지우기 |
| del | 파일 삭제 | systeminfo | OS 환경 정보 | shutdown | 시스템 종료/재부팅 |
| md / mkdir | 디렉토리 생성 | netstat | 포트/통신 확인 | sfc | 시스템 파일 검사 |
| cd / chdir | 디렉토리 이동 | arp | MAC/IP 변환 정보 | sc | 서비스 제어 |
| ren | 파일 이름 변경 | nslookup | DNS 조회 | driverquery | 드라이버 목록 |
| rd / rmdir | 디렉토리 삭제 | hostname | 호스트명 표시 | reg | 레지스트리 관리 |



#### GUI 기본 명령어
바탕 화면이나 Windows 탐색기에서 마우스로 아이콘을 클릭하여 실행

### UNIX/LINUX 기본 명령어

#### CLI 기본 명령어
쉘(Shell)에 명령어를 입력하여 작업 수행

| 명령어 | 기능 | 예시 |
|--------|------|------|
| `ls` | 디렉토리 내용 보기 | `ls -la` |
| `cat` | 파일 내용 보기 | `cat file.txt` |
| `rm` | 파일 삭제 | `rm file.txt` |
| `chmod` | 파일 권한 변경 | `chmod 755 file.txt` |
| `pwd` | 현재 디렉토리 경로 보기 | `pwd` |


<summary>🌟 Unix 명령어 요약표 </summary>

| 파일 관리 | 설명 | 텍스트/로그 처리 | 설명 | 시스템/권한 관리 | 설명 |
|----------|------|-----------------|------|----------------|------|
| ls | 목록 출력 | grep | 패턴 검색 | ps | 프로세스 목록 |
| cp | 파일 복사 | awk | 필드 기반 처리 | kill | 프로세스 종료 |
| mv | 이동/이름 변경 | sed | 스트림 편집 | chmod | 권한 변경 |
| rm | 파일 삭제 | head | 앞부분 출력 | chown | 소유자 변경 |
| mkdir | 디렉토리 생성 | tail | 뒷부분 출력 | | |
| pwd | 현재 위치 | cat | 내용 출력 | | |
| cd | 디렉토리 이동 | find | 검색 | | |
| rmdir | 디렉토리 삭제 | tar | 압축/묶기 | | |




#### GUI 기본 명령어
UNIX와 LINUX는 기본적으로 CLI를 사용하지만, X Window라는 별도의 프로그램을 설치하여 GUI 방식으로 운영 가능

## 5. 프로세스 관리 및 스케줄링 :star::star:
### 프로세스(Process)의 정의 `실실프프비운PCB`{:.success}
프로세스는 일반적으로 <span class="blue-text">프로세서(처리기, CPU)</span>에 의해 처리되는 <span class="blue-text">사용자 프로그램</span>, 즉 <span class="blue-text">실행중인 프로그램</span>을 의미하며, <span class="blue-text">작업(Job)</span> 또는 <span class="blue-text">태스크(Task)</span>라고도 한다.

* <span class="blue-text">실기억장치에 저장된 프로그램</span>
* <span class="blue-text">프로세서가 할당되는 실체</span>
* <span class="blue-text">프로시저가 활동중인 것</span>
* <span class="blue-text">운영체제가 관리하는 실행 단위</span>
* <span class="blue-text">실행중인 프로그램</span>
* <span class="blue-text">PCB를 가진 프로그램</span>
* <span class="blue-text">비동기적 행위를 일으키는 주체</span>

### 프로세스 상태 전이

<figure>
    <img src="/notes/assets/info-processing-technician/chapter-01-01.png" alt="프로세스 상태 전이">
    <figcaption>프로세스 상태 전이</figcaption>
</figure>

* <span class="blue-text">제출(Submit)</span>: 작업 처리를 위해 사용자가 작업을 시스템에 제출
* <span class="blue-text">접수(Hold)</span>: 제출된 작업이 <span class="blue-text">스풀 공간</span>에 저장된 상태
* <span class="blue-text">준비(Ready)</span>: 스케줄러에 의해 프로세서에 할당될 준비가 된 상태 (<span class="blue-text">준비상태 큐</span>)
* <span class="blue-text">실행(Running)</span>: 프로세서에 할당되어 실행 중인 상태
* <span class="blue-text">대기(Waiting)</span>: 실행 중인 프로세스가 <span class="blue-text">입출력</span> 등의 이유로 대기 중인 상태
* <span class="blue-text">종료(Terminate)</span>: 작업 처리가 완료된 상태

### 스케줄링
스케줄링은 프로세스가 생성되어 실행될 때 필요한 시스템의 여러 자원을 해당 프로세스에게 할당하는 작업을 의미하며, 이를 수행하는 것을 <span class="blue-text">스케줄러</span>라 함.

* 프로세스가 생성되어 완료될 때까지 프로세스는 여러 종류의 스케줄링 과정을 거침
* 프로세스 스케줄링 기법에는 <span class="blue-text">비선점(Non-preemptive)</span> 스케줄링과 <span class="blue-text">선점(Preemptive)</span> 스케줄링이 있다


#### 비선점 스케줄링 `FSHP`{:.success}
이미 할당된 <span class="blue-text">CPU</span>를 다른 프로세스가 <span class="blue-text">강제로 빼앗아 사용할 수 없는</span> 스케줄링 기법

| 기법 | 설명 | 특징 |
|------|------|------|
| <span class="blue-text">F</span>CFS | First Come First Served<br/>준비상태 큐에 도착한 순서에 따라 차례로 CPU 할당 | FIFO 방식, 공정하지만 긴 작업이 있으면 대기시간 증가 |
| <span class="blue-text">S</span>JF | Shortest Job First<br/>실행 시간이 가장 짧은 프로세스에게 먼저 CPU 할당 | 평균 대기시간 최소화, 기아현상 발생 가능 |
| <span class="blue-text">H</span>RRN | Highest Response Ratio Next<br/>대기 시간과 서비스 실행 시간을 이용하는 기법 | SJF의 기아현상 보완, 응답비율 계산 |
| <span class="blue-text">P</span>S(우선순위) | Priority Scheduling<br/>가장 높은 우선순위 프로세스에게 먼저 CPU 할당 | 우선순위에 따른 처리, 기아현상 발생 가능 |

#### 선점 스케줄링 `SR다다`{:.success}
<span class="blue-text">우선순위가 높은</span> 다른 프로세스가 <span class="blue-text">CPU를 강제로 빼앗아 사용할 수 있는</span> 스케줄링 기법

| 기법 | 설명 | 특징 |
|------|------|------|
| <span class="blue-text">SRT</span> | <span class="blue-text">Shortest Remaining Time</span><br/>남은 실행 시간이 가장 짧은 프로세스에게 CPU 할당 | SJF의 선점 버전, 동적 우선순위 |
| <span class="blue-text">RR</span> | <span class="blue-text">Round Robin</span><br/>시간 할당량(Time Quantum)을 정하여 순환 방식으로 CPU 할당 | 공정한 처리, 대화형 시스템에 적합 |
| <span class="blue-text">다단계 큐</span> | <span class="blue-text">Multi-level Queue</span><br/>프로세스를 여러 그룹으로 분류하여 각각 다른 큐에서 관리 | 프로세스 유형별 차별적 처리 |
| <span class="blue-text">다단계 피드백 큐</span> | <span class="blue-text">Multi-level Feedback Queue</span><br/>프로세스가 큐 간 이동 가능한 다단계 큐 | 동적 우선순위 조정, 복잡하지만 유연함 |
