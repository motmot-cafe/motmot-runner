# 모트모트 실행기 — 배포 자리

여기는 **코드가 아니라 꾸러미**만 두는 곳이다. 실행기(`실행기.exe`)가 켤 때와 6시간마다 `latest.json` 을 보고,
새 판이면 **물어본 뒤** `pension-sync-*.zip` 을 받아 갈아 끼운다.

- `latest.json` — 지금 판 번호 · 안내 · 꾸러미 주소 · sha256
- `pension-sync-0.8.9.zip` — 지금 판 꾸러미(`실행기.exe` 포함)
- `pension-sync-0.8.8.zip` — 바로 앞 판(되돌릴 때)
- `실행기.exe` — 지금 판의 실행기만 따로. 백신이 격리했을 때 여기서 다시 받는다(모토모토 I-104)

받는 쪽은 https 만 받고, 꾸러미 주소가 안내문과 같은 호스트여야 하며, sha256 이 맞아야만 적용한다.
`.env`(비밀값) · `state`(세션·로그) · `node_modules` · `artifacts` 는 덮지 않는다.

⚠ 이 저장소에 올릴 수 있는 사람은 사장님 PC 에서 코드를 돌릴 수 있다(모토모토 I-099). 사장님 허락(2026-09-28)으로 여기서 배포한다.
0.8.5 까지의 exe 는 `wavely1213/motmot-runner` 한 곳만 본다. 0.8.6 부터는 **이 저장소와 그 저장소 두 곳을 같이** 보고 더 새 판을 받는다(사장님 2026-09-28).
0.8.5 PC 가 처음 여기서 받으려면 그 PC `.env` 에 `UPDATE_URL=https://raw.githubusercontent.com/motmot-cafe/motmot-runner/main/latest.json` 한 줄이 필요하다(개인 저장소에는 올리지 않는다 — 사장님 결정).

## 블로그 원고기 (`blog-writer/`)

모토모토 블로그 원고기(`모토모토-블로그원고.exe`)도 여기서 받는다 — `blog-writer/latest.json` · zip · sha256. 자세한 것은 `blog-writer/README.md`.

## 사진정리 (`photo-sorter/`)

모토모토 사진정리(사장님 PC 의 바탕화면 아이콘 판)도 여기서 받는다 — 판 **2026.10.06-1** 부터 프로그램 안 「업데이트」.
켤 때와 6시간마다 `photo-sorter/latest.json` 을 보고, 새 판이면 화면 맨 위 「새 판이 있습니다」 → **「업데이트」 를 눌러야** 받는다.
받는 쪽은 https · 이 자리(raw.githubusercontent.com/motmot-cafe/motmot-runner/)만 · zip 의 sha256 이 맞아야만 바꾼다.

- `latest.json` — 판 번호 · 바뀐 점 · zip 주소 · sha256 · size
- `photo-sorter-<판>.zip` — 지금 판(안에 `사진정리/…`) · 바로 앞 판 하나(되돌릴 때)
- 올리기: 모토모토 저장소에서 `node tools/photo-sorter/publish.mjs <이 폴더> "바뀐 점"` → 커밋 · push.
- 원고기와 함께 도는 사진정리는 원고기 업데이트로 바뀐다(이것과 따로).
