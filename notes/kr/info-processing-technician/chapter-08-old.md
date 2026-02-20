---
layout: article
title: 8. 애플리케이션 테스트 관리 (2)
permalink: /notes/kr/info-processing-technician/chapter-08
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 정보처리기능사 실기 강의 노트, 애플리케이션 테스트의 개념과 분류, 테스트 기법 및 단계별 테스트 방법을 다룹니다.
keywords: "정보처리기능사, 실기, 애플리케이션 테스트, 블랙박스 테스트, 화이트박스 테스트, 단위 테스트, 통합 테스트, 시스템 테스트, 인수 테스트"
---

<style>
    /* 색상 활용 규칙
      빨강: 주의, 경고, 위험 (결함, 오류 등)
      파랑: 핵심 개념, 주요 기능 (테스트 종류, 검증 기준 등)
      초록: 안전한 대안, 긍정적 결과 (검증, 확인 등)
      노랑: 코드 요소 (테스트 기법명, 메서드명 등)
    */
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%EC%A0%95%EB%B3%B4%EC%B2%98%EB%A6%AC%EA%B8%B0%EB%8A%A5%EC%82%AC&reversal=false&textBg=false)

통합 테스트는 개별 모듈을 결합하여 시스템으로 완성하는 과정에서 수행하는 테스트입니다.
<span class="blue-text">상향식</span>, <span class="blue-text">하향식</span>, <span class="blue-text">혼합식</span> 통합 방법을 이해하고, 테스트 자동화 도구를 활용하여 효율적으로 테스트를 수행할 수 있어야 합니다!

## 1. 통합 테스트 :star:

> 💡 **전문가의 조언**: 통합 테스트에서는 특히 상향식 테스트와 하향식 테스트의 차이점을 명확히 이해해야 합니다. 스텁(Stub)과 드라이버(Driver)의 역할, 각 방식의 장단점을 구분할 수 있어야 시험에서 좋은 점수를 받을 수 있습니다.

### 통합 테스트의 방식

통합 테스트는 모듈을 결합하는 방식에 따라 <span class="blue-text">비점진적 통합 방식</span>과 <span class="blue-text">점진적 통합 방식</span>으로 구분됩니다.

| 통합 방식 | 설명 | 특징 |
|----------|------|------|
| <span class="blue-text">비점진적 통합</span> | • 모든 모듈을 한 번에 결합하여 전체 프로그램을 테스트<br/>• **빅뱅(Big-Bang) 통합** 방식이 대표적 | • 소규모 소프트웨어에 적합<br/>• 단시간 내 테스트 가능<br/>• <span class="red-text">오류 발견 및 위치 파악이 어려움</span> |
| <span class="blue-text">점진적 통합</span> | • 모듈을 단계적으로 통합하며 테스트<br/>• **하향식, 상향식, 혼합식** 방식 존재 | • <span class="green-text">오류 수정이 용이</span><br/>• 인터페이스 오류를 효과적으로 발견<br/>• 체계적인 테스트 가능 |

### 하향식 통합 테스트 (Top-Down Integration)

하향식 통합 테스트는 <span class="blue-text">상위 모듈에서 하위 모듈 방향</span>으로 통합하며 테스트하는 기법입니다.

#### 하향식 통합 테스트의 특징

- **주요 제어 모듈**을 중심으로 아래로 이동하며 통합
- **깊이 우선(Depth-First)** 또는 **넓이 우선(Breadth-First)** 방식 사용
- <span class="green-text">초기에 시스템 구조를 사용자에게 제시 가능</span>
- 상위 모듈에서는 테스트 케이스 적용이 어려움
- **스텁(Stub)** 필요: 하위 모듈을 대체하는 임시 모듈

#### 하향식 통합 절차

```
1단계: 주요 제어 모듈 작성, 하위 모듈은 스텁(Stub)으로 대체
   ↓
2단계: 깊이 우선 또는 넓이 우선 방식으로 스텁을 실제 모듈로 교체
   ↓
3단계: 모듈 통합 시마다 테스트 실시
   ↓
4단계: 회귀 테스트로 새로운 오류 발생 여부 확인
```

