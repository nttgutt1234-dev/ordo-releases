# ORDO Windows r111 프리뷰

## 변경 사항

- 작업을 불러올 때 세 점의 크기가 순서대로 바뀌는 로딩 표시를 적용했습니다.
- 작업을 이어갈 수 있을 때 선택 가능한 조치를 보여주고, 실행 환경 확인이나 추가 요청이 필요한 경우 그 이유를 표시합니다.
- 실행 중임이 확인된 작업에 복구 안내가 진행 상태보다 먼저 나오던 문제를 수정했습니다. 현재 실행 상태가 확인되지 않으면 기존 확인 안내를 표시합니다.

## 배포 파일

| 항목 | 값 |
| --- | --- |
| Windows x64 ZIP | [ORDO-Windows-20261110-r111.zip](https://github.com/nttgutt1234-dev/ordo-releases/releases/download/r111-preview/ORDO-Windows-20261110-r111.zip) |
| SHA-256 | `e5177a0bb14ec845d27ba03feb08923324602b3e260772ed1f08676767f15e6d` · [체크섬 파일](https://github.com/nttgutt1234-dev/ordo-releases/releases/download/r111-preview/ORDO-Windows-20261110-r111.zip.sha256) |
| `ORDO.exe` 코드 서명 | Windows Authenticode 미서명 |
| 필수 외부 도구 | Git for Windows `2.54.0.windows.1`, Codex CLI `0.163.0` |
| 내장 런타임 | Node.js `24.14.1`, Electron `44.4.3` |

설치와 첫 작업은 [한국어 빠른 시작](https://github.com/nttgutt1234-dev/ordo-releases/blob/main/QUICK_START.ko.md)에서 확인할 수 있습니다.

ORDO에 포함된 FFmpeg에는 LGPL 2.1 이상 라이선스가 적용됩니다. 소스 ZIP에는 대응 소스, 빌드 방법과 수정본 사용 절차가 있습니다. [FFmpeg 소스 ZIP](https://github.com/nttgutt1234-dev/ordo-releases/releases/download/r111-preview/ORDO-FFmpeg-source-20261110-r111.zip), [FFmpeg 소스 ZIP SHA-256](https://github.com/nttgutt1234-dev/ordo-releases/releases/download/r111-preview/ORDO-FFmpeg-source-20261110-r111.zip.sha256)

## 검증 범위

- 최종 Windows ZIP의 파일 무결성을 확인했습니다. 앱을 한국어 화면으로 열어 로컬 상태를 두 차례 조회하고 정상 종료했습니다. 마지막 화면 표시 변경은 단위·통합 검사와 소스 검토를 통과했습니다.
- 마지막 화면 표시 변경 전 r111 후보의 패키지 엔진에서는 Codex로 JavaScript 예제 작업을 완료했습니다. 테스트 7개와 별도 검증 사례 4개가 통과했고, 내려받은 결과 파일 3개의 해시가 일치했습니다.
- 별도 복사본에 Electron `44.4.3`에서 별도로 배포한 FFmpeg DLL을 적용해 한국어 화면 기동, 로컬 상태 조회, 정상 종료를 확인했습니다.
- 이전 r107에서는 작은 JavaScript 작업 하나를 Codex로 실행해 테스트 통과와 결과물 세 파일의 다운로드 및 체크섬 일치를 확인했습니다.
- 계정·워크스페이스별 모델 접근과 MXC 지원은 각 환경에서 확인해야 합니다.

동봉 라이선스의 위치와 FFmpeg 소스는 [제3자 구성 요소 고지](https://github.com/nttgutt1234-dev/ordo-releases/blob/main/THIRD_PARTY_NOTICES.md)에서 확인할 수 있습니다.
