# ORDO 빠른 시작

## 1. 실행 환경 확인

| 항목 | 필요한 환경 |
| --- | --- |
| Windows | Windows 11 x64. AI 작업에는 MXC를 지원하는 장치와 이를 허용하는 관리 정책이 필요합니다. |
| Git | Git for Windows `2.54.0.windows.1`이 정확히 필요합니다. |
| Codex | Codex CLI `0.163.0`이 정확히 필요합니다. ORDO와 같은 Windows 계정에서 기본 Codex 설정 폴더를 사용합니다. |
| AI 실행 | 인터넷 연결, Codex 로그인, `gpt-6-astra`의 Ultra 추론과 `gpt-6.1-sol`을 사용할 권한이 필요합니다. 플랜별 지원 범위는 확인되지 않았습니다. |
| Node.js | ORDO에 `24.14.1`이 포함되어 있어 별도 설치 없이 실행할 수 있습니다. |

`Win + R`에서 `winver`를 실행해 Windows 빌드를 확인할 수 있습니다. MXC는 Windows 11 24H2 빌드 `26100.9278`과 25H2 빌드 `26200.9278`부터 도입됐습니다. 실제 사용 가능 여부는 장치 지원과 관리 정책에도 달려 있습니다. [OpenAI Windows 샌드박스 안내](https://learn.chatgpt.com/docs/windows/windows-sandbox#mxc-compatibility)

## 2. ZIP 풀고 실행

이번 프리뷰의 `ORDO.exe`에는 Windows Authenticode 코드 서명이 없습니다.

1. [Windows x64 ZIP](https://github.com/nttgutt1234-dev/ordo-releases/releases/download/r111-preview/ORDO-Windows-20261110-r111.zip)을 내려받습니다. ZIP을 저장한 폴더에서 PowerShell을 열고, SHA-256을 확인해 [릴리스 노트](https://github.com/nttgutt1234-dev/ordo-releases/blob/main/RELEASE_NOTES.md)의 값과 비교합니다.

   ```powershell
   Get-FileHash -Algorithm SHA256 -LiteralPath '.\ORDO-Windows-20261110-r111.zip'
   ```

2. ZIP을 새 폴더에 모두 풉니다. `ORDO-Windows-20261110-r111` 앱 폴더 안에 `ORDO.exe`가 있습니다. `ORDO.exe`와 옆에 있는 `resources` 및 기타 파일을 함께 둡니다.
3. PowerShell에서 `git --version`이 `git version 2.54.0.windows.1`이고 `codex --version`이 `codex-cli 0.163.0`인지 확인합니다. 명령을 찾을 수 없거나 버전이 다르면 아래의 별도 실행 방법을 사용하세요.
4. `codex login status`로 로그인 상태를 확인합니다. 로그인되어 있지 않으면 `codex login`을 실행하고 브라우저에서 로그인합니다. 그 뒤 `ORDO.exe`를 더블 클릭합니다. ORDO가 지원 버전을 찾지 못하면 아래의 방법으로 실행 파일을 직접 지정하세요. [OpenAI Codex 로그인 안내](https://learn.chatgpt.com/docs/developer-commands#codex-login)

ORDO에 포함된 FFmpeg에는 LGPL 2.1 이상 라이선스가 적용됩니다. [FFmpeg 소스 ZIP](https://github.com/nttgutt1234-dev/ordo-releases/releases/download/r111-preview/ORDO-FFmpeg-source-20261110-r111.zip)

### ORDO 실행에만 필요한 버전 지정하기

1. [Codex CLI 0.163.0 공식 릴리스](https://github.com/openai/codex/releases/tag/rust-v0.163.0)의 Assets에서 `codex-package-x86_64-pc-windows-msvc.tar.gz`를 내려받아 별도 폴더에 모두 풉니다. 패키지 안의 `bin\codex.exe`와 함께 제공된 파일을 같은 배치로 유지합니다.
2. 필요한 Git 버전이 없으면 [Git for Windows 2.54.0 공식 릴리스](https://github.com/git-for-windows/git/releases/tag/v2.54.0.windows.1)의 Assets에서 `PortableGit-2.54.0-64-bit.7z.exe`를 받아 별도 폴더에 풉니다.
3. `ORDO.exe`가 있는 앱 폴더에서 PowerShell을 열고 예시의 두 경로를 실제 위치로 바꿉니다. 이미 일치하는 Git이 `PATH`에 있다면 `$gitDir`과 `PATH` 설정 줄을 생략합니다. 이 `PATH` 설정은 현재 PowerShell과 여기서 시작한 프로그램에 적용됩니다.

   ```powershell
   $codexExe = 'C:\Tools\Codex-0.163.0\bin\codex.exe'
   $gitDir = 'C:\Tools\PortableGit-2.54.0\cmd'
   $env:Path = "$gitDir;$env:Path"
   git --version
   & $codexExe --version
   & $codexExe login status
   ```

4. 로그인 상태가 확인되지 않으면 같은 PowerShell에서 `& $codexExe login`을 실행하고 브라우저에서 로그인합니다. `& $codexExe login status`를 다시 확인한 뒤 아래 명령으로 ORDO를 엽니다.

   ```powershell
   .\ORDO.exe --ordo-codex-executable "$codexExe"
   ```

MXC 확인이 필요하면 아래 명령을 실행하세요. `$codexExe`는 위에서 확인한 Codex 실행 파일입니다. 기존 Codex 명령을 사용한다면 `& $codexExe` 대신 `codex`를 입력합니다. `MXC_OK`와 종료 코드 `0`은 이 환경에서 격리 명령을 시작할 수 있다는 뜻입니다. 지원되지 않거나 관리 정책에서 막힌 경우에는 Windows 업데이트 상태와 관리 정책을 확인하세요. [OpenAI MXC 호환성 검사](https://learn.chatgpt.com/docs/windows/windows-sandbox#mxc-compatibility)

```powershell
& $codexExe -c windows.sandbox=mxc sandbox --include-managed-config --permission-profile :workspace -- cmd.exe /d /c echo MXC_OK
$LASTEXITCODE
```

## 3. 첫 작업 실행

ORDO에서 **연결 설정**을 열어 Codex CLI를 선택합니다. **새 작업**을 눌러 아래 요청을 붙여넣고 **시작**을 누릅니다. **다음 행동**에 질문이 표시되면 답변을 제출합니다.

```text
외부 자료와 첨부 파일 없이 동작하는 독립적인 JavaScript 문자열 함수를 만들어 주세요.
normalizeWhitespace(text)는 문자열 양끝의 공백 문자를 제거하고 내부의 연속 공백 문자(예: 공백, 탭, 줄바꿈)를 한 칸으로 바꿉니다. 나머지 문자는 그대로 유지합니다.

결과물은 normalize-whitespace.js, normalize-whitespace.test.js, README.md 세 파일입니다.
함수 파일은 CommonJS로 normalizeWhitespace를 내보내고, 테스트는 Node.js 내장 node:test와 node:assert/strict를 사용해 앞뒤 공백, 섞인 공백, 공백만 있는 문자열, 한글과 문장부호 보존을 각각 확인해 주세요.
생성할 함수와 테스트는 외부 패키지나 네트워크 요청 없이 Node.js 내장 기능만 사용하세요. 이 제한은 생성 파일의 동작에 적용되며, Codex 실행 환경에서는 모델 통신을 사용할 수 있습니다.
README에는 함수 예시와 테스트 명령을 적어 주세요. 완료 기준은 세 파일을 내려받을 수 있고 node --test normalize-whitespace.test.js가 통과하는 것입니다.
```

작업 상세의 **검증 근거**에서 테스트 결과를 확인합니다. **결과물** 탭에서 **내려받기**를 눌러 세 파일을 같은 폴더에 저장합니다. 직접 테스트를 반복하려면 그 폴더에서 `node --test normalize-whitespace.test.js`를 실행합니다. 별도 Node.js가 없다면 `node` 대신 앱 폴더 안 `resources\node\node.exe`의 전체 경로를 사용합니다.

## 데이터와 사용량

- 기본 저장 위치는 `%LOCALAPPDATA%\ORDO\user-data`입니다. 요청, 작업 파일과 실행 기록은 압축을 푼 앱 폴더와 별도로 저장됩니다.
- 저장된 작업과 결과를 여는 것은 로컬 동작입니다. AI 실행을 시작하면 처리에 필요한 요청과 자료가 로그인한 Codex 연결을 통해 전달됩니다. 첫 작업에는 개인 정보, 비밀값, 업무 파일을 넣지 마세요.
- AI 사용량은 로그인 방식과 계정의 사용 한도 또는 과금 조건을 따릅니다. ORDO의 **관측 토큰**은 선택한 실행에서 확인된 수치입니다. 계정의 전체 사용량이나 청구 금액은 연결한 서비스에서 확인하세요. [OpenAI 인증 방식 안내](https://learn.chatgpt.com/docs/auth)