> 💡 **스텁(Stub)**: 하위 모듈을 대신하는 임시 모듈로, 상위 모듈의 호출에 대해 간단한 응답을 반환합니다.

### 상향식 통합 테스트 (Bottom-Up Integration)

상향식 통합 테스트는 <span class="blue-text">하위 모듈에서 상위 모듈 방향</span>으로 통합하며 테스트하는 기법입니다.

#### 상향식 통합 테스트의 특징

- 최하위 모듈부터 통합 및 테스트 수행
- **스텁(Stub)은 불필요**, 대신 **드라이버(Driver)** 필요
- **클러스터(Cluster)**: 주요 제어 모듈과 관련된 종속 모듈의 그룹

#### 상향식 통합 절차

```
1단계: 하위 모듈들을 클러스터(Cluster)로 결합
   ↓
2단계: 상위 모듈의 역할을 수행할 드라이버(Driver) 작성
   ↓
3단계: 클러스터 단위로 테스트 수행
   ↓
4단계: 테스트 완료 후 클러스터를 상위로 이동, 드라이버를 실제 모듈로 교체
```

> 💡 **드라이버(Driver)**: 상위 모듈을 대신하는 임시 모듈로, 하위 모듈을 호출하고 테스트 데이터를 전달합니다.

### 통합 테스트 방식 비교

| 구분 | 하향식 | 상향식 |
|------|--------|--------|
| **진행 방향** | 상위 → 하위 | 하위 → 상위 |
| **필요한 도구** | 스텁(Stub) | 드라이버(Driver) |
| **장점** | • 초기에 시스템 구조 파악 가능<br/>• 주요 제어 기능을 먼저 테스트 | • 하위 모듈의 정확한 테스트 가능<br/>• 모듈 개발과 병행 가능 |
| **단점** | • 하위 모듈 테스트 불충분<br/>• 많은 스텁 필요 | • 전체 시스템 파악 어려움<br/>• 많은 드라이버 필요 |

### 혼합식 통합 테스트

혼합식 통합 테스트는 하향식과 상향식을 <span class="blue-text">조합</span>한 방식으로, **샌드위치(Sandwich) 통합**이라고도 합니다.

- 하위 레벨: 상향식 통합 적용
- 상위 레벨: 하향식 통합 적용
- 두 방식의 장점을 활용하여 최적의 테스트 지원

### 회귀 테스트 (Regression Test)

회귀 테스트는 <span class="blue-text">변경된 모듈이나 컴포넌트에 새로운 오류가 없는지</span> 확인하는 테스트입니다.

#### 회귀 테스트의 목적

- 수정한 모듈이 다른 부분에 <span class="red-text">부작용</span>을 일으키지 않는지 검증
- 새로운 오류가 발생하지 않음을 보증
- 이미 테스트된 프로그램의 반복 테스트

#### 회귀 테스트 케이스 선정 방법

| 선정 기준 | 설명 |
|----------|------|
| <span class="yellow-code">대표 테스트 케이스</span> | 애플리케이션의 모든 기능을 수행할 수 있는 대표 케이스 선정 |
| <span class="yellow-code">파급 효과 분석</span> | 변경에 따른 파급 효과가 높은 부분의 테스트 케이스 선정 |
| <span class="yellow-code">실제 수정 영역</span> | 실제로 수정이 발생한 모듈의 테스트 케이스 선정 |

> 💡 **팁**: 모든 테스트 케이스로 회귀 테스트를 수행하는 것이 이상적이지만, 시간과 비용을 고려하여 선별적으로 수행합니다.

## 2. 애플리케이션 테스트 프로세스

애플리케이션 테스트는 효과적으로 수행하기 위해 <span class="blue-text">체계적인 절차</span>를 따라야 합니다.

### 테스트 프로세스 흐름

