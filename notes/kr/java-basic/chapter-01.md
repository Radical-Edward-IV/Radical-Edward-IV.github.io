---
layout: article
title: 1. Orientation & 개발 환경 설정
permalink: /notes/kr/java-basic/chapter-01
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: Java 기초 과정 강의 노트, Orientation 및 Java 개발 환경 설정 방법과 핵심 개념을 다룹니다.
keywords: "Java, JDK, IntelliJ IDEA, Eclipse, 기초 문법, 컴파일, 객체지향 프로그래밍"
---

<style>
    /* 색상 활용 규칙
      빨강: 주의, 경고, 위험 (에러, 예외 등)
      파랑: 핵심 개념, 주요 기능 (클래스, 메서드 등)
      초록: 안전한 대안, 긍정적 결과 (성공, 정답 등)
      노랑: 코드 요소 (함수명, 메서드명 등)
    */
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
    .large-quote p { font-size: 1.2em !important; }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=Java%20Basic&reversal=false&textBg=false)

---

## 시작하기 전에

<blockquote class="large-quote">
  <p>언어를 배우기 전, 가장 중요한 질문이 하나 있습니다. <strong>"나는 왜 이것을 배우는가?"</strong></p>
  <p> 작은 목표라도 좋습니다. 명확한 이유가 있을 때, 배움은 더 즐거워집니다.</p>
</blockquote>

<div class="motivation-container">
  <div class="motivation-question">당신은 왜 Java를 배우고 싶나요?</div>

  <div class="input-wrapper">
    <input type="text" id="motivationInput" placeholder="예: 안드로이드 앱 개발을 위해, 웹 백엔드 개발자가 되고 싶어서..." />
    <button id="submitMotivation" class="motivation-btn">시작하기</button>
  </div>

  <div id="fireworksContainer" class="fireworks-container">
    <div class="firework"></div>
    <div class="firework"></div>
    <div class="firework"></div>
  </div>

  <div id="celebrationMessage" class="celebration-message">
    <div class="celebration-content">
      <h2 class="celebration-title"></h2>
      <p class="celebration-text"></p>
    </div>
  </div>
</div>

<style>
.motivation-container {
  position: relative;
  margin: 50px auto;
  padding: 40px;
  max-width: 700px;
  background: #ffffff;
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);
}

.motivation-question {
  text-align: center;
  font-size: 1.2rem;
  font-weight: 600;
  color: #111827;
  margin-bottom: 30px;
  letter-spacing: -0.02em;
}

.input-wrapper {
  display: flex;
  flex-direction: column;
  gap: 16px;
  align-items: center;
}

#motivationInput {
  width: 100%;
  max-width: 500px;
  padding: 13px 18px;
  font-size: 15px;
  border: 2px solid #e5e7eb;
  border-radius: 8px;
  outline: none;
  transition: all 0.2s ease;
  font-family: inherit;
  color: #1f2937;
  background: white;
}

#motivationInput:focus {
  border-color: #203BB0;
  box-shadow: 0 0 0 4px rgba(32, 59, 176, 0.1);
  transform: translateY(-1px);
}

.motivation-btn {
  padding: 13px 36px;
  font-size: 15px;
  font-weight: 600;
  color: white;
  background: #203BB0;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.2s ease;
  letter-spacing: -0.01em;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 2px 6px rgba(32, 59, 176, 0.15);
}

.motivation-btn:hover {
  background: #1a2f8f;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(32, 59, 176, 0.2);
  transform: translateY(-1px);
}

.motivation-btn:active {
  transform: translateY(0);
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.05), 0 1px 3px rgba(32, 59, 176, 0.1);
}

/* 폭죽 애니메이션 */
.fireworks-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 10001;
  opacity: 0;
  transition: opacity 0.5s ease-out;
}

.fireworks-container.active {
  opacity: 1;
  pointer-events: auto;
  cursor: pointer;
  animation: fadeIn 0.5s ease-out;
}

.fireworks-container.hiding {
  animation: fadeOut 0.5s ease-out;
  opacity: 0;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}

.fireworks-container.active .firework,
.fireworks-container.active .firework::before,
.fireworks-container.active .firework::after {
  animation: firework 2s ease-out infinite;
}

