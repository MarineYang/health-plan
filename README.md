# 30일 운동 루틴 (혼자 쓰는 PWA)

기록은 폰 안(브라우저 저장소)에만 저장되고 서버로 가지 않아요. 백업은 앱 안의 "파일로 내보내기"로 JSON 파일을 만들어 두세요.

## GitHub Pages에 올리기

```bash
cd workout-30
git init && git add . && git commit -m "workout 30"
gh repo create workout-30 --public --source=. --push
gh api -X POST repos/{owner}/workout-30/pages -f "source[branch]=main" -f "source[path]=/"
```

1~2분 뒤 `https://<깃허브아이디>.github.io/workout-30/` 에서 열려요.
(gh CLI를 안 쓰면: GitHub에서 저장소를 만들고 push → Settings → Pages → Branch: main / root → Save)

## 아이폰에 설치

1. 사파리로 위 주소 열기
2. 공유 → "홈 화면에 추가"
3. 홈 화면 아이콘으로 실행 (한 번 열고 나면 인터넷 없이도 열려요)

## 수정 후 배포

파일을 고친 뒤 `sw.js` 맨 위 `CACHE = 'plan30-v1'`의 숫자를 올리고 push하면, 폰에서 앱을 두 번 껐다 켜면 새 버전으로 바뀌어요.

## 데이터 파일 형식

```json
{ "app": "plan30", "version": 1, "exportedAt": "...",
  "days": { "day-1": { "n": 1, "date": "2026-11-06", "done": true,
                       "sets": { "EZ바 컬": [ { "w": 20, "r": 10 } ] } } } }
```
