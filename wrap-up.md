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