```
테스트 계획
    ↓
테스트 분석 및 디자인
    ↓
테스트 케이스 및 시나리오 작성
    ↓
테스트 수행
    ↓
테스트 결과 평가 및 리포팅
    ↓
결함 추적 및 관리
```

### 테스트 산출물

| 산출물 | 설명 |
|--------|------|
| <span class="blue-text">테스트 계획서</span> | 테스트 목적, 범위, 일정, 수행 절차, 대상 시스템, 조직 역할 등을 정의한 문서 |
| <span class="blue-text">테스트 케이스</span> | 입력 값, 실행 조건, 기대 결과 등으로 구성된 테스트 항목의 명세서 |
| <span class="blue-text">테스트 시나리오</span> | 여러 테스트 케이스의 실행 순서를 기술한 문서 |
| <span class="blue-text">테스트 결과서</span> | 테스트 결과를 비교·분석한 내용을 정리한 문서 |

### 테스트 계획 단계

테스트 계획 단계에서는 프로젝트 계획서와 요구 명세서를 기반으로 테스트를 준비합니다.

#### 주요 활동

- **테스트 목표 정의**: 무엇을 테스트할 것인가
- **테스트 대상 및 범위 결정**: 어디까지 테스트할 것인가
- **시스템 구조 파악**: 대상 시스템의 아키텍처 이해
- **자원 산정**: 조직, 인력, 비용 계획
- **조건 정의**: 시작 조건과 종료 조건 설정

#### 테스트 조건 정의

| 조건 | 설명 | 예시 |
|------|------|------|
| <span class="green-text">시작 조건</span> | 테스트를 시작할 수 있는 상태 | • 테스트 계획 완료<br/>• 테스트 환경 구축 완료<br/>• 테스트 명세서 작성 완료<br/>• 투입 인력 역할 정의 완료 |
| <span class="green-text">종료 조건</span> | 테스트를 종료하는 기준 | • 정상적으로 테스트 완료<br/>• 테스트 일정 만료<br/>• 테스트 비용 소진 |

> 💡 **참고**: 업무 기능의 중요도에 따라 시작·종료 조건을 다르게 지정할 수 있습니다.

## 3. 테스트 케이스 / 테스트 시나리오 / 테스트 오라클 :star:

> 💡 **전문가의 조언**: 테스트 케이스는 "무엇을" 테스트할지 정의하고, 테스트 시나리오는 "어떤 순서로" 테스트할지 정의하며, 테스트 오라클은 "결과가 옳은지" 판단하는 도구입니다. 이 세 가지 개념을 명확히 구분해야 합니다.

### 테스트 케이스 (Test Case)

테스트 케이스는 소프트웨어가 <span class="blue-text">요구사항을 정확히 준수</span>했는지 확인하기 위한 명세서입니다.

#### 테스트 케이스의 구성 요소

- **입력 값**: 테스트에 사용할 데이터
- **실행 조건**: 테스트를 수행하기 위한 환경 및 전제 조건
- **기대 결과**: 예상되는 출력 및 동작

#### 테스트 케이스 작성의 장점

- <span class="green-text">테스트 오류 방지</span>
- 인력, 시간 등 자원 낭비 감소
- 체계적인 테스트 수행 가능

> 💡 **팁**: 가장 이상적인 테스트 케이스는 시스템 설계 단계에서 작성하는 것입니다!

### 테스트 케이스 작성 절차

