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