.firework,
.firework::before,
.firework::after {
  --initialSize: 0.5vmin;
  --finalSize: 45vmin;
  --particleSize: 0.2vmin;
  --color1: #667eea;
  --color2: #764ba2;
  --color3: #f093fb;
  --color4: #4facfe;
  --color5: #43e97b;
  --color6: #fa709a;
  --y: -30vmin;
  --x: -50%;
  --initialY: 60vmin;
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, var(--y));
  width: var(--initialSize);
  aspect-ratio: 1;
  background:
    radial-gradient(circle, var(--color1) var(--particleSize), #0000 0) 50% 0%,
    radial-gradient(circle, var(--color2) var(--particleSize), #0000 0) 100% 50%,
    radial-gradient(circle, var(--color3) var(--particleSize), #0000 0) 50% 100%,
    radial-gradient(circle, var(--color4) var(--particleSize), #0000 0) 0% 50%,

    radial-gradient(circle, var(--color5) var(--particleSize), #0000 0) 80% 90%,
    radial-gradient(circle, var(--color6) var(--particleSize), #0000 0) 95% 90%,
    radial-gradient(circle, var(--color1) var(--particleSize), #0000 0) 90% 70%,
    radial-gradient(circle, var(--color2) var(--particleSize), #0000 0) 100% 60%,
    radial-gradient(circle, var(--color3) var(--particleSize), #0000 0) 55% 80%,
    radial-gradient(circle, var(--color4) var(--particleSize), #0000 0) 70% 77%,

    radial-gradient(circle, var(--color5) var(--particleSize), #0000 0) 22% 90%,
    radial-gradient(circle, var(--color6) var(--particleSize), #0000 0) 45% 90%,
    radial-gradient(circle, var(--color1) var(--particleSize), #0000 0) 33% 70%,
    radial-gradient(circle, var(--color2) var(--particleSize), #0000 0) 10% 60%,
    radial-gradient(circle, var(--color3) var(--particleSize), #0000 0) 31% 80%,
    radial-gradient(circle, var(--color4) var(--particleSize), #0000 0) 28% 77%,
    radial-gradient(circle, var(--color5) var(--particleSize), #0000 0) 13% 72%,

    radial-gradient(circle, var(--color6) var(--particleSize), #0000 0) 80% 10%,
    radial-gradient(circle, var(--color1) var(--particleSize), #0000 0) 95% 14%,
    radial-gradient(circle, var(--color2) var(--particleSize), #0000 0) 90% 23%,
    radial-gradient(circle, var(--color3) var(--particleSize), #0000 0) 100% 43%,
    radial-gradient(circle, var(--color4) var(--particleSize), #0000 0) 85% 27%,
    radial-gradient(circle, var(--color5) var(--particleSize), #0000 0) 77% 37%,
    radial-gradient(circle, var(--color6) var(--particleSize), #0000 0) 60% 7%,

    radial-gradient(circle, var(--color1) var(--particleSize), #0000 0) 22% 14%,
    radial-gradient(circle, var(--color2) var(--particleSize), #0000 0) 45% 20%,
    radial-gradient(circle, var(--color3) var(--particleSize), #0000 0) 33% 34%,
    radial-gradient(circle, var(--color4) var(--particleSize), #0000 0) 10% 29%,
    radial-gradient(circle, var(--color5) var(--particleSize), #0000 0) 31% 37%,
    radial-gradient(circle, var(--color6) var(--particleSize), #0000 0) 28% 7%,
    radial-gradient(circle, var(--color1) var(--particleSize), #0000 0) 13% 42%;
  background-size: var(--initialSize) var(--initialSize);
  background-repeat: no-repeat;
}

.firework::before {
  --x: -50%;
  --y: -50%;
  --initialY: -50%;
  transform: translate(-50%, -50%) rotate(40deg) scale(1.3) rotateY(40deg);
}

.firework::after {
  --x: -50%;
  --y: -50%;
  --initialY: -50%;
  transform: translate(-50%, -50%) rotate(170deg) scale(1.15) rotateY(-30deg);
}

.firework:nth-child(2) {
  --x: 30vmin;
}

.firework:nth-child(1),
.firework:nth-child(1)::before,
.firework:nth-child(1)::after {
  animation-delay: 0s;
}

.firework:nth-child(2),
.firework:nth-child(2)::before,
.firework:nth-child(2)::after {
  --color1: #f093fb;
  --color2: #f5576c;
  --color3: #4facfe;
  --color4: #00f2fe;
  --color5: #43e97b;
  --color6: #38f9d7;
  --finalSize: 40vmin;
  left: 30%;
  top: 60%;
  animation-delay: 0.67s;
}

.firework:nth-child(3) {
  --x: -30vmin;
  --y: -50vmin;
}

.firework:nth-child(3),
.firework:nth-child(3)::before,
.firework:nth-child(3)::after {
  --color1: #fa709a;
  --color2: #fee140;
  --color3: #30cfd0;
  --color4: #330867;
  --color5: #667eea;
  --color6: #764ba2;
  --finalSize: 35vmin;
  left: 70%;
  top: 60%;
  animation-delay: 1.33s;
}

@keyframes firework {
  0% {
    transform: translate(var(--x), var(--initialY));
    width: var(--initialSize);
    opacity: 1;
  }
  50% {
    width: 0.5vmin;
    opacity: 1;
  }
  100% {
    width: var(--finalSize);
    opacity: 0;
  }
}

/* 축하 메시지 */
.celebration-message {
  display: none;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 10000;
  text-align: center;
  background: white;
  padding: 40px 56px;
  border-radius: 12px;
  border: 1px solid #e5e7eb;
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.2);
  cursor: pointer;
}

.celebration-message.showing {
  display: block;
  animation: slideUpFadeIn 0.5s ease-out;
}

.celebration-message.hiding {
  animation: slideDownFadeOut 0.5s ease-out;
}

.celebration-content {
  max-width: 450px;
}

.celebration-title {
  font-size: 1.6rem;
  color: #203BB0;
  margin-bottom: 14px;
  font-weight: 700;
  letter-spacing: -0.02em;
}

.celebration-text {
  font-size: 1.05rem;
  color: #4b5563;
  line-height: 1.6;
  font-weight: 500;
}

@keyframes slideUpFadeIn {
  from {
    opacity: 0;
    transform: translate(-50%, -40%);
  }
  to {
    opacity: 1;
    transform: translate(-50%, -50%);
  }
}

@keyframes slideDownFadeOut {
  from {
    opacity: 1;
    transform: translate(-50%, -50%);
  }
  to {
    opacity: 0;
    transform: translate(-50%, -40%);
  }
}

@keyframes shake {
  0%, 100% { transform: translateX(0); }
  25% { transform: translateX(-10px); }
  75% { transform: translateX(10px); }
}

@media (max-width: 768px) {
  .motivation-container {
    padding: 28px;
    margin: 30px 16px;
  }

  .motivation-question {
    font-size: 1.1rem;
  }

  #motivationInput {
    font-size: 14px;
    padding: 11px 16px;
  }

  .motivation-btn {
    font-size: 14px;
    padding: 11px 30px;
  }

  .celebration-message {
    padding: 32px 40px;
    margin: 0 20px;
  }

  .celebration-title {
    font-size: 1.35rem;
  }

  .celebration-text {
    font-size: 0.95rem;
  }

  .firework,
  .firework::before,
  .firework::after {
    --finalSize: 30vmin;
  }
}
</style>

<script>
(function() {
  const motivationInput = document.getElementById('motivationInput');
  const submitBtn = document.getElementById('submitMotivation');
  const fireworksContainer = document.getElementById('fireworksContainer');
  const celebrationMessage = document.getElementById('celebrationMessage');

  const messages = [
    '멋진 목표네요',
    '훌륭한 선택입니다',
    '최고의 시작입니다',
    '대단한 의지네요',
    '멋진 여정이 될 거예요',
  ];

  function showCelebration(motivation) {
    const randomMessage = messages[Math.floor(Math.random() * messages.length)];
    const title = celebrationMessage.querySelector('.celebration-title');
    const text = celebrationMessage.querySelector('.celebration-text');

    title.textContent = randomMessage;
    text.innerHTML = `<span class="blue-text">"${motivation}"</span><br>이 목표를 향해 함께 달려봅시다!`;

    // 기존 클래스 제거
    celebrationMessage.classList.remove('hiding');
    celebrationMessage.style.display = 'block';
    
    // 애니메이션을 위해 다음 프레임에서 클래스 추가
    requestAnimationFrame(() => {
      requestAnimationFrame(() => {
        celebrationMessage.classList.add('showing');
      });
    });
  }

  function launchFireworks() {
    // 기존 클래스 제거 (재실행을 위해)
    fireworksContainer.classList.remove('active', 'hiding');

    // requestAnimationFrame을 사용하여 확실하게 리플로우 발생
    requestAnimationFrame(() => {
      requestAnimationFrame(() => {
        // 클래스 추가로 애니메이션 시작 (클릭 전까지 계속)
        fireworksContainer.classList.add('active');
      });
    });
  }

  function hideCelebrationAndFireworks() {
    // 축하 메시지 사라지는 애니메이션
    celebrationMessage.classList.remove('showing');
    celebrationMessage.classList.add('hiding');
    
    // 폭죽 사라지는 애니메이션
    fireworksContainer.classList.remove('active');
    fireworksContainer.classList.add('hiding');
    
    // 애니메이션 완료 후 완전히 숨김
    setTimeout(() => {
      celebrationMessage.style.display = 'none';
      celebrationMessage.classList.remove('hiding');
      fireworksContainer.classList.remove('hiding');
    }, 500);
  }

  // 축하 메시지 클릭 시 닫기
  celebrationMessage.addEventListener('click', hideCelebrationAndFireworks);

  // 폭죽 영역 클릭 시 닫기
  fireworksContainer.addEventListener('click', hideCelebrationAndFireworks);

  submitBtn.addEventListener('click', function() {
    const motivation = motivationInput.value.trim();

    if (motivation === '') {
      motivationInput.focus();
      motivationInput.style.animation = 'shake 0.5s';
      setTimeout(() => {
        motivationInput.style.animation = '';
      }, 500);
      return;
    }

    launchFireworks();
    showCelebration(motivation);

    submitBtn.style.transform = 'scale(0.95)';
    setTimeout(() => {
      submitBtn.style.transform = '';
    }, 200);
  });

  motivationInput.addEventListener('keypress', function(e) {
    if (e.key === 'Enter') {
      submitBtn.click();
    }
  });
})();
</script>

---

## Java, 왜 배워야 할까?

### Java의 활용 분야

Java는 1995년 Sun Microsystems에서 개발한 프로그래밍 언어로, **"Write Once, Run Anywhere"**(한 번 작성하면 어디서나 실행)라는 철학을 가지고 있습니다.

**Java가 사용되는 곳**

> - **안드로이드 앱 개발**: 전 세계 모바일 기기의 대부분이 안드로이드
> - **웹 서버 및 백엔드**: Spring, Spring Boot를 활용한 기업용 시스템
> - **빅데이터**: Hadoop, Spark 등의 핵심 프레임워크
> - **IoT 기기**: 임베디드 시스템 및 스마트 기기
> - **금융 시스템**: 은행, 증권사의 거래 시스템
> - **게임 서버**: Minecraft 등의 서버 개발

### Java가 중요한 이유

#### 1. 플랫폼 독립성

Java로 작성한 프로그램은 <span class="blue-text">JVM(Java Virtual Machine)</span>이 설치된 모든 운영체제에서 실행됩니다. Windows에서 작성한 코드를 macOS나 Linux에서도 별도의 수정 없이 실행할 수 있습니다.

<!--
Java는 기계마다 다른 부품에 직접 맞추지 않고, 공통 규격으로 만든 제품이라고 생각하면 쉽습니다.

예를 들어 USB 메모리를 떠올려 보세요.
USB는 노트북이 Windows이든, macOS이든, Linux이든 USB 포트만 있으면 그대로 꽂아서 사용할 수 있습니다.
USB를 만들 때 “이 노트북 전용”, “저 노트북 전용”으로 다시 만들 필요가 없습니다.

여기서
	•	Java 프로그램 = USB 메모리
	•	JVM = 각 컴퓨터에 있는 USB 포트

각 운영체제는 구조가 달라도, 자기에게 맞는 JVM만 설치되어 있으면 Java 프로그램을 고치지 않고 그대로 실행할 수 있습니다.
그래서 Java는 여러 운영체제에서 동일하게 동작하는 언어입니다.
-->

```
Java 소스코드 (.java) → 컴파일 → 바이트코드 (.class) → JVM → 모든 OS에서 실행
```

#### 2. 객체지향 프로그래밍 (OOP)

Java는 철저하게 객체지향 개념을 따르는 언어입니다. <span class="blue-text">클래스</span>와 <span class="blue-text">객체</span>를 통해 코드를 구조화하고, 재사용 가능한 소프트웨어를 작성할 수 있습니다.

<!--
객체지향 프로그래밍(OOP)은 현실에 있는 물건을 그대로 본떠서 프로그램을 만드는 방식입니다.

예를 들어 자동차를 생각해보면, 자동차는 색깔과 속도 같은 특징이 있고, 출발하기·가속하기 같은 기능이 있습니다. 객체지향 프로그래밍에서는 이 자동차를 하나의 객체로 만들어서, 특징과 기능을 함께 묶어 관리합니다.

그래서 자동차를 여러 대 만들거나 기능을 바꿔야 할 때도, 설계도만 잘 만들어 두면 쉽게 관리하고 재사용할 수 있습니다.
-->

#### 3. 강력한 생태계

- **Spring Framework**: 웹 애플리케이션 개발의 표준
- **Maven/Gradle**: 빌드 및 의존성 관리 도구
- **JUnit**: 테스트 프레임워크
- **수많은 라이브러리**: Apache, Google 등에서 제공하는 다양한 라이브러리

#### 4. 자동 메모리 관리

Java는 <span class="green-text">가비지 컬렉션(Garbage Collection)</span>을 통해 메모리를 자동으로 관리합니다. 개발자가 직접 메모리를 할당하고 해제할 필요가 없어 메모리 누수를 방지할 수 있습니다.

#### 5. 강한 타입 시스템

컴파일 시점에 타입 오류를 잡아내어 런타임 오류를 줄일 수 있습니다. 이는 대규모 프로젝트에서 특히 중요합니다.

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">한 줄 요약</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Java는 플랫폼 독립적이고, 강력한 생태계를 가진 객체지향 언어로 안정적이고 확장 가능한 소프트웨어를 만드는 최고의 선택입니다.
</p>
</div>

---

## 개발 환경 설정

Java 프로그래밍을 시작하기 위해서는 코드를 작성하고 실행할 수 있는 환경이 필요합니다.

### 1. JDK (Java Development Kit) 설치

JDK는 Java 프로그램을 개발하고 실행하는 데 필요한 모든 도구를 포함합니다.

#### JDK 버전 선택

- **Java 17 LTS (Long Term Support)**: 장기 지원 버전, 안정성이 중요한 프로젝트에 추천
- **Java 21 LTS**: 최신 LTS 버전, 최신 기능 사용 가능

이 강의에서는 **Java 21 LTS**를 사용합니다.

#### Windows에서 JDK 설치

1. [Oracle JDK 다운로드 페이지](https://www.oracle.com/java/technologies/downloads/) 또는 [OpenJDK](https://openjdk.org/)에 접속합니다.
2. **Java 21 (LTS)** 버전을 선택합니다.
3. Windows용 설치 파일(`.exe` 또는 `.msi`)을 다운로드합니다.
4. 다운로드한 파일을 실행하여 설치를 진행합니다.
5. 설치 경로를 기억해두세요 (예: `C:\Program Files\Java\jdk-21`).

#### macOS에서 JDK 설치

Homebrew를 사용하여 설치하는 방법을 추천합니다.

```bash
# Homebrew 설치 (이미 설치되어 있다면 생략)
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# JDK 21 설치
brew install openjdk@21

# 심볼릭 링크 생성
sudo ln -sfn /opt/homebrew/opt/openjdk@21/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-21.jdk
```

Homebrew가 없다면 [OpenJDK](https://openjdk.org/)에서 macOS용 JDK 21을 직접 다운로드하여 설치할 수 있습니다.

#### 환경 변수 설정

**Windows:**

1. "내 PC" 우클릭 → "속성" → "고급 시스템 설정" → "환경 변수"
2. 시스템 변수에서 "새로 만들기" 클릭
   - 변수 이름: `JAVA_HOME`
   - 변수 값: JDK 설치 경로 (예: `C:\Program Files\Java\jdk-21`)
3. Path 변수에 `%JAVA_HOME%\bin` 추가

**macOS/Linux:**

`.zshrc` 또는 `.bash_profile`에 다음 추가:

```bash
export JAVA_HOME=$(/usr/libexec/java_home -v 21)
export PATH=$JAVA_HOME/bin:$PATH
```

터미널 재시작 후:

```bash
source ~/.zshrc  # 또는 source ~/.bash_profile
```

#### 설치 확인

터미널(또는 명령 프롬프트)에서 다음 명령어를 입력합니다:

```bash
java -version

javac -version
```

**출력 예시:**

```
openjdk version "21.0.x" 2024-xx-xx
OpenJDK Runtime Environment (build 21.0.x)
OpenJDK 64-Bit Server VM (build 21.0.x, mixed mode, sharing)

javac 21.0.x
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">✅</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">체크포인트</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
java와 javac 명령어가 모두 정상적으로 동작하면 JDK 설치가 완료된 것입니다!
</p>
</div>

---

### 2. IDE (통합 개발 환경) 선택 및 설치

Java 개발을 위한 대표적인 IDE는 다음과 같습니다:

#### IntelliJ IDEA (추천)

**장점:**
- 강력한 코드 자동완성 및 리팩토링 기능
- 직관적인 UI
- 커뮤니티 에디션 무료 제공
- Spring Framework와의 뛰어난 통합

**설치 방법:**

1. [IntelliJ IDEA 다운로드 페이지](https://www.jetbrains.com/idea/download/)에 접속
2. **Community Edition** (무료) 다운로드
3. 설치 파일 실행
4. 설치 옵션:
   - "Create Desktop Shortcut" 체크
   - ".java" 파일 연결 체크
   - "Add 'bin' folder to PATH" 체크

#### Eclipse

**장점:**
- 완전 무료 오픈소스
- 다양한 플러그인
- 가볍고 안정적

**설치 방법:**

1. [Eclipse 다운로드 페이지](https://www.eclipse.org/downloads/)에 접속
2. "Eclipse IDE for Java Developers" 다운로드
3. 압축 해제 후 `eclipse.exe` 실행

#### Visual Studio Code

**장점:**
- 가볍고 빠름
- 다양한 언어 지원
- Extension으로 Java 지원

**설치 방법:**

1. [VSCode 다운로드](https://code.visualstudio.com/)
2. Extension 설치:
   - "Extension Pack for Java" 검색 및 설치 (Microsoft 제공)

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">🎯</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">추천</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
이 강의에서는 <span class="blue-text">IntelliJ IDEA Community Edition</span>을 사용합니다. 초보자에게 가장 사용하기 쉽고, 업계에서도 널리 사용되는 IDE입니다.
</p>
</div>

---

## Hello World 프로그램 작성

이제 모든 준비가 끝났습니다! 첫 번째 Java 프로그램을 작성해봅시다.

### IntelliJ IDEA에서 프로젝트 생성

#### 1. 새 프로젝트 만들기

1. IntelliJ IDEA 실행
2. "New Project" 클릭
3. 프로젝트 설정:
   - **Name**: `HelloJava`
   - **Location**: 원하는 경로 선택
   - **Language**: Java
   - **Build system**: IntelliJ
   - **JDK**: 설치한 JDK 17 선택
   - **Add sample code** 체크 해제
4. "Create" 클릭

#### 2. 새 Java 클래스 생성

1. 프로젝트 창에서 `src` 폴더 우클릭
2. "New" → "Java Class" 선택
3. 클래스 이름: `HelloWorld` 입력
4. Enter 키를 눌러 생성

#### 3. 코드 작성

생성된 `HelloWorld.java` 파일에 다음 코드를 입력합니다:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Java World!");
    }
}
```

#### 4. 실행하기

**방법 1: 단축키 사용**
- Windows/Linux: `Shift + F10`
- macOS: `Control + R`

**방법 2: 우클릭**
- 코드 편집기에서 우클릭 → "Run 'HelloWorld.main()'"

**방법 3: 재생 버튼**
- 코드 왼쪽의 초록색 재생 버튼 클릭

#### 실행 결과

IntelliJ IDEA 하단의 "Run" 창에 다음과 같이 출력됩니다:

```
Hello, Java World!

Process finished with exit code 0
```

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">🎉</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">축하합니다!</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
첫 번째 Java 프로그램을 성공적으로 실행했습니다. 이제 본격적으로 Java를 배울 준비가 완료되었습니다.
</p>
</div>

---

## Java 프로그램의 구조 이해하기

방금 작성한 Hello World 프로그램을 다시 살펴보면서 Java 프로그램의 기본 구조를 이해해봅시다.

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Java World!");
    }
}
```

### 1. 클래스 (Class)

```java
public class HelloWorld {
    // 클래스 내용
}
```

Java는 **모든 것이 클래스 안에 존재**해야 합니다. 클래스는 프로그램의 기본 단위이며, 데이터와 메서드를 담는 틀입니다.

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">클래스 = 설계도</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
<span class="blue-text">클래스</span>는 객체를 만들기 위한 설계도와 같습니다. 건물을 짓기 위해 설계도가 필요하듯, Java에서는 클래스를 통해 프로그램을 구성합니다.
</p>
</div>

**클래스 이름 규칙:**
- 파일 이름과 클래스 이름이 **반드시 동일**해야 합니다
- 첫 글자는 **대문자**로 시작 (PascalCase)
- 예: `HelloWorld.java` → `public class HelloWorld`

### 2. main 메서드

```java
public static void main(String[] args) {
    // 프로그램 시작점
}
```

<span class="blue-text">main 메서드</span>는 Java 프로그램의 **시작점(Entry Point)**입니다. JVM은 프로그램을 실행할 때 가장 먼저 `main` 메서드를 찾아 실행합니다.

**main 메서드 구성 요소:**

| 키워드 | 의미 |
|--------|------|
| `public` | 어디서든 접근 가능 (접근 제어자) |
| `static` | 객체 생성 없이 호출 가능 |
| `void` | 반환값이 없음 |
| `main` | 메서드 이름 (고정) |
| `String[] args` | 명령줄 인자를 받는 매개변수 |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">⚠️</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">주의</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
main 메서드의 형식은 반드시 <code>public static void main(String[] args)</code>여야 합니다. 하나라도 다르면 프로그램이 실행되지 않습니다.
</p>
</div>

### 3. System.out.println()

```java
System.out.println("Hello, Java World!");
```

콘솔에 문자열을 출력하는 메서드입니다.

- <span class="yellow-code">System</span>: Java의 표준 시스템 클래스
- <span class="yellow-code">out</span>: 표준 출력 스트림 (콘솔)
- <span class="yellow-code">println</span>: 문자열을 출력하고 줄바꿈 (print + line)

**print vs println:**

```java
System.out.print("Hello ");     // 줄바꿈 없음
System.out.print("World!");      // 출력: Hello World!

System.out.println("Hello");     // 줄바꿈 있음
System.out.println("World!");    // 출력:
                                  // Hello
                                  // World!
```

### 4. 세미콜론 (;)

Java에서 모든 문장(statement)은 **세미콜론(;)**으로 끝나야 합니다.

```java
System.out.println("Hello");  // ✅ 올바름
System.out.println("World")   // ❌ 오류: 세미콜론 누락
```

### 5. 중괄호 ({ })

중괄호는 **코드 블록**을 정의합니다. 클래스, 메서드, 제어문 등의 범위를 나타냅니다.

```java
public class HelloWorld {        // 클래스 블록 시작
    public static void main(String[] args) {  // 메서드 블록 시작
        System.out.println("Hello!");
    }  // 메서드 블록 끝
}  // 클래스 블록 끝
```

---

## Java 프로그램 실행 과정

Java 프로그램이 실행되는 과정을 단계별로 살펴봅시다.

### 1. 컴파일 과정

```
HelloWorld.java (소스 코드)
        ↓
   [javac 컴파일러]
        ↓
HelloWorld.class (바이트코드)
```

- `javac` (Java Compiler): 소스 코드(.java)를 바이트코드(.class)로 변환
- **바이트코드**: JVM이 이해할 수 있는 중간 언어

### 2. 실행 과정

```
HelloWorld.class (바이트코드)
        ↓
     [JVM]
        ↓
   기계어로 변환
        ↓
  운영체제에서 실행
```

- JVM은 바이트코드를 읽고 해석하여 실행
- 운영체제에 관계없이 동일한 바이트코드 실행 가능

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">Write Once, Run Anywhere (WORA)</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Java의 핵심 철학입니다. 한 번 컴파일한 바이트코드는 JVM이 설치된 모든 플랫폼에서 실행할 수 있습니다.
</p>
</div>

### 3. 터미널에서 직접 컴파일 및 실행

IntelliJ IDEA 없이 터미널에서 직접 실행할 수도 있습니다.

**1) 컴파일:**

```bash
javac HelloWorld.java
```

→ `HelloWorld.class` 파일 생성

**2) 실행:**

```bash
java HelloWorld
```

→ 출력: `Hello, Java World!`

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">팁</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
실행할 때는 <code>.class</code> 확장자를 붙이지 않습니다. 클래스 이름만 입력합니다.
</p>
</div>

---

## 자주 발생하는 오류와 해결 방법

### 1. "javac를 인식할 수 없습니다"

**원인:** JDK가 설치되지 않았거나 환경 변수가 설정되지 않음

**해결 방법:**
- JDK 설치 확인: `java -version`
- 환경 변수 `JAVA_HOME` 및 `PATH` 설정 확인
- 터미널 재시작

### 2. "클래스 이름과 파일 이름이 일치하지 않습니다"

```java
// 파일명: HelloWorld.java
public class Hello {  // ❌ 오류
    // ...
}
```

**해결 방법:** 클래스 이름을 파일 이름과 동일하게 수정

```java
// 파일명: HelloWorld.java
public class HelloWorld {  // ✅ 올바름
    // ...
}
```

### 3. "main 메서드를 찾을 수 없습니다"

```java
public class HelloWorld {
    public void main(String[] args) {  // ❌ static 누락
        // ...
    }
}
```

**해결 방법:** main 메서드는 반드시 `public static void main(String[] args)` 형식이어야 함

### 4. "';' 필요"

```java
System.out.println("Hello")  // ❌ 세미콜론 누락
```

**해결 방법:** 모든 문장 끝에 세미콜론(;) 추가

### 5. 한글 깨짐 문제

**Windows 명령 프롬프트에서 한글이 깨지는 경우:**

```bash
chcp 65001
javac -encoding UTF-8 HelloWorld.java
java HelloWorld
```

**또는 IntelliJ IDEA 사용 (자동으로 인코딩 처리)**

---

## 첫 번째 실습: 출력 연습

이제 직접 코드를 작성해봅시다!

### 실습 1: 여러 줄 출력하기

다음과 같이 출력되도록 프로그램을 작성하세요:

```
안녕하세요!
Java 프로그래밍을 배우고 있습니다.
열심히 공부하겠습니다!
```

<details>
<summary>정답 보기</summary>

<pre><code class="language-java">public class Practice01 {
    public static void main(String[] args) {
        System.out.println("안녕하세요!");
        System.out.println("Java 프로그래밍을 배우고 있습니다.");
        System.out.println("열심히 공부하겠습니다!");
    }
}
</code></pre>

</details>

### 실습 2: 특수 문자 출력하기

다음과 같이 출력되도록 프로그램을 작성하세요:

```
"Java"는 재미있다!
파일 경로: C:\Program Files\Java
```

**힌트:**
- 큰따옴표를 출력하려면: `\"`
- 역슬래시를 출력하려면: `\\`

<details>
<summary>정답 보기</summary>

<pre><code class="language-java">public class Practice02 {
    public static void main(String[] args) {
        System.out.println("\"Java\"는 재미있다!");
        System.out.println("파일 경로: C:\\Program Files\\Java");
    }
}
</code></pre>

<p><strong>이스케이프 시퀀스:</strong></p>
<ul>
<li><code>\n</code>: 줄바꿈</li>
<li><code>\t</code>: 탭</li>
<li><code>\"</code>: 큰따옴표</li>
<li><code>\\</code>: 역슬래시</li>
</ul>

</details>

---

## 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 16px;">
<span style="font-size: 1.25rem;">✅</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">이번 챕터에서 배운 내용</h3>
</div>

<ol style="margin: 0; padding-left: 20px; color: #4b5563;">
<li style="margin-bottom: 12px;"><strong>Java의 특징</strong>
   <ul style="margin-top: 8px; margin-bottom: 0;">
   <li>플랫폼 독립성 (Write Once, Run Anywhere)</li>
   <li>객체지향 프로그래밍</li>
   <li>자동 메모리 관리 (Garbage Collection)</li>
   </ul>
</li>
<li style="margin-bottom: 12px;"><strong>개발 환경 설정</strong>
   <ul style="margin-top: 8px; margin-bottom: 0;">
   <li>JDK 설치 및 환경 변수 설정</li>
   <li>IntelliJ IDEA 설치 및 프로젝트 생성</li>
   </ul>
</li>
<li style="margin-bottom: 12px;"><strong>Java 프로그램 구조</strong>
   <pre style="margin-top: 8px; margin-bottom: 0;"><code class="language-java">public class ClassName {
    public static void main(String[] args) {
        // 코드 작성
    }
}
</code></pre>
</li>
<li style="margin-bottom: 12px;"><strong>컴파일 및 실행</strong>
   <ul style="margin-top: 8px; margin-bottom: 0;">
   <li><code>javac FileName.java</code> → 컴파일</li>
   <li><code>java ClassName</code> → 실행</li>
   </ul>
</li>
<li style="margin-bottom: 0;"><strong>기본 출력</strong>
   <ul style="margin-top: 8px; margin-bottom: 0;">
   <li><code>System.out.println()</code>: 출력 + 줄바꿈</li>
   <li><code>System.out.print()</code>: 출력 (줄바꿈 없음)</li>
   </ul>
</li>
</ol>

</div>

---

## 다음 챕터 예고

다음 챕터에서는 **변수와 자료형**을 배웁니다.

- 변수란 무엇인가?
- 기본 자료형 (int, double, boolean, char 등)
- 변수 선언과 초기화
- 형변환 (Type Casting)
- 문자열 (String) 다루기

---

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04); text-align: center;">
<div style="display: flex; align-items: center; justify-content: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">🎯</span>
<h3 style="margin: 0; font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">첫 걸음을 축하합니다!</h3>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
Java 프로그래밍의 첫 걸음을 성공적으로 마쳤습니다.<br>
이제 본격적으로 Java의 세계로 들어갈 준비가 되었습니다!
</p>
</div>