| 단계 | 주요 활동 |
|------|----------|
| <span class="blue-text">1. 테스트 계획 검토</span> | • 테스트 계획서 재검토<br/>• 테스트 대상 범위 및 접근 방법 파악<br/>• 요구사항 및 기능 명세서 검토 |
| <span class="blue-text">2. 위험 평가</span> | • 결함의 위험도에 따른 우선순위 결정<br/>• 중점 테스트 영역 선정 |
| <span class="blue-text">3. 테스트 요구사항 정의</span> | • 사용자 요구사항 재검토<br/>• 테스트 특성, 조건, 기능 분석 |
| <span class="blue-text">4. 테스트 구조 설계</span> | • 테스트 케이스 형식 및 분류 방법 결정<br/>• 테스트 절차, 장비, 도구 선정<br/>• 문서화 방법 결정 |
| <span class="blue-text">5. 테스트 케이스 작성</span> | • 요구사항별 테스트 케이스 작성<br/>• 입력 값, 실행 조건, 예상 결과 기술 |
| <span class="blue-text">6. 타당성 확인 및 유지보수</span> | • 기능 또는 환경 변화에 따른 갱신<br/>• 테스트 케이스 유용성 검토 |

### 테스트 시나리오 (Test Scenario)

테스트 시나리오는 <span class="blue-text">여러 테스트 케이스의 실행 순서</span>를 정의한 문서입니다.

#### 테스트 시나리오의 특징

- 구체적인 절차, 사전 조건, 입력 데이터 포함
- 테스트 항목을 빠짐없이 수행하도록 순서 지정
- 시스템별, 모듈별, 항목별로 분리 작성

#### 테스트 시나리오 작성 시 유의사항

| 유의사항 | 설명 |
|----------|------|
| <span class="yellow-code">분리 작성</span> | 시스템별, 모듈별, 항목별로 여러 시나리오로 분리 |
| <span class="yellow-code">문서 기반</span> | 요구사항과 설계 문서를 토대로 작성 |
| <span class="yellow-code">항목 구성</span> | 식별자, 순서 번호, 테스트 데이터, 테스트 케이스, 예상 결과, 확인 사항 포함 |
| <span class="yellow-code">업무 흐름</span> | 유스케이스 간 업무 흐름의 정상 동작 여부 확인 가능하도록 작성 |
| <span class="yellow-code">모듈 연계</span> | 모듈 또는 프로그램 간 연계가 정상 동작하는지 확인 가능하도록 작성 |

### 테스트 오라클 (Test Oracle)

테스트 오라클은 <span class="blue-text">테스트 결과의 정확성을 판단</span>하기 위해 사전 정의된 참 값과 비교하는 기법입니다.

#### 테스트 오라클의 특징

- **제한된 검증**: 모든 테스트 케이스에 적용할 수 없음
- **수학적 기법**: 오라클 값을 수학적으로 계산 가능
- **자동화 가능**: 실행, 비교, 커버리지 측정 자동화 지원

### 테스트 오라클의 종류

| 오라클 유형 | 설명 |
|------------|------|
| <span class="blue-text">참(True) 오라클</span> | • 모든 테스트 케이스의 입력 값에 대해 기대 결과 제공<br/>• 발생된 모든 오류 검출 가능<br/>• 가장 이상적이지만 구현이 어려움 |
| <span class="blue-text">샘플링(Sampling) 오라클</span> | • 특정 몇몇 테스트 케이스에 대해서만 기대 결과 제공<br/>• 일부 입력 값에 대해서만 정확성 검증 |
| <span class="blue-text">추정(Heuristic) 오라클</span> | • 샘플링 오라클을 개선한 형태<br/>• 특정 케이스는 정확한 결과, 나머지는 추정으로 처리 |
| <span class="blue-text">일관성 검사(Consistent) 오라클</span> | • 애플리케이션 변경 시 수행 전후 결과 비교<br/>• 변경 전후의 일관성 확인 |

## 4. 테스트 자동화 도구 :star:

> 💡 **전문가의 조언**: 테스트 자동화는 반복적인 작업을 효율화하고 휴먼 에러를 줄이는 핵심 기술입니다. 도구의 유형과 특징을 이해하고, 프로젝트에 적합한 도구를 선택할 수 있어야 합니다.

### 테스트 자동화의 개념

테스트 자동화는 <span class="blue-text">반복적인 테스트 절차를 스크립트로 구현</span>하여 효율적으로 수행하는 것입니다.

#### 테스트 자동화의 효과

