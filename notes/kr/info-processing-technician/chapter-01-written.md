---
layout: article
title: 1. 프로그래밍기능사 개편 안내 (2026년)
permalink: /notes/kr/info-processing-technician/chapter-01-written
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 2026년 정보처리기능사가 프로그래밍기능사로 개편됩니다. 실기 시험이 필답형에서 코딩 실습 작업형으로 전면 변경됩니다.
keywords: "프로그래밍기능사, 정보처리기능사, 2026년 개편, 실기 작업형, 코딩 시험, Python, Java, SQL, C언어"
---

<style>
    /* 색상 활용 규칙
      빨강: 주의, 경고, 위험 (에러, 필수 주의사항 등)
      파랑: 핵심 개념, 주요 기능 (프로그래밍기능사, 실무 코딩 등)
      초록: 안전한 대안, 긍정적 결과 (합격 팁, 권장 사항 등)
      노랑: 코드 요소 (프로그래밍 언어명, 기술 용어 등)
    */
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EA%B8%B0%EB%8A%A5%EC%82%AC&reversal=false&textBg=false)

---

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">중요 공지: 2026년 시험 개편</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
<strong>정보처리기능사</strong>가 <strong class="blue-text">프로그래밍기능사</strong>로 명칭 변경되며, 실기 시험 방식이 <span class="red-text">필답형에서 PC 기반 작업형(코딩)</span>으로 전면 개편됩니다.
</p>
</div>

## 프로그래밍기능사란?

<span class="blue-text">프로그래밍기능사</span>는 2026년부터 기존의 정보처리기능사 자격증 명칭과 시험 방식이 변경된 국가기술자격으로, **정보기술 분야의 가장 기초적인 코딩 실무 능력을 평가**합니다.

### 핵심 특징

- 실기 시험이 **필답형 → <span class="blue-text">PC 기반 작업형(코딩)</span>**으로 전면 개편
- **Python, Java, C, SQL** 등을 활용한 실습 중심 평가
- IT 입문자에게 유용한 **NCS 기반 실무 중심** 자격증
- 정보기술 분야의 **기초 코딩 실무 능력** 검증

---

## 주요 변경 사항 (2026년부터)

### 1. 명칭 변경

