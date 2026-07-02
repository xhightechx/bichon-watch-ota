# bichon-watch-ota

미니 비숑 스마트 시계(ESP32-S3) OTA 펌웨어 피드.

- `manifest.json` — `{"version": "x.y.z", "url": "<bichon_watch.bin raw URL>"}`
- `bichon_watch.bin` — 해당 버전 펌웨어 이미지

기기는 `manifest.json`의 raw URL을 주기적으로/수동으로 확인하고,
버전이 다르면 `url`에서 이미지를 받아 반대 OTA 슬롯에 설치한 뒤 재부팅한다.
부팅 검증에 실패하면 부트로더가 이전 슬롯으로 롤백한다.

## 새 버전 배포

1. 프로젝트에서 `version.txt` 버전 올리고 `idf.py build`
2. `build/bichon_watch.bin`을 이 저장소에 복사
3. `manifest.json`의 `version`을 같은 값으로 수정
4. commit + push (main 브랜치)