- 휴먼 에러 감소
- 테스트 정확성 유지
- 테스트 품질 향상

### 테스트 자동화 도구의 장단점

#### 장점 ✅

- <span class="green-text">반복 작업 자동화</span>로 인력과 시간 절감
- 다중 플랫폼 호환성 등 <span class="green-text">향상된 품질 보장</span>
- 요구사항의 <span class="green-text">일관성 있는 검증</span>
- 테스트 결과를 그래프 등 <span class="green-text">다양한 형태로 제공</span>
- UI 없는 서비스도 정밀 테스트 가능

#### 단점 ⚠️

- 도구 사용법에 대한 <span class="red-text">교육 및 학습 필요</span>
- 프로세스 적용을 위한 <span class="red-text">시간과 노력 소요</span>
- 상용 도구의 경우 <span class="red-text">고가의 비용 발생</span>

### 테스트 자동화 수행 시 고려사항

| 고려사항 | 설명 |
|----------|------|
| <span class="yellow-code">테스트 절차 검토</span> | 재사용 및 측정이 불가능한 테스트는 제외 |
| <span class="yellow-code">적절한 도구 선택</span> | 모든 과정을 자동화할 수 있는 도구는 없으므로 용도에 맞는 도구 선택 |
| <span class="yellow-code">일정 계획</span> | 도구의 환경 설정 및 습득 기간을 고려한 계획 수립 |
| <span class="yellow-code">인력 투입 시기</span> | 테스트 엔지니어를 프로젝트 초기에 투입하여 이해도 향상 |

### 테스트 자동화 도구의 유형

| 도구 유형 | 설명 | 특징 |
|----------|------|------|
| <span class="blue-text">정적 분석 도구</span> | 프로그램을 실행하지 않고 소스 코드 분석 | • 코딩 표준, 스타일 검사<br/>• 코드 복잡도 측정<br/>• 잔존 결함 발견<br/>• 소스 코드 이해 필요 |
| <span class="blue-text">테스트 실행 도구</span> | 스크립트를 사용하여 테스트 자동 실행 | **데이터 주도 방식**<br/>• 스프레드시트에 테스트 데이터 저장<br/>• 동일 케이스로 다양한 데이터 반복 테스트<br/>• 스크립트 미숙자도 사용 가능<br/><br/>**키워드 주도 방식**<br/>• 동작을 나타내는 키워드와 데이터 저장<br/>• 키워드 기반 자동 실행 |
| <span class="blue-text">성능 테스트 도구</span> | 가상 사용자를 생성하여 성능 측정 | • 처리량, 응답 시간 측정<br/>• 경과 시간, 자원 사용률 확인<br/>• 성능 목표 달성 여부 검증 |
| <span class="blue-text">테스트 통제 도구</span> | 테스트 계획, 수행, 결함 관리 지원 | • 형상 관리 도구<br/>• 결함 추적/관리 도구 |
| <span class="blue-text">테스트 하네스 도구</span> | 테스트 환경을 시뮬레이션 | • 컴포넌트 및 모듈 테스트 환경 구성<br/>• 테스트 지원 코드와 데이터 제공 |

> 💡 **테스트 하네스(Test Harness)**: 컴포넌트 및 모듈을 테스트하기 위해 생성된 코드와 데이터의 집합입니다.

### 테스트 수행 단계별 자동화 도구

