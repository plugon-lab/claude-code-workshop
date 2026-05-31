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
