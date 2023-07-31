---
layout: article
title: 2. 화면 설계
permalink: /notes/kr/info-processing-engineer/chapter-02
key: notes
sidebar:
  nav: notes-kr
---

## UI 요구사항 확인
### UI 요구사항 확인 :star::star::star:

* **UI**
    - **개념:** **사용자**와 **시스템** 사이에서 **의사소통**할 수 있도록 고안된 **물리적**, **가상의 매개체**

        + **UX:** 제품과 시스템 등을 사용자가 경험하면서 느끼고 생각하는 총체적 경험

    - **유형:** **C**LI(정적 텍스트), **G**UI(그래픽 반응), **N**UI(직관적 사용자 반응), **O**UI(유기적 상호 작용) `#CGNO`{:.info}

    - **분야:** 물리적 제어 분야, 디자인적 분야, 기능적 분야

    - **설계 원칙:** **직**관성, **유**효성, **학**습성, **유**연성 `#직유학유`{:.info}

    - **설계 지침:** **사**용자 중심, **일**관성, **단**순성, **결**과 예측 가능성, **가**시성, **표**준화, **접**근성, **명**확성, **오**류 발생 해결 `#사일단결 가표접명오`{:.info}

* **UI 요구사항 확인**

    - **구분:** 기능적 요구사항, 비기능적 요구사항

    - **UI 품질 요구사항(ISO/IEC 9126 기반):** **기능성**(적정성, 정밀성, 상호운용성, 보안성, 호환성), **신뢰성**(성숙성, 고장 허용성, 회복성), **사용성**(이해성, 학습성, 운용성), **효율성**(시간 효율성, 자원 효율성), **유지보수성**(분석성, 변경성, 안정성, 시험성), **이식성**(적용성, 설치성, 대체성) `#기신사효유이`{:.info}

### UI 표준 :star:

* **UI 표준**

    - **개념:** 디자인 철학과 원칙, 정책 및 철학, UI 스타일 가이드, UI 패턴 모델 정의, UI 표준 수립을 위한 조직 구성으로 되어 있다.

    - **구성:** 전체적인 U**X** 원칙, **정**책 및 철학, UI **스**타일 가이드, UI **패**턴 모델 정의, UI 표준 수립을 위한 **조**직 구성 `#액정 스패조`{:.info}

### UI 지침 :star:

* **UI 지침**

    - **개념:** UI 표준에 따라 사용자 인터페이스 설계, 개발 시 지켜야할 세부 사항

    - **사용자 요구사항 도출 순서:** 페르소나 정의 → 콘셉트 모델 정의 → 사용자 요구사항 정의 → UI 컨셉션
    
* **UI 표준 적용을 위한 환경 분석**

* **UI 개발 목표 및 범위**

    - **UI 개발을 위한 주요 기법:** 3C 분석, SWOT 분석, 시나리오 플래닝, 사용성 테스트, 워크숍

### 스토리보드 :star::star:

* **개념:** UI 화면 설계를 위해서 **정책**이나 **프로세스 및 콘텐츠**의 **구성**, 와이어프레임 **등** 구축하는 서비스를 위한 **대부분의 정보가 수록된 문서**이다.

* **UI 화면 설계 구분:** **와**이어프레임, **스**토리보드, **프**로토타입 `#와스프`{:.info}

* **작성 절차:** 전체 개요 작성 → 서비스 흐름 작성 → 스타일 확정 → 메뉴별 화면 설계도 작성 및 상세 설명 → 추가 관련 정보 작성

### UI 프로토타입 제작 및 검토 :star:

* **UI 프로토타입 이해**

    - **개념:** **전체적인 기능**을 **간략**한 형태로 **구현**한 **시제품**

    - **장점:** 사용자 설득과 이해가 쉬움, 개발 시간 감소, 오류 사전 발견을 통한 예방 가능

    - **단점:** 수정 과정 증가 시 작업 시간 증가 위험, 필요 이상의 많은 자원 소모

### UI 설계를 위한 UML :star::star::star:

* **개념:** **객체 지향 소프트웨어** 개발 과정에서 **산출물**을 **명세화**, **시각화**, **문서화할 때 사용**되는 **표준화된 범용 모델링 언어**이다.

* **특징:** **가**시화 언어, **구**축 언어, **명**세화 언어, **문**서화 언어 `#가구명문`{:.info}

* **구성 요소:** **사**물, **관**계, **다**이어그램 `#사관다`{:.info}

    - **다이어그램의 구분**

        + **정적 다이어그램:** **클**래스, **객**체, **컴**포넌트, **배**치, **복**합체 구조, **패**키지 `#클객컴배복패`{:.info}<br>

            👉 **클래스 다이어그램 접근 제어자:** private(-), public(+), protected(#), default(~)   

            👉 **패키지 다이어그램 구성요소:** 패키지, 의존관계   

            👉 **컴포넌트 다이어그램 구성요소:** 컴포넌트, 인터페이스, 의존 관계

        + **동적 다이어그램:** **유**스케이스, **시**퀀스, **커**뮤니케이션, **상**태, **활**동, **타**이밍 `#유시커 상활타`{:.info}<br>

            👉 **유스케이스 다이어그램 구성요소:** 유스케이스, 액터, 시스템, 시나리오, 이벤트 흐름   

            👉 **시퀀스 다이어그램 구성요소:** 객체, 생명선, 실행, 메시지   

            👉 **커뮤니케이션 다이어그램 구성요소:** 액터, 객체, 링크, 메시지   

            👉 **상태 다이어그램 구성요소:** 상태, 시작 상태, 종료 상태, 전이, 이벤트, 전이 조건   

            👉 **활동 다이어그램 구성요소:** 시작점, 전이, 액션, 종료점, 조건 노드, 병합 노드, 포크 노드, 조인 노드, 구획면   

    - **관계의 구분:** **연**관, **의**존, **일**반화, **실**체화, **포**함, **집**합 `#연의 일실 포집`{:.info}

    - **확장 모델의 스테레오 타입:** ‘<<>>’(길러멧) 기호를 사용하여 표현한다.

        + **유형:** include, extends, interface, entity, boundary, control   *ex) <<include>>*

### UI 흐름 설계 :star:

* **UI 흐름 설계서**

    - **구성요소:** 표지, 개정 이력, 요구사항 정의, 시스템 구조, 사이트 맵, 프로세스 정의, 화면 설계

### UI 상세 설계 :star:

* **UI 상세 설계**

    - **프로세스:** UI 설계 시안을 토대로 실제 설계 및 구현을 위해서 모든 화면에 대한 UI 상세 설계 단계를 진행한다.

* **UI 시나리오 문서의 작성 요건:** **완**전성, **일**관성, **이**해성, **가**독성, **추**적 용이성, **수**정 용이성 `#완일이가 추수`{:.info}

### UI 설계 도구 :star:

* **유형:** **화면 설계 도구**(파워 목업, 발사믹 목업, 카카오 오븐), **프로토타이핑 도구**(UX핀, 액슈어, 네이버 프로토나우), **UI 디자인 도구**(스케치, 어도비 익스피리언스 디자인 CC), **디자인 산출물로 작업하는 프로토타이핑 도구**(인비전, 픽사에이트, 프레이머)