# 철도 일본! 리얼프로 히노토리 한국어 패치 v1.0.1

[최신 패치 다운로드](https://github.com/TeamLimRyan/TETSUDOU_NIPPON_REAL_PRO_HINOTORI_KOREAN_LOCALIZATION_RELEASE/releases/latest) · [오류 제보](https://github.com/TeamLimRyan/TETSUDOU_NIPPON_REAL_PRO_HINOTORI_KOREAN_LOCALIZATION_RELEASE/issues/new/choose)


**필수 구성: 히노토리 본편 + 업데이트 1.0.1.** 다른 게임 원본은 필요하지 않습니다.
본편 타이틀 ID: `010081F02464E000` / 업데이트 타이틀 ID: `010081F02464E800`.

## 이번 수정

텍스처를 GPU에 올릴 때 복사 범위가 버퍼 크기를 넘는 오류를 수정했습니다. 그림과 밉맵 픽셀은 그대로 유지합니다.
v1.0.0 사용자는 이 버전으로 새 출력 폴더를 만든 뒤 기존 JPRA_KO를 교체하세요. v1.0.0 위에 중복으로 활성화하지 마세요.

## 설치

Python 3.10 이상이 필요합니다. Windows 11 / Python 3.12에서 검증했습니다.
NSP/XCI를 직접 입력하지 않습니다. 본편에 업데이트 1.0.1을 반영한 유효 exefs/romfs 추출 파일을 준비하세요.
히노토리 본편과 업데이트만 필요합니다.
원본 패키지 해시는 `SOURCE-HASHES.txt`, 추출 파일별 입력/출력 해시는 `manifest.json`에 있습니다. 잘못된 원본·업데이트는 설치기가 거부합니다.

```text
originals/
  010081F02464E000/exefs/main
  010081F02464E000/romfs/Data/...
```

```powershell
python apply_patch.py --input "D:\originals" --output "D:\hinotori-ko-v1.0.1" --layout eden
```

`eden`은 `load/<타이틀 ID>/JPRA_KO`, `atmosphere`는 `atmosphere/contents/<타이틀 ID>`, `plain`은 `<타이틀 ID>` 아래에 파일을 만듭니다.
원본과 겹치지 않는 새 출력 폴더를 지정하세요. 569개 xdelta와 사용자 원본에서 복사하는 보조 파일 229개, 총 798개를 검증합니다.

게임을 종료하고 기존 모드를 백업한 뒤 생성된 `load` 또는 `atmosphere` 내용을 적용하세요. 해당 업데이트와 DLC가 실행 환경에도 설치되어 있어야 합니다. 같은 파일을 바꾸는 다른 모드는 비활성화하세요.

## 중단·복구·제거

중단 후 같은 명령을 재실행하면 검증된 임시 파일부터 이어갑니다. 동일 결과가 이미 있으면 재설치하지 않으며 다른 파일이 있는 출력 폴더는 덮어쓰지 않습니다.
로그와 임시 폴더는 출력 옆 `.jpra-install-...json`, `.jpra-stage-...` 이름으로 남습니다.
제거할 때는 해당 JPRA_KO 또는 이번 출력 목록의 모드 파일만 제거하고 이전 모드를 복구하세요. 원본 게임·업데이트·세이브는 삭제하지 않습니다.

## 검증 범위

최종 설치 결과의 전체 크기·SHA-256을 확인하고 Eden 0.2.1에서 영향 경로를 재시험했습니다. 이전 r7의 모드별 검증과 이번 수정의 검증 범위를 구분합니다. 자세한 최종 결과는 `QA-ko.md`를 확인하세요.
실기 크래시의 동일 ARM64 복사 오류를 재현하고 수정 후 통과한 것을 확인했습니다. 실제 Switch 기기에서의 재시험은 수행하지 않았습니다. 모든 역·전 구간 완주를 뜻하지 않습니다.

영상과 사용자 원본 유지·보호 영역은 원본을 유지하므로 일본어가 남을 수 있습니다. 게임·업데이트 원본, 키, 세이브는 배포하지 않습니다.
글꼴 라이선스는 `licenses/OFL-NotoSansCJK.txt`, 권리 안내는 `NOTICE.txt`를 참조하세요.
