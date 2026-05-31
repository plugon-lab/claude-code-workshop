# PART 1. 설치 & 첫 대화 (50분)

## 사전 준비 (강의 전에 완료)

설치는 강의 중 Part 1에서 함께 진행합니다.  
아래 두 가지는 **강의 시작 전에 미리** 준비해 오세요.

- [ ] GitHub 계정 만들기 ([github.com](https://github.com) → Sign up)
- [ ] claude.ai 계정 만들기 + **Pro 또는 Max 플랜** 구독 ([claude.ai](https://claude.ai))

---

### ❶ VS Code 설치

#### ■ 다운로드 및 설치

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

### ❷ Node.js 설치

Claude Code는 Node.js 위에서 동작합니다. 반드시 설치가 필요합니다.

#### ■ 다운로드 및 설치

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

### ❸ Git 설치

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

### ❹ Claude Code 설치

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

### ❺ Claude 구독 계정으로 로그인

Claude Code는 **API 키 없이 claude.ai 구독 계정(Pro/Max 플랜)으로 바로 사용**할 수 있습니다.

#### ■ 로그인 실행

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

#### ■ 브라우저 인증

1. 터미널에 인증 URL이 표시됩니다
2. URL을 복사해 브라우저에 붙여넣거나, 자동으로 브라우저가 열립니다
3. claude.ai 로그인 페이지에서 **본인 계정으로 로그인**
4. **"Authorize Claude Code"** 버튼 클릭
5. 터미널로 돌아오면 로그인 완료 메시지 확인

> **구독 플랜 확인**: Pro 또는 Max 플랜이어야 합니다.  
> Free 플랜은 Claude Code를 지원하지 않습니다.  
> 플랜 확인: [claude.ai](https://claude.ai) → 우측 상단 프로필 → Plan

---

### ❻ VS Code 확장 설치

1. VS Code 실행
2. 좌측 Extensions 아이콘 클릭
   - Windows: `Ctrl+Shift+X`
   - Mac: `Cmd+Shift+X`
3. 검색창에 `Claude Code` 입력
4. **Claude Code** (Anthropic 제작) → **Install** 클릭

설치 후 VS Code 좌측 사이드바에 Claude Code 아이콘이 생깁니다.  
아이콘을 클릭하면 터미널 없이 패널에서 바로 대화할 수 있습니다.

---

### ❼ 첫 대화 실습

VS Code 사이드패널의 Claude Code를 열거나, 터미널에서 `claude`를 실행해 대화해보세요.

#### ■ 실습 프롬프트 1 — 자기소개 요청
```
안녕! 너는 어떤 걸 잘 할 수 있어?
```

#### ■ 실습 프롬프트 2 — 파일 생성 요청
```
hello.txt 파일을 만들고 "안녕하세요, Claude Code입니다!"라고 적어줘
```

만들어진 파일을 VS Code 탐색기(왼쪽 파일 목록)에서 확인해보세요.

#### ■ 실습 프롬프트 3 — 코드 생성 요청
```
Python으로 1부터 10까지 숫자를 출력하는 코드를 count.py 파일로 만들어줘
```

#### ■ 실습 프롬프트 4 — 코드 설명 요청
```
방금 만든 count.py 코드를 초보자도 이해할 수 있게 설명해줘
```

#### ■ 실습 프롬프트 5 — 코드 수정 요청
```
count.py에서 짝수만 출력하도록 수정해줘
```

> **핵심 포인트**: Claude Code는 실제 파일을 직접 읽고, 수정하고, 생성합니다.  
> 일반 챗GPT처럼 코드를 "보여주는" 게 아니라 "실제로 작업"합니다.

---

#### ■ Part 1 체크포인트

- [ ] VS Code가 정상 실행되는가
- [ ] `node --version` 명령이 정상 출력되는가
- [ ] `git --version` 명령이 정상 출력되는가
- [ ] `claude --version` 명령이 정상 출력되는가
- [ ] VS Code에서 Claude Code 확장 아이콘이 보이는가
- [ ] hello.txt 파일이 실제로 생성되었는가
- [ ] count.py 파일이 짝수만 출력하도록 수정되었는가
