# Claude Code 핸즈온 가이드
### 설치부터 배포까지 — 4시간 실습 완성

> 이 문서는 강의 중 수강생이 직접 따라 하는 단계별 실습 가이드입니다.  
> 막히는 부분이 있으면 옆 사람과 비교하거나 강사에게 질문하세요.

---

## 사전 준비 (강의 전에 완료)

설치는 강의 중 Part 1에서 함께 진행합니다.  
아래 두 가지는 **강의 시작 전에 미리** 준비해 오세요.

- [ ] GitHub 계정 만들기 ([github.com](https://github.com) → Sign up)
- [ ] claude.ai 계정 만들기 + **Pro 또는 Max 플랜** 구독 ([claude.ai](https://claude.ai))

---

---

# PART 1. 설치 & 첫 대화 (50분)

## 1-1. VS Code 설치

### 다운로드 및 설치

**Windows:**
1. [code.visualstudio.com](https://code.visualstudio.com) 접속
2. **Download for Windows** 버튼 클릭 → `.exe` 파일 다운로드
3. 다운로드된 파일 실행 → 설치 옵션은 기본값 유지
4. 설치 중 **"PATH에 추가"** 옵션이 있으면 반드시 체크
5. 설치 완료 후 VS Code 실행 확인

**Mac:**
1. [code.visualstudio.com](https://code.visualstudio.com) 접속
2. **Download for Mac** 버튼 클릭 → `.zip` 파일 다운로드
3. 다운로드된 `.zip` 파일 더블클릭 → `Visual Studio Code.app` 압축 해제
4. `Visual Studio Code.app`을 **응용 프로그램(Applications)** 폴더로 드래그
5. VS Code 실행 후 상단 메뉴 → **Shell Command: Install 'code' command in PATH** 실행

> **Mac에서 PATH 등록이 중요한 이유**: 나중에 터미널에서 `code .` 명령으로 폴더를 VS Code로 바로 열 수 있습니다.

---

## 1-2. Node.js 설치

Claude Code는 Node.js 위에서 동작합니다. 반드시 설치가 필요합니다.

### 다운로드 및 설치

**Windows:**
1. [nodejs.org](https://nodejs.org) 접속
2. **LTS** 버전 다운로드 버튼 클릭 (예: `v20.x.x LTS`)
3. 다운로드된 `.msi` 파일 실행
4. 설치 옵션은 모두 기본값으로 진행 → **Next** 계속 클릭
5. 설치 완료 후 **PowerShell** 또는 **명령 프롬프트** 새로 열기
6. 아래 명령으로 설치 확인:

```bash
node --version
npm --version
```

**Mac:**
1. [nodejs.org](https://nodejs.org) 접속
2. **LTS** 버전 다운로드 버튼 클릭 (예: `v20.x.x LTS`)
3. 다운로드된 `.pkg` 파일 실행
4. 설치 옵션은 모두 기본값으로 진행 → **계속** 클릭
5. 설치 완료 후 **터미널** 새로 열기 (기존 터미널은 닫고 새로 열어야 반영됨)
6. 아래 명령으로 설치 확인:

```bash
node --version
npm --version
```

**정상 출력 예시:**
```
v20.11.0
10.2.4
```

> 버전 숫자가 나오면 OK. 숫자 앞의 `v`는 version의 약자입니다.

---

## 1-3. Git 설치

Part 4 배포 실습에서 `git commit`, `git push`를 사용합니다. 반드시 설치가 필요합니다.

**Windows:**
1. [git-scm.com](https://git-scm.com) 접속 → **Download for Windows** 클릭
2. 다운로드된 `.exe` 파일 실행
3. 설치 옵션은 모두 기본값 → **Next** 계속 클릭
4. **"Git Credential Manager"** 옵션이 나오면 체크 상태 유지
5. 설치 완료 후 PowerShell 새로 열고 확인:

```bash
git --version
```

**Mac:**

터미널에서 아래 명령어를 실행하세요:

```bash
git --version
```

Git이 없으면 **"개발자 도구를 설치하겠습니까?"** 팝업이 자동으로 뜹니다.  
**설치** 버튼을 클릭하면 Xcode Command Line Tools가 설치되며 Git이 포함됩니다.

> Mac에서 Homebrew는 필수가 아닙니다. Xcode CLI 도구만으로 Git을 사용할 수 있습니다.

**정상 출력 예시:**
```
git version 2.x.x
```

---

## 1-4. Claude Code 설치

Node.js 설치가 완료되었으면 Claude Code를 설치합니다.

**터미널 여는 방법:**
- Windows: VS Code 상단 메뉴 → 터미널 → 새 터미널 (또는 `` Ctrl+` ``)
- Mac: VS Code 상단 메뉴 → 터미널 → 새 터미널 (또는 `` Cmd+` ``)

아래 명령어를 실행하세요:

```bash
npm install -g @anthropic-ai/claude-code
```

> `-g` 옵션은 전역(global) 설치를 의미합니다. 어떤 폴더에서든 `claude` 명령을 쓸 수 있게 됩니다.

설치 완료 후 확인:

```bash
claude --version
```

**정상 출력 예시:**
```
1.x.x
```

---

## 1-5. Claude 구독 계정으로 로그인

Claude Code는 **API 키 없이 claude.ai 구독 계정(Pro/Max 플랜)으로 바로 사용**할 수 있습니다.

### 로그인 실행

```bash
claude
```

처음 실행하면 아래와 같은 인증 선택 화면이 나타납니다:

```
How would you like to authenticate?
❯ claude.ai account (Pro or Max plan)
  Anthropic API key
```

키보드 방향키로 **첫 번째 항목(claude.ai account)** 을 선택하고 Enter를 누르세요.

### 브라우저 인증

1. 터미널에 인증 URL이 표시됩니다
2. URL을 복사해 브라우저에 붙여넣거나, 자동으로 브라우저가 열립니다
3. claude.ai 로그인 페이지에서 **본인 계정으로 로그인**
4. **"Authorize Claude Code"** 버튼 클릭
5. 터미널로 돌아오면 로그인 완료 메시지 확인

> **구독 플랜 확인**: Pro 또는 Max 플랜이어야 합니다.  
> Free 플랜은 Claude Code를 지원하지 않습니다.  
> 플랜 확인: [claude.ai](https://claude.ai) → 우측 상단 프로필 → Plan

---

## 1-6. VS Code 확장 설치

1. VS Code 실행
2. 좌측 Extensions 아이콘 클릭
   - Windows: `Ctrl+Shift+X`
   - Mac: `Cmd+Shift+X`
3. 검색창에 `Claude Code` 입력
4. **Claude Code** (Anthropic 제작) → **Install** 클릭

설치 후 VS Code 좌측 사이드바에 Claude Code 아이콘이 생깁니다.  
아이콘을 클릭하면 터미널 없이 패널에서 바로 대화할 수 있습니다.

---

## 1-7. 첫 대화 실습

VS Code 사이드패널의 Claude Code를 열거나, 터미널에서 `claude`를 실행해 대화해보세요.

### 실습 프롬프트 1 — 자기소개 요청
```
안녕! 너는 어떤 걸 잘 할 수 있어?
```

### 실습 프롬프트 2 — 파일 생성 요청
```
hello.txt 파일을 만들고 "안녕하세요, Claude Code입니다!"라고 적어줘
```

만들어진 파일을 VS Code 탐색기(왼쪽 파일 목록)에서 확인해보세요.

### 실습 프롬프트 3 — 코드 생성 요청
```
Python으로 1부터 10까지 숫자를 출력하는 코드를 count.py 파일로 만들어줘
```

### 실습 프롬프트 4 — 코드 설명 요청
```
방금 만든 count.py 코드를 초보자도 이해할 수 있게 설명해줘
```

### 실습 프롬프트 5 — 코드 수정 요청
```
count.py에서 짝수만 출력하도록 수정해줘
```

> **핵심 포인트**: Claude Code는 실제 파일을 직접 읽고, 수정하고, 생성합니다.  
> 일반 챗GPT처럼 코드를 "보여주는" 게 아니라 "실제로 작업"합니다.

---

### Part 1 체크포인트

- [ ] VS Code가 정상 실행되는가
- [ ] `node --version` 명령이 정상 출력되는가
- [ ] `git --version` 명령이 정상 출력되는가
- [ ] `claude --version` 명령이 정상 출력되는가
- [ ] VS Code에서 Claude Code 확장 아이콘이 보이는가
- [ ] hello.txt 파일이 실제로 생성되었는가
- [ ] count.py 파일이 짝수만 출력하도록 수정되었는가

---

---

# PART 2. 나만의 링크트리 만들기 (70분)

## 2-1. Plan 모드란? (이론 15분)

### Plan 모드가 필요한 이유

Claude Code에는 두 가지 작업 방식이 있습니다.

| 방식 | 특징 | 적합한 상황 |
|------|------|-------------|
| **즉시 실행** | 요청하면 바로 파일 수정 | 간단한 수정, 한 파일 작업 |
| **Plan 모드** | 계획 먼저 → 내가 확인 → 실행 | 여러 파일 생성, 구조가 있는 작업 |

### Plan 모드 흐름

```
내가 요청
    ↓
Claude가 계획 제시
    ↓
내가 검토 & 승인 (또는 수정 요청)
    ↓
Claude가 실행
```

### Plan 모드를 써야 할 때

- 새 프로젝트를 처음 만들 때
- 여러 파일을 한번에 생성/수정할 때
- 잘못 실행되면 되돌리기 어려운 작업일 때
- 결과물의 구조를 미리 확인하고 싶을 때

---

## 2-2. 프로젝트 폴더 만들기

원하는 위치로 이동한 뒤 폴더를 만드세요.

**Windows (PowerShell 또는 명령 프롬프트):**
```bash
cd C:\Users\사용자명\Documents
mkdir my-linktree
cd my-linktree
```

**Mac (터미널):**
```bash
cd ~/Documents
mkdir my-linktree
cd my-linktree
```

VS Code에서 해당 폴더를 열기 (공통):
```bash
code .
```

> `code .` 명령이 동작하지 않으면 VS Code에서 **파일 → 폴더 열기**로 직접 선택하세요.

---

## 2-3. CLAUDE.md 설정 (프로젝트 규칙 등록)

CLAUDE.md는 Claude Code에게 이 프로젝트에 대한 맥락을 알려주는 파일입니다.  
프로젝트 루트에 직접 만들어도 되고, 아래 프롬프트로 만들어도 됩니다.

### 실습 프롬프트
```
이 프로젝트는 개인 링크트리 웹페이지야.
순수 HTML, CSS, JavaScript만 사용하고 외부 라이브러리는 쓰지 않아.
파일 구조는 index.html, style.css, script.js로 구성해줘.
한국어로 작업해줘.
이 내용을 CLAUDE.md 파일로 만들어줘.
```

생성된 CLAUDE.md를 열어서 내용을 확인하세요.

---

## 2-4. 링크트리 만들기 — Plan 모드 실습

### 실습 프롬프트 (Plan 모드 진입)
```
Plan 모드로 진행해줘.

내 링크트리 페이지를 만들어줘. 요구사항은 아래와 같아:

- 상단에 프로필 사진 자리 (원형, 100x100px)
- 내 이름과 한 줄 소개
- 링크 버튼 5개:
  1. GitHub - https://github.com/내아이디
  2. 인스타그램 - https://instagram.com/내아이디
  3. 유튜브 - https://youtube.com/@내채널
  4. 블로그 - https://내블로그주소
  5. 이메일 - mailto:내이메일@gmail.com
- 배경색은 부드러운 그라디언트
- 버튼은 hover 시 살짝 올라오는 애니메이션
- 모바일에서도 잘 보이는 반응형 디자인
```

Claude가 계획을 보여주면:
1. 파일 구조를 확인하세요
2. 내용이 마음에 들면 **승인(yes/y)** 입력
3. 수정이 필요하면 구체적으로 요청

---

## 2-5. 결과 확인

생성된 파일 확인:

**Windows:**
```bash
dir
```
**Mac:**
```bash
ls
```

브라우저에서 바로 열기:

**Windows:**
```bash
start index.html
```
**Mac:**
```bash
open index.html
```

또는 VS Code에서 `index.html` 파일 우클릭 → **Open with Live Server** (Live Server 확장 필요, Windows/Mac 공통)

---

## 2-6. 추가 실습 — 멀티턴 수정 경험하기

### 실습 A: 다크모드 토글 추가
```
현재 링크트리에 다크모드/라이트모드 토글 버튼을 추가해줘.
오른쪽 상단에 🌙 / ☀️ 아이콘 버튼으로 만들고,
선택한 모드는 localStorage에 저장해서 새로고침해도 유지되게 해줘.
```

### 실습 B: 방문 카운터 추가
```
페이지 하단에 "오늘 N명이 방문했습니다" 텍스트를 추가해줘.
localStorage를 사용해서 방문 횟수를 저장하고,
페이지를 새로 열 때마다 카운트가 올라가게 해줘.
```

### 실습 C: 링크 정보 수정
```
내 실제 정보로 링크트리 내용을 수정해줘:
- 이름: [본인 이름 입력]
- 소개: [한 줄 소개 입력]
- GitHub: [본인 GitHub URL]
- 이메일: [본인 이메일]
나머지 링크는 임시로 # 처리해줘.
```

> **핵심 포인트**: 한 번에 완벽하게 만들려 하지 않아도 됩니다.  
> "이거 수정해줘", "이거 추가해줘"처럼 대화하듯 이어가는 게 Claude Code의 핵심 사용법입니다.

---

### Part 2 체크포인트

- [ ] CLAUDE.md 파일이 생성되었는가
- [ ] index.html, style.css, script.js 3개 파일이 만들어졌는가
- [ ] 브라우저에서 링크트리 페이지가 열리는가
- [ ] 다크모드 토글 버튼이 동작하는가

---

---

# PART 3. Playwright MCP 실습 (60분)

## 3-1. MCP란? (이론 10분)

### MCP (Model Context Protocol)

Claude Code는 기본적으로 파일 시스템과 터미널만 다룰 수 있습니다.  
MCP는 Claude Code에게 **외부 도구를 연결하는 플러그인 시스템**입니다.

```
Claude Code
    ├── 기본 기능: 파일 읽기/쓰기, 터미널 실행
    └── MCP 연결 시:
            ├── Playwright → 브라우저 자동화
            ├── Notion → 노션 문서 읽기/쓰기
            ├── Google Drive → 구글 드라이브 연동
            └── 기타 수백 가지 도구...
```

### Playwright MCP

Playwright는 브라우저를 코드로 제어하는 도구입니다.  
Playwright MCP를 연결하면 Claude Code가 직접 브라우저를 열고, 클릭하고, 입력하고, 스크린샷을 찍을 수 있습니다.

**실습에서 해볼 것:**
- 브라우저 자동으로 열기
- 특정 웹사이트 접속
- 스크린샷 찍기
- 만든 링크트리 페이지 자동 검수

---

## 3-2. Playwright MCP 설치 및 설정

### 설치

```bash
npm install -g @playwright/mcp
```

```bash
npx playwright install chromium
```

### settings.json 설정

커맨드 팔레트를 열어 설정 파일을 수정합니다.

- Windows: `Ctrl+Shift+P` → `Open User Settings (JSON)`
- Mac: `Cmd+Shift+P` → `Open User Settings (JSON)`

또는 아래 경로의 파일을 직접 수정:

- Windows: `C:\Users\사용자명\.claude\settings.json`
- Mac: `~/.claude/settings.json`

파일에 아래 내용을 추가하세요:

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    }
  }
}
```

> 파일이 이미 다른 내용이 있다면 `mcpServers` 부분만 추가하세요.

### 설정 적용

Claude Code를 재시작합니다:
```bash
claude
```

---

## 3-3. Playwright MCP 실습

### 실습 1 — 브라우저 열고 스크린샷 찍기

```
playwright를 사용해서 구글 홈페이지를 열고 스크린샷을 찍어줘.
스크린샷 파일은 screenshot_google.png로 저장해줘.
```

실습 후 `screenshot_google.png` 파일이 생성되었는지 확인하세요.

---

### 실습 2 — 검색 자동화

```
playwright로 네이버(naver.com)에 접속해서
검색창에 "Claude Code 강의"를 입력하고 검색한 뒤
결과 페이지 스크린샷을 screenshot_search.png로 저장해줘.
```

---

### 실습 3 — 내 링크트리 페이지 자동 검수

**Windows 사용자:**
```
playwright를 사용해서 내 링크트리 페이지를 열고 검수해줘.
파일 경로는 C:\Users\사용자명\Documents\my-linktree\index.html 이야.

확인해야 할 것들:
1. 페이지가 정상적으로 열리는지
2. 프로필 영역이 보이는지
3. 링크 버튼 5개가 모두 보이는지
4. 모바일 크기(390px)로 변경했을 때도 잘 보이는지

각 단계별로 스크린샷을 찍고, 발견된 문제가 있으면 알려줘.
```

**Mac 사용자:**
```
playwright를 사용해서 내 링크트리 페이지를 열고 검수해줘.
파일 경로는 /Users/사용자명/Documents/my-linktree/index.html 이야.

확인해야 할 것들:
1. 페이지가 정상적으로 열리는지
2. 프로필 영역이 보이는지
3. 링크 버튼 5개가 모두 보이는지
4. 모바일 크기(390px)로 변경했을 때도 잘 보이는지

각 단계별로 스크린샷을 찍고, 발견된 문제가 있으면 알려줘.
```

> **내 정확한 경로 확인 방법**
> - Windows: 터미널에서 `cd my-linktree && pwd` 또는 탐색기 주소창 확인
> - Mac: 터미널에서 `cd my-linktree && pwd`

---

### 실습 4 — 발견된 문제 자동 수정 (도전 과제)

실습 3에서 Claude Code가 문제를 발견했다면:

```
방금 검수에서 발견된 문제들을 수정해줘.
수정 후 다시 playwright로 확인해줘.
```

> **핵심 포인트**: MCP를 통해 Claude Code가 "눈"을 갖게 됩니다.  
> 코드를 작성하고 → 브라우저로 확인하고 → 문제를 발견하고 → 수정하는 사이클을  
> 사람 개입 없이 자동으로 돌릴 수 있습니다.

---

### Part 3 체크포인트

- [ ] `settings.json`에 MCP 설정이 추가되었는가
- [ ] `screenshot_google.png` 파일이 생성되었는가
- [ ] 링크트리 페이지 검수 스크린샷이 생성되었는가
- [ ] 발견된 문제가 수정되었는가

---

---

# PART 4. GitHub Pages로 배포하기 (60분)

## 4-1. 배포란? (이론 10분)

### 내 컴퓨터 vs 인터넷

지금까지 만든 링크트리는 내 컴퓨터에서만 열립니다.  
**배포(Deploy)**는 이 파일을 인터넷 서버에 올려서 누구나 접근할 수 있게 하는 과정입니다.

### GitHub Pages 선택 이유

| 서비스 | 비용 | 난이도 | 특징 |
|--------|------|--------|------|
| **GitHub Pages** | 무료 | 쉬움 | GitHub과 연동, 정적 사이트 |
| Netlify | 무료(기본) | 쉬움 | 자동 배포 편리 |
| Vercel | 무료(기본) | 보통 | Next.js 친화적 |

오늘은 GitHub Pages를 사용합니다. 무료이고 설정이 간단합니다.

**최종 URL 형태**: `https://내아이디.github.io/my-linktree`

---

## 4-2. Git 초기화 및 첫 커밋

`my-linktree` 폴더에서 진행합니다.

### Git 초기 설정 (처음 사용하는 경우)

```bash
git config --global user.name "본인이름"
git config --global user.email "본인이메일@gmail.com"
```

### 실습 프롬프트 — Git 설정 및 커밋

```
이 프로젝트를 Git으로 관리하려고 해.
아래 순서로 진행해줘:

1. git init으로 저장소 초기화
2. .gitignore 파일 생성 (node_modules, .DS_Store, *.log 제외)
3. 현재 변경사항을 보고 적절한 커밋 메시지를 작성해서 첫 커밋 만들기

커밋 메시지는 한국어로 써줘.
```

---

## 4-3. GitHub 원격 저장소 만들기

1. [github.com](https://github.com) 로그인
2. 우측 상단 **+** → **New repository** 클릭
3. Repository name: `my-linktree`
4. **Public** 선택 (GitHub Pages는 Public 필요)
5. **Create repository** 클릭

---

## 4-4. 로컬 저장소를 GitHub에 연결

GitHub에서 새 저장소를 만들면 아래와 비슷한 명령어가 표시됩니다:

```bash
git remote add origin https://github.com/내아이디/my-linktree.git
git branch -M main
git push -u origin main
```

### 실습 프롬프트
```
GitHub에 방금 my-linktree 저장소를 만들었어.
내 GitHub 아이디는 [본인 아이디] 야.
원격 저장소 연결하고 push까지 해줘.
```

---

## 4-5. GitHub Pages 활성화

1. GitHub에서 `my-linktree` 저장소로 이동
2. 상단 탭 **Settings** 클릭
3. 좌측 메뉴 **Pages** 클릭
4. **Source** → **Deploy from a branch**
5. **Branch** → `main` 선택, 폴더 `/ (root)` → **Save**

1~2분 후 페이지 상단에 아래 메시지가 나타납니다:
```
Your site is live at https://내아이디.github.io/my-linktree
```

해당 링크를 클릭해서 배포된 페이지를 확인하세요!

---

## 4-6. 수정 후 재배포 실습

배포 이후 수정하는 사이클을 경험해봅시다.

### 실습 프롬프트 — 내용 수정
```
링크트리 페이지 하단에 "© 2025 내이름. Made with Claude Code" 라는
저작권 표시를 추가해줘.
```

### 수정사항 확인 및 커밋

```
변경된 내용을 확인하고 적절한 커밋 메시지로 커밋한 뒤 push해줘.
```

push 후 1~2분 기다리면 GitHub Pages가 자동으로 업데이트됩니다.  
배포된 URL을 새로고침해서 변경사항을 확인하세요.

---

## 4-7. Playwright로 배포 결과 확인 (도전 과제)

```
playwright를 사용해서 배포된 내 링크트리를 확인해줘.
URL은 https://내아이디.github.io/my-linktree 야.

페이지가 정상적으로 열리는지,
모든 링크 버튼이 보이는지 확인하고
스크린샷을 screenshot_deployed.png로 저장해줘.
```

---

### Part 4 체크포인트

- [ ] GitHub에 `my-linktree` 저장소가 생성되었는가
- [ ] `git push`가 성공했는가
- [ ] GitHub Pages에서 URL이 발급되었는가
- [ ] 브라우저에서 배포된 페이지가 열리는가
- [ ] 수정 후 재배포가 자동으로 반영되었는가

---

---

# 마무리 정리

## 오늘 배운 흐름

```
Claude Code 설치 & 첫 대화
        ↓
Plan 모드로 링크트리 설계 & 제작
        ↓
Playwright MCP로 브라우저 자동 검수
        ↓
GitHub Pages로 인터넷 배포
```

---

## Claude Code 자주 쓰는 조작법

### 중단 / 취소
| 조작 | 설명 |
|------|------|
| `Esc` | 현재 입력 취소 (타이핑 중일 때) |
| `Ctrl + C` | 실행 중인 작업 강제 중단 |

### 줄바꿈
| 조작 | 설명 |
|------|------|
| `Shift + Enter` | 줄바꿈 (패널/채팅 UI 환경) |
| `\` 입력 후 `Enter` | 줄바꿈 (터미널 환경) |
| `Option + Enter` (Mac) / `Alt + Enter` (Windows) | 줄바꿈 (터미널 환경) |

### 이전 메시지 수정
| 조작 | 설명 |
|------|------|
| `↑` 방향키 | 이전에 입력한 메시지 불러오기 |
| 수정 후 `Enter` | 수정된 내용으로 재전송 |

### 대화 관리
| 조작 | 설명 |
|------|------|
| `/clear` | 대화 히스토리 초기화 (새로 시작) |
| `/compact` | 긴 대화를 요약해서 컨텍스트 절약 |
| `/undo` | 마지막 파일 변경 되돌리기 |
| `/status` | 현재 상태 확인 |

### 파일 / 참조
| 조작 | 설명 |
|------|------|
| `@파일명` | 특정 파일을 대화에 첨부 |
| `#` | 자주 쓰는 지시사항(메모리) 불러오기 |

### 모드 지정
| 조작 | 설명 |
|------|------|
| `/edit` | 파일 수정에만 집중 |
| `/chat` | 대화만, 파일 건드리지 않음 |

---

## 핵심 프롬프트 패턴 모음

| 상황 | 프롬프트 패턴 |
|------|--------------|
| 새 기능 추가 | `[기능명]을 추가해줘. 조건은 [조건]이야.` |
| 버그 수정 | `[증상]이 발생해. 원인을 찾아서 수정해줘.` |
| 코드 개선 | `[파일명] 코드를 더 읽기 좋게 개선해줘.` |
| 구조 변경 | `Plan 모드로 [작업 설명] 해줘.` |
| 배포 자동화 | `변경사항 확인하고 커밋 메시지 작성해서 push해줘.` |

---

## 앞으로 혼자 해볼 수 있는 실무 시나리오

1. **포트폴리오 사이트 만들기** — 링크트리를 발전시켜 전체 포트폴리오 페이지로
2. **React/Vue 앱 생성** — "React로 [앱 이름] 만들어줘"로 시작
3. **업무 자동화 스크립트** — "엑셀 파일 읽어서 데이터 정리하는 Python 스크립트 만들어줘"
4. **API 서버 만들기** — "Node.js로 간단한 REST API 서버 만들어줘"
5. **기존 코드 리뷰** — 회사 코드를 붙여넣고 "이 코드 어떻게 개선할 수 있어?"

---

## 문제 해결 (트러블슈팅)

### Claude Code 명령을 못 찾는 경우
```bash
# 설치 확인
npm list -g @anthropic-ai/claude-code

# 재설치
npm uninstall -g @anthropic-ai/claude-code
npm install -g @anthropic-ai/claude-code
```

Mac에서 `claude` 명령이 없다고 나오면:
```bash
# npm 전역 경로를 PATH에 추가 (zsh 기준)
echo 'export PATH="$PATH:$(npm prefix -g)/bin"' >> ~/.zshrc
source ~/.zshrc
```

Windows에서 명령을 못 찾는 경우 PowerShell을 **관리자 권한**으로 다시 실행한 뒤 재설치하세요.

### 로그인 오류가 나는 경우
```bash
# 로그아웃 후 재로그인
claude logout
claude

# 브라우저가 자동으로 안 열리면 터미널에 표시된 URL을 직접 복사해서 브라우저에 붙여넣기
```

> Free 플랜이면 로그인 후 오류가 발생할 수 있습니다. claude.ai에서 Pro/Max 플랜 여부를 확인하세요.

### Playwright MCP가 연결 안 되는 경우
- `settings.json` 경로가 정확한지 확인
  - Windows: `C:\Users\사용자명\.claude\settings.json`
  - Mac: `~/.claude/settings.json`
- Claude Code 완전 종료 후 재시작
- `npx playwright install chromium` 재실행
- Mac에서 보안 경고가 뜨는 경우: **시스템 설정 → 개인 정보 보호 및 보안** → Chromium 실행 허용

### GitHub push 오류가 나는 경우
```bash
# 인증 방법 확인
git remote -v

# HTTPS 방식으로 재설정
git remote set-url origin https://github.com/내아이디/my-linktree.git
```

---

*강의 관련 문의: 강사에게 직접 연락하세요.*
