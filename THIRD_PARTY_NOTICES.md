# 제3자 구성 요소 고지

아래 경로는 모두 ZIP을 풀었을 때 `ORDO.exe`가 있는 `ORDO-Windows-20261110-r111` 앱 폴더를 기준으로 합니다.

| 구성 요소 | 동봉된 라이선스 및 고지 |
| --- | --- |
| Electron `44.4.3` | `LICENSE` |
| Chromium `152.0.7977.130` 및 포함된 라이브러리 | `LICENSES.chromium.html` |
| Node.js `24.14.1` | `resources/node/LICENSE` |
| parse5 | `resources/app/engine/product/vendor/parse5.LICENSE.txt` |

## FFmpeg 소스와 빌드

ORDO에 포함된 `ffmpeg.dll`에는 LGPL 2.1 이상(LGPL-2.1-or-later) 라이선스가 적용됩니다. `LICENSES.chromium.html`의 **ffmpeg** 항목에서 고지를 확인할 수 있습니다. [FFmpeg 라이선스 안내](https://www.ffmpeg.org/legal.html), [LGPL 2.1 원문](https://www.gnu.org/licenses/old-licenses/lgpl-2.1.html)

동일 릴리스의 소스 ZIP에는 FFmpeg 커밋 `2b68d2babae73714846961fb0ee47e3b3d2e39a9`의 소스, Electron `44.4.3`의 패치와 빌드 설정, Windows x64 빌드 방법, 호환 DLL을 별도 ORDO 복사본에 적용하는 절차가 있습니다. [FFmpeg 소스 ZIP](https://github.com/nttgutt1234-dev/ordo-releases/releases/download/r111-preview/ORDO-FFmpeg-source-20261110-r111.zip), [FFmpeg 소스 ZIP SHA-256](https://github.com/nttgutt1234-dev/ordo-releases/releases/download/r111-preview/ORDO-FFmpeg-source-20261110-r111.zip.sha256)
