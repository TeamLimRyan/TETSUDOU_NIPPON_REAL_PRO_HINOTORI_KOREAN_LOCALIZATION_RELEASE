# 철도 일본! 리얼프로 특급 히노토리편 한국어 패치 v1.0.2

[최신 패치 다운로드](https://github.com/TeamLimRyan/TETSUDOU_NIPPON_REAL_PRO_HINOTORI_KOREAN_LOCALIZATION_RELEASE/releases/latest) · [오류 제보](https://github.com/TeamLimRyan/TETSUDOU_NIPPON_REAL_PRO_HINOTORI_KOREAN_LOCALIZATION_RELEASE/issues/new/choose)

필수 구성: **해당 게임 본편 + 업데이트 1.0.1**.

## 변경 사항

- 로딩 멈춤과 이미지 깨짐 제보에 대응해 텍스처의 GPU 압축 형식과 외부 스트림 저장을 복원했습니다.
- 기존 한국어 이미지와 배경·아이콘을 보존하면서 텍스처 데이터 증가를 줄였습니다.
- 기존 버전에서 적용한 내부 식별자와 텍스처 버퍼 보정도 유지합니다.

v1.0.1 사용자는 새 출력 폴더에 설치한 후 기존 모드를 교체하세요.

## 설치

Python 3.10 이상이 필요합니다. Windows 11 / Python 3.12에서 설치 검증을 완료했습니다.
사용자가 보유한 본편에 위 업데이트를 반영한 유효 exefs/romfs 추출 파일을 준비하세요. NSP/XCI를 직접 입력하지 않습니다. 원본 패키지 해시는 SOURCE-HASHES.txt, 추출 입력·출력 해시는 manifest.json에 있습니다.

```text
originals/<타이틀 ID>/exefs/main
originals/<타이틀 ID>/romfs/Data/...
```

```powershell
python apply_patch.py --input "D:\originals" --output "D:\hinotori-ko-v1.0.2" --layout atmosphere
```

`atmosphere`는 `atmosphere/contents/<타이틀 ID>`에, `eden`은 `load/<타이틀 ID>/JPRA_KO`에 설치합니다. 583개 xdelta와 사용자 원본에서 복사하는 보조 파일 224개, 총 807개를 크기·SHA-256으로 검증합니다.

원본과 겹치지 않는 새 출력 폴더를 사용하세요. 게임을 종료하고 기존 모드를 백업한 뒤 출력 내용을 교체합니다. 이전 JPRA_KO와 중복 활성화하지 마세요. 같은 파일을 바꾸는 다른 모드는 비활성화합니다. 실행 환경에도 해당 업데이트와 DLC가 설치되어 있어야 합니다.

## 재시도·제거

중단 후 같은 명령을 실행하면 검증된 임시 파일부터 이어갑니다. 잘못된 버전·손상된 패치·다른 내용이 있는 출력 폴더는 거부합니다. 진단 로그는 출력 폴더 옆 `.jpra-install-...json`에 남습니다.
제거할 때는 이번 출력 목록의 모드 파일만 제거하고 백업한 모드를 복구합니다. 원본 게임·업데이트·세이브는 삭제하지 않습니다.

영상·원본 유지 대상·보호 영역에는 일본어가 남을 수 있습니다. 원본 ROM·키·세이브는 포함하지 않습니다. 글꼴 라이선스는 licenses/OFL-NotoSansCJK.txt를 확인하세요.
