---
layout: article
title: 1. Orientation & 개발 환경 설정
permalink: /notes/kr/c-basic/chapter-01
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: C 기초 과정 강의 노트, Orientation 및 C 개발 환경 설정 방법과 핵심 개념을 다룹니다.
keywords: "C언어, 개발 환경, gcc, Visual Studio Code, 기초 문법, 컴파일, 프로그래밍"
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

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=C%20Programming%20Basic&reversal=false&textBg=false)

---

## 시작하기 전에

> 언어를 배우기 전, 가장 중요한 질문이 하나 있습니다. **"나는 왜 이것을 배우는가?"**
> 작은 목표라도 좋습니다. 명확한 이유가 있을 때, 배움은 더 즐거워집니다.

<div class="motivation-container">
  <div class="motivation-question">당신은 왜 C언어를 배우고 싶나요?</div>

  <div class="input-wrapper">
    <input type="text" id="motivationInput" placeholder="예: 임베디드 시스템 개발을 위해, 게임 엔진을 만들고 싶어서..." />
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
  background: linear-gradient(to bottom, #ffffff, #f9fafb);
  border: 1px solid #e5e7eb;
  border-radius: 12px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
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
  background: linear-gradient(135deg, #203BB0 0%, #1a2f8f 100%);
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.25s ease;
  letter-spacing: -0.01em;
  box-shadow: 0 4px 12px rgba(32, 59, 176, 0.3);
}

.motivation-btn:hover {
  background: linear-gradient(135deg, #1a2f8f 0%, #142366 100%);
  box-shadow: 0 6px 16px rgba(32, 59, 176, 0.4);
  transform: translateY(-2px);
}

.motivation-btn:active {
  transform: translateY(0);
  box-shadow: 0 2px 8px rgba(32, 59, 176, 0.3);
}

/* 폭죽 애니메이션 */
.fireworks-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 9999;
  opacity: 0;
  transition: opacity 0.3s;
}

.fireworks-container.active {
  opacity: 1;
}

.fireworks-container.active .firework,
.fireworks-container.active .firework::before,
.fireworks-container.active .firework::after {
  animation: firework 2s ease-out;
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
  animation-delay: -0.25s;
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
  animation-delay: -0.4s;
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
  animation: slideUpFadeIn 0.5s ease-out;
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
    
    celebrationMessage.style.display = 'block';
    
    setTimeout(() => {
      celebrationMessage.style.display = 'none';
    }, 3500);
  }
  
  function launchFireworks() {
    // 기존 클래스 제거 (재실행을 위해)
    fireworksContainer.classList.remove('active');

    // requestAnimationFrame을 사용하여 확실하게 리플로우 발생
    requestAnimationFrame(() => {
      requestAnimationFrame(() => {
        // 클래스 추가로 애니메이션 시작
        fireworksContainer.classList.add('active');

        setTimeout(() => {
          fireworksContainer.classList.remove('active');
        }, 2000);
      });
    });
  }
  
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

## C언어, 왜 배워야 할까?

### C언어의 활용 분야

C언어는 1972년에 개발된 오래된 언어지만, 여전히 현대 소프트웨어 개발의 핵심으로 자리잡고 있습니다.

**C언어가 사용되는 곳**

> - **운영체제**: Windows, Linux, macOS의 핵심 부분은 C로 작성되었습니다
> - **임베디드 시스템**: 자동차, 가전제품, IoT 기기의 펌웨어
> - **게임 엔진**: Unreal Engine, Unity 등의 핵심 엔진
> - **데이터베이스**: MySQL, PostgreSQL 등
> - **컴파일러**: Python, Java 등의 인터프리터와 컴파일러
> - **시스템 프로그래밍**: 드라이버, 네트워크 프로토콜 스택

### C언어가 중요한 이유

#### 1. 하드웨어에 가까운 언어

C언어는 **고급 언어**이면서도 하드웨어를 직접 제어할 수 있는 능력을 제공합니다. 메모리를 직접 관리하고, 포인터를 통해 메모리 주소에 접근할 수 있어 시스템의 동작 원리를 깊이 이해할 수 있습니다.

#### 2. 빠른 실행 속도

C언어로 작성된 프로그램은 기계어에 가깝게 컴파일되어 매우 빠른 실행 속도를 자랑합니다. 성능이 중요한 분야에서는 여전히 C가 최선의 선택입니다.

#### 3. 다른 언어의 기초

C언어를 배우면 C++, Java, C#, JavaScript 등 수많은 언어를 쉽게 배울 수 있습니다. 많은 현대 언어들이 C의 문법과 개념을 기반으로 설계되었기 때문입니다.

#### 4. 컴퓨터 과학의 기본 개념 학습

메모리 관리, 포인터, 자료구조, 알고리즘 등 컴퓨터 과학의 핵심 개념을 C를 통해 배울 수 있습니다. 이는 프로그래머로서 성장하는 데 필수적인 지식입니다.

<div style="background-color: #fff3cd; padding: 15px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #BD8739;">
<strong>💡 한 줄 요약</strong><br>
C언어는 컴퓨터의 동작 원리를 이해하고, 효율적인 프로그램을 작성하는 방법을 배우는 최고의 언어입니다.
</div>

---

## 개발 환경 설정

C 언어 프로그래밍을 시작하기 위해서는 코드를 작성할 **에디터**와 코드를 실행 가능한 프로그램으로 만들어주는 **컴파일러**가 필요합니다.

### 1. Visual Studio Code 설치

Visual Studio Code(VSCode)는 Microsoft에서 개발한 무료 코드 에디터로, 가볍고 강력한 기능을 제공합니다.

#### 다운로드 및 설치

1. [Visual Studio Code 공식 웹사이트](https://code.visualstudio.com/)에 접속합니다.
2. 운영체제에 맞는 버전을 다운로드합니다.
   - Windows: `.exe` 파일 다운로드
   - macOS: `.dmg` 파일 다운로드
   - Linux: `.deb` 또는 `.rpm` 파일 다운로드
3. 다운로드한 파일을 실행하여 설치를 진행합니다.
4. 설치 과정에서 "PATH에 추가" 옵션을 체크하면 터미널에서 `code` 명령어로 VSCode를 실행할 수 있습니다.

---

### 2. C 컴파일러 설치

C 언어로 작성한 코드를 실행하려면 컴파일러가 필요합니다. 운영체제별로 설치 방법이 다릅니다.

#### Windows - MinGW 설치

**MinGW**(Minimalist GNU for Windows)는 Windows에서 GCC 컴파일러를 사용할 수 있게 해주는 도구입니다.

1. [MinGW-w64 다운로드 페이지](https://sourceforge.net/projects/mingw-w64/)에 접속합니다.
2. 최신 버전을 다운로드하고 설치합니다.
3. 설치 시 옵션 선택:
   - **Architecture**: `x86_64` (64비트) 선택
   - **Threads**: `posix` 선택
   - **Exception**: `seh` 선택
4. 설치가 완료되면 환경 변수에 MinGW의 `bin` 폴더 경로를 추가합니다.
   ```
   C:\mingw-w64\mingw64\bin
   ```
5. 명령 프롬프트에서 다음 명령어로 설치를 확인합니다:
   ```bash
   gcc --version
   ```

#### macOS - Xcode Command Line Tools

macOS에는 기본적으로 gcc가 포함된 Xcode Command Line Tools를 설치할 수 있습니다.

1. 터미널을 엽니다.
2. 다음 명령어를 입력합니다:
   ```bash
   xcode-select --install
   ```
3. 설치 창이 나타나면 "설치"를 클릭합니다.
4. 설치 완료 후 다음 명령어로 확인합니다:
   ```bash
   gcc --version
   ```

---

### 3. VSCode Extension 설치

VSCode에서 C 언어 개발을 편리하게 하기 위해 확장 프로그램을 설치합니다.

#### C/C++ Extension 설치

1. VSCode를 실행합니다.
2. 왼쪽 사이드바에서 확장(Extensions) 아이콘을 클릭하거나 `Ctrl+Shift+X` (macOS: `Cmd+Shift+X`)를 누릅니다.
3. 검색창에 **"C/C++"**를 입력합니다.
4. Microsoft에서 제공하는 **C/C++** 확장을 찾아 "설치(Install)" 버튼을 클릭합니다.

<div style="background-color: #f0f4f8; padding: 15px; border-radius: 8px; margin: 15px 0; border-left: 4px solid #203BB0;">
<strong>추천 Extension</strong>
<ul style="margin-top: 10px;">
<li><span class="blue-text">C/C++</span> (Microsoft): IntelliSense, 디버깅, 코드 탐색 기능</li>
<li><span class="blue-text">Code Runner</span>: 코드를 빠르게 실행할 수 있는 확장</li>
<li><span class="blue-text">C/C++ Themes</span>: C 언어 문법 하이라이팅 개선</li>
</ul>
</div>

---

### 4. Hello World 프로그램 작성

이제 모든 준비가 끝났습니다! 첫 번째 C 프로그램을 작성해봅시다.

#### 프로젝트 폴더 생성

1. 작업할 폴더를 생성합니다 (예: `c-basic`).
2. VSCode에서 `파일 > 폴더 열기`를 통해 해당 폴더를 엽니다.

#### hello.c 파일 생성

1. VSCode에서 새 파일을 생성합니다 (`Ctrl+N` 또는 `Cmd+N`).
2. 다음 코드를 입력합니다:

```c
#include <stdio.h>

int main() {
    printf("Hello World!\n");
    return 0;
}
```

3. 파일을 `hello.c`로 저장합니다 (`Ctrl+S` 또는 `Cmd+S`).

#### 코드 설명

- `#include <stdio.h>`: 표준 입출력 함수를 사용하기 위한 헤더 파일
- `int main()`: 프로그램의 시작점인 main 함수
- `printf("Hello World!\n")`: 화면에 "Hello World!" 출력
- `\n`: 줄바꿈 문자
- `return 0`: 프로그램 정상 종료

#### 컴파일 및 실행

**터미널 열기:**
- VSCode에서 `` Ctrl+` `` (백틱) 또는 `터미널 > 새 터미널`

**컴파일:**
```bash
gcc hello.c -o hello
```

**실행:**

Windows:
```bash
hello.exe
```

macOS:
```bash
./hello
```

**출력 결과:**
```
Hello World!
```

<div style="background-color: #e8f4f8; padding: 15px; border-radius: 8px; margin: 20px 0;">
<strong>축하합니다!</strong> 첫 번째 C 프로그램을 성공적으로 실행했습니다. 이제 본격적으로 C 언어를 배울 준비가 완료되었습니다.
</div>

---

## C 프로그램의 구조 이해하기

방금 작성한 Hello World 프로그램을 다시 살펴보면서 C 프로그램의 기본 구조를 이해해봅시다.

### main() 함수의 역할

```c
#include <stdio.h>

int main() {
    printf("Hello World!\n");
    return 0;
}
```

모든 C 프로그램은 반드시 `main()` 함수를 포함해야 합니다. 프로그램이 실행되면 컴퓨터는 가장 먼저 `main()` 함수를 찾아 그 안의 코드를 실행합니다.

<div style="background-color: #f9fafb; padding: 20px; border-radius: 8px; margin: 20px 0;">
<strong>main() 함수 = 프로그램의 시작점</strong><br><br>
<code>main()</code> 함수가 없는 C 프로그램은 실행될 수 없습니다. 마치 건물의 정문과 같은 역할을 합니다.
</div>

#### 간단한 실험

다음 코드를 작성하고 실행해보세요:

```c
int main() {
    return 0;
}
```

이 프로그램은 아무것도 출력하지 않지만, 정상적으로 컴파일되고 실행됩니다. `main()` 함수만 있으면 최소한의 C 프로그램이 완성되는 것입니다.

### 헤더 파일이란?

`#include <stdio.h>`는 무엇일까요?

**헤더 파일**은 프로그램에서 사용할 함수들이 어떻게 동작하는지 미리 정의해놓은 파일입니다. 마치 도구 상자에서 필요한 도구를 꺼내 쓰는 것과 같습니다.

#### stdio.h의 역할

- `stdio.h`는 **Standard Input Output**의 약자입니다
- `printf()`, `scanf()` 같은 입출력 함수들이 정의되어 있습니다
- 이 헤더를 포함하지 않으면 `printf()` 함수를 사용할 수 없습니다

#### 헤더 파일 없이 실행하면?

다음 코드를 실행해보세요:

```c
int main() {
    printf("Test");  // 오류 발생!
    return 0;
}
```

컴파일러는 `printf`가 무엇인지 모르기 때문에 오류를 발생시킵니다. 헤더 파일을 포함해야 `printf` 함수를 사용할 수 있습니다.

### C 프로그램의 기본 구조

```c
// 1. 헤더 파일 포함 (전처리기 지시문)
#include <stdio.h>

// 2. main() 함수 정의
int main() {
    // 3. 실행할 명령문들
    printf("Hello World!\n");

    // 4. 프로그램 종료
    return 0;
}
```

<div style="background-color: #f0f4f8; padding: 20px; border-radius: 8px; margin: 20px 0; border-left: 4px solid #203BB0;">
<strong>구조 요약</strong>
<ol style="margin-top: 10px;">
<li><strong>헤더 파일</strong>: 필요한 함수들을 사용하기 위해 포함</li>
<li><strong>main() 함수</strong>: 프로그램의 시작점</li>
<li><strong>중괄호 { }</strong>: 코드 블록을 묶어주는 역할</li>
<li><strong>세미콜론 ;</strong>: 각 명령문의 끝을 표시</li>
<li><strong>return 0</strong>: 프로그램이 정상적으로 종료되었음을 의미</li>
</ol>
</div>

### 주요 개념 정리

#### 함수 (Function)

여러 명령어를 하나로 묶어놓은 것입니다. `printf()`도 함수이고, `main()`도 함수입니다.

```c
함수이름() {
    실행할 내용
}
```

#### 전처리기 (Preprocessor)

`#include`처럼 `#`으로 시작하는 명령은 컴파일 전에 먼저 처리됩니다. 이를 전처리기 지시문이라고 합니다.

#### 코드 블록 (Code Block)

중괄호 `{ }`로 묶인 영역을 말합니다. 여러 명령문을 하나의 그룹으로 묶을 때 사용합니다.

```c
int main() {
    // 이 부분이 코드 블록
    printf("첫 번째 줄\n");
    printf("두 번째 줄\n");
}
```

### 실습: 다양한 헤더 파일

자주 사용되는 헤더 파일들:

```c
#include <stdio.h>   // 입출력 함수
#include <stdlib.h>  // 메모리 할당, 난수 생성 등
#include <string.h>  // 문자열 처리 함수
#include <math.h>    // 수학 함수
```

---

### 컴파일 과정 이해하기

C 언어는 **컴파일 언어**입니다. 작성한 코드(소스 코드)가 바로 실행되는 것이 아니라, 컴파일러를 통해 기계어로 변환되는 과정을 거칩니다.

```
소스 코드(.c) → [컴파일러] → 실행 파일(.exe 또는 바이너리)
```

**gcc 명령어 옵션:**
- `gcc`: GCC 컴파일러 실행
- `hello.c`: 컴파일할 소스 파일
- `-o hello`: 출력 파일 이름 지정 (`-o`는 output의 약자)
- 옵션을 생략하면 `a.out` (macOS) 또는 `a.exe` (Windows)로 생성됩니다

---

### 문제 해결

#### gcc를 인식하지 못하는 경우

**Windows:**
- 환경 변수에 MinGW의 bin 폴더가 제대로 추가되었는지 확인
- 명령 프롬프트를 재시작

**macOS:**
- Xcode Command Line Tools가 제대로 설치되었는지 확인
- `xcode-select --install` 재실행

#### VSCode에서 IntelliSense가 작동하지 않는 경우

1. C/C++ Extension이 제대로 설치되었는지 확인
2. VSCode 재시작
3. `c_cpp_properties.json` 파일 설정 확인

---