<table style="border-collapse: collapse; width: 100%;">
<thead>
<tr style="background-color: #203BB0; color: white;">
<th style="border: 1px solid #ddd; padding: 8px;">테스트 단계</th>
<th style="border: 1px solid #ddd; padding: 8px;">자동화 도구</th>
<th style="border: 1px solid #ddd; padding: 8px;">설명</th>
</tr>
</thead>
<tbody>
<tr>
<td style="border: 1px solid #ddd; padding: 8px;"><strong>테스트 계획</strong></td>
<td style="border: 1px solid #ddd; padding: 8px;">요구사항 관리</td>
<td style="border: 1px solid #ddd; padding: 8px;">사용자 요구사항 정의 및 변경 사항 관리</td>
</tr>
<tr>
<td style="border: 1px solid #ddd; padding: 8px;"><strong>테스트 분석/설계</strong></td>
<td style="border: 1px solid #ddd; padding: 8px;">테스트 케이스 생성</td>
<td style="border: 1px solid #ddd; padding: 8px;">테스트 기법에 따른 데이터 및 케이스 작성 지원</td>
</tr>
<tr>
<td rowspan="4" style="border: 1px solid #ddd; padding: 8px;"><strong>테스트 수행</strong></td>
<td style="border: 1px solid #ddd; padding: 8px;">테스트 자동화</td>
<td style="border: 1px solid #ddd; padding: 8px;">테스트 자동화로 효율성 향상</td>
</tr>
<tr>
<td style="border: 1px solid #ddd; padding: 8px;">정적 분석</td>
<td style="border: 1px solid #ddd; padding: 8px;">코딩 표준, 런타임 오류 검증</td>
</tr>
<tr>
<td style="border: 1px solid #ddd; padding: 8px;">동적 분석</td>
<td style="border: 1px solid #ddd; padding: 8px;">시스템 시뮬레이션을 통한 오류 검출</td>
</tr>
<tr>
<td style="border: 1px solid #ddd; padding: 8px;">성능 테스트</td>
<td style="border: 1px solid #ddd; padding: 8px;">가상 사용자 생성으로 처리 능력 측정</td>
</tr>
<tr>
<td style="border: 1px solid #ddd; padding: 8px;"><strong>테스트 수행</strong></td>
<td style="border: 1px solid #ddd; padding: 8px;">모니터링</td>
<td style="border: 1px solid #ddd; padding: 8px;">CPU, Memory 등 시스템 자원 상태 확인 및 분석</td>
</tr>
<tr>
<td rowspan="3" style="border: 1px solid #ddd; padding: 8px;"><strong>테스트 관리</strong></td>
<td style="border: 1px solid #ddd; padding: 8px;">커버리지 분석</td>
<td style="border: 1px solid #ddd; padding: 8px;">테스트 완료 후 충분성 여부 검증</td>
</tr>
<tr>
<td style="border: 1px solid #ddd; padding: 8px;">형상 관리</td>
<td style="border: 1px solid #ddd; padding: 8px;">테스트 수행에 필요한 도구 및 데이터 관리</td>
</tr>
<tr>
<td style="border: 1px solid #ddd; padding: 8px;">결함 추적/관리</td>
<td style="border: 1px solid #ddd; padding: 8px;">테스트 시 발생한 결함 추적 및 관리 지원</td>
</tr>
</tbody>
</table>

---

## 핵심 요약 정리

### 통합 테스트 방식 비교

| 구분 | 하향식 | 상향식 | 혼합식 |
|------|--------|--------|--------|
| **방향** | 상위 → 하위 | 하위 → 상위 | 양방향 |
| **필요 도구** | 스텁(Stub) | 드라이버(Driver) | 스텁 + 드라이버 |
| **별칭** | Top-Down | Bottom-Up | Sandwich |

### 테스트 3대 요소

```
테스트 케이스 (무엇을)
    ↓
테스트 시나리오 (어떤 순서로)
    ↓
테스트 오라클 (결과가 옳은지)
```

### 테스트 자동화 도구 분류

- **정적 분석**: 코드 분석 (실행 X)
- **동적 분석**: 실행하여 분석 (실행 O)
- **성능 테스트**: 가상 사용자로 부하 테스트
- **테스트 통제**: 계획, 관리, 결함 추적
- **테스트 하네스**: 테스트 환경 시뮬레이션

> 💡 **전문가의 조언**: 통합 테스트는 단위 테스트와 시스템 테스트를 연결하는 중요한 단계입니다. 각 통합 방식의 특징을 이해하고, 프로젝트 상황에 맞는 방식을 선택할 수 있어야 합니다!