```
정보처리기능사 → 프로그래밍기능사
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">✓</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">왜 바뀌나요?</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
실무 코딩 능력을 강조하고, 프로그래밍 중심의 자격증임을 명확히 하기 위함입니다.
</p>
</div>

### 2. 실기 시험 방식 변경

| 구분 | 변경 전 (2025년까지) | 변경 후 (2026년부터) |
|------|---------------------|---------------------|
| **방식** | 필답형 (종이 시험) | <span class="blue-text">PC 기반 작업형 (코딩 실습)</span> |
| **시간** | 2시간 30분 | <span class="blue-text">1시간 30분</span> |
| **내용** | 암기 위주 | <span class="blue-text">NCS 기반 실무 코딩</span> |
| **평가** | 이론 + 단순 코드 해석 | <span class="blue-text">직접 코드 작성 및 실행</span> |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">중요</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
실제 <span class="red-text">코딩 실력</span>이 필수입니다. 단순 암기로는 합격할 수 없습니다!
</p>
</div>

### 3. 출제 내용 변경

**변경 전 (2025년까지):**
- 필기: 전자계산기일반, 패키지활용, PC운영체제, 정보통신일반
- 실기: 필답형 - 운영체제, 데이터베이스, 네트워크 이론 중심
- 암기 위주의 평가

**변경 후 (2026년):**

| 영역 | 세부 내용 |
|------|----------|
| **프로그래밍** | 구조적/객체지향 프로그래밍, 기초문법, 순차/선택/반복 구문, 상속, 다형성, 추상화 |
| **응용SW 기초** | 네트워크(프로토콜, OSI, TCP/IP), 데이터베이스(모델링, E-R, 무결성, 자료구조) |
| **화면구현** | HTML, CSS, JavaScript 기초, UI/UX 개념, UI 테스트 기법 |
| **SQL** | SELECT, DML(INSERT/UPDATE/DELETE), DDL(CREATE/ALTER/DROP), DCL, 트랜잭션 |
| **테스트/배포** | 단위/통합/블랙박스/화이트박스 테스트, DevOps, CI/CD 개념 |
| **개발환경** | 운영체제 기초, 기본 명령어, 개발도구 설정, 백업/복원, 형상관리 |

---

## 시험 정보

### 주관 기관

- **주관**: 한국산업인력공단 (과학기술정보통신부 주관)
- **접수**: 큐넷 (www.q-net.or.kr)

### 출제기준표 다운로드

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📄</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">Q-Net 출제기준표</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
- <a href="/notes/assets/info-processing-technician/프로그래밍기능사_출제기준_20250101.pdf" download style="color: #203BB0; text-decoration: none; font-weight: 500;">📥 2025년 출제기준표 다운로드</a><br>
- <a href="/notes/assets/info-processing-technician/프로그래밍기능사_출제기준_20260101.pdf" download style="color: #203BB0; text-decoration: none; font-weight: 500;">📥 2026년 출제기준표 다운로드</a>
</p>
</div>

### 응시 자격

- **제한 없음** (비전공자, 중·고등학생도 응시 가능)
- 학력, 경력, 나이 제한 없음

### 시험 과목

#### 필기 시험

- **방식**: 객관식 4지선다형
- **시간**: 60분
- **문항**: 60문항
- **과목**: 프로그래밍 언어 | 응용SW기초기술 | SQL 활용 | 정보시스템 기초기술
  1. **프로그래밍 언어 활용 및 응용**: 구조적/객체지향 프로그래밍
  2. **응용SW 기초 기술 활용**: 네트워크 기초, 데이터베이스 기초
  3. **화면구현 및 UI 테스트**: HTML, CSS, JavaScript 기초
  4. **SQL 작성 및 활용**: SELECT, DML, DDL, DCL
  5. **테스트 및 배포**: 단위/통합 테스트, DevOps, CI/CD
  6. **개발자 환경 구축**: 운영체제 기초, 개발환경 설정
  7. **개발 환경 운영 지원**: 백업/복원, 소스코드 형상 관리

#### 실기 시험 (2026년 개편)

- **방식**: <span class="blue-text">PC 기반 작업형 (코딩 실습)</span>
- **시간**: 1시간 30분
- **과목**: 기초프로그래밍 실무
  1. **프로그래밍 언어 활용**: 구조적/객체지향/스크립트 언어 활용 (C, Java, Python)
  2. **프로그래밍 언어 응용**: 언어특성 활용, 라이브러리 활용
  3. **SQL 활용**: 기본/고급 SQL 작성 (DDL, DML, DCL, 인덱스, 뷰)
  4. **SQL 작성**: 데이터 조회 및 수정

### 합격 기준

- **필기**: 100점 만점에 60점 이상
- **실기**: 100점 만점에 60점 이상

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">합격 팁</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
필기와 실기 모두 60점 이상이어야 하며, 한 과목이라도 60점 미만이면 불합격입니다.
</p>
</div>

---

## 대상

✅ IT 분야 입문자 및 비전공자
✅ 취업 준비생
✅ 중·고등학생

---

## 준비 방법


### 학습 핵심 포인트

| 영역 | 학습 내용 |
|------|----------|
| **프로그래밍 언어** | C, Java, Python 기본 문법, 조건문, 반복문, 함수, 객체지향 개념 |
| **SQL** | SELECT, JOIN, 서브쿼리, DML(INSERT/UPDATE/DELETE), DDL, DCL |
| **웹 기초** | HTML 태그, CSS 스타일링, JavaScript 기초 문법 |
| **테스트** | 단위/통합 테스트, 블랙박스/화이트박스 테스트 개념 |
| **DevOps** | CI/CD 개념, 형상관리(Git) 기초 |
| **운영체제** | 운영체제 개념, Linux 기본 명령어 (ls, cd, mkdir, chmod, grep 등) |
| **네트워크** | OSI 7계층, TCP/IP, 프로토콜 개념 |

---

## 시험 일정 및 접수

### 정기 시험

- 연간 **4회** 시행 (통상)
- 일정은 매년 1월경 확정

### 접수 방법

1. [큐넷 홈페이지](https://www.q-net.or.kr) 접속
2. 회원가입 및 로그인
3. 원서접수 → 정기시험 → 프로그래밍기능사 선택
4. 응시 지역 및 시험장 선택
5. 응시료 결제 (2026년 기준 약 20,000원 예상)

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">✓</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">중요 일정</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• 원서접수 마감일을 꼭 확인하세요!<br>
• 시험장이 조기 마감될 수 있으니 빠르게 접수하세요.
</p>
</div>

---

## 추천 학습 방법

**이론 학습**: YouTube 무료 강의, 기출문제집 활용
**기출문제 풀이**: 2020년 개편 이후 기출문제 반복 풀이 (가장 중요!)
**실습 중심**: 직접 코드 작성 및 실행, SQL/Linux 실습 환경 구축

---

## FAQ (자주 묻는 질문)

**Q1. 비전공자도 합격 가능한가요?**  
A: 네, 가능합니다. 2026년 개편 후에는 실제 코딩 능력이 필요하므로 3~6개월 정도의 준비 기간이 권장됩니다.

**Q2. 어떤 프로그래밍 언어를 먼저 공부해야 하나요?**  
A: Python을 추천합니다. 문법이 간결하고 배우기 쉬워 입문자에게 적합합니다.

**Q3. 실기 시험에서 모든 언어를 다 사용해야 하나요?**
A: 아닙니다. 문제에 따라 특정 언어로 작성하거나 선택할 수 있습니다. 다만, C, Java, Python 중 최소 2개 이상은 능숙하게 다룰 수 있어야 하며, SQL은 필수입니다.

**Q4. 2026년 개편 후 웹 관련 내용도 출제되나요?**
A: 네, 2026년부터 HTML, CSS, JavaScript 기초가 필기와 실기 모두에 포함됩니다. 기본적인 웹 페이지 구조와 스타일링을 이해해야 합니다.

**Q5. DevOps, CI/CD도 공부해야 하나요?**
A: 필기 시험에서 개념 수준으로 출제됩니다. 깊은 실무 지식보다는 기본 개념과 용어를 이해하면 됩니다.

---

## 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 16px;">
<span style="font-size: 1.25rem;">✅</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">2026년 프로그래밍기능사 개편 핵심</h3>
</div>

<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li style="margin-bottom: 8px;"><strong>명칭 변경</strong>: 정보처리기능사 → <span class="blue-text">프로그래밍기능사</span></li>
<li style="margin-bottom: 8px;"><strong>실기 방식</strong>: 필답형 → <span class="blue-text">PC 기반 작업형 (코딩 실습)</span></li>
<li style="margin-bottom: 8px;"><strong>시험 시간</strong>: 2시간 30분 → <span class="blue-text">1시간 30분</span></li>
<li style="margin-bottom: 8px;"><strong>출제 내용</strong>: 프로그래밍(C/Java/Python), SQL, 웹(HTML/CSS/JS), 테스트, DevOps</li>
<li style="margin-bottom: 8px;"><strong>준비 전략</strong>: 직접 코딩 실습, 기출문제 반복 풀이</li>
<li style="margin-bottom: 0;"><strong>합격 기준</strong>: 필기/실기 각 60점 이상</li>
</ul>

</div>

---

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04); text-align: center;">
<div style="display: flex; align-items: center; justify-content: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">🎯</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">프로그래밍기능사 합격을 응원합니다!</h3>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
2026년 개편에 대비하여 지금부터 차근차근 준비하세요.<br>
실습 중심 학습으로 <strong>실무 코딩 능력</strong>을 갖춘다면 반드시 합격할 수 있습니다!
</p>
</div>

---

## 관련 링크

- 📚 [기존 내용 보기 (응용 SW 기초 기술 활용)](/notes/kr/info-processing-technician/chapter-01-old)
- 🌐 [큐넷 공식 홈페이지](https://www.q-net.or.kr)
- 📝 [프로그래머스 코딩테스트 연습](https://programmers.co.kr)