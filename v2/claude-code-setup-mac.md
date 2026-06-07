# Mac 설치 가이드

> Plug:ON | 비개발자를 위한 Claude Code 입문\
> 이 워크북은 **Mac 사용자**용입니다.




## ❶ 시작 전 준비 체크리스트

***

* [ ] Mac이 켜져 있고 인터넷에 연결되어 있다
* [ ] claude.ai 계정이 있다 (없으면 지금 [claude.ai](https://claude.ai)에서 만들어두세요)

{% hint style="info" %}
**터미널이 처음이어도 괜찮습니다.**\
"복사 → 붙여넣기 → 엔터" 세 동작만으로 완성됩니다.
{% endhint %}

&#x20;



## ❷ VS Code 설치

***

{% stepper %}
{% step %}
### VS Code 다운로드

1. 브라우저에서 [code.visualstudio.com](https://code.visualstudio.com) 에 접속합니다
2. 파란색 **Download for Mac** 버튼을 클릭합니다
3. 다운로드된 `.zip` 파일을 더블클릭해서 압축을 풀면 `Visual Studio Code.app` 파일이 나타납니다
4. 이 파일을 **응용 프로그램(Applications) 폴더**로 드래그해서 이동합니다

{% hint style="info" %}
Applications 폴더로 이동하지 않으면 나중에 실행할 때 경고창이 뜰 수 있습니다.
{% endhint %}


{% endstep %}

{% step %}
### VS Code 실행 확인

Dock 또는 Launchpad에서 **Visual Studio Code**를 실행합니다.\
처음 실행 시 "인터넷에서 다운로드된 파일입니다" 경고창이 나오면 **열기**를 클릭합니다.

{% code title="이렇게 나오면 성공" %}
```
VS Code 첫 화면이 뜨면 설치 완료입니다.
```
{% endcode %}

{% hint style="warning" %}
**"손상되었거나 열 수 없습니다" 오류가 나면?**\
`시스템 설정 → 개인 정보 보호 및 보안 → 보안` 항목에서 **"그래도 열기"** 버튼을 클릭하세요.
{% endhint %}
{% endstep %}
{% endstepper %}

***




## ❸ Claude Code(CLI) 설치

***

{% stepper %}
{% step %}
### VS Code 터미널 열기

Claude Code를 설치하려면 **터미널**이라는 입력창이 필요합니다.\
별도 앱을 열 필요 없이 **VS Code 안에서 바로** 사용할 수 있습니다.

| 방법 | 동작 |
|------|------|
| 단축키 | `` Ctrl + ` `` (백틱 — Tab 키 바로 위에 있는 키) |
| 메뉴 | 상단 **Terminal → New Terminal** |

{% code title="이렇게 나오면 성공" %}
```
화면 아래쪽에 입력창이 열리고 % 또는 $ 기호가 깜빡입니다.
```
{% endcode %}


{% endstep %}

{% step %}
### Claude Code 설치

{% code title="터미널" %}
```bash
curl -fsSL https://claude.ai/install.sh | bash
```
{% endcode %}

설치가 시작되면 글자들이 쭉 흘러내립니다. 끝날 때까지 기다리세요 (1\~3분 소요).

{% hint style="info" %}
빨간/노란 글씨가 나와도 정상입니다. 경고(warning)일 뿐 설치는 계속 진행됩니다.
{% endhint %}

{% hint style="warning" %}
**"permission denied" 또는 "권한" 에러가 나면?**\
명령어 앞에 `sudo `를 붙여 다시 실행하세요.

{% code title="터미널" %}
```bash
sudo curl -fsSL https://claude.ai/install.sh | bash
```
{% endcode %}

Mac 로그인 비밀번호를 입력하라고 하면 입력하세요.\
**입력해도 화면에 아무것도 표시되지 않는 것이 정상입니다.** 다 입력하고 엔터를 누르세요.
{% endhint %}


{% endstep %}

{% step %}
### 설치 확인

{% code title="터미널" %}
```bash
claude --version
```
{% endcode %}

{% code title="이렇게 나오면 성공" %}
```
claude 1.x.x
```
{% endcode %}

{% hint style="warning" %}
**"command not found: claude" 에러가 나면?**\
VS Code 터미널을 완전히 닫고 새로 여세요.\
`Ctrl+Shift+P` → `Terminal: Kill All Terminals` 입력 → 엔터 → 다시 `` Ctrl+` ``
{% endhint %}
{% endstep %}
{% endstepper %}

***




## ❹ Claude Code 실행 & 로그인

***

{% stepper %}
{% step %}
### Claude Code 실행

{% code title="터미널" %}
```bash
claude
```
{% endcode %}


{% endstep %}

{% step %}
### 로그인

처음 실행하면 로그인 안내 화면이 나타납니다.

1. 방향키 또는 엔터로 **"Log in with Claude.ai"** 를 선택합니다
2. 브라우저가 자동으로 열리면 **claude.ai 계정으로 로그인**합니다
3. "Authorization successful" 메시지가 뜨면 터미널로 돌아옵니다

{% code title="이렇게 나오면 성공" %}
```
✓ Logged in as [내 이메일]
> 
```
{% endcode %}

{% hint style="warning" %}
**브라우저가 자동으로 열리지 않으면?**\
터미널에 표시된 URL을 복사해서 브라우저 주소창에 직접 붙여넣으세요.
{% endhint %}


{% endstep %}

{% step %}
### 첫 번째 대화 해보기

프롬프트(`>`) 뒤에 아래 문장을 입력하고 엔터를 눌러보세요.

{% code title="프롬프트" %}
```
안녕! 간단하게 자기소개 해줘.
```
{% endcode %}

Claude가 답변을 출력하면 성공입니다 🙌

{% code title="프롬프트" %}
```
오늘 처음 만나는 사람에게 AI를 한 문장으로 설명해줘.
```
{% endcode %}

{% code title="프롬프트" %}
```
이 폴더에서 작업하려면 어떻게 시작하면 좋을까?
```
{% endcode %}

{% hint style="info" %}
**종료하려면?** `/exit` 를 입력하거나 `Ctrl + C` 를 누르세요.
{% endhint %}
{% endstep %}
{% endstepper %}

***



&#x20;

## ❺ VS Code 확장 프로그램 설치 & 연동

터미널 명령어 방식 대신, **VS Code 패널 안에서 Claude와 대화**할 수 있습니다.\
일상적으로 가장 편하게 사용하는 방법입니다.

***

{% stepper %}
{% step %}
### 확장 프로그램 설치

**방법 A — 마켓플레이스에서 직접 설치 (권장)**

1. VS Code에서 `Cmd+Shift+X` 를 눌러 확장 프로그램 패널을 엽니다
2. 검색창에 `Claude Code` 를 입력합니다
3. **Anthropic** 이 만든 "Claude Code" 를 찾아 **설치** 를 클릭합니다

**방법 B — 링크로 바로 설치**

VS Code가 열린 상태에서 아래 링크를 브라우저에서 클릭합니다.\
[VS Code용 Claude Code 설치](vscode:extension/anthropic.claude-code)

{% hint style="warning" %}
**설치 후 Spark(⚡) 아이콘이 보이지 않으면?**\
`Cmd+Shift+P` → `Developer: Reload Window` 를 실행해 VS Code를 재시작하세요.
{% endhint %}


{% endstep %}

{% step %}
### Claude Code 패널 열기

| 방법 | 동작 |
|------|------|
| **가장 쉬운 방법** | 파일을 하나 열고, 편집기 오른쪽 위 ⚡ (Spark) 아이콘 클릭 |
| 명령 팔레트 | `Cmd+Shift+P` → "Claude Code: 새 탭에서 열기" 입력 |
| 상태 표시줄 | 화면 오른쪽 아래 **✱ Claude Code** 클릭 |

{% hint style="info" %}
Spark 아이콘은 파일을 열었을 때만 나타납니다. 빈 상태에서는 상태 표시줄의 **✱ Claude Code** 를 사용하세요.
{% endhint %}


{% endstep %}

{% step %}
### 패널에서 로그인

패널을 처음 열면 로그인 화면이 나타납니다.

1. **로그인** 버튼을 클릭합니다
2. 브라우저에서 claude.ai 계정으로 인증합니다

{% code title="이렇게 나오면 성공" %}
```
패널에 대화창이 나타나면 연동 완료입니다.
```
{% endcode %}

{% hint style="info" %}
이미 터미널에서 로그인했다면 이 단계가 자동으로 생략됩니다.
{% endhint %}

{% hint style="warning" %}
**"로그인하지 않음 · /login을 실행하십시오" 메시지가 나오면?**\
`Cmd+Shift+P` → `Developer: Reload Window` 로 창을 재시작하세요.
{% endhint %}


{% endstep %}

{% step %}
### 패널에서 첫 대화 해보기

{% code title="프롬프트" %}
```
지금 열려 있는 파일이 뭔지 설명해줘.
```
{% endcode %}

{% code title="프롬프트" %}
```
내가 처음 Claude Code를 쓴다면 뭐부터 해보면 좋을까?
```
{% endcode %}
{% endstep %}
{% endstepper %}

***



&#x20;

## ❻ 설치 완료 최종 점검

{% stepper %}
{% step %}
### 체크리스트

아래 항목을 하나씩 확인해보세요.

* [ ] VS Code를 설치하고 정상 실행된다
* [ ] VS Code 터미널에서 `claude --version` 을 실행하면 버전 숫자가 나온다
* [ ] `claude` 명령어로 터미널에서 로그인하고 대화를 해봤다
* [ ] VS Code 확장 프로그램 "Claude Code" 가 설치되어 있다
* [ ] VS Code 패널에서 Claude와 대화가 가능하다

모두 체크됐나요? 완벽합니다! 🎉


{% endstep %}

{% step %}
### 막힐 때 에러 해결 루틴

어떤 에러가 나든 당황하지 마세요. 아래 순서대로 따라오세요.

**1단계 — 에러 메시지를 그대로 복사한다**\
빨간 글씨를 드래그해서 복사하세요.

**2단계 — Claude에게 물어본다**\
[claude.ai](https://claude.ai) 채팅창에 아래처럼 입력하세요.

{% code title="프롬프트" %}
```
Claude Code 설치 중에 이런 에러가 났어: [복사한 에러 메시지]
Mac이고 VS Code 터미널 사용 중이야. 해결 방법 알려줘.
```
{% endcode %}

**3단계 — 강사에게 손든다**\
혼자 3분 이상 막히면 바로 손드세요. 부끄러운 게 아닙니다. 👋


{% endstep %}

{% step %}
### 자주 발생하는 에러 모음

| 에러 메시지 | 원인 | 해결 방법 |
| ------- | -- | ----- |
| `permission denied` | 설치 권한 부족 | 명령어 앞에 `sudo ` 붙이기 |
| `command not found: claude` | 터미널 경로 미반영 | 터미널 닫고 새로 열기 |
| Spark 아이콘 안 보임 | 파일 미열람 또는 VS Code 재시작 필요 | 파일 하나 열기 또는 `Developer: Reload Window` |
| 로그인 브라우저 안 열림 | 기본 브라우저 설정 문제 | 터미널에 표시된 URL 직접 복사해서 브라우저에 붙여넣기 |
| 확장 설치 후 패널 안 보임 | VS Code 재시작 필요 | `Cmd+Shift+P` → `Developer: Reload Window` |
{% endstep %}
{% endstepper %}

***

_Plug:ON — AI를 실무에 연결하다 | Plug in. Power on._
