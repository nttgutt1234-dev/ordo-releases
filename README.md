# ORDO for Windows

ORDO는 작업 요청을 받아 Codex CLI로 실행하고, 진행 상태와 검증 근거, 내려받을 결과물을 한 화면에 보여주는 Windows 앱입니다.

## 다운로드

- [Windows x64 ZIP 내려받기](https://github.com/nttgutt1234-dev/ordo-releases/releases/download/r111-preview/ORDO-Windows-20261110-r111.zip)
- [r111 프리뷰 릴리스](https://github.com/nttgutt1234-dev/ordo-releases/releases/tag/r111-preview)
- [한국어 빠른 시작](QUICK_START.ko.md)
- [제3자 구성 요소 고지](THIRD_PARTY_NOTICES.md)
- [r111 릴리스 노트](https://github.com/nttgutt1234-dev/ordo-releases/blob/main/RELEASE_NOTES.md)

ORDO에 포함된 FFmpeg에는 LGPL 2.1 이상 라이선스가 적용됩니다. [FFmpeg 소스 ZIP](https://github.com/nttgutt1234-dev/ordo-releases/releases/download/r111-preview/ORDO-FFmpeg-source-20261110-r111.zip)

ZIP을 모두 풀고 `ORDO-Windows-20261110-r111` 앱 폴더 안의 `ORDO.exe`를 엽니다. r111은 Git for Windows `2.54.0.windows.1`과 Codex CLI `0.163.0`을 정확히 요구합니다. Node.js `24.14.1`은 ZIP에 포함되어 있습니다.

AI 작업에는 Windows 11의 Microsoft Execution Containers(MXC) 지원, Codex 로그인 및 `gpt-6-astra`와 `gpt-6.1-sol` 모델 접근 권한이 필요합니다. 모델 접근은 로그인한 계정과 워크스페이스에서 확인해야 합니다. [OpenAI Windows 샌드박스 안내](https://learn.chatgpt.com/docs/windows/windows-sandbox#mxc-compatibility)
