# 철도 일본! 리얼프로 히노토리 한국어 패치 v1.0.0 (게임 빌드 r7)

[최신 패치 다운로드](https://github.com/TeamLimRyan/TETSUDOU_NIPPON_REAL_PRO_HINOTORI_KOREAN_LOCALIZATION_RELEASE/releases/latest) · [오류 제보](https://github.com/TeamLimRyan/TETSUDOU_NIPPON_REAL_PRO_HINOTORI_KOREAN_LOCALIZATION_RELEASE/issues/new/choose)


이 패키지는 **히노토리 전용**입니다. 다른 게임의 원본이나 업데이트를 요구하지 않습니다. 각 게임별로 배포하는 공개 한국어 패치입니다.

## 필수 본편·업데이트

- 본편 타이틀 ID: `010081F02464E000`
- **필수 업데이트: 1.0.1** (업데이트 타이틀 ID `010081F02464E800`)
- 히노토리 본편과 업데이트만 필요합니다.

본편만으로는 적용할 수 없습니다. 업데이트 1.0.1이 덮어쓰는 파일은 해당 업데이트 파일을 사용하고, 나머지는 본편 파일을 사용한 유효 파일 세트를 준비하세요. 업데이트 실행 파일·리소스의 SHA-256이 다르면 설치기가 거부합니다. 정확한 본편·업데이트·DLC 원본 패키지 해시는 `SOURCE-HASHES.txt`에, 추출 파일별 입력·출력 해시는 `manifest.json`에 있습니다.

게임을 실행하는 환경에도 해당 본편과 업데이트를 설치하고, DLC가 있는 경우 해당 DLC를 정상 설치해야 합니다. 게임·업데이트 원본, 암호화 키, 세이브는 이 패키지에 포함하지 않습니다.

## 설치

Python 3.10 이상이 필요합니다. Windows 11 / Python 3.12에서 검증했습니다. NSP/XCI 파일을 그대로 넣는 방식은 지원하지 않습니다. 준비한 추출 파일을 다음 구조로 둡니다.

```text
originals/
  010081F02464E000/exefs/main
  010081F02464E000/romfs/...
```

패키지 폴더에서 실행하세요.

```powershell
python apply_patch.py --input "D:\originals" --output "D:\hinotori-ko" --layout eden
```

`--layout eden`은 `load/<타이틀 ID>/JPRA_KO`, `atmosphere`는 `atmosphere/contents/<타이틀 ID>`, `plain`은 `<타이틀 ID>` 아래에 exefs/romfs를 만듭니다. 원본과 겹치지 않는 새 출력 폴더를 지정하세요.

569개 xdelta를 복원하고 사용자 입력에서 원본 보조 파일 229개를 복사하여 총 798개를 설치합니다. 보조 원본 자체는 패키지에 포함하지 않습니다. 모든 결과의 크기·SHA-256을 확인한 뒤 출력 폴더를 완성합니다.

Eden은 게임을 종료한 뒤 생성된 `load` 내용을 사용자 데이터 `load`에 복사하고 해당 JPRA_KO를 활성화하세요. Atmosphère는 생성된 `atmosphere` 폴더를 SD 카드에 병합하기 전에 기존 모드를 백업하세요. 같은 파일을 바꾸는 다른 한국어 패치는 비활성화하세요.

## 중단·복구·제거

설치가 중단되면 같은 명령을 재실행하면 검증된 임시 파일부터 이어갑니다. 동일 결과가 있으면 재설치 없이 종료하며 다른 파일이 있는 출력 폴더는 덮어쓰지 않습니다. 로그·임시 폴더는 출력 폴더 옆 `.jpra-install-...json`, `.jpra-stage-...` 이름으로 남습니다.

제거할 때는 게임을 종료하고 해당 JPRA_KO 모드를 비활성화하거나 이번 출력 목록의 모드 파일만 제거한 뒤 이전 모드를 복구하세요. 원본 게임·업데이트·세이브는 삭제하지 않습니다.

## 검증 범위·제한

기존 최종 r7와 xdelta·설치기·출력 파일이 같습니다. 이 게임의 실행 시나리오 12개와 모드 7개는 Eden 0.2.1에서 검증했습니다. 모든 역·전 구간 완주나 실기기 동작을 보증하지 않습니다. Atmosphère는 폴더·파일 해시 검증 대상입니다. 잠금 해제 모드는 격리된 QA 세이브를 사용했습니다.

모든 영상, 사용자 원본 유지 결정, 판독 불가 부분·보호 영역은 원본을 유지하므로 일본어가 남을 수 있습니다. 

글꼴 라이선스는 `licenses/OFL-NotoSansCJK.txt`, 도구·권리 안내는 `NOTICE.txt`를 참조하세요.
