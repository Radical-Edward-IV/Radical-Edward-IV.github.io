---
layout: article
title: 2. 스크립트 언어와 쉘 명령어
permalink: /notes/kr/info-processing-technician/chapter-03
key: notes
sidebar:
  nav: notes-kr
aside:
  toc: true
excerpt: 프로그래밍기능사 실기 대비 - 스크립트 언어의 종류와 특징, UNIX/Linux 쉘 명령어를 학습합니다.
keywords: "프로그래밍기능사, 스크립트 언어, JavaScript, Python, PHP, 쉘 명령어, UNIX, Linux"
---

<script src="/assets/js/quiz.js"></script>

<style>
    .quiz-container {
        margin: 20px 0;
        padding: 15px;
        border: 1px solid #e5e7eb;
        border-radius: 12px;
        background-color: #ffffff;
        box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);
    }
    .quiz-number {
        display: inline-block;
        background-color: #203BB0;
        color: white;
        padding: 5px 12px;
        border-radius: 15px;
        margin-right: 10px;
        font-size: 0.9em;
    }
    .red-text { color: #D53C41; font-weight: bold; }
    .blue-text { color: #203BB0; font-weight: bold; }
    .green-text { color: #448F52; font-weight: bold; }
    .yellow-code { color: #BD8739; font-weight: bold; }
</style>

![header](https://capsule-render.vercel.app/api?type=waving&height=300&color=gradient&text=%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EA%B8%B0%EB%8A%A5%EC%82%AC&reversal=false&textBg=false)

---

## SECTION 01. 스크립트 언어

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
스크립트 언어를 <span class="blue-text">서버용</span>과 <span class="blue-text">클라이언트용</span>으로 구분하여 정리하고, 각 언어별 특징을 명확히 파악해 두세요.
</p>
</div>

### 1.1 스크립트 언어의 개념

<span class="blue-text">스크립트 언어(Script Language)</span>는 HTML 문서 안에 프로그래밍 코드를 직접 삽입하여 사용할 수 있는 언어입니다.

**핵심 특징**
- 기계어로 컴파일하지 않고 별도의 번역기(인터프리터)가 소스를 분석하여 즉시 실행
- 게시판 처리, 상품 검색, 회원가입 등 데이터베이스 처리 작업에 주로 사용

**스크립트 언어의 분류**

| 분류 | 설명 | 대표 언어 |
|------|------|-----------|
| 서버용 스크립트 | 서버에서 해석 및 실행 후 결과만 클라이언트로 전송 | ASP, JSP, PHP, Python |
| 클라이언트용 스크립트 | 클라이언트의 웹 브라우저에서 해석 및 실행 | JavaScript, VBScript |

---

### 1.2 주요 스크립트 언어

| 언어 | 주요 특징 |
|------|-----------|
| **JavaScript** | 웹 페이지의 동작을 제어하는 클라이언트용 스크립트 언어. 클래스가 없고 변수 선언이 필수가 아님. 입력값 확인 용도로 많이 사용됨 |
| **VBScript** | 마이크로소프트가 JavaScript에 대응하여 제작한 언어. Active X를 통해 MS 애플리케이션 제어 가능 |
| **ASP** | 마이크로소프트가 제작한 서버 측 동적 페이지 언어. Windows 환경에서만 실행 가능 |
| **JSP** | Java 기반 서버용 스크립트 언어. 다양한 운영체제에서 실행 가능 |
| **PHP** | Linux, Unix, Windows에서 모두 사용 가능한 서버용 스크립트 언어. C, Java와 문법이 유사하여 학습하기 쉬움 |
| **Python** | 객체지향 기능을 지원하는 대화형 인터프리터 언어. 플랫폼 독립적이며 문법이 간결함 |
| **Shell Script** | UNIX/Linux 쉘에서 사용되는 명령어 조합. 선택형(if, case), 반복형(for, while, until) 제어문 사용 |
| **Basic** | 절차지향 대화형 인터프리터 언어. 초보자도 쉽게 사용할 수 있는 문법 구조 |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">참고 용어</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
<strong>인터프리터 언어</strong>: 원시 프로그램을 한 줄씩 번역하여 즉시 실행하는 언어. 목적 프로그램을 생성하지 않음.<br><br>
<strong>쉘(Shell)</strong>: 사용자의 명령을 해석하여 프로그램을 호출하고 실행하는 명령 해석기.
</p>
</div>

---

### 1.3 관련 기술: XML, JSON, AJAX

| 기술 | 설명 |
|------|------|
| **XML** (eXtensible Markup Language) | 특수 목적의 마크업 언어를 만드는 데 사용되는 다목적 마크업 언어. HTML의 상호 호환 문제와 SGML의 복잡함을 해결하기 위해 개발됨 |
| **JSON** (JavaScript Object Notation) | 속성-값 쌍(Attribute-Value Pairs)으로 이루어진 데이터 객체를 전달하기 위한 개방형 표준 포맷. 사람이 읽을 수 있는 텍스트 사용. AJAX에서 XML을 대체하여 사용됨 |
| **AJAX** (Asynchronous JavaScript and XML) | JavaScript 등을 이용하여 클라이언트와 서버 간에 XML 데이터를 비동기적으로 교환하며, 웹 페이지와 자유롭게 상호작용할 수 있게 하는 통신 기술 |

---

## SECTION 02. 쉘(Shell) 명령어

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">💡</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">학습 TIP</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
UNIX/Linux 명령어는 실기 시험에서 자주 출제됩니다. 각 명령어의 기능과 사용 예시를 정확히 암기하세요.
</p>
</div>

### 2.1 명령어의 기본 형식

```
[프롬프트] 명령어 [옵션] [매개변수]
```

**주의사항**
- 프롬프트는 쉘 종류에 따라 다름 ($, %, #)
- 명령어는 **대소문자를 구분**하여 입력
- 명령어와 옵션 사이에는 공백 필요, 옵션 앞에는 `-` 기호 사용
- `명령어 --help`로 해당 명령어의 옵션 확인 가능

---

### 2.2 시스템 및 프로세스 관련 명령어

| 명령어 | 기능 | 사용 예시 |
|--------|------|-----------|
| **kill** | PID(프로세스 고유 번호)로 프로세스 종료 | `kill 1234` |
| **killall** | 프로세스 이름으로 해당 프로세스 모두 종료 | `killall myprocess` |
| **finger** | 현재 시스템에 등록된 사용자 정보 조회 | `finger` 또는 `finger kim` |
| **ps** | 현재 실행 중인 프로세스 표시 | `ps` |
| **login** | 사용자 ID와 비밀번호로 세션 시작 | `login kim` |
| **logout** | 쉘 접속 종료 | `logout` |
| **passwd** | 비밀번호 설정 또는 변경 | `passwd` |
| **who** | 현재 시스템에 접속 중인 사용자 표시 | `who` |
| **fsck** | 파일 시스템 검사 및 복구 | `fsck /dev/sda1` |
| **top** | 프로세스와 메모리 사용 현황 표시 | `top` |

---

### 2.3 네트워크 관련 명령어

| 명령어 | 기능 | 사용 예시 |
|--------|------|-----------|
| **ping** | IP 주소나 도메인으로 특정 서버의 연결 상태 확인 | `ping example.com` 또는 `ping 192.168.0.1` |
| **ifconfig** | IP 주소, 서브넷 마스크, MAC 주소 등 네트워크 인터페이스 상태 표시 | `ifconfig` |

---

### 2.4 디렉터리 관련 명령어

| 명령어 | 기능 | 사용 예시 |
|--------|------|-----------|
| **pwd** | 현재 작업 중인 디렉터리 경로 표시 | `pwd` |
| **ls** | 현재 디렉터리의 파일 목록 표시 | `ls` |
| **mkdir** | 디렉터리 생성 | `mkdir mydir` |
| **rmdir** | 디렉터리 삭제 | `rmdir mydir` |
| **cd** | 디렉터리 위치 변경 | `cd mydir` |

**경로 표기법**

| 기호 | 의미 | 사용 예시 |
|------|------|-----------|
| `.` | 현재 디렉터리 | `./script.sh` (현재 디렉터리의 script.sh 실행) |
| `..` | 상위 디렉터리 | `cd ..` (상위 디렉터리로 이동) |
| `/` | 루트 디렉터리 (최상위) | `cd /` (루트 디렉터리로 이동) |

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">
<div style="display: flex; align-items: center; gap: 10px; margin-bottom: 12px;">
<span style="font-size: 1.25rem;">📌</span>
<strong style="font-size: 1rem; font-weight: 600; color: #111827; letter-spacing: -0.01em;">절대 경로 vs 상대 경로</strong>
</div>
<p style="margin: 0; font-size: 0.95rem; line-height: 1.6; color: #4b5563;">
• <strong>절대 경로</strong>: /로 시작하며, 루트 디렉터리 기준 (예: /home/user/docs)<br>
• <strong>상대 경로</strong>: /로 시작하지 않으며, 현재 디렉터리 기준 (예: ../src/test)
</p>
</div>

---

### 2.5 파일 관련 명령어

| 명령어 | 기능 | 사용 예시 |
|--------|------|-----------|
| **cp** | 파일 복사 | `cp file.txt backup/file2.txt` |
| **rm** | 파일 삭제 | `rm file.txt` |
| **cat** | 파일 내용을 화면에 표시 | `cat file.txt` |
| **mv** | 파일 이동 | `mv file.txt dir/file2.txt` |
| **find** | 파일 검색 | `find file.txt` |
| **chmod** | 파일/디렉터리 접근 권한 변경 | `chmod u=rwx file.txt` |
| **chown** | 파일 소유자와 그룹 변경 | `chown member1 file.txt` |
| **tar** | 파일 압축 또는 해제 | `tar cvf archive.tar` / `tar xvf archive.tar` |
| **head** | 파일 앞부분 출력 (기본 10행) | `head -n 5 file.txt` |

---

### 2.6 chmod 명령어 상세

**문자 모드**

| 구분 | 기호 | 의미 |
|------|------|------|
| 사용자 | u | user (소유자) |
| | g | group (그룹) |
| | o | other (다른 사용자) |
| | a | all (모두) |
| 설정기호 | + | 권한 추가 |
| | - | 권한 삭제 |
| | = | 권한 부여 |
| 권한 | r | read (읽기) |
| | w | write (쓰기) |
| | x | execute (실행) |

**숫자 모드 (8진법)**

권한을 이진수로 변환 후 8진수로 표현합니다.

```
예) rwx rwx r-x
    111 111 101  → 이진수
     7   7   5   → 8진수

chmod 775 script.sh
```

**UNIX 파일 권한 표기 예시**
```
-rwxrwxr-x
│ │  │  └── 기타 사용자: 읽기, 실행 가능
│ │  └───── 그룹: 읽기, 쓰기, 실행 가능
│ └──────── 소유자: 읽기, 쓰기, 실행 가능
└────────── 파일 구분 (- : 파일, d : 디렉터리)
```

---

### 2.7 tar 명령어 옵션

| 옵션 | 기능 |
|------|------|
| f | 압축/해제 시 기본 사용 옵션 |
| c | 압축할 때 사용 |
| x | 압축 해제할 때 사용 |
| v | 처리 과정 상세 표시 |

---

## 연습문제

<div class="quiz-number">문제 1</div><strong>UNIX에서 파일 내용을 화면에 출력하는 명령어를 작성하시오.</strong>

{% include quiz-text.html
   id="quiz1_shell"
   answer="cat"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 2</div><strong>현재 작업 디렉터리가 `/Users/dev/workspace/project`일 때, 상대 경로 `../../data/files`의 절대 경로를 작성하시오.</strong>

{% include quiz-text.html
   id="quiz2_shell"
   answer="/Users/dev/data/files"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 3</div><strong>다음 기능에 해당하는 Linux 명령어를 쉼표(,)로 구분하여 작성하시오.</strong>

{% capture code_block3 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 파일이나 디렉터리의 접근 권한을 변경하는 명령어<br>
② 현재 작업 중인 디렉터리 경로를 표시하는 명령어
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz3_shell"
   code_html=code_block3
   answer="chmod, pwd|chmod,pwd"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 4</div><strong>JavaScript 등을 이용하여 클라이언트와 서버 간 비동기 방식으로 데이터를 교환하며, 페이지 전체를 새로고침하지 않고 일부 영역만 업데이트하는 기술을 작성하시오.</strong>

{% include quiz-text.html
   id="quiz4_script"
   answer="AJAX"
   tags="스크립트 언어"
%}

---

<div class="quiz-number">문제 5</div><strong>테이프 아카이브에서 유래되어, UNIX/Linux에서 여러 파일을 하나로 묶거나 묶인 파일을 풀 때 사용하는 명령어를 작성하시오.</strong>

{% include quiz-text.html
   id="quiz5_shell"
   answer="tar"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 6</div><strong>다음 기능에 해당하는 Linux 명령어를 쉼표(,)로 구분하여 작성하시오.</strong>

{% capture code_block6 %}
<div style="margin: 15px 0; line-height: 1.8;">
① IP 주소, 서브넷 마스크, MAC 주소 등 네트워크 인터페이스의 현재 상태를 표시한다.<br>
② IP 주소나 도메인 이름으로 특정 서버의 연결 상태를 확인한다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz6_shell"
   code_html=code_block6
   answer="ifconfig, ping|ifconfig,ping"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 7</div><strong>속성-값 쌍(Attribute-Value Pairs) 형태로 구조적 데이터를 표현하며, 사람이 읽을 수 있는 텍스트를 사용하는 데이터 교환용 개방형 표준 포맷을 작성하시오.</strong>

{% include quiz-text.html
   id="quiz7_script"
   answer="JSON"
   tags="스크립트 언어"
%}

---

<div class="quiz-number">문제 8</div><strong>영어 'List'에서 파생된 단어로, Linux에서 현재 디렉터리의 파일 목록을 표시하는 명령어를 작성하시오.</strong>

{% include quiz-text.html
   id="quiz8_shell"
   answer="ls"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 9</div><strong>다음 내용에 해당하는 UNIX 명령문을 쉼표(,)로 구분하여 작성하시오.</strong>

{% capture code_block9 %}
<div style="margin: 15px 0; line-height: 1.8;">
① backup이라는 디렉터리를 삭제한다.<br>
② project라는 디렉터리를 생성한다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz9_shell"
   code_html=code_block9
   answer="rmdir backup, mkdir project|rmdir backup,mkdir project"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 10</div><strong>현재 작업 디렉터리가 `/home/user/documents`일 때, 상대 경로 `../../pictures`의 절대 경로를 작성하시오.</strong>

{% include quiz-text.html
   id="quiz10_shell"
   answer="/home/pictures"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 11</div><strong>다음 기능에 해당하는 Linux 명령어를 쉼표(,)로 구분하여 작성하시오.</strong>

{% capture code_block11 %}
<div style="margin: 15px 0; line-height: 1.8;">
① 파일 시스템을 검사하고 보수하는 명령어<br>
② 시스템의 프로세스와 메모리 사용 현황을 표시하는 명령어<br>
③ 현재 시스템에 등록되어 있는 사용자 정보를 조회하는 명령어
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz11_shell"
   code_html=code_block11
   answer="fsck, top, finger|fsck,top,finger"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 12</div><strong>UNIX에서 현재 디렉터리의 source.txt 파일을 backup 디렉터리로 이동하면서 파일명을 target.txt로 변경하는 명령문을 작성하시오.</strong>

{% include quiz-text.html
   id="quiz12_shell"
   answer="mv source.txt backup/target.txt"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 13</div><strong>소유자(user)에게 report.txt 파일의 읽기, 쓰기, 실행 권한을 추가하는 명령어를 작성하시오.</strong>

{% include quiz-text.html
   id="quiz13_shell"
   answer="chmod u+rwx report.txt|chmod u=rwx report.txt"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 14</div><strong>다음 UNIX 명령어와 기능의 연결이 올바른 것을 쉼표(,)로 구분하여 작성하시오. (예: ①-ⓐ, ②-ⓑ)</strong>

{% capture code_block14 %}
<div style="margin: 15px 0; line-height: 1.8;">
① ls<br>
② kill<br>
③ cat<br>
④ fsck<br><br>
ⓐ 파일 내용을 화면에 표시한다.<br>
ⓑ 현재 디렉터리의 파일 목록을 표시한다.<br>
ⓒ 파일 시스템을 검사하고 보수한다.<br>
ⓓ PID를 이용하여 프로세스를 종료한다.
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz14_shell"
   code_html=code_block14
   answer="①-ⓑ, ②-ⓓ, ③-ⓐ, ④-ⓒ|①ⓑ,②ⓓ,③ⓐ,④ⓒ"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 15</div><strong>UNIX에서 시스템의 프로세스와 메모리 사용 현황을 실시간으로 표시하는 명령어를 작성하시오.</strong>

{% include quiz-text.html
   id="quiz15_shell"
   answer="top"
   tags="쉘 명령어"
%}

---

<div class="quiz-number">문제 16</div><strong>Linux에서 config.txt 파일에 대해 다음 조건의 권한을 부여하는 명령문을 8진법 숫자를 이용하여 작성하시오.</strong>

{% capture code_block16 %}
<div style="margin: 15px 0; line-height: 1.8;">
• 소유자(user): 읽기, 쓰기, 실행 권한<br>
• 그룹(group): 읽기, 실행 권한<br>
• 기타 사용자(other): 읽기, 실행 권한
</div>
{% endcapture %}

{% include quiz-text.html
   id="quiz16_shell"
   code_html=code_block16
   answer="chmod 755 config.txt"
   tags="쉘 명령어"
%}

---

## 핵심 요약

<div style="background: #ffffff; padding: 24px; border-radius: 12px; margin: 32px 0; border: 1px solid #e5e7eb; box-shadow: 0 1px 3px rgba(0, 0, 0, 0.05), 0 4px 12px rgba(0, 0, 0, 0.04);">

<h3 style="margin-top: 0; margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">스크립트 언어</h3>
<ul style="margin: 0 0 24px 0; padding-left: 20px; color: #4b5563;">
<li><strong>개념</strong>: HTML 문서에 삽입하여 사용하는 언어, 인터프리터로 즉시 실행</li>
<li><strong>서버용</strong>: ASP, JSP, PHP, Python</li>
<li><strong>클라이언트용</strong>: JavaScript, VBScript</li>
<li><strong>관련 기술</strong>: XML(마크업 언어), JSON(데이터 교환 포맷), AJAX(비동기 통신)</li>
</ul>

<h3 style="margin-bottom: 16px; font-size: 1.1rem; font-weight: 600; color: #111827;">쉘 명령어</h3>
<ul style="margin: 0; padding-left: 20px; color: #4b5563;">
<li><strong>시스템/프로세스</strong>: kill, killall, ps, top, who, finger, passwd, fsck</li>
<li><strong>네트워크</strong>: ping, ifconfig</li>
<li><strong>디렉터리</strong>: pwd, ls, mkdir, rmdir, cd</li>
<li><strong>파일</strong>: cp, rm, mv, cat, find, chmod, chown, tar, head</li>
<li><strong>경로</strong>: . (현재), .. (상위), / (루트)</li>
<li><strong>chmod 권한</strong>: r(4), w(2), x(1) → 8진수로 표현 (예: 755)</li>
</ul>

</div>

---
